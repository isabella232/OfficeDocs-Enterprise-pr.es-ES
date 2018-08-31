---
title: Seguridad para Contoso Corporation
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 8f6f9894-5394-4110-8b0a-b8765028c10b
description: 'Resumen: Conozca cómo Contoso asigna sus requisitos de seguridad a las características de las ofertas de nube de Microsoft y determina una ruta de acceso a la nube de preparación de la seguridad.'
ms.openlocfilehash: 722c01995c95c36b9975b0682858c38063f79d2c
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914835"
---
# <a name="security-for-the-contoso-corporation"></a><span data-ttu-id="a707b-103">Seguridad para Contoso Corporation</span><span class="sxs-lookup"><span data-stu-id="a707b-103">Security for the Contoso Corporation</span></span>

 <span data-ttu-id="a707b-104">**Resumen:** Comprender cómo Contoso asigna sus requisitos de seguridad a las características de las ofertas de nube de Microsoft y determina una ruta de acceso a la nube de preparación de la seguridad.</span><span class="sxs-lookup"><span data-stu-id="a707b-104">**Summary:** Understand how Contoso mapped their security requirements to features in Microsoft's cloud offerings and determined a path to cloud security readiness.</span></span>
  
<span data-ttu-id="a707b-p101">Contoso es grave sobre su protección y seguridad de la información. Al trasladar su infraestructura de TI a una nube inclusive, realizan asegurarse de que sus requisitos de seguridad local se admitían e implementados en las ofertas de nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a707b-p101">Contoso is serious about their information security and protection. When transitioning their IT infrastructure to a cloud-inclusive one, they made sure that their on-premises security requirements were supported and implemented in Microsoft's cloud offerings.</span></span>
  
## <a name="contosos-security-requirements-in-the-cloud"></a><span data-ttu-id="a707b-107">Requisitos de seguridad de Contoso en la nube</span><span class="sxs-lookup"><span data-stu-id="a707b-107">Contoso's security requirements in the cloud</span></span>

<span data-ttu-id="a707b-108">Estos son los requisitos de seguridad de Contoso para la nube:</span><span class="sxs-lookup"><span data-stu-id="a707b-108">Here are Contoso's security requirements for the cloud:</span></span>
  
- <span data-ttu-id="a707b-109">Autenticación sólida para los recursos de la nube</span><span class="sxs-lookup"><span data-stu-id="a707b-109">Strong authentication to cloud resources</span></span>
    
    <span data-ttu-id="a707b-110">Se debe autenticar el acceso a los recursos en la nube y, cuando sea posible, aprovechar la autenticación multifactor.</span><span class="sxs-lookup"><span data-stu-id="a707b-110">Cloud resource access must be authenticated and, where possible, leverage multi-factor authentication.</span></span>
    
- <span data-ttu-id="a707b-111">Cifrado de tráfico a través de Internet</span><span class="sxs-lookup"><span data-stu-id="a707b-111">Encryption for traffic across the Internet</span></span>
    
    <span data-ttu-id="a707b-p102">No se envían datos en texto sin formato a través de Internet. Usar siempre conexiones HTTPS, IPsec u otros métodos de cifrado de datos descentralizados.</span><span class="sxs-lookup"><span data-stu-id="a707b-p102">No data sent across the Internet is in plain text form. Always use HTTPS connections, IPsec, or other end-to-end data encryption methods.</span></span>
    
- <span data-ttu-id="a707b-114">Cifrado de datos en reposo en la nube</span><span class="sxs-lookup"><span data-stu-id="a707b-114">Encryption for data at rest in the cloud</span></span>
    
    <span data-ttu-id="a707b-115">Todos los datos almacenados en discos o en otros lugares en la nube deben estar en un formato cifrado.</span><span class="sxs-lookup"><span data-stu-id="a707b-115">All data stored on disks or elsewhere in the cloud must be in an encrypted form.</span></span>
    
- <span data-ttu-id="a707b-116">ACL para el acceso con privilegios mínimos</span><span class="sxs-lookup"><span data-stu-id="a707b-116">ACLs for least privilege access</span></span>
    
    <span data-ttu-id="a707b-117">Los permisos de cuenta para acceder a los recursos en la nube y lo que pueden hacer deben seguir las directrices de privilegios mínimos.</span><span class="sxs-lookup"><span data-stu-id="a707b-117">Account permissions to access resources in the cloud and what they are allowed to do must follow least-privilege guidelines.</span></span>
    
## <a name="contosos-data-sensitivity-classification"></a><span data-ttu-id="a707b-118">Clasificación de confidencialidad de datos de Contoso</span><span class="sxs-lookup"><span data-stu-id="a707b-118">Contoso's data sensitivity classification</span></span>

<span data-ttu-id="a707b-119">Con la información en el [Kit de herramientas de clasificación de datos](https://msdn.microsoft.com/library/hh204743.aspx)de Microsoft, Contoso realizó un análisis de sus datos y determina los siguientes niveles.</span><span class="sxs-lookup"><span data-stu-id="a707b-119">Using the information in Microsoft's [Data Classification Toolkit](https://msdn.microsoft.com/library/hh204743.aspx), Contoso performed an analysis of their data and determined the following levels.</span></span>
  
|<span data-ttu-id="a707b-120">**Nivel 1: valor empresarial bajo**</span><span class="sxs-lookup"><span data-stu-id="a707b-120">**Level 1: Low business value**</span></span>|<span data-ttu-id="a707b-121">**Nivel 2: valor empresarial medio**</span><span class="sxs-lookup"><span data-stu-id="a707b-121">**Level 2: Medium business value**</span></span>|<span data-ttu-id="a707b-122">**Nivel 3: valor empresarial alto**</span><span class="sxs-lookup"><span data-stu-id="a707b-122">**Level 3: High business value**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="a707b-123">Los datos están cifrados y solo están disponibles para los usuarios autenticados

</span><span class="sxs-lookup"><span data-stu-id="a707b-123">Data is encrypted and available only to authenticated users</span></span>  <br/> <span data-ttu-id="a707b-p103">Se proporciona para todos los datos almacenados de forma local y en almacenamiento y cargas de trabajo basadas en la nube, como Office 365. Los datos se encriptan mientras residen en el servicio y en tránsito entre el servicio y los dispositivos de cliente.</span><span class="sxs-lookup"><span data-stu-id="a707b-p103">Provided for all data stored on premises and in cloud-based storage and workloads, such as Office 365. Data is encrypted while it resides in the service and in transit between the service and client devices.</span></span>  <br/> <span data-ttu-id="a707b-126">Algunos ejemplos de datos de nivel 1 son las comunicaciones empresariales normales (correo electrónico) y los archivos de empleados administrativos, de ventas y de soporte técnico.</span><span class="sxs-lookup"><span data-stu-id="a707b-126">Examples of Level 1 data are normal business communications (email) and files for administrative, sales, and support workers.</span></span>  <br/> |<span data-ttu-id="a707b-127">Características del nivel 1 más autenticación sólida y protección contra la pérdida de datos
</span><span class="sxs-lookup"><span data-stu-id="a707b-127">Level 1 plus strong authentication and data loss protection</span></span>  <br/> <span data-ttu-id="a707b-p104">La autenticación segura incluye autenticación multifactor con validación de SMS. La prevención de pérdida de datos garantiza que la información crítica o confidencial no sale de la red local.
</span><span class="sxs-lookup"><span data-stu-id="a707b-p104">Strong authentication includes multi-factor authentication with SMS validation. Data loss prevention ensures that sensitive or critical information does not travel outside the on-premises network.</span></span>  <br/> <span data-ttu-id="a707b-130">Algunos ejemplos de datos de nivel 2 son la información jurídica y financiera, y los datos de investigación y desarrollo de nuevos productos.</span><span class="sxs-lookup"><span data-stu-id="a707b-130">Examples of Level 2 data are financial and legal information and research and development data for new products.</span></span>  <br/> |<span data-ttu-id="a707b-131">Características del nivel 2 además de los niveles más altos de cifrado, autenticación y auditoría
</span><span class="sxs-lookup"><span data-stu-id="a707b-131">Level 2 plus the highest levels of encryption, authentication, and auditing</span></span>  <br/> <span data-ttu-id="a707b-132">Los niveles más altos de cifrado de datos en reposo y en la nube, conformes con la normativa regional, combinados con autentificación multifactor con tarjetas inteligentes y auditoría y alertas pormenorizadas.
</span><span class="sxs-lookup"><span data-stu-id="a707b-132">The highest levels of encryption for data at rest and in the cloud, compliant with regional regulations, combined with multi-factor authentication with smart cards and granular auditing and alerting.</span></span>  <br/> <span data-ttu-id="a707b-133">Algunos ejemplos de datos de nivel 3 son la información de identificación personal de clientes y partners, las especificaciones de ingeniería de productos y las técnicas de fabricación patentadas.</span><span class="sxs-lookup"><span data-stu-id="a707b-133">Examples of Level 3 data are customer and partner personally identifiable information and product engineering specifications and proprietary manufacturing techniques.</span></span>  <br/> |
   
## <a name="mapping-microsoft-cloud-offerings-and-features-to-contosos-data-levels"></a><span data-ttu-id="a707b-134">Asignación de las ofertas de nube de Microsoft y características en los niveles de datos de Contoso</span><span class="sxs-lookup"><span data-stu-id="a707b-134">Mapping Microsoft cloud offerings and features to Contoso's data levels</span></span>

<span data-ttu-id="a707b-135">En la tabla siguiente se muestra la asignación de niveles de datos de Contoso a funciones en las ofertas de nube de Microsoft:</span><span class="sxs-lookup"><span data-stu-id="a707b-135">The following table shows the mapping of Contoso's data levels to features in Microsoft's cloud offerings:</span></span>
  
||<span data-ttu-id="a707b-136">**SaaS**</span><span class="sxs-lookup"><span data-stu-id="a707b-136">**SaaS**</span></span>|<span data-ttu-id="a707b-137">**Plataforma como servicio de Azure**</span><span class="sxs-lookup"><span data-stu-id="a707b-137">**Azure PaaS**</span></span>|<span data-ttu-id="a707b-138">**IaaS de Azure**</span><span class="sxs-lookup"><span data-stu-id="a707b-138">**Azure IaaS**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="a707b-139">Nivel 1: valor empresarial bajo</span><span class="sxs-lookup"><span data-stu-id="a707b-139">Level 1: Low business value</span></span>  <br/> | <span data-ttu-id="a707b-140">HTTPS para todas las conexiones
</span><span class="sxs-lookup"><span data-stu-id="a707b-140">HTTPS for all connections</span></span> <br/>  <span data-ttu-id="a707b-141">Cifrado en reposo</span><span class="sxs-lookup"><span data-stu-id="a707b-141">Encryption at rest</span></span> <br/> | <span data-ttu-id="a707b-142">Admitir solo las conexiones HTTPS
</span><span class="sxs-lookup"><span data-stu-id="a707b-142">Support only HTTPS connections</span></span> <br/>  <span data-ttu-id="a707b-143">Cifrar archivos almacenados en Azure</span><span class="sxs-lookup"><span data-stu-id="a707b-143">Encrypt files stored in Azure</span></span> <br/> | <span data-ttu-id="a707b-144">Requerir HTTPS o IPsec para el acceso al servidor
</span><span class="sxs-lookup"><span data-stu-id="a707b-144">Require HTTPS or IPsec for server access</span></span> <br/>  <span data-ttu-id="a707b-145">Azure Disk Encryption</span><span class="sxs-lookup"><span data-stu-id="a707b-145">Azure disk encryption</span></span> <br/> |
|<span data-ttu-id="a707b-146">Nivel 2: valor empresarial medio</span><span class="sxs-lookup"><span data-stu-id="a707b-146">Level 2: Medium business value</span></span>  <br/> | <span data-ttu-id="a707b-147">Autenticación multifactor de Azure AD (MFA) con SMS</span><span class="sxs-lookup"><span data-stu-id="a707b-147">Azure AD multi-factor authentication (MFA) with SMS</span></span> <br/> | <span data-ttu-id="a707b-148">Usar Azure Key Vault para las claves de cifrado
</span><span class="sxs-lookup"><span data-stu-id="a707b-148">Use Azure Key Vault for encryption keys</span></span> <br/>  <span data-ttu-id="a707b-149">MFA de Azure AD con SMS</span><span class="sxs-lookup"><span data-stu-id="a707b-149">Azure AD MFA with SMS</span></span> <br/> | <span data-ttu-id="a707b-150">MFA con SMS</span><span class="sxs-lookup"><span data-stu-id="a707b-150">MFA with SMS</span></span> <br/> |
|<span data-ttu-id="a707b-151">Nivel 3: valor empresarial alto</span><span class="sxs-lookup"><span data-stu-id="a707b-151">Level 3: High business value</span></span>  <br/> | <span data-ttu-id="a707b-152">Sistema Azure Rights Management (RMS)

</span><span class="sxs-lookup"><span data-stu-id="a707b-152">Azure Rights Management System (RMS)</span></span> <br/>  <span data-ttu-id="a707b-153">MFA de Azure AD con tarjetas inteligentes</span><span class="sxs-lookup"><span data-stu-id="a707b-153">Azure AD MFA with smart cards</span></span> <br/>  <span data-ttu-id="a707b-154">Acceso condicional de Intune</span><span class="sxs-lookup"><span data-stu-id="a707b-154">Intune conditional access</span></span> <br/> | <span data-ttu-id="a707b-155">Azure RMS</span><span class="sxs-lookup"><span data-stu-id="a707b-155">Azure RMS</span></span> <br/>  <span data-ttu-id="a707b-156">MFA de Azure AD con tarjetas inteligentes</span><span class="sxs-lookup"><span data-stu-id="a707b-156">Azure AD MFA with smart cards</span></span> <br/> | <span data-ttu-id="a707b-157">MFA con tarjetas inteligentes</span><span class="sxs-lookup"><span data-stu-id="a707b-157">MFA with smart cards</span></span> <br/> |
   
## <a name="contosos-information-policies"></a><span data-ttu-id="a707b-158">Directivas de información de Contoso</span><span class="sxs-lookup"><span data-stu-id="a707b-158">Contoso's information policies</span></span>

<span data-ttu-id="a707b-159">La siguiente tabla enumera las directivas de información de Contoso.</span><span class="sxs-lookup"><span data-stu-id="a707b-159">The following table lists Contoso's information policies.</span></span>
  
||<span data-ttu-id="a707b-160">**Acceso**</span><span class="sxs-lookup"><span data-stu-id="a707b-160">**Access**</span></span>|<span data-ttu-id="a707b-161">**Retención de datos**</span><span class="sxs-lookup"><span data-stu-id="a707b-161">**Data retention**</span></span>|<span data-ttu-id="a707b-162">**Protección de la información**</span><span class="sxs-lookup"><span data-stu-id="a707b-162">**Information protection**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="a707b-163">Nivel 1: valor empresarial bajo</span><span class="sxs-lookup"><span data-stu-id="a707b-163">Level 1: Low business value</span></span>  <br/> | <span data-ttu-id="a707b-164">Permitir el acceso a todo el mundo</span><span class="sxs-lookup"><span data-stu-id="a707b-164">Allow access to all</span></span> <br/> |<span data-ttu-id="a707b-165">6 meses</span><span class="sxs-lookup"><span data-stu-id="a707b-165">6 months</span></span>  <br/> |<span data-ttu-id="a707b-166">Usa cifrado</span><span class="sxs-lookup"><span data-stu-id="a707b-166">Use encryption</span></span>  <br/> |
|<span data-ttu-id="a707b-167">Nivel 2: valor empresarial medio</span><span class="sxs-lookup"><span data-stu-id="a707b-167">Level 2: Medium business value</span></span>  <br/> | <span data-ttu-id="a707b-168">Permitir el acceso a subcontratistas, partners y empleados de Contoso
</span><span class="sxs-lookup"><span data-stu-id="a707b-168">Allow access to Contoso employees, subcontractors, and partners</span></span> <br/>  <span data-ttu-id="a707b-169">Usar MFA, TLS y MAM</span><span class="sxs-lookup"><span data-stu-id="a707b-169">Use MFA, TLS, and MAM</span></span> <br/> |<span data-ttu-id="a707b-170">2 años</span><span class="sxs-lookup"><span data-stu-id="a707b-170">2 years</span></span>  <br/> |<span data-ttu-id="a707b-171">Usar valores hash para la integridad de datos</span><span class="sxs-lookup"><span data-stu-id="a707b-171">Use hash values for data integrity</span></span>  <br/> |
|<span data-ttu-id="a707b-172">Nivel 3: valor empresarial alto</span><span class="sxs-lookup"><span data-stu-id="a707b-172">Level 3: High business value</span></span>  <br/> | <span data-ttu-id="a707b-173">Permitir el acceso a ejecutivos y clientes potenciales de ingeniería y fabricación
</span><span class="sxs-lookup"><span data-stu-id="a707b-173">Allow access to executives and leads in engineering and manufacturing</span></span> <br/>  <span data-ttu-id="a707b-174">RMS con dispositivos de red administrados solamente</span><span class="sxs-lookup"><span data-stu-id="a707b-174">RMS with managed network devices only</span></span> <br/> |<span data-ttu-id="a707b-175">7 años</span><span class="sxs-lookup"><span data-stu-id="a707b-175">7 years</span></span>  <br/> |<span data-ttu-id="a707b-176">Usar firmas digitales para evitar el rechazo</span><span class="sxs-lookup"><span data-stu-id="a707b-176">Use digital signatures for non-repudiation</span></span>  <br/> |
   
## <a name="contosos-path-to-cloud-security-readiness"></a><span data-ttu-id="a707b-177">Ruta de acceso de Contoso para la preparación de la seguridad en la nube</span><span class="sxs-lookup"><span data-stu-id="a707b-177">Contoso's path to cloud security readiness</span></span>

<span data-ttu-id="a707b-178">Contoso usó los pasos siguientes para preparar su seguridad para la nube de Microsoft:</span><span class="sxs-lookup"><span data-stu-id="a707b-178">Contoso used the following steps to ready their security for the Microsoft cloud:</span></span>
  
1. <span data-ttu-id="a707b-179">Optimizar las cuentas de administrador para la nube
</span><span class="sxs-lookup"><span data-stu-id="a707b-179">Optimize administrator accounts for the cloud</span></span>
    
    <span data-ttu-id="a707b-180">Contoso realizó una revisión exhaustiva de las cuentas de administrador de Windows Server AD existentes y estableció una serie de grupos y cuentas de administrador de la nube.</span><span class="sxs-lookup"><span data-stu-id="a707b-180">Contoso did an extensive review of the existing Windows Server AD administrator accounts and set up a series of cloud administrator accounts and groups.</span></span>
    
2. <span data-ttu-id="a707b-181">Realizar análisis de clasificación de datos en tres niveles
</span><span class="sxs-lookup"><span data-stu-id="a707b-181">Perform data classification analysis into three levels</span></span>
    
    <span data-ttu-id="a707b-182">Contoso lleva a cabo una cuidadosa revisión y determina los tres niveles, que se utilizan para determinar la nube de Microsoft que ofrece características para proteger los datos más valiosos de Contoso.</span><span class="sxs-lookup"><span data-stu-id="a707b-182">Contoso performed a careful review and determined the three levels, which was used to determine the Microsoft cloud offering features to protect Contoso's most valuable data.</span></span>
    
3. <span data-ttu-id="a707b-183">Determinar las directivas de acceso, retención y protección de la información para los niveles de datos
</span><span class="sxs-lookup"><span data-stu-id="a707b-183">Determine access, retention, and information protection policies for data levels</span></span>
    
    <span data-ttu-id="a707b-184">Según los niveles de datos, Contoso determinó los requisitos detallados, que se usarán para calificar futuras cargas de trabajo de TI que se muevan a la nube.</span><span class="sxs-lookup"><span data-stu-id="a707b-184">Based on the data levels, Contoso determined detailed requirements, which will be used to qualify future IT workloads being moved to the cloud.</span></span>
    
## <a name="contosos-use-of-office-365-security-best-practices"></a><span data-ttu-id="a707b-185">Uso de Contoso de procedimientos recomendados de seguridad de Office 365</span><span class="sxs-lookup"><span data-stu-id="a707b-185">Contoso's use of Office 365 security best practices</span></span>

<span data-ttu-id="a707b-186">Conformidad con Office 365 procedimientos recomendados de seguridad, los administradores de seguridad y el departamento de TI de Contoso han implementado lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="a707b-186">In accordance with Office 365 security best practices, Contoso's security administrators and IT department have deployed the following:</span></span>
  
- <span data-ttu-id="a707b-187">**Dedicada a las cuentas de administrador global con contraseñas muy seguras**</span><span class="sxs-lookup"><span data-stu-id="a707b-187">**Dedicated global administrator accounts with very strong passwords**</span></span>
    
    <span data-ttu-id="a707b-p105">En lugar de asignar el rol de administrador global para las cuentas de usuario cotidianas, Contoso ha crear tres, dedicada a las cuentas de administrador global con contraseñas muy seguras. Iniciar sesión con una cuenta de administrador global se realiza sólo para tareas administrativas específicas y sólo se conocen las contraseñas al personal designado. Los administradores de seguridad de Contoso han asignado roles de administrador a las cuentas que son adecuadas para la función de trabajo de esa persona de TI y la responsabilidad.</span><span class="sxs-lookup"><span data-stu-id="a707b-p105">Rather than assign the global admin role to everyday user accounts, Contoso has create three, dedicated global administrator accounts with very strong passwords. Signing in with a global administrator account is only done for specific administrative tasks and the passwords are only known to designated staff. Contoso's security administrators have assigned admin roles to accounts that are appropriate to that IT person's job function and responsibility.</span></span>
    
    <span data-ttu-id="a707b-191">Para obtener más información, vea [roles de administrador acerca de Office 365](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d).</span><span class="sxs-lookup"><span data-stu-id="a707b-191">For more information, see [About Office 365 admin roles](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d).</span></span>
    
- <span data-ttu-id="a707b-192">**Autenticación multifactor (MFA) para las cuentas de usuario importantes**</span><span class="sxs-lookup"><span data-stu-id="a707b-192">**Multi-factor authentication (MFA) for important user accounts**</span></span>
    
    <span data-ttu-id="a707b-p106">MFA agrega una capa adicional de protección para el proceso de inicio de sesión al requerir que los usuarios a una llamada de teléfono, mensaje de texto o una notificación de la aplicación en su teléfono inteligente después de escribir correctamente su contraseña. Con MFA, las cuentas de usuario de Office 365 están protegidas contra el inicio de sesión no autorizado de incluso si se ve comprometida una contraseña de la cuenta.</span><span class="sxs-lookup"><span data-stu-id="a707b-p106">MFA adds an additional layer of protection to the sign-in process by requiring users to acknowledge a phone call, text message, or an app notification on their smart phone after correctly entering their password. With MFA, Office 365 user accounts are protected against unauthorized sign-in even if an account password is compromised.</span></span>
    
  - <span data-ttu-id="a707b-195">Para proteger contra un compromiso de la suscripción de Office 365, Contoso habilitado MFA en todas las cuentas de administrador global de tres.</span><span class="sxs-lookup"><span data-stu-id="a707b-195">To protect against a compromise of the Office 365 subscription, Contoso enabled MFA on all three global administrator accounts.</span></span>
    
  - <span data-ttu-id="a707b-196">Para proteger contra los ataques de suplantación de identidad, en la que un atacante ponga en peligro las credenciales de una persona de confianza en la organización y envía mensajes de correo electrónico, Contoso habilitado MFA en todas las cuentas de usuario para los administradores, incluido el personal ejecutivo.</span><span class="sxs-lookup"><span data-stu-id="a707b-196">To protect against phishing attacks, in which an attacker compromises the credentials of a trusted person in the organization and sends malicious emails, Contoso enabled MFA on all user accounts for managers, including the executive staff.</span></span>
    
    <span data-ttu-id="a707b-197">Para obtener más información, vea [Planear la autenticación multifactor para las implementaciones de Office 365](https://support.office.com/article/Plan-for-multifactor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)</span><span class="sxs-lookup"><span data-stu-id="a707b-197">For more information, see [Plan for multi-factor authentication for Office 365 Deployments](https://support.office.com/article/Plan-for-multifactor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)</span></span>
    
- <span data-ttu-id="a707b-198">**Administración de seguridad avanzada (ASM)**</span><span class="sxs-lookup"><span data-stu-id="a707b-198">**Advanced Security Management (ASM)**</span></span>
    
    <span data-ttu-id="a707b-p107">Usos ASM configurado directivas para supervisar la actividad anómala. Configurar alertas con ASM de modo que se notifican a los administradores de TI de actividad de usuario inusual o arriesgado, como una descarga grandes cantidades de datos, los administradores de seguridad de Contoso no pudo varios intentos de inicio de sesión o inicios de sesión desde direcciones IP desconocidas o peligrosas</span><span class="sxs-lookup"><span data-stu-id="a707b-p107">ASM uses configured policies to monitor for anomalous activity. Contoso security administrators set up alerts with ASM so that IT administrators are notified of unusual or risky user activity, such as downloading large amounts of data, multiple failed sign-in attempts, or sign-ins from unknown or dangerous IP addresses</span></span>
    
    <span data-ttu-id="a707b-201">Para obtener más información, vea [Información general de administración avanzada de seguridad en Office 365 ](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).</span><span class="sxs-lookup"><span data-stu-id="a707b-201">For more information, see [Overview of Advanced Security Management in Office 365 ](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).</span></span>
    
- <span data-ttu-id="a707b-202">**Flujo de correo electrónico seguro y el buzón de registro de auditoría**</span><span class="sxs-lookup"><span data-stu-id="a707b-202">**Secure email flow and mailbox audit logging**</span></span>
    
    <span data-ttu-id="a707b-p108">Especialistas en seguridad de Contoso usa Exchange Online Protection y protección avanzada de amenaza (ATP) para proteger contra malware desconocido, virus y direcciones URL malintencionadas se transmite a través de mensajes de correo electrónico. Contoso también ha habilitado registro de auditoría para determinar quién ha iniciado sesión en los buzones de usuario, mensajes enviados y otras actividades realizadas por el propietario del buzón, un usuario delegado o un administrador.</span><span class="sxs-lookup"><span data-stu-id="a707b-p108">Contoso security specialists are using Exchange Online Protection and Advanced Threat Protection (ATP) to protect against unknown malware, viruses, and malicious URLs transmitted through emails. Contoso has also enabled mailbox audit logging to determine who has logged into user mailboxes, sent messages, and other activities performed by the mailbox owner, a delegated user, or an administrator.</span></span>
    
    <span data-ttu-id="a707b-205">Para obtener más información, vea:</span><span class="sxs-lookup"><span data-stu-id="a707b-205">For more information, see:</span></span> 
    
  - [<span data-ttu-id="a707b-206">Protección contra correo no deseado de Office 365</span><span class="sxs-lookup"><span data-stu-id="a707b-206">Office 365 Email Anti-Spam Protection</span></span>](https://support.office.com/article/Office-365-Email-AntiSpam-Protection-6a601501-a6a8-4559-b2e7-56b59c96a586)
    
  - [<span data-ttu-id="a707b-207">Protección contra amenazas avanzada para datos adjuntos seguros y vínculos seguros</span><span class="sxs-lookup"><span data-stu-id="a707b-207">Advanced threat protection for safe attachments and safe links</span></span>](https://technet.microsoft.com/library/mt148491.aspx)
    
  - [<span data-ttu-id="a707b-208">Habilitar la auditoría de buzones de correo en Office 365</span><span class="sxs-lookup"><span data-stu-id="a707b-208">Enable mailbox auditing in Office 365</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=626109)
    
- <span data-ttu-id="a707b-209">**Prevención de pérdida de datos (DLP)**</span><span class="sxs-lookup"><span data-stu-id="a707b-209">**Data Loss Prevention (DLP)**</span></span>
    
    <span data-ttu-id="a707b-210">Contoso ha identificado sus datos confidenciales y configurado las directivas de DLP para Exchange Online, SharePoint Online y OneDrive ayudar a impedir que los usuarios los datos de uso compartido de forma accidental o intencionada.</span><span class="sxs-lookup"><span data-stu-id="a707b-210">Contoso has identified its sensitive data and configured DLP policies for Exchange Online, SharePoint Online, and OneDrive to help prevent users from accidentally or intentionally sharing the data.</span></span> 
    
    <span data-ttu-id="a707b-211">Para obtener más información, consulte [Información general sobre directivas de prevención de pérdida de datos](https://support.office.com/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e).</span><span class="sxs-lookup"><span data-stu-id="a707b-211">For more information, see [Overview of data loss prevention policies](https://support.office.com/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e).</span></span>
    
## <a name="see-also"></a><span data-ttu-id="a707b-212">See Also</span><span class="sxs-lookup"><span data-stu-id="a707b-212">See Also</span></span>

[<span data-ttu-id="a707b-213">Contoso en la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="a707b-213">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="a707b-214">Recursos de arquitectura de TI de la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="a707b-214">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="a707b-215">Mapa de ruta de Enterprise Cloud de Microsoft: Recursos para los responsables de decisiones de TI</span><span class="sxs-lookup"><span data-stu-id="a707b-215">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)
  
[<span data-ttu-id="a707b-216">Procedimientos recomendados de seguridad para Office 365</span><span class="sxs-lookup"><span data-stu-id="a707b-216">Security best practices for Office 365</span></span>](https://support.office.com/article/Security-best-practices-for-Office-365-9295e396-e53d-49b9-ae9b-0b5828cdedc3)




