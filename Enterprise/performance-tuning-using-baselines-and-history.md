---
title: Ajuste del rendimiento de Office 365 mediante líneas base y el historial de rendimiento
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 8/31/2017
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 1492cb94-bd62-43e6-b8d0-2a61ed88ebae
ms.collection:
- M365-security-compliance
- Ent_O365
description: Hay sencillas formas de comprobar el rendimiento de la conexión entre Office 365 y su empresa que le permitirá establecer una línea de base aproximada de su conectividad. Conocer el historial de rendimiento de las conexiones de los equipos cliente puede ayudarle a detectar los problemas emergentes con anticipación, la identificación y la predicción de los problemas.
ms.openlocfilehash: 755f4c4bde7e040638e768002a528710bcdd48fd
ms.sourcegitcommit: 1c97471f47e1869f6db684f280f9085b7c2ff59f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/18/2019
ms.locfileid: "35781910"
---
# <a name="office-365-performance-tuning-using-baselines-and-performance-history"></a>Ajuste del rendimiento de Office 365 mediante líneas base y el historial de rendimiento

Hay sencillas formas de comprobar el rendimiento de la conexión entre Office 365 y su empresa que le permitirá establecer una línea de base aproximada de su conectividad. Conocer el historial de rendimiento de las conexiones de los equipos cliente puede ayudarle a detectar los problemas emergentes con anticipación, la identificación y la predicción de los problemas.
  
Si no se usa para trabajar en problemas de rendimiento, este artículo está diseñado para ayudarle a tener en cuenta algunas preguntas comunes, como por ejemplo, cómo sabe que el problema que está viendo es un problema de rendimiento y no un incidente del servicio de Office 365. ¿Cómo puede planear el buen rendimiento, a largo plazo? ¿Cómo se puede vigilar el rendimiento? Si el equipo o los clientes ven un rendimiento lento mientras usan Office 365 y se pregunta sobre cualquiera de estas preguntas, siga leyendo.
  
> [!IMPORTANT]
> **¿Tiene un problema de rendimiento entre su cliente y Office 365 ahora?** Siga los pasos descritos en el [plan de solución de problemas de rendimiento para Office 365](performance-troubleshooting-plan.md). 
    
## <a name="something-you-should-know-about-office-365-performance"></a>Algo que debe saber sobre el rendimiento de Office 365

Office 365 vive en una red de Microsoft de gran capacidad y dedicada que está en un monitoreo único y no solo por la automatización, sino por personas reales. Una parte de la función de mantenimiento de la nube de Office 365 es el refuerzo y la optimización del rendimiento cuando es posible. Como los clientes de la nube de Office 365 tienen que conectarse a través de Internet, hay un esfuerzo continuo para ajustar el rendimiento entre los servicios de Office 365 también. Las mejoras de rendimiento nunca se detienen realmente en la nube y hay una gran experiencia acumulada para mantener la nube en buen estado y de forma rápida. Si experimenta un problema de rendimiento que se conecta desde su ubicación a Office 365, es mejor no empezar y esperar un caso de soporte técnico. En su lugar, debe empezar a investigar el problema de "The Inside Out". Es decir, comience dentro de la red y trabaje de la manera que espera para Office 365. Antes de abrir un caso con soporte técnico de Office 365, puede recopilar datos y emprender acciones que exploren y puede resolver el problema.
  
> [!IMPORTANT]
> Tenga en cuenta los límites y la planeación de la capacidad en Office 365. Esta información le llevará por delante de la curva cuando intente resolver un problema de rendimiento. Este es un vínculo a la [Descripción del servicio de la plataforma 365 de Office](https://technet.microsoft.com/en-us/library/office-365-service-descriptions.aspx). Se trata de un concentrador central y todos los servicios ofrecidos por Office 365 tienen un vínculo que va a sus propias descripciones de servicio desde aquí. Esto significa que, por ejemplo, si necesita ver los límites estándar de SharePoint Online, tendría que hacer clic en [Descripción del servicio de SharePoint Online](https://technet.microsoft.com/en-us/library/sharepoint-online-service-description.aspx) y buscar su [sección límites de SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkID=856113). 
  
Asegúrese de que va a solucionar problemas con la comprensión de que el rendimiento es una escala deslizante, no es conseguir un valor ideal y mantenerlo de forma permanente (si cree que esto es así), las tareas ocasionales de gran ancho de banda, como la incorporación de un un gran número de usuarios o la realización de grandes migraciones de datos serán muy estresantes, así que planee el impacto en el rendimiento. Puede, y debe, tener una idea aproximada de sus objetivos de rendimiento, pero una gran cantidad de variables se reproducen en el rendimiento, por lo que el rendimiento varía. Esa es la naturaleza del rendimiento. 
  
La solución de problemas de rendimiento no es sobre la satisfacción de objetivos específicos y el mantenimiento de dichos números indefinidamente, se trata de mejorar las actividades existentes, dadas todas las variables. 
  
## <a name="okay-what-does-a-performance-problem-look-like"></a>Bien, ¿qué aspecto tiene un problema de rendimiento?

En primer lugar, debe asegurarse de que lo que está experimentando es, en realidad, un problema de rendimiento y no un incidente de servicio. Un problema de rendimiento es diferente de un incidente de servicio en Office 365. Aquí te mostramos cómo distinguirlas.
  
Si el servicio de Office 365 tiene problemas, es un incidente del servicio. Verá los iconos rojos o amarillos bajo **mantenimiento actual** en el centro de administración de Microsoft 365, también puede observar un rendimiento lento en los equipos cliente que se conectan a Office 365. Por ejemplo, si el estado actual informa de un icono rojo y **** ve investigando junto a Exchange, puede que también reciba un grupo de llamadas de personas de su organización que se quejan de que los buzones de correo de cliente que usan Exchange Online se están realizando mal. En ese caso, es razonable asumir que el rendimiento de Exchange Online se ha convertido en una víctima de problemas en el servicio. 
  
![El panel de estado de Office 365 con todas las cargas de trabajo que muestran Green, excepto Exchange, que muestra el servicio restaurado.](media/ec7f0325-9e61-4e1a-bec0-64b87f4469be.PNG)
  
En este momento, el administrador de Office 365, debe comprobar el **estado actual** y **ver los detalles y el historial**, con frecuencia, para mantener la actualización del mantenimiento que realizamos en el sistema. El panel de **salud actual** se ha realizado para actualizarle sobre los cambios y problemas en el servicio. Las notas y explicaciones escritas en historial de salud, administrador a administrador, están ahí para ayudarle a evaluar su impacto y para mantener el registro de trabajo continuo. 
  
![Una imagen del panel de estado de Office 365 que explica que el servicio Exchange Online se ha restaurado y por qué.](media/66609554-426a-4448-8be6-ea09817f41ba.PNG)
  
Un problema de rendimiento no es un incidente del servicio, aunque los incidentes pueden provocar un rendimiento lento. Un problema de rendimiento tiene el siguiente aspecto:
  
- Un problema de rendimiento se produce independientemente del **estado actual** del centro de administración que informa al servicio. 
    
-  Un comportamiento que solía ser relativamente fluido tarda mucho tiempo en completarse o nunca en completarse. 
    
- Puede replicar el problema también o, al menos, saber que ocurrirá si realiza la serie adecuada de pasos.
    
-  Si el problema es intermitente, sigue habiendo un patrón, por ejemplo, sabrá que, a partir de 10:00 A.M., tendrá llamadas de usuarios que no pueden obtener acceso de manera confiable a Office 365 y que las llamadas se detendrán en torno a mediodía. 
    
Esto probablemente suena familiar; quizá le resulte muy familiar. Una vez que sabe que es un problema de rendimiento, la pregunta se convierte en "¿Qué debe hacer a continuación?". El resto de este artículo le ayudará a determinar exactamente eso.
  
## <a name="how-to-define-and-test-the-performance-problem"></a>Cómo definir y probar el problema de rendimiento

Los problemas de rendimiento suelen surgir a lo largo del tiempo, por lo que puede resultar difícil definir el problema real. Debe crear una buena declaración del problema y una buena idea del contexto del problema y, a continuación, necesita realizar pasos de prueba repetibles para ganar el día. De lo contrario, si no hay ningún error de su elección, es posible que se pierda. ¿Por qué? Bueno, a continuación se muestran algunos ejemplos de instrucciones de problemas que no proporcionan suficiente información:
  
- Cambiar de mi bandeja de entrada a mi calendario usado para ser algo que no he observado y ahora es un café. ¿Puede hacer que funcione como en su uso?
    
- Cargar mis archivos en SharePoint Online está tardando de forma permanente. ¿Por qué es lenta en la tarde, pero en cualquier otro momento, es rápido? ¿No es tan rápido?
    
Hay varios desafíos importantes que plantean las declaraciones anteriores del problema. En concreto, hay muchas ambigüedades con las que lidiar. Por ejemplo:
  
- No está claro cómo el cambio entre la bandeja de entrada y el calendario se usa para actuar en el portátil.
    
- Cuando el usuario dice "no es posible hacerlo rápido", ¿cuál es la "velocidad" rápida?
    
- ¿Cuánto tiempo es "Forever"? ¿Es que varios segundos, o minutos, el usuario puede ir a comer y terminar? 10 minutos después de que el usuario haya obtenido una copia?
    
Todo esto se debe a que no es necesario tener en cuenta que el administrador y el solucionador de problemas no pueden conocer muchos detalles de las instrucciones con problemas como estos. Por ejemplo, Cuándo comenzó a ocurrir el problema; Que el usuario trabaja desde casa y que solo ve nunca el cambio lento mientras está en una red doméstica; Que el usuario debe ejecutar otras aplicaciones que requieran mucha memoria RAM en el cliente local, o bien el usuario está ejecutando un sistema operativo anterior o no ejecutó actualizaciones recientes.
  
Cuando los usuarios notifican un problema de rendimiento, hay mucha información que recopilar. La recopilación de esta información forma parte de un proceso denominado el ámbito del problema o su investigación. A continuación se muestra una lista de ámbito básica que puede usar para recopilar información sobre el problema de rendimiento. Esta lista no es exhaustiva, pero es un lugar donde iniciar una de las suyas propias: 
  
- ¿En qué fecha tuvo lugar el problema y en qué hora del día o de la noche?
    
- ¿Qué tipo de equipo cliente estaba usando y cómo se conecta a la red empresarial (VPN, cableada, inalámbrica)?
    
- ¿Estaba trabajando de forma remota o estuvo en la oficina?
    
- ¿Ha intentado las mismas acciones en otro equipo y veo el mismo comportamiento?
    
- Recorra los pasos que le dan el problema para que pueda escribir las acciones que se van a realizar.
    
- ¿Cuál es el rendimiento en segundos o minutos?
    
- ¿En qué lugar del mundo se encuentra?
    
Algunas de estas preguntas son más obvias que otras. La mayoría de los usuarios sabrán que un solucionador de problemas necesita los pasos exactos para reproducir el problema. Después de todo, ¿de qué otra forma puede grabar qué es mal y cómo se puede probar si el problema se ha corregido? Menos obvios son cosas como "¿Cuál es la fecha y la hora en que apareció el problema?" y "¿Dónde se encuentra usted en el mundo?", información que se puede usar en tándem. Según el momento en que el usuario trabajaba, algunas horas de diferencia de tiempo pueden significar que el mantenimiento ya está en las partes de la red de la empresa. Si, por ejemplo, su compañía tiene una implementación híbrida, como una búsqueda híbrida de SharePoint, que puede consultar los índices de búsqueda en SharePoint Online y en una instancia local de SharePoint Server 2013, es posible que se estén realizando actualizaciones en la granja de servidores local. Si su compañía está en la nube, el mantenimiento del sistema puede incluir la adición o eliminación de hardware de red, la distribución de actualizaciones que se realicen en toda la empresa o la realización de cambios en el DNS o en otras infraestructuras principales.
  
Cuando está solucionando un problema de rendimiento, es un poco parecido a una escena de delitos, necesita ser preciso y observant para extraer cualquier conclusiones de la evidencia. Para ello, debe obtener una buena declaración del problema mediante la recopilación de pruebas. Debe incluir el contexto del equipo, el contexto del usuario, Cuándo comenzó el problema y los pasos exactos que exponían el problema de rendimiento. Esta declaración de problema debería ser, y permanecer, la página superior de las notas. Al recorrer la declaración del problema de nuevo después de trabajar con la resolución, está llevando a cabo los pasos para probar y demostrar si las acciones que se realizan han resuelto el problema. Esto es fundamental para saber cuándo se ha realizado su trabajo.
  
## <a name="do-you-know-how-performance-used-to-look-when-it-was-good"></a>¿Sabe cómo se usa el rendimiento para ver cuándo estaba bien?

Si no tiene suerte, nadie sabrá. Nadie tenía números. Esto significa que nadie puede responder a la pregunta sencilla "¿cuántos segundos se usó para hacer que aparezca una bandeja de entrada en Office 365?" o "¿cuánto tiempo tardó en realizarse cuando los ejecutivos tuvieron una reunión de Lync Online?", que es un escenario común para muchas empresas.
  
Lo que falta aquí es una línea de base de rendimiento.
  
Las líneas de base proporcionan un contexto para el rendimiento. Debe tomar una línea de base de vez en cuando, en función de las necesidades de su compañía. Si es una compañía más grande, su equipo de operaciones puede tomar líneas de base para su entorno local ya. Por ejemplo, si aplica la revisión a todos los servidores de Exchange en el primer lunes del mes y a todos los servidores de SharePoint el tercer lunes, es probable que el equipo de operaciones tenga una lista de tareas y escenarios en los que se ejecuta la revisión posterior para demostrar que las funciones críticas son práctica. Por ejemplo, abrir la bandeja de entrada, hacer clic en enviar y recibir y asegurarse de que las carpetas se actualizan o, en SharePoint, se examina la Página principal del sitio, pasa a la página de búsqueda Enterprise Search y se realiza una búsqueda que devuelve resultados.
  
Si sus aplicaciones están en Office 365, algunas de las líneas de base más fundamentales que puede tomar permiten medir el tiempo (en milisegundos) de un equipo cliente dentro de la red, en un punto de salida o en el punto en el que abandona la red y sale a Office 365. Estas son algunas de las líneas de base útiles que puede investigar y registrar:
  
- Identifique los dispositivos entre el equipo cliente y el punto de salida, por ejemplo, el servidor proxy.
    
  - Debe conocer los dispositivos para que tenga el contexto (direcciones IP, tipo de dispositivo, et cetera) para los problemas de rendimiento que se produzcan.
    
  - Los servidores proxy son puntos de salida comunes, por lo que puede consultar el explorador Web para ver qué servidor proxy está configurado para usar, si hay alguno.
    
  - Hay herramientas de terceros que pueden descubrir y asignar la red, pero la forma más segura de conocer los dispositivos es preguntar a un miembro del equipo de la red.
    
- Identifique su proveedor de servicios de Internet (ISP), anote su información de contacto y pregunte cuántos circuitos de ancho de banda tiene.
    
- Dentro de su empresa, identifique los recursos para los dispositivos entre su cliente y el punto de salida, o bien identifique un contacto de emergencia para hablar con los problemas de red.
    
Estas son algunas de las líneas base que pueden calcular las pruebas sencillas con herramientas:
  
- Tiempo desde el equipo cliente hasta el punto de salida en milisegundos
    
- Tiempo desde el punto de salida hasta Office 365 en milisegundos
    
- Ubicación en el mundo del servidor que resuelve las direcciones URL para Office 365 cuando explora
    
- La velocidad de la resolución DNS de su ISP en milisegundos, incoherencias en la llegada de paquetes (vibración de red), tiempos de carga y descarga en milisegundos
    
Si no está familiarizado con el modo de llevar a cabo estos pasos, profundizaremos en este artículo. 
  
## <a name="what-is-a-baseline"></a>¿Qué es una línea base?

Sabrá el impacto cuando se produzca un mal, pero si no conoce los datos de rendimiento históricos, no es posible tener un contexto de lo malo que podría haber pasado a ser y cuando. Por lo tanto, sin una línea de base, le falta la pista clave para resolver el rompecabezas: la imagen en el cuadro Puzzle. En la solución de problemas de rendimiento, necesita un punto de *comparación* . Las líneas de base de rendimiento simple no son difíciles de tomar. El equipo de operaciones puede encargarse de llevar a cabo esta tarea según una programación. Por ejemplo, supongamos que la conexión tiene un aspecto similar a este: 
  
![Un gráfico de red básica que muestra el cliente, el proxy y la nube de Office 365.](media/c6ca7140-09f9-4c2d-a775-dbf2820eaa0c.PNG)
  
Esto significa que se ha comprobado con el equipo de red y que se ha abandonado la empresa para Internet a través de un servidor proxy, y ese proxy controla todas las solicitudes que el equipo cliente envía a la nube. En este caso, debe dibujar una versión simplificada de la conexión que Enumere todos los dispositivos que intervienen. Ahora, inserte herramientas que puede usar para probar el rendimiento entre el cliente, el punto de salida (donde deja la red para Internet) y la nube de Office 365.
  
![Red básica con cliente, proxy y nube, y sugerencias de herramientas PSPing, TraceTCP y seguimientos de red.](media/627bfb77-abf7-4ef1-bbe8-7f8cbe48e1d2.png)
  
Las opciones se muestran de forma **sencilla** y **avanzada** debido a la cantidad de experiencia que necesita para encontrar los datos de rendimiento. Un seguimiento de red tardará mucho tiempo, en comparación con la ejecución de herramientas de línea de comandos, como PsPing y TraceTCP. Estas dos herramientas de línea de comandos se eligieron porque no usan paquetes ICMP, que se bloquearán en Office 365 y porque dan el tiempo en milisegundos que se tarda en dejar el equipo cliente, o en el servidor proxy (si tiene acceso) y en Office 365. Cada salto individual de un equipo a otro terminará con un valor de tiempo y es estupendo para las líneas de base. Como es importante, estas herramientas de línea de comandos le permiten agregar un número de puerto en el comando, esto es útil porque Office 365 se comunica a través del puerto 443, que es el puerto que usan la capa de sockets seguros y la seguridad de la capa de transporte (SSL y TLS). Sin embargo, otras herramientas de terceros pueden ser mejores soluciones para su situación. Microsoft no es compatible con todas estas herramientas, por lo que si, por algún motivo, no consigue usar PsPing y TraceTCP, pase a un seguimiento de red con una herramienta como Netmon. 
  
Puede tomar una línea de base antes del horario comercial, de nuevo durante el uso intenso y después de nuevo fuera del horario laboral. Esto significa que puede tener una estructura de carpetas que tenga un aspecto similar a este al final:
  
![Gráfico que propone una manera de organizar los datos de rendimiento en carpetas.](media/13e01ffa-f0f2-4d10-b89d-d5980ec89fae.png)
  
También debe elegir una Convención de nomenclatura para los archivos. Aquí le mostramos otros ejemplos:
  
- Feb_09_2015_9amPST_PerfBaseline_Netmon_ClientToEgress_Normal
    
- Jan_10_2015_3pmCST_PerfBaseline_PsPing_ClientToO365_bypassProxy_SLOW
    
- Feb_08_2015_2pmEST_PerfBaseline_BADPerf
    
- Feb_08_2015_8-30amEST_PerfBaseline_GoodPerf
    
Hay muchas maneras diferentes de hacerlo, pero usar ** \<DateTime\>\<Format lo que sucede\> en la prueba** es un buen punto de partida. Ser diligente con respecto a esto le ayudará mucho cuando intente solucionar problemas más adelante. Más adelante, podrá decir "he tomado dos seguimientos el 8 de febrero, uno demostró un buen rendimiento y uno mostró que es malo, para que podamos compararlos". Esto es muy útil para solucionar problemas. 
  
Debe disponer de un método organizado para mantener las líneas de base del historial. En este ejemplo, los métodos simples generaban tres salidas de línea de comandos y los resultados se recopilaban como capturas de pantalla, pero en su lugar puede tener archivos de captura de red. Use el método que funcione mejor para usted. Almacene las líneas de base del historial y haga referencia a ellas en los puntos donde advierta los cambios en el comportamiento de los servicios en línea. 
  
## <a name="why-collect-performance-data-during-a-pilot"></a>¿Por qué recopilar datos de rendimiento durante una prueba piloto?

No hay mejor tiempo para empezar a tomar líneas de base que durante la prueba piloto del servicio de Office 365. Su oficina puede tener miles de usuarios, cientos de miles o cinco, pero incluso con un pequeño número de usuarios, puede realizar pruebas para medir las fluctuaciones en el rendimiento. En el caso de una compañía de gran tamaño, una muestra representativa de varios cientos de usuarios piloto de Office 365 puede proyectarse hacia afuera a varios miles para que sepa dónde pueden surgir los problemas antes de que ocurran.
  
En el caso de una empresa pequeña, donde la incorporación de embarques significa que todos los usuarios se conectan al servicio al mismo tiempo y que no hay pruebas piloto, tenga en cuenta las medidas de rendimiento para que tenga los datos que se mostrarán a cualquier persona que pueda tener problemas para solucionar una operación que no funciona correctamente. Por ejemplo, si observa que todo un repentino puede recorrer el edificio en el tiempo que se tarda en cargar un gráfico de tamaño mediano en el que se usaba con mucha rapidez.
  
## <a name="how-to-collect-baselines"></a>Cómo recopilar líneas de base

Para todos los planes de solución de problemas necesita identificar estas cosas como mínimo:
  
- El equipo cliente que está usando (el tipo de equipo o dispositivo, una dirección IP y las acciones que produjeron el problema)
    
- Donde el equipo cliente está ubicado en el mundo (por ejemplo, si este usuario se encuentra en una VPN a la red, trabaja de forma remota o en la intranet de la compañía)
    
- El punto de salida que el equipo cliente usa desde la red (el punto en el que el tráfico abandona su empresa para un ISP o Internet)
    
 Puede averiguar el diseño de su red desde el administrador de la red. Si está en una red pequeña, eche un vistazo a los dispositivos que se conectan a Internet y llame a su ISP si tiene preguntas sobre el diseño. Cree un gráfico del diseño final de la referencia. 
  
Esta sección está dividida en sencillos métodos y herramientas de línea de comandos y opciones de herramientas más avanzadas. Primero trataremos los métodos sencillos. Pero si tiene un problema de rendimiento en este momento, debe ir a métodos avanzados y probar el plan de acción de solución de problemas de rendimiento de ejemplo.
  
### <a name="simple-methods"></a>Métodos sencillos

El objetivo de estos métodos sencillos es aprender a tomar, comprender y almacenar adecuadamente las líneas de base de rendimiento simple con el tiempo para que se le informe sobre el rendimiento de Office 365. Este es el sencillo diagrama sencillo, tal y como ha visto antes:
  
![Red básica con cliente, proxy y nube, y sugerencias de herramientas PSPing, TraceTCP y seguimientos de red.](media/627bfb77-abf7-4ef1-bbe8-7f8cbe48e1d2.png)
  
> [!NOTE]
> TraceTCP se incluye en esta captura de pantalla porque es una herramienta útil para mostrar, en milisegundos, el tiempo que tarda en procesarse una solicitud y Cuántos saltos de red o conexiones de un equipo a la siguiente, que la solicitud tarda en llegar a un destino. TraceTCP también puede dar los nombres de los servidores usados durante los saltos, lo que puede resultar útil para un solucionador de problemas de Microsoft Office 365 en soporte técnico. Los comandos de > TraceTCP pueden ser muy sencillos, como `tracetcp.exe outlook.office365.com:443` : >> Recuerde incluir el número de puerto en el comando! > [TraceTCP](http://simulatedsimian.github.io/tracetcp_download.html) es una descarga gratuita, pero depende de wincap. Wincap es una herramienta que Netmon también usa e instala. También usamos Netmon en la sección métodos avanzados. 
  
 Si tiene varias oficinas, tendrá que mantener un conjunto de datos de un cliente en cada una de esas ubicaciones también. Esta prueba mide la latencia, que, en este caso, es un valor numérico que describe la cantidad de tiempo entre un cliente que envía una solicitud a Office 365 y Office 365 a responder a la solicitud. Las pruebas se originan dentro de su dominio en un equipo cliente y buscan medir un recorrido de ida y vuelta desde dentro de la red, pasando por un punto de salida, a través de Internet a Office 365 y atrás. 
  
Hay varias formas de tratar el punto de salida, en este caso, el servidor proxy. Puede realizar un seguimiento de 1 a 2 y, después, de 2 a 3 y, a continuación, agregar los números en milisegundos para obtener un total final hasta el perímetro de la red. O bien, puede configurar la conexión para omitir el proxy para las direcciones de Office 365. En una red más grande con un firewall, un proxy inverso o alguna combinación de ambos, es posible que deba realizar excepciones en el servidor proxy que permitan que el tráfico pase una gran cantidad de direcciones URL. Para obtener una lista de los extremos usados por Office 365, consulte [office 365 URL e intervalos de direcciones IP](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2). Si tiene un proxy de autenticación, comience por probar las excepciones para lo siguiente:
  
- Puertos 80 y 443
    
- TCP y HTTPs
    
- Conexiones salientes a cualquiera de estas direcciones URL:
    
- \*. microsoftonline.com
    
- \*. microsoftonline-p.com
    
- \*. sharepoint.com
    
- \*. outlook.com
    
- \*. lync.com
    
- osub.microsoft.com
    
Todos los usuarios deben tener permiso para acceder a estas direcciones sin ninguna interferencia de proxy o autenticación. En una red más pequeña, debe agregarlas a la lista de omisión de proxy en el explorador Web. 
  
Para agregarlos a la lista de omisión de proxy en Internet Explorer, vaya a **herramientas** \> **Opciones** \> de Internet **conexiones** \> **configuración** \> **avanzada**de LAN. La ficha avanzadas también es donde encontrará el servidor proxy y el puerto del servidor proxy. Es posible que deba hacer clic en la casilla **usar un servidor proxy para la LAN**para obtener acceso al botón **avanzadas** . Querrá asegurarse de que la casilla **omitir servidor proxy para direcciones locales** esté activada. Una vez que haga clic en **avanzada**, verá un cuadro de texto en el que puede escribir excepciones. Separe las direcciones URL con caracteres comodín enumerados anteriormente con puntos y coma, por ejemplo:
  
\*. microsoftonline.com; \*. SharePoint.com
  
Una vez que haya omitido el proxy, debe poder usar ping o PsPing directamente en una dirección URL de Office 365. El paso siguiente será probar el ping **Outlook.Office365.com**. O bien, si está usando PsPing u otra herramienta que le permitirá proporcionar un número de puerto al comando, PsPing contra **portal.microsoftonline.com:443** para ver el tiempo promedio de ida y vuelta en milisegundos. 
  
El tiempo de ida y vuelta, o RTT, es un valor numérico que mide el tiempo que se tarda en enviar una solicitud HTTP a un servidor como outlook.office365.com y obtener una respuesta que confirme que el servidor sabe que lo hizo. A veces verá esto abreviado como RTT. Este debe ser un período de tiempo relativamente corto.
  
Debe usar [PSPing](https://technet.microsoft.com/en-us/sysinternals/jj729731.aspx) u otra herramienta que no use paquetes ICMP que estén bloqueados por Office 365 para realizar esta prueba. 
  
 **Cómo usar PsPing para obtener un tiempo global de ida y vuelta en milisegundos directamente desde una dirección URL de Office 365**
  
1. Para ejecutar un símbolo del sistema con privilegios elevados, siga estos pasos:
    
1. Haga clic en  **Iniciar **.
    
2. En el cuadro **Iniciar búsqueda** , escriba cmd y, a continuación, presione Ctrl + Mayús + entrar.
    
3. Si aparece el cuadro de diálogo **Control de cuentas de usuario**, confirme que la acción que muestra es la que desea y, a continuación, haga clic en **Continuar**.
    
2. Desplácese hasta la carpeta en la que está instalada la herramienta (en este caso, PsPing) y Pruebe estas direcciones URL de Office 365:
    
  - psping portal.office.com:443
    
  - psping microsoft-my.sharepoint.com:443
    
  - psping outlook.office365.com:443
    
  - psping www.yammer.com:443
    
    ![El comando PSPing que va a microsoft-my.sharepoint.com puerto 443.](media/3258f620-4513-4e82-95c9-06b387fc3a82.PNG)
  
Asegúrese de incluir el número de puerto de 443. Recuerde que Office 365 funciona en un canal cifrado. Si es PsPing sin el número de puerto, se producirá un error en la solicitud. Una vez que haya hecho ping en su lista corta, busque el tiempo promedio en milisegundos (MS). Eso es lo que desea grabar.
  
![Gráfico que muestra una ilustración de PSPing de cliente a proxy con un tiempo de ida y vuelta de 2,8 milisegundos.](media/96901aea-1093-4f1b-b5a3-6078e9035e6c.png)
  
Si no está familiarizado con la omisión de proxy y prefiere realizar todas las tareas paso a paso, debe averiguar primero el nombre del servidor proxy. En Internet Explorer, vaya a **herramientas** \> **Opciones** \> de Internet **conexiones** \> **configuración** \> **avanzada**de LAN. La ficha **Opciones avanzadas** es la que verá el servidor proxy en la lista. Haga ping a ese Proxy Server en un símbolo del sistema realizando esta tarea: 
  
 **Para hacer ping al servidor proxy y obtener un valor de recorrido de ida y vuelta en milisegundos para la fase 1 a 2**
  
1. Para ejecutar un símbolo del sistema con privilegios elevados, siga estos pasos:
    
1. Haga clic en  **Iniciar **.
    
2. En el cuadro **Iniciar búsqueda** , escriba cmd y, a continuación, presione Ctrl + Mayús + entrar.
    
3. Si aparece el cuadro de diálogo **Control de cuentas de usuario**, confirme que la acción que muestra es la que desea y, a continuación, haga clic en **Continuar**.
    
2. Escriba ping \<el nombre del servidor proxy que usa su explorador, o la dirección IP del servidor\> proxy y, a continuación, presione Entrar. Si tiene una PsPing o alguna otra herramienta instalada, puede elegir usar esa herramienta en su lugar. 
    
    El comando puede tener un aspecto similar a cualquiera de estos ejemplos: 
    
  - ping ourproxy.ourdomain.industry.business.com
    
  - ping 155.55.121.55
    
  - ping ourproxy
    
  - psping ourproxy.ourdomain.industry.business.com:80
    
  - psping 155.55.121.55:80
    
  - psping ourproxy: 80
    
3. Cuando la traza deje de enviar paquetes de prueba, obtendrá un pequeño resumen que indica un promedio, en milisegundos, que es el valor que tiene después. Realice una captura de pantalla del mensaje y guárdelo con la Convención de nomenclatura. En este punto, también puede ayudar a rellenar el diagrama con el valor.
    
Es posible que haya realizado un seguimiento a principios de la mañana y su cliente puede obtener acceso al proxy (o al servidor de salida que sale a Internet) rápidamente. En este caso, los números pueden tener el siguiente aspecto:
  
![Gráfico que muestra el tiempo de ida y vuelta desde un cliente a un proxy de 2,8 milisegundos.](media/1bd03544-23fc-47d4-bbae-c1feb466a5d8.PNG)
  
Si el equipo cliente es uno de los pocos selecciones con acceso al servidor proxy (o salida), puede ejecutar el siguiente segmento de la prueba conectando remotamente con ese equipo, ejecutando el símbolo del sistema para PsPing a una dirección URL de Office 365 desde allí. Si no tiene acceso a ese equipo, puede ponerse en contacto con sus recursos de red para obtener ayuda con el próximo segmento y obtener números exactos. Si esto no es posible, debe realizar un PsPing contra la dirección URL de Office 365 en cuestión y compararlo con el tiempo de ping o la hora de ping con el servidor proxy. 
  
Por ejemplo, si tiene 51,84 milisegundos del cliente en la dirección URL de Office 365 y tiene 2,8 milisegundos del cliente en el proxy (o punto de salida), entonces tiene 49,04 milisegundos de salida a Office 365. Del mismo modo, si tiene un PsPing de 12,25 milisegundos desde el cliente al proxy durante la altura del día y 62,01 milisegundos desde el cliente hasta la dirección URL de Office 365, el valor promedio del proxy se mantiene en la dirección URL de Office 365 es de 49,76 milisegundos.
  
![Gráfico adicional que muestra el ping en milisegundos del cliente al proxy al lado del cliente a Office 365 para que se puedan restar los valores.](media/cd764e77-5154-44ba-a5cd-443a628eb2d9.PNG)
  
En cuanto a la solución de problemas, es posible que le resulte interesante mantener estas líneas de base. Por ejemplo, si ve que por lo general tiene aproximadamente de 40 a 59 milisegundos de latencia desde el proxy o el punto de salida a la dirección URL de Office 365, y tiene un cliente para el proxy o la latencia de punto de salida de aproximadamente 3 a 7 milisegundos (según la cantidad de tráfico de red que esté Seein g durante esa hora del día) seguramente sabrá que algo es problemático si los tres últimos tres clientes a proxy o de salida de referencia muestran una latencia de 45 milisegundos.
  
### <a name="advanced-methods"></a>Métodos avanzados

Si realmente quiere saber lo que ocurre con sus solicitudes de Internet a Office 365, debe familiarizarse con los seguimientos de red. No importa qué herramientas se prefieren para estos seguimientos, HTTPWatch, Netmon, Message Analyzer, Wireshark, Fiddler, la herramienta del panel del programador o cualquier otro, lo hará siempre que esa herramienta pueda capturar y filtrar el tráfico de red. En esta sección, verá que es ventajoso ejecutar más de una de estas herramientas para obtener una imagen más completa del problema. Al realizar las pruebas, algunas de estas herramientas también actúan como servidores proxy en su propio derecho. Herramientas que se usan en el artículo adjunto [plan de solución de problemas de rendimiento para Office 365](performance-troubleshooting-plan.md), incluidos [Netmon 3,4](https://www.microsoft.com/en-us/download/details.aspx?id=4865), [HTTPWatch](https://www.httpwatch.com/download/)o [Wireshark](https://www.wireshark.org/).
  
Tomar una línea de base de rendimiento es la parte sencilla de este método y muchos de los pasos son los mismos que cuando se soluciona un problema de rendimiento. Los métodos más avanzados para crear líneas base para el rendimiento requieren que se tomen y almacenen los seguimientos de red. La mayoría de los ejemplos de este artículo usan SharePoint Online, pero debe desarrollar una lista de acciones comunes en los servicios de Office 365 a los que se suscribe para probar y grabar. Este es un ejemplo de línea de base:
  
- Lista de líneas base para SPO-* * paso 1: * * Explore la Página principal del sitio web de SPO y realice un seguimiento de la red. Guarde la traza. 
    
- Lista de línea base para SPO- **Step 2:** buscar un término (como el nombre de la compañía) mediante el servicio de búsqueda Enterprise Search y realizar un seguimiento de la red. Guarde la traza. 
    
- Lista de línea base para SPO- **Step 3:** cargar un archivo de gran tamaño en una biblioteca de documentos de SharePoint Online y realizar un seguimiento de la red. Guarde la traza. 
    
- Lista de línea base para SPO- **paso 4:** examinar la Página principal del sitio web de OneDrive y realizar un seguimiento de la red. Guarde la traza. 
    
Esta lista debe incluir las acciones comunes más importantes que los usuarios toman en SharePoint Online. Observe que el último paso, para realizar un seguimiento hacia OneDrive para la empresa, crea una comparación entre la carga de la Página principal de SharePoint Online (que a menudo es personalizada por las empresas) y la Página principal de OneDrive para la empresa, que rara vez está personalizada. Se trata de una prueba muy básica en lo que se refiere a un sitio de SharePoint Online de carga lenta. Puede crear un registro de esta diferencia en las pruebas.
  
Si está en medio de un problema de rendimiento, muchos de los pasos son los mismos que para tomar una línea de base. Los seguimientos de red se convierten en críticos, por lo que vamos a controlar *Cómo* realizar los seguimientos importantes a continuación. 
  
Para solucionar un problema de rendimiento, *ahora* tiene que realizar un seguimiento en el momento en que experimenta el problema de rendimiento. Debe disponer de las herramientas adecuadas para recopilar los registros y necesitará un plan de acción, es decir, una lista de acciones de solución de problemas para recopilar la mejor información que puede. Lo primero que debe hacer es registrar la fecha y la hora de la prueba para que los archivos se puedan guardar en una carpeta que refleje el intervalo. A continuación, Refine los pasos del problema. Estos son los pasos exactos que usará para las pruebas. No olvide los conceptos básicos: Si el problema solo está relacionado con Outlook, asegúrese de grabar que el comportamiento del problema ocurre en un solo servicio de Office 365. Restringir el alcance de este problema le ayudará a centrarse en algo que pueda resolver. 
  
## <a name="see-also"></a>Vea también

[Administrar puntos de conexión de Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)

