---
title: "Guías del laboratorio de pruebas de adopción de la nube (TLG)"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Hybrid
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
- Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: "Resumen: Utilice estas guías de laboratorio de prueba (TLGs) de adopción de nube para configurar demostración, prueba de concepto o entornos de prueba/desarrollo para Office 365, movilidad en la empresa + seguridad (EMS), Dynamics 365 y productos de servidor de Office."
ms.openlocfilehash: 532215a08e28a9d67cd19ef60d60419b06df4957
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2017
---
# <a name="cloud-adoption-test-lab-guides-tlgs"></a><span data-ttu-id="afe33-103">Guías del laboratorio de pruebas de adopción de la nube (TLG)</span><span class="sxs-lookup"><span data-stu-id="afe33-103">Cloud adoption Test Lab Guides (TLGs)</span></span>

 <span data-ttu-id="afe33-104">**Resumen:** Utilice estas guías de laboratorio de prueba (TLGs) de adopción de nube para configurar demostración, prueba de concepto o entornos de prueba/desarrollo para Office 365, movilidad en la empresa + seguridad (EMS), Dynamics 365 y productos de servidor de Office.</span><span class="sxs-lookup"><span data-stu-id="afe33-104">**Summary:** Use these cloud adoption Test Lab Guides (TLGs) to set up demonstration, proof of concept, or dev/test environments for Office 365, Enterprise Mobility + Security (EMS), Dynamics 365, and Office Server products.</span></span>
  
<span data-ttu-id="afe33-p101">TLGs ayudará a conocer rápidamente los productos de Microsoft. Son muy importantes para situaciones donde es necesario evaluar una configuración o tecnología antes de decidir si es adecuado para usted o antes de distribuirlo por los usuarios. La experiencia práctica "compilarlo a mí y funciona" le ayuda a comprender los requisitos de implementación de un nuevo producto o una solución para que pueda prever mejor para alojarlo en producción.</span><span class="sxs-lookup"><span data-stu-id="afe33-p101">TLGs help you quickly learn about Microsoft products. They're great for situations where you need to evaluate a technology or configuration before you decide whether it's right for you or before you roll it out to users. The "I built it out myself and it works" hands-on experience helps you understand the deployment requirements of a new product or solution so you can better plan for hosting it in production.</span></span>
  
<span data-ttu-id="afe33-108">Las guías del laboratorio de pruebas también crean entornos representativos para desarrollo y pruebas de aplicaciones, también conocidos como entornos de desarrollo y pruebas.</span><span class="sxs-lookup"><span data-stu-id="afe33-108">TLGs also create representative environments for development and testing of applications, also known as dev/test environments.</span></span>
  
![Guías de laboratorio de prueba en Microsoft Cloud](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
<span data-ttu-id="afe33-110">Antes de adentrarnos, consulte estos recursos adicionales:</span><span class="sxs-lookup"><span data-stu-id="afe33-110">See these additional resources before diving in:</span></span>
  
- <span data-ttu-id="afe33-111">Ver la sesión de [experiencia con las guías de laboratorio de prueba de adopción de nube en la nube de Microsoft](https://mva.microsoft.com/en-US/training-courses/experience-the-microsoft-cloud-with-cloud-adoption-test-lab-guides-17960?l=LXNRdhSLE_1000115881 ) Microsoft Virtual Academy (sólo 22 minutos).</span><span class="sxs-lookup"><span data-stu-id="afe33-111">View the [Experience the Microsoft Cloud with Cloud Adoption Test Lab Guides](https://mva.microsoft.com/en-US/training-courses/experience-the-microsoft-cloud-with-cloud-adoption-test-lab-guides-17960?l=LXNRdhSLE_1000115881 ) Microsoft Virtual Academy session (only 22 minutes).</span></span>
    
- <span data-ttu-id="afe33-112">Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual para todos los artículos de la pila de una guía de laboratorio de prueba de nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="afe33-112">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
    
## <a name="office-365-devtest-environment"></a><span data-ttu-id="afe33-113">Entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="afe33-113">Office 365 dev/test environment</span></span>
<span data-ttu-id="afe33-114"><a name="O365"> </a></span><span class="sxs-lookup"><span data-stu-id="afe33-114"></span></span>

<span data-ttu-id="afe33-115">Use estos artículos para crear su entorno de desarrollo y pruebas de Office 365:</span><span class="sxs-lookup"><span data-stu-id="afe33-115">Use these articles to build your Office 365 dev/test environment:</span></span>
  
- [<span data-ttu-id="afe33-116">Entorno de desarrollo y pruebas de la configuración básica</span><span class="sxs-lookup"><span data-stu-id="afe33-116">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
    
    <span data-ttu-id="afe33-p102">Cree una intranet simplificada que se ejecute en los servicios de infraestructura de Azure. Este paso es opcional si quiere crear una configuración de empresa simulada.</span><span class="sxs-lookup"><span data-stu-id="afe33-p102">Create a simplified intranet running in Microsoft Azure infrastructure services. This is an optional step if you want to build a simulated enterprise configuration.</span></span>
    
- [<span data-ttu-id="afe33-119">Entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="afe33-119">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
    
    <span data-ttu-id="afe33-120">Crear una suscripción de prueba Office 365 Enterprise E5, lo que puede hacer desde el equipo o desde una intranet simplificada que se ejecutan en servicios de infraestructura de Azure.</span><span class="sxs-lookup"><span data-stu-id="afe33-120">Create an Office 365 Enterprise E5 trial subscription, which you can do from your computer or from a simplified intranet running in Azure infrastructure services.</span></span>
    
- [<span data-ttu-id="afe33-121">Sincronización de directorios (DirSync) para el entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="afe33-121">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="afe33-p103">Instale y configure Azure AD Connect para la sincronización de directorios con sincronización de contraseñas. Este paso es opcional si quiere crear una configuración de empresa simulada.</span><span class="sxs-lookup"><span data-stu-id="afe33-p103">Install and configure Azure AD Connect for directory synchronization with password synchronization. This is an optional step if you want to build a simulated enterprise configuration.</span></span>
    
<span data-ttu-id="afe33-124">Para el entorno de desarrollo y prueba de Office 365, utilice estos artículos para demostrar las funciones de empresa de Office 365:</span><span class="sxs-lookup"><span data-stu-id="afe33-124">For your Office 365 dev/test environment, use these articles to demonstrate enterprise features of Office 365:</span></span>
  
- [<span data-ttu-id="afe33-125">Autenticación con varios factores para el entorno de desarrollo y prueba de Office 365</span><span class="sxs-lookup"><span data-stu-id="afe33-125">Multi-factor authentication for your Office 365 dev/test environment</span></span>](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="afe33-126">Configure y pruebe autenticación secundaria con un mensaje de texto enviado a su smartphone para una cuenta en su suscripción de Office 365.</span><span class="sxs-lookup"><span data-stu-id="afe33-126">Configure and test secondary authentication using a text message sent to your smart phone for an account in your Office 365 subscription.</span></span>
    
- [<span data-ttu-id="afe33-127">Identidad federada para el entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="afe33-127">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="afe33-128">Configure y demuestre autenticación federada con las cuentas de un dominio Active Directory de Windows Server.</span><span class="sxs-lookup"><span data-stu-id="afe33-128">Configure and demonstrate federated authentication with the accounts of a Windows Server Active Directory domain.</span></span>
    
- [<span data-ttu-id="afe33-129">Seguridad de la aplicación de nube para su entorno de pruebas y desarrollo de Office 365</span><span class="sxs-lookup"><span data-stu-id="afe33-129">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="afe33-130">Configurar y demostrar la seguridad App de Office 365 Cloud, que permite crear directivas que supervisión y le informan de actividades sospechosas en su suscripción de Office 365.</span><span class="sxs-lookup"><span data-stu-id="afe33-130">Configure and demonstrate Office 365 Cloud App Security, which allows you to create policies that monitor for and inform you of suspicious activities in your Office 365 subscription.</span></span>
    
- [<span data-ttu-id="afe33-131">Una protección avanzada para su entorno de pruebas y desarrollo de Office 365</span><span class="sxs-lookup"><span data-stu-id="afe33-131">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="afe33-132">Configure y pruebe la Protección contra amenazas avanzada, que es una característica de Exchange Online Protection (EOP) que le ayuda a evitar el malware en el correo electrónico.</span><span class="sxs-lookup"><span data-stu-id="afe33-132">Configure and demonstrate Advanced Threat Protection, which is a feature of Exchange Online Protection (EOP) that helps keep malware out of your email.</span></span>
    
- [<span data-ttu-id="afe33-133">EDiscovery avanzada para su entorno de pruebas y desarrollo de Office 365</span><span class="sxs-lookup"><span data-stu-id="afe33-133">Advanced eDiscovery for your Office 365 dev/test environment</span></span>](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="afe33-134">Agregue datos de ejemplo y pruebe eDiscovery avanzado, que permite buscar y analizar rápidamente los datos que se almacenan en Office 365, como el correo electrónico y los documentos.</span><span class="sxs-lookup"><span data-stu-id="afe33-134">Add example data and demonstrate Advanced eDiscovery, which allows you to quickly find and analyze the data that is stored in Office 365, including email and documents.</span></span>
    
- [<span data-ttu-id="afe33-135">Protección de archivos confidenciales en el entorno de desarrollo y prueba de Office 365</span><span class="sxs-lookup"><span data-stu-id="afe33-135">Sensitive file protection in the Office 365 dev/test environment</span></span>](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
    <span data-ttu-id="afe33-136">Pruebe el uso de Office 365 Information Rights Management para proteger los datos en documentos confidenciales, incluso cuando se han publicado accidentalmente en las carpetas de documentos incorrectas.</span><span class="sxs-lookup"><span data-stu-id="afe33-136">Demonstrate how you can use Office 365 Information Rights Management to protect the data in sensitive documents, even when they are accidentally posted in the wrong document folders.</span></span>
    
- [<span data-ttu-id="afe33-137">Clasificación de datos y el etiquetado en el entorno de desarrollo y prueba de Office 365</span><span class="sxs-lookup"><span data-stu-id="afe33-137">Data classification and labeling in the Office 365 dev/test environment</span></span>](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
    <span data-ttu-id="afe33-138">Demuestre cómo el cliente de protección de información de Azure (AIP) puede utilizarse para clasificar documentos con varios niveles de seguridad.</span><span class="sxs-lookup"><span data-stu-id="afe33-138">Demonstrate how the Azure Information Protection (AIP) client can be used to classify documents with various levels of security.</span></span>
    
- [<span data-ttu-id="afe33-139">Entorno de pruebas y desarrollo de SharePoint Online team sitio aislado</span><span class="sxs-lookup"><span data-stu-id="afe33-139">Isolated SharePoint Online team site dev/test environment</span></span>](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
    <span data-ttu-id="afe33-140">Demuestre cómo crear un sitio de grupo SharePoint Online que está aislado del resto de la organización de recursos altamente confidencial.</span><span class="sxs-lookup"><span data-stu-id="afe33-140">Demonstrate how to create a SharePoint Online team site that is isolated from the rest of the organization for sensitive or highly confidential resources.</span></span>
    
## <a name="the-microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="afe33-141">El entorno de pruebas y desarrollo empresarial de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="afe33-141">The Microsoft 365 Enterprise dev/test environment</span></span>
<span data-ttu-id="afe33-142"><a name="O365"> </a></span><span class="sxs-lookup"><span data-stu-id="afe33-142"></span></span>

<span data-ttu-id="afe33-143">Crear un entorno de prueba/desarrollo para escenarios de [Empresa de Microsoft 365](https://docs.microsoft.com/microsoft-365-enterprise/) con estos artículos:</span><span class="sxs-lookup"><span data-stu-id="afe33-143">Create a dev/test environment for [Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365-enterprise/) scenarios with these articles:</span></span>
  
- [<span data-ttu-id="afe33-144">El entorno de pruebas y desarrollo empresarial de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="afe33-144">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
    
    <span data-ttu-id="afe33-145">Crear el entorno inicial que incluye Office 365 E5, E5 EMS y un equipo que ejecuta Windows 10 Enterprise.</span><span class="sxs-lookup"><span data-stu-id="afe33-145">Create the initial environment that includes Office 365 E5, EMS E5, and a computer running Windows 10 Enterprise.</span></span>
    
- [<span data-ttu-id="afe33-146">Directivas MAM para su entorno de pruebas y desarrollo empresarial de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="afe33-146">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
    
    <span data-ttu-id="afe33-147">Cree grupos de usuarios y directivas de administración de aplicaciones móviles (MAM) para dispositivos iOS y Android.</span><span class="sxs-lookup"><span data-stu-id="afe33-147">Create user groups and mobile application management (MAM) policies for ioS and Android devices.</span></span>
    
- [<span data-ttu-id="afe33-148">Inscribir a dispositivos iOS y Android en su entorno de pruebas y desarrollo de Microsoft Enterprise 365</span><span class="sxs-lookup"><span data-stu-id="afe33-148">Enroll iOS and Android devices in your Microsoft Enterprise 365 dev/test environment</span></span>](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
    
    <span data-ttu-id="afe33-149">Inscriba dispositivos Android o iOS y adminístrelos de forma remota.</span><span class="sxs-lookup"><span data-stu-id="afe33-149">Enroll iOS or Android devices and manage them remotely.</span></span>
    
## <a name="office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="afe33-150">Entorno de desarrollo y pruebas de Office 365 y Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="afe33-150">Office 365 and Dynamics 365 dev/test environment</span></span>
<span data-ttu-id="afe33-151"><a name="O365_D365"> </a></span><span class="sxs-lookup"><span data-stu-id="afe33-151"></span></span>

<span data-ttu-id="afe33-152">Agregue una suscripción de prueba a Dynamics 365 y pruebe las características y los escenarios integrados de Office 365 y Dynamics 365 con estos artículos:</span><span class="sxs-lookup"><span data-stu-id="afe33-152">Add a Dynamics 365 trial subscription and test Office 365 and Dynamics 365 integrated features and scenarios with these articles:</span></span>
  
- [<span data-ttu-id="afe33-153">Entorno de desarrollo y pruebas de Office 365 y Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="afe33-153">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
    
    <span data-ttu-id="afe33-154">Agregue una suscripción de prueba a Dynamics 365, así como licencias y permisos de Dynamics 365 a sus cuentas de usuario.</span><span class="sxs-lookup"><span data-stu-id="afe33-154">Add a Dynamics 365 trial subscription and Dynamics 365 licences and permissions to your user accounts.</span></span>
    
- [<span data-ttu-id="afe33-155">Integración de Exchange Online para Office 365 y Dynamics 365 dev/entorno de prueba</span><span class="sxs-lookup"><span data-stu-id="afe33-155">Exchange Online integration for your Office 365 and Dynamics 365 dev/test environment</span></span>](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md)
    
    <span data-ttu-id="afe33-156">Configurar y, a continuación, demuestre cómo Office 365 Dynamics 365 funcionan juntos y buzones de Exchange en línea.</span><span class="sxs-lookup"><span data-stu-id="afe33-156">Configure and then demonstrate how Office 365 and Dynamics 365 work together in Exchange Online mailboxes.</span></span>
    
## <a name="the-one-microsoft-cloud-devtest-environment"></a><span data-ttu-id="afe33-157">El entorno de desarrollo y prueba de una nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="afe33-157">The One Microsoft Cloud dev/test environment</span></span>
<span data-ttu-id="afe33-158"><a name="O365_D365"> </a></span><span class="sxs-lookup"><span data-stu-id="afe33-158"></span></span>

<span data-ttu-id="afe33-p104">Crear un entorno de pruebas y desarrollo que incluye todas las ofertas de nube de Microsoft: Office 365, Azure, EMS y Dynamics 365. Para ver las instrucciones paso a paso, vea [la nube de Microsoft de un entorno de pruebas y desarrollo](the-one-microsoft-cloud-dev-test-environment.md) .</span><span class="sxs-lookup"><span data-stu-id="afe33-p104">Create a dev/test environment that includes all of Microsoft's cloud offerings: Office 365, Azure, EMS, and Dynamics 365. See [The One Microsoft Cloud dev/test environment](the-one-microsoft-cloud-dev-test-environment.md) for the step-by-step instructions.</span></span>
  
## <a name="simulated-cross-premises-devtest-environments"></a><span data-ttu-id="afe33-161">Entornos de pruebas y desarrollo simulado de varias ubicaciones</span><span class="sxs-lookup"><span data-stu-id="afe33-161">Simulated cross-premises dev/test environments</span></span>
<span data-ttu-id="afe33-162"><a name="O365_D365"> </a></span><span class="sxs-lookup"><span data-stu-id="afe33-162"></span></span>

<span data-ttu-id="afe33-163">Puede crear un entorno de pruebas y desarrollo simulado de varias ubicaciones que incluya una red virtual Azure y una red local simulada con estos artículos:</span><span class="sxs-lookup"><span data-stu-id="afe33-163">You can create a cross-premises dev/test environment, which includes an Azure virtual network and a simulated on-premises network, with these articles:</span></span>
  
- [<span data-ttu-id="afe33-164">Red virtual de local entre simulado en Azure</span><span class="sxs-lookup"><span data-stu-id="afe33-164">Simulated cross-premises virtual network in Azure</span></span>](simulated-cross-premises-virtual-network-in-azure.md)
    
    <span data-ttu-id="afe33-165">Cree una intranet simulada conectada a una red virtual de Azure en una configuración de la nube híbrida.</span><span class="sxs-lookup"><span data-stu-id="afe33-165">Create a simulated intranet connected to an Azure virtual network in a hybrid cloud configuration.</span></span>
    
- [<span data-ttu-id="afe33-166">SharePoint Server 2016 de intranet en el entorno de pruebas y desarrollo de Azure</span><span class="sxs-lookup"><span data-stu-id="afe33-166">Intranet SharePoint Server 2016 in Azure dev/test environment</span></span>](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx)
    
    <span data-ttu-id="afe33-167">Cree una granja de un solo servidor de SharePoint Server 2016 en la red virtual de Azure y pruebe la conectividad y administración desde la red local.</span><span class="sxs-lookup"><span data-stu-id="afe33-167">Create a single-server SharePoint Server 2016 farm in the Azure virtual network and test connectivity and administration from the simulated on-premises network.</span></span>
    
## <a name="additional-cloud-based-devtest-environments"></a><span data-ttu-id="afe33-168">Entornos adicionales de desarrollo y pruebas basados en la nube</span><span class="sxs-lookup"><span data-stu-id="afe33-168">Additional cloud-based dev/test environments</span></span>
<span data-ttu-id="afe33-169"><a name="ADD_TLGs"> </a></span><span class="sxs-lookup"><span data-stu-id="afe33-169"></span></span>

<span data-ttu-id="afe33-170">Estos son entornos adicionales de desarrollo y pruebas basados en la nube que puede crear en los servicios de infraestructura de Azure:</span><span class="sxs-lookup"><span data-stu-id="afe33-170">Here are additional cloud-based dev/test environments that you can create in Azure infrastructure services:</span></span>
  
- [<span data-ttu-id="afe33-171">Entorno de desarrollo y prueba de 2016 de SharePoint Server en Azure</span><span class="sxs-lookup"><span data-stu-id="afe33-171">SharePoint Server 2016 dev/test environment in Azure</span></span>](https://technet.microsoft.com/library/mt723354.aspx)
    
    <span data-ttu-id="afe33-172">Cree una granja de un solo servidor de SharePoint Server 2016 en los servicios de infraestructura de Azure.</span><span class="sxs-lookup"><span data-stu-id="afe33-172">Build a single-server SharePoint Server 2016 farm in Azure infrastructure services.</span></span>
    
- [<span data-ttu-id="afe33-173">Entorno de desarrollo y prueba de 2016 de Exchange en Azure</span><span class="sxs-lookup"><span data-stu-id="afe33-173">Exchange 2016 dev/test environment in Azure</span></span>](https://technet.microsoft.com/library/mt733070%28v=exchg.160%29.aspx)
    
    <span data-ttu-id="afe33-174">Cree un único servidor de Exchange 2016 en los servicios de infraestructura de Azure.</span><span class="sxs-lookup"><span data-stu-id="afe33-174">Build a single Exchange 2016 server in Azure infrastructure services.</span></span>
    
- [<span data-ttu-id="afe33-175">Entornos de pruebas y desarrollo de SharePoint Server 2013 en Azure</span><span class="sxs-lookup"><span data-stu-id="afe33-175">SharePoint Server 2013 dev/test environments in Azure</span></span>](http://technet.microsoft.com/library/165de4d5-8fe6-4fbb-a15b-39a8b0a0eb23.aspx)
    
    <span data-ttu-id="afe33-176">Cree granjas de servidores básicas y de alta disponibilidad de SharePoint Server 2013 en los servicios de infraestructura de Azure.</span><span class="sxs-lookup"><span data-stu-id="afe33-176">Build basic and high-availability SharePoint Server 2013 farms in Azure infrastructure services.</span></span>
    
<span data-ttu-id="afe33-177">**Participar en la discusión**</span><span class="sxs-lookup"><span data-stu-id="afe33-177">**Join the discussion**</span></span>

|<span data-ttu-id="afe33-178">**Póngase en contacto con nosotros**</span><span class="sxs-lookup"><span data-stu-id="afe33-178">**Contact us**</span></span>|<span data-ttu-id="afe33-179">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="afe33-179">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="afe33-180">**¿Qué soluciones necesita?**</span><span class="sxs-lookup"><span data-stu-id="afe33-180">**What cloud adoption content do you need?**</span></span> <br/> |<span data-ttu-id="afe33-p105">Estamos creando contenido para soluciones que abarcan varios productos y servicios de Microsoft. Díganos qué piensa sobre nuestras soluciones entre servidores o solicite soluciones específicas por correo electrónico a [MODAcontent@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).</span><span class="sxs-lookup"><span data-stu-id="afe33-p105">We are creating content for cloud adoption that spans multiple Microsoft cloud platforms and services. Let us know what you think about our cloud adoption content, or ask for specific content by sending email to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).  </span></span><br/> |
|<span data-ttu-id="afe33-183">**Participe en la discusión sobre soluciones**</span><span class="sxs-lookup"><span data-stu-id="afe33-183">**Join the cloud adoption discussion**</span></span> <br/> |<span data-ttu-id="afe33-p106">Si es un apasionado de las soluciones basadas en la nube, considere la posibilidad de unirse a la nube adopción Advisory Board (CAAB) para conectar con una comunidad vibrante, más grande de los desarrolladores de contenido de Microsoft, profesionales de la industria y los clientes de todo el mundo. Para unir, Agréguese como un miembro del [espacio CAAB (nube adopción Advisory Board)](https://aka.ms/caab) de la Comunidad de tecnología Microsoft y envíenos un correo electrónico rápido a [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Cualquier persona puede leer contenido relacionados con la Comunidad en el [blog CAAB](https://blogs.technet.com/b/solutions_advisory_board/). Sin embargo, los miembros CAAB obtener invitaciones para seminarios Web privada que describen las soluciones y los nuevos recursos de adopción de nube.</span><span class="sxs-lookup"><span data-stu-id="afe33-p106">If you are passionate about cloud-based solutions, consider joining the Cloud Adoption Advisory Board (CAAB) to connect with a larger, vibrant community of Microsoft content developers, industry professionals, and customers from around the globe. To join, add yourself as a member of the [CAAB (Cloud Adoption Advisory Board) space](https://aka.ms/caab) of the Microsoft Tech Community and send us a quick email at [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Anyone can read community-related content on the [CAAB blog](https://blogs.technet.com/b/solutions_advisory_board/). However, CAAB members get invitations to private webinars that describe new cloud adoption resources and solutions.  </span></span><br/> |
|<span data-ttu-id="afe33-187">**Obtenga los archivos de arte que ve aquí**</span><span class="sxs-lookup"><span data-stu-id="afe33-187">**Get the art you see here**</span></span> <br/> |<span data-ttu-id="afe33-p107">Si desea una copia editable del arte que vea en este artículo, le gustará lo envíe de nuevo. Correo electrónico de su solicitud, incluidas la dirección URL y el título del arte, a [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).</span><span class="sxs-lookup"><span data-stu-id="afe33-p107">If you want an editable copy of the art you see in this article, we'll be glad to send it to you. Email your request, including the URL and title of the art, to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).  </span></span><br/> |
   
## <a name="see-also"></a><span data-ttu-id="afe33-190">See Also</span><span class="sxs-lookup"><span data-stu-id="afe33-190">See Also</span></span>

<span data-ttu-id="afe33-191"><a name="ADD_TLGs"> </a></span><span class="sxs-lookup"><span data-stu-id="afe33-191"></span></span>

[<span data-ttu-id="afe33-192">Adopción de la nube y soluciones híbridas</span><span class="sxs-lookup"><span data-stu-id="afe33-192">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="afe33-193">Recursos de arquitectura de TI de la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="afe33-193">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)
  
[<span data-ttu-id="afe33-194">Modelos arquitectónicos para SharePoint, Exchange, Skype para empresas y Lync</span><span class="sxs-lookup"><span data-stu-id="afe33-194">Architectural models for SharePoint, Exchange, Skype for Business, and Lync</span></span>](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[<span data-ttu-id="afe33-195">Soluciones híbridas</span><span class="sxs-lookup"><span data-stu-id="afe33-195">Hybrid solutions</span></span>](hybrid-solutions.md)


