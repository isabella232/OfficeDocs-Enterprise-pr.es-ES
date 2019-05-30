---
title: Office 365 puntos de conexión altos de GCC U.S. Government
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/28/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid: MET150
ms.assetid: cbd2369c-fd96-464c-bf48-c99826b459ee
description: Si su organización usa Office 365 y restringe la conexión de los equipos de la red a Internet, a continuación encontrará los extremos (FQDN, puertos, direcciones URL, IPv4 e intervalos de direcciones IPv6) que debe incluir en las listas de permitidos de salida para asegurarse de que el los equipos pueden usar correctamente Office 365.
hideEdit: true
ms.openlocfilehash: 243533aabab312f366580c806b2c8ca247afc22a
ms.sourcegitcommit: a168f0df1a1034761be2ff6d4dbe8d6ba81ce0ee
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/28/2019
ms.locfileid: "34494811"
---
# <a name="office-365-us-government-gcc-high-endpoints"></a>Office 365 puntos de conexión altos de GCC U.S. Government

 *Se aplica a: Office 365 administrador*

**Resumen:** Office 365 requiere conectividad a Internet. Los puntos de conexión a continuación deben ser accesibles para los clientes que usen únicamente los planes altos de Office 365 Estados Unidos GCC.
  
> [!NOTE]
> Microsoft ha publicado un servicio web basado en REST para las direcciones IP y las entradas FQDN de esta página. Este servicio le ayudará a configurar y actualizar dispositivos de perímetro de red, como firewalls y servidores proxy. Puede descargar la lista de puntos de conexión, la versión actual de la lista o cambios específicos. Este servicio reemplaza al documento XML que se vincula desde esta página, que ha pasado a estar en desusos el 2 de octubre de 2018. Para probar este nuevo servicio, vaya a [Servicio web](office-365-ip-web-service.md).
  
 **Puntos de conexión de Office 365:** [mundial (incluido GCC)](urls-and-ip-address-ranges.md) | [Office 365 operado por 21Vianet](urls-and-ip-address-ranges-21vianet.md)  | [Office 365 Germany](office-365-germany-endpoints.md)   |  [Office 365 Administración Pública de Estados Unidos (DoD)](office-365-u-s-government-dod-endpoints.md) | *Office 365 Administración Pública de Estados Unidos (GCC High)* |
  
|||
|:-----|:-----|
|**Última actualización:** 05/28/2019- ![](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [suscripción de registro de cambios](https://endpoints.office.com/version/USGOVGCCHigh?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) de RSS <br/> |**Descargar:** lista completa en [formato JSON](https://endpoints.office.com/endpoints/USGOVGCCHigh?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |
   
 Comience con la administración de los puntos de conexión de [Office 365](managing-office-365-endpoints.md) para comprender nuestras recomendaciones para administrar la conectividad de red con estos datos. Los datos de puntos de conexión se actualizan al principio de cada mes con nuevas direcciones IP y direcciones URL publicadas 30 días antes de estar activo. Esto permite a los clientes que aún no tienen actualizaciones automatizadas para completar sus procesos antes de que sea necesaria una nueva conectividad. Los puntos de conexión también se pueden actualizar durante el mes si es necesario para resolver las escalaciones de soporte, los incidentes de seguridad u otros requisitos operativos inmediatos. Los datos que se muestran en esta página se generan a partir de los servicios web basados en REST. Si usa un script o un dispositivo de red para tener acceso a estos datos, debe ir directamente al [servicio Web](office-365-ip-web-service.md) .

Los siguientes datos de puntos de conexión enumeran los requisitos para la conectividad del equipo de un usuario a Office 365. No incluye las conexiones de red de Microsoft a una red de clientes, a veces denominadas híbridas o conexiones de red de entrada.

Los puntos de conexión se agrupan en cuatro áreas de servicio. Las tres primeras se pueden seleccionar por separado para la conectividad; la cuarta área de servicio es una dependencia común (denominada de Microsoft 365 Common y Office Online) y debe disponer de conectividad de red en todo momento.

Estas son columnas de datos que se muestran:

- **ID**: el número de identificación de la fila, también conocido como un conjunto de puntos de conexión. Este identificador es el mismo que devuelve el servicio web para el conjunto de puntos de conexión.

- **Categoría**: muestra si el conjunto de puntos de conexión se clasifica como "Optimizar", "Permitir" o "Predeterminado". Puede leer acerca de estas categorías y encontrar indicaciones para su administración en [http://aka.ms/pnc](http://aka.ms/pnc). Esta columna también muestra los conjuntos de puntos de conexión que deben tener conectividad de red. Para los conjuntos de puntos de conexión que no necesitan conectividad de red, le proporcionamos notas en este campo para indicar qué funcionalidad faltaría si se bloqueara el conjunto de puntos de conexión. Si va a excluir un área de servicio completa, los conjuntos de puntos de conexión enumerados como necesarios no necesitan conectividad.

- **Er**: esto es **sí** si el conjunto de puntos de conexión es compatible con Azure ExpressRoute con los prefijos de ruta de Office 365. La comunidad de BGP que incluye los prefijos de ruta que se muestran se alinea con el área de servicio enumerada. Cuando ER es **no**, significa que ExpressRoute no es compatible con este conjunto de puntos de conexión. Sin embargo, no debe suponerse que ninguna ruta se anuncie para un punto de conexión en el que ER es **no**. Si tiene previsto usar Azure AD Connect, lea la [sección consideraciones especiales](https://docs.microsoft.com/azure/active-directory/connect/active-directory-AADconnect-instances#microsoft-azure-government-cloud) para asegurarse de que tiene la configuración adecuada de Azure ad Connect.

- **Direcciones**: enumera los FQDN o nombres de dominio con caracteres comodín y los intervalos de direcciones IP para el conjunto de puntos de conexión. Tenga en cuenta que un intervalo de direcciones IP está en formato CIDR y puede incluir varias direcciones IP individuales en la red especificada.
 
- **Puertos**: muestra los puertos TCP o UDP que se combinan con las direcciones para formar el punto de conexión de la red. Es posible que observe repeticiones de intervalos de direcciones IP cuando se enumeran diferentes puertos.
 
[!INCLUDE [Office 365 U.S. Government GCC High endpoints](./includes/office-365-u.s.-government-gcc-high-endpoints.md)]

Notas sobre esta tabla:

- El centro de seguridad y cumplimiento (SCC) proporciona compatibilidad con Azure ExpressRoute para Office 365. Lo mismo se aplica a muchas características expuestas a través del SCC, como la creación de informes, la auditoría, la exhibición avanzada de documentos electrónicos, la DLP unificada y el gobierno de datos. Dos características específicas, la importación de PST y la exportación de exhibición de documentos electrónicos, actualmente no admiten Azure ExpressRoute con solo filtros de ruta de Office 365 debido a su dependencia del almacenamiento de blobs de Azure. Para usar estas características, necesitará conectividad independiente a Azure BLOB Storage mediante las opciones de conectividad de Azure que se puedan admitir, que incluyen conectividad a Internet o Azure ExpressRoute con filtros de ruta pública de Azure. Debe evaluar el establecimiento de dicha conectividad para ambas características. El equipo de protección de la información de Office 365 conoce esta limitación y está trabajando activamente para permitir que Azure ExpressRoute para Office 365 se limite a los filtros de ruta de Office 365 para ambas características.

- Hay puntos de conexión opcionales adicionales para Office 365 ProPlus que no se muestran y que no son necesarios para que los usuarios inicien aplicaciones de Office 365 ProPlus y editen documentos. Los puntos de conexión opcionales se hospedan en centros de datos de Microsoft y no procesan, transmiten ni almacenan datos de clientes. Se recomienda que las conexiones de usuario con estos extremos se dirijan al perímetro de salida de Internet predeterminado.

