---
title: Eliminar licencias de cuentas de usuario con PowerShell de Office 365
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
- PowerShell
- Ent_Office_Other
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: Se explica cómo usar PowerShell de Office 365 para quitar licencias de Office 365 que anteriormente se han asignado a los usuarios.
ms.openlocfilehash: a993737f4bd1186a7fb5beb7fa0f6a2ae6782618
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123307"
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a><span data-ttu-id="90278-103">Eliminar licencias de cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="90278-103">Remove licenses from user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="90278-104">**Resumen:** Se explica cómo usar PowerShell de Office 365 para quitar licencias de Office 365 que anteriormente se han asignado a los usuarios.</span><span class="sxs-lookup"><span data-stu-id="90278-104">**Summary:** Explains how to use Office 365 PowerShell to remove Office 365 licenses that were previously assigned to users.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="90278-105">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="90278-105">Before you begin</span></span>

- <span data-ttu-id="90278-p101">Los procedimientos de este tema requieren conectarse a PowerShell de Office 365. Para obtener instrucciones, vea [Conectarse a PowerShell de Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="90278-p101">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="90278-108">Para ver la información del plan (**AccountSkuID** ) de licencias de la organización, consulte los temas siguientes:</span><span class="sxs-lookup"><span data-stu-id="90278-108">To view the licensing plan (**AccountSkuID** ) information in your organization, see the following topics:</span></span>
    
  - [<span data-ttu-id="90278-109">Ver las licencias y los servicios con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="90278-109">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="90278-110">Ver los detalles del servicio y la licencia de la cuenta con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="90278-110">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
- <span data-ttu-id="90278-111">Si usa el cmdlet **Get-MsolUser** sin usar el parámetro _All_, solo se devuelven las 500 primeras cuentas.</span><span class="sxs-lookup"><span data-stu-id="90278-111">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="removing-licenses-from-user-accounts"></a><span data-ttu-id="90278-112">Eliminación de licencias de las cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="90278-112">Removing licenses from user accounts</span></span>

<span data-ttu-id="90278-113">Para quitar licencias de una cuenta de usuario existente, utilice la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="90278-113">To remove licenses from an existing user account, use the following syntax:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

<span data-ttu-id="90278-114">En este ejemplo se quita el `litwareinc:ENTERPRISEPACK` licencia (Office 365 Enterprise E3) de la cuenta de usuario BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="90278-114">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user account BelindaN@litwareinc.com.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="90278-115">Para quitar licencias de un grupo de usuarios con licencia existentes, utilice uno de los métodos siguientes:</span><span class="sxs-lookup"><span data-stu-id="90278-115">To remove licenses from a group of existing licensed users, use either of the following methods:</span></span>
  
- <span data-ttu-id="90278-116">**Filtrar las cuentas basadas en un atributo de cuenta existente** Para ello, use la siguiente sintaxis:</span><span class="sxs-lookup"><span data-stu-id="90278-116">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
```
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="90278-117">En este ejemplo se quita el `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licencias de todas las cuentas para los usuarios del departamento de ventas en los Estados Unidos.</span><span class="sxs-lookup"><span data-stu-id="90278-117">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licenses from all accounts for users in the Sales department in the United States.</span></span>
    
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- <span data-ttu-id="90278-118">**Usar una lista de cuentas específicas** Para ello, realice los pasos siguientes:</span><span class="sxs-lookup"><span data-stu-id="90278-118">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="90278-119">Cree y guarde un archivo de texto que contenga una cuenta en cada línea de esta manera:</span><span class="sxs-lookup"><span data-stu-id="90278-119">Create and save a text file that contains one account on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. <span data-ttu-id="90278-120">Utilice la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="90278-120">Use the following syntax:</span></span>
    
  ```
  Get-Content "<FileNameAndPath>" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
  ```

<span data-ttu-id="90278-121">En este ejemplo se quita el `litwareinc:ENTERPRISEPACK` licencia (Office 365 Enterprise E3) de las cuentas de usuario definidos en el archivo de texto C:\My Documents\Accounts.txt.</span><span class="sxs-lookup"><span data-stu-id="90278-121">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user accounts defined in the text file C:\My Documents\Accounts.txt.</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  ```

<span data-ttu-id="90278-122">Para quitar las licencias de todas las cuentas de usuario, utilice la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="90278-122">To remove licenses from all existing user accounts, use the following syntax:</span></span>
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="90278-123">En este ejemplo se quita el `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licencia de todas las existentes con licencia de cuentas de usuario.</span><span class="sxs-lookup"><span data-stu-id="90278-123">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from all existing licensed user accounts.</span></span>
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

<span data-ttu-id="90278-p102">Otra forma de liberar una licencia es mediante la eliminación de la cuenta de usuario. Para obtener más información, vea [eliminar y restaurar las cuentas de usuario con PowerShell de Office 365](delete-and-restore-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="90278-p102">Another way to free up a license is by deleting the user account. For more information, see [Delete and restore user accounts with Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="90278-126">Consulte también</span><span class="sxs-lookup"><span data-stu-id="90278-126">See also</span></span>

<span data-ttu-id="90278-127">Vea los siguientes temas adicionales acerca de cómo administrar usuarios con Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="90278-127">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="90278-128">Crear cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="90278-128">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="90278-129">Eliminar y restaurar cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="90278-129">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="90278-130">Bloquear cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="90278-130">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="90278-131">Asignar licencias a cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="90278-131">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="90278-132">Para obtener más información sobre los cmdlets que se usan en estos procedimientos, consulte los siguientes temas:</span><span class="sxs-lookup"><span data-stu-id="90278-132">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="90278-133">Get-Content</span><span class="sxs-lookup"><span data-stu-id="90278-133">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [<span data-ttu-id="90278-134">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="90278-134">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="90278-135">Set-MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="90278-135">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="90278-136">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="90278-136">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="90278-137">Where-Object</span><span class="sxs-lookup"><span data-stu-id="90278-137">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
## <a name="new-to-office-365"></a><span data-ttu-id="90278-138">¿Es la primera vez que usa Office 365?</span><span class="sxs-lookup"><span data-stu-id="90278-138">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   

