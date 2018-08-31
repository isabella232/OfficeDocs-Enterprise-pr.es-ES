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
# <a name="nat-support-with-office-365"></a><span data-ttu-id="553c4-103">Compatibilidad de NAT con Office 365</span><span class="sxs-lookup"><span data-stu-id="553c4-103">NAT support with Office 365</span></span>

 <span data-ttu-id="553c4-104">**Resumen:** proporciona detalles sobre cómo aproximar el número correcto de clientes que se pueden usar por dirección IP dentro de la organización mediante la traducción de direcciones de red (NAT).</span><span class="sxs-lookup"><span data-stu-id="553c4-104">**Summary:** Provides details about how to approximate the correct number of clients you can use per IP address within your organization using Network Address Translation (NAT).</span></span> 
  
<span data-ttu-id="553c4-105">Anteriormente, instrucciones sugieren que el número máximo de clientes de Exchange que debe usar por dirección IP para conectarse a Office 365 era clientes aproximadamente 2.000 por puerto de red.</span><span class="sxs-lookup"><span data-stu-id="553c4-105">Previously, guidance suggested that the maximum number of Exchange clients you should use per IP address to connect to Office 365 was about 2,000 clients per network port.</span></span>
  
## <a name="why-use-nat"></a><span data-ttu-id="553c4-106">¿Por qué usar NAT?</span><span class="sxs-lookup"><span data-stu-id="553c4-106">Why use NAT?</span></span>

<span data-ttu-id="553c4-107">Mediante el uso de NAT, miles de personas en una red corporativa pueden "compartir" unas pocas direcciones IP enrutables públicamente.</span><span class="sxs-lookup"><span data-stu-id="553c4-107">By using NAT, thousands of people on a corporate network can "share" a few publicly routable IP addresses.</span></span>
  
<span data-ttu-id="553c4-p101">La mayoría de las redes corporativas usan espacio de dirección IP (RFC1918) privada. El espacio de dirección privada está asignado por la Internet Assigned Numbers Authority (IANA) y está pensado exclusivamente para redes que no se enrutan hacia Internet global ni desde allí.</span><span class="sxs-lookup"><span data-stu-id="553c4-p101">Most corporate networks use private (RFC1918) IP address space. Private address space is allocated by the Internet Assigned Numbers Authority (IANA) and intended solely for networks that do not route directly to and from the global Internet.</span></span>
  
<span data-ttu-id="553c4-p102">Para proporcionar acceso a Internet para los dispositivos en un espacio de direcciones IP privado, las organizaciones usan tecnologías de puerta de enlace al igual que los firewalls y servidores proxy que proporcionan la traducción de direcciones de red (NAT) o servicios (PAT) de traducción de direcciones de puerto. Estas puertas de enlace harán que el tráfico de interna dispositivos a Internet (incluido Office 365) parecen ser procedentes de una o varias direcciones IP enrutables públicamente. Cada conexión saliente desde un dispositivo interno se traduce en un puerto TCP de origen diferentes en la dirección IP pública.</span><span class="sxs-lookup"><span data-stu-id="553c4-p102">To provide Internet access to devices on a private IP address space, organizations use gateway technologies like firewalls and proxies that provide network address translation (NAT) or port address translation (PAT) services. These gateways make traffic from internal devices to the Internet (including Office 365) appear to be coming from one or more publicly routable IP addresses. Each outbound connection from an internal device translates to a different source TCP port on the public IP address.</span></span> 
  
## <a name="why-do-you-need-to-have-so-many-connections-open-to-office-365-at-the-same-time"></a><span data-ttu-id="553c4-113">¿Por qué necesita tienen tantas conexiones abiertas a Office 365 al mismo tiempo?</span><span class="sxs-lookup"><span data-stu-id="553c4-113">Why do you need to have so many connections open to Office 365 at the same time?</span></span>

<span data-ttu-id="553c4-p103">Outlook puede abrir ocho conexiones o incluso más (cuando existen complementos, calendarios compartidos, buzones, etc.). Debido a que existe un máximo de 64.000 puertos disponibles en un dispositivo NAT basado en Windows, puede existir un máximo de 8.000 usuarios detrás de una dirección IP antes de que se agoten los puertos. Tenga en cuenta que si los clientes están usando para NAT dispositivos que no están basados en un sistema operativo Windows, los puertos disponibles totales dependen del software o dispositivo NAT que se esté usando. En esta situación, el número máximo de puertos podría ser menor de 64.000. La disponibilidad de los puertos también se ve afectada por otros factores como la restricción de 4.000 puertos que Windows se reserva para su uso propio, lo cual reduce el número total de puertos disponibles a 60.000. Puede haber otras aplicaciones, como Internet Explorer, que podrían conectarse al mismo tiempo y requerir puertos adicionales.</span><span class="sxs-lookup"><span data-stu-id="553c4-p103">Outlook may open eight or more connections (in situations where there are add-ins, shared calendars, mailboxes, etc.). Because there are a maximum of 64,000 ports available on a Windows-based NAT device, there can be a maximum of 8,000 users behind an IP address before the ports are exhausted. Note that if customers are using non-Windows OS-based devices for NAT, the total available ports are dependent on what NAT device or software is being used. In this scenario, the maximum number of ports could be less than 64,000. Availability of ports is also affected by other factors such as Windows restricting 4,000 ports for its own use, which reduces the total number of available ports to 60,000.There may be other applications, such as Internet Explorer, that could connect at the same time, requiring additional ports.</span></span>
  
## <a name="calculating-maximum-supported-devices-behind-a-single-public-ip-address-with-office-365"></a><span data-ttu-id="553c4-119">Calcular el número máximo de dispositivos admitidos detrás una sola dirección IP pública con Office 365</span><span class="sxs-lookup"><span data-stu-id="553c4-119">Calculating maximum supported devices behind a single public IP address with Office 365</span></span>

<span data-ttu-id="553c4-p104">Para determinar el número máximo de dispositivos detrás de una sola dirección IP pública, debe supervisar el tráfico de red para determinar el consumo de puerto máximo por cliente. Además, se debe usar un factor pico para el uso del puerto (mínimo de 4).</span><span class="sxs-lookup"><span data-stu-id="553c4-p104">To determine the maximum number of devices behind a single public IP address, you should monitor network traffic to determine peak port consumption per client. Also, a peak factor should be used for the port usage (minimum 4).</span></span> 
  
 <span data-ttu-id="553c4-122">**Use la siguiente fórmula para calcular el número de dispositivos admitidos por dirección IP:**</span><span class="sxs-lookup"><span data-stu-id="553c4-122">**Use the following formula to calculate the number of supported devices per IP address:**</span></span>
  
<span data-ttu-id="553c4-123">Dispositivos máximos admitidos detrás de una sola dirección IP pública = (64.000 - puertos restringidos) / (puerto consumo pico + factor pico)</span><span class="sxs-lookup"><span data-stu-id="553c4-123">Maximum supported devices behind a single public IP address = (64,000 - restricted ports)/(Peak port consumption + peak factor)</span></span>
  
 <span data-ttu-id="553c4-124">**Por ejemplo, si las siguientes son true:**</span><span class="sxs-lookup"><span data-stu-id="553c4-124">**For example, if the following were true:**</span></span>
  
- <span data-ttu-id="553c4-125">**Puertos restringidos:** 4.000 para el sistema operativo</span><span class="sxs-lookup"><span data-stu-id="553c4-125">**Restricted ports:** 4,000 for the operating system</span></span> 
    
- <span data-ttu-id="553c4-126">**Consumo de puertos pico:** 6 por dispositivo</span><span class="sxs-lookup"><span data-stu-id="553c4-126">**Peak port consumption:** 6 per device</span></span> 
    
- <span data-ttu-id="553c4-127">**Factor pico:** 4</span><span class="sxs-lookup"><span data-stu-id="553c4-127">**Peak factor:** 4</span></span> 
    
<span data-ttu-id="553c4-128">A continuación, los dispositivos máximos admitidos detrás de una sola dirección IP pública = (64.000 4.000) / (6 + 4) = 6.000</span><span class="sxs-lookup"><span data-stu-id="553c4-128">Then, the maximum supported devices behind a single public IP address = (64,000 - 4,000)/(6 + 4) = 6,000</span></span>
  
<span data-ttu-id="553c4-p105">Con la versión del paquete, incluida en las actualizaciones de septiembre de 2011 de Microsoft Office Outlook 2007 o de noviembre de 2011 de Microsoft Outlook 2010, o una actualización posterior, el número de conexiones de Outlook (ambos Office Outlook 2007 con el servicio de host de Office 365 Pack 2 y Outlook 2010) para Exchange puede ser tan solo 2. Necesita factor en los distintos sistemas operativos, comportamientos de usuario, y así sucesivamente para determinar el número mínimo y máximo de puertos que requiere un rendimiento máximo en su red.</span><span class="sxs-lookup"><span data-stu-id="553c4-p105">With the release of Office 365 hosting pack, included in the updates from September 2011 for Microsoft Office Outlook 2007, or November 2011 for Microsoft Outlook 2010, or a later update, the number of connections from Outlook (both Office Outlook 2007 with Service Pack 2 and Outlook 2010) to Exchange can be as few as 2. You'll need to factor in the different operating systems, user behaviors, and so on to determine the minimum and maximum number of ports that your network will require at peak.</span></span>
  
<span data-ttu-id="553c4-131">Si desea admitir más dispositivos detrás de una sola dirección IP pública, siga los pasos descritos para evaluar el número máximo de dispositivos que se pueden admitir:</span><span class="sxs-lookup"><span data-stu-id="553c4-131">If you want to support more devices behind a single public IP address, follow the steps outlined to assess the maximum number of devices that can be supported:</span></span>
  
<span data-ttu-id="553c4-p106">Supervisar el tráfico de red para determinar el consumo de puerto máximo por cliente. Debe recopilar estos datos:</span><span class="sxs-lookup"><span data-stu-id="553c4-p106">Monitor network traffic to determine peak port consumption per client. You should collect this data:</span></span>
  
- <span data-ttu-id="553c4-134">De varias ubicaciones</span><span class="sxs-lookup"><span data-stu-id="553c4-134">From multiple locations</span></span>
    
- <span data-ttu-id="553c4-135">De varios dispositivos</span><span class="sxs-lookup"><span data-stu-id="553c4-135">From multiple devices</span></span>
    
- <span data-ttu-id="553c4-136">En varios momentos</span><span class="sxs-lookup"><span data-stu-id="553c4-136">At multiple times</span></span>
    
<span data-ttu-id="553c4-137">Use la fórmula anterior para calcular los usuarios máximos por dirección IP que se pueden admitir en sus entornos.</span><span class="sxs-lookup"><span data-stu-id="553c4-137">Use the preceding formula to calculate the maximum users per IP address that can be supported in their environment.</span></span>
  
<span data-ttu-id="553c4-p107">Existen varios métodos para distribuir la carga de cliente a través de las direcciones IP públicas adicionales. Estrategias disponibles dependen de las capacidades de la solución de puerta de enlace corporativo. La solución más sencilla es el espacio de direcciones de usuario de segmento y "asignar" estáticamente un número de direcciones IP para cada puerta de enlace. Otra alternativa que ofrecen muchos dispositivos de puerta de enlace es la capacidad de usar un grupo de direcciones IP. La ventaja de la agrupación de direcciones es que es menos probable que requiera ajuste a medida que crece su base de usuarios y mucho más dinámico.</span><span class="sxs-lookup"><span data-stu-id="553c4-p107">There are various methods for distributing client load across additional public IP addresses. Strategies available depend on the capabilities of the corporate gateway solution. The simplest solution is to segment your user address space and statically "assign" a number of IP addresses to each gateway. Another alternative that many gateway devices offer is the ability to use a pool of IP addresses. The benefit of the address pool is that it is much more dynamic and less likely to require adjustment as your user base grows.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="553c4-143">Vea también</span><span class="sxs-lookup"><span data-stu-id="553c4-143">See also</span></span>

[<span data-ttu-id="553c4-144">Administración de extremos de Office 365</span><span class="sxs-lookup"><span data-stu-id="553c4-144">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[<span data-ttu-id="553c4-145">Preguntas más frecuentes de los extremos de Office 365</span><span class="sxs-lookup"><span data-stu-id="553c4-145">Office 365 endpoints FAQ</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

