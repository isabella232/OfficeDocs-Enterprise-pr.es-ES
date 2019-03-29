---
title: Cuotas de almacenamiento de SharePoint en entornos multigeográficos
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Obtenga información sobre las cuotas de almacenamiento de SharePoint en entornos multigeográficos.
ms.openlocfilehash: 9c43f21a844507c4de7971d70a110665ddc094ba
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2019
ms.locfileid: "30934095"
---
# <a name="sharepoint-storage-quotas-in-multi-geo-environments"></a>Cuotas de almacenamiento de SharePoint en entornos multigeográficos

De forma predeterminada, todas las ubicaciones geográficas de un entorno multigeográfico comparten la cuota de almacenamiento del espacio empresarial disponible.

Con la configuración de cuota de almacenamiento de SharePoint geográfica, puede administrar la cuota de almacenamiento para cada ubicación geográfica. Al asignar una cuota de almacenamiento de una ubicación geográfica, esta se convierte en la cantidad máxima de almacenamiento disponible para esa ubicación geográfica y se resta de la cuota de almacenamiento disponible por espacio empresarial. Luego, la cuota de almacenamiento disponible por espacio empresarial restante se comparte entre las ubicaciones geográficas configuradas a las que no se ha asignado una cuota de almacenamiento.

La cuota de almacenamiento de SharePoint para cualquier ubicación geográfica puede asignarse por el administrador de SharePoint Online mediante la conexión a la ubicación central. Los administradores geográficos de ubicaciones satélites pueden ver la cuota de almacenamiento, pero no pueden asignarlas.

## <a name="configure-a-storage-quota-for-a-geo-location"></a>Configurar una cuota de almacenamiento de una ubicación geográfica

Use el [módulo de Microsoft Office SharePoint Online](https://www.microsoft.com/en-us/download/details.aspx?id=35588 ) y conéctese a la ubicación central para asignar la cuota de almacenamiento de una ubicación geográfica. 

Para asignar la cuota de almacenamiento de una ubicación, ejecute el cmdlet:

`Set-SPOGeoStorageQuota -GeoLocation <geolocationcode> -StorageQuotaMB <value>`

Para ver la cuota de almacenamiento de la ubicación geográfica actual, ejecute:

`Get-SPOGeoStorageQuota`

![Ventana de captura de pantalla de PowerShell que muestra el cmdlet Get-SPOGeoStorageQuota](media/multi-geo-storage-quota.png)

Para ver la cuota de almacenamiento de todas las ubicaciones geográficas, ejecute:

`Get-SPOGeoStorageQuota -AllLocations`

Para quitar la cuota de almacenamiento asignada a una ubicación geográfica, establezca `StorageQuota value = 0`:

`Set-SPOGeoStorageQuota -GeoLocation <geolocationcode> -StorageQuotaMB 0`
