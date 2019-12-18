---
title: Colaborar con invitados en un sitio
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
description: Obtenga información sobre cómo colaborar con invitados en un sitio de SharePoint.
ms.openlocfilehash: 31e1365467729753cec358b4fb33462894cdcbb8
ms.sourcegitcommit: 9dfaeff7a1625a7325bb94f3eb322fc161ce066b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/18/2019
ms.locfileid: "40261363"
---
# <a name="collaborate-with-guests-in-a-site"></a>Colaborar con invitados en un sitio

Si necesita colaborar con invitados en documentos, datos y listas, puede usar un sitio de SharePoint. Los sitios modernos de SharePoint están conectados a Office 365 grupos que pueden administrar la pertenencia al sitio y proporcionar herramientas de colaboración adicionales, como un buzón compartido y un calendario.

En este artículo, analizaremos los pasos de configuración de Microsoft 365 necesarios para configurar un sitio de SharePoint para la colaboración con los invitados.

## <a name="video-demonstration"></a>Vídeo de demostración

En este vídeo se muestran los pasos de configuración que se describen en este documento.</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE44Llg?autoplay=false]

## <a name="azure-organizational-relationships-settings"></a>Configuración de las relaciones de organización de Azure

El uso compartido en Microsoft 365 se rige en su nivel más alto por la configuración de relaciones organizativas en Azure Active Directory. Si el uso compartido de invitado está deshabilitado o restringido en Azure AD, se invalidará cualquier configuración de uso compartido que configure en Microsoft 365.

Compruebe la configuración de relaciones de organización para asegurarse de que no se bloquee el uso compartido con invitados.

![Captura de pantalla de la página de configuración de relaciones de organización de Azure Active Directory](media/azure-ad-organizational-relationships-settings.png)

Para establecer la configuración de relación organizativa

1. Inicie sesión en Microsoft Azure en [https://portal.azure.com](https://portal.azure.com).
2. En el panel de navegación izquierdo, haga clic en **Azure Active Directory**.
3. En el panel de **información general** , haga clic en **relaciones organizativas**.
4. En el panel relaciones de la **organización** , haga clic en **configuración**.
5. Asegúrese de que los **administradores y los usuarios de la función invitador invitado puedan** invitar y que **los miembros puedan invitar** están establecidos en **sí**.
6. Si ha realizado cambios, haga clic en **Guardar**.

Anote la configuración de la sección **restricciones de colaboración** . Asegúrese de que los dominios de los invitados con los que desea colaborar no están bloqueados.

## <a name="office-365-groups-guest-settings"></a>Configuración de invitado de Office 365 Groups

Los sitios modernos de SharePoint usan grupos de Office 365 para controlar el acceso al sitio. La configuración de invitado de los grupos de Office 365 debe estar activada para que el acceso de invitado en los sitios de SharePoint funcione.

![Captura de pantalla de la configuración de invitados de Grupos de Office 365 en el Centro de administración de Microsoft 365](media/office-365-groups-guest-settings.png)

Para establecer la configuración de invitado de Office 365 Groups

1. En el centro de administración de Microsoft 365, en el panel de navegación de la izquierda, expanda **configuración**.
2. Haga clic en **servicios & complementos**.
3. En la lista, haga clic en **grupos de Office 365**.
4. Asegúrese de que la casilla **permitir a los miembros del grupo fuera de la organización el acceso al contenido del grupo** y **que los propietarios del grupo agreguen personas fuera de la organización a las** casillas de verificación están activadas.
5. Si ha realizado cambios, haga clic en **Guardar cambios**.


## <a name="sharepoint-organization-level-sharing-settings"></a>Configuración de uso compartido en el nivel de organización de SharePoint

Para que los invitados tengan acceso a los sitios de SharePoint, la configuración de uso compartido en el nivel de la organización de SharePoint debe permitir el uso compartido con invitados.

La configuración en el nivel de la organización determina qué opciones de configuración están disponibles para cada sitio. La configuración del sitio no puede ser más permisiva que la configuración de nivel de organización.

Si desea permitir el uso compartido de archivos y carpetas sin autenticar, elija **cualquiera**. Si desea asegurarse de que todos los usuarios ajenos a la organización tienen que autenticarse, elija los **invitados nuevos y existentes**. Elija la configuración más permisiva que necesitará cualquier sitio de la organización.

![Captura de pantalla de la configuración de uso compartido en el nivel de organización de SharePoint](media/sharepoint-organization-external-sharing-controls.png)


Para establecer la configuración de uso compartido en el nivel de la organización de SharePoint

1. En el centro de administración de Microsoft 365, en el panel de navegación izquierdo, en **centros de administración**, haga clic en **SharePoint**.
2. En el centro de administración de SharePoint, en el panel de navegación izquierdo, haga clic en **Uso compartido**.
3. Asegúrese de que el uso compartido externo para SharePoint está establecido en **todos** o en **invitados nuevos o existentes**.
4. Si ha realizado cambios, haga clic en **Guardar**.

## <a name="create-a-site"></a>Crear un sitio

El siguiente paso es crear el sitio que va a usar para colaborar con los invitados.

Para crear un sitio
1. En el centro de administración de SharePoint, en **sitios**, haga clic en **sitios activos**.
2. Haga clic en **Crear**.
3. Haga clic en **sitio de grupo**.
4. Escriba un nombre de sitio y escriba un nombre para el propietario del grupo (propietario del sitio).
5. En **Configuración avanzada**, elija si desea que sea un sitio público o privado.
6. Haga clic en **Siguiente**.
7. Haga clic en **Finalizar**.

Invitaremos a los usuarios más adelante. A continuación, es importante comprobar la configuración de uso compartido de nivel de sitio para este sitio.

## <a name="sharepoint-site-level-sharing-settings"></a>Configuración de uso compartido del nivel de sitio de SharePoint

Compruebe la configuración de uso compartido de nivel de sitio para asegurarse de que permite el tipo de acceso que desea para este sitio. Por ejemplo, si establece la configuración de nivel de organización en **cualquiera**, pero desea que todos los invitados se autentiquen en este sitio, asegúrese de que la configuración de uso compartido de nivel de sitio esté establecida en **invitados nuevos y existentes**.

Tenga en cuenta que no se puede compartir el sitio con personas no autenticadas (configuración de**cualquier persona** ), pero puede que los archivos y las carpetas individuales.

![Captura de pantalla de la configuración de uso compartido externo del sitio de SharePoint](media/sharepoint-site-external-sharing-settings.png)

Para establecer la configuración de uso compartido de nivel de sitio
1. En el Centro de administración de SharePoint, en el panel de navegación izquierdo, expanda **Sitios** y haga clic en **Sitios activos**.
2. Seleccione el sitio que acaba de crear.
3. En la cinta de opciones, haga clic en **Uso compartido**.
4. Asegúrese de que el uso compartido está establecido en **todos** o en **invitados nuevos o existentes**.
5. Si ha realizado cambios, haga clic en **Guardar**.

## <a name="invite-users"></a>Invitar a usuarios

La configuración de uso compartido de invitados ya está configurada, por lo que puede empezar a agregar invitados y usuarios internos a su sitio. El acceso al sitio se controla mediante el grupo de Office 365 asociado, por lo que vamos a agregar a los usuarios.

Para invitar a usuarios internos a un grupo
1. Navegue hasta el sitio en el que desea agregar usuarios.
2. Haga clic en **miembros** en la esquina superior derecha.
3. Haga clic en **Agregar miembros**.
4. Escriba los nombres o las direcciones de correo electrónico de los usuarios que desea invitar al sitio y, a continuación, haga clic en **Guardar**.

No se pueden agregar usuarios invitados desde el sitio. Debe agregarlos mediante Outlook en la Web.

Para invitar a invitados a un grupo
1. En Outlook en la web, en **grupos**, haga clic en el grupo al que desea agregar miembros.
2. Abra la tarjeta de contacto del grupo y, a continuación, en **más opciones** (...), haga clic en **Agregar miembros**.
3. Escriba las direcciones de correo electrónico de los invitados que desea invitar y, a continuación, haga clic en **Agregar**.
4. Haga clic en **Cerrar**.

## <a name="see-also"></a>Vea también

[Prácticas recomendadas para compartir archivos y carpetas con usuarios no autenticados](best-practices-anonymous-sharing.md)

[Reducir la exposición accidental de archivos al compartirlos con invitados](sharing-limit-accidental-exposure.md)

[Crear un entorno seguro de uso compartido para invitados](create-a-secure-guest-sharing-environment.md)

[Crear una extranet B2B con invitados administrados](b2b-extranet.md)

