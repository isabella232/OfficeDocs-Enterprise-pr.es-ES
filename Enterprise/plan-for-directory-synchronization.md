---
title: Identidad híbrida y sincronización de directorios para Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.date: 06/09/2020
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MOE150
- MET150
ms.assetid: d3577c90-dda5-45ca-afb0-370d2889b10f
description: Describe la sincronización de directorios con Microsoft 365, la limpieza de los servicios de dominio de Active Directory y la herramienta Azure Active Directory Connect.
ms.openlocfilehash: ef7af68a65e4799e7bffbe6edba4f2b237a4d8b4
ms.sourcegitcommit: ff1d21fe5eb8eba7a65d250aa37aadc8f503a10a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2020
ms.locfileid: "44698967"
---
# <a name="hybrid-identity-and-directory-synchronization-for-microsoft-365"></a><span data-ttu-id="e494a-103">Identidad híbrida y sincronización de directorios para Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="e494a-103">Hybrid identity and directory synchronization for Microsoft 365</span></span>

<span data-ttu-id="e494a-104">*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="e494a-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="e494a-105">En función de las necesidades de negocio y los requisitos técnicos, el modelo de identidad híbrida y la sincronización de directorios son las opciones más comunes para los clientes empresariales que están adoptando Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="e494a-105">Depending on your business needs and technical requirements, the hybrid identity model and directory synchronization is the most common choice for enterprise customers who are adopting Microsoft 365.</span></span> <span data-ttu-id="e494a-106">La sincronización de directorios permite administrar las identidades de los servicios de dominio de Active Directory (AD DS) y todas las actualizaciones de las cuentas de usuario, los grupos y los contactos se sincronizan con el inquilino de Azure Active Directory (Azure AD) de la suscripción a Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="e494a-106">Directory synchronization allows you to manage identities in your Active Directory Domain Services (AD DS) and all updates to user accounts, groups, and contacts are synchronized to the Azure Active Directory (Azure AD) tenant of your Microsoft 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="e494a-107">Cuando las cuentas de usuario de AD DS se sincronizan por primera vez, no se les asigna automáticamente una licencia de Microsoft 365 y no pueden acceder a los servicios de Microsoft 365, como el correo electrónico.</span><span class="sxs-lookup"><span data-stu-id="e494a-107">When AD DS user accounts are synchronized for the first time, they are not automatically assigned an Microsoft 365 license and cannot access Microsoft 365 services, such as email.</span></span> <span data-ttu-id="e494a-108">Primero debe asignarles una ubicación de uso.</span><span class="sxs-lookup"><span data-stu-id="e494a-108">You must first assign them a usage location.</span></span> <span data-ttu-id="e494a-109">A continuación, asigne una licencia a estas cuentas de usuario, ya sea de forma individual o dinámica a través de la pertenencia a grupos.</span><span class="sxs-lookup"><span data-stu-id="e494a-109">Then, assign a license to these user accounts, either individually or dynamically through group membership.</span></span>
>

## <a name="authentication-for-hybrid-identity"></a><span data-ttu-id="e494a-110">Autenticación para la identidad híbrida</span><span class="sxs-lookup"><span data-stu-id="e494a-110">Authentication for hybrid identity</span></span>

<span data-ttu-id="e494a-111">Hay dos tipos de autenticación cuando se usa el modelo de identidad híbrida:</span><span class="sxs-lookup"><span data-stu-id="e494a-111">There are two types of authentication when using the hybrid identity model:</span></span>

- <span data-ttu-id="e494a-112">Autenticación administrada</span><span class="sxs-lookup"><span data-stu-id="e494a-112">Managed authentication</span></span>

  <span data-ttu-id="e494a-113">Azure AD administra el proceso de autenticación mediante el uso de una versión hash de la contraseña almacenada de forma local o envía las credenciales a un agente de software local para que lo autentique el AD DS local.</span><span class="sxs-lookup"><span data-stu-id="e494a-113">Azure AD handles the authentication process by using a locally-stored hashed version of the password or sends the credentials to an on-premises software agent to be authenticated by the on-premises AD DS.</span></span>

- <span data-ttu-id="e494a-114">Autenticación federada</span><span class="sxs-lookup"><span data-stu-id="e494a-114">Federated authentication</span></span>

  <span data-ttu-id="e494a-115">Azure AD redirige al equipo cliente que solicita la autenticación a otro proveedor de identidad.</span><span class="sxs-lookup"><span data-stu-id="e494a-115">Azure AD redirects the client computer requesting authentication to another identity provider.</span></span>

### <a name="managed-authentication"></a><span data-ttu-id="e494a-116">Autenticación administrada</span><span class="sxs-lookup"><span data-stu-id="e494a-116">Managed authentication</span></span>

<span data-ttu-id="e494a-117">Hay dos tipos de autenticación administrada:</span><span class="sxs-lookup"><span data-stu-id="e494a-117">There are two types of managed authentication:</span></span>

- <span data-ttu-id="e494a-118">Sincronización de hash de contraseña (PHS)</span><span class="sxs-lookup"><span data-stu-id="e494a-118">Password hash synchronization (PHS)</span></span>

  <span data-ttu-id="e494a-119">Azure AD realiza la autenticación en sí.</span><span class="sxs-lookup"><span data-stu-id="e494a-119">Azure AD performs the authentication itself.</span></span>

- <span data-ttu-id="e494a-120">Autenticación de paso a través (PTA)</span><span class="sxs-lookup"><span data-stu-id="e494a-120">Pass-through authentication (PTA)</span></span>

  <span data-ttu-id="e494a-121">Azure AD tiene AD DS realizar la autenticación.</span><span class="sxs-lookup"><span data-stu-id="e494a-121">Azure AD has AD DS perform the authentication.</span></span>


#### <a name="password-hash-synchronization-phs"></a><span data-ttu-id="e494a-122">Sincronización de hash de contraseña (PHS)</span><span class="sxs-lookup"><span data-stu-id="e494a-122">Password hash synchronization (PHS)</span></span>

<span data-ttu-id="e494a-123">Con PHS, se sincronizan las cuentas de usuario de AD DS con Microsoft 365 y se administran los usuarios de forma local.</span><span class="sxs-lookup"><span data-stu-id="e494a-123">With PHS, you synchronize your AD DS user accounts with Microsoft 365 and manage your users on-premises.</span></span> <span data-ttu-id="e494a-124">Los valores hash de las contraseñas de usuario se sincronizan de AD DS con Azure AD para que los usuarios tengan la misma contraseña local y en la nube.</span><span class="sxs-lookup"><span data-stu-id="e494a-124">Hashes of user passwords are synchronized from your AD DS to Azure AD so that the users have the same password on-premises and in the cloud.</span></span> <span data-ttu-id="e494a-125">Esta es la forma más sencilla de habilitar la autenticación para las identidades de AD DS en Azure AD.</span><span class="sxs-lookup"><span data-stu-id="e494a-125">This is the simplest way to enable authentication for AD DS identities in Azure AD.</span></span> 

![Sincronización de hash de contraseña (PHS)](./media/plan-for-directory-synchronization/phs-authentication.png)

<span data-ttu-id="e494a-127">Cuando se cambian o se restablecen las contraseñas locales, los nuevos hash de contraseña se sincronizan con Azure AD para que los usuarios siempre puedan usar la misma contraseña para los recursos de la nube y los recursos locales.</span><span class="sxs-lookup"><span data-stu-id="e494a-127">When passwords are changed or reset on-premises, the new password hashes are synchronized to Azure AD so that your users can always use the same password for cloud resources and on-premises resources.</span></span> <span data-ttu-id="e494a-128">Las contraseñas de usuario nunca se envían a Azure AD o se almacenan en Azure AD en texto no cifrado.</span><span class="sxs-lookup"><span data-stu-id="e494a-128">The user passwords are never sent to Azure AD or stored in Azure AD in clear text.</span></span> <span data-ttu-id="e494a-129">Algunas características Premium de Azure AD, como la protección de identidad, requieren PHS independientemente del método de autenticación que se seleccione.</span><span class="sxs-lookup"><span data-stu-id="e494a-129">Some premium features of Azure AD, such as Identity Protection, require PHS regardless of which authentication method is selected.</span></span>
  
<span data-ttu-id="e494a-130">Vea [elegir el método de autenticación correcto](https://docs.microsoft.com/azure/active-directory/hybrid/choose-ad-authn) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="e494a-130">See [choosing the right authentication method](https://docs.microsoft.com/azure/active-directory/hybrid/choose-ad-authn) to learn more.</span></span>
  
#### <a name="pass-through-authentication-pta"></a><span data-ttu-id="e494a-131">Autenticación de paso a través (PTA)</span><span class="sxs-lookup"><span data-stu-id="e494a-131">Pass-through authentication (PTA)</span></span>

<span data-ttu-id="e494a-132">PTA proporciona una validación de contraseña simple para los servicios de autenticación de Azure AD mediante un agente de software que se ejecuta en uno o varios servidores locales para validar a los usuarios directamente con AD DS.</span><span class="sxs-lookup"><span data-stu-id="e494a-132">PTA provides a simple password validation for Azure AD authentication services using a software agent running on one or more on-premises servers to validate the users directly with your AD DS.</span></span> <span data-ttu-id="e494a-133">Con PTA, se sincronizan las cuentas de usuario de AD DS con Microsoft 365 y se administran los usuarios de forma local.</span><span class="sxs-lookup"><span data-stu-id="e494a-133">With PTA, you synchronize AD DS user accounts with Microsoft 365 and manage your users on-premises.</span></span> 

![Autenticación de paso a través (PTA)](./media/plan-for-directory-synchronization/pta-authentication.png)

<span data-ttu-id="e494a-135">PTA permite que los usuarios inicien sesión en las aplicaciones y los recursos locales y de Microsoft 365 usando su cuenta local y su contraseña.</span><span class="sxs-lookup"><span data-stu-id="e494a-135">PTA allows your users to sign in to both on-premises and Microsoft 365 resources and applications using their on-premises account and password.</span></span> <span data-ttu-id="e494a-136">Esta configuración valida las contraseñas de los usuarios directamente en AD DS local sin almacenar los hash de contraseña en Azure AD.</span><span class="sxs-lookup"><span data-stu-id="e494a-136">This configuration validates users passwords directly against your on-premises AD DS without storing password hashes in Azure AD.</span></span> 

<span data-ttu-id="e494a-137">PTA también es para las organizaciones con requisitos de seguridad para aplicar inmediatamente Estados de cuentas de usuario locales, directivas de contraseñas y horas de inicio de sesión.</span><span class="sxs-lookup"><span data-stu-id="e494a-137">PTA is also for organizations with a security requirement to immediately enforce on-premises user account states, password policies, and logon hours.</span></span> 
  
<span data-ttu-id="e494a-138">Vea [elegir el método de autenticación correcto](https://docs.microsoft.com/azure/active-directory/hybrid/choose-ad-authn) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="e494a-138">See [choosing the right authentication method](https://docs.microsoft.com/azure/active-directory/hybrid/choose-ad-authn) to learn more.</span></span>
  
### <a name="federated-authentication"></a><span data-ttu-id="e494a-139">Autenticación federada</span><span class="sxs-lookup"><span data-stu-id="e494a-139">Federated authentication</span></span>

<span data-ttu-id="e494a-140">La autenticación federada es principalmente para grandes empresas con requisitos de autenticación más complejos.</span><span class="sxs-lookup"><span data-stu-id="e494a-140">Federated authentication is primarily for large enterprise organizations with more complex authentication requirements.</span></span> <span data-ttu-id="e494a-141">Las identidades de AD DS se sincronizan con Microsoft 365 y las cuentas de usuario se administran de forma local.</span><span class="sxs-lookup"><span data-stu-id="e494a-141">AD DS identities are synchronized with Microsoft 365 and users accounts are managed on-premises.</span></span> <span data-ttu-id="e494a-142">Con la autenticación federada, los usuarios tienen la misma contraseña local y en la nube, y no tienen que iniciar sesión de nuevo para usar Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="e494a-142">With federated authentication, users have the same password on-premises and in the cloud and they do not have to sign in again to use Microsoft 365.</span></span> 

<span data-ttu-id="e494a-143">La autenticación federada puede admitir requisitos de autenticación adicionales, como la autenticación basada en tarjeta inteligente o una autenticación multifactor de terceros y suele ser necesario cuando las organizaciones tienen un requisito de autenticación que Azure AD no admite de forma nativa.</span><span class="sxs-lookup"><span data-stu-id="e494a-143">Federated authentication can support additional authentication requirements, such as smartcard-based authentication or a third-party multi-factor authentication and is typically required when organizations have an authentication requirement not natively supported by Azure AD.</span></span>
 
<span data-ttu-id="e494a-144">Vea [elegir el método de autenticación correcto](https://docs.microsoft.com/azure/active-directory/hybrid/choose-ad-authn) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="e494a-144">See [choosing the right authentication method](https://docs.microsoft.com/azure/active-directory/hybrid/choose-ad-authn) to learn more.</span></span>
  
#### <a name="third-party-authentication-and-identity-providers"></a><span data-ttu-id="e494a-145">Proveedores de autenticación e identidad de terceros</span><span class="sxs-lookup"><span data-stu-id="e494a-145">Third-party authentication and identity providers</span></span>

<span data-ttu-id="e494a-146">Los objetos de directorio local se pueden sincronizar con Microsoft 365 y el acceso a recursos de la nube es administrado principalmente por un proveedor de identidades de terceros (IdP).</span><span class="sxs-lookup"><span data-stu-id="e494a-146">On-premises directory objects may be synchronized to Microsoft 365 and cloud resource access is primarily managed by a third-party identity provider (IdP).</span></span> <span data-ttu-id="e494a-147">Si su organización usa una solución de Federación de terceros, puede configurar el inicio de sesión con esa solución para Microsoft 365, siempre que la solución de Federación de terceros sea compatible con Azure AD.</span><span class="sxs-lookup"><span data-stu-id="e494a-147">If your organization uses a third-party federation solution, you can configure sign-on with that solution for Microsoft 365 provided that the third-party federation solution is compatible with Azure AD.</span></span>
  
<span data-ttu-id="e494a-148">Consulte la [lista de compatibilidad de Federación de Azure ad](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="e494a-148">See the [Azure AD federation compatibility list](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility) to learn more.</span></span>
  
## <a name="ad-ds-cleanup"></a><span data-ttu-id="e494a-149">Limpieza de AD DS</span><span class="sxs-lookup"><span data-stu-id="e494a-149">AD DS Cleanup</span></span>

<span data-ttu-id="e494a-150">Para ayudar a garantizar una transición sin problemas a Microsoft 365 mediante la sincronización, debe preparar el bosque de AD DS antes de comenzar con la implementación de sincronización de directorios de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="e494a-150">To help ensure a seamless transition to Microsoft 365 by using synchronization, you must prepare your AD DS forest before you begin your Microsoft 365 directory synchronization deployment.</span></span>
  
<span data-ttu-id="e494a-151">Al [configurar la sincronización de directorios](set-up-directory-synchronization.md), uno de los pasos es [Descargar y ejecutar la herramienta IdFix](install-and-run-idfix.md).</span><span class="sxs-lookup"><span data-stu-id="e494a-151">When you [set up directory synchronization](set-up-directory-synchronization.md), one of the steps is to [download and run the IdFix tool](install-and-run-idfix.md).</span></span> <span data-ttu-id="e494a-152">Puede usar la herramienta IdFix para ayudar con la [limpieza de directorios](prepare-directory-attributes-for-synch-with-idfix.md).</span><span class="sxs-lookup"><span data-stu-id="e494a-152">You can use the IdFix tool to help with [directory cleanup](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  
<span data-ttu-id="e494a-153">La limpieza de directorios debe centrarse en las siguientes tareas:</span><span class="sxs-lookup"><span data-stu-id="e494a-153">Your directory cleanup should focus on the following tasks:</span></span>

- <span data-ttu-id="e494a-154">Quitar los atributos **proxyAddress** y **userPrincipalName** duplicados.</span><span class="sxs-lookup"><span data-stu-id="e494a-154">Remove duplicate **proxyAddress** and **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="e494a-155">Actualice los atributos **userPrincipalName** no válidos o en blanco con atributos **userPrincipalName** válidos.</span><span class="sxs-lookup"><span data-stu-id="e494a-155">Update blank and invalid **userPrincipalName** attributes with valid **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="e494a-156">Quite los caracteres dudosos y no válidos de los atributos **givenName**, apellidos ( **SN** ), **samAccountName**, **displayName**, **mail**, **proxyAddresses**, **mailNickname**y **userPrincipalName** .</span><span class="sxs-lookup"><span data-stu-id="e494a-156">Remove invalid and questionable characters in the **givenName**, surname ( **sn** ), **sAMAccountName**, **displayName**, **mail**, **proxyAddresses**, **mailNickname**, and **userPrincipalName** attributes.</span></span> <span data-ttu-id="e494a-157">Para obtener información detallada sobre la preparación de atributos, consulte [lista de atributos que se sincronizan mediante la herramienta de sincronización de Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span><span class="sxs-lookup"><span data-stu-id="e494a-157">For details about preparing attributes, see [List of attributes that are synced by the Azure Active Directory Sync Tool](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

    > [!NOTE]
    > <span data-ttu-id="e494a-158">Estos son los mismos atributos que Azure AD Connect sincroniza.</span><span class="sxs-lookup"><span data-stu-id="e494a-158">These are the same attributes that Azure AD Connect synchronizes.</span></span> 
  
## <a name="multi-forest-deployment-considerations"></a><span data-ttu-id="e494a-159">Consideraciones sobre la implementación de varios bosques</span><span class="sxs-lookup"><span data-stu-id="e494a-159">Multi-forest deployment considerations</span></span>

<span data-ttu-id="e494a-160">Para varios bosques y opciones de SSO, use una [instalación personalizada de Azure ad Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span><span class="sxs-lookup"><span data-stu-id="e494a-160">For multiple forests and SSO options, use a [Custom Installation of Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span></span>
  
<span data-ttu-id="e494a-161">Si su organización tiene varios bosques para la autenticación (bosques de inicio de sesión), recomendamos encarecidamente lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="e494a-161">If your organization has multiple forests for authentication (logon forests), we highly recommend the following:</span></span>
  
- <span data-ttu-id="e494a-162">**Considere la posibilidad de consolidar los bosques.**</span><span class="sxs-lookup"><span data-stu-id="e494a-162">**Consider consolidating your forests.**</span></span> <span data-ttu-id="e494a-163">En general, es necesario más carga para mantener varios bosques.</span><span class="sxs-lookup"><span data-stu-id="e494a-163">In general, there's more overhead required to maintain multiple forests.</span></span> <span data-ttu-id="e494a-164">A menos que la organización tenga restricciones de seguridad que determinen la necesidad de bosques independientes, considere la posibilidad de simplificar el entorno local.</span><span class="sxs-lookup"><span data-stu-id="e494a-164">Unless your organization has security constraints that dictate the need for separate forests, consider simplifying your on-premises environment.</span></span>
- <span data-ttu-id="e494a-165">**Use solamente en el bosque de inicio de sesión principal.**</span><span class="sxs-lookup"><span data-stu-id="e494a-165">**Use only in your primary logon forest.**</span></span> <span data-ttu-id="e494a-166">Considere la posibilidad de implementar Microsoft 365 solo en el bosque de inicio de sesión principal para la implementación inicial de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="e494a-166">Consider deploying Microsoft 365 only in your primary logon forest for your initial rollout of Microsoft 365.</span></span> 

<span data-ttu-id="e494a-167">Si no puede consolidar su implementación de AD DS de varios bosques o está usando otros servicios de directorio para administrar las identidades, es posible que pueda sincronizarlas con la ayuda de Microsoft o de un asociado.</span><span class="sxs-lookup"><span data-stu-id="e494a-167">If you can't consolidate your multi-forest AD DS deployment or are using other directory services to manage identities, you may be able to synchronize these with the help of Microsoft or a partner.</span></span>
  
<span data-ttu-id="e494a-168">Consulte [topologías para Azure ad Connect](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-topologies) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="e494a-168">See [Topologies for Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-topologies) for more information.</span></span>
  
## <a name="features-that-are-dependent-on-directory-synchronization"></a><span data-ttu-id="e494a-169">Características que dependen de la sincronización de directorios</span><span class="sxs-lookup"><span data-stu-id="e494a-169">Features that are dependent on directory synchronization</span></span>
  
<span data-ttu-id="e494a-170">La sincronización de directorios es necesaria para las siguientes características y funciones:</span><span class="sxs-lookup"><span data-stu-id="e494a-170">Directory synchronization is required for the following features and functionality:</span></span>
  
- <span data-ttu-id="e494a-171">Inicio de sesión único de línea directa de Azure AD (SSO)</span><span class="sxs-lookup"><span data-stu-id="e494a-171">Azure AD Seamless Single Sign-On (SSO)</span></span>
- <span data-ttu-id="e494a-172">Coexistencia de Skype</span><span class="sxs-lookup"><span data-stu-id="e494a-172">Skype coexistence</span></span>
- <span data-ttu-id="e494a-173">Implementación híbrida de Exchange, que incluye:</span><span class="sxs-lookup"><span data-stu-id="e494a-173">Exchange hybrid deployment, including:</span></span>
  - <span data-ttu-id="e494a-174">Lista global de direcciones (GAL) totalmente compartida entre el entorno de Exchange local y Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="e494a-174">Fully shared global address list (GAL) between your on-premises Exchange environment and Microsoft 365.</span></span>
  - <span data-ttu-id="e494a-175">Sincronización de información de GAL desde varios sistemas de correo.</span><span class="sxs-lookup"><span data-stu-id="e494a-175">Synchronizing GAL information from different mail systems.</span></span>
  - <span data-ttu-id="e494a-176">La capacidad de agregar usuarios y quitar usuarios de las ofertas de servicio de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="e494a-176">The ability to add users to and remove users from Microsoft 365 service offerings.</span></span> <span data-ttu-id="e494a-177">Esto requiere lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="e494a-177">This requires the following:</span></span>
  - <span data-ttu-id="e494a-178">La sincronización bidireccional debe configurarse durante la configuración de la sincronización de directorios.</span><span class="sxs-lookup"><span data-stu-id="e494a-178">Two-way synchronization must be configured during directory synchronization setup.</span></span> <span data-ttu-id="e494a-179">De forma predeterminada, las herramientas de sincronización de directorios escriben información de directorio solo en la nube.</span><span class="sxs-lookup"><span data-stu-id="e494a-179">By default, directory synchronization tools write directory information only to the cloud.</span></span> <span data-ttu-id="e494a-180">Cuando se configura la sincronización bidireccional, se habilita la funcionalidad de reescritura de modo que se copie un número limitado de atributos de objeto de la nube y, a continuación, se escriban de nuevo en el AD DS local.</span><span class="sxs-lookup"><span data-stu-id="e494a-180">When you configure two-way synchronization, you enable write-back functionality so that a limited number of object attributes are copied from the cloud, and then written them back to your local AD DS.</span></span> <span data-ttu-id="e494a-181">La escritura diferida también se conoce como modo híbrido de Exchange.</span><span class="sxs-lookup"><span data-stu-id="e494a-181">Write-back is also referred to as Exchange hybrid mode.</span></span> 
  - <span data-ttu-id="e494a-182">Una implementación híbrida de Exchange local</span><span class="sxs-lookup"><span data-stu-id="e494a-182">An on-premises Exchange hybrid deployment</span></span>
  - <span data-ttu-id="e494a-183">La capacidad de mover algunos buzones de usuario a Microsoft 365 mientras se mantienen otros buzones de usuario locales.</span><span class="sxs-lookup"><span data-stu-id="e494a-183">The ability to move some user mailboxes to Microsoft 365 while keeping other user mailboxes on-premises.</span></span>
  - <span data-ttu-id="e494a-184">Los remitentes seguros y los remitentes bloqueados locales se replican en Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="e494a-184">Safe senders and blocked senders on-premises are replicated to Microsoft 365.</span></span>
  - <span data-ttu-id="e494a-185">Función de delegación básica y envío en nombre de otra persona.</span><span class="sxs-lookup"><span data-stu-id="e494a-185">Basic delegation and send-on-behalf-of email functionality.</span></span>
  - <span data-ttu-id="e494a-186">Tiene una solución de autenticación multifactor o de tarjeta inteligente local integrada.</span><span class="sxs-lookup"><span data-stu-id="e494a-186">You have an integrated on-premises smart card or multi-factor authentication solution.</span></span>
- <span data-ttu-id="e494a-187">Sincronización de fotos, miniaturas, salas de conferencias y grupos de seguridad</span><span class="sxs-lookup"><span data-stu-id="e494a-187">Synchronization of photos, thumbnails, conference rooms, and security groups</span></span>

## <a name="next-step"></a><span data-ttu-id="e494a-188">Paso siguiente</span><span class="sxs-lookup"><span data-stu-id="e494a-188">Next step</span></span>

<span data-ttu-id="e494a-189">Cuando esté listo para implementar la identidad híbrida, vea [preparar el aprovisionamiento de usuarios](prepare-for-directory-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="e494a-189">When you are ready to deploy hybrid identity, see [prepare to provision users](prepare-for-directory-synchronization.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e494a-190">Vea también</span><span class="sxs-lookup"><span data-stu-id="e494a-190">See also</span></span>

[<span data-ttu-id="e494a-191">Información general de Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="e494a-191">Microsoft 365 Enterprise overview</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)

