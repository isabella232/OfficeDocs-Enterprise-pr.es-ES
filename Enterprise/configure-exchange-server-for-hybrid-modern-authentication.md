---
title: Cómo configurar Exchange Server local para usar la autenticación moderna híbrida
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/16/2018
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: cef3044d-d4cb-4586-8e82-ee97bd3b14ad
ms.collection:
- M365-security-compliance
description: La autenticación moderna híbrida (HMA) es un método de administración de identidades que ofrece autenticación y autorización de usuarios más seguras, y está disponible para las implementaciones híbridas locales de Exchange Server.
ms.openlocfilehash: 1a8bed186acd8da9c5f223120c5e58e8bfd445b4
ms.sourcegitcommit: ef5447665d6ebbc79399b560c9725d74e1479f7d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2020
ms.locfileid: "41122569"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a><span data-ttu-id="426b8-103">Cómo configurar Exchange Server local para usar la autenticación moderna híbrida</span><span class="sxs-lookup"><span data-stu-id="426b8-103">How to configure Exchange Server on-premises to use Hybrid Modern Authentication</span></span>

<span data-ttu-id="426b8-104">*Este artículo se aplica tanto a Office 365 Enterprise como a Microsoft 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="426b8-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="426b8-105">La autenticación moderna híbrida (HMA) es un método de administración de identidades que ofrece autenticación y autorización de usuarios más seguras, y está disponible para las implementaciones híbridas locales de Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="426b8-105">Hybrid Modern Authentication (HMA), is a method of identity management that offers more secure user authentication and authorization, and is available for Exchange server on-premises hybrid deployments.</span></span>
  
## <a name="fyi"></a><span data-ttu-id="426b8-106">FYI</span><span class="sxs-lookup"><span data-stu-id="426b8-106">FYI</span></span>

<span data-ttu-id="426b8-107">Antes de empezar, debo llamar a:</span><span class="sxs-lookup"><span data-stu-id="426b8-107">Before we begin, I call:</span></span>
  
- <span data-ttu-id="426b8-108">HMA de autenticación \> moderna híbrida</span><span class="sxs-lookup"><span data-stu-id="426b8-108">Hybrid Modern Authentication \> HMA</span></span>
    
- <span data-ttu-id="426b8-109">T local \> de Exchange</span><span class="sxs-lookup"><span data-stu-id="426b8-109">Exchange on-premises \> EXCH</span></span>
    
- <span data-ttu-id="426b8-110">Exo de \> Exchange Online</span><span class="sxs-lookup"><span data-stu-id="426b8-110">Exchange Online \> EXO</span></span>
    
<span data-ttu-id="426b8-111">Además, *si un gráfico de este artículo tiene un objeto que está "atenuado" o "atenuado", lo que significa que el elemento que se muestra en gris no se incluye en la configuración específica del HMA* .</span><span class="sxs-lookup"><span data-stu-id="426b8-111">Also,  *if a graphic in this article has an object that's 'grayed-out' or 'dimmed' that means the element shown in gray is not included in HMA-specific configuration*  .</span></span> 
  
## <a name="enabling-hybrid-modern-authentication"></a><span data-ttu-id="426b8-112">Habilitación de la autenticación moderna híbrida</span><span class="sxs-lookup"><span data-stu-id="426b8-112">Enabling Hybrid Modern Authentication</span></span>

<span data-ttu-id="426b8-113">La activación de la HMA significa:</span><span class="sxs-lookup"><span data-stu-id="426b8-113">Turning HMA on means:</span></span>
  
1. <span data-ttu-id="426b8-114">Asegúrese de que cumple los requisitos previos antes de empezar.</span><span class="sxs-lookup"><span data-stu-id="426b8-114">Being sure you meet the prereqs before you begin.</span></span>
    
1. <span data-ttu-id="426b8-115">Dado que muchos **requisitos previos** son comunes para Skype empresarial y Exchange, introducción a la [autenticación moderna híbrida y requisitos previos para su uso con Skype empresarial local y servidores de Exchange](hybrid-modern-auth-overview.md).</span><span class="sxs-lookup"><span data-stu-id="426b8-115">Since many **prerequisites** are common for both Skype for Business and Exchange, [Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers](hybrid-modern-auth-overview.md).</span></span> <span data-ttu-id="426b8-116">Hágalo antes de empezar con cualquiera de los pasos de este artículo.</span><span class="sxs-lookup"><span data-stu-id="426b8-116">Do this before you begin any of the steps in this article.</span></span>
    
2. <span data-ttu-id="426b8-117">Agregar direcciones URL de servicios web locales como nombres principales de servicio (SPN) en Azure AD.</span><span class="sxs-lookup"><span data-stu-id="426b8-117">Adding on-premises web service URLs as Service Principal Names (SPNs) in Azure AD.</span></span>
    
3. <span data-ttu-id="426b8-118">Asegurarse de que todos los directorios virtuales están habilitados para HMA</span><span class="sxs-lookup"><span data-stu-id="426b8-118">Ensuring all Virtual Directories are enabled for HMA</span></span>
    
4. <span data-ttu-id="426b8-119">Comprobación del objeto de servidor de autenticación de EvoSTS</span><span class="sxs-lookup"><span data-stu-id="426b8-119">Checking for the EvoSTS Auth Server object</span></span>
    
5. <span data-ttu-id="426b8-120">Habilitación de la HMA en EXCH</span><span class="sxs-lookup"><span data-stu-id="426b8-120">Enabling HMA in EXCH.</span></span>
    
 <span data-ttu-id="426b8-121">**Nota:** ¿Su versión de Office es compatible con MA?</span><span class="sxs-lookup"><span data-stu-id="426b8-121">**Note** Does your version of Office support MA?</span></span> <span data-ttu-id="426b8-122">Vea [Cómo funciona la autenticación moderna para las aplicaciones cliente de office 2013 y office 2016](modern-auth-for-office-2013-and-2016.md).</span><span class="sxs-lookup"><span data-stu-id="426b8-122">See [How modern authentication works for Office 2013 and Office 2016 client apps](modern-auth-for-office-2013-and-2016.md).</span></span>
  
## <a name="make-sure-you-meet-all-the-pre-reqs"></a><span data-ttu-id="426b8-123">Asegurarse de que cumple todos los requisitos previos</span><span class="sxs-lookup"><span data-stu-id="426b8-123">Make sure you meet all the pre-reqs</span></span>

<span data-ttu-id="426b8-124">Dado que muchos requisitos previos son comunes para Skype empresarial y Exchange, revise la [Introducción a la autenticación moderna híbrida y los requisitos previos para usarlo con Skype empresarial y los servidores de Exchange locales](hybrid-modern-auth-overview.md).</span><span class="sxs-lookup"><span data-stu-id="426b8-124">Since many prerequisites are common for both Skype for Business and Exchange, review [Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers](hybrid-modern-auth-overview.md).</span></span> <span data-ttu-id="426b8-125">Hágalo *antes* de empezar con cualquiera de los pasos de este artículo.</span><span class="sxs-lookup"><span data-stu-id="426b8-125">Do this  *before*  you begin any of the steps in this article.</span></span> 
  
## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a><span data-ttu-id="426b8-126">Agregar direcciones URL de servicios web locales como SPN en Azure AD</span><span class="sxs-lookup"><span data-stu-id="426b8-126">Add on-premises web service URLs as SPNs in Azure AD</span></span>

<span data-ttu-id="426b8-127">Ejecute los comandos que asignan las direcciones URL del servicio Web local como SPN de Azure AD.</span><span class="sxs-lookup"><span data-stu-id="426b8-127">Run the commands that assign your on-premises web service URLs as Azure AD SPNs.</span></span> <span data-ttu-id="426b8-128">Los equipos cliente y los dispositivos usan los SPN durante la autenticación y la autorización.</span><span class="sxs-lookup"><span data-stu-id="426b8-128">SPNs are used by client machines and devices during authentication and authorization.</span></span> <span data-ttu-id="426b8-129">Todas las direcciones URL que se pueden usar para conectarse de local a Azure Active Directory (AAD) deben registrarse en AAD (esto incluye los espacios de nombres internos y externos).</span><span class="sxs-lookup"><span data-stu-id="426b8-129">All the URLs that might be used to connect from on-premises to Azure Active Directory (AAD) must be registered in AAD (this includes both internal and external namespaces).</span></span>
  
<span data-ttu-id="426b8-130">En primer lugar, reúna todas las direcciones URL que necesite agregar en AAD.</span><span class="sxs-lookup"><span data-stu-id="426b8-130">First, gather all the URLs that you need to add in AAD.</span></span> <span data-ttu-id="426b8-131">Ejecute estos comandos de forma local:</span><span class="sxs-lookup"><span data-stu-id="426b8-131">Run these commands on-premises:</span></span>
  
```powershell
Get-MapiVirtualDirectory | FL server,*url*
Get-WebServicesVirtualDirectory | FL server,*url*
Get-ActiveSyncVirtualDirectory | FL server,*url*
Get-OABVirtualDirectory | FL server,*url*
```
    
<span data-ttu-id="426b8-132">Asegúrese de que las direcciones URL a las que se pueden conectar los clientes aparecen como nombres de entidad de servicio HTTPS en AAD.</span><span class="sxs-lookup"><span data-stu-id="426b8-132">Ensure the URLs clients may connect to are listed as HTTPS service principal names in AAD.</span></span>
  
1. <span data-ttu-id="426b8-133">En primer lugar, conéctese a AAD con [estas instrucciones](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span><span class="sxs-lookup"><span data-stu-id="426b8-133">First, connect to AAD with [these instructions](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span></span> 

 <span data-ttu-id="426b8-134">**Nota:** Debe usar la opción Connect-MsolService de esta página para poder usar el comando siguiente.</span><span class="sxs-lookup"><span data-stu-id="426b8-134">**Note** You need to use the Connect-MsolService option from this page to be able to use the command below.</span></span> 
    
2. <span data-ttu-id="426b8-135">Para las direcciones URL relacionadas con Exchange, escriba el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="426b8-135">For your Exchange related URLs, type the following command:</span></span>
    
```powershell
Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | select -ExpandProperty ServicePrincipalNames
```

<span data-ttu-id="426b8-136">Tome nota de (y captura de pantalla para comparaciones posteriores) el resultado de este comando, que debe incluir un https:// *Autodiscover.yourdomain.com* y https:// *mail.yourdomain.com* dirección URL, pero en su mayoría consta de SPN que comienzan con 00000002-0000-0ff1-ce00-000000000000/.</span><span class="sxs-lookup"><span data-stu-id="426b8-136">Take note of (and screenshot for later comparison) the output of this command, which should include an https://  *autodiscover.yourdomain.com*  and https://  *mail.yourdomain.com*  URL, but mostly consist of SPNs that begin with 00000002-0000-0ff1-ce00-000000000000/.</span></span> <span data-ttu-id="426b8-137">Si hay direcciones URL de https://de su local que no se encuentran, tendrá que agregar esos registros específicos a esta lista.</span><span class="sxs-lookup"><span data-stu-id="426b8-137">If there are https:// URLs from your on-premises that are missing we will need to add those specific records to this list.</span></span> 
  
3. <span data-ttu-id="426b8-138">Si no ve los registros interno y externo de MAPI/HTTP, EWS, ActiveSync, OAB y detección automática en esta lista, debe agregarlos mediante el siguiente comando (las direcciones URL de ejemplo son`mail.corp.contoso.com`' ' y`owa.contoso.com`' '), pero debe **reemplazar las direcciones URL de ejemplo con las suyas** :</span><span class="sxs-lookup"><span data-stu-id="426b8-138">If you don't see your internal and external MAPI/HTTP, EWS, ActiveSync, OAB and Autodiscover records in this list, you must add them using the command below (the example URLs are '`mail.corp.contoso.com`' and '`owa.contoso.com`', but you'd **replace the example URLs with your own** ):</span></span> <br/>
```powershell
$x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000   
$x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
$x.ServicePrincipalnames.Add("https://owa.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
 
4. <span data-ttu-id="426b8-139">Compruebe que los nuevos registros se han agregado ejecutando el comando Get-MsolServicePrincipal del paso 2 de nuevo y observando los resultados.</span><span class="sxs-lookup"><span data-stu-id="426b8-139">Verify your new records were added by running the Get-MsolServicePrincipal command from step 2 again, and looking through the output.</span></span> <span data-ttu-id="426b8-140">Compare la lista o la captura de pantalla de antes con la nueva lista de SPN (también puede mostrar una captura de pantalla de la nueva lista de sus registros).</span><span class="sxs-lookup"><span data-stu-id="426b8-140">Compare the list / screenshot from before to the new list of SPNs (you may also screenshot the new list for your records).</span></span> <span data-ttu-id="426b8-141">Si ha tenido éxito, verá las dos nuevas direcciones URL en la lista.</span><span class="sxs-lookup"><span data-stu-id="426b8-141">If you were successful, you will see the two new URLs in the list.</span></span> <span data-ttu-id="426b8-142">Siguiendo nuestro ejemplo, la lista de SPN ahora incluirá las direcciones URL `https://mail.corp.contoso.com` específicas y `https://owa.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="426b8-142">Going by our example, the list of SPNs will now include the specific URLs  `https://mail.corp.contoso.com`  and  `https://owa.contoso.com`.</span></span> 
  
## <a name="verify-virtual-directories-are-properly-configured"></a><span data-ttu-id="426b8-143">Comprobar que los directorios virtuales están correctamente configurados</span><span class="sxs-lookup"><span data-stu-id="426b8-143">Verify Virtual Directories are Properly Configured</span></span>

<span data-ttu-id="426b8-144">Ahora, compruebe que OAuth está correctamente habilitado en Exchange en todos los directorios virtuales que Outlook puede usar mediante la ejecución de los siguientes comandos:</span><span class="sxs-lookup"><span data-stu-id="426b8-144">Now verify OAuth is properly enabled in Exchange on all of the Virtual Directories Outlook might use by running the following commands:</span></span>

```powershell
Get-MapiVirtualDirectory | FL server,*url*,*auth* 
Get-WebServicesVirtualDirectory | FL server,*url*,*oauth*
Get-OABVirtualDirectory | FL server,*url*,*oauth*
Get-AutoDiscoverVirtualDirectory | FL server,*oauth*
```

<span data-ttu-id="426b8-145">Compruebe el resultado para asegurarse de que **OAuth** está habilitado en cada uno de estos VDirs, que tendrá un aspecto similar al siguiente (y que el elemento clave que debe analizar es "OAuth");</span><span class="sxs-lookup"><span data-stu-id="426b8-145">Check the output to make sure **OAuth** is enabled on each of these VDirs, it will look something like this (and the key thing to look at is 'OAuth');</span></span> 

```powershell
Get-MapiVirtualDirectory | fl server,*url*,*auth*
```

```
Server                        : EX1
InternalUrl                   : https://mail.contoso.com/mapi
ExternalUrl                   : https://mail.contoso.com/mapi
IISAuthenticationMethods      : {Ntlm, OAuth, Negotiate}
InternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
ExternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
```
  
<span data-ttu-id="426b8-146">Si OAuth no está en ningún servidor y en cualquiera de los cuatro directorios virtuales, debe agregarlo con los comandos relevantes antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="426b8-146">If OAuth is missing from any server and any of the four virtual directories then you need to add it using the relevant commands before proceeding.</span></span>
  
## <a name="confirm-the-evosts-auth-server-object-is-present"></a><span data-ttu-id="426b8-147">Confirmar que el objeto de servidor de autenticación de EvoSTS está presente</span><span class="sxs-lookup"><span data-stu-id="426b8-147">Confirm the EvoSTS Auth Server Object is Present</span></span>

<span data-ttu-id="426b8-148">Vuelva al shell de administración de Exchange local para este último comando.</span><span class="sxs-lookup"><span data-stu-id="426b8-148">Return to the on-premises Exchange Management Shell for this last command.</span></span> <span data-ttu-id="426b8-149">Ahora puede validar que su entorno local tiene una entrada para el proveedor de autenticación de evoSTS:</span><span class="sxs-lookup"><span data-stu-id="426b8-149">Now you can validate that your on-premises has an entry for the evoSTS authentication provider:</span></span>
  
```powershell
Get-AuthServer | where {$_.Name -eq "EvoSts"}
```

<span data-ttu-id="426b8-150">El resultado debe mostrar un AuthServer del nombre EvoSts y el estado "habilitado" debe ser true.</span><span class="sxs-lookup"><span data-stu-id="426b8-150">Your output should show an AuthServer of the Name EvoSts and the 'Enabled' state should be True.</span></span> <span data-ttu-id="426b8-151">Si no ve esto, debe descargar y ejecutar la versión más reciente del Asistente para la configuración híbrida.</span><span class="sxs-lookup"><span data-stu-id="426b8-151">If you don't see this, you should download and run the most recent version of the Hybrid Configuration Wizard.</span></span>
  
 <span data-ttu-id="426b8-152">**Importante** Si está ejecutando Exchange 2010 en su entorno, no se creará el proveedor de autenticación EvoSTS.</span><span class="sxs-lookup"><span data-stu-id="426b8-152">**Important** If you're running Exchange 2010 in your environment, the EvoSTS authentication provider won't be created.</span></span> 
  
## <a name="enable-hma"></a><span data-ttu-id="426b8-153">Habilitar HMA</span><span class="sxs-lookup"><span data-stu-id="426b8-153">Enable HMA</span></span>

<span data-ttu-id="426b8-154">Ejecute el siguiente comando en el shell de administración de Exchange, local:</span><span class="sxs-lookup"><span data-stu-id="426b8-154">Run the following command in the Exchange Management Shell, on-premises:</span></span>

```powershell
Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true  
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```
    
## <a name="verify"></a><span data-ttu-id="426b8-155">Comprueba</span><span class="sxs-lookup"><span data-stu-id="426b8-155">Verify</span></span>

<span data-ttu-id="426b8-156">Una vez habilitada la HMA, el próximo inicio de sesión de un cliente usará el nuevo flujo de autenticación.</span><span class="sxs-lookup"><span data-stu-id="426b8-156">Once you enable HMA, a client's next login will use the new auth flow.</span></span> <span data-ttu-id="426b8-157">Tenga en cuenta que, al activar la HMA no se activará una nueva autenticación para ningún cliente.</span><span class="sxs-lookup"><span data-stu-id="426b8-157">Note that just turning on HMA won't trigger a re-authentication for any client.</span></span> <span data-ttu-id="426b8-158">Los clientes se vuelven a autenticar en función de la duración de los tokens de autenticación o de los certificados que tienen.</span><span class="sxs-lookup"><span data-stu-id="426b8-158">The clients re-authenticate based on the lifetime of the auth tokens and/or certs they have.</span></span>
  
<span data-ttu-id="426b8-159">También debe mantener presionada la tecla CTRL al mismo tiempo que se hace clic en el icono del cliente de Outlook (también en la bandeja de notificaciones de Windows) y en "estado de conexión".</span><span class="sxs-lookup"><span data-stu-id="426b8-159">You should also hold down the CTRL key at the same time you right click the icon for the Outlook client (also in the Windows Notifications tray) and click 'Connection Status'.</span></span> <span data-ttu-id="426b8-160">Busque la dirección SMTP del cliente en un "authn" tipo de "portador\*", que representa el token del portador usado en OAuth.</span><span class="sxs-lookup"><span data-stu-id="426b8-160">Look for the client's SMTP address against an 'Authn' type of 'Bearer\*', which represents the bearer token used in OAuth.</span></span>
  
 <span data-ttu-id="426b8-161">**Nota:** ¿Necesita configurar Skype empresarial con HMA?</span><span class="sxs-lookup"><span data-stu-id="426b8-161">**Note** Need to configure Skype for Business with HMA?</span></span> <span data-ttu-id="426b8-162">Necesitará dos artículos: uno que muestre las [topologías admitidas](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)y otro que muestre [Cómo realizar la configuración](configure-skype-for-business-for-hybrid-modern-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="426b8-162">You'll need two articles: One that lists [supported topologies](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported), and one that shows you [how to do the configuration](configure-skype-for-business-for-hybrid-modern-authentication.md).</span></span>
 
## <a name="using-hybrid-modern-authentication-with-outlook-for-ios-and-android"></a><span data-ttu-id="426b8-163">Uso de híbridos modernos de autenticación con Outlook para iOS y Android</span><span class="sxs-lookup"><span data-stu-id="426b8-163">Using hybrid Modern Authentication with Outlook for iOS and Android</span></span>

<span data-ttu-id="426b8-164">Si es un cliente local que usa Exchange Server en TCP 443, debe tener en la lista blanca los siguientes intervalos de direcciones IP: </span><span class="sxs-lookup"><span data-stu-id="426b8-164">If you are an on-premises customer using Exchange server on TCP 443, please whitelist the following IP ranges:  </span></span><BR> ```52.125.128.0/20``` <BR> ```52.127.96.0/23``` <BR> 
  

## <a name="related-topics"></a><span data-ttu-id="426b8-165">Temas relacionados</span><span class="sxs-lookup"><span data-stu-id="426b8-165">Related topics</span></span>

[<span data-ttu-id="426b8-166">Introducción a la autenticación moderna híbrida y requisitos previos para su uso con servidores locales de Skype empresarial y Exchange</span><span class="sxs-lookup"><span data-stu-id="426b8-166">Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers</span></span>](hybrid-modern-auth-overview.md) 
  
<span data-ttu-id="426b8-167">Obligar a los usuarios de Outlook a realizar la autenticación moderna</span><span class="sxs-lookup"><span data-stu-id="426b8-167">Force Outlook users to Modern Authentication</span></span>  
[<span data-ttu-id="426b8-168">Requisitos de configuración de autenticación moderna para la transición de Office 365 dedicado/ITAR a vNext</span><span class="sxs-lookup"><span data-stu-id="426b8-168">Modern Authentication configuration requirements for transition from Office 365 dedicated/ITAR to vNext</span></span>](modern-authentication-configuration.md)
