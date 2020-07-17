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
ms.openlocfilehash: 04aec45b7d6c68b3e32d4ee384c9927896849bab
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998545"
---
# <a name="nat-support-with-office-365"></a><span data-ttu-id="cdf8d-103">Compatibilidad de NAT con Office 365</span><span class="sxs-lookup"><span data-stu-id="cdf8d-103">NAT support with Office 365</span></span>

<span data-ttu-id="cdf8d-104">*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="cdf8d-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="cdf8d-105">Anteriormente, las instrucciones sugieren que el número máximo de clientes de Exchange que debe usar por dirección IP para conectarse a Office 365 era aproximadamente de 2.000 clientes por puerto de red.</span><span class="sxs-lookup"><span data-stu-id="cdf8d-105">Previously, guidance suggested that the maximum number of Exchange clients you should use per IP address to connect to Office 365 was about 2,000 clients per network port.</span></span>
  
## <a name="why-use-nat"></a><span data-ttu-id="cdf8d-106">¿Por qué usar NAT?</span><span class="sxs-lookup"><span data-stu-id="cdf8d-106">Why use NAT?</span></span>

<span data-ttu-id="cdf8d-107">Mediante NAT, miles de personas en una red corporativa pueden "compartir" unas pocas direcciones IP enrutables públicamente.</span><span class="sxs-lookup"><span data-stu-id="cdf8d-107">By using NAT, thousands of people on a corporate network can "share" a few publicly routable IP addresses.</span></span>
  
<span data-ttu-id="cdf8d-108">La mayoría de las redes corporativas usan espacio de direcciones IP privadas (RFC1918).</span><span class="sxs-lookup"><span data-stu-id="cdf8d-108">Most corporate networks use private (RFC1918) IP address space.</span></span> <span data-ttu-id="cdf8d-109">El espacio de direcciones privadas se asigna mediante IANA (Internet Assigned Numbers Authority) y está destinado exclusivamente a redes que no se enrutan directamente desde y hacia la Internet global.</span><span class="sxs-lookup"><span data-stu-id="cdf8d-109">Private address space is allocated by the Internet Assigned Numbers Authority (IANA) and intended solely for networks that do not route directly to and from the global Internet.</span></span>
  
<span data-ttu-id="cdf8d-110">Para proporcionar acceso a Internet a los dispositivos en un espacio de direcciones IP privadas, las organizaciones usan tecnologías de puerta de enlace como firewalls y servidores proxy que proporcionan servicios de traducción de direcciones de red (NAT) o de traducción de direcciones de puerto (PAT).</span><span class="sxs-lookup"><span data-stu-id="cdf8d-110">To provide Internet access to devices on a private IP address space, organizations use gateway technologies like firewalls and proxies that provide network address translation (NAT) or port address translation (PAT) services.</span></span> <span data-ttu-id="cdf8d-111">Estas puertas de enlace permiten que el tráfico desde dispositivos internos a Internet (incluido Office 365) provenga de una o varias direcciones IP enrutables públicamente.</span><span class="sxs-lookup"><span data-stu-id="cdf8d-111">These gateways make traffic from internal devices to the Internet (including Office 365) appear to be coming from one or more publicly routable IP addresses.</span></span> <span data-ttu-id="cdf8d-112">Cada conexión saliente de un dispositivo interno se traduce en un puerto TCP de origen diferente en la dirección IP pública.</span><span class="sxs-lookup"><span data-stu-id="cdf8d-112">Each outbound connection from an internal device translates to a different source TCP port on the public IP address.</span></span> 
  
## <a name="why-do-you-need-to-have-so-many-connections-open-to-office-365-at-the-same-time"></a><span data-ttu-id="cdf8d-113">¿Por qué necesita tener tantas conexiones abiertas a Office 365 al mismo tiempo?</span><span class="sxs-lookup"><span data-stu-id="cdf8d-113">Why do you need to have so many connections open to Office 365 at the same time?</span></span>

<span data-ttu-id="cdf8d-114">Outlook puede abrir ocho o más conexiones (en situaciones en las que hay complementos, calendarios compartidos, buzones de correo, etc.).</span><span class="sxs-lookup"><span data-stu-id="cdf8d-114">Outlook may open eight or more connections (in situations where there are add-ins, shared calendars, mailboxes, etc.).</span></span> <span data-ttu-id="cdf8d-115">Como hay un máximo de 64.000 puertos disponibles en un dispositivo NAT basado en Windows, puede haber un máximo de 8.000 usuarios detrás de una dirección IP antes de que se agoten los puertos.</span><span class="sxs-lookup"><span data-stu-id="cdf8d-115">Because there are a maximum of 64,000 ports available on a Windows-based NAT device, there can be a maximum of 8,000 users behind an IP address before the ports are exhausted.</span></span> <span data-ttu-id="cdf8d-116">Tenga en cuenta que si los clientes usan dispositivos que no están basados en el sistema operativo Windows para NAT, los puertos totales disponibles dependen de qué dispositivo o software NAT se esté usando.</span><span class="sxs-lookup"><span data-stu-id="cdf8d-116">Note that if customers are using non-Windows OS-based devices for NAT, the total available ports are dependent on what NAT device or software is being used.</span></span> <span data-ttu-id="cdf8d-117">En este escenario, el número máximo de puertos podría ser inferior a 64.000.</span><span class="sxs-lookup"><span data-stu-id="cdf8d-117">In this scenario, the maximum number of ports could be less than 64,000.</span></span> <span data-ttu-id="cdf8d-118">La disponibilidad de los puertos también se ve afectada por otros factores, como Windows, restringiendo 4.000 puertos para su propio uso, lo que reduce el número total de puertos disponibles a 60, 000. puede haber otras aplicaciones, como Internet Explorer, que se puedan conectar al mismo tiempo y que requieran puertos adicionales.</span><span class="sxs-lookup"><span data-stu-id="cdf8d-118">Availability of ports is also affected by other factors such as Windows restricting 4,000 ports for its own use, which reduces the total number of available ports to 60,000.There may be other applications, such as Internet Explorer, that could connect at the same time, requiring additional ports.</span></span>
  
## <a name="calculating-maximum-supported-devices-behind-a-single-public-ip-address-with-office-365"></a><span data-ttu-id="cdf8d-119">Calcular el número máximo de dispositivos admitidos detrás de una sola dirección IP pública con Office 365</span><span class="sxs-lookup"><span data-stu-id="cdf8d-119">Calculating maximum supported devices behind a single public IP address with Office 365</span></span>

<span data-ttu-id="cdf8d-120">Para determinar el número máximo de dispositivos que hay detrás de una sola dirección IP pública, debe supervisar el tráfico de red para determinar el consumo de puertos máximo por cliente.</span><span class="sxs-lookup"><span data-stu-id="cdf8d-120">To determine the maximum number of devices behind a single public IP address, you should monitor network traffic to determine peak port consumption per client.</span></span> <span data-ttu-id="cdf8d-121">Además, se debe usar un factor máximo para el uso del puerto (mínimo 4).</span><span class="sxs-lookup"><span data-stu-id="cdf8d-121">Also, a peak factor should be used for the port usage (minimum 4).</span></span> 
  
 <span data-ttu-id="cdf8d-122">**Use la siguiente fórmula para calcular el número de dispositivos admitidos por dirección IP:**</span><span class="sxs-lookup"><span data-stu-id="cdf8d-122">**Use the following formula to calculate the number of supported devices per IP address:**</span></span>
  
<span data-ttu-id="cdf8d-123">Dispositivos máximos admitidos detrás de una sola dirección IP pública = (64.000-puertos restringidos)/(consumo máximo de puertos + factor máximo)</span><span class="sxs-lookup"><span data-stu-id="cdf8d-123">Maximum supported devices behind a single public IP address = (64,000 - restricted ports)/(Peak port consumption + peak factor)</span></span>
  
 <span data-ttu-id="cdf8d-124">**Por ejemplo, si se cumplen las siguientes condiciones:**</span><span class="sxs-lookup"><span data-stu-id="cdf8d-124">**For example, if the following were true:**</span></span>
  
- <span data-ttu-id="cdf8d-125">**Puertos restringidos:** 4.000 para el sistema operativo</span><span class="sxs-lookup"><span data-stu-id="cdf8d-125">**Restricted ports:** 4,000 for the operating system</span></span>

- <span data-ttu-id="cdf8d-126">**Consumo de puertos máximo:** 6 por dispositivo</span><span class="sxs-lookup"><span data-stu-id="cdf8d-126">**Peak port consumption:** 6 per device</span></span>

- <span data-ttu-id="cdf8d-127">**Factor máximo:** 4</span><span class="sxs-lookup"><span data-stu-id="cdf8d-127">**Peak factor:** 4</span></span>

<span data-ttu-id="cdf8d-128">A continuación, el máximo de dispositivos admitidos detrás de una sola dirección IP pública = (64.000-4000)/(6 + 4) = 6.000</span><span class="sxs-lookup"><span data-stu-id="cdf8d-128">Then, the maximum supported devices behind a single public IP address = (64,000 - 4,000)/(6 + 4) = 6,000</span></span>
  
<span data-ttu-id="cdf8d-129">Con el lanzamiento del paquete de hospedaje de Office 365, incluido en las actualizaciones de septiembre de 2011 para Microsoft Office Outlook 2007 o de noviembre de 2011 para Microsoft Outlook 2010, o una actualización posterior, el número de conexiones de Outlook (Office Outlook 2007 con Service Pack 2 y Outlook 2010) a Exchange puede ser tan solo 2.</span><span class="sxs-lookup"><span data-stu-id="cdf8d-129">With the release of Office 365 hosting pack, included in the updates from September 2011 for Microsoft Office Outlook 2007, or November 2011 for Microsoft Outlook 2010, or a later update, the number of connections from Outlook (both Office Outlook 2007 with Service Pack 2 and Outlook 2010) to Exchange can be as few as 2.</span></span> <span data-ttu-id="cdf8d-130">Necesitará tener en cuentan los diferentes sistemas operativos, comportamientos de usuario, etc., para determinar el número mínimo y máximo de puertos que la red necesitará como pico.</span><span class="sxs-lookup"><span data-stu-id="cdf8d-130">You'll need to factor in the different operating systems, user behaviors, and so on to determine the minimum and maximum number of ports that your network will require at peak.</span></span>
  
<span data-ttu-id="cdf8d-131">Si desea admitir más dispositivos detrás de una sola dirección IP pública, siga los pasos descritos para evaluar el número máximo de dispositivos que se pueden admitir:</span><span class="sxs-lookup"><span data-stu-id="cdf8d-131">If you want to support more devices behind a single public IP address, follow the steps outlined to assess the maximum number of devices that can be supported:</span></span>
  
<span data-ttu-id="cdf8d-132">Supervise el tráfico de red para determinar el consumo de puertos máximo por cliente.</span><span class="sxs-lookup"><span data-stu-id="cdf8d-132">Monitor network traffic to determine peak port consumption per client.</span></span> <span data-ttu-id="cdf8d-133">Debe recopilar estos datos:</span><span class="sxs-lookup"><span data-stu-id="cdf8d-133">You should collect this data:</span></span>
  
- <span data-ttu-id="cdf8d-134">Desde varias ubicaciones</span><span class="sxs-lookup"><span data-stu-id="cdf8d-134">From multiple locations</span></span>
    
- <span data-ttu-id="cdf8d-135">Desde varios dispositivos</span><span class="sxs-lookup"><span data-stu-id="cdf8d-135">From multiple devices</span></span>
    
- <span data-ttu-id="cdf8d-136">En varias ocasiones</span><span class="sxs-lookup"><span data-stu-id="cdf8d-136">At multiple times</span></span>
    
<span data-ttu-id="cdf8d-137">Use la fórmula anterior para calcular el número máximo de usuarios por dirección IP que se pueden admitir en su entorno.</span><span class="sxs-lookup"><span data-stu-id="cdf8d-137">Use the preceding formula to calculate the maximum users per IP address that can be supported in their environment.</span></span>
  
<span data-ttu-id="cdf8d-138">Hay varios métodos para distribuir la carga de clientes a través de direcciones IP públicas adicionales.</span><span class="sxs-lookup"><span data-stu-id="cdf8d-138">There are various methods for distributing client load across additional public IP addresses.</span></span> <span data-ttu-id="cdf8d-139">Las estrategias disponibles dependen de las capacidades de la solución de puerta de enlace corporativa.</span><span class="sxs-lookup"><span data-stu-id="cdf8d-139">Strategies available depend on the capabilities of the corporate gateway solution.</span></span> <span data-ttu-id="cdf8d-140">La solución más sencilla es segmentar el espacio de direcciones de usuario y "asignar" estáticamente una cantidad de direcciones IP a cada puerta de enlace.</span><span class="sxs-lookup"><span data-stu-id="cdf8d-140">The simplest solution is to segment your user address space and statically "assign" a number of IP addresses to each gateway.</span></span> <span data-ttu-id="cdf8d-141">Otra alternativa que muchos dispositivos de puerta de enlace ofrece es la capacidad de usar un grupo de direcciones IP.</span><span class="sxs-lookup"><span data-stu-id="cdf8d-141">Another alternative that many gateway devices offer is the ability to use a pool of IP addresses.</span></span> <span data-ttu-id="cdf8d-142">La ventaja del grupo de direcciones es que es mucho más dinámica y menos probable que sea necesario ajustarse a medida que crece la base de usuarios.</span><span class="sxs-lookup"><span data-stu-id="cdf8d-142">The benefit of the address pool is that it is much more dynamic and less likely to require adjustment as your user base grows.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="cdf8d-143">Ver también</span><span class="sxs-lookup"><span data-stu-id="cdf8d-143">See also</span></span>

[<span data-ttu-id="cdf8d-144">Administrar puntos de conexión de Office 365</span><span class="sxs-lookup"><span data-stu-id="cdf8d-144">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[<span data-ttu-id="cdf8d-145">Preguntas frecuentes sobre extremos de Office 365</span><span class="sxs-lookup"><span data-stu-id="cdf8d-145">Office 365 endpoints FAQ</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
