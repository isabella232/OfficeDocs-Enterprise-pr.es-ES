---
title: Preguntas más frecuentes sobre redes de vídeo de Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 3/14/2019
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 2bed67a1-4052-49ff-a4ce-b7e6530eb98e
description: El repositorio de vídeo de Office 365 y los servicios de streaming simplifican el almacenamiento y la transmisión de vídeos en la organización. Hay mucha información importante sobre Office 365 video; estas preguntas frecuentes sobre redes están diseñadas para responder las preguntas más comunes sobre la planeación del ancho de banda, el cifrado y cómo el servicio aprovecha las redes de entrega de contenido (CDN).
ms.openlocfilehash: f11bd8baff7c2527287f6e1249ad4dae1928bdd2
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491936"
---
# <a name="office-365-video-networking-frequently-asked-questions"></a>Preguntas más frecuentes sobre redes de vídeo de Office 365

El repositorio de vídeo de Office 365 y los servicios de streaming simplifican el almacenamiento y la transmisión de vídeos en la organización. Hay mucha [información importante sobre Office 365 video](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50); estas preguntas frecuentes sobre redes están diseñadas para responder las preguntas más comunes sobre la planeación del ancho de banda, el cifrado y cómo el servicio aprovecha las [redes de entrega de contenido](content-delivery-networks.md) (CDN).
  
Si aún no tiene un conocimiento exhaustivo de lo que sucede cuando se carga o reproduce un vídeo, consulte este vídeo que hemos realizado juntos, [lo que ocurre con un archivo de vídeo cuando se carga en vídeo de Office 365](https://www.youtube.com/watch?v=HXSZ0jYBKlM).
  
## <a name="what-are-the-office-365-video-bandwidth-requirements"></a>¿Cuáles son los requisitos de ancho de banda de vídeo de Office 365?

Hay varios formatos de [vídeo compatibles](https://support.office.com/article/dd1af01c-fd8e-4640-b17b-93ee02b9b817) que se pueden cargar a Office 365. Cada archivo de vídeo se codifica a un formato estándar con varias cualidades de vídeo distintas para la reproducción. Office 365 vídeo usa streaming de velocidad de bits adaptable para seleccionar la mejor calidad de reproducción de vídeo en función del ancho de banda de red disponible y el tamaño del reproductor de vídeo. Para ello, el reproductor solicita inicialmente la calidad de reproducción más baja. A continuación, el servicio empieza a enviar segmentos de vídeo de 2 segundos al reproductor de vídeo. A continuación, el reproductor puede solicitar una calidad de reproducción mayor o menor según la velocidad de entrega de cada segmento.
  
La transmisión de velocidad de bits adaptable hace todo esto en segundo plano, mientras que el vídeo se reproduce con la menor cantidad de interrupciones o almacenamiento en búfer. Durante la reproducción de vídeo, el reproductor de vídeo permite al espectador anular manualmente la calidad de reproducción automática para seleccionar una calidad de reproducción de vídeo específica.
  
Esta es una tabla rápida que describe los requisitos de red para cada una de las cualidades de reproducción de vídeo. El ancho de banda mínimo por persona necesaria para reproducir un vídeo es de 802Kbps.
  
|||
|:-----|:-----|
|**Calidad de reproducción** <br/> |**Velocidad de red** <br/> |
|288p  <br/> |802Kbps  <br/> |
|360p  <br/> |1,2 Mbps  <br/> |
|576p  <br/> |2,5 Mbps  <br/> |
|720p  <br/> |3,8 Mbps  <br/> |

([Volver al principio](office-365-video-networking-faq.md))
  
## <a name="how-do-content-delivery-networks-cdns-help-video-playback"></a>¿Cómo sirven las redes de entrega de contenido (CDN) para la reproducción de vídeo?

Si varias personas de la misma organización en la misma ubicación geográfica están transmitiendo los mismos vídeos, las CDN almacenarán una copia de estos vídeos en una ubicación más cercana a esa región geográfica. Con el vídeo almacenado, o almacenado en caché en la ubicación más cercana, cada persona transmite el vídeo de la ubicación más cercana a ellos, en lugar de hacerlo desde una ubicación. Office 365 vídeo usa Azure Media Services para administrar lo que se almacena en caché en los CDN de Azure y durante cuánto tiempo. Servicios multimedia de Azure puede usar cualquiera de las ubicaciones de la [red CDN de Azure](https://azure.microsoft.com/documentation/articles/cdn-pop-locations/) para almacenar en caché fragmentos de vídeo y manifiestos durante unos días. Si las personas de su organización continúan viendo los vídeos en caché que permanecerán en la memoria caché. Si nadie obtiene acceso al vídeo durante varios días, el vídeo se perderá finalmente de la memoria caché. La próxima vez que alguien intente ver el vídeo, volverá a almacenarse en caché en la ubicación de la red CDN más cercana.
  
Todos los usuarios que intentan ver el vídeo mientras el contenido se almacena en la caché en una red CDN cercana aprovechan el vídeo más cerca y, en la mayoría de los casos, menos saltos. Esto mejora la velocidad de reproducción de vídeo; sin embargo, no cambia el requisito de red para reproducir el vídeo.
  
> [!NOTE]
> Hay algunas circunstancias, como nuestro límite de capacidad alcanzado, en las que el vídeo puede quitarse antes de que se hayan alcanzado los tres días.
  
([Volver al principio](office-365-video-networking-faq.md))
  
## <a name="can-i-cache-the-videos-locally-for-faster-playback"></a>¿Puedo almacenar los vídeos en caché localmente para una reproducción más rápida?

Sí. Office 365 no le impedirá usar una red CDN local o un proxy de almacenamiento en caché para llevar vídeo u otro contenido de Office 365 a su red local para obtener un acceso más rápido. Hay varias formas de implementar una solución de almacenamiento en caché local en la red, el método más común es usar una solución de proxy que almacene el contenido de forma local. Una vez que un proxy o una red CDN privada ha almacenado en caché los fragmentos de vídeo y los manifiestos, las solicitudes futuras de los archivos que se enrutan a través del proxy o la red CDN privada se extraen de la memoria caché local y no se extraen de una ubicación de Internet. Considere el ancho de banda de red, la capacidad y la simultaneidad de la reproducción de vídeo durante la planeación de una solución como esta.
  
([Volver al principio](office-365-video-networking-faq.md))
  
## <a name="how-videos-are-encrypted-and-secured"></a>¿Cómo se cifran y protegen los vídeos?

Office 365 video sabe lo importante que es mantener los datos protegidos y privados. El [centro de confianza de Microsoft](https://products.office.com/business/office-365-trust-center-welcome) describe nuestro compromiso con la privacidad y la seguridad de su contenido. Con la reproducción de vídeo, la velocidad es importante para una buena experiencia; sin embargo, no ponen en peligro su seguridad o privacidad en Exchange para agilizar la velocidad. Esta es la forma en que se ajusta la velocidad, la seguridad y la privacidad.
  
Cuando usted o alguien de su organización carga un vídeo nuevo, ese vídeo se transcodifica, cifra con cifrado AES-128 y se almacena en servicios multimedia de Azure. Esto significa que los vídeos están cifrados tanto en tránsito como en reposo.
  
Cuando alguien de su organización intenta ver un nuevo vídeo, sigue estos pasos:
  
1. Solicite a SharePoint Online si tiene permiso para ver el vídeo.

2. SharePoint Online usa los permisos de archivo para determinar si la persona puede ver el vídeo.

3. Si están permitidos, SharePoint Online recupera un token de Azure para darle al reproductor de vídeo.

4. A continuación, el reproductor de vídeo usa el token para solicitar la clave de descifrado de Azure.

5. Con la clave de descifrado a mano, el reproductor de vídeo puede transmitir el vídeo.

![Reproducción de vídeo de O365](media/9d3c6e76-151d-48a3-a30e-ba8dd07db0b7.png)
  
([Volver al principio](office-365-video-networking-faq.md))
  
## <a name="what-are-the-requirements-to-playback-office-365-video"></a>¿Cuáles son los requisitos para reproducir vídeo de Office 365?

Office 365 los sistemas operativos compatibles con vídeo y exploradores Web son los mismos que los requisitos de SharePoint Online en [Office 365 del sistema](https://support.office.com/article/Office-365-system-requirements-719254c0-2671-4648-9c84-c6a3d4f3be45). Según la configuración del sistema operativo y del explorador Web que tenga, determinará las necesidades específicas del reproductor de vídeo. Aquí encontrará más información sobre [los requisitos de reproducción de vídeo](https://support.office.com/article/ca1cc1a9-a615-46e1-b6a3-40dbd99939a6).
  
([Volver al principio](office-365-video-networking-faq.md))
  
## <a name="i-cant-get-office-365-video-to-work-where-should-i-start"></a>No puedo conseguir que Office 365 vídeo funcione, ¿dónde debo empezar?

Solución de problemas de conectividad a Office 365 vídeo implica la solución de problemas de la red, los ISP y la configuración de Office 365. El primer punto de partida es el panel de estado del servicio. Esto le dirá que el vídeo de Office 365 tiene un problema o no. Si todo tiene un aspecto excelente, aquí tiene algunos recursos adicionales para ayudarle.
  
- Asegúrese de que puede conectarse a los [puntos de conexión de red necesarios para el vídeo de Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).

- Compruebe la conectividad de red mediante nuestra [Guía de solución de problemas de red de Office 365](https://support.office.com/article/Office-365-performance-tuning-and-troubleshooting-Admin-and-IT-Pro-1492cb94-bd62-43e6-b8d0-2a61ed88ebae).

- Vea nuestros [procedimientos recomendados para usar Office 365 en una red lenta](https://support.office.com/article/Best-practices-for-using-Office-365-on-a-slow-network-fd16c8d2-4799-4c39-8fd7-045f06640166).

- [Busque ayuda sobre la configuración de vídeo de Office 365](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50).

([Volver al principio](office-365-video-networking-faq.md))
  
## <a name="office-365-video-resources"></a>Recursos de vídeo de Office 365

Estos son algunos otros recursos que le ayudarán a implementar y usar Office 365 video correctamente:
  
[Obtener ayuda sobre la configuración de vídeo de Office 365](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50)
  
[Meet Office 365 Video](https://support.office.com/article/Meet-Office-365-Video-ca1cc1a9-a615-46e1-b6a3-40dbd99939a6) (Conozca Office 365 Video)
  
[Crear y administrar un canal en Office 365 video](https://support.office.com/article/Create-and-manage-a-channel-in-Office-365-Video-1fede4cc-13c0-435a-b585-e7fbf1c83bb2)
  

  [Manage your Office 365 Video portal](https://support.office.com/article/Manage-your-Office-365-Video-portal-c059465b-eba9-44e1-b8c7-8ff7793ff5da) (Administrar el portal de Office 365 Video)
  
[Formatos de vídeo que funcionan en Office 365 video](https://support.office.com/article/Video-formats-that-work-in-Office-365-Video-dd1af01c-fd8e-4640-b17b-93ee02b9b817)
  
([Volver al principio](office-365-video-networking-faq.md))
  
Este es un vínculo breve que se puede usar para volver: [https://aka.ms/video365networkfaq](https://aka.ms/video365networkfaq)
