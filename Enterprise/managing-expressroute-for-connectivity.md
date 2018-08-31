---
title: Administrar ExpressRoute para la conectividad de Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/13/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365_Setup
search.appverid:
- MET150
- BCS160
ms.assetid: e4468915-15e1-4530-9361-cd18ce82e231
description: ExpressRoute para Office 365 ofrece una ruta de acceso alternativo de enrutamiento para llegar a muchos servicios de Office 365 sin necesidad de todo el tráfico a egreso a internet. Aunque aún es necesaria la conexión a internet para Office 365, las rutas específicas que se anuncia a Microsoft a través de BGP en su red realizar el circuito ExpressRoute directo preferido a menos que hay otros valores de configuración en la red. Las tres áreas comunes que es posible que desea configurar para administrar este enrutamiento incluyen prefijo filtrado, seguridad y cumplimiento de normas.
ms.openlocfilehash: 5345c4067f4ecf9b1b1bc1a0ad20d6e1f5273f65
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542760"
---
# <a name="managing-expressroute-for-office-365-connectivity"></a>Administrar ExpressRoute para la conectividad de Office 365

ExpressRoute para Office 365 ofrece una ruta de acceso alternativo de enrutamiento para llegar a muchos servicios de Office 365 sin necesidad de todo el tráfico a egreso a internet. Aunque aún es necesaria la conexión a internet para Office 365, las rutas específicas que se anuncia a Microsoft a través de BGP en su red realizar el circuito ExpressRoute directo preferido a menos que hay otros valores de configuración en la red. Las tres áreas comunes que es posible que desea configurar para administrar este enrutamiento incluyen prefijo filtrado, seguridad y cumplimiento de normas.
  
> [!NOTE]
> Microsoft puede cambiar cómo se revisa el dominio de enrutamiento de Microsoft Peering para ExpressRoute de Azure. Iniciar el 31 de julio de 2017, todos los clientes de Azure ExpressRoute pueden habilitar Microsoft Peering directamente desde la consola administrativa de Azure o a través de PowerShell. Después de habilitar Microsoft Peering, cualquier cliente puede crear filtros de ruta para recibir los anuncios de rutas BGP para las aplicaciones de contratación del cliente de Dynamics 365 (anteriormente conocidos como CRM Online). Los clientes que necesitan ExpressRoute de Azure para Office 365 deben obtener la revisión de Microsoft antes de que pueden crear filtros de ruta para Office 365. Póngase en contacto con su equipo de Account de Microsoft para obtener más información acerca de cómo solicitar una revisión para habilitar ExpressRoute de Office 365. Las suscripciones no autorizadas intenta crear filtros de ruta para Office 365 recibirá un [mensaje de error](https://support.microsoft.com/kb/3181709)
  
## <a name="prefix-filtering"></a>Prefijo de filtrado

Microsoft recomienda que los clientes aceptan todas las rutas BGP tal y como se ha anunciado de Microsoft, las rutas proporcionadas debe llevar a cabo un proceso de revisión y validación riguroso quitar ninguna ventaja a exigentes se ha agregado. ExpressRoute ofrece forma nativa los controles recomendados como propiedad de prefijo IP, la integridad y escala - con ninguna ruta entrante filtrado en el lado del cliente.
  
Si necesita una validación adicional de la propiedad de la ruta a través de interconexión pública de ExpressRoute, puede comprobar las rutas advertidas respecto de la lista de todos los prefijos de IPv4 e IPv6 IP que representan los [intervalos IP públicas de Microsoft](https://www.microsoft.com/download/details.aspx?id=53602). Estos intervalos de cubrir el espacio de direcciones completo de Microsoft y cambian con poca frecuencia, que proporciona un conjunto de intervalos que se filtrará confiable que también proporciona protección adicional a los clientes que preocupan que no son de Microsoft que pertenecen las rutas de una pérdida en sus entorno. En el caso de que hay un cambio, se realizarán en el 1 del mes y el número de versión en la sección **Detalles** de la página cambiará cada vez que se actualiza el archivo.
  
Existen varias razones para evitar el uso de los [intervalos de direcciones IP y URL de Office 365](https://aka.ms/o365endpoints) para generar las listas de filtros de prefijo. Como los siguientes:
  
- Los prefijos de Office 365 IP debe llevar a cabo una gran cantidad de cambios con frecuencia.

- La dirección IP y URL de Office 365 rangos están diseñados para administrar firewall permiten listas y la infraestructura de Proxy, el enrutamiento no.

- Los intervalos de direcciones IP y URL de Office 365 no abordan otros servicios de Microsoft que pueden estar en el ámbito de las conexiones de ExpressRoute.

| |
|**Opción**|**Complejidad**|**Control de cambios**|
|:-----|:-----|:-----|
|Aceptar todas las rutas de Microsoft  <br/> |**Baja:** Atención al cliente se basa en los controles de Microsoft para asegurarse de que todas las rutas pertenecen correctamente.  <br/> |Ninguno  <br/> |
|Propiedad de Microsoft de filtro supernets  <br/> |**Medio:** Cliente implementa prefijo resumida listas de filtros para permitir que sólo Microsoft que pertenecen las rutas.  <br/> |Deben asegurarse de los clientes que se reflejan las actualizaciones poco frecuentes en filtros de rutas.  <br/> |
|Filtrar rangos IP de Office 365  <br/> [!CAUTION] Se recomienda no
|**Alta:** Cliente filtra las rutas basándose en los prefijos de Office 365 IP definidos.  <br/> |Los clientes deben implementar un proceso de administración de cambios eficaz para obtener las actualizaciones mensuales.  <br/> [!CAUTION]Esta solución requiere cambios significativos. Cambios que no se implementa en tiempo probablemente tendrá como resultado una interrupción del servicio.   |

Conectarse a Office 365 utilizando ExpressRoute de Azure se basa en anuncios BGP de subredes IP específicas que representan las redes donde se implementan los extremos de Office 365. Debido a la naturaleza global de Office 365 y el número de servicios que hacen que Office 365, los clientes a menudo tienen una necesidad para administrar los anuncios que se aceptan en su red. Si está interesado con el número de prefijos anunciado en su entorno, la característica de [la Comunidad BGP](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099) permite filtrar los anuncios a un conjunto específico de servicios de Office 365. Esta característica está ahora en la vista previa.
  
Independientemente de cómo administrar los anuncios de rutas BGP procedentes de Microsoft, no tener cualquier exposición especial a los servicios de Office 365 en comparación con conexión a Office 365 a través de un solo circuito de internet. Microsoft mantiene la seguridad, cumplimiento y los niveles de rendimiento independientemente del tipo de circuito que un cliente usa para conectarse a Office 365.
  
### <a name="security"></a>Seguridad

Microsoft recomienda mantener sus propios controles de perímetro de red y de seguridad para las conexiones que se iba a y desde ExpressRoute pública e interconexión de Microsoft, que incluye las conexiones a y desde los servicios de Office 365. Controles de seguridad deben ser en lugar de las solicitudes de red que viajan saliente desde la red a la red de Microsoft, así como entrante de red de Microsoft en su red.
  
#### <a name="outbound-from-customer-to-microsoft"></a>Salida de cliente a Microsoft
  
Cuando los equipos se conectan a Office 365, se conectan al mismo conjunto de extremos, independientemente de si la conexión se realiza a través de un circuito de ExpressRoute o internet. Independientemente del circuito usado, Microsoft recomienda tratar de servicios de Office 365 como de confianza más que genérico destinos de internet. Los controles de seguridad de salida deben centrarse en los puertos y protocolos para reducir la exposición y minimizar el mantenimiento continuado. La información de puerto requerido está disponible en el artículo de referencia de [los extremos de Office 365](https://aka.ms/o365endpoints) .
  
Para controles agregados, puede utilizar nivel FQDN filtrado dentro de su infraestructura de proxy para restringir o inspeccionar algunas o todas las solicitudes de red destinadas a internet o por Office 365. Mantenimiento de la lista de nombres de dominio completos tal y como se lanzan las características y las ofertas de Office 365 evolucionan requiere más sólida administración de cambios y seguimiento de los cambios a los publicados [extremos de Office 365](https://aka.ms/o365endpoints).
  
> [!CAUTION]
> Microsoft recomienda que no confíe únicamente en los prefijos IP para administrar la seguridad de salida a Office 365.

|**Opción**|**Complejidad**|**Control de cambios**|
|:-----|:-----|:-----|
|Sin restricciones  <br/> |**Baja:** Cliente permite el acceso sin restricciones de salida a Microsoft.  <br/> |Ninguno  <br/> |
|Restricciones de puerto  <br/> |**Baja:** Cliente restringe el acceso de salida a Microsoft por los puertos esperados.  <br/> |Poco frecuentes.  <br/> |
|Restricciones de nombre de dominio completo  <br/> |**Alta:** Cliente restringe el acceso de salida a Office 365 según los FQDN publicados.  <br/> |Cambios mensuales.  <br/> |

#### <a name="inbound-from-microsoft-to-customer"></a>Entrada de Microsoft a cliente
  
Hay varios escenarios opcionales que requieren Microsoft iniciar las conexiones a la red.
  
- ADFS durante la validación de la contraseña para el inicio de sesión.

- [Las implementaciones híbridas de Exchange Server](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx).

- Enviar correo electrónico desde un inquilino de Exchange Online a un host local.

- Enviar correo de SharePoint Online desde SharePoint Online para un host local.

- [SharePoint federados búsqueda híbrida](https://technet.microsoft.com/library/dn197174.aspx).

- [Entornos híbridos de SharePoint BCS](https://technet.microsoft.com/library/dn197239.aspx ).

- [Skype para entornos híbridos de negocio](https://technet.microsoft.com/en-us/library/jj205403.aspx) o [Skype para la federación de negocio](https://technet.microsoft.com/library/skype-for-business-online-federation-and-public-im-conectivity.aspx).

- [Skype para la nube de Business Connector](https://technet.microsoft.com/library/mt605227.aspx ).

Microsoft recomienda que acepte estas conexiones a través de su circuito de internet en lugar de su circuito ExpressRoute para reducir la complejidad. Si su cumplimiento o rendimiento necesita dictar que deben aceptar las conexiones entrantes a través de un circuito ExpressRoute, se recomienda el uso de un firewall o el proxy inverso para delimitar las conexiones aceptadas. Puede usar los [extremos de Office 365](https://aka.ms/o365endpoints) para averiguar los nombres de dominio completos de la derecha y prefijos IP.
  
### <a name="compliance"></a>Cumplimiento

No dependen de la ruta de acceso de enrutamiento que usar para cualquiera de los controles de cumplimiento de normas. Independientemente de si se conecta a servicios de Office 365 a través de un circuito ExpressRoute o internet, no cambiarán nuestros controles de cumplimiento de normas. Debe revisar el cumplimiento de normas diferente y niveles de certificación de seguridad para Office 365 averiguar la mejor opción para satisfacer las necesidades de su organización.
  
Éste es un vínculo corto que puede usar para volver:[https://aka.ms/manageexpressroute365](https://aka.ms/manageexpressroute365)
  
## <a name="related-topics"></a>Temas relacionados

[Redes de entrega de contenido](content-delivery-networks.md)
  
[Direcciones URL e intervalos de direcciones IP de Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Administración de extremos de Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Aprendizaje de Azure ExpressRoute para Office 365](https://channel9.msdn.com/series/aer)
