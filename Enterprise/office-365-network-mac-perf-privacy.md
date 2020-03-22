---
title: Office 365 Network Insights privacidad y condiciones de uso (versión preliminar)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 03/04/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Office 365 Network Insights privacidad y condiciones de uso (versión preliminar)
ms.openlocfilehash: 9c47149ebef1e8b1614b26ad90fb60335783cfd0
ms.sourcegitcommit: 1c3aa0654336acec14098241f785ea1d8c6caf50
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "42891511"
---
# <a name="office-365-network-insights-privacy-and-terms-of-use-preview"></a>Office 365 Network Insights privacidad y condiciones de uso (versión preliminar)

El centro de administración de 365 de Microsoft muestra ahora la **información sobre la red y las recomendaciones de rendimiento**, que son métricas de rendimiento real recopiladas de su inquilino de Office 365 y que están disponibles para que las vean solo los usuarios administrativos de su espacio empresarial. La conectividad de red de la organización se diseña por ubicación de la oficina a través de una ubicación de salida de red a Internet. Office 365 Client Connectivity usa esa ruta y, a continuación, a través de Internet a los servidores de puerta de servicios de Microsoft. La identificación de las ubicaciones de oficina es la clave para poder mostrar esta información de red.

## <a name="location-in-network-measurements"></a>Ubicación en las medidas de red

El administrador de una organización puede optar por la ubicación que se va a incluir en las medidas de red usadas por esta característica. Esto permite la detección automática de la ciudad en la que se encuentra cada oficina. La información de ubicación no es precisa y se ofusca a 300 $ y se categoriza por ciudad. En el momento en que la ubicación se captura en un dispositivo Windows, mostrará un icono **de ubicación en uso** en la bandeja de herramientas y es posible que los administradores deseen notificar a los usuarios de esta. Con este procesamiento, la ubicación se trata como la ubicación de la oficina de la organización y no por la ubicación de una persona o un dispositivo. La información de red se puede mostrar en estas ciudades descubiertas de la ubicación de la oficina. Si se desea una mayor precisión de las recomendaciones, un administrador puede especificar direcciones de ubicación específicas de Office y la información de red se agregará a esos en su lugar. Las ubicaciones de oficina no se pueden agregar más de cerca de 300 metros.

## <a name="location-in-the-microsoft-365-admin-center"></a>Ubicación en el centro de administración de Microsoft 365

En el centro de administración de Microsoft 365, los controles de mapas de Bing se usan para mostrar dónde están las ubicaciones de la organización y para mostrar la topología de perímetro de red de una ubicación de la oficina seleccionada. Cuando un administrador agrega detalles de dirección específicos para ubicaciones de oficinas, los mapas de Bing también se usan para sugerir direcciones para facilitar la entrada de datos.

## <a name="terms-of-use"></a>Condiciones de uso

Cualquier contenido que se proporcione a través de mapas de Bing, incluidos los códigos geocodes, solo se puede usar dentro del producto a través del cual se proporciona el contenido. El uso del cliente de la característica de servicios de ubicación del centro de administración de M365, con tecnología de mapas de Bing, está regido por las _condiciones de uso disponibles del usuario final de mapas de Bing_ en <https://go.microsoft.com/?linkid=9710837> y la _declaración de privacidad de Microsoft_ disponible en<https://go.microsoft.com/fwlink/?LinkID=248686.>

Esta característica, que se proporciona a través de mapas de Bing, también es compatible con las **tecnologías de este**. La forma en que se aprovechan los servicios de ubicación proporcionados por estas tecnologías se rige por <https://legal.here.com/en-gb/terms>las _siguientes condiciones del servicio de tecnologías_ disponibles en.
