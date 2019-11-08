---
title: Automatizar la recopilación de archivos para la exhibición de documentos electrónicos
ms.author: chrfox
author: chrfox
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 8d751419-d81b-4eb7-a2e5-8b03ccbf670c
search.appverid:
- MET150
description: 'Resumen: Aprenda a automatizar una recopilación de archivos de los equipos del usuario para la exhibición de documentos electrónicos.'
ms.openlocfilehash: 0133da6eecb229ad999043c9dfcb15d98a732829
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2019
ms.locfileid: "38030494"
---
# <a name="automate-file-collection-for-ediscovery"></a>Automatizar la recopilación de archivos para la exhibición de documentos electrónicos

 **Resumen:** Aprenda a automatizar una recopilación de archivos de los equipos del usuario para la exhibición de documentos electrónicos.
  
Todas las empresas se enfrentan a la posibilidad de juicios u otros tipos de acciones legales. Mientras los departamentos legales trabajan para reducir dicha exposición, los juicios son un hecho de la vida empresarial. Cuando una empresa se enfrenta a acciones legales, se necesita, a través del proceso de descubrimiento legal, que se proporcionen todos los materiales de documentación pertinentes al Tribunal y a los abogados de la contraparte. 
  
eDiscovery es el proceso mediante el cual las empresas crean un inventario, buscan, identifican, conservan, filtran y hacen que los materiales de documentación pertinentes que existen estén disponibles en formato electrónico. SharePoint 2013,Exchange Server 2013,Lync Server 2013,SharePoint Online y Exchange Online pueden disponer de grandes cantidades de contenido documental. Dependiendo de la versión, estos productos pueden admitir eDiscovery y retenciones locales (Lync mediante Exchange Server), facilitando a los equipos legales la indexación, identificación, retención y filtración del contenido más relevante para un caso determinado.
  
Muchos documentos se almacenan en los equipos locales de los usuarios (administradores) y no se encuentra en una ubicación centralizada. Esto hace prácticamente imposible la búsqueda de SharePoint 2013, y si no se puede buscar, no se puede incluir en eDiscovery. Esta solución le muestra cómo usar scripts de inicio de sesión, System Center Orchestrator 2012 R2 y Windows PowerShell de Exchange Server para automatizar la identificación y la recopilación de los materiales documentales de los equipos de los usuarios.
  
## <a name="what-this-solution-does"></a>Qué hace esta solución

Esta solución usa un grupo de seguridad global, una directiva de grupo y un script Windows PowerShell para buscar, inventariar y recopilar contenido y archivos de almacenamiento personal (PST) Outlook de los equipos locales de los usuarios en un recurso compartido de archivos oculto. Desde allí, los archivos PST se pueden volver a importar en Exchange Server 2013 o en Exchange Online. Todos los archivos se mueven a otro recurso compartido de archivos en Microsoft Azure usando un Runbook System Center Orchestrator 2012 R2 para un periodo de almacenamiento más largo y se indexan por SharePoint 2013. Posteriormente, usará centros de eDiscovery en su implementación de SharePoint 2013 local o en SharePoint Online, de la misma manera en la que realizaría normalmente eDiscovery. 
  
> [!IMPORTANT]
> Esta solución usa Robocopy para copiar archivos desde equipos de administrador a un recurso compartido de archivos centralizado. Como Robocopy no copia archivos que están abiertos o bloqueados, cualquier archivo, incluidos los archivos PST, que el administrador tenga abierto no se recopilará. Tendrá que recopilarlos manualmente. Esta solución le proporciona una lista que identifica de forma explícita los archivos que no puede copiar y la ruta de acceso completa de cada archivo. 
  
El siguiente diagrama le dirige por todos los pasos y elementos de la solución
  
![Introducción a la solución de recopilación automatizada de archivos](media/dbb447b5-c74c-4956-986c-10a1d047ac99.png)
  
|****Leyenda****||
|:-----|:-----|
|![Llamada magenta 1](media/000026a3-2bf0-4678-b468-ccb5f81da6f1.png)|Crear un objeto de directiva de grupo (GPO) y asociarlo a la recopilación de scripts de inicio de sesión  <br/> |
|![Llamada magenta 2](media/a31b11e2-3597-42a4-933e-b6af11ed6ef1.png)|   Configurar el filtro de seguridad GPO para aplicar el GPO solo al grupo de administradores <br/> |
|![Llamada magenta 3](media/3ced060c-daec-460d-a9b5-260a3dfcae36.png)|Cuando un administrador inicia sesión y se ejecuta el GPO, se llama a la recopilación de scripts de inicio de sesión.  <br/> |
|![Llamada magenta 4](media/6f269d84-2559-49e3-b18e-af6ac94d0419.png)|La recopilación de scripts de inicio de sesión hace un inventario de todas las unidades adjuntadas de forma local del equipo de los administradores, en busca de los archivos que desea, y registra su ubicación.  <br/> |
|![Llamada magenta 5](media/4bf8898c-44ad-4524-b983-70175804eb85.png)|La recopilación de scripts de inicio de sesión copia los archivos inventariados en un recurso compartido de archivos oculto en el servidor de implementación.  <br/> |
|![Llamada magenta 6](media/99589726-0c7e-406b-a276-44301a135768.png)| (Opción A) Ejecute manualmente el script de importación de PST para importar los archivos PST recopilados en Exchange Server 2013. <br/> |
|![Llamada magenta 7](media/ff15e89c-d2fd-4614-9838-5e18287d578b.png)|(Opción B) Mediante la herramienta de Importar y procesar de Office 365, importe los archivos PST recopilados en Exchange Online.  <br/> |
|![Llamada magenta 8](media/aaf3bd3d-9508-4aaf-a3af-44ba501da63a.png)|Mueva todos los archivos recopilados a un recurso compartido de archivos de Azure para un almacenamiento a largo plazo con el Runbook MoveToColdStorageSystem Center Orchestrator 2012 R2. <br/> |
|![Llamada magenta 9](media/b354642e-445e-4723-a84a-b41f7ac6e774.png)|Indexe los archivos en el recurso compartido de archivos de almacenamiento en frío con SharePoint 2013.  <br/> |
|![Llamada magenta 10](media/cebf7de5-7525-413b-9e52-638a4f8b2f74.png)|Realice eDiscovery en el contenido del almacenamiento en frío y en el Exchange Server 2013 local.  <br/> |
|![Llamada magenta 11](media/e59ab403-2f19-497a-92a5-549846dded66.png)|Realice eDiscovery en el contenido del Office 365.  <br/> |
   
## <a name="prerequisites"></a>Requisitos previos

La configuración de esta solución requiere muchos elementos, la mayoría de los cuales tenga probablemente en su sitio y configurados si está pensando en eDiscovery. Para los elementos que quizás no tenga o que necesiten una configuración específica, le proporcionaremos los vínculos que necesita para crear su configuración base. Debe tener la configuración base en su sitio antes de que configure la propia solución.
  
### <a name="base-configuration"></a>Configuración básica

|**Elemento**|**Vínculo**|
|:-----|:-----|
|Dominio de Servicios de dominio de Active Directory (AD DS)  <br/> ||
|Conectividad de Internet desde su red local  <br/> ||
|SQL Server 2012 para admitir SharePoint 2013 y System Center Orchestrator 2012 R2  <br/> |[Implementación de System Center Orchestrator: 2012](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
| Local o Azure basado en SharePoint 2013 para eDiscovery (necesario para la opción A) <br/> ||
|Servidor local de recurso compartido de archivos de implementación  <br/> ||
|Exchange Server 2013 local para la importación PST de la opción A  <br/> |CU5 (15.913.22) está disponible en [CU5](https://go.microsoft.com/fwlink/p/?LinkId=613426).  <br/> |
|System Center Orchestrator 2012 R2  <br/> |[Implementación de System Center Orchestrator: 2012](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
|Office 365 (Plan E3) con Exchange Online y SharePoint Online (necesario para la opción B)  <br/> |Para registrarse en una suscripción a Office 365 E3, consulte [Suscripción a Office 365 E3](https://go.microsoft.com/fwlink/p/?LinkId=613504).  <br/> |
|Suscripción a Azure con una máquina virtual  <br/> |Para registrarse en Azure, consulte: [Suscribirse a Windows Azure](https://go.microsoft.com/fwlink/p/?LinkId=512010) <br/> |
|Una conexión VPN entre su red local y su suscripción a Azure  <br/> |Para configurar un túnel VPN entre su suscripción a Azure y su red local, consulte [Conectar una red local a una red virtual de Microsoft Azure](https://go.microsoft.com/fwlink/p/?LinkId=613507).  <br/> |
|SharePoint 2013eDiscovery está configurado para buscar a través de SharePoint y Exchange Server 2013 y, opcionalmente, Lync Server 2013  <br/> |Para configurar eDiscovery de esta manera, consulte: [Configurar eDiscovery en SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=613508) y[Guía de entorno de pruebas: Configurar eDiscovery para Exchange, Lync, SharePoint y para el entorno de pruebas de recursos compartidos de archivos de Windows](https://go.microsoft.com/fwlink/p/?LinkId=393130).  <br/> |
|eDiscovery en Office 365 para SharePoint Online y Exchange Online  <br/> |Para configurar eDiscovery en Office 365, consulte [Configurar un centro eDiscovery en SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=613628).  <br/> |
   
## <a name="configure-the-environment"></a>Configurar el entorno

Ahora que tiene la configuración básica local, puede pasar a la configuración de la propia solución. 
  
### <a name="staging-file-share"></a>Implementar el uso compartido de archivos

1. En el dominio local, cree un grupo de seguridad global denominado Custodians.
    
2. Cree un recurso compartido de archivos oculto para los archivos que recopile de los equipos de los administradores. Este debería estar en un servidor local. Por ejemplo, en un servidor llamado Staging, cree un recurso compartido de archivos denominado Cases$. El símbolo **$** es necesario para que el recurso compartido esté oculto.
    
3. Establezca los siguientes permisos de recurso compartido:
    
  - Administradores: Modificar, leer
    
  - Administradores: Control total
    
  - Subsistema de confianza de Exchange: Modificar, leer
    
4. Abra la pestaña **Seguridad**, agregue el grupo Administradores y haga clic en **Avanzado**. Establecer los siguientes permisos para el grupo Administradores:
    
  - **Tipo: Denegar**
    
  - **Se aplica a: Esta carpeta, subcarpetas y archivos**
    
5. Haga clic en **Permisos avanzados** y seleccione lo siguiente:
    
  - **Atributos de lectura**
    
  - **Atributos extendidos de lectura**
    
  - **Permisos de lectura**
    
6. Pruebe el acceso al recurso compartido de archivos Casos$ haciendo lo siguiente:
    
1. Agregar un usuario al grupo de administradores
    
2. Coloque un archivo en la carpeta Casos$.
    
3. Como usuario, busque el servidor de almacenamiento provisional, por ejemplo, busque el recurso compartido \\\\Staging para ver qué recursos compartidos están disponibles. No debería ver el recurso compartido **Casos$** enumerado.
    
4. Escriba manualmente la ruta de acceso completa al recurso compartido Casos$ en Explorer. En ese momento, debería abrirse el recurso compartido Casos$.
    
5. Intente abrir el archivo que previamente colocó en el recurso compartido. Debería producirse un error.
    
### <a name="logon-script"></a>Script de inicio de sesión

1. Copie y pegue este script Windows PowerShell en el Bloc de notas:
    
  ```
  # Automated file collection script
# Substantial error processing should be added for robust execution and troubleshooting opportunities
# All commented out write-hosts are for debugging only and are commented out for regular execution

# Functions 

Function CreateCaseFolder() {

#Check to see if case folder already exists
$CaseFolderCheck = Test-Path $CaseLocation

try {

    if (!$CaseFolderCheck) {
    # Case folder doesn't exist.  Create the case folder and the log file location
    # Write-Host -ForegroundColor Cyan "Creating Case Folder $CaseLocation"
    New-Item "$CaseLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
    # Write-Host -ForegroundColor Cyan "Creating Case Log Folder $CaseLogLocation"
    New-Item "$CaseLogLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
    # Write-Host -ForegroundColor Cyan "Creating Case PST folder $CasePSTLocation"
    New-Item "$CasePSTLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue

    }
    else {

    # do nothing since the target case folder already exists

    }
}
catch [System.Exception] {

    # To do..
    # to log to an exception or log file
    
    }
}

Function CopyFileToCaseFolder($SourcePath, $TargetPath, $FileName) {
    
    # Check to see if the file already exists
    $TargetFileCheck = Test-Path $TargetPath\$FileName

try {

    if (!$TargetFileCheck) {
    # Copy the file to the case folder
    Write-Host $SourcePath $TargetPath $FileName
    robocopy "$SourcePath" "$TargetPath" "$FileName" /COPY:DATSO /TEE /LOG+:$LoggingFile /R:10 /W:10 | Out-Null

    }
    else {

    # do nothing since file is already in the target case folder

    }
}
catch [System.Exception] {

    # To do..
    # to log to an exception or log file
    
    }
}

# Global variable initializations

# Error log
$Loggederrors=@()

# The array to contain the file types we collect
$FileTypes = @("*.doc","*.docx","*.pst","*.txt")

# We'll set the case number to be a combination of the date and user name
# For example, a case for John Doe on Dec 14, 2014 at 2:38pm would be:
# 201412141438_jdoe
$CaseNo = get-date -Format yyyyMMddHHmm
$CaseNo = $CaseNo + "_" + [Environment]::UserName

# Target location to copy case files
$CaseRootLocation = "\\staging\Cases$" 

# File copy location, log file location, PST file location and temporary log file location
$CaseLocation = $CaseRootLocation + "\" + $CaseNo
$CaseLogLocation = $CaseRootLocation + "\" + $CaseNo + "\_Log"
$CasePSTLocation = $CaseRootLocation + "\" + $CaseNo + "\_PSTs"
$TemporaryLogLocation = [Environment]::getfolderpath('ApplicationData') + "\" + $CaseNo

# Inventory of local drives
$LocalDrives = Get-PSDrive -PSProvider FileSystem -Scope Global

$LoggingFile = "$CaseLogLocation\FileCopyErrors.log"

# Main script

# Create the case folder if it doesn't already exist
CreateCaseFolder

# Create the list of files to be copied
# First create the temporary directory in the AppData\Roaming folder
New-Item "$TemporaryLogLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
$LocalDrives | foreach {

    # Write-Host -ForeGroundColor Cyan "Collecting Files for Drive: " $_
    Get-ChildItem -Path $_.Root -Recurse -Include $FileTypes -ErrorAction SilentlyContinue -ErrorVariable +Loggederrors | Export-Clixml $TemporaryLogLocation\$_.xml -Force
    # Needs try catch and logged collection error file
}

# Now let's read each file and copy any files we need to the case folder
# We will also copy these XMLs to the case log files folder as we go along
# We only want to process XML files, just in case something else got in there as the script ran
$CaseDriveFiles = Get-ChildItem $TemporaryLogLocation -Filter '*.xml'
$CaseDriveFiles | foreach {
    # Copy the XML file to the case log location
    CopyFileToCaseFolder $_.Directory.FullName $CaseLogLocation $_.Name
    $DriveFile = $_.FullName
    # Write-Host -ForegroundColor Cyan "Copying Files specified in the XML file: $DriveFile"
    $CurrentDriveFile = Import-Clixml $DriveFile
    $CurrentDriveFile | foreach {
        # write-host $_.FullName
        # if it's a PST, add to the PSTs folder. otherwise add it to case folder
        if ($_.Extension -match '.PST')
        {
            CopyFileToCaseFolder $_.Directory.FullName $CasePSTLocation $_.Name
            write-host "this is a PST"
        }
        else
        {
            CopyFileToCaseFolder $_.Directory.FullName $CaseLocation $_.Name
        }
    }
}

# Now delete the temporary log file
Remove-Item $TemporaryLogLocation -Recurse 

Write-Host -ForegroundColor Cyan "Finished."

  ```

2. Guarde el script como CollectionScript.ps1 en una ubicación fácil de encontrar, por ejemplo, C:\\AFCScripts.
    
3. Use la característica Ir a del Bloc de notas. Realice estos cambios según sea necesario:
    
|**Número de línea**|**Lo que es necesario cambiar**|**obligatorio/opcional**|
|:-----|:-----|:-----|
|71  <br/> |Variable **$FileTypes**. Incluir todos los tipos de extensiones de archivo que desea que el script inventarie y recopile en la variable de matriz<br/> |Optional  <br/> |
|76 y 77  <br/> |Cambie la manera en la que la variable **$CaseNo** se genera para que se adapte a sus necesidades. El script captura la fecha y hora actuales y le anexa el nombre de usuario.<br/> |Optional  <br/> |
|80  <br/> |La variable **$CaseRootLocation** debe establecerse en el recurso compartido de archivos del archivo de colección de servidores de implementación. Por ejemplo, **\\\\Staging\\Cases$** <br/> |Necesario  <br/> |
   
4. Coloque el archivo CollectionScript.ps1 en el recurso compartido de archivo Netlogon en un controlador de dominio.  
    
### <a name="configure-gpo-for-the-logon-script-and-custodians-group"></a>Configurar el GPO para el grupo Administradores y el script de inicio de sesión

1. Configure un script de inicio de sesión para el grupo Administradores siguiendo la sección "Cómo asignar los scripts de inicio de sesión del usuario" en el tema, [Usar scripts de inicio, apagado, inicio de sesión y cierre de sesión en la directiva de grupo](https://go.microsoft.com/fwlink/p/?LinkId=614844).
    
2. Quite los usuarios autenticados de **Filtrado de seguridad** y agregue el grupo de administradores.
    
### <a name="pst-import-option-a-script-for-exchange-server-2013"></a>Opción A de importación de PST, script para Exchange Server 2013

1.  Copie y pegue el siguiente script Windows PowerShell en el Bloc de notas:
    
  ```
  # Script to import all PSTs in a given folder to a target mailbox
#
# This is for on-prem Exchange only
# Input parameters
# When you run the script, you call it with two parameters, PST source path and target mailbox alias
# For example:  .\PSTImport.ps1 \\FileShare\PSTFiles jdoe

param ([String]$SourcePath,[String]$MailboxAlias)

# Folder identifier is the string we want to show in the mailbox that we import the PSTs to

$FolderIdentifier = "zzImportedPSTs_"

# Connect to Exchange remote powershell using the connection Uri below
# This would be the format https://<exchange server FQDN>/Powershell

$ConnectionUri = 'https://h10-exch/PowerShell'
$RemoteEx2013Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri $ConnectionUri -Authentication Kerberos
Import-PSSession $RemoteEx2013Session

# Get all the files in the source path

$AllFiles = Get-ChildItem $SourcePath -Recurse

# Go through each file and if it's a PST launch a mailbox import request for it

$AllFiles | ForEach-Object {
    If ($_.Extension -eq ".pst") {
        $ImportName = $MailboxAlias + "_" + $_.Name
        $FolderName = $FolderIdentifier + $_.Name
        New-MailboxImportRequest -Name $ImportName -Mailbox $MailboxAlias -FilePath $_.FullName -TargetRootFolder $FolderName
    }
}
  ```

2. Guarde este script como PSTImportScript.ps1 en una ubicación fácil de encontrar. Por ejemplo, para mayor facilidad de uso, cree una carpeta en el servidor de almacenamiento provisional denominado \\\\Staging\\AFCScripts, y guárdelo allí.
    
3. Use la característica Ir a del Bloc de notas y realice los siguientes cambios según sea necesario:
    
|**Número de línea**|**Lo que es necesario cambiar**|**obligatorio/opcional**|
|:-----|:-----|:-----|
|12  <br/> |**$FolderIdentifier** etiqueta las carpetas del buzón en las que se importan los archivos PST. Cambie esto si es necesario.<br/> |Opcional  <br/> |
|432  <br/> |**$ConnectionUri** tiene que estar establecido como su propio servidor. <br/> > [!IMPORTANT]> Asegúrese de que su **$ConnectionUri** indica una ubicación http://, y no a una https://. No funcionará con https://          |Obligatorio  <br/> |
   
4. Compruebe que la cuenta del subsistema de confianza de Exchange tiene permisos de lectura, escritura y ejecución en el recurso compartido \\\\Staging\\Cases$.
    
5. El script de importación de PST requiere los dos parámetros de entrada siguientes:
    
  - **$SourcePath** La ubicación en la que se van a importar los archivos PST, por ejemplo \\\\Staging\\Cases$
    
  - **$MailboxAlias** el alias del buzón de destino que va a recibir los elementos de correo electrónico importados
    
6. Por ejemplo, si desea importar todos los archivos PST de la ruta de acceso \\Staging\Cases$ en un buzón con el alias eDiscoveryMailbox, ha de ejecutar el script de la siguiente manera `\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox`.
    
### <a name="pst-import-option-b-for-exchange-online"></a>Opción B de importación de PST, para Exchange Online

-  Cree la estructura del buzón para colocar los archivos PST importados. Para obtener más información sobre cómo crear un buzón de usuario en Exchange Online, consulte[Crear buzones de usuario en Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=615118).
    
### <a name="cold-storage"></a>Almacenamiento en frío

1. Cree un recurso compartido de archivos en el Máquina virtual de Azure, donde se colocarán todos los archivos recopilados, por ejemplo, \\\\AZFile1\\ContentColdStorage.
    
2. Conceda a la cuenta de acceso de contenido predeterminada al menos permisos de lectura al recurso compartido y a todas las subcarpetas y archivos. Para obtener más información sobre cómo configurar la Búsqueda de SharePoint 2013, consulte [Crear y configurar una aplicación de servicio de búsqueda en SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=614940).
    
3. Si prevé que se van a importar archivos PST desde \\\\AZFile1\\ContentColdStorage, conceda al subsistema de confianza de Exchange permisos de lectura, escritura y ejecución para el recurso compartido.
    
### <a name="orchestrator"></a>Orchestrator

1. Descargue el [runbook MoveToColdStorage](https://go.microsoft.com/fwlink/?LinkId=616095) desde el Centro de descarga de Microsoft.
    
2. Abra **Runbook Designer**, en el panel **Conexiones** y haga clic en la carpeta en la que desea importar el Runbook. Haga clic en el menú **Acciones** y, después, haga clic en **Importar**. Aparecerá el cuadro de diálogo **Importar**.
    
3. En el cuadro **Ubicación del archivo**, escriba la ruta de acceso y el nombre del Runbook que desea importar o haga clic en el botón de los puntos suspensivos ( **...**) para buscar el archivo que desea importar. 
    
4. Seleccione **Importar Runbooks** e **Importar datos cifrados de Orchestrator**. Borre **Contadores**, **Programaciones**, **Variables**, **Grupos de equipos**, **Importar configuraciones globales** y **Sobrescribir configuraciones globales existentes**.
    
5. Haga clic en **Finalizar**.
    
6. Edite el runbook **MoveFilesToColdStorage** de la siguiente manera:
    
1. Actividad **Mover archivo**: establezca la ruta de acceso del **archivo de origen** en el recurso compartido de archivos de la colección, por ejemplo \\\\Staging\\cases$. Establezca la **Carpeta de destino** del recurso compartido de archivos de almacenamiento en frío en Azure, por ejemplo, \\\\AZFile1\\ContentColdStorage. Seleccione **Crear un archivo con un nombre único**.
    
2. Actividad **Eliminar carpeta**: establezca la **ruta de acceso:** en el recurso compartido de archivos de la colección, por ejemplo \\\\Staging\\cases$\\*, y seleccione **Eliminar todos los archivos y las subcarpetas**. 
    
7. Implemente el runbook **MoveToColdStorage** usando los procedimientos descritos en[Implementar runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615120).
    
### <a name="sharepoint-on-premises-search-for-cold-storage"></a>Búsqueda local de SharePoint para el almacenamiento en frío

1. Cree un nuevo origen de contenido en su granja de servidores de SharePoint 2013 para el recurso compartido de almacenamiento en frío en Azure, por ejemplo, \\\\AZFile1\\ContentColdStorage. Para obtener más información sobre cómo administrar orígenes de contenido, consulte [Agregar, editar o eliminar un origen de contenido en SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615004).
    
2. Inicie un Rastreo completo. Para obtener más información, consulte [Iniciar, pausar, reanudar o detener un rastreo en SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).
    
## <a name="using-the-solution"></a>Uso de la solución

Hay cinco pasos principales para usar esta solución suponiendo que no desee importar los archivos PST en Exchange Server 2013 y en Exchange Online. Esta sección le proporciona los procedimientos para todos ellos. Su principal interacción con la solución consistirá en realizar lo siguiente:
  
1. Administre la pertenencia de un usuario en el grupo Administradores.
    
2. Errores
    
3. Administre el proceso de importación de PST.
    
4. Mover los archivos de la colección a un almacenamiento en frío
    
El resto de los pasos no son específicos para esta solución. Son tareas administrativas estándares que realiza en SharePoint 2013, Office 365 y Azure. Hay elementos para los que esta solución no proporciona ninguna orientación y que tendrá que solucionar en función de las necesidades de su empresa, como:
  
1. El seguimiento de sus casos de eDiscovery y los administradores que están asociados con cada uno
    
2. El seguimiento los conjuntos de colecciones de archivos que están asociados con cada caso de eDiscovery
    
3. La coordinación de la sincronización de los pasos de importación y desplazamiento a un almacenamiento en frío.
    
4. Administrar el espacio de archivo usado en Azure.
    
5. Administrar los buzones en los que se importan los archivos PST.
    
6. La copia de seguridad y restauración de todos los datos locales
    
### <a name="custodian-management"></a>La administración de los administradores

- Para iniciar el proceso de recopilación automatizada de archivos para un usuario concreto, agréguelos al grupo de administradores. La próxima vez que el usuario inicie sesión, se ejecutará el script de inicio de sesión asignado al grupo de administradores mediante la directiva de grupo. 
    
### <a name="monitor-collected-files-and-review-log-files"></a>Supervisar los archivos recopilados y revisar los archivos de registro.

1. Observe el recurso compartido de archivos de la colección, por ejemplo, \\\\Staging\\cases$\\*, de la carpeta de colección del usuario. Al nombre de la carpeta se le aplicará el siguiente formato:  *yyyyMMddHHmm_UserName*  .
    
2. Cuando la colección esté completa, abra la carpeta de la colección y vaya hasta la carpeta _Log. Dentro de la carpeta _Log verá lo siguiente:
    
  - Un archivo XML para cada unidad local del equipo de los usuarios, por ejemplo, **A.xml**, **C.xml**. Estos archivos contienen las unidades de inventario que llevan su nombre y se usan para la operación robocopy.
    
    > [!NOTE]
    > El script de colección solo creará una entrada en el archivo de inventario para los tipos de archivo que usted definió en el propio script. No creará una entrada de inventario para cada archivo del equipo de los usuarios. 
  
  - Un archivo de registro denominado FileCopyErrors.log para la ejecución de cada colección. Este archivo contiene una lista de los archivos que robocopy no pudo copiar en el recurso compartido de la colección de archivos, por ejemplo, \\\\Staging\\cases$\\*. Necesitará revisar esto y decidir qué acciones llevar a cabo para estos archivos perdidos. Normalmente, deberá recopilarlos manualmente si desea conservarlos y, si decide que no son necesarios, pueden omitirse de la colección.
    
### <a name="pst-import-option-a-for-exchange-server-2013"></a>Opción A de importación de PST para Exchange Server 2013

1. Inicie sesión en el servidor que hospeda el recurso compartido de archivos de la colección, por ejemplo, **Almacenamiento provisional** y abra Windows PowerShell. Para obtener más información sobre cómo iniciar Windows PowerShell, consulte[Iniciar Windows PowerShell en Windows Server](https://go.microsoft.com/fwlink/p/?LinkId=615115).
    
2. Establezca la directiva de ejecución en la opción Sin restricción. Escriba  `Set-ExecutionPolicy Unrestricted -Scope Process` en Windows PowerShell y, a continuación, presione Entrar.
    
3. Ejecute el archivo PSTImportScript.ps1 y proporcione los parámetros **$SourcePath** y **$MailboxAlias**. Para obtener más información sobre cómo ejecutar los scripts de Windows PowerShell, consulte[Ejecutar scripts](https://go.microsoft.com/fwlink/p/?LinkID=615117).
    
4. Revise la salida de errores.
    
5. Antes de intentar importar un archivo PST con el mismo nombre en el mismo buzón, deberá quitar la solicitud de importación del buzón. Ejecute el comando siguiente para hacerlo:  `Get-MailboxImportRequest | Remove-MailboxImportRequest`. Se le solicitará que quite cada solicitud individual de la cola. Responda según sea necesario.
    
### <a name="pst-import-option-b-for-exchange-online"></a>Opción B de importación de PST, para Exchange Online

- Para colocar los archivos PST recopilados en Exchange Online, siga los procedimientos descritos en la sección Importar archivos en Office 365 a través de la sección carga en red del [Servicio de importación de Office 365](https://go.microsoft.com/fwlink/p/?LinkId=614938).
    
### <a name="move-to-cold-storage"></a>Mover a un almacenamiento en frío

1. Ejecute el runbook **MoveToColdStorage** usando los procedimientos descritos en[Ejecutar runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615123).
    
2. Observe el recurso compartido de archivos de Azure que está usando para el almacenamiento a largo plazo, por ejemplo, \\\\AZFile1\\ContentColdStorage y en el recurso compartido de archivos de la colección local, por ejemplo,\\\\Staging\\cases$. Debería ver que los archivos y carpetas aparecen en el recurso compartido de archivos de almacenamiento en frío y desaparecen del recurso compartido de archivos de la colección.
    
### <a name="ediscovery"></a>eDiscovery

1. Permita que se ejecute el rastreo completo del recurso compartido de archivos de almacenamiento en frío de forma programada o inicie un rastreo. Para obtener más información sobre cómo iniciar rastreos completos o incrementales, consulte [Iniciar, pausar, reanudar o detener un rastreo en SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).
    
2. Cree un caso de eDiscovery en SharePoint 2013 si usó la opción A para la importación de un archivo PST o cree un caso de eDiscovery en SharePoint Online si usó la opción B.
    

