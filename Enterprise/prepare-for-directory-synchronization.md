---
title: Preparación para aprovisionar a los usuarios a través de la sincronización del directorio a Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Describe cómo preparar el aprovisionamiento de usuarios a Office 365 mediante la sincronización de directorios y las ventajas a largo plazo del uso de este método.
ms.openlocfilehash: af402950b3681285898d0d87b897d363a693bf98
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085109"
---
# <a name="prepare-to-provision-users-through-directory-synchronization-to-office-365"></a><span data-ttu-id="bdafe-103">Preparación para aprovisionar a los usuarios a través de la sincronización del directorio a Office 365</span><span class="sxs-lookup"><span data-stu-id="bdafe-103">Prepare to provision users through directory synchronization to Office 365</span></span>

<span data-ttu-id="bdafe-p101">El aprovisionamiento de usuarios con la sincronización de directorios requiere más planeación y preparación que simplemente administrar la cuenta profesional o educativa directamente en Office 365. Las tareas adicionales de planeación y preparación son necesarias para asegurarse de que la implementación local de Active Directory se sincroniza correctamente con Azure Active Directory. Entre las ventajas agregadas a su organización se incluyen:</span><span class="sxs-lookup"><span data-stu-id="bdafe-p101">Provisioning users with directory synchronization requires more planning and preparation than simply managing your work or school account directly in Office 365. The additional planning and preparation tasks are required to ensure that your on-premises Active Directory synchronizes properly to Azure Active Directory. The added benefits to your organization include:</span></span>
  
- <span data-ttu-id="bdafe-107">Reducción de los programas de administración de la organización</span><span class="sxs-lookup"><span data-stu-id="bdafe-107">Reducing the administrative programs in your organization</span></span>
- <span data-ttu-id="bdafe-108">Habilitar opcionalmente escenario de inicio de sesión único</span><span class="sxs-lookup"><span data-stu-id="bdafe-108">Optionally enabling single sign-on scenario</span></span>
- <span data-ttu-id="bdafe-109">Automatizar cambios de cuenta en Office 365</span><span class="sxs-lookup"><span data-stu-id="bdafe-109">Automating account changes in Office 365</span></span>
    
<span data-ttu-id="bdafe-110">Para obtener más información acerca de las ventajas del uso de la sincronización de directorios, vea el [mapa de ruta de sincronización de directorios]( https://go.microsoft.com/fwlink/p/?LinkId=525398) y la identidad de [Office 365 y Azure Active Directory](about-office-365-identity.md).</span><span class="sxs-lookup"><span data-stu-id="bdafe-110">For more information about the advantages of using directory synchronization, see [Directory synchronization roadmap]( https://go.microsoft.com/fwlink/p/?LinkId=525398) and [Understanding Office 365 Identity and Azure Active Directory](about-office-365-identity.md).</span></span>
  
<span data-ttu-id="bdafe-111">Para determinar qué escenario es el mejor para su organización, revise la [comparación](https://go.microsoft.com/fwlink/p/?LinkId=525320)de las herramientas de integración de directorios.</span><span class="sxs-lookup"><span data-stu-id="bdafe-111">To determine which scenario is the best for your organization, review the [directory integration tools comparison](https://go.microsoft.com/fwlink/p/?LinkId=525320).</span></span>
  
## <a name="directory-cleanup-tasks"></a><span data-ttu-id="bdafe-112">Tareas de limpieza de directorios</span><span class="sxs-lookup"><span data-stu-id="bdafe-112">Directory cleanup tasks</span></span>

<span data-ttu-id="bdafe-113">Antes de empezar a sincronizar el directorio, deberá limpiar su directorio.</span><span class="sxs-lookup"><span data-stu-id="bdafe-113">Before you begin synchronizing your directory, you need to clean up your directory.</span></span>
  
<span data-ttu-id="bdafe-114">Revise también los [atributos que Azure ad Connect ha sincronizado con Azure Active Directory](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized).</span><span class="sxs-lookup"><span data-stu-id="bdafe-114">Review also the [attributes synchronized to Azure Active Directory by Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized).</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="bdafe-p102">Si no realiza la limpieza del directorio antes de sincronizar, puede haber un efecto negativo significativo en el proceso de implementación. Puede tardar días, o incluso semanas, en pasar por el ciclo de sincronización de directorios, identificar errores y volver a sincronizar.</span><span class="sxs-lookup"><span data-stu-id="bdafe-p102">If you don't perform directory cleanup before you synchronize, there can be a significant negative effect on the deployment process. It might take days, or even weeks, to go through the cycle of directory synchronization, identifying errors, and re-synchronization.</span></span> 
  
<span data-ttu-id="bdafe-117">En el directorio local, complete las siguientes tareas de limpieza:</span><span class="sxs-lookup"><span data-stu-id="bdafe-117">In your on-premises directory, complete the following clean-up tasks:</span></span>
  
1. <span data-ttu-id="bdafe-118">Asegúrese de que cada usuario al que se le asignen ofertas de servicio de Office 365 tenga una dirección de correo electrónico válida y única en el atributo **proxyAddresses**.</span><span class="sxs-lookup"><span data-stu-id="bdafe-118">Ensure that each user who will be assigned Office 365 service offerings has a valid and unique email address in the **proxyAddresses** attribute.</span></span> 
    
2. <span data-ttu-id="bdafe-119">Quite los valores duplicados en el atributo **proxyAddresses**.</span><span class="sxs-lookup"><span data-stu-id="bdafe-119">Remove any duplicate values in the **proxyAddresses** attribute.</span></span> 
    
3.  <span data-ttu-id="bdafe-p103">Si es posible, asegúrese de que cada uno de los usuarios a los que se asignarán ofertas de servicio de Office 365 tenga un valor único y válido para el atributo **userPrincipalName** en el objeto de **usuario** del usuario. Para una mejor experiencia de sincronización, asegúrese de que el UPN de Active Directory local coincida con el UPN de nube. Si un usuario no tiene un valor para el atributo **userPrincipalName** , el objeto de **usuario** debe contener un valor válido y único para el atributo **samAccountName** . Quite los valores duplicados en el atributo **userPrincipalName** .</span><span class="sxs-lookup"><span data-stu-id="bdafe-p103">If possible, ensure that each user who will be assigned Office 365 service offerings has a valid and unique value for the **userPrincipalName** attribute in the user's **user** object. For best synchronization experience, ensure that the on-premises Active Directory UPN matches the cloud UPN. If a user does not have a value for the **userPrincipalName** attribute, then the **user** object must contain a valid and unique value for the **sAMAccountName** attribute. Remove any duplicate values in the **userPrincipalName** attribute.</span></span> 
    
4. <span data-ttu-id="bdafe-124">Para el uso óptimo de la lista global de direcciones (LGD), asegúrese de que la información de los siguientes atributos es correcta:</span><span class="sxs-lookup"><span data-stu-id="bdafe-124">For optimal use of the global address list (GAL), be sure the information in the following attributes is correct:</span></span>
    
  - <span data-ttu-id="bdafe-125">givenName </span><span class="sxs-lookup"><span data-stu-id="bdafe-125">givenName</span></span>
  - <span data-ttu-id="bdafe-126">apellido</span><span class="sxs-lookup"><span data-stu-id="bdafe-126">surname</span></span>
  - <span data-ttu-id="bdafe-127">displayName</span><span class="sxs-lookup"><span data-stu-id="bdafe-127">displayName</span></span>
  - <span data-ttu-id="bdafe-128">Puesto</span><span class="sxs-lookup"><span data-stu-id="bdafe-128">Job Title</span></span>
  - <span data-ttu-id="bdafe-129">Departamento</span><span class="sxs-lookup"><span data-stu-id="bdafe-129">Department</span></span>
  - <span data-ttu-id="bdafe-130">Oficina</span><span class="sxs-lookup"><span data-stu-id="bdafe-130">Office</span></span>
  - <span data-ttu-id="bdafe-131">Teléfono de la oficina</span><span class="sxs-lookup"><span data-stu-id="bdafe-131">Office Phone</span></span>
  - <span data-ttu-id="bdafe-132">Teléfono móvil</span><span class="sxs-lookup"><span data-stu-id="bdafe-132">Mobile Phone</span></span>
  - <span data-ttu-id="bdafe-133">Número de fax</span><span class="sxs-lookup"><span data-stu-id="bdafe-133">Fax Number</span></span>
  - <span data-ttu-id="bdafe-134">Dirección</span><span class="sxs-lookup"><span data-stu-id="bdafe-134">Street Address</span></span>
  - <span data-ttu-id="bdafe-135">Ciudad</span><span class="sxs-lookup"><span data-stu-id="bdafe-135">City</span></span>
  - <span data-ttu-id="bdafe-136">Estado o provincia</span><span class="sxs-lookup"><span data-stu-id="bdafe-136">State or Province</span></span>
  - <span data-ttu-id="bdafe-137">Código postal</span><span class="sxs-lookup"><span data-stu-id="bdafe-137">Zip or Postal Code</span></span>
  - <span data-ttu-id="bdafe-138">País o región</span><span class="sxs-lookup"><span data-stu-id="bdafe-138">Country or Region</span></span>
    
## <a name="directory-object-and-attribute-preparation"></a><span data-ttu-id="bdafe-139">Preparación de atributos y objetos de directorio</span><span class="sxs-lookup"><span data-stu-id="bdafe-139">Directory object and attribute preparation</span></span>

<span data-ttu-id="bdafe-p104">La correcta sincronización de directorios entre el directorio local y Office 365 requiere que los atributos del directorio local estén preparados correctamente. Por ejemplo, debe asegurarse de que los caracteres específicos no se usan en determinados atributos que se sincronizan con el entorno de Office 365. Los caracteres inEsperados no causan un error en la sincronización de directorios, pero podrían devolver una advertencia. Caracteres no válidos, se producirá un error en la sincronización de directorios.</span><span class="sxs-lookup"><span data-stu-id="bdafe-p104">Successful directory synchronization between your on-premises directory and Office 365 requires that your on-premises directory attributes are properly prepared. For example, you need to ensure that specific characters aren't used in certain attributes that are synchronized with the Office 365 environment. Unexpected characters do not cause directory synchronization to fail but might return a warning. Invalid characters will cause directory synchronization to fail.</span></span>
  
<span data-ttu-id="bdafe-p105">También se producirá un error en la sincronización de directorios si algunos de los usuarios de Active Directory tienen uno o más atributos duplicados. Cada usuario debe tener atributos únicos.</span><span class="sxs-lookup"><span data-stu-id="bdafe-p105">Directory synchronization will also fail if some of your Active Directory users have one or more duplicate attributes. Each user must have unique attributes.</span></span>
  
<span data-ttu-id="bdafe-146">A continuación se enumeran los atributos que debe preparar:</span><span class="sxs-lookup"><span data-stu-id="bdafe-146">The attributes that you need to prepare are listed here:</span></span>
  
 <span data-ttu-id="bdafe-147">**Nota:** También puede usar la [herramienta IdFix](install-and-run-idfix.md) para que este proceso sea mucho más fácil.</span><span class="sxs-lookup"><span data-stu-id="bdafe-147">**NOTE:** You can also use the [IdFix tool](install-and-run-idfix.md) to make this process a lot easier.</span></span> 
  
- <span data-ttu-id="bdafe-148">**displayName**</span><span class="sxs-lookup"><span data-stu-id="bdafe-148">**displayName**</span></span>
    
  - <span data-ttu-id="bdafe-149">Si el atributo existe en el objeto de usuario, se sincronizará con Office 365.</span><span class="sxs-lookup"><span data-stu-id="bdafe-149">If the attribute exists in the user object, it will be synchronized with Office 365.</span></span>
  - <span data-ttu-id="bdafe-p106">Si este atributo existe en el objeto de usuario, debe haber un valor para él. Es decir, el atributo no debe estar en blanco.</span><span class="sxs-lookup"><span data-stu-id="bdafe-p106">If this attribute exists in the user object, there must be a value for it. That is, the attribute must not be blank.</span></span>
  - <span data-ttu-id="bdafe-152">Número máximo de caracteres: 256</span><span class="sxs-lookup"><span data-stu-id="bdafe-152">Maximum number of characters: 256</span></span>
    
- <span data-ttu-id="bdafe-153">\*\*givenName \*\*</span><span class="sxs-lookup"><span data-stu-id="bdafe-153">**givenName**</span></span>
    
  - <span data-ttu-id="bdafe-154">Si el atributo existe en el objeto de usuario, se sincronizará con Office 365, pero Office 365 no lo necesita ni lo usa.</span><span class="sxs-lookup"><span data-stu-id="bdafe-154">If the attribute exists in the user object, it will be synchronized with Office 365, but Office 365 does not require or use it.</span></span>
  - <span data-ttu-id="bdafe-155">Número máximo de caracteres: 64</span><span class="sxs-lookup"><span data-stu-id="bdafe-155">Maximum number of characters: 64</span></span>
    
- <span data-ttu-id="bdafe-156">**correo**</span><span class="sxs-lookup"><span data-stu-id="bdafe-156">**mail**</span></span>
    
  - <span data-ttu-id="bdafe-157">El valor del atributo debe ser único dentro del directorio.</span><span class="sxs-lookup"><span data-stu-id="bdafe-157">The attribute value must be unique within the directory.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="bdafe-p107">Si hay valores duplicados, se sincroniza el primer usuario con el valor. Los usuarios posteriores no aparecerán en Office 365. Debe modificar el valor de Office 365, o bien modificar ambos valores en el directorio local para que ambos usuarios aparezcan en Office 365.</span><span class="sxs-lookup"><span data-stu-id="bdafe-p107">If there are duplicate values, the first user with the value is synchronized. Subsequent users will not appear in Office 365. You must modify either the value in Office 365, or modify both of the values in the on-premises directory in order for both users to appear in Office 365.</span></span> 
  
- <span data-ttu-id="bdafe-161">**mailNickname** (alias de Exchange)</span><span class="sxs-lookup"><span data-stu-id="bdafe-161">**mailNickname** (Exchange alias)</span></span> 
    
  - <span data-ttu-id="bdafe-162">El valor del atributo no puede comenzar con un punto (.).</span><span class="sxs-lookup"><span data-stu-id="bdafe-162">The attribute value cannot begin with a period (.).</span></span>
  - <span data-ttu-id="bdafe-163">El valor del atributo debe ser único dentro del directorio.</span><span class="sxs-lookup"><span data-stu-id="bdafe-163">The attribute value must be unique within the directory.</span></span>
    
- <span data-ttu-id="bdafe-164">\*\*proxyAddresses \*\*</span><span class="sxs-lookup"><span data-stu-id="bdafe-164">**proxyAddresses**</span></span>
    
  - <span data-ttu-id="bdafe-165">Atributo de varios valores</span><span class="sxs-lookup"><span data-stu-id="bdafe-165">Multiple-value attribute</span></span>
  - <span data-ttu-id="bdafe-166">Número máximo de caracteres por valor: 256</span><span class="sxs-lookup"><span data-stu-id="bdafe-166">Maximum number of characters per value: 256</span></span>
  - <span data-ttu-id="bdafe-167">El valor del atributo no debe contener un espacio.</span><span class="sxs-lookup"><span data-stu-id="bdafe-167">The attribute value must not contain a space.</span></span>
  - <span data-ttu-id="bdafe-168">El valor del atributo debe ser único dentro del directorio.</span><span class="sxs-lookup"><span data-stu-id="bdafe-168">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="bdafe-169">Caracteres no válidos: \< \> (); , [ ] "</span><span class="sxs-lookup"><span data-stu-id="bdafe-169">Invalid characters: \< \> ( ) ; , [ ] "</span></span>
    
    <span data-ttu-id="bdafe-170">Tenga en cuenta que los caracteres no válidos se aplican a los caracteres que siguen al delimitador de tipo y ":", de modo que SMTP:User@contso.com está permitido, pero SMTP:user:M@contoso.com no lo es.</span><span class="sxs-lookup"><span data-stu-id="bdafe-170">Note that the invalid characters apply to the characters following the type delimiter and ":", such that SMTP:User@contso.com is allowed, but SMTP:user:M@contoso.com is not.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="bdafe-p108">Todas las direcciones de Protocolo simple de transferencia de correo (SMTP) deben cumplir con los estándares de mensajería de correo electrónico. Si hay direcciones duplicadas o no deseadas, consulte el tema [de la ayuda quitar direcciones proxy duplicadas y no deseadas en Exchange](https://go.microsoft.com/fwlink/?LinkId=293860).</span><span class="sxs-lookup"><span data-stu-id="bdafe-p108">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards. If duplicate or unwanted addresses exist, see the Help topic [Removing duplicate and unwanted proxy addresses in Exchange](https://go.microsoft.com/fwlink/?LinkId=293860).</span></span> 
  
- <span data-ttu-id="bdafe-173">**sAMAccountName**</span><span class="sxs-lookup"><span data-stu-id="bdafe-173">**sAMAccountName**</span></span>
    
  - <span data-ttu-id="bdafe-174">Número máximo de caracteres: 20</span><span class="sxs-lookup"><span data-stu-id="bdafe-174">Maximum number of characters: 20</span></span>
  - <span data-ttu-id="bdafe-175">El valor del atributo debe ser único dentro del directorio.</span><span class="sxs-lookup"><span data-stu-id="bdafe-175">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="bdafe-p109">Caracteres no válidos: [\ "|, \< \> /: + =;? \* ]</span><span class="sxs-lookup"><span data-stu-id="bdafe-p109">Invalid characters: [ \ " | , / : \< \> + = ; ? \* ]</span></span>
  - <span data-ttu-id="bdafe-178">Si un usuario tiene un atributo **sAMAccountName** no válido, pero tiene un atributo **userPrincipalName** válido, se crea la cuenta del usuario en Office 365.</span><span class="sxs-lookup"><span data-stu-id="bdafe-178">If a user has an invalid **sAMAccountName** attribute but has a valid **userPrincipalName** attribute, the user account is created in Office 365.</span></span> 
  - <span data-ttu-id="bdafe-179">Si **samAccountName** y **userPrincipalName** no son válidos, se debe actualizar el atributo **userPrincipalName** local de Active Directory.</span><span class="sxs-lookup"><span data-stu-id="bdafe-179">If both **sAMAccountName** and **userPrincipalName** are invalid, the on-premises Active Directory **userPrincipalName** attribute must be updated.</span></span> 
    
- <span data-ttu-id="bdafe-180">**sn** (apellido)</span><span class="sxs-lookup"><span data-stu-id="bdafe-180">**sn** (surname)</span></span> 
    
  - <span data-ttu-id="bdafe-181">Si el atributo existe en el objeto de usuario, se sincronizará con Office 365, pero Office 365 no lo necesita ni lo usa.</span><span class="sxs-lookup"><span data-stu-id="bdafe-181">If the attribute exists in the user object, it will be synchronized with Office 365, but Office 365 does not require or use it.</span></span>
    
- <span data-ttu-id="bdafe-182">**targetAddress**</span><span class="sxs-lookup"><span data-stu-id="bdafe-182">**targetAddress**</span></span>
    
    <span data-ttu-id="bdafe-p110">Es necesario que el atributo **targetAddress** (por ejemplo, SMTP:Tom@contoso.com) que se rellene para el usuario deba aparecer en la GAL de Office 365. En los escenarios de migración de mensajería de terceros, sería necesaria la extensión de esquema de Office 365 para el directorio local. La extensión de esquema de Office 365 también agregará otros atributos útiles para administrar objetos de Office 365 que se rellenan con una herramienta de sincronización de directorios desde un directorio local. Por ejemplo, se agregaría el atributo **msExchHideFromAddressLists** para administrar los buzones ocultos o los grupos de distribución.</span><span class="sxs-lookup"><span data-stu-id="bdafe-p110">It's required that the **targetAddress** attribute (for example, SMTP:tom@contoso.com) that's populated for the user must appear in the Office 365 GAL. In third-party messaging migration scenarios, this would require the Office 365 schema extension for the on-premises directory. The Office 365 schema extension would also add other useful attributes to manage Office 365 objects that are populated by using a directory synchronization tool from on-premises directory. For example, the **msExchHideFromAddressLists** attribute to manage hidden mailboxes or distribution groups would be added.</span></span> 
   
  - <span data-ttu-id="bdafe-187">Número máximo de caracteres: 256</span><span class="sxs-lookup"><span data-stu-id="bdafe-187">Maximum number of characters: 256</span></span>
  - <span data-ttu-id="bdafe-188">El valor del atributo no debe contener un espacio.</span><span class="sxs-lookup"><span data-stu-id="bdafe-188">The attribute value must not contain a space.</span></span>
  - <span data-ttu-id="bdafe-189">El valor del atributo debe ser único dentro del directorio.</span><span class="sxs-lookup"><span data-stu-id="bdafe-189">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="bdafe-190">Caracteres no válidos \< \> : \ (); , [ ] "</span><span class="sxs-lookup"><span data-stu-id="bdafe-190">Invalid characters: \ \< \> ( ) ; , [ ] "</span></span>
  - <span data-ttu-id="bdafe-191">Todas las direcciones de Protocolo simple de transferencia de correo (SMTP) deben cumplir las normas de mensajería de correo.</span><span class="sxs-lookup"><span data-stu-id="bdafe-191">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span>
    
- <span data-ttu-id="bdafe-192">**userPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="bdafe-192">**userPrincipalName**</span></span>
    
  - <span data-ttu-id="bdafe-p111">El atributo **userPrincipalName** debe estar en el formato de inicio de sesión de estilo Internet, donde el nombre de usuario está seguido del signo de arroba (@) y de un nombre de dominio: por ejemplo, user@contoso.com. Todas las direcciones de Protocolo simple de transferencia de correo (SMTP) deben cumplir con los estándares de mensajería de correo electrónico.</span><span class="sxs-lookup"><span data-stu-id="bdafe-p111">The **userPrincipalName** attribute must be in the Internet-style sign-in format where the user name is followed by the at sign (@) and a domain name: for example, user@contoso.com. All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span>
  - <span data-ttu-id="bdafe-p112">El número máximo de caracteres para el atributo **userPrincipalName** es 113. Se permite un número de caracteres específico antes y después del signo arroba (@), como se muestra aquí:</span><span class="sxs-lookup"><span data-stu-id="bdafe-p112">The maximum number of characters for the **userPrincipalName** attribute is 113. A specific number of characters are permitted before and after the at sign (@), as follows:</span></span> 
  - <span data-ttu-id="bdafe-197">Número máximo de caracteres del nombre de usuario situado delante del signo (@): 64</span><span class="sxs-lookup"><span data-stu-id="bdafe-197">Maximum number of characters for the user name that is in front of the at sign (@): 64</span></span>
  - <span data-ttu-id="bdafe-198">Número máximo de caracteres para el nombre de dominio después de la arroba (@): 48</span><span class="sxs-lookup"><span data-stu-id="bdafe-198">Maximum number of characters for the domain name following the at sign (@): 48</span></span>
  - <span data-ttu-id="bdafe-p113">Caracteres no válidos: &amp; \* \% +/=? { } | \< \> ( ) ; : , [ ] "</span><span class="sxs-lookup"><span data-stu-id="bdafe-p113">Invalid characters: \ % &amp; \* + / = ? { } | \< \> ( ) ; : , [ ] "</span></span>
  - <span data-ttu-id="bdafe-201">Una umlaut también es un carácter no válido.</span><span class="sxs-lookup"><span data-stu-id="bdafe-201">An umlaut is also an invalid character.</span></span>
  - <span data-ttu-id="bdafe-202">El carácter @ es necesario en cada valor **userPrincipalName** .</span><span class="sxs-lookup"><span data-stu-id="bdafe-202">The @ character is required in each **userPrincipalName** value.</span></span> 
  - <span data-ttu-id="bdafe-203">El carácter @ no puede ser el primer carácter de cada valor **userPrincipalName**.</span><span class="sxs-lookup"><span data-stu-id="bdafe-203">The @ character cannot be the first character in each **userPrincipalName** value.</span></span> 
  - <span data-ttu-id="bdafe-204">El nombre de usuario no puede terminar con un punto (.), un&amp;signo de y comercial (), un espacio o un signo de arroba (@).</span><span class="sxs-lookup"><span data-stu-id="bdafe-204">The user name cannot end with a period (.), an ampersand (&amp;), a space, or an at sign (@).</span></span>
  - <span data-ttu-id="bdafe-205">El nombre de usuario no puede tener espacios.</span><span class="sxs-lookup"><span data-stu-id="bdafe-205">The user name cannot contain any spaces.</span></span>
  - <span data-ttu-id="bdafe-206">Deben usarse dominios enRutables; por ejemplo, no se pueden usar dominios locales o internos.</span><span class="sxs-lookup"><span data-stu-id="bdafe-206">Routable domains must be used; for example, local or internal domains cannot be used.</span></span>
  - <span data-ttu-id="bdafe-207">Unicode se convierte a guiones bajos.</span><span class="sxs-lookup"><span data-stu-id="bdafe-207">Unicode is converted to underscore characters.</span></span>
  - <span data-ttu-id="bdafe-208">**userPrincipalName** no puede contener valores duplicados en el directorio.</span><span class="sxs-lookup"><span data-stu-id="bdafe-208">**userPrincipalName** cannot contain any duplicate values in the directory.</span></span> 
    
## <a name="prepare-the-userprincipalname-attribute"></a><span data-ttu-id="bdafe-209">Preparar el atributo userPrincipalName</span><span class="sxs-lookup"><span data-stu-id="bdafe-209">Prepare the userPrincipalName attribute</span></span>

<span data-ttu-id="bdafe-p114">Active Directory está diseñado para permitir que los usuarios finales de la organización inicien sesión en su directorio mediante **samAccountName** o **userPrincipalName**. De forma similar, los usuarios finales pueden iniciar sesión en Office 365 mediante el nombre principal de usuario (UPN) de su cuenta profesional o educativa. La sincronización de directorios intenta crear nuevos usuarios en Azure Active Directory con el mismo UPN que se encuentra en el directorio local. El UPN tiene el mismo formato que una dirección de correo electrónico.</span><span class="sxs-lookup"><span data-stu-id="bdafe-p114">Active Directory is designed to allow the end users in your organization to sign in to your directory by using either **sAMAccountName** or **userPrincipalName**. Similarly, end users can sign in to Office 365 by using the user principal name (UPN) of their work or school account. Directory synchronization attempts to create new users in Azure Active Directory by using the same UPN that's in your on-premises directory. The UPN is formatted like an email address.</span></span> 

<span data-ttu-id="bdafe-p115">En Office 365, el UPN es el atributo predeterminado que se usa para generar la dirección de correo electrónico. Es fácil obtener **userPrincipalName** (local y en Azure Active Directory) y la dirección de correo electrónico principal de **proxyAddresses** establecida en valores diferentes. Cuando se establecen en valores diferentes, puede haber confusión para los administradores y los usuarios finales.</span><span class="sxs-lookup"><span data-stu-id="bdafe-p115">In Office 365, the UPN is the default attribute that's used to generate the email address. It's easy to get **userPrincipalName** (on-premises and in Azure Active Directory) and the primary email address in **proxyAddresses** set to different values. When they are set to different values, there can be confusion for administrators and end users.</span></span> 
  
<span data-ttu-id="bdafe-p116">Es mejor alinear estos atributos para reducir la confusión. Para cumplir los requisitos de inicio de sesión único con los servicios de Federación de Active Directory (AD FS) 2,0, debe asegurarse de que los UPN de Azure Active Directory y su implementación local de Active Directory coincidan con un espacio de nombres de dominio válido.</span><span class="sxs-lookup"><span data-stu-id="bdafe-p116">It's best to align these attributes to reduce confusion. To meet the requirements of single sign-on with Active Directory Federation Services (AD FS) 2.0, you need to ensure that the UPNs in Azure Active Directory and your on-premises Active Directory match and are using a valid domain namespace.</span></span>
  
## <a name="add-an-alternative-upn-suffix-to-ad-ds"></a><span data-ttu-id="bdafe-219">Adición de un sufijo UPN alternativo a AD DS</span><span class="sxs-lookup"><span data-stu-id="bdafe-219">Add an alternative UPN suffix to AD DS</span></span>

<span data-ttu-id="bdafe-p117">Es posible que deba agregar un sufijo UPN alternativo para asociar las credenciales corporativas del usuario con el entorno de Office 365. Un sufijo UPN es la parte de un UPN a la derecha del carácter @. Los UPN que se usan para el inicio de sesión único pueden contener letras, números, puntos, guiones y caracteres de subrayado, pero ningún otro tipo de caracteres.</span><span class="sxs-lookup"><span data-stu-id="bdafe-p117">You may need to add an alternative UPN suffix to associate the user's corporate credentials with the Office 365 environment. A UPN suffix is the part of a UPN to the right of the @ character. UPNs that are used for single sign-on can contain letters, numbers, periods, dashes, and underscores, but no other types of characters.</span></span>
  
<span data-ttu-id="bdafe-223">Para obtener más información acerca de cómo agregar un sufijo UPN alternativo a Active Directory, consulte [preparar la sincronización de directorios]( https://go.microsoft.com/fwlink/p/?LinkId=525430).</span><span class="sxs-lookup"><span data-stu-id="bdafe-223">For more information on how to add an alternative UPN suffix to Active Directory, see [Prepare for directory synchronization]( https://go.microsoft.com/fwlink/p/?LinkId=525430).</span></span>
  
## <a name="match-the-on-premises-upn-with-the-office-365-upn"></a><span data-ttu-id="bdafe-224">Hacer coincidir el UPN local con el UPN de Office 365</span><span class="sxs-lookup"><span data-stu-id="bdafe-224">Match the on-premises UPN with the Office 365 UPN</span></span>

<span data-ttu-id="bdafe-p118">Si ya ha configurado la sincronización de directorios, es posible que el UPN del usuario para Office 365 no concuerda con el UPN local del usuario que se define en el servicio de directorio local. Esto puede ocurrir cuando a un usuario se le asignó una licencia antes de que se comprobó el dominio. Para solucionar esto, use [PowerShell para corregir](https://go.microsoft.com/fwlink/p/?LinkId=396730) el UPN duplicado y actualizar el UPN del usuario para asegurarse de que el UPN de Office 365 coincide con el nombre de usuario corporativo y el dominio. Si actualiza el UPN en el servicio de directorio local y desea que se sincronice con la identidad de Azure Active Directory, debe quitar la licencia del usuario en Office 365 antes de realizar los cambios de forma local.</span><span class="sxs-lookup"><span data-stu-id="bdafe-p118">If you've already set up directory synchronization, the user's UPN for Office 365 may not match the user's on-premises UPN that's defined in your on-premises directory service. This can occur when a user was assigned a license before the domain was verified. To fix this, use [PowerShell to fix duplicate UPN](https://go.microsoft.com/fwlink/p/?LinkId=396730) to update the user's UPN to ensure that the Office 365 UPN matches the corporate user name and domain. If you are updating the UPN in the on-premises directory service and would like it to synchronize with the Azure Active Directory identity, you need to remove the user's license in Office 365 prior to making the changes on-premises.</span></span> 
  
<span data-ttu-id="bdafe-229">Consulte también [Cómo preparar un dominio no enrutable (como un dominio. local) para la sincronización de directorios](prepare-a-non-routable-domain-for-directory-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="bdafe-229">See also [How to prepare a non-routable domain (such as .local domain) for directory synchronization](prepare-a-non-routable-domain-for-directory-synchronization.md).</span></span>
  
## <a name="directory-integration-tools"></a><span data-ttu-id="bdafe-230">Herramientas de integración de directorios</span><span class="sxs-lookup"><span data-stu-id="bdafe-230">Directory integration tools</span></span>

<span data-ttu-id="bdafe-p119">La sincronización de directorios es la sincronización de objetos de directorio (usuarios, grupos y contactos) desde el entorno local de Active Directory a la infraestructura de directorios de Office 365, Azure Active Directory. Consulte [herramientas de integración de directorios](https://go.microsoft.com/fwlink/p/?LinkID=510956) para obtener una lista de las herramientas disponibles y su funcionalidad. La herramienta recomendada es [Microsoft Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkID=510956). Para obtener más información acerca de Azure Active Directory Connect, consulte [integración de las identidades locales con Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=527969).</span><span class="sxs-lookup"><span data-stu-id="bdafe-p119">Directory synchronization is the synchronization of directory objects (users, groups, and contacts) from your on-premises Active Directory environment to the Office 365 directory infrastructure, Azure Active Directory. See [Directory Integration Tools](https://go.microsoft.com/fwlink/p/?LinkID=510956) for a list of the available tools and their functionality. The recommended tool is [Microsoft Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkID=510956). For more information about Azure Active Directory Connect, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=527969).</span></span>
  
<span data-ttu-id="bdafe-p120">Cuando las cuentas de usuario se sincronizan con el directorio de Office 365 por primera vez, se marcan como no activadas. No pueden enviar ni recibir correo electrónico y no consumen licencias de suscripción. Cuando esté listo para asignar suscripciones de Office 365 a usuarios específicos, debe seleccionarlas y activarlas [asignando licencias a los usuarios de Office 365 para empresas](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).</span><span class="sxs-lookup"><span data-stu-id="bdafe-p120">When user accounts are synchronized with the Office 365 directory for the first time, they are marked as not activated. They cannot send or receive email, and they don't consume subscription licenses. When you're ready to assign Office 365 subscriptions to specific users, you must select and activate them by [Assign licenses to users in Office 365 for business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).</span></span>
  
<span data-ttu-id="bdafe-p121">También puede usar [PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=613097) para asignar licencias. Consulte [Cómo usar PowerShell para asignar licencias automáticamente a los usuarios de Office 365](https://go.microsoft.com/fwlink/p?LinkID=329805) para una solución automatizada.</span><span class="sxs-lookup"><span data-stu-id="bdafe-p121">You can also use [PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=613097) to assign licenses. See [How to Use PowerShell to Automatically Assign Licenses to Your Office 365 Users](https://go.microsoft.com/fwlink/p?LinkID=329805) for an automated solution.</span></span>