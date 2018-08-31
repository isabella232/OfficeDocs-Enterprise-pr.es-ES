---
title: Administración de extremos de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 7/18/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 99cab9d4-ef59-4207-9f2b-3728eb46bf9a
description: Algunas redes están diseñados para restringir el acceso a internet, para asegurarse de que los equipos de las redes como estos pueden tener acceso a Office 365, los administradores de red y proxy necesitan para administrar la lista de nombres de dominio completos, las direcciones URL, y las direcciones IP que componen la lista de extremos de Office 365. Estos necesidad que se agregará al proxy o firewall reglas y PAC archivos para asegurarse de las solicitudes de red son capaces de ponerse en contacto con Office 365.
ms.openlocfilehash: 0396174719adc7794a1d6bb4b1f950bfe4603996
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542832"
---
# <a name="managing-office-365-endpoints"></a><span data-ttu-id="625ce-104">Administración de extremos de Office 365</span><span class="sxs-lookup"><span data-stu-id="625ce-104">Managing Office 365 endpoints</span></span>

## <a name="office-365-network-connectivity"></a><span data-ttu-id="625ce-105">Conectividad de red de Office 365</span><span class="sxs-lookup"><span data-stu-id="625ce-105">Office 365 network connectivity</span></span>

 <span data-ttu-id="625ce-p102">Las conexiones a Office 365 constan de gran volumen, las solicitudes de red de confianza que realizar mejor cuando haya realizado a través de una salida de latencia baja está próxima al usuario. Algunas conexiones de Office 365 pueden beneficiarse de la optimización de la conexión.</span><span class="sxs-lookup"><span data-stu-id="625ce-p102">Connections to Office 365 consist of high volume, trusted network requests that perform best when they're made over a low-latency egress that is near the user. Some Office 365 connections can benefit from optimizing the connection.</span></span> 
  
1. <span data-ttu-id="625ce-108">Asegúrese de su firewall permitir listas permiten para la conectividad a los extremos de Office 365.</span><span class="sxs-lookup"><span data-stu-id="625ce-108">Ensure your firewall allow lists allow for connectivity to Office 365 endpoints.</span></span>
    
2. <span data-ttu-id="625ce-109">Use la infraestructura de proxy para permitir la conectividad a Internet con caracteres comodín y los destinos no publicados.</span><span class="sxs-lookup"><span data-stu-id="625ce-109">Use your proxy infrastructure to allow Internet connectivity to wildcard and unpublished destinations.</span></span>
    
3. <span data-ttu-id="625ce-110">Mantener una configuración de red perimetral óptimo.</span><span class="sxs-lookup"><span data-stu-id="625ce-110">Maintain an optimal perimeter network configuration.</span></span>
    
4. <span data-ttu-id="625ce-111">[Asegúrese de que está obteniendo la mejor conectividad](https://aka.ms/o365perfprinciples).</span><span class="sxs-lookup"><span data-stu-id="625ce-111">[Ensure you're getting the best connectivity](https://aka.ms/o365perfprinciples).</span></span>
    
5. <span data-ttu-id="625ce-112">Lea los [Principios de conectividad de red de Office 365](office-365-network-connectivity-principles.md) para comprender los principios de conectividad para administrar el tráfico de Office 365 y obtener el mejor rendimiento posible de forma segura.</span><span class="sxs-lookup"><span data-stu-id="625ce-112">Read [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md) to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance.</span></span> 
    
![Conectarse a Office 365 a través de firewalls y servidores proxy.](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)
  
## <a name="update-your-firewalls-outbound-allow-lists"></a><span data-ttu-id="625ce-114">Actualización del firewall de salida permitir listas</span><span class="sxs-lookup"><span data-stu-id="625ce-114">Update your firewall's outbound allow lists</span></span>

<span data-ttu-id="625ce-p103">Puede optimizar la red por enviar que todas las solicitudes de red de Office 365 directamente a través de su servidor de seguridad de confianza, omitir la inspección del nivel de todos los paquetes adicionales o procesamiento. Esto reduce el rendimiento lento de latencia y reduce los requisitos de capacidad de perímetro. La forma más sencilla para elegir qué red solicita confiar es usar nuestros archivos PAC previamente creados en la ficha **servidores proxy de** arriba.</span><span class="sxs-lookup"><span data-stu-id="625ce-p103">You can optimize your network by sending all trusted Office 365 network requests directly through your firewall, bypassing all additional packet level inspection or processing. This reduces slow performance from latency and reduces your perimeter capacity requirements. The easiest way to choose which network requests to trust is to use our pre-built PAC files on the **Proxies** tab above.</span></span> 
  
<span data-ttu-id="625ce-p104">Si su firewall bloquea el tráfico saliente, querrá garantizar que todos de la dirección IP y FQDN aparecen como **necesarios** en este [archivo XML](https://go.microsoft.com/fwlink/?LinkId=533185) se encuentran en la lista Permitir. Reconocer que todos los servicios requieren el uso de algunos servicios de terceros 3ª. Se no proporcionar las direcciones IP para estos servicios parte 3ª como proveedores de certificado proveedores, redes de distribución de contenido, DNS y así sucesivamente. Para la funcionalidad completa de Office 365, debe ser capaz de llegar a todos los destinos solicitados por Office 365, independientemente de la cantidad de información se publique sobre el destino.</span><span class="sxs-lookup"><span data-stu-id="625ce-p104">If your firewall blocks outbound traffic, you'll want to ensure all of the IP and FQDNs listed as **Required** in this [XML file](https://go.microsoft.com/fwlink/?LinkId=533185) are on the allow list. Recognize all services require the use of some 3rd party services. We don't provide IP addresses for these 3rd party services such as certificate providers, Content Delivery Networks, DNS providers, and so on. For full Office 365 functionality, you must be able to reach all destinations requested by Office 365 regardless of how much information we publish about the destination.</span></span> 
  
<span data-ttu-id="625ce-122">Muchos destinos no tienen una dirección IP publicada o aparecen como un dominio comodín con ningún nombre de dominio completo específico, para usar esta funcionalidad debe poder resolver estas solicitudes de red a la dirección IP actual de direcciones que se solicita y enviar el solicitud de red a través de Internet.</span><span class="sxs-lookup"><span data-stu-id="625ce-122">Many destinations do not have an IP address published or are listed as a wildcard domain with no specific fully qualified domain name, to use this functionality you must be able to resolve these network requests to the current IP address being requested and send the network request over the Internet.</span></span>
  
<span data-ttu-id="625ce-p105">Automatizar el proceso mediante el uso de un firewall que analiza el archivo XML en su nombre y actualiza las reglas automáticamente en función de los servicios o características de que planeación enrutar directamente a través del firewall. También puede usar la herramienta de [Azure rango](https://azurerange.azurewebsites.net/) que se ha generado por la Comunidad y analiza el XML para usted con opciones de exportación de configuración de la lista ruta Cisco XE o ACL, texto sin formato o CSV.</span><span class="sxs-lookup"><span data-stu-id="625ce-p105">Automate your process by using a firewall that parses the XML file on your behalf and updates your rules automatically based on the services or features you plan to route directly through your firewall. You can also use the [Azure Range](https://azurerange.azurewebsites.net/) tool that has been built by the community and parses the XML for you with export options for Cisco XE Route or ACL list configuration, plain text, or CSV.</span></span> 
  
<span data-ttu-id="625ce-125">Una explicación más extensa de los destinos de red está disponible en nuestro [sitio de referencia](urls-and-ip-address-ranges.md) así como a través de nuestro [RSS en función de registro de cambios](https://go.microsoft.com/fwlink/p/?linkid=236301) por lo que se puede suscribir a los cambios.</span><span class="sxs-lookup"><span data-stu-id="625ce-125">A longer explanation of the network destinations is available on our [reference site](urls-and-ip-address-ranges.md) as well through our [RSS based change log](https://go.microsoft.com/fwlink/p/?linkid=236301) so you can subscribe to changes.</span></span> 
  
<span data-ttu-id="625ce-126"><a name="pacfiles"> </a></span><span class="sxs-lookup"><span data-stu-id="625ce-126"></span></span>
## <a name="configure-outbound-paths-with-pac-files"></a><span data-ttu-id="625ce-127">Configurar las rutas de acceso de salida con archivos PAC</span><span class="sxs-lookup"><span data-stu-id="625ce-127">Configure outbound paths with PAC files</span></span>

<span data-ttu-id="625ce-p106">Usar archivos PAC o WPAD para administrar las solicitudes de red que están asociados con Office 365, pero no tienen una dirección IP proporcionada. Las solicitudes de red típicas que se envían a través de un dispositivo de proxy o perimetral provocar latencia adicional. Mientras que la autenticación proxy incurre el impuesto más grande, otros servicios, como la búsqueda de reputación e intentos para inspeccionar paquetes pueden provocar una experiencia de usuario deficiente. Además, estos dispositivos de red perimetral necesitan suficiente capacidad para procesar todas las solicitudes de red. Se recomienda no usar la infraestructura de proxy o inspección para solicitudes de red de Office 365 directas.</span><span class="sxs-lookup"><span data-stu-id="625ce-p106">Use PAC or WPAD files to manage network requests that are associated with Office 365 but don't have an IP address provided. Typical network requests that are sent through a proxy or perimeter device incur additional latency. While proxy authentication incurs the largest tax, other services such as reputation lookup and attempts to inspect packets can cause a poor user experience. Additionally, these perimeter network devices need enough capacity to process all of the network requests. We recommend bypassing your proxy or inspection infrastructure for direct Office 365 network requests.</span></span>
  
<span data-ttu-id="625ce-p107">Use uno de nuestros archivos PAC como punto de partida para determinar qué tráfico de red que se van a enviar a un servidor proxy y que se van a enviar a un servidor de seguridad. Si está familiarizado con los archivos PAC o WPAD, leído esta entrada acerca de los [archivos de implementación PAC](https://blogs.technet.microsoft.com/undocumentedfeatures/2016/04/06/deploying-the-office-365-proxy-pac-to-manage-your-users/) de uno de nuestros consultores de Office 365. Desea revisar estos como punto de partida y modificar para adaptarse a su entorno.</span><span class="sxs-lookup"><span data-stu-id="625ce-p107">Use one of our PAC files as a starting place to determine what network traffic will be sent to a proxy and which will be sent to a firewall. If you're new to PAC or WPAD files, read this post about [deploying PAC files](https://blogs.technet.microsoft.com/undocumentedfeatures/2016/04/06/deploying-the-office-365-proxy-pac-to-manage-your-users/) from one of our Office 365 consultants. You'll want to review these as a starting place and edit to suit your environment.</span></span> 
  
 <span data-ttu-id="625ce-136">**10/7/2018 han actualizado los archivos PAC**.</span><span class="sxs-lookup"><span data-stu-id="625ce-136">**PAC files updated 7/10/2018**.</span></span> 
  
### <a name="1---pac-file-separates-required-internet-fqdns-from-known-office-365-fqdn"></a><span data-ttu-id="625ce-137">#1 - archivo PAC: separa necesarios y los FQDN de Internet desde conocidos Office 365 FQDN.</span><span class="sxs-lookup"><span data-stu-id="625ce-137">#1 - PAC file: Separates required Internet FQDNs from known Office 365 FQDN.</span></span>

<span data-ttu-id="625ce-p108">El primer ejemplo es una demostración de nuestro enfoque recomendado para administrar extremos a través de Internet sólo. Omite al servidor proxy para destinos de Office 365, donde la dirección IP se publica y envía las solicitudes de red restantes para el proxy.</span><span class="sxs-lookup"><span data-stu-id="625ce-p108">The first example is a demonstration of our recommended approach to managing endpoints over the Internet only. Bypasses the proxy for Office 365 destinations where the IP address is published and sends remaining network requests to the proxy.</span></span>
  
<span data-ttu-id="625ce-140">Fragmento de código:</span><span class="sxs-lookup"><span data-stu-id="625ce-140">Code snippet:</span></span>
  
```
// JavaScript source code
//July 2018 - Updates go live 1st August2018
//This PAC file contains all FQDNs needed for all services and splits the traffic between those which Microsoft can provide IPs for (so can be sent through a managed firewall with conditional access if desired) and those which IPs cannot be provided for, so need to go to an unrestricted proxy or egress. 
//Due to the use of wildcards, some extra logic is provided to send traffic to the proxy before a 'direct' wildcard is hit.
//Includes Core ProPlus URLs but not Office Mobile/IPAD/IOS/ANDROID fqdns from https://support.office.com/en-gb/article/Network-requests-in-Office-365-ProPlus-eb73fcd1-ca88-4d02-a74b-2dd3a9f3364d
//Every Effort is made to ensure 100% accuracy but this PAC should be used as an example and cross-checked with your needs and the Office 365 URL &amp; IP page
//Intended only for Worldwide Office 365 instances, which the vast majority of customers will be using
function FindProxyForURL(url, host)
{
    // Define proxy server
    var proxyserver = "PROXY 10.10.10.10:8080";
    var proxyserver2 = "PROXY 10.10.10.11:8080";
    // Make host lowercase
    var lhost = host.toLowerCase();
    host = lhost;
    //Catch explicit FQDNs which need the proxy but are covered under wildcarded FQDNs which have IPs. This has to be done first before the wildcard is hit
    if ((shExpMatch(host, "quicktips.skypeforbusiness.com"))    
        || (shExpMatch(host, "*.um.outlook.com"))
        || (shExpMatch(host, "r3.res.office365.com"))
        || (shExpMatch(host, "r3.res.outlook.com"))
        || (shExpMatch(host, "r4.res.office365.com"))
        || (shExpMatch(host, "xsi.outlook.com"))
        || (shExpMatch(host, "r1.res.office365.com")))
    {
        return proxyserver;
    }
        //Send FQDNs which Microsoft provide IPs for direct, so they can be sent via a firewall
    else if ((isPlainHostName(host))
    || (shExpMatch(host, "*.aria.microsoft.com"))    
    || (shExpMatch(host, "*.dc.trouter.io"))
    || (shExpMatch(host, "*.lync.com"))
    || (shExpMatch(host, "*.manage.office.com"))
    || (shExpMatch(host, "*.office365.com"))
    || (shExpMatch(host, "*.onenote.com"))
    || (shExpMatch(host, "*.outlook.com"))
    || (shExpMatch(host, "*.outlook.office.com"))
    || (shExpMatch(host, "*.portal.cloudappsecurity.com"))
    || (shExpMatch(host, "*.protection.office.com"))
    || (shExpMatch(host, "*.sharepoint.com"))
    || (shExpMatch(host, "*.skype.com"))
    || (shExpMatch(host, "*.skypeforbusiness.com"))
    || (shExpMatch(host, "*.svc.ms"))
    || (shExpMatch(host, "*.teams.microsoft.com"))
    || (shExpMatch(host, "*.yammer.com"))
    || (shExpMatch(host, "*.yammerusercontent.com"))    
    || (shExpMatch(host, "*broadcast.officeapps.live.com"))
    || (shExpMatch(host, "*excel.officeapps.live.com"))
    || (shExpMatch(host, "*onenote.officeapps.live.com"))
    || (shExpMatch(host, "*powerpoint.officeapps.live.com"))
    || (shExpMatch(host, "*view.officeapps.live.com"))
    || (shExpMatch(host, "*visio.officeapps.live.com"))
    || (shExpMatch(host, "*word-edit.officeapps.live.com"))
    || (shExpMatch(host, "*word-view.officeapps.live.com"))
    || (shExpMatch(host, "admin.microsoft.com"))    
    || (shExpMatch(host, "account.office.net"))
    || (shExpMatch(host, "adminwebservice.microsoftonline.com"))
    || (shExpMatch(host, "agent.office.net"))
    || (shExpMatch(host, "api.login.microsoftonline.com"))
    || (shExpMatch(host, "api.passwordreset.microsoftonline.com"))
    || (shExpMatch(host, "apc.delve.office.com"))
    || (shExpMatch(host, "aus.delve.office.com"))
    || (shExpMatch(host, "autologon.microsoftazuread-sso.com"))  
    || (shExpMatch(host, "becws.microsoftonline.com"))
    || (shExpMatch(host, "browser.pipe.aria.microsoft.com"))  
    || (shExpMatch(host, "can.delve.office.com"))
    || (shExpMatch(host, "ccs.login.microsoftonline.com"))
    || (shExpMatch(host, "ccs-sdf.login.microsoftonline.com"))
    || (shExpMatch(host, "clientconfig.microsoftonline-p.net"))
    || (shExpMatch(host, "clientlog.portal.office.com"))
    || (shExpMatch(host, "companymanager.microsoftonline.com"))
    || (shExpMatch(host, "cus-000.tasks.osi.office.net"))
    || (shExpMatch(host, "delve.office.com"))
    || (shExpMatch(host, "device.login.microsoftonline.com"))    
    || (shExpMatch(host, "ea-000.tasks.osi.office.net"))
    || (shExpMatch(host, "eur.delve.office.com"))
    || (shExpMatch(host, "eus-zzz.tasks.osi.office.net"))
    || (shExpMatch(host, "gbr.delve.office.com"))    
    || (shExpMatch(host, "hip.microsoftonline-p.net"))
    || (shExpMatch(host, "hipservice.microsoftonline.com"))
    || (shExpMatch(host, "home.office.com"))
    || (shExpMatch(host, "ind.delve.office.com"))
    || (shExpMatch(host, "jpn.delve.office.com"))
    || (shExpMatch(host, "kor.delve.office.com"))
    || (shExpMatch(host, "lam.delve.office.com"))
    || (shExpMatch(host, "login.microsoft.com"))
    || (shExpMatch(host, "login.microsoftonline.com"))
    || (shExpMatch(host, "login.microsoftonline-p.com"))
    || (shExpMatch(host, "login.windows.net"))
    || (shExpMatch(host, "logincert.microsoftonline.com"))
    || (shExpMatch(host, "loginex.microsoftonline.com"))
    || (shExpMatch(host, "login-us.microsoftonline.com"))     
    || (shExpMatch(host, "manage.office.com"))
    || (shExpMatch(host, "mobile.pipe.aria.microsoft.com"))
    || (shExpMatch(host, "nam.delve.office.com"))
    || (shExpMatch(host, "neu-000.tasks.osi.office.net"))
    || (shExpMatch(host, "nexus.microsoftonline-p.com"))
    || (shExpMatch(host, "nexus.officeapps.live.com"))
    || (shExpMatch(host, "nexusrules.officeapps.live.com"))
    || (shExpMatch(host, "office.live.com"))
    || (shExpMatch(host, "officeapps.live.com"))
    || (shExpMatch(host, "passwordreset.microsoftonline.com"))
    || (shExpMatch(host, "portal.microsoftonline.com"))
    || (shExpMatch(host, "portal.office.com"))
    || (shExpMatch(host, "protection.office.com"))
    || (shExpMatch(host, "provisioningapi.microsoftonline.com"))
    || (shExpMatch(host, "scsinstrument-ss-us.trafficmanager.net"))   
    || (shExpMatch(host, "scsquery-ss-asia.trafficmanager.net")) 
    || (shExpMatch(host, "scsquery-ss-eu.trafficmanager.net")) 
    || (shExpMatch(host, "scsquery-ss-us.trafficmanager.net"))
    || (shExpMatch(host, "sea-000.tasks.osi.office.net"))    
    || (shExpMatch(host, "stamp2.login.microsoftonline.com"))
    || (shExpMatch(host, "suite.office.net"))    
    || (shExpMatch(host, "tasks.office.com"))
    || (shExpMatch(host, "teams.microsoft.com"))
    || (shExpMatch(host, "testconnectivity.microsoft.com"))
    || (shExpMatch(host, "webshell.suite.office.com"))
    || (shExpMatch(host, "weu-000.tasks.osi.office.net"))
    || (shExpMatch(host, "wus-000.tasks.osi.office.net"))
    || (shExpMatch(host, "www.office.com")))
      
    {
        return "DIRECT";
    }
    else
        // Send all unknown IP traffic to Proxy for unrestricted access. This section is not necessary if you have a catchall for all other traffic to go to an unfiltered proxy. 
        //However the fqdns required, but for which we dont have IPs for, are listed here incase you need an explicit list.
   if          ((shExpMatch(host, "*.aadrm.com"))
        || (shExpMatch(host, "*.adhybridhealth.azure.com")) 
        || (shExpMatch(host, "*.adl.windows.com"))   
        || (shExpMatch(host, "*.api.microsoftstream.com"))      
        || (shExpMatch(host, "*.assets-yammer.com"))   
        || (shExpMatch(host, "*.azureedge.net"))            
        || (shExpMatch(host, "*.azurerms.com"))
        || (shExpMatch(host, "*.cloudapp.net"))
        || (shExpMatch(host, "*.entrust.net")) 
        || (shExpMatch(host, "*.geotrust.com"))   
        || (shExpMatch(host, "*.helpshift.com"))   
        || (shExpMatch(host, "*.hockeyapp.net"))    
        || (shExpMatch(host, "*.localytics.com"))    
        || (shExpMatch(host, "*.log.optimizely.com"))    
        || (shExpMatch(host, "*.microsoft.com"))
        || (shExpMatch(host, "*.microsoftonline.com"))
        || (shExpMatch(host, "*.microsoftonline-p.com"))
        || (shExpMatch(host, "*.microsoftonline-p.net"))
        || (shExpMatch(host, "*.msecnd.net"))
        || (shExpMatch(host, "*.msedge.net"))      
        || (shExpMatch(host, "*.msocdn.com")) 
        || (shExpMatch(host, "*.mstea.ms"))    
        || (shExpMatch(host, "*.notification.api.microsoftstream.com")) 
        || (shExpMatch(host, "*.o365weve.com"))     
        || (shExpMatch(host, "*.office.com"))   
        || (shExpMatch(host, "*.office.net"))
        || (shExpMatch(host, "*.omniroot.com"))
        || (shExpMatch(host, "*.onmicrosoft.com"))
        || (shExpMatch(host, "*.phonefactor.net"))
        || (shExpMatch(host, "*.public-trust.com"))
        || (shExpMatch(host, "*.search.production.apac.trafficmanager.net"))
        || (shExpMatch(host, "*.search.production.emea.trafficmanager.net"))
        || (shExpMatch(host, "*.search.production.us.trafficmanager.net"))
        || (shExpMatch(host, "*.secure.skypeassets.com"))  
        || (shExpMatch(host, "*.sfbassets.com"))
        || (shExpMatch(host, "*.sharepointonline.com"))
        || (shExpMatch(host, "*.sway.com"))
        || (shExpMatch(host, "*.symcb.com"))
        || (shExpMatch(host, "*.teams.microsoft.com"))  
        || (shExpMatch(host, "*.tenor.com"))  
        || (shExpMatch(host, "*.symcd.com"))     
        || (shExpMatch(host, "*.users.storage.live.com"))
        || (shExpMatch(host, "*.verisign.com"))
        || (shExpMatch(host, "*.verisign.net"))
        || (shExpMatch(host, "*.windows.net"))
        || (shExpMatch(host, "*cdn.onenote.net"))
        || (shExpMatch(host, "account.activedirectory.windowsazure.com"))
        || (shExpMatch(host, "ad.atdmt.com"))
        || (shExpMatch(host, "admin.onedrive.com"))
        || (shExpMatch(host, "ajax.aspnetcdn.com"))
        || (shExpMatch(host, "aka.ms"))
        || (shExpMatch(host, "amp.azure.net"))
        || (shExpMatch(host, "api.microsoftstream.com"))
        || (shExpMatch(host, "apis.live.net"))  
        || (shExpMatch(host, "apps.identrust.com"))  
        || (shExpMatch(host, "assets.onestore.ms"))
        || (shExpMatch(host, "auth.gfx.ms"))
        || (shExpMatch(host, "cacerts.digicert.com"))        
        || (shExpMatch(host, "cdn.odc.officeapps.live.com"))  
        || (shExpMatch(host, "cdn.onenote.net"))
        || (shExpMatch(host, "cdn.optimizely.com")) 
        || (shExpMatch(host, "cert.int-x3.letsencrypt.org"))
        || (shExpMatch(host, "client.hip.live.com"))
        || (shExpMatch(host, "connect.facebook.net"))        
        || (shExpMatch(host, "crl.globalsign.com"))
        || (shExpMatch(host, "crl.globalsign.net"))
        || (shExpMatch(host, "crl.identrust.com"))    
        || (shExpMatch(host, "crl3.digicert.com"))  
        || (shExpMatch(host, "crl4.digicert.com"))
        || (shExpMatch(host, "cus-odc.officeapps.live.com"))              
        || (shExpMatch(host, "cus-roaming.officeapps.live.com"))
        || (shExpMatch(host, "dc.services.visualstudio.com"))
        || (shExpMatch(host, "domains.live.com"))
        || (shExpMatch(host, "ea-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "ea-roaming.officeapps.live.com"))          
        || (shExpMatch(host, "ecn.dev.virtualearth.net "))   
        || (shExpMatch(host, "eus2-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "eus2-roaming.officeapps.live.com"))             
        || (shExpMatch(host, "eus-odc.officeapps.live.com"))         
        || (shExpMatch(host, "eus-www.sway-cdn.com"))
        || (shExpMatch(host, "eus-www.sway-extensions.com"))        
        || (shExpMatch(host, "firstpartyapps.oaspapps.com"))
        || (shExpMatch(host, "g.live.com"))
        || (shExpMatch(host, "groupsapi2-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi3-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi4-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi-prod.outlookgroups.ms"))   
        || (shExpMatch(host, "isrg.trustid.ocsp.identrust.com"))   
        || (shExpMatch(host, "liverdcxstorage.blob.core.windowsazure.com"))
        || (shExpMatch(host, "management.azure.com"))        
        || (shExpMatch(host, "mem.gfx.ms"))
        || (shExpMatch(host, "mrodevicemgr.officeapps.live.com"))      
        || (shExpMatch(host, "ncus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "ncus-roaming.officeapps.live.com"))                
        || (shExpMatch(host, "neu-000.ocws.officeapps.live.com")) 
        || (shExpMatch(host, "neu-odc.officeapps.live.com"))         
        || (shExpMatch(host, "neu-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "nexus.officeapps.live.com"))
        || (shExpMatch(host, "nexusrules.officeapps.live.com"))
        || (shExpMatch(host, "nps.onyx.azure.net"))
        || (shExpMatch(host, "ocsa.officeapps.live.com"))
        || (shExpMatch(host, "ocsp.digicert.com"))
        || (shExpMatch(host, "ocspx.digicert.com"))
        || (shExpMatch(host, "ocsp.globalsign.com"))
        || (shExpMatch(host, "ocsp.int-x3.letsencrypt.org"))
        || (shExpMatch(host, "ocsp.msocsp.com"))       
        || (shExpMatch(host, "ocsp2.globalsign.com"))
        || (shExpMatch(host, "ocsredir.officeapps.live.com"))
        || (shExpMatch(host, "ocws.officeapps.live.com"))
        || (shExpMatch(host, "odc.officeapps.live.com"))  
        || (shExpMatch(host, "officecdn.microsoft.com.edgekey.net"))            
        || (shExpMatch(host, "officecdn.microsoft.com.edgesuite.net"))              
        || (shExpMatch(host, "ols.officeapps.live.com"))  
        || (shExpMatch(host, "oneclient.sfx.ms"))
        || (shExpMatch(host, "outlook.uservoice.com"))
        || (shExpMatch(host, "platform.linkedin.com"))
        || (shExpMatch(host, "policykeyservice.dc.ad.msft.net"))
        || (shExpMatch(host, "prod.firstpartyapps.oaspapps.com.akadns.net")) 
        || (shExpMatch(host, "r1.res.office365.com"))
        || (shExpMatch(host, "r3.res.office365.com"))
        || (shExpMatch(host, "r4.res.office365.com"))
        || (shExpMatch(host, "s.ytimg.com"))
        || (shExpMatch(host, "scus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "scus-odc.officeapps.live.com"))         
        || (shExpMatch(host, "scus-roaming.officeapps.live.com"))                 
        || (shExpMatch(host, "sea-odc.officeapps.live.com"))         
        || (shExpMatch(host, "sea-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "secure.globalsign.com"))
        || (shExpMatch(host, "site-cdn.onenote.net"))
        || (shExpMatch(host, "skydrive.wns.windows.com"))
        || (shExpMatch(host, "skypemaprdsitus.trafficmanager.net"))   
        || (shExpMatch(host, "spoprod-a.akamaihd.net"))  
        || (shExpMatch(host, "ssw.live.com"))
        || (shExpMatch(host, "staffhub.ms"))
        || (shExpMatch(host, "staffhub.uservoice.com"))
        || (shExpMatch(host, "storage.live.com"))
        || (shExpMatch(host, "sway.com")) 
        || (shExpMatch(host, "teams.microsoft.com"))              
        || (shExpMatch(host, "telemetry.remoteapp.windowsazure.com"))         
        || (shExpMatch(host, "telemetryservice.firstpartyapps.oaspapps.com"))    
        || (shExpMatch(host, "web.microsoftstream.com"))         
        || (shExpMatch(host, "weu-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "weu-odc.officeapps.live.com"))         
        || (shExpMatch(host, "weu-roaming.officeapps.live.com"))
        || (shExpMatch(host, "wu.client.hip.live.com"))
        || (shExpMatch(host, "wus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "wus-firstpartyapps.oaspapps.com"))  
        || (shExpMatch(host, "wus-odc.officeapps.live.com"))         
        || (shExpMatch(host, "wus-roaming.officeapps.live.com"))
        || (shExpMatch(host, "wus-www.sway-cdn.com"))
        || (shExpMatch(host, "wus-www.sway-extensions.com"))   
        || (shExpMatch(host, "www.digicert.com"))
        || (shExpMatch(host, "www.google-analytics.com"))
        || (shExpMatch(host, "www.onedrive.com"))
        || (shExpMatch(host, "www.remoteapp.windowsazure.com"))
        || (shExpMatch(host, "www.youtube.com"))
        || (shExpMatch(host, "xsi.outlook.com")))
        
    {
        return proxyserver;
    }
    //Catchall for all other traffic to another proxy 
else return proxyserver;
}

```

### <a name="2---pac-file-connect-to-office-365-over-the-internet-and-expressroute"></a><span data-ttu-id="625ce-141">#2: archivo PAC: conectarse a Office 365 a través de Internet y ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="625ce-141">#2 - PAC file: Connect to Office 365 over the Internet and ExpressRoute</span></span>
<span data-ttu-id="625ce-142"><a name="bkmk_inet-aer"> </a></span><span class="sxs-lookup"><span data-stu-id="625ce-142"></span></span>

<span data-ttu-id="625ce-p109">El segundo ejemplo es una demostración de nuestro enfoque recomendado para administrar las conexiones de circuitos ExpressRoute e Internet estén disponibles. Envía ExpressRoute anuncian destinos al circuito ExpressRoute y Internet sólo anuncia destinos para el proxy.</span><span class="sxs-lookup"><span data-stu-id="625ce-p109">The second example is a demonstration of our recommended approach to managing connections when ExpressRoute and Internet circuits are available. Sends ExpressRoute advertised destinations to the ExpressRoute circuit and Internet only advertised destinations to the proxy.</span></span>
  
<span data-ttu-id="625ce-145">Fragmento de código:</span><span class="sxs-lookup"><span data-stu-id="625ce-145">Code snippet:</span></span>
  
```
// JavaScript source code
//July 2018 Update
// Consolidated FQDNs of URLS which are reachable via Microsoft peering over ExpressRoute. All other traffic sent to a proxy in this example. 
//Every Effort is made to ensure 100% accuracy but this PAC should be used as an example and cross-checked with your traffic flow needs and the Office 365 URL &amp; IP page. 
//Intended only for Worldwide Office 365 instances, which the vast majority of customers will be using
//PAC presumes all Office 365 BGP communities/route filters are allowed.
function FindProxyForURL(url, host)
{
    // Define proxy server
    var proxyserver = "PROXY 10.10.10.10:8080";
    // Make host lowercase
    var lhost = host.toLowerCase();
    host = lhost;
    //SUB-FQDNs of ExpressRoutable wildcards which need to be explicitly sent to the proxy at the top of the PAC because they arent ER routable
    if ((shExpMatch(host, "xsi.outlook.com"))
        || (shExpMatch(host, "r3.res.outlook.com"))
        || (shExpMatch(host, "quicktips.skypeforbusiness.com"))
        || (shExpMatch(host, "*.um.outlook.com")))                  
    {
        return proxyserver;
    }
        //EXPRESS ROUTE DIRECT
    else if ((isPlainHostName(host))  
            || (shExpMatch(host, "*.aria.microsoft.com"))             
            || (shExpMatch(host, "*.dc.trouter.io"))
            || (shExpMatch(host, "*.lync.com"))
            || (shExpMatch(host, "*.manage.office.com"))
            || (shExpMatch(host, "*.outlook.com"))
            || (shExpMatch(host, "*.outlook.office.com"))
            || (shExpMatch(host, "*.portal.cloudappsecurity.com"))
            || (shExpMatch(host, "*.protection.office.com"))
            || (shExpMatch(host, "*.protection.outlook.com"))
            || (shExpMatch(host, "*.sharepoint.com")) 
            || (shExpMatch(host, "*.skype.com")) 
            || (shExpMatch(host, "*.skypeforbusiness.com")) 
            || (shExpMatch(host, "*.svc.ms"))   
            || (shExpMatch(host, "*.teams.microsoft.com"))  
            || (shExpMatch(host, "*broadcast.officeapps.live.com"))
            || (shExpMatch(host, "*excel.officeapps.live.com"))
            || (shExpMatch(host, "*onenote.officeapps.live.com"))
            || (shExpMatch(host, "*powerpoint.officeapps.live.com"))
            || (shExpMatch(host, "*view.officeapps.live.com"))                                 
            || (shExpMatch(host, "*visio.officeapps.live.com"))
            || (shExpMatch(host, "*word-edit.officeapps.live.com"))
            || (shExpMatch(host, "*word-view.officeapps.live.com"))
            || (shExpMatch(host, "account.office.net"))
            || (shExpMatch(host, "adminwebservice.microsoftonline.com"))
            || (shExpMatch(host, "agent.office.net"))  
            || (shExpMatch(host, "apc.delve.office.com"))
            || (shExpMatch(host, "api.login.microsoftonline.com"))
            || (shExpMatch(host, "api.passwordreset.microsoftonline.com"))
            || (shExpMatch(host, "aus.delve.office.com"))
            || (shExpMatch(host, "autologon.microsoftazuread-sso.com")) 
            || (shExpMatch(host, "becws.microsoftonline.com"))
            || (shExpMatch(host, "browser.pipe.aria.microsoft.com"))  
            || (shExpMatch(host, "can.delve.office.com")) 
            || (shExpMatch(host, "ccs.login.microsoftonline.com"))  
            || (shExpMatch(host, "ccs-sdf.login.microsoftonline.com"))
            || (shExpMatch(host, "clientconfig.microsoftonline-p.net"))
            || (shExpMatch(host, "companymanager.microsoftonline.com"))
            || (shExpMatch(host, "delve.office.com"))
            || (shExpMatch(host, "device.login.microsoftonline.com"))
            || (shExpMatch(host, "domains.live.com")) 
            || (shExpMatch(host, "eur.delve.office.com"))
            || (shExpMatch(host, "gbr.delve.office.com"))
            || (shExpMatch(host, "hip.microsoftonline-p.net"))
            || (shExpMatch(host, "hipservice.microsoftonline.com"))
            || (shExpMatch(host, "home.office.com"))
            || (shExpMatch(host, "ind.delve.office.com"))
            || (shExpMatch(host, "jpn.delve.office.com"))
            || (shExpMatch(host, "kor.delve.office.com"))
            || (shExpMatch(host, "lam.delve.office.com"))
            || (shExpMatch(host, "login.microsoft.com"))
            || (shExpMatch(host, "login.microsoftonline.com"))
            || (shExpMatch(host, "login.microsoftonline-p.net"))
            || (shExpMatch(host, "login.windows.net"))
            || (shExpMatch(host, "logincert.microsoftonline.com"))
            || (shExpMatch(host, "loginex.microsoftonline.com"))
            || (shExpMatch(host, "login-us.microsoftonline.com"))
            || (shExpMatch(host, "manage.office.com"))
            || (shExpMatch(host, "mobile.pipe.aria.microsoft.com"))
            || (shExpMatch(host, "nam.delve.office.com"))
            || (shExpMatch(host, "nexus.microsoftonline-p.net"))
            || (shExpMatch(host, "office.live.com")) 
            || (shExpMatch(host, "officeapps.live.com")) 
            || (shExpMatch(host, "outlook.office365.com")) 
            || (shExpMatch(host, "passwordreset.microsoftonline.com"))
            || (shExpMatch(host, "portal.office.com"))
            || (shExpMatch(host, "protection.office.com"))
            || (shExpMatch(host, "provisioningapi.microsoftonline.com"))
            || (shExpMatch(host, "scsinstrument-ss-us.trafficmanager.net")) 
            || (shExpMatch(host, "scsquery-ss-asia.trafficmanager.net"))
            || (shExpMatch(host, "scsquery-ss-eu.trafficmanager.net")) 
            || (shExpMatch(host, "scsquery-ss-us.trafficmanager.net"))  
            || (shExpMatch(host, "signup.microsoft.com"))
            || (shExpMatch(host, "smtp.office365.com"))  
            || (shExpMatch(host, "stamp2.login.microsoftonline.com"))
            || (shExpMatch(host, "suite.office.net")) 
            || (shExpMatch(host, "teams.microsoft.com")) 
            || (shExpMatch(host, "webshell.suite.office.com")) 
            || (shExpMatch(host, "www.office.com")))             
       
    {
        return "DIRECT";
    }
        //Catchall for all other traffic to proxy
    else
    {
        return proxyserver;
    }
}

```

### <a name="3---pac-file-manage-all-office-365-destinations-collectively"></a><span data-ttu-id="625ce-146">#3 - archivo PAC: administrar de forma colectiva todos los destinos de Office 365</span><span class="sxs-lookup"><span data-stu-id="625ce-146">#3 - PAC file: Manage all Office 365 destinations collectively</span></span>
<span data-ttu-id="625ce-147"><a name="bkmk_inet-direct"> </a></span><span class="sxs-lookup"><span data-stu-id="625ce-147"></span></span>

<span data-ttu-id="625ce-p110">El tercer ejemplo muestra cómo enviar todas las solicitudes de red asociadas con Office 365 a un único destino. Esto se suele utilizar para omitir la inspección de todos los de las solicitudes de red de Office 365 y ofrece un formato donde todas las publicadas extremos está en la lista en el formato de PAC que se usará para la personalización.</span><span class="sxs-lookup"><span data-stu-id="625ce-p110">The third example demonstrates sending all network requests associated with Office 365 to a single destination. This is commonly used to bypass all inspection of Office 365 network requests and offers you a format where all published endpoints are in list in the PAC format to use for your customization.</span></span>
  
<span data-ttu-id="625ce-150">Fragmento de código:</span><span class="sxs-lookup"><span data-stu-id="625ce-150">Code snippet:</span></span>
  
```
// JavaScript source code
//July 2018 Update new URLS go live 1st August 2018 -
//Consolidated FQDNs required to access Office 365 - All services including optional components covered and elements covered under wildcards removed. 
//Some repeated domains have been consoliodated into unpublished wildcards in order to keep the file as small as possible.
//Includes Core ProPlus URLs but not Office Mobile/IPAD/IOS/ANDROID fqdns from https://support.office.com/en-gb/article/Network-requests-in-Office-365-ProPlus-eb73fcd1-ca88-4d02-a74b-2dd3a9f3364d
//Every Effort is made to ensure 100% accuracy but this PAC should be used as an example and cross-checked with your needs and the Office 365 URL &amp; IP page
//Intended only for Worldwide Office 365 instances, which the vast majority of customers will be using
function FindProxyForURL(url, host)
{
    // Define proxy server
    var proxyserver = "PROXY 10.10.10.10:8080";
    // Make host lowercase
    var lhost = host.toLowerCase();
    host = lhost;
   if  ((shExpMatch(host, "*.aadrm.com"))
        || (shExpMatch(host, "*.adhybridhealth.azure.com"))
        || (shExpMatch(host, "*.adl.windows.com"))
        || (shExpMatch(host, "*.api.microsoftstream.com"))  
        || (shExpMatch(host, "*.assets-yammer.com"))
        || (shExpMatch(host, "autologon.microsoftazuread-sso.com"))  
        || (shExpMatch(host, "*.azureedge.net"))   
        || (shExpMatch(host, "*.azurerms.com"))
        || (shExpMatch(host, "*.cloudapp.net")) 
        || (shExpMatch(host, "*.dc.trouter.io"))
        || (shExpMatch(host, "*.entrust.net")) 
        || (shExpMatch(host, "*.geotrust.com"))
        || (shExpMatch(host, "*.helpshift.com"))
        || (shExpMatch(host, "*.hockeyapp.net"))       
        || (shExpMatch(host, "*.localytics.com"))
        || (shExpMatch(host, "*.log.optimizely.com"))     
        || (shExpMatch(host, "*.lync.com"))
        || (shExpMatch(host, "*.microsoft.com"))
        || (shExpMatch(host, "*.microsoftonline.com"))
        || (shExpMatch(host, "*.microsoftonline-p.com"))
        || (shExpMatch(host, "*.microsoftonline-p.net"))
        || (shExpMatch(host, "*.msecnd.net"))
        || (shExpMatch(host, "*.msedge.net"))
        || (shExpMatch(host, "*.msocdn.com"))
        || (shExpMatch(host, "*.mstea.ms"))
        || (shExpMatch(host, "*.o365weve.com"))
        || (shExpMatch(host, "*.office.com"))
        || (shExpMatch(host, "*.office.net"))
        || (shExpMatch(host, "*.office365.com"))
        || (shExpMatch(host, "*.omniroot.com"))
        || (shExpMatch(host, "*.onenote.com"))
        || (shExpMatch(host, "*.onmicrosoft.com"))
        || (shExpMatch(host, "*.outlook.com"))
        || (shExpMatch(host, "*.phonefactor.net")) 
        || (shExpMatch(host, "*.portal.cloudappsecurity.com"))
        || (shExpMatch(host, "*.public-trust.com"))
        || (shExpMatch(host, "*.search.production.apac.trafficmanager.net"))
        || (shExpMatch(host, "*.search.production.emea.trafficmanager.net"))
        || (shExpMatch(host, "*.search.production.us.trafficmanager.net"))
        || (shExpMatch(host, "*.secure.skypeassets.com"))
        || (shExpMatch(host, "*.sfbassets.com"))  
        || (shExpMatch(host, "*.sharepoint.com"))
        || (shExpMatch(host, "*.sharepointonline.com"))
        || (shExpMatch(host, "*.skype.com"))
        || (shExpMatch(host, "*.skypeforbusiness.com"))
        || (shExpMatch(host, "*.svc.ms")) 
        || (shExpMatch(host, "*.sway.com"))
        || (shExpMatch(host, "*.symcb.com"))
        || (shExpMatch(host, "*.symcd.com"))
        || (shExpMatch(host, "*.tenor.com"))
        || (shExpMatch(host, "*.users.storage.live.com"))
        || (shExpMatch(host, "*.verisign.com"))
        || (shExpMatch(host, "*.verisign.net"))
        || (shExpMatch(host, "*.windows.net"))
        || (shExpMatch(host, "*.yammer.com"))
        || (shExpMatch(host, "*.yammerusercontent.com"))         
        || (shExpMatch(host, "*broadcast.officeapps.live.com"))
        || (shExpMatch(host, "*cdn.onenote.net"))
        || (shExpMatch(host, "*excel.officeapps.live.com"))
        || (shExpMatch(host, "*onenote.officeapps.live.com"))
        || (shExpMatch(host, "*powerpoint.officeapps.live.com"))
        || (shExpMatch(host, "*view.officeapps.live.com"))
        || (shExpMatch(host, "*visio.officeapps.live.com"))
        || (shExpMatch(host, "*word-edit.officeapps.live.com"))
        || (shExpMatch(host, "*word-view.officeapps.live.com"))    
        || (shExpMatch(host, "account.activedirectory.windowsazure.com"))
        || (shExpMatch(host, "ad.atdmt.com"))
        || (shExpMatch(host, "admin.onedrive.com"))
        || (shExpMatch(host, "ajax.aspnetcdn.com"))
        || (shExpMatch(host, "aka.ms"))
        || (shExpMatch(host, "amp.azure.net"))
        || (shExpMatch(host, "api.microsoftstream.com"))
        || (shExpMatch(host, "apis.live.net"))
        || (shExpMatch(host, "apps.identrust.com")) 
        || (shExpMatch(host, "assets.onestore.ms"))
        || (shExpMatch(host, "auth.gfx.ms"))
        || (shExpMatch(host, "cacerts.digicert.com"))    
        || (shExpMatch(host, "cdn.odc.officeapps.live.com"))  
        || (shExpMatch(host, "cdn.onenote.net"))
        || (shExpMatch(host, "cdn.optimizely.com"))
        || (shExpMatch(host, "cert.int-x3.letsencrypt.org"))
        || (shExpMatch(host, "client.hip.live.com"))     
        || (shExpMatch(host, "connect.facebook.net"))
        || (shExpMatch(host, "crl.globalsign.com"))
        || (shExpMatch(host, "crl.globalsign.net"))
        || (shExpMatch(host, "crl.identrust.com"))    
        || (shExpMatch(host, "crl3.digicert.com"))  
        || (shExpMatch(host, "crl4.digicert.com"))
        || (shExpMatch(host, "cus-odc.officeapps.live.com"))              
        || (shExpMatch(host, "cus-roaming.officeapps.live.com"))      
        || (shExpMatch(host, "dc.services.visualstudio.com"))
        || (shExpMatch(host, "domains.live.com"))
        || (shExpMatch(host, "ea-000.ocws.officeapps.live.com")) 
        || (shExpMatch(host, "ea-roaming.officeapps.live.com"))           
        || (shExpMatch(host, "ecn.dev.virtualearth.net"))
        || (shExpMatch(host, "eus2-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "eus2-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "eus-odc.officeapps.live.com"))              
        || (shExpMatch(host, "eus-www.sway-cdn.com"))
        || (shExpMatch(host, "eus-www.sway-extensions.com"))
        || (shExpMatch(host, "firstpartyapps.oaspapps.com"))
        || (shExpMatch(host, "g.live.com"))
        || (shExpMatch(host, "groupsapi2-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi3-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi4-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "isrg.trustid.ocsp.identrust.com"))
        || (shExpMatch(host, "liverdcxstorage.blob.core.windowsazure.com"))
        || (shExpMatch(host, "management.azure.com"))
        || (shExpMatch(host, "mem.gfx.ms"))
        || (shExpMatch(host, "mrodevicemgr.officeapps.live.com"))               
        || (shExpMatch(host, "ncus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "ncus-roaming.officeapps.live.com"))                 
        || (shExpMatch(host, "neu-000.ocws.officeapps.live.com")) 
        || (shExpMatch(host, "neu-odc.officeapps.live.com"))              
        || (shExpMatch(host, "neu-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "nexus.officeapps.live.com"))
        || (shExpMatch(host, "nexusrules.officeapps.live.com"))
        || (shExpMatch(host, "nps.onyx.azure.net"))   
        || (shExpMatch(host, "ocsa.officeapps.live.com"))
        || (shExpMatch(host, "ocsp.digicert.com"))
        || (shExpMatch(host, "ocsp.globalsign.com"))
        || (shExpMatch(host, "ocsp.int-x3.letsencrypt.org"))
        || (shExpMatch(host, "ocsp.msocsp.com"))     
        || (shExpMatch(host, "ocsp2.globalsign.com")) 
        || (shExpMatch(host, "ocspx.digicert.com"))
        || (shExpMatch(host, "ocsredir.officeapps.live.com"))
        || (shExpMatch(host, "ocws.officeapps.live.com"))
        || (shExpMatch(host, "odc.officeapps.live.com"))  
        || (shExpMatch(host, "office.live.com"))
        || (shExpMatch(host, "officeapps.live.com"))
        || (shExpMatch(host, "officecdn.microsoft.com.edgekey.net"))              
        || (shExpMatch(host, "officecdn.microsoft.com.edgesuite.net"))
        || (shExpMatch(host, "ols.officeapps.live.com"))  
        || (shExpMatch(host, "oneclient.sfx.ms"))
        || (shExpMatch(host, "outlook.uservoice.com"))
        || (shExpMatch(host, "platform.linkedin.com"))
        || (shExpMatch(host, "policykeyservice.dc.ad.msft.net"))
        || (shExpMatch(host, "prod.firstpartyapps.oaspapps.com.akadns.net"))
        || (shExpMatch(host, "s.ytimg.com"))
        || (shExpMatch(host, "s0.assets-yammer.com"))  
        || (shExpMatch(host, "scsinstrument-ss-us.trafficmanager.net")) 
        || (shExpMatch(host, "scsquery-ss-asia.trafficmanager.net"))
        || (shExpMatch(host, "scsquery-ss-eu.trafficmanager.net")) 
        || (shExpMatch(host, "scsquery-ss-us.trafficmanager.net")) 
        || (shExpMatch(host, "scus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "scus-odc.officeapps.live.com"))         
        || (shExpMatch(host, "scus-roaming.officeapps.live.com"))                 
        || (shExpMatch(host, "sea-odc.officeapps.live.com"))              
        || (shExpMatch(host, "sea-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "secure.globalsign.com"))
        || (shExpMatch(host, "site-cdn.onenote.net"))
        || (shExpMatch(host, "skydrive.wns.windows.com"))
        || (shExpMatch(host, "skypemaprdsitus.trafficmanager.net"))
        || (shExpMatch(host, "spoprod-a.akamaihd.net"))
        || (shExpMatch(host, "ssw.live.com"))
        || (shExpMatch(host, "staffhub.ms"))
        || (shExpMatch(host, "staffhub.uservoice.com"))    
        || (shExpMatch(host, "storage.live.com"))
        || (shExpMatch(host, "telemetry.remoteapp.windowsazure.com"))
        || (shExpMatch(host, "telemetryservice.firstpartyapps.oaspapps.com"))
        || (shExpMatch(host, "web.microsoftstream.com"))   
        || (shExpMatch(host, "weu-000.ocws.officeapps.live.com")) 
        || (shExpMatch(host, "weu-odc.officeapps.live.com"))              
        || (shExpMatch(host, "weu-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "wu.client.hip.live.com"))
        || (shExpMatch(host, "wus-000.ocws.officeapps.live.com"))  
        || (shExpMatch(host, "wus-firstpartyapps.oaspapps.com"))  
        || (shExpMatch(host, "wus-odc.officeapps.live.com"))              
        || (shExpMatch(host, "wus-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "wus-www.sway-cdn.com"))
        || (shExpMatch(host, "wus-www.sway-extensions.com"))        
        || (shExpMatch(host, "www.digicert.com"))
        || (shExpMatch(host, "www.google-analytics.com"))
        || (shExpMatch(host, "www.onedrive.com"))
        || (shExpMatch(host, "www.remoteapp.windowsazure.com"))
        || (shExpMatch(host, "www.youtube.com")))
    {
        return proxyserver;
    }
        //Catchall for all other traffic to another proxy
    else return "PROXY 10.10.10.11:8080";
}

```

### <a name="use-custom-scripts-or-manually-create-your-own-pac-files"></a><span data-ttu-id="625ce-151">Usar secuencias de comandos personalizadas o crear manualmente sus propios archivos PAC</span><span class="sxs-lookup"><span data-stu-id="625ce-151">Use custom scripts or manually create your own PAC files</span></span>
<span data-ttu-id="625ce-152"><a name="pacfiles_manual"> </a></span><span class="sxs-lookup"><span data-stu-id="625ce-152"></span></span>

<span data-ttu-id="625ce-p111">Aquí tiene unas más herramientas de la Comunidad, si ha creado algo que le gustaría compartir deje una nota en los comentarios. Ninguno de la Comunidad de herramientas que se mencionan en este artículo son oficialmente compatible o mantenida por Microsoft y se proporcionan aquí para su comodidad.</span><span class="sxs-lookup"><span data-stu-id="625ce-p111">Here's a few more tools from the community, if you've built something you'd like to share leave a note in the comments. None of the community tools referenced in this article are officially supported or maintained by Microsoft and are provided here for your convenience.</span></span>
  
- <span data-ttu-id="625ce-p112">Es la herramienta más antigua de generado por la Comunidad para ayudar a administrar el proceso, una herramienta creada por un miembro de la Comunidad de Office 365. Éste es el vínculo para [Descargar](https://gallery.technet.microsoft.com/Office-365-Proxy-Pac-60fb28f7).</span><span class="sxs-lookup"><span data-stu-id="625ce-p112">This is the oldest community generated tool to help manage the process, a tool built by a member of the Office 365 community. Here is link to [download](https://gallery.technet.microsoft.com/Office-365-Proxy-Pac-60fb28f7).</span></span>
    
- <span data-ttu-id="625ce-157">Prueba de concepto con reglas de firewall exportable: [API de IP de Microsoft en la nube](https://mscloudips.azurewebsites.net/).</span><span class="sxs-lookup"><span data-stu-id="625ce-157">Proof of Concept with exportable firewall rules: [Microsoft Cloud IP API](https://mscloudips.azurewebsites.net/).</span></span>
    
- <span data-ttu-id="625ce-158">Desde Praktyk de TI: [Conversión de RSS](https://gallery.technet.microsoft.com/Convert-the-RSS-channel-5efe18b7) y [conversión de XML](https://gallery.technet.microsoft.com/Convert-the-O365IPAddresses-9890d896).</span><span class="sxs-lookup"><span data-stu-id="625ce-158">From IT Praktyk: [RSS conversion](https://gallery.technet.microsoft.com/Convert-the-RSS-channel-5efe18b7) and [XML conversion](https://gallery.technet.microsoft.com/Convert-the-O365IPAddresses-9890d896).</span></span>
    
- <span data-ttu-id="625ce-159">De Peter Abele: [Descargar](https://gallery.technet.microsoft.com/How-to-create-an-up-to-b1fc33f3).</span><span class="sxs-lookup"><span data-stu-id="625ce-159">From Peter Abele: [Download](https://gallery.technet.microsoft.com/How-to-create-an-up-to-b1fc33f3).</span></span>
    
- <span data-ttu-id="625ce-p113">Usar el análisis de la red para determinar la red que solicita debe omitir la infraestructura de proxy. Los FQDN más comunes que se utiliza para omitir a los servidores proxy del cliente incluyen los siguientes debido al volumen de tráfico de red enviados y recibidos desde estos extremos.</span><span class="sxs-lookup"><span data-stu-id="625ce-p113">Use your network analysis to determine which network requests should bypass your proxy infrastructure. The most common FQDNs used to bypass customer proxies include the following due to the volume of network traffic sent and received from these endpoints.</span></span>
    
  ```
  outlook.office365.com
  outlook.office.com
  <tenant-name>.sharepoint.com
  <tenant-name>-my.sharepoint.com
  <tenant-name>-<app>.sharepoint.com
  *.Lync.com
  
  ```

- <span data-ttu-id="625ce-162">Asegúrese de que las solicitudes de red que se envían directamente al servidor de seguridad tienen una entrada correspondiente en el servidor de seguridad Permitir lista Permitir que la solicitud pase a través de.</span><span class="sxs-lookup"><span data-stu-id="625ce-162">Ensure any network requests being sent to your firewall directly have a corresponding entry in the firewall allow list to allow the request to go through.</span></span>
    
## <a name="perimeter-network-integration"></a><span data-ttu-id="625ce-163">Integración de la red perimetral</span><span class="sxs-lookup"><span data-stu-id="625ce-163">Perimeter network integration</span></span>
<span data-ttu-id="625ce-164"><a name="BKMK_Perimeter"> </a></span><span class="sxs-lookup"><span data-stu-id="625ce-164"></span></span>

<span data-ttu-id="625ce-165">¿Sabía que... de Microsoft WAN es una de las redes troncales mayores en el mundo?</span><span class="sxs-lookup"><span data-stu-id="625ce-165">Did you know Microsoft's WAN is one of the largest backbones in the world?</span></span>
  
<span data-ttu-id="625ce-p114">Es true, que esta red masiva es lo que hace que Office 365 y nuestras otros servicios de nube funcionan con independencia de dónde en el mundo que es. Nuestra red consta de gran ancho de banda, latencia baja, vínculos con capacidad de conmutación por error con miles de millas de ruta de propiedad privada de fibra oscura y multi-Terabit conexiones entre los nodos de centros de datos y el borde, todos para facilitar el uso de nuestros servicios en la nube.</span><span class="sxs-lookup"><span data-stu-id="625ce-p114">It's true, this massive network is what makes Office 365 and our other cloud services work regardless of where in the world you are. Our network consists of high bandwidth, low latency, fail-over capable links with thousands of route miles of privately owned dark fiber, and multi-Terabit connections between datacenters and edge nodes, all to make it easier to use our cloud services.</span></span>
  
<span data-ttu-id="625ce-p115">Con una red similar, desea que los dispositivos de su organización se conecten a nuestra red de tan pronto como sea posible. Con relaciones de interconexión ISP más 2500 globalmente y 70 puntos de presencia, introducción desde la red a nuestro debería ser transparente. No se puede dañar a dedicar unos minutos, asegurándose de que relación de interconexión de su ISP es el más óptima, [le presentamos algunos ejemplos](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__) de buena y no tan buena interconexión no intervención a nuestra red.</span><span class="sxs-lookup"><span data-stu-id="625ce-p115">With a network like this, you want your organization's devices to connect to our network as soon as possible. With over 2500 ISP peering relationships globally and 70 points of presence, getting from your network to ours should be seamless. It can't hurt to spend a few minutes making sure your ISP's peering relationship is the most optimal, [here's a few examples](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__) of good and not so good peering hand-offs to our network.</span></span> 
  
<span data-ttu-id="625ce-p116">Puede manualmente o configurar automáticamente los dispositivos de la red para controlar las solicitudes de red del aplicación de Office 365, dependiendo de su equipo de forma óptima. Los cambios de configuración que debe tomar controlar el tráfico de red de Office 365 de forma óptima dependerá de su entorno. Office 365 red solicitudes pueden beneficiarse de las configuraciones de red que permiten lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="625ce-p116">You can manually or automatically configure the devices on your network to optimally handle Office 365 application network requests, depending on your equipment. What configuration changes you need to make to optimally handle Office 365 network traffic will depend on your environment. Office 365 network requests may benefit from network configurations that allow the following:</span></span>
  
- <span data-ttu-id="625ce-174">Prioridad sobre el tráfico de red menos importante.</span><span class="sxs-lookup"><span data-stu-id="625ce-174">Priority over less critical network traffic.</span></span>
    
- <span data-ttu-id="625ce-p117">Enrutar a una salida local a fin de evitar backhauling a través de una red WAN lenta vínculo mientras se aprovecha la latencia baja disponible en la red de Microsoft. [Esta es una buena explicación](https://blogs.technet.microsoft.com/onthewire/2017/05/03/office-365-connectivity-guidance-part-2/) basado en contrataciones de clientes.</span><span class="sxs-lookup"><span data-stu-id="625ce-p117">Routing to a local egress to avoid backhauling over a slow WAN link while taking advantage of the low latency available on the Microsoft network. [Here's a good discussion](https://blogs.technet.microsoft.com/onthewire/2017/05/03/office-365-connectivity-guidance-part-2/) based on customer engagements.</span></span> 
    
- <span data-ttu-id="625ce-177">Uso de DNS cerca de una salida local para asegurarse de la solicitud de red que deja la salida local llega a la ubicación de interconexión de Microsoft más cercana.</span><span class="sxs-lookup"><span data-stu-id="625ce-177">Using DNS near a local egress to ensure the network request that leaves the local egress arrives at the nearest Microsoft peering location.</span></span>
    
- <span data-ttu-id="625ce-178">Exclusión de inspección profunda del paquete u otros para satisfacer los requisitos de latencia en escala de procesamiento de paquetes de red intensiva.</span><span class="sxs-lookup"><span data-stu-id="625ce-178">Exclusion from deep packet inspection or other intensive network packet processing to meet latency requirements at scale.</span></span>
    
<span data-ttu-id="625ce-p118">Dispositivos de red modernos incluyen las capacidades para administrar las solicitudes de red para las aplicaciones de confianza, como Office 365 de forma diferente que el tráfico de Internet que no se confía y genérico. Con el panorama de emergente de soluciones SD WAN, también se puede realizar dicha diferenciación de selección de ruta de acceso y de tráfico con conocimiento del estado cambiante de la red como punto de disponibilidad de tiempo, latencia o el rendimiento de las distintas rutas de acceso de conectividad entre el usuario y la nube.</span><span class="sxs-lookup"><span data-stu-id="625ce-p118">Modern network devices include capabilities to manage network requests for trusted applications such as Office 365 differently than generic, untrusted Internet traffic. With the emerging landscape of SD-WAN solutions, such differentiation of traffic and path selection can also be performed with awareness of the changing state of the network, such as point in time availability, latency or performance of various connectivity paths between the user and the cloud.</span></span>
  
<span data-ttu-id="625ce-181">Vea [red y migración de planeación para Office 365](network-and-migration-planning.md), [solución de problemas de rendimiento de planeación de Office 365](performance-troubleshooting-plan.md)y [lista de comprobación de planeación de implementación para Office 365](deployment-planning-checklist.md) para obtener orientación adicional acerca de cómo planear la configuración de red.</span><span class="sxs-lookup"><span data-stu-id="625ce-181">See [Network and migration planning for Office 365](network-and-migration-planning.md), [Performance troubleshooting plan for Office 365](performance-troubleshooting-plan.md), and [Deployment planning checklist for Office 365](deployment-planning-checklist.md) for additional guidance on planning your network configuration.</span></span> 
  
### <a name="to-implement-this-scenario"></a><span data-ttu-id="625ce-182">Para implementar este escenario:</span><span class="sxs-lookup"><span data-stu-id="625ce-182">To implement this scenario:</span></span>

<span data-ttu-id="625ce-p119">Compruebe con su proveedor de soluciones o servicio de red si pueden utilizar direcciones URL en Office 365 y las definiciones de IP de XML para facilitar una sobrecarga local (para el usuario), bajo salida para Office 365 el tráfico de red, administración su prioridad con respecto a otras aplicaciones y ajustan el ruta de acceso de red para las conexiones de Office 365 en la red de Microsoft según las condiciones de red cambiantes. Algunas soluciones de descargan y automatizan la definición de direcciones URL en Office 365 y XMLs IP en sus pilas.</span><span class="sxs-lookup"><span data-stu-id="625ce-p119">Check with your network solution or service provider if they can use Office 365 URL and IP definitions from XML to facilitate local (to the user), low overhead network egress for Office 365 traffic, manage its priority relative to other applications and adjust the network path for Office 365 connections into Microsoft network depending on changing network conditions. Some solutions download and automate Office 365 URL and IP XMLs definition in their stacks.</span></span>
  
<span data-ttu-id="625ce-185">Asegúrese siempre de que la solución implementada tiene necesario grado de resistencia, redundancia de geo adecuado de la ruta de acceso de red para el tráfico de Office 365 y los cambios realizados en IP y URL de Office 365 adapta como se convierten en publicado.</span><span class="sxs-lookup"><span data-stu-id="625ce-185">Always ensure that the implemented solution has necessary degree of resiliency, appropriate geo-redundancy of the network path for Office 365 traffic and accommodates changes to Office 365 URLs and IPs as they become published.</span></span>
  
## <a name="web-service"></a><span data-ttu-id="625ce-186">Servicio web</span><span class="sxs-lookup"><span data-stu-id="625ce-186">Web service</span></span>
<span data-ttu-id="625ce-187"><a name="webservice"> </a></span><span class="sxs-lookup"><span data-stu-id="625ce-187"></span></span>

<span data-ttu-id="625ce-p120">Para ayudarle a identificar y diferenciar el tráfico de red de Office 365, un nuevo servicio web publica los extremos de Office 365, haciendo que sea más fácil para evaluar, configurar y Manténgase actualizado con los cambios. Este nuevo servicio de web (ahora en la vista previa), eventualmente reemplazará las listas de extremos en el artículo [las direcciones URL de Office 365 y los intervalos de direcciones IP](urls-and-ip-address-ranges.md) , junto con las versiones de RSS y XML de los datos. Estas de formato de datos de extremo se planea desfasada en 2 de octubre de 2018.</span><span class="sxs-lookup"><span data-stu-id="625ce-p120">To help you better identify and differentiate Office 365 network traffic, a new web service publishes Office 365 endpoints, making it easier for you to evaluate, configure, and stay up to date with changes. This new web service (now in preview), will eventually replace the lists of endpoints in the [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md) article, along with the RSS and XML versions of that data. These format of endpoint data are planned to be phased out on October 2, 2018.</span></span> 
  
<span data-ttu-id="625ce-191">Como un cliente o un proveedor de dispositivos de red perimetral, puede crear con el nuevo servicio web basado en REST para la dirección IP de Office 365 y las entradas de FQDN.</span><span class="sxs-lookup"><span data-stu-id="625ce-191">As a customer or a network perimeter device vendor, you can build against the new REST-based web service for the Office 365 IP address and FQDN entries.</span></span>
  
- <span data-ttu-id="625ce-192">Para obtener la versión más reciente de los intervalos de direcciones IP y URL de Office 365, use [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="625ce-192">For the latest version of the Office 365 URLs and IP address ranges, use [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
    
- <span data-ttu-id="625ce-193">Para los datos en la página de intervalos de direcciones IP para los servidores proxy y las direcciones URL de Office 365, use [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="625ce-193">For the data on the Office 365 URLs and IP address ranges page for firewalls and proxy servers, use [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
    
- <span data-ttu-id="625ce-194">Para obtener los cambios más recientes, utilice [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="625ce-194">To get the latest changes, use [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
    
<span data-ttu-id="625ce-195">Como un cliente, puede usar este servicio web para:</span><span class="sxs-lookup"><span data-stu-id="625ce-195">As a customer, you can use this web service to:</span></span> 
  
- <span data-ttu-id="625ce-196">Actualizar los scripts de PowerShell para obtener datos de extremo de Office 365 y modificar cualquier formato para los dispositivos de redes.</span><span class="sxs-lookup"><span data-stu-id="625ce-196">Update your PowerShell scripts to obtain Office 365 endpoint data and modify any formatting for your networking devices.</span></span>
    
- <span data-ttu-id="625ce-197">Use esta información para actualizar archivos de PAC implementados en equipos cliente.</span><span class="sxs-lookup"><span data-stu-id="625ce-197">Use this information to update PAC files deployed to client computers.</span></span>
    
<span data-ttu-id="625ce-198">Como un proveedor de dispositivos de red perimetral, puede usar este servicio web para:</span><span class="sxs-lookup"><span data-stu-id="625ce-198">As a network perimeter device vendor, you can use this web service to:</span></span> 
  
- <span data-ttu-id="625ce-199">Crear y probar el software de dispositivo para descargar la lista para la configuración automatizada.</span><span class="sxs-lookup"><span data-stu-id="625ce-199">Create and test device software to download the list for automated configuration.</span></span> 
    
- <span data-ttu-id="625ce-200">Comprobar la versión actual.</span><span class="sxs-lookup"><span data-stu-id="625ce-200">Check for the current version.</span></span>
    
- <span data-ttu-id="625ce-201">Obtener los cambios actuales.</span><span class="sxs-lookup"><span data-stu-id="625ce-201">Get the current changes.</span></span>
    
<span data-ttu-id="625ce-202">Las secciones siguientes describen la vista previa de este servicio web, lo que podría cambiar con el tiempo hasta que el servicio esté disponible para el público.</span><span class="sxs-lookup"><span data-stu-id="625ce-202">The following sections describe the preview of this web service, which might change over time until the service is generally available.</span></span> 
  
<span data-ttu-id="625ce-203">Los datos en el servicio web están actualizados y no va a realizar más cambios en las direcciones URL de servicio de web o devuelve el esquema de los datos antes del lanzamiento de la disponibilidad general de este servicio web.</span><span class="sxs-lookup"><span data-stu-id="625ce-203">The data on the web service is up to date and we are not planning to make further changes to the web service URLs or returned data schema before the general availability release of this web service.</span></span>
  
<span data-ttu-id="625ce-204">Para obtener información adicional, vea:</span><span class="sxs-lookup"><span data-stu-id="625ce-204">For additional information, see:</span></span>
  
- [<span data-ttu-id="625ce-205">Entrada de blog de anuncio en el foro de la Comunidad de Office 365 Tech</span><span class="sxs-lookup"><span data-stu-id="625ce-205">Announcement blog post in the Office 365 Tech Community Forum</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
    
- [<span data-ttu-id="625ce-206">Foro de la Comunidad de Office 365 Tech para preguntas sobre el uso de los servicios web</span><span class="sxs-lookup"><span data-stu-id="625ce-206">Office 365 Tech Community Forum for questions about use of the web services</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)
    
### <a name="common-parameters"></a><span data-ttu-id="625ce-207">Parámetros comunes</span><span class="sxs-lookup"><span data-stu-id="625ce-207">Common parameters</span></span>

<span data-ttu-id="625ce-208">Estos parámetros son comunes a todos los métodos de servicio web:</span><span class="sxs-lookup"><span data-stu-id="625ce-208">These parameters are common across all the web service methods:</span></span>
  
- <span data-ttu-id="625ce-p121">formato de **= CSV | JSON** -parámetro de cadena de consulta. De forma predeterminada, el formato de datos que se devuelven es JSON. Incluir este parámetro opcional para devolver los datos en formato de valores separados por comas (CSV).</span><span class="sxs-lookup"><span data-stu-id="625ce-p121">**format=CSV | JSON** - Query string parameter. By default, the returned data format is JSON. Include this optional parameter to return the data in comma-separated values (CSV) format.</span></span> 
    
- <span data-ttu-id="625ce-p122">**ClientRequestId** - parámetro de cadena de consulta. Un GUID requiere que se genera para la asociación de la sesión de cliente. Debe generar un GUID para cada equipo cliente que llama al servicio web. No use los GUID que se muestra en los ejemplos siguientes, debido a que puedan estar bloqueadas por el servicio web en el futuro. Formato GUID es xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx, donde x representa un número hexadecimal. Para generar un GUID, utilice el comando de PowerShell [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) .</span><span class="sxs-lookup"><span data-stu-id="625ce-p122">**ClientRequestId** - Query string parameter. A required GUID that you generate for client session association. You should generate a GUID for each client machine that calls the web service. Do not use the GUIDs shown in the following examples because they may be blocked by the web service in the future. GUID format is xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx, where x represents a hexadecimal number. To generate a GUID, use the [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell command.</span></span> 
    
### <a name="version-web-method"></a><span data-ttu-id="625ce-218">Método web de la versión</span><span class="sxs-lookup"><span data-stu-id="625ce-218">Version web method</span></span>

<span data-ttu-id="625ce-p123">Microsoft actualiza la dirección IP de Office 365 y las entradas de FQDN al final de cada mes y ocasionalmente fuera de ciclo para operativas o satisfacer los requisitos. Los datos para cada instancia publicado se asignan a un número de versión. El método web de versión permite sondear para la versión más reciente para cada instancia de servicio de Office 365. Se recomienda que comprobar la versión del diario, o como máximo, cada hora.</span><span class="sxs-lookup"><span data-stu-id="625ce-p123">Microsoft updates the Office 365 IP address and FQDN entries at the end of each month and occasionally out of cycle for operational or support requirements. The data for each published instance is assigned a version number. The version web method lets you poll for the latest version for each Office 365 service instance. We recommend you check the version daily, or at the most, hourly.</span></span>
  
<span data-ttu-id="625ce-223">Hay un parámetro para el método web de versión:</span><span class="sxs-lookup"><span data-stu-id="625ce-223">There is one parameter for the version web method:</span></span>
  
- <span data-ttu-id="625ce-p124">**AllVersions = true** -parámetro de cadena de consulta. De forma predeterminada, la versión devuelta es la más reciente. Incluir este parámetro opcional para solicitar que todas las versiones publicadas.</span><span class="sxs-lookup"><span data-stu-id="625ce-p124">**AllVersions=true** - Query string parameter. By default, the version returned is the latest. Include this optional parameter to request all published versions.</span></span> 
    
- <span data-ttu-id="625ce-p125">**Instancia** - el parámetro de ruta. Este parámetro opcional especifica la instancia para devolver la versión para. Si se omite, se devuelven todas las instancias. Sesiones válidos son: en todo el mundo, China, Alemania, USGovDoD, USGovGCCHigh</span><span class="sxs-lookup"><span data-stu-id="625ce-p125">**Instance** - Route parameter. This optional parameter specifies the instance to return the version for. If omitted, all instances are returned. Valid instances are: Worldwide, China, Germany, USGovDoD, USGovGCCHigh</span></span> 
    
<span data-ttu-id="625ce-p126">El resultado del método web de versión puede ser un único registro o una matriz de registros. Los elementos de cada registro son:</span><span class="sxs-lookup"><span data-stu-id="625ce-p126">The result from the version web method may be a single record or an array of records. The elements of each record are:</span></span>
  
- <span data-ttu-id="625ce-233">instancia - el nombre corto de la instancia de servicio de Office 365.</span><span class="sxs-lookup"><span data-stu-id="625ce-233">instance - The short name of the Office 365 service instance.</span></span>
    
- <span data-ttu-id="625ce-234">último - la versión más reciente para los extremos de la instancia especificada.</span><span class="sxs-lookup"><span data-stu-id="625ce-234">latest - The latest version for endpoints of the specified instance.</span></span>
    
- <span data-ttu-id="625ce-p127">versiones - una lista de todas las versiones anteriores para la instancia especificada. Este elemento sólo está incluido, si el parámetro AllVersions es true.</span><span class="sxs-lookup"><span data-stu-id="625ce-p127">versions - A list of all previous versions for the specified instance. This element is only included if the AllVersions parameter is true.</span></span>
   
#### <a name="examples"></a><span data-ttu-id="625ce-237">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="625ce-237">Examples:</span></span>
  
<span data-ttu-id="625ce-238">URI de la solicitud en el ejemplo 1: ** <span>https:</span>//endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span><span class="sxs-lookup"><span data-stu-id="625ce-238">Example 1 request URI: **<span>https:</span>//endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span></span>
  
<span data-ttu-id="625ce-p128">Este URI devuelve la versión más reciente de cada instancia de servicio de Office 365. Resultado de ejemplo:</span><span class="sxs-lookup"><span data-stu-id="625ce-p128">This URI returns the latest version of each Office 365 service instance. Example result:</span></span>
  
```
[
 {
  "instance": "Worldwide", 
  "latest": "2018063000"
 },
 {
  "instance": "USGovDoD", 
  "latest": "2018063000"
 },
 {
  "instance": "USGovGCCHigh",
  "latest": "2018063000"
 },
 {
  "instance": "China",
  "latest": "2018063000"
 },
 {
  "instance": "Germany",
  "latest": "2018063000"
 }
] 
```

> [!IMPORTANT]
> <span data-ttu-id="625ce-p129">El GUID para el parámetro ClientRequestID en estos URI son sólo un ejemplo. Para probar la web de los URI de fuera de servicio, genere su propio GUID. Los GUID que se muestra en estos ejemplos se pueden bloquear por el servicio web en el futuro.</span><span class="sxs-lookup"><span data-stu-id="625ce-p129">The GUID for the ClientRequestID parameter in these URIs are only an example. To try the web service URIs out, generate your own GUID. The GUIDs shown in these examples may be blocked by the web service in the future.</span></span> 
  
<span data-ttu-id="625ce-244">URI de la solicitud en el ejemplo 2: ** <span>https:</span>//endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span><span class="sxs-lookup"><span data-stu-id="625ce-244">Example 2 request URI: **<span>https:</span>//endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span></span>
  
<span data-ttu-id="625ce-p130">Este URI devuelve la última versión de la instancia de servicio especificada de Office 365. Resultado de ejemplo:</span><span class="sxs-lookup"><span data-stu-id="625ce-p130">This URI returns the latest version of the specified Office 365 service instance. Example result:</span></span>
  
```
{
 "instance": "Worldwide",
 "latest": "2018063000"
}
```

<span data-ttu-id="625ce-247">URI de la solicitud de ejemplo 3: ** <span>https:</span>//endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId = b10c5ed1-bad1-445f-b386-b919946339a7**</span><span class="sxs-lookup"><span data-stu-id="625ce-247">Example 3 request URI: **<span>https:</span>//endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span></span>
  
<span data-ttu-id="625ce-p131">Este URI muestra resultados en formato CSV. Resultado de ejemplo:</span><span class="sxs-lookup"><span data-stu-id="625ce-p131">This URI shows output in CSV format. Example result:</span></span>
  
```
instance,latest
Worldwide,2018063000
```

<span data-ttu-id="625ce-250">URI de la solicitud de ejemplo 4: ** <span>https:</span>//endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId = b10c5ed1-bad1-445f-b386-b919946339a7**</span><span class="sxs-lookup"><span data-stu-id="625ce-250">Example 4 request URI: **<span>https:</span>//endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span></span>
  
<span data-ttu-id="625ce-p132">Este URI muestra todas las versiones anteriores que se han publicado para la instancia de servicio en todo el mundo de Office 365. Resultado de ejemplo:</span><span class="sxs-lookup"><span data-stu-id="625ce-p132">This URI shows all prior versions that have been published for the Office 365 worldwide service instance. Example result:</span></span>
  
```
{
  "instance": "Worldwide",
  "latest": "2018063000",
  "versions": [
    "2018063000",
    "2018062000"
  ]
}
```

### <a name="endpoints-web-method"></a><span data-ttu-id="625ce-253">Los extremos de web (método)</span><span class="sxs-lookup"><span data-stu-id="625ce-253">Endpoints web method</span></span>

<span data-ttu-id="625ce-p133">El método web de extremos devuelve todos los registros de intervalos de direcciones IP y direcciones URL que componen el servicio Office 365. Parámetros para el método web de extremos son:</span><span class="sxs-lookup"><span data-stu-id="625ce-p133">The endpoints web method returns all records for IP address ranges and URLs that make up the Office 365 service. Parameters for the endpoints web method are:</span></span>
  
- <span data-ttu-id="625ce-p134">**ServiceAreas** - parámetro de cadena de consulta. Una lista separada por comas de las áreas de servicio. Elementos válidos son común, Exchange, SharePoint, Skype. Debido a que los elementos comunes de área de servicio son un requisito previo para todas las demás áreas de servicio, el servicio web de ellos incluirá siempre. Si no se incluye este parámetro, se devuelven todas las áreas de servicio.</span><span class="sxs-lookup"><span data-stu-id="625ce-p134">**ServiceAreas** - Query string parameter. A comma-separated list of service areas. Valid items are Common,Exchange,SharePoint,Skype. Because Common service area items are a prerequisite for all other service areas, the web service will always include them. If you do not include this parameter, all service areas are returned.</span></span> 
    
- <span data-ttu-id="625ce-p135">**TenantName** - parámetro de cadena de consulta. El nombre del inquilino de Office 365. El servicio web toma el nombre proporcionado y lo inserta en elementos de las direcciones URL que incluyen el nombre del inquilino. Si no proporciona un nombre del inquilino, las partes de las direcciones URL tienen el carácter comodín (\*).</span><span class="sxs-lookup"><span data-stu-id="625ce-p135">**TenantName** - Query string parameter. Your Office 365 tenant name. The web service takes your provided name and inserts it in parts of URLs that include the tenant name. If you don't provide a tenant name, those parts of URLs have the wildcard character (\*).</span></span> 
    
- <span data-ttu-id="625ce-p136">**NoIPv6** - parámetro de cadena de consulta. Establecer en True para las direcciones IPv6 de excluir de los resultados, por ejemplo, si no usa IPv6 en la red.</span><span class="sxs-lookup"><span data-stu-id="625ce-p136">**NoIPv6** - Query string parameter. Set this to true to exclude IPv6 addresses from the output, for example, if you don't use IPv6 in your network.</span></span> 
    
- <span data-ttu-id="625ce-p137">**Instancia** - el parámetro de ruta. Este parámetro obligatorio especifica la instancia para devolver los extremos para. Sesiones válidos son: en todo el mundo, China, Alemania, USGovDoD, USGovGCCHigh.</span><span class="sxs-lookup"><span data-stu-id="625ce-p137">**Instance** - Route parameter. This required parameter specifies the instance to return the endpoints for. Valid instances are: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span></span> 
    
<span data-ttu-id="625ce-p138">El resultado del método web de extremos es una matriz de registros con cada registro que representa un conjunto de extremo. Los elementos de cada registro son:</span><span class="sxs-lookup"><span data-stu-id="625ce-p138">The result from the endpoints web method is an array of records with each record representing an endpoint set. The elements for each record are:</span></span>
  
- <span data-ttu-id="625ce-272">establece en el identificador - el número de identificador inmutable del extremo.</span><span class="sxs-lookup"><span data-stu-id="625ce-272">id - The immutable id number of the endpoint set.</span></span>
    
- <span data-ttu-id="625ce-273">serviceArea - del área de servicio que es parte de: común, Exchange, SharePoint o Skype.</span><span class="sxs-lookup"><span data-stu-id="625ce-273">serviceArea - The service area that this is part of: Common, Exchange, SharePoint, or Skype.</span></span>
    
- <span data-ttu-id="625ce-p139">las direcciones URL - conjunto de direcciones URL para el extremo. Una matriz JSON de registros DNS. Se omite si está en blanco.</span><span class="sxs-lookup"><span data-stu-id="625ce-p139">urls - URLs for the endpoint set. A JSON array of DNS records. Omitted if blank.</span></span>
    
- <span data-ttu-id="625ce-p140">establecer los puertos TCP para el extremo de tcpPorts. Tienen el formato de todos los elementos de puertos como una lista separada por comas de los puertos o intervalos de puertos separados por un carácter de guión (-). Los puertos se aplican a todas las direcciones IP y todas las direcciones URL en que el extremo se establece para esa categoría. Se omite si está en blanco.</span><span class="sxs-lookup"><span data-stu-id="625ce-p140">tcpPorts - TCP ports for the endpoint set. All ports elements are formatted as a comma-separated list of ports or port ranges separated by a dash character (-). Ports apply to all IP addresses and all URLs in that endpoint set for that category. Omitted if blank.</span></span>
    
- <span data-ttu-id="625ce-p141">udpPorts - puertos UDP para la dirección IP intervalos en este conjunto de extremo de direcciones. Se omite si está en blanco.</span><span class="sxs-lookup"><span data-stu-id="625ce-p141">udpPorts - UDP ports for the IP address ranges in this endpoint set. Omitted if blank.</span></span>
    
- <span data-ttu-id="625ce-p142">IP - intervalos de direcciones IP asociados a este extremo que se establezca como asociado con los puertos TCP o UDP mostrados. Se omite si está en blanco.</span><span class="sxs-lookup"><span data-stu-id="625ce-p142">ips - The IP address ranges associated with this endpoint set as associated with the listed TCP or UDP ports. Omitted if blank.</span></span>
    
- <span data-ttu-id="625ce-p143">categoría - establecido de la categoría de conectividad para el extremo. Los valores válidos son optimizar, permitir y predeterminado. Obligatorio.</span><span class="sxs-lookup"><span data-stu-id="625ce-p143">category - The connectivity category for the endpoint set. Valid values are Optimize, Allow, and Default. Required.</span></span>
    
- <span data-ttu-id="625ce-288">expressRoute - True o False si este conjunto de extremo se enruta a través de ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="625ce-288">expressRoute - True or False if this endpoint set is routed over ExpressRoute.</span></span>
    
- <span data-ttu-id="625ce-p144">requerido - True si es necesario tener conectividad para Office 365 sean compatibles con este conjunto de extremo. Se omite si es false.</span><span class="sxs-lookup"><span data-stu-id="625ce-p144">required - True if this endpoint set is required to have connectivity for Office 365 to be supported. Omitted if false.</span></span>
    
- <span data-ttu-id="625ce-p145">notas - para extremos opcionales, este texto describe la funcionalidad de Office 365 no aparecerá si direcciones IP o las direcciones URL en este extremo set no se puede tener acceso en la capa de red. Se omite si está en blanco.</span><span class="sxs-lookup"><span data-stu-id="625ce-p145">notes - For optional endpoints, this text describes Office 365 functionality that will be missing if IP addresses or URLs in this endpoint set cannot be accessed at the network layer. Omitted if blank.</span></span>
    
#### <a name="examples"></a><span data-ttu-id="625ce-293">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="625ce-293">Examples:</span></span>
  
<span data-ttu-id="625ce-294">URI de la solicitud en el ejemplo 1: ** <span>https:</span>//endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span><span class="sxs-lookup"><span data-stu-id="625ce-294">Example 1 request URI: **<span>https:</span>//endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span></span>
  
<span data-ttu-id="625ce-p146">Este URI Obtiene todos los extremos de la instancia de todo el mundo de Office 365 para todas las cargas de trabajo. Resultados de ejemplo que muestra un extracto del resultado:</span><span class="sxs-lookup"><span data-stu-id="625ce-p146">This URI obtains all endpoints for the Office 365 worldwide instance for all workloads. Example result showing an excerpt of the output:</span></span>
  
```
[ 
 { 
  "id": 1, 
  "serviceArea": "Exchange", 
  "serviceAreaDisplayName": "Exchange Online", 
  "urls": 
   [ 
    "*.protection.outlook.com" 
   ], 
  "ips": 
   [ 
    "2a01:111:f403::/48", "23.103.132.0/22", "23.103.136.0/21", "23.103.198.0/23", "23.103.212.0/22", "40.92.0.0/14", "40.107.0.0/17", "40.107.128.0/18", "52.100.0.0/14", "213.199.154.0/24", "213.199.180.128/26", "94.245.120.64/26", "207.46.163.0/24", "65.55.88.0/24", "216.32.180.0/23", "23.103.144.0/20", "65.55.169.0/24", "207.46.100.0/24", "2a01:111:f400:7c00::/54", "157.56.110.0/23", "23.103.200.0/22", "104.47.0.0/17", "2a01:111:f400:fc00::/54", "157.55.234.0/24", "157.56.112.0/24", "52.238.78.88/32" 
   ], 
  "tcpPorts": "443", 
  "expressRoute": true, 
  "category": "Allow" 
 }, 
 { 
  "id": 2, 
  "serviceArea": "Exchange", 
  "serviceAreaDisplayName": "Exchange Online", 
  "urls": 
   [ 
    "*.mail.protection.outlook.com" 
   ],
...
```

<span data-ttu-id="625ce-297">Conjuntos de extremo adicionales no se incluyen en este ejemplo.</span><span class="sxs-lookup"><span data-stu-id="625ce-297">Additional endpoint sets are not included in this example.</span></span>
  
<span data-ttu-id="625ce-298">URI de la solicitud en el ejemplo 2: ** <span>https:</span>//endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId = b10c5ed1-bad1-445f-b386-b919946339a7**</span><span class="sxs-lookup"><span data-stu-id="625ce-298">Example 2 request URI: **<span>https:</span>//endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span></span>
  
<span data-ttu-id="625ce-299">En este ejemplo se obtiene los extremos de la instancia de todo el mundo en Office 365 para Exchange Online y dependencias sólo.</span><span class="sxs-lookup"><span data-stu-id="625ce-299">This example obtains endpoints for the Office 365 Worldwide instance for Exchange Online and dependencies only.</span></span>
  
<span data-ttu-id="625ce-300">El resultado por ejemplo 2 es similar al ejemplo 1, excepto en que los resultados no incluirán extremos para SharePoint Online o de Skype para profesionales en línea.</span><span class="sxs-lookup"><span data-stu-id="625ce-300">The output for example 2 is similar to example 1 except that the results will not include endpoints for SharePoint Online or Skype for Business Online.</span></span>
  
### <a name="changes-web-method"></a><span data-ttu-id="625ce-301">Cambios de web (método)</span><span class="sxs-lookup"><span data-stu-id="625ce-301">Changes web method</span></span>

<span data-ttu-id="625ce-p147">El método web de cambios devuelve las actualizaciones más recientes que se hayan publicado. Esto suele ser cambios del mes anterior a intervalos de direcciones IP y direcciones URL.</span><span class="sxs-lookup"><span data-stu-id="625ce-p147">The changes web method returns the most recent updates that have been published. This is typically the previous month's changes to IP address ranges and URLs.</span></span>
  
> [!NOTE]
> <span data-ttu-id="625ce-304">Datos de la API de cambios es precisos en la vista previa y deben ser usados para el desarrollo y prueba sólo.</span><span class="sxs-lookup"><span data-stu-id="625ce-304">Data from the changes API is accurate in the preview and should be used for development and testing only.</span></span> 
  
<span data-ttu-id="625ce-305">El parámetro para el método web de cambios es:</span><span class="sxs-lookup"><span data-stu-id="625ce-305">The parameter for the changes web method is:</span></span>
  
- <span data-ttu-id="625ce-p148">**Versión** : parámetro de ruta de dirección URL necesarios. La versión que se ha implementado actualmente, y que desea ver los cambios desde esa versión. El formato es YYYYMMDDNN.</span><span class="sxs-lookup"><span data-stu-id="625ce-p148">**Version** - Required URL route parameter. The version that you have currently implemented, and you want to see the changes since that version. The format is YYYYMMDDNN.</span></span> 
    
<span data-ttu-id="625ce-p149">El resultado del método web de cambios es una matriz de registros con cada registro que representa un cambio en una versión específica de los extremos. Los elementos de cada registro son:</span><span class="sxs-lookup"><span data-stu-id="625ce-p149">The result from the changes web method is an array of records with each record representing a change in a specific version of the endpoints. The elements for each record are:</span></span>
  
- <span data-ttu-id="625ce-311">Id: identificador inmutable del registro de cambios.</span><span class="sxs-lookup"><span data-stu-id="625ce-311">id - The immutable id of the change record.</span></span>
    
- <span data-ttu-id="625ce-p150">endpointSetId - el identificador del extremo establece registro que se ha cambiado. Obligatorio.</span><span class="sxs-lookup"><span data-stu-id="625ce-p150">endpointSetId - The ID of the endpoint set record that is changed. Required.</span></span>
    
- <span data-ttu-id="625ce-314">disposición - Esto puede ser de cambiar, agregar o quitar y describe lo que hizo el cambio en el registro del conjunto de extremo.</span><span class="sxs-lookup"><span data-stu-id="625ce-314">disposition - This can be either of change, add, or remove and describes what the change did to the endpoint set record.</span></span>
    
- <span data-ttu-id="625ce-p151">versión: la versión del extremo publicado establece en que se introdujo el cambio. Números de versión son con el formato YYYYMMDDNN, donde NN es un número natural incrementado si hay varias versiones necesarias para ser publicado en un solo día.</span><span class="sxs-lookup"><span data-stu-id="625ce-p151">version - The version of the published endpoint set in which the change was introduced. Version numbers are of the format YYYYMMDDNN, where NN is a natural number incremented if there are multiple versions required to be published on a single day.</span></span>
    
- <span data-ttu-id="625ce-p152">anterior - que establezca una subestructura que se detallan los valores anteriores de los elementos cambiados en el extremo. Esto no se incluirán para conjuntos de extremo recién agregado. Incluye tcpPorts, udpPorts, ExpressRoute, categoría, necesaria, notas.</span><span class="sxs-lookup"><span data-stu-id="625ce-p152">previous - A substructure detailing previous values of changed elements on the endpoint set. This will not be included for newly added endpoint sets. Includes tcpPorts, udpPorts, ExpressRoute, category, required, notes.</span></span>
    
- <span data-ttu-id="625ce-p153">actual - una subestructura que se detallan los valores de los elementos de los cambios en la endpoinset actualizados. Incluye tcpPorts, udpPorts, ExpressRoute, categoría, necesaria, notas.</span><span class="sxs-lookup"><span data-stu-id="625ce-p153">current - A substructure detailing updated values of changes elements on the endpoinset. Includes tcpPorts, udpPorts, ExpressRoute, category, required, notes.</span></span>
    
- <span data-ttu-id="625ce-p154">Add - colecciones de conjunto de una estructura de sub que incluye los elementos que se agregará al extremo. Se omite si no hay ningún adiciones.</span><span class="sxs-lookup"><span data-stu-id="625ce-p154">add - A sub structure detailing items to be added to endpoint set collections. Omitted if there are no additions.</span></span>
    
  - <span data-ttu-id="625ce-324">effectiveDate - define los datos cuando las adiciones será live en el servicio.</span><span class="sxs-lookup"><span data-stu-id="625ce-324">effectiveDate - Defines the data when the additions will be live in the service.</span></span>
    
  - <span data-ttu-id="625ce-325">IP - elementos que se agregarán a la matriz de IP.</span><span class="sxs-lookup"><span data-stu-id="625ce-325">ips - Items to be added to the ips array.</span></span>
    
  - <span data-ttu-id="625ce-326">Elementos de las direcciones URL que se agregará a la matriz de direcciones URL.</span><span class="sxs-lookup"><span data-stu-id="625ce-326">urls- Items to be added to the urls array.</span></span>
    
- <span data-ttu-id="625ce-p155">Remove - que establezca una subestructura que incluye los elementos que desea quitar desde el punto final. Se omite si no hay ningún eliminaciones.</span><span class="sxs-lookup"><span data-stu-id="625ce-p155">remove - A substructure detailing items to be removed from the endpoint set. Omitted if there are no removals.</span></span>
    
  - <span data-ttu-id="625ce-329">IP - elementos que debe quitarse de la matriz de IP.</span><span class="sxs-lookup"><span data-stu-id="625ce-329">ips - Items to be removed from the ips array.</span></span>
    
  - <span data-ttu-id="625ce-330">las direcciones URL de los elementos que debe quitarse de la matriz de direcciones URL.</span><span class="sxs-lookup"><span data-stu-id="625ce-330">urls- Items to be removed from the urls array.</span></span>
    
 <span data-ttu-id="625ce-331">**Ejemplos:**</span><span class="sxs-lookup"><span data-stu-id="625ce-331">**Examples:**</span></span>
  
<span data-ttu-id="625ce-332">URI de la solicitud en el ejemplo 1: ** <span>https:</span>//endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span><span class="sxs-lookup"><span data-stu-id="625ce-332">Example 1 request URI: **<span>https:</span>//endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span></span>
  
<span data-ttu-id="625ce-p156">Esto solicita todos los cambios anteriores a la instancia de servicio en todo el mundo de Office 365. Resultado de ejemplo:</span><span class="sxs-lookup"><span data-stu-id="625ce-p156">This requests all previous changes to the Office 365 worldwide service instance. Example result:</span></span>
  
```
[ 
 { 
  "id": 424, 
  "endpointSetId": 32, 
  "disposition": "Change", 
  "version": "2018062700", 
  "remove": 
   { 
    "urls": 
     [ 
      "*.api.skype.com", "skypegraph.skype.com" 
     ] 
   } 
 }, 
 { 
  "id": 426, 
  "endpointSetId": 31, 
  "disposition": "Change", 
  "version": "2018062700", 
  "add": 
   { 
    "effectiveDate": "20180609", 
    "ips": 
     [ 
      "51.140.203.190/32" 
     ]
   },
  "remove": 
   { 
    "ips": 
     [
...

```

<span data-ttu-id="625ce-335">URI de la solicitud en el ejemplo 2: ** <span>https:</span>//endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span><span class="sxs-lookup"><span data-stu-id="625ce-335">Example 2 request URI: **<span>https:</span>//endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span></span>
  
<span data-ttu-id="625ce-p157">Esto solicita cambios con respecto a la versión especificada a la instancia de Office 365 en todo el mundo. En este caso, la versión especificada es el último. Resultado de ejemplo:</span><span class="sxs-lookup"><span data-stu-id="625ce-p157">This requests changes since the specified version to the Office 365 Worldwide instance. In this case, the version specified is the latest. Example result:</span></span>
  
```
[
  {
    "id":3,
    "endpointSetId":33,
    "changeDescription":"Removing old IP prefixes",
    "disposition":"Change",
    "version":"2018031301",
    "remove":{
      "ips":["65.55.127.0/24","66.119.157.192/26","66.119.158.0/25",
      "111.221.76.128/25","111.221.77.0/26","207.46.5.0/24"]
    }
  },
  {
    "id":4,
    "endpointSetId":45,
    "changeDescription":"Removing old IP prefixes",
    "disposition":"Change",
    "version":"2018031301",
    "remove":{
      "ips":["13.78.93.8/32","40.113.87.220/32","40.114.149.220/32",
      "40.117.100.83/32","40.118.214.164/32","104.208.31.113/32"]
    }
  }
]

```

### <a name="example-powershell-script"></a><span data-ttu-id="625ce-339">Script de PowerShell de ejemplo</span><span class="sxs-lookup"><span data-stu-id="625ce-339">Example PowerShell Script</span></span>

<span data-ttu-id="625ce-p158">Aquí es un script de PowerShell que puede ejecutar para ver si hay acciones que debe tener para los datos actualizados. Este script comprueba el número de versión para los extremos de instancia Office 365 en todo el mundo. Cuando se produce un cambio, descarga los extremos y filtros para los extremos de categoría "Permitir" y "Optimizar". También se utiliza un único ClientRequestId a través de varias llamadas y se guarda la versión más reciente que se encuentra en un archivo temporal. Esta secuencia de comandos se debe llamar una vez cada hora para comprobar si hay una actualización de versión.</span><span class="sxs-lookup"><span data-stu-id="625ce-p158">Here is a PowerShell script that you can run to see if there are actions you need to take for updated data. This script checks the version number for the Office 365 Worldwide instance endpoints. When there is a change, it downloads the endpoints and filters for the "Allow" and "Optimize" category endpoints. It also uses a unique ClientRequestId across multiple calls and saves the latest version found in a temporary file. You should call this script once an hour to check for a version update.</span></span>
  
```
# webservice root URL
$ws = "https://endpoints.office.com"
# path where client ID and latest version number will be stored
$datapath = $Env:TEMP + "\endpoints_clientid_latestversion.txt"
# fetch client ID and version if data file exists; otherwise create new file
if (Test-Path $datapath) {
    $content = Get-Content $datapath
    $clientRequestId = $content[0]
    $lastVersion = $content[1]
}
else {
    $clientRequestId = [GUID]::NewGuid().Guid
    $lastVersion = "0000000000"
    @($clientRequestId, $lastVersion) | Out-File $datapath
}
# call version method to check the latest version, and pull new data if version number is different
$version = Invoke-RestMethod -Uri ($ws + "/version/Worldwide?clientRequestId=" + $clientRequestId)
if ($version.latest -gt $lastVersion) {
    Write-Host "New version of Office 365 worldwide commercial service instance endpoints detected"
    
    # write the new version number to the data file
    @($clientRequestId, $version.latest) | Out-File $datapath
    # invoke endpoints method to get the new data
    $endpointSets = Invoke-RestMethod -Uri ($ws + "/endpoints/Worldwide?clientRequestId=" + $clientRequestId)
    # filter results for Allow and Optimize endpoints, and transform these into custom objects with port and category
    $flatUrls = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $urls = $(if ($endpointSet.urls.Count -gt 0) { $endpointSet.urls } else { @() })
        $urlCustomObjects = @()
        if ($endpointSet.category -in ("Allow", "Optimize")) {
            $urlCustomObjects = $urls | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    url      = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $urlCustomObjects
    }
    $flatIps = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $ips = $(if ($endpointSet.ips.Count -gt 0) { $endpointSet.ips } else { @() })
        # IPv4 strings have dots while IPv6 strings have colons
        $ip4s = $ips | Where-Object { $_ -like '*.*' }
        
        $ipCustomObjects = @()
        if ($endpointSet.category -in ("Allow", "Optimize")) {
            $ipCustomObjects = $ip4s | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    ip = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $ipCustomObjects
    }
    Write-Output "IPv4 Firewall IP Address Ranges"
    ($flatIps.ip | Sort-Object -Unique) -join "," | Out-String
    Write-Output "URLs for Proxy Server"
    ($flatUrls.url | Sort-Object -Unique) -join "," | Out-String
    # TODO Call Send-MailMessage with new endpoints data
}
else {
    Write-Host "Office 365 worldwide commercial service instance endpoints are up-to-date"
}
```

### <a name="example-python-script"></a><span data-ttu-id="625ce-345">Secuencia de comandos de ejemplo Python</span><span class="sxs-lookup"><span data-stu-id="625ce-345">Example Python Script</span></span>

<span data-ttu-id="625ce-p159">Aquí es una secuencia de comandos de Python, probado con Python 3.6.3 en 10 de Windows, que se pueden ejecutar para ver si hay acciones que debe tener para los datos actualizados. Este script comprueba el número de versión para los extremos de instancia Office 365 en todo el mundo. Cuando se produce un cambio, descarga los extremos y filtros para los extremos de categoría "Permitir" y "Optimizar". También se utiliza un único ClientRequestId a través de varias llamadas y se guarda la versión más reciente que se encuentra en un archivo temporal. Esta secuencia de comandos se debe llamar una vez cada hora para comprobar si hay una actualización de versión.</span><span class="sxs-lookup"><span data-stu-id="625ce-p159">Here is a Python script, tested with Python 3.6.3 on Windows 10, that you can run to see if there are actions you need to take for updated data. This script checks the version number for the Office 365 Worldwide instance endpoints. When there is a change, it downloads the endpoints and filters for the "Allow" and "Optimize" category endpoints. It also uses a unique ClientRequestId across multiple calls and saves the latest version found in a temporary file. You should call this script once an hour to check for a version update.</span></span>
  
```
import json
import os
import urllib.request
import uuid
# helper to call the webservice and parse the response
def webApiGet(methodName, instanceName, clientRequestId):
    ws = "https://endpoints.office.com"
    requestPath = ws + '/' + methodName + '/' + instanceName + '?clientRequestId=' + clientRequestId
    request = urllib.request.Request(requestPath)
    with urllib.request.urlopen(request) as response:
        return json.loads(response.read().decode())
# path where client ID and latest version number will be stored
datapath = os.environ['TEMP'] + '\endpoints_clientid_latestversion.txt'
# fetch client ID and version if data exists; otherwise create new file
if os.path.exists(datapath):
    with open(datapath, 'r') as fin:
        clientRequestId = fin.readline().strip()
        latestVersion = fin.readline().strip()
else:
    clientRequestId = str(uuid.uuid4())
    latestVersion = '0000000000'
    with open(datapath, 'w') as fout:
        fout.write(clientRequestId + '\n' + latestVersion)
# call version method to check the latest version, and pull new data if version number is different
version = webApiGet('version', 'Worldwide', clientRequestId)
if version['latest'] > latestVersion:
    print('New version of Office 365 worldwide commercial service instance endpoints detected')
    # write the new version number to the data file
    with open(datapath, 'w') as fout:
        fout.write(clientRequestId + '\n' + version['latest'])
    # invoke endpoints method to get the new data
    endpointSets = webApiGet('endpoints', 'Worldwide', clientRequestId)
    # filter results for Allow and Optimize endpoints, and transform these into tuples with port and category
    flatUrls = []
    for endpointSet in endpointSets:
        if endpointSet['category'] in ('Optimize', 'Allow'):
            category = endpointSet['category']
            urls = endpointSet['urls'] if 'urls' in endpointSet else []
            tcpPorts = endpointSet['tcpPorts'] if 'tcpPorts' in endpointSet else ''
            udpPorts = endpointSet['udpPorts'] if 'udpPorts' in endpointSet else ''
            flatUrls.extend([(category, url, tcpPorts, udpPorts) for url in urls])
    flatIps = []
    for endpointSet in endpointSets:
        if endpointSet['category'] in ('Optimize', 'Allow'):
            ips = endpointSet['ips'] if 'ips' in endpointSet else []
            category = endpointSet['category']
            # IPv4 strings have dots while IPv6 strings have colons
            ip4s = [ip for ip in ips if '.' in ip]
            tcpPorts = endpointSet['tcpPorts'] if 'tcpPorts' in endpointSet else ''
            udpPorts = endpointSet['udpPorts'] if 'udpPorts' in endpointSet else ''
            flatIps.extend([(category, ip, tcpPorts, udpPorts) for ip in ip4s])
    print('IPv4 Firewall IP Address Ranges')
    print(','.join(sorted(set([ip for (category, ip, tcpPorts, udpPorts) in flatIps]))))
    print('URLs for Proxy Server')
    print(','.join(sorted(set([url for (category, url, tcpPorts, udpPorts) in flatUrls]))))
    
    # TODO send mail (e.g. with smtplib/email modules) with new endpoints data
else:
    print('Office 365 worldwide commercial service instance endpoints are up-to-date')
```

### <a name="web-service-interface-versioning"></a><span data-ttu-id="625ce-351">Control de versiones de interfaz de servicio de Web</span><span class="sxs-lookup"><span data-stu-id="625ce-351">Web Service interface versioning</span></span>

<span data-ttu-id="625ce-p160">Las actualizaciones de los parámetros o los resultados de estos métodos de servicio web pueden ser necesarias en el futuro. Después de publica la versión de la disponibilidad general de estos servicios web, Microsoft hará un esfuerzo razonable para proporcionar notificación anticipada de materiales actualizaciones al servicio web. Cuando Microsoft cree que una actualización requerirá cambios en los clientes mediante el servicio web, Microsoft mantendrá la versión anterior (versión inmediatamente anterior) del servicio de web disponible para al menos doce (12) meses después del lanzamiento de la nueva versión. Los clientes que no actualizar durante ese tiempo posible que pueda obtener acceso el servicio web y sus métodos. Los clientes deben asegurarse de que los clientes del servicio web continuarán trabajando sin errores si se realizan los cambios siguientes a la firma de interfaz de servicio web:</span><span class="sxs-lookup"><span data-stu-id="625ce-p160">Updates to the parameters or results for these web service methods may be required in the future. After the general availability version of these web services is published, Microsoft will make reasonable efforts to provide advance notice of material updates to the web service. When Microsoft believes that an update will require changes to clients using the web service, Microsoft will keep the previous version (one version back) of the web service available for at least twelve (12) months after the release of the new version. Customers who do not upgrade during that time may be unable to access the web service and its methods. Customers must ensure that clients of the web service continue working without error if the following changes are made to the web service interface signature:</span></span>
  
- <span data-ttu-id="625ce-357">Adición de un nuevo parámetro opcional a un método web existente que no tiene que ser proporcionado por los clientes más antiguos y no afecta el resultado recibe un cliente más antiguos.</span><span class="sxs-lookup"><span data-stu-id="625ce-357">Adding a new optional parameter to an existing web method that doesn't have to be provided by older clients and doesn't impact the result an older client receives.</span></span>
    
- <span data-ttu-id="625ce-358">Adición de un nuevo atributo con nombre de uno de los elementos del resto de respuesta o columnas adicionales a la respuesta CSV.</span><span class="sxs-lookup"><span data-stu-id="625ce-358">Adding a new named attribute in one of the response REST items or additional columns to the response CSV.</span></span>
    
- <span data-ttu-id="625ce-359">Adición de un nuevo método web con un nombre nuevo que no se llama a los clientes más antiguos.</span><span class="sxs-lookup"><span data-stu-id="625ce-359">Adding a new web method with a new name that is not called by the older clients.</span></span>
    
## <a name="faq"></a><span data-ttu-id="625ce-360">Preguntas más frecuentes</span><span class="sxs-lookup"><span data-stu-id="625ce-360">FAQ</span></span>

<span data-ttu-id="625ce-361">Preguntas más frecuentes con frecuencia administrador sobre la conectividad de:</span><span class="sxs-lookup"><span data-stu-id="625ce-361">Frequently-asked administrator questions about connectivity:</span></span>
  
### <a name="how-do-i-submit-a-question"></a><span data-ttu-id="625ce-362">¿Cómo se puede enviar una pregunta?</span><span class="sxs-lookup"><span data-stu-id="625ce-362">How do I submit a question?</span></span>

<span data-ttu-id="625ce-p161">Haga clic en el vínculo en la parte inferior para indicar si el artículo ha sido útil y enviar preguntas adicionales. Se supervisión los comentarios y actualización las preguntas aquí con las preguntas más frecuentes.</span><span class="sxs-lookup"><span data-stu-id="625ce-p161">Click the link at the bottom to indicate if the article was helpful or not and submit any additional questions. We monitor the feedback and update the questions here with the most frequently asked.</span></span>
  
### <a name="when-is-the-xml-file-updated"></a><span data-ttu-id="625ce-365">¿Cuando se actualice el archivo XML?</span><span class="sxs-lookup"><span data-stu-id="625ce-365">When is the XML file updated?</span></span>

<span data-ttu-id="625ce-p162">Cuando se anuncian nuevos extremos, suele haber un búfer de más de 30 días antes de que sean efectivas y de las solicitudes de red dirigirán a ellos. Este búfer es garantizar a que los clientes y los socios tienen una oportunidad para actualizar sus sistemas. IP y FQDN prefijo adiciones y eliminaciones se procesan en el archivo XML al mismo tiempo como el anuncio, lo que significa que un FQDN nuevo estará en el archivo XML de 30 días antes de su uso. Dado que se deje de enviar las solicitudes de red a los extremos que nos estamos quitar antes de anunciar su eliminación, cuando se quita el extremo de la XML al mismo tiempo como el anuncio ya está no usado.</span><span class="sxs-lookup"><span data-stu-id="625ce-p162">When new endpoints are announced, there is usually a 30+ day buffer before they are effective and network requests begin going to them. This buffer is to ensure customers and partners have an opportunity to update their systems. FQDN and IP prefix additions and removals are processed in the XML file at the same time as the announcement, meaning a new FQDN will be in the XML file 30 days before use. Since we stop sending network requests to endpoints we're removing prior to announcing their removal, when we remove the endpoint from the XML at the same time as the announcement it is already unused.</span></span>
  
### <a name="how-can-i-be-notified-of-changes"></a><span data-ttu-id="625ce-370">¿Cómo puedo ¿se recibe una notificación de cambios?</span><span class="sxs-lookup"><span data-stu-id="625ce-370">How can I be notified of changes?</span></span>
<span data-ttu-id="625ce-371"><a name="bkmk_changes"> </a></span><span class="sxs-lookup"><span data-stu-id="625ce-371"></span></span>

<span data-ttu-id="625ce-p163">Los extremos de Office 365 se publican al final de cada mes con el aviso de 30 días. En ocasiones, los cambios se producirán más de una vez un mes o con períodos más cortos de aviso. Cuando se agrega un extremo, la fecha efectiva que aparecen en la [fuente RSS](https://go.microsoft.com/fwlink/p/?linkid=236301) es la fecha después de que se van a enviar las solicitudes de red para el extremo. Si está familiarizado con RSS, aquí es cómo [suscribirse a través de Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) o puede [tener la actualizaciones de correo electrónico de fuente RSS](https://go.microsoft.com/fwlink/p/?LinkId=532417).</span><span class="sxs-lookup"><span data-stu-id="625ce-p163">Office 365 endpoints are published at the end of each month with 30 days notice. Occasionally changes will occur more than once a month or with shorter notice periods. When an endpoint is added, the effective date listed in the [RSS feed](https://go.microsoft.com/fwlink/p/?linkid=236301) is the date after which network requests will be sent to the endpoint. If you're new to RSS, here is how to [subscribe via Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) or you can [have the RSS feed updates emailed to you](https://go.microsoft.com/fwlink/p/?LinkId=532417).</span></span>
  
### <a name="how-do-i-read-the-rss-change-log"></a><span data-ttu-id="625ce-376">¿Cómo se puede leer que el RSS cambiar registro?</span><span class="sxs-lookup"><span data-stu-id="625ce-376">How do I read the RSS change log?</span></span>
<span data-ttu-id="625ce-377"><a name="bkmk_changes"> </a></span><span class="sxs-lookup"><span data-stu-id="625ce-377"></span></span>

<span data-ttu-id="625ce-p164">Después de suscribirse a la fuente RSS, puede analizar la información usted mismo o con una secuencia de comandos. En la siguiente tabla se describe el formato de RSS de la fuente o facilitar la tarea.</span><span class="sxs-lookup"><span data-stu-id="625ce-p164">After you subscribe to the RSS feed, you can parse the information yourself or with a script. The following table describes the format of the RSS feed o make it easier.</span></span>
  
|<span data-ttu-id="625ce-380">**Sección**</span><span class="sxs-lookup"><span data-stu-id="625ce-380">**Section**</span></span>|<span data-ttu-id="625ce-381">**Parte 1**</span><span class="sxs-lookup"><span data-stu-id="625ce-381">**Part 1**</span></span>|<span data-ttu-id="625ce-382">**Parte 2**</span><span class="sxs-lookup"><span data-stu-id="625ce-382">**Part 2**</span></span>|<span data-ttu-id="625ce-383">**Parte 3**</span><span class="sxs-lookup"><span data-stu-id="625ce-383">**Part 3**</span></span>|<span data-ttu-id="625ce-384">**Parte 4**</span><span class="sxs-lookup"><span data-stu-id="625ce-384">**Part 4**</span></span>|<span data-ttu-id="625ce-385">**Parte 5**</span><span class="sxs-lookup"><span data-stu-id="625ce-385">**Part 5**</span></span>|<span data-ttu-id="625ce-386">**Parte 6**</span><span class="sxs-lookup"><span data-stu-id="625ce-386">**Part 6**</span></span>|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="625ce-387">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="625ce-387">**Description**</span></span> <br/> |<span data-ttu-id="625ce-388">Contador</span><span class="sxs-lookup"><span data-stu-id="625ce-388">Count</span></span>  <br/> |<span data-ttu-id="625ce-389">Fecha después de que puede esperar que se envíen al extremo de las solicitudes de red.</span><span class="sxs-lookup"><span data-stu-id="625ce-389">Date after which you can expect network requests to be sent to the endpoint.</span></span>  <br/> |<span data-ttu-id="625ce-390">Descripción básica de la característica o servicio que requiere el extremo.</span><span class="sxs-lookup"><span data-stu-id="625ce-390">Basic description of the feature or service that requires the endpoint.</span></span>  <br/> |<span data-ttu-id="625ce-391">¿Puede conectarse a este extremo en un circuito ExpressRoute además de internet?</span><span class="sxs-lookup"><span data-stu-id="625ce-391">Can you connect to this endpoint on an ExpressRoute Circuit in addition to the internet?</span></span>  <br/> |<span data-ttu-id="625ce-392">**Sí** - puede conectarse a este extremo en internet y ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="625ce-392">**Yes** - you can connect to this endpoint on both the internet and ExpressRoute.</span></span>  <br/> <span data-ttu-id="625ce-393">**No** : sólo se puede conectar a este extremo en internet.</span><span class="sxs-lookup"><span data-stu-id="625ce-393">**No** - you can only connect to this endpoint on the internet.</span></span>  <br/> |<span data-ttu-id="625ce-394">El intervalo IP o FQDN que se agregan o quitan de destino.</span><span class="sxs-lookup"><span data-stu-id="625ce-394">The destination FQDN or IP range being added or removed.</span></span>  <br/> |
|<span data-ttu-id="625ce-395">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="625ce-395">**Example**</span></span> <br/> |<span data-ttu-id="625ce-396">1 /</span><span class="sxs-lookup"><span data-stu-id="625ce-396">1/</span></span>  <br/> |<span data-ttu-id="625ce-397">[Eficaz xx/xx/xxx.</span><span class="sxs-lookup"><span data-stu-id="625ce-397">[Effective xx/xx/xxx.</span></span>  <br/> |<span data-ttu-id="625ce-398">Obligatorio: \<descripción\>.</span><span class="sxs-lookup"><span data-stu-id="625ce-398">Required: \<description\>.</span></span>  <br/> |<span data-ttu-id="625ce-399">ExpressRoute:</span><span class="sxs-lookup"><span data-stu-id="625ce-399">ExpressRoute:</span></span>  <br/> |<span data-ttu-id="625ce-400">\<Sí/No\>.</span><span class="sxs-lookup"><span data-stu-id="625ce-400">\<Yes/No\>.</span></span>  <br/> |<span data-ttu-id="625ce-401">\<FQDN/IP\>],</span><span class="sxs-lookup"><span data-stu-id="625ce-401">\<FQDN/IP\>],</span></span>  <br/> |
   
<span data-ttu-id="625ce-402">Un par otros aspectos a tener en cuenta, cada entrada tiene un conjunto común de los delimitadores:</span><span class="sxs-lookup"><span data-stu-id="625ce-402">A couple other things to note, every entry has a common set of delimiters:</span></span>
  
- <span data-ttu-id="625ce-403">**/**-Después de la cuenta</span><span class="sxs-lookup"><span data-stu-id="625ce-403">**/** - after the count</span></span> 
    
- <span data-ttu-id="625ce-404">**[** - para indicar la entrada para el recuento</span><span class="sxs-lookup"><span data-stu-id="625ce-404">**[** - to indicate the entry for the count</span></span> 
    
- <span data-ttu-id="625ce-p165">**.** -usar entre cada sección distinta de la entrada</span><span class="sxs-lookup"><span data-stu-id="625ce-p165">**.** - used in between each distinct section of the entry</span></span> 
    
- <span data-ttu-id="625ce-407">**],** - para indicar el final de una única entrada</span><span class="sxs-lookup"><span data-stu-id="625ce-407">**],** - to indicate the end of a single entry</span></span> 
    
- <span data-ttu-id="625ce-p166">**].** -Para indicar el final de todas las entradas</span><span class="sxs-lookup"><span data-stu-id="625ce-p166">**].** - To indicate the end of all the entries</span></span> 
    
### <a name="how-do-i-determine-the-location-of-my-tenant"></a><span data-ttu-id="625ce-410">¿Cómo se puede determinar la ubicación de mi inquilino?</span><span class="sxs-lookup"><span data-stu-id="625ce-410">How do I determine the location of my tenant?</span></span>

 <span data-ttu-id="625ce-411">**Ubicación del inquilino** se determina mejor con nuestro [Centro de datos se asignan](https://o365datacentermap.azurewebsites.net/).</span><span class="sxs-lookup"><span data-stu-id="625ce-411">**Tenant location** is best determined using our [datacenter map](https://o365datacentermap.azurewebsites.net/).</span></span>
  
### <a name="am-i-peering-appropriately-with-microsoft"></a><span data-ttu-id="625ce-412">¿Estoy interconexión adecuadamente con Microsoft?</span><span class="sxs-lookup"><span data-stu-id="625ce-412">Am I peering appropriately with Microsoft?</span></span>

 <span data-ttu-id="625ce-413">**Ubicaciones de Peering** se describen con más detalle en [interconexión con Microsoft](https://www.microsoft.com/peering).</span><span class="sxs-lookup"><span data-stu-id="625ce-413">**Peering locations** are described in more detail in [peering with Microsoft](https://www.microsoft.com/peering).</span></span>
  
<span data-ttu-id="625ce-p167">Con relaciones de interconexión ISP más 2500 globalmente y 70 puntos de presencia, introducción desde la red a nuestro debería ser transparente. No se puede dañar a dedicar unos minutos, asegurándose de que relación de interconexión de su ISP es el más óptima, [le presentamos algunos ejemplos](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__) de buena y no tan buena interconexión no intervención a nuestra red.</span><span class="sxs-lookup"><span data-stu-id="625ce-p167">With over 2500 ISP peering relationships globally and 70 points of presence, getting from your network to ours should be seamless. It can't hurt to spend a few minutes making sure your ISP's peering relationship is the most optimal, [here's a few examples](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__) of good and not so good peering hand-offs to our network.</span></span> 
  
### <a name="how-do-i-determine-which-ip-addresses-to-accept-over-expressroute"></a><span data-ttu-id="625ce-416">Cómo determinar qué direcciones IP para aceptar a través de ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="625ce-416">How do I determine which IP addresses to accept over ExpressRoute?</span></span>

 <span data-ttu-id="625ce-417">**ExpressRoute aceptan rutas** se definen mediante [intervalos IP de Microsoft](https://www.microsoft.com/download/details.aspx?id=53602) y las específicas de Office 365 [Comunidades BGP](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099).</span><span class="sxs-lookup"><span data-stu-id="625ce-417">**Accepted ExpressRoute routes** are defined by [Microsoft's IP ranges](https://www.microsoft.com/download/details.aspx?id=53602) and the specific Office 365 [BGP communities](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099).</span></span>
  
### <a name="how-do-i-determine-which-endpoints-i-need"></a><span data-ttu-id="625ce-418">¿Cómo se puede determinar qué extremos necesito?</span><span class="sxs-lookup"><span data-stu-id="625ce-418">How do I determine which endpoints I need?</span></span>

<span data-ttu-id="625ce-p168">Con regularidad agregamos nuevas características y servicios para el conjunto de aplicaciones de Office 365, expandir el panorama de la conectividad. Si se está suscrito a la E3 o E5 SKU, piense en la lista de extremos de la forma simple es que necesita todos ellos para obtener la funcionalidad completa para el conjunto de aplicaciones. Si no está suscrito a cualquiera de estos SKU la diferencia es mínima en cuanto al número de extremos.</span><span class="sxs-lookup"><span data-stu-id="625ce-p168">We regularly add new features and services to the Office 365 suite, expanding the connectivity landscape. If you're subscribed to the E3 or E5 SKU, the simple way to think about the list of endpoints is that you need all of them to get full functionality for the suite. If you aren't subscribed to either of these SKUs the difference is minimal in terms of the number of endpoints.</span></span>
  
<span data-ttu-id="625ce-422">Lea los [Principios de conectividad de red de Office 365](office-365-network-connectivity-principles.md) para obtener más información sobre las categorías de extremo de Office 365 y para comprender los principios de conectividad para administrar el tráfico de Office 365 y obtener el mejor rendimiento posible de forma segura.</span><span class="sxs-lookup"><span data-stu-id="625ce-422">Read [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md) to get more information on Office 365 endpoint categories, and to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance.</span></span> 
  
<span data-ttu-id="625ce-p169">En la imagen que aparece a continuación, puede ver un ejemplo de una parte de la tabla FQDN en la sección Office Online. Las filas se organizan por característica y las diferencias en la conectividad. Las dos primeras filas indican Office Online se basa en los extremos de marcado necesarios en el portal e identidad y autenticación de Office 365 y secciones compartidas. Esto es típico para un servicio incluido en Office 365 a se basan en estos servicios compartidos. La tercera fila indica los equipos cliente deben ser capaz de ponerse en contacto con \*. officeapps.live.com para usar Office Online y la cuarta fila indica los equipos también deben ser capaz de ponerse en contacto con \*. cdn.office.net a usar Office Online.</span><span class="sxs-lookup"><span data-stu-id="625ce-p169">In the image below, you can see an example from a portion of the FQDN table in the Office Online section. The rows are organized by feature and differences in connectivity. The first two rows indicate Office Online relies on the endpoints marked Required in the Office 365 Authentication and Identity and portal and shared sections. This is typical for a service within Office 365 to rely on these shared services. The third row indicates client computers must be able to reach \*.officeapps.live.com to use Office Online and the fourth row indicates computers must also be able to reach \*.cdn.office.net to use Office Online.</span></span>
  
<span data-ttu-id="625ce-428">Aunque ambos fila tres y cuatro son necesarios para usar Office Online, ha ha separado para indicar que el destino es diferente:</span><span class="sxs-lookup"><span data-stu-id="625ce-428">Even though both row three and four are required to use Office Online, they've been separated to indicate the destination is different:</span></span>
  
1. <span data-ttu-id="625ce-429">\*. officeapps.live.com no representan una CDN, solicitudes de significado a este espacio de nombres irán directamente a un centro de datos de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="625ce-429">\*.officeapps.live.com does not represent a CDN, meaning requests to this namespace will go directly to a Microsoft datacenter.</span></span>
    
2. <span data-ttu-id="625ce-430">\*. officeapps.live.com es accesible en circuitos ExpressRoute con Microsoft Peering.</span><span class="sxs-lookup"><span data-stu-id="625ce-430">\*.officeapps.live.com is accessible on ExpressRoute circuits using Microsoft Peering.</span></span>
    
3. <span data-ttu-id="625ce-431">Las direcciones IP asociadas con Office Online y \*. officeapps.live.com puede encontrarse siguiendo este vínculo.</span><span class="sxs-lookup"><span data-stu-id="625ce-431">The IP addresses associated with Office Online and \*.officeapps.live.com can be found by following this link.</span></span>
    
4. <span data-ttu-id="625ce-432">\*. cdn.office.net representa una CDN hospedada por Akamai, solicitudes de significado a este espacio de nombres se vayan a un centro de datos Akamai.</span><span class="sxs-lookup"><span data-stu-id="625ce-432">\*.cdn.office.net represents a CDN hosted by Akamai, meaning requests to this namespace will go to an Akamai datacenter.</span></span>
    
5. <span data-ttu-id="625ce-433">\*. cdn.office.net no es accesible en circuitos ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="625ce-433">\*.cdn.office.net is not accessible on ExpressRoute circuits.</span></span>
    
6. <span data-ttu-id="625ce-434">Las direcciones IP asociadas con Office Online y \*. cdn.office.net no están disponibles.</span><span class="sxs-lookup"><span data-stu-id="625ce-434">The IP addresses associated with Office Online and \*.cdn.office.net are not available.</span></span>
    
![Captura de pantalla de página extremos](media/42b487f3-24f3-48fe-9885-f97aae3194f3.png)
  
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a><span data-ttu-id="625ce-436">¿Ver las solicitudes de red a direcciones IP no en la lista publicada, necesito para proporcionar acceso a ellos?</span><span class="sxs-lookup"><span data-stu-id="625ce-436">I see network requests to IP addresses not on the published list, do I need to provide access to them?</span></span>
<span data-ttu-id="625ce-437"><a name="bkmk_MissingIP"> </a></span><span class="sxs-lookup"><span data-stu-id="625ce-437"></span></span>

<span data-ttu-id="625ce-p170">Sólo proporcionamos direcciones IP para los servidores de Office 365 que se debe enrutar directamente a través de Internet o ExpressRoute. Esto no es una lista completa de todas las direcciones IP, verá las peticiones de red. Verá las solicitudes de red de Microsoft y de terceros propietario, cancelar la publicación, las direcciones IP. Estas direcciones IP se generado dinámicamente o se administra de forma que impide que oportuna aviso cuando cambian. Si el servidor de seguridad no puede permitir el acceso basado en el FQDN para estas solicitudes de red, use un archivo PAC o WPAD para administrar las solicitudes.</span><span class="sxs-lookup"><span data-stu-id="625ce-p170">We only provide IP addresses for the Office 365 servers you should route directly to over the Internet or ExpressRoute. This isn't a comprehensive list of all IP addresses you'll see network requests for. You'll see network requests to Microsoft and third-party owned, unpublished, IP addresses. These IP addresses are dynamically generated or managed in a way that prevents timely notice when they change. If your firewall can't allow access based on the FQDNs for these network requests, use a PAC or WPAD file to manage the requests.</span></span>
  
<span data-ttu-id="625ce-443">¿Vea que una dirección IP asociada con la que desea obtener más información sobre Office 365?</span><span class="sxs-lookup"><span data-stu-id="625ce-443">See an IP associated with Office 365 that you want more information on?</span></span>
  
1. <span data-ttu-id="625ce-444">Compruebe si la dirección IP que se incluye en un rango publicado mayor que con una [Calculadora de CIDR](http://jodies.de/ipcalc).</span><span class="sxs-lookup"><span data-stu-id="625ce-444">Check if the IP address is included in a larger published range using a [CIDR calculator](http://jodies.de/ipcalc).</span></span>
    
2. <span data-ttu-id="625ce-p171">Vea si un socio propietario de la dirección IP con una [consulta whois](https://dnsquery.org/). Si es que son propiedad de Microsoft, puede ser un socio interno.</span><span class="sxs-lookup"><span data-stu-id="625ce-p171">See if a partner owns the IP with a [whois query](https://dnsquery.org/). If it's Microsoft owned, it may be an internal partner.</span></span>
    
3. <span data-ttu-id="625ce-p172">Comprobar el certificado, en un explorador se conectan a la dirección IP utilizando *HTTPS://\<dirección IP\> * , compruebe los dominios que aparecen en el certificado para comprender qué dominios están asociados con la dirección IP. Si es una propiedad de dirección IP de Microsoft y no en la lista de direcciones IP de Office 365, es probable que es la dirección IP está asociado con una CDN de Microsoft, como *MSOCDN.NET* o de otro dominio de Microsoft sin información publicada de IP. Si encuentra que el dominio en el certificado es donde se notificación para obtener una lista de la dirección IP, háganoslo saber.</span><span class="sxs-lookup"><span data-stu-id="625ce-p172">Check the certificate, in a browser connect to the IP address using  *HTTPS://\<IP_ADDRESS\>*  , check the domains listed on the certificate to understand what domains are associated with the IP address. If it's a Microsoft owned IP address and not on the list of Office 365 IP addresses, it's likely the IP address is associated with a Microsoft CDN such as  *MSOCDN.NET*  or another Microsoft domain without published IP information. If you do find the domain on the certificate is one where we claim to list the IP address, please let us know.</span></span> 
    
### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a><span data-ttu-id="625ce-450">¿Por qué se pueden ver los nombres como nsatc.net o akadns.net en los nombres de dominio de Microsoft?</span><span class="sxs-lookup"><span data-stu-id="625ce-450">Why do I see names such as nsatc.net or akadns.net in the Microsoft domain names?</span></span>
<span data-ttu-id="625ce-451"><a name="bkmk_akamai"> </a></span><span class="sxs-lookup"><span data-stu-id="625ce-451"></span></span>

<span data-ttu-id="625ce-p173">Office 365 y otros servicios de Microsoft usan varios servicios de terceros, como Akamai y MarkMonitor para mejorar la experiencia de Office 365. Para mantener proporcionar la mejor experiencia posible, podemos cambiar estos servicios en el futuro. De esta forma, a menudo se publique el registro CNAME que señala a un tercero dominio propietario, un registro o la dirección IP. Dominios de otros fabricantes pueden hospedar contenido, como una CDN, o pueden hospedar un servicio, como un servicio de administración de tráfico geográfica. Cuando vea las conexiones a estos terceros, estén en el formulario de un redireccionamiento o referencia, no una solicitud inicial desde el cliente. Algunos clientes necesitan para garantizar este formulario de referencia y se permite la redirección para pasar sin agregar explícitamente que la larga lista de servicios de terceros de posibles nombres de dominio completos se puede usar.</span><span class="sxs-lookup"><span data-stu-id="625ce-p173">Office 365 and other Microsoft services use several third-party services such as Akamai and MarkMonitor to improve your Office 365 experience. To keep giving you the best experience possible, we may change these services in the future. In doing so, we often publish the CNAME record which points to a third party owned domain, A record, or IP address. Third party domains may host content, such as a CDN, or they may host a service, such as a geographical traffic management service. When you see connections to these third parties, they're in the form of a redirect or referral, not an initial request from the client. Some customers need to ensure this form of referral and redirection is allowed to pass without explicitly adding the long list of potential FQDNs third party services may use.</span></span>
  
<span data-ttu-id="625ce-p174">La lista de servicios está sujeta a cambios en cualquier momento. Algunos de los servicios que están en uso son:</span><span class="sxs-lookup"><span data-stu-id="625ce-p174">The list of services is subject to change at any time. Some of the services currently in use include:</span></span>
  
<span data-ttu-id="625ce-p175">[MarkMonitor](https://www.markmonitor.com/) está en uso cuando se ven las solicitudes que incluyan \* \*. nsatc.net\* . Este servicio proporciona protección de nombre de dominio y supervisión para proteger el comportamiento malintencionado.</span><span class="sxs-lookup"><span data-stu-id="625ce-p175">[MarkMonitor](https://www.markmonitor.com/) is in use when you see requests that include  *\*.nsatc.net*  . This service provides domain name protection and monitoring to protect against malicious behavior.</span></span> 
  
<span data-ttu-id="625ce-p176">[ExactTarget](https://www.marketingcloud.com/) está en uso cuando se ven las solicitudes a \* \*. exacttarget.com\* . Este servicio proporciona administración de vínculos de correo electrónico y supervisión contra un comportamiento malintencionado.</span><span class="sxs-lookup"><span data-stu-id="625ce-p176">[ExactTarget](https://www.marketingcloud.com/) is in use when you see requests to  *\*.exacttarget.com*  . This service provides email link management and monitoring against malicious behavior.</span></span> 
  
<span data-ttu-id="625ce-p177">[Akamai](https://www.akamai.com/) está en uso cuando se ven las solicitudes que incluyan uno de los siguientes FQDN. Este servicio ofrece ubican DNS y servicios de red de entrega de contenido.</span><span class="sxs-lookup"><span data-stu-id="625ce-p177">[Akamai](https://www.akamai.com/) is in use when you see requests that include one of the following FQDNs. This service offers geo-DNS and content delivery network services.</span></span> 
  
```
*.akadns.net
*.akam.net
*.akamai.com
*.akamai.net
*.akamaiedge.net
*.akamaihd.net
*.akamaized.net
*.edgekey.net
*.edgesuite.net

```

### <a name="what-are-the-three-types-of-office-365-endpoints"></a><span data-ttu-id="625ce-466">¿Cuáles son los tres tipos de extremos de Office 365?</span><span class="sxs-lookup"><span data-stu-id="625ce-466">What are the three types of Office 365 endpoints?</span></span>
<span data-ttu-id="625ce-467"><a name="bkmk_akamai"> </a></span><span class="sxs-lookup"><span data-stu-id="625ce-467"></span></span>

- <span data-ttu-id="625ce-p178">Conectarse a los servicios de terceros para recuperar los servicios de internet básicos, como consultas DNS y recuperación de contenido CDN. También se conecta a los servicios de terceros para aplicaciones integradas tales como la incorporación de vídeos de YouTube en los blocs de notas de OneNote.</span><span class="sxs-lookup"><span data-stu-id="625ce-p178">You connect to third-party services to retrieve basic internet services such as DNS lookups and CDN content retrieval. You also connect to third-party services for integrations such as incorporating YouTube videos in your OneNote notebooks.</span></span>
    
- <span data-ttu-id="625ce-p179">Conectarse a servicios secundarios hospedado y ejecute por Microsoft como nodos perimetrales que permiten la solicitud de red que escriba red global de Microsoft en la ubicación de internet más cercana a su equipo. Como la red mayor en tercer lugar en el planeta, esto mejora la experiencia de conectividad. También se conecta a los servicios de Microsoft Azure, como servicios de multimedia de Azure que se usan por una variedad de servicios de Office 365.</span><span class="sxs-lookup"><span data-stu-id="625ce-p179">You connect to secondary services hosted and run by Microsoft such as edge nodes that enable your network request to enter Microsoft's global network at the closest internet location to your computer. As the third largest network on the planet, this improves your connectivity experience. You also connect to Microsoft Azure services such as Azure Media Services which are used by a variety of Office 365 services.</span></span>
    
- <span data-ttu-id="625ce-p180">Se conecta a servicios de Office 365 principales como el servidor de buzones de Exchange Online o el Skype para servidor empresarial en línea donde se encuentran los datos únicos y propietarios. Puede conectarse a los servicios de Office 365 principales por el FQDN o la dirección IP y utilizar internet o circuitos ExpressRoute. Sólo se puede conectar a los servicios secundarios con nombres de dominio completos en un circuito de internet y el tercero.</span><span class="sxs-lookup"><span data-stu-id="625ce-p180">You connect to primary Office 365 services such as the Exchange Online mailbox server or the Skype for Business Online server where your unique and proprietary data lives. You can connect to the primary Office 365 services by FQDN or IP address and use internet or ExpressRoute circuits. You can only connect to the third party and secondary services using FQDNs on an internet circuit.</span></span>
    
<span data-ttu-id="625ce-p181">En el siguiente diagrama se muestra las diferencias entre estas áreas de servicio. En este diagrama, la red local del cliente en la parte inferior izquierda tiene varios dispositivos de red para ayudarle a administrar la conectividad de red. Las configuraciones como ésta son comunes para los clientes de empresa. Si la red sólo tiene un firewall entre los equipos cliente e internet, que también es compatible, y desea asegurarse de que el servidor de seguridad puede admitir nombres de dominio completos y caracteres comodín en las reglas de la lista Permitir.</span><span class="sxs-lookup"><span data-stu-id="625ce-p181">The following diagram shows the differences between these service areas. In this diagram, the customer on-premises network in the lower left has multiple network devices to assist in managing network connectivity. Configurations like this one are common for enterprise customers. If your network only has a firewall between your client computers and the internet, that's supported as well, and you'll want to ensure your firewall can support FQDNs and wildcards in the allow list rules.</span></span>
  
<span data-ttu-id="625ce-480">Lea los [Principios de conectividad de red de Office 365](office-365-network-connectivity-principles.md) para obtener más información sobre las categorías de extremo de Office 365 y para comprender los principios de conectividad para administrar el tráfico de Office 365 y obtener el mejor rendimiento posible de forma segura.</span><span class="sxs-lookup"><span data-stu-id="625ce-480">Read [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md) to get more information on Office 365 endpoint categories, and to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance.</span></span> 
  
![Muestra los tres tipos diferentes de los extremos de la red cuando se usa Office 365](media/6582bcfa-11ba-4ac2-9b69-14bef0437670.png)
  
### <a name="i-cant-or-dont-want-to-use-any-third-party-service"></a><span data-ttu-id="625ce-482">I no se puede o no desea utilizar cualquier servicio de otro fabricante</span><span class="sxs-lookup"><span data-stu-id="625ce-482">I can't or don't want to use any third-party service</span></span>
<span data-ttu-id="625ce-483"><a name="bkmk_thirdparty"> </a></span><span class="sxs-lookup"><span data-stu-id="625ce-483"></span></span>

<span data-ttu-id="625ce-p182">Office 365 es un conjunto de servicios integrados a función a través de internet, la confiabilidad y la disponibilidad promesas se basan en muchos servicios de internet estándar que están disponibles. Por ejemplo, servicios de internet estándar, como DNS, CRL y las CDN deben ser accesibles para usar Office 365, al igual que deben ser accesibles para usar los servicios de internet más modernos.</span><span class="sxs-lookup"><span data-stu-id="625ce-p182">Office 365 is a suite of services built to function over the internet, the reliability and availability promises are based on many standard internet services being available. For example, standard internet services such as DNS, CRL, and CDNs must be reachable to use Office 365 just as they must be reachable to use most modern internet services.</span></span>
  
<span data-ttu-id="625ce-p183">Además de estos servicios básicos de internet, existen servicios de terceros que sólo se usan para integrar la funcionalidad. Por ejemplo, uso de Giphy.com dentro de Microsoft Teams permite a los clientes sin ningún problema incluyen archivos GIF dentro de los equipos. De forma similar, YouTube y Flickr son los servicios de terceros que se usan para integrar sin problemas vídeos e imágenes en los clientes de Office desde internet. Mientras que son necesarios para la integración, que se han marcado como opcional en el artículo de los extremos de Office 365 lo que significa que la funcionalidad principal del servicio seguirán funcionando si el extremo no es accesible.</span><span class="sxs-lookup"><span data-stu-id="625ce-p183">In addition to these basic internet services, there are third-party services that are only used to integrate functionality. For example, using Giphy.com within Microsoft Teams allows customers to seamlessly include Gifs within Teams. Similarly, YouTube and Flickr are third-party services that are used to seamlessly integrate video and images into Office clients from the internet. While these are needed for integration, they're marked as optional in the Office 365 endpoints article which means core functionality of the service will continue to function if the endpoint isn't accessible.</span></span>
  
<span data-ttu-id="625ce-490">Si está intentando usar Office 365 y se dando cuenta de servicios de terceros no están accesibles desea [asegurarse de que todos los nombres de dominio completos marcados obligatorio u opcional en este artículo se permiten a través del proxy y el firewall](urls-and-ip-address-ranges.md).</span><span class="sxs-lookup"><span data-stu-id="625ce-490">If you're attempting to use Office 365 and are finding third party services aren't accessible you'll want to [ensure all FQDNs marked required or optional in this article are allowed through the proxy and firewall](urls-and-ip-address-ranges.md).</span></span>
  
### <a name="i-cant-or-dont-want-to-use-any-secondary-services"></a><span data-ttu-id="625ce-491">I no se puede o no desea utilizar todos los servicios secundarios</span><span class="sxs-lookup"><span data-stu-id="625ce-491">I can't or don't want to use any secondary services</span></span>
<span data-ttu-id="625ce-492"><a name="bkmk_secondary"> </a></span><span class="sxs-lookup"><span data-stu-id="625ce-492"></span></span>

<span data-ttu-id="625ce-p184">Servicios secundarios son los servicios de Microsoft que no se encuentren dentro del control de Office 365. Estos son cosas como la red perimetral, servicios de medios de Azure y Azure redes de distribución de contenido. Estos son todos los necesarios para usar Office 365 y deben ser accesibles.</span><span class="sxs-lookup"><span data-stu-id="625ce-p184">Secondary services are Microsoft services that don't fall within Office 365 control. These are things like the edge network, Azure Media Services, and Azure Content Delivery Networks. These are all required to use Office 365 and must be reachable.</span></span>
  
<span data-ttu-id="625ce-496">Si está intentando usar Office 365 y se dando cuenta de servicios de terceros no están accesibles desea [asegurarse de que todos los nombres de dominio completos marcados obligatorio u opcional en este artículo se permiten a través del proxy y el firewall](urls-and-ip-address-ranges.md).</span><span class="sxs-lookup"><span data-stu-id="625ce-496">If you're attempting to use Office 365 and are finding third party services aren't accessible you'll want to [ensure all FQDNs marked required or optional in this article are allowed through the proxy and firewall](urls-and-ip-address-ranges.md).</span></span>
  
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a><span data-ttu-id="625ce-497">¿Cómo se puede bloquear el acceso a los servicios de consumidor de Microsoft?</span><span class="sxs-lookup"><span data-stu-id="625ce-497">How do I block access to Microsoft's consumer services?</span></span>
<span data-ttu-id="625ce-498"><a name="bkmk_consumer"> </a></span><span class="sxs-lookup"><span data-stu-id="625ce-498"></span></span>

<span data-ttu-id="625ce-p185">Restricción del acceso a nuestros servicios de consumidor debe realizarse bajo su responsabilidad, la forma confiable sólo a los servicios de consumidor de bloque es restringir el acceso a la *login.live.com* FQDN. Este FQDN se usa en un amplio conjunto de servicios, incluidos los servicios que no sean consumidor como MSDN, TechNet y otros. Restricción del acceso a este FQDN puede ocasionar la necesidad de incluir también excepciones a la regla para las solicitudes de red asociados con estos servicios.</span><span class="sxs-lookup"><span data-stu-id="625ce-p185">Restricting access to our consumer services should be done at your own risk, the only reliable way to block consumer services is to restrict access to the  *login.live.com*  FQDN. This FQDN is used by a broad set of services including non-consumer services such as MSDN, TechNet, and others. Restricting access to this FQDN may result in the need to also include exceptions to the rule for network requests associated with these services.</span></span> 
  
<span data-ttu-id="625ce-502">Tenga en cuenta que bloquear el acceso a los servicios de consumidor de Microsoft por sí solo no impedir la capacidad de a alguien de la red a la información de exfiltrate mediante un inquilino de Office 365 o cualquier otro servicio.</span><span class="sxs-lookup"><span data-stu-id="625ce-502">Keep in mind that blocking access to the Microsoft consumer services alone won't prevent the ability for someone on your network to exfiltrate information using an Office 365 tenant or other service.</span></span>
  
## <a name="related-topics"></a><span data-ttu-id="625ce-503">Temas relacionados</span><span class="sxs-lookup"><span data-stu-id="625ce-503">Related Topics</span></span>

[<span data-ttu-id="625ce-504">Intervalos de IP del centro de datos de Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="625ce-504">Microsoft Azure Datacenter IP Ranges</span></span>](https://www.microsoft.com/download/details.aspx?id=41653)
  
[<span data-ttu-id="625ce-505">Espacio IP pública de Microsoft</span><span class="sxs-lookup"><span data-stu-id="625ce-505">Microsoft Public IP Space</span></span>](https://www.microsoft.com/download/details.aspx?id=53602)
  
[<span data-ttu-id="625ce-506">Requisitos de infraestructura de red para Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="625ce-506">Network infrastructure requirements for Microsoft Intune</span></span>](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[<span data-ttu-id="625ce-507">ExpressRoute y power BI</span><span class="sxs-lookup"><span data-stu-id="625ce-507">Power BI and ExpressRoute</span></span>](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[<span data-ttu-id="625ce-508">Direcciones URL e intervalos de direcciones IP de Office 365</span><span class="sxs-lookup"><span data-stu-id="625ce-508">Office 365 URLs and IP address ranges</span></span>](urls-and-ip-address-ranges.md)
  
[<span data-ttu-id="625ce-509">Administrar ExpressRoute para la conectividad de Office 365</span><span class="sxs-lookup"><span data-stu-id="625ce-509">Managing ExpressRoute for Office 365 connectivity</span></span>](managing-expressroute-for-connectivity.md)
  
[<span data-ttu-id="625ce-510">Principios de conectividad de red de Office 365</span><span class="sxs-lookup"><span data-stu-id="625ce-510">Office 365 Network Connectivity Principles</span></span>](office-365-network-connectivity-principles.md)
  

