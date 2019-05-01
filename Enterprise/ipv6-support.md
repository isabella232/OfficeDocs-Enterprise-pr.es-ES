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
description: 'Resumen: describe la compatibilidad de IPv6 en componentes de Microsoft Office 365 y en ofertas de administración pública de Office 365.'
ms.openlocfilehash: 82af5c7659b3c16c8e92b45b65b6868a404eca23
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487757"
---
# <a name="ipv6-support-in-office-365-services"></a>Compatibilidad con IPv6 en servicios de Office 365

 **Resumen**: describe la compatibilidad de IPv6 en componentes de Microsoft Office 365 y en ofertas de administración pública de Office 365.
  
Office 365 admite tanto IPv6 como IPv4; sin embargo, no todas las características de Office 365 están completamente habilitadas con IPv6. Esto significa que debe usar tanto IPv4 como IPv6 para conectarse a Office 365. Si va a filtrar el tráfico saliente a Office 365, la lista completa de direcciones IPv6 admitidas por Office 365 puede encontrarse en el artículo [office 365 URL e intervalos de direcciones IP](urls-and-ip-address-ranges.md). Una vez configurada la red y se permiten las direcciones IPv6 adecuadas, puede descargar el [plan de pruebas de IPv6 de Office 365](https://go.microsoft.com/fwlink/?LinkId=293447) desde el centro de descarga de Microsoft.
  
||
|:-----|
| Este artículo forma parte de la planeación de [red y el ajuste del rendimiento de Office 365](https://aka.ms/tune).|

## <a name="ipv6-support-in-office-365-subscription-service"></a>Compatibilidad con IPv6 en el servicio de suscripción de Office 365

### <a name="exchange-online-and-ipv6"></a>Exchange Online e IPv6

Si el programa que usa para conectarse a Exchange Online es compatible con IPv6, usará IPv6 de forma predeterminada tanto en las redes cableadas como en las inalámbricas. Si desea controlar las comunicaciones con Exchange Online, use los intervalos de direcciones IP en [Office 365 URL e intervalos de direcciones IP](urls-and-ip-address-ranges.md).
  
### <a name="sharepoint-online-and-ipv6"></a>SharePoint Online e IPv6

 **Office 365 Government G1/G3/G4/K1** Si el programa que usa para conectarse a SharePoint Online admite IPv6, intentará usar IPv6 de forma predeterminada.
  
 **Nube de varios inquilinos pública** Microsoft habilita IPv6 de SharePoint Online en su solicitud. Debe proporcionar las direcciones IP de CIDR expresadas para la infraestructura DNS de su organización. Tenga en cuenta que esta infraestructura DNS no se puede compartir con otras organizaciones para que IPv6 esté habilitado para su inquilino. Después de habilitar IPv6, si el programa que usa para conectarse a SharePoint Online es compatible con IPv6, usa IPv6 de forma predeterminada.
  
Si el programa que usa para conectarse a SharePoint Online admite IPv6, usará IPv6 de forma predeterminada en las redes cableadas e inalámbricas. Si quiere controlar las comunicaciones a SharePoint Online, use los intervalos de direcciones IP en [Office 365 URL e intervalos de direcciones IP](urls-and-ip-address-ranges.md).
  
 **Office 365 Government G1/G3/G4/K1** Si el programa que usa para conectarse a SharePoint Online admite IPv6, intentará usar IPv6 de forma predeterminada.
  
### <a name="skype-for-business-and-ipv6"></a>Skype empresarial e IPv6

Tenga en cuenta que el IPv6 no es compatible con Skype empresarial y ya no se puede habilitar.
  
### <a name="exchange-online-protection-and-ipv6"></a>Exchange Online Protection e IPv6

Exchange Online Protection (EOP) admite IPv6 si la transmisión se produce a través del Protocolo de seguridad de la capa de transporte. Para el intervalo de EOP, use [Office 365 URL e intervalos de direcciones IP](urls-and-ip-address-ranges.md).
  
### <a name="ipv6-support-for-office-365-government-offerings"></a>Compatibilidad con IPv6 para las ofertas de Office 365 Government

Office 365 IPv6 Support for Government offers se ajusta al Office of Management and Budget (OMB) memorándum para los responsables de información de los departamentos y agencias ejecutivos, así como la adopción del Protocolo de Internet versión 6 (IPv6 Memorándum. [Microsoft Office 365 para administración pública](https://go.microsoft.com/fwlink/p/?LinkId=325414) es un servicio multiempresa que almacena datos gubernamentales de Estados Unidos en una nube de la comunidad segregada. Como otras ofertas de Office 365, proporciona servicios de productividad y colaboración, como Exchange Online, Skype empresarial, SharePoint Online y Office Professional Plus. 

Las ofertas de Microsoft Office 365 Government solo se aplican a 2013 y versiones posteriores. Para obtener más información acerca de las ofertas de Office 365 Government, consulte el [anuncio de office 365 para la administración pública: una nube de la comunidad de administración pública de Estados Unidos](https://go.microsoft.com/fwlink/p/?LinkId=325414). El tráfico internacional en las regulaciones de brazos (ITAR) es un conjunto de regulaciones del gobierno de Estados Unidos que controlan la exportación y la importación de artículos y servicios relacionados con la defensa en la lista de municiones de [Estados Unidos (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415). 

Microsoft Office 365 para empresas proporciona servicios de hospedaje dedicados para soluciones de productividad de Microsoft que admiten los requisitos de seguridad, privacidad y cumplimiento normativo para agencias federales de Estados Unidos que requieran la seguridad de la información federal Certificación de administración (FISMA) y entidades comerciales sujetas a ITAR.
  
## <a name="things-to-consider-when-using-ipv6-and-office-365"></a>Aspectos que se deben tener en cuenta al usar IPv6 y Office 365

Le recomendamos que no deshabilite IPv6. Para obtener más información, vea este [artículo de orientación](https://support.microsoft.com/help/929852/guidance-for-configuring-ipv6-in-windows-for-advanced-users). Para determinar qué versiones IP se usan en la red, tenga en cuenta lo siguiente:
  
- Si la presentación del comando **ipconfig** en el símbolo del sistema contiene filas denominadas "dirección IPv6" o "dirección IPv6 temporal", tiene IPv6 en su entorno.

- Si todas las direcciones IPv6 empiezan por "fe80" y se corresponden con las filas denominadas "dirección IPv6 local de vínculo", no tiene IPv6 en su entorno.

Estas consideraciones podrían aplicarse a su red:
  
- El servicio de suscripción pública no admite la compra mediante tarjeta de crédito a través de IPv6. Esto no se aplica a la nube de la comunidad de administración pública (GCC) porque los gobiernos tienen licencias de Enterprise Agreement (EA).

- IPv6 no admite algunos escenarios de Rights Management Services (RMS).

- IPv6 no es compatible con BlackBerry ® Enterprise Server (BES) porque BlackBerry no es compatible con IPv6.

- Si usa los servicios de Federación de Active Directory (AD FS) con Office 365, no se admite la publicidad del punto de conexión de red de AD FS en Office 365 con IPv6. No debe incluir registros AAAA en la entrada DNS de AD FS cuando use Exchange Online. 

Este es un vínculo breve que se puede usar para volver: [https://aka.ms/o365ip6](https://aka.ms/o365ip6)
  
## <a name="see-also"></a>Vea también

[Mapa de ruta de aprendizaje de IPv6](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/gg250710(v%3dws.10))
  
[Guía de supervivencia de IPv6](https://social.technet.microsoft.com/wiki/contents/articles/1728.ipv6-survival-guide.aspx)
