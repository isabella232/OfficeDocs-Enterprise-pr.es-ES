---
title: Implementar Office 365 Enterprise para la organización
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- M365-subscription-management
ms.custom: Adm_O365
ms.assetid: ee73dafb-be54-492e-bcfd-0fbfb5f65e94
description: Estos pasos generales están diseñados para ayudarle a implementar Office 365, conectar su Active Directory y migrar los datos, y para ayudar a las personas de su organización a empezar a usar la versión más reciente de Office 2016.
ms.openlocfilehash: 2530b170c607f635f6f1baebf1d83fa7745d23a6
ms.sourcegitcommit: 47c6156c0038745103b71f44b2a3b103c62e5d6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2019
ms.locfileid: "34102548"
---
# <a name="deploy-office-365-enterprise-for-your-organization"></a><span data-ttu-id="6ab47-103">Implementar Office 365 Enterprise para la organización</span><span class="sxs-lookup"><span data-stu-id="6ab47-103">Deploy Office 365 Enterprise for your organization</span></span>
<span data-ttu-id="6ab47-p101">¿Listo para implementar e integrar Office 365 Enterprise en su infraestructura local? Estos pasos generales están diseñados para ayudarle a conectar su directorio y migrar los datos, y para ayudar a las personas de su organización a empezar a usar la versión más reciente de Office 2016.</span><span class="sxs-lookup"><span data-stu-id="6ab47-p101">Ready to deploy and integrate Office 365 Enterprise with your on-premises infrastructure? These overview steps are designed to help you connect your directory, migrate your data, and help the people in your organization begin using the latest version of Office 2016.</span></span>
  
<span data-ttu-id="6ab47-106">Estos pasos van dirigidos a empresas y [organizaciones sin ánimo de lucro](https://go.microsoft.com/fwlink/?LinkId=627221) que deseen comenzar con una implementación personalizada de Office 365 Enterprise.</span><span class="sxs-lookup"><span data-stu-id="6ab47-106">These steps are for businesses and [nonprofits](https://go.microsoft.com/fwlink/?LinkId=627221) that want to start with a custom deployment of Office 365 Enterprise.</span></span> 
  
<span data-ttu-id="6ab47-p102">¿No tiene Office 365 Enterprise? Vea [Configurar Office 365 para empresas](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) para obtener instrucciones para pequeñas empresas.</span><span class="sxs-lookup"><span data-stu-id="6ab47-p102">Don't have Office 365 Enterprise? See [Set up Office 365 for business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) for instructions for small businesses.</span></span> 
  
## <a name="guided-enterprise-office-365-setup-process-with-fasttrack"></a><span data-ttu-id="6ab47-109">Proceso guiado de implementación empresarial de Office 365 con FastTrack</span><span class="sxs-lookup"><span data-stu-id="6ab47-109">Guided enterprise Office 365 setup process with FastTrack</span></span>
<span data-ttu-id="6ab47-p103">**[FastTrack](https://docs.microsoft.com/fasttrack)** para Office 365 es el mejor método para implementar Office 365. FastTrack le guiará por las configuraciones de implementación más comunes y puede responder a preguntas durante el proceso. Si desea autoayuda o la orientación de un partner, use la [Guía de instalación de Office 365](https://support.office.com/article/Set-up-Office-365-for-business-6a3a29a0-e616-4713-99d1-15eda62d04fa), nuestros [asistentes para la instalación de Office 365](https://aka.ms/o365fasttrack), o [busque un partner cualificado](https://partnercenter.microsoft.com/en-us/pcv/search).</span><span class="sxs-lookup"><span data-stu-id="6ab47-p103">Office 365 **[FastTrack](https://docs.microsoft.com/fasttrack)** is the best method for deploying Office 365. FastTrack guides you through the most common deployment configurations and can answer questions along the way. If you want to self-help or guidance from a partner, use our [Office 365 setup guide](https://support.office.com/article/Set-up-Office-365-for-business-6a3a29a0-e616-4713-99d1-15eda62d04fa), our [Office 365 setup wizards](https://aka.ms/o365fasttrack), or [find a qualified partner](https://partnercenter.microsoft.com/en-us/pcv/search).</span></span>

## <a name="self-deployment-of-office-365"></a><span data-ttu-id="6ab47-113">Implantación de Office 365 sin ayuda</span><span class="sxs-lookup"><span data-stu-id="6ab47-113">Self-deployment of Office 365</span></span>
<span data-ttu-id="6ab47-114">Si desea implementar Office 365 por su cuenta, los siguientes pasos pueden servirle de ayuda.</span><span class="sxs-lookup"><span data-stu-id="6ab47-114">If you want to deploy Office 365 on your own, the following deployment steps are here to help.</span></span>

1. <span data-ttu-id="6ab47-p104">**[Prepararse para Office 365](get-your-organization-ready-for-office-365.md)**. Estas herramientas y recursos le servirán de ayuda para preparar la red, el directorio y los usuarios finales para Office 365.</span><span class="sxs-lookup"><span data-stu-id="6ab47-p104">**[Get ready for Office 365](get-your-organization-ready-for-office-365.md)**. These tools and resources will help you get your network, directory, and end users ready for Office 365.</span></span>

2. <span data-ttu-id="6ab47-117">**Inicie sesión y agregue sus dominios de Internet a Office 365**.</span><span class="sxs-lookup"><span data-stu-id="6ab47-117">**Sign in and add your internet domain(s) to Office 365**.</span></span> <span data-ttu-id="6ab47-118">Inicie sesión en el [centro de administración de 365 de Microsoft](https://portal.microsoft.com), haga clic en **configurar > dominios**y, a continuación, haga clic en **nuevo dominio**.</span><span class="sxs-lookup"><span data-stu-id="6ab47-118">Sign into the [Microsoft 365 admin center](https://portal.microsoft.com), click **Setup > Domains**, and then click **New domain**.</span></span> <span data-ttu-id="6ab47-119">Agregue uno o más dominios a su suscripción de Office 365 sin agregar usuarios o migrar correo electrónico.</span><span class="sxs-lookup"><span data-stu-id="6ab47-119">Add one or more domains to your Office 365 subscription without adding users or migrating email.</span></span> 

>[!IMPORTANT] 
><span data-ttu-id="6ab47-120">Las instrucciones básicas de configuración no funcionarán si desea sincronizar los usuarios desde un directorio local o usar un inicio de sesión único.</span><span class="sxs-lookup"><span data-stu-id="6ab47-120">The basic set up instructions won't work if you want to synchronize your users from an on-premises directory or utilize Single Sign-On.</span></span>

3. <span data-ttu-id="6ab47-p106">**[Conectar el directorio a Office 365](about-office-365-identity.md)**. Guía para las opciones de configuración de sincronización de identidades y/o el inicio de sesión único. Use el [asesor de AAD Connect](https://aka.ms/aadconnectpwsync) y la [Guía de configuración de Azure AD Premium](https://aka.ms/aadpguidance) para obtener instrucciones de configuración personalizadas.</span><span class="sxs-lookup"><span data-stu-id="6ab47-p106">**[Connect your directory to Office 365](about-office-365-identity.md)**. Guide to the identity synchronization and/or single sign-on configuration options. Use the [AAD Connect advisor](https://aka.ms/aadconnectpwsync) and the [Azure AD Premium setup guide](https://aka.ms/aadpguidance) to get customized set up guidance.</span></span>
4. <span data-ttu-id="6ab47-p107">**[Configurar las aplicaciones y los servicios de Office 365](configure-services-and-applications.md)**. Empiece aquí para configurar el correo electrónico, el uso compartido de archivos, la mensajería instantánea o cualquier otro servicio o aplicación de Office 365.</span><span class="sxs-lookup"><span data-stu-id="6ab47-p107">**[Configure Office 365 services and applications](configure-services-and-applications.md)**. Start here to configure email, file sharing, instant messaging, or any of the other Office 365 services and applications.</span></span>
5. <span data-ttu-id="6ab47-p108">**[Migrar datos a Office 365](migrate-data-to-office-365.md)**. Una vez que los servicios estén configurados, podrá empezar a migrar los datos.</span><span class="sxs-lookup"><span data-stu-id="6ab47-p108">**[Migrate data to Office 365](migrate-data-to-office-365.md)**. Once the services are configured, you can start migrating data.</span></span>
6. <span data-ttu-id="6ab47-p109">**[Ayudar a los usuarios con Office 365](https://support.office.com/article/Get-started-with-Office-365-for-business-d6466f0d-5d13-464a-adcb-00906ae87029)**. Ayude a los usuarios de su organización a familiarizarse con Office 365 mediante estos recursos.</span><span class="sxs-lookup"><span data-stu-id="6ab47-p109">**[Get people using Office 365](https://support.office.com/article/Get-started-with-Office-365-for-business-d6466f0d-5d13-464a-adcb-00906ae87029)**. Help people in your organization build confidence using Office 365 with these resources.</span></span>