---
title: Use la herramienta de diagnóstico de la página de SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
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
ms.openlocfilehash: fb5bb9a333a3b04acfe3d014952eb6406f7dbe31
ms.sourcegitcommit: 0466a88133a42e2db4245f972cecb371721c9b5d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "23849363"
---
# <a name="use-the-page-diagnostics-tool-for-sharepoint-online"></a>Use la herramienta de diagnóstico de la página de SharePoint Online

En este artículo se describe cómo puede usar la herramienta de diagnóstico de página para analizar sus páginas de publicación clásicas y las páginas de sitios de equipo clásico, frente a un subconjunto de las prácticas recomendadas en **SharePoint Online**. 
  
Los sitios de grupo que no tengan habilitada la publicación no se pueden hacer uso de las CDN pero todas las reglas restantes son aplicables. Publicación agrega sobrecarga adicional, por lo que no activa la publicación sólo para obtener la funcionalidad CDN tal y como lo quedará afectado negativamente tiempos de carga de página.
  
> [!IMPORTANT]
> La herramienta de diagnóstico de la página no se ejecutará con las bibliotecas de documentos o páginas del sistema, como la herramienta está diseñada para revisar las páginas del sitio de SharePoint. Una página *allitems.aspx* es un sistema. Si intenta ejecutar la herramienta en una página del sistema, recibirá un mensaje que lee, "esta aplicación sólo se debe ejecutar en las páginas de SharePoint."</br> ![Debe ejecutar en una página de SharePoint](media/34aadfff-1009-496b-9c87-4fc2780e017c.png)</br>No es un error en la herramienta como no hay ningún valor en la evaluación de bibliotecas o páginas del sistema. Navegue a una página de SharePoint que no sea de sistema para usar la herramienta. ¿Si desea enviar comentarios acerca de la herramienta por favor, haga clic en la ficha acerca y siga el [ceder el vínculo de comentarios](https://go.microsoft.com/fwlink/?linkid=874109). 
  
## <a name="install-the-page-diagnostic-tool"></a>Instalar la herramienta de diagnóstico de página

> [!IMPORTANT]
> Microsoft no lee los datos o sitios Web que visite y no se captura cualquier información personal, la información de sitio Web o descargar con esta herramienta. La única información registrada por la herramienta es el nombre del inquilino, count y si se ha usado la opción de compatibilidad con el registro cuando se ejecuta la herramienta de la regla. Esta información es de Microsoft para analizar cuáles son los desafíos que se está produciendo por nuestros clientes y para garantizar que la capacidad de registro de soporte técnico no es un mal uso.

1. Mediante un explorador de Chrome, abra directamente el [vínculo a la herramienta](https://chrome.google.com/webstore/detail/inahogkhlkbkjkkaleonemeijihmfagi) o abra la búsqueda en el [Almacén Web del explorador de Chrome](https://chrome.google.com/webstore/search/page%20diagnostics%20for%20sharepoint) e instale la extensión de explorador. Revise la directiva de privacidad del usuario proporcionada en la página de descripción en el almacén. Al agregar la herramienta para el explorador, verá lo siguiente tenga en cuenta los permisos.</br>![Permisos del almacén de cromo](media/e9fbcef0-1171-43ac-8ea8-c2b5be1b7925.png)</br>   Este aviso está en su lugar debido a que una página puede contener contenido desde ubicaciones fuera de SharePoint según los elementos Web y las personalizaciones en la página. Esto significa que la herramienta leerá las solicitudes y respuestas cuando se hace clic en el botón Inicio y sólo de la ficha activa de SharePoint donde se ejecuta la herramienta. Esta información se captura localmente por el explorador web y está disponible a través de la exportación al vínculo de JSON en la herramienta. **La información no se envía o capturada por Microsoft.** (La herramienta respeta el Microsoft Privacy directiva accesible [aquí](https://go.microsoft.com/fwlink/p/?linkid=857875).)</br></br>La funcionalidad "Exportar a JSON" en la herramienta también es ¿por qué se necesita el permiso "Administrar sus descargas". Siga las directrices de privacidad de la compañía antes de compartir el archivo JSON fuera de la organización, como los resultados contienen direcciones URL y se puede clasificar como PII (información de identificación personal).
    
2. (Esto es opcional) Si desea usar la herramienta en modo de incognito de cromo, navegue a la extensión y haga clic en **Permitir en incognito**.
    
3. Navegue a la página de publicación de SharePoint clásica en SharePoint Online que le gustaría usar para revisar. Nos hemos permitido para "carga retrasada" de elementos en las páginas; por lo tanto, la **herramienta no se detiene automáticamente**. Si desea detener la colección, puede hacer clic en **Detener**. (Esto es por diseño que abarquen para todos los escenarios de carga de página). Antes de hacer clic en **Detener**, asegúrese de que los datos de seguimiento de red están completas. En caso contrario, tendrá un seguimiento parcial. Además, la herramienta es una extensión de explorador y apertura de varias fichas o windows solo permitirá una instancia activa de la herramienta para ejecutarse a la vez. Se trata de una limitación de extensiones en el explorador. 
  
4. Haga clic en el logotipo de extensión ![Diagnósticos de página para el logotipo de SharePoint](media/60a3e44d-1b59-483f-b50f-d580044d921a.png) para cargar la herramienta y se presentarán con la siguiente ventana emergente de extensión:</br> ![Herramienta de diagnóstico de página de elemento emergente](media/b01fa00e-c5f3-4c37-91f2-6edd096cf87e.png)</br>Iniciar y detener follow operaciones comenzará el concepto básico de cuando haga clic en Inicio que volverá a cargar la página y la colección.

Lea las secciones siguientes para obtener más información acerca de la información proporcionada en la herramienta.

## <a name="what-youll-see-in-the-page-diagnostics-tool"></a>Lo que verá en la herramienta de diagnóstico de página
    
1. El vínculo **sobre** proporciona instrucciones generales y obtener información detallada acerca de la herramienta que incluye un vínculo a este artículo. También incluye un vínculo directo a las recomendaciones de rendimiento de SharePoint, un aviso de terceros y una opción para proporcionar comentarios sobre la herramienta. 
    
2. Los detalles del **identificador de correlación, SPRequestDuration, SPIISLatency**, **tiempo de carga de página**y **dirección URL** son informativos y pueden usarse para fines unos. 
    
  - **CorrelationID** es un elemento importante cuando se trabaja con los equipos de soporte técnico de Microsoft, tal como les permite extraer datos de diagnóstico adicionales. 
    
  - **SPRequestDuration** es la hora del servidor necesario para procesar la página. Si este tiempo es larga, no necesariamente significa que el servidor estaba realizando mal, pero también puede reflejar el número de llamadas y cargar inserta por la página en el servidor, por ejemplo, navegación estructural, imágenes de gran tamaño, una gran cantidad de llamadas a la API podría contribuir a más tiempo del servidor . 
    
  - **SPIISLatency** es el tiempo en milisegundos que se llevan a cabo en el servidor Web Front-End cuando se recibe la solicitud para cargar la página. Este es un indicador de latencia para iniciar el procesamiento de la página y no incluye el tiempo necesario para que la aplicación web responder. 
    
  - **Tiempo de carga de página** es el tiempo registrado por la página desde el momento de la solicitud a la hora de la respuesta se ha recibido y leídos por el explorador. Tiempo adicional se ve afectada por el rendimiento del equipo y el tiempo que tarda el explorador cargar. 
    
  - La **dirección URL** (localizador uniforme de recursos) es la dirección web de la página actual. 
    
3. La [ficha **diagnóstico** ](#how-to-use-the-diagnostic-tab) mostrará una lista de las reglas y si cualquiera de ellos están marcados con un color rojo ![entre](media/9859ac84-be43-4eae-984c-e0e827f5a228.png), a continuación, hay problemas identificados en la página.</br>Cada regla tiene su propio vínculo "más información" que haga clic en si un elemento es rojo. Que le llevará a los detalles detrás de esa regla y cómo corregir el problema.</br>![Diagnósticos rojo - regla open](media/1598f0f7-3103-4613-8787-dfec6fffd40a.png)

4. Una [ficha de **seguimiento de red** ](#how-to-use-the-network-trace-tab) proporciona detalles acerca de la página generación las solicitudes y respuestas.

## <a name="how-to-use-the-diagnostic-tab"></a>Cómo usar la ficha diagnóstico

1. **Comprobar está ejecutando como usuario estándar**  Comprobar el rendimiento de la página no se debe realizar cuando inicia sesión como una cuenta de servicio, administrador o administrador de colección de sitios o cualquier cuenta con privilegios elevados. Funcionalidad y secuencias de comandos adicionales se cargan específicamente para esos tipos de cuentas, por lo que los resultados no será una representación verdadera del rendimiento de la página.
    
2. **Comprobar las solicitudes de SharePoint**  Se debe limitar la cantidad de datos y las solicitudes realizadas al servidor como una página sobrecargada experimentará un rendimiento deficiente. Esta comprobación comprueba el número de solicitudes que se realizan en SharePoint y le aconseje cuando las solicitudes de superar los 6 solicitudes. La mayoría de las solicitudes deben se almacena en caché y, por tanto, no se llama para cada carga de página. Memoria caché debe ser el programa de instalación y utilizada durante al menos 15 minutos para reducir la cantidad de llamadas a una página por cada usuario. Éste es un problema común y en la mayoría de los casos sólo cambian los datos diariamente pero la página comprueba y recupera los datos cada vez para cada página para cada usuario que a menudo no es necesario.
    
3. **Comprobar el uso de las CDN**  Redes de distribución de contenido (CDN) se han proporcionado por Microsoft y a los que hace referencia a que estos son las redes de entrega de contenido en línea SharePoint. Hay varios tipos de, así como los distintos servicios CDN al igual que las CDN de SharePoint y, a continuación, las CDN en Azure. [Use las siguientes instrucciones](https://go.microsoft.com/fwlink/?linkid=873250).
    
4. **Compruebe si los tamaños de imagen grande**  Imágenes deben ser optimizadas para web mediante el uso de tipos de web mejor como PNG. Representaciones de imágenes también debe utilizarse y está disponibles en SharePoint directamente. Imágenes / representaciones de imágenes mayores que 100kb se marcará como no optimizada para web. [Use las siguientes instrucciones para optimizar el imágenes](https://go.microsoft.com/fwlink/?linkid=873251).
    
5. **Comprobar para la navegación estructural**  Navegación estructural se diseñó originalmente para su uso en SharePoint local donde se podría utilizar la memoria caché de objetos. Navegación estructural no se recomienda para su uso en SharePoint Online y se debe cambiar a navegación administrada o un proveedor personalizado. [Usar las siguientes instrucciones para optimizar la navegación.](https://go.microsoft.com/fwlink/?linkid=873247)
    
6. **Compruebe si CBQ WebPart** (CBQ - elemento Web consulta de contenido)  El elemento Web consulta de contenido genera una alta carga SQL medida que pasa por todos los elementos de la consulta para cada carga de página, para cada usuario. A diferencia de una instalación local, no hay ninguna caché disponible para limitar el número de consultas que sea necesario para rellenar este elemento Web. Como tal, CBQ se ejecuta lentamente y afecta al rendimiento general de la página que es la razón por la que no se debe utilizar. Utilice el elemento Web de búsqueda de contenido (CSWP) como un reemplazo para el elemento Web consulta de contenido. [Use las directrices siguientes relacionadas con el elemento Web de búsqueda de contenido](https://go.microsoft.com/fwlink/?linkid=873245).

## <a name="how-to-use-the-network-trace-tab"></a>Cómo usar la ficha seguimiento de red
    
La ficha **Seguimiento de red** proporciona información detallada sobre las solicitudes para crear la página, así como las respuestas recibidas. 

1. **Busque los tiempos de carga de elemento marcados como en rojo**. El rendimiento de cada solicitud y respuesta tienen colores diferentes, según su impacto en el rendimiento general de la página de la siguiente manera:
- Verde: \< 500 ms
- Amarillo: 500 ms-1.000 ms
- Rojo: \> 1000ms
</br>![Seguimiento de red](media/3cfede99-7d31-4041-888d-7bbc275cadc2.png)</br>En la imagen que se muestra anteriormente, el elemento rojo pertenece a la página predeterminada. Siempre mostrará rojo a menos que la página se carga en \< 1000ms (menos de 1 segundo).

2. **Tiempos de carga de elemento de prueba**. En algunos casos no habrá ningún indicador de color o de tiempo debido a que los elementos estén ya en caché por el explorador. Para probar correctamente, abra la página, desactive la memoria caché del explorador y, a continuación, haga clic en **Iniciar** como que va a forzar la carga de una página "pasiva" y ser un reflejo de la carga de página inicial es true. Esto debe, a continuación, compararse a la carga de página "caliente" también le ayudará a determinar qué elementos se que se almacenan en caché en la página. 
    
3. **Detalles pertinentes de compartir con otros usuarios que pueden ayudar a investigar los problemas**. Para compartir los detalles o la información proporcionada en la herramienta con sus desarrolladores o una persona de soporte técnico, haga clic en **Exportar a JSON** (tal como se muestra en la imagen anterior). Que le permitirá descargar los resultados, pueden verse con un visor de archivos JSON.

> [!IMPORTANT]
> Estos resultados contienen direcciones URL y que se pueden clasificar como PII (información de identificación personal). Asegúrese de seguir las instrucciones de su organización antes de distribuir dicha información. 

## <a name="engaging-with-microsoft-support"></a>Trabajar con el soporte técnico de Microsoft
   
Hemos incluido una **característica de nivel de soporte técnico de Microsoft** que sólo se utiliza cuando se trabaja directamente en un caso de soporte técnico para obtener un rendimiento. Uso de esta característica no le proporcionará ninguna ventaja cuando se usa sin nuestro equipo de soporte técnico. De hecho hará que la página realizar mucho más lentamente y puede considerarse uso continuado de la característica de uso "incorrecto" del servicio. No hay ninguna información adicional cuando se utiliza esta característica en la herramienta tal y como se agrega la información adicional para el registro en el servicio. 

Ningún cambio es visible, excepto en que se le notificará que se ha habilitado y se degradará significativamente el rendimiento de la página por 2 - 3 veces un rendimiento más lento mientras que está habilitado. Sólo será relevante para la página determinada y esa sesión activa. Por este motivo, debe usarse con moderación y sólo cuando activamente ocupado con nuestro equipo de soporte técnico.

### <a name="to-enable-the-microsoft-support-level-feature"></a>Para habilitar la característica de nivel de soporte técnico de Microsoft

1. Abra la herramienta de diagnóstico de la página.
2. En el teclado, presione ALT-MAYÚS-L. Esto mostrará **Habilitar el registro de nivel de soporte técnico**. 
3. Seleccione la casilla de verificación y, a continuación, haga clic en **Iniciar** para volver a cargar la página y generar el registro detallado de soporte técnico analizar.</br>![Habilitada la opción de soporte técnico](media/ddef47de-8593-4b28-9346-eb48ebf6cdab.png)
  
Un elemento importante para esto es el CorrelationID como el equipo de soporte técnico, a continuación, utilizará ese número para extraer la información necesaria. Por favor, copie el CorrelationID (en la parte superior de la herramienta de diagnóstico de página) y proporcione a soporte técnico al no pueden llevar a cabo el trabajo necesario sin el identificador completo.
    
## <a name="related-topics"></a>Temas relacionados

[Ajustar el rendimiento de SharePoint Online](tune-sharepoint-online-performance.md)

[Ajustar el rendimiento de Office 365](tune-office-365-performance.md)

[Redes de entrega de contenido](content-delivery-networks.md)
