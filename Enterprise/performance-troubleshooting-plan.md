---
title: Plan de solución de problemas de rendimiento para Office 365
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 4/26/2017
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
ms.assetid: e241e5d9-b1d8-4f1d-a5c8-4106b7325f8c
description: ¿Necesita conocer los pasos a seguir para la identificación y corrección de rendimiento lento entre SharePoint Online, OneDrive para el negocio, Exchange Online o Skype para profesionales en línea y el equipo cliente, se bloquea e intervalos? Antes de llamar a soporte técnico, este artículo puede ayudarle a solucionar problemas de rendimiento de Office 365 e incluso solucionar algunos de los problemas más comunes.
ms.openlocfilehash: c7eed9498920c601b3b345e8d1879ddbb16c56c3
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542863"
---
# <a name="performance-troubleshooting-plan-for-office-365"></a>Plan de solución de problemas de rendimiento para Office 365

¿Necesita conocer los pasos a seguir para la identificación y corrección de rendimiento lento entre SharePoint Online, OneDrive para el negocio, Exchange Online o Skype para profesionales en línea y el equipo cliente, se bloquea e intervalos? Antes de llamar a soporte técnico, este artículo puede ayudarle a solucionar problemas de rendimiento de Office 365 e incluso solucionar algunos de los problemas más comunes.
  
En este artículo es realmente un plan de acción de ejemplo que puede utilizar para capturar datos valiosos sobre el problema de rendimiento como está ocurriendo. Algunos problemas principales también se incluyen en este artículo.
    
Si es nuevo en el rendimiento de la red y desea crear un plan a largo plazo para supervisar el rendimiento entre los equipos cliente y Office 365, eche un vistazo en el [rendimiento de Office 365 ajuste y solución de problemas - Admin y para profesionales de TI](performance-tuning-using-baselines-and-history.md).
  
## <a name="sample-performance-troubleshooting-action-plan"></a>Plan de acción de para solucionar problemas de rendimiento de ejemplo

Este plan de acción consta de dos partes; una fase de preparación y una fase de registro. Si tiene un problema de rendimiento ahora mismo, y necesita para realizar la recolección de datos, puede empezar a usar inmediatamente este plan.
  
 **Preparar el equipo cliente**
  
- Busque un equipo cliente que puede reproducir el problema de rendimiento. Este equipo se usará durante el transcurso de la solución de problemas.
    
- Anote los pasos que producen el problema de rendimiento a que se produzca de modo que está listo cuando llegue el momento para probar.
    
- Instalar las herramientas para recopilar y registrar la información:
    
  - Instale [Netmon 3.4](https://www.microsoft.com/en-us/download/details.aspx?id=4865) (o usar una herramienta de seguimiento de red equivalente). 
    
  - Instalar la edición básica gratuita de [HTTPWatch](https://www.httpwatch.com/download/) (o usar una herramienta de seguimiento de red equivalente). 
    
  - Usar una grabadora de pantalla o ejecute la grabadora de pasos (PSR.exe) que se incluye con Windows Vista y versiones posteriores, con el fin de mantener un registro de los pasos que necesarios durante las pruebas.
    
 **El problema de rendimiento de registro**
  
- Cierre todos los exploradores de Internet extraños.
    
- Iniciar la grabadora de pasos u otra grabadora de pantalla.
    
- Iniciar la captura de Netmon (o la herramienta de seguimiento de red).
    
- Vaciar la caché DNS en el equipo cliente desde la línea de comandos escribiendo ipconfig /flushdns.
    
- Iniciar una nueva sesión de explorador y activar HTTPWatch.
    
- Opcional: Si está probando Exchange Online, ejecute la herramienta Analizador de rendimiento del cliente de Exchange desde la consola de administración de Office 365.
    
- Reproducir los pasos exactos que provocar el problema de rendimiento.
    
- Detener la Netmon o seguimiento de otra herramienta.
    
- En la línea de comandos, ejecute una ruta de seguimiento a su suscripción de Office 365 por escribiendo el siguiente comando y, a continuación, presione ENTRAR:
    
    `tracert \< *subscriptionname*  \>.onmicrosoft.com` 
    
- Detenga la grabadora de pasos y guardar el vídeo. Asegúrese de incluir la fecha y hora de la captura y si muestra el rendimiento buena o es incorrecto.
    
- Guarde los archivos de seguimiento. Una vez más, no olvide incluir la fecha y hora de la captura y si muestra el rendimiento buena o es incorrecto.
    
Si no está familiarizado con la ejecución de las herramientas que se mencionan en este artículo, no se preocupe porque describimos los pasos a continuación. Si está acostumbrados a realizar este tipo de red capturar, puede omitir [cómo recopilar las líneas de base](performance-tuning-using-baselines-and-history.md#how-to-collect-baselines), que describe el filtrado y la lectura de los registros. 
  
## <a name="flush-the-dns-cache-first"></a>Vaciar la memoria caché de DNS en primer lugar

¿Por qué? Por vaciado de la memoria caché de DNS para empezar las pruebas con un espacio vacío. Desactivando la memoria caché, que desea restablecer el contenido de la resolución DNS a las entradas más actualizadas. Recuerde que un vaciado no quita las entradas del archivo HOSTs. Si utiliza las entradas del archivo HOST ampliamente, debe copie las entradas de la a un archivo en otro directorio y, a continuación, vaciar el archivo HOST.
  
 **Vaciar la caché de resolución DNS**
  
1. Abra el símbolo del sistema, (puede ser **Iniciar** \> **Ejecutar** \> **clave de Windows** o **cmd** \> **cmd**).
    
2. Escriba el siguiente comando y presione ENTRAR:`ipconfig /flushdns`
    
## <a name="netmon"></a>Netmon

Herramienta de supervisión de red de Microsoft ([Netmon](https://www.microsoft.com/download/details.aspx?id=4865)) analiza los paquetes, que es el tráfico, lo que pasa entre los equipos de redes. Mediante el uso de Netmon para el tráfico con Office 365 puede capturar, vista, de seguimiento y leer los encabezados de paquetes, identificar los dispositivos intermedios, comprobar la configuración importante en hardware de red, busque los paquetes descartados y siga el flujo de tráfico entre los equipos de su empresa red y Office 365. Debido a que se cifra el cuerpo del tráfico real, es decir, lo (viajes en el puerto 443 a través de SSL/TLS, no puede leer los archivos que se está enviados. En su lugar, obtenga un seguimiento de la ruta de acceso que la toma de paquetes que le ayudarán a realizar un seguimiento hacia abajo el comportamiento de problema sin filtrar.
  
Asegúrese de que no aplicar un filtro en este momento. En su lugar, ejecute los pasos y demostrar el problema antes de detener el seguimiento y guardar.
  
Después de instalar Netmon 3.4, abra la herramienta y lleve a cabo estos pasos:
  
 **Realizar un seguimiento de Netmon y reproduzca el problema**
  
1. Inicie Netmon 3.4.
    
    Hay tres paneles en la página de **Inicio** : **Captura recientes**, **Seleccione redes**y la **Introducción con Monitor de red 3.4 de Microsoft. Aviso de**. El panel seleccionar redes también le ofrecerá una lista de las redes de forma predeterminada desde la que puede capturar. Asegúrese de que las tarjetas de red se seleccionan aquí.
    
2. Haga clic en **Nueva captura** en la parte superior de la página de **Inicio** . Esto agrega una nueva ficha situado junto a la ficha de página de **Inicio** denominada **capturar 1**.
    
    ![Usuario del Nemon una interfaz con la nueva captura, inicio, botones y detener resaltados.](media/d4527d84-62ec-4301-82d5-e0166ff71f20.PNG)
  
3. Para realizar una captura de simple, haga clic en **Inicio** , en la barra de herramientas. 
    
4. Reproduzca los pasos que presentan un problema de rendimiento.
    
5. Haga clic en **Detener** \> **archivo** \> **Guardar como**. Recuerde que para dar a la fecha y hora con la zona horaria y mencionar si muestra incorrecto o buen rendimiento.
    
## <a name="httpwatch"></a>HTTPWatch

[HTTPWatch](https://www.httpwatch.com/download/) viene cargada y una edición gratuita. La edición básica gratuita cubre todo lo que necesita para esta prueba. HTTPWatch monitores tiempo de carga de página y el tráfico de red a la derecha de la ventana del explorador. HTTPWatch es un complemento para Internet Explorer que describe gráficamente el rendimiento. El análisis se pueden guardar y verse en HTTPWatch Studio. 
  
> [!NOTE]
> Si usa otro explorador, como Firefox, Google Chrome, o si no se puede instalar HTTPWatch en Internet Explorer, abra una nueva ventana del explorador y presione la tecla F12. Debería ver la herramienta para desarrolladores emergente en la parte inferior del explorador. Si usa Opera, presione CTRL + MAYÚS + I para Web Inspector, a continuación, haga clic en la ficha **red** y realizar las pruebas se describen a continuación. La información puede variar ligeramente, pero aún se mostrará tiempos de carga en milisegundos. > HTTPWatch también es muy útil para problemas con SharePoint Online tiempos de carga de página. 
  
 **Ejecute HTTPWatch y reproduzca el problema**
  
1. HTTPWatch es un explorador Plug-in, por lo que la exposición de la herramienta en el explorador es ligeramente diferente para cada versión de Internet Explorer. Normalmente, puede encontrar HTTPWatch en la barra de comandos en el Explorador de Internet Explorer.</br></br>Si no ve el complemento HTTPWatch en la ventana del explorador, compruebe la versión del explorador por haga clic en Ayuda \> acerca de, o en versiones posteriores de Internet Explorer, haga clic en el símbolo de engranaje y acerca de Internet Explorer. Para iniciar la barra de **comandos** , haga clic en la barra de menús en el Explorador de Internet y haga clic en la **barra de comandos**. En el pasado, HTTPWatch se ha asociado con los comandos y las barras del explorador, por lo que una vez instale, si no ve inmediatamente el icono (incluso después de reiniciar) compruebe **las herramientas**y las barras de herramientas para el icono. Recuerde que se pueden personalizar las barras de herramientas y opciones que pueden agregarse a ellos.</br>
    ![Barra de herramientas de comando de Internet Explorer con el icono de HTTPWatch que se muestra.](media/198590b0-d7b1-4bff-a6ad-e4ec3a1e83df.png)
  
2. Inicie HTTPWatch en una ventana del explorador Internet Explorer. Aparecerá acoplada en el explorador en la parte inferior de esa ventana. Haga clic en **registro**.
    
3. Reproducir los pasos exactos implicados en el problema de rendimiento. Haga clic en el botón **Detener** en HTTPWatch. 
    
4. **Guardar** el HTTPWatch o **Enviar por correo electrónico**. Recuerde que un nombre al archivo para que incluya información de fecha y hora y una indicación de si la inspección contiene una demostración de rendimiento correcto o incorrecto.</br></br>![HTTPWatch que muestra la ficha de red para una carga de página de la página de inicio de Office 365.](media/021a2c64-d581-49fd-adf4-4c364f589d75.PNG)</br></br>
    Esta captura de pantalla es desde la versión de HTTPWatch Professional. Puede abrir seguimientos realizados en la versión básica en un equipo con una versión Professional y leerlo allí. Información adicional puede estar disponible desde el seguimiento a través de este método.
    
## <a name="problem-steps-recorder"></a>Grabación de acciones

Grabadora de pasos o PSR.exe, permite registrar problemas a medida que se producen. Se trata de una herramienta muy útil y muy simple ejecutar.
  
 **Ejecute la grabación de acciones (PSR.exe) para registrar su trabajo**
  
1. Utilice **Iniciar** \> **Ejecutar** \> escriba **PSR.exe** \> **Aceptar**, o bien, haga clic en la **Tecla de Windows** \> escriba **PSR.exe** \> y, a continuación, presione ENTRAR. 
    
2. Cuando aparezca la ventana de PSR.exe pequeña, haga clic en **Iniciar registro** y reproduzca los pasos que se reproduzca el problema de rendimiento. Puede agregar comentarios según sea necesario, al hacer clic en **Agregar comentarios**.
    
3. Cuando haya completado los pasos, haga clic en **Detener registro** . Si el problema de rendimiento es una representación de la página, espere a que la página representar antes de detener la grabación. 
    
4. Haga clic en **Guardar**.
    
![Una captura de pantalla de la grabadora de pasos o PSR.exe.](media/8542b0aa-a3ff-4718-8dc4-43f5521c6c34.PNG)
  
La fecha y la hora se registra para usted. Esto vincula la región Determinada a su seguimiento de Netmon y HTTPWatch en tiempo y ayuda con la solución de problemas de precisión. Pueden mostrar la fecha y hora en el registro de la región Determinada que pasa un minuto entre el inicio de sesión y la exploración de la dirección URL y la representación parcial del sitio de administración, por ejemplo.
  
## <a name="read-your-traces"></a>Los seguimientos de lectura

No es posible enseñar todo acerca de la red y solución de problemas de rendimiento que alguien tendría que saber a través de un artículo. Introducción buena en rendimiento tiene experiencia y conocimientos del funcionamiento de la red y normalmente se realiza. Pero es posible que se desea redondear hacia arriba en una lista de los principales problemas y se muestre cómo herramientas pueden facilitar a eliminar los problemas más comunes.
  
Si desea seleccionar conocimientos de lectura de trazas de red para los sitios de Office 365, no hay ningún profesor mejor que crear los seguimientos de carga de las páginas con regularidad y adquiere experiencia leerlos. Por ejemplo, cuando tiene una oportunidad, cargue un servicio de Office 365 y el proceso de seguimiento. Filtrar el seguimiento para el tráfico DNS o buscar la FrameData para el nombre del servicio que consultadas. Examinar el seguimiento para hacerse una idea de los pasos que se producen cuando se carga el servicio. Esto le ayudarán a aprender qué normal carga de la página debe tener un aspecto como y, en el caso de solución de problemas, especialmente alrededor de rendimiento, comparación de seguimientos de buenos a incorrecta puede mostrarle un lote.
  
Netmon usa Microsoft Intellisense en el campo de filtro para mostrar. IntelliSense o finalización de código inteligente, es que trucos donde se escribe en un período y se muestran todas las opciones disponibles en un cuadro de selección de la lista desplegable. Si, por ejemplo, le preocupa el escalado de ventanas TCP, puede encontrar la forma de un filtro (como `.protocol.tcp.window < 100`) por este medio.
  
![Captura de pantalla de Netmon que muestra que el campo de filtro de presentación utiliza intellisense.](media/75a56c11-9a60-47ee-a100-aabdfb1ba10f.PNG)
  
Los seguimientos de Netmon pueden tener una gran cantidad de tráfico en ellos. Si no experimentados con leerlos, es probable que va a estar abrumado abrir el seguimiento de la primera vez. Lo primero que debe hacer es separar la señal de ruido de fondo en el seguimiento. Probado con Office 365, y que son el tráfico que desee ver. Si se utilizan para navegar por los seguimientos, puede que no tenga esta lista.
  
El tráfico entre el cliente y Office 365 se transmite a través de TLS, lo que significa que el cuerpo del tráfico estará cifrado y no se puede leer en un seguimiento de Netmon genérico. El análisis de rendimiento no es necesario conocer los detalles de la información en el paquete. Sin embargo, es muy interesado en encabezados de paquetes y la información que contienen.
  
 **Sugerencias para obtener un buen seguimiento**
  
- Conocer el valor de la dirección IPv4 o IPv6 del equipo cliente. Puede obtener desde el símbolo del sistema, escriba **IPConfig** y, a continuación, presione ENTRAR. Conocer esta dirección le permiten ver rápidamente si el tráfico en el seguimiento implica directamente el equipo cliente. Si no hay un proxy conocido, aplicar el comando ping y obtener así como su dirección IP. 
    
- Vaciar la caché de resolución DNS y, si es posible, cierre todos los exploradores excepto el uno en el que está ejecutando las pruebas. Si no puede hacerlo, por ejemplo, si soporte técnico usa alguna herramienta basada en explorador para ver el escritorio del equipo cliente, esté preparado para filtrar su seguimiento.
    
- En un seguimiento ocupado, busque el servicio Office 365 que esté usando. Si ya ha visto el tráfico antes de nunca o poco, este es un paso útil en separar el problema de rendimiento de otros ruidos de red. Hay varias formas de hacer esto. Directamente antes de la prueba, puede usar ping o PsPing, a la dirección URL del servicio específico ( `ping outlook.office365.com` o `psping -4 microsoft-my.sharepoint.com:443`, para ver ejemplos). Puede encontrar fácilmente esa PsPing en un seguimiento de Netmon (por su nombre de proceso). Que le proporcionará un lugar para empezar a buscar.
    
    Si se usa sólo el seguimiento de Netmon en el momento del problema, que es demasiado correcto. Para orientar usted mismo, utilice un filtro como `ContainsBin(FrameData, ASCII, "office")` o `ContainsBin(FrameData, ASCII, "outlook")`. Puede registrar su número de marco desde el archivo de seguimiento. También es posible que desee desplazarse por el panel Resumen del marco a la derecha y busque la columna de identificador de la conversación. No hay un número indicado no existe para el identificador de esta conversación específico que también se puede registrar y mire en el aislamiento más adelante. Recuerde quitar este filtro antes de aplicar cualquier otra operación de filtrado.
    
> [!TIP]
> Netmon tiene una gran cantidad de filtros integrados útiles. Pruebe el botón "Filtro de carga" en la parte superior del panel de filtro **para mostrar** . 
  
![Busque su IP mediante el uso de PSPing en la línea de comandos en el equipo cliente.](media/4c43ac67-e28e-4536-842d-7add7aa28847.PNG)
  
![Seguimiento de Netmon desde el cliente que se muestra el mismo comando PSPing a través del filtro TCP. Flags.Syn == 1.](media/0ae7ef7d-e003-4d01-a006-dc49bd1fcef2.PNG)
  
Familiarizarse con el tráfico y obtenga información sobre cómo localizar la información que necesita. Por ejemplo, obtenga información determinar qué paquetes del seguimiento tiene la primera referencia al servicio Office 365 que está utilizando (por ejemplo, "Outlook").
    
Toma de Office 365 Online de Outlook como ejemplo, el tráfico comienza algo parecido a esto:
  
- Consulta de DNS estándar y respuesta de DNS para outlook.office365.com con coincidencia de QueryIDs. Es importante tener en cuenta el desplazamiento de tiempo para este turn-alrededor, así como where en el mundo el DNS Global de Office 365 envía la solicitud de resolución de nombres. Idealmente, localmente como sea posible, en lugar de intermedio en todo el mundo. (Esto puede ser seguido de algunas DNS tráfico al inicio de sesión en línea.)
    
- Un HTTP petición GET cuyo estado notificar movido permanentemente (301)
    
- Tráfico de RWS incluidos RWS conectar las solicitudes y respuestas de conectar. (Esto es Winsock remoto realizar una conexión para usted.)
    
- Una conversación TCP SYN y sincronización/confirmación de TCP. Una gran cantidad de la configuración de esta conversación afectar a su rendimiento.
    
- A continuación, una serie de tráfico de TLS:TLS que es donde llevará a cabo el protocolo de enlace TLS y las conversaciones de certificado TLS. (Recuerde que los datos se cifran mediante SSL/TLS).
    
Todos los elementos del tráfico son importantes y conectado, pero pequeñas partes del seguimiento contienen información particularmente importante en cuanto a la solución de problemas de rendimiento, por lo que nos centraremos en estas cuatro áreas. Además, dado que hemos hecho suficiente rendimiento de Office 365, solución de problemas en Microsoft para compilar una lista de los problemas más comunes diez más frecuentes, nos centraremos en dichos problemas y cómo usar las herramientas que tenemos acabar con ellos siguiente.
  
Si no ha instalado ellos todo lista, la siguiente matriz hace que el uso de varias herramientas. Siempre que sea posible. Se proporcionan vínculos a los puntos de instalación. La lista incluye herramientas de seguimiento de red comunes como [Netmon](https://www.microsoft.com/en-us/download/details.aspx?id=4865) y [Wireshark](https://www.wireshark.org/), pero usar cualquier herramienta de seguimiento que se encuentra cómodo con y, en la que está acostumbrados para filtrar el tráfico de red. Cuando se está probando, recuerde:
  
-  *Cierre los exploradores y probar con solo un explorador que se ejecuta* - Esto permite reducir el tráfico global de la captura. Hace un seguimiento de menos ocupado. 
    
-  *Vaciar la caché de resolución DNS en el equipo cliente* - le proporcionará un espacio vacío al iniciar realizar la captura, para un seguimiento más limpio. 
    
## <a name="some-top-issues"></a>Algunos problemas principales

Algunos problemas comunes que pueden surgir y cómo encontrarlos en el seguimiento de red.

### <a name="tcp-windows-scaling"></a>Escala de ventanas TCP

Que se encuentran en el SYN - SYN/confirmaciones heredado o hardware de antigüedad es posible que no permite aprovechar las ventanas de TCP de escala.  Sin configuración de escala de ventanas TCP adecuadas, el búfer de 16 bits de forma predeterminada en los encabezados TCP se rellena en milisegundos.  El tráfico no se puede continuar enviando hasta que el cliente recibe una confirmación de que se ha recibido los datos originales, causando retrasos.

#### <a name="tools"></a>Herramientas:

- Netmon
- Wireshark 

#### <a name="what-youre-looking-for"></a>Lo que está buscando:

Busque el SYN - sincronización/confirmación el tráfico en el seguimiento de red.  En Netmon, utilice un filtro como `tcp.flags.syn == 1`. Este filtro es la misma en Wireshark.  

![Filtro de Netmon o Wireshark para paquetes de sincronización para ambas herramientas: TCP. Flags.Syn == 1.](media/4b9a12a1-c915-43c8-ac2f-a679d0435a29.PNG)         
Tenga en cuenta que para cada SYN es un número de puerto (SrcPort) de origen que se corresponde con el puerto de destino (DstPort) de la confirmación relacionado (sincronización/confirmación). 

Para ver el valor de ajuste de escala de Windows que se usa en la conexión de red, expanda primero el SYN y, a continuación, el SYN/confirmaciones relacionados  

![Gráfico que muestra cómo hacer coincidir SrcPort a DstPort en un seguimiento, para obtener el tiempo de diferencia.](media/6a4ca573-0253-4fbd-93e8-92821ee1c351.png)  

### <a name="tcp-idle-time-settings"></a>Configuración de tiempo de inactividad de TCP

Tradicionalmente, la mayoría de las redes de perímetro están configuradas para conexiones transitorias, lo que significa que generalmente se terminan las conexiones inactivas. Pueden terminar las sesiones TCP inactivas por los servidores proxy y firewalls en mayor que 100 a 300 segundos. Esto es un inconveniente para Outlook en línea debido a que se crea y usa conexiones a largo plazo, si está inactivo o no.  

Cuando se terminan las conexiones proxy o los dispositivos de firewall, el cliente no está informado y un intento de usar Outlook en línea significa un equipo cliente intenta, repetidamente, restablece la conexión antes de realizar una nueva. Es posible que vea se bloquea en el producto, mensajes o reducir el rendimiento en la carga de la página.

#### <a name="tools"></a>Herramientas:

- Netmon
- Wireshark

#### <a name="what-to-look-for"></a>Qué buscar:

En Netmon, fíjese en el campo de desplazamiento de tiempo para un ida y vuelta. Una ida y vuelta es el tiempo entre cliente enviar una solicitud al servidor y recibir una respuesta. Comprobar entre el cliente y el punto de salida (ej cliente--\> Proxy), o el cliente de Office 365 (cliente--\> Office 365). Puede ver esto en muchos tipos de paquetes. 

Por ejemplo, es posible que aspecto el filtro en Netmon `.Protocol.IPv4.Address == 10.102.14.112 AND .Protocol.IPv4.Address == 10.201.114.12`, o bien, en Wireshark, `ip.addr == 10.102.14.112 &amp;&amp; ip.addr == 10.201.114.12`.  

> [!TIP]
> ¿No sabe si la dirección IP en su seguimiento pertenece a su servidor DNS? Intente buscar en la línea de comandos. Haga clic en **Inicio** \> **Ejecutar** \> y escriba **cmd**, o presione la **Tecla de Windows** \> y escriba **cmd**. En el símbolo del sistema, escriba `nslookup <the IP address from the network trace>`. Para probar, use nslookup frente a la dirección IP de su propio equipo. > Para ver una lista de intervalos IP de Microsoft, vea [las direcciones URL de Office 365 y los intervalos de direcciones IP](https://technet.microsoft.com/en-us/library/hh373144.aspx). 

Si hay un problema, esperar largo tiempo, se desplaza a aparecen en este caso (Outlook en línea), especialmente en los paquetes de TLS:TLS que muestran el paso de los datos de la aplicación (por ejemplo, en Netmon puede encontrar los paquetes de datos de aplicación a través de `.Protocol.TLS AND Description == "TLS:TLS Rec Layer-1 SSL Application Data"`). Debería ver una progresión uniforme en el tiempo a través de la sesión. Si ve grandes retrasos al actualizar Outlook conectado, esto podría deberse a un alto grado de restablecimientos de que se está enviando. 

### <a name="latencyround-trip-time"></a>Tiempo de viaje de ida/latencia 

La latencia es una medida que puede cambiar mucho dependiendo muchas variables, este tipo de actualización de dispositivos de antigüedad, agregar un gran número de usuarios a una red y el porcentaje de ancho de banda general consumido por otras tareas en una conexión de red. 

Existen calculadoras de ancho de banda para Office 365 desde esta página de [Diseño de la red y ajuste del rendimiento de Office 365](network-planning-and-performance.md) .  

¿Necesita medir la velocidad de la conexión o ancho de banda de la conexión de su ISP? Pruebe este sitio (o los sitios le gusta): [Sitio oficial de Speedtest](https://www.speedtest.net/)y [Pingtest](http://www.pingtest.net/).

#### <a name="tools"></a>Herramientas:

- Ping
- PsPing
- Netmon
- Wireshark

#### <a name="what-to-look-for"></a>Qué buscar:

Para realizar un seguimiento de un seguimiento de la latencia, se beneficiarán de tener registrada la dirección IP del equipo cliente y la dirección IP del servidor DNS en Office 365. Esto es con el fin de facilitar el filtrado de seguimiento. Si se conecta a través de un servidor proxy, necesitará la dirección IP del equipo cliente, la dirección IP de proxy/salida y la dirección IP de DNS de Office 365, para facilitar el trabajo.  

Una solicitud de ping enviada a outlook.office365.com le indicará el nombre del centro de datos recibir la solicitud, incluso si ping *es posible que* no pueda conectar para enviar la marca los paquetes ICMP consecutivos. Si utiliza PsPing (es decir, una herramienta gratuita para su descarga) y el puerto (443) específicos y, posiblemente, para usar IPv4 (-4) que obtiene una round-trip-tiempo promedio de paquetes enviados. Esto funcionará esto para otras direcciones URL en los servicios de Office 365, como `psping -4 yourSite.sharepoint.com:443`. De hecho, puede especificar un número de llamadas ping para obtener un ejemplo más extenso para su try promedio, similar al siguiente: `psping -4 -n 20 yourSite-my.sharepoint.com:443`.  

> [!NOTE]
> PsPing no envía paquetes ICMP. Hace ping con paquetes TCP a través de un puerto específico, por lo que puede usar cualquier uno que sabe que esté abierto. En Office 365, que usa SSL/TLS, intente adjuntar puerto: 443 a su PsPing.

![Captura que muestra un ping resolución de outlook.office365.com y un PSPing con el 443 haciendo lo mismo, pero también informes un RTT promedio 6.5ms de pantalla.](media/c64339f2-2c96-45b8-b168-c2a060430266.PNG)        

Si carga la página de Office 365 rendimiento lento mientras se hace un seguimiento de red, que se debe filtrar un seguimiento de Netmon o Wireshark para `DNS`. Ésta es una de las direcciones IP que estamos buscando.  

Estos son los pasos a seguir para filtrar su Netmon para obtener la dirección IP (y eche un vistazo a la latencia de DNS). En este ejemplo se utiliza outlook.office365.com, pero también puede usar la dirección URL de un inquilino de SharePoint Online (hithere.sharepoint.com por ejemplo).  

1. Haga ping a la dirección URL `ping outlook.office365.com` y, en los resultados, anote el nombre y la dirección IP del servidor DNS que se envió la solicitud de ping a. 
2. Red abrir la página de seguimiento o realiza la acción que proporciona el problema de rendimiento o, si ve una latencia alta en el comando ping, propiamente dicha, seguimiento de red se. 
3. Abrir el seguimiento de Netmon y filtro para DNS (este filtro también funciona en Wireshark, pero minúsculas `-- dns`). Dado que conoce el nombre del servidor DNS desde el comando ping también puede filtrar más rápidamente en Netmon similar: `DNS AND ContainsBin(FrameData, ASCII, "namnorthwest")` , que tiene este aspecto en Wireshark dns y marco contiene "namnorthwest".</br>Abra el paquete de respuesta y, en la ventana de detalles de las tramas de Netmon, haga clic en DNS para expandir para obtener más información. En la información de DNS que encontrará la dirección IP del servidor DNS que la solicitud ha producido un problema en Office 365--que necesitará esta dirección IP para el siguiente paso (la herramienta de PsPing). Quitar el filtro, haga clic en la respuesta de DNS en resumen de marco de Netmon \> buscar conversaciones \> DNS para ver la consulta DNS y respuesta--paralelo. 
4. En Netmon, tenga en cuenta también la columna de desplazamiento de tiempo entre la solicitud de DNS y la respuesta. En el siguiente paso, fácil de instalar y usar [PsPing](https://technet.microsoft.com/en-us/sysinternals/jj729731.aspx) herramienta resulta muy práctica, porque a menudo está bloqueado ICMP en los Firewalls y debido a que PsPing elegante realiza un seguimiento de latencia en milisegundos. PsPing finalice una conexión TCP con una dirección y el puerto (en nuestro caso abra el puerto 443). 
5. Instalar PsPing. 
6. Abra un símbolo del sistema (iniciar \> ejecutar \> escriba cmd o clave de Windows \> escriba cmd) y cambie el directorio al directorio donde ha instalado PsPing para ejecutar el comando PsPing. En mis ejemplos se puede ver que se ha realizado una carpeta 'Rendimiento' en la raíz de C. Puede hacer lo mismo con acceso rápido. 
7. Escriba el comando para que está realizando la PsPing según la dirección IP del servidor DNS de Office 365 desde su seguimiento Netmon anterior, no olvide agregar el número de puerto. </br>En otras palabras, `psping -n 20 132.245.24.82:445`. Esto podrá un muestreo de llamadas 20 ping y promedio de la latencia cuando deja de PsPing. 

Si va a Office 365 a través de un servidor proxy, los pasos son un poco diferentes. Lo haría PsPing primero el servidor proxy para obtener un valor promedio de latencia en milisegundos para proxy/salida y back y, a continuación, ejecute PsPing en el servidor proxy, o en un equipo con una conexión directa a Internet para obtener el valor que falta (uno a Office 365 y back).  

Si opta por ejecutar PsPing desde el servidor proxy, tendrá dos valores de milisegundo: equipo de cliente a servidor proxy o el punto de salida y servidor proxy a Office 365. Y ya está! Bueno, grabación, los valores de todos modos.  

Si ejecuta PsPing en otro equipo cliente que tiene una conexión directa a Internet, es decir, sin un servidor proxy, tendrá dos valores de milisegundo: equipo de cliente a servidor proxy o el punto de salida y del equipo cliente para Office 365. Restar en este caso, el valor del equipo cliente al punto de salida o de servidor proxy respecto al valor del equipo cliente para Office 365 y tendrán los números RTT desde el equipo cliente hasta el punto de salida o de servidor proxy y de proxy server o salida elija Offi CE 365. 

Sin embargo, si un equipo cliente se puede encontrar en la ubicación afectada que está conectada directamente u omite al servidor proxy, es posible que elija ver si el problema se reproduce para empezar y probar con ella, a partir de entonces. 

Latencia, tal como se muestra en un seguimiento de Netmon, esos milisegundos adicionales pueden agregar copia de seguridad, si hay suficiente de ellos en cualquier sesión determinada.  

![Latencia general de Netmon, con la columna de diferencia de tiempo predeterminada de Netmon agregada al Resumen de marco.](media/7ad17380-8527-4bc2-9b9b-6310cf19ba6b.PNG)

> [!NOTE]
> La dirección IP puede ser diferente de las direcciones IP que se muestra aquí, por ejemplo, que el comando ping puede devolver algo más parecido a 157.56.0.0/16 o un rango similar. Para obtener una lista de intervalos utilizados por Office 365, desproteger [las direcciones URL de Office 365 y los intervalos de direcciones IP](https://technet.microsoft.com/en-us/library/hh373144.aspx). 

Recuerde que debe expandir todos los nodos (hay un botón en la parte superior de este) si desea buscar, por ejemplo, 132.245.

### <a name="proxy-authentication"></a>Autenticación de proxy

Esto sólo se aplica a usted si va a través de un servidor proxy. Si no es así, puede omitir estos pasos. Cuando funciona correctamente, la autenticación proxy tendrá lugar en milisegundos, de forma coherente. No debería ver un rendimiento incorrecto intermitente durante los períodos de uso (por ejemplo).  

Si la autenticación Proxy está habilitado, cada vez que realice una nueva conexión TCP a Office 365 para obtener información, debe pasar a través de un proceso de autenticación en segundo plano. Por lo tanto, por ejemplo, cuando se cambia de calendario para correo en Outlook en línea, se va a realizar la autenticación. Y en SharePoint Online, si muestra una página de medios o datos de varios sitios o ubicaciones, se va a realizar la autenticación para cada conexión TCP diferente que se necesita para representar los datos.  

En Outlook en línea puede experimentar tiempos de carga lenta de cada vez que cambia entre calendario y su buzón de correo o lenta página se carga en SharePoint Online. Sin embargo, hay otros síntomas que no se muestran aquí. 

Autenticación de proxy es una opción de configuración en el servidor de proxy de salida. Si se está generando un problema de rendimiento con Office 365, deberá consultar a su equipo de red.  

#### <a name="tool"></a>Herramienta: 

- Netmon
- Wireshark 

#### <a name="what-to-look-for"></a>Qué buscar:

Proxy autenticación lleva a cabo cada vez que una nueva sesión TCP debe poner en marcha, con frecuencia para solicitar los archivos o información desde el servidor, o para proporcionar información. Por ejemplo, es posible que vea autenticación proxy alrededor de las solicitudes HTTP POST o HTTP GET. Si desea ver los marcos donde se autentican las solicitudes en su seguimiento, agregar la columna 'NTLMSSP resumen' Netmon y filtrar para `.property.NTLMSSPSummary`. Para ver cuánto está tomando la autenticación, agregue la columna de Delta de tiempo. 

Para agregar una columna a Netmon: 
1. Haga clic en una columna como descripción. 
2. Haga clic en Elegir columnas. 
3. Busque NTLMSSP resumen y Delta de tiempo en la lista y haga clic en Agregar. 
4. Traslado de las nuevas columnas en su lugar antes o detrás de la columna de descripción por lo que puede leer en paralelo.
5. Haga clic en Aceptar. 

Incluso si no agregar la columna, el filtro de Netmon funcionará. Pero será mucho más sencillo si puede ver qué escenario de autenticación está en la solución de problemas. 

Cuando está presente al buscar instancias de autenticación de Proxy, asegúrese de estudiar todos los marcos donde hay un desafío de NTLM, o un mensaje de autenticar. Si es necesario, haga clic en el elemento específico de tráfico y buscar conversaciones \> TCP. Tenga en cuenta los valores de Delta de tiempo en estas conversaciones. 

![Netmon seguimiento que muestra autenticación proxy, filtrada por conversación.](media/b640f176-0a52-4bbb-972e-60fb3d6aece2.PNG)        

Un segundo cuatro retraso en la autenticación proxy tal y como se puede apreciar en Wireshark. La columna de **delta de tiempo de fotograma mostrado anterior** se realizó a través de bien el campo del mismo nombre en los detalles de marco y seleccione Agregar como columna.<br/> ![En Wireshark, se puede establecer la columna 'Delta de tiempo de fotograma mostrado anterior' a través de bien el campo del mismo nombre en los detalles de marco y seleccione Agregar como columna.](media/f5b7bde4-8067-4ee0-bc7f-e9062ce1ba6f.PNG)        

### <a name="dns-performance"></a>Rendimiento de DNS

Nombre de la solución funciona mejor y más rápidamente cuando lleva a cabo lo más cerca del país del cliente como sea posible. 

Si la resolución de nombres DNS está produciendo extranjero, pueden agregar a segundos a la carga de las páginas. Idealmente, la resolución de nombres ocurre en 100 ms. Si no, debe realizar una investigación más minuciosa. 

> [!TIP]
> ¿No está seguro de cómo funciona la conectividad de cliente en Office 365? Eche un vistazo en el documento de referencia de la conectividad de cliente [aquí](https://technet.microsoft.com/en-us/library/dn741250.aspx).           

#### <a name="tools"></a>Herramientas: 

- Netmon
- Wireshark
- PsPing

#### <a name="what-to-look-for"></a>Qué buscar:
Analizar el rendimiento de DNS es normalmente otra tarea para un seguimiento de red. Sin embargo, también es útil en la decisión, o desprotege una causa posible PsPing. 

El tráfico DNS se basa en TCP y UDP las solicitudes y respuestas claramente marcadas con un identificador que le ayudarán a para que coincida con una solicitud específica con su respuesta específico. Verá DNS tráfico cuando, por ejemplo, SharePoint Online usa un nombre de red o la dirección URL en una página web. Como regla general, la mayor parte de este tráfico, excepto cuando la transferencia de zonas, se ejecuta a través de UDP. 

En Netmon y Wireshark, el filtro más básico que le permitirá examine el tráfico DNS es simplemente `dns`. Asegúrese de usar minúsculas al especificar el filtro. No olvide vaciar la caché de resolución DNS antes de comenzar a reproducir el problema en el equipo cliente. Por ejemplo, si tiene una carga de página de SharePoint Online lenta para la página principal, debe cerrar todos los exploradores, abra una nueva ventana del explorador, inicie el seguimiento, vaciar la caché de resolución DNS y vaya al sitio de SharePoint Online. Una vez que se resuelve toda la página, debe detener y guarde el seguimiento.

![Un filtro básico para DNS en Netmon es DNS.](media/1bebc118-ca13-45f3-803f-ab73e7af401d.png)

Que desea buscar en el tiempo de desplazamiento aquí. Y puede resultar útil agregar la columna de **Delta de tiempo** a Netmon que se puede realizar mediante la realización de estos pasos: 
1. Haga clic en una columna como descripción. 
2. Haga clic en Elegir columnas. 
3. Busque Delta de tiempo en la lista y haga clic en Agregar. 
4. Mover la nueva columna en su lugar antes o detrás de la columna de descripción por lo que puede leer en paralelo.
5. Haga clic en Aceptar. 

Si una consulta de interés, considere la posibilidad de aislar haciendo doble clic en esa consulta en el panel de detalles de marco, elegir **Buscar conversaciones** \> **DNS**. Tenga en cuenta que el panel de las conversaciones de red salta derecha a la conversación específica en su registro de tráfico UDP. 

![Un seguimiento de Netmon de carga en línea de Outlook filtrados por DNS y uso de buscar conversaciones, a continuación, en DNS para restringir los resultados.](media/763cf20e-7b48-4a37-9449-c9978cfe118b.PNG)        

En Wireshark puede hacer que una columna para el tiempo DNS. Realizar el seguimiento (o abra un seguimiento) en Wireshark y filtro por `dns`, o bien, ofrece más ayuda, `dns.time`. Haga clic en cualquier consulta DNS y, en el panel que muestra los detalles, expanda la `Domain Name System (response)` obtener información detallada. Verá un campo de tiempo (por ejemplo, ` [Time: 0.001111100 seconds] `. Haga clic en este momento y seleccione **aplicar como columna**. Esto le proporcionará una columna de **tiempo** para la ordenación más rápidas de su seguimiento. Haga clic en la nueva columna para ordenar de forma descendente valores para ver qué llamadas DNS tardaron más tiempo libre para resolver. 

[Una exploración de SharePoint Online filtrada en Wireshark por dns.time (minúscula), con el tiempo de los detalles convertido en columna y ordenado de forma ascendente.](media/1439dcc2-12ff-4ee2-9ef3-1484cf79c384.PNG)

Si desea hacer una mayor investigación del tiempo de resolución DNS, intente un PsPing contra el puerto DNS usado por TCP (por ejemplo, `psping <IP address of DNS server>:53`). ¿Puede ver aún un problema de rendimiento? Si lo hace, el problema es más probable que sea una red más amplia de asuntos que un problema específico de la aplicación de DNS se llega a para llevar a cabo resolución. Es también vale la pena mencionar, una vez más, que un ping a outlook.office365.com le indicará donde resolución de nombres DNS para Outlook Online está produciendo (por ejemplo, outlook-namnorthwest.office365.com).<br/> Si el problema tiene un aspecto para que sea específica de DNS, puede ser necesario ponerse en contacto con el departamento de TI para buscar en las configuraciones de DNS y servidores de reenvío de DNS para investigar este problema. 

### <a name="proxy-scalability"></a>Escalabilidad de proxy

Servicios como Outlook Online en Office 365 conceden a los clientes de varias conexiones a largo plazo. Por lo tanto, cada usuario puede utilizar más conexiones que requieren una mayor duración.  

> [!TIP]
> ¿Debe planear el uso de ancho de banda debido a que se va a agregar mucho a los usuarios a Office 365? Pruebe a [Planear el uso de ancho de banda de Internet para Office 365](https://technet.microsoft.com/en-us/library/hh852542.aspx). Existen calculadoras de ancho de banda disponible no existe.

#### <a name="tool"></a>Herramienta:
 
Math  

#### <a name="what-to-look-for"></a>Qué buscar: 

No hay ningún seguimiento de red o la herramienta de solución de problemas específicos a la siguiente. En su lugar, se basa en los cálculos de ancho de banda asignado limitaciones y otras variables.  

### <a name="tcp-max-segment-size"></a>Tamaño del segmento de Max TCP

Que se encuentra en el SYN - ACK SYN /.  Realizar esta comprobación en cualquier seguimiento de rendimiento de red que ha tomado para garantizar que los paquetes TCP están configurados para llevar a cabo la cantidad máxima de datos posibles. 

El objetivo es ver un MSS de 1460 bytes para la transmisión de datos. Si está detrás de un proxy o está utilizando un dispositivo NAT, no olvide ejecutar esta prueba de cliente de salida/proxy o NAT y de salida/proxy/NAT a Office 365 para obtener los mejores resultados! Se trata de las distintas sesiones TCP.

#### <a name="tool"></a>Herramienta: 

Netmon

#### <a name="what-to-look-for"></a>Qué buscar:

Tamaño de segmento de Max (MSS) de TCP es otro parámetro del protocolo de enlace de tres vías en la traza de red, que significa que encontrará los datos que necesita en el SYN - paquetes de sincronización/confirmación. MSS es bastante sencillo ver. 

Abra cualquier seguimiento de rendimiento de red tiene y encontrar la conexión de que tiene curiosidad acerca, o muestra el problema de rendimiento. 

> [!NOTE]
> Si está viendo un seguimiento y necesita encontrar el tráfico correspondiente a su conversación, se filtra según la dirección IP del cliente o la dirección IP del servidor proxy o el punto de salida o ambos. Va directamente, debe hacer ping a la dirección URL que se está probando para la dirección IP de Office 365 en el seguimiento y filtro por ella. 

¿Está buscando en el seguimiento de la segunda mano? Intente utilizar filtros para orientar usted mismo. En Netmon, ejecutar una búsqueda basada en la dirección URL, como `Containsbin(framedata, ascii, "sphybridExample")`, tome nota del número de marco. 

En Wireshark usar algo como `frame contains "sphybridExample"`. Si observa que ha encontrado el tráfico de Winsock remoto (RWS) (que es posible que aparezca como una [Psh:, confirmación] en Wireshark), recuerde que se conecta RWS puede verse en breve antes relevante SYN - SYN/confirmaciones, como se explicó anteriormente. 

En este momento, puede registrar el número de trama, colocar el filtro, haga clic en todo el tráfico en la ventana de las conversaciones de red en Netmon mirar el SYN más cercano. 

Lo que es importante, si no ha recibido alguna de la información de dirección IP en el momento de la traza, búsqueda de la dirección URL en el seguimiento (parte de `sphybridExample-my.sharepoint.com`, por ejemplo), le proporcionará las direcciones IP para filtrar por. 

Busque la conexión en el seguimiento de la que está interesado en ver. Puede hacerlo mediante el examen el seguimiento mediante el filtrado de direcciones IP, o seleccionando ID de conversación específicos mediante la ventana de las conversaciones de red en Netmon. Una vez que ha encontrado el paquete SYN, expanda TCP (en Netmon) o protocolo de Control de transmisión (en Wireshark) en el panel de detalles de las tramas. Expanda MaxSegementSize y opciones de TCP. Busque el marco de ataque de SYN relacionado y expanda Opciones de TCP y MaxSegmentSize. El menor de los dos valores será su tamaño máximo de segmento. En esta imagen, se puede realizar el uso de la columna integrada en Netmon llama a solucionar problemas de TCP.  

![Seguimiento de red filtrado en Netmon con las columnas integradas.](media/e073df13-71f8-497a-83b4-bb9f70bd9833.PNG)

Es la columna integrada en la parte superior del panel de **Detalles de las tramas** . (Para volver a la vista normal, haga clic de nuevo en columnas y, a continuación, elija zona horaria). 

![Dónde encontrar la lista de columnas desplegable para la opción de Solucionar problemas de TCP (arriba del Resumen de marco).](media/64fd4baa-a872-4f07-b959-752d7d37fd62.PNG)           
Aquí tiene un seguimiento filtrado en Wireshark. Hay un filtro específico para el valor de MSS ( `tcp.options.mss`). Los marcos de SYN, sincronización/confirmación, el protocolo de enlace de confirmación están vinculados en la parte inferior de la Wireshark equivalente a los detalles de las tramas (por lo que contenga confirmación 47, vínculos a 46 sincronización/confirmación, vínculos a SYN 43) para facilitar este tipo de trabajo. 

![Seguimiento filtrado en Wireshark por tcp.options.mss para el tamaño de segmento máximo (MSS).](media/51e278db-801b-48bc-9b68-87cf92f03fd6.PNG)         
Si necesita comprobar confirmación selectiva (tema siguiente en esta matriz), no cierre su seguimiento!

### <a name="selective-acknowledgment"></a>Confirmación selectiva

Que se encuentran en el SYN - SYN/confirmaciones deben ser notificado como permitidos en SYN y confirmación selectiva de SYN/confirmaciones (SACK) permite la retransmisión más suave de datos cuando un paquete o paquetes vaya que faltan. Dispositivos pueden deshabilitar esta característica, que puede dar lugar a problemas de rendimiento. 

Si está detrás de un proxy o está utilizando un dispositivo NAT, no olvide ejecutar esta prueba de cliente de salida/proxy o NAT y de salida/proxy/NAT a Office 365 para obtener los mejores resultados! Se trata de las distintas sesiones TCP.

#### <a name="tool"></a>Herramienta: 

Netmon 

#### <a name="what-to-look-for"></a>Qué buscar:

Confirmación selectiva (SACK) es otro parámetro en el protocolo de enlace SYN-sincronización/confirmación. Puede filtrar el seguimiento para SYN - sincronización/confirmación de muchas maneras. 

Busque la conexión en el seguimiento de la que está interesado en ver ya sea mediante el examen de la traza, filtrado de direcciones IP, o haciendo clic en un identificador de conversación de uso de la ventana de las conversaciones de red en Netmon. Una vez que ha encontrado el paquete SYN, expanda TCP en Netmon o protocolo de Control de transmisión en Wireshark en la sección detalles del marco. Expanda las opciones de TCP y, a continuación, bolsa. Busque el marco de SYN relacionado y expanda Opciones de TCP y su campo SACK. Asegúrese de que está permitido SACK en SYN y SYN/confirmaciones Aquí son valores SACK tal y como se puede apreciar en Netmon y Wireshark.

![Confirmación selectiva (SACK) en Netmon como resultado de tcp.flags.syn == 1.](media/216f556f-5031-4ed2-b066-a0d9b3251fa2.PNG)           <br/> ![BOLSA tal y como aparece en Wireshark con el filtro tcp.flags.syn == 1.](media/0a6e26e5-43dc-403b-adc9-3349a55f4e4b.PNG)        

### <a name="dns-geolocation"></a>Ubicación geográfica DNS 

Cuando en el mundo Office 365 intenta resolver el DNS llame a efectos de la velocidad de conexión. 

En Outlook Online, una vez finalizada la primera búsqueda de DNS, la ubicación de ese DNS se usará para conectarse a su centro de datos más cercano. Se conectará a un servidor de entidades de certificación en línea de Outlook, que usará la red troncal de red para conectarse al centro de datos (dC) donde se almacenan los datos. Esto es más rápido.

Al obtener acceso a SharePoint Online, un usuario que viajan en el extranjero se dirigirán a su centro de datos activo--que es el controlador de dominio cuya ubicación se basa en su inquilino SPO de la página principal de base (por lo tanto, un controlador de dominio en los Estados Unidos si el usuario si basada en Estados Unidos).  <br/>  Lync online tiene nodos activos en más de un controlador de dominio a la vez. Cuando las solicitudes están enviados para Lync online instancias, Microsoft DNS determinará en el mundo de la solicitud de procedencia y devolver direcciones IP desde el controlador de dominio regional más cercano donde Lync online está activo. 

> [!TIP]
> ¿Necesita saber más información acerca de cómo los clientes se conectan a Office 365? Eche un vistazo en el artículo de referencia de la [Conectividad de cliente](https://technet.microsoft.com/en-us/library/dn741250.aspx) (y sus gráficos útiles).           
#### <a name="tools"></a>Herramientas:

- Ping
- PsPing

#### <a name="what-to-look-for"></a>Qué buscar:

En caso de las solicitudes de resolución de nombres de los servidores DNS del cliente a los servidores DNS de Microsoft en el resultado de la mayoría de los casos en devolver la dirección IP de un centro de datos regional (dC) de DNS de Microsoft. ¿Qué significa esto para usted? Si sus sedes centrales se encuentran en Bangalore, India, pero está de viaje en los Estados Unidos, cuando el explorador realiza una solicitud para Outlook en línea, los servidores DNS de Microsoft deben entregará direcciones IP en centros de datos en los Estados Unidos--un centro de datos regional. Si se necesita el correo de Outlook, se trasladarán esos datos a través de red troncal de red rápido de Microsoft entre los centros de datos.

DNS funciona más rápido cuando se realiza la resolución de nombres cerca de la ubicación del usuario como sea posible. Si se encuentra en Europa, desea que vaya a un DNS de Microsoft en Europa y abordar los problemas (lo ideal) con un centro de datos en Europa. Rendimiento de un cliente en Europa va a DNS y un centro de datos de América será más lento.

Ejecutar la herramienta de Ping en outlook.office365.com para determinar donde se se enruta la solicitud DNS en el mundo. Si se encuentra en Europa, debería ver un mensaje de respuesta de algo como emeawest.office365.com de outlook. En América, esperar a que algo como namnorthwest.office365.com de outlook. 

Abra el símbolo del sistema en el equipo cliente (a través de inicio \> ejecutar \> cmd o clave de Windows \> escriba cmd). Escriba ping outlook.office365.com y presione ENTRAR. Recuerde que, para especificar -4 si desea especificar para hacer ping a través de IPv4. Puede producirse un error obtener una respuesta de los paquetes de ICMP, pero debería ver el nombre del DNS a la que se redirige la solicitud. Si desea ver los números de latencia para esta conexión intente PsPing a la dirección IP del servidor que es devuelto por ping.  

![Ping de outlook.office365.com que muestra la resolución en outlook-namnorthwest.](media/06c944d5-6159-43ec-aa31-757770695e8b.PNG)           
![PSPing a la dirección IP devuelta por el comando ping para outlook.office365.com muestra la latencia promedio de milisegundo 28.](media/f2b25a75-1a87-4479-b8a7-fa4375683507.PNG)           
### <a name="office-365-application-troubleshooting"></a>Solución de problemas de aplicación de Office 365

#### <a name="tools"></a>Herramientas: 

- Netmon
- HTTPWatch
- Consola de F12 en el explorador

No tratamos las herramientas usadas para solucionar problemas específicos de la aplicación en este artículo específicos de la red. Encontrará recursos, pero se *puede* usar [en esta página](https://support.office.com/en-us/article/Network-planning-and-performance-tuning-for-Office-365-e5f1228c-da3c-4654-bf16-d163daee8848).
   
## <a name="related-topics"></a>Temas relacionados

[Administración de extremos de Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Preguntas más frecuentes de los extremos de Office 365](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
  

