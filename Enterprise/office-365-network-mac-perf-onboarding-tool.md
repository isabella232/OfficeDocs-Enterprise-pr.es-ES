---
title: Herramienta de incorporación de red de Office 365 en el centro de administración de M365 (versión preliminar)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 03/31/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Herramienta de incorporación de red de Office 365 en el centro de administración de M365 (versión preliminar)
ms.openlocfilehash: 299bace51b768add9ace29ce2f0680a2d8dd0250
ms.sourcegitcommit: 44a0e9a134373eb0d1292761089a6557b01ac327
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2020
ms.locfileid: "43081702"
---
# <a name="office-365-network-onboarding-tool-in-the-m365-admin-center-preview"></a>Herramienta de incorporación de red de Office 365 en el centro de administración de M365 (versión preliminar)

La herramienta de incorporación de red de Office 365 se encuentra <https://connectivity.office.com>en. Se trata de una herramienta de Adjunct a la información sobre la puntuación de red y la puntuación de red disponible en el centro de administración de Microsoft 365 en el área **mantenimiento | **Menú de rendimiento de la red.

La información de red del centro de administración de Microsoft 365 se basa en las mediciones del producto de su inquilino de Office 365. En comparación, la información de red de la herramienta de incorporación de red de Office 365 se ejecuta de forma local en la herramienta. Las pruebas que se pueden llevar a cabo en el producto son limitadas y al ejecutar pruebas locales para el usuario se pueden recopilar más datos, lo que da lugar a una información más profunda. Considere que en la información de red del centro de administración de Microsoft 365 se muestra que hay un problema de red para usar Office 365 en una ubicación específica de la oficina. La herramienta de incorporación de red de Office 365 puede ayudarle a identificar la causa raíz de ese problema, lo que provoca una acción recomendada para mejorar el rendimiento de la red.

Le recomendamos que se usen conjuntamente donde el estado de calidad de la red pueda evaluarse para cada ubicación de la oficina en el centro de administración de Microsoft 365 y se puedan encontrar más detalles tras la implementación de las pruebas basadas en la herramienta de incorporación de la red de Office 365.

>[!IMPORTANT]
>Información sobre la red, recomendaciones de rendimiento y evaluaciones en el centro de administración de Microsoft 365 se encuentra actualmente en estado de versión preliminar y solo está disponible para los inquilinos de Office 365 que se han inscrito en el programa de vista previa de características.

## <a name="the-advanced-tests-client-application"></a>Aplicación cliente de pruebas avanzadas

La herramienta de incorporación de red de Office 365 está configurada en dos partes. Hay un sitio <https://connectivity.office.com> web y hay una aplicación cliente de Windows descargable. El cliente descargable ejecuta pruebas avanzadas de conectividad de red y la mayoría de las pruebas requieren que esto se ejecute.

Puede ejecutar la prueba del cliente avanzado desde el sitio web y rellenará los resultados de nuevo en la página web mientras se ejecuta.

![Resultados de pruebas de ejemplo de la herramienta de incorporación de la red de O365](Media/m365-mac-perf/m365-mac-perf-onboarding-tool-tests.png)

## <a name="user-office-location"></a>Ubicación de la oficina de usuario

La ubicación de la oficina de usuario se detecta desde el explorador Web de los usuarios. Se usa para identificar distancias de red a partes específicas del perímetro de la red de la empresa.

La ubicación de la oficina de usuario se muestra en la vista del mapa.

## <a name="distance-to-the-network-egress-location"></a>Distancia a la ubicación de salida de red

Identificamos la dirección IP de salida de red en el lado servidor. Las bases de datos de ubicación se usan para buscar la ubicación aproximada de salida de red y determinar la distancia desde esa ubicación a la ubicación de la oficina. Esto se muestra como un conocimiento de la red si la distancia es superior a 500 millas (800 kilómetros).

La ubicación de salida de red se muestra en la vista del mapa y se conecta a la ubicación de la oficina del usuario que indica el backhaul de red dentro de la WAN empresarial.

Es posible que la ubicación buscada en la dirección IP de salida de red no sea precisa y esto provocaría un resultado falso en esta prueba. Para validar si se produce este error para una dirección IP específica, puede usar sitios web de ubicación de direcciones IP de red de acceso público.

La implementación de salida de red local y directa desde ubicaciones de oficinas de usuario a Internet es la recomendada para la conectividad de red de Office 365. Las mejoras en la salida local y directa son la mejor forma de afrontar esta visión de la red.

## <a name="exchange-online-service-front-door"></a>Puerta frontal del servicio Exchange Online

La puerta de la puerta del servicio de Exchange online en uso se identifica de la misma forma que lo hace Outlook y se mide la latencia de TCP de red de la ubicación de la oficina de usuario a ella. Ambos se muestran y el servicio en uso de Exchange Online se compara con la lista de puertas de las puertas de servicio óptimas recomendadas para la ubicación actual. Se muestra como un conocimiento de la red si se usa un servicio de la puerta principal no óptimo de Exchange Online.

El uso de un servicio de Exchange online no óptimo puede deberse a una backhaul? n de red antes de que la red corporativa se deshaga, en cuyo caso se recomienda la salida local y directa de la red. También podría deberse al uso de un servidor remoto de resolución de recursiva de DNS, en cuyo caso se recomienda alinear el servidor de resolución de DNS recursivo con la salida de red.

Se calcula una posible mejora de la latencia TCP para la puerta de la puerta del servicio de Exchange Online. Esto se realiza examinando la latencia de red de la ubicación de la oficina de usuario probada y restando la latencia de red de la ubicación actual a la puerta de la puerta del servicio de Exchange online de cierre. La diferencia representa la posible oportunidad de mejora.

## <a name="comparison-of-performance-of-customers-in-the-area"></a>Comparación del rendimiento de los clientes en el área

La latencia TCP de red de la ubicación de la oficina del usuario al servicio de Exchange Online se compara con otros clientes de Office 365 en la misma zona metropolitana. Se muestra un conocimiento de la red si el 10% o más de los clientes de la misma área metropolitana tienen un mejor rendimiento.

Este conocimiento de red se genera sobre la base de que todos los usuarios de una ciudad tienen acceso a la misma infraestructura de telecomunicaciones y a la misma proximidad a los circuitos de Internet y la red de Microsoft.

## <a name="in-use-default-gateway"></a>En usar la puerta de enlace predeterminada

La puerta de enlace predeterminada en uso es el enrutador que el cliente de prueba ha configurado para enrutar conexiones de red TCP/IP.

Se proporciona solo para información y no contribuye a ningún conocimiento de la red.

## <a name="in-use-dns-servers"></a>En usar servidor (es) DNS

Muestra el servidor DNS configurado en el equipo cliente que ejecutó las pruebas. Es posible que sea un servidor de resolución de recursiva de DNS, pero no es frecuente. Es más probable que sea un servidor de reenviador DNS que almacene los resultados de DNS y reenvíe las solicitudes de DNS que no estén en caché a otro servidor DNS.

Se proporciona solo para información y no contribuye a ningún conocimiento de la red.

## <a name="identified-dns-recursive-resolver-server"></a>Servidor de resolución de nombres recursivo de DNS identificado

La resolución de problemas de DNS en uso se identifica mediante la realización de una solicitud de DNS específica y, a continuación, preguntando al servidor de nombres DNS la dirección IP que recibió la misma solicitud. Esta dirección IP es la resolución de DNS recursiva y se buscará en las bases de datos de ubicación de direcciones IP para buscar la ubicación. A continuación, se calcula la distancia desde la ubicación de la oficina del usuario hasta la ubicación del servidor de resolución de DNS recursivo. Esto se muestra como un conocimiento de la red si la distancia es superior a 500 millas (800 kilómetros).

Es posible que la ubicación buscada en la dirección IP de salida de red no sea precisa y esto provocaría un resultado falso en esta prueba. Para validar si se produce este error para una dirección IP específica, puede usar sitios web de ubicación de direcciones IP de red de acceso público.

Este conocimiento de la red afectará específicamente a la selección de la puerta del servicio de Exchange Online. Para resolver esta visión, la salida local y directa de la red debe ser un requisito previo y, a continuación, la resolución de nombres recursivos de DNS se debe encontrar cerca de la salida de la red.

## <a name="dns-lookup-of-exchange-online-front-end-server-and-sharepoint-online-front-end-server"></a>Búsqueda de DNS del servidor front-end de Exchange Online y el servidor front-end de SharePoint Online

Estos muestran el registro DNS para la puerta de entrada del servicio de estas dos cargas de trabajo de Office 365. Solo se proporcionan para información y no hay ningún conocimiento de la red asociado.

## <a name="proxy-server-identification"></a>Identificación del servidor proxy

Se identifican los servidores proxy configurados en el equipo local. Se identifica si cualquiera de estos se configura en la ruta de red para optimizar el tráfico de red de la categoría Office 365. Se identifica la distancia desde la ubicación de la oficina del usuario hacia los servidores proxy. La distancia se prueba primero por ping ICMP y, si se produce un error, se prueba con el comando TCP Ping y, finalmente, si se produce un error al buscar la dirección IP del servidor proxy en una base de datos de ubicación de direcciones IP. Se muestra un conocimiento de la red si el servidor proxy es superior a 500 millas (800 kilómetros) lejos de la ubicación de la oficina del usuario.

## <a name="media-quality-checks"></a>Comprobaciones de calidad de medios

Esta prueba instala y ejecuta la herramienta de evaluación de la red de Skype empresarial e interpreta los resultados. La herramienta se puede encontrar en [https://www.microsoft.com/download/details.aspx?id=53885](https://www.microsoft.com/download/details.aspx?id=53885).

Se trata de pruebas de protocolo UDP que se usan en la funcionalidad de conferencia y audio y vídeo de Microsoft Teams. Se prueba la pérdida de paquetes UDP, la latencia de red UDP, la vibración UDP y la reordenación de paquetes UDP. Se muestra un conocimiento de la red si alguno de ellos se encuentra a lo largo del intervalo permitido.

## <a name="tcp-connectivity-tests"></a>Pruebas de conectividad TCP

Se prueba la conectividad HTTP desde la ubicación de la oficina del usuario hasta todos los puntos de conexión de red de Office 365 necesarios. Se publican en [https://aka.ms/o365ip](https://aka.ms/o365ip). Se muestra un conocimiento de red para cualquier punto de conexión de red necesario al que no se pueda conectar.

La conectividad de Ay será bloqueada por un servidor proxy, un firewall u otro dispositivo de seguridad de red en el perímetro de red de la empresa o en uso como proxy en la nube.

## <a name="ssl-interception-tests"></a>Pruebas de interceptación de SSL

Probamos el certificado SSL en cada punto de conexión de red de Office 365 necesario que se encuentra en la categoría optimizar [https://aka.ms/o365ip](https://aka.ms/o365ip)o permitir como se define en. Si alguna de las pruebas no encuentra un certificado SSL de Microsoft, la red cifrada conectada debe haber sido interceptada por un dispositivo de red intermediario. Se muestra un conocimiento de red en cualquier punto de conexión de red cifrado interceptado.

Donde se encuentra un certificado SSL que Microsoft no proporciona, se muestra el FQDN de la prueba y el propietario del certificado SSL en uso. Este propietario de certificado SSL puede ser un proveedor de servidor proxy o un certificado autofirmado de empresa.

## <a name="network-path-diagnostics"></a>Diagnósticos de ruta de red

En esta sección se muestran los resultados de ICMP traceroute en la puerta frontal del servicio de Exchange Online, el servicio de SharePoint Online y la puerta principal del servicio de Microsoft Teams. Se proporciona solo para información y no hay ningún conocimiento de la red asociado.

## <a name="related-topics"></a>Temas relacionados

[Recomendaciones de rendimiento de red en el centro de administración de Microsoft 365 (versión preliminar)](office-365-network-mac-perf-overview.md)

[Office 365 Network performance Insight (versión preliminar)](office-365-network-mac-perf-insights.md)

[Evaluación de la red de Office 365 (versión preliminar)](office-365-network-mac-perf-score.md)

[Servicios de ubicación de conectividad de red 365 de Office (versión preliminar)](office-365-network-mac-location-services.md)
