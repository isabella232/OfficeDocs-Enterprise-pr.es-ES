---
title: Office 365 puntos de conexión altos de GCC U.S. Government
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/28/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid: MET150
ms.assetid: cbd2369c-fd96-464c-bf48-c99826b459ee
description: En este artículo, encontrará los extremos a los que se puede llegar para los clientes con los planes altos de Office 365 U.S. Government GCC.
hideEdit: true
ms.openlocfilehash: 509cbf028899d0e289bc151922c63f22a231a827
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606535"
---
# <a name="office-365-us-government-gcc-high-endpoints"></a>Office 365 puntos de conexión altos de GCC U.S. Government

 *Se aplica a: Office 365 administrador*

Office 365 requiere conectividad a Internet. Los puntos de conexión a continuación deben ser accesibles para los clientes que usen únicamente los planes altos de Office 365 Estados Unidos GCC.
  
 **Puntos de conexión de Office 365:** [mundial (incluido GCC)](urls-and-ip-address-ranges.md) | [Office 365 operado por 21Vianet](urls-and-ip-address-ranges-21vianet.md)  | [Office 365 Germany](office-365-germany-endpoints.md)   |  [Office 365 Administración Pública de Estados Unidos (DoD)](office-365-u-s-government-dod-endpoints.md) | *Office 365 Administración Pública de Estados Unidos (GCC High)* |
  
|||
|:-----|:-----|
|**Última actualización:** 07/28/2020- ![ ](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [suscripción de registro de cambios](https://endpoints.office.com/version/USGOVGCCHigh?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) de RSS <br/> |**Descargar:** lista completa en [formato JSON](https://endpoints.office.com/endpoints/USGOVGCCHigh?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |

 Comience con la administración de los puntos de conexión de [Office 365](managing-office-365-endpoints.md) para comprender nuestras recomendaciones para administrar la conectividad de red con estos datos. Los datos de puntos de conexión se actualizan al principio de cada mes con nuevas direcciones IP y direcciones URL publicadas 30 días antes de estar activo. Esto permite a los clientes que aún no tienen actualizaciones automatizadas para completar sus procesos antes de que sea necesaria una nueva conectividad. Los puntos de conexión también se pueden actualizar durante el mes si es necesario para resolver las escalaciones de soporte, los incidentes de seguridad u otros requisitos operativos inmediatos. Los datos que se muestran en esta página se generan a partir de los servicios web basados en REST. Si usa un script o un dispositivo de red para tener acceso a estos datos, debe ir directamente al [servicio Web](office-365-ip-web-service.md) .

Los siguientes datos de puntos de conexión enumeran los requisitos para la conectividad del equipo de un usuario a Office 365. No incluye las conexiones de red de Microsoft a una red de clientes, a veces denominadas híbridas o conexiones de red de entrada.

Los puntos de conexión se agrupan en cuatro áreas de servicio. Las tres primeras se pueden seleccionar por separado para la conectividad; la cuarta área de servicio es una dependencia común (denominada de Microsoft 365 Common y Office) y debe disponer de conectividad de red en todo momento.

Estas son columnas de datos que se muestran:

- **ID**: el número de identificación de la fila, también conocido como un conjunto de puntos de conexión. Este identificador es el mismo que devuelve el servicio web para el conjunto de puntos de conexión.

- **Categoría**: muestra si el conjunto de puntos de conexión se clasifica como "Optimizar", "Permitir" o "Predeterminado". Puede leer acerca de estas categorías y encontrar indicaciones para su administración en [https://aka.ms/pnc](https://aka.ms/pnc). Esta columna también muestra los conjuntos de puntos de conexión que deben tener conectividad de red. Para los conjuntos de puntos de conexión que no necesitan conectividad de red, le proporcionamos notas en este campo para indicar qué funcionalidad faltaría si se bloqueara el conjunto de puntos de conexión. Si va a excluir un área de servicio completa, los conjuntos de puntos de conexión enumerados como necesarios no necesitan conectividad.

- **Er**: esto es **sí** si el conjunto de puntos de conexión es compatible con Azure ExpressRoute con los prefijos de ruta de Office 365. La comunidad de BGP que incluye los prefijos de ruta que se muestran se alinea con el área de servicio enumerada. Cuando ER es **no**, significa que ExpressRoute no es compatible con este conjunto de puntos de conexión. Sin embargo, no debe suponerse que ninguna ruta se anuncie para un punto de conexión en el que ER es **no**. Si tiene previsto usar Azure AD Connect, lea la [sección consideraciones especiales](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-instances#microsoft-azure-government) para asegurarse de que tiene la configuración adecuada de Azure ad Connect.

- **Direcciones**: enumera los FQDN o nombres de dominio con caracteres comodín y los intervalos de direcciones IP para el conjunto de puntos de conexión. Tenga en cuenta que un intervalo de direcciones IP está en formato CIDR y puede incluir varias direcciones IP individuales en la red especificada.
 
- **Puertos**: muestra los puertos TCP o UDP que se combinan con las direcciones para formar el punto de conexión de la red. Es posible que observe repeticiones de intervalos de direcciones IP cuando se enumeran diferentes puertos.
 
[!INCLUDE [Office 365 U.S. Government GCC High endpoints](./includes/office-365-u.s.-government-gcc-high-endpoints.md)]

Notas sobre esta tabla:

- El centro de seguridad y cumplimiento (SCC) proporciona compatibilidad con Azure ExpressRoute para Office 365. Lo mismo se aplica a muchas características expuestas a través del SCC, como la creación de informes, la auditoría, la exhibición avanzada de documentos electrónicos, la DLP unificada y el gobierno de datos. Dos características específicas, la importación de PST y la exportación de exhibición de documentos electrónicos, actualmente no admiten Azure ExpressRoute con solo filtros de ruta de Office 365 debido a su dependencia del almacenamiento de blobs de Azure. Para usar estas características, necesitará conectividad independiente a Azure BLOB Storage mediante las opciones de conectividad de Azure que se puedan admitir, que incluyen conectividad a Internet o Azure ExpressRoute con filtros de ruta pública de Azure. Debe evaluar el establecimiento de dicha conectividad para ambas características. El equipo de protección de la información de Office 365 conoce esta limitación y está trabajando activamente para permitir que Azure ExpressRoute para Office 365 se limite a los filtros de ruta de Office 365 para ambas características.

- Hay puntos de conexión opcionales adicionales para las aplicaciones de Microsoft 365 para empresas que no se muestran y que no son necesarios para que los usuarios inicien aplicaciones de Microsoft 365 para aplicaciones empresariales y editar documentos. Los puntos de conexión opcionales se hospedan en centros de datos de Microsoft y no procesan, transmiten ni almacenan datos de clientes. Se recomienda que las conexiones de usuario con estos extremos se dirijan al perímetro de salida de Internet predeterminado.

