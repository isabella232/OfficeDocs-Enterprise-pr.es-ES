---
title: Agregar un dominio a un arrendamiento de cliente con Windows PowerShell para asociados con permiso de acceso delegado (DAP)
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
ms.custom: ''
ms.assetid: f49b4d24-9aa0-48a6-95dd-6bae9cf53d2c
description: 'Resumen: Use Windows PowerShell para Office 365 para agregar un nombre de dominio alternativo a un inquilino de cliente existente.'
ms.openlocfilehash: 5f22e21e1eafc7c2d3fb9bc7286e860ad468445b
ms.sourcegitcommit: 4b057db053e93b0165f1ec6c4799cff4c2852566
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/25/2019
ms.locfileid: "39257469"
---
# <a name="add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-permission-dap-partners"></a><span data-ttu-id="0ba85-103">Agregar un dominio a un arrendamiento de cliente con Windows PowerShell para asociados con permiso de acceso delegado (DAP)</span><span class="sxs-lookup"><span data-stu-id="0ba85-103">Add a domain to a client tenancy with Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>

 <span data-ttu-id="0ba85-104">**Resumen:** use Windows PowerShell para Office 365 para agregar un nombre de dominio alternativo a un espacio empresarial de cliente existente.</span><span class="sxs-lookup"><span data-stu-id="0ba85-104">**Summary:** Use Windows PowerShell for Office 365 to add an alternate domain name to an existing customer tenant.</span></span>
  
<span data-ttu-id="0ba85-105">Puede crear y asociar nuevos dominios con el arrendamiento del cliente con Windows PowerShell para Office 365 más rápido que con el Centro de administración de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="0ba85-105">You can create and associate new domains with your customer's tenancy with Windows PowerShell for Office 365 faster than using the Microsoft 365 admin center.</span></span>
  
<span data-ttu-id="0ba85-106">Los asociados con permiso de acceso delegado (DAP) son asociados de sindicación y proveedor de soluciones en la nube (CSP).</span><span class="sxs-lookup"><span data-stu-id="0ba85-106">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="0ba85-107">Con frecuencia son los proveedores de red o de telecomunicaciones para otras compañías.</span><span class="sxs-lookup"><span data-stu-id="0ba85-107">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="0ba85-108">Empaquetan las suscripciones de Office 365 en sus ofertas de servicio a sus clientes.</span><span class="sxs-lookup"><span data-stu-id="0ba85-108">They bundle Office 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="0ba85-109">Cuando se vende una suscripción a Office 365, automáticamente se les conceden permisos Administrar en nombre de (AOBO) a los arrendamientos de cliente para que puedan administrar y notificar los arrendamientos de cliente.</span><span class="sxs-lookup"><span data-stu-id="0ba85-109">When they sell an Office 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="0ba85-110">¿Qué necesita saber antes de comenzar?</span><span class="sxs-lookup"><span data-stu-id="0ba85-110">What do you need to know before you begin?</span></span>

<span data-ttu-id="0ba85-p102">Los procedimientos de este tema requieren conectarse a Windows PowerShell para Office 365. Para obtener instrucciones, vea [Conectarse a PowerShell de Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="0ba85-p102">The procedures in this topic require you to connect to Windows PowerShell for Office 365. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
<span data-ttu-id="0ba85-113">Necesita también las credenciales del administrador de inquilinos del asociado.</span><span class="sxs-lookup"><span data-stu-id="0ba85-113">You also need your partner tenant administrator credentials.</span></span>
  
<span data-ttu-id="0ba85-114">También necesitará la siguiente información:</span><span class="sxs-lookup"><span data-stu-id="0ba85-114">You also need the following information:</span></span>
  
- <span data-ttu-id="0ba85-115">Necesitará el nombre de dominio completo (FQDN) que desea el cliente.</span><span class="sxs-lookup"><span data-stu-id="0ba85-115">You need the fully qualified domain name (FQDN) that your customer wants.</span></span>
    
- <span data-ttu-id="0ba85-116">Necesita el **TenantId** del cliente.</span><span class="sxs-lookup"><span data-stu-id="0ba85-116">You need the customer's **TenantId**.</span></span>
    
- <span data-ttu-id="0ba85-p103">El FQDN debe estar registrado con un registrador del servicio de nombres de dominio (DNS), como GoDaddy. Para obtener más información sobre cómo registrar públicamente un nombre de dominio, vea [Cómo comprar un nombre de dominio](https://go.microsoft.com/fwlink/p/?LinkId=532541).</span><span class="sxs-lookup"><span data-stu-id="0ba85-p103">The FQDN must be registered with an Internet domain name service (DNS) registrar, such as GoDaddy. For more information on how to publically register a domain name, see [How to buy a domain name](https://go.microsoft.com/fwlink/p/?LinkId=532541).</span></span>
    
- <span data-ttu-id="0ba85-p104">Necesita saber cómo agregar un registro TXT a la zona DNS registrada para su registrador DNS. Para obtener más información sobre cómo agregar un registro TXT, vea [Crear DNS en proveedores de hospedaje DNS para Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542). Si esos procedimientos no funcionan, necesitará encontrar los procedimientos de su registrador DNS.</span><span class="sxs-lookup"><span data-stu-id="0ba85-p104">You need to know how to add a TXT record to the registered DNS zone for your DNS registrar. For more information on how to add a TXT record, see [Create DNS records at any DNS hosting provider for Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542). If those procedures don't work for you, you will need to find the procedures for your DNS registrar.</span></span>
    
## <a name="create-domains"></a><span data-ttu-id="0ba85-122">Crear dominios</span><span class="sxs-lookup"><span data-stu-id="0ba85-122">Create domains</span></span>

 <span data-ttu-id="0ba85-p105">Sus clientes probablemente le pedirán crear dominios adicionales para asociar con su arrendamiento, ya que no desean que el dominio predeterminado <domain>.onmicrosoft.com sea el dominio principal que represente su identidad corporativa en el mundo. En este procedimiento se explica cómo crear un nuevo dominio asociado con el arrendamiento de su cliente.</span><span class="sxs-lookup"><span data-stu-id="0ba85-p105">Your customers will likely ask you to create additional domains to associate with their tenancy because they don't want the default <domain>.onmicrosoft.com domain to be the primary one that represents their corporate identities to the world. This procedure walks you through creating a new domain associated with your customer's tenancy.</span></span>
  
> [!NOTE]
> <span data-ttu-id="0ba85-125">Para realizar algunas de estas operaciones, la cuenta de administrador de asociados con la que inicia sesión debe estar establecida en **administración completa** para la opción **asignar acceso administrativo a compañías que admite, que** se encuentra en los detalles de la cuenta de administrador en el centro de administración de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="0ba85-125">To perform some of these operations, the partner administrator account you sign in with must be set to **Full administration** for the **Assign administrative access to companies you support** setting found in the details of the admin account in the Microsoft 365 admin center.</span></span> <span data-ttu-id="0ba85-126">Para obtener más información sobre cómo administrar roles de administrador de asociado, vea[Asociados: Ofrecer administración delegada](https://go.microsoft.com/fwlink/p/?LinkId=532435).</span><span class="sxs-lookup"><span data-stu-id="0ba85-126">For more information on managing partner administrator roles, see[Partners: Offer delegated administration](https://go.microsoft.com/fwlink/p/?LinkId=532435).</span></span> 
  
### <a name="create-the-domain-in-azure-active-directory"></a><span data-ttu-id="0ba85-127">Crear el dominio en Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="0ba85-127">Create the domain in Azure Active Directory</span></span>

<span data-ttu-id="0ba85-128">Este comando crea el dominio en Azure Active Directory, pero no lo asocia al dominio registrado públicamente.</span><span class="sxs-lookup"><span data-stu-id="0ba85-128">This command creates the domain in Azure Active Directory but does not associate it with the publicly registered domain.</span></span> <span data-ttu-id="0ba85-129">Eso sucede cuando le demuestra a Microsoft Office 365 para empresas que es propietario del dominio registrado públicamente.</span><span class="sxs-lookup"><span data-stu-id="0ba85-129">That comes when you prove that you own the publicly registered domain to Microsoft Office 365 for enterprises.</span></span>
  
```
New-MsolDomain -TenantId <customer TenantId> -Name <FQDN of new domain>
```

>[!Note]
><span data-ttu-id="0ba85-130">PowerShell Core no es compatible con el módulo Microsoft Azure Active Directory para el módulo y los cmdlets de Windows PowerShell con **msol** en su nombre.</span><span class="sxs-lookup"><span data-stu-id="0ba85-130">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="0ba85-131">Para seguir usando estos cmdlets, debe ejecutarlos desde Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0ba85-131">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

### <a name="get-the-data-for-the-dns-txt-verification-record"></a><span data-ttu-id="0ba85-132">Obtener los datos para la verificación del registro TXT de DNS</span><span class="sxs-lookup"><span data-stu-id="0ba85-132">Get the data for the DNS TXT verification record</span></span>

 <span data-ttu-id="0ba85-p109">Office 365 generará los datos específicos que necesita colocar en el registro de comprobación de TXT de DNS. Para obtener los datos, ejecute este comando.</span><span class="sxs-lookup"><span data-stu-id="0ba85-p109">Office 365 will generate the specific data that you need to place into the DNS TXT verification record. To get the data, run this command.</span></span>
  
```
Get-MsolDomainVerificationDNS -TenantId <customer TenantId> -DomainName <FQDN of new domain> -Mode DnsTxtRecord
```

<span data-ttu-id="0ba85-135">Se obtendrá el siguiente resultado:</span><span class="sxs-lookup"><span data-stu-id="0ba85-135">This will give you output like:</span></span>
  
 `Label: domainname.com`
  
 `Text: MS=ms########`
  
 `Ttl: 3600`
  
> [!NOTE]
> <span data-ttu-id="0ba85-136">Necesitará este texto para crear el registro TXT en la zona DNS registrada públicamente.</span><span class="sxs-lookup"><span data-stu-id="0ba85-136">You will need this text to create the TXT record in the publicly registered DNS zone.</span></span> <span data-ttu-id="0ba85-137">Asegúrese de copiarlo y guardarlo.</span><span class="sxs-lookup"><span data-stu-id="0ba85-137">Be sure to copy and save it.</span></span> 
  
### <a name="add-a-txt-record-to-the-publically-registered-dns-zone"></a><span data-ttu-id="0ba85-138">Agregar un registro TXT a la zona DNS registrada públicamente</span><span class="sxs-lookup"><span data-stu-id="0ba85-138">Add a TXT record to the publically registered DNS zone</span></span>

<span data-ttu-id="0ba85-139">Antes de que Office 365 empiece a aceptar tráfico que se dirigirá al nombre de dominio registrado públicamente, debe demostrar que tiene permisos de administrador sobre el dominio.</span><span class="sxs-lookup"><span data-stu-id="0ba85-139">Before Office 365 will start accepting traffic that is directed to the publicly registered domain name, you must prove that you own and have administrator permissions to the domain.</span></span> <span data-ttu-id="0ba85-140">Demuestre que el dominio le pertenece mediante la creación de un registro TXT en el dominio.</span><span class="sxs-lookup"><span data-stu-id="0ba85-140">You prove you own the domain by creating a TXT record in the domain.</span></span> <span data-ttu-id="0ba85-141">Un registro TXT no hace nada en su dominio y puede eliminarse una vez que se establezca su propiedad del dominio.</span><span class="sxs-lookup"><span data-stu-id="0ba85-141">A TXT record doesn't do anything in your domain, and it can be deleted after your ownership of the domain is established.</span></span> <span data-ttu-id="0ba85-142">Para crear los registros TXT, siga los procedimientos en [Crear DNS en proveedores de hospedaje DNS para Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542).</span><span class="sxs-lookup"><span data-stu-id="0ba85-142">To create the TXT records, follow the procedures at [Create DNS records at any DNS hosting provider for Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542).</span></span> <span data-ttu-id="0ba85-143">Si esos procedimientos no funcionan, necesitará encontrar los procedimientos de su registrador DNS.</span><span class="sxs-lookup"><span data-stu-id="0ba85-143">If those procedures don't work for you , you need to find the procedures for your DNS registrar.</span></span>
  
<span data-ttu-id="0ba85-p112">Confirme la creación correcta del registro TXT mediante nslookup. Siga esta sintaxis.</span><span class="sxs-lookup"><span data-stu-id="0ba85-p112">Confirm the successful creation of the TXT record via nslookup. Follow this syntax.</span></span>
  
```
nslookup -type=TXT <FQDN of registered domain>
```

<span data-ttu-id="0ba85-146">Se obtendrá el siguiente resultado:</span><span class="sxs-lookup"><span data-stu-id="0ba85-146">This will give you output like:</span></span>
  
 `Non-authoritative answer:`
  
 `FQDN of the registered domain`
  
 `text=MS=ms########`
  
### <a name="validate-domain-ownership-in-office-365"></a><span data-ttu-id="0ba85-147">Validar la propiedad del dominio en Office 365</span><span class="sxs-lookup"><span data-stu-id="0ba85-147">Validate domain ownership in Office 365</span></span>

<span data-ttu-id="0ba85-p113">En este último paso, el usuario valida en Office 365 que es el propietario del dominio registrado públicamente. Después de este paso, Office 365 empezará a aceptar tráfico enrutado al nuevo nombre de dominio. Para completar la creación del dominio y el proceso de registro, ejecute este comando.</span><span class="sxs-lookup"><span data-stu-id="0ba85-p113">In this last step, you validate to Office 365 that you own the publically registered domain. After this step, Office 365 will begin accepting traffic routed to the new domain name. To complete the domain creation and registration process, run this command.</span></span> 
  
```
Confirm-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

<span data-ttu-id="0ba85-151">Este comando no devolverá ningún resultado, por lo tanto, para confirmar que funcionó, ejecute este comando.</span><span class="sxs-lookup"><span data-stu-id="0ba85-151">This command won't return any output, so to confirm that this worked, run this command.</span></span>
  
```
Get-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

<span data-ttu-id="0ba85-152">Se mostrará un resultado semejante a</span><span class="sxs-lookup"><span data-stu-id="0ba85-152">This will return something like this</span></span>
  
||||
|:-----|:-----|:-----|
| `Name` <br/> | `Status` <br/> | `Authentication` <br/> |
| `FQDN of new domain` <br/> | `Verified` <br/> | `Managed` <br/> |
   
## <a name="see-also"></a><span data-ttu-id="0ba85-153">Consulte también</span><span class="sxs-lookup"><span data-stu-id="0ba85-153">See also</span></span>

#### 

[<span data-ttu-id="0ba85-154">Ayuda para asociados</span><span class="sxs-lookup"><span data-stu-id="0ba85-154">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)

