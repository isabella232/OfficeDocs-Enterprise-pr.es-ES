---
title: Protección de sitios de SharePoint Online en un entorno de prueba y desarrollo
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Priority
ms.custom: ''
ms.assetid: 06af70f3-e7dc-4ee2-a385-fb4d61a5e93b
description: 'Resumen: Cree sitios de grupo de SharePoint Online públicos, privados, confidenciales y altamente confidenciales en un entorno de desarrollo o prueba.'
ms.openlocfilehash: 8c02f1416cb00150e68dcc27dc7afb41bf82ed21
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2018
---
# <a name="secure-sharepoint-online-sites-in-a-devtest-environment"></a>Protección de sitios de SharePoint Online en un entorno de prueba y desarrollo

 **Resumen:** Crear sitios de grupo de SharePoint Online públicos, privados, confidenciales y altamente confidenciales en un entorno de desarrollo o prueba.
  
Este artículo proporciona instrucciones paso a paso para crear un entorno de desarrollo y prueba que incluye los cuatro tipos diferentes de sitios de grupo de SharePoint Online para la solución de [archivos y sitios de SharePoint Online seguro](secure-sharepoint-online-sites-and-files.md) .
  
![Los cuatro sitios de grupo del entorno de pruebas y desarrollo de SharePoint Online seguro.](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
Con este entorno de prueba y desarrollo podrá experimentar con los comportamientos de protección de la información y ajustar la configuración a sus necesidades concretas antes de implementar sitios de grupo de SharePoint Online en producción.
  
## <a name="phase-1-create-your-devtest-environment"></a>Fase 1: Crear el entorno de prueba y desarrollo

En esta fase se obtienen suscripciones de evaluación para Office 365 y Enterprise Mobility + Security para una organización ficticia.
  
Primero siga las instrucciones de la **fase 2** del [entorno de prueba y desarrollo de Office 365](office-365-dev-test-environment.md).
  
A continuación, registrarse para la suscripción de prueba de EMS y agregarlo a la misma organización que su suscripción de prueba de Office 365.
  
1. Si es necesario, inicie sesión el portal de Office 365 con las credenciales de la cuenta de administrador global de su suscripción de prueba. Para obtener ayuda, consulte [Where iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Haga clic en el icono **Administración**.
    
3. En la pestaña **Centro de administración de Office** del explorador, en el panel de navegación izquierdo, haga clic en **Facturación > Servicios de compra**.
    
4. En la página **Servicios de compra** , busque el elemento de **movilidad en la empresa + E5 de seguridad** . Sitúe el puntero del mouse sobre él y haga clic en **iniciar la versión de prueba gratuita**.
    
5. En la página **Confirmar pedido**, haga clic en **Probar ahora**.
    
6. En la página **Recibo del pedido**, haga clic en **Continuar**.
    
Después, habilite la licencia de Enterprise Mobility + Security E5 para la cuenta de administrador global.
  
1. En la pestaña **Centro de administración de Office 365** del explorador, en el panel de navegación izquierdo, haga clic en **Usuarios > Usuarios activos**.
    
2. Haga clic en la cuenta de administrador global y, a continuación, haga clic en **Editar** para **licencias de producto**.
    
3. En el panel de **licencias de producto** , activar la licencia del producto para **movilidad de la empresa + seguridad E5** **activado**, haga clic en **Guardar** y, a continuación, haga clic en **Cerrar** dos veces.
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups-and-users"></a>Fase 2: Crear y configurar los usuarios y grupos de Azure Active Directory (AD)

En esta fase se crean y configuran los grupos y usuarios de Azure AD para la organización ficticia.
  
En primer lugar, cree un conjunto de grupos para una organización típica en Azure Portal.
  
1. Crear una ficha independiente en el explorador y, a continuación, vaya al portal de Azure en [https://portal.azure.com](https://portal.azure.com). Si es necesario, inicie sesión con las credenciales de la cuenta de administrador global para la suscripción de prueba de Office 365 E5.
    
2. En Azure Portal, haga clic en **Azure Active Directory > Usuarios y grupos > Todos los grupos**.
    
3. En la hoja **Todos los grupos**, haga clic en **+ Nuevo grupo**.
    
4. En la hoja **Grupo**:
    
  - Escriba **C-Suite** en **Nombre**.
    
  - Seleccione **Asignada** en **Pertenencia**.
    
  - Para la opción **Habilitar las características de Office**, seleccione **Sí**.
    
5. Haga clic en **Crear** y, luego, cierre la hoja **Grupo**.
    
6. Repita los pasos del 3 al 5 para los siguientes nombres de grupo:
    
  - IT staff (Personal de TI)
    
  - Research staff (Personal de investigación)
    
  - Regular staff (Personal normal)
    
  - Marketing staff (Personal de marketing)
    
  - Sales staff (Personal de ventas)
    
7. Mantenga la pestaña de Azure Portal abierta en el explorador.
    
A continuación, configure la acción de licencias automático para que los miembros de los grupos se les asigna automáticamente licencias para las suscripciones de Office 365 y EMS.
  
1. En Azure Portal, haga clic en **Azure Active Directory > Licencias > Todos los productos**.
    
2. En la lista, seleccione **seguridad E5 + de movilidad en la empresa** y **Office 365 Enterprise E5**y, a continuación, haga clic en **asignar**.
    
3. En la hoja **Asignar licencia**, haga clic en **Usuarios y grupos**.
    
4. En la lista de grupos, seleccione lo siguiente:
    
  - C-Suite (Directivos)
    
  - IT staff (Personal de TI)
    
  - Research staff (Personal de investigación)
    
  - Regular staff (Personal normal)
    
  - Marketing staff (Personal de marketing)
    
  - Sales staff (Personal de ventas)
    
5. Haga clic en **Seleccionar**y, a continuación, haga clic en **asignar**.
    
6. Cierre la pestaña Azure Portal del explorador.
    
Después, debe [conectarse al módulo PowerShell de Azure Active Directory V2](https://go.microsoft.com/fwlink/?linkid=842218).
  
Rellene el nombre de la organización, su ubicación y una contraseña común y, a continuación, ejecute estos comandos desde el símbolo del sistema de PowerShell o el entorno de secuencia de comandos integrado (ISE) para crear cuentas de usuario y agregarlos a sus grupos de:
  
```
$orgName="<organization name, such as contoso for the contoso.onmicrosoft.com trial subscription domain name>"
$location="<the ISO ALPHA2 country code, such as US for the United States>"
$commonPassword="<common password for all the new accounts>"

$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPassword

$groupName="C-Suite"
$userNames=@("CEO","CFO","CIO") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="IT staff"
$userNames=@("ITAdmin1","ITAdmin2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Research staff"
$userNames=@("Researcher1") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Regular staff"
$userNames=@("Regular1", "Regular2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Marketing staff"
$userNames=@("Marketing1", "Marketing2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Sales staff"
$userNames=@("SalesPerson1") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
```

> [!NOTE]
> Se usa una contraseña común para automatizar y facilitar la configuración de un entorno de prueba y desarrollo. No se recomienda para suscripciones de producción. 
  
Siga estos pasos para comprobar que basadas en grupos de licencias está funcionando correctamente.
  
1. En la pestaña de **inicio de Microsoft Office** del explorador, haga clic en el icono **Administración**.
    
2. En la nueva pestaña **Centro de administración de Office** del explorador, haga clic en **Usuarios**.
    
3. En la lista de usuarios, haga clic en **CEO** (Consejero delegado).
    
4. En el panel que muestra las propiedades de la cuenta de usuario **CEO**, compruebe que se le han asignado las licencias **Enterprise Mobility + Security E5** y **Office 365 Enterprise E5** (en **Licencias de productos**).
    
## <a name="phase-3-create-office-365-labels"></a>Fase 3: Crear etiquetas de Office 365

En esta fase se crean las etiquetas para los diferentes niveles de seguridad de las carpetas de documentos de sitios de grupo de SharePoint Online.
  
1. Si es necesario, use una instancia privada de su explorador de Internet e inicie sesión el portal de Office 365 con la cuenta de administrador global de su suscripción de prueba de Office 365 E5. Para obtener ayuda, consulte [Where iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. En la pestaña de **inicio de Microsoft Office**, haga clic en el icono **Administración**.
    
3. En la ficha del **Centro de administración de Office de** nuevo del explorador, haga clic en **centros de administración > seguridad &amp; cumplimiento**.
    
4. Desde la nueva **principal - seguridad &amp; cumplimiento** ficha del explorador, haga clic en **clasificaciones > etiquetas**.
    
5. En el panel **Inicio > Etiquetas**, haga clic en **Crear una etiqueta**.
    
6. En el panel de **la etiqueta de nombre** , escriba **Público interno**y, a continuación, haga clic en **siguiente**.
    
7. En el panel **Configuración de etiquetas**, haga clic en **Siguiente**.
    
8. En el panel de **revisión de la configuración** , haga clic en **crear esta etiqueta**y, a continuación, haga clic en **Cerrar**.
    
9. Repita los pasos del 5 al 8 para estas etiquetas adicionales:
    
  - Private
    
  - Confidencial
    
  - Extremadamente confidencial
    
10. En el panel **Inicio > Etiquetas**, haga clic para **Publish labels** (Publicar etiquetas).
    
11. En el panel **Choose labels to publish** (Elegir las etiquetas que se van a publicar), haga clic en **Choose labels to publish**.
    
12. En el panel de **elección de etiquetas**, haga clic en **Agregar** y seleccione las cuatro etiquetas.
    
13. Haga clic en **Listo**.
    
14. En el panel **Choose labels to publish** (Elegir las etiquetas que se van a publicar), haga clic en **Siguiente**.
    
15. En el panel **Elegir ubicaciones**, haga clic en **Siguiente**.
    
16. En el panel de **nombre de la directiva** , escriba **organización de ejemplo** en **nombre**y, a continuación, haga clic en **siguiente**.
    
17. En el panel de **revisión de la configuración** , haga clic en **etiquetas de publicar**y, a continuación, haga clic en **Cerrar**.
    
## <a name="phase-4-create-your-sharepoint-online-team-sites"></a>Fase 4: Crear los sitios de grupo de SharePoint Online

En esta fase se crean y configuran los cuatro tipos de sitios de grupo de SharePoint Online de la organización de ejemplo.
  
### <a name="organization-wide-team-site"></a>Sitio de grupo De organización

Para crear un sitio de grupo público de base de referencia de SharePoint Online, haga lo siguiente:
  
1. Si es necesario, use un explorador en el equipo local e inicie sesión en el portal de Office 365 con la cuenta de administrador global. Para obtener ayuda, vea [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4) (Dónde iniciar sesión en Office 365).
    
2. En la lista de iconos, haga clic en **SharePoint**.
    
3. En la nueva pestaña **SharePoint** del explorador, haga clic en **+ Crear sitio**.
    
4. En la página **Crear un sitio**, haga clic en **Sitio de grupo**.
    
5. En **Nombre del sitio**, escriba **En toda la organización**. 
    
6. En **Team site description** (Descripción de sitio de grupo), escriba **Sitio de SharePoint para toda la organización**.
    
7. En **la configuración de privacidad**, seleccione **pública - cualquier persona de la organización puede tener acceso a este sitio**y, a continuación, haga clic en **siguiente**.
    
8. En el panel **Who do you want to add?** (Usuarios que quiere agregar), haga clic en **Finalizar**.
    
Después configure la carpeta de documentos del sitio de grupo En toda la organización para la etiqueta Interno público.
  
1. En la ficha **Home de toda la organización** del explorador, haga clic en **documentos**.
    
2. Haga clic en el icono de configuración y luego en **Configuración de biblioteca**.
    
3. En **Permisos y administración**, haga clic en **Apply label to items in this library** (Aplicar la etiqueta a los elementos de esta biblioteca).
    
4. En **Aplicar a la configuración de etiqueta**, seleccione **Interna pública**y, a continuación, haga clic en **Guardar**.
    
Esta es la configuración resultante.
  
![Protección de nivel de línea base del sitio de grupo de SharePoint Online público de toda la organización.](images/25c86847-a38d-49ad-bb5f-c7c04206b6dc.png)
  
### <a name="project-1-team-site"></a>Sitio de grupo Proyecto 1

Para crear un sitio de grupo privado de base de referencia de SharePoint Online para un proyecto dentro de la organización, haga lo siguiente:
  
1. Si es necesario, use un explorador en el equipo local e inicie sesión en el portal de Office 365 con la cuenta de administrador global. Para obtener ayuda, vea [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4) (Dónde iniciar sesión en Office 365).
    
2. En la lista de iconos, haga clic en **SharePoint**.
    
3. En la nueva pestaña **SharePoint** del explorador, haga clic en **+ Crear sitio**.
    
4. En la página **Crear un sitio**, haga clic en **Sitio de grupo**.
    
5. En **Nombre del sitio**, escriba **Proyecto 1**. 
    
6. En **Descripción del sitio del equipo,** escriba el **sitio de SharePoint para el proyecto 1**.
    
7. En **la configuración de privacidad**, seleccione **privada - sólo los miembros pueden tener acceso a este sitio**y, a continuación, haga clic en **siguiente**.
    
8. En el panel **Who do you want to add?** (Usuarios que quiere agregar), haga clic en **Finalizar**.
    
Después, configure la carpeta de documentos del sitio de grupo Proyecto 1 para la etiqueta Privado.
  
1. En la pestaña **Proyecto 1-Inicio** del explorador, haga clic en **Documentos**.
    
2. Haga clic en el icono de configuración y luego en **Configuración de biblioteca**.
    
3. En **Permisos y administración**, haga clic en **Apply label to items in this library** (Aplicar la etiqueta a los elementos de esta biblioteca).
    
4. En la **Configuración se aplica la etiqueta**, seleccione **privada**y, a continuación, haga clic en **Guardar**.
    
Esta es la configuración resultante.
  
![Protección de nivel de línea base del sitio de grupo de SharePoint Online privado Project1.](images/ecd96376-b5dc-4042-9cbd-b3765507ace7.png)
  
### <a name="marketing-campaigns-team-site"></a>Sitio de grupo Campañas de marketing

Para crear un sitio de grupo aislado de SharePoint Online que tenga el nivel confidencial para recursos de campañas de marketing, haga lo siguiente:
  
1. Uso de un explorador en su equipo local, inicie sesión en el portal de Office 365 con su cuenta de administrador global. Para obtener ayuda, consulte [Where iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. En la lista de iconos, haga clic en **SharePoint**.
    
3. En la nueva pestaña **SharePoint** del explorador, haga clic en **+ Crear sitio**.
    
4. En la página **Crear un sitio**, haga clic en **Sitio de grupo**.
    
5. En **Team site name** (Nombre del sitio de grupo), escriba **Campañas de marketing**.
    
6. En **Team site description** (Descripción del sitio de grupo), escriba **Sitio de SharePoint para recursos de campaña de marketing (confidencial)**.
    
7.  En **la configuración de privacidad**, seleccione **privada - sólo los miembros pueden tener acceso a este sitio**y, a continuación, haga clic en **siguiente**.
    
8. En el panel **Who do you want to add?** (Usuarios que quiere agregar), haga clic en **Finalizar**.
    
9. En la ficha nuevo de **campañas de Marketing** en el explorador, en la barra de herramientas, haga clic en el icono de configuración y, a continuación, haga clic en **permisos del sitio**.
    
10. En el panel **Permisos del sitio**, haga clic en **Advanced permissions settings** (Configuración de permisos avanzada).
    
11. En la nueva pestaña **Permisos** del explorador, haga clic en **Configuración de solicitud de acceso**.
    
12. En el cuadro de diálogo **Configuración de solicitud de acceso** , desactive las casillas de verificación **Permitir miembros para compartir el sitio y archivos y carpetas individuales** y **Permitir miembros para invitar a otras personas al grupo de miembros del sitio** , escriba **ITAdmin1 @**\<su nombre de la organización >**. onmicrosoft.com** en **Enviar todas las solicitudes de acceso**y, a continuación, haga clic en **Aceptar**.
    
13. Haga clic en **Campañas de Marketing-Miembros** en la lista.
    
14. En la página **Personas y grupos**, haga clic en **Nuevo**.
    
15. En el cuadro de diálogo **Compartir** , escriba **personal de Marketing**, selecciónelo y, a continuación, haga clic en **Compartir**.
    
16. Repita los pasos 14 y 15 para la cuenta de usuario **Researcher1** .
    
17. Haga clic en el botón Atrás del explorador.
    
18. En la lista, haga clic en **campañas de Marketing propietarios** .
    
19. En la página **Personas y grupos**, haga clic en **Nuevo**.
    
20. En el cuadro de diálogo **Compartir** , escriba **el personal de TI**, selecciónelo y, a continuación, haga clic en **Compartir**.
    
21. Haga clic en el botón Atrás del explorador.
    
22. Cierre la ficha **personas y grupos** en el explorador, haga clic en la ficha **principal de campañas de Marketing** en el explorador y, a continuación, cierre el panel de **los permisos del sitio** .
    
Estos son los resultados de la configuración de los permisos:
  
- El grupo de SharePoint de **Integrantes de campañas de Marketing** contiene sólo el grupo de **campañas de Marketing** (que contiene la cuenta de usuario de administrador global), el grupo de **personal de Marketing** (que contiene el usuario Marketing1 y Marketing2 las cuentas) y la cuenta de usuario **Researcher1** .
    
- El grupo de SharePoint **Propietarios de las campañas de Marketing** contiene sólo el grupo de **personal de TI** (que contiene sólo las cuentas de usuario ITAdmin1 y ITAdmin2).
    
- El grupo de SharePoint **Campañas de marketing-Visitantes** no contiene grupos ni cuentas de usuario.
    
- Los miembros no pueden modificar los permisos de nivel de sitio (esto solo pueden hacerlo los miembros del grupo **Campañas de marketing-Propietarios**).
    
- Otras cuentas de usuario no pueden obtener acceso a sus recursos o el sitio, pero pueden solicitar acceso al sitio, que enviará un correo electrónico al buzón de la cuenta de usuario de ITAdmin1.
    
Después, configure la carpeta de documentos del sitio de grupo Campañas de marketing para la etiqueta Confidencial.
  
1. En la pestaña **Campañas de marketing-Inicio** del explorador, haga clic en **Documentos**.
    
2. Haga clic en el icono de configuración y luego en **Configuración de biblioteca**.
    
3. En **Permisos y administración**, haga clic en **Apply label to items in this library** (Aplicar la etiqueta a los elementos de esta biblioteca).
    
4. En la **Configuración se aplica la etiqueta**, seleccione **confidencial**y, a continuación, haga clic en **Guardar**.
    
Luego configure una directiva de prevención de pérdida de datos (DLP) que notifique a los usuarios cada vez que compartan un documento en un sitio de grupo de SharePoint Online con la etiqueta Confidencial, que incluye el sitio Campañas de marketing, fuera de la organización.
  
1. En la ficha **Página principal de Microsoft Office** en el explorador, haga clic en el **seguridad &amp; cumplimiento** colocar en mosaico.
    
2. En el nuevo **seguridad &amp; cumplimiento** , haga clic en el explorador **prevención de pérdida de datos > directiva**.
    
3. En el panel **Prevención de pérdida de datos**, haga clic en **+ Crear una directiva**.
    
4. En la **empezar con una plantilla o crear una directiva personalizada** panel, haga clic en **personalizado**y, a continuación, haga clic en **siguiente**.
    
5. En el panel de **nombre de la directiva** , escriba **sitios de grupo de SharePoint Online de etiqueta confidencial** en **nombre**y, a continuación, haga clic en **siguiente**.
    
6. En el panel **Elegir ubicaciones**, haga clic para que se le **permita elegir ubicaciones concretas** y luego haga clic en **Siguiente**.
    
7. En la lista de ubicaciones, deshabilitar las ubicaciones de **correo electrónico de Exchange** y **las cuentas de OneDrive** y, a continuación, haga clic en **siguiente**.
    
8. En el panel **Customize the types of sensitive info you want to protect** (Personalizar los tipos de información confidencial que quiere proteger), haga clic en **Editar**.
    
9. En el panel **Elegir los tipos de contenido para proteger** , haga clic en **Agregar** en el cuadro de lista desplegable y, a continuación, haga clic en **etiquetas**.
    
10. En el panel de **etiquetas** , haga clic en **+ Agregar**, seleccione la etiqueta **confidencial** , haga clic en **Agregar**y, a continuación, haga clic en **Listo**.
    
11. En el panel **Choose the types of content to protect** (Elegir los tipos de contenido que se va a proteger), haga clic en **Guardar**.
    
12. En el panel **Customize the types of sensitive info you want to protect** (Personalizar los tipos de información confidencial que quiere proteger), haga clic en **Siguiente**.
    
13. En el panel **What do you want to do if we detect sensitive info?** (¿Qué quiere hacer si se detecta información confidencial?), haga clic en **Customize the tip and email** (Personalizar la sugerencia y el correo electrónico).
    
14. En el panel **Customize policy tips and email notifications** (Personalizar sugerencias de directiva y notificaciones de correo electrónico), haga clic en **Customize the policy tip text** (Personalizar el texto de la sugerencia de directiva).
    
15. En el cuadro de texto, escriba o pegue lo siguiente:
    
  - Para compartir con un usuario de fuera de la organización, descargue el archivo y luego ábralo. Haga clic en Archivo, Proteger documento y Cifrar con contraseña y, luego, especifique una contraseña segura. Envíe la contraseña en un correo electrónico diferente u otro medio de comunicación.
    
16. Haga clic en **Aceptar**.
    
17. En la **¿Qué desea hacer si se detecta información confidencial?** panel, desactive la casilla de verificación **Bloquear personas de uso compartido y restringir el acceso al contenido compartido** y, a continuación, haga clic en **siguiente**.
    
18. En el **¿desea activar las acciones de directiva o de prueba primero?** panel, haga clic en **Sí, activarlo inmediatamente**y, a continuación, haga clic en **siguiente**.
    
19. En el panel de **revisión de la configuración** , haga clic en **crear**y, a continuación, haga clic en **Cerrar**.
    
Esta es la configuración resultante.
  
![Protección de nivel confidencial del sitio de grupo de SharePoint Online aislado de campañas de marketing.](images/33992bd5-96ee-4bfb-9ecf-c8a6736dd100.png)
  
### <a name="company-strategy-team-site"></a>Sitio de grupo Estrategia de empresa

Para crear un sitio de grupo aislado de SharePoint Online que tenga el nivel extremadamente confidencial para recursos estratégicos de empresa dirigido a los directores ejecutivos de la organización, haga lo siguiente:
  
1. Si es necesario, use un explorador en el equipo local e inicie sesión en el portal de Office 365 con la cuenta de administrador global. Para obtener ayuda, vea [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4) (Dónde iniciar sesión en Office 365).
    
2. En la lista de iconos, haga clic en **SharePoint**.
    
3. En la nueva pestaña **SharePoint** del explorador, haga clic en **+ Crear sitio**.
    
4. En la página **Crear un sitio**, haga clic en **Sitio de grupo**.
    
5. En **Team site name** (Nombre de sitio de grupo), escriba **Estrategia de empresa**.
    
6. En **Team site description** (Descripción de sitio de grupo), escriba **Sitio de SharePoint para la estrategia de empresa (extremadamente confidencial)**.
    
7.  En **la configuración de privacidad**, seleccione **privada - sólo los miembros pueden tener acceso a este sitio**y, a continuación, haga clic en **siguiente**.
    
8. En el panel **Who do you want to add?** (Usuarios que quiere agregar), haga clic en **Finalizar**.
    
9. En la ficha nuevo de la **estrategia de la empresa** en el explorador, en la barra de herramientas, haga clic en el icono de configuración y, a continuación, haga clic en **permisos del sitio**.
    
10. En el panel **Permisos del sitio**, haga clic en **Advanced permissions settings** (Configuración de permisos avanzada).
    
11. En la nueva pestaña **Permisos** del explorador, haga clic en **Configuración de solicitud de acceso**.
    
12. En el cuadro de diálogo **Configuración de acceso de la petición** , desactive **Permitir miembros para compartir el sitio y archivos y carpetas individuales** y **Permitir miembros para invitar a otras personas al grupo de miembros del sitio** (de manera que se desactivan todas las casillas de verificación tres) y, a continuación, haga clic en ** Aceptar**.
    
13. Haga clic en **la estrategia de la empresa (miembros de)** en la lista.
    
14. En la página **Personas y grupos**, haga clic en **Nuevo**.
    
15. En el cuadro de diálogo **Compartir** , escriba **C-Suite**, selecciónelo y, a continuación, haga clic en **Compartir**.
    
16. En la lista, haga clic en **estrategia los propietarios de la empresa** .
    
17. En la página **Personas y grupos**, haga clic en **Nuevo**.
    
18. En el cuadro de diálogo **Compartir** , escriba **el personal de TI**, selecciónelo y, a continuación, haga clic en **Compartir**.
    
19. Haga clic en el botón Atrás del explorador.
    
20. Cierre la ficha **personas y grupos** en el explorador, haga clic en la ficha **Página principal de estrategia de la empresa** en el explorador y, a continuación, cierre el panel de **los permisos del sitio** .
    
Estos son los resultados de la configuración de los permisos:
  
- El grupo de SharePoint de la **Estrategia de la empresa: los miembros** contiene sólo el grupo de **Conjunto de aplicaciones de C** (que contiene sólo las cuentas de usuario consejero Delegado, director financiero y director) y el grupo de **estrategia de la empresa** (que contiene sólo la cuenta de usuario de administrador global).
    
- El grupo de SharePoint **Propietarios de estrategia de compañía** contiene sólo el grupo de **personal de TI** (que contiene sólo las cuentas de usuario ITAdmin1 y ITAdmin2).
    
- El grupo de SharePoint **Estrategia de empresa-Visitantes** no contiene grupos ni cuentas de usuario.
    
- Los miembros no pueden modificar los permisos de nivel de sitio (esto solo pueden hacerlo los miembros del grupo **Estrategia de empresa-Propietarios**).
    
- Otras cuentas de usuario no pueden acceder al sitio o a sus recursos ni pedir acceso al sitio. Los permisos adicionales para el sitio deben ser asignados por el administrador global o por un miembro del grupo **Estrategia de empresa-Propietarios**.
    
Después, configure la carpeta de documentos del sitio de grupo Estrategia de empresa para la etiqueta Extremadamente confidencial.
  
1. En la pestaña **Estrategia de empresa-Inicio** del explorador, haga clic en **Documentos**.
    
2. Haga clic en el icono de configuración y luego en **Configuración de biblioteca**.
    
3. En **Permisos y administración**, haga clic en **Apply label to items in this library** (Aplicar la etiqueta a los elementos de esta biblioteca).
    
4. En la **Configuración se aplica la etiqueta**, seleccione **Altamente confidencial**y, a continuación, haga clic en **Guardar**.
    
Después, configure una directiva de DLP que impida a los usuarios compartir un documento en un sitio de grupo de SharePoint Online con la etiqueta Extremadamente confidencial, que incluye el sitio Estrategia de empresa, fuera de la organización.
  
1. Si es necesario, use un explorador en su equipo local e inicie sesión el portal de Office 365 con una cuenta que tenga el rol de administrador de seguridad o administrador de la compañía. Para obtener ayuda, consulte [Where iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. En la ficha **Página principal de Microsoft Office** en el explorador, haga clic en el **seguridad &amp; cumplimiento** colocar en mosaico.
    
3. En el nuevo **seguridad &amp; cumplimiento** , haga clic en el explorador **prevención de pérdida de datos > directiva**.
    
4. En el panel **Prevención de pérdida de datos**, haga clic en **+ Crear una directiva**.
    
5. En la **empezar con una plantilla o crear una directiva personalizada** panel, haga clic en **personalizado**y, a continuación, haga clic en **siguiente**.
    
6. En el panel de **nombre de la directiva** , escriba **altamente confidencial sitios de grupo de SharePoint Online etiqueta** en **nombre**y, a continuación, haga clic en **siguiente**.
    
7. En el panel **Elegir ubicaciones**, haga clic para que se le **permita elegir ubicaciones concretas** y luego haga clic en **Siguiente**.
    
8. En la lista de ubicaciones, deshabilitar las ubicaciones de **correo electrónico de Exchange** y **las cuentas de OneDrive** y, a continuación, haga clic en **siguiente**.
    
9. En el panel **Customize the types of sensitive info you want to protect** (Personalizar los tipos de información confidencial que quiere proteger), haga clic en **Editar**.
    
10. En el panel **Elegir los tipos de contenido para proteger** , haga clic en **Agregar** en el cuadro de lista desplegable y, a continuación, haga clic en **etiquetas**.
    
11. En el panel de **etiquetas** , haga clic en **+ Agregar**, seleccione la etiqueta **Altamente confidencial** , haga clic en **Agregar**y, a continuación, haga clic en **Listo**.
    
12. En el panel **Choose the types of content to protect** (Elegir los tipos de contenido que se va a proteger), haga clic en **Guardar**.
    
13. En el panel **Customize the types of sensitive info you want to protect** (Personalizar los tipos de información confidencial que quiere proteger), haga clic en **Siguiente**.
    
14. En el panel **What do you want to do if we detect sensitive info?** (¿Qué quiere hacer si se detecta información confidencial?), haga clic en **Customize the tip and email** (Personalizar la sugerencia y el correo electrónico).
    
15. En el panel **Customize policy tips and email notifications** (Personalizar sugerencias de directiva y notificaciones de correo electrónico), haga clic en **Customize the policy tip text** (Personalizar el texto de la sugerencia de directiva).
    
16. En el cuadro de texto, escriba o pegue lo siguiente:
    
  - Para compartir con un usuario de fuera de la organización, descargue el archivo y luego ábralo. Haga clic en Archivo, Proteger documento y Cifrar con contraseña y, luego, especifique una contraseña segura. Envíe la contraseña en un correo electrónico diferente u otro medio de comunicación.
    
17. Haga clic en **Aceptar**.
    
18. En la **¿Qué desea hacer si se detecta información confidencial?** panel, seleccione **requerir una justificación comercial para reemplazar**y, a continuación, haga clic en **siguiente**.
    
19. En el **¿desea activar las acciones de directiva o de prueba primero?** panel, haga clic en **Sí, activarlo inmediatamente**y, a continuación, haga clic en **siguiente**.
    
20. En el panel de **revisión de la configuración** , haga clic en **crear**y, a continuación, haga clic en **Cerrar**.
    
Luego siga las instrucciones de [Activación de Azure Rights Management desde el Centro de administración de Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).
  
A continuación, siga estos pasos para configurar Azure Information Protection con una nueva directiva de ámbito y la etiqueta secundaria para la protección y permisos:
  
1. Inicie sesión el portal de Office 365 con una cuenta que tenga el rol de administrador de seguridad o administrador de la compañía. Para obtener ayuda, consulte [Where iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. En una ficha independiente del explorador, vaya al portal de Azure ([https://portal.azure.com](https://portal.azure.com)).
    
3. Si se trata de la primera vez que se va a configurar la protección de la información de Azure, vea estas [instrucciones](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).
    
4. En el panel de lista, haga clic en **más servicios**, escriba la **información**y, a continuación, haga clic en **Protección de la información de Azure**.
    
5. En el servidor blade de **protección de la información de Azure** , haga clic en **con ámbito de directivas > + Agregar una nueva directiva de**.
    
6. Escriba **EstrategiaEmpresa** en **Nombre de la directiva** y **Etiqueta para los documentos del sitio de grupo Estrategia de empresa** en **Descripción**.
    
7. Haga clic en **Seleccionar a qué usuarios o grupos se aplica esta directiva > Usuarios o grupos** y seleccione **C-Suite**.
    
8. Haga clic en **Seleccionar > Aceptar**.
    
9. Para la etiqueta **Extremadamente confidencial**, haga clic en el botón de puntos suspensivos (...) y, luego, en **Agregar una subetiqueta**.
    
10. Escriba un nombre para la subetiqueta en **Nombre** y una descripción en **Descripción**.
    
11. En **Establecer permisos para documentos y correos electrónicos que contengan esta etiqueta**, haga clic en **Proteger**.
    
12. En la sección **Protección**, haga clic en **Azure (clave de nube)**.
    
13. En la hoja **Protección**, en **Configuración de protección**, haga clic en **+ Agregar permisos**.
    
14. En la hoja **Agregar permisos**, en **Especificar usuarios y grupos**, haga clic en **+ Examinar directorio**.
    
15. En el panel de **AAD usuarios y grupos** , seleccione el **Conjunto de aplicaciones de C**y, a continuación, haga clic en **Seleccionar**.
    
16. En **elija permisos del ajuste preestablecido**, desactive las casillas de verificación **Imprimir**, **Copiar y extraer contenido**y **hacia delante** .
    
17. Haga clic en **Aceptar** dos veces.
    
18. En la hoja **Subetiqueta**, haga clic en **Guardar**.
    
19. Cierre la hoja de directiva en la que acaba de agregar el ámbito.
    
20. En el servidor blade de **protección de la información de Azure - las directivas de ámbito** , haga clic en **Publicar**y, a continuación, haga clic en **Sí**.
    
Para proteger un documento con la protección de la información de Azure y esta nueva etiqueta, debe [instalar al cliente de protección de la información de Azure](https://docs.microsoft.com/information-protection/rms-client/install-client-app) en un equipo de prueba, instalar Office desde el portal de Office 365 y, a continuación, iniciar sesión en desde Microsoft Word con una cuenta en el ** Conjunto de aplicaciones de C** grupo de su suscripción de prueba.
  
Esta es la configuración resultante.
  
![Protección de nivel alto de confidencialidad de un sitio de grupo de SharePoint Online aislado de estrategia de empresa.](images/c22695f9-50a1-4abf-a0dd-344b0c92cf94.png)
  
Ahora está listo para crear documentos en estos cuatro sitios y probar el acceso a ellos con diferentes cuentas de usuario de la suscripción de evaluación.
  
Esta es la configuración global de los cuatro sitios de grupo de SharePoint Online.
  
![Los cuatro sitios de grupo del entorno de pruebas y desarrollo de SharePoint Online seguro.](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
## <a name="next-step"></a>Paso siguiente

Cuando esté listo para la implementación en producción de sitios seguros de SharePoint Online, vea [Protección de archivos y sitios de SharePoint Online](secure-sharepoint-online-sites-and-files.md) para obtener información detallada y vínculos a artículos de implementación paso a paso.
  
## <a name="see-also"></a>Consulte también

[Protección de archivos y sitios de SharePoint Online](secure-sharepoint-online-sites-and-files.md)
  
[Soluciones de seguridad](security-solutions.md)
  
[Adopción de la nube y soluciones híbridas](cloud-adoption-and-hybrid-solutions.md)
  
[Instrucciones de seguridad de Microsoft para campañas políticas, organizaciones sin ánimo de lucro y otras organizaciones ágiles](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)




