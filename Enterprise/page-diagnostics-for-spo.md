---
title: Use la herramienta de diagnóstico de la página de SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/26/2018
ms.audience: Admin
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
description: Use los diagnósticos de página para la herramienta de SharePoint para analizar sus páginas clásicas con las mejores prácticas recomendadas para SharePoint Online.
ms.openlocfilehash: 6bfe26900426b30b9f0ad0746b0c1840e122dc82
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542942"
---
# <a name="use-the-page-diagnostics-tool-for-sharepoint-online"></a>Use la herramienta de diagnóstico de la página de SharePoint Online

En este artículo se describe cómo puede usar la herramienta de diagnóstico de página para analizar sus páginas de publicación clásicas y las páginas de sitios de equipo clásico, frente a un subconjunto de las prácticas recomendadas en **SharePoint Online**. 
  
Los sitios de grupo que no tengan habilitada la publicación no se pueden hacer uso de las CDN pero todas las reglas restantes son aplicables. Publicación agrega sobrecarga adicional, por lo que no activa la publicación sólo para obtener la funcionalidad CDN tal y como lo quedará afectado negativamente tiempos de carga de página.
  
> [!IMPORTANT]
> La herramienta de diagnóstico de la página no se ejecutará con las bibliotecas de documentos o páginas del sistema, como la herramienta está diseñada para revisar las páginas del sitio de SharePoint. Una página *allitems.aspx* es un sistema. Si intenta ejecutar la herramienta en una página del sistema, recibirá un mensaje que lee, "sólo se debe ejecutar esta aplicación en las páginas de SharePoint." > ![debe ejecutar en una página de SharePoint](media/34aadfff-1009-496b-9c87-4fc2780e017c.png)
  
> No es un error en la herramienta como no hay ningún valor en la evaluación de bibliotecas o páginas del sistema. Navegue a una página de SharePoint que no sea de sistema para usar la herramienta. ¿Si desea enviar comentarios acerca de la herramienta por favor, haga clic en la ficha acerca y siga el [ceder el vínculo de comentarios](https://go.microsoft.com/fwlink/?linkid=874109). 
  
## <a name="how-to-use-the-page-diagnostic-tool"></a>Cómo usar la herramienta de diagnóstico de página
<a name="useit"> </a>

1. Mediante un explorador de Chrome, abra directamente el [vínculo a la herramienta](https://chrome.google.com/webstore/detail/inahogkhlkbkjkkaleonemeijihmfagi) o abra la búsqueda en el [Almacén Web del explorador de Chrome](https://chrome.google.com/webstore/search/page%20diagnostics%20for%20sharepoint) e instale la extensión de explorador. 
    
    Revise la directiva de privacidad del usuario proporcionada en la página de descripción en el almacén.
    
    Al agregar la herramienta para el explorador, verá lo siguiente tenga en cuenta los permisos.
    
    ![Permisos del almacén de cromo](media/e9fbcef0-1171-43ac-8ea8-c2b5be1b7925.png)
  
    Este aviso está en su lugar debido a que una página puede contener contenido desde ubicaciones fuera de SharePoint según los elementos Web y las personalizaciones en la página. Esto significa que la herramienta leerá las solicitudes y respuestas cuando se hace clic en el botón Inicio y sólo de la ficha activa de SharePoint donde se ejecuta la herramienta. Esta información se captura localmente por el explorador web y está disponible a través de la exportación al vínculo de JSON en la herramienta. **La información no se envía o capturada por Microsoft.**
    
    > [!IMPORTANT]
    > Microsoft no lee los datos o sitios Web que visite y no se captura cualquier información personal, la información de sitio Web o descargar con esta herramienta. La única información registrada por la herramienta es el nombre del inquilino, count y si se ha usado la opción de compatibilidad con el registro cuando se ejecuta la herramienta de la regla. Esta información es de Microsoft para analizar cuáles son los desafíos que se está produciendo por nuestros clientes y para garantizar que la capacidad de registro de soporte técnico no es un mal uso.
  
La herramienta respeta el Microsoft Privacy directiva accesible [aquí](https://go.microsoft.com/fwlink/p/?linkid=857875). 
  
    The "Export to JSON" functionality in the tool is also why the "Manage your downloads" permission is needed. Please follow your Company's own Privacy guidelines before sharing the JSON file outside of your Company as it contains the URL's and they fall within PII (Personally Identifiable Information).
    
2. (Opcional) Si desea usar la herramienta en modo de incognito de cromo, navegue a la extensión y haga clic en "permitir en incognito".
    
3. Navegue a la página de publicación de SharePoint clásica en SharePoint Online que le gustaría usar para revisar.
    
    > [!IMPORTANT]
    > Nos hemos permitido para "carga retrasada" de elementos en las páginas; por lo tanto, la **herramienta no se detiene automáticamente**. Si desea detener la colección, puede hacer clic en **Detener**. (Esto es por diseño que abarquen para todos los escenarios de carga de página) 
  
Antes de hacer clic en **Detener**, asegúrese de que los datos de seguimiento de red están completas. En caso contrario, tendrá un seguimiento parcial. 
  
Además, la herramienta es una extensión de explorador y apertura de varias fichas o windows solo permitirá una instancia activa de la herramienta para ejecutarse a la vez. Se trata de una limitación de extensiones en el explorador. 
  
4. Haga clic en el logotipo de extensión ![Diagnósticos de página para el logotipo de SharePoint](media/60a3e44d-1b59-483f-b50f-d580044d921a.png) para cargar la herramienta y se presentarán con la siguiente ventana emergente de extensión: 
    
    ![Herramienta de diagnóstico de página de elemento emergente](media/b01fa00e-c5f3-4c37-91f2-6edd096cf87e.png)
  
    Iniciar y detener follow operaciones comenzará el concepto básico de cuando haga clic en Inicio que volverá a cargar la página y la colección.
    
5. El primer vínculo es el vínculo **acerca de** y proporciona instrucciones generales y obtener información detallada acerca de la herramienta que incluye un vínculo a este artículo. También incluye un vínculo directo a las recomendaciones de rendimiento de SharePoint, un aviso de terceros y una opción para proporcionar comentarios sobre la herramienta. 
    
6. Revise la información **identificador de correlación, SPRequestDuration, SPIISLatency** **, hora y dirección URL de carga de página** . (Esta sección es informativa y puede usarse para fines unos). 
    
  - **CorrelationID** es un elemento importante cuando se trabaja con los equipos de soporte técnico de Microsoft, tal como les permite extraer datos de diagnóstico adicionales. 
    
  - **SPRequestDuration** es la hora del servidor necesario para procesar la página. Si este tiempo es larga, no necesariamente significa que el servidor estaba realizando mal, pero también puede reflejar el número de llamadas y cargar inserta por la página en el servidor, por ejemplo, navegación estructural, imágenes de gran tamaño, una gran cantidad de llamadas a la API podría contribuir a más tiempo del servidor . 
    
  - **SPIISLatency** es el tiempo en milisegundos que se llevan a cabo en el servidor Web Front-End cuando se recibe la solicitud para cargar la página. Este es un indicador de latencia para iniciar el procesamiento de la página y no incluye el tiempo necesario para que la aplicación web responder. 
    
  - **Tiempo de carga de página** es el tiempo registrado por la página desde el momento de la solicitud a la hora de la respuesta se ha recibido y leídos por el explorador. Tiempo adicional se ve afectada por el rendimiento del equipo y el tiempo que tarda el explorador cargar. 
    
  - La **dirección URL** (localizador uniforme de recursos) es la dirección web de la página actual. 
    
7. La **ficha diagnóstico** mostrará una lista de las reglas y si cualquiera de ellos están marcados con un color rojo ![entre](media/9859ac84-be43-4eae-984c-e0e827f5a228.png), a continuación, hay problemas identificados en la página.
    
    Cada regla tiene su propio vínculo "más información" Si hace clic en él cuando es de color rojo. Que le llevará a los detalles detrás de esa regla y cómo corregir el problema.
    
    ![Diagnósticos rojo - regla open](media/1598f0f7-3103-4613-8787-dfec6fffd40a.png)
  
1. Comprobar el usuario que ejecute como estándar
  
Comprobar el rendimiento de la página no se debe realizar cuando inicia sesión como una cuenta de servicio, el administrador o el Administrador de colección de sitios, es decir, una cuenta con privilegios elevados. Funcionalidad y secuencias de comandos adicionales se carga específicamente para esos tipos de cuentas y no proporcionará una representación verdadera del rendimiento de la página.
    
2. Solicitudes de verificación para SharePoint
  
Se debe limitar la cantidad de datos y las solicitudes realizadas al servidor como una página sobrecargada experimentará un rendimiento deficiente. Esta comprobación comprueba el número de solicitudes que se realizan en SharePoint y le aconseje cuando las solicitudes de superar los 6 solicitudes. La mayoría de las solicitudes deben se almacena en caché y, por tanto, no se llama para cada carga de página. Memoria caché debe ser el programa de instalación y utilizada durante al menos 15 minutos para reducir la cantidad de llamadas a una página por cada usuario. Éste es un problema común y en la mayoría de los casos sólo cambian los datos diariamente pero la página comprueba y recupera los datos cada vez para cada página para cada usuario que a menudo no es necesario.
    
3. Comprobar el uso de las CDN
  
Redes de distribución de contenido se han proporcionado por Microsoft y a los que hace referencia a que estos son las redes de entrega de contenido en línea SharePoint. Hay varios tipos de, así como los distintos servicios CDN al igual que las CDN de SharePoint y, a continuación, las CDN en Azure. [Use las siguientes instrucciones](https://go.microsoft.com/fwlink/?linkid=873250).
    
4. Verificación de tamaños de imagen grande
  
Imágenes deben ser optimizadas para web mediante el uso de tipos de web mejor como PNG. Representaciones de imágenes también debe utilizarse y está disponibles en SharePoint directamente. Imágenes / representaciones de imágenes mayores que 100kb se marcará como no optimizada para web. [Use las siguientes instrucciones para optimizar el imágenes](https://go.microsoft.com/fwlink/?linkid=873251).
    
5. Protección para la navegación estructural
  
Navegación estructural se diseñó originalmente para su uso en SharePoint local donde se podría utilizar la memoria caché de objetos. Navegación estructural no se recomienda para su uso en SharePoint Online y se debe cambiar a navegación administrada o un proveedor personalizado. [Usar las siguientes instrucciones para optimizar la navegación.](https://go.microsoft.com/fwlink/?linkid=873247)
    
6. Verificación de WebPart CBQ (CBQ - elemento Web consulta de contenido)
  
El elemento Web consulta de contenido genera una alta carga SQL medida que pasa por todos los elementos de la consulta para cada carga de página, para cada usuario. A diferencia de una instalación local, no hay ninguna caché disponible para limitar el número de consultas que sea necesario para rellenar este elemento Web. Como tal, CBQ se ejecuta lentamente y afecta al rendimiento general de la página que es la razón por la que no se debe utilizar. Utilice el elemento Web de búsqueda de contenido (CSWP) como un reemplazo para el elemento Web consulta de contenido. [Use las directrices siguientes relacionadas con el elemento Web de búsqueda de contenido](https://go.microsoft.com/fwlink/?linkid=873245).
    
8. La **ficha seguimiento de red** proporciona *** información detallada acerca de las solicitudes para crear la página, así como las respuestas recibidas. El rendimiento de cada solicitud y respuesta son codificación por colores en función de su impacto en el rendimiento general de la página, es decir, verde \< 500 ms, amarilla 500 ms-1.000 ms y rojo \> 1000ms. 
    
    En esta ficha hay una exportación a opción de JSON si desea descargar y compartir los detalles de solicitud y respuesta.
    
    > [!IMPORTANT]
    > Mantenga el mouse sobre la dirección URL abreviada para ver la dirección URL completa. 
  
    ![Seguimiento de red](media/3cfede99-7d31-4041-888d-7bbc275cadc2.png)
  
    En esta imagen el color rojo es la propia página y que se muestra siempre rojo a menos que la página se carga en \< 1000ms (es decir, de 1 segundo).
    
    En algunos casos, *no habrá ningún indicador de color o de tiempo debido a que los elementos estén ya en caché por el explorador* . Para probar correctamente, abra la página, desactive la memoria caché del explorador y, a continuación, haga clic en **Iniciar** como que va a forzar la carga de una página "pasiva" y ser un reflejo de la carga de página inicial es true. Esto debe, a continuación, compararse a la carga de página "caliente" también le ayudará a determinar qué elementos se que se almacenan en caché en la página. 
    
9. Si desea compartir estos detalles o información con sus desarrolladores o una persona de soporte técnico, a continuación, puede hacer clic en "Exportar a JSON" según la imagen anterior y que descargará los resultados. Tenga en cuenta que el archivo, a continuación, se puede abrir con un visor de archivos JSON.
    
    > [!IMPORTANT]
    > Estos resultados contendrá la dirección de URL y, por tanto, contiene PII (información de identificación personal) y debe seguir las directrices de la compañía antes de distribuir dicha información. 
  
10. Hemos incluido una **característica de nivel de soporte técnico de Microsoft** que sólo se utiliza cuando se trabaja directamente en un caso de soporte técnico para obtener un rendimiento. Uso de esta característica no le proporcionará ninguna ventaja cuando se usa sin nuestro equipo de soporte técnico. De hecho hará que la página realizar mucho más lentamente y puede considerarse uso continuado de la característica de uso "incorrecto" del servicio. No hay ninguna información adicional cuando se utiliza esta característica en la herramienta tal y como se agrega la información adicional para el registro en el servicio. 
    
    Ningún cambio es visible, excepto en que se le notificará que se ha habilitado y se degradará significativamente el rendimiento de la página por 2 - 3 veces un rendimiento más lento mientras que está habilitado. Sólo será relevante para la página determinada y esa sesión activa. Por este motivo, debe usarse con moderación y sólo cuando activamente ocupado con nuestro equipo de soporte técnico.
    
    Para habilitar la característica por favor, abra la herramienta y use ALT-MAYÚS-L que, a continuación, se mostrará "Habilitar el registro de nivel de soporte técnico". Haga clic en que la casilla de verificación y, a continuación, haga clic en inician para volver a cargar la página y generar el registro detallado para soporte técnico analizar.
    
    ![Habilitada la opción de soporte técnico](media/ddef47de-8593-4b28-9346-eb48ebf6cdab.png)
  
    Un elemento importante para esto es el CorrelationID como el equipo de soporte técnico, a continuación, utilizará ese número para extraer la información necesaria. Por favor, copie el CorrelationID y proporcione a soporte técnico al no pueden llevar a cabo el trabajo necesario sin el identificador completo.
    

