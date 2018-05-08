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
ms.openlocfilehash: 881e67b7eb2d8bb5e04f83e28569aa54341d16b9
ms.sourcegitcommit: 5c5489db5d1000296945c9774198bd911bee4f14
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a><span data-ttu-id="a3f4c-103">Administrar grupos de sitio de SharePoint Online con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="a3f4c-103">Manage SharePoint Online site groups with Office 365 PowerShell</span></span>

 <span data-ttu-id="a3f4c-104">**Resumen:** Usar PowerShell de Office 365 para administrar grupos de sitio de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="a3f4c-104">**Summary:** Use Office 365 PowerShell to manage SharePoint Online site groups.</span></span>
  
<span data-ttu-id="a3f4c-105">Aunque se puede usar el centro de administración de Office 365, también puede usar Office 365 PowerShell para administrar los grupos de sitio de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="a3f4c-105">Although you can use the Office 365 admin center, you can also use Office 365 PowerShell to manage your SharePoint Online site groups.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="a3f4c-106">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="a3f4c-106">Before you begin</span></span>

<span data-ttu-id="a3f4c-p101">Los procedimientos descritos en este artículo requieren que se va a conectar a SharePoint Online. Para obtener instrucciones, vea [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span><span class="sxs-lookup"><span data-stu-id="a3f4c-p101">The procedures in this article require you to connect to SharePoint Online. For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>

## <a name="view-sharepoint-online-with-office-365-powershell"></a><span data-ttu-id="a3f4c-109">Vista SharePoint Online con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="a3f4c-109">View SharePoint Online with Office 365 PowerShell</span></span>

<span data-ttu-id="a3f4c-p102">El centro de administración de SharePoint Online tiene algunos métodos fáciles de usar para administrar grupos de sitio. Por ejemplo, suponga que desea buscar en los grupos y los miembros del grupo, para el https\://litwareinc.sharepoint.com/sites/finance sitio. Aquí es lo que tiene que hacer para:</span><span class="sxs-lookup"><span data-stu-id="a3f4c-p102">The SharePoint Online admin center has some easy-to-use methods for managing site groups. For example, suppose you want to look at the groups, and the group members, for the https\://litwareinc.sharepoint.com/sites/finance site. Here’s what you have to do to:</span></span>

1. <span data-ttu-id="a3f4c-113">Desde el centro de administración de Office 365, haga clic en **recursos** > de**sitios**y, a continuación, haga clic en la dirección URL del sitio.</span><span class="sxs-lookup"><span data-stu-id="a3f4c-113">From the Office 365 admin center, click **Resources** > **Sites**, and then click the URL of the site.</span></span>
2. <span data-ttu-id="a3f4c-114">En el cuadro de diálogo de colección de sitios, haga clic en **Ir a este sitio**.</span><span class="sxs-lookup"><span data-stu-id="a3f4c-114">In the site collection dialog box, click **Go to this site**.</span></span>
3. <span data-ttu-id="a3f4c-115">En la página del sitio, haga clic en el icono de **configuración** (que se encuentra en la esquina superior derecha de la página) y, a continuación, haga clic en **Configuración del sitio**:</span><span class="sxs-lookup"><span data-stu-id="a3f4c-115">On the site page, click the **Settings** icon (located in the upper right-hand corner of the page) and then click **Site settings**:</span></span></br>
<span data-ttu-id="a3f4c-116">![Configuración del sitio de SharePoint Online](images/spo-site-settings.png)</span><span class="sxs-lookup"><span data-stu-id="a3f4c-116">![SharePoint Online site settings](images/spo-site-settings.png)</span></span></br>
4. <span data-ttu-id="a3f4c-117">En la página Configuración del sitio, haga clic en **permisos de sitios** , en **usuarios y permisos**.</span><span class="sxs-lookup"><span data-stu-id="a3f4c-117">On the Site Settings page, click **Sites permissions** under **Users and Permissions**.</span></span>

<span data-ttu-id="a3f4c-118">Y, así, repita el proceso con el siguiente sitio que quiera ver.</span><span class="sxs-lookup"><span data-stu-id="a3f4c-118">And then repeat the process for the next site you want to look at.</span></span>

<span data-ttu-id="a3f4c-119">Para obtener una lista de los grupos con PowerShell de Office 365, use el siguiente conjunto de comandos:</span><span class="sxs-lookup"><span data-stu-id="a3f4c-119">To get a list of the groups with Office 365 PowerShell, you would use the following command set:</span></span>

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

<span data-ttu-id="a3f4c-120">Hay dos formas de ejecutar este comando establecer en el símbolo del Shell de administración de SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="a3f4c-120">There are two ways to run this command set in the SharePoint Online Management Shell command prompt:</span></span>

- <span data-ttu-id="a3f4c-p103">Copiar los comandos en el Bloc de notas (o en otro editor de texto), modifique el valor de la variable **$siteURL** , seleccione los comandos y, a continuación, péguelos en el símbolo del Shell de administración de SharePoint Online. Cuando lo hace, PowerShell se detendrá en un **>>** símbolo del sistema. Presione ENTRAR para ejecutar el comando **foreach** .</span><span class="sxs-lookup"><span data-stu-id="a3f4c-p103">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, select the commands, and then paste them into the SharePoint Online Management Shell command prompt. When you do, PowerShell will stop at a **>>** prompt. Press Enter to execute the **foreach** command.</span></span></br>
- <span data-ttu-id="a3f4c-p104">Copiar los comandos en el Bloc de notas (o en otro editor de texto), modifique el valor de la variable **$siteURL** y, a continuación, guarde este archivo de texto con un nombre y la extensión. ps1 en una carpeta adecuada. A continuación, ejecute la secuencia de comandos desde el símbolo del Shell de administración de SharePoint Online mediante la especificación de su ruta de acceso y nombre de archivo. Este es un comando de ejemplo:</span><span class="sxs-lookup"><span data-stu-id="a3f4c-p104">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, and then save this text file with a name and the .ps1 extension in a suitable folder. Next, run the script from the SharePoint Online Management Shell command prompt by specifying its path and file name. Here is an example command:</span></span>

```
C:\Scripts\SiteGroupsAndUsers.ps1
```

<span data-ttu-id="a3f4c-127">En ambos casos, el resultado será parecido a lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="a3f4c-127">In both cases, you should see something similar to this:</span></span>

![Grupos de sitio de SharePoint Online](images/SPO-site-groups.png)

<span data-ttu-id="a3f4c-p105">Estos son todos los grupos que se han creado para el sitio https\:/ / litwareinc.sharepoint.com/sites/finance, así como todos los usuarios asignan a esos grupos. Los nombres de grupo se encuentran en amarillo que le ayudarán a los nombres de grupo independiente de sus miembros.</span><span class="sxs-lookup"><span data-stu-id="a3f4c-p105">These are all the groups that have been created for the site https\://litwareinc.sharepoint.com/sites/finance, as well as all the users assigned to those groups. The group names are in yellow to help you separate group names from their members.</span></span>

<span data-ttu-id="a3f4c-131">Como otro ejemplo, aquí es un conjunto de comandos que enumera los grupos y todas las pertenencias a grupos, para todos los sitios de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="a3f4c-131">As another example, here is a command set that lists the groups, and all the group memberships, for all of your SharePoint Online sites.</span></span>

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
    
## <a name="see-also"></a><span data-ttu-id="a3f4c-132">Ver también</span><span class="sxs-lookup"><span data-stu-id="a3f4c-132">See also</span></span>

[<span data-ttu-id="a3f4c-133">Conectarse a SharePoint Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="a3f4c-133">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="a3f4c-134">Crear sitios de SharePoint Online y agregar usuarios con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="a3f4c-134">Create SharePoint Online sites and add users with Office 365 PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

[<span data-ttu-id="a3f4c-135">Administrar usuarios y grupos de SharePoint Online con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="a3f4c-135">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>](manage-sharepoint-users-and-groups-with-powershell.md)

[<span data-ttu-id="a3f4c-136">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="a3f4c-136">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="a3f4c-137">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="a3f4c-137">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

