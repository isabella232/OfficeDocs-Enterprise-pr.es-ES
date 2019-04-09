---
title: Configurar la sincronización de directorios para el entorno de desarrollo y pruebas de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: e6b27e25-74ae-4b54-9421-c8e911aef543
description: 'Resumen: configure la sincronización de directorios para el entorno de desarrollo y pruebas de Office 365.'
ms.openlocfilehash: d5aff42837d3cf4789cf8785383ad213f98d35a3
ms.sourcegitcommit: 201d3338d8bbc6da9389e62e2add8a17384fab4d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "31037914"
---
# <a name="directory-synchronization-for-your-office-365-devtest-environment"></a>Configurar la sincronización de directorios para el entorno de desarrollo y pruebas de Office 365

 **Resumen:** configure la sincronización de directorios para el entorno de desarrollo y pruebas de Office 365.
  
Muchas organizaciones usan Azure AD Connect y la sincronización de directorios para sincronizar el conjunto de cuentas de su bosque de Active Directory Domain Services (AD DS) local para el conjunto de cuentas de Office 365. En este artículo, se describe cómo agregar la sincronización de directorios con la sincronización de hash de contraseña al entorno de desarrollo y pruebas de Office 365, lo que da como resultado la siguiente configuración.
  
![Entorno de desarrollo y pruebas de Office 365 con sincronización de directorios](media/be5b37b0-f832-4878-b153-436c31546e21.png)
  
Esta configuración se compone de: 
  
- Una suscripción de prueba a Office 365 E5, que expira a los 30 días de su creación.
- La intranet de una organización simplificada conectada a Internet, que consta de tres máquinas virtuales en una subred de una red virtual de Azure (DC1, APP1 y CLIENTE1). Azure AD Connect se ejecuta en APP1 para sincronizar el dominio de AD DS con Office 365.
    
Existen dos fases para configurar el entorno de desarrollo y pruebas:
  
1. Crear el entorno de desarrollo y pruebas de Office 365 (las máquinas virtuales DC1, APP1 y CLIENTE1 en una red virtual Azure con una suscripción de prueba a Office 365 E5).
2. Instalar y configurar Azure AD Connect en APP1.
    
> [!TIP]
> Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual de todos los artículos en la pila de la Guía del entorno de pruebas de One Microsoft Cloud.
  
## <a name="phase-1-create-an-office-365-devtest-environment"></a>Fase 1: Crear un entorno de desarrollo y pruebas de Office 365

Siga las instrucciones de las fases 1, 2 y 3 del artículo [Entorno de desarrollo y pruebas de Office 365](office-365-dev-test-environment.md). Esta es la configuración resultante.
  
![El entorno de desarrollo y pruebas de Office 365](media/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
Esta configuración se compone de: 
  
- Una suscripción de prueba a Office 365 E5.
- La intranet de una organización simplificada conectada a Internet, que consta de las máquinas virtuales DC1, APP1 y CLIENTE1 en una subred de una red virtual de Azure.
    
## <a name="phase-2-install-azure-ad-connect-on-app1"></a>Fase 2: Instalar Azure AD Connect en APP1

Una vez instalado y configurado, Azure AD Connect sincroniza el conjunto de cuentas del dominio de AD DS de CORP con el conjunto de cuentas de su suscripción de prueba a Office 365. El siguiente procedimiento le guía a través de la instalación de Azure AD Connect en APP1 y la comprobación de que funciona.
  
### <a name="install-and-configure-azure-ad-connect-on-app1"></a>Instalar y configurar Azure AD Connect en APP1

1. En [Azure Portal](https://portal.azure.com), conéctese a APP1 con la cuenta CORP\\Usuario1.
    
2. Desde APP1, abra un símbolo del sistema de Windows PowerShell con el nivel de administrador y ejecute estos comandos:
    
  ```
  Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Stop-Process -Name Explorer -Force

  ```

3. En la barra de tareas, haga clic en **Internet Explorer** y vaya a [https://aka.ms/aadconnect](https://aka.ms/aadconnect).
    
4. En la página de Microsoft Azure Active Directory Connect, haga clic en **Descargar** y, después, en **Ejecutar**.
    
5. En la página **Bienvenido a Azure AD Connect**, haga clic en **Acepto** y, después, en **Continuar**.
    
6. En la página **Configuración rápida**, haga clic en **Usar configuración rápida**.
    
7. En la página **Conectar a Azure AD**, escriba el nombre de la cuenta de administrador global en **Nombre de usuario**, escriba la contraseña en **Contraseña** y, después, haga clic en **Siguiente**.
    
8. En la página **Conectarse a AD DS**, escriba **CORP\\Usuario1** en **Nombre de usuario**, escriba la contraseña en **Contraseña** y, después, haga clic en **Siguiente**.
    
9. En la página **Configuración de inicio de sesión de Azure AD**, haga clic en **Continuar sin dominios comprobados** y después en **Siguiente**.
    
10. En la página **Listo para configurar**, haga clic en **Instalar**.
    
11. En la página **Configuración completada** de página, haga clic en **Salir**.
    
12. En Internet Explorer, vaya al Centro de administración de Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com)) e inicie sesión en la suscripción de prueba de Office 365 con la cuenta de administrador global.
    
13. En la página principal del portal, haga clic en **Administración**.
    
14. En el panel de navegación izquierdo, haga clic en **Usuarios > Usuarios activos**.
    
    Observe la cuenta llamada **Usuario1**. Esta cuenta pertenece al dominio de AD DS de CORP y es una prueba de que la sincronización de directorios funcionó correctamente.
    
15. Haga clic en la cuenta **Usuario1**. Para licencias de productos, haga clic en **Editar**.
    
16. En **Licencias de productos**, seleccione su país y, después, haga clic en el control **Desactivado** de **Office 365 Enterprise E5** (para cambiarlo a **Activado**). Haga clic en **Guardar** en la parte inferior de la página y, después, en **Cerrar**.
    
Esta es la configuración resultante.
  
![Entorno de desarrollo y pruebas de Office 365 con sincronización de directorios](media/be5b37b0-f832-4878-b153-436c31546e21.png)
  
Esta configuración se compone de: 
  
- Una suscripción de prueba a Office 365 E5.
- La intranet de una organización simplificada conectada a Internet, que consta de las máquinas virtuales DC1, APP1 y CLIENTE1 en una subred de una red virtual de Azure. Azure AD Connect se ejecuta en APP1 para sincronizar el dominio de AD DS de CORP con Office 365 cada 30 minutos.
    
## <a name="next-step"></a>Paso siguiente

Cuando esté preparado para implementar la sincronización de directorios para su organización, vea [Implementar la sincronización de directorios de Office 365 en Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).

## <a name="see-also"></a>Vea también

[Guías del laboratorio de pruebas de adopción de la nube (TLG)](cloud-adoption-test-lab-guides-tlgs.md)

[Entorno de desarrollo y pruebas de la configuración básica](base-configuration-dev-test-environment.md)

[Entorno de desarrollo y pruebas de Office 365](office-365-dev-test-environment.md)

[Cloud App Security para el entorno de desarrollo y pruebas de Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md)

[Protección contra amenazas avanzada en el entorno de desarrollo y prueba de Office 365](advanced-threat-protection-for-your-office-365-dev-test-environment.md)

[Adopción de la nube y soluciones híbridas](cloud-adoption-and-hybrid-solutions.md)




