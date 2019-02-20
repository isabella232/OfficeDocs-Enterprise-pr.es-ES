---
title: Preparar la organización para Office 365 Enterprise
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 712fced7-f9d0-4fde-8b79-286262a5d0bc
description: Si ha decidido no participar en la implementación de FastTrack y no encuentra lo que necesita en nuestros pasos de implementación básicos, este es el punto de partida.
ms.openlocfilehash: a15bd73efe2fd2e2dfd13b3a444f77b9d0bfc764
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085379"
---
# <a name="get-your-organization-ready-for-office-365-enterprise"></a>Preparar la organización para Office 365 Enterprise

## <a name="what-do-you-need-to-do-to-get-ready-for-office-365"></a>¿Qué necesita hacer para prepararse para Office 365?

La mayoría de las organizaciones no tienen que hacer nada para prepararse para Office 365. Es una aplicación en la web y los usuarios pueden usarla tan pronto como tengan una cuenta. Otras organizaciones tienen más ubicaciones, prácticas de seguridad u otros requisitos que crean la necesidad de más planeación. Para las organizaciones de nivel empresarial, siga los siguientes elementos de lista de comprobación para empezar a trabajar con Office 365.
  
Si necesita ayuda para empezar a configurar Office 365, [FastTrack](https://fasttrack.microsoft.com/office) es la forma más sencilla de implementarlo. También puede iniciar sesión y usar los [Asesores de implementación de los servicios de Office 365](deployment-advisors-for-office-365.md).
  
|**Elija uno o más para empezar:**||
|:-----|:-----|
| [Requisitos del sistema para Office](https://products.office.com/office-system-requirements) |-Microsoft Office Professional, Office 365, Office 365 proPlus y todas las aplicaciones de Office para Windows, Mac, iOS y Android tienen requisitos de sistema específicos. Asegúrese de que el hardware y el software cumplen con los requisitos mínimos del sistema.|
|**La mayoría** de los clientes conectan su directorio local con Office 365. Obtenga una introducción a la preparación del directorio al [instalar y ejecutar IdFix en la red](https://www.microsoft.com/download/details.aspx?id=36832).<br> Use [AAD Connect Advisor](https://aka.ms/aadconnectpwsync) y la [Guía de configuración de Azure ad Premium](https://aka.ms/aadpguidance) para obtener instrucciones de configuración personalizadas. <br> |-Las comprobaciones automatizadas en el directorio para [validar las cuentas de las personas se sincronizarán correctamente](https://support.office.com/article/Prepare-to-provision-users-through-directory-synchronization-to-Office-365-01920974-9e6f-4331-a370-13aea4e82b3e). <br> -Recomienda cambios en los objetos de directorio y ofrece la automatización de los cambios. <br> - [Más información sobre el uso de la herramienta IdFix](prepare-directory-attributes-for-synch-with-idfix.md). |
|**Lea** nuestra [Guía de rendimiento de red](https://aka.ms/tune) y use nuestras herramientas para asegurarse de que tiene la conectividad y la configuración de rendimiento necesarias para proporcionar a los usuarios la mejor experiencia posible.  <br> | -Asegúrese de que puede conectarse a Office 365, si filtra o analiza el tráfico saliente, le interesará saber qué significa [administrar los puntos de conexión de Office 365](https://support.office.com/article/Managing-Office-365-endpoints-99cab9d4-ef59-4207-9f2b-3728eb46bf9a) para su organización.  <br>  - [Modele y pruebe su capacidad de red](https://support.office.com/article/Network-and-migration-planning-for-Office-365-f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132) o desplácese a un circuito de [Azure ExpressRoute para Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd) para obtener una experiencia más predecible.   |
|**Use** nuestra [lista de comprobación](https://support.office.com/article/Deployment-planning-checklist-for-Office-365-5fa4f6ef-35ad-4840-91c1-4834df3df5a0) de planeación como punto de partida para crear su propio plan de implementación.  <br> | -En profundidad información general sobre las posibles áreas que necesitará planear con vínculos a referencias o información de procedimientos para ayudarle a planear. |
|**Use** el [script de elementos grandes de Exchange Server](https://gallery.technet.microsoft.com/Exchange-Server-Large-Item-b9546cc6) para buscar elementos de correo que puedan ser demasiado grandes para la migración.  <br> | : Usa los servicios Web de Exchange para suplantar, tener acceso, analizar el buzón en busca de tamaños de archivo que especifique y volcar los resultados en un archivo CSV. Lea las [instrucciones detalladas sobre cómo usar el script](https://blogs.technet.com/b/mikehall/archive/2013/06/27/large-mail-item-script.aspx). |
|**** Aprovéchese de los [expertos en implementación de Microsoft](https://go.microsoft.com/fwlink/?LinkId=517115) que pueden ayudarle a planear la ayuda de todos los usuarios a empezar a usar los nuevos servicios y aplicaciones.  <br> Use los [asistentes para la implementación de los servicios de Office 365](https://support.office.com/article/Deployment-wizards-for-Office-365-services-165f46e8-3533-4d76-be57-97f81ebd40f2) para obtener instrucciones de configuración personalizadas.  <br> | -El centro de incorporación trabaja directamente con los clientes y con organizaciones asociadas. Dar una llamada hoy. |
|**Use** las [plantillas y recursos del centro de éxito de Office 365](https://www.microsoft.com/fasttrack/resources) para compartir su implementación y planes de incorporación con las personas de su organización.  <br> | -La comunicación con todos los usuarios antes, durante y después de la transición a Office 365 es fundamental.  <br> -Use nuestras plantillas, guías y documentos para mejorar sus comunicaciones. |
|**Lea** el artículo los [principios de conectividad de red de Office 365](https://aka.ms/o365networkingprinciples) para comprender los principios de conectividad para administrar de forma segura el tráfico de Office 365 y obtener el mejor rendimiento posible.  <br> | -Este artículo le ayudará a comprender las instrucciones más recientes para optimizar de manera segura la conectividad de red de Office 365. |
   
¿Desea más recursos para ayudarle a integrar Office 365 con su estrategia de nube más amplia? Estos son los [recursos de arquitectura de TI de Microsoft Cloud](https://docs.microsoft.com/en-us/office365/enterprise/microsoft-cloud-it-architecture-resources).
  
## <a name="want-to-talk-with-support"></a>¿Desea hablar con soporte técnico?

Estamos aquí para ayudarle, [póngase en contacto con soporte técnico](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) para productos empresariales.
