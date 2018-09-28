---
title: Crear sitios de SharePoint Online y agregar usuarios con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 'Resumen: Use PowerShell de Office 365 para crear nuevos sitios de SharePoint Online y, a continuación, agregar usuarios y grupos a esos sitios.'
ms.openlocfilehash: 41ca26249bd494d5603a425689e47f9fe6809f1a
ms.sourcegitcommit: 82219b5f8038ae066405dfb7933c40bd1f598bd0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/14/2018
ms.locfileid: "23975208"
---
# <a name="create-sharepoint-online-sites-and-add-users-with-office-365-powershell"></a><span data-ttu-id="339db-103">Crear sitios de SharePoint Online y agregar usuarios con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="339db-103">Create SharePoint Online sites and add users with Office 365 PowerShell</span></span>

 <span data-ttu-id="339db-104">**Resumen:** Usar PowerShell de Office 365 para crear nuevos sitios de SharePoint Online y, a continuación, agregar usuarios y grupos a esos sitios.</span><span class="sxs-lookup"><span data-stu-id="339db-104">**Summary:** Use Office 365 PowerShell to create new SharePoint Online sites, and then add users and groups to those sites.</span></span>

<span data-ttu-id="339db-p101">Cuando se usa Office 365 PowerShell para crear sitios de SharePoint Online y agregar usuarios, puede rápida y repetidamente realizar tareas mucho más rápidas que en el centro de administración de Office 356. También puede realizar las tareas que no son posibles para llevar a cabo en el centro de administración de Office 356.</span><span class="sxs-lookup"><span data-stu-id="339db-p101">When you use Office 365 PowerShell to create SharePoint Online sites and add users, you can quickly and repeatedly perform tasks much faster than you can in the Office 356 admin center. You can also perform tasks that are not possible to perform in the Office 356 admin center.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="339db-107">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="339db-107">Before you begin</span></span>

<span data-ttu-id="339db-p102">Los procedimientos descritos en este tema requieren que se va a conectar a SharePoint Online. Para obtener instrucciones, vea [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span><span class="sxs-lookup"><span data-stu-id="339db-p102">The procedures in this topic require you to connect to SharePoint Online. For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span></span>

## <a name="step-1-create-new-site-collections-using-office-365-powershell"></a><span data-ttu-id="339db-110">Paso 1: crear colecciones de sitios con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="339db-110">Step 1: Create new site collections using Office 365 PowerShell</span></span>

<span data-ttu-id="339db-p103">Cree varios sitios mediante Office 365 PowerShell y un archivo .csv con el código de ejemplo provisto y el Bloc de notas. En este procedimiento, reemplazará la información de marcador de posición entre corchetes por su propia información específica de sitios e inquilinos. Durante el proceso, puede crear un único archivo y ejecutar un solo comando de Office 365 PowerShell que use dicho archivo. De este modo, las acciones que lleve a cabo serán repetibles y reproducibles, y se eliminarán muchos de los errores (si no todos) que pueden surgir al escribir comandos largos en el shell de administración de SharePoint Online. El procedimiento se divide en dos partes: primero crearemos un archivo .csv y, luego, haremos referencia a él mediante Office 365 PowerShell, que usará su contenido para crear los sitios.</span><span class="sxs-lookup"><span data-stu-id="339db-p103">Create multiple sites using Office 365 PowerShell and a .csv file that you create using the example code provided and Notepad. For this procedure, you’ll be replacing the placeholder information shown in brackets with your own site- and tenant-specific information. This process allows you to create a single file and run a single Office 365 PowerShell command that uses that file. This makes the actions taken both repeatable and portable and eliminates many, if not all, errors that can come from typing long commands into the SharePoint Online Management Shell. There are two parts to this procedure. First you’ll create a .csv file, and then you’ll reference that .csv file using Office 365 PowerShell, which will use its contents to create the sites.</span></span>

<span data-ttu-id="339db-p104">El cmdlet de Office 365 PowerShell importa el archivo .csv y lo canaliza en un bucle entre llaves que lee la primera línea del archivo como encabezados de columna. Luego, el cmdlet de Office 365 PowerShell itera en el resto de los registros, crea una colección de sitios para cada uno de ellos y asigna propiedades a la colección de sitios en función de los encabezados de columna.</span><span class="sxs-lookup"><span data-stu-id="339db-p104">The Office 365 PowerShell cmdlet imports the .csv file and pipes it to a loop inside the curly brackets that reads the first line of the file as column headers. The Office 365 PowerShell cmdlet then iterates through the remaining records, creates a new site collection for each record, and assigns properties of the site collection according to the column headers.</span></span>

### <a name="create-a-csv-file"></a><span data-ttu-id="339db-119">Crear un archivo .csv</span><span class="sxs-lookup"><span data-stu-id="339db-119">Create a .csv file</span></span>

1. <span data-ttu-id="339db-120">Abra el Bloc de notas y pegue el siguiente bloque de texto:</span><span class="sxs-lookup"><span data-stu-id="339db-120">Open Notepad, and paste the following text block into it:</span></span><br/>

```
Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
```
<br/><span data-ttu-id="339db-121">Donde *inquilino* es el nombre de su inquilino y *propietario* es el nombre de usuario del usuario en el inquilino a quienes desea conceder el rol de administrador de la colección de sitios primaria.</span><span class="sxs-lookup"><span data-stu-id="339db-121">Where *tenant* is the name of your tenant, and *owner* is the user name of the user on your tenant to whom you want to grant the role of primary site collection administrator.</span></span><br/><span data-ttu-id="339db-122">(Puede presionar Ctrl + H al usar el Bloc de notas para reemplazar de forma masiva con mayor rapidez).</span><span class="sxs-lookup"><span data-stu-id="339db-122">(You can press Ctrl+H when you use Notepad to bulk replace faster.)</span></span><br/>

2. <span data-ttu-id="339db-123">Guarde el archivo en el escritorio como **SiteCollections.csv**.</span><span class="sxs-lookup"><span data-stu-id="339db-123">Save the file on your desktop as **SiteCollections.csv**.</span></span><br/>

> [!TIP]
> <span data-ttu-id="339db-p105">Antes de usar este o cualquier otro .csv o archivo de script de Windows PowerShell, es recomendable para asegurarse de que no hay ningún carácter extrañas o no imprimibles. Abra el archivo en Word y, en la cinta de opciones, haga clic en el icono de párrafo para mostrar los caracteres no imprimibles. No debe haber ningún extraños caracteres no imprimibles. Por ejemplo, no debería haber ninguna marca de párrafo además del final al final del archivo.</span><span class="sxs-lookup"><span data-stu-id="339db-p105">Before you use this or any other .csv or Windows PowerShell script file, it is good practice to make sure that there are no extraneous or nonprinting characters. Open the file in Word, and in the ribbon, click the paragraph icon to show nonprinting characters. There should be no extraneous nonprinting characters. For example, there should be no paragraph marks beyond the final one at the end of the file.</span></span>

### <a name="run-the-windows-powershell-command"></a><span data-ttu-id="339db-128">Ejecutar el comando de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="339db-128">Run the Windows PowerShell command</span></span>

1. <span data-ttu-id="339db-129">En el símbolo del sistema de Windows PowerShell, escriba o copie y pegue el siguiente cmdlet y presione ENTRAR:</span><span class="sxs-lookup"><span data-stu-id="339db-129">At the Windows PowerShell prompt, type or copy and paste the following cmdlet, and press Enter:</span></span><br/>
```
Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {New-SPOSite -Owner $_.Owner -StorageQuota $_.StorageQuota -Url $_.Url -NoWait -ResourceQuota $_.ResourceQuota -Template $_.Template -TimeZoneID $_.TimeZoneID -Title $_.Name}
```
<br/><span data-ttu-id="339db-130">Donde *MyAlias* es igual al alias del usuario.</span><span class="sxs-lookup"><span data-stu-id="339db-130">Where *MyAlias* equals your user alias.</span></span><br/>

2. <span data-ttu-id="339db-p106">Espere a que el símbolo del sistema de Windows PowerShell aparezca de nuevo. Esto puede tardar un par de minutos.</span><span class="sxs-lookup"><span data-stu-id="339db-p106">Wait for the Windows PowerShell prompt to reappear. It might take a minute or two.</span></span><br/>

3. <span data-ttu-id="339db-133">En el símbolo del sistema de Windows PowerShell, escriba o copie y pegue el siguiente cmdlet y presione ENTRAR:</span><span class="sxs-lookup"><span data-stu-id="339db-133">At the Windows PowerShell prompt, type or copy and paste the following cmdlet, and press Enter:</span></span><br/>

```
Get-SPOSite -Detailed | Format-Table -AutoSize
```
<br/>

4. <span data-ttu-id="339db-p107">Tenga en cuenta las nuevas colecciones de sitios en la lista. Debería ver las colecciones de sitios siguientes: **contosotest**, **TeamSite01**, **Blog01**y **Project01**</span><span class="sxs-lookup"><span data-stu-id="339db-p107">Note the new site collections in the list. You should see the following site collections: **contosotest**, **TeamSite01**, **Blog01**, and **Project01**</span></span>

<span data-ttu-id="339db-p108">Eso es todo. Ha creado varias colecciones de sitios con el archivo .csv que creó anteriormente y un único cmdlet de Windows PowerShell. Ya está listo para crear y asignar usuarios a estos sitios.</span><span class="sxs-lookup"><span data-stu-id="339db-p108">That’s it. You’ve created multiple site collections using the .csv file you created and a single Windows PowerShell cmdlet. You’re now ready to create and assign users to these sites.</span></span>

## <a name="step-2-add-users-and-groups"></a><span data-ttu-id="339db-139">Paso 2: agregar usuarios y grupos</span><span class="sxs-lookup"><span data-stu-id="339db-139">Step 2: Add users and groups</span></span>

<span data-ttu-id="339db-p109">Ahora vamos a crear usuarios y a agregarlos a un grupo de colecciones de sitios. Luego, usaremos un archivo .csv para cargar los nuevos usuarios y grupos de forma masiva.</span><span class="sxs-lookup"><span data-stu-id="339db-p109">Now you’re going to create users and add them to a site collection group. You will then use a .csv file to bulk upload new groups and users.</span></span>

<span data-ttu-id="339db-142">En estos procedimientos se da por hecho que ya se han creado las colecciones de sitios contosotest, TeamSite01, Blog01 y Project01.</span><span class="sxs-lookup"><span data-stu-id="339db-142">The following procedures assume that you successfully created the site collections contosotest, TeamSite01, Blog01, and Project01.</span></span>

### <a name="create-csv-and-ps1-files"></a><span data-ttu-id="339db-143">Crear los archivos .csv y .ps1</span><span class="sxs-lookup"><span data-stu-id="339db-143">Create .csv and .ps1 files</span></span>

1. <span data-ttu-id="339db-144">Abra el Bloc de notas y pegue el siguiente bloque de texto:</span><span class="sxs-lookup"><span data-stu-id="339db-144">Open Notepad, and paste the following text block into it:</span></span><br/>
```
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
<br/><span data-ttu-id="339db-145">Donde *inquilino* es el nombre del inquilino.</span><span class="sxs-lookup"><span data-stu-id="339db-145">Where *tenant* equals your tenant name.</span></span><br/>

2. <span data-ttu-id="339db-146">Guarde el archivo en el escritorio como **GroupsAndPermissions.csv**.</span><span class="sxs-lookup"><span data-stu-id="339db-146">Save the file to your desktop as **GroupsAndPermissions.csv**.</span></span><br/>

3. <span data-ttu-id="339db-147">Abra otra instancia del Bloc de notas y pegue el siguiente bloque de texto:</span><span class="sxs-lookup"><span data-stu-id="339db-147">Open a new instance of Notepad, and paste the following text block into it:</span></span><br/>

```
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
<br/><span data-ttu-id="339db-148">Donde *inquilino* es el nombre del inquilino y *nombre de usuario* es el nombre de usuario de un usuario existente.</span><span class="sxs-lookup"><span data-stu-id="339db-148">Where *tenant* equals your tenant name, and *username* equals the user name of an existing user.</span></span><br/>

4. <span data-ttu-id="339db-149">Guarde el archivo en el escritorio como **Users.csv**.</span><span class="sxs-lookup"><span data-stu-id="339db-149">Save the file to your desktop as **Users.csv**.</span></span><br/>

5. <span data-ttu-id="339db-150">Abra otra instancia del Bloc de notas y pegue el siguiente bloque de texto:</span><span class="sxs-lookup"><span data-stu-id="339db-150">Open a new instance of Notepad, and paste the following text block into it:</span></span><br/>

```
Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\users\MyAlias\desktop\Users.csv | where {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```
<br/><span data-ttu-id="339db-151">Donde MyAlias es el nombre de usuario del usuario que ha iniciado sesión actualmente.</span><span class="sxs-lookup"><span data-stu-id="339db-151">Where MyAlias equals the user name of the user that is currently logged on.</span></span><br/>

6. <span data-ttu-id="339db-p110">Guarde el archivo en el escritorio como **UsersAndGroups.ps1**. Este es un script de Windows PowerShell simple.</span><span class="sxs-lookup"><span data-stu-id="339db-p110">Save the file to your desktop as **UsersAndGroups.ps1**. This is a simple Windows PowerShell script.</span></span>

<span data-ttu-id="339db-154">Ya puede ejecutar el script UsersAndGroup.ps1 para agregar usuarios y grupos a varias colecciones de sitios.</span><span class="sxs-lookup"><span data-stu-id="339db-154">You’re now ready to run the UsersAndGroup.ps1 script to add users and groups to multiple site collections.</span></span>

### <a name="run-usersandgroupsps1-script"></a><span data-ttu-id="339db-155">Ejecutar el script UsersAndGroups.ps1</span><span class="sxs-lookup"><span data-stu-id="339db-155">Run UsersAndGroups.ps1 script</span></span>

1. <span data-ttu-id="339db-156">Vuelva al Shell de administración de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="339db-156">Return to the SharePoint Online Management Shell.</span></span><br/>
2. <span data-ttu-id="339db-157">En el símbolo del sistema de Windows PowerShell, escriba o copie y pegue la siguiente línea y presione ENTRAR:</span><span class="sxs-lookup"><span data-stu-id="339db-157">At the Windows PowerShell prompt, type or copy and paste the following line, and press Enter:</span></span><br/>
```
Set-ExecutionPolicy Bypass
```
<br/>

3. <span data-ttu-id="339db-158">En el símbolo del sistema de confirmación, presione **s.**</span><span class="sxs-lookup"><span data-stu-id="339db-158">At the confirmation prompt, press **Y**.</span></span><br/>

4. <span data-ttu-id="339db-159">En el símbolo del sistema de Windows PowerShell, escriba o copie y pegue lo siguiente y presione ENTRAR:</span><span class="sxs-lookup"><span data-stu-id="339db-159">At the Windows PowerShell prompt, type or copy and paste the following, and press Enter:</span></span><br/>

```
c:\users\MyAlias\desktop\UsersAndGroups.ps1
```
<br/><span data-ttu-id="339db-160">Donde *MyAlias* es igual a su nombre de usuario.</span><span class="sxs-lookup"><span data-stu-id="339db-160">Where *MyAlias* equals your user name.</span></span><br/>

5. <span data-ttu-id="339db-p111">Antes de continuar, espere a que el símbolo del sistema vuelva. Primero verá que los grupos aparecen según se han creado y, luego, verá la lista de grupos repetida a medida que se vayan agregando usuarios.</span><span class="sxs-lookup"><span data-stu-id="339db-p111">Wait for the prompt to return before moving on. You will first see the groups appear as they are created. Then you will see the group list repeated as users are added.</span></span>

## <a name="see-also"></a><span data-ttu-id="339db-164">Vea también</span><span class="sxs-lookup"><span data-stu-id="339db-164">See also</span></span>

[<span data-ttu-id="339db-165">Conectarse a SharePoint Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="339db-165">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="339db-166">Administrar grupos de sitio de SharePoint Online PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="339db-166">Manage SharePoint Online site groups Office 365 PowerShell</span></span>](manage-sharepoint-site-groups-with-powershell.md)

[<span data-ttu-id="339db-167">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="339db-167">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="339db-168">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="339db-168">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

