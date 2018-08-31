---
title: Objetos y atributos admitidos y excluidos en IdFix
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2016
ms.audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.custom: Adm_O365
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: Se enumeran los atributos que son compatibles con la herramienta IdFix y excluidos.
ms.openlocfilehash: de8d57bb8ad9a3097ec9da3ff2a485095a140a42
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542850"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a>Objetos y atributos admitidos y excluidos en IdFix
Hay dos conjuntos de reglas que mantiene IdFix: multiempresa y dedicado/ITAR. Por el momento, los dos conjuntos de reglas excluyen los mismos objetos, atributos y valores de atributos de la búsqueda. Esto puede cambiar en las próximas versiones.
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a>Exclusiones de errores dedicados y multiempresa que usa IdFix
En esta sección se enumera los objetos, atributos y valores que IdFix se excluye de la búsqueda del directorio. El asterisco (\*) es un carácter comodín que se puede sustituir por otros caracteres.
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a>Objetos, atributos y valores excluidos durante una búsqueda de IdFix

|**Exclusión**|**Ejemplo**|
|:-----|:-----|
|Derechos\* |Administrador |
|{CAS_\*  |CAS_{fe35fc98e69e4d08} |
|DiscoverySearchMailbox\*  |DiscoverySearchMailbox  |
|FederatedEmail\* |FederatedEmail. *GUID* |
|Invitado\* ||
|HTTPConnector\*  |HTTPConnector |
|krbtgt\* |MS-DS-KrbTgt-vínculo |
|IUSR_\* |IUSR_ *nombreEquipo* |
|IWAM\*  |IWAM_ *nombreEquipo* |
|msol\* |MSOL_AD_SYNC |
|Support_\* ||
|SystemMailbox\* |SystemMailbox { *GUID* }|
|WWIOadmini\*  ||
|\*$ ||
|distinguishedName contiene "\0ACNF:"|"\0ACNF: *GUID* " |
|Object contains the IsCriticalSystemObject attribute |Vea el [atributo isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169). |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a>Objetos y atributos multiempresa y dedicados que comprueba IdFix
Se describen los atributos que se comprueban los errores de idfix en la sección "Objeto y atributo preparación de Active Directory" en [la preparación atributos de Active directory para la sincronización con Office 365 mediante el uso de la herramienta IdFix](prepare-directory-attributes-for-synch-with-idfix.md).
  

