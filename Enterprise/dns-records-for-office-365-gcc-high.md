---
title: Registros DNS para Office 365 GCC High
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
description: 'Resumen: registros DNS para Office 365 GCC High'
hideEdit: true
ms.openlocfilehash: 9bcaa71ab965f01481887d50a3e6ddbbbe3fadee
ms.sourcegitcommit: 576c3dbdef535f952a861197dea5348908da9504
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "44339807"
---
# <a name="dns-records-for-office-365-gcc-high"></a><span data-ttu-id="7663f-103">Registros DNS para Office 365 GCC High</span><span class="sxs-lookup"><span data-stu-id="7663f-103">DNS records for Office 365 GCC High</span></span>

<span data-ttu-id="7663f-104">*Este artículo se aplica a Office 365 GCC High y Microsoft 365 GCC High*</span><span class="sxs-lookup"><span data-stu-id="7663f-104">*This article applies to Office 365 GCC High and Microsoft 365 GCC High*</span></span>

<span data-ttu-id="7663f-105">Como parte de la incorporación a Office 365 GCC High, tendrá que agregar los dominios SMTP y SIP a su inquilino de servicios en línea.</span><span class="sxs-lookup"><span data-stu-id="7663f-105">As part of onboarding to Office 365 GCC High, you will need to add your SMTP and SIP domains to your Online Services tenant.</span></span>  <span data-ttu-id="7663f-106">Para hacerlo, use el cmdlet New-MsolDomain en Azure AD PowerShell o use el [portal de Azure Government](https://portal.azure.us) para iniciar el proceso de agregar el dominio y demostrar la propiedad.</span><span class="sxs-lookup"><span data-stu-id="7663f-106">You’ll do this using the New-MsolDomain cmdlet in Azure AD PowerShell or use the [Azure Government Portal](https://portal.azure.us) to start the process of adding the domain and proving ownership.</span></span>

<span data-ttu-id="7663f-107">Una vez que haya agregado los dominios al espacio empresarial y se hayan validado, use las siguientes instrucciones para agregar los registros DNS adecuados para los servicios que se indican a continuación.</span><span class="sxs-lookup"><span data-stu-id="7663f-107">Once you have your domains added to your tenant and validated, use the following guidance to add the appropriate DNS records for the services below.</span></span>  <span data-ttu-id="7663f-108">Es posible que deba modificar la tabla que se muestra a continuación para ajustarse a las necesidades de su organización con respecto a los registros MX de entrada y los registros de Exchange Autodiscover existentes que haya en marcha.</span><span class="sxs-lookup"><span data-stu-id="7663f-108">You may need to modify the below table to fit your organization’s needs with respect to the inbound MX record(s) and any existing Exchange Autodiscover record(s) you have in place.</span></span>  <span data-ttu-id="7663f-109">Recomendamos encarecidamente coordinar estos registros DNS con su equipo de mensajería para evitar interrupciones o entregas no deseadas de correo electrónico.</span><span class="sxs-lookup"><span data-stu-id="7663f-109">We strongly recommend coordinating these DNS records with your messaging team to avoid any outages or mis-delivery of email.</span></span>

## <a name="exchange-online"></a><span data-ttu-id="7663f-110">Exchange en línea</span><span class="sxs-lookup"><span data-stu-id="7663f-110">Exchange Online</span></span>

| <span data-ttu-id="7663f-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="7663f-111">Type</span></span> | <span data-ttu-id="7663f-112">Prioridad</span><span class="sxs-lookup"><span data-stu-id="7663f-112">Priority</span></span> | <span data-ttu-id="7663f-113">Nombre de host</span><span class="sxs-lookup"><span data-stu-id="7663f-113">Host name</span></span> | <span data-ttu-id="7663f-114">Apunta a una dirección o un valor</span><span class="sxs-lookup"><span data-stu-id="7663f-114">Points to address or value</span></span> | <span data-ttu-id="7663f-115">TTL</span><span class="sxs-lookup"><span data-stu-id="7663f-115">TTL</span></span> |
| --- | --- | --- | --- | --- |
| <span data-ttu-id="7663f-116">MX</span><span class="sxs-lookup"><span data-stu-id="7663f-116">MX</span></span> | <span data-ttu-id="7663f-117">comprendi</span><span class="sxs-lookup"><span data-stu-id="7663f-117">0</span></span> | @ | <span data-ttu-id="7663f-118">*tenant*. mail.Protection.Office365.US (consulte a continuación para obtener más información)</span><span class="sxs-lookup"><span data-stu-id="7663f-118">*tenant*.mail.protection.office365.us (see below for additional details)</span></span> | <span data-ttu-id="7663f-119">1 Hour</span><span class="sxs-lookup"><span data-stu-id="7663f-119">1 Hour</span></span> |
| <span data-ttu-id="7663f-120">TXT</span><span class="sxs-lookup"><span data-stu-id="7663f-120">TXT</span></span> | - | @ | <span data-ttu-id="7663f-121">v = spf1 include include SPF. Protection. Office365. US-All</span><span class="sxs-lookup"><span data-stu-id="7663f-121">v=spf1 include:spf.protection.office365.us -all</span></span> | <span data-ttu-id="7663f-122">1 Hour</span><span class="sxs-lookup"><span data-stu-id="7663f-122">1 Hour</span></span> |
| <span data-ttu-id="7663f-123">CNAME</span><span class="sxs-lookup"><span data-stu-id="7663f-123">CNAME</span></span> | - | <span data-ttu-id="7663f-124">autodiscover</span><span class="sxs-lookup"><span data-stu-id="7663f-124">autodiscover</span></span> | <span data-ttu-id="7663f-125">autodiscover.office365.us</span><span class="sxs-lookup"><span data-stu-id="7663f-125">autodiscover.office365.us</span></span> | <span data-ttu-id="7663f-126">1 Hour</span><span class="sxs-lookup"><span data-stu-id="7663f-126">1 Hour</span></span> |

### <a name="exchange-autodiscover-record"></a><span data-ttu-id="7663f-127">Registro de detección automática de Exchange</span><span class="sxs-lookup"><span data-stu-id="7663f-127">Exchange Autodiscover record</span></span>

<span data-ttu-id="7663f-128">Si tiene Exchange Server local, le recomendamos dejar el registro existente en su lugar mientras migra a Exchange Online y actualizar dicho registro una vez que haya completado la migración.</span><span class="sxs-lookup"><span data-stu-id="7663f-128">If you have Exchange Server on-premises, we recommend leaving your existing record in place while you migrate to Exchange Online, and update that record once you have completed your migration.</span></span> 

### <a name="exchange-online-mx-record"></a><span data-ttu-id="7663f-129">Registro MX de Exchange Online</span><span class="sxs-lookup"><span data-stu-id="7663f-129">Exchange Online MX Record</span></span>

<span data-ttu-id="7663f-130">El valor del registro MX para los dominios aceptados sigue un formato estándar, como se ha indicado anteriormente: *tenant*. mail.Protection.Office365.US, reemplazando a *tenant* con la primera parte del nombre del espacio empresarial predeterminado.</span><span class="sxs-lookup"><span data-stu-id="7663f-130">The MX record value for your accepted domains follows a standard format as noted above: *tenant*.mail.protection.office365.us, replacing *tenant* with the first part of your default tenant name.</span></span>

<span data-ttu-id="7663f-131">Por ejemplo, si el nombre de su espacio empresarial es contoso.onmicrosoft.us, usaría **contoso.mail.Protection.Office365.US** como el valor para el registro MX.</span><span class="sxs-lookup"><span data-stu-id="7663f-131">For example, if your tenant name is contoso.onmicrosoft.us, you’d use **contoso.mail.protection.office365.us** as the value for your MX record.</span></span>

## <a name="skype-for-business-online"></a><span data-ttu-id="7663f-132">Skype Empresarial Online</span><span class="sxs-lookup"><span data-stu-id="7663f-132">Skype for Business Online</span></span>

### <a name="cname-records"></a><span data-ttu-id="7663f-133">Registros CNAME</span><span class="sxs-lookup"><span data-stu-id="7663f-133">CNAME records</span></span>

| <span data-ttu-id="7663f-134">Tipo</span><span class="sxs-lookup"><span data-stu-id="7663f-134">Type</span></span> | <span data-ttu-id="7663f-135">Nombre de host</span><span class="sxs-lookup"><span data-stu-id="7663f-135">Host name</span></span> | <span data-ttu-id="7663f-136">Apunta a una dirección o un valor</span><span class="sxs-lookup"><span data-stu-id="7663f-136">Points to address or value</span></span> | <span data-ttu-id="7663f-137">TTL</span><span class="sxs-lookup"><span data-stu-id="7663f-137">TTL</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="7663f-138">CNAME</span><span class="sxs-lookup"><span data-stu-id="7663f-138">CNAME</span></span> | <span data-ttu-id="7663f-139">sip</span><span class="sxs-lookup"><span data-stu-id="7663f-139">sip</span></span> | <span data-ttu-id="7663f-140">sipdir.online.gov.skypeforbusiness.us</span><span class="sxs-lookup"><span data-stu-id="7663f-140">sipdir.online.gov.skypeforbusiness.us</span></span> | <span data-ttu-id="7663f-141">1 Hour</span><span class="sxs-lookup"><span data-stu-id="7663f-141">1 Hour</span></span> |
| <span data-ttu-id="7663f-142">CNAME</span><span class="sxs-lookup"><span data-stu-id="7663f-142">CNAME</span></span> | <span data-ttu-id="7663f-143">lyncdiscover</span><span class="sxs-lookup"><span data-stu-id="7663f-143">lyncdiscover</span></span> | <span data-ttu-id="7663f-144">webdir.online.gov.skypeforbusiness.us</span><span class="sxs-lookup"><span data-stu-id="7663f-144">webdir.online.gov.skypeforbusiness.us</span></span> | <span data-ttu-id="7663f-145">1 Hour</span><span class="sxs-lookup"><span data-stu-id="7663f-145">1 Hour</span></span> |

### <a name="srv-records"></a><span data-ttu-id="7663f-146">Registros SRV</span><span class="sxs-lookup"><span data-stu-id="7663f-146">SRV records</span></span>

| <span data-ttu-id="7663f-147">Tipo</span><span class="sxs-lookup"><span data-stu-id="7663f-147">Type</span></span> | <span data-ttu-id="7663f-148">Servicio</span><span class="sxs-lookup"><span data-stu-id="7663f-148">Service</span></span> | <span data-ttu-id="7663f-149">Protocolo</span><span class="sxs-lookup"><span data-stu-id="7663f-149">Protocol</span></span> | <span data-ttu-id="7663f-150">Puerto</span><span class="sxs-lookup"><span data-stu-id="7663f-150">Port</span></span> | <span data-ttu-id="7663f-151">Peso</span><span class="sxs-lookup"><span data-stu-id="7663f-151">Weight</span></span> | <span data-ttu-id="7663f-152">Priority</span><span class="sxs-lookup"><span data-stu-id="7663f-152">Priority</span></span> | <span data-ttu-id="7663f-153">Nombre</span><span class="sxs-lookup"><span data-stu-id="7663f-153">Name</span></span> | <span data-ttu-id="7663f-154">Target</span><span class="sxs-lookup"><span data-stu-id="7663f-154">Target</span></span> | <span data-ttu-id="7663f-155">TTL</span><span class="sxs-lookup"><span data-stu-id="7663f-155">TTL</span></span> |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| <span data-ttu-id="7663f-156">SRV</span><span class="sxs-lookup"><span data-stu-id="7663f-156">SRV</span></span> | <span data-ttu-id="7663f-157">\_sip</span><span class="sxs-lookup"><span data-stu-id="7663f-157">\_sip</span></span> | <span data-ttu-id="7663f-158">\_MTLS</span><span class="sxs-lookup"><span data-stu-id="7663f-158">\_tls</span></span> | <span data-ttu-id="7663f-159">443</span><span class="sxs-lookup"><span data-stu-id="7663f-159">443</span></span> | <span data-ttu-id="7663f-160">1 </span><span class="sxs-lookup"><span data-stu-id="7663f-160">1</span></span> | <span data-ttu-id="7663f-161">100</span><span class="sxs-lookup"><span data-stu-id="7663f-161">100</span></span> | @ | <span data-ttu-id="7663f-162">sipdir.online.gov.skypeforbusiness.us</span><span class="sxs-lookup"><span data-stu-id="7663f-162">sipdir.online.gov.skypeforbusiness.us</span></span> | <span data-ttu-id="7663f-163">1 hora</span><span class="sxs-lookup"><span data-stu-id="7663f-163">1 Hour</span></span> |
| <span data-ttu-id="7663f-164">SRV</span><span class="sxs-lookup"><span data-stu-id="7663f-164">SRV</span></span> | <span data-ttu-id="7663f-165">\_sipfederationtls</span><span class="sxs-lookup"><span data-stu-id="7663f-165">\_sipfederationtls</span></span> | <span data-ttu-id="7663f-166">\_TPC</span><span class="sxs-lookup"><span data-stu-id="7663f-166">\_tcp</span></span> | <span data-ttu-id="7663f-167">5061</span><span class="sxs-lookup"><span data-stu-id="7663f-167">5061</span></span> | <span data-ttu-id="7663f-168">1 </span><span class="sxs-lookup"><span data-stu-id="7663f-168">1</span></span> | <span data-ttu-id="7663f-169">100</span><span class="sxs-lookup"><span data-stu-id="7663f-169">100</span></span> | @ | <span data-ttu-id="7663f-170">sipfed.online.gov.skypeforbusiness.us</span><span class="sxs-lookup"><span data-stu-id="7663f-170">sipfed.online.gov.skypeforbusiness.us</span></span> | <span data-ttu-id="7663f-171">1 Hour</span><span class="sxs-lookup"><span data-stu-id="7663f-171">1 Hour</span></span> |

## <a name="additional-dns-records"></a><span data-ttu-id="7663f-172">Registros DNS adicionales</span><span class="sxs-lookup"><span data-stu-id="7663f-172">Additional DNS records</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7663f-173">Si ya tiene un registro CNAME de *msoid* en la zona DNS, debe **quitar** el registro de DNS en este momento.</span><span class="sxs-lookup"><span data-stu-id="7663f-173">If you have an existing *msoid* CNAME record in your DNS zone, you must **remove** the record from DNS at this time.</span></span>  <span data-ttu-id="7663f-174">El registro msoid es incompatible con las aplicaciones empresariales de Microsoft 365 *(anteriormente Office 365 ProPlus)* y evitará que la activación se realice correctamente.</span><span class="sxs-lookup"><span data-stu-id="7663f-174">The msoid record is incompatible with Microsoft 365 Enterprise Apps *(formerly Office 365 ProPlus)* and will prevent activation from succeeding.</span></span>
