---
title: Procedimientos recomendados para el uso compartido anónimo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Priority
description: Obtenga más información sobre los procedimientos recomendados para compartir archivos y carpetas con usuarios anónimos
ms.openlocfilehash: f6263fe09a677094055f79a4ff38ec9d41f48898
ms.sourcegitcommit: c16ab90d0b9902228ce4337f1c64900592936cce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/23/2019
ms.locfileid: "37108408"
---
# <a name="best-practices-for-sharing-files-and-folders-with-anonymous-users"></a>Procedimientos recomendados para compartir archivos y carpetas con usuarios anónimos

El uso compartido anónimo (los vínculos para *Cualquiera*) puede ser práctico y útil en diversos escenarios. Los vínculos para *Cualquiera* son la manera más fácil de compartir: los invitados pueden abrir el vínculo sin autenticación y tienen la libertad de compartirlo con otros usuarios.

Por lo general, no todo el contenido de una organización es adecuado para el uso compartido anónimo. Este artículo describe las opciones disponibles para ayudarle a crear un entorno en el que los usuarios puedan compartir archivos y carpetas de forma anónima, pero donde existan medidas de seguridad para ayudar a proteger el contenido de su organización.

> [!NOTE]
> Para que funcione el uso compartido anónimo, debe habilitarlo para su organización y para el sitio individual o el equipo que lo utilizará. Consulte [Colaborar con personas fuera de su organización](collaborating-with-people-outside-your-organization.md) para ver el escenario que quiere habilitar.

## <a name="set-an-expiration-date-for-anyone-links"></a>Establezca una fecha de expiración de los vínculos para Cualquiera

A menudo, los archivos se almacenan en sitios, grupos y equipos durante largos períodos de tiempo. En ocasiones, hay directivas de retención de datos que requieren que se conserven archivos durante años. Si esos archivos son compartidos de forma anónima, esto podría originar un acceso inesperado y cambios en los archivos en el futuro. Para mitigar esta posibilidad, puede configurar una fecha de expiración de los vínculos para *Cualquiera*.

Una vez que el vínculo para *Cualquiera* haya expirado, ya no podrá usarse para acceder al contenido.

Establezca una fecha de expiración de los vínculos para cualquiera
1. Inicie el centro de administración de SharePoint Online.
2. En el panel de navegación izquierdo, haga clic en **Uso compartido**.
3. En la **Configuración avanzada de vínculos para "Cualquiera"**, seleccione la casilla **Los vínculos deben expirar dentro de este número de días**.</br>
   ![Captura de pantalla de la configuración de los vínculos para Cualquiera en el nivel de organización de SharePoint](media/sharepoint-organization-anyone-link-expiration.png)
4. Escriba un número de días en el cuadro y después haga clic en **Guardar**.

Tenga en cuenta que una vez que el vínculo para *Cualquiera*expire, el archivo o la carpeta se podrá volver a compartir con un nuevo vínculo para *Cualquiera*.

## <a name="set-link-permissions"></a>Establezca permisos de vínculos

De forma predeterminada, los vínculos para *Cualquiera*para un archivo permiten a los usuarios editar el archivo, mientras que los vínculos para *Cualquiera*para una carpeta permiten a los usuarios ver, editar los archivos, y cargar archivos nuevos en la carpeta. Puede cambiar estos permisos para los archivos y las carpetas independientemente de si está en modo solo vista.

Si desea permitir el uso compartido anónimo, pero le preocupa que los usuarios sin autenticación modifiquen el contenido de su organización, considere la posibilidad de configurar los permisos de archivos y carpetas al modo **Vista**.

Para establecer los permisos para vínculos anónimos
1. Inicie el centro de administración de SharePoint Online.
2. En el panel de navegación izquierdo, haga clic en **Uso compartido**.
3. En **Configuración avanzada de vínculos para "Cualquiera"**, seleccione los permisos de los archivos y carpetas que quiera usar.</br>
   ![Captura de pantalla de la configuración de permisos de los vínculos para Cualquiera en el nivel de organización de SharePoint](media/sharepoint-organization-anyone-link-permissions.png)

Con los vínculos para *Cualquiera* que se establecen en **Vista**, los usuarios pueden seguir compartiendo archivos y carpetas con los invitados y concederles permisos de edición mediante vínculos para *Personas específicas*. Estos vínculos requieren la autenticación de los invitados, y puede realizar un seguimiento de la actividad de los invitados en los archivos y carpetas compartidos con estos vínculos.

## <a name="set-default-link-type-to-only-work-for-people-in-your-organization"></a>Establezca el tipo de vínculo predeterminado para que solo funcione para las personas de su organización

Cuando *Cualquiera* está habilitado para su organización, el vínculo de uso compartido predeterminado está generalmente establecido para **Cualquiera**. Aunque esto puede resultar conveniente para los usuarios, puede aumentar el riesgo de un uso compartido anónimo involuntario. Si un usuario olvida cambiar el tipo de vínculo mientras comparte un documento confidencial, podría crear accidentalmente un vínculo de uso compartido que no requiera autenticación.

Para mitigar este riesgo, puede cambiar la configuración de vínculo predeterminado a un vínculo que solo funcione para las personas de su organización. Los usuarios que quieran compartir de forma anónima tendrían que seleccionar esa opción específicamente.

Para establecer el vínculo de uso compartido de archivos y carpetas predeterminado
1. En el centro de administración de SharePoint, en el panel de navegación izquierdo, haga clic en **Uso compartido**.
2. En **Enlaces de archivos y carpetas**, seleccione **Solo personas de la organización**.</br>
   ![Captura de pantalla de la configuración del tipo de vínculo predeterminado de SharePoint](media/sharepoint-default-sharing-link-company-link.png)
3. Haga clic en **Guardar**

## <a name="protect-against-malicious-files"></a>Protéjase contra archivos maliciosos

Cuando permite que los usuarios anónimos carguen archivos, aumenta el riesgo de que alguien cargue un archivo malintencionado. En Microsoft 365, puede usar la característica *datos adjuntos seguros* en Protección contra amenazas avanzada, para analizar automáticamente los archivos cargados y los archivos en cuarentena que se encuentren como no seguros.

Para activar los datos adjuntos seguros
1. Abra el administrador del centro de [Seguridad de Microsoft 365](https://security.microsoft.com).
2. En el panel de navegación izquierdo, haga clic en **Directivas**.
3. En **Protección contra amenazas **, haga clic en **Datos adjuntos seguros ATP (Office 365)**.
4. Seleccione la casilla **Activar ATP para SharePoint, OneDrive y Microsoft Teams** y después, haga clic en **Guardar**.</br>
   ![Captura de pantalla de la opción datos adjuntos seguros en el Centro de seguridad y cumplimiento](media/safe-attachments-setting.png)

## <a name="add-copyright-information-to-your-files"></a>Agregar información de copyright a los archivos

Si usa etiquetas de confidencialidad en el centro de administración de Cumplimiento de Microsoft 365, puede configurar las etiquetas para agregar automáticamente una marca de agua, un encabezado o un pie de página a los documentos de Office de su organización. De esta forma, puede asegurarse de que los archivos compartidos contengan derechos de autor u otra información de propiedad.

Para agregar un pie de página a un archivo con etiqueta
1. Abra el [Centro de administración de Cumplimiento de Microsoft 365](https://compliance.microsoft.com).
2. En el panel de navegación izquierdo, en **Clasificación**, haga clic en **Etiquetas de sensibilidad**.
3. Haga clic en la etiqueta que desea que agregue un pie de página y después, haga clic en **Editar etiqueta**.
4. Haga clic en la pestaña **Marcado de contenido** y después, seleccione **Activar** marcado de contenido.
5. Active la casilla de verificación del tipo de texto que desee añadir y después, haga clic en **Personalizar texto**.
6. Escriba el texto que quiere agregar a sus documentos, seleccione las opciones de texto que desee y después, haga clic en **Guardar**.</br>
   ![Captura de pantalla de la configuración de marcado de contenido para una etiqueta de sensibilidad](media/content-marking-for-anonymous-sharing.png)
7. Haga clic en **Guardar** y, después, en **Cerrar**.

Con el marcado de contenido habilitado para la etiqueta, el texto que haya especificado se agregará a los documentos de Office cuando un usuario aplique dicha etiqueta.

## <a name="see-also"></a>Vea también


[Información general de etiquetas de confidencialidad](https://docs.microsoft.com/Office365/SecurityCompliance/sensitivity-labels)

[Reducir la exposición accidental de archivos al compartirlos con invitados](sharing-limit-accidental-exposure.md)

[Crear un entorno seguro de uso compartido para invitados](create-a-secure-guest-sharing-environment.md)