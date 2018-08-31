---
title: Cómo configurar Skype Empresarial local para usar la autenticación moderna híbrida
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 6/4/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 522d5cec-4e1b-4cc3-937f-293570717bc6
description: Autenticación moderna, es un método de administración de identidades que ofrece la autorización y autenticación de usuario más segura, está disponible para Skype para Business server local y Exchange server local, así como dominio dividido Skype para híbridos de negocio.
ms.openlocfilehash: 48ce10022e384ec88b88c0e8ec038bf201adc707
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22543051"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a>Cómo configurar Skype Empresarial local para usar la autenticación moderna híbrida

Autenticación moderna, es un método de administración de identidades que ofrece la autorización y autenticación de usuario más segura, está disponible para Skype para Business server local y Exchange server local, así como dominio dividido Skype para híbridos de negocio.
  
 **Importante** ¿Desea saber más sobre autenticación moderno (MA) y por qué es preferible usar en su compañía u organización? Compruebe [este documento](hybrid-modern-auth-overview.md) para obtener información general. Si necesita saber qué Skype para topologías empresariales son compatibles con MA, que se documenta aquí! 
  
 **Antes de empezar**, puedo llamar: 
  
- Autenticación moderna \> MA
    
- Autenticación moderno híbrida \> HMA
    
- Exchange local \> EXCH
    
- Exchange Online \> EXO
    
- Skype para empresarial local \> SFB
    
- y Skype para la empresa en línea \> SFBO
    
Además, * si un gráfico en este artículo no tiene un valor object que tiene 'atenuada' o 'atenuada' que significa que el elemento que se muestra en gris **no está** incluido en la configuración específica del agente de administración. * 
  
## <a name="read-the-summary"></a>Lea el resumen

En este resumen se reduce el proceso en pasos que en caso contrario, es posible que se pierden durante la ejecución y es conveniente para una lista de comprobación general realizar un seguimiento de dónde se encuentre en el proceso.
  
1. En primer lugar, asegúrese de que cumple todos los requisitos previos.
    
1. Con respecto a muchos de **los requisitos previos** son comunes para ambos Skype para empresariales y de Exchange, [consulte el artículo de información general para la lista de comprobación de requisito previo](hybrid-modern-auth-overview.md). Realice este *antes de* comenzar cualquiera de los pasos descritos en este artículo. 
    
2. Recopilar la información de HMA específicas que necesitará en un archivo o OneNote.
    
3. Activar ON moderno Authentication for EXO (si no está ya activada).
    
4. Activar ON moderno Authentication for SFBO (si no está ya activada).
    
5. Activar la autenticación moderno híbrida de Exchange local.
    
6. Activar la autenticación moderno híbrido de Skype para empresarial local.
    
Tenga en cuenta que estos pasos activar MA para SFB, SFBO, EXCH y EXO--es decir, todos los productos que pueden participar en una configuración de HMA de SFB y SFBO (incluidas las dependencias en EXCH/EXO). En otras palabras, si los usuarios están hospedados en / crean buzones de correo en cualquier parte de la híbrido (EXO + SFBO, EXO + SFB, EXCH + SFBO, o EXCH + SFB), el precio del producto terminado tendrá el siguiente aspecto:
  
![Un Skype 6 mixto de topología del negocio HMA tiene MA en todas las ubicaciones posibles cuatro.](media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)
  
Como puede ver, hay cuatro distintos lugares para activar el agente de administración de! Para la mejor experiencia de usuario, se recomienda que activar MA en cuatro de estas ubicaciones. Si no se puede activar el agente de administración en todas las ubicaciones de estos, ajuste los pasos para que encienda MA sólo en las ubicaciones que son necesarios para su entorno.
  
Vea el [tema de la compatibilidad de Skype para la empresa con el agente de administración](https://technet.microsoft.com/en-us/library/mt803262.aspx) de topologías admitidas. 
  
 **Importante** Vuelva a comprobar que cumple todos los requisitos previos antes de empezar. Puede encontrar esa información [aquí](hybrid-modern-auth-overview.md).
  
## <a name="collect-all-hma-specific-info-youll-need"></a>Recopilar toda la información específica de HMA que necesitará

Una vez haya comprobado que se cumplen los [requisitos previos](hybrid-modern-auth-overview.md) para usar autenticación moderno (consulte la nota anterior), debe crear un archivo para contener la información que necesitará para configurar HMA en los pasos con antelación. Ejemplos que se utilizan en este artículo: 
  
- **Dominio SIP/SMTP**
    
  - Contoso.com ex. (está asociado a Office 365)
    
- **Identificador de inquilino**
    
  - El GUID que representa al inquilino de Office 365 (en el inicio de sesión de contoso.onmicrosoft.com).
    
- **Direcciones URL del servicio SFB 2015 CU5 Web**
    
Necesitará la dirección URL de servicio web internos y externos para todos los grupos de servidores SfB 2015 implementados. Para obtener estos, ejecute lo siguiente desde Skype para Shell de administración de negocio:
  
Get-CsService - WebServer | Select-Object PoolFqdn, InternalFqdn, Fqdnexterno | FL
  
- Ex. interno:https://lyncwebint01.contoso.com
    
- Ex. externos:https://lyncwebext01.contoso.com
    
Si está utilizando un servidor Standard Edition, la dirección URL interna estará en blanco. En este caso, use el fqdn del grupo de servidores para la dirección URL interna.
  
## <a name="turn-on-modern-authentication-for-exo"></a>Activar la autenticación moderna para EXO

Siga las instrucciones aquí: [Exchange Online: cómo habilitar el inquilino de para la autenticación moderno.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)
  
## <a name="turn-on-modern-authentication-for-sfbo"></a>Activar la autenticación moderna para SFBO

Siga las instrucciones aquí: [Skype para profesionales Online: habilitar el inquilino de para la autenticación moderno](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).
  
## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a>Activar la autenticación moderno híbrida de Exchange local

Siga las instrucciones aquí: [cómo configurar el servidor de Exchange local para usar la autenticación moderno híbrida](configure-exchange-server-for-hybrid-modern-authentication.md).
  
## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a>Activar la autenticación moderno híbrido de Skype para empresarial local

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a>Agregar local web direcciones URL de servicios como SPN en Azure AD

Ahora que necesitará para ejecutar comandos para agregar las direcciones URL (anteriormente recopilados) como entidades de seguridad de servicio en SFBO.
  
 **Nota** Nombres principales de servicio (SPN) identificación de servicios web y asociación a una entidad de seguridad (por ejemplo, un nombre de cuenta o grupo) para que el servicio pueda actuar en nombre de un usuario autorizado. Autenticación a un servidor de clientes hacen uso de la información que SPN contenidos en. 
  
1. En primer lugar, conectarse a AAD con [estas instrucciones](https://docs.microsoft.com/en-us/powershell/azure/active-directory/install-adv2?view=azureadps-2.0).
    
2. Ejecute este comando, local, para obtener una lista de direcciones URL de servicio de web SFB.
    
  - Get-MsolServicePrincipal - AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Seleccione ServicePrincipalNames - ExpandProperty
    
    Tenga en cuenta que el AppPrincipalId comienza con '00000004'. Esto corresponde al Skype para profesionales en línea.
    
    Tomar nota de (y captura de pantalla para realizar una comparación posterior) el resultado de este comando, que se incluyen un SE y la dirección URL de WS, pero se componen principalmente de SPN que comiencen con 00000004-0000-0ff1-ce00-000000000000 /.
    
3. Si la interna **o** externa SFB las direcciones URL de local faltan (por ejemplo, https://lyncwebint01.contoso.com y https://lyncwebext01.contoso.com) necesitamos agregar esos registros específicos a esta lista. 
    
    ¡Asegúrese de reemplazar *las direcciones URL de ejemplo* , a continuación, con las direcciones URL real en los comandos Agregar! 
    
  - $x = get-MsolServicePrincipal - AppPrincipalId 00000004-0000-0ff1-ce00-000000000000
    
  - $x.ServicePrincipalnames.Add (" *https://lyncwebint01.contoso.com/* ") 
    
  - $x.ServicePrincipalnames.Add (" *https://lyncwebext01.contoso.com/* ") 
    
  - Set-MSOLServicePrincipal - AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 - ServicePrincipalNames $x.ServicePrincipalNames
    
4. Compruebe que los registros nuevos agregados por ejecutar de nuevo el comando Get-MsolServicePrincipal desde el paso 2 y con un aspecto a través del resultado. Compare la lista / captura de pantalla de antes de a la nueva lista de SPN (que es posible que también captura de pantalla de la nueva lista para sus registros). Si se realizaron correctamente, verá las dos nuevas direcciones URL en la lista. Va por nuestro ejemplo, la lista de los SPN ahora incluirá las direcciones URL específicas https://lyncweb01.contoso.com y https://autodiscover.contoso.com.
    
### <a name="create-the-evosts-auth-server-object"></a>Crear el objeto de servidor de autenticación EvoSTS

Ejecute el siguiente comando en el Skype para Shell de administración de negocio.
  
- New-CsOAuthServer-Identity evoSTS - MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml - AcceptSecurityIdentifierInformation $true-tipo AzureAD
    
### <a name="enable-hybrid-modern-authentication"></a>Habilitar la autenticación moderno híbrida

Éste es el paso que realmente activa MA. Todos los pasos anteriores se pueden ejecutar antes de tiempo sin cambiar el flujo de autenticación de cliente. Cuando esté listo para cambiar el flujo de autenticación, ejecute este comando en el Skype para Shell de administración de negocio. 
  
- Set-CsOAuthConfiguration - ClientAuthorizationOAuthServerIdentity evoSTS
    
## <a name="verify"></a>Comprobar

Una vez habilitar HMA, el siguiente inicio de sesión de un cliente utilizará el nuevo flujo de autenticación. Tenga en cuenta la activación de HMA no desencadenar una nueva autenticación para cualquier cliente. Los clientes volver a autenticar en función de la duración de los tokens de autenticación o que tienen los certificados.
  
Para probar que está funcionando HMA después de que la ha habilitado, cerrar la sesión de un cliente de Windows SFB de prueba y asegúrese de hacer clic en 'eliminar mis credenciales'. Iniciar sesión de nuevo. El cliente ahora debe usar el flujo de Auth moderno y su inicio de sesión incluirá un símbolo del sistema de **Office 365** para un 'trabajo o escuela' cuenta, se puede apreciar justo antes de que el cliente se pone en contacto con el servidor e inicia una sesión. 
  
También debe comprobar la información de configuración de' ' para Skype para clientes empresariales para una entidad de' OAuth'. Para hacer esto en el equipo cliente, mantenga presionada la tecla CTRL al mismo tiempo que secundario la Skype para empresarial icono en la Bandeja de notificación de Windows. En el menú que aparece, haga clic en información de configuración. En la ventana 'Skype para información de configuración de la empresa' que aparecerá en el escritorio, busque lo siguiente:
  
![La información de configuración de un Skype para el cliente de negocio mediante autenticación moderno muestra un Lync y la dirección URL de EWS OAUTH autoridad de https://login.windows.net/common/oauth2/authorize.](media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png)
  
También debe mantenga presionada la tecla CTRL al mismo tiempo botón secundario haga clic en el icono para el cliente de Outlook (también en la Bandeja de notificaciones de Windows) y haga clic en estado de la conexión. Busque la dirección del cliente SMTP con respecto a un tipo de niveles de autenticación de ' Bearer\*', que representa el token de portador utilizado en OAuth.
  
## <a name="related-articles"></a>Artículos relacionados

[Vínculo hacia atrás a la introducción a la autenticación moderno](hybrid-modern-auth-overview.md) . 
  
¿Necesita saber cómo usar autenticación moderno (ADAL) para su Skype para clientes empresariales? Tenemos pasos [aquí](https://technet.microsoft.com/en-us/library/mt710548.aspx).
  
¿Desea para leer estos pasos, tal como aparecen para Exchange Server, local, que se ejecuta sin SFB? Esos pasos están disponibles aquí.
  

