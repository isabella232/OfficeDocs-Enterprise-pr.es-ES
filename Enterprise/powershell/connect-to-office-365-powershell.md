---
title: Conectarse a PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- O365ITProTrain
- DecEntMigration
- apr17entnews
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: "Resumen: Conectarse a su organización de Office 365 mediante Office 365 PowerShell para realizar tareas del centro de administración de Office 365 desde la línea de comandos."
ms.openlocfilehash: 3ac368a3d3584c15e1d0c26104616e8258a78e7b
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2017
---
# <a name="connect-to-office-365-powershell"></a>Conectarse a PowerShell de Office 365

 **Resumen:** Conectarse a su organización de Office 365 mediante Office 365 PowerShell para realizar tareas de administración de Office 365 desde la línea de comandos.
  
Office 365 PowerShell permite administrar la configuración de Office 365 desde la línea de comandos. Conectarse a Office 365 PowerShell es un proceso sencillo de tres pasos donde instalar el software necesario, ejecutar el software necesario y, a continuación, conectarse a su organización de Office 365. 

Tenga en cuenta que estas instrucciones de conexión son las mismas que las del tema [ActiveDirectory Azure (MSOnline)](https://go.microsoft.com/fwlink/p/?LinkId=528113).
  
> [!TIP]
> **Nuevo a PowerShell?** Vea un [Vídeo de información general de PowerShell](http://technet.microsoft.com/library/https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), ofrecido por aprendizaje de LinkedIn. 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>¿Qué necesita saber antes de comenzar?

- Tiempo estimado para finalizar: 5 minutos
    
- Puede usar las siguientes versiones de Windows:
    
  - Windows 10, Windows 8.1, Windows 8 o Windows 7 Service Pack 1 (SP1) 
    
  - Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 o Windows Server 2008 R2 SP1
    
    > [!NOTE]
    >Utilice una versión de 64 bits de Windows. Soporte para la versión de 32 bits del Microsoft Azure Active Directory módulo para Windows PowerShell se interrumpió en octubre de 2014.
    
-  El Office 365 trabajo o escuela cuenta utilizar para estos procedimientos necesidades para ser miembro de una función de administración de Office 365. Para obtener más información, consulte [las funciones de administrador acerca de Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).
    
## <a name="step-1-install-required-software"></a>Paso 1: instalar el software necesario

Estos pasos son necesarios una sola vez en el equipo, no cada vez que se conecta. Sin embargo, probablemente necesitará instalar las versiones más recientes de software periódicamente.
  
1.  Instalar la versión de 64 bits del Ayudante de inicio de sesión de Microsoft Online Services: [Asistente de inicio de sesión de Microsoft Online Services para RTW de profesionales de TI](https://go.microsoft.com/fwlink/p/?LinkId=286152).
    
2. Instale la versión de 64 bits de Módulo de Microsoft Azure Active Directory para Windows PowerShell siguiendo estos pasos:
    
  - Abra la página web [Azure Active Directory Connection](http://connect.microsoft.com/site1164/Downloads/DownloadDetails.aspx?DownloadID=59185).
    
  - En **Archivos para descargar**, en la parte inferior de la página, haga clic en el botón **Descargar** del archivo **AdministrationConfig-V1.1.166.0-GA.msi** e instálelo.
    
## <a name="step-2-open-the-windows-azure-active-directory-module"></a>Paso 2: abrir el módulo Active Directory de Windows Azure

1. Busque y abra Módulo de Microsoft Azure Active Directory para Windows PowerShell mediante uno de los métodos siguientes según la versión de Windows:
    
  - **Menú Inicio** En el escritorio, haga clic en **Inicio** y escribaAzure.
    
  - **No hay menú Inicio** BusqueAzure mediante cualquiera de estos métodos:
    
  - En la pantalla Inicio, haga clic en un área vacía y escriba Azure.
    
  - En el escritorio o la pantalla Inicio, pulse la tecla Windows + Q. En el acceso Buscar, escriba Azure.
    
  - En el escritorio o la pantalla de inicio, mueva el cursor a la esquina superior derecha, o Deslizar hacia la izquierda desde el borde derecho de la pantalla para mostrar los encantos. Seleccione los bueno de búsqueda y escriba **Azure**.
    
2. En los resultados, haga clic en **Módulo de Microsoft Azure Active Directory para Windows PowerShell**.
    
## <a name="step-3-connect-to-your-office-365-subscription"></a>Paso 3: conectarse a la suscripción de Office 365
<a name="step3"> </a>

Para conectarse con solo el  *nombre de cuenta y la contraseña*  :
  
1. Ejecute los comandos siguientes en la ventana de comandos **Módulo de Microsoft Azure Active Directory para Windows PowerShell**.
    
  ```
  $UserCredential = Get-Credential
Connect-MsolService -Credential $UserCredential
  ```

2. En el cuadro de diálogo **Solicitud de credenciales para Windows PowerShell**, escriba su nombre de usuario y contraseña de Office 365cuenta profesional o educativa y, luego, haga clic en **Aceptar**.
    
Para conectarse mediante la  *autenticación multifactor (AMF)*  :
  
1. Ejecute el comando siguiente en la ventana de comandos **Módulo de Microsoft Azure Active Directory para Windows PowerShell**.
    
  ```
  Connect-MsolService
  ```

2. En el cuadro de diálogo **Azure Active Directory PowerShell**, escriba su nombre de usuario y contraseña de Office 365cuenta profesional o educativa y, a continuación, haga clic en **Iniciar sesión**.
    
3. Siga las instrucciones del cuadro de diálogo de **Azure Active Directory PowerShell** para proporcionar información de autenticación adicional, como un código de comprobación, y haga clic en **Iniciar sesión**.
    
## <a name="how-do-you-know-this-worked"></a>¿Cómo saber si el proceso se ha completado correctamente?
<a name="step3"> </a>

Si no se muestra ningún error, la conexión se habrá establecido correctamente. Para hacer una prueba rápida, ejecute un cmdlet de Office 365, como **Get-MsolUser**, y vea los resultados.
  
Si surgen errores, compruebe los siguientes requisitos:
  
- **Un problema habitual es una contraseña incorrecta**. Vuelva a realizar el paso 3 y preste especial atención al nombre de usuario y la contraseña que escriba.
    
- **Módulo de Microsoft Azure Active Directory para Windows PowerShell requiere que la característica Microsoft .NET Framework 3.5. _x_ esté habilitada en el equipo**. Es probable que el equipo tenga instalada una versión más reciente (por ejemplo, 4 o 4.5. _x_), pero sea posible habilitar o deshabilitar la compatibilidad con versiones anteriores de .NET Framework. Para obtener más información al respecto, consulte los temas siguientes:
    
  - Para Windows Server 2012 o 2012 R2 de Windows Server, vea [Habilitar.NET Framework 3.5 mediante el agregar funciones y características de asistente](https://go.microsoft.com/fwlink/p/?LinkId=532368)
    
  - Para Windows 8 o Windows 8.1, vea [instalar el 3.5 de.NET Framework en Windows 8 o 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369)
    
  - Para Windows 7 o Windows Server 2008 R2, vea [no se puede abrir Azure Active Directory módulo para Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)
    
- **Puede que su versión de Módulo de Microsoft Azure Active Directory para Windows PowerShell esté obsoleta.** Para comprobarlo, ejecute el siguiente comando en PowerShell de Office 365 o Módulo de Microsoft Azure Active Directory para Windows PowerShell:
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    Si el número de versión devuelto es menor que el valor 1.0.8070.2, desinstale el Módulo de Microsoft Azure Active Directory para Windows PowerShell e instale la versión más reciente desde el vínculo en el paso 1.
    
- **Si recibe un error de conexión, vea este tema:** ["Connect-MsolService: excepción de tipo" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).
    
## <a name="connect-with-the-azure-active-directory-v2-powershell-module"></a>Conectarse con el módulo de PowerShell Azure Active Directory V2
<a name="ConnectV2"> </a>

Para los procedimientos que necesitan los nuevos cmdlets del [módulo de PowerShell Azure Active Directory V2](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory), siga estos pasos para instalar el módulo y conectarse a su suscripción a Office 365:
  
1. Abra un símbolo del sistema de Windows PowerShell con privilegios elevados (ejecute Windows PowerShell como administrador).
    
2. En la ventana de comandos **Administrador: Windows PowerShell**, ejecute este comando:
    
  ```
  Install-Module -Name AzureAD 
  ```

Si se le pregunta si quiere instalar un módulo desde un repositorio que no es de confianza, escriba **Y** y presione ENTRAR.
    
3. Cuando se complete la instalación del nuevo módulo, use estos comandos para conectarse a su suscripción a Office 365:
    
  -  Con un  *nombre de cuenta y contraseña*  :
    
  ```
  $UserCredential = Get-Credential
Connect-AzureAD -Credential $UserCredential
  ```

 En el cuadro de diálogo **Solicitud de credenciales para Windows PowerShell**, escriba su nombre de usuario y contraseña de Office 365cuenta profesional o educativa y, luego, haga clic en **Aceptar**.
    
  - Con la  *autenticación multifactor (MFA)*  :
    
  ```
  Connect-AzureAD
  ```

En el cuadro de diálogo **Azure Active Directory PowerShell**, escriba su nombre de usuario y contraseña de Office 365cuenta profesional o educativa y, a continuación, haga clic en **Iniciar sesión**.
    
Siga las instrucciones del cuadro de diálogo de **Azure Active Directory PowerShell** para proporcionar información de autenticación adicional, como un código de comprobación, y haga clic en **Iniciar sesión**.
    
Después de conectarse, podrá usar los nuevos cmdlets del [módulo de PowerShell Azure Active Directory V2](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).
  
## <a name="see-also"></a>See also

#### 

[Administrar Office 365 con PowerShell de Office 365](manage-office-365-with-office-365-powershell.md)
  
[Introducción a PowerShell de Office 365](getting-started-with-office-365-powershell.md)
  
[Conectarse a todos los servicios de Office 365 en una sola ventana de Windows PowerShell](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
#### 

[Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618)
  
[MsolService conectar](https://go.microsoft.com/fwlink/p/?LinkId=532375)

