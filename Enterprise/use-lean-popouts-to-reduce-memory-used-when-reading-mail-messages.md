---
title: Use popouts lean para reducir la memoria usada al leer los mensajes de correo
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 3/8/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: a6d6ba01-2562-4c3d-a8f1-78748dd506cf
description: Este artículo contiene información para mejorar el rendimiento de descarga de mensaje en Outlook en el web.
ms.openlocfilehash: 07c427793c1cd60d25020a1ab49855ed1bc77cf6
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542777"
---
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a>Use popouts lean para reducir la memoria usada al leer los mensajes de correo

Este artículo contiene información para mejorar el rendimiento de descarga de mensaje en Outlook en el web. En este artículo es parte del proyecto de [Diseño de la red y ajuste del rendimiento de Office 365](https://aka.ms/tune) .
   
Como administrador global de Office 365, puede configurar Outlook en la web para ofrecer *popouts lean* , más pequeña y menos versión con uso intensivo de memoria de determinados mensajes de correo electrónico en Microsoft Edge o Internet Explorer. Cuando se configuran popouts lean para Outlook en la web, se cargan representan componentes del servidor que optimizar el rendimiento. 
  
> [!NOTE]
> A partir de marzo de 2018, lean popouts actualmente no están disponibles para los mensajes que especifican restricciones de derechos de uso, como Information Rights Management (IRM). 
  
Estas características seguirán funcionando en la ventana principal, pero no están disponibles en popouts lean:
  
- Complementos de Outlook
    
- Skype para la presencia de negocio
    
 **Para configurar lean popouts para todos los usuarios dentro de la organización de Office 365**
  
1. [Conectarse a Exchange Online mediante PowerShell remoto](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).
    
2. Ejecute el cmdlet [Set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) con el parámetro LeanPopoutEnabled como sigue: 
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

    Por ejemplo, para habilitar lean popouts para todos los usuarios de su organización:
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

    Para deshabilitar lean popouts para todos los usuarios de su organización:
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```


