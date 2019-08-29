---
title: Puntos de conexión de Office 365 de Alemania
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/28/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 8a113a50-0071-4155-bb8e-eba5a8dbd4c8
description: Si su organización usa Office 365 y restringe la conexión de los equipos de la red a Internet, a continuación encontrará los extremos (FQDN, puertos, direcciones URL e intervalos de direcciones IPv4 e IPv6) que debe incluir en las listas de permitidos de salida para asegurarse de que el los equipos pueden usar correctamente Office 365.
hideEdit: true
ms.openlocfilehash: 761cf4d6f3b6c214aae624138902d2f75a0e7a01
ms.sourcegitcommit: 0d21bd4edac07db94269e2a176c92469c02b2e26
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/28/2019
ms.locfileid: "36656028"
---
# <a name="office-365-germany-endpoints"></a>Puntos de conexión de Office 365 de Alemania

 *Se aplica a: Office 365 administrador*

**Resumen:** Office 365 requiere conectividad a Internet. Los puntos de conexión a continuación deben ser accesibles para los clientes que usen únicamente los planes de **Office 365 Germany** .
  
> [!NOTE]
> Microsoft ha publicado un servicio web basado en REST para las direcciones IP y las entradas FQDN de esta página. Este servicio le ayudará a configurar y actualizar dispositivos de perímetro de red, como firewalls y servidores proxy. Puede descargar la lista de puntos de conexión, la versión actual de la lista o cambios específicos. Este servicio reemplaza al documento XML que se vincula desde esta página, que ha pasado a estar en desusos el 2 de octubre de 2018. Para probar este nuevo servicio, vaya a [Servicio web](office-365-ip-web-service.md).
 
 **Puntos de conexión de Office 365:** [mundial (incluido GCC)](urls-and-ip-address-ranges.md)  | [Office 365 operado por 21Vianet](urls-and-ip-address-ranges-21vianet.md)  | *Office 365 Germany*  |  [Office 365 Administración Pública de Estados Unidos (DoD)](office-365-u-s-government-dod-endpoints.md) | [Office 365 Administración Pública de Estados Unidos (GCC High)](office-365-u-s-government-gcc-high-endpoints.md)  |
  
|||
|:-----|:-----|
|**Última actualización:** 08/28/2019- ![](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [suscripción de registro de cambios](https://endpoints.office.com/version/Germany?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) de RSS |**Descargue:** todos los destinos obligatorios y opcionales en una lista de [formato JSON](https://endpoints.office.com/endpoints/Germany?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).  <br/> |

Comience con la administración de los puntos de conexión de [Office 365](managing-office-365-endpoints.md) para comprender nuestras recomendaciones para administrar la conectividad de red con estos datos. Los datos de puntos de conexión se actualizan al principio de cada mes con nuevas direcciones IP y direcciones URL publicadas 30 días antes de estar activo. Esto permite a los clientes que aún no tienen actualizaciones automatizadas para completar sus procesos antes de que sea necesaria una nueva conectividad. Los puntos de conexión también se pueden actualizar durante el mes si es necesario para resolver las escalaciones de soporte, los incidentes de seguridad u otros requisitos operativos inmediatos. Siempre puede consultar la suscripción de [registro de cambios](https://endpoints.office.com/version/Germany?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).

Los datos que se muestran en esta página se generan a partir de los servicios web basados en REST. Si usa un script o un dispositivo de red para tener acceso a estos datos, debe ir directamente al [servicio Web](office-365-ip-web-service.md) .

Los siguientes datos de puntos de conexión enumeran los requisitos para la conectividad del equipo de un usuario a Office 365. No incluye las conexiones de red de Microsoft a una red de clientes, a veces denominadas híbridas o conexiones de red de entrada.

Los puntos de conexión se agrupan en cuatro áreas de servicio. Las tres primeras áreas de servicio se pueden seleccionar por separado para la conectividad. El cuarto área de servicio es una dependencia común (denominada Microsoft 365 Common y Office) y siempre debe tener conectividad de red.

Estas son columnas de datos que se muestran:

- **ID**: el número de identificación de la fila, también conocido como un conjunto de puntos de conexión. Este identificador es el mismo que devuelve el servicio web para el conjunto de puntos de conexión.

- **Categoría**: muestra si el conjunto de puntos de conexión se clasifica como "Optimizar", "Permitir" o "Predeterminado". Puede leer acerca de estas categorías y encontrar indicaciones para su administración en [http://aka.ms/pnc](http://aka.ms/pnc). Esta columna también muestra los conjuntos de puntos de conexión que deben tener conectividad de red. Para los conjuntos de puntos de conexión que no necesitan conectividad de red, le proporcionamos notas en este campo para indicar qué funcionalidad faltaría si se bloqueara el conjunto de puntos de conexión. Si va a excluir un área de servicio completa, los conjuntos de puntos de conexión enumerados como necesarios no necesitan conectividad.

- **EMERGENCIA**: aparece como **Sí** si el conjunto de puntos de conexión se admite en Azure ExpressRoute con prefijos de ruta de Office 365. La comunidad de BGP que incluye los prefijos de ruta que aparecen se alinea con el área de servicio que se muestra. Si EMERGENCIA aparece como **No**, esto significa que ExpressRoute no es compatible con este conjunto de puntos de conexión. Sin embargo, no se debe dar por hecho que no se anuncia ninguna ruta para un conjunto de puntos de conexión cuando EMERGENCIA se establezca como **No**.

- **Direcciones**: enumera los FQDN o nombres de dominio con caracteres comodín y los intervalos de direcciones IP para el conjunto de puntos de conexión. Tenga en cuenta que un intervalo de direcciones IP está en formato CIDR y puede incluir varias direcciones IP individuales en la red especificada.
 
- **Puertos**: muestra los puertos TCP o UDP que se combinan con las direcciones para formar el punto de conexión de la red. Es posible que observe repeticiones de intervalos de direcciones IP cuando se enumeran diferentes puertos.

[!INCLUDE [Office 365 Germany endpoints](./includes/office-365-germany-endpoints.md)]

 

