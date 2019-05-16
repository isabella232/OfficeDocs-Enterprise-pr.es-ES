---
title: Ajustar el rendimiento de Exchange Online
ms.author: krowley
author: tracyp
manager: laurawi
ms.date: 12/14/2017
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Adm_O365
ms.assetid: 026e83cb-a945-4543-97b0-a8af6e80ac61
description: Este artículo contiene sugerencias generales y vínculos a otros recursos que le indican cómo mejorar el rendimiento de Exchange Online.
ms.openlocfilehash: d736568687da5ffe0ebed5a57a6afa6f93173c54
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070356"
---
# <a name="tune-exchange-online-performance"></a>Ajustar el rendimiento de Exchange Online

Este artículo contiene sugerencias generales y vínculos a otros recursos que le indican cómo mejorar el rendimiento de Exchange Online, especialmente delante de una migración. Este artículo forma parte del proyecto [planeación de red y ajuste del rendimiento para Office 365](https://aka.ms/tune) .
   
## <a name="things-to-consider-in-order-to-improve-exchange-online-performance"></a>Aspectos que se deben tener en cuenta para mejorar el rendimiento de Exchange Online

Para mejorar la velocidad de migración y reducir las restricciones de ancho de banda de la organización para Exchange Online, tenga en cuenta lo siguiente:
  
- **Reducir el tamaño de los buzones.** El tamaño de buzón más pequeño mejora la velocidad de migración. 
    
- **Use las funciones de movimiento de buzones con una implementación híbrida de Exchange.** Con una implementación híbrida de Exchange, correo sin conexión (en forma de. OST) no requieren que se vuelvan a descargar al migrar a Exchange Online. Esto reduce considerablemente los requisitos de ancho de banda de descarga. 
    
- **Programar movimientos de buzones de correo para que se produzcan durante períodos de poco tráfico de Internet y el uso de Exchange local bajo.** Al programar movimientos, las solicitudes de migración se envían al proxy de replicación de buzones y es posible que no tengan lugar inmediatamente. 
    
- **Usar lean ventanas emergentes para Outlook en la Web.** Lean ventanas emergentes proporcionan versiones más pequeñas y intensivas de memoria de determinados mensajes de correo electrónico en Microsoft Edge o Internet Explorer al representar algunos componentes en el servidor. Para obtener más información, vea [use lean ventanas emergentes para reducir la memoria usada al leer mensajes de correo](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf).


## <a name="general-advice"></a>Consejo General

- Asegúrese de que la búsqueda de DNS para outlook.office.com entra en el centro de seguridad de MS en una ubicación de entrada lógica para su ubicación.

- Consultar el almacenamiento en memoria caché de buzones y elegir las opciones adecuadas (re. período de almacenamiento en caché, almacenamiento de buzones compartidos, et cetera).

- Mantenga los datos de Outlook pasando por las conexiones VPN (a una oficina central) antes de pasar a través de Internet.

- Asegúrese de que los datos del buzón cumplan con las limitaciones en la carpeta y los importes de elementos.
    
Para obtener más información acerca del rendimiento de la migración de Exchange, consulte [Office 365 Migration Performance and Best Practices](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57).
  

