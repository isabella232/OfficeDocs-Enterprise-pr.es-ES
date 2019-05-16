---
title: Crear cuentas de usuario con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Aprenda a usar PowerShell de Office 365 para crear cuentas de usuario en Office 365.
ms.openlocfilehash: 846dafb842b87f119670f44848152a99341939e7
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069066"
---
# <a name="create-user-accounts-with-office-365-powershell"></a><span data-ttu-id="6c305-103">Crear cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="6c305-103">Create user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="6c305-104">**Resumen:** obtenga información sobre cómo usar PowerShell de Office 365 para crear cuentas de usuario en Office 365.</span><span class="sxs-lookup"><span data-stu-id="6c305-104">**Summary:** Learn how to use Office 365 PowerShell to create user accounts in Office 365.</span></span>
  
<span data-ttu-id="6c305-p101">Puede usar PowerShell de Office 365 para crear de forma eficaz cuentas de usuario, especialmente varias cuentas de usuario. Al crear cuentas de usuario en PowerShell de Office 365, siempre se requieren determinadas propiedades de la cuenta. Otras propiedades no son necesarias para crear la cuenta, pero aun así son importantes. Estas propiedades se describen en la tabla siguiente:</span><span class="sxs-lookup"><span data-stu-id="6c305-p101">You can use Office 365 PowerShell to efficiently create user accounts, especially multiple user accounts. When you create user accounts in Office 365 PowerShell, certain account properties are always required. Other properties aren't required to create the account, but are otherwise important. These properties are described in the following table:</span></span>
  
|<span data-ttu-id="6c305-109">**Nombre de propiedad**</span><span class="sxs-lookup"><span data-stu-id="6c305-109">**Property name**</span></span>|<span data-ttu-id="6c305-110">**Obligatorio**</span><span class="sxs-lookup"><span data-stu-id="6c305-110">**Required?**</span></span>|<span data-ttu-id="6c305-111">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="6c305-111">**Description**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="6c305-112">**DisplayName**</span><span class="sxs-lookup"><span data-stu-id="6c305-112">**DisplayName**</span></span> <br/> |<span data-ttu-id="6c305-113">Sí</span><span class="sxs-lookup"><span data-stu-id="6c305-113">Yes</span></span>  <br/> |<span data-ttu-id="6c305-p102">Este es el nombre para mostrar que se usa en servicios de Office 365. Por ejemplo, Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="6c305-p102">This is the display name that's used in Office 365 services. For example, Caleb Sills.</span></span>  <br/> |
|<span data-ttu-id="6c305-116">**UserPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="6c305-116">**UserPrincipalName**</span></span> <br/> |<span data-ttu-id="6c305-117">Sí</span><span class="sxs-lookup"><span data-stu-id="6c305-117">Yes</span></span>  <br/> |<span data-ttu-id="6c305-p103">Este es el nombre de cuenta que se usa para iniciar sesión en servicios de Office 365. Por ejemplo, CalebS@contoso.onmicrosoft.com.</span><span class="sxs-lookup"><span data-stu-id="6c305-p103">This is the account name that's used to sign in to Office 365 services. For example, CalebS@contoso.onmicrosoft.com.</span></span>  <br/> |
|<span data-ttu-id="6c305-120">**FirstName**</span><span class="sxs-lookup"><span data-stu-id="6c305-120">**FirstName**</span></span> <br/> |<span data-ttu-id="6c305-121">No</span><span class="sxs-lookup"><span data-stu-id="6c305-121">No</span></span>  <br/> ||
|<span data-ttu-id="6c305-122">**Apellidos**</span><span class="sxs-lookup"><span data-stu-id="6c305-122">**LastName**</span></span> <br/> |<span data-ttu-id="6c305-123">No</span><span class="sxs-lookup"><span data-stu-id="6c305-123">No</span></span>  <br/> ||
|<span data-ttu-id="6c305-124">**LicenseAssignment**</span><span class="sxs-lookup"><span data-stu-id="6c305-124">**LicenseAssignment**</span></span> <br/> |<span data-ttu-id="6c305-125">No</span><span class="sxs-lookup"><span data-stu-id="6c305-125">No</span></span>  <br/> |<span data-ttu-id="6c305-p104">Este es el plan de licencias (también conocido como plan de Office 365 o SKU) desde el que se asigna una licencia disponible a la cuenta de usuario. La licencia define los servicios de Office 365 que están disponibles para la cuenta. No tiene que asignar una licencia a un usuario al crear la cuenta, pero la cuenta requiere una licencia para tener acceso a los servicios de Office 365. Dispone de 30 días para conceder una licencia a la cuenta de usuario después de crearla.</span><span class="sxs-lookup"><span data-stu-id="6c305-p104">This is the licensing plan (also known as the license plan, Office 365 plan, or SKU) from which an available license is assigned to the user account. The license defines the Office 365 services that are available to account. You don't have to assign a license to a user when you create the account, but the account requires a license to access Office 365 services. You have 30 days to license the user account after you create it.</span></span> |
|<span data-ttu-id="6c305-130">**Password**</span><span class="sxs-lookup"><span data-stu-id="6c305-130">**Password**</span></span> <br/> |<span data-ttu-id="6c305-131">No</span><span class="sxs-lookup"><span data-stu-id="6c305-131">No</span></span>  <br/> | <span data-ttu-id="6c305-p105">Si no especifica una contraseña, se asignará una aleatoria a la cuenta de usuario y esta será visible en los resultados del comando. Si especifica una contraseña, debe tener entre 8 y 16 caracteres ASCII de cualquiera de los siguientes tipos: letras minúsculas, letras mayúsculas, números y símbolos.</span><span class="sxs-lookup"><span data-stu-id="6c305-p105">If you don't specify a password, a random password is assigned to the user account, and the password is visible in the results of the command. If you specify a password, it needs to be 8 to 16 ASCII text characters from any three of the following types: lowercase letters, uppercase letters, numbers, and symbols.</span></span> <br/> |
|<span data-ttu-id="6c305-134">**UsageLocation**</span><span class="sxs-lookup"><span data-stu-id="6c305-134">**UsageLocation**</span></span> <br/> |<span data-ttu-id="6c305-135">No</span><span class="sxs-lookup"><span data-stu-id="6c305-135">No</span></span>  <br/> |<span data-ttu-id="6c305-p106">Se trata de un código de país válido ISO 3166-1 alpha-2. Por ejemplo, US para Estados Unidos y FR para Francia. Es importante proporcionar este valor, ya que algunos servicios de Office 365 no están disponibles en determinados países, por lo que no se puede asignar una licencia a una cuenta de usuario a menos que la cuenta tenga este valor configurado. Para obtener más información, consulte [Sobre las restricciones de licencia](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span><span class="sxs-lookup"><span data-stu-id="6c305-p106">This is a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. It's important to provide this value, because some Office 365 services aren't available in certain countries, so you can't assign a license to a user account unless the account has this value configured. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).  </span></span><br/> |
   

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="6c305-140">Use el módulo de PowerShell Azure Active Directory para Graph</span><span class="sxs-lookup"><span data-stu-id="6c305-140">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="6c305-141">Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="6c305-141">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

<span data-ttu-id="6c305-142">Después de haberse conectado, use la sintaxis siguiente para crear una cuenta individual:</span><span class="sxs-lookup"><span data-stu-id="6c305-142">After you have connected, use the following syntax to create an individual account:</span></span>
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName "<display name>" -GivenName "<first name>" -SurName "<last name>" -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

<span data-ttu-id="6c305-143">En este ejemplo se crea una cuenta para el usuario de Estados Unidos llamado Caleb Sills:</span><span class="sxs-lookup"><span data-stu-id="6c305-143">This example creates an account for the United States user named Caleb Sills:</span></span>
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="6c305-144">Use el Módulo Microsoft Azure Active Directory para Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6c305-144">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="6c305-145">Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="6c305-145">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

### <a name="create-an-individual-user-account"></a><span data-ttu-id="6c305-146">Cree una cuenta de usuario individual</span><span class="sxs-lookup"><span data-stu-id="6c305-146">Create an individual user account</span></span>

<span data-ttu-id="6c305-147">Para crear una cuenta individual, use la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="6c305-147">To create an individual account, use the following syntax:</span></span>
  
```
New-MsolUser -DisplayName <display name> -FirstName <first name> -LastName <last name> -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -LicenseAssignment <licensing plan name> [-Password <Password>]
```

<span data-ttu-id="6c305-148">Para obtener una lista de los nombres de planes de licencias disponibles, use este comando:</span><span class="sxs-lookup"><span data-stu-id="6c305-148">To list the available licensing plan names, use this command:</span></span>

````
Get-MsolAccountSku
````

<span data-ttu-id="6c305-149">En este ejemplo se crea una cuenta para el usuario de Estados Unidos llamado Caleb Sills y se asigna una licencia desde el plan de licencias `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="6c305-149">This example creates an account for the United States user named Caleb Sills, and assigns a license from the `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan.</span></span>
  
```
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

### <a name="create-multiple-user-accounts"></a><span data-ttu-id="6c305-150">Crear varias cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="6c305-150">Create multiple user accounts</span></span>

1. <span data-ttu-id="6c305-p107">Cree un archivo de valores separados por comas (CSV) que contenga la información necesaria de la cuenta de usuario. Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="6c305-p107">Create a comma-separated value (CSV) file that contains the required user account information. For example:</span></span>
    
  ```
  UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
  ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
  LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
  ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
  ```

 > [!NOTE]
><span data-ttu-id="6c305-153">Los nombres de columna y su orden en la primera fila del archivo CSV son arbitrarios, pero asegúrese de que los datos del resto del archivo coincidan con el orden de los nombres de columna y use los nombres de columna para los valores de parámetro en el comando de PowerShell de Office 365.</span><span class="sxs-lookup"><span data-stu-id="6c305-153">The column names and their order in the first row of the CSV file are arbitrary, but make sure the data in the rest of the file matches the order of the column names, and use the column names for the parameter values in the Office 365 PowerShell command.</span></span>
    
2. <span data-ttu-id="6c305-154">Utilice la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="6c305-154">Use the following syntax:</span></span>
    
  ```
  Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
  ```

<span data-ttu-id="6c305-155">En este ejemplo se crean las cuentas de usuario a partir del archivo denominado C:\My Documents\NewAccounts.csv y se registran los resultados en el archivo denominado C:\My Documents\NewAccountResults.csv.</span><span class="sxs-lookup"><span data-stu-id="6c305-155">This example creates the user accounts from the file named C:\My Documents\NewAccounts.csv, and logs the results in the file named C:\My Documents\NewAccountResults.csv</span></span>
    
  ```
  Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
  ```

3. <span data-ttu-id="6c305-p108">Revise el archivo de salida para ver los resultados. No se han especificado las contraseñas, por lo que las contraseñas aleatorias generadas por Office 365 son visibles en el archivo de salida.</span><span class="sxs-lookup"><span data-stu-id="6c305-p108">Review the output file to see the results. We didn't specify passwords, so the random passwords that Office 365 generated are visible in the output file.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="6c305-158">Vea también</span><span class="sxs-lookup"><span data-stu-id="6c305-158">See also</span></span>

[<span data-ttu-id="6c305-159">Administrar licencias y cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="6c305-159">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="6c305-160">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="6c305-160">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="6c305-161">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="6c305-161">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
