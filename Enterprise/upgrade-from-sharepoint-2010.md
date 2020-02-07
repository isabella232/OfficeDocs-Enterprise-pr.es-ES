---
title: Actualización desde SharePoint 2010
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 08/21/2019
audience: ITPro
ms.topic: conceptual
ms.prod: office-online-server
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
search.appverid:
- MET150
- WSU140
- OSU140
ms.assetid: 985a357f-6db7-401f-bf7a-1bafdf1f312c
f1.keywords:
- NOCSH
description: La compatibilidad finaliza para SharePoint 2010 y SharePoint Server 2010 finaliza el 13 de octubre de 2020. Use este artículo como guía para actualizar a SharePoint Online o a una versión más reciente de SharePoint Server local.
ms.openlocfilehash: 51c372bf2d96c245223a1ea3776f889e60bf4491
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841057"
---
# <a name="upgrading-from-sharepoint-2010"></a>Actualización desde SharePoint 2010

*Este artículo se aplica tanto a Office 365 Enterprise como a Microsoft 365 Enterprise.*

Microsoft SharePoint 2010 y SharePoint Server 2010 llegarán a fin de soporte el **13 de octubre de 2020**. En este artículo se detallan los recursos que le ayudarán a migrar los datos existentes de SharePoint Server 2010 a SharePoint Online en Office 365 o a actualizar el entorno local de SharePoint Server 2010.
  
## <a name="what-is-end-of-support"></a>¿Qué es el final del soporte técnico?

Cuando el software de SharePoint Server 2010 y SharePoint Foundation 2010 alcanza el final de su ciclo de vida de soporte técnico (el tiempo durante el cual Microsoft proporciona nuevas características, correcciones de errores, correcciones de seguridad, etc.), se denomina "fin del soporte" del software, o a veces, su "jubilación". Una vez finalizado el soporte técnico (o EOS) de un producto, ningún hecho se cierra o deja de funcionar; sin embargo, al final del soporte técnico de software, Microsoft ya no ofrece:
  
- Soporte técnico para los problemas que pueden surgir;
    
- Correcciones de errores para problemas detectados y que pueden afectar a la estabilidad y la usabilidad del servidor;
    
- Revisiones de seguridad para las vulnerabilidades detectadas y que pueden hacer que el servidor sea vulnerable a las infracciones de seguridad;
    
- Las actualizaciones de zona horaria.
    
Esto significa que no se enviarán más actualizaciones, parches ni correcciones para el producto (incluidas las revisiones o correcciones de seguridad) y el soporte técnico de Microsoft se desplazará completamente a las versiones más recientes. Como fin de soporte para enfoques de SharePoint Server 2010, debe aprovechar las oportunidades para recortar los datos que ya no necesita antes de actualizar el producto y/o migrar los datos importantes.
  
> [!NOTE]
> Un ciclo de vida de software suele durar diez años a partir de la fecha de lanzamiento inicial del producto. Puede buscar proveedores de [soluciones de Microsoft](https://go.microsoft.com/fwlink/?linkid=841249) que puedan ayudarle a actualizar a la siguiente versión del software o a la migración de Office 365 (o ambas). Asegúrese de que está al tanto de las fechas de fin de soporte en las tecnologías subyacentes fundamentales, sobre todo de la versión de SQL Server que está usando con SharePoint. Vea la [Directiva de ciclo de vida fijo](https://support.microsoft.com/help/14085) para comprender el ciclo de vida del producto en detalle.
  
## <a name="what-are-my-options"></a>¿Qué opciones tengo?

En primer lugar, Compruebe la fecha en la que finaliza el soporte técnico del [sitio de ciclo de vida del producto](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010). A continuación, asegúrese de planear su tiempo de actualización o migración con conocimiento de esta fecha. Recuerde que el producto *no dejará de funcionar* en la fecha que aparece en la lista, y que puede continuar con su uso, pero que, dado que la instalación ya no será revisada después de esa fecha, querrá una estrategia que le ayude a realizar una transición más eficaz a la siguiente versión del producto. 
  
Esta matriz ayuda a trazar un curso en lo referente a la migración de características de productos y datos de usuario:
  
|**Fin del producto de soporte**|**Good**|**Procedimientos**|
|:-----|:-----|:-----|
|SharePoint Server 2010  <br/> |SharePoint Server 2013 (local)  <br/> |SharePoint Online  <br/> |
||SharePoint Server 2013 híbrido con SharePoint Online  <br/> |SharePoint Server 2016 (local)  <br/> |
|||Búsqueda híbrida en la nube de SharePoint  <br/> |
   
Si elige opciones en el extremo inferior de la escala (buenas opciones), deberá comenzar a planear otra actualización inmediatamente después de que finalice la migración de SharePoint Server 2010. 

Estas son las tres rutas que puede realizar para evitar la finalización de la compatibilidad con SharePoint Server 2010.

![Rutas de actualización de SharePoint Server 2010](./media/upgrade-from-sharepoint-2010/upgrade-from-sharepoint-2010-paths.png)

>[!Note]
>El final del soporte técnico para SharePoint Server 2010 y SharePoint Foundation 2010 están programados para el 13 de octubre de 2020, pero tenga en *cuenta* que siempre debe comprobar el [sitio de ciclo de vida del producto](https://support.microsoft.com/lifecycle) en busca de las fechas más recientes.
>

  
## <a name="where-should-i-go-next"></a>¿Dónde debo ir ahora?

SharePoint Server 2013 y SharePoint Foundation 2013 se pueden instalar localmente en sus propios servidores. De lo contrario, puede usar SharePoint Online, que es un servicio en línea que forma parte de Microsoft Office 365. Puede elegir entre:
  
- Migrar a SharePoint Online
    
- Actualización de SharePoint Server o SharePoint Foundation local
    
- Hacer lo anterior
    
- Implementar una solución [híbrida de SharePoint](https://docs.microsoft.com/sharepoint/hybrid/hybrid) 
    
Tenga en cuenta los costos ocultos asociados con el mantenimiento de una granja de servidores en el futuro, el mantenimiento o la migración de personalizaciones, y la actualización del hardware que depende de SharePoint Server. Si tiene constancia y tiene en cuenta todas estas, será más fácil continuar con la actualización local. De lo contrario, si ejecuta la granja de servidores de SharePoint heredados sin una gran personalización, puede beneficiarse de una migración planeada a SharePoint Online. También es posible que, para su entorno de SharePoint Server local, pueda optar por colocar algunos datos en SharePoint Online para reducir la cantidad de administración de hardware que implica que todos los datos de la implementación local se conserven. Es posible que sea más económico mover algunos datos en SharePoint Online.
  
> [!NOTE]
> Los administradores de SharePoint pueden [crear una suscripción de Office 365](https://go.microsoft.com/fwlink/?linkid=843152), configurar un nuevo sitio de SharePoint Online de marca y, a continuación, alejarse de sharepoint Server 2010, sin problemas, tomando solo los documentos más esenciales en los sitios de SharePoint Online nuevos. Desde allí, cualquier dato restante se puede purgar del sitio de SharePoint Server 2010 en archivos locales. 
  
|**SharePoint Online**|**SharePoint Server local**|
|:-----|:-----|
|Costo elevado en el tiempo (planificación/ejecución/comprobación)  <br/> |Costo elevado en el tiempo (planificación/ejecución/comprobación)  <br/> |
|Menor coste de fondos (no hay compras de hardware)  <br/> |Costo mayor en fondos (adquisiciones de hardware)  <br/> |
|Costo de tiempo único en la migración  <br/> |Costo de tiempo único repetido por migración futura  <br/> |
|Bajo costo total de propiedad/mantenimiento  <br/> |Costo total de propiedad/mantenimiento elevado  <br/> |
   
Al migrar a Office 365, el cambio único tendrá un costo más pesado en el tiempo dedicado a la planeación, ya que es la primera vez que se organizan los datos y se decide qué se va a llevar a la nube y qué se debe dejar atrás. Sin embargo, una vez que se han migrado los datos, las actualizaciones serán automáticas desde ese momento, a medida que ya no necesitará administrar las actualizaciones de hardware y software, y el tiempo de actividad de la granja de servidores estará respaldado por un contrato de nivel de servicio ([SLA](https://go.microsoft.com/fwlink/?linkid=843153)) de Microsoft.
  
### <a name="migrate-to-sharepoint-online"></a>Migrar a SharePoint Online

Asegúrese de que SharePoint Online ofrece todas las características que necesita revisando la [Descripción](https://docs.microsoft.com/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-service-description)de su servicio.
  
Actualmente no hay ningún medio que pueda migrar directamente de SharePoint Server 2010 (o SharePoint Foundation 2010) a SharePoint Online, por lo que gran parte del trabajo es manual. Esto le ofrece la oportunidad de archivar y eliminar los datos y los sitios que ya no son necesarios antes del traslado. Puede archivar otros datos en el almacenamiento. Recuerde también que ni SharePoint Server 2010 ni SharePoint Foundation 2010 dejarán de funcionar al final del soporte técnico, por lo que los administradores pueden tener un período durante el cual SharePoint aún se está ejecutando si los clientes olvidan mover algunos de sus datos.
  
Si actualiza a SharePoint Server 2013 o SharePoint Server 2016 y decide colocar datos en SharePoint Online, su traslado también podría implicar el uso de la [API de migración de SharePoint](https://support.office.com/article/Upload-on-premises-content-to-SharePoint-Online-using-PowerShell-cmdlets-555049c6-15ef-45a6-9a1f-a1ef673b867c?ui=en-US&amp;rs=en-US&amp;ad=US) (para migrar información a OneDrive para la empresa). 
  
|**Ventajas de SharePoint Online**|**Inconvenientes de SharePoint Online**|
|:-----|:-----|
|Microsoft proporciona el hardware de SPO y toda la administración de hardware.  <br/> |Las características disponibles pueden ser diferentes entre la implementación local de SharePoint Server y SPO.  <br/> |
|Usted es el administrador global de su suscripción y puede asignar administradores a los sitios de SPO.  <br/> |Algunas acciones disponibles para un administrador de la granja de servidores en SharePoint Server local no existen (o no son necesarias) en el rol de administrador de SharePoint en Office 365, pero la administración de SharePoint, la administración de colecciones de sitios y la propiedad del sitio son locales para su organización.  <br/> |
|Microsoft aplica revisiones, correcciones y actualizaciones al hardware y software subyacentes (incluidos los servidores SQL en los que se ejecuta SharePoint Online).  <br/> |Como no hay acceso al sistema de archivos subyacente en el servicio, algunas personalizaciones son limitadas.  <br/> |
|Microsoft publica [contratos de nivel de servicio](https://go.microsoft.com/fwlink/?linkid=843153) y se mueve rápidamente para resolver los incidentes de nivel de servicio.  <br/> |La copia de seguridad y restauración y otras opciones de recuperación están automatizadas por el servicio en SharePoint Online: las copias de seguridad se sobrescriben si no se usan.  <br/> |
|Las pruebas de seguridad y el ajuste del rendimiento del servidor se llevan a cabo de manera continua en el servicio de Microsoft.  <br/> |El servicio instala los cambios en la interfaz de usuario y en otras características de SharePoint, por lo que es posible que deban activarse o desactivarse.  <br/> |
|Office 365 cumple muchos estándares del sector: [office 365 Compliance](https://go.microsoft.com/fwlink/?linkid=843165).  <br/> |La asistencia de [FastTrack](https://go.microsoft.com/fwlink/?linkid=518597) para la migración es limitada.  <br/> La mayor parte de la actualización será manual o a través de la API de migración de SPO que se describe en la [Guía de contenido de migración de SharePoint Online y OneDrive](https://go.microsoft.com/fwlink/?linkid=843184).  <br/> |
|Ni los ingenieros de soporte técnico de Microsoft ni los empleados en el centro de administración de la sesión tienen acceso de administrador sin restricciones a su suscripción.  <br/> |Puede haber costos adicionales si es necesario actualizar la infraestructura de hardware para que sea compatible con la versión más reciente de SharePoint o si se requiere una granja secundaria para la actualización.  <br/> |
|Los proveedores de soluciones pueden ayudarle con el trabajo único de migrar los datos a SharePoint Online.  <br/> |No todos los cambios en SharePoint Online se encuentran en el control. Después de la migración, las diferencias de diseño en menús, bibliotecas y otras características pueden afectar temporalmente al uso.  <br/> |
|Los productos en línea se actualizan automáticamente en el servicio, lo que significa que, aunque las características puedan dejar de estar en desuso, no hay un verdadero fin del ciclo de vida de soporte técnico.  <br/> |Hay un fin del ciclo de vida de soporte técnico para SharePoint Server (o SharePoint Foundation), así como para los servidores SQL subyacentes.  <br/> |
   
Si ha decidido crear un nuevo sitio de Office 365 y migrar los datos de forma manual según sea necesario, puede mirar sus opciones de plan de [office 365](https://go.microsoft.com/fwlink/?linkid=843151).
  

  
### <a name="upgrade-sharepoint-server-on-premises"></a>Actualizar SharePoint Server local

A partir de la última versión del producto local de SharePoint (SharePoint Server 2019), las actualizaciones de SharePoint Server deben realizarse en *serie*, lo que significa que no hay forma de actualizar de sharepoint Server 2010 a sharepoint Server 2016 o a SharePoint 2019, directamente. 
  
|||
|:-----|:-----|
||Ruta de actualización en serie * * * *: SharePoint **\>** Server 2010 sharepoint **\>** server 2013 SharePoint Server 2016 |
   
Si elige seguir la ruta de acceso completa de SharePoint 2010 a SharePoint Server 2016, el tiempo y la planeación serán prolongados. Las actualizaciones implican un costo en términos de hardware actualizado (tenga en cuenta que también deben actualizarse los servidores SQL), el software y la administración. Además, puede ser necesario actualizar las personalizaciones o incluso abandonarlas. Asegúrese de recopilar notas en todas las personalizaciones críticas antes de actualizar la granja de servidores de SharePoint Server.
  
> [!NOTE]
> Es posible mantener su extremo de soporte de la granja de servidores de SharePoint 2010, instalar una granja de servidores de SharePoint Server 2016 en hardware nuevo (por lo que las granjas de servidores independientes se ejecutan en paralelo) y, a continuación, planear y ejecutar una migración manual del contenido (para descargar y volver a cargar contenido, para ejemplo). Existen posibles problemas en estos movimientos manuales (por ejemplo, los documentos que provienen de 2010 con una última cuenta modificada con el alias de la cuenta que realiza el traslado manual) y algunos trabajos deben realizarse antes de tiempo (volver a crear sitios, subsitios, permisos y enumerar estructuras). Es un buen momento tener en cuenta qué datos se pueden mover al almacenamiento o ya no se necesitan. Esto puede reducir el impacto de la migración. En cualquier caso, limpie su entorno antes de actualizar. Asegúrese de que la granja de servidores existente es funcional antes de realizar la actualización y, (para asegurarse) antes de su retiro. 
  
Recuerde revisar las **rutas de actualización admitidas y no admitidas**: 
  
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843157)
    
Si tiene **personalizaciones**, es fundamental que disponga de un plan de actualización para cada paso de la ruta de migración: 
  
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843160)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843162)
    
|**Ventajas locales**|**Desventaja local**|
|:-----|:-----|
|Control total de todos los aspectos de la granja de servidores de SharePoint (y su SQL), desde el hardware del servidor hacia arriba.  <br/> |Todos los descansos y las correcciones son responsabilidad de la empresa (pero usted puede participar en el soporte de Microsoft si su producto no está al final del soporte técnico):  <br/> |
|Conjunto completo de características de SharePoint Server local con la opción de conectar la granja de servidores local con una suscripción de SharePoint Online a través de un híbrido.  <br/> |La actualización, las revisiones, las revisiones de seguridad, las actualizaciones de hardware y todo el mantenimiento de SharePoint Server y su granja de servidores SQL se administran de forma local.  <br/> |
|Acceso completo para obtener más opciones de personalización que con SharePoint Online.  <br/> |Los [estándares de cumplimiento admitidos por Office 365](https://go.microsoft.com/fwlink/?linkid=843165) deben configurarse manualmente de forma local.  <br/> |
|Pruebas de seguridad y ajuste del rendimiento del servidor, realizadas en sus instalaciones (bajo su control).  <br/> |Office 365 puede poner características a disposición de SharePoint Online que no interoperen con SharePoint Server local  <br/> |
|Los proveedores de soluciones pueden ayudarle a migrar datos a la próxima versión de SharePoint Server (y versiones posteriores).  <br/> |Los sitios de SharePoint Server no usarán automáticamente los certificados [SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167) como se ve en SharePoint Online.  <br/> |
|Control total de las convenciones de nomenclatura, copia de seguridad y restauración, y otras opciones de recuperación en SharePoint Server local.  <br/> |SharePoint Server local es sensible a los ciclos de vida de los productos.  <br/> |
   
### <a name="upgrade-resources"></a>Recursos de actualización

Comience por comparar los requisitos de hardware y software. Si no cumple los requisitos básicos para la actualización en el hardware actual, esto puede significar que debe actualizar en primer lugar el hardware de la granja de servidores o de SQL Server, o que puede decidir mover el porcentaje de sus sitios al hardware de "perennes" de SharePoint Online. Una vez que haya realizado la evaluación, siga las rutas de actualización y los métodos admitidos.
  
- **Requisitos de hardware y software para**: 
    
    [](https://go.microsoft.com/fwlink/?linkid=843204) | SharePoint Server 2010 SharePoint[Server 2013](https://go.microsoft.com/fwlink/?linkid=843206) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843207)
    
- Límites **de software para**: 
    
    [](https://go.microsoft.com/fwlink/?linkid=843247) | SharePoint Server 2010 SharePoint[Server 2013](https://go.microsoft.com/fwlink/?linkid=843248) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843249)
    
- **Información general sobre el proceso de actualización para**: 
    
    [](https://go.microsoft.com/fwlink/?linkid=843251) | SharePoint Server 2010 SharePoint[Server 2013](https://go.microsoft.com/fwlink/?linkid=843252) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843359)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-sharepoint-server-on-premises"></a>Crear una solución híbrida de SharePoint entre SharePoint Online y SharePoint Server local

Otra opción (que puede ser la mejor de los mundos locales y en línea para algunas necesidades de migración) es un híbrido, puede conectar granjas de servidores de SharePoint Server 2013 o 2016 o 2019 a SharePoint Online para crear un entorno híbrido de SharePoint: [obtenga información sobre las soluciones híbridas de SharePoint](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx).
  
Si decide que una granja de servidores híbrida de SharePoint Server es su objetivo de migración, asegúrese de planear los sitios y usuarios a los que se debe mover en línea y que deben permanecer de forma local. Una revisión y una clasificación del contenido de la granja de servidores de SharePoint Server (determinar qué datos son de alto, medio o bajo impacto en su compañía) pueden ser útiles para tomar esta decisión. Es posible que lo único que debe compartir con SharePoint Online sea (a) las cuentas de usuario para iniciar sesión y (b) el índice de búsqueda de SharePoint Server, que puede no ser claro hasta que vea cómo se usan los sitios. Si su compañía decide posteriormente migrar todo el contenido a SharePoint Online, puede mover todas las cuentas y datos restantes en línea y retirar la granja de servidores local, y la administración o administración de la granja de servidores de SharePoint se realizará a través de las consolas de Office 365 a partir de ese momento.
  
Asegúrese de familiarizarse con los tipos existentes de híbrido y cómo configurar la conexión entre su granja de SharePoint local y su suscripción a Office 365.
  
Una buena forma de ver cómo funciona una granja de servidores híbrida de SharePoint consiste en crear un [entorno de desarrollo y pruebas de Office 365](https://go.microsoft.com/fwlink/?linkid=843152). Una vez que tenga una suscripción a la versión de prueba de Office 365, estará en la forma de crear las colecciones de sitios, los webs y las bibliotecas de documentos en SharePoint Online a los que puede migrar datos (ya sea manualmente, mediante la API de migración, o si desea migrar mi Contenido del sitio en OneDrive para la empresa mediante el asistente híbrido).
  
> [!NOTE]
> Recuerde que la granja de servidores de SharePoint Server 2010 primero debe actualizarse, local, a SharePoint Server 2013 o a SharePoint Server 2016 para usar la opción híbrido. SharePoint Foundation 2010 y SharePoint Foundation 2013 no pueden crear conexiones híbridas con SharePoint Online. 

## <a name="summary-of-options-for-office-2010-client-and-servers-and-windows-7"></a>Resumen de opciones para el cliente y los servidores de Office 2010 y Windows 7

Para obtener un resumen visual de las opciones de actualización, migración y movimiento a la nube para los clientes y servidores de Office 2010 y Windows 7, consulte el [póster de final de soporte técnico](./media/upgrade-from-office-2010-servers-and-products/Office2010Windows7EndOfSupport.pdf).

![](./media/upgrade-from-office-2010-servers-and-products/office2010-windows7-end-of-support.png)

Este póster de una página es una forma rápida de comprender las diversas rutas que puede realizar para evitar que los productos de cliente y servidor de Office 2010 y Windows 7 lleguen al final del soporte técnico, con las rutas preferidas y la compatibilidad con la opción en Microsoft 365 Enterprise resaltado.

También puede [Descargar](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/enterprise/media/migration-microsoft-365-enterprise-workload/Office2010Windows7EndOfSupport.pdf) este póster e imprimirlo en formato carta, legal o tabloide (11 x 17).
        
## <a name="related-topics"></a>Temas relacionados

[Recursos para ayudarle a actualizar desde servidores y clientes de Office 2007 o 2010](upgrade-from-office-2010-servers-and-products.md)
  
[Overview of the upgrade process from SharePoint 2010 to SharePoint 2013](https://technet.microsoft.com/library/mt493301%28v=office.16%29.aspx)
  
[Procedimientos recomendados para actualizar de SharePoint 2010 a SharePoint 2013](https://technet.microsoft.com/library/mt493305%28v=office.16%29.aspx)
  
[Solucionar problemas de actualización de bases de datos en SharePoint 2013](https://go.microsoft.com/fwlink/?linkid=843195)
  
[Buscar proveedores de soluciones de Microsoft para ayudarle con la actualización](https://go.microsoft.com/fwlink/?linkid=841249)
  
[Directiva de servicio del producto actualizada para SharePoint 2013](https://technet.microsoft.com/library/mt493253%28v=office.16%29.aspx)
  
[Directiva de servicio del producto actualizada para SharePoint Server 2016](https://technet.microsoft.com/library/mt782882%28v=office.16%29.aspx)
  

