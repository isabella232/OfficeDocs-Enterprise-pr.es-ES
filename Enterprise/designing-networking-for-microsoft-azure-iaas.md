---
title: Diseño de redes para IaaS de Microsoft Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 9cb70c9d-9ed9-47cc-af5a-6403d87d3372
description: 'Resumen: Aprenda a diseñar redes optimizadas para cargas de trabajo en IaaS de Microsoft Azure.'
ms.openlocfilehash: c41e92445dd01a94b7d305b521bbd4330311fcb4
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491146"
---
# <a name="designing-networking-for-microsoft-azure-iaas"></a>Diseño de redes para IaaS de Microsoft Azure

 **Resumen:** Comprenda cómo diseñar redes optimizadas para cargas de trabajo en IaaS de Microsoft Azure.
  
La optimización de las redes para las cargas de trabajo de TI hospedadas en IaaS de Azure requiere un conocimiento de las redes virtuales (VNets) de Azure, los espacios de direcciones, el enrutamiento, el DNS y el equilibrio de carga.
  
## <a name="planning-steps-for-any-vnet"></a>Pasos de planeación para cualquier red virtual

Siga estos pasos para cualquier tipo de red virtual.
  
### <a name="step-1-prepare-your-intranet-for-microsoft-cloud-services"></a>Paso 1: Preparar la intranet para los servicios en la nube de Microsoft.

Vea la sección **Pasos para preparar la red para Servicios en la nube de Microsoft** en [Elementos comunes de conectividad de Microsoft Cloud](common-elements-of-microsoft-cloud-connectivity.md).
  
### <a name="step-2-optimize-your-internet-bandwidth"></a>Paso 2: Optimizar el ancho de banda de Internet.

Para optimizar el ancho de banda de Internet, siga los pasos 2 a 4 de la sección **Pasos para preparar la red para los servicios SaaS de Microsoft** del artículo [Diseño de redes para SaaS de Microsoft](designing-networking-for-microsoft-saas.md).
  
### <a name="step-3-determine-the-type-of-vnet-cloud-only-or-cross-premises"></a>Paso 3: Determinar el tipo de red virtual (solo nube o entre locales).

Una red virtual de solo nube no tiene conexión a una red local. Aquí le mostramos un ejemplo.
  
**Figura 1: Una red virtual de solo nube**

![Figura 1: una red virtual de solo nube en Azure](media/8be19104-02b3-4a7f-b0a0-30d6fcf8890b.png)
  
La figura 1 muestra un conjunto de máquinas virtuales en una red virtual de solo nube.
  
Una red virtual entre locales tiene una conexión VPN de sitio a sitio (S2S) o de ExpressRoute a una red local a través de una puerta de enlace de Azure. Aquí le mostramos un ejemplo.
  
**Figura 2: Una red virtual entre locales**

![Figura 2: una red virtual entre locales en Azure](media/caacf007-e0dc-45d3-9531-441109776d25.png)
  
La figura 2 muestra un conjunto de máquinas virtuales en una red virtual entre locales, que está conectada a una red local.
  
Consulte la sección adicional [Pasos de planeación para una red virtual entre locales](designing-networking-for-microsoft-azure-iaas.md#cross_prem) de este artículo.
  
### <a name="step-4-determine-the-address-space-of-the-vnet"></a>Paso 4: Determinar el espacio de direcciones de la red virtual.

La tabla 1 muestra los espacios de direcciones para los distintos tipos de redes virtuales.
  
|**Tipo de red virtual**|**Espacio de direcciones de la red virtual**|
|:-----|:-----|
|Solo de nube  <br/> |Espacio de direcciones privadas arbitrarias  <br/> |
|Basada solo en la nube e interconectada  <br/> |Privado arbitrario, pero no se superpone con otras redes virtuales conectadas  <br/> |
|Entre locales  <br/> |Privada, pero sin que se superponga con redes locales  <br/> |
|Local e interconectada  <br/> |Privada, pero sin que se superponga con otras redes locales y virtuales conectadas  <br/> |
   
 **Tabla 1: Tipos de redes virtuales y el espacio de direcciones correspondiente**
  
El DHCP asigna a las máquinas virtuales una configuración de direcciones desde el espacio de direcciones de la subred:
  
- Dirección/máscara de subred
    
- Puerta de enlace predeterminada
    
- Direcciones IP del servidor DNS
    
También puede reservar una dirección IP estática.
  
A las máquinas virtuales también se les puede asignar una dirección IP pública, ya sea individualmente o desde el servicio en la nube que las contiene (solo para máquinas de implementación clásicas).
  
### <a name="step-5-determine-the-subnets-within-the-vnet-and-the-address-spaces-assigned-to-each"></a>Paso 5: Determinar las subredes de la red virtual y los espacios de direcciones asignados a cada una.

Hay dos tipos de subredes en una red virtual: una subred de puerta de enlace y una subred de hospedaje de máquina virtual.
  
**Figura 3: Los dos tipos de subredes de Azure**

![Figura 3: Los dos tipos de subredes de Azure](media/2eaa512d-1293-4e9b-b927-6bfe0fc0acb4.png)
  
La figura 3 muestra una VNet que contiene una subred de puerta de enlace que tiene una puerta de enlace de Azure y un conjunto de subredes de hospedaje de máquina virtual que contienen máquinas virtuales.
  
Azure necesita la subred de puerta de enlace de Azure para hospedar las dos máquinas virtuales de su puerta de enlace de Azure. Especifique un espacio de direcciones que tenga una longitud de prefijo de, al menos, 29 bits (ejemplo: 192.168.15.248/29). Se recomienda una longitud de prefijo de 27 bits o más pequeña, especialmente si está pensando en usar ExpressRoute.
  
Un procedimiento recomendado para determinar el espacio de direcciones de la subred de la puerta de enlace de Azure es:
  
1. Decida el tamaño de la subred de puerta de enlace.
    
2. En los bits variables del espacio de direcciones de la red virtual, establezca los bits usados para la subred de puerta de enlace en 0 y los bits restantes en 1.
    
3. Convierta a decimales y expréselo como un espacio de direcciones con la longitud de prefijo establecida en el tamaño de la subred de puerta de enlace.
    
Con este método, el espacio de direcciones de la subred de puerta de enlace siempre está en el extremo más alejado del espacio de direcciones de la red virtual.
  
En este ejemplo, se define el prefijo de dirección que corresponde a la subred de puerta de enlace: el espacio de direcciones de la red virtual es 10.119.0.0/16. La organización usará inicialmente una conexión VPN de sitio a sitio, pero al final empleará ExpressRoute. La tabla 2 muestra los pasos y los resultados de determinar el prefijo de dirección de la subred de puerta de enlace en una notación de prefijos de red (también conocido como CIDR).

Estos son los pasos y el ejemplo de cómo determinar el prefijo de la dirección de subred de la puerta de enlace:

1. Decida el tamaño de la subred de puerta de enlace. Para nuestro ejemplo, elegimos/28.
2. Establezca los bits de la parte variable del espacio de direcciones de la red virtual (b) en 0 para los bits de subred de la puerta de enlace (G); en caso contrario, 1 (V). Para nuestro ejemplo, estamos usando el espacio de direcciones de 10.119.0.0/16 para la VNet.
<br/>
<br/>10,119. bbbbbbbb. bbbbbbbb
<br/>10,119. VVVVVVVV. VVVVGGGG
<br/>10,119. 11111111. 11110000
<br/><br/>
3. ConVierta el resultado del paso 2 a decimal y Express como un espacio de direcciones. En nuestro ejemplo, 10,119. 11111111. 11110000 es 10.119.255.240 y con la longitud de prefijo del paso 1 (28 en nuestro ejemplo), el prefijo de dirección de subred de la puerta de enlace resultante es 10.119.255.240/28.
  
Para obtener más información, vea [calculadora de espacio de direcciones para subredes de puerta de enlace de Azure](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) .
  
En las subredes de hospedaje de máquina virtual es donde se colocan las máquinas virtuales de Azure, lo cual se puede hacer siguiendo las instrucciones locales típicas, como un rol común o el nivel de una aplicación o para el aislamiento de la subred.
  
Azure usa las tres primeras direcciones de cada subred. Por lo tanto, el número de direcciones posibles en una subred de Azure es 2<sup>n</sup> -5, donde n es el número de bits de host. La tabla 3 muestra la gama de máquinas virtuales y el número de bits de hosts necesarios, y el tamaño de la subred correspondiente.
  
|**Máquinas virtuales requeridas**|**Bits de host**|**Tamaño de la subred**|
|:-----|:-----|:-----|
|1-3  <br/> |3  <br/> |/29  <br/> |
|4-11  <br/> |4   <br/> |/28  <br/> |
|12-27  <br/> |5   <br/> |/27  <br/> |
|28-59  <br/> |6   <br/> |/26  <br/> |
|60-123  <br/> |7   <br/> |/25  <br/> |
   
 **Tabla 3: Requisitos de la máquina virtual y tamaños de subred**
  
Para obtener más información acerca de la cantidad máxima de máquinas virtuales en una subred o VNet, consulte [límites de red](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).
  
Para obtener más información, vea [planeación y diseño de redes virtuales de Azure](https://azure.microsoft.com/documentation/articles/virtual-network-vnet-plan-design-arm/).
  
### <a name="step-6-determine-the-dns-server-configuration-and-the-addresses-of-the-dns-servers-to-assign-to-vms-in-the-vnet"></a>Paso 6: Determinar la configuración del servidor DNS y las direcciones de los servidores DNS para asignar a las máquinas virtuales en la red virtual.

Azure asigna a las máquinas virtuales las direcciones de los servidores DNS mediante DHCP. Los servidores DNS pueden suministrarlos:
  
- Azure: se proporciona un registro de nombres locales y una resolución de nombres de Internet
    
- Usted: se proporciona un registro de nombres locales o de intranet y una resolución de nombres de Internet o de intranet
    
En la tabla 4, se muestran las diferentes configuraciones de los servidores DNS para cada tipo de red virtual.
    
|**Tipo de red virtual**|**Servidor DNS**|
|:-----|:-----|
|Solo de nube  <br/> |Suministrado por Azure para la resolución de nombres de Internet y locales  <br/> Máquina virtual de Azure para la resolución de nombres de Internet y locales (reenvío DNS)  <br/> |
|Entre locales  <br/> |Local para la resolución de nombres locales y de intranet  <br/> Máquina virtual de Azure para la resolución de nombres de Internet y locales (replicación y reenvío DNS)  <br/> |
   
 **Tabla 4: Opciones del servidor DNS para los dos tipos diferentes de redes virtuales**
  
Para obtener más información, vea [resolución de nombres para máquinas virtuales e instancias de rol](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances).
  
### <a name="step-7-determine-the-load-balancing-configuration-internet-facing-or-internal"></a>Paso 7: Determinar la configuración de equilibrio de carga (accesible desde Internet o interna).

En algunos casos, queremos distribuir el tráfico entrante a un conjunto de servidores que tienen el mismo rol. IaaS de Azure dispone de una instalación integrada para hacer esto con cargas de tráfico accesibles desde Internet e internas.
  
El equilibrio de carga de Azure accesible desde Internet distribuye aleatoriamente el tráfico entrante no solicitado de Internet a los miembros de un conjunto de carga equilibrada. 
  
**Figura 4: Un equilibrador de carga externo en Azure**

![Figura 4: Un equilibrador de carga externo en Azure](media/eb5945e5-0c2b-40f1-b9ed-54bb2b0f9e59.png)
  
La figura 4 muestra un equilibrador de carga externo en Azure que distribuye el tráfico entrante en una regla de NAT de entrada o un punto de conexión a un conjunto de máquinas virtuales en un conjunto de carga equilibrada.
  
El equilibrio de carga interno de Azure distribuye aleatoriamente el tráfico entrante no solicitado desde otras máquinas virtuales de Azure o desde equipos de la intranet a los miembros de un conjunto de equilibrio de carga.  
  
**Figura 5: Un equilibrador de carga interno en Azure**

![Figura 5: Un equilibrador de carga interno en Azure](media/d1451b73-6465-449d-b3e6-22160ce51f35.png)
  
La figura 5 muestra un equilibrador de carga interno en Azure que distribuye el tráfico entrante en una regla de NAT de entrada o un punto de conexión a un conjunto de máquinas virtuales en un conjunto de carga equilibrada.
  
Para obtener más información, vea equilibrador de [carga de Azure](https://docs.microsoft.com/azure/load-balancer/load-balancer-overview).
  
### <a name="step-8-determine-the-use-of-virtual-appliances-and-user-defined-routes"></a>Paso 8: Determinar el uso de las aplicaciones virtuales y las rutas definidas por el usuario.

Si tiene que reenviar el tráfico a aplicaciones virtuales de la red virtual, puede que deba agregar a una subred una o varias rutas que haya definido el usuario.
  
**Figura 6: Las aplicaciones virtuales y las rutas definidas por el usuario en Azure**

![Figura 6: Las aplicaciones virtuales y las rutas definidas por el usuario en Azure](media/f181d0f4-ebf9-439e-9c98-dec17428c32b.png)
  
La figura 6 muestra una red virtual entre locales y una ruta definida por el usuario asignada a una subred de hospedaje de máquina virtual que apunta a una aplicación virtual.
  
Para obtener más información, vea [rutas definidas por el usuario y el reenvío IP](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview).
  
### <a name="step-9-determine-how-computers-from-the-internet-will-connect-to-virtual-machines"></a>Paso 9: Determinar cómo se conectarán los equipos de Internet a las máquinas virtuales.

Hay varias maneras de proporcionar acceso a Internet a las máquinas virtuales de una red virtual, que incluye el acceso desde la red de la organización a través del servidor proxy u otro dispositivo perimetral.
  
La tabla 5 recoge los métodos para filtrar o inspeccionar el tráfico entrante no solicitado.
  
|**Método**|**Modelo de implementación**|
|:-----|:-----|
|1. Puntos de conexión y ACL configurados en los servicios en la nube  <br/> |SICA  <br/> |
|2. Grupos de seguridad de red  <br/> |Administrador de recursos y clásico  <br/> |
|3. Equilibrador de carga accesible desde Internet con reglas de NAT entrantes  <br/> |Administrador de recursos  <br/> |
|4. dispositivos de seguridad de red en Azure Marketplace (no se muestra)  <br/> |Administrador de recursos y clásico  <br/> |
   
 **Tabla 5: Métodos de conexión a máquinas virtuales y sus correspondientes modelos de implementación de Azure**
  
**Figura 7: Conexión a máquinas virtuales de Azure a través de Internet**

![Figura 7: Conexión a máquinas virtuales de Azure a través de Internet](media/c5e3531b-170a-4482-a6ff-fb8fbbe81b35.png)
  
La figura 7 muestra un equipo conectado a Internet que se conecta a una máquina virtual en un servicio en la nube usando un punto de conexión, una máquina virtual de una subred que usa un grupo de seguridad de red y una máquina virtual de una subred que usa un equilibrador de carga externo y reglas de NAT entrantes.
  
La seguridad adicional la proporcionan:
  
- Conexiones de Escritorio remoto y SSH, que se autentican y se cifran.
    
- Sesiones remotas de PowerShell, que se autentican y se cifran.
    
- Modo de transporte IPsec, que puede usar para el cifrado de extremo a extremo.
    
- Protección DDoS de Azure, que ayuda a prevenir ataques internos y externos
    
Para obtener más información, consulte [seguridad en la nube de Microsoft para arquitectos de empresa](https://aka.ms/cloudarchsecurity) y [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/).
  
### <a name="step-10-for-multiple-vnets-determine-the-vnet-to-vnet-connection-topology"></a>Paso 10: Para varias redes virtuales, determinar la topología de conexión de una red virtual a otra.

Las redes virtuales pueden conectarse entre sí mediante topologías como las que se usan para conectar los sitios de una organización.
  
Una configuración de encadenamiento conecta las redes virtuales de una serie.
  
**Figura 8: Una configuración de encadenamiento para redes virtuales**

![Figura 8: una configuración de encadenamiento para redes virtuales de Azure](media/264d5dd4-06c5-483f-9428-a18cc1f68ac1.png)
  
La figura 8 muestra cinco redes virtuales conectadas en serie con una configuración de encadenamiento.
  
Una configuración de concentrador y radio conecta varias redes virtuales a un conjunto de redes virtuales centrales, que están conectadas entre sí.
  
**Figura 9: Una configuración de concentrador y radio para redes virtuales**

![Figura 9: una configuración de concentrador y radio para redes virtuales de Azure](media/dd442a38-5b76-4ac5-b743-8fc7711a91ba.png)
  
La figura 9 muestra seis redes virtuales, dos redes virtuales son concentradores conectados entre sí y también otras dos son redes virtuales de radio.
  
Una configuración de malla completa conecta las redes virtuales entre sí.
  
**Figura 10: Una configuración de malla completa para redes virtuales**

![Figura 10: una configuración de malla para redes virtuales de Azure](media/9dda0738-10db-4a63-95b3-79851a399b71.png)
  
La figura 10 muestra cuatro redes virtuales que están conectadas entre sí y que usan un total de seis conexiones de red virtual a red virtual.
  
## <a name="planning-steps-for-a-cross-premises-vnet"></a>Pasos de planeación para una red virtual entre locales
<a name="cross_prem"> </a>

Siga estos pasos para una red virtual entre locales.
  
> [!TIP]
> Para crear un entorno de prueba y desarrollo simulado entre locales, vea [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md). 
  
### <a name="step-1-determine-the-cross-premises-connection-to-the-vnet-s2s-vpn-or-expressroute"></a>Paso 1: Determinar la conexión entre locales a la red virtual (VPN S2S o ExpressRoute).

En la tabla 6 se recogen los distintos tipos de conexiones.
  
|**Tipo de conexión**|**Finalidad**|
|:-----|:-----|
|VPN sitio a sitio (S2S)  <br/> |Conecte los sitios de 1-10 (incluidas otras redes virtuales) a una única VNet.  <br/> |
|ExpressRoute  <br/> |Un vínculo seguro y privado a Azure a través de un proveedor de intercambio de Internet (IXP) o un proveedor de servicio de red (NSP).  <br/> |
|VPN punto a sitio (P2S)  <br/> |Conecta un solo equipo a una red virtual.  <br/> |
|Dispositivos VPN para el emparejamiento de VNET o de red virtual a red virtual (V2V)   <br/> |Conecta una red virtual a otra.  <br/> |
   
 **Tabla 6: Los tipos de conexiones para redes virtuales entre locales**
  
Para obtener más información sobre el número máximo de conexiones, consulte [límites de red](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).
  
Para obtener más información acerca de los dispositivos VPN, vea [dispositivos VPN para conexiones de red virtual de sitio a sitio](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).
  
Para obtener más información sobre el emparejamiento de VNet, consulte [emparejamiento de Vnet](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview).
  
**Figura 11: Las cuatro maneras de conectarse a una red virtual entre locales**

![Figura 11: las tres maneras de conectarse a una red virtual de Azure entre locales](media/d5d4a625-cfbd-4a77-9159-eaca69d07e93.png)
  
La figura 11 muestra una red virtual con los cuatro tipos de conexiones: una conexión de P2S de un equipo, una conexión VPN S2S desde una red local, una conexión de ExpressRoute desde una red local y una conexión de red virtual a red virtual desde otra red virtual. 
  
Puede conectarse a las máquinas virtuales de una red virtual de las maneras siguientes:
  
- Administración de máquinas virtuales de redes virtuales desde la red local o Internet
    
- Acceso a cargas de trabajo de TI desde la red local
    
- Ampliación de la red a través de redes virtuales adicionales
    
La seguridad en las conexiones se consigue mediante lo siguiente:
  
- P2S usa el protocolo de túnel de sockets de seguros (SSTP)  
    
- S2S y conexiones VPN de red virtual a red virtual usan el modo de túnel IPsec con AES256
    
- ExpressRoute es una conexión WAN privada
    
Para obtener más información, consulte [seguridad en la nube de Microsoft para arquitectos de empresa](https://aka.ms/cloudarchsecurity) y [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/).
  
### <a name="step-2-determine-the-on-premises-vpn-device-or-router"></a>Paso 2: Determinar el dispositivo o enrutador VPN local.

El dispositivo o enrutador VPN local actúa como:
  
- Par IPsec que finaliza la conexión de VPN S2S desde la puerta de enlace de Azure.
    
- Par BPG y punto de finalización para la conexión de ExpressRoute de emparejamiento privado.
    
**Figura 12: El dispositivo o enrutador de VPN local**

![Figura 12: El dispositivo o enrutador de VPN local](media/bd221468-a660-4730-aa55-0426986480b9.png)
  
La figura 12 muestra una red virtual entre locales conectada a un enrutador o dispositivo VPN local.
  
Para obtener más información, vea [acerca de la puerta de enlace VPN](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways).
  
### <a name="step-3-add-routes-to-your-intranet-to-make-the-address-space-of-the-vnet-reachable"></a>Paso 3: agregar rutas a la intranet para que el espacio de direcciones de la red virtual sea accesible.

El enrutamiento a redes virtuales desde ubicaciones locales consiste en lo siguiente:
  
1. Una ruta para el espacio de direcciones de red virtual que apunte al dispositivo VPN.
    
2. Una ruta para el espacio de direcciones de red virtual en el dispositivo VPN que apunte a la conexión VPN S2S o de ExpressRoute
    
**Figura 13: Las rutas locales necesarias para hacer que una red virtual sea accesible**

![Figura 13: las rutas locales necesarias para hacer que una red virtual de Azure sea accesible](media/7a1e20c1-fbc4-4cb9-9961-735da4e23307.png)
  
En la figura 13, se muestra la información de enrutamiento que necesitan los enrutadores locales y el enrutador o dispositivo VPN que representa el espacio de direcciones de la red virtual.
  
### <a name="step-4-for-expressroute-plan-for-the-new-connection-with-your-provider"></a>Paso 4: Para ExpressRoute, planear la nueva conexión con el proveedor.

Puede crear una conexión de ExpressRoute con emparejamiento privado entre la red local y la nube de Microsoft de tres maneras diferentes:
  
- Colocalizada en un intercambio en la nube
    
- Conexiones Ethernet de punto a punto
    
- Redes (IP VPN) universales
    
**Figura 14: Uso de ExpressRoute para conectarse a una red virtual entre locales**

![Figura 14: uso de ExpressRoute para conectarse a una red virtual de Azure entre locales](media/7030bd39-69a6-4283-8567-3434e1ab6ba6.png)
  
La figura 14 muestra una red virtual entre locales y una conexión de ExpressRoute de un enrutador local a Microsoft Azure.
  
Para obtener más información, consulte [ExpressRoute para la conectividad en la nube de Microsoft](expressroute-for-microsoft-cloud-connectivity.md).
  
### <a name="step-5-determine-the-local-network-address-space-for-the-azure-gateway"></a>Paso 5: Determinar el espacio de direcciones de red local para la puerta de enlace de Azure.

Para el enrutamiento a una red local u otras redes virtuales desde una red virtual, Azure reenvía el tráfico a través de una puerta de enlace de Azure que coincide con el espacio de direcciones de red local asignado a la puerta de enlace.
  
**Figura 15: El espacio de direcciones de red local para una red virtual entre locales**

![Figura 15: el espacio de direcciones de red local para una red virtual de Azure entre locales](media/e3af2652-8b8e-4551-9a0b-b550e6e7e3c0.png)
  
La figura 15 muestra una red virtual entre locales y el espacio de direcciones de red local en la puerta de enlace de Azure, que representa el espacio de direcciones accesible en la red local.  
  
Puede definir el espacio de direcciones de red local de las siguientes formas:
  
- Opción 1: La lista de prefijos del espacio de direcciones que se necesita actualmente o que está en uso (podría ser necesario actualizar al agregar nuevas subredes).
    
- Opción 2: El espacio de direcciones local completo (solo es necesario actualizar cuando se agrega un espacio de direcciones nuevo).
    
Como la puerta de enlace de Azure no permite rutas resumidas, debe definir el espacio de direcciones de red local para la opción 2 de modo que no incluya el espacio de direcciones de red virtual.
  
**Figura 16: El orificio del espacio de direcciones que crea el espacio de direcciones de red virtual**

![Figura 16: el orificio del espacio de direcciones que crea el espacio de direcciones de la red virtual](media/e79c4840-f9e3-4741-9b72-59db6043aefa.png)
  
La figura 16 muestra una representación de un espacio de direcciones con el espacio raíz y el espacio de direcciones de red virtual.
  
A continuación, se muestra un ejemplo de cómo definir los prefijos para el espacio de direcciones de red local alrededor del espacio de direcciones "agujero" creado por la red virtual:
  
- Una organización usa partes del espacio de direcciones privadas (10.0.0.0/8, 172.16.0.0/12 y 192.168.0.0/16) a través de su red local. Eligió la opción 2 y 10.100.100.0/24 como espacio de direcciones de red virtual.
    
La tabla 7 muestra los pasos y prefijos resultantes que definen el espacio de direcciones de red local en este ejemplo.
  
|**Paso**|**Resultados**|
|:-----|:-----|
|1. Mostrar los prefijos que no son el espacio raíz para el espacio de direcciones de red virtual.  <br/> |172.16.0.0/12 y 192.168.0.0/16  <br/> |
|2. enumerar los prefijos que no se superponen para los octetos variables hasta el último octeto usado en el espacio de direcciones de red virtual, pero sin incluirlo.  <br/> |10.0.0.0/16, 10.1.0.0/16... 10.99.0.0/16, 10.101.0.0/16... 10.254.0.0/16, 10.255.0.0/16 (255 prefijos, omitir 10.100.0.0/16)  <br/> |
|3. enumerar los prefijos que no se superponen en el último octeto usado del espacio de direcciones de la red virtual.  <br/> |10.100.0.0/24, 10.100.1.0/24... 10.100.99.0/24, 10.100.101.0/24... 10.100.254.0/24, 10.100.0.255.0/24 (255 prefijos, omitir 10.100.100.0/24)  <br/> |
   
 **Tabla 7: Ejemplo de espacio de red de dirección local**
  
### <a name="step-6-configure-on-premises-dns-servers-for-dns-replication-with-dns-servers-hosted-in-azure"></a>Paso 6: Configurar los servidores DNS locales para la replicación DNS con servidores DNS hospedados en Azure.

Para garantizar que los equipos locales puedan resolver los nombres de los servidores basados en Azure y que estos servidores puedan resolver los nombres de los equipos locales, configure:
  
- Los servidores DNS de la red virtual para que reenvíen a los servidores DNS locales
    
- La replicación DNS de las zonas apropiadas entre servidores DNS locales y en la red virtual
    
**Figura 17: Reenvío y replicación DNS de un servidor DNS en una red virtual entre locales**

![Figura 17: reenvío y replicación DNS de un servidor DNS en una red virtual de Azure entre locales](media/ab55e5ce-ccb0-49d4-a301-657a727f97b2.png)
  
La figura 17 muestra una red virtual entre locales con servidores DNS en la red local y en una subred de la red virtual. El reenvío y la replicación de DNS se han configurado entre los dos servidores DNS.
  
### <a name="step-7-determine-the-use-of-forced-tunneling"></a>Paso 7: Determinar el uso de la tunelización forzada.

La ruta predeterminada del sistema para las subredes de Azure apunta a Internet. Para asegurarse de que todo el tráfico de las máquinas virtuales se recorre a través de la conexión entre locales, cree una tabla de enrutamiento con la ruta predeterminada que use la puerta de enlace de Azure como su dirección de próximo salto. A continuación, asocie la tabla de rutas con la subred. Esto se conoce como tunelización forzada. Para obtener más información, consulte [configurar túneles forzados](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-forced-tunneling-rm).
  
**Figura 18: Rutas definidas por el usuario y tunelización forzada en una red virtual entre locales**

![Figura 18: rutas definidas por el usuario y tunelización forzada para una red virtual de Azure entre locales](media/1e545ec6-c2d9-48d2-bb5e-e0a581fee004.png)
  
La figura 18 muestra una red virtual entre locales con una ruta definida por el usuario para una subred que apunta a la puerta de enlace de Azure.
  
## <a name="sharepoint-server-2016-farm-in-azure"></a>Granja de servidores de SharePoint Server 2016 en Azure
<a name="cross_prem"> </a>

Un ejemplo de una carga de trabajo de TI de intranet hospedada en IaaS de Azure es una granja de servidores de SharePoint Server 2016 de varios niveles y altamente disponible.
  
**Figura 19: Una granja de SharePoint Server 2016 de la intranet y de alta disponibilidad en IaaS de Azure**

![Una granja de servidores de alta disponibilidad de SharePoint Server 2016 en IaaS de Azure](media/3a922e21-df91-455f-ba90-78abdd48d98d.png)
  
La figura 19 muestra los nueve servidores de una granja de servidores de SharePoint Server 2016 implementada en una red virtual entre locales que usa equilibradores de carga internos para los niveles front-end y de datos. Para obtener más información, incluidas las instrucciones paso a paso para la implementación y el diseño, vea [SharePoint Server 2016 en Microsoft Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure).
  
> [!TIP]
> Para crear una granja de servidores de SharePoint Server 2016 de un solo servidor en una red virtual entre locales simulada, vea [intranet SharePoint server 2016 en el entorno de prueba y desarrollo de Azure](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment). 
  
Para obtener ejemplos adicionales de cargas de trabajo de ti implementadas en máquinas virtuales en una red virtual de Azure entre locales, vea [escenarios de nube híbrida para IaaS de Azure](https://docs.microsoft.com/office365/enterprise/hybrid-cloud-scenarios-for-azure-iaas).
  
## <a name="see-also"></a>Ver también

[Microsoft Cloud Networking para arquitectos profesionales](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Recursos de arquitectura de TI de Microsoft Cloud](microsoft-cloud-it-architecture-resources.md)


