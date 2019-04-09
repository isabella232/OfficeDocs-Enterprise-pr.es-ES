---
title: Manage Office 365 with Windows PowerShell for Delegated Access Permissions (DAP) partners
ms.author: chrfox
author: chrfox
manager: laurawi
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
ms.custom: ''
ms.assetid: be497751-596f-431d-b256-0a89d36a47ce
description: Resumen:Socios de sindicación y proveedor de soluciones en la nube (CSP) can use Windows PowerShell to manage Office 365 customer tenants.
ms.openlocfilehash: cab32f5c38e09a2c4407eb0831f4b67ccc3940f1
ms.sourcegitcommit: 29f937b7430c708c9dbec23bdc4089e86c37c225
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/29/2019
ms.locfileid: "31001803"
---
# <a name="manage-office-365-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="91a91-103">Manage Office 365 with Windows PowerShell for Delegated Access Permissions (DAP) partners</span><span class="sxs-lookup"><span data-stu-id="91a91-103">Manage Office 365 with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

 <span data-ttu-id="91a91-104">**Resumen:** los partners de redifusión y los proveedores de soluciones en la nube (CSP) pueden usar Windows PowerShell para administrar espacios empresariales de clientes de Office 365.</span><span class="sxs-lookup"><span data-stu-id="91a91-104">**Summary:** Syndication and Cloud Solution Provider (CSP) partners can use Windows PowerShell to manage Office 365 customer tenants.</span></span>
  
<span data-ttu-id="91a91-105">Los asociados con permiso de acceso delegado (DAP) son asociados de sindicación y proveedor de soluciones en la nube (CSP).</span><span class="sxs-lookup"><span data-stu-id="91a91-105">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="91a91-106">Con frecuencia son los proveedores de red o de telecomunicaciones para otras compañías.</span><span class="sxs-lookup"><span data-stu-id="91a91-106">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="91a91-107">Empaquetan las suscripciones de Office 365 en sus ofertas de servicio a sus clientes.</span><span class="sxs-lookup"><span data-stu-id="91a91-107">They bundle Office 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="91a91-108">Cuando se vende una suscripción a Office 365, automáticamente se les conceden permisos Administrar en nombre de (AOBO) a los arrendamientos de cliente para que puedan administrar y notificar los arrendamientos de cliente.</span><span class="sxs-lookup"><span data-stu-id="91a91-108">When they sell an O365_W14_2nd subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span> <span data-ttu-id="91a91-109">At best, this is difficult and time consuming to do in the Centro de administración de Office 365.</span><span class="sxs-lookup"><span data-stu-id="91a91-109">At best, this is difficult and time consuming to do in the Office 365 admin center.</span></span> <span data-ttu-id="91a91-110">It is much easier to do administrative tasks like listing all the customer **TenantIds** and their domains or identifying all users in a customer tenancy and what licenses they are assigned by using Windows PowerShell for Office 365.</span><span class="sxs-lookup"><span data-stu-id="91a91-110">It is much easier to do administrative tasks like listing all the customer **TenantIds** and their domains or identifying all users in a customer tenancy and what licenses they are assigned by using Windows PowerShell for Office 365.</span></span> <span data-ttu-id="91a91-111">In some cases, it is possible to do these administrative tasks only in Windows PowerShell for Office 365.</span><span class="sxs-lookup"><span data-stu-id="91a91-111">In some cases, it is possible to do these administrative tasks only in Windows PowerShell for Office 365.</span></span> <span data-ttu-id="91a91-112">Here are samples of scenarios that Syndication and CSP partners most frequently use to administer their customer tenancies:</span><span class="sxs-lookup"><span data-stu-id="91a91-112">Here are samples of scenarios that Syndication and CSP partners most frequently use to administer their customer tenancies:</span></span>
  
## 

- [<span data-ttu-id="91a91-113">Administrar inquilinos de Office 365 con Windows PowerShell para asociados con permiso de acceso delegado (DAP)</span><span class="sxs-lookup"><span data-stu-id="91a91-113">Manage Office 365 tenants with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](manage-office-365-tenants-with-windows-powershell-for-delegated-access-permissio.md)
    
- [<span data-ttu-id="91a91-114">Agregar un dominio a un arrendamiento de cliente con Windows PowerShell para asociados con permiso de acceso delegado (DAP)</span><span class="sxs-lookup"><span data-stu-id="91a91-114">Add a domain to a client tenancy with Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>](add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-pe.md)
    
- [<span data-ttu-id="91a91-115">Conectarse a los inquilinos de Exchange Online con el modo remoto de Windows PowerShell para asociados con permiso de acceso delegado (DAP)</span><span class="sxs-lookup"><span data-stu-id="91a91-115">Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)
    
- [<span data-ttu-id="91a91-116">Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners</span><span class="sxs-lookup"><span data-stu-id="91a91-116">Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-ac.md)
    
- [<span data-ttu-id="91a91-117">Agregar datos de informes de clientes a través de Windows PowerShell para asociados con permiso de acceso delegado (DAP)</span><span class="sxs-lookup"><span data-stu-id="91a91-117">Aggregate customer reporting data via Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>](aggregate-customer-reporting-data-via-windows-powershell-for-delegated-access-pe.md)
    

