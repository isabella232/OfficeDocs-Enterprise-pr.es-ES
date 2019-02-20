---
title: Integración de Azure con Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: a5efce5d-9c9c-4190-b61b-fd273c1d425f
description: Su suscripción a Office 365 incluye una suscripción a Azure AD. Integre Office 365 con Azure AD si desea la sincronización de contraseña o el inicio de sesión único con el entorno local.
ms.openlocfilehash: 0ad1c064d2ffe29f0f06e1368cd728d8b3bd630b
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085479"
---
# <a name="azure-integration-with-office-365"></a><span data-ttu-id="28211-104">Integración de Azure con Office 365</span><span class="sxs-lookup"><span data-stu-id="28211-104">Azure integration with Office 365</span></span>

<span data-ttu-id="28211-p102">Office 365 usa Azure Active Directory (Azure AD) para administrar las identidades de usuario en segundo plano. Su suscripción a Office 365 incluye una suscripción gratuita a Azure AD para que pueda integrar Office 365 con Azure AD si desea sincronizar contraseñas o configurar el inicio de sesión único con su entorno local. También puede comprar características avanzadas para administrar mejor sus cuentas.</span><span class="sxs-lookup"><span data-stu-id="28211-p102">Office 365 uses Azure Active Directory (Azure AD) to manage user identities behind the scenes. Your Office 365 subscription includes a free subscription to Azure AD so that you can integrate Office 365 with Azure AD if you want to sync passwords or set up single sign-on with your on-premises environment. You can also buy advanced features to better manage your accounts.</span></span>
  
<span data-ttu-id="28211-108">Azure también ofrece otras funciones, como la administración de aplicaciones integradas, que puede usar para ampliar y personalizar sus suscripciones a Office 365.</span><span class="sxs-lookup"><span data-stu-id="28211-108">Azure also offers other functionality, like managing integrated apps, that you can use to extend and customize your Office 365 subscriptions.</span></span>
  
<span data-ttu-id="28211-109">Puede usar los asesores de implementación de Azure AD para una instalación guiada y una experiencia de configuración:</span><span class="sxs-lookup"><span data-stu-id="28211-109">You can use the Azure AD deployment advisors for a guided setup and configuration experience:</span></span>
 - [<span data-ttu-id="28211-110">Azure AD Connect Advisor</span><span class="sxs-lookup"><span data-stu-id="28211-110">Azure AD Connect advisor</span></span>](https://aka.ms/aadconnectpwsync)
 - [<span data-ttu-id="28211-111">Asesor de implementación de AD FS</span><span class="sxs-lookup"><span data-stu-id="28211-111">AD FS deployment advisor</span></span>](https://aka.ms/adfsguidance)
 - [<span data-ttu-id="28211-112">Asistente para la implementación de Azure RMS</span><span class="sxs-lookup"><span data-stu-id="28211-112">Azure RMS Deployment Wizard</span></span>](https://aka.ms/azuremsguidance)
 - [<span data-ttu-id="28211-113">Guía de instalación de Azure AD Premium</span><span class="sxs-lookup"><span data-stu-id="28211-113">Azure AD Premium setup guide</span></span>](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-office-365-identity-management"></a><span data-ttu-id="28211-114">Azure AD Editions y Office 365 Identity Management</span><span class="sxs-lookup"><span data-stu-id="28211-114">Azure AD editions and Office 365 identity management</span></span>

<span data-ttu-id="28211-p103">Si tiene una suscripción de pago a Office 365, también tiene una suscripción gratuita a Azure AD. Puede usar Azure AD para crear y administrar cuentas de grupo y de usuario. Para activar esta suscripción tiene que completar un registro único. Después, puede tener acceso a Azure AD desde el portal de administración de Office 365. Para obtener instrucciones, consulte [registrar su suscripción gratuita a Azure ad](https://go.microsoft.com/fwlink/p/?LinkId=617127).</span><span class="sxs-lookup"><span data-stu-id="28211-p103">If you have a paid subscription to Office 365, you also have a free subscription to Azure AD. You can use Azure AD to create and manage user and group accounts. To activate this subscription you have to complete a one-time registration. Afterward, you can access Azure AD from your Office 365 admin portal. For instructions, see [register your free Azure AD subscription](https://go.microsoft.com/fwlink/p/?LinkId=617127).</span></span> 
  
> [!TIP]
> <span data-ttu-id="28211-p104">Siga las instrucciones anteriores para registrar la suscripción gratuita a Azure AD que se incluye con su suscripción a Office 365. No vaya directamente a azure.microsoft.com para registrarse o termine con una suscripción de prueba o de pago a Microsoft Azure que es independiente de su versión gratuita de una para Office 365.</span><span class="sxs-lookup"><span data-stu-id="28211-p104">Follow the instructions above to register the free Azure AD subscription that comes with your subscription to Office 365. Don't go directly to azure.microsoft.com to sign up or you'll end up with a trial or paid subscription to Microsoft Azure that is separate from your free one for Office 365.</span></span> 
  
<span data-ttu-id="28211-122">Con la suscripción gratuita, puede sincronizar con directorios locales, configurar el inicio de sesión único y sincronizar con muchos software como aplicaciones de servicio, como Salesforce, DropBox y muchos más.</span><span class="sxs-lookup"><span data-stu-id="28211-122">With the free subscription you can synchronize with on-premises directories, set up single sign-on, and synchronize with many software as service applications, such as Salesforce, DropBox and many more.</span></span>
  
<span data-ttu-id="28211-p105">Si desea funcionalidad de AD DS mejorada, sincronización bidireccional y otras capacidades de administración, puede actualizar su suscripción gratuita a una suscripción Premium de pago. Para obtener información detallada, consulte [Azure Active Directory Editions](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis).</span><span class="sxs-lookup"><span data-stu-id="28211-p105">If you want enhanced AD DS functionality, bi-directional synchronization, and other management capabilities, you can upgrade your free subscription to a paid premium subscription. For details see [Azure Active Directory editions](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis).</span></span>
  
<span data-ttu-id="28211-125">Para obtener más información sobre Office 365 y Azure AD, consulte [understandIng office 365 Identity and Azure Active Directory](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9).</span><span class="sxs-lookup"><span data-stu-id="28211-125">For more information about Office 365 and Azure AD, see [Understanding Office 365 Identity and Azure Active Directory](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9).</span></span>
  
## <a name="extend-the-capabilities-of-your-office-365-tenant"></a><span data-ttu-id="28211-126">Ampliar las capacidades de su inquilino de Office 365</span><span class="sxs-lookup"><span data-stu-id="28211-126">Extend the capabilities of your Office 365 tenant</span></span>

|<span data-ttu-id="28211-127">**Característica**</span><span class="sxs-lookup"><span data-stu-id="28211-127">**Feature**</span></span>|<span data-ttu-id="28211-128">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="28211-128">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="28211-129">Aplicaciones integradas</span><span class="sxs-lookup"><span data-stu-id="28211-129">Integrated apps</span></span>  <br/> |<span data-ttu-id="28211-p106">Puede conceder acceso a aplicaciones individuales a los datos de Office 365, como correo, calendarios, contactos, usuarios, grupos, archivos y carpetas. También puede autorizar estas aplicaciones en el nivel de administrador global y ponerlas a disposición de toda la empresa registrando las aplicaciones en Azure AD. Para obtener información detallada [, vea aplicaciones integradas y Azure ad para administradores de Office 365](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).</span><span class="sxs-lookup"><span data-stu-id="28211-p106">You can grant individual apps access to your Office 365 data, like mail, calendars, contacts, users, groups, files, and folders. You can also authorize these apps at global admin level and make them available to your entire company by registering the apps in Azure AD. For details see [Integrated Apps and Azure AD for Office 365 administrators](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).  </span></span><br/> <span data-ttu-id="28211-133">Consulte también la [Galería de aplicaciones de Azure ad y el inicio de sesión único](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span><span class="sxs-lookup"><span data-stu-id="28211-133">See also [Azure AD application gallery and single-sign-on](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span></span>  <br/> |
|<span data-ttu-id="28211-134">PowerApps</span><span class="sxs-lookup"><span data-stu-id="28211-134">PowerApps</span></span>  <br/> | <span data-ttu-id="28211-p107">Las aplicaciones Power se centran en aplicaciones para dispositivos móviles que se pueden conectar a los orígenes de datos existentes, como las listas de SharePoint y otras aplicaciones de datos. Consulte [Create a PowerApp for a List in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps Page](https://powerapps.microsoft.com/) for details.</span><span class="sxs-lookup"><span data-stu-id="28211-p107">Power apps are focused apps for mobile devices that can connect to your existing data sources like SharePoint lists, and other data apps. See [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) for details.  </span></span><br/> |
   
<span data-ttu-id="28211-137">Para obtener información sobre otros recursos sobre la nube de Microsoft y Office 365, consulte estos recursos:</span><span class="sxs-lookup"><span data-stu-id="28211-137">For other resources about the Microsoft Cloud and Office 365, see these resources:</span></span>
  
- [<span data-ttu-id="28211-138">Identidad de Microsoft Cloud para arquitectos empresariales</span><span class="sxs-lookup"><span data-stu-id="28211-138">Microsoft Cloud Identity for Enterprise Architects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524586)
    
- [<span data-ttu-id="28211-139">Implementar Sincronización de directorios (DirSync) de Office 365 en Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="28211-139">Deploy Office 365 Directory Synchronization (DirSync) in Microsoft Azure</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=517887)
    

<span data-ttu-id="28211-140">Para obtener más información [, vea aplicaciones integradas y Azure ad para Office 365 administradores](integrated-apps-and-azure-ads.md) y la [Galería de aplicaciones de Azure ad y el inicio de sesión único](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).</span><span class="sxs-lookup"><span data-stu-id="28211-140">Learn more at [Integrated Apps and Azure AD for Office 365 administrators](integrated-apps-and-azure-ads.md) and [Azure AD application gallery and single-sign-on](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).</span></span>

### <a name="power-apps"></a><span data-ttu-id="28211-141">Power apps</span><span class="sxs-lookup"><span data-stu-id="28211-141">Power Apps</span></span>
<span data-ttu-id="28211-p108">Las aplicaciones Power se centran en aplicaciones para dispositivos móviles que se pueden conectar a los orígenes de datos existentes, como las listas de SharePoint y otras aplicaciones de datos. Consulte [Create a PowerApp for a List in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps Page](https://powerapps.microsoft.com/) for details.</span><span class="sxs-lookup"><span data-stu-id="28211-p108">Power apps are focused apps for mobile devices that can connect to your existing data sources like SharePoint lists, and other data apps. See [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) for details.</span></span>