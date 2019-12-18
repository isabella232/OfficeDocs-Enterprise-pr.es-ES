---
title: Colaborar con invitados en un equipo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
description: Obtenga información sobre cómo colaborar con invitados en Microsoft Teams.
ms.openlocfilehash: 2743b1062aebf5e8fbc1db191fcf36f4091bc1f3
ms.sourcegitcommit: f18f75dba4cbec557fa094bd1cebd8c5cc4752c1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/17/2019
ms.locfileid: "40085205"
---
# <a name="collaborate-with-guests-in-a-team"></a>Colaborar con invitados en un equipo

Si necesita colaborar con invitados en documentos, tareas y conversaciones, le recomendamos que use Microsoft Teams. Teams ofrece todas las características de colaboración disponibles en Office y SharePoint con chat persistente y un conjunto de herramientas de colaboración personalizable y extensible en una experiencia de usuario unificada.

En este artículo, analizaremos los pasos de configuración de Microsoft 365 necesarios para configurar un equipo para la colaboración con los invitados.

## <a name="video-demonstration"></a>Vídeo de demostración

En este vídeo se muestran los pasos de configuración que se describen en este documento.</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE44NTr?autoplay=false]

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

## <a name="teams-guest-access-settings"></a>Configuración de acceso de invitado de Microsoft Teams

Los equipos tienen un conmutador de encendido y apagado principal para el acceso de invitado y una variedad de opciones de configuración disponibles para controlar lo que pueden hacer los invitados en un equipo. El conmutador maestro, **permitir el acceso de invitado en Microsoft Teams** , debe estar **activado** para que el acceso de invitado trabaje en Microsoft Teams.

Asegúrese de que el acceso de invitado esté habilitado en Microsoft Teams y realice cualquier ajuste en la configuración de invitado en función de las necesidades de su empresa. Tenga en cuenta que esta configuración afecta a todos los equipos.

![Captura de pantalla de la opción de acceso de invitado de Teams](media/teams-guest-access-toggle-on.png)

Para establecer la configuración de acceso de invitado de Teams

1. Inicie sesión en el centro de administración de Microsoft [https://admin.microsoft.com](https://admin.microsoft.com)365 en.
2. En el panel de navegación izquierdo, haga clic en **Mostrar todo**.
3. En **centros de administración**, haga clic en **Teams**.
4. En el centro de administración de Teams, en el panel de navegación de la izquierda, expanda **configuración de toda la organización** y haga clic en **acceso de invitado**.
5. Asegúrese de que la **opción permitir el acceso de invitado en Microsoft Teams** está **activada**.
6. Realice los cambios que desee en la configuración de invitado adicional y, a continuación, haga clic en **Guardar**.

> [!NOTE]
> La configuración del invitado de Teams puede tardar hasta 24 horas en activa una vez que la activa.

## <a name="office-365-groups-guest-settings"></a>Configuración de invitado de Office 365 Groups

Microsoft Teams usa los grupos de Office 365 para la pertenencia al equipo. La configuración de invitado de los grupos de Office 365 debe estar activada para que el acceso de invitado en Microsoft Teams funcione.

![Captura de pantalla de la configuración de invitados de Grupos de Office 365 en el Centro de administración de Microsoft 365](media/office-365-groups-guest-settings.png)

Para establecer la configuración de invitado de Office 365 Groups

1. En el centro de administración de Microsoft 365, en el panel de navegación de la izquierda, expanda **configuración**.
2. Haga clic en **servicios & complementos**.
3. En la lista, haga clic en **grupos de Office 365**.
4. Asegúrese de que la casilla **permitir a los miembros del grupo fuera de la organización el acceso al contenido del grupo** y **que los propietarios del grupo agreguen personas fuera de la organización a las** casillas de verificación están activadas.
5. Si ha realizado cambios, haga clic en **Guardar cambios**.


## <a name="sharepoint-organization-level-sharing-settings"></a>Configuración de uso compartido en el nivel de organización de SharePoint

El contenido de Microsoft Teams, como archivos, carpetas y listas, se almacena en SharePoint. Para que los invitados tengan acceso a estos elementos en Microsoft Teams, la configuración de uso compartido en el nivel de la organización de SharePoint debe permitir el uso compartido con invitados.

La configuración en el nivel de la organización determina qué opciones de configuración están disponibles para cada uno de los sitios, incluidos los sitios asociados a teams. La configuración del sitio no puede ser más permisiva que la configuración de nivel de organización.

Si desea permitir el uso compartido de archivos y carpetas con personas sin autenticar, elija **cualquiera**. Si desea asegurarse de que todos los invitados tienen que autenticarse, elija los **invitados nuevos y existentes**. Elija la configuración más permisiva que necesitará cualquier sitio de la organización.

![Captura de pantalla de la configuración de uso compartido en el nivel de organización de SharePoint](media/sharepoint-organization-external-sharing-controls.png)


Para establecer la configuración de uso compartido en el nivel de la organización de SharePoint

1. En el centro de administración de Microsoft 365, en el panel de navegación izquierdo, en **centros de administración**, haga clic en **SharePoint**.
2. En el centro de administración de SharePoint, en el panel de navegación izquierdo, haga clic en **Uso compartido**.
3. Asegúrese de que el uso compartido externo para SharePoint está establecido en **todos** o en **invitados nuevos o existentes**.
4. Si ha realizado cambios, haga clic en **Guardar**.


## <a name="sharepoint-organization-level-default-link-settings"></a>Configuración de vínculos predeterminados de nivel de organización de SharePoint

La configuración predeterminada de los vínculos de archivos y carpetas determina qué opción de vínculo se muestra al usuario de forma predeterminada cuando comparte un archivo o una carpeta. Los usuarios pueden cambiar el tipo de vínculo a una de las otras opciones antes de compartirlo, si lo desea.

Tenga en cuenta que esta configuración afecta a todos los equipos y sitios de SharePoint de la organización.

Elija el tipo de vínculo que está seleccionado de forma predeterminada cuando los usuarios comparten archivos y carpetas:

- **Cualquiera que tenga el vínculo** : elija esta opción si tiene previsto compartir de forma considerable archivos y carpetas sin autenticar. Si desea permitir que *todos* los vínculos, pero le preocupa el uso compartido no autenticado accidentalmente, considere una de las otras opciones como predeterminada. Este tipo de vínculo solo está disponible si ha habilitado a **todos los usuarios** que comparten el mismo.
- **Solo las personas de su organización** : elija esta opción si prevé que la mayoría del uso compartido de archivos y carpetas sea para personas dentro de la organización.
- **Personas específicas** : considere esta opción si espera compartir muchos archivos y carpetas con los invitados. Este tipo de vínculo funciona con los invitados y requiere que se autentiquen.
 
![Captura de pantalla de la configuración de uso compartido de los archivos y carpetas de nivel de organización de SharePoint ](media/sharepoint-organization-files-folders-sharing-settings.png)


Para establecer la configuración de vínculos predeterminados de nivel de organización de SharePoint

1. Vaya a la página de uso compartido en el centro de administración de SharePoint.
2. En **vínculos de archivos y carpetas**, seleccione el vínculo de uso compartido predeterminado que desee usar.
3. Si ha realizado cambios, haga clic en **Guardar**.

## <a name="create-a-team"></a>Crear un equipo

El siguiente paso es crear el equipo que planea usar para colaborar con invitados.

Para crear un equipo
1. En Microsoft Teams, en **la pestaña Microsoft Teams** , haga clic en **unirse o en crear un equipo** en la parte inferior del panel izquierdo.
2. Haga clic en **crear un equipo**.
3. Haga clic en **crear un equipo desde cero**.
4. Elija **privado** o **público**.
5. Escriba un nombre y una descripción para el equipo y, a continuación, haga clic en **crear**.
6. Haga clic en **omitir**.

Invitaremos a los usuarios más adelante. A continuación, es importante comprobar la configuración de uso compartido de nivel de sitio para el sitio de SharePoint asociado al equipo.

## <a name="sharepoint-site-level-sharing-settings"></a>Configuración de uso compartido del nivel de sitio de SharePoint

Compruebe la configuración de uso compartido de nivel de sitio para asegurarse de que permite el tipo de acceso que desea para este equipo. Por ejemplo, si establece la configuración en el nivel de la organización en **cualquiera**, pero desea que todos los invitados se autentiquen para este equipo, asegúrese de que la configuración de uso compartido de nivel de sitio esté establecida en **invitados nuevos y existentes**.

![Captura de pantalla de la configuración de uso compartido externo del sitio de SharePoint](media/sharepoint-site-external-sharing-settings.png)


Para establecer la configuración de uso compartido de nivel de sitio
1. En el Centro de administración de SharePoint, en el panel de navegación izquierdo, expanda **Sitios** y haga clic en **Sitios activos**.
2. Seleccione el sitio para el equipo recién creado.
3. En la cinta de opciones, haga clic en **Uso compartido**.
4. Asegúrese de que el uso compartido está establecido en **todos** o en **invitados nuevos o existentes**.
5. Si ha realizado cambios, haga clic en **Guardar**.

## <a name="invite-users"></a>Invitar a usuarios

La configuración de uso compartido de invitados ya está configurada, por lo que puede empezar a agregar invitados y usuarios internos a su equipo. 

Para invitar a usuarios internos a un equipo
1. En el equipo, haga clic en **más opciones** (**\*\***) y, a continuación, haga clic en **Agregar miembro**.
2. Escriba el nombre de la persona a la que desea invitar.
3. Haga clic en **Agregar** y, después, en **Cerrar**.

Para invitar a invitados a un equipo
1. En el equipo, haga clic en **más opciones** (**\*\***) y, a continuación, haga clic en **Agregar miembro**.
2. Escriba la dirección de correo electrónico del invitado al que desea invitar.
3. Haga clic en **editar información de invitado**.
4. Escriba el nombre completo del invitado y haga clic en la marca de verificación.
5. Haga clic en **Agregar** y, después, en **Cerrar**.

## <a name="see-also"></a>Vea también

[Prácticas recomendadas para compartir archivos y carpetas con usuarios no autenticados](best-practices-anonymous-sharing.md)

[Reducir la exposición accidental de archivos al compartirlos con invitados](sharing-limit-accidental-exposure.md)

[Crear un entorno de uso compartido de invitado seguro](create-a-secure-guest-sharing-environment.md))

[Crear una extranet B2B con invitados administrados](b2b-extranet.md)
