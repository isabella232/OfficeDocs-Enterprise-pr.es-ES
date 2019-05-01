---
title: Diagrama accesible Opciones de plataformas de Microsoft Exchange 2013
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 129f4e45-647e-4cf1-92a6-4d86d8396e73
description: Este artículo es una versión de texto accesible del diagrama con el nombre Opciones de plataforma de Microsoft Exchange 2013, que está disponible en Diagramas técnicos.
ms.openlocfilehash: e1c4957c9152c5a23008c657d7e2d0d47b5cce0f
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487807"
---
# <a name="accessible-diagram---microsoft-exchange-2013-platform-options"></a>Diagrama accesible: Opciones de plataformas de Microsoft Exchange 2013

**Resumen:** este artículo es una versión de texto accesible del diagrama “Opciones de plataformas de Microsoft Exchange 2013”, que está disponible en [Diagramas técnicos](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).
  
Este póster describe lo que los arquitectos y responsables de decisiones empresariales (BDM) necesitan saber sobre implementaciones de Exchange Online e Exchange Server. Incluye lo siguiente: 
  
- Una comparación de cuatro opciones de plataforma disponibles para Exchange 2013: Exchange Online (Office 365), Exchange Hybrid, Exchange Server local e Exchange hospedado por el proveedor. 
    
- Descripciones de tres características nuevas o actualizadas en Exchange 2013. 
    
## <a name="comparison-of-four-different-deployments-for-the-exchange-2013-platform"></a>Comparación de cuatro implementaciones diferentes para la plataforma de Exchange 2013

La comparación proporciona información sobre cada opción de implementación en las siguientes áreas: 
  
- Información general sobre las diferentes características de implementación 
    
- Ventajas de la implementación de cada opción de implementación 
    
- Requisitos de licencia 
    
- Tareas de arquitectura requeridas 
    
- Responsabilidades del profesional de TI para implementar cada opción de implementación 
    
### <a name="overview"></a>Información general

#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

Se gana eficiencia y reducen costes con Office 365.
  
El diagrama correspondiente muestra Exchange Online con un inquilino de Azure Active Directory que sincroniza nombres y contraseñas de cuentas entre el entorno de Servicios de dominio de Active Directory (AD DS) y el inquilino de Azure Active Directory. Los Servicios de federación de Active Directory (AD FS) son necesarios para el inicio de sesión único. 
  
Descripción de las características y funcionalidades:
  
- Microsoft controla el funcionamiento de los servidores y el software de servidor.
    
- Conjunto enriquecido de Exchange Server 2013 como servicio basado en nube.
    
- Siempre actualizado con las características más recientes.
    
- Exchange Online Protection (EOP) se incluye para la protección de correo no deseado y contra malware.
    
- Alta disponibilidad integrada con un contrato de nivel de servicio (SLA) del 99,9 %.
    
- Sincronización de directorios que incluye contraseñas entre los Servicios de dominio de Active Directory (AD DS) locales y el inquilino de Azure Active Directory. Los Servicios de federación de Active Directory (AD FS) son necesarios para el inicio de sesión único.
    
#### <a name="exchange-hybrid"></a>Exchange Hybrid

Puede aprovechar las ventajas de Office 365 mientras mantiene Exchange Server local.
  
El diagrama correspondiente muestra Office 365 con Exchange Online donde algunos usuarios están alojados de forma local y algunos usuarios están alojados en línea. También muestra un inquilino de Azure Active Directory que sincroniza nombres y contraseñas de cuentas entre el entorno de Servicios de dominio de Active Directory (AD DS) y el inquilino de Azure. Active Directory.
  
Descripción de las características y funcionalidades:
  
- Algunos usuarios están alojados de forma local y algunos usuarios están alojados en línea. Los usuarios comparten el mismo espacio de direcciones de correo electrónico.
    
- Aprovecha la infraestructura existente de Exchange Server.
    
- Migre desde Exchange local a Exchange Online con el transcurso del tiempo, según su programación.
    
- Integre con otras aplicaciones Office 365, incluidas Lync Online y SharePoint Online.
    
#### <a name="exchange-server-on-premises"></a>Exchange Server local

Puede diseñar y administrar su propia infraestructura de Exchange Server 2013.
  
El diagrama correspondiente muestra una infraestructura de Exchange Server con un entorno de Active Directory Domain Services (AD DS) local donde los usuarios están alojados de forma local.
  
Descripción de las características y funcionalidades:
  
- El mayor grado de control y personalización para su configuración.
    
- Sin dependencia en mantener la afinidad de sesión en la capa de equilibrio de carga.
    
- Alta disponibilidad y resistencia de sitios sencillas con grupos de disponibilidad de base de datos (DAG).
    
- Disponibilidad administrada que ayuda a mantener una excelente experiencia del usuario.
    
- Aproveche la infraestructura existente de hardware y almacenamiento.
    
#### <a name="provider-hosted-exchange"></a>Exchange hospedado por el proveedor

Puede subcontratar su carga de trabajo de Exchange Server a un proveedor de soluciones de Exchange Server.
  
El diagrama correspondiente muestra un entorno de Exchange Server que un proveedor se encarga de hacer funcionar y mantener.
  
Descripción de las características y funcionalidades:
  
- El proveedor controla el funcionamiento de los servidores y el software de servidor.
    
- Se delegan al proveedor la planeación, la modificación de tamaño, el escalado y el mantenimiento de la infraestructura de Exchange Server.
    
- El proveedor controla el mantenimiento de servicio.
    
- El conjunto de características de Exchange está limitado a la versión de software que el proveedor implementa.
    
### <a name="benefits-of-implementing-each-deployment-option"></a>Ventajas de la implementación de cada opción de implementación

#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

Esta opción de implementación es la mejor para:
  
- Organizaciones que buscan reducir costes de operaciones para implementaciones de Exchange local.
    
- Organizaciones que planean aprovechar otras ofertas de Office 365, como SharePoint Online y Lync Online.
    
#### <a name="exchange-hybrid"></a>Exchange Hybrid

Esta opción de implementación es la mejor para:
  
- Facilitar una migración de Exchange local a Exchange Online.
    
- Soporte de sitios remotos sin invertir en infraestructura de oficinas de sucursales.
    
- Multinacionales con filiales que requieren datos que residan de forma local.
    
#### <a name="exchange-server-on-premises"></a>Exchange Server local

Esta opción de implementación es la mejor para:
  
- Soluciones muy personalizadas.
    
- Soluciones heredadas con componentes de terceros que dependen de hardware y software que no son compatibles con Exchange Online.
    
- Organizaciones sujetas a regulaciones de datos gubernamentales que exigen que los datos residan de forma local.
    
- Organizaciones que desean conservar el control de toda la plataforma y solución.
    
#### <a name="provider-hosted-exchange"></a>Exchange hospedado por el proveedor

Esta opción de implementación es la mejor para:
  
- Organizaciones que necesitan funcionalidad de Exchange Server, pero desean subcontratar la implementación y el mantenimiento.
    
- Organizaciones que necesitan opciones de soporte personalizado.
    
- Soluciones e integración personalizadas con aplicaciones personalizadas que el proveedor ofrece.
    
- Soluciones heredadas con componentes de terceros que dependen de hardware y software que no son compatibles con Exchange Online.
    
### <a name="license-requirements"></a>Requisitos de licencia

La siguiente tabla detalla los requisitos de licencia para cada opción de implementación.
  
|**Opción de implementación**|**Requisitos de licencia**|
|:-----|:-----|
|Exchange Online (Office 365)  <br/> |Modelo de suscripción  <br/> |
|Exchange Hybrid  <br/> | Office 365: Modelo de suscripción <br/>  Local: Se aplican todas las licencias locales (revise las licencias para Exchange Server local) <br/>  Licencia de servidor híbrido* <br/> |
|Exchange Server local  <br/> | Sistema operativo del servidor <br/>  Licencia de Exchange 2013 Server <br/>  Licencia de acceso de cliente de Exchange 2013 <br/> |
|Exchange hospedado por el proveedor  <br/> |Los costes se basan en el acuerdo con el proveedor  <br/> |
   
### <a name="architecture-tasks"></a>Tareas de arquitectura

Esta sección muestra las tareas de arquitectura para cada opción de implementación.
  
#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

- Planee y diseñe la sincronización de directorios.
    
- Garantice la capacidad de red y conectividad mediante firewalls, servidores proxy, puertas de enlace y vínculos por WAN.
    
#### <a name="exchange-hybrid"></a>Exchange Hybrid

Además de las tareas de arquitectura para los entornos de Office 365 y locales:
  
- Decida si va a proporcionar una experiencia de inicio de sesión único.
    
- Decida si va a enrutar el correo entrante de Internet a través de una organización local o a través de Exchange Online Protection.
    
#### <a name="exchange-server-on-premises"></a>Exchange Server local

- Diseñe la topología de Exchange.
    
- Planee la capacidad para hardware de servidor.
    
- Diseñe la topología de enrutamiento de mensajes.
    
- Diseñe equilibrio de carga para servidores de acceso de cliente.
    
- Planee una alta disponibilidad con grupos de disponibilidad de bases de datos.
    
#### <a name="provider-hosted-exchange"></a>Exchange hospedado por el proveedor

Asegúrese de que la capacidad de red y disponibilidad mediante firewalls, servidores proxy, puertas de enlace y vínculos por WAN estén disponibles para su proveedor.
  
### <a name="it-pro-responsibilities"></a>Responsabilidades del profesional de TI

Esta sección muestra las responsabilidades del profesional de TI para cada opción de implementación.
  
#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

- Implemente el plan de sincronización de directorios.
    
- Planee e implemente enrutamiento y registros DNS internos y externos.
    
- Configure el servidor proxy o firewall para los requisitos de direcciones URL e IP de Office 365.
    
- Administre las cuentas de usuario y la configuración de Exchange Online.
    
#### <a name="exchange-hybrid"></a>Exchange Hybrid

Además de las responsabilidades del profesional de TI para los entornos de Office 365 y locales:
  
- Configure los Servicios de federación de Active Directory (AD FS) para inicio de sesión único (si lo desea).
    
- Configure certificados de Exchange para proteger las comunicaciones entre servidores de Exchange 2013 y Office 365.
    
- Configure registros DNS para la ruta de correo de Internet entrante que desee.
    
#### <a name="exchange-server-on-premises"></a>Exchange Server local

- Configure los certificados necesarios para los servicios de Exchange.
    
- Aprovisione los servidores.
    
- Implemente la topología de enrutamiento de mensajes de Exchange.
    
- Implemente grupos de disponibilidad de bases de datos.
    
- Actualice y mantenga servidores de Exchange.
    
- En función de la utilización, agregue o quite servidores según sea necesario.
    
#### <a name="provider-hosted-exchange"></a>Exchange hospedado por el proveedor

Las responsabilidades del proveedor incluyen:
  
- Mantenimiento del sistema y el servicio.
    
- Lanzamientos de características.
    
- Recuperación ante desastres y protección de datos.
    
Las responsabilidades del personal de TI de la organización incluyen crear y administrar cuentas de usuarios.
  
#### <a name="more-information"></a>Más información

Para obtener más información sobre Exchange Online (Office 365), consulte:
  
- [Descripción de servicio de Exchange Online](https://aka.ms/EXOSD)
    
- [Biblioteca de Exchange Online en TechNet](https://aka.ms/EXOTN)
    
- [Portal de Exchange Online](https://aka.ms/EXO)
    
Para obtener más información sobre Exchange Hybrid, consulte:
  
- [Implementaciones híbridas de Exchange 2013 ](https://aka.ms/ExchangeHybrid). Tenga en cuenta que la licencia del servidor híbrido solo se requiere para los siguientes escenarios: organización de Exchange 2010 con servidor híbrido Exchange 2013 y organización de Exchange 2007 con servidor híbrido Exchange 2013 o Exchange 2010.
    
- [Inicio de sesión de Office 365](https://aka.ms/HybridKey)
    
Para obtener más información sobre Exchange Server local, consulte:
  
- [Biblioteca de Exchange Server 2013 en TechNet](https://aka.ms/Ex2013TN)
    
- [Portal de Exchange Server 2013](https://aka.ms/Exchange2013)
    
- [Arquitectura de Exchange Server 2013](https://aka.ms/Ex2013SP1ArchPoster)
    
Para obtener más información sobre Exchange hospedado por el proveedor, consulte:
  
[Guía y soluciones de varios inquilinos y hospedaje de Exchange Server 2013](https://aka.ms/Ex2013Hosting)
  
## <a name="descriptions-of-three-new-or-updated-features-in-exchange-2013"></a>Descripciones de tres características nuevas o actualizadas en Exchange 2013

### <a name="exchange-online-protection"></a>Exchange Online Protection

Exchange Online Protection (EOP) proporciona protección de correo no deseado y contra malware para cualquier implementación mediante una capa de características de protección que se implementan en una red global de centros de datos. Esto ayuda a simplificar la administración de los entornos de mensajería. EOP se incluye en las suscripciones de Exchange Online, pero también es adecuado para implementaciones híbridas y locales.
  
Los diagramas correspondientes muestran implementaciones para Exchange Online, Exchange Hybrid e Exchange local que incluyen la capa EOP en la red global.
  
### <a name="exchange-server-deployment-assistant"></a>Asistente para la implementación de Exchange Server

El Asistente para la implementación de Exchange Server es una herramienta basada en Internet que realiza algunas preguntas sobre el entorno actual, y luego genera una lista de comprobación personalizada y paso a paso para ayudarle a implementar Exchange Server para diferentes tipos de escenarios. Ya sea que migre desde una versión previa de Exchange a Exchange 2013, migre a Exchange Online, o planee una infraestructura híbrida, el Asistente para la implementación de Exchange Server crea una lista de comprobación de implementación personalizada para su escenario.
  
La captura de pantalla correspondiente muestra una lista de comprobación de ejemplo creada con el Asistente para la implementación de Exchange Server.
  
### <a name="integration-with-lync-and-sharepoint"></a>Integración con Lync y SharePoint

Exchange Server 2013 incluye muchas características que se integran con Lync Server 2013 y SharePoint Server 2013. En conjunto, estos productos ofrecen una amplia variedad de características y mejoran la colaboración en la organización. 
  
El diagrama correspondiente muestra el póster de autenticación de servidor a servidor e incluye un vínculo al póster. 
  
- Archivado, suspensión y exhibición de documentos electrónicos
    
- Buzones de sitio
    
- Almacén de contactos unificado
    
- Fotos de usuarios en alta resolución
    
- Presencia de Lync en Outlook y Outlook Web App
    
- Autenticación de servidor en servidor
    
- Correo de voz
    
- Grabaciones de reuniones
    
- Sincronización de tareas de Exchange
    
El diagrama correspondiente muestra el póster de la arquitectura de Exchange Server 2013 SP1 e incluye un vínculo al póster.
  

