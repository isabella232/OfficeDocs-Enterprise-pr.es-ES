---
title: Registros DNS para Office 365 DoD
ms.author: dzazzo
author: dzazzo
manager: dzazzo
ms.date: 05/19/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- OGA150
- OGC150
- OGD150
- MOE150
ms.assetid: ''
description: 'Resumen: registros DNS para Office 365 DoD'
hideEdit: true
ms.openlocfilehash: d1f8c82224934f11eddbfa10c5dea7d15cc9e9a2
ms.sourcegitcommit: 576c3dbdef535f952a861197dea5348908da9504
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "44339817"
---
# <a name="dns-records-for-office-365-dod"></a><span data-ttu-id="0533c-103">Registros DNS para Office 365 DoD</span><span class="sxs-lookup"><span data-stu-id="0533c-103">DNS records for Office 365 DoD</span></span>

<span data-ttu-id="0533c-104">*Este artículo se aplica a Office 365 DoD y Microsoft 365 DoD*</span><span class="sxs-lookup"><span data-stu-id="0533c-104">*This article applies to Office 365 DoD and Microsoft 365 DoD*</span></span>

<span data-ttu-id="0533c-105">Como parte de la incorporación a Office 365 DoD, tendrá que agregar los dominios SMTP y SIP a su inquilino de servicios en línea.</span><span class="sxs-lookup"><span data-stu-id="0533c-105">As part of onboarding to Office 365 DoD, you will need to add your SMTP and SIP domains to your Online Services tenant.</span></span>  <span data-ttu-id="0533c-106">Para hacerlo, use el cmdlet New-MsolDomain en Azure AD PowerShell o use el [portal de Azure Government](https://portal.azure.us) para iniciar el proceso de agregar el dominio y demostrar la propiedad.</span><span class="sxs-lookup"><span data-stu-id="0533c-106">You’ll do this using the New-MsolDomain cmdlet in Azure AD PowerShell or use the [Azure Government Portal](https://portal.azure.us) to start the process of adding the domain and proving ownership.</span></span>

<span data-ttu-id="0533c-107">Una vez que haya agregado los dominios al espacio empresarial y se hayan validado, use las siguientes instrucciones para agregar los registros DNS adecuados para los servicios que se indican a continuación.</span><span class="sxs-lookup"><span data-stu-id="0533c-107">Once you have your domains added to your tenant and validated, use the following guidance to add the appropriate DNS records for the services below.</span></span>  <span data-ttu-id="0533c-108">Es posible que deba modificar la tabla que se muestra a continuación para ajustarse a las necesidades de su organización con respecto a los registros MX de entrada y los registros de Exchange Autodiscover existentes que haya en marcha.</span><span class="sxs-lookup"><span data-stu-id="0533c-108">You may need to modify the below table to fit your organization’s needs with respect to the inbound MX record(s) and any existing Exchange Autodiscover record(s) you have in place.</span></span>  <span data-ttu-id="0533c-109">Recomendamos encarecidamente coordinar estos registros DNS con su equipo de mensajería para evitar interrupciones o entregas no deseadas de correo electrónico.</span><span class="sxs-lookup"><span data-stu-id="0533c-109">We strongly recommend coordinating these DNS records with your messaging team to avoid any outages or mis-delivery of email.</span></span>

## <a name="exchange-online"></a><span data-ttu-id="0533c-110">Exchange en línea</span><span class="sxs-lookup"><span data-stu-id="0533c-110">Exchange Online</span></span>

| <span data-ttu-id="0533c-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="0533c-111">Type</span></span> | <span data-ttu-id="0533c-112">Prioridad</span><span class="sxs-lookup"><span data-stu-id="0533c-112">Priority</span></span> | <span data-ttu-id="0533c-113">Nombre de host</span><span class="sxs-lookup"><span data-stu-id="0533c-113">Host name</span></span> | <span data-ttu-id="0533c-114">Apunta a una dirección o un valor</span><span class="sxs-lookup"><span data-stu-id="0533c-114">Points to address or value</span></span> | <span data-ttu-id="0533c-115">TTL</span><span class="sxs-lookup"><span data-stu-id="0533c-115">TTL</span></span> |
| --- | --- | --- | --- | --- |
| <span data-ttu-id="0533c-116">MX</span><span class="sxs-lookup"><span data-stu-id="0533c-116">MX</span></span> | <span data-ttu-id="0533c-117">comprendi</span><span class="sxs-lookup"><span data-stu-id="0533c-117">0</span></span> | @ | <span data-ttu-id="0533c-118">*tenant*. mail.Protection.Office365.US (consulte a continuación para obtener más información)</span><span class="sxs-lookup"><span data-stu-id="0533c-118">*tenant*.mail.protection.office365.us (see below for additional details)</span></span> | <span data-ttu-id="0533c-119">1 Hour</span><span class="sxs-lookup"><span data-stu-id="0533c-119">1 Hour</span></span> |
| <span data-ttu-id="0533c-120">TXT</span><span class="sxs-lookup"><span data-stu-id="0533c-120">TXT</span></span> | - | @ | <span data-ttu-id="0533c-121">v = spf1 include include SPF. Protection. Office365. US-All</span><span class="sxs-lookup"><span data-stu-id="0533c-121">v=spf1 include:spf.protection.office365.us -all</span></span> | <span data-ttu-id="0533c-122">1 Hour</span><span class="sxs-lookup"><span data-stu-id="0533c-122">1 Hour</span></span> |
| <span data-ttu-id="0533c-123">CNAME</span><span class="sxs-lookup"><span data-stu-id="0533c-123">CNAME</span></span> | - | <span data-ttu-id="0533c-124">autodiscover</span><span class="sxs-lookup"><span data-stu-id="0533c-124">autodiscover</span></span> | <span data-ttu-id="0533c-125">autodiscover-dod.office365.us</span><span class="sxs-lookup"><span data-stu-id="0533c-125">autodiscover-dod.office365.us</span></span> | <span data-ttu-id="0533c-126">1 Hour</span><span class="sxs-lookup"><span data-stu-id="0533c-126">1 Hour</span></span> |

### <a name="exchange-autodiscover-record"></a><span data-ttu-id="0533c-127">Registro de detección automática de Exchange</span><span class="sxs-lookup"><span data-stu-id="0533c-127">Exchange Autodiscover record</span></span>

<span data-ttu-id="0533c-128">Si tiene Exchange Server local, le recomendamos dejar el registro existente en su lugar mientras migra a Exchange Online y actualizar dicho registro una vez que haya completado la migración.</span><span class="sxs-lookup"><span data-stu-id="0533c-128">If you have Exchange Server on-premises, we recommend leaving your existing record in place while you migrate to Exchange Online, and update that record once you have completed your migration.</span></span>

### <a name="exchange-online-mx-record"></a><span data-ttu-id="0533c-129">Registro MX de Exchange Online</span><span class="sxs-lookup"><span data-stu-id="0533c-129">Exchange Online MX Record</span></span>

<span data-ttu-id="0533c-130">El valor del registro MX para los dominios aceptados sigue un formato estándar, como se ha indicado anteriormente: *tenant*. mail.Protection.Office365.US, reemplazando a *tenant* con la primera parte del nombre del espacio empresarial predeterminado.</span><span class="sxs-lookup"><span data-stu-id="0533c-130">The MX record value for your accepted domains follows a standard format as noted above: *tenant*.mail.protection.office365.us, replacing *tenant* with the first part of your default tenant name.</span></span>

<span data-ttu-id="0533c-131">Por ejemplo, si el nombre de su espacio empresarial es contoso.onmicrosoft.us, usaría **contoso.mail.Protection.Office365.US** como el valor para el registro MX.</span><span class="sxs-lookup"><span data-stu-id="0533c-131">For example, if your tenant name is contoso.onmicrosoft.us, you’d use **contoso.mail.protection.office365.us** as the value for your MX record.</span></span>

## <a name="skype-for-business-online"></a><span data-ttu-id="0533c-132">Skype Empresarial Online</span><span class="sxs-lookup"><span data-stu-id="0533c-132">Skype for Business Online</span></span>

### <a name="cname-records"></a><span data-ttu-id="0533c-133">Registros CNAME</span><span class="sxs-lookup"><span data-stu-id="0533c-133">CNAME records</span></span>

| <span data-ttu-id="0533c-134">Tipo</span><span class="sxs-lookup"><span data-stu-id="0533c-134">Type</span></span> | <span data-ttu-id="0533c-135">Nombre de host</span><span class="sxs-lookup"><span data-stu-id="0533c-135">Host name</span></span> | <span data-ttu-id="0533c-136">Apunta a una dirección o un valor</span><span class="sxs-lookup"><span data-stu-id="0533c-136">Points to address or value</span></span> | <span data-ttu-id="0533c-137">TTL</span><span class="sxs-lookup"><span data-stu-id="0533c-137">TTL</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="0533c-138">CNAME</span><span class="sxs-lookup"><span data-stu-id="0533c-138">CNAME</span></span> | <span data-ttu-id="0533c-139">sip</span><span class="sxs-lookup"><span data-stu-id="0533c-139">sip</span></span> | <span data-ttu-id="0533c-140">sipdir.online.dod.skypeforbusiness.us</span><span class="sxs-lookup"><span data-stu-id="0533c-140">sipdir.online.dod.skypeforbusiness.us</span></span> | <span data-ttu-id="0533c-141">1 Hour</span><span class="sxs-lookup"><span data-stu-id="0533c-141">1 Hour</span></span> |
| <span data-ttu-id="0533c-142">CNAME</span><span class="sxs-lookup"><span data-stu-id="0533c-142">CNAME</span></span> | <span data-ttu-id="0533c-143">lyncdiscover</span><span class="sxs-lookup"><span data-stu-id="0533c-143">lyncdiscover</span></span> | <span data-ttu-id="0533c-144">webdir.online.dod.skypeforbusiness.us</span><span class="sxs-lookup"><span data-stu-id="0533c-144">webdir.online.dod.skypeforbusiness.us</span></span> | <span data-ttu-id="0533c-145">1 Hour</span><span class="sxs-lookup"><span data-stu-id="0533c-145">1 Hour</span></span> | 

### <a name="srv-records"></a><span data-ttu-id="0533c-146">Registros SRV</span><span class="sxs-lookup"><span data-stu-id="0533c-146">SRV records</span></span>

| <span data-ttu-id="0533c-147">Tipo</span><span class="sxs-lookup"><span data-stu-id="0533c-147">Type</span></span> | <span data-ttu-id="0533c-148">Servicio</span><span class="sxs-lookup"><span data-stu-id="0533c-148">Service</span></span> | <span data-ttu-id="0533c-149">Protocolo</span><span class="sxs-lookup"><span data-stu-id="0533c-149">Protocol</span></span> | <span data-ttu-id="0533c-150">Puerto</span><span class="sxs-lookup"><span data-stu-id="0533c-150">Port</span></span> | <span data-ttu-id="0533c-151">Peso</span><span class="sxs-lookup"><span data-stu-id="0533c-151">Weight</span></span> | <span data-ttu-id="0533c-152">Priority</span><span class="sxs-lookup"><span data-stu-id="0533c-152">Priority</span></span> | <span data-ttu-id="0533c-153">Nombre</span><span class="sxs-lookup"><span data-stu-id="0533c-153">Name</span></span> | <span data-ttu-id="0533c-154">Target</span><span class="sxs-lookup"><span data-stu-id="0533c-154">Target</span></span> | <span data-ttu-id="0533c-155">TTL</span><span class="sxs-lookup"><span data-stu-id="0533c-155">TTL</span></span> |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| <span data-ttu-id="0533c-156">SRV</span><span class="sxs-lookup"><span data-stu-id="0533c-156">SRV</span></span> | <span data-ttu-id="0533c-157">\_sip</span><span class="sxs-lookup"><span data-stu-id="0533c-157">\_sip</span></span> | <span data-ttu-id="0533c-158">\_MTLS</span><span class="sxs-lookup"><span data-stu-id="0533c-158">\_tls</span></span> | <span data-ttu-id="0533c-159">443</span><span class="sxs-lookup"><span data-stu-id="0533c-159">443</span></span> | <span data-ttu-id="0533c-160">1 </span><span class="sxs-lookup"><span data-stu-id="0533c-160">1</span></span> | <span data-ttu-id="0533c-161">100</span><span class="sxs-lookup"><span data-stu-id="0533c-161">100</span></span> | @ | <span data-ttu-id="0533c-162">sipdir.online.dod.skypeforbusiness.us</span><span class="sxs-lookup"><span data-stu-id="0533c-162">sipdir.online.dod.skypeforbusiness.us</span></span> | <span data-ttu-id="0533c-163">1 hora</span><span class="sxs-lookup"><span data-stu-id="0533c-163">1 Hour</span></span> |
| <span data-ttu-id="0533c-164">SRV</span><span class="sxs-lookup"><span data-stu-id="0533c-164">SRV</span></span> | <span data-ttu-id="0533c-165">\_sipfederationtls</span><span class="sxs-lookup"><span data-stu-id="0533c-165">\_sipfederationtls</span></span> | <span data-ttu-id="0533c-166">\_TPC</span><span class="sxs-lookup"><span data-stu-id="0533c-166">\_tcp</span></span> | <span data-ttu-id="0533c-167">5061</span><span class="sxs-lookup"><span data-stu-id="0533c-167">5061</span></span> | <span data-ttu-id="0533c-168">1 </span><span class="sxs-lookup"><span data-stu-id="0533c-168">1</span></span> | <span data-ttu-id="0533c-169">100</span><span class="sxs-lookup"><span data-stu-id="0533c-169">100</span></span> | @ | <span data-ttu-id="0533c-170">sipfed.online.dod.skypeforbusiness.us</span><span class="sxs-lookup"><span data-stu-id="0533c-170">sipfed.online.dod.skypeforbusiness.us</span></span> | <span data-ttu-id="0533c-171">1 Hour</span><span class="sxs-lookup"><span data-stu-id="0533c-171">1 Hour</span></span> |

## <a name="additional-dns-records"></a><span data-ttu-id="0533c-172">Registros DNS adicionales</span><span class="sxs-lookup"><span data-stu-id="0533c-172">Additional DNS records</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0533c-173">Si ya tiene un registro CNAME de *msoid* en la zona DNS, debe **quitar** el registro de DNS en este momento.</span><span class="sxs-lookup"><span data-stu-id="0533c-173">If you have an existing *msoid* CNAME record in your DNS zone, you must **remove** the record from DNS at this time.</span></span>  <span data-ttu-id="0533c-174">El registro msoid es incompatible con las aplicaciones empresariales de Microsoft 365 *(anteriormente Office 365 ProPlus)* y evitará que la activación se realice correctamente.</span><span class="sxs-lookup"><span data-stu-id="0533c-174">The msoid record is incompatible with Microsoft 365 Enterprise Apps *(formerly Office 365 ProPlus)* and will prevent activation from succeeding.</span></span>
