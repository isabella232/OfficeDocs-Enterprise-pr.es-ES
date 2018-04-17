---
title: Capacidades de Multi-Geo en OneDrive y SharePoint Online en Office 365
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: Expandir su presencia en Office 365 para varias regiones geográficas con capacidades de multi-geo en OneDrive y SharePoint Online.
ms.openlocfilehash: 2c5de533aaaace68e51b747cd62a53b9572bcaec
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365"></a>Capacidades de Multi-Geo en OneDrive y SharePoint Online en Office 365

Con multi-geo las capacidades de OneDrive y SharePoint Online, su organización puede expandir su presencia en Office 365 a múltiples regiones geográficas o países en su arrendatario existente. Esta característica está actualmente en la vista previa. Llegar a su equipo de cuentas de Microsoft para suscribirse a su empresa multinacional para la previsualización de OneDrive Multi-Geo.
  
Con OneDrive Multi-Geo, puede aprovisionar y almacenar los datos en reposo en las ubicaciones geo que ha elegido para satisfacer los requisitos de residencia de los datos y al mismo tiempo desbloquear su implementación global de experiencias de productividad moderna a los empleados.
  
Le mostramos cómo características multi-geo pueden beneficiar a su organización:
  
- Funcionar como una organización conectada global con un único inquilino de Office 365 que abarcan varias ubicaciones geo.
    
- Cumplir los requisitos de residencia de datos mediante la creación y alojamiento de datos en reposo dentro de una ubicación geográfica especificada.
    
- Equipe a sus usuarios de satélite con las mismas experiencias de productividad moderna disfrutadas los usuarios de una ubicación central.
    
- Permitir a los usuarios mover entre geo ubicaciones como sus cambios de funciones, mientras que el acceso a su contenido se mantiene intacto.
    
- Adaptar las directivas de uso compartidas por ubicación geográfica y las políticas de prevención de pérdida de datos por cada sitio.
    
- Designar administradores por ubicación geográfica de eDiscovery y permitir que regulan casos adaptados a su ubicación geográfica.
    
- Elegir espacios de nombres únicos de dirección URL (por ejemplo, ContosoEUR.sharepoint.com) para las ubicaciones geo adicionales.
    
- Consolidar los datos de instalaciones regionales a los inquilinos de multi-geo Office 365.
    
En una configuración multi-geo, el arrendatario Office 365 consiste en una ubicación central (también conocida como la ubicación predeterminada) y una o más ubicaciones de geo de satélite. El concepto clave de multi-geo es que un único contrato de arrendamiento abarcar uno varias ubicaciones geo. En un arrendatario multi-geo, la información acerca de la información de usuario, grupos y ubicaciones geo se domina en Azure Active Directory (DAA). Porque la información del arrendatario es domina centralmente y sincronizado en cada ubicación geográfica, compartir y experiencias que implican cualquier persona de la compañía contienen conocimiento global.
  
## <a name="sample-multi-geo-tenant-configuration"></a>Ejemplo de configuración de inquilinos multi-geo

Utilizando un arrendatario multi-geo, Contoso, con una ubicación central de América del Norte, puede expandir a satélite geo ubicaciones en Europa y Australia bajo el paraguas de organización único de Contoso.com. Los usuarios con su ubicación preferida de datos establecido en Europa tendrán su OneDrive en Europa mientras que los usuarios con su ubicación de datos preferido en América del Norte tendrá su OneDrive en los Estados Unidos.
  
![Mapa del mundo, mostrando geo ubicaciones de Contoso y otras ubicaciones disponibles geo](images/df317ccc-2e53-411d-9211-a5aee63ca1e5.png)
  
## <a name="get-multi-geo-features-in-three-simple-steps"></a>Obtener características de multi-geo en tres sencillos pasos

Es fácil configurar multi-geo:
  
1. Trabaje con su equipo de cuenta para agregar el plan de servicio _Multi-Geo capacidades de Office 365_ . Servirán de guía para agregar el número de licencias necesarias.
    
2. Agregar las ubicaciones de satélite.
    
3. Configurar las cuentas de usuario para la ubicación adecuada.
    
## <a name="multi-geo-status-and-availability"></a>Disponibilidad y estado de Multi-Geo

OneDrive Multi-Geo se ofrece actualmente en estos países y regiones:
  
- Asia y Pacífico
    
- Australia
    
- Canadá
    
- Unión Europea (EMEA)
    
- Japón
    
- Reino Unido
    
- Estados Unidos (Norteamérica)
    
- Corea
      
Ubicaciones próximas geo:
  
- Francia
- India
    
## <a name="getting-started"></a>Introducción

Para comenzar con la OneDrive de negocios Multi-Geo, el primer paso es planificar [la OneDrive para el entorno de negocios Multi-Geo](plan-for-multi-geo.md). Siguiente, [Obtenga información acerca de cómo administrar un entorno multi-geo](administering-a-multi-geo-environment.md) y [cómo los usuarios experimentarán un entorno multi-geo](multi-geo-user-experience.md). Cuando esté listo para configurar OneDrive para negocios Multi-Geo, [Configurar el arrendatario para multi-geo](multi-geo-tenant-configuration.md), a continuación, [mover los sitios OneDrive a sus nuevas ubicaciones de geo](move-onedrive-between-geo-locations.md) y [Configurar la búsqueda](configure-search-for-multi-geo.md).
