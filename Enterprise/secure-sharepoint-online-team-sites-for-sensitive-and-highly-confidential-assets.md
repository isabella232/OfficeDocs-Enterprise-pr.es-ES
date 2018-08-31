---
title: Proteger los sitios de grupo de SharePoint Online para los activos confidenciales y altamente confidenciales
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 8c088e88-a9ba-4044-bced-722196f4496d
description: 'Resumen: Cómo Contoso implementa protección confidencial y sitios de grupo de SharePoint Online altamente confidenciales para sea más fácil, aún seguro, sus centros de investigación y colaboración para los ejecutivos.'
ms.openlocfilehash: 23511e4156bb04e8bacf970913b00ed36e8ff9c8
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914865"
---
# <a name="secure-sharepoint-online-team-sites-for-sensitive-and-highly-confidential-assets"></a>Proteger los sitios de grupo de SharePoint Online para los activos confidenciales y altamente confidenciales

 **Resumen:** Cómo Contoso implementada confidencial protección y altamente confidencial SharePoint Online sitios para la colaboración sea más fácil, pero seguro, para los ejecutivos y sus centros de investigación de equipo.
  
El liderazgo ejecutivo de Contoso se vaya a usar Office 365 y almacenar sus archivos en una sola ubicación para la colaboración, independientemente de donde podría ser un ejecutivo. De forma similar, los departamentos de investigación de Contoso, con divisiones de París, Moscú, Nueva York, Beijing y Bangalore — que le gustaría realizar la transición de sus activos digitales de local a la nube de acceso más fácil y más susceptible de colaboración entre los equipos.
  
Sin embargo, en ambos casos, acceso a estos recursos debe estar restringido al subconjunto de personas que tienen permiso para ver o cambiar a ellas, con permisos de curso para los sitios administrados por el personal de TI. Además, incluso si algunos recursos intencionada o no distribuido, deben estar cifradas y tengan permisos para evitar que los usuarios que no tienen acceso para ver o cambiar su contenido.
  
Los administradores de seguridad y SharePoint en Contoso del departamento de TI decidido utilizar protección confidencial y sitios de grupo de SharePoint Online altamente confidencial, tal como se muestra en la figura 1.
  
**En la figura 1: Comparación de protección confidencial y sitios de grupo de SharePoint Online altamente confidenciales**

![Protección de información confidencial y sitios de grupo de SharePoint Online muy confidenciales](media/Contoso-Poster/SP-Solution.png)
  
Contoso utiliza estos pasos para crear sitios de equipo de SharePoint Online seguros para sus los ejecutivos y equipos de investigación:
  
1. Crear un sitio de grupo de SharePoint Online confidencial **ejecutivos**
    
    El nuevo sitio de grupo usa grupos de Azure Active Directory (AD) existente para los ejecutivos como miembros con el nivel de permisos de edición de SharePoint y un pequeño conjunto de cuentas de administrador de SharePoint como propietarios con el nivel de permiso Control total.
    
2. Migración de archivos de los ejecutivos
    
    Mover local ejecutivo archivos y carpetas existentes para el nuevo sitio de grupo ejecutivos SharePoint Online.
    
3. Crear un sitio de grupo de SharePoint Online altamente confidencial **investigación**
    
    El nuevo sitio de grupo usa grupos de equipo de investigación de Azure AD existentes como miembros con el nivel de permiso de edición y un pequeño conjunto de cuentas de administrador de SharePoint como propietarios con el nivel de permiso Control total. Una etiqueta AIP asignada a los archivos de la investigación se asegura de que están cifrados y sólo los miembros de un grupo de investigación pueden abrirlos.
    
4. Migración de archivos de investigación
    
    Mover el equipo existente de investigación local archivos y carpetas para el nuevo sitio de grupo investigación SharePoint Online.
    
El resultado es dos sitios de colaboración cuyo acceso se controla de forma estricta, seguridad y los administradores de SharePoint. Para los archivos con la etiqueta altamente confidencial AIP, incluso si se distribuyen fuera del sitio del equipo de investigación, que se cifran y sólo se pueden abrir mediante un miembro de un equipo de investigación.
  
Para obtener más información, vea [archivos y sitios de SharePoint Online seguro](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-and-files).
  
 Para definir esta opción para pruebas y desarrollo, prueba de concepto o demostración, vea [sitios de SharePoint Online seguro en un entorno de desarrollo o prueba](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-dev-test).
  
## <a name="see-also"></a>Vea también

[Escenarios empresariales para Contoso Corporation](enterprise-scenarios-for-the-contoso-corporation.md)
  
[Contoso en la nube de Microsoft](contoso-in-the-microsoft-cloud.md)
  
[Recursos de arquitectura de TI de la nube de Microsoft](microsoft-cloud-it-architecture-resources.md)

[Stretch Database](https://msdn.microsoft.com/library/dn935011.aspx)
  
[Mapa de ruta de Enterprise Cloud de Microsoft: Recursos para los responsables de la toma de decisiones de TI](https://sway.com/FJ2xsyWtkJc2taRD)




