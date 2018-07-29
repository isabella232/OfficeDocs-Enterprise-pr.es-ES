---
title: Actualizar desde SharePoint 2010
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 2/2/2018
ms.audience: ITPro
ms.topic: conceptual
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- WSU140
- OSU140
ms.assetid: 985a357f-6db7-401f-bf7a-1bafdf1f312c
description: SharePoint 2010 y SharePoint Server 2010 se está acercando a fin de soporte. Use este artículo como guía para la actualización a SharePoint Online o una versión más reciente del servidor de SharePoint local.
ms.openlocfilehash: c88c6010aa398d8076fce59976bf6f5c0aa1a743
ms.sourcegitcommit: a9c84d02e94c99ff6b1099b4a9ae695be08210e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/25/2018
ms.locfileid: "21169872"
---
# <a name="upgrading-from-sharepoint-2010"></a>Actualizar desde SharePoint 2010

En la 13 de Oct de 2020, Microsoft Office SharePoint Server 2010 llega a fin de soporte. En este artículo se detalla los recursos para ayudar a las personas a migrar sus datos existentes de SharePoint Server 2010 para SharePoint Online, o actualizar el servidor de SharePoint local.
  
## <a name="what-is-end-of-support"></a>¿Qué es fin del soporte?

Cuando el software de SharePoint Server 2010 y SharePoint Foundation 2010 llega al final de su ciclo de vida de soporte técnico (es decir, el tiempo durante el cual Microsoft proporciona nuevas características, correcciones de errores, las revisiones de seguridad y así sucesivamente), esto se denomina 'fin del software del soporte ', o bien, en ocasiones, su 'jubilación'. Tras el final de soporte técnico (o EOS) de un producto, no hay nada realmente se apaga o deja de funcionar; Sin embargo, al final de compatibilidad de software, Microsoft ya no proporciona:
  
- Soporte técnico para problemas que puedan surgir;
    
- Correcciones de errores para los problemas que se descubren y que puede afectar a la estabilidad y la facilidad de uso del servidor;
    
- Revisiones de seguridad para las vulnerabilidades de seguridad que se descubren y que puede hacer el servidor vulnerable a infracciones de seguridad;
    
- Actualizaciones de zona horaria.
    
Esto significa que no habrá ninguna otra actualizaciones, revisiones, o correcciones se enviarán para el producto (incluidas las revisiones y revisiones de seguridad) y Microsoft Support totalmente habrá desplaza sus esfuerzos de soporte técnico a las versiones más recientes. Tal y como se aproxima el final del soporte técnico de SharePoint Server 2010, debe aprovechar las oportunidades para recortar datos que ya no necesita antes de la actualización del producto, o migrar los datos importantes.
  
> [!NOTE]
> Un ciclo de vida de software normalmente dura 10 años desde la fecha de lanzamiento del producto. Puede buscar [Los socios de Microsoft](https://go.microsoft.com/fwlink/?linkid=841249) que puede ayudar a con la actualización a la siguiente versión del software, o con la migración de Office 365 (o ambos). Asegúrese de que está al tanto de final de las fechas de soporte técnico en críticas tecnologías subyacentes así, especialmente de la versión de SQL server que está utilizando con SharePoint. 
  
## <a name="what-are-my-options"></a>¿Cuáles son las opciones de mi?

En primer lugar, compruebe la fecha en que termina de soporte en el [sitio del ciclo de vida del producto](https://support.microsoft.com/en-us/lifecycle/search?alpha=SharePoint%20Server%202010). A continuación, asegúrese de planear la actualización o migración de tiempo con conocimiento de esta fecha. Recuerde que su producto *no deje de funcionar* en la fecha y, puede continuar su uso, pero que, puesto que la instalación ya no se aplicará una revisión después de esa fecha, querrá una estrategia que le ayudarán a más suave transición a la siguiente versión del producto. 
  
Esta matriz ayuda a trazar un curso cuando lo que respecta a la migración de las características del producto y datos de usuario:
  
|**final del producto de soporte técnico**|**Bueno**|**Procedimientos**|
|:-----|:-----|:-----|
|SharePoint Server 2010  <br/> |SharePoint Server 2013  <br/> |SharePoint Online  <br/> |
||Entorno híbrido de SharePoint  <br/> |SharePoint Server 2016 (local)  <br/> |
|||Búsqueda de SharePoint en la nube híbrida  <br/> |
   
Si elige opciones en el extremo inferior de la escala (las opciones de buena), debe iniciar la planeación de actualización otra poco después de que se complete la migración desde SharePoint Server 2010. (fin del soporte para SharePoint Server 2010 y SharePoint Foundation 2010 están programados para el 13 de octubre de 2020, pero *tenga en cuenta* que siempre debe comprobar el [sitio del ciclo de vida del producto](https://support.microsoft.com/en-us/lifecycle) las fechas más precisas!) 
  
## <a name="where-should-i-go-next"></a>¿Dónde puedo siguiente?

SharePoint Server 2013 y SharePoint Foundation 2013 pueden ser instalados localmente en sus propios servidores. De lo contrario, puede usar SharePoint Online, que es un servicio en línea que forma parte de Microsoft Office 365. Puede elegir para:
  
- Migrar a SharePoint Online
    
- Actualización de SharePoint Server o SharePoint Foundation local
    
- Realice los dos mencionados anteriormente
    
- Implementar una solución [híbrida de SharePoint](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx) 
    
Tenga en cuenta oculta los costos asociados al mantenimiento de una granja de servidores en el futuro, mantener o migrar las personalizaciones y actualizar el hardware que depende el servidor de SharePoint. Si está al tanto y ha tenido en cuenta todas estas, será más fácil continuar con la actualización local. De lo contrario, si ejecuta la granja de servidores en los servidores de SharePoint heredado sin una fuerte personalización, podría beneficiarse de una migración planeada a SharePoint Online. También es posible que local tiendas de SharePoint Server pueden optar por instalar algunos datos en SharePoint Online para reducir la cantidad de administración de hardware mantener todas sus datos locales implica. Puede ser más económico mover algunos de los datos en SharePoint Online.
  
> [!NOTE]
> Los administradores de SharePoint, se puede [crear una suscripción de Office 365](https://go.microsoft.com/fwlink/?linkid=843152), configurar un nuevo sitio de SharePoint Online y, a continuación, cortar fuera de SharePoint Server 2010, sin problemas, teniendo sólo los documentos más esenciales para los sitios de SharePoint Online actualizados. Desde allí, pueden ser mayor los datos restantes desde el sitio de SharePoint Server 2010 en archivos locales. 
  
|**SharePoint Online (SPO)**|**Servidor de SharePoint local**|
|:-----|:-----|
|Alto costo en el tiempo (plan / ejecución y comprobación)  <br/> |Alto costo en el tiempo (plan / ejecución y comprobación)  <br/> |
|Menor costo en fondos (sin compras de hardware)  <br/> |Mayor costo en fondos (compras de hardware)  <br/> |
|Costo de una sola vez en la migración  <br/> |Costo de una sola vez se repite por migración futura  <br/> |
|Bajo costo total de propiedad y mantenimiento  <br/> |Alto costo total de propiedad y mantenimiento  <br/> |
   
Al migrar a Office 365, la única mover habrá un costo mayor en el tiempo empleado en la planeación inicial (mientras está organizar los datos y decidir qué se va a seguir para la nube y qué dejar). Sin embargo, una vez que se migran los datos, las actualizaciones estarán automáticas desde ese punto, vean como ya no se necesita administrar las actualizaciones de hardware y software, y el tiempo de funcionamiento de la granja de servidores se realizará por un contrato de nivel de servicio ([SLA](https://go.microsoft.com/fwlink/?linkid=843153)) de Microsoft.
  
### <a name="migrate-to-sharepoint-online"></a>Migrar a SharePoint Online

Asegúrese de que SharePoint Online ofrece todas las características que necesita mediante la revisión de la descripción del servicio asociado. Éste es el vínculo a todas las descripciones del servicio de Office 365:
  
[Descripciones del servicio Office 365](https://go.microsoft.com/fwlink/?linkid=272060)
  
Actualmente no hay un medio mediante el cual puede directamente migrar desde SharePoint Server 2010 (o SharePoint Foundation 2010) en SharePoint Online, por lo que cantidad de trabajo es manual. Esto le otorga la oportunidad de archivo y eliminación de datos y los sitios que ya no son necesarios, antes del movimiento. Puede archivar otros datos en almacenamiento de información. Asimismo, recuerde que ni de SharePoint Server 2010 ni de SharePoint Foundation 2010 dejará de funcionar a fin de soporte, por lo que los administradores pueden tener un período durante el cual SharePoint todavía se está ejecutando si sus clientes se olvide de mover algunos de sus datos.
  
Si actualizar a SharePoint Server 2013 o SharePoint Server 2016 y decidir poner datos en SharePoint Online, su movimiento también puede implicar el uso de la [API de migración de SharePoint](https://support.office.com/en-us/article/Upload-on-premises-content-to-SharePoint-Online-using-PowerShell-cmdlets-555049c6-15ef-45a6-9a1f-a1ef673b867c?ui=en-US&amp;rs=en-US&amp;ad=US) (para migrar la información en OneDrive para la empresa). 
  
|**Pro en línea**|**En línea Con**|
|:-----|:-----|
|Microsoft proporciona hardware SPO y toda la administración de hardware.  <br/> |Características disponibles pueden ser diferentes entre SharePoint Server local y SPO.  <br/> |
|Es el administrador global de su suscripción y puede asignar a administradores a sitios SPO.  <br/> |Algunas acciones disponibles para un administrador de granja de servidores en SharePoint Server local no existen (o no son necesarios) en la función de administrador de SharePoint en Office 365, pero la administración de SharePoint, son locales para administración de la colección de sitios y la propiedad de sitio su org.  <br/> |
|Microsoft aplica revisiones, corrige y se actualiza para hardware y software (incluidos los servidores de SQL Server en el que SharePoint Online se ejecuta) subyacente.  <br/> |Debido a que no hay ningún acceso al sistema de archivos subyacente en el servicio, algunas personalizaciones están limitados.  <br/> |
|Microsoft publica [Los acuerdos de nivel de servicio](https://go.microsoft.com/fwlink/?linkid=843153) y se mueve rápidamente resolver incidentes de nivel de servicio.  <br/> |Otras opciones de recuperación y copia de seguridad y restauración son automáticas por el servicio en SharePoint Online: las copias de seguridad se sobrescriben si no se utilizan.  <br/> |
|Las pruebas de seguridad y ajuste del rendimiento de servidor se llevar a cabo de forma continuada en el servicio de Microsoft.  <br/> |Cambios realizados en la interfaz de usuario y otro SharePoint características se instalan de forma que el servicio y es posible que se activan o desactivan.  <br/> |
|Office 365 cumple los estándares del sector muchas: [Cumplimiento de normas de Office 365](https://go.microsoft.com/fwlink/?linkid=843165).  <br/> |[FastTrack](https://go.microsoft.com/fwlink/?linkid=518597) asistencia para la migración es limitado.  <br/> Gran parte de la actualización será manual o a través de la API de migración de SPO se describe en [SharePoint Online y guía básica de contenido de OneDrive para la migración](https://go.microsoft.com/fwlink/?linkid=843184).  <br/> |
|Los ingenieros de soporte técnico de Microsoft ni a los empleados en el centro de datos tienen acceso sin restricciones admin a su suscripción.  <br/> |Puede haber costos adicionales si la infraestructura de hardware necesita actualizarse para admitir la versión más reciente de SharePoint, o si una granja de servidores secundaria es necesario para la actualización.  <br/> |
|Los socios pueden ayudarle con el trabajo único de migrar los datos a SharePoint Online.  <br/> |No todos los cambios en SharePoint Online están dentro del control. Después de la migración, las diferencias de diseño en los menús, bibliotecas y otras características pueden afectar temporalmente a facilidad de uso.  <br/> |
|Los productos en línea se actualizan automáticamente a través del servicio de lo que significa que aunque pueden dejar de utilizar las características, no hay ningún true final del ciclo de vida de soporte técnico.  <br/> |Hay un final del ciclo de vida de soporte técnico para SharePoint Server (o SharePoint Foundation), así como los servidores SQL subyacentes.  <br/> |
   
Si ha decidido crear un nuevo sitio de Office 365 y manualmente migrar datos a él como sea necesario, se puede examinar en su derecho de opciones de Office 365:
  
[Opciones de planes de Office 365](https://go.microsoft.com/fwlink/?linkid=843151)
  
### <a name="upgrade-sharepoint-server-on-premises"></a>Actualizar el servidor de SharePoint local

Como de la versión más reciente del producto de local de SharePoint (SharePoint Server 2016), actualizaciones de los servidores de SharePoint deben ir *en serie* , que significa que no hay ninguna forma de actualizar desde SharePoint Server 2010 para SharePoint Server 2016, directamente. 
  
|||
|:-----|:-----|
||Ruta de acceso de actualización en serie ***: SharePoint Server 2010 **\>** SharePoint Server 2013 **\>** 2016 de SharePoint Server |
   
Si opta por seguir la ruta de acceso completa de SharePoint 2010 para SharePoint Server 2016, esto llevará tiempo y planeación. Las actualizaciones relacionadas con un costo en términos de hardware actualizado (tenga en cuenta que también se debe actualizar servidores SQL Server), software y administración. Además, las personalizaciones necesite se actualizan o incluso abandonado. Asegúrese de que recopilar notas en todas las personalizaciones críticas antes de actualizar la granja de servidores de SharePoint.
  
> [!NOTE]
> Es posible mantener el final de la granja de servidores de soporte técnico de SharePoint 2010, instalar una granja de servidores de SharePoint Server 2016 en hardware nuevo (de manera que las granjas de servidores independientes se ejecutan en paralelo) y, a continuación, planear y ejecutar una migración manual de contenido (para descargar y volver a cargar contenido, para ejemplo). Hay posibles dificultades para estos movimientos manuales (como documentos procedentes de 2010 tener una cuenta modificado última actual con el alias de la cuenta que realiza el movimiento manual), y algunos trabajo debe llevarse a cabo antes de tiempo (volver a crear sitios, subsitios, permisos y estructuras de lista). Es un buen momento para tener en cuenta lo datos que puede mover en almacenamiento de información o ya no se necesitan. Esto puede reducir el impacto de la migración. En ambos casos, limpie su antes de su entorno de actualización. ¡Estar seguro de la granja de servidores existente es funcional antes de actualizar y (seguro) antes de retirar! 
  
Recuerde que debe revisar las **rutas de actualización admitidas y no admitidas**: 
  
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843157)
    
Si dispone de **las personalizaciones**, es fundamental que tener un plan de la actualización para cada paso en la ruta de acceso de migración: 
  
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843160)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843162)
    
|**Local Pro**|**Local Con**|
|:-----|:-----|
|Control total de todos los aspectos de la granja de servidores de SharePoint (y SQL de TI), desde el hardware del servidor de copia de seguridad.  <br/> |Todos los saltos y correcciones son la responsabilidad de la compañía (pero puede integrarse pago Support Microsoft si no es el precio del producto final de soporte técnico):  <br/> |
|Conjunto completo de características del servidor de SharePoint local con la opción para conectarse a la granja de servidores local en una suscripción de SharePoint Online a través de híbrida.  <br/> |Actualización, revisiones, las revisiones de seguridad, las actualizaciones de hardware y todo el mantenimiento de la granja de servidores SQL SharePoint Server y de TI son administrados local.  <br/> |
|Acceso total para mayor las opciones de personalización que con SharePoint Online.  <br/> |[Los estándares de cumplimiento de normas compatibles con Office 365](https://go.microsoft.com/fwlink/?linkid=843165) debe estar configurada manualmente local.  <br/> |
|Las pruebas de seguridad y ajuste del rendimiento de servidor, llevar a cabo en sus instalaciones (bajo su control).  <br/> |Office 365 puede hacer que las características disponibles en SharePoint Online que no interactúan con el servidor de SharePoint local  <br/> |
|Los socios pueden ayudarle con la migración de datos a la siguiente versión de SharePoint Server (y versiones posteriores).  <br/> |Los sitios de SharePoint Server no usará automáticamente los certificados [SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167) tal y como se ve en SharePoint Online.  <br/> |
|Control total de las convenciones de nomenclatura, copia de seguridad y restauración y otras opciones de recuperación en el servidor de SharePoint local.  <br/> |Servidor de SharePoint local es sensible a los ciclos de vida del producto.  <br/> |
   
### <a name="upgrade-resources"></a>Recursos de actualización

Comience mediante la comparación de los requisitos de hardware y software. Si no cumple los requisitos básicos para la actualización en hardware actual, que puede significar necesita actualizar el hardware de la granja de servidores o servidores SQL Server en primer lugar, o que es posible que decida mover algunos porcentaje de los sitios para el hardware 'permanentes' de SharePoint Online. Una vez que ha realizado la evaluación, siga las rutas de actualización compatibles y métodos.
  
- **Requisitos de hardware y software para**: 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843206) | [2016 de SharePoint Server](https://go.microsoft.com/fwlink/?linkid=843207)
    
- **Restricciones de software y límites de**: 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843247) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843248) | [2016 de SharePoint Server](https://go.microsoft.com/fwlink/?linkid=843249)
    
- **La introducción del proceso de actualización para**: 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843251) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843252) | [2016 de SharePoint Server](https://go.microsoft.com/fwlink/?linkid=843359)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-sharepoint-server-on-premises"></a>Crear una solución híbrida de SharePoint entre SharePoint Online y SharePoint Server local

Otra opción (uno que puede ser la mejor de locales y online mundos para algunos migración necesita) es un híbrido, puede conectar SharePoint Server 2013 o granjas de servidores de 2016 a SharePoint Online para crear un entorno híbrido de SharePoint: [Aprenda sobre soluciones híbridas de SharePoint ](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx).
  
Si decide que un granja de servidores de SharePoint híbrido es su objetivo de migración, asegúrese de planear qué sitios y los usuarios deben mover a online, y que deben permanecer local. Una revisión y clasificación de contenido de la granja de servidores de SharePoint (determinar qué datos están alta, Media o baja impacto a su compañía) pueden ser útiles para tomar esta decisión. Es posible que lo único que necesita compartir con SharePoint Online esté cuentas de usuario (a) para inicio de sesión y (b) el índice de búsqueda de SharePoint Server--esto no se puede borrar hasta que examine cómo se usan los sitios. Si su compañía más adelante decide migrar todo su contenido a SharePoint Online, puede mover todas las demás cuentas y datos en línea y retirar la granja de servidores local y administración de la granja de servidores de SharePoint se realizará a través de Office 365 consolas a partir de ese momento.
  
Asegúrese de familiarizarse con los tipos existentes de híbrido y cómo configurar la conexión entre la granja de servidores de SharePoint local y su suscripción de Office 365.
  
Es una buena manera de ver cómo funciona una granja de servidores de SharePoint híbrido mediante la creación de un [entorno de desarrollo y prueba de Office 365](https://go.microsoft.com/fwlink/?linkid=843152). Una vez que tiene una versión de prueba o adquirido la suscripción a Office 365, estará en el camino a la creación de la colecciones de sitios, sitios Web y bibliotecas de documentos en SharePoint Online para que pueda migrar datos (ya sea manualmente, por uso de la API de migración, o - si desea migrar mi Sitio de contenido a OneDrive para la empresa - mediante el Asistente para la híbrida).
  
> [!NOTE]
> Recuerde que la granja de servidores de SharePoint Server 2010 en primer lugar tendrá que actualizarse, local, para SharePoint Server 2013 o SharePoint Server 2016 para usar la opción híbrida. SharePoint Foundation 2010 y SharePoint Foundation 2013 no pueden crear conexiones híbrida con SharePoint Online. 
  
## <a name="related-topics"></a>Temas relacionados

[Recursos para ayudar a realiza una actualización de Office 2007 o 2010 los clientes y servidores](upgrade-from-office-2010-servers-and-products.md)
  
[Overview of the upgrade process from SharePoint 2010 to SharePoint 2013](https://technet.microsoft.com/en-us/library/mt493301%28v=office.16%29.aspx)
  
[Procedimientos recomendados para actualizar de SharePoint 2010 a SharePoint 2013](https://technet.microsoft.com/en-us/library/mt493305%28v=office.16%29.aspx)
  
[Solucionar problemas de actualización de bases de datos en SharePoint 2013](https://go.microsoft.com/fwlink/?linkid=843195)
  
[Busque Microsoft Partners ayudar con la actualización](https://go.microsoft.com/fwlink/?linkid=841249)
  
[Directiva de servicio del producto actualizada para SharePoint 2013](https://technet.microsoft.com/en-us/library/mt493253%28v=office.16%29.aspx)
  
[Directiva de servicio del producto actualizada para SharePoint Server 2016](https://technet.microsoft.com/en-us/library/mt782882%28v=office.16%29.aspx)
  

