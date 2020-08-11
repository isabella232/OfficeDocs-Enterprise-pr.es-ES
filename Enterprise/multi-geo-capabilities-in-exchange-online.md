---
title: Multi-Geo de Exchange
ms.reviewer: adwood
ms.author: chrisda
author: chrisda
manager: serdars
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
localization_priority: Normal
description: Obtenga información sobre las funcionalidades multigeográficas en Exchange Online, como limitaciones de características y ubicación de buzones.
ms.openlocfilehash: 8d9432fdade9d10581d386c2ab01e96f1b2cdda6
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606816"
---
# <a name="multi-geo-capabilities-in-exchange-online"></a>Capacidades multigeográficas en Exchange Online

En un entorno multigeográfico, puede seleccionar la ubicación del contenido del buzón de Exchange Online (datos almacenados) de cada usuario.

Puede colocar buzones en ubicaciones geográficas satélite:

- Creando un nuevo buzón de Exchange Online directamente en una ubicación geográfica satélite.

- Moviendo un buzón de Exchange Online existente a una ubicación geográfica satélite si cambia la ubicación de datos preferida del usuario.

- Incorporando un buzón de una organización de Exchange local directamente en una ubicación geográfica satélite. 

## <a name="mailbox-placement-and-moves"></a>Colocación y movimiento de buzones

Cuando Microsoft complete los requisitos previos de configuración multigeográfica, Exchange Online respetará el atributo **PreferredDataLocation** de los objetos de usuario de Azure AD.

Exchange Online sincroniza la propiedad **PreferredDataLocation** de Azure AD en la propiedad **MailboxRegion** en el servicio de directorio de Exchange Online. El valor de **MailboxRegion** determina la ubicación geográfica donde se colocarán los buzones de usuario y cualquier archivo asociado. No es posible configurar el buzón principal y los de archivo de un usuario para que residan en ubicaciones geográficas distintas. Solo puede configurarse una ubicación geográfica por objeto de usuario.

- Cuando **PreferredDataLocation** está configurado en un usuario con un buzón existente, el buzón se colocará en una cola de reubicación y se moverá automáticamente a la ubicación geográfica especificada.

- Cuando **PreferredDataLocation** está configurado en un usuario sin un buzón existente, al aprovisionar el buzón, se aprovisionará en la ubicación geográfica especificada.

- Cuando **PreferredDataLocation** no está especificada en un usuario, al aprovisionar el buzón, se aprovisionará en la ubicación geográfica central.

- Si el código**PreferredDataLocation** no es correcto (por ejemplo, un tipo de NAN en lugar de NAM), el buzón se aprovisionará en la ubicación geográfica central.

**Nota**: las funciones de Multi-geo y las reuniones hospedadas regionalmente por Skype Empresarial Online utilizan la propiedad **PreferredDataLocation** en los objetos de usuario para buscar servicios. Si configura los valores de **PreferredDataLocation** en los objetos de usuario para reuniones hospedadas regionalmente, el buzón de correo de esos usuarios se moverá automáticamente a la ubicación geográfica especificada después de que se habilite en el espacio empresarial de Microsoft 365.

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a>Limitación de funciones para empresas multigeográficas en Exchange Online

- Características de seguridad y cumplimiento (por ejemplo, auditoría y eDiscovery) que están disponibles en el centro de administración de Exchange (EAC) no están disponibles en las organizaciones multigeográficas. En su lugar, debe utilizar el [Centro de seguridad y cumplimiento de Microsoft 365](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) para configurar las características de seguridad y cumplimiento.

- Los usuarios de Outlook para Mac pueden experimentar una pérdida temporal de acceso a su carpeta de archivo en línea mientras mueven su buzón de correo a una nueva ubicación geográfica. Esta condición se produce cuando los buzones de correo principal y de archivo del usuario se encuentran en diferentes ubicaciones geográficas, ya que los movimientos de buzones entre ubicaciones geográficas se pueden completar en diferentes momentos.

- Los usuarios no pueden compartir *carpetas del buzón* entre distintas ubicaciones geográficas de Outlook en la Web (anteriormente conocida como Outlook Web App u OWA). Por ejemplo, un usuario de la Unión Europea no puede usar Outlook en la Web para abrir una carpeta compartida en un buzón que se encuentra en Estados Unidos. Pero los usuarios de Outlook en la Web pueden abrir *otros buzones* en diferentes ubicaciones geográficas utilizando una ventana de explorador separada, como se describe en [Abrir el buzón de otra persona en una ventana de navegador separada en Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).

  **Nota**: el uso compartido de carpetas de buzones entre distintas ubicaciones geográficas es compatible con Outlook en Windows.

- Las carpetas públicas se admiten en organizaciones multigeográficas. Sin embargo, las carpetas públicas deben permanecer en la ubicación geográfica central. No puede mover carpetas públicas a ubicaciones geográficas satélite.

- En un entorno multigeográfico, la auditoría de buzón multigeográfico no es compatible. Por ejemplo, si se asignan permisos a un usuario para tener acceso a un buzón compartido en una ubicación geográfica diferente, las acciones de buzón que realiza el usuario no se registran en el registro de auditoría del buzón de correo compartido. Para más información, consulte [Administrar auditoría del buzón](https://docs.microsoft.com/microsoft-365/compliance/enable-mailbox-auditing?view=o365-worldwide)..
