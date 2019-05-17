---
title: Identidad híbrida y sincronización de directorios para Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MOE150
- MET150
ms.assetid: d3577c90-dda5-45ca-afb0-370d2889b10f
description: Describe la sincronización de directorios con Office 365, la limpieza de los servicios de dominio de Active Directory y la herramienta Azure Active Directory Connect.
ms.openlocfilehash: 31fcd8baaccabf5d3f4f0cf47c7573c43f7cd40b
ms.sourcegitcommit: 47c6156c0038745103b71f44b2a3b103c62e5d6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2019
ms.locfileid: "34102507"
---
# <a name="hybrid-identity-and-directory-synchronization-for-office-365"></a><span data-ttu-id="ceeee-103">Identidad híbrida y sincronización de directorios para Office 365</span><span class="sxs-lookup"><span data-stu-id="ceeee-103">Hybrid identity and directory synchronization for Office 365</span></span>

<span data-ttu-id="ceeee-104">En función de las necesidades empresariales y los requisitos técnicos, el modelo de identidad híbrida y la sincronización de directorios son las opciones más comunes para los clientes empresariales que están adoptando Office 365.</span><span class="sxs-lookup"><span data-stu-id="ceeee-104">Depending on business needs and technical requirements, the hybrid identity model and directory synchronization is the most common choice for enterprise customers who are adopting Office 365.</span></span> <span data-ttu-id="ceeee-105">La sincronización de directorios permite administrar las identidades de los servicios de dominio de Active Directory (AD DS) y todas las actualizaciones de las cuentas de usuario, los grupos y los contactos se sincronizan con el inquilino de Azure Active Directory (Azure AD) de la suscripción a Office 365.</span><span class="sxs-lookup"><span data-stu-id="ceeee-105">Directory synchronization allows you to manage identities in your Active Directory Domain Services (AD DS) and all updates to user accounts, groups, and contacts are synchronized to the Azure Active Directory (Azure AD) tenant of your Office 365 subscription.</span></span>


>[!Note]
><span data-ttu-id="ceeee-106">Cuando las cuentas de usuario de AD DS se sincronizan por primera vez, no se les asigna automáticamente una licencia de Office 365 y no se puede acceder a los servicios de Office 365, como el correo electrónico.</span><span class="sxs-lookup"><span data-stu-id="ceeee-106">When AD DS user accounts are synchronized for the first time, they are not automatically assigned an Office 365 license and cannot access Office 365 services, such as email.</span></span> <span data-ttu-id="ceeee-107">Debe asignar una licencia a estas cuentas de usuario, ya sea de forma individual o dinámica a través de la pertenencia a grupos.</span><span class="sxs-lookup"><span data-stu-id="ceeee-107">You must assign a license to these user accounts, either individually or dynamically through group membership.</span></span>
>

## <a name="authentication-for-hybrid-identity"></a><span data-ttu-id="ceeee-108">Autenticación para la identidad híbrida</span><span class="sxs-lookup"><span data-stu-id="ceeee-108">Authentication for hybrid identity</span></span>

<span data-ttu-id="ceeee-109">Hay dos tipos de autenticación cuando se usa el modelo de identidad híbrida:</span><span class="sxs-lookup"><span data-stu-id="ceeee-109">There are two types of authentication when using the hybrid identity model:</span></span>

- <span data-ttu-id="ceeee-110">Autenticación administrada</span><span class="sxs-lookup"><span data-stu-id="ceeee-110">Managed authentication</span></span>

  <span data-ttu-id="ceeee-111">Azure AD controla el proceso de autenticación mediante el uso de una versión de la contraseña de hash almacenada de forma local o envía las credenciales a un agente de software local para que lo autentique el AD DS local.</span><span class="sxs-lookup"><span data-stu-id="ceeee-111">Azure AD handles the authentication process by using a locally stored hashed version of the password or sends the credentials to an on-premises software agent to be authenticated by the on-premises AD DS.</span></span>

- <span data-ttu-id="ceeee-112">Autenticación federada</span><span class="sxs-lookup"><span data-stu-id="ceeee-112">Federated authentication</span></span>

  <span data-ttu-id="ceeee-113">Azure AD redirige al equipo cliente que solicita la autenticación para ponerse en contacto con otro proveedor de identidades.</span><span class="sxs-lookup"><span data-stu-id="ceeee-113">Azure AD redirects the client computer requesting authentication to contact another identity provider.</span></span>

### <a name="managed-authentication"></a><span data-ttu-id="ceeee-114">Autenticación administrada</span><span class="sxs-lookup"><span data-stu-id="ceeee-114">Managed authentication</span></span>

<span data-ttu-id="ceeee-115">Hay dos tipos de autenticación administrada:</span><span class="sxs-lookup"><span data-stu-id="ceeee-115">There are two types of managed authentication:</span></span>

- <span data-ttu-id="ceeee-116">Sincronización de hash de contraseña (PHS)</span><span class="sxs-lookup"><span data-stu-id="ceeee-116">Password hash synchronization (PHS)</span></span>

  <span data-ttu-id="ceeee-117">Azure AD realiza la autenticación en sí.</span><span class="sxs-lookup"><span data-stu-id="ceeee-117">Azure AD performs the authentication itself.</span></span>

- <span data-ttu-id="ceeee-118">Autenticación de paso a través (PTA)</span><span class="sxs-lookup"><span data-stu-id="ceeee-118">Pass-through authentication (PTA)</span></span>

  <span data-ttu-id="ceeee-119">Azure AD tiene AD DS realizar la autenticación.</span><span class="sxs-lookup"><span data-stu-id="ceeee-119">Azure AD has AD DS perform the authentication.</span></span>


#### <a name="password-hash-synchronization"></a><span data-ttu-id="ceeee-120">Sincronización de hash de contraseñas</span><span class="sxs-lookup"><span data-stu-id="ceeee-120">Password hash synchronization</span></span>

<span data-ttu-id="ceeee-121">Con la sincronización de hash de contraseña (PHS), se sincronizan las cuentas de usuario de AD DS con Office 365 y se administran los usuarios de forma local.</span><span class="sxs-lookup"><span data-stu-id="ceeee-121">With password hash synchronization (PHS), you synchronize your AD DS user accounts with Office 365 and manage your users on-premises.</span></span> <span data-ttu-id="ceeee-122">Los valores hash de las contraseñas de usuario se sincronizan de AD DS con Azure AD para que los usuarios tengan la misma contraseña local y en la nube.</span><span class="sxs-lookup"><span data-stu-id="ceeee-122">Hashes of user passwords are synchronized from your AD DS to Azure AD so that the users have the same password on-premises and in the cloud.</span></span> <span data-ttu-id="ceeee-123">Esta es la forma más sencilla de habilitar la autenticación para las identidades de AD DS en Azure AD.</span><span class="sxs-lookup"><span data-stu-id="ceeee-123">This is the simplest way to enable authentication for AD DS identities in Azure AD.</span></span> 

![](./media/plan-for-directory-synchronization/phs-authentication.png)

<span data-ttu-id="ceeee-124">Cuando se cambian o se restablecen las contraseñas locales, los nuevos hash de contraseña se sincronizan con Azure AD para que los usuarios siempre puedan usar la misma contraseña para los recursos de la nube y los recursos locales.</span><span class="sxs-lookup"><span data-stu-id="ceeee-124">When passwords are changed or reset on-premises, the new password hashes are synchronized to Azure AD so that your users can always use the same password for cloud resources and on-premises resources.</span></span> <span data-ttu-id="ceeee-125">Las contraseñas de usuario nunca se envían a Azure AD o se almacenan en Azure AD en texto no cifrado.</span><span class="sxs-lookup"><span data-stu-id="ceeee-125">The user passwords are never sent to Azure AD or stored in Azure AD in clear text.</span></span> <span data-ttu-id="ceeee-126">Algunas características Premium de Azure AD, como la protección de identidad, requieren PHS independientemente del método de autenticación que se seleccione.</span><span class="sxs-lookup"><span data-stu-id="ceeee-126">Some premium features of Azure AD, such as Identity Protection, require PHS regardless of which authentication method is selected.</span></span>
  
<span data-ttu-id="ceeee-127">Vea [elegir PHS](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="ceeee-127">See [choosing PHS](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) to learn more.</span></span>
  
#### <a name="pass-through-authentication"></a><span data-ttu-id="ceeee-128">Autenticación de paso a través</span><span class="sxs-lookup"><span data-stu-id="ceeee-128">Pass-through authentication</span></span>

<span data-ttu-id="ceeee-129">La autenticación de paso a través (PTA) proporciona una validación de contraseña sencilla para los servicios de autenticación de Azure AD mediante un agente de software que se ejecuta en uno o varios servidores locales para validar a los usuarios directamente con AD DS.</span><span class="sxs-lookup"><span data-stu-id="ceeee-129">Pass-through authentication (PTA) provides a simple password validation for Azure AD authentication services using a software agent running on one or more on-premises servers to validate the users directly with your AD DS.</span></span> <span data-ttu-id="ceeee-130">Con la autenticación de paso a través (PTA), se sincronizan las cuentas de usuario de AD DS con Office 365 y se administran los usuarios de forma local.</span><span class="sxs-lookup"><span data-stu-id="ceeee-130">With pass-through authentication (PTA), you synchronize AD DS user accounts with Office 365 and manage your users on-premises.</span></span> 

![](./media/plan-for-directory-synchronization/pta-authentication.png)

<span data-ttu-id="ceeee-131">PTA permite que los usuarios inicien sesión en recursos y aplicaciones locales y de Office 365 con su cuenta local y su contraseña.</span><span class="sxs-lookup"><span data-stu-id="ceeee-131">PTA allows your users to sign in to both on-premises and Office 365 resources and applications using their on-premises account and password.</span></span> <span data-ttu-id="ceeee-132">Esta configuración valida las contraseñas de los usuarios directamente en AD DS local sin almacenar los hash de contraseña en Azure AD.</span><span class="sxs-lookup"><span data-stu-id="ceeee-132">This configuration validates users passwords directly against your on-premises AD DS without storing password hashes in Azure AD.</span></span> 

<span data-ttu-id="ceeee-133">PTA también es para las organizaciones con requisitos de seguridad para aplicar inmediatamente Estados de cuentas de usuario locales, directivas de contraseñas y horas de inicio de sesión.</span><span class="sxs-lookup"><span data-stu-id="ceeee-133">PTA is also for organizations with a security requirement to immediately enforce on-premises user account states, password policies, and logon hours.</span></span> 
  
<span data-ttu-id="ceeee-134">Vea [elegir PTA](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="ceeee-134">See [choosing PTA](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) to learn more.</span></span>
  
### <a name="federated-authentication"></a><span data-ttu-id="ceeee-135">Autenticación federada</span><span class="sxs-lookup"><span data-stu-id="ceeee-135">Federated authentication</span></span>

<span data-ttu-id="ceeee-136">La autenticación federada es principalmente para grandes empresas con requisitos de autenticación más complejos.</span><span class="sxs-lookup"><span data-stu-id="ceeee-136">Federated authentication is primarily for large enterprise organizations with more complex authentication requirements.</span></span> <span data-ttu-id="ceeee-137">Las identidades de AD DS se sincronizan con Office 365 y las cuentas de usuario se administran de forma local.</span><span class="sxs-lookup"><span data-stu-id="ceeee-137">AD DS identities are synchronized with Office 365 and users accounts are managed on-premises.</span></span> <span data-ttu-id="ceeee-138">Con la autenticación federada, los usuarios tienen la misma contraseña local y en la nube, y no tienen que iniciar sesión de nuevo para usar Office 365.</span><span class="sxs-lookup"><span data-stu-id="ceeee-138">With federated authentication, users have the same password on-premises and in the cloud and they do not have to sign in again to use Office 365.</span></span> 

<span data-ttu-id="ceeee-139">La autenticación federada puede admitir requisitos de autenticación adicionales, como la autenticación basada en tarjeta inteligente o una autenticación multifactor de terceros y suele ser necesario cuando las organizaciones tienen un requisito de autenticación que no compatible de forma nativa con Azure AD.</span><span class="sxs-lookup"><span data-stu-id="ceeee-139">Federated authentication can support additional authentication requirements, such as smartcard-based authentication or a third-party multi-factor authentication and is typically required when organizations have an authentication requirement not natively supported by Azure AD.</span></span>
 
<span data-ttu-id="ceeee-140">Consulte [elegir la autenticación federada](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="ceeee-140">See [choosing federated authentication](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) to learn more.</span></span>
  
#### <a name="third-party-authentication-and-identity-providers"></a><span data-ttu-id="ceeee-141">Proveedores de autenticación e identidad de terceros</span><span class="sxs-lookup"><span data-stu-id="ceeee-141">Third-party authentication and identity providers</span></span>

<span data-ttu-id="ceeee-142">Los objetos de directorio local se pueden sincronizar con Office 365 y el acceso a recursos de la nube es administrado principalmente por un proveedor de identidades de terceros (IdP).</span><span class="sxs-lookup"><span data-stu-id="ceeee-142">On-premises directory objects may be synchronized to Office 365 and cloud resource access is primarily managed by a third-party identity provider (IdP).</span></span> <span data-ttu-id="ceeee-143">Si su organización usa una solución de Federación de terceros, puede configurar el inicio de sesión con esa solución para Office 365, siempre que la solución de Federación de terceros sea compatible con Azure AD.</span><span class="sxs-lookup"><span data-stu-id="ceeee-143">If your organization uses a third-party federation solution, you can configure sign-on with that solution for Office 365 provided that the third-party federation solution is compatible with Azure AD.</span></span>
  
<span data-ttu-id="ceeee-144">Consulte [compatibilidad de Federación de Azure ad](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="ceeee-144">See [Azure AD federation compatibility](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility) to learn more.</span></span>
  
## <a name="ad-ds-cleanup"></a><span data-ttu-id="ceeee-145">Limpieza de AD DS</span><span class="sxs-lookup"><span data-stu-id="ceeee-145">AD DS Cleanup</span></span>

<span data-ttu-id="ceeee-146">Para ayudar a garantizar una transición sin problemas a Office 365 mediante la sincronización, debe preparar el bosque de AD DS antes de comenzar con la implementación de sincronización de directorios de Office 365.</span><span class="sxs-lookup"><span data-stu-id="ceeee-146">To help ensure a seamless transition to Office 365 by using synchronization, you must prepare your AD DS forest before you begin your Office 365 directory synchronization deployment.</span></span>
  
<span data-ttu-id="ceeee-147">Al [configurar la sincronización de directorios en Office 365](set-up-directory-synchronization.md), uno de los pasos es [Descargar y ejecutar la herramienta IdFix](install-and-run-idfix.md).</span><span class="sxs-lookup"><span data-stu-id="ceeee-147">When you [set up directory synchronization in Office 365](set-up-directory-synchronization.md), one of the steps is to [download and run the IdFix tool](install-and-run-idfix.md).</span></span> <span data-ttu-id="ceeee-148">Puede usar la herramienta IdFix para ayudar con la [limpieza de directorios](prepare-directory-attributes-for-synch-with-idfix.md).</span><span class="sxs-lookup"><span data-stu-id="ceeee-148">You can use the IdFix tool to help with [directory cleanup](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  
<span data-ttu-id="ceeee-149">La limpieza de directorios debe centrarse en las siguientes tareas:</span><span class="sxs-lookup"><span data-stu-id="ceeee-149">Your directory cleanup should focus on the following tasks:</span></span>

- <span data-ttu-id="ceeee-150">Quitar los atributos **proxyAddress** y **userPrincipalName** duplicados.</span><span class="sxs-lookup"><span data-stu-id="ceeee-150">Remove duplicate **proxyAddress** and **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="ceeee-151">Actualice los atributos **userPrincipalName** no válidos o en blanco con atributos **userPrincipalName** válidos.</span><span class="sxs-lookup"><span data-stu-id="ceeee-151">Update blank and invalid **userPrincipalName** attributes with valid **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="ceeee-152">Quitar los caracteres dudosos y no válidos de **givenName**, apellidos ( **SN** ), **samAccountName**, **displayName**, **mail**, **proxyAddresses**, **mailNickname**y **userPrincipalName** sus.</span><span class="sxs-lookup"><span data-stu-id="ceeee-152">Remove invalid and questionable characters in the **givenName**, surname ( **sn** ), **sAMAccountName**, **displayName**, **mail**, **proxyAddresses**, **mailNickname**, and **userPrincipalName** attributes.</span></span> <span data-ttu-id="ceeee-153">Para obtener información detallada sobre la preparación de atributos, consulte [lista de atributos que se sincronizan mediante la herramienta de sincronización de Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span><span class="sxs-lookup"><span data-stu-id="ceeee-153">For details about preparing attributes, see [List of attributes that are synced by the Azure Active Directory Sync Tool](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

    > [!NOTE]
    > <span data-ttu-id="ceeee-154">Estos son los mismos atributos que Azure AD Connect sincroniza.</span><span class="sxs-lookup"><span data-stu-id="ceeee-154">These are the same attributes that Azure AD Connect synchronizes.</span></span> 
  
## <a name="multi-forest-deployment-considerations"></a><span data-ttu-id="ceeee-155">Consideraciones sobre la implementación de varios bosques</span><span class="sxs-lookup"><span data-stu-id="ceeee-155">Multi-forest deployment considerations</span></span>

<span data-ttu-id="ceeee-156">Para varios bosques y opciones de SSO, use la [instalación personalizada de Azure ad Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span><span class="sxs-lookup"><span data-stu-id="ceeee-156">For multiple forests and SSO options, use [Custom Installation of Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span></span>
  
<span data-ttu-id="ceeee-157">Si su organización tiene varios bosques para la autenticación (bosques de inicio de sesión), recomendamos encarecidamente lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="ceeee-157">If your organization has multiple forests for authentication (logon forests), we highly recommend the following:</span></span>
  
- <span data-ttu-id="ceeee-158">**Considere la posibilidad de consolidar los bosques.**</span><span class="sxs-lookup"><span data-stu-id="ceeee-158">**Consider consolidating your forests.**</span></span> <span data-ttu-id="ceeee-159">En general, es necesario más carga para mantener varios bosques.</span><span class="sxs-lookup"><span data-stu-id="ceeee-159">In general, there's more overhead required to maintain multiple forests.</span></span> <span data-ttu-id="ceeee-160">A menos que la organización tenga restricciones de seguridad que determinen la necesidad de bosques independientes, considere la posibilidad de simplificar el entorno local.</span><span class="sxs-lookup"><span data-stu-id="ceeee-160">Unless your organization has security constraints that dictate the need for separate forests, consider simplifying your on-premises environment.</span></span>
- <span data-ttu-id="ceeee-161">**Use solamente en el bosque de inicio de sesión principal.**</span><span class="sxs-lookup"><span data-stu-id="ceeee-161">**Use only in your primary logon forest.**</span></span> <span data-ttu-id="ceeee-162">Considere la posibilidad de implementar Office 365 solo en el bosque de inicio de sesión principal para su lanzamiento inicial de Office 365.</span><span class="sxs-lookup"><span data-stu-id="ceeee-162">Consider deploying Office 365 only in your primary logon forest for your initial rollout of Office 365.</span></span> 

<span data-ttu-id="ceeee-163">Si no puede consolidar su implementación de AD DS de varios bosques o está usando otros servicios de directorio para administrar las identidades, es posible que pueda sincronizarlas con la ayuda de Microsoft o de un asociado.</span><span class="sxs-lookup"><span data-stu-id="ceeee-163">If you can't consolidate your multi-forest AD DS deployment or are using other directory services to manage identities, you may be able to synchronize these with the help of Microsoft or a partner.</span></span>
  
<span data-ttu-id="ceeee-164">Para obtener más información [, consulte sincronización de directorios de varios bosques con escenario de inicio de sesión único](https://go.microsoft.com/fwlink/p/?LinkId=525321) .</span><span class="sxs-lookup"><span data-stu-id="ceeee-164">See [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=525321) for more information.</span></span>
  
## <a name="features-that-are-dependent-on-directory-synchronization"></a><span data-ttu-id="ceeee-165">Características que dependen de la sincronización de directorios</span><span class="sxs-lookup"><span data-stu-id="ceeee-165">Features that are dependent on directory synchronization</span></span>
  
<span data-ttu-id="ceeee-166">La sincronización de directorios es necesaria para las siguientes características y funciones:</span><span class="sxs-lookup"><span data-stu-id="ceeee-166">Directory synchronization is required for the following features and functionality:</span></span>
  
- <span data-ttu-id="ceeee-167">Inicio de sesión único de línea directa de Azure AD (SSO)</span><span class="sxs-lookup"><span data-stu-id="ceeee-167">Azure AD Seamless Single Sign-On (SSO)</span></span>
- <span data-ttu-id="ceeee-168">Coexistencia de Skype</span><span class="sxs-lookup"><span data-stu-id="ceeee-168">Skype coexistence</span></span>
- <span data-ttu-id="ceeee-169">Implementación híbrida de Exchange, que incluye:</span><span class="sxs-lookup"><span data-stu-id="ceeee-169">Exchange hybrid deployment, including:</span></span>
  - <span data-ttu-id="ceeee-170">Lista global de direcciones (GAL) totalmente compartida entre el entorno de Exchange local y Office 365.</span><span class="sxs-lookup"><span data-stu-id="ceeee-170">Fully shared global address list (GAL) between your on-premises Exchange environment and Office 365.</span></span>
  - <span data-ttu-id="ceeee-171">Sincronización de información de GAL desde varios sistemas de correo.</span><span class="sxs-lookup"><span data-stu-id="ceeee-171">Synchronizing GAL information from different mail systems.</span></span>
  - <span data-ttu-id="ceeee-172">La capacidad de agregar usuarios y quitar usuarios de las ofertas de servicio de Office 365.</span><span class="sxs-lookup"><span data-stu-id="ceeee-172">The ability to add users to and remove users from Office 365 service offerings.</span></span> <span data-ttu-id="ceeee-173">Esto requiere lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="ceeee-173">This requires the following:</span></span>
  - <span data-ttu-id="ceeee-174">La sincronización bidireccional debe configurarse durante la configuración de la sincronización de directorios.</span><span class="sxs-lookup"><span data-stu-id="ceeee-174">Two-way synchronization must be configured during directory synchronization setup.</span></span> <span data-ttu-id="ceeee-175">De forma predeterminada, las herramientas de sincronización de directorios escriben información de directorio solo en la nube.</span><span class="sxs-lookup"><span data-stu-id="ceeee-175">By default, directory synchronization tools write directory information only to the cloud.</span></span> <span data-ttu-id="ceeee-176">Cuando se configura la sincronización bidireccional, se habilita la funcionalidad de reescritura de modo que se copie un número limitado de atributos de objeto de la nube y, a continuación, se escriban de nuevo en el AD DS local.</span><span class="sxs-lookup"><span data-stu-id="ceeee-176">When you configure two-way synchronization, you enable write-back functionality so that a limited number of object attributes are copied from the cloud, and then written them back to your local AD DS.</span></span> <span data-ttu-id="ceeee-177">La escritura diferida también se conoce como modo híbrido de Exchange.</span><span class="sxs-lookup"><span data-stu-id="ceeee-177">Write-back is also referred to as Exchange hybrid mode.</span></span> 
  - <span data-ttu-id="ceeee-178">Una implementación híbrida de Exchange local</span><span class="sxs-lookup"><span data-stu-id="ceeee-178">An on-premises Exchange hybrid deployment</span></span>
  - <span data-ttu-id="ceeee-179">La capacidad de mover algunos buzones de usuario a Office 365 al mismo tiempo que se conservan otros buzones de usuario locales.</span><span class="sxs-lookup"><span data-stu-id="ceeee-179">The ability to move some user mailboxes to Office 365 while keeping other user mailboxes on-premises.</span></span>
  - <span data-ttu-id="ceeee-180">Los remitentes seguros y los remitentes bloqueados locales se replican en Office 365.</span><span class="sxs-lookup"><span data-stu-id="ceeee-180">Safe senders and blocked senders on-premises are replicated to Office 365.</span></span>
  - <span data-ttu-id="ceeee-181">Función de delegación básica y envío en nombre de otra persona.</span><span class="sxs-lookup"><span data-stu-id="ceeee-181">Basic delegation and send-on-behalf-of email functionality.</span></span>
  - <span data-ttu-id="ceeee-182">Tiene una solución de autenticación multifactor o de tarjeta inteligente local integrada.</span><span class="sxs-lookup"><span data-stu-id="ceeee-182">You have an integrated on-premises smart card or multi-factor authentication solution.</span></span>
- <span data-ttu-id="ceeee-183">Sincronización de fotos, miniaturas, salas de conferencias y grupos de seguridad</span><span class="sxs-lookup"><span data-stu-id="ceeee-183">Synchronization of photos, thumbnails, conference rooms, and security groups</span></span>

## <a name="next-step"></a><span data-ttu-id="ceeee-184">Paso siguiente</span><span class="sxs-lookup"><span data-stu-id="ceeee-184">Next step</span></span>

<span data-ttu-id="ceeee-185">Cuando esté listo para implementar la identidad híbrida, vea [preparar el aprovisionamiento de usuarios](prepare-for-directory-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="ceeee-185">When you are ready to deploy hybrid identity, see [prepare to provision users](prepare-for-directory-synchronization.md).</span></span>
  

