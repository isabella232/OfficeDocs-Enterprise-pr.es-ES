---
title: Auditoría y creación de informes en los servicios en la nube de Microsoft
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- M365-analytics
- SPO_Content
f1.keywords:
- NOCSH
description: Información general sobre las características de auditoría e informes de Office 365, Microsoft 365 y Service Assurance.
ms.openlocfilehash: 05c16b201cecb742ab2c74e8938893222d04d59f
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843701"
---
# <a name="auditing-and-reporting-in-microsoft-cloud-services"></a>Auditoría y creación de informes en los servicios en la nube de Microsoft

## <a name="introduction"></a>Introducción

Los servicios en la nube de Microsoft incluyen varias características de informes y auditoría que puede usar para realizar un seguimiento de la actividad administrativa y del usuario dentro de su espacio empresarial; por ejemplo, los cambios realizados en las opciones de configuración de los inquilinos de Exchange Online y SharePoint Online, y cambios realizados por los usuarios en documentos y otros elementos. Puede usar la información de auditoría y los informes disponibles en los servicios en la nube de Microsoft para administrar de forma más eficaz la experiencia del usuario, mitigar los riesgos y cumplir las obligaciones de cumplimiento.

## <a name="security--compliance-centers"></a>Centros de cumplimiento de & de seguridad

[Office 365 security &](https://protection.office.com)el centro de cumplimiento, el centro de [seguridad de Microsoft 365](https://security.microsoft.com)y el [centro de cumplimiento de Microsoft 365](https://compliance.microsoft.com) son portales de un solo punto para la protección de datos en su organización y incluyen muchas características de auditoría e informes. Estos centros le ayudarán con la protección de datos o las necesidades de cumplimiento y la actividad de usuario y de administrador de auditoría. Puede acceder a estos centros con su cuenta de administrador de suscripción.

Estos centros incluyen paneles de navegación para tener acceso a varias características:

- **Alertas:** Permite administrar alertas, ver alertas relacionadas con la seguridad y administrar alertas avanzadas mediante [Office 365 Cloud App Security](https://docs.microsoft.com/cloud-app-security/what-is-cloud-app-security).
- **Permisos:** Permite [asignar permisos](https://support.office.com/article/Give-users-access-to-the-Office-365-Security-Compliance-Center-2cfce2c8-20c5-47f9-afc4-24b059c1bd76) como administrador de cumplimiento, administrador de exhibición de documentos electrónicos y otros usuarios a las personas de su organización para que puedan realizar tareas en estos centros. Se asignan permisos para la mayoría de las características de cada centro, pero otros permisos deben configurarse con el centro de administración de Exchange y el centro de administración de SharePoint.
- **Administración de amenazas:** Permite crear y aplicar directivas de administración de dispositivos mediante la [Administración de dispositivos móviles de Office 365](https://support.office.com/article/Overview-of-Mobile-Device-Management-for-Office-365-faa7d8e5-645d-4d59-839c-c8d4c1869e4a), para configurar directivas de [prevención de pérdida de datos](https://support.office.com/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e) (DLP) para su organización, para configurar el filtrado de correo electrónico, el software antimalware, el correo identificado por DomainKeys (DKIM), datos adjuntos seguros, vínculos seguros y aplicaciones de OAuth.
- **Gobierno de datos:** Permite [importar correo electrónico o datos de SharePoint desde otros sistemas en Office 365](https://support.office.com/article/Import-PST-files-or-SharePoint-data-to-Office-365-ba688e0a-0fcb-4bd7-8e57-2b669564ea84), [configurar buzones de archivo](https://support.office.com/article/Enable-archive-mailboxes-in-the-Office-365-Security-Compliance-Center-268a109e-7843-405b-bb3d-b9393b2342ce)y establecer [directivas de retención](https://docs.microsoft.com/microsoft-365/compliance/retention-policies) para el correo electrónico y otros contenidos dentro de la organización.
- **Búsqueda & investigación:** Proporciona herramientas de [búsqueda de contenido](https://support.office.com/article/Run-a-Content-Search-in-the-Office-365-Security-Compliance-Center-61852fd9-fe8a-4880-a339-cb19ed3bff4a), de [registro de auditoría](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c), de cuarentena y de administración de [casos de eDiscovery](https://support.office.com/article/Manage-eDiscovery-cases-in-the-Office-365-Security-Compliance-Center-edea80d6-20a7-40fb-b8c4-5e8c8395f6da) para profundizar rápidamente en la actividad entre buzones de correo, grupos y carpetas públicas de Exchange Online, SharePoint Online y OneDrive para la empresa.
- **Informes:** Permite tener acceso rápidamente a los [informes](https://support.office.com/article/Reports-in-the-Office-365-Security-Compliance-Center-7acd33ce-1ec8-49fb-b625-43bac7b58c5a) de SharePoint Online, OneDrive para la empresa, Exchange Online y Azure ad.
- **Garantía del servicio:** Proporciona información sobre cómo Microsoft mantiene la seguridad, la privacidad y el cumplimiento de los estándares globales de Office 365, Azure, Microsoft Dynamics CRM Online, Microsoft Intune y otros servicios en la nube. También incluye el acceso a los informes de auditoría ISO, SOC y otros de terceros, así como a los controles auditados, que proporciona información detallada acerca de los diversos controles que han sido probados y verificados por auditores de terceros de Office 365.

## <a name="service-assurance"></a>Garantía del servicio

Muchas organizaciones de industrias reguladas están sujetas a amplios requisitos de cumplimiento. Para realizar sus propias evaluaciones de riesgos, los clientes a menudo necesitan información detallada sobre cómo Office 365 mantiene la seguridad y privacidad de sus datos. Microsoft se compromete a proteger la seguridad y privacidad de los datos de los clientes en sus servicios en la nube y a conseguir la confianza del cliente proporcionando una vista transparente de sus operaciones y un acceso sencillo a las evaluaciones y los informes de cumplimiento independientes.

Garantía del servicio proporciona transparencia de operaciones e información sobre cómo Microsoft mantiene la seguridad, la privacidad y el cumplimiento de los datos del cliente en Office 365. Incluye informes de auditoría de terceros junto con una biblioteca de notas del producto, preguntas más frecuentes y otros materiales sobre los temas de Office 365, como el cifrado de datos, la resistencia de datos, la administración de incidentes de seguridad y mucho más. Los clientes pueden usar esta información para realizar sus propias evaluaciones de riesgos reguladoras. Los responsables de cumplimiento normativo pueden asignar el rol "usuario de garantía de servicio" para dar a los usuarios acceso a la garantía del servicio. El administrador de inquilinos también puede proporcionar a los usuarios externos, como auditores independientes, acceso a la información del panel de garantía del servicio a través del [portal de confianza del servicio](https://aka.ms/STP) en la nube de Microsoft (STP). Para obtener más información sobre cómo acceder a STP, visite [Introducción al portal de confianza de servicios para las suscripciones de Office 365 para empresas, Azure y Dynamics CRM Online](https://aka.ms/STPHelp).

## <a name="onedrive-for-business-admin-center"></a>Centro de administración de OneDrive para la empresa

El centro de administración de Microsoft OneDrive le ayuda a administrar de forma rápida y sencilla la configuración de OneDrive para la empresa de su organización en un solo punto. Para usar el centro de administración de OneDrive, se necesita acceso a onedrive.com. También debe ser un administrador global de su organización o un administrador personalizado con el rol de administrador de SharePoint. Obtenga acceso al centro de administración de OneDrive [https://admin.onedrive.com](https://admin.onedrive.com/)para la empresa en.

Las características clave incluyen un área de cumplimiento que proporciona a los administradores vínculos al centro de administración adecuado para escenarios clave, como la búsqueda en el registro de auditoría, el trabajo con DLP, la retención, la exhibición de documentos electrónicos y las alertas.

## <a name="related-links"></a>Vínculos relacionados

- [Características de búsqueda y eDiscovery](office-365-ediscovery-and-search-features.md)
- [Características de presentación de informes de Office 365](office-365-reporting-features.md)
- [API de Actividad de administración de Office 365](office-365-management-activity-api.md)
- [Migraciones de buzones de Office 365](office-365-mailbox-migrations.md)
- [Registro interno para el equipo de ingeniería de Office 365](office-365-internal-logging.md)