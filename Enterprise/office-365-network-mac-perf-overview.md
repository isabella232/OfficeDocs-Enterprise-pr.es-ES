---
title: Recomendaciones de rendimiento de red en el centro de administración de Microsoft 365 (versión preliminar)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 04/21/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Información general sobre las recomendaciones de rendimiento de red en el centro de administración de Microsoft 365 (versión preliminar)
ms.openlocfilehash: 077202f5ba1ffa95324131e6c283f2c3845aa07f
ms.sourcegitcommit: 07ab7d300c8df8b1665cfe569efc506b00915d23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2020
ms.locfileid: "43612940"
---
# <a name="network-performance-recommendations-in-the-microsoft-365-admin-center-preview"></a>Recomendaciones de rendimiento de red en el centro de administración de Microsoft 365 (versión preliminar)

El centro de administración de Microsoft 365 ahora incluye métricas de rendimiento en vivo recopiladas de su inquilino de Microsoft 365 y disponibles para que las vean solo los usuarios administrativos de su espacio empresarial. **información de red y recomendaciones de rendimiento** y **evaluaciones de red** se muestran en el centro de administración de 365 <https://portal.microsoft.com/adminportal/home#/networkperformance>de Microsoft en. Puede encontrar la página en el panel de navegación bajo **mantenimiento | Rendimiento**de la red.

![Página de rendimiento de red](Media/m365-mac-perf/m365-mac-perf-page-nav.png)

Cuando navegue por primera vez a la página rendimiento de red, verá un panel de información general que contiene un mapa de rendimiento global de la red, una evaluación de red con ámbito de todo el inquilino y una lista de problemas actuales. Desde la introducción, puede profundizar para ver las métricas de rendimiento de red y los problemas específicos por ubicación. Para obtener más información, consulte [Network performance Overview en el centro de administración de Microsoft 365](#network-performance-overview-in-the-microsoft-365-admin-center).

## <a name="pre-requisites-for-connectivity-measurements-to-appear"></a>Requisitos previos para que las medidas de conectividad aparezcan

Para que las medidas de conectividad aparezcan, debe tener al menos dos equipos en ejecución en cada ubicación de la oficina que admita los requisitos previos. La versión 19,232 o superior del cliente de sincronización de OneDrive para la empresa debe estar instalada en cada equipo. Para obtener más información, vea las notas de la [versión de OneDrive](https://support.office.com/article/onedrive-release-notes-845dcf18-f921-435e-bf28-4e24b95e5fc0).

El servicio de ubicación de Windows debe estar Consent en los equipos. Puede probar esto ejecutando la aplicación **mapas** y buscándolo. Se puede habilitar en un único equipo con la**Ubicación** de**privacidad** ->  **configuración** -> en la que la configuración "permitir que las aplicaciones tengan acceso a la ubicación" debe estar habilitada. El consentimiento de los servicios de ubicación de Windows se puede implementar en equipos que usen MDM o la Directiva de grupo con la configuración _LetAppsAccessLocation_.

Los equipos deben tener una red Wi-Fi en lugar de un cable Ethernet. Los equipos con un cable Ethernet no tienen información precisa sobre la ubicación.

Las muestras de medidas y las ubicaciones de la oficina deberían empezar a parecer 24 horas después de que se hayan cumplido estos requisitos previos.

## <a name="how-do-i-use-this-information"></a>¿Cómo puedo usar esta información?

**Network Insights**, las recomendaciones de rendimiento y las evaluaciones de red relacionadas con el mismo tienen como objetivo ayudarle a diseñar perímetros de red para sus ubicaciones de oficina. Cada conocimiento proporciona detalles sobre las características de rendimiento de un problema común específico para cada ubicación geográfica en la que los usuarios obtienen acceso a su inquilino. Las **recomendaciones de rendimiento** para cada visión de red ofrecen cambios de diseño de arquitectura de red específicos que puede realizar para mejorar la experiencia del usuario con la conectividad de red de Microsoft 365. La evaluación de la red muestra cómo la conectividad de red afecta a la experiencia del usuario, lo que permite comparar distintas conexiones de red de ubicación de usuario.

Las **evaluaciones de red** transforman una amplia variedad de métricas de rendimiento de red en una instantánea del estado de la red de la empresa, representada por un valor Points de 1-100. Las evaluaciones de red están en el ámbito de todo el inquilino y en cada ubicación geográfica desde la que los usuarios se conectan a su espacio empresarial, lo que proporciona a los administradores de Microsoft 365 una manera fácil de captar de forma instantánea un Gestalt del estado de la red de la empresa y profundizar rápidamente en un informe detallado de cualquier ubicación global de la oficina.

Las empresas complejas con varias ubicaciones de oficina y arquitecturas de perímetro de red no triviales pueden beneficiarse de esta información, ya sea durante su incorporación inicial a Microsoft 365 o para corregir los problemas de rendimiento de red detectados con el crecimiento de uso. Esto no suele ser necesario para las empresas pequeñas con Microsoft 365 o para las empresas que ya tienen conectividad de red sencilla y directa. Se espera que las empresas con más de 500 usuarios y varias ubicaciones de oficina disfruten de lo máximo.

>[!IMPORTANT]
>Información sobre la red, recomendaciones de rendimiento y evaluaciones en el centro de administración de Microsoft 365 se encuentra actualmente en estado de versión preliminar y solo está disponible para los inquilinos de Microsoft 365 que se han inscrito en el programa de vista previa de características.

## <a name="enterprise-network-connectivity-challenges"></a>Desafíos de conectividad de red empresarial

![Red del cliente a la nube](Media/m365-mac-perf/m365-mac-perf-first-last-mile.png)

Muchas empresas tienen configuraciones de perímetro de red que han crecido con el tiempo y están diseñadas principalmente para acomodar el acceso al sitio web de Internet de los empleados, donde la mayoría de los sitios web no se conocen de antemano y no son de confianza. El enfoque predominante y necesario evita los ataques de malware y de pesca de estos sitios web desconocidos. Esta estrategia de configuración de red, a la vez que resulta útil por motivos de seguridad, puede llevar a una degradación del rendimiento del usuario y de la experiencia del usuario de Microsoft 365.

## <a name="how-we-can-solve-these-challenges"></a>Cómo podemos resolver estos desafíos

Las empresas pueden mejorar la experiencia general del usuario y proteger su entorno siguiendo los [principios de conectividad de Office 365](https://aka.ms/pnc) y el uso de la característica de rendimiento de red del centro de administración de Microsoft 365. En la mayoría de los casos, los siguientes principios generales tendrán un impacto positivo significativo en la latencia del usuario final, la confiabilidad del servicio y el rendimiento general de Microsoft 365.

A veces, Microsoft se le pide que investigue los problemas de rendimiento de la red con Microsoft 365 para grandes clientes empresariales, y estos suelen tener una causa raíz relacionada con la infraestructura de salida de red de los clientes. Cuando se encuentra una causa de raíz común de un problema con el perímetro de la red del cliente, buscamos la identificación de medidas de prueba simples que la identifiquen. Una prueba con un umbral de medida que identifica un problema específico es valiosa porque podemos probar la misma medida en cualquier ubicación, saber si esta causa es la que está presente allí y compartirla como un conocimiento de red con el administrador.

En algunos detalles de red, simplemente se indica un problema que necesita una investigación más. Un conocimiento de la red donde se tienen suficientes pruebas para mostrar una acción de corrección específica para corregir la causa raíz aparece como una **Acción recomendada**. Estas recomendaciones, basadas en las métricas activas que revelan los valores que se encuentran fuera de un umbral predeterminado, son mucho más valiosas que los consejos de prácticas recomendadas generales, ya que son específicas de su entorno y muestran la mejora real una vez que se han realizado los cambios recomendados.

## <a name="network-performance-overview-in-the-microsoft-365-admin-center"></a>Introducción al rendimiento de red en el centro de administración de Microsoft 365

Microsoft tiene medidas de red existentes desde varios clientes Web y de escritorio de Office que admiten el funcionamiento de Microsoft 365. Estas mediciones ahora se usan para proporcionar información sobre el diseño de la arquitectura de red y una evaluación del rendimiento de la red que se muestran en la página **rendimiento de red** en el centro de administración de Microsoft 365.

De forma predeterminada, la información de ubicación aproximada asociada con las medidas de red identifica la ciudad en la que se encuentran los dispositivos cliente. La evaluación de la red en cada ubicación se muestra con color y el número relativo de usuarios en cada ubicación se representa por el tamaño del círculo.

![Mapa de información general de Network Insights](Media/m365-mac-perf/m365-mac-perf-overview-map.png)

La página de información general también muestra la evaluación de la red para el cliente como un promedio ponderado en todas las ubicaciones de la oficina.

![Evaluación de la red](Media/m365-mac-perf/m365-mac-perf-overview-score.png)

## <a name="specific-office-location-network-performance-summary-and-insights"></a>Información específica sobre el rendimiento y el resumen del rendimiento de red de una ubicación de Office

Al seleccionar una ubicación de la oficina se abre una página de Resumen específica de ubicación que muestra los detalles de las salidas de red que se han identificado a partir de las medidas de esa ubicación de la oficina.

![Detalles de Network Insights por ubicación](Media/m365-mac-perf/m365-mac-perf-locations-plan-overview.png)

La página de Resumen de ubicación de oficinas muestra además la evaluación de la red de la ubicación, el historial de la evaluación de la red, una comparación de la evaluación de esta ubicación con otros clientes de la misma ciudad y una lista de información específica y recomendaciones que puede emprender para mejorar el rendimiento y la fiabilidad de la red. Las ubicaciones con recomendaciones específicas también pueden incluir una posible mejora de la latencia.

Las comparaciones entre clientes en la misma ciudad se basan en la expectativa de que todos los clientes tengan el mismo acceso a los proveedores de servicios de red, la infraestructura de telecomunicaciones y los puntos cercanos de presencia de la red de Microsoft.

![Ubicaciones de Network Insights](Media/m365-mac-perf/m365-mac-perf-locations.png)

La pestaña detalles de la página ubicación de la oficina muestra los resultados de medidas específicos que se usaron para provenir de información, recomendaciones y la evaluación de la red. Esto se proporciona para que los ingenieros de red puedan validar las recomendaciones y el factor de las restricciones o los detalles de su entorno.

![Detalles específicos de la ubicación](Media/m365-mac-perf/m365-mac-perf-locations-plan-details-all.png)

Para los clientes que quieren mejorar la precisión de las recomendaciones y métricas específicas de ubicación, le permiten especificar información más específica. Esto puede reducir las aproximaciones inherentes a la información de ubicación disponible para las mediciones de red. Para editar la dirección de una ubicación específica de la <functionality not there yet>oficina,.

## <a name="import-undiscovered-office-locations"></a>Importar ubicaciones de oficina no descubiertas

La ficha **ubicaciones** de rendimiento de red muestra una lista de ubicaciones de oficinas detectadas automáticamente desde la telemetría de red. Estas ubicaciones de oficina son ciudades descubiertas. Puede Agregar de forma manual ubicaciones específicas dentro de esas ciudades si no aparecen automáticamente en la lista importándola de un archivo CSV. Si las ubicaciones de oficina no se muestran en absoluto, debe solucionar el problema por el que no aparecen sus mediciones en la red en lugar de simplemente agregar la ubicación aquí. También puede actualizar el valor de dirección de las ubicaciones de oficina existentes.

En el archivo CSV la ubicación de la ciudad descubierta se denomina **City**y una ubicación de la oficina agregada manualmente es la **Ubicación**de la etiqueta.

1. En la ventana principal _conectividad a Microsoft 365_ , haga clic en la pestaña **ubicaciones** .
1. Haga clic en el botón **importar** , justo encima de la lista ubicaciones. Aparecerá el control flotante **ubicaciones de importación** .

   ![Mensaje de error de importación de CSV](Media/m365-mac-perf/m365-mac-perf-import.png)

1. Haga clic en el vínculo **Descargar ubicaciones actuales de Office (. csv)** para exportar la lista de ubicaciones actuales a un archivo CSV y guárdelo en el disco duro local. Esto le proporcionará un archivo CSV con el formato correcto en el que puede Agregar ubicaciones. Puede dejar las ubicaciones exportadas tal y como están; no se duplicarán cuando importe el CSV actualizado. Si desea cambiar la dirección de una ubicación existente, se actualizará cuando importe el archivo CSV. No puede cambiar la dirección de una ciudad descubierta.
1. Abra el archivo CSV y agregue sus ubicaciones rellenando los siguientes campos en una nueva línea para cada ubicación que desee agregar. Deje todos los demás campos en blanco; se omitirán los valores que especifique en otros campos.
   1. **Dirección** (obligatorio): dirección física de la oficina
   1. **Latitud** (opcional): se rellena desde la búsqueda de mapas de Bing si está en blanco
   1. **Longitud** (opcional): se rellena desde la búsqueda de mapas de Bing si está en blanco
   1. **Intervalos de direcciones IP de salida 1-5** (opcional): para cada intervalo, escriba el nombre del circuito seguido de una lista separada por espacios de direcciones CIDR IPv4 o IPv6 válidas. Estos valores solo se usan cuando se ha habilitado la integración de SDWAN para una ubicación de oficina determinada.
1. Una vez que haya agregado las ubicaciones de la oficina y guardado el archivo, haga clic en el botón **examinar** situado junto al campo **cargar el completado** y seleccione el archivo CSV guardado.
1. El archivo se validará automáticamente. Si hay errores de validación, verá un mensaje de error que indica que _hay algunos errores en el archivo de importación. Revise los errores, corrija el archivo de importación y, a continuación, vuelva a intentarlo._ Haga clic en el vínculo **abrir detalles de error** para obtener una lista de errores de validación de campo específicos.

   ![Mensaje de error de importación de CSV](Media/m365-mac-perf/m365-mac-perf-import-error.png)

1. Si no hay errores en el archivo, verá el mensaje _el informe está listo. Se han encontrado x ubicaciones para agregar y x ubicaciones que se van a actualizar._ Haga clic en el botón **importar** para cargar el archivo CSV.

   ![Mensaje listo para importación de CSV](Media/m365-mac-perf/m365-mac-perf-import-ready.png)

## <a name="faq"></a>Preguntas más frecuentes

### <a name="what-is-a-microsoft-365-service-front-door"></a>¿Qué es una puerta de servicio de Microsoft 365?

La puerta de entrada del servicio 365 de Microsoft es un punto de entrada en la red global de Microsoft donde los clientes y servicios de Office terminan su conexión de red. Para obtener una conexión de red óptima a Microsoft 365, se recomienda que la conexión de red se termine en la puerta frontal de Microsoft 365 más cercana en su ciudad o metro.

>[!NOTE]
>La puerta de servicio de Microsoft 365 no tiene ninguna relación directa con el producto de servicio de puerta de Azure Front-Door disponible en Azure Marketplace.

### <a name="what-is-an-optimal-microsoft-365-service-front-door"></a>¿Qué es una puerta de servicio de Microsoft 365 óptima?

Una puerta frontal de servicio Microsoft 365 óptima es la que más se aproxime a la salida de la red, generalmente en su ciudad o área metropolitana. Use la [prueba de conectividad de microsoft 365](office-365-network-mac-perf-onboarding-tool.md) para determinar la ubicación de la puerta frontal del servicio de Microsoft 365 y la puerta de servicio óptima. Si la herramienta determina que la puerta frontal en uso es óptima, se está conectando de forma óptima a la red global de Microsoft.

### <a name="what-is-an-internet-egress-location"></a>¿Qué es una ubicación de salida de Internet?

La ubicación de salida de Internet es la ubicación en la que el tráfico de red sale de la red de la empresa y se conecta a Internet. También se identifica como la ubicación en la que tiene un dispositivo de traducción de direcciones de red (NAT) y normalmente donde se conecta con un proveedor de servicios de Internet (ISP). Si ve una larga distancia entre su ubicación y la ubicación de salida de Internet, esto puede indicar una backhaul? a WAN importante.

## <a name="related-topics"></a>Temas relacionados

[Información de la red de 365 de Microsoft (versión preliminar)](office-365-network-mac-perf-insights.md)

[Evaluación de red de Microsoft 365 (versión preliminar)](office-365-network-mac-perf-score.md)

[Prueba de conectividad de Microsoft 365 en el centro de administración de M365 (versión preliminar)](office-365-network-mac-perf-onboarding-tool.md)

[Servicios de ubicación de conectividad de red 365 de Microsoft (versión preliminar)](office-365-network-mac-location-services.md)
