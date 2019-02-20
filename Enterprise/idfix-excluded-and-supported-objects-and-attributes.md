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
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: Enumera los atributos que se excluyen y son compatibles con la herramienta IdFix.
ms.openlocfilehash: d6b7aac023e9fe96b8308483322e718937ab1355
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085089"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a>Objetos y atributos admitidos y excluidos en IdFix
Hay dos conjuntos de reglas que mantiene IdFix: multiempresa y dedicado/ITAR. Por el momento, los dos conjuntos de reglas excluyen los mismos objetos, atributos y valores de atributos de la búsqueda. Esto puede cambiar en las próximas versiones.
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a>Exclusiones de errores dedicados y multiempresa que usa IdFix
En esta sección se enumeran los objetos, los atributos y los valores que se excluyen en IdFix de su búsqueda en el directorio. El asterisco (\*) es un carácter comodín que se puede sustituir por otros caracteres.
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a>Objetos, atributos y valores excluidos durante una búsqueda de IdFix

|**Exclusión**|**Ejemplo**|
|:-----|:-----|
|Elección\* |Administrador |
|CAS_ {\*  |CAS_{fe35fc98e69e4d08} |
|DiscoverySearchMailbox\*  |DiscoverySearchMailbox  |
|FederatedEmail\* |FederatedEmail. *GUID* |
|"\* ||
|HTTPConnector\*  |HTTPConnector |
|krbtgt\* |MS-DS-KrbTgt-Link |
|cuenta\* |IUSR _ *nombreEquipo* |
|IWAM\*  |IWAM _ *nombreEquipo* |
|msol\* |MSOL_AD_SYNC |
|admisión\* ||
|SystemMailbox\* |SystemMailbox { *GUID* }|
|WWIOadmini\*  ||
|\*$ ||
|distinguishedName contiene "\0ACNF:"|"\0ACNF: *GUID* " |
|Object contains the IsCriticalSystemObject attribute |Consulte [atributos isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169). |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a>Objetos y atributos multiempresa y dedicados que comprueba IdFix
Los atributos que IdFix comprueba para detectar errores se describen en la sección "preparación de objetos y atributos de directorio" en [preparar atributos de directorio para la sincronización con Office 365 mediante la herramienta IdFix](prepare-directory-attributes-for-synch-with-idfix.md).
  

