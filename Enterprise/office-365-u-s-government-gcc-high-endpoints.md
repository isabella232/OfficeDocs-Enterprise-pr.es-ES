---
title: Extremos de GCC alta de gobierno de Estados Unidos de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/17/2019
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
ms.openlocfilehash: 5c849775c8fd55d9e4196ebad6c55cdf56d2ab60
ms.sourcegitcommit: 0c4f50aa55699b8390038efbb8b50dbe10f3eefe
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2019
ms.locfileid: "28723387"
---
# <a name="office-365-us-government-gcc-high-endpoints"></a>Extremos de GCC alta de gobierno de Estados Unidos de Office 365

 *Se aplica a: Administración de Office 365*

**Resumen:** Office 365 requiere conectividad a Internet. Los extremos que aparece a continuación deben ser accesibles para los clientes que usen sólo planes de Office 365 US gobierno GCC alta.
  
> [!NOTE]
> Microsoft ha publicado un servicio web basado en REST para las direcciones IP y las entradas FQDN de esta página. Este servicio le ayudará a configurar y actualizar dispositivos de perímetro de red, como firewalls y servidores proxy. Puede descargar la lista de puntos de conexión, la versión actual de la lista o cambios específicos. Este servicio reemplaza al documento XML que se vincula desde esta página, que ha pasado a estar en desusos el 2 de octubre de 2018. Para probar este nuevo servicio, vaya a [Servicio web](office-365-ip-web-service.md).
  
 **Puntos de conexión de Office 365:** [mundial (incluido GCC)](urls-and-ip-address-ranges.md) | [Office 365 operado por 21Vianet](urls-and-ip-address-ranges-21vianet.md)  | [Office 365 Germany](office-365-germany-endpoints.md)   |  [Office 365 Administración Pública de Estados Unidos (DoD)](office-365-u-s-government-dod-endpoints.md) | *Office 365 Administración Pública de Estados Unidos (GCC High)* |
  
|||
|:-----|:-----|
|**Última actualización:** 01/2019/17 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [suscripción del registro de cambios](https://endpoints.office.com/version/USGOVGCCHigh?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |**Descargar:** la lista completa en [formato JSON](https://endpoints.office.com/endpoints/USGOVGCCHigh?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |
   
 Empiece con [extremos de administración de Office 365](managing-office-365-endpoints.md) comprender nuestras recomendaciones para administrar la conectividad de red con estos datos. Datos de extremos se actualizan al principio de cada mes con nuevas direcciones IP y URL publicadas 30 días antes de que sea activo. Esto permite a los clientes que todavía no han automatizado actualizaciones para completar sus procesos antes de que se requiere conectividad nuevo. Si es necesario para escalaciones de soporte técnico de dirección, incidentes de seguridad u otros requisitos de funcionamiento inmediatos extremos también pueden actualizarse durante el mes. Los datos que se muestran en esta página que aparece a continuación se generan desde los servicios web basado en REST. Si usa una secuencia de comandos o un dispositivo de red para tener acceso a estos datos, debe ir directamente al [servicio Web](office-365-ip-web-service.md) .

Los siguientes datos de puntos de conexión enumeran los requisitos para la conectividad del equipo de un usuario a Office 365. No incluye las conexiones de red de Microsoft a una red de clientes, a veces denominadas híbridas o conexiones de red de entrada.

Los puntos de conexión se agrupan en cuatro áreas de servicio. Las tres primeras se pueden seleccionar por separado para la conectividad; la cuarta área de servicio es una dependencia común (denominada de Microsoft 365 Common y Office Online) y debe disponer de conectividad de red en todo momento.

Estas son columnas de datos que se muestran:

- **ID**: el número de identificación de la fila, también conocido como un conjunto de puntos de conexión. Este identificador es el mismo que devuelve el servicio web para el conjunto de puntos de conexión.

- **Categoría**: muestra si el conjunto de puntos de conexión se clasifica como "Optimizar", "Permitir" o "Predeterminado". Puede leer acerca de estas categorías y encontrar indicaciones para su administración en [http://aka.ms/pnc](http://aka.ms/pnc). Esta columna también muestra los conjuntos de puntos de conexión que deben tener conectividad de red. Para los conjuntos de puntos de conexión que no necesitan conectividad de red, le proporcionamos notas en este campo para indicar qué funcionalidad faltaría si se bloqueara el conjunto de puntos de conexión. Si va a excluir un área de servicio completa, los conjuntos de puntos de conexión enumerados como necesarios no necesitan conectividad.

- **Recuperación de emergencia**: Esto es **Yes** si se admite el conjunto de extremo a través de ExpressRoute de Azure con prefijos de ruta de Office 365. Alinea la Comunidad BGP que incluye los prefijos de ruta que se muestra con el área de servicio que aparecen. Cuando la recuperación de emergencia es **No**, esto significa que no se admite ExpressRoute para este conjunto de extremo. Sin embargo, no se debe suponer que no hay rutas se anuncian para un conjunto de extremo donde RE es **No**. Si tiene previsto usar Azure Connect de AD, lea la [sección Consideraciones especiales](https://docs.microsoft.com/azure/active-directory/connect/active-directory-AADconnect-instances#microsoft-azure-government-cloud) para asegurarse de que tiene la correspondiente configuración de Azure Connect de AD.

- **Direcciones**: enumera los FQDN o nombres de dominio con caracteres comodín y los intervalos de direcciones IP para el conjunto de puntos de conexión. Tenga en cuenta que un intervalo de direcciones IP está en formato CIDR y puede incluir varias direcciones IP individuales en la red especificada.
 
- **Puertos**: muestra los puertos TCP o UDP que se combinan con las direcciones para formar el punto de conexión de la red. Es posible que observe repeticiones de intervalos de direcciones IP cuando se enumeran diferentes puertos.
 
[!INCLUDE [Office 365 U.S. Government GCC High endpoints](./includes/office-365-u.s.-government-gcc-high-endpoints.md)]

Notas sobre esta tabla:

- La seguridad y el centro de cumplimiento (SCC) proporciona compatibilidad con ExpressRoute de Azure para Office 365. Lo mismo ocurre para muchas características que se exponen a través del control de código fuente, como informes, auditoría, eDiscovery avanzada, DLP unificada y gobierno de datos. Dos características específicas, PST Import y exhibición de documentos electrónicos exportación, actualmente no admiten ExpressRoute de Azure con Office 365 solo los filtros de rutas de debido a su dependencia en el almacenamiento de blobs de Azure. Para usar estas características, necesita conectividad independiente al almacenamiento de blobs de Azure usando cualquier opciones de conectividad de Azure trasladarse, que incluyen la conectividad a Internet o ExpressRoute de Azure con filtros de rutas pública de Azure. Se debe evaluar el establecimiento de dicha conectividad para ambos tipos de dichas características. El equipo de protección de la información de Office 365 es consciente de esta limitación y está trabajando activamente para ofrecer soporte técnico para ExpressRoute de Azure para Office 365 como limitada a los filtros de ruta de Office 365 para ambos tipos de dichas características.

- Hay extremos opcionales adicionales para Office 365 ProPlus que no están en la lista y no son necesarios para que los usuarios ejecutar aplicaciones de Office 365 ProPlus y editar documentos. Extremos opcionales se hospedan en centros de datos de Microsoft y no procesar, transmitir o almacenar los datos de cliente. Se recomienda que las conexiones de usuario a estos extremos se dirigirá al perímetro de salida de Internet de forma predeterminada.

