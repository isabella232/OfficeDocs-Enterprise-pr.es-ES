---
title: Planificación de dispositivos de red que se conecten a servicios de Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/29/2016
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 073433ca-3511-4db9-b173-7a2edca57691
description: 'Resumen: describe las consideraciones sobre la capacidad de la red, los aceleradores de WAN y los dispositivos que equilibran la carga y que se utilizan para conectarse a Office 365.'
ms.openlocfilehash: 023eb3f5ed4d81d1d49d18c69ef8c81032fd5851
ms.sourcegitcommit: 317c2753be2aedb60698e94606ba59b63c962328
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/02/2018
ms.locfileid: "25933127"
---
# <a name="plan-for-network-devices-that-connect-to-office-365-services"></a>Planificación de dispositivos de red que se conecten a servicios de Office 365

 **Resumen**: describe las consideraciones sobre la capacidad de la red, los aceleradores de WAN y los dispositivos que equilibran la carga y que se utilizan para conectarse a Office 365.
  
Algunos hardware de red puede tener limitaciones en el número de sesiones simultáneas que se admiten. Para organizaciones que tengan más de 2.000 usuarios, se recomienda que sus dispositivos de red para asegurarse de que son capaces de administrar el tráfico del servicio Office 365 adicional que van a supervisar. Red administración Protocolo simple (SNMP) software de supervisión pueden ayudarle a hacerlo.

||
|:-----|
| En este artículo forma parte de la [planeación de la red y ajuste del rendimiento de Office 365](https://aka.ms/tune).|

Configuración de proxy de Internet saliente también afecta a la conectividad a los servicios de Office 365 para las aplicaciones cliente en local. También debe configurar los dispositivos de proxy de la red para permitir conexiones para las aplicaciones y direcciones URL de servicios de nube de Microsoft. Cada organización es diferente. Para obtener una idea de cómo Microsoft administra este proceso y la cantidad de ancho de banda se aprovisione, [Lea el caso práctico](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365).
  
El siguiente Skype para artículos de Ayuda de negocio tienen más información acerca de Skype para la configuración de negocio:
  
- [Solución de problemas de Skype para errores de inicio de sesión empresarial en línea para los administradores](https://docs.microsoft.com/skypeforbusiness/set-up-skype-for-business-online/troubleshooting-sign-in-errors-for-admins)

- [No se puede conectar a Skype para la empresa o determinadas características no funcionan, porque un firewall local bloquea la conexión](https://go.microsoft.com/fwlink/p/?LinkID=243625)

> [!NOTE]
> Si bien muchas de estas opciones son Skype para específicas de la empresa, las instrucciones generales sobre la configuración de red son útil para todos los servicios de Office 365.
  
## <a name="determining-network-capacity"></a>Determinar la capacidad de la red

Cada dispositivo de red que existe en una conexión tiene un límite de capacidad. Entre estos dispositivos se incluyen los adaptadores, enrutadores y  conmutadores de la red de cliente y servidor, así como los concentradores  que los interconectan. Una capacidad de red adecuada significa que ninguno de ellos está saturado. Supervisar la actividad de la red es fundamental para contribuir a garantizar que las cargas reales en todos los dispositivos de red estén por debajo de su capacidad máxima. La capacidad de la red afecta el rendimiento del dispositivo proxy.
  
En la mayoría de las situaciones, el ancho de banda de conexión de Internet establece el límite para la cantidad de tráfico. Un rendimiento bajo durante horas punta de tráfico probablemente está causado por un uso excesivo del vínculo de Internet. Esta situación también se aplica a un escenario de sucursal, donde están conectados los equipos de servidor proxy sucursales para el dispositivo de proxy en sedes centrales de la sucursal a través de un vínculo lento de red de área extensa (WAN).
  
Para probar la capacidad de red, supervisar la actividad de red en la interfaz de red del proxy. Si es más del 75 por ciento del ancho de banda máximo de cualquier interfaz de red, considere la posibilidad de aumentar el ancho de banda de la infraestructura de red que no es la adecuada. O bien, considere el uso de características avanzadas, como la compresión HTTP.
  
## <a name="wan-accelerators"></a>Aceleradores WAN

Si su organización usa dispositivos de proxy de aceleración de área extensa (WAN) de red, es posible que tiene problemas al tener acceso a los servicios de Office 365. Es posible que necesite optimizar su dispositivo de red o dispositivos para asegurarse de que los usuarios tengan una experiencia coherente al obtener acceso a Office 365. Por ejemplo, servicios de Office 365 cifran algún contenido de Office 365 y el encabezado TCP. El dispositivo no es posible que sea capaz de controlar este tipo de tráfico.
  
Lea nuestra declaración de soporte técnico sobre el [uso de controlador de optimización de la WAN o dispositivos de inspección del tráfico con Office 365](https://support.microsoft.com/kb/2690045).
  
## <a name="hardware-and-software-load-balancing-devices"></a>Dispositivos de equilibrio de carga de hardware y software

Su organización necesita usar un equilibrador de carga de red basado en hardware (HLB) o una solución de equilibrio de carga de red (NLB) para distribuir solicitudes a sus servidores de servicios de federación de Active Directory (AD FS) o servidores híbridos Exchange. Los equilibradores de carga controlan el tráfico de red de los servidores locales. Estos servidores son muy importantes para contribuir a garantizar la disponibilidad de una implementación híbrida de Exchange y de inicio de sesión único.
  
Se proporciona una solución NLB basada en software integrada en Windows Server. Office 365 es compatible con esta solución para lograr el equilibrio de carga.
  
## <a name="firewalls-and-proxies"></a>Los firewalls y servidores proxy

Para obtener más información acerca de cómo configurar los firewall y servidores proxy para conectarse a Office 365, lea [los extremos de administración de Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), [conectividad de red a Office 365](network-connectivity.md)y [Office 365 extremos preguntas más frecuentes](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) para obtener más información acerca de la selección de circuitos y dispositivos.
  
## <a name="see-also"></a>Vea también

[Asesores de implementación para servicios de Office 365](deployment-advisors-for-office-365.md)
