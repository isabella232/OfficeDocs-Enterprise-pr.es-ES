---
title: Opciones de migración de SharePoint 2007 a tener en cuenta
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- SPS150
- OSU140
- SPO160
- SPB160
- OSI150
- OSI160
- BSA160
- OSU160
ms.assetid: 66325a43-5816-4f8e-81ba-c11b71345b7c
description: SharePoint Server 2007 ha alcanzado el final del soporte técnico y es el momento de la actualización. Use este artículo para ayudarle a crear el plan.
ms.openlocfilehash: 4395bc330efd97ae8865e0fb75f93f04fd162ecd
ms.sourcegitcommit: a9c84d02e94c99ff6b1099b4a9ae695be08210e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/25/2018
ms.locfileid: "21169882"
---
# <a name="sharepoint-2007-migration-options-to-consider"></a>Opciones de migración de SharePoint 2007 a tener en cuenta

Microsoft SharePoint 2007 y SharePoint Server 2007 han alcanzado el final del soporte técnico. ¡Es el momento de actualizar! En este artículo se proporciona información acerca de las opciones de migración.
  
## <a name="common-upgrade-strategies-for-sharepoint"></a>Estrategias de actualización comunes de SharePoint

Existen varios métodos para actualizar un entorno de SharePoint Server. Si tiene una granja de servidores de Microsoft Office SharePoint Server 2007, estos son algunos ejemplos de los métodos de actualización:
  
- Base de datos adjunta
    
- Actualización en paralelo
    
- Actualización en contexto
    
- Actualización híbrida (en contexto con bases de datos separadas / independiente base de datos adjunta)
    
- Híbridos de SharePoint (en línea conectarse a SharePoint local)
    
- Mover manualmente los datos entre colecciones de sitios o bibliotecas
    
- Asistente de FastTrack para actualizar a Office 365 ([Asesor de implementación de SharePoint Online](https://aka.ms/spoguidance))
    
- API de migración a SharePoint Online (SPO) en Office 365
    
¿Qué funciona mejor para usted?
  
El conocimiento de lo que hace y se usa para la granja de servidores es una fortaleza táctica lo que respecta al actualizar. La forma de utilizar la granja de servidores de SharePoint le ayudará a elegir entre las opciones.
  
> [!TIP]
> Microsoft Office SharePoint Server 2007 también dispone de una actualización gradual, que no se incluyen aquí. Para ver una lista de actualizaciones específicas del paso artículos vea el [final de SharePoint Server 2007 de admitir guía básica](sharepoint-2007-end-of-support.md). 
  
No olvide comprobar el [Ciclo de vida del producto](https://support.microsoft.com/en-us/lifecycle/search) y los requisitos del sistema para cualquier versión de SharePoint que se está actualizando a. Esto es por lo que se podrá tener en cuenta cuando la próxima actualización será necesaria (por ejemplo, si hace una pausa en un producto heredado, como SharePoint Server 2010 para planear las actualizaciones más, debe asegurarse de conocer su final de la fecha de soporte) y que se asegure de que dispone de hardware que es compatible con el plan. 
  
Si va a realizar la transición de algunos o todos los sitios de SharePoint para Office 365 en la nube, este es un momento para marcar un vínculo a las [Descripciones del servicio de Office 365](https://technet.microsoft.com/en-us/library/office-365-service-descriptions.aspx). Necesitará las descripciones de servicio para obtener más información acerca de las características de SharePoint Online y cómo es posible que difieren del local de SharePoint Server. Actualización de granjas de servidores de Microsoft Office SharePoint Server 2007 funcionales. Si la instalación tiene sitios que están rotos, corregirlos antes de la actualización.
  
## <a name="a-note-about-managing-risk"></a>Una nota sobre la administración de riesgos

Métodos como 'side-by-side' son importantes en la combinación de lógica de actualización. Cuando se actualiza en paralelo, mantener la granja de servidores de Microsoft Office SharePoint Server 2007, pero generar una granja de servidores de la siguiente versión de él (SharePoint Server 2010) en hardware nuevo. Esto ayuda a de tres maneras:
  
1. Tener un lugar para realizar copias de seguridad de las bases de datos de Microsoft Office SharePoint Server 2007 para actualizarlas por separado, mediante el uso de la base de datos adjunta.
    
2. Si se calcula que sólo un pequeño número de bibliotecas de documentos críticos y otra información están en uso en la granja de servidores de Microsoft Office SharePoint Server 2007, puede elegir mover manualmente los datos de Microsoft Office SharePoint Server 2007 a SharePoint Server 2010 , o tomar sólo determinados sitios y sitios Web a la siguiente versión (que puede que su trabajo sea más fácil).
    
3. Menor que hacer a la Microsoft Office SharePoint Server 2007 granja de servidores, directamente, el más segura contienen los datos de la granja de servidores como realiza una actualización.
    
Métodos al igual que la actualización en contexto actuará directamente en la granja de servidores de Microsoft Office SharePoint Server 2007, que confiere menos opciones fáciles abandonar una ruta de acceso y volver a empezar con el entorno original. En la medida de lo posible, crear en algunas medidas de seguridad (al igual que las pruebas de las copias de seguridad del entorno original y tomar). Por ejemplo, si la granja de servidores de Microsoft Office SharePoint Server 2007 es virtual y se duplica para los fines de copia de seguridad y restauración, a continuación, realizar copias de seguridad y restaurar las bases de datos más recientes antes de la ventana de servicio para la actualización. Sabiendo que la opción para restaurar la base de datos de las copias de seguridad no sólo le una a prueba de errores, puede proporcionar tranquilidad.
  
> [!TIP]
> Existen documentos de procedimientos recomendados para la actualización para [Microsoft Office SharePoint Server 2007](https://technet.microsoft.com/en-us/library/cc261992%28v=office.12%29.aspx), [SharePoint Server 2010](https://technet.microsoft.com/en-us/library/cc261992%28v=office.14%29.aspx), [SharePoint Server 2013](https://technet.microsoft.com/en-us/library/cc261992%28v=office.15%29.aspx)y [SharePoint Server 2016](https://technet.microsoft.com/en-us/library/cc261992%28v=office.16%29.aspx). También puede buscar [Los socios de Microsoft](https://partnercenter.microsoft.com/en-us/pcv/search) que tienen experiencia con las actualizaciones o migraciones de Office 365. 
  
## <a name="make-your-plan"></a>Realizar el plan

Si necesita actualizar, necesita un plan y un tamaño no cabe todo en estos casos. El plan puede ser tan simple como 'Crear una suscripción a Office 365 con SharePoint Online, registrar un dominio y redirigir las personas para guardar sus archivos allí'. Y puede que no sea. Tomar esa decisión es suya, y es hacia abajo hasta que lo que usted y sus usuarios realmente necesitan.
  
> [!NOTE]
> Es arriesgado para que se ejecute en software ha finalizado cuyo ciclo de vida. Productos que están fuera del soporte técnico ya no se han modificado cuando se encuentran problemas. Esto también significa que si surgen nuevas amenazas de seguridad, no habrá revisiones de seguridad o revisiones debido a que ya no se admiten los productos de final de ciclo de vida. Por favor, evitar esa situación! 
  
### <a name="first-know-your-farm"></a>En primer lugar, conocer la granja de servidores

Al actualizar, la toma de decisiones debe basarse en lo que hace la granja de servidores para su organización. ¿Qué necesidad cumplen? ¿Cuál es su función? Cada granja de servidores de la compañía puede tener una función diferente. Algunas de las granjas de servidores de SharePoint pueden ser *crítico* , algunos pueden ser archivos comprimidos--allí para custodia. O bien, si la granja de servidores a la vez rellena muchas funciones, a continuación, es posible que necesita saber qué colecciones de sitios, sitios Web o incluso las bibliotecas de documentos de hacerlo, las personalizaciones, y su importancia. Análisis de los datos en este nivel pueden parecer una gran cantidad de trabajo, pero puede ahorrar tiempo y esfuerzo para dominar su dominio antes de actualizar o migrar, lo. Una vez que sepa todos los elementos de mover y los bits más importantes, también podrá saber qué ha superado y puede dejar. Que beneficiarán sólo conocimientos que en el futuro. 
  
Por lo tanto, ¿qué usuarios dicen es más importante acerca de la granja de servidores de SharePoint?
  
- Características integradas de SharePoint
    
- El corpus de datos de gran tamaño (por ejemplo, un almacén de archivos)
    
- Disponibilidad
    
- Aplicaciones críticas, elementos web o documentos en la granja de servidores (granja de misión crítica)
    
- Cumplido los estándares de cumplimiento
    
- Personalizaciones
    
Si se ejecuta algo esencial para su negocio de la granja de servidores de SharePoint, por ejemplo, actúa como un catálogo de gran tamaño de los datos críticos acerca de los requisitos del servicio de cliente, puede colocar una marca de verificación junto a 'Aplicaciones críticas', pero también sería 'Disponibilidad'--es decir, su negocio afectado si no se ha podido utilizar SharePoint durante un tiempo. Del mismo modo, es posible que compruebe 'Personalizaciones' debido a que las importantes de servicios de la granja de servidores ofrece se basa en código personalizado, las definiciones de sitio o un número de personalizaciones que funcionan conjuntamente.
  
Si SharePoint cumple dichas necesidades sin tener que hacer nada fuera de uso de lo que está integrada en el software y que por lo general actualizarlo y llevar a cabo administración normal y mantenimiento, puede que haya elegido 'SharePoint integrados': también puede ser su motivo de la sentado en una versión anterior de SharePoint. En otras palabras, ya que hace lo que necesita para y todavía no lo necesario para actualizar hasta ahora, como Microsoft Office SharePoint Server 2007 fin del soporte.
  
Cuando viñeta lista estas cosas, crear criterios para la actualización. En otras palabras, cualquier actualización tendría que cumplir esta barra para tener en cuenta. Esto le ofrece una forma de la regla de métodos que actualmente no se ajustan a sus necesidades.
  
### <a name="a-simple-sample-plan"></a>Un plan de ejemplo simple

Es posible que necesite ser más amplio consenso con los altos directivos y otros administradores en la ruta de acceso que tardará la actualización de SharePoint. Los administradores de servidores de SharePoint a menudo colaborar con los administradores de Microsoft SQL Server, trabajar con los equipos de red y la seguridad y mucho más. Cuando hay una gran cantidad de las partes interesadas, es posible que necesita crear contrato para, o ajustar el plan de actualización y migración. Por ejemplo, si migra datos de forma que parte de su compañía usa SharePoint Online en Office 365, hay probablemente tendrá que ser ajuste del rendimiento o pruebas dentro de la red. Equipos afectados deben estar informados con anterioridad.
  
En mi ejemplo sencillo, muestra la propuesta de un administrador de SharePoint y a continuación, muestre el plan que se aceptan todas las partes interesadas. Para mayor claridad, documentar los contratos y las decisiones.
  
El plan se inicia después de un análisis en profundidad de una granja de servidores e intenta identificar la función de la granja de servidores, los puntos débiles y otra información importante que le llevará a limitar abajo algunas opciones de actualización. Posteriormente, una propuesta de actualización se realiza por el Administrador de SharePoint, y las partes interesadas de acuerdo en un plan de acción.
  
Mi lista de viñeta 'más importante':
  
- Disponibilidad, las características integradas de SharePoint y los estándares de cumplimiento de normas.
    
- La mayoría de los datos es en tres colecciones de sitios, con un área de reuniones usado por un equipo de desarrollo especialmente importante y un uso intensivo en varias de las zonas horarias en todo el mundo.
    
- Hay diecisiete otros sitios que se usan con frecuencia.
    
- Dos bibliotecas de documentos (área de reuniones y documentos en la colección de sitios raíz) son más grandes (más de 8000 documentos cada). Tenemos un gran número de documentos archivados y lista con datos adjuntos de la hoja de cálculo.
    
- Hay catorce listas de bibliotecas que tienen datos confidenciales que deben permanecer en cumplimiento.
    
- DEBEMOS tener la posibilidad de realizar suspensiones y exhibición de documentos electrónicos donde quiera que vaya.
    
- Algunos de estos datos deben permanecer local, debido a las reglas de InfoSec.
    
 **Mis opciones de actualización y migración:**
  
|||
|:-----|:-----|
|**Sí** <br/> |**No** <br/> |
|Adjuntar bases de datos de actualización con base de datos  <br/> |Actualización en contexto  <br/> |
|Actualización de granjas de servidores en paralelo  <br/> |Actualización híbrida  <br/> |
|API de migración a SPO en Office 365 (para los datos de un sitio personal)  <br/> |Híbrido de SharePoint (que no es necesario aún)  <br/> |
|Algunas migraciones manual de datos a SharePoint Online para datos críticos  <br/> |Actualización de asistente FastTrack a Office 365  <br/> |
   
 **Mi plan propuesto:**
  
Actualización local, con las versiones de SharePoint side-by-side, algunas virtualizado, de modo que nos podemos actualizar las bases de datos en primer lugar. Vaya de SharePoint 2007 a SharePoint 2010. Los administradores y programadores probar la granja de servidores resultante. Los usuarios de prueba la granja de servidores resultante. Corregir los problemas de detención de mostrar durante este tiempo. Una vez más, en paralelo, actualización SharePoint 2010 bases de datos a SharePoint 2013. Prueba de usuario de prueba/piloto. Corregir los problemas de detención de mostrar durante este tiempo.
  
- Tenga en cuenta si un híbrido de búsqueda federada con SPO satisface sus necesidades.
    
- Considere la posibilidad de [asistencia FastTrack](https://fasttrack.microsoft.com) si desea actualizar a SharePoint Online desde aquí. 
    
- Determinar si las colecciones de sitios se pueden descargar en una suscripción de Office 365. (Office 365 cumple [los estándares de cumplimiento de normas](https://technet.microsoft.com/library/office-365-compliance.aspx)de muchos. Office 365 tiene [exhibición de documentos electrónicos](https://support.office.com/article/edea80d6-20a7-40fb-b8c4-5e8c8395f6da) y puede hacer [las suspensiones](https://support.office.com/article/A18F8975-AA7F-43B4-A7D6-001D14744D8E) a través del centro de cumplimiento de normas.) 
    
De lo contrario, continúe con una actualización en paralelo para SharePoint Server 2016.
  
> [!NOTE]
> Entre las recomendaciones de los administradores de planeación de la actualización y el proceso real son las conversaciones que se producen con otras partes interesadas en la que se basa la actualización. Por ejemplo, en ocasiones, ahorro forzar los administradores para cambiar sus planes. Con independencia de la decisión final es, debe documentar el plan acordado What ' s, en el futuro. Podría tener un aspecto similar al siguiente: 
  
 **Mi plan de acción:**
  
Local, usamos un entorno virtual para generar valor predeterminado en SharePoint Server 2010 y 2013. SharePoint Server 2016 se generarán en nuevo hardware que cumpla los requisitos del sistema para 2016. Haremos adjunta para actualizar las bases de datos de SharePoint 2007 a través de todas las versiones entre éste y SharePoint Server 2016 de base de datos. Las personalizaciones de núcleo se que se vuelven a crear para y probado en el servidor de SharePoint 2016 entorno en este momento, si las características nativas ya no satisfacen nuestras necesidades. Si se son correctas, tendremos una granja de servidores local en hardware nuevo con bases de datos actualizadas y las personalizaciones menos. Se debe adjuntar las bases de datos de contenido actualizados a nuevas colecciones de sitios en SharePoint Server 2013, prueba, piloto y pruebas de usuario, y, a continuación, realice un DNS transferencia al nuevo entorno de SharePoint Server 2016 para su uso directo.
  
- No se va a tener en cuenta federados híbrida entre SharePoint Server 2016 y SharePoint Online ahora mismo.
    
- Un 35% estimado de nuestros sitios puede ser convertido en nuevos sitios SPO con dominios de cortesía, o, en última instancia, se convierten en OneDrive para el almacenamiento de negocio. Buscando otras oportunidades para convertir sitios o enrutar los sitios nuevos a SPO.
    
- Algunas de esta parte de la migración será manual mediante arrastrar y colocar a OneDrive para los sitios personales empresarial y algunos mediante la API de migración.
    
Pasos más detallan, o un número de vínculos a instrucciones específicas de actualización debe seguir un plan. No se debe desactivar el equipo de MOSS 2007 y entornos virtuales deben mantenerse por motivos de comparación; Sin embargo, la actualización se completará cuando los usuarios se redirigen a SharePoint Server 2016.
  
Elegir un método de los factores principales a menudo son el costo total de la actualización y el costo en tiempo (podrá ver más información al respecto en el artículo de la Guía de migración de SharePoint). Sin embargo, planeación con antelación le puede beneficiar en gran medida de establecer las expectativas, elegir con precaución, y qué éxito de tramas tendrá el siguiente aspecto.
  
## <a name="related-links"></a>Vínculos relacionados

[Recursos que le ayudarán a actualizar de Office 2007 de los clientes y servidores](upgrade-from-office-2007-servers-and-products.md)
  
[Policy Microsoft Lifecycle y ciclo de vida de búsqueda](https://support.microsoft.com/en-us/lifecycle)
  
[Busque Microsoft Partners que ayude con la actualización o migración](https://partnercenter.microsoft.com/en-us/pcv/search)
  

