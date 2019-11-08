---
title: Plan de solución de problemas de rendimiento para Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 5/10/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: e241e5d9-b1d8-4f1d-a5c8-4106b7325f8c
ms.collection:
- M365-security-compliance
- Ent_O365
description: ¿Necesita conocer los pasos que debe seguir para identificar y corregir los intervalos, los bloqueos y el rendimiento lento entre SharePoint Online, OneDrive para la empresa, Exchange online o Skype empresarial online, y el equipo cliente? Antes de llamar al soporte técnico, este artículo puede ayudarle a solucionar problemas de rendimiento de Office 365 e incluso a solucionar algunos de los problemas más comunes.
ms.openlocfilehash: e0117cebc80acbd2b29ce319002dbd3dccafb764
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2019
ms.locfileid: "38031135"
---
# <a name="performance-troubleshooting-plan-for-office-365"></a>Plan de solución de problemas de rendimiento para Office 365

¿Necesita conocer los pasos que debe seguir para identificar y corregir los intervalos, los bloqueos y el rendimiento lento entre SharePoint Online, OneDrive para la empresa, Exchange online o Skype empresarial online, y el equipo cliente? Antes de llamar al soporte técnico, este artículo puede ayudarle a solucionar problemas de rendimiento de Office 365 e incluso a solucionar algunos de los problemas más comunes.
  
Este artículo es, en realidad, un plan de acción de ejemplo que se puede usar para capturar datos valiosos sobre el problema de rendimiento a medida que se produzcan. También se incluyen algunos problemas principales en este artículo.

Si no está familiarizado con el rendimiento de la red y desea crear un plan a largo plazo para supervisar el rendimiento entre los equipos cliente y Office 365, eche un vistazo a [office 365 performance tuning and Troubleshooting-admin y IT Pro](performance-tuning-using-baselines-and-history.md).
  
## <a name="sample-performance-troubleshooting-action-plan"></a>Ejemplo de plan de acción de solución de problemas de rendimiento

Este plan de acción contiene dos partes; una fase de preparación y una fase de registro. Si tiene un problema de rendimiento en este momento y necesita realizar la recopilación de datos, puede empezar a usar este plan inmediatamente.
  
### <a name="prepare-the-client-computer"></a>Preparar el equipo cliente
  
- Busque un equipo cliente que pueda reproducir el problema de rendimiento. Este equipo se usará durante la solución de problemas.
- Anote los pasos que provocan el problema de rendimiento para que esté listo cuando llegue el momento de realizar la prueba.
- Instalar herramientas para recopilar y registrar información:
  - Instale [Netmon 3,4](https://www.microsoft.com/download/details.aspx?id=4865) (o use una herramienta de seguimiento de red equivalente).
  - Instale la edición básica gratuita de [HTTPWatch](https://www.httpwatch.com/download/) (o use una herramienta de seguimiento de red equivalente).
  - Use una grabadora de pantalla o ejecute el grabador de acciones (PSR. exe) que se incluye con Windows Vista y versiones posteriores para mantener un registro de los pasos que debe seguir durante las pruebas.

### <a name="log-the-performance-issue"></a>Registrar el problema de rendimiento
  
- Cierre todos los exploradores extraños de Internet.
- Inicie el grabador de acciones u otra grabadora de pantalla.
- Inicie la captura de Netmon (o la herramienta de seguimiento de red).
- Para borrar la memoria caché de DNS en el equipo cliente de la línea de comandos, escriba ipconfig/flushdns.
- Inicie una nueva sesión del explorador y Active HTTPWatch.
- Opcional: Si está probando Exchange Online, ejecute la herramienta analizador de rendimiento del cliente de Exchange desde la consola de administración de Office 365.
- Reproduzca los pasos exactos que causan el problema de rendimiento.
- Detenga la traza de la herramienta Netmon o de otro fabricante.
- En la línea de comandos, ejecute una ruta de seguimiento a su suscripción a Office 365; para ello, escriba el siguiente comando y presione ENTRAR:

  ``` cmd
  tracert <subscriptionname>.onmicrosoft.com
  ```

- Detenga la grabación de acciones y guarde el vídeo. Asegúrese de incluir la fecha y la hora de la captura y de si muestra un rendimiento bueno o incorrecto.
- Guarde los archivos de seguimiento. De nuevo, asegúrese de incluir la fecha y la hora de la captura y de si muestra un rendimiento bueno o incorrecto.

Si no está familiarizado con la ejecución de las herramientas mencionadas en este artículo, no se preocupe porque le ofrecemos los pasos a continuación. Si está acostumbrado a realizar este tipo de capturas de red, puede omitir [cómo recopilar líneas de base](performance-tuning-using-baselines-and-history.md#how-to-collect-baselines), lo que describe el filtrado y la lectura de los registros.
  
### <a name="flush-the-dns-cache-first"></a>Vacíe primero la memoria caché de DNS

¿Por qué? Vaciando la memoria caché DNS que va a iniciar las pruebas con una tableta limpia. Al borrar la caché, se restablece el contenido de la resolución DNS a las entradas más actualizadas. Recuerde que un vaciado no quita las entradas del archivo de hosts. Si usa las entradas de archivo de HOST extensivamente, debe copiar esas entradas en un archivo de otro directorio y, a continuación, vaciar el archivo HOST.
  
#### <a name="flush-your-dns-resolver-cache"></a>Vaciar la memoria caché de resolución de DNS
  
1. Abra el símbolo del sistema ( **inicie** \> **Ejecutar** \> **cmd** o CMD **clave** \> **** de Windows).
2. Escriba el siguiente comando y presione ENTRAR:

    ``` cmd
    ipconfig /flushdns
    ```

## <a name="netmon"></a>Netmon

La herramienta de supervisión de red ([Netmon](https://www.microsoft.com/download/details.aspx?id=4865)) de Microsoft analiza los paquetes, es decir, el tráfico que pasa entre los equipos de las redes. Mediante el uso de Netmon para realizar un seguimiento del tráfico con Office 365, puede capturar, ver y leer encabezados de paquetes, identificar dispositivos que intervienen, comprobar configuraciones importantes en el hardware de red, buscar paquetes perdidos y seguir el flujo de tráfico entre los equipos de la organización. red y Office 365. Dado que el cuerpo real del tráfico está cifrado, es decir, se transmite en el puerto 443 mediante SSL/TLS, no se pueden leer los archivos que se envían. En su lugar, obtiene un seguimiento sin filtrar de la ruta que lleva el paquete y que puede ayudarle a localizar el comportamiento del problema.
  
Asegúrese de no aplicar un filtro en este momento. En su lugar, realice los pasos y muestre el problema antes de detener el seguimiento y guardarlo.
  
Después de instalar Netmon 3,4, abra la herramienta y siga estos pasos:
  
### <a name="take-a-netmon-trace-and-reproduce-the-issue"></a>Realizar un seguimiento de Netmon y reproducir el problema
  
1. Inicie Netmon 3,4.
Hay tres paneles en la página de **Inicio** : **capturas recientes**, **Seleccione redes**y la **introducción al monitor de red de Microsoft 3,4. Aviso**. El panel Seleccionar redes también le proporcionará una lista de las redes predeterminadas que puede capturar. Asegúrese de que las tarjetas de red están seleccionadas aquí.

2. Haga clic en **nueva captura** en la parte superior de la página de **Inicio** . Se agrega una pestaña nueva junto a la ficha Página de **Inicio** denominada **captura 1**.
![La interfaz de usuario de Netmon con los nuevos botones capturar, iniciar y detener resaltados.](media/d4527d84-62ec-4301-82d5-e0166ff71f20.PNG)

3. Para realizar una captura simple, haga clic en **Inicio** en la barra de herramientas.

4. Reproduzca los pasos que presentan un problema de rendimiento.

5. Haga clic en **detener** \> **archivo** \> **Guardar como**. No olvide dar la fecha y la hora con la zona horaria y mencione si muestra un buen rendimiento o mal.

## <a name="httpwatch"></a>HTTPWatch

[HTTPWatch](https://www.httpwatch.com/download/) incluye carga y una edición gratuita. La edición básica gratuita cubre todo lo que necesita para esta prueba. HTTPWatch supervisa el tráfico de red y el tiempo de carga de páginas directamente desde la ventana del explorador. HTTPWatch es un complemento de Internet Explorer que describe gráficamente el rendimiento. El análisis se puede guardar y ver en HTTPWatch Studio.
  
> [!NOTE]
> Si usa otro explorador, como Firefox, Google Chrome o si no puede instalar HTTPWatch en Internet Explorer, abra una nueva ventana del explorador y presione F12 en el teclado. Debería ver el elemento emergente de la herramienta de desarrollo en la parte inferior del explorador. Si usa opera, presione CTRL + MAYÚS + I para inspector web, a continuación, haga clic en la pestaña **red** y complete las pruebas descritas a continuación. La información será ligeramente distinta, pero los tiempos de carga seguirán apareciendo en milisegundos. > HTTPWatch también es muy útil para los problemas con tiempos de carga de páginas de SharePoint Online.
  
### <a name="run-httpwatch-and-reproduce-the-issue"></a>Ejecutar HTTPWatch y reproducir el problema
  
HTTPWatch es un complemento del explorador, por lo que exponer la herramienta en el explorador es ligeramente diferente para cada versión de Internet Explorer. Normalmente, puede encontrar HTTPWatch en la barra de comandos en el explorador Internet Explorer. Si no ve el complemento HTTPWatch en la ventana del explorador, Compruebe la versión del explorador haciendo clic en **ayuda** \> **o, en**versiones posteriores de Internet Explorer, haga clic en el símbolo de engranaje y **sobre Internet Explorer**. Para iniciar la barra de **comandos** , haga clic con el botón secundario en la barra de menús de Internet Explorer y haga clic en **barra de comandos**.

En el pasado, HTTPWatch se ha asociado a los comandos y las barras del explorador, por lo que, si no ve inmediatamente el icono (incluso después del reinicio), las **herramientas**de comprobación y las barras de herramientas del icono. Recuerde que las barras de herramientas se pueden personalizar y se pueden agregar opciones a ellas.

![Barra de herramientas de comandos de Internet Explorer con el icono HTTPWatch mostrado.](media/198590b0-d7b1-4bff-a6ad-e4ec3a1e83df.png)
  
1. Inicie HTTPWatch en una ventana del explorador de Internet Explorer. Aparecerá acoplada al explorador en la parte inferior de la ventana. Haga clic en **grabar**.

2. Reproduzca los pasos exactos implicados en el problema de rendimiento. Haga clic en el botón **detener** en HTTPWatch.

3. **Guarde** el HTTPWatch o **envíe por correo electrónico**. Recuerde que debe asignar un nombre al archivo para que incluya información de fecha y hora, así como una indicación de si su reloj contiene una demostración del rendimiento correcto o incorrecto.

![HTTPWatch que muestra la ficha de red para una carga de página de la página de inicio de Office 365.](media/021a2c64-d581-49fd-adf4-4c364f589d75.PNG)

Esta captura de pantalla es de la versión profesional de HTTPWatch. Puede abrir los seguimientos realizados en la versión básica en un equipo con una versión profesional y leerlo allí. Puede que haya información adicional disponible en el seguimiento a través de ese método.

## <a name="problem-steps-recorder"></a>Grabación de acciones de problemas

Grabación de acciones de usuario, o PSR. exe, permite registrar los problemas que se produzcan. Es una herramienta muy útil y muy sencilla de ejecutar.
  
### <a name="run-problem-steps-recorder-psrexe-to-record-your-work"></a>Ejecutar la grabadora de acciones de problemas (PSR. exe) para registrar el trabajo
  
1. Use **Start** \> **Run** \> Type **PSR. exe** \> **OK**, o bien, haga clic en la **tecla** \> de Windows **PSR. exe** \> y, a continuación, presione Entrar.

2. Cuando aparezca la ventana pequeña PSR. exe, haga clic en **iniciar grabación** y reproduzca los pasos que reproducen el problema de rendimiento. Puede agregar comentarios si es necesario; para ello, haga clic en **Agregar comentarios**.

3. Haga clic en **Detener grabación** cuando haya completado los pasos. Si el problema de rendimiento es representación de una página, espere a que la página se represente antes de detener la grabación.

4. Haga clic en **Guardar**.

![Captura de pantalla de los grabadores de acciones o PSR. exe.](media/8542b0aa-a3ff-4718-8dc4-43f5521c6c34.PNG)
  
La fecha y la hora se registran para usted. Esto vincula los VECPRD a la traza de Netmon y HTTPWatch en el tiempo, y ayuda a solucionar problemas de precisión. La fecha y la hora del registro de PSR pueden mostrar un minuto pasado entre el inicio de sesión y la exploración de la dirección URL y la representación parcial del sitio de administración, por ejemplo.
  
## <a name="read-your-traces"></a>Leer los seguimientos

No es posible enseñar todo lo relacionado con la solución de problemas de red y rendimiento que alguien necesita saber a través de un artículo. La obtención de un rendimiento óptimo tiene experiencia y el conocimiento de cómo funciona la red y suele llevarse a cabo. Pero es posible redondear hacia arriba una lista de los problemas principales y mostrar cómo las herramientas pueden facilitarle la tarea de eliminar los problemas más comunes.
  
Si desea obtener conocimientos sobre los seguimientos de red para los sitios de Office 365, no hay ningún profesor mejor que crear los seguimientos de las cargas de páginas periódicamente y obtener experiencia para leerlas. Por ejemplo, si tiene alguna oportunidad, cargue un servicio de Office 365 y trace el proceso. Filtre la traza para el tráfico DNS o busque en el FrameData el nombre del servicio que ha explorado. Analice el seguimiento para hacerse una idea de los pasos que se producen cuando se carga el servicio. Esto le ayudará a saber qué aspecto tiene la carga de página normal y, en el caso de la solución de problemas, en concreto sobre el rendimiento, la comparación de un buen con un seguimiento malo puede enseñarle mucho.
  
Netmon usa Microsoft IntelliSense en el campo de filtro de presentación. IntelliSense, o la finalización de código inteligente, es el truco en el que se escribe en un período y todas las opciones disponibles se muestran en un cuadro de selección desplegable. Si, por ejemplo, está preocupado por el ajuste de escala de la ventana TCP, puede encontrar la forma de hacerlo con `.protocol.tcp.window < 100`un filtro (como) por este medio.
  
![Captura de pantalla de Netmon que muestra que el campo Mostrar filtro usa IntelliSense.](media/75a56c11-9a60-47ee-a100-aabdfb1ba10f.PNG)
  
Los seguimientos de Netmon pueden tener una gran cantidad de tráfico en ellos. Si no tiene experiencia de lectura, es probable que se desbordará al abrir el seguimiento la primera vez. Lo primero que debe hacer es separar la señal del ruido de fondo en el seguimiento. Ha probado con Office 365, que es el tráfico que desea ver. Si se usa para desplazarse por las trazas, es posible que no necesite esta lista.
  
El tráfico entre el cliente y Office 365 viaja a través de TLS, lo que significa que el cuerpo del tráfico se cifrará y no se podrá leer en un seguimiento genérico de Netmon. El análisis de rendimiento no necesita conocer los detalles de la información del paquete. Sin embargo, está muy interesado en los encabezados de los paquetes y en la información que contienen.
  
### <a name="tips-to-get-a-good-trace"></a>Sugerencias para obtener una buena traza
  
- Conocer el valor de la dirección IPv4 o IPv6 del equipo cliente. Para obtener esto desde el símbolo del sistema, escriba **ipconfig** y, a continuación, presione Entrar. Conocer esta dirección le permitirá saber de un vistazo si el tráfico de la traza está directamente implicado en el equipo cliente. Si hay un proxy conocido, haga ping y obtenga también su dirección IP.

- Vacíe la caché de resolución de DNS y, si es posible, cierre todos los exploradores excepto el en el que esté ejecutando las pruebas. Si no puede hacerlo, por ejemplo, si la compatibilidad usa alguna herramienta basada en el explorador para ver el escritorio del equipo cliente, esté preparado para filtrar el seguimiento.

- En un seguimiento de ocupado, busque el servicio de Office 365 que está usando. Si no ha visto nunca o rara vez el tráfico, este es un paso útil para separar el problema de rendimiento de otros ruidos en la red. Hay varias formas de hacerlo. Justo antes de la prueba, puede usar _ping_ o _PsPing_ en la dirección URL del servicio específico (`ping outlook.office365.com` o `psping -4 microsoft-my.sharepoint.com:443`, por ejemplo,). También puede encontrar fácilmente un ping o PsPing en un seguimiento de Netmon (por su nombre de proceso). Esto le dará un punto para empezar a buscar.

Si solo usa el seguimiento de Netmon en el momento del problema, eso también es correcto. Para orientarse, use un filtro como `ContainsBin(FrameData, ASCII, "office")` o `ContainsBin(FrameData, ASCII, "outlook")`. Puede grabar el número de marco desde el archivo de seguimiento. Es posible que también desee desplazar el panel de _Resumen de tramas_ a la derecha y buscar la columna de identificador de conversación. Hay un número que se indica allí para el identificador de esta conversación específica que también puede grabar y mirar en aislamiento más adelante. Recuerde quitar este filtro antes de aplicar cualquier otro filtrado.

> [!TIP]
> Netmon tiene muchos filtros integrados útiles. Pruebe el botón **cargar filtro** en la parte superior del panel de filtros para _Mostrar_ .
  
![Busque su IP mediante PSPing en la línea de comandos del equipo cliente.](media/4c43ac67-e28e-4536-842d-7add7aa28847.PNG)
  
![Seguimiento de Netmon desde el cliente que muestra el mismo comando PSPing a través del TCP del filtro. Flags. SYN = = 1.](media/0ae7ef7d-e003-4d01-a006-dc49bd1fcef2.PNG)
  
Familiarizarse con el tráfico y aprender a localizar la información que necesita. Por ejemplo, aprenda a determinar qué paquete de la traza tiene la primera referencia al servicio de Office 365 que está usando (como "Outlook").

Realizar Office 365 Outlook online como ejemplo, el tráfico comienza de la siguiente manera:
  
- Consulta estándar de DNS y respuesta DNS para outlook.office365.com con QueryIDs coincidentes. Es importante tener en cuenta el desplazamiento de tiempo de esta solución, así como el lugar del mundo en el que el DNS global de Office 365 envía la solicitud de resolución de nombres. Idealmente, en la medida de lo posible, en lugar de una mitad de camino en todo el mundo.

- Una solicitud GET HTTP cuyo informe de estado se movió permanentemente (301)

- Tráfico RWS, incluidas las solicitudes de conexión RWS y las respuestas de conexión. (Este es el Winsock remoto que realiza una conexión).

- Una conversación TCP SYN y TCP SYN/ACK. Muchas de las opciones de configuración de esta conversación afectan al rendimiento.

- A continuación, una serie de tráfico TLS: TLS, que es donde tienen lugar el protocolo de enlace TLS y las conversaciones del certificado TLS. Recuerde que los datos se cifran a través de SSL/TLS.

Todas las partes del tráfico son importantes y conectadas, pero las pequeñas partes de la traza contienen información especialmente importante en términos de solución de problemas de rendimiento, por lo que nos centraremos en esas áreas. Además, dado que hemos realizado suficiente solución de problemas de rendimiento de Office 365 en Microsoft para compilar una lista de los diez principales problemas comunes, nos centraremos en esos problemas y en cómo usar las herramientas que debemos incluir en la raíz siguiente.
  
Si no los ha instalado, la matriz siguiente hace uso de varias herramientas. Siempre que sea posible. Se proporcionan vínculos a los puntos de instalación. La lista incluye herramientas de seguimiento de red comunes como [Netmon](https://www.microsoft.com/download/details.aspx?id=4865) y [Wireshark](https://www.wireshark.org/), pero use cualquier herramienta de seguimiento con la que esté familiarizado y en el que esté acostumbrado a filtrar el tráfico de red. Al realizar las pruebas, recuerde:
  
- *Cierre los exploradores y pruebe con un solo explorador en ejecución* , lo que reducirá el tráfico general que se captura. Realiza un seguimiento menos ocupado.
- *Vacíe la caché de resolución DNS en el equipo cliente* : Esto le ofrecerá una tableta táctil limpia cuando empiece a realizar la captura, para obtener un seguimiento más nítido.

## <a name="common-issues"></a>Problemas comunes

Algunos problemas comunes que pueden surgir y cómo encontrarlos en el seguimiento de la red.

### <a name="tcp-windows-scaling"></a>Ajuste de escala de Windows TCP

Se encuentra en el SYN-SYN/ACK. Es posible que el hardware heredado o antiguo no aproveche el escalado de ventanas TCP.  Sin la configuración de escalado de Windows TCP adecuada, el búfer de 16 bits predeterminado en los encabezados TCP se rellenará en milisegundos.  El tráfico no puede continuar el envío hasta que el cliente recibe una confirmación de que se han recibido los datos originales, lo que provoca retrasos.

#### <a name="tools"></a>Herramientas

- Netmon
- Wireshark

#### <a name="what-to-look-for"></a>Qué buscar

Busque el tráfico SYN-SYN/ACK en el seguimiento de red.  En Netmon, use un filtro como `tcp.flags.syn == 1`. Este filtro es el mismo en Wireshark.  

![Filtrar en Netmon o Wireshark para paquetes SYN para ambas herramientas: TCP. Flags. SYN = = 1.](media/4b9a12a1-c915-43c8-ac2f-a679d0435a29.PNG)

Observe que para cada SYN hay un número de puerto de origen (SrcPort) que coincide en el puerto de destino (DstPort) de la confirmación relacionada (SYN/ACK).

Para ver el valor de escalado de ventanas que usa la conexión de red, expanda primero el SYN y, después, el SYN/ACK relacionado.  

![Gráfico que muestra cómo hacer coincidir SrcPort con DstPort en un seguimiento para obtener la diferencia de tiempo.](media/6a4ca573-0253-4fbd-93e8-92821ee1c351.png)  

### <a name="tcp-idle-time-settings"></a>Configuración de tiempo de inactividad de TCP

Históricamente, la mayoría de las redes perimetrales están configuradas para conexiones transitorias, lo que significa que las conexiones inactivas suelen finalizar. Las sesiones TCP inactivas pueden finalizar por los servidores proxy y los firewalls de más de 100 a 300 segundos. Esto es problemático para Outlook online porque crea y usa conexiones a largo plazo, independientemente de si están inactivas o no.  

Cuando las conexiones se terminan por medio de proxy o dispositivos de firewall, el cliente no se informa, y un intento de usar Outlook online significa que un equipo cliente probará, repetidamente, la conexión antes de crear una nueva. Es posible que vea bloqueos en el producto, mensajes o un rendimiento lento en la carga de páginas.

#### <a name="tools"></a>Herramientas

- Netmon
- Wireshark

#### <a name="what-to-look-for"></a>Qué buscar

En Netmon, mire en el campo de desplazamiento de tiempo para una acción de ida y vuelta. Un recorrido de ida y vuelta es el tiempo que transvierte entre el cliente que envía una solicitud al servidor y recibe una respuesta. Compruebe entre el cliente y el punto de salida (ex. Cliente:\> proxy) o el cliente a Office 365 (Client--\> Office 365). Puede ver esto en muchos tipos de paquetes.

Por ejemplo, el filtro de Netmon puede tener el aspecto `.Protocol.IPv4.Address == 10.102.14.112 AND .Protocol.IPv4.Address == 10.201.114.12`o, en Wireshark, `ip.addr == 10.102.14.112 &amp;&amp; ip.addr == 10.201.114.12`.  

> [!TIP]
> ¿No sabe si la dirección IP de su seguimiento pertenece a su servidor DNS? Intente buscarlo en la línea de comandos. Haga clic en **iniciar** \> **la ejecución** \> , escriba **cmd**, o presione la **tecla** \> Windows y escriba **cmd**. En el símbolo del sistema `nslookup <the IP address from the network trace>`, escriba. Para probar, use nslookup con la dirección IP de su equipo. > para ver una lista de los intervalos IP de Microsoft, consulte [Office 365 URL e intervalos de direcciones IP](https://technet.microsoft.com/library/hh373144.aspx).

Si hay un problema, espere que aparezcan desplazamientos de tiempo prolongados (en este caso, Outlook online), especialmente en TLS: paquetes TLS que muestran el paso de los datos de la aplicación (por ejemplo, en Netmon puede encontrar paquetes `.Protocol.TLS AND Description == "TLS:TLS Rec Layer-1 SSL Application Data"`de datos de aplicación a través de). Debería ver una progresión suave en el tiempo a lo largo de la sesión. Si ve retrasos prolongados al actualizar Outlook online, esto podría deberse a un alto grado de Resets que se enviaron.

### <a name="latencyround-trip-time"></a>Tiempo de latencia/tiempo de ida y vuelta

La latencia es una medida que puede cambiar mucho en función de muchas variables, como la actualización de dispositivos de caducidad, la adición de un gran número de usuarios a una red y el porcentaje de ancho de banda general consumido por otras tareas en una conexión de red.

Hay calculadoras de ancho de banda para Office 365 disponible en esta página de [planeación de red y ajuste del rendimiento para office 365](network-planning-and-performance.md) .  

¿Necesita medir la velocidad de la conexión o el ancho de banda de la conexión de su ISP? Prueba este sitio (o sitios como él): [sitio oficial de speedtest](https://www.speedtest.net/)y [Pingtest](https://www.pingtest.net/).

#### <a name="tools"></a>Herramientas

- Ping
- PsPing
- Netmon
- Wireshark

#### <a name="what-to-look-for"></a>Qué buscar

Para realizar un seguimiento de la latencia en un seguimiento, se beneficiará de haber registrado la dirección IP del equipo cliente y la dirección IP del servidor DNS en Office 365. Esto se realiza con el fin de facilitar el filtrado de seguimiento. Si se conecta a través de un proxy, necesitará la dirección IP del equipo cliente, la dirección IP del servidor proxy/salida y la dirección IP de DNS de Office 365 para facilitar el trabajo.  

Una solicitud de ping enviada a outlook.office365.com le dirá el nombre del centro de recursos que recibe la solicitud, *aunque ping no* pueda conectarse para enviar los paquetes ICMP consecutivos de marca comercial. Si usa PsPing (una herramienta gratuita para la descarga) y específica el puerto (443) y quizás para usar IPv4 (-4), obtendrá un tiempo medio de ida y vuelta para los paquetes enviados. Esto funcionará para otras direcciones URL en los servicios de Office 365, `psping -4 yourSite.sharepoint.com:443`como. De hecho, puede especificar un número de pings para obtener un ejemplo más amplio para su promedio, pruebe algo como `psping -4 -n 20 yourSite-my.sharepoint.com:443`.  

> [!NOTE]
> PsPing no envía paquetes ICMP. Hace ping con los paquetes TCP a través de un puerto específico, por lo que puede usar uno que sepa que está abierto. En Office 365, que usa SSL/TLS, intente conectar el puerto: 443 a la PsPing.

![Captura de pantalla que muestra un ping que resuelve outlook.office365.com y un PSPing con 443 haciendo lo mismo, pero también informa de un RTT MS media de 6,5.](media/c64339f2-2c96-45b8-b168-c2a060430266.PNG)

Si cargó la página de Office 365 con lentitud al realizar un seguimiento de red, debe filtrar un seguimiento de Netmon o `DNS`Wireshark para. Esta es una de las IP que estamos buscando.  

Estos son los pasos que se deben seguir para filtrar Netmon para obtener la dirección IP (y echar un vistazo a la latencia de DNS). En este ejemplo se usa outlook.office365.com, pero también se puede usar la dirección URL de un inquilino de SharePoint Online (hithere.sharepoint.com por ejemplo).  

1. Haga ping a `ping outlook.office365.com` la dirección URL y, en los resultados, anote el nombre y la dirección IP del servidor DNS al que se envió la solicitud de ping.
2. Trace en la red abriendo la página o realizando la acción que le da el problema de rendimiento, o bien, si ve una latencia alta en el ping, realice un seguimiento de la red.
3. Abra la traza en Netmon y filtre por DNS (este filtro también funciona en Wireshark, pero es sensible a mayúsculas y minúsculas `-- dns`). Como conoce el nombre del servidor DNS de su ping, también puede filtrar con mayor rapidez en Netmon de la manera siguiente `DNS AND ContainsBin(FrameData, ASCII, "namnorthwest")`:, que tiene este aspecto en DNS de Wireshark y frame contiene "namnorthwest".<br/>Abra el paquete de respuesta y, en la ventana **detalles del marco** Netmon, haga clic en **DNS** para expandir para obtener más información. En la información de DNS, encontrará la dirección IP del servidor DNS al que se redirigió la solicitud en Office 365. Necesitará esta dirección IP para el paso siguiente (la herramienta PsPing). Quite el filtro, haga clic con el botón secundario en la respuesta DNS en Netmon (**Frame Summary** \> **Find Conversations** \> **DNS**) para ver la consulta y la respuesta DNS en paralelo.
4. En Netmon, tenga en cuenta también la columna de desplazamiento de tiempo entre la solicitud de DNS y la respuesta. En el paso siguiente, la herramienta [PsPing](https://technet.microsoft.com/sysinternals/jj729731.aspx) fácil de instalar y usar es muy útil, porque ICMP suele bloquearse en los firewalls y porque PsPing rastrea de forma elegante la latencia en milisegundos. PsPing completa una conexión TCP con una dirección y un puerto (en nuestro caso, Open Port 443).
5. Instale PsPing.
6. Abra un símbolo del sistema ( \> inicie \> el tipo de ejecución CMD o \> el tipo de clave de Windows cmd) y cambie el directorio al directorio en el que ha instalado psping para ejecutar el comando psping. En mis ejemplos, puede ver que he creado una carpeta "Perf" en la raíz de C. Puede hacer lo mismo para tener acceso rápido.
7. Escriba el comando para crear PsPing con la dirección IP del servidor DNS de Office 365 desde la traza anterior de Netmon, incluido el número de puerto, como `psping -n 20 132.245.24.82:445`. Esto le proporcionará un muestreo de 20 pings y el promedio de latencia cuando se detiene PsPing.

Si va a Office 365 a través de un servidor proxy, los pasos son un poco diferentes. Primero puede usar PsPing en el servidor proxy para obtener un valor de latencia media en milisegundos a proxy/salida y hacia atrás y, a continuación, ejecutar PsPing en el proxy o en un equipo con una conexión directa a Internet para obtener el valor que falta (de uno a Office 365 y posterior).  

Si elige ejecutar PsPing desde el proxy, tendrá dos valores de milisegundos: el equipo cliente al servidor proxy o el punto de salida y el servidor proxy a Office 365. Y ya habrá terminado. Pues bien, registre valores de todas formas.  

Si ejecuta PsPing en otro equipo cliente que tiene una conexión directa a Internet, es decir, tendrá dos valores de milisegundos: el equipo cliente al servidor proxy o el punto de salida, y el equipo cliente a Office 365. En este caso, reste el valor del equipo cliente al servidor proxy o del punto de salida del valor del equipo cliente a Office 365, y tendrá los números de RTT desde el equipo cliente al servidor proxy o el punto de salida, y desde el servidor proxy o el punto de salida a Offi CE 365.

Sin embargo, si puede encontrar un equipo cliente en la ubicación afectada que esté directamente conectada, o si omite el proxy, puede elegir ver si el problema reproduce allí para empezar y probar su uso posterior.

Latencia, como se ve en un seguimiento de Netmon, esos milisegundos adicionales pueden sumarse si hay suficientes en una sesión determinada.  

![Latencia general de Netmon, con la columna de diferencia de tiempo predeterminada de Netmon agregada al Resumen de marco.](media/7ad17380-8527-4bc2-9b9b-6310cf19ba6b.PNG)

> [!NOTE]
> Es posible que la dirección IP sea diferente a la que se muestra aquí; por ejemplo, la ping puede devolver algo más similar a 157.56.0.0/16 o un intervalo similar. Para obtener una lista de los rangos usados por Office 365, consulte [office 365 URL e intervalos de direcciones IP](https://technet.microsoft.com/library/hh373144.aspx).

Recuerde expandir todos los nodos (hay un botón en la parte superior para esto) Si desea buscar, por ejemplo, 132,245.

### <a name="proxy-authentication"></a>Autenticación de proxy

Esto solo se aplica a usted si va a través de un servidor proxy. Si no es así, puede omitir estos pasos. Cuando funciona correctamente, la autenticación de proxy se debe realizar en milisegundos, de forma coherente. No debe ver intermitentemente un rendimiento defectuoso durante los períodos de uso máximo (por ejemplo).  

Si la autenticación de proxy está activada, cada vez que realice una nueva conexión TCP a Office 365 para obtener información, deberá pasar por un proceso de autenticación en segundo plano. Así que, por ejemplo, al cambiar de calendario a correo en Outlook online, se autenticará. Y en SharePoint Online, si una página muestra medios o datos de varios sitios o ubicaciones, se autenticará por cada conexión TCP necesaria para representar los datos.  

En Outlook online, es posible que experimente tiempos de carga lentos cada vez que cambie entre el calendario y el buzón o que la carga de páginas sea lenta en SharePoint Online. Sin embargo, hay otros síntomas que no aparecen aquí.

La autenticación de proxy es una configuración en el servidor proxy de salida. Si está causando un problema de rendimiento con Office 365, debe consultar a su equipo de red.  

#### <a name="tools"></a>Herramientas

- Netmon
- Wireshark

#### <a name="what-to-look-for"></a>Qué buscar

La autenticación de proxy tiene lugar siempre que se debe subir una nueva sesión de TCP, normalmente solicitar archivos o información del servidor, o proporcionar información. Por ejemplo, puede ver la autenticación proxy en torno a las solicitudes HTTP GET o HTTP POST. Si desea ver los marcos en los que va a autenticar las solicitudes en el seguimiento, agregue la columna "Resumen de NTLMSSP" a Netmon y `.property.NTLMSSPSummary`filtre por. Para ver el tiempo que toma la autenticación, agregue la columna Delta de tiempo.

Para agregar una columna a Netmon:

1. Haga clic con el botón secundario en una columna como **Descripción**.
2. Haga clic en **elegir columnas**.
3. Busque _Resumen de NTLMSSP_ y _Delta de tiempo_ en la lista y haga clic en **Agregar**.
4. Mueva las nuevas columnas a su posición antes o detrás de la columna de _Descripción_ para que pueda leerlas en paralelo.
5. Haga clic en **Aceptar**.

Incluso si no agrega la columna, el filtro Netmon funcionará. Pero su solución de problemas será mucho más fácil si puede ver en qué fase de autenticación se encuentra.

Al buscar instancias de autenticación proxy, asegúrese de estudiar todas las tramas en las que haya un desafío NTLM o de que haya un mensaje de autenticación presente. Si es necesario, haga clic con el botón secundario en la parte específica \> del tráfico y busque las conversaciones TCP. Tenga en cuenta los valores de incremento de tiempo de estas conversaciones.

![Seguimiento de Netmon que muestra la autenticación de proxy, filtrada por conversación.](media/b640f176-0a52-4bbb-972e-60fb3d6aece2.PNG)

Un retraso de cuatro segundos en la autenticación de proxy tal y como aparece en Wireshark. La **diferencia de tiempo de la columna de marco mostrada anteriormente** se realizó haciendo clic con el botón secundario en el campo del mismo nombre en los detalles del marco y seleccionando Agregar como columna.  <br/> ![En Wireshark, se puede hacer clic con el botón secundario del mouse en el campo del mismo nombre en los detalles del marco y seleccionar agregar como columna para realizar la "diferencia de tiempo desde el marco mostrado anteriormente".](media/f5b7bde4-8067-4ee0-bc7f-e9062ce1ba6f.PNG)

### <a name="dns-performance"></a>Rendimiento de DNS

La resolución de nombres funciona mejor y más rápidamente cuando tiene una posición tan cercana al país del cliente como sea posible.

Si la resolución de nombres DNS tiene lugar internacional, puede Agregar segundos a la carga de páginas. Idealmente, la resolución de nombres tiene lugar en menos de 100 ms. Si no es así, debe seguir investigando.

> [!TIP]
> ¿No está seguro de cómo funciona la conectividad de cliente en Office 365? Eche un vistazo [al documento de](https://technet.microsoft.com/library/dn741250.aspx)referencia de conectividad de clientes.

#### <a name="tools"></a>Herramientas

- Netmon
- Wireshark
- PsPing

#### <a name="what-to-look-for"></a>Qué buscar

El análisis del rendimiento de DNS suele ser otro trabajo para realizar un seguimiento de la red. Sin embargo, PsPing también resulta útil para dar una causa o una posible causa.

El tráfico DNS se basa en las solicitudes y respuestas de TCP y UDP que se marcan claramente con un identificador que le ayudará a hacer coincidir una solicitud específica con su respuesta específica. Verá el tráfico de DNS cuando, por ejemplo, SharePoint Online usa un nombre de red o una dirección URL en una página web. Como regla general, la mayor parte de este tráfico, excepto cuando se transfieren zonas, se ejecuta sobre UDP.

En Netmon y Wireshark, el filtro más básico que le permitirá ver el tráfico de DNS es sencillamente `dns`. Asegúrese de usar minúsculas al especificar el filtro. Recuerde vaciar la memoria caché de resolución DNS antes de empezar a reproducir el problema en el equipo cliente. Por ejemplo, si tiene una carga de página de SharePoint Online lenta para la Página principal, debe cerrar todos los exploradores, abrir un nuevo explorador, iniciar el seguimiento, vaciar la memoria caché de resolución de DNS y buscar el sitio de SharePoint Online. Una vez que se resuelva la página completa, debe detener y guardar el seguimiento.

![Un filtro básico para DNS en Netmon es DNS.](media/1bebc118-ca13-45f3-803f-ab73e7af401d.png)

Desea ver el desplazamiento de tiempo aquí. Puede que le resulte útil agregar la columna **Delta de tiempo** a Netmon, que puede hacer completando estos pasos:

1. Haga clic con el botón secundario en una columna como **Descripción**.
2. Haga clic en **elegir columnas**.
3. Busque la _diferencia de tiempo_ en la lista y haga clic en **Agregar**.
4. Mueva la columna nueva a su posición antes o detrás de la columna de _Descripción_ para que pueda leerlas en paralelo.
5. Haga clic en **Aceptar**.

Si encuentra una consulta de interés, considere la posibilidad de aislarla haciendo clic con el botón secundario en la consulta en el panel de detalles del marco y seleccionando **Buscar conversaciones** \> **DNS**. Observe que el panel conversaciones de red pasa directamente a la conversación específica en su registro de tráfico UDP.

![Un seguimiento de Netmon de la carga de Outlook online filtrada por DNS y el uso de buscar conversaciones y, a continuación, DNS para acotar los resultados.](media/763cf20e-7b48-4a37-9449-c9978cfe118b.PNG)

En Wireshark, puede crear una columna para la hora de DNS. Realice el seguimiento (o abra un seguimiento) en Wireshark y filtre por `dns`o, más útil, `dns.time`. Haga clic en cualquier consulta DNS y, en el panel que muestra los detalles, `Domain Name System (response)` expanda los detalles. Verá un campo por hora (por ejemplo, `[Time: 0.001111100 seconds]`. Haga clic con el botón secundario en esta hora y seleccione **aplicar como columna**. Esto le proporcionará una columna de **tiempo** para ordenar la traza de forma más rápida. Haga clic en la nueva columna para ordenar por valores descendentes para ver qué llamada DNS tardó más tiempo en resolverse.

[Una exploración de SharePoint Online filtrada en Wireshark por dns.time (minúscula), con el tiempo de los detalles convertido en columna y ordenado de forma ascendente.](media/1439dcc2-12ff-4ee2-9ef3-1484cf79c384.PNG)

Si desea realizar más investigaciones sobre el tiempo de resolución DNS, pruebe con PsPing el puerto DNS que usa TCP (por ejemplo, `psping <IP address of DNS server>:53`). ¿Sigue viendo un problema de rendimiento? Si lo hace, es más probable que el problema sea un problema de red más amplio que un problema de la aplicación DNS específica que está presionando para llevar a cabo la solución. También merece la pena mencionar, de nuevo, que un ping a outlook.office365.com le dirá dónde se está llevando a cabo la resolución de nombres DNS para Outlook online (por ejemplo, outlook-namnorthwest.office365.com).

Si el problema parece ser específico de DNS, puede que sea necesario ponerse en contacto con el Departamento de TI para ver las configuraciones de DNS y los reenviadores de DNS y así poder investigar este problema.

### <a name="proxy-scalability"></a>Escalabilidad de proxy

Los servicios como Outlook online en Office 365 conceden a los clientes varias conexiones a largo plazo. Por lo tanto, cada usuario puede usar más conexiones que requieran una mayor duración.  

#### <a name="tools"></a>Herramientas

Matemáticas  

#### <a name="what-to-look-for"></a>Qué buscar

No hay ninguna herramienta de seguimiento de red o de solución de problemas específica para esto. En su lugar, se basa en los cálculos de ancho de banda dados limitaciones y otras variables.  

### <a name="tcp-max-segment-size"></a>Tamaño de segmento máximo de TCP

Se encuentra en el SYN-SYN/ACK.  Realice esta comprobación en cualquier seguimiento de red de rendimiento que haya tomado para asegurarse de que los paquetes TCP están configurados para conllevar la máxima cantidad de datos posible.

El objetivo es ver un MSS de 1460 bytes para la transmisión de datos. Si está detrás de un proxy o está usando un NAT, recuerde ejecutar esta prueba del cliente a proxy/salida/NAT, y de proxy/salida/NAT a Office 365 para obtener mejores resultados. Se trata de sesiones TCP diferentes.

#### <a name="tools"></a>Herramientas

Netmon

#### <a name="what-to-look-for"></a>Qué buscar

El tamaño de segmento máximo de TCP (MSS) es otro parámetro del Protocolo de enlace de tres vías en el seguimiento de red, lo que significa que encontrará los datos que necesita en el paquete SYN-SYN/ACK. En realidad, MSS es muy fácil de ver.

Abra cualquier seguimiento de red de rendimiento que tenga y busque la conexión de la que siente curiosidad o que muestra el problema de rendimiento.

> [!NOTE]
> Si va a realizar un seguimiento y necesita encontrar el tráfico relevante para la conversación, filtre por la IP del cliente o la IP del servidor proxy o el punto de salida, o ambos. Ir directamente, tendrá que hacer ping a la dirección URL que está probando para la dirección IP de Office 365 en el seguimiento y filtrarla por ella.

¿Mira la segunda mano de seguimiento? Intente usar filtros para orientarse a sí mismo. En Netmon, ejecute una búsqueda basada en la dirección URL, como `Containsbin(framedata, ascii, "sphybridExample")`, tome nota del número de la trama.

En Wireshark, use algo `frame contains "sphybridExample"`como. Si observa que ha encontrado tráfico remoto de Winsock (RWS) (puede aparecer como un [PSH, ACK] en Wireshark), recuerde que las conexiones RWS se pueden ver en breve antes de los SYN-SYN/ACK relevantes, tal como se explicó anteriormente.

En este punto, puede grabar el número de la trama, quitar el filtro, hacer clic en **todo el tráfico** en la ventana de conversaciones de red en Netmon para ver el SYN más cercano.

Importantemente, si no ha recibido ninguna información de dirección IP en el momento de la traza, al buscar la dirección URL en la traza (parte `sphybridExample-my.sharepoint.com`de, por ejemplo), obtendrá direcciones IP para filtrar por.

Busque la conexión en la traza que le interesa ver. Puede hacer esto examinando la traza, filtrando por direcciones IP o seleccionando identificadores de conversación específicos mediante la ventana de conversaciones de red en Netmon. Una vez que haya encontrado el paquete SYN, expanda TCP (en Netmon) o protocolo de control de transmisión (en Wireshark) en el panel Detalles de trama. Expanda opciones de TCP y MaxSegmentSize. Busque la trama SYN-ACK relacionada y expanda opciones de TCP y MaxSegmentSize. El menor de los dos valores será el tamaño máximo de segmento. En esta imagen, uso la columna integrada en Netmon denominado TCP Troubleshooting.  

![Seguimiento de red filtrado en Netmon con las columnas integradas.](media/e073df13-71f8-497a-83b4-bb9f70bd9833.PNG)

La columna integrada se encuentra en la parte superior del panel **detalles de marco** . (Para volver a la vista normal, vuelva a hacer clic en **columnas** y, a continuación, elija **zona horaria**.)

![Dónde encontrar la lista de columnas desplegable para la opción de Solucionar problemas de TCP (arriba del Resumen de marco).](media/64fd4baa-a872-4f07-b959-752d7d37fd62.PNG)

Este es un seguimiento filtrado en Wireshark. Hay un filtro específico para el valor de MSS ( `tcp.options.mss`). Los marcos de un protocolo de enlace de confirmación SYN, SYN/ACK están vinculados en la parte inferior del objeto Wireshark equivalente a los detalles del marco (de modo que Frame 47 ACK, vínculos a 46 SYN/ACK, vínculos a 43 SYN) para facilitar este tipo de trabajo.

![Seguimiento filtrado en Wireshark por TCP. Options. MSS para el tamaño máximo del segmento (MSS).](media/51e278db-801b-48bc-9b68-87cf92f03fd6.PNG)

Si necesita comprobar la **confirmación selectiva** (tema siguiente de esta matriz), no cierre la traza.

### <a name="selective-acknowledgment"></a>Confirmación selectiva

Se encuentra en el SYN-SYN/ACK. Debe indicarse como permitido tanto en SYN como en SYN/ACK. La confirmación selectiva (SACK) permite una retransmisión de datos más fluida cuando falta un paquete o paquetes. Los dispositivos pueden deshabilitar esta característica, lo que puede dar lugar a problemas de rendimiento.

Si está detrás de un proxy o está usando un NAT, recuerde ejecutar esta prueba del cliente a proxy/salida/NAT, y de proxy/salida/NAT a Office 365 para obtener mejores resultados. Se trata de sesiones TCP diferentes.

#### <a name="tools"></a>Herramientas

Netmon

#### <a name="what-to-look-for"></a>Qué buscar

La confirmación selectiva (SACK) es otro parámetro en el protocolo de enlace SYN-SYN/ACK. Puede filtrar la traza para SYN-SYN/ACK de muchas formas.

Busque la conexión en la traza que le interesa ver mediante la exploración de la traza, el filtrado por direcciones IP o haciendo clic en un identificador de conversación mediante la ventana de conversaciones de red de Netmon. Una vez que haya encontrado el paquete SYN, expanda TCP en Netmon o Transmission Control Protocol in Wireshark en la sección detalles de trama. Expanda opciones de TCP y SACK. Busque la trama SYN-ACK relacionada y expanda opciones de TCP y su campo SACK. Asegúrese de que se permite cierto SACK en SYN y SYN/ACK. Estos son los valores de SACK tal y como se muestran en Netmon y Wireshark.

![Confirmación selectiva (SACK) en Netmon como resultado de TCP. Flags. SYN = = 1.](media/216f556f-5031-4ed2-b066-a0d9b3251fa2.PNG)

![BOLSA tal y como aparece en Wireshark con el filtro tcp.flags.syn == 1.](media/0a6e26e5-43dc-403b-adc9-3349a55f4e4b.PNG)

### <a name="dns-geolocation"></a>Ubicación geográfica de DNS

El lugar de la oficina mundial 365 intenta resolver la llamada DNS afecta a la velocidad de conexión.

En Outlook online, una vez completada la primera búsqueda DNS, la ubicación de ese DNS se usará para conectarse al centro de recursos más cercano. Se conectará a un servidor CAS de Outlook online, que usará la red troncal para conectarse al centro de datos (dC) en el que se almacenan los datos. Esto es más rápido.

Cuando se tiene acceso a SharePoint Online, un usuario que viaja en el extranjero se dirige a su centro de datos activo, es decir, el dC cuya ubicación se basa en la base de inicio del inquilino de SPO (por lo tanto, un dC en los Estados Unidos si el usuario está basado en Estados Unidos).

Lync Online tiene nodos activos en más de un dC a la vez. Cuando se envían solicitudes para las instancias de Lync Online, el DNS de Microsoft determinará en qué parte del mundo procedía la solicitud y devolverá las direcciones IP del dC regional más cercano donde Lync Online está activo.

> [!TIP]
> ¿Necesita más información sobre cómo se conectan los clientes a Office 365? Eche un vistazo al artículo de referencia de [conectividad de cliente](https://technet.microsoft.com/library/dn741250.aspx) (y sus gráficos útiles).

#### <a name="tools"></a>Herramientas

- Ping
- PsPing

#### <a name="what-to-look-for"></a>Qué buscar

Las solicitudes de resolución de nombres de los servidores DNS del cliente a los servidores DNS de Microsoft deben, en la mayoría de los casos, dar lugar a que DNS de Microsoft devuelva la dirección IP de un centro de recursos regional (dC). ¿Qué significa esto para usted? Si su sede está en Bangalore, India, pero viaja en los Estados Unidos, cuando el explorador realiza una solicitud de Outlook online, los servidores DNS de Microsoft deben entregarle direcciones IP a los centros de seguridad de los Estados Unidos, un centro de seguridad regional. Si el correo es necesario desde Outlook, estos datos se transmiten a través de la red de red troncal de Microsoft entre los centros de datos.

El DNS funciona con mayor rapidez cuando se realiza la resolución de nombres lo más cerca posible de la ubicación del usuario. Si está en Europa, quiere ir a un DNS de Microsoft en Europa y (idealmente) tratar con un centro de recursos en Europa. El rendimiento de un cliente en Europa dirigido a DNS y a un centro de recursos en América será más lento.

Ejecute la herramienta ping en outlook.office365.com para determinar en qué lugar del mundo se enrutará su solicitud de DNS. Si está en Europa, debería ver una respuesta de algo parecido a outlook-emeawest.office365.com. En América, espere algo parecido a outlook-namnorthwest.office365.com.

Abra el símbolo del sistema en el equipo cliente (a \> través \> de Start Start cmd \> o el tipo de clave de Windows cmd). Escriba ping outlook.office365.com y presione Entrar. Recuerde que para especificar-4 Si desea especificar un ping a través de IPv4. Es posible que no pueda obtener una respuesta de los paquetes ICMP, pero debería ver el nombre del DNS al que se enrutó la solicitud. Si desea ver los números de latencia de esta conexión, pruebe PsPing a la dirección IP del servidor que se devuelve mediante ping.  

![Ping de outlook.office365.com que muestra la resolución en outlook-namnorthwest.](media/06c944d5-6159-43ec-aa31-757770695e8b.PNG)

![PSPing a la dirección IP devuelta por el comando ping a outlook.office365.com que muestra la latencia promedio de 28 milisegundos.](media/f2b25a75-1a87-4479-b8a7-fa4375683507.PNG)

### <a name="office-365-application-troubleshooting"></a>Solución de problemas de aplicaciones de Office 365

#### <a name="tools"></a>Herramientas

- Netmon
- HTTPWatch
- Consola F12 en el explorador

No se incluyen las herramientas usadas en la solución de problemas específicos de la aplicación en este artículo específico de la red. Pero encontrará recursos que *puede* usar [en esta página](https://support.office.com/article/Network-planning-and-performance-tuning-for-Office-365-e5f1228c-da3c-4654-bf16-d163daee8848).

## <a name="related-topics"></a>Temas relacionados

[Administrar puntos de conexión de Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Preguntas frecuentes sobre extremos de Office 365](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
