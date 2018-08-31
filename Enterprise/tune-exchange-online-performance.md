---
title: Ajustar el rendimiento de Exchange Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/14/2017
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Adm_O365
ms.assetid: 026e83cb-a945-4543-97b0-a8af6e80ac61
description: Este artículo contiene sugerencias generales y vínculos a otros recursos que le indican cómo mejorar el rendimiento de Exchange Online.
ms.openlocfilehash: 20a3a61517212df88cb380ade47c268c429e52a8
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22543067"
---
# <a name="tune-exchange-online-performance"></a><span data-ttu-id="4bce7-103">Ajustar el rendimiento de Exchange Online</span><span class="sxs-lookup"><span data-stu-id="4bce7-103">Tune Exchange Online performance</span></span>

<span data-ttu-id="4bce7-p101">Este artículo contiene sugerencias generales y vínculos a otros recursos que le indican cómo mejorar el rendimiento de Exchange Online. En este artículo es parte del proyecto de [Diseño de la red y ajuste del rendimiento de Office 365](https://aka.ms/tune) .</span><span class="sxs-lookup"><span data-stu-id="4bce7-p101">This article contains general tips and links to other resources that tell you how to improve performance of Exchange Online. This article is part of the [Network planning and performance tuning for Office 365](https://aka.ms/tune) project.</span></span>
   
## <a name="things-to-consider-in-order-to-improve-exchange-online-performance"></a><span data-ttu-id="4bce7-106">Cosas que hay que tener en cuenta con el fin de mejorar el rendimiento de Exchange Online</span><span class="sxs-lookup"><span data-stu-id="4bce7-106">Things to consider in order to improve Exchange Online performance</span></span>

<span data-ttu-id="4bce7-107">Para mejorar la velocidad de la migración y reducir las restricciones de ancho de banda de la organización de Exchange Online, tenga en cuenta lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="4bce7-107">To improve the speed of migration and reduce your organization's bandwidth constraints for Exchange Online, consider the following:</span></span>
  
- <span data-ttu-id="4bce7-p102">**Reduzca el tamaño de los buzones de correo.** Un buzón de correo más pequeño mejora la velocidad de migración.</span><span class="sxs-lookup"><span data-stu-id="4bce7-p102">**Reduce mailbox sizes.** Smaller mailbox size improves migration speed.</span></span> 
    
- <span data-ttu-id="4bce7-p103">**Use las capacidades de movimiento de buzones de correo con una implementación híbrida de Exchange.** Con una implementación híbrida de Exchange, el correo sin conexión (en forma de archivos .OST) no requiere una nueva descarga al migrar a Exchange Online. Esto reduce significativamente los requisitos de ancho de banda para descarga.</span><span class="sxs-lookup"><span data-stu-id="4bce7-p103">**Use the mailbox move capabilities with an Exchange hybrid deployment.** With an Exchange hybrid deployment, offline mail (in the form of .OST files) does not require re-download when migrating to Exchange Online. This significantly reduces your download bandwidth requirements.</span></span> 
    
- <span data-ttu-id="4bce7-p104">**Programe los movimientos de buzones para que se realicen durante períodos de poco tráfico de Internet y poco uso de Exchange local.** A la hora de programar movimientos, las solicitudes de migración se envían al proxy de replicación de buzones de correo y pueden no ocurrir de forma inmediata.</span><span class="sxs-lookup"><span data-stu-id="4bce7-p104">**Schedule mailbox moves to occur during periods of low Internet traffic and low on-premises Exchange use.** When scheduling moves, migration requests are submitted to the mailbox replication proxy and may not take place immediately.</span></span> 
    
- <span data-ttu-id="4bce7-p105">**Usar popouts lean para Outlook en el web.** Popouts lean más pequeños, proporcionar menos versiones con uso intensivo de memoria de determinados mensajes de correo electrónico en Microsoft Edge o Internet Explorer mediante la representación de algunos componentes en el servidor. Para obtener más información, vea [uso popouts lean para reducir la memoria que se usa al leer los mensajes de correo](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf).</span><span class="sxs-lookup"><span data-stu-id="4bce7-p105">**Use lean popouts for Outlook on the web.** Lean popouts provide smaller, less memory-intensive versions of certain email messages in Microsoft Edge or Internet Explorer by rendering some components on the server. For more information, see [Use lean popouts to reduce memory used when reading mail messages](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf).</span></span>
    
<span data-ttu-id="4bce7-118">Para obtener más información acerca del rendimiento de la migración de Exchange, consulte [rendimiento de la migración de Office 365 y procedimientos recomendados](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57).</span><span class="sxs-lookup"><span data-stu-id="4bce7-118">For more information about Exchange migration performance, see [Office 365 migration performance and best practices](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57).</span></span>
  

