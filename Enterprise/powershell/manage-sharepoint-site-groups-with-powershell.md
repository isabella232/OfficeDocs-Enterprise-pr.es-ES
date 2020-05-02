---
title: Administrar grupos de sitio de SharePoint Online con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/17/2019
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- SPO_Content
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 'Resumen: Use Office 365 PowerShell para administrar grupos de sitio de SharePoint Online.'
ms.openlocfilehash: 3a1b999470746cbe02ec52fe888ea26b59cd423b
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004203"
---
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a><span data-ttu-id="7d16b-103">Administrar grupos de sitio de SharePoint Online con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="7d16b-103">Manage SharePoint Online site groups with Office 365 PowerShell</span></span>

<span data-ttu-id="7d16b-104">Aunque puede usar el centro de administración de Microsoft 365, también puede usar Office 365 PowerShell para administrar los grupos de sitio de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="7d16b-104">Although you can use the Microsoft 365 admin center, you can also use Office 365 PowerShell to manage your SharePoint Online site groups.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="7d16b-105">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="7d16b-105">Before you begin</span></span>

<span data-ttu-id="7d16b-106">Los procedimientos de este artículo requieren que se conecte a SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="7d16b-106">The procedures in this article require you to connect to SharePoint Online.</span></span> <span data-ttu-id="7d16b-107">Para obtener instrucciones, consulte [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span><span class="sxs-lookup"><span data-stu-id="7d16b-107">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>

## <a name="view-sharepoint-online-with-office-365-powershell"></a><span data-ttu-id="7d16b-108">Ver SharePoint Online con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="7d16b-108">View SharePoint Online with Office 365 PowerShell</span></span>

<span data-ttu-id="7d16b-109">El centro de administración de SharePoint Online tiene algunos métodos fáciles de usar para administrar grupos de sitio.</span><span class="sxs-lookup"><span data-stu-id="7d16b-109">The SharePoint Online admin center has some easy-to-use methods for managing site groups.</span></span> <span data-ttu-id="7d16b-110">Por ejemplo, supongamos que desea ver los grupos y los miembros del grupo para el `https://litwareinc.sharepoint.com/sites/finance` sitio.</span><span class="sxs-lookup"><span data-stu-id="7d16b-110">For example, suppose you want to look at the groups, and the group members, for the `https://litwareinc.sharepoint.com/sites/finance` site.</span></span> <span data-ttu-id="7d16b-111">Haga lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="7d16b-111">Here’s what you have to do to:</span></span>

1. <span data-ttu-id="7d16b-112">En el centro de administración de SharePoint, haga clic en **sitios activos**y, a continuación, haga clic en la dirección URL del sitio.</span><span class="sxs-lookup"><span data-stu-id="7d16b-112">From the SharePoint admin center, click **Active sites**, and then click the URL of the site.</span></span>
2. <span data-ttu-id="7d16b-113">En la página sitio, haga clic en el icono **configuración** (situado en la esquina superior derecha de la página) y, a continuación, haga clic en **permisos del sitio**.</span><span class="sxs-lookup"><span data-stu-id="7d16b-113">On the site page, click the **Settings** icon (located in the upper right-hand corner of the page), and then click **Site permissions**.</span></span>

<span data-ttu-id="7d16b-114">Y, así, repita el proceso con el siguiente sitio que quiera ver.</span><span class="sxs-lookup"><span data-stu-id="7d16b-114">And then repeat the process for the next site you want to look at.</span></span>

<span data-ttu-id="7d16b-115">Para obtener una lista de los grupos con Office 365 PowerShell, puede usar los siguientes comandos:</span><span class="sxs-lookup"><span data-stu-id="7d16b-115">To get a list of the groups with Office 365 PowerShell, you can use the following commands:</span></span>

```powershell
$siteURL = "https://litwareinc.sharepoint.com/sites/finance"
$x = Get-SPOSiteGroup -Site $siteURL
foreach ($y in $x)
    {
        Write-Host $y.Title -ForegroundColor "Yellow"
        Get-SPOSiteGroup -Site $siteURL -Group $y.Title | Select-Object -ExpandProperty Users
        Write-Host
    }
```

<span data-ttu-id="7d16b-116">Hay dos formas de ejecutar este comando configurado en el símbolo del sistema del shell de administración de SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="7d16b-116">There are two ways to run this command set in the SharePoint Online Management Shell command prompt:</span></span>

- <span data-ttu-id="7d16b-117">Copie los comandos en el Bloc de notas (u otro editor de texto), modifique el valor de la variable **$siteUrl** , seleccione los comandos y péguelos en el símbolo del sistema del shell de administración de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="7d16b-117">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, select the commands, and then paste them into the SharePoint Online Management Shell command prompt.</span></span> <span data-ttu-id="7d16b-118">Cuando lo haga, PowerShell se detendrá en **>>** un símbolo del sistema.</span><span class="sxs-lookup"><span data-stu-id="7d16b-118">When you do, PowerShell will stop at a **>>** prompt.</span></span> <span data-ttu-id="7d16b-119">Presione Entrar para ejecutar el `foreach` comando.</span><span class="sxs-lookup"><span data-stu-id="7d16b-119">Press Enter to execute the `foreach` command.</span></span><br/>
- <span data-ttu-id="7d16b-120">Copie los comandos en el Bloc de notas (u otro editor de texto), modifique el valor de la variable **$siteURL** y después guarde este archivo de texto con un nombre y la extensión. ps1 en la carpeta adecuada.</span><span class="sxs-lookup"><span data-stu-id="7d16b-120">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, and then save this text file with a name and the .ps1 extension in a suitable folder.</span></span> <span data-ttu-id="7d16b-121">A continuación, ejecute el script desde el símbolo del sistema del shell de administración de SharePoint Online especificando su ruta de acceso y nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="7d16b-121">Next, run the script from the SharePoint Online Management Shell command prompt by specifying its path and file name.</span></span> <span data-ttu-id="7d16b-122">A continuación se muestra un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="7d16b-122">Here is an example command:</span></span>

```powershell
C:\Scripts\SiteGroupsAndUsers.ps1
```

<span data-ttu-id="7d16b-123">En ambos casos, el resultado será parecido a lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="7d16b-123">In both cases, you should see something similar to this:</span></span>

![Grupos de sitio de SharePoint Online](media/SPO-site-groups.png)

<span data-ttu-id="7d16b-125">Se trata de todos los grupos que se han creado para el `https://litwareinc.sharepoint.com/sites/finance`sitio y de todos los usuarios asignados a dichos grupos.</span><span class="sxs-lookup"><span data-stu-id="7d16b-125">These are all the groups that have been created for the site `https://litwareinc.sharepoint.com/sites/finance`, and all the users assigned to those groups.</span></span> <span data-ttu-id="7d16b-126">Los nombres de grupo están en amarillo para ayudarle a separar los nombres de los grupos de sus miembros.</span><span class="sxs-lookup"><span data-stu-id="7d16b-126">The group names are in yellow to help you separate group names from their members.</span></span>

<span data-ttu-id="7d16b-127">Otro ejemplo: a continuación se muestra un conjunto de comandos que enumera los grupos y todas las pertenencias a grupos de todos los sitios de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="7d16b-127">As another example, here is a command set that lists the groups, and all the group memberships, for all of your SharePoint Online sites.</span></span>

```powershell
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
    
## <a name="see-also"></a><span data-ttu-id="7d16b-128">Consulte también</span><span class="sxs-lookup"><span data-stu-id="7d16b-128">See also</span></span>

[<span data-ttu-id="7d16b-129">Conectarse a SharePoint Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="7d16b-129">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="7d16b-130">Crear sitios de SharePoint Online y agregar usuarios con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="7d16b-130">Create SharePoint Online sites and add users with Office 365 PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

[<span data-ttu-id="7d16b-131">Administrar usuarios y grupos de SharePoint Online con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="7d16b-131">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>](manage-sharepoint-users-and-groups-with-powershell.md)

[<span data-ttu-id="7d16b-132">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="7d16b-132">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="7d16b-133">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="7d16b-133">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

