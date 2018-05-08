---
title: Administrar usuarios y grupos de SharePoint Online con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/07/2018
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 'Resumen: Use PowerShell de Office 365 para administrar usuarios, grupos y sitios de SharePoint Online.'
ms.openlocfilehash: a04bf1538d6f56b760932b5be89b1953fcaa33d5
ms.sourcegitcommit: 5c5489db5d1000296945c9774198bd911bee4f14
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="manage-sharepoint-online-users-and-groups-with-office-365-powershell"></a>Administrar usuarios y grupos de SharePoint Online con PowerShell de Office 365

 **Resumen:** Usar PowerShell de Office 365 para administrar usuarios, grupos y sitios de SharePoint Online.

Si es un administrador de SharePoint Online que funciona con listas de gran tamaño de las cuentas de usuario o grupos y desea una manera más fácil de administrar ellos, puede usar PowerShell de Office 365. 

## <a name="before-you-begin"></a>Antes de empezar

Los procedimientos descritos en este tema requieren que se va a conectar a SharePoint Online. Para obtener instrucciones, vea [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

## <a name="get-a-list-of-sites-groups-and-users"></a>Obtener una lista de sitios, grupos y usuarios

Antes de empezar a administrar usuarios y grupos, hay que conseguir las listas de los sitios, grupos y usuarios. Después puede usar esta información para trabajar con el ejemplo de este artículo.

### <a name="get-a-list-of-sites"></a>Conseguir una lista de sitios

Obtenga la lista de los sitios de su inquilino con este comando:

```
Get-SPOSite
```

### <a name="get-a-list-of-groups"></a>Conseguir una lista de grupos

Obtenga la lista de los grupos de su inquilino con este comando:

```
Get-SPOSite | ForEach {Get-SPOSiteGroup -Site $_.Url} | Format-Table
```

### <a name="get-a-list-of-users"></a>Conseguir una lista de usuarios

Obtenga la lista de los usuarios de su inquilino con este comando:

```
Get-SPOSite | ForEach {Get-SPOUser -Site $_.Url}
```

## <a name="add-a-user-to-the-site-collection-administrators-group"></a>Agregar un usuario al grupo Administradores de la colección de sitios

Use el comando **Set-SPOUser** para agregar un usuario a la lista de administradores de colección de sitios en una colección de sitios. Este es el aspecto de la sintaxis:

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
 ```

Para usar estos comandos, replace reemplace todo el contenido de las comillas, incluido el < y > caracteres, con los nombres correctos.

Por ejemplo, este conjunto de comandos agrega Opal Castillo (opalc de nombre de usuario) la lista de administradores de colección de sitios en la colección de sitios ContosoTest en el inquilino contoso1:

```
$tenant = "contoso1"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
```

Puede copiar y pegar estos comandos en el Bloc de notas, cambie los valores de las variables para $tenant, $site y $user a los valores reales del entorno y, a continuación, pegue esto en la ventana de la consola de administración de SharePoint Online para ejecutarlas.

## <a name="add-a-user-to-other-site-collection-administrators-groups"></a>Agregar un usuario a otros grupos de administradores de la colección de sitios

En esta tarea, se usará el comando **Add-SPOUser** para agregar un usuario a un grupo de SharePoint en una colección de sitios.

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site

```

Por ejemplo, vamos a agregar Glen abundan (glenr de nombre de usuario) al grupo en la colección de sitios ContosoTest en el inquilino contoso1 auditores:

```
$tenant = "contoso1"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a>Crear un grupo de colecciones de sitios

Use el comando **Set-SPOSiteGroup** para crear un nuevo grupo de SharePoint y agregarlo a la colección de sitios ContosoTest.

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$group = "<group name name, such as Auditors>"
$level = "<permission level, such as View Only>"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```
Las propiedades de grupo, como los niveles de permisos se pueden actualizar más adelante mediante el cmdlet **Set-SPOSiteGroup** .

Por ejemplo, vamos a agregar el grupo auditores con permisos de sólo lectura a la colección de sitios de prueba de Contoso en el inquilino contoso1:

```
$tenant = "contoso1"
$site = "Contoso Test"
$group = "Auditors"
$level = "View Only"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a>Quitar usuarios de un grupo

A veces, es necesario quitar un usuario de un sitio o incluso de todos los sitios. Tal vez el empleado se mueva de una división a otra o abandone la compañía. Puede hacer esto fácilmente para un empleado en la interfaz de usuario, pero no es tan fácil cuando hay que mover una división completa de un sitio a otro.

Sin embargo, mediante el uso de los archivos de Shell de administración de SharePoint Online y CSV, esto es rápido y fácil. En esta tarea, debe usar Windows PowerShell para quitar un usuario de un grupo de seguridad de la colección de sitios. A continuación, podrá usar un archivo CSV y quitar una gran cantidad de usuarios de sitios diferentes. 

Se se van a usar el comando **Remove-SPOUser** para quitar un único usuario de Office 365 de un grupo de la colección de sitios sólo para poder ver la sintaxis del comando. Aquí es el aspecto de la sintaxis:

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```
Por ejemplo, vamos a quitar Bobby Overby desde el grupo de auditores de colección de sitios en la colección de sitios de prueba de Contoso en el inquilino contoso1:

```
$tenant = "contoso1"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

Supongamos que quisiéramos quitar a Bobby de todos los grupos a los que pertenece. Este es el método que usaríamos para hacerlo:

```
$tenant = "contoso1"
$user = "bobbyo"
Get-SPOSite | ForEach {Get-SPOSiteGroup –Site $_.Url} | ForEach {Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site &_.Url}
```

> [!WARNING]
> Esto es sólo un ejemplo. No se debe ejecutar este comando, a menos que realmente necesita que quitar un usuario de cada grupo, por ejemplo, si el usuario abandona la compañía.

## <a name="automate-management-of-large-lists-of-users-and-groups"></a>Automatizar la administración de grandes listas de usuarios y grupos

Para agregar un gran número de cuentas para los sitios de SharePoint y conceda permisos, puede usar el centro de administración de Office 365, los comandos de PowerShell individuales o PowerShell un un archivo CSV. De estas opciones, el archivo CSV es la forma más rápida para automatizar esta tarea.

El proceso básico es crear un archivo CSV que tiene encabezados (columnas) que se corresponden con los parámetros que necesita la secuencia de comandos de Windows PowerShell. Puede crear fácilmente como una lista en Excel y, a continuación, se exporta como un archivo CSV. A continuación, use un script de Windows PowerShell para iterar a través de registros (filas) en el archivo CSV, agregar los usuarios a grupos y los grupos a los sitios. 

Por ejemplo, vamos a crear un archivo CSV para definir un grupo de colecciones de sitios, grupos y permisos. A continuación, vamos a crear un archivo CSV para rellenar los grupos con usuarios. Por último, vamos a crear y ejecutar un script de Windows PowerShell que cree y rellene los grupos.

El primer archivo CSV agregará uno o más grupos a una o más colecciones de sitios y tendrá esta estructura:

### <a name="header"></a>Encabezado:

```
Site,Group,PermissionLevels
```

### <a name="item"></a>Elemento:

```
https://tenant.sharepoint.com/sites/site,group,level
```

Este es un archivo de ejemplo:

```
Site,Group,PermissionLevels
https://contoso1.sharepoint.com/sites/contosotest,Contoso Project Leads,Full Control
https://contoso1.sharepoint.com/sites/contosotest,Contoso Auditors,View Only
https://contoso1.sharepoint.com/sites/contosotest,Contoso Designers,Design
https://contoso1.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
https://contoso1.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
https://contoso1.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
https://contoso1.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
https://contoso1.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
```

El segundo archivo CSV agregará uno o varios usuarios a uno o varios grupos y tendrá esta estructura:

### <a name="header"></a>Encabezado:

```
Group,LoginName,Site
```

### <a name="item"></a>Elemento:

```
group,login,https://tenant.sharepoint.com/sites/site
```

Este es un archivo de ejemplo:

```
Group,LoginName,Site
Contoso Project Leads,bobbyo@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/contosotest
Contoso Auditors,allieb@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/contosotest
Contoso Designers,bonniek@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/contosotest
XT1000 Team Leads,dorenap@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/TeamSite01
XT1000 Advisors,garthf@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/TeamSite01
Contoso Blog Designers,janets@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/Blog01
Contoso Blog Editors,opalc@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/Blog01
Project Alpha Approvers,robinc@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/Project01
```

Para el siguiente paso, debe tener los dos archivos CSV guardados en la unidad. Aquí están los comandos de ejemplo que usan ambos archivos CSV y para agregar permisos y la pertenencia al grupo:

```
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

La secuencia de comandos importa el contenido del archivo CSV y utiliza los valores de las columnas para rellenar los parámetros de los comandos **New-SPOSiteGroup** y **Add-SPOUser** . En nuestro ejemplo, también ahorramos esto a la carpeta theO365Admin en la unidad C, pero puede guardar siempre que lo desee.

Ahora, vamos a quitar un montón de personas para varios grupos en distintos sitios con el mismo archivo CSV. Este es un comando de ejemplo:

```
Import-Csv C:\O365Admin\Users.csv | ForEach {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a>Generar informes de usuario

Tal vez desee obtener un informe sencillo para unos cuantos sitios y mostrar los usuarios de dichos sitios, su nivel de permisos y otras propiedades. Este es el aspecto de la sintaxis:

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

Esto va a obtener los datos para estos tres sitios y escribirlos en un archivo de texto en la unidad local. Tenga en cuenta que el parámetro – Append va a agregar nuevo contenido a un archivo existente.

Por ejemplo, vamos a ejecutar un informe en los sitios ContosoTest, TeamSite01 y Project01 para el inquilino Contoso1:

```
$tenant = "contoso1"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

Tenga en cuenta que hemos tenido que cambiar sólo la variable **$site** . La variable **$tenant** mantiene su valor a través de todas las ejecuciones de tres del comando.

Sin embargo, ¿qué pasa si quisiera hacer esto para cada sitio? Puede hacerlo sin tener que escribir todos los sitios web con este comando:

```
Get-SPOSite | ForEach {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

Este informe es bastante sencilla, y puede agregar más código para crear informes de más específica o informes que incluyen información más detallada. Pero esto debería darle una idea de cómo usar el Shell de administración de SharePoint Online para administrar usuarios en el entorno de SharePoint Online.
   
## <a name="see-also"></a>Ver también

[Conectarse a SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[Administrar SharePoint Online con PowerShell de Office 365](create-sharepoint-sites-and-add-users-with-powershell.md)

[Administrar Office 365 con PowerShell de Office 365](manage-office-365-with-office-365-powershell.md)
  
[Introducción a PowerShell de Office 365](getting-started-with-office-365-powershell.md)

