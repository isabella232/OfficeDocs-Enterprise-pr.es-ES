---
title: Uso de Azure AD para la autenticación de SharePoint Server
ms.author: tracyp
author: MSFTTracyP
ms.reviewer: kirke, josephd, kirks
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Ent_O365_Hybrid
ms.custom: Ent_Solutions
ms.assetid: ''
description: 'Resumen: Obtenga información sobre cómo omitir Azure Access Control Service y usar SAML 1,1 para autenticar a los usuarios de SharePoint Server con Azure Active Directory.'
ms.openlocfilehash: c2c9f33aa5e095a8b7fdde08e80cb1a61e88f3eb
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070796"
---
# <a name="using-azure-ad-for-sharepoint-server-authentication"></a>Uso de Azure AD para la autenticación de SharePoint Server

 **Resumen:** Obtenga información sobre cómo autenticar a los usuarios de SharePoint Server 2016 con Azure Active Directory. 

<blockquote>
<p>Este artículo hace referencia a ejemplos de código para interactuar con el gráfico de Azure Active Directory. Puede descargar los ejemplos de código [aquí](https://github.com/kaevans/spsaml11/tree/master/scripts).</p>
</blockquote>

SharePoint Server 2016 permite autenticar a los usuarios mediante la autenticación basada en notificaciones, lo que facilita la administración de los usuarios mediante su autenticación con proveedores de identidades diferentes en los que confía, pero que otras personas administran. Por ejemplo, en lugar de administrar la autenticación de usuario a través de los servicios de dominio de Active Directory (AD DS), puede permitir que los usuarios se autentiquen con Azure Active Directory (Azure AD). Esto habilita la autenticación para los usuarios de solo nube con el sufijo onmicrosoft.com en su nombre de usuario, los usuarios sincronizados con un directorio local y los usuarios invitados invitados desde otros directorios. También le permite aprovechar las ventajas de las características de Azure AD, como la autenticación multifactor y las capacidades de informes avanzadas.

> [!IMPORTANT]
> La solución que se describe en este artículo también puede usarse con SharePoint Server 2013; sin embargo, tenga en cuenta que SharePoint Server 2013 está llegando al final de la compatibilidad estándar. Para obtener más información, vea [Directiva de ciclo de vida de Microsoft](https://support.microsoft.com/en-us/lifecycle/search?alpha=SharePoint%20Server%202013) y [Directiva de servicio del producto actualizada para SharePoint 2013](https://technet.microsoft.com/library/684173bb-e90a-4eb7-b268-b8d7458bc802(v=office.16).aspx).

En este artículo se explica cómo se puede usar Azure AD en lugar de su AD DS local para autenticar a los usuarios. En esta configuración, Azure AD se convierte en un proveedor de identidad de confianza para SharePoint Server 2016. Esta configuración agrega un método de autenticación de usuario que es independiente de la autenticación de AD DS que usa la instalación de SharePoint Server 2016. Para sacarle el máximo partido a este artículo, recomendamos que esté familiarizado con WS-Federation. Para más información, consulte el tema de [introducción a WS-Federation ](https://go.microsoft.com/fwlink/p/?linkid=188052). Para obtener información detallada sobre la integración de SharePoint local con Azure Active Directory, vea el [tutorial dedicado](https://docs.microsoft.com/azure/active-directory/saas-apps/sharepoint-on-premises-tutorial).

![Uso de Azure AD para la autenticación de SharePoint](media/SAML11/fig1-architecture.png)

Anteriormente, esta configuración habría requerido un servicio de Federación como Azure Access Control Service (ACS) en la nube o un entorno que hospede los servicios de Federación de Active Directory (AD FS) para transformar los tokens de SAML 2,0 a SAML 1,1. Esta transformación ya no es necesaria ya que Azure AD ahora habilita la emisión de tokens SAML 1,1. El diagrama anterior muestra cómo funciona la autenticación para los usuarios de SharePoint 2016 en esta configuración, lo que demuestra que ya no es necesario que un intermediario realice esta transformación.

> [!NOTE]
> Esta configuración funciona si la granja de servidores de SharePoint está hospedada en máquinas virtuales de Azure o en local. No requiere que se abran otros puertos de firewall que no sean la garantía de que los usuarios puedan acceder a Azure Active Directory desde el explorador.

Para obtener información sobre la accesibilidad de SharePoint 2016, vea [directrices de accesibilidad en SharePoint Server 2016](https://go.microsoft.com/fwlink/p/?LinkId=393123).

## <a name="configuration-overview"></a>Descripción general de la configuración

Siga estos pasos generales para configurar el entorno para que use Azure AD como un proveedor de identidades de SharePoint Server 2016.

1. Cree un nuevo directorio de Azure AD o use el directorio existente.
2. Asegúrese de que la zona de la aplicación web que desea proteger con Azure AD esté configurada para usar SSL.
3. Cree una nueva aplicación de empresa en Azure AD.
4. Configure un nuevo proveedor de identidades de confianza en SharePoint Server 2016.
5. Establezca los permisos para la aplicación Web.
6. Agregue una directiva de emisión de token SAML 1,1 en Azure AD.
7. Compruebe el nuevo proveedor.

En las secciones siguientes se describe cómo realizar estas tareas.

## <a name="step-1-create-a-new-azure-ad-directory-or-use-your-existing-directory"></a>Paso 1: crear un nuevo directorio de Azure AD o usar el directorio existente

En el portal de Azure[https://portal.azure.com](https://portal.azure.com)(), cree un nuevo directorio. Proporcione el nombre de la organización, el nombre del dominio inicial y el país o la región.

![Creación de un directorio](media/SAML11/fig2-createdirectory.png) 

 Si ya tiene un directorio como el que se usa para Microsoft Office 365 o su suscripción de Microsoft Azure, puede usar ese directorio en su lugar. Debe tener permisos para registrar las aplicaciones en el directorio.

## <a name="step-2-ensure-the-zone-for-the-web-application-that-you-want-to-secure-with-azure-ad-is-configured-to-use-ssl"></a>Paso 2: asegurarse de que la zona de la aplicación web que desea proteger con Azure AD está configurada para usar SSL

Este artículo se escribió con la arquitectura de referencia en [ejecutar una granja de servidores de SharePoint Server 2016 de alta disponibilidad en Azure](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint). Los scripts adjuntos del artículo que se usan para implementar la solución que se describe en [este artículo](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint) crean un sitio que no usa SSL.  

El uso de SAML requiere que la aplicación esté configurada para usar SSL. Si la aplicación Web de SharePoint no está configurada para usar SSL, use los siguientes pasos para crear un nuevo certificado autofirmado para configurar la aplicación web para SSL. Esta configuración solo está diseñada para un entorno de laboratorio y no está pensada para producción. Los entornos de producción deben usar un certificado firmado.

1. Vaya a **** > **Administración** > central de administración de aplicaciones**Administrar aplicaciones web**y elija la aplicación web que debe extenderse para usar SSL. Seleccione la aplicación web y haga clic en el botón **extender cinta** . Extienda la aplicación web para usar la misma dirección URL, pero use SSL con el puerto 443.<br/>![Extensión de la aplicación web a otro sitio de IIS](media/SAML11/fig3-extendwebapptoiis.png)<br/>
2. En Administrador de IIS, haga doble clic en **Certificados de servidor**.
3. En el panel **Acciones**, haga clic en **Crear certificado autofirmado**. Escriba un nombre descriptivo para el certificado en el cuadro Especifique un nombre descriptivo para el certificado y haga clic en **Aceptar**.
4. En el cuadro de diálogo **editar enlace de sitio** , asegúrese de que el nombre de host es el mismo que el nombre descriptivo, como se muestra en la siguiente imagen.<br/>![Edición del enlace de sitios en IIS](media/SAML11/fig4-editsitebinding.png)<br/>

Cada uno de los servidores front-end web de la granja de servidores de SharePoint requerirá la configuración del certificado para el enlace de sitio en IIS.


## <a name="step-3-create-a-new-enterprise-application-in-azure-ad"></a>Paso 3: crear una nueva aplicación de empresa en Azure AD

1. En el portal de Azure[https://portal.azure.com](https://portal.azure.com)(), abra el directorio de Azure ad. Haga clic en **aplicaciones de empresa**y, a continuación, en **nueva aplicación**. Elija **aplicación que no sea de Galería**. Proporcione un nombre como la *integración de SAML de SharePoint* y haga clic en **Agregar**.<br/>![Adición de una nueva aplicación que no es de Galería](media/SAML11/fig5-addnongalleryapp.png)<br/>
2. Haga clic en el vínculo de inicio de sesión único en el panel de navegación para configurar la aplicación. Cambie el desplegable de **modo de inicio de sesión único** a **Inicio de sesión basado en SAML** para mostrar las propiedades de configuración de SAML para la aplicación. Configure con las siguientes propiedades:<br/>
    - Identificador`urn:sharepoint:portal.contoso.local`
    - Dirección URL de respuesta:`https://portal.contoso.local/_trust/default.aspx`
    - Dirección URL de inicio de sesión:`https://portal.contoso.local/_trust/default.aspx`
    - Identificador de usuario:`user.userprincipalname`<br/>
    - Nota: Recuerde cambiar las direcciones URL reemplazando *portal. contoso. local* por la dirección URL del sitio de SharePoint que desea proteger.<br/>
3. Configure una tabla (similar a la tabla 1 a continuación) que incluya las filas siguientes:<br/> 
    - Realm
    - Ruta de acceso completa al archivo de certificado de firma de SAML
    - URL del servicio de inicio de sesión único (Single Sign-on) de SAML (reemplazando */saml2* por */wsfed*)
    - IDENTIFICADOR del objeto de la aplicación. <br/>
Copie el valor *identificador* en la propiedad *Realm* en una tabla (vea la tabla 1 a continuación).
4. Guarde los cambios.
5. Haga clic en el vínculo **Configurar (nombre de la aplicación)** para acceder a la página configurar el inicio de sesión.<br/>![Configuración de una página de inicio de sesión único](media/SAML11/fig7-configssopage.png)<br/> 
    -  Haga clic en el vínculo **certificado de firma de SAML-RAW** para descargar el certificado de firma de SAML como un archivo con la extensión. cer. Copie y pegue la ruta de acceso completa del archivo descargado en la tabla.
    - Copie y pegue el vínculo de la dirección URL del servicio de inicio de sesión único de SAML en el, reemplazando la parte */saml2* de la dirección URL por */wsfed*.<br/>
6.  Navegue hasta el panel de **propiedades** de la aplicación. Copie y pegue el valor del identificador de objeto en la tabla que configuró en el paso 3.<br/>![Panel de propiedades de la aplicación](media/SAML11/fig8-propertiespane.png)<br/>
7. Con los valores que ha capturado, asegúrese de que la tabla que configuró en el paso 3 sea similar a la tabla 1 siguiente.


| Tabla 1: valores capturados  |  |
|---------|---------|
|Realm | `urn:sharepoint:portal.contoso.local` |
|Ruta de acceso completa al archivo de certificado de firma de SAML | `C:/temp/SharePoint SAML Integration.cer`  |
|Dirección URL del servicio de inicio de sesión único de SAML (reemplace/saml2 por/wsfed) | `https://login.microsoftonline.com/b1726649-b616-460d-8d20-defab80d476c/wsfed` |
|IDENTIFICADOR del objeto de la aplicación | `a812f48b-d1e4-4c8e-93be-e4808c8ca3ac` |

> [!IMPORTANT]
> Reemplace el valor */saml2* en la dirección URL con */wsfed*. El extremo */saml2* procesará los tokens SAML 2,0. El extremo */wsfed* habilita el procesamiento de tokens SAML 1,1 y es necesario para la Federación SAML de SharePoint 2016.

## <a name="step-4-configure-a-new-trusted-identity-provider-in-sharepoint-server-2016"></a>Paso 4: configurar un nuevo proveedor de identidades de confianza en SharePoint Server 2016

Inicie sesión en el servidor de SharePoint Server 2016 y abra el shell de administración de SharePoint 2016. Rellene los valores de $realm, $wsfedurl y $filepath de la tabla 1 y ejecute los siguientes comandos para configurar un nuevo proveedor de identidades de confianza.

> [!TIP]
> Si no está familiarizado con PowerShell o desea obtener más información sobre cómo funciona PowerShell, consulte [SharePoint PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/overview?view=sharepoint-ps). 

```
$realm = "<Realm from Table 1>"
$wsfedurl="<SAML single sign-on service URL from Table 1>"
$filepath="<Full path to SAML signing certificate file from Table 1>"
$cert = New-Object System.Security.Cryptography.X509Certificates.X509Certificate2($filepath)
New-SPTrustedRootAuthority -Name "AzureAD" -Certificate $cert
$map = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" -IncomingClaimTypeDisplayName "name" -LocalClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn"
$map2 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname" -IncomingClaimTypeDisplayName "GivenName" -SameAsIncoming
$map3 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname" -IncomingClaimTypeDisplayName "SurName" -SameAsIncoming
$ap = New-SPTrustedIdentityTokenIssuer -Name "AzureAD" -Description "SharePoint secured by Azure AD" -realm $realm -ImportTrustCertificate $cert -ClaimsMappings $map,$map2,$map3 -SignInUrl $wsfedurl -IdentifierClaim "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name"
```

A continuación, siga estos pasos para habilitar el proveedor de identidad de confianza para su aplicación:
1. En administración central, vaya a **Administración de aplicaciones web** y seleccione la aplicación web que desea proteger con Azure ad. 
2. En la cinta, haga clic en **proveedores de autenticación** y elija la zona que desea usar.
3. Seleccione **proveedor de identidad de confianza** y seleccione el proveedor de identificación que acaba de registrar con el nombre *AzureAD*.  
4. En la configuración de dirección URL de la página de inicio de sesión, seleccione **Página de inicio de sesión personalizada** y proporcione el valor "/_trust/". 
5. Haga clic en **Aceptar**.

![Configurar el proveedor de autenticación](media/SAML11/fig10-configauthprovider.png)

> [!IMPORTANT]
> Es importante seguir todos los pasos, incluida la configuración de la página de inicio de sesión personalizada en "/_trust/", como se muestra. La configuración no funcionará correctamente a menos que se sigan todos los pasos.

## <a name="step-5-set-the-permissions"></a>Paso 5: establecer los permisos

Se debe conceder acceso a la aplicación a los usuarios que iniciarán sesión en Azure AD y Access a SharePoint. 

1. En Azure portal, abra el directorio de Azure AD. Haga clic en **aplicaciones de empresa**y, a continuación, en **todas las aplicaciones**. Haga clic en la aplicación que creó anteriormente (integración de SAML de SharePoint).
2. Haga clic en **usuarios y grupos**. 
3. Haga clic en **Agregar usuario** para agregar un usuario o grupo que tendrá permisos para iniciar sesión en SharePoint con Azure ad.
4. Seleccione el usuario o grupo y, a continuación, haga clic en **asignar**.
 
Se ha concedido permiso al usuario en Azure AD, pero también se le debe conceder el permiso en SharePoint. Siga estos pasos para establecer los permisos para obtener acceso a la aplicación web.

1. En Administración central, haga clic en **Administración de aplicaciones**.
2. En la sección **Aplicaciones web** de la página **Administración de aplicaciones**, haga clic en **Administrar aplicaciones web**.
3. Haga clic en la aplicación web adecuada y, a continuación, haga clic en **Directiva de usuario**.
4. En Directiva de aplicación Web, haga clic en **Agregar usuarios**.<br/>![Buscar a un usuario por su notificación de nombre](media/SAML11/fig11-searchbynameclaim.png)<br/>
5. En el cuadro de diálogo **Agregar usuarios**, haga clic en la zona apropiada en la sección **Zonas** y, después, haga clic en **Siguiente**.
6. En el cuadro de diálogo **Directiva de aplicación web** , en la sección **elegir usuarios** , haga clic en el icono **examinar** .
7. En el cuadro de texto **Buscar** , escriba el nombre de inicio de sesión de un usuario en el directorio y haga clic en **Buscar**. <br/>Ejemplo: *demouser@blueskyabove.onmicrosoft.com*.
8. En el encabezado AzureAD de la vista de lista, seleccione la propiedad Name y haga clic en **Agregar** y, a continuación, haga clic en **Aceptar** para cerrar el cuadro de diálogo.
9. En permisos, haga clic en **control total**.<br/>![Concesión de control total a un usuario de notificaciones](media/SAML11/fig12-grantfullcontrol.png)<br/>
10. Haga clic en **Finalizar** y, después, en **Aceptar**.

## <a name="step-6-add-a-saml-11-token-issuance-policy-in-azure-ad"></a>Paso 6: agregar una directiva de emisión de token de SAML 1,1 en Azure AD

Cuando se crea la aplicación de Azure AD en el portal, el valor predeterminado es usar SAML 2,0. SharePoint Server 2016 requiere el formato de token SAML 1,1. El siguiente script quitará la Directiva SAML 2,0 predeterminada y agregará una nueva Directiva para emitir tokens SAML 1,1. 

> Este código requiere descargar los ejemplos adjuntos que [demuestran la interacción con el gráfico de Azure Active](https://github.com/kaevans/spsaml11/tree/master/scripts)Directory. Si descarga los scripts como un archivo ZIP desde GitHub a un escritorio de Windows, asegúrese de desbloquear el `MSGraphTokenLifetimePolicy.psm1` archivo de módulo de script y `Initialize.ps1` el archivo de script (haga clic con el botón secundario en propiedades, elija desbloquear y haga clic en Aceptar). 
![Desbloqueo de archivos descargados](media/SAML11/fig17-unblock.png)

Una vez que se haya descargado el script de ejemplo, cree un nuevo script de PowerShell con el código siguiente, reemplazando el `Initialize.ps1` marcador de posición por la ruta de acceso de archivo del equipo local descargado. Reemplace el marcador de posición del identificador de objeto de la aplicación por el identificador del objeto de la aplicación que escribió en la tabla 1. Una vez creado, ejecute el script de PowerShell. 

```
function AssignSaml11PolicyToAppPrincipal
{
    Param(
        [Parameter(Mandatory=$true)]
        [string]$pathToInitializeScriptFile, 
        [Parameter(Mandatory=$true)]
        [string]$appObjectid
    )

    $folder = Split-Path $pathToInitializeScriptFile
    Push-Location $folder

    #Loads the dependent ADAL module used to acquire tokens
    Import-Module $pathToInitializeScriptFile 

    #Gets the existing token issuance policy
    $existingTokenIssuancePolicy = Get-PoliciesAssignedToServicePrincipal -servicePrincipalId $appObjectid | ?{$_.type -EQ "TokenIssuancePolicy"} 
    Write-Host "The following TokenIssuancePolicy policies are assigned to the service principal." -ForegroundColor Green
    Write-Host $existingTokenIssuancePolicy -ForegroundColor White
    $policyId = $existingTokenIssuancePolicy.objectId

    #Removes existing token issuance policy
    Write-Host "Only a single policy can be assigned to the service principal. Removing the existing policy with ID $policyId" -ForegroundColor Green
    Remove-PolicyFromServicePrincipal -policyId $policyId -servicePrincipalId $appObjectid

    #Creates a new token issuance policy and assigns to the service principal
    Write-Host "Adding the new SAML 1.1 TokenIssuancePolicy" -ForegroundColor Green
    $policy = Add-TokenIssuancePolicy -DisplayName SPSAML11 -SigningAlgorithm "http://www.w3.org/2001/04/xmldsig-more#rsa-sha256" -TokenResponseSigningPolicy TokenOnly -SamlTokenVersion "1.1"
    Write-Host "Assigning the new SAML 1.1 TokenIssuancePolicy $policy.objectId to the service principal $appObjectid" -ForegroundColor Green
    Set-PolicyToServicePrincipal -policyId $policy.objectId -servicePrincipalId $appObjectid
    Pop-Location
}

#Only edit the following two variables
$pathToInitializeScriptFile = "<file path of Initialize.ps1>"
$appObjectid = "<Application Object ID from Table 1>"

AssignSaml11PolicyToAppPrincipal $pathToInitializeScriptFile $appObjectid
```
> [!IMPORTANT]
> Los scripts de PowerShell no están firmados y es posible que se le pida que establezca la Directiva de ejecución. Para obtener más información sobre las directivas de ejecución, consulte [acerca de las directivas de ejecución](http://go.microsoft.com/fwlink/?LinkID=135170). Además, es posible que necesite abrir un símbolo del sistema con privilegios elevados para ejecutar correctamente los comandos contenidos en los scripts de ejemplo.

Estos comandos de PowerShell de ejemplo son ejemplos de cómo ejecutar consultas en la API de Graph. Para obtener más información sobre las directivas de emisión de tokens con Azure AD, consulte la [referencia de la API de Graph para operaciones en la Directiva](https://msdn.microsoft.com/en-us/library/azure/ad/graph/api/policy-operations#create-a-policy).

## <a name="step-7-verify-the-new-provider"></a>Paso 7: comprobar el nuevo proveedor

Abra un explorador para la dirección URL de la aplicación web que configuró en los pasos anteriores. Se le redirige a iniciar sesión en Azure AD.

![Iniciar sesión en Azure AD configurado para Federación](media/SAML11/fig13-examplesignin.png)

Se le preguntará si desea mantener la sesión iniciada.

![¿Mantener la sesión iniciada?](media/SAML11/fig14-staysignedin.png)

Por último, puede tener acceso al sitio que ha iniciado sesión como usuario desde su inquilino de Azure Active Directory.

![Usuario ha iniciado sesión en SharePoint](media/SAML11/fig15-signedinsharepoint.png)

## <a name="managing-certificates"></a>Administración de certificados
Es importante comprender que el certificado de firma que se ha configurado para el proveedor de identidades de confianza en el paso 4 anterior tiene una fecha de expiración y debe renovarse. Consulte el artículo [administrar certificados para el inicio de sesión único federado en Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-sso-certs) para obtener información sobre la renovación de certificados. Una vez renovado el certificado en Azure AD, descárguelo en un archivo local y use el siguiente script para configurar el proveedor de identidades de confianza con el certificado de firma renovado. 

```
$filepath="<Full path to renewed SAML signing certificate file>"
$cert= New-Object System.Security.Cryptography.X509Certificates.X509Certificate2($filePath)
New-SPTrustedRootAuthority -Name "AzureAD" -Certificate $cert
Get-SPTrustedIdentityTokenIssuer "AzureAD" | Set-SPTrustedIdentityTokenIssuer -ImportTrustCertificate $cert
```
## <a name="configuring-one-trusted-identity-provider-for-multiple-web-applications"></a>Configuración de un proveedor de identidades de confianza para varias aplicaciones Web
La configuración funciona para una aplicación web única, pero necesita una configuración adicional si tiene previsto usar el mismo proveedor de identidad de confianza para varias aplicaciones Web. Por ejemplo, supongamos que hemos ampliado una aplicación web para usar `https://portal.contoso.local` la dirección URL y ahora desea autenticar también `https://sales.contoso.local` a los usuarios. Para ello, es necesario actualizar el proveedor de identidades para que respete el parámetro WReply y actualizar el registro de la aplicación en Azure AD para agregar una dirección URL de respuesta.

1. En Azure portal, abra el directorio de Azure AD. Haga clic en **registros de aplicaciones**y, a continuación, en **ver todas las aplicaciones**. Haga clic en la aplicación que creó anteriormente (integración de SAML de SharePoint).
2. Haga clic en **configuración**.
3. En la hoja configuración, haga clic en **URL de respuesta**. 
4. Agregue la dirección URL de la aplicación web adicional `/_trust/default.aspx` con anexado a la dirección URL ( `https://sales.contoso.local/_trust/default.aspx`como) y haga clic en **Guardar**. 
5. En el servidor de SharePoint, abra el **Shell de administración de sharepoint 2016** y ejecute los siguientes comandos, usando el nombre del emisor de tokens de identidad de confianza que usó anteriormente.

```
$t = Get-SPTrustedIdentityTokenIssuer "AzureAD"
$t.UseWReplyParameter=$true
$t.Update()
```
6. En administración central, vaya a la aplicación web y habilite el proveedor de identidades de confianza existente. Recuerde también configurar la dirección URL de la página de inicio de sesión como página `/_trust/`de inicio de sesión personalizada.
7. En administración central, haga clic en la aplicación web y elija **Directiva de usuario**. Agregue un usuario con los permisos adecuados, tal y como se muestra anteriormente en este artículo.

## <a name="fixing-people-picker"></a>Corrección del selector de personas
Los usuarios ahora pueden iniciar sesión en SharePoint 2016 mediante identidades de Azure AD, pero todavía hay oportunidades para mejorar la experiencia del usuario. Por ejemplo, la búsqueda de un usuario presenta varios resultados de búsqueda en el selector de personas. Hay un resultado de búsqueda para cada uno de los 3 tipos de notificación que se crearon en la asignación de notificación. Para elegir un usuario con el selector de personas, debe escribir su nombre de usuario exactamente y elegir el **nombre** de notificación resultado.

![Resultados de la búsqueda de notificaciones](media/SAML11/fig16-claimssearchresults.png)

No hay ninguna validación de los valores que busque, lo que puede dar lugar a errores ortográficos o a los usuarios que elijan accidentalmente el tipo de notificación **** incorrecto para asignarlo, por ejemplo, la notificación de apellidos. Esto puede impedir que los usuarios tengan acceso a los recursos correctamente.

Para ayudar con este escenario, hay una solución de código abierto denominada [AzureCP](https://yvand.github.io/AzureCP/) que proporciona un proveedor de notificaciones personalizado para SharePoint 2016. Usará el gráfico de Azure AD para resolver lo que los usuarios especifican y realizan la validación. Obtenga más información en [AzureCP](https://yvand.github.io/AzureCP/). 

## <a name="additional-resources"></a>Recursos adicionales

[Introducción a WS-Federation](https://go.microsoft.com/fwlink/p/?linkid=188052)
  
[Adopción de la nube y soluciones híbridas](cloud-adoption-and-hybrid-solutions.md)
  
## <a name="join-the-discussion"></a>Participar en la discusión

|**Póngase en contacto con nosotros**|**Descripción**|
|:-----|:-----|
|**¿Qué soluciones necesita?** <br/> |Estamos creando contenido para soluciones que abarcan varios productos y servicios de Microsoft. Díganos qué piensa sobre nuestras soluciones entre servidores o solicite soluciones específicas por correo electrónico a [MODAcontent@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).<br/> |
|**Participe en la discusión sobre soluciones** <br/> |Si es un apasionado de las soluciones basadas en la nube, puede unirse a Cloud Adoption Advisory Board (CAAB) para conectarse a una interesante comunidad de mayor tamaño formada por desarrolladores de contenido de Microsoft, profesionales del sector y clientes de todo el mundo. Para unirse, agregue a su usuario como miembro del [espacio CAAB (Cloud Adoption Advisory Board)](https://aka.ms/caab) de Microsoft Tech Community y envíenos un correo electrónico a [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Cualquiera puede leer contenido relacionado con la comunidad en el [blog de CAAB](https://blogs.technet.com/b/solutions_advisory_board/). Pero los miembros de CAAB reciben invitaciones a seminarios web privados donde se describen nuevos recursos y soluciones de adopción de la nube.  <br/> |
|**Obtenga los archivos de arte que ve aquí** <br/> |Si quiere recibir una copia editable de las ilustraciones que se muestran en este artículo, estaremos encantados de enviárselas. Envíe su solicitud por correo electrónico, incluida la dirección URL y el título de la ilustración, a [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).  <br/> |
   

