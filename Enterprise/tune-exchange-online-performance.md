---
title: Ajustar el rendimiento de Exchange Online
ms.author: krowley
author: tracyp
manager: laurawi
ms.date: 12/14/2017
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.assetid: 026e83cb-a945-4543-97b0-a8af6e80ac61
description: Este artículo contiene sugerencias generales y vínculos a otros recursos que le indican cómo mejorar el rendimiento de Exchange Online.
ms.openlocfilehash: 4ef0276345a3d7f1c9aeba016824f9cb06c475cb
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841087"
---
# <a name="tune-exchange-online-performance"></a><span data-ttu-id="b747f-103">Ajustar el rendimiento de Exchange Online</span><span class="sxs-lookup"><span data-stu-id="b747f-103">Tune Exchange Online performance</span></span>

<span data-ttu-id="b747f-104">Este artículo contiene sugerencias generales y vínculos a otros recursos que le indican cómo mejorar el rendimiento de Exchange Online, especialmente delante de una migración.</span><span class="sxs-lookup"><span data-stu-id="b747f-104">This article contains general tips and links to other resources that tell you how to improve performance of Exchange Online, particularly in front of a migration.</span></span> <span data-ttu-id="b747f-105">Este artículo forma parte del proyecto [planeación de red y ajuste del rendimiento para Office 365](https://aka.ms/tune) .</span><span class="sxs-lookup"><span data-stu-id="b747f-105">This article is part of the [Network planning and performance tuning for Office 365](https://aka.ms/tune) project.</span></span>
   
## <a name="things-to-consider-in-order-to-improve-exchange-online-performance"></a><span data-ttu-id="b747f-106">Aspectos que se deben tener en cuenta para mejorar el rendimiento de Exchange Online</span><span class="sxs-lookup"><span data-stu-id="b747f-106">Things to consider in order to improve Exchange Online performance</span></span>

<span data-ttu-id="b747f-107">Para mejorar la velocidad de migración y reducir las restricciones de ancho de banda de la organización para Exchange Online, tenga en cuenta lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="b747f-107">To improve the speed of migration and reduce your organization's bandwidth constraints for Exchange Online, consider the following:</span></span>
  
- <span data-ttu-id="b747f-108">**Reducir el tamaño de los buzones.**</span><span class="sxs-lookup"><span data-stu-id="b747f-108">**Reduce mailbox sizes.**</span></span> <span data-ttu-id="b747f-109">El tamaño de buzón más pequeño mejora la velocidad de migración.</span><span class="sxs-lookup"><span data-stu-id="b747f-109">Smaller mailbox size improves migration speed.</span></span> 
    
- <span data-ttu-id="b747f-110">**Use las funciones de movimiento de buzones con una implementación híbrida de Exchange.**</span><span class="sxs-lookup"><span data-stu-id="b747f-110">**Use the mailbox move capabilities with an Exchange hybrid deployment.**</span></span> <span data-ttu-id="b747f-111">Con una implementación híbrida de Exchange, correo sin conexión (en forma de. OST) no requieren que se vuelvan a descargar al migrar a Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="b747f-111">With an Exchange hybrid deployment, offline mail (in the form of .OST files) does not require re-download when migrating to Exchange Online.</span></span> <span data-ttu-id="b747f-112">Esto reduce considerablemente los requisitos de ancho de banda de descarga.</span><span class="sxs-lookup"><span data-stu-id="b747f-112">This significantly reduces your download bandwidth requirements.</span></span> 
    
- <span data-ttu-id="b747f-113">**Programar movimientos de buzones de correo para que se produzcan durante períodos de poco tráfico de Internet y el uso de Exchange local bajo.**</span><span class="sxs-lookup"><span data-stu-id="b747f-113">**Schedule mailbox moves to occur during periods of low Internet traffic and low on-premises Exchange use.**</span></span> <span data-ttu-id="b747f-114">Al programar movimientos, las solicitudes de migración se envían al proxy de replicación de buzones y es posible que no tengan lugar inmediatamente.</span><span class="sxs-lookup"><span data-stu-id="b747f-114">When scheduling moves, migration requests are submitted to the mailbox replication proxy and may not take place immediately.</span></span> 
    
- <span data-ttu-id="b747f-115">**Usar lean ventanas emergentes para Outlook en la Web.**</span><span class="sxs-lookup"><span data-stu-id="b747f-115">**Use lean popouts for Outlook on the web.**</span></span> <span data-ttu-id="b747f-116">Lean ventanas emergentes proporcionan versiones más pequeñas y intensivas de memoria de determinados mensajes de correo electrónico en Microsoft Edge o Internet Explorer al representar algunos componentes en el servidor.</span><span class="sxs-lookup"><span data-stu-id="b747f-116">Lean popouts provide smaller, less memory-intensive versions of certain email messages in Microsoft Edge or Internet Explorer by rendering some components on the server.</span></span> <span data-ttu-id="b747f-117">Para obtener más información, vea [use lean ventanas emergentes para reducir la memoria usada al leer mensajes de correo](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf).</span><span class="sxs-lookup"><span data-stu-id="b747f-117">For more information, see [Use lean popouts to reduce memory used when reading mail messages](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf).</span></span>


## <a name="general-advice"></a><span data-ttu-id="b747f-118">Consejo General</span><span class="sxs-lookup"><span data-stu-id="b747f-118">General advice</span></span>

- <span data-ttu-id="b747f-119">Asegúrese de que la búsqueda de DNS para outlook.office.com entra en el centro de seguridad de MS en una ubicación de entrada lógica para su ubicación.</span><span class="sxs-lookup"><span data-stu-id="b747f-119">Make certain that DNS lookup for outlook.office.com enters the MS-datacenter at a logical entry location for your location.</span></span>

- <span data-ttu-id="b747f-120">Consultar el almacenamiento en memoria caché de buzones y elegir las opciones adecuadas (re.</span><span class="sxs-lookup"><span data-stu-id="b747f-120">Research mailbox caching and choose the appropriate options (re.</span></span> <span data-ttu-id="b747f-121">período de almacenamiento en caché, almacenamiento de buzones compartidos, et cetera).</span><span class="sxs-lookup"><span data-stu-id="b747f-121">caching period, shared mailbox caching, et cetera).</span></span>

- <span data-ttu-id="b747f-122">Mantenga los datos de Outlook pasando por las conexiones VPN (a una oficina central) antes de pasar a través de Internet.</span><span class="sxs-lookup"><span data-stu-id="b747f-122">Keep your Outlook data from passing over VPN connections (to a central office) before it goes over the Internet.</span></span>

- <span data-ttu-id="b747f-123">Asegúrese de que los datos del buzón cumplan con las limitaciones en la carpeta y los importes de elementos.</span><span class="sxs-lookup"><span data-stu-id="b747f-123">Be sure your mailbox data adheres to the limitations on folder, and item, amounts.</span></span>
    
<span data-ttu-id="b747f-124">Para obtener más información acerca del rendimiento de la migración de Exchange, consulte [Office 365 Migration Performance and Best Practices](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57).</span><span class="sxs-lookup"><span data-stu-id="b747f-124">For more information about Exchange migration performance, see [Office 365 migration performance and best practices](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57).</span></span>
  

