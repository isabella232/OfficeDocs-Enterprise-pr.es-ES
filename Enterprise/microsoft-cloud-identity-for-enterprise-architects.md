---
title: Identidad de nube de Microsoft para arquitectos de empresa
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- Strat_O365_Enterprise
- Ent_Architecture
ms.assetid: d27b5085-7325-4ab9-9d9a-438908a65d2c
description: "Resumen: diseñar la solución de identidad para plataformas y servicios en la nube de Microsoft."
ms.openlocfilehash: 601d449937d0b21299f4653aa872e0a3d4bc5337
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2018
---
# <a name="microsoft-cloud-identity-for-enterprise-architects"></a><span data-ttu-id="e4674-103">Identidad de nube de Microsoft para arquitectos de empresa</span><span class="sxs-lookup"><span data-stu-id="e4674-103">Microsoft Cloud Identity for Enterprise Architects</span></span>

 <span data-ttu-id="e4674-104">**Resumen:** diseñar la solución de identidad para plataformas y servicios en la nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e4674-104">**Summary:** Design your identity solution for Microsoft cloud services and platforms.</span></span>
  
<span data-ttu-id="e4674-p101">En este artículo se describe lo que los arquitectos de TI necesitan saber sobre el diseño de la identidad para las organizaciones que usan plataformas y servicios en la nube de Microsoft. También puede ver este artículo como un póster de cinco páginas e imprimirlo en formato tabloide (también conocido como doble carta, 11 x 17 o A3).</span><span class="sxs-lookup"><span data-stu-id="e4674-p101">This article describes what IT architects need to know about designing identity for organizations using Microsoft cloud services and platforms. You can also view this article as a 5-page poster and print it in tabloid format (also known as ledger, 11 x 17, or A3).</span></span>
  
<span data-ttu-id="e4674-107">[![Imagen en miniatura del modelo de identidad de Microsoft Cloud](images/ffa145a1-97e6-4c36-b08b-01c4a4ae8b9b.png) 
](https://www.microsoft.com/download/details.aspx?id=54431)</span><span class="sxs-lookup"><span data-stu-id="e4674-107">[![Thumb image for Microsoft cloud identity model](images/ffa145a1-97e6-4c36-b08b-01c4a4ae8b9b.png) 
](https://www.microsoft.com/download/details.aspx?id=54431)</span></span>
  
<span data-ttu-id="e4674-108">![Archivo PDF](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=524586) | ![Archivo de Visio](images/ITPro_Other_VisioIcon.jpg)[Visio](https://download.microsoft.com/download/2/3/8/238228E6-9017-4F6C-BD3C-5559E6708F82/MSFT_cloud_architecture_identity.vsd) | ![Ver una página con versiones en otros idiomas](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[Más idiomas](https://www.microsoft.com/download/details.aspx?id=54431)</span><span class="sxs-lookup"><span data-stu-id="e4674-108">![PDF file](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=524586) | ![Visio file](images/ITPro_Other_VisioIcon.jpg)[Visio](https://download.microsoft.com/download/2/3/8/238228E6-9017-4F6C-BD3C-5559E6708F82/MSFT_cloud_architecture_identity.vsd) | ![See a page with versions in additional languages](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[More languages](https://www.microsoft.com/download/details.aspx?id=54431)</span></span>
  
<span data-ttu-id="e4674-109">También puede ver todos los modelos en los [Recursos de arquitectura de TI de Microsoft Cloud](microsoft-cloud-it-architecture-resources.md) y conocer el [Plan de desarrollo de la nube empresarial de Microsoft: Recursos para responsables de toma de decisiones de TI](https://aka.ms/cloudarchitecture).</span><span class="sxs-lookup"><span data-stu-id="e4674-109">You can also see all of the models in the [Microsoft Cloud IT architecture resources](microsoft-cloud-it-architecture-resources.md) and swipe through [Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers](https://aka.ms/cloudarchitecture).</span></span>
  
> [!NOTE]
> <span data-ttu-id="e4674-p102">En este artículo, se refleja la versión de enero de 2016 del póster de la **Identidad de Microsoft Cloud para arquitectos empresariales**. No contiene los cambios de la versión de abril de 2016 ni versiones posteriores del póster.</span><span class="sxs-lookup"><span data-stu-id="e4674-p102">This article reflects the January 2016 version of the **Microsoft cloud identity for enterprise architects** poster. It does not contain the changes for the April 2016 or later versions of the poster.</span></span>
  
## <a name="designing-identity-for-the-microsoft-cloud"></a><span data-ttu-id="e4674-112">Diseño de la identidad para Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="e4674-112">Designing identity for the Microsoft cloud</span></span>

<span data-ttu-id="e4674-p103">La integración de las identidades con la nube de Microsoft proporciona acceso a una amplia gama de servicios y opciones de plataforma en la nube. Existen dos opciones principales:</span><span class="sxs-lookup"><span data-stu-id="e4674-p103">Integrating your identities with the Microsoft cloud provides access to a broad range of services and cloud platform options. There are two main options:</span></span>
  
- <span data-ttu-id="e4674-p104">Puede realizar la integración con Microsoft Azure Active Directory (AD). Esto implica la sincronización de las cuentas locales con Azure AD, el proveedor de identidades para la nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e4674-p104">You can integrate with Microsoft Azure Active Directory (AD). This involves synchronizing your on-premises accounts to Azure AD, the identity provider for the Microsoft cloud.</span></span>
    
- <span data-ttu-id="e4674-117">Puede ampliar su entorno de Servicios de dominio de Active Directory (AD DS) local para las máquinas virtuales que se ejecutan en servicios de infraestructura de Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="e4674-117">You can extend your on-premises Active Directory Domain Services (AD DS) environment to virtual machines running in Microsoft Azure infrastructure services.</span></span>
    
![Opciones para diseñar sus identidades en la nube](images/08277e96-e4d2-43cb-a56f-a11c7647881a.png)
  
 <span data-ttu-id="e4674-119">**Figura 1: Opciones para diseñar las identidades en la nube**</span><span class="sxs-lookup"><span data-stu-id="e4674-119">**Figure 1: Options for designing your identities in the cloud**</span></span>
  
<span data-ttu-id="e4674-120">La figura 1 muestra que Azure AD es el proveedor de identidades de los servicios de software como servicio (SaaS) de Microsoft y de las aplicaciones de plataforma como servicio (PaaS) de Azure, y que las aplicaciones de línea de negocio pueden usar AD DS local.</span><span class="sxs-lookup"><span data-stu-id="e4674-120">Figure 1 shows how Azure AD is the identity provider for Microsoft Software as a Service (SaaS) services and Azure Platform as a Service (PaaS) applications and how line-of-business applications can use on-premises AD DS.</span></span> 
  
### <a name="azure-active-directory"></a><span data-ttu-id="e4674-121">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="e4674-121">Azure Active Directory</span></span>

<span data-ttu-id="e4674-p105">Microsoft Azure AD es el servicio de administración de acceso e identidades hospedado en la nube de Microsoft. Es el elemento central de las plataformas y los servicios en la nube de Microsoft. La integración con Azure AD proporciona acceso a todos los servicios SaaS de Microsoft usando su conjunto actual de cuentas y contraseñas. Dicha integración también proporciona una identidad basada en la nube para las aplicaciones PaaS de Azure.</span><span class="sxs-lookup"><span data-stu-id="e4674-p105">Microsoft Azure AD is the Microsoft cloud-hosted identity and access management service. It's at the center of Microsoft cloud services and platforms. Integrating with Azure AD provides access to all of the Microsoft SaaS services using your current set of accounts and passwords. That integration also provides cloud-based identity for Azure PaaS applications.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="e4674-126">Azure AD no evita tener que usar AD DS local para las organizaciones empresariales o para las máquinas virtuales basadas en Windows que se ejecutan en la infraestructura como servicio (IaaS) de Azure.</span><span class="sxs-lookup"><span data-stu-id="e4674-126">Azure AD does not replace the need for AD DS on-premises for enterprise organizations or for Windows -based virtual machines running in Azure Infrastructure as a Service (IaaS).</span></span> 
  
<span data-ttu-id="e4674-127">Hay tres ediciones de Azure AD: Gratuita, Basic y Premium.</span><span class="sxs-lookup"><span data-stu-id="e4674-127">There are three editions of Azure AD: Free, Basic, and Premium.</span></span> 
  
||||
|:-----|:-----|:-----|
|<span data-ttu-id="e4674-128">**Gratuito**</span><span class="sxs-lookup"><span data-stu-id="e4674-128">**Free**</span></span> <br/> |<span data-ttu-id="e4674-129">**Basic**</span><span class="sxs-lookup"><span data-stu-id="e4674-129">**Basic**</span></span> <br/> |<span data-ttu-id="e4674-130">**Premium**</span><span class="sxs-lookup"><span data-stu-id="e4674-130">**Premium**</span></span> <br/> |
| <span data-ttu-id="e4674-131">	Administrar cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="e4674-131">Manage user accounts</span></span> <br/>  <span data-ttu-id="e4674-132">Sincronizar con directorios locales</span><span class="sxs-lookup"><span data-stu-id="e4674-132">Synchronize with on-premises directories</span></span> <br/>  <span data-ttu-id="e4674-133">Inicio de sesión único en Azure, Office 365 y miles de aplicaciones SaaS populares, como Salesforce, Workday, Concur, DocuSign, Google Apps, Box, ServiceNow, Dropbox y muchas más</span><span class="sxs-lookup"><span data-stu-id="e4674-133">Single sign-on across Azure, Office 365, and thousands of other popular SaaS applications, such as Salesforce, Workday, Concur, DocuSign, Google Apps, Box, ServiceNow, Dropbox, and more</span></span> <br/> | <span data-ttu-id="e4674-134">Incluye todas las capacidades de la edición gratuita, así como:</span><span class="sxs-lookup"><span data-stu-id="e4674-134">Includes all of the abilities in the Free edition, plus:</span></span> <br/>  <span data-ttu-id="e4674-135">Personalización de marca de la empresa</span><span class="sxs-lookup"><span data-stu-id="e4674-135">Company branding</span></span> <br/>  <span data-ttu-id="e4674-136">Acceso a aplicaciones basadas en grupos</span><span class="sxs-lookup"><span data-stu-id="e4674-136">Group-based application access</span></span> <br/>  <span data-ttu-id="e4674-137">Restablecimiento de contraseñas de autoservicio</span><span class="sxs-lookup"><span data-stu-id="e4674-137">Self-service password reset</span></span> <br/>  <span data-ttu-id="e4674-138">SLA empresarial del 99,9 %</span><span class="sxs-lookup"><span data-stu-id="e4674-138">Enterprise SLA of 99.9%</span></span> <br/> | <span data-ttu-id="e4674-139">Incluye todas las características de las ediciones gratuita y Basic, así como:</span><span class="sxs-lookup"><span data-stu-id="e4674-139">Includes all of the features of the Free and Basic editions, plus:</span></span> <br/>  <span data-ttu-id="e4674-140">Administración de grupos de autoservicio</span><span class="sxs-lookup"><span data-stu-id="e4674-140">Self-service group management</span></span> <br/>  <span data-ttu-id="e4674-141">	Alertas e informes de seguridad avanzada</span><span class="sxs-lookup"><span data-stu-id="e4674-141">Advanced security reports and alerts</span></span> <br/>  <span data-ttu-id="e4674-142">	Autenticación multifactor</span><span class="sxs-lookup"><span data-stu-id="e4674-142">Multi-factor authentication</span></span> <br/>  <span data-ttu-id="e4674-143">Restablecimiento de contraseña con reescritura en AD DS local</span><span class="sxs-lookup"><span data-stu-id="e4674-143">Password reset with write-back to on-premises AD DS</span></span> <br/>  <span data-ttu-id="e4674-144">Sincronización bidireccional de herramientas de Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="e4674-144">Azure AD Connect tool bidirectional synchronization</span></span> <br/>  <span data-ttu-id="e4674-145">Proxy de aplicación de Azure AD</span><span class="sxs-lookup"><span data-stu-id="e4674-145">Azure AD Application Proxy</span></span> <br/>  <span data-ttu-id="e4674-146">	Microsoft Forefront Identity Manager (MIM)</span><span class="sxs-lookup"><span data-stu-id="e4674-146">Microsoft Forefront Identity Manager (MIM)</span></span> <br/> |
   
<span data-ttu-id="e4674-147">Para obtener más información sobre las versiones, consulte [Ediciones de Azure Active Directory ](https://go.microsoft.com/fwlink/p/?LinkId=524280).</span><span class="sxs-lookup"><span data-stu-id="e4674-147">For more information about versions, see [Azure Active Directory editions](https://go.microsoft.com/fwlink/p/?LinkId=524280).</span></span>
  
### <a name="option-1-integrate-with-azure-active-directory"></a><span data-ttu-id="e4674-148">Opción 1: Integración con Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="e4674-148">Option 1: Integrate with Azure Active Directory</span></span>

<span data-ttu-id="e4674-p106">La mayoría de las organizaciones sincronizan un conjunto estándar de objetos y atributos con el inquilino de Azure AD. La herramienta de Azure AD Connect sincroniza las cuentas entre AD DS local y un inquilino de Azure AD.</span><span class="sxs-lookup"><span data-stu-id="e4674-p106">Most organizations synchronize a standard set of objects and attributes to their Azure AD tenant. The Azure AD Connect tool synchronizes your accounts between on-premises AD DS and an Azure AD tenant.</span></span>
  
![Integración con Azure AD](images/3ce05e49-2cb6-4cdc-99ab-d96c5bd12fe8.png)
  
 <span data-ttu-id="e4674-152">**Figura 2: Integración con Azure AD**</span><span class="sxs-lookup"><span data-stu-id="e4674-152">**Figure 2: Integrating with Azure AD**</span></span>
  
<span data-ttu-id="e4674-p107">La figura 2 muestra la manera en que la herramienta de Azure AD Connect obtiene los cambios en AD DS y los envía al inquilino de Azure AD. En este caso, el inquilino de Azure AD es un duplicado hospedado en la nube del contenido esencial del directorio local.</span><span class="sxs-lookup"><span data-stu-id="e4674-p107">Figure 2 shows how the Azure AD Connect tool obtains AD DS changes and sends them to your Azure AD tenant. In this case, your Azure AD tenant is a cloud-hosted duplicate of essential on-premises directory content.</span></span>
  
<span data-ttu-id="e4674-p108">Muchas organizaciones usan AD DS como proveedor de identidades local. Puede usar otro tipo de proveedor de identidades local (por ejemplo, uno que use LDAP) y sincronizarlas con Azure AD.</span><span class="sxs-lookup"><span data-stu-id="e4674-p108">Many organizations use AD DS as their on-premises identity provider. You can use a different type of identity provider on-premises (such as one that uses LDAP), and synchronize these to Azure AD.</span></span>
  
### <a name="option-2-extend-ad-ds-to-azure"></a><span data-ttu-id="e4674-157">Opción 2: Ampliación de AD DS a Azure</span><span class="sxs-lookup"><span data-stu-id="e4674-157">Option 2: Extend AD DS to Azure</span></span>

<span data-ttu-id="e4674-p109">La ampliación de AD DS a máquinas virtuales que se ejecutan en servicios de infraestructura de Azure admite un conjunto de soluciones y aplicaciones diferente del que admite la sincronización con Azure AD. A continuación se indican dos:</span><span class="sxs-lookup"><span data-stu-id="e4674-p109">Extending AD DS to virtual machines running in Azure infrastructure services supports a different set of solutions and applications compared to synchronization with Azure AD. Here are two:</span></span>
  
- <span data-ttu-id="e4674-160">Admite soluciones basadas en la nube que requieren la autenticación NTLM o Kerberos, o máquinas virtuales unidas a un dominio de AD DS.</span><span class="sxs-lookup"><span data-stu-id="e4674-160">Supports cloud-based solutions that require NTLM or Kerberos authentication, or AD DS domain-joined virtual machines.</span></span>
    
- <span data-ttu-id="e4674-161">Agrega la posibilidad de integración adicional para aplicaciones y servicios en la nube a través de plataformas y servicios en la nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e4674-161">Adds additional integration potential for cloud services and applications across Microsoft cloud services and platforms.</span></span>
    
![Ampliación de AD DS a Azure](images/4675cf17-962c-4840-b1dc-bbd1d8894a27.png)
  
 <span data-ttu-id="e4674-163">**Figura 3: Ampliación de AD DS a Azure**</span><span class="sxs-lookup"><span data-stu-id="e4674-163">**Figure 3: Extending AD DS to Azure**</span></span>
  
<span data-ttu-id="e4674-p110">La figura 3 muestra un controlador de dominio de AD DS conectado a una red virtual de Azure mediante un dispositivo VPN local y una puerta de enlace de VPN de Azure. La red virtual de Azure contiene servidores para una aplicación de línea de negocio y su propio conjunto de controladores de dominio de AD DS.</span><span class="sxs-lookup"><span data-stu-id="e4674-p110">Figure 3 shows an AD DS domain controller connected to an Azure virtual network through an on-premises VPN device and an Azure VPN gateway. The Azure virtual network contains servers for a line-of-business application and its own set of AD DS domain controllers.</span></span>
  
### <a name="more-information"></a><span data-ttu-id="e4674-166">Más información</span><span class="sxs-lookup"><span data-stu-id="e4674-166">More Information</span></span>

- [<span data-ttu-id="e4674-167">Sincronizar el directorio con Office 365 es fácil</span><span class="sxs-lookup"><span data-stu-id="e4674-167">Synchronizing your directory with Office 365 is easy</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524281)
    
- [<span data-ttu-id="e4674-168">Infografía: Administración de acceso e identidades en la nube</span><span class="sxs-lookup"><span data-stu-id="e4674-168">Infographic: Cloud identity and access management</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524282)
    
- [<span data-ttu-id="e4674-169">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="e4674-169">Azure Active Directory</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524283)
    
## <a name="integrate-your-on-premises-ad-ds-accounts-with-microsoft-azure-ad"></a><span data-ttu-id="e4674-170">Integración de las cuentas de AD DS local con Microsoft Azure AD</span><span class="sxs-lookup"><span data-stu-id="e4674-170">Integrate your on-premises AD DS accounts with Microsoft Azure AD</span></span>

<span data-ttu-id="e4674-171">Al sincronizar las cuentas de AD DS local con Azure AD, los usuarios pueden usar sus cuentas de AD DS local para acceder a:</span><span class="sxs-lookup"><span data-stu-id="e4674-171">By synchronizing your on-premises AD DS accounts with Azure AD, your users can use their on-premises AD DS accounts to access:</span></span>
  
- <span data-ttu-id="e4674-172">Todos los servicios SaaS de Microsoft (Office 365, Microsoft Intune y Dynamics CRM Online)</span><span class="sxs-lookup"><span data-stu-id="e4674-172">All of the Microsoft SaaS services (Office 365, Microsoft Intune, and Dynamics CRM Online)</span></span>
    
- <span data-ttu-id="e4674-173">Las aplicaciones que se ejecutan en PaaS de Azure</span><span class="sxs-lookup"><span data-stu-id="e4674-173">Your applications running in Azure PaaS</span></span>
    
<span data-ttu-id="e4674-174">Hay dos maneras de configurar esta integración:</span><span class="sxs-lookup"><span data-stu-id="e4674-174">There are two ways to configure this integration:</span></span>
  
- <span data-ttu-id="e4674-175">Sincronización de directorio y contraseña</span><span class="sxs-lookup"><span data-stu-id="e4674-175">Directory and password synchronization</span></span>
    
- <span data-ttu-id="e4674-176">Federación e inicio de sesión único</span><span class="sxs-lookup"><span data-stu-id="e4674-176">Federation and single sign-on</span></span>
    
<span data-ttu-id="e4674-p111">Comience con la opción más sencilla que satisfaga sus necesidades. Puede alternar entre estas opciones, si es necesario.</span><span class="sxs-lookup"><span data-stu-id="e4674-p111">Start with the simplest option that meets your needs. You can switch between these options, if needed.</span></span>
  
> [!NOTE]
> <span data-ttu-id="e4674-179">No se recomienda el uso de cuentas solo en la nube (es decir, no realizar la integración con AD DS local) para organizaciones de escala empresarial.</span><span class="sxs-lookup"><span data-stu-id="e4674-179">Using cloud-only accounts (not integrating with your on-premises AD DS) is not recommended for enterprise-scale organizations.</span></span> 
  
### <a name="directory-and-password-synchronization"></a><span data-ttu-id="e4674-180">Sincronización de directorio y contraseña</span><span class="sxs-lookup"><span data-stu-id="e4674-180">Directory and password synchronization</span></span>

<span data-ttu-id="e4674-181">Esta es la opción más sencilla y solo requiere un servidor que ejecute la herramienta de Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="e4674-181">This is the simplest option and requires only a server running the Azure AD Connect tool.</span></span> 
  
![Configuración de sincronización de directorio y contraseña](images/e7dcfe8f-dab5-461e-89cc-d7a48f58dc0f.png)
  
 <span data-ttu-id="e4674-183">**Figura 4: Configuración de sincronización de directorio y contraseña**</span><span class="sxs-lookup"><span data-stu-id="e4674-183">**Figure 4: Directory and password synchronization configuration**</span></span>
  
<span data-ttu-id="e4674-p112">La figura 4 muestra un centro de datos en la nube privado o local con un controlador de dominio de AD DS. Un servidor que ejecuta la herramienta de Azure AD Connect sincroniza la lista de nombres de cuenta con Azure AD.</span><span class="sxs-lookup"><span data-stu-id="e4674-p112">Figure 4 shows an on-premises or private cloud datacenter with an AD DS domain controller. A server running the Azure AD Connect tool synchronizes the list of account names with Azure AD.</span></span>
  
<span data-ttu-id="e4674-186">Con esta opción:</span><span class="sxs-lookup"><span data-stu-id="e4674-186">With this option:</span></span>
  
- <span data-ttu-id="e4674-p113">Las cuentas de usuario se sincronizan de AD DS local (u otro proveedor de identidades) con el inquilino de Azure AD. El directorio local sigue siendo el origen de autoridad de las cuentas y todos los cambios en las cuentas se administran desde allí.</span><span class="sxs-lookup"><span data-stu-id="e4674-p113">User accounts are synchronized from your on-premises AD DS (or other identity provider) to your Azure AD tenant. The on-premises directory remains the authoritative source for accounts and you manage all account changes from there.</span></span>
    
- <span data-ttu-id="e4674-189">Azure AD lleva a cabo la autenticación de los servicios basados en SaaS de Microsoft y las aplicaciones PaaS de Azure.</span><span class="sxs-lookup"><span data-stu-id="e4674-189">Azure AD performs all authentication for Microsoft SaaS-based services and Azure PaaS applications.</span></span>
    
- <span data-ttu-id="e4674-190">También puede configurar la sincronización de varios bosques de AD DS.</span><span class="sxs-lookup"><span data-stu-id="e4674-190">You can also configure synchronization for multiple AD DS forests.</span></span>
    
<span data-ttu-id="e4674-191">Con la sincronización de contraseñas:</span><span class="sxs-lookup"><span data-stu-id="e4674-191">With password synchronization:</span></span>
  
- <span data-ttu-id="e4674-192">Se pide a los usuarios que escriban una contraseña al acceder a los servicios en la nube, que es la misma contraseña que usan para los recursos locales.</span><span class="sxs-lookup"><span data-stu-id="e4674-192">Users are prompted to enter a password when accessing cloud services, which is the same password that they use for on-premises resources.</span></span>
    
- <span data-ttu-id="e4674-p114">Las contraseñas de usuario nunca se envían como texto no cifrado a Azure AD. En su lugar, se usa un hash de la contraseña. Es criptográficamente imposible descifrar el hash de la contraseña o usar técnicas de ingeniería inversa para obtener la contraseña como texto no cifrado.</span><span class="sxs-lookup"><span data-stu-id="e4674-p114">User passwords are never sent as cleartext to Azure AD. Instead, a hash of the password is used. It is cryptographically impossible to decrypt or reverse-engineer the password hash and obtain the cleartext password.</span></span> 
    
<span data-ttu-id="e4674-196">Con la autenticación multifactor (MFA):</span><span class="sxs-lookup"><span data-stu-id="e4674-196">With multi-factor authentication (MFA):</span></span>
  
- <span data-ttu-id="e4674-197">Puede aprovechar las características básicas de MFA que se ofrecen con Office 365.</span><span class="sxs-lookup"><span data-stu-id="e4674-197">You can take advantage of basic MFA features offered with Office 365.</span></span>
    
- <span data-ttu-id="e4674-198">Los desarrolladores de aplicaciones PaaS de Azure pueden aprovechar el servicio de autenticación multifactor de Azure.</span><span class="sxs-lookup"><span data-stu-id="e4674-198">Azure PaaS application developers can take advantage of the Azure Multi-Factor Authentication service.</span></span>
    
<span data-ttu-id="e4674-199">La sincronización de directorios no proporciona integración con soluciones MFA locales.</span><span class="sxs-lookup"><span data-stu-id="e4674-199">Directory synchronization does not provide integration with on-premises MFA solutions.</span></span>
  
### <a name="federation-and-single-sign-on"></a><span data-ttu-id="e4674-200">Federación e inicio de sesión único</span><span class="sxs-lookup"><span data-stu-id="e4674-200">Federation and single sign-on</span></span>

<span data-ttu-id="e4674-201">Esta opción requiere una infraestructura y servidores adicionales.</span><span class="sxs-lookup"><span data-stu-id="e4674-201">This option requires additional servers and infrastructure.</span></span> 
  
![Servidores necesarios para la autenticación federada](images/1e54f0d2-e650-4eb5-957f-4f1d3c44da16.png)
  
 <span data-ttu-id="e4674-203">**Figura 5: Servidores necesarios para la autenticación federada**</span><span class="sxs-lookup"><span data-stu-id="e4674-203">**Figure 5: Servers needed for federated authentication**</span></span>
  
<span data-ttu-id="e4674-p115">La figura 5 muestra el conjunto de componentes para la autenticación federada. Azure AD se pone en contacto con un proxy de aplicación web, el cual reenvía la solicitud de autenticación a un servidor de Servicios de federación de Active Directory (AD FS) que, a su vez, reenvía la solicitud a un controlador de dominio de AD DS para la evaluación y la respuesta. Un servidor que ejecuta la herramienta de Azure AD Connect sincroniza la lista de nombres de cuenta de AD DS con Azure AD.</span><span class="sxs-lookup"><span data-stu-id="e4674-p115">Figure 5 shows the set of components for federated authentication. Azure AD contacts a web application proxy, which forwards the authentication request to an Active Directory Federation Services (AD FS) server, which forwards the request to an AD DS domain controller for evaluation and response. A server running the Azure AD Connect tool synchronizes the list of account names from AD DS to Azure AD.</span></span>
  
<span data-ttu-id="e4674-207">La federación ofrece las siguientes capacidades empresariales adicionales:</span><span class="sxs-lookup"><span data-stu-id="e4674-207">Federation provides these additional enterprise capabilities:</span></span>
  
- <span data-ttu-id="e4674-208">Todas las solicitudes de autenticación enviadas a Azure AD se reenvían y se llevan a cabo con el proveedor de identidades local a través de AD FS.</span><span class="sxs-lookup"><span data-stu-id="e4674-208">All authentication requests sent to Azure AD are forwarded to and performed against the on-premises identity provider through AD FS.</span></span>
    
- <span data-ttu-id="e4674-209">Funciona con proveedores de identidades que no son de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e4674-209">Works with non-Microsoft identity providers.</span></span>
    
- <span data-ttu-id="e4674-210">La sincronización del hash de contraseña puede actuar como copia de seguridad de inicio de sesión para el inicio de sesión federado (por ejemplo, si se produce un error en la autenticación federada).</span><span class="sxs-lookup"><span data-stu-id="e4674-210">Password hash synchronization can act as a sign-in backup for federated sign-in (for example, if the federated authentication fails).</span></span>
    
<span data-ttu-id="e4674-211">Use la federación si:</span><span class="sxs-lookup"><span data-stu-id="e4674-211">Use federation if:</span></span>
  
- <span data-ttu-id="e4674-p116">Se requiere el inicio de sesión único. Con el inicio de sesión único, no se les pide a los usuarios que especifiquen las credenciales (nombre de usuario o contraseña) al acceder a un servicio en la nube.</span><span class="sxs-lookup"><span data-stu-id="e4674-p116">Single sign-on is required. With single sign-on, users are not prompted to enter any credentials (user name or password), when accessing a cloud service.</span></span>
    
- <span data-ttu-id="e4674-214">Ya se ha implementado AD FS.</span><span class="sxs-lookup"><span data-stu-id="e4674-214">AD FS is already deployed.</span></span>
    
- <span data-ttu-id="e4674-215">Usa un proveedor de identidades de terceros.</span><span class="sxs-lookup"><span data-stu-id="e4674-215">You use a third-party identity provider.</span></span>
    
- <span data-ttu-id="e4674-216">Usa Forefront Identity Manager 2010 R2 (no admite la sincronización de hash de contraseña).</span><span class="sxs-lookup"><span data-stu-id="e4674-216">You use Forefront Identity Manager 2010 R2 (does not support password hash synchronization).</span></span>
    
- <span data-ttu-id="e4674-217">Tiene una tarjeta inteligente integrada local u otra solución MFA.</span><span class="sxs-lookup"><span data-stu-id="e4674-217">You have an on-premises integrated smart card or other MFA solution.</span></span>
    
- <span data-ttu-id="e4674-218">Requiere la auditoría de inicio de sesión o la deshabilitación de cuentas.</span><span class="sxs-lookup"><span data-stu-id="e4674-218">You require sign-in audit and/or disablement of accounts.</span></span>
    
- <span data-ttu-id="e4674-219">Su organización requiere restricciones en el inicio de sesión de cliente en función de la ubicación de red o las horas laborables.</span><span class="sxs-lookup"><span data-stu-id="e4674-219">Your organization requires client sign-in restrictions by network location or work hours.</span></span>
    
- <span data-ttu-id="e4674-220">Debe cumplir los Estándares federales de procesamiento de información (FIPS).</span><span class="sxs-lookup"><span data-stu-id="e4674-220">You must comply with Federal Information Processing Standards (FIPS).</span></span>
    
<span data-ttu-id="e4674-221">La autenticación federada requiere una mayor inversión en la infraestructura local.</span><span class="sxs-lookup"><span data-stu-id="e4674-221">Federated authentication requires a greater investment in infrastructure on-premises.</span></span>
  
- <span data-ttu-id="e4674-p117">Los servidores locales deben ser accesibles desde Internet a través de un firewall corporativo. Microsoft recomienda el uso de servidores proxy de aplicación web implementados en la red perimetral.</span><span class="sxs-lookup"><span data-stu-id="e4674-p117">The on-premises servers must be Internet-accessible through a corporate firewall. Microsoft recommends the use of Web Application Proxy servers deployed in your perimeter network.</span></span>
    
- <span data-ttu-id="e4674-224">Requiere hardware, licencias y operaciones para servidores de AD FS, servidores proxy de AD FS o servidores proxy de aplicación web, firewalls y equilibradores de carga.</span><span class="sxs-lookup"><span data-stu-id="e4674-224">Requires hardware, licenses, and operations for AD FS servers, AD FS proxy or Web Application Proxy servers, firewalls, and load balancers.</span></span> 
    
- <span data-ttu-id="e4674-225">La disponibilidad y el rendimiento son importantes para garantizar que los usuarios puedan acceder a Office 365 y otras aplicaciones en la nube.</span><span class="sxs-lookup"><span data-stu-id="e4674-225">Availability and performance are important to ensure users can access Office 365 and other cloud applications.</span></span>
    
### <a name="more-information"></a><span data-ttu-id="e4674-226">Más información</span><span class="sxs-lookup"><span data-stu-id="e4674-226">More Information</span></span>

- [<span data-ttu-id="e4674-227">Sincronizar el directorio con Office 365 es fácil</span><span class="sxs-lookup"><span data-stu-id="e4674-227">Synchronizing your directory with Office 365 is easy</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524281)
    
- [<span data-ttu-id="e4674-228">Preparar el aprovisionamiento de usuarios a Office 365 mediante la sincronización de directorios</span><span class="sxs-lookup"><span data-stu-id="e4674-228">Prepare to provision users through directory synchronization to Office 365</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524284)
    
- [<span data-ttu-id="e4674-229">Autenticación multifactor para Office 365</span><span class="sxs-lookup"><span data-stu-id="e4674-229">Multi-Factor Authentication for Office 365</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=392012)
    
- [<span data-ttu-id="e4674-230">Autenticación multifactor de Azure</span><span class="sxs-lookup"><span data-stu-id="e4674-230">Azure Multi-Factor Authentication</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524285)
    
- [<span data-ttu-id="e4674-231">TechEd 2014: Integración de directorios: Crear un directorio con Active Directory y Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="e4674-231">TechEd 2014: Directory Integration: Creating One Directory with Active Directory and Azure Active Directory</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524286)
    
## <a name="extend-ad-ds-to-azure"></a><span data-ttu-id="e4674-232">Ampliación de AD DS a Azure</span><span class="sxs-lookup"><span data-stu-id="e4674-232">Extend AD DS to Azure</span></span>

<span data-ttu-id="e4674-233">La ampliación de AD DS a Azure es el primer paso para admitir aplicaciones de línea de negocio que se ejecutan en máquinas virtuales en servicios de infraestructura de Azure, lo que proporciona:</span><span class="sxs-lookup"><span data-stu-id="e4674-233">Extending AD DS to Azure is the first step to support line-of-business applications running on virtual machines in Azure infrastructure services, which provides:</span></span>
  
- <span data-ttu-id="e4674-234">Compatibilidad con soluciones basadas en la nube que requieren la autenticación NTLM o Kerberos, o máquinas virtuales unidas a un dominio de AD DS.</span><span class="sxs-lookup"><span data-stu-id="e4674-234">Support for cloud-based solutions that require NTLM or Kerberos authentication, or AD DS domain-joined virtual machines.</span></span>
    
- <span data-ttu-id="e4674-235">Posibilidad de integración adicional para aplicaciones y servicios en la nube, que se pueden agregar en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="e4674-235">Additional integration potential for cloud services and applications and can be added at any time.</span></span>
    
![Ampliación de AD DS a una red virtual de Azure](images/9fe2e27d-7fc8-441a-a694-1db4b9f6d03f.png)
  
 <span data-ttu-id="e4674-237">**Figura 6: Ampliación de AD DS a una red virtual de Azure**</span><span class="sxs-lookup"><span data-stu-id="e4674-237">**Figure 6: Extending AD DS to an Azure virtual network**</span></span>
  
<span data-ttu-id="e4674-p118">La figura 6 muestra un centro de datos en la nube privado o local con AD DS conectado a una red virtual de Azure con una conexión de sitio a sitio VPN o ExpressRoute. La red virtual de Azure contiene servidores para una aplicación de línea de negocio y su propio conjunto de controladores de dominio de AD DS. Esta configuración es una implementación híbrida de AD DS local y en servicios de infraestructura de Azure. Requiere lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="e4674-p118">Figure 6 shows an on-premises or private cloud datacenter with AD DS connected to an Azure virtual network with a site-to-site VPN or ExpressRoute connection. The Azure virtual network contains servers for a line-of-business application and its own set of AD DS domain controllers. This configuration is a hybrid deployment of AD DS on-premises and in Azure infrastructure services. It requires:</span></span>
  
- <span data-ttu-id="e4674-242">Una red virtual de Azure.</span><span class="sxs-lookup"><span data-stu-id="e4674-242">An Azure virtual network.</span></span>
    
- <span data-ttu-id="e4674-243">Una conexión entre un dispositivo de red privada virtual (VPN) o enrutador local y una puerta de enlace de VPN de Azure.</span><span class="sxs-lookup"><span data-stu-id="e4674-243">A connection between an on-premises virtual private network (VPN) device or router and an Azure VPN gateway.</span></span>
    
- <span data-ttu-id="e4674-244">El uso de una parte del espacio local de direcciones IP para las máquinas virtuales de la red virtual.</span><span class="sxs-lookup"><span data-stu-id="e4674-244">Using a portion of your on-premises IP address space for the virtual machines in the virtual network.</span></span>
    
- <span data-ttu-id="e4674-245">La implementación de uno o más controladores de dominio en la red virtual designados como servidores de catálogo global (lo que reduce el tráfico de salida en la conexión VPN).</span><span class="sxs-lookup"><span data-stu-id="e4674-245">Deploying one or more domain controllers in the virtual network designated as global catalog servers (reduces egress traffic across the VPN connection).</span></span>
    
<span data-ttu-id="e4674-246">Esta arquitectura de identidad admite un conjunto de soluciones y aplicaciones diferente del que admite la sincronización con Azure AD.</span><span class="sxs-lookup"><span data-stu-id="e4674-246">This identity architecture supports a different set of solutions and applications compared to synchronization with Azure AD.</span></span>
  
### <a name="on-premises-to-azure-connection-options"></a><span data-ttu-id="e4674-247">Opciones de conexión de local a Azure</span><span class="sxs-lookup"><span data-stu-id="e4674-247">On-premises to Azure connection options</span></span>

<span data-ttu-id="e4674-248">Para conectar su red local a una red virtual de Azure, puede usar lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="e4674-248">To connect your on-premises network to an Azure virtual network, you can use:</span></span>
  
- <span data-ttu-id="e4674-249">Una conexión VPN de sitio a sitio, que puede conectar entre 1 y 10 sitios (incluidas otras redes virtuales de Azure) a una sola red virtual de Azure.</span><span class="sxs-lookup"><span data-stu-id="e4674-249">A site-to-site VPN connection, which can connect 1-10 sites (including other Azure virtual networks) to a single Azure virtual network.</span></span>
    
- <span data-ttu-id="e4674-p119">ExpressRoute, un vínculo WAN seguro y privado a Azure a través de un proveedor de servicios de red y centro de datos asociado. Las conexiones ExpressRoute pueden ofrecer una mayor confiabilidad, un mayor ancho de banda y latencias menores.</span><span class="sxs-lookup"><span data-stu-id="e4674-p119">ExpressRoute, a private, secure WAN link to Azure through a partner network and datacenter services provider. ExpressRoute connections can offer increased reliability, higher bandwidth, and lower latencies.</span></span>
    
### <a name="more-information"></a><span data-ttu-id="e4674-252">Más información</span><span class="sxs-lookup"><span data-stu-id="e4674-252">More Information</span></span>

- [<span data-ttu-id="e4674-253">Acerca de la conectividad segura entre locales de redes virtuales</span><span class="sxs-lookup"><span data-stu-id="e4674-253">Cross-premises connectivity for virtual networks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524293)
    
- [<span data-ttu-id="e4674-254">Información técnica de ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="e4674-254">ExpressRoute Technical Overview</span></span>](https://go.microsoft.com/fwlink/?LinkID=392081)
    
- [<span data-ttu-id="e4674-255">Directrices para implementar Windows Server Active Directory en máquinas virtuales de Azure</span><span class="sxs-lookup"><span data-stu-id="e4674-255">Guidelines for Deploying Windows Server Active Directory on Azure Virtual Machines</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524295)
    
## <a name="integrate-your-applications-with-cloud-identities"></a><span data-ttu-id="e4674-256">Integración de sus aplicaciones con identidades de nube</span><span class="sxs-lookup"><span data-stu-id="e4674-256">Integrate your applications with cloud identities</span></span>

<span data-ttu-id="e4674-p120">Al diseñar y desarrollar aplicaciones que se ejecutan en la nube, debe fijarse como objetivo la coherencia de la experiencia del usuario en el proceso de autenticación, incluido el conjunto de credenciales necesarias. Por ejemplo, si usa credenciales de Windows, tanto en Azure AD como en AD DS ampliado, asegúrese de que los usuarios pueden autenticarse y centrarse en sus tareas rápidamente.</span><span class="sxs-lookup"><span data-stu-id="e4674-p120">When designing and developing applications that run in the cloud, you should aim for consistency of the user experience for the authentication process, including the set of required credentials. For example, when using Windows credentials, whether against Azure AD or an extended AD DS, ensure that users can quickly authenticate and focus on their tasks.</span></span>
  
![Integración de sus aplicaciones con identidades de nube](images/1e6304b0-fa15-4f80-a3b4-7507a28808ae.png)
  
 <span data-ttu-id="e4674-260">**Figura 7: Integración de sus aplicaciones con identidades de nube**</span><span class="sxs-lookup"><span data-stu-id="e4674-260">**Figure 7: Integrate your applications with cloud identities**</span></span>
  
<span data-ttu-id="e4674-261">La figura 7 muestra tres opciones para integrar la aplicación con identidades de nube.</span><span class="sxs-lookup"><span data-stu-id="e4674-261">Figure 7 shows three options for integrating your application with cloud identities.</span></span>
  
1. <span data-ttu-id="e4674-262">Registre las aplicaciones hospedadas en la nube con Azure AD.</span><span class="sxs-lookup"><span data-stu-id="e4674-262">Register your cloud-hosted applications with Azure AD.</span></span>
    
    <span data-ttu-id="e4674-p121">Consulte el artículo de MSDN [Integración de aplicaciones con Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524303). Esto le permite usar Azure AD para autenticar el acceso a la aplicación PaaS, así como permitir que los usuarios o los administradores concedan derechos a la aplicación para que acceda a contenido en su nombre desde otros servicios en la nube, como Office 365. Encontrará más detalles y ejemplos de código en el artículo de MSDN [Escenarios de autenticación para Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524304).</span><span class="sxs-lookup"><span data-stu-id="e4674-p121">See the MSDN article [Integrating Applications with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524303). This lets you use Azure AD to authenticate access to your PaaS application, as well as allowing users or administrators to grant rights to your application to access content on their behalf from other cloud services, such as Office 365. More details and code samples can be found in the MSDN article [Authentication Scenarios for Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524304).</span></span> 
    
2. <span data-ttu-id="e4674-266">Las aplicaciones que requieren autenticación mediante programación para acceder a una aplicación protegida por AD SD, AD FS en Windows Server 2012 R2 o Azure AD pueden usar:</span><span class="sxs-lookup"><span data-stu-id="e4674-266">Applications that require programmatic authentication to gain access to an application secured by AD SD, AD FS on Windows Server 2012 R2, or Azure AD can use:</span></span>
    
  - <span data-ttu-id="e4674-267">La [API de Graph de Azure AD](https://go.microsoft.com/fwlink/p/?LinkId=524305)</span><span class="sxs-lookup"><span data-stu-id="e4674-267">The [Azure AD Graph API](https://go.microsoft.com/fwlink/p/?LinkId=524305)</span></span>
    
  - [<span data-ttu-id="e4674-268">Biblioteca de autenticación de Active Directory (ADAL)</span><span class="sxs-lookup"><span data-stu-id="e4674-268">Active Directory Authentication Library (ADAL)</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=524297)
    
    <span data-ttu-id="e4674-p122">La API de Graph de Azure AD admite OAuth y OpenID Connect. También funciona con aplicaciones PaaS.</span><span class="sxs-lookup"><span data-stu-id="e4674-p122">The Azure AD Graph API supports OAuth and OpenID Connect. It also works with PaaS applications.</span></span>
    
3. <span data-ttu-id="e4674-p123">Configure las aplicaciones locales o las aplicaciones de línea de negocio que se ejecutan en máquinas virtuales en una red virtual de Azure de modo que usen directamente la autenticación de Windows (NTLM o Kerberos). Esta es la mejor experiencia para los usuarios y requiere una configuración mínima para los desarrolladores de aplicaciones de servidor.</span><span class="sxs-lookup"><span data-stu-id="e4674-p123">Configure on-premises applications or line-of-business applications running on virtual machines in an Azure virtual network to use Windows authentication (NTLM or Kerberos) directly. This is the best experience for users and requires the least configuration for server application developers.</span></span>
    
### <a name="application-integration-example"></a><span data-ttu-id="e4674-273">Ejemplo de integración de aplicaciones</span><span class="sxs-lookup"><span data-stu-id="e4674-273">Application integration example</span></span>

<span data-ttu-id="e4674-p124">Una organización crea una aplicación ASP.NET que expone un punto de conexión REST donde otras aplicaciones pueden obtener los datos de ventas más recientes. El acceso a ese punto de conexión REST está protegido con Azure AD. Las aplicaciones deben proporcionar credenciales que puedan ser autenticadas por Azure AD antes de que la aplicación ASP.NET envíe los datos solicitados. A continuación, otros desarrolladores de la organización pueden escribir sus propias aplicaciones que usen los datos de ventas del punto de conexión REST.</span><span class="sxs-lookup"><span data-stu-id="e4674-p124">An organization builds an ASP.NET application that exposes a REST endpoint where other applications can obtain the latest sales data. Access to that REST endpoint is secured with Azure AD. Applications must provide credentials that can be authenticated by Azure AD before the ASP.NET application sends the requested data. Other developers in the organization can then write their own applications that use the sales data from the REST endpoint.</span></span>
  
<span data-ttu-id="e4674-p125">Para autenticarse en Azure AD y recuperar datos, ADAL administra el proceso de autenticación del usuario y entrega el token de acceso a la aplicación para que pueda usarse para acceder a los datos de ventas. ADAL elimina gran parte de la complejidad que conlleva la obtención y el análisis de tokens, flujos de OAuth y otros elementos. ADAL es otra solución de tecnología que está cambiando rápidamente, por lo que los desarrolladores deben buscar la versión más reciente en NuGet.</span><span class="sxs-lookup"><span data-stu-id="e4674-p125">To authenticate to Azure AD and retrieve data, ADAL manages the user authentication process and hands the access token off to the application so it can be used to gain access to the sales data. ADAL abstracts out much of the complexity of obtaining and parsing tokens, OAuth flows, and other elements. ADAL is another technology solution that is rapidly changing so developers should look for the latest version on NuGet.</span></span>
  
## <a name="deploying-directory-components-in-azure"></a><span data-ttu-id="e4674-281">Implementar componentes de directorio en Azure</span><span class="sxs-lookup"><span data-stu-id="e4674-281">Deploying directory components in Azure</span></span>

<span data-ttu-id="e4674-p126">Puede implementar componentes de directorio, como servidores para la sincronización de contraseñas o la autenticación federada, en una red virtual de Azure en lugar de un centro de datos local. Tenga en cuenta sus ventajas, especialmente si piensa ampliar AD DS en Azure.</span><span class="sxs-lookup"><span data-stu-id="e4674-p126">You can deploy directory components, such as servers for password synchronization or federated authentication, in an Azure virtual network rather than an on-premises datacenter. Consider its benefits, especially if you plan to extend AD DS into Azure.</span></span>
  
<span data-ttu-id="e4674-284">Estos son los componentes de directorio que se pueden poner en una red virtual de Azure:</span><span class="sxs-lookup"><span data-stu-id="e4674-284">Here are the directory components that can be put in an Azure virtual network:</span></span>
  
- <span data-ttu-id="e4674-285">Herramienta de Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="e4674-285">Azure AD Connect tool</span></span>
    
- <span data-ttu-id="e4674-286">Componentes de autenticación federada</span><span class="sxs-lookup"><span data-stu-id="e4674-286">Federated authentication components</span></span>
    
- <span data-ttu-id="e4674-287">Entorno de AD DS independiente</span><span class="sxs-lookup"><span data-stu-id="e4674-287">A standalone AD DS environment</span></span>
    
### <a name="ad-connect-tool"></a><span data-ttu-id="e4674-288">Herramienta de AD Connect</span><span class="sxs-lookup"><span data-stu-id="e4674-288">AD Connect tool</span></span>

<span data-ttu-id="e4674-p127">La herramienta de Azure AD Connect se puede hospedar en la nube en una red virtual de Azure. Tenga en cuenta las ventajas de implementar esta carga de trabajo en Azure:</span><span class="sxs-lookup"><span data-stu-id="e4674-p127">The Azure AD Connect tool can be hosted in the cloud on an Azure virtual network. Consider these benefits of deploying this workload to Azure:</span></span>
  
- <span data-ttu-id="e4674-291">Aprovisionamiento potencialmente más rápido y menor costo de las operaciones</span><span class="sxs-lookup"><span data-stu-id="e4674-291">Potentially faster provisioning and lower cost of operations</span></span>
    
- <span data-ttu-id="e4674-292">Mayor disponibilidad</span><span class="sxs-lookup"><span data-stu-id="e4674-292">Increased availability</span></span>
    
![La herramienta de AD Connect se ejecuta en los servicios de infraestructura de Azure](images/97593481-e06a-4e34-b8b5-cc63acb5f9f1.png)
  
 <span data-ttu-id="e4674-294">**Figura 8: La herramienta de AD Connect en ejecución en Azure**</span><span class="sxs-lookup"><span data-stu-id="e4674-294">**Figure 8: The AD Connect tool running in Azure**</span></span>
  
<span data-ttu-id="e4674-p128">La figura 8 muestra la herramienta de AD Connect en ejecución en una máquina virtual en una red virtual de Azure, que consulta un controlador de dominio de AD DS local para conocer los cambios en una cuenta y los envía a Office 365. Esta solución funciona con:</span><span class="sxs-lookup"><span data-stu-id="e4674-p128">Figure 8 shows the AD Connect tool running on a virtual machine in an Azure virtual network, which queries an on-premises AD DS domain controller for account changes and then sends those changes to Office 365. This solution works with:</span></span>
  
- <span data-ttu-id="e4674-297">Servicios de Office 365.</span><span class="sxs-lookup"><span data-stu-id="e4674-297">Office 365 services.</span></span>
    
- <span data-ttu-id="e4674-298">Aplicaciones PaaS de Azure que están disponibles a través de Internet.</span><span class="sxs-lookup"><span data-stu-id="e4674-298">Azure PaaS applications that are available over the Internet.</span></span>
    
- <span data-ttu-id="e4674-299">Aplicaciones de línea de negocio en Azure que están disponibles en entornos locales a través de la conexión ExpressRoute o VPN de sitio a sitio.</span><span class="sxs-lookup"><span data-stu-id="e4674-299">Line-of-business applications in Azure that are available from on-premises environments through the site-to-site VPN or ExpressRoute connection.</span></span>
    
<span data-ttu-id="e4674-300">Para obtener más información, consulte [Integración de las identidades locales con Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span><span class="sxs-lookup"><span data-stu-id="e4674-300">For more information, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span></span>
  
### <a name="federated-authentication-infrastructure"></a><span data-ttu-id="e4674-301">Infraestructura de autenticación federada</span><span class="sxs-lookup"><span data-stu-id="e4674-301">Federated authentication infrastructure</span></span>

<span data-ttu-id="e4674-302">Si todavía no ha implementado AD FS local, tenga en cuenta las ventajas de implementar esta carga de trabajo en Azure:</span><span class="sxs-lookup"><span data-stu-id="e4674-302">If you haven't already deployed AD FS on-premises, consider these benefits of deploying this workload to Azure:</span></span>
  
- <span data-ttu-id="e4674-303">Proporciona autonomía para la autenticación en servicios en la nube (sin dependencias locales)</span><span class="sxs-lookup"><span data-stu-id="e4674-303">Provides autonomy for authentication to cloud services (no on-premises dependencies)</span></span>
    
- <span data-ttu-id="e4674-304">Reduce los servidores y las herramientas hospedados localmente</span><span class="sxs-lookup"><span data-stu-id="e4674-304">Reduces servers and tools hosted on-premises</span></span>
    
- <span data-ttu-id="e4674-305">Usa una puerta de enlace de VPN de sitio a sitio en un clúster de conmutación por error de dos nodos para conectarse a Azure (nuevo)</span><span class="sxs-lookup"><span data-stu-id="e4674-305">Uses a site-to-site VPN gateway on a two-node failover cluster to connect to Azure (new)</span></span>
    
- <span data-ttu-id="e4674-306">Usa ACL para asegurarse de que los servidores proxy de aplicación web solo pueden comunicarse con AD FS, no con controladores de dominio u otros servidores directamente</span><span class="sxs-lookup"><span data-stu-id="e4674-306">Uses ACLs to ensure that Web Application Proxy servers can only communicate with AD FS, not domain controllers or other servers directly</span></span>
    
![Implementación de la infraestructura de autenticación federada en Azure](images/4e023dd4-b9fb-403a-a8eb-069b56d7a65e.png)
  
 <span data-ttu-id="e4674-308">**Figura 9: Implementación de la infraestructura de autenticación federada en Azure**</span><span class="sxs-lookup"><span data-stu-id="e4674-308">**Figure 9: Deploying your federated authentication infrastructure in Azure**</span></span>
  
<span data-ttu-id="e4674-p129">La figura 9 muestra un conjunto de controladores de dominio locales que replican información de AD DS con un conjunto de controladores de dominio en una red virtual de Azure. La herramienta de Azure AD Connect que se ejecuta en un servidor en la red virtual de Azure consulta los controladores de dominio locales para saber qué cambios se han producido y los envía a Azure AD. Las solicitudes de autenticación que entran en Azure AD desde servicios SaaS de Microsoft, aplicaciones PaaS de Azure y otras aplicaciones en la nube se reenvían a un equilibrador de carga externo, el cual reenvía la solicitud a un conjunto de servidores proxy de aplicación web. Los servidores proxy de aplicación web reenvían la solicitud a un equilibrador de carga interno, que reenvía la solicitud a un conjunto de servidores de AD FS. A continuación, los servidores de AD FS reenvían la solicitud a un controlador de dominio para validar las credenciales de envío.</span><span class="sxs-lookup"><span data-stu-id="e4674-p129">Figure 9 shows a set of on-premises domain controllers replicating AD DS information with a set of domain controllers in an Azure virtual network. The Azure AD Connect tool running on a server in the Azure virtual network queries the local domain controllers for changes and then sends those changes to Azure AD. Incoming authentication requests to Azure AD from Microsoft SaaS services, Azure PaaS applications, and other cloud applications are forwarded to an external load balancer, which forwards the request to a set of Web Application Proxy servers. The Web Application Proxy servers forward the request to an internal load balancer, which forwards the request to a set of AD FS servers. The AD FS servers then forward the request to a domain controller to validate the send credentials.</span></span>
  
 <span data-ttu-id="e4674-314">Esta solución funciona con:</span><span class="sxs-lookup"><span data-stu-id="e4674-314">This solution works with:</span></span>
  
- <span data-ttu-id="e4674-315">Aplicaciones que requieren Kerberos</span><span class="sxs-lookup"><span data-stu-id="e4674-315">Applications that require Kerberos</span></span>
    
- <span data-ttu-id="e4674-316">Todos los servicios SaaS de Microsoft</span><span class="sxs-lookup"><span data-stu-id="e4674-316">All of Microsoft's SaaS services</span></span>
    
- <span data-ttu-id="e4674-317">Aplicaciones de Azure accesibles desde Internet</span><span class="sxs-lookup"><span data-stu-id="e4674-317">Applications in Azure that are Internet-facing</span></span>
    
- <span data-ttu-id="e4674-318">Aplicaciones de IaaS o PaaS de Azure que requieren la autenticación con el conjunto de cuentas de AD DS de su organización</span><span class="sxs-lookup"><span data-stu-id="e4674-318">Applications in Azure IaaS or PaaS that require authentication with the set of accounts in your organization's AD DS</span></span>
    
<span data-ttu-id="e4674-319">Para obtener más información, consulte [Integración de las identidades locales con Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span><span class="sxs-lookup"><span data-stu-id="e4674-319">For more information, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span></span>
  
### <a name="standalone-ad-ds-environment-in-an-azure-virtual-network"></a><span data-ttu-id="e4674-320">Entorno de AD DS independiente en una red virtual de Azure</span><span class="sxs-lookup"><span data-stu-id="e4674-320">Standalone AD DS environment in an Azure virtual network</span></span>

<span data-ttu-id="e4674-p130">No siempre es necesario integrar una aplicación en la nube con el entorno local. Por ejemplo, un dominio de AD DS independiente en una red virtual de Azure admite aplicaciones de acceso público, como sitios de Internet.</span><span class="sxs-lookup"><span data-stu-id="e4674-p130">You don't always need to integrate a cloud application with your on-premises environment. For example, a standalone AD DS domain in an Azure virtual network supports applications that are public-facing, such as Internet sites.</span></span>
  
![Un entorno independiente de AD DS para una aplicación basada en servidor](images/98c7349f-535d-4c9b-8de4-e580f6d573d4.png)
  
 <span data-ttu-id="e4674-324">**Figura 10: Un entorno de AD DS independiente para una aplicación basada en servidor**</span><span class="sxs-lookup"><span data-stu-id="e4674-324">**Figure 10: A standalone AD DS environment for a server-based application**</span></span>
  
<span data-ttu-id="e4674-p131">La figura 10 muestra una red virtual Azure que hospeda un conjunto de servidores de AD DS, que ofrecen servicios de AD DS y DNS, con un conjunto de servidores que hospedan una aplicación. Esta solución funciona con:</span><span class="sxs-lookup"><span data-stu-id="e4674-p131">Figure 10 shows an Azure virtual network hosting a set of AD DS servers, providing both AD DS and DNS services, with a set of servers that host an application. This solution works with:</span></span>
  
- <span data-ttu-id="e4674-327">Aplicaciones y sitios web accesibles desde Internet</span><span class="sxs-lookup"><span data-stu-id="e4674-327">Internet-facing web sites and applications</span></span>
    
- <span data-ttu-id="e4674-328">Aplicaciones que requieren autenticación NTLM o Kerberos</span><span class="sxs-lookup"><span data-stu-id="e4674-328">Applications that require NTLM or Kerberos authentication</span></span>
    
- <span data-ttu-id="e4674-329">Aplicaciones que se ejecutan en servidores basados en Windows que requieren AD DS</span><span class="sxs-lookup"><span data-stu-id="e4674-329">Applications running on Windows-based servers that require AD DS</span></span>
    
<span data-ttu-id="e4674-330">Para obtener más información, consulte [Integración de las identidades locales con Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span><span class="sxs-lookup"><span data-stu-id="e4674-330">For more information, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e4674-331">Consulte también</span><span class="sxs-lookup"><span data-stu-id="e4674-331">See Also</span></span>

[<span data-ttu-id="e4674-332">Recursos de arquitectura de TI de la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="e4674-332">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

<span data-ttu-id="e4674-333">[Mapa de ruta de Enterprise Cloud de Microsoft: Recursos para los responsables de decisiones de TI](https://sway.com/FJ2xsyWtkJc2taRD)</span><span class="sxs-lookup"><span data-stu-id="e4674-333">[Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers](https://sway.com/FJ2xsyWtkJc2taRD)</span></span>



