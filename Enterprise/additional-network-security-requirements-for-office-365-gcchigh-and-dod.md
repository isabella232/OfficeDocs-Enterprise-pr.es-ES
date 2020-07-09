---
title: Requisitos de seguridad de red adicionales para Office 365 GCC High y DoD
ms.author: dzazzo
author: dzazzo
manager: dzazzo
ms.date: 05/19/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- OGA150m
- OGC150
- OGD150
- MOE150
ms.assetid: ''
description: 'Resumen: Office 365 GCC High y DoD tienen requisitos de seguridad de red adicionales'
hideEdit: true
ms.openlocfilehash: a79204809787391065ac833d9a3872af4cdc1528
ms.sourcegitcommit: 576c3dbdef535f952a861197dea5348908da9504
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "44371636"
---
# <a name="additional-network-security-requirements-for-office-365-gcc-high-and-dod"></a>Requisitos de seguridad de red adicionales para Office 365 GCC High y DOD

*Este artículo se aplica a Office 365 GCC High, Office 365 DOD, Microsoft 365 GCC High y Microsoft 365 DOD.*

Office 365 GCC High and DOD son entornos de nube segura para satisfacer las necesidades del gobierno de Estados Unidos y sus proveedores y contratistas.  Estos entornos de nube tienen restricciones de red adicionales en las que se permite el acceso a los extremos externos a los que tienen acceso los servicios.

Los clientes de GCC High y DOD que planean usar identidades federadas o coexistencia híbrida pueden requerir que Microsoft permita el acceso entrante y saliente a las implementaciones locales existentes.  Algunos ejemplos de estas actividades son:

* Uso de identidades federadas (con servicios de Federación de Active Directory o STS compatibles similares)
* Coexistencia híbrida con una implementación local de Exchange Server o Skype empresarial
* Migración del contenido de usuario existente desde un sistema local

Para permitir que el servicio se comunique con los extremos locales, **debe** enviar un correo electrónico a Office 365 Engineering para cambios de red.

> [!WARNING]
> Todas las solicitudes tienen un SLA de **tres semanas** y no se pueden acelerar debido a los controles de seguridad y cumplimiento necesarios y a las canalizaciones de implementación.  Esto incluye las solicitudes de red de incorporación inicial y los cambios después de la migración al servicio.  Asegúrese de que los equipos de red conocen esta escala de tiempo e lo incluyen en sus ciclos de planeación.

Envíe un correo electrónico a la [lista blanca de redes de Office 365 Government](mailto:o365gwlt@microsoft.com) con la siguiente información:

* **Para**: [lista blanca de redes públicas de Office 365](mailto:o365gwlt@microsoft.com)
* **De**: un administrador de inquilinos: el envío de correo electrónico **debe** coincidir con un contacto de administrador global de su espacio empresarial.
* **Asunto de correo electrónico**: Office 365 GCC solicitud de red alta-contoso.onmicrosoft.US (reemplácelo por el nombre del espacio empresarial)

El cuerpo del mensaje debe incluir los datos siguientes:

* El nombre del inquilino de Microsoft Online Services (por ejemplo, contoso.onmicrosoft.com, fabrikam.onmicrosoft.us)
* Una lista de distribución de correo electrónico con la que Microsoft se comunicará para las comunicaciones en curso relacionadas con los cambios en la red o el seguimiento de subredes no válidas
* Indicar si planea usar la coexistencia híbrida de Microsoft Teams con las implementaciones locales
* Sistema de identidad federada URL de acceso externo (por ejemplo, sts.contoso.com) e intervalo de direcciones IP en notación CIDR (por ejemplo, 10.1.1.0/28)
* Dirección URL de la lista de revocación de certificados de PKI local e intervalo de direcciones IP en notación CIDR
* Dirección URL y intervalo de direcciones IP accesibles externamente para la implementación local de Exchange Server en la notación CIDR
* Dirección URL y intervalo de direcciones IP accesibles externamente para la implementación local de Skype empresarial en notación CIDR

Por motivos de seguridad y cumplimiento, tenga en cuenta las siguientes restricciones en su solicitud:

* Hay una limitación de cuatro subredes por espacio empresarial
* Las subredes deben estar en la notación CIDR (por ejemplo, 10.1.1.0/28)
* Los intervalos de subred no pueden ser mayores que/24
* **No se** admiten solicitudes para permitir el acceso a servicios en la nube comercial (commercial Office 365, Google G-Suite, servicios Web de Amazon, etc.)

Una vez que Microsoft ha recibido y aprobado su solicitud, hay un SLA de tres semanas para la implementación y no se le puede acelerar.  Recibirá una confirmación inicial cuando haya recibido su solicitud y una confirmación final una vez que se haya completado.
