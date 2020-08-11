---
title: Migraciones de buzones de Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: Este artículo contiene un breve resumen sobre las migraciones de buzones de correo de Microsoft 365 y una lista de los cmdlets que se usan para las migraciones.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: c28ab1702e6a81826ce77bf0b4ef30e4d24832b4
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605572"
---
# <a name="microsoft-365-mailbox-migrations"></a>Migraciones de buzones de Microsoft 365

Con una implementación híbrida basada en Exchange, los clientes pueden elegir entre mover buzones de Exchange locales a una organización de [Exchange Online](https://docs.microsoft.com/Exchange/exchange-online) o mover buzones de correo de Exchange Online a una organización [local de Exchange](https://docs.microsoft.com/Exchange/exchange-server) . Los lotes de migración se usan cuando se mueven buzones de correo entre organizaciones locales y de Exchange Online.

Los clientes pueden revisar las estadísticas y otra información sobre las migraciones de buzones de correo con los siguientes cmdlets:

- [Get-MoveRequestStatistics](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MoveRequestStatistics?view=exchange-ps): proporciona estadísticas predeterminadas para un buzón de usuario, que incluye el estado, el tamaño del buzón, el tamaño del buzón de archivo y el porcentaje completado.
- [Get-Mailbox](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Get-Mailbox?view=exchange-ps
): proporciona una lista resumida de los objetos de buzón y los atributos de la organización.
- [Get-recipient](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient?view=exchange-ps): proporciona una lista de objetos existentes habilitados para correo, como buzones de correo, usuarios de correo, contactos y grupos de distribución.
- [Get-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MoveRequest?view=exchange-ps): proporciona un estado detallado de una migración de buzones de correo en curso.
- [Get-MigrationUser](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MigrationUser?view=exchange-ps): proporciona información sobre los usuarios de migración y movimiento de buzones.
- [Get-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MigrationBatch?view=exchange-ps): proporciona información sobre el estado del lote de migración actual.
- [Get-MigrationUserStatistics](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MigrationUserStatistics?view=exchange-ps): proporciona información detallada sobre el estado de la migración de un usuario específico.
- [Get-MailboxStatistics](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Get-MailboxStatistics?view=exchange-ps): proporciona información acerca de los buzones de correo, como el tamaño, el número de mensajes y la hora del último acceso.

Para obtener más información acerca de los cmdlets, consulte [Move and Migration cmdlets in Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps).
