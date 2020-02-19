---
title: Office 365 global tenant performance Optimization para usuarios de China
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 2/13/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
search.appverid: MET150
f1.keywords:
- NOCSH
description: En este artículo se proporcionan instrucciones para optimizar el rendimiento de red de los usuarios de China de los inquilinos globales de Office 365.
ms.openlocfilehash: 33e475dfbf4accf306a099542cf8cf2f22ff23a5
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106450"
---
# <a name="office-365-global-tenant-performance-optimization-for-china-users"></a>Office 365 global tenant performance Optimization para usuarios de China

>[!IMPORTANT]
>Esta guía es específica para los escenarios de uso en los que **los usuarios empresariales de office 365 ubicados en China** se conectan a un **inquilino global de Office 365**. Esta guía **no** se aplica a los inquilinos de Office 365 operado por 21Vianet.

Para las empresas con inquilinos globales de Office 365 y presencia corporativa en China, el rendimiento del cliente de Office 365 para los usuarios basados en China puede ser complicado con factores exclusivos de la arquitectura de Internet de la Telco de China.

Los ISP de China tienen conexiones internacionales reguladas a la Internet pública global que atraviesan dispositivos perimetrales que son propensos a la congestión de la red transfronteriza. Esta congestión genera la pérdida de paquetes y la latencia de todo el tráfico de Internet que entra y sale de China.

![Tráfico de Office 365-no optimizado](media/O365-networking/China-O365-unoptimized.png)

La pérdida y la latencia del paquete perjudican al rendimiento de los servicios de red, en especial los servicios que requieren intercambios de datos de gran tamaño (como transferencias de archivos de gran tamaño) o que requieran un rendimiento casi en tiempo real (aplicaciones de audio y vídeo).

El objetivo de este tema es proporcionar los procedimientos recomendados para mitigar el impacto de la congestión de la red entre bordes China en los servicios de Office 365. En este tema no se abordan otros problemas de rendimiento de última millas comunes, como problemas de alta latencia de paquetes debido a un enrutamiento complejo dentro de los operadores de China.

## <a name="corporate-network-best-practices"></a>Procedimientos recomendados de red corporativa

Muchas empresas con inquilinos globales de Office 365 y usuarios en China han implementado redes privadas que transportan el tráfico de red corporativa entre las ubicaciones de la oficina de China y las ubicaciones internacionales de todo el mundo. Estas empresas pueden aprovechar esta infraestructura de red para evitar la congestión de la red transfronteriza y optimizar el rendimiento del servicio de Office 365 en China.

>[!IMPORTANT]
>Como con todas las implementaciones de WAN privadas, siempre debe consultar los requisitos normativos de su país o región para asegurarse de que la configuración de red cumple los requisitos.

Como primer paso, es crucial que siga nuestras instrucciones para la red de criterios de referencia en [planificación de red y ajuste del rendimiento para Office 365](https://aka.ms/tune). El objetivo principal es evitar el acceso a los servicios globales de Office 365 desde Internet en China, si es posible.

- Aproveche su red privada existente para transportar el tráfico de red de Office 365 entre las redes de Office China y las ubicaciones en el extranjero que salen de la Internet pública fuera de China. Casi cualquier ubicación fuera de China le proporcionará una ventaja clara. Los administradores de red pueden optimizar aún más la salida en áreas con interconexiones de baja latencia con [Microsoft Global Network](https://docs.microsoft.com/azure/networking/microsoft-global-network). Hong Kong, Japón y Corea del sur son ejemplos.
- Configure los dispositivos de usuario para que tengan acceso a la red corporativa a través de una conexión VPN para permitir que el tráfico de Office 365 transporte el vínculo exterior privado de la red corporativa. Asegúrese de que los clientes de VPN no están configurados para usar el túnel dividido o que los dispositivos de usuario están configurados para omitir el túnel dividido para el tráfico de Office 365.
- Configure su red para enrutar todo el tráfico de Office 365 en su vínculo de extranjero privado. Si necesita minimizar el volumen de tráfico en su vínculo privado, puede elegir sólo enrutar los extremos en la categoría **optimizar** y permitir que las solicitudes de **permiso** y extremos **predeterminados** atraviesen Internet. Esto mejorará el rendimiento y minimizará el consumo de ancho de banda limitando el tráfico optimizado a los servicios críticos que sean más sensibles a la alta latencia y pérdida de paquetes.
- Si es posible, use UDP en lugar de TCP para el tráfico de transmisión de medios en directo, como en el caso de Microsoft Teams. UDP ofrece un mejor rendimiento de transmisión por secuencias de medios en directo que TCP.

Para obtener información acerca de cómo enrutar selectivamente el tráfico de Office 365, consulte [Managing office 365 endpoints](managing-office-365-endpoints.md). Para obtener una lista de todas las direcciones IP y URL de Office 365 en todo el mundo, consulte [direcciones URL e intervalos de direcciones IP de office 365](urls-and-ip-address-ranges.md).

![Office 365 con tráfico optimizado](media/O365-networking/China-O365-optimized.png)

## <a name="user-best-practices"></a>Procedimientos recomendados para el usuario

Los usuarios de China que se conectan a inquilinos globales de Office 365 desde ubicaciones remotas como hogares, cafeterías, hoteles y sucursales sin conexión a redes empresariales pueden experimentar un rendimiento deficiente en la red, ya que el tráfico entre sus dispositivos y Office 365 debe atravesar los circuitos de red transfronterizos congestionados de China.

Si las redes privadas transfronterizas o el acceso VPN a la red corporativa no son una opción, los problemas de rendimiento por usuario todavía pueden mitigarse al entrenar a los usuarios basados en China para que sigan estos procedimientos recomendados.

- Use clientes de Office enriquecidos que admitan el almacenamiento en caché (por ejemplo, Outlook, Teams, OneDrive, etc.) y evite los clientes basados en Web. El almacenamiento en caché del cliente de Office y las características de acceso sin conexión pueden reducir drásticamente el impacto de la saturación y la latencia de la red.
- Si su inquilino de Office 365 se ha configurado con la característica _audioconferencia_ , los usuarios de Teams pueden unirse a reuniones a través de la red telefónica conmutada (RTC). Para obtener más información, vea [audioconferencia en Office 365](https://docs.microsoft.com/microsoftteams/audio-conferencing-in-office-365).
- Si los usuarios experimentan problemas de rendimiento de la red, deben informar a su Departamento de TI para solucionar problemas y escalar al soporte técnico de Microsoft si se sospecha que hay problemas con los servicios de Office 365. No todos los problemas están causados por el rendimiento de la red transfronteriza.

Microsoft está trabajando continuamente para mejorar la experiencia de usuario de Office 365 y el rendimiento de los clientes en una gama más amplia posible de arquitecturas de red y características. Visite la [comunidad técnica de Office 365](https://techcommunity.microsoft.com/t5/office-365/bd-p/Office365General) para iniciar o unirse a una conversación, buscar recursos y enviar solicitudes y sugerencias de características.

## <a name="related-topics"></a>Temas relacionados

[Planeamiento de red y ajuste del rendimiento para Office 365](https://aka.ms/tune)

[Principios de conectividad de red de Office 365](office-365-network-connectivity-principles.md)

[Administrar puntos de conexión de Office 365](managing-office-365-endpoints.md)

[Direcciones URL e intervalos de direcciones IP de Office 365](urls-and-ip-address-ranges.md)

[Red global de Microsoft](https://docs.microsoft.com/azure/networking/microsoft-global-network)
