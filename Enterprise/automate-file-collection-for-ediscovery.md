---
title: Automatizar la recopilación de archivos para la exhibición de documentos electrónicos
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: ''
ms.assetid: 8d751419-d81b-4eb7-a2e5-8b03ccbf670c
search.appverid:
- MET150
description: 'Resumen: Aprenda a automatizar una recopilación de archivos de los equipos del usuario para la exhibición de documentos electrónicos.'
ms.openlocfilehash: 83bd55ff786803cfcb3eec9430d72de30179d000
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997981"
---
# <a name="automate-file-collection-for-ediscovery"></a>Automatizar la recopilación de archivos para la exhibición de documentos electrónicos

All companies face the potential of lawsuits or other types of legal action. While legal departments work to reduce that exposure, litigation is a fact of business life. When a company faces legal action, they are required, through the process of legal discovery, to provide all relevant documentary materials to the court and to opposing counsel. 
  
eDiscovery is the process by which companies inventory, search, identify, preserve, filter, and make available the relevant documentary materials that exist in electronic form. SharePoint 2013, Exchange Server 2013, Lync Server 2013, SharePoint Online, and Exchange Online can hold large amounts of documentary content. Depending on the version, these products may support eDiscovery and in place holds (Lync via Exchange Server), making it easier for the legal teams to index, identify, hold, and filter the most relevant content for a given case.
  
Many documents are stored on users' (Custodians) local computers, not in a centralized location. This makes it essentially impossible for SharePoint 2013 to search, and if it can't be searched, it can't be included in eDiscovery. This solution shows you how to use logon scripts, System Center Orchestrator 2012 R2 and Windows PowerShell for Exchange Server to automate the identification and collection of documentary materials from users' computers.
  
## <a name="what-this-solution-does"></a>Qué hace esta solución

This solution uses a global security group, Group Policy, and a Windows PowerShell script to locate, inventory, and collect content and Outlook personal store (PST) files from users local computers to a hidden file share. From there, the PST files can be imported into either Exchange Server 2013 or Exchange Online. All files are then moved using a System Center Orchestrator 2012 R2 runbook to another file share in Microsoft Azure for long-term storage and indexing by SharePoint 2013. You then use eDiscovery centers in your on-premises SharePoint 2013 deployment or in SharePoint Online as you regularly would to perform eDiscovery. 
  
> [!IMPORTANT]
> This solution uses robocopy to copy files from custodian's computers to a centralized file share. Because robocopy does not copy files that are open or locked, any files, including PST files, that the custodian has open will not be collected. You will have to collect them manually. This solution does provide you with a list that explicitly identifies the files it cannot copy and the full path to each file. 
  
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
|![Llamada magenta 7](media/ff15e89c-d2fd-4614-9838-5e18287d578b.png)|(Opción B) Mediante la herramienta de importación y el proceso de 365 de Microsoft, importe los archivos PST recopilados en Exchange Online.  <br/> |
|![Llamada magenta 8](media/aaf3bd3d-9508-4aaf-a3af-44ba501da63a.png)|Mueva todos los archivos recopilados a un recurso compartido de archivos de Azure para un almacenamiento a largo plazo con el Runbook MoveToColdStorageSystem Center Orchestrator 2012 R2. <br/> |
|![Llamada magenta 9](media/b354642e-445e-4723-a84a-b41f7ac6e774.png)|Indexe los archivos en el recurso compartido de archivos de almacenamiento en frío con SharePoint 2013.  <br/> |
|![Llamada magenta 10](media/cebf7de5-7525-413b-9e52-638a4f8b2f74.png)|Realice eDiscovery en el contenido del almacenamiento en frío y en el Exchange Server 2013 local.  <br/> |
|![Llamada magenta 11](media/e59ab403-2f19-497a-92a5-549846dded66.png)|Realizar eDiscovery en el contenido de Microsoft 365.  <br/> |
   
## <a name="prerequisites"></a>Requisitos previos

The configuration of this solution requires many elements, most of which you likely have in place and configured if you're thinking about eDiscovery. For the elements that you may not have or ones that require a specific configuration, we'll provide you with the links you need build out your base configuration. You must have the base configuration in place before you configure the solution itself.
  
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
|Microsoft 365 E3 con Exchange Online y SharePoint Online (necesario para la opción B)  <br/> |Para suscribirse a una suscripción a Microsoft 365 E3, consulte [suscripción a microsoft 365 E3](https://www.microsoft.com/microsoft-365/enterprise-e3-business-software?activetab=pivot%3aoverviewtab).  <br/> |
|Suscripción a Azure con una máquina virtual  <br/> |Para registrarse en Azure, consulte: [Suscribirse a Windows Azure](https://go.microsoft.com/fwlink/p/?LinkId=512010) <br/> |
|Una conexión VPN entre su red local y su suscripción a Azure  <br/> |Para configurar un túnel VPN entre su suscripción a Azure y su red local, consulte [Conectar una red local a una red virtual de Microsoft Azure](https://go.microsoft.com/fwlink/p/?LinkId=613507).  <br/> |
|SharePoint 2013eDiscovery está configurado para buscar a través de SharePoint y Exchange Server 2013 y, opcionalmente, Lync Server 2013  <br/> |Para configurar eDiscovery de esta manera, consulte: [Configurar eDiscovery en SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=613508) y[Guía de entorno de pruebas: Configurar eDiscovery para Exchange, Lync, SharePoint y para el entorno de pruebas de recursos compartidos de archivos de Windows](https://go.microsoft.com/fwlink/p/?LinkId=393130).  <br/> |
|eDiscovery en Microsoft 365 para SharePoint Online y Exchange Online  <br/> |Para configurar la exhibición de documentos electrónicos en Microsoft 365, consulte [configurar un centro de exhibición de documentos electrónicos en SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=613628).  <br/> |
   
## <a name="configure-the-environment"></a>Configurar el entorno

Ahora que tiene la configuración básica local, puede pasar a la configuración de la propia solución. 
  
### <a name="staging-file-share"></a>Implementar el uso compartido de archivos

1. En el dominio local, cree un grupo de seguridad global denominado Custodians.
    
2. Create a hidden file share for the files that are collected from Custodians computers. This should be on an on-premises server. For example, on a server called Staging, create a file share called Cases$. The **$** is required to make this a hidden share.
    
3. Establezca los siguientes permisos de recurso compartido:
    
  - Administradores: Modificar, leer
    
  - Administradores: Control total
    
  - Subsistema de confianza de Exchange: Modificar, leer
    
4. Open the **Security** tab, add the Custodians group, and click **Advanced**. Set the following permissions for the Custodians group:
    
  - **Tipo: Denegar**
    
  - **Se aplica a: Esta carpeta, subcarpetas y archivos**
    
5. Haga clic en **Permisos avanzados** y seleccione lo siguiente:
    
  - **Atributos de lectura**
    
  - **Atributos extendidos de lectura**
    
  - **Permisos de lectura**
    
6. Pruebe el acceso al recurso compartido de archivos Casos$ haciendo lo siguiente:
    
1. Agregar un usuario al grupo de administradores
    
2. Coloque un archivo en la carpeta Casos$.
    
3. As the user, browse to the staging server, for example browse to the \\\\Staging share to see what shares are available. You shouldn't see the **Cases$** share listed.
    
4. Manually type the full path to the Cases$ share into Explorer. This should open the Cases$ share.
    
5. Try to open the file you previously placed in the share. This should fail.
    
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
    
3. Use the Go To feature in Notepad. Make the following changes, as needed:
    
|**Número de línea**|**Lo que es necesario cambiar**|**obligatorio/opcional**|
|:-----|:-----|:-----|
|71  <br/> |**$FileTypes** variable. Include all the file type extensions that you want the script to inventory and collect in the array variable. <br/> |Opcional  <br/> |
|76 y 77  <br/> |Change the way the **$CaseNo** variable is built to suit your needs. The script captures the current date and time and appends the user name to it. <br/> |Opcional  <br/> |
|80  <br/> |La variable **$CaseRootLocation** debe establecerse en el recurso compartido de archivos del archivo de colección de servidores de implementación. Por ejemplo, **\\\\Staging\\Cases$** <br/> |Obligatorio  <br/> |
   
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

2. Save the script as PSTImportScript.ps1 in a location that's easy for you to find. For example and ease of use, create a folder on your staging server called \\\\Staging\\AFCScripts, and save it there.
    
3. Use la característica Ir a del Bloc de notas y realice los siguientes cambios según sea necesario:
    
|**Número de línea**|**Lo que es necesario cambiar**|**obligatorio/opcional**|
|:-----|:-----|:-----|
|12   <br/> |**$FolderIdentifier** tags the mailbox folders that PSTs are imported into. Change this if necessary. <br/> |Opcional  <br/> |
|17   <br/> |**$ConnectionUri** tiene que estar establecido como su propio servidor. <br/> > [!IMPORTANT]> Make sure your **$ConnectionUri** points to a http location, not https. It won't work with https:.          |Obligatorio  <br/> |
   
4. Compruebe que la cuenta del subsistema de confianza de Exchange tiene permisos de lectura, escritura y ejecución en el recurso compartido \\\\Staging\\Cases$.
    
5. El script de importación de PST requiere los dos parámetros de entrada siguientes:
    
  - **$SourcePath** La ubicación en la que se van a importar los archivos PST, por ejemplo \\\\Staging\\Cases$
    
  - **$MailboxAlias** el alias del buzón de destino que va a recibir los elementos de correo electrónico importados
    
6. Por ejemplo, si desea importar todos los archivos PST de la ruta de acceso \\Staging\Cases$ en un buzón con el alias eDiscoveryMailbox, ha de ejecutar el script de la siguiente manera `\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox`.
    
### <a name="pst-import-option-b-for-exchange-online"></a>Opción B de importación de PST, para Exchange Online

-  Create the mailbox structure to place the imported PST files into. For more information on how to create a user mailbox in Exchange Online, see[Create User Mailboxes in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=615118).
    
### <a name="cold-storage"></a>Almacenamiento en frío

1. Cree un recurso compartido de archivos en el Máquina virtual de Azure, donde se colocarán todos los archivos recopilados, por ejemplo, \\\\AZFile1\\ContentColdStorage.
    
2. Grant the default content access account at least Read permissions to the share and all subfolders and files. For more information about configuring SharePoint 2013 Search, see [Create and configure a Search service application in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=614940).
    
3. Si prevé que se van a importar archivos PST desde \\\\AZFile1\\ContentColdStorage, conceda al subsistema de confianza de Exchange permisos de lectura, escritura y ejecución para el recurso compartido.
    
### <a name="orchestrator"></a>Orchestrator

1. Descargue el [runbook MoveToColdStorage](https://go.microsoft.com/fwlink/?LinkId=616095) desde el Centro de descarga de Microsoft.
    
2. Open the **Runbook Designer**, in the **Connections** pane, click the folder that you want to import the runbook into. Click the **Actions** menu, and the click **Import**. The **Import** dialog box appears.
    
3. En el cuadro **Ubicación del archivo**, escriba la ruta de acceso y el nombre del Runbook que desea importar o haga clic en el botón de los puntos suspensivos ( **...**) para buscar el archivo que desea importar. 
    
4. Select **Import runbooks** and **Import Orchestrator encrypted data**. Clear **Counters**, **Schedules**, **Variables**, **Computer Groups**, **Import global configurations**, and **Overwrite existing global configurations**.
    
5. Haga clic en **Finalizar**.
    
6. Edite el runbook **MoveFilesToColdStorage** de la siguiente manera:
    
1. **Move File** activity - set the **Source File** path to the collection file share, for example \\\\Staging\\cases$. Set the **Destination Folder** to the cold storage file share in Azure, for example \\\\AZFile1\\ContentColdStorage. Select **Create a file with a unique name**.
    
2. Actividad **Eliminar carpeta**: establezca la **ruta de acceso:** en el recurso compartido de archivos de la colección, por ejemplo \\\\Staging\\cases$\\*, y seleccione **Eliminar todos los archivos y las subcarpetas**. 
    
7. Implemente el runbook **MoveToColdStorage** usando los procedimientos descritos en[Implementar runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615120).
    
### <a name="sharepoint-on-premises-search-for-cold-storage"></a>Búsqueda local de SharePoint para el almacenamiento en frío

1. Create an new content source in your SharePoint 2013 farm for the cold storage share in Azure, for example \\\\AZFile1\\ContentColdStorage. For more information about managing content sources, see [Add, edit, or delete a content source in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615004)
    
2. Start a full crawl. For more information see, [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).
    
## <a name="using-the-solution"></a>Uso de la solución

There are five major steps in using this solution, assuming you don't want to import the PST files into both Exchange Server 2013 and Exchange Online. This section provides you with the procedures for all of them. Your primary interaction with the solution will be in doing the following:
  
1. Administre la pertenencia de un usuario en el grupo Administradores.
    
2. Review the log files generated by the logon script. The FileCopyErrors.log lists all the files that were not successfully copied. You need to decide what you want to do with them
    
3. Administre el proceso de importación de PST.
    
4. Mover los archivos de la colección a un almacenamiento en frío
    
El resto de los pasos no son específicos para esta solución. Son tareas administrativas estándar que realiza en SharePoint 2013, Microsoft 365 y Azure. Hay elementos para los que esta solución no proporciona ninguna orientación y que tendrá que solucionar en función de las necesidades de su empresa, como:
  
1. El seguimiento de sus casos de eDiscovery y los administradores que están asociados con cada uno
    
2. El seguimiento los conjuntos de colecciones de archivos que están asociados con cada caso de eDiscovery
    
3. La coordinación de la sincronización de los pasos de importación y desplazamiento a un almacenamiento en frío.
    
4. Administrar el espacio de archivo usado en Azure.
    
5. Administrar los buzones en los que se importan los archivos PST.
    
6. La copia de seguridad y restauración de todos los datos locales
    
### <a name="custodian-management"></a>La administración de los administradores

- To start the automated file collection process for an individual user, add them to the Custodians group. The next time that the user logs on, the logon script assigned to the Custodians group through Group Policy will run. 
    
### <a name="monitor-collected-files-and-review-log-files"></a>Supervisar los archivos recopilados y revisar los archivos de registro.

1. Watch the collection file share, for example \\\\Staging\\cases$\\*, for the collection folder from the user. The name of the folder will be formatted like this:  *yyyyMMddHHmm_UserName*  .
    
2. When the collection is completed, open the collection folder, and browse to the _Log folder. In the _Log folder, you will see the following:
    
  - One XML file for every local drive on the user's computer, for example **A.xml**, **C.xml**. These files contain the inventory drives that they are named after, and they are used for the robocopy operation.
    
    > [!NOTE]
    > The collection script will only create an entry in the inventory file for the file types that you defined in the script itself. It will not create an inventory entry for every file on the user's computer. 
  
  - One log file named FileCopyErrors.log for each collection run. This file contains a listing of the files that robocopy could not copy to the file collection share, for example, \\\\Staging\\cases$\\*. You will need to review this and decide what actions to take for these missed files. Usually, you either need to collect them manually if you want them, or you may decide that they are not required and can therefore be omitted from the collection.
    
### <a name="pst-import-option-a-for-exchange-server-2013"></a>Opción A de importación de PST para Exchange Server 2013

1. Log on to the server that hosts the collection file share, for example **Staging**, and open Windows PowerShell. For more information about starting Windows PowerShell, see[Starting Windows PowerShell on Windows Server](https://go.microsoft.com/fwlink/p/?LinkId=615115).
    
2. Set the Execution policy to Unrestricted . Type  `Set-ExecutionPolicy Unrestricted -Scope Process` into Windows PowerShell, and press Enter.
    
3. Run the PSTImportScript.ps1 file, and provide the **$SourcePath** and **$MailboxAlias** parameters. For more information about running Windows PowerShell scripts, see[Running Scripts](https://go.microsoft.com/fwlink/p/?LinkID=615117).
    
4. Revise la salida de errores.
    
5. Before you attempt to import an identically named PST file into the same mailbox, you have to remove the mailbox import request. Run the following command to do that:  `Get-MailboxImportRequest | Remove-MailboxImportRequest`. You will be prompted to remove each individual request from the queue. Respond as needed.
    
### <a name="pst-import-option-b-for-exchange-online"></a>Opción B de importación de PST, para Exchange Online

- Para ubicar los archivos PST recopilados en Exchange Online, siga los procedimientos que se describen en los archivos de importación en Microsoft 365 a través de [carga de red](https://docs.microsoft.com/microsoft-365/compliance/use-network-upload-to-import-pst-files).
    
### <a name="move-to-cold-storage"></a>Mover a un almacenamiento en frío

1. Ejecute el runbook **MoveToColdStorage** usando los procedimientos descritos en [Ejecutar Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615123).
    
2. Watch the Azure file share you are using for long term storage, for example \\\\AZFile1\\ContentColdStorage and the on-premises collection file share, for example \\\\Staging\\cases$. You should see the files and folders appear in the cold storage file share and disappear from the collection file share.
    
### <a name="ediscovery"></a>eDiscovery

1. Either allow the full crawl of the cold storage file share to run as schedules, or initiate a crawl. For more information on starting full or incremental crawls, see [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).
    
2. Cree un caso de eDiscovery en SharePoint 2013 si usó la opción A para la importación de un archivo PST o cree un caso de eDiscovery en SharePoint Online si usó la opción B.
    

