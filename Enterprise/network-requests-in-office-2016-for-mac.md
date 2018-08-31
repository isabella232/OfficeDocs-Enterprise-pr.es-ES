---
title: Solicitudes de red en Office 2016 para Mac
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 8/13/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365_Setup
search.appverid: MOM160
ms.assetid: afdae969-4046-44b9-9adb-f1bab216414b
description: 2016 de Office para las aplicaciones de Mac proporcionan una experiencia de aplicación nativa en la plataforma de Mac OS. Cada aplicación está diseñado para funcionar en una variedad de escenarios, incluidos los Estados cuando no hay acceso a la red está disponible. Cuando un equipo está conectado a una red, las aplicaciones se conectan automáticamente a una serie de servicios basados en web para proporcionar funcionalidad mejorada. Este documento describe qué extremos y direcciones URL de las aplicaciones de intentan ponerse en contacto con y los servicios proporcionados. Esta información es útil cuando la solución de problemas de red problemas de configuración y configurar una directiva para los servidores proxy de red. Los detalles de este artículo están diseñados para complementar el artículo de intervalos de direcciones y direcciones URL en Office 365.
ms.openlocfilehash: b94b77a0ff8cd37b0fa1c881ba590853615bfe93
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542955"
---
# <a name="network-requests-in-office-2016-for-mac"></a>Solicitudes de red en Office 2016 para Mac

2016 de Office para las aplicaciones de Mac proporcionan una experiencia de aplicación nativa en la plataforma de Mac OS. Cada aplicación está diseñado para funcionar en una variedad de escenarios, incluidos los Estados cuando no hay acceso a la red está disponible. Cuando un equipo está conectado a una red, las aplicaciones se conectan automáticamente a una serie de servicios basados en web para proporcionar funcionalidad mejorada. Este documento describe qué extremos y direcciones URL de las aplicaciones de intentan ponerse en contacto con y los servicios proporcionados. Esta información es útil para solucionar problemas de configuración de red y las directivas de configuración para los servidores proxy de red. Los detalles de este artículo están diseñados para complementar el [artículo de intervalos de direcciones URL en Office 365 y la dirección](urls-and-ip-address-ranges.md), que incluye los extremos para los equipos que ejecutan Microsoft Windows.
  
La mayor parte de este artículo es tablas que se detallan las direcciones URL de red, el tipo y la descripción de servicio o característica proporcionada por dicho extremo. Cada una de las aplicaciones de Office puede diferir en su uso del servicio y de extremo. Las aplicaciones siguientes se definen en las tablas siguientes:
  
- Anchura: Word
- P: PowerPoint
- X: Excel
- O: outlook
- N: OneNote
   
El tipo de dirección URL se define como sigue:
  
- ST: Es la dirección URL de estático - codificado de forma rígida en la aplicación cliente.
    
- SS: Static delimitadas-la dirección URL se codifica como parte de una página web o redirector.
    
- CS: Config Service - la dirección URL se devuelve como parte del servicio de configuración de Office.
    
## <a name="office-2016-for-mac-default-configuration"></a>2016 de Office para la configuración predeterminada de Mac

 **Instalación y actualizaciones**
  
Los extremos de red siguientes se utilizan para descargar el 2016 de Office para el programa de instalación de Mac desde la red de entrega de contenido (CDN) de Microsoft.
  
|**URL**|**Tipo**|**Descripción**|
|:-----|:-----|:-----|
|```https://go.microsoft.com/fwlink/```  <br/> |ST  <br/> |Servicio de vínculo hacia delante de Portal de instalación de Office 365 a los paquetes de instalación más recientes.  <br/> |
|```https://officecdn-microsoft-com.akamaized.net/```  <br/> |SS  <br/> |Ubicación de los paquetes de instalación en la red de entrega de contenido.  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |SS  <br/> |Ubicación de los paquetes de instalación en la red de entrega de contenido.  <br/> |
|```https://officeci-mauservice.azurewebsites.net/```  <br/> |ST  <br/> |Extremo de Control de administración para Microsoft AutoUpdate  <br/> |
   
 **Primer inicio de aplicación**
  
Los extremos de red siguientes se ponen en contacto en primer inicio de una aplicación de Office. Estos extremos proporcionan funcionalidad de Office mejorada para los usuarios y las direcciones URL se ponen en contacto independientemente del tipo de licencia (incluidas las instalaciones de licencia por volumen).
  
|**URL**|**Aplicaciones**|**Tipo**|**Descripción**|
|:-----|:-----|:-----|:-----|
|```https://config.edge.skype.com/```  <br/> |WXPON  <br/> |ST  <br/> |Configuración 'Flighting' - permite la característica de seguridad de luz y experimentación.  <br/> |
|```https://ocos-office365-s2s.msedge.net/```  <br/> |WXPON  <br/> |ST  <br/> |Prueba de configuración de red 'Flighting'  <br/> |
|```https://client-office365-tas.msedge.net/```  <br/> |WXPON  <br/> |ST  <br/> |Prueba de configuración de red 'Flighting'  <br/> |
|```https://officeclient.microsoft.com/```  <br/> |WXPON  <br/> |ST  <br/> |Servicio de configuración de Office - Master lista de extremos de servicio.  <br/> |
|```https://nexusrules.officeapps.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Descarga de telemetría de reglas de Office - informa al cliente acerca de qué datos y eventos para cargar en el servicio de telemetría.  <br/> |
|```https://mobile.pipe.aria.microsoft.com/```  <br/> |N  <br/> |CS  <br/> |Servicio de telemetría de OneNote  <br/> |
|```https://nexus.officeapps.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Telemetría de Office cargar informes - "Heartbeart" y los eventos de error que se producen en el cliente se cargan en el servicio de telemetría.  <br/> |
|```https://templateservice.office.com/```  <br/> |WXP  <br/> |CS  <br/> |Servicio de plantilla de Office Online - proporciona a los usuarios con las plantillas de documento en línea.  <br/> |
|```https://omextemplates.content.office.net/```  <br/> |WXP  <br/> |CS  <br/> |Descargas de plantillas de Office - almacenamiento de imágenes PNG de plantilla.  <br/> |
|```https://store.office.com/```  <br/> |WXP  <br/> |CS  <br/> |Configuración de almacenamiento para las aplicaciones de Office.  <br/> |
|```https://odc.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Catálogo de servicios de integración de documento de Office (lista de servicios y los extremos) y detección de dominio Kerberos principal.  <br/> |
|```https://cdn.odc.officeapps.live.com/```  <br/> |WXPON  <br/> |CS  <br/> |Recursos para la detección del territorio Home v2 (15.40 y versiones posteriores)  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |WXPON  <br/> |ST  <br/> |Microsoft AutoUpdate manifiestos - comprobaciones para ver si hay actualizaciones disponibles  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |WXPO  <br/> |SS  <br/> |Biblioteca de JavaScript de Ajax de Microsoft  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |W  <br/> |SS  <br/> |Aplicación de Wikipedia para configuración de Office y los recursos.  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Aplicación de mapa de Bing para la configuración de Office y recursos.  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Aplicación de gráfico de personas para la configuración de Office y recursos.  <br/> |
|```https://www.onenote.com/```  <br/> |N  <br/> |ST  <br/> |¿Qué es el nuevo contenido de OneNote.  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |ST  <br/> |Nuevo contenido de OneNote.  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |SS  <br/> |¿Qué es nuevas imágenes de OneNote.  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |ST  <br/> |Servicio de soporte técnico de la aplicación.  <br/> |
|```https://prod-global-autodetect.acompli.net/```  <br/> |O  <br/> |ST  <br/> |Servicio de detección de la cuenta de correo electrónico.  <br/> |
|```https://autodiscover-s.outlook.com/```  <br/> |WXPO  <br/> |ST  <br/> |Detección automática de Outlook  <br/> |
|```https://outlook.office365.com/```  <br/> |WXPO  <br/> |ST  <br/> |Extremo de Outlook para el servicio de Office 365.  <br/> |
|```https://r1.res.office365.com/```  <br/> |O  <br/> |ST  <br/> |Iconos de complementos de Outlook.  <br/> |
   
> [!NOTE]
> El servicio de configuración de Office actúa como un servicio de detección automática para todos los clientes de Microsoft Office, no sólo para Mac. Los extremos devueltos en la respuesta son parcialmente estáticos en que el cambio es muy poco frecuentes, pero aún posibles. 
  
 **Inicio de sesión**
  
Los extremos de red siguientes se ponen en contacto al iniciar la sesión al almacenamiento de información basada en la nube. Según el tipo de cuenta, se pueden establecer contacto con distintos servicios. Por ejemplo:
  
- **MSA: Account Microsoft** : se usan normalmente para escenarios de consumidor y venta por menor 
    
- **OrgID: cuenta de organización** : se usan normalmente para escenarios comerciales 
    
|**URL**|**Aplicaciones**|**Tipo**|**Descripción**|
|:-----|:-----|:-----|:-----|
|```https://login.windows.net/```  <br/> |WXPON  <br/> |ST  <br/> |Servicio de autorización de Windows  <br/> |
|```https://login.microsoftonline.com/```  <br/> |WXPON  <br/> |ST  <br/> |Servicio de inicio de sesión de Office 365 (OrgID)  <br/> |
|```https://login.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Servicio de inicio de sesión de cuenta de Microsoft (MSA)  <br/> |
|```https://auth.gfx.ms/```  <br/> |WXPON  <br/> |CS  <br/> |Ayudante de servicio de inicio de sesión de cuenta de Microsoft (MSA)  <br/> |
|```https://secure.aadcdn.microsoftonline-p.com/```  <br/> |WXPON  <br/> |SS  <br/> |Personalización de marca (OrgID) de inicio de sesión de Office 365  <br/> |
|```https://ocws.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Documento y lugares localizador de almacenamiento de información  <br/> |
|```https://roaming.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Servicio de documentos usados recientemente (MRU) mayoría  <br/> |
   
> [!NOTE]
> Para las licencias de suscripción-based y por menor, iniciar sesión en ambos activa el producto y permite el acceso a recursos de la nube, como OneDrive. Para las instalaciones de licencia por volumen, se sigue pide a los usuarios iniciar sesión (de forma predeterminada), pero que sólo es necesario para el acceso a los recursos de la nube, como el producto ya está activado. 
  
 **Activación de productos**
  
Los extremos de red siguientes se aplican a las activaciones de suscripción de Office 365 y licencia de venta por menor. En concreto, esto no se aplica a las instalaciones de licencia por volumen.
  
|**URL**|**Aplicaciones**|**Tipo**|**Descripción**|
|:-----|:-----|:-----|:-----|
|```https://ols.officeapps.live.com/```  <br/> |WXPON  <br/> |CS  <br/> |Servicio de licencias de Office  <br/> |
   
 **¿Qué es nuevo contenido**
  
Los extremos de red siguientes sólo se aplican a la suscripción de Office 365.
  
|**URL**|**Aplicaciones**|**Tipo**|**Descripción**|
|:-----|:-----|:-----|:-----|
|```https://contentstorage.osi.office.net/```  <br/> |WXPO  <br/> |SS  <br/> |¿Qué es el contenido de la página nueva JSON.  <br/> |
   
 **Investigador**
  
Los extremos de red siguientes se aplican a ambos suscripción de Office 365.
  
|**URL**|**Aplicaciones**|**Tipo**|**Descripción**|
|:-----|:-----|:-----|:-----|
|```https://entity.osi.office.net/```  <br/> |W  <br/> |CS  <br/> |Servicio Web de entrevistador  <br/> |
|```https://cdn.entity.osi.office.net/```  <br/> |W  <br/> |CS  <br/> |Contenido estático entrevistador  <br/> |
|```https://www.bing.com/```  <br/> |W  <br/> |CS  <br/> |Proveedor de contenido de entrevistador  <br/> |
   
 **Búsqueda inteligente**
  
Los extremos de red siguientes se aplican a las activaciones de suscripción de Office 365 y licencia de venta por menor o volumen.
  
|**URL**|**Aplicaciones**|**Tipo**|**Descripción**|
|:-----|:-----|:-----|:-----|
|```https://uci.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Servicio Web de conocimientos  <br/> |
|```https://ajax.googleapis.com/```  <br/> |WXPN  <br/> |CS  <br/> |Biblioteca de JQuery  <br/> |
|```https://cdnjs.cloudflare.com/```  <br/> |WXPN  <br/> |CS  <br/> |Compatibilidad con la biblioteca de JavaScript  <br/> |
|```https://www.bing.com/```  <br/> |WXPN  <br/> |CS  <br/> |Proveedor de contenido de conocimientos  <br/> |
|```https://tse1.mm.bing.net/```  <br/> |WXPN  <br/> |CS  <br/> |Proveedor de contenido de conocimientos  <br/> |
   
 **Diseñador de PowerPoint**
  
Los extremos de red siguientes sólo se aplican a la suscripción de Office 365.
  
|**URL**|**Aplicaciones**|**Tipo**|**Descripción**|
|:-----|:-----|:-----|:-----|
|```https://pptsgs.officeapps.live.com/```  <br/> |P  <br/> |CS  <br/> |Servicio web de diseñador de PowerPoint  <br/> |
   
 **Inicio rápido de PowerPoint**
  
Los extremos de red siguientes sólo se aplican a la suscripción de Office 365.
  
|**URL**|**Aplicaciones**|**Tipo**|**Descripción**|
|:-----|:-----|:-----|:-----|
|```https://pptcts.officeapps.live.com/```  <br/> |P  <br/> |CS  <br/> |Servicio web de QuickStarter de PowerPoint  <br/> |
   
 **Enviar sonrisa/gusta nada**
  
Los extremos de red siguientes se aplican a las activaciones de suscripción de Office 365 y licencia de venta por menor o volumen.
  
|**URL**|**Aplicaciones**|**Tipo**|**Descripción**|
|:-----|:-----|:-----|:-----|
|```https://sas.office.microsoft.com/```  <br/> |WXPON  <br/> |CS  <br/> |Enviar un servicio sonrisa  <br/> |
   
 **Ponte en contacto con soporte técnico**
  
Los extremos de red siguientes se aplican a las activaciones de suscripción de Office 365 y licencia de venta por menor o volumen.
  
|**URL**|**Aplicaciones**|**Tipo**|**Descripción**|
|:-----|:-----|:-----|:-----|
|```https://powerlift-frontdesk.acompli.net/```  <br/> |O  <br/> |CS  <br/> |Póngase en contacto con el servicio de soporte  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |CS  <br/> |Servicio de soporte de aplicación  <br/> |
   
 **Guardar como PDF**
  
Los extremos de red siguientes se aplican a las activaciones de suscripción de Office 365 y licencia de venta por menor o volumen.
  
|**URL**|**Aplicaciones**|**Tipo**|**Descripción**|
|:-----|:-----|:-----|:-----|
|```https://wordcs.officeapps.live.com/```  <br/> |W  <br/> |CS  <br/> |Servicio de conversión de documentos de Word (PDF)  <br/> |
   
 **Office Apps (también conocido como complementos)**
  
Los extremos de red siguientes se aplican a las activaciones de suscripción de Office 365 y licencia de venta por menor o volumen cuando los complementos de la aplicación de Office son de confianza.
  
|**URL**|**Aplicaciones**|**Tipo**|**Descripción**|
|:-----|:-----|:-----|:-----|
|```https://store.office.com/```  <br/> |WXPO  <br/> |CS  <br/> |Configuración de almacén de aplicaciones de Office  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |W  <br/> |SS  <br/> |Recursos de aplicación Wikipedia  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Recursos de la aplicación de mapa de Bing  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com```  <br/> |X  <br/> |SS  <br/> |Recursos de la aplicación de gráfico de personas  <br/> |
|```https://o15.officeredir.microsoft.com/```  <br/> |WPX  <br/> |SS  <br/> |Servicio de redirección de Office  <br/> |
|```https://appsforoffice.microsoft.com/```  <br/> |WXP  <br/> |SS  <br/> |Bibliotecas de JavaScript de Office  <br/> |
|```https://telemetry.firstpartyapps.oaspapps.com/```  <br/> |WX  <br/> |SS  <br/> |Telemetría y servicio de informes para las aplicaciones de Office  <br/> |
|```https://ajax.microsoft.com/```  <br/> |W  <br/> |SS  <br/> |Biblioteca de JavaScript de Ajax de Microsoft  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |X  <br/> |SS  <br/> |Biblioteca de JavaScript de Ajax de Microsoft  <br/> |
|```https://c.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Bibliotecas de JavaScript de Office  <br/> |
|```https://c1.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Recursos de soporte técnico  <br/> |
|```https://cs.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Recursos de soporte técnico  <br/> |
|```https://c.bing.com/```  <br/> |WPXO  <br/> |SS  <br/> |Recursos de soporte técnico  <br/> |
|```https://*.cdn.optimizely.com/```  <br/> |WPXO  <br/> |SS  <br/> |Biblioteca de JavaScript  <br/> |
|```https://errors.client.optimizely.com/```  <br/> |WPX  <br/> |SS  <br/> |Informes de errores  <br/> |
|```https://*-contentstorage.osi.office.net/```  <br/> |WPXO  <br/> |SS  <br/> |Recursos de fuente  <br/> |
|```https://nexus.ensighten.com/```  <br/> |WPXO  <br/> |SS  <br/> |Servicio de telemetría  <br/> |
|```https://browser.pipe.aria.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Informes de telemetría  <br/> |
|```https://*.vo.msecnd.net/```  <br/> |WPXO  <br/> |SS  <br/> |Biblioteca de activos de almacenamiento de Microsoft  <br/> |
|```https://*.wikipedia.org/```  <br/> |W  <br/> |SS  <br/> |Recursos de la página de Wikipedia  <br/> |
|```https://upload.wikimedia.org/```  <br/> |W  <br/> |SS  <br/> |Recursos de medios de Wikipedia  <br/> |
|```https://wikipedia.firstpartyappssandbox.oappseperate.com/```  <br/> |W  <br/> |SS  <br/> |Marco de espacio aislado de Wikipedia  <br/> |
|```https://*.virtualearth.net/```  <br/> |X  <br/> |SS  <br/> |Plantillas de mapa  <br/> |
   
 **Vínculos seguros**
  
El extremo de red siguientes se aplica a las aplicaciones de Office 2016.
  
|**URL**|**Tipo**|**Descripción**|
|:-----|:-----|:-----|
|```https://*.oscs.protection.outlook.com/```  <br/> |CS  <br/> |Servicio de vínculo de seguridad de Microsoft  <br/> |
   
 **Bloqueo de creación de informes**
  
El extremo de red siguientes se aplica a todas las aplicaciones de Office 2016 y tipos de licencia. Cuando un proceso se bloquea inesperadamente, se genera un informe y se envía al servicio de Watson.
  
|**URL**|**Tipo**|**Descripción**|
|:-----|:-----|:-----|
|```https://watson.microsoft.com/```  <br/> |ST  <br/> |Servicio informe de errores de Microsoft  <br/> |
|```https://officeci.azurewebsites.net/```  <br/> |ST  <br/> |Servicio de perspectivas de colaboración de Office  <br/> |
   
## <a name="options-for-reducing-network-requests-and-traffic"></a>Opciones para reducir el tráfico y las solicitudes de red

La configuración predeterminada de 2016 de Office para Mac proporciona la mejor experiencia de usuario, tanto en términos de funcionalidad y mantener el equipo actualizado. En algunos casos, es posible que desee evitar que las aplicaciones ponerse en contacto con extremos de la red. En esta sección se describe las opciones para hacerlo.
  
 ### <a name="disabling-cloud-sign-in-and-office-add-ins"></a>Deshabilitar complementos de inicio de sesión en la nube y Office
  
Los clientes de licencias por volumen pueden tener directivas estrictas sobre cómo guardar documentos en almacenamiento de información basada en la nube. Para deshabilitar MSA/OrgID para iniciar sesión y tener acceso a los complementos de Office, se puede establecer la siguiente preferencia por aplicación.
  
- ```defaults write com.microsoft.Word UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Excel UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Powerpoint UseOnlineContent -integer 0```

Si los usuarios intentan tener acceso a la función de inicio de sesión, verán un error que una conexión de red no está presente. Debido a que esta preferencia también bloquea la activación del producto en línea, sólo debe usarse para las instalaciones de licencia por volumen. En concreto, utiliza esta preferencia impedirá que las aplicaciones de Office pueda tener acceso a los siguientes extremos:
  
- ```https://odc.officeapps.live.com```
    
- ```https://*.firstpartyapps.oaspapps.com```
    
- Todos los extremos que aparecen en la sección 'Iniciar sesión' anterior.
    
- Todos los extremos enumerados en la sección 'Búsqueda inteligente' anterior.
    
- Todos los extremos que aparecen en la sección de activación del producto anterior.
    
- Todos los extremos enumerados en la sección 'Aplicaciones de Office (también conocido como complementos)' anterior.
    
Para volver a establecer la funcionalidad completa para el usuario, establezca la preferencia a '2' o quitarlo.
  
> [!NOTE]
> Esta preferencia requiere 2016 de Office para Mac compilación 15.25 [160726] o posterior. 
  
### <a name="telemetry"></a>Telemetría
  
2016 de Office para Mac envía información de telemetría a Microsoft a intervalos regulares. Datos se cargan en el extremo de 'Nexo'. Los datos de telemetría ayuda al equipo de ingeniería a evaluar el estado y los comportamientos inesperados de cada aplicación de Office. Existen dos categorías de telemetría:
  
- **Latido** contiene información de versión y licencia. Estos datos se envían inmediatamente tras el inicio de la aplicación. 
    
- **Uso** contiene información acerca de cómo se usan las aplicaciones y los errores que no sean irrecuperables. Estos datos se envían cada 60 minutos. 
    
Microsoft toma muy en serio su privacidad. Puede leer acerca de la directiva de colección de datos de Microsoft en [https://privacy.microsoft.com](https://privacy.microsoft.com). Para evitar que las aplicaciones de envío de telemetría 'Uso', se puede ajustar la preferencia de **SendAllTelemetryEnabled** . La preferencia es por aplicación y se puede establecer a través de los perfiles de configuración de Mac OS, o manualmente desde Terminal: 
  
```defaults write com.microsoft.Word SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Excel SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Powerpoint SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Outlook SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.onenote.mac SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.autoupdate2 SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Office365ServiceV2 SendAllTelemetryEnabled -bool FALSE```

Telemetría Heartbeat siempre se envía y no se puede deshabilitar.
  
### <a name="crash-reporting"></a>Bloqueo de creación de informes
  
Cuando se produce un error grave de aplicación, la aplicación inesperadamente terminar y cargar un informe de bloqueo para el servicio 'Watson'. El informe de errores de bloqueo consta de una pila de llamadas, que es la lista de los pasos que estaba procesando la aplicación lleva el bloqueo. Estos pasos ayudan a que el equipo de ingeniería identificar la función exacta que no se pudo y por qué.
  
En algunos casos, el contenido de un documento hará que la aplicación se bloquee. Si la aplicación identifica el documento como la causa, le pedirá al usuario si es correcto también enviar el documento junto con la pila de llamadas. Los usuarios pueden tomar una decisión documentada a esta pregunta. Los administradores de TI pueden tener requisitos estrictos acerca de la transmisión de documentos y tomar la decisión en nombre del usuario para no enviar nunca documentos. Para evitar que los documentos que se envían y para suprimir la pregunta al usuario, se puede establecer la siguiente preferencia:
  
```defaults write com.microsoft.errorreporting IsAttachFilesEnabled -bool FALSE```

> [!NOTE]
> Si **SendAllTelemetryEnabled** se establece en **FALSE**, todos los bloqueos informes para que el proceso está deshabilitado. Para habilitar el informe de errores de bloqueo sin enviar telemetría de uso, se puede establecer la siguiente preferencia:```defaults write com.microsoft.errorreporting IsMerpEnabled -bool TRUE``` 
  
### <a name="updates"></a>Actualizaciones
  
Microsoft publica 2016 de Office para actualizaciones de Mac a intervalos regulares (normalmente, una vez al mes). Recomendamos encarecidamente a los usuarios y se instalan los administradores de TI a mantener los equipos actualizados para asegurarse de las correcciones de seguridad más recientes. En los casos donde los administradores de TI desean controlar estrechamente y administrar las actualizaciones de la máquina, se puede establecer la siguiente preferencia para evitar que el proceso de actualización automática de detección automática y que ofrece las actualizaciones del producto:
  
```defaults write com.microsoft.autoupdate2 HowToCheck -string 'Manual'```

### <a name="blocking-requests-with-a-firewallproxy"></a>Bloqueo de las solicitudes con un Proxy de servidor de seguridad
  
Si solicita los bloques de la organización a las direcciones URL a través de un firewall o el servidor proxy no olvide configurar las direcciones URL que aparecen en este documento como permitido, o bloquear incluidos con una respuesta de X 40 (por ejemplo, 403 o 404). Una respuesta X 40 va a permitir que las aplicaciones de Office Aceptar correctamente la imposibilidad de tener acceso al recurso y proporcionará una experiencia de usuario más rápida, que simplemente eliminarla de la conexión, lo que a su vez hará que el cliente para volver a intentar.
  
Si el servidor proxy requiere autenticación, se devolverá una respuesta 407 al cliente. Para la mejor experiencia, asegúrese de que está usando Office 2016 compilaciones 15.27 o posteriores, ya que incluyen correcciones específicas para trabajar con servidores de NTLM y Kerberos.
  
  
## <a name="see-also"></a>Vea también

[Direcciones URL e intervalos de direcciones IP de Office 365](urls-and-ip-address-ranges.md)

