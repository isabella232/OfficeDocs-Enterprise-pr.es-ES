---
title: Asignar licencias a cuentas de usuario con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/29/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
description: Se explica cómo usar PowerShell de Office 365 para asignar una licencia de Office 365 a los usuarios sin licencia.
ms.openlocfilehash: 4c91c9f2441d0e537f2fa23fd1f021fe0bfe03b6
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123297"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="fd2dc-103">Asignar licencias a cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="fd2dc-103">Assign licenses to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="fd2dc-104">**Resumen:** se explica cómo usar PowerShell de Office 365 para asignar una licencia de Office 365 a los usuarios sin licencia.</span><span class="sxs-lookup"><span data-stu-id="fd2dc-104">**Summary:**  Explains how to use Office 365 PowerShell assign an Office 365 license to unlicensed users.</span></span>
  
<span data-ttu-id="fd2dc-p101">Es importante asignar licencias a las cuentas de usuario de Office 365, ya que los usuarios no pueden usar ningún servicio de Office 365 hasta que su cuenta tenga una licencia. Puede usar PowerShell de Office 365 para asignar de forma eficiente licencias a cuentas sin licencia, especialmente a varias cuentas.</span><span class="sxs-lookup"><span data-stu-id="fd2dc-p101">Licensing user accounts in Office 365 is important, because users can't use any Office 365 services until their account has been licensed. You can use Office 365 PowerShell to efficiently assign licenses to unlicensed accounts, especially multiple accounts.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="fd2dc-107">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="fd2dc-107">Before you begin</span></span>
<span data-ttu-id="fd2dc-108"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="fd2dc-108"><a name="RTT"> </a></span></span>

- <span data-ttu-id="fd2dc-p102">Los procedimientos de este tema requieren conectarse a PowerShell de Office 365. Para obtener instrucciones, vea [Conectarse a PowerShell de Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="fd2dc-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="fd2dc-p103">Use el cmdlet **Get-MsolAccountSku** para ver los planes de licencias disponibles y el número de licencias disponibles en cada plan de la organización. El número de licencias disponibles en cada plan es **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. Para obtener más información sobre los planes de licencias, las licencias y los servicios, vea[Ver licencias y servicios con PowerShell de Office 365](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="fd2dc-p103">Use the **Get-MsolAccountSku** cmdlet to view the available licensing plans and the number of available licenses in each plan in your organization. The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. For more information about licensing plans, licenses, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="fd2dc-114">Para buscar las cuentas sin licencia de la organización, ejecute el comando  `Get-MsolUser -All -UnlicensedUsersOnly`</span><span class="sxs-lookup"><span data-stu-id="fd2dc-114">To find the unlicensed accounts in your organization, run the command  `Get-MsolUser -All -UnlicensedUsersOnly`</span></span>
    
- <span data-ttu-id="fd2dc-p104">Solo puede asignar licencias a cuentas de usuario que tengan la propiedad **UsageLocation** establecida en un código de país ISO 3166-1 alpha-2 válido (por ejemplo, “US” para Estados Unidos y “FR” para Francia). Algunos servicios de Office 365 no están disponibles en determinados países. Para obtener más información, vea [Información sobre restricciones de licencia](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span><span class="sxs-lookup"><span data-stu-id="fd2dc-p104">You can assign licenses only to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. Some Office 365 services aren't available in certain countries. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
    <span data-ttu-id="fd2dc-p105">Para buscar cuentas que no tengan un valor **UsageLocation**, ejecute el comando `Get-MsolUser -All | where {$_.UsageLocation -eq $null}`. Para establecer el valor **UsageLocation** en una cuenta, utilice la sintaxis `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`. Por ejemplo,  `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`.</span><span class="sxs-lookup"><span data-stu-id="fd2dc-p105">To find accounts that don't have a **UsageLocation** value, run the command `Get-MsolUser -All | where {$_.UsageLocation -eq $null}`. To set the **UsageLocation** value on an account, use the syntax `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`. For example,  `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`.</span></span>
    
- <span data-ttu-id="fd2dc-122">Si usa el cmdlet **Get-MsolUser** sin el parámetro `-All`, solo se devuelven las 500 primeras cuentas.</span><span class="sxs-lookup"><span data-stu-id="fd2dc-122">If you use the **Get-MsolUser** cmdlet without using the `-All` parameter, only the first 500 accounts are returned.</span></span>

## <a name="assigning-licenses-to-user-accounts"></a><span data-ttu-id="fd2dc-123">Asignación de licencias para las cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="fd2dc-123">Assigning licenses to user accounts</span></span>
    
<span data-ttu-id="fd2dc-124">Para asignar una licencia a un usuario, use la sintaxis siguiente en PowerShell de Office 365:</span><span class="sxs-lookup"><span data-stu-id="fd2dc-124">To assign a license to a user, use the following syntax in Office 365 PowerShell:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="fd2dc-125">En este ejemplo, se asigna una licencia desde el plan de licencias `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) al usuario sin licencia `belindan@litwareinc.com`.</span><span class="sxs-lookup"><span data-stu-id="fd2dc-125">This example assigns a license from the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan to the unlicensed user `belindan@litwareinc.com`.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="fd2dc-126">Para asignar una licencia a varios usuarios sin licencia, use la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="fd2dc-126">To assign a license to many unlicensed users, use the following syntax:</span></span>
  
```
$x = Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>]; $x | foreach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```

 <span data-ttu-id="fd2dc-127">**Notas**</span><span class="sxs-lookup"><span data-stu-id="fd2dc-127">**Notes**</span></span>
  
- <span data-ttu-id="fd2dc-128">No se pueden asignar varias licencias a un usuario desde el mismo plan de licencias.</span><span class="sxs-lookup"><span data-stu-id="fd2dc-128">You can't assign multiple licenses to a user from the same licensing plan.</span></span>
    
- <span data-ttu-id="fd2dc-129">Si no dispone de licencias suficientes, las licencias se asignan a los usuarios en el orden en que los devuelve el cmdlet **Get-MsolUser** hasta que se agoten las licencias disponibles.</span><span class="sxs-lookup"><span data-stu-id="fd2dc-129">If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
    
<span data-ttu-id="fd2dc-130">En este ejemplo, se asignan licencias desde el plan de licencias `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) a todos los usuarios sin licencia.</span><span class="sxs-lookup"><span data-stu-id="fd2dc-130">This example assigns licenses from the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan to all unlicensed users.</span></span>
  
```
$AllUn = Get-MsolUser -All -UnlicensedUsersOnly; $AllUn | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

<span data-ttu-id="fd2dc-131">En este ejemplo se asignan esas mismas licencias a los usuarios sin licencia del departamento de ventas de los Estados Unidos.</span><span class="sxs-lookup"><span data-stu-id="fd2dc-131">This example assigns those same licenses to unlicensed users in the Sales department in the United States.</span></span>
  
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly; $USSales | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```
  
## <a name="new-to-office-365"></a><span data-ttu-id="fd2dc-132">¿Es la primera vez que usa Office 365?</span><span class="sxs-lookup"><span data-stu-id="fd2dc-132">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="fd2dc-133">Consulte también</span><span class="sxs-lookup"><span data-stu-id="fd2dc-133">See also</span></span>
<span data-ttu-id="fd2dc-134"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="fd2dc-134"></span></span>

<span data-ttu-id="fd2dc-135">Vea los siguientes temas adicionales acerca de cómo administrar usuarios con Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="fd2dc-135">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="fd2dc-136">Crear cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="fd2dc-136">Create user accounts</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="fd2dc-137">Eliminación y restauración de las cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="fd2dc-137">Delete and restore user accounts</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="fd2dc-138">Cuentas de usuario de bloque</span><span class="sxs-lookup"><span data-stu-id="fd2dc-138">Block user accounts</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="fd2dc-139">Quitar las licencias de las cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="fd2dc-139">Remove licenses from user accounts</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="fd2dc-140">Para obtener más información sobre los cmdlets que se usan en estos procedimientos, consulte los siguientes temas:</span><span class="sxs-lookup"><span data-stu-id="fd2dc-140">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="fd2dc-141">Get-MsolAccountSku</span><span class="sxs-lookup"><span data-stu-id="fd2dc-141">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [<span data-ttu-id="fd2dc-142">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="fd2dc-142">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="fd2dc-143">Set-MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="fd2dc-143">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="fd2dc-144">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="fd2dc-144">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="fd2dc-145">Select-Object</span><span class="sxs-lookup"><span data-stu-id="fd2dc-145">Select-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [<span data-ttu-id="fd2dc-146">Where-Object</span><span class="sxs-lookup"><span data-stu-id="fd2dc-146">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

