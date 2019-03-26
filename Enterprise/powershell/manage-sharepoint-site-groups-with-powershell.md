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
description: 'Resumen: Use Office 365 PowerShell para administrar grupos de sitio de SharePoint Online.'
ms.openlocfilehash: 04df780732913eaaf80d9bca64db5174089ed80b
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "30573914"
---
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a><span data-ttu-id="6d675-103">Administrar grupos de sitio de SharePoint Online con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="6d675-103">Manage SharePoint Online site groups with Office 365 PowerShell</span></span>

 <span data-ttu-id="6d675-104">**Resumen:** Use Office 365 PowerShell para administrar grupos de sitio de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="6d675-104">**Summary:** Use Office 365 PowerShell to manage SharePoint Online site groups.</span></span>
  
<span data-ttu-id="6d675-105">Aunque puede usar el centro de administración de Microsoft 365, también puede usar Office 365 PowerShell para administrar los grupos de sitio de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="6d675-105">Although you can use the Microsoft 365 admin center, you can also use Office 365 PowerShell to manage your SharePoint Online site groups.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="6d675-106">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="6d675-106">Before you begin</span></span>

<span data-ttu-id="6d675-107">Los procedimientos de este artículo requieren que se conecte a SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="6d675-107">The procedures in this article require you to connect to SharePoint Online.</span></span> <span data-ttu-id="6d675-108">Para obtener instrucciones, consulte [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span><span class="sxs-lookup"><span data-stu-id="6d675-108">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>

## <a name="view-sharepoint-online-with-office-365-powershell"></a><span data-ttu-id="6d675-109">Ver SharePoint Online con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="6d675-109">View SharePoint Online with Office 365 PowerShell</span></span>

<span data-ttu-id="6d675-110">El centro de administración de SharePoint Online tiene algunos métodos fáciles de usar para administrar grupos de sitio.</span><span class="sxs-lookup"><span data-stu-id="6d675-110">The SharePoint Online admin center has some easy-to-use methods for managing site groups.</span></span> <span data-ttu-id="6d675-111">Por ejemplo, supongamos que desea ver los grupos y los miembros del grupo para el `https://litwareinc.sharepoint.com/sites/finance` sitio.</span><span class="sxs-lookup"><span data-stu-id="6d675-111">For example, suppose you want to look at the groups, and the group members, for the `https://litwareinc.sharepoint.com/sites/finance` site.</span></span> <span data-ttu-id="6d675-112">Haga lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="6d675-112">Here’s what you have to do to:</span></span>

1. <span data-ttu-id="6d675-113">en el centro de administración de Microsoft 365, haga clic en**sitios**de **recursos** > y, a continuación, haga clic en la dirección URL del sitio.</span><span class="sxs-lookup"><span data-stu-id="6d675-113">From the Microsoft 365 admin center, click **Resources** > **Sites**, and then click the URL of the site.</span></span>
2. <span data-ttu-id="6d675-114">En el cuadro de diálogo Colección de sitios, haga clic en **Ir al sitio**.</span><span class="sxs-lookup"><span data-stu-id="6d675-114">In the site collection dialog box, click **Go to this site**.</span></span>
3. <span data-ttu-id="6d675-115">En la página del sitio, haga clic en el icono **Configuración** (situado en la esquina superior derecha de la página) y después en **Configuración del sitio**:</span><span class="sxs-lookup"><span data-stu-id="6d675-115">On the site page, click the **Settings** icon (located in the upper right-hand corner of the page) and then click **Site settings**:</span></span><br/>
<span data-ttu-id="6d675-116">![Configuración del sitio de SharePoint Online](media/spo-site-settings.png)</span><span class="sxs-lookup"><span data-stu-id="6d675-116">![SharePoint Online site settings](media/spo-site-settings.png)</span></span><br/>
4. <span data-ttu-id="6d675-117">En la página Configuración del sitio, haga clic en la opción **Permisos de los sitios** de **Usuarios y permisos**.</span><span class="sxs-lookup"><span data-stu-id="6d675-117">On the Site Settings page, click **Sites permissions** under **Users and Permissions**.</span></span>

<span data-ttu-id="6d675-118">Y, así, repita el proceso con el siguiente sitio que quiera ver.</span><span class="sxs-lookup"><span data-stu-id="6d675-118">And then repeat the process for the next site you want to look at.</span></span>

<span data-ttu-id="6d675-119">Para obtener una lista de los grupos con PowerShell de Office 365, use el siguiente conjunto de comandos:</span><span class="sxs-lookup"><span data-stu-id="6d675-119">To get a list of the groups with Office 365 PowerShell, you would use the following command set:</span></span>

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

<span data-ttu-id="6d675-120">Hay dos formas de ejecutar este comando configurado en el símbolo del sistema del shell de administración de SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="6d675-120">There are two ways to run this command set in the SharePoint Online Management Shell command prompt:</span></span>

- <span data-ttu-id="6d675-121">Copie los comandos en el Bloc de notas (u otro editor de texto), modifique el valor de la variable **$siteUrl** , seleccione los comandos y péguelos en el símbolo del sistema del shell de administración de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="6d675-121">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, select the commands, and then paste them into the SharePoint Online Management Shell command prompt.</span></span> <span data-ttu-id="6d675-122">Cuando lo haga, PowerShell se detendrá en **>>** un símbolo del sistema.</span><span class="sxs-lookup"><span data-stu-id="6d675-122">When you do, PowerShell will stop at a **>>** prompt.</span></span> <span data-ttu-id="6d675-123">Presione Entrar para ejecutar el comando **foreach**.</span><span class="sxs-lookup"><span data-stu-id="6d675-123">Press Enter to execute the **foreach** command.</span></span><br/>
- <span data-ttu-id="6d675-124">Copie los comandos en el Bloc de notas (u otro editor de texto), modifique el valor de la variable **$siteURL** y después guarde este archivo de texto con un nombre y la extensión. ps1 en la carpeta adecuada.</span><span class="sxs-lookup"><span data-stu-id="6d675-124">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, and then save this text file with a name and the .ps1 extension in a suitable folder.</span></span> <span data-ttu-id="6d675-125">A continuación, ejecute el script desde el símbolo del sistema del shell de administración de SharePoint Online especificando su ruta de acceso y nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="6d675-125">Next, run the script from the SharePoint Online Management Shell command prompt by specifying its path and file name.</span></span> <span data-ttu-id="6d675-126">A continuación se muestra un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="6d675-126">Here is an example command:</span></span>

```
C:\Scripts\SiteGroupsAndUsers.ps1
```

<span data-ttu-id="6d675-127">En ambos casos, el resultado será parecido a lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="6d675-127">In both cases, you should see something similar to this:</span></span>

![Grupos de sitio de SharePoint Online](media/SPO-site-groups.png)

<span data-ttu-id="6d675-129">Se trata de todos los grupos que se han creado para el `https://litwareinc.sharepoint.com/sites/finance`sitio y de todos los usuarios asignados a dichos grupos.</span><span class="sxs-lookup"><span data-stu-id="6d675-129">These are all the groups that have been created for the site `https://litwareinc.sharepoint.com/sites/finance`, and all the users assigned to those groups.</span></span> <span data-ttu-id="6d675-130">Los nombres de grupo están en amarillo para ayudarle a separar los nombres de los grupos de sus miembros.</span><span class="sxs-lookup"><span data-stu-id="6d675-130">The group names are in yellow to help you separate group names from their members.</span></span>

<span data-ttu-id="6d675-131">Otro ejemplo: a continuación se muestra un conjunto de comandos que enumera los grupos y todas las pertenencias a grupos de todos los sitios de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="6d675-131">As another example, here is a command set that lists the groups, and all the group memberships, for all of your SharePoint Online sites.</span></span>

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
    
## <a name="see-also"></a><span data-ttu-id="6d675-132">Vea también</span><span class="sxs-lookup"><span data-stu-id="6d675-132">See also</span></span>

[<span data-ttu-id="6d675-133">Conectarse a SharePoint Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="6d675-133">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="6d675-134">Crear sitios de SharePoint Online y agregar usuarios con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="6d675-134">Create SharePoint Online sites and add users with Office 365 PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

[<span data-ttu-id="6d675-135">Administrar usuarios y grupos de SharePoint Online con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="6d675-135">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>](manage-sharepoint-users-and-groups-with-powershell.md)

[<span data-ttu-id="6d675-136">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="6d675-136">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="6d675-137">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="6d675-137">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

