---
title: Integración de Azure con Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/09/2019
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-identity-device-management
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: a5efce5d-9c9c-4190-b61b-fd273c1d425f
description: Integre Microsoft 365 con Azure AD si desea la sincronización de contraseña o el inicio de sesión único con el entorno local.
ms.openlocfilehash: 64fcf25c75e636bebf78e9367f4cc68b367548f7
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606106"
---
# <a name="azure-integration-with-microsoft-365"></a><span data-ttu-id="1bcc5-103">Integración de Azure con Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="1bcc5-103">Azure integration with Microsoft 365</span></span>

<span data-ttu-id="1bcc5-104">*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="1bcc5-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="1bcc5-105">Microsoft 365 usa Azure Active Directory (Azure AD) para administrar las identidades de usuario en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="1bcc5-105">Microsoft 365 uses Azure Active Directory (Azure AD) to manage user identities behind the scenes.</span></span> <span data-ttu-id="1bcc5-106">Su suscripción a Microsoft 365 incluye una suscripción gratuita a Azure AD para que pueda integrar Microsoft 365 con Azure AD si desea sincronizar contraseñas o configurar el inicio de sesión único con su entorno local.</span><span class="sxs-lookup"><span data-stu-id="1bcc5-106">Your Microsoft 365 subscription includes a free subscription to Azure AD so that you can integrate Microsoft 365 with Azure AD if you want to sync passwords or set up single sign-on with your on-premises environment.</span></span> <span data-ttu-id="1bcc5-107">También puede comprar características avanzadas para administrar mejor sus cuentas.</span><span class="sxs-lookup"><span data-stu-id="1bcc5-107">You can also buy advanced features to better manage your accounts.</span></span>
  
<span data-ttu-id="1bcc5-108">Azure también ofrece otras funciones, como la administración de aplicaciones integradas, que puede usar para ampliar y personalizar sus suscripciones de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="1bcc5-108">Azure also offers other functionality, like managing integrated apps, that you can use to extend and customize your Microsoft 365 subscriptions.</span></span>
  
<span data-ttu-id="1bcc5-109">Puede usar los asesores de implementación de Azure AD para una instalación guiada y una experiencia de configuración (debe haber iniciado sesión en Microsoft 365):</span><span class="sxs-lookup"><span data-stu-id="1bcc5-109">You can use the Azure AD deployment advisors for a guided setup and configuration experience (you must be signed in to Microsoft 365):</span></span>

 - [<span data-ttu-id="1bcc5-110">Azure AD Connect Advisor</span><span class="sxs-lookup"><span data-stu-id="1bcc5-110">Azure AD Connect advisor</span></span>](https://aka.ms/aadconnectpwsync)
 - [<span data-ttu-id="1bcc5-111">Asesor de implementación de AD FS</span><span class="sxs-lookup"><span data-stu-id="1bcc5-111">AD FS deployment advisor</span></span>](https://aka.ms/adfsguidance)
 - [<span data-ttu-id="1bcc5-112">Guía de configuración de Azure AD</span><span class="sxs-lookup"><span data-stu-id="1bcc5-112">Azure AD setup guide</span></span>](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-microsoft-365-identity-management"></a><span data-ttu-id="1bcc5-113">Azure AD Editions y Microsoft 365 Identity Management</span><span class="sxs-lookup"><span data-stu-id="1bcc5-113">Azure AD editions and Microsoft 365 identity management</span></span>

<span data-ttu-id="1bcc5-114">Si tiene una suscripción de pago a Microsoft 365, también tiene una suscripción gratuita a Azure AD.</span><span class="sxs-lookup"><span data-stu-id="1bcc5-114">If you have a paid subscription to Microsoft 365, you also have a free subscription to Azure AD.</span></span> <span data-ttu-id="1bcc5-115">Puede usar Azure AD para crear y administrar cuentas de grupo y de usuario.</span><span class="sxs-lookup"><span data-stu-id="1bcc5-115">You can use Azure AD to create and manage user and group accounts.</span></span> <span data-ttu-id="1bcc5-116">Para activar esta suscripción tiene que completar un registro único.</span><span class="sxs-lookup"><span data-stu-id="1bcc5-116">To activate this subscription you have to complete a one-time registration.</span></span> <span data-ttu-id="1bcc5-117">Después, puede obtener acceso a Azure AD desde el centro de administración de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="1bcc5-117">Afterward, you can access Azure AD from your Microsoft 365 admin center.</span></span> 

<span data-ttu-id="1bcc5-118">Para obtener instrucciones, consulte [usar la suscripción gratuita de Azure ad](https://go.microsoft.com/fwlink/p/?LinkId=617127).</span><span class="sxs-lookup"><span data-stu-id="1bcc5-118">For instructions, see [use your free Azure AD subscription](https://go.microsoft.com/fwlink/p/?LinkId=617127).</span></span> <span data-ttu-id="1bcc5-119">Siga las instrucciones para registrar la suscripción gratuita a Azure AD que se incluye con su suscripción a Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="1bcc5-119">Follow the instructions to register the free Azure AD subscription that comes with your subscription to Microsoft 365.</span></span> <span data-ttu-id="1bcc5-120">No vaya directamente a azure.microsoft.com para registrarse o acabará con una suscripción de prueba o de pago a Microsoft Azure que es independiente de su versión gratuita para Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="1bcc5-120">Don't go directly to azure.microsoft.com to sign up or you'll end up with a trial or paid subscription to Microsoft Azure that is separate from your free one for Microsoft 365.</span></span> 
  
<span data-ttu-id="1bcc5-121">Con la suscripción gratuita, puede sincronizar con directorios locales, configurar el inicio de sesión único y sincronizar con muchos software como aplicaciones de servicio, como Salesforce, DropBox y muchos más.</span><span class="sxs-lookup"><span data-stu-id="1bcc5-121">With the free subscription you can synchronize with on-premises directories, set up single sign-on, and synchronize with many software as service applications, such as Salesforce, DropBox and many more.</span></span>
  
<span data-ttu-id="1bcc5-122">Si desea la funcionalidad mejorada de servicios de dominio de Active Directory (AD DS), sincronización bidireccional y otras capacidades de administración, puede actualizar su suscripción gratuita a una suscripción Premium de pago.</span><span class="sxs-lookup"><span data-stu-id="1bcc5-122">If you want enhanced Active Directory Domain Services (AD DS) functionality, bi-directional synchronization, and other management capabilities, you can upgrade your free subscription to a paid premium subscription.</span></span> <span data-ttu-id="1bcc5-123">Para obtener información detallada, consulte [Azure Active Directory Editions](https://azure.microsoft.com/pricing/details/active-directory/).</span><span class="sxs-lookup"><span data-stu-id="1bcc5-123">For details see [Azure Active Directory editions](https://azure.microsoft.com/pricing/details/active-directory/).</span></span>
  
<span data-ttu-id="1bcc5-124">Para obtener más información acerca de Microsoft 365 y Azure AD, consulte [Understanding microsoft 365 Identity and Azure Active Directory](about-office-365-identity.md).</span><span class="sxs-lookup"><span data-stu-id="1bcc5-124">For more information about Microsoft 365 and Azure AD, see [Understanding Microsoft 365 Identity and Azure Active Directory](about-office-365-identity.md).</span></span>
  
## <a name="extend-the-capabilities-of-your-microsoft-365-tenant"></a><span data-ttu-id="1bcc5-125">Ampliar las capacidades de su inquilino de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="1bcc5-125">Extend the capabilities of your Microsoft 365 tenant</span></span>

|<span data-ttu-id="1bcc5-126">**Característica**</span><span class="sxs-lookup"><span data-stu-id="1bcc5-126">**Feature**</span></span>|<span data-ttu-id="1bcc5-127">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="1bcc5-127">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="1bcc5-128">Aplicaciones integradas</span><span class="sxs-lookup"><span data-stu-id="1bcc5-128">Integrated apps</span></span>  <br/> |<span data-ttu-id="1bcc5-129">Puede conceder acceso a las aplicaciones individuales a los datos de Microsoft 365, como correo, calendarios, contactos, usuarios, grupos, archivos y carpetas.</span><span class="sxs-lookup"><span data-stu-id="1bcc5-129">You can grant individual apps access to your Microsoft 365 data, like mail, calendars, contacts, users, groups, files, and folders.</span></span> <span data-ttu-id="1bcc5-130">También puede autorizar estas aplicaciones en el nivel de administrador global y ponerlas a disposición de toda la empresa registrando las aplicaciones en Azure AD.</span><span class="sxs-lookup"><span data-stu-id="1bcc5-130">You can also authorize these apps at global admin level and make them available to your entire company by registering the apps in Azure AD.</span></span> <span data-ttu-id="1bcc5-131">Para obtener información detallada [, vea aplicaciones integradas y Azure ad para administradores de Microsoft 365](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).</span><span class="sxs-lookup"><span data-stu-id="1bcc5-131">For details see [Integrated Apps and Azure AD for Microsoft 365 administrators](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).</span></span>  <br/> <span data-ttu-id="1bcc5-132">Consulte también [el inicio de sesión único para las aplicaciones](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span><span class="sxs-lookup"><span data-stu-id="1bcc5-132">Also see [single sign-on to applications](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span></span>  <br/> |
|<span data-ttu-id="1bcc5-133">PowerApps</span><span class="sxs-lookup"><span data-stu-id="1bcc5-133">PowerApps</span></span>  <br/> | <span data-ttu-id="1bcc5-134">Las aplicaciones Power se centran en aplicaciones para dispositivos móviles que se pueden conectar a los orígenes de datos existentes, como las listas de SharePoint y otras aplicaciones de datos.</span><span class="sxs-lookup"><span data-stu-id="1bcc5-134">Power apps are focused apps for mobile devices that can connect to your existing data sources like SharePoint lists, and other data apps.</span></span> <span data-ttu-id="1bcc5-135">Consulte [Create a PowerApp for a List in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps Page](https://powerapps.microsoft.com/) for details.</span><span class="sxs-lookup"><span data-stu-id="1bcc5-135">See [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) for details.</span></span>  <br/> |
   
<span data-ttu-id="1bcc5-136">Obtenga más información en [aplicaciones integradas y Azure ad para los administradores de Microsoft 365](integrated-apps-and-azure-ads.md) y [la galería de aplicaciones de Azure ad y el inicio de sesión único](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).</span><span class="sxs-lookup"><span data-stu-id="1bcc5-136">Learn more at [Integrated Apps and Azure AD for Microsoft 365 administrators](integrated-apps-and-azure-ads.md) and [Azure AD application gallery and single-sign-on](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).</span></span>

## <a name="see-also"></a><span data-ttu-id="1bcc5-137">Ver también</span><span class="sxs-lookup"><span data-stu-id="1bcc5-137">See also</span></span>

[<span data-ttu-id="1bcc5-138">Información general de Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="1bcc5-138">Microsoft 365 Enterprise overview</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
