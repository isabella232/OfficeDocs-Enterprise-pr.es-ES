---
title: Usar la herramienta de diagnóstico de página para SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 06/03/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
search.appverid:
- MET150
- SPO160
- MOE150
- BSA160
f1.keywords:
- NOCSH
description: Use la herramienta diagnósticos de página para SharePoint para analizar el portal moderno de SharePoint Online y las páginas de publicación clásicas con un conjunto predefinido de criterios de rendimiento.
ms.openlocfilehash: 08bfa6abf0aab4abafaf5fad3a0e43afb9000370
ms.sourcegitcommit: ea2f92f147dbf8183124476302ca33c4cf4265a9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2020
ms.locfileid: "44561809"
---
# <a name="use-the-page-diagnostics-for-sharepoint-tool"></a>Usar la herramienta diagnósticos de página para SharePoint

En este artículo se describe cómo usar la **herramienta diagnósticos de página para SharePoint** para analizar páginas de sitio modernas y clásicas de SharePoint Online con un conjunto predefinido de criterios de rendimiento.

La herramienta diagnósticos de página para SharePoint se puede instalar para:

- **Microsoft Edge** [(extensión perimetral)](https://microsoftedge.microsoft.com/addons/detail/ocemkolpnamjcacndljdfmhlpcaoipji)
- **Chrome** [(extensión Chrome)](https://chrome.google.com/webstore/detail/inahogkhlkbkjkkaleonemeijihmfagi)

>[!TIP]
>La versión **2.0.0** y las versiones posteriores son compatibles con las páginas modernas además de las páginas de sitio clásicas. Si no está seguro de qué versión de la herramienta está usando, puede seleccionar el vínculo **acerca** de o los puntos suspensivos (...) para comprobar la versión. **Actualice siempre a la versión más reciente** cuando use la herramienta.

La herramienta de Diagnóstico de páginas para SharePoint es una extensión de explorador para los nuevos exploradores de Microsoft Edge (https://www.microsoft.com/edge) y Chrome que analiza las páginas del sitio de publicación clásicas y las modernas del portal de SharePoint Online. Esta herramienta solo funciona para SharePoint Online y no se puede usar en una página del sistema de SharePoint.

La herramienta genera un informe para cada página analizada que muestra cómo se ejecuta la página en un conjunto predefinido de reglas y muestra información detallada cuando los resultados de una prueba se encuentran fuera del valor de línea base. Los diseñadores y administradores de SharePoint Online pueden usar la herramienta para solucionar problemas de rendimiento y garantizar que las nuevas páginas se optimizan antes de la publicación.

La herramienta de diagnóstico de página está diseñada únicamente para analizar páginas de sitio de SharePoint, no páginas de sistema como *AllItems. aspx* o *SharePoint. aspx*. Si intenta ejecutar la herramienta en una página del sistema o en cualquier otra página que no sea del sitio, recibirá un mensaje de error que le advierte que la herramienta no se puede ejecutar para ese tipo de página.

![Debe ejecutarse en una página de SharePoint](media/page-diagnostics-for-spo/pagediag-Error-StartPage.png)

No se trata de un error de la herramienta, ya que no hay ningún valor para evaluar las bibliotecas o las páginas del sistema. Navegue a una página del sitio de SharePoint para usar la herramienta. Si este error se produce en una página de SharePoint, Compruebe la página maestra para asegurarse de que las metaetiquetas de SharePoint no se han quitado.

Para proporcionar comentarios sobre la herramienta, seleccione los puntos suspensivos en la esquina superior derecha de la herramienta y, a continuación, seleccione [Enviar comentarios](https://go.microsoft.com/fwlink/?linkid=874109).

![Enviar comentarios](media/page-diagnostics-for-spo/pagediag-feedback.png)
  
## <a name="install-the-page-diagnostics-for-sharepoint-tool"></a>Instalar la herramienta diagnósticos de página para SharePoint

El procedimiento de instalación de esta sección funcionará tanto para los exploradores Chrome como para los de Microsoft Edge.

> [!IMPORTANT]
> Microsoft no lee datos ni contenido de páginas analizados por la herramienta diagnósticos de páginas para SharePoint, y no capturamos información personal, sitio web o información de descarga. La única información identificable que ha iniciado sesión en Microsoft por la herramienta es el nombre del espacio empresarial, el número de reglas que han generado errores y la fecha y la hora en la que se ejecutó la herramienta. Microsoft usa esta información para comprender mejor el portal moderno y la publicación de tendencias de uso de sitios y problemas comunes de rendimiento.

1. Instale la herramienta diagnósticos de página para SharePoint para **Microsoft Edge** [(extensión perimetral)](https://microsoftedge.microsoft.com/addons/detail/ocemkolpnamjcacndljdfmhlpcaoipji) o **Chrome** [(extensión Chrome)](https://chrome.google.com/webstore/detail/inahogkhlkbkjkkaleonemeijihmfagi). Revise la Directiva de privacidad de usuario que se proporciona en la página Descripción de la tienda. Al agregar la herramienta a su explorador, verá los siguientes avisos de permisos.

    ![Permisos de extensión](media/page-diagnostics-for-spo/pagediag-add-to-edge.png)

    Este aviso está en su lugar porque una página puede incluir contenido de ubicaciones fuera de SharePoint en función de los elementos Web y las personalizaciones de la página. Esto significa que la herramienta leerá las solicitudes y respuestas cuando se haga clic en el botón Inicio y solo para la pestaña de SharePoint activa en la que se está ejecutando la herramienta. Esta información se captura de forma local mediante el explorador Web y está disponible a través del botón **exportar a JSON** o **exportar a har** en la ficha _seguimiento de red_ de la herramienta. **la información no es enviada o capturada por Microsoft.** (La herramienta respeta la Directiva de privacidad de Microsoft accesible [aquí](https://go.microsoft.com/fwlink/p/?linkid=857875)).

    El permiso _administrar las descargas_ cubre el uso de la herramienta **exportar a** la funcionalidad JSON. Siga las propias directrices de privacidad de su empresa antes de compartir el archivo JSON fuera de su organización, ya que los resultados contienen direcciones URL y pueden clasificarse como PII (información de identificación personal).
1. Si desea usar la herramienta en el modo incógnito o InPrivate, siga el procedimiento del explorador:
    1. En Microsoft Edge, vaya a **extensiones** o escriba _Edge://Extensions_ en la barra de direcciones URL y seleccione los **detalles** de la extensión. En la configuración de la extensión, marque la casilla **permitir en InPrivate**.
    1. En Chrome, vaya a **extensiones** o escriba _Chrome://Extensions_ en la barra de direcciones URL y seleccione **detalles** para la extensión. En la configuración de la extensión, seleccione el control deslizante para **permitir en incógnito**.
1. Vaya a la página del sitio de SharePoint en SharePoint Online que quiera revisar. Hemos permitido la "carga retrasada" de los elementos en las páginas; por lo tanto, la herramienta no se detendrá automáticamente (esto es por diseño para acomodar todos los escenarios de carga de páginas). Para detener la recolección, seleccione **detener**. Asegúrese de que la carga de página se ha completado antes de detener la recopilación de datos o de que solo se Capture un seguimiento parcial.
1. Haga clic en el botón de la barra de herramientas de la extensión ![Logotipo de Page Diagnostics for SharePoint](media/page-diagnostics-for-spo/pagediag-icon32.png) para cargar la herramienta y se presentará la siguiente ventana emergente de extensiones:

    ![Menú emergente herramienta de diagnóstico de página](media/page-diagnostics-for-spo/pagediag-Landing.png)

Seleccione **Inicio** para empezar a recopilar datos para el análisis.

## <a name="what-youll-see-in-the-page-diagnostics-for-sharepoint-tool"></a>Lo que verá en la herramienta diagnósticos de página para SharePoint

1. Haga clic en los puntos suspensivos (...) en la esquina superior derecha de la herramienta para buscar los siguientes vínculos:
   1. El vínculo **recursos adicionales** proporciona instrucciones y detalles generales sobre la herramienta, incluido un vínculo de vuelta a este artículo.
   1. El vínculo **proporcionar comentarios** proporciona un vínculo al sitio de _voz de usuarios de colaboración y sitios de SharePoint_ .
   1. El vínculo **acerca** de incluye la versión instalada actualmente de la herramienta y un vínculo directo al aviso de terceros de la herramienta.  
1. El **identificador de correlación, SPRequestDuration, SPIISLatency**, el **tiempo de carga de página**y los detalles de **dirección URL** son informativos y se pueden usar para algunos fines.

    ![Detalles de diagnósticos de página](media/page-diagnostics-for-spo/pagediag-details.PNG)

   - **CorrelationID** es un elemento importante al trabajar con el soporte técnico de Microsoft, ya que les permite recopilar datos de diagnóstico adicionales para la página específica.
   - **SPRequestDuration** es el tiempo que tarda SharePoint en procesar la página. La navegación estructural, las imágenes grandes y muchas llamadas a la API pueden contribuir a duraciones más largas.
   - **SPIISLatency** es el tiempo en milisegundos que tardó SharePoint Online en cargar la página. Este valor no incluye el tiempo que tarda la aplicación web en responder.
   - El **tiempo de carga de página** es el tiempo total registrado por la página desde el momento de la solicitud hasta el momento en que se recibió y se representó la respuesta en el explorador. Este valor se ve afectado por diversos factores, como la latencia de red, el rendimiento del equipo y el tiempo que tarda el explorador en cargar la página.
   - La dirección URL de la **Página** (localizador de recursos universal) es la dirección Web de la página actual.

1. La pestaña [**pruebas de diagnóstico**](#how-to-use-the-diagnostic-tests-tab) muestra los resultados del análisis en tres categorías; **No es necesario realizar ninguna acción**, las **oportunidades de mejora** y la **atención**. Cada resultado de la prueba está representado por un elemento en una de estas categorías, tal como se describe en la tabla siguiente:

    |Categoría  |Color  |Description  |
    |---------|---------|---------|
    |**Atención necesaria** |Rojo |El resultado de la prueba está fuera del valor de línea base y afecta al rendimiento de la página. Siga las instrucciones de corrección.|
    |**Oportunidades de mejora** |Amarillo |El resultado de la prueba está fuera del valor de línea base y podría contribuir a problemas de rendimiento. Se pueden aplicar criterios específicos de la prueba.|
    |**No se requiere ninguna acción.** |Verde |El resultado de la prueba está dentro del valor de línea base de la prueba.|

    ![Diagnósticos de página](media/page-diagnostics-for-spo/pagediag-results-general.PNG)

1. Una pestaña de [**seguimiento de red**](#how-to-use-the-network-trace-tab) proporciona detalles sobre las solicitudes y respuestas de compilación de página.

## <a name="how-to-use-the-diagnostic-tests-tab"></a>Cómo usar la pestaña pruebas de diagnóstico

Al analizar una página de portal moderna de SharePoint o una página de sitio de publicación clásica con la herramienta diagnósticos de página para SharePoint, los resultados se analizan mediante reglas predefinidas que comparan los resultados con los valores de línea base y se muestran en la ficha **pruebas de diagnóstico** . las reglas de algunas pruebas pueden usar diferentes valores de línea base para portales modernos y sitios de publicación

Los resultados de las pruebas que aparecen en las categorías de **oportunidades de mejora** o **atención necesaria** indican las áreas que deben revisarse en función de las prácticas recomendadas y se pueden seleccionar para mostrar información adicional sobre el resultado. Los detalles de cada elemento incluyen un vínculo _obtener más información_ que le lleva directamente a las instrucciones adecuadas relacionadas con la prueba. Los resultados de las pruebas que aparecen en la categoría **no se requiere ninguna acción** indican la conformidad con la regla relevante y no muestran detalles adicionales cuando se seleccionan.

La información de la pestaña pruebas de diagnóstico no le dirá cómo diseñar páginas, pero resaltará factores que pueden afectar al rendimiento de la página. Algunas funciones y personalizaciones de página tienen un impacto inevitable en el rendimiento de la página y deben revisarse para detectar posibles correcciones o omisiones en la página si su impacto es considerable.

Los resultados rojos o amarillos también pueden indicar elementos Web que actualizan datos con demasiada frecuencia. Por ejemplo, las noticias corporativas no se actualizan cada segundo, pero los elementos Web personalizados a menudo se crean para obtener las últimas noticias cada segundo en lugar de implementar los elementos de almacenamiento en caché que podrían mejorar la experiencia general del usuario. Tenga en cuenta que, al incluir elementos Web en una página, a menudo hay formas sencillas de reducir el impacto en el rendimiento mediante la evaluación del valor de cada parámetro disponible para asegurarse de que está configurado correctamente para el propósito previsto.

>[!NOTE]
>Los sitios de grupo clásicos que no tienen habilitada la característica de publicación no pueden hacer uso de CDN. Cuando se ejecuta la herramienta en estos sitios, se espera que se produzca un error en la prueba de la red CDN y se puede omitir, pero se aplican todas las pruebas restantes. La funcionalidad adicional de la característica de publicación de SharePoint puede aumentar el tiempo de carga de la página, por lo que no debe habilitarse solo para permitir la funcionalidad de la red CDN.

>[!IMPORTANT]
>Las reglas de prueba se agregan y se actualizan con regularidad, por lo que consulte la versión más reciente de la herramienta para obtener información detallada sobre las reglas actuales y la información específica incluida en los resultados de las pruebas. Puede comprobar la versión mediante la administración de las extensiones y la extensión le avisará si hay una actualización disponible.

## <a name="how-to-use-the-network-trace-tab"></a>Uso de la ficha seguimiento de red

La pestaña **seguimiento de red** proporciona información detallada sobre ambas solicitudes para crear la página y las respuestas recibidas desde SharePoint.

1. **Busque los tiempos de carga de los elementos marcados como rojos**. Cada solicitud y respuesta se codifica por colores para indicar su impacto en el rendimiento general de la página mediante las siguientes métricas de latencia:
    - Verde: \< 500ms
    - Amarillo: 500 a 1000MD
    - Rojo: \> 1000MD

    ![Seguimiento de red](media/page-diagnostics-for-spo/pagediag-networktrace-red.png)

    En la imagen mostrada anteriormente, el elemento rojo pertenece a la página predeterminada. Siempre mostrará el color rojo a menos que la página se cargue en los \< 1000MD (menos de 1 segundo).

2. **Probar los tiempos de carga de elementos**. En algunos casos, no habrá ningún indicador de hora ni de color, ya que el explorador ya ha almacenado en caché los elementos. Para probar esto correctamente, abra la página, borre la memoria caché del explorador y, a continuación, haga clic en **iniciar** puesto que forzará una carga de página "fría" y será un reflejo real de la carga de página inicial. Esto se debe comparar con la carga de la página "cálida", ya que también ayudará a determinar qué elementos se almacenan en la página.

3. **Comparta los detalles relevantes con otras personas que puedan ayudar a investigar los problemas**. Para compartir los detalles o la información proporcionada en la herramienta con sus desarrolladores o con un personal de soporte técnico, haga clic en **exportar a JSON** (como se muestra en la imagen anterior). Esto le permitirá descargar los resultados, visibles con un visor de archivos JSON.

    Si ha optado por usar la función de vista previa *Habilitar exportación a har* , el tipo de exportación se mostrará como **Export to har**.

    ![Seguimiento de red](media/page-diagnostics-for-spo/pagediag-NetworkTraceHAR.PNG)

> [!IMPORTANT]
> Estos resultados contienen direcciones URL que se pueden clasificar como PII (información de identificación personal). Asegúrese de seguir las instrucciones de la organización antes de distribuir dicha información.

## <a name="engaging-with-microsoft-support"></a>Participar en el soporte técnico de Microsoft

Hemos incluido una **característica de nivel de soporte técnico de Microsoft** que solo debe usarse cuando se trabaja directamente en un caso de soporte técnico. El uso de esta característica no le proporcionará ningún beneficio cuando se use sin la participación en el equipo y puede hacer que la página se realice de manera considerablemente más lenta. No hay información adicional al usar esta característica en la herramienta ya que la información adicional se agrega al registro en el servicio.

No se ve ningún cambio, excepto que se le notificará que lo ha habilitado y que el rendimiento de la página se degradará significativamente 2-3 veces el rendimiento es más lento mientras está habilitado. Solo será relevante para la página en particular y para esa sesión activa. Por este motivo, debe usarse con moderación y solo cuando se contrata activamente con soporte técnico.

### <a name="to-enable-the-microsoft-support-level-feature"></a>Para habilitar la característica de nivel de soporte técnico de Microsoft

1. Abra la herramienta diagnósticos de página para SharePoint.
2. En el teclado, presione **Alt-Mayús-L**. Se mostrará la casilla de verificación **Habilitar registro de compatibilidad** .
3. Active la casilla y, a continuación, haga clic en **iniciar** para volver a cargar la página y generar un registro detallado.

    ![Opción de compatibilidad habilitada](media/page-diagnostics-for-spo/pagediag-support.png)
  
    Debe tener en cuenta la CorrelationID (que se muestra en la parte superior de la herramienta) y proporcionarla a su representante de soporte técnico para que pueda recopilar información adicional sobre la sesión de diagnóstico.

## <a name="related-topics"></a>Temas relacionados

[Ajustar el rendimiento de SharePoint Online](tune-sharepoint-online-performance.md)

[Ajustar el rendimiento de Office 365](tune-office-365-performance.md)

[Rendimiento en la experiencia moderna de SharePoint](https://docs.microsoft.com/sharepoint/modern-experience-performance)

[Redes de entrega de contenido](content-delivery-networks.md)

[Uso de la red de entrega de contenido (CDN) de Office 365 con SharePoint Online](use-office-365-cdn-with-spo.md)
