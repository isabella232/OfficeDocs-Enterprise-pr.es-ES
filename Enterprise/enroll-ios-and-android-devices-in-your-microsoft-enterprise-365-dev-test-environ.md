---
title: Inscriba los dispositivos iOS y Android en el entorno de desarrollo y prueba de Microsoft 365 Enterprise
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/20/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: 'Resumen: Use esta guía de laboratorio de prueba para inscribirse dispositivos en su entorno de desarrollo y prueba de Microsoft 365 y administrar de forma remota.'
ms.openlocfilehash: e4b8491a70d0d0177e0a434d228136243201e788
ms.sourcegitcommit: c3869a332512dd1cc25cd5a92a340050f1da0418
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/20/2018
ms.locfileid: "20720416"
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-enterprise-devtest-environment"></a>Inscriba los dispositivos iOS y Android en el entorno de desarrollo y prueba de Microsoft 365 Enterprise

 **Resumen:** Use esta guía de laboratorio de prueba para inscribirse dispositivos en su entorno de desarrollo y prueba de Microsoft 365 y administrar de forma remota.
  
El conjunto de aplicaciones de movilidad de Microsoft Enterprise (EMS) ayuda a mantener la productividad con sus aplicaciones favoritas y dispositivos durante la protección de datos de la organización de los empleados. Para obtener más información, vea [Enterprise movilidad + seguridad (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).
  
Si necesita aplicar la seguridad en el nivel de dispositivo, debe inscribirse dispositivos en Microsoft Intune. Inscripción de dispositivo no sólo le ayuda a administrar los dispositivos de propiedad de la organización, pero también personal (BYOD) y dispositivos compartidos, dependiendo de la organización del departamento legal directivas.
  
Siguiendo las instrucciones proporcionadas en este artículo, podrá inscribirse y capacidades de administración de dispositivo móvil básica para iOS y Android dispositivos de prueba en el entorno de desarrollo y prueba de Microsoft 365.
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a>Fase 1: Crear el entorno de desarrollo y prueba de Microsoft 365

Siga las instrucciones que aparecen en el [entorno de desarrollo o prueba de la empresa de 365 de Microsoft](the-microsoft-365-enterprise-dev-test-environment.md).
  
## <a name="phase-2-enroll-your-ios-and-android-devices"></a>Fase 2: Inscribirse los dispositivos Android y iOS

En primer lugar, use las instrucciones de [instalar e inicie sesión en la aplicación de Portal de empresa](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) para personalizar la aplicación de Portal de empresa de Microsoft Intune para su entorno de prueba.

A continuación, siga las instrucciones de [Configurar el acceso a los recursos de empresa](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) para inscribirse en un dispositivo de iOS.

A continuación, siga las instrucciones de [inscripción su dispositivo Android en Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) para inscribirse en un dispositivo Android.

## <a name="phase-3-manage-your-ios-and-android-devices-remotely"></a>Fase 3: Administrar su iOS y Android dispositivos de forma remota

Microsoft Intune proporciona capacidades de restablecimiento de bloqueo remoto y código de acceso. Si alguien pierde su dispositivo, puede bloquear el dispositivo de forma remota. Si alguien olvida su código de acceso, puede restablecer de forma remota.
  
Para bloquear una iOS o Android dispositivo de forma remota:

1. Inicie sesión en el portal de Azure en [https://portal.azure.com](https://portal.azure.com) con las credenciales de su cuenta de administrador global.
2. Haga clic en **todos los servicios**, escriba **Intune**y, a continuación, haga clic en **Intune**.
3. Haga clic en **dispositivos > todos los dispositivos**.
4. En la lista de dispositivos, haga clic en un dispositivo Android o iOS y, a continuación, haga clic en la acción de **bloqueo remoto** .

    
Para restablecer el código de acceso de forma remota:

1. Si es necesario, inicie sesión en el portal de Azure en [https://portal.azure.com](https://portal.azure.com) con las credenciales de su cuenta de administrador global.
2. Haga clic en **todos los servicios**, escriba **Intune**y, a continuación, haga clic en **Intune**.
3. Haga clic en **dispositivos > todos los dispositivos**.
4. En la lista de los dispositivos de administrar, haga clic en un dispositivo Android o iOS y elija **... Más**. A continuación, elija la acción **quitar el código de acceso de** dispositivo remota.

Para realizar otras pruebas, consulte [acciones de dispositivo disponible](https://docs.microsoft.com/intune/device-management#available-device-actions).

    

> [!TIP]
> Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual de todos los artículos en la pila de la Guía del entorno de pruebas de One Microsoft Cloud.
  
## <a name="see-also"></a>Consulte también

[Entorno de pruebas y desarrollo de Microsoft 365 Enterprise](the-microsoft-365-enterprise-dev-test-environment.md)
  
[Directivas MAM para sus entornos de desarrollo y prueba de Microsoft 365](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[Guías de entorno de pruebas de adopción de la nube (TLG)](cloud-adoption-test-lab-guides-tlgs.md)

[Movilidad de la empresa + seguridad (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


