---
title: Preguntas más frecuentes a redes de vídeo de Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/13/2016
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
description: El repositorio de vídeo de Office 365 y servicios de transmisión simplifican almacenar y transmitir los vídeos dentro de la organización. Hay una gran cantidad de mucha información acerca de Office 365 vídeo; estas preguntas más frecuentes de red está diseñada para responder a las preguntas más comunes alrededor de ancho de banda de planeación, cifrado y cómo el servicio aprovecha las redes de entrega de contenido (CDN).
ms.openlocfilehash: bea9838277b5752e4c9905162c0e8525e8aded04
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542771"
---
# <a name="office-365-video-networking-frequently-asked-questions"></a>Preguntas más frecuentes a redes de vídeo de Office 365

El repositorio de vídeo de Office 365 y servicios de transmisión simplifican almacenar y transmitir los vídeos dentro de la organización. Hay una gran cantidad de [información acerca de Office 365 vídeo](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50); estas preguntas más frecuentes de red está diseñada para responder a las preguntas más comunes alrededor de ancho de banda de planeación, cifrado y cómo el servicio aprovecha [las redes de entrega de contenido (CDN)](https://support.office.com/article/Content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f).
  
Si ya no tienen una comprensión de lo que sucede cuando se carga un vídeo o reproducirse, eche un vistazo a este vídeo se coloque juntos, [lo que ocurre con un archivo de vídeo cuando se cargan en vídeo de Office 365](https://www.youtube.com/watch?v=HXSZ0jYBKlM).
  
## <a name="what-are-the-office-365-video-bandwidth-requirements"></a>¿Cuáles son los requisitos de ancho de banda de vídeo de Office 365?

Hay un numerosos [formatos de vídeo compatibles](https://support.office.com/article/dd1af01c-fd8e-4640-b17b-93ee02b9b817) que se pueden cargar a Office 365. Cada archivo de vídeo, a continuación, se codifica a un formato estándar con varias calidades diferentes de vídeo para la reproducción. Vídeo de Office 365 usa adaptable velocidad de bits de transmisión por secuencias para seleccionar la mejor calidad de reproducción de vídeo en función del ancho de banda de red disponible y el tamaño del Reproductor de vídeo. Para ello, el Reproductor solicita inicialmente la calidad de reproducción más baja. El servicio, a continuación, comienza a enviar segmentos de vídeo de 2 segundos para el Reproductor de vídeo. El Reproductor puede solicitar a continuación, según la rapidez se entrega cada segmento de calidad de reproducción mayores o menores.
  
La velocidad de bits adaptable transmisión por secuencias hace todo esto en segundo plano mientras se reproduce el vídeo con la menor cantidad de almacenamiento en búfer o una interrupción. Durante la reproducción de vídeo, el Reproductor de vídeo permite que el Visor de reemplazar manualmente la calidad de la reproducción automática, para seleccionar una calidad de reproducción de vídeo específico.
  
Aquí es una tabla rápida que se describe los requisitos de red para cada una de las características de reproducción de vídeo. El ancho de banda mínimo por persona necesaria para reproducir un vídeo es 802Kbps.
  
|||
|:-----|:-----|
|**Calidad de la reproducción** <br/> |**Velocidad de la red** <br/> |
|288p  <br/> |802kbps  <br/> |
|360p  <br/> |1.2 Mbps  <br/> |
|p 576  <br/> |2.5 Mbps  <br/> |
|720p  <br/> |3.8 Mbps  <br/> |

([Volver al principio](office-365-video-networking-faq.md))
  
## <a name="how-do-cdns-help-video-playback"></a>¿Cómo ayuda las CDN a la reproducción de vídeo?

Si varias personas de la misma organización dentro de la misma ubicación geográfica se transmisión por secuencias del mismo video(s), las CDN almacenará una copia de estos vídeos en una ubicación más cerca de región geográfica. Con el vídeo almacenados, o en caché en la ubicación más cercana, cada persona transmite el vídeo desde la ubicación más cercana a ellos en lugar de una ubicación aún más ausente. Vídeo de Office 365 usa servicios de medios de Azure para administrar lo que se almacena en caché en la CDN de Azure y durante cuánto tiempo. Servicios de medios Azure puede usar cualquiera de las [ubicaciones de CDN de Azure](https://azure.microsoft.com/documentation/articles/cdn-pop-locations/) para almacenar en caché fragmentos de vídeo y los manifiestos de unos días. Si las personas de su organización continuarán en los vídeos en caché permanecen en la memoria caché. Si no tiene acceso a uno el vídeo durante varios días, el vídeo va a finalmente colocar quitarse de la memoria caché. La próxima vez que un usuario intenta ver el vídeo se una vez más almacena en caché en la ubicación de CDN más cercana.
  
Todas las personas que intenta ver el vídeo mientras el contenido se almacena en caché una beneficios CDN cercanos desde el vídeo que se va a más cerca y en la mayoría de los casos menos saltos, como ausente. Esto mejora la velocidad de reproducción de vídeo; Sin embargo, no cambia el requisito de red para reproducir el vídeo.
  
> [!NOTE]
> Hay algunas circunstancias, como nuestro límite de capacidad que se ha alcanzado, donde se puede quitar el vídeo antes de que se ha alcanzado el tres días.
  
([Volver al principio](office-365-video-networking-faq.md))
  
## <a name="can-i-cache-the-videos-locally-for-faster-playback"></a>¿Memoria caché de los vídeos localmente para reproducción más rápido?

Sí. Office 365 no impedir usen una CDN local o un proxy de almacenamiento en caché para incorporar vídeo o contenido de Office 365 en su red local para un acceso más rápido. Hay varias maneras de implementar una solución de almacenamiento en memoria caché local en la red, el método más común consiste en utilizar una solución de proxy que almacena en caché contenido localmente. Una vez que un servidor proxy o privada CDN ha almacenado en caché los fragmentos de vídeo y los manifiestos, las solicitudes futuras para los archivos que se enrutan a través del proxy o CDN privada son procedente de la memoria caché local y no procedente de una ubicación de internet. Considere la posibilidad de simultaneidad de reproducción de vídeo, la capacidad y el ancho de banda de red durante la planeación de una solución similar.
  
([Volver al principio](office-365-video-networking-faq.md))
  
## <a name="how-videos-are-encrypted-and-secured"></a>¿Cómo vídeos se cifrada y protegidos?

Vídeo de Office 365 sabe lo importante que es mantener los datos seguros y privados. [Centro de confianza de la Office 365](https://products.office.com/business/office-365-trust-center-cloud-computing-security) describe nuestro compromiso con la privacidad y seguridad de su contenido. Con la reproducción de vídeo, la velocidad es importante para una buena experiencia; Sin embargo, nos no poner en peligro la seguridad o privacidad a cambio de velocidad. Aquí es cómo se dar cabida a la velocidad, seguridad y privacidad.
  
Cuando usted o alguien de su organización carga un vídeo nuevo, que el vídeo es transcodificación, cifrado con cifrado AES-128 y almacena en los servicios de medios de Azure. Esto significa que los vídeos se cifran en tránsito y en reposo.
  
Cuando una persona de su organización intenta ver un vídeo nuevo, siga estos pasos:
  
1. Pregunte SharePoint Online si tienen permiso para ver el vídeo.

2. SharePoint Online usa los permisos de archivo para determinar si la persona puede ver el vídeo.

3. Si tienen permiso, SharePoint Online recupera un token de Azure para poner en el Reproductor de vídeo.

4. El Reproductor de vídeo, a continuación, utiliza el token para solicitar la clave de descifrado de Azure.

5. Con la clave de descifrado de mano, el Reproductor de vídeo es capaz de transmitir el vídeo.

![O365 Reproducción de vídeo](media/9d3c6e76-151d-48a3-a30e-ba8dd07db0b7.png)
  
([Volver al principio](office-365-video-networking-faq.md))
  
## <a name="what-are-the-requirements-to-playback-office-365-video"></a>¿Cuáles son los requisitos para la reproducción de vídeo de Office 365?

Vídeo de Office 365 admite sistemas operativos y exploradores web son los mismos que los requisitos de SharePoint Online en [requisitos del sistema de Office 365](https://support.office.com/article/Office-365-system-requirements-719254c0-2671-4648-9c84-c6a3d4f3be45). Dependiendo de qué sistema operativo y web configuración de explorador que tiene determinará las necesidades específicas del Reproductor de vídeo. Aquí tiene más información sobre [los requisitos de reproducción de vídeo](https://support.office.com/article/ca1cc1a9-a615-46e1-b6a3-40dbd99939a6).
  
([Volver al principio](office-365-video-networking-faq.md))
  
## <a name="i-cant-get-office-365-video-to-work-where-should-i-start"></a>No se puede obtener Office 365 vídeo para que funcione, ¿dónde debo empezar?

Solución de problemas de conectividad a Office 365 vídeo implica la solución de problemas de la red, su ISP(s) y su configuración de Office 365. El primer punto de inicio es el panel de estado de servicio. Esto le indicará que de vídeo de Office 365 está teniendo un problema o no. Si todo lo que tiene un aspecto atractivo existe, le presentamos algunos recursos adicionales que le ayudarán a.
  
- Asegúrese de que puede conectarse a los [extremos de la red necesarios para el vídeo de Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).

- Comprobar la conectividad de red con nuestra [Guía de solución de problemas de red de Office 365](https://support.office.com/article/Office-365-performance-tuning-and-troubleshooting-Admin-and-IT-Pro-1492cb94-bd62-43e6-b8d0-2a61ed88ebae).

- Vea nuestros [procedimientos recomendados para usar Office 365 en una red lenta](https://support.office.com/article/Best-practices-for-using-Office-365-on-a-slow-network-fd16c8d2-4799-4c39-8fd7-045f06640166).

- Buscar [Ayuda acerca de la configuración de vídeo de Office 365](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50).

([Volver al principio](office-365-video-networking-faq.md))
  
## <a name="office-365-video-resources"></a>Recursos de vídeo de Office 365

Evaluar el tema y deje un comentario para hacernos saber si se ha atendido sus preguntas o si aún está buscando respuestas. Aquí es algunos de nuestros otros recursos que le ayudarán a implementar y usar Office 365 vídeo correctamente:
  
[Buscar ayuda acerca de la configuración de vídeo de Office 365](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50).
  
[Cumplir vídeo de Office 365](https://support.office.com/article/Meet-Office-365-Video-ca1cc1a9-a615-46e1-b6a3-40dbd99939a6)
  
[Crear y administrar un canal de vídeo de Office 365](https://support.office.com/article/Create-and-manage-a-channel-in-Office-365-Video-1fede4cc-13c0-435a-b585-e7fbf1c83bb2)
  
[Administrar su portal de vídeo de Office 365](https://support.office.com/article/Manage-your-Office-365-Video-portal-c059465b-eba9-44e1-b8c7-8ff7793ff5da)
  
[Formatos de vídeo que funcionan en vídeo de Office 365](https://support.office.com/article/Video-formats-that-work-in-Office-365-Video-dd1af01c-fd8e-4640-b17b-93ee02b9b817)
  
([Volver al principio](office-365-video-networking-faq.md))
  
Éste es un vínculo corto que puede usar para volver:[https://aka.ms/video365networkfaq](https://aka.ms/video365networkfaq)
