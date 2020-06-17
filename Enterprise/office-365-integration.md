---
title: Integración de Microsoft 365 con entornos locales
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 10/08/2019
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
search.appverid:
- MET150
- LYN150
- SPS150
- MOE150
- MED150
ms.assetid: 263faf8d-aa21-428b-aed3-2021837a4b65
description: Obtenga información sobre cómo integrar Microsoft 365 con los servicios de directorio existentes.
ms.openlocfilehash: 456e3e73451a07750d707e2fca52df9214c2dfaa
ms.sourcegitcommit: c112869b3ecc0f574b7054ee1edc8c57132f8237
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2020
ms.locfileid: "44736038"
---
# <a name="microsoft-365-integration-with-on-premises-environments"></a><span data-ttu-id="eb835-103">Integración de Microsoft 365 con entornos locales</span><span class="sxs-lookup"><span data-stu-id="eb835-103">Microsoft 365 integration with on-premises environments</span></span>

<span data-ttu-id="eb835-104">*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="eb835-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="eb835-105">Puede integrar Microsoft 365 con los servicios de directorio existentes y con una instalación local de Exchange Server, Skype empresarial Server 2015 o SharePoint Server.</span><span class="sxs-lookup"><span data-stu-id="eb835-105">You can integrate Microsoft 365 with your existing directory services and with an on-premises installation of Exchange Server, Skype for Business Server 2015, or SharePoint Server.</span></span>
  
 - <span data-ttu-id="eb835-106">Cuando se integra con los servicios de directorio, puede sincronizar y administrar cuentas de usuario para ambos entornos.</span><span class="sxs-lookup"><span data-stu-id="eb835-106">When you integrate with directory services, you can synchronize and manage user accounts for both environments.</span></span> <span data-ttu-id="eb835-107">También puede Agregar la sincronización de hash de contraseña o el inicio de sesión único (SSO) para que los usuarios puedan iniciar sesión en ambos entornos con sus credenciales locales.</span><span class="sxs-lookup"><span data-stu-id="eb835-107">You can also add password hash synchronization or single sign-on (SSO) so users can log on to both environments with their on-premises credentials.</span></span>
 - <span data-ttu-id="eb835-108">Cuando se integra con productos de servidor local, se crea un entorno híbrido.</span><span class="sxs-lookup"><span data-stu-id="eb835-108">When you integrate with on-premises server products, you create a hybrid environment.</span></span> <span data-ttu-id="eb835-109">Un entorno híbrido puede ayudarle a migrar usuarios o información a Microsoft 365, o puede seguir teniendo algunos usuarios o información local y algunos en la nube.</span><span class="sxs-lookup"><span data-stu-id="eb835-109">A hybrid environment can help as you migrate users or information to Microsoft 365, or you can continue to have some users or some information on-premises and some in the cloud.</span></span> <span data-ttu-id="eb835-110">Para obtener más información acerca de los entornos híbridos, consulte [información general sobre la nube híbrida](https://docs.microsoft.com/Office365/Enterprise/hybrid-cloud-overview).</span><span class="sxs-lookup"><span data-stu-id="eb835-110">For more information about hybrid environments, see [Hybrid cloud overview](https://docs.microsoft.com/Office365/Enterprise/hybrid-cloud-overview).</span></span>

<span data-ttu-id="eb835-111">También puede usar los asesores de Azure Active Directory (Azure AD) para obtener instrucciones de configuración personalizadas (debe haber iniciado sesión en Microsoft 365):</span><span class="sxs-lookup"><span data-stu-id="eb835-111">You can also use the Azure Active Directory (Azure AD) advisors for customized setup guidance (you must be signed in to Microsoft 365):</span></span>

- [<span data-ttu-id="eb835-112">Sincronizar usuarios del directorio de su organización</span><span class="sxs-lookup"><span data-stu-id="eb835-112">Sync users from your org's directory</span></span>](https://aka.ms/aadconnectpwsync)
- [<span data-ttu-id="eb835-113">Asesor de implementación de AD FS</span><span class="sxs-lookup"><span data-stu-id="eb835-113">AD FS deployment advisor</span></span>](https://aka.ms/adfsguidance)
- [<span data-ttu-id="eb835-114">Guía de configuración de Azure AD</span><span class="sxs-lookup"><span data-stu-id="eb835-114">Azure AD setup guide</span></span>](https://aka.ms/aadpguidance)
   
## <a name="before-you-begin"></a><span data-ttu-id="eb835-115">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="eb835-115">Before you begin</span></span>

<span data-ttu-id="eb835-116">Antes de integrar Microsoft 365 y un entorno local, también debe asistir a la [planeación de red y el ajuste del rendimiento](network-planning-and-performance.md).</span><span class="sxs-lookup"><span data-stu-id="eb835-116">Before you integrate Microsoft 365 and an on-premises environment, you also need to attend to [network planning and performance tuning](network-planning-and-performance.md).</span></span> <span data-ttu-id="eb835-117">También le interesará conocer los modelos de [identidad](about-office-365-identity.md)disponibles.</span><span class="sxs-lookup"><span data-stu-id="eb835-117">You will also want to understand the available [identity models](about-office-365-identity.md).</span></span> 

<span data-ttu-id="eb835-118">Vea [dónde administrar las cuentas de microsoft 365](manage-office-365-accounts.md) para obtener una lista de las herramientas que puede usar para administrar usuarios y cuentas de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="eb835-118">See [where to manage Microsoft 365 accounts](manage-office-365-accounts.md) for a list of tools you can use to manage Microsoft 365 users and accounts.</span></span> 
  
## <a name="integrate-microsoft-365-with-directory-services"></a><span data-ttu-id="eb835-119">Integración de Microsoft 365 con los servicios de directorio</span><span class="sxs-lookup"><span data-stu-id="eb835-119">Integrate Microsoft 365 with directory services</span></span>
<span data-ttu-id="eb835-120">Si tiene cuentas de usuario existentes en un directorio local, no desea volver a crear todas esas cuentas en Microsoft 365 y arriesgar la introducción de diferencias o errores entre los entornos.</span><span class="sxs-lookup"><span data-stu-id="eb835-120">If you have existing user accounts in an on-premises directory, you don't want to re-create all of those accounts in Microsoft 365 and risk introducing differences or errors between the environments.</span></span> <span data-ttu-id="eb835-121">La sincronización de directorios le ayuda a reflejar esas cuentas entre su entorno local y en línea.</span><span class="sxs-lookup"><span data-stu-id="eb835-121">Directory synchronization helps you mirror those accounts between your online and on-premises environments.</span></span> <span data-ttu-id="eb835-122">Con la sincronización de directorios, los usuarios no tienen que recordar nueva información para cada entorno y no es necesario crear o actualizar cuentas dos veces.</span><span class="sxs-lookup"><span data-stu-id="eb835-122">With directory synchronization, your users don't have to remember new information for each environment, and you don't have to create or update accounts twice.</span></span> <span data-ttu-id="eb835-123">Tendrá que [preparar el directorio local para la](prepare-for-directory-synchronization.md) sincronización de directorios, puede hacerlo manualmente o usar la [herramienta idfix](install-and-run-idfix.md) (la herramienta Idfix solo funciona con servicios de dominio de Active Directory [AD DS]).</span><span class="sxs-lookup"><span data-stu-id="eb835-123">You will need to [prepare your on-premises directory](prepare-for-directory-synchronization.md) for directory synchronization, you can do this manually or use the [IdFix tool](install-and-run-idfix.md) (IdFix tool only works with Active Directory Domain Services [AD DS]).</span></span> 
  
![Usar la sincronización de directorios para mantener sincronizada la información de cuenta de usuario local y en línea](media/a64af0d0-9be6-46b1-8727-277e683abf5e.png)
  
<span data-ttu-id="eb835-125">Si desea que los usuarios puedan iniciar sesión en Microsoft 365 con sus credenciales locales, también puede configurar el SSO.</span><span class="sxs-lookup"><span data-stu-id="eb835-125">If you want users to be able to log on to Microsoft 365 with their on-premises credentials, you can also configure SSO.</span></span> <span data-ttu-id="eb835-126">Con SSO, Microsoft 365 está configurado para confiar en el entorno local para la autenticación de usuarios.</span><span class="sxs-lookup"><span data-stu-id="eb835-126">With SSO, Microsoft 365 is configured to trust the on-premises environment for user authentication.</span></span>
  
![Con el inicio de sesión único, la misma cuenta está disponible tanto en el entorno local como en el en línea.](media/d76235f2-8a53-405e-b8ef-dfa4cfc208b8.png)
  
<span data-ttu-id="eb835-128">Las distintas técnicas de administración de cuentas de usuario proporcionan distintas experiencias para los usuarios, como se muestra en la siguiente tabla.</span><span class="sxs-lookup"><span data-stu-id="eb835-128">Different user account management techniques provide different experiences for your users, as shown in the following table.</span></span>
 
### <a name="directory-synchronization-with-or-without-password-hash-synchronization-or-pass-through-authentication"></a><span data-ttu-id="eb835-129">Sincronización de directorios con o sin sincronización de hash de contraseña o autenticación de paso a través</span><span class="sxs-lookup"><span data-stu-id="eb835-129">Directory synchronization with or without password hash synchronization or pass-through authentication</span></span>

<span data-ttu-id="eb835-130">Un usuario inicia sesión en su entorno local con su cuenta de usuario (dominio\nombre de usuario).</span><span class="sxs-lookup"><span data-stu-id="eb835-130">A user logs on to their on-premises environment with their user account (domain\username).</span></span> <span data-ttu-id="eb835-131">Cuando vayan a Microsoft 365, deben volver a iniciar sesión con su cuenta profesional o educativa (user@domain.com).</span><span class="sxs-lookup"><span data-stu-id="eb835-131">When they go to Microsoft 365, they must log on again with their work or school account (user@domain.com).</span></span> <span data-ttu-id="eb835-132">El nombre de usuario es el mismo en ambos entornos.</span><span class="sxs-lookup"><span data-stu-id="eb835-132">The user name is the same in both environments.</span></span> <span data-ttu-id="eb835-133">Al agregar la sincronización de hash de contraseña o la autenticación de paso a través, el usuario tiene la misma contraseña para ambos entornos, pero tendrá que volver a proporcionar las credenciales al iniciar sesión en Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="eb835-133">When you add password hash sync or pass-through authentication, the user has the same password for both environments, but will have to provide those credentials again when logging on to Microsoft 365.</span></span> <span data-ttu-id="eb835-134">La sincronización de directorios con sincronización de hash de contraseña es el escenario de sincronización de directorios que se usa con más frecuencia.</span><span class="sxs-lookup"><span data-stu-id="eb835-134">Directory synchronization with password hash sync is the most commonly used directory sync scenario.</span></span>

<span data-ttu-id="eb835-135">Para configurar la sincronización de directorios, use Azure Active Directory Connect.</span><span class="sxs-lookup"><span data-stu-id="eb835-135">To set up directory synchronization, use Azure Active Directory Connect.</span></span> <span data-ttu-id="eb835-136">Para obtener instrucciones, consulte [configurar la sincronización de directorios para Microsoft 365](set-up-directory-synchronization.md)y [Azure ad Connect con la configuración rápida](https://go.microsoft.com/fwlink/p/?LinkId=698537).</span><span class="sxs-lookup"><span data-stu-id="eb835-136">For instructions, read [Set up directory synchronization for Microsoft 365](set-up-directory-synchronization.md), and [Azure AD Connect with express settings](https://go.microsoft.com/fwlink/p/?LinkId=698537).</span></span>

<span data-ttu-id="eb835-137">Obtenga más información sobre la [preparación para la sincronización de directorios en Microsoft 365](prepare-for-directory-synchronization.md) e [integración de los identificadores locales con Azure Active Directory](https://go.microsoft.com/fwlink/?LinkId=518101).</span><span class="sxs-lookup"><span data-stu-id="eb835-137">Learn more about [preparing for directory synchronization to Microsoft 365](prepare-for-directory-synchronization.md) and [integrating your on-premises identifies with Azure Active Directory](https://go.microsoft.com/fwlink/?LinkId=518101).</span></span>

### <a name="directory-synchronization-with-sso"></a><span data-ttu-id="eb835-138">Sincronización de directorios con SSO</span><span class="sxs-lookup"><span data-stu-id="eb835-138">Directory synchronization with SSO</span></span>

<span data-ttu-id="eb835-139">Un usuario inicia sesión en su entorno local con su cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="eb835-139">A user logs on to their on-premises environment with their user account.</span></span> <span data-ttu-id="eb835-140">Cuando van a Microsoft 365, inician sesión automáticamente o inician sesión con las mismas credenciales que usan para su entorno local (dominio\nombre de usuario).</span><span class="sxs-lookup"><span data-stu-id="eb835-140">When they go to Microsoft 365, they are either logged on automatically, or they log on using the same credentials they use for their on-premises environment (domain\username).</span></span>

<span data-ttu-id="eb835-141">Para configurar el SSO, también puede usar Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="eb835-141">To set up SSO you also use Azure AD Connect.</span></span> <span data-ttu-id="eb835-142">Para obtener instrucciones, consulte read [Custom Installation of Azure ad Connect](https://go.microsoft.com/fwlink/p/?LinkID=698430).</span><span class="sxs-lookup"><span data-stu-id="eb835-142">For instructions, read [Custom installation of Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkID=698430).</span></span>

<span data-ttu-id="eb835-143">Obtenga más información sobre [el inicio de sesión único en aplicaciones en Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span><span class="sxs-lookup"><span data-stu-id="eb835-143">Learn more about [single sign-on to applications in Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span></span>

## <a name="azure-ad-connect"></a><span data-ttu-id="eb835-144">Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="eb835-144">Azure AD Connect</span></span>

<span data-ttu-id="eb835-145">Azure AD Connect reemplaza versiones antiguas de herramientas de integración de identidades, como DirSync y sincronización de Azure AD. Para obtener más información, vea [¿Qué es la identidad híbrida con Azure Active Directory?](https://go.microsoft.com/fwlink/p/?LinkId=527969).</span><span class="sxs-lookup"><span data-stu-id="eb835-145">Azure AD Connect replaces older versions of identity integration tools such as DirSync and Azure AD Sync. For more information, see [What is hybrid identity with Azure Active Directory?](https://go.microsoft.com/fwlink/p/?LinkId=527969).</span></span> <span data-ttu-id="eb835-146">Si quiere actualizar desde Azure Active Directory Sync a Azure AD Connect, consulte [las instrucciones de actualización](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span><span class="sxs-lookup"><span data-stu-id="eb835-146">If you want to update from Azure Active Directory Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span> 

<span data-ttu-id="eb835-147">Consulte también [implementar la sincronización de directorios de microsoft 365 en Microsoft Azure](https://go.microsoft.com/fwlink/?LinkId=517887).</span><span class="sxs-lookup"><span data-stu-id="eb835-147">Also see [Deploy Microsoft 365 Directory Synchronization in Microsoft Azure](https://go.microsoft.com/fwlink/?LinkId=517887).</span></span>

## <a name="see-also"></a><span data-ttu-id="eb835-148">Vea también</span><span class="sxs-lookup"><span data-stu-id="eb835-148">See also</span></span>

[<span data-ttu-id="eb835-149">Información general de Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="eb835-149">Microsoft 365 Enterprise overview</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
