---
title: Compatibilidad de NAT con Office 365
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 1/24/2017
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: 170e96ea-d65d-4e51-acac-1de56abe39b9
description: 'Resumen: proporciona detalles sobre cómo aproximar el número correcto de clientes que se pueden usar por dirección IP dentro de la organización mediante la traducción de direcciones de red (NAT).'
ms.openlocfilehash: 733d591bded599cfaece988a624baa7a3c0d4b06
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542684"
---
# <a name="nat-support-with-office-365"></a>Compatibilidad de NAT con Office 365

 **Resumen:** proporciona detalles sobre cómo aproximar el número correcto de clientes que se pueden usar por dirección IP dentro de la organización mediante la traducción de direcciones de red (NAT). 
  
Anteriormente, instrucciones sugieren que el número máximo de clientes de Exchange que debe usar por dirección IP para conectarse a Office 365 era clientes aproximadamente 2.000 por puerto de red.
  
## <a name="why-use-nat"></a>¿Por qué usar NAT?

Mediante el uso de NAT, miles de personas en una red corporativa pueden "compartir" unas pocas direcciones IP enrutables públicamente.
  
La mayoría de las redes corporativas usan espacio de dirección IP (RFC1918) privada. El espacio de dirección privada está asignado por la Internet Assigned Numbers Authority (IANA) y está pensado exclusivamente para redes que no se enrutan hacia Internet global ni desde allí.
  
Para proporcionar acceso a Internet para los dispositivos en un espacio de direcciones IP privado, las organizaciones usan tecnologías de puerta de enlace al igual que los firewalls y servidores proxy que proporcionan la traducción de direcciones de red (NAT) o servicios (PAT) de traducción de direcciones de puerto. Estas puertas de enlace harán que el tráfico de interna dispositivos a Internet (incluido Office 365) parecen ser procedentes de una o varias direcciones IP enrutables públicamente. Cada conexión saliente desde un dispositivo interno se traduce en un puerto TCP de origen diferentes en la dirección IP pública. 
  
## <a name="why-do-you-need-to-have-so-many-connections-open-to-office-365-at-the-same-time"></a>¿Por qué necesita tienen tantas conexiones abiertas a Office 365 al mismo tiempo?

Outlook puede abrir ocho conexiones o incluso más (cuando existen complementos, calendarios compartidos, buzones, etc.). Debido a que existe un máximo de 64.000 puertos disponibles en un dispositivo NAT basado en Windows, puede existir un máximo de 8.000 usuarios detrás de una dirección IP antes de que se agoten los puertos. Tenga en cuenta que si los clientes están usando para NAT dispositivos que no están basados en un sistema operativo Windows, los puertos disponibles totales dependen del software o dispositivo NAT que se esté usando. En esta situación, el número máximo de puertos podría ser menor de 64.000. La disponibilidad de los puertos también se ve afectada por otros factores como la restricción de 4.000 puertos que Windows se reserva para su uso propio, lo cual reduce el número total de puertos disponibles a 60.000. Puede haber otras aplicaciones, como Internet Explorer, que podrían conectarse al mismo tiempo y requerir puertos adicionales.
  
## <a name="calculating-maximum-supported-devices-behind-a-single-public-ip-address-with-office-365"></a>Calcular el número máximo de dispositivos admitidos detrás una sola dirección IP pública con Office 365

Para determinar el número máximo de dispositivos detrás de una sola dirección IP pública, debe supervisar el tráfico de red para determinar el consumo de puerto máximo por cliente. Además, se debe usar un factor pico para el uso del puerto (mínimo de 4). 
  
 **Use la siguiente fórmula para calcular el número de dispositivos admitidos por dirección IP:**
  
Dispositivos máximos admitidos detrás de una sola dirección IP pública = (64.000 - puertos restringidos) / (puerto consumo pico + factor pico)
  
 **Por ejemplo, si las siguientes son true:**
  
- **Puertos restringidos:** 4.000 para el sistema operativo 
    
- **Consumo de puertos pico:** 6 por dispositivo 
    
- **Factor pico:** 4 
    
A continuación, los dispositivos máximos admitidos detrás de una sola dirección IP pública = (64.000 4.000) / (6 + 4) = 6.000
  
Con la versión del paquete, incluida en las actualizaciones de septiembre de 2011 de Microsoft Office Outlook 2007 o de noviembre de 2011 de Microsoft Outlook 2010, o una actualización posterior, el número de conexiones de Outlook (ambos Office Outlook 2007 con el servicio de host de Office 365 Pack 2 y Outlook 2010) para Exchange puede ser tan solo 2. Necesita factor en los distintos sistemas operativos, comportamientos de usuario, y así sucesivamente para determinar el número mínimo y máximo de puertos que requiere un rendimiento máximo en su red.
  
Si desea admitir más dispositivos detrás de una sola dirección IP pública, siga los pasos descritos para evaluar el número máximo de dispositivos que se pueden admitir:
  
Supervisar el tráfico de red para determinar el consumo de puerto máximo por cliente. Debe recopilar estos datos:
  
- De varias ubicaciones
    
- De varios dispositivos
    
- En varios momentos
    
Use la fórmula anterior para calcular los usuarios máximos por dirección IP que se pueden admitir en sus entornos.
  
Existen varios métodos para distribuir la carga de cliente a través de las direcciones IP públicas adicionales. Estrategias disponibles dependen de las capacidades de la solución de puerta de enlace corporativo. La solución más sencilla es el espacio de direcciones de usuario de segmento y "asignar" estáticamente un número de direcciones IP para cada puerta de enlace. Otra alternativa que ofrecen muchos dispositivos de puerta de enlace es la capacidad de usar un grupo de direcciones IP. La ventaja de la agrupación de direcciones es que es menos probable que requiera ajuste a medida que crece su base de usuarios y mucho más dinámico.
  
## <a name="see-also"></a>Vea también

[Administración de extremos de Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Preguntas más frecuentes de los extremos de Office 365](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

