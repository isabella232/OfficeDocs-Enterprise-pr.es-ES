---
title: Administración de puntos de conexión de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/21/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 99cab9d4-ef59-4207-9f2b-3728eb46bf9a
description: Algunas redes empresariales restringen el acceso a ubicaciones de Internet genéricas o incluyen backhaul o procesamiento de tráfico de red substancial. Para garantizar que los equipos de redes como estos puedan tener acceso a Office 365, los administradores de red y de proxy deben administrar la lista de FQDN, direcciones URL y direcciones IP que componen la lista de puntos de conexión de Office 365. Estos deben agregarse a ruta directa, omisión de proxy o reglas de firewall y archivos PAC para garantizar que las solicitudes de red puedan alcanzar el alcance de Office 365.
ms.openlocfilehash: 1a694d516a81fec7d6c619c17414e2245dd6b0ef
ms.sourcegitcommit: 8027254ab4b9ed44a5b0c336f714049859f93f3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2019
ms.locfileid: "38030614"
---
# <a name="managing-office-365-endpoints"></a>Administración de puntos de conexión de Office 365

La mayoría de las organizaciones empresariales que tienen varias ubicaciones de oficina y una WAN que se conecta necesitarán tener la configuración de la conectividad de red de Office 365. Puede optimizar la red mediante el envío de todas las solicitudes de red de Office 365 de confianza directamente a través del firewall, evitando el procesamiento o la inspección adicionales del nivel de paquetes. Esto reduce la latencia y los requisitos de capacidad del perímetro. La identificación del tráfico de red de Office 365 es el primer paso para ofrecer un rendimiento óptimo para los usuarios. Para obtener más información acerca de la conectividad de red de Office 365, consulte [office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md).

Microsoft recomienda el acceso a los puntos de conexión de red de Office 365 y los cambios en ellos mediante el [servicio Web de direcciones IP y URL de office 365](office-365-ip-web-service.md).

Independientemente de cómo administre el tráfico de red vital de Office 365, Office 365 requiere conectividad a Internet. Otros extremos de red en los que se requiere conectividad se muestran en puntos de conexión [adicionales no incluidos en la dirección IP de Office 365 y el servicio Web de dirección URL](additional-office365-ip-addresses-and-urls.md).

La forma de usar los extremos de red de Office 365 dependerá de la arquitectura de red de la organización de la empresa. Este artículo describe varias maneras en las que se pueden integrar las arquitecturas de red empresarial con las direcciones IP y URL de Office 365. La forma más sencilla de elegir las solicitudes de red en las que confiar es usar dispositivos de SDWAN que admitan la configuración de Office 365 automatizada en cada una de las oficinas de la oficina.

## <a name="sdwan-for-local-branch-egress-of-vital-office-365-network-traffic"></a>SDWAN para la salida de bifurcaciones locales de tráfico de red vital de Office 365

En cada sucursal, puede proporcionar un dispositivo SDWAN configurado para enrutar el tráfico para Office 365 optimizar categoría de extremos, o bien optimizar y permitir categorías, directamente en la red de Microsoft. Otro tráfico de red, incluido el tráfico local del centro de recursos, el tráfico general de sitios web de Internet y el tráfico a Office 365 extremos de categoría predeterminada se envían a otra ubicación en la que se tiene un perímetro de red más importante.

Microsoft está trabajando con proveedores de SDWAN para habilitar la configuración automatizada. Para obtener más información, consulte [Office 365 Networking Partner Program](office-365-networking-partner-program.md).

<a name="pacfiles"> </a>
## <a name="use-a-pac-file-for-direct-routing-of-vital-office-365-traffic"></a>Usar un archivo PAC para el enrutamiento directo de tráfico vital de Office 365

Usar archivos PAC o WPAD para administrar solicitudes de red asociadas con Office 365 pero que no tienen una dirección IP. Las solicitudes de red típicas que se envían a través de un proxy o un dispositivo perimetral aumentan la latencia. Mientras que la interrupción de SSL y la inspección crean la latencia más grande, otros servicios como la autenticación de proxy y la búsqueda de reputación pueden provocar un bajo rendimiento y una experiencia de usuario deficiente. Además, estos dispositivos de red perimetral necesitan suficiente capacidad para procesar todas las solicitudes de conexión de red. Se recomienda omitir el proxy o los dispositivos de inspección para solicitudes de red directas de Office 365.
  
[PowerShell Gallery Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile) es un script de PowerShell que lee los puntos de conexión de red más recientes de la dirección IP de Office 365 y del servicio Web de dirección URL y crea un archivo PAC de ejemplo. Puede modificar el script para que se integre con la administración de archivos PAC existente.

![Conectarse a Office 365 a través de firewalls y servidores proxy.](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)

**Figura 1: perímetro de red empresarial simple**

El archivo PAC se implementa en los exploradores Web en el punto 1 de la figura 1. Cuando se usa un archivo PAC para salidas directas de tráfico de red vital de Office 365, también se debe permitir la conectividad a las direcciones IP que se encuentran detrás de estas URL en el firewall perimetral de red. Para ello, se obtienen las direcciones IP de las mismas categorías de punto de conexión de Office 365, tal como se especifica en el archivo PAC y se crean ACL de Firewall basadas en dichas direcciones. El servidor de seguridad es el punto 3 de la figura 1.

Por separado, si opta por solo el enrutamiento directo para los extremos de la categoría de optimización, los extremos de categoría de permiso necesarios que envíe al servidor proxy deben aparecer en el servidor proxy para omitir el procesamiento adicional. Por ejemplo, el salto de SSL e inspección y la autenticación de proxy son incompatibles con los extremos de la categoría optimizar y permitir. El servidor proxy es el punto 2 de la figura 1.

La configuración común es permitir sin procesar todo el tráfico saliente del servidor proxy para las direcciones IP de destino para el tráfico de red de Office 365 que alcanza el servidor proxy. Para obtener información acerca de los problemas de salto de SSL e inspeccionar, vea [usar dispositivos de red de terceros o soluciones en el tráfico de Office 365](https://support.microsoft.com/help/2690045/using-third-party-network-devices-or-solutions-with-office-365).

Hay dos tipos de archivos PAC que el script Get-PacFile generará.

|**Tipo**|**Descripción**|
|:-----|:-----|
|**1** <br/> |Enviar el tráfico de extremo optimizado directo y todo lo demás al servidor proxy. <br/> |
|**segundo** <br/> |Send: optimizar y permitir el tráfico de extremo directo y todo lo demás al servidor proxy. Este tipo también se puede usar para enviar todo el tráfico de ExpressRoute admitido para Office 365 a los segmentos de red de ExpressRoute y todo lo demás al servidor proxy. <br/> |

Este es un ejemplo sencillo de llamada al script de PowerShell:

```powershell
Get-PacFile -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

Hay varios parámetros que puede pasar a la secuencia de comandos:

|**Parámetro**|**Descripción**|
|:-----|:-----|
|**ClientRequestId** <br/> |Esto es obligatorio y es un GUID que se pasa al servicio Web que representa al equipo cliente que realiza la llamada. <br/> |
|**Instancia** <br/> |La instancia del servicio Office 365, que es el valor predeterminado de todo el mundo. También se pasa al servicio Web. <br/> |
|**TenantName** <br/> |El nombre del espacio empresarial de Office 365. Se pasa al servicio Web y se usa como un parámetro reemplazable en algunas direcciones URL de Office 365. <br/> |
|**Tipo** <br/> |El tipo de archivo PAC de proxy que desea generar. <br/> |

Este es otro ejemplo de cómo llamar al script de PowerShell con parámetros adicionales:

```powershell
Get-PacFile -Type 2 -Instance Worldwide -TenantName Contoso -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

## <a name="proxy-server-bypass-processing-of-office-365-network-traffic"></a>Omisión de procesamiento de tráfico de red de Office 365 en el servidor proxy

Cuando los archivos PAC no se usan para el tráfico saliente directo, sigue siendo conveniente omitir el procesamiento en el perímetro de la red mediante la configuración del servidor proxy. Algunos proveedores de servidores proxy han habilitado la configuración automatizada de esto tal como se describe en el [programa Office 365 Networking Partner](office-365-networking-partner-program.md).

Si está haciendo esto manualmente, tendrá que obtener los datos de categoría de extremo optimizar y permitir de la dirección IP y el servicio Web de Office 365 y configurar el servidor proxy para que omita el procesamiento de estos. Es importante evitar la interrupción de SSL e inspeccionar y autenticar proxy para los extremos de la categoría optimizar y permitir.
  
<a name="bkmk_changes"> </a>
## <a name="change-management-for-office-365-ip-addresses-and-urls"></a>Administración de cambios de direcciones IP y URL de Office 365

Además de seleccionar la configuración adecuada para el perímetro de la red, es fundamental que adopte un proceso de administración de cambios para los puntos de conexión de Office 365. Estos extremos cambian con regularidad y, si no administra los cambios, puede acabar con los usuarios bloqueados o con un bajo rendimiento después de agregar una dirección IP o dirección URL nueva.

Los cambios en las direcciones URL y direcciones IP de Office 365 suelen publicarse cerca del último día de cada mes. A veces, un cambio se publicará fuera de esa programación debido a los requisitos de funcionamiento, soporte técnico o seguridad.

Cuando se publica un cambio que requiere la acción de una dirección IP o dirección URL agregada, se espera recibir un aviso de 30 días desde el momento en que se publica el cambio hasta que haya un servicio de Office 365 en ese punto de conexión. Aunque nos interesa este período de notificación, es posible que no siempre sea posible a causa de los requisitos de funcionamiento, soporte técnico o seguridad. Los cambios que no requieren acciones inmediatas para mantener la conectividad, como direcciones IP o direcciones URL quitadas o cambios menos significativos, no incluyen notificación avanzada. Independientemente de la notificación que se proporcione, enumeramos la fecha activa del servicio previsto para cada cambio.

### <a name="change-notification-using-the-web-service"></a>Notificación de cambios mediante el servicio Web

Puede usar la dirección IP de Office 365 y el servicio Web de dirección URL para obtener la notificación de cambios. Le recomendamos que llame al método Web **/version** una vez por hora para comprobar la versión de los puntos de conexión que usa para conectarse a Office 365. Si esta versión cambia en comparación con la versión que se está usando, debe obtener los datos de extremo más recientes del método Web **/endpoints** y, de manera opcional, obtener las diferencias del método Web **/Changes** . No es necesario llamar a los métodos Web **/endpoints** o **/Changes** si no ha habido ningún cambio en la versión que ha encontrado.

Para obtener más información, consulte [Office 365 IP address and URL Web Service](office-365-ip-web-service.md).

### <a name="change-notification-using-rss-feeds"></a>Notificación de cambios mediante fuentes RSS

El servicio Web de dirección IP y URL de Office 365 proporciona una fuente RSS a la que puede suscribirse en Outlook. Hay vínculos a las direcciones URL de RSS en cada una de las páginas específicas de la instancia del servicio Office 365 para las direcciones IP y las direcciones URL. Para obtener más información, consulte [Office 365 IP address and URL Web Service](office-365-ip-web-service.md).

### <a name="change-notification-and-approval-review-using-microsoft-flow"></a>Revisión de notificaciones y aprobación de cambios con Microsoft Flow

Somos conscientes de que es posible que deba seguir requiriendo procesamiento manual para los cambios de punto de conexión de red que se realicen cada mes. Puede usar Microsoft Flow para crear un flujo que le notifique por correo electrónico y, de forma opcional, ejecuta un proceso de aprobación para los cambios cuando los puntos de conexión de red de Office 365 tienen cambios. Una vez completada la revisión, puede hacer que el flujo envíe por correo automáticamente los cambios en el equipo de administración del servidor proxy y del firewall.

Para obtener información sobre una plantilla y un ejemplo de Microsoft Flow, vea [usar Microsoft Flow para recibir un correo electrónico de cambios en las direcciones IP y URL de Office 365](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/td-p/240651).
  
<a name="FAQ"> </a>
## <a name="office-365-network-endpoints-faq"></a>Preguntas más frecuentes sobre puntos de conexión de red 365 de Office

Preguntas de administrador más frecuentes sobre la conectividad de Office 365:
  
### <a name="how-do-i-submit-a-question"></a>¿Cómo envío una pregunta?

Haga clic en el vínculo de la parte inferior para indicar si el artículo resultó útil o no y envíe otras preguntas. Supervisamos los comentarios y actualizamos las preguntas con los más frecuentes.
  
### <a name="how-do-i-determine-the-location-of-my-tenant"></a>¿Cómo se determina la ubicación de mi espacio empresarial?

 La **Ubicación del espacio empresarial** se determina mejor usando nuestro [mapa de centro de recursos](https://aka.ms/datamaps).
  
### <a name="am-i-peering-appropriately-with-microsoft"></a>¿Estoy emparejamiento adecuadamente con Microsoft?

 Las **ubicaciones de emparejamiento** se describen con más detalle en [emparejamiento con Microsoft](https://www.microsoft.com/peering).
  
Con más de 2500 relaciones de emparejamiento de ISP globalmente y 70 puntos de presencia, obtener desde su red a los nuestros deben estar sin problemas. No puede resultar perjudicial dedicar unos minutos asegurándose de que la relación de emparejamiento del ISP es la más óptima, a [continuación le presentamos algunos ejemplos](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__guidance/) de buenas y no tan buenas entregas de emparejamiento a nuestra red.
  
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a>Veo que las solicitudes de red a las direcciones IP no están en la lista publicada, ¿es necesario proporcionar acceso a las mismas?
<a name="bkmk_MissingIP"> </a>

Solo se proporcionan direcciones IP para los servidores de Office 365 a los que se debe dirigir directamente. Esta no es una lista completa de todas las direcciones IP para las que verá solicitudes de red. Verá solicitudes de red a las direcciones IP de Microsoft y de terceros, no publicadas. Estas direcciones IP se generan de forma dinámica o se administran de una manera que evita la notificación oportuna cuando cambian. Si el Firewall no puede permitir el acceso en función de los FQDN de estas solicitudes de red, use un archivo PAC o WPAD para administrar las solicitudes.
  
Vea una dirección IP asociada a Office 365 de la que desea obtener más información.
  
1. Compruebe si la dirección IP se incluye en un intervalo publicado mayor con una [calculadora CIDR](https://jodies.de/ipcalc).
2. Compruebe si un partner es propietario de la IP con una [consulta Whois](https://dnsquery.org/). Si es propietario de Microsoft, puede ser un asociado interno.
3. Compruebe el certificado, en un explorador Conéctese a la dirección IP *mediante\<https://\> IP_ADDRESS* , compruebe los dominios que aparecen en el certificado para comprender qué dominios están asociados con la dirección IP. Si es una dirección IP de propiedad de Microsoft y no se encuentra en la lista de direcciones IP de Office 365, es probable que la dirección IP esté asociada a una CDN de Microsoft como *MSOCDN.net* u otro dominio de Microsoft sin información de IP publicada. Si encuentra el dominio en el certificado es aquel en el que le indicamos que indique la dirección IP, infórmenos.

<a name="bkmk_cname"> </a>
### <a name="some-office-365-urls-point-to-cname-records-instead-of-a-records-in-the-dns-what-do-i-have-to-do-with-the-cname-records"></a>Algunas direcciones URL de Office 365 señalan a registros CNAME en lugar de a registros en el DNS. ¿Qué tengo que hacer con los registros CNAME?

Los equipos cliente necesitan un registro DNS A o AAAA que incluya una o varias direcciones IP para conectarse a un servicio en la nube. Algunas direcciones URL incluidas en Office 365 muestran registros CNAME en lugar de registros A o AAAA. Estos registros CNAME son intermediarios y es posible que haya varios en una cadena. Siempre se resolverán finalmente en un registro a o AAAA para una dirección IP. Por ejemplo, considere la siguiente serie de registros DNS, que, en última instancia, se resuelve en la dirección IP _IP_1_:

```
serviceA.office.com -> CNAME: serviceA.domainA.com -> CNAME: serviceA.domainB.com -> A: IP_1
```

Estas redirecciones de CNAME son una parte normal del DNS y son transparentes para el equipo cliente y transparentes para los servidores proxy. Se usan para equilibrio de carga, redes de entrega de contenido, alta disponibilidad y mitigación de incidentes de servicio. Microsoft no publica los registros CNAME intermediarios, están sujetos a cambios en cualquier momento y no es necesario configurarlos como permitidos en el servidor proxy.

Un servidor proxy valida la dirección URL inicial que en el ejemplo anterior es serviceA.office.com y esta dirección URL se incluiría en la publicación de Office 365. El servidor proxy solicita la resolución DNS de esa dirección URL a una dirección IP y recibirá una IP_1. No valida los registros del redireccionamiento CNAME del intermediario.

No se recomienda la configuración o la lista blanca codificada de forma rígida basada en FQDN indirectos de Office 365, que no es compatible con Microsoft, y se sabe que causa problemas de conectividad con los clientes. Las soluciones DNS que se bloquean en la redirección de CNAME o que, de lo contrario, resuelven incorrectamente las entradas DNS de Office 365, pueden resolverse mediante el reenvío condicional de DNS (en el ámbito de los FQDN de Office 365 de uso directo) con la recursión de DNS habilitada. Muchos productos perimetrales de red de terceros integran de forma nativa la lista blanca de puntos de conexión de Office 365 en su configuración mediante el [servicio Web de direcciones IP y URL de office 365](https://docs.microsoft.com/office365/enterprise/office-365-ip-web-service).

### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a>¿Por qué veo nombres como nsatc.net o akadns.net en los nombres de dominio de Microsoft?
<a name="bkmk_akamai"> </a>

Office 365 y otros servicios de Microsoft usan varios servicios de terceros, como Akamai y MarkMonitor, para mejorar la experiencia de Office 365. Para seguir dándole la mejor experiencia posible, podemos cambiar estos servicios en el futuro. Los dominios de terceros pueden hospedar contenido, como una red CDN, o pueden hospedar un servicio, como un servicio de administración de tráfico geográfico. Algunos de los servicios actualmente en uso incluyen:
  
[MarkMonitor](https://www.markmonitor.com/) está en uso cuando se ven solicitudes que incluyen * \*. nsatc.net* . Este servicio proporciona protección y supervisión de nombres de dominio para protegerse contra comportamientos malintencionados.
  
[ExactTarget](https://www.marketingcloud.com/) está en uso cuando se ven solicitudes a * \*. ExactTarget.com* . Este servicio proporciona supervisión y administración de vínculos de correo electrónico contra comportamientos malintencionados.
  
[Akamai](https://www.akamai.com/) está en uso cuando se ven solicitudes que incluyen uno de los siguientes FQDN. Este servicio ofrece servicios de red de entrega de contenido y de DNS geográfico.
  
```
*.akadns.net
*.akam.net
*.akamai.com
*.akamai.net
*.akamaiedge.net
*.akamaihd.net
*.akamaized.net
*.edgekey.net
*.edgesuite.net
```

### <a name="i-have-to-have-the-minimum-connectivity-possible-for-office-365"></a>Tengo que tener la conectividad mínima posible para Office 365
<a name="bkmk_thirdparty"> </a>

Como Office 365 es un conjunto de servicios creado para que funcione a través de Internet, las promesas de confiabilidad y disponibilidad se basan en muchos servicios estándar de Internet que están disponibles. Por ejemplo, los servicios estándar de Internet como DNS, CRL y CDN deben ser accesibles para usar Office 365 de la misma manera que deben ser accesibles para usar los servicios de Internet más modernos.

El conjunto de aplicaciones de Office 365 se desglosa en las principales áreas de servicio. Estos pueden habilitarse selectivamente para la conectividad y hay un área común que es una dependencia para todos y siempre es necesario.

|**Área de servicio**|**Descripción**|
|:-----|:-----|
|**Exchange** <br/> |Exchange Online y Exchange Online Protection <br/> |
|**SharePoint** <br/> |SharePoint Online y OneDrive para la Empresa <br/> |
|**Skype Empresarial Online y Microsoft Teams** <br/> |Skype empresarial y Microsoft Teams <br/> |
|**Común** <br/> |Office 365 Pro Plus, Office en un explorador, Azure AD y otros extremos de red comunes <br/> |

Además de los servicios básicos de Internet, hay servicios de terceros que solo se usan para integrar la funcionalidad. Aunque estas son necesarias para la integración, están marcadas como opcionales en el artículo Office 365 endpoints, lo que significa que la funcionalidad básica del servicio seguirá funcionando si no se puede acceder al punto de conexión. Cualquier punto de conexión de red necesario tendrá el atributo necesario establecido en true. Cualquier punto de conexión de red que sea opcional tendrá el atributo necesario establecido en false y el atributo notas detallará las funciones que faltan en espera si la conectividad está bloqueada.
  
Si está intentando usar Office 365 y no se puede encontrar servicios de terceros, querrá [asegurarse de que todos los FQDN marcados como obligatorios u opcionales en este artículo se permiten a través del proxy y el Firewall](urls-and-ip-address-ranges.md).
  
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a>¿Cómo se bloquea el acceso a los servicios de consumidores de Microsoft?
<a name="bkmk_consumer"> </a>

La restricción del acceso a nuestros servicios de consumidor debe realizarse bajo su responsabilidad. La única forma confiable de bloquear los servicios de consumidor es restringir el acceso al FQDN *login.Live.com* . Este FQDN se usa en un amplio conjunto de servicios, incluidos los servicios que no son de consumidor, como MSDN, TechNet y otros. Este FQDN también se usa en el programa de intercambio de archivos seguro del soporte técnico de Microsoft y es necesario para transferir archivos para facilitar la solución de problemas de los productos de Microsoft.  Restringir el acceso a este FQDN puede dar como resultado la necesidad de incluir también excepciones a la regla para las solicitudes de red asociadas con estos servicios.
  
Tenga en cuenta que bloquear el acceso a los servicios de atención al cliente de Microsoft por sí solo no impedirá que un usuario de la red pueda exfiltrar información con un espacio empresarial de Office 365 u otro servicio.
  
## <a name="related-topics"></a>Temas relacionados

[Dirección IP de Office 365 y servicio web de URL](office-365-ip-web-service.md)

[Intervalos IP del centro de datos de Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Espacio IP público de Microsoft](https://www.microsoft.com/download/details.aspx?id=53602)
  
[Requisitos de la infraestructura de red para Microsoft Intune](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[ExpressRoute y Power BI](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[Direcciones URL e intervalos de direcciones IP de Office 365](urls-and-ip-address-ranges.md)
  
[Administrar ExpressRoute para la conectividad de Office 365](managing-expressroute-for-connectivity.md)
  
[Principios de conectividad de red de Office 365](office-365-network-connectivity-principles.md)
