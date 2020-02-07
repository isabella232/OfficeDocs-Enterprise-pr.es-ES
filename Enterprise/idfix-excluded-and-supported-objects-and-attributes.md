---
title: Objetos y atributos admitidos y excluidos en IdFix
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: Enumera los atributos que se excluyen y son compatibles con la herramienta IdFix.
ms.openlocfilehash: 0203f47864dc4222cd2f95a4e67b2f10bec44f71
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840147"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a>Objetos y atributos admitidos y excluidos en IdFix

*Este artículo se aplica tanto a Office 365 Enterprise como a Microsoft 365 Enterprise.*

Hay dos conjuntos de reglas que se mantienen en IdFix; Multiinquilino y dedicado/ITAR. En este momento, los dos conjuntos de reglas excluyen los mismos objetos, atributos y valores de atributo de su búsqueda. Esto puede cambiar en futuras versiones.
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a>Exclusiones de error dedicadas y multiinquilino usadas por IdFix
En esta sección se enumeran los objetos, los atributos y los valores que se excluyen en IdFix de su búsqueda en el directorio. El asterisco (\*) es un carácter comodín que se puede sustituir por otros caracteres.
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a>Objetos, atributos y valores excluidos durante una búsqueda de IdFix

|**Exclusión**|**Ejemplo**|
|:-----|:-----|
|Elección\* |Administrador |
|CAS_ {\*  |CAS_ {fe35fc98e69e4d08} |
|DiscoverySearchMailbox\*  |DiscoverySearchMailbox  |
|FederatedEmail\* |FederatedEmail. *GUID* |
|Guest\* ||
|HTTPConnector\*  |HTTPConnector |
|krbtgt\* |MS-DS-KrbTgt-Link |
|iusr_\* |iusr_ *MachineName* |
|IWAM\*  |IWAM_ *MachineName* |
|msol\* |MSOL_AD_SYNC |
|support_\* ||
|SystemMailbox\* |SystemMailbox { *GUID* }|
|WWIOadmini\*  ||
|\*$ ||
|distinguishedName contiene "\0ACNF:"|"\0ACNF: *GUID* " |
|El objeto contiene el atributo IsCriticalSystemObject |Consulte [atributos isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169). |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a>Atributos y objetos dedicados multiinquilinos y dedicados comprobados por IdFix
Los atributos que IdFix comprueba para detectar errores se describen en la sección "preparación de objetos y atributos de directorio" en [preparar atributos de directorio para la sincronización con Office 365 mediante la herramienta IdFix](prepare-directory-attributes-for-synch-with-idfix.md).
  

