---
title: Extremos de GCC alta de gobierno de Estados Unidos de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 8/13/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: MET150
ms.assetid: cbd2369c-fd96-464c-bf48-c99826b459ee
description: Si su organización usa Office 365 e impide que los equipos de la red que se conectan a Internet, a continuación encontrará los extremos (nombres de dominio completos, puertos, las direcciones URL, IPv4 y IPv6 intervalos de direcciones) que debe incluir en la salida permitir listas para asegurarse de que su los equipos pueden utilizar correctamente Office 365.
hideEdit: true
ms.openlocfilehash: eb1ac47ad8317b46ce19106e8eeab5dae3c25432
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542940"
---
# <a name="office-365-us-government-gcc-high-endpoints"></a>Extremos de GCC alta de gobierno de Estados Unidos de Office 365

 *Se aplica a: Administración de Office 365*

**Resumen:** Office 365 requiere conectividad a Internet. Los extremos que aparece a continuación deben ser accesibles para los clientes que usen sólo planes de Office 365 US gobierno GCC alta.
  
> [!NOTE]
> Microsoft está desarrollando un servicio web basado en REST para la dirección IP y las entradas de FQDN en esta página. Este nuevo servicio le ayudará a configurar y actualizar los dispositivos de perímetro de red, como firewalls y servidores proxy. Puede descargar la lista de extremos, la versión actual de la lista o cambios específicos. Este servicio finalmente reemplazará el documento XML, la fuente RSS y la dirección IP y las entradas de FQDN en esta página. Para probar este nuevo servicio, vaya al [servicio Web](managing-office-365-endpoints.md#webservice).
  
 **Los extremos de office 365:** [En el mundo (incluidos GCC)](urls-and-ip-address-ranges.md)  |  [Office 365 operado por 21 Vianet](urls-and-ip-address-ranges-21vianet.md)  | [Office 365 Alemania](office-365-germany-endpoints.md)  | [DoD de gobierno de Estados Unidos de Office 365](office-365-u-s-government-dod-endpoints.md) | *Alta de GCC de gobierno de Estados Unidos Office 365* |
  
|||
|:-----|:-----|
|**Última actualización:** 7/2018/2 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [suscripción del registro de cambios](https://aka.ms/usendpointrss) <br/> |**Descargar:** la lista completa en [formato XML](https://aka.ms/usdefenseendpoints) <br/> |
   
 Empiece con [extremos de administración de Office 365](managing-office-365-endpoints.md) comprender nuestras recomendaciones para administrar la conectividad de red con estos datos. Datos de extremos se actualizan al principio de cada mes con nuevas direcciones IP y URL publicadas 30 días antes de que sea activo. Esto permite que los clientes que todavía no han automatizado actualizaciones para completar sus procesos antes de que se requiere conectividad nuevo. Si es necesario para escalaciones de soporte técnico de dirección, incidentes de seguridad u otros requisitos de funcionamiento inmediatos extremos también pueden actualizarse durante el mes. Los datos que se muestran en esta página que aparece a continuación se generan desde los servicios web basado en REST. Si usa una secuencia de comandos o un dispositivo de red para tener acceso a estos datos, debe ir directamente al [servicio Web](managing-office-365-endpoints.md#webservice) .

Datos de extremo que aparece a continuación enumeran los requisitos para la conectividad desde el equipo de un usuario a Office 365. No incluye las conexiones de red de Microsoft en una red de cliente, a veces denominado híbrido o conexiones de red entrantes.

Los extremos se agrupan en cuatro áreas de servicio. Las áreas de servicio de tres primera pueden seleccionar de manera independiente para la conectividad. La cuarto área de servicio es una dependencia comunes (denominada Microsoft 365 comunes y Office Online) y siempre debe tener conectividad de red.

Columnas de datos que se muestran son:

- **ID**: el número de identificador de la fila, también conocido como un conjunto de extremo. Este identificador es el mismo que el devuelto por el servicio web para el conjunto de extremo.

- **Categoría**: muestra si el conjunto de extremo se clasifica como "Optimizar", "Permitir" o "Default". Puede leer acerca de estas categorías y orientación para la administración de ellos en [http://aka.ms/pnc](http://aka.ms/pnc). Esta columna también muestra qué conjuntos de extremo son necesarios para tener conectividad de red. Para los conjuntos de extremo que no es necesario tener conectividad de red, se proporcionan notas en este campo para indicar qué funcionalidad sería que faltan si está bloqueado el conjunto de extremo. Si va a excluir un área de todo el servicio, los conjuntos de extremo que aparecen según sea necesario no requieren conectividad.

- **Recuperación de emergencia**: Esto es **Yes** si se admite el conjunto de extremo a través de ExpressRoute de Azure con prefijos de ruta de Office 365. Alinea la Comunidad BGP que incluye los prefijos de ruta que se muestra con el área de servicio que aparecen. Cuando la recuperación de emergencia es **No**, esto significa que no se admite ExpressRoute para este conjunto de extremo. Sin embargo, no se debe suponer que no hay rutas se anuncian para un conjunto de extremo donde RE es **No**. Si tiene previsto usar Azure Connect de AD, lea la [sección Consideraciones especiales](https://docs.microsoft.com/azure/active-directory/connect/active-directory-AADconnect-instances#microsoft-azure-government-cloud) para asegurarse de que tiene la correspondiente configuración de Azure Connect de AD.

- **Direcciones**: enumera los nombres de dominio completos o nombres de dominio de caracteres comodín y los intervalos de direcciones IP para el conjunto de extremo. Tenga en cuenta que un intervalo de direcciones IP se encuentra en formato CIDR y puede incluir muchas direcciones IP individuales en la red especificada.
 
- **Puertos**: se enumeran los puertos TCP o UDP que se combinan con las direcciones para formar el extremo de la red. Es posible que observe algunos duplicación en intervalos de direcciones IP que existen diferentes puertos enumerados.
 
[!INCLUDE [Office 365 U.S. Government GCC High endpoints](./includes/office-365-u.s.-government-gcc-high-endpoints.md)]

Notas sobre esta tabla:

- La seguridad y el centro de cumplimiento (SCC) proporciona compatibilidad con ExpressRoute de Azure para Office 365. Lo mismo ocurre para muchas características que se exponen a través del control de código fuente, como informes, auditoría, eDiscovery avanzada, DLP unificada y gobierno de datos. Dos características específicas, PST Import y exhibición de documentos electrónicos exportación, actualmente no admiten ExpressRoute de Azure con Office 365 solo los filtros de rutas de debido a su dependencia en el almacenamiento de blobs de Azure. Para usar estas características, necesita conectividad independiente al almacenamiento de blobs de Azure usando cualquier opciones de conectividad de Azure trasladarse, que incluyen la conectividad a Internet o ExpressRoute de Azure con filtros de rutas pública de Azure. Se debe evaluar el establecimiento de dicha conectividad para ambos tipos de dichas características. El equipo de protección de la información de Office 365 es consciente de esta limitación y está trabajando activamente para ofrecer soporte técnico para ExpressRoute de Azure para Office 365 como limitada a los filtros de ruta de Office 365 para ambos tipos de dichas características.

- Hay extremos opcionales adicionales para Office 365 ProPlus que no están en la lista y no son necesarios para que los usuarios ejecutar aplicaciones de Office 365 ProPlus y editar documentos. Extremos opcionales se hospedan en centros de datos de Microsoft y no procesar, transmitir o almacenar los datos de cliente. Se recomienda que las conexiones de usuario a estos extremos se dirigirá al perímetro de salida de Internet de forma predeterminada.

