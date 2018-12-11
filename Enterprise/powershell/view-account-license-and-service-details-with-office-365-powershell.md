---
title: Ver los detalles del servicio y la licencia de la cuenta con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/10/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: Se explica cómo usar PowerShell de Office 365 para determinar los servicios de Office 365 que se han asignado a los usuarios.
ms.openlocfilehash: 5d575ea9e0b45ddc453b3b1c73bd53bf73adab2e
ms.sourcegitcommit: 16806849f373196797d65e63ced825d547aef956
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2018
ms.locfileid: "27213957"
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a><span data-ttu-id="09051-103">Ver los detalles del servicio y la licencia de la cuenta con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="09051-103">View account license and service details with Office 365 PowerShell</span></span>

<span data-ttu-id="09051-104">**Resumen:** Se explica cómo usar PowerShell de Office 365 para determinar los servicios de Office 365 que se han asignado a los usuarios.</span><span class="sxs-lookup"><span data-stu-id="09051-104">**Summary:** Explains how to use Office 365 PowerShell to determine the Office 365 services that have been assigned to users.</span></span>
  
<span data-ttu-id="09051-p101">En Office 365, licencias de planes de licencias (también llamadas SKU o Office 365 planes) ofrecer a los usuarios acceso a los servicios de Office 365 que se definen para esos planes. Sin embargo, un usuario no puede tener acceso a todos los servicios que están disponibles en una licencia que está asignada actualmente a ellos. Puede usar PowerShell de Office 365 para ver el estado de los servicios en las cuentas de usuario.</span><span class="sxs-lookup"><span data-stu-id="09051-p101">In Office 365, licenses from licensing plans (also called SKUs or Office 365 plans) give users access to the Office 365 services that are defined for those plans. However, a user might not have access to all the services that are available in a license that's currently assigned to them. You can use Office 365 PowerShell to view the status of services on user accounts.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="09051-108">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="09051-108">Before you begin</span></span>

- <span data-ttu-id="09051-p102">Los procedimientos de este tema requieren conectarse a PowerShell de Office 365. Para obtener instrucciones, vea [Conectarse a PowerShell de Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="09051-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="09051-111">Use los comandos de `Get-MsolAccountSku` y `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` para buscar la siguiente información:</span><span class="sxs-lookup"><span data-stu-id="09051-111">Use the commands  `Get-MsolAccountSku` and `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` to find the following information:</span></span>
    
  - <span data-ttu-id="09051-112">Los planes de licencias que están disponibles en su organización.</span><span class="sxs-lookup"><span data-stu-id="09051-112">The licensing plans that are available in your organization.</span></span>
    
  - <span data-ttu-id="09051-113">Los servicios que están disponibles en cada plan de licencias y el orden en que muestran (el número de índice).</span><span class="sxs-lookup"><span data-stu-id="09051-113">The services that are available in each licensing plan, and the order in which they are listed (the index number).</span></span>
    
     <span data-ttu-id="09051-114">Para obtener más información acerca de las licencias de los planes, la licencia y servicios, vea [ver licencias y servicios con PowerShell de Office 365](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="09051-114">For more information about licensing plans, license, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="09051-115">Use el comando `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` para buscar las licencias que se asignan a un usuario y el orden en que están enumerados (el número de índice).</span><span class="sxs-lookup"><span data-stu-id="09051-115">Use the command  `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` to find the licenses that are assigned to a user, and the order in which they are listed (the index number).</span></span>
    
- <span data-ttu-id="09051-116">Si usa el cmdlet **Get-MsolUser** sin usar el parámetro _All_, solo se devuelven las 500 primeras cuentas.</span><span class="sxs-lookup"><span data-stu-id="09051-116">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 accounts are returned.</span></span>
    

## <a name="to-view-services-for-a-user-account"></a><span data-ttu-id="09051-117">Para ver los servicios para una cuenta de usuario</span><span class="sxs-lookup"><span data-stu-id="09051-117">To view services for a user account</span></span>

<span data-ttu-id="09051-118">Para ver todos los servicios de Office 365 que un usuario tiene acceso a, use la siguiente sintaxis:</span><span class="sxs-lookup"><span data-stu-id="09051-118">To view all the Office 365 services that a user has access to, use the following syntax:</span></span>
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

<span data-ttu-id="09051-p103">En este ejemplo se muestran los servicios a la que el usuario BelindaN@litwareinc.com tiene acceso. Esto muestra los servicios que están asociados con todas las licencias que se asignan a su cuenta.</span><span class="sxs-lookup"><span data-stu-id="09051-p103">This example shows the services to which the user BelindaN@litwareinc.com has access. This shows the services that are associated with all licenses that are assigned to her account.</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

<span data-ttu-id="09051-121">En este ejemplo se muestran los servicios a los que tiene acceso la usuaria BelindaN@litwareinc.com a partir de la primera licencia asignada a su cuenta (el número de índice es 0).</span><span class="sxs-lookup"><span data-stu-id="09051-121">This example shows the services that user BelindaN@litwareinc.com has access to from the first license that's assigned to her account (the index number is 0).</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

<span data-ttu-id="09051-122">Para ver todos los servicios para un usuario que se ha asignado *varias licencias*, use la siguiente sintaxis:</span><span class="sxs-lookup"><span data-stu-id="09051-122">To view all the services for a user who has been assigned *multiple licenses*, use the following syntax:</span></span>

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

  
## <a name="see-also"></a><span data-ttu-id="09051-123">Consulte también</span><span class="sxs-lookup"><span data-stu-id="09051-123">See also</span></span>

<span data-ttu-id="09051-124">Vea los siguientes temas adicionales acerca de cómo administrar usuarios con Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="09051-124">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="09051-125">Crear cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="09051-125">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="09051-126">Eliminar y restaurar cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="09051-126">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="09051-127">Bloquear cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="09051-127">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="09051-128">Asignar licencias a cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="09051-128">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="09051-129">Eliminar licencias de cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="09051-129">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="09051-130">Para obtener más información sobre los cmdlets que se usan en estos procedimientos, consulte los siguientes temas:</span><span class="sxs-lookup"><span data-stu-id="09051-130">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="09051-131">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="09051-131">ConvertTo-Html</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113290)
    
- [<span data-ttu-id="09051-132">Format-List</span><span class="sxs-lookup"><span data-stu-id="09051-132">Format-List</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113302)
    
- [<span data-ttu-id="09051-133">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="09051-133">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="09051-134">Select-Object</span><span class="sxs-lookup"><span data-stu-id="09051-134">Select-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [<span data-ttu-id="09051-135">Where-Object</span><span class="sxs-lookup"><span data-stu-id="09051-135">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

  
## <a name="new-to-office-365"></a><span data-ttu-id="09051-136">¿Es la primera vez que usa Office 365?</span><span class="sxs-lookup"><span data-stu-id="09051-136">New to Office 365?</span></span>


[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]