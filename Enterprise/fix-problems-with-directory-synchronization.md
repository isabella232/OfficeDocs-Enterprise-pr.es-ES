---
title: Solucionar problemas de la sincronización de directorios para Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: Describe las causas habituales de problemas con la sincronización de directorios en Office 365 y proporciona algunos métodos para ayudar a solucionar y resolverlos conflictos.
ms.openlocfilehash: ad3b6e27439354a2ede9b1a4b100e0f9e06148d3
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542772"
---
# <a name="fixing-problems-with-directory-synchronization-for-office-365"></a><span data-ttu-id="7d645-103">Solucionar problemas de la sincronización de directorios para Office 365</span><span class="sxs-lookup"><span data-stu-id="7d645-103">Fixing problems with directory synchronization for Office 365</span></span>

<span data-ttu-id="7d645-p101">Con la sincronización de Active directory, puede continuar administrar usuarios y grupos locales y sincronizar las adiciones, eliminaciones y los cambios realizados en la nube. El programa de instalación es un poco complicado, pero a veces puede resultar difícil identificar el origen de los problemas. Disponemos de recursos que le ayudarán a identificar posibles problemas y solucionarlos.</span><span class="sxs-lookup"><span data-stu-id="7d645-p101">With directory synchronization, you can continue to manage users and groups on-premises and synchronize additions, deletions, and changes to the cloud. But setup is a little complicated and it can sometimes be difficult to identify the source of problems. We have resources to help you identify potential issues and fix them.</span></span>
  
## <a name="how-do-i-know-if-something-is-wrong"></a><span data-ttu-id="7d645-107">¿Cómo se puede saber si algo es incorrecta?</span><span class="sxs-lookup"><span data-stu-id="7d645-107">How do I know if something is wrong?</span></span>

<span data-ttu-id="7d645-108">La primera indicación de que algo es incorrecto es cuando el icono de estado de sincronización de directorios en el centro de administración de Office 365 indica que hay un problema:</span><span class="sxs-lookup"><span data-stu-id="7d645-108">The first indication that something is wrong is when the DirSync Status tile in the Office 365 admin center indicates there is a problem:</span></span>
  
![El estado de sincronización de directorios en mosaico en la vista previa del centro de administración](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
<span data-ttu-id="7d645-p102">También recibirá un correo (para el correo electrónico alternativo y a su correo electrónico de administración) de Office 365 que indica que el inquilino ha encontrado errores de sincronización de Active directory. Para obtener información detallada, vea [identificar errores de sincronización de Active directory en Office 365](identify-directory-synchronization-errors.md).</span><span class="sxs-lookup"><span data-stu-id="7d645-p102">You will also receive a mail (to the alternate email and to your admin email) from Office 365 that indicates your tenant has encountered directory synchronization errors. For details see [Identify directory synchronization errors in Office 365](identify-directory-synchronization-errors.md).</span></span>
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a><span data-ttu-id="7d645-112">¿Cómo se puede obtener herramienta conectar de Azure Active Directory?</span><span class="sxs-lookup"><span data-stu-id="7d645-112">How do I get Azure Active Directory Connect tool?</span></span>

<span data-ttu-id="7d645-p103">En el centro de administración de Office 365, vaya a ** usuarios ** \> **usuarios activos**. Haga clic en el menú **más** y seleccione la **sincronización de Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="7d645-p103">In the Office 365 admin center, navigate to ** Users ** \> **Active users**. Click the **More** menu and select **Directory synchronization**.</span></span> 
  
![En el menú más, elija la sincronización de directorios](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
<span data-ttu-id="7d645-116">En el centro de administración de Office 365 antiguo, vaya a **los usuarios** \> **Usuarios activos**y seleccione **Configurar** junto a **sincronización de Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="7d645-116">In the old Office 365 admin center, navigate to **USERS** \> **Active Users**, and select **Set up** next to **Active Directory synchronization**.</span></span> 
  
![Elija Configurar junto a sincronización de Active Directory](media/bd95492b-d65e-4072-a6ee-e562f5f566c3.png)
  
<span data-ttu-id="7d645-118">Siga las [instrucciones del asistente](set-up-directory-synchronization.md) para descargar Connect de Azure AD.</span><span class="sxs-lookup"><span data-stu-id="7d645-118">Follow the [instructions in the wizard](set-up-directory-synchronization.md) to download Azure AD Connect.</span></span> 
  
<span data-ttu-id="7d645-119">Si todavía está utilizando la sincronización de Azure Active Directory (DirSync), eche un vistazo a [cómo solucionar problemas de instalación de la herramienta de sincronización de Azure Active Directory y los mensajes de error del Asistente para la configuración en Office 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) para obtener información acerca de los requisitos del sistema para instalar sincronización de directorios, los permisos que necesita y cómo solucionar errores comunes.</span><span class="sxs-lookup"><span data-stu-id="7d645-119">If you are still using Azure Active Directory Sync (DirSync), take a look at [How to troubleshoot Azure Active Directory Sync Tool installation and Configuration Wizard error messages in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) for information about the system requirements to install dirsync, the permissions you need, and how to troubleshoot common errors.</span></span> 
  
<span data-ttu-id="7d645-120">Para actualizar desde la sincronización de Azure Active Directory a Azure Connect de AD, vea [las instrucciones de actualización](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span><span class="sxs-lookup"><span data-stu-id="7d645-120">To update from Azure Active Directory Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-office-365"></a><span data-ttu-id="7d645-121">Resolución de comunes causas de los problemas con la sincronización de directorios en Office 365</span><span class="sxs-lookup"><span data-stu-id="7d645-121">Resolving common causes of problems with directory synchronization in Office 365</span></span>

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a><span data-ttu-id="7d645-122">**Objetos sincronizados no aparezca o actualizar en línea u obtienen los informes de errores de sincronización desde el servicio.**</span><span class="sxs-lookup"><span data-stu-id="7d645-122">**Synchronized objects aren't appearing or updating online, or I'm getting synchronization error reports from the Service.**</span></span>

- [<span data-ttu-id="7d645-123">Resistencia de atributo de sincronización y duplicado de identidad</span><span class="sxs-lookup"><span data-stu-id="7d645-123">Identity synchronization and duplicate attribute resiliency</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=798300)

### <a name="i-have-an-alert-in-the-office-365-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a><span data-ttu-id="7d645-124">**Tener una alerta en el centro de administración de Office 365, o estoy recibiendo mensajes de correo electrónico automatizados que no ha habido un evento de sincronización recientes**</span><span class="sxs-lookup"><span data-stu-id="7d645-124">**I have an alert in the Office 365 admin center, or am receiving automated emails that there hasn't been a recent synchronization event**</span></span>
- [<span data-ttu-id="7d645-125">Solucionar problemas de conectividad con Azure Connect de AD</span><span class="sxs-lookup"><span data-stu-id="7d645-125">Troubleshoot connectivity issues with Azure AD Connect</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820597)
- [<span data-ttu-id="7d645-126">Permisos y cuentas de conexión de AD de Azure</span><span class="sxs-lookup"><span data-stu-id="7d645-126">Azure AD Connect Accounts and permissions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [<span data-ttu-id="7d645-127">Sincronización de Azure AD Connect: cómo administrar la cuenta de servicio de Azure AD</span><span class="sxs-lookup"><span data-stu-id="7d645-127">Azure AD Connect sync: How to manage the Azure AD service account</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820599)
- [<span data-ttu-id="7d645-128">Sincronización de directorios para deja de Azure Active Directory o se está le advierte que la sincronización no ha registrado en más de un día</span><span class="sxs-lookup"><span data-stu-id="7d645-128">Directory synchronization to Azure Active Directory stops or you're warned that sync hasn't registered in more than a day</span></span>](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-office-365-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a><span data-ttu-id="7d645-129">**No sincronización los hashes de contraseña u obtengo una alerta en el centro de administración de Office 365 que no ha habido una sincronización de hash de contraseña recientes**</span><span class="sxs-lookup"><span data-stu-id="7d645-129">**Password hashes aren't synchronizing, or I'm seeing an alert in the Office 365 admin center that there hasn't been a recent password hash synchronization**</span></span>
- [<span data-ttu-id="7d645-130">Implementación de la sincronización de hash de contraseña con la sincronización de Azure Connect de AD</span><span class="sxs-lookup"><span data-stu-id="7d645-130">Implementing password hash synchronization with Azure AD Connect sync</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820600)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a><span data-ttu-id="7d645-131">**Estoy viendo una alerta que se ha excedido la cuota de objeto**</span><span class="sxs-lookup"><span data-stu-id="7d645-131">**I'm seeing an alert that Object quota exceeded**</span></span>
- <span data-ttu-id="7d645-p104">Hemos desarrollado una cuota de objeto integrado para ayudar a proteger el servicio. Si tiene demasiados objetos en el directorio que se deben sincronizar con Office 365, tendrá que el [contacto de soporte para productos de negocio](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) para aumentar la cuota.</span><span class="sxs-lookup"><span data-stu-id="7d645-p104">We have a built-in object quota to help protect the service. If you have too many objects in your directory that need to sync to Office 365, you'll have to [Contact support for business products](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) to increase your quota.</span></span>

### <a name="i-need-to-know-which-attributes-are-synchronized"></a><span data-ttu-id="7d645-134">**Necesito saber cuáles son los atributos que se sincronizan**</span><span class="sxs-lookup"><span data-stu-id="7d645-134">**I need to know which attributes are synchronized**</span></span>
- <span data-ttu-id="7d645-135">Puede encontrar una lista de todos los atributos que se sincronizan entre local y la nube [derecha aquí](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span><span class="sxs-lookup"><span data-stu-id="7d645-135">You can find a list of all the attributes that are synced between on-premises and the cloud [right here](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a><span data-ttu-id="7d645-136">**No se puede administrar o quitar objetos que se han sincronizado a la nube**</span><span class="sxs-lookup"><span data-stu-id="7d645-136">**I can't manage or remove objects that were synchronized to the cloud**</span></span>
- <span data-ttu-id="7d645-p105">¿Está preparado para administrar objetos en la nube solo? ¿O bien, hay un objeto que fue eliminado local, pero se quedó en la nube? Eche un vistazo de esta [Solución de problemas de errores durante la sincronización](https://go.microsoft.com/fwlink/p/?linkid=842044) y el [artículo de soporte técnico](https://go.microsoft.com/fwlink/p/?LinkId=396720) para obtener instrucciones sobre cómo resolver estos problemas.</span><span class="sxs-lookup"><span data-stu-id="7d645-p105">Are you ready to manage objects in the cloud only? Or is there an object that was deleted on-premises, but is stuck in the cloud? Take a look at this [Troubleshooting Errors during synchronization](https://go.microsoft.com/fwlink/p/?linkid=842044) and [support article](https://go.microsoft.com/fwlink/p/?LinkId=396720) for guidance on how to resolve these issues.</span></span>

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a><span data-ttu-id="7d645-140">**Un mensaje de error indica que mi compañía ha excedido el número de objetos que se pueden sincronizar**</span><span class="sxs-lookup"><span data-stu-id="7d645-140">**I got an error message that my company has exceeded the number of objects that can be synchronized**</span></span>
- <span data-ttu-id="7d645-141">Puede leer más información acerca de este problema [aquí](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span><span class="sxs-lookup"><span data-stu-id="7d645-141">You can read more about this issue [here](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span></span>
   
## <a name="other-resources"></a><span data-ttu-id="7d645-142">Otros recursos</span><span class="sxs-lookup"><span data-stu-id="7d645-142">Other resources</span></span>

- [<span data-ttu-id="7d645-143">Secuencia de comandos para corregir nombres principales de usuario duplicados</span><span class="sxs-lookup"><span data-stu-id="7d645-143">Script to fix duplicate user principal names</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [<span data-ttu-id="7d645-144">Procedimiento para preparar un dominio no se puede enrutar (por ejemplo, el dominio local) para la sincronización de Active directory</span><span class="sxs-lookup"><span data-stu-id="7d645-144">How to prepare a non-routable domain (such as .local domain) for directory synchronization</span></span>](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [<span data-ttu-id="7d645-145">Script para contar el número total de objetos sincronizados</span><span class="sxs-lookup"><span data-stu-id="7d645-145">Script to count total synchronized objects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [<span data-ttu-id="7d645-146">Solución de problemas de AD FS 2.0</span><span class="sxs-lookup"><span data-stu-id="7d645-146">Troubleshoot AD FS 2.0</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [<span data-ttu-id="7d645-147">Uso de PowerShell para corregir los atributos DisplayName vacíos para grupos habilitados para correo</span><span class="sxs-lookup"><span data-stu-id="7d645-147">Use PowerShell to fix empty DisplayName attributes for mail-enabled groups</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [<span data-ttu-id="7d645-148">Uso de PowerShell para corregir UPN duplicado</span><span class="sxs-lookup"><span data-stu-id="7d645-148">Use PowerShell to fix duplicate UPN</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [<span data-ttu-id="7d645-149">Uso de PowerShell para corregir direcciones de correo electrónico duplicados</span><span class="sxs-lookup"><span data-stu-id="7d645-149">Use PowerShell to fix duplicate email addresses</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a><span data-ttu-id="7d645-150">Herramientas de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="7d645-150">Diagnostic tools</span></span>

<span data-ttu-id="7d645-p106">[Herramienta IDFix](prepare-directory-attributes-for-synch-with-idfix.md) se usa para llevar a cabo la detección y corrección de objetos de identidad y sus atributos en un entorno de Active Directory local en la preparación para la migración a Office 365. IDFix está pensado para los administradores de Active Directory responsables de la sincronización de directorios con el servicio de Office 365.</span><span class="sxs-lookup"><span data-stu-id="7d645-p106">[IDFix tool](prepare-directory-attributes-for-synch-with-idfix.md) is used to perform discovery and remediation of identity objects and their attributes in an on-premises Active Directory environment in preparation for migration to Office 365. IDFix is intended for the Active Directory administrators responsible for DirSync with the Office 365 service.</span></span> 

<span data-ttu-id="7d645-153">[Descargue la herramienta IDFix](https://go.microsoft.com/fwlink/p/?LinkId=396718) desde el centro de descarga de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="7d645-153">[Download the IDFix tool](https://go.microsoft.com/fwlink/p/?LinkId=396718) from the Microsoft download center.</span></span>