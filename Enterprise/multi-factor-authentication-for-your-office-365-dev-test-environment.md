---
title: "Autenticación multifactor para el entorno de desarrollo y pruebas de Office 365"
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
ms.assetid: e2b354b9-7f18-4da0-9107-6245eae0f33f
description: "Resumen: Configurar la autenticación multifactor mediante mensajes de texto enviados a un teléfono inteligente en un entorno de pruebas y desarrollo de Office 365."
ms.openlocfilehash: 5f0767aedd69cd568c88617eac739ba7abb00b9b
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/13/2018
---
# <a name="multi-factor-authentication-for-your-office-365-devtest-environment"></a>Autenticación multifactor para el entorno de desarrollo y pruebas de Office 365

 **Resumen:** Configurar la autenticación multifactor mediante mensajes de texto enviados a un teléfono inteligente en un entorno de pruebas y desarrollo de Office 365.
  
Si quiere obtener un nivel adicional de seguridad para iniciar sesión en su suscripción de Office 365, puede habilitar la autenticación multifactor de Azure, que requiere algo más que el nombre de usuario y una contraseña para comprobar una cuenta. Con la autenticación multifactor para Office 365, los usuarios deben confirmar una llamada telefónica, escribir un código de comprobación enviado en un mensaje de texto o especificar una contraseña de aplicación en su smartphone tras introducir correctamente la contraseña. Pueden iniciar sesión solo después de que se haya cumplido este segundo factor de autenticación.  
  
En este artículo, se describe cómo habilitar y probar la autenticación basada en mensajes de texto para una cuenta específica de Office 365.
  
Existen dos fases para configurar la autenticación multifactor para Office 365 en un entorno de desarrollo y prueba:
  
1. Crear el entorno de desarrollo y pruebas de Office 365.
    
2. Habilitar y probar la autenticación multifactor para la cuenta Usuario 2.
    
> [!TIP]
> Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual para todos los artículos de la pila de una guía de laboratorio de prueba de nube de Microsoft.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>Fase 1: Crear un entorno de desarrollo y pruebas ligero o de una empresa simulada de Office 365

Si desea probar la autenticación con varios factores en una manera ligera con los requisitos mínimos, siga las instrucciones que aparecen en las fases 2 y 3 del [entorno de desarrollo y prueba de Office 365](office-365-dev-test-environment.md).
  
Si desea probar la autenticación con varios factores en una empresa simulada, siga las instrucciones de [sincronización de directorios para el entorno de desarrollo y prueba de Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> Probar la autenticación multifactor no requiere el entorno de desarrollo y pruebas de una empresa simulada, que incluye una intranet simulada conectada a Internet y la sincronización de directorios para un bosque de Windows Server AD. Aquí se ofrece como opción para que pueda probar la autenticación multifactor y experimentar con ella en un entorno que representa una organización típica. 
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a>Fase 2: habilitar y probar la autenticación multifactor para la cuenta Usuario 2

Siga estos pasos para habilitar la autenticación multifactor para la cuenta Usuario 2:
  
1. Abrir una instancia independiente del explorador, vaya al portal de Office 365 ([https://portal.office.com](https://portal.office.com)) y, a continuación, iniciar sesión en su suscripción de prueba de Office 365 con su cuenta de administrador global.
    
2. Desde la página principal del portal, haga clic en **Admin**.
    
3. En el panel de navegación izquierdo, haga clic en **Usuarios > Usuarios activos**.
    
4. En el panel de usuarios activos, haga clic en **más > auth multifactor de Azure de instalación**.
    
5. En la lista, haga clic en la cuenta de **usuario 2** .
    
6. En la sección **usuario 2** , **pasos rápidos**, haga clic en **Habilitar**.
    
7. En el cuadro de diálogo **acerca de cómo habilitar la autenticación multifactor** , haga clic en **Habilitar autenticación multifactor**.
    
8. En el cuadro de diálogo **actualización correcta** , haga clic en **Cerrar**.
    
9. En la ficha **Página de inicio de Microsoft Office** , haga clic en el icono de la cuenta de usuario en la parte superior derecha y, a continuación, haga clic en **Cerrar sesión**.
    
10. Cierre la instancia del explorador.
    
Complete la configuración de la cuenta Usuario 2 para usar un mensaje de texto con fines de validación y prueba mediante los pasos siguientes:
  
1. Abra una nueva instancia del explorador.
    
2. Visita el portal de Office 365 ([https://portal.office.com](https://portal.office.com)) e iniciar sesión con la cuenta de usuario 2 (user2 @\<nombre de la organización >. onmicrosoft.com) y la contraseña.
    
3. Después de iniciar sesión, deberá configurar la cuenta para la validación de seguridad adicionales. Haga clic en **Instalar ahora**.
    
4. En la página de **comprobación de seguridad adicional** :
    
  - Seleccione el país o región.
    
  - Escriba el número de teléfono del smartphone que va a recibir los mensajes de texto.
    
  - Seleccione **envíeme un código por mensaje de texto**.
    
5. Haga clic en **Contacto**.
    
6. Introduzca el código de verificación del mensaje de texto recibido en tu teléfono inteligente y, a continuación, haga clic en **Comprobar**.
    
7. En el **paso 3: mantener las aplicaciones existentes** página, registre la contraseña muestra la aplicación de la cuenta de usuario 2 en una ubicación segura y, a continuación, haga clic en **Listo**.
    
8. En la página de inicio de sesión, escriba la contraseña de la cuenta de usuario 2 y haga clic en **iniciar sesión**.
    
9. Introduce el código de verificación del mensaje de texto recibido en tu teléfono inteligente y, a continuación, haga clic en **iniciar sesión**.
    
10. Si es la primera vez que se firmaron con la cuenta de usuario 2, se le pide cambiar la contraseña. Escriba la contraseña original y la nueva contraseña dos veces y, a continuación, haga clic en **Actualizar contraseña e iniciar sesión en**. Registrar la nueva contraseña en un lugar seguro.
    
    Debería ver el Portal de Office 365 para el Usuario 2.
    
## <a name="see-also"></a>Consulte también

[Guías del laboratorio de pruebas de adopción de la nube (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[Entorno de desarrollo y pruebas de la configuración básica](base-configuration-dev-test-environment.md)
  
[Entorno de desarrollo y pruebas de Office 365](office-365-dev-test-environment.md)
  
[Adopción de la nube y soluciones híbridas](cloud-adoption-and-hybrid-solutions.md)

[Plan para la autenticación con varios factores para las implementaciones de Office 365](https://support.office.com/article/Plan-for-multi-factor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

