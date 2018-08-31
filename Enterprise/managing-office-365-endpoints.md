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
# <a name="managing-office-365-endpoints"></a>Administración de extremos de Office 365

## <a name="office-365-network-connectivity"></a>Conectividad de red de Office 365

 Las conexiones a Office 365 constan de gran volumen, las solicitudes de red de confianza que realizar mejor cuando haya realizado a través de una salida de latencia baja está próxima al usuario. Algunas conexiones de Office 365 pueden beneficiarse de la optimización de la conexión. 
  
1. Asegúrese de su firewall permitir listas permiten para la conectividad a los extremos de Office 365.
    
2. Use la infraestructura de proxy para permitir la conectividad a Internet con caracteres comodín y los destinos no publicados.
    
3. Mantener una configuración de red perimetral óptimo.
    
4. [Asegúrese de que está obteniendo la mejor conectividad](https://aka.ms/o365perfprinciples).
    
5. Lea los [Principios de conectividad de red de Office 365](office-365-network-connectivity-principles.md) para comprender los principios de conectividad para administrar el tráfico de Office 365 y obtener el mejor rendimiento posible de forma segura. 
    
![Conectarse a Office 365 a través de firewalls y servidores proxy.](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)
  
## <a name="update-your-firewalls-outbound-allow-lists"></a>Actualización del firewall de salida permitir listas

Puede optimizar la red por enviar que todas las solicitudes de red de Office 365 directamente a través de su servidor de seguridad de confianza, omitir la inspección del nivel de todos los paquetes adicionales o procesamiento. Esto reduce el rendimiento lento de latencia y reduce los requisitos de capacidad de perímetro. La forma más sencilla para elegir qué red solicita confiar es usar nuestros archivos PAC previamente creados en la ficha **servidores proxy de** arriba. 
  
Si su firewall bloquea el tráfico saliente, querrá garantizar que todos de la dirección IP y FQDN aparecen como **necesarios** en este [archivo XML](https://go.microsoft.com/fwlink/?LinkId=533185) se encuentran en la lista Permitir. Reconocer que todos los servicios requieren el uso de algunos servicios de terceros 3ª. Se no proporcionar las direcciones IP para estos servicios parte 3ª como proveedores de certificado proveedores, redes de distribución de contenido, DNS y así sucesivamente. Para la funcionalidad completa de Office 365, debe ser capaz de llegar a todos los destinos solicitados por Office 365, independientemente de la cantidad de información se publique sobre el destino. 
  
Muchos destinos no tienen una dirección IP publicada o aparecen como un dominio comodín con ningún nombre de dominio completo específico, para usar esta funcionalidad debe poder resolver estas solicitudes de red a la dirección IP actual de direcciones que se solicita y enviar el solicitud de red a través de Internet.
  
Automatizar el proceso mediante el uso de un firewall que analiza el archivo XML en su nombre y actualiza las reglas automáticamente en función de los servicios o características de que planeación enrutar directamente a través del firewall. También puede usar la herramienta de [Azure rango](https://azurerange.azurewebsites.net/) que se ha generado por la Comunidad y analiza el XML para usted con opciones de exportación de configuración de la lista ruta Cisco XE o ACL, texto sin formato o CSV. 
  
Una explicación más extensa de los destinos de red está disponible en nuestro [sitio de referencia](urls-and-ip-address-ranges.md) así como a través de nuestro [RSS en función de registro de cambios](https://go.microsoft.com/fwlink/p/?linkid=236301) por lo que se puede suscribir a los cambios. 
  
<a name="pacfiles"> </a>
## <a name="configure-outbound-paths-with-pac-files"></a>Configurar las rutas de acceso de salida con archivos PAC

Usar archivos PAC o WPAD para administrar las solicitudes de red que están asociados con Office 365, pero no tienen una dirección IP proporcionada. Las solicitudes de red típicas que se envían a través de un dispositivo de proxy o perimetral provocar latencia adicional. Mientras que la autenticación proxy incurre el impuesto más grande, otros servicios, como la búsqueda de reputación e intentos para inspeccionar paquetes pueden provocar una experiencia de usuario deficiente. Además, estos dispositivos de red perimetral necesitan suficiente capacidad para procesar todas las solicitudes de red. Se recomienda no usar la infraestructura de proxy o inspección para solicitudes de red de Office 365 directas.
  
Use uno de nuestros archivos PAC como punto de partida para determinar qué tráfico de red que se van a enviar a un servidor proxy y que se van a enviar a un servidor de seguridad. Si está familiarizado con los archivos PAC o WPAD, leído esta entrada acerca de los [archivos de implementación PAC](https://blogs.technet.microsoft.com/undocumentedfeatures/2016/04/06/deploying-the-office-365-proxy-pac-to-manage-your-users/) de uno de nuestros consultores de Office 365. Desea revisar estos como punto de partida y modificar para adaptarse a su entorno. 
  
 **10/7/2018 han actualizado los archivos PAC**. 
  
### <a name="1---pac-file-separates-required-internet-fqdns-from-known-office-365-fqdn"></a>#1 - archivo PAC: separa necesarios y los FQDN de Internet desde conocidos Office 365 FQDN.

El primer ejemplo es una demostración de nuestro enfoque recomendado para administrar extremos a través de Internet sólo. Omite al servidor proxy para destinos de Office 365, donde la dirección IP se publica y envía las solicitudes de red restantes para el proxy.
  
Fragmento de código:
  
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

### <a name="2---pac-file-connect-to-office-365-over-the-internet-and-expressroute"></a>#2: archivo PAC: conectarse a Office 365 a través de Internet y ExpressRoute
<a name="bkmk_inet-aer"> </a>

El segundo ejemplo es una demostración de nuestro enfoque recomendado para administrar las conexiones de circuitos ExpressRoute e Internet estén disponibles. Envía ExpressRoute anuncian destinos al circuito ExpressRoute y Internet sólo anuncia destinos para el proxy.
  
Fragmento de código:
  
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

### <a name="3---pac-file-manage-all-office-365-destinations-collectively"></a>#3 - archivo PAC: administrar de forma colectiva todos los destinos de Office 365
<a name="bkmk_inet-direct"> </a>

El tercer ejemplo muestra cómo enviar todas las solicitudes de red asociadas con Office 365 a un único destino. Esto se suele utilizar para omitir la inspección de todos los de las solicitudes de red de Office 365 y ofrece un formato donde todas las publicadas extremos está en la lista en el formato de PAC que se usará para la personalización.
  
Fragmento de código:
  
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

### <a name="use-custom-scripts-or-manually-create-your-own-pac-files"></a>Usar secuencias de comandos personalizadas o crear manualmente sus propios archivos PAC
<a name="pacfiles_manual"> </a>

Aquí tiene unas más herramientas de la Comunidad, si ha creado algo que le gustaría compartir deje una nota en los comentarios. Ninguno de la Comunidad de herramientas que se mencionan en este artículo son oficialmente compatible o mantenida por Microsoft y se proporcionan aquí para su comodidad.
  
- Es la herramienta más antigua de generado por la Comunidad para ayudar a administrar el proceso, una herramienta creada por un miembro de la Comunidad de Office 365. Éste es el vínculo para [Descargar](https://gallery.technet.microsoft.com/Office-365-Proxy-Pac-60fb28f7).
    
- Prueba de concepto con reglas de firewall exportable: [API de IP de Microsoft en la nube](https://mscloudips.azurewebsites.net/).
    
- Desde Praktyk de TI: [Conversión de RSS](https://gallery.technet.microsoft.com/Convert-the-RSS-channel-5efe18b7) y [conversión de XML](https://gallery.technet.microsoft.com/Convert-the-O365IPAddresses-9890d896).
    
- De Peter Abele: [Descargar](https://gallery.technet.microsoft.com/How-to-create-an-up-to-b1fc33f3).
    
- Usar el análisis de la red para determinar la red que solicita debe omitir la infraestructura de proxy. Los FQDN más comunes que se utiliza para omitir a los servidores proxy del cliente incluyen los siguientes debido al volumen de tráfico de red enviados y recibidos desde estos extremos.
    
  ```
  outlook.office365.com
  outlook.office.com
  <tenant-name>.sharepoint.com
  <tenant-name>-my.sharepoint.com
  <tenant-name>-<app>.sharepoint.com
  *.Lync.com
  
  ```

- Asegúrese de que las solicitudes de red que se envían directamente al servidor de seguridad tienen una entrada correspondiente en el servidor de seguridad Permitir lista Permitir que la solicitud pase a través de.
    
## <a name="perimeter-network-integration"></a>Integración de la red perimetral
<a name="BKMK_Perimeter"> </a>

¿Sabía que... de Microsoft WAN es una de las redes troncales mayores en el mundo?
  
Es true, que esta red masiva es lo que hace que Office 365 y nuestras otros servicios de nube funcionan con independencia de dónde en el mundo que es. Nuestra red consta de gran ancho de banda, latencia baja, vínculos con capacidad de conmutación por error con miles de millas de ruta de propiedad privada de fibra oscura y multi-Terabit conexiones entre los nodos de centros de datos y el borde, todos para facilitar el uso de nuestros servicios en la nube.
  
Con una red similar, desea que los dispositivos de su organización se conecten a nuestra red de tan pronto como sea posible. Con relaciones de interconexión ISP más 2500 globalmente y 70 puntos de presencia, introducción desde la red a nuestro debería ser transparente. No se puede dañar a dedicar unos minutos, asegurándose de que relación de interconexión de su ISP es el más óptima, [le presentamos algunos ejemplos](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__) de buena y no tan buena interconexión no intervención a nuestra red. 
  
Puede manualmente o configurar automáticamente los dispositivos de la red para controlar las solicitudes de red del aplicación de Office 365, dependiendo de su equipo de forma óptima. Los cambios de configuración que debe tomar controlar el tráfico de red de Office 365 de forma óptima dependerá de su entorno. Office 365 red solicitudes pueden beneficiarse de las configuraciones de red que permiten lo siguiente:
  
- Prioridad sobre el tráfico de red menos importante.
    
- Enrutar a una salida local a fin de evitar backhauling a través de una red WAN lenta vínculo mientras se aprovecha la latencia baja disponible en la red de Microsoft. [Esta es una buena explicación](https://blogs.technet.microsoft.com/onthewire/2017/05/03/office-365-connectivity-guidance-part-2/) basado en contrataciones de clientes. 
    
- Uso de DNS cerca de una salida local para asegurarse de la solicitud de red que deja la salida local llega a la ubicación de interconexión de Microsoft más cercana.
    
- Exclusión de inspección profunda del paquete u otros para satisfacer los requisitos de latencia en escala de procesamiento de paquetes de red intensiva.
    
Dispositivos de red modernos incluyen las capacidades para administrar las solicitudes de red para las aplicaciones de confianza, como Office 365 de forma diferente que el tráfico de Internet que no se confía y genérico. Con el panorama de emergente de soluciones SD WAN, también se puede realizar dicha diferenciación de selección de ruta de acceso y de tráfico con conocimiento del estado cambiante de la red como punto de disponibilidad de tiempo, latencia o el rendimiento de las distintas rutas de acceso de conectividad entre el usuario y la nube.
  
Vea [red y migración de planeación para Office 365](network-and-migration-planning.md), [solución de problemas de rendimiento de planeación de Office 365](performance-troubleshooting-plan.md)y [lista de comprobación de planeación de implementación para Office 365](deployment-planning-checklist.md) para obtener orientación adicional acerca de cómo planear la configuración de red. 
  
### <a name="to-implement-this-scenario"></a>Para implementar este escenario:

Compruebe con su proveedor de soluciones o servicio de red si pueden utilizar direcciones URL en Office 365 y las definiciones de IP de XML para facilitar una sobrecarga local (para el usuario), bajo salida para Office 365 el tráfico de red, administración su prioridad con respecto a otras aplicaciones y ajustan el ruta de acceso de red para las conexiones de Office 365 en la red de Microsoft según las condiciones de red cambiantes. Algunas soluciones de descargan y automatizan la definición de direcciones URL en Office 365 y XMLs IP en sus pilas.
  
Asegúrese siempre de que la solución implementada tiene necesario grado de resistencia, redundancia de geo adecuado de la ruta de acceso de red para el tráfico de Office 365 y los cambios realizados en IP y URL de Office 365 adapta como se convierten en publicado.
  
## <a name="web-service"></a>Servicio web
<a name="webservice"> </a>

Para ayudarle a identificar y diferenciar el tráfico de red de Office 365, un nuevo servicio web publica los extremos de Office 365, haciendo que sea más fácil para evaluar, configurar y Manténgase actualizado con los cambios. Este nuevo servicio de web (ahora en la vista previa), eventualmente reemplazará las listas de extremos en el artículo [las direcciones URL de Office 365 y los intervalos de direcciones IP](urls-and-ip-address-ranges.md) , junto con las versiones de RSS y XML de los datos. Estas de formato de datos de extremo se planea desfasada en 2 de octubre de 2018. 
  
Como un cliente o un proveedor de dispositivos de red perimetral, puede crear con el nuevo servicio web basado en REST para la dirección IP de Office 365 y las entradas de FQDN.
  
- Para obtener la versión más reciente de los intervalos de direcciones IP y URL de Office 365, use [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).
    
- Para los datos en la página de intervalos de direcciones IP para los servidores proxy y las direcciones URL de Office 365, use [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).
    
- Para obtener los cambios más recientes, utilice [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).
    
Como un cliente, puede usar este servicio web para: 
  
- Actualizar los scripts de PowerShell para obtener datos de extremo de Office 365 y modificar cualquier formato para los dispositivos de redes.
    
- Use esta información para actualizar archivos de PAC implementados en equipos cliente.
    
Como un proveedor de dispositivos de red perimetral, puede usar este servicio web para: 
  
- Crear y probar el software de dispositivo para descargar la lista para la configuración automatizada. 
    
- Comprobar la versión actual.
    
- Obtener los cambios actuales.
    
Las secciones siguientes describen la vista previa de este servicio web, lo que podría cambiar con el tiempo hasta que el servicio esté disponible para el público. 
  
Los datos en el servicio web están actualizados y no va a realizar más cambios en las direcciones URL de servicio de web o devuelve el esquema de los datos antes del lanzamiento de la disponibilidad general de este servicio web.
  
Para obtener información adicional, vea:
  
- [Entrada de blog de anuncio en el foro de la Comunidad de Office 365 Tech](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
    
- [Foro de la Comunidad de Office 365 Tech para preguntas sobre el uso de los servicios web](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)
    
### <a name="common-parameters"></a>Parámetros comunes

Estos parámetros son comunes a todos los métodos de servicio web:
  
- formato de **= CSV | JSON** -parámetro de cadena de consulta. De forma predeterminada, el formato de datos que se devuelven es JSON. Incluir este parámetro opcional para devolver los datos en formato de valores separados por comas (CSV). 
    
- **ClientRequestId** - parámetro de cadena de consulta. Un GUID requiere que se genera para la asociación de la sesión de cliente. Debe generar un GUID para cada equipo cliente que llama al servicio web. No use los GUID que se muestra en los ejemplos siguientes, debido a que puedan estar bloqueadas por el servicio web en el futuro. Formato GUID es xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx, donde x representa un número hexadecimal. Para generar un GUID, utilice el comando de PowerShell [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) . 
    
### <a name="version-web-method"></a>Método web de la versión

Microsoft actualiza la dirección IP de Office 365 y las entradas de FQDN al final de cada mes y ocasionalmente fuera de ciclo para operativas o satisfacer los requisitos. Los datos para cada instancia publicado se asignan a un número de versión. El método web de versión permite sondear para la versión más reciente para cada instancia de servicio de Office 365. Se recomienda que comprobar la versión del diario, o como máximo, cada hora.
  
Hay un parámetro para el método web de versión:
  
- **AllVersions = true** -parámetro de cadena de consulta. De forma predeterminada, la versión devuelta es la más reciente. Incluir este parámetro opcional para solicitar que todas las versiones publicadas. 
    
- **Instancia** - el parámetro de ruta. Este parámetro opcional especifica la instancia para devolver la versión para. Si se omite, se devuelven todas las instancias. Sesiones válidos son: en todo el mundo, China, Alemania, USGovDoD, USGovGCCHigh 
    
El resultado del método web de versión puede ser un único registro o una matriz de registros. Los elementos de cada registro son:
  
- instancia - el nombre corto de la instancia de servicio de Office 365.
    
- último - la versión más reciente para los extremos de la instancia especificada.
    
- versiones - una lista de todas las versiones anteriores para la instancia especificada. Este elemento sólo está incluido, si el parámetro AllVersions es true.
   
#### <a name="examples"></a>Ejemplos
  
URI de la solicitud en el ejemplo 1: ** <span>https:</span>//endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**
  
Este URI devuelve la versión más reciente de cada instancia de servicio de Office 365. Resultado de ejemplo:
  
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
> El GUID para el parámetro ClientRequestID en estos URI son sólo un ejemplo. Para probar la web de los URI de fuera de servicio, genere su propio GUID. Los GUID que se muestra en estos ejemplos se pueden bloquear por el servicio web en el futuro. 
  
URI de la solicitud en el ejemplo 2: ** <span>https:</span>//endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**
  
Este URI devuelve la última versión de la instancia de servicio especificada de Office 365. Resultado de ejemplo:
  
```
{
 "instance": "Worldwide",
 "latest": "2018063000"
}
```

URI de la solicitud de ejemplo 3: ** <span>https:</span>//endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId = b10c5ed1-bad1-445f-b386-b919946339a7**
  
Este URI muestra resultados en formato CSV. Resultado de ejemplo:
  
```
instance,latest
Worldwide,2018063000
```

URI de la solicitud de ejemplo 4: ** <span>https:</span>//endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId = b10c5ed1-bad1-445f-b386-b919946339a7**
  
Este URI muestra todas las versiones anteriores que se han publicado para la instancia de servicio en todo el mundo de Office 365. Resultado de ejemplo:
  
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

### <a name="endpoints-web-method"></a>Los extremos de web (método)

El método web de extremos devuelve todos los registros de intervalos de direcciones IP y direcciones URL que componen el servicio Office 365. Parámetros para el método web de extremos son:
  
- **ServiceAreas** - parámetro de cadena de consulta. Una lista separada por comas de las áreas de servicio. Elementos válidos son común, Exchange, SharePoint, Skype. Debido a que los elementos comunes de área de servicio son un requisito previo para todas las demás áreas de servicio, el servicio web de ellos incluirá siempre. Si no se incluye este parámetro, se devuelven todas las áreas de servicio. 
    
- **TenantName** - parámetro de cadena de consulta. El nombre del inquilino de Office 365. El servicio web toma el nombre proporcionado y lo inserta en elementos de las direcciones URL que incluyen el nombre del inquilino. Si no proporciona un nombre del inquilino, las partes de las direcciones URL tienen el carácter comodín (\*). 
    
- **NoIPv6** - parámetro de cadena de consulta. Establecer en True para las direcciones IPv6 de excluir de los resultados, por ejemplo, si no usa IPv6 en la red. 
    
- **Instancia** - el parámetro de ruta. Este parámetro obligatorio especifica la instancia para devolver los extremos para. Sesiones válidos son: en todo el mundo, China, Alemania, USGovDoD, USGovGCCHigh. 
    
El resultado del método web de extremos es una matriz de registros con cada registro que representa un conjunto de extremo. Los elementos de cada registro son:
  
- establece en el identificador - el número de identificador inmutable del extremo.
    
- serviceArea - del área de servicio que es parte de: común, Exchange, SharePoint o Skype.
    
- las direcciones URL - conjunto de direcciones URL para el extremo. Una matriz JSON de registros DNS. Se omite si está en blanco.
    
- establecer los puertos TCP para el extremo de tcpPorts. Tienen el formato de todos los elementos de puertos como una lista separada por comas de los puertos o intervalos de puertos separados por un carácter de guión (-). Los puertos se aplican a todas las direcciones IP y todas las direcciones URL en que el extremo se establece para esa categoría. Se omite si está en blanco.
    
- udpPorts - puertos UDP para la dirección IP intervalos en este conjunto de extremo de direcciones. Se omite si está en blanco.
    
- IP - intervalos de direcciones IP asociados a este extremo que se establezca como asociado con los puertos TCP o UDP mostrados. Se omite si está en blanco.
    
- categoría - establecido de la categoría de conectividad para el extremo. Los valores válidos son optimizar, permitir y predeterminado. Obligatorio.
    
- expressRoute - True o False si este conjunto de extremo se enruta a través de ExpressRoute.
    
- requerido - True si es necesario tener conectividad para Office 365 sean compatibles con este conjunto de extremo. Se omite si es false.
    
- notas - para extremos opcionales, este texto describe la funcionalidad de Office 365 no aparecerá si direcciones IP o las direcciones URL en este extremo set no se puede tener acceso en la capa de red. Se omite si está en blanco.
    
#### <a name="examples"></a>Ejemplos
  
URI de la solicitud en el ejemplo 1: ** <span>https:</span>//endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**
  
Este URI Obtiene todos los extremos de la instancia de todo el mundo de Office 365 para todas las cargas de trabajo. Resultados de ejemplo que muestra un extracto del resultado:
  
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

Conjuntos de extremo adicionales no se incluyen en este ejemplo.
  
URI de la solicitud en el ejemplo 2: ** <span>https:</span>//endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId = b10c5ed1-bad1-445f-b386-b919946339a7**
  
En este ejemplo se obtiene los extremos de la instancia de todo el mundo en Office 365 para Exchange Online y dependencias sólo.
  
El resultado por ejemplo 2 es similar al ejemplo 1, excepto en que los resultados no incluirán extremos para SharePoint Online o de Skype para profesionales en línea.
  
### <a name="changes-web-method"></a>Cambios de web (método)

El método web de cambios devuelve las actualizaciones más recientes que se hayan publicado. Esto suele ser cambios del mes anterior a intervalos de direcciones IP y direcciones URL.
  
> [!NOTE]
> Datos de la API de cambios es precisos en la vista previa y deben ser usados para el desarrollo y prueba sólo. 
  
El parámetro para el método web de cambios es:
  
- **Versión** : parámetro de ruta de dirección URL necesarios. La versión que se ha implementado actualmente, y que desea ver los cambios desde esa versión. El formato es YYYYMMDDNN. 
    
El resultado del método web de cambios es una matriz de registros con cada registro que representa un cambio en una versión específica de los extremos. Los elementos de cada registro son:
  
- Id: identificador inmutable del registro de cambios.
    
- endpointSetId - el identificador del extremo establece registro que se ha cambiado. Obligatorio.
    
- disposición - Esto puede ser de cambiar, agregar o quitar y describe lo que hizo el cambio en el registro del conjunto de extremo.
    
- versión: la versión del extremo publicado establece en que se introdujo el cambio. Números de versión son con el formato YYYYMMDDNN, donde NN es un número natural incrementado si hay varias versiones necesarias para ser publicado en un solo día.
    
- anterior - que establezca una subestructura que se detallan los valores anteriores de los elementos cambiados en el extremo. Esto no se incluirán para conjuntos de extremo recién agregado. Incluye tcpPorts, udpPorts, ExpressRoute, categoría, necesaria, notas.
    
- actual - una subestructura que se detallan los valores de los elementos de los cambios en la endpoinset actualizados. Incluye tcpPorts, udpPorts, ExpressRoute, categoría, necesaria, notas.
    
- Add - colecciones de conjunto de una estructura de sub que incluye los elementos que se agregará al extremo. Se omite si no hay ningún adiciones.
    
  - effectiveDate - define los datos cuando las adiciones será live en el servicio.
    
  - IP - elementos que se agregarán a la matriz de IP.
    
  - Elementos de las direcciones URL que se agregará a la matriz de direcciones URL.
    
- Remove - que establezca una subestructura que incluye los elementos que desea quitar desde el punto final. Se omite si no hay ningún eliminaciones.
    
  - IP - elementos que debe quitarse de la matriz de IP.
    
  - las direcciones URL de los elementos que debe quitarse de la matriz de direcciones URL.
    
 **Ejemplos:**
  
URI de la solicitud en el ejemplo 1: ** <span>https:</span>//endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**
  
Esto solicita todos los cambios anteriores a la instancia de servicio en todo el mundo de Office 365. Resultado de ejemplo:
  
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

URI de la solicitud en el ejemplo 2: ** <span>https:</span>//endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**
  
Esto solicita cambios con respecto a la versión especificada a la instancia de Office 365 en todo el mundo. En este caso, la versión especificada es el último. Resultado de ejemplo:
  
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

### <a name="example-powershell-script"></a>Script de PowerShell de ejemplo

Aquí es un script de PowerShell que puede ejecutar para ver si hay acciones que debe tener para los datos actualizados. Este script comprueba el número de versión para los extremos de instancia Office 365 en todo el mundo. Cuando se produce un cambio, descarga los extremos y filtros para los extremos de categoría "Permitir" y "Optimizar". También se utiliza un único ClientRequestId a través de varias llamadas y se guarda la versión más reciente que se encuentra en un archivo temporal. Esta secuencia de comandos se debe llamar una vez cada hora para comprobar si hay una actualización de versión.
  
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

### <a name="example-python-script"></a>Secuencia de comandos de ejemplo Python

Aquí es una secuencia de comandos de Python, probado con Python 3.6.3 en 10 de Windows, que se pueden ejecutar para ver si hay acciones que debe tener para los datos actualizados. Este script comprueba el número de versión para los extremos de instancia Office 365 en todo el mundo. Cuando se produce un cambio, descarga los extremos y filtros para los extremos de categoría "Permitir" y "Optimizar". También se utiliza un único ClientRequestId a través de varias llamadas y se guarda la versión más reciente que se encuentra en un archivo temporal. Esta secuencia de comandos se debe llamar una vez cada hora para comprobar si hay una actualización de versión.
  
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

### <a name="web-service-interface-versioning"></a>Control de versiones de interfaz de servicio de Web

Las actualizaciones de los parámetros o los resultados de estos métodos de servicio web pueden ser necesarias en el futuro. Después de publica la versión de la disponibilidad general de estos servicios web, Microsoft hará un esfuerzo razonable para proporcionar notificación anticipada de materiales actualizaciones al servicio web. Cuando Microsoft cree que una actualización requerirá cambios en los clientes mediante el servicio web, Microsoft mantendrá la versión anterior (versión inmediatamente anterior) del servicio de web disponible para al menos doce (12) meses después del lanzamiento de la nueva versión. Los clientes que no actualizar durante ese tiempo posible que pueda obtener acceso el servicio web y sus métodos. Los clientes deben asegurarse de que los clientes del servicio web continuarán trabajando sin errores si se realizan los cambios siguientes a la firma de interfaz de servicio web:
  
- Adición de un nuevo parámetro opcional a un método web existente que no tiene que ser proporcionado por los clientes más antiguos y no afecta el resultado recibe un cliente más antiguos.
    
- Adición de un nuevo atributo con nombre de uno de los elementos del resto de respuesta o columnas adicionales a la respuesta CSV.
    
- Adición de un nuevo método web con un nombre nuevo que no se llama a los clientes más antiguos.
    
## <a name="faq"></a>Preguntas más frecuentes

Preguntas más frecuentes con frecuencia administrador sobre la conectividad de:
  
### <a name="how-do-i-submit-a-question"></a>¿Cómo se puede enviar una pregunta?

Haga clic en el vínculo en la parte inferior para indicar si el artículo ha sido útil y enviar preguntas adicionales. Se supervisión los comentarios y actualización las preguntas aquí con las preguntas más frecuentes.
  
### <a name="when-is-the-xml-file-updated"></a>¿Cuando se actualice el archivo XML?

Cuando se anuncian nuevos extremos, suele haber un búfer de más de 30 días antes de que sean efectivas y de las solicitudes de red dirigirán a ellos. Este búfer es garantizar a que los clientes y los socios tienen una oportunidad para actualizar sus sistemas. IP y FQDN prefijo adiciones y eliminaciones se procesan en el archivo XML al mismo tiempo como el anuncio, lo que significa que un FQDN nuevo estará en el archivo XML de 30 días antes de su uso. Dado que se deje de enviar las solicitudes de red a los extremos que nos estamos quitar antes de anunciar su eliminación, cuando se quita el extremo de la XML al mismo tiempo como el anuncio ya está no usado.
  
### <a name="how-can-i-be-notified-of-changes"></a>¿Cómo puedo ¿se recibe una notificación de cambios?
<a name="bkmk_changes"> </a>

Los extremos de Office 365 se publican al final de cada mes con el aviso de 30 días. En ocasiones, los cambios se producirán más de una vez un mes o con períodos más cortos de aviso. Cuando se agrega un extremo, la fecha efectiva que aparecen en la [fuente RSS](https://go.microsoft.com/fwlink/p/?linkid=236301) es la fecha después de que se van a enviar las solicitudes de red para el extremo. Si está familiarizado con RSS, aquí es cómo [suscribirse a través de Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) o puede [tener la actualizaciones de correo electrónico de fuente RSS](https://go.microsoft.com/fwlink/p/?LinkId=532417).
  
### <a name="how-do-i-read-the-rss-change-log"></a>¿Cómo se puede leer que el RSS cambiar registro?
<a name="bkmk_changes"> </a>

Después de suscribirse a la fuente RSS, puede analizar la información usted mismo o con una secuencia de comandos. En la siguiente tabla se describe el formato de RSS de la fuente o facilitar la tarea.
  
|**Sección**|**Parte 1**|**Parte 2**|**Parte 3**|**Parte 4**|**Parte 5**|**Parte 6**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|**Descripción** <br/> |Contador  <br/> |Fecha después de que puede esperar que se envíen al extremo de las solicitudes de red.  <br/> |Descripción básica de la característica o servicio que requiere el extremo.  <br/> |¿Puede conectarse a este extremo en un circuito ExpressRoute además de internet?  <br/> |**Sí** - puede conectarse a este extremo en internet y ExpressRoute.  <br/> **No** : sólo se puede conectar a este extremo en internet.  <br/> |El intervalo IP o FQDN que se agregan o quitan de destino.  <br/> |
|**Ejemplo** <br/> |1 /  <br/> |[Eficaz xx/xx/xxx.  <br/> |Obligatorio: \<descripción\>.  <br/> |ExpressRoute:  <br/> |\<Sí/No\>.  <br/> |\<FQDN/IP\>],  <br/> |
   
Un par otros aspectos a tener en cuenta, cada entrada tiene un conjunto común de los delimitadores:
  
- **/**-Después de la cuenta 
    
- **[** - para indicar la entrada para el recuento 
    
- **.** -usar entre cada sección distinta de la entrada 
    
- **],** - para indicar el final de una única entrada 
    
- **].** -Para indicar el final de todas las entradas 
    
### <a name="how-do-i-determine-the-location-of-my-tenant"></a>¿Cómo se puede determinar la ubicación de mi inquilino?

 **Ubicación del inquilino** se determina mejor con nuestro [Centro de datos se asignan](https://o365datacentermap.azurewebsites.net/).
  
### <a name="am-i-peering-appropriately-with-microsoft"></a>¿Estoy interconexión adecuadamente con Microsoft?

 **Ubicaciones de Peering** se describen con más detalle en [interconexión con Microsoft](https://www.microsoft.com/peering).
  
Con relaciones de interconexión ISP más 2500 globalmente y 70 puntos de presencia, introducción desde la red a nuestro debería ser transparente. No se puede dañar a dedicar unos minutos, asegurándose de que relación de interconexión de su ISP es el más óptima, [le presentamos algunos ejemplos](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__) de buena y no tan buena interconexión no intervención a nuestra red. 
  
### <a name="how-do-i-determine-which-ip-addresses-to-accept-over-expressroute"></a>Cómo determinar qué direcciones IP para aceptar a través de ExpressRoute

 **ExpressRoute aceptan rutas** se definen mediante [intervalos IP de Microsoft](https://www.microsoft.com/download/details.aspx?id=53602) y las específicas de Office 365 [Comunidades BGP](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099).
  
### <a name="how-do-i-determine-which-endpoints-i-need"></a>¿Cómo se puede determinar qué extremos necesito?

Con regularidad agregamos nuevas características y servicios para el conjunto de aplicaciones de Office 365, expandir el panorama de la conectividad. Si se está suscrito a la E3 o E5 SKU, piense en la lista de extremos de la forma simple es que necesita todos ellos para obtener la funcionalidad completa para el conjunto de aplicaciones. Si no está suscrito a cualquiera de estos SKU la diferencia es mínima en cuanto al número de extremos.
  
Lea los [Principios de conectividad de red de Office 365](office-365-network-connectivity-principles.md) para obtener más información sobre las categorías de extremo de Office 365 y para comprender los principios de conectividad para administrar el tráfico de Office 365 y obtener el mejor rendimiento posible de forma segura. 
  
En la imagen que aparece a continuación, puede ver un ejemplo de una parte de la tabla FQDN en la sección Office Online. Las filas se organizan por característica y las diferencias en la conectividad. Las dos primeras filas indican Office Online se basa en los extremos de marcado necesarios en el portal e identidad y autenticación de Office 365 y secciones compartidas. Esto es típico para un servicio incluido en Office 365 a se basan en estos servicios compartidos. La tercera fila indica los equipos cliente deben ser capaz de ponerse en contacto con \*. officeapps.live.com para usar Office Online y la cuarta fila indica los equipos también deben ser capaz de ponerse en contacto con \*. cdn.office.net a usar Office Online.
  
Aunque ambos fila tres y cuatro son necesarios para usar Office Online, ha ha separado para indicar que el destino es diferente:
  
1. \*. officeapps.live.com no representan una CDN, solicitudes de significado a este espacio de nombres irán directamente a un centro de datos de Microsoft.
    
2. \*. officeapps.live.com es accesible en circuitos ExpressRoute con Microsoft Peering.
    
3. Las direcciones IP asociadas con Office Online y \*. officeapps.live.com puede encontrarse siguiendo este vínculo.
    
4. \*. cdn.office.net representa una CDN hospedada por Akamai, solicitudes de significado a este espacio de nombres se vayan a un centro de datos Akamai.
    
5. \*. cdn.office.net no es accesible en circuitos ExpressRoute.
    
6. Las direcciones IP asociadas con Office Online y \*. cdn.office.net no están disponibles.
    
![Captura de pantalla de página extremos](media/42b487f3-24f3-48fe-9885-f97aae3194f3.png)
  
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a>¿Ver las solicitudes de red a direcciones IP no en la lista publicada, necesito para proporcionar acceso a ellos?
<a name="bkmk_MissingIP"> </a>

Sólo proporcionamos direcciones IP para los servidores de Office 365 que se debe enrutar directamente a través de Internet o ExpressRoute. Esto no es una lista completa de todas las direcciones IP, verá las peticiones de red. Verá las solicitudes de red de Microsoft y de terceros propietario, cancelar la publicación, las direcciones IP. Estas direcciones IP se generado dinámicamente o se administra de forma que impide que oportuna aviso cuando cambian. Si el servidor de seguridad no puede permitir el acceso basado en el FQDN para estas solicitudes de red, use un archivo PAC o WPAD para administrar las solicitudes.
  
¿Vea que una dirección IP asociada con la que desea obtener más información sobre Office 365?
  
1. Compruebe si la dirección IP que se incluye en un rango publicado mayor que con una [Calculadora de CIDR](http://jodies.de/ipcalc).
    
2. Vea si un socio propietario de la dirección IP con una [consulta whois](https://dnsquery.org/). Si es que son propiedad de Microsoft, puede ser un socio interno.
    
3. Comprobar el certificado, en un explorador se conectan a la dirección IP utilizando *HTTPS://\<dirección IP\> * , compruebe los dominios que aparecen en el certificado para comprender qué dominios están asociados con la dirección IP. Si es una propiedad de dirección IP de Microsoft y no en la lista de direcciones IP de Office 365, es probable que es la dirección IP está asociado con una CDN de Microsoft, como *MSOCDN.NET* o de otro dominio de Microsoft sin información publicada de IP. Si encuentra que el dominio en el certificado es donde se notificación para obtener una lista de la dirección IP, háganoslo saber. 
    
### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a>¿Por qué se pueden ver los nombres como nsatc.net o akadns.net en los nombres de dominio de Microsoft?
<a name="bkmk_akamai"> </a>

Office 365 y otros servicios de Microsoft usan varios servicios de terceros, como Akamai y MarkMonitor para mejorar la experiencia de Office 365. Para mantener proporcionar la mejor experiencia posible, podemos cambiar estos servicios en el futuro. De esta forma, a menudo se publique el registro CNAME que señala a un tercero dominio propietario, un registro o la dirección IP. Dominios de otros fabricantes pueden hospedar contenido, como una CDN, o pueden hospedar un servicio, como un servicio de administración de tráfico geográfica. Cuando vea las conexiones a estos terceros, estén en el formulario de un redireccionamiento o referencia, no una solicitud inicial desde el cliente. Algunos clientes necesitan para garantizar este formulario de referencia y se permite la redirección para pasar sin agregar explícitamente que la larga lista de servicios de terceros de posibles nombres de dominio completos se puede usar.
  
La lista de servicios está sujeta a cambios en cualquier momento. Algunos de los servicios que están en uso son:
  
[MarkMonitor](https://www.markmonitor.com/) está en uso cuando se ven las solicitudes que incluyan * \*. nsatc.net* . Este servicio proporciona protección de nombre de dominio y supervisión para proteger el comportamiento malintencionado. 
  
[ExactTarget](https://www.marketingcloud.com/) está en uso cuando se ven las solicitudes a * \*. exacttarget.com* . Este servicio proporciona administración de vínculos de correo electrónico y supervisión contra un comportamiento malintencionado. 
  
[Akamai](https://www.akamai.com/) está en uso cuando se ven las solicitudes que incluyan uno de los siguientes FQDN. Este servicio ofrece ubican DNS y servicios de red de entrega de contenido. 
  
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

### <a name="what-are-the-three-types-of-office-365-endpoints"></a>¿Cuáles son los tres tipos de extremos de Office 365?
<a name="bkmk_akamai"> </a>

- Conectarse a los servicios de terceros para recuperar los servicios de internet básicos, como consultas DNS y recuperación de contenido CDN. También se conecta a los servicios de terceros para aplicaciones integradas tales como la incorporación de vídeos de YouTube en los blocs de notas de OneNote.
    
- Conectarse a servicios secundarios hospedado y ejecute por Microsoft como nodos perimetrales que permiten la solicitud de red que escriba red global de Microsoft en la ubicación de internet más cercana a su equipo. Como la red mayor en tercer lugar en el planeta, esto mejora la experiencia de conectividad. También se conecta a los servicios de Microsoft Azure, como servicios de multimedia de Azure que se usan por una variedad de servicios de Office 365.
    
- Se conecta a servicios de Office 365 principales como el servidor de buzones de Exchange Online o el Skype para servidor empresarial en línea donde se encuentran los datos únicos y propietarios. Puede conectarse a los servicios de Office 365 principales por el FQDN o la dirección IP y utilizar internet o circuitos ExpressRoute. Sólo se puede conectar a los servicios secundarios con nombres de dominio completos en un circuito de internet y el tercero.
    
En el siguiente diagrama se muestra las diferencias entre estas áreas de servicio. En este diagrama, la red local del cliente en la parte inferior izquierda tiene varios dispositivos de red para ayudarle a administrar la conectividad de red. Las configuraciones como ésta son comunes para los clientes de empresa. Si la red sólo tiene un firewall entre los equipos cliente e internet, que también es compatible, y desea asegurarse de que el servidor de seguridad puede admitir nombres de dominio completos y caracteres comodín en las reglas de la lista Permitir.
  
Lea los [Principios de conectividad de red de Office 365](office-365-network-connectivity-principles.md) para obtener más información sobre las categorías de extremo de Office 365 y para comprender los principios de conectividad para administrar el tráfico de Office 365 y obtener el mejor rendimiento posible de forma segura. 
  
![Muestra los tres tipos diferentes de los extremos de la red cuando se usa Office 365](media/6582bcfa-11ba-4ac2-9b69-14bef0437670.png)
  
### <a name="i-cant-or-dont-want-to-use-any-third-party-service"></a>I no se puede o no desea utilizar cualquier servicio de otro fabricante
<a name="bkmk_thirdparty"> </a>

Office 365 es un conjunto de servicios integrados a función a través de internet, la confiabilidad y la disponibilidad promesas se basan en muchos servicios de internet estándar que están disponibles. Por ejemplo, servicios de internet estándar, como DNS, CRL y las CDN deben ser accesibles para usar Office 365, al igual que deben ser accesibles para usar los servicios de internet más modernos.
  
Además de estos servicios básicos de internet, existen servicios de terceros que sólo se usan para integrar la funcionalidad. Por ejemplo, uso de Giphy.com dentro de Microsoft Teams permite a los clientes sin ningún problema incluyen archivos GIF dentro de los equipos. De forma similar, YouTube y Flickr son los servicios de terceros que se usan para integrar sin problemas vídeos e imágenes en los clientes de Office desde internet. Mientras que son necesarios para la integración, que se han marcado como opcional en el artículo de los extremos de Office 365 lo que significa que la funcionalidad principal del servicio seguirán funcionando si el extremo no es accesible.
  
Si está intentando usar Office 365 y se dando cuenta de servicios de terceros no están accesibles desea [asegurarse de que todos los nombres de dominio completos marcados obligatorio u opcional en este artículo se permiten a través del proxy y el firewall](urls-and-ip-address-ranges.md).
  
### <a name="i-cant-or-dont-want-to-use-any-secondary-services"></a>I no se puede o no desea utilizar todos los servicios secundarios
<a name="bkmk_secondary"> </a>

Servicios secundarios son los servicios de Microsoft que no se encuentren dentro del control de Office 365. Estos son cosas como la red perimetral, servicios de medios de Azure y Azure redes de distribución de contenido. Estos son todos los necesarios para usar Office 365 y deben ser accesibles.
  
Si está intentando usar Office 365 y se dando cuenta de servicios de terceros no están accesibles desea [asegurarse de que todos los nombres de dominio completos marcados obligatorio u opcional en este artículo se permiten a través del proxy y el firewall](urls-and-ip-address-ranges.md).
  
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a>¿Cómo se puede bloquear el acceso a los servicios de consumidor de Microsoft?
<a name="bkmk_consumer"> </a>

Restricción del acceso a nuestros servicios de consumidor debe realizarse bajo su responsabilidad, la forma confiable sólo a los servicios de consumidor de bloque es restringir el acceso a la *login.live.com* FQDN. Este FQDN se usa en un amplio conjunto de servicios, incluidos los servicios que no sean consumidor como MSDN, TechNet y otros. Restricción del acceso a este FQDN puede ocasionar la necesidad de incluir también excepciones a la regla para las solicitudes de red asociados con estos servicios. 
  
Tenga en cuenta que bloquear el acceso a los servicios de consumidor de Microsoft por sí solo no impedir la capacidad de a alguien de la red a la información de exfiltrate mediante un inquilino de Office 365 o cualquier otro servicio.
  
## <a name="related-topics"></a>Temas relacionados

[Intervalos de IP del centro de datos de Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Espacio IP pública de Microsoft](https://www.microsoft.com/download/details.aspx?id=53602)
  
[Requisitos de infraestructura de red para Microsoft Intune](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[ExpressRoute y power BI](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[Direcciones URL e intervalos de direcciones IP de Office 365](urls-and-ip-address-ranges.md)
  
[Administrar ExpressRoute para la conectividad de Office 365](managing-expressroute-for-connectivity.md)
  
[Principios de conectividad de red de Office 365](office-365-network-connectivity-principles.md)
  

