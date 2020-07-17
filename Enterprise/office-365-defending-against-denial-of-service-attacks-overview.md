---
title: Defenderse contra ataques por denegación de servicio en Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: Información general sobre los ataques de denegación de servicio (DoS).
ms.openlocfilehash: 2cbe5eb86402fd7b7888f39440a58935604c90eb
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998424"
---
# <a name="defend-against-denial-of-service-attacks-in-microsoft-365"></a><span data-ttu-id="68998-103">Defenderse contra ataques por denegación de servicio en Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="68998-103">Defend Against Denial-of-Service Attacks in Microsoft 365</span></span>

## <a name="introduction"></a><span data-ttu-id="68998-104">Introducción</span><span class="sxs-lookup"><span data-stu-id="68998-104">Introduction</span></span>

<span data-ttu-id="68998-105">Microsoft ofrece una infraestructura de confianza para más de 200 servicios en la nube hospedados en una infraestructura de nube global de más de 100 centros de recursos.</span><span class="sxs-lookup"><span data-stu-id="68998-105">Microsoft delivers a trustworthy infrastructure for more than 200 cloud services hosted in a global cloud infrastructure of more than 100 datacenters.</span></span> <span data-ttu-id="68998-106">Entre ellos se incluyen:</span><span class="sxs-lookup"><span data-stu-id="68998-106">These include:</span></span>

- <span data-ttu-id="68998-107">Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="68998-107">Microsoft Azure</span></span>
- <span data-ttu-id="68998-108">Microsoft Bing</span><span class="sxs-lookup"><span data-stu-id="68998-108">Microsoft Bing</span></span>
- <span data-ttu-id="68998-109">Microsoft Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="68998-109">Microsoft Dynamics 365</span></span>
- <span data-ttu-id="68998-110">Microsoft 365 y Office 365</span><span class="sxs-lookup"><span data-stu-id="68998-110">Microsoft 365 and Office 365</span></span>
- <span data-ttu-id="68998-111">Microsoft OneDrive</span><span class="sxs-lookup"><span data-stu-id="68998-111">Microsoft OneDrive</span></span>
- <span data-ttu-id="68998-112">Skype</span><span class="sxs-lookup"><span data-stu-id="68998-112">Skype</span></span>
- <span data-ttu-id="68998-113">Xbox Live</span><span class="sxs-lookup"><span data-stu-id="68998-113">Xbox Live</span></span>

<span data-ttu-id="68998-114">Como organización global con una presencia importante en Internet y muchas propiedades de Internet destacadas que proporcionan servicios en la nube, Microsoft es un objetivo común y amplio para los hackers y otras personas malintencionadas.</span><span class="sxs-lookup"><span data-stu-id="68998-114">As a global organization with a significant Internet presence and many prominent Internet properties that provide cloud services, Microsoft is a large, common target for hackers and other malicious individuals.</span></span> <span data-ttu-id="68998-115">La capa de comunicación de red entre los clientes y la nube de Microsoft es uno de los principales objetivos de ataques malintencionados.</span><span class="sxs-lookup"><span data-stu-id="68998-115">The network communication layer between clients and the Microsoft Cloud is one of the biggest targets of malicious attacks.</span></span> <span data-ttu-id="68998-116">De hecho, Microsoft es de manera continua y persistente bajo alguna forma de ciberataque basada en la red.</span><span class="sxs-lookup"><span data-stu-id="68998-116">In fact, Microsoft is continuously and persistently under some form of network-based cyberattack.</span></span> <span data-ttu-id="68998-117">En línea con esto, Microsoft usa principios de seguridad de defensa en profundidad para proteger sus redes y servicios en la nube.</span><span class="sxs-lookup"><span data-stu-id="68998-117">In line with this, Microsoft uses defense-in-depth security principles to protect its cloud services and networks.</span></span> <span data-ttu-id="68998-118">Sin sistemas de mitigación confiable y persistente que defienden contra estos ataques, los servicios en la nube de Microsoft estarán sin conexión y no estarán disponibles para los clientes.</span><span class="sxs-lookup"><span data-stu-id="68998-118">Without reliable and persistent mitigation systems that defend against these attacks, Microsoft's cloud services would be offline and unavailable to customers.</span></span>

## <a name="definition-and-symptoms-of-denial-of-service-attacks"></a><span data-ttu-id="68998-119">Definición y síntomas de ataques por denegación de servicio</span><span class="sxs-lookup"><span data-stu-id="68998-119">Definition and Symptoms of Denial-of-Service Attacks</span></span>

<span data-ttu-id="68998-120">Una forma de atacar los servicios de red es crear muchas solicitudes a los hosts de servicio para saturar la red y los servidores para denegar el servicio a los usuarios legítimos.</span><span class="sxs-lookup"><span data-stu-id="68998-120">One way to attack network services is to create many requests against service hosts to overwhelm the network and servers to deny service to legitimate users.</span></span> <span data-ttu-id="68998-121">Esto se conoce como un ataque de denegación de servicio (DoS).</span><span class="sxs-lookup"><span data-stu-id="68998-121">This is referred to as a denial-of-service (DoS) attack.</span></span> <span data-ttu-id="68998-122">Cuando varios actores, extremos o vectores realizan el ataque, se hace referencia a él como un ataque de denegación de servicio (DDoS) distribuido.</span><span class="sxs-lookup"><span data-stu-id="68998-122">When the attack is performed by multiple actors, endpoints, and/or vectors, it is referred to as a distributed denial-of-service (DDoS) attack.</span></span> <span data-ttu-id="68998-123">Aunque los medios, motivos y objetivos varían, los ataques entre DoS y DDoS suelen estar formados por los esfuerzos para evitar que un sitio o servicio de Internet funcione correctamente o en su totalidad, ya sea de forma temporal o indefinida.</span><span class="sxs-lookup"><span data-stu-id="68998-123">Although the means, motives, and targets vary, DoS and DDoS attacks generally consist of efforts to prevent an Internet site or service from functioning correctly or at all, either temporarily or indefinitely.</span></span>

<span data-ttu-id="68998-124">El equipo de [preparación de emergencia para equipos de Estados Unidos](https://www.us-cert.gov/) (US-CERT) define los síntomas de ataques dos para incluir:</span><span class="sxs-lookup"><span data-stu-id="68998-124">The [United States Computer Emergency Readiness Team](https://www.us-cert.gov/) (US-CERT) defines symptoms of DoS attacks to include:</span></span>

- <span data-ttu-id="68998-125">Rendimiento de red inusualmente lento (al abrir archivos o acceder a sitios de Internet)</span><span class="sxs-lookup"><span data-stu-id="68998-125">Unusually slow network performance (when opening files or accessing Internet sites)</span></span>
- <span data-ttu-id="68998-126">No disponibilidad de un sitio web</span><span class="sxs-lookup"><span data-stu-id="68998-126">Unavailability of a Web site</span></span>
- <span data-ttu-id="68998-127">Incapacidad para obtener acceso a un sitio web</span><span class="sxs-lookup"><span data-stu-id="68998-127">Inability to access a Web site</span></span>
- <span data-ttu-id="68998-128">Aumento espectacular en el correo no deseado recibido</span><span class="sxs-lookup"><span data-stu-id="68998-128">Dramatic increase in received spam</span></span>
- <span data-ttu-id="68998-129">Desconexión de una conexión a Internet inalámbrica o cableada</span><span class="sxs-lookup"><span data-stu-id="68998-129">Disconnection of a wireless or wired Internet connection</span></span>
- <span data-ttu-id="68998-130">Pérdida a largo plazo de acceso a la web o a cualquier servicio de Internet</span><span class="sxs-lookup"><span data-stu-id="68998-130">Long-term loss of access to the Web or any Internet services</span></span>

## <a name="related-topics"></a><span data-ttu-id="68998-131">Temas relacionados</span><span class="sxs-lookup"><span data-stu-id="68998-131">Related Topics</span></span>

- [<span data-ttu-id="68998-132">Principios básicos de la defensa contra ataques por denegación de servicio</span><span class="sxs-lookup"><span data-stu-id="68998-132">Core Principles of Defense Against Denial-of-Service Attacks</span></span>](office-365-core-principles-of-defense-against-dos-attacks.md)
- [<span data-ttu-id="68998-133">Estrategia de la defensa de denegación de servicio de Microsoft</span><span class="sxs-lookup"><span data-stu-id="68998-133">Microsoft's Denial-of-Service Defense Strategy</span></span>](office-365-microsoft-dos-defense-strategy.md)
- [<span data-ttu-id="68998-134">Defensa de los servicios en la nube de Microsoft contra ataques por denegación de servicio</span><span class="sxs-lookup"><span data-stu-id="68998-134">Defending Microsoft Cloud Services Against Denial-of-Service Attacks</span></span>](office-365-defending-cloud-services-against-dos-attacks.md)
