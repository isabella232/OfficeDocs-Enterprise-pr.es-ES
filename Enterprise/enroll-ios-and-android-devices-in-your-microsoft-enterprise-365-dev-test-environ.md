---
title: Inscriba los dispositivos iOS y Android en el entorno de desarrollo y prueba de Microsoft 365 Enterprise
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
ms.openlocfilehash: a5d43a0ef3ed090f84c8415de3ac26f53fdafe0a
ms.sourcegitcommit: c23b95d32a865e45be7843f38a1f23b5693ba76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2018
ms.locfileid: "20188108"
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-enterprise-devtest-environment"></a>Inscriba los dispositivos iOS y Android en el entorno de desarrollo y prueba de Microsoft 365 Enterprise

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

3. En el panel **Grupos**, abra **Todos los dispositivos > Todos los dispositivos móviles > Todos los dispositivos administrados directamente**.
    
4. En el panel **Todos los dispositivos administrados directamente**, haga clic en la pestaña **Dispositivos**.
    
5. En la lista de dispositivos, haga clic en su dispositivo iOS.  
    
6. En su dispositivo iOS, asegúrese de que está en la pantalla principal.  
    
7. En el equipo de administración, en la barra de tareas, haga clic en **Tareas remotas > Bloqueo remoto**. Observe su dispositivo iOS mientras cambia a la pantalla de bloqueo.
    
Para eliminar el código de acceso:
  
1. En el equipo de administración, en el panel **Todos los dispositivos administrados directamente**, haga clic en la pestaña **Dispositivos**.
    
2. En la lista, haga clic en su dispositivo iOS. En la barra de tareas, haga clic en **Tareas remotas > Restablecimiento de código de acceso**. Espere un minuto.
    
3. En su dispositivo iOS, desbloquéelo y observe que ya no hay código de acceso. Para volver a cambiar el código de acceso, vaya a **Configuración** y luego **Código de acceso**.
    
Para bloquear de forma remota un dispositivo Android:
  
1. Desde la consola de administración de Microsoft Intune del explorador, haga clic en **grupos** en el panel de navegación izquierdo.
    
2. En el panel **Grupos**, abra **Todos los dispositivos > Todos los dispositivos móviles > Todos los dispositivos administrados directamente**.
    
3. En el panel **Todos los dispositivos administrados directamente**, haga clic en la pestaña **Dispositivos**.
    
4. En la lista de dispositivos, haga clic en su dispositivo Android.  
    
5. En su dispositivo Android, asegúrese de que está en la pantalla principal.  
    
6. En el equipo de administración, en la barra de tareas, haga clic en **Tareas remotas > Bloqueo remoto**. Cuando se le solicite, haga clic en **Sí**.
    
7. Observe su dispositivo Android mientras cambia a la pantalla de bloqueo.
    
Cuando se restablece el código de acceso para dispositivos Android, el portal de administración Intune genera y configura un código de acceso seguro.
  
Para restablecer el código de acceso de forma remota:
  
1. En el equipo de administración, en la pestaña de la consola de administración de Microsoft Intune del explorador, en el panel **Todos los dispositivos administrados directamente**, haga clic en su dispositivo Android.
    
2. En la barra de tareas, haga clic en **Tareas remotas > Restablecimiento de código de acceso**.
    
3. En el aviso **Tarea remota: Restablecimiento de código de acceso**, haga clic en **Sí**. Espere un minuto.
    
4. En el panel **Todos los dispositivos administrados directamente**, haga clic en **Ver propiedades**.
    
5. En **Restablecimiento de código de acceso**, anote el nuevo código de acceso.
    
6. En su dispositivo Android, introduzca el nuevo código de acceso en la pantalla de bloqueo.  
    
7. Para volver a cambiar el código de acceso, vaya a **Configuración**, pulse **Dispositivo**, pulse **Pantalla de bloqueo**, escriba el nuevo código de acceso, pulse **Bloqueo de pantalla** y luego su elección de código de acceso.
    

> [!TIP]
> Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual de todos los artículos en la pila de la Guía del entorno de pruebas de One Microsoft Cloud.
  
## <a name="see-also"></a>Consulte también

[Entorno de pruebas y desarrollo de Microsoft 365 Enterprise](the-microsoft-365-enterprise-dev-test-environment.md)
  
[Directivas MAM para sus entornos de desarrollo y prueba de Microsoft 365 Enterprise](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[Guías de entorno de pruebas de adopción de la nube (TLG)](cloud-adoption-test-lab-guides-tlgs.md)

[Movilidad de la empresa + seguridad (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


