---
title: Diagrama accesible Integración de redes de productos de servidores de Microsoft Office
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 89f564eb-95c3-4077-bb92-75bf71b51270
f1.keywords:
- NOCSH
description: Este artículo es una versión de texto accesible del diagrama con el nombre Integración de red de los productos de servidor de Microsoft Office.
ms.openlocfilehash: def94a4523ad78676d6a9532a60dcba78032f23b
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843871"
---
# <a name="accessible-diagram---network-integration-of-microsoft-office-server-products"></a>Diagrama accesible: Integración de redes de productos de servidores de Microsoft Office

**Resumen:** este artículo es una versión de texto accesible del diagrama “Integración de red de los productos de servidor de Microsoft Office”.
  
En este póster se describe de manera general un entorno de red que incluye Lync Server 2013, SharePoint 2013 y Exchange Server 2013. También se muestran los siguientes elementos de red comunes a dichos productos: acceso remoto e interno, autenticación, tráfico de cliente y enrutamiento de tráfico a través de dispositivos compartidos. 
  
## <a name="high-level-concepts-for-lync-exchange-sharepoint-server-and-office-web-apps"></a>Conceptos de alto nivel para Lync, Exchange, SharePoint Server y Office Web Apps

### <a name="about-the-design"></a>Acerca del diseño

#### <a name="streamlined-network-design"></a>Diseño de red simplificado

Esta topología ilustra una implementación de la red local de SharePoint 2013, Exchange Server 2013 y Lync Server 2013. También muestra el uso del servicio basado en la nube de Microsoft, Exchange Online Protection, que proporciona protección contra correo no deseado y malware para el tráfico entrante del Protocolo simple de transferencia de correo (SMTP) de Internet. 
  
El diseño de esta red se simplificó a un conjunto mínimo de características de red y no incluye características adicionales de seguridad o infraestructura que algunas organizaciones podrían requerir. 
  
Este diagrama: 
  
- Proporciona un ejemplo de topología de red que ilustra el tráfico entrante y saliente a través de un enrutador de puerta de enlace y el equilibrio de carga del tráfico (externo e interno) de sesiones de cliente a los niveles de servidor de SharePoint, Exchange y Lync adecuados. 
    
- Muestra el uso de servidores de acceso remoto opcionales, como una puerta de enlace VPN de terceros o un servidor de DirectAccess, para proporcionar comunicación segura para los empleados con movilidad o remotos. 
    
- Describe el flujo de tráfico de Lync, Exchange y SharePoint desde el cliente a cada nivel de servidor de plataforma. 
    
- Identifica el tipo de conexión de acceso remoto o interno basado en el cliente (asociado o empleado, por ejemplo) y el método de autenticación usado. 
    
- Divide las plataformas SharePoint, Exchange y Lync según los roles de servidor necesarios, identificando el front-end, la aplicación, la base de datos y otros niveles. 
    
La arquitectura que se usa aquí para Lync, SharePoint y Exchange no sugiere una forma de implementación preferente de estas plataformas. Únicamente es un ejemplo, dado que las topologías varían en función de consideraciones de seguridad y requisitos de red específicos. 
  
#### <a name="gateway-router"></a>Enrutador de puerta de enlace

Para esta topología, el enrutador de la puerta de enlace se encuentra en el perímetro de la red y enruta todo el tráfico entrante y saliente hacia y desde la intranet. Como alternativa, también puede haber otros componentes que eliminen la brecha entre el enrutador de la puerta de enlace y el equilibrador de carga que se muestra, por ejemplo, varias capas de firewall. Esta topología representa solo una manera entre muchas de implementar la red. En esta configuración, la puerta de enlace se configuró con listas de control de acceso (ACL) para permitir tráfico entrante y saliente muy específico y basado en IP en las interfaces del enrutador. También se puede ejecutar ACL, inspecciones avanzadas o traducción de direcciones de red (NAT) en otros dispositivos, como los firewall, en la red. 
  
#### <a name="load-balancer-and-reverse-proxy-devices"></a>Equilibrador de carga y dispositivos de proxy inverso

Puede usar soluciones de equilibrio de carga de hardware o software para redirigir el tráfico de segmentos, incluidos servidores front-end web de SharePoint y servidores de acceso de cliente de Exchange (CAS). En algunos casos, lo ideal es usar un equilibrador de carga basado en hardware de nivel 7 para los requisitos de persistencia ya que puede funcionar mejor gracias a que usa información, como cookies o encabezados, en la solicitud. Sin embargo, factores como el costo y un uso y cargas de trabajo mayores de este tipo de solución podrían no ser convenientes para sus necesidades específicas. Tenga en cuenta los siguientes aspectos sobre el equilibrio de carga entre SharePoint, Exchange y Lync: 
  
- SharePoint: para SharePoint 2013, no es necesario habilitar la afinidad de los servidores front-end web. Normalmente, esta se usa para el mantenimiento de sesiones y para evitar varias solicitudes de autenticación de los clientes a cada servidor web front-end. El nuevo servicio de caché distribuida en SharePoint 2013 almacena y distribuye los tokens de inicio de sesión en los servidores web de la granja de servidores de SharePoint. 
    
- Exchange: en Exchange 2013, la función de CAS está diseñada para usar el equilibrio de carga de nivel 4, que distribuye las solicitudes a la capa de transporte. Esto puede reducir considerablemente el uso del equilibrador de carga y la carga de trabajo. 
    
- Lync: se recomienda usar el equilibrio de carga del Sistema de nombres de dominio (DNS) para el tráfico de protocolo de inicio de sesión (SIP) de granjas de servidores de Lync. El equilibrio de carga de hardware (HLB) es necesario para el tráfico de Lync Web (HTTPS). 
    
### <a name="remote-access-options"></a>Opciones de acceso remoto

Hay varias opciones que pueden publicar en Internet los recursos de la intranet para los asociados o proporcionar acceso remoto seguro a los empleados remotos o con movilidad. Estos ejemplos incluyen servidores proxy inversos, DirectAccess y puertas de enlace de VPN de terceros. Las soluciones de acceso remoto que se describen más adelante en esta sección son posibilidades para SharePoint, Lync y Exchange, o para cualquier combinación de estos servidores en una implementación local. Sin embargo, algunas opciones remotas podrían no funcionar con una solución concreta. 
  
Proxy inverso: un proxy inverso admite el cifrado de tráfico, como la capa de sockets seguros (SSL), y con este puede publicar en Internet aplicaciones de intranet y recursos web para usuarios autenticados y asociados. Un ejemplo es Microsoft Forefront Unified Access Gateway (UAG). Muchos equilibradores de carga de hardware también admiten la funcionalidad de proxy inverso. Sin embargo, todavía hay escenarios válidos para el uso de una solución independiente con base en sus necesidades y requisitos, tales como optimización del rendimiento, compartimentación de seguridad y aislamiento de tráfico. 
  
Ventajas y consideraciones del proxy inverso: 
  
- Proporciona acceso seguro y autenticado a los socios o usuarios que acceden a recursos de la intranet (usa SSL [TCP 443] entre el cliente y el servidor proxy inverso). 
    
- Para Exchange, una ventaja de usar un proxy inverso como Forefront UAG es la autenticación previa antes de acceder al servidor acceso de cliente de Exchange. Los usuarios de acceso remoto que usan aplicaciones publicadas como Outlook Web Access (OWA), pueden autenticar con los métodos básico, NTLM o Kerberos antes de acceder a la red interna. 
    
- Para Exchange y SharePoint, soluciones como Forefront UAG pueden terminar las conexiones SSL y disminuir la carga del servidor de recursos de la intranet y al mismo tiempo proporcionar un punto de administración único para los certificados. 
    
- Para Lync, el tráfico de Web (HTTPS) atraviesa el proxy inverso (TCP 443) para la comunicación con el cliente. El proxy inverso retransmite la conexión HTTPS a los servicios de Lync Web, los CAS de Exchange y Office Web Apps. Lync Server 2013 no es compatible con UAG. 
    
DirectAccess: tecnología de acceso remoto que se basa en el protocolo de seguridad de Internet (IPsec) para la autenticación y el cifrado de tráfico entre el servidor y el cliente de DirectAccess. DirectAccess proporciona acceso simultáneo a los recursos de Internet e intranet para los empleados remotos y con movilidad sin necesidad de iniciar una conexión. 
  
Aspectos a considerar sobre DirectAccess: 
  
- DirectAccess usa tráfico protegido por IPsec (protocolo 50 y 51 y UDP 500) entre el servidor y el cliente de DirectAccess. 
    
- DirectAccess para Windows Server 2012 y Windows 8 no necesita una implementación de infraestructura de clave pública (PKI) para la autenticación de cliente y servidor. 
    
- Se recomienda no usar DirectAccess con Lync Server 2013 debido a problemas de latencia de audio y vídeo asociados con el cifrado y descifrado de IPsec. 
    
    Puerta de enlace de VPN: las puertas de enlace de VPN típicas proporcionan una conexión de acceso remoto en la que el equipo de un cliente de acceso remoto se proyecta de forma lógica a la intranet a través de una conexión de túnel iniciada por el usuario. Puede usar el acceso remoto unificado de Windows Server 2012 o varias soluciones de terceros para proporcionar acceso seguro a la intranet para los empleados con movilidad o remotos. La opción de VPN no se recomienda para Lync. El tráfico remoto de Lync debe usar servidores perimetrales y el túnel dividido. 
    
### <a name="domain-name-system-dns-considerations"></a>Consideraciones sobre el Sistema de nombres de dominio (DNS)

Necesitará elaborar un plan para el conjunto de registros DNS que permiten a los usuarios de Internet e intranet resolver nombres DNS para las direcciones IP adecuadas. 
  
- Para los asociados basados en Internet y los empleados con movilidad o remotos, los registros DNS registrados con servidores DNS de Internet proporcionan una resolución para el conjunto de direcciones IP públicas correspondientes al enrutador de la puerta de enlace, el servidor perimetral de Lync, el conjunto de direcciones IP virtuales (VIP) en el equilibrador de carga, y la puerta de enlace VPN o DirectAccess según sea necesario. 
    
- Para los usuarios de la intranet, los registros DNS registrados con servidores DNS de la intranet proporcionan una resolución para el conjunto de direcciones IP virtuales (VIP) en el equilibrador de carga para el acceso a los recursos de Exchange, SharePoint y Lync. 
    
- Los clientes de DirectAccess usan servidores DNS de la intranet para los nombres que corresponden al espacio de nombres DNS de intranet y los servidores DNS de Internet para los demás nombres. Para simplificar la operación de DirectAccess, considere el uso de una implementación dividida de DNS que use distintos espacios de nombres DNS para los nombres basados en Internet y de intranet. Por ejemplo, use contoso.com para el espacio de nombres de Internet y corp.contoso.com para el espacio de nombres de intranet. 
    
- Exchange usa un modelo de DNS dividido donde el host de resolución de direcciones IP es diferente para el tráfico enrutado públicamente y para el tráfico de la red corporativa. Como mínimo, necesitará tener registros DNS para OWA, el servicio de detección automática, las direcciones URL de ActiveSync para el tráfico del cliente y un registro MX para el correo entrante. 
    
- Si está utilizando Exchange Online Protection (EOP), el registro MX señala a ese servicio en lugar de la granja de servidores de Exchange. 
    
- Para Exchange, necesitará un registro TXT de prueba de propiedad en el DNS público y un identificador de la organización de federación para configurar el uso compartido federado. 
    
- Los clientes de VPN de acceso remoto se pueden configurar para usar únicamente servidores DNS de la intranet cuando la conexión VPN de acceso remoto esté activa. 
    
### <a name="diagram-description"></a>Descripción del diagrama

Este diagrama proporciona un ejemplo de topología de red que ilustra el tráfico entrante y saliente a través de un enrutador de puerta de enlace y el equilibrio de carga del tráfico (externo e interno) de sesiones de cliente a los niveles de servidor de SharePoint, Exchange y Lync adecuados. La descripción de este diagrama se divide en dos partes: 
  
- Descripción de componentes mostrados en el diagrama 
    
- Descripción de cómo se mueve el tráfico a través de los componentes a los niveles de servidor de SharePoint, Exchange, Lync y Office Web Apps. 
    
#### <a name="description-of-components-shown-in-the-diagram"></a>Descripción de componentes mostrados en el diagrama

#### <a name="user-types"></a>Tipos de usuario

Hay cuatro tipos de usuario diferentes, tres fuera de los servicios de red y de nube y uno interno, que incluyen: 
  
- Empresas asociadas (negocio a negocio): externo 
    
- Asociados particulares (SharePoint y anónimo [Lync]): externo 
    
- Empleados remotos y con movilidad: externo 
    
- Empleados internos 
    
#### <a name="cloud-based-email-traffic"></a>Tráfico de correo electrónico basado en la nube

Hay un componente basado en la nube para el tráfico de correo electrónico basado en SMTP: hosts de correo de Internet o Exchange Online Protection. 
  
#### <a name="authentication-for-external-access"></a>Autenticación para acceso externo

Hay un conjunto específico de procedimientos de autenticación para cada uno de los tipos de usuario de Exchange, SharePoint y Lync. Estos se describen con mayor detalle más adelante en este documento. 
  
#### <a name="gateway-router-with-acls"></a>Enrutador de puerta de enlace con ACL

El enrutador de la puerta de enlace se encuentra en el perímetro de la red y enruta todo el tráfico entrante y saliente hacia y desde la intranet. 
  
#### <a name="remote-access-servers-for-lync-and-sharepoint"></a>Servidores de acceso remoto para Lync y SharePoint

Esta topología incluye un servidor perimetral de Lync y una puerta de enlace de VPN de SharePoint o un servidor de DirectAccess. 
  
#### <a name="load-balancer-and-reverse-proxy-device"></a>Equilibrador de carga y dispositivo de proxy inverso

Puede usar soluciones de equilibrio de carga de hardware o software para redirigir el tráfico de segmentos, incluidos servidores front-end web de SharePoint y servidores de acceso de cliente de Exchange (CAS). Esta topología muestra los componentes de direcciones IP virtuales de Lync, SharePoint y Exchange en el equilibrador de carga. 
  
#### <a name="servers"></a>Servidores

Hay cuatro servidores: Lync, Exchange, SharePoint y Office Web Apps Server. Cada servidor puede tener tres niveles: un front-end, un nivel de acceso de cliente, una capa de aplicación y un nivel de base de datos o almacenamiento de información.
  
#### <a name="front-end-client-access-tier"></a>Nivel de acceso de cliente front-end

Este nivel tiene componentes en los cuatro servidores: 
  
- Granja de servidores de Lync (front-end). El diagrama muestra dos bases de datos de Lync. 
    
- El servidor front-end de SharePoint y la caché distribuida. El diagrama muestra tres bases de datos de SharePoint. 
    
- CAS de Exchange. El diagrama muestra dos bases de datos de Exchange. 
    
- Office Web Apps Server. El diagrama muestra dos bases de datos de Office Web Apps. 
    
#### <a name="application-tier"></a>Capa de aplicación

Esta capa tiene componentes únicamente en el servidor de SharePoint: 
  
- Búsqueda (consulta, índice, administración). El diagrama muestra tres bases de datos de SharePoint. 
    
- Procesamiento por lotes. El diagrama muestra tres bases de datos de SharePoint. 
    
#### <a name="databasestorage-tier"></a>Nivel de base de datos y almacenamiento de información

Este nivel tiene componentes en los servidores de Exchange, SharePoint y Lync: 
  
- Base de datos de Lync (back-end). El diagrama muestra tres bases de datos de Lync. 
    
- Base de datos de SharePoint El diagrama muestra tres bases de datos de SharePoint. 
    
- Servidor de buzones de Exchange. El diagrama muestra dos servidores de buzones de Exchange. 
    
Para obtener más información sobre los componentes instalados en cada uno de los roles de servidor de SharePoint, consulte [Topologías simplificadas para SharePoint 2013](https://aka.ms/Ma5cgk). 
  
#### <a name="description-of-how-traffic-moves-through-the-components-to-the-different-server-tiers"></a>Descripción de cómo se mueve el tráfico a través de los componentes a los distintos niveles de servidor

Esta sección describe cómo se mueven las solicitudes del usuario a través de la topología de red. 
  
#### <a name="authentication-and-routing-for-external-access"></a>Autenticación y enrutamiento para acceso externo

Hay tres tipos de usuario diferentes fuera de los servicios de red y de nube, que incluyen: 
  
- Empresas asociadas (negocio a negocio): externo 
    
- Asociados particulares (SharePoint y anónimo [Lync]): externo 
    
- Empleados remotos y con movilidad: externo 
    
El proceso de autenticación y enrutamiento para cada tipo de usuario externo se describe de manera individual. 
  
#### <a name="partner-companies-business-to-business-httpspartnerwebcontosocom"></a>Empresas asociadas (negocio a negocio) (https://partnerweb.contoso.com)

- Lync: confianza de federación con otras organizaciones, Skype y conectividad de mensajería instantánea pública (PIC) con AOL. El tráfico de federación de Lync pasa a través del enrutador de puerta de enlace al servidor perimetral de Lync, a la dirección VIP de Lync (equilibrador de carga/servidor proxy inverso) y después al servidor de Lync. 
    
- SharePoint: Proveedor de identidad de asociados de confianza con autenticación SAML. El tráfico de cliente de SharePoint pasa a través del enrutador de puerta de enlace a la dirección VIP de SharePoint (equilibrador de carga/servidor proxy inverso) y después al servidor de SharePoint. 
    
- Exchange: Autenticación TLS mutua para el tráfico de correo, autenticación SAML para el uso compartido federado. El tráfico de cliente de Exchange pasa a través del enrutador de puerta de enlace a la dirección VIP de Exchange (equilibrador de carga/servidor proxy inverso) y después al servidor de Exchange. 
    
- El tráfico de SMTP pasa a través del enrutador de puerta de enlace y de la dirección VIP de Exchange (equilibrador de carga/servidor proxy inverso) al servidor de Exchange. 
    
#### <a name="individual-partners-sharepoint-and-anonymous-lync-httpspartnerwebcontosocom-and-httpsmeetcontosocom"></a>Asociados particulares (SharePoint) y anónimos (Lync) (https://partnerweb.contoso.com y https://meet.contoso.com)

- Lync: los usuarios anónimos solo pueden unirse a reuniones de Lync organizadas por los empleados. El tráfico de federación de Lync pasa a través del enrutador de puerta de enlace al servidor perimetral de Lync, a la dirección VIP de Lync (equilibrador de carga/servidor proxy inverso) y después al servidor de Lync. 
    
- SharePoint: Proveedor de identidad de asociados de confianza con autenticación SAML o autenticación basada en formularios. El tráfico de cliente de SharePoint pasa a través del enrutador de puerta de enlace a la dirección VIP de SharePoint (equilibrador de carga/servidor proxy inverso) y después al servidor de SharePoint. 
    
- Exchange: no aplica. 
    
- El tráfico de Lync Web pasa a través del enrutador de puerta de enlace al servidor perimetral de Lync, a la dirección VIP de Lync (equilibrador de carga/servidor proxy inverso), a un equilibrador de carga de hardware, que se requiere para el tráfico HTTPS, y después al servidor de Lync. 
    
#### <a name="roaming-and-remote-employees"></a>Empleados remotos y con movilidad

1. https://intranet.contoso.com 
    
2. https://teams.contoso.com 
    
3. https://my.contoso.com
    
4. https://partnerweb.contoso.com 
    
5. https://mail.contoso.com* 
    
6. https://dial.contoso.com*
    
7. https://meet.contoso.com*
    
* La dirección URL de Exchange consta de los siguientes directorios virtuales: Detección automática, ECP, EWS, Microsoft-Server-ActiveSync, OAB, OWA y PowerShell. 
  
- Lync: Autenticación TLS-DSK o NTLM. El tráfico de cliente de Lync pasa a través del enrutador de puerta de enlace al servidor perimetral de Lync, a la dirección VIP de Lync (equilibrador de carga/servidor proxy inverso) y después al servidor de Lync. 
    
- SharePoint: Servicios de dominio de Active Directory (AD DS), autenticación basada en formularios o autenticación SAML. El tráfico de cliente de SharePoint pasa a través de la puerta de enlace VPN o el servidor de DirectAccess a la dirección VIP de SharePoint (equilibrador de carga/servidor proxy inverso) y después al servidor de SharePoint. 
    
- Exchange: Autenticación básica mediante SSL (ActiveSync, detección automática) y autenticación basada en formularios (OWA). El tráfico de cliente de Exchange pasa a través del enrutador de puerta de enlace a la dirección VIP de Exchange (equilibrador de carga/servidor proxy inverso) y después al servidor de Exchange. 
    
- El tráfico de cliente de Lync pasa a través del enrutador de puerta de enlace a la dirección VIP de Lync (equilibrador de carga/servidor proxy inverso), a un equilibrador de carga de hardware, que se requiere para el tráfico HTTPS, y después al servidor de Lync. 
    
#### <a name="authentication-for-internal-access"></a>Autenticación para acceso interno

#### <a name="internal-employees"></a>Empleados internos

> https://intranet.contoso.com 
    
> https://teams.contoso.com 
    
> https://my.contoso.com
    
> https://partnerweb.contoso.com
    
> https://mail.contoso.com* 
    
> https://dial.contoso.com 
    
> https://meet.contoso.com
    
> https://admin.contoso.com
    
- Lync: Autenticación mediante Kerberos, TLS-DSK o NTLM. El tráfico de cliente de Lync pasa a la dirección VIP de Lync (equilibrador de carga/servidor proxy inverso) y después al servidor de Lync. 
    
- SharePoint: Servicios de dominio de Active Directory (AD DS), autenticación basada en formularios o autenticación SAML. El tráfico de cliente de SharePoint pasa a la dirección VIP de SharePoint (equilibrador de carga/servidor proxy inverso) y después al servidor de SharePoint. 
    
- Exchange: AD DS y autenticación basada en formularios. El tráfico de cliente de Exchange pasa a la dirección VIP de Exchange (equilibrador de carga/servidor proxy inverso) y después al servidor de Exchange. 
    
- El tráfico de cliente de Lync pasa a la dirección VIP de Lync (equilibrador de carga/servidor proxy inverso), a un equilibrador de carga de hardware, que se requiere para el tráfico HTTPS, y después al servidor de Lync. 
    
#### <a name="cloud-based-email-traffic"></a>Tráfico de correo electrónico basado en la nube

El componente basado en la nube para el tráfico de correo electrónico basado en SMTP consiste en hosts de correo de Internet o Exchange Online Protection.
  
Estos componentes mueven el tráfico de correo electrónico a través de la red mediante SMTP. El tráfico pasa a través del enrutador de puerta de enlace a la dirección VIP de Exchange (equilibrador de carga/servidor proxy inverso) y después al servidor de Exchange. 
  
### <a name="network-traffic-legend"></a>Leyenda de tráfico de red

El cuadro de la leyenda muestra de forma gráfica (con líneas de diferentes colores) los distintos tipos de tráfico representados en el gráfico, de la siguiente manera: 
  
- Línea verde: tráfico SIP de Lync 
    
- Línea azul: tráfico de Lync Web 
    
- Línea púrpura: Tráfico de cliente de SharePoint 
    
- Línea naranja: Tráfico de cliente de Exchange 
    
- Línea gris: Tráfico del servidor de correo de Exchange entre Exchange locales y Exchange Online Protection. 
    
En el cuadro de la leyenda también se describen los distintos tipos de tráfico y los puertos usados. 
  
#### <a name="lync-sip-traffic-and-lync-web-traffic"></a>Tráfico SIP de Lync y tráfico de Lync Web

El servidor perimetral de Lync usa los siguientes puertos para la comunicación del usuario externo: 
  
- Tráfico de señalización/IM (SIP o SIMPLE): Puerto TCP 443 (abierto para el tráfico entrante) 
    
- Tráfico de conferencias Web (PSOM): TCP 443 (abierto para el tráfico entrante) 
    
- Tráfico de A/V (SRTP): TCP 443, UDP 3478 y TCP 50000-59999 (opcional) (abiertos para el tráfico entrante y saliente) 
    
El servidor perimetral de Lync usa los siguientes puertos para la comunicación con servicios de federación: 
  
- Puertos TCP 5061 (SIP), 5269 (XMPP) y 443 y puerto UDP 3478 (SRTP) (abiertos para el tráfico entrante y saliente) 
    
#### <a name="sharepoint-client-traffic"></a>Tráfico de cliente de SharePoint

SharePoint puede usar el puerto TCP 443 (SSL) para comunicaciones cifradas entre el cliente y el equilibrador de carga. Para el acceso externo desde Internet, este puerto debe abrirse para el tráfico entrante y saliente en el enrutador de la puerta de enlace (o firewall externo). 
  
#### <a name="exchange-client-traffic-and-exchange-mail-server-traffic"></a>Tráfico de cliente de Exchange y tráfico del servidor de correo de Exchange

Exchange usa el puerto TCP 25 (SMTP) para las comunicaciones de servidor a servidor. La mayor parte del tráfico de cliente (OWA, ActiveSync, detección automática, Outlook en cualquier lugar) se controla a través del puerto 443 (HTTPS). Si tiene clientes POP o IMAP, los puertos 110 (POP3), 995 (cifrado POP3), 143 (IMAP4), 993 (IMAP4 cifrados) y 587 (SMTP) también se usan para ofrecer compatibilidad a estos clientes. 
  
#### <a name="more-on-lync-network-traffic"></a>¿Desea conocer más sobre el tráfico de red de Lync?

Infórmese de cómo Lync Server puede ayudar a su organización a proporcionar mensajería instantánea, conferencias web, uso compartido de aplicaciones y comunicación de voz. Para obtener más información, consulte el [Póster de cargas de trabajo de protocolos de Microsoft Lync Server 2013 ](https://aka.ms/G5jzjo). 
  
El póster también incluye un código QR para acceder a esta información. 
  

