---
title: Directivas MAM para su entorno de pruebas y desarrollo empresarial de Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: "Resumen: Utilice a esta guía de laboratorio de prueba para agregar directivas de administración (MAM) de una aplicación móvil de EMS a su entorno de pruebas y desarrollo de Microsoft 365."
ms.openlocfilehash: cd5a9801ec7cc5c8fe287fa65015fcb02dd542bf
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2018
---
# <a name="mam-policies-for-your-microsoft-365-enterprise-devtest-environment"></a>Directivas MAM para su entorno de pruebas y desarrollo empresarial de Microsoft 365

 **Resumen:** Utilice a esta guía de laboratorio de prueba para agregar directivas de administración (MAM) de una aplicación móvil de EMS a su entorno de pruebas y desarrollo de Microsoft 365.
  
La movilidad en la empresa Microsoft + seguridad (EMS) ayuda a mantener la productividad con sus aplicaciones favoritas y dispositivos mientras protege los datos de la organización de sus empleados. Para obtener más información, vea [seguridad (EMS) + de movilidad en la empresa](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).
  
Con las instrucciones de este artículo, agregue las directivas de administración (MAM) de aplicación móvil a su entorno de pruebas y desarrollo de Microsoft 365.
  
## <a name="phase-1-build-out-your-microsoft-365-devtest-environment"></a>Fase 1: Construir su entorno de pruebas y desarrollo de Microsoft 365

Siga las instrucciones en el [entorno de desarrollo y prueba el Microsoft 365 Enterprise](the-microsoft-365-enterprise-dev-test-environment.md).
  
## <a name="phase-2-create-and-deploy-mam-policies-for-ios-and-android-devices"></a>Fase 2: Crear e implementar directivas de MAM para dispositivos iOS y Android

En esta fase, creará e implementará dos directivas de MAM diferentes: una para dispositivos iOS y otra para dispositivos Android.
  
1. Ir al portal de Office 365 ([https://portal.office.com](https://portal.office.com)) e iniciar sesión en su suscripción de prueba de Office 365 con su cuenta de administrador global.
    
2. En una nueva pestaña del explorador, abra el portal de Azure ([https://azure.portal.com](https://azure.portal.com)) e inicie sesión con su cuenta de administrador global de Office 365.
    
3. En la ficha portal Azure en Internet Explorer, en el panel de exploración, haga clic en **más servicios** (o la flecha derecha), escriba **Intune**y, a continuación, haga clic en **Intune**.
    
4. En el panel de navegación izquierdo, haga clic en **Grupos**.
    
5. En el módulo de **usuarios y grupos de grupos** , haga clic en **Agregar**.
    
6. En la hoja de **grupo** , escriba **administran los usuarios de dispositivos iOS** en **nombre**, seleccione **asignado** en el **tipo de suscripción**, seleccione **Sí** para **funciones de activar Office?**y, a continuación, haga clic en **crear**. 
    
7. Cierre la hoja de **grupo** .
    
8. En el módulo de **usuarios y grupos de grupos** , haga clic en **Agregar**.
    
9. En la hoja de **grupo** , escriba **usuarios de dispositivos Android administrado** en **nombre**, seleccione **asignado** en el **tipo de suscripción**, seleccione **Sí** para **funciones de activar Office?**y, a continuación, haga clic en **crear**.
    
10. Cierre la hoja de **usuarios y grupos de grupos** .
    
11. En la hoja de **Intune** , en la lista de **tareas rápidas** , haga clic en **crear una directiva de conformidad**.
    
12. En el módulo de **Perfiles de la directiva de conformidad** , haga clic en **Crear directiva**.
    
13. En el módulo **Crear directiva** , en **nombre**, escriba **iOS**. En la **plataforma**, seleccione **iOS**, haga clic en **Aceptar** en el módulo de **Directiva de conformidad de iOS** y, a continuación, haga clic en **crear**.
    
14. En el módulo de **Perfiles de la directiva de conformidad** , haga clic en **Crear directiva**.
    
15. En el módulo **Crear directiva** , en **nombre**, escriba **Android**. En la **plataforma**, seleccione **Android**, haga clic en **Aceptar** en el módulo de **Directiva de conformidad Android** y, a continuación, haga clic en **crear**.
    
16. En el módulo de **Perfiles de la directiva de conformidad** , haga clic en el nombre de directiva **Android** .
    
17. En la exploración de la izquierda de la hoja de **Android - propiedades** , haga clic en **asignaciones**y, a continuación, haga clic en **Seleccionar grupos**.
    
18. En el blade de **Seleccionar grupos** , haga clic en el grupo de **usuarios de dispositivos Android administrado** y, a continuación, haga clic en **Seleccionar**.
    
19. Haga clic en **Guardar**y, a continuación, cierre la hoja **Android - asignaciones** .
    
20. En el módulo de **Perfiles de la directiva de conformidad** , haga clic en el nombre de la directiva de **iOS** .
    
21. En la exploración de la izquierda de la hoja de **iOS - propiedades** , haga clic en **asignaciones**y, a continuación, haga clic en **Seleccionar grupos**.
    
22. En el blade de **Seleccionar grupos** , haga clic en el grupo de **usuarios de dispositivos iOS administrado** y, a continuación, haga clic en **Seleccionar**.
    
23. Haga clic en **Guardar**y, a continuación, cierre la hoja de **iOS - asignaciones** .
    
24. Cierre la hoja de **Perfiles de la directiva de conformidad** .
    
25. En la hoja **Intune** , haga clic en **Administrar aplicaciones** en la navegación de la izquierda.
    
26. En el módulo de **Aplicaciones móviles** , haga clic en **aplicaciones**.
    
27. En la lista de aplicaciones, haga clic en **PowerPoint**, 
    
28. En el módulo **Introducción a PowerPoint** , haga clic en **asignaciones > Seleccionar grupos > iOS dispositivos gestionados > Seleccionar**. En **tipo**, seleccione **disponible**y, a continuación, haga clic en **Guardar**.
    
29. Repita el paso 28 para las aplicaciones siguientes:
    
  - Outlook para Android
    
  - Word para iOS
    
  - Excel para iOS
    
  - Outlook para iOS
    
  - Microsoft Dynamics CRM en iPad para iOS
    
  - Microsoft Dynamics CRM en iPhone para iOS
    
  - Dynamics CRM para teléfonos Android
    
  - Dynamics CRM para tabletas Android
    
  - Excel para Android
    
  - Word para Android
    
  - OneNote para iOS
    
30. Cierre la hoja de **Aplicaciones móviles - Apps** .
    
31. En el módulo de **Aplicaciones móviles** , haga clic en **Directivas de protección de la aplicación**.
    
32. En el módulo de **Directivas de protección de la aplicación** , haga clic en **Agregar una directiva**.
    
33. En el blade de **Agregar una directiva** , escriba **iOS**y, a continuación, haga clic en **seleccionar aplicaciones necesarias**.
    
34. En el módulo de **aplicaciones** , haga clic en **PowerPoint**, **Microsoft Dynamics CRM en iPhone**, **Excel**, **Microsoft Dynamics CRM en iPhone**, **Word**, **OneNote**y **Outlook**y, a continuación, haga clic en **Seleccionar**.
    
35. En la hoja de **Agregar una directiva** , haga clic en **crear**.
    
36. En el módulo de **Directivas de protección de la aplicación** , haga clic en **Agregar una directiva**.
    
37. En la hoja de **Agregar una directiva** , escriba **Android**, seleccione **Android** en **la plataforma**y, a continuación, haga clic en **seleccionar aplicaciones necesarias**.
    
38. En el módulo de **aplicaciones** , haga clic en **Dynamics CRM para teléfonos**, **Dynamics CRM para tabletas**, **Excel**, **Word**, **Outlook**y **PowerPoint**y, a continuación, haga clic en **Seleccionar**.
    
39. En la hoja de **Agregar una directiva** , haga clic en **crear**.
    
Ahora tiene dos directivas de MAM, una para dispositivos iOS y otra para dispositivos Android, y está preparado para experimentar con la configuración de prueba para las aplicaciones seleccionadas.
  
> [!TIP]
> Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual de todos los artículos en la pila de la Guía del entorno de pruebas de One Microsoft Cloud.
  
## <a name="see-also"></a>Consulte también

[El entorno de pruebas y desarrollo empresarial de Microsoft 365](the-microsoft-365-enterprise-dev-test-environment.md)
  
[Inscribir a dispositivos iOS y Android en su entorno de pruebas y desarrollo de Microsoft Enterprise 365](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
  
[Guías de entorno de pruebas de adopción de la nube (TLG)](cloud-adoption-test-lab-guides-tlgs.md)

[Movilidad en la empresa + seguridad (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


