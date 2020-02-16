---
title: Capacidades multigeográficas de OneDrive y SharePoint Online
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection:
- Strat_SP_gtc
- SPO_Content
localization_priority: Priority
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: Expanda la presencia de Office 365 a varias regiones geográficas con las capacidades multigeográficas de OneDrive Online.
ms.openlocfilehash: 5c3f372756a7fa160dbd322ba01ac170ca2cee26
ms.sourcegitcommit: 265cc03b600e9015a44c60c3f8bb9075b1c20888
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2020
ms.locfileid: "41973972"
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online"></a>Capacidades multigeográficas de OneDrive y SharePoint Online

Las capacidades multigeográficas de OneDrive y SharePoint Online permiten controlar el país o región donde se almacenan los recursos compartidos, como sitios de grupo de SharePoint y buzones de grupo de Office 365.

Todos los usuarios, buzones de grupo y sitios de SharePoint tienen una Ubicación de datos preferida (PDL) que indica la ubicación geográfica donde están almacenados los datos relacionados. Los datos personales de los usuarios (buzón de Exchange y OneDrive), junto con los Grupos de Office 365 o los sitios de SharePoint que creen, pueden almacenarse en la ubicación geográfica especificada para cumplir los requisitos de residencia de datos. También puede [especificar administradores diferentes para cada ubicación geográfica](add-a-sharepoint-geo-admin.md).

Los usuarios obtienen una experiencia fluida al usar los servicios de Office 365, incluidas las aplicaciones de Office, OneDrive y Search. Vea [Experiencia de usuario en un entorno multi-geográfico](multi-geo-user-experience.md) para obtener más información.

## <a name="onedrive"></a>OneDrive

El OneDrive de cada usuario lo puede aprovisionar o [mover un administrador](move-onedrive-between-geo-locations.md) a una ubicación de satélite conforme con la PDL del usuario. Los archivos personales se conservan en esa ubicación geográfica, aunque se pueden compartir con usuarios en otra ubicación geográfica.

## <a name="sharepoint-sites-and-groups"></a>Sitios y grupos de SharePoint

La administración de la característica multigeográfica está disponible en el Centro de administración de SharePoint. Encontrará información detallada en la [correspondiente entrada de blog](https://techcommunity.microsoft.com/t5/Office-365-Blog/Now-available-Multi-Geo-in-SharePoint-and-Office-365-Groups/ba-p/263302).

Cuando un usuario crea un sitio de SharePoint conectado al grupo en un entorno multigeográfico, su PDL se utiliza para determinar la ubicación geográfica donde se crean el sitio y su buzón de grupo asociado. (Si el valor de la PDL del usuario no se ha configurado o se ha establecido en una ubicación geográfica que no se ha configurado como una ubicación de satélite, el sitio y el buzón se crean en la ubicación central).

Otros servicios de Office 365 aparte de Exchange, OneDrive y SharePoint no son multigeográficos. Sin embargo, los Grupos de Office 365 creados por estos servicios estarán marcados con la PDL del creador, y su buzón de grupo de Exchange y el sitio de grupo de Office 365 SharePoint estarán aprovisionados con la ubicación geográfica correspondiente. 

## <a name="managing-the-multi-geo-environment"></a>Administrar el entorno multigeográfico

Puede configurar y administrar su entorno multigeográfico mediante el Centro de administración de SharePoint. 

![Captura de pantalla de la página de ubicaciones geográficas en el Centro de administración de SharePoint](media/sharepoint-multi-geo-admin-center.png)

(Algunas acciones, como cambiar un sitio de SharePoint o un sitio de OneDrive, requieren Microsoft PowerShell).

## <a name="see-also"></a>Vea también

[Capacidades multigeográficas en Grupos de Office 365 y SharePoint](https://techcommunity.microsoft.com/t5/Office-365-Blog/Now-available-Multi-Geo-in-SharePoint-and-Office-365-Groups/ba-p/263302)

[Administración de un entorno multigeográfico](administering-a-multi-geo-environment.md)

[Cuotas de almacenamiento de SharePoint en entornos multigeográficos](sharepoint-multi-geo-storage-quota.md)

[Administración de buzones de correo de Exchange Online en un entorno multigeográfico](administering-exchange-online-multi-geo.md)
