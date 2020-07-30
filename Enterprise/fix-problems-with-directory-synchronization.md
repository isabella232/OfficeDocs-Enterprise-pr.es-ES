---
title: Solucionar problemas de la sincronización de directorios para Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Priority
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: Describe las causas comunes de problemas con la sincronización de directorios en Office 365 y ofrece unos cuantos métodos para ayudar a identificarlos y resolverlos.
ms.openlocfilehash: fac0c477f3c68271a2f0f8c4e2a09fc051fe1ce4
ms.sourcegitcommit: d9abb99b336170f07b8f3f6d00fac19ad2159d3a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/28/2020
ms.locfileid: "46502655"
---
# <a name="fixing-problems-with-directory-synchronization-for-microsoft-365"></a><span data-ttu-id="55395-103">Solucionar problemas de la sincronización de directorios para Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="55395-103">Fixing problems with directory synchronization for Microsoft 365</span></span>

<span data-ttu-id="55395-104">La sincronización de directorios permite continuar con la administración de usuarios y grupos en una implementación local y sincronizar las adiciones, las eliminaciones y los cambios en la nube.</span><span class="sxs-lookup"><span data-stu-id="55395-104">With directory synchronization, you can continue to manage users and groups on-premises and synchronize additions, deletions, and changes to the cloud.</span></span> <span data-ttu-id="55395-105">Pero la configuración es algo complicada y en ocasiones puede resultar difícil identificar el origen de los problemas.</span><span class="sxs-lookup"><span data-stu-id="55395-105">But setup is a little complicated and it can sometimes be difficult to identify the source of problems.</span></span> <span data-ttu-id="55395-106">Contamos con los recursos para ayudarle a identificar posibles problemas y a resolverlos.</span><span class="sxs-lookup"><span data-stu-id="55395-106">We have resources to help you identify potential issues and fix them.</span></span>
  
## <a name="how-do-i-know-if-something-is-wrong"></a><span data-ttu-id="55395-107">¿Cómo puedo saber si algo va mal?</span><span class="sxs-lookup"><span data-stu-id="55395-107">How do I know if something is wrong?</span></span>

<span data-ttu-id="55395-108">La primera indicación que algo va mal es cuando el icono del estado de DirSync en el centro de administración de Microsoft 365 indica que hay un problema.</span><span class="sxs-lookup"><span data-stu-id="55395-108">The first indication that something is wrong is when the DirSync Status tile in the Microsoft 365 admin center indicates there is a problem.</span></span>
  
<span data-ttu-id="55395-109">También recibirá un correo de Microsoft 365 (al correo electrónico alternativo y al correo electrónico de administrador) que indica que su inquilino ha detectado errores de sincronización de directorios.</span><span class="sxs-lookup"><span data-stu-id="55395-109">You will also receive a mail (to the alternate email and to your admin email) from Microsoft 365 that indicates your tenant has encountered directory synchronization errors.</span></span> <span data-ttu-id="55395-110">Para obtener información detallada, vea [Identificar errores de sincronización de directorios en Microsoft 365](identify-directory-synchronization-errors.md).</span><span class="sxs-lookup"><span data-stu-id="55395-110">For details see [Identify directory synchronization errors in Microsoft 365](identify-directory-synchronization-errors.md).</span></span>
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a><span data-ttu-id="55395-111">¿Cómo puedo obtener la herramienta Azure Active Directory Connect?</span><span class="sxs-lookup"><span data-stu-id="55395-111">How do I get Azure Active Directory Connect tool?</span></span>

<span data-ttu-id="55395-112">En el [Centro de administración de Microsoft 365](https://admin.microsoft.com), vaya a **Usuarios** \> **Usuarios activos**.</span><span class="sxs-lookup"><span data-stu-id="55395-112">In the [Microsoft 365 admin center](https://admin.microsoft.com), navigate to **Users** \> **Active users**.</span></span> <span data-ttu-id="55395-113">Haga clic en el menú **Más** (puntos suspensivos) y seleccione **Sincronización de directorios**.</span><span class="sxs-lookup"><span data-stu-id="55395-113">Click the **More** menu (three dots) and select **Directory synchronization**.</span></span> 
  
<span data-ttu-id="55395-114">Siga las [instrucciones del asistente](set-up-directory-synchronization.md) para descargar Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="55395-114">Follow the [instructions in the wizard](set-up-directory-synchronization.md) to download Azure AD Connect.</span></span> 
  
<span data-ttu-id="55395-115">Si todavía está usando la sincronización (DirSync) de Azure Active Directory (Azure AD), eche un vistazo a [Cómo solucionar los problemas de instalación de la herramienta de sincronización de Azure Active Directory y de los mensajes de error del asistente de configuración en Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) para obtener información sobre los requisitos del sistema para instalar dirsync, los permisos que necesita y cómo solucionar los errores comunes.</span><span class="sxs-lookup"><span data-stu-id="55395-115">If you are still using Azure Active Directory (Azure AD) Sync (DirSync), take a look at [How to troubleshoot Azure Active Directory Sync Tool installation and Configuration Wizard error messages in Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) for information about the system requirements to install dirsync, the permissions you need, and how to troubleshoot common errors.</span></span> 
  
<span data-ttu-id="55395-116">Para actualizar desde la sincronización de Azure AD a Azure AD Connect, vea [las instrucciones de actualización](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span><span class="sxs-lookup"><span data-stu-id="55395-116">To update from Azure AD Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-microsoft-365"></a><span data-ttu-id="55395-117">Resolver causas comunes de los problemas de la sincronización de directorios de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="55395-117">Resolving common causes of problems with directory synchronization in Microsoft 365</span></span>

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a><span data-ttu-id="55395-118">Los objetos sincronizados no aparecen o no se actualizan en línea, o recibo informes de errores de sincronización del servicio.</span><span class="sxs-lookup"><span data-stu-id="55395-118">Synchronized objects aren't appearing or updating online, or I'm getting synchronization error reports from the Service.</span></span>

- [<span data-ttu-id="55395-119">Resistencia de atributo duplicado y sincronización de identidad</span><span class="sxs-lookup"><span data-stu-id="55395-119">Identity synchronization and duplicate attribute resiliency</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a><span data-ttu-id="55395-120">Tengo una alerta en el centro de administración o recibo correos electrónicos automatizados que indican que no ha habido ningún evento de sincronización reciente</span><span class="sxs-lookup"><span data-stu-id="55395-120">I have an alert in the admin center, or am receiving automated emails that there hasn't been a recent synchronization event</span></span>
- [<span data-ttu-id="55395-121">Solucionar problemas de conectividad con Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="55395-121">Troubleshoot connectivity issues with Azure AD Connect</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [<span data-ttu-id="55395-122">Cuentas y permisos de Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="55395-122">Azure AD Connect Accounts and permissions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [<span data-ttu-id="55395-123">Sincronización de Azure AD Connect: Cómo administrar la cuenta de servicio de Azure AD</span><span class="sxs-lookup"><span data-stu-id="55395-123">Azure AD Connect sync: How to manage the Azure AD service account</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [<span data-ttu-id="55395-124">La sincronización de directorios con Azure Active Directory se detiene o le advierte que la sincronización no se ha registrado en más de un día</span><span class="sxs-lookup"><span data-stu-id="55395-124">Directory synchronization to Azure Active Directory stops or you're warned that sync hasn't registered in more than a day</span></span>](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a><span data-ttu-id="55395-125">Los hash de contraseñas no se sincronizan o veo una alerta en el centro de administración que indica que no ha habido ninguna sincronización de los hash de contraseñas reciente</span><span class="sxs-lookup"><span data-stu-id="55395-125">Password hashes aren't synchronizing, or I'm seeing an alert in the admin center that there hasn't been a recent password hash synchronization</span></span>
- [<span data-ttu-id="55395-126">Implementar la sincronización de hash de contraseñas con la sincronización de Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="55395-126">Implementing password hash synchronization with Azure AD Connect sync</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a><span data-ttu-id="55395-127">Veo una alerta que indica que se ha superado la cuota de objetos</span><span class="sxs-lookup"><span data-stu-id="55395-127">I'm seeing an alert that Object quota exceeded</span></span>
- <span data-ttu-id="55395-128">Se aplica una cuota de objetos integrada para ayudar a proteger el servicio.</span><span class="sxs-lookup"><span data-stu-id="55395-128">We have a built-in object quota to help protect the service.</span></span> <span data-ttu-id="55395-129">Si en su directorio hay demasiados objetos deben sincronizarse en Microsoft 365, [Póngase en contacto con soporte técnico para productos para empresas](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) para aumentar la cuota.</span><span class="sxs-lookup"><span data-stu-id="55395-129">If you have too many objects in your directory that need to sync to Microsoft 365, you'll have to [Contact support for business products](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) to increase your quota.</span></span>

### <a name="i-need-to-know-which-attributes-are-synchronized"></a><span data-ttu-id="55395-130">Necesito saber qué atributos están sincronizados</span><span class="sxs-lookup"><span data-stu-id="55395-130">I need to know which attributes are synchronized</span></span>
- <span data-ttu-id="55395-131">Puede ver una lista de todos los atributos sincronizados entre la instalación local y la nube [aquí](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span><span class="sxs-lookup"><span data-stu-id="55395-131">You can find a list of all the attributes that are synced between on-premises and the cloud [right here](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a><span data-ttu-id="55395-132">No puedo administrar o quitar objetos sincronizados con la nube</span><span class="sxs-lookup"><span data-stu-id="55395-132">I can't manage or remove objects that were synchronized to the cloud</span></span>
- <span data-ttu-id="55395-133">¿Está listo para administrar objetos en la nube exclusivamente?</span><span class="sxs-lookup"><span data-stu-id="55395-133">Are you ready to manage objects in the cloud only?</span></span> <span data-ttu-id="55395-134">¿O un objeto que se eliminó en la implementación local ha quedado atascado en la nube?</span><span class="sxs-lookup"><span data-stu-id="55395-134">Or is there an object that was deleted on-premises, but is stuck in the cloud?</span></span> <span data-ttu-id="55395-135">Eche un vistazo a [Solución de problemas de errores durante la sincronización](https://go.microsoft.com/fwlink/p/?linkid=842044) y [artículo de soporte técnico](https://go.microsoft.com/fwlink/p/?LinkId=396720) para obtener instrucciones sobre cómo resolver estos problemas.</span><span class="sxs-lookup"><span data-stu-id="55395-135">Take a look at this [Troubleshooting Errors during synchronization](https://go.microsoft.com/fwlink/p/?linkid=842044) and [support article](https://go.microsoft.com/fwlink/p/?LinkId=396720) for guidance on how to resolve these issues.</span></span>

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a><span data-ttu-id="55395-136">Un mensaje de error indica que mi compañía ha excedido el número de objetos que se pueden sincronizar</span><span class="sxs-lookup"><span data-stu-id="55395-136">I got an error message that my company has exceeded the number of objects that can be synchronized</span></span>
- <span data-ttu-id="55395-137">Puede leer más sobre este problema [aquí](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span><span class="sxs-lookup"><span data-stu-id="55395-137">You can read more about this issue [here](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span></span>
   
## <a name="other-resources"></a><span data-ttu-id="55395-138">Otros recursos</span><span class="sxs-lookup"><span data-stu-id="55395-138">Other resources</span></span>

- [<span data-ttu-id="55395-139">Script para corregir los nombres principales de usuario duplicados</span><span class="sxs-lookup"><span data-stu-id="55395-139">Script to fix duplicate user principal names</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [<span data-ttu-id="55395-140">Cómo preparar un dominio no enrutable (por ejemplo, el dominio local) para la sincronización de directorios</span><span class="sxs-lookup"><span data-stu-id="55395-140">How to prepare a non-routable domain (such as .local domain) for directory synchronization</span></span>](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [<span data-ttu-id="55395-141">Script para contar el total de objetos sincronizados</span><span class="sxs-lookup"><span data-stu-id="55395-141">Script to count total synchronized objects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [<span data-ttu-id="55395-142">Solución de problemas de AD FS 2.0</span><span class="sxs-lookup"><span data-stu-id="55395-142">Troubleshoot AD FS 2.0</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [<span data-ttu-id="55395-143">Usar PowerShell para corregir atributos DisplayName vacíos de grupos habilitados para correo</span><span class="sxs-lookup"><span data-stu-id="55395-143">Use PowerShell to fix empty DisplayName attributes for mail-enabled groups</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [<span data-ttu-id="55395-144">Usar PowerShell para corregir UPN duplicados</span><span class="sxs-lookup"><span data-stu-id="55395-144">Use PowerShell to fix duplicate UPN</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [<span data-ttu-id="55395-145">Usar PowerShell para corregir direcciones de correo duplicadas</span><span class="sxs-lookup"><span data-stu-id="55395-145">Use PowerShell to fix duplicate email addresses</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a><span data-ttu-id="55395-146">Herramientas de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="55395-146">Diagnostic tools</span></span>

<span data-ttu-id="55395-147">[La herramienta IDFix](prepare-directory-attributes-for-synch-with-idfix.md) se usa para realizar detecciones y correcciones de objetos de identidad y de sus atributos en entornos de Active Directory locales en la preparación para la migración a Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="55395-147">[IDFix tool](prepare-directory-attributes-for-synch-with-idfix.md) is used to perform discovery and remediation of identity objects and their attributes in an on-premises Active Directory environment in preparation for migration to Microsoft 365.</span></span> <span data-ttu-id="55395-148">IDFix está pensado para los administradores de Active Directory responsables de la sincronización de directorios con el servicio de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="55395-148">IDFix is intended for the Active Directory administrators responsible for directory synchronization with the Microsoft 365 service.</span></span> 

<span data-ttu-id="55395-149">[Descargue la herramienta IDFix](https://go.microsoft.com/fwlink/p/?LinkId=396718) desde el centro de descarga de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="55395-149">[Download the IDFix tool](https://go.microsoft.com/fwlink/p/?LinkId=396718) from the Microsoft download center.</span></span>
