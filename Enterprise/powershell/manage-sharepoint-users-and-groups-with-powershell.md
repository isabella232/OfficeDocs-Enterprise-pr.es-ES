---
title: Administrar usuarios y grupos de SharePoint Online con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/05/2019
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
description: 'Resumen: Use Office 365 PowerShell para administrar usuarios, grupos y sitios de SharePoint Online.'
ms.openlocfilehash: e011946fa46455d1c1eba2bdff565bd55ec875bf
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2019
ms.locfileid: "38747625"
---
# <a name="manage-sharepoint-online-users-and-groups-with-office-365-powershell"></a><span data-ttu-id="ca712-103">Administrar usuarios y grupos de SharePoint Online con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="ca712-103">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>

<span data-ttu-id="ca712-104">Si es un administrador de SharePoint Online que trabaja con grandes listas de grupos o cuentas de usuario y quiere un método más fácil para administrarlos, puede usar Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ca712-104">If you are a SharePoint Online administrator who works with large lists of user accounts or groups and wants an easier way to manage them, you can use Office 365 PowerShell.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="ca712-105">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="ca712-105">Before you begin</span></span>

<span data-ttu-id="ca712-106">Los procedimientos de este tema requieren que se conecte a SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="ca712-106">The procedures in this topic require you to connect to SharePoint Online.</span></span> <span data-ttu-id="ca712-107">Para obtener instrucciones, vea [conectarse a PowerShell de SharePoint Online](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span><span class="sxs-lookup"><span data-stu-id="ca712-107">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span></span>

## <a name="get-a-list-of-sites-groups-and-users"></a><span data-ttu-id="ca712-108">Obtener una lista de sitios, grupos y usuarios</span><span class="sxs-lookup"><span data-stu-id="ca712-108">Get a list of sites, groups, and users</span></span>

<span data-ttu-id="ca712-p102">Antes de empezar a administrar usuarios y grupos, hay que conseguir las listas de los sitios, grupos y usuarios. Después puede usar esta información para trabajar con el ejemplo de este artículo.</span><span class="sxs-lookup"><span data-stu-id="ca712-p102">Before we start to manage users and groups, you need to get lists of your sites, groups, and users. You can then use this information to work through the example in this article.</span></span>

### <a name="get-a-list-of-sites"></a><span data-ttu-id="ca712-111">Conseguir una lista de sitios</span><span class="sxs-lookup"><span data-stu-id="ca712-111">Get a list of sites</span></span>

<span data-ttu-id="ca712-112">Obtenga la lista de los sitios de su inquilino con este comando:</span><span class="sxs-lookup"><span data-stu-id="ca712-112">Get a list of the sites in your tenant with this command:</span></span>

```powershell
Get-SPOSite
```

### <a name="get-a-list-of-groups"></a><span data-ttu-id="ca712-113">Conseguir una lista de grupos</span><span class="sxs-lookup"><span data-stu-id="ca712-113">Get a list of groups</span></span>

<span data-ttu-id="ca712-114">Obtenga la lista de los grupos de su inquilino con este comando:</span><span class="sxs-lookup"><span data-stu-id="ca712-114">Get a list of the groups in your tenant with this command:</span></span>

```powershell
Get-SPOSite | ForEach {Get-SPOSiteGroup -Site $_.Url} | Format-Table
```

### <a name="get-a-list-of-users"></a><span data-ttu-id="ca712-115">Conseguir una lista de usuarios</span><span class="sxs-lookup"><span data-stu-id="ca712-115">Get a list of users</span></span>

<span data-ttu-id="ca712-116">Obtenga la lista de los usuarios de su inquilino con este comando:</span><span class="sxs-lookup"><span data-stu-id="ca712-116">Get a list of the users in your tenant with this command:</span></span>

```powershell
Get-SPOSite | ForEach {Get-SPOUser -Site $_.Url}
```

## <a name="add-a-user-to-the-site-collection-administrators-group"></a><span data-ttu-id="ca712-117">Agregar un usuario al grupo Administradores de la colección de sitios</span><span class="sxs-lookup"><span data-stu-id="ca712-117">Add a user to the Site Collection Administrators group</span></span>

<span data-ttu-id="ca712-118">Para agregar un usuario a la lista de Administradores de la colección de sitios en una colección de sitios, hay que usar el comando **Set-SPOUser**.</span><span class="sxs-lookup"><span data-stu-id="ca712-118">You use the **Set-SPOUser** command to add a user to the list of Site Collection Administrators on a site collection.</span></span> <span data-ttu-id="ca712-119">Este es el aspecto de la sintaxis:</span><span class="sxs-lookup"><span data-stu-id="ca712-119">This is how the syntax looks:</span></span>

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
 ```

<span data-ttu-id="ca712-120">Para usar estos comandos, reemplace todo lo que haya entre las comillas, incluidos los caracteres < y >, con los nombres correctos.</span><span class="sxs-lookup"><span data-stu-id="ca712-120">To use these commands, replace replace everything within the quotes, including the < and > characters, with the correct names.</span></span>

<span data-ttu-id="ca712-121">Por ejemplo, este conjunto de comandos agrega Opal Castillo (User Name opalc) la lista de administradores de colecciones de sitios en la colección de sitios ContosoTest en el arrendamiento de Contoso1:</span><span class="sxs-lookup"><span data-stu-id="ca712-121">For example, this set of commands adds Opal Castillo (user name opalc) the list of Site Collection Administrators on the ContosoTest site collection in the contoso1 tenancy:</span></span>

```powershell
$tenant = "contoso1"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
```

<span data-ttu-id="ca712-122">Puede copiar y pegar estos comandos en el Bloc de notas, cambiar los valores de las variables para $tenant, $site y $user a valores reales de su entorno y, a continuación, pegarlos en la ventana del shell de administración de SharePoint Online para ejecutarlos.</span><span class="sxs-lookup"><span data-stu-id="ca712-122">You can copy and paste these commands into Notepad, change the variable values for $tenant, $site, and $user to actual values from your environment, and then paste this into your SharePoint Online Management Shell window to run them.</span></span>

## <a name="add-a-user-to-other-site-collection-groups"></a><span data-ttu-id="ca712-123">Agregar un usuario a otros grupos de la colección de sitios</span><span class="sxs-lookup"><span data-stu-id="ca712-123">Add a user to other site collection groups</span></span>

<span data-ttu-id="ca712-124">En esta tarea, vamos a usar el comando **Add-SPOUser** para agregar un usuario a un grupo de SharePoint en una colección de sitios.</span><span class="sxs-lookup"><span data-stu-id="ca712-124">In this task, we'll use the **Add-SPOUser** command to add a user to a SharePoint group on a site collection.</span></span>

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site

```

<span data-ttu-id="ca712-125">Por ejemplo, vamos a agregar a Glen Rife (nombre de usuario: glenr) al grupo Auditors en la colección de sitios ContosoTest en el arrendamiento contoso1:</span><span class="sxs-lookup"><span data-stu-id="ca712-125">For example, let’s add Glen Rife (user name glenr) to the Auditors group on the ContosoTest site collection in the contoso1 tenancy:</span></span>

```powershell
$tenant = "contoso1"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a><span data-ttu-id="ca712-126">Crear un grupo de colecciones de sitios</span><span class="sxs-lookup"><span data-stu-id="ca712-126">Create a site collection group</span></span>

<span data-ttu-id="ca712-127">Use el comando **New-SPOSiteGroup** para crear un nuevo grupo de SharePoint y agregarlo a la colección de sitios ContosoTest.</span><span class="sxs-lookup"><span data-stu-id="ca712-127">You use the **New-SPOSiteGroup** command to create a new SharePoint group and add it to the ContosoTest site collection.</span></span>

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$group = "<group name name, such as Auditors>"
$level = "<permission level, such as View Only>"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```
<span data-ttu-id="ca712-128">Las propiedades de grupo, como los niveles de permisos, se pueden actualizar más adelante mediante el cmdlet **Set-SPOSiteGroup**.</span><span class="sxs-lookup"><span data-stu-id="ca712-128">Group properties, such as permission levels, can be updated later by using the **Set-SPOSiteGroup** cmdlet.</span></span>

<span data-ttu-id="ca712-129">Por ejemplo, vamos a agregar el grupo Auditors con permisos de solo vista a la colección de sitios contoso test en el arrendamiento Contoso1:</span><span class="sxs-lookup"><span data-stu-id="ca712-129">For example, let’s add the Auditors group with View Only permissions to the Contoso Test site collection in the contoso1 tenancy:</span></span>

```powershell
$tenant = "contoso1"
$site = "Contoso Test"
$group = "Auditors"
$level = "View Only"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a><span data-ttu-id="ca712-130">Quitar usuarios de un grupo</span><span class="sxs-lookup"><span data-stu-id="ca712-130">Remove users from a group</span></span>

<span data-ttu-id="ca712-p104">A veces, es necesario quitar un usuario de un sitio o incluso de todos los sitios. Tal vez el empleado se mueva de una división a otra o abandone la compañía. Puede hacer esto fácilmente para un empleado en la interfaz de usuario, pero no es tan fácil cuando hay que mover una división completa de un sitio a otro.</span><span class="sxs-lookup"><span data-stu-id="ca712-p104">Sometimes you have to remove a user from a site or even all sites. Perhaps the employee moves from one division to another or leaves the company. You can do this for one employee easily in the UI, but this is not easily done when you have to move a complete division from one site to another.</span></span>

<span data-ttu-id="ca712-134">Sin embargo, con el shell de administración de SharePoint Online y los archivos CSV, esto es rápido y fácil.</span><span class="sxs-lookup"><span data-stu-id="ca712-134">However by using the SharePoint Online Management Shell and CSV files, this is fast and easy.</span></span> <span data-ttu-id="ca712-135">En esta tarea, vamos a usar Windows PowerShell para quitar un usuario de un grupo de seguridad de la colección de sitios.</span><span class="sxs-lookup"><span data-stu-id="ca712-135">In this task, you'll use Windows PowerShell to remove a user from a site collection security group.</span></span> <span data-ttu-id="ca712-136">A continuación, puede usar un archivo CSV y quitar muchos usuarios de distintos sitios.</span><span class="sxs-lookup"><span data-stu-id="ca712-136">Then you'll use a CSV file and remove lots of users from different sites.</span></span> 

<span data-ttu-id="ca712-137">Usaremos el comando **Remove-cónyuge** para quitar un solo usuario de Office 365 de un grupo de colección de sitios para que podamos ver la sintaxis del comando.</span><span class="sxs-lookup"><span data-stu-id="ca712-137">We'll be using the **Remove-SPOUser** command to remove a single Office 365 user from a site collection group just so we can see the command syntax.</span></span> <span data-ttu-id="ca712-138">Este es el aspecto de la sintaxis:</span><span class="sxs-lookup"><span data-stu-id="ca712-138">Here is how the syntax looks:</span></span>

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```
<span data-ttu-id="ca712-139">Por ejemplo, vamos a quitar Alberto Overby del grupo auditores de la colección de sitios en la colección de sitios de prueba de Contoso en el arrendamiento Contoso1:</span><span class="sxs-lookup"><span data-stu-id="ca712-139">For example, let’s remove Bobby Overby from the site collection Auditors group in the Contoso Test site collection in the contoso1 tenancy:</span></span>

```powershell
$tenant = "contoso1"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

<span data-ttu-id="ca712-140">Supongamos que quisiéramos quitar a Bobby de todos los grupos a los que pertenece.</span><span class="sxs-lookup"><span data-stu-id="ca712-140">Suppose we wanted to remove Bobby from all the groups he is currently in.</span></span> <span data-ttu-id="ca712-141">Este es el método que usaríamos para hacerlo:</span><span class="sxs-lookup"><span data-stu-id="ca712-141">Here is how we would do that:</span></span>

```powershell
$tenant = "contoso1"
$user = "bobbyo"
Get-SPOSite | ForEach {Get-SPOSiteGroup –Site $_.Url} | ForEach {Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site &_.Url}
```

> [!WARNING]
> <span data-ttu-id="ca712-142">Esto es solo un ejemplo.</span><span class="sxs-lookup"><span data-stu-id="ca712-142">This is just an example.</span></span> <span data-ttu-id="ca712-143">No debe ejecutar este comando a menos que realmente tenga que quitar un usuario de cada grupo, por ejemplo, si el usuario deja la empresa.</span><span class="sxs-lookup"><span data-stu-id="ca712-143">You should not run this command unless you really have to remove a user from every group, for example if the user leaves the company.</span></span>

## <a name="automate-management-of-large-lists-of-users-and-groups"></a><span data-ttu-id="ca712-144">Automatizar la administración de grandes listas de usuarios y grupos</span><span class="sxs-lookup"><span data-stu-id="ca712-144">Automate management of large lists of users and groups</span></span>

<span data-ttu-id="ca712-145">Para agregar un gran número de cuentas a los sitios de SharePoint y concederles permisos, puede usar el centro de administración de Microsoft 365, los comandos de PowerShell individuales o PowerShell en un archivo CSV.</span><span class="sxs-lookup"><span data-stu-id="ca712-145">To add a large number of accounts to SharePoint sites and give them permissions, you can use the Microsoft 365 admin center, individual PowerShell commands, or PowerShell an a CSV file.</span></span> <span data-ttu-id="ca712-146">De estas opciones, el uso del archivo CSV es la forma más rápida de automatizar esta tarea.</span><span class="sxs-lookup"><span data-stu-id="ca712-146">Of these choices, the CSV file is the fastest way to automate this task.</span></span>

<span data-ttu-id="ca712-147">El proceso básico consiste en crear un archivo CSV que tiene encabezados (columnas) que se corresponden con los parámetros que el script de Windows PowerShell necesita.</span><span class="sxs-lookup"><span data-stu-id="ca712-147">The basic process is to create a CSV file that has headers (columns) that correspond to the parameters that the Windows PowerShell script needs.</span></span> <span data-ttu-id="ca712-148">Puede crear fácilmente dicha lista en Excel y, a continuación, exportarla como un archivo CSV.</span><span class="sxs-lookup"><span data-stu-id="ca712-148">You can easily create such a list in Excel and then export it as a CSV file.</span></span> <span data-ttu-id="ca712-149">A continuación, puede usar un script de Windows PowerShell para iterar a través de registros (filas) en el archivo CSV, agregar los usuarios a los grupos y los grupos a los sitios.</span><span class="sxs-lookup"><span data-stu-id="ca712-149">Then, you use a Windows PowerShell script to iterate through records (rows) in the CSV file, adding the users to groups and the groups to sites.</span></span> 

<span data-ttu-id="ca712-p111">Por ejemplo, vamos a crear un archivo CSV para definir un grupo de colecciones de sitios, grupos y permisos. A continuación, vamos a crear un archivo CSV para rellenar los grupos con usuarios. Por último, vamos a crear y ejecutar un script de Windows PowerShell que cree y rellene los grupos.</span><span class="sxs-lookup"><span data-stu-id="ca712-p111">For example, let’s create a CSV file to define a group of site collections, groups, and permissions. Next, we will create a CSV file to populate the groups with users. Finally, we will create and run a simple Windows PowerShell script that creates and populates the groups.</span></span>

<span data-ttu-id="ca712-153">El primer archivo CSV agregará uno o más grupos a una o más colecciones de sitios y tendrá esta estructura:</span><span class="sxs-lookup"><span data-stu-id="ca712-153">The first CSV file will add one or more groups to one or more site collections and will have this structure:</span></span>

### <a name="header"></a><span data-ttu-id="ca712-154">CAB</span><span class="sxs-lookup"><span data-stu-id="ca712-154">Header:</span></span>

```powershell
Site,Group,PermissionLevels
```

### <a name="item"></a><span data-ttu-id="ca712-155">Punto</span><span class="sxs-lookup"><span data-stu-id="ca712-155">Item:</span></span>

```powershell
https://tenant.sharepoint.com/sites/site,group,level
```

<span data-ttu-id="ca712-156">Este es un archivo de ejemplo:</span><span class="sxs-lookup"><span data-stu-id="ca712-156">Here is an example file:</span></span>

```powershell
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

<span data-ttu-id="ca712-157">El segundo archivo CSV agregará uno o varios usuarios a uno o varios grupos y tendrá esta estructura:</span><span class="sxs-lookup"><span data-stu-id="ca712-157">The second CSV file will add one or more users to one or more groups and will have this structure:</span></span>

### <a name="header"></a><span data-ttu-id="ca712-158">CAB</span><span class="sxs-lookup"><span data-stu-id="ca712-158">Header:</span></span>

```powershell
Group,LoginName,Site
```

### <a name="item"></a><span data-ttu-id="ca712-159">Punto</span><span class="sxs-lookup"><span data-stu-id="ca712-159">Item:</span></span>

```powershell
group,login,https://tenant.sharepoint.com/sites/site
```

<span data-ttu-id="ca712-160">Este es un archivo de ejemplo:</span><span class="sxs-lookup"><span data-stu-id="ca712-160">Here is an example file:</span></span>

```powershell
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

<span data-ttu-id="ca712-161">En el paso siguiente, debe tener los dos archivos CSV guardados en la unidad.</span><span class="sxs-lookup"><span data-stu-id="ca712-161">For the next step, you must have the two CSV files saved to your drive.</span></span> <span data-ttu-id="ca712-162">A continuación se muestran ejemplos de comandos que usan archivos CSV y para agregar permisos y pertenencia a grupos:</span><span class="sxs-lookup"><span data-stu-id="ca712-162">Here are example commands that use both CSV files and to add permissions and group membership:</span></span>

```powershell
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

<span data-ttu-id="ca712-163">El script importa el contenido del archivo CSV y usa los valores de las columnas para rellenar los parámetros de los comandos **New-SPOSiteGroup** y **Add-cónyugeer** .</span><span class="sxs-lookup"><span data-stu-id="ca712-163">The script imports the CSV file contents and uses the values in the columns to populate the parameters of the **New-SPOSiteGroup** and **Add-SPOUser** commands.</span></span> <span data-ttu-id="ca712-164">En nuestro ejemplo, lo estamos guardando en la carpeta theO365Admin de la unidad C, pero puede guardarla dondequiera que quiera.</span><span class="sxs-lookup"><span data-stu-id="ca712-164">In our example, we are saving this to theO365Admin folder on drive C, but you can save it wherever you want.</span></span>

<span data-ttu-id="ca712-165">Ahora, vamos a quitar unas cuantas personas de varios grupos en distintos sitios usando el mismo archivo CSV.</span><span class="sxs-lookup"><span data-stu-id="ca712-165">Now, let’s remove a bunch of people for several groups in different sites using the same CSV file.</span></span> <span data-ttu-id="ca712-166">A continuación se muestra un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="ca712-166">Here is an example command:</span></span>

```powershell
Import-Csv C:\O365Admin\Users.csv | ForEach {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a><span data-ttu-id="ca712-167">Generar informes de usuario</span><span class="sxs-lookup"><span data-stu-id="ca712-167">Generate user reports</span></span>

<span data-ttu-id="ca712-p115">Tal vez desee obtener un informe sencillo para unos cuantos sitios y mostrar los usuarios de dichos sitios, su nivel de permisos y otras propiedades. Este es el aspecto de la sintaxis:</span><span class="sxs-lookup"><span data-stu-id="ca712-p115">You might want to get a simple report for a few sites and display the users for those sites, their permission level, and other properties. This is how the syntax looks:</span></span>

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="ca712-170">Esto tomará los datos de estos tres sitios y los escribirá en un archivo de texto de la unidad local.</span><span class="sxs-lookup"><span data-stu-id="ca712-170">This will grab the data for these three sites and write them to a text file on your local drive.</span></span> <span data-ttu-id="ca712-171">Tenga en cuenta que el parámetro –Append agregará nuevo contenido a un archivo existente.</span><span class="sxs-lookup"><span data-stu-id="ca712-171">Note that the parameter –Append will add new content to an existing file.</span></span>

<span data-ttu-id="ca712-172">Por ejemplo, vamos a ejecutar un informe en los sitios ContosoTest, TeamSite01 y Project01 para el inquilino Contoso1:</span><span class="sxs-lookup"><span data-stu-id="ca712-172">For example, let's run a report on the ContosoTest, TeamSite01, and Project01 sites for the Contoso1 tenant:</span></span>

```powershell
$tenant = "contoso1"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="ca712-173">Tenga en cuenta que sólo tuvimos que cambiar la variable **$site** .</span><span class="sxs-lookup"><span data-stu-id="ca712-173">Note that we had to change only the **$site** variable.</span></span> <span data-ttu-id="ca712-174">La variable **$tenant** mantiene su valor en las tres ejecuciones del comando.</span><span class="sxs-lookup"><span data-stu-id="ca712-174">The **$tenant** variable keeps its value through all three runs of the command.</span></span>

<span data-ttu-id="ca712-p118">Sin embargo, ¿qué pasa si quisiera hacer esto para cada sitio? Puede hacerlo sin tener que escribir todos los sitios web con este comando:</span><span class="sxs-lookup"><span data-stu-id="ca712-p118">However, what if you wanted to do this for every site? You can do this without having to type all those websites by using this command:</span></span>

```powershell
Get-SPOSite | ForEach {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="ca712-177">Este informe es bastante sencillo y podemos agregar más código para crear informes más específicos o que incluyan información más detallada.</span><span class="sxs-lookup"><span data-stu-id="ca712-177">This report is fairly simple, and you can add more code to create more specific reports or reports that include more detailed information.</span></span> <span data-ttu-id="ca712-178">Pero esto debería dar una idea de cómo usar el shell de administración de SharePoint Online para administrar usuarios en el entorno de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="ca712-178">But this should give you an idea of how to use the SharePoint Online Management Shell to manage users in the SharePoint Online environment.</span></span>
   
## <a name="see-also"></a><span data-ttu-id="ca712-179">Vea también</span><span class="sxs-lookup"><span data-stu-id="ca712-179">See also</span></span>

[<span data-ttu-id="ca712-180">Conectarse a SharePoint Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="ca712-180">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="ca712-181">Administrar SharePoint Online con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="ca712-181">Manage SharePoint Online with Office 365 PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

[<span data-ttu-id="ca712-182">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="ca712-182">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="ca712-183">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="ca712-183">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

