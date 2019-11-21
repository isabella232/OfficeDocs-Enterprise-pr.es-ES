---
title: Planificación de los certificados SSL de terceros para Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.date: 05/15/2019
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: b48cdf63-07e0-4cda-8c12-4871590f59ce
description: 'Resumen: describe los certificados SSL necesarios para Exchange local e híbrido, SSO con AD FS, servicios de Exchange Online y servicios web Exchange.'
ms.openlocfilehash: 74540fb612bd515443912114ebec20cd8ed5e1aa
ms.sourcegitcommit: 6639b0f0171f7552111267a64d6b199755bf34fc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "38756619"
---
# <a name="plan-for-third-party-ssl-certificates-for-office-365"></a>Planificación de los certificados SSL de terceros para Office 365

*Este artículo se aplica tanto a Office 365 Enterprise como a Microsoft 365 Enterprise.*

Para cifrar las comunicaciones entre los clientes y el entorno de Office 365, los certificados de capa de sockets seguros (SSL) de terceros deben estar instalados en los servidores de la infraestructura.

||
|:-----|
| Este artículo forma parte de la [planeación de red y el ajuste del rendimiento de Office 365](https://aka.ms/tune).|
   
Los certificados son necesarios para los siguientes componentes de Office 365:
  
- Implementación local de Exchange
    
- Inicio de sesión único (SSO) (para los servidores de Federación de los servicios de Federación de Active Directory (AD FS) y los proxies del servidor de Federación de AD FS)
    
- Servicios de Exchange Online, como detección automática, Outlook en cualquier lugar y servicios web Exchange
    
- Servidor híbrido de Exchange
    
## <a name="certificates-for-exchange-on-premises"></a>Certificados para Exchange local

Para obtener información general sobre cómo usar certificados digitales para que la comunicación entre la organización de Exchange local y Exchange online sea segura, consulte el artículo de TechNet [información sobre los requisitos de certificados](https://go.microsoft.com/fwlink/p/?LinkID=243657).
  
## <a name="certificates-for-single-sign-on"></a>Certificados para el inicio de sesión único

Para proporcionar a los usuarios una experiencia de inicio de sesión único simplificada que incluya seguridad robusta, los certificados que se muestran en la tabla siguiente son necesarios en los servidores de Federación o en los proxies del servidor de Federación. La siguiente tabla se centra en los servicios de Federación de Active Directory (AD FS), también tenemos más información sobre el [uso de proveedores de identidades de terceros](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-fed-compatibility).
  
||||
|:-----|:-----|:-----|
|**Tipo de certificado** <br/> |**Descripción** <br/> |**Lo que debe saber antes de implementar** <br/> |
|**Certificado SSL (también denominado certificado de autenticación de servidor)** <br/> |Se trata de un certificado SSL estándar que se usa para proteger las comunicaciones entre servidores de Federación, clientes y equipos proxy de servidor de Federación.  <br/> |AD FS requiere un certificado SSL. De forma predeterminada, AD FS usa el certificado SSL configurado para el sitio web predeterminado en Internet Information Services (IIS).  <br/> El nombre de sujeto de este certificado SSL se usa para determinar el nombre del servicio de Federación (FS) para cada instancia de AD FS que implemente. Considere la posibilidad de elegir un nombre de sujeto para los certificados emitidos por una nueva entidad de certificación (CA) que mejor represente el nombre de su compañía u organización a Office 365. Este nombre debe ser enrutable a Internet.  <br/>**PRECAUCIÓN:** AD FS requiere que este certificado SSL no tenga un nombre de sujeto (nombre corto) sin puntos.          <br/> **Recomendación:** Como este certificado debe ser de confianza para los clientes de AD FS, se recomienda usar un certificado SSL emitido por una entidad de certificación pública (de terceros) o por una CA subordinada a una raíz de confianza pública; por ejemplo, VeriSign o Thawte.  <br/> |
|**Certificado de firma de tokens** <br/> |Se trata de un certificado X. 509 estándar que se usa para firmar de forma segura todos los tokens que emite el servidor de Federación y que Office 365 acepta y valida.  <br/> |El certificado de firma de tokens debe contener una clave privada que encadena a una raíz de confianza en el FS. De forma predeterminada, AD FS crea un certificado autofirmado. Sin embargo, en función de las necesidades de su organización, puede cambiar este certificado por un certificado emitido por una entidad de certificación mediante el complemento Administración de AD FS.  <br/>**PRECAUCIÓN:** El certificado de firma de tokens es crítico para la estabilidad del FS. Si se cambia el certificado, se debe notificar el cambio a Office 365. Si no se proporciona una notificación, los usuarios no pueden iniciar sesión en sus ofertas de servicio de Office 365.<br/>**Recomendación:** Le recomendamos que use el certificado autofirmado de firma de tokens que genera AD FS. Al hacerlo, se administra el certificado de forma predeterminada. Por ejemplo, cuando está a punto de caducar este certificado, AD FS generará un nuevo certificado autofirmado.  <br/> |
   
Los servidores proxy de Federación requieren el certificado que se describe en la tabla siguiente.
  
||||
|:-----|:-----|:-----|
|**Tipo de certificado** <br/> |**Descripción** <br/> |**Lo que debe saber antes de implementar** <br/> |
|certificado SSL  <br/> |Se trata de un certificado SSL estándar que se usa para asegurar las comunicaciones entre un servidor de Federación, un proxy de servidor de Federación y los equipos cliente de Internet.  <br/> |Este certificado SSL debe estar enlazado al sitio web predeterminado de IIS para que el Asistente para la configuración del servidor proxy de Federación de AD FS se pueda ejecutar correctamente.  <br/> Este certificado debe tener el mismo nombre de sujeto que el certificado SSL que se configuró en el servidor de Federación de la red corporativa.  <br/> **Recomendación:** Le recomendamos que use el mismo certificado de autenticación de servidor que está configurado en el servidor de Federación al que se conecta este proxy de servidor de Federación.  <br/> |
   
## <a name="certificates-for-autodiscover-outlook-anywhere-and-active-directory-synchronization"></a>Certificados para la detección automática, Outlook en cualquier lugar y la sincronización de Active Directory

Los servidores de acceso de cliente de Exchange 2013, Exchange 2010, Exchange 2007 e Exchange 2003 (CASs) requieren un certificado SSL de terceros para las conexiones seguras para la detección automática, Outlook en cualquier lugar y los servicios de sincronización de Active Directory. Puede que ya tenga instalado este certificado en su entorno local.
  
## <a name="certificate-for-an-exchange-hybrid-server"></a>Certificado para un servidor híbrido de Exchange

Los servidores o servidores híbridos de Exchange con conexión externa requieren un certificado SSL de terceros para la conectividad segura con el servicio de Exchange Online. Debe obtener este certificado de su proveedor de SSL de terceros.
  
## <a name="office-365-certificate-chains"></a>Cadenas de certificados de Office 365

En este artículo se describen los certificados que puede que necesite instalar en su infraestructura. Para obtener más información sobre los certificados instalados en nuestros servidores de Office 365, consulte [office 365 Certificate Chains](https://support.office.com/article/0c03e6b3-e73f-4316-9e2b-bf4091ae96bb).
  
## <a name="see-also"></a>Vea también

[Información general de Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
