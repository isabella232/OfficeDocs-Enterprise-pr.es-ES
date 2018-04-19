---
title: Conectarse a PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: 'Resumen: conéctese a su organización de Office 365 con PowerShell de Office 365 para realizar tareas del Centro de administración de Office 365 desde la línea de comandos.'
ms.openlocfilehash: 71b8c8d61a914fa7fd036fadb7e17ca3f66cd639
ms.sourcegitcommit: 62c0630cc0d2611710e73e0592bddfe093e00783
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="connect-to-office-365-powershell"></a>Conectarse a PowerShell de Office 365

 **Resumen:** conéctese a su organización de Office 365 con PowerShell de Office 365 para realizar tareas de administración de Office 365 desde la línea de comandos.
  
Con PowerShell de Office 365, se puede configurar Office 365 desde la línea de comandos. Conectarse a PowerShell de Office 365 es un sencillo proceso de tres pasos con el que instalará el software, ejecutará el software necesario y, después, se conectará a la organización de Office 365. 

  
> [!TIP]
> **¿Es la primera vez que usa PowerShell?** Vea el [vídeo de información general sobre PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx) ofrecido por LinkedIn Learning. 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>¿Qué necesita saber antes de empezar?

- Tiempo estimado para finalizar: 5 minutos
    
- Puede usar las siguientes versiones de Windows:
    
  - Windows 10, Windows 8.1, Windows 8 o Windows 7 Service Pack 1 (SP1) 
    
  - Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 o Windows Server 2008 R2 SP1
    
    > [!NOTE]
    >Use una versión de 64 bits de Windows. La compatibilidad con la versión de 32 bits de Módulo de Microsoft Azure Active Directory para Windows PowerShell se descontinuó en octubre de 2014.
    
-  Estos procedimientos están destinados a usuarios que son miembros de una función de administración de Office 365. Para obtener más información, consulte [las funciones de administrador acerca de Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Conectar con el Módulo Microsoft Azure Active Directory para Windows PowerShell

Los comandos del Módulo Microsoft Azure Active Directory para Windows PowerShell tienen **Msol** en el nombre de su cmdlet.
    
### <a name="step-1-install-required-software"></a>Paso 1: Instalar el software necesario

Estos pasos son necesarios una sola vez en el equipo, no cada vez que se conecta. Sin embargo, probablemente necesitará instalar las versiones más recientes de software periódicamente.
  
1.  Instale la versión de 64 bits de Microsoft Online Services - Ayudante para el inicio de sesión: [Ayudante para el inicio de sesión de Microsoft Online Services para profesionales de TI (RTW)](https://go.microsoft.com/fwlink/p/?LinkId=286152).
    
2. Instale el Módulo Microsoft Azure Active Directory para Windows PowerShell siguiendo estos pasos:
    
  - Abra un símbolo del sistema de PowerShell con permisos de administrador.
  - Ejecute el comando **Install-Module MSOnline**.
  - Si se le pide que instale el proveedor de NuGet, escriba **Y** y presione ENTRAR.
  - Si se le pide que instale el módulo desde PSGallery, escriba **Y** y presione ENTRAR.
  - Después de la instalación, cierre la ventana de comandos de PowerShell.
    
### <a name="step-2-connect-to-your-office-365-subscription"></a>Paso 2: Conectarse a la suscripción de Office 365
<a name="step3"> </a>

Para conectarse solo con el *nombre de cuenta y la contraseña*:
  
1. Ejecute un símbolo del sistema de Windows PowerShell.
2. En la ventana de comandos de **Windows PowerShell**, ejecute los comandos siguientes:
    
```
$UserCredential = Get-Credential
Connect-MsolService -Credential $UserCredential
```

3. En el cuadro de diálogo **Solicitud de credenciales para Windows PowerShell**, escriba su nombre de usuario y contraseña de Office 365cuenta profesional o educativa y, luego, haga clic en **Aceptar**.
    
Para conectarse mediante la *autenticación multifactor (MFA)*:
  
1. Ejecute un símbolo del sistema de Windows PowerShell.
2. Ejecute el comando siguiente en la ventana de comandos del **Módulo Microsoft Azure Active Directory para Windows PowerShell**.
    
```
Connect-MsolService
```

3. En el cuadro de diálogo **Azure Active Directory PowerShell**, escriba su nombre de usuario y contraseña de Office 365cuenta profesional o educativa y, a continuación, haga clic en **Iniciar sesión**.
    
4. Siga las instrucciones del cuadro de diálogo de **Azure Active Directory PowerShell** para proporcionar información de autenticación adicional, como un código de comprobación, y haga clic en **Iniciar sesión**.
    
### <a name="how-do-you-know-this-worked"></a>¿Cómo saber si el proceso se ha completado correctamente?
<a name="step3"> </a>

Si no se muestra ningún error, la conexión se habrá establecido correctamente. Para hacer una prueba rápida, ejecute un cmdlet de Office 365, como **Get-MsolUser**, y vea los resultados.
  
Si surgen errores, compruebe los siguientes requisitos:
  
- **Un problema habitual es una contraseña incorrecta**. Vuelva a realizar el paso 3 y preste especial atención al nombre de usuario y la contraseña que escriba.
    
- **El Módulo de Microsoft Azure Active Directory para Windows PowerShell requiere que la característica Microsoft .NET Framework 3.5.*x* esté habilitada en el equipo**. Es probable que el equipo tenga instalada una versión más reciente (por ejemplo, 4 o 4.5. *x*), pero sea posible habilitar o deshabilitar la compatibilidad con versiones anteriores de .NET Framework. Para obtener más información al respecto, consulte los temas siguientes:
    
  - Para Windows Server 2012 o Windows Server 2012 R2, vea [Habilitar .NET Framework 3.5 con el Asistente para agregar roles y características](https://go.microsoft.com/fwlink/p/?LinkId=532368).
    
  - Para Windows 8 o Windows 8.1, vea [Instalar .NET Framework 3.5 en Windows 8 u 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369).
    
  - Para Windows 7 o Windows Server 2008 R2, vea [No puede abrir el Módulo de Azure Active Directory para Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370).
    
- **Puede que su versión de Módulo de Microsoft Azure Active Directory para Windows PowerShell esté obsoleta.** Para comprobarlo, ejecute el siguiente comando en PowerShell de Office 365 o Módulo de Microsoft Azure Active Directory para Windows PowerShell:
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    Si el número de versión devuelto es menor que el valor 1.0.8070.2, desinstale el Módulo de Microsoft Azure Active Directory para Windows PowerShell e instale la versión más reciente desde el vínculo en el paso 1.
    
- **Si recibe un error de conexión, vea este tema:** [Error “Connect-MsolService: Se produjo una excepción de tipo”](https://go.microsoft.com/fwlink/p/?LinkId=532377).
    
## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a>Conectar con el PowerShell de Azure Active Directory para el módulo de gráfico
<a name="ConnectV2"> </a>

Comandos en el PowerShell de Azure Active Directory para el módulo de gráfico tienen "AzureAD" en el nombre de cmdlet.

Procedimientos que requieren los nuevos cmdlets en el PowerShell de Azure Active Directory para el módulo de gráfico, siga estos pasos para instalar el módulo y conectar a su suscripción de Office 365.

>[!Note]
>Para obtener información acerca de la compatibilidad con diferentes versiones de Microsoft Windows, consulte [Azure Active Directory PowerShell para módulo de gráfico](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) .
>

### <a name="step-1-install-required-software"></a>Paso 1: Instalar el software necesario

Estos pasos son necesarios una sola vez en el equipo, no cada vez que se conecta. Sin embargo, probablemente necesitará instalar las versiones más recientes de software periódicamente.

  
1. Abra un símbolo del sistema de Windows PowerShell con privilegios elevados (ejecute Windows PowerShell como administrador).
    
2. En la ventana de comandos **Administrador: Windows PowerShell**, ejecute este comando:
    
  ```
  Install-Module -Name AzureAD 
  ```

Si se le pregunta si quiere instalar un módulo desde un repositorio que no es de confianza, escriba **Y** y presione ENTRAR.


### <a name="step-2-connect-to-office-365"></a>Paso 2: Conectarse a Office 365

Para conectarse a su suscripción de Office 365 mediante el *nombre de cuenta y la contraseña*:
    
```
$UserCredential = Get-Credential
Connect-AzureAD -Credential $UserCredential
```

En el cuadro de diálogo **Solicitud de credenciales para Windows PowerShell**, escriba su nombre de usuario y contraseña de Office 365cuenta profesional o educativa y, luego, haga clic en **Aceptar**.
    
Para conectarse a su suscripción de Office 365 mediante la *autenticación multifactor (MFA)*:

```
Connect-AzureAD
```

En el cuadro de diálogo **Azure Active Directory PowerShell**, escriba su nombre de usuario y contraseña de Office 365cuenta profesional o educativa y, a continuación, haga clic en **Iniciar sesión**.
    
Siga las instrucciones del cuadro de diálogo de **Azure Active Directory PowerShell** para proporcionar información de autenticación adicional, como un código de comprobación, y haga clic en **Iniciar sesión**.
    
Después de conectarse, puede usar los cmdlets de nuevo para el [Azure Active Directory PowerShell para módulo de gráfico](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).
  
## <a name="see-also"></a>Consulte también

- [Administrar Office 365 con PowerShell de Office 365](manage-office-365-with-office-365-powershell.md)
- [Introducción a PowerShell de Office 365](getting-started-with-office-365-powershell.md)
- [Conectarse a todos los servicios de Office 365 en una sola ventana de Windows PowerShell](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
- [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618)
- [Connect-MsolService](https://go.microsoft.com/fwlink/p/?LinkId=532375)

