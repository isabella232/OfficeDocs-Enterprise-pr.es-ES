---
title: Eliminación de datos de Skype empresarial para Office 365
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
description: Explicación de la eliminación de datos en Skype empresarial.
ms.openlocfilehash: 7c94c5d1ddfb5a8056e139d664627dd1e7bed0de
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997800"
---
# <a name="skype-for-business-data-deletion-in-office-365"></a>Eliminación de datos de Skype empresarial en Office 365

Skype for Business provides archiving of peer-to-peer instant messages, multiparty instant messages, and content upload activities in meetings. The archiving capability requires Exchange and is controlled by the user's Exchange mailbox In-Place Hold attribute, which archives both email and Skype for Business contents.

All archiving in Skype for Business is considered "user-level archiving" because you enable or disable it for one or more specific users or groups of users by creating, configuring, and applying a user-level archiving policy for those users. There is no direct control of archiving settings from within the Skype for Business admin center.

Los siguientes tipos de contenido no se archivan en Skype empresarial:

- Transferencias de archivos de punto a punto
- Audio y vídeo para conferencias y mensajes instantáneos de punto a punto
- Uso compartido de aplicaciones para conferencias y mensajes instantáneos de punto a punto
- Anotaciones de conferencias 

## <a name="meeting-content-retention"></a>Retención del contenido de la reunión

Los clientes que usan Skype empresarial pueden cargar contenido en una reunión de Skype empresarial como datos adjuntos, como presentaciones de PowerPoint, archivos de OneNote y otros archivos. El período de retención para el contenido que se ha cargado en una reunión es el siguiente:

- **Reunión única** : el contenido se conserva durante 15 días a partir del momento en que la última persona abandona la reunión.
- **Reunión recurrente** : el contenido se conserva durante 15 días después de que la última persona abandone la última sesión de la reunión. El temporizador de retención se reinicia si alguien se une a la misma sesión de reunión en 15 días. Por ejemplo, supongamos que una reunión de Skype empresarial está programada para realizarse semanalmente durante un año y se carga un archivo en la reunión durante la primera instancia. Si al menos una persona se une a la sesión de reunión cada semana, el archivo se conserva en los servidores de Skype empresarial online durante todo el año más 15 días después de que la última persona abandone la última reunión de la serie.
- **Reunirse ahora** : el contenido se conserva durante 8 horas después de la hora de finalización de la reunión.

> [!NOTE]
> Si un usuario está deshabilitado o sin licencia (por ejemplo, si **msRTCSIP-userEnabled** está establecido en *false*) y, a continuación, vuelve a estar habilitado o con licencia, no se conservará el contenido de la reunión.

## <a name="meeting-expiration"></a>Expiración de la reunión

Los usuarios pueden tener acceso a una reunión específica una vez finalizada la reunión, siempre que se cumplan los siguientes períodos de tiempo de expiración:

- **Reunión única** : la reunión expira 14 días después de la hora de finalización programada de la reunión.
- **Reunión periódica con fecha de finalización** : la reunión expira 14 días después de la hora de finalización programada de la última ocurrencia de la reunión.
- **Reunirse ahora** : reunión expira después de 8 horas.

## <a name="whiteboard-collaboration"></a>Colaboración en pizarra

Las anotaciones que se hagan en las pizarras podrán verlas todos los participantes. Al guardar una pizarra, la pizarra y todas las anotaciones se almacenarán en un servidor de Skype empresarial, y se conservará en el servidor de acuerdo con las directivas de expiración del contenido de la reunión establecidas por el administrador.

## <a name="audio-test-service"></a>Servicio de prueba de audio

Una muestra breve (aproximadamente 5 segundos) de la voz se graba durante la llamada de servicio de prueba de audio. La muestra de voz se usa para comprobar o comprobar la calidad de sonido de la llamada de Skype empresarial en función de la calidad de la grabación. Cuando finaliza la llamada del servicio de prueba de audio, se elimina la muestra de voz.

## <a name="persistent-group-chat"></a>Chat de grupo persistente

El chat de grupo persistente almacena el contenido de las conversaciones de chat en grupo. Si se habilita, el administrador puede controlar el período de retención, el servidor en el que se almacena esta información, si el historial de chat de grupo se archiva para cumplimiento o para otros fines, y administrar o modificar las propiedades de un salón. Los usuarios con diferentes roles tienen un acceso diferente a los datos persistentes, de la siguiente manera:

- Los administradores pueden eliminar contenido antiguo (por ejemplo, contenido publicado antes de una fecha determinada) de cualquier salón de chat para evitar que el tamaño de la base de datos crezca en gran medida. O bien pueden quitar o reemplazar los mensajes considerados inapropiados para un salón de chat determinado (o considerados inadecuados).
- Los usuarios finales, incluidos los autores de mensajes, no pueden eliminar contenido de ningún salón de chat.
- Los administradores de salones de chat pueden deshabilitar las salas pero no eliminar las salas. Solo los administradores pueden eliminar un salón de chat una vez creado.