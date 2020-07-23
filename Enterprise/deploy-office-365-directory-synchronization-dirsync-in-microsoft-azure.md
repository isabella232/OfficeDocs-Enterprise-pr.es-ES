---
title: Implementar la sincronización de directorios de Microsoft 365 en Microsoft Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/05/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_Solutions
ms.assetid: b8464818-4325-4a56-b022-5af1dad2aa8b
description: 'Resumen: implemente Azure AD Connect en una máquina virtual en Azure para sincronizar las cuentas entre el directorio local y el inquilino de Azure AD de su suscripción a Microsoft 365.'
ms.openlocfilehash: bd1b973c60576002f110a909c0022b27f4595b81
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/22/2020
ms.locfileid: "45229976"
---
# <a name="deploy-microsoft-365-directory-synchronization-in-microsoft-azure"></a><span data-ttu-id="1991f-103">Implementar la sincronización de directorios de Microsoft 365 en Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="1991f-103">Deploy Microsoft 365 Directory Synchronization in Microsoft Azure</span></span>

<span data-ttu-id="1991f-104">Azure Active Directory (Azure AD) Connect (anteriormente conocido como la herramienta de sincronización de directorios, la herramienta de sincronización de directorios o la herramienta de DirSync.exe) es una aplicación que se instala en un servidor unido a un dominio para sincronizar los usuarios locales de servicios de dominio de Active Directory (AD DS) con el inquilino de Azure AD de su suscripción a Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="1991f-104">Azure Active Directory (Azure AD) Connect (formerly known as the Directory Synchronization tool, Directory Sync tool, or the DirSync.exe tool) is an application that you install on a domain-joined server to synchronize your on-premises Active Directory Domain Services (AD DS) users to the Azure AD tenant of your Microsoft 365 subscription.</span></span> <span data-ttu-id="1991f-105">Microsoft 365 usa Azure AD para su servicio de directorio.</span><span class="sxs-lookup"><span data-stu-id="1991f-105">Microsoft 365 uses Azure AD for its directory service.</span></span> <span data-ttu-id="1991f-106">Su suscripción a Microsoft 365 incluye un inquilino de Azure AD.</span><span class="sxs-lookup"><span data-stu-id="1991f-106">Your Microsoft 365 subscription includes an Azure AD tenant.</span></span> <span data-ttu-id="1991f-107">Este inquilino también se puede usar para la administración de las identidades de la organización con otras cargas de trabajo en la nube, incluidas otras aplicaciones SaaS y aplicaciones en Azure.</span><span class="sxs-lookup"><span data-stu-id="1991f-107">This tenant can also be used for management of your organization's identities with other cloud workloads, including other SaaS applications and apps in Azure.</span></span>

<span data-ttu-id="1991f-108">Puede instalar Azure AD Connect en un servidor local, pero también puede instalarlo en una máquina virtual en Azure por los motivos siguientes:</span><span class="sxs-lookup"><span data-stu-id="1991f-108">You can install Azure AD Connect on a on-premises server, but you can also install it on a virtual machine in Azure for these reasons:</span></span>
  
- <span data-ttu-id="1991f-109">Puede aprovisionar y configurar los servidores basados en la nube con mayor rapidez, y conseguir así que los servicios estén disponibles para los usuarios mucho antes.</span><span class="sxs-lookup"><span data-stu-id="1991f-109">You can provision and configure cloud-based servers faster, making the services available to your users sooner.</span></span>
- <span data-ttu-id="1991f-110">Azure ofrece mejor disponibilidad de sitios con menos esfuerzo.</span><span class="sxs-lookup"><span data-stu-id="1991f-110">Azure offers better site availability with less effort.</span></span>
- <span data-ttu-id="1991f-111">Puede reducir el número de servidores locales de su organización.</span><span class="sxs-lookup"><span data-stu-id="1991f-111">You can reduce the number of on-premises servers in your organization.</span></span>

<span data-ttu-id="1991f-p102">Esta solución requiere conectividad entre la red local y la red virtual de Azure. Para más información, vea [Conectar una red local con una red virtual de Microsoft Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span><span class="sxs-lookup"><span data-stu-id="1991f-p102">This solution requires connectivity between your on-premises network and your Azure virtual network. For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span> 
  
> [!NOTE]
> <span data-ttu-id="1991f-114">En este artículo se describe la sincronización de un único dominio en un único bosque.</span><span class="sxs-lookup"><span data-stu-id="1991f-114">This article describes synchronization of a single domain in a single forest.</span></span> <span data-ttu-id="1991f-115">Azure AD Connect sincroniza todos los dominios de AD DS de su bosque de Active Directory con Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="1991f-115">Azure AD Connect synchronizes all AD DS domains in your Active Directory forest with Microsoft 365.</span></span> <span data-ttu-id="1991f-116">Si tiene varios bosques de Active Directory para sincronizarse con Microsoft 365, consulte [la sincronización de directorios de varios bosques con escenario de inicio de sesión único](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span><span class="sxs-lookup"><span data-stu-id="1991f-116">If you have multiple Active Directory forests to synchronize with Microsoft 365, see [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span></span> 
  
## <a name="overview-of-deploying-microsoft-365-directory-synchronization-in-azure"></a><span data-ttu-id="1991f-117">Información general sobre la implementación de la sincronización de directorios de Microsoft 365 en Azure</span><span class="sxs-lookup"><span data-stu-id="1991f-117">Overview of deploying Microsoft 365 directory synchronization in Azure</span></span>

<span data-ttu-id="1991f-118">El siguiente diagrama muestra Azure AD Connect en ejecución en una máquina virtual en Azure (el servidor de sincronización de directorios) que sincroniza un bosque de AD DS local con una suscripción a Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="1991f-118">The following diagram shows Azure AD Connect running on a virtual machine in Azure (the directory sync server) that synchronizes an on-premises AD DS forest to a Microsoft 365 subscription.</span></span>
  
![Herramienta de Azure AD Connect en una máquina virtual en Azure que sincroniza las cuentas locales con el inquilino de Azure AD de una suscripción a Microsoft 365 con flujo de tráfico](media/CP-DirSyncOverview.png)
  
<span data-ttu-id="1991f-p104">En el diagrama hay dos redes conectadas por una conexión VPN de sitio a sitio o ExpressRoute. Hay una red local donde se encuentran los controladores de dominio de AD DS y una red virtual de Azure con un servidor de sincronización de directorios, que es una máquina virtual en ejecución en [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). Hay dos flujos de tráfico principal que se originan en el servidor de sincronización de directorios:</span><span class="sxs-lookup"><span data-stu-id="1991f-p104">In the diagram, there are two networks connected by a site-to-site VPN or ExpressRoute connection. There is an on-premises network where AD DS domain controllers are located, and there is an Azure virtual network with a directory sync server, which is a virtual machine running [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). There are two main traffic flows originating from the directory sync server:</span></span>
  
-  <span data-ttu-id="1991f-123">Azure AD Connect consulta un controlador de dominio en la red local para conocer los cambios de cuentas y contraseñas.</span><span class="sxs-lookup"><span data-stu-id="1991f-123">Azure AD Connect queries a domain controller on the on-premises network for changes to accounts and passwords.</span></span>
-  <span data-ttu-id="1991f-124">Azure AD Connect envía los cambios a las cuentas y las contraseñas a la instancia de Azure AD de su suscripción a Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="1991f-124">Azure AD Connect sends the changes to accounts and passwords to the Azure AD instance of your Microsoft 365 subscription.</span></span> <span data-ttu-id="1991f-125">Como el servidor de sincronización de directorios está en una parte extendida de la red local, estos cambios se envían a través del servidor proxy de la red local.</span><span class="sxs-lookup"><span data-stu-id="1991f-125">Because the directory sync server is in an extended portion of your on-premises network, these changes are sent through the on-premises network's proxy server.</span></span>
    
> [!NOTE]
> <span data-ttu-id="1991f-126">En esta solución se describe la sincronización de un único dominio de Active Directory en un único bosque de Active Directory.</span><span class="sxs-lookup"><span data-stu-id="1991f-126">This solution describes synchronization of a single Active Directory domain, in a single Active Directory forest.</span></span> <span data-ttu-id="1991f-127">Azure AD Connect sincroniza todos los dominios de Active Directory en el bosque de Active Directory con Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="1991f-127">Azure AD Connect synchronizes all Active Directory domains in your Active Directory forest with Microsoft 365.</span></span> <span data-ttu-id="1991f-128">Si tiene varios bosques de Active Directory para sincronizarse con Microsoft 365, consulte [la sincronización de directorios de varios bosques con escenario de inicio de sesión único](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span><span class="sxs-lookup"><span data-stu-id="1991f-128">If you have multiple Active Directory forests to synchronize with Microsoft 365, see [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span></span> 
  
<span data-ttu-id="1991f-129">Existen dos pasos principales cuando implementa esta solución:</span><span class="sxs-lookup"><span data-stu-id="1991f-129">There are two major steps when you deploy this solution:</span></span>
  
1. <span data-ttu-id="1991f-p107">Crear una red virtual de Azure y establecer una conexión VPN de sitio a sitio en su red local. Para obtener más información, consulte [Conectar una red local con una red virtual de Microsoft Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span><span class="sxs-lookup"><span data-stu-id="1991f-p107">Create an Azure virtual network and establish a site-to-site VPN connection to your on-premises network. For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
    
2. <span data-ttu-id="1991f-132">Instale [Azure ad Connect](https://www.microsoft.com/download/details.aspx?id=47594) en una máquina virtual unida a un dominio en Azure y, a continuación, sincronice AD DS local con Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="1991f-132">Install [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594) on a domain-joined virtual machine in Azure, and then synchronize the on-premises AD DS to Microsoft 365.</span></span> <span data-ttu-id="1991f-133">Esto conlleva lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="1991f-133">This involves:</span></span>
    
    <span data-ttu-id="1991f-134">Crear una Máquina virtual de Azure para ejecutar Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="1991f-134">Creating an Azure Virtual Machine to run Azure AD Connect.</span></span>
    
    <span data-ttu-id="1991f-135">Instalar y configurar [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594).</span><span class="sxs-lookup"><span data-stu-id="1991f-135">Installing and configuring [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594).</span></span>
    
    <span data-ttu-id="1991f-136">Para configurar Azure AD Connect se necesitan las credenciales (nombre de usuario y contraseña) de una cuenta de administrador de Azure AD y una cuenta de administrador empresarial de AD DS.</span><span class="sxs-lookup"><span data-stu-id="1991f-136">Configuring Azure AD Connect requires the credentials (user name and password) of an Azure AD administrator account and a AD DS enterprise administrator account.</span></span> <span data-ttu-id="1991f-137">Azure AD Connect se ejecuta inmediatamente y de manera continua para sincronizar el bosque de AD DS local con Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="1991f-137">Azure AD Connect runs immediately and on an ongoing basis to synchronize the on-premises AD DS forest to Microsoft 365.</span></span>
    
<span data-ttu-id="1991f-138">Antes de implementar esta solución en producción, puede seguir las instrucciones de [la configuración básica empresarial simulada](https://docs.microsoft.com/microsoft-365/enterprise/simulated-ent-base-configuration-microsoft-365-enterprise) para establecer esta configuración como una prueba de concepto, para demostraciones o para experimentación.</span><span class="sxs-lookup"><span data-stu-id="1991f-138">Before you deploy this solution in production, you can use the instructions in [The simulated enterprise base configuration](https://docs.microsoft.com/microsoft-365/enterprise/simulated-ent-base-configuration-microsoft-365-enterprise) to set this configuration up as a proof of concept, for demonstrations, or for experimentation.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="1991f-139">Cuando la configuración de Azure AD Connect se completa, no guarda las credenciales de la cuenta de administrador de organización de AD DS.</span><span class="sxs-lookup"><span data-stu-id="1991f-139">When Azure AD Connect configuration completes, it does not save the AD DS enterprise administrator account credentials.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="1991f-140">Esta solución describe cómo sincronizar un solo bosque de AD DS con Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="1991f-140">This solution describes synchronizing a single AD DS forest to Microsoft 365.</span></span> <span data-ttu-id="1991f-141">La topología descrita en este artículo solo representa una manera de implementar esta solución.</span><span class="sxs-lookup"><span data-stu-id="1991f-141">The topology discussed in this article represents only one way to implement this solution.</span></span> <span data-ttu-id="1991f-142">La topología de la organización puede variar en función de los requisitos de red y las consideraciones de seguridad únicos.</span><span class="sxs-lookup"><span data-stu-id="1991f-142">Your organization's topology might differ based on your unique network requirements and security considerations.</span></span> 
  
## <a name="plan-for-hosting-a-directory-sync-server-for-microsoft-365-in-azure"></a><span data-ttu-id="1991f-143">Planeación para hospedar un servidor de sincronización de directorios para Microsoft 365 en Azure</span><span class="sxs-lookup"><span data-stu-id="1991f-143">Plan for hosting a directory sync server for Microsoft 365 in Azure</span></span>
<span data-ttu-id="1991f-144"><a name="PlanningVirtual"> </a></span><span class="sxs-lookup"><span data-stu-id="1991f-144"><a name="PlanningVirtual"> </a></span></span>

### <a name="prerequisites"></a><span data-ttu-id="1991f-145">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="1991f-145">Prerequisites</span></span>

<span data-ttu-id="1991f-146">Antes de comenzar, revise los siguientes requisitos previos para esta solución:</span><span class="sxs-lookup"><span data-stu-id="1991f-146">Before you begin, review the following prerequisites for this solution:</span></span>
  
- <span data-ttu-id="1991f-147">Revise el contenido de planeación relacionado en [Planear la red virtual de Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#plan-your-azure-virtual-network).</span><span class="sxs-lookup"><span data-stu-id="1991f-147">Review the related planning content in [Plan your Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#plan-your-azure-virtual-network).</span></span>
    
- <span data-ttu-id="1991f-148">Asegúrese de que cumple todos los [requisitos previos](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#prerequisites) para configurar la red virtual de Azure.</span><span class="sxs-lookup"><span data-stu-id="1991f-148">Ensure that you meet all [Prerequisites](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#prerequisites) for configuring the Azure virtual network.</span></span>
    
- <span data-ttu-id="1991f-149">Tener una suscripción a Microsoft 365 que incluya la característica de integración de Active Directory.</span><span class="sxs-lookup"><span data-stu-id="1991f-149">Have a Microsoft 365 subscription that includes the Active Directory integration feature.</span></span> <span data-ttu-id="1991f-150">Para obtener información acerca de las suscripciones de Microsoft 365, vaya a la [Página de suscripción de microsoft 365](https://products.office.com/compare-all-microsoft-office-products?tab=2).</span><span class="sxs-lookup"><span data-stu-id="1991f-150">For information about Microsoft 365 subscriptions, go to the [Microsoft 365 subscription page](https://products.office.com/compare-all-microsoft-office-products?tab=2).</span></span>
    
- <span data-ttu-id="1991f-151">Aprovisione una máquina virtual de Azure que ejecute Azure AD Connect para sincronizar el bosque de AD DS local con Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="1991f-151">Provision one Azure Virtual Machine that runs Azure AD Connect to synchronize your on-premises AD DS forest with Microsoft 365.</span></span>
    
    <span data-ttu-id="1991f-152">Debe tener las credenciales (nombres y contraseñas) de la cuenta de administrador empresarial de AD DS y una cuenta de administrador de Azure AD.</span><span class="sxs-lookup"><span data-stu-id="1991f-152">You must have the credentials (names and passwords) for a AD DS enterprise administrator account and an Azure AD Administrator account.</span></span>
    
### <a name="solution-architecture-design-assumptions"></a><span data-ttu-id="1991f-153">Suposiciones de diseño de la arquitectura de la solución</span><span class="sxs-lookup"><span data-stu-id="1991f-153">Solution architecture design assumptions</span></span>

<span data-ttu-id="1991f-154">En la siguiente lista se describen las elecciones de diseño que se han tomado para esta solución.</span><span class="sxs-lookup"><span data-stu-id="1991f-154">The following list describes the design choices made for this solution.</span></span>
  
- <span data-ttu-id="1991f-p112">Esta solución usa una sola red virtual de Azure con una conexión VPN de sitio a sitio. La red virtual de Azure hospeda una sola subred que solo contiene un servidor, el servidor de sincronización de directorios que ejecuta Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="1991f-p112">This solution uses a single Azure virtual network with a site-to-site VPN connection. The Azure virtual network hosts a single subnet that has one server, the directory sync server that is running Azure AD Connect.</span></span> 
    
- <span data-ttu-id="1991f-157">En la red local, hay un controlador de dominio y servidores DNS.</span><span class="sxs-lookup"><span data-stu-id="1991f-157">On the on-premises network, a domain controller and DNS servers exist.</span></span>
    
- <span data-ttu-id="1991f-p113">Azure AD Connect realiza la sincronización de hash de contraseña, en lugar de usar el inicio de sesión único. No tiene que implementar una infraestructura de los Servicios de federación de Active Directory (AD FS). Para obtener más información sobre la sincronización de hash de contraseña y las opciones de inicio de sesión único, vea [Seleccionar el método de autenticación adecuado para una solución de identidad híbrida de Azure Active Directory](https://aka.ms/auth-options).</span><span class="sxs-lookup"><span data-stu-id="1991f-p113">Azure AD Connect performs password hash synchronization instead of single sign-on. You do not have to deploy an Active Directory Federation Services (AD FS) infrastructure. To learn more about password hash synchronization and single sign-on options, see [Choosing the right authentication method for your Azure Active Directory hybrid identity solution](https://aka.ms/auth-options).</span></span>
    
<span data-ttu-id="1991f-p114">Hay otras opciones de diseño adicionales que puede tener en cuenta cuando implementa esta solución en su entorno. Se incluyen las siguientes:</span><span class="sxs-lookup"><span data-stu-id="1991f-p114">There are additional design choices that you might consider when you deploy this solution in your environment. These include the following:</span></span>
  
- <span data-ttu-id="1991f-163">Si hay servidores DNS en una red virtual existente de Azure, determine si desea que el servidor de sincronización de directorios los use para la resolución de nombres, en lugar de usar los servidores DNS de la red local.</span><span class="sxs-lookup"><span data-stu-id="1991f-163">If there are existing DNS servers in an existing Azure virtual network, determine whether you want your directory sync server to use them for name resolution instead of DNS servers on the on-premises network.</span></span>
    
- <span data-ttu-id="1991f-p115">Si hay controladores de dominio en una red virtual existente de Azure, determine si la configuración de Sitios y servicios de Active Directory puede suponer una mejor opción. El servidor de sincronización de directorios puede consultar los controladores de dominio de la red virtual de Azure para buscar cambios en las cuentas y las contraseñas, en lugar de usar los controladores de dominio de la red local.</span><span class="sxs-lookup"><span data-stu-id="1991f-p115">If there are domain controllers in an existing Azure virtual network, determine whether configuring Active Directory Sites and Services may be a better option for you. The directory sync server can query the domain controllers in the Azure virtual network for changes in accounts and passwords instead of domain controllers on the on-premises network.</span></span>
    
## <a name="deployment-roadmap"></a><span data-ttu-id="1991f-166">Guía de implementación</span><span class="sxs-lookup"><span data-stu-id="1991f-166">Deployment roadmap</span></span>

<span data-ttu-id="1991f-167">La implementación de Azure AD Connect en una máquina virtual en Azure consta de tres fases:</span><span class="sxs-lookup"><span data-stu-id="1991f-167">Deploying Azure AD Connect on a virtual machine in Azure consists of three phases:</span></span>
  
- <span data-ttu-id="1991f-168">Fase 1: Creación y configuración de la red virtual de Azure</span><span class="sxs-lookup"><span data-stu-id="1991f-168">Phase 1: Create and configure the Azure virtual network</span></span>
    
- <span data-ttu-id="1991f-169">Fase 2: Creación y configuración de la máquina virtual de Azure</span><span class="sxs-lookup"><span data-stu-id="1991f-169">Phase 2: Create and configure the Azure virtual machine</span></span>
    
- <span data-ttu-id="1991f-170">Fase 3: Instalar y configurar Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="1991f-170">Phase 3: Install and configure Azure AD Connect</span></span>
    
<span data-ttu-id="1991f-171">Después de la implementación, también debe asignar ubicaciones y licencias para las nuevas cuentas de usuario en Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="1991f-171">After deployment, you must also assign locations and licenses for the new user accounts in Microsoft 365.</span></span>


### <a name="phase-1-create-and-configure-the-azure-virtual-network"></a><span data-ttu-id="1991f-172">Fase 1: Creación y configuración de la red virtual de Azure</span><span class="sxs-lookup"><span data-stu-id="1991f-172">Phase 1: Create and configure the Azure virtual network</span></span>

<span data-ttu-id="1991f-173">Para crear y configurar la red virtual de Azure, complete la [Fase 1: Preparar la red local](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-1-prepare-your-on-premises-network) y la [Fase 2: Crear la red virtual entre locales en Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-2-create-the-cross-premises-virtual-network-in-azure) del plan de implementación de [Conectar una red local a Microsoft Azure Virtual Network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span><span class="sxs-lookup"><span data-stu-id="1991f-173">To create and configure the Azure virtual network, complete [Phase 1: Prepare your on-premises network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-1-prepare-your-on-premises-network) and [Phase 2: Create the cross-premises virtual network in Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-2-create-the-cross-premises-virtual-network-in-azure) in the deployment roadmap of [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
  
<span data-ttu-id="1991f-174">Esta es la configuración resultante.</span><span class="sxs-lookup"><span data-stu-id="1991f-174">This is your resulting configuration.</span></span>
  
![Fase 1 del servidor de sincronización de directorios para Microsoft 365 hospedado en Azure](media/aab6a9a4-eb78-4d85-9b96-711e6de420d7.png)
  
<span data-ttu-id="1991f-176">En esta figura se muestra una red local conectada a una red virtual de Azure mediante una conexión de ExpressRoute o VPN de sitio a sitio.</span><span class="sxs-lookup"><span data-stu-id="1991f-176">This figure shows an on-premises network connected to an Azure virtual network through a site-to-site VPN or ExpressRoute connection.</span></span>
  
### <a name="phase-2-create-and-configure-the-azure-virtual-machine"></a><span data-ttu-id="1991f-177">Fase 2: Creación y configuración de la máquina virtual de Azure</span><span class="sxs-lookup"><span data-stu-id="1991f-177">Phase 2: Create and configure the Azure virtual machine</span></span>

<span data-ttu-id="1991f-p116">Cree la máquina virtual en Azure con las instrucciones [Creación de la primera máquina virtual de Windows en Azure Portal](https://go.microsoft.com/fwlink/p/?LinkId=393098). Use la configuración siguiente:</span><span class="sxs-lookup"><span data-stu-id="1991f-p116">Create the virtual machine in Azure using the instructions [Create your first Windows virtual machine in the Azure portal](https://go.microsoft.com/fwlink/p/?LinkId=393098). Use the following settings:</span></span>
  
- <span data-ttu-id="1991f-p117">En el panel **Datos básicos**, seleccione la misma suscripción, ubicación y grupo de recursos que la red virtual. Registre el nombre de usuario y la contraseña en un lugar seguro. Los necesitará posteriormente para conectarse a la máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="1991f-p117">On the **Basics** pane, select the same subscription, location, and resource group as your virtual network. Record the user name and password in a secure location. You will need these later to connect to the virtual machine.</span></span>
    
- <span data-ttu-id="1991f-183">En el panel **Elija un tamaño**, seleccione el tamaño **A2 estándar**.</span><span class="sxs-lookup"><span data-stu-id="1991f-183">On the **Choose a size** pane, choose the **A2 Standard** size.</span></span>
    
- <span data-ttu-id="1991f-p118">En la sección **Almacenamiento** del panel **Configuración**, seleccione el tipo de almacenamiento **Estándar**. En la sección **Red**, seleccione el nombre de la red virtual y la subred que van a hospedar el servidor de sincronización de directorios (no la subred de puerta de enlace). Deje todas las demás opciones con sus valores predeterminados.</span><span class="sxs-lookup"><span data-stu-id="1991f-p118">On the **Settings** pane, in the **Storage** section, select the **Standard** storage type. In the **Network** section, select the name of your virtual network and the subnet for hosting the directory sync server (not the GatewaySubnet). Leave all other settings at their default values.</span></span>
    
<span data-ttu-id="1991f-187">Compruebe que el servidor de sincronización de directorios usa DNS correctamente. Para ello, compruebe su DNS interno y asegúrese de que se ha agregado un registro de dirección (A) para la máquina virtual con su dirección IP.</span><span class="sxs-lookup"><span data-stu-id="1991f-187">Verify that your directory sync server is using DNS correctly by checking your internal DNS to make sure that an Address (A) record was added for the virtual machine with its IP address.</span></span> 
  
<span data-ttu-id="1991f-p119">Siga las instrucciones de [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon) (Conectarse a la máquina virtual e iniciar sesión) para conectarse al servidor de sincronización de directorios con una conexión a Escritorio remoto. Después de iniciar sesión, una la máquina virtual al dominio de AD DS local.</span><span class="sxs-lookup"><span data-stu-id="1991f-p119">Use the instructions in [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon) to connect to the directory sync server with a Remote Desktop Connection. After signing in, join the virtual machine to the on-premises AD DS domain.</span></span>
  
<span data-ttu-id="1991f-p120">Para que Azure AD Connect obtenga acceso a recursos de Internet, hay que configurar el servidor de sincronización de directorios de modo que use el servidor proxy de la red local. Póngase en contacto con su administrador de red para conocer los pasos de configuración adicionales que debe realizar.</span><span class="sxs-lookup"><span data-stu-id="1991f-p120">For Azure AD Connect to gain access to Internet resources, you must configure the directory sync server to use the on-premises network's proxy server. You should contact your network administrator for any additional configuration steps to perform.</span></span>
  
<span data-ttu-id="1991f-192">Esta es la configuración resultante.</span><span class="sxs-lookup"><span data-stu-id="1991f-192">This is your resulting configuration.</span></span>
  
![Fase 2 del servidor de sincronización de directorios para Microsoft 365 hospedado en Azure](media/9d8c9349-a207-4828-9b2b-826fe9c06af3.png)
  
<span data-ttu-id="1991f-194">En esta figura se muestra la máquina virtual del servidor de sincronización de directorios en la red virtual de Azure entre locales.</span><span class="sxs-lookup"><span data-stu-id="1991f-194">This figure shows the directory sync server virtual machine in the cross-premises Azure virtual network.</span></span>
  
### <a name="phase-3-install-and-configure-azure-ad-connect"></a><span data-ttu-id="1991f-195">Fase 3: Instalar y configurar Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="1991f-195">Phase 3: Install and configure Azure AD Connect</span></span>

<span data-ttu-id="1991f-196">Haga lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="1991f-196">Complete the following procedure:</span></span>
  
1. <span data-ttu-id="1991f-p121">Conéctese al servidor de sincronización de directorios mediante una conexión a Escritorio remoto con una cuenta de dominio de AD DS que tenga privilegios de administrador local. Vea [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon) (Conectarse a la máquina virtual e iniciar sesión).</span><span class="sxs-lookup"><span data-stu-id="1991f-p121">Connect to the directory sync server using a Remote Desktop Connection with an AD DS domain account that has local administrator privileges. See [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon).</span></span>
    
2. <span data-ttu-id="1991f-199">Desde el servidor de sincronización de directorios, abra el artículo [configurar la sincronización de directorios para Microsoft 365](set-up-directory-synchronization.md) y siga las instrucciones para la sincronización de directorios con la sincronización de hash de contraseña.</span><span class="sxs-lookup"><span data-stu-id="1991f-199">From the directory sync server, open the [Set up directory synchronization for Microsoft 365](set-up-directory-synchronization.md) article and follow the directions for directory synchronization with password hash synchronization.</span></span>
    
> [!CAUTION]
> <span data-ttu-id="1991f-p122">El programa de instalación crea la cuenta **AAD_xxxxxxxxxxxx** en la unidad organizativa (UO) de usuarios locales. No mueva ni quite esta cuenta porque entonces se producirá un error de sincronización.</span><span class="sxs-lookup"><span data-stu-id="1991f-p122">Setup creates the **AAD_xxxxxxxxxxxx** account in the Local Users organizational unit (OU). Do not move or remove this account or synchronization will fail.</span></span>
  
<span data-ttu-id="1991f-202">Esta es la configuración resultante.</span><span class="sxs-lookup"><span data-stu-id="1991f-202">This is your resulting configuration.</span></span>
  
![Fase 3 del servidor de sincronización de directorios para Microsoft 365 hospedado en Azure](media/3f692b62-b77c-4877-abee-83c7edffa922.png)
  
<span data-ttu-id="1991f-204">En esta figura se muestra el servidor de sincronización de directorios con Azure AD Connect en la red virtual de Azure entre locales.</span><span class="sxs-lookup"><span data-stu-id="1991f-204">This figure shows the directory sync server with Azure AD Connect in the cross-premises Azure virtual network.</span></span>
  
### <a name="assign-locations-and-licenses-to-users-in-microsoft-365"></a><span data-ttu-id="1991f-205">Asignar ubicaciones y licencias a los usuarios en Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="1991f-205">Assign locations and licenses to users in Microsoft 365</span></span>

<span data-ttu-id="1991f-206">Azure AD Connect agrega cuentas a su suscripción de Microsoft 365 desde AD DS local, pero para que los usuarios inicien sesión en Microsoft 365 y usen sus servicios, las cuentas deben configurarse con una ubicación y licencias.</span><span class="sxs-lookup"><span data-stu-id="1991f-206">Azure AD Connect adds accounts to your Microsoft 365 subscription from the on-premises AD DS, but in order for users to sign in to Microsoft 365 and use its services, the accounts must be configured with a location and licenses.</span></span> <span data-ttu-id="1991f-207">Use estos pasos para agregar la ubicación y activar las licencias para las cuentas de usuario adecuadas:</span><span class="sxs-lookup"><span data-stu-id="1991f-207">Use these steps to add the location and activate licenses for the appropriate user accounts:</span></span>
  
1. <span data-ttu-id="1991f-208">Inicie sesión en el [centro de administración de Microsoft 365](https://admin.microsoft.com)y, a continuación, haga clic en **Administrador**.</span><span class="sxs-lookup"><span data-stu-id="1991f-208">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com), and then click **Admin**.</span></span>
    
2. <span data-ttu-id="1991f-209">En el panel de navegación izquierdo, haga clic en **Usuarios > Usuarios activos**.</span><span class="sxs-lookup"><span data-stu-id="1991f-209">In the left navigation, click **Users > Active users**.</span></span>
    
3. <span data-ttu-id="1991f-210">En la lista de las cuentas de usuarios, seleccione la casilla junto al usuario que quiere activar.</span><span class="sxs-lookup"><span data-stu-id="1991f-210">In the list of user accounts, select the check box next to the user you want to activate.</span></span>
    
4. <span data-ttu-id="1991f-211">En la página del usuario, haga clic en **Editar** para **Licencias de productos**.</span><span class="sxs-lookup"><span data-stu-id="1991f-211">On the page for the user, click **Edit** for **Product licenses**.</span></span>
    
5. <span data-ttu-id="1991f-212">En la página **Licencias de productos**, seleccione una ubicación para el usuario en **Ubicación** y, después, habilite las licencias adecuadas para el usuario.</span><span class="sxs-lookup"><span data-stu-id="1991f-212">On the **Product licenses** page, select a location for the user for **Location**, and then enable the appropriate licenses for the user.</span></span>
    
6. <span data-ttu-id="1991f-213">Cuando finalice, haga clic en **Guardar** y, después, haga clic en **Cerrar** dos veces.</span><span class="sxs-lookup"><span data-stu-id="1991f-213">When complete, click **Save**, and then click **Close** twice.</span></span>
    
7. <span data-ttu-id="1991f-214">Vuelva al paso 3 para usuarios adicionales.</span><span class="sxs-lookup"><span data-stu-id="1991f-214">Go back to step 3 for additional users.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="1991f-215">Recursos adicionales</span><span class="sxs-lookup"><span data-stu-id="1991f-215">See also</span></span>

[<span data-ttu-id="1991f-216">Adopción de la nube y soluciones híbridas</span><span class="sxs-lookup"><span data-stu-id="1991f-216">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.yml)
  
[<span data-ttu-id="1991f-217">Conectar una red local con una red virtual de Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="1991f-217">Connect an on-premises network to a Microsoft Azure virtual network</span></span>](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)

[<span data-ttu-id="1991f-218">Descargar Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="1991f-218">Download Azure AD Connect</span></span>](https://www.microsoft.com/download/details.aspx?id=47594)
  
[<span data-ttu-id="1991f-219">Configurar la sincronización de directorios para Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="1991f-219">Set up directory synchronization for Microsoft 365</span></span>](set-up-directory-synchronization.md)
  
