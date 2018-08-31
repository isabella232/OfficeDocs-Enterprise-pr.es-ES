---
title: Protección de las cuentas de administrador global de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 4/10/2018
ms.audience: Admin
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
description: Proteger el acceso de administrador global para la suscripción a Office 365 con estos tres pasos.
ms.openlocfilehash: 7260e903ea007735c87ab8aa826e3b97e7bd28c1
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542954"
---
# <a name="protect-your-office-365-global-administrator-accounts"></a><span data-ttu-id="f020c-103">Protección de las cuentas de administrador global de Office 365</span><span class="sxs-lookup"><span data-stu-id="f020c-103">Protect your Office 365 global administrator accounts</span></span>

 <span data-ttu-id="f020c-104">**Resumen:** Proteger su suscripción de Office 365 de los ataques basados en el compromiso de una cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="f020c-104">**Summary:** Protect your Office 365 subscription from attacks based on the compromise of a global administrator account.</span></span> 
  
<span data-ttu-id="f020c-p101">Las infracciones de seguridad de una suscripción de Office 365, incluyendo la recopilación de información y los ataques de suplantación de identidad, normalmente se realiza por poner en peligro las credenciales de una cuenta de administrador global de Office 365. Seguridad en la nube es una asociación entre usted y Microsoft:</span><span class="sxs-lookup"><span data-stu-id="f020c-p101">Security breaches of an Office 365 subscription, including information harvesting and phishing attacks, are typically done by compromising the credentials of an Office 365 global administrator account. Security in the cloud is a partnership between you and Microsoft:</span></span>
  
- <span data-ttu-id="f020c-p102">Servicios de nube de Microsoft se basan en una base de seguridad y confianza. Microsoft proporciona controles de seguridad y las capacidades que le ayudarán a proteger los datos y aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="f020c-p102">Microsoft cloud services are built on a foundation of trust and security. Microsoft provides you security controls and capabilities to help you protect your data and applications.</span></span>
    
- <span data-ttu-id="f020c-109">Propietario de los datos y las identidades y la responsabilidad de protección, la seguridad de los recursos locales y la seguridad de los componentes de la nube, controlar.</span><span class="sxs-lookup"><span data-stu-id="f020c-109">You own your data and identities and the responsibility for protecting them, the security of your on-premises resources, and the security of cloud components you control.</span></span>
    
<span data-ttu-id="f020c-p103">Microsoft proporciona capacidades para ayudar a proteger su organización, pero son efectivos sólo si los utiliza. Si no se utiliza, puede ser vulnerable a un ataque. Para proteger las cuentas de administrador global, Microsoft está aquí para ayudarle con instrucciones detalladas para:</span><span class="sxs-lookup"><span data-stu-id="f020c-p103">Microsoft provides capabilities to help protect your organization, but they are effective only if you use them. If you do not use them, you may be vulnerable to attack. To protect your global administrator accounts, Microsoft is here to help you with detailed instructions to:</span></span>
  
1. <span data-ttu-id="f020c-113">Crear cuentas de administrador global de Office 365 dedicadas y utilizarlos sólo cuando sea necesario.</span><span class="sxs-lookup"><span data-stu-id="f020c-113">Create dedicated Office 365 global administrator accounts and use them only when necessary.</span></span>
    
2. <span data-ttu-id="f020c-114">Configuración de la autenticación multifactor para las cuentas de administrador global de Office 365 dedicadas y usar la forma más segura de autenticación secundaria.</span><span class="sxs-lookup"><span data-stu-id="f020c-114">Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of secondary authentication.</span></span>
    
3. <span data-ttu-id="f020c-115">Habilitar y configurar la seguridad de aplicación de Office 365 en la nube para supervisar la actividad de la cuenta de administrador global sospechosos.</span><span class="sxs-lookup"><span data-stu-id="f020c-115">Enable and configure Office 365 Cloud App Security to monitor for suspicious global administrator account activity.</span></span>
    
> [!NOTE]
> <span data-ttu-id="f020c-116">Aunque en este artículo se centra en las cuentas de administrador global, también debe considerar si adicionales cuentas con los permisos tan amplios para tener acceso a los datos en su suscripción, como administrador de la exhibición de documentos electrónicos o de cumplimiento de normas o de seguridad las cuentas de administrador, se deben proteger de la misma manera.</span><span class="sxs-lookup"><span data-stu-id="f020c-116">Although this article is focused on global administrator accounts, you should also consider whether additional accounts with wide-ranging permissions to access the data in your subscription, such as eDiscovery administrator or security or compliance administrator accounts, should be protected in the same way.</span></span> 
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a><span data-ttu-id="f020c-p104">Paso 1. Crear cuentas de administrador global de Office 365 dedicadas y utilizarlos sólo cuando sea necesario</span><span class="sxs-lookup"><span data-stu-id="f020c-p104">Step 1. Create dedicated Office 365 global administrator accounts and use them only when necessary</span></span>

<span data-ttu-id="f020c-p105">Hay relativamente pocas tareas administrativas, como la asignación de roles a las cuentas de usuario, que requieren privilegios de administrador global. Por lo tanto, en lugar de usar cuentas de usuario cotidianas que ha asignado el rol de administrador global, siga estos pasos:</span><span class="sxs-lookup"><span data-stu-id="f020c-p105">There are relatively few administrative tasks, such as assigning roles to user accounts, that require global administrator privileges. Therefore, instead of using everyday user accounts that have been assigned the global admin role, do these steps:</span></span>
  
1. <span data-ttu-id="f020c-p106">Determinar el conjunto de cuentas de usuario que ha asignado el rol de administrador global. Puede hacerlo con este comando en el símbolo del sistema de Microsoft Azure Active Directory módulo para Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="f020c-p106">Determine the set of user accounts that have been assigned the global admin role. You can do this with this command at the Microsoft Azure Active Directory Module for Windows PowerShell command prompt:</span></span>
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

2. <span data-ttu-id="f020c-123">Inicie sesión en su suscripción de Office 365 con una cuenta de usuario que se ha asignado el rol de administrador global.</span><span class="sxs-lookup"><span data-stu-id="f020c-123">Sign into your Office 365 subscription with a user account that has been assigned the global admin role.</span></span>
    
3. <span data-ttu-id="f020c-p107">Cree al menos uno y hasta un máximo de cinco dedicado las cuentas de usuario de administrador global. **Caracteres de largo contraseñas seguras al menos 12 uso.** Para obtener más información, vea [crear una contraseña segura](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) . Almacenar las contraseñas de las cuentas de nuevo en una ubicación segura.</span><span class="sxs-lookup"><span data-stu-id="f020c-p107">Create at least one and up to a maximum of five dedicated global administrator user accounts. **Use strong passwords at least 12 characters long.** See [Create a strong password](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) for more information. Store the passwords for the new accounts in a secure location.</span></span> 
    
4. <span data-ttu-id="f020c-128">Asignar el rol de administrador global a cada una de las cuentas de usuario de administrador global nuevo dedicado.</span><span class="sxs-lookup"><span data-stu-id="f020c-128">Assign the global admin role to each of the new dedicated global administrator user accounts.</span></span>
    
5. <span data-ttu-id="f020c-129">Cerrar la sesión de Office 365.</span><span class="sxs-lookup"><span data-stu-id="f020c-129">Sign out of Office 365.</span></span>
    
6. <span data-ttu-id="f020c-130">Inicie sesión con una de las nuevas cuentas de usuario de administrador global dedicado.</span><span class="sxs-lookup"><span data-stu-id="f020c-130">Sign in with one of the new dedicated global administrator user accounts.</span></span>
    
7. <span data-ttu-id="f020c-131">Para cada cuenta de usuario existente que está asignado el rol de administrador global desde el paso 1:</span><span class="sxs-lookup"><span data-stu-id="f020c-131">For each existing user account that had been assigned the global admin role from step 1:</span></span>
    
  - <span data-ttu-id="f020c-132">Quite el rol de administrador global.</span><span class="sxs-lookup"><span data-stu-id="f020c-132">Remove the global admin role.</span></span>
    
  - <span data-ttu-id="f020c-p108">Asignar roles de administrador a la cuenta de que son adecuados para la función de trabajo y la responsabilidad de dicho usuario. Para obtener más información acerca de diversos roles de administración de Office 365, vea [roles de administrador acerca de Office 365](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span><span class="sxs-lookup"><span data-stu-id="f020c-p108">Assign admin roles to the account that are appropriate to that user's job function and responsibility. For more information about various admin roles in Office 365, see [About Office 365 admin roles](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span></span>
    
8. <span data-ttu-id="f020c-135">Cerrar la sesión de Office 365.</span><span class="sxs-lookup"><span data-stu-id="f020c-135">Sign out of Office 365.</span></span>
    
<span data-ttu-id="f020c-136">El resultado debería ser:</span><span class="sxs-lookup"><span data-stu-id="f020c-136">The result should be:</span></span>
  
- <span data-ttu-id="f020c-p109">Las cuentas de usuario sólo en la suscripción que tienen la función de administrador global son el nuevo conjunto de cuentas de administrador global dedicado. Para comprobar esto con el siguiente comando de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="f020c-p109">The only user accounts in your subscription that have the global admin role are the new set of dedicated global administrator accounts. Verify this with the following PowerShell command:</span></span>
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

- <span data-ttu-id="f020c-139">El resto de las cuentas de usuario habituales que administran la suscripción tienen asignados roles de administrador que están asociados con las funciones del puesto.</span><span class="sxs-lookup"><span data-stu-id="f020c-139">All other everyday user accounts that manage your subscription have admin roles assigned that are associated with their job responsibilities.</span></span>
    
<span data-ttu-id="f020c-p110">Desde este momento en adelante, iniciar sesión con las cuentas de administrador global dedicado sólo para las tareas que requieren privilegios de administrador global. Otro tipo de administración de Office 365 debe realizarse mediante la asignación de otras funciones de administración a cuentas de usuario.</span><span class="sxs-lookup"><span data-stu-id="f020c-p110">From this moment onward, you sign in with the dedicated global administrator accounts only for tasks that require global administrator privileges. All other Office 365 administration must be done by assigning other administration roles to user accounts.</span></span>
  
> [!NOTE]
> <span data-ttu-id="f020c-p111">Sí, esto requiere pasos adicionales para cerrar la sesión como la cuenta de usuario cotidianas e iniciar sesión con una cuenta de administrador global dedicado. Pero esto sólo necesita realizarse cada cierto tiempo para operaciones de administrador global. Tenga en cuenta la recuperación después de una infracción de la cuenta de administrador global requiere mucho más pasos de su suscripción de Office 365.</span><span class="sxs-lookup"><span data-stu-id="f020c-p111">Yes, this requires additional steps to sign out as your everyday user account and sign in with a dedicated global administrator account. But this only needs to be done occasionally for global administrator operations. Consider that recovering your Office 365 subscription after a global administrator account breach requires a lot more steps.</span></span> 
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-secondary-authentication"></a><span data-ttu-id="f020c-p112">Paso 2. Configuración de la autenticación multifactor para las cuentas de administrador global de Office 365 dedicadas y usar la forma más segura de autenticación secundaria</span><span class="sxs-lookup"><span data-stu-id="f020c-p112">Step 2. Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of secondary authentication</span></span>

<span data-ttu-id="f020c-p113">Autenticación multifactor (MFA) para las cuentas de administrador global requiere información adicional más allá del nombre de cuenta y la contraseña. Office 365 admite los siguientes métodos de comprobación:</span><span class="sxs-lookup"><span data-stu-id="f020c-p113">Multi-factor authentication (MFA) for your global administrator accounts requires additional information beyond the account name and password. Office 365 supports these verification methods:</span></span>
  
- <span data-ttu-id="f020c-149">Una llamada de teléfono</span><span class="sxs-lookup"><span data-stu-id="f020c-149">A phone call</span></span>
    
- <span data-ttu-id="f020c-150">Un código de acceso generado de forma aleatoria</span><span class="sxs-lookup"><span data-stu-id="f020c-150">A randomly generated pass code</span></span>
    
- <span data-ttu-id="f020c-151">Una tarjeta inteligente (virtual o física)</span><span class="sxs-lookup"><span data-stu-id="f020c-151">A smart card (virtual or physical)</span></span>
    
- <span data-ttu-id="f020c-152">Un dispositivo biométrico</span><span class="sxs-lookup"><span data-stu-id="f020c-152">A biometric device</span></span>
    
<span data-ttu-id="f020c-153">Si es una pequeña empresa que está usando las cuentas de usuario que se almacenan solo en la nube (el modelo de identidad en la nube), siga estos pasos para configurar MFA mediante una llamada telefónica o un código de comprobación de mensaje de texto enviado a un teléfono inteligente:</span><span class="sxs-lookup"><span data-stu-id="f020c-153">If you are a small business that is using user accounts stored only in the cloud (the cloud identity model), use these steps to configure MFA using a phone call or a text message verification code sent to a smart phone:</span></span>
  
1. <span data-ttu-id="f020c-154">[Habilitar MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span><span class="sxs-lookup"><span data-stu-id="f020c-154">[Enable MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span></span>
    
2. <span data-ttu-id="f020c-155">[Conjunto de copia de seguridad - paso 2 de comprobación para Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) para configurar cada uno dedicado cuenta de administrador global para la llamada de teléfono o mensaje de texto como el método de comprobación.</span><span class="sxs-lookup"><span data-stu-id="f020c-155">[Set up 2-step verification for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for phone call or text message as the verification method.</span></span> 
    
<span data-ttu-id="f020c-p114">Si es una organización más grande que usa un modelo de identidad de Office 365 híbrida, tiene más opciones de comprobación. Si ya tiene la infraestructura de seguridad en lugar de un método de autenticación secundario más seguro, siga estos pasos:</span><span class="sxs-lookup"><span data-stu-id="f020c-p114">If you are a larger organization that is using an Office 365 hybrid identity model, you have more verification options. If you have the security infrastructure already in place for a stronger secondary authentication method, use these steps:</span></span>
  
1. <span data-ttu-id="f020c-158">[Habilitar MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span><span class="sxs-lookup"><span data-stu-id="f020c-158">[Enable MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span></span>
    
2. <span data-ttu-id="f020c-159">[Conjunto de copia de seguridad - paso 2 de comprobación para Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) para configurar cada uno dedicado cuenta de administrador global para el método de comprobación adecuada.</span><span class="sxs-lookup"><span data-stu-id="f020c-159">[Set up 2-step verification for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for the appropriate verification method.</span></span> 
    
<span data-ttu-id="f020c-p115">Si la infraestructura de seguridad para el método de comprobación más sólida deseada no está en contexto y el funcionamiento de Office 365 MFA, recomendamos encarecidamente que configure las cuentas de administrador global dedicado con MFA mediante una llamada telefónica o un mensaje de texto código de verificación enviado a un teléfono inteligente para las cuentas de administrador global como una medida de seguridad provisional. No deje las cuentas de administrador global dedicado sin la protección adicional proporcionada por MFA.</span><span class="sxs-lookup"><span data-stu-id="f020c-p115">If the security infrastructure for the desired stronger verification method is not in place and functioning for Office 365 MFA, we strongly recommend that you configure dedicated global administrator accounts with MFA using a phone call or a text message verification code sent to a smart phone for your global administrator accounts as an interim security measure. Do not leave your dedicated global administrator accounts without the additional protection provided by MFA.</span></span>
  
<span data-ttu-id="f020c-162">Para obtener más información, vea [Planear la autenticación multifactor para implementaciones de Office 365](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba).</span><span class="sxs-lookup"><span data-stu-id="f020c-162">For more information, see [Plan for multi-factor authentication for Office 365 Deployments](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba).</span></span>
  
<span data-ttu-id="f020c-163">Para conectarse a servicios de Office 365 con MFA y PowerShell, vea [este artículo](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/).</span><span class="sxs-lookup"><span data-stu-id="f020c-163">To connect to Office 365 services with MFA and PowerShell, see [this article](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/).</span></span>
  
## <a name="step-3-monitor-for-suspicious-global-administrator-account-activity"></a><span data-ttu-id="f020c-p116">Paso 3. Monitor de actividad de la cuenta de administrador global sospechosos</span><span class="sxs-lookup"><span data-stu-id="f020c-p116">Step 3. Monitor for suspicious global administrator account activity</span></span>

<span data-ttu-id="f020c-p117">Seguridad de la aplicación en la nube Office 365 le permite crear directivas para notificar de comportamiento sospechoso en su suscripción. Seguridad de la aplicación en la nube está integrada en Office 365 E5, pero también está disponible como un servicio independiente. Por ejemplo, si no tiene Office 365 E5, puede comprar licencias individuales de seguridad de la aplicación en la nube para las cuentas de usuario que se asignan el administrador global, Administrador de seguridad y roles de administrador de cumplimiento de normas.</span><span class="sxs-lookup"><span data-stu-id="f020c-p117">Office 365 Cloud App Security allows you to create policies to notify you of suspicious behavior in your subscription. Cloud App Security is built into Office 365 E5, but is also available as a separate service. For example, if you do not have Office 365 E5, you can purchase individual Cloud App Security licenses for the user accounts that are assigned the global administrator, security administrator, and compliance administrator roles.</span></span>
  
<span data-ttu-id="f020c-169">Si tiene la seguridad de la aplicación en la nube en su suscripción de Office 365, siga estos pasos:</span><span class="sxs-lookup"><span data-stu-id="f020c-169">If you have Cloud App Security in your Office 365 subscription, use these steps:</span></span>
  
1. <span data-ttu-id="f020c-170">Inicie sesión en el portal de Office 365 con una cuenta que está asignado el rol de administrador de seguridad o administrador de cumplimiento de normas.</span><span class="sxs-lookup"><span data-stu-id="f020c-170">Sign into the Office 365 portal with an account that is assigned the Security Administrator or Compliance Administrator role.</span></span>
    
2. <span data-ttu-id="f020c-171">[Activar la seguridad de la aplicación de Office 365 en la nube](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c).</span><span class="sxs-lookup"><span data-stu-id="f020c-171">[Turn on Office 365 Cloud App Security](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c).</span></span>
    
3. <span data-ttu-id="f020c-172">Revise las [directivas de detección de anomalías en la seguridad de la aplicación de Office 365 en la nube](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6) para recibir una notificación por correo electrónico de patrones anómalos de actividades administrativas con privilegios.</span><span class="sxs-lookup"><span data-stu-id="f020c-172">Review your [Anomaly detection policies in Office 365 Cloud App Security](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6) to notify you by email of anomalous patterns of privileged administrative activity.</span></span> 
    
<span data-ttu-id="f020c-173">Para agregar una cuenta de usuario a la función de administrador de seguridad, [conectarse a Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx#step3) con una cuenta de administrador global dedicado y MFA, rellene el nombre principal de usuario de la cuenta de usuario y, a continuación, ejecute estos comandos:</span><span class="sxs-lookup"><span data-stu-id="f020c-173">To add a user account to the Security Administrator role, [connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx#step3) with a dedicated global administrator account and MFA, fill in the user principal name of the user account, and then run these commands:</span></span> 
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upn -RoleName "Security Administrator"
```

<span data-ttu-id="f020c-174">Para agregar una cuenta de usuario a la función de administrador de cumplimiento de normas, rellene el nombre principal de usuario de la cuenta de usuario y, a continuación, ejecute estos comandos:</span><span class="sxs-lookup"><span data-stu-id="f020c-174">To add a user account to the Compliance Administrator role, fill in the user principal name of the user account, and then run these commands:</span></span>
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress  $upn -RoleName "Compliance Administrator"
```

## <a name="additional-protections-for-enterprise-organizations"></a><span data-ttu-id="f020c-175">Protecciones adicionales para las organizaciones empresariales</span><span class="sxs-lookup"><span data-stu-id="f020c-175">Additional protections for enterprise organizations</span></span>

<span data-ttu-id="f020c-176">Después de los pasos 1-3, utilizan estos métodos adicionales para asegurarse de que la cuenta de administrador global y la configuración que se realiza con él, son tan seguros como sea posible.</span><span class="sxs-lookup"><span data-stu-id="f020c-176">After steps 1-3, use these additional methods to ensure that your global administrator account, and the configuration that you perform using it, are as secure as possible.</span></span>
  
### <a name="privileged-access-workstation-paw"></a><span data-ttu-id="f020c-177">Estación de trabajo de Access con privilegios (PATA)</span><span class="sxs-lookup"><span data-stu-id="f020c-177">Privileged Access Workstation (PAW)</span></span>

<span data-ttu-id="f020c-p118">Para asegurarse de que la ejecución de tareas con muchos privilegios es tan segura como sea posible, use un PATA. Un PATA es un equipo dedicado que se utiliza únicamente para las tareas de configuración confidencial, como la configuración de Office 365 que requiere una cuenta de administrador global. Debido a que este equipo no se usa diariamente para correo electrónico o la exploración de Internet, está mejor protegido frente a las amenazas y ataques de Internet.</span><span class="sxs-lookup"><span data-stu-id="f020c-p118">To ensure that the execution of highly privileged tasks is as secure as possible, use a PAW. A PAW is a dedicated computer that is only used for sensitive configuration tasks, such as Office 365 configuration that requires a global administrator account. Because this computer is not used daily for Internet browsing or email, it is better protected from Internet attacks and threats.</span></span>
  
<span data-ttu-id="f020c-181">Para obtener instrucciones sobre cómo configurar un pata, consulte [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw).</span><span class="sxs-lookup"><span data-stu-id="f020c-181">For instructions on how to set up a PAW, see [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw).</span></span>
  
### <a name="azure-ad-privileged-identity-management-pim"></a><span data-ttu-id="f020c-182">Administración de identidades de Azure con privilegios de AD (PIM)</span><span class="sxs-lookup"><span data-stu-id="f020c-182">Azure AD Privileged Identity Management (PIM)</span></span>

<span data-ttu-id="f020c-183">En lugar de tener las cuentas de administrador global asignado de forma permanente la función de administrador global, puede usar Azure AD PIM para habilitar la asignación de petición, just-in-time de la función de administrador global cuando sea necesario.</span><span class="sxs-lookup"><span data-stu-id="f020c-183">Rather than having your global administrator accounts be permanently assigned the global administrator role, you can use Azure AD PIM to enable on-demand, just-in-time assignment of the global administrator role when it is needed.</span></span>
  
<span data-ttu-id="f020c-p119">En lugar de las cuentas de administrador global que se va a un administrador permanente, se convierten en administradores aptos. La función de administrador global está inactiva hasta que alguien la necesita. A continuación, complete un proceso de activación para agregar la función de administrador global para la cuenta de administrador global para un período de tiempo predeterminado. Cuando se agota el tiempo, PIM quita la función de administrador global de la cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="f020c-p119">Instead of your global administrator accounts being a permanent admin, they become eligible administrators. The global administrator role is inactive until someone needs it. You then complete an activation process to add the global administrator role to the global administrator account for a predetermined amount of time. When the time expires, PIM removes the global administrator role from the global administrator account.</span></span>
  
<span data-ttu-id="f020c-188">Uso de PIM y este proceso reduce considerablemente la cantidad de tiempo que las cuentas de administrador global son vulnerables a ataques y usar por usuarios malintencionados.</span><span class="sxs-lookup"><span data-stu-id="f020c-188">Using PIM and this process significantly reduces the amount of time that your global administrator accounts are vulnerable to attack and use by malicious users.</span></span>
  
<span data-ttu-id="f020c-189">Para obtener más información, vea [configurar AD de Azure con privilegios de administración de identidades](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).</span><span class="sxs-lookup"><span data-stu-id="f020c-189">For more information, see [Configure Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).</span></span>
  
> [!NOTE]
> <span data-ttu-id="f020c-190">PIM está disponible con Azure Active Directory Premium P2, que se incluye con movilidad de la empresa + E5 de seguridad (EMS), o puede adquirir licencias individuales para las cuentas de administrador global.</span><span class="sxs-lookup"><span data-stu-id="f020c-190">PIM is available with Azure Active Directory Premium P2, which is included with Enterprise Mobility + Security (EMS) E5, or you can purchase individual licenses for your global administrator accounts.</span></span> 
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a><span data-ttu-id="f020c-191">Seguridad información y eventos (SIEM) software de administración para el registro de Office 365</span><span class="sxs-lookup"><span data-stu-id="f020c-191">Security information and event management (SIEM) software for Office 365 logging</span></span>

<span data-ttu-id="f020c-p120">Ejecutar en un servidor de software SIEM realiza análisis en tiempo real de las alertas de seguridad y eventos creados por las aplicaciones y el hardware de red. Para permitir que el servidor SIEM incluir las alertas de seguridad de Office 365 y eventos en su análisis y funciones de notificación, integrar en el sistema SIEM:</span><span class="sxs-lookup"><span data-stu-id="f020c-p120">SIEM software run on a server performs real-time analysis of security alerts and events created by applications and network hardware. To allow your SIEM server to include Office 365 security alerts and events in its analysis and reporting functions, integrate these in your SIEM system:</span></span>
  
- <span data-ttu-id="f020c-194">Azure AD</span><span class="sxs-lookup"><span data-stu-id="f020c-194">Azure AD</span></span>
    
    <span data-ttu-id="f020c-195">Para obtener más información, vea [los registros de integrar de Azure recursos en los sistemas SIEM](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).</span><span class="sxs-lookup"><span data-stu-id="f020c-195">For more information, see [Integrate logs from Azure resources into your SIEM systems](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).</span></span>
    
- <span data-ttu-id="f020c-196">Office 365 Cloud App Security</span><span class="sxs-lookup"><span data-stu-id="f020c-196">Office 365 Cloud App Security</span></span>
    
    <span data-ttu-id="f020c-197">Para obtener más información, vea [integrar su servidor SIEM con seguridad de la aplicación de nube de Office 365](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532).</span><span class="sxs-lookup"><span data-stu-id="f020c-197">For more information, see [Integrate your SIEM server with Office 365 Cloud App Security](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532).</span></span>
    
## <a name="next-step"></a><span data-ttu-id="f020c-198">Paso siguiente</span><span class="sxs-lookup"><span data-stu-id="f020c-198">Next step</span></span>

<span data-ttu-id="f020c-199">Vea [procedimientos recomendados de seguridad para Office 365](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3).</span><span class="sxs-lookup"><span data-stu-id="f020c-199">See [Security best practices for Office 365](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3).</span></span>
  

