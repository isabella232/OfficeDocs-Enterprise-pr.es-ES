---
title: Requisitos de seguridad de red adicionales para Office 365 GCC High y DoD
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
- OGA150m
- OGC150
- OGD150
- MOE150
ms.assetid: ''
description: 'Resumen: Office 365 GCC High y DoD tienen requisitos de seguridad de red adicionales'
hideEdit: true
ms.openlocfilehash: a79204809787391065ac833d9a3872af4cdc1528
ms.sourcegitcommit: 576c3dbdef535f952a861197dea5348908da9504
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "44371636"
---
# <a name="additional-network-security-requirements-for-office-365-gcc-high-and-dod"></a><span data-ttu-id="c7bbc-103">Requisitos de seguridad de red adicionales para Office 365 GCC High y DOD</span><span class="sxs-lookup"><span data-stu-id="c7bbc-103">Additional network security requirements for Office 365 GCC High and DOD</span></span>

<span data-ttu-id="c7bbc-104">*Este artículo se aplica a Office 365 GCC High, Office 365 DOD, Microsoft 365 GCC High y Microsoft 365 DOD.*</span><span class="sxs-lookup"><span data-stu-id="c7bbc-104">*This article applies to Office 365 GCC High, Office 365 DOD, Microsoft 365 GCC High, and Microsoft 365 DOD.*</span></span>

<span data-ttu-id="c7bbc-105">Office 365 GCC High and DOD son entornos de nube segura para satisfacer las necesidades del gobierno de Estados Unidos y sus proveedores y contratistas.</span><span class="sxs-lookup"><span data-stu-id="c7bbc-105">Office 365 GCC High and DOD are secure cloud environments to meet the needs of the United States Government and its suppliers and contractors.</span></span>  <span data-ttu-id="c7bbc-106">Estos entornos de nube tienen restricciones de red adicionales en las que se permite el acceso a los extremos externos a los que tienen acceso los servicios.</span><span class="sxs-lookup"><span data-stu-id="c7bbc-106">These cloud environments have additional network restrictions on which external endpoints the services are permitted to access.</span></span>

<span data-ttu-id="c7bbc-107">Los clientes de GCC High y DOD que planean usar identidades federadas o coexistencia híbrida pueden requerir que Microsoft permita el acceso entrante y saliente a las implementaciones locales existentes.</span><span class="sxs-lookup"><span data-stu-id="c7bbc-107">GCC High and DOD customers planning to use federated identities or hybrid co-existence may require Microsoft to permit inbound and/or outbound access to your existing on-premises deployments.</span></span>  <span data-ttu-id="c7bbc-108">Algunos ejemplos de estas actividades son:</span><span class="sxs-lookup"><span data-stu-id="c7bbc-108">Examples of these activities include:</span></span>

* <span data-ttu-id="c7bbc-109">Uso de identidades federadas (con servicios de Federación de Active Directory o STS compatibles similares)</span><span class="sxs-lookup"><span data-stu-id="c7bbc-109">Use of federated identities (with Active Directory Federation Services or similar supported STS)</span></span>
* <span data-ttu-id="c7bbc-110">Coexistencia híbrida con una implementación local de Exchange Server o Skype empresarial</span><span class="sxs-lookup"><span data-stu-id="c7bbc-110">Hybrid coexistence with an on-premises Exchange Server or Skype for Business deployment</span></span>
* <span data-ttu-id="c7bbc-111">Migración del contenido de usuario existente desde un sistema local</span><span class="sxs-lookup"><span data-stu-id="c7bbc-111">Migration of existing user content from an on-premises system</span></span>

<span data-ttu-id="c7bbc-112">Para permitir que el servicio se comunique con los extremos locales, **debe** enviar un correo electrónico a Office 365 Engineering para cambios de red.</span><span class="sxs-lookup"><span data-stu-id="c7bbc-112">To permit the service to communicate with your on-premises endpoints, you **must** send an email to Office 365 engineering for network changes.</span></span>

> [!WARNING]
> <span data-ttu-id="c7bbc-113">Todas las solicitudes tienen un SLA de **tres semanas** y no se pueden acelerar debido a los controles de seguridad y cumplimiento necesarios y a las canalizaciones de implementación.</span><span class="sxs-lookup"><span data-stu-id="c7bbc-113">All requests have a **three-week** SLA and cannot be expedited due to the required security and compliance controls and deployment pipelines.</span></span>  <span data-ttu-id="c7bbc-114">Esto incluye las solicitudes de red de incorporación inicial y los cambios después de la migración al servicio.</span><span class="sxs-lookup"><span data-stu-id="c7bbc-114">This includes initial onboarding network requests as well as any changes after you have migrated to the service.</span></span>  <span data-ttu-id="c7bbc-115">Asegúrese de que los equipos de red conocen esta escala de tiempo e lo incluyen en sus ciclos de planeación.</span><span class="sxs-lookup"><span data-stu-id="c7bbc-115">Please ensure that your network teams are aware of this timeline and include it in their planning cycles.</span></span>

<span data-ttu-id="c7bbc-116">Envíe un correo electrónico a la [lista blanca de redes de Office 365 Government](mailto:o365gwlt@microsoft.com) con la siguiente información:</span><span class="sxs-lookup"><span data-stu-id="c7bbc-116">Please send an email to [Office 365 Government Network Whitelist](mailto:o365gwlt@microsoft.com) with the following information:</span></span>

* <span data-ttu-id="c7bbc-117">**Para**: [lista blanca de redes públicas de Office 365](mailto:o365gwlt@microsoft.com)</span><span class="sxs-lookup"><span data-stu-id="c7bbc-117">**To**: [Office 365 Government Network Whitelist](mailto:o365gwlt@microsoft.com)</span></span>
* <span data-ttu-id="c7bbc-118">**De**: un administrador de inquilinos: el envío de correo electrónico **debe** coincidir con un contacto de administrador global de su espacio empresarial.</span><span class="sxs-lookup"><span data-stu-id="c7bbc-118">**From**: A tenant administrator - the send email **must** match a Global Administrator contact in your tenant</span></span>
* <span data-ttu-id="c7bbc-119">**Asunto de correo electrónico**: Office 365 GCC solicitud de red alta-contoso.onmicrosoft.US (reemplácelo por el nombre del espacio empresarial)</span><span class="sxs-lookup"><span data-stu-id="c7bbc-119">**Email subject**: Office 365 GCC High Network Request - contoso.onmicrosoft.us (replace this with your tenant name)</span></span>

<span data-ttu-id="c7bbc-120">El cuerpo del mensaje debe incluir los datos siguientes:</span><span class="sxs-lookup"><span data-stu-id="c7bbc-120">The body of your message should include the following data:</span></span>

* <span data-ttu-id="c7bbc-121">El nombre del inquilino de Microsoft Online Services (por ejemplo, contoso.onmicrosoft.com, fabrikam.onmicrosoft.us)</span><span class="sxs-lookup"><span data-stu-id="c7bbc-121">Your Microsoft Online Services tenant name (i.e. contoso.onmicrosoft.com, fabrikam.onmicrosoft.us)</span></span>
* <span data-ttu-id="c7bbc-122">Una lista de distribución de correo electrónico con la que Microsoft se comunicará para las comunicaciones en curso relacionadas con los cambios en la red o el seguimiento de subredes no válidas</span><span class="sxs-lookup"><span data-stu-id="c7bbc-122">An email distribution list that Microsoft will communicate with for on-going communications related to network changes and/or follow up for invalid subnets</span></span>
* <span data-ttu-id="c7bbc-123">Indicar si planea usar la coexistencia híbrida de Microsoft Teams con las implementaciones locales</span><span class="sxs-lookup"><span data-stu-id="c7bbc-123">Indicate whether you plan to use Microsoft Teams hybrid co-existence with your on-premises deployments</span></span>
* <span data-ttu-id="c7bbc-124">Sistema de identidad federada URL de acceso externo (por ejemplo, sts.contoso.com) e intervalo de direcciones IP en notación CIDR (por ejemplo, 10.1.1.0/28)</span><span class="sxs-lookup"><span data-stu-id="c7bbc-124">Federated identity system externally accessible URL (e.g. sts.contoso.com) and IP address range in CIDR notation (e.g. 10.1.1.0/28)</span></span>
* <span data-ttu-id="c7bbc-125">Dirección URL de la lista de revocación de certificados de PKI local e intervalo de direcciones IP en notación CIDR</span><span class="sxs-lookup"><span data-stu-id="c7bbc-125">On-Premises PKI Certificate Revocation List URL and IP address range in CIDR notation</span></span>
* <span data-ttu-id="c7bbc-126">Dirección URL y intervalo de direcciones IP accesibles externamente para la implementación local de Exchange Server en la notación CIDR</span><span class="sxs-lookup"><span data-stu-id="c7bbc-126">Externally accessible URL and IP address range for Exchange Server on-premises deployment in CIDR notation</span></span>
* <span data-ttu-id="c7bbc-127">Dirección URL y intervalo de direcciones IP accesibles externamente para la implementación local de Skype empresarial en notación CIDR</span><span class="sxs-lookup"><span data-stu-id="c7bbc-127">Externally accessible URL and IP address range for Skype for Business on-premises deployment in CIDR notation</span></span>

<span data-ttu-id="c7bbc-128">Por motivos de seguridad y cumplimiento, tenga en cuenta las siguientes restricciones en su solicitud:</span><span class="sxs-lookup"><span data-stu-id="c7bbc-128">For security and compliance reasons, please keep in mind the following restrictions on your request:</span></span>

* <span data-ttu-id="c7bbc-129">Hay una limitación de cuatro subredes por espacio empresarial</span><span class="sxs-lookup"><span data-stu-id="c7bbc-129">There is a four subnet limitation per tenant</span></span>
* <span data-ttu-id="c7bbc-130">Las subredes deben estar en la notación CIDR (por ejemplo, 10.1.1.0/28)</span><span class="sxs-lookup"><span data-stu-id="c7bbc-130">Subnets must be in CIDR Notation (e.g. 10.1.1.0/28)</span></span>
* <span data-ttu-id="c7bbc-131">Los intervalos de subred no pueden ser mayores que/24</span><span class="sxs-lookup"><span data-stu-id="c7bbc-131">Subnet ranges cannot be larger than /24</span></span>
* <span data-ttu-id="c7bbc-132">**No se** admiten solicitudes para permitir el acceso a servicios en la nube comercial (commercial Office 365, Google G-Suite, servicios Web de Amazon, etc.)</span><span class="sxs-lookup"><span data-stu-id="c7bbc-132">We **cannot** accommodate requests to allow access to commercial cloud services (commercial Office 365, Google G-Suite, Amazon Web Services, etc.)</span></span>

<span data-ttu-id="c7bbc-133">Una vez que Microsoft ha recibido y aprobado su solicitud, hay un SLA de tres semanas para la implementación y no se le puede acelerar.</span><span class="sxs-lookup"><span data-stu-id="c7bbc-133">Once your request has been received and approved by Microsoft, there is a three-week SLA for implementation and cannot be expedited.</span></span>  <span data-ttu-id="c7bbc-134">Recibirá una confirmación inicial cuando haya recibido su solicitud y una confirmación final una vez que se haya completado.</span><span class="sxs-lookup"><span data-stu-id="c7bbc-134">You will receive an initial acknowledgment when we’ve received your request and a final acknowledgement once it has been completed.</span></span>
