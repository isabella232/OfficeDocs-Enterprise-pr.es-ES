---
title: Preparación para la sincronización de directorios en Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/18/2019
audience: Admin
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
ms.openlocfilehash: 22db70d659d74e6d0f37f54a7743a562f220565d
ms.sourcegitcommit: 23c8781d1a2b0472612c3a2cb6e5d13edb03e236
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2019
ms.locfileid: "38702241"
---
# <a name="prepare-for-directory-synchronization-to-office-365"></a><span data-ttu-id="5d981-103">Preparación para la sincronización de directorios en Office 365</span><span class="sxs-lookup"><span data-stu-id="5d981-103">Prepare for directory synchronization to Office 365</span></span>

<span data-ttu-id="5d981-104">Entre las ventajas de la identidad híbrida y la sincronización de directorios de su organización se incluyen:</span><span class="sxs-lookup"><span data-stu-id="5d981-104">The benefits to hybrid identity and directory synchronization your organization include:</span></span>
  
- <span data-ttu-id="5d981-105">Reducción de los programas administrativos de la organización</span><span class="sxs-lookup"><span data-stu-id="5d981-105">Reducing the administrative programs in your organization</span></span>
- <span data-ttu-id="5d981-106">Habilitar opcionalmente escenario de inicio de sesión único</span><span class="sxs-lookup"><span data-stu-id="5d981-106">Optionally enabling single sign-on scenario</span></span>
- <span data-ttu-id="5d981-107">Automatizar cambios de cuenta en Office 365</span><span class="sxs-lookup"><span data-stu-id="5d981-107">Automating account changes in Office 365</span></span>
    
<span data-ttu-id="5d981-108">Para obtener más información acerca de las ventajas del uso de la sincronización de directorios, consulte [Guía básica de sincronización de directorios]( https://go.microsoft.com/fwlink/p/?LinkId=525398) e [identidad híbrida para Office 365](plan-for-directory-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="5d981-108">For more information about the advantages of using directory synchronization, see [Directory synchronization roadmap]( https://go.microsoft.com/fwlink/p/?LinkId=525398) and [Hybrid identity for Office 365](plan-for-directory-synchronization.md).</span></span>

<span data-ttu-id="5d981-109">Sin embargo, la sincronización de directorios requiere planeación y preparación para garantizar que los servicios de dominio de Active Directory (AD DS) se sincronicen con el inquilino de Azure Active Directory (Azure AD) de la suscripción a Office 365 con un mínimo de errores.</span><span class="sxs-lookup"><span data-stu-id="5d981-109">However, directory synchronization requires planning and preparation to ensure that your Active Directory Domain Services (AD DS) synchronizes to the Azure Active Directory (Azure AD) tenant of your Office 365 subscription with a minimum of errors.</span></span> 

<span data-ttu-id="5d981-110">Siga estos pasos en orden para obtener los mejores resultados.</span><span class="sxs-lookup"><span data-stu-id="5d981-110">Follow these steps in order for the best results.</span></span>
  
## <a name="1-directory-cleanup-tasks"></a><span data-ttu-id="5d981-111">1. tareas de limpieza de directorios</span><span class="sxs-lookup"><span data-stu-id="5d981-111">1. Directory cleanup tasks</span></span>

<span data-ttu-id="5d981-112">Antes de sincronizar AD DS con su espacio empresarial de Azure AD, debe limpiar su AD DS.</span><span class="sxs-lookup"><span data-stu-id="5d981-112">Before you synchronize your AD DS to your Azure AD tenant, you need to clean up your AD DS.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5d981-113">Si no realiza la limpieza de AD DS antes de sincronizar, puede haber un efecto negativo significativo en el proceso de implementación.</span><span class="sxs-lookup"><span data-stu-id="5d981-113">If you don't perform AD DS cleanup before you synchronize, there can be a significant negative effect on the deployment process.</span></span> <span data-ttu-id="5d981-114">Puede tardar días, o incluso semanas, en pasar por el ciclo de sincronización de directorios, identificar errores y volver a sincronizar.</span><span class="sxs-lookup"><span data-stu-id="5d981-114">It might take days, or even weeks, to go through the cycle of directory synchronization, identifying errors, and re-synchronization.</span></span> 
  
<span data-ttu-id="5d981-115">En AD DS, complete las siguientes tareas de limpieza para cada cuenta de usuario a la que se asignará una licencia de Office 365:</span><span class="sxs-lookup"><span data-stu-id="5d981-115">In your AD DS, complete the following clean-up tasks for each user account that will be assigned an Office 365 license:</span></span>
  
1. <span data-ttu-id="5d981-116">Asegúrese de que haya una dirección de correo electrónico válida y única en el atributo **proxyAddresses** .</span><span class="sxs-lookup"><span data-stu-id="5d981-116">Ensure a valid and unique email address in the **proxyAddresses** attribute.</span></span> 

  >[!Note]
  ><span data-ttu-id="5d981-117">Se omitirá un carácter de tilde (~) en las direcciones de correo electrónico.</span><span class="sxs-lookup"><span data-stu-id="5d981-117">A tilde (~) character in email addresses will be ignored.</span></span> <span data-ttu-id="5d981-118">Esto puede dar lugar a errores de sincronización de directorios falsos positivos al duplicar proxyAddresses.</span><span class="sxs-lookup"><span data-stu-id="5d981-118">This can lead to false-positive directory synchronization errors about duplicate proxyAddresses.</span></span>
    
2. <span data-ttu-id="5d981-119">Quite los valores duplicados en el atributo **proxyAddresses** .</span><span class="sxs-lookup"><span data-stu-id="5d981-119">Remove any duplicate values in the **proxyAddresses** attribute.</span></span> 
    
3.  <span data-ttu-id="5d981-120">Si es posible, asegúrese de un valor válido y único para el atributo **userPrincipalName** en el objeto de **usuario** del usuario.</span><span class="sxs-lookup"><span data-stu-id="5d981-120">If possible, ensure a valid and unique value for the **userPrincipalName** attribute in the user's **user** object.</span></span> <span data-ttu-id="5d981-121">Para obtener una mejor experiencia de sincronización, asegúrese de que el UPN de AD DS coincida con el UPN de Azure AD.</span><span class="sxs-lookup"><span data-stu-id="5d981-121">For the best synchronization experience, ensure that the AD DS UPN matches the Azure AD UPN.</span></span> <span data-ttu-id="5d981-122">Si un usuario no tiene un valor para el atributo **userPrincipalName** , el objeto de **usuario** debe contener un valor válido y único para el atributo **samAccountName** .</span><span class="sxs-lookup"><span data-stu-id="5d981-122">If a user does not have a value for the **userPrincipalName** attribute, then the **user** object must contain a valid and unique value for the **sAMAccountName** attribute.</span></span> <span data-ttu-id="5d981-123">Quite los valores duplicados en el atributo **userPrincipalName** .</span><span class="sxs-lookup"><span data-stu-id="5d981-123">Remove any duplicate values in the **userPrincipalName** attribute.</span></span> 
    
4. <span data-ttu-id="5d981-124">Para un uso óptimo de la lista global de direcciones (GAL), asegúrese de que la información de los siguientes atributos de la cuenta de usuario de AD DS es correcta:</span><span class="sxs-lookup"><span data-stu-id="5d981-124">For optimal use of the global address list (GAL), ensure the information in the following attributes of the AD DS user account is correct:</span></span>
    
  - <span data-ttu-id="5d981-125">givenName</span><span class="sxs-lookup"><span data-stu-id="5d981-125">givenName</span></span>
  - <span data-ttu-id="5d981-126">surname</span><span class="sxs-lookup"><span data-stu-id="5d981-126">surname</span></span>
  - <span data-ttu-id="5d981-127">displayName</span><span class="sxs-lookup"><span data-stu-id="5d981-127">displayName</span></span>
  - <span data-ttu-id="5d981-128">Puesto</span><span class="sxs-lookup"><span data-stu-id="5d981-128">Job Title</span></span>
  - <span data-ttu-id="5d981-129">Departamento</span><span class="sxs-lookup"><span data-stu-id="5d981-129">Department</span></span>
  - <span data-ttu-id="5d981-130">Oficina</span><span class="sxs-lookup"><span data-stu-id="5d981-130">Office</span></span>
  - <span data-ttu-id="5d981-131">Teléfono de la oficina</span><span class="sxs-lookup"><span data-stu-id="5d981-131">Office Phone</span></span>
  - <span data-ttu-id="5d981-132">Teléfono móvil</span><span class="sxs-lookup"><span data-stu-id="5d981-132">Mobile Phone</span></span>
  - <span data-ttu-id="5d981-133">Número de fax</span><span class="sxs-lookup"><span data-stu-id="5d981-133">Fax Number</span></span>
  - <span data-ttu-id="5d981-134">Dirección</span><span class="sxs-lookup"><span data-stu-id="5d981-134">Street Address</span></span>
  - <span data-ttu-id="5d981-135">Ciudad</span><span class="sxs-lookup"><span data-stu-id="5d981-135">City</span></span>
  - <span data-ttu-id="5d981-136">Provincia</span><span class="sxs-lookup"><span data-stu-id="5d981-136">State or Province</span></span>
  - <span data-ttu-id="5d981-137">Código postal</span><span class="sxs-lookup"><span data-stu-id="5d981-137">Zip or Postal Code</span></span>
  - <span data-ttu-id="5d981-138">País o región</span><span class="sxs-lookup"><span data-stu-id="5d981-138">Country or Region</span></span>
    
## <a name="2-directory-object-and-attribute-preparation"></a><span data-ttu-id="5d981-139">2. preparación del objeto y el atributo del directorio</span><span class="sxs-lookup"><span data-stu-id="5d981-139">2. Directory object and attribute preparation</span></span>

<span data-ttu-id="5d981-140">La correcta sincronización de directorios entre su AD DS y Office 365 requiere que los atributos de AD DS estén preparados correctamente.</span><span class="sxs-lookup"><span data-stu-id="5d981-140">Successful directory synchronization between your AD DS and Office 365 requires that your AD DS attributes are properly prepared.</span></span> <span data-ttu-id="5d981-141">Por ejemplo, debe asegurarse de que los caracteres específicos no se usan en determinados atributos que se sincronizan con el entorno de Office 365.</span><span class="sxs-lookup"><span data-stu-id="5d981-141">For example, you need to ensure that specific characters aren't used in certain attributes that are synchronized with the Office 365 environment.</span></span> <span data-ttu-id="5d981-142">Los caracteres inesperados no causan un error en la sincronización de directorios, pero podrían devolver una advertencia.</span><span class="sxs-lookup"><span data-stu-id="5d981-142">Unexpected characters do not cause directory synchronization to fail but might return a warning.</span></span> <span data-ttu-id="5d981-143">Caracteres no válidos, se producirá un error en la sincronización de directorios.</span><span class="sxs-lookup"><span data-stu-id="5d981-143">Invalid characters will cause directory synchronization to fail.</span></span>
  
<span data-ttu-id="5d981-144">También se producirá un error en la sincronización de directorios si algunos de los usuarios de AD DS tienen uno o más atributos duplicados.</span><span class="sxs-lookup"><span data-stu-id="5d981-144">Directory synchronization will also fail if some of your AD DS users have one or more duplicate attributes.</span></span> <span data-ttu-id="5d981-145">Cada usuario debe tener atributos únicos.</span><span class="sxs-lookup"><span data-stu-id="5d981-145">Each user must have unique attributes.</span></span>
  
<span data-ttu-id="5d981-146">A continuación se enumeran los atributos que debe preparar:</span><span class="sxs-lookup"><span data-stu-id="5d981-146">The attributes that you need to prepare are listed here:</span></span>
  
- <span data-ttu-id="5d981-147">**displayName**</span><span class="sxs-lookup"><span data-stu-id="5d981-147">**displayName**</span></span>
    
  - <span data-ttu-id="5d981-148">Si el atributo existe en el objeto de usuario, se sincronizará con Office 365.</span><span class="sxs-lookup"><span data-stu-id="5d981-148">If the attribute exists in the user object, it will be synchronized with Office 365.</span></span>
  - <span data-ttu-id="5d981-149">Si este atributo existe en el objeto de usuario, debe haber un valor para él.</span><span class="sxs-lookup"><span data-stu-id="5d981-149">If this attribute exists in the user object, there must be a value for it.</span></span> <span data-ttu-id="5d981-150">Es decir, el atributo no debe estar en blanco.</span><span class="sxs-lookup"><span data-stu-id="5d981-150">That is, the attribute must not be blank.</span></span>
  - <span data-ttu-id="5d981-151">Número máximo de caracteres: 256</span><span class="sxs-lookup"><span data-stu-id="5d981-151">Maximum number of characters: 256</span></span>
    
- <span data-ttu-id="5d981-152">**givenName**</span><span class="sxs-lookup"><span data-stu-id="5d981-152">**givenName**</span></span>
    
  - <span data-ttu-id="5d981-153">Si el atributo existe en el objeto de usuario, se sincronizará con Office 365, pero Office 365 no lo necesita ni lo usa.</span><span class="sxs-lookup"><span data-stu-id="5d981-153">If the attribute exists in the user object, it will be synchronized with Office 365, but Office 365 does not require or use it.</span></span>
  - <span data-ttu-id="5d981-154">Número máximo de caracteres: 64</span><span class="sxs-lookup"><span data-stu-id="5d981-154">Maximum number of characters: 64</span></span>
    
- <span data-ttu-id="5d981-155">**mail**</span><span class="sxs-lookup"><span data-stu-id="5d981-155">**mail**</span></span>
    
  - <span data-ttu-id="5d981-156">El valor del atributo debe ser único dentro del directorio.</span><span class="sxs-lookup"><span data-stu-id="5d981-156">The attribute value must be unique within the directory.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="5d981-157">Si hay valores duplicados, se sincroniza el primer usuario con el valor.</span><span class="sxs-lookup"><span data-stu-id="5d981-157">If there are duplicate values, the first user with the value is synchronized.</span></span> <span data-ttu-id="5d981-158">Los usuarios posteriores no aparecerán en Office 365.</span><span class="sxs-lookup"><span data-stu-id="5d981-158">Subsequent users will not appear in Office 365.</span></span> <span data-ttu-id="5d981-159">Debe modificar el valor de Office 365 o modificar ambos valores en AD DS para que ambos usuarios aparezcan en Office 365.</span><span class="sxs-lookup"><span data-stu-id="5d981-159">You must modify either the value in Office 365 or modify both of the values in AD DS in order for both users to appear in Office 365.</span></span> 
  
- <span data-ttu-id="5d981-160">**mailNickname** (alias de Exchange)</span><span class="sxs-lookup"><span data-stu-id="5d981-160">**mailNickname** (Exchange alias)</span></span> 
    
  - <span data-ttu-id="5d981-161">El valor del atributo no puede comenzar con un punto (.).</span><span class="sxs-lookup"><span data-stu-id="5d981-161">The attribute value cannot begin with a period (.).</span></span>
  - <span data-ttu-id="5d981-162">El valor del atributo debe ser único dentro del directorio.</span><span class="sxs-lookup"><span data-stu-id="5d981-162">The attribute value must be unique within the directory.</span></span>
    
- <span data-ttu-id="5d981-163">**proxyAddresses**</span><span class="sxs-lookup"><span data-stu-id="5d981-163">**proxyAddresses**</span></span>
    
  - <span data-ttu-id="5d981-164">Atributo de varios valores</span><span class="sxs-lookup"><span data-stu-id="5d981-164">Multiple-value attribute</span></span>
  - <span data-ttu-id="5d981-165">Número máximo de caracteres por valor: 256</span><span class="sxs-lookup"><span data-stu-id="5d981-165">Maximum number of characters per value: 256</span></span>
  - <span data-ttu-id="5d981-166">El valor del atributo no debe contener un espacio.</span><span class="sxs-lookup"><span data-stu-id="5d981-166">The attribute value must not contain a space.</span></span>
  - <span data-ttu-id="5d981-167">El valor del atributo debe ser único dentro del directorio.</span><span class="sxs-lookup"><span data-stu-id="5d981-167">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="5d981-168">Caracteres no válidos: \< \> (); , [ ] " '</span><span class="sxs-lookup"><span data-stu-id="5d981-168">Invalid characters: \< \> ( ) ; , [ ] " '</span></span>
    
    <span data-ttu-id="5d981-169">Tenga en cuenta que los caracteres no válidos se aplican a los caracteres que siguen al delimitador de tipo y ":", de modo que SMTP:User@contso.com está permitido, pero SMTP:user:M@contoso.com no lo es.</span><span class="sxs-lookup"><span data-stu-id="5d981-169">Note that the invalid characters apply to the characters following the type delimiter and ":", such that SMTP:User@contso.com is allowed, but SMTP:user:M@contoso.com is not.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="5d981-170">Todas las direcciones de Protocolo simple de transferencia de correo (SMTP) deben cumplir con los estándares de mensajería de correo electrónico.</span><span class="sxs-lookup"><span data-stu-id="5d981-170">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span> <span data-ttu-id="5d981-171">Si hay direcciones duplicadas o no deseadas, consulte el tema [de la ayuda quitar direcciones proxy duplicadas y no deseadas en Exchange](https://go.microsoft.com/fwlink/?LinkId=293860).</span><span class="sxs-lookup"><span data-stu-id="5d981-171">If duplicate or unwanted addresses exist, see the Help topic [Removing duplicate and unwanted proxy addresses in Exchange](https://go.microsoft.com/fwlink/?LinkId=293860).</span></span> 
  
- <span data-ttu-id="5d981-172">**sAMAccountName**</span><span class="sxs-lookup"><span data-stu-id="5d981-172">**sAMAccountName**</span></span>
    
  - <span data-ttu-id="5d981-173">Número máximo de caracteres: 20</span><span class="sxs-lookup"><span data-stu-id="5d981-173">Maximum number of characters: 20</span></span>
  - <span data-ttu-id="5d981-174">El valor del atributo debe ser único dentro del directorio.</span><span class="sxs-lookup"><span data-stu-id="5d981-174">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="5d981-175">Caracteres no válidos: [\ "|, \< \> /: + =;?</span><span class="sxs-lookup"><span data-stu-id="5d981-175">Invalid characters: [ \ " | , / : \< \> + = ; ?</span></span> <span data-ttu-id="5d981-176">\* ']</span><span class="sxs-lookup"><span data-stu-id="5d981-176"></span></span>
  - <span data-ttu-id="5d981-177">Si un usuario tiene un atributo **samAccountName** no válido, pero tiene un atributo **userPrincipalName** válido, se crea la cuenta de usuario en Office 365.</span><span class="sxs-lookup"><span data-stu-id="5d981-177">If a user has an invalid **sAMAccountName** attribute but has a valid **userPrincipalName** attribute, the user account is created in Office 365.</span></span> 
  - <span data-ttu-id="5d981-178">Si **samAccountName** y **userPrincipalName** no son válidos, se debe actualizar el atributo **userPrincipalName** de AD DS.</span><span class="sxs-lookup"><span data-stu-id="5d981-178">If both **sAMAccountName** and **userPrincipalName** are invalid, the AD DS **userPrincipalName** attribute must be updated.</span></span> 
    
- <span data-ttu-id="5d981-179">**SN** (Apellidos)</span><span class="sxs-lookup"><span data-stu-id="5d981-179">**sn** (surname)</span></span> 
    
  - <span data-ttu-id="5d981-180">Si el atributo existe en el objeto de usuario, se sincronizará con Office 365, pero Office 365 no lo necesita ni lo usa.</span><span class="sxs-lookup"><span data-stu-id="5d981-180">If the attribute exists in the user object, it will be synchronized with Office 365, but Office 365 does not require or use it.</span></span>
    
- <span data-ttu-id="5d981-181">**targetAddress**</span><span class="sxs-lookup"><span data-stu-id="5d981-181">**targetAddress**</span></span>
    
    <span data-ttu-id="5d981-182">Es necesario que el atributo **targetAddress** (por ejemplo, SMTP:Tom@contoso.com) que se rellene para el usuario deba aparecer en la GAL de Office 365.</span><span class="sxs-lookup"><span data-stu-id="5d981-182">It's required that the **targetAddress** attribute (for example, SMTP:tom@contoso.com) that's populated for the user must appear in the Office 365 GAL.</span></span> <span data-ttu-id="5d981-183">En los escenarios de migración de mensajería de terceros, sería necesaria la extensión de esquema de Office 365 para AD DS.</span><span class="sxs-lookup"><span data-stu-id="5d981-183">In third-party messaging migration scenarios, this would require the Office 365 schema extension for the AD DS.</span></span> <span data-ttu-id="5d981-184">La extensión de esquema de Office 365 también agregará otros atributos útiles para administrar objetos de Office 365 que se rellenan con una herramienta de sincronización de directorios de AD DS.</span><span class="sxs-lookup"><span data-stu-id="5d981-184">The Office 365 schema extension would also add other useful attributes to manage Office 365 objects that are populated by using a directory synchronization tool from AD DS.</span></span> <span data-ttu-id="5d981-185">Por ejemplo, se agregaría el atributo **msExchHideFromAddressLists** para administrar los buzones ocultos o los grupos de distribución.</span><span class="sxs-lookup"><span data-stu-id="5d981-185">For example, the **msExchHideFromAddressLists** attribute to manage hidden mailboxes or distribution groups would be added.</span></span> 
   
  - <span data-ttu-id="5d981-186">Número máximo de caracteres: 256</span><span class="sxs-lookup"><span data-stu-id="5d981-186">Maximum number of characters: 256</span></span>
  - <span data-ttu-id="5d981-187">El valor del atributo no debe contener un espacio.</span><span class="sxs-lookup"><span data-stu-id="5d981-187">The attribute value must not contain a space.</span></span>
  - <span data-ttu-id="5d981-188">El valor del atributo debe ser único dentro del directorio.</span><span class="sxs-lookup"><span data-stu-id="5d981-188">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="5d981-189">Caracteres no válidos \< \> : \ (); , [ ] "</span><span class="sxs-lookup"><span data-stu-id="5d981-189">Invalid characters: \ \< \> ( ) ; , [ ] "</span></span>
  - <span data-ttu-id="5d981-190">Todas las direcciones de Protocolo simple de transferencia de correo (SMTP) deben cumplir con los estándares de mensajería de correo electrónico.</span><span class="sxs-lookup"><span data-stu-id="5d981-190">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span>
    
- <span data-ttu-id="5d981-191">**userPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="5d981-191">**userPrincipalName**</span></span>
    
  - <span data-ttu-id="5d981-192">El atributo **userPrincipalName** debe estar en el formato de inicio de sesión de estilo Internet, donde el nombre de usuario está seguido del signo de arroba (@) y de un nombre de dominio: por ejemplo, user@contoso.com.</span><span class="sxs-lookup"><span data-stu-id="5d981-192">The **userPrincipalName** attribute must be in the Internet-style sign-in format where the user name is followed by the at sign (@) and a domain name: for example, user@contoso.com.</span></span> <span data-ttu-id="5d981-193">Todas las direcciones de Protocolo simple de transferencia de correo (SMTP) deben cumplir con los estándares de mensajería de correo electrónico.</span><span class="sxs-lookup"><span data-stu-id="5d981-193">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span>
  - <span data-ttu-id="5d981-194">El número máximo de caracteres para el atributo **userPrincipalName** es de 113.</span><span class="sxs-lookup"><span data-stu-id="5d981-194">The maximum number of characters for the **userPrincipalName** attribute is 113.</span></span> <span data-ttu-id="5d981-195">Se permite un número específico de caracteres antes y después de la arroba (@), de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="5d981-195">A specific number of characters are permitted before and after the at sign (@), as follows:</span></span> 
  - <span data-ttu-id="5d981-196">Número máximo de caracteres para el nombre de usuario que está delante del signo (@): 64</span><span class="sxs-lookup"><span data-stu-id="5d981-196">Maximum number of characters for the username that is in front of the at sign (@): 64</span></span>
  - <span data-ttu-id="5d981-197">Número máximo de caracteres para el nombre de dominio después de la arroba (@): 48</span><span class="sxs-lookup"><span data-stu-id="5d981-197">Maximum number of characters for the domain name following the at sign (@): 48</span></span>
  - <span data-ttu-id="5d981-198">Caracteres no válidos: &amp; \* \% +/=?</span><span class="sxs-lookup"><span data-stu-id="5d981-198">Invalid characters: \ % &amp; \* + / = ?</span></span> <span data-ttu-id="5d981-199">{ } | \< \> ( ) ; : , [ ] " '</span><span class="sxs-lookup"><span data-stu-id="5d981-199"></span></span>
  - <span data-ttu-id="5d981-200">Una umlaut también es un carácter no válido.</span><span class="sxs-lookup"><span data-stu-id="5d981-200">An umlaut is also an invalid character.</span></span>
  - <span data-ttu-id="5d981-201">El carácter @ es necesario en cada valor **userPrincipalName** .</span><span class="sxs-lookup"><span data-stu-id="5d981-201">The @ character is required in each **userPrincipalName** value.</span></span> 
  - <span data-ttu-id="5d981-202">El carácter @ no puede ser el primer carácter de cada valor **userPrincipalName**.</span><span class="sxs-lookup"><span data-stu-id="5d981-202">The @ character cannot be the first character in each **userPrincipalName** value.</span></span> 
  - <span data-ttu-id="5d981-203">El nombre de usuario no puede terminar con un punto (.),&amp;un signo de y comercial (), un espacio o un signo de arroba (@).</span><span class="sxs-lookup"><span data-stu-id="5d981-203">The username cannot end with a period (.), an ampersand (&amp;), a space, or an at sign (@).</span></span>
  - <span data-ttu-id="5d981-204">El nombre de usuario no puede contener espacios.</span><span class="sxs-lookup"><span data-stu-id="5d981-204">The username cannot contain any spaces.</span></span>
  - <span data-ttu-id="5d981-205">Deben usarse dominios enrutables; por ejemplo, no se pueden usar dominios locales o internos.</span><span class="sxs-lookup"><span data-stu-id="5d981-205">Routable domains must be used; for example, local or internal domains cannot be used.</span></span>
  - <span data-ttu-id="5d981-206">Unicode se convierte a guiones bajos.</span><span class="sxs-lookup"><span data-stu-id="5d981-206">Unicode is converted to underscore characters.</span></span>
  - <span data-ttu-id="5d981-207">**userPrincipalName** no puede contener valores duplicados en el directorio.</span><span class="sxs-lookup"><span data-stu-id="5d981-207">**userPrincipalName** cannot contain any duplicate values in the directory.</span></span> 

<span data-ttu-id="5d981-208">Vea [preparar los atributos de directorio con la herramienta idfix](prepare-directory-attributes-for-synch-with-idfix.md) para usar la herramienta idfix con el fin de identificar errores en los atributos de AD DS.</span><span class="sxs-lookup"><span data-stu-id="5d981-208">See [Prepare directory attributes with the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md) to use the IdFIx tool to identify errors in the attributes of your AD DS.</span></span>
    
## <a name="3-prepare-the-userprincipalname-attribute"></a><span data-ttu-id="5d981-209">3. preparar el atributo userPrincipalName</span><span class="sxs-lookup"><span data-stu-id="5d981-209">3. Prepare the userPrincipalName attribute</span></span>

<span data-ttu-id="5d981-210">Active Directory está diseñado para permitir que los usuarios finales de la organización inicien sesión en su directorio mediante **samAccountName** o **userPrincipalName**.</span><span class="sxs-lookup"><span data-stu-id="5d981-210">Active Directory is designed to allow the end users in your organization to sign in to your directory by using either **sAMAccountName** or **userPrincipalName**.</span></span> <span data-ttu-id="5d981-211">De forma similar, los usuarios finales pueden iniciar sesión en Office 365 mediante el nombre principal de usuario (UPN) de su cuenta profesional o educativa.</span><span class="sxs-lookup"><span data-stu-id="5d981-211">Similarly, end users can sign in to Office 365 by using the user principal name (UPN) of their work or school account.</span></span> <span data-ttu-id="5d981-212">La sincronización de directorios intenta crear nuevos usuarios en Azure Active Directory con el mismo UPN que se encuentra en AD DS.</span><span class="sxs-lookup"><span data-stu-id="5d981-212">Directory synchronization attempts to create new users in Azure Active Directory by using the same UPN that's in your AD DS.</span></span> <span data-ttu-id="5d981-213">El UPN tiene el mismo formato que una dirección de correo electrónico.</span><span class="sxs-lookup"><span data-stu-id="5d981-213">The UPN is formatted like an email address.</span></span> 

<span data-ttu-id="5d981-214">En Office 365, el UPN es el atributo predeterminado que se usa para generar la dirección de correo electrónico.</span><span class="sxs-lookup"><span data-stu-id="5d981-214">In Office 365, the UPN is the default attribute that's used to generate the email address.</span></span> <span data-ttu-id="5d981-215">Es fácil obtener **userPrincipalName** (en AD DS y en Azure ad) y la dirección de correo electrónico principal en **proxyAddresses** se establece en valores diferentes.</span><span class="sxs-lookup"><span data-stu-id="5d981-215">It's easy to get **userPrincipalName** (in AD DS and in Azure AD) and the primary email address in **proxyAddresses** set to different values.</span></span> <span data-ttu-id="5d981-216">Cuando se establecen en valores diferentes, puede haber confusión para los administradores y los usuarios finales.</span><span class="sxs-lookup"><span data-stu-id="5d981-216">When they are set to different values, there can be confusion for administrators and end users.</span></span> 
  
<span data-ttu-id="5d981-217">Es mejor alinear estos atributos para reducir la confusión.</span><span class="sxs-lookup"><span data-stu-id="5d981-217">It's best to align these attributes to reduce confusion.</span></span> <span data-ttu-id="5d981-218">Para cumplir los requisitos de inicio de sesión único con los servicios de Federación de Active Directory (AD FS) 2,0, debe asegurarse de que los UPN de Azure Active Directory y su AD DS coinciden y usan un espacio de nombres de dominio válido.</span><span class="sxs-lookup"><span data-stu-id="5d981-218">To meet the requirements of single sign-on with Active Directory Federation Services (AD FS) 2.0, you need to ensure that the UPNs in Azure Active Directory and your AD DS match and are using a valid domain namespace.</span></span>
  
## <a name="4-add-an-alternative-upn-suffix-to-ad-ds"></a><span data-ttu-id="5d981-219">4. agregar un sufijo UPN alternativo a AD DS</span><span class="sxs-lookup"><span data-stu-id="5d981-219">4. Add an alternative UPN suffix to AD DS</span></span>

<span data-ttu-id="5d981-220">Es posible que deba agregar un sufijo UPN alternativo para asociar las credenciales corporativas del usuario con el entorno de Office 365.</span><span class="sxs-lookup"><span data-stu-id="5d981-220">You may need to add an alternative UPN suffix to associate the user's corporate credentials with the Office 365 environment.</span></span> <span data-ttu-id="5d981-221">Un sufijo UPN es la parte de un UPN situada a la derecha del carácter @.</span><span class="sxs-lookup"><span data-stu-id="5d981-221">A UPN suffix is the part of a UPN to the right of the @ character.</span></span> <span data-ttu-id="5d981-222">Los UPN que se usan para el inicio de sesión único pueden contener letras, números, puntos, guiones y caracteres de subrayado, pero ningún otro tipo de carácter.</span><span class="sxs-lookup"><span data-stu-id="5d981-222">UPNs that are used for single sign-on can contain letters, numbers, periods, dashes, and underscores, but no other types of characters.</span></span>
  
<span data-ttu-id="5d981-223">Para obtener más información acerca de cómo agregar un sufijo UPN alternativo a Active Directory, consulte [preparar la sincronización de directorios]( https://go.microsoft.com/fwlink/p/?LinkId=525430).</span><span class="sxs-lookup"><span data-stu-id="5d981-223">For more information on how to add an alternative UPN suffix to Active Directory, see [Prepare for directory synchronization]( https://go.microsoft.com/fwlink/p/?LinkId=525430).</span></span>
  
## <a name="5-match-the-ad-ds-upn-with-the-office-365-upn"></a><span data-ttu-id="5d981-224">5. hacer coincidir con el UPN de AD DS con el UPN de Office 365</span><span class="sxs-lookup"><span data-stu-id="5d981-224">5. Match the AD DS UPN with the Office 365 UPN</span></span>

<span data-ttu-id="5d981-225">Si ya ha configurado la sincronización de directorios, es posible que el UPN del usuario para Office 365 no concuerda con el UPN AD DS del usuario definido en AD DS.</span><span class="sxs-lookup"><span data-stu-id="5d981-225">If you've already set up directory synchronization, the user's UPN for Office 365 may not match the user's AD DS UPN that's defined in your AD DS.</span></span> <span data-ttu-id="5d981-226">Esto puede suceder cuando se ha asignado una licencia a un usuario antes de que se comprobara el dominio.</span><span class="sxs-lookup"><span data-stu-id="5d981-226">This can occur when a user was assigned a license before the domain was verified.</span></span> <span data-ttu-id="5d981-227">Para solucionar esto, use [PowerShell para corregir el UPN duplicado](https://go.microsoft.com/fwlink/p/?LinkId=396730) y actualizar el UPN del usuario para asegurarse de que el UPN de Office 365 coincide con el nombre de usuario corporativo y el dominio.</span><span class="sxs-lookup"><span data-stu-id="5d981-227">To fix this, use [PowerShell to fix duplicate UPN](https://go.microsoft.com/fwlink/p/?LinkId=396730) to update the user's UPN to ensure that the Office 365 UPN matches the corporate user name and domain.</span></span> <span data-ttu-id="5d981-228">Si actualiza el UPN en AD DS y desea que se sincronice con la identidad de Azure Active Directory, debe quitar la licencia del usuario en Office 365 antes de realizar los cambios en AD DS.</span><span class="sxs-lookup"><span data-stu-id="5d981-228">If you are updating the UPN in the AD DS and would like it to synchronize with the Azure Active Directory identity, you need to remove the user's license in Office 365 prior to making the changes in AD DS.</span></span> 
  
<span data-ttu-id="5d981-229">Consulte también [Cómo preparar un dominio no enrutable (como un dominio. local) para la sincronización de directorios](prepare-a-non-routable-domain-for-directory-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="5d981-229">Also see [How to prepare a non-routable domain (such as .local domain) for directory synchronization](prepare-a-non-routable-domain-for-directory-synchronization.md).</span></span>


## <a name="next-steps"></a><span data-ttu-id="5d981-230">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="5d981-230">Next steps</span></span>

<span data-ttu-id="5d981-231">Vea [preparar los atributos de directorio con la herramienta IdFix](prepare-directory-attributes-for-synch-with-idfix.md) para ayudarle a corregir errores en los atributos de AD DS antes de la sincronización de directorios.</span><span class="sxs-lookup"><span data-stu-id="5d981-231">See [Prepare directory attributes with the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md) to help you correct errors in the attributes of your AD DS prior to directory synchronization.</span></span>

<span data-ttu-id="5d981-232">Si ha corregido todos los errores de atributo identificados con la herramienta IdFix y ha realizado los pasos 1 a 5 anteriores, consulte [configurar la sincronización de directorios](set-up-directory-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="5d981-232">If you have corrected all the attribute errors identified with the IdFix tool and have done steps 1 through 5 above, see [Set up directory synchronization](set-up-directory-synchronization.md).</span></span>
