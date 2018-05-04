---
title: Administrar grupos de sitio de SharePoint Online con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/01/2018
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 'Resumen: Use PowerShell de Office 365 para administrar grupos de sitio de SharePoint Online.'
ms.openlocfilehash: 68be9ce3ef26cb46df6d43716c6719ffd9c172e2
ms.sourcegitcommit: 74cdb2534bce376abc9cf4fef85ff039c46ee790
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a>Administrar grupos de sitio de SharePoint Online con PowerShell de Office 365

 **Resumen:** Usar PowerShell de Office 365 para administrar grupos de sitio de SharePoint Online.
  
Aunque se puede usar el centro de administración de Office 365, también puede usar Office 365 PowerShell para administrar los grupos de sitio de SharePoint Online.

## <a name="before-you-begin"></a>Antes de empezar

Los procedimientos descritos en este artículo requieren que se va a conectar a SharePoint Online. Para obtener instrucciones, vea [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).

## <a name="view-sharepoint-online-with-office-365-powershell"></a>Vista SharePoint Online con PowerShell de Office 365

El centro de administración de SharePoint Online tiene algunos métodos fáciles de usar para administrar grupos de sitio. Por ejemplo, suponga que desea buscar en los grupos y los miembros del grupo, el https://litwareinc.sharepoint.com/sites/finance sitio. Aquí es lo que tiene que hacer para:

1. Desde el centro de administración de Office 365, haga clic en **recursos** > de**sitios**y, a continuación, haga clic en la dirección URL del sitio.
2. En el cuadro de diálogo de colección de sitios, haga clic en **Ir a este sitio**.
3. En la página del sitio, haga clic en el icono de **configuración** (que se encuentra en la esquina superior derecha de la página) y, a continuación, haga clic en **Configuración del sitio**:</br>
![Configuración del sitio de SharePoint Online](images/spo-site-settings.png)</br>
4. En la página Configuración del sitio, haga clic en **permisos de sitios** , en **usuarios y permisos**.

Y, así, repita el proceso con el siguiente sitio que quiera ver.

Para obtener una lista de los grupos con PowerShell de Office 365, use el siguiente conjunto de comandos:

```
$siteURL = "https://litwareinc.sharepoint.com/sites/finance"
$x = Get-SPOSiteGroup -Site $siteURL
foreach ($y in $x)
    {
        Write-Host $y.Title -ForegroundColor "Yellow"
        Get-SPOSiteGroup -Site $siteURL -Group $y.Title | Select-Object -ExpandProperty Users
        Write-Host
    }
```

Hay dos formas de ejecutar este comando establecer en el símbolo del Shell de administración de SharePoint Online:
- Copiar los comandos en el Bloc de notas (o en otro editor de texto), modifique el valor de la variable **$siteURL** , seleccione los comandos y, a continuación, péguelos en el símbolo del Shell de administración de SharePoint Online. Cuando lo hace, PowerShell se detendrá en un >> símbolo del sistema. Presione ENTRAR para ejecutar el para cada comando.</br>
- Copiar los comandos en el Bloc de notas (o en otro editor de texto), modifique el valor de la variable **$siteURL** y, a continuación, guarde este archivo de texto con un nombre y la extensión. ps1 en una carpeta adecuada. A continuación, ejecute la secuencia de comandos desde el símbolo del Shell de administración de SharePoint Online mediante la especificación de su ruta de acceso y nombre de archivo. Este es un ejemplo:</br>
```
C:\Scripts\SiteGroupsAndUsers.ps1
```</br>

In both cases, you should see something similar to this:

![SharePoint Online site groups](images/SPO-site-groups.png)

These are all the groups that have been created for the site https://litwareinc.sharepoint.com/sites/finance, as well as all the users assigned to those groups. The group names are in yellow to help you separate group names from their members.

As another example, here is a command set that lists the groups, and all the group memberships, for all of your SharePoint Online sites.

```
$x = get-SPOSite foreach ($y en $x) {Write-Host $y.Url - ForegroundColor "amarillo" $z = Get-SPOSiteGroup-sitio $y.Url foreach ($un $z en) {$b = Get-SPOSiteGroup-$y.Url del sitio-grupo $a.Title Write-Host $b.Title - ForegroundColor "Cian" $b | Escritura de los usuarios de Select-Object - ExpandProperty-Host}}
```
    
## See also

[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[Create SharePoint Online sites and add users with Office 365 PowerShell](create-sharepoint-sites-and-add-users-with-powershell.md)

[Manage SharePoint Online users and groups with Office 365 PowerShell](manage-sharepoint-users-and-groups-with-powershell.md)

[Manage Office 365 with Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Getting started with Office 365 PowerShell](getting-started-with-office-365-powershell.md)

