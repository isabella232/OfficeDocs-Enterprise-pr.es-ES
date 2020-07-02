---
title: Automatizar la recopilación de archivos para la exhibición de documentos electrónicos
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: ''
ms.assetid: 8d751419-d81b-4eb7-a2e5-8b03ccbf670c
search.appverid:
- MET150
description: 'Resumen: Aprenda a automatizar una recopilación de archivos de los equipos del usuario para la exhibición de documentos electrónicos.'
ms.openlocfilehash: 83bd55ff786803cfcb3eec9430d72de30179d000
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997981"
---
# <a name="automate-file-collection-for-ediscovery"></a><span data-ttu-id="f9ce6-103">Automatizar la recopilación de archivos para la exhibición de documentos electrónicos</span><span class="sxs-lookup"><span data-stu-id="f9ce6-103">Automate file collection for eDiscovery</span></span>

<span data-ttu-id="f9ce6-104">All companies face the potential of lawsuits or other types of legal action.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-104">All companies face the potential of lawsuits or other types of legal action.</span></span> <span data-ttu-id="f9ce6-105">While legal departments work to reduce that exposure, litigation is a fact of business life.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-105">While legal departments work to reduce that exposure, litigation is a fact of business life.</span></span> <span data-ttu-id="f9ce6-106">When a company faces legal action, they are required, through the process of legal discovery, to provide all relevant documentary materials to the court and to opposing counsel.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-106">When a company faces legal action, they are required, through the process of legal discovery, to provide all relevant documentary materials to the court and to opposing counsel.</span></span> 
  
<span data-ttu-id="f9ce6-107">eDiscovery is the process by which companies inventory, search, identify, preserve, filter, and make available the relevant documentary materials that exist in electronic form.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-107">eDiscovery is the process by which companies inventory, search, identify, preserve, filter, and make available the relevant documentary materials that exist in electronic form.</span></span> <span data-ttu-id="f9ce6-108">SharePoint 2013, Exchange Server 2013, Lync Server 2013, SharePoint Online, and Exchange Online can hold large amounts of documentary content.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-108">SharePoint 2013, Exchange Server 2013, Lync Server 2013, SharePoint Online, and Exchange Online can hold large amounts of documentary content.</span></span> <span data-ttu-id="f9ce6-109">Depending on the version, these products may support eDiscovery and in place holds (Lync via Exchange Server), making it easier for the legal teams to index, identify, hold, and filter the most relevant content for a given case.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-109">Depending on the version, these products may support eDiscovery and in place holds (Lync via Exchange Server), making it easier for the legal teams to index, identify, hold, and filter the most relevant content for a given case.</span></span>
  
<span data-ttu-id="f9ce6-110">Many documents are stored on users' (Custodians) local computers, not in a centralized location.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-110">Many documents are stored on users' (Custodians) local computers, not in a centralized location.</span></span> <span data-ttu-id="f9ce6-111">This makes it essentially impossible for SharePoint 2013 to search, and if it can't be searched, it can't be included in eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-111">This makes it essentially impossible for SharePoint 2013 to search, and if it can't be searched, it can't be included in eDiscovery.</span></span> <span data-ttu-id="f9ce6-112">This solution shows you how to use logon scripts, System Center Orchestrator 2012 R2 and Windows PowerShell for Exchange Server to automate the identification and collection of documentary materials from users' computers.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-112">This solution shows you how to use logon scripts, System Center Orchestrator 2012 R2 and Windows PowerShell for Exchange Server to automate the identification and collection of documentary materials from users' computers.</span></span>
  
## <a name="what-this-solution-does"></a><span data-ttu-id="f9ce6-113">Qué hace esta solución</span><span class="sxs-lookup"><span data-stu-id="f9ce6-113">What this solution does</span></span>

<span data-ttu-id="f9ce6-114">This solution uses a global security group, Group Policy, and a Windows PowerShell script to locate, inventory, and collect content and Outlook personal store (PST) files from users local computers to a hidden file share.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-114">This solution uses a global security group, Group Policy, and a Windows PowerShell script to locate, inventory, and collect content and Outlook personal store (PST) files from users local computers to a hidden file share.</span></span> <span data-ttu-id="f9ce6-115">From there, the PST files can be imported into either Exchange Server 2013 or Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-115">From there, the PST files can be imported into either Exchange Server 2013 or Exchange Online.</span></span> <span data-ttu-id="f9ce6-116">All files are then moved using a System Center Orchestrator 2012 R2 runbook to another file share in Microsoft Azure for long-term storage and indexing by SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-116">All files are then moved using a System Center Orchestrator 2012 R2 runbook to another file share in Microsoft Azure for long-term storage and indexing by SharePoint 2013.</span></span> <span data-ttu-id="f9ce6-117">You then use eDiscovery centers in your on-premises SharePoint 2013 deployment or in SharePoint Online as you regularly would to perform eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-117">You then use eDiscovery centers in your on-premises SharePoint 2013 deployment or in SharePoint Online as you regularly would to perform eDiscovery.</span></span> 
  
> [!IMPORTANT]
> <span data-ttu-id="f9ce6-118">This solution uses robocopy to copy files from custodian's computers to a centralized file share.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-118">This solution uses robocopy to copy files from custodian's computers to a centralized file share.</span></span> <span data-ttu-id="f9ce6-119">Because robocopy does not copy files that are open or locked, any files, including PST files, that the custodian has open will not be collected.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-119">Because robocopy does not copy files that are open or locked, any files, including PST files, that the custodian has open will not be collected.</span></span> <span data-ttu-id="f9ce6-120">You will have to collect them manually.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-120">You will have to collect them manually.</span></span> <span data-ttu-id="f9ce6-121">This solution does provide you with a list that explicitly identifies the files it cannot copy and the full path to each file.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-121">This solution does provide you with a list that explicitly identifies the files it cannot copy and the full path to each file.</span></span> 
  
<span data-ttu-id="f9ce6-122">El siguiente diagrama le dirige por todos los pasos y elementos de la solución</span><span class="sxs-lookup"><span data-stu-id="f9ce6-122">The following diagram walks you through all the steps and elements of the solution.</span></span>
  
![Introducción a la solución de recopilación automatizada de archivos](media/dbb447b5-c74c-4956-986c-10a1d047ac99.png)
  
|<span data-ttu-id="f9ce6-124">\*\*\*\*Leyenda\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="f9ce6-124">\*\*\*\*Legend\*\*\*\*</span></span>||
|:-----|:-----|
|![Llamada magenta 1](media/000026a3-2bf0-4678-b468-ccb5f81da6f1.png)|<span data-ttu-id="f9ce6-126">Crear un objeto de directiva de grupo (GPO) y asociarlo a la recopilación de scripts de inicio de sesión</span><span class="sxs-lookup"><span data-stu-id="f9ce6-126">Create a Group Policy object (GPO), and associate it with the collection logon script.</span></span>  <br/> |
|![Llamada magenta 2](media/a31b11e2-3597-42a4-933e-b6af11ed6ef1.png)| <span data-ttu-id="f9ce6-128">  Configurar el filtro de seguridad GPO para aplicar el GPO solo al grupo de administradores</span><span class="sxs-lookup"><span data-stu-id="f9ce6-128">Configure the GPO security filter to apply the GPO only to the Custodians group.</span></span> <br/> |
|![Llamada magenta 3](media/3ced060c-daec-460d-a9b5-260a3dfcae36.png)|<span data-ttu-id="f9ce6-130">Cuando un administrador inicia sesión y se ejecuta el GPO, se llama a la recopilación de scripts de inicio de sesión.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-130">A Custodian logs on and the GPO runs, calling the collection logon script.</span></span>  <br/> |
|![Llamada magenta 4](media/6f269d84-2559-49e3-b18e-af6ac94d0419.png)|<span data-ttu-id="f9ce6-132">La recopilación de scripts de inicio de sesión hace un inventario de todas las unidades adjuntadas de forma local del equipo de los administradores, en busca de los archivos que desea, y registra su ubicación.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-132">The collection logon script inventories all locally attached drives on the Custodians computer, searching for the files you want, and recording their location.</span></span>  <br/> |
|![Llamada magenta 5](media/4bf8898c-44ad-4524-b983-70175804eb85.png)|<span data-ttu-id="f9ce6-134">La recopilación de scripts de inicio de sesión copia los archivos inventariados en un recurso compartido de archivos oculto en el servidor de implementación.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-134">The collection logon script copies the inventoried files to a hidden file share on the staging server.</span></span>  <br/> |
|![Llamada magenta 6](media/99589726-0c7e-406b-a276-44301a135768.png)| <span data-ttu-id="f9ce6-136">(Opción A) Ejecute manualmente el script de importación de PST para importar los archivos PST recopilados en Exchange Server 2013.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-136">(Option A) Manually run the PST import script to import the collected PST files into Exchange Server 2013.</span></span> <br/> |
|![Llamada magenta 7](media/ff15e89c-d2fd-4614-9838-5e18287d578b.png)|<span data-ttu-id="f9ce6-138">(Opción B) Mediante la herramienta de importación y el proceso de 365 de Microsoft, importe los archivos PST recopilados en Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-138">(Option B) Using the Microsoft 365 Import tool and process, import the collected PST files into Exchange Online.</span></span>  <br/> |
|![Llamada magenta 8](media/aaf3bd3d-9508-4aaf-a3af-44ba501da63a.png)|<span data-ttu-id="f9ce6-140">Mueva todos los archivos recopilados a un recurso compartido de archivos de Azure para un almacenamiento a largo plazo con el Runbook MoveToColdStorageSystem Center Orchestrator 2012 R2.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-140">Move all collected files to an Azure file share for long term storage with the MoveToColdStorage System Center Orchestrator 2012 R2 runbook.</span></span> <br/> |
|![Llamada magenta 9](media/b354642e-445e-4723-a84a-b41f7ac6e774.png)|<span data-ttu-id="f9ce6-142">Indexe los archivos en el recurso compartido de archivos de almacenamiento en frío con SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-142">Index the files in the cold storage file share with SharePoint 2013.</span></span>  <br/> |
|![Llamada magenta 10](media/cebf7de5-7525-413b-9e52-638a4f8b2f74.png)|<span data-ttu-id="f9ce6-144">Realice eDiscovery en el contenido del almacenamiento en frío y en el Exchange Server 2013 local.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-144">Perform eDiscovery on content in cold storage and in the on-premises Exchange Server 2013.</span></span>  <br/> |
|![Llamada magenta 11](media/e59ab403-2f19-497a-92a5-549846dded66.png)|<span data-ttu-id="f9ce6-146">Realizar eDiscovery en el contenido de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-146">Perform eDiscovery on content in Microsoft 365.</span></span>  <br/> |
   
## <a name="prerequisites"></a><span data-ttu-id="f9ce6-147">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="f9ce6-147">Prerequisites</span></span>

<span data-ttu-id="f9ce6-148">The configuration of this solution requires many elements, most of which you likely have in place and configured if you're thinking about eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-148">The configuration of this solution requires many elements, most of which you likely have in place and configured if you're thinking about eDiscovery.</span></span> <span data-ttu-id="f9ce6-149">For the elements that you may not have or ones that require a specific configuration, we'll provide you with the links you need build out your base configuration.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-149">For the elements that you may not have or ones that require a specific configuration, we'll provide you with the links you need build out your base configuration.</span></span> <span data-ttu-id="f9ce6-150">You must have the base configuration in place before you configure the solution itself.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-150">You must have the base configuration in place before you configure the solution itself.</span></span>
  
### <a name="base-configuration"></a><span data-ttu-id="f9ce6-151">Configuración básica</span><span class="sxs-lookup"><span data-stu-id="f9ce6-151">Base configuration</span></span>

|<span data-ttu-id="f9ce6-152">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="f9ce6-152">**Element**</span></span>|<span data-ttu-id="f9ce6-153">**Vínculo**</span><span class="sxs-lookup"><span data-stu-id="f9ce6-153">**Link**</span></span>|
|:-----|:-----|
|<span data-ttu-id="f9ce6-154">Dominio de Servicios de dominio de Active Directory (AD DS)</span><span class="sxs-lookup"><span data-stu-id="f9ce6-154">Active Directory Domain Services (AD DS) domain</span></span>  <br/> ||
|<span data-ttu-id="f9ce6-155">Conectividad de Internet desde su red local</span><span class="sxs-lookup"><span data-stu-id="f9ce6-155">Internet connectivity from your on-premises network</span></span>  <br/> ||
|<span data-ttu-id="f9ce6-156">SQL Server 2012 para admitir SharePoint 2013 y System Center Orchestrator 2012 R2</span><span class="sxs-lookup"><span data-stu-id="f9ce6-156">SQL Server 2012 to support SharePoint 2013 and System Center Orchestrator 2012 R2</span></span>  <br/> |[<span data-ttu-id="f9ce6-157">Implementación de System Center Orchestrator: 2012</span><span class="sxs-lookup"><span data-stu-id="f9ce6-157">Deploying System Center Orchestrator - 2012</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
| <span data-ttu-id="f9ce6-158">Local o Azure basado en SharePoint 2013 para eDiscovery (necesario para la opción A)</span><span class="sxs-lookup"><span data-stu-id="f9ce6-158">On-premises or Azure based SharePoint 2013 for eDiscovery (required for Option A)</span></span> <br/> ||
|<span data-ttu-id="f9ce6-159">Servidor local de recurso compartido de archivos de implementación</span><span class="sxs-lookup"><span data-stu-id="f9ce6-159">On-premises file share server for staging</span></span>  <br/> ||
|<span data-ttu-id="f9ce6-160">Exchange Server 2013 local para la importación PST de la opción A</span><span class="sxs-lookup"><span data-stu-id="f9ce6-160">On-premises Exchange Server 2013 for Option A PST import</span></span>  <br/> |<span data-ttu-id="f9ce6-161">CU5 (15.913.22) está disponible en [CU5](https://go.microsoft.com/fwlink/p/?LinkId=613426).</span><span class="sxs-lookup"><span data-stu-id="f9ce6-161">CU5 (15.913.22) is available at [CU5](https://go.microsoft.com/fwlink/p/?LinkId=613426).</span></span>  <br/> |
|<span data-ttu-id="f9ce6-162">System Center Orchestrator 2012 R2</span><span class="sxs-lookup"><span data-stu-id="f9ce6-162">System Center Orchestrator 2012 R2</span></span>  <br/> |[<span data-ttu-id="f9ce6-163">Implementación de System Center Orchestrator: 2012</span><span class="sxs-lookup"><span data-stu-id="f9ce6-163">Deploying System Center Orchestrator - 2012</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
|<span data-ttu-id="f9ce6-164">Microsoft 365 E3 con Exchange Online y SharePoint Online (necesario para la opción B)</span><span class="sxs-lookup"><span data-stu-id="f9ce6-164">Microsoft 365 E3 with Exchange Online and SharePoint Online (required for Option B)</span></span>  <br/> |<span data-ttu-id="f9ce6-165">Para suscribirse a una suscripción a Microsoft 365 E3, consulte [suscripción a microsoft 365 E3](https://www.microsoft.com/microsoft-365/enterprise-e3-business-software?activetab=pivot%3aoverviewtab).</span><span class="sxs-lookup"><span data-stu-id="f9ce6-165">To sign up for a Microsoft 365 E3 subscription, see [Microsoft 365 E3 subscription](https://www.microsoft.com/microsoft-365/enterprise-e3-business-software?activetab=pivot%3aoverviewtab).</span></span>  <br/> |
|<span data-ttu-id="f9ce6-166">Suscripción a Azure con una máquina virtual</span><span class="sxs-lookup"><span data-stu-id="f9ce6-166">Azure subscription with a virtual machine</span></span>  <br/> |<span data-ttu-id="f9ce6-167">Para registrarse en Azure, consulte: [Suscribirse a Windows Azure](https://go.microsoft.com/fwlink/p/?LinkId=512010)</span><span class="sxs-lookup"><span data-stu-id="f9ce6-167">To sign up for a Azure, see [Subscribe to Windows Azure](https://go.microsoft.com/fwlink/p/?LinkId=512010)</span></span> <br/> |
|<span data-ttu-id="f9ce6-168">Una conexión VPN entre su red local y su suscripción a Azure</span><span class="sxs-lookup"><span data-stu-id="f9ce6-168">A VPN connection between your on-premises network and your Azure subscription</span></span>  <br/> |<span data-ttu-id="f9ce6-169">Para configurar un túnel VPN entre su suscripción a Azure y su red local, consulte [Conectar una red local a una red virtual de Microsoft Azure](https://go.microsoft.com/fwlink/p/?LinkId=613507).</span><span class="sxs-lookup"><span data-stu-id="f9ce6-169">To set up a VPN tunnel between your Azure subscription and your on-premises network, see [Connect an on-premises network to a Microsoft Azure virtual network](https://go.microsoft.com/fwlink/p/?LinkId=613507).</span></span>  <br/> |
|<span data-ttu-id="f9ce6-170">SharePoint 2013eDiscovery está configurado para buscar a través de SharePoint y Exchange Server 2013 y, opcionalmente, Lync Server 2013</span><span class="sxs-lookup"><span data-stu-id="f9ce6-170">SharePoint 2013 eDiscovery configured to search across SharePoint and Exchange Server 2013 and optionally Lync Server 2013</span></span>  <br/> |<span data-ttu-id="f9ce6-171">Para configurar eDiscovery de esta manera, consulte: [Configurar eDiscovery en SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=613508) y[Guía de entorno de pruebas: Configurar eDiscovery para Exchange, Lync, SharePoint y para el entorno de pruebas de recursos compartidos de archivos de Windows](https://go.microsoft.com/fwlink/p/?LinkId=393130).</span><span class="sxs-lookup"><span data-stu-id="f9ce6-171">To configure eDiscovery in this fashion, see [Configure eDiscovery in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=613508) and[Test Lab Guide: Configure eDiscovery for an Exchange, Lync, SharePoint and Windows File Shares Test Lab](https://go.microsoft.com/fwlink/p/?LinkId=393130).</span></span>  <br/> |
|<span data-ttu-id="f9ce6-172">eDiscovery en Microsoft 365 para SharePoint Online y Exchange Online</span><span class="sxs-lookup"><span data-stu-id="f9ce6-172">eDiscovery in Microsoft 365 for SharePoint Online and Exchange Online</span></span>  <br/> |<span data-ttu-id="f9ce6-173">Para configurar la exhibición de documentos electrónicos en Microsoft 365, consulte [configurar un centro de exhibición de documentos electrónicos en SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=613628).</span><span class="sxs-lookup"><span data-stu-id="f9ce6-173">To configure eDiscovery in Microsoft 365, see [Set up an eDiscovery Center in SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=613628).</span></span>  <br/> |
   
## <a name="configure-the-environment"></a><span data-ttu-id="f9ce6-174">Configurar el entorno</span><span class="sxs-lookup"><span data-stu-id="f9ce6-174">Configure the environment</span></span>

<span data-ttu-id="f9ce6-175">Ahora que tiene la configuración básica local, puede pasar a la configuración de la propia solución.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-175">Now that you have the base configuration in place, you can move ahead to configuring the solution itself.</span></span> 
  
### <a name="staging-file-share"></a><span data-ttu-id="f9ce6-176">Implementar el uso compartido de archivos</span><span class="sxs-lookup"><span data-stu-id="f9ce6-176">Staging file share</span></span>

1. <span data-ttu-id="f9ce6-177">En el dominio local, cree un grupo de seguridad global denominado Custodians.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-177">In the on-premises domain, create a global security group named Custodians.</span></span>
    
2. <span data-ttu-id="f9ce6-178">Create a hidden file share for the files that are collected from Custodians computers.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-178">Create a hidden file share for the files that are collected from Custodians computers.</span></span> <span data-ttu-id="f9ce6-179">This should be on an on-premises server.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-179">This should be on an on-premises server.</span></span> <span data-ttu-id="f9ce6-180">For example, on a server called Staging, create a file share called Cases$.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-180">For example, on a server called Staging, create a file share called Cases$.</span></span> <span data-ttu-id="f9ce6-181">The **$** is required to make this a hidden share.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-181">The **$** is required to make this a hidden share.</span></span>
    
3. <span data-ttu-id="f9ce6-182">Establezca los siguientes permisos de recurso compartido:</span><span class="sxs-lookup"><span data-stu-id="f9ce6-182">Set the following share permissions:</span></span>
    
  - <span data-ttu-id="f9ce6-183">Administradores: Modificar, leer</span><span class="sxs-lookup"><span data-stu-id="f9ce6-183">Custodians: Change, Read</span></span>
    
  - <span data-ttu-id="f9ce6-184">Administradores: Control total</span><span class="sxs-lookup"><span data-stu-id="f9ce6-184">Administrators: Full Control</span></span>
    
  - <span data-ttu-id="f9ce6-185">Subsistema de confianza de Exchange: Modificar, leer</span><span class="sxs-lookup"><span data-stu-id="f9ce6-185">Exchange Trusted Subsystem: Change, Read</span></span>
    
4. <span data-ttu-id="f9ce6-186">Open the **Security** tab, add the Custodians group, and click **Advanced**.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-186">Open the **Security** tab, add the Custodians group, and click **Advanced**.</span></span> <span data-ttu-id="f9ce6-187">Set the following permissions for the Custodians group:</span><span class="sxs-lookup"><span data-stu-id="f9ce6-187">Set the following permissions for the Custodians group:</span></span>
    
  - <span data-ttu-id="f9ce6-188">**Tipo: Denegar**</span><span class="sxs-lookup"><span data-stu-id="f9ce6-188">**Type: Deny**</span></span>
    
  - <span data-ttu-id="f9ce6-189">**Se aplica a: Esta carpeta, subcarpetas y archivos**</span><span class="sxs-lookup"><span data-stu-id="f9ce6-189">**Applies to: This folder, subfolders and files**</span></span>
    
5. <span data-ttu-id="f9ce6-190">Haga clic en **Permisos avanzados** y seleccione lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="f9ce6-190">Click **Advanced Permissions** and select the following:</span></span>
    
  - <span data-ttu-id="f9ce6-191">**Atributos de lectura**</span><span class="sxs-lookup"><span data-stu-id="f9ce6-191">**Read attributes**</span></span>
    
  - <span data-ttu-id="f9ce6-192">**Atributos extendidos de lectura**</span><span class="sxs-lookup"><span data-stu-id="f9ce6-192">**Read extended attributes**</span></span>
    
  - <span data-ttu-id="f9ce6-193">**Permisos de lectura**</span><span class="sxs-lookup"><span data-stu-id="f9ce6-193">**Read permissions**</span></span>
    
6. <span data-ttu-id="f9ce6-194">Pruebe el acceso al recurso compartido de archivos Casos$ haciendo lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="f9ce6-194">Test access to the Cases$ file share by doing the following:</span></span>
    
1. <span data-ttu-id="f9ce6-195">Agregar un usuario al grupo de administradores</span><span class="sxs-lookup"><span data-stu-id="f9ce6-195">Add a user to the Custodians group.</span></span>
    
2. <span data-ttu-id="f9ce6-196">Coloque un archivo en la carpeta Casos$.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-196">Place a file in the Cases$ folder.</span></span>
    
3. <span data-ttu-id="f9ce6-197">As the user, browse to the staging server, for example browse to the \\\\Staging share to see what shares are available.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-197">As the user, browse to the staging server, for example browse to the \\\\Staging share to see what shares are available.</span></span> <span data-ttu-id="f9ce6-198">You shouldn't see the **Cases$** share listed.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-198">You shouldn't see the **Cases$** share listed.</span></span>
    
4. <span data-ttu-id="f9ce6-199">Manually type the full path to the Cases$ share into Explorer.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-199">Manually type the full path to the Cases$ share into Explorer.</span></span> <span data-ttu-id="f9ce6-200">This should open the Cases$ share.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-200">This should open the Cases$ share.</span></span>
    
5. <span data-ttu-id="f9ce6-201">Try to open the file you previously placed in the share.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-201">Try to open the file you previously placed in the share.</span></span> <span data-ttu-id="f9ce6-202">This should fail.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-202">This should fail.</span></span>
    
### <a name="logon-script"></a><span data-ttu-id="f9ce6-203">Script de inicio de sesión</span><span class="sxs-lookup"><span data-stu-id="f9ce6-203">Logon script</span></span>

1. <span data-ttu-id="f9ce6-204">Copie y pegue este script Windows PowerShell en el Bloc de notas:</span><span class="sxs-lookup"><span data-stu-id="f9ce6-204">Copy and paste this Windows PowerShell script into Notepad:</span></span>
    
  ```
  # Automated file collection script
# Substantial error processing should be added for robust execution and troubleshooting opportunities
# All commented out write-hosts are for debugging only and are commented out for regular execution

# Functions 

Function CreateCaseFolder() {

#Check to see if case folder already exists
$CaseFolderCheck = Test-Path $CaseLocation

try {

    if (!$CaseFolderCheck) {
    # Case folder doesn't exist.  Create the case folder and the log file location
    # Write-Host -ForegroundColor Cyan "Creating Case Folder $CaseLocation"
    New-Item "$CaseLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
    # Write-Host -ForegroundColor Cyan "Creating Case Log Folder $CaseLogLocation"
    New-Item "$CaseLogLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
    # Write-Host -ForegroundColor Cyan "Creating Case PST folder $CasePSTLocation"
    New-Item "$CasePSTLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue

    }
    else {

    # do nothing since the target case folder already exists

    }
}
catch [System.Exception] {

    # To do..
    # to log to an exception or log file
    
    }
}

Function CopyFileToCaseFolder($SourcePath, $TargetPath, $FileName) {
    
    # Check to see if the file already exists
    $TargetFileCheck = Test-Path $TargetPath\$FileName

try {

    if (!$TargetFileCheck) {
    # Copy the file to the case folder
    Write-Host $SourcePath $TargetPath $FileName
    robocopy "$SourcePath" "$TargetPath" "$FileName" /COPY:DATSO /TEE /LOG+:$LoggingFile /R:10 /W:10 | Out-Null

    }
    else {

    # do nothing since file is already in the target case folder

    }
}
catch [System.Exception] {

    # To do..
    # to log to an exception or log file
    
    }
}

# Global variable initializations

# Error log
$Loggederrors=@()

# The array to contain the file types we collect
$FileTypes = @("*.doc","*.docx","*.pst","*.txt")

# We'll set the case number to be a combination of the date and user name
# For example, a case for John Doe on Dec 14, 2014 at 2:38pm would be:
# 201412141438_jdoe
$CaseNo = get-date -Format yyyyMMddHHmm
$CaseNo = $CaseNo + "_" + [Environment]::UserName

# Target location to copy case files
$CaseRootLocation = "\\staging\Cases$" 

# File copy location, log file location, PST file location and temporary log file location
$CaseLocation = $CaseRootLocation + "\" + $CaseNo
$CaseLogLocation = $CaseRootLocation + "\" + $CaseNo + "\_Log"
$CasePSTLocation = $CaseRootLocation + "\" + $CaseNo + "\_PSTs"
$TemporaryLogLocation = [Environment]::getfolderpath('ApplicationData') + "\" + $CaseNo

# Inventory of local drives
$LocalDrives = Get-PSDrive -PSProvider FileSystem -Scope Global

$LoggingFile = "$CaseLogLocation\FileCopyErrors.log"

# Main script

# Create the case folder if it doesn't already exist
CreateCaseFolder

# Create the list of files to be copied
# First create the temporary directory in the AppData\Roaming folder
New-Item "$TemporaryLogLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
$LocalDrives | foreach {

    # Write-Host -ForeGroundColor Cyan "Collecting Files for Drive: " $_
    Get-ChildItem -Path $_.Root -Recurse -Include $FileTypes -ErrorAction SilentlyContinue -ErrorVariable +Loggederrors | Export-Clixml $TemporaryLogLocation\$_.xml -Force
    # Needs try catch and logged collection error file
}

# Now let's read each file and copy any files we need to the case folder
# We will also copy these XMLs to the case log files folder as we go along
# We only want to process XML files, just in case something else got in there as the script ran
$CaseDriveFiles = Get-ChildItem $TemporaryLogLocation -Filter '*.xml'
$CaseDriveFiles | foreach {
    # Copy the XML file to the case log location
    CopyFileToCaseFolder $_.Directory.FullName $CaseLogLocation $_.Name
    $DriveFile = $_.FullName
    # Write-Host -ForegroundColor Cyan "Copying Files specified in the XML file: $DriveFile"
    $CurrentDriveFile = Import-Clixml $DriveFile
    $CurrentDriveFile | foreach {
        # write-host $_.FullName
        # if it's a PST, add to the PSTs folder. otherwise add it to case folder
        if ($_.Extension -match '.PST')
        {
            CopyFileToCaseFolder $_.Directory.FullName $CasePSTLocation $_.Name
            write-host "this is a PST"
        }
        else
        {
            CopyFileToCaseFolder $_.Directory.FullName $CaseLocation $_.Name
        }
    }
}

# Now delete the temporary log file
Remove-Item $TemporaryLogLocation -Recurse 

Write-Host -ForegroundColor Cyan "Finished."

  ```

2. <span data-ttu-id="f9ce6-205">Guarde el script como CollectionScript.ps1 en una ubicación fácil de encontrar, por ejemplo, C:\\AFCScripts.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-205">Save the above script as CollectionScript.ps1 in a location that's easy for you to find, for example, C:\\AFCScripts.</span></span>
    
3. <span data-ttu-id="f9ce6-206">Use the Go To feature in Notepad.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-206">Use the Go To feature in Notepad.</span></span> <span data-ttu-id="f9ce6-207">Make the following changes, as needed:</span><span class="sxs-lookup"><span data-stu-id="f9ce6-207">Make the following changes, as needed:</span></span>
    
|<span data-ttu-id="f9ce6-208">**Número de línea**</span><span class="sxs-lookup"><span data-stu-id="f9ce6-208">**Line #**</span></span>|<span data-ttu-id="f9ce6-209">**Lo que es necesario cambiar**</span><span class="sxs-lookup"><span data-stu-id="f9ce6-209">**What you need to change**</span></span>|<span data-ttu-id="f9ce6-210">**obligatorio/opcional**</span><span class="sxs-lookup"><span data-stu-id="f9ce6-210">**Required/optional**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="f9ce6-211">71</span><span class="sxs-lookup"><span data-stu-id="f9ce6-211">71</span></span>  <br/> |<span data-ttu-id="f9ce6-212">**$FileTypes** variable.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-212">**$FileTypes** variable.</span></span> <span data-ttu-id="f9ce6-213">Include all the file type extensions that you want the script to inventory and collect in the array variable.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-213">Include all the file type extensions that you want the script to inventory and collect in the array variable.</span></span> <br/> |<span data-ttu-id="f9ce6-214">Opcional</span><span class="sxs-lookup"><span data-stu-id="f9ce6-214">Optional</span></span>  <br/> |
|<span data-ttu-id="f9ce6-215">76 y 77</span><span class="sxs-lookup"><span data-stu-id="f9ce6-215">76 and 77</span></span>  <br/> |<span data-ttu-id="f9ce6-216">Change the way the **$CaseNo** variable is built to suit your needs.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-216">Change the way the **$CaseNo** variable is built to suit your needs.</span></span> <span data-ttu-id="f9ce6-217">The script captures the current date and time and appends the user name to it.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-217">The script captures the current date and time and appends the user name to it.</span></span> <br/> |<span data-ttu-id="f9ce6-218">Opcional</span><span class="sxs-lookup"><span data-stu-id="f9ce6-218">Optional</span></span>  <br/> |
|<span data-ttu-id="f9ce6-219">80</span><span class="sxs-lookup"><span data-stu-id="f9ce6-219">80</span></span>  <br/> |<span data-ttu-id="f9ce6-220">La variable **$CaseRootLocation** debe establecerse en el recurso compartido de archivos del archivo de colección de servidores de implementación. Por ejemplo, **\\\\Staging\\Cases$**</span><span class="sxs-lookup"><span data-stu-id="f9ce6-220">**$CaseRootLocation** variable needs to be set to your staging servers collection file share, for example **\\\\Staging\\Cases$**.</span></span> <br/> |<span data-ttu-id="f9ce6-221">Obligatorio</span><span class="sxs-lookup"><span data-stu-id="f9ce6-221">Required</span></span>  <br/> |
   
4. <span data-ttu-id="f9ce6-222">Coloque el archivo CollectionScript.ps1 en el recurso compartido de archivo Netlogon en un controlador de dominio. </span><span class="sxs-lookup"><span data-stu-id="f9ce6-222">Place the CollectionScript.ps1 file in the Netlogon file share on a domain controller.</span></span> 
    
### <a name="configure-gpo-for-the-logon-script-and-custodians-group"></a><span data-ttu-id="f9ce6-223">Configurar el GPO para el grupo Administradores y el script de inicio de sesión</span><span class="sxs-lookup"><span data-stu-id="f9ce6-223">Configure GPO for the logon script and Custodians Group</span></span>

1. <span data-ttu-id="f9ce6-224">Configure un script de inicio de sesión para el grupo Administradores siguiendo la sección "Cómo asignar los scripts de inicio de sesión del usuario" en el tema, [Usar scripts de inicio, apagado, inicio de sesión y cierre de sesión en la directiva de grupo](https://go.microsoft.com/fwlink/p/?LinkId=614844).</span><span class="sxs-lookup"><span data-stu-id="f9ce6-224">Configure a logon script for the Custodians group by following the "How to assign user logon scripts" section in the topic, [Using Startup, Shutdown, Logon, and Logoff Scripts in Group Policy](https://go.microsoft.com/fwlink/p/?LinkId=614844).</span></span>
    
2. <span data-ttu-id="f9ce6-225">Quite los usuarios autenticados de **Filtrado de seguridad** y agregue el grupo de administradores.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-225">Remove authenticated users from **Security Filtering**, and add the Custodians group.</span></span>
    
### <a name="pst-import-option-a-script-for-exchange-server-2013"></a><span data-ttu-id="f9ce6-226">Opción A de importación de PST, script para Exchange Server 2013</span><span class="sxs-lookup"><span data-stu-id="f9ce6-226">PST import Option A, script for Exchange Server 2013</span></span>

1.  <span data-ttu-id="f9ce6-227">Copie y pegue el siguiente script Windows PowerShell en el Bloc de notas:</span><span class="sxs-lookup"><span data-stu-id="f9ce6-227">Copy and paste the following Windows PowerShell script into Notepad:</span></span>
    
  ```
  # Script to import all PSTs in a given folder to a target mailbox
#
# This is for on-prem Exchange only
# Input parameters
# When you run the script, you call it with two parameters, PST source path and target mailbox alias
# For example:  .\PSTImport.ps1 \\FileShare\PSTFiles jdoe

param ([String]$SourcePath,[String]$MailboxAlias)

# Folder identifier is the string we want to show in the mailbox that we import the PSTs to

$FolderIdentifier = "zzImportedPSTs_"

# Connect to Exchange remote powershell using the connection Uri below
# This would be the format https://<exchange server FQDN>/Powershell

$ConnectionUri = 'https://h10-exch/PowerShell'
$RemoteEx2013Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri $ConnectionUri -Authentication Kerberos
Import-PSSession $RemoteEx2013Session

# Get all the files in the source path

$AllFiles = Get-ChildItem $SourcePath -Recurse

# Go through each file and if it's a PST launch a mailbox import request for it

$AllFiles | ForEach-Object {
    If ($_.Extension -eq ".pst") {
        $ImportName = $MailboxAlias + "_" + $_.Name
        $FolderName = $FolderIdentifier + $_.Name
        New-MailboxImportRequest -Name $ImportName -Mailbox $MailboxAlias -FilePath $_.FullName -TargetRootFolder $FolderName
    }
}
  ```

2. <span data-ttu-id="f9ce6-228">Save the script as PSTImportScript.ps1 in a location that's easy for you to find.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-228">Save the script as PSTImportScript.ps1 in a location that's easy for you to find.</span></span> <span data-ttu-id="f9ce6-229">For example and ease of use, create a folder on your staging server called \\\\Staging\\AFCScripts, and save it there.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-229">For example and ease of use, create a folder on your staging server called \\\\Staging\\AFCScripts, and save it there.</span></span>
    
3. <span data-ttu-id="f9ce6-230">Use la característica Ir a del Bloc de notas y realice los siguientes cambios según sea necesario:</span><span class="sxs-lookup"><span data-stu-id="f9ce6-230">Use the Go To feature in Notepad, and make the following changes, as needed:</span></span>
    
|<span data-ttu-id="f9ce6-231">**Número de línea**</span><span class="sxs-lookup"><span data-stu-id="f9ce6-231">**Line #**</span></span>|<span data-ttu-id="f9ce6-232">**Lo que es necesario cambiar**</span><span class="sxs-lookup"><span data-stu-id="f9ce6-232">**What you need to change**</span></span>|<span data-ttu-id="f9ce6-233">**obligatorio/opcional**</span><span class="sxs-lookup"><span data-stu-id="f9ce6-233">**Required/optional**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="f9ce6-234">12 </span><span class="sxs-lookup"><span data-stu-id="f9ce6-234">12</span></span>  <br/> |<span data-ttu-id="f9ce6-235">**$FolderIdentifier** tags the mailbox folders that PSTs are imported into.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-235">**$FolderIdentifier** tags the mailbox folders that PSTs are imported into.</span></span> <span data-ttu-id="f9ce6-236">Change this if necessary.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-236">Change this if necessary.</span></span> <br/> |<span data-ttu-id="f9ce6-237">Opcional</span><span class="sxs-lookup"><span data-stu-id="f9ce6-237">Optional</span></span>  <br/> |
|<span data-ttu-id="f9ce6-238">17 </span><span class="sxs-lookup"><span data-stu-id="f9ce6-238">17</span></span>  <br/> |<span data-ttu-id="f9ce6-239">**$ConnectionUri** tiene que estar establecido como su propio servidor.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-239">**$ConnectionUri** needs to be set to your own server.</span></span> <br/> <span data-ttu-id="f9ce6-240">> [!IMPORTANT]> Make sure your **$ConnectionUri** points to a http location, not https.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-240">> [!IMPORTANT]> Make sure your **$ConnectionUri** points to a http location, not https.</span></span> <span data-ttu-id="f9ce6-241">It won't work with https:.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-241">It won't work with https:.</span></span>          |<span data-ttu-id="f9ce6-242">Obligatorio</span><span class="sxs-lookup"><span data-stu-id="f9ce6-242">Required</span></span>  <br/> |
   
4. <span data-ttu-id="f9ce6-243">Compruebe que la cuenta del subsistema de confianza de Exchange tiene permisos de lectura, escritura y ejecución en el recurso compartido \\\\Staging\\Cases$.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-243">Verify that the Exchange Trusted Subsystem account has Read, Write, and Execute permissions to the \\\\Staging\\Cases$ share.</span></span>
    
5. <span data-ttu-id="f9ce6-244">El script de importación de PST requiere los dos parámetros de entrada siguientes:</span><span class="sxs-lookup"><span data-stu-id="f9ce6-244">The PST import script requires the following two input parameters:</span></span>
    
  - <span data-ttu-id="f9ce6-245">**$SourcePath** La ubicación en la que se van a importar los archivos PST, por ejemplo \\\\Staging\\Cases$</span><span class="sxs-lookup"><span data-stu-id="f9ce6-245">**$SourcePath** The location of the PST files to be imported, for example \\\\Staging\\Cases$.</span></span>
    
  - <span data-ttu-id="f9ce6-246">**$MailboxAlias** el alias del buzón de destino que va a recibir los elementos de correo electrónico importados</span><span class="sxs-lookup"><span data-stu-id="f9ce6-246">**$MailboxAlias** The alias of the target mailbox that will receive the imported email items.</span></span>
    
6. <span data-ttu-id="f9ce6-247">Por ejemplo, si desea importar todos los archivos PST de la ruta de acceso \\Staging\Cases$ en un buzón con el alias eDiscoveryMailbox, ha de ejecutar el script de la siguiente manera `\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox`.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-247">For example, if you want to import all the PST files from the path \\Staging\Cases$ into a mailbox with the alias eDiscoveryMailbox, you would run the script like this `\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox`.</span></span>
    
### <a name="pst-import-option-b-for-exchange-online"></a><span data-ttu-id="f9ce6-248">Opción B de importación de PST, para Exchange Online</span><span class="sxs-lookup"><span data-stu-id="f9ce6-248">PST Import Option B, for Exchange Online</span></span>

-  <span data-ttu-id="f9ce6-249">Create the mailbox structure to place the imported PST files into.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-249">Create the mailbox structure to place the imported PST files into.</span></span> <span data-ttu-id="f9ce6-250">For more information on how to create a user mailbox in Exchange Online, see[Create User Mailboxes in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=615118).</span><span class="sxs-lookup"><span data-stu-id="f9ce6-250">For more information on how to create a user mailbox in Exchange Online, see[Create User Mailboxes in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=615118).</span></span>
    
### <a name="cold-storage"></a><span data-ttu-id="f9ce6-251">Almacenamiento en frío</span><span class="sxs-lookup"><span data-stu-id="f9ce6-251">Cold storage</span></span>

1. <span data-ttu-id="f9ce6-252">Cree un recurso compartido de archivos en el Máquina virtual de Azure, donde se colocarán todos los archivos recopilados, por ejemplo, \\\\AZFile1\\ContentColdStorage.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-252">Create a file share on the Azure Virtual Machine, where all the collected files will be placed, for example, \\\\AZFile1\\ContentColdStorage.</span></span>
    
2. <span data-ttu-id="f9ce6-253">Grant the default content access account at least Read permissions to the share and all subfolders and files.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-253">Grant the default content access account at least Read permissions to the share and all subfolders and files.</span></span> <span data-ttu-id="f9ce6-254">For more information about configuring SharePoint 2013 Search, see [Create and configure a Search service application in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=614940).</span><span class="sxs-lookup"><span data-stu-id="f9ce6-254">For more information about configuring SharePoint 2013 Search, see [Create and configure a Search service application in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=614940).</span></span>
    
3. <span data-ttu-id="f9ce6-255">Si prevé que se van a importar archivos PST desde \\\\AZFile1\\ContentColdStorage, conceda al subsistema de confianza de Exchange permisos de lectura, escritura y ejecución para el recurso compartido.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-255">If you anticipate importing PST files from \\\\AZFile1\\ContentColdStorage, grant the Exchange Trusted Subsystem Read, Write, and Execute permissions to the share.</span></span>
    
### <a name="orchestrator"></a><span data-ttu-id="f9ce6-256">Orchestrator</span><span class="sxs-lookup"><span data-stu-id="f9ce6-256">Orchestrator</span></span>

1. <span data-ttu-id="f9ce6-257">Descargue el [runbook MoveToColdStorage](https://go.microsoft.com/fwlink/?LinkId=616095) desde el Centro de descarga de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-257">Download the[ MoveToColdStorage runbook](https://go.microsoft.com/fwlink/?LinkId=616095) from the Microsoft Download Center.</span></span>
    
2. <span data-ttu-id="f9ce6-258">Open the **Runbook Designer**, in the **Connections** pane, click the folder that you want to import the runbook into.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-258">Open the **Runbook Designer**, in the **Connections** pane, click the folder that you want to import the runbook into.</span></span> <span data-ttu-id="f9ce6-259">Click the **Actions** menu, and the click **Import**.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-259">Click the **Actions** menu, and the click **Import**.</span></span> <span data-ttu-id="f9ce6-260">The **Import** dialog box appears.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-260">The **Import** dialog box appears.</span></span>
    
3. <span data-ttu-id="f9ce6-261">En el cuadro **Ubicación del archivo**, escriba la ruta de acceso y el nombre del Runbook que desea importar o haga clic en el botón de los puntos suspensivos ( **...**) para buscar el archivo que desea importar.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-261">In the **File Location** box, type the path and file name of the runbook you want to import, or click the ellipsis ( **...**) to browse to the file you want to import.</span></span> 
    
4. <span data-ttu-id="f9ce6-262">Select **Import runbooks** and **Import Orchestrator encrypted data**.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-262">Select **Import runbooks** and **Import Orchestrator encrypted data**.</span></span> <span data-ttu-id="f9ce6-263">Clear **Counters**, **Schedules**, **Variables**, **Computer Groups**, **Import global configurations**, and **Overwrite existing global configurations**.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-263">Clear **Counters**, **Schedules**, **Variables**, **Computer Groups**, **Import global configurations**, and **Overwrite existing global configurations**.</span></span>
    
5. <span data-ttu-id="f9ce6-264">Haga clic en **Finalizar**.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-264">Click **Finish**.</span></span>
    
6. <span data-ttu-id="f9ce6-265">Edite el runbook **MoveFilesToColdStorage** de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="f9ce6-265">Edit the **MoveFilesToColdStorage** runbook as follows:</span></span>
    
1. <span data-ttu-id="f9ce6-266">**Move File** activity - set the **Source File** path to the collection file share, for example \\\\Staging\\cases$.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-266">**Move File** activity - set the **Source File** path to the collection file share, for example \\\\Staging\\cases$.</span></span> <span data-ttu-id="f9ce6-267">Set the **Destination Folder** to the cold storage file share in Azure, for example \\\\AZFile1\\ContentColdStorage.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-267">Set the **Destination Folder** to the cold storage file share in Azure, for example \\\\AZFile1\\ContentColdStorage.</span></span> <span data-ttu-id="f9ce6-268">Select **Create a file with a unique name**.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-268">Select **Create a file with a unique name**.</span></span>
    
2. <span data-ttu-id="f9ce6-269">Actividad **Eliminar carpeta**: establezca la **ruta de acceso:** en el recurso compartido de archivos de la colección, por ejemplo \\\\Staging\\cases$\\*, y seleccione **Eliminar todos los archivos y las subcarpetas**.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-269">**Delete Folder** activity - Set the **Path:** to the collection file share, for example \\\\Staging\\cases$\\*, and select **Delete all files and sub-folders**.</span></span> 
    
7. <span data-ttu-id="f9ce6-270">Implemente el runbook **MoveToColdStorage** usando los procedimientos descritos en[Implementar runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615120).</span><span class="sxs-lookup"><span data-stu-id="f9ce6-270">Deploy the **MoveToColdStorage** runbook using the procedures in[Deploying Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615120).</span></span>
    
### <a name="sharepoint-on-premises-search-for-cold-storage"></a><span data-ttu-id="f9ce6-271">Búsqueda local de SharePoint para el almacenamiento en frío</span><span class="sxs-lookup"><span data-stu-id="f9ce6-271">SharePoint on-premises search for cold storage</span></span>

1. <span data-ttu-id="f9ce6-272">Create an new content source in your SharePoint 2013 farm for the cold storage share in Azure, for example \\\\AZFile1\\ContentColdStorage.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-272">Create an new content source in your SharePoint 2013 farm for the cold storage share in Azure, for example \\\\AZFile1\\ContentColdStorage.</span></span> <span data-ttu-id="f9ce6-273">For more information about managing content sources, see [Add, edit, or delete a content source in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615004)</span><span class="sxs-lookup"><span data-stu-id="f9ce6-273">For more information about managing content sources, see [Add, edit, or delete a content source in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615004)</span></span>
    
2. <span data-ttu-id="f9ce6-274">Start a full crawl.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-274">Start a full crawl.</span></span> <span data-ttu-id="f9ce6-275">For more information see, [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span><span class="sxs-lookup"><span data-stu-id="f9ce6-275">For more information see, [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span></span>
    
## <a name="using-the-solution"></a><span data-ttu-id="f9ce6-276">Uso de la solución</span><span class="sxs-lookup"><span data-stu-id="f9ce6-276">Using the solution</span></span>

<span data-ttu-id="f9ce6-277">There are five major steps in using this solution, assuming you don't want to import the PST files into both Exchange Server 2013 and Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-277">There are five major steps in using this solution, assuming you don't want to import the PST files into both Exchange Server 2013 and Exchange Online.</span></span> <span data-ttu-id="f9ce6-278">This section provides you with the procedures for all of them.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-278">This section provides you with the procedures for all of them.</span></span> <span data-ttu-id="f9ce6-279">Your primary interaction with the solution will be in doing the following:</span><span class="sxs-lookup"><span data-stu-id="f9ce6-279">Your primary interaction with the solution will be in doing the following:</span></span>
  
1. <span data-ttu-id="f9ce6-280">Administre la pertenencia de un usuario en el grupo Administradores.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-280">Manage user membership in the Custodians group.</span></span>
    
2. <span data-ttu-id="f9ce6-281">Review the log files generated by the logon script.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-281">Review the log files generated by the logon script.</span></span> <span data-ttu-id="f9ce6-282">The FileCopyErrors.log lists all the files that were not successfully copied.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-282">The FileCopyErrors.log lists all the files that were not successfully copied.</span></span> <span data-ttu-id="f9ce6-283">You need to decide what you want to do with them</span><span class="sxs-lookup"><span data-stu-id="f9ce6-283">You need to decide what you want to do with them</span></span>
    
3. <span data-ttu-id="f9ce6-284">Administre el proceso de importación de PST.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-284">Managing the PST import process.</span></span>
    
4. <span data-ttu-id="f9ce6-285">Mover los archivos de la colección a un almacenamiento en frío</span><span class="sxs-lookup"><span data-stu-id="f9ce6-285">Moving the collection files to cold storage.</span></span>
    
<span data-ttu-id="f9ce6-286">El resto de los pasos no son específicos para esta solución.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-286">All the other steps are not specific to this solution.</span></span> <span data-ttu-id="f9ce6-287">Son tareas administrativas estándar que realiza en SharePoint 2013, Microsoft 365 y Azure.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-287">They are standard administrative tasks that you perform in SharePoint 2013, Microsoft 365, and Azure.</span></span> <span data-ttu-id="f9ce6-288">Hay elementos para los que esta solución no proporciona ninguna orientación y que tendrá que solucionar en función de las necesidades de su empresa, como:</span><span class="sxs-lookup"><span data-stu-id="f9ce6-288">There are items that this solution does not provide any guidance that you will need to work out based on your company's needs, such as:</span></span>
  
1. <span data-ttu-id="f9ce6-289">El seguimiento de sus casos de eDiscovery y los administradores que están asociados con cada uno</span><span class="sxs-lookup"><span data-stu-id="f9ce6-289">Tracking your eDiscovery cases, and which Custodians are associated with which case.</span></span>
    
2. <span data-ttu-id="f9ce6-290">El seguimiento los conjuntos de colecciones de archivos que están asociados con cada caso de eDiscovery</span><span class="sxs-lookup"><span data-stu-id="f9ce6-290">Tracking which sets of file collections are associate with which eDiscovery case.</span></span>
    
3. <span data-ttu-id="f9ce6-291">La coordinación de la sincronización de los pasos de importación y desplazamiento a un almacenamiento en frío.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-291">Coordinating the timing of the Import and move to cold storage steps.</span></span>
    
4. <span data-ttu-id="f9ce6-292">Administrar el espacio de archivo usado en Azure.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-292">Managing the file space used in Azure.</span></span>
    
5. <span data-ttu-id="f9ce6-293">Administrar los buzones en los que se importan los archivos PST.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-293">Managing the mailboxes that PSTs are imported into.</span></span>
    
6. <span data-ttu-id="f9ce6-294">La copia de seguridad y restauración de todos los datos locales</span><span class="sxs-lookup"><span data-stu-id="f9ce6-294">Backup and restoration of all on-premises data.</span></span>
    
### <a name="custodian-management"></a><span data-ttu-id="f9ce6-295">La administración de los administradores</span><span class="sxs-lookup"><span data-stu-id="f9ce6-295">Custodian management</span></span>

- <span data-ttu-id="f9ce6-296">To start the automated file collection process for an individual user, add them to the Custodians group.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-296">To start the automated file collection process for an individual user, add them to the Custodians group.</span></span> <span data-ttu-id="f9ce6-297">The next time that the user logs on, the logon script assigned to the Custodians group through Group Policy will run.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-297">The next time that the user logs on, the logon script assigned to the Custodians group through Group Policy will run.</span></span> 
    
### <a name="monitor-collected-files-and-review-log-files"></a><span data-ttu-id="f9ce6-298">Supervisar los archivos recopilados y revisar los archivos de registro.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-298">Monitor collected files and review log files</span></span>

1. <span data-ttu-id="f9ce6-299">Watch the collection file share, for example \\\\Staging\\cases$\\*, for the collection folder from the user.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-299">Watch the collection file share, for example \\\\Staging\\cases$\\*, for the collection folder from the user.</span></span> <span data-ttu-id="f9ce6-300">The name of the folder will be formatted like this:  *yyyyMMddHHmm_UserName*  .</span><span class="sxs-lookup"><span data-stu-id="f9ce6-300">The name of the folder will be formatted like this:  *yyyyMMddHHmm_UserName*  .</span></span>
    
2. <span data-ttu-id="f9ce6-301">When the collection is completed, open the collection folder, and browse to the _Log folder.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-301">When the collection is completed, open the collection folder, and browse to the _Log folder.</span></span> <span data-ttu-id="f9ce6-302">In the _Log folder, you will see the following:</span><span class="sxs-lookup"><span data-stu-id="f9ce6-302">In the _Log folder, you will see the following:</span></span>
    
  - <span data-ttu-id="f9ce6-303">One XML file for every local drive on the user's computer, for example **A.xml**, **C.xml**.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-303">One XML file for every local drive on the user's computer, for example **A.xml**, **C.xml**.</span></span> <span data-ttu-id="f9ce6-304">These files contain the inventory drives that they are named after, and they are used for the robocopy operation.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-304">These files contain the inventory drives that they are named after, and they are used for the robocopy operation.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="f9ce6-305">The collection script will only create an entry in the inventory file for the file types that you defined in the script itself.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-305">The collection script will only create an entry in the inventory file for the file types that you defined in the script itself.</span></span> <span data-ttu-id="f9ce6-306">It will not create an inventory entry for every file on the user's computer.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-306">It will not create an inventory entry for every file on the user's computer.</span></span> 
  
  - <span data-ttu-id="f9ce6-307">One log file named FileCopyErrors.log for each collection run.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-307">One log file named FileCopyErrors.log for each collection run.</span></span> <span data-ttu-id="f9ce6-308">This file contains a listing of the files that robocopy could not copy to the file collection share, for example, \\\\Staging\\cases$\\*.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-308">This file contains a listing of the files that robocopy could not copy to the file collection share, for example, \\\\Staging\\cases$\\*.</span></span> <span data-ttu-id="f9ce6-309">You will need to review this and decide what actions to take for these missed files.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-309">You will need to review this and decide what actions to take for these missed files.</span></span> <span data-ttu-id="f9ce6-310">Usually, you either need to collect them manually if you want them, or you may decide that they are not required and can therefore be omitted from the collection.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-310">Usually, you either need to collect them manually if you want them, or you may decide that they are not required and can therefore be omitted from the collection.</span></span>
    
### <a name="pst-import-option-a-for-exchange-server-2013"></a><span data-ttu-id="f9ce6-311">Opción A de importación de PST para Exchange Server 2013</span><span class="sxs-lookup"><span data-stu-id="f9ce6-311">PST import option A for Exchange Server 2013</span></span>

1. <span data-ttu-id="f9ce6-312">Log on to the server that hosts the collection file share, for example **Staging**, and open Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-312">Log on to the server that hosts the collection file share, for example **Staging**, and open Windows PowerShell.</span></span> <span data-ttu-id="f9ce6-313">For more information about starting Windows PowerShell, see[Starting Windows PowerShell on Windows Server](https://go.microsoft.com/fwlink/p/?LinkId=615115).</span><span class="sxs-lookup"><span data-stu-id="f9ce6-313">For more information about starting Windows PowerShell, see[Starting Windows PowerShell on Windows Server](https://go.microsoft.com/fwlink/p/?LinkId=615115).</span></span>
    
2. <span data-ttu-id="f9ce6-314">Set the Execution policy to Unrestricted .</span><span class="sxs-lookup"><span data-stu-id="f9ce6-314">Set the Execution policy to Unrestricted .</span></span> <span data-ttu-id="f9ce6-315">Type  `Set-ExecutionPolicy Unrestricted -Scope Process` into Windows PowerShell, and press Enter.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-315">Type  `Set-ExecutionPolicy Unrestricted -Scope Process` into Windows PowerShell, and press Enter.</span></span>
    
3. <span data-ttu-id="f9ce6-316">Run the PSTImportScript.ps1 file, and provide the **$SourcePath** and **$MailboxAlias** parameters.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-316">Run the PSTImportScript.ps1 file, and provide the **$SourcePath** and **$MailboxAlias** parameters.</span></span> <span data-ttu-id="f9ce6-317">For more information about running Windows PowerShell scripts, see[Running Scripts](https://go.microsoft.com/fwlink/p/?LinkID=615117).</span><span class="sxs-lookup"><span data-stu-id="f9ce6-317">For more information about running Windows PowerShell scripts, see[Running Scripts](https://go.microsoft.com/fwlink/p/?LinkID=615117).</span></span>
    
4. <span data-ttu-id="f9ce6-318">Revise la salida de errores.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-318">Review the output for errors.</span></span>
    
5. <span data-ttu-id="f9ce6-319">Before you attempt to import an identically named PST file into the same mailbox, you have to remove the mailbox import request.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-319">Before you attempt to import an identically named PST file into the same mailbox, you have to remove the mailbox import request.</span></span> <span data-ttu-id="f9ce6-320">Run the following command to do that:  `Get-MailboxImportRequest | Remove-MailboxImportRequest`.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-320">Run the following command to do that:  `Get-MailboxImportRequest | Remove-MailboxImportRequest`.</span></span> <span data-ttu-id="f9ce6-321">You will be prompted to remove each individual request from the queue.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-321">You will be prompted to remove each individual request from the queue.</span></span> <span data-ttu-id="f9ce6-322">Respond as needed.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-322">Respond as needed.</span></span>
    
### <a name="pst-import-option-b-for-exchange-online"></a><span data-ttu-id="f9ce6-323">Opción B de importación de PST, para Exchange Online</span><span class="sxs-lookup"><span data-stu-id="f9ce6-323">PST import option B, for Exchange Online</span></span>

- <span data-ttu-id="f9ce6-324">Para ubicar los archivos PST recopilados en Exchange Online, siga los procedimientos que se describen en los archivos de importación en Microsoft 365 a través de [carga de red](https://docs.microsoft.com/microsoft-365/compliance/use-network-upload-to-import-pst-files).</span><span class="sxs-lookup"><span data-stu-id="f9ce6-324">To place the collected PST files into Exchange Online, follow the procedures in the Import files into Microsoft 365 through [network upload](https://docs.microsoft.com/microsoft-365/compliance/use-network-upload-to-import-pst-files).</span></span>
    
### <a name="move-to-cold-storage"></a><span data-ttu-id="f9ce6-325">Mover a un almacenamiento en frío</span><span class="sxs-lookup"><span data-stu-id="f9ce6-325">Move to cold storage</span></span>

1. <span data-ttu-id="f9ce6-326">Ejecute el runbook **MoveToColdStorage** usando los procedimientos descritos en [Ejecutar Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615123).</span><span class="sxs-lookup"><span data-stu-id="f9ce6-326">Run the **MoveToColdStorage** runbook using the procedures in [Running Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615123).</span></span>
    
2. <span data-ttu-id="f9ce6-327">Watch the Azure file share you are using for long term storage, for example \\\\AZFile1\\ContentColdStorage and the on-premises collection file share, for example \\\\Staging\\cases$.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-327">Watch the Azure file share you are using for long term storage, for example \\\\AZFile1\\ContentColdStorage and the on-premises collection file share, for example \\\\Staging\\cases$.</span></span> <span data-ttu-id="f9ce6-328">You should see the files and folders appear in the cold storage file share and disappear from the collection file share.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-328">You should see the files and folders appear in the cold storage file share and disappear from the collection file share.</span></span>
    
### <a name="ediscovery"></a><span data-ttu-id="f9ce6-329">eDiscovery</span><span class="sxs-lookup"><span data-stu-id="f9ce6-329">eDiscovery</span></span>

1. <span data-ttu-id="f9ce6-330">Either allow the full crawl of the cold storage file share to run as schedules, or initiate a crawl.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-330">Either allow the full crawl of the cold storage file share to run as schedules, or initiate a crawl.</span></span> <span data-ttu-id="f9ce6-331">For more information on starting full or incremental crawls, see [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span><span class="sxs-lookup"><span data-stu-id="f9ce6-331">For more information on starting full or incremental crawls, see [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span></span>
    
2. <span data-ttu-id="f9ce6-332">Cree un caso de eDiscovery en SharePoint 2013 si usó la opción A para la importación de un archivo PST o cree un caso de eDiscovery en SharePoint Online si usó la opción B.</span><span class="sxs-lookup"><span data-stu-id="f9ce6-332">Create an eDiscovery case in SharePoint 2013 if you used option A for a PST file import or create an eDiscovery case in SharePoint Online if you used option B.</span></span>
    

