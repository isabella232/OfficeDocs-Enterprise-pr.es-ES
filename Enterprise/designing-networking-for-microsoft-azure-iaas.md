---
title: "Diseño de redes para IaaS de Microsoft Azure"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 9cb70c9d-9ed9-47cc-af5a-6403d87d3372
description: "Resumen: Comprender cómo diseñar redes optimizadas para cargas de trabajo en Microsoft Azure IaaS."
ms.openlocfilehash: 2430b62e04392ddd4266d37797b18ae7e890c092
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="designing-networking-for-microsoft-azure-iaas"></a>Diseño de redes para IaaS de Microsoft Azure

 **Resumen:** Entender cómo diseñar redes optimizadas para cargas de trabajo en Microsoft Azure IaaS.
  
La optimización de las redes para las cargas de trabajo de TI hospedadas en IaaS de Azure requiere un conocimiento de las redes virtuales (VNets) de Azure, los espacios de direcciones, el enrutamiento, el DNS y el equilibrio de carga.
  
## <a name="planning-steps-for-any-vnet"></a>Pasos de planeación para cualquier red virtual

Siga estos pasos para cualquier tipo de red virtual.
  
### <a name="step-1-prepare-your-intranet-for-microsoft-cloud-services"></a>Paso 1: Preparar la intranet para los servicios en la nube de Microsoft.

Vea la sección **Pasos para preparar la red para Servicios en la nube de Microsoft** en [Elementos comunes de conectividad de Microsoft Cloud](common-elements-of-microsoft-cloud-connectivity.md).
  
### <a name="step-2-optimize-your-internet-bandwidth"></a>Paso 2: Optimizar el ancho de banda de Internet.

Para optimizar el ancho de banda de Internet, siga los pasos 2 a 4 de la sección **Pasos para preparar la red para los servicios SaaS de Microsoft** del artículo [Diseño de redes para SaaS de Microsoft](designing-networking-for-microsoft-saas.md).
  
### <a name="step-3-determine-the-type-of-vnet-cloud-only-or-cross-premises"></a>Paso 3: Determinar el tipo de red virtual (solo nube o entre locales).

Una red virtual de solo nube no tiene conexión a una red local. Aquí le mostramos un ejemplo.
  
**Figura 1: Una nube de sólo VNet**

![Figura 1: Una red virtual de solo nube en Azure](images/8be19104-02b3-4a7f-b0a0-30d6fcf8890b.png)
  
La figura 1 muestra un conjunto de máquinas virtuales en una red virtual de solo nube.
  
Una red virtual entre locales tiene una conexión VPN de sitio a sitio (S2S) o de ExpressRoute a una red local a través de una puerta de enlace de Azure. Aquí le mostramos un ejemplo.
  
**Figura 2: Un local entre VNet**

![Figura 2: Una red virtual entre locales en Azure](images/caacf007-e0dc-45d3-9531-441109776d25.png)
  
La figura 2 muestra un conjunto de máquinas virtuales en una red virtual entre locales, que está conectada a una red local.
  
Consulte la sección de [pasos de planificación para un VNet local entre](designing-networking-for-microsoft-azure-iaas.md#cross_prem) en este artículo.
  
### <a name="step-4-determine-the-address-space-of-the-vnet"></a>Paso 4: Determinar el espacio de direcciones de la red virtual.

La tabla 1 muestra los espacios de direcciones para los distintos tipos de redes virtuales.
  
|**Tipo de VNet**|**Espacio de direcciones de red virtual**|
|:-----|:-----|
|Basada solo en la nube  <br/> |Espacio de direcciones privadas arbitrarias  <br/> |
|Basada solo en la nube e interconectada  <br/> |Privado arbitrario, pero no se superponen con otros conectados VNets  <br/> |
|Entre locales  <br/> |Privada, pero sin que se superponga con redes locales  <br/> |
|Local e interconectada  <br/> |Privada, pero sin que se superponga con otras redes locales y virtuales conectadas  <br/> |
   
 **Tabla 1: Tipos de VNets y su correspondiente espacio de dirección**
  
El DHCP asigna a las máquinas virtuales una configuración de direcciones desde el espacio de direcciones de la subred:
  
- Dirección/máscara de subred
    
- Puerta de enlace predeterminada
    
- Direcciones IP del servidor DNS
    
También puede reservar una dirección IP estática.
  
A las máquinas virtuales también se les puede asignar una dirección IP pública, ya sea individualmente o desde el servicio en la nube que las contiene (solo para máquinas de implementación clásicas).
  
### <a name="step-5-determine-the-subnets-within-the-vnet-and-the-address-spaces-assigned-to-each"></a>Paso 5: Determinar las subredes de la red virtual y los espacios de direcciones asignados a cada una.

Hay dos tipos de subredes en una red virtual: una subred de puerta de enlace y una subred de hospedaje de máquina virtual.
  
**Figura 3: Los dos tipos de subredes de Azure**

![Figura 3: Los dos tipos de subredes de Azure](images/2eaa512d-1293-4e9b-b927-6bfe0fc0acb4.png)
  
La figura 3 muestra una red virtual que contiene una subred de puerta de enlace que, a su vez, contiene una puerta de enlace de Azure y un conjunto de subredes de hospedaje de máquina virtual que engloba las máquinas virtuales.
  
Azure necesita la subred de puerta de enlace de Azure para hospedar las dos máquinas virtuales de su puerta de enlace de Azure. Especifique un espacio de direcciones que tenga una longitud de prefijo de, al menos, 29 bits (ejemplo: 192.168.15.248/29). Se recomienda una longitud de prefijo de 28 bits o menor, especialmente si va a usar ExpressRoute.
  
Una práctica recomendada para determinar el espacio de direcciones de la subred de puerta de enlace de Azure es la siguiente:
  
1. Decida el tamaño de la subred de puerta de enlace.
    
2. En los bits variables del espacio de direcciones de la red virtual, establezca los bits usados para la subred de puerta de enlace en 0 y los bits restantes en 1.
    
3. Convierta a decimales y expréselo como un espacio de direcciones con la longitud de prefijo establecida en el tamaño de la subred de puerta de enlace.
    
Con este método, el espacio de direcciones de la subred de puerta de enlace siempre está en el extremo más alejado del espacio de direcciones de la red virtual.
  
En este ejemplo, se define el prefijo de dirección que corresponde a la subred de puerta de enlace: el espacio de direcciones de la red virtual es 10.119.0.0/16. La organización usará inicialmente una conexión VPN de sitio a sitio, pero al final empleará ExpressRoute. La tabla 2 muestra los pasos y los resultados de determinar el prefijo de dirección de la subred de puerta de enlace en una notación de prefijos de red (también conocido como CIDR).

A continuación presentamos los pasos y ejemplo de determinar el prefijo de la dirección de subred puerta de enlace:

1. Decidir el tamaño de la subred de puerta de enlace. En nuestro ejemplo, elegimos /28.
2. Establecer los bits de la parte variable del espacio de direcciones VNet (b) a 0 para la puerta de enlace de bits de subred (G), 1 en caso contrario (V). En nuestro ejemplo, estamos utilizando el espacio de direcciones de 10.119.0.0/16 para el VNet.<br/>
<br/>10.119. bbbbbbbb. bbbbbbbb<br/>10.119. VVVVVVVV. VVVVGGGG<br/>10.119. 11111111. 11110000<br/><br/>
3. Convertir el resultado del paso 2 en decimal y se expresa como un espacio de direcciones. En nuestro ejemplo, 10.119. 11111111. 11110000 es 10.119.255.240, y con la longitud del prefijo del paso 1, (28 en nuestro ejemplo), el prefijo de dirección de subred puerta de enlace resultante es 10.119.255.240/28.
  
Para obtener más información, vea [Calculadora de espacio de direcciones para las subredes de la puerta de enlace de Azure](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) .
  
En las subredes de hospedaje de máquina virtual es donde se colocan las máquinas virtuales de Azure, lo cual se puede hacer siguiendo las instrucciones locales típicas, como un rol común o el nivel de una aplicación o para el aislamiento de la subred.
  
Azure utiliza las primeros 3 direcciones en cada subred. Por lo tanto, el número de posibles direcciones de una subred Azure es 2<sup>n</sup> -5, donde n es el número de bits de host. La tabla 3 se muestra la gama de máquinas virtuales que necesite, con el número de hosts bits necesarios y el tamaño de la subred correspondiente.
  
|**Máquinas virtuales que necesite**|**Bits de host**|**Tamaño de la subred**|
|:-----|:-----|:-----|
|1-3  <br/> |3  <br/> |/29  <br/> |
|4-11  <br/> |4  <br/> |/28  <br/> |
|12-27  <br/> |5  <br/> |/27  <br/> |
|28-59  <br/> |6  <br/> |/26  <br/> |
|60-123  <br/> |7  <br/> |/25  <br/> |
   
 **Tabla 3: requisitos de la máquina Virtual y sus tamaños de subred**
  
Para obtener más información acerca de la cantidad máxima de máquinas virtuales en una subred o VNet, consulte [Límites de redes](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).
  
Para obtener más información, consulte [Plan y diseño de redes virtuales de Azure](https://azure.microsoft.com/documentation/articles/virtual-network-vnet-plan-design-arm/).
  
### <a name="step-6-determine-the-dns-server-configuration-and-the-addresses-of-the-dns-servers-to-assign-to-vms-in-the-vnet"></a>Paso 6: Determinar la configuración del servidor DNS y las direcciones de los servidores DNS para asignar a las máquinas virtuales en la red virtual.

Azure asigna a las máquinas virtuales las direcciones de los servidores DNS mediante DHCP. Los servidores DNS pueden suministrarlos:
  
- Azure: se proporciona un registro de nombres locales y una resolución de nombres de Internet
    
- Usted: se proporciona un registro de nombres locales o de intranet y una resolución de nombres de Internet o de intranet
    
En la tabla 4, se muestran las diferentes configuraciones de los servidores DNS para cada tipo de red virtual.
    
|**Tipo de VNet**|**Servidor DNS**|
|:-----|:-----|
|Basada solo en la nube  <br/> |Suministrado por Azure para la resolución de nombres de Internet y locales  <br/> Máquina virtual de Azure para la resolución de nombres de Internet y locales (reenvío DNS)  <br/> |
|Entre locales  <br/> |Local para la resolución de nombres locales y de intranet  <br/> Máquina virtual de Azure para la resolución de nombres de Internet y locales (replicación y reenvío DNS)  <br/> |
   
 **Tabla 4: Opciones de servidor DNS para los dos tipos diferentes de VNets**
  
Para obtener más información, vea [Resolución de nombres para las máquinas virtuales y las instancias de la función](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances).
  
### <a name="step-7-determine-the-load-balancing-configuration-internet-facing-or-internal"></a>Paso 7: Determinar la configuración de equilibrio de carga (accesible desde Internet o interna).

En algunos casos, queremos distribuir el tráfico entrante a un conjunto de servidores que tienen el mismo rol. IaaS de Azure dispone de una instalación integrada para hacer esto con cargas de tráfico accesibles desde Internet e internas.
  
El equilibrio de carga de Azure accesible desde Internet distribuye aleatoriamente el tráfico entrante no solicitado de Internet a los miembros de un conjunto de carga equilibrada. 
  
**Figura 4: Un equilibrador de carga externo en Azure**

![Figura 4: Un equilibrador de carga externo en Azure](images/eb5945e5-0c2b-40f1-b9ed-54bb2b0f9e59.png)
  
La figura 4 muestra un equilibrador de carga externo en Azure y que distribuye el tráfico entrante en una regla de NAT de entrada o extremo a un conjunto de máquinas virtuales en un conjunto de equilibrio de carga.
  
El equilibrio de carga interno de Azure distribuye aleatoriamente el tráfico entrante no solicitado desde otras máquinas virtuales de Azure o desde equipos de la intranet a los miembros de un conjunto de equilibrio de carga.  
  
**Figura 5: Un equilibrador de carga interno en Azure**

![Figura 5: Un equilibrador de carga interno en Azure](images/d1451b73-6465-449d-b3e6-22160ce51f35.png)
  
La figura 5 muestra un equilibrador de carga interno en Azure y que distribuye el tráfico entrante en una regla de NAT de entrada o extremo a un conjunto de máquinas virtuales en un conjunto de equilibrio de carga.
  
Para obtener más información, vea el [Equilibrador de carga de Azure](https://docs.microsoft.com/azure/load-balancer/load-balancer-overview).
  
### <a name="step-8-determine-the-use-of-virtual-appliances-and-user-defined-routes"></a>Paso 8: Determinar el uso de las aplicaciones virtuales y las rutas definidas por el usuario.

Si tiene que reenviar el tráfico a aplicaciones virtuales de la red virtual, puede que deba agregar a una subred una o varias rutas que haya definido el usuario.
  
**Figura 6: Dispositivos virtuales y rutas definidas por el usuario en Azure**

![Figura 6: Las aplicaciones virtuales y las rutas definidas por el usuario en Azure](images/f181d0f4-ebf9-439e-9c98-dec17428c32b.png)
  
La figura 6 muestra una red virtual entre locales y una ruta definida por el usuario asignada a una subred de hospedaje de máquina virtual que apunta a una aplicación virtual.
  
Para obtener más información, vea [rutas de usuario definidos y el reenvío de IP](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview).
  
### <a name="step-9-determine-how-computers-from-the-internet-will-connect-to-virtual-machines"></a>Paso 9: Determinar cómo se conectarán los equipos de Internet a las máquinas virtuales.

Hay varias maneras de proporcionar acceso a Internet a las máquinas virtuales de una red virtual, que incluye el acceso desde la red de la organización a través del servidor proxy u otro dispositivo perimetral.
  
La tabla 5 recoge los métodos para filtrar o inspeccionar el tráfico entrante no solicitado.
  
|**Método**|**Modelo de implementación**|
|:-----|:-----|
|1. Puntos de conexión y ACL configurados en los servicios en la nube  <br/> |Clásico  <br/> |
|2. Grupos de seguridad de red  <br/> |Administrador de recursos y clásico  <br/> |
|3. Equilibrador de carga accesible desde Internet con reglas de NAT entrantes  <br/> |Administrador de recursos  <br/> |
|4. dispositivos de seguridad en el mercado de Azure (no se muestra) de la red  <br/> |Administrador de recursos y clásico  <br/> |
   
 **Tabla 5: Métodos de conectarse a máquinas virtuales y sus correspondientes modelos de implementación de Azure**
  
**Figura 7: Conexión a Azure máquinas virtuales a través de Internet**

![Figura 7: Conexión a máquinas virtuales de Azure a través de Internet](images/c5e3531b-170a-4482-a6ff-fb8fbbe81b35.png)
  
La figura 7 muestra un equipo conectado a Internet que se conecta a una máquina virtual en un servicio en la nube usando un punto de conexión, una máquina virtual de una subred que usa un grupo de seguridad de red y una máquina virtual de una subred que usa un equilibrador de carga externo y reglas de NAT entrantes.
  
La seguridad adicional la proporcionan:
  
- Conexiones de Escritorio remoto y SSH, que se autentican y se cifran.
    
- Sesiones remotas de PowerShell, que se autentican y se cifran.
    
- Modo de transporte IPsec, que puede usar para el cifrado de extremo a extremo.
    
- Protección DDoS de Azure, que ayuda a prevenir ataques internos y externos
    
Para obtener más información, vea [Seguridad de nube de Microsoft para Enterprise Architects](https://aka.ms/cloudarchsecurity) y [Seguridad de la red de Azure](https://azure.microsoft.com/blog/azure-network-security/).
  
### <a name="step-10-for-multiple-vnets-determine-the-vnet-to-vnet-connection-topology"></a>Paso 10: Para varias redes virtuales, determinar la topología de conexión de una red virtual a otra.

Las redes virtuales pueden conectarse entre sí mediante topologías como las que se usan para conectar los sitios de una organización.
  
Una configuración de encadenamiento conecta las redes virtuales de una serie.
  
**Figura 8: Una margarita configuración para VNets**

![Figura 8: Una configuración de conexión en serie para redes virtuales de Azure](images/264d5dd4-06c5-483f-9428-a18cc1f68ac1.png)
  
La figura 8 muestra cinco VNets conectados en serie con una configuración de margarita.
  
Una configuración de concentrador y radio conecta varias redes virtuales a un conjunto de redes virtuales centrales, que están conectadas entre sí.
  
**Figura 9: Un concentrador y radios configuración para VNets**

![Figura 9: Una configuración de concentrador y radio para las redes virtuales de Azure](images/dd442a38-5b76-4ac5-b743-8fc7711a91ba.png)
  
La figura 9 muestra seis redes virtuales, dos redes virtuales son concentradores conectados entre sí y también otras dos son redes virtuales de radio.
  
Una configuración de malla completa conecta las redes virtuales entre sí.
  
**Figura 10: Configuración de VNets de malla completa**

![Figura 10: Una configuración de malla para redes virtuales de Azure](images/9dda0738-10db-4a63-95b3-79851a399b71.png)
  
La figura 10 muestra cuatro redes virtuales que están conectadas entre sí y que usan un total de seis conexiones de red virtual a red virtual.
  
## <a name="planning-steps-for-a-cross-premises-vnet"></a>Pasos de planeación para una red virtual entre locales
<a name="cross_prem"> </a>

Siga estos pasos para una red virtual entre locales.
  
> [!TIP]
> Para crear un entorno de prueba/desarrollo local entre simulado, consulte [simulada entre local red virtual en Azure](simulated-cross-premises-virtual-network-in-azure.md). 
  
### <a name="step-1-determine-the-cross-premises-connection-to-the-vnet-s2s-vpn-or-expressroute"></a>Paso 1: Determinar la conexión entre locales a la red virtual (VPN S2S o ExpressRoute).

En la tabla 6 se recogen los distintos tipos de conexiones.
  
|**Tipo de conexión**|**Finalidad**|
|:-----|:-----|
|VPN sitio a sitio (S2S)  <br/> |Conectar sitios de 1 a 10 (incluidos otros VNets) a un VNet único.  <br/> |
|ExpressRoute  <br/> |Un vínculo seguro y privado a Azure a través de un proveedor de intercambio de Internet (IXP) o un proveedor de servicio de red (NSP).  <br/> |
|VPN punto a sitio (P2S)  <br/> |Conecta un solo equipo a una red virtual.  <br/> |
|Dispositivos VPN para el emparejamiento de VNET o de red virtual a red virtual (V2V)   <br/> |Conecta una red virtual a otra.  <br/> |
   
 **Tabla 6: Los tipos de conexiones para entre local VNets**
  
Para obtener más información sobre el número máximo de conexiones, consulte [Límites de redes](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).
  
Para obtener más información acerca de los dispositivos VPN, consulte [dispositivos VPN para las conexiones de red virtual de sitio a sitio](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).
  
Para obtener más información acerca de la interconexión de VNet, consulte [VNet peering](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview).
  
**Figura 11: Las cuatro maneras de conectarse a un VNet local entre**

![Figura 11: Las tres formas de conectarse a una red virtual de Azure entre locales](images/d5d4a625-cfbd-4a77-9159-eaca69d07e93.png)
  
La figura 11 muestra un VNet con los cuatro tipos de conexiones: una conexión P2S desde un equipo, una conexión VPN S2S desde una red local, una conexión de ExpressRoute desde una red local y una conexión de VNet a VNet desde otro VNet. 
  
Puede conectarse a las máquinas virtuales de una red virtual de las maneras siguientes:
  
- Administración de máquinas virtuales de redes virtuales desde la red local o Internet
    
- Acceso a cargas de trabajo de TI desde la red local
    
- Ampliación de la red a través de redes virtuales adicionales
    
La seguridad en las conexiones se consigue mediante lo siguiente:
  
- P2S usa el protocolo de túnel de sockets de seguros (SSTP)  
    
- S2S y conexiones VPN de red virtual a red virtual usan el modo de túnel IPsec con AES256
    
- ExpressRoute es una conexión WAN privada
    
Para obtener más información, vea [Seguridad de nube de Microsoft para Enterprise Architects](https://aka.ms/cloudarchsecurity) y [Seguridad de la red de Azure](https://azure.microsoft.com/blog/azure-network-security/).
  
### <a name="step-2-determine-the-on-premises-vpn-device-or-router"></a>Paso 2: Determinar el dispositivo o enrutador VPN local.

El dispositivo o enrutador VPN local actúa como:
  
- Par IPsec que finaliza la conexión de VPN S2S desde la puerta de enlace de Azure.
    
- Par BPG y punto de finalización para la conexión de ExpressRoute de emparejamiento privado.
    
**Figura 12: Enrutador VPN local o dispositivo**

![Figura 12: El dispositivo o enrutador de VPN local](images/bd221468-a660-4730-aa55-0426986480b9.png)
  
La figura 12 muestra una red virtual entre locales conectada a un enrutador o dispositivo VPN local.
  
Para obtener más información, consulte [acerca de VPN gateway](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways).
  
### <a name="step-3-add-routes-to-your-intranet-to-make-the-address-space-of-the-vnet-reachable"></a>Paso 3: Agregar rutas a la intranet para hacer que el espacio de dirección de la VNet alcanzable.

El enrutamiento a redes virtuales desde ubicaciones locales consiste en lo siguiente:
  
1. Una ruta para el espacio de direcciones de red virtual que apunte al dispositivo VPN.
    
2. Una ruta para el espacio de direcciones de red virtual en el dispositivo VPN que apunte a la conexión VPN S2S o de ExpressRoute
    
**Figura 13: Las rutas locales necesarios para hacer accesible un VNet**

![Figura 13: Las rutas locales necesarias para hacer que una red virtual de Azure sea accesible](images/7a1e20c1-fbc4-4cb9-9961-735da4e23307.png)
  
En la figura 13, se muestra la información de enrutamiento que necesitan los enrutadores locales y el enrutador o dispositivo VPN que representa el espacio de direcciones de la red virtual.
  
### <a name="step-4-for-expressroute-plan-for-the-new-connection-with-your-provider"></a>Paso 4: Para ExpressRoute, planear la nueva conexión con el proveedor.

Puede crear una conexión de ExpressRoute con emparejamiento privado entre la red local y la nube de Microsoft de tres maneras diferentes:
  
- Colocalizada en un intercambio en la nube
    
- Conexiones Ethernet de punto a punto
    
- Redes (IP VPN) universales
    
**Figura 14: Utiliza ExpressRoute para conectarse a un VNet local entre**

![Figura 14: Uso de ExpressRoute para conectarse a una red virtual de Azure entre locales](images/7030bd39-69a6-4283-8567-3434e1ab6ba6.png)
  
La figura 14 muestra una red virtual entre locales y una conexión de ExpressRoute de un enrutador local a Microsoft Azure.
  
Para obtener más información, consulte [ExpressRoute para la conectividad en la nube de Microsoft](expressroute-for-microsoft-cloud-connectivity.md).
  
### <a name="step-5-determine-the-local-network-address-space-for-the-azure-gateway"></a>Paso 5: Determinar el espacio de direcciones de red local para la puerta de enlace de Azure.

Para el enrutamiento a una red local u otras redes virtuales desde una red virtual, Azure reenvía el tráfico a través de una puerta de enlace de Azure que coincide con el espacio de direcciones de red local asignado a la puerta de enlace.
  
**Figura 15: Espacio de direcciones red Local para un VNet entre locales**

![Figura 15: El espacio de direcciones de red local para una red virtual de Azure entre locales](images/e3af2652-8b8e-4551-9a0b-b550e6e7e3c0.png)
  
La figura 15 muestra una red virtual entre locales y el espacio de direcciones de red local en la puerta de enlace de Azure, que representa el espacio de direcciones accesible en la red local.  
  
El espacio de direcciones de red local se puede definir de las siguientes maneras:
  
- Opción 1: La lista de prefijos del espacio de direcciones que se necesita actualmente o que está en uso (podría ser necesario actualizar al agregar nuevas subredes).
    
- Opción 2: El espacio de direcciones local completo (solo es necesario actualizar cuando se agrega un espacio de direcciones nuevo).
    
Como la puerta de enlace de Azure no permite rutas resumidas, debe definir el espacio de direcciones de red local para la opción 2 de modo que no incluya el espacio de direcciones de red virtual.
  
**Figura 16: La dirección espacio hueco creado por el espacio de dirección VNet**

![Figura 16: El orificio del espacio de direcciones que crea el espacio de direcciones de red virtual](images/e79c4840-f9e3-4741-9b72-59db6043aefa.png)
  
La figura 16 muestra una representación de un espacio de direcciones con el espacio raíz y el espacio de direcciones de red virtual.
  
Aquí es un ejemplo de la definición de los prefijos de espacio de direcciones de red Local alrededor del espacio de direcciones "hueco" creado por el VNet:
  
- Una organización usa partes del espacio de direcciones privadas (10.0.0.0/8, 172.16.0.0/12 y 192.168.0.0/16) a través de su red local. Eligió la opción 2 y 10.100.100.0/24 como espacio de direcciones de red virtual.
    
La tabla 7 muestra los pasos y prefijos resultantes que definen el espacio de direcciones de red local en este ejemplo.
  
|**Paso**|**Resultados**|
|:-----|:-----|
|1. Mostrar los prefijos que no son el espacio raíz para el espacio de direcciones de red virtual.  <br/> |172.16.0.0/12 y 192.168.0.0/16  <br/> |
|2. lista de los prefijos no se superponen para variable octetos hasta, pero sin incluir el último octeto utilizado en el espacio de direcciones de VNet.  <br/> |10.0.0.0/16, 10.1.0.0/16... 10.99.0.0/16, 10.101.0.0/16... 10.254.0.0/16, 10.255.0.0/16 (255 prefijos, omitiendo 10.100.0.0/16)  <br/> |
|3. lista de los prefijos no se superponen en el último octeto utilizado del espacio de direcciones VNet.  <br/> |10.100.0.0/24, 10.100.1.0/24... 10.100.99.0/24, 10.100.101.0/24... 10.100.254.0/24, 10.100.0.255.0/24 (255 prefijos, omitiendo 10.100.100.0/24)  <br/> |
   
 **Tabla 7: Espacio de dirección Local del ejemplo de red**
  
### <a name="step-6-configure-on-premises-dns-servers-for-dns-replication-with-dns-servers-hosted-in-azure"></a>Paso 6: Configurar los servidores DNS locales para la replicación DNS con servidores DNS hospedados en Azure.

Para garantizar que los equipos locales puedan resolver los nombres de los servidores basados en Azure y que estos servidores puedan resolver los nombres de los equipos locales, configure:
  
- Los servidores DNS de la red virtual para que reenvíen a los servidores DNS locales
    
- La replicación DNS de las zonas apropiadas entre servidores DNS locales y en la red virtual
    
**Figura 17: Replicación de DNS y reenvío a un servidor DNS en un VNet entre locales**

![Figura 17: Reenvío y replicación DNS de un servidor DNS en una red virtual de Azure entre locales](images/ab55e5ce-ccb0-49d4-a301-657a727f97b2.png)
  
La figura 17 muestra una red virtual entre locales con servidores DNS en la red local y en una subred de la red virtual. El reenvío y la replicación de DNS se han configurado entre los dos servidores DNS.
  
### <a name="step-7-determine-the-use-of-forced-tunneling"></a>Paso 7: Determinar el uso de la tunelización forzada.

La ruta de sistema predeterminada para las subredes Azure señala a Internet. Para asegurarse de que todo el tráfico desde máquinas virtuales viaja a través de la conexión entre local, cree una tabla de enrutamiento con la ruta predeterminada que utiliza la puerta de enlace de Azure como su dirección de salto siguiente. A continuación, asociar la tabla de enrutamiento la subred. Esto se conoce como túnel de forzado. Para obtener más información, consulte [Configurar había forzado de túnel](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-forced-tunneling-rm).
  
**Figura 18: Rutas definidas por el usuario y túneles forzada de un VNet entre locales**

![Figura 18: Rutas definidas por el usuario y tunelización forzada en una red virtual de Azure entre locales](images/1e545ec6-c2d9-48d2-bb5e-e0a581fee004.png)
  
La figura 18 muestra un VNet entre locales con una ruta definida por el usuario para una subred que señala a la puerta de enlace de Azure.
  
## <a name="sharepoint-server-2016-farm-in-azure"></a>Granja de servidores de SharePoint Server 2016 en Azure
<a name="cross_prem"> </a>

Un ejemplo de una carga de trabajo de TI alojado en Azure IaaS intranet es una granja de SharePoint Server 2016 altamente disponible y de varios niveles.
  
**Figura 19: Una granja de SharePoint Server 2016 de intranet de gran disponibilidad en Azure IaaS**

![Una granja de servidores de SharePoint Server 2016 de alta disponibilidad en laaS de Azure](images/3a922e21-df91-455f-ba90-78abdd48d98d.png)
  
Figura 19 muestra los nueve servidores de una granja de SharePoint Server 2016 implementado en un VNet entre local que utiliza los equilibradores de carga interna para las capas de aplicaciones y datos. Para obtener más información, incluyendo el diseño paso a paso e instrucciones de implementación, consulte [SharePoint Server 2016 en Azure de Microsoft](https://technet.microsoft.com/library/mt779107%28v=office.16%29.aspx).
  
> [!TIP]
> Para crear una granja de SharePoint Server 2016 de servidor único en un VNet local entre simulado, consulte [Intranet 2016 de servidor de SharePoint en el entorno de pruebas y desarrollo de Azure](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx). 
  
Para obtener ejemplos adicionales de cargas de trabajo de TI implementados en máquinas virtuales en un Azure entre instalaciones virtual de red, vea [escenarios de nube híbrida de Azure IaaS](https://technet.microsoft.com/library/mt750502.aspx).
  
## <a name="see-also"></a>Vea también

<a name="cross_prem"> </a>

[Microsoft Cloud Networking para arquitectos profesionales](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Recursos de arquitectura de TI de la nube de Microsoft](microsoft-cloud-it-architecture-resources.md)

[Mapa de ruta de Enterprise Cloud de Microsoft: Recursos para los responsables de decisiones de TI](https://sway.com/FJ2xsyWtkJc2taRD)



