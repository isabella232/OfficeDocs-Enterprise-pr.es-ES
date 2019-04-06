---
title: Multi-Geo de Exchange
ms.author: chrisda
author: chrisda
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: Obtenga más información sobre las funcionalidades multigeográficas en Exchange Online.
ms.openlocfilehash: 60d25cab08ada195d1b189b30bdce8ea505f1d19
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2019
ms.locfileid: "30931779"
---
# <a name="multi-geo-capabilities-in-exchange-online"></a>Capacidades multigeográficas de Exchange Online

En un entorno multigeográfico, puede seleccionar la ubicación del contenido del buzón de correo de Exchange Online (datos en reposo) por cada usuario.

Puede poner buzones de correo en ubicaciones de satélite:

- Crear un nuevo buzón de correo de Exchange online directamente en una ubicación de satélite

- Mover un buzón de Exchange Online existente a una ubicación satélite cambiando la ubicación de datos preferida del usuario

- Incorporación de un buzón de correo desde una organización local de Exchange directamente en una ubicación de satélite

## <a name="mailbox-placement-and-moves"></a>Colocación y desplazamiento de buzones
Una vez que Microsoft complete los pasos de configuración multigeográfico de requisitos previos, Exchange Online admitirá el atributo **PreferredDataLocation** en objetos de usuario en Azure ad.

Exchange Online sincroniza la propiedad **PreferredDataLocation** de Azure ad con la propiedad **MailboxRegion** del servicio de directorio de Exchange Online. El valor de **MailboxRegion** determina la geoárea geográfica en la que se colocarán los buzones de usuario y los buzones de archivo asociados. No se puede configurar el buzón de correo principal de un usuario y los buzones de archivo para que residan en ubicaciones geográficas diferentes. Solo se puede configurar una ubicación geográfica por cada objeto de usuario.

- Cuando **PreferredDataLocation** se configura en un usuario con un buzón existente, el buzón se coloca en una cola de reubicación y se mueve automáticamente a la ubicación geográfica especificada. 

- Cuando se configura **PreferredDataLocation** en un usuario sin un buzón existente, al aprovisionar el buzón de correo, se aprovisionará en la ubicación geográfica especificada. 

- Cuando no se especifica **PreferredDataLocation** en un usuario, al aprovisionar el buzón, se aprovisionará en la ubicación central.

- Si el código de **PreferredDataLocation** es incorrecto (por ejemplo, un tipo Nan en lugar de Nam), el buzón de correo se aprovisionará en la ubicación central.

**Nota**: las capacidades multigeográficas y las reuniones hospedadas en el país de Skype empresarial online usan la propiedad **PreferredDataLocation** en objetos de usuario para ubicar los servicios. Si configura valores de **PreferredDataLocation** en objetos de usuario para reuniones hospedadas de forma regional, el buzón de correo de dichos usuarios se moverá automáticamente a la ubicación geográfica especificada después de habilitar multigeográfico en el inquilino de Office 365.

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a>Limitaciones de características para multi-geo en Exchange Online

1. Las características de seguridad y cumplimiento (por ejemplo, la auditoría y la exhibición de documentos electrónicos) que están disponibles en el centro de administración de Exchange (EAC) no están disponibles en organizaciones multigeográficas. En su lugar, debe usar el [centro de cumplimiento de & de seguridad de Office 365](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) para configurar las características de cumplimiento y seguridad.

2. Los usuarios de Outlook para Mac pueden experimentar una pérdida temporal de acceso a su carpeta de archivo en línea mientras mueve su buzón de correo a una nueva ubicación geográfica. Esta condición se produce cuando los buzones de correo principales y de archivo del usuario se encuentran en ubicaciones geográficas diferentes, ya que los movimientos entre buzones de correo geográfico pueden completarse en diferentes momentos.

3. Los usuarios no pueden compartir carpetas de buzones de *correo* entre ubicaciones geográficas en Outlook en la web (anteriormente conocido como Outlook Web App o OWA). Por ejemplo, un usuario de la Unión Europea no puede usar Outlook en la web para abrir una carpeta compartida en un buzón que se encuentra en los Estados Unidos. Sin embargo, los usuarios de Outlook en la web pueden abrir *otros buzones de correo* en diferentes GEOS mediante una ventana del explorador independiente, como se describe en [abrir el buzón de otra persona en una ventana del explorador independiente en Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).

    **Nota**: el uso compartido de carpetas entre buzones de correo entre bosques se admite en Outlook en Windows.

