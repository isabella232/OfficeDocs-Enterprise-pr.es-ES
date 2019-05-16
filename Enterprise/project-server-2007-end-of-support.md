---
title: Plan de fin del soporte técnico de Project Server 2007
ms.author: efrene
author: efrene
manager: laurawi
ms.date: 1/31/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: IT_ProjectAdmin
search.appverid:
- MET150
- ZPJ120
- PJU120
- PJW120
ms.assetid: d379018f-72b7-4284-b40a-6c23c8ae38fe
description: El 10 de octubre de 2017, se finalizó la compatibilidad con Project Server 2007, Project Portfolio Server y Project 2007. Use este artículo para planear la actualización ahora.
ms.openlocfilehash: 620b5ae3e23c3b4bdba9c429def81eebedbd32a3
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071056"
---
# <a name="project-server-2007-end-of-support-roadmap"></a>Plan de fin del soporte técnico de Project Server 2007

El soporte técnico está finalizado para los servidores y aplicaciones de Office 2007 en 2017 y debe tener en cuenta los planes para la migración. Si actualmente usa Project Server 2007, tenga en cuenta que estos productos relacionados tendrán las siguientes fechas de finalización de soporte:
  
|**Producto**|**fecha de finalización del soporte técnico**|
|:-----|:-----|
|Project Server 2007  <br/> |10 de octubre de 2017  <br/> |
|Project Portfolio Server 2007  <br/> |10 de octubre de 2017  <br/> |
|Proyecto 2007 estándar  <br/> |10 de octubre de 2017  <br/> |
|Proyecto 2007 Professional  <br/> |10 de octubre de 2017  <br/> |
   
Para obtener más información acerca de los servidores de Office 2007 que alcanzan la jubilación, consulte [upgrade from office 2007 Servers and Client Products](upgrade-from-office-2007-servers-and-products.md).
  
## <a name="what-does-end-of-support-mean"></a>¿Qué significa el fin de soporte?

Project Server, al igual que casi todos los productos de Microsoft, tiene un ciclo de vida de soporte técnico durante el cual ofrecemos nuevas características, correcciones de errores, correcciones de seguridad, etc. Este ciclo de vida suele durar 10 años a partir de la fecha de lanzamiento inicial del producto y el final de este ciclo de vida se conoce como el final del soporte técnico del producto. Como Project Server 2007 ha llegado al final del soporte técnico el 10 de octubre de 2017, Microsoft dejará de proporcionar:
  
- Soporte técnico para los problemas que pueden surgir.
    
- Correcciones de errores para problemas detectados y que pueden afectar a la estabilidad y la usabilidad del servidor.
    
- Revisiones de seguridad para las vulnerabilidades detectadas y que pueden hacer que el servidor sea vulnerable a las infracciones de seguridad.
    
- Las actualizaciones de zona horaria.
    
La instalación de Project Server 2007 seguirá ejecutándose después de esta fecha. Sin embargo, debido a los cambios mencionados anteriormente, se recomienda encarecidamente que migre de Project Server 2007 lo antes posible.
  
## <a name="what-are-my-options"></a>¿Qué opciones tengo?

Si usa Project Server 2007, debe explorar las opciones de migración, que son:
  
- Migrar a Project online
    
- Migre a una versión local más reciente de Project Server (preferiblemente Project Server 2016).
    
|**Por qué preferiría migrar a Project online**|**Por qué preferiría migrar a Project Server 2016**|
|:-----|:-----|
| Tengo usuarios móviles.  <br/>  Los costos de migración son una gran preocupación (hardware, software, horas y esfuerzo de implementación, etc.).  <br/>  Después de la migración, los costos de mantenimiento de mi entorno son una gran preocupación (por ejemplo, actualizaciones automáticas, tiempo de actividad garantizado, etc.).  <br/> | Las reglas de negocios delimitan el funcionamiento de mi empresa en la nube.  <br/>  Necesito el control de las actualizaciones de mi entorno.  <br/> |
   
> [!NOTE]
> Para obtener más información acerca de las opciones para mover desde los servidores de Office 2007, vea [recursos para ayudarle a actualizar desde office 2007 servidores y clientes](upgrade-from-office-2007-servers-and-products.md). Tenga en cuenta que Project Server no admite una configuración híbrida, ya que Project Server y Project online no pueden compartir el mismo grupo de recursos. 
  
## <a name="important-considerations-you-need-to-make-when-planning-to-migrate-from-project-server-2007"></a>Consideraciones importantes que debe tener en cuenta al planear la migración desde Project Server 2007

Debe tener en cuenta lo siguiente al planear la migración desde Project Server 2007:
  
- **Obtener ayuda de un socio de Microsoft** : la actualización desde Project Server 2007 puede ser un reto y requiere una gran preparación y planeación. Puede ser especialmente difícil si no es el que se va a instalar y configurar originalmente Project Server 2007. Afortunadamente, hay socios de Microsoft que puede pasar a la persona que lo hace por un testamento vital, independientemente de si planea migrar a Project Server 2016 o a Project online. Puede buscar un socio de Microsoft para ayudarle con la migración en el [centro de Partners de Microsoft](https://go.microsoft.com/fwlink/p/?linkid=841249). Puede extraer una lista de todos los socios de Microsoft que tienen experiencia en Project realizando búsquedas en el término *Gold Project Management y* en la administración de carteras. 
    
- **Planeación de las personalizaciones** : tenga en cuenta que muchas de las personalizaciones que ha trabajado en el entorno de project Server 2007 podrían no funcionar al migrar a project Server 2016 o a Project online. Existen grandes diferencias en la arquitectura de Project Server entre versiones, así como los sistemas operativos, los servidores de bases de datos y los exploradores Web de cliente que se admiten para trabajar con la versión más reciente. Disponer de un plan sobre cómo probar o volver a crear las personalizaciones según sea necesario en el nuevo entorno. La planeación de la actualización también será una buena oportunidad para comprobar si realmente se necesita una personalización específica mientras avanza. [Crear un plan de personalizaciones actuales durante la actualización a SharePoint 2013 tiene una](https://go.microsoft.com/fwlink/p/?linkid=842061) gran información general sobre la evaluación y la planeación de las personalizaciones actuales durante la actualización. 
    
- La planeación, ejecución y pruebas de actualización del **tiempo y la paciencia** requerirán mucho tiempo y esfuerzo, especialmente si va a actualizar a Project Server 2016. Por ejemplo, si va a migrar de Project Server 2007 a Project Server 2016, primero tendrá que migrar de Project Server 2007 a Project Server 2010 y, a continuación, comprobar los datos y, a continuación, hacer lo mismo al migrar a cada versión sucesiva. Es posible que quiera consultar a un socio de Microsoft para que compare sus costos con sus estimaciones sobre Cuánto tardarán en hacerlo y con qué costos. 
    
## <a name="migrate-to-project-online"></a>Migrar a Project online

Si elige migrar de Project Server 2007 a Project online, puede hacer lo siguiente para migrar manualmente los datos del plan del proyecto:
  
1. Guarde los planes de proyecto de Project Server 2003 en. Formato MPP.
    
2. Con Project Professional 2013, Project Professional 2016 o el cliente de escritorio de Project online, abra cada archivo. MPP y, a continuación, guárdelo y publíquelo en Project online.
    
Puede crear manualmente la configuración de PWA en Project online (por ejemplo, volver a crear los campos personalizados o los calendarios de empresa necesarios). Los socios de Microsoft también pueden ayudarle con esto.
  
Recursos clave:
  
|**Recurso**|**Descripción**|
|:-----|:-----|
|[Introducción a Project Online](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11) <br/> |Cómo configurar y usar Project online.  <br/> |
|[Descripciones del servicio Project online](https://go.microsoft.com/fwlink/p/?linkid=829088) <br/> |Información sobre los distintos planes de Project online que tiene a su disposición.  <br/> |
   
## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>Migrar a una versión local más reciente de Project Server

Aunque creemos que puede lograr el mejor valor y la experiencia del usuario mediante la migración a Project online, también sabemos que algunas organizaciones necesitan mantener los datos de Project en un entorno local. Si opta por mantener los datos de proyecto locales, puede migrar el entorno de Project Server 2007 a Project Server 2010, Project Server 2013 o Project Server 2016.
  
Le recomendamos que migre a Project Server 2016 si no puede migrar a Project online. Project Server 2016 incluye todas las características y los avances incluidos en versiones anteriores de Project Server, y se ajusta mejor a la experiencia disponible en Project online (aunque algunas características solo están disponibles en Project online).
  
Una vez completada cada migración, debe comprobar los datos para asegurarse de que se han migrado correctamente.
  
> [!NOTE]
> Si solo está pensando en migrar a Project Server 2010 si está limitado a una solución local, es importante tener en cuenta que solo hay unos cuantos años de soporte técnico restantes. La fecha de finalización del soporte técnico de Project Server 2010 con Service Pack 2 es la 10/13/2020. Para obtener más información acerca de las fechas de fin de soporte, consulte [Directiva de ciclo de vida del producto de Microsoft](https://go.microsoft.com/fwlink/p/?linkid=842066). 
  
### <a name="how-do-i-migrate-to-project-server-2016"></a>¿Cómo migro a Project Server 2016?

Las diferencias de arquitectura entre Project Server 2007 y Project Server 2016 impiden una ruta de migración directa. Esto significa que tendrá que migrar los datos de Project Server 2007 a la siguiente versión sucesiva de Project Server hasta que actualice a Project Server 2016.
  
Tendrá que hacer lo siguiente para actualizar a Project Server 2016:
  
1. Paso 1: migrar de Project Server 2007 a Project Server 2010.
    
2. Paso 2: migrar desde Project atender 2010 a Project Server 2013.
    
3. Paso 3: migrar de Project Server 2013 a Project Server 2016.
    
Una vez completada cada migración, debe comprobar los datos para asegurarse de que se han migrado correctamente.
  
### <a name="step-1-migrate-from-project-server-2007-to-project-server-2010"></a>Paso 1: migrar de Project Server 2007 a Project Server 2010

Para obtener una descripción completa de lo que debe hacer para actualizar de Project Server 2007 a Project Server 2010, consulte el conjunto de contenido [actualizar a Project server 2010](https://go.microsoft.com/fwlink/p/?linkid=841812) en TechNet. 
  
Recursos clave:
  
|**Recurso**|**Descripción**|
|:-----|:-----|
|[Introducción a la actualización de Project Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841813) <br/> |Obtenga información de alto nivel sobre lo que necesita hacer para actualizar de Project Server 2007 a Project Server 2010.  <br/> |
|[Planeación de la actualización a Project Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841815) <br/> |Consulte las consideraciones de planeación que debe tomar al actualizar de Project Server 2007 a Project Server 2010, incluidos los requisitos del sistema.  <br/> |
   
#### <a name="how-do-i-upgrade"></a>¿Cómo se realiza la actualización?

Mientras que los detalles sobre cómo actualizar se pueden encontrar en el conjunto de contenido [actualizar a Project Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841812) , es importante comprender que hay dos métodos distintos que puede usar para actualizar: 
  
- **Actualización de base de datos adjunta:** Este método solo actualiza el contenido de su entorno y no los valores de configuración. Es necesario si va a actualizar desde Office Project Server 2007 implementado en hardware que solo admite un sistema operativo de servidor de 32 bits. Hay dos tipos de métodos de actualización de base de datos adjunta: 
    
  - **Actualización completa de base** de datos adjunta: migra los datos del proyecto almacenados en las bases de datos de Office project Server 2007, además de los datos del sitio de Microsoft Project Web App (PWA) almacenados en una base de datos de contenido de SharePoint. 
    
  - **Actualización principal de base de datos adjunta** : migra solo los datos del proyecto almacenados en las bases de datos de Project Server. 
    
- **Actualización local**: los datos de configuración de la granja de servidores y todo el contenido de la granja de servidores se actualizan en el hardware existente, en un orden fijo. Cuando inicia el proceso de actualización en el sitio, el programa de instalación pone toda la granja de servidores sin conexión y los sitios web y los sitios de Microsoft Project Web App no están disponibles hasta que finaliza la actualización y, a continuación, el programa de instalación reinicia el servidor. Una vez iniciada la actualización en contexto, no se puede pausar ni revertir a la versión anterior. Se recomienda encarecidamente crear una imagen reflejada de su entorno de producción y realizar la actualización en el lugar a este entorno, y no a su entorno de producción. 
    
Recursos adicionales:
  
- [Superflow para la actualización de Microsoft Project Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841277)
    
- [Migración de Project Server 2007 a Project Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841278)
    
- [Consideraciones sobre la actualización de elementos web de Project Web App](https://go.microsoft.com/fwlink/p/?linkid=841276)
    
- [Kit de desarrollo de software (SDK) de Project](https://go.microsoft.com/fwlink/p/?linkid=841275)
    
### <a name="step-2-migrate-to-project-server-2013"></a>Paso 2: migrar a Project Server 2013

Después de migrar a Project Server 2010 y comprobar que los datos se han migrado correctamente, el siguiente paso consiste en migrar los datos a Project Server 2013.
  
Para obtener una descripción completa de lo que debe hacer para actualizar de Project Server 2010 a Project Server 2013, consulte el conjunto de contenido [actualizar a Project server 2013](https://go.microsoft.com/fwlink/p/?linkid=841822) en TechNet. 
  
Recursos clave:
  
|**Recurso**|**Descripción**|
|:-----|:-----|
|[Información general sobre el proceso de actualización de Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841822) <br/> |Obtenga información de alto nivel sobre lo que necesita hacer para actualizar de Project Server 2010 a Project Server 2013.  <br/> |
|[Planeación de la actualización a Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841823) <br/> |Consulte las consideraciones de planeación que debe tomar al actualizar de Project Server 2010 a Project Server 2013, incluidos los requisitos del sistema.  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>Cosas que debe saber sobre la actualización a esta versión

[What's New in Project Server 2013 upgrade](https://go.microsoft.com/fwlink/p/?linkid=841824) le indica algunos cambios importantes para la actualización de esta versión, el que resulta más notable: 
  
- No hay ninguna actualización local a Project Server 2013. El método de base de datos adjunta es el único método admitido para actualizar de Project Server 2010 a Project Server 2013.
    
- El proceso de actualización no solo convertirá los datos de Project Server 2010 al formato de Project Server 2013, sino que también consolidará las cuatro bases de datos de Project Server 2010 en una sola base de datos de Project Web App.
    
- Tanto SharePoint Server 2013 como Project Server 2013 cambian a la autenticación basada en notificaciones de la versión anterior. Tendrá que tener en cuenta al actualizar si usa la autenticación clásica. Para obtener más información, vea [Migrar del modo clásico a autenticaciones basadas en notificaciones en SharePoint 2013](https://go.microsoft.com/fwlink/p/?linkid=841825).
    
Recursos adicionales:
  
- [Introducción al proceso de actualización a Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841274)
    
- [Actualización de las bases de datos y de las colecciones de sitios de Project Web App (Project Server 2013)](https://go.microsoft.com/fwlink/p/?linkid=841272)
    
- [Diagrama del proceso de actualización de Microsoft Project Server](https://go.microsoft.com/fwlink/p/?linkid=841270)
    
- [La gran consolidación de la base de datos, la migración de Project Server 2010 a 2013 en 8 pasos sencillos](https://go.microsoft.com/fwlink/p/?linkid=841271)
    
### <a name="step-3-migrate-to-project-server-2016"></a>Paso 3: migrar a Project Server 2016

Después de migrar a Project Server 2013 y comprobar que los datos se han migrado correctamente, el siguiente paso consiste en migrar los datos a Project Server 2016.
  
Para obtener una descripción completa de lo que debe hacer para actualizar de Project Server 2013 a Project Server 2016, consulte el conjunto de contenido actualizar a Project Server 2016 en TechNet.
  
Recursos clave:
  
|**Recurso**|**Descripción**|
|:-----|:-----|
|[Introducción al proceso de actualización a Project Server 2016](https://go.microsoft.com/fwlink/p/?linkid=841260) <br/> |Obtenga información de alto nivel sobre lo que necesita hacer para actualizar de Project Server 2013 a Project Server 2016.  <br/> |
|[Planeación de la actualización a Project Server 2016](https://go.microsoft.com/fwlink/p/?linkid=841826) <br/> |Consulte las consideraciones de planeación que necesita realizar al actualizar de Project Server 2013 a Project Server 2016, incluidos.  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>Cosas que debe saber sobre la actualización a esta versión

Lo [que debe saber sobre la actualización de Project Server 2016](https://go.microsoft.com/fwlink/p/?linkid=841827) le indica algunos cambios importantes para la actualización de esta versión, que incluyen: 
  
- Al crear su entorno de Project Server 2016 en el que va a migrar los datos de Project Server 2013, tenga en cuenta que los archivos de instalación de Project Server 2016 se incluyen en SharePoint Server 2016. Para obtener más información, vea [deploy Project Server 2016](https://go.microsoft.com/fwlink/p/?linkid=841829).
    
- Los planes de recursos están en desuso en Project Server 2016. Los planes de recursos de Project Server 2013 se migrarán a las negociaciones de recursos en Project Server 2016 y Project online. Para obtener más información, vea [información general: negociaciones de recursos](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870) . 
    
## <a name="migrate-from-portfolio-server-2007"></a>Migrar desde el servidor de cartera 2007

Project Portfolio Server 2007 se usó con Project Server 2007 para la estrategia de cartera, la priorización y la optimización. No se han creado versiones adicionales del servidor de la cartera de proyectos después de esta versión. Sin embargo, las características de administración de cartera están disponibles tanto en Project Server 2016 como en la versión Premium de Project online. Los datos de Project Portfolio Server 2007 no se pueden migrar a ninguno de los dos. Se deben volver a crear los datos, como los impulsores de negocios.
  
Otros recursos:
  
- Descripciones de [servicios de Project online](https://go.microsoft.com/fwlink/p/?linkid=841280): vea las características de administración de cartera incluidas en project Server 2016 y Project online Premium.
    
- [Guía de migración de Microsoft Office Project Portfolio Server 2007](https://go.microsoft.com/fwlink/p/?linkid=841279)
    
## <a name="related-topics"></a>Temas relacionados

[Mapa de ruta de fin de soporte para SharePoint Server 2007](sharepoint-2007-end-of-support.md)
  
[Recursos que le ayudarán a actualizar desde los servidores y clientes de Office 2007](upgrade-from-office-2007-servers-and-products.md)
  

