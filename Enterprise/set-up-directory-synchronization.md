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
ms.openlocfilehash: 505dde1a371d269f157ec076b75ca1bc5962c9da
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072152"
---
# <a name="set-up-directory-synchronization-for-office-365"></a><span data-ttu-id="7c5d3-103">Configurar la sincronización de directorios en Office 365</span><span class="sxs-lookup"><span data-stu-id="7c5d3-103">Set up directory synchronization for Office 365</span></span>

<span data-ttu-id="7c5d3-104">*Este artículo se aplica tanto a Office 365 Enterprise como a Microsoft 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="7c5d3-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="7c5d3-105">Office 365 usa un inquilino de Azure Active Directory (Azure AD) para almacenar y administrar identidades de autenticación y permisos para obtener acceso a los recursos basados en la nube.</span><span class="sxs-lookup"><span data-stu-id="7c5d3-105">Office 365 uses an Azure Active Directory (Azure AD) tenant to store and manage identities for authentication and permissions to access cloud-based resources.</span></span> 

<span data-ttu-id="7c5d3-106">Si tiene un servicio de dominio de Active Directory (AD DS) local, puede sincronizar las cuentas de usuario, los grupos y los contactos de AD DS con el inquilino de Azure AD de su suscripción a Office 365.</span><span class="sxs-lookup"><span data-stu-id="7c5d3-106">If you have an on-premises Active Directory Domain Services (AD DS), you can synchronize your AD DS user accounts, groups, and contacts with the Azure AD tenant of your Office 365 subscription.</span></span> <span data-ttu-id="7c5d3-107">Se trata de una identidad híbrida para Office 365.</span><span class="sxs-lookup"><span data-stu-id="7c5d3-107">This is hybrid identity for Office 365.</span></span> <span data-ttu-id="7c5d3-108">A continuación se muestran sus componentes.</span><span class="sxs-lookup"><span data-stu-id="7c5d3-108">Here are its components.</span></span>

![Componentes de la sincronización de directorios para Office 365](./media/about-office-365-identity/hybrid-identity.png)

<span data-ttu-id="7c5d3-110">Azure AD Connect se ejecuta en un servidor local y sincroniza AD DS con el inquilino de Azure AD.</span><span class="sxs-lookup"><span data-stu-id="7c5d3-110">Azure AD Connect runs on an on-premises server and synchronizes your AD DS with the Azure AD tenant.</span></span> <span data-ttu-id="7c5d3-111">Además de la sincronización de directorios, puede especificar estas opciones de autenticación:</span><span class="sxs-lookup"><span data-stu-id="7c5d3-111">Along with directory synchronization, you can also specify these authentication options:</span></span>

- <span data-ttu-id="7c5d3-112">Sincronización de hash de contraseña (PHS)</span><span class="sxs-lookup"><span data-stu-id="7c5d3-112">Password hash synchronization (PHS)</span></span>

  <span data-ttu-id="7c5d3-113">Azure AD realiza la autenticación en sí.</span><span class="sxs-lookup"><span data-stu-id="7c5d3-113">Azure AD performs the authentication itself.</span></span>

- <span data-ttu-id="7c5d3-114">Autenticación de paso a través (PTA)</span><span class="sxs-lookup"><span data-stu-id="7c5d3-114">Pass-through authentication (PTA)</span></span>

  <span data-ttu-id="7c5d3-115">Azure AD tiene AD DS realizar la autenticación.</span><span class="sxs-lookup"><span data-stu-id="7c5d3-115">Azure AD has AD DS perform the authentication.</span></span>

- <span data-ttu-id="7c5d3-116">Autenticación federada</span><span class="sxs-lookup"><span data-stu-id="7c5d3-116">Federated authentication</span></span>

  <span data-ttu-id="7c5d3-117">Azure AD redirige al equipo cliente que solicita la autenticación para ponerse en contacto con otro proveedor de identidades.</span><span class="sxs-lookup"><span data-stu-id="7c5d3-117">Azure AD redirects the client computer requesting authentication to contact another identity provider.</span></span>

<span data-ttu-id="7c5d3-118">Consulte [identidades híbridas](plan-for-directory-synchronization.md) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="7c5d3-118">See [Hybrid identities](plan-for-directory-synchronization.md) for more information.</span></span>
  
## <a name="1-review-prerequisites-for-azure-ad-connect"></a><span data-ttu-id="7c5d3-119">1. Revise los requisitos previos de Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="7c5d3-119">1. Review prerequisites for Azure AD Connect</span></span>

<span data-ttu-id="7c5d3-120">Obtendrá una suscripción gratuita a Azure AD con su suscripción de Office 365.</span><span class="sxs-lookup"><span data-stu-id="7c5d3-120">You get a free Azure AD subscription with your Office 365 subscription.</span></span> <span data-ttu-id="7c5d3-121">Al configurar la sincronización de directorios, se instalará Azure AD Connect en uno de los servidores locales.</span><span class="sxs-lookup"><span data-stu-id="7c5d3-121">When you set up directory synchronization, you will install Azure AD Connect on one of your on-premises servers.</span></span>
  
<span data-ttu-id="7c5d3-122">Para Office 365, necesitará:</span><span class="sxs-lookup"><span data-stu-id="7c5d3-122">For Office 365 you'll need to:</span></span>
  
- <span data-ttu-id="7c5d3-123">Compruebe el dominio local.</span><span class="sxs-lookup"><span data-stu-id="7c5d3-123">Verify your on-premises domain.</span></span> <span data-ttu-id="7c5d3-124">El Asistente de Azure AD Connect le guía a través de esto.</span><span class="sxs-lookup"><span data-stu-id="7c5d3-124">The Azure AD Connect wizard guides you through this.</span></span>
- <span data-ttu-id="7c5d3-125">Obtenga los nombres de usuario y las contraseñas de las cuentas de administrador del inquilino de Office 365 y AD DS.</span><span class="sxs-lookup"><span data-stu-id="7c5d3-125">Obtain the user names and passwords for the admin accounts of your Office 365 tenant and AD DS.</span></span>

<span data-ttu-id="7c5d3-126">Para el servidor local en el que instale Azure AD Connect, necesitará:</span><span class="sxs-lookup"><span data-stu-id="7c5d3-126">For your on-premises server on which you install Azure AD Connect, you'll need:</span></span>
  
|<span data-ttu-id="7c5d3-127">**Sistema operativo del servidor**</span><span class="sxs-lookup"><span data-stu-id="7c5d3-127">**Server OS**</span></span>|<span data-ttu-id="7c5d3-128">**Otros programas de software**</span><span class="sxs-lookup"><span data-stu-id="7c5d3-128">**Other software**</span></span>|
|:-----|:-----|
|<span data-ttu-id="7c5d3-129">Windows Server 2012 R2 y posterior</span><span class="sxs-lookup"><span data-stu-id="7c5d3-129">Windows Server 2012 R2 and later</span></span> | <span data-ttu-id="7c5d3-130">-PowerShell está instalado de forma predeterminada, no se requiere ninguna acción.</span><span class="sxs-lookup"><span data-stu-id="7c5d3-130">- PowerShell is installed by default, no action is required.</span></span>  <br> <span data-ttu-id="7c5d3-131">-Net 4.5.1 y versiones posteriores se ofrecen a través de Windows Update.</span><span class="sxs-lookup"><span data-stu-id="7c5d3-131">- Net 4.5.1 and later releases are offered through Windows Update.</span></span> <span data-ttu-id="7c5d3-132">Asegúrese de que tiene instaladas las últimas actualizaciones de Windows Server en el panel de control.</span><span class="sxs-lookup"><span data-stu-id="7c5d3-132">Make sure you have installed the latest updates to Windows Server in the Control Panel.</span></span> |
|<span data-ttu-id="7c5d3-133">Windows Server 2008 R2 con Service Pack 1 (SP1) \* \* o Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="7c5d3-133">Windows Server 2008 R2 with Service Pack 1 (SP1)\*\* or Windows Server 2012</span></span> | <span data-ttu-id="7c5d3-134">-La versión más reciente de PowerShell está disponible en Windows Management Framework 4,0.</span><span class="sxs-lookup"><span data-stu-id="7c5d3-134">- The latest version of PowerShell is available in Windows Management Framework 4.0.</span></span> <span data-ttu-id="7c5d3-135">Buscarlo en el [centro de descarga de Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="7c5d3-135">Search for it on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br> <span data-ttu-id="7c5d3-136">-.Net 4.5.1 y versiones posteriores están disponibles en el [centro de descarga de Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="7c5d3-136">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |
|<span data-ttu-id="7c5d3-137">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="7c5d3-137">Windows Server 2008</span></span> | <span data-ttu-id="7c5d3-138">-La versión más reciente compatible de PowerShell está disponible en Windows Management Framework 3,0, disponible en el [centro de descarga de Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="7c5d3-138">- The latest supported version of PowerShell is available in Windows Management Framework 3.0, available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br> <span data-ttu-id="7c5d3-139">-.Net 4.5.1 y versiones posteriores están disponibles en el [centro de descarga de Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="7c5d3-139">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |

<span data-ttu-id="7c5d3-140">Consulte requisitos [previos de Azure Active Directory Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites) para obtener información detallada sobre los requisitos de hardware, software, cuentas y permisos, los requisitos de certificados SSL y los límites de objetos para Azure ad Connect.</span><span class="sxs-lookup"><span data-stu-id="7c5d3-140">See [Prerequisites for Azure Active Directory Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites) for the details of hardware, software, account and permissions requirements, SSL certificate requirements, and object limits for Azure AD Connect.</span></span>
  
<span data-ttu-id="7c5d3-141">También puede revisar el [historial de versiones](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) de Azure ad Connect para ver lo que se incluye y corregir en cada versión.</span><span class="sxs-lookup"><span data-stu-id="7c5d3-141">You can also review the Azure AD Connect [version release history](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) to see what is included and fixed in each release.</span></span>

## <a name="2-install-azure-ad-connect-and-configure-directory-synchronization"></a><span data-ttu-id="7c5d3-142">2. instalar Azure AD Connect y configurar la sincronización de directorios</span><span class="sxs-lookup"><span data-stu-id="7c5d3-142">2. Install Azure AD Connect and configure directory synchronization</span></span>

<span data-ttu-id="7c5d3-143">Antes de empezar, asegúrese de que tiene:</span><span class="sxs-lookup"><span data-stu-id="7c5d3-143">Before you begin, make sure you have:</span></span>

- <span data-ttu-id="7c5d3-144">El nombre de usuario y la contraseña de un administrador global de Office 365</span><span class="sxs-lookup"><span data-stu-id="7c5d3-144">The user name and password of an Office 365 global admin</span></span>
- <span data-ttu-id="7c5d3-145">El nombre de usuario y la contraseña de un administrador de dominio de AD DS</span><span class="sxs-lookup"><span data-stu-id="7c5d3-145">The user name and password of an AD DS domain administrator</span></span>
- <span data-ttu-id="7c5d3-146">Qué método de autenticación (PHS, PTA, federado)</span><span class="sxs-lookup"><span data-stu-id="7c5d3-146">Which authentication method (PHS, PTA, federated)</span></span>
- <span data-ttu-id="7c5d3-147">Si desea usar [el inicio de sesión único de línea directa (SSO) de Azure ad](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)</span><span class="sxs-lookup"><span data-stu-id="7c5d3-147">Whether you want to use [Azure AD Seamless Single Sign-on (SSO)](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)</span></span>

<span data-ttu-id="7c5d3-148">Siga estos pasos:</span><span class="sxs-lookup"><span data-stu-id="7c5d3-148">Follow these steps:</span></span>

1. <span data-ttu-id="7c5d3-149">Inicie sesión en el [centro de administración de Microsoft 365](https://admin.microsoft.com) https://admin.microsoft.com) ( **y seleccione** \> usuarios **activos** usuarios en el panel de navegación de la izquierda.</span><span class="sxs-lookup"><span data-stu-id="7c5d3-149">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) (https://admin.microsoft.com) and choose **Users** \> **Active Users** on the left navigation.</span></span>
2. <span data-ttu-id="7c5d3-150">En la **Página usuarios activos** , elija una **sincronización de directorios** **más** (tres puntos) \> .</span><span class="sxs-lookup"><span data-stu-id="7c5d3-150">On the **Active users** page, choose **More** (three dots) \> **Directory synchronization**.</span></span>
  
3. <span data-ttu-id="7c5d3-151">En la página **preparación de Azure Active Directory** , seleccione el vínculo **ir al centro de descargas para obtener la herramienta de Azure ad Connect** para empezar.</span><span class="sxs-lookup"><span data-stu-id="7c5d3-151">On the **Azure Active Directory preparation** page, select the **Go to the Download center to get the Azure AD Connect tool** link to get started.</span></span> 
4. <span data-ttu-id="7c5d3-152">Siga los pasos del [mapa de ruta de la instalación de Azure ad Connect y Azure ad Connect Health](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).</span><span class="sxs-lookup"><span data-stu-id="7c5d3-152">Follow the steps in [Azure AD Connect and Azure AD Connect Health installation roadmap](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).</span></span>

## <a name="3-finish-setting-up-domains"></a><span data-ttu-id="7c5d3-153">3. finalizar la configuración de dominios</span><span class="sxs-lookup"><span data-stu-id="7c5d3-153">3. Finish setting up domains</span></span>

<span data-ttu-id="7c5d3-154">Siga los pasos descritos en [crear registros DNS para Office 365 cuando administre sus registros DNS](https://docs.microsoft.com/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) para finalizar la configuración de sus dominios.</span><span class="sxs-lookup"><span data-stu-id="7c5d3-154">Follow the steps in [Create DNS records for Office 365 when you manage your DNS records](https://docs.microsoft.com/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) to finish setting up your domains.</span></span>

## <a name="next-step"></a><span data-ttu-id="7c5d3-155">Paso siguiente</span><span class="sxs-lookup"><span data-stu-id="7c5d3-155">Next step</span></span>

[<span data-ttu-id="7c5d3-156">Asignar licencias a cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="7c5d3-156">Assign licenses to user accounts</span></span>](assign-licenses-to-user-accounts.md)
