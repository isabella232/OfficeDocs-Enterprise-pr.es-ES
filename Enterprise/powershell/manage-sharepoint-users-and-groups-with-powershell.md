---
title: Administrar usuarios y grupos de SharePoint Online con PowerShell de Office 365
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
description: 'Resumen: Use PowerShell de Office 365 para administrar usuarios, grupos y sitios de SharePoint Online.'
ms.openlocfilehash: 8ed40d2c736853145e21f0f9852bdb18c7842075
ms.sourcegitcommit: 74cdb2534bce376abc9cf4fef85ff039c46ee790
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="manage-sharepoint-online-users-and-groups-with-office-365-powershell"></a><span data-ttu-id="44dd7-103">Administrar usuarios y grupos de SharePoint Online con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="44dd7-103">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>

 <span data-ttu-id="44dd7-104">**Resumen:** Usar PowerShell de Office 365 para administrar usuarios, grupos y sitios de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="44dd7-104">**Summary:** Use Office 365 PowerShell to manage SharePoint Online users, groups, and sites.</span></span>

<span data-ttu-id="44dd7-105">Si es un SharePoint Online que funciona con listas de gran tamaño de las cuentas de usuario o grupos y desea una manera más fácil de administrar ellos, puede usar PowerShell de Office 365.</span><span class="sxs-lookup"><span data-stu-id="44dd7-105">If you are a SharePoint Online who works with large lists of user accounts or groups and wants an easier way to manage them, you can use Office 365 PowerShell.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="44dd7-106">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="44dd7-106">Before you begin</span></span>

<span data-ttu-id="44dd7-p101">Los procedimientos descritos en este tema requieren que se va a conectar a SharePoint Online. Para obtener instrucciones, vea [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span><span class="sxs-lookup"><span data-stu-id="44dd7-p101">The procedures in this topic require you to connect to SharePoint Online. For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span></span>

## <a name="get-a-list-of-sites-groups-and-users"></a><span data-ttu-id="44dd7-109">Obtener una lista de sitios, grupos y usuarios</span><span class="sxs-lookup"><span data-stu-id="44dd7-109">Get a list of sites, groups, and users</span></span>

<span data-ttu-id="44dd7-p102">Antes de empezar a administrar usuarios y grupos, hay que conseguir las listas de los sitios, grupos y usuarios. Después puede usar esta información para trabajar con el ejemplo de este artículo.</span><span class="sxs-lookup"><span data-stu-id="44dd7-p102">Before we start to manage users and groups, you need to get lists of your sites, groups, and users. You can then use this information to work through the example in this article.</span></span>

### <a name="get-a-list-of-sites"></a><span data-ttu-id="44dd7-112">Conseguir una lista de sitios</span><span class="sxs-lookup"><span data-stu-id="44dd7-112">Get a list of sites</span></span>

<span data-ttu-id="44dd7-113">Obtenga la lista de los sitios de su inquilino con este comando:</span><span class="sxs-lookup"><span data-stu-id="44dd7-113">Get a list of the sites in your tenant with this command:</span></span>

```
Get-SPOSite
```

### <a name="get-a-list-of-groups"></a><span data-ttu-id="44dd7-114">Conseguir una lista de grupos</span><span class="sxs-lookup"><span data-stu-id="44dd7-114">Get a list of groups</span></span>

<span data-ttu-id="44dd7-115">Obtenga la lista de los grupos de su inquilino con este comando:</span><span class="sxs-lookup"><span data-stu-id="44dd7-115">Get a list of the groups in your tenant with this command:</span></span>

```
Get-SPOSite | ForEach-Object {Get-SPOSiteGroup -Site $_.Url} |Format-Table
```

### <a name="get-a-list-of-users"></a><span data-ttu-id="44dd7-116">Conseguir una lista de usuarios</span><span class="sxs-lookup"><span data-stu-id="44dd7-116">Get a list of users</span></span>

<span data-ttu-id="44dd7-117">Obtenga la lista de los usuarios de su inquilino con este comando:</span><span class="sxs-lookup"><span data-stu-id="44dd7-117">Get a list of the users in your tenant with this command:</span></span>

```Get-SPOSite | ForEach-Object {Get-SPOUser -Site $_.Url}```

## <a name="add-a-user-to-the-site-collection-administrators-group"></a><span data-ttu-id="44dd7-118">Agregar un usuario al grupo Administradores de la colección de sitios</span><span class="sxs-lookup"><span data-stu-id="44dd7-118">Add a user to the Site Collection Administrators group</span></span>

<span data-ttu-id="44dd7-p103">Use el comando **Set-SPOUser** para agregar un usuario a la lista de administradores de colección de sitios en una colección de sitios. Este es el aspecto de la sintaxis:</span><span class="sxs-lookup"><span data-stu-id="44dd7-p103">You use the **Set-SPOUser** command to add a user to the list of Site Collection Administrators on a site collection. This is how the syntax looks:</span></span>

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks. Example: "Contoso01"-->
$site = "site"
<!--# This is the Site name. Value must be enclosed in double quotation marks. Example: "contosotest"-->
$user = "loginname"
<!--This is the users login name. Value must be enclosed in double quotation marks. Example "opalc"-->
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
 ```

<span data-ttu-id="44dd7-121">En este ejemplo se usa variables para almacenar los valores y tiene notas en la secuencia de comandos (por ejemplo "<!--This is the Tenant Name…-->") que le ayudarán a comprender qué deben esos valores.</span><span class="sxs-lookup"><span data-stu-id="44dd7-121">This example uses variables to store values and has notes in the script (for example "<!--This is the Tenant Name…-->") to help you understand what those values should be.</span></span>

<span data-ttu-id="44dd7-122">Por ejemplo, este conjunto de comandos agrega Opal Castillo (opalc de nombre de usuario) la lista de administradores de colección de sitios en la colección de sitios ContosoTest en el inquilino contoso1:</span><span class="sxs-lookup"><span data-stu-id="44dd7-122">For example, this set of commands adds Opal Castillo (user name opalc) the list of Site Collection Administrators on the ContosoTest site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
```

<span data-ttu-id="44dd7-123">De hecho, puede cortar y pegar estos comandos en el Bloc de notas, cambiar los valores de variable de $tenant, $site y $user por valores reales del entorno y después pegarlos en la ventana del Shell de administración de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="44dd7-123">You can actually cut and paste these commands into Notepad, change the variable values for $tenant, $site, and $user to actual values from your environment, and then paste this into your SharePoint Online Management Shell window.</span></span>

## <a name="add-a-user-to-other-site-collection-administrators-groups"></a><span data-ttu-id="44dd7-124">Agregar un usuario a otros grupos de administradores de la colección de sitios</span><span class="sxs-lookup"><span data-stu-id="44dd7-124">Add a user to other Site Collection Administrators groups</span></span>

<span data-ttu-id="44dd7-p104">En esta tarea, se usará el comando **Add-SPOUser** para agregar un usuario a un grupo de SharePoint en una colección de sitios. Este es el aspecto de la sintaxis:</span><span class="sxs-lookup"><span data-stu-id="44dd7-p104">In this task, we'll use the **Add-SPOUser** command to add a user to a SharePoint group on a site collection. This is how the syntax looks:</span></span>

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks. Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotation marks. Example: "contosotest"-->
$user = "loginname"
<!--This is the users login name. Value must be enclosed in double quotation marks. Example: "opalc"-->
$group = "group"
<!--This is the SharePoint security Group name. Value must be enclosed in double quotation marks. Example: "Auditors"-->
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site

```

<span data-ttu-id="44dd7-127">Por ejemplo, vamos a agregar Glen abundan (glenr de nombre de usuario) al grupo en la colección de sitios ContosoTest en el inquilino contoso1 auditores:</span><span class="sxs-lookup"><span data-stu-id="44dd7-127">For example, let’s add Glen Rife (user name glenr) to the Auditors group on the ContosoTest site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a><span data-ttu-id="44dd7-128">Crear un grupo de colecciones de sitios</span><span class="sxs-lookup"><span data-stu-id="44dd7-128">Create a site collection group</span></span>

<span data-ttu-id="44dd7-p105">Use el comando **Set-SPOSiteGroup** para crear un nuevo grupo de SharePoint y agregarlo a la colección de sitios ContosoTest. Este es el aspecto de la sintaxis:</span><span class="sxs-lookup"><span data-stu-id="44dd7-p105">You use the **Set-SPOSiteGroup** command to create a new SharePoint group and add it to the ContosoTest site collection. This is how the syntax looks:</span></span>

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks, Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotation marks, Example: "contosotest"-->
$group = "group"
<!--This is the SharePoint security Group name. Value must be enclosed in double quotation marks, Example: "Auditors"-->
$level = "permission level"
<!--This is the level of permissions to assign to the group. Value must be enclosed in double quotation marks, Example: "View Only"-->
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

> [!IMPORTANT]
> <span data-ttu-id="44dd7-p106">Debe incluir cualquier cadena con espacios entre comillas. Las propiedades de grupo, como los niveles de permisos se pueden actualizar más adelante mediante el cmdlet **Set-SPOSiteGroup** .</span><span class="sxs-lookup"><span data-stu-id="44dd7-p106">You must enclose any string with spaces in quotation marks. Group properties, such as permission levels, can be updated later by using the **Set-SPOSiteGroup** cmdlet.</span></span>

<span data-ttu-id="44dd7-133">Por ejemplo, vamos a agregar el grupo auditores con permisos de sólo lectura a la colección de sitios de prueba de Contoso en el inquilino contoso1:</span><span class="sxs-lookup"><span data-stu-id="44dd7-133">For example, let’s add the Auditors group with View Only permissions to the Contoso Test site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "Contoso Test"
$level = "View Only"
$group = "Auditors"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a><span data-ttu-id="44dd7-134">Quitar usuarios de un grupo</span><span class="sxs-lookup"><span data-stu-id="44dd7-134">Remove users from a group</span></span>

<span data-ttu-id="44dd7-p107">A veces, es necesario quitar un usuario de un sitio o incluso de todos los sitios. Tal vez el empleado se mueva de una división a otra o abandone la compañía. Puede hacer esto fácilmente para un empleado en la interfaz de usuario, pero no es tan fácil cuando hay que mover una división completa de un sitio a otro.</span><span class="sxs-lookup"><span data-stu-id="44dd7-p107">Sometimes you have to remove a user from a site or even all sites. Perhaps the employee moves from one division to another or leaves the company. You can do this for one employee easily in the UI, but this is not easily done when you have to move a complete division from one site to another.</span></span>

<span data-ttu-id="44dd7-p108">Sin embargo, mediante el uso de los archivos de Shell de administración de SharePoint Online y CSV, esto es rápido y fácil. En esta tarea, debe usar Windows PowerShell para quitar un usuario de un grupo de seguridad de la colección de sitios. A continuación, podrá usar un archivo CSV y quitar una gran cantidad de usuarios de sitios diferentes.</span><span class="sxs-lookup"><span data-stu-id="44dd7-p108">However by using the SharePoint Online Management Shell and CSV files, this is fast and easy. In this task, you'll use Windows PowerShell to remove a user from a site collection security group. Then you'll use a CSV file and remove lots of users from different sites.</span></span> 

<span data-ttu-id="44dd7-p109">Se se van a usar el comando **Remove-SPOUser** para quitar un único usuario de Office 365 de un grupo de la colección de sitios sólo para poder ver la sintaxis del comando. Aquí es el aspecto de la sintaxis:</span><span class="sxs-lookup"><span data-stu-id="44dd7-p109">We'll be using the **Remove-SPOUser** command to remove a single Office 365 user from a site collection group just so we can see the command syntax. Here is how the syntax looks:</span></span>

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks, Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotation marks, Example: "contosotest"-->
$group = "group"
<!--This is the SharePoint security Group name. Value must be enclosed in double quotation marks, Example: "Auditors"-->
$user = "loginname"
<!--This is the user’s login name. Value must be enclosed in double quotation marks, Example: "opalc"-->
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site
```

<span data-ttu-id="44dd7-143">Por ejemplo, vamos a quitar Bobby Overby desde el grupo de auditores de colección de sitios en la colección de sitios de prueba de Contoso en el inquilino contoso1:</span><span class="sxs-lookup"><span data-stu-id="44dd7-143">For example, let’s remove Bobby Overby from the site collection Auditors group in the Contoso Test site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

<span data-ttu-id="44dd7-p110">Supongamos que quisiéramos quitar a Bobby de todos los grupos a los que pertenece. Este es el método que usaríamos para hacerlo:</span><span class="sxs-lookup"><span data-stu-id="44dd7-p110">Suppose we wanted to remove Bobby from all the groups he is currently in. Here is how we would do that:</span></span>

```
$tenant = "contoso1"
$user = "bobbyo"
Get-SPOSite | ForEach-Object {Get-SPOSiteGroup –Site $_.Url} | ForEach-Object {Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site &_.Url}
```

> [!WARNING]
> <span data-ttu-id="44dd7-p111">Esto es solo para mostrarle cómo hacerlo. No debe ejecutar este comando a menos que realmente tenga que quitar un usuario de cada grupo, por ejemplo, si el usuario deja la empresa.</span><span class="sxs-lookup"><span data-stu-id="44dd7-p111">This is just to show how to do this. You should not run this command unless you really have to remove a user from every group, for example if the user leaves the company.</span></span>

## <a name="automate-management-of-large-lists-of-users-and-groups"></a><span data-ttu-id="44dd7-148">Automatizar la administración de grandes listas de usuarios y grupos</span><span class="sxs-lookup"><span data-stu-id="44dd7-148">Automate management of large lists of users and groups</span></span>

<span data-ttu-id="44dd7-p112">Para agregar un gran número de cuentas para los sitios de SharePoint y conceda permisos, puede usar el centro de administración de Office 365, los comandos de PowerShell individuales o PowerShell un un archivo CSV. De estas opciones, el archivo CSV es la forma más rápida para automatizar esta tarea.</span><span class="sxs-lookup"><span data-stu-id="44dd7-p112">To add a large number of accounts to SharePoint sites and give them permissions, you can use the Office 365 admin center, individual PowerShell commands, or PowerShell an a CSV file. Of these choices, the CSV file is the fastest way to automate this task.</span></span>

<span data-ttu-id="44dd7-p113">El proceso básico es crear un archivo CSV que tiene encabezados (columnas) que se corresponden con los parámetros que necesita la secuencia de comandos de Windows PowerShell. Puede crear fácilmente como una lista en Excel y, a continuación, se exporta como un archivo CSV. A continuación, use un script de Windows PowerShell para iterar a través de registros (filas) en el archivo CSV, agregar los usuarios a grupos y los grupos a los sitios.</span><span class="sxs-lookup"><span data-stu-id="44dd7-p113">The basic process is to create a CSV file that has headers (columns) that correspond to the parameters that the Windows PowerShell script needs. You can easily create such a list in Excel and then export it as a CSV file. Then, you use a Windows PowerShell script to iterate through records (rows) in the CSV file, adding the users to groups and the groups to sites.</span></span> 

<span data-ttu-id="44dd7-p114">Por ejemplo, vamos a crear un archivo CSV para definir un grupo de colecciones de sitios, grupos y permisos. A continuación, vamos a crear un archivo CSV para rellenar los grupos con usuarios. Por último, vamos a crear y ejecutar un script de Windows PowerShell que cree y rellene los grupos.</span><span class="sxs-lookup"><span data-stu-id="44dd7-p114">For example, let’s create a CSV file to define a group of site collections, groups, and permissions. Next, we will create a CSV file to populate the groups with users. Finally, we will create and run a simple Windows PowerShell script that creates and populates the groups.</span></span>

<span data-ttu-id="44dd7-157">El primer archivo CSV agregará uno o más grupos a una o más colecciones de sitios y tendrá esta estructura:</span><span class="sxs-lookup"><span data-stu-id="44dd7-157">The first CSV file will add one or more groups to one or more site collections and will have this structure:</span></span>

### <a name="header"></a><span data-ttu-id="44dd7-158">Encabezado:</span><span class="sxs-lookup"><span data-stu-id="44dd7-158">Header:</span></span>

```
Site,Group,PermissionLevels
```

### <a name="item"></a><span data-ttu-id="44dd7-159">Elemento:</span><span class="sxs-lookup"><span data-stu-id="44dd7-159">Item:</span></span>

```
https://tenant.sharepoint.com/sites/site,site collection,group,level
```

<span data-ttu-id="44dd7-160">Este es un archivo de ejemplo:</span><span class="sxs-lookup"><span data-stu-id="44dd7-160">Here is an example file:</span></span>

```
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

<span data-ttu-id="44dd7-161">El segundo archivo CSV agregará uno o varios usuarios a uno o varios grupos y tendrá esta estructura:</span><span class="sxs-lookup"><span data-stu-id="44dd7-161">The second CSV file will add one or more users to one or more groups and will have this structure:</span></span>

### <a name="header"></a><span data-ttu-id="44dd7-162">Encabezado:</span><span class="sxs-lookup"><span data-stu-id="44dd7-162">Header:</span></span>

```
Group,LoginName,Site
```

### <a name="item"></a><span data-ttu-id="44dd7-163">Elemento:</span><span class="sxs-lookup"><span data-stu-id="44dd7-163">Item:</span></span>

```
group,login,https://tenant.sharepoint.com/sites/site
```

<span data-ttu-id="44dd7-164">Este es un archivo de ejemplo:</span><span class="sxs-lookup"><span data-stu-id="44dd7-164">Here is an example file:</span></span>

```
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

<span data-ttu-id="44dd7-p115">En el paso siguiente, debe tener los dos archivos CSV guardados en la unidad. Estos son los comandos que usan los dos archivos CSV para agregar permisos y la pertenencia al grupo:</span><span class="sxs-lookup"><span data-stu-id="44dd7-p115">For the next step, you must have the two CSV files saved to your drive. Here are the commands that use both CSV files and to add permissions and group membership:</span></span>

```
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach-Object {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

<span data-ttu-id="44dd7-p116">La secuencia de comandos importa el contenido del archivo CSV y utiliza los valores de las columnas (en negrita) para rellenar los parámetros de los comandos **New-SPOSiteGroup** y **Add-SPOUser** . En nuestro ejemplo, también ahorramos a la unidad C, pero puede guardar siempre que lo desee.</span><span class="sxs-lookup"><span data-stu-id="44dd7-p116">The script imports the CSV file contents and uses the values in the columns (in bold) to populate the parameters of the **New-SPOSiteGroup** and **Add-SPOUser** commands. In our example, we are saving this to the drive C, but you can save it wherever you want.</span></span>

<span data-ttu-id="44dd7-p117">Ahora, vamos a quitar unas cuantas personas de varios grupos en distintos sitios usando el mismo archivo CSV. Este es el comando:</span><span class="sxs-lookup"><span data-stu-id="44dd7-p117">Now, let’s remove a bunch of people for several groups in different sites using the same CSV file. Here is the command:</span></span>

```
Import-Csv C:\O365Admin\Users.csv | ForEach-Object {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a><span data-ttu-id="44dd7-171">Generar informes de usuario</span><span class="sxs-lookup"><span data-stu-id="44dd7-171">Generate user reports</span></span>

<span data-ttu-id="44dd7-p118">Tal vez desee obtener un informe sencillo para unos cuantos sitios y mostrar los usuarios de dichos sitios, su nivel de permisos y otras propiedades. Este es el aspecto de la sintaxis:</span><span class="sxs-lookup"><span data-stu-id="44dd7-p118">You might want to get a simple report for a few sites and display the users for those sites, their permission level, and other properties. This is how the syntax looks:</span></span>

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotes, Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotes, Example: "contosotest"-->
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="44dd7-p119">Esto va a obtener los datos para estos tres sitios y escribirlos en un archivo de texto en la unidad local. Tenga en cuenta que el parámetro – Append va a agregar nuevo contenido a un archivo existente.</span><span class="sxs-lookup"><span data-stu-id="44dd7-p119">This will grab the data for these three sites and write them to a text file on your local drive. Note that the parameter –Append will add new content to an existing file.</span></span>

<span data-ttu-id="44dd7-176">Por ejemplo, vamos a ejecutar un informe en los sitios ContosoTest, TeamSite01 y Project01 para el inquilino Contoso1:</span><span class="sxs-lookup"><span data-stu-id="44dd7-176">For example, let's run a report on the ContosoTest, TeamSite01, and Project01 sites for the Contoso1 tenant:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="44dd7-p120">Tenga en cuenta que hemos tenido que cambiar sólo la variable **$site** . La variable **$tenant** mantiene su valor a través de todas las ejecuciones de tres del comando.</span><span class="sxs-lookup"><span data-stu-id="44dd7-p120">Note that we had to change only the **$site** variable. The **$tenant** variable keeps its value through all three runs of the command.</span></span>

<span data-ttu-id="44dd7-p121">Sin embargo, ¿qué pasa si quisiera hacer esto para cada sitio? Puede hacerlo sin tener que escribir todos los sitios web con este comando:</span><span class="sxs-lookup"><span data-stu-id="44dd7-p121">However, what if you wanted to do this for every site? You can do this without having to type all those websites by using this command:</span></span>

```
Get-SPOSite | ForEach-Object {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="44dd7-p122">Este informe es bastante sencilla, y puede agregar más código para crear informes de más específica o informes que incluyen información más detallada. Pero esto debería darle una idea de cómo usar el Shell de administración de SharePoint Online para administrar usuarios en el entorno de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="44dd7-p122">This report is fairly simple, and you can add more code to create more specific reports or reports that include more detailed information. But this should give you an idea of how to use the SharePoint Online Management Shell to manage users in the SharePoint Online environment.</span></span>
   
## <a name="see-also"></a><span data-ttu-id="44dd7-183">Consulte también</span><span class="sxs-lookup"><span data-stu-id="44dd7-183">See also</span></span>

[<span data-ttu-id="44dd7-184">Conectarse a SharePoint Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="44dd7-184">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="44dd7-185">Administrar SharePoint Online con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="44dd7-185">Manage SharePoint Online with Office 365 PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

[<span data-ttu-id="44dd7-186">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="44dd7-186">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="44dd7-187">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="44dd7-187">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

