---
title: Opciones de migración de SharePoint 2007 para tener en cuenta
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 1/31/2018
audience: ITPro
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
description: SharePoint Server 2007 ha alcanzado el final del soporte técnico y es el momento de actualizar. Use este artículo para ayudarle a crear su plan.
ms.openlocfilehash: 98151ecd32f0066f583da1142d6010d46e120a43
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070706"
---
# <a name="sharepoint-2007-migration-options-to-consider"></a>Opciones de migración de SharePoint 2007 para tener en cuenta

Microsoft SharePoint 2007 y SharePoint Server 2007 han llegado al final del soporte técnico. Es el momento de actualizar. En este artículo se proporciona información acerca de las opciones de migración.
  
## <a name="common-upgrade-strategies-for-sharepoint"></a>Estrategias de actualización comunes para SharePoint

Hay varios métodos para actualizar un entorno de SharePoint Server. Si tiene una granja de servidores de Microsoft Office SharePoint Server 2007, estos son algunos ejemplos de los métodos de actualización:
  
- Base de datos adjunta
    
- Actualización en paralelo
    
- Actualización en contexto
    
- Actualización híbrida (en la misma ubicación con bases de datos desasociadas/adjunta de bases de datos independiente)
    
- Entornos híbridos de SharePoint (conectar en línea con SharePoint local)
    
- Movimiento manual de datos entre colecciones de sitios o bibliotecas
    
- Actualización del asistente de FastTrack a Office 365 ([Asesor de implementación de SharePoint Online](https://aka.ms/spoguidance))
    
- API de migración a SharePoint Online (SPO) en Office 365
    
¿Qué funciona mejor para usted?
  
El conocimiento de la función de la granja de servidores y se usa para es una resistencia táctica en lo que se refiere a la actualización. La forma en que los usuarios usan la granja de servidores de SharePoint le ayudará a elegir entre las opciones.
  
> [!TIP]
> Microsoft Office SharePoint Server 2007 también tiene una actualización gradual que no se incluye aquí. Para ver una lista de los artículos de actualización específica del paso, vea el [mapa de ruta del fin de soporte de SharePoint Server 2007](sharepoint-2007-end-of-support.md). 
  
Recuerde comprobar el [ciclo de vida del producto](https://support.microsoft.com/en-us/lifecycle/search) y los requisitos del sistema para cualquier versión de SharePoint a la que esté actualizando. Esto es así que sabrá Cuándo será necesaria la próxima actualización (por ejemplo, si pausa en un producto heredado como SharePoint Server 2010 para planear más actualizaciones, asegúrese de que conoce la fecha de finalización del soporte técnico) y asegúrese de que dispone de hardware compatible con su plan. 
  
Si está planeando realizar la transición de algunos o todos los sitios de SharePoint a Office 365 en la nube, esta es una hora para marcar un vínculo a las descripciones [de servicio de Office 365](https://technet.microsoft.com/en-us/library/office-365-service-descriptions.aspx). Necesitará las descripciones de servicio para obtener información sobre las características de SharePoint Online y cómo podrían diferir de SharePoint Server local. Actualización de granjas funcionales de Microsoft Office SharePoint Server 2007. Si su instalación tiene sitios rotos, corríjalos antes de realizar la actualización.
  
## <a name="a-note-about-managing-risk"></a>Una nota sobre la administración de riesgos

Los métodos como ' en paralelo ' son importantes en el esquema de la lógica de actualización. Cuando se actualiza en paralelo, se mantiene la granja de servidores de Microsoft Office SharePoint Server 2007, pero se crea una granja de servidores con la siguiente versión (SharePoint Server 2010) en hardware nuevo. Esto sirve de tres maneras:
  
1. Tiene un punto de realizar copias de seguridad de las bases de datos de Microsoft Office SharePoint Server 2007 para actualizarlas por separado, mediante la Asociación de bases de datos.
    
2. Si se averigua que solo se usa un pequeño número de bibliotecas de documentos críticas y otra información en la granja de servidores de Microsoft Office SharePoint Server 2007, puede optar por mover manualmente los datos de Microsoft Office SharePoint Server 2007 a SharePoint Server 2010 o usar sitios y sitios web específicos en la siguiente versión (lo que puede simplificar su trabajo).
    
3. Lo menos que se hace con la granja de servidores de Microsoft Office SharePoint Server 2007, de forma directa, más seguro es la información que contiene la granja de servidores durante la actualización.
    
Los métodos como la actualización local actuarán directamente en su granja de servidores de Microsoft Office SharePoint Server 2007, lo que le proporcionará menos opciones sencillas para abandonar una ruta y comenzar de nuevo con su entorno original. En la medida de lo posible, cree algunas medidas de seguridad (como tomar y probar las copias de seguridad del entorno original). Por ejemplo, si la granja de servidores de Microsoft Office SharePoint Server 2007 es virtual y está duplicada con fines de copia de seguridad y restauración, haga una copia de seguridad y restaure las bases de datos más recientes antes de la ventana de servicio para la actualización. Saber que tiene la opción de restaurar las copias de seguridad de la base de datos no solo le ofrecerá un failsafe, sino que podrá tener la tranquilidad.
  
> [!TIP]
> Procedimientos recomendados los documentos para la actualización existen para [Microsoft Office SharePoint server 2007](https://technet.microsoft.com/en-us/library/cc261992%28v=office.12%29.aspx), [SharePoint Server 2010](https://technet.microsoft.com/en-us/library/cc261992%28v=office.14%29.aspx), [SharePoint server 2013](https://technet.microsoft.com/en-us/library/cc261992%28v=office.15%29.aspx)y [SharePoint Server 2016](https://technet.microsoft.com/en-us/library/cc261992%28v=office.16%29.aspx). También puede buscar a los [socios de Microsoft](https://partnercenter.microsoft.com/en-us/pcv/search) que tienen experiencia con las actualizaciones o migraciones de Office 365. 
  
## <a name="make-your-plan"></a>Hacer que el plan

Si necesita realizar una actualización, necesitará un plan y no se ajustará el tamaño alguno en estos casos. El plan puede ser tan simple como ' crear una suscripción de Office 365 con SharePoint Online, registrar un dominio y redirigir a los usuarios para que guarden sus archivos allí '. Y puede no ser así. La decisión es suya, y se refiere a lo que usted y los usuarios necesitan realmente.
  
> [!NOTE]
> Es arriesgado ejecutarse en un software cuyo ciclo de vida haya finalizado. Los productos que no tienen soporte técnico ya no se revisan cuando se encuentran problemas. Esto también significa que si surgen nuevas amenazas de seguridad, no habrá revisiones ni correcciones de seguridad porque ya no se admiten los productos de fin de ciclo de vida. Por ello, evite esta situación. 
  
### <a name="first-know-your-farm"></a>En primer lugar, conozca la granja de servidores

Al actualizar, la toma de decisiones debe basarse en las funciones de la granja de servidores para su organización. ¿Qué es necesario satisfacer? ¿Cuál es su rol? Cada granja de servidores de su compañía puede tener un rol diferente. Es posible que algunas de las granjas de servidores de SharePoint sean *críticas* , algunas puedan ser archivos comprimidos (para mantener la seguridad). O bien, si la granja de servidores rellena muchas funciones a la vez, es posible que necesite saber qué colecciones de sitios, sitios web o incluso bibliotecas de documentos hacen, qué personalizaciones y qué importancia tienen. El análisis de los datos en este nivel puede parecer una gran cantidad de trabajo, pero ahorra tiempo y esfuerzo para dominar el dominio antes de que se actualice o se migre. Una vez que conozca todas las partes móviles y los bits más importantes, también sabrá qué ha sobrecrecedo y puede dejar atrás. Ese conocimiento solo le beneficiará de su futuro. 
  
Por lo tanto, ¿qué opinan los usuarios sobre la granja de servidores de SharePoint Server?
  
- Características integradas de SharePoint
    
- El corpus de datos de gran tamaño (por ejemplo, un archivo de archivos)
    
- Disponibilidad
    
- Aplicaciones críticas, elementos Web o documentos de la granja de servidores (granja de servidores de misión crítica)
    
- Estándares de cumplimiento cumplidos
    
- Personalizaciones
    
Si ejecuta algo esencial para su empresa desde su granja de servidores de SharePoint, diga que actúa como un gran catálogo de datos críticos sobre los requisitos de servicio de cliente, puede poner una marca junto a ' aplicaciones críticas ', pero también ' disponibilidad '--es decir, su empresa será se ve afectado si no ha podido usar SharePoint durante un rato. Del mismo modo, puede comprobar ' personalizaciones ' porque los servicios críticos que ofrece la granja de servidores se basan en código personalizado, definiciones de sitio o varias personalizaciones que funcionan juntas.
  
Si SharePoint cumplía esas necesidades sin tener que hacer nada fuera del uso de lo que está integrado en el software y, por lo general, se actualiza y se realiza el mantenimiento normal, puede que haya elegido "SharePoint integrado", que también puede ser su razón para estar en una versión anterior de SharePoint. Es decir, ya tiene lo que necesita y no ha necesitado actualizar hasta ahora, en Microsoft Office SharePoint Server 2007, el fin de soporte técnico.
  
Al enumerar con viñetas estos elementos, se crean criterios para la actualización. Es decir, cualquier actualización tendría que cumplir esta barra para poder considerarse. Esto le ofrece una forma de descartar métodos que no se ajustan a sus necesidades en la actualidad.
  
### <a name="a-simple-sample-plan"></a>Un plan de ejemplo sencillo

Es posible que deba ser un consenso más amplio con liderazgo y otros administradores en la ruta que llevará a cabo la actualización de SharePoint. Los administradores de SharePoint Server a menudo cooperan con los administradores de Microsoft SQL Server, funcionan con los equipos de seguridad y redes, y más. Cuando hay muchas partes interesadas, es posible que deba crear un contrato para o ajustar el plan de actualización y migración. Por ejemplo, si migra datos para que parte de la compañía use SharePoint Online en Office 365, probablemente habrá que ajustar el rendimiento o realizar pruebas dentro de la red. Los equipos afectados deben estar informados antes de tiempo.
  
En mi ejemplo sencillo, se muestra una propuesta de administrador de SharePoint y, a continuación, se muestra el plan sobre el que se acordaron todas las partes interesadas. Para una mayor claridad, documente sus contratos y decisiones.
  
El plan se inicia después de un análisis exhaustivo de una granja de servidores e intenta identificar el rol de la granja de servidores, los Pain Points y otra información importante que conducirá a limitar algunas opciones de actualización. Después, el administrador de SharePoint realiza una propuesta de actualización y las partes interesadas acuerdan un plan de acción.
  
Mi lista de viñetas "más importante":
  
- Disponibilidad, características integradas en SharePoint y estándares de cumplimiento.
    
- La mayoría de los datos se encuentra en tres colecciones de sitios, con un área de reuniones usada por un equipo de desarrollo especialmente importante y de uso intenso en varias zonas horarias en todo el mundo.
    
- Hay diecisiete otros sitios que se usan ampliamente.
    
- Dos bibliotecas de documentos (el área de reuniones y los documentos de la colección de sitios raíz) son mayores (más de 8000 documentos). Tenemos un gran número de documentos archivados y listas con datos adjuntos de hoja de cálculo.
    
- Hay catorce listas de bibliotecas que tienen datos confidenciales que deben cumplirse.
    
- Debemos tener la capacidad de llevar contenciones y e-Discovery siempre que vayamos.
    
- Algunos de estos datos deben permanecer en local, debido a las reglas de InfoSec.
    
 **Mis opciones de actualización y migración:**
  
|||
|:-----|:-----|
|**Sí** <br/> |**No** <br/> |
|Actualizar bases de datos con adjuntar base de datos  <br/> |Actualización en contexto  <br/> |
|Actualizar con granjas en paralelo  <br/> |Actualización híbrida  <br/> |
|API de migración a SPO en Office 365 (para datos de sitios personales)  <br/> |Entorno híbrido de SharePoint (no es necesario todavía)  <br/> |
|Algunas migraciones de datos manuales a SharePoint Online para datos críticos  <br/> |Actualización del asistente de FastTrack a Office 365  <br/> |
   
 **Mi plan propuesto:**
  
La actualización local, con versiones de SharePoint en paralelo, algunas virtualizadas, por lo que se pueden actualizar primero las bases de datos. Vaya de SharePoint 2007 a SharePoint 2010. Los administradores y desarrolladores prueban la granja de servidores resultante. Los usuarios prueban la granja de servidores resultante. Corrija los problemas de presentación que se hayan detenido durante este tiempo. De nuevo, en paralelo, actualice las bases de datos de SharePoint 2010 a SharePoint 2013. Comprobación. Prueba del usuario o piloto. Corrija los problemas de presentación que se hayan detenido durante este tiempo.
  
- Considere si un híbrido federado de búsqueda con SPO satisface sus necesidades.
    
- Considere la [asistencia de FastTrack](https://fasttrack.microsoft.com) si desea actualizar a SharePoint Online desde aquí. 
    
- Determine si las colecciones de sitios se pueden descargar a una suscripción de Office 365. (Office 365 cumple muchos [estándares de cumplimiento](https://technet.microsoft.com/library/office-365-compliance.aspx). Office 365 tiene [eDiscovery](https://support.office.com/article/edea80d6-20a7-40fb-b8c4-5e8c8395f6da) y puede realizar [suspensiones](https://support.office.com/article/A18F8975-AA7F-43B4-A7D6-001D14744D8E) a través del centro de cumplimiento.) 
    
De lo contrario, continúe con una actualización en paralelo a SharePoint Server 2016.
  
> [!NOTE]
> Entre las recomendaciones realizadas por los administradores que planean la actualización y el proceso real se encuentran las conversaciones que se producen con otras partes interesadas en las que se basa la actualización. Por ejemplo, a veces el ahorro de los administradores obliga a cambiar sus planes. Independientemente de la decisión final, debe documentar lo que es el plan acordado, en el futuro. Puede tener un aspecto similar al siguiente: 
  
 **Mi plan de acción:**
  
De forma local, usamos un entorno virtual para crear SharePoint Server 2010 y 2013. SharePoint Server 2016 se creará en hardware nuevo que cumpla los requisitos del sistema para 2016. Realizaremos la base de datos adjunta para actualizar las bases de datos de SharePoint 2007 a todas las versiones entre ti y SharePoint Server 2016. Las personalizaciones principales se recrean para y se prueban en el entorno de SharePoint Server 2016 en este momento, si las características nativas aún no satisfacen nuestras necesidades. Si tenemos éxito, tendremos una granja de servidores local en hardware nuevo con bases de datos actualizadas y menos personalizaciones. Adjuntaremos las bases de datos de contenido actualizadas a las nuevas colecciones de sitios en SharePoint Server 2013, prueba, prueba del usuario o piloto y, a continuación, realizará un recorte de DNS para el nuevo entorno de SharePoint Server 2016 para el uso en directo.
  
- No consideraremos el híbrido federado entre SharePoint Server 2016 y SharePoint Online en este momento.
    
- Un estimado 35% de nuestros sitios se puede convertir en nuevos sitios de SPO con dominios de cortesía o, en última instancia, en OneDrive para la empresa. Buscar otras oportunidades para convertir sitios o enrutar nuevos sitios a SPO.
    
- Parte de esta parte de la migración será manual, mediante la función de arrastrar y colocar a los sitios personales de OneDrive para la empresa, y algunas mediante la API de migración.
    
Los pasos más detallados, o una serie de vínculos a direcciones de actualización específicas, deben seguir un plan. El equipo con MOSS 2007 no debe ser retirado, y los entornos virtuales deben mantenerse con fines de comparación; sin embargo, la actualización se completará cuando se redirija a los usuarios a SharePoint Server 2016.
  
A menudo, los principales factores a la hora de elegir un método son el costo total de la actualización y el costo en el tiempo (verá más información al respecto en el artículo plan de desarrollo de la migración de SharePoint). Sin embargo, la planeación anticipada le ayudará en gran medida en establecer las expectativas, elegir sabiamente y establecer el aspecto que tendrá el éxito.
  
## <a name="related-links"></a>Vínculos relacionados

[Recursos que le ayudarán a actualizar desde los servidores y clientes de Office 2007](upgrade-from-office-2007-servers-and-products.md)
  
[Búsqueda del ciclo de vida y la Directiva de Microsoft Lifecycle](https://support.microsoft.com/en-us/lifecycle)
  
[Buscar asociados de Microsoft que puedan ayudarle con la actualización o migración](https://partnercenter.microsoft.com/en-us/pcv/search)
  

