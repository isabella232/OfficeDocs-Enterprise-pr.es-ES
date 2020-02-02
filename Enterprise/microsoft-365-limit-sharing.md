---
title: Limitar el uso compartido en Microsoft 365
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection: SPO_Content
ms.custom: ''
localization_priority: Priority
description: Obtenga información sobre cómo limitar el uso compartido en Microsoft 365.
ms.openlocfilehash: dd2705aefd4f91c4ce8773019f94acf53afea6c8
ms.sourcegitcommit: 4f465f690c6563cfa9f6029d3e7e9e3cace96671
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2020
ms.locfileid: "41658824"
---
# <a name="limit-sharing-in-microsoft-365"></a>Limitar el uso compartido en Microsoft 365

Aunque no puede deshabilitar el uso compartido interno por completo ni quitar el botón Compartir de los sitios, hay varias maneras en las que puede limitar el uso compartido de Microsoft 365 para satisfacer las necesidades de la organización.

Los métodos para compartir archivos se muestran en la tabla siguiente. Haga clic en el vínculo de la columna **Método de uso compartido** para obtener información detallada.

|Método de uso compartido|Descripción|Opciones de limitación|
|:-------------|:----------|:-------------|
|[Grupo o equipo de Office 365](#office-365-group-or-team)|Los usuarios a los que se les ha concedido acceso a un equipo de Microsoft Teams o a un grupo de Office 365 pueden editar el acceso a los archivos del sitio de SharePoint asociado.|Si el grupo o equipo es privado, las invitaciones de uso compartido para unirse al equipo se envían al propietario del sitio para su aprobación. Los administradores pueden deshabilitar el acceso de invitados para impedir el acceso a personas externas a la organización.|
|[Sitio de SharePoint](#sharepoint-site)|A los usuarios se pueden conceder el acceso de propietario, miembro o visitante a un sitio de SharePoint y tendrán ese nivel de acceso a los archivos del sitio.|Los permisos del sitio se pueden restringir para que solo sus propietarios puedan compartirlo.|
|[Compartir con usuarios específicos](#sharing-with-specific-people)|Los miembros del sitio y los usuarios con permisos de edición pueden conceder permisos directos a archivos y carpetas, o compartirlos con vínculos de *Usuarios específicos*.|Los permisos del sitio se pueden restringir para que solo los propietarios del sitio puedan compartir archivos y carpetas. En este caso, el acceso directo y el uso compartido del vínculo de *Usuarios específicos* por miembros del sitio se envían al propietario para su aprobación.|
|[Uso compartido de invitados de SharePoint](#sharepoint-guest-sharing)|Los propietarios y miembros del sitio de SharePoint pueden compartir archivos y carpetas con usuarios externos a la organización.|El uso compartido de invitados se puede deshabilitar para toda la organización o para sitios individuales.|
|[Vínculos de uso compartido de *Personas de su organización*](#people-in-your-organization-sharing-links)|Los propietarios y miembros del sitio de SharePoint pueden compartir archivos con vínculos de *Personas de su organización*, que funcionarán para cualquier persona dentro de la organización.|Los vínculos de *Personas de su organización* se pueden deshabilitar en el nivel de sitio.|
|[Correo electrónico](#email)|Los usuarios que tengan acceso a un archivo pueden enviárselo a otros usuarios por correo electrónico.|Los administradores pueden cifrar archivos con las etiquetas de confidencialidad para evitar que se compartan con usuarios no autorizados.|
|[Descargar o copiar archivos](#download-or-file-copy)|Los usuarios que tienen acceso a un archivo pueden descargarlo o copiarlo y compartirlo con otros usuarios externos al ámbito de Microsoft 365.|Los administradores pueden cifrar archivos con las etiquetas de confidencialidad para evitar que se compartan con usuarios no autorizados.|

Aunque puede usar los controles de administración descritos en este artículo para limitar el uso compartido en su organización, le recomendamos que considere usar las características de seguridad y cumplimiento disponibles en Microsoft 365 para crear un entorno de uso compartido seguro. Para obtener más información, vea [Colaboración de archivos en SharePoint con Microsoft 365](https://docs.microsoft.com/sharepoint/deploy-file-collaboration) y [Teams para datos altamente regulados](https://docs.microsoft.com/microsoft-365/enterprise/secure-teams-highly-regulated-data-scenario).

Para comprender cómo se usa el uso compartido en su organización, [ejecute un informe sobre el uso compartido de archivos y carpetas](https://docs.microsoft.com/sharepoint/sharing-reports).

## <a name="office-365-group-or-team"></a>Grupo o equipo de Office 365

Si quiere limitar el uso compartido en un grupo de Office 365 o un equipo de Microsoft Teams, es importante que el grupo o equipo sea privado. Los usuarios dentro de su organización pueden unirse a un equipo o grupo público en cualquier momento. Si el grupo o equipo no es privado, no hay ninguna forma de limitar el uso compartido del equipo o de sus archivos en la organización.

### <a name="guest-sharing"></a>Uso compartido de invitados

Si quiere evitar el acceso de invitados en Teams, puede desactivar el uso compartido de invitados en el centro de administración de Teams.

Para desactivar el uso compartido de invitados en Teams
1. En el centro de administración de Teams, expanda **Configuración de toda la organización** y, después, haga clic en **Acceso de invitado**.
2. Desactive **Permitir el acceso de invitado en Teams**.
3. Haga clic en **Guardar**.

Si quiere evitar el acceso de invitado en los grupos de Office 365, puede desactivar la configuración del acceso de invitado de los grupos en el Centro de administración de Microsoft 365.

Para desactivar el uso compartido de invitados en los grupos de Office 365
1. En el Centro de administración de Microsoft 365, haga clic en **Configuración** y, después, haga clic en **Configuración**.
2. En la pestaña **Servicios**, haga clic en **Grupos de Office 365**.
3. Desactive las casillas **Permitir que los miembros del grupo de fuera de la organización tengan acceso al contenido del grupo** y **Permitir que los propietarios de grupos agreguen a usuarios ajenos a la organización a los grupos**.
4. Haga clic en **Guardar cambios**.

    ![Captura de pantalla de la configuración de uso compartido de grupos de Office 365 en el Centro de administración de Microsoft 365](media/office-365-groups-guest-settings-off.png)

> [!NOTE]
> Si quiere evitar el uso compartido de invitados para un grupo o equipo determinado, puede usar Microsoft PowerShell. Vea [Bloquear a los usuarios invitados de un grupo específico](https://docs.microsoft.com/office365/admin/create-groups/manage-guest-access-in-groups?view=o365-worldwide#block-guest-users-from-a-specific-group) para más detalles.

Puede limitar el uso compartido de invitados a usuarios de dominios específicos al permitir o bloquear dominios en Azure Active Directory. Esto también afecta al uso compartido de invitados en SharePoint si ha habilitado la [integración de SharePoint y OneDrive con Azure AD B2B](https://docs.microsoft.com/sharepoint/sharepoint-azureb2b-integration-preview).

Para permitir las invitaciones de uso compartido solo de dominios específicos
1. En la página Información general de Azure Active Directory, haga clic en **Relaciones de la organización**.
2. Haga clic en **Configuración**.
3. En **Restricciones de colaboración**, seleccione **Denegar las invitaciones a los dominios especificados** o **Permitir solo invitaciones a los dominios especificados** y, después, escriba los dominios que quiera usar.
4. Haga clic en **Guardar**.

    ![Captura de pantalla de la configuración de restricciones de colaboración en Azure Active Directory](media/azure-ad-allow-only-specified-domains.png)

## <a name="sharepoint-site"></a>Sitio de SharePoint

Puede limitar el uso compartido de sitios de SharePoint solo a los propietarios del sitio. Esto impide que los miembros del sitio lo compartan. Tenga en cuenta que si el sitio está conectado a un grupo de Office 365, sus miembros pueden invitar a otros usuarios al grupo, lo que les dará acceso al sitio.

Para limitar el uso compartido de sitios a los propietarios
1. En el sitio, haga clic en el icono de engranaje y, después, haga clic en **Permisos del sitio**.
2. En **Configuración de uso compartido**, haga clic en **Cambiar configuración de uso compartido**.
3. Seleccione **Los propietarios y miembros del sitio, y las personas con permisos de edición pueden compartir archivos y carpetas, pero solo los propietarios de sitios pueden compartir el sitio**.
4. Haga clic en **Guardar**.

    ![Captura de pantalla de la configuración de permisos de uso compartido en un sitio de SharePoint](media/sharepoint-site-sharing-permissions-level-two.png)

Puede desactivar las solicitudes de acceso para impedir que los usuarios que no sean miembros del sitio lo soliciten.

Para desactivar las solicitudes de acceso
1. En el sitio, haga clic en el icono de engranaje y, después, haga clic en **Permisos del sitio**.
2. En **Configuración de uso compartido**, haga clic en **Cambiar configuración de uso compartido**.
3. Desactive **Permitir solicitudes de acceso** y, después, haga clic en **Guardar**.

Puede limitar el uso compartido de sitios a dominios específicos al permitirlos o bloquearlos.

Para limitar el uso compartido del sitio por dominio
1. En el Centro de administración de SharePoint, en **Sitios**, haga clic en **Sitios activos**.
2. Haga clic en el sitio que quiere configurar.
3. En **Uso compartido externo** de la pestaña **Directivas**, haga clic en **Editar**.
4. En **Configuración avanzada para uso compartido externo**, seleccione **Limitar uso compartido por dominio**.
5. Agregue los dominios que quiera permitir o bloquear y, después, haga clic en **Guardar**.
6. Haga clic en **Guardar**.

    ![Captura de pantalla de la configuración en el nivel de sitio de dominios permitidos](media/limit-site-sharing-by-domain.png)

## <a name="sharing-with-specific-people"></a>Compartir con usuarios específicos

Si quiere limitar el uso compartido de un sitio o de su contenido, puede configurarlo para que solo los propietarios puedan compartir archivos, carpetas y el sitio. Cuando se configura, los intentos de los miembros del sitio para compartir archivos o carpetas con vínculos de *Usuarios específicos* se envían al propietario del sitio para su aprobación.

Para limitar el uso compartido de sitios, archivos y carpetas a los propietarios
1. En el sitio, haga clic en el icono de engranaje y, después, haga clic en **Permisos del sitio**.
2. En **Configuración de uso compartido**, haga clic en **Cambiar configuración de uso compartido**.
3. Seleccione **Solo los propietarios del sitio pueden compartir archivos, carpetas y el sitio**.
4. Haga clic en **Guardar**.

    ![Captura de pantalla de la configuración de permisos de uso compartido en un sitio de SharePoint](media/sharepoint-site-only-site-owners-can-share.png)

## <a name="sharepoint-guest-sharing"></a>Uso compartido de invitados de SharePoint

Si quiere evitar el uso compartido de archivos y carpetas de SharePoint o OneDrive con usuarios externos a la organización, puede desactivar el uso compartido de invitados para toda la organización o para un sitio individual.

Para desactivar el uso compartido de invitados de SharePoint en su organización
1. En el Centro de administración de SharePoint, en **Directivas**, haga clic en **Uso compartido**.
2. En **Uso compartido externo**, arrastre el control deslizante de SharePoint hacia abajo hasta **Solo los usuarios de la organización**.
3. Haga clic en **Guardar**.

    ![Captura de pantalla de la configuración de uso compartido en el nivel de organización de SharePoint](media/sharepoint-tenant-sharing-off.png)


Para desactivar el uso compartido de invitados en un sitio
1. En el Centro de administración de SharePoint, en **Sitios**, haga clic en **Sitios activos**.
2. Haga clic en el sitio que quiere configurar.
3. En **Uso compartido externo** de la pestaña **Directivas**, haga clic en **Editar**.
4. En **Uso compartido externo**, elija **Solo los usuarios de la organización** y, después, haga clic en **Guardar**.

    ![Captura de pantalla de la configuración del uso compartido en el nivel de sitio de SharePoint](media/sharepoint-site-external-sharing-settings-off.png)

Si quiere permitir el uso compartido con personas externas a la organización, pero quiere asegurarse de que todos los usuarios se autentican, puede deshabilitar los vínculos de tipo *Cualquiera* (uso compartido anónimo) para toda la organización o para un sitio individual.

Para desactivar los vínculos de tipo *Cualquiera* en el nivel de organización
1. En el Centro de administración de SharePoint, en **Directivas**, haga clic en **Uso compartido**.
2. En **Uso compartido externo**, arrastre el control deslizante de SharePoint hacia abajo hasta **Invitados nuevos y existentes**.
3. Haga clic en **Guardar**.

    ![Captura de pantalla de la configuración del uso compartido en el nivel de sitio de SharePoint](media/sharepoint-guest-sharing-new-and-existing-guests.png)

Para desactivar los vínculos de tipo *Cualquiera* de un sitio
1. En el Centro de administración de SharePoint, en **Sitios**, haga clic en **Sitios activos**.
2. Haga clic en el sitio que quiere configurar.
3. En **Uso compartido externo** de la pestaña **Directivas**, haga clic en **Editar**.
4. En **Uso compartido externo**, elija **Invitados nuevos y existentes** y, después, haga clic en **Guardar**.

    ![Captura de pantalla de la configuración del uso compartido en el nivel de sitio de SharePoint](media/sharepoint-site-external-sharing-settings-new-and-existing-guests.png)

## <a name="people-in-your-organization-sharing-links"></a>Vínculos de uso compartido de *Personas de su organización*

De forma predeterminada, los miembros de un sitio pueden compartir archivos y carpetas con otras personas de su organización con un vínculo de *Personas de su organización*. Puede deshabilitar los vínculos de *Personas de su organización* con PowerShell:

`Set-SPOSite -Identity <site> -DisableCompanyWideSharingLinks`

Por ejemplo:

`Set-SPOSite -Identity https://contoso.sharepoint.com -DisableCompanyWideSharingLinks`

## <a name="email"></a>Correo electrónico

Puede evitar el uso compartido no deseado de mensajes de correo electrónico mediante el cifrado. Esto impide que los mensajes de correo electrónico se reenvíen o se compartan de algún modo con usuarios no autorizados. El cifrado de correo electrónico se puede habilitar mediante etiquetas de confidencialidad. Para más detalles, vea [Restringir el acceso al contenido mediante el cifrado en las etiquetas de confidencialidad](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels).

## <a name="download-or-file-copy"></a>Descargar o copiar archivos

Los usuarios que tienen acceso a los archivos y carpetas de Microsoft 365 pueden descargar archivos y copiarlos en medios externos. Para reducir el riesgo del uso compartido de archivos no deseados, puede cifrar el contenido con las etiquetas de confidencialidad.

## <a name="see-also"></a>Vea también

[Referencia de la configuración de uso compartido de invitados de Microsoft 365](microsoft-365-guest-settings.md)