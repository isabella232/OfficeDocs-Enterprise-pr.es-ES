---
title: Modelos de identidad de Office 365 y Azure Active Directory
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.date: 05/20/2019
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-identity-device-management
- M365-security-compliance
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 06a189e7-5ec6-4af2-94bf-a22ea225a7a9
description: Obtenga información sobre cómo se administra la identidad del usuario en Office 365.
ms.openlocfilehash: a44f3073895ef1c8172a6ab5637f50cd9c6ac186
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843811"
---
# <a name="office-365-identity-models-and-azure-active-directory"></a><span data-ttu-id="758cb-103">Modelos de identidad de Office 365 y Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="758cb-103">Office 365 identity models and Azure Active Directory</span></span>

<span data-ttu-id="758cb-104">*Este artículo se aplica tanto a Office 365 Enterprise como a Microsoft 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="758cb-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="758cb-105">Office 365 usa Azure Active Directory (Azure AD), una identidad de usuario basada en la nube y un servicio de autenticación que se incluye con su suscripción a Office 365, para administrar las identidades y la autenticación de Office 365.</span><span class="sxs-lookup"><span data-stu-id="758cb-105">Office 365 uses Azure Active Directory (Azure AD), a cloud-based user identity and authentication service that is included with your Office 365 subscription, to manage identities and authentication for Office 365.</span></span> <span data-ttu-id="758cb-106">La configuración correcta de la infraestructura de identidades es fundamental para administrar el acceso de usuarios y los permisos de Office 365 para la organización.</span><span class="sxs-lookup"><span data-stu-id="758cb-106">Getting your identity infrastructure configured correctly is vital to managing Office 365 user access and permissions for your organization.</span></span>

<span data-ttu-id="758cb-107">Antes de empezar, vea este vídeo para obtener una introducción a los modelos de identidad y la autenticación de Office 365 y Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="758cb-107">Before you begin, watch this video for an overview of identity models and authentication for both Office 365 and Microsoft 365.</span></span>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2Pjwu]

<span data-ttu-id="758cb-108">La primera opción de planeación es el modelo de identidad de Office 365.</span><span class="sxs-lookup"><span data-stu-id="758cb-108">Your first planning choice is the Office 365 identity model.</span></span>

## <a name="office-365-identity-models"></a><span data-ttu-id="758cb-109">Modelos de identidad de Office 365</span><span class="sxs-lookup"><span data-stu-id="758cb-109">Office 365 identity models</span></span>

<span data-ttu-id="758cb-110">Para planear las cuentas de usuario, primero debe conocer los dos modelos de identidad de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="758cb-110">To plan for user accounts, you first need to understand the two identity models in Microsoft 365.</span></span> <span data-ttu-id="758cb-111">Puede mantener las identidades de su organización solo en la nube o puede mantener sus identidades locales de servicios de dominio de Active Directory (AD DS) y usarlas para la autenticación cuando los usuarios obtienen acceso a los servicios en la nube de 365 de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="758cb-111">You can maintain your organization's identities only in the cloud, or you can maintain your on-premises Active Directory Domain Services (AD DS) identities and use them for authentication when users access Microsoft 365 cloud services.</span></span>  

<span data-ttu-id="758cb-112">Estos son los dos tipos de identidad y sus mejores ventajas y ventajas.</span><span class="sxs-lookup"><span data-stu-id="758cb-112">Here are the two types of identity and their best fit and benefits.</span></span>

|||
|:-------|:-----|:-----|
|  | <span data-ttu-id="758cb-113">**Identidad solo de nube**</span><span class="sxs-lookup"><span data-stu-id="758cb-113">**Cloud-only identity**</span></span> | <span data-ttu-id="758cb-114">**Identidad híbrida**</span><span class="sxs-lookup"><span data-stu-id="758cb-114">**Hybrid identity**</span></span> |
| <span data-ttu-id="758cb-115">**Definición**</span><span class="sxs-lookup"><span data-stu-id="758cb-115">**Definition**</span></span> | <span data-ttu-id="758cb-116">La cuenta de usuario solo existe en el inquilino de Azure Active Directory (Azure AD) para su suscripción a Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="758cb-116">User account only exists in the Azure Active Directory (Azure AD) tenant for your Microsoft 365 subscription.</span></span> | <span data-ttu-id="758cb-117">La cuenta de usuario existe en AD DS y una copia también se encuentra en el inquilino de Azure AD para su suscripción a Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="758cb-117">User account exists in AD DS and a copy is also in the Azure AD tenant for your Microsoft 365 subscription.</span></span> <span data-ttu-id="758cb-118">La cuenta de usuario en Azure AD también puede incluir una versión hash de la contraseña de la cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="758cb-118">The user account in Azure AD might also include a hashed version of the user account password.</span></span> |
| <span data-ttu-id="758cb-119">**Cómo autentica Microsoft 365 las credenciales de usuario**</span><span class="sxs-lookup"><span data-stu-id="758cb-119">**How Microsoft 365 authenticates user credentials**</span></span> | <span data-ttu-id="758cb-120">El inquilino de Azure AD para su suscripción a Microsoft 365 realiza la autenticación con la cuenta de identidad de nube.</span><span class="sxs-lookup"><span data-stu-id="758cb-120">The Azure AD tenant for your Microsoft 365 subscription performs the authentication with the cloud identity account.</span></span> | <span data-ttu-id="758cb-121">El inquilino de Azure AD para su suscripción de Microsoft 365 administra el proceso de autenticación o redirige al usuario a otro proveedor de identidades.</span><span class="sxs-lookup"><span data-stu-id="758cb-121">The Azure AD tenant for your Microsoft 365 subscription either handles the authentication process or redirects the user to another identity provider.</span></span> |
| <span data-ttu-id="758cb-122">**Ideal para**</span><span class="sxs-lookup"><span data-stu-id="758cb-122">**Best for**</span></span> | <span data-ttu-id="758cb-123">Organizaciones que no tienen ni necesitan un AD DS local.</span><span class="sxs-lookup"><span data-stu-id="758cb-123">Organizations that do not have or need an on-premises AD DS.</span></span> | <span data-ttu-id="758cb-124">Organizaciones que usan AD DS u otro proveedor de identidades.</span><span class="sxs-lookup"><span data-stu-id="758cb-124">Organizations using AD DS or another identity provider.</span></span> |
| <span data-ttu-id="758cb-125">**Mayor beneficio**</span><span class="sxs-lookup"><span data-stu-id="758cb-125">**Greatest benefit**</span></span> | <span data-ttu-id="758cb-126">Fácil de usar.</span><span class="sxs-lookup"><span data-stu-id="758cb-126">Simple to use.</span></span> <span data-ttu-id="758cb-127">No se necesitan servidores o herramientas de directorio adicionales.</span><span class="sxs-lookup"><span data-stu-id="758cb-127">No extra directory tools or servers required.</span></span> | <span data-ttu-id="758cb-128">Los usuarios pueden usar las mismas credenciales al obtener acceso a los recursos locales o basados en la nube.</span><span class="sxs-lookup"><span data-stu-id="758cb-128">Users can use the same credentials when accessing on-premises or cloud-based resources.</span></span> |
||||

## <a name="cloud-only-identity"></a><span data-ttu-id="758cb-129">Identidad solo de nube</span><span class="sxs-lookup"><span data-stu-id="758cb-129">Cloud-only identity</span></span>

<span data-ttu-id="758cb-130">Una identidad de solo nube usa cuentas de usuario que solo existen en Azure AD.</span><span class="sxs-lookup"><span data-stu-id="758cb-130">A cloud-only identity uses user accounts that exist only in Azure AD.</span></span> <span data-ttu-id="758cb-131">La identidad de nube suele usarse en organizaciones pequeñas que no tienen servidores locales o que no usan AD DS para administrar identidades locales.</span><span class="sxs-lookup"><span data-stu-id="758cb-131">Cloud identity is typically used by small organizations that do not have on-premises servers or do not use AD DS to manage local identities.</span></span> 

<span data-ttu-id="758cb-132">Estos son los componentes básicos de la identidad solo de la nube.</span><span class="sxs-lookup"><span data-stu-id="758cb-132">Here are the basic components of cloud-only identity.</span></span>
 
![Componentes básicos de identidad solo en la nube](./media/about-office-365-identity/cloud-only-identity.png)

<span data-ttu-id="758cb-134">Los usuarios locales y remotos (en línea) usan sus cuentas de usuario y contraseñas de Azure AD para acceder a los servicios en la nube de Office 365.</span><span class="sxs-lookup"><span data-stu-id="758cb-134">Both on-premises and remote (online) users use their Azure AD user accounts and passwords to access Office 365 cloud services.</span></span> <span data-ttu-id="758cb-135">Azure AD autentica las credenciales de usuario en función de sus cuentas de usuario y contraseñas almacenadas.</span><span class="sxs-lookup"><span data-stu-id="758cb-135">Azure AD authenticates user credentials based on its stored user accounts and passwords.</span></span>

### <a name="administration"></a><span data-ttu-id="758cb-136">Administración</span><span class="sxs-lookup"><span data-stu-id="758cb-136">Administration</span></span>
<span data-ttu-id="758cb-137">Como las cuentas de usuario se almacenan solo en Azure AD, puede administrar las identidades de nube con herramientas como el [centro de administración de 365 de Microsoft](https://admin.microsoft.com) y Windows PowerShell con el módulo Azure Active Directory PowerShell para Graph.</span><span class="sxs-lookup"><span data-stu-id="758cb-137">Because user accounts are only stored in Azure AD, you manage cloud identities with tools such as the [Microsoft 365 admin center](https://admin.microsoft.com) and Windows PowerShell with the Azure Active Directory PowerShell for Graph module.</span></span> 

## <a name="hybrid-identity"></a><span data-ttu-id="758cb-138">Identidad híbrida</span><span class="sxs-lookup"><span data-stu-id="758cb-138">Hybrid identity</span></span>

<span data-ttu-id="758cb-139">La identidad híbrida usa cuentas que se originan en un AD DS local y tienen una copia en el inquilino de Azure AD de una suscripción a Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="758cb-139">Hybrid identity uses accounts that originate in an on-premises AD DS and have a copy in the Azure AD tenant of a Microsoft 365 subscription.</span></span> <span data-ttu-id="758cb-140">Sin embargo, la mayoría de los cambios solo fluyen en un sentido.</span><span class="sxs-lookup"><span data-stu-id="758cb-140">However, most changes only flow one way.</span></span> <span data-ttu-id="758cb-141">Los cambios que realice en las cuentas de usuario de AD DS se sincronizan con su copia en Azure AD.</span><span class="sxs-lookup"><span data-stu-id="758cb-141">Changes that you make to AD DS user accounts are synchronized to their copy in Azure AD.</span></span> <span data-ttu-id="758cb-142">Pero los cambios realizados en cuentas basadas en la nube en Azure AD, como nuevas cuentas de usuario, no se sincronizan con AD DS.</span><span class="sxs-lookup"><span data-stu-id="758cb-142">But changes made to cloud-based accounts in Azure AD, such as new user accounts, are not synchronized with AD DS.</span></span>

<span data-ttu-id="758cb-143">Azure AD Connect proporciona la sincronización de cuentas en curso.</span><span class="sxs-lookup"><span data-stu-id="758cb-143">Azure AD Connect provides the ongoing account synchronization.</span></span> <span data-ttu-id="758cb-144">Se ejecuta en un servidor local, comprueba los cambios en AD DS y reenvía dichos cambios a Azure AD.</span><span class="sxs-lookup"><span data-stu-id="758cb-144">It runs on an on-premises server, checks for changes in the AD DS, and forwards those changes to Azure AD.</span></span> <span data-ttu-id="758cb-145">Azure AD Connect permite filtrar las cuentas que se van a sincronizar y si se debe sincronizar una versión hash de las contraseñas de usuario, conocidas como sincronización de hash de contraseña (PHS).</span><span class="sxs-lookup"><span data-stu-id="758cb-145">Azure AD Connect provides the ability to filter which accounts are synchronized and whether to synchronize a hashed version of user passwords, known as password hash synchronization (PHS).</span></span>

<span data-ttu-id="758cb-146">Al implementar la identidad híbrida, su AD DS local es el origen de autoridad para la información de la cuenta.</span><span class="sxs-lookup"><span data-stu-id="758cb-146">When you implement hybrid identity, your on-premises AD DS is the authoritative source for account information.</span></span> <span data-ttu-id="758cb-147">Esto significa que las tareas de administración se realizan principalmente en el entorno local, que luego se sincronizan con Azure AD.</span><span class="sxs-lookup"><span data-stu-id="758cb-147">This means that you perform administration tasks mostly on-premises, which are then synchronized to Azure AD.</span></span> 

<span data-ttu-id="758cb-148">Estos son los componentes de la identidad híbrida.</span><span class="sxs-lookup"><span data-stu-id="758cb-148">Here are the components of hybrid identity.</span></span>

![Componentes de la identidad híbrida](./media/about-office-365-identity/hybrid-identity.png)

<span data-ttu-id="758cb-150">El inquilino de Azure AD tiene una copia de las cuentas de AD DS.</span><span class="sxs-lookup"><span data-stu-id="758cb-150">The Azure AD tenant has a copy of the AD DS accounts.</span></span> <span data-ttu-id="758cb-151">En esta configuración, los usuarios locales y remotos que tienen acceso a los servicios en la nube de Microsoft 365 se autentican con Azure AD.</span><span class="sxs-lookup"><span data-stu-id="758cb-151">In this configuration, both on-premises and remote users accessing Microsoft 365 cloud services authenticate against Azure AD.</span></span>

>[!Note]
><span data-ttu-id="758cb-152">Siempre tiene que usar Azure AD Connect para sincronizar las cuentas de usuario para la identidad híbrida.</span><span class="sxs-lookup"><span data-stu-id="758cb-152">You always need to use Azure AD Connect to synchronize user accounts for hybrid identity.</span></span> <span data-ttu-id="758cb-153">Necesita las cuentas de usuario sincronizadas en Azure AD para realizar la asignación de licencias y la administración de grupos, configurar permisos y otras tareas administrativas que implican cuentas de usuario.</span><span class="sxs-lookup"><span data-stu-id="758cb-153">You need the synchronized user accounts in Azure AD to perform license assignment and group management, configure permissions, and other administrative tasks that involve user accounts.</span></span>
>

### <a name="administration"></a><span data-ttu-id="758cb-154">Administración</span><span class="sxs-lookup"><span data-stu-id="758cb-154">Administration</span></span>

<span data-ttu-id="758cb-155">Debido a que las cuentas de usuario originales y autorizadas se almacenan en AD DS local, administra las identidades con las mismas herramientas que AD DS, como la herramienta usuarios y equipos de Active Directory.</span><span class="sxs-lookup"><span data-stu-id="758cb-155">Because the original and authoritative user accounts are stored in the on-premises AD DS, you manage your identities with the same tools as AD DS, such as the Active Directory Users and Computers tool.</span></span> 

<span data-ttu-id="758cb-156">No usa el centro de administración de Microsoft 365 o Windows PowerShell para administrar cuentas de usuario sincronizadas en Azure AD.</span><span class="sxs-lookup"><span data-stu-id="758cb-156">You don’t use the Microsoft 365 admin center or Windows PowerShell to manage synchronized user accounts in Azure AD.</span></span>

## <a name="next-step"></a><span data-ttu-id="758cb-157">Paso siguiente</span><span class="sxs-lookup"><span data-stu-id="758cb-157">Next step</span></span>

<span data-ttu-id="758cb-158">Si necesita el modelo de identidad solo de la nube, consulte [identidades solo de nube](cloud-only-identities.md).</span><span class="sxs-lookup"><span data-stu-id="758cb-158">If you need the cloud-only identity model, see [Cloud-only identities](cloud-only-identities.md).</span></span>

<span data-ttu-id="758cb-159">Si necesita el modelo de identidad híbrida, consulte [sincronización de directorios](plan-for-directory-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="758cb-159">If you need the hybrid identity model, see [directory synchronization](plan-for-directory-synchronization.md).</span></span>
  

## <a name="video-training"></a><span data-ttu-id="758cb-160">Vídeo de aprendizaje</span><span class="sxs-lookup"><span data-stu-id="758cb-160">Video training</span></span>

<span data-ttu-id="758cb-161">Consulte el curso de vídeo [Office 365: administrar identidades con Azure ad Connect](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx)y ofrecido por LinkedIn Learning.</span><span class="sxs-lookup"><span data-stu-id="758cb-161">See the video course [Office 365: Manage Identities Using Azure AD Connect](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx), brought to you by LinkedIn Learning.</span></span>

## <a name="see-also"></a><span data-ttu-id="758cb-162">Vea también</span><span class="sxs-lookup"><span data-stu-id="758cb-162">See also</span></span>

[<span data-ttu-id="758cb-163">Información general de Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="758cb-163">Microsoft 365 Enterprise overview</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
