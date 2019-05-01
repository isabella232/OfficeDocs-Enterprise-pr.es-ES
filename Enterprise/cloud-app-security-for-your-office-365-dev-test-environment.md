---
title: Cloud App Security para el entorno de desarrollo y pruebas de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/05/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 22248f2f-b370-435e-b6ac-0ae0cae36b96
description: 'Resumen: Configure y demuestre Office 365 Cloud App Security en su entorno de desarrollo y pruebas de Office 365.'
ms.openlocfilehash: aa6fada78ada2f97242ffe8f60c9032d618f3b9b
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490126"
---
# <a name="cloud-app-security-for-your-office-365-devtest-environment"></a>Cloud App Security para el entorno de desarrollo y pruebas de Office 365

 **Resumen:** Configure y demuestre Office 365 Cloud App Security en su entorno de desarrollo y pruebas de Office 365.
  
Office 365 Cloud App Security, anteriormente conocido como Office 365 Advanced Security Management, le permite crear directivas que supervisan e informan de actividades sospechosas en su suscripción a Office 365, de modo que pueda investigar y realizar posibles correcciones acciona. Para obtener más información, vea [información general sobre Cloud App Security en Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).
  
Con las instrucciones de este artículo, puede habilitar y probar Cloud App Security en su suscripción de prueba de Office 365.
  
> [!TIP]
> Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual de todos los artículos en la pila de la Guía del laboratorio de pruebas de Office 365.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>Fase 1: Crear un entorno de desarrollo y pruebas ligero o de una empresa simulada de Office 365

Si solo quiere probar Cloud App Security de manera ligera con los requisitos mínimos, siga las instrucciones indicadas en las fases 2 y 3 del [entorno de desarrollo y pruebas de Office 365](office-365-dev-test-environment.md).
  
Si quiere probar Cloud App Security en una empresa simulada, siga las instrucciones que se indican en [DirSync para el entorno de desarrollo y pruebas de Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> La prueba de Cloud App Security no requiere el entorno de desarrollo y pruebas de una empresa simulada, que incluye una intranet simulada conectada a Internet y la sincronización de directorios para un bosque de servicios de dominio de Active Directory (AD DS). Se proporciona aquí como una opción para poder probar Cloud App Security y experimentar con ella en un entorno que representa una organización típica. 
  
## <a name="phase-2-before-enabling-cloud-app-security-and-creating-a-policy"></a>Fase 2: antes de habilitar Cloud App Security y crear una directiva

En este procedimiento, se demuestra que antes de habilitar Cloud App Security, cambiar el rol de un usuario no proporciona ninguna notificación de correo electrónico al administrador global.
  
### <a name="test-the-default-notification-behavior-of-office-365"></a>Probar el comportamiento de notificación predeterminado de Office 365

1. Vaya al centro de administración de 365 de[https://admin.microsoft.com](https://admin.microsoft.com)Microsoft () e inicie sesión en su suscripción de prueba de Office 365 con su cuenta de administrador global.
    
  - Si usa el entorno de desarrollo y pruebas ligero de Office 365, inicie sesión desde el equipo local.
    
  - Si usa el entorno de desarrollo y pruebas de una empresa simulada de Office 365, use [Azure portal](https://portal.azure.com) para conectarse a la máquina virtual CLIENT1 y, a continuación, inicie sesión desde cliente1.
    
2. En la página principal del portal, haga clic en **Administración**.
    
3. En el panel de navegación izquierdo, haga clic en **Usuarios > Usuarios activos**.
    
4. 	Haga clic en la cuenta **Usuario 4**.
    
5. En la página del **Usuario 4**, haga clic en **Editar** en la fila **Roles**.
    
6. En la página **Edit user roles** (Editar roles de usuario), haga clic en **Administrador global**, escriba **user4@contoso.com** en **Alternative email address** (Dirección de correo electrónico alternativa) y haga clic en **Guardar**. Haga clic dos veces en **Cerrar**.
    
7. 	Seleccione el icono del iniciador de aplicaciones en la esquina superior izquierda y elija **Correo**.
    
8. Espere 30 minutos. Observe que no hay ningún mensaje de correo electrónico en la bandeja de entrada que le notifique el cambio en el rol del usuario 4 como administrador global.
    
## <a name="phase-3-enable-cloud-app-security-and-create-a-policy"></a>Fase 3: habilitar Cloud App Security y crear una directiva

En este procedimiento, se habilita Cloud App Security y se crea una nueva Directiva para enviar notificaciones de correo electrónico a la cuenta de administrador global para los cambios en los roles de cuenta de usuario. Este procedimiento requiere lo siguiente:
  
- El nombre y la contraseña de la cuenta de administrador global de la suscripción de prueba de Office 365.
    
- El nombre y la contraseña de la cuenta del Usuario 5 de la suscripción de prueba de Office 365.
    
### <a name="enable-and-configure-cloud-app-security"></a>Habilitar y configurar Cloud App Security

1. Vaya al centro de administración de 365 de[https://admin.microsoft.com](https://admin.microsoft.com)Microsoft () e inicie sesión en su suscripción de prueba de Office 365 con su cuenta de administrador global.
    
2. Haga clic en el icono **Administración**. En la pestaña **centro de administración de Office** , haga clic en centros de **Administración _GT_ seguridad de & cumplimiento**.
    
3. En el panel de navegación izquierdo, haga clic en **alertas > de administración de alertas avanzadas**.
    
4. En la página **Administrar alertas avanzadas** , haga clic en **activar Office 365 Cloud App Security**y, a continuación, haga clic en **ir a Office 365 Cloud App Security**.
    
5. En la pestaña nuevo **Panel** , haga clic en **directivas de > de control**.
    
6. En la página **Directiva** , haga clic en **crear Directiva**y, a continuación, haga clic en **Directiva de actividad**.
    
7. En **nombre**de la Directiva, escriba **actividad administrativa**.
    
8. En **Gravedad de directiva**, haga clic en **Alto**.
    
9. En **categoría**, haga clic en **cuentas con privilegios**.
    
10. En **crear filtros para la Directiva**, en **actividades que coincidan con todas las opciones siguientes**, haga clic en **actividad administrativa**.
    
11. En **Alertas**, haga clic en **Enviar alerta como mensaje de correo electrónico**. En **Para**, escriba la dirección de correo electrónico de la cuenta de administrador global.
    
12. En la parte inferior de la página, haga clic en **Crear**.
    
## <a name="phase-4-show-cloud-app-security-in-action"></a>Fase 4: Mostrar Cloud App Security en acción

En este procedimiento, demostrará cómo Cloud App Security crea alertas y envía notificaciones de correo electrónico a la cuenta de administrador global cuando el usuario 4 convierte al usuario 5 en una contraseña y un administrador de administración de usuarios.
  
### <a name="demonstrate-email-notification-for-a-change-in-user-account-roles"></a>Demostración de la notificación por correo electrónico en caso de cambio en los roles de la cuenta de usuario

1. En la esquina superior derecha, haga clic en el icono de usuario y después en **Cerrar sesión**.
    
2. Vaya a [https://www.office.com](https://www.office.com).
    
3. En la página de inicio de sesión de Office 365, haga clic en **Usar otra cuenta**.
    
4. Escriba el nombre de cuenta del Usuario 4 y su contraseña y luego haga clic en **Iniciar sesión**.
    
5. Si es necesario, cambie la contraseña de la cuenta del Usuario 4 y después haga clic en **Actualizar contraseña e iniciar sesión**.
    
6. En la página del Portal de Office 365, haga clic en **Administración**.
    
7. Si es necesario, haga clic en **Cancelar** cuando se le pida que actualice su información de contacto de administrador.
    
8. En la página principal del portal, haga clic en **Administración**.
    
9. En el panel de navegación izquierdo, haga clic en **Usuarios > Usuarios activos**.
    
10. Haga clic en la cuenta **Usuario 5**.
    
11. En la página del **Usuario 5**, haga clic en **Editar** en la fila **Roles**.
    
12. En la página **Edit user roles** (Editar roles de usuario), haga clic en **Customized administrator** (Administrador personalizado), haga clic en **Administrador de contraseñas** y **Administrador de control de usuarios**, escriba **user5@contoso.com** en **Alternative email address** (Dirección de correo electrónico alternativa) y haga clic en **Guardar**. Haga clic dos veces en **Cerrar**.
    
13. Haga clic en el icono de usuario en la esquina superior derecha y después en **Cerrar sesión**. 
    
14. Vaya a [https://www.office.com](https://www.office.com).
    
15. En la página **Inicio de sesión en Office 365**, haga clic en el nombre de la cuenta de administrador global.
    
16. Escriba la contraseña y haga clic en **Iniciar sesión**.
    
17. En la página del portal de Office 365, haga clic en **Administración**.
    
18. Haga clic en el icono **seguridad &amp; y cumplimiento** .
    
19. En el panel de navegación izquierdo, haga clic en **alertas > de administración de alertas avanzadas**.
    
20. En la página **Administrar alertas avanzadas** , haga clic en **ir a Office 365 Cloud App Security**.
    
21. En la pestaña nuevo **Panel** , observe las dos nuevas alertas de **actividad administrativa**.
    
22. En la pestaña **Página principal de Microsoft Office** , haga clic en **correo**. Espere unos 30 minutos. 
    
    Verá dos nuevos mensajes de correo electrónico en la bandeja de entrada con el título **servicio de notificación de Microsoft Azure ad**. Un mensaje indica que la cuenta de usuario 5 se ha agregado a la función de **Administrador de contraseña** y otro mensaje indica que la cuenta de usuario 5 se ha agregado a la función de **Administrador** de usuarios (igual al rol de administrador de administración de usuarios en el Centro de administración de Office 365
    
Ahora puede usar este entorno para crear nuevas directivas y seguir probando con Office 365 Cloud App Security. Vea [Get Ready for Office 365 Cloud App Security](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a) para obtener vínculos a artículos de configuración adicionales.
  
## <a name="see-also"></a>Vea también

[Guías del entorno de pruebas de adopción de la nube (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[Entorno de desarrollo y prueba de Office 365](office-365-dev-test-environment.md)
  
[Adopción de la nube y soluciones híbridas](cloud-adoption-and-hybrid-solutions.md)

[Información general sobre Cloud App Security en Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)


