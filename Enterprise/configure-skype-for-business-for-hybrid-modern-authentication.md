---
title: Cómo configurar Skype Empresarial local para usar la autenticación moderna híbrida
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/3/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 522d5cec-4e1b-4cc3-937f-293570717bc6
ms.collection:
- M365-security-compliance
f1.keywords:
- NOCSH
description: La autenticación moderna es un método de administración de identidades que ofrece autenticación y autorización de usuarios más seguras, está disponible para Skype empresarial Server local y Exchange Server local, así como para entornos híbridos de dominio dividido de Skype empresarial.
ms.openlocfilehash: de5063da9eed03e2cd455b79b3a2d1c2f671ad1e
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840727"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a>Cómo configurar Skype Empresarial local para usar la autenticación moderna híbrida

*Este artículo se aplica tanto a Office 365 Enterprise como a Microsoft 365 Enterprise.*

La autenticación moderna es un método de administración de identidades que ofrece autenticación y autorización de usuarios más seguras, está disponible para Skype empresarial Server local y Exchange Server local, así como para entornos híbridos de dominio dividido de Skype empresarial.
  
 **Importante** ¿Le gustaría saber más sobre la autenticación moderna (MA) y por qué prefiere usarla en su empresa u organización? Consulte [este documento](hybrid-modern-auth-overview.md) para obtener información general. Si necesita saber qué topologías de Skype empresarial son compatibles con MA, esto se documenta aquí.
  
 **Antes de empezar**, debo llamar a:
  
- MA de \> autenticación moderna

- HMA de autenticación \> moderna híbrida

- T local \> de Exchange

- Exo de \> Exchange Online

- Skype empresarial local \> SFB

- y Skype empresarial online \> SFBO

Además, si un gráfico de este artículo tiene un objeto que está atenuado o está atenuado, significa que el elemento que se muestra en gris **no se** incluye en la configuración específica de ma.
  
## <a name="read-the-summary"></a>Leer el Resumen

Este Resumen divide el proceso en pasos que, de lo contrario, podrían perderse durante la ejecución y es conveniente para una lista de comprobación global para realizar un seguimiento de dónde se encuentra en el proceso.
  
1. En primer lugar, asegúrese de que cumple todos los requisitos previos.

1. Dado que muchos de los **requisitos previos** son comunes para Skype empresarial y Exchange, [consulte el artículo de información general para obtener una lista de comprobación previa a la solicitud](hybrid-modern-auth-overview.md). Hágalo *antes* de empezar con cualquiera de los pasos de este artículo.

1. Recopile la información específica del HMA que necesitará en un archivo o en OneNote.

1. Active la autenticación moderna para EXO (si aún no está activada).

1. Active la autenticación moderna para SFBO (si aún no está activada).

1. Active la autenticación moderna híbrida para Exchange local.

1. Active la autenticación moderna híbrida para Skype empresarial local.

Estos pasos activan el MA para SFB, SFBO, EXCH y EXO-es decir, todos los productos que pueden participar en una configuración de HMA de SFB y SFBO (incluidas las dependencias de EXCH/EXO). En otras palabras, si los usuarios están hospedados en o tienen buzones creados en cualquier parte del híbrido (EXO + SFBO, EXO + SFB, EXCH + SFBO o EXCH + SFB), el producto terminado tendrá el siguiente aspecto:
  
![Una topología de HMA de Skype empresarial de 6 mixtas tiene MA activada en las cuatro ubicaciones posibles.](media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)
  
Como puede ver, hay cuatro lugares distintos para activar MA. Para obtener la mejor experiencia de usuario, se recomienda activar MA en cuatro de estas ubicaciones. Si no puede activar MA en todas estas ubicaciones, ajuste los pasos para que Active MA solo en las ubicaciones necesarias para su entorno.
  
Vea el [tema sobre compatibilidad de Skype empresarial con Ma](https://technet.microsoft.com/library/mt803262.aspx) para topologías compatibles.
  
 **Importante** Compruebe que ha cumplido todos los requisitos previos antes de comenzar. Encontrará esta información [aquí](hybrid-modern-auth-overview.md).
  
## <a name="collect-all-hma-specific-info-youll-need"></a>Recopilar toda la información específica de la HMA que tendrás

Una vez que haya comprobado que cumple los [requisitos previos](hybrid-modern-auth-overview.md) para usar la autenticación moderna (consulte la nota anterior), debe crear un archivo que contenga la información que necesitará para configurar HMA en los pasos venideros. Ejemplos que se usan en este artículo:
  
- **Dominio SIP/SMTP**

  - Precio. contoso.com (se ha federado con Office 365)

- **Identificación del inquilino**

  - El GUID que representa el inquilino de Office 365 (en el inicio de sesión de contoso.onmicrosoft.com).

- **Direcciones URL del servicio Web SFB 2015 CU5**

Necesitará direcciones URL de servicios Web internos y externos para todos los grupos de SfB 2015 que se implementen. Para obtenerlos, ejecute lo siguiente desde Shell de administración de Skype empresarial:
  
```powershell
Get-CsService -WebServer | Select-Object PoolFqdn, InternalFqdn, ExternalFqdn | FL
```

- Precio. Internoshttps://lyncwebint01.contoso.com

- Precio. Exteriorhttps://lyncwebext01.contoso.com

Si usa un servidor Standard Edition, la dirección URL interna estará en blanco. En este caso, use el FQDN del grupo de servidores para la dirección URL interna.
  
## <a name="turn-on-modern-authentication-for-exo"></a>Activar la autenticación moderna para EXO

Siga las instrucciones que se indican aquí: [Exchange Online: Cómo habilitar el inquilino para la autenticación moderna.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)
  
## <a name="turn-on-modern-authentication-for-sfbo"></a>Activar la autenticación moderna para SFBO

Siga las instrucciones que se indican aquí: [Skype empresarial online: habilitar el espacio empresarial para la autenticación moderna](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).
  
## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a>Activar la autenticación moderna híbrida para Exchange local

Siga las instrucciones que se indican a continuación: [Cómo configurar Exchange Server local para usar la autenticación moderna híbrida](configure-exchange-server-for-hybrid-modern-authentication.md).
  
## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a>Activar la autenticación moderna híbrida para Skype empresarial local

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a>Agregar direcciones URL de servicios web locales como SPN en Azure AD

Ahora deberá ejecutar comandos para agregar las direcciones URL (recopiladas anteriormente) como entidades de servicio en SFBO.
  
 **Nota:** Los nombres de entidad de seguridad de servicio (SPN) identifican los servicios web y los asocian a una entidad de seguridad (como un grupo o nombre de cuenta) para que el servicio pueda actuar en nombre de un usuario autorizado. Los clientes que se autentican en un servidor usan la información contenida en los SPN.
  
1. En primer lugar, conéctese a AAD con [estas instrucciones](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-1.0).

2. Ejecute este comando, local, para obtener una lista de las direcciones URL del servicio Web de SFB.

   Tenga en cuenta que el AppPrincipalId `00000004`comienza con. Esto corresponde a Skype empresarial online.

   Tome nota de (y captura de pantalla para comparaciones posteriores) el resultado de este comando, que incluirá una dirección URL de SE y WS, pero en `00000004-0000-0ff1-ce00-000000000000/`su mayoría constará de los SPN que comienzan con.

```powershell
Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Select -ExpandProperty ServicePrincipalNames
```

3. Si faltan las URL de SFB internas **o** externas de local (por ejemplo, https://lyncwebint01.contoso.com https://lyncwebext01.contoso.com) se deben agregar esos registros específicos a esta lista.

    Asegúrese de reemplazar *las direcciones URL de ejemplo* , a continuación, con las direcciones URL reales en el comando Agregar comandos!
  
```powershell
$x= Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000
$x.ServicePrincipalnames.Add("https://lyncwebint01.contoso.com/")
$x.ServicePrincipalnames.Add("https://lyncwebext01.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
  
4. Compruebe que los nuevos registros se han agregado ejecutando el comando **Get-MsolServicePrincipal** del paso 2 de nuevo y observando los resultados. Compare la lista o la captura de pantalla de antes con la nueva lista de SPN (también puede mostrar una captura de pantalla de la nueva lista de sus registros). Si ha tenido éxito, verá las dos nuevas direcciones URL en la lista. Siguiendo nuestro ejemplo, la lista de SPN ahora incluirá las direcciones URL https://lyncwebint01.contoso.com específicas y https://lyncwebext01.contoso.com/.

### <a name="create-the-evosts-auth-server-object"></a>Crear el objeto de servidor de autenticación de EvoSTS

Ejecute el siguiente comando en el shell de administración de Skype empresarial.
  
```powershell
New-CsOAuthServer -Identity evoSTS -MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml -AcceptSecurityIdentifierInformation $true -Type AzureAD
```

### <a name="enable-hybrid-modern-authentication"></a>Habilitar la autenticación moderna híbrida

Este es el paso que realmente activa MA. Todos los pasos anteriores se pueden ejecutar con antelación sin cambiar el flujo de autenticación del cliente. Cuando esté listo para cambiar el flujo de autenticación, ejecute este comando en el shell de administración de Skype empresarial.

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity evoSTS
```

## <a name="verify"></a>Comprueba

Una vez habilitada la HMA, el próximo inicio de sesión de un cliente usará el nuevo flujo de autenticación. Tenga en cuenta que, al activar la HMA no se activará una nueva autenticación para ningún cliente. Los clientes se vuelven a autenticar en función de la duración de los tokens de autenticación o de los certificados que tienen.
  
Para probar que la HMA funciona después de habilitarla, cierre la sesión del cliente de Windows SFB y haga clic en "eliminar mis credenciales". Vuelva a iniciar sesión. Ahora, el cliente debe usar el flujo de autenticación moderna y el inicio de sesión incluirá un mensaje de **Office 365** para una cuenta de trabajo o escuela, visto justo antes de que el cliente se pone en contacto con el servidor e inicie sesión.
  
También debe comprobar la "información de configuración" para los clientes de Skype empresarial para una "entidad de OAuth". Para hacer esto en el equipo cliente, mantenga presionada la tecla CTRL al mismo tiempo que hace clic con el botón secundario en el icono de Skype empresarial en la bandeja de notificaciones de Windows. Haga clic en **información de configuración** en el menú que aparece. En la ventana ' información de configuración de Skype empresarial ' que aparecerá en el escritorio, busque lo siguiente:
  
![La información de configuración de un cliente de Skype empresarial mediante autenticación moderna muestra una dirección URL de la entidad de https://login.windows.net/common/oauth2/authorizeOAUTH de Lync y EWS de.](media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png)
  
También debe mantener presionada la tecla CTRL al mismo tiempo que se hace clic en el icono del cliente de Outlook (también en la bandeja de notificaciones de Windows) y en "estado de conexión". Busque la dirección SMTP del cliente en un tipo de "portador\*" de authn, que representa el token del portador usado en OAuth.
  
## <a name="related-articles"></a>Artículos relacionados

[Vínculo volver a la introducción a la autenticación moderna](hybrid-modern-auth-overview.md).
  
¿Necesita saber cómo usar la autenticación moderna (ADAL) para sus clientes de Skype empresarial? Tenemos pasos [aquí](https://technet.microsoft.com/library/mt710548.aspx).
