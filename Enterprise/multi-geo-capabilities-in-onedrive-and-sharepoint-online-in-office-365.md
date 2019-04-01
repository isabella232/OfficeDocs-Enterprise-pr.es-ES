---
title: Capacidades multigeográficas de OneDrive y SharePoint Online
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: Expanda la presencia de Office 365 a varias regiones geográficas con las capacidades multigeográficas de OneDrive Online.
ms.openlocfilehash: 15dcb44943fa1bf331ef6260946f7c3a632d3c4a
ms.sourcegitcommit: dffbcfb1cbc9776a29229a787c1eab4192e55cff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/28/2019
ms.locfileid: "30948591"
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online"></a>Capacidades multigeográficas de OneDrive y SharePoint Online

Las capacidades multigeográficas de OneDrive y SharePoint Online permiten controlar el país o región donde se almacenan los recursos compartidos, como sitios de grupo de SharePoint y buzones de grupo de Office 365.

Todos los usuarios, buzones de grupo y sitios de SharePoint tienen una Ubicación de datos preferida (PDL) que indica la ubicación geográfica donde están almacenados los datos relacionados. Los datos personales de los usuarios (buzón de Exchange y OneDrive), junto con los Grupos de Office 365 o los sitios de SharePoint que creen, pueden almacenarse en la ubicación geográfica especificada para cumplir los requisitos de residencia de datos. También puede [especificar administradores diferentes para cada ubicación geográfica](add-a-sharepoint-geo-admin.md).

Los usuarios obtienen una experiencia fluida al usar los servicios de Office 365, incluidas las aplicaciones de Office, OneDrive y Search. Vea [Experiencia de usuario en un entorno multi-geográfico](multi-geo-user-experience.md) para obtener más información.

## <a name="onedrive"></a>OneDrive

El OneDrive de cada usuario lo puede aprovisionar o [mover un administrador](move-onedrive-between-geo-locations.md) a una ubicación de satélite conforme con la PDL del usuario. Los archivos personales se conservan en esa ubicación geográfica, aunque se pueden compartir con usuarios en otra ubicación geográfica.

## <a name="sites-and-groups"></a>Equipos y grupos

Cuando un usuario crea un sitio de SharePoint conectado al grupo, su PDL se utiliza para determinar la ubicación geográfica donde se crean el sitio y su buzón de grupo asociado. (Si el valor de la PDL del usuario no se ha configurado o se ha establecido en una ubicación geográfica que no se ha configurado como una ubicación de satélite, el sitio y el buzón se crean en la ubicación central).

Otros servicios de Office 365 aparte de Exchange, OneDrive y SharePoint no son multigeográficos. Sin embargo, los Grupos de Office 365 creados por estos servicios estarán marcados con la PDL del creador, y su buzón de grupo de Exchange y el sitio de grupo de Office 365 SharePoint estarán aprovisionados con la ubicación geográfica correspondiente. 

## <a name="managing-the-multi-geo-environment"></a>Administrar el entorno multigeográfico

Puede configurar y administrar su entorno multigeográfico mediante el Centro de administración de SharePoint. 

![Captura de pantalla de la página de ubicaciones geográficas en el Centro de administración de SharePoint](media/sharepoint-multi-geo-admin-center.png)

(Algunas acciones, como cambiar un sitio de SharePoint o un sitio de OneDrive, requieren Microsoft PowerShell).

## <a name="see-also"></a>Vea también

[Aka.ms/GetMultiGeo ](https://Aka.ms/GetMultiGeo)

[Administración de un entorno multigeográfico](administering-a-multi-geo-environment.md)

[Cuotas de almacenamiento de SharePoint en entornos multigeográficos](sharepoint-multi-geo-storage-quota.md)

[Administración de buzones de correo de Exchange Online en un entorno multigeográfico](administering-exchange-online-multi-geo.md)
