---
title: Fase 5 de la autenticación federada de alta disponibilidad Configurar la autenticación federada para Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/25/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Solutions
ms.assetid: 0f1dbf52-5bff-44cc-a264-1b48641af98f
description: 'Resumen: Configure Azure AD Connect para la autenticación federada de alta disponibilidad para Office 365 en Microsoft Azure.'
ms.openlocfilehash: 8a65ee9af994d46cdc53266a92851e0684e06121
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840247"
---
# <a name="high-availability-federated-authentication-phase-5-configure-federated-authentication-for-office-365"></a><span data-ttu-id="8ae82-103">Fase 5 de la autenticación federada de alta disponibilidad: Configurar la autenticación federada para Office 365</span><span class="sxs-lookup"><span data-stu-id="8ae82-103">High availability federated authentication Phase 5: Configure federated authentication for Office 365</span></span>

<span data-ttu-id="8ae82-104">En esta fase final de implementación de la autenticación federada de alta disponibilidad para Office 365 en los servicios de infraestructura de Azure, se obtiene e instala un certificado emitido por una entidad de certificación pública, se comprueba la configuración y, a continuación, se instala y ejecuta Azure AD Conéctese en el servidor de sincronización de directorios.</span><span class="sxs-lookup"><span data-stu-id="8ae82-104">In this final phase of deploying high availability federated authentication for Office 365 in Azure infrastructure services, you get and install a certificate issued by a public certification authority, verify your configuration, and then install and run Azure AD Connect on the directory synchronization server.</span></span> <span data-ttu-id="8ae82-105">Azure AD Connect configura la suscripción a Office 365 y los Servicios de federación de Active Directory (AD FS) y servidores proxy de aplicación web para la autenticación federada.</span><span class="sxs-lookup"><span data-stu-id="8ae82-105">Azure AD Connect configures your Office 365 subscription and your Active Directory Federation Services (AD FS) and web application proxy servers for federated authentication.</span></span>
  
<span data-ttu-id="8ae82-106">Consulte todas las fases en [Implementar la autenticación federada de alta disponibilidad para Office 365 en Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md).</span><span class="sxs-lookup"><span data-stu-id="8ae82-106">See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="get-a-public-certificate-and-copy-it-to-the-directory-synchronization-server"></a><span data-ttu-id="8ae82-107">Obtener un certificado público y copiarlo en el servidor de sincronización de directorios</span><span class="sxs-lookup"><span data-stu-id="8ae82-107">Get a public certificate and copy it to the directory synchronization server</span></span>

<span data-ttu-id="8ae82-108">Obtenga un certificado digital de una entidad de certificación con las siguientes propiedades:</span><span class="sxs-lookup"><span data-stu-id="8ae82-108">Get a digital certificate from a public certification authority with the following properties:</span></span>
  
- <span data-ttu-id="8ae82-109">Un certificado X.509 adecuado para crear conexiones SSL.</span><span class="sxs-lookup"><span data-stu-id="8ae82-109">An X.509 certificate suitable for creating SSL connections.</span></span>
    
- <span data-ttu-id="8ae82-110">La propiedad extendida de nombre alternativo del firmante (SAN) se establece en el FQDN de servicio de federación (ejemplo: fs.contoso.com).</span><span class="sxs-lookup"><span data-stu-id="8ae82-110">The Subject Alternative Name (SAN) extended property is set to your federation service FQDN (example: fs.contoso.com).</span></span>
    
- <span data-ttu-id="8ae82-111">El certificado debe tener la clave privada y estar almacenado en formato PFX.</span><span class="sxs-lookup"><span data-stu-id="8ae82-111">The certificate must have the private key and be stored in PFX format.</span></span>
    
<span data-ttu-id="8ae82-p102">Además, los equipos y dispositivos de la organización deben confiar en la entidad de certificación pública que emite el certificado digital. Esta confianza se establece al tener un certificado raíz de la entidad de certificación pública instalado en el almacén de entidades de certificación raíz de confianza en sus equipos y dispositivos. Los equipos que ejecutan Microsoft Windows normalmente tienen instalado un conjunto de estos tipos de certificados de entidades de certificación usadas frecuentemente. Si el certificado raíz de la entidad de certificación pública no está instalado, debe implementarlo en los equipos y dispositivos de su organización.</span><span class="sxs-lookup"><span data-stu-id="8ae82-p102">Additionally, your organization computers and devices must trust the public certification authority that is issuing the digital certificate. This trust is established by having a root certificate from the public certification authority installed in the trusted root certification authorities store on your computers and devices. Computers running Microsoft Windows typically have a set of these types of certificates installed from commonly-used certification authorities. If the root certificate from your public certification authority is not already installed, you must deploy this to the computers and devices of your organization.</span></span>
  
<span data-ttu-id="8ae82-116">Para obtener más información sobre los requisitos de certificado para la autenticación federada, consulte [Requisitos previos para la instalación y la configuración de la federación](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-prerequisites#prerequisites-for-federation-installation-and-configuration).</span><span class="sxs-lookup"><span data-stu-id="8ae82-116">For more information about certificate requirements for federated authentication, see [Prerequisites for federation installation and configuration](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-prerequisites#prerequisites-for-federation-installation-and-configuration).</span></span>
  
<span data-ttu-id="8ae82-117">Cuando reciba el certificado, cópielo en una carpeta de la unidad C: del servidor de sincronización de directorios.</span><span class="sxs-lookup"><span data-stu-id="8ae82-117">When you receive the certificate, copy it to a folder on the C: drive of the directory synchronization server.</span></span> <span data-ttu-id="8ae82-118">Por ejemplo, asigne al archivo el nombre SSL. pfx y almacénelo en la carpeta\\C: certs del servidor de sincronización de directorios.</span><span class="sxs-lookup"><span data-stu-id="8ae82-118">For example, name the file SSL.pfx and store it in the C:\\Certs folder on the directory synchronization server.</span></span>
  
## <a name="verify-your-configuration"></a><span data-ttu-id="8ae82-119">Comprobar la configuración</span><span class="sxs-lookup"><span data-stu-id="8ae82-119">Verify your configuration</span></span>

<span data-ttu-id="8ae82-p104">Ahora debería estar preparado para configurar Azure AD Connect y la autenticación federada para Office 365. Para asegurarse de estarlo, aquí tiene una lista de comprobación:</span><span class="sxs-lookup"><span data-stu-id="8ae82-p104">You should now be ready to configure Azure AD Connect and federated authentication for Office 365. To ensure that you are, here is a checklist:</span></span>
  
- <span data-ttu-id="8ae82-122">El dominio público de la organización está agregado en la suscripción de Office 365.</span><span class="sxs-lookup"><span data-stu-id="8ae82-122">Your organization's public domain is added to your Office 365 subscription.</span></span>
    
- <span data-ttu-id="8ae82-123">Las cuentas de usuario de Office 365 de la organización están configuradas para el nombre de dominio público de la organización y pueden iniciar sesión correctamente.</span><span class="sxs-lookup"><span data-stu-id="8ae82-123">Your organization's Office 365 user accounts are configured to your organization's public domain name and can successfully sign in.</span></span>
    
- <span data-ttu-id="8ae82-124">Ha determinado un FQDN de servicio de federación en función de su nombre de dominio público.</span><span class="sxs-lookup"><span data-stu-id="8ae82-124">You have determined a federation service FQDN based your public domain name.</span></span>
    
- <span data-ttu-id="8ae82-125">Un registro A de DNS público del FQDN de servicio de federación apunta a la dirección IP pública del equilibrador de carga de Azure accesible desde Internet para los servidores proxy de aplicación web.</span><span class="sxs-lookup"><span data-stu-id="8ae82-125">A public DNS A record for your federation service FQDN points to the public IP address of the Internet-facing Azure load balancer for the web application proxy servers.</span></span>
    
- <span data-ttu-id="8ae82-126">Un registro D de DNS privado del FQDN de servicio de federación apunta a la dirección IP privada del equilibrador de carga interno de Azure para los servidores de AD FS.</span><span class="sxs-lookup"><span data-stu-id="8ae82-126">A private DNS A record for your federation service FQDN points to the private IP address of the internal Azure load balancer for the AD FS servers.</span></span>
    
- <span data-ttu-id="8ae82-127">Un certificado digital de entidad de certificación (isssued) adecuado para conexiones SSL con el SAN establecido en el FQDN de servicio de Federación es un archivo PFX almacenado en el servidor de sincronización de directorios.</span><span class="sxs-lookup"><span data-stu-id="8ae82-127">A public certification authority-isssued digital certificate suitable for SSL connections with the SAN set to your federation service FQDN is a PFX file stored on your directory synchronization server.</span></span>
    
- <span data-ttu-id="8ae82-128">El certificado raíz de la entidad de certificación pública está instalado en el almacén de entidades de certificación raíz de confianza en sus equipos y dispositivos.</span><span class="sxs-lookup"><span data-stu-id="8ae82-128">The root certificate for the public certification authority is installed in the Trusted Root Certification Authorities store on your computers and devices.</span></span>
    
<span data-ttu-id="8ae82-129">Este es un ejemplo de la organización Contoso:</span><span class="sxs-lookup"><span data-stu-id="8ae82-129">Here is an example for the Contoso organization:</span></span>
  
<span data-ttu-id="8ae82-130">**Ejemplo de configuración de una infraestructura de autenticación federada de alta disponibilidad en Azure**</span><span class="sxs-lookup"><span data-stu-id="8ae82-130">**An example configuration for a high availability federated authentication infrastructure in Azure**</span></span>

![Un ejemplo de configuración de la infraestructura de la autenticación federada de Office 365 con alta disponibilidad en Azure](media/ac1a6a0d-0156-4407-9336-6e4cd6db8633.png)
  
## <a name="run-azure-ad-connect-to-configure-federated-authentication"></a><span data-ttu-id="8ae82-132">Ejecutar Azure AD Connect para configurar la autenticación federada</span><span class="sxs-lookup"><span data-stu-id="8ae82-132">Run Azure AD Connect to configure federated authentication</span></span>

<span data-ttu-id="8ae82-133">La herramienta Azure AD Connect configura los servidores de AD FS, los servidores proxy de aplicación web y Office 365 para la autenticación federada con estos pasos:</span><span class="sxs-lookup"><span data-stu-id="8ae82-133">The Azure AD Connect tool configures the AD FS servers, the web application proxy servers, and Office 365 for federated authentication with these steps:</span></span>
  
1. <span data-ttu-id="8ae82-134">Cree una conexión a escritorio remoto al servidor de sincronización de directorios con una cuenta de dominio que tenga privilegios de administrador local.</span><span class="sxs-lookup"><span data-stu-id="8ae82-134">Create a remote desktop connection to your directory synchronization server with a domain account that has local administrator privileges.</span></span>
    
2. <span data-ttu-id="8ae82-135">Desde el escritorio del servidor de sincronización de directorios, abra Internet Explorer y vaya [https://aka.ms/aadconnect](https://aka.ms/aadconnect)a.</span><span class="sxs-lookup"><span data-stu-id="8ae82-135">From the desktop of the directory synchronization server, open Internet Explorer and go to [https://aka.ms/aadconnect](https://aka.ms/aadconnect).</span></span>
    
3. <span data-ttu-id="8ae82-136">En la página **Microsoft Azure Active Directory Connect**, haga clic en **Descargar** y, después, en **Ejecutar**.</span><span class="sxs-lookup"><span data-stu-id="8ae82-136">On the **Microsoft Azure Active Directory Connect** page, click **Download**, and then click **Run**.</span></span>
    
4. <span data-ttu-id="8ae82-137">En la página **Bienvenido a Azure AD Connect**, haga clic en **Acepto** y, después, en **Continuar**.</span><span class="sxs-lookup"><span data-stu-id="8ae82-137">On the **Welcome to Azure AD Connect** page, click **I agree**, and then click **Continue.**</span></span>
    
5. <span data-ttu-id="8ae82-138">En la página **Configuración rápida**, haga clic en **Personalizar**.</span><span class="sxs-lookup"><span data-stu-id="8ae82-138">On the **Express Settings** page, click **Customize**.</span></span>
    
6. <span data-ttu-id="8ae82-139">En la página **Instalar componentes necesarios**, haga clic en **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="8ae82-139">On the **Install required components** page, click **Install**.</span></span>
    
7. <span data-ttu-id="8ae82-140">En la página **Inicio de sesión de usuario**, haga clic en **Federación con AD FS** y, después, haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="8ae82-140">On the **User sign-in** page, click **Federation with AD FS**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="8ae82-141">En la página **Conectar con Azure AD**, escriba el nombre y la contraseña de una cuenta de administrador global de la suscripción de Office 365 y, después, haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="8ae82-141">On the **Connect to Azure AD** page, type the name and password of a global administrator account for your Office 365 subscription, and then click **Next**.</span></span>
    
9. <span data-ttu-id="8ae82-142">En la página **conectar los directorios** , asegúrese de que el bosque de servicios de dominio de Active Directory (AD DS) local esté seleccionado en el **bosque**, escriba el nombre y la contraseña de una cuenta de administrador de dominio, haga clic en **Agregar directorio**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="8ae82-142">On the **Connect your directories** page, ensure that your on-premises Active Directory Domain Services (AD DS) forest is selected in **Forest**, type the name and password of a domain administrator account, click **Add Directory**, and then click **Next**.</span></span>
    
10. <span data-ttu-id="8ae82-143">En la página **Configuración de inicio de sesión de Azure AD**, haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="8ae82-143">On the **Azure AD sign-in configuration** page, click **Next**.</span></span>
    
11. <span data-ttu-id="8ae82-144">En la página **Filtrado de dominios y unidades organizativas**, haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="8ae82-144">On the **Domain and OU filtering** page, click **Next**.</span></span>
    
12. <span data-ttu-id="8ae82-145">En la página **Identificación de forma exclusiva de usuarios**, haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="8ae82-145">On the **Uniquely identifying your users** page, click **Next**.</span></span>
    
13. <span data-ttu-id="8ae82-146">En la página **Filtrar usuarios y dispositivos**, haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="8ae82-146">On the **Filter users and devices** page, click **Next**.</span></span>
    
14. <span data-ttu-id="8ae82-147">En la página **Características opcionales**, haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="8ae82-147">On the **Optional features** page, click **Next**.</span></span>
    
15. <span data-ttu-id="8ae82-148">En la página **Granja de AD FS**, haga clic en **Configurar una nueva granja de servidores de AD FS**.</span><span class="sxs-lookup"><span data-stu-id="8ae82-148">On the **AD FS farm** page, click **Configure a new AD FS farm**.</span></span>
    
16. <span data-ttu-id="8ae82-149">Haga clic en **Examinar** y especifique la ubicación y el nombre del certificado SSL de la entidad de certificación pública.</span><span class="sxs-lookup"><span data-stu-id="8ae82-149">Click **Browse** and specify the location and name of the SSL certificate from the public certification authority.</span></span>
    
17. <span data-ttu-id="8ae82-150">Cuando se le pida, escriba la contraseña del certificado y, después, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="8ae82-150">When prompted, type the certificate password, and then click **OK**.</span></span>
    
18. <span data-ttu-id="8ae82-151">Compruebe que el **Nombre del firmante** y el **Nombre del servicio de federación** están establecidos en el FQDN de servicio de federación y, después, haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="8ae82-151">Verify that the **Subject Name** and **Federation Service Name** are set to your federation service FQDN, and then click **Next**.</span></span>
    
19. <span data-ttu-id="8ae82-152">En la página **Servidores de AD FS**, escriba el nombre del primer servidor de AD FS (tabla M, elemento 4, columna Nombre de máquina virtual) y, después, haga clic en **Agregar**.</span><span class="sxs-lookup"><span data-stu-id="8ae82-152">On the **AD FS servers** page, type your first AD FS server's name (Table M - Item 4 - Virtual machine name column), and then click **Add**.</span></span>
    
20. <span data-ttu-id="8ae82-153">Escriba el nombre del segundo servidor de AD FS (tabla M, elemento 5, columna Nombre de máquina virtual), haga clic en **Agregar** y, después, haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="8ae82-153">Type your second AD FS server's name (Table M - Item 5 - Virtual machine name column), click **Add**, and then click **Next**.</span></span>
    
21. <span data-ttu-id="8ae82-154">En la página **Servidores de Proxy de aplicación web**, escriba el nombre del primer servidor proxy de aplicación web (tabla M, elemento 6, columna Nombre de máquina virtual) y, después, haga clic en **Agregar**.</span><span class="sxs-lookup"><span data-stu-id="8ae82-154">On the **Web Application Proxy servers** page, type your first web application proxy server's name (Table M - Item 6 - Virtual machine name column), and then click **Add**.</span></span>
    
22. <span data-ttu-id="8ae82-155">Escriba el nombre del segundo servidor proxy de aplicación web (tabla M, elemento 7, columna Nombre de máquina virtual), haga clic en **Agregar** y, después, haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="8ae82-155">Type your second web application proxy server's name (Table M - Item 7 - Virtual machine name column), click **Add**, and then click **Next**.</span></span>
    
23. <span data-ttu-id="8ae82-156">En la página **Credenciales de administrador de dominio**, escriba el nombre de usuario y la contraseña de una cuenta de administrador de dominio y después haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="8ae82-156">On the **Domain Administrator credentials** page, type the user name and password of a domain administrator account, and then click **Next**.</span></span>
    
24. <span data-ttu-id="8ae82-157">En la página **Cuenta del servicio AD FS**, escriba el nombre de usuario y la contraseña de una cuenta de administrador empresarial y después haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="8ae82-157">On the **AD FS service account** page, type the user name and password of an enterprise administrator account, and then click **Next**.</span></span>
    
25. <span data-ttu-id="8ae82-158">En la página **Dominio de Azure AD**, en **Dominio**, seleccione el nombre de dominio DNS de su organización y, después, haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="8ae82-158">On the **Azure AD Domain** page, in **Domain**, select your organization's DNS domain name, and then click **Next**.</span></span>
    
26. <span data-ttu-id="8ae82-159">En la página **Listo para configurar**, haga clic en **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="8ae82-159">On the **Ready to configure** page, click **Install**.</span></span>
    
27. <span data-ttu-id="8ae82-p105">En la página **Instalación completada**, haga clic en **Comprobar**. Debe ver dos mensajes que indican que tanto la configuración de Internet como la de la intranet se han comprobado correctamente.</span><span class="sxs-lookup"><span data-stu-id="8ae82-p105">On the **Installation complete** page, click **Verify**. You should see two messages indicating that both the intranet and Internet configuration was successfully verified.</span></span>
    
  - <span data-ttu-id="8ae82-162">El mensaje de la intranet debe mostrar la dirección IP privada del equilibrador de carga interno de Azure para los servidores de AD FS.</span><span class="sxs-lookup"><span data-stu-id="8ae82-162">The intranet message should list the private IP address of your Azure internal load balancer for your AD FS servers.</span></span>
    
  - <span data-ttu-id="8ae82-163">El mensaje de Internet debe mostrar la dirección IP pública del equilibrador de carga de Azure accesible desde Internet para los servidores proxy de aplicación web.</span><span class="sxs-lookup"><span data-stu-id="8ae82-163">The Internet message should list the public IP address of your Azure Internet-facing load balancer for your web application proxy servers.</span></span>
    
28. <span data-ttu-id="8ae82-164">En la página **Instalación completada**, haga clic en **Salir**.</span><span class="sxs-lookup"><span data-stu-id="8ae82-164">On the **Installation complete** page, click **Exit**.</span></span>
    
<span data-ttu-id="8ae82-165">Esta es la configuración final, con nombres de marcador de posición para los servidores.</span><span class="sxs-lookup"><span data-stu-id="8ae82-165">Here is the final configuration, with placeholder names for the servers.</span></span>
  
<span data-ttu-id="8ae82-166">**Fase 5: Configuración final de una infraestructura de autenticación federada de alta disponibilidad en Azure**</span><span class="sxs-lookup"><span data-stu-id="8ae82-166">**Phase 5: The final configuration of a high availability federated authentication infrastructure in Azure**</span></span>

![La configuración final de la infraestructura de la autenticación federada de Office 365 con alta disponibilidad en Azure](media/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
<span data-ttu-id="8ae82-168">La infraestructura de autenticación federada de alta disponibilidad para Office 365 en Azure está completada.</span><span class="sxs-lookup"><span data-stu-id="8ae82-168">Your high availability federated authentication infrastructure for Office 365 in Azure is complete.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8ae82-169">Vea también</span><span class="sxs-lookup"><span data-stu-id="8ae82-169">See Also</span></span>

[<span data-ttu-id="8ae82-170">Implementar la autenticación federada de alta disponibilidad para Office 365 en Azure</span><span class="sxs-lookup"><span data-stu-id="8ae82-170">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="8ae82-171">Identidad federada para el entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="8ae82-171">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="8ae82-172">Adopción de la nube y soluciones híbridas</span><span class="sxs-lookup"><span data-stu-id="8ae82-172">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="8ae82-173">Identidad federada para Office 365</span><span class="sxs-lookup"><span data-stu-id="8ae82-173">Federated identity for Office 365</span></span>](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)


