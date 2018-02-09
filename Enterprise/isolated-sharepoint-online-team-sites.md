---
title: Sitios de equipo de SharePoint Online aislados
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: 71250a04-fd2d-4c3c-a32b-b8a838b19a54
description: 'Resumen: Conozca los usos de los sitios de grupo de SharePoint Online aislados.'
ms.openlocfilehash: 907959e1ad693e710a2a84d0bd0ffd0804ac3ddf
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="isolated-sharepoint-online-team-sites"></a>Sitios de equipo de SharePoint Online aislados

 **Resumen:** Obtenga información sobre los usos de los sitios de grupo de SharePoint Online aislados.
  
Sitios de equipo de SharePoint Online son una manera fácil de crear rápidamente un espacio de colaboración de notas, documentos, artículos, un calendario y otros recursos de Microsoft Office 365. Sitios de equipo de SharePoint Online están basados en un grupo de Office 365 y tienen un modelo de administración simplificada para permitir una colaboración abierta con un conjunto privado de los miembros del grupo o de toda la organización. Un sitio de grupo de SharePoint Online predeterminada permite a los miembros del grupo Office 365 invitar a otros usuarios y controlar la configuración de permisos.
  
Sin embargo, en algunos casos, desea crear un sitio de grupo SharePoint Online para colaboración donde los permisos de ese sitio están controlados más estrechamente a través de la pertenencia a grupos y niveles de permisos SharePoint Online, que sólo son administrados por SharePoint administradores. Llamamos a esto un sitio aislado, que se aísla en el conjunto de usuarios que están colaborando, ver su contenido o administrar el sitio. Puede que necesite un sitio aislado para lo siguiente:
  
- Un proyecto secreto dentro de su organización.
    
- Ubicación muy importantes o valiosa propiedad intelectual de su organización.
    
- Los recursos para una acción legal tomada por la organización o a la que se ve sometido.
    
- Compartir una suscripción a Office 365 entre varias organizaciones que dispone de algunos se superponen, pero la mayor parte existen como entidades de negocio independientes.
    
Aquí están los requisitos de un sitio aislado:
  
- Sólo los administradores de SharePoint Online pueden realizar la administración del sitio, que incluye la pertenencia al grupo de acceso al sitio y la configuración de permisos personalizados.
    
- Los miembros del sitio no pueden invitar a otros miembros al sitio del grupo.
    
- Los usuarios que no son miembros del sitio aislado no pueden solicitar acceso al sitio. Recibirán un acceso denegado página web cuando intentan tener acceso a cualquier dirección URL asociada con el sitio.
    
La desventaja de que requieren permisos personalizados por los administradores de SharePoint Online y control de acceso centralizado es que el sitio permanece aislado en el tiempo. Por ejemplo, miembros actuales no pueden, ya sea intencionada o accidentalmente, invitar o configurar permisos personalizados a otros usuarios de la suscripción de Office 365 que no sean miembros del sitio.
  
Un sitio aislado puede utilizarse con otras características, tales como:
  
- Information Rights Management para asegurar que los recursos en el sitio permanecen cifrados, incluso si se descargan localmente y cargar a otro sitio que esté disponible para toda la organización.
    
- Prevención de pérdida de datos para evitar que los usuarios envíen los recursos del sitio, como los archivos de correo electrónico.
    
## <a name="next-steps"></a>Pasos siguientes

Para probar un sitio de grupo de SharePoint Online aislado en una suscripción de prueba, consulte las instrucciones paso a paso en el [entorno de pruebas y desarrollo de sitio de equipo aislado de SharePoint Online](isolated-sharepoint-online-team-site-dev-test-environment.md).
  
Cuando esté listo para implementar un sitio de equipo de SharePoint Online aislado de producción, consulte las consideraciones de diseño paso a paso en el [Diseño de un sitio de grupo SharePoint Online aislado](design-an-isolated-sharepoint-online-team-site.md).
  
## <a name="see-also"></a>Consulte también

[Diseñar un sitio de grupo SharePoint Online aislado](design-an-isolated-sharepoint-online-team-site.md)
  
[Administrar un sitio de grupo SharePoint Online aislado](manage-an-isolated-sharepoint-online-team-site.md)
  
[Soluciones de seguridad](security-solutions.md)

[Implementar un sitio de grupo SharePoint Online aislado](deploy-an-isolated-sharepoint-online-team-site.md)


