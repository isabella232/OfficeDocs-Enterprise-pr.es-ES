---
title: Solucionar problemas de la sincronización de directorios para Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: Describe las causas comunes de los problemas con la sincronización de directorios en Office 365 y proporciona algunos métodos para ayudar a solucionar problemas y resolverlos.
ms.openlocfilehash: e83ca495ca96ac41fb2f79775c3d5970a6b538fb
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085399"
---
# <a name="fixing-problems-with-directory-synchronization-for-office-365"></a><span data-ttu-id="26584-103">Solucionar problemas de la sincronización de directorios para Office 365</span><span class="sxs-lookup"><span data-stu-id="26584-103">Fixing problems with directory synchronization for Office 365</span></span>

<span data-ttu-id="26584-p101">Con la sincronización de directorios, puede seguir Administrando usuarios y grupos locales y sincronizar adiciones, eliminaciones y cambios en la nube. Pero la configuración es un poco complicada y a veces puede ser difícil identificar el origen de los problemas. Tenemos recursos para ayudarle a identificar posibles problemas y solucionarlos.</span><span class="sxs-lookup"><span data-stu-id="26584-p101">With directory synchronization, you can continue to manage users and groups on-premises and synchronize additions, deletions, and changes to the cloud. But setup is a little complicated and it can sometimes be difficult to identify the source of problems. We have resources to help you identify potential issues and fix them.</span></span>
  
## <a name="how-do-i-know-if-something-is-wrong"></a><span data-ttu-id="26584-107">¿Cómo sé si algo es incorrecto?</span><span class="sxs-lookup"><span data-stu-id="26584-107">How do I know if something is wrong?</span></span>

<span data-ttu-id="26584-108">La primera indicación de que algo es incorrecto es cuando el icono Estado de sincronización de directorios del centro de administración de Office 365 indica que hay un problema:</span><span class="sxs-lookup"><span data-stu-id="26584-108">The first indication that something is wrong is when the DirSync Status tile in the Office 365 admin center indicates there is a problem:</span></span>
  
![Icono de estado de sincronización de directorios de la versión preliminar del centro de administración](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
<span data-ttu-id="26584-p102">También recibirá un mensaje de correo (para el correo electrónico alternativo y el correo electrónico de administrador) de Office 365 que indica que el inquilino ha encontrado errores de sincronización de directorios. Para obtener información detallada, vea [identificar errores de sincronización de directorios en Office 365](identify-directory-synchronization-errors.md).</span><span class="sxs-lookup"><span data-stu-id="26584-p102">You will also receive a mail (to the alternate email and to your admin email) from Office 365 that indicates your tenant has encountered directory synchronization errors. For details see [Identify directory synchronization errors in Office 365](identify-directory-synchronization-errors.md).</span></span>
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a><span data-ttu-id="26584-112">¿Cómo obtengo la herramienta Azure Active Directory Connect?</span><span class="sxs-lookup"><span data-stu-id="26584-112">How do I get Azure Active Directory Connect tool?</span></span>

<span data-ttu-id="26584-p103">en el centro de administración de Office 365, vaya a \* \* usuarios \> \* \* **usuarios activos**. Haga clic en el menú **más** y seleccione **sincronización de directorios**.</span><span class="sxs-lookup"><span data-stu-id="26584-p103">In the Office 365 admin center, navigate to \*\* Users \*\* \> **Active users**. Click the **More** menu and select **Directory synchronization**.</span></span> 
  
![En el menú más, elija sincronización de directorios.](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
<span data-ttu-id="26584-116">en el antiguo centro de administración de Office 365, vaya a **usuarios** \> **activos**y seleccione **configurar** junto a **sincronización de Active**directory.</span><span class="sxs-lookup"><span data-stu-id="26584-116">In the old Office 365 admin center, navigate to **USERS** \> **Active Users**, and select **Set up** next to **Active Directory synchronization**.</span></span> 
  
![Elija configurar junto a sincronización de Active Directory](media/bd95492b-d65e-4072-a6ee-e562f5f566c3.png)
  
<span data-ttu-id="26584-118">Siga las [instrucciones del asistente](set-up-directory-synchronization.md) para descargar Azure ad Connect.</span><span class="sxs-lookup"><span data-stu-id="26584-118">Follow the [instructions in the wizard](set-up-directory-synchronization.md) to download Azure AD Connect.</span></span> 
  
<span data-ttu-id="26584-119">Si sigue usando Azure Active Directory Sync (dirSync), eche un vistazo a [cómo solucionar problemas de los mensajes de error del Asistente para la instalación y configuración de la herramienta de sincronización de Azure Active Directory en Office 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) para obtener información sobre los requisitos del sistema para instalar. DirSync, los permisos que necesita y cómo solucionar errores comunes.</span><span class="sxs-lookup"><span data-stu-id="26584-119">If you are still using Azure Active Directory Sync (DirSync), take a look at [How to troubleshoot Azure Active Directory Sync Tool installation and Configuration Wizard error messages in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) for information about the system requirements to install dirsync, the permissions you need, and how to troubleshoot common errors.</span></span> 
  
<span data-ttu-id="26584-120">Para actualizar desde Azure Active Directory Sync a Azure AD Connect, consulte [las instrucciones de actualización](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span><span class="sxs-lookup"><span data-stu-id="26584-120">To update from Azure Active Directory Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-office-365"></a><span data-ttu-id="26584-121">Resolver las causas comunes de los problemas con la sincronización de directorios en Office 365</span><span class="sxs-lookup"><span data-stu-id="26584-121">Resolving common causes of problems with directory synchronization in Office 365</span></span>

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a><span data-ttu-id="26584-122">**Los objetos sincronizados no aparecen o no se actualizan en línea, o bien se obtienen informes de errores de sincronización del servicio.**</span><span class="sxs-lookup"><span data-stu-id="26584-122">**Synchronized objects aren't appearing or updating online, or I'm getting synchronization error reports from the Service.**</span></span>

- [<span data-ttu-id="26584-123">Resistencia de sincronización de identidades y atributos duplicados</span><span class="sxs-lookup"><span data-stu-id="26584-123">Identity synchronization and duplicate attribute resiliency</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-office-365-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a><span data-ttu-id="26584-124">**Tengo una alerta en el centro de administración de Office 365 o estoy recibiendo correos electrónicos automatizados que no han habido un evento de sincronización reciente**</span><span class="sxs-lookup"><span data-stu-id="26584-124">**I have an alert in the Office 365 admin center, or am receiving automated emails that there hasn't been a recent synchronization event**</span></span>
- [<span data-ttu-id="26584-125">Solucionar problemas de conectividad con Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="26584-125">Troubleshoot connectivity issues with Azure AD Connect</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [<span data-ttu-id="26584-126">Cuentas y permisos de Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="26584-126">Azure AD Connect Accounts and permissions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [<span data-ttu-id="26584-127">Sincronización de Azure AD Connect: Cómo administrar la cuenta de servicio de Azure AD</span><span class="sxs-lookup"><span data-stu-id="26584-127">Azure AD Connect sync: How to manage the Azure AD service account</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [<span data-ttu-id="26584-128">Se detiene la sincronización de directorios en Azure Active Directory o se le advierte de que la sincronización no se ha registrado en más de un día</span><span class="sxs-lookup"><span data-stu-id="26584-128">Directory synchronization to Azure Active Directory stops or you're warned that sync hasn't registered in more than a day</span></span>](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-office-365-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a><span data-ttu-id="26584-129">**Los hash de contraseña no se sincronizan o veo una alerta en el centro de administración de Office 365 que indica que no había una sincronización de hash de contraseña reciente.**</span><span class="sxs-lookup"><span data-stu-id="26584-129">**Password hashes aren't synchronizing, or I'm seeing an alert in the Office 365 admin center that there hasn't been a recent password hash synchronization**</span></span>
- [<span data-ttu-id="26584-130">Implementación de la sincronización de hash de contraseña con Azure AD Connect Sync</span><span class="sxs-lookup"><span data-stu-id="26584-130">Implementing password hash synchronization with Azure AD Connect sync</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a><span data-ttu-id="26584-131">**Veo una alerta que indica que se ha superado la cuota de objetos**</span><span class="sxs-lookup"><span data-stu-id="26584-131">**I'm seeing an alert that Object quota exceeded**</span></span>
- <span data-ttu-id="26584-p104">Tenemos una cuota de objeto integrada para ayudar a proteger el servicio. Si tiene demasiados objetos en el directorio que deben sincronizarse con Office 365, deberá [ponerse en contacto con el soporte técnico para productos empresariales](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) para aumentar la cuota.</span><span class="sxs-lookup"><span data-stu-id="26584-p104">We have a built-in object quota to help protect the service. If you have too many objects in your directory that need to sync to Office 365, you'll have to [Contact support for business products](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) to increase your quota.</span></span>

### <a name="i-need-to-know-which-attributes-are-synchronized"></a><span data-ttu-id="26584-134">**Necesito saber cuáles son los atributos que se sincronizan**</span><span class="sxs-lookup"><span data-stu-id="26584-134">**I need to know which attributes are synchronized**</span></span>
- <span data-ttu-id="26584-135">Puede encontrar una lista de todos los atributos que se sincronizan entre el entorno local y la nube [aquí](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span><span class="sxs-lookup"><span data-stu-id="26584-135">You can find a list of all the attributes that are synced between on-premises and the cloud [right here](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a><span data-ttu-id="26584-136">**No puedo administrar o quitar objetos que se sincronizaron en la nube**</span><span class="sxs-lookup"><span data-stu-id="26584-136">**I can't manage or remove objects that were synchronized to the cloud**</span></span>
- <span data-ttu-id="26584-p105">¿Está preparado para administrar objetos solo en la nube? ¿O hay un objeto que se eliminó localmente pero está bloqueado en la nube? Eche un vistazo a este artículo sobre los [errores de solución de problemas durante la sincronización](https://go.microsoft.com/fwlink/p/?linkid=842044) y el artículo de [soporte técnico](https://go.microsoft.com/fwlink/p/?LinkId=396720) para obtener instrucciones sobre cómo resolver estos problemas.</span><span class="sxs-lookup"><span data-stu-id="26584-p105">Are you ready to manage objects in the cloud only? Or is there an object that was deleted on-premises, but is stuck in the cloud? Take a look at this [Troubleshooting Errors during synchronization](https://go.microsoft.com/fwlink/p/?linkid=842044) and [support article](https://go.microsoft.com/fwlink/p/?LinkId=396720) for guidance on how to resolve these issues.</span></span>

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a><span data-ttu-id="26584-140">**Un mensaje de error indica que mi compañía ha excedido el número de objetos que se pueden sincronizar**</span><span class="sxs-lookup"><span data-stu-id="26584-140">**I got an error message that my company has exceeded the number of objects that can be synchronized**</span></span>
- <span data-ttu-id="26584-141">Para obtener más información sobre este problema, vea [aquí](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span><span class="sxs-lookup"><span data-stu-id="26584-141">You can read more about this issue [here](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span></span>
   
## <a name="other-resources"></a><span data-ttu-id="26584-142">Otros recursos</span><span class="sxs-lookup"><span data-stu-id="26584-142">Other resources</span></span>

- [<span data-ttu-id="26584-143">Script para corregir los nombres principales de usuario duplicados</span><span class="sxs-lookup"><span data-stu-id="26584-143">Script to fix duplicate user principal names</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [<span data-ttu-id="26584-144">Cómo preparar un dominio no enrutable (como un dominio. local) para la sincronización de directorios</span><span class="sxs-lookup"><span data-stu-id="26584-144">How to prepare a non-routable domain (such as .local domain) for directory synchronization</span></span>](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [<span data-ttu-id="26584-145">Secuencia de comandos para contar objetos sincronizados totales</span><span class="sxs-lookup"><span data-stu-id="26584-145">Script to count total synchronized objects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [<span data-ttu-id="26584-146">Solución de problemas de AD FS 2,0</span><span class="sxs-lookup"><span data-stu-id="26584-146">Troubleshoot AD FS 2.0</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [<span data-ttu-id="26584-147">Usar PowerShell para corregir atributos DisplayName vacíos para grupos habilitados para correo</span><span class="sxs-lookup"><span data-stu-id="26584-147">Use PowerShell to fix empty DisplayName attributes for mail-enabled groups</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [<span data-ttu-id="26584-148">Usar PowerShell para corregir un UPN duplicado</span><span class="sxs-lookup"><span data-stu-id="26584-148">Use PowerShell to fix duplicate UPN</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [<span data-ttu-id="26584-149">Usar PowerShell para corregir direcciones de correo electrónico duplicadas</span><span class="sxs-lookup"><span data-stu-id="26584-149">Use PowerShell to fix duplicate email addresses</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a><span data-ttu-id="26584-150">Herramientas de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="26584-150">Diagnostic tools</span></span>

<span data-ttu-id="26584-p106">La [herramienta IDFix](prepare-directory-attributes-for-synch-with-idfix.md) se usa para realizar la detección y la corrección de objetos de identidad y sus atributos en un entorno local de Active Directory para preparar la migración a Office 365. IDFix está destinado a los administradores de Active Directory responsables de la sincronización de directorios con el servicio de Office 365.</span><span class="sxs-lookup"><span data-stu-id="26584-p106">[IDFix tool](prepare-directory-attributes-for-synch-with-idfix.md) is used to perform discovery and remediation of identity objects and their attributes in an on-premises Active Directory environment in preparation for migration to Office 365. IDFix is intended for the Active Directory administrators responsible for DirSync with the Office 365 service.</span></span> 

<span data-ttu-id="26584-153">[Descargue la herramienta IDFix](https://go.microsoft.com/fwlink/p/?LinkId=396718) desde el centro de descarga de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="26584-153">[Download the IDFix tool](https://go.microsoft.com/fwlink/p/?LinkId=396718) from the Microsoft download center.</span></span>