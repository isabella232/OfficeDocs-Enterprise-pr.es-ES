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
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 8f6f9894-5394-4110-8b0a-b8765028c10b
description: "Resumen: Comprender cómo Contoso asigna sus requisitos de seguridad a las características de las ofertas de nube de Microsoft y determina una ruta de acceso a la nube de preparación de la seguridad."
ms.openlocfilehash: f8df7f6437159aefe88851a22cc8da8b19c3838c
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="security-for-the-contoso-corporation"></a>Seguridad para Contoso Corporation

 **Resumen:** Comprender cómo Contoso asigna sus requisitos de seguridad a las características de las ofertas de nube de Microsoft y determina una ruta de acceso a la nube de preparación de la seguridad.
  
Contoso es en serio su seguridad de la información y la protección. Al realizar la transición de su infraestructura de TI en una nube inclusive, se aseguraron que sus requisitos de seguridad locales eran compatibles e implementados en las ofertas de nube de Microsoft.
  
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
    
## <a name="contosos-data-sensitivity-classification"></a>Clasificación de sensibilidad de los datos de Contoso

Con la información en el [Kit de herramientas de clasificación de datos](https://msdn.microsoft.com/library/hh204743.aspx)de Microsoft, Contoso realiza un análisis de sus datos y determina los siguientes niveles.
  
|**Nivel 1: Valor para el negocio de bajo**|**Nivel 2: Valor de la mediana empresa**|**Nivel 3: Valor para el negocio alto**|
|:-----|:-----|:-----|
|Datos están disponible sólo para los usuarios autenticados y cifrados  <br/> Se proporciona para todos los datos almacenados de forma local y en almacenamiento y cargas de trabajo basadas en la nube, como Office 365. Los datos se encriptan mientras residen en el servicio y en tránsito entre el servicio y los dispositivos de cliente.  <br/> Algunos ejemplos de datos de nivel 1 son las comunicaciones empresariales normales (correo electrónico) y los archivos de empleados administrativos, de ventas y de soporte técnico.  <br/> |Nivel 1 más sólida protección de pérdida de datos y autenticación  <br/> Autenticación segura incluye autenticación multifactor con validación de SMS. Prevención de pérdidas de datos garantiza que la información crítica o confidencial no viajar fuera de la red local.  <br/> Algunos ejemplos de datos de nivel 2 son la información jurídica y financiera, y los datos de investigación y desarrollo de nuevos productos.  <br/> |Nivel 2 además de los niveles más altos de cifrado, autenticación y auditoría  <br/> Los niveles más altos de cifrado de datos en reposo y en la nube, cumple las reglamentaciones regionales, combinan con autentificación multifactor mediante tarjetas inteligentes y granular auditoría y alertas.  <br/> Algunos ejemplos de datos de nivel 3 son la información de identificación personal de clientes y partners, las especificaciones de ingeniería de productos y las técnicas de fabricación patentadas.  <br/> |
   
## <a name="mapping-microsoft-cloud-offerings-and-features-to-contosos-data-levels"></a>Asignación de ofertas de nube de Microsoft y características a los niveles de datos de Contoso

En la tabla siguiente se muestra la asignación de niveles de datos de Contoso a funciones en las ofertas de nube de Microsoft:
  
||**SaaS**|**PaaS Azure**|**Azure IaaS**|
|:-----|:-----|:-----|:-----|
|Nivel 1: valor empresarial bajo  <br/> | HTTPS para todas las conexiones <br/>  Cifrado en reposo <br/> | Admitir sólo las conexiones HTTPS <br/>  Cifrar archivos almacenados en Azure <br/> | Requerir HTTPS o IPsec para el acceso al servidor <br/>  Azure Disk Encryption <br/> |
|Nivel 2: valor empresarial medio  <br/> | Autenticación multifactor de Azure AD (MFA) con SMS <br/> | Utilizar Azure clave de bóveda para claves de cifrado <br/>  MFA de Azure AD con SMS <br/> | MFA con SMS <br/> |
|Nivel 3: valor empresarial alto  <br/> | Sistema de administración de Azure de derechos (RMS) <br/>  MFA de Azure AD con tarjetas inteligentes <br/>  Acceso condicional de Intune <br/> | Azure RMS <br/>  MFA de Azure AD con tarjetas inteligentes <br/> | MFA con tarjetas inteligentes <br/> |
   
## <a name="contosos-information-policies"></a>Políticas de información de Contoso

La siguiente tabla enumera las directivas de información de Contoso.
  
||**Acceso**|**Retención de datos**|**Protección de la información**|
|:-----|:-----|:-----|:-----|
|Nivel 1: valor empresarial bajo  <br/> | Permitir el acceso a todo el mundo <br/> |6 meses  <br/> |Usa cifrado  <br/> |
|Nivel 2: valor empresarial medio  <br/> | Permitir el acceso a subcontratistas, socios y empleados de Contoso <br/>  Usar MFA, TLS y MAM <br/> |2 años  <br/> |Usar valores hash para la integridad de datos  <br/> |
|Nivel 3: valor empresarial alto  <br/> | Permitir el acceso a clientes potenciales en ingeniería y fabricación y ejecutivos <br/>  RMS con dispositivos de red administrados solamente <br/> |7 años  <br/> |Usar firmas digitales para evitar el rechazo  <br/> |
   
## <a name="contosos-path-to-cloud-security-readiness"></a>Ruta de acceso de Contoso para la preparación de la seguridad de nube

Contoso usó los pasos siguientes para preparar su seguridad para la nube de Microsoft:
  
1. Optimizar las cuentas de administrador para la nube
    
    Contoso realizó una revisión exhaustiva de las cuentas de administrador de Windows Server AD existentes y estableció una serie de grupos y cuentas de administrador de la nube.
    
2. Realizar análisis de clasificación de los datos en tres niveles
    
    Contoso realiza una revisión detenida y determina los tres niveles, que se utiliza para determinar la nube de Microsoft, que ofrece características para proteger los datos más valiosos de Contoso.
    
3. Determinar directivas de protección de información, retención y acceso para los niveles de datos
    
    Según los niveles de datos, Contoso determinó los requisitos detallados, que se usarán para calificar futuras cargas de trabajo de TI que se muevan a la nube.
    
## <a name="contosos-use-of-office-365-security-best-practices"></a>Uso de Contoso de recomendaciones de seguridad de Office 365

Con arreglo a prácticas recomendadas de seguridad de Office 365, los administradores de seguridad y el departamento de TI de Contoso han implementado las siguientes:
  
- **Dedicado a las cuentas de administrador global con contraseñas muy seguras**
    
    En lugar de asignar la función de administrador global para las cuentas de usuario diarias, Contoso ha crear tres, dedicado a las cuentas de administrador global con contraseñas muy seguras. Iniciar sesión con una cuenta de administrador global se realiza sólo para tareas administrativas específicas y sólo se conocen las contraseñas al personal designado. Los administradores de seguridad de Contoso han asignado funciones de administrador a cuentas que sean apropiadas para la función de trabajo de esa persona de TI y la responsabilidad.
    
    Para obtener más información, consulte [las funciones de administrador acerca de Office 365](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d).
    
- **Autenticación con varios factores (AMF) para cuentas de usuario importantes**
    
    AMF agrega una capa adicional de protección para el proceso de inicio de sesión pidiendo a los usuarios a reconocer una llamada telefónica, mensaje de texto o una notificación de la aplicación en su teléfono inteligente después de escribir correctamente su contraseña. Con AMF, cuentas de usuario de Office 365 están protegidas contra el inicio de sesión no autorizados en incluso si se pone en peligro la contraseña de una cuenta.
    
  - Para proteger contra un posible peligro de la suscripción de Office 365, Contoso habilita AMF en todas las tres cuentas de administrador global.
    
  - Para protegerse contra los ataques de phishing, en el que un atacante ponga en peligro las credenciales de una persona de confianza de la organización y envía mensajes de correo electrónico, Contoso habilitado AMF en todas las cuentas de usuario para administradores, incluido el personal ejecutivo.
    
    Para obtener más información, consulte el [Plan para la autenticación con varios factores para las implementaciones de Office 365](https://support.office.com/article/Plan-for-multifactor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)
    
- **Seguridad avanzada Management (ASM)**
    
    Usos ASM configurado directivas para supervisar la actividad anómala. Configurar alertas con ASM de modo que se notificación a los administradores de TI de actividad de usuario inusual o arriesgado, como descargar grandes cantidades de datos, los administradores de seguridad de Contoso no pudo varios intentos de inicio de sesión o inicios de sesión desde direcciones IP desconocidas o peligrosas
    
    Para obtener más información, vea [Información general de administración avanzada de seguridad de Office 365 ](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).
    
- **Flujo de seguridad de correo electrónico y el buzón de registro de auditoría**
    
    Expertos en seguridad de Contoso utiliza protección en línea de Exchange y protección avanzada de amenaza (ATP) para proteger contra malware desconocido, virus y direcciones URL malintencionadas transmitidas a través de mensajes de correo electrónico. Contoso también ha para determinar quién ha iniciado sesión en los buzones de usuario, mensajes enviados y otras actividades realizadas por el propietario del buzón, un usuario delegado o un administrador del registro de auditoría de buzón habilitado.
    
    Para más información, visite: 
    
  - [Protección antispam de correo electrónico de Office 365](https://support.office.com/article/Office-365-Email-AntiSpam-Protection-6a601501-a6a8-4559-b2e7-56b59c96a586)
    
  - [Protección avanzada para los datos adjuntos seguros y vínculos seguros](https://technet.microsoft.com/library/mt148491.aspx)
    
  - [Habilitar la auditoría de buzón en Office 365](https://go.microsoft.com/fwlink/p/?LinkID=626109)
    
- **Data Loss Prevention (DLP)**
    
    Contoso ha identificado sus datos confidenciales y configurado las directivas de DLP para Exchange Online, SharePoint Online y OneDrive ayudar a impedir que los usuarios los datos de uso compartido de forma accidental o intencionada. 
    
    Para obtener más información, vea [información general sobre las políticas de prevención de pérdida de datos](https://support.office.com/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e).
    
## <a name="see-also"></a>See Also

[Contoso en la nube de Microsoft](contoso-in-the-microsoft-cloud.md)
  
[Recursos de arquitectura de TI de la nube de Microsoft](microsoft-cloud-it-architecture-resources.md)

[Mapa de ruta de Enterprise Cloud de Microsoft: Recursos para los responsables de decisiones de TI](https://sway.com/FJ2xsyWtkJc2taRD)
  
[Recomendaciones de seguridad para Office 365](https://support.office.com/article/Security-best-practices-for-Office-365-9295e396-e53d-49b9-ae9b-0b5828cdedc3)




