---
title: Planificación de los certificados SSL de terceros para Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 10/24/2017
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
ms.assetid: b48cdf63-07e0-4cda-8c12-4871590f59ce
description: 'Resumen: describe los certificados SSL necesarios para Exchange local e híbrido, SSO con AD FS, servicios de Exchange Online y servicios Web Exchange.'
ms.openlocfilehash: 1746cf5059ba83e225e4a2d55c8eebc082366362
ms.sourcegitcommit: bdd0083dc9dc62994de29421a1f4056ebe27f15f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "29952476"
---
# <a name="plan-for-third-party-ssl-certificates-for-office-365"></a>Planificación de los certificados SSL de terceros para Office 365

 **Resumen:** Describe los certificados SSL necesarios para Exchange local y híbrido, SSO con AD FS, servicios de Exchange Online y servicios Web de Exchange. 
  
Para cifrar las comunicaciones entre los clientes y el entorno de Office 365, certificados de capa de sockets seguros (SSL) de otro fabricante deben instalarse en los servidores de infraestructura.

||
|:-----|
| En este artículo forma parte de la [planeación de la red y ajuste del rendimiento de Office 365](https://aka.ms/tune).|
   
Necesitará certificados para los siguientes componentes de Office 365:
  
- Exchange local
    
- Inicio de sesión único (SSO) (para los servidores de federación de Servicios de federación de Active Directory (AD FS) y servidores proxy de federación de AD FS)
    
- Servicios de Exchange Online, como detección automática, Outlook en cualquier lugar y servicios Web de Exchange
    
- Servidor híbrido de Exchange
    
## <a name="certificates-for-exchange-on-premises"></a>Certificados de Exchange local

Para obtener información general acerca de cómo usar certificados digitales para asegurar la comunicación entre la organización de Exchange local y Exchange Online, vea el artículo de TechNet [Comprender los requisitos de certificado](https://go.microsoft.com/fwlink/p/?LinkID=243657).
  
## <a name="certificates-for-single-sign-on"></a>Certificados para inicio de sesión único

Para proporcionar a los usuarios con una único inicio de sesión experiencia simplificada que incluye seguridad sólida, los certificados que se muestra en la siguiente tabla son necesarios en los servidores de federación o el proxy de servidor de federación. En la tabla siguiente se centra en los servicios de federación de Active Directory (AD FS), también tenemos obtener más información sobre el [uso de proveedores de identidad de terceros](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-fed-compatibility).
  
||||
|:-----|:-----|:-----|
|**Tipo de certificado** <br/> |**Descripción** <br/> |**Lo que necesita hacer antes de implementar** <br/> |
|**Certificado SSL (también denominado certificado de autenticación de servidor)** <br/> |Es un certificado SSL estándar que se usa para asegurar las comunicaciones entre servidores de federación, clientes y equipos proxy de servidores de federación.  <br/> |AD FS requiere un certificado SSL. De forma predeterminada, AD FS usa el certificado SSL que está configurado para el sitio Web predeterminado en Internet Information Services (IIS).<br/> El nombre de sujeto del certificado SSL se usa para determinar el nombre de servicio de federación (FS) para cada instancia de AD FS que implemente. Considere la posibilidad de elegir un nombre de sujeto para cualquier nueva entidad de certificación (CA)-emitido certificados que mejor representa el nombre de su compañía u organización a Office 365. Este nombre debe ser enrutables a Internet.<br/>**Precaución:** AD FS requiere que este certificado SSL no tenga ningún nombre corto sujeto (nombre corto).          <br/> **Recomendación:** Debido a que este certificado debe ser de confianza por los clientes de AD FS, se recomienda que use un certificado SSL emitido por una entidad de certificación pública (de terceros) o por una entidad de certificación subordinada a una raíz de confianza públicos; Por ejemplo, VeriSign o Thawte.  <br/> |
|**Certificado de firma de tokens** <br/> |Se trata de un certificado X.509 estándar que se usa para firmar de forma segura todos los tokens que emite el servidor de federación y que Office 365 acepta y valida.  <br/> |El certificado de firma de tokens debe contener una clave privada que se encadena a una raíz de confianza en el FS. De forma predeterminada, AD FS crea un certificado autofirmado. Sin embargo, según las necesidades de su organización, puede cambiar este certificado para un certificado emitido por entidad emisora de certificados mediante el complemento Administración de AD FS.<br/>**Precaución:** El certificado de firma de tokens es fundamental para la estabilidad de la FS. Si se cambia el certificado, Office 365 debe recibir una notificación del cambio. Si no se proporciona la notificación, los usuarios no pueden iniciar sesión en sus ofertas de servicio de Office 365.<br/>**Recomendación:** Se recomienda que use el certificado autofirmado de firma de tokens que se genera mediante AD FS. Al hacerlo, administra este certificado de forma predeterminada. Por ejemplo, cuando este certificado está a punto de caducar, AD FS generará un nuevo certificado autofirmado.<br/> |
   
Los servidores proxy de federación necesitan el certificado que se describe en la tabla siguiente.
  
||||
|:-----|:-----|:-----|
|**Tipo de certificado** <br/> |**Descripción** <br/> |**Lo que necesita hacer antes de implementar** <br/> |
|Certificado SSL  <br/> |Es un certificado SSL estándar que se usa para asegurar las comunicaciones entre un servidor de federación, un servidor proxy de servidores de federación y equipos clientes de Internet.  <br/> |Este certificado SSL debe estar enlazado al sitio Web predeterminado en IIS para poder ejecutar correctamente el Asistente para la configuración de Proxy de servidor de federación de AD FS.  <br/> Este certificado debe tener el mismo nombre de sujeto que el certificado SSL configurado en el servidor de federación en la red corporativa.  <br/> **Recomendación:** Se recomienda usar el mismo certificado de autenticación de servidor configurado en el servidor de federación al que se conecta este servidor proxy de federación.  <br/> |
   
## <a name="certificates-for-autodiscover-outlook-anywhere-and-active-directory-synchronization"></a>Certificados para detección automática, Outlook en cualquier lugar y sincronización de Active Directory

Sus externo servidores orientados a Exchange 2013, Exchange 2010, Exchange 2007 y acceso de cliente de Exchange 2003 (clases) requieren un certificado SSL de terceros para las conexiones seguras de servicios de sincronización de detección automática, Outlook en cualquier lugar y Active Directory. Puede que ya tenga este certificado instalado en su entorno local.
  
## <a name="certificate-for-an-exchange-hybrid-server"></a>Certificado para un servidor Exchange híbrido

Su externo servidor híbrido de Exchange o los servidores requieren un certificado SSL de terceros para la conectividad segura con el servicio de Exchange Online. Debe obtener este certificado desde su proveedor SSL de terceros.
  
## <a name="office-365-certificate-chains"></a>Cadenas de certificados de Office 365

Este artículo describe los certificados que se debe instalar en su infraestructura. Para obtener más información sobre los certificados instalados en nuestros servidores de Office 365, vea [Cadenas de certificados de Office 365](https://support.office.com/article/0c03e6b3-e73f-4316-9e2b-bf4091ae96bb).
  

