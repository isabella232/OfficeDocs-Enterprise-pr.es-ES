---
title: Para obtener más información, consulte Crear una extranet de B2B con invitados administrados.
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
f1.keywords: NOCSH
description: Obtenga información sobre cómo crear un sitio o un equipo de extranet B2B con usuarios invitados administrados desde una organización asociada.
ms.openlocfilehash: cdf4470920a307d569fcfd650f40c77f4a5423a4
ms.sourcegitcommit: 4e50f43857f93f42b71650354d1aec9ed4cc7fe2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "42549069"
---
# <a name="create-a-b2b-extranet-with-managed-guests"></a>Para obtener más información, consulte Crear una extranet de B2B con invitados administrados.

Puede usar la [Administración de derechos de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/governance/entitlement-management-overview) para crear una extranet B2B para colaborar con una organización asociada que use Azure Active Directory. Esto permite a los usuarios inscribirse por sí mismos en el sitio o equipo de extranet y recibir acceso a través de un flujo de trabajo de aprobación.

Con este método de compartir recursos para colaboración, la organización asociada puede ayudarle a mantener y aprobar a los usuarios invitados en su extremo, lo que reduce la carga en el Departamento de ti y permite que los usuarios más familiarizados con el acuerdo de colaboración administren al usuario. al.

En este artículo se describen los pasos para crear un paquete de recursos (en este caso, un sitio o un equipo) que puede compartir con una organización asociada a través de un modelo de registro de acceso sin ayuda de autoservicio. 

Antes de empezar, cree el sitio o equipo que desea compartir con la organización asociada y habilítelo para compartir el invitado. Consulte [colaborar con invitados en un sitio](collaborate-in-a-site.md) o [colaborar con los invitados en un equipo](collaborate-as-a-team.md) para obtener más información. También le recomendamos que revise [crear un entorno seguro de uso compartido de invitados](create-a-secure-guest-sharing-environment.md) para obtener información sobre las características de seguridad y cumplimiento que puede usar para ayudar a mantener sus directivas de gobierno al colaborar con invitados.

## <a name="connect-the-partner-organization"></a>Conexión de la organización asociada

Para invitar a invitados de una organización asociada, debe agregar el dominio del asociado como una organización conectada en Azure Active Directory.

Para agregar una organización conectada
1. En [Azure Active Directory](https://aad.portal.azure.com), haga clic en **gobierno de identidades**.
2. Haga clic en **organizaciones conectadas**.
4. Haga clic en **Agregar organización conectada**.
5. Escriba un nombre y una descripción para la organización y, a continuación, haga clic en **siguiente: Directory + Domain**.
6. Haga clic en **Agregar directorio + dominio**.
7. Escriba el dominio de la organización a la que desea conectarse y, a continuación, haga clic en **Agregar**.
8. Haga clic en **conectar**y, a continuación, haga clic en **siguiente: patrocinadores**.
9. Agregue personas de su organización o de la organización a la que se va a conectar a quién desea aprobar el acceso para los usuarios invitados.
10. Haga clic en **siguiente: revisión + crear**.
11. Revise la configuración que eligió y, a continuación, haga clic en **crear**.

    ![Captura de pantalla de la página organizaciones conectadas en Azure Active Directory](media/identity-governance-connected-organizations.png)

## <a name="choose-the-resources-to-share"></a>Elegir los recursos que se van a compartir

El primer paso para seleccionar recursos para compartir con una organización asociada es crear un catálogo que los contenga.

Para crear un catálogo
1. En [Azure Active Directory](https://aad.portal.azure.com), haga clic en **gobierno de identidades**.
2. Haga clic en **catálogos**.
3. Haga clic en **nuevo catálogo**.
4. Escriba un nombre y una descripción para el catálogo y asegúrese de que estén **habilitados** y habilitados **para los usuarios externos** establecidos en **sí**.
5. Haga clic en **Crear**.

   ![Captura de pantalla de la página de catálogos en el gobierno de identidad de Azure Active Directory](media/identity-governance-catalogs.png)

Una vez creado el catálogo, agregue el sitio o equipo de SharePoint que desea compartir con la organización asociada.

Para agregar recursos a un catálogo
1. En el gobierno de identidad de Azure AD, haga clic en **catálogos**y, a continuación, haga clic en el catálogo en el que desea agregar recursos.
2. Haga clic en **recursos** y, a continuación, en **Agregar recursos**.
3. Seleccione los equipos o sitios de SharePoint que desea incluir en la extranet y, a continuación, haga clic en **Agregar**.

   ![Captura de pantalla de la página de recursos del catálogo en el gobierno de identidad de Azure Active Directory](media/identity-governance-catalog-resource.png)

Una vez que haya definido los recursos que desea compartir, el siguiente paso consiste en crear un paquete de acceso, que define el tipo de acceso que se concede a los usuarios asociados y el proceso de aprobación para los nuevos usuarios asociados que solicitan acceso.

Para crear un paquete de Access
1. En el gobierno de identidad de Azure AD, haga clic en **catálogos**y, a continuación, haga clic en el catálogo en el que desea crear un paquete de acceso.
2. Haga clic en **paquetes de Access**y, a continuación, en **nuevo paquete de acceso**.
3. Escriba un nombre y una descripción para el paquete de Access y, a continuación, haga clic en **siguiente: roles de recursos**.
4. Elija los recursos del catálogo que desea usar para la extranet.
5. Para cada recurso, en la columna **rol** , elija el rol de usuario que desea conceder a los usuarios invitados que usan la extranet.
6. Haga clic en **siguiente: solicitudes**.
7. En **usuarios que pueden solicitar acceso**, elija **para los usuarios que no están en el directorio**.
8. Asegúrese de que la opción **organizaciones conectadas específicas** está seleccionada y, a continuación, haga clic en **Agregar directorios**.
9. Elige la organización conectada que agregaste anteriormente y, a continuación, haz clic en **seleccionar**
10. En **aprobación**, elija **sí** para **requerir aprobación**.
11. En **primer aprobador**, elija uno de los patrocinadores que agregó anteriormente o elija un usuario específico.
12. Haga clic en **Agregar suplencia** y seleccione un aprobador de reserva.
13. En **Habilitar**, elija **sí**.
14. Haga clic en **siguiente: ciclo de vida**.
15. Elija la configuración de caducidad y revisión de Access que desea usar y, a continuación, haga clic en **siguiente: revisión + crear**.
16. Revise la configuración y, a continuación, haga clic en **crear**.

    ![Captura de pantalla de la pantalla de paquetes de acceso en el gobierno de identidad de Azure Active Directory](media/identity-governance-access-packages.png)

Si está asociando con una organización de gran tamaño, es posible que quiera ocultar el paquete de Access. Si el paquete está oculto, los usuarios de la organización asociada no podrán ver el paquete en su portal de *acceso* . En su lugar, se deben enviar a un vínculo directo para registrarse en el paquete. Ocultar el paquete de acceso puede reducir el número de solicitudes de acceso inadecuadas y también puede ayudar a mantener los paquetes de acceso disponibles en el portal de la organización asociada.

Para establecer un paquete de Access en oculto
1. En Azure AD control de identidad, haga clic en **paquetes de acceso**y, después, haga clic en el paquete de acceso.
2. En la página **información general** , haga clic en **Editar**.
3. En **propiedades**, elija **sí** para **ocultar**y, a continuación, haga clic en **Guardar**.

   ![Captura de pantalla de una pantalla Editar propiedades del paquete de Access](media/identity-governance-access-package-hidden.png)

## <a name="invite-partner-users"></a>Invitar a usuarios asociados

Si establece el paquete de Access en oculto, deberá enviar un vínculo directo a la organización asociada para que pueda solicitar acceso a su sitio o equipo.

Para buscar el vínculo del portal de Access
1. En Azure AD control de identidad, haga clic en **paquetes de acceso**y, después, haga clic en el paquete de acceso.
2. En la página **información general** , haga clic en el vínculo **copiar al portapapeles** del **vínculo del portal de acceso**.

   ![Captura de pantalla de las propiedades del paquete de Access con el vínculo del portal de Access](media/identity-governance-access-portal-link.png)

Una vez que haya copiado el vínculo, puede compartirlo con su contacto en la organización asociada y puede enviarlo a los usuarios de su equipo de colaboración.

## <a name="see-also"></a>Vea también

[Crear un entorno seguro de uso compartido para invitados](create-a-secure-guest-sharing-environment.md)

