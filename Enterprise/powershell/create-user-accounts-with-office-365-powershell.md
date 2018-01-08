---
title: Crear cuentas de usuario con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- apr17entnews
- Ent_Office_Other
- DecEntMigration
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Aprenda a usar PowerShell de Office 365 para crear cuentas de usuario en Office 365.
ms.openlocfilehash: 9f6eb4cafa82ae511e806b7e32f2ed98a065d52e
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2017
---
# <a name="create-user-accounts-with-office-365-powershell"></a><span data-ttu-id="3f2b5-103">Crear cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="3f2b5-103">Create user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="3f2b5-104">**Resumen:** obtenga información sobre cómo usar PowerShell de Office 365 para crear cuentas de usuario en Office 365.</span><span class="sxs-lookup"><span data-stu-id="3f2b5-104">Learn how to use Office 365 PowerShell to create user accounts in Office 365.</span></span>
  
<span data-ttu-id="3f2b5-p101">Puede usar PowerShell de Office 365 para crear de forma eficaz cuentas de usuario, especialmente varias cuentas de usuario. Al crear cuentas de usuario en PowerShell de Office 365, siempre se requieren determinadas propiedades de la cuenta. Otras propiedades no son necesarias para crear la cuenta, pero aun así son importantes. Estas propiedades se describen en la tabla siguiente:</span><span class="sxs-lookup"><span data-stu-id="3f2b5-p101">You can use Office 365 PowerShell to efficiently create user accounts, especially multiple user accounts. When you create user accounts in Office 365 PowerShell, certain account properties are always required. Other properties aren't required to create the account, but are otherwise important. These properties are described in the following table:</span></span>
  
****

|<span data-ttu-id="3f2b5-109">**Nombre de propiedad**</span><span class="sxs-lookup"><span data-stu-id="3f2b5-109">**Property name**</span></span>|<span data-ttu-id="3f2b5-110">**Obligatorio**</span><span class="sxs-lookup"><span data-stu-id="3f2b5-110">**Required?**</span></span>|<span data-ttu-id="3f2b5-111">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="3f2b5-111">**Description**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="3f2b5-112">**DisplayName**</span><span class="sxs-lookup"><span data-stu-id="3f2b5-112">**DisplayName**</span></span> <br/> |<span data-ttu-id="3f2b5-113">Sí</span><span class="sxs-lookup"><span data-stu-id="3f2b5-113">Yes</span></span>  <br/> |<span data-ttu-id="3f2b5-p102">Este es el nombre para mostrar que se usa en servicios de Office 365. Por ejemplo, Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="3f2b5-p102">This is the display name that's used in Office 365 services. For example, Caleb Sills.</span></span>  <br/> |
|<span data-ttu-id="3f2b5-116">**UserPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="3f2b5-116">**UserPrincipalName**</span></span> <br/> |<span data-ttu-id="3f2b5-117">Sí</span><span class="sxs-lookup"><span data-stu-id="3f2b5-117">Yes</span></span>  <br/> |<span data-ttu-id="3f2b5-p103">Este es el nombre de cuenta que se usa para iniciar sesión en servicios de Office 365. Por ejemplo, CalebS@contoso.onmicrosoft.com.</span><span class="sxs-lookup"><span data-stu-id="3f2b5-p103">This is the account name that's used to sign in to Office 365 services. For example, CalebS@contoso.onmicrosoft.com.</span></span>  <br/> |
|<span data-ttu-id="3f2b5-120">**FirstName**</span><span class="sxs-lookup"><span data-stu-id="3f2b5-120">**FirstName**</span></span> <br/> |<span data-ttu-id="3f2b5-121">No</span><span class="sxs-lookup"><span data-stu-id="3f2b5-121">No</span></span>  <br/> ||
|<span data-ttu-id="3f2b5-122">**Apellidos**</span><span class="sxs-lookup"><span data-stu-id="3f2b5-122">**LastName**</span></span> <br/> |<span data-ttu-id="3f2b5-123">No</span><span class="sxs-lookup"><span data-stu-id="3f2b5-123">No</span></span>  <br/> ||
|<span data-ttu-id="3f2b5-124">**LicenseAssignment**</span><span class="sxs-lookup"><span data-stu-id="3f2b5-124">**LicenseAssignment**</span></span> <br/> |<span data-ttu-id="3f2b5-125">No</span><span class="sxs-lookup"><span data-stu-id="3f2b5-125">No</span></span>  <br/> |<span data-ttu-id="3f2b5-p104">Este es el plan de licencias (también conocido como plan de Office 365 o SKU) desde el que se asigna una licencia disponible a la cuenta de usuario. La licencia define los servicios de Office 365 que están disponibles para la cuenta. No tiene que asignar una licencia a un usuario al crear la cuenta, pero la cuenta requiere una licencia para tener acceso a los servicios de Office 365. Dispone de 30 días para conceder una licencia a la cuenta de usuario después de crearla.</span><span class="sxs-lookup"><span data-stu-id="3f2b5-p104">This is the licensing plan (also known as the license plan, Office 365 plan, or SKU) from which an available license is assigned to the user account. The license defines the Office 365 services that are available to account. You don't have to assign a license to a user when you create the account, but the account requires a license to access Office 365 services. You have 30 days to license the user account after you create it.  </span></span><br/> <span data-ttu-id="3f2b5-p105">Use el cmdlet **Get-MsolAccountSku** para ver los planes de licencias (**AccountSkuId**) y las licencias disponibles en la organización. Para obtener más información, vea [Ver licencias y servicios con PowerShell de Office 365](view-licenses-and-services-with-office-365-powershell.md).  </span><span class="sxs-lookup"><span data-stu-id="3f2b5-p105">Use the **Get-MsolAccountSku** cmdlet to view the licensing plans ( **AccountSkuId** ) and available licenses in your organization. For more information, see[View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span><br/> |
|<span data-ttu-id="3f2b5-132">**Password**</span><span class="sxs-lookup"><span data-stu-id="3f2b5-132">**Password**</span></span> <br/> |<span data-ttu-id="3f2b5-133">No</span><span class="sxs-lookup"><span data-stu-id="3f2b5-133">No</span></span>  <br/> | <span data-ttu-id="3f2b5-p106">Si no especifica una contraseña, se asignará una contraseña aleatoria a la cuenta de usuario y la contraseña será visible en los resultados del comando. Si especifica una contraseña, debe cumplir los siguientes requisitos de complejidad:</span><span class="sxs-lookup"><span data-stu-id="3f2b5-p106">If you don't specify a password, a random password is assigned to the user account, and the password is visible in the results of the command. If you specify a password, it needs to meet the following complexity requirements:</span></span> <br/>  <span data-ttu-id="3f2b5-136">De 8 a 16 caracteres de texto ASCII.</span><span class="sxs-lookup"><span data-stu-id="3f2b5-136">8 to 16 ASCII text characters.</span></span> <br/>  <span data-ttu-id="3f2b5-137">Caracteres de tres de los tipos siguientes: letras minúsculas, letras mayúsculas, números y símbolos.</span><span class="sxs-lookup"><span data-stu-id="3f2b5-137">Characters from any three of the following types: lowercase letters, uppercase letters, numbers, and symbols.</span></span> <br/> |
|<span data-ttu-id="3f2b5-138">**UsageLocation**</span><span class="sxs-lookup"><span data-stu-id="3f2b5-138">**UsageLocation**</span></span> <br/> |<span data-ttu-id="3f2b5-139">No</span><span class="sxs-lookup"><span data-stu-id="3f2b5-139">No</span></span>  <br/> |<span data-ttu-id="3f2b5-p107">Se trata de un código de país válido ISO 3166-1 alpha-2. Por ejemplo, US para Estados Unidos y FR para Francia. Es importante proporcionar este valor, ya que algunos servicios de Office 365 no están disponibles en determinados países, por lo que no se puede asignar una licencia a una cuenta de usuario a menos que la cuenta tenga este valor configurado. Para obtener más información, consulte [Sobre las restricciones de licencia](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span><span class="sxs-lookup"><span data-stu-id="3f2b5-p107">This is a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. It's important to provide this value, because some Office 365 services aren't available in certain countries, so you can't assign a license to a user account unless the account has this value configured. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).  </span></span><br/> |
   
## <a name="before-you-begin"></a><span data-ttu-id="3f2b5-144">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="3f2b5-144">Before you begin</span></span>

<span data-ttu-id="3f2b5-p108">Los procedimientos de este tema requieren conectarse a PowerShell de Office 365. Para obtener instrucciones, vea [Conectarse a PowerShell de Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="3f2b5-p108">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="use-office-365-powershell-to-create-individual-user-accounts"></a><span data-ttu-id="3f2b5-147">Usar PowerShell de Office 365 para crear cuentas de usuario individuales</span><span class="sxs-lookup"><span data-stu-id="3f2b5-147">Use Office 365 PowerShell to create individual user accounts</span></span>

<span data-ttu-id="3f2b5-148">Para crear una cuenta individual, use la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="3f2b5-148">To create an individual account, use the following syntax:</span></span>
  
```
New-MsolUser -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -UserPrincipalName <Account> -UsageLocation <CountryCode> -LicenseAssignment <AccountSkuID> [-Password <Password>]
```

<span data-ttu-id="3f2b5-149">En este ejemplo se crea una cuenta para el usuario de Estados Unidos llamado Caleb Sills y se asigna una licencia desde el plan de licencias  `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="3f2b5-149">This example creates an account for the United States user named Caleb Sills, and assigns a license from the  `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan.</span></span>
  
```
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

## <a name="use-office-365-powershell-to-create-multiple-user-accounts"></a><span data-ttu-id="3f2b5-150">Usar PowerShell de Office 365 para crear varias cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="3f2b5-150">Use Office 365 PowerShell to create multiple user accounts</span></span>

1. <span data-ttu-id="3f2b5-p109">Cree un archivo de valores separados por comas (CSV) que contenga la información necesaria de la cuenta de usuario. Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="3f2b5-p109">Create a comma-separated value (CSV) file that contains the required user account information. For example:</span></span>
    
  ```
  UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
  ```

 > [!NOTE]
><span data-ttu-id="3f2b5-153">Los nombres de columna y su orden en la primera fila del archivo CSV son arbitrarios, pero asegúrese de que los datos del resto del archivo coincidan con el orden de los nombres de columna y use los nombres de columna para los valores de parámetro en el comando de PowerShell de Office 365.</span><span class="sxs-lookup"><span data-stu-id="3f2b5-153">Note: The column names and their order in the first row of the CSV file are arbitrary, but make sure the data in the rest of the file matches the order of the column names, and use the column names for the parameter values in the Office 365 PowerShell command.</span></span>
    
2. <span data-ttu-id="3f2b5-154">Utilice la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="3f2b5-154">Use the following syntax:</span></span>
    
  ```
  Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
  ```

<span data-ttu-id="3f2b5-155">En este ejemplo se crean las cuentas de usuario a partir del archivo denominado C:\My Documents\NewAccounts.csv y se registran los resultados en el archivo denominado C:\My Documents\NewAccountResults.csv.</span><span class="sxs-lookup"><span data-stu-id="3f2b5-155">This example creates the user accounts from the file named C:\My Documents\NewAccounts.csv, and logs the results in the file named C:\My Documents\NewAccountResults.csv</span></span>
    
  ```
  Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
  ```

3. <span data-ttu-id="3f2b5-p110">Revise el archivo de salida para ver los resultados. No se han especificado las contraseñas, por lo que las contraseñas aleatorias que se generaron son visibles en el archivo de salida.</span><span class="sxs-lookup"><span data-stu-id="3f2b5-p110">Review the output file to see the results. We didn't specify passwords, so the random passwords that were generated are visible in the output file.</span></span>
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-create-individual-user-accounts"></a><span data-ttu-id="3f2b5-158">Usar el módulo de PowerShell Azure Active Directory V2 para crear cuentas de usuario individuales</span><span class="sxs-lookup"><span data-stu-id="3f2b5-158">Use the Azure Active Directory V2 PowerShell module to create individual user accounts</span></span>

<span data-ttu-id="3f2b5-p111">Para usar el cmdlet **New-AzureADUser** desde el módulo de PowerShell Azure Active Directory V2, primero tiene que conectarse a la suscripción. Para obtener instrucciones, vea [Conectarse con el módulo de PowerShell Azure Active Directory V2](https://go.microsoft.com/fwlink/?linkid=842218).</span><span class="sxs-lookup"><span data-stu-id="3f2b5-p111">To use the **New-AzureADUser** cmdlet from the Azure Active Directory V2 PowerShell module, you must first connect to your subscription. For the instructions, see[Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="3f2b5-161">Después de haberse conectado, use la sintaxis siguiente para crear una cuenta individual:</span><span class="sxs-lookup"><span data-stu-id="3f2b5-161">After you have connected, use the following syntax to create an individual account:</span></span>
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName <DisplayName> -GivenName <FirstName> -SurName <LastName> -UserPrincipalName <Account> -UsageLocation <CountryCode> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

<span data-ttu-id="3f2b5-162">En este ejemplo se crea una cuenta para el usuario de Estados Unidos llamado Caleb Sills:</span><span class="sxs-lookup"><span data-stu-id="3f2b5-162">This example creates an account for the United States user named Caleb Sills:</span></span>
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```
  
## <a name="see-also"></a><span data-ttu-id="3f2b5-163">Consulte también</span><span class="sxs-lookup"><span data-stu-id="3f2b5-163">See also</span></span>

<span data-ttu-id="3f2b5-164">Vea estos temas adicionales sobre cómo administrar usuarios con PowerShell de Office 365:</span><span class="sxs-lookup"><span data-stu-id="3f2b5-164">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="3f2b5-165">Eliminar y restaurar cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="3f2b5-165">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="3f2b5-166">Bloquear cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="3f2b5-166">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="3f2b5-167">Asignar licencias a cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="3f2b5-167">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="3f2b5-168">Eliminar licencias de cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="3f2b5-168">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="3f2b5-169">Para obtener más información sobre los cmdlets que se usan en estos procedimientos, consulte los siguientes temas:</span><span class="sxs-lookup"><span data-stu-id="3f2b5-169">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="3f2b5-170">Export-Csv</span><span class="sxs-lookup"><span data-stu-id="3f2b5-170">Export-Csv</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113299)
    
- <span data-ttu-id="3f2b5-171">[Import-Csv]((https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-csv))</span><span class="sxs-lookup"><span data-stu-id="3f2b5-171">[Import-Csv]((https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-csv))</span></span>
    
- [<span data-ttu-id="3f2b5-172">New-MsolUser</span><span class="sxs-lookup"><span data-stu-id="3f2b5-172">New-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="3f2b5-173">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="3f2b5-173">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="3f2b5-174">New-AzureADUser</span><span class="sxs-lookup"><span data-stu-id="3f2b5-174">New-AzureADUser</span></span>](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

