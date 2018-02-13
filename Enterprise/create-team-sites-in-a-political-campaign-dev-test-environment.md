---
title: "Crear sitios de equipo en un entorno de pruebas y desarrollo de campaña política"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365, Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: None
ms.custom: Strat_O365_Enterprise
ms.assetid: c2112ce8-1c4b-424f-b200-59e161db2d21
description: "Resumen: Crear sitios de equipo de SharePoint Online públicos, privados, confidenciales y altamente confidenciales en su entorno de pruebas y desarrollo de campaña política."
ms.openlocfilehash: d1515d2534713de41c16640d0008b1f8146ab300
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/13/2018
---
# <a name="create-team-sites-in-a-political-campaign-devtest-environment"></a>Crear sitios de equipo en un entorno de pruebas y desarrollo de campaña política

 **Resumen:** Crear sitios de equipo de SharePoint Online públicos, privados, confidenciales y altamente confidenciales en su entorno de pruebas y desarrollo de campaña política. 
  
Siga las instrucciones de este artículo para crear un entorno de pruebas y desarrollo que incluye los cuatro tipos diferentes de sitios de grupo de SharePoint Online para obtener la [Guía de seguridad de Microsoft para campañas políticas, las ONG y otras organizaciones de Agile](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) solución. Estos sitios se describen detalladamente en el tema 10, titulado **SharePoint y OneDrive para el negocio**.
  
## <a name="phase-1-create-your-political-campaign-devtest-environment"></a>Fase 1: Crear el entorno de pruebas y desarrollo de campaña política

En primer lugar, siga las instrucciones de [Configurar grupos y usuarios de un entorno de pruebas y desarrollo de campaña política](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md) para crear suscripciones, usuarios y grupos.
  
## <a name="phase-2-create-office-365-labels"></a>Fase 2: Crear etiquetas de Office 365

En esta fase, crear las etiquetas para los diferentes niveles de seguridad de carpetas de documentos de SharePoint Online team site.
  
1. Si es necesario, iniciar sesión en el portal de Office 365 con las credenciales de la cuenta de administrador global de su suscripción de prueba. Para obtener ayuda, visite [dónde puede iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Desde la ficha **Página de inicio de Microsoft Office** , haga clic en el mosaico de **Admin** .
    
3. Desde la ficha del **Centro de administración de Office** nueva del explorador, haga clic en **centros de administración > seguridad &amp; Compliance**.
    
4. Desde la nueva **Inicio - seguridad &amp; Compliance** ficha del explorador, haga clic en **las clasificaciones > etiquetas**.
    
5. Desde el **Home > etiquetas** panel, haga clic en **crear una etiqueta**.
    
6. En el panel **nombre de la etiqueta** , tipo **interno**y, a continuación, haga clic en **siguiente**.
    
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
    
16. En el panel **nombre de la directiva** , escriba **nombre de** **campaña** y, a continuación, haga clic en **siguiente**.
    
17. En el panel **Revisar la configuración** , haga clic en **etiquetas de publicar**y, a continuación, haga clic en **Cerrar**.
    
## <a name="phase-3-create-your-sharepoint-online-team-sites"></a>Fase 3: Crear sus sitios de equipo de SharePoint Online

En esta fase, crear y configurar sitios de equipo de SharePoint Online para la campaña de política correspondientes a los cuatro tipos de sitios de grupo de SharePoint Online.
  
### <a name="campaign-wide-team-site"></a>Sitio de grupo amplio de campaña

Para crear un sitio de equipo de SharePoint Online público previsto, haga lo siguiente:
  
1. Si es necesario, utilice un explorador en el equipo local e inicie sesión en el portal de Office 365 ([https://portal.office.com](https://portal.office.com)) mediante la cuenta de administrador global.
    
2. En la lista de fichas, haga clic en **SharePoint**.
    
3. En la ficha nuevo de **SharePoint** en el explorador, haga clic en **Crear sitio +**.
    
4. En la página **crear un sitio Web** , haga clic en **sitio de equipo**.
    
5. En **nombre del sitio**, escriba **campaña amplia**. 
    
6. En **Descripción del sitio de equipo**, escriba el **sitio de SharePoint para toda la campaña**.
    
7. En **la configuración de privacidad**, seleccione **pública - cualquier persona de la organización puede tener acceso a este sitio**y, a continuación, haga clic en **siguiente**.
    
8. En el **que desea agregar?** panel, haga clic en **Finalizar**.
    
A continuación, configure la carpeta de documentos del sitio del grupo amplia campaña para la etiqueta interna.
  
1. En la ficha **toda la página de inicio de la campaña** del explorador, haga clic en **documentos**.
    
2. Haga clic en el icono de configuración y, a continuación, haga clic en **configuración de la biblioteca**.
    
3. En **permisos y administración**, haga clic en **Aplicar etiqueta a los elementos de esta biblioteca**.
    
4. En **Aplicar configuración de etiqueta**, seleccione **interna**y, a continuación, haga clic en **Guardar**.
    
### <a name="campaign-project-1-team-site"></a>Sitio del grupo 1 de proyecto de campaña

Para crear un sitio de grupo de línea de base privado SharePoint Online para un proyecto dentro de la campaña, realice lo siguiente:
  
1. Si es necesario, utilice un explorador en el equipo local e inicie sesión en el portal de Office 365 ([https://portal.office.com](https://portal.office.com)) mediante la cuenta de administrador global.
    
2. En la lista de fichas, haga clic en **SharePoint**.
    
3. En la ficha nuevo de **SharePoint** en el explorador, haga clic en **Crear sitio +**.
    
4. En la página **crear un sitio Web** , haga clic en **sitio de equipo**.
    
5. En **nombre del sitio**, escriba **proyecto campaña 1**. 
    
6. En la **Descripción del sitio de equipo,** escriba **el sitio de SharePoint para el proyecto de campaña 1**.
    
7. En **la configuración de privacidad**, seleccione **Private: sólo los miembros pueden tener acceso a este sitio**y, a continuación, haga clic en **siguiente**.
    
8. En el **que desea agregar?** panel, haga clic en **Finalizar**.
    
A continuación, configure la carpeta de documentos del sitio del grupo 1 proyecto campaña para la etiqueta privada.
  
1. En la ficha **proyecto 1-Inicio de la campaña** del explorador, haga clic en **documentos**.
    
2. Haga clic en el icono de configuración y, a continuación, haga clic en **configuración de la biblioteca**.
    
3. En **permisos y administración**, haga clic en **Aplicar etiqueta a los elementos de esta biblioteca**.
    
4. En **Aplicar configuración de etiqueta**, seleccione **privado**y, a continuación, haga clic en **Guardar**.
    
### <a name="campaign-marketing-team-site"></a>Sitio de grupo de marketing de campaña

Para crear un nivel sensible aislado SharePoint Online team sitio para la campaña de marketing de recursos, haga lo siguiente:
  
1. Mediante un explorador en el equipo local, inicie sesión en el portal de Office 365 ([https://portal.office.com](https://portal.office.com)) mediante la cuenta de administrador global.
    
2. En la lista de fichas, haga clic en **SharePoint**.
    
3. En la ficha nuevo de **SharePoint** en el explorador, haga clic en **Crear sitio +**.
    
4. En la página **crear un sitio Web** , haga clic en **sitio de equipo**.
    
5. En **nombre de sitio de equipo**, tipo de **campaña de marketing**.
    
6. En **Descripción del sitio de equipo**, escriba el **sitio de SharePoint para la campaña de marketing (confidencial)**.
    
7.  En **la configuración de privacidad**, seleccione **Private: sólo los miembros pueden tener acceso a este sitio**y, a continuación, haga clic en **siguiente**.
    
8. En el **que desea agregar?** panel, haga clic en **Finalizar**.
    
9. En la nueva ficha de **campaña de marketing** en el explorador, en la barra de herramientas, haga clic en el icono de configuración y, a continuación, haga clic en **permisos del sitio**.
    
10. En el panel **permisos de sitio** , haga clic en **configuración de permisos avanzados**.
    
11. En la ficha **permisos** de nuevo en el explorador, haga clic en **Configuración de solicitud de acceso**.
    
12. En el cuadro de diálogo **Configuración de solicitud de acceso** , desactive las casillas de verificación **Permitir miembros para compartir el sitio y archivos y carpetas individuales** y **miembros de permitir invitar a otras personas al grupo de miembros del sitio** , escriba **ITAdmin1 @** <your organization name> **. onmicrosoft.com** en **Enviar todas las solicitudes de acceso**y, a continuación, haga clic en **Aceptar**.
    
13. Haga clic en **campaña de marketing a integrantes** de la lista.
    
14. En la página **personas y grupos** , haga clic en **nuevo**.
    
15. En el cuadro de diálogo **Compartir** , escriba **Senior y personal estratégico**, selecciónelo y, a continuación, haga clic en **Compartir**.
    
16. Repita los pasos 14 y 15 para el grupo de **personal de análisis** y de la cuenta de usuario **Regular1** .
    
17. Haga clic en el botón Atrás del explorador.
    
18. En la lista, haga clic en **campaña de marketing a los propietarios** .
    
19. En la página **personas y grupos** , haga clic en **nuevo**.
    
20. En el cuadro de diálogo **Compartir** , escriba **personal de TI**, selecciónelo y, a continuación, haga clic en **Compartir**.
    
21. Haga clic en el botón Atrás del explorador.
    
22. Cierre la ficha **personas y grupos** en el explorador, haga clic en la ficha de la **Página inicial de marketing de campaña** en el explorador y, a continuación, cierre el panel de **permisos del sitio** .
    
A continuación se indican los resultados de la configuración de permisos:
  
- El grupo de SharePoint de **Integrantes de marketing campaña** contiene sólo el **Director y el personal estratégico** grupo (que contiene las cuentas de usuario de candidato, ChiefOfStaff y Strategic1), el grupo de **campaña de marketing** (que contiene el cuenta de usuario de administrador global), el grupo de **personal de Analytics** (que contiene la cuenta de usuario de DataScientist1) y la cuenta de usuario **Regular1** .
    
- El grupo de SharePoint **Propietarios de marketing campaña** contiene sólo el grupo de **personal de TI** (que contiene sólo las cuentas de usuario ITAdmin1 y ITAdmin2).
    
- El grupo de SharePoint **Visitantes de marketing de campaña** no contiene grupos o cuentas de usuario.
    
- Los miembros no pueden modificar los permisos de nivel de sitio (Esto sólo es posible miembros del grupo **Propietarios de marketing de campaña** ).
    
- Otras cuentas de usuario no tiene acceso a sus recursos o el sitio, pero pueden solicitar el acceso al sitio, que enviará un correo electrónico al buzón de la cuenta de usuario de ITAdmin1.
    
A continuación, configure la carpeta de documentos del sitio grupo marketing campaña para la etiqueta sensible.
  
1. En la ficha de la **Página inicial de marketing de campaña** del explorador, haga clic en **documentos**.
    
2. Haga clic en el icono de configuración y, a continuación, haga clic en **configuración de la biblioteca**.
    
3. En **permisos y administración**, haga clic en **Aplicar etiqueta a los elementos de esta biblioteca**.
    
4. En **Aplicar configuración de etiqueta**, seleccione **confidencial**y, a continuación, haga clic en **Guardar**.
    
A continuación, configurar una directiva de prevention (DLP) de pérdida de datos que notifica a los usuarios que comparten un documento en un sitio de grupo SharePoint Online con la etiqueta confidencial fuera de la organización. Esta directiva DLP se aplicará a los recursos en el sitio de marketing de la campaña.
  
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
    
### <a name="campaign-strategy-team-site"></a>Sitio de grupo de estrategia de campaña

Para crear un sitio de grupo SharePoint Online aislado en el nivel de recursos de estrategia de campaña altamente confidencial, haga lo siguiente:
  
1. Si es necesario, utilice un explorador en el equipo local e inicie sesión en el portal de Office 365 ([https://portal.office.com](https://portal.office.com)) mediante la cuenta de administrador global.
    
2. En la lista de fichas, haga clic en **SharePoint**.
    
3. En la ficha nuevo de **SharePoint** en el explorador, haga clic en **Crear sitio +**.
    
4. En la página **crear un sitio Web** , haga clic en **sitio de equipo**.
    
5. En **nombre de sitio de equipo**, escriba **la estrategia de campaña**.
    
6. En **Descripción del sitio de equipo**, escriba el **sitio de SharePoint para la estrategia de campaña (confidencial)**.
    
7.  En **la configuración de privacidad**, seleccione **Private: sólo los miembros pueden tener acceso a este sitio**y, a continuación, haga clic en **siguiente**.
    
8. En el **que desea agregar?** panel, haga clic en **Finalizar**.
    
9. En la ficha nuevo de **la estrategia de campaña** en el explorador, en la barra de herramientas, haga clic en el icono de configuración y, a continuación, haga clic en **permisos del sitio**.
    
10. En el panel **permisos de sitio** , haga clic en **configuración de permisos avanzados**.
    
11. En la ficha **permisos** de nuevo en el explorador, haga clic en **Configuración de solicitud de acceso**.
    
12. En el cuadro de diálogo **Configuración de solicitud de acceso** , desactive **Permitir miembros para compartir el sitio y archivos y carpetas individuales** y **miembros de permitir invitar a otras personas al grupo de miembros del sitio** (de modo que todas las casillas de verificación está desactivadas) y, a continuación, haga clic en ** Aceptar**.
    
13. En la lista, haga clic en **los miembros de la estrategia de campaña** .
    
14. En la página **personas y grupos** , haga clic en **nuevo**.
    
15. En el cuadro de diálogo **Compartir** , escriba **Senior y personal estratégico**, selecciónelo y, a continuación, haga clic en **Compartir**.
    
16. En la lista, haga clic en **la estrategia de campaña propietarios** .
    
17. En la página **personas y grupos** , haga clic en **nuevo**.
    
18. En el cuadro de diálogo **Compartir** , escriba **personal de TI**, selecciónelo y, a continuación, haga clic en **Compartir**.
    
19. Haga clic en el botón Atrás del explorador.
    
20. Cierre la ficha **personas y grupos** en el explorador, haga clic en la ficha **principal de la estrategia de campaña** en el explorador y, a continuación, cierre el panel de **permisos del sitio** .
    
A continuación se indican los resultados de la configuración de permisos:
  
- El grupo de SharePoint **Miembros de estrategia de campaña** contiene sólo el grupo de **personal estratégico y Senior** (que contiene sólo las cuentas de usuario de candidato, ChiefOfStaff y Strategic1) y el grupo de **estrategia de campaña** (que contiene sólo la cuenta de administrador global).
    
- El grupo de SharePoint **Propietarios de estrategia de campaña** contiene sólo el grupo de **personal de TI** (que contiene sólo las cuentas de usuario ITAdmin1 y ITAdmin2).
    
- El grupo de SharePoint **Visitantes de estrategia de campaña** no contiene grupos o cuentas de usuario.
    
- Los miembros no pueden modificar los permisos de nivel de sitio (Esto sólo es posible miembros del grupo **Propietarios de estrategia de campaña** ).
    
- Otras cuentas de usuario no pueden tener acceso a sus recursos o el sitio o solicitar acceso al sitio. Permisos adicionales para el sitio deben realizarse por el administrador global o por un miembro del grupo de **Propietarios de estrategia de campaña** .
    
A continuación, configure la carpeta de documentos del sitio de grupo de estrategia de campaña para la etiqueta altamente confidencial.
  
1. En la ficha **principal de la estrategia de campaña** del explorador, haga clic en **documentos**.
    
2. Haga clic en el icono de configuración y, a continuación, haga clic en **configuración de la biblioteca**.
    
3. En **permisos y administración**, haga clic en **Aplicar etiqueta a los elementos de esta biblioteca**.
    
4. En **Aplicar configuración de etiqueta**, seleccione **Confidencial**y, a continuación, haga clic en **Guardar**.
    
A continuación, configure una directiva DLP que impide a los usuarios cuando se comparten un documento en un sitio de grupo SharePoint Online con la etiqueta altamente confidencial fuera de la organización. Esta directiva DLP se aplicará a los recursos en el sitio de la estrategia de campaña.
  
1. Si es necesario, utilizar un explorador en el equipo local e iniciar sesión en el portal de Office 365 ([https://portal.office.com](https://portal.office.com)) con una cuenta que tiene la función de administrador de seguridad o de la empresa.
    
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
    
Siga las instrucciones de [Activar Azure RMS con el centro de administración de Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).
  
A continuación, configurar la protección de la información de Azure con una nueva directiva con ámbito y Sub-etiqueta de protección y los permisos con los pasos siguientes:
  
1. Iniciar sesión en el portal de Office 365 con una cuenta que tiene la función de administrador de seguridad o de la empresa. Para obtener ayuda, visite [dónde puede iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. En una ficha independiente del explorador, vaya al portal de Azure ([https://portal.azure.com](https://portal.azure.com)).
    
3. Si es la primera vez se configura la protección de la información de Azure, consulte estas [instrucciones](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).
    
4. En el panel lista, haga clic en **más servicios**, escriba la **información**y, a continuación, haga clic en **Protección de la información de Azure**.
    
5. En la hoja de **protección de la información de Azure** , haga clic en **ámbito directivas > + Agregar una nueva directiva de**.
    
6. En **nombre de directiva** y la **etiqueta para los documentos en el sitio del equipo de estrategia de campaña** en **Descripción**, escriba **CampaignStrategy** .
    
7. Haga clic en **Seleccionar qué usuarios o grupos Obtén esta directiva > usuario/grupos**y luego seleccione **Senior y personal estratégico**.
    
8. Haga clic en **Seleccionar > Aceptar**.
    
9. Para la etiqueta **Altamente confidencial** , haga clic en los puntos suspensivos (...) y, a continuación, haga clic en **Agregar una etiqueta Sub**.
    
10. Escriba un nombre para la Sub-etiqueta de **nombre** y una descripción de la etiqueta de **Descripción**.
    
11. **Establecer permisos para documentos y correos electrónicos con esta etiqueta**, haga clic en **proteger**.
    
12. En la sección de **protección** , haga clic en **Azure (clave de nube)**.
    
13. En la hoja de **protección** , en **configuración de protección**, haga clic en **+ Agregar permisos**.
    
14. En la hoja de **permisos para agregar** , en **especificar usuarios y grupos**, haga clic en **+ Examinar directorio**.
    
15. En el panel de **DAA usuarios y grupos** , seleccione el **Director y el personal estratégico**y, a continuación, haga clic en **Seleccionar**.
    
16. En **Elija el ajuste preestablecido los permisos**, desactive las casillas de verificación **Imprimir**, **Copiar y extraer contenido**y **hacia delante** .
    
17. Haga clic en **Aceptar** dos veces.
    
18. En la hoja **secundario-etiqueta** , haga clic en **Guardar**.
    
19. Cierre el nuevo blade de ámbito de la política.
    
20. En el módulo de **protección de la información de Azure - directivas de ámbito** , haga clic en **Publicar**y, a continuación, haga clic en **Sí**.
    
Ahora está listo para empezar a crear documentos en estos cuatro sitios y probar el acceso a ellos con varias cuentas de usuario en su suscripción de prueba. 
  
Para proteger un documento con la protección de la información de Azure y esta nueva etiqueta, debe [instalar al cliente de protección de la información de Azure](https://docs.microsoft.com/information-protection/rms-client/install-client-app) en un equipo de prueba, instalar Office desde el portal de Office 365 y, a continuación, iniciar sesión en desde Microsoft Word con una cuenta en el ** Director y el personal estratégico** grupo de su suscripción de prueba.
  
## <a name="see-also"></a>Consulte también

[Guía de seguridad de Microsoft para campañas políticas, las ONG y otras organizaciones de Agile](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[Configurar grupos y usuarios de un entorno de pruebas y desarrollo de campaña política](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md)
  
[Guías de entorno de pruebas de adopción de la nube (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[Adopción de la nube y soluciones híbridas](cloud-adoption-and-hybrid-solutions.md)




