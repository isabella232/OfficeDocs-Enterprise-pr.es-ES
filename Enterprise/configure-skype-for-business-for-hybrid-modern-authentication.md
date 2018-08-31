---
title: Cómo configurar Skype Empresarial local para usar la autenticación moderna híbrida
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 6/4/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 522d5cec-4e1b-4cc3-937f-293570717bc6
description: Autenticación moderna, es un método de administración de identidades que ofrece la autorización y autenticación de usuario más segura, está disponible para Skype para Business server local y Exchange server local, así como dominio dividido Skype para híbridos de negocio.
ms.openlocfilehash: 48ce10022e384ec88b88c0e8ec038bf201adc707
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22543051"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a><span data-ttu-id="b9fb6-103">Cómo configurar Skype Empresarial local para usar la autenticación moderna híbrida</span><span class="sxs-lookup"><span data-stu-id="b9fb6-103">How to configure Skype for Business on-premises to use Hybrid Modern Authentication</span></span>

<span data-ttu-id="b9fb6-104">Autenticación moderna, es un método de administración de identidades que ofrece la autorización y autenticación de usuario más segura, está disponible para Skype para Business server local y Exchange server local, así como dominio dividido Skype para híbridos de negocio.</span><span class="sxs-lookup"><span data-stu-id="b9fb6-104">Modern Authentication, is a method of identity management that offers more secure user authentication and authorization, is available for Skype for Business server on-premises and Exchange server on-premises, as well as split-domain Skype for Business hybrids.</span></span>
  
 <span data-ttu-id="b9fb6-p101">**Importante** ¿Desea saber más sobre autenticación moderno (MA) y por qué es preferible usar en su compañía u organización? Compruebe [este documento](hybrid-modern-auth-overview.md) para obtener información general. Si necesita saber qué Skype para topologías empresariales son compatibles con MA, que se documenta aquí!</span><span class="sxs-lookup"><span data-stu-id="b9fb6-p101">**Important** Would you like to know more about Modern Authentication (MA) and why you might prefer to use it in your company or organization? Check [this document](hybrid-modern-auth-overview.md) for an overview. If you need to know what Skype for Business topologies are supported with MA, that's documented here!</span></span> 
  
 <span data-ttu-id="b9fb6-108">**Antes de empezar**, puedo llamar:</span><span class="sxs-lookup"><span data-stu-id="b9fb6-108">**Before we begin**, I call:</span></span> 
  
- <span data-ttu-id="b9fb6-109">Autenticación moderna \> MA</span><span class="sxs-lookup"><span data-stu-id="b9fb6-109">Modern Authentication \> MA</span></span>
    
- <span data-ttu-id="b9fb6-110">Autenticación moderno híbrida \> HMA</span><span class="sxs-lookup"><span data-stu-id="b9fb6-110">Hybrid Modern Authentication \> HMA</span></span>
    
- <span data-ttu-id="b9fb6-111">Exchange local \> EXCH</span><span class="sxs-lookup"><span data-stu-id="b9fb6-111">Exchange on-premises \> EXCH</span></span>
    
- <span data-ttu-id="b9fb6-112">Exchange Online \> EXO</span><span class="sxs-lookup"><span data-stu-id="b9fb6-112">Exchange Online \> EXO</span></span>
    
- <span data-ttu-id="b9fb6-113">Skype para empresarial local \> SFB</span><span class="sxs-lookup"><span data-stu-id="b9fb6-113">Skype for Business on-premises \> SFB</span></span>
    
- <span data-ttu-id="b9fb6-114">y Skype para la empresa en línea \> SFBO</span><span class="sxs-lookup"><span data-stu-id="b9fb6-114">and Skype for Business Online \> SFBO</span></span>
    
<span data-ttu-id="b9fb6-115">Además, \* si un gráfico en este artículo no tiene un valor object que tiene 'atenuada' o 'atenuada' que significa que el elemento que se muestra en gris **no está** incluido en la configuración específica del agente de administración.</span><span class="sxs-lookup"><span data-stu-id="b9fb6-115">Also,  \*if a graphic in this article has an object that's 'grayed-out' or 'dimmed' that means the element shown in gray **is not** included in MA-specific configuration.</span></span> * 
  
## <a name="read-the-summary"></a><span data-ttu-id="b9fb6-116">Lea el resumen</span><span class="sxs-lookup"><span data-stu-id="b9fb6-116">Read the summary</span></span>

<span data-ttu-id="b9fb6-117">En este resumen se reduce el proceso en pasos que en caso contrario, es posible que se pierden durante la ejecución y es conveniente para una lista de comprobación general realizar un seguimiento de dónde se encuentre en el proceso.</span><span class="sxs-lookup"><span data-stu-id="b9fb6-117">This summary boils the process into steps that might otherwise get lost during the execution, and is good for an overall check-list to keep track of where you are in the process.</span></span>
  
1. <span data-ttu-id="b9fb6-118">En primer lugar, asegúrese de que cumple todos los requisitos previos.</span><span class="sxs-lookup"><span data-stu-id="b9fb6-118">First, make sure you meet all the prerequisites.</span></span>
    
1. <span data-ttu-id="b9fb6-p102">Con respecto a muchos de **los requisitos previos** son comunes para ambos Skype para empresariales y de Exchange, [consulte el artículo de información general para la lista de comprobación de requisito previo](hybrid-modern-auth-overview.md). Realice este *antes de* comenzar cualquiera de los pasos descritos en este artículo.</span><span class="sxs-lookup"><span data-stu-id="b9fb6-p102">Since many **prerequisites** are common for both Skype for Business and Exchange, [see the overview article for your pre-req checklist](hybrid-modern-auth-overview.md). Do this  *before*  you begin any of the steps in this article.</span></span> 
    
2. <span data-ttu-id="b9fb6-121">Recopilar la información de HMA específicas que necesitará en un archivo o OneNote.</span><span class="sxs-lookup"><span data-stu-id="b9fb6-121">Collect the HMA-specific info you'll need in a file, or OneNote.</span></span>
    
3. <span data-ttu-id="b9fb6-122">Activar ON moderno Authentication for EXO (si no está ya activada).</span><span class="sxs-lookup"><span data-stu-id="b9fb6-122">Turn ON Modern Authentication for EXO (if it is not already turned on).</span></span>
    
4. <span data-ttu-id="b9fb6-123">Activar ON moderno Authentication for SFBO (si no está ya activada).</span><span class="sxs-lookup"><span data-stu-id="b9fb6-123">Turn ON Modern Authentication for SFBO (if it is not already turned on).</span></span>
    
5. <span data-ttu-id="b9fb6-124">Activar la autenticación moderno híbrida de Exchange local.</span><span class="sxs-lookup"><span data-stu-id="b9fb6-124">Turn ON Hybrid Modern Authentication for Exchange on-premises.</span></span>
    
6. <span data-ttu-id="b9fb6-125">Activar la autenticación moderno híbrido de Skype para empresarial local.</span><span class="sxs-lookup"><span data-stu-id="b9fb6-125">Turn ON Hybrid Modern Authentication for Skype for Business on-premises.</span></span>
    
<span data-ttu-id="b9fb6-p103">Tenga en cuenta que estos pasos activar MA para SFB, SFBO, EXCH y EXO--es decir, todos los productos que pueden participar en una configuración de HMA de SFB y SFBO (incluidas las dependencias en EXCH/EXO). En otras palabras, si los usuarios están hospedados en / crean buzones de correo en cualquier parte de la híbrido (EXO + SFBO, EXO + SFB, EXCH + SFBO, o EXCH + SFB), el precio del producto terminado tendrá el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="b9fb6-p103">Note These steps turn on MA for SFB, SFBO, EXCH, and EXO -- that is, all the products that can participate in a HMA configuration of SFB and SFBO (including dependencies on EXCH/EXO). In other words, if your users are homed in/have mailboxes created in any part of the Hybrid (EXO + SFBO, EXO + SFB, EXCH + SFBO, or EXCH + SFB), your finished product will look like this:</span></span>
  
![Un Skype 6 mixto de topología del negocio HMA tiene MA en todas las ubicaciones posibles cuatro.](media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)
  
<span data-ttu-id="b9fb6-p104">Como puede ver, hay cuatro distintos lugares para activar el agente de administración de! Para la mejor experiencia de usuario, se recomienda que activar MA en cuatro de estas ubicaciones. Si no se puede activar el agente de administración en todas las ubicaciones de estos, ajuste los pasos para que encienda MA sólo en las ubicaciones que son necesarios para su entorno.</span><span class="sxs-lookup"><span data-stu-id="b9fb6-p104">As you can see there are four different places to turn on MA! For the best user experience we recommend you turn on MA in all four of these locations. If you can't turn MA on in all these locations, adjust the steps so that you turn on MA only in the locations that are necessary for your environment.</span></span>
  
<span data-ttu-id="b9fb6-132">Vea el [tema de la compatibilidad de Skype para la empresa con el agente de administración](https://technet.microsoft.com/en-us/library/mt803262.aspx) de topologías admitidas.</span><span class="sxs-lookup"><span data-stu-id="b9fb6-132">See the [Supportability topic for Skype for Business with MA](https://technet.microsoft.com/en-us/library/mt803262.aspx) for supported topologies.</span></span> 
  
 <span data-ttu-id="b9fb6-p105">**Importante** Vuelva a comprobar que cumple todos los requisitos previos antes de empezar. Puede encontrar esa información [aquí](hybrid-modern-auth-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b9fb6-p105">**Important** Double-check that you've met all the prerequisites before you begin. You'll find that information [here](hybrid-modern-auth-overview.md).</span></span>
  
## <a name="collect-all-hma-specific-info-youll-need"></a><span data-ttu-id="b9fb6-135">Recopilar toda la información específica de HMA que necesitará</span><span class="sxs-lookup"><span data-stu-id="b9fb6-135">Collect all HMA-specific info you'll need</span></span>

<span data-ttu-id="b9fb6-p106">Una vez haya comprobado que se cumplen los [requisitos previos](hybrid-modern-auth-overview.md) para usar autenticación moderno (consulte la nota anterior), debe crear un archivo para contener la información que necesitará para configurar HMA en los pasos con antelación. Ejemplos que se utilizan en este artículo:</span><span class="sxs-lookup"><span data-stu-id="b9fb6-p106">After you've double-checked that you meet the [prerequisites](hybrid-modern-auth-overview.md) to use Modern Authentication (see the note above), you should create a file to hold the info you'll need for configuring HMA in the steps ahead. Examples used in this article:</span></span> 
  
- <span data-ttu-id="b9fb6-138">**Dominio SIP/SMTP**</span><span class="sxs-lookup"><span data-stu-id="b9fb6-138">**SIP/SMTP domain**</span></span>
    
  - <span data-ttu-id="b9fb6-p107">Contoso.com ex. (está asociado a Office 365)</span><span class="sxs-lookup"><span data-stu-id="b9fb6-p107">Ex. contoso.com (is federated with Office 365)</span></span>
    
- <span data-ttu-id="b9fb6-141">**Identificador de inquilino**</span><span class="sxs-lookup"><span data-stu-id="b9fb6-141">**Tenant ID**</span></span>
    
  - <span data-ttu-id="b9fb6-142">El GUID que representa al inquilino de Office 365 (en el inicio de sesión de contoso.onmicrosoft.com).</span><span class="sxs-lookup"><span data-stu-id="b9fb6-142">The GUID that represents your Office 365 tenant (at the login of contoso.onmicrosoft.com).</span></span>
    
- <span data-ttu-id="b9fb6-143">**Direcciones URL del servicio SFB 2015 CU5 Web**</span><span class="sxs-lookup"><span data-stu-id="b9fb6-143">**SFB 2015 CU5 Web Service URLs**</span></span>
    
<span data-ttu-id="b9fb6-p108">Necesitará la dirección URL de servicio web internos y externos para todos los grupos de servidores SfB 2015 implementados. Para obtener estos, ejecute lo siguiente desde Skype para Shell de administración de negocio:</span><span class="sxs-lookup"><span data-stu-id="b9fb6-p108">You will need internal and external web service URL's for all SfB 2015 pools deployed. To obtain these, run the following from Skype for Business Management Shell:</span></span>
  
<span data-ttu-id="b9fb6-146">Get-CsService - WebServer | Select-Object PoolFqdn, InternalFqdn, Fqdnexterno | FL</span><span class="sxs-lookup"><span data-stu-id="b9fb6-146">Get-CsService -WebServer | Select-Object PoolFqdn, InternalFqdn, ExternalFqdn | FL</span></span>
  
- <span data-ttu-id="b9fb6-p109">Ex. interno:https://lyncwebint01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="b9fb6-p109">Ex. Internal: https://lyncwebint01.contoso.com</span></span>
    
- <span data-ttu-id="b9fb6-p110">Ex. externos:https://lyncwebext01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="b9fb6-p110">Ex. External: https://lyncwebext01.contoso.com</span></span>
    
<span data-ttu-id="b9fb6-p111">Si está utilizando un servidor Standard Edition, la dirección URL interna estará en blanco. En este caso, use el fqdn del grupo de servidores para la dirección URL interna.</span><span class="sxs-lookup"><span data-stu-id="b9fb6-p111">If you are using a Standard Edition server, the internal URL will be blank. In this case, use the pool fqdn for the internal URL.</span></span>
  
## <a name="turn-on-modern-authentication-for-exo"></a><span data-ttu-id="b9fb6-153">Activar la autenticación moderna para EXO</span><span class="sxs-lookup"><span data-stu-id="b9fb6-153">Turn on Modern Authentication for EXO</span></span>

<span data-ttu-id="b9fb6-154">Siga las instrucciones aquí: [Exchange Online: cómo habilitar el inquilino de para la autenticación moderno.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)</span><span class="sxs-lookup"><span data-stu-id="b9fb6-154">Follow the instructions here: [Exchange Online: How to enable your tenant for modern authentication.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)</span></span>
  
## <a name="turn-on-modern-authentication-for-sfbo"></a><span data-ttu-id="b9fb6-155">Activar la autenticación moderna para SFBO</span><span class="sxs-lookup"><span data-stu-id="b9fb6-155">Turn on Modern Authentication for SFBO</span></span>

<span data-ttu-id="b9fb6-156">Siga las instrucciones aquí: [Skype para profesionales Online: habilitar el inquilino de para la autenticación moderno](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).</span><span class="sxs-lookup"><span data-stu-id="b9fb6-156">Follow the instructions here: [Skype for Business Online: Enable your tenant for modern authentication](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a><span data-ttu-id="b9fb6-157">Activar la autenticación moderno híbrida de Exchange local</span><span class="sxs-lookup"><span data-stu-id="b9fb6-157">Turn on Hybrid Modern Authentication for Exchange on-premises</span></span>

<span data-ttu-id="b9fb6-158">Siga las instrucciones aquí: [cómo configurar el servidor de Exchange local para usar la autenticación moderno híbrida](configure-exchange-server-for-hybrid-modern-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="b9fb6-158">Follow the instructions here: [How to configure Exchange Server on-premises to use Hybrid Modern Authentication](configure-exchange-server-for-hybrid-modern-authentication.md).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a><span data-ttu-id="b9fb6-159">Activar la autenticación moderno híbrido de Skype para empresarial local</span><span class="sxs-lookup"><span data-stu-id="b9fb6-159">Turn on Hybrid Modern Authentication for Skype for Business on-premises</span></span>

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a><span data-ttu-id="b9fb6-160">Agregar local web direcciones URL de servicios como SPN en Azure AD</span><span class="sxs-lookup"><span data-stu-id="b9fb6-160">Add on-premises web service URLs as SPNs in Azure AD</span></span>

<span data-ttu-id="b9fb6-161">Ahora que necesitará para ejecutar comandos para agregar las direcciones URL (anteriormente recopilados) como entidades de seguridad de servicio en SFBO.</span><span class="sxs-lookup"><span data-stu-id="b9fb6-161">Now you'll need to run commands to add the URLs (collected earlier) as Service Principals in SFBO.</span></span>
  
 <span data-ttu-id="b9fb6-p112">**Nota** Nombres principales de servicio (SPN) identificación de servicios web y asociación a una entidad de seguridad (por ejemplo, un nombre de cuenta o grupo) para que el servicio pueda actuar en nombre de un usuario autorizado. Autenticación a un servidor de clientes hacen uso de la información que SPN contenidos en.</span><span class="sxs-lookup"><span data-stu-id="b9fb6-p112">**Note** Service principal names (SPNs) identify web services and associate them with a security principal (such as an account name or group) so that the service can act on the behalf of an authorized user. Clients authenticating to a server make use of information that's contained in SPNs.</span></span> 
  
1. <span data-ttu-id="b9fb6-164">En primer lugar, conectarse a AAD con [estas instrucciones](https://docs.microsoft.com/en-us/powershell/azure/active-directory/install-adv2?view=azureadps-2.0).</span><span class="sxs-lookup"><span data-stu-id="b9fb6-164">First, connect to AAD with [these instructions](https://docs.microsoft.com/en-us/powershell/azure/active-directory/install-adv2?view=azureadps-2.0).</span></span>
    
2. <span data-ttu-id="b9fb6-165">Ejecute este comando, local, para obtener una lista de direcciones URL de servicio de web SFB.</span><span class="sxs-lookup"><span data-stu-id="b9fb6-165">Run this command, on-premises, to get a list of SFB web service URLs.</span></span>
    
  - <span data-ttu-id="b9fb6-166">Get-MsolServicePrincipal - AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Seleccione ServicePrincipalNames - ExpandProperty</span><span class="sxs-lookup"><span data-stu-id="b9fb6-166">Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Select -ExpandProperty ServicePrincipalNames</span></span>
    
    <span data-ttu-id="b9fb6-p113">Tenga en cuenta que el AppPrincipalId comienza con '00000004'. Esto corresponde al Skype para profesionales en línea.</span><span class="sxs-lookup"><span data-stu-id="b9fb6-p113">Notice that the AppPrincipalId begins with '00000004'. This corresponds to Skype for Business Online.</span></span>
    
    <span data-ttu-id="b9fb6-169">Tomar nota de (y captura de pantalla para realizar una comparación posterior) el resultado de este comando, que se incluyen un SE y la dirección URL de WS, pero se componen principalmente de SPN que comiencen con 00000004-0000-0ff1-ce00-000000000000 /.</span><span class="sxs-lookup"><span data-stu-id="b9fb6-169">Take note of (and screenshot for later comparison) the output of this command, which will include an SE and WS URL, but mostly consist of SPNs that begin with 00000004-0000-0ff1-ce00-000000000000/.</span></span>
    
3. <span data-ttu-id="b9fb6-170">Si la interna **o** externa SFB las direcciones URL de local faltan (por ejemplo, https://lyncwebint01.contoso.com y https://lyncwebext01.contoso.com) necesitamos agregar esos registros específicos a esta lista.</span><span class="sxs-lookup"><span data-stu-id="b9fb6-170">If the internal **or** external SFB URLs from on-premises are missing (for example, https://lyncwebint01.contoso.com and https://lyncwebext01.contoso.com) we will need to add those specific records to this list.</span></span> 
    
    <span data-ttu-id="b9fb6-171">¡Asegúrese de reemplazar *las direcciones URL de ejemplo* , a continuación, con las direcciones URL real en los comandos Agregar!</span><span class="sxs-lookup"><span data-stu-id="b9fb6-171">Be sure to replace  *the example URLs*  , below, with your actual URLs in the Add commands!</span></span> 
    
  - <span data-ttu-id="b9fb6-172">$x = get-MsolServicePrincipal - AppPrincipalId 00000004-0000-0ff1-ce00-000000000000</span><span class="sxs-lookup"><span data-stu-id="b9fb6-172">$x= Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000</span></span>
    
  - <span data-ttu-id="b9fb6-173">$x.ServicePrincipalnames.Add (" *https://lyncwebint01.contoso.com/* ")</span><span class="sxs-lookup"><span data-stu-id="b9fb6-173">$x.ServicePrincipalnames.Add(" *https://lyncwebint01.contoso.com/*  ")</span></span> 
    
  - <span data-ttu-id="b9fb6-174">$x.ServicePrincipalnames.Add (" *https://lyncwebext01.contoso.com/* ")</span><span class="sxs-lookup"><span data-stu-id="b9fb6-174">$x.ServicePrincipalnames.Add(" *https://lyncwebext01.contoso.com/*  ")</span></span> 
    
  - <span data-ttu-id="b9fb6-175">Set-MSOLServicePrincipal - AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 - ServicePrincipalNames $x.ServicePrincipalNames</span><span class="sxs-lookup"><span data-stu-id="b9fb6-175">Set-MSOLServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames</span></span>
    
4. <span data-ttu-id="b9fb6-p114">Compruebe que los registros nuevos agregados por ejecutar de nuevo el comando Get-MsolServicePrincipal desde el paso 2 y con un aspecto a través del resultado. Compare la lista / captura de pantalla de antes de a la nueva lista de SPN (que es posible que también captura de pantalla de la nueva lista para sus registros). Si se realizaron correctamente, verá las dos nuevas direcciones URL en la lista. Va por nuestro ejemplo, la lista de los SPN ahora incluirá las direcciones URL específicas https://lyncweb01.contoso.com y https://autodiscover.contoso.com.</span><span class="sxs-lookup"><span data-stu-id="b9fb6-p114">Verify your new records were added by running the Get-MsolServicePrincipal command from step 2 again, and looking through the output. Compare the list / screenshot from before to the new list of SPNs (you may also screenshot the new list for your records). If you were successful, you will see the two new URLs in the list. Going by our example, the list of SPNs will now include the specific URLs https://lyncweb01.contoso.com and https://autodiscover.contoso.com.</span></span>
    
### <a name="create-the-evosts-auth-server-object"></a><span data-ttu-id="b9fb6-180">Crear el objeto de servidor de autenticación EvoSTS</span><span class="sxs-lookup"><span data-stu-id="b9fb6-180">Create the EvoSTS Auth Server Object</span></span>

<span data-ttu-id="b9fb6-181">Ejecute el siguiente comando en el Skype para Shell de administración de negocio.</span><span class="sxs-lookup"><span data-stu-id="b9fb6-181">Run the following command in the Skype for Business Management Shell.</span></span>
  
- <span data-ttu-id="b9fb6-182">New-CsOAuthServer-Identity evoSTS - MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml - AcceptSecurityIdentifierInformation $true-tipo AzureAD</span><span class="sxs-lookup"><span data-stu-id="b9fb6-182">New-CsOAuthServer -Identity evoSTS -MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml -AcceptSecurityIdentifierInformation $true -Type AzureAD</span></span>
    
### <a name="enable-hybrid-modern-authentication"></a><span data-ttu-id="b9fb6-183">Habilitar la autenticación moderno híbrida</span><span class="sxs-lookup"><span data-stu-id="b9fb6-183">Enable Hybrid Modern Authentication</span></span>

<span data-ttu-id="b9fb6-p115">Éste es el paso que realmente activa MA. Todos los pasos anteriores se pueden ejecutar antes de tiempo sin cambiar el flujo de autenticación de cliente. Cuando esté listo para cambiar el flujo de autenticación, ejecute este comando en el Skype para Shell de administración de negocio.</span><span class="sxs-lookup"><span data-stu-id="b9fb6-p115">This is the step that actually turns MA on. All the previous steps can be run ahead of time without changing the client authentication flow. When you are ready to change the authentication flow, run this command in the Skype for Business Management Shell.</span></span> 
  
- <span data-ttu-id="b9fb6-187">Set-CsOAuthConfiguration - ClientAuthorizationOAuthServerIdentity evoSTS</span><span class="sxs-lookup"><span data-stu-id="b9fb6-187">Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity evoSTS</span></span>
    
## <a name="verify"></a><span data-ttu-id="b9fb6-188">Comprobar</span><span class="sxs-lookup"><span data-stu-id="b9fb6-188">Verify</span></span>

<span data-ttu-id="b9fb6-p116">Una vez habilitar HMA, el siguiente inicio de sesión de un cliente utilizará el nuevo flujo de autenticación. Tenga en cuenta la activación de HMA no desencadenar una nueva autenticación para cualquier cliente. Los clientes volver a autenticar en función de la duración de los tokens de autenticación o que tienen los certificados.</span><span class="sxs-lookup"><span data-stu-id="b9fb6-p116">Once you enable HMA, a client's next login will use the new auth flow. Note that just turning on HMA won't trigger a re-authentication for any client. The clients re-authenticate based on the lifetime of the auth tokens and/or certs they have.</span></span>
  
<span data-ttu-id="b9fb6-p117">Para probar que está funcionando HMA después de que la ha habilitado, cerrar la sesión de un cliente de Windows SFB de prueba y asegúrese de hacer clic en 'eliminar mis credenciales'. Iniciar sesión de nuevo. El cliente ahora debe usar el flujo de Auth moderno y su inicio de sesión incluirá un símbolo del sistema de **Office 365** para un 'trabajo o escuela' cuenta, se puede apreciar justo antes de que el cliente se pone en contacto con el servidor e inicia una sesión.</span><span class="sxs-lookup"><span data-stu-id="b9fb6-p117">To test that HMA is working after you've enabled it, sign out of a test SFB Windows client and be sure to click 'delete my credentials'. Sign in again. The client should now use the Modern Auth flow and your login will now include an **Office 365** prompt for a 'Work or school' account, seen right before the client contacts the server and logs you in.</span></span> 
  
<span data-ttu-id="b9fb6-p118">También debe comprobar la información de configuración de' ' para Skype para clientes empresariales para una entidad de' OAuth'. Para hacer esto en el equipo cliente, mantenga presionada la tecla CTRL al mismo tiempo que secundario la Skype para empresarial icono en la Bandeja de notificación de Windows. En el menú que aparece, haga clic en información de configuración. En la ventana 'Skype para información de configuración de la empresa' que aparecerá en el escritorio, busque lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="b9fb6-p118">You should also check the 'Configuration Information' for Skype for Business Clients for an 'OAuth Authority'. To do this on your client computer, hold down the CTRL key at the same time you right-click the Skype for Business Icon in the Windows Notification tray. Click Configuration Information in the menu that appears. In the 'Skype for Business Configuration Information' window that will appear on the desktop, look for the following:</span></span>
  
![La información de configuración de un Skype para el cliente de negocio mediante autenticación moderno muestra un Lync y la dirección URL de EWS OAUTH autoridad de https://login.windows.net/common/oauth2/authorize.](media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png)
  
<span data-ttu-id="b9fb6-p119">También debe mantenga presionada la tecla CTRL al mismo tiempo botón secundario haga clic en el icono para el cliente de Outlook (también en la Bandeja de notificaciones de Windows) y haga clic en estado de la conexión. Busque la dirección del cliente SMTP con respecto a un tipo de niveles de autenticación de ' Bearer\*', que representa el token de portador utilizado en OAuth.</span><span class="sxs-lookup"><span data-stu-id="b9fb6-p119">You should also hold down the CTRL key at the same time you right click the icon for the Outlook client (also in the Windows Notifications tray) and click 'Connection Status'. Look for the client's SMTP address against an Authn type of 'Bearer\*', which represents the bearer token used in OAuth.</span></span>
  
## <a name="related-articles"></a><span data-ttu-id="b9fb6-202">Artículos relacionados</span><span class="sxs-lookup"><span data-stu-id="b9fb6-202">Related articles</span></span>

<span data-ttu-id="b9fb6-203">[Vínculo hacia atrás a la introducción a la autenticación moderno](hybrid-modern-auth-overview.md) .</span><span class="sxs-lookup"><span data-stu-id="b9fb6-203">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  
<span data-ttu-id="b9fb6-p120">¿Necesita saber cómo usar autenticación moderno (ADAL) para su Skype para clientes empresariales? Tenemos pasos [aquí](https://technet.microsoft.com/en-us/library/mt710548.aspx).</span><span class="sxs-lookup"><span data-stu-id="b9fb6-p120">Do you need to know how to use Modern Authentication (ADAL) for your Skype for Business clients? We've got steps [here](https://technet.microsoft.com/en-us/library/mt710548.aspx).</span></span>
  
<span data-ttu-id="b9fb6-p121">¿Desea para leer estos pasos, tal como aparecen para Exchange Server, local, que se ejecuta sin SFB? Esos pasos están disponibles aquí.</span><span class="sxs-lookup"><span data-stu-id="b9fb6-p121">Would you like to read these steps as they appear for Exchange Server, on-premises, running without SFB? Those steps are available here.</span></span>
  

