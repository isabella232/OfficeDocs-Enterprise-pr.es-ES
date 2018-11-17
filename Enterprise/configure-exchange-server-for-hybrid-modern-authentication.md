---
title: Cómo configurar Exchange Server local para usar la autenticación moderna híbrida
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 11/16/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: cef3044d-d4cb-4586-8e82-ee97bd3b14ad
description: Híbrido moderno autenticación (HMA), es un método de administración de identidades que ofrece más seguro autorización y autenticación de usuario y está disponible para las implementaciones híbridas de Exchange server local.
ms.openlocfilehash: df5ea03b06ee1c101b03e19c7acb445c9543586b
ms.sourcegitcommit: 45633b7034ee98d0cd833db9743f283b638237f4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "26547162"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a>Cómo configurar Exchange Server local para usar la autenticación moderna híbrida

Híbrido moderno autenticación (HMA), es un método de administración de identidades que ofrece más seguro autorización y autenticación de usuario y está disponible para las implementaciones híbridas de Exchange server local.
  
## <a name="fyi"></a>PARA SU INFORMACIÓN

Antes de empezar, puedo llamar:
  
- Autenticación moderno híbrida \> HMA
    
- Exchange local \> EXCH
    
- Exchange Online \> EXO
    
Además, *que si un gráfico en este artículo tiene un objeto que tiene ' atenuada ' o 'atenuada' Esto significa que el elemento que se muestra en gris no está incluido en la configuración específica del HMA* . 
  
## <a name="enabling-hybrid-modern-authentication"></a>Habilitar la autenticación híbrida moderno

Encienda HMA significa:
  
1. Asegurándose de que cumple con los requisitos previos antes de empezar.
    
1. Con respecto a muchos de **los requisitos previos** son comunes para ambos Skype para empresas y Exchange, [Introducción a la autenticación moderno híbrida y requisitos previos para usar con local Skype para profesionales y los servidores Exchange](hybrid-modern-auth-overview.md). Hacer esto antes de iniciar cualquiera de los pasos descritos en este artículo.
    
2. Adición de local direcciones URL de servicios web como nombres principales de servicio (SPN) en Azure AD.
    
3. Asegurarse de todos los directorios virtuales están habilitados para HMA
    
4. Comprobación de que el objeto de servidor de autenticación EvoSTS
    
5. HMA habilitación de cambio
    
 **Nota** ¿Se admite MA de su versión de Office? Vea [moderno cómo funciona la autenticación para aplicaciones de cliente de Office 2013 y Office 2016](modern-auth-for-office-2013-and-2016.md).
  
## <a name="make-sure-you-meet-all-the-pre-reqs"></a>Asegúrese de que cumple todos los requisitos previos

Dado que muchos de los requisitos previos son comunes para ambos Skype para empresariales y de Exchange, revise [Introducción a la autenticación moderno híbrida y requisitos previos para usar con Skype local para los servidores de Exchange y profesionales](hybrid-modern-auth-overview.md). Realice este *antes de* comenzar cualquiera de los pasos descritos en este artículo. 
  
## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a>Agregar local web direcciones URL de servicios como SPN en Azure AD

Ejecute los comandos que asignación direcciones URL de servicios de su web local como SPN de AD de Azure. SPN usados por los equipos cliente y dispositivos durante la autenticación y autorización. Todas las direcciones URL que pueden usarse para conectarse desde local a Azure Active Directory (AAD) deben estar registradas en AAD (Esto incluye los espacios de nombres internos y externos).
  
En primer lugar, recopilar todas las direcciones URL que necesita agregar en AAD. Ejecute estos comandos local:
  
```powershell
Get-MapiVirtualDirectory | FL server,*url*
Get-WebServicesVirtualDirectory | FL server,*url*
Get-ActiveSyncVirtualDirectory | FL server,*url*
Get-OABVirtualDirectory | FL server,*url*
```
    
Asegúrese de que las direcciones URL que los clientes pueden conectarse a aparecen como nombres principales de servicio HTTPS en AAD.
  
1. En primer lugar, conectarse a AAD con [estas instrucciones](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell). 

 **Nota** Debe usar la opción de Connect-MsolService desde esta página para poder utilizar el siguiente comando. 
    
2. Para Exchange URL relacionadas, escriba el siguiente comando:
    
```powershell
Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | select -ExpandProperty ServicePrincipalNames
```

Tome nota de (y captura de pantalla para realizar una comparación posterior) el resultado de este comando, que debe incluir un https:// *autodiscover.yourdomain.com* y la dirección URL de *correo.sudominio.com* https://, pero se componen principalmente de SPN que comienzan con 00000002-0000-0ff1-CE00-000000000000 /. Si no hay direcciones URL https:// desde su local que faltan necesitamos agregar esos registros específicos a esta lista. 
  
3. Si no ve los registros MAPI/HTTP, EWS, ActiveSync, OAB y detección automática internos y externos en esta lista, debe agregarlas mediante el siguiente comando (en el ejemplo de las direcciones URL son '`mail.corp.contoso.com`'y'`owa.contoso.com`', pero tenía **reemplazar las direcciones URL de ejemplo con su propio** ) : <br/>
```powershell
$x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000   
$x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
$x.ServicePrincipalnames.Add("https://owa.contoso.com/")
$x.ServicePrincipalnames.Add("https://eas.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
 
4. Compruebe que los registros nuevos agregados por ejecutar de nuevo el comando Get-MsolServicePrincipal desde el paso 2 y con un aspecto a través del resultado. Compare la lista / captura de pantalla de antes de a la nueva lista de SPN (que es posible que también captura de pantalla de la nueva lista para sus registros). Si se realizaron correctamente, verá las dos nuevas direcciones URL en la lista. Va por nuestro ejemplo, la lista de los SPN ahora incluirá las direcciones URL específicas `https://mail.corp.contoso.com` y `https://owa.contoso.com`. 
  
## <a name="verify-virtual-directories-are-properly-configured"></a>Compruebe que los directorios virtuales están configurados correctamente

Ahora compruebe OAuth está habilitada correctamente en podría usar Exchange en todos los de Outlook de los directorios virtuales mediante la ejecución de los siguientes comandos:

```powershell
Get-MapiVirtualDirectory | FL server,*url*,*auth* 
Get-WebServicesVirtualDirectory | FL server,*url*,*oauth*
Get-OABVirtualDirectory | FL server,*url*,*oauth*
Get-AutoDiscoverVirtualDirectory | FL server,*oauth*
```

Comprobar el resultado para hacer que **OAuth** está habilitada en cada uno de estos directorios virtuales combinados, buscará algo parecido a esto (y lo clave a mirar es 'OAuth'); 

```powershell
Get-MapiVirtualDirectory | fl server,*url*,*auth*
```

```
Server                        : EX1
InternalUrl                   : https://mail.contoso.com/mapi
ExternalUrl                   : https://mail.contoso.com/mapi
IISAuthenticationMethods      : {Ntlm, OAuth, Negotiate}
InternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
ExternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
```
  
Si no se encuentra ningún servidor y cualquiera de los cuatro directorios virtuales de OAuth, a continuación, debe agregar los comandos relevantes antes de continuar.
  
## <a name="confirm-the-evosts-auth-server-object-is-present"></a>Confirme que el objeto de servidor de autenticación de EvoSTS está presente

Volver a la consola de administración de Exchange local para este último comando. Ahora puede validar que su local tiene una entrada para el proveedor de autenticación evoSTS:
  
```powershell
Get-AuthServer | where {$_.Name -eq "EvoSts"}
```

El resultado debe mostrar una AuthServer de la EvoSts de nombre y el estado de 'Habilitado' debe ser True. Si no ve esto, debe descargar y ejecutar la versión más reciente del Asistente de configuración híbrida.
  
 **Importante** Si está ejecutando Exchange 2010 en su entorno, no se creará el proveedor de autenticación EvoSTS. 
  
## <a name="enable-hma"></a>Habilitar HMA

Ejecute el siguiente comando en el Shell de administración de Exchange local:

```powershell
Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true  
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```
    
## <a name="verify"></a>Comprobar

Una vez habilitar HMA, el siguiente inicio de sesión de un cliente utilizará el nuevo flujo de autenticación. Tenga en cuenta la activación de HMA no desencadenar una nueva autenticación para cualquier cliente. Los clientes volver a autenticar en función de la duración de los tokens de autenticación o que tienen los certificados.
  
También debe mantenga presionada la tecla CTRL al mismo tiempo botón secundario haga clic en el icono para el cliente de Outlook (también en la Bandeja de notificaciones de Windows) y haga clic en estado de la conexión. Busque la dirección del cliente SMTP con respecto a un tipo 'Niveles de autenticación' de ' Bearer\*', que representa el token de portador utilizado en OAuth.
  
 **Nota** ¿Necesita configurar Skype para la empresa con HMA? Necesitará dos artículos: uno que enumera las [topologías admitidas](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)y otro que muestra [cómo realizar la configuración](configure-skype-for-business-for-hybrid-modern-authentication.md).
  

## <a name="related-topics"></a>Temas relacionados

[Introducción a la autenticación moderno híbrida y requisitos previos para usar con Skype local para los servidores empresariales y de Exchange](hybrid-modern-auth-overview.md) 
  

