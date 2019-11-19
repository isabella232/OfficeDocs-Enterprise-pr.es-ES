---
title: Crear sitios de SharePoint Online y agregar usuarios con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- SPO_Content
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 'Resumen: Use Office 365 PowerShell para crear nuevos sitios de SharePoint Online y, después, agregue usuarios y grupos a esos sitios.'
ms.openlocfilehash: abe8f76de07c230c0d1484ccfb57b3b9a7bf8d34
ms.sourcegitcommit: 21901808f112dd1d8d01617c4be37911efc379f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2019
ms.locfileid: "38707027"
---
# <a name="create-sharepoint-online-sites-and-add-users-with-office-365-powershell"></a>Crear sitios de SharePoint Online y agregar usuarios con PowerShell de Office 365

 **Resumen:** Use Office 365 PowerShell para crear nuevos sitios de SharePoint Online y, después, agregue usuarios y grupos a esos sitios.

Cuando usa Office 365 PowerShell para crear sitios de SharePoint Online y agregar usuarios, puede realizar tareas de forma rápida y repetida en gran medida de la velocidad que puede hacerlo en el centro de administración de Office 356. También puede efectuar tareas que no se pueden llevar a cabo en el Centro de administración de Office 365. 

## <a name="before-you-begin"></a>Antes de empezar

Los procedimientos de este tema requieren que se conecte a SharePoint Online. Para obtener instrucciones, vea [conectarse a PowerShell de SharePoint Online](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

## <a name="step-1-create-new-site-collections-using-office-365-powershell"></a>Paso 1: crear colecciones de sitios con Office 365 PowerShell

Cree varios sitios con Office 365 PowerShell y un archivo. csv que cree con el código de ejemplo proporcionado y el Bloc de notas. Para este procedimiento, reemplazará la información de marcador de posición que se muestra entre corchetes con su propia información de sitio y espacio empresarial específica. Este proceso le permite crear un único archivo y ejecutar un único comando de PowerShell de Office 365 que usa ese archivo. Esto hace que las acciones se tomen repetibles y se puedan reportar y elimina muchos errores, si no todos, que pueden venir de escribir comandos largos en el shell de administración de SharePoint Online. Este procedimiento consta de dos partes. En primer lugar, creará un archivo. csv y, a continuación, hará referencia a ese archivo. csv con Office 365 PowerShell, que usará su contenido para crear los sitios.

El cmdlet de Office 365 PowerShell importa el archivo .csv y lo canaliza en un bucle entre llaves que lee la primera línea del archivo como encabezados de columna. Luego, el cmdlet de Office 365 PowerShell itera en el resto de los registros, crea una colección de sitios para cada uno de ellos y asigna propiedades a la colección de sitios en función de los encabezados de columna.

### <a name="create-a-csv-file"></a>Crear un archivo .csv

1. Abra el Bloc de notas y pegue el siguiente bloque de texto:<br/>

```powershell
Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
```
<br/>Donde *tenant* es el nombre del espacio empresarial y *propietario* es el nombre del usuario del inquilino al que desea conceder la función de administrador de la colección de sitios primaria.<br/>(Puede presionar CTRL + H cuando use el Bloc de notas para reemplazarla en masa de forma más rápida).<br/>

2. Guarde el archivo en el escritorio como **SiteCollections. csv**.<br/>

> [!TIP]
> Antes de usar este o cualquier otro archivo .csv, o bien un archivo de script de Windows PowerShell, conviene asegurarse de que no contiene caracteres extraños o no imprimibles. Abra el archivo en Word y, en la cinta de opciones, haga clic en el icono de párrafo para mostrar los caracteres no imprimibles. No debe haber ningún carácter extraño o no imprimible. Por ejemplo, no debe haber ninguna marca de párrafo después del último carácter al final del archivo.

### <a name="run-the-windows-powershell-command"></a>Ejecutar el comando de Windows PowerShell

1. En el símbolo del sistema de Windows PowerShell, escriba o copie y pegue el siguiente cmdlet y presione ENTRAR:<br/>
```powershell
Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {New-SPOSite -Owner $_.Owner -StorageQuota $_.StorageQuota -Url $_.Url -NoWait -ResourceQuota $_.ResourceQuota -Template $_.Template -TimeZoneID $_.TimeZoneID -Title $_.Name}
```
<br/>Donde *alias* es igual al alias del usuario.<br/>

2. Espere a que el símbolo del sistema de Windows PowerShell aparezca de nuevo. Esto puede tardar un par de minutos.<br/>

3. En el símbolo del sistema de Windows PowerShell, escriba o copie y pegue el siguiente cmdlet y presione ENTRAR:<br/>

```powershell
Get-SPOSite -Detailed | Format-Table -AutoSize
```
<br/>

4. Observe que las nuevas colecciones de sitios figuran en la lista. Debe ver las siguientes colecciones de sitios: **contosotest**, **TeamSite01**, **Blog01**y **Project01**

Eso es todo. Ha creado varias colecciones de sitios con el archivo .csv que creó anteriormente y un único cmdlet de Windows PowerShell. Ya está listo para crear y asignar usuarios a estos sitios.

## <a name="step-2-add-users-and-groups"></a>Paso 2: agregar usuarios y grupos

Ahora vamos a crear usuarios y a agregarlos a un grupo de colecciones de sitios. Luego, usaremos un archivo .csv para cargar los nuevos usuarios y grupos de forma masiva.

En estos procedimientos se da por hecho que ya se han creado las colecciones de sitios contosotest, TeamSite01, Blog01 y Project01.

### <a name="create-csv-and-ps1-files"></a>Crear los archivos .csv y .ps1

1. Abra el Bloc de notas y pegue el siguiente bloque de texto:<br/>
```powershell
Site,Group,PermissionLevels
https://tenant.sharepoint.com/sites/contosotest,Contoso Project Leads,Full Control
https://tenant.sharepoint.com/sites/contosotest,Contoso Auditors,View Only
https://tenant.sharepoint.com/sites/contosotest,Contoso Designers,Design
https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
https://tenant.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
```
<br/>Donde *tenant* es el nombre del espacio empresarial.<br/>

2. Guarde el archivo en el escritorio como **GroupsAndPermissions. csv**.<br/>

3. Abra otra instancia del Bloc de notas y pegue el siguiente bloque de texto:<br/>

```powershell
Group,LoginName,Site
Contoso Project Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest
Contoso Auditors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest
Contoso Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest
XT1000 Team Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
XT1000 Advisors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
Contoso Blog Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
Contoso Blog Editors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
Project Alpha Approvers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Project01
```
<br/>Donde *tenant* es el nombre del inquilino y *username* es el nombre de usuario de un usuario existente.<br/>

4. Guarde el archivo en el escritorio como **users. csv**.<br/>

5. Abra otra instancia del Bloc de notas y pegue el siguiente bloque de texto:<br/>

```powershell
Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\users\MyAlias\desktop\Users.csv | where {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```
<br/>Donde alias es igual al nombre del usuario que ha iniciado sesión actualmente.<br/>

6. Guarde el archivo en el escritorio como **UsersAndGroups. PS1**. Este es un script de Windows PowerShell sencillo.

Ya puede ejecutar el script UsersAndGroup.ps1 para agregar usuarios y grupos a varias colecciones de sitios.

### <a name="run-usersandgroupsps1-script"></a>Ejecutar el script UsersAndGroups.ps1

1. Vuelva al Shell de administración de SharePoint Online.<br/>
2. En el símbolo del sistema de Windows PowerShell, escriba o copie y pegue la siguiente línea y presione ENTRAR:<br/>
```powershell
Set-ExecutionPolicy Bypass
```
<br/>

3. En el mensaje de confirmación, presione **s**.<br/>

4. En el símbolo del sistema de Windows PowerShell, escriba o copie y pegue lo siguiente y presione ENTRAR:<br/>

```powershell
c:\users\MyAlias\desktop\UsersAndGroups.ps1
```
<br/>Donde *alias* es igual al nombre de usuario.<br/>

5. Antes de continuar, espere a que el símbolo del sistema vuelva. Primero verá que los grupos aparecen según se han creado y, luego, verá la lista de grupos repetida a medida que se vayan agregando usuarios.

## <a name="see-also"></a>Vea también

[Conectarse a SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[Administración de grupos de sitio de SharePoint Online Office 365 PowerShell](manage-sharepoint-site-groups-with-powershell.md)

[Administrar Office 365 con PowerShell de Office 365](manage-office-365-with-office-365-powershell.md)
  
[Introducción a PowerShell de Office 365](getting-started-with-office-365-powershell.md)

