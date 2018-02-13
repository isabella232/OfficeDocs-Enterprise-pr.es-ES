---
title: "Seguridad de la aplicación de nube para su entorno de pruebas y desarrollo de Office 365"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: TLG, Ent_TLGs
ms.assetid: 22248f2f-b370-435e-b6ac-0ae0cae36b96
description: "Resumen: Configurar y demostrar la seguridad de la aplicación de Office 365 nube en el entorno de desarrollo y prueba de Office 365."
ms.openlocfilehash: a1a7269b5ac9bff949d9f7d31775bdaa2c4d3d3a
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/13/2018
---
# <a name="cloud-app-security-for-your-office-365-devtest-environment"></a>Seguridad de la aplicación de nube para su entorno de pruebas y desarrollo de Office 365

 **Resumen:** Configurar y demostrar la seguridad de la aplicación de Office 365 nube en el entorno de desarrollo y prueba de Office 365.
  
Seguridad de aplicación nube Office 365, anteriormente conocido como Office 365 administración avanzada de seguridad, le permite crear directivas que supervisión y le informan de actividades sospechosas en su suscripción de Office 365, para que pueda investigar y tomar posible acción de corrección. Para obtener más información, consulte [Información general de nube App seguridad en Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).
  
Con las instrucciones de este artículo, habilitar y probar la seguridad de la aplicación de nube en su suscripción de prueba de Office 365.
  
> [!TIP]
> Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual para todos los artículos de la pila de una guía de laboratorio de prueba de nube de Microsoft.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>Fase 1: Crear un entorno de desarrollo y pruebas ligero o de una empresa simulada de Office 365

Si desea probar la seguridad de la aplicación de nube en una manera ligera con los requisitos mínimos, siga las instrucciones que aparecen en las fases 2 y 3 del [entorno de desarrollo y prueba de Office 365](office-365-dev-test-environment.md).
  
Si desea probar la seguridad de la aplicación de nube en una empresa simulada, siga las instrucciones de [sincronización de directorios para el entorno de desarrollo y prueba de Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> Pruebas de nube, seguridad de la aplicación no requiere que el entorno de desarrollo/pruebas simuladas enterprise, que incluye una intranet simulada conectada a Internet y sincronización de directorios para un bosque de Windows Server AD. Se proporciona aquí como una opción para que pueda probar la seguridad de la aplicación de nube y experimentar con él en un entorno que representa una organización típica. 
  
## <a name="phase-2-before-enabling-cloud-app-security-and-creating-a-policy"></a>Fase 2: antes de habilitar la seguridad de la aplicación de nube y la creación de una directiva

En este procedimiento, se demuestre que antes de habilitar la seguridad de la aplicación de nube, cambiar una función de usuario no proporciona ninguna notificación de correo electrónico para el administrador global.
  
### <a name="test-the-default-notification-behavior-of-office-365"></a>Probar el comportamiento de notificación predeterminado de Office 365

1. Ir al portal de Office 365 ([https://portal.office.com](https://portal.office.com)) e iniciar sesión en su suscripción de prueba de Office 365 con su cuenta de administrador global.
    
  - Si usa el entorno de desarrollo y pruebas ligero de Office 365, inicie sesión desde el equipo local.
    
  - Si utiliza el entorno de desarrollo/pruebas simuladas enterprise Office 365, usar el [portal de Azure](https://portal.azure.com) para conectarse a la máquina virtual de CLIENTE1 e inicie sesión desde CLIENTE1.
    
2. Desde la página principal del portal, haga clic en **Admin**.
    
3. En el panel de navegación izquierdo, haga clic en **Usuarios > Usuarios activos**.
    
4. Haga clic en la cuenta de **usuario 4** .
    
5. En la página **4 de usuario** , haga clic en **Editar** para la fila de **funciones** .
    
6. En la página **Editar roles de usuario** , haga clic en **Administrador Global**, escriba **user4@contoso.com** en la **dirección de correo electrónico alternativa**y, a continuación, haga clic en **Guardar**. Haga clic dos veces en **Cerrar** .
    
7. Seleccione el icono del selector de la aplicación en la parte superior izquierda y elija **correo**.
    
8. Espere 30 minutos. Observe que no aparece ningún mensaje de correo electrónico en la Bandeja de entrada que notifica el cambio en el rol de usuario 4 como un administrador global.
    
## <a name="phase-3-enable-cloud-app-security-and-create-a-policy"></a>Fase 3: Habilitar la seguridad de la aplicación de nube y crear una directiva

En este procedimiento, puede habilita la seguridad de la aplicación de nube y crea una nueva directiva para enviar notificaciones por correo electrónico a su cuenta de administrador global para cambios en las funciones de cuenta de usuario. Este procedimiento requiere:
  
- El nombre y la contraseña de la cuenta de administrador global de la suscripción de prueba de Office 365.
    
- El nombre y la contraseña de la cuenta del Usuario 5 de la suscripción de prueba de Office 365.
    
### <a name="enable-and-configure-cloud-app-security"></a>Habilitar y configurar la seguridad de la aplicación de nube

1. Ir al portal de Office 365 ([https://portal.office.com](https://portal.office.com)) e iniciar sesión en su suscripción de prueba de Office 365 con su cuenta de administrador global.
    
2. Haga clic en el **seguridad &amp; Compliance** mosaico.
    
3. En el panel de navegación de la izquierda, haga clic en **alertas > Administrar alertas de avanzada**.
    
4. En la página **Administrar alertas de avanzada** , haga clic en **activar la seguridad de la aplicación de nube de Office 365**y, a continuación, haga clic en **Ir a la seguridad de la aplicación de nube de Office 365**.
    
5. En la ficha nuevo del **panel** , haga clic en **Control > directivas**.
    
6. En la página de **Directiva** , haga clic en **Crear directiva**y, a continuación, haga clic en **Directiva de actividad**.
    
7. En **nombre de directiva**, escriba **actividad administrativa**.
    
8. **Gravedad de la directiva**, haga clic en **alto**.
    
9. En **categoría**, haga clic en **cuentas con privilegios**.
    
10. **Crear filtros para la directiva**, en **las actividades que coinciden con todas las opciones siguientes**, haga clic en **actividad administrativa**.
    
11. En **alertas**, haga clic en **Enviar alerta por correo electrónico**. En el cuadro **para**, escriba la dirección de correo electrónico de la cuenta de administrador global.
    
12. En la parte inferior de la página, haga clic en **crear**.
    
## <a name="phase-4-show-cloud-app-security-in-action"></a>Fase 4: Mostrar nube App seguridad en acción

En este procedimiento, que demuestran cómo la seguridad de la aplicación de nube crea alertas y envía notificaciones por correo electrónico a la cuenta de administrador global al usuario 4 hace 5 de usuario, un administrador del usuario y la contraseña.
  
### <a name="demonstrate-email-notification-for-a-change-in-user-account-roles"></a>Demostración de la notificación por correo electrónico en caso de cambio en los roles de la cuenta de usuario

1. En la parte superior derecha, haga clic en el icono de usuario y, a continuación, haga clic en **Cerrar sesión**.
    
2. Vaya a [https://portal.office.com](https://portal.office.com).
    
3. En la página de identificación Office 365, haga clic en **usar otra cuenta**.
    
4. Escriba el nombre de la cuenta de usuario 4 y su contraseña y, a continuación, haga clic en **iniciar sesión**.
    
5. Si es necesario, cambiar la contraseña de la cuenta de usuario 4 y, a continuación, haga clic en **Actualizar contraseña e iniciar sesión en**.
    
6. En la página de portal de Office 365, haga clic en **Admin**.
    
7. Si es necesario, haga clic en **Cancelar** cuando se le pida para actualizar tu información de contacto del administrador.
    
8. Desde la página principal del portal, haga clic en **Admin**.
    
9. En el panel de navegación izquierdo, haga clic en **Usuarios > Usuarios activos**.
    
10. Haga clic en la cuenta de **usuario 5** .
    
11. En la página **5 de usuario** , haga clic en **Editar** para la fila de **funciones** .
    
12. En la página **Editar roles de usuario** , haga clic en **Administrador de personalizado**, haga clic en **Administrador de contraseñas** y de **Administrador del usuario**, escriba **user5@contoso.com** en la **dirección de correo electrónico alternativa**y, a continuación, haga clic en **Guardar**. Haga clic dos veces en **Cerrar** .
    
13. Haga clic en el icono de usuario en la parte superior derecha y, a continuación, haga clic en **Cerrar sesión**. 
    
14. Vaya a [https://portal.office.com](https://portal.office.com).
    
15. En la página **Office 365 iniciar sesión en** , haga clic en el nombre de la cuenta de administrador global.
    
16. Escriba la contraseña y, a continuación, haga clic en **iniciar sesión**.
    
17. Desde la página principal del portal, haga clic en **Admin**.
    
18. Haga clic en el **seguridad &amp; Compliance** mosaico.
    
19. En el panel de navegación de la izquierda, haga clic en **alertas > Administrar alertas de avanzada**.
    
20. En la página **Administrar alertas de avanzada** , haga clic en **Ir a la seguridad de la aplicación de nube de Office 365**.
    
21. En la ficha nuevo del **panel** , observe las dos nuevas alertas de **actividad administrativa**.
    
22. En la ficha **Página de inicio de Microsoft Office** , haga clic en **correo**. Espere 30 minutos. 
    
    Debería ver dos mensajes de correo electrónico nuevo en la Bandeja de entrada con el título **Servicio de notificación de AD de Microsoft Azure**. Un mensaje indica que se ha agregado la cuenta de usuario 5 a la función de **Administrador de contraseñas** y otro mensaje que se ha agregado la cuenta de usuario 5 a la función de **Administrador de usuarios** (igual que la función de administrador de gestión de usuario en el Centro de administración de Office 365).
    
Ahora puede utilizar este entorno para crear nuevas directivas y experimentar aún más con la seguridad de la aplicación de nube de Office 365. Para obtener vínculos a artículos de configuración adicionales, consulte [Prepárese para seguridad de la aplicación de nube de Office 365](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a) .
  
## <a name="see-also"></a>Consulte también

[Guías de entorno de pruebas de adopción de la nube (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[Entorno de desarrollo y pruebas de Office 365](office-365-dev-test-environment.md)
  
[Adopción de la nube y soluciones híbridas](cloud-adoption-and-hybrid-solutions.md)

[Resumen de seguridad de la aplicación de nube en Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)


