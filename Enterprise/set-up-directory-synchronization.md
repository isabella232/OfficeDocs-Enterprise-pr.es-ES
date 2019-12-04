---
title: Configurar la sincronización de directorios en Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/03/2019
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED15
- MBS150
- BCS160
ms.assetid: 1b3b5318-6977-42ed-b5c7-96fa74b08846
description: Obtenga información sobre cómo configurar la sincronización de directorios entre Office 365 y su Active Directory local.
ms.openlocfilehash: 5cd56eb90e6421d530ff0c2b8739bd13be238eae
ms.sourcegitcommit: a9804062071939b7b7e60da5b69f484ce1d34ff8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/04/2019
ms.locfileid: "39814598"
---
# <a name="set-up-directory-synchronization-for-office-365"></a><span data-ttu-id="7bfa0-103">Configurar la sincronización de directorios en Office 365</span><span class="sxs-lookup"><span data-stu-id="7bfa0-103">Set up directory synchronization for Office 365</span></span>

<span data-ttu-id="7bfa0-104">*Este artículo se aplica tanto a Office 365 Enterprise como a Microsoft 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="7bfa0-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="7bfa0-105">Office 365 usa un inquilino de Azure Active Directory (Azure AD) para almacenar y administrar identidades de autenticación y permisos para obtener acceso a los recursos basados en la nube.</span><span class="sxs-lookup"><span data-stu-id="7bfa0-105">Office 365 uses an Azure Active Directory (Azure AD) tenant to store and manage identities for authentication and permissions to access cloud-based resources.</span></span> 

<span data-ttu-id="7bfa0-106">Si tiene un servicio de dominio de Active Directory (AD DS) local, puede sincronizar las cuentas de usuario, los grupos y los contactos de AD DS con el inquilino de Azure AD de su suscripción a Office 365.</span><span class="sxs-lookup"><span data-stu-id="7bfa0-106">If you have an on-premises Active Directory Domain Services (AD DS), you can synchronize your AD DS user accounts, groups, and contacts with the Azure AD tenant of your Office 365 subscription.</span></span> <span data-ttu-id="7bfa0-107">Se trata de una identidad híbrida para Office 365.</span><span class="sxs-lookup"><span data-stu-id="7bfa0-107">This is hybrid identity for Office 365.</span></span> <span data-ttu-id="7bfa0-108">A continuación se muestran sus componentes.</span><span class="sxs-lookup"><span data-stu-id="7bfa0-108">Here are its components.</span></span>

![](./media/about-office-365-identity/hybrid-identity.png)

<span data-ttu-id="7bfa0-109">Azure AD Connect se ejecuta en un servidor local y sincroniza AD DS con el inquilino de Azure AD.</span><span class="sxs-lookup"><span data-stu-id="7bfa0-109">Azure AD Connect runs on an on-premises server and synchronizes your AD DS with the Azure AD tenant.</span></span> <span data-ttu-id="7bfa0-110">Además de la sincronización de directorios, puede especificar estas opciones de autenticación:</span><span class="sxs-lookup"><span data-stu-id="7bfa0-110">Along with directory synchronization, you can also specify these authentication options:</span></span>

- <span data-ttu-id="7bfa0-111">Sincronización de hash de contraseña (PHS)</span><span class="sxs-lookup"><span data-stu-id="7bfa0-111">Password hash synchronization (PHS)</span></span>

  <span data-ttu-id="7bfa0-112">Azure AD realiza la autenticación en sí.</span><span class="sxs-lookup"><span data-stu-id="7bfa0-112">Azure AD performs the authentication itself.</span></span>

- <span data-ttu-id="7bfa0-113">Autenticación de paso a través (PTA)</span><span class="sxs-lookup"><span data-stu-id="7bfa0-113">Pass-through authentication (PTA)</span></span>

  <span data-ttu-id="7bfa0-114">Azure AD tiene AD DS realizar la autenticación.</span><span class="sxs-lookup"><span data-stu-id="7bfa0-114">Azure AD has AD DS perform the authentication.</span></span>

- <span data-ttu-id="7bfa0-115">Autenticación federada</span><span class="sxs-lookup"><span data-stu-id="7bfa0-115">Federated authentication</span></span>

  <span data-ttu-id="7bfa0-116">Azure AD redirige al equipo cliente que solicita la autenticación para ponerse en contacto con otro proveedor de identidades.</span><span class="sxs-lookup"><span data-stu-id="7bfa0-116">Azure AD redirects the client computer requesting authentication to contact another identity provider.</span></span>

<span data-ttu-id="7bfa0-117">Consulte [identidades híbridas](plan-for-directory-synchronization.md) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="7bfa0-117">See [Hybrid identities](plan-for-directory-synchronization.md) for more information.</span></span>
  
## <a name="1-review-prerequisites-for-azure-ad-connect"></a><span data-ttu-id="7bfa0-118">1. Revise los requisitos previos de Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="7bfa0-118">1. Review prerequisites for Azure AD Connect</span></span>

<span data-ttu-id="7bfa0-119">Obtendrá una suscripción gratuita a Azure AD con su suscripción de Office 365.</span><span class="sxs-lookup"><span data-stu-id="7bfa0-119">You get a free Azure AD subscription with your Office 365 subscription.</span></span> <span data-ttu-id="7bfa0-120">Al configurar la sincronización de directorios, se instalará Azure AD Connect en uno de los servidores locales.</span><span class="sxs-lookup"><span data-stu-id="7bfa0-120">When you set up directory synchronization, you will install Azure AD Connect on one of your on-premises servers.</span></span>
  
<span data-ttu-id="7bfa0-121">Para Office 365, necesitará:</span><span class="sxs-lookup"><span data-stu-id="7bfa0-121">For Office 365 you'll need to:</span></span>
  
- <span data-ttu-id="7bfa0-122">Compruebe el dominio local.</span><span class="sxs-lookup"><span data-stu-id="7bfa0-122">Verify your on-premises domain.</span></span> <span data-ttu-id="7bfa0-123">El Asistente de Azure AD Connect le guía a través de esto.</span><span class="sxs-lookup"><span data-stu-id="7bfa0-123">The Azure AD Connect wizard guides you through this.</span></span>
- <span data-ttu-id="7bfa0-124">Obtenga los nombres de usuario y las contraseñas de las cuentas de administrador del inquilino de Office 365 y AD DS.</span><span class="sxs-lookup"><span data-stu-id="7bfa0-124">Obtain the user names and passwords for the admin accounts of your Office 365 tenant and AD DS.</span></span>

<span data-ttu-id="7bfa0-125">Para el servidor local en el que instale Azure AD Connect, necesitará:</span><span class="sxs-lookup"><span data-stu-id="7bfa0-125">For your on-premises server on which you install Azure AD Connect, you'll need:</span></span>
  
|<span data-ttu-id="7bfa0-126">**Sistema operativo del servidor**</span><span class="sxs-lookup"><span data-stu-id="7bfa0-126">**Server OS**</span></span>|<span data-ttu-id="7bfa0-127">**Otros programas de software**</span><span class="sxs-lookup"><span data-stu-id="7bfa0-127">**Other software**</span></span>|
|:-----|:-----|
|<span data-ttu-id="7bfa0-128">Windows Server 2012 R2 y posterior</span><span class="sxs-lookup"><span data-stu-id="7bfa0-128">Windows Server 2012 R2 and later</span></span> | <span data-ttu-id="7bfa0-129">-PowerShell está instalado de forma predeterminada, no se requiere ninguna acción.</span><span class="sxs-lookup"><span data-stu-id="7bfa0-129">- PowerShell is installed by default, no action is required.</span></span>  <br> <span data-ttu-id="7bfa0-130">-Net 4.5.1 y versiones posteriores se ofrecen a través de Windows Update.</span><span class="sxs-lookup"><span data-stu-id="7bfa0-130">- Net 4.5.1 and later releases are offered through Windows Update.</span></span> <span data-ttu-id="7bfa0-131">Asegúrese de que tiene instaladas las últimas actualizaciones de Windows Server en el panel de control.</span><span class="sxs-lookup"><span data-stu-id="7bfa0-131">Make sure you have installed the latest updates to Windows Server in the Control Panel.</span></span> |
|<span data-ttu-id="7bfa0-132">Windows Server 2008 R2 con Service Pack 1 (SP1) \* \* o Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="7bfa0-132">Windows Server 2008 R2 with Service Pack 1 (SP1)\*\* or Windows Server 2012</span></span> | <span data-ttu-id="7bfa0-133">-La versión más reciente de PowerShell está disponible en Windows Management Framework 4,0.</span><span class="sxs-lookup"><span data-stu-id="7bfa0-133">- The latest version of PowerShell is available in Windows Management Framework 4.0.</span></span> <span data-ttu-id="7bfa0-134">Buscarlo en el [centro de descarga de Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="7bfa0-134">Search for it on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br> <span data-ttu-id="7bfa0-135">-.Net 4.5.1 y versiones posteriores están disponibles en el [centro de descarga de Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="7bfa0-135">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |
|<span data-ttu-id="7bfa0-136">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="7bfa0-136">Windows Server 2008</span></span> | <span data-ttu-id="7bfa0-137">-La versión más reciente compatible de PowerShell está disponible en Windows Management Framework 3,0, disponible en el [centro de descarga de Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="7bfa0-137">- The latest supported version of PowerShell is available in Windows Management Framework 3.0, available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br> <span data-ttu-id="7bfa0-138">-.Net 4.5.1 y versiones posteriores están disponibles en el [centro de descarga de Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="7bfa0-138">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |

<span data-ttu-id="7bfa0-139">Consulte requisitos [previos de Azure Active Directory Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites) para obtener información detallada sobre los requisitos de hardware, software, cuentas y permisos, los requisitos de certificados SSL y los límites de objetos para Azure ad Connect.</span><span class="sxs-lookup"><span data-stu-id="7bfa0-139">See [Prerequisites for Azure Active Directory Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites) for the details of hardware, software, account and permissions requirements, SSL certificate requirements, and object limits for Azure AD Connect.</span></span>
  
<span data-ttu-id="7bfa0-140">También puede revisar el [historial de versiones](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) de Azure ad Connect para ver lo que se incluye y corregir en cada versión.</span><span class="sxs-lookup"><span data-stu-id="7bfa0-140">You can also review the Azure AD Connect [version release history](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) to see what is included and fixed in each release.</span></span>

## <a name="2-install-azure-ad-connect-and-configure-directory-synchronization"></a><span data-ttu-id="7bfa0-141">2. instalar Azure AD Connect y configurar la sincronización de directorios</span><span class="sxs-lookup"><span data-stu-id="7bfa0-141">2. Install Azure AD Connect and configure directory synchronization</span></span>

<span data-ttu-id="7bfa0-142">Antes de empezar, asegúrese de que tiene:</span><span class="sxs-lookup"><span data-stu-id="7bfa0-142">Before you begin, make sure you have:</span></span>

- <span data-ttu-id="7bfa0-143">El nombre de usuario y la contraseña de un administrador global de Office 365</span><span class="sxs-lookup"><span data-stu-id="7bfa0-143">The user name and password of an Office 365 global admin</span></span>
- <span data-ttu-id="7bfa0-144">El nombre de usuario y la contraseña de un administrador de dominio de AD DS</span><span class="sxs-lookup"><span data-stu-id="7bfa0-144">The user name and password of an AD DS domain administrator</span></span>
- <span data-ttu-id="7bfa0-145">Qué método de autenticación (PHS, PTA, federado)</span><span class="sxs-lookup"><span data-stu-id="7bfa0-145">Which authentication method (PHS, PTA, federated)</span></span>
- <span data-ttu-id="7bfa0-146">Si desea usar [el inicio de sesión único de línea directa (SSO) de Azure ad](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)</span><span class="sxs-lookup"><span data-stu-id="7bfa0-146">Whether you want to use [Azure AD Seamless Single Sign-on (SSO)](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)</span></span>

<span data-ttu-id="7bfa0-147">Siga estos pasos:</span><span class="sxs-lookup"><span data-stu-id="7bfa0-147">Follow these steps:</span></span>

1. <span data-ttu-id="7bfa0-148">Inicie sesión en el [centro de administración de Microsoft 365](https://admin.microsoft.com) https://admin.microsoft.com) ( **y seleccione** \> usuarios **activos** usuarios en el panel de navegación de la izquierda.</span><span class="sxs-lookup"><span data-stu-id="7bfa0-148">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) (https://admin.microsoft.com) and choose **Users** \> **Active Users** on the left navigation.</span></span>
2. <span data-ttu-id="7bfa0-149">En la **Página usuarios activos** , elija una **sincronización de directorios** **más** (tres puntos) \> .</span><span class="sxs-lookup"><span data-stu-id="7bfa0-149">On the **Active users** page, choose **More** (three dots) \> **Directory synchronization**.</span></span>
  
3. <span data-ttu-id="7bfa0-150">En la página **preparación de Azure Active Directory** , seleccione el vínculo **ir al centro de descargas para obtener la herramienta de Azure ad Connect** para empezar.</span><span class="sxs-lookup"><span data-stu-id="7bfa0-150">On the **Azure Active Directory preparation** page, select the **Go to the Download center to get the Azure AD Connect tool** link to get started.</span></span> 
4. <span data-ttu-id="7bfa0-151">Siga los pasos del [mapa de ruta de la instalación de Azure ad Connect y Azure ad Connect Health](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).</span><span class="sxs-lookup"><span data-stu-id="7bfa0-151">Follow the steps in [Azure AD Connect and Azure AD Connect Health installation roadmap](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).</span></span>

## <a name="3-finish-setting-up-domains"></a><span data-ttu-id="7bfa0-152">3. finalizar la configuración de dominios</span><span class="sxs-lookup"><span data-stu-id="7bfa0-152">3. Finish setting up domains</span></span>

<span data-ttu-id="7bfa0-153">Siga los pasos descritos en [crear registros DNS para Office 365 cuando administre sus registros DNS](https://docs.microsoft.com/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) para finalizar la configuración de sus dominios.</span><span class="sxs-lookup"><span data-stu-id="7bfa0-153">Follow the steps in [Create DNS records for Office 365 when you manage your DNS records](https://docs.microsoft.com/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) to finish setting up your domains.</span></span>

## <a name="next-step"></a><span data-ttu-id="7bfa0-154">Paso siguiente</span><span class="sxs-lookup"><span data-stu-id="7bfa0-154">Next step</span></span>

[<span data-ttu-id="7bfa0-155">Asignar licencias a cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="7bfa0-155">Assign licenses to user accounts</span></span>](assign-licenses-to-user-accounts.md)
