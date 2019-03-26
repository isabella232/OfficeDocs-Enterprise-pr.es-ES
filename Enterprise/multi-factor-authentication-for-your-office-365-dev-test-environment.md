---
title: Autenticación multifactor para el entorno de desarrollo y pruebas de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/20/2019
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
ms.assetid: e2b354b9-7f18-4da0-9107-6245eae0f33f
description: 'Resumen: configure la autenticación multifactor mediante mensajes de texto enviados a un smartphone en un entorno de desarrollo y pruebas de Office 365.'
ms.openlocfilehash: 13dc02cc23d12f6eb6e2898d34271685badd9f5a
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "30573984"
---
# <a name="multi-factor-authentication-for-your-office-365-devtest-environment"></a>Autenticación multifactor para el entorno de desarrollo y pruebas de Office 365

 **Resumen:** configure la autenticación multifactor mediante mensajes de texto enviados a un smartphone en un entorno de desarrollo y pruebas de Office 365.
  
Para obtener un nivel de seguridad adicional para iniciar sesión en su suscripción de Office 365, puede habilitar la autenticación multifactor de Azure, que requiere más que un nombre de usuario y una contraseña para autenticar una cuenta. Con la autenticación multifactor para Office 365, los usuarios deben confirmar una llamada telefónica, escribir un código de comprobación enviado en un mensaje de texto o especificar una contraseña de aplicación en su smartphone tras introducir correctamente la contraseña. Pueden iniciar sesión solo después de que se haya cumplido este segundo factor de autenticación. 
  
En este artículo, se describe cómo habilitar y probar la autenticación basada en mensajes de texto para una cuenta específica de Office 365.
  
Existen dos fases para configurar la autenticación multifactor para Office 365 en un entorno de desarrollo y prueba:
  
1. Crear el entorno de desarrollo y pruebas de Office 365.
    
2. Habilitar y probar la autenticación multifactor para la cuenta Usuario 2.
    
> [!TIP]
> Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual de todos los artículos de la pila Guía de laboratorio de pruebas de One Microsoft Cloud.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>Fase 1: Crear un entorno de desarrollo y pruebas ligero o de una empresa simulada de Office 365

Si solo quiere probar la autenticación multifactor de manera ligera con los requisitos mínimos, siga las instrucciones indicadas en las fases 2 y 3 de [Office 365 dev/test Environment](office-365-dev-test-environment.md).
  
Si desea probar la autenticación multifactor en una empresa simulada, siga las instrucciones que se indican en [DirSync para el entorno de desarrollo y pruebas de Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> Probar la autenticación multifactor no requiere el entorno de desarrollo y pruebas de una empresa simulada, que incluye una intranet simulada conectada a Internet y la sincronización de directorios para un bosque de Windows Server AD. Aquí se ofrece como opción para que pueda probar la autenticación multifactor y experimentar con ella en un entorno que representa una organización típica. 
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a>Fase 2: habilitar y probar la autenticación multifactor para la cuenta Usuario 2

Siga estos pasos para habilitar la autenticación multifactor para la cuenta Usuario 2:
  
1. Abra una instancia independiente del explorador, vaya al portal de Office 365 ([https://www.office.com](https://www.office.com)) y, a continuación, inicie sesión en su suscripción de prueba de Office 365 con su cuenta de administrador global.
    
2. En la página principal del portal, haga clic en **Administración**.
    
3. En el panel de navegación izquierdo, haga clic en **Usuarios > Usuarios activos**.
    
4. En el panel usuarios activos, haga clic en **más _GT_ multi-factor Authentication Setup**.
    
5. En la lista, seleccione la cuenta **usuario 2** .
    
6. En la sección **Usuario 2**, en **Pasos rápidos**, haga clic en **Habilitar**.
    
7. En el cuadro de diálogo **Acerca de la habilitación de autenticación multifactor**, haga clic en **Habilitar Multi-Factor Auth**.
    
8. En el cuadro de diálogo **actualizaciones correctas** , haga clic en **cerrar**.
    
9. En la pestaña **Página principal de Microsoft Office**, haga clic en el icono de cuenta de usuario en la esquina superior derecha y, después, en **Cerrar sesión**.
    
10. Cierre la instancia del explorador.
    
Complete la configuración de la cuenta Usuario 2 para usar un mensaje de texto con fines de validación y prueba mediante los pasos siguientes:
  
1. Abra una nueva instancia del explorador.
    
2. Vaya al portal de Office 365 ([https://www.office.com](https://www.office.com)) e inicie sesión con la cuenta usuario 2 (usuario2 @\<Organization name>. en Microsoft. com) y la contraseña.
    
3. Después de iniciar sesión, se le pedirá que configure la cuenta para la validación de seguridad adicional. Haga clic en **Configurar ahora**.
    
4. En la página **Comprobación de seguridad adicional**: 
    
  - Seleccione el país o región.
    
  - Escriba el número de teléfono del smartphone que va a recibir los mensajes de texto.
    
  - en **método**, haga clic en **enviarme un código por mensaje de texto**.
    
5. Haga clic en **Siguiente**.
    
6. Escriba el código de comprobación incluido en el mensaje de texto que ha recibido en el smartphone y, después, haga clic en **Comprobar**.
    
7. En la página **Step 3: Keep your existing applications** (Paso 3: conservar las aplicaciones existentes), guarde en una ubicación segura la contraseña de aplicación que se muestra para la cuenta Usuario 2 y, después, haga clic en **Listo**.
    
8. Si es la primera vez que inicia sesión con la cuenta Usuario 2, se le pedirá que cambie la contraseña. Escriba la contraseña original y la contraseña nueva dos veces y, después, haga clic en **Actualizar contraseña e iniciar sesión**. Anote la contraseña nueva en un lugar seguro.
    
    Debe ver el portal de Office 365 para el usuario 2 en la pestaña **Página principal de Microsoft Office** del explorador.
    
## <a name="see-also"></a>Vea también

[Guías del entorno de pruebas de adopción de la nube (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[Entorno de desarrollo y pruebas de la configuración básica](base-configuration-dev-test-environment.md)
  
[Entorno de desarrollo y pruebas de Office 365](office-365-dev-test-environment.md)
  
[Adopción de la nube y soluciones híbridas](cloud-adoption-and-hybrid-solutions.md)

[Planeación de multi-factor Authentication para implementaciones de Office 365](https://support.office.com/article/Plan-for-multi-factor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

