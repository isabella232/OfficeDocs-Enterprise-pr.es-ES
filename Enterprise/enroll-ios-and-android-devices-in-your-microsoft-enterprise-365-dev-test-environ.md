---
title: Inscribirse iOS y Android dispositivos en su entorno de desarrollo y prueba de Microsoft Enterprise 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/14/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: 'Resumen: Use esta guía de laboratorio de prueba para inscribirse dispositivos en su entorno de desarrollo y prueba de Microsoft 365 y administrar de forma remota.'
ms.openlocfilehash: 8765a7ffb1bff1f257d7cd1ce5181561c2cf0080
ms.sourcegitcommit: 771f227d3049498fcbd7cfbeaf649e3d77e73c86
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-devtest-environment"></a>Inscribirse iOS y Android dispositivos en su entorno de desarrollo y prueba de Microsoft Enterprise 365

 **Resumen:** Use esta guía de laboratorio de prueba para inscribirse dispositivos en su entorno de desarrollo y prueba de Microsoft 365 y administrar de forma remota.
  
El conjunto de aplicaciones de movilidad de Microsoft Enterprise (EMS) ayuda a mantener la productividad con sus aplicaciones favoritas y dispositivos durante la protección de datos de la organización de los empleados. Para obtener más información, vea [Enterprise movilidad + seguridad (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).
  
Si necesita aplicar la seguridad en el nivel de dispositivo, debe inscribirse dispositivos en Microsoft Intune. Inscripción de dispositivo no sólo le ayuda a administrar los dispositivos de propiedad de la organización, pero también personal (BYOD) y dispositivos compartidos, dependiendo de la organización del departamento legal directivas.
  
Siguiendo las instrucciones proporcionadas en este artículo, podrá inscribirse y capacidades de administración de dispositivo móvil básica para iOS y Android dispositivos de prueba en el entorno de desarrollo y prueba de Microsoft 365.
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a>Fase 1: Crear el entorno de desarrollo y prueba de Microsoft 365

Siga las instrucciones que aparecen en el [entorno de desarrollo o prueba de la empresa de 365 de Microsoft](the-microsoft-365-enterprise-dev-test-environment.md).
  
## <a name="phase-2-enroll-your-ios-and-android-devices"></a>Fase 2: Inscribirse los dispositivos Android y iOS

En primer lugar, use las instrucciones de [instalar e inicie sesión en la aplicación de Portal de empresa](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) para personalizar la aplicación de Portal de empresa de Microsoft Intune para el inquilino de desarrollo o prueba.

A continuación, siga las instrucciones de [Configurar el acceso a los recursos de empresa](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) para inscribirse en un dispositivo de iOS.

A continuación, siga las instrucciones de [inscripción su dispositivo Android en Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) para inscribirse en un dispositivo Android.

## <a name="phase-2-manage-your-ios-and-android-devices-remotely"></a>Fase 2: Administrar su iOS y Android dispositivos de forma remota

Microsoft Intune proporciona capacidades de restablecimiento de código de acceso y bloqueo remoto. Si alguien pierde su dispositivo, puede bloquearlo de forma remota. Si alguien olvida su código de acceso, puede eliminar el código de forma remota.
  
Para bloquear de forma remota un dispositivo iOS:
  
1.  Abra una nueva ficha y vaya a http://manage.microsoft.com (si es necesario). 

2.  Desde la consola de administración de Microsoft Intune del explorador, haga clic en **grupos** en el panel de navegación izquierdo.

3. En el panel **grupos** , abra **todos los dispositivos > dispositivos móviles todos > todos los dispositivos directa administrado**.
    
4. En el panel de **Todos los dispositivos administrados de directa** , haga clic en la ficha **dispositivos** .
    
5. En la lista de dispositivos, haga clic en su dispositivo iOS.  
    
6. En su dispositivo iOS, asegúrese de que está en la pantalla principal.  
    
7. Desde el equipo de administración, en la barra de tareas, haga clic en **tareas remotas > bloqueo remoto**. Vea su dispositivo iOS tal y como lo pasa a la pantalla de bloqueo.
    
Para eliminar el código de acceso:
  
1. Desde el equipo de administración, en el panel de **Todos los dispositivos administrados de directa** , haga clic en la ficha **dispositivos** .
    
2. En la lista, haga clic en el dispositivo iOS. En la barra de tareas, haga clic en **tareas remotas > Restablecer el código de acceso**. Espere un minuto.
    
3. Desde su dispositivo iOS, desbloquearlo y observe que ya no es un código de acceso. Para cambiar la copia el código de acceso, vaya a **configuración**y, a continuación, **el código de acceso**.
    
Para bloquear de forma remota un dispositivo Android:
  
1. Desde la consola de administración de Microsoft Intune del explorador, haga clic en **grupos** en el panel de navegación izquierdo.
    
2. En el panel **grupos** , abra **todos los dispositivos > dispositivos móviles todos > todos los dispositivos directa administrado**.
    
3. En el panel de **Todos los dispositivos administrados de directa** , haga clic en la ficha **dispositivos** .
    
4. En la lista de dispositivos, haga clic en su dispositivo Android.  
    
5. En su dispositivo Android, asegúrese de que está en la pantalla principal.  
    
6. Desde el equipo de administración, en la barra de tareas, haga clic en **tareas remotas > bloqueo remoto**. Cuando se le solicite, haga clic en **Sí**.
    
7. Observe su dispositivo Android mientras cambia a la pantalla de bloqueo.
    
Cuando se restablece el código de acceso para dispositivos Android, el portal de administración Intune genera y configura un código de acceso seguro.
  
Para restablecer el código de acceso de forma remota:
  
1. Desde el equipo de administración, en la ficha de consola de administración de Microsoft Intune del explorador, en el panel de **Todos los dispositivos administrados de directa** , haga clic en su dispositivo Android.
    
2. En la barra de tareas, haga clic en **tareas remotas > Restablecer el código de acceso**.
    
3. En la **tarea remota: restablecer el código de acceso** el mensaje, haga clic en **Sí**. Espere un minuto.
    
4. En el panel de **Todos los dispositivos administrados de directa** , haga clic en **Ver propiedades**.
    
5. Bajo **Restablecer el código de acceso**, tenga en cuenta la nueva contraseña.
    
6. En su dispositivo Android, introduzca el nuevo código de acceso en la pantalla de bloqueo.  
    
7. Para cambiar el código de acceso atrás, vaya a **configuración**, puntee en el **dispositivo**, puntee en la **pantalla de bloqueo**, escriba la nueva contraseña, puntee en **bloqueo de pantalla**y, a continuación, en su elección para el código de acceso.
    

> [!TIP]
> Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual de todos los artículos en la pila de la Guía del entorno de pruebas de One Microsoft Cloud.
  
## <a name="see-also"></a>Consulte también

[Entorno de pruebas y desarrollo de Microsoft 365 Enterprise](the-microsoft-365-enterprise-dev-test-environment.md)
  
[Directivas MAM para sus entornos de desarrollo y prueba de Microsoft 365](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[Guías de entorno de pruebas de adopción de la nube (TLG)](cloud-adoption-test-lab-guides-tlgs.md)

[Movilidad de la empresa + seguridad (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


