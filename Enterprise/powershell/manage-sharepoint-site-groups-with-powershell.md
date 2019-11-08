---
title: Administrar grupos de sitio de SharePoint Online con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/01/2018
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 'Resumen: Use Office 365 PowerShell para administrar grupos de sitio de SharePoint Online.'
ms.openlocfilehash: 2deaeb2a39b094b828f75a18d4a2c2f06ca79e47
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2019
ms.locfileid: "38031745"
---
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a>Administrar grupos de sitio de SharePoint Online con PowerShell de Office 365

 **Resumen:** Use Office 365 PowerShell para administrar grupos de sitio de SharePoint Online.
  
Aunque puede usar el centro de administración de Microsoft 365, también puede usar Office 365 PowerShell para administrar los grupos de sitio de SharePoint Online.

## <a name="before-you-begin"></a>Antes de empezar

Los procedimientos de este artículo requieren que se conecte a SharePoint Online. Para obtener instrucciones, consulte [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).

## <a name="view-sharepoint-online-with-office-365-powershell"></a>Ver SharePoint Online con Office 365 PowerShell

El centro de administración de SharePoint Online tiene algunos métodos fáciles de usar para administrar grupos de sitio. Por ejemplo, supongamos que desea ver los grupos y los miembros del grupo para el `https://litwareinc.sharepoint.com/sites/finance` sitio. Haga lo siguiente:

1. En el centro de administración de Microsoft 365, haga clic en**sitios**de **recursos** > y, a continuación, haga clic en la dirección URL del sitio.
2. En el cuadro de diálogo Colección de sitios, haga clic en **Ir al sitio**.
3. En la página del sitio, haga clic en el icono **Configuración** (situado en la esquina superior derecha de la página) y después en **Configuración del sitio**:<br/>
![Configuración del sitio de SharePoint Online](media/spo-site-settings.png)<br/>
4. En la página Configuración del sitio, haga clic en la opción **Permisos de los sitios** de **Usuarios y permisos**.

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

Hay dos formas de ejecutar este comando configurado en el símbolo del sistema del shell de administración de SharePoint Online:

- Copie los comandos en el Bloc de notas (u otro editor de texto), modifique el valor de la variable **$siteUrl** , seleccione los comandos y péguelos en el símbolo del sistema del shell de administración de SharePoint Online. Cuando lo haga, PowerShell se detendrá en **>>** un símbolo del sistema. Presione Entrar para ejecutar el comando **foreach**.<br/>
- Copie los comandos en el Bloc de notas (u otro editor de texto), modifique el valor de la variable **$siteURL** y después guarde este archivo de texto con un nombre y la extensión. ps1 en la carpeta adecuada. A continuación, ejecute el script desde el símbolo del sistema del shell de administración de SharePoint Online especificando su ruta de acceso y nombre de archivo. A continuación se muestra un ejemplo:

```
C:\Scripts\SiteGroupsAndUsers.ps1
```

En ambos casos, el resultado será parecido a lo siguiente:

![Grupos de sitio de SharePoint Online](media/SPO-site-groups.png)

Se trata de todos los grupos que se han creado para el `https://litwareinc.sharepoint.com/sites/finance`sitio y de todos los usuarios asignados a dichos grupos. Los nombres de grupo están en amarillo para ayudarle a separar los nombres de los grupos de sus miembros.

Otro ejemplo: a continuación se muestra un conjunto de comandos que enumera los grupos y todas las pertenencias a grupos de todos los sitios de SharePoint Online.

```
$x = Get-SPOSite
foreach ($y in $x)
    {
        Write-Host $y.Url -ForegroundColor "Yellow"
        $z = Get-SPOSiteGroup -Site $y.Url
        foreach ($a in $z)
            {
                 $b = Get-SPOSiteGroup -Site $y.Url -Group $a.Title 
                 Write-Host $b.Title -ForegroundColor "Cyan"
                 $b | Select-Object -ExpandProperty Users
                 Write-Host
            }
    }
```
    
## <a name="see-also"></a>Vea también

[Conectarse a SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[Crear sitios de SharePoint Online y agregar usuarios con PowerShell de Office 365](create-sharepoint-sites-and-add-users-with-powershell.md)

[Administrar usuarios y grupos de SharePoint Online con PowerShell de Office 365](manage-sharepoint-users-and-groups-with-powershell.md)

[Administrar Office 365 con PowerShell de Office 365](manage-office-365-with-office-365-powershell.md)
  
[Introducción a PowerShell de Office 365](getting-started-with-office-365-powershell.md)

