---
title: Puntos de conexión de Office 365 Germany
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 8/13/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 8a113a50-0071-4155-bb8e-eba5a8dbd4c8
description: Si su organización usa Office 365 e impide que los equipos de la red que se conectan a Internet, a continuación encontrará los extremos (nombres de dominio completos, puertos, las direcciones URL y IPv4 y IPv6 intervalos de direcciones) que debe incluir en la salida permitir listas para asegurarse de que su los equipos pueden utilizar correctamente Office 365.
hideEdit: true
ms.openlocfilehash: fa5133391a24a3b9bb82a9dc5065e4dd10bb5bfe
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542694"
---
# <a name="office-365-germany-endpoints"></a>Puntos de conexión de Office 365 Germany

 *Se aplica a: Administración de Office 365*

**Resumen:** Office 365 requiere conectividad a Internet. Los extremos que aparece a continuación deben ser accesibles para los clientes que usen únicamente los planes de **Office 365 Alemania** .
  
> [!NOTE]
> Microsoft está desarrollando un servicio web basado en REST para la dirección IP y las entradas de FQDN en esta página. Este nuevo servicio le ayudará a configurar y actualizar los dispositivos de perímetro de red, como firewalls y servidores proxy. Puede descargar la lista de extremos, la versión actual de la lista o cambios específicos. Este servicio finalmente reemplazará el documento XML, la fuente RSS y la dirección IP y las entradas de FQDN en esta página. Para probar este nuevo servicio, vaya al [servicio Web](managing-office-365-endpoints.md#webservice). 
  
 **Los extremos de office 365:** [En el mundo (incluidos GCC)](urls-and-ip-address-ranges.md)   |  [Office 365 operado por 21 Vianet](urls-and-ip-address-ranges-21vianet.md)  | *Office 365 Alemania* | [DoD de gobierno de Estados Unidos de Office 365](office-365-u-s-government-dod-endpoints.md) | [Alta de GCC de gobierno de Estados Unidos Office 365](office-365-u-s-government-gcc-high-endpoints.md)  |
  
|||
|:-----|:-----|
|**Última actualización:** 7/2018/2 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [lista de los cambios realizados en los extremos de Office 365 Alemania](office-365-germany-endpoints-change-log.md)||

Empiece con [extremos de administración de Office 365](managing-office-365-endpoints.md) comprender nuestras recomendaciones para administrar la conectividad de red con estos datos. Datos de extremos se actualizan al principio de cada mes con nuevas direcciones IP y URL publicadas 30 días antes de que sea activo. Esto permite que los clientes que todavía no han automatizado actualizaciones para completar sus procesos antes de que se requiere conectividad nuevo. Si es necesario para escalaciones de soporte técnico de dirección, incidentes de seguridad u otros requisitos de funcionamiento inmediatos extremos también pueden actualizarse durante el mes. Siempre puede hacer referencia a la [lista de los cambios realizados en los extremos de Office 365 Alemania](office-365-germany-endpoints-change-log.md).

Los datos que se muestran en esta página que aparece a continuación se generan desde los servicios web basado en REST. Si usa una secuencia de comandos o un dispositivo de red para tener acceso a estos datos, debe ir directamente al [servicio Web](managing-office-365-endpoints.md#webservice) .

Datos de extremo que aparece a continuación enumeran los requisitos para la conectividad desde el equipo de un usuario a Office 365. No incluye las conexiones de red de Microsoft en una red de cliente, a veces denominado híbrido o conexiones de red entrantes.

Los extremos se agrupan en cuatro áreas de servicio. Las áreas de servicio de tres primera pueden seleccionar de manera independiente para la conectividad. La cuarto área de servicio es una dependencia comunes (denominada Microsoft 365 comunes y Office Online) y siempre debe tener conectividad de red.

Columnas de datos que se muestran son:

- **ID**: el número de identificador de la fila, también conocido como un conjunto de extremo. Este identificador es el mismo que el devuelto por el servicio web para el conjunto de extremo.

- **Categoría**: muestra si el conjunto de extremo se clasifica como "Optimizar", "Permitir" o "Default". Puede leer acerca de estas categorías y orientación para la administración de ellos en [http://aka.ms/pnc](http://aka.ms/pnc). Esta columna también muestra qué conjuntos de extremo son necesarios para tener conectividad de red. Para los conjuntos de extremo que no es necesario tener conectividad de red, se proporcionan notas en este campo para indicar qué funcionalidad sería que faltan si está bloqueado el conjunto de extremo. Si va a excluir un área de todo el servicio, los conjuntos de extremo que aparecen según sea necesario no requieren conectividad.

- **Recuperación de emergencia**: Esto es **Yes** si se admite el conjunto de extremo a través de ExpressRoute de Azure con prefijos de ruta de Office 365. Alinea la Comunidad BGP que incluye los prefijos de ruta que se muestra con el área de servicio que aparecen. Cuando la recuperación de emergencia es **No**, esto significa que no se admite ExpressRoute para este conjunto de extremo. Sin embargo, no se debe suponer que no hay rutas se anuncian para un conjunto de extremo donde RE es **No**.

- **Direcciones**: enumera los nombres de dominio completos o nombres de dominio de caracteres comodín y los intervalos de direcciones IP para el conjunto de extremo. Tenga en cuenta que un intervalo de direcciones IP se encuentra en formato CIDR y puede incluir muchas direcciones IP individuales en la red especificada.
 
- **Puertos**: se enumeran los puertos TCP o UDP que se combinan con las direcciones para formar el extremo de la red. Es posible que observe algunos duplicación en intervalos de direcciones IP que existen diferentes puertos enumerados.

[!INCLUDE [Office 365 Germany endpoints](./includes/office-365-germany-endpoints.md)]

 

