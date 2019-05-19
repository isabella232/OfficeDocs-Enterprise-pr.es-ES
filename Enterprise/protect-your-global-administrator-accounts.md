---
title: Proteger las cuentas de administrador global de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 5/16/2019
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
description: Proteger el acceso de administrador global a su suscripción a Office 365.
ms.openlocfilehash: 353787ccda7ab96583fe75bc423f70d339d3435b
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2019
ms.locfileid: "34162403"
---
# <a name="protect-your-office-365-global-administrator-accounts"></a>Proteger las cuentas de administrador global de Office 365

 **Resumen:** Proteja su suscripción de Office 365 de ataques en función de la intromisión de una cuenta de administrador global. 
  
Las infracciones de seguridad de una suscripción de Office 365, incluidos los ataques de suplantación de identidad (phishing) y recopilación de información, suelen realizarse poniendo en peligro las credenciales de una cuenta de administrador global de Office 365. La seguridad en la nube es una asociación entre usted y Microsoft:
  
- Los servicios en la nube de Microsoft se basan en una base de confianza y seguridad. Microsoft le proporciona controles y funciones de seguridad para ayudarle a proteger los datos y las aplicaciones.
    
- Debe poseer sus datos e identidades y la responsabilidad de protegerlos, la seguridad de los recursos locales y la seguridad de los componentes de la nube que usted controle.
    
Microsoft ofrece capacidades para ayudar a proteger su organización, pero solo se aplican si las usa. Si no las usa, puede ser vulnerable a un ataque. Para proteger sus cuentas de administrador global, Microsoft está aquí para ayudarle con instrucciones detalladas para:
  
1. Cree cuentas dedicadas de administrador global de Office 365 y úselas solo cuando sea necesario.
    
2. Configure multi-factor Authentication para las cuentas de administrador global de Office 365 y use la forma más segura de autenticación secundaria.
    
> [!NOTE]
> Aunque este artículo se centra en las cuentas de administrador global, debe tener en cuenta si hay cuentas adicionales con amplios permisos de acceso a los datos de la suscripción, como administrador de exhibición de documentos electrónicos o administrador de seguridad o cumplimiento. cuentas, deben protegerse de la misma manera. 
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a>Paso 1. Crear cuentas de administrador global de Office 365 dedicadas y usarlas solo cuando sea necesario

Hay relativamente pocas tareas administrativas, como asignar roles a cuentas de usuario, que requieran privilegios de administrador global. Por lo tanto, en lugar de usar las cuentas de usuario diarias que tienen asignado el rol de administrador global, siga estos pasos:
  
1. Determine el conjunto de cuentas de usuario a las que se ha asignado el rol de administrador global. Puede hacerlo con el comando Azure Active (Azure AD) de PowerShell de directorio para Graph:
  
  ```
  Get-AzureADDirectoryRole | where { $_.DisplayName -eq "Company Administrator" } | Get-AzureADDirectoryRoleMember | Ft DisplayName
  ```

2. Inicie sesión en su suscripción a Office 365 con una cuenta de usuario a la que se le haya asignado el rol de administrador global.
    
3. Cree al menos una y hasta un máximo de cinco cuentas de usuario de administrador global dedicadas. **Use contraseñas seguras con un mínimo de 12 caracteres de longitud.** Vea [crear una contraseña segura](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) para obtener más información. Almacene las contraseñas de las cuentas nuevas en una ubicación segura. 
    
4. Asigne el rol de administrador global a cada una de las nuevas cuentas de usuario de administrador global dedicadas.
    
5. Cierre la sesión de Office 365.
    
6. Inicie sesión con una de las nuevas cuentas de usuario de administrador global dedicadas.
    
7. Para cada cuenta de usuario existente a la que se le haya asignado el rol de administrador global del paso 1:
    
  - Quite el rol de administrador global.
    
  - Asigne roles de administrador a la cuenta que sean adecuados para la función y responsabilidad de la tarea del usuario. Para obtener más información acerca de varios roles de administrador en Office 365, consulte [acerca de los roles de administrador de office 365](https://docs.microsoft.com/office365/admin/add-users/about-admin-roles).
    
8. Cierre la sesión de Office 365.
    
El resultado debe ser:
  
- Las únicas cuentas de usuario de su suscripción que tienen el rol de administrador global son aquellas pertenecientes al nuevo conjunto de cuentas de administrador global dedicadas. Compruebe esto con el siguiente comando de PowerShell:
    
  ```
  Get-AzureADDirectoryRole | where { $_.DisplayName -eq "Company Administrator" } | Get-AzureADDirectoryRoleMember | Ft DisplayName
  ```

- El resto de las cuentas de usuario habituales que administran la suscripción tienen asignados roles de administrador que están asociados con las funciones del puesto.
    
A partir de este momento, podrá iniciar sesión con las cuentas de administrador global dedicada solo para tareas que requieran privilegios de administrador global. El resto de la administración de Office 365 debe realizarse asignando otros roles de administración a las cuentas de usuario.
  
> [!NOTE]
> Esto requiere pasos adicionales para cerrar la sesión como su cuenta de usuario diaria e iniciar sesión con una cuenta de administrador global dedicada. Pero esto solo debe realizarse ocasionalmente para las operaciones de administrador global. Considere la posibilidad de recuperar su suscripción de Office 365 después de una infracción de la cuenta de administrador global requiere muchos pasos más.
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-secondary-authentication"></a>Paso 2. Configurar la autenticación multifactor para las cuentas de administrador global de Office 365 dedicadas y usar la forma más segura de autenticación secundaria

La autenticación multifactor (MFA) requiere información adicional aparte del nombre y la contraseña de la cuenta. Office 365 admite estos métodos de comprobación:
  
- Una llamada de teléfono
    
- Un código de acceso generado de forma aleatoria
    
- Una tarjeta inteligente (física o virtual)
    
- Un dispositivo biométrico
    
Si es una pequeña empresa que usa cuentas de usuario almacenadas solo en la nube (el modelo de identidad solo de nube), siga estos pasos para configurar la MFA mediante una llamada de teléfono o un código de verificación de mensaje de texto enviado a un teléfono inteligente:
  
1. [Habilitar MFA](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication).
    
2. [Configure la verificación en dos pasos para Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) para configurar cada cuenta de administrador global dedicada para la llamada telefónica o mensaje de texto como el método de verificación. 
    
Si es una organización de mayor tamaño que usa un modelo de identidad híbrida de Office 365, tiene más opciones de comprobación. Si ya ha implementado la infraestructura de seguridad para obtener un método de autenticación secundaria más seguro, siga estos pasos:
  
1. [Habilitar MFA](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication).
    
2. [Configure la verificación en dos pasos para Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) para configurar cada cuenta de administrador global dedicada para el método de verificación adecuado. 
    
Si la infraestructura de seguridad para el método de comprobación más seguro deseado no está en vigor y no funciona para Office 365 MFA, se recomienda encarecidamente que configure cuentas de administrador global dedicadas con MFA mediante una llamada de teléfono o un mensaje de texto. código de verificación enviado a un teléfono inteligente para sus cuentas de administrador global como medida de seguridad provisional. No deje las cuentas de administrador global dedicadas sin la protección adicional que proporciona MFA.
  
Para obtener más información, vea [Planear la autenticación multifactor para implementaciones de Office 365](https://docs.microsoft.com/office365/admin/security-and-compliance/multi-factor-authentication-plan).
  
Para conectarse a los servicios de Office 365 con MFA y PowerShell, consulte [este artículo](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/).


## <a name="additional-protections-for-enterprise-organizations"></a>Protecciones adicionales para organizaciones empresariales

Después de los pasos 1 y 2, use estos métodos adicionales para asegurarse de que la cuenta de administrador global y la configuración que realiza con ella son lo más seguras posible.
  
### <a name="privileged-access-workstation"></a>Estación de trabajo de acceso privilegiado

Para asegurarse de que la ejecución de las tareas con privilegios elevados sea lo más segura posible, use una estación de trabajo de acceso privilegiado (pata). Una pata es un equipo dedicado que solo se usa para tareas de configuración confidenciales, como la configuración de Office 365 que requiere una cuenta de administrador global. Como este equipo no se usa diariamente para la exploración de Internet o el correo electrónico, es mejor estar protegido frente a ataques y amenazas de Internet.
  
Para obtener instrucciones sobre cómo configurar un pata, mira [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw).
  
### <a name="azure-ad-privileged-identity-management"></a>Azure AD Privileged Identity Management

En lugar de que las cuentas de administrador global estén permanentemente asignadas a la función de administrador global, puede usar Azure AD privileged Identity Management (PIM) para habilitar la asignación Just-in-Time del rol de administrador global cuando se fuer.
  
En lugar de las cuentas de administrador global que son administradores permanentes, se convierten en administradores elegibles. El rol de administrador global está inactivo hasta que alguien lo necesita. A continuación, debe completar un proceso de activación para agregar el rol de administrador global a la cuenta de administrador global para un período de tiempo predeterminado. Cuando expira el tiempo, PIM quita el rol de administrador global de la cuenta de administrador global.
  
El uso de PIM y este proceso reduce considerablemente la cantidad de tiempo que las cuentas de administrador global son vulnerables a ataques y uso de usuarios malintencionados.
  
Para obtener más información, consulte [Configure Azure ad privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).
  
> [!NOTE]
> PIM está disponible con Azure AD Premium P2, que se incluye con Enterprise Mobility + Security (EMS) E5, o puede comprar licencias individuales para sus cuentas de administrador global. 
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a>Software de administración de eventos e información de seguridad (SIEM) para el registro de Office 365

El software de SIEM se ejecuta en un servidor realiza un análisis en tiempo real de los eventos y las alertas de seguridad creados por las aplicaciones y el hardware de red. Para permitir que el servidor de SIEM incluya eventos y alertas de seguridad de Office 365 en sus funciones de análisis e informes, integre Azure AD en su SEIM. Consulte [integrar registros de recursos de Azure en sus sistemas Siem](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).

## <a name="next-step"></a>Paso siguiente

Si está configurando una identidad para su suscripción de Office 365, consulte:

- [Identidades solo en la nube](cloud-only-identities.md) si usa la identidad solo de nube
- [Preparar la sincronización de directorios](prepare-for-directory-synchronization.md) si está usando una identidad híbrida

  
## <a name="see-also"></a>Vea también

[Guía básica de seguridad de Office 365](https://docs.microsoft.com/office365/securitycompliance/security-roadmap).
