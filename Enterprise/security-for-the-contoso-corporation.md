---
title: Seguridad para Contoso Corporation
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 8f6f9894-5394-4110-8b0a-b8765028c10b
description: 'Resumen: Conozca cómo Contoso asigna sus requisitos de seguridad a las características de las ofertas de nube de Microsoft y determina una ruta de acceso a la nube de preparación de la seguridad.'
ms.openlocfilehash: 722c01995c95c36b9975b0682858c38063f79d2c
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914835"
---
# <a name="security-for-the-contoso-corporation"></a>Seguridad para Contoso Corporation

 **Resumen:** Comprender cómo Contoso asigna sus requisitos de seguridad a las características de las ofertas de nube de Microsoft y determina una ruta de acceso a la nube de preparación de la seguridad.
  
Contoso es grave sobre su protección y seguridad de la información. Al trasladar su infraestructura de TI a una nube inclusive, realizan asegurarse de que sus requisitos de seguridad local se admitían e implementados en las ofertas de nube de Microsoft.
  
## <a name="contosos-security-requirements-in-the-cloud"></a>Requisitos de seguridad de Contoso en la nube

Estos son los requisitos de seguridad de Contoso para la nube:
  
- Autenticación sólida para los recursos de la nube
    
    Se debe autenticar el acceso a los recursos en la nube y, cuando sea posible, aprovechar la autenticación multifactor.
    
- Cifrado de tráfico a través de Internet
    
    No se envían datos en texto sin formato a través de Internet. Usar siempre conexiones HTTPS, IPsec u otros métodos de cifrado de datos descentralizados.
    
- Cifrado de datos en reposo en la nube
    
    Todos los datos almacenados en discos o en otros lugares en la nube deben estar en un formato cifrado.
    
- ACL para el acceso con privilegios mínimos
    
    Los permisos de cuenta para acceder a los recursos en la nube y lo que pueden hacer deben seguir las directrices de privilegios mínimos.
    
## <a name="contosos-data-sensitivity-classification"></a>Clasificación de confidencialidad de datos de Contoso

Con la información en el [Kit de herramientas de clasificación de datos](https://msdn.microsoft.com/library/hh204743.aspx)de Microsoft, Contoso realizó un análisis de sus datos y determina los siguientes niveles.
  
|**Nivel 1: valor empresarial bajo**|**Nivel 2: valor empresarial medio**|**Nivel 3: valor empresarial alto**|
|:-----|:-----|:-----|
|Los datos están cifrados y solo están disponibles para los usuarios autenticados

  <br/> Se proporciona para todos los datos almacenados de forma local y en almacenamiento y cargas de trabajo basadas en la nube, como Office 365. Los datos se encriptan mientras residen en el servicio y en tránsito entre el servicio y los dispositivos de cliente.  <br/> Algunos ejemplos de datos de nivel 1 son las comunicaciones empresariales normales (correo electrónico) y los archivos de empleados administrativos, de ventas y de soporte técnico.  <br/> |Características del nivel 1 más autenticación sólida y protección contra la pérdida de datos
  <br/> La autenticación segura incluye autenticación multifactor con validación de SMS. La prevención de pérdida de datos garantiza que la información crítica o confidencial no sale de la red local.
  <br/> Algunos ejemplos de datos de nivel 2 son la información jurídica y financiera, y los datos de investigación y desarrollo de nuevos productos.  <br/> |Características del nivel 2 además de los niveles más altos de cifrado, autenticación y auditoría
  <br/> Los niveles más altos de cifrado de datos en reposo y en la nube, conformes con la normativa regional, combinados con autentificación multifactor con tarjetas inteligentes y auditoría y alertas pormenorizadas.
  <br/> Algunos ejemplos de datos de nivel 3 son la información de identificación personal de clientes y partners, las especificaciones de ingeniería de productos y las técnicas de fabricación patentadas.  <br/> |
   
## <a name="mapping-microsoft-cloud-offerings-and-features-to-contosos-data-levels"></a>Asignación de las ofertas de nube de Microsoft y características en los niveles de datos de Contoso

En la tabla siguiente se muestra la asignación de niveles de datos de Contoso a funciones en las ofertas de nube de Microsoft:
  
||**SaaS**|**Plataforma como servicio de Azure**|**IaaS de Azure**|
|:-----|:-----|:-----|:-----|
|Nivel 1: valor empresarial bajo  <br/> | HTTPS para todas las conexiones
 <br/>  Cifrado en reposo <br/> | Admitir solo las conexiones HTTPS
 <br/>  Cifrar archivos almacenados en Azure <br/> | Requerir HTTPS o IPsec para el acceso al servidor
 <br/>  Azure Disk Encryption <br/> |
|Nivel 2: valor empresarial medio  <br/> | Autenticación multifactor de Azure AD (MFA) con SMS <br/> | Usar Azure Key Vault para las claves de cifrado
 <br/>  MFA de Azure AD con SMS <br/> | MFA con SMS <br/> |
|Nivel 3: valor empresarial alto  <br/> | Sistema Azure Rights Management (RMS)

 <br/>  MFA de Azure AD con tarjetas inteligentes <br/>  Acceso condicional de Intune <br/> | Azure RMS <br/>  MFA de Azure AD con tarjetas inteligentes <br/> | MFA con tarjetas inteligentes <br/> |
   
## <a name="contosos-information-policies"></a>Directivas de información de Contoso

La siguiente tabla enumera las directivas de información de Contoso.
  
||**Acceso**|**Retención de datos**|**Protección de la información**|
|:-----|:-----|:-----|:-----|
|Nivel 1: valor empresarial bajo  <br/> | Permitir el acceso a todo el mundo <br/> |6 meses  <br/> |Usa cifrado  <br/> |
|Nivel 2: valor empresarial medio  <br/> | Permitir el acceso a subcontratistas, partners y empleados de Contoso
 <br/>  Usar MFA, TLS y MAM <br/> |2 años  <br/> |Usar valores hash para la integridad de datos  <br/> |
|Nivel 3: valor empresarial alto  <br/> | Permitir el acceso a ejecutivos y clientes potenciales de ingeniería y fabricación
 <br/>  RMS con dispositivos de red administrados solamente <br/> |7 años  <br/> |Usar firmas digitales para evitar el rechazo  <br/> |
   
## <a name="contosos-path-to-cloud-security-readiness"></a>Ruta de acceso de Contoso para la preparación de la seguridad en la nube

Contoso usó los pasos siguientes para preparar su seguridad para la nube de Microsoft:
  
1. Optimizar las cuentas de administrador para la nube

    
    Contoso realizó una revisión exhaustiva de las cuentas de administrador de Windows Server AD existentes y estableció una serie de grupos y cuentas de administrador de la nube.
    
2. Realizar análisis de clasificación de datos en tres niveles

    
    Contoso lleva a cabo una cuidadosa revisión y determina los tres niveles, que se utilizan para determinar la nube de Microsoft que ofrece características para proteger los datos más valiosos de Contoso.
    
3. Determinar las directivas de acceso, retención y protección de la información para los niveles de datos

    
    Según los niveles de datos, Contoso determinó los requisitos detallados, que se usarán para calificar futuras cargas de trabajo de TI que se muevan a la nube.
    
## <a name="contosos-use-of-office-365-security-best-practices"></a>Uso de Contoso de procedimientos recomendados de seguridad de Office 365

Conformidad con Office 365 procedimientos recomendados de seguridad, los administradores de seguridad y el departamento de TI de Contoso han implementado lo siguiente:
  
- **Dedicada a las cuentas de administrador global con contraseñas muy seguras**
    
    En lugar de asignar el rol de administrador global para las cuentas de usuario cotidianas, Contoso ha crear tres, dedicada a las cuentas de administrador global con contraseñas muy seguras. Iniciar sesión con una cuenta de administrador global se realiza sólo para tareas administrativas específicas y sólo se conocen las contraseñas al personal designado. Los administradores de seguridad de Contoso han asignado roles de administrador a las cuentas que son adecuadas para la función de trabajo de esa persona de TI y la responsabilidad.
    
    Para obtener más información, vea [roles de administrador acerca de Office 365](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d).
    
- **Autenticación multifactor (MFA) para las cuentas de usuario importantes**
    
    MFA agrega una capa adicional de protección para el proceso de inicio de sesión al requerir que los usuarios a una llamada de teléfono, mensaje de texto o una notificación de la aplicación en su teléfono inteligente después de escribir correctamente su contraseña. Con MFA, las cuentas de usuario de Office 365 están protegidas contra el inicio de sesión no autorizado de incluso si se ve comprometida una contraseña de la cuenta.
    
  - Para proteger contra un compromiso de la suscripción de Office 365, Contoso habilitado MFA en todas las cuentas de administrador global de tres.
    
  - Para proteger contra los ataques de suplantación de identidad, en la que un atacante ponga en peligro las credenciales de una persona de confianza en la organización y envía mensajes de correo electrónico, Contoso habilitado MFA en todas las cuentas de usuario para los administradores, incluido el personal ejecutivo.
    
    Para obtener más información, vea [Planear la autenticación multifactor para las implementaciones de Office 365](https://support.office.com/article/Plan-for-multifactor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)
    
- **Administración de seguridad avanzada (ASM)**
    
    Usos ASM configurado directivas para supervisar la actividad anómala. Configurar alertas con ASM de modo que se notifican a los administradores de TI de actividad de usuario inusual o arriesgado, como una descarga grandes cantidades de datos, los administradores de seguridad de Contoso no pudo varios intentos de inicio de sesión o inicios de sesión desde direcciones IP desconocidas o peligrosas
    
    Para obtener más información, vea [Información general de administración avanzada de seguridad en Office 365 ](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).
    
- **Flujo de correo electrónico seguro y el buzón de registro de auditoría**
    
    Especialistas en seguridad de Contoso usa Exchange Online Protection y protección avanzada de amenaza (ATP) para proteger contra malware desconocido, virus y direcciones URL malintencionadas se transmite a través de mensajes de correo electrónico. Contoso también ha habilitado registro de auditoría para determinar quién ha iniciado sesión en los buzones de usuario, mensajes enviados y otras actividades realizadas por el propietario del buzón, un usuario delegado o un administrador.
    
    Para obtener más información, vea: 
    
  - [Protección contra correo no deseado de Office 365](https://support.office.com/article/Office-365-Email-AntiSpam-Protection-6a601501-a6a8-4559-b2e7-56b59c96a586)
    
  - [Protección contra amenazas avanzada para datos adjuntos seguros y vínculos seguros](https://technet.microsoft.com/library/mt148491.aspx)
    
  - [Habilitar la auditoría de buzones de correo en Office 365](https://go.microsoft.com/fwlink/p/?LinkID=626109)
    
- **Prevención de pérdida de datos (DLP)**
    
    Contoso ha identificado sus datos confidenciales y configurado las directivas de DLP para Exchange Online, SharePoint Online y OneDrive ayudar a impedir que los usuarios los datos de uso compartido de forma accidental o intencionada. 
    
    Para obtener más información, consulte [Información general sobre directivas de prevención de pérdida de datos](https://support.office.com/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e).
    
## <a name="see-also"></a>See Also

[Contoso en la nube de Microsoft](contoso-in-the-microsoft-cloud.md)
  
[Recursos de arquitectura de TI de la nube de Microsoft](microsoft-cloud-it-architecture-resources.md)

[Mapa de ruta de Enterprise Cloud de Microsoft: Recursos para los responsables de decisiones de TI](https://sway.com/FJ2xsyWtkJc2taRD)
  
[Procedimientos recomendados de seguridad para Office 365](https://support.office.com/article/Security-best-practices-for-Office-365-9295e396-e53d-49b9-ae9b-0b5828cdedc3)




