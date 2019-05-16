---
title: Proteger las cuentas de administrador global de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 4/10/2018
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Strat_O365_IP
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 6b4ded77-ac8d-42ed-8606-c014fd947560
description: Proteja el acceso de administrador global a su suscripción a Office 365 con estos tres pasos.
ms.openlocfilehash: bb1b19a7ac0ec8e32c23303e8acf2b7ee42f0532
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071026"
---
# <a name="protect-your-office-365-global-administrator-accounts"></a><span data-ttu-id="1ba7b-103">Proteger las cuentas de administrador global de Office 365</span><span class="sxs-lookup"><span data-stu-id="1ba7b-103">Protect your Office 365 global administrator accounts</span></span>

 <span data-ttu-id="1ba7b-104">**Resumen:** Proteja su suscripción de Office 365 de ataques en función de la intromisión de una cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-104">**Summary:** Protect your Office 365 subscription from attacks based on the compromise of a global administrator account.</span></span> 
  
<span data-ttu-id="1ba7b-105">Las infracciones de seguridad de una suscripción de Office 365, incluidos los ataques de suplantación de identidad (phishing) y recopilación de información, suelen realizarse poniendo en peligro las credenciales de una cuenta de administrador global de Office 365.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-105">Security breaches of an Office 365 subscription, including information harvesting and phishing attacks, are typically done by compromising the credentials of an Office 365 global administrator account.</span></span> <span data-ttu-id="1ba7b-106">La seguridad en la nube es una asociación entre usted y Microsoft:</span><span class="sxs-lookup"><span data-stu-id="1ba7b-106">Security in the cloud is a partnership between you and Microsoft:</span></span>
  
- <span data-ttu-id="1ba7b-107">Los servicios en la nube de Microsoft se basan en una base de confianza y seguridad.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-107">Microsoft cloud services are built on a foundation of trust and security.</span></span> <span data-ttu-id="1ba7b-108">Microsoft le proporciona controles y funciones de seguridad para ayudarle a proteger los datos y las aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-108">Microsoft provides you security controls and capabilities to help you protect your data and applications.</span></span>
    
- <span data-ttu-id="1ba7b-109">Debe poseer sus datos e identidades y la responsabilidad de protegerlos, la seguridad de los recursos locales y la seguridad de los componentes de la nube que usted controle.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-109">You own your data and identities and the responsibility for protecting them, the security of your on-premises resources, and the security of cloud components you control.</span></span>
    
<span data-ttu-id="1ba7b-110">Microsoft ofrece capacidades para ayudar a proteger su organización, pero solo se aplican si las usa.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-110">Microsoft provides capabilities to help protect your organization, but they are effective only if you use them.</span></span> <span data-ttu-id="1ba7b-111">Si no las usa, puede ser vulnerable a un ataque.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-111">If you do not use them, you may be vulnerable to attack.</span></span> <span data-ttu-id="1ba7b-112">Para proteger sus cuentas de administrador global, Microsoft está aquí para ayudarle con instrucciones detalladas para:</span><span class="sxs-lookup"><span data-stu-id="1ba7b-112">To protect your global administrator accounts, Microsoft is here to help you with detailed instructions to:</span></span>
  
1. <span data-ttu-id="1ba7b-113">Cree cuentas dedicadas de administrador global de Office 365 y úselas solo cuando sea necesario.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-113">Create dedicated Office 365 global administrator accounts and use them only when necessary.</span></span>
    
2. <span data-ttu-id="1ba7b-114">Configure multi-factor Authentication para las cuentas de administrador global de Office 365 y use la forma más segura de autenticación secundaria.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-114">Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of secondary authentication.</span></span>
    
3. <span data-ttu-id="1ba7b-115">Habilitar y configurar Office 365 Cloud App Security para supervisar la actividad de una cuenta de administrador global sospechosa.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-115">Enable and configure Office 365 Cloud App Security to monitor for suspicious global administrator account activity.</span></span>
    
> [!NOTE]
> <span data-ttu-id="1ba7b-116">Aunque este artículo se centra en las cuentas de administrador global, también debe tener en cuenta si hay cuentas adicionales con amplios permisos de acceso a los datos de la suscripción, como administrador de eDiscovery o seguridad o cumplimiento. las cuentas de administrador deben protegerse del mismo modo.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-116">Although this article is focused on global administrator accounts, you should also consider whether additional accounts with wide-ranging permissions to access the data in your subscription, such as eDiscovery administrator or security or compliance administrator accounts, should be protected in the same way.</span></span> 
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a><span data-ttu-id="1ba7b-117">Paso 1.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-117">Step 1.</span></span> <span data-ttu-id="1ba7b-118">Crear cuentas de administrador global de Office 365 dedicadas y usarlas solo cuando sea necesario</span><span class="sxs-lookup"><span data-stu-id="1ba7b-118">Create dedicated Office 365 global administrator accounts and use them only when necessary</span></span>

<span data-ttu-id="1ba7b-119">Hay relativamente pocas tareas administrativas, como asignar roles a cuentas de usuario, que requieran privilegios de administrador global.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-119">There are relatively few administrative tasks, such as assigning roles to user accounts, that require global administrator privileges.</span></span> <span data-ttu-id="1ba7b-120">Por lo tanto, en lugar de usar las cuentas de usuario diarias que tienen asignado el rol de administrador global, siga estos pasos:</span><span class="sxs-lookup"><span data-stu-id="1ba7b-120">Therefore, instead of using everyday user accounts that have been assigned the global admin role, do these steps:</span></span>
  
1. <span data-ttu-id="1ba7b-121">Determine el conjunto de cuentas de usuario a las que se ha asignado el rol de administrador global.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-121">Determine the set of user accounts that have been assigned the global admin role.</span></span> <span data-ttu-id="1ba7b-122">Puede hacerlo con este comando en el símbolo del sistema de módulo de Microsoft Azure Active Directory para Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="1ba7b-122">You can do this with this command at the Microsoft Azure Active Directory Module for Windows PowerShell command prompt:</span></span>
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

2. <span data-ttu-id="1ba7b-123">Inicie sesión en su suscripción a Office 365 con una cuenta de usuario a la que se le haya asignado el rol de administrador global.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-123">Sign into your Office 365 subscription with a user account that has been assigned the global admin role.</span></span>
    
3. <span data-ttu-id="1ba7b-124">Cree al menos una y hasta un máximo de cinco cuentas de usuario de administrador global dedicadas.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-124">Create at least one and up to a maximum of five dedicated global administrator user accounts.</span></span> <span data-ttu-id="1ba7b-125">**Use contraseñas seguras con un mínimo de 12 caracteres de longitud.**</span><span class="sxs-lookup"><span data-stu-id="1ba7b-125">**Use strong passwords at least 12 characters long.**</span></span> <span data-ttu-id="1ba7b-126">Vea [crear una contraseña segura](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-126">See [Create a strong password](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) for more information.</span></span> <span data-ttu-id="1ba7b-127">Almacene las contraseñas de las cuentas nuevas en una ubicación segura.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-127">Store the passwords for the new accounts in a secure location.</span></span> 
    
4. <span data-ttu-id="1ba7b-128">Asigne el rol de administrador global a cada una de las nuevas cuentas de usuario de administrador global dedicadas.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-128">Assign the global admin role to each of the new dedicated global administrator user accounts.</span></span>
    
5. <span data-ttu-id="1ba7b-129">Cierre la sesión de Office 365.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-129">Sign out of Office 365.</span></span>
    
6. <span data-ttu-id="1ba7b-130">Inicie sesión con una de las nuevas cuentas de usuario de administrador global dedicadas.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-130">Sign in with one of the new dedicated global administrator user accounts.</span></span>
    
7. <span data-ttu-id="1ba7b-131">Para cada cuenta de usuario existente a la que se le haya asignado el rol de administrador global del paso 1:</span><span class="sxs-lookup"><span data-stu-id="1ba7b-131">For each existing user account that had been assigned the global admin role from step 1:</span></span>
    
  - <span data-ttu-id="1ba7b-132">Quite el rol de administrador global.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-132">Remove the global admin role.</span></span>
    
  - <span data-ttu-id="1ba7b-133">Asigne roles de administrador a la cuenta que sean adecuados para la función y responsabilidad de la tarea del usuario.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-133">Assign admin roles to the account that are appropriate to that user's job function and responsibility.</span></span> <span data-ttu-id="1ba7b-134">Para obtener más información acerca de varios roles de administrador en Office 365, consulte [acerca de los roles de administrador de office 365](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span><span class="sxs-lookup"><span data-stu-id="1ba7b-134">For more information about various admin roles in Office 365, see [About Office 365 admin roles](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span></span>
    
8. <span data-ttu-id="1ba7b-135">Cierre la sesión de Office 365.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-135">Sign out of Office 365.</span></span>
    
<span data-ttu-id="1ba7b-136">El resultado debe ser:</span><span class="sxs-lookup"><span data-stu-id="1ba7b-136">The result should be:</span></span>
  
- <span data-ttu-id="1ba7b-137">Las únicas cuentas de usuario de su suscripción que tienen el rol de administrador global son aquellas pertenecientes al nuevo conjunto de cuentas de administrador global dedicadas.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-137">The only user accounts in your subscription that have the global admin role are the new set of dedicated global administrator accounts.</span></span> <span data-ttu-id="1ba7b-138">Compruebe esto con el siguiente comando de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="1ba7b-138">Verify this with the following PowerShell command:</span></span>
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

- <span data-ttu-id="1ba7b-139">El resto de las cuentas de usuario habituales que administran la suscripción tienen asignados roles de administrador que están asociados con las funciones del puesto.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-139">All other everyday user accounts that manage your subscription have admin roles assigned that are associated with their job responsibilities.</span></span>
    
<span data-ttu-id="1ba7b-140">A partir de este momento, podrá iniciar sesión con las cuentas de administrador global dedicada solo para tareas que requieran privilegios de administrador global.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-140">From this moment onward, you sign in with the dedicated global administrator accounts only for tasks that require global administrator privileges.</span></span> <span data-ttu-id="1ba7b-141">El resto de la administración de Office 365 debe realizarse asignando otros roles de administración a las cuentas de usuario.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-141">All other Office 365 administration must be done by assigning other administration roles to user accounts.</span></span>
  
> [!NOTE]
> <span data-ttu-id="1ba7b-142">Sí, esto requiere unos pasos adicionales para cerrar la sesión como su cuenta de usuario diaria e iniciar sesión con una cuenta de administrador global dedicada.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-142">Yes, this requires additional steps to sign out as your everyday user account and sign in with a dedicated global administrator account.</span></span> <span data-ttu-id="1ba7b-143">Pero esto solo debe realizarse ocasionalmente para las operaciones de administrador global.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-143">But this only needs to be done occasionally for global administrator operations.</span></span> <span data-ttu-id="1ba7b-144">Considere la posibilidad de recuperar su suscripción de Office 365 después de una infracción de la cuenta de administrador global requiere muchos pasos más.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-144">Consider that recovering your Office 365 subscription after a global administrator account breach requires a lot more steps.</span></span> 
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-secondary-authentication"></a><span data-ttu-id="1ba7b-145">Paso 2.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-145">Step 2.</span></span> <span data-ttu-id="1ba7b-146">Configurar la autenticación multifactor para las cuentas de administrador global de Office 365 dedicadas y usar la forma más segura de autenticación secundaria</span><span class="sxs-lookup"><span data-stu-id="1ba7b-146">Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of secondary authentication</span></span>

<span data-ttu-id="1ba7b-147">La autenticación multifactor (MFA) para las cuentas de administrador global requiere información adicional aparte del nombre y la contraseña de la cuenta.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-147">Multi-factor authentication (MFA) for your global administrator accounts requires additional information beyond the account name and password.</span></span> <span data-ttu-id="1ba7b-148">Office 365 admite estos métodos de comprobación:</span><span class="sxs-lookup"><span data-stu-id="1ba7b-148">Office 365 supports these verification methods:</span></span>
  
- <span data-ttu-id="1ba7b-149">Una llamada de teléfono</span><span class="sxs-lookup"><span data-stu-id="1ba7b-149">A phone call</span></span>
    
- <span data-ttu-id="1ba7b-150">Un código de acceso generado de forma aleatoria</span><span class="sxs-lookup"><span data-stu-id="1ba7b-150">A randomly generated pass code</span></span>
    
- <span data-ttu-id="1ba7b-151">Una tarjeta inteligente (física o virtual)</span><span class="sxs-lookup"><span data-stu-id="1ba7b-151">A smart card (virtual or physical)</span></span>
    
- <span data-ttu-id="1ba7b-152">Un dispositivo biométrico</span><span class="sxs-lookup"><span data-stu-id="1ba7b-152">A biometric device</span></span>
    
<span data-ttu-id="1ba7b-153">Si es una pequeña empresa que usa cuentas de usuario almacenadas solo en la nube (el modelo de identidad de nube), use estos pasos para configurar la MFA con una llamada de teléfono o un código de verificación de mensaje de texto enviado a un teléfono inteligente:</span><span class="sxs-lookup"><span data-stu-id="1ba7b-153">If you are a small business that is using user accounts stored only in the cloud (the cloud identity model), use these steps to configure MFA using a phone call or a text message verification code sent to a smart phone:</span></span>
  
1. <span data-ttu-id="1ba7b-154">[Habilitar MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span><span class="sxs-lookup"><span data-stu-id="1ba7b-154">[Enable MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span></span>
    
2. <span data-ttu-id="1ba7b-155">[Configure la verificación en dos pasos para Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) para configurar cada cuenta de administrador global dedicada para la llamada telefónica o mensaje de texto como el método de verificación.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-155">[Set up 2-step verification for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for phone call or text message as the verification method.</span></span> 
    
<span data-ttu-id="1ba7b-156">Si es una organización de mayor tamaño que usa un modelo de identidad híbrida de Office 365, tiene más opciones de comprobación.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-156">If you are a larger organization that is using an Office 365 hybrid identity model, you have more verification options.</span></span> <span data-ttu-id="1ba7b-157">Si ya ha implementado la infraestructura de seguridad para obtener un método de autenticación secundaria más seguro, siga estos pasos:</span><span class="sxs-lookup"><span data-stu-id="1ba7b-157">If you have the security infrastructure already in place for a stronger secondary authentication method, use these steps:</span></span>
  
1. <span data-ttu-id="1ba7b-158">[Habilitar MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span><span class="sxs-lookup"><span data-stu-id="1ba7b-158">[Enable MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span></span>
    
2. <span data-ttu-id="1ba7b-159">[Configure la verificación en dos pasos para Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) para configurar cada cuenta de administrador global dedicada para el método de verificación adecuado.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-159">[Set up 2-step verification for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for the appropriate verification method.</span></span> 
    
<span data-ttu-id="1ba7b-160">Si la infraestructura de seguridad para el método de comprobación más seguro deseado no está en vigor y no funciona para Office 365 MFA, se recomienda encarecidamente que configure cuentas de administrador global dedicadas con MFA mediante una llamada de teléfono o un mensaje de texto. código de verificación enviado a un teléfono inteligente para sus cuentas de administrador global como medida de seguridad provisional.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-160">If the security infrastructure for the desired stronger verification method is not in place and functioning for Office 365 MFA, we strongly recommend that you configure dedicated global administrator accounts with MFA using a phone call or a text message verification code sent to a smart phone for your global administrator accounts as an interim security measure.</span></span> <span data-ttu-id="1ba7b-161">No deje las cuentas de administrador global dedicadas sin la protección adicional que proporciona MFA.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-161">Do not leave your dedicated global administrator accounts without the additional protection provided by MFA.</span></span>
  
<span data-ttu-id="1ba7b-162">Para obtener más información, vea [Planear la autenticación multifactor para implementaciones de Office 365](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba).</span><span class="sxs-lookup"><span data-stu-id="1ba7b-162">For more information, see [Plan for multi-factor authentication for Office 365 Deployments](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba).</span></span>
  
<span data-ttu-id="1ba7b-163">Para conectarse a los servicios de Office 365 con MFA y PowerShell, consulte [este artículo](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/).</span><span class="sxs-lookup"><span data-stu-id="1ba7b-163">To connect to Office 365 services with MFA and PowerShell, see [this article](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/).</span></span>
  
## <a name="step-3-monitor-for-suspicious-global-administrator-account-activity"></a><span data-ttu-id="1ba7b-164">Paso 3.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-164">Step 3.</span></span> <span data-ttu-id="1ba7b-165">Supervisar la actividad de una cuenta de administrador global sospechosa</span><span class="sxs-lookup"><span data-stu-id="1ba7b-165">Monitor for suspicious global administrator account activity</span></span>

<span data-ttu-id="1ba7b-166">Office 365 Cloud App Security le permite crear directivas para notificar un comportamiento sospechoso en su suscripción.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-166">Office 365 Cloud App Security lets you create policies to notify you of suspicious behavior in your subscription.</span></span> <span data-ttu-id="1ba7b-167">Cloud App Security está integrada en Office 365 E5, pero también está disponible como un servicio independiente.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-167">Cloud App Security is built into Office 365 E5, but is also available as a separate service.</span></span> <span data-ttu-id="1ba7b-168">Por ejemplo, si no tiene Office 365 E5, puede comprar licencias de seguridad de aplicaciones de nube individuales para las cuentas de usuario que tienen asignados los roles de administrador global, administrador de seguridad y administrador de cumplimiento.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-168">For example, if you do not have Office 365 E5, you can purchase individual Cloud App Security licenses for the user accounts that are assigned the global administrator, security administrator, and compliance administrator roles.</span></span>
  
<span data-ttu-id="1ba7b-169">Si tiene Cloud App Security en su suscripción a Office 365, siga estos pasos:</span><span class="sxs-lookup"><span data-stu-id="1ba7b-169">If you have Cloud App Security in your Office 365 subscription, use these steps:</span></span>
  
1. <span data-ttu-id="1ba7b-170">Inicie sesión en el centro de administración de Microsoft 365 con una cuenta que tenga asignado el rol de administrador de seguridad o administrador de cumplimiento.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-170">Sign into the Microsoft 365 admin center with an account that is assigned the Security Administrator or Compliance Administrator role.</span></span>
    
2. <span data-ttu-id="1ba7b-171">[Active Office 365 Cloud App Security](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c).</span><span class="sxs-lookup"><span data-stu-id="1ba7b-171">[Turn on Office 365 Cloud App Security](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c).</span></span>
    
3. <span data-ttu-id="1ba7b-172">Revise sus [directivas de detección de anomalías en Office 365 Cloud App Security](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6) para notificarle por correo electrónico los patrones anómalos de actividad administrativa privilegiada.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-172">Review your [Anomaly detection policies in Office 365 Cloud App Security](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6) to notify you by email of anomalous patterns of privileged administrative activity.</span></span> 
    
<span data-ttu-id="1ba7b-173">Para agregar una cuenta de usuario a la función de administrador de seguridad, [Conéctese a Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx#step3) con una cuenta de administrador global y una MFA dedicadas, rellene el nombre principal de usuario de la cuenta de usuario y, a continuación, ejecute estos comandos:</span><span class="sxs-lookup"><span data-stu-id="1ba7b-173">To add a user account to the Security Administrator role, [connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx#step3) with a dedicated global administrator account and MFA, fill in the user principal name of the user account, and then run these commands:</span></span> 
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upn -RoleName "Security Administrator"
```

<span data-ttu-id="1ba7b-174">Para agregar una cuenta de usuario al rol de administrador de cumplimiento, escriba el nombre principal de usuario de la cuenta de usuario y ejecute estos comandos:</span><span class="sxs-lookup"><span data-stu-id="1ba7b-174">To add a user account to the Compliance Administrator role, fill in the user principal name of the user account, and then run these commands:</span></span>
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress  $upn -RoleName "Compliance Administrator"
```

## <a name="additional-protections-for-enterprise-organizations"></a><span data-ttu-id="1ba7b-175">Protecciones adicionales para organizaciones empresariales</span><span class="sxs-lookup"><span data-stu-id="1ba7b-175">Additional protections for enterprise organizations</span></span>

<span data-ttu-id="1ba7b-176">Después de los pasos 1-3, use estos métodos adicionales para asegurarse de que su cuenta de administrador global y la configuración que realiza con ella son lo más seguras posible.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-176">After steps 1-3, use these additional methods to ensure that your global administrator account, and the configuration that you perform using it, are as secure as possible.</span></span>
  
### <a name="privileged-access-workstation-paw"></a><span data-ttu-id="1ba7b-177">Estación de trabajo de acceso con privilegios (pata)</span><span class="sxs-lookup"><span data-stu-id="1ba7b-177">Privileged Access Workstation (PAW)</span></span>

<span data-ttu-id="1ba7b-178">Para asegurarse de que la ejecución de las tareas con privilegios elevados es lo más segura posible, use un pata.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-178">To ensure that the execution of highly privileged tasks is as secure as possible, use a PAW.</span></span> <span data-ttu-id="1ba7b-179">Una pata es un equipo dedicado que solo se usa para tareas de configuración confidenciales, como la configuración de Office 365 que requiere una cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-179">A PAW is a dedicated computer that is only used for sensitive configuration tasks, such as Office 365 configuration that requires a global administrator account.</span></span> <span data-ttu-id="1ba7b-180">Como este equipo no se usa diariamente para la exploración de Internet o el correo electrónico, es mejor estar protegido frente a ataques y amenazas de Internet.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-180">Because this computer is not used daily for Internet browsing or email, it is better protected from Internet attacks and threats.</span></span>
  
<span data-ttu-id="1ba7b-181">Para obtener instrucciones sobre cómo configurar un pata, mira [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw).</span><span class="sxs-lookup"><span data-stu-id="1ba7b-181">For instructions on how to set up a PAW, see [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw).</span></span>
  
### <a name="azure-ad-privileged-identity-management-pim"></a><span data-ttu-id="1ba7b-182">Azure AD privileged Identity Management (PIM)</span><span class="sxs-lookup"><span data-stu-id="1ba7b-182">Azure AD Privileged Identity Management (PIM)</span></span>

<span data-ttu-id="1ba7b-183">En lugar de tener sus cuentas de administrador global asignadas permanentemente al rol de administrador global, puede usar Azure AD PIM para habilitar la asignación Just-in-Time del rol de administrador global cuando sea necesario.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-183">Rather than having your global administrator accounts be permanently assigned the global administrator role, you can use Azure AD PIM to enable on-demand, just-in-time assignment of the global administrator role when it is needed.</span></span>
  
<span data-ttu-id="1ba7b-184">En lugar de las cuentas de administrador global que son administradores permanentes, se convierten en administradores elegibles.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-184">Instead of your global administrator accounts being a permanent admin, they become eligible administrators.</span></span> <span data-ttu-id="1ba7b-185">El rol de administrador global está inactivo hasta que alguien lo necesita.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-185">The global administrator role is inactive until someone needs it.</span></span> <span data-ttu-id="1ba7b-186">A continuación, debe completar un proceso de activación para agregar el rol de administrador global a la cuenta de administrador global para un período de tiempo predeterminado.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-186">You then complete an activation process to add the global administrator role to the global administrator account for a predetermined amount of time.</span></span> <span data-ttu-id="1ba7b-187">Cuando expira el tiempo, PIM quita el rol de administrador global de la cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-187">When the time expires, PIM removes the global administrator role from the global administrator account.</span></span>
  
<span data-ttu-id="1ba7b-188">El uso de PIM y este proceso reduce considerablemente la cantidad de tiempo que las cuentas de administrador global son vulnerables a ataques y uso de usuarios malintencionados.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-188">Using PIM and this process significantly reduces the amount of time that your global administrator accounts are vulnerable to attack and use by malicious users.</span></span>
  
<span data-ttu-id="1ba7b-189">Para obtener más información, consulte [Configure Azure ad privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).</span><span class="sxs-lookup"><span data-stu-id="1ba7b-189">For more information, see [Configure Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).</span></span>
  
> [!NOTE]
> <span data-ttu-id="1ba7b-190">PIM está disponible con Azure Active Directory Premium P2, que se incluye con Enterprise Mobility + Security (EMS) E5, o puede comprar licencias individuales para sus cuentas de administrador global.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-190">PIM is available with Azure Active Directory Premium P2, which is included with Enterprise Mobility + Security (EMS) E5, or you can purchase individual licenses for your global administrator accounts.</span></span> 
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a><span data-ttu-id="1ba7b-191">Software de administración de eventos e información de seguridad (SIEM) para el registro de Office 365</span><span class="sxs-lookup"><span data-stu-id="1ba7b-191">Security information and event management (SIEM) software for Office 365 logging</span></span>

<span data-ttu-id="1ba7b-192">El software de SIEM se ejecuta en un servidor realiza un análisis en tiempo real de los eventos y las alertas de seguridad creados por las aplicaciones y el hardware de red.</span><span class="sxs-lookup"><span data-stu-id="1ba7b-192">SIEM software run on a server performs real-time analysis of security alerts and events created by applications and network hardware.</span></span> <span data-ttu-id="1ba7b-193">Para permitir que el servidor de SIEM incluya eventos y alertas de seguridad de Office 365 en sus funciones de análisis e informes, integre estos en su sistema SIEM:</span><span class="sxs-lookup"><span data-stu-id="1ba7b-193">To allow your SIEM server to include Office 365 security alerts and events in its analysis and reporting functions, integrate these in your SIEM system:</span></span>
  
- <span data-ttu-id="1ba7b-194">Azure AD</span><span class="sxs-lookup"><span data-stu-id="1ba7b-194">Azure AD</span></span>
    
    <span data-ttu-id="1ba7b-195">Para obtener más información, consulte [integrar registros de recursos de Azure en sus sistemas Siem](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).</span><span class="sxs-lookup"><span data-stu-id="1ba7b-195">For more information, see [Integrate logs from Azure resources into your SIEM systems](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).</span></span>
    
- <span data-ttu-id="1ba7b-196">Office 365 Cloud App Security</span><span class="sxs-lookup"><span data-stu-id="1ba7b-196">Office 365 Cloud App Security</span></span>
    
    <span data-ttu-id="1ba7b-197">Para obtener más información, consulte [integrar el servidor de Siem con Office 365 Cloud App Security](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532).</span><span class="sxs-lookup"><span data-stu-id="1ba7b-197">For more information, see [Integrate your SIEM server with Office 365 Cloud App Security](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532).</span></span>
    
## <a name="next-step"></a><span data-ttu-id="1ba7b-198">Paso siguiente</span><span class="sxs-lookup"><span data-stu-id="1ba7b-198">Next step</span></span>

<span data-ttu-id="1ba7b-199">Vea [procedimientos recomendados de seguridad para Office 365](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3).</span><span class="sxs-lookup"><span data-stu-id="1ba7b-199">See [Security best practices for Office 365](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3).</span></span>
  

