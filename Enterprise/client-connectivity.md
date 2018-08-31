---
title: Conectividad de clientes
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/6/2017
ms.audience: ITPro
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
description: 'Resumen: explica de qué manera los equipos cliente se conectan con los inquilinos de Office 365, según la ubicación del equipo cliente y el centro de datos del inquilino de Office 365.'
ms.openlocfilehash: 9455147e70a391619e1602f2e36d9162ff2c0928
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223042"
---
# <a name="client-connectivity"></a>Conectividad de clientes

 **Resumen:** explica de qué manera los equipos cliente se conectan con los inquilinos de Office 365, según la ubicación del equipo cliente y el centro de datos del inquilino de Office 365.
  
Office 365 reside en centros de datos Microsoft todo el mundo que ayudan a mantener el servicio de copia de seguridad y la ejecución incluso cuando hay un problema importante en una región, como un terremoto o un corte de alimentación. Cuando se conecta a su inquilino de Office 365, la conexión del cliente se dirigirá al centro de datos adecuado donde se hospeda el inquilino. Las reglas que determinan dónde se puede hospedar el inquilino se definen mediante el contrato de Microsoft. Las reglas que determinan cómo el cliente adquiere los datos desde esa ubicación de centro de datos dependen de la arquitectura del servicio que está utilizando.
  
Por ejemplo, cuando se inicia sesión en el portal de Office 365, está suela estar conectado al centro de datos más cercano al cliente y dirigido a continuación, en función del servicio que usar siguiente. Si iniciar el correo electrónico, la conexión inicial para mostrar la interfaz de usuario todavía puede venir desde el centro de datos más cercano, pero es posible que se abre una segunda conexión entre el centro de datos más cercano y el centro de datos donde se encuentra el inquilino de para mostrar lo que aparece en los mensajes de correo electrónico lea. Microsoft administra una de las redes de diez principales en el mundo resultante en conexiones increíblemente fast de centro de datos para datacenter fast.
  
Después de leer el artículo, es probable que comprenderá ¿por qué no proporcionamos [intervalos de direcciones IP y URL de Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2) por centro de datos, simplemente son demasiado conectadas entre sí y depende de otra para hacer que sea posible.
  
Si está utilizando ExpressRoute de Azure para Office 365, en la mayoría de los casos la conectividad se vaya a través de una conexión privada a Office 365 en lugar de la conexión pública que se describen aquí. Los principios acerca de cómo los clientes se conectan continúan siendo exactos. Obtenga más información acerca de [ExpressRoute de Azure para Office 365](azure-expressroute.md).
  
Para obtener más profundidad en Skype para las solicitudes de red empresarial, lea el artículo de [calidad de los medios y el rendimiento de la conectividad de red en Skype para profesionales en línea](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).

||
|:-----|
| En este artículo forma parte de la [planeación de la red y ajuste del rendimiento de Office 365](https://aka.ms/tune).|

> [!NOTE]
> Echamos mucho cuidado para administrar los datos de cliente, por lo que es segura y privada en nuestros centros de datos. Se incluye información acerca de los pasos que se tomen para administrar la privacidad en el [Centro de confianza](https://go.microsoft.com/fwlink/?LinkID=397383).
  
## <a name="connecting-to-the-nearest-datacenter"></a>Conectar con el centro de datos más cercano

Éste es el tipo de conexión más comunes y se usa mediante el portal de Office 365 y Exchange Online. En esta situación, cuando los clientes intentan conectarse a Office 365, consulta DNS de su equipo determina la región del mundo que procede de su equipo y Office 365 redirige la solicitud al centro de datos más cercano.
  
Las conexiones en el portal de detención en el centro de datos más cercano y el equipo cliente se presenta con información sobre el inquilino del cliente desde esa ubicación.
  
Exchange Online va un paso más allá. Una vez que el equipo cliente está conectado al centro de datos más cercano, un servidor de Exchange en ese centro de datos se conecta al centro de datos donde el inquilino es realmente encuentra tal como se ilustra en el *¿cómo esto trabajar sección* por debajo. Los servidores de Exchange Online en el centro de datos más cercano, a continuación, proxy de las solicitudes desde el equipo cliente en el servidor de buzón de correo. Esto acelera la experiencia para el equipo cliente desplazando el trabajo de recuperación de mensajes de correo electrónico y elementos de calendario a la red de Microsoft.
  
## <a name="how-does-this-work-for-standard-cloud-offerings"></a>¿Cómo funciona esto para las ofertas de nube estándar?

Este proceso de conexión es estándar para tráfico alto, las aplicaciones web de alto valor, como Office 365. En esta sección, se de esquema y se ilustran los pasos en el proceso. Cuando el equipo cliente no está en la misma región como el inquilino, busca mucho varían en función del servicio que el cliente se conecta a la conexión.
  
 Este diagrama ilustra a un cliente con una oferta estándar de Office 365 con un inquilino en Norteamérica. En este escenario, la persona que realiza la solicitud se haya desplazado a Europa y está usando Office 365 desde esa ubicación.
  
1. El equipo cliente solicita a los servidores DNS locales para la dirección IP asociada con Office 365.

2. Los servidores DNS locales del equipo cliente solicitan a los servidores de DNS de Microsoft para la dirección IP asociada con Office 365.

3. Los servidores DNS de Microsoft devolución el nombre del servidor regional (basado en la ubicación de los servidores del cliente DNS) y el equipo cliente repite los pasos 1 y 2 para obtener la dirección IP del centro de datos de Office 365 regional.

4. El equipo cliente se conecta a la dirección IP del centro de datos regional.

5. Los servidores de Exchange Online establecen una conexión con el centro de datos activo donde reside el inquilino del cliente.

![Centro de datos regional más próximo](media/4ea108e9-a299-4e3d-b0d3-469b434ff899.png)
  
## <a name="how-does-this-work-for-sovereign-cloud-offerings"></a>¿Cómo la nube este trabajo para soberanos a las ofertas?

Esta conexión es ligeramente diferente para las ofertas de nube soberanos, como Office 365 operado por Vianet 21. Con el inquilino en una instancia soberano de Office 365, los servidores de Office 365 más cercanos que aceptarán conexiones del portal son los servidores dentro de la región soberano donde reside el inquilino. De forma similar, los clientes de acceso a SharePoint Online en nuestro soberanos en la nube o las ofertas estándares se dirigirán a los servidores front-end donde reside el inquilino. Vea conectar con el centro de datos activo que aparece a continuación.
  
1. El equipo cliente solicita a los servidores DNS locales para la dirección IP asociada con Office 365.

2. Los servidores DNS locales del equipo cliente solicitan a los servidores de DNS de Microsoft para la dirección IP asociada con Office 365.

3. Los servidores DNS de Microsoft devolución el nombre del servidor regional (basado en la ubicación de los servidores del cliente DNS) y el equipo cliente repite los pasos 1 y 2 para obtener la dirección IP del centro de datos de Office 365 regional.

4. El equipo cliente se conecta a la dirección IP del centro de datos regional.

5. Los servidores de Exchange Online establecen una conexión con el centro de datos activo donde reside el inquilino del cliente.

![Centro de datos regional más próximo de EE. UU.](media/c0628c54-0059-48c5-8a0f-41bf392ee182.png)
  
## <a name="connecting-to-the-active-datacenter"></a>Conexión con el centro de datos activo

Conectar con el centro de datos activo está diseñado para más pesadas cargas de trabajo de transferencia de datos y se usa actualmente en SharePoint Online. En esta situación, cuando los clientes intentan conectarse a Office 365, su explorador se redirige al centro de datos activo para su inquilino de SharePoint Online.
  
## <a name="how-does-this-work"></a>¿Cómo funciona esto?

Cuando el equipo cliente se conecta a SharePoint Online desde una región diferente, la conexión se redirige al centro de datos de SharePoint Online activo. En este escenario, el cliente está utilizando un estándar que ofrece, lo que en las conexiones del portal restante local y las conexiones de SharePoint Online que se dirige al centro de datos activa.
  
1. El equipo cliente solicita a los servidores DNS locales para la dirección IP asociada con Office 365.

2. Los servidores DNS locales del equipo cliente solicitan a los servidores de DNS de Microsoft para la dirección IP asociada con Office 365.

3. Los servidores DNS de Microsoft devolución el nombre del servidor del centro de datos SharePoint Online activo (basado en la ubicación del inquilino de Office 365 del cliente), y el equipo cliente repite los pasos 1 y 2 para obtener la dirección IP del centro de datos de Office 365 activo.

4. El equipo cliente se conecta a la dirección IP del centro de datos activo.

![Centro de datos activo de EE. UU.](media/c6d2933f-49cb-4536-bea7-c868707755ae.png)
  
## <a name="connecting-over-virtual-private-networks-vpns"></a>Conexión a través de redes privadas virtuales (VPN)

Este tipo de conexión aplica sólo cuando se usa una red privada virtual (VPN) en los equipos cliente. En realidad, el comportamiento de Office 365 no cambia simplemente porque se usa una red privada virtual, pero las redes privadas virtuales con frecuencia se usan para controlar cómo los equipos cliente establecen conexiones a Office 365 y, normalmente, los resultados en una experiencia degradada, por lo que es importante cubrir.
  
## <a name="how-does-this-work"></a>¿Cómo funciona esto?

Cuando el equipo cliente establece una conexión VPN a una oficina corporativa en una región diferente, los servidores DNS en los que office se usan en lugar de los servidores DNS en la ubicación del equipo cliente. En la mayoría de los casos, esta conexión adicional a través de la VPN, degradará la experiencia de Office 365. Los servicios de Office 365 están optimizados para conexiones de cliente de servicio como más cercano al usuario final como sea posible. Muchos servicios sacar provecho de la red perimetral Azure, redes de distribución de contenido y la capacidad de red confiable en la red de Microsoft para ofrecer la mejor experiencia de usuario posible cuando se realizan las solicitudes de red para servicios de Office 365 lo más cerca del equipo cliente como sea posible.
  
1. El equipo cliente solicita el DNS VPN servidores para la dirección IP asociada con Office 365.

2. Los servidores DNS de la VPN del equipo cliente solicitan a los servidores de DNS de Microsoft para la dirección IP asociada con Office 365.

3. Los servidores DNS de Microsoft devolución el nombre del servidor regional (basado en la ubicación de los servidores DNS de la VPN), y el equipo cliente repite los pasos 1 y 2 para obtener la información de dirección IP del centro de datos de Office 365 regional.

4. El equipo cliente conecta al centro de datos dirección IP que se encuentra más cercano a la oficina corporativa con que se estableció una conexión VPN.

![Conectividad VPN de centro de datos](media/b5f4c06c-65a3-462d-aae8-9a4602dd8d9e.png)
  
Éste es un vínculo corto que puede usar para volver:[https://aka.ms/o365clientconnectivity](https://aka.ms/o365clientconnectivity)
  
## <a name="see-also"></a>Vea también

[Administración de extremos de Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Conectividad de red a Office 365](network-connectivity.md)
