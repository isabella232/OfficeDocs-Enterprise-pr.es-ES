---
title: Guía del laboratorio de pruebas Configurar un laboratorio de pruebas integrado de Exchange, Lync y SharePoint
ms.author: jhendr
author: JoanneHendrickson
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 48e16935-3429-456a-8fe6-50afa257924c
description: 'Resumen: obtenga información sobre cómo crear un entorno de pruebas que contenga un servidor con Exchange Server 2013, un servidor con Lync Server 2013 y un servidor con SharePoint Server 2013.'
ms.openlocfilehash: b5d4527c063b0bfbac205007a9642b8edafd813b
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897053"
---
# <a name="test-lab-guide-configure-an-integrated-exchange-lync-and-sharepoint-test-lab"></a><span data-ttu-id="2e037-103">Guía del laboratorio de pruebas: Configurar un laboratorio de pruebas integrado de Exchange, Lync y SharePoint</span><span class="sxs-lookup"><span data-stu-id="2e037-103">Test Lab Guide: Configure an integrated Exchange, Lync, and SharePoint test lab</span></span>

 <span data-ttu-id="2e037-104">**Resumen:** obtenga información sobre cómo crear un entorno de pruebas integrado que contenga un servidor con Exchange Server 2013, un servidor con Lync Server 2013 y un servidor con SharePoint Server 2013.</span><span class="sxs-lookup"><span data-stu-id="2e037-104">**Summary:** Learn how to create an integrated test lab that contains a server that runs Exchange Server 2013, a server that runs Lync Server 2013, and a server that runs SharePoint Server 2013.</span></span>
 
<span data-ttu-id="2e037-105">**Ver el vídeo informativo de la guía del entorno de pruebas de Exchange, Lync y SharePoint**</span><span class="sxs-lookup"><span data-stu-id="2e037-105">**Watch the integrated Exchange, Lync, and SharePoint test lab guide overview video**</span></span>

> [!VIDEO https://videoplayercdn.osi.office.net/hub/?csid=ux-cms-en-us-msoffice&uuid=8d1f00cc-b8b1-4394-9367-0cc9765e380a&AutoPlayVideo=false]
 
<span data-ttu-id="2e037-106">El entorno de pruebas que se obtiene con esta configuración, que incluye la autenticación de servidor a servidor entre los tres tipos de servidores, puede usarse para crear los escenarios multiproducto y las soluciones que usan un servidor con Exchange Server 2013, un servidor con Lync Server 2013 y un servidor con SharePoint Server 2013, así como para mostrar su funcionamiento.</span><span class="sxs-lookup"><span data-stu-id="2e037-106">The test lab that results from this configuration, which includes server-to-server authentication between all three types of servers, can be used to build out and demonstrate multi-product scenarios and solutions that use a server that runs Exchange Server 2013, a server that runs Lync Server 2013, and a server that runs SharePoint Server 2013.</span></span>
  
<span data-ttu-id="2e037-107">Este documento contiene instrucciones para:</span><span class="sxs-lookup"><span data-stu-id="2e037-107">This document contains instructions for:</span></span>
  
1. <span data-ttu-id="2e037-108">Configurar el entorno de pruebas de configuración básica de Windows Server 2012.</span><span class="sxs-lookup"><span data-stu-id="2e037-108">Configuring the Windows Server 2012 Base Configuration test lab.</span></span>
    
2. <span data-ttu-id="2e037-109">Instalar y configurar un nuevo servidor denominado SQL1.</span><span class="sxs-lookup"><span data-stu-id="2e037-109">Installing and configuring a new server named SQL1.</span></span>
    
3. <span data-ttu-id="2e037-110">Instalar SQL Server 2012 en el servidor SQL1.</span><span class="sxs-lookup"><span data-stu-id="2e037-110">Installing SQL Server 2012 on the SQL1 server.</span></span>
    
4. <span data-ttu-id="2e037-111">Instalar y configurar un nuevo equipo cliente denominado CLIENT2.</span><span class="sxs-lookup"><span data-stu-id="2e037-111">Installing and configuring a new client computer named CLIENT2.</span></span>
    
5. <span data-ttu-id="2e037-112">Instalar y configurar Exchange Server 2013 en EX1.</span><span class="sxs-lookup"><span data-stu-id="2e037-112">Installing and configuring Exchange Server 2013 on EX1.</span></span>
    
6. <span data-ttu-id="2e037-113">Instalar y configurar un nuevo servidor denominado LYNC1.</span><span class="sxs-lookup"><span data-stu-id="2e037-113">Installing and configuring a new server named LYNC1.</span></span>
    
7. <span data-ttu-id="2e037-114">Instalar Lync Server 2013 Standard Edition en LYNC1.</span><span class="sxs-lookup"><span data-stu-id="2e037-114">Installing Lync Server 2013 Standard Edition on LYNC1.</span></span>
    
8. <span data-ttu-id="2e037-115">Instalar SharePoint Server 2013 en SP1.</span><span class="sxs-lookup"><span data-stu-id="2e037-115">Installing SharePoint Server 2013 on SP1.</span></span>
    
9. <span data-ttu-id="2e037-116">Configurar la integración entre EX1, LYNC1 y SP1.</span><span class="sxs-lookup"><span data-stu-id="2e037-116">Configuring integration between EX1, LYNC1, and SP1.</span></span>
    
<span data-ttu-id="2e037-117">Para obtener información sobre cómo configurar este entorno de pruebas en Hyper-V, consulte el tema sobre el [hospedaje del entorno de pruebas integrado de Exchange, Lync y SharePoint con Windows Server 2012 Hyper-V](https://social.technet.microsoft.com/wiki/contents/articles/18483.hosting-the-integrated-exchange-lync-and-sharepoint-test-lab-with-windows-server-2012-hyper-v.aspx).</span><span class="sxs-lookup"><span data-stu-id="2e037-117">For information about how to configure this test lab in Hyper-V, see [Hosting the integrated Exchange, Lync, and SharePoint test lab with Windows Server 2012 Hyper-V](https://social.technet.microsoft.com/wiki/contents/articles/18483.hosting-the-integrated-exchange-lync-and-sharepoint-test-lab-with-windows-server-2012-hyper-v.aspx).</span></span>
  
## <a name="download-the-test-lab-guide"></a><span data-ttu-id="2e037-118">Descargar la guía de entorno de pruebas</span><span class="sxs-lookup"><span data-stu-id="2e037-118">Download the test lab guide</span></span>

<span data-ttu-id="2e037-119">[Guía del laboratorio de pruebas: configurar un Exchange integrada, Lync y laboratorio de pruebas de SharePoint](https://go.microsoft.com/fwlink/p/?LinkId=313670) (https://go.microsoft.com/fwlink/p/?LinkId=313670)</span><span class="sxs-lookup"><span data-stu-id="2e037-119">[Test Lab Guide: Configure an Integrated Exchange, Lync, and SharePoint Test Lab](https://go.microsoft.com/fwlink/p/?LinkId=313670) (https://go.microsoft.com/fwlink/p/?LinkId=313670)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2e037-120">Consulte también</span><span class="sxs-lookup"><span data-stu-id="2e037-120">See Also</span></span>

[<span data-ttu-id="2e037-121">Guías de entorno de pruebas</span><span class="sxs-lookup"><span data-stu-id="2e037-121">Test Lab Guides</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=202817)




