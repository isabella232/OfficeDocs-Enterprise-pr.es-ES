---
title: Administración de buzones de correo de Exchange Online en un entorno multigeográfico
ms.author: chrisda
author: chrisda
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: Obtenga información sobre cómo administrar el ajuste multigeográfico de Exchange Online con Microsoft PowerShell.
ms.openlocfilehash: 5e1108c946ab1d9588ad5d1d41f21799e8254257
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2019
ms.locfileid: "30934094"
---
# <a name="administering-exchange-online-mailboxes-in-a-multi-geo-environment"></a><span data-ttu-id="ea3df-103">Administración de buzones de correo de Exchange Online en un entorno multigeográfico</span><span class="sxs-lookup"><span data-stu-id="ea3df-103">Administering Exchange Online mailboxes in a multi-geo environment</span></span>

<span data-ttu-id="ea3df-104">Se requiere un PowerShell remoto para ver y configurar las propiedades multigeográficas en su entorno de Office 365.</span><span class="sxs-lookup"><span data-stu-id="ea3df-104">Remote PowerShell is required to view and configure multi geo properties in your Office 365 environment.</span></span> <span data-ttu-id="ea3df-105">Para conectarse al PowerShell de Exchange Online, consulte [Conectarse al PowerShell de Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span><span class="sxs-lookup"><span data-stu-id="ea3df-105">To learn how to connect to Exchange Online PowerShell, see [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span></span>

<span data-ttu-id="ea3df-106">Necesitará la v1.1.166.0 o una versión posterior en la v1.x del [módulo PowerShell de Microsoft Azure Active Directory](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) para ver la propiedad **PreferredDataLocation** en los objetos de usuario.</span><span class="sxs-lookup"><span data-stu-id="ea3df-106">You need the [Microsoft Azure Active Directory PowerShell Module](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 or later in v1.x to see the **PreferredDataLocation** property on user objects.</span></span> <span data-ttu-id="ea3df-107">No se puede modificar el valor de **PreferredDataLocation** directamente a través del PowerShell de AAD en los objetos de usuario que se sincronizan en AAD a través de AAD Connect.</span><span class="sxs-lookup"><span data-stu-id="ea3df-107">User objects synchronized via AAD Connect into AAD cannot have their **PreferredDataLocation** value directly modified via AAD PowerShell.</span></span> <span data-ttu-id="ea3df-108">Solo se pueden modificar objetos basados en la nube a través del PowerShell de AAD.</span><span class="sxs-lookup"><span data-stu-id="ea3df-108">Cloud-only user objects can be modified via AAD PowerShell.</span></span> <span data-ttu-id="ea3df-109">Para conectarse al PowerShell de Azure AD, consulte [Conectarse al PowerShell de Office 365](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span><span class="sxs-lookup"><span data-stu-id="ea3df-109">To connect to Security & Compliance Center PowerShell, see [Connect to Office 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span></span> 

## <a name="connect-directly-to-a-geo-location-using-exchange-online-powershell"></a><span data-ttu-id="ea3df-110">Conectarse directamente a una ubicación geográfica con el PowerShell de Exchange Online</span><span class="sxs-lookup"><span data-stu-id="ea3df-110">Connect directly to a geo location using Exchange Online PowerShell</span></span>
<span data-ttu-id="ea3df-111">Normalmente, el PowerShell de Exchange Online se conecta a la ubicación central.</span><span class="sxs-lookup"><span data-stu-id="ea3df-111">Typically, Exchange Online PowerShell will connect to the central location.</span></span> <span data-ttu-id="ea3df-112">Sin embargo, también puede conectarse directamente a las ubicaciones satélite.</span><span class="sxs-lookup"><span data-stu-id="ea3df-112">But, you can also connect directly to satellite locations.</span></span> <span data-ttu-id="ea3df-113">Gracias a las mejoras en el rendimiento, se recomienda conectarse directamente a la ubicación satélite si únicamente administra usuarios en esa ubicación geográfica.</span><span class="sxs-lookup"><span data-stu-id="ea3df-113">Because of performance improvements, we recommend connecting directly to the satellite location when you only manage users in that geo location.</span></span>

<span data-ttu-id="ea3df-114">Para conectarse a una ubicación geográfica específica, el parámetro *ConnectionUri* es diferente a las instrucciones de conexión normales.</span><span class="sxs-lookup"><span data-stu-id="ea3df-114">To connect to a specific geo location, the *ConnectionUri* parameter is different than the regular connection instructions.</span></span> <span data-ttu-id="ea3df-115">El resto de comandos y valores son los mismos.</span><span class="sxs-lookup"><span data-stu-id="ea3df-115">The rest of the commands and values are the same.</span></span> <span data-ttu-id="ea3df-116">Estos pasos son:</span><span class="sxs-lookup"><span data-stu-id="ea3df-116">The steps are:</span></span>

1. <span data-ttu-id="ea3df-117">En el equipo local, abra Windows PowerShell y ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="ea3df-117">On your local computer, open Windows PowerShell and run the following command.</span></span>
    
    ```
    $UserCredential = Get-Credential
    ```
   <span data-ttu-id="ea3df-118">En el cuadro de diálogo **Solicitud de credenciales para Windows PowerShell**, escriba el usuario de su cuenta profesional o educativa y la contraseña, y luego haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="ea3df-118">In the **Windows PowerShell Credential Request** dialog box, type your work or school account and password, and then click **OK**.</span></span>
    
2. <span data-ttu-id="ea3df-119">Reemplace `<emailaddress>` con la dirección de correo electrónico de **cualquier** buzón en la ubicación geográfica de destino y ejecute el comando siguiente.</span><span class="sxs-lookup"><span data-stu-id="ea3df-119">Replace `<emailaddress>` with the email address of **any** mailbox in the target geo location and run the following command.</span></span> <span data-ttu-id="ea3df-120">Los permisos en el buzón y la relación con sus credenciales en el paso 1 no se tienen en cuenta; la dirección de correo electrónico simplemente indica a Exchange Online dónde debe conectarse.</span><span class="sxs-lookup"><span data-stu-id="ea3df-120">Your permissions on the mailbox and the relationship to your credentials in Step 1 are not a factor; the email address simply tells Exchange Online where to connect.</span></span>
  
   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   <span data-ttu-id="ea3df-121">Por ejemplo, si olga@contoso.onmicrosoft.com es la dirección de correo electrónico de un buzón válido en la ubicación geográfica a la que desea conectarse, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="ea3df-121">For example, if olga@contoso.onmicrosoft.com is the email address of a valid mailbox in the Geo you want to connect, run the following command:</span></span>

   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```
3. <span data-ttu-id="ea3df-122">Ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="ea3df-122">Run the following command:</span></span>
    
    ```
    Import-PSSession $Session
    ```


## <a name="view-the-available-geo-locations-that-are-configured-in-your-exchange-online-organization"></a><span data-ttu-id="ea3df-123">Ver las ubicaciones geográficas disponibles configuradas en su organización de Exchange Online</span><span class="sxs-lookup"><span data-stu-id="ea3df-123">View the available geo locations that are configured in your Exchange Online organization</span></span>
<span data-ttu-id="ea3df-124">Para ver la lista de ubicaciones geográficas configuradas en Office 365 Multi-Geo, ejecute el siguiente comando en el PowerShell de Exchange Online:</span><span class="sxs-lookup"><span data-stu-id="ea3df-124">To see the list of configured geo locations in Office 365 Multi-Geo, run the following command in Exchange Online PowerShell:</span></span>

```
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table
```

## <a name="view-the-central-location-for-your-exchange-online-organization"></a><span data-ttu-id="ea3df-125">Ver la ubicación central para su organización de Exchange Online</span><span class="sxs-lookup"><span data-stu-id="ea3df-125">View the central location for your Exchange Online organization</span></span>
<span data-ttu-id="ea3df-126">Para ver la ubicación central de su inquilino, ejecute el siguiente comando en el PowerShell de Exchange Online:</span><span class="sxs-lookup"><span data-stu-id="ea3df-126">To view your tenant's central location, run the following command in Exchange Online PowerShell:</span></span>

```
Get-OrganizationConfig | Select DefaultMailboxRegion
```

## <a name="find-the-geo-location-of-a-mailbox"></a><span data-ttu-id="ea3df-127">Buscar la ubicación geográfica de un buzón</span><span class="sxs-lookup"><span data-stu-id="ea3df-127">Find the geo location of a mailbox</span></span>
<span data-ttu-id="ea3df-128">El cmdlet **Get-Mailbox** en el PowerShell de Exchange Online muestra las siguientes propiedades multigeográficas en buzones:</span><span class="sxs-lookup"><span data-stu-id="ea3df-128">The **Get-Mailbox** cmdlet in Exchange Online PowerShell displays the following multi-geo related properties on mailboxes:</span></span>

- <span data-ttu-id="ea3df-129">**Database**: Las tres primeras letras del nombre de la base de datos corresponden al código geográfico, que indica dónde se encuentra el buzón.</span><span class="sxs-lookup"><span data-stu-id="ea3df-129">**Database**: The first 3 letters of the database name correspond to the geo code, which tells you where the mailbox is currently located.</span></span> <span data-ttu-id="ea3df-130">Para los buzones de archivo en línea, podría usarse la propiedad **ArchiveDatabase**.</span><span class="sxs-lookup"><span data-stu-id="ea3df-130">For Online Archive Mailboxes the **ArchiveDatabase** property should be used.</span></span>

- <span data-ttu-id="ea3df-131">**MailboxRegion**: Especifica el código de ubicación geográfica definido por el administrador (sincronizado desde **PreferredDataLocation** en Azure AD).</span><span class="sxs-lookup"><span data-stu-id="ea3df-131">**MailboxRegion**: Specifies the geo location code that was set by the admin (synchronized from **PreferredDataLocation** in Azure AD).</span></span>

- <span data-ttu-id="ea3df-132">**MailboxRegionLastUpdateTime**: Indica cuándo se actualizó MailboxRegion por última vez (de forma automática o manual).</span><span class="sxs-lookup"><span data-stu-id="ea3df-132">**MailboxRegionLastUpdateTime**: Indicates when MailboxRegion was last updated (either automatically or manually).</span></span>

<span data-ttu-id="ea3df-133">Para ver estas propiedades de un buzón, use la siguiente sintaxis:</span><span class="sxs-lookup"><span data-stu-id="ea3df-133">To see these properties for a mailbox, use the following syntax:</span></span>

```
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

<span data-ttu-id="ea3df-134">Por ejemplo, para ver la información geográfica del buzón chris@contoso.onmicrosoft.com, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="ea3df-134">For example, to see the Geo information for the mailbox chris@contoso.onmicrosoft.com, run the following command:</span></span>

```
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

<span data-ttu-id="ea3df-135">El resultado del comando tiene este aspecto:</span><span class="sxs-lookup"><span data-stu-id="ea3df-135">The output of the command looks like this:</span></span>

```
Database                    : EURPR03DG077-db007 
MailboxRegion               : EUR 
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM 
```

> <span data-ttu-id="ea3df-136">**Nota:** Si el código de ubicación geográfica en el nombre de la base de datos no coincide con el valor de **MailboxRegion**, el buzón se pondrá automáticamente en una cola de reubicación y se moverá a la ubicación geográfica especificada por el valor \*\* MailboxRegion\*\* (Exchange Online busca un error de coincidencia entre estos valores de propiedad).</span><span class="sxs-lookup"><span data-stu-id="ea3df-136">**Note:** If the geo location code in the database name doesn't match **MailboxRegion** value, the mailbox will be automatically be put into a relocation queue and moved to the geo location specified by the **MailboxRegion** value (Exchange Online looks for a mismatch between these property values).</span></span>

## <a name="move-an-existing-cloud-only-mailbox-to-a-specific-geo-location"></a><span data-ttu-id="ea3df-137">Mover un buzón existente basado únicamente en la nube a una ubicación geográfica específica</span><span class="sxs-lookup"><span data-stu-id="ea3df-137">Move an existing cloud-only mailbox to a specific geo location</span></span>
<span data-ttu-id="ea3df-138">Un usuario basado únicamente en la nube es un usuario que no está sincronizado con el inquilino a través de AAD Connect.</span><span class="sxs-lookup"><span data-stu-id="ea3df-138">A cloud-only user is a user not syncrhonized to the tenant via AAD Connect.</span></span> <span data-ttu-id="ea3df-139">Dicho usuario se creó directamente en Azure AD.</span><span class="sxs-lookup"><span data-stu-id="ea3df-139">This user was created directly in Azure AD.</span></span> <span data-ttu-id="ea3df-140">Use los cmdlets **Get-MsolUser** y **Set-MsolUser** en el módulo de Azure AD para Windows PowerShell para ver o especificar la ubicación geográfica donde se almacenará el buzón de un usuario basado únicamente en la nube.</span><span class="sxs-lookup"><span data-stu-id="ea3df-140">Use the **Get-MsolUser** and **Set-MsolUser** cmdlets in the Azure AD Module for Windows PowerShell to view or specify the Geo where a cloud-only user's mailbox will be stored.</span></span>

<span data-ttu-id="ea3df-141">Para ver el valor **PreferredDataLocation** de un usuario, use la siguiente sintaxis en el PowerShell de Azure AD:</span><span class="sxs-lookup"><span data-stu-id="ea3df-141">To view the **PreferredDataLocation** value for a user, use this syntax in Azure AD PowerShell:</span></span>

```
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

<span data-ttu-id="ea3df-142">Por ejemplo, para ver el valor de **PreferredDataLocation** para el usuario michelle@contoso.onmicrosoft.com, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="ea3df-142">For example, to see the **PreferredDataLocation** value for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

```
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

<span data-ttu-id="ea3df-143">Para modificar el valor de **PreferredDataLocation** para un objeto de un usuario basado únicamente en la nube, use la siguiente sintaxis en el PowerShell de Azure AD:</span><span class="sxs-lookup"><span data-stu-id="ea3df-143">To modify the **PreferredDataLocation** value for a cloud-only user object, use the following syntax in Azure AD PowerShell:</span></span>

``` 
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoCode>
```

<span data-ttu-id="ea3df-144">Por ejemplo, para definir el valor de **PreferredDataLocation** en la ubicación geográfica Unión Europea (EUR) para el usuario michelle@contoso.onmicrosoft.com, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="ea3df-144">For example, to set the **PreferredDataLocation** value to the European Union (EUR) geo for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

``` 
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

<span data-ttu-id="ea3df-145">**Notas**:</span><span class="sxs-lookup"><span data-stu-id="ea3df-145">**Notes**:</span></span>

- <span data-ttu-id="ea3df-146">Como se mencionó anteriormente, no puede usar este procedimiento para objetos sincronizados del usuario desde el entorno local de Active Directory.</span><span class="sxs-lookup"><span data-stu-id="ea3df-146">As mentioned previously you cannot use this procedure for synchronized user objects from on-premises Active Directory.</span></span> <span data-ttu-id="ea3df-147">Tiene que cambiar el valor de **PreferredDataLocation** en Active Directory y sincronizarlo con AAD Connect.</span><span class="sxs-lookup"><span data-stu-id="ea3df-147">You need to change the **PreferredDataLocation** value in Active Directory and synchronize it using AAD Connect.</span></span> <span data-ttu-id="ea3df-148">Para obtener más información, consulte [Sincronización de Azure Active Directory Connect: configurar la ubicación de datos preferida para recursos de Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span><span class="sxs-lookup"><span data-stu-id="ea3df-148">For more information, see [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span> 

- <span data-ttu-id="ea3df-149">El tiempo que se tarda en reubicar un buzón a una nueva ubicación geográfica depende de varios factores:</span><span class="sxs-lookup"><span data-stu-id="ea3df-149">How long it takes to relocate a mailbox to a new geo location depends on several factors:</span></span>
 
  - <span data-ttu-id="ea3df-150">El tamaño y tipo de buzón.</span><span class="sxs-lookup"><span data-stu-id="ea3df-150">The size and type of mailbox.</span></span>
 
  - <span data-ttu-id="ea3df-151">La cantidad de buzones que se migrarán.</span><span class="sxs-lookup"><span data-stu-id="ea3df-151">The number of mailboxes being moved.</span></span>
 
  - <span data-ttu-id="ea3df-152">La disponibilidad de recursos de migración.</span><span class="sxs-lookup"><span data-stu-id="ea3df-152">The availability of move resources.</span></span>

### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a><span data-ttu-id="ea3df-153">Mover buzones deshabilitados que se encuentran en Retención por juicio</span><span class="sxs-lookup"><span data-stu-id="ea3df-153">Move disabled mailboxes that are on Litigation Hold</span></span>
<span data-ttu-id="ea3df-154">Los buzones deshabilitados en Retención por juicio que se conservan para eDiscovery no se pueden mover cambiando el valor de **PreferredDataLocation** en el estado deshabilitado.</span><span class="sxs-lookup"><span data-stu-id="ea3df-154">Disabled mailboxes on Litigation Hold that are preserved for eDiscovery purposes cannot be moved by changing their **PreferredDataLocation** value in their disabled state.</span></span> <span data-ttu-id="ea3df-155">Para mover un buzón deshabilitado en Retención por juicio:</span><span class="sxs-lookup"><span data-stu-id="ea3df-155">To move a disabled mailbox on litigation hold:</span></span>

1. <span data-ttu-id="ea3df-156">Asigne temporalmente una licencia al buzón.</span><span class="sxs-lookup"><span data-stu-id="ea3df-156">Temporarily assign a license to the mailbox.</span></span>

2. <span data-ttu-id="ea3df-157">Cambie el valor de **PreferredDataLocation**.</span><span class="sxs-lookup"><span data-stu-id="ea3df-157">Change the **PreferredDataLocation**.</span></span>

3. <span data-ttu-id="ea3df-158">Elimine la licencia del buzón después de moverlo a la ubicación geográfica seleccionada para volver a definir el estado de deshabilitado.</span><span class="sxs-lookup"><span data-stu-id="ea3df-158">Remove the license from the mailbox after it has been moved to the selected geo location to put it back into the disabled state.</span></span>

## <a name="create-new-cloud-mailboxes-in-a-specific-geo-location"></a><span data-ttu-id="ea3df-159">Crear nuevos buzones basados en la nube en una ubicación geográfica específica</span><span class="sxs-lookup"><span data-stu-id="ea3df-159">Create new cloud mailboxes in a specific geo location</span></span>
<span data-ttu-id="ea3df-160">Para crear un nuevo buzón en una ubicación geográfica específica, debe realizar uno de estos pasos:</span><span class="sxs-lookup"><span data-stu-id="ea3df-160">To create a new mailbox in a specific geo location, you need to do either of these steps:</span></span>

- <span data-ttu-id="ea3df-161">Configurar el valor de **PreferredDataLocation** como se describe en la sección anterior *antes* de crear el buzón en Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="ea3df-161">Configure the **PreferredDataLocation** value as described in the previous section *before* the mailbox is created in Exchange Online.</span></span> <span data-ttu-id="ea3df-162">Por ejemplo, configure el valor de **PreferredDataLocation** de un usuario antes de asignarle una licencia.</span><span class="sxs-lookup"><span data-stu-id="ea3df-162">For example, configure the **PreferredDataLocation** value on a user before assigning a license.</span></span> 

- <span data-ttu-id="ea3df-163">Asignar una licencia al mismo tiempo que se define el valor de **PreferredDataLocation**.</span><span class="sxs-lookup"><span data-stu-id="ea3df-163">Assign a license at the same time you set the **PreferredDataLocation** value.</span></span>

<span data-ttu-id="ea3df-164">Para crear un nuevo usuario con licencia basado únicamente en la nube (que no esté sincronizado con AAD Connect) en una ubicación geográfica específica, use la siguiente sintaxis en el PowerShell de Azure AD:</span><span class="sxs-lookup"><span data-stu-id="ea3df-164">To create a new cloud-only licensed user (not AAD Connect synchronized) in a specific Geo, use the following syntax in Azure AD PowerShell:</span></span>

```
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoCode> 
```
<span data-ttu-id="ea3df-165">Este ejemplo crea una cuenta de usuario para Elizabeth Brunner con los valores siguientes:</span><span class="sxs-lookup"><span data-stu-id="ea3df-165">This example create a new user account for Elizabeth Brunner with the following values:</span></span>

- <span data-ttu-id="ea3df-166">Nombre de usuario principal: ebrunner@contoso.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="ea3df-166">User principal name: ebrunner@contoso.onmicrosoft.com</span></span>

- <span data-ttu-id="ea3df-167">Nombre: Elizabeth</span><span class="sxs-lookup"><span data-stu-id="ea3df-167">First name: Elizabeth</span></span>

- <span data-ttu-id="ea3df-168">Apellido: Brunner</span><span class="sxs-lookup"><span data-stu-id="ea3df-168">Last name: Brunner</span></span>

- <span data-ttu-id="ea3df-169">Nombre para mostrar: Elizabeth Brunner</span><span class="sxs-lookup"><span data-stu-id="ea3df-169">Display name Elizabeth Brunner</span></span>

- <span data-ttu-id="ea3df-170">Contraseña: Se genera de forma aleatoria y se muestra en los resultados del comando (debido a que no se usa el parámetro *contraseña*)</span><span class="sxs-lookup"><span data-stu-id="ea3df-170">Password: randomly-generated and shown in the results of the command (because we're not using the *Password* parameter)</span></span>

- <span data-ttu-id="ea3df-171">Licencia: contoso:ENTERPRISEPREMIUM (E5)</span><span class="sxs-lookup"><span data-stu-id="ea3df-171">License: contoso:ENTERPRISEPREMIUM (E5)</span></span>

- <span data-ttu-id="ea3df-172">Ubicación: Australia (AUS)</span><span class="sxs-lookup"><span data-stu-id="ea3df-172">Location: Australia (AUS)</span></span>

```
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

<span data-ttu-id="ea3df-173">Para obtener más información sobre cómo crear nuevas cuentas de usuario y cómo encontrar valores de LicenseAssignment en el PowerShell de Azure AD, consulte [Crear cuentas de usuario con el PowerShell de Office 365](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) y [Ver licencias y servicios con el PowerShell de Office 365](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).</span><span class="sxs-lookup"><span data-stu-id="ea3df-173">For more information about creating new user accounts and finding LicenseAssignment values in Azure AD PowerShell, see [Create user accounts with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) and [View licenses and services with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).</span></span>

> <span data-ttu-id="ea3df-174">**Nota:** Si usa el PowerShell de Exchange Online para habilitar un buzón y necesita que este se cree directamente en la ubicación geográfica especificada en **PreferredDataLocation**, debe usar un cmdlet de Exchange Online como **Enable-Mailbox** o **New-Mailbox** directamente con el servicio basado en la nube.</span><span class="sxs-lookup"><span data-stu-id="ea3df-174">**Note:** If you are using Exchange Online PowerShell to enable a mailbox and need the mailbox to be created directly in the Geo that's specified in **PreferredDataLocation**, you need to use an Exchange Online cmdlet such as **Enable-Mailbox** or **New-Mailbox** directly against the cloud service.</span></span> <span data-ttu-id="ea3df-175">Si usa el cmdlet **Enable-RemoteMailbox** en el entorno local de Exchange, el buzón se creará en la ubicación central.</span><span class="sxs-lookup"><span data-stu-id="ea3df-175">If you use the **Enable-RemoteMailbox** on-premises Exchange cmdlet, the mailbox will be created in the central location.</span></span>

## <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo-location"></a><span data-ttu-id="ea3df-176">Incorporar buzones existentes en el entorno local a una ubicación geográfica específica</span><span class="sxs-lookup"><span data-stu-id="ea3df-176">Onboard existing on-premises mailboxes in a specific geo location</span></span>
<span data-ttu-id="ea3df-177">Puede usar las herramientas y procesos de incorporación estándar para migrar un buzón del entorno local de una organización de Exchange a Exchange Online, incluidos el [Panel de migración en el EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331) y el cmdlet [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) del PowerShell de Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="ea3df-177">You can use the standard onboarding tools and processes to migrate a mailbox from an on-premises Exchange organization to Exchange Online, including the [Migration dashboard in the EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331), and the [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) cmdlet in Exchange Online PowerShell.</span></span>

<span data-ttu-id="ea3df-178">El primer paso consiste en comprobar que existe un objeto de usuario para que cada buzón se quiere incorporar y comprobar que el valor de **PreferredDataLocation** está configurado correctamente en Azure AD.</span><span class="sxs-lookup"><span data-stu-id="ea3df-178">The first step is to verify a user object exists for each mailbox to be onboarded, and verify the correct **PreferredDataLocation** value is configured in Azure AD.</span></span> <span data-ttu-id="ea3df-179">Las herramientas de incorporación respetarán el valor de **PreferredDataLocation** y migrarán los buzones directamente a la ubicación geográfica especificada.</span><span class="sxs-lookup"><span data-stu-id="ea3df-179">The onboarding tools will respect the **PreferredDataLocation** value and will migrate the mailboxes directly to the specified Geo.</span></span>

<span data-ttu-id="ea3df-180">Como alternativa, puede seguir los pasos a continuación para incorporar buzones directamente a una ubicación geográfica específica con el cmdlet [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) del PowerShell de Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="ea3df-180">Or, you can use the following steps to onboard mailboxes directly in a specific geo location using the [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) cmdlet in Exchange Online PowerShell.</span></span>

1. <span data-ttu-id="ea3df-181">Compruebe que existe el objeto de usuario para cada buzón que se va a incorporar y que **PreferredDataLocation** está definido en el valor deseado en Azure AD.</span><span class="sxs-lookup"><span data-stu-id="ea3df-181">Verify the user object exists for each mailbox to be onboarded and that **PreferredDataLocation** is set to the desired value in Azure AD.</span></span> <span data-ttu-id="ea3df-182">El valor de **PreferredDataLocation** se sincronizará con el atributo **MailboxRegion** del objeto de usuario del correo correspondiente en Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="ea3df-182">The value of **PreferredDataLocation** will be synchronized to the **MailboxRegion** attribute of the corresponding mail user object in Exchange Online.</span></span>

2. <span data-ttu-id="ea3df-183">Conéctese directamente con la ubicación geográfica satélite específica siguiendo las instrucciones de conexión mostradas anteriormente en este tema.</span><span class="sxs-lookup"><span data-stu-id="ea3df-183">Connect directly to the specific satellite Geo using the connection instructions from earlier in this topic.</span></span>

3. <span data-ttu-id="ea3df-184">En el PowerShell de Exchange Online, almacene en una variable las credenciales de administrador del entorno local que se usan para realizar una migración de buzones ejecutando el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="ea3df-184">In Exchange Online PowerShell, store the on-premises administrator credentials that's used to perform a mailbox migration in a variable by running the following command:</span></span>

    ```
    $RC = Get-Credential
    ```

4. <span data-ttu-id="ea3df-185">En el PowerShell de Exchange Online, cree un nuevo **New-MoveRequest** similar al del ejemplo siguiente:</span><span class="sxs-lookup"><span data-stu-id="ea3df-185">In Exchange Online PowerShell, create a new **New-MoveRequest** similar to the following example:</span></span> 

    ```
    New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
    ```

5. <span data-ttu-id="ea3df-186">Repita el paso 4 para cada buzón que quiera migrar del entorno local de Exchange a la ubicación satélite a la que está conectado actualmente.</span><span class="sxs-lookup"><span data-stu-id="ea3df-186">Repeat step #4 for every mailbox you need to migrate from on-premises Exchange to the satellite location you are currently connected to.</span></span>

6. <span data-ttu-id="ea3df-187">Si quiere migrar más buzones a una ubicación satélite diferente, repita los pasos 2 a 4 para cada ubicación satélite específica.</span><span class="sxs-lookup"><span data-stu-id="ea3df-187">If you need to migrate additional mailboxes to a different satellite location, repeat steps 2 through 4 for each specific satellite location.</span></span>

## <a name="multi-geo-reporting"></a><span data-ttu-id="ea3df-188">Informes multigeográficos</span><span class="sxs-lookup"><span data-stu-id="ea3df-188">Multi-geo reporting</span></span>
<span data-ttu-id="ea3df-189">Los **Informes de uso multigeográfico** en el Centro de administración de Microsoft 365 muestran el número de usuarios por ubicación geográfica.</span><span class="sxs-lookup"><span data-stu-id="ea3df-189">**Multi-Geo Usage Reports** in the Microsoft 365 admin center displays the user count by geo location.</span></span> <span data-ttu-id="ea3df-190">El informe muestra la distribución de usuarios durante el mes actual y proporciona los datos históricos para los últimos 6 meses.</span><span class="sxs-lookup"><span data-stu-id="ea3df-190">The report displays user distribution for the current month and provides historical data for the past 6 months.</span></span>

## <a name="see-also"></a><span data-ttu-id="ea3df-191">Vea también</span><span class="sxs-lookup"><span data-stu-id="ea3df-191">See also</span></span>

[<span data-ttu-id="ea3df-192">Administración de Office 365 y Exchange Online con Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ea3df-192">Managing Office 365 and Exchange Online with Windows PowerShell</span></span>](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6)