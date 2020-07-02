---
title: Conectarse a los inquilinos de Exchange Online con el modo remoto de Windows PowerShell para asociados con permiso de acceso delegado (DAP)
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: ae5f1a87-8b77-4f93-a1b8-56f800aeb283
description: 'Resumen: use el modo remoto de Windows PowerShell para conectarse a Exchange Online con el valor DelegatedOrg.'
ms.openlocfilehash: 4a9f08325fc56308b27467423b047375985562c5
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997376"
---
# <a name="connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated-access-permissions-dap-partners"></a>Conectarse a los inquilinos de Exchange Online con el modo remoto de Windows PowerShell para asociados con permiso de acceso delegado (DAP)

> [!IMPORTANT]
> The procedures in this topic are only for Delegated Access Permission (DAP) partners. If you aren't a DAP partner, don't use the procedures in this topic. 
  
Los asociados con DAP son asociados de proveedor de soluciones en la nube (CSP) y redifusión web. Generalmente son proveedores de red o de telecomunicaciones para otras compañías. Agrupan las suscripciones en sus ofertas de servicio para sus clientes. Poseen un arrendamiento de Partners al que se conceden automáticamente permisos de administración en nombre de (AOBO) para los arrendamientos de clientes de Microsoft 365 para que puedan administrar y informar sobre todos los arrendamientos de clientes.

Los asociados de DAP pueden usar Exchange Online PowerShell para administrar la configuración de Exchange online de clientes y obtener los informes de Microsoft 365 desde la línea de comandos. Use la sesión de Windows PowerShell en su equipo local para crear una sesión remota de PowerShell en Exchange Online. Se trata de un proceso de tres pasos sencillo donde se escriben las credenciales, se proporcionan las opciones de conexión necesarias y, a continuación, se importan los cmdlets de Exchange Online a la sesión local de Windows PowerShell para que se puedan usar.

> [!NOTE]
> DAP partners can't use the procedures in [Connect to Exchange Online PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell) to connect to their customer tenant organizations in Exchange Online PowerShell. MFA and the Exchange Online Remote PowerShell Module don't work with delegated authentication.
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>¿Qué necesita saber antes de comenzar?

- Tiempo estimado para finalizar: 5 minutos

- Puede usar las siguientes versiones de Windows:
    
  - Windows 10

  - Windows 8.1

  - Windows Server 2016

  - Windows Server 2012 o Windows Server 2012 R2

  - Windows 7 Service Pack 1 (SP1)<sup>*</sup>

  - Windows Server 2008 R2 SP1<sup>*</sup>

    <sup>*</sup> For older versions of Windows, you need to install the Microsoft.NET Framework 4.5 or later and then an updated version of the Windows Management Framework: 3.0, 4.0, or 5.1 (only one). For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868), [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757), [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344), and [Windows Management Framework 5.1](https://aka.ms/wmf5download).

- Windows PowerShell needs to be configured to run scripts, and by default, it isn't. You'll get the following error when you try to connect:

  `Files cannot be loaded because running scripts is disabled on this system. Provide a valid certificate with which to sign the files.`

  Para requerir que todos los scripts de PowerShell que se descargue de internet sean de publicadores de confianza, ejecute el siguiente comando en una ventana de Windows PowerShell con permisos elevados (o sea, una ventana de Windows PowerShell que se abre seleccionando **Ejecutar como administrador**):

    ```
    Set-ExecutionPolicy RemoteSigned
    ```

  Esta opción se configura una sola vez en el equipo, y no cada vez que se conecte.

- Para obtener información acerca de los métodos abreviados de teclado que se pueden aplicar a los procedimientos de este tema, consulte [Métodos abreviados de teclado en el Centro de administración de Exchange](https://go.microsoft.com/fwlink/p/?LinkId=534017).

## <a name="connect-to-exchange-online-for-customer-organizations"></a>Conectarse a Exchange Online para organizaciones de cliente

1. En el equipo local, abra Windows PowerShell y ejecute el siguiente comando.
    
    ```
    $UserCredential = Get-Credential
    ```

    En el cuadro de diálogo **Solicitud de credenciales para Windows PowerShell**, escriba su nombre de usuario de administrador DAP y contraseña y, a continuación, haga clic en **Aceptar**.
    
2. Reemplace _\<customer tenant domain name\>_ por el nombre del dominio del inquilino al que desea conectarse y ejecute el siguiente comando:
    
    ```
    $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid?DelegatedOrg=<customer tenant domain name> -Credential $UserCredential -Authentication Basic -AllowRedirection
    ```

    El paso clave de este comando es especificar a qué cliente tiene acceso para obtener información sobre los informes. Esto se hace en el parámetro _ConnectionURI_ , donde se proporciona el FQDN del nombre de dominio inicial como valor de `?DelegatedOrg=` . Este valor indica el punto de conexión de PowerShell de Exchange Online correcto al que se va a conectar. PowerShell remoto debe conectarse a los informes de Microsoft 365 en el contexto de un cliente específico cada vez que se ejecuta un informe. Después de conectarse a Exchange Online PowerShell, todos los comandos siguientes se ejecutan en el contexto del cliente, lo que le proporciona acceso a todos los informes disponibles para el cliente.
    
3. Ejecute el comando siguiente.
    
    ```
    Import-PSSession $Session
    ```

> [!NOTE]
> There's a limit of three simultaneous sessions that can run under one account. Be sure to disconnect the remote PowerShell session when you're finished. If you close the Windows PowerShell window without disconnecting the session, you can use up all the remote PowerShell sessions available to you, and you'll need to wait for the sessions to expire. To disconnect the remote PowerShell session, run the following command:

```
Remove-PSSession $Session
```
  
## <a name="how-do-you-know-this-worked"></a>¿Cómo saber si el proceso se ha completado correctamente?

After Step 3, the Exchange Online cmdlets are imported into your local Windows PowerShell session as tracked by a progress bar. If you don't receive any errors, you connected successfully. A quick test is to run an Exchange Online cmdlet (for example, **Get-Mailbox**) and see the results.
  
Si surgen errores, compruebe los siguientes requisitos:
  
- A common problem is an incorrect password. Run the three steps again and pay close attention to the user name and password you enter in Step 1.
    
- The account you use to connect to Exchange Online must be enabled for remote PowerShell. For more information, see [Enable or disable access to Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534018).
    
- TCP port 80 traffic needs to be open between your local computer and Exchange Online. It's probably open, but it's something to consider if your organization has a restrictive Internet access policy.
    
## <a name="call-the-cmdlet-directly-with-invoke-command"></a>Llamar directamente al cmdlet con Invoke-Command

Importing a remote PowerShell session (Step 3) can be a lengthy process because it brings in _all_ Exchange Online cmdlets. This can be an issue in batch processing (for example, when you're running reports or making bulk changes for different tenants). As an alternative to using **Import-PSSession**, you can call cmdlets you want to use directly with **Invoke-Command**. For example, to call the **Get-Milbox** cmdlet, substitute this syntax for the `Import-PSSession $Session` command in Step 3:
  
```
Invoke-Command -Session $Session -ScriptBlock {Get-Mailbox}
```

## <a name="more-reporting-cmdlets"></a>Más cmdlets de informes

The cmdlets that you used in this topic are Windows PowerShell cmdlets. For more information about these cmdlets, see the following topics:
  
- [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618)
    
- [New-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389621)
    
- [Import-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389619)
    
- [Remove-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389620)
    
- [Set-ExecutionPolicy](https://go.microsoft.com/fwlink/p/?LinkId=389623)
    

