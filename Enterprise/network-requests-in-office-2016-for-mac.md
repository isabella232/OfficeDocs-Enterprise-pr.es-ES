---
title: Solicitudes de red en Office para Mac
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/9/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365_Setup
search.appverid: MOM160
ms.assetid: afdae969-4046-44b9-9adb-f1bab216414b
description: Las aplicaciones de Office para Mac proporcionan una experiencia de aplicación nativa en la plataforma de macOS. Cada aplicación está diseñada para trabajar en diversos escenarios, incluidos los Estados en los que no hay acceso a la red disponible. Cuando un equipo está conectado a una red, las aplicaciones se conectan automáticamente a una serie de servicios basados en web para proporcionar funciones mejoradas. En este documento se describen los puntos de conexión y las direcciones URL que las aplicaciones intentan alcanzar y los servicios que se proporcionan. Esta información es útil para solucionar problemas de configuración de red y establecer una directiva para los servidores proxy de red. Los detalles de este artículo tienen como objetivo complementar el artículo Office 365 URL y los intervalos de direcciones.
ms.openlocfilehash: 44acbc83b2bb32e60a470dc5d3ba27f13cbd033c
ms.sourcegitcommit: 1c97471f47e1869f6db684f280f9085b7c2ff59f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/18/2019
ms.locfileid: "35781960"
---
# <a name="network-requests-in-office-for-mac"></a>Solicitudes de red en Office para Mac

Las aplicaciones de Office para Mac proporcionan una experiencia de aplicación nativa en la plataforma de macOS. Cada aplicación está diseñada para trabajar en diversos escenarios, incluidos los Estados en los que no hay acceso a la red disponible. Cuando un equipo está conectado a una red, las aplicaciones se conectan automáticamente a una serie de servicios basados en web para proporcionar funciones mejoradas. La siguiente información describe los puntos de conexión y las direcciones URL que las aplicaciones intentan alcanzar y los servicios que se proporcionan. Esta información es útil para solucionar problemas de configuración de red y configurar directivas para servidores proxy de red. Los detalles de este artículo tienen como objetivo complementar el [artículo Office 365 URL y los intervalos de direcciones](urls-and-ip-address-ranges.md), que incluye extremos para equipos que ejecutan Microsoft Windows. A menos que se indique lo contrario, la información de este artículo también se aplica a Office 2019 para Mac y Office 2016 para Mac, que están disponibles como una compra de pago único en una tienda minorista o a través de un contrato de licencia por volumen. 

  
La mayoría de este artículo son tablas que detallan las direcciones URL de red, el tipo y la descripción de servicio o la característica proporcionada por ese punto de conexión. Cada una de las aplicaciones de Office puede diferir en su servicio y uso de extremo. Las siguientes aplicaciones están definidas en las tablas siguientes:
  
- W: Word
- P: PowerPoint
- X: Excel
- O: Outlook
- N: OneNote
   
El tipo de dirección URL se define de la siguiente manera:
  
- ST: estática: la dirección URL está codificada de forma rígida en la aplicación cliente.
    
- SS: semi-estática-la dirección URL está codificada como parte de una página web o un Redirector.
    
- CS: servicio de configuración: la dirección URL se devuelve como parte del servicio de configuración de Office.

    
## <a name="office-for-mac-default-configuration"></a>Configuración predeterminada de Office para Mac

 **Instalación y actualizaciones**
  
Los siguientes puntos de conexión de red se usan para descargar el programa de instalación de Office para Mac de la red de entrega de contenido (CDN) de Microsoft.
  
|**URL**|**Tipo**|**Descripción**|
|:-----|:-----|:-----|
|```https://go.microsoft.com/fwlink/```  <br/> |Provincia  <br/> |Portal de instalación de Office 365 reenviar el servicio de vínculos hacia delante a los paquetes de instalación más recientes.  <br/> |
|```https://officecdn-microsoft-com.akamaized.net/```  <br/> |SS  <br/> |Ubicación de los paquetes de instalación en la red de entrega de contenido.  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |SS  <br/> |Ubicación de los paquetes de instalación en la red de entrega de contenido.  <br/> |
|```https://officeci-mauservice.azurewebsites.net/```  <br/> |Provincia  <br/> |Punto de conexión de control de administración para Microsoft AutoUpdate  <br/> |
   
 **Primer inicio de la aplicación**
  
Los siguientes puntos de conexión de red se contactan en el primer inicio de una aplicación de Office. Estos puntos de conexión proporcionan funciones de Office mejoradas para los usuarios y se Contacta con las direcciones URL independientemente del tipo de licencia (incluidas las instalaciones de licencias por volumen).
  
|**URL**|**Aplicaciones**|**Tipo**|**Descripción**|
|:-----|:-----|:-----|:-----|
|```https://config.edge.skype.com/```  <br/> |WXPON  <br/> |Provincia  <br/> |Configuración de "vuelo": permite una característica de luz encendida y experimentación.  <br/> |
|```https://ocos-office365-s2s.msedge.net/```  <br/> |WXPON  <br/> |Provincia  <br/> |Prueba de configuración de red de "vuelo"  <br/> |
|```https://client-office365-tas.msedge.net/```  <br/> |WXPON  <br/> |Provincia  <br/> |Prueba de configuración de red de "vuelo"  <br/> |
|```https://officeclient.microsoft.com/```  <br/> |WXPON  <br/> |Provincia  <br/> |Servicio de configuración de Office: lista maestra de puntos de conexión de servicio.  <br/> |
|```https://nexusrules.officeapps.live.com/```  <br/> |WXPON  <br/> |Provincia  <br/> |Descarga de telemetría de reglas de Office: informa al cliente sobre los datos y eventos que se deben cargar en el servicio de telemetría.  <br/> |
|```https://mobile.pipe.aria.microsoft.com/```  <br/> |N  <br/> |COMPLEJO  <br/> |Servicio de telemetría de OneNote  <br/> |
|```https://nexus.officeapps.live.com/```  <br/> |WXPON  <br/> |Provincia  <br/> |Informes de carga de telemetría de Office: "Heartbeart" y eventos de error que se producen en el cliente se cargan en el servicio de telemetría.  <br/> |
|```https://templateservice.office.com/```  <br/> |WXP  <br/> |COMPLEJO  <br/> |Servicio de plantillas de Office: proporciona a los usuarios plantillas de documento en línea.  <br/> |
|```https://omextemplates.content.office.net/```  <br/> |WXP  <br/> |COMPLEJO  <br/> |Descargas de plantillas de Office: almacenamiento de imágenes de plantillas PNG.  <br/> |
|```https://store.office.com/```  <br/> |WXP  <br/> |COMPLEJO  <br/> |Configuración de la tienda para las aplicaciones de Office.  <br/> |
|```https://odc.officeapps.live.com/```  <br/> |WXPN  <br/> |COMPLEJO  <br/> |Catálogo de servicios de integración de documentos de Office (lista de servicios y extremos) y detección del dominio de inicio.  <br/> |
|```https://cdn.odc.officeapps.live.com/```  <br/> |WXPON  <br/> |COMPLEJO  <br/> |Recursos para la detección de territorios domésticos V2 (15,40 y versiones posteriores)  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |WXPON  <br/> |Provincia  <br/> |Manifiestos de Microsoft AutoUpdate: comprobaciones para ver si hay actualizaciones disponibles  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |WXPO  <br/> |SS  <br/> |Biblioteca de JavaScript de Microsoft Ajax  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |M  <br/> |SS  <br/> |Configuración y recursos de la aplicación Wikipedia para Office.  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Aplicación de mapa de Bing para la configuración y los recursos de Office.  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Aplicación de gráfico People para la configuración y los recursos de Office.  <br/> |
|```https://www.onenote.com/```  <br/> |N  <br/> |Provincia  <br/> |Contenido nuevo de OneNote.  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |Provincia  <br/> |Contenido nuevo para OneNote.  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |SS  <br/> |Nuevas imágenes para OneNote.  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |Provincia  <br/> |Servicio de soporte técnico desde la aplicación.  <br/> |
|```https://prod-global-autodetect.acompli.net/```  <br/> |O  <br/> |Provincia  <br/> |Servicio de detección de cuentas de correo electrónico.  <br/> |
|```https://autodiscover-s.outlook.com/```  <br/> |WXPO  <br/> |Provincia  <br/> |Detección automática de Outlook  <br/> |
|```https://outlook.office365.com/```  <br/> |WXPO  <br/> |Provincia  <br/> |Extremo de Outlook para el servicio de Office 365.  <br/> |
|```https://r1.res.office365.com/```  <br/> |O  <br/> |Provincia  <br/> |Iconos para complementos de Outlook.  <br/> |
   
> [!NOTE]
> El servicio de configuración de Office actúa como un servicio de detección automática para todos los clientes de Microsoft Office, no solo para Mac. Los puntos de conexión devueltos en la respuesta son semi-estáticas en ese cambio es muy poco frecuente, pero aún es posible. 
  
 **Inicio de sesión**
  
Los siguientes puntos de conexión de red se contactan al iniciar sesión en el almacenamiento basado en la nube. Según el tipo de cuenta, puede ponerse en contacto con diferentes servicios. Por ejemplo:
  
- **MSA: cuenta Microsoft** -suele usarse para escenarios de cliente y de comercio minorista 
    
- **OrgID: cuenta** de la organización: normalmente usada para escenarios comerciales 
    
|**URL**|**Aplicaciones**|**Tipo**|**Descripción**|
|:-----|:-----|:-----|:-----|
|```https://login.windows.net/```  <br/> |WXPON  <br/> |Provincia  <br/> |Servicio de autorización de Windows  <br/> |
|```https://login.microsoftonline.com/```  <br/> |WXPON  <br/> |Provincia  <br/> |Servicio de inicio de sesión de Office 365 (OrgID)  <br/> |
|```https://login.live.com/```  <br/> |WXPON  <br/> |Provincia  <br/> |Servicio de inicio de sesión de la cuenta de Microsoft (MSA)  <br/> |
|```https://auth.gfx.ms/```  <br/> |WXPON  <br/> |COMPLEJO  <br/> |Ayudante del servicio de inicio de sesión de la cuenta de Microsoft (MSA)  <br/> |
|```https://secure.aadcdn.microsoftonline-p.com/```  <br/> |WXPON  <br/> |SS  <br/> |Office 365 de marca de inicio de sesión (OrgID)  <br/> |
|```https://ocws.officeapps.live.com/```  <br/> |WXPN  <br/> |COMPLEJO  <br/> |Documento y lugar donde se ubica el localizador de almacenamiento  <br/> |
|```https://roaming.officeapps.live.com/```  <br/> |WXPN  <br/> |COMPLEJO  <br/> |Servicio de documentos usados recientemente (MRU)  <br/> |
   
> [!NOTE]
> Para las licencias de minoristas y basadas en suscripciones, el inicio de sesión activa el producto y permite el acceso a los recursos en la nube, como OneDrive. Para instalaciones de licencias por volumen, se sigue solicitando a los usuarios que inicien sesión (de forma predeterminada), pero esto solo es necesario para obtener acceso a los recursos en la nube, ya que el producto ya está activado. 
  
 **Activación del producto**
  
Los siguientes puntos de conexión de red se aplican a las activaciones de suscripción de Office 365 y de licencia comercial. En concreto, esto no se aplica a las instalaciones de licencias por volumen.
  
|**URL**|**Aplicaciones**|**Tipo**|**Descripción**|
|:-----|:-----|:-----|:-----|
|```https://ols.officeapps.live.com/```  <br/> |WXPON  <br/> |COMPLEJO  <br/> |Servicio de licencias de Office  <br/> |
   
 **Contenido nuevo**
  
Los siguientes puntos de conexión de red se aplican solo a la suscripción de Office 365.
  
|**URL**|**Aplicaciones**|**Tipo**|**Descripción**|
|:-----|:-----|:-----|:-----|
|```https://contentstorage.osi.office.net/```  <br/> |WXPO  <br/> |SS  <br/> |Contenido de la página JSON nuevo.  <br/> |
   
 **Investigador**
  
Los siguientes puntos de conexión de red se aplican solo a la suscripción de Office 365.
  
|**URL**|**Aplicaciones**|**Tipo**|**Descripción**|
|:-----|:-----|:-----|:-----|
|```https://entity.osi.office.net/```  <br/> |M  <br/> |COMPLEJO  <br/> |Servicio Web del investigador  <br/> |
|```https://cdn.entity.osi.office.net/```  <br/> |M  <br/> |COMPLEJO  <br/> |Contenido estático del investigador  <br/> |
|```https://www.bing.com/```  <br/> |M  <br/> |COMPLEJO  <br/> |Proveedor de contenido del investigador  <br/> |
   
 **Búsqueda inteligente**
  
Los siguientes puntos de conexión de red se aplican tanto a la suscripción de Office 365 como a las activaciones de licencias por volumen o minorista.
  
|**URL**|**Aplicaciones**|**Tipo**|**Descripción**|
|:-----|:-----|:-----|:-----|
|```https://uci.officeapps.live.com/```  <br/> |WXPN  <br/> |COMPLEJO  <br/> |Servicio Web Insights  <br/> |
|```https://ajax.googleapis.com/```  <br/> |WXPN  <br/> |COMPLEJO  <br/> |Biblioteca de JQuery  <br/> |
|```https://cdnjs.cloudflare.com/```  <br/> |WXPN  <br/> |COMPLEJO  <br/> |Biblioteca de JavaScript compatible  <br/> |
|```https://www.bing.com/```  <br/> |WXPN  <br/> |COMPLEJO  <br/> |Proveedor de contenido de Insights  <br/> |
|```https://tse1.mm.bing.net/```  <br/> |WXPN  <br/> |COMPLEJO  <br/> |Proveedor de contenido de Insights  <br/> |
   
 **Diseñador de PowerPoint**
  
Los siguientes puntos de conexión de red se aplican solo a la suscripción de Office 365.
  
|**URL**|**Aplicaciones**|**Tipo**|**Descripción**|
|:-----|:-----|:-----|:-----|
|```https://pptsgs.officeapps.live.com/```  <br/> |P  <br/> |COMPLEJO  <br/> |Servicio Web de diseñador de PowerPoint  <br/> |
   
 **Inicio rápido de PowerPoint**
  
Los siguientes puntos de conexión de red se aplican solo a la suscripción de Office 365.
  
|**URL**|**Aplicaciones**|**Tipo**|**Descripción**|
|:-----|:-----|:-----|:-----|
|```https://pptcts.officeapps.live.com/```  <br/> |P  <br/> |COMPLEJO  <br/> |Servicio Web de inicio rápido de PowerPoint  <br/> |
   
 **Enviar una sonrisa o una enfadada**
  
Los siguientes puntos de conexión de red se aplican tanto a la suscripción de Office 365 como a las activaciones de licencias por volumen o minorista.
  
|**URL**|**Aplicaciones**|**Tipo**|**Descripción**|
|:-----|:-----|:-----|:-----|
|```https://sas.office.microsoft.com/```  <br/> |WXPON  <br/> |COMPLEJO  <br/> |Enviar un servicio de sonrisa  <br/> |
   
 **Póngase en contacto con soporte técnico**
  
Los siguientes puntos de conexión de red se aplican tanto a la suscripción de Office 365 como a las activaciones de licencias por volumen o minorista.
  
|**URL**|**Aplicaciones**|**Tipo**|**Descripción**|
|:-----|:-----|:-----|:-----|
|```https://powerlift-frontdesk.acompli.net/```  <br/> |O  <br/> |COMPLEJO  <br/> |Servicio de soporte técnico de contactos  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |COMPLEJO  <br/> |Servicio de soporte técnico desde la aplicación  <br/> |
   
 **Guardar como PDF**
  
Los siguientes puntos de conexión de red se aplican tanto a la suscripción de Office 365 como a las activaciones de licencias por volumen o minorista.
  
|**URL**|**Aplicaciones**|**Tipo**|**Descripción**|
|:-----|:-----|:-----|:-----|
|```https://wordcs.officeapps.live.com/```  <br/> |M  <br/> |COMPLEJO  <br/> |Servicio de conversión de documentos de Word (PDF)  <br/> |
   
 **Aplicaciones de Office (también conocidas como complementos)**
  
Los siguientes puntos de conexión de red se aplican a la suscripción de Office 365 y a las activaciones de licencias por volumen o minoristas cuando los complementos de aplicaciones de Office son de confianza.
  
|**URL**|**Aplicaciones**|**Tipo**|**Descripción**|
|:-----|:-----|:-----|:-----|
|```https://store.office.com/```  <br/> |WXPO  <br/> |COMPLEJO  <br/> |Configuración de la tienda de aplicaciones de Office  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |M  <br/> |SS  <br/> |Recursos de la aplicación Wikipedia  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Recursos de aplicaciones de mapas de Bing  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com```  <br/> |X  <br/> |SS  <br/> |Recursos de la aplicación gráfica de contactos  <br/> |
|```https://o15.officeredir.microsoft.com/```  <br/> |WPX  <br/> |SS  <br/> |Servicio de redirección de Office  <br/> |
|```https://appsforoffice.microsoft.com/```  <br/> |WXP  <br/> |SS  <br/> |Bibliotecas de JavaScript de Office  <br/> |
|```https://telemetry.firstpartyapps.oaspapps.com/```  <br/> |WX  <br/> |SS  <br/> |Telemetría y servicio de informes para las aplicaciones de Office  <br/> |
|```https://ajax.microsoft.com/```  <br/> |M  <br/> |SS  <br/> |Biblioteca de JavaScript de Microsoft Ajax  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |X  <br/> |SS  <br/> |Biblioteca de JavaScript de Microsoft Ajax  <br/> |
|```https://c.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Bibliotecas de JavaScript de Office  <br/> |
|```https://c1.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Recursos de soporte técnico  <br/> |
|```https://cs.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Recursos de soporte técnico  <br/> |
|```https://c.bing.com/```  <br/> |WPXO  <br/> |SS  <br/> |Recursos de soporte técnico  <br/> |
|```https://*.cdn.optimizely.com/```  <br/> |WPXO  <br/> |SS  <br/> |Biblioteca de JavaScript  <br/> |
|```https://errors.client.optimizely.com/```  <br/> |WPX  <br/> |SS  <br/> |Elaboración de informes de errores  <br/> |
|```https://*-contentstorage.osi.office.net/```  <br/> |WPXO  <br/> |SS  <br/> |Recursos de fuente  <br/> |
|```https://nexus.ensighten.com/```  <br/> |WPXO  <br/> |SS  <br/> |Servicio de telemetría  <br/> |
|```https://browser.pipe.aria.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Informes de telemetría  <br/> |
|```https://*.vo.msecnd.net/```  <br/> |WPXO  <br/> |SS  <br/> |Biblioteca de activos de Microsoft Store  <br/> |
|```https://*.wikipedia.org/```  <br/> |M  <br/> |SS  <br/> |Recursos de la página de Wikipedia  <br/> |
|```https://upload.wikimedia.org/```  <br/> |M  <br/> |SS  <br/> |Recursos de medios de Wikipedia  <br/> |
|```https://wikipedia.firstpartyappssandbox.oappseperate.com/```  <br/> |M  <br/> |SS  <br/> |Marco de espacio aislado de Wikipedia  <br/> |
|```https://*.virtualearth.net/```  <br/> |X  <br/> |SS  <br/> |Plantillas de mapa  <br/> |
   
 **Vínculos seguros**
  
El siguiente punto de conexión de red se aplica a todas las aplicaciones de Office para Office 365 solo suscripción.
  
|**URL**|**Tipo**|**Descripción**|
|:-----|:-----|:-----|
|```https://*.oscs.protection.outlook.com/```  <br/> |COMPLEJO  <br/> |Servicio de vínculo seguro de Microsoft  <br/> |
   
 **Informes de bloqueo**
  
El siguiente punto de conexión de red se aplica a todas las aplicaciones de Office para la suscripción de Office 365 y las activaciones de licencias por volumen o minorista. Cuando un proceso se bloquea inesperadamente, se genera un informe y se envía al servicio Watson.
  
|**URL**|**Tipo**|**Descripción**|
|:-----|:-----|:-----|
|```https://watson.microsoft.com/```  <br/> |Provincia  <br/> |Servicio de informe de errores de Microsoft  <br/> |
|```https://officeci.azurewebsites.net/```  <br/> |Provincia  <br/> |Servicio de Office Collaborative Insights  <br/> |
   
## <a name="options-for-reducing-network-requests-and-traffic"></a>Opciones para reducir las solicitudes de red y el tráfico

La configuración predeterminada de Office para Mac proporciona la mejor experiencia de usuario, tanto en términos de funcionalidad como de mantener el equipo al día. En algunos escenarios, es posible que desee impedir que las aplicaciones se pongan en contacto con los extremos de la red. En esta sección se describen las opciones para hacerlo.
  
 ### <a name="disabling-cloud-sign-in-and-office-add-ins"></a>Deshabilitar el inicio de sesión en la nube y complementos de Office
  
Los clientes de licencias por volumen pueden tener directivas estrictas sobre cómo guardar documentos en el almacenamiento basado en la nube. Se puede configurar la siguiente preferencia por aplicación para deshabilitar el inicio de sesión de MSA/OrgID y acceder a los complementos de Office.
  
- ```defaults write com.microsoft.Word UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Excel UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Powerpoint UseOnlineContent -integer 0```

Si los usuarios intentan tener acceso a la función de inicio de sesión, verán un error que le impedirá que una conexión de red no esté presente. Como esta preferencia también bloquea la activación de productos en línea, solo debe usarse para instalaciones de licencias por volumen. Concretamente, el uso de esta preferencia impedirá que las aplicaciones de Office accedan a los siguientes extremos:
  
- ```https://odc.officeapps.live.com```
    
- ```https://*.firstpartyapps.oaspapps.com```
    
- Todos los puntos de conexión que aparecen en la sección "iniciar sesión" anterior.
    
- Todos los puntos de conexión aparecen en la sección "búsqueda inteligente" anterior.
    
- Todos los puntos de conexión que aparecen en la sección "activación del producto" anterior.
    
- Todos los puntos de conexión que aparecen en la sección "aplicaciones de Office (aka Add-Ins)" anterior.
    
Para restablecer la funcionalidad completa del usuario, establezca la preferencia en "2" o quítela.
  
> [!NOTE]
> Esta preferencia requiere Office para Mac compilación 15,25 [160726] o posterior. 
  
### <a name="telemetry"></a>Telemetría
  
Office para Mac devuelve información de telemetría a Microsoft a intervalos regulares. Los datos se cargan en el punto de conexión de "Nexus". Los datos de telemetría ayudan al equipo de ingeniería a evaluar el estado y los comportamientos inesperados de cada aplicación de Office. Hay dos categorías de telemetría:
  
- El **latido** contiene información de versión y de licencia. Estos datos se envían inmediatamente al iniciar la aplicación. 
    
- **Uso** contiene información sobre cómo se usan las aplicaciones y los errores que no son irrecuperables. Estos datos se envían cada 60 minutos. 
    
Microsoft se toma muy en serio su privacidad. Puede obtener información sobre la Directiva de recopilación de datos [https://privacy.microsoft.com](https://privacy.microsoft.com)de Microsoft en. Para evitar que las aplicaciones envíen una telemetría de "uso", se puede ajustar la preferencia **SendAllTelemetryEnabled** . La preferencia es por aplicación y se puede establecer a través de perfiles de configuración de macOS o manualmente desde terminal: 
  
```defaults write com.microsoft.Word SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Excel SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Powerpoint SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Outlook SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.onenote.mac SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.autoupdate2 SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Office365ServiceV2 SendAllTelemetryEnabled -bool FALSE```

La telemetría de latidos siempre se envía y no se puede deshabilitar.
  
### <a name="crash-reporting"></a>Informes de bloqueo
  
Cuando se produce un error grave de la aplicación, la aplicación finalizará de forma inesperada y cargará un informe de bloqueo en el servicio "Watson". El informe de bloqueo consta de una pila de llamadas, que es la lista de pasos que el procesamiento de la aplicación inicializó hasta el bloqueo. Estos pasos ayudan al equipo de ingeniería a identificar la función exacta que produjo el error y por qué.
  
En algunos casos, el contenido de un documento hará que la aplicación se bloquee. Si la aplicación identifica el documento como la causa, le preguntará al usuario si es correcto enviar también el documento junto con la pila de llamadas. Los usuarios pueden tomar una decisión informada sobre esta pregunta. Los administradores de TI pueden tener requisitos estrictos sobre la transmisión de documentos y tomar la decisión en nombre del usuario para no enviar nunca documentos. La siguiente preferencia se puede establecer para evitar que se envíen los documentos y para suprimir el aviso al usuario:
  
```defaults write com.microsoft.errorreporting IsAttachFilesEnabled -bool FALSE```

> [!NOTE]
> Si **SendAllTelemetryEnabled** se establece en **false**, se deshabilitan todos los informes de bloqueo del proceso. Para habilitar el informe de errores sin enviar la telemetría de uso, se puede establecer la siguiente preferencia:```defaults write com.microsoft.errorreporting IsMerpEnabled -bool TRUE``` 
  
### <a name="updates"></a>Actualizaciones
  
Microsoft publica actualizaciones de Office para Mac a intervalos regulares (normalmente una vez al mes). Recomendamos encarecidamente a los usuarios y a los administradores de ti mantener los equipos actualizados para asegurarse de que se instalan las revisiones de seguridad más recientes. En los casos donde los administradores de ti quieren controlar y administrar las actualizaciones de los equipos, se puede configurar la siguiente preferencia para evitar que el proceso de actualización automática detecte y ofrezca actualizaciones de productos automáticamente:
  
```defaults write com.microsoft.autoupdate2 HowToCheck -string 'Manual'```

### <a name="blocking-requests-with-a-firewallproxy"></a>Bloqueo de solicitudes con un firewall o proxy
  
Si su organización bloquea solicitudes a direcciones URL a través de un firewall o un servidor proxy, asegúrese de configurar las direcciones URL que aparecen en este documento como permitidas o como bloques enumerados con una respuesta 40X (por ejemplo, 403 o 404). Una respuesta de 40X permitirá a las aplicaciones de Office aceptar correctamente la incapacidad para obtener acceso al recurso y proporcionar una experiencia de usuario más rápida que simplemente quitar la conexión, lo que, a su vez, hará que el cliente vuelva a intentarlo.
  
Si el servidor proxy requiere autenticación, se devolverá una respuesta 407 al cliente. Para obtener la mejor experiencia, asegúrese de que está usando las compilaciones de Office para Mac 15,27 o versiones posteriores, ya que incluyen revisiones específicas para trabajar con servidores NTLM y Kerberos.
  
  
## <a name="see-also"></a>Vea también

[Intervalos de direcciones IP y URL de Office 365](urls-and-ip-address-ranges.md)

