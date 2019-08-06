---
title: Planificación de dispositivos de red que se conecten a servicios de Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/29/2016
audience: ITPro
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
description: 'Resumen: describe las consideraciones sobre la capacidad de red, los aceleradores WAN y los dispositivos de equilibrio de carga que se usan para conectarse a Office 365.'
ms.openlocfilehash: b6804e7922178a3b653b3767a33e02e2a382ef93
ms.sourcegitcommit: 0449c6f854c682719cac1bd0d086f2e3b20078b9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2019
ms.locfileid: "34722629"
---
# <a name="plan-for-network-devices-that-connect-to-office-365-services"></a>Planificación de dispositivos de red que se conecten a servicios de Office 365

 **Resumen**: describe las consideraciones sobre la capacidad de red, los aceleradores WAN y los dispositivos de equilibrio de carga que se usan para conectarse a Office 365.
  
Es posible que el hardware de red tenga limitaciones en el número de sesiones simultáneas que se admiten. Para las organizaciones que tienen más de 2.000 usuarios, recomendamos que supervisen sus dispositivos de red para garantizar que puedan controlar el tráfico adicional del servicio Office 365. El software de supervisión del Protocolo simple de administración de redes (SNMP) puede ayudarle a hacerlo.

||
|:-----|
| Este artículo forma parte de la planeación de [red y el ajuste del rendimiento de Office 365](https://aka.ms/tune).|

La configuración de proxy de Internet saliente local también afecta a la conectividad con los servicios de Office 365 para las aplicaciones cliente. También debe configurar los dispositivos proxy de red para permitir conexiones de las aplicaciones y las direcciones URL de servicios en la nube de Microsoft. Cada organización es diferente. Para hacerse una idea de cómo Microsoft administra este proceso y la cantidad de ancho de banda que aprovisionamos, [Lea el caso práctico](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365).
  
Los siguientes artículos de ayuda de Skype empresarial contienen más información sobre la configuración de Skype empresarial:
  
- [Solución de errores de inicio de sesión de Skype empresarial online para administradores](https://docs.microsoft.com/skypeforbusiness/set-up-skype-for-business-online/troubleshooting-sign-in-errors-for-admins)

- [No puede conectarse a Skype empresarial o algunas características no funcionan porque un firewall local bloquea la conexión](https://go.microsoft.com/fwlink/p/?LinkID=243625)

> [!NOTE]
> Aunque muchos de estos valores son específicos de Skype empresarial, las instrucciones generales sobre la configuración de red son útiles para todos los servicios de Office 365.
  
## <a name="determining-network-capacity"></a>Determinación de la capacidad de red

Cada dispositivo de red que existe en una conexión tiene su límite de capacidad. Estos dispositivos incluyen los adaptadores de red de cliente y de servidor, los enrutadores, los conmutadores y los concentradores que los interconectaron. Una capacidad de red adecuada significa que ninguna de ellas está saturada. La supervisión de la actividad de red es esencial para ayudar a garantizar que las cargas reales en todos los dispositivos de red son inferiores a su capacidad máxima. La capacidad de la red afecta el rendimiento del dispositivo proxy.
  
En la mayoría de los casos, el ancho de banda de la conexión a Internet establece el límite para la cantidad de tráfico. El rendimiento mínimo durante las horas pico de tráfico es probablemente causado por un uso excesivo del vínculo de Internet. Esta situación también se aplica a un escenario de sucursal, donde los equipos de servidor proxy de sucursal se conectan al dispositivo proxy en la oficina central de la sucursal a través de un vínculo de red de área extensa (WAN) lento.
  
Para probar la capacidad de la red, supervise la actividad de red en la interfaz de red de proxy. Si es superior al 75 por ciento del ancho de banda máximo de cualquier interfaz de red, considere la posibilidad de aumentar el ancho de banda de la infraestructura de red que no es suficiente. O bien, considere la posibilidad de usar características avanzadas, como la compresión HTTP.
  
## <a name="wan-accelerators"></a>Aceleradores WAN

Si su organización usa dispositivos proxy de aceleración de red de área extensa (WAN), puede tener problemas al obtener acceso a los servicios de Office 365. Es posible que necesite optimizar el dispositivo o dispositivos de red para asegurarse de que los usuarios tienen una experiencia coherente al obtener acceso a Office 365. Por ejemplo, los servicios de Office 365 cifran algunos contenidos de Office 365 y el encabezado TCP. Es posible que el dispositivo no pueda controlar este tipo de tráfico.
  
Lea nuestra declaración de soporte técnico sobre el [uso del controlador de optimización de WAN o dispositivos de tráfico/inspección con Office 365](https://support.microsoft.com/kb/2690045).
  
## <a name="hardware-and-software-load-balancing-devices"></a>Dispositivos de equilibrio de carga de hardware y software

Su organización debe usar un equilibrador de carga de hardware (HLB) o una solución de equilibrio de carga de red (NLB) para distribuir las solicitudes a los servidores de los servicios de Federación de Active Directory (AD FS) o a los servidores híbridos de Exchange. Los dispositivos de equilibrio de carga controlan el tráfico de red a los servidores locales. Estos servidores son cruciales para garantizar la disponibilidad de inicio de sesión único y la implementación híbrida de Exchange.
  
Proporcionamos una solución NLB basada en software integrada en Windows Server. Office 365 admite esta solución para lograr el equilibrio de carga.
  
## <a name="firewalls-and-proxies"></a>Firewalls y servidores proxy

Para obtener más información sobre cómo configurar firewalls y servidores proxy para conectarse a Office 365, consulte Administración de puntos de conexión de [office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), evaluación de la [conectividad de red](assessing-network-connectivity.md)de Office 365 y preguntas más frecuentes de los puntos de conexión de [Office 365](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) para obtener más información sobre los dispositivos y el circuito selección.
  
## <a name="see-also"></a>Vea también

[Asesores de implementación para servicios de Office 365](deployment-advisors-for-office-365.md)
