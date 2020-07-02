---
title: Aislamiento y control de acceso 365 de Microsoft en Azure Active Directory
ms.author: josephd
author: JoeDavies-MSFT
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
f1.keywords:
- NOCSH
description: 'Resumen: funcionamiento del aislamiento y el control de acceso dentro de Azure Active Directory.'
ms.openlocfilehash: fe242acb5d14f5c90d6e646140b50f5f96c7a331
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998720"
---
# <a name="microsoft-365-isolation-and-access-control-in-azure-active-directory"></a>Aislamiento y control de acceso 365 de Microsoft en Azure Active Directory

Azure Active Directory (Azure AD) se diseñó para hospedar varios inquilinos de forma muy segura mediante el aislamiento de datos lógicos. El acceso a Azure AD está canalizado por una capa de autorización. Azure AD aísla a los clientes que usan contenedores de inquilinos como límites de seguridad para proteger el contenido de un cliente de modo que los coinquilinos no puedan obtener acceso a dicho contenido ni puedan verse comprometidos. La capa de autorización de Azure AD realiza tres comprobaciones:

- ¿Está habilitada la entidad principal para obtener acceso al espacio empresarial de Azure AD?
- ¿Está habilitada la entidad principal para obtener acceso a los datos de este inquilino?
- ¿La entidad de identidad está autorizada en este inquilino para el tipo de acceso a datos solicitado?

Ninguna aplicación, usuario, servidor o servicio puede obtener acceso a Azure AD sin la autenticación y el certificado correctos. Las solicitudes se rechazan si no van acompañadas de las credenciales correctas.

De hecho, Azure AD hospeda cada inquilino en su propio contenedor protegido, con directivas y permisos para y dentro del contenedor que solo posee y administra el inquilino.
 
![Azure Container](media/office-365-isolation-azure-container.png)

El concepto de contenedores de inquilinos es profundamente ingranulado en el servicio de directorio en todas las capas, desde portales hasta almacenamiento persistente. Incluso cuando varios metadatos de inquilino de Azure AD se almacenan en el mismo disco físico, no hay una relación entre los contenedores que no sean lo definido por el servicio de directorio, que a su vez es dictado por el administrador de inquilinos. No puede haber conexiones directas con el almacenamiento de Azure AD desde ninguna aplicación o servicio de solicitud sin atravesar primero el nivel de autorización.

En el ejemplo siguiente, contoso y Fabrikam tienen contenedores independientes dedicados y, aunque estos contenedores pueden compartir algunas de las infraestructuras subyacentes, como los servidores y el almacenamiento, permanecen separadas y aisladas entre sí y se canalizan por capas de autorización y control de acceso.
 
![Contenedores dedicados de Azure](media/office-365-isolation-azure-dedicated-containers.png)

Además, no hay componentes de la aplicación que se puedan ejecutar desde dentro de Azure AD y no es posible que un inquilino infrinja forzosamente la integridad de otro inquilino, obtenga acceso a las claves de cifrado de otro inquilino o lea datos sin procesar del servidor.

De forma predeterminada, Azure AD no permite todas las operaciones emitidas por las identidades en otros inquilinos. Cada inquilino se aísla lógicamente en Azure AD mediante los controles de acceso basados en notificaciones. Las lecturas y escrituras de datos de directorio se limitan a contenedores de inquilinos y se canalizan mediante una capa de abstracción interna y una capa de control de acceso basado en roles (RBAC), que en conjunto aplican el inquilino como límite de seguridad. Todas las solicitudes de acceso a datos de directorio se procesan mediante estas capas y cada solicitud de acceso en Microsoft 365 se controla mediante la lógica anterior.

Azure AD tiene particiones en Norteamérica, gobierno de Estados Unidos, Unión Europea, Alemania y World Wide. Un inquilino existe en una sola partición y las particiones pueden contener varios inquilinos. La información de particiones se abstrae de los usuarios. Una partición determinada (incluidos todos los inquilinos que contenga) se replica en varios centros de recursos. La partición de un inquilino se elige en función de las propiedades del espacio empresarial (por ejemplo, el código del país). Los secretos y otra información confidencial en cada partición se cifran con una clave dedicada. Las claves se generan automáticamente cuando se crea una partición nueva.

Las funciones del sistema de Azure AD son una instancia única para cada sesión de usuario. Además, Azure AD usa tecnologías de cifrado para proporcionar aislamiento de recursos del sistema compartidos en el nivel de red para evitar la transferencia de información no autorizada e involuntaria.
