---
title: Crear cuentas de usuario 365 de Microsoft con PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- O365ITProTrain
- seo-marvel-apr2020
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: En este artículo, aprenderá a usar PowerShell para crear cuentas de usuario o varias cuentas de usuario de Microsoft 365.
ms.openlocfilehash: 2f4d7b42e68e3bd426ea73c8568e0c603af06dcb
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605996"
---
# <a name="create-microsoft-365-user-accounts-with-powershell"></a><span data-ttu-id="23681-103">Crear cuentas de usuario 365 de Microsoft con PowerShell</span><span class="sxs-lookup"><span data-stu-id="23681-103">Create Microsoft 365 user accounts with PowerShell</span></span>

<span data-ttu-id="23681-104">*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="23681-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="23681-105">Puede usar PowerShell para Microsoft 365 para crear de forma eficaz cuentas de usuario, especialmente varias cuentas de usuario.</span><span class="sxs-lookup"><span data-stu-id="23681-105">You can use PowerShell for Microsoft 365 to efficiently create user accounts, especially multiple user accounts.</span></span> <span data-ttu-id="23681-106">Al crear cuentas de usuario en PowerShell, siempre son necesarias determinadas propiedades de la cuenta.</span><span class="sxs-lookup"><span data-stu-id="23681-106">When you create user accounts in PowerShell, certain account properties are always required.</span></span> <span data-ttu-id="23681-107">Otras propiedades no son necesarias para crear la cuenta, pero aun así son importantes.</span><span class="sxs-lookup"><span data-stu-id="23681-107">Other properties aren't required to create the account, but are otherwise important.</span></span> <span data-ttu-id="23681-108">Estas propiedades se describen en la tabla siguiente:</span><span class="sxs-lookup"><span data-stu-id="23681-108">These properties are described in the following table:</span></span>
  
|<span data-ttu-id="23681-109">**Nombre de propiedad**</span><span class="sxs-lookup"><span data-stu-id="23681-109">**Property name**</span></span>|<span data-ttu-id="23681-110">**Obligatorio**</span><span class="sxs-lookup"><span data-stu-id="23681-110">**Required?**</span></span>|<span data-ttu-id="23681-111">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="23681-111">**Description**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="23681-112">**DisplayName**</span><span class="sxs-lookup"><span data-stu-id="23681-112">**DisplayName**</span></span> <br/> |<span data-ttu-id="23681-113">Sí</span><span class="sxs-lookup"><span data-stu-id="23681-113">Yes</span></span>  <br/> |<span data-ttu-id="23681-114">Este es el nombre para mostrar que se usa en los servicios de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="23681-114">This is the display name that's used in Microsoft 365 services.</span></span> <span data-ttu-id="23681-115">Por ejemplo, Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="23681-115">For example, Caleb Sills.</span></span>  <br/> |
|<span data-ttu-id="23681-116">**UserPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="23681-116">**UserPrincipalName**</span></span> <br/> |<span data-ttu-id="23681-117">Sí</span><span class="sxs-lookup"><span data-stu-id="23681-117">Yes</span></span>  <br/> |<span data-ttu-id="23681-118">Este es el nombre de cuenta que se usa para iniciar sesión en los servicios de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="23681-118">This is the account name that's used to sign in to Microsoft 365 services.</span></span> <span data-ttu-id="23681-119">Por ejemplo, CalebS@contoso.onmicrosoft.com.</span><span class="sxs-lookup"><span data-stu-id="23681-119">For example, CalebS@contoso.onmicrosoft.com.</span></span>  <br/> |
|<span data-ttu-id="23681-120">**FirstName**</span><span class="sxs-lookup"><span data-stu-id="23681-120">**FirstName**</span></span> <br/> |<span data-ttu-id="23681-121">No</span><span class="sxs-lookup"><span data-stu-id="23681-121">No</span></span>  <br/> ||
|<span data-ttu-id="23681-122">**Apellidos**</span><span class="sxs-lookup"><span data-stu-id="23681-122">**LastName**</span></span> <br/> |<span data-ttu-id="23681-123">No</span><span class="sxs-lookup"><span data-stu-id="23681-123">No</span></span>  <br/> ||
|<span data-ttu-id="23681-124">**LicenseAssignment**</span><span class="sxs-lookup"><span data-stu-id="23681-124">**LicenseAssignment**</span></span> <br/> |<span data-ttu-id="23681-125">No</span><span class="sxs-lookup"><span data-stu-id="23681-125">No</span></span>  <br/> |<span data-ttu-id="23681-126">Se trata del plan de licencias (también conocido como el plan de licencia o SKU) desde el que se asigna una licencia disponible a la cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="23681-126">This is the licensing plan (also known as the license plan or SKU) from which an available license is assigned to the user account.</span></span> <span data-ttu-id="23681-127">La licencia define los servicios de Microsoft 365 que están disponibles para la cuenta.</span><span class="sxs-lookup"><span data-stu-id="23681-127">The license defines the Microsoft 365 services that are available to account.</span></span> <span data-ttu-id="23681-128">No es necesario asignar una licencia a un usuario cuando se crea la cuenta, pero la cuenta requiere una licencia para obtener acceso a los servicios de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="23681-128">You don't have to assign a license to a user when you create the account, but the account requires a license to access Microsoft 365 services.</span></span> <span data-ttu-id="23681-129">Dispone de 30 días para conceder una licencia a la cuenta de usuario después de crearla.</span><span class="sxs-lookup"><span data-stu-id="23681-129">You have 30 days to license the user account after you create it.</span></span> |
|<span data-ttu-id="23681-130">**Password**</span><span class="sxs-lookup"><span data-stu-id="23681-130">**Password**</span></span> <br/> |<span data-ttu-id="23681-131">No</span><span class="sxs-lookup"><span data-stu-id="23681-131">No</span></span>  <br/> | <span data-ttu-id="23681-p105">Si no especifica una contraseña, se asignará una aleatoria a la cuenta de usuario y esta será visible en los resultados del comando. Si especifica una contraseña, debe tener entre 8 y 16 caracteres ASCII de cualquiera de los siguientes tipos: letras minúsculas, letras mayúsculas, números y símbolos.</span><span class="sxs-lookup"><span data-stu-id="23681-p105">If you don't specify a password, a random password is assigned to the user account, and the password is visible in the results of the command. If you specify a password, it needs to be 8 to 16 ASCII text characters from any three of the following types: lowercase letters, uppercase letters, numbers, and symbols.</span></span> <br/> |
|<span data-ttu-id="23681-134">**UsageLocation**</span><span class="sxs-lookup"><span data-stu-id="23681-134">**UsageLocation**</span></span> <br/> |<span data-ttu-id="23681-135">No</span><span class="sxs-lookup"><span data-stu-id="23681-135">No</span></span>  <br/> |<span data-ttu-id="23681-136">Se trata de un código de país válido ISO 3166-1 alpha-2.</span><span class="sxs-lookup"><span data-stu-id="23681-136">This is a valid ISO 3166-1 alpha-2 country code.</span></span> <span data-ttu-id="23681-137">Por ejemplo, US para Estados Unidos y FR para Francia.</span><span class="sxs-lookup"><span data-stu-id="23681-137">For example, US for the United States, and FR for France.</span></span> <span data-ttu-id="23681-138">Es importante proporcionar este valor, ya que algunos servicios de Microsoft 365 no están disponibles en determinados países, por lo que no puede asignar una licencia a una cuenta de usuario a menos que la cuenta tenga este valor configurado.</span><span class="sxs-lookup"><span data-stu-id="23681-138">It's important to provide this value, because some Microsoft 365 services aren't available in certain countries, so you can't assign a license to a user account unless the account has this value configured.</span></span> <span data-ttu-id="23681-139">Para obtener más información, consulte [Sobre las restricciones de licencia](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span><span class="sxs-lookup"><span data-stu-id="23681-139">For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>  <br/> |
   

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="23681-140">Use el módulo de PowerShell Azure Active Directory para Graph</span><span class="sxs-lookup"><span data-stu-id="23681-140">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="23681-141">En primer lugar, [Conéctese a su inquilino de Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="23681-141">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

<span data-ttu-id="23681-142">Después de haberse conectado, use la sintaxis siguiente para crear una cuenta individual:</span><span class="sxs-lookup"><span data-stu-id="23681-142">After you have connected, use the following syntax to create an individual account:</span></span>
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName "<display name>" -GivenName "<first name>" -SurName "<last name>" -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

<span data-ttu-id="23681-143">En este ejemplo se crea una cuenta para el usuario de Estados Unidos llamado Caleb Sills:</span><span class="sxs-lookup"><span data-stu-id="23681-143">This example creates an account for the United States user named Caleb Sills:</span></span>
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="23681-144">Use el Módulo Microsoft Azure Active Directory para Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="23681-144">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="23681-145">En primer lugar, [Conéctese a su inquilino de Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="23681-145">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

### <a name="create-an-individual-user-account"></a><span data-ttu-id="23681-146">Cree una cuenta de usuario individual</span><span class="sxs-lookup"><span data-stu-id="23681-146">Create an individual user account</span></span>

<span data-ttu-id="23681-147">Para crear una cuenta individual, use la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="23681-147">To create an individual account, use the following syntax:</span></span>
  
```powershell
New-MsolUser -DisplayName <display name> -FirstName <first name> -LastName <last name> -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -LicenseAssignment <licensing plan name> [-Password <Password>]
```

>[!Note]
><span data-ttu-id="23681-148">PowerShell Core no es compatible con el Módulo Microsoft Azure Active Directory para Windows PowerShell ni los cmdlet que llevan **Msol** en su nombre.</span><span class="sxs-lookup"><span data-stu-id="23681-148">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="23681-149">Para seguir usando estos cmdlets, debe ejecutarlos desde Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="23681-149">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="23681-150">Para obtener una lista de los nombres de planes de licencias disponibles, use este comando:</span><span class="sxs-lookup"><span data-stu-id="23681-150">To list the available licensing plan names, use this command:</span></span>

````powershell
Get-MsolAccountSku
````

<span data-ttu-id="23681-151">En este ejemplo se crea una cuenta para el usuario de Estados Unidos llamado Caleb Sills y se asigna una licencia desde el plan de licencias `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="23681-151">This example creates an account for the United States user named Caleb Sills, and assigns a license from the `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan.</span></span>
  
```powershell
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

### <a name="create-multiple-user-accounts"></a><span data-ttu-id="23681-152">Crear varias cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="23681-152">Create multiple user accounts</span></span>

1. <span data-ttu-id="23681-p108">Cree un archivo de valores separados por comas (CSV) que contenga la información necesaria de la cuenta de usuario. Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="23681-p108">Create a comma-separated value (CSV) file that contains the required user account information. For example:</span></span>
    
  ```powershell
  UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
  ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
  LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
  ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
  ```

 > [!NOTE]
><span data-ttu-id="23681-155">Los nombres de columna y su orden en la primera fila del archivo CSV son arbitrarios, pero asegúrese de que los datos del resto del archivo coinciden con el orden de los nombres de columna y use los nombres de columna para los valores de parámetro en el comando PowerShell para Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="23681-155">The column names and their order in the first row of the CSV file are arbitrary, but make sure the data in the rest of the file matches the order of the column names, and use the column names for the parameter values in the PowerShell for Microsoft 365 command.</span></span>
    
2. <span data-ttu-id="23681-156">Utilice la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="23681-156">Use the following syntax:</span></span>
    
  ```powershell
  Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
  ```

<span data-ttu-id="23681-157">En este ejemplo se crean las cuentas de usuario a partir del archivo denominado C:\My Documents\NewAccounts.csv y se registran los resultados en el archivo denominado C:\My Documents\NewAccountResults.csv.</span><span class="sxs-lookup"><span data-stu-id="23681-157">This example creates the user accounts from the file named C:\My Documents\NewAccounts.csv, and logs the results in the file named C:\My Documents\NewAccountResults.csv</span></span>
    
  ```powershell
  Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
  ```

3. <span data-ttu-id="23681-158">Revise el archivo de salida para ver los resultados.</span><span class="sxs-lookup"><span data-stu-id="23681-158">Review the output file to see the results.</span></span> <span data-ttu-id="23681-159">No se especificaron contraseñas, por lo que las contraseñas aleatorias generadas por Microsoft 365 son visibles en el archivo de salida.</span><span class="sxs-lookup"><span data-stu-id="23681-159">We didn't specify passwords, so the random passwords that Microsoft 365 generated are visible in the output file.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="23681-160">Ver también</span><span class="sxs-lookup"><span data-stu-id="23681-160">See also</span></span>

[<span data-ttu-id="23681-161">Administrar cuentas de usuario, licencias y grupos de Microsoft 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="23681-161">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="23681-162">Administrar Microsoft 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="23681-162">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="23681-163">Introducción a PowerShell para Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="23681-163">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)
