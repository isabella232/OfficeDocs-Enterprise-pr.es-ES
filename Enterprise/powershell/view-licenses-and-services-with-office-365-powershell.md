---
title: Ver licencias y servicios de Microsoft 365 con PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- O365ITProTrain
- LIL_Placement
- PowerShell
ms.assetid: bb5260a9-a6a3-4f34-b19a-06c6699f6723
description: Explica cómo usar PowerShell para ver información sobre los planes de licencias, los servicios y las licencias disponibles en su organización de Microsoft 365.
ms.openlocfilehash: f0b7d6cd5981bec09e7773d10d82ff81c0f34d4e
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230216"
---
# <a name="view-microsoft-365-licenses-and-services-with-powershell"></a><span data-ttu-id="c9af9-103">Ver licencias y servicios de Microsoft 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="c9af9-103">View Microsoft 365 licenses and services with PowerShell</span></span>

<span data-ttu-id="c9af9-104">*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="c9af9-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="c9af9-105">Todas las suscripciones de Microsoft 365 constan de los siguientes elementos:</span><span class="sxs-lookup"><span data-stu-id="c9af9-105">Every Microsoft 365 subscription consists of the following elements:</span></span>

- <span data-ttu-id="c9af9-106">**Planes de licencias** También se conocen como planes de licencia o planes de 365 de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c9af9-106">**Licensing plans** These are also known as license plans or Microsoft 365 plans.</span></span> <span data-ttu-id="c9af9-107">Los planes de licencias definen los servicios de Microsoft 365 que están disponibles para los usuarios.</span><span class="sxs-lookup"><span data-stu-id="c9af9-107">Licensing plans define the Microsoft 365 services that are available to users.</span></span> <span data-ttu-id="c9af9-108">Su suscripción a Microsoft 365 puede contener varios planes de licencias.</span><span class="sxs-lookup"><span data-stu-id="c9af9-108">Your Microsoft 365 subscription may contain multiple licensing plans.</span></span> <span data-ttu-id="c9af9-109">Un plan de licencias de ejemplo sería Microsoft 365 E3.</span><span class="sxs-lookup"><span data-stu-id="c9af9-109">An example licensing plan would be Microsoft 365 E3.</span></span>
    
- <span data-ttu-id="c9af9-110">**Servicios** de También se conocen como planes de servicio.</span><span class="sxs-lookup"><span data-stu-id="c9af9-110">**Services** These are also known as service plans.</span></span> <span data-ttu-id="c9af9-111">Los servicios son los productos, las características y las capacidades de Microsoft 365 que están disponibles en cada plan de licencias, por ejemplo, Exchange Online y Microsoft 365 apps for Enterprise (anteriormente denominado Office 365 ProPlus).</span><span class="sxs-lookup"><span data-stu-id="c9af9-111">Services are the Microsoft 365 products, features, and capabilities that are available in each licensing plan, for example, Exchange Online and Microsoft 365 Apps for enterprise (previously named Office 365 ProPlus).</span></span> <span data-ttu-id="c9af9-112">Los usuarios pueden tener varias licencias asignadas que provengan de diferentes planes de licencias, y les permitan obtener acceso a diferentes servicios.</span><span class="sxs-lookup"><span data-stu-id="c9af9-112">Users can have multiple licenses assigned to them from different licensing plans that grant access to different services.</span></span>
    
- <span data-ttu-id="c9af9-113">**Licencias** Los planes de licencias contienen el número de licencias que haya adquirido.</span><span class="sxs-lookup"><span data-stu-id="c9af9-113">**Licenses** Each licensing plan contains the number of licenses that you purchased.</span></span> <span data-ttu-id="c9af9-114">Las licencias se asignan a los usuarios para que puedan usar los servicios de Microsoft 365 definidos por el plan de licencias.</span><span class="sxs-lookup"><span data-stu-id="c9af9-114">You assign licenses to users so they can use the Microsoft 365 services that are defined by the licensing plan.</span></span> <span data-ttu-id="c9af9-115">Todas las cuentas de usuario requieren al menos una licencia de un plan de licencias para que puedan iniciar sesión en Microsoft 365 y usar los servicios.</span><span class="sxs-lookup"><span data-stu-id="c9af9-115">Every user account requires at least one license from one licensing plan so they can log on to Microsoft 365 and use the services.</span></span>
    
<span data-ttu-id="c9af9-116">Puede usar PowerShell para Microsoft 365 para ver detalles sobre los planes de licencias, las licencias y los servicios disponibles en su organización de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="c9af9-116">You can use PowerShell for Microsoft 365 to view details about the available licensing plans, licenses, and services in your Microsoft 365 organization.</span></span> <span data-ttu-id="c9af9-117">Para obtener más información sobre los productos, las características y los servicios disponibles en las diferentes suscripciones de Office 365, consulte [Opciones de planes de Office 365](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span><span class="sxs-lookup"><span data-stu-id="c9af9-117">For more information about the products, features, and services that are available in different Office 365 subscriptions, see [Office 365 Plan Options](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span></span>


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="c9af9-118">Use el módulo de PowerShell Azure Active Directory para Graph</span><span class="sxs-lookup"><span data-stu-id="c9af9-118">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="c9af9-119">En primer lugar, [Conéctese a su inquilino de Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="c9af9-119">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="c9af9-120">Para ver información resumida sobre los planes de licencias actuales y las licencias disponibles para cada plan, ejecute este comando:</span><span class="sxs-lookup"><span data-stu-id="c9af9-120">To view summary information about your current licensing plans and the available licenses for each plan, run this command:</span></span>
  
```powershell
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

<span data-ttu-id="c9af9-121">Los resultados contienen:</span><span class="sxs-lookup"><span data-stu-id="c9af9-121">The results contain:</span></span>
  
- <span data-ttu-id="c9af9-122">**SkuPartNumber:** Muestra los planes de licencias disponibles para su organización.</span><span class="sxs-lookup"><span data-stu-id="c9af9-122">**SkuPartNumber:** Shows the available licensing plans for your organization.</span></span> <span data-ttu-id="c9af9-123">Por ejemplo, `ENTERPRISEPACK` es el nombre del plan de licencias de Office 365 Enterprise E3.</span><span class="sxs-lookup"><span data-stu-id="c9af9-123">For example, `ENTERPRISEPACK` is the license plan name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="c9af9-124">**Habilitado:** Número de licencias que ha comprado para un plan de licencias específico.</span><span class="sxs-lookup"><span data-stu-id="c9af9-124">**Enabled:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="c9af9-125">**ConsumedUnits**: es el número de licencias asignadas a los usuarios de un plan de licencias específico.</span><span class="sxs-lookup"><span data-stu-id="c9af9-125">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="c9af9-126">Para ver información detallada sobre los servicios de Microsoft 365 que están disponibles en todos los planes de licencias, primero muestre una lista de los planes de licencia.</span><span class="sxs-lookup"><span data-stu-id="c9af9-126">To view details about the Microsoft 365 services that are available in all of your license plans, first display a list of your license plans.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="c9af9-127">A continuación, almacene la información de los planes de licencia en una variable.</span><span class="sxs-lookup"><span data-stu-id="c9af9-127">Next, store the license plans information in a variable.</span></span>

```powershell
$licenses = Get-AzureADSubscribedSku
```

<span data-ttu-id="c9af9-128">A continuación, muestre los servicios en un plan de licencias específico.</span><span class="sxs-lookup"><span data-stu-id="c9af9-128">Next, display the services in a specific license plan.</span></span>

```powershell
$licenses[<index>].ServicePlans
```

<span data-ttu-id="c9af9-129">\<index>es un entero que especifica el número de fila del plan de licencia desde la presentación del `Get-AzureADSubscribedSku | Select SkuPartNumber` comando, menos 1.</span><span class="sxs-lookup"><span data-stu-id="c9af9-129">\<index> is an integer that specifies the row number of the license plan from the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command, minus 1.</span></span>

<span data-ttu-id="c9af9-130">Por ejemplo, si la presentación del `Get-AzureADSubscribedSku | Select SkuPartNumber` comando es la siguiente:</span><span class="sxs-lookup"><span data-stu-id="c9af9-130">For example, if the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command is this:</span></span>

```powershell
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
```

<span data-ttu-id="c9af9-131">A continuación, el comando para mostrar los servicios del plan de licencias ENTERPRISEPREMIUM es el siguiente:</span><span class="sxs-lookup"><span data-stu-id="c9af9-131">Then the command to display the services for the ENTERPRISEPREMIUM license plan is this:</span></span>

```powershell
$licenses[2].ServicePlans
```

<span data-ttu-id="c9af9-132">ENTERPRISEPREMIUM es la tercera fila.</span><span class="sxs-lookup"><span data-stu-id="c9af9-132">ENTERPRISEPREMIUM is the third row.</span></span> <span data-ttu-id="c9af9-133">Por lo tanto, el valor de índice es (3-1) o 2.</span><span class="sxs-lookup"><span data-stu-id="c9af9-133">Therefore, the index value is (3 - 1), or 2.</span></span>

<span data-ttu-id="c9af9-134">Para obtener una lista completa de los planes de licencia (también conocidos como nombres de producto), sus planes de servicio incluidos y los nombres descriptivos correspondientes, consulte [Product Names and Service Plan Identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span><span class="sxs-lookup"><span data-stu-id="c9af9-134">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="c9af9-135">Use el Módulo Microsoft Azure Active Directory para Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c9af9-135">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="c9af9-136">En primer lugar, [Conéctese a su inquilino de Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="c9af9-136">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

>[!Note]
><span data-ttu-id="c9af9-137">Hay un script de PowerShell que automatiza los procedimientos descritos en este tema.</span><span class="sxs-lookup"><span data-stu-id="c9af9-137">A PowerShell script is available that automates the procedures described in this topic.</span></span> <span data-ttu-id="c9af9-138">En concreto, el script permite ver y deshabilitar servicios en la organización de Microsoft 365, incluido Sway.</span><span class="sxs-lookup"><span data-stu-id="c9af9-138">Specifically, the script lets you view and disable services in your Microsoft 365 organization, including Sway.</span></span> <span data-ttu-id="c9af9-139">Para obtener más información, vea [deshabilitar el acceso a Sway con PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="c9af9-139">For more information, see [Disable access to Sway with PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
>
    
<span data-ttu-id="c9af9-140">Para ver información resumida sobre los planes de licencias actuales y las licencias disponibles para cada plan, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="c9af9-140">To view summary information about your current licensing plans and the available licenses for each plan, run the following command:</span></span>
  
```powershell
Get-MsolAccountSku
```

>[!Note]
><span data-ttu-id="c9af9-141">PowerShell Core no es compatible con el Módulo Microsoft Azure Active Directory para Windows PowerShell ni los cmdlet que llevan **Msol** en su nombre.</span><span class="sxs-lookup"><span data-stu-id="c9af9-141">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="c9af9-142">Para seguir usando estos cmdlets, debe ejecutarlos desde Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c9af9-142">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="c9af9-143">Los resultados contienen la siguiente información:</span><span class="sxs-lookup"><span data-stu-id="c9af9-143">The results contain the following information:</span></span>
  
- <span data-ttu-id="c9af9-144">**AccountSkuId:** Mostrar los planes de licencias disponibles para la organización mediante la sintaxis `<CompanyName>:<LicensingPlan>` .</span><span class="sxs-lookup"><span data-stu-id="c9af9-144">**AccountSkuId:** Show the available licensing plans for your organization by using the syntax `<CompanyName>:<LicensingPlan>`.</span></span>  <span data-ttu-id="c9af9-145">_\<CompanyName>_ es el valor que proporcionó cuando se inscribió en Microsoft 365 y es único para su organización.</span><span class="sxs-lookup"><span data-stu-id="c9af9-145">_\<CompanyName>_ is the value that you provided when you enrolled in Microsoft 365, and is unique for your organization.</span></span> <span data-ttu-id="c9af9-146">El valor _\<LicensingPlan>_ es el mismo para todos los usuarios.</span><span class="sxs-lookup"><span data-stu-id="c9af9-146">The _\<LicensingPlan>_ value is the same for everyone.</span></span> <span data-ttu-id="c9af9-147">Por ejemplo, en el valor `litwareinc:ENTERPRISEPACK`, el nombre de la empresa es  `litwareinc` y el nombre del plan de licencias, `ENTERPRISEPACK`, que es el nombre de sistema para Office 365 Enterprise E3.</span><span class="sxs-lookup"><span data-stu-id="c9af9-147">For example, in the value `litwareinc:ENTERPRISEPACK`, the company name is  `litwareinc`, and the licensing plan name  `ENTERPRISEPACK`, which is the system name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="c9af9-148">**ActiveUnits:** Número de licencias que ha comprado para un plan de licencias específico.</span><span class="sxs-lookup"><span data-stu-id="c9af9-148">**ActiveUnits:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="c9af9-149">**WarningUnits**: número de licencias de un plan de licencias que no renovó y que expirarán al finalizar los 30 días del período de gracia.</span><span class="sxs-lookup"><span data-stu-id="c9af9-149">**WarningUnits:** Number of licenses in a licensing plan that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="c9af9-150">**ConsumedUnits**: es el número de licencias asignadas a los usuarios de un plan de licencias específico.</span><span class="sxs-lookup"><span data-stu-id="c9af9-150">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="c9af9-151">Para ver información detallada sobre los servicios de Microsoft 365 que están disponibles en todos los planes de licencia, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="c9af9-151">To view details about the Microsoft 365 services that are available in all of your license plans, run the following command:</span></span>
  
```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="c9af9-152">En la siguiente tabla se muestran los planes de servicio de Microsoft 365 y sus nombres descriptivos para los servicios más comunes.</span><span class="sxs-lookup"><span data-stu-id="c9af9-152">The following table shows the Microsoft 365 service plans and their friendly names for the most common services.</span></span> <span data-ttu-id="c9af9-153">Su lista de planes de servicio puede ser diferente.</span><span class="sxs-lookup"><span data-stu-id="c9af9-153">Your list of service plans might be different.</span></span> 
  
|<span data-ttu-id="c9af9-154">**Plan de servicio**</span><span class="sxs-lookup"><span data-stu-id="c9af9-154">**Service plan**</span></span>|<span data-ttu-id="c9af9-155">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="c9af9-155">**Description**</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="c9af9-156">Sway</span><span class="sxs-lookup"><span data-stu-id="c9af9-156">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="c9af9-157">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="c9af9-157">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="c9af9-158">Yammer</span><span class="sxs-lookup"><span data-stu-id="c9af9-158">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="c9af9-159">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="c9af9-159">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="c9af9-160">Microsoft 365 apps for Enterprise *(anteriormente denominado Office 365 ProPlus)*</span><span class="sxs-lookup"><span data-stu-id="c9af9-160">Microsoft 365 Apps for enterprise *(previously named Office 365 ProPlus)*</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="c9af9-161">Skype Empresarial Online</span><span class="sxs-lookup"><span data-stu-id="c9af9-161">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="c9af9-162">Office</span><span class="sxs-lookup"><span data-stu-id="c9af9-162">Office</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="c9af9-163">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="c9af9-163">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="c9af9-164">Plan 2 de Exchange Online</span><span class="sxs-lookup"><span data-stu-id="c9af9-164">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="c9af9-165">Para obtener una lista completa de los planes de licencia (también conocidos como nombres de producto), sus planes de servicio incluidos y los nombres descriptivos correspondientes, consulte [Product Names and Service Plan Identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span><span class="sxs-lookup"><span data-stu-id="c9af9-165">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

<span data-ttu-id="c9af9-166">Para ver información detallada sobre los servicios de Microsoft 365 que están disponibles en un plan de licencias específico, use la siguiente sintaxis.</span><span class="sxs-lookup"><span data-stu-id="c9af9-166">To view details about the Microsoft 365 services that are available in a specific licensing plan, use the following syntax.</span></span>
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

<span data-ttu-id="c9af9-167">En este ejemplo se muestran los servicios que están disponibles en el plan de licencias litwareinc: ENTERPRISEPACK (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="c9af9-167">This example shows the services that are available in the litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3) licensing plan.</span></span>
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```

## <a name="see-also"></a><span data-ttu-id="c9af9-168">Consulte también</span><span class="sxs-lookup"><span data-stu-id="c9af9-168">See also</span></span>

[<span data-ttu-id="c9af9-169">Administración de cuentas de usuario, licencias y grupos de Microsoft 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="c9af9-169">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="c9af9-170">Administrar Microsoft 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="c9af9-170">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="c9af9-171">Introducción a PowerShell para Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="c9af9-171">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)
