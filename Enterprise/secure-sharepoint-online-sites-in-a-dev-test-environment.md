---
title: Sitios de SharePoint Online seguros en un entorno de pruebas y desarrollo
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
ms.assetid: 06af70f3-e7dc-4ee2-a385-fb4d61a5e93b
description: "Resumen: Crear sitios de equipo de SharePoint Online públicos, privados, confidenciales y altamente confidenciales en un entorno de pruebas y desarrollo."
ms.openlocfilehash: 17abee7a293996194a097693607b4b4d9c117046
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2017
---
# <a name="secure-sharepoint-online-sites-in-a-devtest-environment"></a>Sitios de SharePoint Online seguros en un entorno de pruebas y desarrollo

 **Resumen:** Crear sitios de equipo de SharePoint Online públicos, privados, confidenciales y altamente confidenciales en un entorno de pruebas y desarrollo.
  
Este artículo proporciona instrucciones paso a paso para crear un entorno de pruebas y desarrollo que incluye los cuatro tipos diferentes de sitios SharePoint Online de equipo para la solución de [archivos y los sitios de SharePoint Online seguro](secure-sharepoint-online-sites-and-files.md) .
  
![Los cuatro sitios de grupo del entorno de pruebas y desarrollo de SharePoint Online seguro.](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
Utilizar este entorno de desarrollo y prueba para experimentar con los comportamientos de protección de la información y ajustar la configuración para sus necesidades específicas antes de implementar SharePoint Online sitios de equipo de producción.
  
## <a name="phase-1-create-your-devtest-environment"></a>Fase 1: Crear el entorno de pruebas y desarrollo

En esta fase, se puede obtener las suscripciones de prueba de Office 365 + seguridad y movilidad en la empresa de una organización ficticia.
  
En primer lugar, siga las instrucciones en la **fase 2** del [entorno de desarrollo y prueba de Office 365](office-365-dev-test-environment.md).
  
A continuación, registrarse para la suscripción de prueba de EMS y agregarlo a la misma organización que su suscripción de prueba de Office 365.
  
1. Si es necesario, iniciar sesión en el portal de Office 365 con las credenciales de la cuenta de administrador global de su suscripción de prueba. Para obtener ayuda, visite [dónde puede iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Haga clic en el mosaico de **Admin** .
    
3. En la ficha del **Centro de administración de Office** en el explorador, en la exploración de la izquierda, haga clic en **de facturación > adquirir servicios**.
    
4. En la página **Servicios de compra** , busque el elemento de **seguridad E5 + de movilidad en la empresa** . Sitúe el puntero del mouse sobre él y haga clic en **iniciar la versión de prueba gratuita**.
    
5. En la página **confirmar su pedido** , haga clic en **Probar ahora**.
    
6. En la página de **confirmación del pedido** , haga clic en **continuar**.
    
A continuación, habilitar la movilidad en la empresa + licencia E5 de seguridad para la cuenta de administrador global.
  
1. En la ficha del **Centro de administración de Office 365** en el explorador, en la exploración de la izquierda, haga clic en **los usuarios > usuarios activos**.
    
2. Haga clic en la cuenta de administrador global y, a continuación, haga clic en **Editar** para **licencias de producto**.
    
3. En el panel de **licencias de producto** , activar la licencia del producto de **movilidad en la empresa + seguridad E5** en **On**, haga clic en **Guardar** y, a continuación, haga clic en **Cerrar** dos veces.
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups-and-users"></a>Fase 2: Crear y configurar los usuarios y grupos de Azure de Active Directory (AD)

En esta fase, crear y configurar los usuarios y grupos de AD Azure para su organización ficticia.
  
Primero, cree un conjunto de grupos de una organización típica con el portal de Azure.
  
1. Crear una ficha independiente en el explorador y, a continuación, vaya al portal de Azure en [https://portal.azure.com](https://portal.azure.com). Si es necesario, inicie sesión con las credenciales de la cuenta de administrador global para la suscripción de prueba de Office 365 E5.
    
2. En el portal de Azure, haga clic en **Azure Active Directory > usuarios y grupos > grupos de todos los**.
    
3. En la hoja de **todos los grupos** , haga clic en **+ nuevo grupo**.
    
4. En la hoja de **grupo** :
    
  - Tipo **C-Suite** en **nombre**.
    
  - Seleccione **asignados** en la **suscripción**.
    
  - Haga clic en **Sí** para **Habilitar Office características**.
    
5. Haga clic en **crear**y, a continuación, cierre la hoja de **grupo** .
    
6. Repita los pasos 3 a 5 para los nombres de grupo siguientes:
    
  - Personal de TI
    
  - Personal de investigación
    
  - Personal estatutario
    
  - Personal de marketing
    
  - Personal de ventas
    
7. Mantener la ficha portal Azure en su explorador se abre.
    
A continuación, configure el licenciamiento automático para que los miembros de los grupos se asignan automáticamente licencias para sus suscripciones a Office 365 y EMS.
  
1. En el portal de Azure, haga clic en **Azure Active Directory > licencias > todos los productos**.
    
2. En la lista, seleccione **seguridad E5 + de movilidad en la empresa** y **Office 365 Enterprise E5**y, a continuación, haga clic en **asignar**.
    
3. En la hoja **asignar licencias** , haga clic en **usuarios y grupos**.
    
4. En la lista de grupos, seleccione lo siguiente:
    
  - C-Suite
    
  - Personal de TI
    
  - Personal de investigación
    
  - Personal estatutario
    
  - Personal de marketing
    
  - Personal de ventas
    
5. Haga clic en **Seleccionar**y, a continuación, haga clic en **asignar**.
    
6. Cierre la ficha portal Azure en el explorador.
    
A continuación, puede [Conectar con el módulo de Active Directory V2 PowerShell de Azure](https://go.microsoft.com/fwlink/?linkid=842218).
  
Rellene el nombre de su organización, su ubicación y una contraseña común y, a continuación, ejecutar estos comandos desde el símbolo del sistema de PowerShell o el entorno de secuencias de comandos integrado (ISE) para crear cuentas de usuario y agregarlos a sus grupos:
  
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
> El uso de una contraseña común aquí es para la automatización y la facilidad de configuración para un entorno de pruebas y desarrollo. Esto no es recomendable para las suscripciones de producción. 
  
Siga estos pasos para comprobar que están basado en el grupo de licencias funciona correctamente.
  
1. Desde la ficha **Página de inicio de Microsoft Office** del explorador, haga clic en el mosaico de **Admin** .
    
2. Desde la ficha del **Centro de administración de Office** nueva del explorador, haga clic en **usuarios**.
    
3. En la lista de usuarios, haga clic en **Director ejecutivo**.
    
4. En el panel que muestra las propiedades de la cuenta de usuario del **Director general** , compruebe que se ha asignado las licencias de **movilidad en la empresa + seguridad E5** y **E5 Enterprise de Office 365** (en **licencias de producto**).
    
## <a name="phase-3-create-office-365-labels"></a>Fase 3: Crear etiquetas de Office 365

En esta fase, crear las etiquetas para los diferentes niveles de seguridad para SharePoint Online carpetas de documentos del sitio de equipo.
  
1. Si es necesario, utilice una instancia privada de su explorador de Internet e iniciar sesión en el portal de Office 365 con la cuenta de gestor global de su suscripción de prueba de Office 365 E5. Para obtener ayuda, visite [dónde puede iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Desde la ficha **Página de inicio de Microsoft Office** , haga clic en el mosaico de **Admin** .
    
3. Desde la ficha del **Centro de administración de Office** nueva del explorador, haga clic en **centros de administración > seguridad &amp; Compliance**.
    
4. Desde la nueva **Inicio - seguridad &amp; Compliance** ficha del explorador, haga clic en **las clasificaciones > etiquetas**.
    
5. Desde el **Home > etiquetas** panel, haga clic en **crear una etiqueta**.
    
6. En el panel de **la etiqueta de nombre** , escriba **Público interno**y, a continuación, haga clic en **siguiente**.
    
7. En el panel de **configuración de etiquetas** , haga clic en **siguiente**.
    
8. En el panel **Revisar la configuración** , haga clic en **crear esta etiqueta**y, a continuación, haga clic en **Cerrar**.
    
9. Repita los pasos 5 a 8 para estas etiquetas adicionales:
    
  - Privada
    
  - Confidencial
    
  - Altamente confidencial
    
10. Desde el **Home > etiquetas** panel, haga clic en **etiquetas de publicar**.
    
11. En el panel **etiquetas elegir publicar** , haga clic en **Elegir etiquetas para publicar**.
    
12. En el panel **etiquetas de elegir** , haga clic en **Agregar** y seleccione todas las etiquetas de cuatro.
    
13. Haga clic en **Listo**.
    
14. En el panel **etiquetas elegir publicar** , haga clic en **siguiente**.
    
15. En el panel **Elegir ubicaciones** , haga clic en **siguiente**.
    
16. En el panel **nombre de la directiva** , escriba **nombre de** **organización de ejemplo** y, a continuación, haga clic en **siguiente**.
    
17. En el panel **Revisar la configuración** , haga clic en **etiquetas de publicar**y, a continuación, haga clic en **Cerrar**.
    
## <a name="phase-4-create-your-sharepoint-online-team-sites"></a>Fase 4: Crear sus sitios de equipo de SharePoint Online

En esta fase, cree y configure los cuatro tipos de sitios de grupo de SharePoint Online para su organización de ejemplo.
  
### <a name="organization-wide-team-site"></a>Sitio de grupo amplio de organización

Para crear un sitio de equipo de SharePoint Online público previsto, haga lo siguiente:
  
1. Si es necesario, utilice un explorador en el equipo local e inicie sesión en el portal de Office 365 mediante su cuenta de administrador global. Para obtener ayuda, visite [dónde puede iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. En la lista de fichas, haga clic en **SharePoint**.
    
3. En la ficha nuevo de **SharePoint** en el explorador, haga clic en **Crear sitio +**.
    
4. En la página **crear un sitio Web** , haga clic en **sitio de equipo**.
    
5. En **nombre del sitio**, escriba la **organización extensa**. 
    
6. En **Descripción del sitio de equipo**, escriba el **sitio de SharePoint para toda la organización**.
    
7. En **la configuración de privacidad**, seleccione **pública - cualquier persona de la organización puede tener acceso a este sitio**y, a continuación, haga clic en **siguiente**.
    
8. En el **que desea agregar?** panel, haga clic en **Finalizar**.
    
A continuación, configure la carpeta de documentos del sitio del grupo gran organización de la etiqueta interna pública.
  
1. En la ficha **Home de toda la organización** del explorador, haga clic en **documentos**.
    
2. Haga clic en el icono de configuración y, a continuación, haga clic en **configuración de la biblioteca**.
    
3. En **permisos y administración**, haga clic en **Aplicar etiqueta a los elementos de esta biblioteca**.
    
4. En **Aplicar configuración de etiqueta**, seleccione **Público interno**y, a continuación, haga clic en **Guardar**.
    
Esta es la configuración resultante.
  
![Protección de nivel de línea base del sitio de grupo de SharePoint Online público de toda la organización.](images/25c86847-a38d-49ad-bb5f-c7c04206b6dc.png)
  
### <a name="project-1-team-site"></a>Sitio de grupo de proyecto 1

Para crear un sitio de grupo de línea de base privado SharePoint Online para un proyecto dentro de la organización, realice lo siguiente:
  
1. Si es necesario, utilice un explorador en el equipo local e inicie sesión en el portal de Office 365 mediante su cuenta de administrador global. Para obtener ayuda, visite [dónde puede iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. En la lista de fichas, haga clic en **SharePoint**.
    
3. En la ficha nuevo de **SharePoint** en el explorador, haga clic en **Crear sitio +**.
    
4. En la página **crear un sitio Web** , haga clic en **sitio de equipo**.
    
5. En **nombre del sitio**, escriba **1 proyecto**. 
    
6. En la **Descripción del sitio de equipo,** escriba **el sitio de SharePoint para el proyecto 1**.
    
7. En **la configuración de privacidad**, seleccione **Private: sólo los miembros pueden tener acceso a este sitio**y, a continuación, haga clic en **siguiente**.
    
8. En el **que desea agregar?** panel, haga clic en **Finalizar**.
    
A continuación, configure la carpeta de documentos del sitio del grupo 1 de proyecto para la etiqueta privada.
  
1. En la ficha **proyecto 1 Inicio** del explorador, haga clic en **documentos**.
    
2. Haga clic en el icono de configuración y, a continuación, haga clic en **configuración de la biblioteca**.
    
3. En **permisos y administración**, haga clic en **Aplicar etiqueta a los elementos de esta biblioteca**.
    
4. En **Aplicar configuración de etiqueta**, seleccione **privado**y, a continuación, haga clic en **Guardar**.
    
Esta es la configuración resultante.
  
![Protección de nivel de línea base del sitio de grupo de SharePoint Online privado Project1.](images/ecd96376-b5dc-4042-9cbd-b3765507ace7.png)
  
### <a name="marketing-campaigns-team-site"></a>Sitio de grupo de campañas de marketing

Para crear un nivel sensible aislado SharePoint Online team sitio para recursos de campaña de marketing, realice lo siguiente:
  
1. Mediante un explorador en el equipo local, inicie sesión en el portal de Office 365 mediante su cuenta de administrador global. Para obtener ayuda, visite [dónde puede iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. En la lista de fichas, haga clic en **SharePoint**.
    
3. En la ficha nuevo de **SharePoint** en el explorador, haga clic en **Crear sitio +**.
    
4. En la página **crear un sitio Web** , haga clic en **sitio de equipo**.
    
5. En **nombre de sitio de equipo**, escriba **campañas de Marketing**.
    
6. En **Descripción del sitio de equipo**, escriba el **sitio de SharePoint para recursos de campaña de marketing (confidenciales)**.
    
7.  En **la configuración de privacidad**, seleccione **Private: sólo los miembros pueden tener acceso a este sitio**y, a continuación, haga clic en **siguiente**.
    
8. En el **que desea agregar?** panel, haga clic en **Finalizar**.
    
9. En la nueva ficha de **campañas de Marketing** en el explorador, en la barra de herramientas, haga clic en el icono de configuración y, a continuación, haga clic en **permisos del sitio**.
    
10. En el panel **permisos de sitio** , haga clic en **configuración de permisos avanzados**.
    
11. En la ficha **permisos** de nuevo en el explorador, haga clic en **Configuración de solicitud de acceso**.
    
12. En el cuadro de diálogo **Configuración de solicitud de acceso** , desactive las casillas de verificación **Permitir miembros para compartir el sitio y archivos y carpetas individuales** y **miembros de permitir invitar a otras personas al grupo de miembros del sitio** , escriba **ITAdmin1 @**\<su nombre de la organización >**. onmicrosoft.com** en **Enviar todas las solicitudes de acceso**y, a continuación, haga clic en **Aceptar**.
    
13. En la lista, haga clic en **los miembros de las campañas de Marketing** .
    
14. En la página **personas y grupos** , haga clic en **nuevo**.
    
15. En el cuadro de diálogo **Compartir** , escriba **personal de Marketing**, selecciónelo y, a continuación, haga clic en **Compartir**.
    
16. Repita los pasos 14 y 15 para la cuenta de usuario de **Researcher1** .
    
17. Haga clic en el botón Atrás del explorador.
    
18. En la lista, haga clic en **campañas de Marketing propietarios** .
    
19. En la página **personas y grupos** , haga clic en **nuevo**.
    
20. En el cuadro de diálogo **Compartir** , escriba **personal de TI**, selecciónelo y, a continuación, haga clic en **Compartir**.
    
21. Haga clic en el botón Atrás del explorador.
    
22. Cierre la ficha **personas y grupos** en el explorador, haga clic en la ficha **Inicio de campañas de Marketing** en el explorador y, a continuación, cierre el panel de **permisos del sitio** .
    
A continuación se indican los resultados de la configuración de permisos:
  
- El grupo de SharePoint de **Integrantes de campañas de Marketing** contiene sólo el grupo de **campañas de Marketing** (que contiene la cuenta de usuario de administrador global), en el grupo de **personal de Marketing** (que contiene los usuarios Marketing1 y Marketing2 cuentas) y la cuenta de usuario de **Researcher1** .
    
- El grupo de SharePoint **Propietarios de campañas de Marketing** contiene sólo el grupo de **personal de TI** (que contiene sólo las cuentas de usuario ITAdmin1 y ITAdmin2).
    
- El grupo de SharePoint **Visitantes de campañas de Marketing** no contiene grupos o cuentas de usuario.
    
- Los miembros no pueden modificar los permisos de nivel de sitio (Esto sólo es posible miembros del grupo **Propietarios de campañas de Marketing** ).
    
- Otras cuentas de usuario no tiene acceso a sus recursos o el sitio, pero pueden solicitar el acceso al sitio, que enviará un correo electrónico al buzón de la cuenta de usuario de ITAdmin1.
    
A continuación, configure la carpeta de documentos del sitio de grupo de campañas de Marketing para la etiqueta sensible.
  
1. En la ficha **Inicio de campañas de Marketing** del explorador, haga clic en **documentos**.
    
2. Haga clic en el icono de configuración y, a continuación, haga clic en **configuración de la biblioteca**.
    
3. En **permisos y administración**, haga clic en **Aplicar etiqueta a los elementos de esta biblioteca**.
    
4. En **Aplicar configuración de etiqueta**, seleccione **confidencial**y, a continuación, haga clic en **Guardar**.
    
A continuación, configurar una directiva de prevention (DLP) de pérdida de datos que notifica a los usuarios que comparten un documento en un sitio de grupo SharePoint Online con la etiqueta confidencial, que incluye el sitio de campañas de Marketing, fuera de la organización.
  
1. En la ficha **Página de inicio de Microsoft Office** en el explorador, haga clic en el **seguridad &amp; Compliance** mosaico.
    
2. En el nuevo **seguridad &amp; Compliance** , haga clic en el explorador **prevención de pérdidas de datos > directiva de**.
    
3. En el panel de **prevención de pérdidas de datos** , haga clic en **+ crear una directiva**.
    
4. En el **comenzar con una plantilla o crear una directiva personalizada** panel, haga clic en **personalizado**y, a continuación, haga clic en **siguiente**.
    
5. En el panel **nombre de la directiva** , escriba **sitios de equipo de SharePoint Online etiqueta sensible** en **nombre**y, a continuación, haga clic en **siguiente**.
    
6. En el panel **Elegir ubicaciones** , haga clic en **Dejarme elegir ubicaciones específicas**y, a continuación, haga clic en **siguiente**.
    
7. En la lista de ubicaciones, deshabilitar las ubicaciones de **correo electrónico de Exchange** y **cuentas de OneDrive** y, a continuación, haga clic en **siguiente**.
    
8. En el panel **Personalizar los tipos de información confidencial que desea proteger** , haga clic en **Editar**.
    
9. En el panel **Elija los tipos de contenido para proteger** , haga clic en **Agregar** en el cuadro de lista desplegable y, a continuación, haga clic en **etiquetas**.
    
10. En el panel **etiquetas** , haga clic en **+ Agregar**, seleccione la etiqueta **confidencial** , haga clic en **Agregar**y, a continuación, haga clic en **Listo**.
    
11. En el panel **Elija los tipos de contenido para proteger** , haga clic en **Guardar**.
    
12. En el panel **Personalizar los tipos de información confidencial que desea proteger** , haga clic en **siguiente**.
    
13. En la **¿Qué desea hacer si se detecta información sensible?** panel, haga clic en **Personalizar la sugerencia y correo electrónico**.
    
14. En el panel de **sugerencias de directiva personalizar y notificaciones por correo electrónico** , haga clic en **Personalizar el texto de sugerencia de directiva**.
    
15. En el cuadro texto, escriba o pegue lo siguiente:
    
  - Para compartir con otros usuarios fuera de la organización, descargue el archivo y, a continuación, ábralo. Haga clic en archivo, a continuación, Proteger documento y a continuación, cifrar con contraseña y, a continuación, especifique una contraseña segura. Enviar la contraseña en un correo electrónico u otros medios de comunicación.
    
16. Haga clic en **Aceptar**.
    
17. En la **¿Qué desea hacer si se detecta información sensible?** panel, desactive la casilla de verificación **Bloquear personas compartan y restringir el acceso al contenido compartido** y, a continuación, haga clic en **siguiente**.
    
18. En el **¿desea activar las cosas de la política o prueba primero?** panel, haga clic en **Sí, activarlo inmediatamente**y, a continuación, haga clic en **siguiente**.
    
19. En el panel **Revisar la configuración** , haga clic en **crear**y, a continuación, haga clic en **Cerrar**.
    
Esta es la configuración resultante.
  
![Protección de nivel confidencial del sitio de grupo de SharePoint Online aislado de campañas de marketing.](images/33992bd5-96ee-4bfb-9ecf-c8a6736dd100.png)
  
### <a name="company-strategy-team-site"></a>Sitio de grupo de estrategia de la empresa

Para crear un sitio de grupo SharePoint Online aislado en el nivel de recursos de empresa estratégico de los ejecutivos de la organización altamente confidencial, haga lo siguiente:
  
1. Si es necesario, utilice un explorador en el equipo local e inicie sesión en el portal de Office 365 mediante su cuenta de administrador global. Para obtener ayuda, visite [dónde puede iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. En la lista de fichas, haga clic en **SharePoint**.
    
3. En la ficha nuevo de **SharePoint** en el explorador, haga clic en **Crear sitio +**.
    
4. En la página **crear un sitio Web** , haga clic en **sitio de equipo**.
    
5. En **nombre de sitio de equipo**, escriba la **estrategia de la empresa**.
    
6. En **Descripción del sitio de equipo**, escriba el **sitio de SharePoint para la estrategia de la empresa (confidencial)**.
    
7.  En **la configuración de privacidad**, seleccione **Private: sólo los miembros pueden tener acceso a este sitio**y, a continuación, haga clic en **siguiente**.
    
8. En el **que desea agregar?** panel, haga clic en **Finalizar**.
    
9. En la ficha nuevo de la **estrategia de la empresa** en el explorador, en la barra de herramientas, haga clic en el icono de configuración y, a continuación, haga clic en **permisos del sitio**.
    
10. En el panel **permisos de sitio** , haga clic en **configuración de permisos avanzados**.
    
11. En la ficha **permisos** de nuevo en el explorador, haga clic en **Configuración de solicitud de acceso**.
    
12. En el cuadro de diálogo **Configuración de solicitud de acceso** , desactive **Permitir miembros para compartir el sitio y archivos y carpetas individuales** y **miembros de permitir invitar a otras personas al grupo de miembros del sitio** (de modo que todas las casillas de verificación está desactivadas) y, a continuación, haga clic en ** Aceptar**.
    
13. En la lista, haga clic en **miembros de estrategia de la empresa** .
    
14. En la página **personas y grupos** , haga clic en **nuevo**.
    
15. En el cuadro de diálogo **Compartir** , escriba **C-Suite**, selecciónelo y, a continuación, haga clic en **Compartir**.
    
16. En la lista, haga clic en **la estrategia de la empresa propietarios** .
    
17. En la página **personas y grupos** , haga clic en **nuevo**.
    
18. En el cuadro de diálogo **Compartir** , escriba **personal de TI**, selecciónelo y, a continuación, haga clic en **Compartir**.
    
19. Haga clic en el botón Atrás del explorador.
    
20. Cierre la ficha **personas y grupos** en el explorador, haga clic en la ficha **Página principal de estrategia de la empresa** en el explorador y, a continuación, cierre el panel de **permisos del sitio** .
    
A continuación se indican los resultados de la configuración de permisos:
  
- El grupo de SharePoint **Miembros de estrategia de la compañía** contiene sólo el grupo **Ejecutivos** (que contiene sólo las cuentas de usuario de director ejecutivo, director financiero y director) y el grupo de **estrategia de la empresa** (que contiene sólo la cuenta de usuario de administrador global).
    
- El grupo de SharePoint **Propietarios de estrategia de la compañía** contiene el grupo de **personal de TI** (que contiene sólo las cuentas de usuario ITAdmin1 y ITAdmin2).
    
- El grupo de SharePoint **Visitantes de estrategia de la compañía** no contiene grupos o cuentas de usuario.
    
- Los miembros no pueden modificar los permisos de nivel de sitio (Esto sólo es posible miembros del grupo **Propietarios de estrategia de la empresa** ).
    
- Otras cuentas de usuario no pueden tener acceso a sus recursos o el sitio o solicitar acceso al sitio. Permisos adicionales para el sitio deben realizarse por el administrador global o por un miembro del grupo de **Propietarios de estrategia de la empresa** .
    
A continuación, configure la carpeta de documentos del sitio del grupo empresa estrategia para la etiqueta altamente confidencial.
  
1. En la ficha **Página principal de estrategia de la compañía** del explorador, haga clic en **documentos**.
    
2. Haga clic en el icono de configuración y, a continuación, haga clic en **configuración de la biblioteca**.
    
3. En **permisos y administración**, haga clic en **Aplicar etiqueta a los elementos de esta biblioteca**.
    
4. En **Aplicar configuración de etiqueta**, seleccione **Confidencial**y, a continuación, haga clic en **Guardar**.
    
A continuación, configure una directiva DLP que impide a los usuarios cuando se comparten un documento en un sitio de grupo SharePoint Online con la etiqueta altamente confidencial, que incluye el sitio de la estrategia de la empresa, fuera de la organización.
  
1. Si es necesario, utilizar un explorador en el equipo local e iniciar sesión en el portal de Office 365 con una cuenta que tiene la función de administrador de seguridad o de la empresa. Para obtener ayuda, visite [dónde puede iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. En la ficha **Página de inicio de Microsoft Office** en el explorador, haga clic en el **seguridad &amp; Compliance** mosaico.
    
3. En el nuevo **seguridad &amp; Compliance** , haga clic en el explorador **prevención de pérdidas de datos > directiva de**.
    
4. En el panel de **prevención de pérdidas de datos** , haga clic en **+ crear una directiva**.
    
5. En el **comenzar con una plantilla o crear una directiva personalizada** panel, haga clic en **personalizado**y, a continuación, haga clic en **siguiente**.
    
6. En el panel **nombre de la directiva** , escriba **sitios de equipo de SharePoint Online de etiqueta altamente confidencial** en **nombre**y, a continuación, haga clic en **siguiente**.
    
7. En el panel **Elegir ubicaciones** , haga clic en **Dejarme elegir ubicaciones específicas**y, a continuación, haga clic en **siguiente**.
    
8. En la lista de ubicaciones, deshabilitar las ubicaciones de **correo electrónico de Exchange** y **cuentas de OneDrive** y, a continuación, haga clic en **siguiente**.
    
9. En el panel **Personalizar los tipos de información confidencial que desea proteger** , haga clic en **Editar**.
    
10. En el panel **Elija los tipos de contenido para proteger** , haga clic en **Agregar** en el cuadro de lista desplegable y, a continuación, haga clic en **etiquetas**.
    
11. En el panel **etiquetas** , haga clic en **+ Agregar**, seleccione la etiqueta **Altamente confidencial** , haga clic en **Agregar**y, a continuación, haga clic en **Listo**.
    
12. En el panel **Elija los tipos de contenido para proteger** , haga clic en **Guardar**.
    
13. En el panel **Personalizar los tipos de información confidencial que desea proteger** , haga clic en **siguiente**.
    
14. En la **¿Qué desea hacer si se detecta información sensible?** panel, haga clic en **Personalizar la sugerencia y correo electrónico**.
    
15. En el panel de **sugerencias de directiva personalizar y notificaciones por correo electrónico** , haga clic en **Personalizar el texto de sugerencia de directiva**.
    
16. En el cuadro texto, escriba o pegue lo siguiente:
    
  - Para compartir con otros usuarios fuera de la organización, descargue el archivo y, a continuación, ábralo. Haga clic en archivo, a continuación, Proteger documento y a continuación, cifrar con contraseña y, a continuación, especifique una contraseña segura. Enviar la contraseña en un correo electrónico u otros medios de comunicación.
    
17. Haga clic en **Aceptar**.
    
18. En la **¿Qué desea hacer si se detecta información sensible?** panel, seleccione **requerir una justificación comercial para reemplazar**y, a continuación, haga clic en **siguiente**.
    
19. En el **¿desea activar las cosas de la política o prueba primero?** panel, haga clic en **Sí, activarlo inmediatamente**y, a continuación, haga clic en **siguiente**.
    
20. En el panel **Revisar la configuración** , haga clic en **crear**y, a continuación, haga clic en **Cerrar**.
    
A continuación, siga las instrucciones en [Activar Azure RMS con el centro de administración de Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).
  
A continuación, configurar la protección de la información de Azure con una nueva directiva con ámbito y Sub-etiqueta de protección y los permisos con los pasos siguientes:
  
1. Iniciar sesión en el portal de Office 365 con una cuenta que tiene la función de administrador de seguridad o de la empresa. Para obtener ayuda, visite [dónde puede iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. En una ficha independiente del explorador, vaya al portal de Azure ([https://portal.azure.com](https://portal.azure.com)).
    
3. Si es la primera vez se configura la protección de la información de Azure, consulte estas [instrucciones](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).
    
4. En el panel lista, haga clic en **más servicios**, escriba la **información**y, a continuación, haga clic en **Protección de la información de Azure**.
    
5. En la hoja de **protección de la información de Azure** , haga clic en **ámbito directivas > + Agregar una nueva directiva de**.
    
6. Escriba **CompanyStrategy** en el **nombre de directiva** y **etiqueta de documentos en el sitio de grupo de estrategia de la empresa** en la **Descripción**.
    
7. Haga clic en **Seleccionar qué usuarios o grupos Obtén esta directiva > grupos de usuarios/**y, a continuación, seleccione **Conjunto de C**.
    
8. Haga clic en **Seleccionar > Aceptar**.
    
9. Para la etiqueta **Altamente confidencial** , haga clic en los puntos suspensivos (...) y, a continuación, haga clic en **Agregar una etiqueta Sub**.
    
10. Escriba un nombre para la Sub-etiqueta de **nombre** y una descripción de la etiqueta de **Descripción**.
    
11. **Establecer permisos para documentos y correos electrónicos con esta etiqueta**, haga clic en **proteger**.
    
12. En la sección de **protección** , haga clic en **Azure (clave de nube)**.
    
13. En la hoja de **protección** , en **configuración de protección**, haga clic en **+ Agregar permisos**.
    
14. En la hoja de **permisos para agregar** , en **especificar usuarios y grupos**, haga clic en **+ Examinar directorio**.
    
15. En el panel de **DAA usuarios y grupos** , seleccione **Conjunto de C**y, a continuación, haga clic en **Seleccionar**.
    
16. En **Elija el ajuste preestablecido los permisos**, desactive las casillas de verificación **Imprimir**, **Copiar y extraer contenido**y **hacia delante** .
    
17. Haga clic en **Aceptar** dos veces.
    
18. En la hoja **secundario-etiqueta** , haga clic en **Guardar**.
    
19. Cierre el nuevo blade de ámbito de la política.
    
20. En el módulo de **protección de la información de Azure - directivas de ámbito** , haga clic en **Publicar**y, a continuación, haga clic en **Sí**.
    
Para proteger un documento con la protección de la información de Azure y esta nueva etiqueta, debe [instalar al cliente de protección de la información de Azure](https://docs.microsoft.com/information-protection/rms-client/install-client-app) en un equipo de prueba, instalar Office desde el portal de Office 365 y, a continuación, iniciar sesión en desde Microsoft Word con una cuenta en el ** C-Suite** grupo de su suscripción de prueba.
  
Esta es la configuración resultante.
  
![Protección de nivel alto de confidencialidad de un sitio de grupo de SharePoint Online aislado de estrategia de empresa.](images/c22695f9-50a1-4abf-a0dd-344b0c92cf94.png)
  
Ahora está listo para crear documentos en estos cuatro sitios y probar el acceso a ellos con varias cuentas de usuario en su suscripción de prueba.
  
Aquí está la configuración global para todos los sitios de equipo de SharePoint Online cuatro.
  
![Los cuatro sitios de grupo del entorno de pruebas y desarrollo de SharePoint Online seguro.](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
## <a name="next-step"></a>Siguiente paso

Cuando esté listo para la implementación de producción de sitios de SharePoint Online seguros, vea [archivos y sitios de SharePoint Online seguro](secure-sharepoint-online-sites-and-files.md) para obtener información detallada y vínculos a artículos de implementación paso a paso.
  
## <a name="see-also"></a>See Also

[Proteger los archivos y los sitios de SharePoint Online](secure-sharepoint-online-sites-and-files.md)
  
[Soluciones de seguridad](security-solutions.md)
  
[Adopción de la nube y soluciones híbridas](cloud-adoption-and-hybrid-solutions.md)
  
[Guía de seguridad de Microsoft para campañas políticas, las ONG y otras organizaciones de Agile](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)




