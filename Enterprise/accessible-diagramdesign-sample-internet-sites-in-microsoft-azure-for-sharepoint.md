---
title: "Ejemplo de diseño diagrama accesible - sitios de Internet de Microsoft Azure para SharePoint 2013"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.collection: Ent_O365
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b91124bc-c7ec-4929-b77c-d6293db9f15e
description: "Este artículo es una versión de texto accesible del diagrama Ejemplo de diseño: Sitios de Internet en Microsoft Azure con SharePoint Server 2013."
ms.openlocfilehash: 0d42a96f80d47b360084557fea47c4155d106d30
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="accessible-diagram---design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a><span data-ttu-id="6a954-103">Diagrama accesible: Muestra de diseño. Sitios de Internet en Microsoft Azure para SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="6a954-103">Accessible diagram - Design sample: Internet sites in Microsoft Azure for SharePoint 2013</span></span>

<span data-ttu-id="6a954-104">**Resumen:** Este artículo es una versión de texto accesible del diagrama denominado diseño sample: sitios de Internet de Microsoft Azure para 2013 de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="6a954-104">**Summary:** This article is an accessible text version of the diagram named Design sample: Internet sites in Microsoft Azure for SharePoint 2013.</span></span>
  
<span data-ttu-id="6a954-105">Utilice este ejemplo de diseño como punto de partida para un sitio en Internet en Azure usando SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="6a954-105">Use this design example as a starting point for an Internet-facing site in Azure using SharePoint 2013.</span></span>
  
<span data-ttu-id="6a954-106">Este póster muestra un ejemplo de cómo diseñar los siguientes aspectos de 2013 de SharePoint:</span><span class="sxs-lookup"><span data-stu-id="6a954-106">This poster shows an example of how to design the following aspects of SharePoint 2013:</span></span>
  
- <span data-ttu-id="6a954-107">Usuarios</span><span class="sxs-lookup"><span data-stu-id="6a954-107">Users</span></span>
    
- <span data-ttu-id="6a954-108">Zonas y autenticación</span><span class="sxs-lookup"><span data-stu-id="6a954-108">Zones and authentication</span></span>
    
- <span data-ttu-id="6a954-109">Granja de servidores</span><span class="sxs-lookup"><span data-stu-id="6a954-109">Server farm</span></span>
    
- <span data-ttu-id="6a954-110">Sitio de administración</span><span class="sxs-lookup"><span data-stu-id="6a954-110">Administration site</span></span>
    
- <span data-ttu-id="6a954-111">Servicios</span><span class="sxs-lookup"><span data-stu-id="6a954-111">Services</span></span>
    
- <span data-ttu-id="6a954-112">Grupos de aplicaciones y aplicaciones web</span><span class="sxs-lookup"><span data-stu-id="6a954-112">Application pools and web applications</span></span>
    
- <span data-ttu-id="6a954-113">Colecciones de sitios</span><span class="sxs-lookup"><span data-stu-id="6a954-113">Site collections</span></span>
    
- <span data-ttu-id="6a954-114">Sitios</span><span class="sxs-lookup"><span data-stu-id="6a954-114">Sites</span></span>
    
- <span data-ttu-id="6a954-115">Bases de datos de contenido</span><span class="sxs-lookup"><span data-stu-id="6a954-115">Content databases</span></span>
    
- <span data-ttu-id="6a954-116">Zonas y direcciones URL</span><span class="sxs-lookup"><span data-stu-id="6a954-116">Zones and URLs</span></span>
    
## <a name="users-zones-and-authentication"></a><span data-ttu-id="6a954-117">Usuarios, zonas y autenticación</span><span class="sxs-lookup"><span data-stu-id="6a954-117">Users, zones and authentication</span></span>

<span data-ttu-id="6a954-p101">Hay cuatro tipos de cuentas de usuario en este diseño. Cada tipo de cuenta está asociado con un sitio para el acceso y con una zona que usa un tipo de autenticación específico. </span><span class="sxs-lookup"><span data-stu-id="6a954-p101">There are four types of user accounts in this design. Each type of account is associated with a site for access and with a zone that uses a specific type of authentication.</span></span> 
  
- <span data-ttu-id="6a954-120">Los clientes anónimos, los clientes anónimos tienen acceso a través de un sitio, por ejemplo, http://www.contoso.com. La zona que utilizan es la "zona Internet / anónimos", que utiliza la autenticación anónima.</span><span class="sxs-lookup"><span data-stu-id="6a954-120">Anonymous customers — Anonymous customers have access through a site such as http://www.contoso.com. The zone they use is the "Internet zone / anonymous", which uses anonymous authentication.</span></span>
    
- <span data-ttu-id="6a954-121">Autenticar clientes: los clientes autenticados tienen acceso a través de un sitio como https://secure.contoso.com. La zona que utilizan es la "zona de Extranet / SAML", que utiliza Active Directory de Azure con autenticación SAML.</span><span class="sxs-lookup"><span data-stu-id="6a954-121">Authenticated customers — Authenticated customers have access through a site such as https://secure.contoso.com. The zone they use is the "Extranet zone / SAML", which uses Azure Active Directory with SAML authentication.</span></span>
    
- <span data-ttu-id="6a954-p102">Autores y los desarrolladores del sitio, los autores de sitios y los desarrolladores tienen acceso a través de sitios como http://authoring.contoso.com:8000 o http://www.contoso.com:8000. La zona que utilizan es la "zona predeterminada Windows integrada", que utiliza los servicios de dominio de Active Directory (AD DS).</span><span class="sxs-lookup"><span data-stu-id="6a954-p102">Site authors and developers — Site authors and developers have access through sites such as http://authoring.contoso.com:8000 or http://www.contoso.com:8000. The zone they use is the "Default zone / Windows integrated", which uses Active Directory Domain Services (AD DS).</span></span>
    
- <span data-ttu-id="6a954-p103">Cuenta de rastreo de búsqueda: La cuenta de rastreo de búsqueda tiene acceso a través de sitios como http://authoring.contoso.com:8000 o http://www.contoso.com:8000. La zona que se utiliza es la "zona predeterminada Windows integrada", que usa AD DS con autenticación Windows NTLM.</span><span class="sxs-lookup"><span data-stu-id="6a954-p103">Search Crawl Account — The search crawl account has access through sites such as http://authoring.contoso.com:8000 or http://www.contoso.com:8000. The zone it uses is the "Default zone / Windows integrated", which uses AD DS with Windows NTLM authentication.</span></span>
    
## <a name="server-farm"></a><span data-ttu-id="6a954-126">Granja de servidores</span><span class="sxs-lookup"><span data-stu-id="6a954-126">Server farm</span></span>

<span data-ttu-id="6a954-p104">Los usuarios acceden a la granja de servidores a través de Azure. La granja de servidores contiene uno o varios servidores web.</span><span class="sxs-lookup"><span data-stu-id="6a954-p104">The users access the server farm through Azure. The server farm contains one or more Web servers.</span></span>
  
## <a name="administration-site"></a><span data-ttu-id="6a954-129">Sitio de administración</span><span class="sxs-lookup"><span data-stu-id="6a954-129">Administration site</span></span>

<span data-ttu-id="6a954-p105">El sitio de administración contiene varios servidores de aplicaciones, que se comunican con un grupo de aplicaciones (grupo de aplicaciones 1 en el ejemplo) que usa el sitio de Administración Central de la aplicación web. El sitio de Administración central proporciona acceso a las colecciones de sitios dentro de la organización.</span><span class="sxs-lookup"><span data-stu-id="6a954-p105">The administration site contains several application servers, which communicate with an Application Pool (Application Pool 1 in the example) that uses the web application Central Administration Site. The Central Administration Site provides access to site collections within the organization.</span></span>
  
<span data-ttu-id="6a954-132">El sitio de administración también contiene servidores de Base de datos SQL, que son servidores de base de datos con SQL Server instalado y configurado para admitir la agrupación en clústeres de SQL, la creación de reflejos o AlwaysOn (AlwaysOn solo se aplica a SQL Server 2012).</span><span class="sxs-lookup"><span data-stu-id="6a954-132">The administration site also contains SQL Database servers, which are database servers with SQL Server installed and configured to support SQL clustering, mirroring, or AlwaysOn (AlwaysOn applies to SQL Server 2012 only).</span></span>
  
## <a name="services"></a><span data-ttu-id="6a954-133">Servicios</span><span class="sxs-lookup"><span data-stu-id="6a954-133">Services</span></span>

<span data-ttu-id="6a954-p106">En el ejemplo de diseño se muestra un sitio web de Internet Information Services (IIS) y SharePoint Web Services. SharePoint Web Services contiene un grupo de aplicaciones (grupo de aplicaciones 2) con tres servicios, perfil de usuario, búsqueda y metadatos administrados.</span><span class="sxs-lookup"><span data-stu-id="6a954-p106">The design example shows an Internet Information Services (IIS) website, SharePoint Web Services. SharePoint Web Services contains an application pool (Application Pool 2) with three services, User Profile, Search, and Managed Metadata.</span></span>
  
<span data-ttu-id="6a954-136">Notas sobre los servicios para sitios de Internet:</span><span class="sxs-lookup"><span data-stu-id="6a954-136">Notes on Services for Internet sites:</span></span>
  
> <span data-ttu-id="6a954-137">Metadatos administrados, No olvide seleccionar **esta aplicación de servicio es la ubicación de almacenamiento predeterminada para conjuntos de términos específicos de la columna**.</span><span class="sxs-lookup"><span data-stu-id="6a954-137">Managed Metadata — Be sure to select **This service application is the default storage location for column specific term sets**.</span></span>
    
> <span data-ttu-id="6a954-138">Administración de la aplicación: le aconsejamos que no use aplicaciones en un sitio de Internet público en Azure.</span><span class="sxs-lookup"><span data-stu-id="6a954-138">App Management — We do not recommend using apps in a public-facing Internet site in Azure.</span></span>
    
## <a name="application-pools-and-web-applications"></a><span data-ttu-id="6a954-139">Grupos de aplicaciones y aplicaciones web</span><span class="sxs-lookup"><span data-stu-id="6a954-139">Application pools and web applications</span></span>

<span data-ttu-id="6a954-p107">El grupo predeterminado en Azure muestra el grupo de aplicación 3, que contiene una aplicación web denominada Sitios de Contoso. Esta colección de sitios basados en la ruta de acceso se encuentra en http://internal:8000.</span><span class="sxs-lookup"><span data-stu-id="6a954-p107">The Default Group in Azure shows Application Pool 3, which contains a web application named Contoso Sites. This path-based site collection is located at http://internal:8000.</span></span>
  
## <a name="site-collections-and-sites"></a><span data-ttu-id="6a954-142">Sitios y colecciones de sitios</span><span class="sxs-lookup"><span data-stu-id="6a954-142">Site collections and sites</span></span>

<span data-ttu-id="6a954-143">Estas son algunas de las colecciones de sitios que se incluyen en el grupo de aplicaciones:</span><span class="sxs-lookup"><span data-stu-id="6a954-143">The site collections contained in the application pool include:</span></span>
  
- <span data-ttu-id="6a954-144">Colección de sitios denominados host 1 para rastreo (ubicación de ejemplo http://authoring.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="6a954-144">Host-named site collection 1 for crawling (example location http://authoring.contoso.com:8000)</span></span>
    
- <span data-ttu-id="6a954-145">Colección de sitios denominados host 2 para consultas (ubicaciones de ejemplo http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="6a954-145">Host-named site collection 2 for queries (sample locations http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000)</span></span>
    
- <span data-ttu-id="6a954-146">Colección de sitios denominados host 3 para consultas (ubicaciones de ejemplo http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="6a954-146">Host-named site collection 3 for queries (sample locations http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000)</span></span>
    
## <a name="content-databases"></a><span data-ttu-id="6a954-147">Bases de datos de contenido</span><span class="sxs-lookup"><span data-stu-id="6a954-147">Content databases</span></span>

<span data-ttu-id="6a954-p108">En el ejemplo se muestran dos bases de datos de contenido. Una es para la colección de sitios 1 usada para rastreo (http://authoring.contoso.com:8000). La otra es para las dos colecciones de sitios 2 y 3 que se usan para consultas (http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000 o http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000).</span><span class="sxs-lookup"><span data-stu-id="6a954-p108">The example shows two content databases. One is for the site collection 1 used for crawling (http://authoring.contoso.com:8000). The other is for the two site collections 2 and 3 used for queries (http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000, or http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000).</span></span>
  
## <a name="zones-and-urls"></a><span data-ttu-id="6a954-151">Zonas y direcciones URL</span><span class="sxs-lookup"><span data-stu-id="6a954-151">Zones and URLs</span></span>

<span data-ttu-id="6a954-152">En el ejemplo se muestran tres zonas con las URL de carga equilibrada asociadas, usadas por distintas cuentas de usuario. </span><span class="sxs-lookup"><span data-stu-id="6a954-152">The example shows three zones with the associated load-balanced URLs that are used by different user accounts.</span></span> 
  
<span data-ttu-id="6a954-153">La primera lista zonas y URL está relacionada con la colección de sitios 1 y contiene esta información:</span><span class="sxs-lookup"><span data-stu-id="6a954-153">The first list of zones and URLs is related to site collection 1, and it contains the following information:</span></span>
  
- <span data-ttu-id="6a954-154">Usuarios: los autores de sitios</span><span class="sxs-lookup"><span data-stu-id="6a954-154">Users - Site authors</span></span>
    
- <span data-ttu-id="6a954-155">Zona - predeterminado</span><span class="sxs-lookup"><span data-stu-id="6a954-155">Zone - Default</span></span>
    
- <span data-ttu-id="6a954-156">URL de carga equilibrada - http://authoring.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="6a954-156">Load-balanced URL - http://authoring.contoso.com:8000</span></span>
    
<span data-ttu-id="6a954-p109">La segunda lista de zonas y URL tiene tres tipos diferentes de usuarios en tres zonas diferentes. Está relacionada con la colección de sitios 2 y contiene esta información:</span><span class="sxs-lookup"><span data-stu-id="6a954-p109">The second list of zones and URLs has three different types of users in three different zones. It is related to site collection 2, and it contains the following information:</span></span>
  
<span data-ttu-id="6a954-159">Primera zona:</span><span class="sxs-lookup"><span data-stu-id="6a954-159">First zone:</span></span>
  
- <span data-ttu-id="6a954-160">Usuarios: los autores de sitios</span><span class="sxs-lookup"><span data-stu-id="6a954-160">Users - Site authors</span></span>
    
- <span data-ttu-id="6a954-161">Zona - predeterminado</span><span class="sxs-lookup"><span data-stu-id="6a954-161">Zone - Default</span></span>
    
- <span data-ttu-id="6a954-162">URL de carga equilibrada - http://www.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="6a954-162">Load-balanced URL - http://www.contoso.com:8000</span></span>
    
<span data-ttu-id="6a954-163">Segunda zona:</span><span class="sxs-lookup"><span data-stu-id="6a954-163">Second zone:</span></span>
  
- <span data-ttu-id="6a954-164">Usuarios: clientes anónimos</span><span class="sxs-lookup"><span data-stu-id="6a954-164">Users - Anonymous customers</span></span>
    
- <span data-ttu-id="6a954-165">Zona - Internet</span><span class="sxs-lookup"><span data-stu-id="6a954-165">Zone - Internet</span></span>
    
- <span data-ttu-id="6a954-166">Equilibrio de carga de URL - http://www.contoso.com</span><span class="sxs-lookup"><span data-stu-id="6a954-166">Load-balanced URL - http://www.contoso.com</span></span>
    
<span data-ttu-id="6a954-167">Tercera zona:</span><span class="sxs-lookup"><span data-stu-id="6a954-167">Third zone:</span></span>
  
- <span data-ttu-id="6a954-168">Usuarios: los clientes autenticados</span><span class="sxs-lookup"><span data-stu-id="6a954-168">Users - Authenticated customers</span></span>
    
- <span data-ttu-id="6a954-169">Zona - Extranet</span><span class="sxs-lookup"><span data-stu-id="6a954-169">Zone - Extranet</span></span>
    
- <span data-ttu-id="6a954-170">Equilibrio de carga de URL - https://secure.contoso.com</span><span class="sxs-lookup"><span data-stu-id="6a954-170">Load-balanced URL - https://secure.contoso.com</span></span>
    
<span data-ttu-id="6a954-p110">La tercera lista de zonas y URL tiene tres tipos diferentes de usuarios en tres zonas diferentes. Está relacionada con la colección de sitios 3 y contiene esta información:</span><span class="sxs-lookup"><span data-stu-id="6a954-p110">The third list of zones and URLs has three different types of users in three different zones. It is related to site collection 3, and it contains the following information:</span></span>
  
<span data-ttu-id="6a954-173">Primera zona:</span><span class="sxs-lookup"><span data-stu-id="6a954-173">First zone:</span></span>
  
- <span data-ttu-id="6a954-174">Usuarios: los autores de sitios</span><span class="sxs-lookup"><span data-stu-id="6a954-174">Users - Site authors</span></span>
    
- <span data-ttu-id="6a954-175">Zona - Internet</span><span class="sxs-lookup"><span data-stu-id="6a954-175">Zone - Internet</span></span>
    
- <span data-ttu-id="6a954-176">URL de carga equilibrada - http://assets.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="6a954-176">Load-balanced URL - http://assets.contoso.com:8000</span></span>
    
<span data-ttu-id="6a954-177">Segunda zona:</span><span class="sxs-lookup"><span data-stu-id="6a954-177">Second zone:</span></span>
  
- <span data-ttu-id="6a954-178">Usuarios: clientes anónimos</span><span class="sxs-lookup"><span data-stu-id="6a954-178">Users - Anonymous customers</span></span>
    
- <span data-ttu-id="6a954-179">Zona - Internet</span><span class="sxs-lookup"><span data-stu-id="6a954-179">Zone - Internet</span></span>
    
- <span data-ttu-id="6a954-180">Equilibrio de carga de URL - http://assets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="6a954-180">Load-balanced URL - http://assets.contoso.com</span></span>
    
<span data-ttu-id="6a954-181">Tercera zona:</span><span class="sxs-lookup"><span data-stu-id="6a954-181">Third zone:</span></span>
  
- <span data-ttu-id="6a954-182">Usuarios: los clientes autenticados</span><span class="sxs-lookup"><span data-stu-id="6a954-182">Users - Authenticated customers</span></span>
    
- <span data-ttu-id="6a954-183">Zona - Extranet</span><span class="sxs-lookup"><span data-stu-id="6a954-183">Zone - Extranet</span></span>
    
- <span data-ttu-id="6a954-184">Equilibrio de carga de URL - http://secureassets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="6a954-184">Load-balanced URL - http://secureassets.contoso.com</span></span>
    

