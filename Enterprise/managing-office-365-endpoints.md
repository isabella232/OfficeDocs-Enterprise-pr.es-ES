---
title: Administrar puntos de conexión de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/22/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 99cab9d4-ef59-4207-9f2b-3728eb46bf9a
description: Algunas de las redes empresariales restricción el acceso a ubicaciones de internet genérico o incluyen backhaul sustancial o el procesamiento de tráfico de red. Para asegurarse de que los equipos de las redes como estos pueden tener acceso a Office 365, los administradores de red y proxy necesitan para administrar la lista de nombres de dominio completos, las direcciones URL, y las direcciones IP que componen la lista de extremos de Office 365. Estos es necesario que se agregará a ruta directa, el desvío de proxy, o las reglas de firewall y archivos PAC para asegurarse de que las solicitudes de red son capaces de ponerse en contacto con Office 365.
ms.openlocfilehash: 480d2fa1b55507187f9150d02907849178a451b5
ms.sourcegitcommit: d93f7a51e8cdefdfc9933cdf1f9e413b013bb367
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "25719024"
---
# <a name="managing-office-365-endpoints"></a>Administrar puntos de conexión de Office 365

La mayoría de las organizaciones de enterprise que tienen varias ubicaciones de office y de una conexión WAN tendrá que necesita la configuración para la conectividad de red de Office 365. Puede optimizar la red por enviar que todas las solicitudes de red de Office 365 directamente a través de su servidor de seguridad de confianza, omitir la inspección del nivel de todos los paquetes adicionales o procesamiento. Esto reduce la latencia y los requisitos de capacidad de perímetro. Que identifica el tráfico de red de Office 365 es el primer paso para proporcionar un rendimiento óptimo para los usuarios. Para obtener más información acerca de la conectividad de red de Office 365, vea [Principios de conectividad de red de Office 365](office-365-network-connectivity-principles.md)

Microsoft recomienda tener acceso a los extremos de la red de Office 365 y los cambios a ellos mediante la [dirección IP de Office 365 y servicio Web de dirección URL](office-365-ip-web-service.md)

Independientemente de cómo administrar el tráfico de red de Office 365 vital, Office 365 requiere conectividad a Internet. Otros extremos de la red donde se requiere conectividad aparecen en [los extremos adicionales que no se incluyen en el servicio Web de dirección URL y la dirección IP de Office 365](additional-office365-ip-addresses-and-urls.md)

Cómo usar los extremos de la red de Office 365 dependerá de la arquitectura de red de la organización de empresa. En este artículo se describe varias formas de arquitecturas de red de empresa pueden integrar con direcciones IP de Office 365 y las direcciones URL. La forma más sencilla para elegir qué red solicita confiar es usar dispositivos SDWAN que admiten la configuración automatizada de Office 365 en cada uno de sus oficinas. 

## <a name="sdwan-for-local-branch-egress-of-vital-office-365-network-traffic"></a>SDWAN de salida de la sucursal local del tráfico de red de Office 365 vital

En cada ubicación de la sucursal, puede proporcionar un dispositivo SDWAN que está configurado para enrutar el tráfico de Office 365 optimizar categoría de extremos, u optimizar y permitir que las categorías, directamente a la red de Microsoft. Otro tráfico de red, incluido el tráfico de centro de datos local, el tráfico de los sitios web de Internet general y el tráfico a extremos de categoría predeterminada de Office 365 se envía a otra ubicación donde se encuentra un perímetro de red más sustancial.

Microsoft está trabajando con los proveedores de SDWAN para habilitar la configuración automática. Para obtener más información, vea el [Programa de socios de red de Office 365](office-365-networking-partner-program.md).

<a name="pacfiles"> </a>
## <a name="use-a-pac-file-for-direct-routing-of-vital-office-365-traffic"></a>Utilizar un archivo de PAC para el enrutamiento directo de tráfico vital de Office 365

Usar archivos PAC o WPAD para administrar las solicitudes de red que están asociados con Office 365, pero no tienen una dirección IP. Las solicitudes de red típicas que se envían a través de un dispositivo de proxy o perimetral aumentan la latencia. Mientras que SSL de interrupción e inspeccionar crea la latencia más grande, otros servicios, como búsqueda de reputación y autenticación de proxy puede causar un rendimiento deficiente y una experiencia de usuario incorrecta. Además, estos dispositivos de red perimetral necesitan suficiente capacidad para procesar todas las solicitudes de conexión de red. Se recomienda no usar los dispositivos de proxy o inspección para las solicitudes de red de Office 365 directas.
  
[Galería de PowerShell Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile) es un script de PowerShell que lee los extremos de red más recientes desde el servicio Web de dirección URL y la dirección IP de Office 365 y crea un archivo de PAC de ejemplo. Puede modificar la secuencia de comandos para que se integra con la administración de archivos PAC existente. 

![Conectarse a Office 365 a través de firewalls y servidores proxy.](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)

**En la figura 1 - perímetro de la red de empresa Simple**

El archivo PAC se implementa en los exploradores web en el punto 1 en la figura 1. Cuando se usa un archivo PAC para salida directa del tráfico de red de Office 365 vital, necesitará también permitir la conectividad con las direcciones IP detrás de estas direcciones URL en el servidor de seguridad de red perimetral. Esto se realiza mediante la obtención de las direcciones IP para las mismas categorías de extremo de Office 365 tal como se especifica en el archivo PAC y creación firewall ACL basadas en esas direcciones. El servidor de seguridad es punto 3 en la figura 1. 

Por separado si elige sólo enrutamiento directo para los extremos de categoría optimizar, cualquier necesario permitir necesitan extremos de categoría que envían al servidor proxy que se mostrarán en el servidor proxy para el desvío de procesamiento adicional. Por ejemplo, no son compatibles con extremos de categoría tanto al permitir la optimizar salto de SSL e inspeccionar y autenticación de Proxy. El servidor proxy es punto 2 en la figura 1.

La configuración común es permitir sin procesar todo el tráfico saliente desde el servidor proxy para las direcciones IP de destino para el tráfico de red de Office 365 que visita al servidor proxy. Para obtener información acerca de los problemas con SSL de interrupción e inspeccionar, vea [uso de dispositivos de red de terceros o soluciones en el tráfico de Office 365](https://support.microsoft.com/en-us/help/2690045/using-third-party-network-devices-or-solutions-with-office-365).

Hay dos tipos de archivos PAC que genera la secuencia de comandos Get-PacFile.

|**Tipo**|**Descripción**|
|:-----|:-----|
|**1** <br/> |Enviar el tráfico de extremo de optimizar directo y todo lo demás con el servidor proxy. <br/> |
|**2** <br/> |Enviar optimizar y permitir tráfico extremo directo y todo lo demás con el servidor proxy. También se puede usar este tipo para enviar que todas las compatibles ExpressRoute para el tráfico de Office 365 a los segmentos de red ExpressRoute y todo lo demás con el servidor proxy. <br/> |

Este es un ejemplo sencillo de llamar a la secuencia de comandos de PowerShell:

```
Get-PacFile -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

Hay un número de parámetros que pueden pasar a la secuencia de comandos:

|**Parámetro**|**Descripción**|
|:-----|:-----|
|**ClientRequestId** <br/> |Esto es necesario y se pasa un GUID para el servicio web que representa el equipo cliente que realiza la llamada. <br/> |
|**Instance** <br/> |La instancia de servicio de Office 365 cuyo valor predeterminado es a todo el mundo. También se pasan al servicio web. <br/> |
|**TenantName** <br/> |El nombre del inquilino de Office 365. Se pasan al servicio web y usar como un parámetro reemplazable en algunas las direcciones URL de Office 365. <br/> |
|**Tipo** <br/> |El tipo del archivo de proxy PAC que se desea generar. <br/> |

Este es otro ejemplo de llamar a la secuencia de comandos de PowerShell con parámetros adicionales.

```
Get-PacFile -Type 2 -Instance Worldwide -TenantName Contoso -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7 
```

## <a name="proxy-server-bypass-processing-of-office-365-network-traffic"></a>Servidor proxy de desvío de procesamiento de tráfico de red de Office 365 

Cuando no se usan archivos PAC para dirigir el tráfico saliente, desea continuar con el desvío de procesamiento en el perímetro de su red mediante la configuración del servidor proxy. Algunos proveedores de servidores proxy han habilitado la configuración automatizada de este tal como se describe en el [Programa de socios de red de Office 365](office-365-networking-partner-program.md). 

Si está realizando este manual necesita obtener optimizar y permitir que los datos de la categoría de extremo desde el servicio de Web de dirección URL y la dirección IP de Office 365 y configurar el servidor proxy para el desvío de procesamiento para estos. Es importante evitar la interrupción de SSL e inspeccionar y la autenticación de Proxy para optimizar y permitir que los extremos de la categoría. 
  
<a name="bkmk_changes"> </a>
## <a name="change-management-for-office-365-ip-addresses-and-urls"></a>Administración de cambios para las direcciones IP de Office 365 y direcciones URL

Además de seleccionar la configuración adecuada para el perímetro de su red, es fundamental que adopte un proceso de administración de cambios para los extremos de Office 365. Estos extremos cambian con regularidad y si no se administra los cambios, puede acabar con los usuarios bloqueados o con un rendimiento deficiente después de una nueva dirección IP se agrega la dirección o dirección URL. 

Normalmente se publican los cambios realizados en las direcciones URL y las direcciones IP de Office 365 cerca el último día de cada mes. A veces se publicará un cambio fuera de esa programación debido a operativas, soporte técnico o los requisitos de seguridad.

Cuando se publica un cambio que requiere que se va a actuar debido a que se ha agregado una dirección IP o la dirección URL, debe esperar recibir el aviso de 30 días desde el momento en que se publique el cambio hasta que haya un servicio de Office 365 en dicho extremo. Aunque nuestro objetivo es para este período de notificación, es posible que no siempre sea posible debido a operativas, soporte técnico o los requisitos de seguridad. Los cambios que no requieren una acción inmediata para mantener la conectividad, como quitan direcciones IP o las direcciones URL o menos cambios significativos, no incluyen la notificación de avance. Independientemente de qué tipo de notificación se proporciona, se lista la fecha activa de servicio previsto para cada cambio.

### <a name="change-notification-using-the-web-service"></a>Cambiar la notificación mediante el servicio Web

Puede usar la dirección IP de Office 365 y el servicio Web de dirección URL para obtener la notificación de cambio. Se recomienda que llamar al método **web/Version** una vez cada hora para comprobar la versión de los extremos que va a usar para conectarse a Office 365. Si cambia esta versión en comparación con la versión que tiene en uso, debe obtener los datos más recientes de extremo desde el método web **/endpoints** y, opcionalmente, obtener las diferencias desde el método de web **/changes** . No es necesario llamar a la **/endpoints** o **/changes** métodos web si no ha habido ningún cambio a la versión que se encuentra. 

Para obtener más información, vea [dirección IP de Office 365 y servicio Web de dirección URL](office-365-ip-web-service.md).

### <a name="change-notification-using-rss-feeds"></a>Notificación de cambio de uso de fuentes RSS

El servicio de Web de dirección URL y la dirección IP de Office 365 proporciona una fuente RSS que puede suscribirse a en Outlook. Hay vínculos a las direcciones URL de RSS en cada una de las páginas de específico de la instancia de servicio de Office 365 para las direcciones IP y direcciones URL. Para obtener más información, vea [dirección IP de Office 365 y servicio Web de dirección URL](office-365-ip-web-service.md).

### <a name="change-notification-and-approval-review-using-microsoft-flow"></a>Notificación de cambios y aprobación revisan utilizando Microsoft Flow

Sabemos que aún es posible que requieren procesamiento manual para que los cambios de extremo de red que se incluyen a través de cada mes. Puede usar Microsoft Flow para crear un flujo que le notifica por correo electrónico y, opcionalmente, se ejecuta un proceso de aprobación de los cambios cuando los extremos de red de Office 365 tienen cambios. Una vez finalizada la revisión, puede tener el flujo de correo electrónico automáticamente los cambios realizados en su equipo de administración de servidor proxy y servidor de seguridad. 

Para obtener información acerca de una plantilla y un ejemplo de Microsoft Flow, vea [Utilizar Microsoft flujo para recibir un correo electrónico para los cambios realizados en las direcciones IP de Office 365 y direcciones URL](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/td-p/240651)
  
<a name="FAQ"> </a>
## <a name="office-365-network-endpoints-faq"></a>Preguntas más frecuentes de extremos de la red de Office 365

Preguntas más frecuentes con frecuencia administrador acerca de la conectividad de Office 365:
  
### <a name="how-do-i-submit-a-question"></a>¿Cómo se puede enviar una pregunta?

Haga clic en el vínculo en la parte inferior para indicar si el artículo ha sido útil y enviar preguntas adicionales. Se supervisión los comentarios y actualización las preguntas aquí con las preguntas más frecuentes.
  
### <a name="how-do-i-determine-the-location-of-my-tenant"></a>¿Cómo se puede determinar la ubicación de mi inquilino?

 **Ubicación del inquilino** se determina mejor con nuestro [Centro de datos se asignan](http://aka.ms/datamaps).
  
### <a name="am-i-peering-appropriately-with-microsoft"></a>¿Estoy interconexión adecuadamente con Microsoft?

 **Ubicaciones de Peering** se describen con más detalle en [interconexión con Microsoft](https://www.microsoft.com/peering).
  
Con relaciones de interconexión ISP más 2500 globalmente y 70 puntos de presencia, introducción desde la red a nuestro debería ser transparente. No se puede dañar a dedicar unos minutos, asegurándose de que relación de interconexión de su ISP es el más óptima, [le presentamos algunos ejemplos](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__guidance/) de buena y no tan buena interconexión no intervención a nuestra red. 
  
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a>¿Ver las solicitudes de red a direcciones IP no en la lista publicada, necesito para proporcionar acceso a ellos?
<a name="bkmk_MissingIP"> </a>

Sólo proporcionamos direcciones IP para los servidores de Office 365 a que se debe enrutar directamente. Esto no es una lista completa de todas las direcciones IP, verá las peticiones de red. Podrá ver las solicitudes de red de Microsoft y de terceros propietario, cancelar la publicación, las direcciones IP. Estas direcciones IP se generado dinámicamente o se administra de forma que impide que oportuna aviso cuando cambian. Si el servidor de seguridad no puede permitir el acceso basado en el FQDN para estas solicitudes de red, use un archivo PAC o WPAD para administrar las solicitudes.
  
¿Vea que una dirección IP asociada con la que desea obtener más información sobre Office 365?
  
1. Compruebe si la dirección IP que se incluye en un rango publicado mayor que con una [Calculadora de CIDR](http://jodies.de/ipcalc).
2. Vea si un socio propietario de la dirección IP con una [consulta whois](https://dnsquery.org/). Si es que son propiedad de Microsoft, puede ser un socio interno.
3. Comprobar el certificado, en un explorador se conectan a la dirección IP utilizando *HTTPS://\<dirección IP\> * , compruebe los dominios que aparecen en el certificado para comprender qué dominios están asociados con la dirección IP. Si es una propiedad de dirección IP de Microsoft y no en la lista de direcciones IP de Office 365, es probable que es la dirección IP está asociado con una CDN de Microsoft, como *MSOCDN.NET* o de otro dominio de Microsoft sin información publicada de IP. Si encuentra que el dominio en el certificado es donde se notificación para obtener una lista de la dirección IP, háganoslo saber.

### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a>¿Por qué se pueden ver los nombres como nsatc.net o akadns.net en los nombres de dominio de Microsoft?
<a name="bkmk_akamai"> </a>

Office 365 y otros servicios de Microsoft usan varios servicios de terceros, como Akamai y MarkMonitor para mejorar la experiencia de Office 365. Para mantener proporcionar la mejor experiencia posible, podemos cambiar estos servicios en el futuro. De esta forma, a menudo se publique el registro CNAME que señala a un tercero dominio propietario, un registro o la dirección IP. Dominios de otros fabricantes pueden hospedar contenido, como una CDN, o pueden hospedar un servicio, como un servicio de administración de tráfico geográfica. Cuando vea las conexiones a estos terceros, estén en el formulario de un redireccionamiento o referencia, no una solicitud inicial desde el cliente. Algunos clientes necesitan para garantizar este formulario de referencia y se permite la redirección para pasar sin agregar explícitamente que la larga lista de servicios de terceros de posibles nombres de dominio completos se puede usar.
  
La lista de servicios está sujeta a cambios en cualquier momento. Algunos de los servicios que están en uso son:
  
[MarkMonitor](https://www.markmonitor.com/) está en uso cuando se ven las solicitudes que incluyan * \*. nsatc.net* . Este servicio proporciona protección de nombre de dominio y supervisión para proteger el comportamiento malintencionado.
  
[ExactTarget](https://www.marketingcloud.com/) está en uso cuando se ven las solicitudes a * \*. exacttarget.com* . Este servicio proporciona administración de vínculos de correo electrónico y supervisión contra un comportamiento malintencionado.
  
[Akamai](https://www.akamai.com/) está en uso cuando se ven las solicitudes que incluyan uno de los siguientes FQDN. Este servicio ofrece ubican DNS y servicios de red de entrega de contenido.
  
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

### <a name="i-have-to-have-the-minimum-connectivity-possible-for-office-365"></a>Que hay que tener la conectividad mínima posible para Office 365
<a name="bkmk_thirdparty"> </a>

Office 365 es un conjunto de servicios integrados a función a través de internet, la confiabilidad y la disponibilidad promesas se basan en muchos servicios de internet estándar que están disponibles. Por ejemplo, servicios de internet estándar, como DNS, CRL y las CDN deben ser accesibles para usar Office 365, al igual que deben ser accesibles para usar los servicios de internet más modernos.

El conjunto de aplicaciones de Office 365 se divide en las áreas principales de servicio. Estos se pueden habilitar de forma selectiva para la conectividad y hay un área común que es una dependencia de todos y siempre es obligatorio.

|**Área de servicio**|**Descripción**|
|:-----|:-----|
|**Exchange** <br/> |Exchange Online y Exchange Online Protection <br/> |
|**SharePoint** <br/> |SharePoint Online y OneDrive para la Empresa <br/> |
|**Skype** <br/> |Skype para profesionales y los equipos de Microsoft <br/> |
|**Comunes** <br/> |Office 365 Pro Plus, Office Online, Azure AD y otros extremos de red comunes <br/> |

Además de los servicios de internet básicos, existen servicios de terceros que sólo se usan para integrar la funcionalidad de. Mientras que son necesarios para la integración, que se han marcado como opcional en el artículo de los extremos de Office 365 lo que significa que la funcionalidad principal del servicio seguirán funcionando si el extremo no es accesible. Cualquier extremo de la red que es necesario tendrá los necesarios atributo establecido como true. Cualquier extremo de la red que es opcional tendrá el atributo required establecido en false y el atributo de notes ofrecerán detalles de la funcionalidad que falta que deben esperar si se bloquea la conectividad.
  
Si está intentando usar Office 365 y se dando cuenta de servicios de terceros no están accesibles desea [asegurarse de que todos los nombres de dominio completos marcados obligatorio u opcional en este artículo se permiten a través del proxy y el firewall](urls-and-ip-address-ranges.md).
  
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a>¿Cómo se puede bloquear el acceso a los servicios de consumidor de Microsoft?
<a name="bkmk_consumer"> </a>

Restricción del acceso a nuestros servicios de consumidor debe realizarse bajo su responsabilidad, la forma confiable sólo a los servicios de consumidor de bloque es restringir el acceso a la *login.live.com* FQDN. Este FQDN se usa en un amplio conjunto de servicios, incluidos los servicios que no sean consumidor como MSDN, TechNet y otros. Restricción del acceso a este FQDN puede ocasionar la necesidad de incluir también excepciones a la regla para las solicitudes de red asociados con estos servicios.
  
Tenga en cuenta que bloquear el acceso a los servicios de consumidor de Microsoft por sí solo no impedir la capacidad de a alguien de la red a la información de exfiltrate mediante un inquilino de Office 365 o cualquier otro servicio.
  
## <a name="related-topics"></a>Temas relacionados

[Dirección IP de Office 365 y servicio web de URL](office-365-ip-web-service.md)

[Intervalos IP del centro de datos de Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Espacio IP público de Microsoft](https://www.microsoft.com/download/details.aspx?id=53602)
  
[Requisitos de infraestructura de red para Microsoft Intune](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[ExpressRoute y power BI](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[Intervalos de direcciones IP y URL de Office 365](urls-and-ip-address-ranges.md)
  
[Administrar ExpressRoute para la conectividad de Office 365](managing-expressroute-for-connectivity.md)
  
[Principios de conectividad de red de Office 365](office-365-network-connectivity-principles.md)
