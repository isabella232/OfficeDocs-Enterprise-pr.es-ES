---
title: Conectarse a PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/16/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: 'Resumen: Conéctese a la organización de Office 365 con Office 365 PowerShell para realizar tareas de centro de administración de la línea de comandos.'
ms.openlocfilehash: d9bee7060f599120d2d6036c45b44e485ea9a0bd
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849896"
---
# <a name="connect-to-office-365-powershell"></a>Conectarse a PowerShell de Office 365

 **Resumen:** Conectarse a la organización de Office 365 con Office 365 PowerShell para realizar tareas de administración desde la línea de comandos.
  
PowerShell de Office 365 le permite administrar la configuración de Office 365 desde la línea de comandos. Conectarse a Office 365 PowerShell es un proceso simple que instalar el software requerido y, a continuación, conectarse a la organización de Office 365. 

Hay dos versiones del módulo de PowerShell que use para conectarse a Office 365 y administrar las licencias, grupos y cuentas de usuario:

- Azure Active Directory PowerShell para gráfico (cmdlets incluir **AzureAD** en su nombre) 
- Microsoft Azure Active Directory módulo para Windows PowerShell (cmdlets incluir **MSol** en su nombre) 

A partir de la fecha de este artículo, Azure Active Directory PowerShell para el módulo de gráfico no reemplazar completamente la funcionalidad en los cmdlets del módulo de Microsoft Azure Active Directory módulo para Windows PowerShell para el usuario, grupo y administración de licencias . En muchos casos, debe utilizar las dos versiones. Forma segura puede instalar ambas versiones en el mismo equipo.

> [!TIP]
> **¿Es la primera vez que usa PowerShell?** Vea el [vídeo de información general sobre PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx) ofrecido por LinkedIn Learning. 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>¿Qué necesita saber antes de comenzar?

- Tiempo estimado para finalizar: 5 minutos
    
- Puede usar las siguientes versiones de Windows:
    
  - 10 de Windows, Windows 8.1, Windows 8 o Windows 7 Service Pack 1 (SP1) 
    
  - Windows Server 2019, 2016 de Windows Server, Windows Server 2012 R2, Windows Server 2012 o Windows Server 2008 R2 SP1
    
    > [!NOTE]
    >Use una versión de 64 bits de Windows. La compatibilidad con la versión de 32 bits de Módulo de Microsoft Azure Active Directory para Windows PowerShell se descontinuó en octubre de 2014.
    
-  Estos procedimientos están diseñados para los usuarios que son miembros de un rol de administración de Office 365. Para obtener más información, vea [roles de administrador acerca de Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a>Conectar con Azure Active Directory PowerShell para el módulo de gráfico

Comandos en el módulo [Azure Active Directory PowerShell para gráfico](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) tienen **AzureAD** en su nombre de cmdlet.

Para conocer los procedimientos que requieren los nuevos cmdlets en Azure Active Directory PowerShell para el módulo de gráfico, siga estos pasos para instalar el módulo y conectarlo a su suscripción de Office 365.

>[!Note]
>Para obtener información acerca de la compatibilidad con diferentes versiones de Microsoft Windows, vea [Windows Azure Active Directory PowerShell para el módulo de gráfico](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) .
>

### <a name="step-1-install-required-software"></a>Paso 1: Instalar el software necesario

Estos pasos son necesarios una sola vez en el equipo, no cada vez que se conecta. Sin embargo, probablemente necesitará instalar las versiones más recientes de software periódicamente.
  
1. Abra un símbolo del sistema de Windows PowerShell con privilegios elevados (ejecute Windows PowerShell como administrador).
    
2. En la ventana de comandos **Administrador: Windows PowerShell**, ejecute este comando:
    
  ```
  Install-Module -Name AzureAD
  ```

Si se le pregunta si quiere instalar un módulo desde un repositorio que no es de confianza, escriba **Y** y presione ENTRAR.

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a>Paso 2: Conectarse a Azure AD para su suscripción de Office 365

Para conectarse a Azure AD para su suscripción de Office 365 con un nombre de cuenta y una contraseña o con *autenticación multifactor (MFA)*, ejecute uno de estos comandos desde un símbolo del sistema de Windows PowerShell (no tiene que ser con privilegios elevados).

|||
|:-------|:-----|
| **Nube de Office 365** | **Comando** |
| Office 365 en todo el mundo (+ GCC) | `Connect-AzureAD` |
| Office 365 operado por Vianet 21 | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| Office 365 Germany | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| DoD de gobierno de Estados Unidos de Office 365 y gobierno de Estados Unidos de Office 365 GCC alta | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

En el cuadro de diálogo **Inicio de sesión en su cuenta** , escriba su trabajo de Office 365 o nombre de usuario de escuela cuenta y contraseña y, a continuación, haga clic en **Aceptar**.

Si está utilizando MFA, siga las instrucciones que aparecen en los cuadros de diálogo adicionales para proporcionar más información de autenticación, como un código de comprobación.


Después de conectar, puede usar los cmdlets de nuevo para el [Azure Active Directory PowerShell para el módulo de gráfico](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Conectar con el Módulo Microsoft Azure Active Directory para Windows PowerShell

Los comandos del Módulo Microsoft Azure Active Directory para Windows PowerShell tienen **Msol** en el nombre de su cmdlet.
    
### <a name="step-1-install-required-software"></a>Paso 1: Instalar el software necesario

Estos pasos son necesarios una sola vez en el equipo, no cada vez que se conecta. Sin embargo, probablemente necesitará instalar las versiones más recientes de software periódicamente.
  
1.  Instale la versión de 64 bits de Microsoft Online Services - Ayudante para el inicio de sesión: [Ayudante para el inicio de sesión de Microsoft Online Services para profesionales de TI (RTW)](https://go.microsoft.com/fwlink/p/?LinkId=286152).
    
2. Instale el Módulo Microsoft Azure Active Directory para Windows PowerShell siguiendo estos pasos:
    
  - Abra un símbolo del sistema de Windows PowerShell con privilegios elevados (ejecute Windows PowerShell como administrador).
  - Ejecute el comando **Install-Module MSOnline**.
  - Si se le pide que instale el proveedor de NuGet, escriba **Y** y presione ENTRAR.
  - Si se le pide que instale el módulo desde PSGallery, escriba **Y** y presione ENTRAR.
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a>Paso 2: Conectarse a Azure AD para su suscripción de Office 365

Para conectarse a Azure AD para su suscripción de Office 365 con un nombre de cuenta y una contraseña o con *autenticación multifactor (MFA)*, ejecute uno de estos comandos desde un símbolo del sistema de Windows PowerShell (no tiene que ser con privilegios elevados).

|||
|:-------|:-----|
| **Nube de Office 365** | **Comando** |
| Office 365 en todo el mundo (+ GCC) | `Connect-MsolService` |
| Office 365 operado por Vianet 21 | `Connect-MsolService -AzureEnvironmentName AzureChinaCloud` |
| Office 365 Germany | `Connect-MsolService -AzureEnvironmentName AzureGermanyCloud` |
| DoD de gobierno de Estados Unidos de Office 365 y gobierno de Estados Unidos de Office 365 GCC alta | `Connect-MsolService -AzureEnvironmentName USGovernment` |
|||

En el cuadro de diálogo **Inicio de sesión en su cuenta** , escriba su trabajo de Office 365 o nombre de usuario de escuela cuenta y contraseña y, a continuación, haga clic en **Aceptar**.

Si está utilizando MFA, siga las instrucciones que aparecen en los cuadros de diálogo adicionales para proporcionar más información de autenticación, como un código de comprobación.

### <a name="how-do-you-know-this-worked"></a>¿Cómo saber si el proceso se ha completado correctamente?

Si no se muestra ningún error, la conexión se habrá establecido correctamente. Para hacer una prueba rápida, ejecute un cmdlet de Office 365, como **Get-MsolUser**, y vea los resultados.
  
Si surgen errores, compruebe los siguientes requisitos:
  
- **Un problema común es una contraseña incorrecta**. Vuelva a ejecutar el paso 2. y preste especial atención para el nombre de usuario y la contraseña que especifique.
    
- **El Módulo de Microsoft Azure Active Directory para Windows PowerShell requiere que la característica Microsoft .NET Framework 3.5.* x* esté habilitada en el equipo**. Es probable que el equipo tenga instalada una versión más reciente (por ejemplo, 4 o 4.5. *x*), pero sea posible habilitar o deshabilitar la compatibilidad con versiones anteriores de .NET Framework. Para obtener más información al respecto, consulte los temas siguientes:
    
  - Para Windows Server 2012 o Windows Server 2012 R2, vea [Habilitar .NET Framework 3.5 con el Asistente para agregar roles y características](https://go.microsoft.com/fwlink/p/?LinkId=532368).
    
  - Para Windows 7 o Windows Server 2008 R2, vea [No puede abrir el Módulo de Azure Active Directory para Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370).

  - Para Windows 10, Windows 8.1 y Windows 8, vea [instalar .NET Framework 3.5 en 10 de Windows, Windows 8.1 y Windows 8](https://docs.microsoft.com/en-us/dotnet/framework/install/dotnet-35-windows-10)

  
- **Puede que su versión de Módulo de Microsoft Azure Active Directory para Windows PowerShell esté obsoleta.** Para comprobarlo, ejecute el siguiente comando en PowerShell de Office 365 o Módulo de Microsoft Azure Active Directory para Windows PowerShell:
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    Si el número de versión devuelto es menor que el valor 1.0.8070.2, desinstale el Módulo de Microsoft Azure Active Directory para Windows PowerShell e instale la versión más reciente desde el vínculo en el paso 1.
    
- **Si recibe un error de conexión, vea este tema:** [Error “Connect-MsolService: Se produjo una excepción de tipo”](https://go.microsoft.com/fwlink/p/?LinkId=532377).
    

## <a name="see-also"></a>Consulte también

- [Administrar Office 365 con PowerShell de Office 365](manage-office-365-with-office-365-powershell.md)
- [Introducción a PowerShell de Office 365](getting-started-with-office-365-powershell.md)
- [Conectarse a todos los servicios de Office 365 en una sola ventana de Windows PowerShell](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
- [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618)
- [Connect-MsolService](https://go.microsoft.com/fwlink/p/?LinkId=532375)

