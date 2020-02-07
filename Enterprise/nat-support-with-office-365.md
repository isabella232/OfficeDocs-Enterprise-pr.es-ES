---
title: Compatibilidad de NAT con Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 1/24/2017
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: 170e96ea-d65d-4e51-acac-1de56abe39b9
description: 'Resumen: proporciona detalles sobre cómo aproximar el número correcto de clientes que se pueden usar por dirección IP dentro de la organización mediante la traducción de direcciones de red (NAT).'
ms.openlocfilehash: 6140cf664a08701e9491c241d5754d51196e3922
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844571"
---
# <a name="nat-support-with-office-365"></a>Compatibilidad de NAT con Office 365

*Este artículo se aplica tanto a Office 365 Enterprise como a Microsoft 365 Enterprise.*

Anteriormente, las instrucciones sugieren que el número máximo de clientes de Exchange que debe usar por dirección IP para conectarse a Office 365 era aproximadamente de 2.000 clientes por puerto de red.
  
## <a name="why-use-nat"></a>¿Por qué usar NAT?

Mediante NAT, miles de personas en una red corporativa pueden "compartir" unas pocas direcciones IP enrutables públicamente.
  
La mayoría de las redes corporativas usan espacio de direcciones IP privadas (RFC1918). El espacio de direcciones privadas se asigna mediante IANA (Internet Assigned Numbers Authority) y está destinado exclusivamente a redes que no se enrutan directamente desde y hacia la Internet global.
  
Para proporcionar acceso a Internet a los dispositivos en un espacio de direcciones IP privadas, las organizaciones usan tecnologías de puerta de enlace como firewalls y servidores proxy que proporcionan servicios de traducción de direcciones de red (NAT) o de traducción de direcciones de puerto (PAT). Estas puertas de enlace permiten que el tráfico desde dispositivos internos a Internet (incluido Office 365) provenga de una o varias direcciones IP enrutables públicamente. Cada conexión saliente de un dispositivo interno se traduce en un puerto TCP de origen diferente en la dirección IP pública. 
  
## <a name="why-do-you-need-to-have-so-many-connections-open-to-office-365-at-the-same-time"></a>¿Por qué necesita tener tantas conexiones abiertas a Office 365 al mismo tiempo?

Outlook puede abrir ocho o más conexiones (en situaciones en las que hay complementos, calendarios compartidos, buzones de correo, etc.). Como hay un máximo de 64.000 puertos disponibles en un dispositivo NAT basado en Windows, puede haber un máximo de 8.000 usuarios detrás de una dirección IP antes de que se agoten los puertos. Tenga en cuenta que si los clientes usan dispositivos que no están basados en el sistema operativo Windows para NAT, los puertos totales disponibles dependen de qué dispositivo o software NAT se esté usando. En este escenario, el número máximo de puertos podría ser inferior a 64.000. La disponibilidad de los puertos también se ve afectada por otros factores, como Windows, restringiendo 4.000 puertos para su propio uso, lo que reduce el número total de puertos disponibles a 60, 000. puede haber otras aplicaciones, como Internet Explorer, que puedan conectarse al mismo tiempo. , requiriendo puertos adicionales.
  
## <a name="calculating-maximum-supported-devices-behind-a-single-public-ip-address-with-office-365"></a>Calcular el número máximo de dispositivos admitidos detrás de una sola dirección IP pública con Office 365

Para determinar el número máximo de dispositivos que hay detrás de una sola dirección IP pública, debe supervisar el tráfico de red para determinar el consumo de puertos máximo por cliente. Además, se debe usar un factor máximo para el uso del puerto (mínimo 4). 
  
 **Use la siguiente fórmula para calcular el número de dispositivos admitidos por dirección IP:**
  
Dispositivos máximos admitidos detrás de una sola dirección IP pública = (64.000-puertos restringidos)/(consumo máximo de puertos + factor máximo)
  
 **Por ejemplo, si se cumplen las siguientes condiciones:**
  
- **Puertos restringidos:** 4.000 para el sistema operativo

- **Consumo de puertos máximo:** 6 por dispositivo

- **Factor máximo:** 4

A continuación, el máximo de dispositivos admitidos detrás de una sola dirección IP pública = (64.000-4000)/(6 + 4) = 6.000
  
Con el lanzamiento del paquete de hospedaje de Office 365, incluido en las actualizaciones de septiembre de 2011 para Microsoft Office Outlook 2007 o de noviembre de 2011 para Microsoft Outlook 2010, o una actualización posterior, el número de conexiones de Outlook (Office Outlook 2007 con Service El paquete 2 y Outlook 2010) a Exchange pueden tener un mínimo de 2. Necesitará tener en cuentan los diferentes sistemas operativos, comportamientos de usuario, etc., para determinar el número mínimo y máximo de puertos que la red necesitará como pico.
  
Si desea admitir más dispositivos detrás de una sola dirección IP pública, siga los pasos descritos para evaluar el número máximo de dispositivos que se pueden admitir:
  
Supervise el tráfico de red para determinar el consumo de puertos máximo por cliente. Debe recopilar estos datos:
  
- Desde varias ubicaciones
    
- Desde varios dispositivos
    
- En varias ocasiones
    
Use la fórmula anterior para calcular el número máximo de usuarios por dirección IP que se pueden admitir en su entorno.
  
Hay varios métodos para distribuir la carga de clientes a través de direcciones IP públicas adicionales. Las estrategias disponibles dependen de las capacidades de la solución de puerta de enlace corporativa. La solución más sencilla es segmentar el espacio de direcciones de usuario y "asignar" estáticamente una cantidad de direcciones IP a cada puerta de enlace. Otra alternativa que muchos dispositivos de puerta de enlace ofrece es la capacidad de usar un grupo de direcciones IP. La ventaja del grupo de direcciones es que es mucho más dinámica y menos probable que sea necesario ajustarse a medida que crece la base de usuarios.
  
## <a name="see-also"></a>Vea también

[Administrar puntos de conexión de Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Preguntas frecuentes sobre extremos de Office 365](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
