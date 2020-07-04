---
title: Registros externos del Sistema de nombres de dominio para Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/21/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: c0531a6f-9e25-4f2d-ad0e-a70bfef09ac0
description: 'Resumen: Lista de referencia de los registros DNS para usar cuando se planee una implementación de Office 365.'
ms.openlocfilehash: d0804cec4ce2c15345a9c4ddc83525d1961f8db4
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "44996544"
---
# <a name="external-domain-name-system-records-for-office-365"></a>Registros externos del Sistema de nombres de dominio para Office 365

|||
|:-----|:-----|
|![Dominio](media/e05b1c78-1df0-4200-ba40-6e26b7ead68f.png)|**Want to see a customized list of DNS records for your Office 365 organization?** You can [find the info you need to create Office 365 DNS records](https://support.office.microsoft.com/article/Gather-the-information-you-need-to-create-Office-365-DNS-records-77f90d4a-dc7f-4f09-8972-c1b03ea85a67) for your domain in Office 365.  <br/> **Need step-by-step help to add these records at your domain's DNS host, such as GoDaddy or eNom?** [Find links to step-by-step instructions for many popular DNS hosts](https://go.microsoft.com/fwlink/?LinkId=286745). <br/>  **Sticking around to use the reference list for your own custom deployment?** The below list should be used as a reference for your custom Office 365 deployment. You will need to select which records apply to your organization and fill in the appropriate values. <br/> **Regrese a ** [Planeamiento de red y ajuste del rendimiento para Office 365](https://aka.ms/tune).  <br/> |

Often the SPF and MX records are the hardest to figure out. We've updated our SPF records guidance at the end of this article. The important thing to remember is that _you can only have a single SPF record for your domain_. You can have multiple MX records; however, that can cause problems for mail delivery. Having a single MX record that directs email to one mail system removes many potential problems.
  
The sections below are organized by service in Office 365. To see a customized list of the Office 365 DNS records for your domain, sign in to Office 365 and [Gather the information you need to create Office 365 DNS records](https://support.office.com/article/77f90d4a-dc7f-4f09-8972-c1b03ea85a67).
  
## <a name="external-dns-records-required-for-office-365-core-services"></a>Registros DNS externos necesarios para Office 365 (servicios principales)
<a name="BKMK_ReqdCore"> </a>

Every Office 365 customer needs to add two records to their external DNS. The first CNAME record ensures that Office 365 can direct workstations to authenticate with the appropriate identity platform. The second required record is to prove you own your domain name.
  
||||
|:-----|:-----|:-----|
|**Registro DNS** <br/> |**Finalidad** <br/> |**Valor para usar** <br/> |
|**CNAME** <br/> **(Conjunto de aplicaciones)** <br/> |Used by Office 365 to direct authentication to the correct identity platform. [More information](https://go.microsoft.com/fwlink/p/?LinkId=322005) <br/> **Nota:** Este CNAME solo se aplica a Office 365 operado por 21Vianet.   |**Alias:** msoid  <br/> **Objetivo: ** clientconfig.partner.microsoftonline-p.net.cn  <br/> |
|**TXT** <br/> **(Verificación de dominio)** <br/> |Used by Office 365 to verify only that you own your domain. It doesn't affect anything else.  <br/> |**Host:** @ (o, para algunos proveedores de hospedaje DNS, su nombre de dominio)  <br/> **Valor de TXT:** _Una cadena de texto proporcionada por _ Office 365  <br/> El asistente de configuración de dominio de **Office 365** proporciona los valores que utiliza para crear este registro.  <br/> |


## <a name="external-dns-records-required-for-email-in-office-365-exchange-online"></a>Registros DNS externos necesarios para el correo electrónico en Office 365 (Exchange Online)
<a name="BKMK_ReqdCore"> </a>

Email in Office 365 requires several different records. The three primary records that all customers should use are the Autodiscover, MX, and SPF records.
  
- **El registro de detección automática** permite que los equipos cliente busquen Exchange de manera automática y configuren el cliente correctamente.

- **The MX record** tells other mail systems where to send email for your domain. **Note:** When you change your email to Office 365, by updating your domain's MX record, ALL email sent to that domain will start coming to Office 365.  
¿Desea cambiar solo algunas direcciones de correo electrónico a Office 365? Usted puede[controlar Office 365 con algunas direcciones de correo electrónico en el dominio personalizado](https://support.office.com/article/39cee536-6a03-40cf-b9c1-f301bb6001d7).

- **El registro TXT para SPF** se usa por los sistemas de correo electrónico del destinatario para validar que el servidor que envía el correo electrónico sea uno que aprueba. Esto ayuda a evitar problemas como la suplantación de identidad y phishing a través del correo electrónico. Consulte los [registros DNS externos necesarios para SPF](external-domain-name-system-records.md#BKMK_SPFrecords) en este artículo para que le resulte más fácil comprender qué se debe incluir en el registro.

Los clientes de correo electrónico que utilizan federación de Exchange también tendrán un registro CNAME y TXT adicional en la parte inferior de la tabla.
  
||||
|:-----|:-----|:-----|
|**Registro DNS** <br/> |**Finalidad** <br/> |**Valor para usar** <br/> |
|**CNAME** <br/> **(Exchange Online)** <br/> |Helps Outlook clients to easily connect to the Exchange Online service by using the Autodiscover service. Autodiscover automatically finds the correct Exchange Server host and configures Outlook for users.  <br/> |**Alias:** Autodiscover  <br/> **Destino:** autodiscover.outlook.com  <br/> |
|**MX** <br/> **(Exchange Online)** <br/> |Envía el correo entrante para su dominio al servicio de Exchange Online de Office 365.  <br/> [!NOTE] Una vez que el correo fluye a Exchange Online, debe quitar los registros MX que hacen referencia a su antiguo sistema.   |**Dominio:** por ejemplo, contoso.com  <br/> **Servidor de correo electrónico de destino:** \<MX token\> . mail.protection.outlook.com  <br/> **Preferencia/Prioridad:** Inferior a todos los registros MX (garantiza el envío de correo a Exchange Online) - por ejemplo, 1 o “baja”  <br/>  Para buscar el \<MX token\> , siga estos pasos:  <br/>  Inicie sesión en Office 365, vaya a la Administración de Office 365 \> Dominios.  <br/>  En la columna Acción para su dominio, elija Corregir problemas.  <br/>  En la sección de registros MX, elija ¿Qué puedo corregir?  <br/>  Siga las instrucciones de esta página para actualizar el registro MX.  <br/> [¿Qué es una prioridad de MX?](https://go.microsoft.com/fwlink/p/?LinkId=396471) <br/> |
|**SPF (TXT)** <br/> **(Exchange Online)**  <br/> |Helps to prevent other people from using your domain to send spam or other malicious email. Sender policy framework (SPF) records work by identifying the servers that are authorized to send email from your domain.  <br/> |[Registros DNS externos necesarios para SPF](external-domain-name-system-records.md#BKMK_SPFrecords) <br/> |
|**TXT** <br/> **(Federación de Exchange)** <br/> |Utilizado para la federación de Exchange para la implementación híbrida.  <br/> |**Registro 1 TXT:** por ejemplo, contoso.com y texto hash asociado, generado de forma personalizada y de prueba de dominio (por ejemplo, Y96nu89138789315669824)  <br/> **Registro 2 TXT:** por ejemplo, exchangedelegation.contoso.com y texto hash asociado, generado de forma personalizada y de prueba del dominio (por ejemplo Y3259071352452626169)  <br/> |
|**CNAME** <br/> **(Federación de Exchange)** <br/> |Helps Outlook clients to easily connect to the Exchange Online service by using the Autodiscover service when your company is using Exchange federation. Autodiscover automatically finds the correct Exchange Server host and configures Outlook for your users.  <br/> |**Alias:** por ejemplo, Autodiscover.service.contoso.com  <br/> **Destino:** autodiscover.outlook.com  <br/> |


## <a name="external-dns-records-required-for-skype-for-business-online"></a>Registros DNS externos necesarios para Skype Empresarial Online
<a name="BKMK_ReqdCore"> </a>

Existen pasos específicos que realizar cuando se usan [direcciones URL y direcciones IP de Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO) para asegurarse de que la red esté correctamente configurada.

> [!NOTE]
> Estos registros DNS también se aplican a Teams, especialmente en un escenario híbrido de Teams y en Skype Empresarial Online, donde pueden producirse ciertos problemas de federación.
  
||||
|:-----|:-----|:-----|
|**Registro DNS** <br/> |**Finalidad** <br/> |**Valor para usar** <br/> |
|**SRV** <br/> **(Skype Empresarial Online)** <br/> |Allows your Office 365 domain to share instant messaging (IM) features with external clients by enabling SIP federation. Read more about [Office 365 URLs and IP address ranges](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO).  <br/> |**Servicio:** sipfederationtls  <br/> **Protocolo:** TCP  <br/> **Prioridad:** 100  <br/> **Peso:** 1  <br/> **Puerto:** 5061  <br/> **Objetivo:** sipfed.online.lync.com  <br/> **Nota:** Si el firewall o el servidor proxy bloquean las búsquedas de SRV en un DNS externo, debería agregar este registro al registro DNS interno.   |
|**SRV** <br/> **(Skype Empresarial Online)** <br/> |Lo usa Skype Empresarial para coordinar el flujo de información entre los clientes de Lync.  <br/> |**Servicio:** sip  <br/> **Protocolo:** TLS  <br/> **Prioridad:** 100  <br/> **Peso:** 1  <br/> **Puerto:** 443  <br/> **Objetivo:** sipdir.online.lync.com  <br/> |
|**CNAME** <br/> **(Skype Empresarial Online)** <br/> |Lo usa el cliente de Lync para ayudar a encontrar el servicio de Skype Empresarial Online e iniciar sesión.  <br/> |**Alias:** sip  <br/> **Objetivo:** sipdir.online.lync.com  <br/> Para obtener más información, consulte[direcciones URL e rangos de direcciones IP de Office 365 ](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO).  <br/> |
|**CNAME** <br/> **(Skype Empresarial Online)** <br/> |Lo usa el cliente móvil de Lync para ayudar a encontrar el servicio de Skype Empresarial Online e iniciar sesión.  <br/> |**Alias:** lyncdiscover  <br/> **Objetivo:** webdir.online.lync.com  <br/> |

## <a name="external-dns-records-required-for-office-365-single-sign-on"></a>Registros DNS externos necesarios para el inicio de sesión único en Office 365
<a name="BKMK_ReqdCore"> </a>

||||
|:-----|:-----|:-----|
|**Registro DNS** <br/> |**Finalidad** <br/> |**Valor para usar** <br/> |
|**Host (A)** <br/> |Used for single sign-on (SSO). It provides the endpoint for your off-premises users (and on-premises users, if you like) to connect to your Active Directory Federation Services (AD FS) federation server proxies or load-balanced virtual IP (VIP).  <br/> |**Destino:** por ejemplo, sts.contoso.com  <br/> |

## <a name="external-dns-records-required-for-spf"></a>Registros DNS externos necesarios para SPF
<a name="BKMK_SPFrecords"> </a>

> [!IMPORTANT]
> SPF is designed to help prevent spoofing, but there are spoofing techniques that SPF cannot protect against. In order to protect against these, once you have set up SPF, you should also configure DKIM and DMARC for Office 365. To get started, see [Use DKIM to validate outbound email sent from your domain in Office 365](https://technet.microsoft.com/library/mt695945%28v=exchg.150%29.aspx). Next, see [Use DMARC to validate email in Office 365](https://technet.microsoft.com/library/mt734386%28v=exchg.150%29.aspx).
  
SPF records are TXT records that help to prevent other people from using your domain to send spam or other malicious email. Sender policy framework (SPF) records work by identifying the servers that are authorized to send email from your domain.
  
You can only have one SPF record (that is, a TXT record that defines SPF) for your domain. That single record can have a few different inclusions but the total DNS lookups that result can't be more than 10 (this helps prevent denial of service attacks). See the table and other examples below to help you create or update the right SPF record values for your environment.
  
### <a name="structure-of-an-spf-record"></a>Estructura de un registro SPF

All SPF records contain three parts: the declaration that it is an SPF record, the domains, and IP addresses that should be sending email, and an enforcement rule. You need all three in a valid SPF record. Here's an example of a common SPF record for Office 365 when you use only Exchange Online email:
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com -all
```

Un sistema de correo electrónico que recibe un correo electrónico de su dominio examina el registro SPF, y si el servidor de correo electrónico que ha enviado el mensaje era un servidor de Office 365, se acepta el mensaje. Si el servidor que ha enviado el mensaje era su sistema de correo antiguo o un sistema malicioso de Internet, por ejemplo, se puede producir un error en la comprobación SPF y el mensaje no se entregará. Comprueba cómo esto ayuda a evitar los mensajes de suplantación de identidad y de phishing.
  
### <a name="choose-the-spf-record-structure-you-need"></a>Elegir la estructura de registro SPF que necesita

Para los escenarios donde no solo utiliza el correo electrónico de Exchange Online para Office 365 (por ejemplo, si también usa correo electrónico procedente de SharePoint Online), use la siguiente tabla para determinar qué incluir en el valor del registro.
  
> [!NOTE]
> If you have a complicated scenario that includes, for example, edge email servers for managing email traffic across your firewall, you'll have a more detailed SPF record to set up. Learn how: [Set up SPF records in Office 365 to help prevent spoofing](https://go.microsoft.com/fwlink/?LinkId=787656). You can also learn much more about how SPF works with Office 365 by reading [How Office 365 uses Sender Policy Framework (SPF) to help prevent spoofing](https://go.microsoft.com/fwlink/?LinkId=787065).
  
|||||
|:-----|:-----|:-----|:-----|
||Si usa...  <br/> |Finalidad  <br/> |Agregar estos includes  <br/> |
|1   <br/> |Todos los sistemas de correo electrónico (obligatorio)  <br/> |Todos los registros SPF comienzan con este valor  <br/> |v=spf1  <br/> |
|2   <br/> |Exchange Online (común)  <br/> |Usar solo con Exchange Online  <br/> |include:spf.protection.outlook.com  <br/> |
|3   <br/> |Sistema de correo electrónico de terceros (menos común)  <br/> ||Incluye:\<email system like mail.contoso.com\>  <br/> |
|4   <br/> |Sistema de correo local (menos común)  <br/> |Usar si usa Exchange Online Protection o Exchange Online además de otro sistema de correo  <br/> |ip4:\<0.0.0.0\>  <br/> ip6:\< : : \>  <br/> Incluye:\<mail.contoso.com\>  <br/> El valor entre corchetes (\<\>) debe corresponder a otros sistemas de correo que enviarán correo electrónico por su dominio.  <br/> |
|5   <br/> |Todos los sistemas de correo electrónico (obligatorio)  <br/> ||-all  <br/> |

### <a name="example-adding-to-an-existing-spf-record"></a>Ejemplo: Agregar a un registro SPF existente
<a name="bkmk_addtospf"> </a>

If you already have an SPF record, you'll need to add or update values for Office 365. For example, say your existing SPF record for contoso.com is this:
  
``` dns
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:smtp.adatum.com -all
```

Ahora está actualizando su registro de SPF para Office 365. Editará su registro actual para tener un registro de SPF que incluya los valores que necesita. Para Office 365, "spf.protection.outlook.com".
  
Correcto:
  
``` dns
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:spf.protection.outlook.com include:smtp.adatum.com -all
```

Incorrecto:
  
``` dns
Record 1:
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:smtp.adatum.com -all
Record 2:
Values: v=spf1 include:spf.protection.outlook.com -all
```

### <a name="more-examples-of-common-spf-values"></a>Más ejemplos de valores SPF comunes
<a name="bkmk_addtospf"> </a>

Si usa el conjunto completo de Office 365 y usa MailChimp para enviar correos electrónicos de marketing en su nombre, el registro de SPF en contoso.com puede tener un aspecto similar al siguiente, que usa las filas 1, 3 y 5 de la tabla anterior. Recuerde que se requieren las filas 1 y 5.
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com include:servers.mcsv.net -all
```

Como alternativa, si tiene una configuración híbrida de Exchange donde se envía correo electrónico desde el sistema de correo local y desde Office 365, el registro SPF en contoso.com podría ser similar al siguiente:
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com include:mail.contoso.com -all
```

These are some common examples that can help you adapt your existing SPF record when you add your domain to Office 365 for email. If you have a complicated scenario that includes, for example, edge email servers for managing email traffic across your firewall, you'll have a more detailed SPF record to set up. Learn how: [Set up SPF records in Office 365 to help prevent spoofing](https://go.microsoft.com/fwlink/?LinkId=787656).
  
Este es un vínculo breve que se puede usar para volver: [https://aka.ms/o365edns](https://aka.ms/o365edns)
