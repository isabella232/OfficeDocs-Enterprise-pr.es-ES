---
title: Plan de fin del soporte técnico de SharePoint Server 2007
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 01/28/2019
audience: ITPro
ms.topic: conceptual
f1_keywords:
- vsemail
- MS_WSS_DirectoryManagement
- MS_WSS_ConfigEmail
- globalemailconfig
- configssc
- AppDefToBDC
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- OFU120
- SPS150
- OSU140
- WSU120
- OSR120
- SPO160
- PJW120
- SPB160
- OSI150
- OSI160
- BSA160
- OSU160
ms.assetid: ba124775-d5c0-4d68-b88d-8458ad4c3717
description: El 10 de octubre de 2017, se finalizó el soporte para SharePoint Server 2007. Lea este artículo para obtener información sobre las opciones de actualización, solución de problemas, procedimientos recomendados, requisitos del sistema, pasos de actualización y cómo obtener asistencia de los socios de Microsoft.
ms.openlocfilehash: 4054ca5c0b502c2008556021a80d3a939a979bb3
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2019
ms.locfileid: "38030915"
---
# <a name="sharepoint-server-2007-end-of-support-roadmap"></a>Plan de fin del soporte técnico de SharePoint Server 2007

El **10 de octubre de 2017**, Microsoft Office SharePoint Server 2007 alcanzó el final del soporte técnico. Si no ha iniciado la migración de SharePoint Server 2007 a Office 365 o a una versión más reciente de SharePoint Server local, ahora es el momento de empezar a planear. En este artículo se detallan los recursos para ayudar a los usuarios a migrar datos a SharePoint Online o actualizar el servidor de SharePoint local. 
  
## <a name="what-does-end-of-support-mean"></a>¿Qué significa el fin de soporte?

SharePoint Server, al igual que casi todos los productos de Microsoft, tiene un ciclo de vida de soporte técnico en el que Microsoft proporciona nuevas características, correcciones de errores, correcciones de seguridad, etc. Este ciclo de vida suele durar 10 años a partir de la fecha de lanzamiento inicial del producto y el final de este ciclo de vida se conoce como el final del soporte técnico del producto. Al final del soporte técnico, Microsoft ya no ofrece:
  
- Soporte técnico para los problemas que pueden surgir;
    
- Correcciones de errores para problemas detectados y que pueden afectar a la estabilidad y la usabilidad del servidor;
    
- Revisiones de seguridad para las vulnerabilidades detectadas y que pueden hacer que el servidor sea vulnerable a las infracciones de seguridad; y 
    
- Las actualizaciones de zona horaria.
    
Aunque la granja de servidores de SharePoint Server 2007 seguirá funcionando después del 10 de octubre de 2017, no se enviarán más actualizaciones, parches ni correcciones para el producto (incluidas las revisiones de seguridad o correcciones), y el soporte técnico de Microsoft se desplazará completamente a las versiones más recientes del producto. Como la instalación ya no será compatible o revisada, como fin de los enfoques de soporte técnico debe actualizar el producto o migrar datos importantes.
  
> [!TIP]
> Si aún no ha planeado la actualización o la migración, consulte: [Opciones de migración de SharePoint 2007 que hay que tener en cuenta](sharepoint-2007-migration-options.md)para algunos ejemplos de dónde comenzar. También puede buscar asociados de [Microsoft](https://go.microsoft.com/fwlink/?linkid=841249) que puedan ayudarle con la actualización o la migración de Office 365 (o ambos). 
  
Para obtener más información acerca de los servidores de Office 2007 que alcanzan el final del soporte técnico, vea [recursos para ayudarle a actualizar desde Office 2007 servidores y clientes](upgrade-from-office-2007-servers-and-products.md).
  
## <a name="what-are-my-options"></a>¿Qué opciones tengo?

El primer punto de interrupción debe ser el [sitio del ciclo de vida del producto](https://go.microsoft.com/fwlink/?linkid=843148). Si tiene un producto de Microsoft local que está obsoleto, debe comprobar la fecha de finalización del soporte técnico para que, un año, o tan bien como lo requieran las migraciones, puede programar la actualización o las migraciones. Al elegir el paso siguiente, es posible que le resulte útil considerar lo que sería lo suficientemente bueno, mejor y mejor cuando se refiere a las características del producto. Aquí le mostramos un ejemplo:
  
|**Good**|**Conseguir**|**Procedimientos**|
|:-----|:-----|:-----|
|SharePoint Server 2010  <br/> |SharePoint Server 2013  <br/> |SharePoint Online  <br/> |
||Entorno híbrido de SharePoint  <br/> |SharePoint Server 2016  <br/> |
|||Entorno híbrido de SharePoint  <br/> |
   
Si elige opciones en el extremo inferior de la escala (bueno), recuerde que tendrá que empezar a planear la actualización muy pronto después de que se complete la migración de SharePoint Server 2007. (el fin del soporte para SharePoint Server 2007 es el 10 de octubre de 2017. Tenga en cuenta que estas fechas están sujetas a cambios y comprobarán el [sitio de ciclo de vida del producto](https://support.microsoft.com/lifecycle).)
  
## <a name="where-can-i-go-next"></a>¿Qué puedo hacer a continuación?

SharePoint Server se puede instalar localmente en sus propios servidores o puede usar SharePoint Online, que es un servicio en línea que forma parte de Microsoft Office 365. Puede elegir entre:
  
- Migrar a SharePoint Online
    
- Actualizar SharePoint Server local
    
- Hacer lo anterior
    
- Implementar una solución [híbrida de SharePoint](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx) 
    
Tenga en cuenta los costos ocultos asociados con el mantenimiento de una granja de servidores en el futuro, el mantenimiento o la migración de personalizaciones, y la actualización del hardware que depende de SharePoint Server. El hecho de tener una granja de servidores de SharePoint Server local es recompensar si es necesario; de lo contrario, si ejecuta la granja de servidores en servidores de SharePoint heredados, sin una personalización intensa, puede beneficiarse de una migración planeada a SharePoint Online.
  
> [!IMPORTANT]
> Hay otra opción si el contenido de SharePoint 2007 se usa con poca frecuencia. Algunos administradores de SharePoint pueden optar por [crear una suscripción de Office 365](https://go.microsoft.com/fwlink/?linkid=843152), configurar un nuevo sitio de SharePoint Online de marca y, a continuación, recortar SharePoint 2007, sin problemas, tomando solo los documentos más esenciales en los sitios de SharePoint Online nuevos. Desde allí, los datos se pueden purgar del sitio de SharePoint 2007 en archivos. Dar a entender cómo los usuarios trabajan con los datos de la instalación de SharePoint 2007. Puede que haya formas creativas para resolver este problema. 
  
|**SharePoint Online (SPO)**|**SharePoint Server local**|
|:-----|:-----|
|Costo elevado en el tiempo (planificación/ejecución/comprobación)  <br/> |Costo elevado en el tiempo (planificación/ejecución/comprobación)  <br/> |
|Menor coste de fondos (no hay compras de hardware)  <br/> |Costo más alto en los fondos (hardware + desarrolladores/administradores)  <br/> |
|Costo de tiempo único en la migración  <br/> |Costo de tiempo único repetido por migración futura  <br/> |
|Bajo costo total de propiedad/mantenimiento  <br/> |Costo total de propiedad/mantenimiento elevado  <br/> |
   
Al migrar a Office 365, el movimiento único tendrá un costo inicial en primer plano, mientras organiza los datos y decide qué va a tomar en la nube y qué debe dejar atrás. Sin embargo, las actualizaciones serán automáticas a partir de ese momento, ya no necesitará administrar las actualizaciones de hardware y software, y el tiempo de actividad de la granja de servidores estará respaldado por un contrato de nivel de servicio ([SLA](https://go.microsoft.com/fwlink/?linkid=843153)) de Microsoft.
  
### <a name="migrate-to-sharepoint-online"></a>Migrar a SharePoint Online

Asegúrese de que SharePoint Online tiene todas las características que necesita mediante la revisión de la descripción del servicio asociado. Este es el vínculo a todas las descripciones del servicio Office 365:
  
[Descripciones del servicio de Office 365](https://go.microsoft.com/fwlink/?linkid=272060)
  
No hay una forma directa de migrar de SharePoint 2007 a SharePoint Online; el cambio a SharePoint Online se realizaría manualmente. Si actualiza a SharePoint Server 2013 o SharePoint Server 2016, su traslado también podría implicar el uso de la API de migración de SharePoint (para migrar información a OneDrive para la empresa, por ejemplo).
  
|**Online Pro**|**Con en línea**|
|:-----|:-----|
|Microsoft proporciona el hardware de SPO y toda la administración de hardware.  <br/> |Las características disponibles pueden ser diferentes entre la implementación local de SharePoint Server y SPO.  <br/> |
|Usted es el administrador global de su suscripción y puede asignar administradores a los sitios de SPO.  <br/> |Algunas acciones disponibles para un administrador de la granja de servidores en SharePoint Server local no existen (o no son necesarias) incluidas en el rol de administrador de SharePoint en Office 365.  <br/> |
|Microsoft aplica revisiones, correcciones y actualizaciones al hardware y software subyacentes.  <br/> |Como no hay acceso al sistema de archivos subyacente en el servicio, algunas personalizaciones son limitadas.  <br/> |
|Microsoft publica [contratos de nivel de servicio](https://go.microsoft.com/fwlink/?linkid=843153) y se mueve rápidamente para resolver los incidentes de nivel de servicio.  <br/> |La copia de seguridad y restauración y otras opciones de recuperación están automatizadas por el servicio en SharePoint Online: las copias de seguridad se sobrescriben si no se usan.  <br/> |
|Las pruebas de seguridad y el ajuste del rendimiento del servidor se llevan a cabo de manera continua en el servicio de Microsoft.  <br/> |El servicio instala los cambios en la interfaz de usuario y en otras características de SharePoint, por lo que es posible que deban activarse o desactivarse.  <br/> |
|Office 365 cumple muchos estándares del sector: [office 365 Compliance](https://go.microsoft.com/fwlink/?linkid=843165).  <br/> |La asistencia de [FastTrack](https://go.microsoft.com/fwlink/?linkid=518597) para la migración es limitada.  <br/> La mayor parte de la actualización será manual o a través de la API de migración de SPO que se describe en la [Guía de contenido de migración de SharePoint Online y OneDrive](https://go.microsoft.com/fwlink/?linkid=843184).  <br/> |
|Ni los ingenieros de soporte técnico de Microsoft ni los empleados en el centro de administración de la sesión tienen acceso de administrador sin restricciones a su suscripción.  <br/> |Puede haber costos adicionales si es necesario actualizar la infraestructura de hardware para que sea compatible con la versión más reciente de SharePoint o si se requiere una granja secundaria para la actualización.  <br/> |
|Los socios pueden ayudarle con el trabajo único de migrar los datos a SharePoint Online.  <br/> ||
|Los productos en línea se actualizan automáticamente en el servicio, lo que significa que, aunque las características puedan dejar de estar en desuso, no hay verdaderos extremos del soporte técnico.  <br/> ||
   
Si ha decidido crear un nuevo sitio de Office 365 y migrar los datos de forma manual según sea necesario, puede ver las opciones de 365 de Office en el siguiente sitio:
  
[Opciones de planes de Office 365](https://go.microsoft.com/fwlink/?linkid=843151)
  
### <a name="upgrade-sharepoint-server-on-premises"></a>Actualizar SharePoint Server local

Históricamente no hay forma de omitir las versiones en las actualizaciones de SharePoint, al menos no a partir de la versión de SharePoint Server 2016. Esto significa que las actualizaciones se realizan en serie:
  
|||
|:-----|:-----|
||SharePoint 2007 | SharePoint Server 2010 | SharePoint Server 2013 | SharePoint Server 2016 |
   
Para que la ruta de acceso completa de SharePoint 2007 a SharePoint Server 2016 signifique una importante inversión de tiempo y implicará un costo en términos de hardware actualizado (tenga en cuenta que también es necesario actualizar los servidores SQL), el software y la administración. Las personalizaciones deberán actualizarse o abandonarse de acuerdo con la criticidad de la característica.
  
> [!NOTE]
> Es posible mantener su granja de servidores de SharePoint 2007 de final de vida, instalar una granja de servidores de SharePoint Server 2016 en hardware nuevo (por lo que las granjas de servidores independientes se ejecutan en paralelo) y, a continuación, planear y ejecutar una migración manual del contenido (para descargar y volver a cargar contenido, para ejemplo). Tenga en cuenta algunas de las trampas de movimientos manuales (como los movimientos de documentos que reemplazan la última cuenta modificada por el alias de la cuenta que realiza el traslado manual) y el trabajo que debe realizarse con antelación (como, por ejemplo, la creación de sitios, subsitios, permisos y listas estructuras). De nuevo, este es el momento de considerar qué datos puede mover a almacenamiento o ya no necesita, una acción que puede reducir el impacto de la migración.
  
En cualquier caso, limpie su entorno antes de actualizar. Asegúrese de que la granja de servidores existente es funcional antes de realizar la actualización y, (para asegurarse) antes de su retiro. 
  
Recuerde revisar las **rutas de actualización admitidas y no admitidas**: 
  
- 
  [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843157)
    
Si tiene **personalizaciones**, es fundamental que disponga de un plan de actualización para cada paso de la ruta de migración: 
  
- [SharePoint 2007](https://go.microsoft.com/fwlink/?linkid=843158)
    
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843160)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843162)
    
|**Pro local**|**Local con**|
|:-----|:-----|
|Control total de todos los aspectos de la granja de servidores de SharePoint, desde el hardware del servidor hacia arriba.  <br/> |Todos los descansos y las correcciones son responsabilidad de su empresa (puede participar en el soporte de Microsoft si su producto no está al final del soporte técnico):  <br/> |
|Conjunto completo de características de SharePoint Server local con la opción de conectar la granja de servidores local con una suscripción de SharePoint Online a través de un híbrido.  <br/> |Actualización, revisiones, correcciones de seguridad y todo el mantenimiento de SharePoint Server administrado localmente.  <br/> |
|Acceso completo para una mayor personalización.  <br/> |Los [estándares de cumplimiento admitidos por Office 365](https://go.microsoft.com/fwlink/?linkid=843165) deben configurarse manualmente de forma local.  <br/> |
|Pruebas de seguridad y ajuste del rendimiento del servidor, realizadas en sus instalaciones (está bajo su control).  <br/> |Office 365 puede poner características a disposición de SharePoint Online que no interoperen con SharePoint Server local  <br/> |
|Los socios pueden ayudarle a migrar datos a la próxima versión de SharePoint Server (y versiones posteriores).  <br/> |Los sitios de SharePoint Server no usarán automáticamente los certificados [SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167) como se ve en SharePoint Online.  <br/> |
|Control total de las convenciones de nomenclatura, copia de seguridad y restauración, y otras opciones de recuperación en SharePoint Server local.  <br/> |SharePoint Server local es sensible a los ciclos de vida de los productos.  <br/> |
   
### <a name="upgrade-resources"></a>Recursos de actualización

Comience por saber que cumple con los requisitos de hardware y software y, a continuación, siga los métodos de actualización admitidos.
  
- **Requisitos de hardware y software para**: 
    
    [](https://go.microsoft.com/fwlink/?linkid=843204) | SharePoint Server 2010 SharePoint[Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | SharePoint Server[2013](https://go.microsoft.com/fwlink/?linkid=843206) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843207)
    
- Límites **de software para**: 
    
    [](https://go.microsoft.com/fwlink/?linkid=843245) | SharePoint Server 2007 SharePoint[Server 2010](https://go.microsoft.com/fwlink/?linkid=843247) | SharePoint Server[2013](https://go.microsoft.com/fwlink/?linkid=843248) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843249)
    
- **Información general sobre el proceso de actualización para**: 
    
    [](https://go.microsoft.com/fwlink/?linkid=843250) | SharePoint Server 2007 SharePoint[Server 2010](https://go.microsoft.com/fwlink/?linkid=843251) | SharePoint Server[2013](https://go.microsoft.com/fwlink/?linkid=843252) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843359)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a>Crear una solución híbrida de SharePoint entre SharePoint Online y local

Si la respuesta a sus necesidades de migración se encuentra en algún lugar entre el autocontrol ofrecido por el sistema local y el menor costo de propiedad ofrecido por SharePoint Online, puede conectar granjas de servidores de SharePoint Server 2013 o 2016 a SharePoint Online, a través de híbridos. [Obtenga información sobre las soluciones híbridas de SharePoint](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)
  
Si decide que una granja de servidores híbrida de SharePoint Server beneficiará su negocio, familiarícese con los tipos existentes de híbridos y cómo configurar la conexión entre su granja de servidores local de SharePoint y la suscripción a Office 365.
  
Una buena forma de ver cómo funciona esto es mediante la creación de un [entorno de desarrollo y pruebas de Office 365](https://go.microsoft.com/fwlink/?linkid=843152). Una vez que tenga una suscripción a la versión de prueba de Office 365, estará en la forma de crear las colecciones de sitios, los webs y las bibliotecas de documentos en SharePoint Online a los que puede migrar datos (ya sea manualmente, mediante la API de migración, o si desea migrar mi Contenido del sitio en OneDrive para la empresa mediante el asistente híbrido).
  
> [!NOTE]
> Recuerde que la granja de servidores de SharePoint 2007 debe actualizarse, local, a SharePoint Server 2013 o SharePoint Server 2016 para usar la opción híbrida 
  
## <a name="related-topics"></a>Temas relacionados

[Solución de problemas y reanudación de la actualización (Office SharePoint Server 2007)](https://go.microsoft.com/fwlink/?linkid=843192)
  
[Solución de problemas de actualización (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?linkid=843194)
  
[Solucionar problemas de actualización de bases de datos en SharePoint 2013](https://go.microsoft.com/fwlink/?linkid=843195)
  
[Buscar a los socios de Microsoft para ayudarle con la actualización](https://go.microsoft.com/fwlink/?linkid=841249)
  
[Recursos que le ayudarán a actualizar desde los servidores y clientes de Office 2007](upgrade-from-office-2007-servers-and-products.md)
  

