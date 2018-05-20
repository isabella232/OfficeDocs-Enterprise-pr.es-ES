---
title: Entorno de desarrollo y pruebas de Office 365 y Dynamics 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Ent_TLGs
ms.assetid: 098c1a1d-83a1-40eb-bbc9-47de7af8bb23
description: 'Resumen: Use esta guía de laboratorio de prueba para agregar Dynamics 365 a su entorno de desarrollo y prueba de Office 365.'
ms.openlocfilehash: 00d5cc0fd347aff7e201056f6af9ca271008d285
ms.sourcegitcommit: 8fcf6fd9f0c45a5445654ef811410fca3f4f5512
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2018
---
# <a name="office-365-and-dynamics-365-devtest-environment"></a>Entorno de desarrollo y pruebas de Office 365 y Dynamics 365

 **Resumen:** Use esta guía de laboratorio de prueba para agregar Dynamics 365 a su entorno de desarrollo y prueba de Office 365.
  
Con las instrucciones de este artículo, agregará una suscripción de prueba a Dynamics 365 en la misma organización que su entorno de desarrollo y pruebas de Office 365 y creará un entorno de pruebas y desarrollo de Office 365 y Dynamics 365.

![Entorno de desarrollo y pruebas de Office 365 y Dynamics 365](images/o365-dynamics365-dev-test.png)
  
  
Puede usar una suscripción de prueba a Dynamics 365 para probar las características y funcionalidades de Dynamics 365. Las siguientes soluciones se incluyen con la prueba de Dynamics 365 Plan 1, Enterprise Edition:
  
- [Microsoft Dynamics 365 para ventas](https://www.microsoft.com/dynamics365/sales). Aumentar las ventas con automatización e inteligencia digital ayudar a los vendedores centrarse y trabajar de manera más eficaz.
    
- [Microsoft Dynamics 365 para el servicio al cliente](https://www.microsoft.com/dynamics365/customer-service). Ganar fidelidad proporcionando a los agentes de la información completa e inteligencia digital que necesitan para proporcionar un servicio sin problemas.
    
- [Microsoft Dynamics 365 para el servicio de campo](https://www.microsoft.com/dynamics365/field-service). Maestro de la llamada de servicio por optimizar sus programaciones, equipamiento de sus empleados y uso de herramientas predictivas para aumentar las ganancias.
    
- [Microsoft Dynamics 365 para la automatización de servicio de Project](https://www.microsoft.com/en-us/dynamics365/project-service-automation). Completar correctamente los proyectos y crear relaciones rentables con los empleados a ser productivos y herramientas inteligentes.
    
Puede explorar uno o más de los servicios anteriores para usar en su suscripción de prueba a Dynamics 365.
  
![Guías del laboratorio de pruebas de Microsoft Cloud](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual de todos los artículos en la pila de la Guía del entorno de pruebas de One Microsoft Cloud.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>Fase 1: Crear un entorno de desarrollo y pruebas ligero o de una empresa simulada de Office 365

Si desea probar Office 365 y Dynamics 365 en una forma sencilla con los requisitos mínimos, siga las instrucciones que aparecen en las fases 2 y 3 del [entorno de desarrollo y prueba de Office 365](office-365-dev-test-environment.md).
  
Si desea probar Office 365 y Dynamics 365 para una empresa simulada, siga las instrucciones que aparecen en la [sincronización de directorios para el entorno de desarrollo y prueba de Office 365](dirsync-for-your-office-365-dev-test-environment.md).

![El entorno de desarrollo y pruebas de Office 365](images/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
> [!NOTE]
> La configuración recogida en este artículo no requiere el entorno de desarrollo y pruebas de una empresa simulada, que incluye una intranet simulada conectada a Internet y la sincronización de directorios para un bosque de Windows Server AD. Aquí se ofrece como opción para que pueda experimentar con Office 365 y Dynamics 365 en un entorno que representa una organización típica. 
  
## <a name="phase-2-add-a-dynamics-365-trial-subscription"></a>Fase 2: Agregar una suscripción de prueba a Dynamics 365

En esta fase, se registrará en la suscripción de prueba a Dynamics 365 y la agregará a la misma organización que su suscripción de prueba a Office 365.
  
### <a name="sign-up-for-a-dynamics-365-trial-subscription"></a>Registrarse para obtener una suscripción de prueba a Dynamics 365

1. Mediante un explorador en cualquiera de su equipo de escritorio (ligero) o desde CLIENT1 (simulado enterprise), inicie sesión el portal de Office 365 en [https://portal.office.com](https://portal.office.com) con las credenciales de su cuenta de administrador global.
    
2. Haga clic en el icono **Administración**.
    
3. En la pestaña **Centro de administración de Office**, en el panel de navegación izquierdo, haga clic en **Facturación > Servicios de compra**.
    
4. En la página **Servicios de compra**, busque el elemento **Dynamics 365 (plan 1) Enterprise Edition**. Mantenga el puntero del mouse sobre ese elemento y haga clic en **Iniciar prueba gratuita**.
    
5. En la página **Confirmar pedido**, haga clic en **Probar ahora**.
    
6. En la página **Recibo del pedido**, haga clic en **Continuar**.

![Entorno de desarrollo y pruebas de Office 365 y Dynamics 365](images/o365-dynamics365-dev-test.png)
    
> [!NOTE]
> La suscripción de prueba de Dynamics 365 Plan 1 Enterprise Edition es de 30 días. Puede extender fácilmente la suscripción de prueba otros 30 días. Para un entorno de pruebas y desarrollo permanente, cree una nueva suscripción de pago con un número reducido de licencias. 
  
## <a name="phase-3-assign-dynamics-365-licenses-and-system-administrators"></a>Fase 3: Asignar licencias Dynamics 365 y administradores del sistema

En esta fase, asignará las licencias de Dynamics 365 al administrador global y a las cuentas Usuario 2 y Usuario 3, y los hará administradores del sistema.
  
Siga estos pasos para asignar licencias de Dynamics 365.
  
1. En la pestaña **Centro de administración de Office**, haga clic en **Usuarios > Usuarios activos**.
    
2. En la lista de usuarios activos, haga clic en su cuenta de administrador global y, después, haga clic en **Editar** en **Licencias de productos**.
    
3. 	En el panel **Licencias de productos**, cambie la licencia del producto de **Dynamics 365 (plan 1) Enterprise Edition** a **Activada**, seleccione **Guardar** y, después, haga clic en **Cerrar** dos veces.
    
4. Realice los pasos 2 y 3 para las cuentas Usuario 2 y Usuario 3.
    
5. Cierre la pestaña **Centro de administración de Office**.
    
Siga estos pasos para configurar las cuentas Usuario 2 y Usuario 3 como administradores del sistema de Dynamics 365.
  
1. En la ficha **Página principal de Microsoft Office** , haga clic en **Admin**.
    
2. En la ficha del **Centro de administración de Office** , en el panel de navegación izquierdo, haga clic en **centros de administración**y, a continuación, haga clic en **Dynamics 365**.
    
    Es posible que tenga que esperar hasta que finalice el aprovisionamiento de Dynamics 365 para que este aparezca en el menú.
    
3. En la pestaña Dynamics 365, haga clic en **Todos estos** y, después, en **Finalizar configuración**.
    
    Espere a que se complete la configuración.
    
    Cuando se complete la configuración, se mostrará un Panel de actividad de ventas basado en datos de ejemplo que forman parte de la suscripción de prueba. Dedique unos minutos a ver el vídeo **Bienvenido a la prueba**. Cuando se complete, cierra la ventana del vídeo.
    
4. En la barra de herramientas de la parte superior, haga clic en la flecha abajo junto a **Ventas**, seleccione **Configuración** y, después, haga clic en **Seguridad**.
    
5. En la página **Seguridad**, haga clic en **Usuarios**.
    
6. En la lista de usuarios, haga clic en **Usuario 2**.
    
7. En la barra de herramientas, haga clic en **Administrar roles**.
    
8. En **Administrar roles**, haga clic en **Administrador del sistema** y, después, en **Aceptar**.
    
9. En la barra de herramientas de la parte superior, haga clic en **Seguridad**.
    
10. Repita los pasos del 5 al 8 para la cuenta Usuario 3.
    
11. Cierre la pestaña **Usuario: Usuario3**.
    
> [!NOTE]
> El rol de administrador del sistema de Dynamics 365 se asignó automáticamente a su cuenta de administrador global de Office 365. 
  
El entorno de desarrollo y pruebas de Office 365 y Dynamics 365 ahora tiene lo siguiente:
  
- Suscripciones de prueba a Office 365 E5 Enterprise y a Dynamics 365 que comparten la misma organización y el mismo inquilino de Azure AD con su lista de cuentas de usuario.
    
- Sus cuentas de administrador de organización global, Usuario 2 y Usuario 3 están habilitadas para usar Office 365 Enterprise E5 y Dynamics 365, y son administradores del sistema de Dynamics 365.
    
## <a name="next-step"></a>Paso siguiente

Configurar y, a continuación, demuestre cómo Office 365 y Dynamics 365 funcionan conjuntamente los buzones de correo de Exchange Online con la [integración de Exchange Online para el entorno de desarrollo y prueba de Office 365 y Dynamics 365](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md).
  
## <a name="see-also"></a>Vea también

[Guías del laboratorio de pruebas de adopción de la nube (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[Entorno de desarrollo y pruebas de la configuración básica](base-configuration-dev-test-environment.md)
  
[Entorno de desarrollo y prueba de Office 365](office-365-dev-test-environment.md)
  
[Sincronización de directorios (DirSync) para el entorno de desarrollo y pruebas de Office 365](dirsync-for-your-office-365-dev-test-environment.md)

[Administración de suscripción para Dynamics 365 (online)](https://technet.microsoft.com/library/jj679903.aspx)
  
[Administración de Dynamics 365](https://technet.microsoft.com/library/dn531101.aspx)


