---
title: Procedimientos recomendados para usar Office 365 en una red lenta
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/29/2016
ms.audience: End User
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- MET150
- MOP150
- MEW150
- BCS160
ms.assetid: fd16c8d2-4799-4c39-8fd7-045f06640166
description: ¿No sería genial si la conexión a Internet siempre era rápida y nunca abajo? Quizás surgirá ese día. Pero mientras tanto, hay prácticas cosas que puede hacer para evitar una red balky y aún realizar su trabajo cotidiano.
ms.openlocfilehash: 2287de562672f5ceb1ab32949168e8dfdeb31585
ms.sourcegitcommit: 317c2753be2aedb60698e94606ba59b63c962328
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/02/2018
ms.locfileid: "25933147"
---
# <a name="best-practices-for-using-office-365-on-a-slow-network"></a>Procedimientos recomendados para usar Office 365 en una red lenta

¿No sería genial si la conexión a Internet siempre era rápida y nunca abajo? Quizás surgirá ese día. Pero mientras tanto, hay prácticas cosas que puede hacer para evitar una red balky y aún realizar su trabajo cotidiano. Aunque Office 365 es un servicio basado en la nube, también proporciona muchas formas para trabajar con el contenido sin conexión y mantener sin problemas los cambios que se sincronizan. Además, a veces resulta más eficaz para trabajar con contenido sin conexión sólo porque las aplicaciones se ejecutan con mayor rapidez y la interfaz de usuario es mayor capacidad de respuesta. El punto es este: Office 365 le ofrece lo mejor de ambos mundos. Aquí es cómo aprovechar. 
  
> [!TIP]
> ¿Desea ver cómo lento (o fast) es la conexión de red? Intente la [prueba de velocidad de OOKLA](https://www.speedtest.net/) o la [Aplicación de prueba de velocidad de red](https://www.windowsphone.com/en-us/store/app/network-speed-test/9b9ae06b-2961-41ef-987d-b09567cffe70). 
     
## <a name="why-is-my-network-so-slow"></a>¿Por qué es mi red tan lento?

Aunque no tiene control sobre el rendimiento de red propio, ayuda a comprender lo que está ocurriendo segundo plano. Internet es muy compleja, pero hay algunos conceptos que le ayudarán a comprender la situación mucho mejor. Siguiendo los procedimientos recomendados en este artículo puede ayudar a problemas de rendimiento de la solución alternativa y reducir las frustraciones.
  
**Factores principales que afectan al rendimiento de la red**

![Factores de rendimiento de red](media/62a94322-3f1a-4d2d-bbdc-2aa0722d2d96.png)
  
 **Ancho de banda y latencia** Las dos medidas más importantes de rendimiento de la red son el ancho de banda y latencia: 
  
- Ancho de banda es la tasa de rendimiento que se mide en bits por segundo. Cuanto más grande es mejor. Ancho de banda es similar a una canalización de agua. Cuanto mayor sea la canalización, el agua más que puede "ponerlo a través de".
    
- La latencia es el tiempo que tarda en contenido obtener desde un servidor o servicio a su dispositivo y se mide en milisegundos. Es más rápido mejor. Latencia puede deberse a una serie de factores, incluidos el ancho de banda bajo, una conexión separado o tiempo de transmisión.
    
 **Problemas comunes** Además de ancho de banda y latencia, otros problemas tienen un impacto en el rendimiento de la red y a menudo están impredecibles. Rendimiento de la red puede fluctúa en función de la hora del día o a la ubicación física. La red se puede obstruyen cuando se produzcan determinados eventos que llegue el uso de Internet, por ejemplo, un desastre natural o un evento público principal. El tamaño y complejidad de la página que se está cargando y el número y tamaño de los archivos que se transfieren tienen una incidencia directa en el rendimiento. Una conexión WiFi temporalmente puede afectar negativamente al: por ejemplo, sondear una reunión de conferencia grande de miles solicitando que todos los mensajes al mismo tiempo. 
  
 **Consideraciones para una red de satélite** Una red de satélite es útil cuando una red terrestre no es viable, como el país atrás, un envío cruise o un área científico remoto. Estas redes se basan en satélites colocadas en una órbita geosynchronous 22.000 millas por encima del Ecuador. Sin embargo, una transmisión realmente viaja a 90.000 millas y, por lo que una red de satélite tiene una latencia más lenta (500 ms o más) que una red terrestre (20 a 50 ms.). En las mejores condiciones, no es posible que tenga en cuenta esta latencia, pero para descargar archivos de gran tamaño, transmisión por secuencias de vídeos y jugar, probablemente hará. Otro problema es "lluvia atenuación" en qué meteorología intensa, como tormentas y blizzards, puede interrumpir temporalmente la transmisión de satélite.
  
## <a name="are-you-sure-its-the-network"></a>¿Está seguro de que es la red?

Siempre que experimente problemas de rendimiento, en primer lugar asegúrese de que el dispositivo no es la causa del problema. Hay dos cosas que puede hacer que hagan una gran mejora:
  
- Asegúrese de que el dispositivo se está ejecutando correctamente y no hay ningún malware en su equipo.
    
- Si es posible, comprar más memoria. Agregar memoria es la más sencilla y más a menudo una forma eficaz para mejorar el rendimiento en su dispositivo. Es especialmente útil cuando se trabaja con vídeos y archivos de gran tamaño.
    
Para obtener más información, consulte [Mantenimiento y rendimiento de Windows](https://windows.microsoft.com/en-us/windows/performance-maintenance-help#performance-maintenance-help) y [problemas de rendimiento del sistema de corrección de Windows](https://support.microsoft.com/mats/slow_windows_performance/).
   
## <a name="best-practices-for-using-your-browser"></a>Procedimientos recomendados para usar el explorador

Su explorador es su puerta de enlace a Office 365, por lo que puede tener un impacto en el rendimiento, especialmente con el tiempo que se tarda en cargar una página y la frecuencia con desea redondear trip a Office 365 servicio. 
  
 **Exploradores en general**
  
Estas son algunas sugerencias para exploradores en general:
  
- Deshabilitar los complementos de explorador que puede afectar al rendimiento o que no necesita realmente.
    
- Aumentar el tamaño de la memoria caché para los archivos temporales de internet.
    
-  Una vez que ha iniciado sesión en su cuenta de trabajo o escuela, mantenga la ventana del explorador abierto a lo largo del día. Puede abrir otras fichas y windows sin iniciar sesión de nuevo. Si necesita iniciar sesión en otra cuenta, use exploración privada. 
    
- Una vez que cada página esté descargado y open, mantenga ellos abierto mediante el uso de las fichas. Es fácil de navegar entre las fichas y use la página más adelante en el día. Actualizar una página sólo si necesita que los datos más recientes en esa página.
    
- Si tarda demasiado tiempo para abrir una página, detenga la descarga de la página (presione ESC) y, a continuación, actualice la página (presione F5). 
    
-  Cuando sea posible, reducir ida y vuelta a Office 365. Por ejemplo, en lugar de paginación a través de las listas o bibliotecas, utilice Buscar para buscar archivos en una biblioteca de gran tamaño y el filtrado en una lista para llegar directamente a los resultados que desea. O bien, crear vistas que minimizar el tiempo de carga de página. Para obtener más información, vea [administrar grandes listas y bibliotecas en Office 365](https://support.office.com/article/b4038448-ec0e-49b7-b853-679d3d8fb784#BKMK_PAGES).
    
- Si el rendimiento de vídeo es mala, es posible que pueda descargar el vídeo y verla en su dispositivo. Un vínculo de descarga puede estar disponible o es posible que pueda a haga clic con el botón secundario del mouse en el vínculo de vídeo y seleccione **Guardar destino como**. 
    
 **Específico del explorador**
  
Éstas son algunas sugerencias para el explorador específico:
  
- **Internet Explorer** Actualizar a Internet Explorer versión 11 o más adelante para las mejoras de rendimiento importantes con respecto a versiones anteriores. Para obtener más información, vea [problemas de corrección de Internet Explorer ](https://support.microsoft.com/mats/ie_performance_and_safety).
    
- **FireFox** Para obtener más información, vea [Firefox es lento o deja de funcionar](https://support.mozilla.org/en-US/products/firefox/fix-problems/slowness-or-hanging).
    
- **Safari** Para obtener más información, vea [Apple - Safari](https://www.apple.com/safari/).
    
- **Cromo** Para obtener más información, consulte la [Ayuda de cromo](https://support.google.com/chrome/?hl=en).
  
## <a name="best-practices-for-using-outlook-and-outlook-web-app"></a>Procedimientos recomendados para el uso de Outlook y Outlook Web App

Lectura, escritura y organización de correo electrónico es una parte importante del día de todos los usuarios. Outlook y Outlook Web App (OWA) ofrecen soporte sin conexión. Uso de una aplicación de correo electrónico en el teléfono inteligente es otra alternativa útil. Utilice las siguientes opciones que se ajusta mejor a sus necesidades:
  
- Actualización a Outlook 2013 SP1 o posterior para mejoras sustanciales de rendimiento con respecto a versiones anteriores. 
    
-  Outlook Web App le permite crear mensajes sin conexión, los contactos y eventos de calendario que se cargan cuando OWA es lo siguiente capaces de conectarse a Office 365. Para obtener más información sobre cómo configurar y usar OWA en modo sin conexión, vea [Uso de Outlook Web App sin conexión](https://support.office.com/article/3214839c-0604-4162-8a97-6856b4c27b36).
    
- Outlook le permite trabajar en modo en caché, en la que se conecta automáticamente siempre que sea posible. Puede hacer que Outlook descargar todo el buzón o sólo una parte de ella. Para obtener más información, vea [activar el modo de intercambio en caché](https://support.office.com/article/7885af08-9a60-4ec3-850a-e221c1ed0c1c) y [trabajar sin conexión en Outlook](https://support.office.com/article/f3a1251c-6dd5-4208-aef9-7c8c9522d633). 
    
- Outlook también ofrece un modo sin conexión. Para ello, primero debe establecer el modo en caché para que la información de su cuenta se copia en el equipo. En el modo sin conexión, Outlook intentará conectarse mediante la operación Enviar y recibir opciones, o cuando establece manualmente para que funcione en línea. Para obtener más información, vea [trabajar sin conexión para evitar gastos de conexión de datos](https://support.office.com/article/827fe51f-5609-4062-82b4-3578057f9282), [cambiar enviar y recibir opciones cuando se trabaja sin conexión](https://support.office.com/article/f681ec10-cb14-40cb-8709-1909a13c304a)y un [conmutador de trabajar sin conexión a en línea](https://support.office.com/article/2460e4a8-16c7-47fc-b204-b1549275aac9). 
    
- Si tiene un teléfono inteligente, se puede usar para evaluar su correo electrónico y calendario a través de red de su operador de telefonía de teléfono. 
    
> [!NOTE]
> Aquí tiene algunas instrucciones sobre cuándo utilizar Outlook u OWA. Si el espacio en disco no es un problema en su dispositivo, Outlook tiene un completo conjunto de características y es posible que funcione mejor para usted. Si el espacio en disco es un problema en su dispositivo, considere el uso de OWA que tiene un subconjunto de características, pero también funciona mejor en una situación en línea. Por supuesto, puede usar cualquiera debido a que funcionan bien juntos. 
  
## <a name="best-practices-for-using-onedrive-for-business"></a>Procedimientos recomendados para el uso de OneDrive para la empresa

OneDrive para la empresa está diseñado desde el principio para trabajar con los archivos en línea y sin conexión. Una vez configurado, se realiza la sincronización de los cambios automáticamente y confiable donde quiera y cuando se realizan. Si la red es lenta, puede trabajar con la versión de los archivos sin conexión.
  
La OneDrive para la aplicación empresarial de sincronización está disponible con Office 2013 (Professional Plus, o las ediciones Standard) o una suscripción a Office 365 que incluye aplicaciones de Office 2013. Si no dispone de Office 2013, se puede [Descargar](https://support.microsoft.com/kb/2903984) el OneDrive para la aplicación empresarial de sincronización de manera gratuita. Esta aplicación también es más rápida que el uso de los comandos **abierta en el explorador** o **cargar** . Para obtener más información, vea [Configurar el equipo para sincronizar su OneDrive para los archivos de negocio de Office 365](https://support.office.com/article/23e1f12b-d896-4cb1-a238-f91d19827a16).
  
Aquí tiene algunas instrucciones adicionales para usar el OneDrive para la aplicación empresarial de sincronización:
  
- Si se está sincronizando una biblioteca grande por primera vez, iniciar la sincronización durante horas de inactividad, por ejemplo, durante la noche. 
    
- Puede usar la característica [detendrá la sincronización de una biblioteca con el OneDrive para la aplicación empresarial](https://support.office.com/article/a7e41f1f-3a98-4ca7-9443-f10250688330) para impedir temporalmente que las actualizaciones de la sincronización. Sin embargo, usar esta característica durante breves períodos, como unas cuantas horas a la vez, para evitar la puesta en cola grandes números de actualizaciones y a fin de minimizar el riesgo de conflictos de combinación si varias personas trabajan en el mismo documento. 
  
## <a name="best-practices-for-using-onenote"></a>Procedimientos recomendados para el uso de OneNote

Cada sitio de grupo de SharePoint tiene un bloc de notas de OneNote integrada y puede crear fácilmente su propio. OneNote es un buen método para recopilar información puntual que necesita cada día para obtener las tareas que realiza. Por ejemplo, muchos equipos utilizan OneNote como un punto de la colección para reuniones semanales, notas del proyecto, ideas, planes e informes de estado. Adaptan perfectamente puede organizar esta información dispersa mediante el uso de las fichas, secciones y páginas.
  
Pero lo bueno de OneNote es que se puede obtener acceso al contenido desde prácticamente cualquier dispositivo, si un equipo de escritorio, un equipo portátil, una tableta o un teléfono inteligente. Y no tienen que preocuparse acerca de guardar o sincronizar porque OneNote lo hace por usted. 
  
Para obtener más información, vea [Microsoft OneNote](https://office.microsoft.com/en-us/onenote/).
  
## <a name="best-practices-for-using-lync-online"></a>Procedimientos recomendados para el uso de Lync Online

Las siguientes son instrucciones generales para el uso de Lync Online cuando la red es lenta:
  
- Utilizar la mensajería instantánea siempre que pueda porque funciona bien en una red lenta.
    
- Evite realizar llamadas telefónicas a través de una red privada virtual (VPN) o conexiones de acceso remoto (RAS) de servicio.
    
- Asegúrese de que el dispositivo de audio está aprobado. Para obtener más información, vea [teléfonos y dispositivos cualificados para Microsoft Lync](https://technet.microsoft.com/en-us/office/dn788944).
    
-  Cuando el uso de PowerPoint en una presentación en línea, reducir el tamaño y la complejidad de las diapositivas. Para obtener más información, vea [sugerencias para mejorar el rendimiento de la presentación](https://support.office.com/article/34c82835-5f23-4bf0-98cc-72235bbd2949).
    
- Siempre que sea posible, compartir a un monitor, en lugar de un programa o un escritorio. Para obtener más información, vea [compartir el escritorio o un programa en Lync](https://support.office.com/article/33aaa965-eb32-42a9-8a9b-cdfffa364842).
    
- En lugar de compartir, enviarán las diapositivas de PowerPoint antes de tiempo como una reunión solicitar datos adjuntos, por lo que los asistentes vean las diapositivas en el dispositivo de cliente. Para obtener más información, consulte [Configurar una reunión de Lync](https://support.office.com/article/258f9d20-f06c-49a4-a77f-7f5ac635bb5d).
    
-  Rendimiento de vídeo es muy dependiente en el rendimiento de la red. Evitar el uso de vídeo si la red es lenta. 
    
Para obtener más información, vea [audio deficiente o calidad de vídeo en Lync Online](https://support.microsoft.com/kb/2386655) y [Actualizar en Lync 2013 lentas de la pantalla](https://support.microsoft.com/kb/2958375).
  
## <a name="best-practices-for-using-sharepoint-lists"></a>Procedimientos recomendados para el uso de las listas de SharePoint

Trabajar con datos de lista sin conexión para "Anular", analizar o datos constituye una excelente manera a fin de minimizar el impacto de una red lenta del informe. Puede leer y escribir la mayoría de las listas de Microsoft Access 2013 vinculando a ellos. También puede exportar una lista a una tabla de Excel, que crea una conexión de datos unidireccional entre la tabla de Excel y la lista.
  
Además, si se activa la característica de servicios de Access, puede trabajar con considerablemente más datos que el umbral de vista de lista, un máximo de 50.000 elementos de forma predeterminada. Tanto Access 2013 and Excel 2013 procesan automáticamente los datos de lista en lotes pequeños y, a continuación, volver a ensamblar los datos, una técnica que le permite trabajar con muchos más datos que el umbral de vista de lista y sin afectar negativamente el rendimiento del servicio de otros usuarios. 
  
Para obtener más información, vea la sección "más información acerca de administración de listas de gran tamaño" en [administrar grandes listas y bibliotecas en Office 365](https://support.office.com/article/b4038448-ec0e-49b7-b853-679d3d8fb784).
  
## <a name="best-practices-for-customizing-web-pages"></a>Procedimientos recomendados para personalizar las páginas web

Cuando personaliza una página web, podría causar por descuido un rendimiento deficiente con la página. Un número de factores puede tener un impacto, como la complejidad y el tamaño de la página, ¿cuántos elementos web se agregan, inicialmente se muestran cuántos elementos de lista o biblioteca y la forma en que la página de código.
  
Para obtener más información, vea [SharePoint Online de ajuste de rendimiento](https://docs.microsoft.com/office365/enterprise/tune-sharepoint-online-performance).
  
## <a name="best-practices-for-using-project-online"></a>Procedimientos recomendados para el uso de Project Online

Las siguientes instrucciones pueden ayudar a mejorar el rendimiento de la red.
  
- Project Online y SharePoint Online requieren sincronización, que puede llevar mucho tiempo. Si los equipos del proyecto tienen rotación baja, deshabilitar la sincronización de sitios de proyecto para mejorar el rendimiento de publicación del proyecto y páginas de detalles del proyecto. Límite de sincronización de Active Directory a los grupos de recursos que realmente se necesitan para usar el sistema y supervisar los posibles problemas de permisos después de la sincronización de grupos de gran tamaño. 
    
- Si su organización usa sitios de proyecto, crearlos a petición en lugar de automáticamente. Esto acelera la primera experiencia de publicación y evita la creación de contenido y sitios innecesarios.
    
- Las páginas de detalles de proyecto (PDP) puede desencadenar una actualización de todo el proyecto e iniciar acciones de flujo de trabajo, ambos de los cuales pueden ser operaciones con uso intensivo de rendimiento. Para evitar que se produzca dos procesos de actualización al mismo tiempo en el mismo PDP, evitar la actualización de los campos de calendario (fecha de inicio, fecha de finalización, fecha de estado y la fecha actual) y los campos que no sean programado (nombre del proyecto, descripción y propietario). 
    
- Reducir el número de elementos Web y los campos personalizados que se muestran en cada PDP. Crear una PDP dedicada con los únicos campos que requieren la actualización para mejorar la carga y ahorrar tiempo. 
    
- Cuando utilice OData para los informes, limitar la cantidad de datos de que consulta en tiempo de ejecución mediante el uso de filtrado del lado del servidor.
    
Para obtener más información, vea [Project Online de ajuste de rendimiento](https://support.office.com/article/12ba0ebd-c616-42e5-b9b6-cad570e8409c).
  
## <a name="whats-the-best-way-to-report-problems"></a>¿Qué es la mejor manera de informar de los problemas?

Microsoft continuamente mejora el rendimiento general de Office 365 mediante la supervisión de la red, medición de ancho de banda y latencia, mejorar el tiempo, reducción E/S de disco, rediseño de carga de página de páginas para usar la estrategia de descarga mínima, agregar hardware a centros de datos y Adición de más centros de datos. Para obtener más información acerca de problemas de creación de informes y comprobación de su estado actual, consulte [Ver el estado de los servicios](https://office.microsoft.com/en-us/office365-suite-help/view-the-status-of-your-services-HA102817837.aspx).
  
## <a name="see-also"></a>Vea también

[Planeamiento de red y ajuste del rendimiento para Office 365](network-planning-and-performance.md)
  
[Curso de Microsoft Virtual Academy: administración de rendimiento de Office 365](https://blogs.office.com/2014/12/03/microsoft-virtual-academy-course-office-365-performance-management/)
  
[Administrar puntos de conexión de Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Preguntas frecuentes sobre extremos de Office 365](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

