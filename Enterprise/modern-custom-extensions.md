---
title: Optimizar las extensiones personalizadas en las páginas de sitio modernas de SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 03/11/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.reviewer: sstewart
search.appverid:
- MET150
description: Obtenga información sobre cómo optimizar el rendimiento de extensiones personalizadas en páginas de sitio modernas de SharePoint Online.
ms.openlocfilehash: dbf0c3cba009a102bf37dd65f14e8cb882303cfe
ms.sourcegitcommit: bb122479c3a2757c0a5adde6c9f0c77c75ab3951
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "46548862"
---
# <a name="optimize-custom-extension-performance-in-sharepoint-online-modern-site-pages"></a>Optimizar el rendimiento de extensiones personalizadas en páginas del sitio modernas de SharePoint Online

Este artículo le ayudará a determinar cómo las extensiones personalizadas afectan a la latencia que percibe el usuario y cómo corregir los problemas más comunes.

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-custom-extensions"></a>Usar la herramienta de Diagnóstico de páginas para SharePoint para analizar las extensiones personalizadas

La herramienta de Diagnóstico de páginas para SharePoint es una extensión de explorador para los nuevos exploradores de Microsoft Edge (https://www.microsoft.com/edge) y Chrome que analiza las páginas del sitio de publicación clásicas y las modernas del portal de SharePoint Online. La herramienta le ofrece un informe para cada página analizada en el que se muestra el rendimiento de la página respecto a un conjunto definido de criterios de rendimiento. Para instalar e informarse de la herramienta Diagnóstico de página de SharePoint, visite [Usar la herramienta Diagnóstico de página para SharePoint Online](page-diagnostics-for-spo.md).

>[!NOTE]
>La herramienta de Diagnóstico de páginas solo funciona para SharePoint Online y no se puede usar en una página del sistema de SharePoint. 

Al analizar una página del sitio de SharePoint con la herramienta de Diagnóstico de páginas para SharePoint, puede ver información sobre las extensiones personalizadas que superan la métrica de la base de referencia en el resultado **Las extensiones afectan al tiempo de carga de la página** o **Demasiadas extensiones utilizadas** en el panel _Pruebas de diagnóstico_. 

Puede encontrarse con los siguientes resultados:

- **Atención necesaria** (en rojo): cualquier extensión _personalizada_ que tarde más de **un** segundo en cargarse. El tiempo de carga total que se muestra en los resultados de la prueba se desglosa por carga de módulos e inicialización. Además, si hay demasiadas extensiones en una página, podrán afectar el tiempo de carga de la página, y esto será más evidente si se usan **siete** o más extensiones en la página.
- **Posibilidades de mejora** (amarillo) Si se usan **cinco** o más extensiones, se mostrarán en esta sección como una advertencia hasta que se utilicen siete o más, lo que se mostrará como Atención necesaria.
- **No es necesario realizar ninguna acción** (en verde): No hay ninguna extensión que tarde más de un segundo en cargarse.

Si una extensión afecta al tiempo de carga de la página o hay demasiadas extensiones en la página, el resultado aparece en la sección **Atención necesaria** de los resultados. Haga clic en el resultado para ver los detalles sobre la extensión que está demorando en cargar o la advertencia sobre la existencia de demasiadas extensiones. Las actualizaciones futuras de la herramienta Diagnóstico de páginas para SharePoint pueden incluir actualizaciones de las reglas de análisis, así que asegúrese de que siempre tiene la versión más reciente de la herramienta.

![Resultados de tiempo de carga de la página](media/page-diagnostics-for-spo/pagediag-extensions-load-time.png)

La información disponible en los resultados incluye lo siguiente:

- **Nombre e identificador** muestra información de identificación que puede ayudarle a encontrar la extensión en la página
- **Total** muestra el tiempo total para que se inicialice y cargue la extensión
- **Carga de módulos** muestra el tiempo que se tarda en recuperar y cargar la extensión
- **Inicialización** muestra el tiempo necesario para que se inicialice la extensión

Se proporciona esta información para que los diseñadores y desarrolladores puedan solucionar problemas. Debe proporcionar esta información a su equipo de diseño y desarrollo.

## <a name="overview-of-extensions"></a>Introducción a las extensiones

Puede usar las Extensiones de SharePoint Framework (SPFx) para ampliar la experiencia de usuario de SharePoint. Con las Extensiones de SharePoint Framework, puede personalizar otros aspectos de la experiencia de SharePoint, como las vistas de datos de lista, las barras de herramientas y las áreas de notificación.

Las extensiones pueden afectar negativamente al rendimiento de una página de SharePoint ya que también necesitan recursos de red y CPU para realizar el trabajo necesario.

Existen cuatro tipos de extensiones:

- **Personalizadores de aplicación** agregan scripts a la página, tienen acceso a marcadores de posición de elementos HTML conocidos y los amplían con representaciones personalizadas.
- **Personalizadores de campo** proporcionan vistas modificadas de los datos para los campos de una lista.
- **Conjuntos de comandos** amplían las superficies de comandos de SharePoint para agregar nuevas acciones y proporcionan código de cliente que puede utilizar para implementar comportamientos.
- **Modificador de consulta de búsqueda (solo vista previa)** se invoca justo antes de ejecutar la consulta de búsqueda.

## <a name="remediate-extension-performance-issues"></a>Corrección de problemas de rendimiento de extensión

Siga las instrucciones de esta sección para identificar y corregir los problemas de rendimiento de las extensiones que se muestran en los resultados **Las extensiones afectan al tiempo de carga de la página**.

>[!NOTE]
>Los personalizadores de la aplicación se pueden ejecutar en la fase temprana del ciclo de vida de una página y pueden influir en el rendimiento de otras extensiones de la misma.

Los resultados de la auditoría en la herramienta de Diagnóstico de páginas mostrarán dos fases de ejecución de una extensión para ayudarle a identificar el potencial impacto en el rendimiento.

- **Carga de módulos** es el tiempo que tarda en cargar la extensión que se ve afectado por el tamaño de la misma, por lo que es una buena idea agrupar solo las bibliotecas necesarias en la extensión y también elegir bibliotecas más ligeras.
- **Inicialización** es el tiempo de inicialización de la extensión. Los desarrolladores de extensiones deben tener en cuenta si la extensión realiza tareas innecesarias o ejecuta demasiados comandos durante la fase de inicialización.

Los autores de páginas también pueden usar el resultado de auditoría para ver si una página tiene demasiadas extensiones ya que pueden afectar negativamente al rendimiento de una página.

- **Tamaño de extensión y dependencias**
  - El uso de la red CDN de Office 365 es necesario para una descarga de recursos estática óptima. Se prefieren los orígenes de la red CDN pública para los archivos _js/css_. Para obtener información sobre cómo usar la CDN de Office 365, vea [Usar la red de entrega de contenido (CDN) de Office 365 con SharePoint Online](use-office-365-cdn-with-spo.md).
  - Reutilice marcos como _importaciones de Fabric_ y _React_ que forman parte de SharePoint Framework (SPFx). Para más información, vea [Información general de SharePoint Framework](https://docs.microsoft.com/sharepoint/dev/spfx/sharepoint-framework-overview).
  - Asegúrese de que está usando la versión más reciente de SharePoint Framework y actualice a las nuevas versiones a medida que estén disponibles.
- **Búsqueda y almacenamiento en caché de datos**
  - Si la extensión se basa en llamadas de servidor adicionales para obtener datos para mostrar, asegúrese de que las API del servidor son rápidas o implementan el almacenamiento en caché del lado cliente (como _localStorage_ o _IndexDB_ para conjuntos más grandes).
  - Si se necesitan varias llamadas para representar datos fundamentales, considere la posibilidad de realizar el procesamiento por lotes en el servidor u otros métodos de consolidación de solicitudes en una sola llamada.
  - Por otra parte, si algunos elementos de datos requieren una API más lenta, pero no son fundamentales para la representación inicial, desacóplelos en una llamada diferente que se ejecuta después de que se representen los datos fundamentales.
  - Si varios elementos usan los mismos datos, utilice una capa de datos común para evitar las llamadas duplicadas.
- **Tiempo de representación**
  - Cualquier fuente multimedia, como imágenes y vídeos, debe tener el tamaño máximo de los límites del contenedor, dispositivo o red, para evitar la descarga de activos de gran tamaño innecesarios. Para obtener información sobre cómo las dependencias de contenido, vea [Usar la red de entrega de contenido (CDN) de Office 365 con SharePoint Online](use-office-365-cdn-with-spo.md).
  - Evite las llamadas a la API que provocan la redistribución, reglas de CSS complejas o animaciones complicadas. Para obtener más información, vea [Minimizar la redistribución del explorador](https://developers.google.com/speed/docs/insights/browser-reflow).
  - Evite usar tareas de larga ejecución encadenadas. En su lugar, divida las tareas de larga ejecución en distintas colas. Para obtener más información, vea [Optimizar la ejecución de JavaScript](https://developers.google.com/web/fundamentals/performance/rendering/optimize-javascript-execution).
  - Reserve el espacio correspondiente para representar de forma asincrónica elementos multimedia u objetos visuales para evitar fotogramas omitidos e interrupciones de flujo.
  - Si un explorador específico no es compatible con una característica que se usa para la representación, cargue un polyfill o excluya la ejecución de un código dependiente. Si la característica no es fundamental, elimine recursos como controladores de eventos para evitar pérdidas de memoria.

Antes de realizar revisiones de página para corregir problemas de rendimiento, anote el tiempo de carga de la página en los resultados del análisis. Ejecute la herramienta de nuevo después de la revisión y compruebe si los nuevos resultados están en línea con su valor de referencia. Luego, compruebe el nuevo tiempo de carga de la página para ver si se ha producido alguna mejora.

![Resultados de tiempo de carga de la página](media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
>El tiempo de carga de la página puede variar en función de varios factores, como la carga de la red, la hora del día y otras condiciones transitorias. Debe probar el tiempo de carga de la página varias veces, antes y después de realizar cambios, para obtener un promedio.

## <a name="related-topics"></a>Temas relacionados

[Ajustar el rendimiento de SharePoint Online](tune-sharepoint-online-performance.md)

[Ajustar el rendimiento de Office 365](tune-office-365-performance.md)

[Rendimiento en la experiencia moderna de SharePoint](https://docs.microsoft.com/sharepoint/modern-experience-performance)

[Redes de entrega de contenido](content-delivery-networks.md)

[Uso de la red de entrega de contenido (CDN) de Office 365 con SharePoint Online](use-office-365-cdn-with-spo.md)
