---
title: Proteger las cuentas de administrador global de Office 365
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
description: Proteja el acceso de administrador global a su suscripción a Office 365 con estos tres pasos.
ms.openlocfilehash: 23d47ec1f5fc4126113dd69e1ac6400d003ca41f
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "30573924"
---
# <a name="protect-your-office-365-global-administrator-accounts"></a>Proteger las cuentas de administrador global de Office 365

 **Resumen:** Proteja su suscripción de Office 365 de ataques en función de la intromisión de una cuenta de administrador global. 
  
Las infracciones de seguridad de una suscripción de Office 365, incluidos los ataques de suplantación de identidad (phishing) y recopilación de información, suelen realizarse poniendo en peligro las credenciales de una cuenta de administrador global de Office 365. La seguridad en la nube es una asociación entre usted y Microsoft:
  
- Los servicios en la nube de Microsoft se basan en una base de confianza y seguridad. Microsoft le proporciona controles y funciones de seguridad para ayudarle a proteger los datos y las aplicaciones.
    
- Debe poseer sus datos e identidades y la responsabilidad de protegerlos, la seguridad de los recursos locales y la seguridad de los componentes de la nube que usted controle.
    
Microsoft ofrece capacidades para ayudar a proteger su organización, pero solo se aplican si las usa. Si no las usa, puede ser vulnerable a un ataque. Para proteger sus cuentas de administrador global, Microsoft está aquí para ayudarle con instrucciones detalladas para:
  
1. Cree cuentas dedicadas de administrador global de Office 365 y úselas solo cuando sea necesario.
    
2. Configure multi-factor Authentication para las cuentas de administrador global de Office 365 y use la forma más segura de autenticación secundaria.
    
3. Habilitar y configurar Office 365 Cloud App Security para supervisar la actividad de una cuenta de administrador global sospechosa.
    
> [!NOTE]
> Aunque este artículo se centra en las cuentas de administrador global, también debe tener en cuenta si hay cuentas adicionales con amplios permisos de acceso a los datos de la suscripción, como administrador de eDiscovery o seguridad o cumplimiento. las cuentas de administrador deben protegerse del mismo modo. 
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a>Paso 1. Crear cuentas de administrador global de Office 365 dedicadas y usarlas solo cuando sea necesario

Hay relativamente pocas tareas administrativas, como asignar roles a cuentas de usuario, que requieran privilegios de administrador global. Por lo tanto, en lugar de usar las cuentas de usuario diarias que tienen asignado el rol de administrador global, siga estos pasos:
  
1. DeTermine el conjunto de cuentas de usuario a las que se ha asignado el rol de administrador global. Puede hacerlo con este comando en el símbolo del sistema de módulo de Microsoft Azure Active Directory para Windows PowerShell:
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

2. Inicie sesión en su suscripción a Office 365 con una cuenta de usuario a la que se le haya asignado el rol de administrador global.
    
3. Cree al menos una y hasta un máximo de cinco cuentas de usuario de administrador global dedicadas. **Use contraseñas seguras con un mínimo de 12 caracteres de longitud.** Vea [crear una contraseña segura](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) para obtener más información. Almacene las contraseñas de las cuentas nuevas en una ubicación segura. 
    
4. Asigne el rol de administrador global a cada una de las nuevas cuentas de usuario de administrador global dedicadas.
    
5. Cierre la sesión de Office 365.
    
6. Inicie sesión con una de las nuevas cuentas de usuario de administrador global dedicadas.
    
7. Para cada cuenta de usuario existente a la que se le haya asignado el rol de administrador global del paso 1:
    
  - Quite el rol de administrador global.
    
  - Asigne roles de administrador a la cuenta que sean adecuados para la función y responsabilidad de la tarea del usuario. Para obtener más información acerca de varios roles de administrador en Office 365, consulte [acerca de los roles de administrador de office 365](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).
    
8. Cierre la sesión de Office 365.
    
El resultado debe ser:
  
- Las únicas cuentas de usuario de su suscripción que tienen el rol de administrador global son el nuevo conjunto de cuentas de administrador global dedicadas. Compruebe esto con el siguiente comando de PowerShell:
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

- El resto de las cuentas de usuario habituales que administran la suscripción tienen asignados roles de administrador que están asociados con las funciones del puesto.
    
A partir de este momento, podrá iniciar sesión con las cuentas de administrador global dedicada solo para tareas que requieran privilegios de administrador global. El resto de la administración de Office 365 debe realizarse asignando otros roles de administración a las cuentas de usuario.
  
> [!NOTE]
> Sí, esto requiere unos pasos adicionales para cerrar la sesión como su cuenta de usuario diaria e iniciar sesión con una cuenta de administrador global dedicada. Pero esto solo debe realizarse ocasionalmente para las operaciones de administrador global. Considere la posibilidad de recuperar su suscripción de Office 365 después de una infracción de la cuenta de administrador global requiere muchos pasos más. 
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-secondary-authentication"></a>Paso 2. Configurar la autenticación multifactor para las cuentas de administrador global de Office 365 dedicadas y usar la forma más segura de autenticación secundaria

La autenticación multifactor (MFA) para las cuentas de administrador global requiere información adicional aparte del nombre y la contraseña de la cuenta. Office 365 admite estos métodos de comprobación:
  
- Una llamada de teléfono
    
- Un código de acceso generado de forma aleatoria
    
- Una tarjeta inteligente (física o virtual)
    
- Un dispositivo biométrico
    
Si es una pequeña empresa que usa cuentas de usuario almacenadas solo en la nube (el modelo de identidad de nube), use estos pasos para configurar la MFA con una llamada de teléfono o un código de verificación de mensaje de texto enviado a un teléfono inteligente:
  
1. [Habilitar MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).
    
2. [Configure la verificación en dos pasos para Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) para configurar cada cuenta de administrador global dedicada para la llamada telefónica o mensaje de texto como el método de verificación. 
    
Si es una organización de mayor tamaño que usa un modelo de identidad híbrida de Office 365, tiene más opciones de comprobación. Si ya ha implementado la infraestructura de seguridad para obtener un método de autenticación secundaria más seguro, siga estos pasos:
  
1. [Habilitar MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).
    
2. [Configure la verificación en dos pasos para Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) para configurar cada cuenta de administrador global dedicada para el método de verificación adecuado. 
    
Si la infraestructura de seguridad para el método de comprobación más seguro deseado no está en vigor y no funciona para Office 365 MFA, se recomienda encarecidamente que configure cuentas de administrador global dedicadas con MFA mediante una llamada de teléfono o un mensaje de texto. código de verificación enviado a un teléfono inteligente para sus cuentas de administrador global como medida de seguridad provisional. No deje las cuentas de administrador global dedicadas sin la protección adicional que proporciona MFA.
  
Para obtener más información, vea [Planear la autenticación multifactor para implementaciones de Office 365](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba).
  
Para conectarse a los servicios de Office 365 con MFA y PowerShell, consulte [este artículo](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/).
  
## <a name="step-3-monitor-for-suspicious-global-administrator-account-activity"></a>Paso 3. Supervisar la actividad de una cuenta de administrador global sospechosa

Office 365 Cloud App Security le permite crear directivas para notificar un comportamiento sospechoso en su suscripción. Cloud App Security está integrada en Office 365 E5, pero también está disponible como un servicio independiente. Por ejemplo, si no tiene Office 365 E5, puede comprar licencias de seguridad de aplicaciones de nube individuales para las cuentas de usuario que tienen asignados los roles de administrador global, administrador de seguridad y administrador de cumplimiento.
  
Si tiene Cloud App Security en su suscripción a Office 365, siga estos pasos:
  
1. Inicie sesión en el centro de administración de Microsoft 365 con una cuenta que tenga asignado el rol de administrador de seguridad o administrador de cumplimiento.
    
2. [Active Office 365 Cloud App Security](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c).
    
3. Revise sus [directivas de detección de anomalías en Office 365 Cloud App Security](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6) para notificarle por correo electrónico los patrones anómalos de actividad administrativa privilegiada. 
    
Para agregar una cuenta de usuario a la función de administrador de seguridad, [Conéctese a Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx#step3) con una cuenta de administrador global y una MFA dedicadas, rellene el nombre principal de usuario de la cuenta de usuario y, a continuación, ejecute estos comandos: 
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upn -RoleName "Security Administrator"
```

Para agregar una cuenta de usuario al rol de administrador de cumplimiento, escriba el nombre principal de usuario de la cuenta de usuario y ejecute estos comandos:
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress  $upn -RoleName "Compliance Administrator"
```

## <a name="additional-protections-for-enterprise-organizations"></a>Protecciones adicionales para organizaciones empresariales

Después de los pasos 1-3, use estos métodos adicionales para asegurarse de que su cuenta de administrador global y la configuración que realiza con ella son lo más seguras posible.
  
### <a name="privileged-access-workstation-paw"></a>Estación de trabajo de acceso con privilegios (pata)

Para asegurarse de que la ejecución de las tareas con privilegios elevados es lo más segura posible, use un pata. Una pata es un equipo dedicado que solo se usa para tareas de configuración confidenciales, como la configuración de Office 365 que requiere una cuenta de administrador global. Como este equipo no se usa diariamente para la exploración de Internet o el correo electrónico, es mejor estar protegido frente a ataques y amenazas de Internet.
  
Para obtener instrucciones sobre cómo configurar un pata, mira [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw).
  
### <a name="azure-ad-privileged-identity-management-pim"></a>Azure AD privileged Identity Management (PIM)

En lugar de tener sus cuentas de administrador global asignadas permanentemente al rol de administrador global, puede usar Azure AD PIM para habilitar la asignación Just-in-Time del rol de administrador global cuando sea necesario.
  
En lugar de las cuentas de administrador global que son administradores permanentes, se convierten en administradores elegibles. El rol de administrador global está inactivo hasta que alguien lo necesita. A continuación, debe completar un proceso de activación para agregar el rol de administrador global a la cuenta de administrador global para un período de tiempo predeterminado. Cuando expira el tiempo, PIM quita el rol de administrador global de la cuenta de administrador global.
  
El uso de PIM y este proceso reduce considerablemente la cantidad de tiempo que las cuentas de administrador global son vulnerables a ataques y uso de usuarios malintencionados.
  
Para obtener más información, consulte [Configure Azure ad privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).
  
> [!NOTE]
> PIM está disponible con Azure Active Directory Premium P2, que se incluye con Enterprise Mobility + Security (EMS) E5, o puede comprar licencias individuales para sus cuentas de administrador global. 
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a>Software de administración de eventos e información de seguridad (SIEM) para el registro de Office 365

El software de SIEM se ejecuta en un servidor realiza un análisis en tiempo real de los eventos y las alertas de seguridad creados por las aplicaciones y el hardware de red. Para permitir que el servidor de SIEM incluya eventos y alertas de seguridad de Office 365 en sus funciones de análisis e informes, integre estos en su sistema SIEM:
  
- Azure AD
    
    Para obtener más información, consulte [integrar registros de recursos de Azure en sus sistemas Siem](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).
    
- Office 365 Cloud App Security
    
    Para obtener más información, consulte [integrar el servidor de Siem con Office 365 Cloud App Security](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532).
    
## <a name="next-step"></a>Paso siguiente

Vea [procedimientos recomendados de seguridad para Office 365](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3).
  

