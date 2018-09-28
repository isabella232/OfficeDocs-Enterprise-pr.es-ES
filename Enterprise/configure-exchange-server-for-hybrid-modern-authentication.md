---
title: Cómo configurar Exchange Server local para usar la autenticación moderna híbrida
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 3/23/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: cef3044d-d4cb-4586-8e82-ee97bd3b14ad
description: Híbrido moderno autenticación (HMA), es un método de administración de identidades que ofrece más seguro autorización y autenticación de usuario y está disponible para las implementaciones híbridas de Exchange server local.
ms.openlocfilehash: cfacb5661ddf4a2ac61054582f0c2043d8fe7a5a
ms.sourcegitcommit: 82219b5f8038ae066405dfb7933c40bd1f598bd0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/14/2018
ms.locfileid: "23975198"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a><span data-ttu-id="569f4-103">Cómo configurar Exchange Server local para usar la autenticación moderna híbrida</span><span class="sxs-lookup"><span data-stu-id="569f4-103">How to configure Exchange Server on-premises to use Hybrid Modern Authentication</span></span>

<span data-ttu-id="569f4-104">Híbrido moderno autenticación (HMA), es un método de administración de identidades que ofrece más seguro autorización y autenticación de usuario y está disponible para las implementaciones híbridas de Exchange server local.</span><span class="sxs-lookup"><span data-stu-id="569f4-104">Hybrid Modern Authentication (HMA), is a method of identity management that offers more secure user authentication and authorization, and is available for Exchange server on-premises hybrid deployments.</span></span>
  
## <a name="fyi"></a><span data-ttu-id="569f4-105">PARA SU INFORMACIÓN</span><span class="sxs-lookup"><span data-stu-id="569f4-105">FYI</span></span>

<span data-ttu-id="569f4-106">Antes de empezar, puedo llamar:</span><span class="sxs-lookup"><span data-stu-id="569f4-106">Before we begin, I call:</span></span>
  
- <span data-ttu-id="569f4-107">Autenticación moderno híbrida \> HMA</span><span class="sxs-lookup"><span data-stu-id="569f4-107">Hybrid Modern Authentication \> HMA</span></span>
    
- <span data-ttu-id="569f4-108">Exchange local \> EXCH</span><span class="sxs-lookup"><span data-stu-id="569f4-108">Exchange on-premises \> EXCH</span></span>
    
- <span data-ttu-id="569f4-109">Exchange Online \> EXO</span><span class="sxs-lookup"><span data-stu-id="569f4-109">Exchange Online \> EXO</span></span>
    
<span data-ttu-id="569f4-110">Además, *que si un gráfico en este artículo tiene un objeto que tiene ' atenuada ' o 'atenuada' Esto significa que el elemento que se muestra en gris no está incluido en la configuración específica del HMA* .</span><span class="sxs-lookup"><span data-stu-id="569f4-110">Also,  *if a graphic in this article has an object that's 'grayed-out' or 'dimmed' that means the element shown in gray is not included in HMA-specific configuration*  .</span></span> 
  
## <a name="enabling-hybrid-modern-authentication"></a><span data-ttu-id="569f4-111">Habilitar la autenticación híbrida moderno</span><span class="sxs-lookup"><span data-stu-id="569f4-111">Enabling Hybrid Modern Authentication</span></span>

<span data-ttu-id="569f4-112">Encienda HMA significa:</span><span class="sxs-lookup"><span data-stu-id="569f4-112">Turning HMA on means:</span></span>
  
1. <span data-ttu-id="569f4-113">Asegurándose de que cumple con los requisitos previos antes de empezar.</span><span class="sxs-lookup"><span data-stu-id="569f4-113">Being sure you meet the prereqs before you begin.</span></span>
    
1. <span data-ttu-id="569f4-p101">Con respecto a muchos de **los requisitos previos** son comunes para ambos Skype para empresas y Exchange, [Introducción a la autenticación moderno híbrida y requisitos previos para usar con local Skype para profesionales y los servidores Exchange](hybrid-modern-auth-overview.md). Hacer esto antes de iniciar cualquiera de los pasos descritos en este artículo.</span><span class="sxs-lookup"><span data-stu-id="569f4-p101">Since many **prerequisites** are common for both Skype for Business and Exchange, [Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers](hybrid-modern-auth-overview.md). Do this before you begin any of the steps in this article.</span></span>
    
2. <span data-ttu-id="569f4-116">Adición de local direcciones URL de servicios web como nombres principales de servicio (SPN) en Azure AD.</span><span class="sxs-lookup"><span data-stu-id="569f4-116">Adding on-premises web service URLs as Service Principal Names (SPNs) in Azure AD.</span></span>
    
3. <span data-ttu-id="569f4-117">Asegurarse de todos los directorios virtuales están habilitados para HMA</span><span class="sxs-lookup"><span data-stu-id="569f4-117">Ensuring all Virtual Directories are enabled for HMA</span></span>
    
4. <span data-ttu-id="569f4-118">Comprobación de que el objeto de servidor de autenticación EvoSTS</span><span class="sxs-lookup"><span data-stu-id="569f4-118">Checking for the EvoSTS Auth Server object</span></span>
    
5. <span data-ttu-id="569f4-119">HMA habilitación de cambio</span><span class="sxs-lookup"><span data-stu-id="569f4-119">Enabling HMA in EXCH.</span></span>
    
 <span data-ttu-id="569f4-p102">**Nota** ¿Se admite MA de su versión de Office? Vea [moderno cómo funciona la autenticación para aplicaciones de cliente de Office 2013 y Office 2016](modern-auth-for-office-2013-and-2016.md).</span><span class="sxs-lookup"><span data-stu-id="569f4-p102">**Note** Does your version of Office support MA? See [How modern authentication works for Office 2013 and Office 2016 client apps](modern-auth-for-office-2013-and-2016.md).</span></span>
  
## <a name="make-sure-you-meet-all-the-pre-reqs"></a><span data-ttu-id="569f4-122">Asegúrese de que cumple todos los requisitos previos</span><span class="sxs-lookup"><span data-stu-id="569f4-122">Make sure you meet all the pre-reqs</span></span>

<span data-ttu-id="569f4-p103">Dado que muchos de los requisitos previos son comunes para ambos Skype para empresariales y de Exchange, revise [Introducción a la autenticación moderno híbrida y requisitos previos para usar con Skype local para los servidores de Exchange y profesionales](hybrid-modern-auth-overview.md). Realice este *antes de* comenzar cualquiera de los pasos descritos en este artículo.</span><span class="sxs-lookup"><span data-stu-id="569f4-p103">Since many prerequisites are common for both Skype for Business and Exchange, review [Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers](hybrid-modern-auth-overview.md). Do this  *before*  you begin any of the steps in this article.</span></span> 
  
## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a><span data-ttu-id="569f4-125">Agregar local web direcciones URL de servicios como SPN en Azure AD</span><span class="sxs-lookup"><span data-stu-id="569f4-125">Add on-premises web service URLs as SPNs in Azure AD</span></span>

<span data-ttu-id="569f4-p104">Ejecute los comandos que asignación direcciones URL de servicios de su web local como SPN de AD de Azure. SPN usados por los equipos cliente y dispositivos durante la autenticación y autorización. Todas las direcciones URL que pueden usarse para conectarse desde local a Azure Active Directory (AAD) deben estar registradas en AAD (Esto incluye los espacios de nombres internos y externos).</span><span class="sxs-lookup"><span data-stu-id="569f4-p104">Run the commands that assign your on-premises web service URLs as Azure AD SPNs. SPNs are used by client machines and devices during authentication and authorization. All the URLs that might be used to connect from on-premises to Azure Active Directory (AAD) must be registered in AAD (this includes both internal and external namespaces).</span></span>
  
<span data-ttu-id="569f4-p105">En primer lugar, recopilar todas las direcciones URL que necesita agregar en AAD. Ejecute estos comandos local:</span><span class="sxs-lookup"><span data-stu-id="569f4-p105">First, gather all the URLs that you need to add in AAD. Run these commands on-premises:</span></span>
  
- <span data-ttu-id="569f4-131">Get-MapiVirtualDirectory | Servidor FL,\*dirección url\*</span><span class="sxs-lookup"><span data-stu-id="569f4-131">Get-MapiVirtualDirectory | FL server,\*url\*</span></span>
    
- <span data-ttu-id="569f4-132">Get-WebServicesVirtualDirectory | Servidor FL,\*dirección url\*</span><span class="sxs-lookup"><span data-stu-id="569f4-132">Get-WebServicesVirtualDirectory | FL server,\*url\*</span></span>
    
- <span data-ttu-id="569f4-133">**Get-ActiveSyncVirtualDirectory | Servidor FL,\*dirección url\***</span><span class="sxs-lookup"><span data-stu-id="569f4-133">**Get-ActiveSyncVirtualDirectory | FL server,\*url\***</span></span>
    
- <span data-ttu-id="569f4-134">Get-OABVirtualDirectory | Servidor FL,\*dirección url\*</span><span class="sxs-lookup"><span data-stu-id="569f4-134">Get-OABVirtualDirectory | FL server,\*url\*</span></span>
    
<span data-ttu-id="569f4-135">Asegúrese de que las direcciones URL que los clientes pueden conectarse a aparecen como nombres principales de servicio HTTPS en AAD.</span><span class="sxs-lookup"><span data-stu-id="569f4-135">Ensure the URLs clients may connect to are listed as HTTPS service principal names in AAD.</span></span>
  
1. <span data-ttu-id="569f4-136">En primer lugar, conectarse a AAD con [estas instrucciones](https://docs.microsoft.com/en-us/office365/enterprise/powershell/connect-to-office-365-powershell).</span><span class="sxs-lookup"><span data-stu-id="569f4-136">First, connect to AAD with [these instructions](https://docs.microsoft.com/en-us/office365/enterprise/powershell/connect-to-office-365-powershell).</span></span>
    
2. <span data-ttu-id="569f4-137">Para Exchange URL relacionadas, escriba el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="569f4-137">For your Exchange related URLs, type the following command:</span></span>
    
- <span data-ttu-id="569f4-138">Get-MsolServicePrincipal - AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | Seleccione - ExpandProperty ServicePrincipalNames</span><span class="sxs-lookup"><span data-stu-id="569f4-138">Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | select -ExpandProperty ServicePrincipalNames</span></span>
    
<span data-ttu-id="569f4-p106">Tome nota de (y captura de pantalla para realizar una comparación posterior) el resultado de este comando, que debe incluir un https:// \* detección automática. .com *SuDominio* \* y la dirección URL de https:// *correo.sudominio.com* , pero se componen principalmente de SPN que comiencen con 00000002-0000-0ff1-ce00-000000000000 /. Si no hay direcciones URL https:// desde su local que faltan necesitamos agregar esos registros específicos a esta lista.</span><span class="sxs-lookup"><span data-stu-id="569f4-p106">Take note of (and screenshot for later comparison) the output of this command, which should include an https:// \*autodiscover. *yourdomain*  .com \*  and https://  *mail.yourdomain.com*  URL, but mostly consist of SPNs that begin with 00000002-0000-0ff1-ce00-000000000000/. If there are https:// URLs from your on-premises that are missing we will need to add those specific records to this list.</span></span> 
  
3. <span data-ttu-id="569f4-142">Si no ve los registros MAPI/HTTP, EWS, ActiveSync, OAB y detección automática internos y externos en esta lista, debe agregarlas mediante el siguiente comando (en el ejemplo de las direcciones URL son '`mail.corp.contoso.com`'y'`owa.contoso.com`', pero tenía **reemplazar las direcciones URL de ejemplo con su propio** ) :</span><span class="sxs-lookup"><span data-stu-id="569f4-142">If you don't see your internal and external MAPI/HTTP, EWS, ActiveSync, OAB and Autodiscover records in this list, you must add them using the command below (the example URLs are '`mail.corp.contoso.com`' and '`owa.contoso.com`', but you'd **replace the example URLs with your own** ):</span></span> <br/>
```
- $x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000   
- $x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
- $x.ServicePrincipalnames.Add("https://owa.contoso.com/")
- $x.ServicePrincipalnames.Add("https://eas.contoso.com/")
- Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
 
4. <span data-ttu-id="569f4-p107">Compruebe que los registros nuevos agregados por ejecutar de nuevo el comando Get-MsolServicePrincipal desde el paso 2 y con un aspecto a través del resultado. Compare la lista / captura de pantalla de antes de a la nueva lista de SPN (que es posible que también captura de pantalla de la nueva lista para sus registros). Si se realizaron correctamente, verá las dos nuevas direcciones URL en la lista. Va por nuestro ejemplo, la lista de los SPN ahora incluirá las direcciones URL específicas `https://mail.corp.contoso.com` y `https://owa.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="569f4-p107">Verify your new records were added by running the Get-MsolServicePrincipal command from step 2 again, and looking through the output. Compare the list / screenshot from before to the new list of SPNs (you may also screenshot the new list for your records). If you were successful, you will see the two new URLs in the list. Going by our example, the list of SPNs will now include the specific URLs  `https://mail.corp.contoso.com`  and  `https://owa.contoso.com`.</span></span> 
  
## <a name="verify-virtual-directories-are-properly-configured"></a><span data-ttu-id="569f4-147">Compruebe que los directorios virtuales están configurados correctamente</span><span class="sxs-lookup"><span data-stu-id="569f4-147">Verify Virtual Directories are Properly Configured</span></span>

<span data-ttu-id="569f4-148">Ahora compruebe OAuth está habilitada correctamente en podría usar Exchange en todos los de Outlook de los directorios virtuales mediante la ejecución de los siguientes comandos:</span><span class="sxs-lookup"><span data-stu-id="569f4-148">Now verify OAuth is properly enabled in Exchange on all of the Virtual Directories Outlook might use by running the following commands:</span></span>

```
Get-MapiVirtualDirectory | FL server,\*url\*,\*auth\* 
Get-WebServicesVirtualDirectory | FL server,\*url\*,\*oauth\*
Get-OABVirtualDirectory | FL server,\*url\*,\*oauth\*
Get-AutoDiscoverVirtualDirectory | FL server,\*oauth\*
```

<span data-ttu-id="569f4-149">Comprobar el resultado para hacer que **OAuth** está habilitada en cada uno de estos directorios virtuales combinados, buscará algo parecido a esto (y lo clave a mirar es 'OAuth');</span><span class="sxs-lookup"><span data-stu-id="569f4-149">Check the output to make sure **OAuth** is enabled on each of these VDirs, it will look something like this (and the key thing to look at is 'OAuth');</span></span> 
  
 <span data-ttu-id="569f4-150">**[PS] C:\Windows\System32\>Get-MapiVirtualDirectory | servidor fl,\*dirección url\*,\*auth\***</span><span class="sxs-lookup"><span data-stu-id="569f4-150">**[PS] C:\Windows\system32\>Get-MapiVirtualDirectory | fl server,\*url\*,\*auth\***</span></span>
  
 <span data-ttu-id="569f4-151">**Servidor: EX1**</span><span class="sxs-lookup"><span data-stu-id="569f4-151">**Server : EX1**</span></span>
  
 <span data-ttu-id="569f4-152">**InternalUrl:`https://mail.contoso.com/mapi`**</span><span class="sxs-lookup"><span data-stu-id="569f4-152">**InternalUrl : `https://mail.contoso.com/mapi`**</span></span>
  
 <span data-ttu-id="569f4-153">**ExternalUrl:`https://mail.contoso.com/mapi`**</span><span class="sxs-lookup"><span data-stu-id="569f4-153">**ExternalUrl : `https://mail.contoso.com/mapi`**</span></span>
  
 <span data-ttu-id="569f4-154">**IISAuthenticationMethods: {Ntlm, OAuth, negociar}**</span><span class="sxs-lookup"><span data-stu-id="569f4-154">**IISAuthenticationMethods : {Ntlm, OAuth, Negotiate}**</span></span>
  
 <span data-ttu-id="569f4-155">**InternalAuthenticationMethods: {Ntlm, OAuth, negociar}**</span><span class="sxs-lookup"><span data-stu-id="569f4-155">**InternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}**</span></span>
  
 <span data-ttu-id="569f4-156">**ExternalAuthenticationMethods: {Ntlm, OAuth, negociar}**</span><span class="sxs-lookup"><span data-stu-id="569f4-156">**ExternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}**</span></span>
  
<span data-ttu-id="569f4-157">Si no se encuentra ningún servidor y cualquiera de los cuatro directorios virtuales de OAuth, a continuación, debe agregar los comandos relevantes antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="569f4-157">If OAuth is missing from any server and any of the four virtual directories then you need to add it using the relevant commands before proceeding.</span></span>
  
## <a name="confirm-the-evosts-auth-server-object-is-present"></a><span data-ttu-id="569f4-158">Confirme que el objeto de servidor de autenticación de EvoSTS está presente</span><span class="sxs-lookup"><span data-stu-id="569f4-158">Confirm the EvoSTS Auth Server Object is Present</span></span>

<span data-ttu-id="569f4-p108">Volver a la consola de administración de Exchange local para este último comando. Ahora puede validar que su local tiene una entrada para el proveedor de autenticación evoSTS:</span><span class="sxs-lookup"><span data-stu-id="569f4-p108">Return to the on-premises Exchange Management Shell for this last command. Now you can validate that your on-premises has an entry for the evoSTS authentication provider:</span></span>
  
`Get-AuthServer | where {$_.Name -eq "EvoSts"}`
    
<span data-ttu-id="569f4-p109">El resultado debe mostrar una AuthServer de la EvoSts de nombre y el estado de 'Habilitado' debe ser True. Si no ve esto, debe descargar y ejecutar la versión más reciente del Asistente de configuración híbrida.</span><span class="sxs-lookup"><span data-stu-id="569f4-p109">Your output should show an AuthServer of the Name EvoSts and the 'Enabled' state should be True. If you don't see this, you should download and run the most recent version of the Hybrid Configuration Wizard.</span></span>
  
 <span data-ttu-id="569f4-163">**Importante** Si está ejecutando Exchange 2010 en su entorno, no se creará el proveedor de autenticación EvoSTS.</span><span class="sxs-lookup"><span data-stu-id="569f4-163">**Important** If you're running Exchange 2010 in your environment, the EvoSTS authentication provider won't be created.</span></span> 
  
## <a name="enable-hma"></a><span data-ttu-id="569f4-164">Habilitar HMA</span><span class="sxs-lookup"><span data-stu-id="569f4-164">Enable HMA</span></span>

<span data-ttu-id="569f4-165">Ejecute el siguiente comando en el Shell de administración de Exchange local:</span><span class="sxs-lookup"><span data-stu-id="569f4-165">Run the following command in the Exchange Management Shell, on-premises:</span></span>

```
Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true  
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```
    
## <a name="verify"></a><span data-ttu-id="569f4-166">Comprobar</span><span class="sxs-lookup"><span data-stu-id="569f4-166">Verify</span></span>

<span data-ttu-id="569f4-p110">Una vez habilitar HMA, el siguiente inicio de sesión de un cliente utilizará el nuevo flujo de autenticación. Tenga en cuenta la activación de HMA no desencadenar una nueva autenticación para cualquier cliente. Los clientes volver a autenticar en función de la duración de los tokens de autenticación o que tienen los certificados.</span><span class="sxs-lookup"><span data-stu-id="569f4-p110">Once you enable HMA, a client's next login will use the new auth flow. Note that just turning on HMA won't trigger a re-authentication for any client. The clients re-authenticate based on the lifetime of the auth tokens and/or certs they have.</span></span>
  
<span data-ttu-id="569f4-p111">También debe mantenga presionada la tecla CTRL al mismo tiempo botón secundario haga clic en el icono para el cliente de Outlook (también en la Bandeja de notificaciones de Windows) y haga clic en estado de la conexión. Busque la dirección del cliente SMTP con respecto a un tipo 'Niveles de autenticación' de ' Bearer\*', que representa el token de portador utilizado en OAuth.</span><span class="sxs-lookup"><span data-stu-id="569f4-p111">You should also hold down the CTRL key at the same time you right click the icon for the Outlook client (also in the Windows Notifications tray) and click 'Connection Status'. Look for the client's SMTP address against an 'Authn' type of 'Bearer\*', which represents the bearer token used in OAuth.</span></span>
  
 <span data-ttu-id="569f4-p112">**Nota** ¿Necesita configurar Skype para la empresa con HMA? Necesitará dos artículos: uno que enumera las [topologías admitidas](https://technet.microsoft.com/en-us/library/mt803262.aspx)y otro que muestra [cómo realizar la configuración](configure-skype-for-business-for-hybrid-modern-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="569f4-p112">**Note** Need to configure Skype for Business with HMA? You'll need two articles: One that lists [supported topologies](https://technet.microsoft.com/en-us/library/mt803262.aspx), and one that shows you [how to do the configuration](configure-skype-for-business-for-hybrid-modern-authentication.md).</span></span>
  

## <a name="related-topics"></a><span data-ttu-id="569f4-174">Temas relacionados</span><span class="sxs-lookup"><span data-stu-id="569f4-174">Related topics</span></span>

[<span data-ttu-id="569f4-175">Introducción a la autenticación moderno híbrida y requisitos previos para usar con Skype local para los servidores empresariales y de Exchange</span><span class="sxs-lookup"><span data-stu-id="569f4-175">Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers</span></span>](hybrid-modern-auth-overview.md) 
  

