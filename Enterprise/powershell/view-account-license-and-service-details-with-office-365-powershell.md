---
title: Ver los detalles del servicio y la licencia de la cuenta con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/13/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: Explica cómo usar Office 365 PowerShell para determinar los servicios de Office 365 que se han asignado a los usuarios.
ms.openlocfilehash: 608d26dfc4aa1be782f94aa3b1ba5f66a0378f1e
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071126"
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a><span data-ttu-id="96e6b-103">Ver los detalles del servicio y la licencia de la cuenta con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="96e6b-103">View account license and service details with Office 365 PowerShell</span></span>

<span data-ttu-id="96e6b-104">**Resumen:** Explica cómo usar Office 365 PowerShell para determinar los servicios de Office 365 que se han asignado a los usuarios.</span><span class="sxs-lookup"><span data-stu-id="96e6b-104">**Summary:** Explains how to use Office 365 PowerShell to determine the Office 365 services that have been assigned to users.</span></span>
  
<span data-ttu-id="96e6b-105">En Office 365, las licencias de los planes de licencias (también denominados SKU o los planes de Office 365) proporcionan a los usuarios acceso a los servicios de Office 365 definidos para esos planes.</span><span class="sxs-lookup"><span data-stu-id="96e6b-105">In Office 365, licenses from licensing plans (also called SKUs or Office 365 plans) give users access to the Office 365 services that are defined for those plans.</span></span> <span data-ttu-id="96e6b-106">Sin embargo, un usuario podría no tener acceso a todos los servicios disponibles en una licencia que está actualmente asignada a ellos.</span><span class="sxs-lookup"><span data-stu-id="96e6b-106">However, a user might not have access to all the services that are available in a license that's currently assigned to them.</span></span> <span data-ttu-id="96e6b-107">Puede usar Office 365 PowerShell para ver el estado de los servicios de las cuentas de usuario.</span><span class="sxs-lookup"><span data-stu-id="96e6b-107">You can use Office 365 PowerShell to view the status of services on user accounts.</span></span> 

<span data-ttu-id="96e6b-108">Para obtener más información acerca de los planes de licencias, la licencia y los servicios, consulte [ver licencias y servicios con Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="96e6b-108">For more information about licensing plans, license, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="96e6b-109">Use el módulo de PowerShell Azure Active Directory para Graph</span><span class="sxs-lookup"><span data-stu-id="96e6b-109">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="96e6b-110">Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="96e6b-110">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="96e6b-111">A continuación, enumere los planes de licencia para el inquilino con este comando.</span><span class="sxs-lookup"><span data-stu-id="96e6b-111">Next, list the license plans for your tenant with this command.</span></span>

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="96e6b-112">Use estos comandos para enumerar los servicios que están disponibles en cada plan de licencias.</span><span class="sxs-lookup"><span data-stu-id="96e6b-112">Use these commands to list the services that are available in each licensing plan.</span></span>

```
$allSKUs=Get-AzureADSubscribedSku
$licArray = @()
for($i = 0; $i -lt $allSKUs.Count; $i++)
{
$licArray += "Service Plan: " + $allSKUs[$i].SkuPartNumber
$licArray +=  Get-AzureADSubscribedSku -ObjectID $allSKUs[$i].ObjectID | Select -ExpandProperty ServicePlans
$licArray +=  ""
}
$licArray
````

<span data-ttu-id="96e6b-113">Use estos comandos para enumerar las licencias que se asignan a una cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="96e6b-113">Use these commands to list the licenses that are assigned to a user account.</span></span>

````
$userUPN="<user account UPN, such as belindan@contoso.com>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
````

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="96e6b-114">Use el Módulo Microsoft Azure Active Directory para Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="96e6b-114">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="96e6b-115">Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="96e6b-115">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="96e6b-116">A continuación, ejecute este comando para enumerar los planes de licencias disponibles en su organización.</span><span class="sxs-lookup"><span data-stu-id="96e6b-116">Next, run this command to list the licensing plans that are available in your organization.</span></span> 

```
Get-MsolAccountSku
```

<span data-ttu-id="96e6b-117">A continuación, ejecute este comando para enumerar los servicios que están disponibles en cada plan de licencias y el orden en que aparecen (el número de índice).</span><span class="sxs-lookup"><span data-stu-id="96e6b-117">Next, run this command to list the services that are available in each licensing plan, and the order in which they are listed (the index number).</span></span>

````
(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus
````
  
<span data-ttu-id="96e6b-118">Use este comando para enumerar las licencias que se asignan a un usuario y el orden en que aparecen (el número de índice).</span><span class="sxs-lookup"><span data-stu-id="96e6b-118">Use this command to list the licenses that are assigned to a user, and the order in which they are listed (the index number).</span></span>

````
Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses
````

>[!Note]
><span data-ttu-id="96e6b-119">Si usa el cmdlet **Get-MsolUser** sin usar el parámetro _All_, solo se devuelven las 500 primeras cuentas.</span><span class="sxs-lookup"><span data-stu-id="96e6b-119">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 accounts are returned.</span></span>
>
   

### <a name="to-view-services-for-a-user-account"></a><span data-ttu-id="96e6b-120">Para ver los servicios de una cuenta de usuario</span><span class="sxs-lookup"><span data-stu-id="96e6b-120">To view services for a user account</span></span>

<span data-ttu-id="96e6b-121">Para ver todos los servicios de Office 365 a los que tiene acceso un usuario, use la siguiente sintaxis:</span><span class="sxs-lookup"><span data-stu-id="96e6b-121">To view all the Office 365 services that a user has access to, use the following syntax:</span></span>
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

<span data-ttu-id="96e6b-122">En este ejemplo se muestran los servicios a los que el usuario BelindaN@litwareinc.com tiene acceso.</span><span class="sxs-lookup"><span data-stu-id="96e6b-122">This example shows the services to which the user BelindaN@litwareinc.com has access.</span></span> <span data-ttu-id="96e6b-123">Se muestran los servicios que están asociados a todas las licencias asignadas a su cuenta.</span><span class="sxs-lookup"><span data-stu-id="96e6b-123">This shows the services that are associated with all licenses that are assigned to her account.</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

<span data-ttu-id="96e6b-124">En este ejemplo se muestran los servicios a los que tiene acceso la usuaria BelindaN@litwareinc.com a partir de la primera licencia asignada a su cuenta (el número de índice es 0).</span><span class="sxs-lookup"><span data-stu-id="96e6b-124">This example shows the services that user BelindaN@litwareinc.com has access to from the first license that's assigned to her account (the index number is 0).</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

<span data-ttu-id="96e6b-125">Para ver todos los servicios de un usuario que tiene asignadas *varias licencias*, use la siguiente sintaxis:</span><span class="sxs-lookup"><span data-stu-id="96e6b-125">To view all the services for a user who has been assigned *multiple licenses*, use the following syntax:</span></span>

```
$userAccountUPN="<user account UPN>"
$AllLicenses=(Get-MsolUser -UserPrincipalName $userAccountUPN).Licenses
$licArray = @()
for($i = 0; $i -lt $AllLicenses.Count; $i++)
{
$licArray += "License: " + $AllLicenses[$i].AccountSkuId
$licArray +=  $AllLicenses[$i].ServiceStatus
$licArray +=  ""
}
$licArray
```

  
## <a name="new-to-office-365"></a><span data-ttu-id="96e6b-126">¿Es la primera vez que usa Office 365?</span><span class="sxs-lookup"><span data-stu-id="96e6b-126">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="96e6b-127">Consulte también</span><span class="sxs-lookup"><span data-stu-id="96e6b-127">See also</span></span>

[<span data-ttu-id="96e6b-128">Administrar licencias y cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="96e6b-128">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="96e6b-129">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="96e6b-129">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="96e6b-130">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="96e6b-130">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
