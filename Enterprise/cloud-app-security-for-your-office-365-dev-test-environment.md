---
title: Seguridad de Cloud App para su entorno de desarrollo y prueba de Office 365
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
description: 'Resumen: Configurar y demostrar la seguridad de la aplicación de Office 365 en la nube en el entorno de desarrollo y prueba de Office 365.'
ms.openlocfilehash: 2c29e650233348e44bf72adcb8b18580e1de8802
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897063"
---
# <a name="cloud-app-security-for-your-office-365-devtest-environment"></a>Seguridad de Cloud App para su entorno de desarrollo y prueba de Office 365

 **Resumen:** Configurar y demostrar la seguridad de la aplicación de Office 365 en la nube en el entorno de desarrollo y prueba de Office 365.
  
Office 365 en la nube seguridad de la aplicación, anteriormente conocido como Office 365 administración avanzada de seguridad, permite crear directivas que supervisión e informan de las actividades sospechosas en su suscripción de Office 365, para que pueda investigar y tomar las medidas posibles acción. Para obtener más información, vea [Información general de la nube seguridad de la aplicación en Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).
  
Con las instrucciones de este artículo, habilitar y probar la seguridad de la aplicación en la nube en su suscripción de prueba de Office 365.
  
> [!TIP]
> Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual de todos los artículos de la pila Guía de laboratorio de pruebas de One Microsoft Cloud.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>Fase 1: Crear un entorno de desarrollo y pruebas ligero o de una empresa simulada de Office 365

Si desea probar la seguridad de la aplicación en la nube en una forma sencilla con los requisitos mínimos, siga las instrucciones que aparecen en las fases 2 y 3 del [entorno de desarrollo y prueba de Office 365](office-365-dev-test-environment.md).
  
Si desea probar la seguridad de la aplicación de nube en una empresa simulada, siga las instrucciones que aparecen en la [sincronización de directorios para el entorno de desarrollo y prueba de Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> Seguridad de la aplicación en la nube pruebas no requiere el entorno de desarrollo o prueba simulado enterprise, que incluye una intranet simulada conectada a Internet y sincronización de Active directory para un bosque de Windows Server AD. Se proporciona aquí como una opción para que pueda probar la seguridad de la aplicación en la nube y experimentar con él en un entorno que representa una organización típica. 
  
## <a name="phase-2-before-enabling-cloud-app-security-and-creating-a-policy"></a>Fase 2: antes de habilitar la seguridad de la aplicación en la nube y creación de una directiva

En este procedimiento, demostrar que antes de habilitar la seguridad de la aplicación en la nube, cambiar un rol de usuario no proporciona ninguna notificación de correo electrónico para el administrador global.
  
### <a name="test-the-default-notification-behavior-of-office-365"></a>Probar el comportamiento de notificación predeterminado de Office 365

1. Vaya al portal de Office 365 ([https://portal.office.com](https://portal.office.com)) e inicie sesión en su suscripción de prueba de Office 365 con su cuenta de administrador global.
    
  - Si usa el entorno de desarrollo y pruebas ligero de Office 365, inicie sesión desde el equipo local.
    
  - Si está utilizando el entorno de desarrollo y prueba de Office 365 enterprise simulado, use el [portal de Azure](https://portal.azure.com) para conectarse a la máquina virtual CLIENT1 y, a continuación, iniciar sesión en desde CLIENT1.
    
2. En la página principal del portal, haga clic en **Administración**.
    
3. En el panel de navegación izquierdo, haga clic en **Usuarios > Usuarios activos**.
    
4. 	Haga clic en la cuenta **Usuario 4**.
    
5. En la página del **Usuario 4**, haga clic en **Editar** en la fila **Roles**.
    
6. En la página **Edit user roles** (Editar roles de usuario), haga clic en **Administrador global**, escriba **user4@contoso.com** en **Alternative email address** (Dirección de correo electrónico alternativa) y haga clic en **Guardar**. Haga clic dos veces en **Cerrar**.
    
7. 	Seleccione el icono del iniciador de aplicaciones en la esquina superior izquierda y elija **Correo**.
    
8. Espere 30 minutos. Tenga en cuenta que no hay ningún mensaje de correo electrónico en la Bandeja de entrada que notifica el cambio en el rol del usuario 4 como un administrador global.
    
## <a name="phase-3-enable-cloud-app-security-and-create-a-policy"></a>Fase 3: Habilitar la seguridad de la aplicación en la nube y crear una directiva

En este procedimiento, habilitar la seguridad de la aplicación en la nube y crear una nueva directiva para enviar notificaciones de correo electrónico a la cuenta de administrador global para que los cambios en los roles de la cuenta de usuario. En este procedimiento, es necesario:
  
- El nombre y la contraseña de la cuenta de administrador global de la suscripción de prueba de Office 365.
    
- El nombre y la contraseña de la cuenta del Usuario 5 de la suscripción de prueba de Office 365.
    
### <a name="enable-and-configure-cloud-app-security"></a>Habilitar y configurar la seguridad de la aplicación en la nube

1. Vaya al portal de Office 365 ([https://portal.office.com](https://portal.office.com)) e inicie sesión en su suscripción de prueba de Office 365 con su cuenta de administrador global.
    
2. Haga clic en el icono de **administración** . En la ficha del **Centro de administración de Office** , haga clic en **Admin centros de seguridad de > & cumplimiento**.
    
3. En el panel de navegación izquierdo, haga clic en **avanzada de alertas > administrar alertas**.
    
4. En la página **Administrar alertas de avanzada** , haga clic en **activar la seguridad de la aplicación de nube de Office 365**y, a continuación, haga clic en **Ir a la seguridad de la aplicación de nube de Office 365**.
    
5. En la ficha nuevo del **panel** , haga clic en **Control > directivas**.
    
6. En la página **Directiva** , haga clic en **Crear directiva**y, a continuación, haga clic en **Directiva de actividad**.
    
7. En **nombre de directiva**, escriba **actividad administrativa**.
    
8. En **Gravedad de directiva**, haga clic en **Alto**.
    
9. En **categoría**, haga clic en **cuentas con privilegios**.
    
10. **Crear filtros para la directiva**, en **las actividades que coincidan con todos los elementos siguientes**, haga clic en **actividades administrativas**.
    
11. En **Alertas**, haga clic en **Enviar alerta como mensaje de correo electrónico**. En **Para**, escriba la dirección de correo electrónico de la cuenta de administrador global.
    
12. En la parte inferior de la página, haga clic en **Crear**.
    
## <a name="phase-4-show-cloud-app-security-in-action"></a>Fase 4: Mostrar la seguridad de la aplicación de nube en acción

En este procedimiento, demostrar cómo la seguridad de la aplicación en la nube crea alertas y envía notificaciones de correo electrónico a la cuenta de administrador global al usuario 4 hace 5 de usuario que un administrador de usuario y la contraseña.
  
### <a name="demonstrate-email-notification-for-a-change-in-user-account-roles"></a>Demostración de la notificación por correo electrónico en caso de cambio en los roles de la cuenta de usuario

1. En la superior derecha, haga clic en el icono de usuario y, a continuación, haga clic en **Cerrar sesión**.
    
2. Vaya a [https://portal.office.com](https://portal.office.com).
    
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
    
13. Haga clic en el icono de usuario en la superior derecha y, a continuación, haga clic en **Cerrar sesión**. 
    
14. Vaya a [https://portal.office.com](https://portal.office.com).
    
15. En la página **Inicio de sesión en Office 365**, haga clic en el nombre de la cuenta de administrador global.
    
16. Escriba la contraseña y haga clic en **Iniciar sesión**.
    
17. En la página principal del portal, haga clic en **Administración**.
    
18. Haga clic en el **seguridad &amp; cumplimiento** colocar en mosaico.
    
19. En el panel de navegación izquierdo, haga clic en **avanzada de alertas > administrar alertas**.
    
20. En la página **Administrar alertas de avanzada** , haga clic en **Ir a la seguridad de la aplicación de nube de Office 365**.
    
21. En la ficha nuevo **panel** , tenga en cuenta las dos alertas nuevo para la **actividad administrativa**.
    
22. En la ficha **Página principal de Microsoft Office** , haga clic en **correo**. Espere hasta 30 minutos. 
    
    Debería ver dos nuevos mensajes de correo electrónico en la Bandeja de entrada con el título **Servicio de notificación de Microsoft Azure AD**. Un mensaje indica que la cuenta de usuario 5 se ha agregado a la función de **Administrador de contraseñas** y otro mensaje indica que la cuenta de usuario 5 se ha agregado a la función de **Administrador del usuario** (igual que el rol de administrador de administración de usuario en el Centro de administración de Office 365).
    
Ahora puede usar este entorno para crear nuevas directivas y aún más experimentar con la seguridad de la aplicación de nube de Office 365. Para obtener vínculos a artículos sobre la configuración adicional, vea [prepararse para la seguridad de la aplicación de nube de Office 365](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a) .
  
## <a name="see-also"></a>Vea también

[Guías del laboratorio de pruebas de adopción de la nube (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[Entorno de desarrollo y prueba de Office 365](office-365-dev-test-environment.md)
  
[Adopción de la nube y soluciones híbridas](cloud-adoption-and-hybrid-solutions.md)

[Información general de seguridad de la aplicación en la nube en Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)


