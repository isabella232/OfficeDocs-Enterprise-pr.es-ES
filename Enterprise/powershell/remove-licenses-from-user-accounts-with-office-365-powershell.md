---
title: Eliminar licencias de cuentas de usuario con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: PowerShell, Ent_Office_Other, LIL_Placement, O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: "Explica cómo utilizar Office 365 PowerShell para quitar licencias de Office 365 que se asignaron previamente a los usuarios."
ms.openlocfilehash: 115a708d8def679d43d88e9c83b68ca13dd72fdc
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/13/2018
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a><span data-ttu-id="9a8d4-103">Eliminar licencias de cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="9a8d4-103">Remove licenses from user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="9a8d4-104">**Resumen:** Explica cómo utilizar Office 365 PowerShell para quitar licencias de Office 365 que se asignaron previamente a los usuarios.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-104">**Summary:** Explains how to use Office 365 PowerShell to remove Office 365 licenses that were previously assigned to users.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="9a8d4-105">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="9a8d4-105">Before you begin</span></span>

- <span data-ttu-id="9a8d4-p101">Los procedimientos de este tema requieren conectarse a PowerShell de Office 365. Para obtener instrucciones, vea [Conectarse a PowerShell de Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="9a8d4-p101">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="9a8d4-108">Para ver la información de licencia ( **AccountSkuID** ) del plan de la organización, consulte los temas siguientes:</span><span class="sxs-lookup"><span data-stu-id="9a8d4-108">To view the licensing plan ( **AccountSkuID** ) information in your organization, see the following topics:</span></span>
    
  - [<span data-ttu-id="9a8d4-109">Ver las licencias y los servicios con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="9a8d4-109">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="9a8d4-110">Ver los detalles del servicio y la licencia de la cuenta con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="9a8d4-110">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
- <span data-ttu-id="9a8d4-111">Si usa el cmdlet **Get-MsolUser** sin usar el parámetro _All_, solo se devuelven las 500 primeras cuentas.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-111">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="9a8d4-112">Versión corta (instrucciones sin explicaciones)</span><span class="sxs-lookup"><span data-stu-id="9a8d4-112">The short version (instructions without explanations)</span></span>
<span data-ttu-id="9a8d4-113"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="9a8d4-113"></span></span>

<span data-ttu-id="9a8d4-p102">En esta sección se presentan los procedimientos sin explicaciones superfluas. Si tiene preguntas o desea obtener más información, puede leer el resto del tema.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-p102">This section presents the procedures without fanfare or superfluous explanation. If you have questions or want more information, you can read rest of the topic.</span></span>
  
<span data-ttu-id="9a8d4-116">Para quitar licencias de una cuenta de usuario existente, utilice la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="9a8d4-116">To remove licenses from an existing user account, use the following syntax:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

<span data-ttu-id="9a8d4-117">Este ejemplo quita la `litwareinc:ENTERPRISEPACK` una licencia (Office 365 Enterprise E3) de la cuenta de usuario BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-117">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user account BelindaN@litwareinc.com.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="9a8d4-118">Para quitar licencias de un grupo de usuarios con licencia existentes, utilice uno de los métodos siguientes:</span><span class="sxs-lookup"><span data-stu-id="9a8d4-118">To remove licenses from a group of existing licensed users, use either of the following methods:</span></span>
  
- <span data-ttu-id="9a8d4-119">**Filtrar las cuentas basadas en un atributo de cuenta existente** Para ello, utilice la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="9a8d4-119">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
```
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="9a8d4-120">Este ejemplo quita el `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licencias de todas las cuentas de los usuarios del departamento de ventas en los Estados Unidos.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-120">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licenses from all accounts for users in the Sales department in the United States.</span></span>
    
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- <span data-ttu-id="9a8d4-121">**Usar una lista de cuentas específicas** Para ello, siga estos pasos:</span><span class="sxs-lookup"><span data-stu-id="9a8d4-121">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="9a8d4-122">Cree y guarde un archivo de texto que contenga una cuenta en cada línea de esta manera:</span><span class="sxs-lookup"><span data-stu-id="9a8d4-122">Create and save a text file that contains one account on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. <span data-ttu-id="9a8d4-123">Utilice la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="9a8d4-123">Use the following syntax:</span></span>
    
  ```
  Get-Content "<FileNameAndPath>" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
  ```

<span data-ttu-id="9a8d4-124">Este ejemplo quita el `litwareinc:ENTERPRISEPACK` licencia (Office 365 Enterprise E3) de las cuentas de usuario definido en el archivo de texto C:\My Documents\Accounts.txt.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-124">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user accounts defined in the text file C:\My Documents\Accounts.txt.</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  ```

<span data-ttu-id="9a8d4-125">Para quitar las licencias de todas las cuentas de usuario, utilice la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="9a8d4-125">To remove licenses from all existing user accounts, use the following syntax:</span></span>
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="9a8d4-126">Este ejemplo quita el `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) una licencia de todo lo existente licencia de cuentas de usuario.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-126">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from all existing licensed user accounts.</span></span>
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="9a8d4-127">Versión larga (instrucciones con explicaciones detalladas)</span><span class="sxs-lookup"><span data-stu-id="9a8d4-127">The long version (instructions with detailed explanations)</span></span>
<span data-ttu-id="9a8d4-128"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="9a8d4-128"></span></span>

<span data-ttu-id="9a8d4-p103">Nada es para siempre, y esto incluye licencias de Office 365: tarde o temprano, llegará un momento cuando necesite quitar una licencia de una cuenta de usuario. Tal vez el usuario se va de baja; tal vez el usuario ya no necesita la licencia; Bueno, quizás - hay obviamente varios motivos de por qué desea quitar una licencia de usuario.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-p103">Nothing lasts forever, and that includes Office 365 licenses: sooner or later, there will come a time when you need to remove a license from a user account. Maybe the user is going on leave; maybe the user no longer needs the license; maybe - well, there are obviously any number of reasons why you might want to remove a user license.</span></span>
  
<span data-ttu-id="9a8d4-p104">Antes de cualquier otra es importante destacar que al eliminar una licencia requiere que, así, eliminar la licencia: deshabilitar todos los servicios en una licencia no es lo mismo que al eliminar una licencia. Por ejemplo, supongamos que hemos utilizado nuestras licencias de Office 365; en otras palabras, no hay disponible ningún tipo de licencias. Decide seguir el procedimiento en [Deshabilitar el acceso a los servicios de Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md) para deshabilitar todos los servicios, digamos, en cuenta de Belinda Newman. ¿Una vez que hacemos que, cuántas licencias tendremos disponible para nosotros? Correcto: cero. Sí, el procedimiento de este tema va a *Deshabilitar* todos los servicios de licencia de Belinda, pero no deshabilitará (es decir, eliminar) la licencia de sí mismo. La licencia seguirán siendo válida y aún se asignará a Belinda Newman. Ella sólo podrá utilizar esa licencia para acceder a los servicios de Office 365.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-p104">Before we go any further it's important to note that removing a license requires you to, well, remove the license: disabling all the services on a license is not the same thing as removing a license. For example, suppose we've used up all our Office 365 licenses; in other words, we have no licenses available whatsoever. You decide to follow the procedure in [Disable access to services with Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md) to disable all the services, say, on Belinda Newman's account. After we do that, how many licenses will we have available to us? That's right: zero. Yes, the procedure from that topic will *disable*  all the services on Belinda's license, but it will not disable (i.e., delete) the license itself. The license will still be valid, and it will still be assigned to Belinda Newman. She just won't be able to use that license to access any Office 365 services.</span></span>
  
<span data-ttu-id="9a8d4-p105">Y que es importante: si desea eliminar una licencia de un usuario primero debe *Quitar* la licencia. Deshabilitar todos los servicios se impide al usuario iniciar sesión en Office 365, pero no libere su licencia. Si desea volver a tomar una licencia que está actualmente asignada a un usuario que necesite ejecutar un comando similar a este, un comando que utiliza el parámetro _RemoveLicenses_ para quitar la licencia asignada previamente a Belinda:</span><span class="sxs-lookup"><span data-stu-id="9a8d4-p105">And that's important: if you want to remove a license from a user you must actually  *remove*  the license. Disabling all the services will prevent the user from logging on to Office 365, but it won't free up his or her license. If you want to take back a license that's currently assigned to a user you need to run a command similar to this one, a command that uses the _RemoveLicenses_ parameter to actually remove the license previously assigned to Belinda:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="9a8d4-142">Ejecutar ese comando y Belinda Newman ya no se tiene licencia para utilizar Office 365.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-142">Run that command, and Belinda Newman will no longer be licensed to use Office 365.</span></span>
  
> [!NOTE]
> <span data-ttu-id="9a8d4-p106">Como puede ver, cuando se utiliza el parámetro _RemoveLicenses_ que debe especificar el nombre de la licencia que se va a quitar. Si no está seguro de qué plan de licencias utilizado para asignar una licencia para el usuario sólo tiene que ejecutar un comando como éste:`Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Format-List DisplayName,Licenses`</span><span class="sxs-lookup"><span data-stu-id="9a8d4-p106">As you can see, when you use the  _RemoveLicenses_ parameter you need to specify the name of the license to be removed. If you aren't sure which licensing plan was used to assign a license to the user just run a command like this:  `Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Format-List DisplayName,Licenses`</span></span>
  
<span data-ttu-id="9a8d4-145">Para comprobar que realmente se ha quitado la licencia, use Get-MsolUser para comprobar la cuenta del usuario en cuestión:</span><span class="sxs-lookup"><span data-stu-id="9a8d4-145">To verify that the license really was removed, use the Get-MsolUser to check the user account in question:</span></span>
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

<span data-ttu-id="9a8d4-146">Si todo ha ido según el plan, ahora se establecerá la propiedad de **isLicensed** de Belinda `False`:</span><span class="sxs-lookup"><span data-stu-id="9a8d4-146">If everything went according to plan, Belinda's **isLicensed** property will now be set to `False`:</span></span>
  
```
UserPrincipalName            DisplayName         isLicensed
-----------------            -----------         ----------
BelindaN@litwareinc.com      Newman, Belinda     False
```

<span data-ttu-id="9a8d4-p107">Otra forma de liberar una licencia es mediante la eliminación de la cuenta de usuario. Para obtener más información, vea [eliminar y restaurar cuentas de usuario con Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="9a8d4-p107">Another way to free up a license is by deleting the user account. For more information, see [Delete and restore user accounts with Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="9a8d4-149">Consulte también</span><span class="sxs-lookup"><span data-stu-id="9a8d4-149">See also</span></span>

<span data-ttu-id="9a8d4-150">Vea los siguientes temas adicionales acerca de cómo administrar usuarios con Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="9a8d4-150">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="9a8d4-151">Crear cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="9a8d4-151">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="9a8d4-152">Eliminar y restaurar cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="9a8d4-152">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="9a8d4-153">Bloquear cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="9a8d4-153">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="9a8d4-154">Asignar licencias a cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="9a8d4-154">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="9a8d4-155">Para obtener más información sobre los cmdlets que se usan en estos procedimientos, consulte los siguientes temas:</span><span class="sxs-lookup"><span data-stu-id="9a8d4-155">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="9a8d4-156">Get-Content</span><span class="sxs-lookup"><span data-stu-id="9a8d4-156">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [<span data-ttu-id="9a8d4-157">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="9a8d4-157">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="9a8d4-158">Set-MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="9a8d4-158">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="9a8d4-159">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="9a8d4-159">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="9a8d4-160">Where-Object</span><span class="sxs-lookup"><span data-stu-id="9a8d4-160">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
## <a name="new-to-office-365"></a><span data-ttu-id="9a8d4-161">¿Es la primera vez que usa Office 365?</span><span class="sxs-lookup"><span data-stu-id="9a8d4-161">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   

