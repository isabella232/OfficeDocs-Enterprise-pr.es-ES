---
title: Habilitar SharePoint Multi-Geo en su ubicación geográfica de satélite
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
description: Habilitar SharePoint Multi-Geo en su ubicación geográfica de satélite.
ms.openlocfilehash: f5f7137f64f26ce324894ee80b5dfb2f46888889
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2020
ms.locfileid: "41848775"
---
# <a name="enabling-sharepoint-multi-geo-in-your-satellite-geo-location"></a>Habilitar SharePoint Multi-Geo en su ubicación geográfica de satélite

Este artículo es para los administradores globales o de SharePoint que crearon una ubicación de satélite multigeográfica **antes** de que las funcionalidades multigeográficas de SharePoint estuvieran disponibles el 27 de marzo de 2019 y que no hayan habilitado SharePoint Multi-Geo en sus ubicaciones geográficas de satélite. 

>[!Note]
>Si ha agregado una nueva ubicación geográfica **después el 27 de marzo**, no es necesario realizar estas acciones, ya que la nueva ubicación geográfica ya estará habilitada para OneDrive y SharePoint Multi-Geo.

Estas instrucciones le permitirán habilitar SharePoint en la ubicación de satélite, por lo que los usuarios del satélite multigeográfico pueden aprovechar las funcionalidades de OneDrive y SharePoint Multi-Geo en Office 365. 

>[!IMPORTANT]
>Tenga en cuenta que esta es una activación unidireccional. Una vez que establezca el modo SPO, no podrá revertir el inquilino al modo de solo OneDrive Multi-Geo sin consultar con el soporte técnico. 

## <a name="to-set-a-geo-location-into-spo-mode"></a>Establecer una ubicación geográfica en modo SPO

Para establecer una ubicación geográfica en modo SPO, conéctese a la ubicación geográfica que desea establecer en modo de SPO:

1.  Abra el Shell de administración de SharePoint Online 
2.  Connect-SPOService -URL "https://$tenantGeo-admin.sharepoint.com" -Credential $credential
3.  Set-SPOMultiGeoExperience</br></br>
![Set-SPOMultiGeoExperience](media/Set-SPO-MultiGeo.jpg)
4.  Esta operación suele tardar aproximadamente una hora mientras se realizan varias acciones en el servicio y se vuelve a marcar el inquilino. Después de al menos una hora, lleve a cabo un Get-SPOMultiGeoExperience.  Esto le mostrará si esta ubicación geográfica está en modo SPO.</br></br>
![Set-SPOMultiGeoExperience](media/Get-SPO-MultiGeo.jpg)

 
 
 
>[!Note]
>Algunas memorias caché del servicio se actualizan cada 24 horas, por lo que es posible que, durante un período de hasta 24 horas, la ubicación geográfica de su satélite se comporte de manera intermitente, como si estuviese todavía en modo ODB. Esto no causa problemas técnicos. 
 
Para obtener más información sobre SharePoint Multi-Geo, consulte [aka.ms/sharepointmultigeo](https://docs.microsoft.com/office365/enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365)


