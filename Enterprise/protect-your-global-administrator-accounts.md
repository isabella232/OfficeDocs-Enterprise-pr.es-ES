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
ms.openlocfilehash: 41168643fb8867017865860624c8b436460fa0b8
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897523"
---
# <a name="protect-your-office-365-global-administrator-accounts"></a>Protección de las cuentas de administrador global de Office 365

 **Resumen:** Proteger su suscripción de Office 365 de los ataques basados en el compromiso de una cuenta de administrador global. 
  
Las infracciones de seguridad de una suscripción de Office 365, incluyendo la recopilación de información y los ataques de suplantación de identidad, normalmente se realiza por poner en peligro las credenciales de una cuenta de administrador global de Office 365. Seguridad en la nube es una asociación entre usted y Microsoft:
  
- Servicios de nube de Microsoft se basan en una base de seguridad y confianza. Microsoft proporciona controles de seguridad y las capacidades que le ayudarán a proteger los datos y aplicaciones.
    
- Propietario de los datos y las identidades y la responsabilidad de protección, la seguridad de los recursos locales y la seguridad de los componentes de la nube, controlar.
    
Microsoft proporciona capacidades para ayudar a proteger su organización, pero son efectivos sólo si los utiliza. Si no se utiliza, puede ser vulnerable a un ataque. Para proteger las cuentas de administrador global, Microsoft está aquí para ayudarle con instrucciones detalladas para:
  
1. Crear cuentas de administrador global de Office 365 dedicadas y utilizarlos sólo cuando sea necesario.
    
2. Configuración de la autenticación multifactor para las cuentas de administrador global de Office 365 dedicadas y usar la forma más segura de autenticación secundaria.
    
3. Habilitar y configurar la seguridad de aplicación de Office 365 en la nube para supervisar la actividad de la cuenta de administrador global sospechosos.
    
> [!NOTE]
> Aunque en este artículo se centra en las cuentas de administrador global, también debe considerar si adicionales cuentas con los permisos tan amplios para tener acceso a los datos en su suscripción, como administrador de la exhibición de documentos electrónicos o de cumplimiento de normas o de seguridad las cuentas de administrador, se deben proteger de la misma manera. 
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a>Paso 1. Crear cuentas de administrador global de Office 365 dedicadas y utilizarlos sólo cuando sea necesario

Hay relativamente pocas tareas administrativas, como la asignación de roles a las cuentas de usuario, que requieren privilegios de administrador global. Por lo tanto, en lugar de usar cuentas de usuario cotidianas que ha asignado el rol de administrador global, siga estos pasos:
  
1. Determinar el conjunto de cuentas de usuario que ha asignado el rol de administrador global. Puede hacerlo con este comando en el símbolo del sistema de Microsoft Azure Active Directory módulo para Windows PowerShell:
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

2. Inicie sesión en su suscripción de Office 365 con una cuenta de usuario que se ha asignado el rol de administrador global.
    
3. Cree al menos uno y hasta un máximo de cinco dedicado las cuentas de usuario de administrador global. **Caracteres de largo contraseñas seguras al menos 12 uso.** Para obtener más información, vea [crear una contraseña segura](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) . Almacenar las contraseñas de las cuentas de nuevo en una ubicación segura. 
    
4. Asignar el rol de administrador global a cada una de las cuentas de usuario de administrador global nuevo dedicado.
    
5. Cerrar la sesión de Office 365.
    
6. Inicie sesión con una de las nuevas cuentas de usuario de administrador global dedicado.
    
7. Para cada cuenta de usuario existente que está asignado el rol de administrador global desde el paso 1:
    
  - Quite el rol de administrador global.
    
  - Asignar roles de administrador a la cuenta de que son adecuados para la función de trabajo y la responsabilidad de dicho usuario. Para obtener más información acerca de diversos roles de administración de Office 365, vea [roles de administrador acerca de Office 365](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).
    
8. Cerrar la sesión de Office 365.
    
El resultado debería ser:
  
- Las cuentas de usuario sólo en la suscripción que tienen la función de administrador global son el nuevo conjunto de cuentas de administrador global dedicado. Para comprobar esto con el siguiente comando de PowerShell:
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

- El resto de las cuentas de usuario habituales que administran la suscripción tienen asignados roles de administrador que están asociados con las funciones del puesto.
    
Desde este momento en adelante, iniciar sesión con las cuentas de administrador global dedicado sólo para las tareas que requieren privilegios de administrador global. Otro tipo de administración de Office 365 debe realizarse mediante la asignación de otras funciones de administración a cuentas de usuario.
  
> [!NOTE]
> Sí, esto requiere pasos adicionales para cerrar la sesión como la cuenta de usuario cotidianas e iniciar sesión con una cuenta de administrador global dedicado. Pero esto sólo necesita realizarse cada cierto tiempo para operaciones de administrador global. Tenga en cuenta la recuperación después de una infracción de la cuenta de administrador global requiere mucho más pasos de su suscripción de Office 365. 
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-secondary-authentication"></a>Paso 2. Configuración de la autenticación multifactor para las cuentas de administrador global de Office 365 dedicadas y usar la forma más segura de autenticación secundaria

Autenticación multifactor (MFA) para las cuentas de administrador global requiere información adicional más allá del nombre de cuenta y la contraseña. Office 365 admite los siguientes métodos de comprobación:
  
- Una llamada de teléfono
    
- Un código de acceso generado de forma aleatoria
    
- Una tarjeta inteligente (física o virtual)
    
- Un dispositivo biométrico
    
Si es una pequeña empresa que está usando las cuentas de usuario que se almacenan solo en la nube (el modelo de identidad en la nube), siga estos pasos para configurar MFA mediante una llamada telefónica o un código de comprobación de mensaje de texto enviado a un teléfono inteligente:
  
1. [Habilitar MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).
    
2. [Conjunto de copia de seguridad - paso 2 de comprobación para Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) para configurar cada uno dedicado cuenta de administrador global para la llamada de teléfono o mensaje de texto como el método de comprobación. 
    
Si es una organización más grande que usa un modelo de identidad de Office 365 híbrida, tiene más opciones de comprobación. Si ya tiene la infraestructura de seguridad en lugar de un método de autenticación secundario más seguro, siga estos pasos:
  
1. [Habilitar MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).
    
2. [Conjunto de copia de seguridad - paso 2 de comprobación para Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) para configurar cada uno dedicado cuenta de administrador global para el método de comprobación adecuada. 
    
Si la infraestructura de seguridad para el método de comprobación más sólida deseada no está en contexto y el funcionamiento de Office 365 MFA, recomendamos encarecidamente que configure las cuentas de administrador global dedicado con MFA mediante una llamada telefónica o un mensaje de texto código de verificación enviado a un teléfono inteligente para las cuentas de administrador global como una medida de seguridad provisional. No deje las cuentas de administrador global dedicado sin la protección adicional proporcionada por MFA.
  
Para obtener más información, vea [Planear la autenticación multifactor para implementaciones de Office 365](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba).
  
Para conectarse a servicios de Office 365 con MFA y PowerShell, vea [este artículo](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/).
  
## <a name="step-3-monitor-for-suspicious-global-administrator-account-activity"></a>Paso 3. Monitor de actividad de la cuenta de administrador global sospechosos

Seguridad de la aplicación en la nube Office 365 le permite crear directivas para notificar de comportamiento sospechoso en su suscripción. Seguridad de la aplicación en la nube está integrada en Office 365 E5, pero también está disponible como un servicio independiente. Por ejemplo, si no tiene Office 365 E5, puede comprar licencias individuales de seguridad de la aplicación en la nube para las cuentas de usuario que se asignan el administrador global, Administrador de seguridad y roles de administrador de cumplimiento de normas.
  
Si tiene la seguridad de la aplicación en la nube en su suscripción de Office 365, siga estos pasos:
  
1. Inicie sesión en el portal de Office 365 con una cuenta que está asignado el rol de administrador de seguridad o administrador de cumplimiento de normas.
    
2. [Activar la seguridad de la aplicación de Office 365 en la nube](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c).
    
3. Revise las [directivas de detección de anomalías en la seguridad de la aplicación de Office 365 en la nube](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6) para recibir una notificación por correo electrónico de patrones anómalos de actividades administrativas con privilegios. 
    
Para agregar una cuenta de usuario a la función de administrador de seguridad, [conectarse a Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx#step3) con una cuenta de administrador global dedicado y MFA, rellene el nombre principal de usuario de la cuenta de usuario y, a continuación, ejecute estos comandos: 
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upn -RoleName "Security Administrator"
```

Para agregar una cuenta de usuario a la función de administrador de cumplimiento de normas, rellene el nombre principal de usuario de la cuenta de usuario y, a continuación, ejecute estos comandos:
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress  $upn -RoleName "Compliance Administrator"
```

## <a name="additional-protections-for-enterprise-organizations"></a>Protecciones adicionales para las organizaciones empresariales

Después de los pasos 1-3, utilizan estos métodos adicionales para asegurarse de que la cuenta de administrador global y la configuración que se realiza con él, son tan seguros como sea posible.
  
### <a name="privileged-access-workstation-paw"></a>Estación de trabajo de Access con privilegios (PATA)

Para asegurarse de que la ejecución de tareas con muchos privilegios es tan segura como sea posible, use un PATA. Un PATA es un equipo dedicado que se utiliza únicamente para las tareas de configuración confidencial, como la configuración de Office 365 que requiere una cuenta de administrador global. Debido a que este equipo no se usa diariamente para correo electrónico o la exploración de Internet, está mejor protegido frente a las amenazas y ataques de Internet.
  
Para obtener instrucciones sobre cómo configurar un pata, consulte [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw).
  
### <a name="azure-ad-privileged-identity-management-pim"></a>Administración de identidades de Azure con privilegios de AD (PIM)

En lugar de tener las cuentas de administrador global asignado de forma permanente la función de administrador global, puede usar Azure AD PIM para habilitar la asignación de petición, just-in-time de la función de administrador global cuando sea necesario.
  
En lugar de las cuentas de administrador global que se va a un administrador permanente, se convierten en administradores aptos. La función de administrador global está inactiva hasta que alguien la necesita. A continuación, complete un proceso de activación para agregar la función de administrador global para la cuenta de administrador global para un período de tiempo predeterminado. Cuando se agota el tiempo, PIM quita la función de administrador global de la cuenta de administrador global.
  
Uso de PIM y este proceso reduce considerablemente la cantidad de tiempo que las cuentas de administrador global son vulnerables a ataques y usar por usuarios malintencionados.
  
Para obtener más información, vea [configurar AD de Azure con privilegios de administración de identidades](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).
  
> [!NOTE]
> PIM está disponible con Azure Active Directory Premium P2, que se incluye con movilidad de la empresa + E5 de seguridad (EMS), o puede adquirir licencias individuales para las cuentas de administrador global. 
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a>Seguridad información y eventos (SIEM) software de administración para el registro de Office 365

Ejecutar en un servidor de software SIEM realiza análisis en tiempo real de las alertas de seguridad y eventos creados por las aplicaciones y el hardware de red. Para permitir que el servidor SIEM incluir las alertas de seguridad de Office 365 y eventos en su análisis y funciones de notificación, integrar en el sistema SIEM:
  
- Azure AD
    
    Para obtener más información, vea [los registros de integrar de Azure recursos en los sistemas SIEM](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).
    
- Office 365 Cloud App Security
    
    Para obtener más información, vea [integrar su servidor SIEM con seguridad de la aplicación de nube de Office 365](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532).
    
## <a name="next-step"></a>Siguiente paso

Vea [procedimientos recomendados de seguridad para Office 365](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3).
  

