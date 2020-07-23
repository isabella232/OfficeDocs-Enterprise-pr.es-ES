---
title: Crear sitios de SharePoint Online y agregar usuarios con PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
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
description: 'Resumen: Use PowerShell para crear sitios de SharePoint Online y luego agregar usuarios y grupos a esos sitios.'
ms.openlocfilehash: 2791b4de9388e3ff828a665aeeef5ada19627107
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230806"
---
# <a name="create-sharepoint-online-sites-and-add-users-with-powershell"></a><span data-ttu-id="c451d-103">Crear sitios de SharePoint Online y agregar usuarios con PowerShell</span><span class="sxs-lookup"><span data-stu-id="c451d-103">Create SharePoint Online sites and add users with PowerShell</span></span>

<span data-ttu-id="c451d-104">*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="c451d-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="c451d-105">Cuando usa PowerShell para Microsoft 365 para crear sitios de SharePoint Online y agregar usuarios, puede realizar las tareas de forma rápida y repetida con mucha más rapidez que en el centro de administración de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="c451d-105">When you use PowerShell for Microsoft 365 to create SharePoint Online sites and add users, you can quickly and repeatedly perform tasks much faster than you can in the Microsoft 365 admin center.</span></span> <span data-ttu-id="c451d-106">También puede realizar tareas que no es posible realizar en el centro de administración de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="c451d-106">You can also perform tasks that are not possible to perform in the Microsoft 365 admin center.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="c451d-107">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="c451d-107">Before you begin</span></span>

<span data-ttu-id="c451d-108">Los procedimientos de este tema requieren que se conecte a SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="c451d-108">The procedures in this topic require you to connect to SharePoint Online.</span></span> <span data-ttu-id="c451d-109">Para obtener instrucciones, vea [conectarse a PowerShell de SharePoint Online](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span><span class="sxs-lookup"><span data-stu-id="c451d-109">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span></span>

## <a name="step-1-create-new-site-collections-using-powershell"></a><span data-ttu-id="c451d-110">Paso 1: crear nuevas colecciones de sitios con PowerShell</span><span class="sxs-lookup"><span data-stu-id="c451d-110">Step 1: Create new site collections using PowerShell</span></span>

<span data-ttu-id="c451d-111">Cree varios sitios con PowerShell y un archivo. csv que cree con el código de ejemplo proporcionado y el Bloc de notas.</span><span class="sxs-lookup"><span data-stu-id="c451d-111">Create multiple sites using PowerShell and a .csv file that you create using the example code provided and Notepad.</span></span> <span data-ttu-id="c451d-112">Para este procedimiento, reemplazará la información de marcador de posición que se muestra entre corchetes con su propia información de sitio y espacio empresarial específica.</span><span class="sxs-lookup"><span data-stu-id="c451d-112">For this procedure, you’ll be replacing the placeholder information shown in brackets with your own site- and tenant-specific information.</span></span> <span data-ttu-id="c451d-113">Este proceso le permite crear un único archivo y ejecutar un solo comando de PowerShell que usa ese archivo.</span><span class="sxs-lookup"><span data-stu-id="c451d-113">This process lets you create a single file and run a single PowerShell command that uses that file.</span></span> <span data-ttu-id="c451d-114">Esto hace que las acciones se tomen repetibles y se puedan reportar y elimina muchos errores, si no todos, que pueden venir de escribir comandos largos en el shell de administración de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="c451d-114">This makes the actions taken both repeatable and portable and eliminates many, if not all, errors that can come from typing long commands into the SharePoint Online Management Shell.</span></span> <span data-ttu-id="c451d-115">Este procedimiento consta de dos partes.</span><span class="sxs-lookup"><span data-stu-id="c451d-115">There are two parts to this procedure.</span></span> <span data-ttu-id="c451d-116">En primer lugar, creará un archivo. csv y, a continuación, hará referencia a ese archivo. csv con PowerShell, que usará su contenido para crear los sitios.</span><span class="sxs-lookup"><span data-stu-id="c451d-116">First you’ll create a .csv file, and then you’ll reference that .csv file using PowerShell, which will use its contents to create the sites.</span></span>

<span data-ttu-id="c451d-117">El cmdlet de PowerShell importa el archivo. csv y lo canaliza en un bucle dentro de las llaves que lee la primera línea del archivo como encabezados de columna.</span><span class="sxs-lookup"><span data-stu-id="c451d-117">The PowerShell cmdlet imports the .csv file and pipes it to a loop inside the curly brackets that reads the first line of the file as column headers.</span></span> <span data-ttu-id="c451d-118">A continuación, el cmdlet de PowerShell recorre en iteración los registros restantes, crea una nueva colección de sitios para cada registro y asigna propiedades de la colección de sitios de acuerdo con los encabezados de columna.</span><span class="sxs-lookup"><span data-stu-id="c451d-118">The PowerShell cmdlet then iterates through the remaining records, creates a new site collection for each record, and assigns properties of the site collection according to the column headers.</span></span>

### <a name="create-a-csv-file"></a><span data-ttu-id="c451d-119">Crear un archivo .csv</span><span class="sxs-lookup"><span data-stu-id="c451d-119">Create a .csv file</span></span>

1. <span data-ttu-id="c451d-120">Abra el Bloc de notas y pegue el siguiente bloque de texto:</span><span class="sxs-lookup"><span data-stu-id="c451d-120">Open Notepad, and paste the following text block into it:</span></span><br/>

```powershell
Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
```
<br/><span data-ttu-id="c451d-121">Donde *tenant* es el nombre del espacio empresarial y *propietario* es el nombre del usuario del inquilino al que desea conceder la función de administrador de la colección de sitios primaria.</span><span class="sxs-lookup"><span data-stu-id="c451d-121">Where *tenant* is the name of your tenant, and *owner* is the user name of the user on your tenant to whom you want to grant the role of primary site collection administrator.</span></span><br/><span data-ttu-id="c451d-122">(Puede presionar CTRL + H cuando use el Bloc de notas para reemplazarla en masa de forma más rápida).</span><span class="sxs-lookup"><span data-stu-id="c451d-122">(You can press Ctrl+H when you use Notepad to bulk replace faster.)</span></span><br/>

2. <span data-ttu-id="c451d-123">Guarde el archivo en el escritorio como **SiteCollections.csv**.</span><span class="sxs-lookup"><span data-stu-id="c451d-123">Save the file on your desktop as **SiteCollections.csv**.</span></span><br/>

> [!TIP]
> <span data-ttu-id="c451d-124">Antes de usar este o cualquier otro archivo de script de Windows PowerShell o. csv, se recomienda asegurarse de que no hay caracteres superfluos o no imprimibles.</span><span class="sxs-lookup"><span data-stu-id="c451d-124">Before you use this or any other .csv or Windows PowerShell script file, it's a good practice to make sure that there are no extraneous or nonprinting characters.</span></span> <span data-ttu-id="c451d-125">Abra el archivo en Word y, en la cinta de opciones, haga clic en el icono de párrafo para mostrar los caracteres no imprimibles.</span><span class="sxs-lookup"><span data-stu-id="c451d-125">Open the file in Word, and in the ribbon, click the paragraph icon to show nonprinting characters.</span></span> <span data-ttu-id="c451d-126">No debe haber ningún carácter extraño o no imprimible.</span><span class="sxs-lookup"><span data-stu-id="c451d-126">There should be no extraneous nonprinting characters.</span></span> <span data-ttu-id="c451d-127">Por ejemplo, no debe haber ninguna marca de párrafo después del último carácter al final del archivo.</span><span class="sxs-lookup"><span data-stu-id="c451d-127">For example, there should be no paragraph marks beyond the final one at the end of the file.</span></span>

### <a name="run-the-windows-powershell-command"></a><span data-ttu-id="c451d-128">Ejecutar el comando de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c451d-128">Run the Windows PowerShell command</span></span>

1. <span data-ttu-id="c451d-129">En el símbolo del sistema de Windows PowerShell, escriba o copie y pegue el siguiente comando y presione ENTRAR:</span><span class="sxs-lookup"><span data-stu-id="c451d-129">At the Windows PowerShell prompt, type or copy and paste the following command, and press Enter:</span></span><br/>
```powershell
Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {New-SPOSite -Owner $_.Owner -StorageQuota $_.StorageQuota -Url $_.Url -NoWait -ResourceQuota $_.ResourceQuota -Template $_.Template -TimeZoneID $_.TimeZoneID -Title $_.Name}
```
<br/><span data-ttu-id="c451d-130">Donde *alias* es igual al alias del usuario.</span><span class="sxs-lookup"><span data-stu-id="c451d-130">Where *MyAlias* equals your user alias.</span></span><br/>

2. <span data-ttu-id="c451d-p106">Espere a que el símbolo del sistema de Windows PowerShell aparezca de nuevo. Esto puede tardar un par de minutos.</span><span class="sxs-lookup"><span data-stu-id="c451d-p106">Wait for the Windows PowerShell prompt to reappear. It might take a minute or two.</span></span><br/>

3. <span data-ttu-id="c451d-133">En el símbolo del sistema de Windows PowerShell, escriba o copie y pegue el siguiente cmdlet y presione ENTRAR:</span><span class="sxs-lookup"><span data-stu-id="c451d-133">At the Windows PowerShell prompt, type or copy and paste the following cmdlet, and press Enter:</span></span><br/>

```powershell
Get-SPOSite -Detailed | Format-Table -AutoSize
```
<br/>

4. <span data-ttu-id="c451d-134">Observe que las nuevas colecciones de sitios figuran en la lista.</span><span class="sxs-lookup"><span data-stu-id="c451d-134">Note the new site collections in the list.</span></span> <span data-ttu-id="c451d-135">Mediante nuestro archivo CSV de ejemplo, vería las siguientes colecciones de sitios: **TeamSite01**, **Blog01**, **Project01**y **Community01**</span><span class="sxs-lookup"><span data-stu-id="c451d-135">Using our example CSV file, you would see the following site collections: **TeamSite01**, **Blog01**, **Project01**, and **Community01**</span></span>

<span data-ttu-id="c451d-136">Eso es todo.</span><span class="sxs-lookup"><span data-stu-id="c451d-136">That’s it.</span></span> <span data-ttu-id="c451d-137">Ha creado varias colecciones de sitios con el archivo. csv que ha creado y un solo comando de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c451d-137">You’ve created multiple site collections using the .csv file you created and a single Windows PowerShell command.</span></span> <span data-ttu-id="c451d-138">Ya está listo para crear y asignar usuarios a estos sitios.</span><span class="sxs-lookup"><span data-stu-id="c451d-138">You’re now ready to create and assign users to these sites.</span></span>

## <a name="step-2-add-users-and-groups"></a><span data-ttu-id="c451d-139">Paso 2: agregar usuarios y grupos</span><span class="sxs-lookup"><span data-stu-id="c451d-139">Step 2: Add users and groups</span></span>

<span data-ttu-id="c451d-p109">Ahora vamos a crear usuarios y a agregarlos a un grupo de colecciones de sitios. Luego, usaremos un archivo .csv para cargar los nuevos usuarios y grupos de forma masiva.</span><span class="sxs-lookup"><span data-stu-id="c451d-p109">Now you’re going to create users and add them to a site collection group. You will then use a .csv file to bulk upload new groups and users.</span></span>

<span data-ttu-id="c451d-142">Los siguientes procedimientos continúan usando los sitios de ejemplo TeamSite01, Blog01, Project01 y Community01.</span><span class="sxs-lookup"><span data-stu-id="c451d-142">The following procedures continue using the example sites TeamSite01, Blog01, Project01, and Community01.</span></span>

### <a name="create-csv-and-ps1-files"></a><span data-ttu-id="c451d-143">Crear los archivos .csv y .ps1</span><span class="sxs-lookup"><span data-stu-id="c451d-143">Create .csv and .ps1 files</span></span>

1. <span data-ttu-id="c451d-144">Abra el Bloc de notas y pegue el siguiente bloque de texto:</span><span class="sxs-lookup"><span data-stu-id="c451d-144">Open Notepad, and paste the following text block into it:</span></span><br/>

```powershell
Site,Group,PermissionLevels
https://tenant.sharepoint.com/sites/Community01,Contoso Project Leads,Full Control
https://tenant.sharepoint.com/sites/Community01,Contoso Auditors,View Only
https://tenant.sharepoint.com/sites/Community01,Contoso Designers,Design
https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
https://tenant.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
```
<br/><span data-ttu-id="c451d-145">Donde *tenant* es el nombre del espacio empresarial.</span><span class="sxs-lookup"><span data-stu-id="c451d-145">Where *tenant* equals your tenant name.</span></span><br/>

2. <span data-ttu-id="c451d-146">Guarde el archivo en el escritorio como **GroupsAndPermissions.csv**.</span><span class="sxs-lookup"><span data-stu-id="c451d-146">Save the file to your desktop as **GroupsAndPermissions.csv**.</span></span><br/>

3. <span data-ttu-id="c451d-147">Abra otra instancia del Bloc de notas y pegue el siguiente bloque de texto:</span><span class="sxs-lookup"><span data-stu-id="c451d-147">Open a new instance of Notepad, and paste the following text block into it:</span></span><br/>

```powershell
Group,LoginName,Site
Contoso Project Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Community01
Contoso Auditors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Community01
Contoso Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Community01
XT1000 Team Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
XT1000 Advisors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
Contoso Blog Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
Contoso Blog Editors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
Project Alpha Approvers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Project01
```
<br/><span data-ttu-id="c451d-148">Donde *tenant* es el nombre del inquilino y *username* es el nombre de usuario de un usuario existente.</span><span class="sxs-lookup"><span data-stu-id="c451d-148">Where *tenant* equals your tenant name, and *username* equals the user name of an existing user.</span></span><br/>

4. <span data-ttu-id="c451d-149">Guarde el archivo en el escritorio como **Users.csv**.</span><span class="sxs-lookup"><span data-stu-id="c451d-149">Save the file to your desktop as **Users.csv**.</span></span><br/>

5. <span data-ttu-id="c451d-150">Abra otra instancia del Bloc de notas y pegue el siguiente bloque de texto:</span><span class="sxs-lookup"><span data-stu-id="c451d-150">Open a new instance of Notepad, and paste the following text block into it:</span></span><br/>

```powershell
Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\users\MyAlias\desktop\Users.csv | where {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```
<br/><span data-ttu-id="c451d-151">Donde alias es igual al nombre del usuario que ha iniciado sesión actualmente.</span><span class="sxs-lookup"><span data-stu-id="c451d-151">Where MyAlias equals the user name of the user that is currently logged on.</span></span><br/>

6. <span data-ttu-id="c451d-152">Guarde el archivo en el escritorio como **UsersAndGroups.ps1**.</span><span class="sxs-lookup"><span data-stu-id="c451d-152">Save the file to your desktop as **UsersAndGroups.ps1**.</span></span> <span data-ttu-id="c451d-153">Este es un script de Windows PowerShell sencillo.</span><span class="sxs-lookup"><span data-stu-id="c451d-153">This is a simple Windows PowerShell script.</span></span>

<span data-ttu-id="c451d-154">Ya puede ejecutar el script UsersAndGroup.ps1 para agregar usuarios y grupos a varias colecciones de sitios.</span><span class="sxs-lookup"><span data-stu-id="c451d-154">You’re now ready to run the UsersAndGroup.ps1 script to add users and groups to multiple site collections.</span></span>

### <a name="run-usersandgroupsps1-script"></a><span data-ttu-id="c451d-155">Ejecutar el script UsersAndGroups.ps1</span><span class="sxs-lookup"><span data-stu-id="c451d-155">Run UsersAndGroups.ps1 script</span></span>

1. <span data-ttu-id="c451d-156">Vuelva al Shell de administración de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="c451d-156">Return to the SharePoint Online Management Shell.</span></span><br/>
2. <span data-ttu-id="c451d-157">En el símbolo del sistema de Windows PowerShell, escriba o copie y pegue la siguiente línea y presione ENTRAR:</span><span class="sxs-lookup"><span data-stu-id="c451d-157">At the Windows PowerShell prompt, type or copy and paste the following line, and press Enter:</span></span><br/>
```powershell
Set-ExecutionPolicy Bypass
```
<br/>

3. <span data-ttu-id="c451d-158">En el mensaje de confirmación, presione **s**.</span><span class="sxs-lookup"><span data-stu-id="c451d-158">At the confirmation prompt, press **Y**.</span></span><br/>

4. <span data-ttu-id="c451d-159">En el símbolo del sistema de Windows PowerShell, escriba o copie y pegue lo siguiente y presione ENTRAR:</span><span class="sxs-lookup"><span data-stu-id="c451d-159">At the Windows PowerShell prompt, type or copy and paste the following, and press Enter:</span></span><br/>

```powershell
c:\users\MyAlias\desktop\UsersAndGroups.ps1
```
<br/><span data-ttu-id="c451d-160">Donde *alias* es igual al nombre de usuario.</span><span class="sxs-lookup"><span data-stu-id="c451d-160">Where *MyAlias* equals your user name.</span></span><br/>

5. <span data-ttu-id="c451d-p111">Antes de continuar, espere a que el símbolo del sistema vuelva. Primero verá que los grupos aparecen según se han creado y, luego, verá la lista de grupos repetida a medida que se vayan agregando usuarios.</span><span class="sxs-lookup"><span data-stu-id="c451d-p111">Wait for the prompt to return before moving on. You will first see the groups appear as they are created. Then you will see the group list repeated as users are added.</span></span>

## <a name="see-also"></a><span data-ttu-id="c451d-164">Consulte también</span><span class="sxs-lookup"><span data-stu-id="c451d-164">See also</span></span>

[<span data-ttu-id="c451d-165">Conectarse a SharePoint Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="c451d-165">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="c451d-166">Administrar grupos de sitio de SharePoint Online con PowerShell</span><span class="sxs-lookup"><span data-stu-id="c451d-166">Manage SharePoint Online site groups with PowerShell</span></span>](manage-sharepoint-site-groups-with-powershell.md)

[<span data-ttu-id="c451d-167">Administrar Microsoft 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="c451d-167">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="c451d-168">Introducción a PowerShell para Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="c451d-168">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)

