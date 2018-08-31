---
title: Preparación de la organización para Office 365 Enterprise
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 712fced7-f9d0-4fde-8b79-286262a5d0bc
description: Si ha optado por fuera de la implementación de FastTrack y no se encuentra lo que necesita en nuestros pasos básicos de implementación, este es el lugar para comenzar.
ms.openlocfilehash: 552579347ae5f4b72821d350a061f3ba8d48841b
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22543010"
---
# <a name="get-your-organization-ready-for-office-365-enterprise"></a>Preparación de la organización para Office 365 Enterprise

## <a name="what-do-you-need-to-do-to-get-ready-for-office-365"></a>¿Qué debe hacer para prepararse para Office 365?

La mayoría de las organizaciones no es necesario hacer nada para preparar para Office 365. Se trata de una aplicación en la web y personas pueden utilizarlo tan pronto como que tienen una cuenta. Otras organizaciones tienen más ubicaciones, prácticas de seguridad u otros requisitos que crean la necesidad de planeación más. Para las organizaciones de nivel de empresa, siga los elementos de lista de comprobación siguientes para empezar a trabajar con Office 365.
  
Si desea obtener ayuda Introducción a Office 365, configurar, [FastTrack](https://fasttrack.microsoft.com/office) es la forma más sencilla de implementar Office 365, también puede iniciar sesión y utilizar los [asesores de implementación de servicios de Office 365](deployment-advisors-for-office-365.md).
  
|**Elija una o más para empezar:**||
|:-----|:-----|
| [Requisitos del sistema para Office](https://products.office.com/office-system-requirements) |-Microsoft Office Professional, Office 365, Office 365 ProPlus y cada aplicación de Office para Windows, Mac, iOS y Android tienen requisitos específicos del sistema. Asegúrese de que su hardware y software cumplan los requisitos mínimos del sistema.|
|**La mayoría** de los clientes conectan su directorio local a Office 365. Obtenga un avance de preparación de Active directory por [instalar y ejecutar IdFix en la red](https://www.microsoft.com/download/details.aspx?id=36832).<br> Use el [Asesor de AAD conectar](https://aka.ms/aadconnectpwsync) y la [que guía de configuración de Azure AD Premium](https://aka.ms/aadpguidance) para obtener instrucciones de configuración personalizada establecer. <br> |-Automatizada comprobaciones en su directorio para [Validar popular cuentas se sincronizarán correctamente](https://support.office.com/article/Prepare-to-provision-users-through-directory-synchronization-to-Office-365-01920974-9e6f-4331-a370-13aea4e82b3e). <br> -Recomienda cambios a objetos de Active directory y ofrece la posibilidad de automatizar los cambios para usted. <br> - [Para obtener más detalles sobre el uso de la herramienta IdFix](prepare-directory-attributes-for-synch-with-idfix.md). |
|**Lectura** nuestra [Guía de rendimiento de red](https://aka.ms/tune) y el uso nuestras herramientas para asegurarse de que tienen la configuración de conectividad y rendimiento necesaria para proporcionar a los usuarios con la mejor experiencia.  <br/> | -Asegúrese de que puede conectarse a Office 365, si filtrar o analizar saliente tráfico, deseará comprender qué de [administración de Office 365 extremos](https://support.office.com/article/Managing-Office-365-endpoints-99cab9d4-ef59-4207-9f2b-3728eb46bf9a) significa para su organización.  <br/>  - [Modelo y probar la capacidad de red](https://support.office.com/article/Network-and-migration-planning-for-Office-365-f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132) o mover a un circuito de [ExpressRoute de Azure para Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd) para una experiencia más predecible.  <br/> |
|**Use** nuestra [lista de comprobación de planeación](https://support.office.com/article/Deployment-planning-checklist-for-Office-365-5fa4f6ef-35ad-4840-91c1-4834df3df5a0) como un punto de partida para crear su propio plan de implementación.  <br/> | -Detallada información general de posibles áreas que necesitará para planear con vínculos a información de referencia o procedimientos que le ayudarán a planear.  <br/> |
|**Usar** el [Script de elemento grande de Exchange Server](https://gallery.technet.microsoft.com/Exchange-Server-Large-Item-b9546cc6) para buscar los elementos de correo que sea demasiado grandes para migrar.  <br/> | -Usa los servicios Web Exchange para suplantar, tener acceso, examinar el buzón de correo para los tamaños de archivo que especifique y volcados de los resultados en un archivo CSV. Lea las [instrucciones detalladas sobre cómo utilizar la secuencia de comandos](https://blogs.technet.com/b/mikehall/archive/2013/06/27/large-mail-item-script.aspx).<br/> |
|**Aproveche [los expertos de implementación de Microsoft](https://go.microsoft.com/fwlink/?LinkId=517115) que pueden ayudarle a desde la planificación para ayudar a todos los usuarios** empezar a usar los nuevos servicios y aplicaciones.  <br/> Use los [asistentes para la implementación de servicios de Office 365](https://support.office.com/article/Deployment-wizards-for-Office-365-services-165f46e8-3533-4d76-be57-97f81ebd40f2) para obtener instrucciones de configuración personalizada establecer.  <br/> | -El centro de incorporación funciona directamente con los clientes y con las organizaciones asociadas. Conceda una llamada de hoy en día.  <br/> |
|**Las [plantillas y los recursos en el centro de éxito de Office 365](https://fasttrack.microsoft.com/office/drive-value/engage) para compartir su implementación y la incorporación de redes planes con las personas de su organización.**  <br/> | -La comunicación con todos los usuarios antes, durante y después de la transición a Office 365 es crítica.  <br/> -Use nuestra plantillas, guías y documentos para mejorar sus comunicaciones.  <br/> |
|**Leer** el artículo [Principios de conectividad de red de Office 365](https://aka.ms/o365networkingprinciples) para comprender los principios de conectividad para administrar el tráfico de Office 365 y obtener el mejor rendimiento posible de forma segura.  <br/> | -Este artículo le ayudará a comprender las instrucciones más reciente para optimizar de forma segura conectividad de red de Office 365.  <br/> |
   
¿Desea obtener más recursos que le ayudarán a integrar Office 365 con su estrategia más amplia de la nube? Estos son los [recursos de la arquitectura de TI de nube de Microsoft](https://docs.microsoft.com/en-us/office365/enterprise/microsoft-cloud-it-architecture-resources).
  
## <a name="want-to-talk-with-support"></a>¿Desea hablar con el soporte técnico?
Estamos aquí para ayudar a, [póngase en contacto con soporte técnico](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) para productos de negocio.
