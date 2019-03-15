---
title: Redes de entrega de contenido
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 3/14/2019
ms.audience: ITPro
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
description: Use esta información para obtener información sobre las redes de entrega de contenido (CDN) y cómo Office 365 las aprovecha.
ms.openlocfilehash: 50f28e8311a501d9bc5b3f2c709fa84b1633e418
ms.sourcegitcommit: e5598a1220316122b5ed206c2607092ea1eac65c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "30636101"
---
# <a name="content-delivery-networks"></a>Redes de entrega de contenido

La información de este tema le ayudará a obtener información sobre las redes de entrega de contenido (CDN) y cómo se usan en Office 365.

Las redes CDN ayudan a mantener Office 365 rápido y fiable para los usuarios finales. Servicios en la nube como Office 365 usar CDN para almacenar en caché activos estáticos más cerca de los exploradores que les solicitan acelerar las descargas y reducir la latencia. Los CDN públicos permiten descargas más rápidas de contenido genérico como archivos JavaScript, iconos e imágenes, mientras que los CDN privados pueden proporcionar acceso rápido y seguro al contenido del usuario, como vídeos y bibliotecas de documentos de SharePoint Online.
  
 **Encabezado volver a** [Planeación de red y ajuste del rendimiento para Office 365](https://aka.ms/tune).
  
## <a name="what-exactly-is-a-cdn"></a>¿Qué es exactamente una CDN?

La mayoría de los servicios de nube de empresa usan las CDN. Los servicios en la nube como Office 365 tienen millones de clientes que descargan una combinación de contenido propietario (como correos electrónicos) y contenido genérico (como iconos) a la vez. Es más eficaz poner las imágenes que usan todos los usuarios, como iconos, lo más cerca posible del equipo del usuario. Sin embargo, no es práctico para todos los servicios en la nube la creación de centros de datos de CDN que almacenen este contenido genérico en cada área metropolitana, o incluso en todos los principales concentradores de Internet en todo el mundo, de modo que se compartan algunas de estas CDN.
  
Los CDN pueden ser privados o públicos. Las redes CDN privadas son propiedad y operativas de una sola empresa, y solo las aplicaciones y servicios de la compañía pueden usarla. Los CDN públicos los ejecutan empresas que conceden el uso a varias empresas. En función de dónde se encuentre, es posible que sea más eficaz para que Office 365 Descargue imágenes genéricas de una red CDN que Office 365 posee y ejecuta una red CDN pública o una combinación de ambas. Independientemente del tipo de red CDN que se use, los pasos para recuperar los datos son los mismos.
  
1. El cliente solicita datos de Office 365.

2. Office 365 ambos devuelve los datos directamente en su cliente o dirige el cliente a una red CDN.

3. Si los datos ya están almacenados en caché en la red CDN, el cliente descarga los datos directamente desde la ubicación de la red CDN más cercana a su cliente en Internet.

4. Si los datos no se almacenan en caché en la red CDN, el nodo de la red CDN solicita los datos de Office 365 y, a continuación, almacena en caché los datos durante un período de tiempo después de que el cliente descargue los datos.

Los CDN extraen los archivos y las imágenes del centro de recursos de Office 365 más cercano y, a su vez, el cliente extrae los archivos y las imágenes de la red CDN más cercana. Cuando los usuarios obtienen acceso a un servicio en la nube, como leer el correo electrónico en Outlook Web App, el explorador del usuario intenta recuperar los archivos y las imágenes del centro de servicios de Office 365. En lugar de gastar el tiempo y el ancho de banda que entrega los archivos, Office 365 redirige el explorador a la red CDN. La red CDN Averigua el centro de recursos más cercano al explorador del usuario y, mediante el redireccionamiento, descarga las imágenes genéricas desde allí. El uso de esta redirección de la red CDN es rápido y ahorra a los usuarios mucho tiempo de descarga.

## <a name="how-do-cdns-make-services-work-faster"></a>¿Cómo hacen que los servicios de CDN funcionen más rápido?

Descargar tareas comunes, como iconos, una y otra vez puede ocupar un ancho de banda de red que se puede utilizar mejor para descargar contenido personal importante, como correo electrónico o documentos. Como Office 365 usa una arquitectura que incluye redes CDN, los iconos, los scripts y otros contenidos genéricos se pueden descargar de los servidores más cercanos a los equipos cliente, lo que hace que las descargas sean más rápidas. Esto implica un acceso más rápido a su contenido personal, que se almacena de forma segura en los centros de datos de Office 365.

## <a name="how-should-i-set-up-my-network-so-that-cdns-work-best-with-office-365"></a>¿Cómo debo configurar mi red para que las redes CDN funcionen mejor con Office 365?

Si está planeando la [conectividad de red con Office 365](network-connectivity.md), es útil comprender cómo funcionan las redes CDN en general y cómo debe administrarse el tráfico de red de CDN.

Cuando se habilita una CDN para el inquilino de Office 365, se comienza por la configuración de directivas que rigen los orígenes de contenido (denominados **orígenes** en el contexto de redes CDN), las clasificaciones de datos o los tipos de archivo que se desea distribuir por la red CDN. Los usuarios que tengan acceso al contenido especificado se redirigirán a la ubicación más cercana del archivo en la red CDN. Por lo tanto, debe usar las prácticas recomendadas que se describen en [Administración de puntos de conexión de Office 365](managing-office-365-endpoints.md) para garantizar que la configuración de red permita a los exploradores de cliente tener acceso a la red CDN directamente en lugar de enrutar el tráfico de la red CDN a través de servidores proxy centralizados para evitar presentar una latencia innecesaria.

## <a name="is-my-data-safe"></a>¿Mis datos son seguros?

Nos preocupamos de ayudarle a garantizar que se protegen los datos que se ejecutan en su empresa. Los datos específicos del cliente almacenados en las CDN se cifran en tránsito y en reposo.

> [!NOTE]
> Los proveedores de CDN pueden tener estándares de privacidad y cumplimiento que difieren de los compromisos indicados por el centro de confianza de Office 365. Los datos que se almacenan en caché a través del servicio de red CDN pueden no cumplir con los términos de procesamiento de datos de Microsoft (DPT) y pueden estar fuera de los límites de cumplimiento del centro de confianza de Office 365.

Para obtener información detallada acerca de la privacidad y la protección de datos de los proveedores de CDN de Office 365, visite lo siguiente:  

+ Obtenga más información sobre la protección de datos y privacidad de Office 365 en el [centro de confianza de Microsoft](https://www.microsoft.com/trustcenter)
+ Obtenga más información sobre la privacidad y la protección de datos de Azure en el [centro de confianza de Azure](https://azure.microsoft.com/en-us/overview/trusted-cloud/)
+ Obtenga más información sobre la privacidad y la protección de datos de Akamai en el centro de confianza de la [privacidad de Akamai](https://www.akamai.com/us/en/about/compliance/data-protection-at-akamai.jsp)

## <a name="how-can-i-secure-my-network-with-all-these-3rd-party-services"></a>¿Cómo puedo proteger mi red con estos servicios de terceros?

Aprovechar un amplio conjunto de servicios de asociados permite escalar Office 365 y cumplir los requisitos de disponibilidad, así como mejorar la experiencia del usuario al usar Office 365. Los servicios de terceros que Office 365 usa incluyen ambas listas de revocación de certificados; como crl.microsoft.com o sa.symcb.com, y CDN; como R3.res.Outlook.com. Cada FQDN de CDN que Office 365 usa es un FQDN personalizado para Office 365. Si se le envía a un FQDN a petición de Office 365, puede tener la certeza de que el proveedor de la red CDN controla el FQDN y el contenido subyacente en esa ubicación.
  
Para los clientes que aún quieren segregar solicitudes dirigidas a un centro de información de Microsoft u Office 365 desde solicitudes destinadas a terceros, hemos escrito una guía sobre la administración de los [puntos de conexión de office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a).

## <a name="is-there-a-list-of-all-the-cdns-that-office-365-uses"></a>¿Hay una lista de todos los CDN que usa Office 365?

Las redes CDN que usa Office 365 siempre están sujetas a cambios y, en muchos casos, hay varios socios de la red CDN configurados en el evento uno no está disponible. Las CDN principales en uso son:

+ [Office 365 (específicamente para el contenido de SharePoint Online)](https://docs.microsoft.com/en-us/office365/enterprise/use-office-365-cdn-with-spo)
+ [Microsoft Azure](https://azure.microsoft.com/documentation/services/cdn/)
+ [Download](https://www.akamai.com/us/en/cdn.jsp)

Estas soluciones de red CDN tienen un alcance global que mejora el alcance del servicio a más esquinas del mundo. El contenido que se almacena incluye los scripts generales de Office 365, archivos e imágenes. Por ejemplo, cuando inicia sesión en portal.office.com, las imágenes se extraen de la red CDN más cercana para acelerar los tiempos de carga de la página. Otros ejemplos incluyen Office 365 proPlus que almacena los bits de instalación en una red CDN para acelerar la cantidad de tiempo que se tarda en descargar la versión más reciente de Office.

También hay contenido propietario que se almacena en los CDN, como los archivos de vídeo para Office 365 video. Después de cargar los vídeos, los archivos se cifran y, a continuación, se almacenan en su formato cifrado con Azure Media Services. Cuando el reproductor de vídeo de Office 365 recupera el vídeo, se almacena en caché en la red CDN más cercana antes de descargarla para acelerar la cantidad de tiempo que se tarda en descargar el vídeo.

Para obtener información sobre cómo usar la red CDN de Office 365, vea [usar la red de entrega de contenido de office 365 con SharePoint Online](use-office-365-cdn-with-spo.md).

## <a name="is-there-a-list-of-all-the-fqdns-that-leverage-cdns"></a>¿Hay una lista de todos los FQDN que aprovechan las CDN?

La lista de FQDN y la forma en que los usuarios usan las CDN cambian con el tiempo, consulte nuestra página de [direcciones url 365 URL publicadas e intervalos de direcciones IP](https://go.microsoft.com/fwlink/p/?LinkID=293744) para obtener los últimos FQDN que aprovechan las CDN.

## <a name="can-i-use-my-own-cdn-and-cache-content-on-my-local-network"></a>¿Puedo usar mi propia red CDN y contenido de caché en mi red local?

Estamos buscando continuamente nuevas formas de apoyar las necesidades de nuestros clientes y actualmente está explorando el uso de soluciones de proxy de almacenamiento en caché y otras soluciones de CDN local.

## <a name="im-using-azure-expressroute-for-office-365-does-that-change-things"></a>Estoy usando Azure ExpressRoute para Office 365, ¿eso cambia?

[Azure ExpressRoute para office 365](azure-expressroute.md) proporciona una conexión dedicada a la infraestructura de Office 365 que está segregada de Internet pública. Esto significa que los clientes aún tendrán que conectarse a través de conexiones que no sean de ExpressRoute para conectarse a CDN y a otra infraestructura de Microsoft que no esté incluida explícitamente en la lista de servicios compatibles con ExpressRoute. Para obtener más información acerca de cómo enrutar tráfico específico, como solicitudes dirigidas a redes CDN, consulte la [Administración del tráfico de red de Office 365](routing-with-expressroute.md).
  
Este es un vínculo breve que se puede usar para volver: [https://aka.ms/o365cdns](https://aka.ms/o365cdns)
  
## <a name="see-also"></a>Vea también

[Administrar puntos de conexión de Office 365](https://docs.microsoft.com/en-us/office365/enterprise/managing-office-365-endpoints)

[Direcciones URL e intervalos de direcciones IP de Office 365](https://go.microsoft.com/fwlink/p/?LinkID=293744)

[Uso de la red de entrega de contenido de Office 365 con SharePoint Online](https://docs.microsoft.com/en-us/office365/enterprise/use-office-365-cdn-with-spo)

[Centro de confianza de Microsoft](https://www.microsoft.com/trustcenter)