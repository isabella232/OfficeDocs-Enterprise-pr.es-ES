---
title: Solución de problemas con la sincronización de directorios para Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
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
ms.openlocfilehash: cc0fe15d0d49542489ac1e586efbe99d0846b3ab
ms.sourcegitcommit: fbd2f3fb297c508212baed3ee9d1ce51765cc8bb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/25/2019
ms.locfileid: "39254529"
---
# <a name="fixing-problems-with-directory-synchronization-for-office-365"></a><span data-ttu-id="1852a-103">Solución de problemas con la sincronización de directorios para Office 365</span><span class="sxs-lookup"><span data-stu-id="1852a-103">Fixing problems with directory synchronization for Office 365</span></span>

<span data-ttu-id="1852a-104">Con la sincronización de directorios, puede seguir Administrando usuarios y grupos locales y sincronizar adiciones, eliminaciones y cambios en la nube.</span><span class="sxs-lookup"><span data-stu-id="1852a-104">With directory synchronization, you can continue to manage users and groups on-premises and synchronize additions, deletions, and changes to the cloud.</span></span> <span data-ttu-id="1852a-105">Pero la configuración es un poco complicada y a veces puede ser difícil identificar el origen de los problemas.</span><span class="sxs-lookup"><span data-stu-id="1852a-105">But setup is a little complicated and it can sometimes be difficult to identify the source of problems.</span></span> <span data-ttu-id="1852a-106">Tenemos recursos para ayudarle a identificar posibles problemas y solucionarlos.</span><span class="sxs-lookup"><span data-stu-id="1852a-106">We have resources to help you identify potential issues and fix them.</span></span>
  
## <a name="how-do-i-know-if-something-is-wrong"></a><span data-ttu-id="1852a-107">¿Cómo sé si algo es incorrecto?</span><span class="sxs-lookup"><span data-stu-id="1852a-107">How do I know if something is wrong?</span></span>

<span data-ttu-id="1852a-108">La primera indicación de que algo es incorrecto es cuando el icono Estado de sincronización de directorios del centro de administración de Microsoft 365 indica que hay un problema.</span><span class="sxs-lookup"><span data-stu-id="1852a-108">The first indication that something is wrong is when the DirSync Status tile in the Microsoft 365 admin center indicates there is a problem.</span></span>
  
<span data-ttu-id="1852a-109">También recibirá un mensaje de correo (para el correo electrónico alternativo y el correo electrónico de administrador) de Office 365 que indica que el inquilino ha encontrado errores de sincronización de directorios.</span><span class="sxs-lookup"><span data-stu-id="1852a-109">You will also receive a mail (to the alternate email and to your admin email) from Office 365 that indicates your tenant has encountered directory synchronization errors.</span></span> <span data-ttu-id="1852a-110">Para obtener información detallada, vea [identificar errores de sincronización de directorios en Office 365](identify-directory-synchronization-errors.md).</span><span class="sxs-lookup"><span data-stu-id="1852a-110">For details see [Identify directory synchronization errors in Office 365](identify-directory-synchronization-errors.md).</span></span>
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a><span data-ttu-id="1852a-111">¿Cómo obtengo la herramienta Azure Active Directory Connect?</span><span class="sxs-lookup"><span data-stu-id="1852a-111">How do I get Azure Active Directory Connect tool?</span></span>

<span data-ttu-id="1852a-112">En el [centro de administración de Microsoft 365](https://admin.microsoft.com), vaya a **usuarios** \> **activos**.</span><span class="sxs-lookup"><span data-stu-id="1852a-112">In the [Microsoft 365 admin center](https://admin.microsoft.com), navigate to **Users** \> **Active users**.</span></span> <span data-ttu-id="1852a-113">Haga clic en el menú **más** (tres puntos) y seleccione **sincronización de directorios**.</span><span class="sxs-lookup"><span data-stu-id="1852a-113">Click the **More** menu (three dots) and select **Directory synchronization**.</span></span> 
  
<span data-ttu-id="1852a-114">Siga las [instrucciones del asistente](set-up-directory-synchronization.md) para descargar Azure ad Connect.</span><span class="sxs-lookup"><span data-stu-id="1852a-114">Follow the [instructions in the wizard](set-up-directory-synchronization.md) to download Azure AD Connect.</span></span> 
  
<span data-ttu-id="1852a-115">Si sigue usando Azure Active Directory Sync (DirSync), eche un vistazo a [cómo solucionar problemas de los mensajes de error del Asistente para la instalación y configuración de la herramienta de sincronización de Azure Active Directory en Office 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) para obtener información acerca de los requisitos del sistema para instalar DirSync, los permisos necesarios y cómo solucionar errores comunes.</span><span class="sxs-lookup"><span data-stu-id="1852a-115">If you are still using Azure Active Directory Sync (DirSync), take a look at [How to troubleshoot Azure Active Directory Sync Tool installation and Configuration Wizard error messages in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) for information about the system requirements to install dirsync, the permissions you need, and how to troubleshoot common errors.</span></span> 
  
<span data-ttu-id="1852a-116">Para actualizar desde Azure Active Directory Sync a Azure AD Connect, consulte [las instrucciones de actualización](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span><span class="sxs-lookup"><span data-stu-id="1852a-116">To update from Azure Active Directory Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-office-365"></a><span data-ttu-id="1852a-117">Resolver las causas comunes de los problemas con la sincronización de directorios en Office 365</span><span class="sxs-lookup"><span data-stu-id="1852a-117">Resolving common causes of problems with directory synchronization in Office 365</span></span>

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a><span data-ttu-id="1852a-118">**Los objetos sincronizados no aparecen o no se actualizan en línea, o bien se obtienen informes de errores de sincronización del servicio.**</span><span class="sxs-lookup"><span data-stu-id="1852a-118">**Synchronized objects aren't appearing or updating online, or I'm getting synchronization error reports from the Service.**</span></span>

- [<span data-ttu-id="1852a-119">Resistencia de sincronización de identidades y atributos duplicados</span><span class="sxs-lookup"><span data-stu-id="1852a-119">Identity synchronization and duplicate attribute resiliency</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a><span data-ttu-id="1852a-120">**Tengo una alerta en el centro de administración o estoy recibiendo correos electrónicos automatizados que no han habido un evento de sincronización reciente**</span><span class="sxs-lookup"><span data-stu-id="1852a-120">**I have an alert in the admin center, or am receiving automated emails that there hasn't been a recent synchronization event**</span></span>
- [<span data-ttu-id="1852a-121">Solucionar problemas de conectividad con Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="1852a-121">Troubleshoot connectivity issues with Azure AD Connect</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [<span data-ttu-id="1852a-122">Cuentas y permisos de Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="1852a-122">Azure AD Connect Accounts and permissions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [<span data-ttu-id="1852a-123">Sincronización de Azure AD Connect: Cómo administrar la cuenta de servicio de Azure AD</span><span class="sxs-lookup"><span data-stu-id="1852a-123">Azure AD Connect sync: How to manage the Azure AD service account</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [<span data-ttu-id="1852a-124">Se detiene la sincronización de directorios en Azure Active Directory o se le advierte de que la sincronización no se ha registrado en más de un día</span><span class="sxs-lookup"><span data-stu-id="1852a-124">Directory synchronization to Azure Active Directory stops or you're warned that sync hasn't registered in more than a day</span></span>](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a><span data-ttu-id="1852a-125">**Los hash de contraseña no se sincronizan o veo una alerta en el centro de administración que indica que no había una sincronización de hash de contraseña reciente.**</span><span class="sxs-lookup"><span data-stu-id="1852a-125">**Password hashes aren't synchronizing, or I'm seeing an alert in the admin center that there hasn't been a recent password hash synchronization**</span></span>
- [<span data-ttu-id="1852a-126">Implementación de la sincronización de hash de contraseña con Azure AD Connect Sync</span><span class="sxs-lookup"><span data-stu-id="1852a-126">Implementing password hash synchronization with Azure AD Connect sync</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a><span data-ttu-id="1852a-127">**Veo una alerta que indica que se ha superado la cuota de objetos**</span><span class="sxs-lookup"><span data-stu-id="1852a-127">**I'm seeing an alert that Object quota exceeded**</span></span>
- <span data-ttu-id="1852a-128">Tenemos una cuota de objeto integrada para ayudar a proteger el servicio.</span><span class="sxs-lookup"><span data-stu-id="1852a-128">We have a built-in object quota to help protect the service.</span></span> <span data-ttu-id="1852a-129">Si tiene demasiados objetos en el directorio que deben sincronizarse con Office 365, deberá [ponerse en contacto con el soporte técnico para productos empresariales](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) para aumentar la cuota.</span><span class="sxs-lookup"><span data-stu-id="1852a-129">If you have too many objects in your directory that need to sync to Office 365, you'll have to [Contact support for business products](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) to increase your quota.</span></span>

### <a name="i-need-to-know-which-attributes-are-synchronized"></a><span data-ttu-id="1852a-130">**Necesito saber qué atributos se sincronizan**</span><span class="sxs-lookup"><span data-stu-id="1852a-130">**I need to know which attributes are synchronized**</span></span>
- <span data-ttu-id="1852a-131">Puede encontrar una lista de todos los atributos que se sincronizan entre el entorno local y la nube [aquí](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span><span class="sxs-lookup"><span data-stu-id="1852a-131">You can find a list of all the attributes that are synced between on-premises and the cloud [right here](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a><span data-ttu-id="1852a-132">**No puedo administrar o quitar objetos que se sincronizaron en la nube**</span><span class="sxs-lookup"><span data-stu-id="1852a-132">**I can't manage or remove objects that were synchronized to the cloud**</span></span>
- <span data-ttu-id="1852a-133">¿Está preparado para administrar objetos solo en la nube?</span><span class="sxs-lookup"><span data-stu-id="1852a-133">Are you ready to manage objects in the cloud only?</span></span> <span data-ttu-id="1852a-134">¿O hay un objeto que se eliminó localmente pero está bloqueado en la nube?</span><span class="sxs-lookup"><span data-stu-id="1852a-134">Or is there an object that was deleted on-premises, but is stuck in the cloud?</span></span> <span data-ttu-id="1852a-135">Eche un vistazo a este artículo sobre los [errores de solución de problemas durante la sincronización](https://go.microsoft.com/fwlink/p/?linkid=842044) y el artículo de [soporte técnico](https://go.microsoft.com/fwlink/p/?LinkId=396720) para obtener instrucciones sobre cómo resolver estos problemas.</span><span class="sxs-lookup"><span data-stu-id="1852a-135">Take a look at this [Troubleshooting Errors during synchronization](https://go.microsoft.com/fwlink/p/?linkid=842044) and [support article](https://go.microsoft.com/fwlink/p/?LinkId=396720) for guidance on how to resolve these issues.</span></span>

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a><span data-ttu-id="1852a-136">**He recibido un mensaje de error que indica que mi compañía ha superado el número de objetos que se pueden sincronizar**</span><span class="sxs-lookup"><span data-stu-id="1852a-136">**I got an error message that my company has exceeded the number of objects that can be synchronized**</span></span>
- <span data-ttu-id="1852a-137">Para obtener más información sobre este problema, vea [aquí](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span><span class="sxs-lookup"><span data-stu-id="1852a-137">You can read more about this issue [here](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span></span>
   
## <a name="other-resources"></a><span data-ttu-id="1852a-138">Otros recursos</span><span class="sxs-lookup"><span data-stu-id="1852a-138">Other resources</span></span>

- [<span data-ttu-id="1852a-139">Script para corregir los nombres principales de usuario duplicados</span><span class="sxs-lookup"><span data-stu-id="1852a-139">Script to fix duplicate user principal names</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [<span data-ttu-id="1852a-140">Cómo preparar un dominio no enrutable (como un dominio. local) para la sincronización de directorios</span><span class="sxs-lookup"><span data-stu-id="1852a-140">How to prepare a non-routable domain (such as .local domain) for directory synchronization</span></span>](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [<span data-ttu-id="1852a-141">Secuencia de comandos para contar objetos sincronizados totales</span><span class="sxs-lookup"><span data-stu-id="1852a-141">Script to count total synchronized objects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [<span data-ttu-id="1852a-142">Solución de problemas de AD FS 2,0</span><span class="sxs-lookup"><span data-stu-id="1852a-142">Troubleshoot AD FS 2.0</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [<span data-ttu-id="1852a-143">Usar PowerShell para corregir atributos DisplayName vacíos para grupos habilitados para correo</span><span class="sxs-lookup"><span data-stu-id="1852a-143">Use PowerShell to fix empty DisplayName attributes for mail-enabled groups</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [<span data-ttu-id="1852a-144">Usar PowerShell para corregir un UPN duplicado</span><span class="sxs-lookup"><span data-stu-id="1852a-144">Use PowerShell to fix duplicate UPN</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [<span data-ttu-id="1852a-145">Usar PowerShell para corregir direcciones de correo electrónico duplicadas</span><span class="sxs-lookup"><span data-stu-id="1852a-145">Use PowerShell to fix duplicate email addresses</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a><span data-ttu-id="1852a-146">Herramientas de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="1852a-146">Diagnostic tools</span></span>

<span data-ttu-id="1852a-147">La [herramienta IDFix](prepare-directory-attributes-for-synch-with-idfix.md) se usa para realizar la detección y la corrección de objetos de identidad y sus atributos en un entorno local de Active Directory para preparar la migración a Office 365.</span><span class="sxs-lookup"><span data-stu-id="1852a-147">[IDFix tool](prepare-directory-attributes-for-synch-with-idfix.md) is used to perform discovery and remediation of identity objects and their attributes in an on-premises Active Directory environment in preparation for migration to Office 365.</span></span> <span data-ttu-id="1852a-148">IDFix está destinado a los administradores de Active Directory responsables de la sincronización de directorios con el servicio de Office 365.</span><span class="sxs-lookup"><span data-stu-id="1852a-148">IDFix is intended for the Active Directory administrators responsible for directory synchronization with the Office 365 service.</span></span> 

<span data-ttu-id="1852a-149">[Descargue la herramienta IDFix](https://go.microsoft.com/fwlink/p/?LinkId=396718) desde el centro de descarga de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="1852a-149">[Download the IDFix tool](https://go.microsoft.com/fwlink/p/?LinkId=396718) from the Microsoft download center.</span></span>