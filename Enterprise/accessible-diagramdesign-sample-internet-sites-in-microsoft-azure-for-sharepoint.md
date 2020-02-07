---
title: 'Diagrama accesible: sitios de Internet de ejemplo de diseño en Microsoft Azure para SharePoint 2013'
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.collection: Ent_O365
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b91124bc-c7ec-4929-b77c-d6293db9f15e
f1.keywords:
- NOCSH
description: 'Este artículo es una versión de texto accesible del diagrama Ejemplo de diseño: Sitios de Internet en Microsoft Azure con SharePoint Server 2013.'
ms.openlocfilehash: b3669304fee6b7a89bc5d1bde96c39c496122d48
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843801"
---
# <a name="accessible-diagram---design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a><span data-ttu-id="3db32-103">Diagrama accesible: Muestra de diseño. Sitios de Internet en Microsoft Azure para SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="3db32-103">Accessible diagram - Design sample: Internet sites in Microsoft Azure for SharePoint 2013</span></span>

<span data-ttu-id="3db32-104">**Resumen:** Este artículo es una versión de texto accesible del diagrama ejemplo de diseño: sitios de Internet en Microsoft Azure para SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="3db32-104">**Summary:** This article is an accessible text version of the diagram named Design sample: Internet sites in Microsoft Azure for SharePoint 2013.</span></span>
  
<span data-ttu-id="3db32-105">Use este ejemplo de diseño como punto de partida para un sitio orientado a Internet en Azure con SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="3db32-105">Use this design example as a starting point for an Internet-facing site in Azure using SharePoint 2013.</span></span>
  
<span data-ttu-id="3db32-106">En este póster se muestra un ejemplo de cómo diseñar los siguientes aspectos de SharePoint 2013:</span><span class="sxs-lookup"><span data-stu-id="3db32-106">This poster shows an example of how to design the following aspects of SharePoint 2013:</span></span>
  
- <span data-ttu-id="3db32-107">Usuarios</span><span class="sxs-lookup"><span data-stu-id="3db32-107">Users</span></span>
    
- <span data-ttu-id="3db32-108">Zonas y autenticación</span><span class="sxs-lookup"><span data-stu-id="3db32-108">Zones and authentication</span></span>
    
- <span data-ttu-id="3db32-109">Granja de servidores</span><span class="sxs-lookup"><span data-stu-id="3db32-109">Server farm</span></span>
    
- <span data-ttu-id="3db32-110">Sitio de administración</span><span class="sxs-lookup"><span data-stu-id="3db32-110">Administration site</span></span>
    
- <span data-ttu-id="3db32-111">Servicios</span><span class="sxs-lookup"><span data-stu-id="3db32-111">Services</span></span>
    
- <span data-ttu-id="3db32-112">Grupos de aplicaciones y aplicaciones web</span><span class="sxs-lookup"><span data-stu-id="3db32-112">Application pools and web applications</span></span>
    
- <span data-ttu-id="3db32-113">Colecciones de sitios</span><span class="sxs-lookup"><span data-stu-id="3db32-113">Site collections</span></span>
    
- <span data-ttu-id="3db32-114">Sitios</span><span class="sxs-lookup"><span data-stu-id="3db32-114">Sites</span></span>
    
- <span data-ttu-id="3db32-115">Bases de datos de contenido</span><span class="sxs-lookup"><span data-stu-id="3db32-115">Content databases</span></span>
    
- <span data-ttu-id="3db32-116">Zonas y direcciones URL</span><span class="sxs-lookup"><span data-stu-id="3db32-116">Zones and URLs</span></span>
    
## <a name="users-zones-and-authentication"></a><span data-ttu-id="3db32-117">Usuarios, zonas y autenticación</span><span class="sxs-lookup"><span data-stu-id="3db32-117">Users, zones and authentication</span></span>

<span data-ttu-id="3db32-p101">Hay cuatro tipos de cuentas de usuario en este diseño. Cada tipo de cuenta está asociado con un sitio para el acceso y con una zona que usa un tipo de autenticación específico. </span><span class="sxs-lookup"><span data-stu-id="3db32-p101">There are four types of user accounts in this design. Each type of account is associated with a site for access and with a zone that uses a specific type of authentication.</span></span> 
  
- <span data-ttu-id="3db32-120">Clientes anónimos: los clientes anónimos tienen acceso a través https://www.contoso.comde un sitio como.</span><span class="sxs-lookup"><span data-stu-id="3db32-120">Anonymous customers — Anonymous customers have access through a site such as https://www.contoso.com.</span></span> <span data-ttu-id="3db32-121">La zona que usan es la "zona de Internet/anónima", que usa la autenticación anónima.</span><span class="sxs-lookup"><span data-stu-id="3db32-121">The zone they use is the "Internet zone / anonymous", which uses anonymous authentication.</span></span>
    
- <span data-ttu-id="3db32-122">Clientes autenticados: los clientes autenticados tienen acceso a través de un https://secure.contoso.comsitio como.</span><span class="sxs-lookup"><span data-stu-id="3db32-122">Authenticated customers — Authenticated customers have access through a site such as https://secure.contoso.com.</span></span> <span data-ttu-id="3db32-123">La zona que usan es la "zona de extranet/SAML", que usa Azure Active Directory con autenticación SAML.</span><span class="sxs-lookup"><span data-stu-id="3db32-123">The zone they use is the "Extranet zone / SAML", which uses Azure Active Directory with SAML authentication.</span></span>
    
- <span data-ttu-id="3db32-124">Autores y desarrolladores de sitios: los autores y programadores de sitios tienen acceso https://authoring.contoso.com:8000 a https://www.contoso.com:8000través de sitios como o.</span><span class="sxs-lookup"><span data-stu-id="3db32-124">Site authors and developers — Site authors and developers have access through sites such as https://authoring.contoso.com:8000 or https://www.contoso.com:8000.</span></span> <span data-ttu-id="3db32-125">La zona que usan es la "zona predeterminada de Windows/integrada", que usa los servicios de dominio de Active Directory (AD DS).</span><span class="sxs-lookup"><span data-stu-id="3db32-125">The zone they use is the "Default zone / Windows integrated", which uses Active Directory Domain Services (AD DS).</span></span>
    
- <span data-ttu-id="3db32-126">Cuenta de rastreo de búsqueda: la cuenta de rastreo de búsqueda https://authoring.contoso.com:8000 tiene https://www.contoso.com:8000acceso a través de sitios como o.</span><span class="sxs-lookup"><span data-stu-id="3db32-126">Search Crawl Account — The search crawl account has access through sites such as https://authoring.contoso.com:8000 or https://www.contoso.com:8000.</span></span> <span data-ttu-id="3db32-127">La zona que usa es la "zona predeterminada integrada en Windows", que usa AD DS con autenticación NTLM de Windows.</span><span class="sxs-lookup"><span data-stu-id="3db32-127">The zone it uses is the "Default zone / Windows integrated", which uses AD DS with Windows NTLM authentication.</span></span>
    
## <a name="server-farm"></a><span data-ttu-id="3db32-128">Granja de servidores</span><span class="sxs-lookup"><span data-stu-id="3db32-128">Server farm</span></span>

<span data-ttu-id="3db32-p106">Los usuarios acceden a la granja de servidores a través de Azure. La granja de servidores contiene uno o varios servidores web.</span><span class="sxs-lookup"><span data-stu-id="3db32-p106">The users access the server farm through Azure. The server farm contains one or more Web servers.</span></span>
  
## <a name="administration-site"></a><span data-ttu-id="3db32-131">Sitio de administración</span><span class="sxs-lookup"><span data-stu-id="3db32-131">Administration site</span></span>

<span data-ttu-id="3db32-p107">El sitio de administración contiene varios servidores de aplicaciones, que se comunican con un grupo de aplicaciones (grupo de aplicaciones 1 en el ejemplo) que usa el sitio de Administración Central de la aplicación web. El sitio de Administración central proporciona acceso a las colecciones de sitios dentro de la organización.</span><span class="sxs-lookup"><span data-stu-id="3db32-p107">The administration site contains several application servers, which communicate with an Application Pool (Application Pool 1 in the example) that uses the web application Central Administration Site. The Central Administration Site provides access to site collections within the organization.</span></span>
  
<span data-ttu-id="3db32-134">El sitio de administración también contiene servidores de Base de datos SQL, que son servidores de base de datos con SQL Server instalado y configurado para admitir la agrupación en clústeres de SQL, la creación de reflejos o AlwaysOn (AlwaysOn solo se aplica a SQL Server 2012).</span><span class="sxs-lookup"><span data-stu-id="3db32-134">The administration site also contains SQL Database servers, which are database servers with SQL Server installed and configured to support SQL clustering, mirroring, or AlwaysOn (AlwaysOn applies to SQL Server 2012 only).</span></span>
  
## <a name="services"></a><span data-ttu-id="3db32-135">Servicios</span><span class="sxs-lookup"><span data-stu-id="3db32-135">Services</span></span>

<span data-ttu-id="3db32-p108">En el ejemplo de diseño se muestra un sitio web de Internet Information Services (IIS) y SharePoint Web Services. SharePoint Web Services contiene un grupo de aplicaciones (grupo de aplicaciones 2) con tres servicios, perfil de usuario, búsqueda y metadatos administrados.</span><span class="sxs-lookup"><span data-stu-id="3db32-p108">The design example shows an Internet Information Services (IIS) website, SharePoint Web Services. SharePoint Web Services contains an application pool (Application Pool 2) with three services, User Profile, Search, and Managed Metadata.</span></span>
  
<span data-ttu-id="3db32-138">Notas sobre los servicios para sitios de Internet:</span><span class="sxs-lookup"><span data-stu-id="3db32-138">Notes on Services for Internet sites:</span></span>
  
> <span data-ttu-id="3db32-139">Metadatos administrados: no olvide seleccionar **Esta aplicación de servicio es la ubicación de almacenamiento predeterminada para conjuntos de términos específicos de columnas**.</span><span class="sxs-lookup"><span data-stu-id="3db32-139">Managed Metadata — Be sure to select **This service application is the default storage location for column specific term sets**.</span></span>
    
> <span data-ttu-id="3db32-140">Administración de la aplicación: le aconsejamos que no use aplicaciones en un sitio de Internet público en Azure.</span><span class="sxs-lookup"><span data-stu-id="3db32-140">App Management — We do not recommend using apps in a public-facing Internet site in Azure.</span></span>
    
## <a name="application-pools-and-web-applications"></a><span data-ttu-id="3db32-141">Grupos de aplicaciones y aplicaciones web</span><span class="sxs-lookup"><span data-stu-id="3db32-141">Application pools and web applications</span></span>

<span data-ttu-id="3db32-142">El grupo predeterminado en Azure muestra el grupo de aplicación 3, que contiene una aplicación web denominada Sitios de Contoso.</span><span class="sxs-lookup"><span data-stu-id="3db32-142">The Default Group in Azure shows Application Pool 3, which contains a web application named Contoso Sites.</span></span> <span data-ttu-id="3db32-143">Esta colección de sitios basada en rutas de acceso https://internal:8000se encuentra en.</span><span class="sxs-lookup"><span data-stu-id="3db32-143">This path-based site collection is located at https://internal:8000.</span></span>
  
## <a name="site-collections-and-sites"></a><span data-ttu-id="3db32-144">Sitios y colecciones de sitios</span><span class="sxs-lookup"><span data-stu-id="3db32-144">Site collections and sites</span></span>

<span data-ttu-id="3db32-145">Estas son algunas de las colecciones de sitios que se incluyen en el grupo de aplicaciones:</span><span class="sxs-lookup"><span data-stu-id="3db32-145">The site collections contained in the application pool include:</span></span>
  
- <span data-ttu-id="3db32-146">Colección de sitios con nombre de host 1 para el rastreo (ubicación de ejemplohttps://authoring.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="3db32-146">Host-named site collection 1 for crawling (example location https://authoring.contoso.com:8000)</span></span>
    
- <span data-ttu-id="3db32-147">Colección de sitios con nombre de host 2 para consultas ( https://www.contoso.comubicaciones https://secure.contoso.comde ejemplo,,https://www.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="3db32-147">Host-named site collection 2 for queries (sample locations https://www.contoso.com, https://secure.contoso.com, https://www.contoso.com:8000)</span></span>
    
- <span data-ttu-id="3db32-148">Colección de sitios con nombre de host 3 para consultas ( https://assets.contoso.comubicaciones https://secureassets.contoso.comde ejemplo,,https://assets.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="3db32-148">Host-named site collection 3 for queries (sample locations https://assets.contoso.com, https://secureassets.contoso.com, https://assets.contoso.com:8000)</span></span>
    
## <a name="content-databases"></a><span data-ttu-id="3db32-149">Bases de datos de contenido</span><span class="sxs-lookup"><span data-stu-id="3db32-149">Content databases</span></span>

<span data-ttu-id="3db32-150">En el ejemplo se muestran dos bases de datos de contenido.</span><span class="sxs-lookup"><span data-stu-id="3db32-150">The example shows two content databases.</span></span> <span data-ttu-id="3db32-151">Una es para la colección de sitios 1 que se usa parahttps://authoring.contoso.com:8000)el rastreo (.</span><span class="sxs-lookup"><span data-stu-id="3db32-151">One is for the site collection 1 used for crawling (https://authoring.contoso.com:8000).</span></span> <span data-ttu-id="3db32-152">La otra es para las dos colecciones de sitios 2 y 3 usadas para lashttps://www.contoso.comconsultas https://secure.contoso.com( https://www.contoso.com:8000,, https://assets.contoso.como https://secureassets.contoso.com, https://assets.contoso.com:8000),.</span><span class="sxs-lookup"><span data-stu-id="3db32-152">The other is for the two site collections 2 and 3 used for queries (https://www.contoso.com, https://secure.contoso.com, https://www.contoso.com:8000, or https://assets.contoso.com, https://secureassets.contoso.com, https://assets.contoso.com:8000).</span></span>
  
## <a name="zones-and-urls"></a><span data-ttu-id="3db32-153">Zonas y direcciones URL</span><span class="sxs-lookup"><span data-stu-id="3db32-153">Zones and URLs</span></span>

<span data-ttu-id="3db32-154">En el ejemplo se muestran tres zonas con las URL de carga equilibrada asociadas, usadas por distintas cuentas de usuario. </span><span class="sxs-lookup"><span data-stu-id="3db32-154">The example shows three zones with the associated load-balanced URLs that are used by different user accounts.</span></span> 
  
<span data-ttu-id="3db32-155">La primera lista zonas y URL está relacionada con la colección de sitios 1 y contiene esta información:</span><span class="sxs-lookup"><span data-stu-id="3db32-155">The first list of zones and URLs is related to site collection 1, and it contains the following information:</span></span>
  
- <span data-ttu-id="3db32-156">Usuarios-autores de sitios</span><span class="sxs-lookup"><span data-stu-id="3db32-156">Users - Site authors</span></span>
    
- <span data-ttu-id="3db32-157">Zona-predeterminada</span><span class="sxs-lookup"><span data-stu-id="3db32-157">Zone - Default</span></span>
    
- <span data-ttu-id="3db32-158">URL de carga equilibrada:https://authoring.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="3db32-158">Load-balanced URL - https://authoring.contoso.com:8000</span></span>
    
<span data-ttu-id="3db32-p111">La segunda lista de zonas y URL tiene tres tipos diferentes de usuarios en tres zonas diferentes. Está relacionada con la colección de sitios 2 y contiene esta información:</span><span class="sxs-lookup"><span data-stu-id="3db32-p111">The second list of zones and URLs has three different types of users in three different zones. It is related to site collection 2, and it contains the following information:</span></span>
  
<span data-ttu-id="3db32-161">Primera zona:</span><span class="sxs-lookup"><span data-stu-id="3db32-161">First zone:</span></span>
  
- <span data-ttu-id="3db32-162">Usuarios-autores de sitios</span><span class="sxs-lookup"><span data-stu-id="3db32-162">Users - Site authors</span></span>
    
- <span data-ttu-id="3db32-163">Zona-predeterminada</span><span class="sxs-lookup"><span data-stu-id="3db32-163">Zone - Default</span></span>
    
- <span data-ttu-id="3db32-164">URL de carga equilibrada:https://www.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="3db32-164">Load-balanced URL - https://www.contoso.com:8000</span></span>
    
<span data-ttu-id="3db32-165">Segunda zona:</span><span class="sxs-lookup"><span data-stu-id="3db32-165">Second zone:</span></span>
  
- <span data-ttu-id="3db32-166">Usuarios: clientes anónimos</span><span class="sxs-lookup"><span data-stu-id="3db32-166">Users - Anonymous customers</span></span>
    
- <span data-ttu-id="3db32-167">Zona: Internet</span><span class="sxs-lookup"><span data-stu-id="3db32-167">Zone - Internet</span></span>
    
- <span data-ttu-id="3db32-168">URL de carga equilibrada:https://www.contoso.com</span><span class="sxs-lookup"><span data-stu-id="3db32-168">Load-balanced URL - https://www.contoso.com</span></span>
    
<span data-ttu-id="3db32-169">Tercera zona:</span><span class="sxs-lookup"><span data-stu-id="3db32-169">Third zone:</span></span>
  
- <span data-ttu-id="3db32-170">Clientes autenticados por usuarios</span><span class="sxs-lookup"><span data-stu-id="3db32-170">Users - Authenticated customers</span></span>
    
- <span data-ttu-id="3db32-171">Zone-extranet</span><span class="sxs-lookup"><span data-stu-id="3db32-171">Zone - Extranet</span></span>
    
- <span data-ttu-id="3db32-172">URL de carga equilibrada:https://secure.contoso.com</span><span class="sxs-lookup"><span data-stu-id="3db32-172">Load-balanced URL - https://secure.contoso.com</span></span>
    
<span data-ttu-id="3db32-p112">La tercera lista de zonas y URL tiene tres tipos diferentes de usuarios en tres zonas diferentes. Está relacionada con la colección de sitios 3 y contiene esta información:</span><span class="sxs-lookup"><span data-stu-id="3db32-p112">The third list of zones and URLs has three different types of users in three different zones. It is related to site collection 3, and it contains the following information:</span></span>
  
<span data-ttu-id="3db32-175">Primera zona:</span><span class="sxs-lookup"><span data-stu-id="3db32-175">First zone:</span></span>
  
- <span data-ttu-id="3db32-176">Usuarios-autores de sitios</span><span class="sxs-lookup"><span data-stu-id="3db32-176">Users - Site authors</span></span>
    
- <span data-ttu-id="3db32-177">Zona: Internet</span><span class="sxs-lookup"><span data-stu-id="3db32-177">Zone - Internet</span></span>
    
- <span data-ttu-id="3db32-178">URL de carga equilibrada:https://assets.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="3db32-178">Load-balanced URL - https://assets.contoso.com:8000</span></span>
    
<span data-ttu-id="3db32-179">Segunda zona:</span><span class="sxs-lookup"><span data-stu-id="3db32-179">Second zone:</span></span>
  
- <span data-ttu-id="3db32-180">Usuarios: clientes anónimos</span><span class="sxs-lookup"><span data-stu-id="3db32-180">Users - Anonymous customers</span></span>
    
- <span data-ttu-id="3db32-181">Zona: Internet</span><span class="sxs-lookup"><span data-stu-id="3db32-181">Zone - Internet</span></span>
    
- <span data-ttu-id="3db32-182">URL de carga equilibrada:https://assets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="3db32-182">Load-balanced URL - https://assets.contoso.com</span></span>
    
<span data-ttu-id="3db32-183">Tercera zona:</span><span class="sxs-lookup"><span data-stu-id="3db32-183">Third zone:</span></span>
  
- <span data-ttu-id="3db32-184">Clientes autenticados por usuarios</span><span class="sxs-lookup"><span data-stu-id="3db32-184">Users - Authenticated customers</span></span>
    
- <span data-ttu-id="3db32-185">Zone-extranet</span><span class="sxs-lookup"><span data-stu-id="3db32-185">Zone - Extranet</span></span>
    
- <span data-ttu-id="3db32-186">URL de carga equilibrada:https://secureassets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="3db32-186">Load-balanced URL - https://secureassets.contoso.com</span></span>
    

