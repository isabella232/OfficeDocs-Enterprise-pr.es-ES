---
title: Migración de Microsoft Cloud Alemania (Microsoft Cloud Deutschland) a los servicios de Office 365 en las nuevas regiones del centro de datos alemán
ms.author: andyber
author: andybergen
manager: laurawi
ms.date: 12/09/2019
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: 'Resumen: comprender la migración de Microsoft Cloud Alemania (Microsoft Cloud Deutschland) a los servicios de Office 365 en las nuevas regiones del centro de datos alemán'
ms.openlocfilehash: 0a90c1b7f74ce9bc14ccae9965c4ce07f74e1b73
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998565"
---
# <a name="migration-from-microsoft-cloud-germany-microsoft-cloud-deutschland-to-office-365-services-in-the-new-german-datacenter-regions"></a>Migración de Microsoft Cloud Alemania (Microsoft Cloud Deutschland) a los servicios de Office 365 en las nuevas regiones del centro de datos alemán


>[!Note]
>Este artículo solo se aplica a los clientes de Microsoft Cloud Alemania/Deutschland elegibles.
>

## <a name="cloud-service-offerings-in-germany"></a>Ofertas del servicio en la nube en Alemania

En agosto de 2018, anunciamos nuestra intención de ofrecer todos los servicios en la nube de Microsoft (Azure, Office 365 y Dynamics 365 y Power Platform) a partir de las nuevas regiones en la nube en Alemania para facilitar la mejor transformación digital posible de nuestros clientes. En agosto de 2019, anunciamos que estamos en proceso de abrir las nuevas regiones en la nube en Alemania. Anunciamos la disponibilidad de Azure en agosto y Office 365 empezó a estar disponible en diciembre.  Creemos que en el primer trimestre de 2020, Power Platform y Dynamics 365 estarán disponibles.  

Las nuevas regiones se diseñaron para satisfacer las necesidades de desarrollo de los clientes alemanes, con la mayor flexibilidad, la última administración en la nube y la conectividad completa con nuestra red global en la nube, así como la permanencia de los datos de los clientes en Alemania.

## <a name="moving-to-the-new-german-regions"></a>Pasar a las nuevas regiones alemanas

Los clientes existentes de Microsoft Cloud Alemania (Microsoft Cloud Deutschland) ahora pueden empezar a migrar sus clientes de Office 365, Dynamics 365 Customer Engagement, y Power Platform BI.  El primer paso consiste en [participar en una migración dirigida por Microsoft](https://aka.ms/office365germanymoveoptin) a las nuevas regiones del centro de datos alemán.

Para las organizaciones que participan en el enfoque liderado por Microsoft, se espera que las migraciones se realicen en 2020. Como resultado de la migración, los datos básicos del cliente y las suscripciones se mueven a las nuevas regiones alemanas. 

Los siguientes servicios se migrarán como parte del enfoque liderado por Microsoft:

- Azure Active Directory
- Exchange en línea
- Exchange Online Protection
- SharePoint Online
- OneDrive para la Empresa
- Skype Empresarial Online

Durante la migración de Microsoft Cloud Alemania a las regiones del centro de datos alemán, los clientes existentes de Skype Empresarial Online pasarán a Microsoft Teams. Para obtener más información, consulte [Introducción a su actualización de Microsoft Teams](https://aka.ms/SkypeToTeams-Home).

- Grupos de Office 365
- Dynamics 365 / Power Platform

Los requisitos y el impacto de la migración para estos servicios se describen en el artículo [Dynamics 365 Customer Engagement](https://aka.ms/D365ceOptIn).

## <a name="how-to-prepare-for-migration-to-office-365-services-in-the-new-german-datacenter-regions"></a>Cómo preparar la migración a los servicios de Office 365 en las nuevas regiones del centro de datos alemán.

El primer paso es notificar a Microsoft del permiso para migrar la suscripción y los datos de Microsoft Cloud Alemania/Deutschland a los servicios de Office 365 en las nuevas regiones del centro de datos alemán.  Para obtener más información, consulte el [proceso de participación](ms-cloud-germany-migration-opt-in.md).

- Todos los clientes que migren deben comprobar la conectividad a las [direcciones IP y URL de Office 365 en todo el mundo](urls-and-ip-address-ranges.md), entre las que se incluyen las nuevas regiones del centro de datos alemán.
- Consulte la descripción del servicio de plataforma de Office 365 para comprender las características y los servicios disponibles en su organización cuando termine el proceso de traslado a la región alemana. 
- En la migración se llevará a cabo la transición de las suscripciones de pago.  No se pueden migrar suscripciones de prueba.

Las migraciones de espacios empresariales se ejecutan como operaciones de servicio back-end con la interacción mínima necesaria con el cliente.  Las demás tareas lideradas por los clientes y el estado general de la migración aparecerán en el Centro de mensajes durante el proceso de migración.  Algunos ejemplos de tareas pueden incluir actualizaciones de DNS administradas por el cliente o cambios en la configuración híbrida para clientes híbridos de Exchange.

## <a name="customer-experience-during-the-migration-to-office-365-services-in-the-new-german-datacenter-regions"></a>Experiencia del cliente en la migración a los servicios de Office 365 en las nuevas regiones del centro de datos alemán.

Las migraciones de inquilinos están diseñadas para tener un impacto mínimo en los clientes finales y en los administradores.  Sin embargo, hay consideraciones para cada carga de trabajo.  

### <a name="azure-active-directory"></a>Azure Active Directory

Las suscripciones de Office/Dynamics de Microsoft Cloud Alemania se transfieren a la región alemana con la reubicación de Azure Active Directory (Azure AD). La organización se actualizará para reflejar las nuevas suscripciones de servicio mundiales. Durante el breve proceso de transferencia de la suscripción, se bloquearán los cambios en las suscripciones.

### <a name="exchange-online"></a>Exchange Online

Los clientes híbridos de Exchange Online deben volver a ejecutar el Asistente para la configuración híbrida con el fin de actualizar la configuración local en base a Microsoft Cloud Alemania antes de la transición, y volver a ejecutar el asistente tras la adaptación al servicio mundial. Es posible que se necesiten actualizaciones de DNS adicionales para los clientes con dominios personalizados.

Los buzones se migran dentro de un proceso de back-end. Los usuarios de su organización pueden estar en Microsoft Cloud Alemania o en una región alemana durante la transición y son parte de la misma organización de Exchange (GAL).

### <a name="exchange-online-protection"></a>Exchange Online Protection

Las características de back-end de Exchange Online Protection se copian a la nueva región de Alemania

### <a name="sharepoint-online"></a>SharePoint Online

Cuando finalice la migración de SharePoint Online a la región alemana, se volverán a crear los índices de datos. Las características que dependan de los índices de búsqueda pueden quedar afectadas cuando termine la indización.

Se conservan las URL de sharepoint.de existentes para las organizaciones que hayan hecho la transición.

### <a name="onedrive-for-business"></a>OneDrive para la Empresa

Cuando finalice la migración de OneDrive para la Empresa a la región alemana, se volverán a crear los índices de datos. Las características que dependan de los índices de búsqueda pueden quedar afectadas cuando termine la indización.

### <a name="skype-for-business-online"></a>Skype Empresarial Online

Los clientes existentes de Skype Empresarial Online pasarán a Microsoft Teams. Vea [https://aka.ms/SkypeToTeams-Home](https://aka.ms/SkypeToTeams-Home) para obtener más información.


## <a name="key-differences-between-microsoft-cloud-germany-microsoft-cloud-deutschland-and-office-365-services-in-the-new-german-datacenter-regions"></a>Diferencias clave entre Microsoft Cloud Alemania (Microsoft Cloud Deutschland) y los servicios de Office 365 en las nuevas regiones del centro de datos alemán


|| Microsoft Cloud Alemania (Microsoft Cloud Deutschland) | Los servicios de Office 365 en las nuevas regiones del centro de datos alemán. |
|:-------|:-----|:-----|
| Servicios de Microsoft 365 disponibles para suscripción con un solo espacio empresarial de Office 365 | 15 servicios (consulte REF) | 29 servicios (consulte REF) |
| Características nuevas | No hay disponibles características nuevas | Las nuevas características estarán uniformemente disponibles con los servicios globales de Office 365. |
| Administrador de datos | Sí | No |
| Colaboración entre espacios empresariales con los espacios empresariales globales de Office 365 | No | Sí |
| Residencia de datos de clientes | Los datos de los clientes se almacenarán únicamente en los centros de datos alemanes. | Microsoft almacenará los siguientes datos de cliente únicamente en Alemania: contenido del buzón de Exchange Online (cuerpo del correo electrónico, entradas de calendario y el contenido de los datos adjuntos del correo electrónico), el contenido y los archivos almacenados en el sitio de SharePoint Online y los archivos cargados en OneDrive para la Empresa. |
| Términos aplicables | [Términos de servicios en línea](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=46) con [suplemento](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=64) | [Términos de servicios en línea](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=46) |
||||

## <a name="frequently-asked-questions"></a>Preguntas más frecuentes

### <a name="is-migration-required"></a>¿Es la migración obligatoria?

Microsoft ofrece sin coste adicional la migración de los espacios empresariales de Office 365, desde Microsoft Cloud Alemania a los servicios de Office 365 en las nuevas regiones del centro de datos alemán.  A pesar de que le recomendamos encarecidamente que participe en la migración a las nuevas regiones del centro de datos alemán, seguiremos ofreciéndole las actualizaciones de seguridad necesarias para la región Microsoft Cloud Alemania.  

Los servicios de Office 365 en las nuevas regiones del centro de datos alemán tienen beneficios adicionales:

- Ofertas competitivas para [Azure](https://azure.microsoft.com/pricing/calculator/), [Office 365](https://www.microsoft.com/microsoft-365/business/compare-more-office-365-for-business-plans), [Dynamics 365 Customer Engagement](https://dynamics.microsoft.com/pricing/) y [Power BI](https://powerbi.microsoft.com/pricing/). 
- Conexión con la red global de Microsoft, con cientos de sitios perimetrales de red, ubicaciones de emparejamiento y puntos de salida para ofrecer una experiencia de usuario robusta en cualquier parte del mundo. 
- Asistencia para que pueda cumplir los requisitos de residencia de datos de clientes locales en Alemania. 
- Nuestra oferta global completa para la nube, que incluye la versión más reciente de nuestros servicios y nuevas funciones, como Microsoft Teams y Multi-Geo en Office 365. Comparar productos por región para [Azure](https://azure.microsoft.com/global-infrastructure/services/?products=all&regions=germany-non-regional,germany-central,germany-north,germany-northeast,germany-west-central), [Office 365](https://docs.microsoft.com/office365/enterprise/o365-data-locations) y [Dynamics 365](https://docs.microsoft.com/dynamics365/get-started/availability).
- Funcionalidad completa, una seguridad de nivel empresarial y una amplia variedad de características para ayudar a los clientes a cumplir los requisitos de cumplimiento normativo. 
- Acceso a través de los contratos de servicios en línea existentes.

#### <a name="what-is-the-service-availability-between-the-different-office-365-cloud-service-offerings"></a>¿Cuál es la disponibilidad del servicio entre las diferentes ofertas de servicios en la nube de Office 365?

En la oferta de servicios en la nube de Microsoft Cloud Alemania (Microsoft Cloud Deutschland) están disponibles los siguientes 15 servicios.  No estamos agregando nuevos servicios a Microsoft Cloud Alemania.

1. Exchange Online
2. Caja de seguridad del cliente (Exchange Online)
3. Grupos (grupos modernos)
4. Perfil de Delve
5. Exchange Online Protection
6. Protección contra amenazas avanzada (ATP)
7. eDiscovery avanzado
8. Control avanzado de datos
9. SharePoint Online
10. Caja de seguridad del cliente (SharePoint Online)
11. OneDrive para la Empresa
12. Skype Empresarial
13. Word Online, Excel Online, PowerPoint, OneNote y Visio Online
14. Office 365 Pro Plus
15. Outlook Mobile

Actualmente, hay 29 servicios disponibles como parte de los servicios de Office 365 en las nuevas regiones del centro de datos alemán.  Las nuevas características y servicios estarán disponibles consecuentemente con los servicios globales de Office 365 de manera continua.

1. Exchange Online
2. Caja de seguridad del cliente (Exchange Online)
3. Grupos (grupos modernos)
4. Perfil de Delve
5. MyAnalytics
6. Workplace Analytics
7. Exchange Online Protection
8. Protección contra amenazas avanzada (ATP)
9. eDiscovery avanzado
10. Administración de seguridad avanzada
11. Information Rights Management
12. Control avanzado de datos
13. SharePoint Online
14. Caja de seguridad del cliente (SharePoint Online)
15. OneDrive para la Empresa
16. Microsoft Stream
17. Skype Empresarial (se hará la transición a Microsoft Teams durante la migración)
18. PBX en la nube
19. Conferencias RTC
20. Llamadas RTC
21. Microsoft Teams
22. Informes de uso e informes de administración
23. Word Online, Excel Online, PowerPoint, OneNote y Visio Online
24. Planner
25. Sway
26. Office 365 Pro Plus
27. Outlook Mobile
28. EMS E3 (Azure Active Directory Premium P1 + Intune + Rights Management Service)
29. Yammer Online

### <a name="when-will-migration-happen"></a>¿Cuándo se producirá la migración?

#### <a name="azure"></a>Azure 

Puede empezar a [migrar](https://docs.microsoft.com/azure/germany/germany-migration-main) los recursos de Azure a otra región. Si tiene Azure con Office 365, Dynamics 365 o Power BI, siga los pasos que se indican a continuación.

#### <a name="office-365"></a>Office 365

[Participe](https://aka.ms/office365germanymoveoptin) hoy en la migración liderada por Microsoft. Cuando esté listo para empezar la migración, le informaremos en el [Centro de mensajes](https://docs.microsoft.com/office365/admin/manage/message-center?view=o365-worldwide) del Centro de administración de Microsoft 365.

#### <a name="dynamics-365-and-power-bi"></a>Dynamics 365 y Power BI

Participe ya en la migración liderada por Microsoft para [Dynamics 365 Customer Engagement](https://aka.ms/D365ceOptIn) y [Power BI](https://aka.ms/pbioptin). Cuando esté listo para empezar la migración, le informaremos en el [Centro de mensajes](https://docs.microsoft.com/office365/admin/manage/message-center?view=o365-worldwide) del Centro de administración de Microsoft 365.

### <a name="will-the-price-change-for-the-office-services-that-i-use"></a>¿Cambiará el precio de los servicios de Office que uso?

Sí, el precio de las regiones en la nube global de Microsoft (incluidas las nuevas regiones del centro de datos) es generalmente inferior.

### <a name="how-do-i-get-help-from-microsoft-to-migrate-to-a-new-region-or-answer-support-questions"></a>¿Cómo puedo obtener ayuda de Microsoft para migrar a una nueva región o hacer preguntas a soporte técnico?

Si tiene alguna pregunta, puede ponerse en contacto con nosotros de la siguiente forma o a través de su asociado:

- Para Azure, puede enviar [nuevas solicitudes de soporte técnico](https://portal.microsoftazure.de/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/newsupportrequest) en Azure Portal.
- Para Office 365, envíe preguntas con el vínculo "¿Necesita ayuda?" del [Centro de administración de Microsoft 365](https://portal.office.de/).
- En el caso de un cliente con Dynamics 365 Customer Engagement y Power BI que también tenga Office 365, puede enviar preguntas con el vínculo "¿Necesita ayuda?" del [Centro de administración de Microsoft 365](https://portal.office.de/). Las opciones de soporte de Dynamics 365 Customer Engagement se encuentran [aquí](https://docs.microsoft.com/dynamics365/get-started/support/). Las opciones de soporte técnico de Power BI se encuentran [aquí](https://powerbi.microsoft.com/support/).

## <a name="more-information"></a>Más información

- [Asistencia para la migración a Microsoft Cloud Alemania](https://aka.ms/germanymigrateassist)
- [Cómo participar en la migración](https://aka.ms/office365germanymoveoptin)
- [Información del programa de migración de Dynamics 365](https://aka.ms/D365ceOptIn)
- [Información del programa de migración de Power BI](https://aka.ms/pbioptin)
- [Direcciones URL e intervalos de direcciones IP de Office 365](https://aka.ms/o365endpoints)
- [Asistente de configuración híbrida de Office 365](https://aka.ms/HybridWizard)
- [Introducción a su actualización de Microsoft Teams](https://aka.ms/SkypeToTeams-Home)
