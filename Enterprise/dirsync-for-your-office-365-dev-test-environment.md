---
title: "Sincronización de directorios (DirSync) para el entorno de desarrollo y pruebas de Office 365"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Hybrid
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
- TLG
- Ent_TLGs
ms.assetid: e6b27e25-74ae-4b54-9421-c8e911aef543
description: "Resumen: Configurar la sincronización de directorios para el entorno de desarrollo y prueba de Office 365."
ms.openlocfilehash: da9a0070587c50ea9fc2f33612fb4885d6eaf695
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2017
---
# <a name="dirsync-for-your-office-365-devtest-environment"></a>Sincronización de directorios (DirSync) para el entorno de desarrollo y pruebas de Office 365

 **Resumen:** Configurar la sincronización de directorios para el entorno de desarrollo y prueba de Office 365.
  
Muchas organizaciones usan Azure Connect de AD y la sincronización de directorios (DirSync) para sincronizar el conjunto de cuentas de su bosque de Windows Server Active Directory (AD) local para el conjunto de cuentas de Office 365. En este artículo se describe cómo puede agregar DirSync con sincronización de contraseñas al entorno de desarrollo y pruebas de Office 365, dando como resultado la siguiente configuración.
  
![El entorno de desarrollo y prueba de Office 365 con DirSync](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
Esta configuración se compone de:  
  
- Una suscripción de prueba a Office 365 E5, que expira a los 30 días de su creación.
    
- La intranet de una organización simplificada conectada a Internet, que consta de tres máquinas virtuales en una subred de una red virtual de Azure (DC1, APP1 y CLIENTE1). Azure Connect de AD se ejecuta en APP1 para sincronizar el dominio de Windows Server AD con Office 365.
    
Existen dos fases para configurar el entorno de desarrollo y pruebas:
  
1. Crear el entorno de desarrollo y pruebas de Office 365 (las máquinas virtuales DC1, APP1 y CLIENTE1 en una red virtual Azure con una suscripción de prueba a Office 365 E5).
    
2. Instalar y configurar Azure AD Connect en APP1.
    
> [!TIP]
> Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual para todos los artículos de la pila de una guía de laboratorio de prueba de nube de Microsoft.
  
## <a name="phase-1-create-an-office-365-devtest-environment"></a>Fase 1: Crear un entorno de desarrollo y pruebas de Office 365

Siga las instrucciones en las fases 1, 2 y 3 del artículo del [entorno de desarrollo y prueba de Office 365](office-365-dev-test-environment.md) . Aquí está la configuración resultante.
  
![El entorno de desarrollo y prueba de Office 365](images/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
Esta configuración se compone de:  
  
- Una suscripción de prueba a Office 365 E5.
    
- La intranet de una organización simplificada conectada a Internet, que consta de las máquinas virtuales DC1, APP1 y CLIENTE1 en una subred de una red virtual de Azure.
    
## <a name="phase-2-install-azure-ad-connect-on-app1"></a>Fase 2: Instalar Azure AD Connect en APP1

Una vez instalado y configurado, Azure Connect AD sincroniza el conjunto de cuentas del dominio CORP Windows Server AD con el conjunto de cuentas de su suscripción de prueba a Office 365. El siguiente procedimiento le guía a través de la instalación de Azure Connect AD en APP1 y la comprobación de que funciona.
  
### <a name="install-and-configure-azure-ad-connect-on-app1"></a>Instalar y configurar Azure Connect de AD en APP1

1. Desde el [portal de Azure](https://portal.azure.com), conéctese a APP1 con el CORP\\cuenta de Usuario1.
    
2. Desde APP1, abra un símbolo del sistema de Windows PowerShell con el nivel de administrador y ejecute estos comandos:
    
  ```
  Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Stop-Process -Name Explorer -Force

  ```

3. Desde la barra de tareas, haga clic en **Internet Explorer** y vaya a [https://aka.ms/aadconnect](https://aka.ms/aadconnect).
    
4. En la página Microsoft Azure Active Directory Connect, haga clic en **Descargar**y, a continuación, haga clic en **Ejecutar**.
    
5. En la página **Bienvenido a Azure Connect de AD** , haga clic en **Acepto**y, a continuación, haga clic en **continuar**.
    
6. En la página **Configuración de Express** , haga clic en **Usar configuración express**.
    
7. En la página **Conectar a Azure AD** , escriba su nombre de cuenta de administrador global en **nombre de usuario,** escriba su contraseña en **contraseña**y, a continuación, haga clic en **siguiente**.
    
8. En la página **Conectar con AD DS** , escriba **CORP\\Usuario1** en **nombre de usuario,** escriba su contraseña en **contraseña**y, a continuación, haga clic en **siguiente**.
    
9. En la página de **configuración de inicio de sesión de anuncio de Azure** , haga clic en **continuar sin ningún verificados dominios**y, a continuación, haga clic en **siguiente**.
    
10. En la página **Listo para configurar**, haga clic en **Instalar**.
    
11. En la página **Configuración finalizada** , haga clic en **Salir**.
    
12. En Internet Explorer, vaya al portal de Office 365 ([https://portal.office.com](https://portal.office.com)) e iniciar sesión en su suscripción de prueba de Office 365 con su cuenta de administrador global.
    
13. Desde la página principal del portal, haga clic en **Admin**.
    
14. En el panel de navegación izquierdo, haga clic en **Usuarios > Usuarios activos**.
    
    Nota la cuenta denominada **Usuario1**. Esta cuenta es desde el dominio CORP Windows Server AD y es la prueba de que ha trabajado la sincronización de directorios.
    
15. Haga clic en la cuenta de **Usuario1** . Licencias de producto, haga clic en **Editar**.
    
16. En las **licencias de producto**, seleccione su país y haga clic en el control de **apagado** para **Office 365 Enterprise E5** (conmutación en **On**). Haga clic en **Guardar** en la parte inferior de la página y, a continuación, haga clic en **Cerrar**.
    
Esta es la configuración resultante.
  
![El entorno de desarrollo y prueba de Office 365 con DirSync](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
Esta configuración se compone de:  
  
- Una suscripción de prueba a Office 365 E5.
    
- La intranet de una organización simplificada conectada a Internet, que consta de las máquinas virtuales DC1, APP1 y CLIENTE1 en una subred de una red virtual de Azure. Azure Connect de AD se ejecuta en APP1 para sincronizar el dominio de Windows Server AD de CORP con Office 365 cada 30 minutos.
    
## <a name="next-step"></a>Paso siguiente

Cuando esté listo para implementar la sincronización de directorios para su organización, consulte [Implementar Office 365 sincronización de directorios (DirSync) de Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).

## <a name="see-also"></a>See Also

[Guías del laboratorio de pruebas de adopción de la nube (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[Entorno de desarrollo y pruebas de la configuración básica](base-configuration-dev-test-environment.md)
  
[Entorno de desarrollo y pruebas de Office 365](office-365-dev-test-environment.md)
  
[Seguridad de la aplicación de nube para su entorno de pruebas y desarrollo de Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[Una protección avanzada para su entorno de pruebas y desarrollo de Office 365](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
  
[Adopción de la nube y soluciones híbridas](cloud-adoption-and-hybrid-solutions.md)




