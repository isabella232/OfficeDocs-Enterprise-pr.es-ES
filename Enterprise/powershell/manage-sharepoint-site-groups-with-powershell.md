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
- SPO_Content
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 'Resumen: Use Office 365 PowerShell para administrar grupos de sitio de SharePoint Online.'
ms.openlocfilehash: 7eb8a472cb021fb2b78468a9100282b72c1b88cb
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2019
ms.locfileid: "38748540"
---
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a><span data-ttu-id="7b18d-103">Administrar grupos de sitio de SharePoint Online con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="7b18d-103">Manage SharePoint Online site groups with Office 365 PowerShell</span></span>

<span data-ttu-id="7b18d-104">Aunque puede usar el centro de administración de Microsoft 365, también puede usar Office 365 PowerShell para administrar los grupos de sitio de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="7b18d-104">Although you can use the Microsoft 365 admin center, you can also use Office 365 PowerShell to manage your SharePoint Online site groups.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="7b18d-105">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="7b18d-105">Before you begin</span></span>

<span data-ttu-id="7b18d-106">Los procedimientos de este artículo requieren que se conecte a SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="7b18d-106">The procedures in this article require you to connect to SharePoint Online.</span></span> <span data-ttu-id="7b18d-107">Para obtener instrucciones, consulte [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span><span class="sxs-lookup"><span data-stu-id="7b18d-107">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>

## <a name="view-sharepoint-online-with-office-365-powershell"></a><span data-ttu-id="7b18d-108">Ver SharePoint Online con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="7b18d-108">View SharePoint Online with Office 365 PowerShell</span></span>

<span data-ttu-id="7b18d-109">El centro de administración de SharePoint Online tiene algunos métodos fáciles de usar para administrar grupos de sitio.</span><span class="sxs-lookup"><span data-stu-id="7b18d-109">The SharePoint Online admin center has some easy-to-use methods for managing site groups.</span></span> <span data-ttu-id="7b18d-110">Por ejemplo, supongamos que desea ver los grupos y los miembros del grupo para el `https://litwareinc.sharepoint.com/sites/finance` sitio.</span><span class="sxs-lookup"><span data-stu-id="7b18d-110">For example, suppose you want to look at the groups, and the group members, for the `https://litwareinc.sharepoint.com/sites/finance` site.</span></span> <span data-ttu-id="7b18d-111">Haga lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="7b18d-111">Here’s what you have to do to:</span></span>

1. <span data-ttu-id="7b18d-112">En el centro de administración de Microsoft 365, haga clic en**sitios**de **recursos** > y, a continuación, haga clic en la dirección URL del sitio.</span><span class="sxs-lookup"><span data-stu-id="7b18d-112">From the Microsoft 365 admin center, click **Resources** > **Sites**, and then click the URL of the site.</span></span>
2. <span data-ttu-id="7b18d-113">En el cuadro de diálogo Colección de sitios, haga clic en **Ir al sitio**.</span><span class="sxs-lookup"><span data-stu-id="7b18d-113">In the site collection dialog box, click **Go to this site**.</span></span>
3. <span data-ttu-id="7b18d-114">En la página del sitio, haga clic en el icono **Configuración** (situado en la esquina superior derecha de la página) y después en **Configuración del sitio**:</span><span class="sxs-lookup"><span data-stu-id="7b18d-114">On the site page, click the **Settings** icon (located in the upper right-hand corner of the page) and then click **Site settings**:</span></span><br/>
<span data-ttu-id="7b18d-115">![Configuración del sitio de SharePoint Online](media/spo-site-settings.png)</span><span class="sxs-lookup"><span data-stu-id="7b18d-115">![SharePoint Online site settings](media/spo-site-settings.png)</span></span><br/>
4. <span data-ttu-id="7b18d-116">En la página Configuración del sitio, haga clic en la opción **Permisos de los sitios** de **Usuarios y permisos**.</span><span class="sxs-lookup"><span data-stu-id="7b18d-116">On the Site Settings page, click **Sites permissions** under **Users and Permissions**.</span></span>

<span data-ttu-id="7b18d-117">Y, así, repita el proceso con el siguiente sitio que quiera ver.</span><span class="sxs-lookup"><span data-stu-id="7b18d-117">And then repeat the process for the next site you want to look at.</span></span>

<span data-ttu-id="7b18d-118">Para obtener una lista de los grupos con PowerShell de Office 365, use el siguiente conjunto de comandos:</span><span class="sxs-lookup"><span data-stu-id="7b18d-118">To get a list of the groups with Office 365 PowerShell, you would use the following command set:</span></span>

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

<span data-ttu-id="7b18d-119">Hay dos formas de ejecutar este comando configurado en el símbolo del sistema del shell de administración de SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="7b18d-119">There are two ways to run this command set in the SharePoint Online Management Shell command prompt:</span></span>

- <span data-ttu-id="7b18d-120">Copie los comandos en el Bloc de notas (u otro editor de texto), modifique el valor de la variable **$siteUrl** , seleccione los comandos y péguelos en el símbolo del sistema del shell de administración de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="7b18d-120">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, select the commands, and then paste them into the SharePoint Online Management Shell command prompt.</span></span> <span data-ttu-id="7b18d-121">Cuando lo haga, PowerShell se detendrá en **>>** un símbolo del sistema.</span><span class="sxs-lookup"><span data-stu-id="7b18d-121">When you do, PowerShell will stop at a **>>** prompt.</span></span> <span data-ttu-id="7b18d-122">Presione Entrar para ejecutar el comando **foreach**.</span><span class="sxs-lookup"><span data-stu-id="7b18d-122">Press Enter to execute the **foreach** command.</span></span><br/>
- <span data-ttu-id="7b18d-123">Copie los comandos en el Bloc de notas (u otro editor de texto), modifique el valor de la variable **$siteURL** y después guarde este archivo de texto con un nombre y la extensión. ps1 en la carpeta adecuada.</span><span class="sxs-lookup"><span data-stu-id="7b18d-123">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, and then save this text file with a name and the .ps1 extension in a suitable folder.</span></span> <span data-ttu-id="7b18d-124">A continuación, ejecute el script desde el símbolo del sistema del shell de administración de SharePoint Online especificando su ruta de acceso y nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="7b18d-124">Next, run the script from the SharePoint Online Management Shell command prompt by specifying its path and file name.</span></span> <span data-ttu-id="7b18d-125">A continuación se muestra un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="7b18d-125">Here is an example command:</span></span>

```powershell
C:\Scripts\SiteGroupsAndUsers.ps1
```

<span data-ttu-id="7b18d-126">En ambos casos, el resultado será parecido a lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="7b18d-126">In both cases, you should see something similar to this:</span></span>

![Grupos de sitio de SharePoint Online](media/SPO-site-groups.png)

<span data-ttu-id="7b18d-128">Se trata de todos los grupos que se han creado para el `https://litwareinc.sharepoint.com/sites/finance`sitio y de todos los usuarios asignados a dichos grupos.</span><span class="sxs-lookup"><span data-stu-id="7b18d-128">These are all the groups that have been created for the site `https://litwareinc.sharepoint.com/sites/finance`, and all the users assigned to those groups.</span></span> <span data-ttu-id="7b18d-129">Los nombres de grupo están en amarillo para ayudarle a separar los nombres de los grupos de sus miembros.</span><span class="sxs-lookup"><span data-stu-id="7b18d-129">The group names are in yellow to help you separate group names from their members.</span></span>

<span data-ttu-id="7b18d-130">Otro ejemplo: a continuación se muestra un conjunto de comandos que enumera los grupos y todas las pertenencias a grupos de todos los sitios de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="7b18d-130">As another example, here is a command set that lists the groups, and all the group memberships, for all of your SharePoint Online sites.</span></span>

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
    
## <a name="see-also"></a><span data-ttu-id="7b18d-131">Vea también</span><span class="sxs-lookup"><span data-stu-id="7b18d-131">See also</span></span>

[<span data-ttu-id="7b18d-132">Conectarse a SharePoint Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="7b18d-132">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="7b18d-133">Crear sitios de SharePoint Online y agregar usuarios con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="7b18d-133">Create SharePoint Online sites and add users with Office 365 PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

[<span data-ttu-id="7b18d-134">Administrar usuarios y grupos de SharePoint Online con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="7b18d-134">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>](manage-sharepoint-users-and-groups-with-powershell.md)

[<span data-ttu-id="7b18d-135">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="7b18d-135">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="7b18d-136">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="7b18d-136">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

