---
title: Redes de entrega de contenido
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/2/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 0140f704-6614-49bb-aa6c-89b75dcd7f1f
description: Use esta información para obtener información sobre cómo Office 365 usa redes de entrega de contenido (CDN) para mejorar el rendimiento.
ms.openlocfilehash: 080e4bac5f77defc9fd87f22c0f2cb1466dc8945
ms.sourcegitcommit: 0449c6f854c682719cac1bd0d086f2e3b20078b9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2019
ms.locfileid: "34722669"
---
# <a name="content-delivery-networks-cdns"></a>Redes de entrega de contenido (CDN)

Las redes CDN ayudan a mantener Office 365 rápido y fiable para los usuarios finales. Servicios en la nube como Office 365 usar CDN para almacenar en caché activos estáticos más cerca de los exploradores que les soliciten acelerar las descargas y reducir la latencia de usuario final. La información de este tema le ayudará a obtener información sobre las redes de entrega de contenido (CDN) y cómo se usan en Office 365.

## <a name="what-exactly-is-a-cdn"></a>¿Qué es exactamente una CDN?

Una red CDN es una red distribuida geográficamente que consta de servidores proxy y de archivos en centros de recursos conectados por redes troncales de alta velocidad. Los CDN se usan para reducir los tiempos de latencia y carga de un conjunto especificado de archivos y objetos en un servicio o sitio Web. Una red CDN puede tener varios miles de puntos de conexión para un mantenimiento óptimo de las solicitudes entrantes desde cualquier ubicación.

Las CDN se suelen usar para proporcionar descargas más rápidas de contenido genérico para un sitio web o servicio como archivos JavaScript, iconos e imágenes, y también pueden proporcionar acceso privado al contenido del usuario, como archivos en bibliotecas de documentos de SharePoint Online, archivos multimedia de transmisión por secuencias y código personalizado.

La mayoría de los servicios de nube de empresa usan las CDN. Los servicios en la nube como Office 365 tienen millones de clientes que descargan una combinación de contenido propietario (como correos electrónicos) y contenido genérico (como iconos) a la vez. Es más eficaz poner las imágenes que usan todos los usuarios, como iconos, lo más cerca posible del equipo del usuario. No es práctico para todos los servicios en la nube la creación de centros de datos de CDN que almacenen este contenido genérico en todas las áreas metropolitanas, o incluso en todos los principales concentradores de Internet en todo el mundo, de modo que se compartan algunas de estas redes CDN.

## <a name="how-do-cdns-make-services-work-faster"></a>¿Cómo hacen que los servicios de CDN funcionen más rápido?

Descargar objetos comunes como iconos una y otra vez puede ocupar un ancho de banda de red que se puede utilizar mejor para descargar contenido personal importante, como correo electrónico o documentos. Como Office 365 usa una arquitectura que incluye redes CDN, los iconos, los scripts y otros contenidos genéricos se pueden descargar de los servidores más cercanos a los equipos cliente, lo que hace que las descargas sean más rápidas. Esto implica un acceso más rápido a su contenido personal, que se almacena de forma segura en los centros de datos de Office 365.

Las CDN ayudan a mejorar el rendimiento del servicio de nube de varias maneras:

- Los CDN desplazan parte de la red y sobrecarga de descarga de archivos del servicio de nube, lo que libera recursos de servicio en la nube para proporcionar contenido de usuario y otros servicios al reducir la necesidad de servir solicitudes para activos estáticos.
- Los CDN están diseñados para proporcionar acceso a los archivos de baja latencia mediante la implementación de redes de alto rendimiento y servidores de archivos, y mediante el uso de protocolos de red actualizados como [http/2](https://en.wikipedia.org/wiki/HTTP/2) con compresión muy eficaz y multiplexación de solicitudes.
- Las redes CDN usan muchos extremos distribuidos globalmente para que el contenido esté disponible lo más cerca posible a los usuarios.

## <a name="the-office-365-cdn"></a>La red CDN de Office 365

La red de entrega de contenido (CDN) integrada de Office 365 permite a los administradores de Office 365 proporcionar un mejor rendimiento para las páginas de SharePoint Online de su organización al almacenar en caché activos estáticos más cerca de los exploradores que les solicitan, lo que ayuda a acelerar descarga y reduce la latencia. La red CDN de Office 365 usa el [protocolo http/2](https://en.wikipedia.org/wiki/HTTP/2) para mejorar la compresión y la velocidad de descarga.

> [!NOTE]
> Restricciones de uso de la red CDN de Office 365:
> + La red CDN de Office 365 solo está disponible para los inquilinos en la nube de **producción** (en todo el mundo). Actualmente, los inquilinos de las nubes del gobierno de Estados Unidos, China y Alemania no admiten la red CDN de Office 365.
> + La red CDN de Office 365 no es compatible actualmente con los inquilinos configurados con dominios personalizados o "" de cortesía ". Si ha agregado un dominio a su inquilino siguiendo las instrucciones del tema [Agregar un dominio a office 365](https://docs.microsoft.com/en-us/office365/admin/setup/add-domain?view=o365-worldwide), la red CDN de Office 365 devolverá errores cuando intente obtener acceso al contenido de la red CDN.

La CDN de Office 365 se compone de varias redes CDN que permite hospedar archivos estáticos en varias ubicaciones u _orígenes_ y a realizar la entrega desde redes de alta velocidad globales. Según el tipo de contenido que quiera hospedar en la CDN de Office 365, puede agregar orígenes **públicos**, **privados** o ambos.

![Diagrama conceptual de la red CDN de Office 365] (media/O365-CDN/o365-cdn-flow-transparent.svg "Diagrama conceptual de la red CDN de Office 365")

El contenido en orígenes **públicos** dentro de la CDN de Office 365 es accesible de forma anónima y cualquier persona que tenga la URL a los activos hospedado puede acceder. Como el acceso al contenido en orígenes públicos es anónimo, solo debe usarlos para almacenar en caché contenido genérico y no confidencial, como archivos javascript, scripts, iconos e imágenes. La CDN de Office 365 se usa de forma predeterminada para descargar activos de recurso genéricos como las aplicaciones cliente de Office 365 desde un origen público.

**Privado** los orígenes dentro de la CDN de Office 365 proporcionan acceso privado al contenido del usuario, como bibliotecas de documentos de SharePoint Online, sitios y elementos multimedia, como vídeos. El acceso al contenido de orígenes privados está protegido con tokens generados de forma dinámica, por lo que pueden acceder los usuarios con permisos para la ubicación de almacenamiento o de biblioteca de documentos original. Los orígenes privados en la CDN de Office 365 solo pueden usarse para el contenido de SharePoint Online y solo se puede acceder a los activos mediante el redireccionamiento de su espacio empresarial de SharePoint Online.

La red CDN de Office 365 se incluye como parte de la suscripción a SharePoint Online.

Para obtener más información acerca de cómo usar la red CDN de Office 365, vea [usar la red de entrega de contenido de office 365 con SharePoint Online](https://docs.microsoft.com/en-us/office365/enterprise/use-office-365-cdn-with-spo).

## <a name="other-microsoft-cdns"></a>Otros CDN de Microsoft

Aunque no forma parte de la red CDN de Office 365, puede usar estas CDN en el inquilino de Office 365 para obtener acceso a bibliotecas de desarrollo de SharePoint, a código personalizado y a otros fines que no se encuentren fuera del ámbito de la red CDN de Office 365.

### <a name="azure-cdn"></a>RED CDN de Azure

Puede usar la **red CDN de Azure** para implementar su propia instancia de CDN para hospedar elementos Web personalizados, bibliotecas y otros activos de recursos, lo que le permite aplicar claves de acceso a su almacenamiento de red CDN y ejercer un mayor control sobre la configuración de la red CDN. El uso de la red CDN de Azure no es gratuito y requiere una suscripción a Azure.

Para obtener más información sobre cómo configurar una instancia de CDN de Azure, consulte [QuickStart: integrar una cuenta de almacenamiento de Azure en la red CDN de Azure](https://docs.microsoft.com/en-us/azure/cdn/cdn-create-a-storage-account-with-cdn).

Para ver un ejemplo de cómo se puede usar la red CDN de Azure para hospedar elementos Web de SharePoint, vea [implementar el elemento Web del lado cliente de SharePoint en la red CDN de Azure](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/web-parts/get-started/deploy-web-part-to-cdn).

Para obtener información sobre el módulo de PowerShell de la red CDN de Azure, vea [administrar la red CDN de Azure con PowerShell](https://docs.microsoft.com/en-us/azure/cdn/cdn-manage-powershell).

### <a name="microsoft-ajax-cdn"></a>RED CDN de Microsoft Ajax

La **red CDN de Ajax** de Microsoft es una red CDN de solo lectura que ofrece muchas bibliotecas de desarrollo populares, como jQuery (y todas sus otras bibliotecas), ASP.NET AJAX, Bootstrap, Knockout. js y otras.
  
Para incluir estos scripts en su proyecto, simplemente reemplace todas las referencias a estas bibliotecas disponibles públicamente por referencias a la dirección de la red CDN en lugar de incluirla en el propio proyecto. Por ejemplo, use el siguiente código para vincular a jQuery:

``` html
<script src=http://ajax.aspnetcdn.com/ajax/jquery-2.1.1.js> </script>
```

Para obtener más información acerca de cómo usar la red CDN de Microsoft Ajax, consulte [CDN de Microsoft Ajax](https://docs.microsoft.com/en-us/aspnet/ajax/cdn/overview).

## <a name="how-does-office-365-use-content-from-a-cdn"></a>¿Cómo usa Office 365 el contenido de una red CDN?

Independientemente de qué red CDN configure para el inquilino de Office 365, el proceso de recuperación de datos básicos es el mismo.

1. El cliente (un explorador o una aplicación cliente de Office) solicita datos de Office 365.

2. Office 365 ambos devuelve los datos directamente en su cliente o, si los datos forman parte de un conjunto de contenido hospedado por la red CDN, redirige el cliente a la dirección URL de la red CDN.

    a. Si los datos ya están almacenados en la memoria caché de un origen _público_ , el cliente descarga los datos directamente desde la ubicación de la red CDN más cercana a su cliente.

    b. Si los datos ya están almacenados en la memoria caché de un origen _privado_ , el servicio de CDN comprueba los permisos de la cuenta de usuario de Office 365 en el origen. Si tiene permisos, SharePoint Online genera dinámicamente una dirección URL personalizada compuesta por la ruta de acceso al activo en la red CDN y dos tokens de acceso y devuelve la dirección URL personalizada a su cliente. A continuación, el cliente descarga los datos directamente desde la ubicación de la red CDN más cercana a su cliente mediante la dirección URL personalizada.

3. Si los datos no se almacenan en caché en la red CDN, el nodo de la red CDN solicita los datos de Office 365 y, a continuación, almacena los datos en la memoria caché durante un período de tiempo después de que el cliente descargue los datos.

La red CDN Averigua el centro de datos más cercano al explorador del usuario y, mediante el redireccionamiento, descarga los datos solicitados desde allí. La redirección de la red CDN es rápida y puede ahorrar un gran tiempo de descarga a los usuarios.

## <a name="how-should-i-set-up-my-network-so-that-cdns-work-best-with-office-365"></a>¿Cómo debo configurar mi red para que las redes CDN funcionen mejor con Office 365?

La reducción de la latencia entre los clientes de la red y los puntos de conexión de red CDN es la consideración clave para garantizar un rendimiento óptimo. Puede usar las prácticas recomendadas que se describen en [Administración de puntos de conexión de Office 365](managing-office-365-endpoints.md) para garantizar que la configuración de red permita a los exploradores del cliente tener acceso a la red CDN directamente en lugar de enrutar el tráfico de la red CDN a través de servidores proxy centralizados para evitar la introducción latencia innecesaria.

También puede leer los [principios de conectividad de red de office 365](https://aka.ms/o365networkingprinciples) para comprender los conceptos que hay tras optimizar el rendimiento de la red de Office 365.

## <a name="is-there-a-list-of-all-the-cdns-that-office-365-uses"></a>¿Hay una lista de todos los CDN que usa Office 365?

Las redes CDN que usa Office 365 siempre están sujetas a cambios y, en muchos casos, hay varios socios de la red CDN configurados en el evento uno no está disponible. Los CDN principales usados por Office 365 son:

|COMPLEMENTA  |Company  |Uso  |Vínculo  |
|---------|---------|---------|---------|
|RED CDN de Office 365     |Download         |Recursos genéricos en orígenes públicos, contenido de usuario de SharePoint en orígenes privados         |[Uso de la red de entrega de contenido de Office 365 con SharePoint Online](https://docs.microsoft.com/en-us/office365/enterprise/use-office-365-cdn-with-spo)         |
|RED CDN de Azure     |Microsoft         |Código personalizado, soluciones de SharePoint Framework         |[CDN de Microsoft Azure](https://azure.microsoft.com/documentation/services/cdn/)         |
|RED CDN de Microsoft Ajax (solo lectura)     |Microsoft         |Bibliotecas comunes para Ajax, jQuery, ASP.NET, Bootstrap, Knockout. js, etc.         |[RED CDN de Microsoft Ajax](https://docs.microsoft.com/en-us/aspnet/ajax/cdn/overview)         |

## <a name="what-performance-gains-does-a-cdn-provide"></a>¿Qué beneficios de rendimiento proporciona una red CDN?

Hay muchos factores implicados en la medición de diferencias específicas de rendimiento entre los datos descargados directamente desde Office 365 y los datos descargados desde una CDN específica, como la ubicación relativa al espacio empresarial y el extremo de red CDN más cercano, el número de activos en una página que atiende la red CDN y cambios transitorios en la latencia y el ancho de banda de la red. Sin embargo, una prueba A/B sencilla puede ayudar a mostrar la diferencia en el tiempo de descarga de un archivo específico.

En las siguientes capturas de pantalla se muestra la diferencia en la velocidad de descarga entre la ubicación nativa de archivos en Office 365 y el mismo archivo hospedado en la [red de entrega de contenido de Microsoft Ajax](https://docs.microsoft.com/en-us/aspnet/ajax/cdn/overview). Estas capturas de pantalla se encuentran en la pestaña **red** de las herramientas de desarrollo de Internet Explorer 11. En estas capturas de pantalla se muestra la latencia de la biblioteca de jQuery de la popular. Para que aparezca esta pantalla, en Internet Explorer, presione **F12** y seleccione la pestaña **red** , que se simbólica con un icono de Wi-Fi.
  
![Captura de pantalla de red F12](media/930541fd-af9b-434a-ae18-7bda867be128.png)
  
En esta captura de pantalla se muestra la biblioteca cargada en la galería de páginas maestras en el propio sitio de SharePoint Online. El tiempo que tardó en cargar la biblioteca es de 1,51 segundos.
  
![Captura de pantalla de tiempo de carga de 1,51 s](media/64225c79-fa53-480f-81cd-0d351674320e.png)
  
La segunda captura de pantalla muestra el mismo archivo que proporciona la red CDN de Microsoft. Esta vez la latencia es de alrededor de 496 milisegundos. Esto es una gran mejora y muestra que se ha recortado un segundo entero el tiempo total de descarga del objeto.
  
![Captura de pantalla de los tiempos de carga de 469 ms](media/6a553cc3-25a0-42c1-aae7-4aebbc2eb4c3.png)

## <a name="is-my-data-safe"></a>¿Mis datos son seguros?

Nos preocupamos por proteger los datos que ejecutan su empresa. Los datos almacenados en la red CDN de Office 365 se cifran en tránsito y en reposo, y el acceso a los datos de la red CDN de SharePoint de Office 365 está protegido por los permisos de usuario y la autorización de tokens de Office 365. Las solicitudes de datos en la red CDN de Office 365 de SharePoint se deben hacer referencia (redirigidas) desde el espacio empresarial de Office 365 o no se generará un token de autorización.

Para asegurarse de que los datos permanecen seguros, le recomendamos que no almacene nunca el contenido de los usuarios ni otros datos confidenciales en una red CDN pública. Dado que el acceso a datos en una red CDN pública es anónimo, los CDN públicos solo deben usarse para hospedar contenido genérico como archivos de script Web, iconos, imágenes y otros activos no confidenciales.

> [!NOTE]
> los proveedores de CDN de terceros pueden tener estándares de privacidad y cumplimiento que difieren de los compromisos indicados por el centro de confianza de Office 365. Los datos que se almacenan en caché a través del servicio de red CDN pueden no cumplir con los términos de procesamiento de datos de Microsoft (DPT) y pueden estar fuera de los límites de cumplimiento del centro de confianza de Office 365.

Para obtener información detallada acerca de la privacidad y la protección de datos de los proveedores de CDN de Office 365, visite lo siguiente:  

- Obtenga más información sobre la protección de datos y privacidad de Office 365 en el [centro de confianza de Microsoft](https://www.microsoft.com/trustcenter)
- Obtenga más información sobre la privacidad y la protección de datos de Akamai en el centro de confianza de la [privacidad de Akamai](https://www.akamai.com/us/en/about/compliance/data-protection-at-akamai.jsp)
- Obtenga más información sobre la privacidad y la protección de datos de Azure en el [centro de confianza de Azure](https://azure.microsoft.com/en-us/overview/trusted-cloud/)

## <a name="how-can-i-secure-my-network-with-all-these-3rd-party-services"></a>¿Cómo puedo proteger mi red con estos servicios de terceros?

Aprovechar un amplio conjunto de servicios de asociados permite escalar Office 365 y cumplir los requisitos de disponibilidad, así como mejorar la experiencia del usuario al usar Office 365. Los servicios de terceros que Office 365 usa incluyen ambas listas de revocación de certificados; como crl.microsoft.com o sa.symcb.com, y CDN; como r3.res.outlook.com. Cada FQDN de CDN generado por Office 365 es un FQDN personalizado para Office 365. Si se le envía a un FQDN a petición de Office 365, puede tener la certeza de que el proveedor de la red CDN controla el FQDN y el contenido subyacente en esa ubicación.
  
Para los clientes que desean segregar las solicitudes dirigidas a un centro de información de Microsoft u Office 365 desde solicitudes destinadas a terceros, hemos escrito una guía sobre la [Administración de puntos de conexión de office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a).

## <a name="is-there-a-list-of-all-the-fqdns-that-leverage-cdns"></a>¿Hay una lista de todos los FQDN que aprovechan las CDN?

La lista de FQDN y la forma en que aprovechan las CDN cambian con el tiempo. Consulte nuestra página de [direcciones url 365 URL publicadas e intervalos de direcciones IP](https://go.microsoft.com/fwlink/p/?LinkID=293744) para obtener los últimos FQDN que aprovechan las CDN.

También puede usar la [dirección IP y el servicio Web de office 365](https://docs.microsoft.com/en-us/office365/enterprise/office-365-ip-web-service) para solicitar las direcciones URL y los intervalos de direcciones IP de Office 365 actuales con formato CSV o JSON.

## <a name="can-i-use-my-own-cdn-and-cache-content-on-my-local-network"></a>¿Puedo usar mi propia red CDN y contenido de caché en mi red local?

Estamos buscando continuamente nuevas formas de apoyar las necesidades de nuestros clientes y actualmente está explorando el uso de soluciones de proxy de almacenamiento en caché y otras soluciones de CDN local.

Aunque no forma parte de la red CDN de Office 365, también puede usar la **red CDN de Azure** para hospedar elementos Web personalizados, bibliotecas y otros activos de recursos, lo que le permite aplicar teclas de acceso al almacenamiento de la red CDN y ejercer un mayor control sobre la configuración de la red CDN. El uso de la red CDN de Azure no es gratuito y requiere una suscripción a Azure. Para obtener más información sobre cómo configurar una instancia de CDN de Azure, consulte [QuickStart: integrar una cuenta de almacenamiento de Azure en la red CDN de Azure](https://docs.microsoft.com/en-us/azure/cdn/cdn-create-a-storage-account-with-cdn).

## <a name="im-using-azure-expressroute-for-office-365-does-that-change-things"></a>Estoy usando Azure ExpressRoute para Office 365, ¿eso cambia?

[Azure ExpressRoute para office 365](azure-expressroute.md) proporciona una conexión dedicada a la infraestructura de Office 365 que está segregada de Internet pública. Esto significa que los clientes aún tendrán que conectarse a través de conexiones que no sean de ExpressRoute para conectarse a CDN y a otra infraestructura de Microsoft que no esté incluida explícitamente en la lista de servicios compatibles con ExpressRoute. Para obtener más información acerca de cómo enrutar tráfico específico, como solicitudes dirigidas a redes CDN, consulte la [Administración del tráfico de red de Office 365](routing-with-expressroute.md).

## <a name="can-i-use-cdns-with-sharepoint-server-on-premises"></a>¿Puedo usar CDN con SharePoint Server local?

El uso de redes CDN solo tiene sentido en un contexto de SharePoint Online y debe evitarse con SharePoint Server. Esto se debe a que todas las ventajas sobre la ubicación geográfica no tienen el valor true si el servidor se encuentra local o geográficamente cerrado de todos modos. Además, si hay una conexión de red a los servidores en los que está hospedada, el sitio puede usarse sin una conexión a Internet y, por lo tanto, no puede recuperar los archivos de la red CDN. De lo contrario, debe usar una red CDN si hay una disponible y estable para la biblioteca y los archivos que necesita para su sitio.
  
Este es un vínculo breve que se puede usar para volver: [https://aka.ms/o365cdns](https://aka.ms/o365cdns)
  
## <a name="see-also"></a>Vea también

[Principios de conectividad de red de Office 365](https://aka.ms/o365networkingprinciples)

[Evaluación de la conectividad de red de Office 365](assessing-network-connectivity.md)

[Administrar puntos de conexión de Office 365](https://docs.microsoft.com/en-us/office365/enterprise/managing-office-365-endpoints)

[Intervalos de direcciones IP y URL de Office 365](https://go.microsoft.com/fwlink/p/?LinkID=293744)

[Uso de la red de entrega de contenido de Office 365 con SharePoint Online](https://docs.microsoft.com/en-us/office365/enterprise/use-office-365-cdn-with-spo)

[Centro de confianza de Microsoft](https://www.microsoft.com/trustcenter)