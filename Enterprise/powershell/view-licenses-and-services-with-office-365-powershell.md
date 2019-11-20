---
title: Ver las licencias y los servicios con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- O365ITProTrain
- LIL_Placement
- PowerShell
ms.assetid: bb5260a9-a6a3-4f34-b19a-06c6699f6723
description: Explica cómo usar PowerShell de Office 365 para ver información sobre los planes de licencias, los servicios y las licencias disponibles en su organización de Office 365.
ms.openlocfilehash: 8ee2c834063ea80388662c1f36f4524715f98a58
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2019
ms.locfileid: "38747459"
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a><span data-ttu-id="1eaf0-103">Ver licencias y servicios con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="1eaf0-103">View licenses and services with Office 365 PowerShell</span></span>

<span data-ttu-id="1eaf0-104">Todas las suscripciones de Office 365 se componen de estos elementos:</span><span class="sxs-lookup"><span data-stu-id="1eaf0-104">Every Office 365 subscription consists of the following elements:</span></span>

- <span data-ttu-id="1eaf0-105">**Planes de licencias** También se conocen como planes de licencia o planes de Office 365.</span><span class="sxs-lookup"><span data-stu-id="1eaf0-105">**Licensing plans** These are also known as license plans or Office 365 plans.</span></span> <span data-ttu-id="1eaf0-106">Los planes de licencias determinan los servicios de Office 365 que están disponibles para los usuarios.</span><span class="sxs-lookup"><span data-stu-id="1eaf0-106">Licensing plans define the Office 365 services that are available to users.</span></span> <span data-ttu-id="1eaf0-107">Su suscripción a Office 365 puede contener varios planes de licencias.</span><span class="sxs-lookup"><span data-stu-id="1eaf0-107">Your Office 365 subscription may contain multiple licensing plans.</span></span> <span data-ttu-id="1eaf0-108">Un plan de licencias de ejemplo sería Office 365 Enterprise E3.</span><span class="sxs-lookup"><span data-stu-id="1eaf0-108">An example licensing plan would be Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="1eaf0-109">**Servicios** de También se conocen como planes de servicio.</span><span class="sxs-lookup"><span data-stu-id="1eaf0-109">**Services** These are also known as service plans.</span></span> <span data-ttu-id="1eaf0-110">Los servicios son los productos, las características y las capacidades de Office 365 disponibles en cada plan de licencias, por ejemplo, Exchange Online y Office Professional Plus.</span><span class="sxs-lookup"><span data-stu-id="1eaf0-110">Services are the Office 365 products, features, and capabilities that are available in each licensing plan, for example, Exchange Online and Office Professional Plus.</span></span> <span data-ttu-id="1eaf0-111">Los usuarios pueden tener varias licencias asignadas que provengan de diferentes planes de licencias, y les permitan obtener acceso a diferentes servicios.</span><span class="sxs-lookup"><span data-stu-id="1eaf0-111">Users can have multiple licenses assigned to them from different licensing plans that grant access to different services.</span></span>
    
- <span data-ttu-id="1eaf0-p103">**Licencias** Los planes de licencias contienen el número de licencias que haya adquirido. Puede asignar licencias a los usuarios para que estos puedan usar los servicios de Office 365 definidos por el plan de licencias. Cada cuenta de usuario necesita como mínimo una licencia del plan de licencias para que el usuario correspondiente pueda iniciar sesión en Office 365 y usar los servicios.</span><span class="sxs-lookup"><span data-stu-id="1eaf0-p103">**Licenses** Each licensing plan contains the number of licenses that you purchased. You assign licenses to users so they can use the Office 365 services that are defined by the licensing plan. Every user account requires at least one license from one licensing plan so they can log on to Office 365 and use the services.</span></span>
    
<span data-ttu-id="1eaf0-p104">Puede usar PowerShell de Office 365 para ver información detallada sobre los planes de licencias, las licencias y los servicios disponibles en su organización de Office 365. Para obtener más información sobre los productos, las características y los servicios disponibles en las diferentes suscripciones de Office 365, consulte [Opciones de planes de Office 365](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span><span class="sxs-lookup"><span data-stu-id="1eaf0-p104">You can use Office 365 PowerShell to view details about the available licensing plans, licenses, and services in your Office 365 organization. For more information about the products, features, and services that are available in different Office 365 subscriptions, see [Office 365 Plan Options](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span></span>


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="1eaf0-117">Use el módulo de PowerShell Azure Active Directory para Graph</span><span class="sxs-lookup"><span data-stu-id="1eaf0-117">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="1eaf0-118">Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="1eaf0-118">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="1eaf0-119">Para ver información resumida sobre los planes de licencias actuales y las licencias disponibles para cada plan, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="1eaf0-119">To view summary information about your current licensing plans and the available licenses for each plan, run the following command:</span></span>
  
```powershell
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

<span data-ttu-id="1eaf0-120">Los resultados contienen la siguiente información:</span><span class="sxs-lookup"><span data-stu-id="1eaf0-120">The results contain the following information:</span></span>
  
- <span data-ttu-id="1eaf0-121">**SkuPartNumber:** Muestra los planes de licencias disponibles para su organización.</span><span class="sxs-lookup"><span data-stu-id="1eaf0-121">**SkuPartNumber:** Shows the available licensing plans for your organization.</span></span> <span data-ttu-id="1eaf0-122">Por ejemplo, `ENTERPRISEPACK` es el nombre del plan de licencias de Office 365 Enterprise E3.</span><span class="sxs-lookup"><span data-stu-id="1eaf0-122">For example, `ENTERPRISEPACK` is the license plan name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="1eaf0-123">**Habilitado:** Número de licencias que ha comprado para un plan de licencias específico.</span><span class="sxs-lookup"><span data-stu-id="1eaf0-123">**Enabled:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="1eaf0-124">**ConsumedUnits**: es el número de licencias asignadas a los usuarios de un plan de licencias específico.</span><span class="sxs-lookup"><span data-stu-id="1eaf0-124">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="1eaf0-125">Para ver información detallada sobre los servicios de Office 365 que están disponibles en todos los planes de licencias, primero muestre una lista de los planes de licencia.</span><span class="sxs-lookup"><span data-stu-id="1eaf0-125">To view details about the Office 365 services that are available in all of your license plans, first display a list of your license plans.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="1eaf0-126">A continuación, almacene la información de los planes de licencia en una variable.</span><span class="sxs-lookup"><span data-stu-id="1eaf0-126">Next, store the license plans information in a variable.</span></span>

```powershell
$licenses = Get-AzureADSubscribedSku
```

<span data-ttu-id="1eaf0-127">A continuación, muestre los servicios en un plan de licencias específico.</span><span class="sxs-lookup"><span data-stu-id="1eaf0-127">Next, display the services in a specific license plan.</span></span>

```powershell
$licenses[<index>].ServicePlans
```

<span data-ttu-id="1eaf0-128">\<el> de índice es un entero que especifica el número de fila del plan de licencia desde la presentación `Get-AzureADSubscribedSku | Select SkuPartNumber` del comando, menos 1.</span><span class="sxs-lookup"><span data-stu-id="1eaf0-128">\<index> is an integer that specifies the row number of the license plan from the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command, minus 1.</span></span>

<span data-ttu-id="1eaf0-129">Por ejemplo, si la presentación del `Get-AzureADSubscribedSku | Select SkuPartNumber` comando es la siguiente:</span><span class="sxs-lookup"><span data-stu-id="1eaf0-129">For example, if the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command is this:</span></span>

```powershell
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
```

<span data-ttu-id="1eaf0-130">A continuación, el comando para mostrar los servicios del plan de licencias ENTERPRISEPREMIUM es el siguiente:</span><span class="sxs-lookup"><span data-stu-id="1eaf0-130">Then the command to display the services for the ENTERPRISEPREMIUM license plan is this:</span></span>

```powershell
$licenses[2].ServicePlans
```

<span data-ttu-id="1eaf0-131">ENTERPRISEPREMIUM es la tercera fila.</span><span class="sxs-lookup"><span data-stu-id="1eaf0-131">ENTERPRISEPREMIUM is the third row.</span></span> <span data-ttu-id="1eaf0-132">Por lo tanto, el valor de índice es (3-1) o 2.</span><span class="sxs-lookup"><span data-stu-id="1eaf0-132">Therefore, the index value is (3 - 1), or 2.</span></span>

<span data-ttu-id="1eaf0-133">Para obtener una lista completa de los planes de licencia (también conocidos como nombres de producto), sus planes de servicio incluidos y los nombres descriptivos correspondientes, consulte [Product Names and Service Plan Identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span><span class="sxs-lookup"><span data-stu-id="1eaf0-133">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="1eaf0-134">Use el Módulo Microsoft Azure Active Directory para Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1eaf0-134">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="1eaf0-135">Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="1eaf0-135">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

>[!Note]
><span data-ttu-id="1eaf0-136">Hay un script de PowerShell que automatiza los procedimientos descritos en este tema.</span><span class="sxs-lookup"><span data-stu-id="1eaf0-136">A PowerShell script is available that automates the procedures described in this topic.</span></span> <span data-ttu-id="1eaf0-137">En concreto, el script permite ver y deshabilitar servicios en la organización de Office 365, incluido Sway.</span><span class="sxs-lookup"><span data-stu-id="1eaf0-137">Specifically, the script lets you view and disable services in your Office 365 organization, including Sway.</span></span> <span data-ttu-id="1eaf0-138">Para obtener más información, consulte [Deshabilitar el acceso a Sway con Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="1eaf0-138">For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
>
    
<span data-ttu-id="1eaf0-139">Para ver información resumida sobre los planes de licencias actuales y las licencias disponibles para cada plan, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="1eaf0-139">To view summary information about your current licensing plans and the available licenses for each plan, run the following command:</span></span>
  
```powershell
Get-MsolAccountSku
```

<span data-ttu-id="1eaf0-140">Los resultados contienen la siguiente información:</span><span class="sxs-lookup"><span data-stu-id="1eaf0-140">The results contain the following information:</span></span>
  
- <span data-ttu-id="1eaf0-p108">**AccountSkuId:** se muestran los planes de licencias disponibles para su organización con la sintaxis `<CompanyName>:<LicensingPlan>`. _<CompanyName>_ es el valor que proporcionó al inscribirse en Office 365; se trata de un valor único para su organización. El valor _<LicensingPlan>_ es el mismo para todos los usuarios. Por ejemplo, en el valor `litwareinc:ENTERPRISEPACK`, el nombre de la compañía es `litwareinc` y el nombre del plan de licencias es `ENTERPRISEPACK` (que es el nombre del sistema para Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="1eaf0-p108">**AccountSkuId:** Show the available licensing plans for your organization by using the syntax `<CompanyName>:<LicensingPlan>`.  _<CompanyName>_ is the value that you provided when you enrolled in Office 365, and is unique for your organization. The _<LicensingPlan>_ value is the same for everyone. For example, in the value `litwareinc:ENTERPRISEPACK`, the company name is  `litwareinc`, and the licensing plan name  `ENTERPRISEPACK`, which is the system name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="1eaf0-145">**ActiveUnits:** Número de licencias que ha comprado para un plan de licencias específico.</span><span class="sxs-lookup"><span data-stu-id="1eaf0-145">**ActiveUnits:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="1eaf0-146">**WarningUnits**: número de licencias de un plan de licencias que no renovó y que expirarán al finalizar los 30 días del período de gracia.</span><span class="sxs-lookup"><span data-stu-id="1eaf0-146">**WarningUnits:** Number of licenses in a licensing plan that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="1eaf0-147">**ConsumedUnits**: es el número de licencias asignadas a los usuarios de un plan de licencias específico.</span><span class="sxs-lookup"><span data-stu-id="1eaf0-147">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="1eaf0-148">Para ver información detallada sobre los servicios de Office 365 disponibles en todos sus planes de licencia, ejecute el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="1eaf0-148">To view details about the Office 365 services that are available in all of your license plans, run the following command:</span></span>
  
```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="1eaf0-149">En la tabla siguiente, se muestran los planes de servicio de Office 365, junto con sus nombres descriptivos, para los servicios más comunes.</span><span class="sxs-lookup"><span data-stu-id="1eaf0-149">The following table shows the Office 365 service plans and their friendly names for the most common services.</span></span> <span data-ttu-id="1eaf0-150">Su lista de planes de servicio puede ser diferente.</span><span class="sxs-lookup"><span data-stu-id="1eaf0-150">Your list of service plans might be different.</span></span> 
  
|<span data-ttu-id="1eaf0-151">**Plan de servicio**</span><span class="sxs-lookup"><span data-stu-id="1eaf0-151">**Service plan**</span></span>|<span data-ttu-id="1eaf0-152">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="1eaf0-152">**Description**</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="1eaf0-153">Sway</span><span class="sxs-lookup"><span data-stu-id="1eaf0-153">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="1eaf0-154">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="1eaf0-154">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="1eaf0-155">Yammer</span><span class="sxs-lookup"><span data-stu-id="1eaf0-155">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="1eaf0-156">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="1eaf0-156">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="1eaf0-157">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="1eaf0-157">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="1eaf0-158">Skype Empresarial Online</span><span class="sxs-lookup"><span data-stu-id="1eaf0-158">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="1eaf0-159">Oficina</span><span class="sxs-lookup"><span data-stu-id="1eaf0-159">Office</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="1eaf0-160">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="1eaf0-160">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="1eaf0-161">Plan 2 de Exchange Online</span><span class="sxs-lookup"><span data-stu-id="1eaf0-161">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="1eaf0-162">Para obtener una lista completa de los planes de licencia (también conocidos como nombres de producto), sus planes de servicio incluidos y los nombres descriptivos correspondientes, consulte [Product Names and Service Plan Identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span><span class="sxs-lookup"><span data-stu-id="1eaf0-162">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

<span data-ttu-id="1eaf0-163">Para obtener información detallada sobre los servicios de Office 365 disponibles en un plan de licencias en concreto, use la sintaxis siguiente.</span><span class="sxs-lookup"><span data-stu-id="1eaf0-163">To view details about the Office 365 services that are available in a specific licensing plan, use the following syntax.</span></span>
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

<span data-ttu-id="1eaf0-164">En este ejemplo se muestran los servicios de Office 365 que están disponibles en el plan de licencias litwareinc: ENTERPRISEPACK (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="1eaf0-164">This example shows the Office 365 services that are available in the litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3) licensing plan.</span></span>
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```


## <a name="new-to-office-365"></a><span data-ttu-id="1eaf0-165">¿Es la primera vez que usa Office 365?</span><span class="sxs-lookup"><span data-stu-id="1eaf0-165">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="1eaf0-166">Consulte también</span><span class="sxs-lookup"><span data-stu-id="1eaf0-166">See also</span></span>

[<span data-ttu-id="1eaf0-167">Administrar licencias y cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="1eaf0-167">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="1eaf0-168">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="1eaf0-168">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="1eaf0-169">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="1eaf0-169">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
