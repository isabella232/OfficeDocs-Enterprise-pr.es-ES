---
title: Usar lean ventanas emergentes para reducir la memoria usada al leer mensajes de correo
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/3/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: a6d6ba01-2562-4c3d-a8f1-78748dd506cf
f1.keywords:
- NOCSH
description: Este artículo contiene información para mejorar el rendimiento de la descarga de mensajes en Outlook en la Web.
ms.openlocfilehash: 49b570da9092ce4fc857757a7da72b2a81fd0090
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843911"
---
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a>Usar lean ventanas emergentes para reducir la memoria usada al leer mensajes de correo

Este artículo contiene información para mejorar el rendimiento de la descarga de mensajes en Outlook en la Web. Este artículo forma parte del proyecto [planeación de red y ajuste del rendimiento para Office 365](https://aka.ms/tune) .
  
Como administrador global de Office 365, puede configurar Outlook en la web para que ofrezca _ventanas emergentes lean_, una versión más pequeña y que consume menos memoria de determinados mensajes de correo electrónico en Microsoft Edge o Internet Explorer. Cuando se configuran los ventanas emergentes Lean para Outlook en la web, se cargan los componentes representados del lado servidor que optimizan el rendimiento.
  
> [!NOTE]
> A partir del 2018 de marzo, los ventanas emergentes lean no están disponibles para los mensajes que especifican restricciones de derechos de uso, como Information Rights Management (IRM).
  
Estas características seguirán funcionando en la ventana principal, pero no estarán disponibles en Lean ventanas emergentes:
  
- Complementos de Outlook
  
- Presencia de Skype empresarial
  
## <a name="to-configure-lean-popouts-for-all-users-within-your-office-365-organization"></a>Para configurar ventanas emergentes eficaces para todos los usuarios de la organización de Office 365
  
1. [Conéctese a Exchange online mediante PowerShell remoto](https://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).
  
2. Ejecute el cmdlet [set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) con el parámetro LeanPopoutEnabled de la siguiente manera:

  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

  Por ejemplo, para habilitar la ventanas emergentes Lean para todos los usuarios de la organización:
  
  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

  Para deshabilitar la ventanas emergentes eficiente para todos los usuarios de la organización:

  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```
