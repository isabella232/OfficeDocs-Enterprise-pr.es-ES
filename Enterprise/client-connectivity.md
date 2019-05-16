---
title: Conectividad de clientes
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/6/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 4232abcf-4ae5-43aa-bfa1-9a078a99c78b
description: 'Resumen: explica cómo se conectan los equipos cliente a los inquilinos de Office 365, según la ubicación del equipo cliente y el centro de recursos de inquilino de Office 365.'
ms.openlocfilehash: d101af5a0fdd4e29e366b34ad1ab682489f6b3ca
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068206"
---
# <a name="client-connectivity"></a>Conectividad de clientes

 **Resumen:** Explica cómo se conectan los equipos cliente a los inquilinos de Office 365, según la ubicación del equipo cliente y el centro de recursos de Office 365 arrendatario.
  
Office 365 reside en centros de información de Microsoft en todo el mundo, lo que ayuda a mantener el servicio en funcionamiento incluso cuando hay un problema importante en una región, como un terremoto o una interrupción de la alimentación. Cuando se conecte a su inquilino de Office 365, la conexión de cliente se dirigirá al centro de recursos apropiado en el que se hospeda el inquilino. Las reglas que determinan dónde se puede hospedar el inquilino están definidas por su acuerdo con Microsoft. Las reglas que determinan la forma en que el cliente adquiere los datos de esa ubicación del centro de datos dependen de la arquitectura del servicio que esté usando.
  
Por ejemplo, cuando inicia sesión en el portal de Office 365, normalmente se conecta al cliente del centro de recursos más cercano y, a continuación, se dirige según el servicio que use a continuación. Si inicia el correo electrónico, es posible que la conexión inicial para mostrar la interfaz de usuario siga apareciendo en el centro de datos más cercano, pero se puede abrir una segunda conexión entre el centro de datos más cercano y el centro de datos donde se encuentra el inquilino para mostrarle lo que hay en los correos electrónicos que lee. Microsoft opera una de las diez principales redes del mundo, lo que da como resultado conexiones increíblemente rápidas de centro de recursos y centro de recursos.
  
Después de leer el artículo, es probable que comprenda por qué no se proporcionan [direcciones URL y intervalos de direcciones IP de Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2) por centro de información, por lo que simplemente están muy interconectados y se confían entre sí para que sea factible.
  
Si está usando Azure ExpressRoute para Office 365, en la mayoría de los casos la conectividad pasará a través de una conexión privada a Office 365 en lugar de la conexión pública que se describe aquí. Los principios sobre cómo se conectan los clientes siguen siendo correctos. Obtenga más información sobre [Azure ExpressRoute para Office 365](azure-expressroute.md).
  
Para obtener más información sobre las solicitudes de red de Skype empresarial, lea el artículo [media Quality and Network Connectivity performance in Skype for Business online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).

||
|:-----|
| Este artículo forma parte de la planeación de [red y el ajuste del rendimiento de Office 365](https://aka.ms/tune).|

> [!NOTE]
> Nos preocupamos por administrar los datos de los clientes para que sean seguros y privados en nuestros centros de datos. Los detalles sobre los pasos necesarios para administrar la privacidad se incluyen en el [centro de confianza](https://go.microsoft.com/fwlink/?LinkID=397383).
  
## <a name="connecting-to-the-nearest-datacenter"></a>Conexión al centro de recursos más cercano

Este es el tipo de conexión más común y se usa en el portal de Office 365 y en Exchange Online. En esta situación, cuando los clientes intentan conectarse a Office 365, la consulta DNS de su equipo determina la región del mundo desde el que proviene su equipo y Office 365 redirige la solicitud al centro de recursos más cercano.
  
Las conexiones al portal se detienen en el centro de datos más cercano y el equipo cliente recibe información sobre el inquilino del cliente desde esa ubicación.
  
Exchange Online va un paso más adelante. Una vez que el equipo cliente se conecta al centro de información más cercano, un servidor de Exchange de ese centro de información se conecta al centro de información donde realmente se encuentra el inquilino, tal como se muestra en la *sección ¿Cómo funciona esta tarea* ? A continuación, los servidores de Exchange online del centro de recursos más cercano canalizan las solicitudes del equipo cliente al servidor de buzones de correo. Esto acelera la experiencia del equipo cliente al cambiar el pesado levantamiento de recuperar correos electrónicos y elementos del calendario a la red de Microsoft.
  
## <a name="how-does-this-work-for-standard-cloud-offerings"></a>¿Cómo funciona esto para las ofertas de nube estándar?

Este proceso de conexión es estándar para aplicaciones Web de gran valor, como Office 365. En esta sección, se describen e ilustran los pasos del proceso. Cuando el equipo cliente no está en la misma región que el inquilino, la conexión tiene un aspecto mucho diferente según el servicio al que se conecta el cliente.
  
 Este diagrama muestra a un cliente que usa una oferta estándar de Office 365 con un espacio empresarial en Norteamérica. En este escenario, la persona que realiza la solicitud ha viajado a Europa y está usando Office 365 desde esa ubicación.
  
1. El equipo cliente solicita a los servidores DNS locales la dirección IP asociada con Office 365.

2. Los servidores DNS locales del equipo cliente solicitan a los servidores DNS de Microsoft la dirección IP asociada con Office 365.

3. Los servidores DNS de Microsoft devuelven el nombre del servidor regional (según la ubicación de los servidores DNS del cliente) y el equipo cliente repite los pasos 1 y 2 para obtener la dirección IP del centro de recursos de Office 365 regional.

4. El equipo cliente se conecta a la dirección IP del centro de configuración regional.

5. Los servidores de Exchange Online establecen una conexión con el centro de recursos activo en el que reside el inquilino del cliente.

![Centro de datos regional más próximo](media/4ea108e9-a299-4e3d-b0d3-469b434ff899.png)
  
## <a name="how-does-this-work-for-sovereign-cloud-offerings"></a>¿Cómo funciona esto con las ofertas de nube soberano?

Esta conexión es ligeramente diferente para las ofertas de nube soberano como Office 365 operado por 21 ViaNet. Con el inquilino en una instancia soberano de Office 365, los servidores de Office 365 más cercanos que aceptarán conexiones de portal serán los servidores dentro de la región soberano donde reside el inquilino. De forma similar, los clientes que acceden a SharePoint Online en nuestra nube soberano o a las ofertas estándar se dirigirán a los servidores front-end donde reside el inquilino. Consulte conectarse al centro de recursos activo a continuación.
  
1. El equipo cliente solicita a los servidores DNS locales la dirección IP asociada con Office 365.

2. Los servidores DNS locales del equipo cliente solicitan a los servidores DNS de Microsoft la dirección IP asociada con Office 365.

3. Los servidores DNS de Microsoft devuelven el nombre del servidor regional (según la ubicación de los servidores DNS del cliente) y el equipo cliente repite los pasos 1 y 2 para obtener la dirección IP del centro de recursos de Office 365 regional.

4. El equipo cliente se conecta a la dirección IP del centro de configuración regional.

5. Los servidores de Exchange Online establecen una conexión con el centro de recursos activo en el que reside el inquilino del cliente.

![Centro de datos regional más próximo de EE. UU.](media/c0628c54-0059-48c5-8a0f-41bf392ee182.png)
  
## <a name="connecting-to-the-active-datacenter"></a>Conexión al centro de recursos activo

La conexión al centro de datos activo está diseñada para cargas de trabajo de transferencia de datos más pesadas y actualmente la usa SharePoint Online. En esta situación, cuando los clientes intentan conectarse a Office 365, su explorador se redirige al centro de recursos activo para su espacio empresarial de SharePoint Online.
  
## <a name="how-does-this-work"></a>¿Cómo funciona?

Cuando el equipo cliente se conecta a SharePoint Online desde una región distinta, la conexión se redirige al centro de recursos de SharePoint Online activo. En este escenario, el cliente usa una oferta estándar, lo que da como resultado las conexiones del portal restantes locales y las conexiones de SharePoint Online dirigidas al centro de recursos activo.
  
1. El equipo cliente solicita a los servidores DNS locales la dirección IP asociada con Office 365.

2. Los servidores DNS locales del equipo cliente solicitan a los servidores DNS de Microsoft la dirección IP asociada con Office 365.

3. Los servidores DNS de Microsoft devuelven el nombre del servidor del centro de recursos de SharePoint Online activo (en función de la ubicación del inquilino Office 365 del cliente) y el equipo cliente repite los pasos 1 y 2 para obtener la dirección IP del centro de seguridad de Office 365 activo.

4. El equipo cliente se conecta a la dirección IP del centro de recursos activo.

![Centro de datos activo de EE. UU.](media/c6d2933f-49cb-4536-bea7-c868707755ae.png)
  
## <a name="connecting-over-virtual-private-networks-vpns"></a>Conexión a través de redes privadas virtuales (VPN)

Este tipo de conexión solo se aplica cuando los equipos cliente usan una red privada virtual (VPN). En realidad, el comportamiento de Office 365 no se cambia simplemente porque se usa una VPN, pero las VPN se suelen usar para controlar cómo los equipos cliente establecen conexiones con Office 365 y, normalmente, se obtiene una disminución de la experiencia, por lo que es importante abarcar.
  
## <a name="how-does-this-work"></a>¿Cómo funciona?

Cuando el equipo cliente establece una conexión VPN con una oficina corporativa en una región distinta, se usan los servidores DNS de esa oficina en lugar de los servidores DNS en la ubicación del equipo cliente. En la mayoría de los casos, esta conexión adicional a través de la VPN reducirá la experiencia de Office 365. Los servicios de Office 365 están optimizados para atender las conexiones de clientes lo más cerca posible del usuario final. Muchos servicios aprovechan la red de Azure Edge, las redes de entrega de contenido y la capacidad de red confiable en la red Microsoft para proporcionar la mejor experiencia posible al usuario cuando las solicitudes de red para servicios de Office 365 se realizan tan cerca del equipo cliente posible.
  
1. El equipo cliente solicita a los servidores DNS de la VPN la dirección IP asociada con Office 365.

2. Los servidores DNS de VPN del equipo cliente solicitan a los servidores DNS de Microsoft la dirección IP asociada con Office 365.

3. Los servidores DNS de Microsoft devuelven el nombre del servidor regional (según la ubicación de los servidores DNS de la VPN) y el equipo cliente repite los pasos 1 y 2 para obtener la información de la dirección IP del centro de datos de Office 365 regional.

4. El equipo cliente se conecta a la dirección IP del centro de usuarios que está más cerca de la oficina corporativa con la que estableció una conexión VPN.

![Conectividad VPN de centro de datos](media/b5f4c06c-65a3-462d-aae8-9a4602dd8d9e.png)
  
Este es un vínculo breve que se puede usar para volver: [https://aka.ms/o365clientconnectivity](https://aka.ms/o365clientconnectivity)
  
## <a name="see-also"></a>Vea también

[Administrar puntos de conexión de Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Conectividad de red a Office 365](network-connectivity.md)
