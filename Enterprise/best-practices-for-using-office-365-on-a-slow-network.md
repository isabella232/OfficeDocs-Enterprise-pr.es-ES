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
description: ¿No sería bueno si la conexión a Internet siempre era rápida y nunca inactiva? Quizá ese día venga. Pero, mientras tanto, hay cosas prácticas que puede hacer para trabajar en una red de balky y seguir haciendo su trabajo cotidiano.
ms.openlocfilehash: 3ddc6483956657485b75a20a540ea83a55b61564
ms.sourcegitcommit: a35d23929bfbfd956ee853b5e828b36e2978bf36
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "33655774"
---
# <a name="best-practices-for-using-office-365-on-a-slow-network"></a>Procedimientos recomendados para usar Office 365 en una red lenta

¿No sería bueno si la conexión a Internet siempre era rápida y nunca inactiva? Quizá ese día venga. Pero, mientras tanto, hay cosas prácticas que puede hacer para trabajar en una red de balky y seguir haciendo su trabajo cotidiano. Aunque Office 365 es un servicio basado en la nube, también ofrece muchas formas de trabajar con el contenido sin conexión y de mantener los cambios sincronizados sin problemas. Además, a veces es más eficaz trabajar con el contenido sin conexión, simplemente porque las aplicaciones se ejecutan más rápido y la interfaz de usuario tiene más capacidad de respuesta. La cuestión es la siguiente: Office 365 le ofrece lo mejor de ambos mundos. Esta es la manera de aprovechar esta ventaja. 
  
> [!TIP]
> ¿Quiere saber qué tan lenta (o rápido) es su conexión de red? Pruebe la [prueba de velocidad de OOKLA](https://www.speedtest.net/) o la [aplicación de prueba de velocidad de red](https://www.windowsphone.com/store/app/network-speed-test/9b9ae06b-2961-41ef-987d-b09567cffe70). 
     
## <a name="why-is-my-network-so-slow"></a>¿Por qué mi red es tan lenta?

Aunque no tiene control sobre el rendimiento de la red, ayuda a entender lo que sucede en segundo plano. Internet es muy complejo, pero hay algunos conceptos que pueden ayudarle a comprender mejor la situación. Seguir los procedimientos recomendados de este artículo puede ayudar a solucionar problemas de rendimiento y reducir la frustración.
  
**Factores importantes que afectan al rendimiento de la red**

![Factores de rendimiento de la red](media/62a94322-3f1a-4d2d-bbdc-2aa0722d2d96.png)
  
 **Ancho de banda y latencia** Las dos medidas más importantes del rendimiento de red son el ancho de banda y la latencia: 
  
- El ancho de banda es la tasa de rendimiento medido en bits por segundo. Mayor es mejor. El ancho de banda es como una tubería de agua. Cuanto mayor sea la canalización, más agua podrá "colocar" por ella.
    
- La latencia es el tiempo que tarda el contenido en llegar desde un servidor o servicio a su dispositivo y se mide en milisegundos. Más rápido es mejor. La latencia puede deberse a una serie de factores, como bajo ancho de banda, una conexión dispersa o un tiempo de transmisión.
    
 **Problemas comunes** Además del ancho de banda y la latencia, otros problemas tienen un impacto en el rendimiento de la red y suelen ser imprevisibles. El rendimiento de la red puede fluctuar en función de la hora del día o de la ubicación física. La red puede obstruirse cuando se producen determinados eventos que hacen que el uso de Internet sea intenso, como un desastre natural o un evento público importante. El rendimiento y el tamaño de la página que se va a cargar y el número y tamaño de los archivos que se van a transferir tienen un cojinete directo en el rendimiento. Una conexión WiFi puede degradarse temporalmente: por ejemplo, para sondear una reunión de conferencia grande de miles, solicite a todos los usuarios a Tweet al mismo tiempo. 
  
 **Consideraciones para una red satélite** Una red de satélite es útil cuando una red terrestre no es viable, como el país de la parte posterior, un barco de crucero o un área científica remota. Estas redes se basan en los satélites colocados en una órbita isosincrónica de 22.000 millas por encima del Ecuador. Sin embargo, una transmisión viaja realmente alrededor de 90.000 millas, por lo que una red de satélite tiene una latencia más lenta (500 ms o más) que una red terrestre (20 a 50ms). En la mejor de las condiciones, es posible que no advierta esta latencia, pero, para descargar archivos de gran tamaño, vídeos de streaming y jugar, probablemente lo hará. Otro problema es "atenuación de la lluvia" en el que la intemperie intensa, como Thunderstorms y Blizzards, puede interrumpir temporalmente la transmisión por satélite.
  
## <a name="are-you-sure-its-the-network"></a>¿Está seguro de que es la red?

Cuando experimente problemas de rendimiento, primero asegúrese de que el dispositivo no es la causa raíz del problema. Hay dos cosas que puede hacer y que pueden hacer una mejora importante:
  
- Asegúrese de que el dispositivo se está ejecutando correctamente y de que no hay ningún malware en el equipo.
    
- Si es posible, compre más memoria. Agregar memoria es la forma más sencilla y frecuente de mejorar el rendimiento de su dispositivo. Es especialmente útil cuando se trabaja con archivos y vídeos de gran tamaño.
    
Para obtener más información, vea [Windows Performance and Maintenance](https://windows.microsoft.com/windows/performance-maintenance-help#performance-maintenance-help) and [tips para mejorar el rendimiento del equipo en Windows 10](https://support.microsoft.com/en-za/help/4002019/windows-10-improve-pc-performance).

## <a name="best-practices-for-using-your-browser"></a>Procedimientos recomendados para usar el explorador

El explorador es la puerta de enlace a Office 365, por lo que puede tener un impacto en el rendimiento, especialmente en el tiempo que se tarda en cargar una página y la frecuencia con la que se realiza la ronda de viajes al servicio Office 365. 
  
 **Exploradores en general**
  
Estas son algunas sugerencias para los exploradores en general:
  
- Deshabilite los complementos del explorador que puedan afectar al rendimiento o que realmente no necesite.
    
- Aumente el tamaño de la memoria caché para los archivos temporales de Internet.
    
-  Una vez que haya iniciado sesión en su cuenta profesional o educativa, mantenga la ventana del explorador abierta durante el día. Puede abrir otras pestañas y ventanas sin iniciar sesión de nuevo. Si necesita iniciar sesión en otra cuenta, use la exploración privada. 
    
- Una vez que se haya descargado y abierto cada página, manténgala abierta con pestañas. Es fácil desplazarse entre las pestañas y usar la página más adelante en el día. Actualice una página solo si necesita los datos más recientes en esa página.
    
- Si una página tarda mucho tiempo en abrirse, detenga la descarga de la página (presione ESC) y, a continuación, actualice la página (presione F5). 
    
-  Cuando sea posible, reduzca los viajes de ida y vuelta a Office 365. Por ejemplo, en lugar de paginar a través de listas o bibliotecas, use la búsqueda para buscar archivos en una biblioteca de gran tamaño y filtrar en una lista para obtener directamente los resultados deseados. O bien, cree vistas que minimicen el tiempo de carga de la página. Para obtener más información, vea [administrar listas y bibliotecas de gran tamaño en Office 365](https://support.office.com/article/b4038448-ec0e-49b7-b853-679d3d8fb784#BKMK_PAGES).
    
- Si el rendimiento de vídeo es deficiente, es posible que puedas descargar el vídeo y ver el vídeo en tu dispositivo. Puede que haya un vínculo de descarga, o puede que pueda hacer clic con el botón secundario en el vínculo de vídeo y seleccionar **Guardar destino como**. 
    
 **Específica del explorador**
  
Estas son algunas sugerencias para su explorador específico:
  
- **Internet Explorer** Actualice a Internet Explorer versión 11 o posterior para obtener mejoras de rendimiento sustanciales respecto a versiones anteriores. Para obtener más información, consulte [Guía de solución de problemas de Internet Explorer](https://support.microsoft.com/help/2437121/troubleshooting-guide-for-internet-explorer-when-you-access-office-365).
    
- **Firefox** Para obtener más información, vea [Firefox es lento o deja de funcionar](https://support.mozilla.org/products/firefox/fix-problems/slowness-or-hanging).
    
- **Safari** Para obtener más información, consulte [Apple-Safari](https://www.apple.com/safari/).
    
- **Cromo** Para obtener más información, consulte la [ayuda de Chrome](https://support.google.com/chrome/?hl=en).
  
## <a name="best-practices-for-using-outlook-and-outlook-web-app"></a>Procedimientos recomendados para usar Outlook y Outlook Web App

La lectura, la escritura y la organización del correo electrónico es una gran parte del día de todos. Tanto Outlook como Outlook Web App (OWA) ofrecen soporte técnico sin conexión. Usar una aplicación de correo electrónico en el smartphone es otra alternativa muy útil. Use las siguientes opciones que mejor se adapten a sus necesidades:
  
- Actualícese a la última versión de Outlook para obtener mejoras sustanciales en el rendimiento sobre las versiones anteriores. 
    
-  Outlook Web App le permite crear mensajes, contactos y eventos de calendario sin conexión que se cargan cuando OWA se puede conectar a Office 365. Para obtener más información acerca de la configuración y el uso de OWA en el modo sin conexión, consulte [uso de Outlook Web App sin](https://support.office.com/article/3214839c-0604-4162-8a97-6856b4c27b36)conexión.
    
- Outlook permite trabajar en modo en caché, en el que se conecta automáticamente siempre que sea posible. Puede hacer que Outlook Descargue todo el buzón o solo una parte de él. Para obtener más información, consulte [activar el modo de intercambio en caché](https://support.office.com/article/7885af08-9a60-4ec3-850a-e221c1ed0c1c) y [trabajar sin conexión en Outlook](https://support.office.com/article/f3a1251c-6dd5-4208-aef9-7c8c9522d633). 
    
- Outlook también ofrece un modo sin conexión. Para usar esto, primero debe configurar el modo en caché para que la información de su cuenta se copie a su equipo. En el modo sin conexión, Outlook intentará conectarse usando la configuración de envío y recepción, o cuando la establezca manualmente para trabajar en línea. Para obtener más información, consulte [trabajar sin conexión para evitar gastos de conexión de datos](https://support.office.com/article/827fe51f-5609-4062-82b4-3578057f9282), cambiar la configuración de [envío y recepción cuando se trabaja sin conexión](https://support.office.com/article/f681ec10-cb14-40cb-8709-1909a13c304a)y [cambiar de trabajar sin conexión a en línea](https://support.office.com/article/2460e4a8-16c7-47fc-b204-b1549275aac9). 
    
- Si tiene un teléfono inteligente, puede usarlo para clasificar el correo electrónico y el calendario a través de la red del proveedor de telefonía. 
    
> [!NOTE]
> Esta es una guía sobre Cuándo usar Outlook o OWA. Si el espacio en disco no es un problema en el dispositivo, Outlook tiene un conjunto completo de características y puede funcionar mejor para usted. Si el espacio en disco es un problema en el dispositivo, considere la posibilidad de usar OWA, que tiene un subconjunto de características, pero que también funciona mejor en una situación en línea. Por supuesto, puede usar cualquiera de las dos porque funcionan bien juntos. 
  
## <a name="best-practices-for-using-onedrive-for-business"></a>Procedimientos recomendados para usar OneDrive para la empresa

OneDrive para la empresa está diseñado desde el principio para trabajar con los archivos en línea y sin conexión. Una vez configurada, la sincronización de los cambios se produce de forma automática y fiable dondequiera que y cuando los haga. Si la red es lenta, puede trabajar con la versión sin conexión de los archivos.
  
La aplicación de sincronización de OneDrive para la empresa incluye una suscripción de SharePoint Online y Office 365 empresa, o bien puede [Descargar](https://support.microsoft.com/kb/2903984) la aplicación de sincronización de onedrive para la empresa de forma gratuita. Esta aplicación también es más rápida que el uso de los comandos **abrir en el explorador** o **cargar** . Para obtener más información, consulte [configurar el equipo para sincronizar los archivos de OneDrive para la empresa en Office 365](https://support.office.com/article/23e1f12b-d896-4cb1-a238-f91d19827a16).
  
Estas son algunas instrucciones adicionales para usar la aplicación de sincronización de OneDrive para la empresa:
  
- Si va a sincronizar una biblioteca de gran tamaño por primera vez, inicie la sincronización fuera del horario laboral, por ejemplo, durante la noche. 
    
- Puede usar la característica [detener la sincronización de una biblioteca con la aplicación de OneDrive para la empresa](https://support.office.com/article/a7e41f1f-3a98-4ca7-9443-f10250688330) para detener temporalmente la sincronización de actualizaciones. Sin embargo, use esta característica durante breves períodos, como algunas horas al mismo tiempo, para evitar la puesta en cola de grandes cantidades de actualizaciones y para minimizar el riesgo de conflictos de combinación si varias personas trabajan en el mismo documento. 
  
## <a name="best-practices-for-using-onenote"></a>Procedimientos recomendados para usar OneNote

Todos los sitios de grupo de SharePoint tienen un bloc de notas de OneNote integrado y puede crear los suyos fácilmente. OneNote es una excelente manera de recopilar la información oportuna que necesita cada día para llevar a cabo las tareas. Por ejemplo, muchos equipos usan OneNote como punto de colección para reuniones semanales, notas del proyecto, ideas, planes e informes de estado. Puede organizar fácilmente esta información dispar usando páginas, secciones y pestañas.
  
La belleza de OneNote es que puede obtener acceso al contenido desde prácticamente cualquier dispositivo, ya sea de escritorio, portátil, tableta o smartphone. Y no tiene que preocuparse de guardar o sincronizar porque OneNote lo hace por usted. 
  
Para obtener más información, vea [Microsoft OneNote](https://office.microsoft.com/onenote).

## <a name="best-practices-for-using-skype-for-business-and-lync-online"></a>Procedimientos recomendados para usar Skype empresarial y Lync Online

A continuación se muestran instrucciones generales para usar Skype empresarial o Lync Online cuando la red es lenta:

- Use la mensajería instantánea siempre que pueda porque funciona bien en una red lenta.
    
- Evite realizar llamadas telefónicas a través de una conexión de red privada virtual (VPN) o de un servicio de acceso remoto (RAS).
    
- Asegúrese de que el dispositivo de audio esté aprobado. Para obtener más información, consulte [teléfonos y dispositivos cualificados para Microsoft Lync](https://docs.microsoft.com/skypeforbusiness/lync-cert/ip-phones).
    
-  Si usa PowerPoint en una presentación en línea, reduzca el tamaño y la complejidad de las diapositivas. Para obtener más información, vea [sugerencias para mejorar el rendimiento de la presentación](https://support.office.com/article/34c82835-5f23-4bf0-98cc-72235bbd2949).
            
-  El rendimiento de vídeo depende en gran parte del rendimiento de la red. Evite usar vídeo si la red es lenta. 

Para obtener más información, vea [calidad de audio o vídeo deficiente en Lync Online](https://support.microsoft.com/kb/2386655)o cómo [solucionar problemas de conexión en Skype empresarial](https://support.office.com/article/troubleshoot-connection-issues-in-skype-for-business-ca302828-783f-425c-bbe2-356348583771).
  
## <a name="best-practices-for-using-sharepoint-lists"></a>Procedimientos recomendados para usar listas de SharePoint

Trabajar con datos de lista sin conexión para "borrar", analizar o notificar datos es una buena forma de minimizar el impacto de una red lenta. Puede leer y escribir la mayoría de las listas de Microsoft Access 2019 y Microsoft Access 2016 vinculando a ellas. También puede exportar una lista a una tabla de Excel, que crea una conexión de datos unidireccional entre la tabla de Excel y la lista. Obtenga información sobre cómo [trabajar sin conexión con las tablas vinculadas a listas de SharePoint](https://support.office.com/article/work-offline-with-tables-that-are-linked-to-sharepoint-lists-5d66594a-6176-4a25-a198-320f13ccf41e).
  
Para obtener más información, vea la sección "más información sobre la administración de listas grandes" en [administrar listas y bibliotecas de gran tamaño en Office 365](https://support.office.com/article/b4038448-ec0e-49b7-b853-679d3d8fb784).
  
## <a name="best-practices-for-customizing-web-pages"></a>Procedimientos recomendados para personalizar páginas web

Cuando se personaliza una página web, es posible que el rendimiento de la página sea deficiente por error. Varios factores pueden tener un impacto, como la complejidad y el tamaño de la página, cuántos elementos Web se agregan, cuántos elementos de lista o biblioteca se muestran inicialmente y la forma de codificar la página.
  
Para obtener más información, vea [ajustar el rendimiento de SharePoint Online](https://docs.microsoft.com/office365/enterprise/tune-sharepoint-online-performance).
  
## <a name="best-practices-for-using-project-online"></a>Procedimientos recomendados para usar Project online

Las instrucciones siguientes pueden ayudarle a mejorar el rendimiento de la red.
  
- Project online y SharePoint Online requieren sincronización, lo que puede tardar mucho tiempo. Si los equipos de proyecto tienen un volumen de negocios bajo, deshabilite la sincronización de sitios de Project para mejorar el rendimiento de las páginas de publicación y detalles de proyectos. Limite la sincronización de Active Directory a los grupos de recursos que realmente necesiten usar el sistema y supervise los posibles problemas de permisos tras la sincronización de grupos grandes. 
    
- Si su organización usa sitios de proyectos, créelos a petición en lugar de automáticamente. Esto acelera la primera experiencia de publicación y evita la creación de sitios y contenido innecesarios.
    
- Las páginas de detalles del proyecto (PDP) pueden desencadenar una actualización de todo el proyecto y iniciar acciones de flujo de trabajo, que pueden ser operaciones que consumen un alto rendimiento. Para evitar que se desencadenen dos procesos de actualización al mismo tiempo en el mismo PDP, evite actualizar los campos de calendario (fecha de inicio, fecha de finalización, fecha de estado y fecha actual) y los campos no programados (nombre de proyecto, Descripción y propietario). 
    
- Reduzca el número de elementos Web y campos personalizados mostrados en cada PDP. Cree un PDP dedicado con los únicos campos que requieren actualización para mejorar la carga y ahorrar tiempo. 
    
- Cuando use OData para la creación de informes, limite la cantidad de datos que consulta en tiempo de ejecución mediante el filtrado del servidor.
    
Para obtener más información, consulte [ajustar el rendimiento de Project online](https://support.office.com/article/12ba0ebd-c616-42e5-b9b6-cad570e8409c).
  
## <a name="whats-the-best-way-to-report-problems"></a>¿Cuál es la mejor forma de informar de los problemas?

Microsoft mejora continuamente el rendimiento general de Office 365 al supervisar la red, medir el ancho de banda y la latencia, mejorar el tiempo de carga de la página, reducir la e/S de disco, rediseñar las páginas para usar una estrategia de descarga mínima, agregar hardware a los centros de datos y agregar más centros de datos. Para obtener más información acerca de cómo comprobar el estado actual e informar de los problemas, consulte [How to check Office 365 Service Health](https://docs.microsoft.com/office365/enterprise/view-service-health).
  
## <a name="see-also"></a>Vea también

[Planeamiento de red y ajuste del rendimiento para Office 365](network-planning-and-performance.md)
  
[Principios de conectividad de red de Office 365](office-365-network-connectivity-principles.md)
  
[Administrar puntos de conexión de Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Preguntas frecuentes sobre extremos de Office 365](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

