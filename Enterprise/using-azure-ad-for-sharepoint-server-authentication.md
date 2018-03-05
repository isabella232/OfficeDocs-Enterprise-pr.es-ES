---
title: "Utiliza AD Azure para autenticación de servidor de SharePoint"
ms.author: tracyp
author: MSFTTracyP
ms.reviewer:
- kirke
- josephd
- kirks
manager: laurawi
ms.date: 3/2/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Hybrid
ms.custom: Ent_Solutions
ms.assetid: 
description: "Resumen: Conozca cómo omitir el servicio de Control de acceso de Azure y utilizar SAML 1.1 para autenticar a los usuarios de SharePoint Server con Active Directory de Azure."
ms.openlocfilehash: e346a79fae32c19e14ce852257d5643041faf5d4
ms.sourcegitcommit: b1cb876c8a8fca1c2d67b2bc8282f1361066962c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2018
---
# <a name="using-azure-ad-for-sharepoint-server-authentication"></a>Utiliza AD Azure para autenticación de servidor de SharePoint

 **Resumen:** Aprenda cómo autenticar a sus usuarios de 2016 de SharePoint Server con Active Directory de Azure.
  
> [!NOTE]
> En este artículo se basa en el trabajo de Kirk Evans, un administrador Principal de programas de Microsoft. 

<blockquote>
<p>En este artículo se refiere a los ejemplos de código para interactuar con el gráfico de Azure Active Directory. Puede descargar los ejemplos de código [aquí](https://1drv.ms/u/s!AuAlJmH2xI6Kg3ItzF78krMFxJu3).</p>
</blockquote>

SharePoint Server 2016 proporciona la capacidad para autenticar a los usuarios mediante la autenticación basada en notificaciones, facilitando la tarea de administrar los usuarios mediante la autenticación de con proveedores de identidades diferentes que confía pero otra persona administra. Por ejemplo, en lugar de administrar la autenticación del usuario a través de los servicios de dominio de Active Directory (AD DS), podría permitir a los usuarios autenticarse con Active Directory (AD Azure) de Azure. Esto permite la autenticación de los usuarios sólo nube con el sufijo onmicrosoft.com en su nombre de usuario, los usuarios sincronizan con un directorio local, invitó a los usuarios invitados desde otros directorios. También permite aprovechar las características de AD Azure como una autenticación multifactor y capacidades de reporting avanzadas.

> [!IMPORTANT]
> La solución descrita en este artículo también puede utilizarse con SharePoint Server 2013; Sin embargo, tenga en cuenta que SharePoint Server 2013 llega al final del periodo de soporte técnico. Para obtener más información, vea [Directiva de ciclo de vida de Microsoft](https://support.microsoft.com/en-us/lifecycle/search?alpha=SharePoint%20Server%202013) y [Actualiza producto Directiva de servicio para SharePoint 2013](https://technet.microsoft.com/library/684173bb-e90a-4eb7-b268-b8d7458bc802(v=office.16).aspx).

Este artículo explica cómo puede usar AD Azure para autenticar a los usuarios en lugar de sus instalaciones en AD DS. En esta configuración, AD Azure se convierte en un proveedor de identidad de confianza para SharePoint Server 2016. Esta configuración agrega un método de autenticación de usuario que es independiente de la autenticación de AD DS utilizada por la propia instalación de SharePoint Server 2016. Para beneficiarse de este artículo, debe estar familiarizado con WS-Federation. Para obtener más información, consulte [Understanding WS-Federation](https://go.microsoft.com/fwlink/p/?linkid=188052).

![Uso de Azure AD para autenticación de SharePoint](images/SAML11/fig1-architecture.png)

Anteriormente, esta configuración habría requerido un servicio de federación como Azure Access Control Service (ACS) en la nube o en un entorno que aloja los servicios de federación de Active Directory (AD FS) transformar los símbolos (tokens) de SAML 2.0 SAML 1.1. Esta transformación ya no es necesaria debido a que ahora AD Azure permite emisores tokens SAML 1.1. El diagrama anterior muestra cómo funciona la autenticación para los usuarios de SharePoint 2016 en esta configuración, demostrando que ya no es un requisito para un intermediario realizar esta transformación.

> [!NOTE]
> Esta configuración funciona si el conjunto de servidores de SharePoint se hospeda en Azure máquinas virtuales o locales. No requiere abrir puertos de firewall adicional aparte de asegurar que los usuarios puede tener acceso a Active Directory de Azure desde su explorador.

Para obtener información acerca de la accesibilidad de 2016 de SharePoint, consulte [Las pautas de accesibilidad de 2016 de SharePoint Server](https://go.microsoft.com/fwlink/p/?LinkId=393123).

## <a name="configuration-overview"></a>Descripción general de la configuración

Siga estos pasos generales para configurar su entorno para utilizar AD Azure como proveedor de identidad de 2016 de SharePoint Server.

1. Crear un nuevo directorio de Azure AD o utilizar su directorio existente.
2. Asegúrese de que la zona de la aplicación web que desea proteger con AD Azure está configurada para utilizar SSL.
3. Cree una nueva aplicación empresarial en Azure AD.
4. Configurar un nuevo proveedor de identidad de confianza en SharePoint Server 2016.
5. Establezca los permisos para la aplicación web.
6. Agregue una directiva de emisión de token SAML 1.1 en Azure AD.
7. Compruebe el nuevo proveedor.

Las secciones siguientes describen cómo realizar estas tareas.

## <a name="step-1-create-a-new-azure-ad-directory-or-use-your-existing-directory"></a>Paso 1: Crear un nuevo directorio de Azure AD o utilizar su directorio existente

En el Portal de Azure ([https://portal.azure.com](https://portal.azure.com)), cree un nuevo directorio. Proporcionar el nombre de la organización, nombre de dominio inicial y el país o región.

![Creación de un directorio](images/SAML11/fig2-createdirectory.png) 

 Si ya tiene un directorio como el que se usa para Microsoft Office 365 o la suscripción de Microsoft Azure, puede utilizar dicho directorio en su lugar. Debe tener permisos para registrar las aplicaciones en el directorio.

## <a name="step-2-ensure-the-zone-for-the-web-application-that-you-want-to-secure-with-azure-ad-is-configured-to-use-ssl"></a>Paso 2: Asegurar la zona para la aplicación web que desea proteger con AD Azure está configurada para utilizar SSL

Este artículo fue escrito con la arquitectura de referencia en [una granja de SharePoint Server 2016 en Azure de alta disponibilidad de ejecución](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint). Secuencias de comandos de acompañamiento del artículo utilizados para implementar la solución descrita en [este artículo](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint) crean un sitio que no utiliza SSL.  

El uso de SAML requiere que la aplicación se ha configurado para utilizar SSL. Si la aplicación web de SharePoint no está configurada para utilizar SSL, siga estos pasos para crear un nuevo certificado autofirmado para configurar la aplicación web para SSL. Esta configuración sólo está pensada para un entorno de laboratorio y no está pensada para la producción. Entornos de producción deben utilizar un certificado de firma.

1. Vaya a **Administración Central** > **Gestión de aplicaciones** > **Administrar aplicaciones Web**y elija la aplicación web que debe ampliarse para que use SSL. Seleccione la aplicación web y haga clic en el botón de la **cinta de opciones de extender** . Ampliar la aplicación web utilice la misma dirección URL sin utilizar SSL con el puerto 443.</br>![Ampliación de la aplicación web a otro sitio IIS](images/SAML11/fig3-extendwebapptoiis.png)</br>
2. En Administrador de IIS, haga doble clic en **Certificados de servidor**.
3. En el panel **acciones** , haga clic en **Crear certificado autofirmado**. Escriba un nombre descriptivo para el certificado en la especifique un nombre descriptivo para el cuadro de certificado y, a continuación, haga clic en **Aceptar**.
4. Desde el cuadro de diálogo **Modificar enlace de sitio** , asegúrese del nombre de host es el mismo que el nombre descriptivo, como se ilustra en la siguiente imagen.</br>![Editar enlace de sitio en IIS](images/SAML11/fig4-editsitebinding.png)</br>

Cada servidor web front-end en la granja de SharePoint requiere configurar el certificado para el enlace de sitio en IIS.


## <a name="step-3-create-a-new-enterprise-application-in-azure-ad"></a>Paso 3: Crear una nueva aplicación empresarial en Azure AD

1. En el Portal de Azure ([https://portal.azure.com](https://portal.azure.com)), abra el directorio de AD de Azure. **Aplicaciones de la empresa**, haga clic en **nueva aplicación**. Elija **Galería de no aplicación**. Proporcione un nombre, como la *Integración de SAML de SharePoint* y haga clic en **Agregar**.</br>![Agregar una nueva aplicación de galería no](images/SAML11/fig5-addnongalleryapp.png)</br>
2. Haga clic en el vínculo de inicio de sesión único del panel de exploración para configurar la aplicación. Cambiar la lista desplegable **modo de inicio de sesión único** **basado en SAML de sesión** para mostrar las propiedades de configuración de SAML para la aplicación. Configurar con las siguientes propiedades:</br>
    - Identificador:`urn:sharepoint:portal.contoso.local`
    - Dirección URL de respuesta:`https://portal.contoso.local/_trust/default.aspx`
    - URL de inicio de sesión:`https://portal.contoso.local/_trust/default.aspx`
    - Identificador de usuario:`user.userprincipalname`</br>
    - Nota: No olvide cambiar las direcciones URL sustituyendo *portal.contoso.local* por la dirección URL del sitio de SharePoint que desea proteger.</br>
3. Configurar una tabla (similar a la tabla 1 a continuación) incluye las filas siguientes:</br> 
    - Territorio
    - Ruta de acceso completa del archivo de certificado de firma de SAML
    - URL SAML Single Sign-On service (sustituyendo */saml2* por */wsfed*)
    - Identificador de objeto de la aplicación. </br>
Copia el valor del *identificador* de la propiedad del *territorio* en una tabla (ver tabla 1 a continuación.)
4. Guarde los cambios.
5. Haga clic en el vínculo **Configurar (nombre de la aplicación)** para tener acceso a la página de inicio de sesión de configuración.</br>![Cómo configurar un inicio de sesión único en la página](images/SAML11/fig7-configssopage.png)</br> 
    -  Haga clic en el vínculo de **SAML certificado de firma - Raw** para descargar el certificado de firma de SAML como un archivo con la extensión .cer. Copie y pegue la ruta de acceso completa del archivo descargado en la tabla.
    - Copie y pegue el vínculo SAML único Sign-On Service URL en su, sustituyendo la porción */saml2* de la dirección URL */wsfed*.</br>
6.  Desplácese hasta el panel de **Propiedades** para la aplicación. Copie y pegue el valor del identificador de objeto en la tabla que se configuró en el paso 3.</br>![Panel de propiedades para la aplicación](images/SAML11/fig8-propertiespane.png)</br>
7. Con los valores capturados, asegúrese de que la tabla que se configuró en el paso 3 es similar a la tabla 1.


| Tabla 1: Los valores capturados  |  |
|---------|---------|
|Territorio | `urn:sharepoint:portal.contoso.local` |
|Ruta de acceso completa del archivo de certificado de firma de SAML | `C:/temp/SharePoint SAML Integration.cer`  |
|Dirección URL del servicio de inicio de sesión único de SAML (reemplace /saml2 por /wsfed) | `https://login.microsoftonline.com/b1726649-b616-460d-8d20-defab80d476c/wsfed` |
|Id. de objeto de aplicación | `a812f48b-d1e4-4c8e-93be-e4808c8ca3ac` |

> [!IMPORTANT]
> Sustituya el valor de */saml2* en la dirección URL */wsfed*. El extremo */saml2* procesará tokens SAML 2.0. El extremo de */wsfed* permite tokens SAML 1.1 de procesamiento y se requiere para la federación de SharePoint 2016 SAML.

## <a name="step-4-configure-a-new-trusted-identity-provider-in-sharepoint-server-2016"></a>Paso 4: Configurar un nuevo proveedor de identidad de confianza en SharePoint Server 2016

Iniciar sesión en el servidor de SharePoint Server 2016 y abra el Shell de administración de SharePoint de 2016. Rellene los valores de $realm, $wsfedurl y $filepath en la tabla 1 y ejecute los comandos siguientes para configurar un nuevo proveedor de identidad de confianza.

> [!TIP]
> Si está acostumbrado a utilizar PowerShell o desea obtener más información acerca del funcionamiento de PowerShell, vea [SharePoint PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/overview?view=sharepoint-ps). 

```
$realm = "<Realm from Table 1>"
$wsfedurl="<SAML single sign-on service URL from Table 1>"
$filepath="<Full path to SAML signing certificate file from Table 1>"
$cert = New-Object 
System.Security.Cryptography.X509Certificates.X509Certificate2($filepath)
New-SPTrustedRootAuthority -Name "AzureAD" -Certificate $cert
$map = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" -IncomingClaimTypeDisplayName "name" -LocalClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn"
$map2 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname" -IncomingClaimTypeDisplayName "GivenName" -SameAsIncoming
$map3 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname" -IncomingClaimTypeDisplayName "SurName" -SameAsIncoming
$ap = New-SPTrustedIdentityTokenIssuer -Name "AzureAD" -Description "SharePoint secured by Azure AD" -realm $realm -ImportTrustCertificate $cert -ClaimsMappings $map,$map2,$map3 -SignInUrl $wsfedurl -IdentifierClaim “http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name”
```

A continuación, siga estos pasos para habilitar al proveedor de identidad de confianza para la aplicación:
1. En Administración Central, vaya a **Administrar las aplicaciones Web** y seleccione la aplicación web que desea asegurar con Azure AD. 
2. En la cinta de opciones, haga clic en **Proveedores de autenticación** y elija la zona que desea utilizar.
3. Seleccione el **proveedor de identidades de confianza** y el proveedor de identidad que acaba de registrar denominado *AzureAD*.  
4. En la configuración de dirección URL de la página de inicio de sesión, seleccione la **página de suscripción personalizados** y proporcionar el valor "/_trust/". 
5. Haga clic en **Aceptar**.

![Configurar el proveedor de autenticación](images/SAML11/fig10-configauthprovider.png)

## <a name="step-5-set-the-permissions"></a>Paso 5: Establecer los permisos

Los usuarios que van a iniciar sesión en Azure AD y tener acceso a SharePoint deben tener acceso a la aplicación. 

1. En el Portal de Azure, abra el directorio de AD de Azure. **Aplicaciones de la empresa**, haga clic en **todas las aplicaciones**. Haga clic en la aplicación que creó anteriormente (integración de SAML de SharePoint).
2. Haga clic en **usuarios y grupos**. 
3. Haga clic en **Agregar usuario** para agregar un usuario o grupo que tenga permisos para iniciar sesión en SharePoint con Azure AD.
4. Seleccione el usuario o grupo y haga clic en **asignar**.
 
El usuario tiene permiso de Azure AD, pero también debe tener permiso en SharePoint. Utilice los pasos siguientes para establecer los permisos para tener acceso a la aplicación web.

1. En Administración Central, haga clic en **Administración de aplicaciones**.
2. En la sección **Aplicaciones web** de la página **Administración de aplicaciones**, haga clic en **Administrar aplicaciones web**.
3. Haga clic en la aplicación web adecuada y, a continuación, haga clic en **Directiva de usuario**.
4. En directiva de aplicación Web, haga clic en **Agregar usuarios**.</br>![Buscar un usuario por su notificación de nombre](images/SAML11/fig11-searchbynameclaim.png)</br>
5. En el cuadro de diálogo **Agregar usuarios**, haga clic en la zona apropiada en la sección **Zonas** y, después, haga clic en **Siguiente**.
6. En el cuadro de diálogo **Directiva de aplicación Web** , en la sección **Elegir usuarios** , haga clic en el icono **Examinar** .
7. En el cuadro de texto **Buscar** , escriba el nombre de inicio de sesión para un usuario en el directorio y haga clic en **Buscar**. </br>Ejemplo: *demouser@blueskyabove.onmicrosoft.com*.
8. Bajo el título de AzureAD en la vista de lista, seleccione la propiedad name y haga clic en **Agregar** , a continuación, haga clic en **Aceptar** para cerrar el cuadro de diálogo.
9. En permisos, haga clic en **Control total**.</br>![Conceder control total a un usuario de reclamaciones](images/SAML11/fig12-grantfullcontrol.png)</br>
10. Haga clic en **Finalizar** y, después, en **Aceptar**.

## <a name="step-6-add-a-saml-11-token-issuance-policy-in-azure-ad"></a>Paso 6: Agregar una directiva de emisión de token SAML 1.1 en Azure AD

Cuando se crea la aplicación AD Azure en el portal, el valor predeterminado es mediante SAML 2.0. SharePoint Server 2016 requiere el formato de token SAML 1.1. La siguiente secuencia de comandos se quite la directiva predeterminada de SAML 2.0 y agregar una nueva directiva a tokens SAML 1.1 del problema.

```
Import-Module <file path of Initialize.ps1> 
$objectid = "<Application Object ID from Table 1>"
$saml2policyid = Get-PoliciesAssignedToServicePrincipal -servicePrincipalId $objectid | ?{$_.displayName -EQ "TokenIssuancePolicy"} | select objectId
Remove-PolicyFromServicePrincipal -policyId $saml2policyid -servicePrincipalId $objectid
$policy = Add-TokenIssuancePolicy -DisplayName SPSAML11 -SigningAlgorithm "http://www.w3.org/2001/04/xmldsig-more#rsa-sha256" -TokenResponseSigningPolicy TokenOnly -SamlTokenVersion "1.1"
Set-PolicyToServicePrincipal -policyId $policy.objectId -servicePrincipalId $objectid
```

## <a name="step-7-verify-the-new-provider"></a>Paso 7: Compruebe el nuevo proveedor

Abra un explorador a la dirección URL de la aplicación web que configuró en los pasos anteriores. Se le redirige para iniciar sesión en Azure AD.

![Iniciar sesión en Azure AD configurado para la federación](images/SAML11/fig13-examplesignin.png)

Le pregunta si desea permanecer conectado.

![¿Permanecer conectado?](images/SAML11/fig14-staysignedin.png)

Por último, puede tener acceso el sitio iniciado sesión como un usuario de su arrendatario Azure Active Directory.

![Usuario que ha iniciado sesión en SharePoint](images/SAML11/fig15-signedinsharepoint.png)


## <a name="additional-resources"></a>Recursos adicionales

[Introducción a WS-Federation](https://go.microsoft.com/fwlink/p/?linkid=188052)
  
[Adopción de la nube y soluciones híbridas](cloud-adoption-and-hybrid-solutions.md)
  
## <a name="join-the-discussion"></a>Participar en la discusión

|**Póngase en contacto con nosotros**|**Descripción**|
|:-----|:-----|
|**¿Qué soluciones necesita?** <br/> |Estamos creando contenido para la adopción en la nube que abarca varios servicios y plataformas en la nube de Microsoft. Díganos qué opina sobre nuestro contenido de adopción en la nube o solicite contenido específico enviando un correo electrónico a [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).  <br/> |
|**Participe en la discusión sobre soluciones** <br/> |Si es un apasionado de las soluciones basadas en la nube, puede unirse a Cloud Adoption Advisory Board (CAAB) para conectarse a una interesante comunidad de mayor tamaño formada por desarrolladores de contenido de Microsoft, profesionales del sector y clientes de todo el mundo. Para unirse, agregue a su usuario como miembro del [espacio CAAB (Cloud Adoption Advisory Board)](https://aka.ms/caab) de Microsoft Tech Community y envíenos un correo electrónico a [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Cualquiera puede leer contenido relacionado con la comunidad en el [blog de CAAB](https://blogs.technet.com/b/solutions_advisory_board/). Pero los miembros de CAAB reciben invitaciones a seminarios web privados donde se describen nuevos recursos y soluciones de adopción de la nube.  <br/> |
|**Obtenga los archivos de arte que ve aquí** <br/> |Si quiere recibir una copia editable de las ilustraciones que se muestran en este artículo, estaremos encantados de enviárselas. Envíe su solicitud por correo electrónico, incluida la dirección URL y el título de la ilustración, a [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).  <br/> |
   

