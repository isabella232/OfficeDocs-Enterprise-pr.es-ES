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
ms.openlocfilehash: 294bf256df48f4c9c846346d7b303ba452b689ec
ms.sourcegitcommit: 1c3aa0654336acec14098241f785ea1d8c6caf50
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "42890349"
---
# <a name="external-domain-name-system-records-for-office-365"></a>Registros externos del Sistema de nombres de dominio para Office 365

 **Resumen:** Lista de referencia de los registros DNS para usar cuando se planee una implementación de Office 365.
  
|||
|:-----|:-----|
|![Dominio](media/e05b1c78-1df0-4200-ba40-6e26b7ead68f.png)|**¿Desea ver una lista personalizada de registros DNS para su organización de Office 365? ** Puede [encontrar la información que necesita para crear los registros DNS de Office 365](https://support.office.microsoft.com/article/Gather-the-information-you-need-to-create-Office-365-DNS-records-77f90d4a-dc7f-4f09-8972-c1b03ea85a67) para su dominio en Office 365.  <br/> **¿Necesita ayuda paso a paso para agregar estos registros al host DNS de su dominio, como GoDaddy o eNom? ** [Encontrará vínculos con instrucciones paso a paso para muchos de los hosts DNS](https://go.microsoft.com/fwlink/?LinkId=286745). <br/>  **¿Busca la lista de referencia para su propia implementación personalizada?** La siguiente lista debe usarse como referencia para la implementación personalizada de Office 365. Tendrá que seleccionar los registros que se aplican a su organización y completar los valores adecuados. <br/> **Regrese a ** [Planeamiento de red y ajuste del rendimiento para Office 365](https://aka.ms/tune).  <br/> |

A menudo, los registros SPF y MX son los más difíciles de averiguar. Hemos actualizado nuestras indicaciones sobre los registros SPF al final de este artículo. Lo importante que debe recordar es que _solo puede tener un único registro SPF para su dominio_. Puede tener varios registros MX. Sin embargo, a menudo es lo que causa problemas de entrega de correo. Tener un registro único de MX que dirige el correo electrónico a un sistema de correo elimina muchos de estos potenciales problemas.
  
Las secciones siguientes están organizadas por servicio en Office 365. Para ver una lista personalizada de los registros DNS de Office 365 para su dominio, inicie sesión en Office 365 y [Recopile la información necesaria para crear registros DNS de Office 365](https://support.office.com/article/77f90d4a-dc7f-4f09-8972-c1b03ea85a67).
  
## <a name="external-dns-records-required-for-office-365-core-services"></a>Registros DNS externos necesarios para Office 365 (servicios principales)
<a name="BKMK_ReqdCore"> </a>

Todos los clientes de Office 365 deben agregar dos registros a su DNS externo. El primer registro CNAME garantiza que Office 365 pueda dirigir las estaciones de trabajo para autenticarlas con la plataforma de identidad adecuada. El segundo registro que se necesita verifica que el usuario es el propietario del nombre de dominio.
  
||||
|:-----|:-----|:-----|
|**Registro DNS** <br/> |**Finalidad** <br/> |**Valor para usar** <br/> |
|**CNAME** <br/> **(Conjunto de aplicaciones)** <br/> |Utilizado por Office 365 para dirigir la autenticación hacia la plataforma de identidad correcta. [Más información](https://go.microsoft.com/fwlink/p/?LinkId=322005) <br/> **Nota:** Este CNAME solo se aplica a Office 365 operado por 21Vianet.   |**Alias:** msoid  <br/> **Objetivo: ** clientconfig.partner.microsoftonline-p.net.cn  <br/> |
|**TXT** <br/> **(Verificación de dominio)** <br/> |Utilizado por Office 365 para verificar que el usuario es el propietario del dominio. No afecta a nada más.  <br/> |**Host:** @ (o, para algunos proveedores de hospedaje DNS, su nombre de dominio)  <br/> **Valor de TXT:** _Una cadena de texto proporcionada por _ Office 365  <br/> El asistente de configuración de dominio de **Office 365** proporciona los valores que utiliza para crear este registro.  <br/> |


## <a name="external-dns-records-required-for-email-in-office-365-exchange-online"></a>Registros DNS externos necesarios para el correo electrónico en Office 365 (Exchange Online)
<a name="BKMK_ReqdCore"> </a>

El correo electrónico en Office 365 requiere distintos registros. Los tres registros principales que todos los clientes deberían usar son los registros de detección automática, MX y SPF.
  
- **El registro de detección automática** permite que los equipos cliente busquen Exchange de manera automática y configuren el cliente correctamente.

- **El registro de MX**le avisa a otros sistemas del correo a donde tiene que enviar el correo electrónico hacia su dominio.**Nota:** Al cambiar el correo electrónico a Office 365, después de actualizar el registro MX del dominio, Todo correo electrónico que se envíe al dominio empezará a llegar a Office 365.  
¿Desea cambiar solo algunas direcciones de correo electrónico a Office 365? Usted puede[controlar Office 365 con algunas direcciones de correo electrónico en el dominio personalizado](https://support.office.com/article/39cee536-6a03-40cf-b9c1-f301bb6001d7).

- **El registro TXT para SPF** se usa por los sistemas de correo electrónico del destinatario para validar que el servidor que envía el correo electrónico sea uno que aprueba. Esto ayuda a evitar problemas como la suplantación de identidad y phishing a través del correo electrónico. Consulte los [registros DNS externos necesarios para SPF](external-domain-name-system-records.md#BKMK_SPFrecords) en este artículo para que le resulte más fácil comprender qué se debe incluir en el registro.

Los clientes de correo electrónico que utilizan federación de Exchange también tendrán un registro CNAME y TXT adicional en la parte inferior de la tabla.
  
||||
|:-----|:-----|:-----|
|**Registro DNS** <br/> |**Finalidad** <br/> |**Valor para usar** <br/> |
|**CNAME** <br/> **(Exchange Online)** <br/> |Ayuda a los clientes de Outlook a conectarse fácilmente al servicio Exchange Online con el servicio de detección automática. La detección automática encuentra automáticamente el host de Exchange Server correcto y configura Outlook para los usuarios.  <br/> |**Alias:** Autodiscover  <br/> **Destino:** autodiscover.outlook.com  <br/> |
|**MX** <br/> **(Exchange Online)** <br/> |Envía el correo entrante para su dominio al servicio de Exchange Online de Office 365.  <br/> [!NOTE] Una vez que el correo fluye a Exchange Online, debe quitar los registros MX que hacen referencia a su antiguo sistema.   |**Dominio:** por ejemplo, contoso.com  <br/> **Servidor de correo electrónico de destino:**\<token MX\>.mail.protection.outlook.com  <br/> **Preferencia/Prioridad:** Inferior a todos los registros MX (garantiza el envío de correo a Exchange Online) - por ejemplo, 1 o “baja”  <br/>  Para buscar su \<token MX\>, siga estos pasos:  <br/>  Inicie sesión en Office 365, vaya a la Administración de Office 365 \> Dominios.  <br/>  En la columna Acción para su dominio, elija Corregir problemas.  <br/>  En la sección de registros MX, elija ¿Qué puedo corregir?  <br/>  Siga las instrucciones de esta página para actualizar el registro MX.  <br/> [¿Qué es una prioridad de MX?](https://go.microsoft.com/fwlink/p/?LinkId=396471) <br/> |
|**SPF (TXT)** <br/> **(Exchange Online)**  <br/> |Ayuda a evitar que otros usen su dominio para enviar correo no deseado u otros correos electrónicos malintencionados. Los registros de la estructura de directivas de remitente (SPF) trabajan para identificar los servidores que estén autorizados para enviar correo electrónico desde su dominio.  <br/> |[Registros DNS externos necesarios para SPF](external-domain-name-system-records.md#BKMK_SPFrecords) <br/> |
|**TXT** <br/> **(Federación de Exchange)** <br/> |Utilizado para la federación de Exchange para la implementación híbrida.  <br/> |**Registro 1 TXT:** por ejemplo, contoso.com y texto hash asociado, generado de forma personalizada y de prueba de dominio (por ejemplo, Y96nu89138789315669824)  <br/> **Registro 2 TXT:** por ejemplo, exchangedelegation.contoso.com y texto hash asociado, generado de forma personalizada y de prueba del dominio (por ejemplo Y3259071352452626169)  <br/> |
|**CNAME** <br/> **(Federación de Exchange)** <br/> |Ayuda a los clientes de Outlook a conectarse fácilmente al servicio de Exchange Online con el servicio de detección automática cuando su empresa utilice la federación de Exchange. La detección automática encuentra automáticamente el host de Exchange Server correcto y configura para los usuarios.  <br/> |**Alias:** por ejemplo, Autodiscover.service.contoso.com  <br/> **Destino:** autodiscover.outlook.com  <br/> |


## <a name="external-dns-records-required-for-skype-for-business-online"></a>Registros DNS externos necesarios para Skype Empresarial Online
<a name="BKMK_ReqdCore"> </a>

Existen pasos específicos que realizar cuando se usan [direcciones URL y direcciones IP de Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO) para asegurarse de que la red esté correctamente configurada.

> [!NOTE]
> Estos registros DNS también se aplican a Teams, especialmente en un escenario híbrido de Teams y en Skype Empresarial Online, donde pueden producirse ciertos problemas de federación.
  
||||
|:-----|:-----|:-----|
|**Registro DNS** <br/> |**Finalidad** <br/> |**Valor para usar** <br/> |
|**SRV** <br/> **(Skype Empresarial Online)** <br/> |Permite a su dominio de Office 365 compartir características de mensajería instantánea (MI) con clientes externos al habilitar la federación SIP. Obtenga más información sobre [direcciones URL e intervalos de direcciones IP de Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO).  <br/> |**Servicio:** sipfederationtls  <br/> **Protocolo:** TCP  <br/> **Prioridad:** 100  <br/> **Peso:** 1  <br/> **Puerto:** 5061  <br/> **Objetivo:** sipfed.online.lync.com  <br/> **Nota:** Si el firewall o el servidor proxy bloquean las búsquedas de SRV en un DNS externo, debería agregar este registro al registro DNS interno.   |
|**SRV** <br/> **(Skype Empresarial Online)** <br/> |Lo usa Skype Empresarial para coordinar el flujo de información entre los clientes de Lync.  <br/> |**Servicio:** sip  <br/> **Protocolo:** TLS  <br/> **Prioridad:** 100  <br/> **Peso:** 1  <br/> **Puerto:** 443  <br/> **Objetivo:** sipdir.online.lync.com  <br/> |
|**CNAME** <br/> **(Skype Empresarial Online)** <br/> |Lo usa el cliente de Lync para ayudar a encontrar el servicio de Skype Empresarial Online e iniciar sesión.  <br/> |**Alias:** sip  <br/> **Objetivo:** sipdir.online.lync.com  <br/> Para obtener más información, consulte[direcciones URL e rangos de direcciones IP de Office 365 ](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO).  <br/> |
|**CNAME** <br/> **(Skype Empresarial Online)** <br/> |Lo usa el cliente móvil de Lync para ayudar a encontrar el servicio de Skype Empresarial Online e iniciar sesión.  <br/> |**Alias:** lyncdiscover  <br/> **Objetivo:** webdir.online.lync.com  <br/> |

## <a name="external-dns-records-required-for-sharepoint-online"></a>Registros DNS externos necesarios para SharePoint Online
<a name="BKMK_ReqdCore"> </a>

SharePoint Online solo requiere un registro DNS si su organización lo usa para enviar correo electrónico a personas externas. En este caso, asegúrese de que ha configurado los [registros DNS externos necesarios para SPF](external-domain-name-system-records.md#BKMK_SPFrecords) para que el correo pueda entregarse.
  
## <a name="external-dns-records-required-for-office-365-single-sign-on"></a>Registros DNS externos necesarios para el inicio de sesión único en Office 365
<a name="BKMK_ReqdCore"> </a>

||||
|:-----|:-----|:-----|
|**Registro DNS** <br/> |**Finalidad** <br/> |**Valor para usar** <br/> |
|**Host (A)** <br/> |Se usa para el inicio de sesión único (SSO). Proporciona el punto de conexión para que los usuarios no locales (y los locales, si lo desea) se conecten a los proxy del servidor de federación de Servicios de federación de Active Directory (AD FS) o a la IP virtual equilibrada (VIP).  <br/> |**Destino:** por ejemplo, sts.contoso.com  <br/> |

## <a name="external-dns-records-required-for-spf"></a>Registros DNS externos necesarios para SPF
<a name="BKMK_SPFrecords"> </a>

> [!IMPORTANT]
>  SPF está diseñado para ayudar a evitar la suplantación de identidad, pero existen técnicas de suplantación de identidad contra las que SPF no puede ofrecer protección. Para obtener protección contra estas, una vez que haya configurado SPF, también debe configurar DKIM y DMARC para Office 365. Vea [Use DKIM to validate outbound email sent from your domain in Office 365](https://technet.microsoft.com/library/mt695945%28v=exchg.150%29.aspx) para comenzar. A continuación, vea [Use DMARC to validate email in Office 365](https://technet.microsoft.com/library/mt734386%28v=exchg.150%29.aspx).
  
Los registros SPF son registros TXT que ayudan a evitar que otros usen su dominio para enviar correo no deseado o correos electrónicos malintencionados. Los registros de la estructura de directivas de remitente (SPF) identifican los servidores autorizados para enviar correo electrónico desde su dominio.
  
Solo puede tener un registro SPF (es decir, un registro TXT que defina SPF) para su dominio. Ese registro único puede tener diferentes inclusiones, pero las búsquedas DNS totales que se producen no pueden ser superiores a 10 (esto ayuda a evitar los ataques por servicio denegado). Vea la tabla y los siguientes ejemplos para ayudarle a crear o actualizar los valores de registro SPF adecuados para su entorno.
  
### <a name="structure-of-an-spf-record"></a>Estructura de un registro SPF

Todos los registros SPF constan de tres partes: la declaración de que es un registro SPF, los dominios y las direcciones IP desde donde se deberían enviar los correos electrónicos y una regla de cumplimiento. Las tres son necesarias en un registro SPF válido. Este es un ejemplo de un registro SPF común para Office 365 cuando usa solo correo electrónico de Exchange Online:
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com -all
```

Un sistema de correo electrónico que recibe un correo electrónico de su dominio examina el registro SPF, y si el servidor de correo electrónico que ha enviado el mensaje era un servidor de Office 365, se acepta el mensaje. Si el servidor que ha enviado el mensaje era su sistema de correo antiguo o un sistema malicioso de Internet, por ejemplo, se puede producir un error en la comprobación SPF y el mensaje no se entregará. Comprueba cómo esto ayuda a evitar los mensajes de suplantación de identidad y de phishing.
  
### <a name="choose-the-spf-record-structure-you-need"></a>Elegir la estructura de registro SPF que necesita

Para los escenarios donde no solo utiliza el correo electrónico de Exchange Online para Office 365 (por ejemplo, si también usa correo electrónico procedente de SharePoint Online), use la siguiente tabla para determinar qué incluir en el valor del registro.
  
> [!NOTE]
> Si tiene un escenario complejo que incluye, por ejemplo, servidores de correo electrónico perimetral para administrar el tráfico de correo electrónico en el firewall, tendrá que configurar un registro SPF más detallado. Obtenga información sobre cómo: [Configurar registros SPF en Office 365 para ayudar a evitar la suplantación de identidad](https://go.microsoft.com/fwlink/?LinkId=787656). Si desea obtener más información sobre cómo funciona SPF con Office 365, consulte [Cómo Office 365 usa el marco de directivas de remitente (SPF) para ayudar a evitar la suplantación de identidad](https://go.microsoft.com/fwlink/?LinkId=787065).
  
|||||
|:-----|:-----|:-----|:-----|
||Si usa...  <br/> |Finalidad  <br/> |Agregar estos includes  <br/> |
|1  <br/> |Todos los sistemas de correo electrónico (obligatorio)  <br/> |Todos los registros SPF comienzan con este valor  <br/> |v=spf1  <br/> |
|2  <br/> |Exchange Online (común)  <br/> |Usar solo con Exchange Online  <br/> |include:spf.protection.outlook.com  <br/> |
|3  <br/> |SharePoint Online y Exchange Online (común)  <br/> |Usar con Exchange Online y SharePoint Online  <br/> |include:sharepointonline.com  <br/> |
|4  <br/> |Sistema de correo electrónico de terceros (menos común)  <br/> ||include:\<sistema de correo electrónico,por ejemplo mail.contoso.com\>  <br/> |
|5  <br/> |Sistema de correo local (menos común)  <br/> |Usar si usa Exchange Online Protection o Exchange Online además de otro sistema de correo  <br/> |ip4:\<0.0.0.0\>  <br/> ip6:\< : \>  <br/> include:\<mail.contoso.com\>  <br/> El valor entre corchetes (\<\>) debe corresponder a otros sistemas de correo que enviarán correo electrónico por su dominio.  <br/> |
|6  <br/> |Todos los sistemas de correo electrónico (obligatorio)  <br/> ||-all  <br/> |

### <a name="example-adding-to-an-existing-spf-record"></a>Ejemplo: Agregar a un registro SPF existente
<a name="bkmk_addtospf"> </a>

Si ya tiene un registro SPF, necesitará agregar o actualizar los valores para Office 365. Por ejemplo, imagine que este es su registro SPF existente para contoso.com:
  
``` dns
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:spf.protection.outlook.com -all
```

Ahora está actualizando su registro SPF para Office 365, por ejemplo, para incluir correo electrónico que se origina desde SharePoint Online. Editará el registro actual para que tenga un solo registro SPF que incluya los valores que necesita. Para Office 365, "sharepointonline.com" en un registro SPF incluye correo electrónico de Exchange Online (Outlook) y SharePoint Online, de manera que reemplace el valor original de "spf.protection.outlook.com".
  
Correcto:
  
``` dns
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:sharepointonline.com -all
```

Incorrecto:
  
``` dns
Record 1:
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:spf.protection.outlook.com -all
Record 2:
Values: v=spf1 include:sharepointonline.com -all
```

### <a name="more-examples-of-common-spf-values"></a>Más ejemplos de valores SPF comunes
<a name="bkmk_addtospf"> </a>

Si usa el conjunto completo de Office 365 y utiliza MailChimp para enviar correos electrónicos de marketing en su nombre, su registro SPF en contoso.com podría ser similar al siguiente, que usa las filas 1, 3, 4 y 6 de la tabla anterior. Recuerde que las filas 1 y 6 son necesarias y "sharepointonline.com" incluye correo electrónico tanto de Exchange (Outlook) como de SharePoint.
  
``` dns
TXT Name @
Values: v=spf1 include:sharepointonline.com include:servers.mcsv.net -all
```

Como alternativa, si tiene una configuración híbrida de Exchange donde se envía correo electrónico desde el sistema de correo local y desde Office 365, el registro SPF en contoso.com podría ser similar al siguiente:
  
``` dns
TXT Name @
Values: v=spf1 include:sharepointonline.com include:mail.contoso.com -all
```

A continuación se muestran algunos ejemplos comunes que le pueden ayudar a adaptar el registro SPF existente cuando agrega su dominio a Office 365 para correo electrónico. Si tiene un escenario complejo que incluye, por ejemplo, servidores de correo electrónico perimetral para administrar el tráfico de correo electrónico en el firewall, tendrá que configurar un registro SPF más detallado. Obtenga información sobre cómo: [Configurar registros SPF en Office 365 para ayudar a evitar la suplantación de identidad](https://go.microsoft.com/fwlink/?LinkId=787656).
  
Este es un vínculo breve que se puede usar para volver: [https://aka.ms/o365edns](https://aka.ms/o365edns)
