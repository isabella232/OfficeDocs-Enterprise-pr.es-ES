---
title: Límites de sitio del portal de SharePoint Online moderno
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/9/2019
audience: Admin
ms.topic: interactive-tutorial
ms.service: o365-administration
localization_priority: Normal
ms.collection: Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
description: Obtenga información sobre las recomendaciones de rendimiento para sitios modernos en SharePoint Online.
ms.openlocfilehash: 2ff7f76a943563644403f3df2b6b0a6ee9b28d53
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2019
ms.locfileid: "38031275"
---
# <a name="sharepoint-online-modern-portal-site-limits"></a>Límites de sitio del portal de SharePoint Online moderno

En este artículo se proporcionan recomendaciones de rendimiento para los sitios de portal modernos en SharePoint Online. Use las directrices de este artículo para optimizar el rendimiento del sitio del portal moderno y evitar problemas comunes de rendimiento.

## <a name="performance-considerations-for-modern-portal-sites"></a>Consideraciones de rendimiento para sitios de portal modernos

Desde el punto de vista de la optimización del rendimiento, hay algunas características que hacen que los sitios modernos del portal sean únicos. La diferencia principal entre la colaboración y los sitios de portal en SharePoint Online es la escala. Por lo general, se espera que los sitios de portal atiendan más vistas de página a un número mayor de usuarios que los sitios de colaboración y que contengan más contenido estático y menos recursos editables. Además, la arquitectura de los sitios modernos difiere de los clásicos en que la mayor parte del procesamiento implicado en la representación de páginas y la ejecución de código tiene lugar en el cliente y no en el servidor.

La optimización del rendimiento de los sitios de portal modernos se centra principalmente en algunos objetivos generales:

- Reducir el tamaño total de los componentes de cada página del sitio
- Descarga de archivos estáticos comunes como imágenes, hojas de estilo y scripts en la red CDN
- Limitar las llamadas a SharePoint y a los extremos externos solo a lo necesario
- Evitar solicitudes duplicadas para el mismo contenido

Muchas de las instrucciones de este artículo se centran en minimizar y optimizar las llamadas a SharePoint Online. Realizar llamadas repetitivas cada vez que se cargue una página, afectará al rendimiento de los usuarios, ya que la información se recuperará del servicio cada vez incluso si no ha cambiado. Por lo tanto, las solicitudes a SharePoint se pueden clasificar como llamadas comunes para todos los usuarios o llamadas necesarias para cada usuario individual. Los resultados de estas dos categorías de llamadas deben almacenarse en caché para optimizar la experiencia del usuario.

>[!NOTE]
>Use la [herramienta diagnósticos de página para SharePoint](https://aka.ms/perftool) como punto de partida para analizar métricas de rendimiento específicas en las páginas de sitio de SharePoint Online.

## <a name="modern-portal-site-limits-and-recommendations"></a>Límites y recomendaciones del sitio del portal modernos

|**Límite**|**Valor máximo recomendado**|**Notas**|
|:-----|:-----|:-----|:-----|
|Páginas y elementos de noticias  <br/> |5.000 por sitio  <br/> |Se recomienda limitar el número de páginas y elementos de noticias en un sitio de portal moderno a menos de 5.000.  <br/> |
|Elementos Web en una página  <br/> |20 por página  <br/> |Se recomienda usar 20 o menos elementos Web por página, incluidos los elementos Web de Microsoft y los elementos Web personalizados. <br/> Para obtener más información, vea [optimizar el rendimiento de elementos Web en las páginas de sitio modernas de SharePoint Online](modern-web-part-optimization.md).  <br/> |
|Elementos web dinámicos en una página  <br/> |4 por página  <br/> |Los elementos web dinámicos que realizan una o más consultas a SharePoint para recuperar los datos más recientes deben limitarse a 4 por página. El elemento Web _News_ es un ejemplo de un elemento Web dinámico. <br/> Para obtener más información, vea [optimizar el rendimiento de elementos Web en las páginas de sitio modernas de SharePoint Online](modern-web-part-optimization.md).    <br/> |
|Grupos de seguridad  <br/> |20 por sitio  <br/> |El número de grupos de seguridad afecta a la escala de muchas consultas en los sitios de portal modernos. Le recomendamos que limite el número de grupos de seguridad a un tamaño tan pequeño como sea posible, sin más de 20 por sitio.  <br/> |
|Elementos en la navegación del sitio  <br/> |100 por sitio  <br/> |Se recomienda agregar menos de 100 elementos a la navegación del sitio y usar controles de navegación preparados.  <br/> Para obtener más información, vea [optimizar el peso de página en las páginas de sitio modernas de SharePoint Online](modern-page-weight-optimization.md). <br/> |
|Tamaño máximo de imagen  <br/> |300 KB por imagen  <br/> |Se recomienda limitar el tamaño de las imágenes a 300kb o menor, y usar una CDN para hospedar imágenes, hojas de estilos y scripts. <br/>Para obtener más información, vea [optimizar imágenes en las páginas de sitio modernas de SharePoint Online](modern-image-optimization.md) y [usar la red de entrega de contenido (CDN) de Office 365 con SharePoint Online](use-office-365-cdn-with-spo.md).  <br/> |
|Usuarios con derechos de edición  <br/> |200 usuarios por sitio  <br/> |Los sitios de portal de SharePoint están optimizados para ver y consumir contenido. Los permisos de edición de un portal deben estar limitados a un grupo restringido de usuarios, ya que los permisos de edición descargan controles adicionales y, por lo tanto, son más lentos para esos usuarios. Por lo tanto, un número excesivo de usuarios con permisos de edición afectará a la experiencia general. <br/> |
|IFrames de terceros  <br/> |2 por página  <br/> |los iFrame son inesperadamente lentos porque cargan una página externa independiente que incluye todo el contenido asociado, como los elementos JavaScript, CSS y Framework. Si debe usar iFrames, limite el número a 2 o menos por página.<br/> Para obtener más información, vea [optimizar los iframes en las páginas de sitio de publicación clásico y moderna de SharePoint Online](modern-iframe-optimization.md). <br/> |
|Llamadas al servicio UPA  <br/> |1 por usuario por hora  <br/> |Le recomendamos que no realice llamadas _por solicitud_ al servicio UPA (aplicación de Perfil de usuario). Se puede usar la API y el [PageContext](https://docs.microsoft.com/javascript/api/sp-page-context/pagecontext?view=sp-typescript-latest) de [Microsoft Graph](https://docs.microsoft.com/graph/call-api) para consultar la información del usuario.  <br/> Si se necesita una llamada del servicio de UPA, realice una única llamada cuando sea necesario y, a continuación, almacene en caché la información para volver a usarla en la misma sesión. |
|Llamadas al servicio de taxonomía  <br/> |5 por usuario y por hora  <br/> |Le recomendamos que no realice llamadas _por solicitud_ al servicio de taxonomía. Si es necesario realizar llamadas al servicio de taxonomía, almacene la información para reutilizarla en la misma sesión. <br/> Para obtener más información, vea [optimizar las llamadas de página en las páginas de sitio de publicación clásico y moderna de SharePoint Online](modern-page-call-optimization.md). <br/> |

## <a name="related-topics"></a>Temas relacionados

[Creación de un portal de SharePoint saludable](https://docs.microsoft.com/sharepoint/portal-health)

[Ajustar el rendimiento de SharePoint Online](tune-sharepoint-online-performance.md)

[Ajustar el rendimiento de Office 365](tune-office-365-performance.md)

[SharePoint Online limits](https://docs.microsoft.com/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits) (Límites de SharePoint Online)

[Rendimiento en la experiencia moderna de SharePoint](https://docs.microsoft.com/sharepoint/modern-experience-performance)

[Guía de rendimiento para los portales de SharePoint Online](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-performance)
