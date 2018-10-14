---
title: Guía básica de fin de soporte de Server 2010 de Project
ms.author: efrene
author: efrene
manager: pamg
ms.date: 10/12/2018
ms.audience: ITPro
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
description: En el 13 de octubre de 2020, finaliza la compatibilidad para Project Server 2010. Use este artículo para planear la actualización ahora.
ms.openlocfilehash: bdfc4dd81dca7fe137be5780e54252eba961910f
ms.sourcegitcommit: e89b5306338ecdb40ad88efcf9cae3b8d5692924
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/13/2018
ms.locfileid: "25549793"
---
# <a name="project-server-2010-end-of-support-roadmap"></a>Final de Project Server 2010 de guía básica de soporte técnico

Soporte técnico está finalizando para las aplicaciones y los servidores de Office 2010 en 2010, y debe tener en cuenta los planes para la migración. Si actualmente usa Project Server 2010, tenga en cuenta que lo y estos otros productos relacionados tendrá el siguiente final de fechas de soporte técnico:
  
|**Product**|**final de la fecha de soporte técnico**|
|:-----|:-----|
|Project Server 2010  <br/> |13 de octubre de 2020  <br/> |
|Project Portfolio Server 2010  <br/> |13 de octubre de 2020  <br/> |
|Estándar de Project 2010  <br/> |13 de octubre de 2020  <br/> |
|Project 2010 Professional  <br/> |13 de octubre de 2020  <br/> |
   
Para obtener más información acerca de los servidores de Office 2010 alcanzar jubilación, vea [actualización de productos de cliente y servidores de Office 2010](https://docs.microsoft.com/office365/enterprise/plan-upgrade-previous-versions-office).
  
## <a name="what-does-end-of-support-mean"></a>¿Qué final hace de Media de soporte técnico?

Project Server, al igual que casi todos los productos de Microsoft, tiene un ciclo de vida de soporte técnico durante el cual se proporcionan las nuevas características, correcciones de errores, las revisiones de seguridad y así sucesivamente. Este ciclo de vida dura normalmente de 10 años desde la fecha de lanzamiento del producto, y el final de este ciclo de vida se conoce como fin del producto del soporte. Debido a que Project Server 2010 alcanza su fin del soporte en el 10 de octubre de 2020, Microsoft ya no proporcionará:
  
- Soporte técnico para problemas que puedan surgir.
    
- Correcciones de errores para los problemas que se descubren y que puede afectar a la estabilidad y la facilidad de uso del servidor.
    
- Revisiones de seguridad para las vulnerabilidades de seguridad que se descubren y que puede hacer el servidor vulnerable a infracciones de seguridad.
    
- Actualizaciones de zona horaria.
    
La instalación de Project Server 2010 continuará ejecutándose después de esta fecha. Sin embargo, debido a los cambios enumerados anteriormente, se recomienda migrar tan pronto como sea posible desde Project Server 2010.
  
## <a name="what-are-my-options"></a>¿Cuáles son las opciones de mi?

Si usa Project Server 2010, debe explorar las opciones de migración, que son:
  
- Migrar a Project Online
    
- Migrar a una versión más reciente de local de Project Server (preferiblemente Project Server 2019).
    
|**¿Por qué tendría prefiere migrar a Project Online**|**¿Por qué tendría prefiere migrar a Project Server 2019**|
|:-----|:-----|
| Tengo que los usuarios móviles.  <br/>  Los costos para migrar son una preocupación big (hardware, software, horas y esfuerzo para implementar, etcetera).  <br/>  Después de la migración, los costos para mantener mi entorno son una cuestión importante (por ejemplo, actualizaciones automáticas, garantizada el tiempo de actividad, etcetera.).  <br/> | Reglas de negocio restringen me operativo mi negocio en la nube.  <br/>  Necesito mi entorno de control de actualizaciones.  <br/> |
   
> [!NOTE]
> Para obtener más información acerca de las opciones para pasar de los servidores de Office 2010, vea [recursos para ayudarle a actualizar de Office 2010 servidores y clientes](https://docs.microsoft.com/office365/enterprise/upgrade-from-office-2010-servers-and-products). Tenga en cuenta que Project Server no es compatible con una configuración híbrida con respecto a Project Server y Project Online no se pueden compartir el mismo grupo de recursos. 
  
## <a name="important-considerations-you-need-to-make-when-planning-to-migrate-from-project-server-2010"></a>Consideraciones importantes que debe tomar al planear la migración de Project Server 2010

Debe tener en cuenta lo siguiente al planear la migración de Project Server 2010:
  
- **Obtener ayuda de un socio de Microsoft** - actualización de Project Server 2010 puede suponer un reto y requiere mucho preparación y planificación. Puede ser especialmente difícil si no estuviera uno de programa de instalación y configuración de Project Server 2010 originalmente. Afortunadamente, existen Microsoft Partners puede activar para que lo haga con un vida, si va a migrar a Project Server 2019 o a Project Online. Puede buscar un Microsoft Partner ayudar con la migración en el [Centro de socio de Microsoft](https://go.microsoft.com/fwlink/p/?linkid=841249). Puede extraer una lista de todos los Microsoft Partner con experiencia en Project, busque en el término de *proyecto oro y administración de cartera de proyectos* . 
    
- **Planeación de las personalizaciones** - tenga en cuenta que muchas de las personalizaciones que debe trabajar en el entorno de Project Server 2010 no funcionen al migrar a Project Server 2019 o a Project Online. Existen grandes diferencias en la arquitectura de Project Server entre versiones, así como los sistemas operativos necesarios, servidores de base de datos y exploradores web de cliente que se admiten para que funcione con la versión más reciente. Tener un plan en lugar de cómo probar o volver a generar las personalizaciones según sea necesario en el nuevo entorno. Planeación de la actualización será también una buena oportunidad para comprobar si realmente se necesita una personalización específico cuando se desplaza hacia delante. [Crear un plan para personalizaciones actuales durante la actualización a SharePoint 2013](https://go.microsoft.com/fwlink/p/?linkid=842061) tiene gran información general acerca de la evaluación y planeación de las personalizaciones actuales al actualizar. 
    
- **Tiempo y paciencia** - actualización de planeación, ejecución y prueba le llevará mucho tiempo y esfuerzo, especialmente si va a actualizar a Project Server 2019. Por ejemplo, si va a migrar desde Project Server 2010 a Project Server 2019, se primero debe migrar desde Project Server 2010 a Project Server 2013 y, a continuación, comprobar si los datos y, a continuación, hacer lo mismo al migrar a cada versión sucesiva (proyecto Servidor 2016 y, a continuación, Project Server 2019). Es posible que desee comprobar con un Partner de Microsoft para comparar los costos estimados con sus estimaciones de cuánto se tardará para ellos hacerlo y cuál es su costo. 
    
## <a name="migrate-to-project-online"></a>Migrar a Project Online

Si decide migrar desde Project Server 2010 a Project Online, puede hacer lo siguiente para migrar manualmente los datos del plan de proyecto:
  
1. Guarde los planes del proyecto desde Project Server 2010 para. Formato MPP.
    
2. Uso de Project Professional 2016, Project Professional 2019 o el cliente de escritorio de Project Online, abrir cada archivo .mpp y, a continuación, guardar y publicar a Project Online.
    
Puede crear manualmente la configuración de PWA en Project Online (por ejemplo, vuelva a crear los campos personalizados que necesite o calendarios de empresa). Partners de Microsoft pueden ayudarle también con esto.
  
Recursos clave:
  
|**Recurso**|**Descripción**|
|:-----|:-----|
|[Introducción a Project Online](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11) <br/> |Cómo instalar y usar Project Online.  <br/> |
|[Descripciones de servicios en línea de Project](https://go.microsoft.com/fwlink/p/?linkid=829088) <br/> |Información acerca de los distintos planes de proyecto en línea que están disponibles para usted.  <br/> |
   
## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>Migrar a una versión más reciente de local de Project Server

Aunque creemos encarecidamente que puede lograr la mejor experiencia de usuario y el valor mediante la migración a Project Online, también sabemos que algunas organizaciones necesitan mantener los datos de proyecto en un entorno local. Si opta por mantener sus proyecto datos locales, puede migrar el entorno de Project Server 2010 a Project Server 2013, Project Server 2016 o 2019 de Project Server.
  
Se recomienda migrar a Project Server 2019 si no se puede migrar a Project Online. Project Server 2019 incluye la mayor parte de la clave de las características y los avances que se incluye con las versiones anteriores de Project Server y más aproxime la experiencia disponible con Project Online (aunque algunas de las características están disponibles únicamente en Project Online).
  
Después de completar cada migración, debe comprobar los datos para asegurarse de que ha migrado correctamente.
  
> [!NOTE]
> Si está pensando en migrar sólo a Project Server 2013 si está limitado a una solución local, es importante tener en cuenta que sólo tiene unos pocos años más de compatibilidad de la izquierda. Project Server 2013 con Service Pack 2 es el final de la compatibilidad con fecha 13/10/2023. Para obtener más información acerca de final de fechas de soporte técnico, vea [Directiva de ciclo de vida de productos de Microsoft](https://go.microsoft.com/fwlink/p/?linkid=842066). 
  
### <a name="how-do-i-migrate-to-project-server-2019"></a>¿Cómo se realiza la migración a Project Server 2019?

Las diferencias de arquitectura entre Project Server 2010 y Project Server 2019 impide que una ruta de migración directa. Esto significa que necesita migrar los datos de Project Server 2010 a la próxima versión sucesiva de Project Server hasta que actualice a Project Server 2019.
  
Debe hacer lo siguiente para actualizar a Project Server 2019:
  
1. Paso 1: Migre los datos de Project Server 2010 a Project Server 2013.
    
2. Paso 2: Migrar los datos de Project 2013 servir a Project Server 2016.
    
3. Paso 3: Migre los datos de Project Server 2016 a Project Server 2019.
    
Después de completar cada migración, debe comprobar los datos para asegurarse de que ha migrado correctamente.
  
    
### <a name="step-1-migrate-to-project-server-2013"></a>Paso 1: Migración a Project Server 2013

El primer paso para migrar los datos de Project Server 2010 a Project Server 2019 es migrar a Project Server 2013. 
  
Para obtener una descripción completa de lo que necesita hacer para actualizar desde Project Server 2010 a Project Server 2013, vea el conjunto de contenido [actualizar a Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841822) en TechNet. 
  
Recursos clave:
  
|**Recurso**|**Descripción**|
|:-----|:-----|
|[Proceso de actualización de información general de Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841822) <br/> |Obtener una descripción de alto nivel de lo que necesita hacer para actualizar desde Project Server 2010 a Project Server 2013.  <br/> |
|[Planear la actualización a Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841823) <br/> |Examine la planeación de consideraciones que debe tomar al actualizar desde Project Server 2010 a Project Server 2013, incluidos los requisitos del sistema.  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>Cosas que debe saber acerca de la actualización a esta versión

[Novedades de la actualización de Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841824) indica a algunos cambios importantes para la actualización para esta versión, la más relevantes que se está: 
  
- No hay ninguna actualización en contexto a Project Server 2013. La base de datos adjunta (método) es el único método admitido para la actualización de Project Server 2010 a Project Server 2013.
    
- El proceso de actualización no sólo convertirá los datos de Project Server 2010 en formato de Project Server 2013, pero también consolidan las cuatro bases de datos de Project Server 2010 para una sola base de datos de Project Web App.
    
- SharePoint Server 2013 y Project Server 2013 se ha cambiado a la autenticación basada en notificaciones desde la versión anterior. Debe realizar consideraciones al actualizar si usa la autenticación clásica. Para obtener más información, vea [migración desde el modo clásico a la autenticación basada en notificaciones en SharePoint 2013](https://go.microsoft.com/fwlink/p/?linkid=841825).
    
Recursos adicionales:
  
- [Introducción al proceso de actualización a Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841274)
    
- [Actualización de las bases de datos y de las colecciones de sitios de Project Web App (Project Server 2013)](https://go.microsoft.com/fwlink/p/?linkid=841272)
    
- [Diagrama del proceso de actualización de Microsoft Project Server](https://go.microsoft.com/fwlink/p/?linkid=841270)
    
- [La consolidación de gran base de datos, migración de Project Server 2010 para 2013 en 8 sencillos pasos](https://go.microsoft.com/fwlink/p/?linkid=841271)
    
### <a name="step-2-migrate-to-project-server-2016"></a>Paso 2 migración a Project Server 2016

Después de migrar a Project Server 2013 y comprobar que los datos se han migrado correctamente, el siguiente paso es migrar los datos a Project Server 2016.
  
Para obtener una descripción completa de lo que necesita hacer para actualizar desde Project Server 2013 a Project Server 2016, vea el conjunto de contenido [actualizar a Project Server 2016](https://docs.microsoft.com/en-us/Project/upgrade-to-project-server-2016) .
  
Recursos clave:
  
|**Recurso**|**Descripción**|
|:-----|:-----|
|[Introducción al proceso de actualización a Project Server 2016](https://docs.microsoft.com/Project/overview-of-the-project-server-2016-upgrade-process) <br/> |Obtener una descripción de alto nivel de lo que necesita hacer para actualizar desde Project Server 2013 a Project Server 2016.  <br/> |
|[Planeación de la actualización a Project Server 2016](https://docs.microsoft.com/Project/plan-for-upgrade-to-project-server-2016) <br/> |Examine las consideraciones de planeación que debe tomar al actualizar desde Project Server 2013 a Project Server 2016.  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>Cosas que debe saber acerca de la actualización a esta versión

[Cosas que debe saber acerca de Project Server 2016 actualización](https://docs.microsoft.com/project/plan-for-upgrade-to-project-server-2016#thingknow) indica a algunos cambios importantes para la actualización para esta versión, que incluyen: 
  
- Cuando se crea el entorno de 2016 de Project Server a la que va a migrar los datos de Project Server 2013, tenga en cuenta que se encuentran los archivos de instalación de Project Server 2016 en SharePoint Server 2016. Para obtener más información, vea [implementación de Project Server 2016](https://go.microsoft.com/fwlink/p/?linkid=841829).
    
- Planes de recursos están en desuso en Project Server 2016. Los planes de recursos de Project Server 2013 se migrará a contrataciones de recursos en Project Server 2016 y en Project Online. Vea [información general: contrataciones de recurso](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870) para obtener más información. 
    
### <a name="step-3-migrate-to-project-server-2019"></a>Paso 3 migración a Project Server 2019

Después de migrar a Project Server 2016 y comprobar que los datos se han migrado correctamente, el siguiente paso es migrar los datos a Project Server 2019.
  
Para obtener una descripción completa de lo que necesita hacer para actualizar desde Project Server 2016 a Project Server 2019, vea el conjunto de contenido [actualizar a Project Server 2019](https://docs.microsoft.com/en-us/Project/upgrade-to-project-server-2016) .
  
Recursos clave:
  
|**Recurso**|**Descripción**|
|:-----|:-----|
|[Proceso de actualización de información general sobre el servidor de Project 2019](https://docs.microsoft.com/project/overview-of-the-project-server-2019-upgrade-process) <br/> |Obtener una descripción de alto nivel de lo que necesita hacer para actualizar desde Project Server 2013 a Project Server 2016.  <br/> |
|[Planeación de la actualización a Project Server 2019](https://docs.microsoft.com/project/plan-for-upgrade-to-project-server-2019) <br/> |Examine las consideraciones de planeación que debe tomar al actualizar desde Project Server 2016 a Project Server 2019.  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>Cosas que debe saber acerca de la actualización a esta versión

[Cosas que debe saber acerca de Project Server 2019 actualización](https://go.microsoft.com/fwlink/p/?linkid=841827) indica a algunos cambios importantes para la actualización para esta versión, que incluyen: 
  
- El proceso de actualización migre los datos de la base de datos de Project Server 2016 a la base de datos de contenido de SharePoint Server 2019.  Project Server 2019 no durante cuánto tiempo va a crear es el propietario de base de datos de Project Server en la granja de servidores de SharePoint.

- Después de la actualización, tenga varios cambios en Project Web App.  Para obtener una descripción de estos, vea [Novedades de Project Server 2019](https://docs.microsoft.com/en-us/project/what-s-new-for-it-pros-in-project-server-2019#PWAChanges).


## <a name="migrate-from-portfolio-server-2010"></a>Migración de Portfolio Server 2010

Project Portfolio Server 2010 se usó con Project Server 2010 para la optimización, asignación de prioridades y estrategia de cartera. No hay versiones adicionales de Project Portfolio Server se crearon después de esta versión. Sin embargo, las características de administración de cartera de proyectos están disponibles en versiones posteriores de Project Server y la versión Premium de Project Online. No se puede migrar datos desde Project Portfolio Server 2010 a cualquiera. Datos como los impulsores de negocios tendrá que volver a crearse.
  
Otros recursos:
  
- [Descripciones del servicio de Project Online](https://go.microsoft.com/fwlink/p/?linkid=841280): vea las características de administración de cartera de proyectos que se incluyen con 2016 de Project Server y Project Online Premium.
    
- [Guía de migración de Microsoft Office Project Portfolio Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841279)
    
## <a name="related-topics"></a>Temas relacionados

[Actualizar desde SharePoint 2010](upgrade-from-sharepoint-2010.md)
  
[Recursos que le ayudarán a actualizar de Office 2010 de los clientes y servidores](upgrade-from-office-2010-servers-and-products.md)
  

