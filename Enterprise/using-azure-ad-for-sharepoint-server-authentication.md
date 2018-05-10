---
title: Con Azure AD para la autenticación de SharePoint Server
ms.author: tracyp
author: MSFTTracyP
ms.reviewer:
- kirke
- josephd
- kirks
manager: laurawi
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Hybrid
ms.custom: Ent_Solutions
ms.assetid: ''
description: 'Resumen: Obtenga información sobre cómo el desvío de Azure Access Control Service y usar SAML 1.1 para autenticar a los usuarios de SharePoint Server con Azure Active Directory.'
ms.openlocfilehash: 8a844cf1f45f6285e676439f934b9119a757804f
ms.sourcegitcommit: c52bd6eaa8772063f9e2bd1acf10fa23422a2b92
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/09/2018
---
# <a name="using-azure-ad-for-sharepoint-server-authentication"></a>Con Azure AD para la autenticación de SharePoint Server

 **Resumen:** Obtenga información sobre cómo autenticar los usuarios de SharePoint Server 2016 con Azure Active Directory.
  
> [!NOTE]
> En este artículo se basa en el trabajo de Kirk Evans, jefe de programa de entidad de seguridad de Microsoft. 

<blockquote>
<p>En este artículo se hace referencia a ejemplos de código para interactuar con el gráfico de Azure Active Directory. Puede descargar los ejemplos de código [aquí](https://github.com/kaevans/spsaml11/tree/master/scripts).</p>
</blockquote>

SharePoint Server 2016 proporciona la capacidad para autenticar a los usuarios mediante la autenticación basada en notificaciones, haciendo que sea más fácil de administrar los usuarios mediante la autenticación de ellos con distintos proveedores de identidades que confía pero otra persona administra. Por ejemplo, en lugar de administrar la autenticación de usuario a través de los servicios de dominio de Active Directory (AD DS), podría permitir a los usuarios autenticarse con Azure Active Directory (AD Azure). Esto habilita la autenticación para los usuarios solo en nube con el sufijo onmicrosoft.com en su nombre de usuario, los usuarios sincronizan con un directorio local y usuarios invitado desde otros directorios invitación. También permite aprovechar las características de Azure AD como la autenticación multifactor y capacidades avanzadas de informes.

> [!IMPORTANT]
> La solución descrita en este artículo también se puede usar con SharePoint Server 2013; Sin embargo, tenga en cuenta que SharePoint Server 2013 se está acercando el final de soporte técnico. Para obtener más información, vea [La directiva de ciclo de vida de Microsoft](https://support.microsoft.com/en-us/lifecycle/search?alpha=SharePoint%20Server%202013) y [Actualizado del producto servicio de actualización de directiva para SharePoint 2013](https://technet.microsoft.com/library/684173bb-e90a-4eb7-b268-b8d7458bc802(v=office.16).aspx).

En este artículo se explica cómo puede usar Azure AD para autenticar a los usuarios en lugar de sus instalaciones en AD DS. En esta configuración, Azure AD se convierte en un proveedor de identidad de confianza para SharePoint Server 2016. Esta configuración agrega un método de autenticación de usuario que es independiente de la autenticación de AD DS utilizada por la instalación de SharePoint Server 2016 propio. Para beneficiarse de este artículo, debe estar familiarizado con WS-Federation. Para obtener más información, consulte [Understanding WS-Federation](https://go.microsoft.com/fwlink/p/?linkid=188052).

![Con Azure AD para la autenticación de SharePoint](images/SAML11/fig1-architecture.png)

Anteriormente, esta configuración habría requerido un servicio de federación como Azure Access Control Service (ACS) en la nube o en un entorno que hospeda los servicios de federación de Active Directory (AD FS) transformar los tokens de SAML 2.0 a la versión 1.1 de SAML. Esta transformación ya no es necesaria como Azure AD ahora permite emite tokens SAML 1.1. El diagrama anterior muestra cómo funciona la autenticación para los usuarios de SharePoint 2016 en esta configuración, que muestra que ya no es un requisito para un intermediario realizar esta transformación.

> [!NOTE]
> Esta configuración funciona si la granja de servidores de SharePoint está hospedado en máquinas virtuales de Azure o local. No requiere la apertura de puertos de firewall adicionales aparte de asegurar que los usuarios puede obtener acceso a Azure Active Directory desde su explorador.

Para obtener información acerca de la accesibilidad de SharePoint 2016, consulte [Las pautas de accesibilidad en SharePoint Server 2016](https://go.microsoft.com/fwlink/p/?LinkId=393123).

## <a name="configuration-overview"></a>Descripción general de la configuración

Siga estos pasos generales para configurar el entorno para usar Azure AD como un proveedor de identidad de 2016 de SharePoint Server.

1. Crear un nuevo directorio de Azure AD o utilizar su directorio existente.
2. Asegúrese de que la zona para la aplicación web que se desea proteger con Azure AD está configurada para usar SSL.
3. Cree una nueva aplicación de empresa en Azure AD.
4. Configurar un nuevo proveedor de identidad de confianza en SharePoint Server 2016.
5. Establezca los permisos para la aplicación web.
6. Agregar una directiva de emisión de token de SAML 1.1 en Azure AD.
7. Compruebe el nuevo proveedor.

Las secciones siguientes describen cómo realizar estas tareas.

## <a name="step-1-create-a-new-azure-ad-directory-or-use-your-existing-directory"></a>Paso 1: Crear un nuevo directorio de Azure AD o utilizar su directorio existente

En el Portal de Azure ([https://portal.azure.com](https://portal.azure.com)), cree un nuevo directorio. Proporcionar el nombre de la organización, nombre de dominio inicial y el país o la región.

![Creación de un directorio](images/SAML11/fig2-createdirectory.png) 

 Si ya tiene un directorio, como el que se usa para Microsoft Office 365 o su suscripción de Microsoft Azure, puede usar ese directorio en su lugar. Debe tener permisos para registrar aplicaciones en el directorio.

## <a name="step-2-ensure-the-zone-for-the-web-application-that-you-want-to-secure-with-azure-ad-is-configured-to-use-ssl"></a>Paso 2: Asegúrese de la zona para la aplicación web que se desea proteger con Azure AD está configurada para usar SSL

En este artículo se ha escrito con la arquitectura de referencia en el cuadro [ejecutar una granja de servidores de SharePoint Server 2016 en Azure de alta disponibilidad](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint). Que lo acompaña secuencias de comandos del artículo utilizadas para implementar la solución descrita en [este artículo](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint) crean un sitio que no use SSL.  

Uso de SAML requiere la aplicación estén configurados para usar SSL. Si la aplicación web de SharePoint no está configurada para usar SSL, siga estos pasos para crear un nuevo certificado autofirmado para configurar la aplicación web para SSL. Esta configuración solo está pensada para un entorno de laboratorio y no está pensada para producción. Los entornos de producción deben usar un certificado autofirmado.

1. Vaya a **Administración Central** > **Administración de aplicaciones** > **Administrar aplicaciones Web**y elija la aplicación web que necesita para poder ampliarse y para usar SSL. Seleccione la aplicación web y haga clic en el botón de **la cinta de opciones Extend** . Extender la aplicación web para usar la misma dirección URL, pero use SSL con el puerto 443.</br>![Ampliación de la aplicación web a otro sitio IIS](images/SAML11/fig3-extendwebapptoiis.png)</br>
2. En Administrador de IIS, haga doble clic en **Certificados de servidor**.
3. En el panel **acciones** , haga clic en **Crear certificado autofirmado**. Escriba un nombre descriptivo para el certificado en la especifique un nombre descriptivo para el cuadro de certificado y, a continuación, haga clic en **Aceptar**.
4. En el cuadro de diálogo **Modificar enlace de sitio** , asegúrese del nombre de host es el mismo que el nombre descriptivo, como se muestra en la siguiente imagen.</br>![Edición de enlace del sitio en IIS](images/SAML11/fig4-editsitebinding.png)</br>

Cada uno de los servidores front-end web en la granja de servidores de SharePoint requiere configurar el certificado para el enlace del sitio en IIS.


## <a name="step-3-create-a-new-enterprise-application-in-azure-ad"></a>Paso 3: Crear una nueva aplicación de empresa en Azure AD

1. En el Portal de Azure ([https://portal.azure.com](https://portal.azure.com)), abra el directorio de Azure AD. Haga clic en **Aplicaciones de empresa**y, a continuación, haga clic en **nueva aplicación**. Elija la **Galería de la no aplicación**. Proporcione un nombre como la *Integración de SAML de SharePoint* y haga clic en **Agregar**.</br>![Adición de una nueva aplicación que no sean Galería](images/SAML11/fig5-addnongalleryapp.png)</br>
2. Haga clic en el vínculo de inicio de sesión único en el panel de navegación para configurar la aplicación. Cambiar la lista desplegable de **modo de inicio de sesión único** **SAML-based Sign-on** para mostrar las propiedades de configuración de SAML para la aplicación. Configurar con las siguientes propiedades:</br>
    - Identificador:`urn:sharepoint:portal.contoso.local`
    - Dirección URL de respuesta:`https://portal.contoso.local/_trust/default.aspx`
    - Inicio de sesión en dirección URL:`https://portal.contoso.local/_trust/default.aspx`
    - Identificador de usuario:`user.userprincipalname`</br>
    - Nota: No olvide cambiar las direcciones URL mediante el reemplazo de *portal.contoso.local* con la dirección URL del sitio de SharePoint que desea proteger.</br>
3. Configurar una tabla (similar a la tabla 1) incluye las filas siguientes:</br> 
    - Dominio Kerberos
    - Ruta de acceso completa al archivo de certificado de firma de SAML
    - SAML Single Sign-On dirección URL del servicio (sustituyendo */saml2* por */wsfed*)
    - Identificador de objeto de aplicación. </br>
Copie el valor de *identificador* en la propiedad de *dominio Kerberos* en una tabla (consulte la tabla 1 a continuación.)
4. Guarde los cambios.
5. Haga clic en el vínculo **Configurar (nombre de la aplicación)** para obtener acceso a la página Configurar la sesión.</br>![Configuración de un inicio de sesión único en la página](images/SAML11/fig7-configssopage.png)</br> 
    -  Haga clic en el vínculo de **SAML certificado de firma de-sin procesar** para descargar el certificado de firma de SAML como un archivo con la extensión .cer. Copie y pegue la ruta de acceso completa para el archivo descargado en la tabla.
    - Copie y pegue el vínculo SAML Single Sign-On dirección URL del servicio en su, reemplazando la parte */saml2* de la dirección URL con */wsfed*.</br>
6.  Desplácese hasta el panel de **Propiedades** de la aplicación. Copie y pegue el valor del identificador de objeto en la tabla que configurar en el paso 3.</br>![Panel de propiedades de la aplicación](images/SAML11/fig8-propertiespane.png)</br>
7. Uso de los valores que se capturó, asegúrese de que la tabla configurado en el paso 3 es similar a la tabla 1.


| La tabla 1: Los valores capturados  |  |
|---------|---------|
|Dominio Kerberos | `urn:sharepoint:portal.contoso.local` |
|Ruta de acceso completa al archivo de certificado de firma de SAML | `C:/temp/SharePoint SAML Integration.cer`  |
|Dirección URL del servicio de inicio de sesión único de SAML (reemplace /saml2 por /wsfed) | `https://login.microsoftonline.com/b1726649-b616-460d-8d20-defab80d476c/wsfed` |
|Identificador del objeto de aplicación | `a812f48b-d1e4-4c8e-93be-e4808c8ca3ac` |

> [!IMPORTANT]
> Reemplace el valor de */saml2* en la dirección URL con */wsfed*. El extremo */saml2* procesará los tokens SAML 2.0. El extremo de */wsfed* permite tokens SAML 1.1 de procesamiento y se requiere para la federación de SharePoint 2016 SAML.

## <a name="step-4-configure-a-new-trusted-identity-provider-in-sharepoint-server-2016"></a>Paso 4: Configurar un nuevo proveedor de identidad de confianza en SharePoint Server 2016

Inicie sesión en el servidor de SharePoint Server 2016 y abra el Shell de administración de SharePoint 2016. Rellene los valores de $realm, $wsfedurl y $filepath desde la tabla 1 y ejecute los comandos siguientes para configurar un nuevo proveedor de identidad de confianza.

> [!TIP]
> Si está familiarizado con el uso de PowerShell o desea obtener más información acerca de cómo funciona la PowerShell, vea [SharePoint PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/overview?view=sharepoint-ps). 

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

A continuación, siga estos pasos para habilitar al proveedor de identidades de confianza para la aplicación:
1. En Administración Central, vaya a **Administrar las aplicaciones Web** y seleccione la aplicación web que se desee proteger con Azure AD. 
2. En la cinta de opciones, haga clic en **Proveedores de autenticación** y elija la zona que desea utilizar.
3. Seleccione el **proveedor de identidad de confianza** y seleccione el proveedor de identidad que acaba de registrar llamado *AzureAD*.  
4. En la configuración de dirección URL de la página de inicio de sesión, seleccione **iniciar sesión personalizada en la página** y proporcionar el valor "/ _trust /". 
5. Haga clic en **Aceptar**.

![Configuración de su proveedor de autenticación](images/SAML11/fig10-configauthprovider.png)

## <a name="step-5-set-the-permissions"></a>Paso 5: Establecer los permisos

Los usuarios que se inicie sesión en Azure AD y tener acceso a SharePoint deben tener acceso a la aplicación. 

1. En el Portal de Azure, abra el directorio de Azure AD. Haga clic en **Aplicaciones de empresa**y, a continuación, haga clic en **todas las aplicaciones**. Haga clic en la aplicación que creó anteriormente (integración de SAML de SharePoint).
2. Haga clic en **usuarios y grupos**. 
3. Haga clic en **Agregar usuario** para agregar un usuario o grupo que se tiene permisos para iniciar sesión en SharePoint con Azure AD.
4. Seleccione el usuario o grupo, a continuación, haga clic en **asignar**.
 
El usuario se ha concedido permiso en Azure AD, pero también debe tener permiso de SharePoint. Use los siguientes pasos para establecer los permisos para tener acceso a la aplicación web.

1. En Administración central, haga clic en **Administración de aplicaciones**.
2. En la sección **Aplicaciones web** de la página **Administración de aplicaciones**, haga clic en **Administrar aplicaciones web**.
3. Haga clic en la aplicación web adecuada y, a continuación, haga clic en **Directiva de usuario**.
4. En la directiva de aplicación Web, haga clic en **Agregar usuarios**.</br>![Búsqueda de un usuario por su nombre de la notificación](images/SAML11/fig11-searchbynameclaim.png)</br>
5. En el cuadro de diálogo **Agregar usuarios**, haga clic en la zona apropiada en la sección **Zonas** y, después, haga clic en **Siguiente**.
6. En el cuadro de diálogo **Directiva de aplicación Web** , en la sección **Elegir usuarios** , haga clic en el icono **Examinar** .
7. En el cuadro de texto **Buscar** , escriba el nombre de inicio de sesión de un usuario en el directorio y haga clic en **Buscar**. </br>Ejemplo: *demouser@blueskyabove.onmicrosoft.com*.
8. Bajo el encabezado de AzureAD en la vista de lista, seleccione la propiedad name y haga clic en **Agregar** , a continuación, haga clic en **Aceptar** para cerrar el cuadro de diálogo.
9. En permisos, haga clic en **Control total**.</br>![Conceder control total a un usuario de notificaciones](images/SAML11/fig12-grantfullcontrol.png)</br>
10. Haga clic en **Finalizar** y, a continuación, en **Aceptar**.

## <a name="step-6-add-a-saml-11-token-issuance-policy-in-azure-ad"></a>Paso 6: Agregar una directiva de emisión de token de SAML 1.1 en Azure AD

Cuando se crea la aplicación de Azure AD en el portal, el valor predeterminado es con SAML 2.0. SharePoint Server 2016 requiere el formato de token de SAML 1.1. La siguiente secuencia de comandos se quite la directiva de SAML 2.0 predeterminada y agregue una nueva directiva de los tokens SAML 1.1 del problema. Este código requiere la descarga de la que se incluyen [ejemplos que muestran la interacción con Azure Active Directory gráfico](https://github.com/kaevans/spsaml11/tree/master/scripts). 


```
Import-Module <file path of Initialize.ps1> 
$objectid = "<Application Object ID from Table 1>"
$saml2policyid = Get-PoliciesAssignedToServicePrincipal -servicePrincipalId $objectid | ?{$_.displayName -EQ "TokenIssuancePolicy"} | select objectId
Remove-PolicyFromServicePrincipal -policyId $saml2policyid -servicePrincipalId $objectid
$policy = Add-TokenIssuancePolicy -DisplayName SPSAML11 -SigningAlgorithm "http://www.w3.org/2001/04/xmldsig-more#rsa-sha256" -TokenResponseSigningPolicy TokenOnly -SamlTokenVersion "1.1"
Set-PolicyToServicePrincipal -policyId $policy.objectId -servicePrincipalId $objectid
```
> Tenga en cuenta que es importante ejecutar el `Import-Module` tal como se muestra en este ejemplo de comando. Esto carga un módulo dependiente que contiene los comandos que se muestra. Debe abrir un símbolo del sistema con privilegios elevados para ejecutar estos comandos en correctamente.

Estos comandos de PowerShell de ejemplo son ejemplos de cómo ejecutar consultas en la API de gráfico. Para obtener más detalles sobre las directivas de emisión Token con Azure AD, vea la [referencia de la API de gráfico para las operaciones en la directiva](https://msdn.microsoft.com/en-us/library/azure/ad/graph/api/policy-operations#create-a-policy).

## <a name="step-7-verify-the-new-provider"></a>Paso 7: Comprobar el nuevo proveedor

Abra un explorador a la dirección URL de la aplicación web que configuró en los pasos anteriores. Se le redirige para iniciar sesión en Azure AD.

![Iniciar sesión en Azure AD configurado para la federación](images/SAML11/fig13-examplesignin.png)

Se le pregunte si desea mantener la sesión de.

![¿Mantener la sesión de?](images/SAML11/fig14-staysignedin.png)

Por último, se puede obtener acceso al sitio iniciado sesión como un usuario desde el inquilino de Azure Active Directory.

![Usuario que ha iniciado sesión en SharePoint](images/SAML11/fig15-signedinsharepoint.png)

## <a name="managing-certificates"></a>Administración de certificados
Es importante comprender que el certificado de firma que se configuró para el proveedor de identidad de confianza en el paso 4 anterior tiene una fecha de caducidad y debe renovarse. Consulte el artículo [Administrar certificados federada single sign - on en Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-sso-certs) para obtener información sobre renovación de certificados. Una vez que el certificado se ha renovado en Azure AD, descargar en un archivo local y usar la siguiente secuencia de comandos para configurar el proveedor de identidades de confianza con el certificado de firma renovado. 

```
$filepath="<Full path to renewed SAML signing certificate file>"
$cert= New-Object System.Security.Cryptography.X509Certificates.X509Certificate2($filePath)
New-SPTrustedRootAuthority -Name "AzureAD" -Certificate $cert
Get-SPTrustedIdentityTokenIssuer "AzureAD" | Set-SPTrustedIdentityTokenIssuer -ImportTrustCertificate $cert
```
## <a name="configuring-one-trusted-identity-provider-for-multiple-web-applications"></a>Configuración de un proveedor de identidad de confianza para varias aplicaciones web
La configuración funciona para una sola aplicación web, pero necesita una configuración adicional si tiene la intención de utilizar el mismo proveedor de identidades de confianza para varias aplicaciones web. Por ejemplo, supongamos que nos hubiéramos extender una aplicación web para usar la dirección URL `https://portal.contoso.local` y ahora desea autenticar a los usuarios a `https://sales.contoso.local` así como. Para ello, es necesario actualizar el proveedor de identidad para respetar el parámetro WReply y actualizar el registro de aplicación en Azure AD para agregar una dirección URL de respuesta.

1. En el Portal de Azure, abra el directorio de Azure AD. Haga clic en **registros de aplicación**y, a continuación, haga clic en **Ver todas las aplicaciones**. Haga clic en la aplicación que creó anteriormente (integración de SAML de SharePoint).
2. Haga clic en **configuración**.
3. En el servidor blade de configuración, haga clic en **Las direcciones URL de respuesta**. 
4. Agregue la dirección URL para la aplicación web adicionales (como `https://sales.contoso.local`) y haga clic en **Guardar**. 
5. En el servidor de SharePoint, abra el **Shell de administración de SharePoint 2016** y ejecute los comandos siguientes, con el nombre del emisor de tokens de identidad de confianza que usó anteriormente.

```
$t = Get-SPTrustedIdentityTokenIssuer "AzureAD"
$t.UseWReplyParameter=$true
$t.Update()
```
6. En Administración Central, vaya a la aplicación web y habilitar al proveedor de identidad de confianza existente. Recuerde que debe configurar también la dirección URL de la página de inicio de sesión como un inicio de sesión personalizado en la página `/_trust/`.
7. En Administración Central, haga clic en la aplicación web y elija la **Directiva de usuario**. Agregar un usuario con los permisos adecuados, tal como se muestra anteriormente en este artículo.

## <a name="fixing-people-picker"></a>Fijación de selector de personas
Los usuarios ahora pueden iniciar en 2016 de SharePoint con las identidades de Azure AD, pero aún hay oportunidades para la mejora de la experiencia del usuario. Por ejemplo, al buscar un usuario, presenta varios resultados de búsqueda en el selector de personas. No hay un resultado de búsqueda para cada uno de los tipos de 3 notificación que se crearon en la asignación de notificación. Para elegir un usuario mediante el selector de personas, debe escribir exactamente su nombre de usuario y elija el **nombre de la** notificación de resultados.

![Los resultados de búsqueda de notificaciones](images/SAML11/fig16-claimssearchresults.png)

No hay ninguna validación en los valores que se busca, lo que puede provocar errores ortográficos o una notificación a los usuarios elegir accidentalmente el incorrecto tipo para asignar como el **apellido** de notificación. Esto puede impedir que los usuarios acceso a los recursos correctamente.

Para ayudar con este escenario, no hay un origen de Abrir solución denominada [AzureCP](https://yvand.github.io/AzureCP/) que proporciona un proveedor de notificaciones personalizados para SharePoint 2016. Usará el gráfico de AD de Azure para resolver lo que los usuarios escribir y realizan validación. Encontrará más información en [AzureCP](https://yvand.github.io/AzureCP/). 

## <a name="additional-resources"></a>Recursos adicionales

[Introducción a WS-Federation](https://go.microsoft.com/fwlink/p/?linkid=188052)
  
[Adopción de la nube y soluciones híbridas](cloud-adoption-and-hybrid-solutions.md)
  
## <a name="join-the-discussion"></a>Participar en la discusión

|**Póngase en contacto con nosotros**|**Descripción**|
|:-----|:-----|
|**¿Qué soluciones necesita?** <br/> |Estamos creando contenido para soluciones que abarcan varios productos y servicios de Microsoft. Díganos qué piensa sobre nuestras soluciones entre servidores o solicite soluciones específicas por correo electrónico a [MODAcontent@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).<br/> |
|**Participe en la discusión sobre soluciones** <br/> |Si es un apasionado de las soluciones basadas en la nube, puede unirse a Cloud Adoption Advisory Board (CAAB) para conectarse a una interesante comunidad de mayor tamaño formada por desarrolladores de contenido de Microsoft, profesionales del sector y clientes de todo el mundo. Para unirse, agregue a su usuario como miembro del [espacio CAAB (Cloud Adoption Advisory Board)](https://aka.ms/caab) de Microsoft Tech Community y envíenos un correo electrónico a [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Cualquiera puede leer contenido relacionado con la comunidad en el [blog de CAAB](https://blogs.technet.com/b/solutions_advisory_board/). Pero los miembros de CAAB reciben invitaciones a seminarios web privados donde se describen nuevos recursos y soluciones de adopción de la nube.  <br/> |
|**Obtenga los archivos de arte que ve aquí** <br/> |Si quiere recibir una copia editable de las ilustraciones que se muestran en este artículo, estaremos encantados de enviárselas. Envíe su solicitud por correo electrónico, incluida la dirección URL y el título de la ilustración, a [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).  <br/> |
   

