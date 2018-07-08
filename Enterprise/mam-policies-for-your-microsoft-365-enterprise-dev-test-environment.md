---
title: Directivas MAM para sus entornos de desarrollo y prueba de Microsoft 365 Enterprise
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
description: 'Resumen: Use esta guía de laboratorio de prueba para agregar las directivas de administración (MAM) de una aplicación móvil de EMS a su entorno de desarrollo y prueba de Microsoft 365.'
ms.openlocfilehash: 0a5c81665edf06631b8cebc57c9e715c78d3d85e
ms.sourcegitcommit: c23b95d32a865e45be7843f38a1f23b5693ba76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2018
ms.locfileid: "20188158"
---
# <a name="mam-policies-for-your-microsoft-365-enterprise-devtest-environment"></a>Directivas MAM para sus entornos de desarrollo y prueba de Microsoft 365 Enterprise

 **Resumen:** Use esta guía de laboratorio de prueba para agregar las directivas de administración (MAM) de una aplicación móvil de EMS a su entorno de desarrollo y prueba de Microsoft 365.
  
La movilidad de Microsoft Enterprise + seguridad (EMS) ayuda a mantener la productividad con sus aplicaciones favoritas y dispositivos durante la protección de datos de la organización de los empleados. Para obtener más información, vea [Enterprise movilidad + seguridad (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).
  
Con las instrucciones de este artículo, agregue las directivas de administración (MAM) de aplicaciones móviles a su entorno de desarrollo y prueba de Microsoft 365.
  
## <a name="phase-1-build-out-your-microsoft-365-devtest-environment"></a>Fase 1: Generar el entorno de desarrollo y prueba de Microsoft 365

Siga las instrucciones que aparecen en el [entorno de desarrollo o prueba de la empresa de 365 de Microsoft](the-microsoft-365-enterprise-dev-test-environment.md).
  
## <a name="phase-2-create-and-deploy-mam-policies-for-ios-and-android-devices"></a>Fase 2: Crear e implementar directivas de MAM para dispositivos iOS y Android

En esta fase, creará e implementará dos directivas de MAM diferentes: una para dispositivos iOS y otra para dispositivos Android.
  
1. Vaya al portal de Office 365 ([https://portal.office.com](https://portal.office.com)) e inicie sesión en su suscripción de prueba de Office 365 con su cuenta de administrador global.
    
2. En una nueva ficha del explorador, abra el portal de Azure ([https://azure.portal.com](https://azure.portal.com)) e iniciar sesión con su cuenta de administrador global de Office 365.
    
3. En la ficha portal Azure en Internet Explorer, en el panel de navegación, haga clic en **todos los servicios**, escriba **Intune**y, a continuación, haga clic en **Intune**.
    
4. En el panel de navegación izquierdo, haga clic en **Grupos**.
    
5. En el servidor blade de **grupos a todos los grupos** , haga clic en **+ nuevo grupo**.
    
6. En el servidor blade de **grupo** , seleccione **Office 365** para **tipo de grupo?**, escriba **administrado a los usuarios de dispositivos iOS** en **nombre**, seleccione **asignado** en **tipo de pertenencia**y, a continuación, haga clic en **crear**. 
    
7. Cierre la hoja **Grupo**.
    
8. En el servidor blade de **grupos a todos los grupos** , haga clic en **Agregar**.
    
9. En el servidor blade de **grupo** , seleccione **Office 365** para **tipo de grupo?**, escriba **usuario de dispositivos Android administrado** en **nombre**, seleccione **asignado** en **tipo de pertenencia**y, a continuación, haga clic en **crear**.
    
10. Cierre el servidor blade de **grupos a todos los grupos** .
    
11. En la hoja **Intune**, en la lista **Tareas rápidas**, haga clic en **Crear una directiva de cumplimiento**.
    
12. En la hoja **Perfiles de directiva de cumplimiento**, haga clic en **Crear directiva**.
    
13. En la hoja **Crear directiva**, en **Nombre**, escriba **iOS**. En **Plataforma**, seleccione **iOS**, haga clic en **Aceptar** en la hoja **Directiva de cumplimiento de iOS** y, a continuación, haga clic en **Crear**.
    
14. En la hoja **Perfiles de directiva de cumplimiento**, haga clic en **Crear directiva**.
    
15. En la hoja **Crear directiva**, en **Nombre**, escriba **Android**. En **Plataforma**, seleccione **Android**, haga clic en **Aceptar** en la hoja **Directiva de cumplimiento de Android** y, a continuación, haga clic en **Crear**.
    
16. En la hoja **Perfiles de directiva de cumplimiento**, haga clic en el nombre de directiva **Android**.
    
17. En el panel de navegación izquierdo de la hoja **Android - Propiedades**, haga clic en **Tareas** y, a continuación, en **Seleccionar grupos**.
    
18. En la hoja **Seleccionar grupos**, haga clic en **Usuarios de dispositivos Android administrados** y después haga clic en **Seleccionar**.
    
19. Haga clic en **Guardar**y, a continuación, cierre el blade **Android - las asignaciones** .
    
20. En la hoja **Perfiles de directiva de cumplimiento**, haga clic en el nombre de directiva **iOS**.
    
21. En el panel de navegación izquierdo de la hoja **iOS - Propiedades**, haga clic en **Tareas** y, a continuación, en **Seleccionar grupos**.
    
22. En la hoja **Seleccionar grupos**, haga clic en el grupo **Usuarios de dispositivos iOS administrados** y después haga clic en **Seleccionar**.
    
23. Haga clic en **Guardar**y, a continuación, cierre el blade **iOS - las asignaciones** .
    
24. Cierre la hoja **Perfiles de directiva de cumplimiento**.
    
25. En la hoja **Intune**, haga clic en **Administrar aplicaciones** en el panel de navegación izquierdo.
    
26. En la hoja **Aplicaciones móviles**, haga clic en **Aplicaciones**.
    
27. En la lista de aplicaciones, haga clic en **PowerPoint**,  
    
28. En la hoja **Información general sobre PowerPoint**, haga clic en **Tareas > Seleccionar grupos > Dispositivos iOS administrados > Seleccionar**. En **Tipo**, seleccione **Disponible** y, a continuación, haga clic en **Guardar**.
    
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
    
30. Cierre la hoja **Aplicaciones móviles - Aplicaciones**.
    
31. En la hoja **Aplicaciones móviles**, haga clic en **Directivas de protección de aplicaciones**.
    
32. En la hoja **Directivas de protección de aplicaciones**, haga clic en **Agregar directiva**.
    
33. En la hoja **Agregar directiva**, escriba **iOS** y, a continuación, haga clic en **Elegir aplicaciones obligatorias**.
    
34. En la hoja **Aplicaciones**, haga clic en **PowerPoint**, **Microsoft Dynamics CRM en iPhone**, **Excel**, **Microsoft Dynamics CRM en iPhone**, **Word**, **OneNote** y **Outlook**, y, a continuación, en **Seleccionar**.
    
35. En la hoja **Agregar una directiva**, haga clic en **Crear**.
    
36. En la hoja **Directivas de protección de aplicaciones**, haga clic en **Agregar directiva**.
    
37. En la hoja **Agregar una directiva**, escriba **Android**, seleccione **Android** en **Plataforma** y, a continuación, haga clic en **Elegir aplicaciones obligatorias**.
    
38. En la hoja **Aplicaciones**, haga clic en **PowerPoint**, **Dynamics CRM para tabletas**, **Excel**, **Word**, **Outlook** y **Dynamics CRM para teléfonos** y, a continuación, en **Seleccionar**.
    
39. En la hoja **Agregar una directiva**, haga clic en **Crear**.
    
Ahora tiene dos directivas de MAM, una para dispositivos iOS y otra para dispositivos Android, y está preparado para experimentar con la configuración de prueba para las aplicaciones seleccionadas.
  
> [!TIP]
> Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual de todos los artículos en la pila de la Guía del entorno de pruebas de One Microsoft Cloud.
  
## <a name="see-also"></a>Consulte también

[Entorno de pruebas y desarrollo de Microsoft 365 Enterprise](the-microsoft-365-enterprise-dev-test-environment.md)
  
[Inscriba los dispositivos iOS y Android en el entorno de desarrollo y prueba de Microsoft 365 Enterprise](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
  
[Guías de entorno de pruebas de adopción de la nube (TLG)](cloud-adoption-test-lab-guides-tlgs.md)

[Movilidad de la empresa + seguridad (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


