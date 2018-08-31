---
title: Ajuste del rendimiento de Office 365 mediante líneas base y el historial de rendimiento
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 8/31/2017
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 1492cb94-bd62-43e6-b8d0-2a61ed88ebae
description: Hay algunos métodos sencillos para comprobar el rendimiento de la conexión entre Office 365 y su negocio que le permiten establecer una línea base aproximada de la conectividad. Conocer el historial de rendimiento del cliente de conexiones de equipo puede ayudarle a detectar problemas emergentes tiempo, identificar y predecir problemas.
ms.openlocfilehash: bb1fe1e1450798e43c15a07610e27450bce6ea5b
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542859"
---
# <a name="office-365-performance-tuning-using-baselines-and-performance-history"></a>Ajuste del rendimiento de Office 365 mediante líneas base y el historial de rendimiento

Hay algunos métodos sencillos para comprobar el rendimiento de la conexión entre Office 365 y su negocio que le permiten establecer una línea base aproximada de la conectividad. Conocer el historial de rendimiento del cliente de conexiones de equipo puede ayudarle a detectar problemas emergentes tiempo, identificar y predecir problemas.
  
Si no está utilizado para trabajar en los problemas de rendimiento, este artículo está diseñado para ayudarle a tener en cuenta algunas preguntas comunes, como ¿cómo sabe el problema que está viendo es un problema de rendimiento y no un incidente de servicio de Office 365? ¿Cómo puede planear un buen rendimiento a largo plazo? ¿Cómo se puede mantener un ojo en el rendimiento? Si su equipo o los clientes se vean un rendimiento lento durante el uso de Office 365, y se pregunta acerca de alguna de estas preguntas, siga leyendo.
  
> [!IMPORTANT]
> **Este momento tiene un problema de rendimiento entre el cliente y Office 365?** Siga los pasos descritos en la [solución de problemas de rendimiento de planeación de Office 365](performance-troubleshooting-plan.md). 
    
## <a name="something-you-should-know-about-office-365-performance"></a>Algo que debe conocer acerca del rendimiento de Office 365

Office 365 se encuentra dentro de una red de Microsoft de gran capacidad, dedicada que se supervisa constantemente no sólo mediante la automatización, pero por personas reales. Parte de la función de mantenimiento de la nube de Office 365 es la creación de optimización del rendimiento y simplificación de donde es posible. Puesto que los clientes de la nube de Office 365 deben conectarse a través de Internet, hay un esfuerzo continuo para ajustar con precisión el rendimiento a través de servicios de Office 365 demasiado. Mejoras de rendimiento se detención nunca realmente en la nube, y hay una gran cantidad de experiencia acumulada con mantener la nube rápido y en buen estado. Debe experimenta un problema de rendimiento que se conectan desde su ubicación a Office 365, es mejor no comenzar con y espere en un caso de soporte técnico. En su lugar, debe comenzar la investigación del problema de 'el inside out'. Es decir, inicie dentro de la red y la manera de averiguar a Office 365. Antes de abrir un caso con soporte técnico de Office 365, puede recopilar datos y realizar las acciones que se va a explorar y pueden resolver el problema.
  
> [!IMPORTANT]
> Tenga en cuenta de planeación de la capacidad y límites en Office 365. Dicha información pondrá su por delante de la curva al intentar resolver un problema de rendimiento. Éste es un vínculo a la [Descripción del servicio de plataforma de Office 365](https://technet.microsoft.com/en-us/library/office-365-service-descriptions.aspx). Se trata de un concentrador central y todos los servicios que ofrece Office 365 tienen un vínculo que vaya a sus propios descripciones del servicio desde aquí. Esto significa que si necesita ver los límites de estándares de SharePoint Online, por ejemplo, haría clic [Descripción del servicio de SharePoint Online](https://technet.microsoft.com/en-us/library/sharepoint-online-service-description.aspx) y busque su [sección límites de SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkID=856113). 
  
Asegúrese de que vaya a la solución de problemas con la descripción que el rendimiento es una escala móvil, no resulta acerca de lograr un valor idealizado y mantenimiento de forma permanente (si cree que esto es así, a continuación, tareas de ancho de banda alto ocasionales like incorporación un gran número de usuarios, o realizar migraciones de datos de gran tamaño será mucho estrés--por lo que planear repercusión en el rendimiento, a continuación,). Puede y debe, tener una idea general de los objetivos de rendimiento, pero una gran cantidad de variables reproducir en el rendimiento, por lo tanto, rendimiento varía. Es la naturaleza de rendimiento. 
  
Solución de problemas de rendimiento no es acerca de los objetivos específicos de la reunión y mantenimiento de dichos números de forma indefinida, es sobre cómo mejorar las actividades existentes, dado todas las variables. 
  
## <a name="okay-what-does-a-performance-problem-look-like"></a>Bien, ¿qué es un problema de rendimiento el aspecto?

En primer lugar, debe asegurarse de que está experimentando es realmente un problema de rendimiento y no un incidente de servicio. Un problema de rendimiento es diferente de un incidente de servicio en Office 365. Así es como con respecto a aparte.
  
Si el servicio Office 365 está teniendo problemas, es un incidente de servicio. Podrá ver los iconos de color rojos o amarillos en **mantenimiento actual** en el centro de administración de Office 365, es posible que Observe también un rendimiento lento en los equipos cliente que se conectan a Office 365. Por ejemplo, si un icono rojo con informes de mantenimiento actual y vea **Investigating** al lado de Exchange, es posible que, a continuación, también recibe un montón de llamadas de los usuarios en su organización se quejan de que los buzones de los clientes que usen Exchange Online están realizando construida. En ese caso, es razonable asumir que el rendimiento de Exchange Online sólo se convirtió en una víctima de problemas en el servicio. 
  
![El panel de mantenimiento de Office 365 con todas las cargas de trabajo que muestra verde, excepto Exchange, lo que se muestra el servicio restaurado.](media/ec7f0325-9e61-4e1a-bec0-64b87f4469be.PNG)
  
En este momento, el Administrador de Office 365, debe comprobar **mantenimiento actual** y, a continuación, **historial y los detalles de la vista**, con frecuencia, para mantener actualizados en mantenimiento llevamos a cabo en el sistema. Se ha realizado actualizada acerca de problemas en el servicio y los cambios realizados en el panel de **estado actual** . Las notas y explicaciones escritos en historial de mantenimiento, administración para la administración, son hay que le ayudarán a evaluar su impacto y para mantener registrar sobre el trabajo en curso. 
  
![Una imagen del mantenimiento de Office 365 panel que explica que se ha restaurado el servicio Exchange Online y por qué.](media/66609554-426a-4448-8be6-ea09817f41ba.PNG)
  
Un problema de rendimiento no es un incidente de servicio, aunque incidentes pueden provocar un rendimiento lento. Un problema de rendimiento tiene este aspecto:
  
- Se produce un problema de rendimiento independientemente de qué es informes el centro de administración de Office 365 **mantenimiento actual** para el servicio. 
    
-  Un comportamiento que solía ser relativamente transparente tarda mucho tiempo en completarse o nunca se completa. 
    
- Puede replicar el problema demasiado, o bien, al menos, sabrá que sucederá si lo hace la serie de pasos derecha.
    
-  Si el problema es intermitente, sigue siendo un patrón, por ejemplo, sabe que por 10:00 AM tendrá las llamadas de los usuarios que no tienen acceso confiable a Office 365, y que las llamadas se dado alrededor del mediodía. 
    
Esto probablemente le resulta familiar; quizá demasiado familiar. Una vez que sepa que es un problema de rendimiento, la pregunta es: "¿qué hacer a continuación?" El resto de este artículo le ayudará a determinar exactamente.
  
## <a name="how-to-define-and-test-the-performance-problem"></a>Cómo definir y probar el problema de rendimiento

Problemas de rendimiento a menudo surgen a través del tiempo, por lo que puede ser un reto para definir el problema real. Que necesita para crear una instrucción de buena problema y una buena idea del contexto del problema y, a continuación, necesitará repetibles pasos de prueba para ganar el día. De lo contrario, a través de ningún error de sus propios, es posible que se perderán. ¿Por qué? Bueno, estos son algunos ejemplos de instrucciones de problemas que no proporcionan suficiente información como:
  
- Cambio de la Bandeja de entrada a mi calendario solía ser algo que no tenga en cuenta y ahora es un descanso. ¿Puede hacer que actúan como solía?
    
- Cargar Mis archivos en SharePoint Online está tomando una eternidad. ¿Por qué resulta lenta en la tarde, pero cualquier otro momento, es rápido? ¿No se puede simplemente ser rápido?
    
Existen varios desafíos grandes que suponen las instrucciones del problema anteriores. En concreto, hay una gran cantidad de ambigüedades para abordar los problemas con. Por ejemplo:
  
- No está claro cómo cambiar entre la Bandeja de entrada y el calendario utilizado para que actúe en el equipo portátil.
    
- Cuando el usuario dice "no ser simplemente fast", ¿qué es "fast"?
    
- ¿Cuánto tiempo es "para siempre"? ¿Es que varios segundos o minutos, o el usuario se pudo ir a comer y podría terminar diez minutos después de que el usuario hemos obtenido?
    
Todo esto es sin tener en cuenta que no tenga el Solucionador de problemas y administración de muchos de los detalles de las instrucciones de problema como estos. Por ejemplo, cuando inicia el problema ocurra; Que el usuario trabaja desde casa y solo nunca ve conmutación lentas mientras se encuentra en una red doméstica; Que el usuario debe ejecutar varias otras aplicaciones intensivas de memoria RAM en el cliente local o el usuario se está ejecutando un sistema operativo anterior o no ejecuta las actualizaciones más recientes.
  
Cuando los usuarios tengan un problema de rendimiento, hay una gran cantidad de información para recopilar. Recopilación de esta información es parte de un proceso que se denomina el problema de ámbito o investigarlo. La siguiente es una lista de alcance básica que se puede usar para recopilar información sobre el problema de rendimiento. Esta lista no es exhaustiva, pero es un punto de partida uno de sus propios: 
  
- ¿En qué fecha hizo el problema ocurrirá y alrededor de en qué momento del día o de la noche?
    
- ¿Qué tipo de equipo cliente estaba utilizando, y cómo se conecta a la red de empresa (VPN, con cable, inalámbrico)?
    
- ¿Se ha trabajan de forma remota o estaban en la oficina?
    
- ¿Pruebe las mismas acciones en otro equipo y vea el mismo comportamiento?
    
- Recorra los pasos que se están dando el problema para que pueda escribir las acciones que realizar hacia abajo.
    
- ¿Cómo lento en segundos o minutos es el rendimiento?
    
- ¿Dónde en el mundo se encuentra?
    
Algunas de estas preguntas son más obvios que otros. La mayoría todos sabrá que un solucionador de problemas necesita los pasos exactos para reproducir el problema. ¿Después de todo, cómo else puede registrar qué es incorrecta y qué otra forma se puede probar si se corrige el problema? Menos obvias son cosas como "¿qué fecha y hora en hizo vea el problema?" y "Donde en el mundo está ubicado?", la información que se puede usar conjuntamente. Función cuando el usuario estaba trabajando, unas pocas horas de diferencia de tiempo pueden significar mantenimiento ya está en curso en partes de la red de su empresa. Si, por ejemplo, su compañía tiene una implementación híbrida, al igual que una búsqueda de SharePoint, que puede consultar híbrida índices de búsqueda en SharePoint Online y un servidor de SharePoint local instancia de 2013, las actualizaciones pueden estar en curso en la granja de servidores local. Si su compañía es todo en la nube, puede incluir mantenimiento del sistema, agregar o quitar hardware de red, implantar las actualizaciones de toda la compañía, o realizar cambios en DNS o en otro infraestructura básica.
  
Cuando está solucionando un problema de rendimiento, es un poco como una escena delito, debe ser precisa y atento para dibujar cualquier conclusiones de las pruebas. Para ello, debe obtener una instrucción problema buena mediante la recopilación de evidencia. Deben incluir el contexto del equipo, el contexto del usuario, cuando comenzó el problema y los pasos exactos que exponen el problema de rendimiento. Esta declaración de problema debe ser y permanecer, la página de nivel superior en las notas. Recorriendo la instrucción problema nuevo después de trabajar en la resolución, están teniendo los pasos para probar y comprobar si las acciones que realizar han resuelto el problema. Esto es fundamental para saber cuándo se realiza el trabajo, allí.
  
## <a name="do-you-know-how-performance-used-to-look-when-it-was-good"></a>¿Sabe cómo rendimiento se usa para buscar cuando estaba buena?

Si está de suerte, nadie sabe. Nadie tenía números. Esto significa que nadie puede responder a la pregunta simple "acerca de cuántos segundos hizo utilizado para tomar para que aparezca una bandeja de entrada en Office 365?" o "¿durante cuánto tiempo hizo utilizado para tomar cuando los ejecutivos tenían una Lync Online reunión?", que es un escenario común para muchas compañías.
  
¿Qué es que faltan aquí es una referencia de rendimiento.
  
Las líneas de base proporcionan un contexto para el rendimiento. Debe tener una línea de base de vez en cuando para con frecuencia, según las necesidades de su compañía. Si es una compañía más grande, su equipo de operaciones puede tardar ya las líneas de base para el entorno local. Por ejemplo, si la revisión de todos los servidores de Exchange en el primer lunes del mes y todos los servidores de SharePoint en el tercer lunes, su equipo de operaciones probablemente tiene una lista de tareas y escenarios se ejecuta posteriores a la aplicación de revisiones, demostrar que son funciones críticas operativas. Por ejemplo, abrir la Bandeja de entrada, al hacer clic en enviar y recibir y, asegurándose de que las carpetas de actualización, o bien, en SharePoint, explore la página principal del sitio, entrar en la página de búsqueda de empresa y se realiza una búsqueda que devuelve los resultados de.
  
Si las aplicaciones se encuentran en Office 365, algunas de las líneas de base más fundamentales que se pueden realizar de medir el tiempo (en milisegundos) de un equipo cliente dentro de la red a un punto de salida o el punto donde abandonar la red y empezaran a Office 365. A continuación presentamos algunas líneas base útiles que puede investigar y registro:
  
- Identificar los dispositivos entre el equipo cliente y el punto de salida, por ejemplo, el servidor proxy.
    
  - Necesita saber los dispositivos de modo que tenga contexto (direcciones IP, el tipo de dispositivo, et cetera) para ver si surgen problemas de rendimiento.
    
  - Los servidores proxy son los puntos de salida comunes, por lo que puede comprobar su explorador web para ver qué servidor proxy que está configurado para usar, si hay alguno.
    
  - Existen herramientas de terceros que pueden detectar y asignar la red, pero es la forma más segura para conocer los dispositivos pedir a un miembro del equipo de su red.
    
- Identificar su proveedor de servicios Internet (ISP), anote su información de contacto y pregunte ¿cuántos circuitos cuánto ancho de banda tiene.
    
- Dentro de su compañía, identificar los recursos para los dispositivos entre el cliente y el punto de salida, o un contacto de emergencia a hablar con acerca de problemas de red.
    
A continuación presentamos algunos simples las pruebas con las herramientas de líneas de base pueden calcular para:
  
- Tiempo desde el equipo cliente para su punto de salida en milisegundos
    
- Tiempo desde el punto de salida a Office 365 en milisegundos
    
- Ubicación en el mundo del servidor que se resuelve las direcciones URL para Office 365 al examinar
    
- La velocidad de resolución DNS de su ISP en milisegundos, las incoherencias de llegada de paquete (vibración de la red), cargar y descargar veces en milisegundos
    
Si no está familiarizado con cómo llevar a cabo estos pasos, abordaremos en más detalle en este artículo. 
  
## <a name="what-is-a-baseline"></a>¿Qué es una línea de base?

Cuando sale mal, pero si no conoce los datos de rendimiento históricos, no es posible tener un contexto de forma incorrecta es posible que se han convertido en y cuando se sabrá el impacto. Por lo que faltan sin una línea de base, la pista clave para resolver el puzzle: la imagen en el cuadro de puzzle. La solución de problemas de rendimiento, es necesario un punto de *comparación* . Las líneas de base de rendimiento simple no son difíciles de tomar. Su equipo de operaciones puede ser la obligación de estos llevar a cabo en una programación. Por ejemplo, supongamos que la conexión tiene este aspecto: 
  
![Un gráfico de red básica que muestra cliente, el proxy y la nube de Office 365.](media/c6ca7140-09f9-4c2d-a775-dbf2820eaa0c.PNG)
  
Esto significa que ha verificado con su equipo de red y descubrió que deja la compañía para Internet a través de un servidor proxy, y ese proxy administra todas las solicitudes que el equipo cliente envía a la nube. En este caso, debe dibujar una versión simplificada de la conexión que se enumera todos los dispositivos intermedios. Ahora, inserte las herramientas que puede usar para probar el rendimiento entre el cliente, el punto de salida (donde dejar la red de Internet) y Office 365 en la nube.
  
![Red básica con el cliente, el proxy y en la nube y las sugerencias de herramientas PSPing, TraceTCP y los seguimientos de red.](media/627bfb77-abf7-4ef1-bbe8-7f8cbe48e1d2.png)
  
Las opciones aparecen como **simples** y **Avanzadas** debido a la cantidad de experiencia que se necesitan para encontrar los datos de rendimiento. Un seguimiento de red tendrán una gran cantidad de tiempo, en comparación con a la ejecución de las herramientas de línea de comandos como PsPing y TraceTCP. Estas dos herramientas de línea de comandos se eligieron porque no usan los paquetes ICMP, que se bloqueará por Office 365, y ya que proporcionan el tiempo en milisegundos que tarda deje el equipo cliente o servidor proxy (si se dispone de acceso) y llegan a Office 365. Cada salto individual de un equipo a otro se terminan con un valor de hora, y que es ideal para las líneas de base! Al igual que lo que es importante, estas herramientas de línea de comandos le permiten agregar un número de puerto en el comando, esto es útil porque Office 365 se comunica a través del puerto 443, que es el puerto usado por la capa de Sockets seguros y seguridad de la capa de transporte (SSL y TLS). Sin embargo, otras herramientas de terceros pueden ser mejores soluciones para su situación. Microsoft no admitan todas estas herramientas, por lo que si, por algún motivo, no se puede obtener PsPing y TraceTCP trabajar, moverse a un seguimiento de red con una herramienta como Netmon. 
  
Puede realizar una línea de base antes de horas de trabajo, vuelva a durante un uso intensivo y, a continuación, vuelva a después del horario laboral. Esto significa que es posible que tenga una estructura de carpetas que un poco tiene este aspecto al final:
  
![Gráfico que propone una manera de organizar los datos de rendimiento en carpetas.](media/13e01ffa-f0f2-4d10-b89d-d5980ec89fae.png)
  
También debe elegir una convención de nomenclatura de los archivos. Estos son algunos ejemplos:
  
- Feb_09_2015_9amPST_PerfBaseline_Netmon_ClientToEgress_Normal
    
- Jan_10_2015_3pmCST_PerfBaseline_PsPing_ClientToO365_bypassProxy_SLOW
    
- Feb_08_2015_2pmEST_PerfBaseline_BADPerf
    
- Feb_08_2015_8 30amEST_PerfBaseline_GoodPerf
    
Hay una gran cantidad de distintas maneras de hacer esto, pero con el formato ** \<dateTime\>\<lo que sucede en la prueba\> ** es un buen punto de partida. Que se va a diligente sobre esto le ayudará a mucho cuando intenta solucionar problemas más adelante. Más adelante, podrá diga "tuvieron dos seguimientos de 8 de febrero, uno mostraron un buen rendimiento y uno mostró incorrecta, por lo que podemos compararlos". Esto es muy útil para solucionar problemas. 
  
Debe tener una forma organizada para mantener sus líneas de base históricas. En este ejemplo, los métodos simples producen tres salidas de línea de comandos y los resultados se recopilaron como capturas de pantalla, pero es posible que tenga archivos de captura de red en su lugar. Utilice el método que mejor se adapte a. Almacenar sus líneas de base históricas y hacer referencia a ellos en los puntos donde se tenga en cuenta los cambios en el comportamiento de los servicios en línea. 
  
## <a name="why-collect-performance-data-during-a-pilot"></a>¿Por qué recopilar datos de rendimiento durante una prueba piloto?

No hay ningún mejor momento para empezar a realizar las líneas de base que durante una prueba piloto del servicio Office 365. Su oficina puede tener miles de usuarios, cientos de miles, o bien pueden tener cinco pero, incluso con un número pequeño de usuarios, puede realizar pruebas para medir las fluctuaciones de rendimiento. En el caso de una empresa de gran tamaño, un ejemplo representativo de varios cientos de usuarios piloto Office 365 puede proyectar hacia fuera a varios miles para que sepan dónde pueden surgir problemas antes de que ocurran.
  
En el caso de una pequeña empresa, donde incorporación significa que todos los usuarios vaya al servicio al mismo tiempo y no hay ningún piloto, mantenga las medidas de rendimiento para que dispone de datos para mostrar a cualquier persona que deba solucionar problemas de una operación mal rendimiento. Por ejemplo, si observa de repente puede recorrer alrededor de su creación en el tiempo que se tarda en cargar un gráfico de tamaño mediano donde solía ocurrir muy rápidamente.
  
## <a name="how-to-collect-baselines"></a>Cómo recopilar las líneas de base

Para todos los planes de solución de problemas debe identificar estas cosas como mínimo:
  
- El equipo cliente que está utilizando (el tipo de equipo o dispositivo, una dirección IP y las acciones que ha provocado el problema)
    
- ¿Dónde se encuentra el equipo cliente en el mundo (por ejemplo, si este usuario en una conexión VPN a la red, trabajar de forma remota, o en la intranet de la compañía)
    
- El punto de salida del equipo cliente usa desde la red (es decir, el punto en el que el tráfico deja su negocio para un ISP o Internet)
    
 Puede averiguar el diseño de la red desde el Administrador de la red. Si está en una red pequeña, eche un vistazo a los dispositivos que se conecta a Internet y llamar a su ISP si tiene alguna pregunta sobre el diseño. Crear un gráfico que muestra el diseño final para su referencia. 
  
En esta sección se divide en los métodos y las herramientas de línea de comandos simples y más avanzados de herramientas, opciones. En primer lugar trataremos métodos simples. Pero si tiene un problema de rendimiento ahora mismo, debe pasar a métodos avanzados y probar el plan de acción de solución de problemas de rendimiento de ejemplo.
  
### <a name="simple-methods"></a>Métodos simples

El objetivo de estos métodos simples es aprender a tomar, comprender y almacenar correctamente las líneas de base de rendimiento simple a través del tiempo para que se le informa sobre el rendimiento de Office 365. Aquí es el diagrama muy simple para simple, como se ha visto antes:
  
![Red básica con el cliente, el proxy y en la nube y las sugerencias de herramientas PSPing, TraceTCP y los seguimientos de red.](media/627bfb77-abf7-4ef1-bbe8-7f8cbe48e1d2.png)
  
> [!NOTE]
> TraceTCP se incluye en esta pantalla captura porque es una herramienta muy útil para mostrar, en milisegundos, cuánto tiempo tarda una solicitud en proceso y cuántos saltos de red o las conexiones de un equipo a la siguiente, que realiza la solicitud para llegar a un destino. TraceTCP también puede proporcionar los nombres de servidores que se utilizan durante saltos, que pueden ser útiles para un solucionador de problemas de Microsoft Office 365 en soporte técnico. > Pueden ser muy simples, como comandos TraceTCP: > `tracetcp.exe outlook.office365.com:443`> no olvide incluir el número de puerto en el comando! > [TraceTCP](https://simulatedsimian.github.io/tracetcp.mdl) es una descarga gratuita, pero se basa en Wincap. Wincap es una herramienta que se utiliza y se instala de forma Netmon también. También usamos Netmon en la sección métodos avanzados. 
  
 Si tiene varias oficinas, debe mantener un conjunto de datos desde un cliente en cada una de esas ubicaciones también. Esta latencia de medidas de prueba, que, en este caso, es un valor numérico que describe la cantidad de tiempo entre un cliente envía una solicitud a Office 365 y responder a la solicitud de Office 365. Las pruebas se origen dentro de su dominio en un equipo cliente y tiene el aspecto para echar una ida y vuelta desde dentro de la red a través de un punto de salida, a través de Internet a Office 365 y realizar una copia. 
  
Hay varias maneras de abordar los problemas con el punto de salida, en este caso, el servidor proxy. Puede rastrear de 1 a 2 y, a continuación, 2 y 3 y, a continuación, agregar los números en milisegundos para obtener un total final hasta el borde de la red. O bien, puede configurar la conexión para utilizar al servidor proxy para las direcciones de Office 365. En una red más grande con un servidor de seguridad, proxy inverso o una combinación de los dos, debe hacer excepciones en el servidor proxy que se va a permitir el tráfico pasar de una gran cantidad de direcciones URL. Para obtener la lista de extremos utilizados por Office 365, vea [las direcciones URL de Office 365 y los intervalos de direcciones IP](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2). Si tiene un proxy de autenticación, comience por las pruebas de excepciones para lo siguiente:
  
- Puertos 80 y 443
    
- TCP y HTTPs
    
- Conexiones de salida a cualquiera de estas direcciones URL:
    
- \*. microsoftonline.com
    
- \*.microsoftonline p.com
    
- \*. sharepoint.com
    
- \*. outlook.com
    
- \*. lync.com
    
- osub.Microsoft.com
    
Todos los usuarios necesitan que se les para llegar a estas direcciones sin autenticación ni interferencias de proxy. En una red más pequeña, debe agregar que estas a su proxy de desvío de lista en el explorador web. 
  
Para agregar a la lista de omisión de proxy en Internet Explorer, vaya a **Herramientas** \> **Opciones de Internet** \> **conexiones** \> **configuración de LAN** \> **Avanzadas**. La ficha Opciones avanzadas también es donde se encuentra el servidor proxy y el puerto del servidor proxy. Puede que tenga que hacer clic en la casilla de verificación **utilizar un servidor proxy para la LAN**, para tener acceso al botón **Opciones avanzadas** . Desea asegurarse de que se comprueba el **servidor proxy para direcciones locales** . Una vez que haga clic en **Avanzadas**, verá un cuadro de texto donde puede escribir excepciones. Separe las direcciones URL de comodín indicadas anteriormente con punto y coma, por ejemplo:
  
\*. microsoftonline.com; \*. sharepoint.com
  
Una vez que omitir al servidor proxy, debe usar ping o PsPing directamente en una dirección de URL de Office 365. El siguiente paso será probar ping **outlook.office365.com**. O bien, si está utilizando PsPing u otra herramienta que le permita proporcionar un número de puerto para el comando, PsPing contra **portal.microsoftonline.com:443** para ver el tiempo promedio ida y vuelta en milisegundos. 
  
El tiempo de ida y vuelta o RTT, es un valor numérico que mide cuánto tarda en enviar una solicitud HTTP a un servidor al igual que outlook.office365.com y obtener una respuesta que reconoce que el servidor sabe que lo hizo. A veces, verá lo abreviada como RTT. Debe ser una cantidad relativamente breve de tiempo.
  
Se debe usar [PSPing](https://technet.microsoft.com/en-us/sysinternals/jj729731.aspx) u otra herramienta que no use paquetes ICMP que están bloqueados por Office 365 con el fin de realizar esta prueba. 
  
 **Cómo usar PsPing para obtener una general viaje de ida y tiempo en milisegundos directamente desde una dirección de URL de Office 365**
  
1. Ejecute un símbolo del sistema con privilegios elevados, siga estos pasos:
    
1. Haga clic en **Iniciar**.
    
2. En el cuadro **Iniciar búsqueda** , escriba cmd y, a continuación, presione CTRL + MAYÚS + ENTRAR.
    
3. Si aparece el cuadro de diálogo **Control de cuentas de usuario**, confirme que la acción que muestra es la que desea y, a continuación, haga clic en **Continuar**.
    
2. Navegue a la carpeta donde está instalada la herramienta (en este caso PsPing) y probar estos las direcciones URL de Office 365:
    
  - psping portal.office.com:443
    
  - psping microsoft-my.sharepoint.com:443
    
  - psping outlook.office365.com:443
    
  - psping www.yammer.com:443
    
    ![El comando PSPing va a microsoft-my.sharepoint.com puerto 443.](media/3258f620-4513-4e82-95c9-06b387fc3a82.PNG)
  
No olvide incluir el número de puerto 443. Recuerde que Office 365 funciona en un canal cifrado. Si se PsPing sin el número de puerto, la solicitud se producirá un error. Una vez que haya un ping a su lista de short, busque el tiempo promedio en milisegundos (ms). Eso es lo que desea registrar!
  
![Gráfico que muestra una ilustración de cliente a servidor proxy PSPing con un tiempo de ida y vuelta de 2,8 milisegundos.](media/96901aea-1093-4f1b-b5a3-6078e9035e6c.png)
  
Si no está familiarizado con el desvío de proxy y prefieren tomar cosas paso a paso, debe averiguar primero el nombre del servidor proxy. En Internet Explorer, vaya a **Herramientas** \> **Opciones de Internet** \> **conexiones** \> **configuración de LAN** \> **Avanzadas**. La ficha **Opciones avanzadas** es donde podrá ver su servidor proxy que aparece. Al completar esta tarea, puede hacer ping a ese servidor proxy en un símbolo del sistema: 
  
 **Haga ping al servidor proxy y obtener un valor de ida y vuelta en milisegundos para la fase 1 y 2**
  
1. Ejecute un símbolo del sistema con privilegios elevados, siga estos pasos:
    
1. Haga clic en **Iniciar**.
    
2. En el cuadro **Iniciar búsqueda** , escriba cmd y, a continuación, presione CTRL + MAYÚS + ENTRAR.
    
3. Si aparece el cuadro de diálogo **Control de cuentas de usuario**, confirme que la acción que muestra es la que desea y, a continuación, haga clic en **Continuar**.
    
2. Escriba ping \<el nombre del servidor proxy utiliza su explorador o la dirección IP del servidor proxy\> y, a continuación, presione ENTRAR. Si tiene PsPing, o alguna otra herramienta, instalado, puede elegir usar dicha herramienta en su lugar. 
    
    El comando puede ser similar a cualquiera de estos ejemplos: 
    
  - ping ourproxy.ourdomain.industry.business.com
    
  - ping 155.55.121.55
    
  - ping ourproxy
    
  - psping ourproxy.ourdomain.industry.business.com:80
    
  - psping 155.55.121.55:80
    
  - psping ourproxy:80
    
3. Cuando el seguimiento detiene el envío de paquetes de prueba, obtendrá un pequeño resumen que muestra un promedio, en milisegundos, y que es el valor que está después. Tomar una captura de pantalla del símbolo del sistema y guárdelo con la convención de nomenclatura. En este momento también puede ayudar a rellenar en el diagrama con el valor.
    
Quizá ha elegido un seguimiento en las primeras horas de la mañana, y su cliente puede obtener rápidamente para el proxy (o sale de cualquier servidor de salida a Internet). En este caso, los números es posible que este aspecto:
  
![Gráfico que muestra el tiempo de ida y vuelta desde un cliente a un proxy de 2,8 milisegundos.](media/1bd03544-23fc-47d4-bbae-c1feb466a5d8.PNG)
  
Si el equipo cliente es uno de los pocos select con acceso al servidor proxy (o salida), puede ejecutar el siguiente tramo de la prueba mediante la conexión de forma remota a dicho equipo que ejecute el símbolo del sistema a PsPing a una dirección de URL de Office 365 desde allí. Si no tiene acceso a ese equipo, puede ponerse en contacto con los recursos de red para obtener ayuda con el tramo siguiente y get exacta números de esta forma. Si eso no es posible, tomar un PsPing contra la dirección de URL de Office 365 en cuestión y comparar a la hora de PsPing o Ping en el servidor proxy. 
  
Por ejemplo, si tiene 51.84 milisegundos desde el cliente a la dirección de URL de Office 365 y tiene 2,8 milisegundos desde el cliente para el proxy (o el punto de salida), a continuación, debe 49.04 milisegundos desde la salida a Office 365. Del mismo modo, si tiene un PsPing de 12.25 milisegundos desde el cliente para el servidor proxy durante el alto del día y 62.01 milisegundos desde el cliente a la dirección de URL de Office 365, el valor medio de la salida de proxy para las direcciones URL en Office 365 es 49.76 milisegundos.
  
![Gráfico adicional que muestra el comando ping en milisegundos, desde el cliente al proxy al lado de cliente de Office 365 por lo que se pueden restar los valores.](media/cd764e77-5154-44ba-a5cd-443a628eb2d9.PNG)
  
En cuanto a la solución de problemas, es posible que encuentre algo interesante acaba de mantener estas líneas de base. Por ejemplo, si observa que generalmente tienen acerca de 40 a 59 milisegundos de latencia desde el proxy o salida apunte a la dirección de URL de Office 365 y tiene un cliente de proxy o salida latencia de punto de aproximadamente 3 a 7 milisegundos (dependiendo de la red de la cantidad de tráfico está seein g durante esa hora del día), a continuación, seguramente sabrá algo es un inconveniente si su cliente tres últimas posiciones en las líneas de base proxy o salida mostrar una latencia de 45 milisegundos.
  
### <a name="advanced-methods"></a>Métodos avanzados

Si realmente desea saber lo que sucede con las solicitudes de Internet a Office 365, debe familiarizarse con los seguimientos de red. No importa qué herramientas que prefiera para estos seguimientos, HTTPWatch, Netmon, analizador de mensaje, Wireshark, Fiddler, herramienta de panel del programador o cualquier otra llevará a cabo mientras que la herramienta puede capturar y filtrar el tráfico de red. En esta sección verá que es beneficioso ejecutar más de una de estas herramientas para obtener una imagen más completa del problema. Cuando se está probando, algunas de estas herramientas también que actúan como proxies en su propios derecha. Las herramientas usadas en el artículo complementarios, [solución de problemas de rendimiento de planeación de Office 365](performance-troubleshooting-plan.md), incluyen [Netmon 3.4](https://www.microsoft.com/en-us/download/details.aspx?id=4865), [HTTPWatch](https://www.httpwatch.com/download/)o [WireShark](https://www.wireshark.org/).
  
Teniendo una referencia de rendimiento es la parte sencilla de este método y muchos de los pasos son los mismos que para solucionar un problema de rendimiento. Los métodos más avanzados de la creación de las líneas de base para el rendimiento, es necesario tomar y almacenar los seguimientos de red. La mayoría de los ejemplos de este artículo usa SharePoint Online, pero debe desarrollar una lista de acciones comunes entre los servicios de Office 365 a los que suscribirse para probar y registrar. Este es un ejemplo de línea de base:
  
- Lista de línea base para SPO - ** paso 1: ** examinar la página principal del sitio Web SPO y hacer un seguimiento de red. Guarde el seguimiento. 
    
- Lista de línea base para SPO - **paso 2:** búsqueda para un término (por ejemplo, el nombre de su compañía) a través de búsqueda Enterprise Search y hacer un seguimiento de red. Guarde el seguimiento. 
    
- Lista de línea base para SPO - **paso 3:** cargar un archivo grande a una biblioteca de documentos de SharePoint Online y realice un seguimiento de red. Guarde el seguimiento. 
    
- Lista de línea base para SPO - **paso 4:** examinar la página principal del sitio Web de OneDrive y hacer un seguimiento de red. Guarde el seguimiento. 
    
Esta lista debe incluir las acciones comunes más importantes que los usuarios tomar frente a SharePoint Online. Tenga en cuenta que el último paso, hacer un seguimiento que se va a OneDrive para la empresa, compilaciones-en una comparación entre la carga de la página principal de SharePoint Online (que normalmente está personalizada por las compañías) y OneDrive para la página principal de negocio, que rara vez se ha personalizado. Esto es una prueba muy básica cuando se trata de un sitio de SharePoint Online lentitud al cargar. Puede crear un registro de esta diferencia en las pruebas.
  
Si se encuentra en medio de un problema de rendimiento, muchos de los pasos son los mismos que cuando teniendo una línea base. Los seguimientos de red se conviertan en críticos, por lo que se podrá controlar *cómo* para tomar los seguimientos importantes siguiente. 
  
Para solucionar un problema de rendimiento, *ahora mismo* , debe tener un seguimiento en el momento en que está experimentando el problema de rendimiento. Debe tener las herramientas adecuadas disponibles para recopilar los registros y necesita un plan de acción, es decir, una lista de acciones para recopilar la información de procedimientos que puede utilizar de la solución de problemas. Lo primero que debe hacer es registrar la fecha y hora de la prueba de modo que los archivos pueden guardarse en una carpeta que reflejen el momento oportuno. A continuación, se estrechan hacia abajo a los propios pasos del problema. Estos son los pasos exactos que se va a usar para las pruebas. No se olvide de los conceptos básicos: si el problema está relacionado sólo con Outlook, asegúrese de que al registro que el comportamiento de problema ocurre en un solo servicio de Office 365. Limitar el ámbito de este problema le ayudará a centrarse en algo que puede resolver. 
  
## <a name="see-also"></a>Vea también

[Administración de extremos de Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)

