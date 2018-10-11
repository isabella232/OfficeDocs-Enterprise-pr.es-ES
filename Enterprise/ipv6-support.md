---
title: Compatibilidad con IPv6 en servicios de Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/10/2018
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
ms.assetid: c08786fb-298e-437c-8222-dab7625fc815
description: 'Resumen: Describe la compatibilidad de IPv6 en los componentes de Microsoft Office 365 y en las ofertas de gobierno de Office 365.'
ms.openlocfilehash: ed06f1eac3c6a3d631445db1d623bd25c62a309c
ms.sourcegitcommit: ae7f2087d51698d3c5ef371888278544a7046205
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/10/2018
ms.locfileid: "25493835"
---
# <a name="ipv6-support-in-office-365-services"></a>Compatibilidad con IPv6 en servicios de Office 365

 **Resumen**: describe la compatibilidad de IPv6 en los componentes de Microsoft Office 365 y en las ofertas de gobierno de Office 365.
  
Office 365 es compatible con IPv6 y IPv4; Sin embargo, no todas las características de Office 365 totalmente se habilitan con IPv6. Esto significa que debe usar IPv4 e IPv6 para conectarse a Office 365. Si se van a filtrar el tráfico saliente a Office 365, la lista completa de las direcciones IPv6 que son compatibles con Office 365 puede encontrarse en el artículo de [las direcciones URL de Office 365 y los intervalos de direcciones IP](https://go.microsoft.com/fwlink/?LinkId=293744). Después de la red está configurada y se permiten las direcciones IPv6 adecuadas, puede descargar el [plan de pruebas de IPv6 de Office 365](https://go.microsoft.com/fwlink/?LinkId=293447) desde Microsoft Download Center.
  
||
|:-----|
| En este artículo forma parte de la [planeación de la red y ajuste del rendimiento de Office 365](https://aka.ms/tune).|

## <a name="ipv6-support-in-office-365-subscription-service"></a>Compatibilidad con IPv6 en el servicio de suscripción de Office 365

### <a name="exchange-online-and-ipv6"></a>Exchange Online e IPv6

Si el programa que use para conectarse a Exchange Online admite IPv6, usará IPv6 de forma predeterminada en redes por cable e inalámbricas. Si desea controlar las comunicaciones a Exchange Online, use los intervalos de direcciones IP en [las direcciones URL de Office 365 y los intervalos de direcciones IP](https://go.microsoft.com/fwlink/?LinkId=293744).
  
### <a name="sharepoint-online-and-ipv6"></a>SharePoint Online e IPv6

 **Office 365 gobierno G1/G3/G4/K1** Si el programa que use para conectarse a SharePoint Online admite IPv6, intentará usar IPv6 de forma predeterminada.
  
 **Nube pública de varios inquilino** Microsoft habilita IPv6 en línea de SharePoint en su solicitud. Es necesario que proporcione que la CIDR expresa las direcciones IP para la infraestructura DNS de su organización. Tenga en cuenta que no se puede compartir esta infraestructura DNS por otras organizaciones para IPv6 a habilitarse para el inquilino. Después de habilitar IPv6, si el programa que use para conectarse a SharePoint Online admite IPv6, usa IPv6 de forma predeterminada.
  
Si el programa que use para conectarse a SharePoint Online admite IPv6, usará IPv6 de forma predeterminada en redes por cable e inalámbricas. Si desea controlar las comunicaciones a SharePoint Online, use los intervalos de direcciones IP en [las direcciones URL de Office 365 y los intervalos de direcciones IP](https://go.microsoft.com/fwlink/?LinkId=293744).
  
 **Office 365 gobierno G1/G3/G4/K1** Si el programa que use para conectarse a SharePoint Online admite IPv6, intentará usar IPv6 de forma predeterminada.
  
### <a name="skype-for-business-and-ipv6"></a>Skype para empresas y IPv6

Microsoft va a habilitar IPv6 para Skype para la empresa en su solicitud en la nube de varios inquilino pública y en Office 365 administración pública G1/G3/G4/K1 suscripciones. Una vez está habilitada, si el programa que use para conectarse a Skype para la empresa es compatible con IPv6, usará IPv6 de forma predeterminada. Si desea controlar las comunicaciones Skype para la empresa, use los intervalos de direcciones IP en [las direcciones URL de Office 365 y los intervalos de direcciones IP](https://go.microsoft.com/fwlink/?LinkId=293744).
  
Por favor, tenga en cuenta IPv6 no está disponible en todas las regiones y Microsoft no podrá activarlo para el inquilino en este momento.
  
### <a name="exchange-online-protection-and-ipv6"></a>Protección en línea de Exchange e IPv6

Exchange Online Protection (EOP) es compatible con IPv6, si se produce la transmisión a través del protocolo de seguridad de capa de transporte. El intervalo de elevación de privilegios, use [las direcciones URL de Office 365 y los intervalos de direcciones IP](https://go.microsoft.com/fwlink/?LinkId=293744).
  
### <a name="ipv6-support-for-office-365-government-offerings"></a>Compatibilidad con IPv6 para las ofertas de Office 365 Administración pública

Compatibilidad con IPv6 de Office 365 para las ofertas de gobierno se ajusta a la oficina de administración y memorando Budget (OMB) para directores de información de departamentos ejecutivo y organismos, así como la Federal gobierno adopción de Internet Protocol versión 6 (IPv6 ) memorando. [Microsoft Office 365 para el gobierno](https://go.microsoft.com/fwlink/p/?LinkId=325414) es un servicio de varios inquilino que nos datos gubernamentales almacena en una nube de la Comunidad separadas. Al igual que otras ofertas de Office 365, proporciona servicios de productividad y colaboración, incluido Exchange Online, Skype para la empresa, SharePoint Online y Office Professional Plus. Las ofertas de administración pública de Microsoft Office 365 se aplican sólo para 2013 y versiones posteriores. Para obtener más información acerca de las ofertas de gobierno de Office 365, vea [anunciar Office 365 para el gobierno: A nosotros gobierno nube de la Comunidad](https://go.microsoft.com/fwlink/p/?LinkId=325414). El tráfico de internacional en las normativas de armas (ITAR) es un conjunto de reglamentaciones gubernamentales de Estados Unidos que controlan la exportación e importación de artículos relacionados con la defensa y servicios en la [Lista de municiones de Estados Unidos (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415). Microsoft Office 365 para empresas proporciona servicios de hospedaje dedicados para soluciones de productividad de Microsoft que admiten la seguridad, privacidad y los requisitos de cumplimiento de normativas para nosotros agencias federales que requieren Federal de información de seguridad Certificación de administración (FISMA) y entidades comerciales sujetas a ITAR.
  
## <a name="things-to-consider-when-using-ipv6-and-office-365"></a>Cosas que debe tener en cuenta cuando use IPv6 y Office 365

Se recomienda deshabilitar IPv6. Para obtener más información, vea [IPv6 para Microsoft Windows: preguntas más frecuentes](https://go.microsoft.com/fwlink/p/?LinkId=325418). Para determinar qué versiones IP se usan en la red, tenga en cuenta lo siguiente:
  
- Si la presentación del comando IPConfig en el símbolo del sistema contiene filas con el nombre "Dirección IPv6" o "Dirección IPv6 temporal", que dispone de IPv6 en su entorno.

- Si todas las direcciones IPv6 comienzan por "fe80" y se corresponden con las filas denominadas "Dirección IPv6 de vínculo Local", que no dispone de IPv6 en su entorno.

Pueden que estas consideraciones se apliquen a su red:
  
- El servicio de suscripción pública no admite compras con tarjeta de crédito a través de IPv6. Esto no se aplica a la nube de comunidad de administración pública (GCC) porque la administración pública dispone de licencias de Contrato Enterprise (EA).

- IPv6 no admite algunos escenarios de Rights Management Services (RMS).

- IPv6 no admite BlackBerry® Enterprise Server (BES) porque BlackBerry no es compatible con IPv6.

- Si usa los servicios de federación de Active Directory (AD FS) con Office 365, anuncie su extremo de la red de AD FS a Office 365 usa IPv6 no se admite. No debe incluir registros AAAA en la entrada de DNS de AD FS al usar Exchange Online. 

Este es un vínculo breve que se puede usar para volver: [https://aka.ms/o365ip6](https://aka.ms/o365ip6)
  
## <a name="see-also"></a>Recursos adicionales

[Papel de la posición de la tecnología de Microsoft](https://go.microsoft.com/fwlink/p/?linkid=525743)
  
[V6 y TCP/IP v4](https://go.microsoft.com/fwlink/p/?LinkID=211898)
  
[Guía de supervivencia de IPv6](https://go.microsoft.com/fwlink/p/?LinkID=237480)
