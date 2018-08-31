---
title: Redes de entrega de contenido
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/26/2018
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
description: Use esta información para obtener más información acerca de redes de distribución de contenido (CDN) y cómo Office 365 las aprovecha. Las CDN ayudan a mantener Office 365 rápidas y confiables para los usuarios finales. Con las CDN, servicios de nube como Office 365 descargar rápidamente contenido genérico, como iconos, en Explorador de los usuarios cuando usa el servicio a través de un cliente web.
ms.openlocfilehash: bcbab3256a0c1ce601abaf3f8b80e998db4bcece
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542961"
---
# <a name="content-delivery-networks"></a>Redes de entrega de contenido

Use esta información para obtener más información acerca de redes de distribución de contenido (CDN) y cómo Office 365 las aprovecha. Las CDN ayudan a mantener Office 365 rápidas y confiables para los usuarios finales. Con las CDN, servicios de nube como Office 365 descargar rápidamente contenido genérico, como iconos, en Explorador de los usuarios cuando usa el servicio a través de un cliente web.
  
 **Realizar una copia de head para** [Planeación de la red y ajuste del rendimiento de Office 365](https://aka.ms/tune).
  
## <a name="how-should-i-set-up-my-network-so-that-cdns-work-best-with-office-365"></a>¿Cómo debo configurar mi red para que las CDN funcionen mejor con Office 365?

Si está planeando [la conectividad de red a Office 365](network-connectivity.md), es útil entender cómo funcionan las CDN. También es importante comprender que no se puede filtrar la conectividad con los CDN por dirección IP. Ofrecemos una lista de esfuerzo procedimientos de IP para los servicios dentro de Office 365, como Exchange Online. Obtenga más información acerca de nuestras recomendaciones para [los extremos de administración de Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a).
  
## <a name="how-do-cdns-make-services-work-faster"></a>¿Cómo hacen las CDN que los servicios funcionen con mayor rapidez?

Descargar cosas comunes como iconos y otra vez puede tardar hasta ancho de banda de red que mejor se puede usar para la descarga de contenido personal importante, al igual que el correo electrónico o documentos. Dado que Office 365 usa una arquitectura que incluye las CDN, los iconos, las secuencias de comandos y otro contenido genérico se puede descargar desde servidores más cerca a los equipos cliente, realizar las descargas más rápido. Esto significa un acceso más rápido a su contenido personal, que se almacena de forma segura en centros de datos de Office 365.
  
## <a name="what-exactly-is-a-cdn"></a>¿Qué es exactamente una CDN?

Se usan las CDN por la mayoría de los servicios de nube de empresa. Servicios de nube como Office 365 con millones de clientes descargar una mezcla de contenido de su propiedad (por ejemplo, mensajes de correo electrónico) y contenido genérico (por ejemplo, los iconos) a la vez. Es más eficaz para colocar imágenes de que todo el mundo utiliza, como iconos, lo más cerca del equipo del usuario como sea posible. Aún, no es práctico para cada servicio de nube crear centros de datos CDN que almacenan este contenido genérico en cada área metropolitana, o incluso en todos los concentradores de Internet principales todo el mundo, por lo que algunas de estas las CDN se comparten.
  
Las CDN pueden ser pública o privada. Las CDN privado se perteneciente y usadas por una sola empresa, y sólo esa compañía las aplicaciones y servicios pueden usar. Se ejecutan las CDN públicas por las compañías que arrendar uso a varias empresas. Dependiendo de dónde se encuentre, puede resultar más eficaz para Office 365 descargar imágenes genéricas para usted desde una CDN que posee Office 365 y se ejecuta, una CDN pública o una combinación de ambas. Independientemente de qué tipo de CDN se usa, los pasos para recuperar los datos son los mismos.
  
1. El cliente solicita datos de Office 365.

2. Office 365 devuelve los datos directamente a su cliente o dirige al cliente para una CDN.

3. Si ya se almacena en caché los datos en la red CDN, el cliente descarga los datos directamente desde la ubicación de CDN más cercana a su cliente en internet.

4. Si no se almacena en caché los datos en la red CDN, el nodo CDN solicita los datos de Office 365 y, a continuación, memoria caché de los datos durante un período de tiempo después de que el cliente de descarga de los datos.

La CDN extraer los archivos y las imágenes desde el centro de datos de Office 365 más cercano y a su vez, su cliente extrae los archivos y las imágenes desde la CDN más cercana. Cuando los usuarios tienen acceso a un servicio de nube, como cuando se lee correo electrónico en Outlook Web App, el explorador del usuario intenta recuperar los archivos y las imágenes desde el centro de datos de Office 365. En lugar de dedicar el tiempo y el ancho de banda de entregar los archivos, Office 365 redirige el explorador a la CDN. La CDN averigua el centro de datos más cercano al explorador del usuario y, mediante el redireccionamiento, descarga las imágenes genéricas desde allí. El uso de esta redirección CDN es rápido y guarda una gran cantidad de tiempo de descarga de los usuarios.
  
## <a name="is-there-a-list-of-all-the-fqdns-that-leverage-cdns"></a>¿Hay una lista de todos los FQDN que aprovechan las CDN?

La lista de nombres de dominio completos y cómo aprovechar el cambio de las CDN con el tiempo, consulte nuestro publicado [página extremos de Office 365](https://go.microsoft.com/fwlink/p/?LinkID=293744) para obtener actualizados en los FQDN más recientes que aprovechan las CDN.
  
## <a name="is-there-a-list-of-all-the-cdns-that-office-365-uses"></a>¿Hay una lista de todas las CDN que usa Office 365?

La CDN en uso por Office 365 es siempre está sujeta a cambios y en muchos casos, hay varios socios CDN configurados en el caso de que uno no está disponible. Los dos CDN más comunes en uso son [Akamai](https://www.akamai.com/us/en/cdn.jsp) y [Microsoft Azure](https://azure.microsoft.com/documentation/services/cdn/). Ambas de estas soluciones CDN tienen un alcance global mejora el alcance del servicio a más esquinas del mundo. El contenido que se almacena allí incluye secuencias de comandos, archivos e imágenes general de Office 365. Por ejemplo, al iniciar sesión en portal.office.com, las imágenes se extraen desde la CDN más cercana para acelerar los tiempos de carga de página. Otros ejemplos incluyen Office 365 ProPlus almacenar los bits de instalación en una CDN para acelerar la cantidad de tiempo que se tarda en descargar la versión más reciente de Office. También es cierto contenido propietario que se almacena en las CDN, como los archivos de vídeo para vídeo de Office 365. Una vez que se carga los vídeos, los archivos se cifran y, a continuación, se almacenan en su formato cifrado con los servicios de Azure Media. Cuando el Reproductor de vídeo de Office 365 recupera el vídeo en primer lugar se caché a la CDN más próxima antes de que se está descargando para acelerar la cantidad de tiempo que se tarda en descargar el vídeo.
  
## <a name="does-office-365-offer-a-cdn-that-i-can-use-for-my-own-files"></a>¿Office 365 ofrece una CDN que puedo usar para mis propios archivos?

¡Sí! La suscripción a Office 365 ahora incluye una CDN que es independiente de Azure que se puede usar específicamente para los activos de SharePoint Online. Para obtener información sobre cómo usar la CDN de Office 365, vea [usar la red de entrega de contenido de Office 365 con SharePoint Online](use-office-365-cdn-with-spo.md).
  
## <a name="can-i-use-my-own-cdn-and-cache-content-on-my-local-network"></a>¿Puedo usar mi propia CDN y memoria caché de contenido en mi red local?

Se está buscando constantemente nuevas formas admitir las necesidades de nuestros clientes y se está explorando actualmente el uso de almacenamiento en caché de soluciones de proxy y otras soluciones CDN local.
  
## <a name="is-my-data-safe"></a>¿Están seguros mis datos?

Echamos mucho cuidado para ayudar a garantizar que se protegen los datos que se ejecuta su negocio. O bien se cifran los elementos almacenados en nuestros asociados de la red de entrega de contenido; como con [Vídeo de Office 365](https://support.office.com/article/2bed67a1-4052-49ff-a4ce-b7e6530eb98e), o no específicos para un cliente; Por ejemplo, los archivos de instalación de Office 365 ProPlus. Head en a través de en el [Centro de confianza de Office 365](https://go.microsoft.com/fwlink/p/?LinkId=397383) para obtener más información acerca de nuestros esfuerzos detallados para proteger su privacidad y los datos.
  
## <a name="how-can-i-secure-my-network-with-all-these-3rd-party-services"></a>¿Cómo puedo proteger mi red con todos estos servicios parte 3ª?

Aprovechamiento de un amplio conjunto de servicios para socios permite a Office 365 escalar y cumplir los requisitos de disponibilidad así como mejorar la experiencia del usuario cuando se usa Office 365. Los servicios de terceros 3ª que Office 365 aprovecha incluyen ambas listas de revocación de certificados; Por ejemplo, crl.microsoft.com o sa.symcb.com y las CDN; Por ejemplo, r3.res.outlook.com. Cada CDN FQDN Office 365 usa es un FQDN personalizado para Office 365, si se envían a un FQDN en la solicitud de Office 365 puede estar seguro de que se controlan el FQDN y el subyacente contenido en esa ubicación.
  
Para los clientes que aún desea segregar solicitudes destinadas a un centro de datos de Microsoft o de Office 365 desde las solicitudes que están destinados a una parte 3ª, hemos escrito una orientación en [los extremos de administración de Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a).
  
## <a name="im-using-azure-expressroute-for-office-365-does-that-change-things"></a>Estoy usando ExpressRoute de Azure para Office 365, cambiar cosas?

[ExpressRoute de Azure para Office 365](azure-expressroute.md) proporciona una conexión dedicada a la infraestructura de Office 365 que se aísla de internet pública. Esto significa que los clientes aún tendrá que conectarse a través de conexiones que no sean ExpressRoute para conectarse a las CDN y otras infraestructuras de Microsoft que no se incluyen explícitamente en la lista de servicios admitidos por ExpressRoute. Para obtener más información acerca de cómo enrutar el tráfico específico, como las solicitudes destinados a las CDN, hacer referencia a la [administración de tráfico de red de Office 365](routing-with-expressroute.md).
  
Éste es un vínculo corto que puede usar para volver:[https://aka.ms/o365cdns](https://aka.ms/o365cdns)
  
## <a name="see-also"></a>Vea también

[Preguntas más frecuentes de los extremos de Office 365](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
