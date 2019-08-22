---
title: Cómo configurar Skype Empresarial local para usar la autenticación moderna híbrida
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/4/2018
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 522d5cec-4e1b-4cc3-937f-293570717bc6
ms.collection:
- M365-security-compliance
description: La autenticación moderna es un método de administración de identidades que ofrece autenticación y autorización de usuarios más seguras, está disponible para Skype empresarial Server local y Exchange Server local, así como para entornos híbridos de dominio dividido de Skype empresarial.
ms.openlocfilehash: 5db33a39ff58ae2aa21968c2f092c8ac29af5681
ms.sourcegitcommit: c8acfa57a22d7d055500f2e8b84a9ef252c70e82
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2019
ms.locfileid: "36493337"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a><span data-ttu-id="8dfb8-103">Cómo configurar Skype Empresarial local para usar la autenticación moderna híbrida</span><span class="sxs-lookup"><span data-stu-id="8dfb8-103">How to configure Skype for Business on-premises to use Hybrid Modern Authentication</span></span>

<span data-ttu-id="8dfb8-104">La autenticación moderna es un método de administración de identidades que ofrece autenticación y autorización de usuarios más seguras, está disponible para Skype empresarial Server local y Exchange Server local, así como para entornos híbridos de dominio dividido de Skype empresarial.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-104">Modern Authentication, is a method of identity management that offers more secure user authentication and authorization, is available for Skype for Business server on-premises and Exchange server on-premises, as well as split-domain Skype for Business hybrids.</span></span>
  
 <span data-ttu-id="8dfb8-105">**Importante** ¿Le gustaría saber más sobre la autenticación moderna (MA) y por qué prefiere usarla en su empresa u organización?</span><span class="sxs-lookup"><span data-stu-id="8dfb8-105">**Important** Would you like to know more about Modern Authentication (MA) and why you might prefer to use it in your company or organization?</span></span> <span data-ttu-id="8dfb8-106">Consulte [este documento](hybrid-modern-auth-overview.md) para obtener información general.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-106">Check [this document](hybrid-modern-auth-overview.md) for an overview.</span></span> <span data-ttu-id="8dfb8-107">Si necesita saber qué topologías de Skype empresarial son compatibles con MA, esto se documenta aquí.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-107">If you need to know what Skype for Business topologies are supported with MA, that's documented here!</span></span> 
  
 <span data-ttu-id="8dfb8-108">**Antes de empezar**, debo llamar a:</span><span class="sxs-lookup"><span data-stu-id="8dfb8-108">**Before we begin**, I call:</span></span> 
  
- <span data-ttu-id="8dfb8-109">MA de \> autenticación moderna</span><span class="sxs-lookup"><span data-stu-id="8dfb8-109">Modern Authentication \> MA</span></span>
    
- <span data-ttu-id="8dfb8-110">HMA de autenticación \> moderna híbrida</span><span class="sxs-lookup"><span data-stu-id="8dfb8-110">Hybrid Modern Authentication \> HMA</span></span>
    
- <span data-ttu-id="8dfb8-111">T local \> de Exchange</span><span class="sxs-lookup"><span data-stu-id="8dfb8-111">Exchange on-premises \> EXCH</span></span>
    
- <span data-ttu-id="8dfb8-112">Exo de \> Exchange Online</span><span class="sxs-lookup"><span data-stu-id="8dfb8-112">Exchange Online \> EXO</span></span>
    
- <span data-ttu-id="8dfb8-113">Skype empresarial local \> SFB</span><span class="sxs-lookup"><span data-stu-id="8dfb8-113">Skype for Business on-premises \> SFB</span></span>
    
- <span data-ttu-id="8dfb8-114">y Skype empresarial online \> SFBO</span><span class="sxs-lookup"><span data-stu-id="8dfb8-114">and Skype for Business Online \> SFBO</span></span>
    
<span data-ttu-id="8dfb8-115">Además, \* si un gráfico de este artículo tiene un objeto que está "atenuado" o "atenuado", significa que el elemento que se muestra en gris **no se** incluye en la configuración específica de ma.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-115">Also,  \*if a graphic in this article has an object that's 'grayed-out' or 'dimmed' that means the element shown in gray **is not** included in MA-specific configuration.</span></span> * 
  
## <a name="read-the-summary"></a><span data-ttu-id="8dfb8-116">Leer el Resumen</span><span class="sxs-lookup"><span data-stu-id="8dfb8-116">Read the summary</span></span>

<span data-ttu-id="8dfb8-117">Este Resumen reduce el proceso en pasos que, de lo contrario, podrían perderse durante la ejecución y es conveniente para una lista de comprobación global para realizar un seguimiento de la ubicación en la que se encuentra en el proceso.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-117">This summary boils the process into steps that might otherwise get lost during the execution, and is good for an overall check-list to keep track of where you are in the process.</span></span>
  
1. <span data-ttu-id="8dfb8-118">En primer lugar, asegúrese de que cumple todos los requisitos previos.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-118">First, make sure you meet all the prerequisites.</span></span>
    
1. <span data-ttu-id="8dfb8-119">Dado que muchos de los **requisitos previos** son comunes para Skype empresarial y Exchange, [consulte el artículo de información general para obtener una lista de comprobación previa a la solicitud](hybrid-modern-auth-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8dfb8-119">Since many **prerequisites** are common for both Skype for Business and Exchange, [see the overview article for your pre-req checklist](hybrid-modern-auth-overview.md).</span></span> <span data-ttu-id="8dfb8-120">Hágalo *antes* de empezar con cualquiera de los pasos de este artículo.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-120">Do this  *before*  you begin any of the steps in this article.</span></span> 
    
2. <span data-ttu-id="8dfb8-121">Recopile la información específica del HMA que necesitará en un archivo o en OneNote.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-121">Collect the HMA-specific info you'll need in a file, or OneNote.</span></span>
    
3. <span data-ttu-id="8dfb8-122">Active la autenticación moderna para EXO (si aún no está activada).</span><span class="sxs-lookup"><span data-stu-id="8dfb8-122">Turn ON Modern Authentication for EXO (if it is not already turned on).</span></span>
    
4. <span data-ttu-id="8dfb8-123">Active la autenticación moderna para SFBO (si aún no está activada).</span><span class="sxs-lookup"><span data-stu-id="8dfb8-123">Turn ON Modern Authentication for SFBO (if it is not already turned on).</span></span>
    
5. <span data-ttu-id="8dfb8-124">Active la autenticación moderna híbrida para Exchange local.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-124">Turn ON Hybrid Modern Authentication for Exchange on-premises.</span></span>
    
6. <span data-ttu-id="8dfb8-125">Active la autenticación moderna híbrida para Skype empresarial local.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-125">Turn ON Hybrid Modern Authentication for Skype for Business on-premises.</span></span>
    
<span data-ttu-id="8dfb8-126">Nota estos pasos activan MA para SFB, SFBO, EXCH y EXO--es decir, todos los productos que pueden participar en una configuración de HMA de SFB y SFBO (incluidas las dependencias de EXCH/EXO).</span><span class="sxs-lookup"><span data-stu-id="8dfb8-126">Note These steps turn on MA for SFB, SFBO, EXCH, and EXO -- that is, all the products that can participate in a HMA configuration of SFB and SFBO (including dependencies on EXCH/EXO).</span></span> <span data-ttu-id="8dfb8-127">En otras palabras, si los usuarios están hospedados en o tienen buzones creados en cualquier parte del híbrido (EXO + SFBO, EXO + SFB, EXCH + SFBO o EXCH + SFB), el producto terminado tendrá el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="8dfb8-127">In other words, if your users are homed in/have mailboxes created in any part of the Hybrid (EXO + SFBO, EXO + SFB, EXCH + SFBO, or EXCH + SFB), your finished product will look like this:</span></span>
  
![Una topología de HMA de Skype empresarial de 6 mixtas tiene MA activada en las cuatro ubicaciones posibles.](media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)
  
<span data-ttu-id="8dfb8-129">Como puede ver, hay cuatro lugares distintos para activar MA.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-129">As you can see there are four different places to turn on MA!</span></span> <span data-ttu-id="8dfb8-130">Para obtener la mejor experiencia de usuario, se recomienda activar MA en cuatro de estas ubicaciones.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-130">For the best user experience we recommend you turn on MA in all four of these locations.</span></span> <span data-ttu-id="8dfb8-131">Si no puede activar MA en todas estas ubicaciones, ajuste los pasos para que Active MA solo en las ubicaciones necesarias para su entorno.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-131">If you can't turn MA on in all these locations, adjust the steps so that you turn on MA only in the locations that are necessary for your environment.</span></span>
  
<span data-ttu-id="8dfb8-132">Vea el [tema sobre compatibilidad de Skype empresarial con Ma](https://technet.microsoft.com/en-us/library/mt803262.aspx) para topologías compatibles.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-132">See the [Supportability topic for Skype for Business with MA](https://technet.microsoft.com/en-us/library/mt803262.aspx) for supported topologies.</span></span> 
  
 <span data-ttu-id="8dfb8-133">**Importante** Compruebe que ha cumplido todos los requisitos previos antes de comenzar.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-133">**Important** Double-check that you've met all the prerequisites before you begin.</span></span> <span data-ttu-id="8dfb8-134">Encontrará esta información [aquí](hybrid-modern-auth-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8dfb8-134">You'll find that information [here](hybrid-modern-auth-overview.md).</span></span>
  
## <a name="collect-all-hma-specific-info-youll-need"></a><span data-ttu-id="8dfb8-135">Recopilar toda la información específica de la HMA que tendrás</span><span class="sxs-lookup"><span data-stu-id="8dfb8-135">Collect all HMA-specific info you'll need</span></span>

<span data-ttu-id="8dfb8-136">Una vez que haya comprobado que cumple los [requisitos previos](hybrid-modern-auth-overview.md) para usar la autenticación moderna (consulte la nota anterior), debe crear un archivo que contenga la información que necesitará para configurar HMA en los pasos venideros.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-136">After you've double-checked that you meet the [prerequisites](hybrid-modern-auth-overview.md) to use Modern Authentication (see the note above), you should create a file to hold the info you'll need for configuring HMA in the steps ahead.</span></span> <span data-ttu-id="8dfb8-137">Ejemplos que se usan en este artículo:</span><span class="sxs-lookup"><span data-stu-id="8dfb8-137">Examples used in this article:</span></span> 
  
- <span data-ttu-id="8dfb8-138">**Dominio SIP/SMTP**</span><span class="sxs-lookup"><span data-stu-id="8dfb8-138">**SIP/SMTP domain**</span></span>
    
  - <span data-ttu-id="8dfb8-139">Precio.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-139">Ex.</span></span> <span data-ttu-id="8dfb8-140">contoso.com (se ha federado con Office 365)</span><span class="sxs-lookup"><span data-stu-id="8dfb8-140">contoso.com (is federated with Office 365)</span></span>
    
- <span data-ttu-id="8dfb8-141">**IDENTIFICADOR de inquilino**</span><span class="sxs-lookup"><span data-stu-id="8dfb8-141">**Tenant ID**</span></span>
    
  - <span data-ttu-id="8dfb8-142">El GUID que representa el inquilino de Office 365 (en el inicio de sesión de contoso.onmicrosoft.com).</span><span class="sxs-lookup"><span data-stu-id="8dfb8-142">The GUID that represents your Office 365 tenant (at the login of contoso.onmicrosoft.com).</span></span>
    
- <span data-ttu-id="8dfb8-143">**Direcciones URL del servicio Web SFB 2015 CU5**</span><span class="sxs-lookup"><span data-stu-id="8dfb8-143">**SFB 2015 CU5 Web Service URLs**</span></span>
    
<span data-ttu-id="8dfb8-144">Necesitará direcciones URL de servicios Web internos y externos para todos los grupos de SfB 2015 que se implementen.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-144">You will need internal and external web service URL's for all SfB 2015 pools deployed.</span></span> <span data-ttu-id="8dfb8-145">Para obtenerlos, ejecute lo siguiente desde Shell de administración de Skype empresarial:</span><span class="sxs-lookup"><span data-stu-id="8dfb8-145">To obtain these, run the following from Skype for Business Management Shell:</span></span>
  
```
Get-CsService -WebServer | Select-Object PoolFqdn, InternalFqdn, ExternalFqdn | FL
```

- <span data-ttu-id="8dfb8-146">Precio.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-146">Ex.</span></span> <span data-ttu-id="8dfb8-147">Internoshttps://lyncwebint01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="8dfb8-147">Internal: https://lyncwebint01.contoso.com</span></span>
    
- <span data-ttu-id="8dfb8-148">Precio.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-148">Ex.</span></span> <span data-ttu-id="8dfb8-149">Exteriorhttps://lyncwebext01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="8dfb8-149">External: https://lyncwebext01.contoso.com</span></span>
    
<span data-ttu-id="8dfb8-150">Si usa un servidor Standard Edition, la dirección URL interna estará en blanco.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-150">If you are using a Standard Edition server, the internal URL will be blank.</span></span> <span data-ttu-id="8dfb8-151">En este caso, use el FQDN del grupo de servidores para la dirección URL interna.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-151">In this case, use the pool fqdn for the internal URL.</span></span>
  
## <a name="turn-on-modern-authentication-for-exo"></a><span data-ttu-id="8dfb8-152">Activar la autenticación moderna para EXO</span><span class="sxs-lookup"><span data-stu-id="8dfb8-152">Turn on Modern Authentication for EXO</span></span>

<span data-ttu-id="8dfb8-153">Siga las instrucciones que se indican aquí: [Exchange Online: Cómo habilitar el inquilino para la autenticación moderna.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)</span><span class="sxs-lookup"><span data-stu-id="8dfb8-153">Follow the instructions here: [Exchange Online: How to enable your tenant for modern authentication.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)</span></span>
  
## <a name="turn-on-modern-authentication-for-sfbo"></a><span data-ttu-id="8dfb8-154">Activar la autenticación moderna para SFBO</span><span class="sxs-lookup"><span data-stu-id="8dfb8-154">Turn on Modern Authentication for SFBO</span></span>

<span data-ttu-id="8dfb8-155">Siga las instrucciones que se indican aquí: [Skype empresarial online: habilitar el espacio empresarial para la autenticación moderna](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).</span><span class="sxs-lookup"><span data-stu-id="8dfb8-155">Follow the instructions here: [Skype for Business Online: Enable your tenant for modern authentication](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a><span data-ttu-id="8dfb8-156">Activar la autenticación moderna híbrida para Exchange local</span><span class="sxs-lookup"><span data-stu-id="8dfb8-156">Turn on Hybrid Modern Authentication for Exchange on-premises</span></span>

<span data-ttu-id="8dfb8-157">Siga las instrucciones que se indican a continuación: [Cómo configurar Exchange Server local para usar la autenticación moderna híbrida](configure-exchange-server-for-hybrid-modern-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="8dfb8-157">Follow the instructions here: [How to configure Exchange Server on-premises to use Hybrid Modern Authentication](configure-exchange-server-for-hybrid-modern-authentication.md).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a><span data-ttu-id="8dfb8-158">Activar la autenticación moderna híbrida para Skype empresarial local</span><span class="sxs-lookup"><span data-stu-id="8dfb8-158">Turn on Hybrid Modern Authentication for Skype for Business on-premises</span></span>

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a><span data-ttu-id="8dfb8-159">Agregar direcciones URL de servicios web locales como SPN en Azure AD</span><span class="sxs-lookup"><span data-stu-id="8dfb8-159">Add on-premises web service URLs as SPNs in Azure AD</span></span>

<span data-ttu-id="8dfb8-160">Ahora deberá ejecutar comandos para agregar las direcciones URL (recopiladas anteriormente) como entidades de servicio en SFBO.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-160">Now you'll need to run commands to add the URLs (collected earlier) as Service Principals in SFBO.</span></span>
  
 <span data-ttu-id="8dfb8-161">**Nota:** Los nombres de entidad de seguridad de servicio (SPN) identifican los servicios web y los asocian a una entidad de seguridad (como un grupo o nombre de cuenta) para que el servicio pueda actuar en nombre de un usuario autorizado.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-161">**Note** Service principal names (SPNs) identify web services and associate them with a security principal (such as an account name or group) so that the service can act on the behalf of an authorized user.</span></span> <span data-ttu-id="8dfb8-162">Los clientes que se autentican en un servidor usan la información contenida en los SPN.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-162">Clients authenticating to a server make use of information that's contained in SPNs.</span></span> 
  
1. <span data-ttu-id="8dfb8-163">En primer lugar, conéctese a AAD con [estas instrucciones](https://docs.microsoft.com/en-us/powershell/azure/active-directory/overview?view=azureadps-1.0).</span><span class="sxs-lookup"><span data-stu-id="8dfb8-163">First, connect to AAD with [these instructions](https://docs.microsoft.com/en-us/powershell/azure/active-directory/overview?view=azureadps-1.0).</span></span>
    
2. <span data-ttu-id="8dfb8-164">Ejecute este comando, local, para obtener una lista de las direcciones URL del servicio Web de SFB.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-164">Run this command, on-premises, to get a list of SFB web service URLs.</span></span>

   <span data-ttu-id="8dfb8-165">Tenga en cuenta que el AppPrincipalId `00000004`comienza con.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-165">Note that the AppPrincipalId begins with `00000004`.</span></span> <span data-ttu-id="8dfb8-166">Esto corresponde a Skype empresarial online.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-166">This corresponds to Skype for Business Online.</span></span>
    
   <span data-ttu-id="8dfb8-167">Tome nota de (y captura de pantalla para comparaciones posteriores) el resultado de este comando, que incluirá una dirección URL de SE y WS, pero en `00000004-0000-0ff1-ce00-000000000000/`su mayoría constará de los SPN que comienzan con.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-167">Take note of (and screenshot for later comparison) the output of this command, which will include an SE and WS URL, but mostly consist of SPNs that begin with `00000004-0000-0ff1-ce00-000000000000/`.</span></span>
    
```
Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Select -ExpandProperty ServicePrincipalNames
```
    
3. <span data-ttu-id="8dfb8-168">Si faltan las URL de SFB internas **o** externas de local (por ejemplo, https://lyncwebint01.contoso.com https://lyncwebext01.contoso.com) se deben agregar esos registros específicos a esta lista.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-168">If the internal **or** external SFB URLs from on-premises are missing (for example, https://lyncwebint01.contoso.com and https://lyncwebext01.contoso.com) we will need to add those specific records to this list.</span></span> 
    
    <span data-ttu-id="8dfb8-169">Asegúrese de reemplazar *las direcciones URL de ejemplo* , a continuación, con las direcciones URL reales en el comando Agregar comandos!</span><span class="sxs-lookup"><span data-stu-id="8dfb8-169">Be sure to replace  *the example URLs*  , below, with your actual URLs in the Add commands!</span></span> 
  
```  
$x= Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000
$x.ServicePrincipalnames.Add("https://lyncwebint01.contoso.com/")
$x.ServicePrincipalnames.Add("https://lyncwebext01.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
  
4. <span data-ttu-id="8dfb8-170">Compruebe que los nuevos registros se han agregado ejecutando el comando Get-MsolServicePrincipal del paso 2 de nuevo y observando los resultados.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-170">Verify your new records were added by running the Get-MsolServicePrincipal command from step 2 again, and looking through the output.</span></span> <span data-ttu-id="8dfb8-171">Compare la lista o la captura de pantalla de antes con la nueva lista de SPN (también puede mostrar una captura de pantalla de la nueva lista de sus registros).</span><span class="sxs-lookup"><span data-stu-id="8dfb8-171">Compare the list / screenshot from before to the new list of SPNs (you may also screenshot the new list for your records).</span></span> <span data-ttu-id="8dfb8-172">Si ha tenido éxito, verá las dos nuevas direcciones URL en la lista.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-172">If you were successful, you will see the two new URLs in the list.</span></span> <span data-ttu-id="8dfb8-173">Siguiendo nuestro ejemplo, la lista de SPN ahora incluirá las direcciones URL https://lyncweb01.contoso.com específicas y https://lyncwebext01.contoso.com/.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-173">Going by our example, the list of SPNs will now include the specific URLs https://lyncweb01.contoso.com and https://lyncwebext01.contoso.com/.</span></span>
    
### <a name="create-the-evosts-auth-server-object"></a><span data-ttu-id="8dfb8-174">Crear el objeto de servidor de autenticación de EvoSTS</span><span class="sxs-lookup"><span data-stu-id="8dfb8-174">Create the EvoSTS Auth Server Object</span></span>

<span data-ttu-id="8dfb8-175">Ejecute el siguiente comando en el shell de administración de Skype empresarial.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-175">Run the following command in the Skype for Business Management Shell.</span></span>
  
```
New-CsOAuthServer -Identity evoSTS -MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml -AcceptSecurityIdentifierInformation $true -Type AzureAD
```
    
### <a name="enable-hybrid-modern-authentication"></a><span data-ttu-id="8dfb8-176">Habilitar la autenticación moderna híbrida</span><span class="sxs-lookup"><span data-stu-id="8dfb8-176">Enable Hybrid Modern Authentication</span></span>

<span data-ttu-id="8dfb8-177">Este es el paso que realmente activa MA.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-177">This is the step that actually turns MA on.</span></span> <span data-ttu-id="8dfb8-178">Todos los pasos anteriores se pueden ejecutar con antelación sin cambiar el flujo de autenticación del cliente.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-178">All the previous steps can be run ahead of time without changing the client authentication flow.</span></span> <span data-ttu-id="8dfb8-179">Cuando esté listo para cambiar el flujo de autenticación, ejecute este comando en el shell de administración de Skype empresarial.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-179">When you are ready to change the authentication flow, run this command in the Skype for Business Management Shell.</span></span> 
  
```
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity evoSTS
```
    
## <a name="verify"></a><span data-ttu-id="8dfb8-180">Comprueba</span><span class="sxs-lookup"><span data-stu-id="8dfb8-180">Verify</span></span>

<span data-ttu-id="8dfb8-181">Una vez habilitada la HMA, el próximo inicio de sesión de un cliente usará el nuevo flujo de autenticación.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-181">Once you enable HMA, a client's next login will use the new auth flow.</span></span> <span data-ttu-id="8dfb8-182">Tenga en cuenta que, al activar la HMA no se activará una nueva autenticación para ningún cliente.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-182">Note that just turning on HMA won't trigger a re-authentication for any client.</span></span> <span data-ttu-id="8dfb8-183">Los clientes se vuelven a autenticar en función de la duración de los tokens de autenticación o de los certificados que tienen.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-183">The clients re-authenticate based on the lifetime of the auth tokens and/or certs they have.</span></span>
  
<span data-ttu-id="8dfb8-184">Para probar que la HMA funciona después de habilitarla, cierre la sesión del cliente de Windows SFB y haga clic en "eliminar mis credenciales".</span><span class="sxs-lookup"><span data-stu-id="8dfb8-184">To test that HMA is working after you've enabled it, sign out of a test SFB Windows client and be sure to click 'delete my credentials'.</span></span> <span data-ttu-id="8dfb8-185">Vuelva a iniciar sesión.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-185">Sign in again.</span></span> <span data-ttu-id="8dfb8-186">Ahora, el cliente debe usar el flujo de autenticación moderna y el inicio de sesión incluirá un mensaje de **Office 365** para una cuenta de trabajo o escuela, visto justo antes de que el cliente se pone en contacto con el servidor e inicie sesión.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-186">The client should now use the Modern Auth flow and your login will now include an **Office 365** prompt for a 'Work or school' account, seen right before the client contacts the server and logs you in.</span></span> 
  
<span data-ttu-id="8dfb8-187">También debe comprobar la "información de configuración" para los clientes de Skype empresarial para una "entidad de OAuth".</span><span class="sxs-lookup"><span data-stu-id="8dfb8-187">You should also check the 'Configuration Information' for Skype for Business Clients for an 'OAuth Authority'.</span></span> <span data-ttu-id="8dfb8-188">Para hacer esto en el equipo cliente, mantenga presionada la tecla CTRL al mismo tiempo que hace clic con el botón secundario en el icono de Skype empresarial en la bandeja de notificaciones de Windows.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-188">To do this on your client computer, hold down the CTRL key at the same time you right-click the Skype for Business Icon in the Windows Notification tray.</span></span> <span data-ttu-id="8dfb8-189">Haga clic en información de configuración en el menú que aparece.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-189">Click Configuration Information in the menu that appears.</span></span> <span data-ttu-id="8dfb8-190">En la ventana ' información de configuración de Skype empresarial ' que aparecerá en el escritorio, busque lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="8dfb8-190">In the 'Skype for Business Configuration Information' window that will appear on the desktop, look for the following:</span></span>
  
![La información de configuración de un cliente de Skype empresarial mediante autenticación moderna muestra una dirección URL de la entidad de https://login.windows.net/common/oauth2/authorizeOAUTH de Lync y EWS de.](media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png)
  
<span data-ttu-id="8dfb8-192">También debe mantener presionada la tecla CTRL al mismo tiempo que se hace clic en el icono del cliente de Outlook (también en la bandeja de notificaciones de Windows) y en "estado de conexión".</span><span class="sxs-lookup"><span data-stu-id="8dfb8-192">You should also hold down the CTRL key at the same time you right click the icon for the Outlook client (also in the Windows Notifications tray) and click 'Connection Status'.</span></span> <span data-ttu-id="8dfb8-193">Busque la dirección SMTP del cliente en un tipo de "portador\*" de authn, que representa el token del portador usado en OAuth.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-193">Look for the client's SMTP address against an Authn type of 'Bearer\*', which represents the bearer token used in OAuth.</span></span>
  
## <a name="related-articles"></a><span data-ttu-id="8dfb8-194">Artículos relacionados</span><span class="sxs-lookup"><span data-stu-id="8dfb8-194">Related articles</span></span>

<span data-ttu-id="8dfb8-195">[Vínculo volver a la introducción a la autenticación moderna](hybrid-modern-auth-overview.md) .</span><span class="sxs-lookup"><span data-stu-id="8dfb8-195">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  
<span data-ttu-id="8dfb8-196">¿Necesita saber cómo usar la autenticación moderna (ADAL) para sus clientes de Skype empresarial?</span><span class="sxs-lookup"><span data-stu-id="8dfb8-196">Do you need to know how to use Modern Authentication (ADAL) for your Skype for Business clients?</span></span> <span data-ttu-id="8dfb8-197">Tenemos pasos [aquí](https://technet.microsoft.com/en-us/library/mt710548.aspx).</span><span class="sxs-lookup"><span data-stu-id="8dfb8-197">We've got steps [here](https://technet.microsoft.com/en-us/library/mt710548.aspx).</span></span>
  
<span data-ttu-id="8dfb8-198">¿Quiere leer estos pasos tal y como aparecen para Exchange Server, local, en ejecución sin SFB?</span><span class="sxs-lookup"><span data-stu-id="8dfb8-198">Would you like to read these steps as they appear for Exchange Server, on-premises, running without SFB?</span></span> <span data-ttu-id="8dfb8-199">Estos pasos están disponibles aquí.</span><span class="sxs-lookup"><span data-stu-id="8dfb8-199">Those steps are available here.</span></span>
  

