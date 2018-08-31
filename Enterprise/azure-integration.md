---
title: Integración de Azure con Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: a5efce5d-9c9c-4190-b61b-fd273c1d425f
description: La suscripción de Office 365 incluye una suscripción a Azure AD. Integrar Office 365 con Azure AD si desea que la sincronización de contraseñas o el inicio de sesión único con su entorno local.
ms.openlocfilehash: 276243b953d18953ef3ea8f1189d1af8292dca6a
ms.sourcegitcommit: b1cd20300a616ebef2f00668f42ba14e8aa5fcab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/30/2018
ms.locfileid: "23531843"
---
# <a name="azure-integration-with-office-365"></a><span data-ttu-id="d1a0f-104">Integración de Azure con Office 365</span><span class="sxs-lookup"><span data-stu-id="d1a0f-104">Azure integration with Office 365</span></span>

<span data-ttu-id="d1a0f-p102">Office 365 usa Azure Active Directory (AD Azure) para administrar las identidades de usuario en segundo plano. La suscripción de Office 365 incluye una suscripción gratuita a Azure AD para que pueda integrar Office 365 con Azure AD si desea sincronizar las contraseñas o configurar un inicio de sesión único con su entorno local. También puede comprar características avanzadas para administrar mejor sus cuentas.</span><span class="sxs-lookup"><span data-stu-id="d1a0f-p102">Office 365 uses Azure Active Directory (Azure AD) to manage user identities behind the scenes. Your Office 365 subscription includes a free subscription to Azure AD so that you can integrate Office 365 with Azure AD if you want to sync passwords or set up single sign-on with your on-premises environment. You can also buy advanced features to better manage your accounts.</span></span>
  
<span data-ttu-id="d1a0f-108">Azure también ofrece otras funciones, como la administración de aplicaciones integradas, que puede usar para ampliar y personalizar las suscripciones de Office 365.</span><span class="sxs-lookup"><span data-stu-id="d1a0f-108">Azure also offers other functionality, like managing integrated apps, that you can use to extend and customize your Office 365 subscriptions.</span></span>
  
<span data-ttu-id="d1a0f-109">Puede usar los asesores de implementación de Azure AD para una experiencia interactiva del programa de instalación y configuración:</span><span class="sxs-lookup"><span data-stu-id="d1a0f-109">You can use the Azure AD deployment advisors for a guided setup and configuration experience:</span></span>
 - [<span data-ttu-id="d1a0f-110">Asesor de Azure Connect de AD</span><span class="sxs-lookup"><span data-stu-id="d1a0f-110">Azure AD Connect advisor</span></span>](https://aka.ms/aadconnectpwsync)
 - [<span data-ttu-id="d1a0f-111">Asesor de implementación de AD FS</span><span class="sxs-lookup"><span data-stu-id="d1a0f-111">AD FS deployment advisor</span></span>](https://aka.ms/adfsguidance)
 - [<span data-ttu-id="d1a0f-112">Asistente para la implementación de RMS de Azure</span><span class="sxs-lookup"><span data-stu-id="d1a0f-112">Azure RMS Deployment Wizard</span></span>](https://aka.ms/azuremsguidance)
 - [<span data-ttu-id="d1a0f-113">Guía de configuración de Azure AD Premium</span><span class="sxs-lookup"><span data-stu-id="d1a0f-113">Azure AD Premium setup guide</span></span>](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-office-365-identity-management"></a><span data-ttu-id="d1a0f-114">Ediciones de Azure AD y administración de identidades de Office 365</span><span class="sxs-lookup"><span data-stu-id="d1a0f-114">Azure AD editions and Office 365 identity management</span></span>

<span data-ttu-id="d1a0f-p103">Si tiene una suscripción de pago a Office 365, también tiene una suscripción gratuita a Azure AD. Puede usar Azure AD para crear y administrar cuentas de usuario y grupo. Para activar esta suscripción que tiene que completar un único registro. Posteriormente, puede tener acceso a Azure AD desde el portal de administración de Office 365. Para obtener instrucciones, vea [registrar su libre suscripción de Azure AD](https://go.microsoft.com/fwlink/p/?LinkId=617127).</span><span class="sxs-lookup"><span data-stu-id="d1a0f-p103">If you have a paid subscription to Office 365, you also have a free subscription to Azure AD. You can use Azure AD to create and manage user and group accounts. To activate this subscription you have to complete a one-time registration. Afterward, you can access Azure AD from your Office 365 admin portal. For instructions, see [register your free Azure AD subscription](https://go.microsoft.com/fwlink/p/?LinkId=617127).</span></span> 
  
> [!TIP]
> <span data-ttu-id="d1a0f-p104">Siga las instrucciones anteriores para registrar el libre Azure AD suscripción que se incluye con la suscripción a Office 365. No ir directamente a azure.microsoft.com para registrarse y o terminará con una suscripción de prueba o de pagada a Microsoft Azure que es independiente de su gratuita para Office 365.</span><span class="sxs-lookup"><span data-stu-id="d1a0f-p104">Follow the instructions above to register the free Azure AD subscription that comes with your subscription to Office 365. Don't go directly to azure.microsoft.com to sign up or you'll end up with a trial or paid subscription to Microsoft Azure that is separate from your free one for Office 365.</span></span> 
  
<span data-ttu-id="d1a0f-122">Con la suscripción gratuita que puede sincronizar con directorios locales, configurar el inicio de sesión único y sincronizar con el software de muchos como aplicaciones de servicio, como la fuerza de ventas, lista desplegable y muchos más.</span><span class="sxs-lookup"><span data-stu-id="d1a0f-122">With the free subscription you can synchronize with on-premises directories, set up single sign-on, and synchronize with many software as service applications, such as Salesforce, DropBox and many more.</span></span>
  
<span data-ttu-id="d1a0f-p105">Si desea que la funcionalidad mejorada de AD DS, la sincronización bidireccional y otras funciones de administración, puede actualizar su suscripción gratuita a una suscripción de pago premium. Para obtener más información, vea [ediciones de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis).</span><span class="sxs-lookup"><span data-stu-id="d1a0f-p105">If you want enhanced AD DS functionality, bi-directional synchronization, and other management capabilities, you can upgrade your free subscription to a paid premium subscription. For details see [Azure Active Directory editions](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis).</span></span>
  
<span data-ttu-id="d1a0f-125">Para obtener más información acerca de Office 365 y Azure AD, consulte [Understanding Office 365 identidad y Azure Active Directory](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9).</span><span class="sxs-lookup"><span data-stu-id="d1a0f-125">For more information about Office 365 and Azure AD, see [Understanding Office 365 Identity and Azure Active Directory](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9).</span></span>
  
## <a name="extend-the-capabilities-of-your-office-365-tenant"></a><span data-ttu-id="d1a0f-126">Extender las capacidades de su inquilino de Office 365</span><span class="sxs-lookup"><span data-stu-id="d1a0f-126">Extend the capabilities of your Office 365 tenant</span></span>

|<span data-ttu-id="d1a0f-127">**Característica**</span><span class="sxs-lookup"><span data-stu-id="d1a0f-127">**Feature**</span></span>|<span data-ttu-id="d1a0f-128">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="d1a0f-128">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="d1a0f-129">Aplicaciones integradas</span><span class="sxs-lookup"><span data-stu-id="d1a0f-129">Integrated apps</span></span>  <br/> |<span data-ttu-id="d1a0f-p106">Puede conceder acceso de aplicaciones individuales a los datos de Office 365, como correo, calendarios, contactos, los usuarios, grupos, archivos y carpetas. También puede autorizar estas aplicaciones en el nivel de administrador global y que estén disponibles para toda la empresa mediante el registro de las aplicaciones en Azure AD. Para obtener información detallada, vea [aplicaciones integrada y Azure AD para administradores de Office 365](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).</span><span class="sxs-lookup"><span data-stu-id="d1a0f-p106">You can grant individual apps access to your Office 365 data, like mail, calendars, contacts, users, groups, files, and folders. You can also authorize these apps at global admin level and make them available to your entire company by registering the apps in Azure AD. For details see [Integrated Apps and Azure AD for Office 365 administrators](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).  </span></span><br/> <span data-ttu-id="d1a0f-133">Consulte también [Galería de Azure AD de aplicación y de sesión único y](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span><span class="sxs-lookup"><span data-stu-id="d1a0f-133">See also [Azure AD application gallery and single-sign-on](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span></span>  <br/> |
|<span data-ttu-id="d1a0f-134">PowerApps</span><span class="sxs-lookup"><span data-stu-id="d1a0f-134">PowerApps</span></span>  <br/> | <span data-ttu-id="d1a0f-p107">Aplicaciones de Power son aplicaciones reducidas para dispositivos móviles que pueden conectarse a los datos existentes orígenes como listas de SharePoint y otras aplicaciones de datos. Para obtener información detallada, vea [crear un PowerApp para obtener una lista de SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) y [PowerApps página](https://powerapps.microsoft.com/) .</span><span class="sxs-lookup"><span data-stu-id="d1a0f-p107">Power apps are focused apps for mobile devices that can connect to your existing data sources like SharePoint lists, and other data apps. See [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) for details.  </span></span><br/> |
   
<span data-ttu-id="d1a0f-137">Para otros recursos acerca de los Microsoft Cloud y Office 365, consulte estos recursos:</span><span class="sxs-lookup"><span data-stu-id="d1a0f-137">For other resources about the Microsoft Cloud and Office 365, see these resources:</span></span>
  
- [<span data-ttu-id="d1a0f-138">Identidad de Microsoft Cloud para arquitectos empresariales</span><span class="sxs-lookup"><span data-stu-id="d1a0f-138">Microsoft Cloud Identity for Enterprise Architects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=828642)
    
- [<span data-ttu-id="d1a0f-139">Implementar Sincronización de directorios (DirSync) de Office 365 en Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="d1a0f-139">Deploy Office 365 Directory Synchronization (DirSync) in Microsoft Azure</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=517887)
    

<span data-ttu-id="d1a0f-140">Encontrará más información en [aplicaciones integrada y Azure AD para administradores de Office 365](integrated-apps-and-azure-ads.md) y [Galería de Azure AD de aplicación y de sesión único y](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).</span><span class="sxs-lookup"><span data-stu-id="d1a0f-140">Learn more at [Integrated Apps and Azure AD for Office 365 administrators](integrated-apps-and-azure-ads.md) and [Azure AD application gallery and single-sign-on](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).</span></span>

### <a name="power-apps"></a><span data-ttu-id="d1a0f-141">Aplicaciones de alimentación</span><span class="sxs-lookup"><span data-stu-id="d1a0f-141">Power Apps</span></span>
<span data-ttu-id="d1a0f-p108">Aplicaciones de Power son aplicaciones reducidas para dispositivos móviles que pueden conectarse a los datos existentes orígenes como listas de SharePoint y otras aplicaciones de datos. Para obtener información detallada, vea [crear un PowerApp para obtener una lista de SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) y [PowerApps página](https://powerapps.microsoft.com/) .</span><span class="sxs-lookup"><span data-stu-id="d1a0f-p108">Power apps are focused apps for mobile devices that can connect to your existing data sources like SharePoint lists, and other data apps. See [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) for details.</span></span>