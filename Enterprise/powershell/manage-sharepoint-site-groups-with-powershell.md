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
ms.openlocfilehash: a9fddf33b2f29e7b4e8ed6b86c2433c7ca19a9fc
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915355"
---
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a>Administrar grupos de sitio de SharePoint Online con PowerShell de Office 365

 **Resumen:** Usar PowerShell de Office 365 para administrar grupos de sitio de SharePoint Online.
  
Aunque se puede usar el centro de administración de Office 365, también puede usar Office 365 PowerShell para administrar los grupos de sitio de SharePoint Online.

## <a name="before-you-begin"></a>Antes de empezar

Los procedimientos descritos en este artículo requieren que se va a conectar a SharePoint Online. Para obtener instrucciones, vea [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).

## <a name="view-sharepoint-online-with-office-365-powershell"></a>Vista SharePoint Online con PowerShell de Office 365

El centro de administración de SharePoint Online tiene algunos métodos fáciles de usar para administrar grupos de sitio. Por ejemplo, suponga que desea buscar en los grupos y los miembros del grupo, el `https://litwareinc.sharepoint.com/sites/finance` sitio. Aquí es lo que tiene que hacer para:

1. Desde el centro de administración de Office 365, haga clic en **recursos** > de**sitios**y, a continuación, haga clic en la dirección URL del sitio.
2. En el cuadro de diálogo Colección de sitios, haga clic en **Ir al sitio**.
3. En la página del sitio, haga clic en el icono **Configuración** (situado en la esquina superior derecha de la página) y después en **Configuración del sitio**:</br>
![Configuración del sitio de SharePoint Online](media/spo-site-settings.png)</br>
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

- Copiar los comandos en el Bloc de notas (o en otro editor de texto), modifique el valor de la variable **$siteURL** , seleccione los comandos y, a continuación, péguelos en el símbolo del Shell de administración de SharePoint Online. Cuando lo hace, PowerShell se detendrá en un **>>** símbolo del sistema. Presione ENTRAR para ejecutar el comando **foreach** .</br>
- Copiar los comandos en el Bloc de notas (o en otro editor de texto), modifique el valor de la variable **$siteURL** y, a continuación, guarde este archivo de texto con un nombre y la extensión. ps1 en una carpeta adecuada. A continuación, ejecute la secuencia de comandos desde el símbolo del Shell de administración de SharePoint Online mediante la especificación de su ruta de acceso y nombre de archivo. Este es un comando de ejemplo:

```
C:\Scripts\SiteGroupsAndUsers.ps1
```

En ambos casos, el resultado será parecido a lo siguiente:

![Grupos de sitio de SharePoint Online](media/SPO-site-groups.png)

Estos son todos los grupos que se han creado para el sitio de `https://litwareinc.sharepoint.com/sites/finance`, así como todos los usuarios asignados a esos grupos. Los nombres de grupo se encuentran en amarillo que le ayudarán a los nombres de grupo independiente de sus miembros.

Como otro ejemplo, aquí es un conjunto de comandos que enumera los grupos y todas las pertenencias a grupos, para todos los sitios de SharePoint Online.

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

