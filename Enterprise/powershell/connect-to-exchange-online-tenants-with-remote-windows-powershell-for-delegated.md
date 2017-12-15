---
title: Conectarse a los inquilinos de Exchange Online con el modo remoto de Windows PowerShell para asociados con permiso de acceso delegado (DAP)
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: DecEntMigration
ms.assetid: ae5f1a87-8b77-4f93-a1b8-56f800aeb283
description: "Resumen: Use el modo remoto de Windows PowerShell para conectarse a Exchange Online con el parámetro DelegatedOrg."
ms.openlocfilehash: 9bb6a5a316f4bc23c6586da825b8755cf755f484
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2017
---
# <a name="connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated-access-permissions-dap-partners"></a>Conectarse a los inquilinos de Exchange Online con el modo remoto de Windows PowerShell para asociados con permiso de acceso delegado (DAP)

 **Resumen:** Uso remoto de Windows PowerShell para conectarse a Exchange Online mediante el parámetro _DelegatedOrg_ .
  
El modo remoto de Windows PowerShell permite administrar la configuración de Exchange Online desde la línea de comandos. Use Windows PowerShell en el equipo local para crear una sesión remota a Exchange Online. Es un proceso de tres pasos en el que se especifican las credenciales de Exchange Online, se proporciona la configuración de conexión requerida y se importan los cmdlets de Exchange Online a la sesión local de Windows PowerShell para poder usarlos.
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>¿Qué necesita saber antes de comenzar?

- Tiempo estimado para finalizar: 5 minutos
    
- Puede usar las siguientes versiones de Windows:
    
  - Windows 10
    
  - Windows 8.1 o Windows 8
    
  - Windows Server 2012 R2 o Windows Server 2012
    
  - Windows 7 Service Pack 1 (SP1)*
    
  - Windows Server 2008 R2 SP1*
    
    * Es necesario instalar .NET Framework 4.5.1 o .NET Framework 4.5 y, después, Windows Management Framework 4.0 o Windows Management Framework 3.0 . Para más información, consulte los siguientes recursos:
    
  - [Instalar .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868)
    
  - [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) o[Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)
    
- Para obtener información acerca de los métodos abreviados de teclado que se pueden aplicar a los procedimientos de este tema, consulte [Métodos abreviados de teclado en el Centro de administración de Exchange](https://go.microsoft.com/fwlink/p/?LinkId=534017).
    
## 

> [!IMPORTANT]
> Este procedimiento es solo paraasociados con permiso de acceso delegado (DAP). Si no es socio DAP, no use este procedimiento. 
  
Los asociados con DAP son asociados de proveedor de soluciones en la nube (CSP) y redifusión web. Generalmente son proveedores de red o de telecomunicaciones para otras compañías. Empaquetan suscripciones en sus ofertas de servicio a sus clientes. Poseen un arrendamiento de asociado al que se le conceden automáticamente permisos Administrar en nombre de (AOBO) para susarrendamientos de cliente de Office 365, de modo que pueden administrar todos sus arrendamientos de cliente e informar al respecto.
  
## <a name="connect-to-exchange-online"></a>Conectarse a Exchange Online

1. En el equipo local, abra Windows PowerShell y ejecute el siguiente comando.
    
  ```
  $UserCredential = Get-Credential
  ```

    En el cuadro de diálogo **Solicitud de credenciales para Windows PowerShell**, escriba su nombre de usuario de administrador DAP y contraseña y, a continuación, haga clic en **Acepta**.
    
2. Ejecute el siguiente comando, reemplace el  _<customer tenant domain name>_ por el nombre de dominio del inquilino al que desee conectarse.
    
  ```
  $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid?DelegatedOrg=<customer tenant domain name>-Credential $UserCredential -Authentication Basic -AllowRedirection
  ```

    El paso clave en este comando es especificar a qué cliente hay que acceder para obtener la información de supervisión. Esto se realiza en el parámetro  _ConnectionURI_, donde se proporciona el FQDN del nombre de dominio inicial como el valor para el parámetro _DelegatedOrg_. Esto indica al modo remoto de Windows PowerShell para Exchange Online para Windows PowerShell debe conectarse a los informes de Office 365 en el contexto de un cliente específico cada vez que un informe se ejecuta. Después de especificar el cliente, todos los comandos siguientes se ejecutan en el contexto de dicho cliente. Esto permite a los asociados acceder a todos los informes disponibles para este cliente.
    
3. Ejecute el comando siguiente.
    
  ```
  Import-PSSession $Session
  ```

> [!NOTE]
> Hay un límite de tres sesiones simultáneas que se pueden ejecutar en una cuenta. Asegúrese de desconectarse de la sesión remota de Windows PowerShell cuando haya finalizado. Si cierra la ventana de Windows PowerShell sin desconectar la sesión, podría agotar todas las sesiones de Windows PowerShell remotas que tenga disponibles y deberá esperar a que las sesiones expiren. Ejecute el siguiente comando para desconectar la sesión remota de Windows PowerShell. >  `Remove-PSSession $Session`
  
## <a name="how-do-you-know-this-worked"></a>¿Cómo saber si el proceso se ha completado correctamente?

Después del paso 3, los cmdlets de Exchange Online se importan a la sesión local de Windows PowerShell, como se indica en una barra de progreso. Si no aparece ningún error, la conexión se habrá establecido correctamente. Una prueba rápida es ejecutar un cmdlet de Exchange Online(por ejemplo, **Get-Mailbox** ) y ver los resultados.
  
Si surgen errores, compruebe los siguientes requisitos:
  
- Un problema habitual es una contraseña incorrecta. Vuelva a realizar los tres pasos y preste especial atención al nombre de usuario y contraseña que escriba en el paso 1.
    
- Para evitar que se produzcan ataques por denegación de servicio (DoS), solo se pueden tener abiertas tres conexiones remotas de Windows PowerShell a la organización de Exchange Online.
    
- Windows PowerShell debe estar configurado para ejecutar scripts. Esta opción se configura una sola vez en el equipo, y no cada vez que se conecte. Para permitir que Windows PowerShell ejecute scripts firmados, ejecute el siguiente comando en una ventana de Windows PowerShell elevada (una ventana de Windows PowerShell que abrió cuando seleccionó **Ejecutar como administrador**).
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

- La cuenta que use para conectarse a Exchange Online debe estar habilitada para Windows PowerShell remoto. Para más información consulte [Administrar el acceso a PowerShell remoto en Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534018).
    
- Debe abrir el tráfico del puerto TCP 80 entre su equipo local y Exchange Online. Probablemente esté abierta, pero es un aspecto que se debe tener en cuenta si la directiva de acceso a Internet de su organización es restrictiva.
    
## <a name="call-the-cmdlet-directly-with-invoke-command"></a>Llamar directamente al cmdlet con Invoke-Command

Importar una sesión remota de Windows PowerShell puede ser un proceso largo, ya que incorpora todos los cmdlets de Exchange Online. Esto puede ser un problema para el procesamiento por lotes, por ejemplo, cuando se ejecutan informes o se realizan cambios masivos para diferentes inquilinos. Como alternativa al uso de **Import-PSSession**, puede llamar a los cmdlets que desea usar directamente con **Invoke-Command**. Por ejemplo, para llamar al cmdlet **get-mailbox**, reemplace esta sintaxis por `Import-PSSession $Session`.
  
```
Invoke-Command -Session $Session -ScriptBlock {Get-Mailbox}
```

## <a name="more-reporting-cmdlets"></a>Más cmdlets de informes

Los cmdlets que se usan en este tema son cmdlets de Windows PowerShell. Para obtener más información sobre estos cmdlets, consulte los siguientes temas:
  
- [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618)
    
- [New-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389621)
    
- [Import-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389619)
    
- [Remove-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389620)
    
- [Set-ExecutionPolicy](https://go.microsoft.com/fwlink/p/?LinkId=389623)
    

