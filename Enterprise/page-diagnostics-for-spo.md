---
title: Usar la herramienta de diagnóstico de página para SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- SPO160
- MOE150
- BSA160
ms.assetid: dbab2593-dc6a-40f7-adfe-031b9baa620f
description: Use la herramienta diagnósticos de página para SharePoint para analizar las páginas clásicas con los procedimientos recomendados para SharePoint Online.
ms.openlocfilehash: f61d680ab4470429436cd0bb88925c2f1fc63323
ms.sourcegitcommit: 6b4c3a11ef7000480463d43a7a4bc2ced063efce
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2019
ms.locfileid: "35616803"
---
# <a name="use-the-page-diagnostics-tool-for-sharepoint-online"></a>Usar la herramienta de diagnóstico de página para SharePoint Online

En este artículo se describe cómo usar la herramienta de diagnóstico de páginas para analizar las páginas y páginas de publicación clásicas en sitios de grupo clásicos, en un subconjunto de prácticas recomendadas en **SharePoint Online**. 
  
Los sitios de grupo que no tienen habilitada la publicación no pueden hacer uso de las CDN, pero se aplican todas las reglas restantes. La publicación agrega sobrecarga adicional, por lo tanto, no active la publicación solo para obtener la funcionalidad de la red CDN, ya que afectará negativamente a los tiempos de carga de la página.

Tenga en cuenta que se ha **lanzado la 1.05 de, por lo tanto, actualice la extensión si ya está instalada**. Si no está seguro de qué versión tiene, haga clic en el vínculo "acerca de" para comprobarla.
  
> [!IMPORTANT]
> La herramienta de diagnóstico de página no se ejecutará en las bibliotecas de documentos ni en las páginas del sistema, ya que la herramienta está diseñada para revisar páginas de sitio de SharePoint. Una página *AllItems. aspx* es una página del sistema. Si intenta ejecutar la herramienta en una página del sistema, recibirá un mensaje que dice "esta aplicación solo debe ejecutarse en las páginas de SharePoint". <br/> ![Debe ejecutarse en una página de SharePoint](media/34aadfff-1009-496b-9c87-4fc2780e017c.png)<br/>No se trata de un error de la herramienta, ya que no hay ningún valor para evaluar las bibliotecas o las páginas del sistema. Navegue a una página de SharePoint que no sea del sistema para usar la herramienta. Si esto ocurre en una página de SharePoint, Compruebe la página maestra ya que hemos visto a los clientes quitar las metaetiquetas de SharePoint y, a continuación, la página ya no es una página de SharePoint. Si desea enviar comentarios sobre la herramienta, haga clic en la ficha acerca de y siga el [vínculo enviar comentarios](https://go.microsoft.com/fwlink/?linkid=874109). 
  
## <a name="install-the-page-diagnostic-tool"></a>Instalación de la herramienta de diagnóstico de página

> [!IMPORTANT]
> Microsoft no lee los datos o los sitios web que visita, y no captura información personal, ningún sitio web o descarga de información con esta herramienta. La única información que registra la herramienta es el nombre del espacio empresarial, el número de reglas y si se ha utilizado la opción de registro de compatibilidad cuando se ejecuta la herramienta. Esta información es para que Microsoft analice los desafíos que experimentan nuestros clientes y para garantizar que la capacidad de registro de soporte no se esté usando insuficientemente.

1. Con un explorador Chrome, abra el [vínculo a la herramienta](https://chrome.google.com/webstore/detail/inahogkhlkbkjkkaleonemeijihmfagi) directamente o abra la búsqueda en el [Webstore del explorador Chrome](https://chrome.google.com/webstore/search/page%20diagnostics%20for%20sharepoint) e instale la extensión del explorador. Revise la Directiva de privacidad de usuario que se proporciona en la página Descripción de la tienda. Al agregar la herramienta a su explorador, verá los siguientes avisos de permisos.<br/>![Permisos del almacén Chrome](media/e9fbcef0-1171-43ac-8ea8-c2b5be1b7925.png)<br/>   Este aviso está en su lugar porque una página puede incluir contenido de ubicaciones fuera de SharePoint en función de los elementos Web y las personalizaciones de la página. Esto significa que la herramienta leerá las solicitudes y respuestas cuando se haga clic en el botón Inicio y solo para la pestaña de SharePoint activa en la que se está ejecutando la herramienta. La información se captura de forma local mediante el explorador Web y está disponible a través del vínculo exportar a JSON de la herramienta. **Microsoft no envía ni captura la información.** (La herramienta respeta la Directiva de privacidad de Microsoft accesible [aquí](https://go.microsoft.com/fwlink/p/?linkid=857875)).<br/><br/>La función "exportar a JSON" de la herramienta también es la razón por la que se necesita el permiso "administrar las descargas". Siga las propias directrices de privacidad de su empresa antes de compartir el archivo JSON fuera de su organización, ya que los resultados contienen direcciones URL y pueden clasificarse como PII (información de identificación personal).
    
2. (Opcional) Si desea usar la herramienta en el modo de incógnito de Chrome, vaya a la extensión y haga clic en **permitir en incógnito**.
    
3. Navegue a la página de publicación clásica de SharePoint en SharePoint Online que quiera revisar. Hemos permitido la "carga retrasada" de los elementos en las páginas; por lo tanto, la **herramienta no se detiene automáticamente**. Si desea detener la recopilación, puede hacer clic en **detener**. (Por diseño, para satisfacer todos los escenarios de carga de páginas). Antes de hacer clic en **detener**, asegúrese de que los datos de la traza de red están completos. De lo contrario, tendrá un seguimiento parcial. Además, la herramienta es una extensión de explorador y, al abrir varias pestañas o ventanas, solo se puede ejecutar una instancia activa de la herramienta al mismo tiempo. Se trata de una limitación de extensiones en el explorador. 
  
4. Haga clic en el logotipo de la extensión ![Logotipo de Page Diagnostics for SharePoint](media/60a3e44d-1b59-483f-b50f-d580044d921a.png) para cargar la herramienta y se presentará la siguiente ventana emergente de extensiones:<br/> ![Menú emergente herramienta de diagnóstico de página](media/b01fa00e-c5f3-4c37-91f2-6edd096cf87e.png)<br/>Las operaciones de inicio y detención siguen el concepto básico de al hacer clic en iniciar la página se recargará y se iniciará la recopilación.

Lea las siguientes secciones para obtener más información acerca de la información proporcionada en la herramienta.

## <a name="what-youll-see-in-the-page-diagnostics-tool"></a>Lo que verá en la herramienta de diagnóstico de página
    
1. El vínculo **About** proporcionará instrucciones y detalles generales sobre la herramienta, incluido un vínculo de vuelta a este artículo. También incluye un vínculo directo a recomendaciones de rendimiento de SharePoint, un aviso de terceros y una opción para proporcionar comentarios sobre la herramienta. 
    
2. El **identificador de correlación, SPRequestDuration, SPIISLatency**, el **tiempo de carga de página**y los detalles de **dirección URL** son informativos y se pueden usar para algunos fines. 
    
  - **CorrelationID** es un elemento importante cuando trabaja con los equipos de soporte técnico de Microsoft, ya que les permite extraer datos de diagnóstico adicionales. 
    
  - **SPRequestDuration** es la hora del servidor que se toma para procesar la página. Si este tiempo es largo, no significa necesariamente que el servidor funcionaba correctamente, pero también puede reflejar el número de llamadas y la carga que la página presiona en el servidor, por ejemplo, la navegación estructural, las imágenes grandes y muchas llamadas a la API podrían contribuir a un tiempo de servidor más prolongado. . 
    
  - **SPIISLatency** es el tiempo en milisegundos que se toma en el servidor front-end web cuando recibe la solicitud para cargar la página. Se trata de un indicador de latencia para empezar a procesar la página y no incluye el tiempo que tarda la aplicación web en responder. 
    
  - El tiempo de **carga de página** es el tiempo que la página registra desde el momento de la solicitud hasta el momento en que el explorador recibió y leyó la respuesta. El tiempo adicional se ve afectado por el rendimiento del equipo y el tiempo que tarda el explorador en cargarse. 
    
  - La **dirección URL** (Uniform Resource Locator) es la dirección Web de la página actual. 
    
3. La [pestaña **diagnóstico** ](#how-to-use-the-diagnostic-tab) mostrará las reglas y, si alguna de ellas está marcada con una cruz ![](media/9859ac84-be43-4eae-984c-e0e827f5a228.png)roja, se detectarán problemas en la página.<br/>Cada regla tiene su propio vínculo "más información", en el que puede hacer clic si un elemento está en rojo. Esto le llevará a los detalles que hay detrás de la regla y cómo corregir el problema.<br/>![Diagnóstico de regla de red abierta](media/1598f0f7-3103-4613-8787-dfec6fffd40a.png)

4. Una [pestaña de **seguimiento de red** ](#how-to-use-the-network-trace-tab) proporciona detalles sobre las solicitudes y respuestas de compilación de página.

## <a name="how-to-use-the-diagnostic-tab"></a>Cómo usar la pestaña diagnóstico

1. **Comprobar la ejecución como usuario estándar**  Comprobar el rendimiento de la página no debe realizarse cuando se ha iniciado sesión como una cuenta de servicio, administrador o administrador de la colección de sitios, o cualquier cuenta con privilegios elevados. Las secuencias de comandos y la funcionalidad adicionales se cargan específicamente para esos tipos de cuentas, por lo que los resultados no serán una representación real del rendimiento de la página.
    
2. **Comprobar solicitudes a SharePoint**  La cantidad de datos y solicitudes realizados en el servidor debe limitarse, ya que una página sobrecargada experimentará un rendimiento deficiente. Esta comprobación comprueba el número de solicitudes que se realizan a SharePoint y le avisará cuando las solicitudes superen 6 solicitudes. La mayoría de las solicitudes se deben almacenar en caché y, por lo tanto, no llamarlas para cada carga de página. La memoria caché se debe configurar y utilizar durante al menos 15 minutos para reducir la cantidad de llamadas a una página por cada usuario y por cada usuario. Se trata de un problema común y, en la mayoría de los casos, los datos solo cambian diariamente, pero la página comprueba y recupera datos cada vez para cada página de cada usuario que a menudo no es necesario.
    
3. **Comprobar el uso de redes CDN**  Las redes de entrega de contenido (CDN) las proporciona Microsoft y las que se mencionan aquí son las redes de entrega de contenido de SharePoint Online. Hay varios tipos disponibles, así como servicios de red CDN diferentes como redes CDN de SharePoint y, a continuación, CDN en Azure. [Use las siguientes instrucciones](https://go.microsoft.com/fwlink/?linkid=873250).
    
4. **Comprobar tamaños de imagen grandes**  Las imágenes deben optimizarse para Web mediante el uso de tipos de web mejores como PNG. Las representaciones de imágenes también se deben usar y están disponibles directamente en SharePoint. Las representaciones de imágenes de más de 100 KB se resaltarán como no optimizadas para Web. [Use las siguientes instrucciones para optimizar las imágenes](https://go.microsoft.com/fwlink/?linkid=873251).
    
5. **Comprobar la navegación estructural**  La navegación estructural se diseñó originalmente para su uso en SharePoint local donde se podría usar la caché de objetos. La navegación estructural no se recomienda para su uso en SharePoint Online y debe cambiarse a navegación administrada o a un proveedor personalizado. [Use las siguientes instrucciones para optimizar la navegación.](https://go.microsoft.com/fwlink/?linkid=873247)
    
6. **Buscar elemento Web de cbq** (CBQ-contenido por elemento Web de consulta)  El elemento Web de consulta de contenido genera una elevada carga SQL a medida que atraviesa todos los elementos de la consulta para cada carga de páginas, para cada usuario. A diferencia de una instalación local, no hay ninguna memoria caché disponible para limitar el número de consultas necesarias para rellenar este elemento Web. Como tal CBQ tiene un rendimiento lento y afecta a la página general, por lo que no debe usarse. Use el elemento Web de búsqueda de contenido (CSWP) como reemplazo del elemento Web de consulta de contenido. [Use las siguientes instrucciones relacionadas con el elemento Web de búsqueda de contenido](https://go.microsoft.com/fwlink/?linkid=873245).

## <a name="how-to-use-the-network-trace-tab"></a>Uso de la ficha seguimiento de red
    
La pestaña **seguimiento de red** proporciona información detallada sobre las solicitudes para compilar la página, así como las respuestas recibidas. 

1. **Busque los tiempos de carga de los elementos marcados como rojos**. El rendimiento de cada solicitud y respuesta está codificado por color, en función de su impacto en el rendimiento general de la página de la siguiente manera:
- Verde: \< 500ms
- Amarillo: 500 a 1000MD
- Rojo: \> 1000MD
<br/>![Seguimiento de red](media/3cfede99-7d31-4041-888d-7bbc275cadc2.png)<br/> En la imagen mostrada anteriormente, el elemento rojo pertenece a la página predeterminada. Siempre mostrará el color rojo a menos que la página \< se cargue en los 1000MD (menos de 1 segundo).

2. **Probar los tiempos de carga de elementos**. En algunos casos, no habrá ningún indicador de hora ni de color, ya que el explorador ya ha almacenado en caché los elementos. Para probar esto correctamente, abra la página, borre la memoria caché del explorador y, a continuación, haga clic en **iniciar** puesto que forzará una carga de página "fría" y será un reflejo real de la carga de página inicial. Esto se debe comparar con la carga de la página "cálida", ya que también ayudará a determinar qué elementos se almacenan en la página. 
    
3. **Comparta los detalles relevantes con otras personas que puedan ayudar a investigar los problemas**. Para compartir los detalles o la información proporcionada en la herramienta con sus desarrolladores o con un personal de soporte técnico, haga clic en **exportar a JSON** (como se muestra en la imagen anterior). Esto le permitirá descargar los resultados, visibles con un visor de archivos JSON.

> [!IMPORTANT]
> Estos resultados contienen direcciones URL que se pueden clasificar como PII (información de identificación personal). Asegúrese de seguir las instrucciones de la organización antes de distribuir dicha información. 

## <a name="engaging-with-microsoft-support"></a>Participar en el soporte técnico de Microsoft
   
Hemos incluido una **característica de nivel de soporte técnico de Microsoft** que solo debe usarse cuando se trabaja directamente en un caso de soporte técnico para el rendimiento. El uso de esta característica no le proporcionará ningún beneficio cuando se use sin nuestro equipo de soporte técnico. De hecho, el rendimiento de la página será considerablemente menor y el uso continuado de la característica puede considerarse "mal uso" del servicio. No hay información adicional al usar esta característica en la herramienta ya que la información adicional se agrega al registro en el servicio. 

No se ve ningún cambio, excepto que se le notificará que lo ha habilitado y que el rendimiento de la página se degradará significativamente 2-3 veces el rendimiento más lento mientras esté habilitado. Solo será relevante para la página en particular y para esa sesión activa. Por este motivo, debe usarse con moderación y solo cuando participe activamente con nuestro equipo de soporte técnico.

### <a name="to-enable-the-microsoft-support-level-feature"></a>Para habilitar la característica de nivel de soporte técnico de Microsoft

1. Abra la herramienta de diagnóstico de página.
2. En el teclado, presione ALT-MAYÚS-L. Se mostrará **Habilitar registro en el nivel de soporte técnico**. 
3. Active la casilla y, a continuación, haga clic en **iniciar** para volver a cargar la página y generar un registro detallado para que admita el análisis.<br/>![Opción de compatibilidad habilitada](media/ddef47de-8593-4b28-9346-eb48ebf6cdab.png)
  
Un elemento importante para esto es CorrelationID, ya que el equipo de soporte técnico utilizará ese número para extraer la información necesaria. Copie el CorrelationID (en la parte superior de la herramienta de diagnóstico de páginas) y asegúrese de que la compatibilidad con no pueda realizar el trabajo necesario sin el identificador completo.
    
## <a name="related-topics"></a>Temas relacionados

[Ajustar el rendimiento de SharePoint Online](tune-sharepoint-online-performance.md)

[Ajustar el rendimiento de Office 365](tune-office-365-performance.md)

[Redes de entrega de contenido](content-delivery-networks.md)
