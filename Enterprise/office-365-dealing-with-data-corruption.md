---
title: Microsoft 365 tratar los daños en los datos
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
ms.custom: seo-marvel-apr2020
description: En este artículo se explican los datos dañados en Microsoft 365 y los esfuerzos realizados por Microsoft para evitar y recuperar datos.
ms.openlocfilehash: dc8e865a69e110fa0a68e6cd9d9f4d6b45d43d71
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606636"
---
# <a name="dealing-with-data-corruption-in-microsoft-365"></a><span data-ttu-id="d0438-103">Información relacionada con los datos dañados en Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="d0438-103">Dealing with Data Corruption in Microsoft 365</span></span>

<span data-ttu-id="d0438-104">Uno de los aspectos desafiantes de la ejecución de un servicio en la nube a gran escala es cómo controlar los daños en los datos, dado el gran volumen de datos y sistemas independientes.</span><span class="sxs-lookup"><span data-stu-id="d0438-104">One of the challenging aspects of running a large-scale cloud service is how to handle data corruption, given the large volume of data and independent systems.</span></span> <span data-ttu-id="d0438-105">Los daños en los datos pueden deberse a:</span><span class="sxs-lookup"><span data-stu-id="d0438-105">Data corruption can be caused by:</span></span>

- <span data-ttu-id="d0438-106">Errores de aplicaciones o de infraestructura, que dañan parte o todo el estado de la aplicación</span><span class="sxs-lookup"><span data-stu-id="d0438-106">Application or infrastructure bugs, corrupting some or all of the application state</span></span>
- <span data-ttu-id="d0438-107">Problemas de hardware que producen datos perdidos o la incapacidad de leer datos</span><span class="sxs-lookup"><span data-stu-id="d0438-107">Hardware issues that result in lost data or an inability to read data</span></span>
- <span data-ttu-id="d0438-108">Errores operativos humanos</span><span class="sxs-lookup"><span data-stu-id="d0438-108">Human operational errors</span></span>
- <span data-ttu-id="d0438-109">Hackers malintencionados y empleados descontentos</span><span class="sxs-lookup"><span data-stu-id="d0438-109">Malicious hackers and disgruntled employees</span></span>
- <span data-ttu-id="d0438-110">Incidentes en servicios externos que resultan en alguna pérdida de datos</span><span class="sxs-lookup"><span data-stu-id="d0438-110">Incidents in external services that result in some loss of data</span></span>

<span data-ttu-id="d0438-111">Debido a que una mayor resistencia en la integridad de los datos significa menos incidentes de daños en los datos, Microsoft ha integrado los mecanismos de protección 365 de Microsoft para evitar que se produzcan daños, así como sistemas y procesos que nos permiten recuperar datos si es así.</span><span class="sxs-lookup"><span data-stu-id="d0438-111">Because greater resiliency in data integrity means fewer data corruption incidents, Microsoft has built into Microsoft 365 protection mechanisms to prevent corruption from happening, as well as systems and processes that enable us to recover data if it does.</span></span> <span data-ttu-id="d0438-112">Las comprobaciones y procesos existen en las distintas fases del proceso de lanzamiento de ingeniería para aumentar la resistencia contra daños en los datos, entre los que se incluyen:</span><span class="sxs-lookup"><span data-stu-id="d0438-112">Checks and processes exist within the various stages of the engineering release process to increase resiliency against data corruption, including:</span></span>

- <span data-ttu-id="d0438-113">Diseño del sistema</span><span class="sxs-lookup"><span data-stu-id="d0438-113">System Design</span></span>
- <span data-ttu-id="d0438-114">Estructura y organización del código</span><span class="sxs-lookup"><span data-stu-id="d0438-114">Code organization and structure</span></span>
- <span data-ttu-id="d0438-115">Revisión de código</span><span class="sxs-lookup"><span data-stu-id="d0438-115">Code review</span></span>
- <span data-ttu-id="d0438-116">Pruebas unitarias, pruebas de integración y pruebas del sistema</span><span class="sxs-lookup"><span data-stu-id="d0438-116">Unit tests, integration tests, and system tests</span></span>
- <span data-ttu-id="d0438-117">Pruebas/puertas de cables de viaje</span><span class="sxs-lookup"><span data-stu-id="d0438-117">Trip wires tests/gates</span></span>

<span data-ttu-id="d0438-118">Dentro de los entornos de producción de Microsoft 365, la replicación del mismo nivel entre centros de datos garantiza que siempre habrá varias copias activas de todos los datos.</span><span class="sxs-lookup"><span data-stu-id="d0438-118">Within Microsoft 365 production environments, peer replication between datacenters ensures that there are always multiple live copies of any data.</span></span> <span data-ttu-id="d0438-119">Las imágenes y los scripts estándar se usan para recuperar los servidores perdidos y los datos replicados se usan para restaurar los datos del cliente.</span><span class="sxs-lookup"><span data-stu-id="d0438-119">Standard images and scripts are used to recover lost servers, and replicated data is used to restore customer data.</span></span> <span data-ttu-id="d0438-120">Debido a las comprobaciones y procesos integrados de resistencia de datos, Microsoft solo mantiene copias de seguridad de la documentación del sistema de información de Microsoft 365 (incluida la documentación relacionada con la seguridad), mediante la replicación integrada en SharePoint Online y nuestra herramienta de repositorio de código interno, Source Depot.</span><span class="sxs-lookup"><span data-stu-id="d0438-120">Because of the built-in data resiliency checks and processes, Microsoft maintains backups only of Microsoft 365 information system documentation (including security-related documentation), using built-in replication in SharePoint Online and our internal code repository tool, Source Depot.</span></span> <span data-ttu-id="d0438-121">La documentación del sistema se almacena en SharePoint Online y Source Depot contiene imágenes del sistema y de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="d0438-121">System documentation is stored in SharePoint Online, and Source Depot contains system and application images.</span></span> <span data-ttu-id="d0438-122">SharePoint Online y Source Depot usan el control de versiones y se replican casi en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="d0438-122">Both SharePoint Online and Source Depot use versioning and are replicated in near real time.</span></span>
