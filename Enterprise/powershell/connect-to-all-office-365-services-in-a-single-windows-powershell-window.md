---
title: "Conectarse a todos los servicios de Office 365 en una sola ventana de Windows PowerShell"
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
- Ent_Office_Other
- O365ITProTrain
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: 'Resumen: Conectar Windows PowerShell con todos los servicios de Office 365 en una sola ventana de Windows PowerShell.'
ms.openlocfilehash: 5f97924d141afa4319c761fee86b13cb2b0705fb
ms.sourcegitcommit: f10e47df0dca4a241659f33061db5217ebc3401e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2018
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a>Conectarse a todos los servicios de Office 365 en una sola ventana de Windows PowerShell

 **Resumen:** En lugar de administrar diferentes servicios de Office 365 en distintas ventanas de la consola de PowerShell, puede conectarse a todos los servicios de Office 365 y gestionarlos desde la ventana de consola única.
  
Al usar PowerShell para administrar Office 365, es posible tener hasta cinco sesiones diferentes de Windows PowerShell abierto al mismo tiempo correspondiente al centro de administración de Office 365, SharePoint Online, Exchange Online, Skype para los negocios en línea y la seguridad &amp;Centro de cumplimiento. Con cinco métodos de conexión diferentes en las sesiones de Windows PowerShell independientes, el escritorio tendría la apariencia siguiente:
  
![Cinco consolas de Windows PowerShell en ejecución al mismo tiempo](images/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
Esto no es óptimo para la administración de Office 365 porque no pueden intercambiar datos entre esos cinco ventanas de administración de servicio de la cruz. Este tema describe cómo utilizar una única instancia de Windows PowerShell desde el que puede administrar la seguridad, Skype para los negocios en línea, Exchange Online, SharePoint Online y Office 365 &amp; centro de cumplimiento.
  
## <a name="before-you-begin"></a>Antes de empezar
<a name="BeforeYouBegin"> </a>

Para poder administrar todo Office 365 desde una sola instancia de Windows PowerShell, tenga en cuenta los siguientes requisitos previos:
  
- El Office 365 trabajo o escuela cuenta utilizar para estos procedimientos necesidades para ser miembro de una función de administración de Office 365. Para obtener más información, consulte [las funciones de administrador acerca de Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367). Este requisito para Office 365 PowerShell, pero no necesariamente para todos los demás servicios de Office 365.
    
- Puede usar las siguientes versiones de Windows de 64 bits:
    
  - Windows 10
    
  - Windows 8.1 o Windows 8
    
  - Windows Server 2016
    
  - Windows Server 2012 R2 o Windows Server 2012
    
  - Windows 7 Service Pack 1 (SP1)*
    
  - Windows Server 2008 R2 SP1*
    
    * Debe instalar el Microsoft.NET Framework 4.5. _x_ y, a continuación, el Windows Management Framework 3.0 o el marco de trabajo de administración de Windows 4.0. Para obtener más información, vea [instalar el.NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) y [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) o [4.0 de Windows Management Framework](https://go.microsoft.com/fwlink/p/?LinkId=391344).
    
    Debe utilizar una versión de 64 bits de Windows debido a los requisitos para el Skype para el módulo de negocios en línea y uno de los módulos de Office 365.
    
- Debe instalar los módulos necesarios para Office 365, SharePoint Online y Skype para los negocios en línea:
    
  - [Servicio en línea Sign-in Ayudante de Microsoft para profesionales de TI RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152)
    
  - [Windows Azure Active Directory módulo para Windows PowerShell (versión de 64 bits)](https://go.microsoft.com/fwlink/p/?linkid=236297)
    
  - [Shell de administración en línea de SharePoint](https://go.microsoft.com/fwlink/p/?LinkId=255251)
    
  - [Skype para el negocio en línea, módulo de Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  Windows PowerShell debe configurarse para ejecutar secuencias de comandos firmadas de Skype para los negocios en línea, Exchange Online y la seguridad &amp; centro de cumplimiento. Para ello, ejecute el siguiente comando en una sesión de Windows PowerShell con privilegios elevados (una ventana de Windows PowerShell que abra seleccionando **Ejecutar como administrador**).
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="the-short-version-instructions-without-explanations"></a>Versión corta (instrucciones sin explicaciones)
<a name="ShortVersion"> </a>

Esta sección presenta los pasos de conexión sin explicaciones detalladas. Si tiene preguntas o desea obtener más información, puede leer el resto del tema. Los números de estos pasos coinciden con los números de las secciones del resto del tema:
  
1. Abrir Windows PowerShell como administrador (uso de **Ejecutar como administrador**).
    
2. Ejecute este comando y especifique su trabajo en Office 365 o credenciales de la cuenta de la escuela.
    
  ```
  $credential = Get-Credential
  ```

3. Ejecutar estos comandos para conectarse a Office 365.
    
  ```
  Import-Module MsOnline
  Connect-MsolService -Credential $credential
  ```

4. Ejecutar estos comandos para conectarse a SharePoint Online. Reemplazar _ \<domainhost >_ con el valor real de su dominio. Por ejemplo, para `litwareinc.onmicrosoft.com`, el _ \<domainhost >_ valor es `litwareinc`.
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. Ejecutar estos comandos para conectar con Skype para los negocios en línea. Una advertencia acerca de cómo aumentar el `WSMan NetworkDelayms` valor se espera la primera vez que se conecta y se debe omitir.
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. Ejecutar estos comandos para conectarse a Exchange Online.
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession -DisableNameChecking
  ```

7. Ejecutar estos comandos para conectarse a la seguridad &amp; centro de cumplimiento.
    
  ```
  $ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
  Import-PSSession $ccSession -Prefix cc
  ```
> [!NOTE]
> El prefijo de texto "cc" se agrega a *todos los* seguridad &amp; centro de cumplimiento de los nombres de cmdlet para poder ejecutar los cmdlets que existe en Exchange Online y la seguridad &amp; centro de cumplimiento en la misma sesión de Windows PowerShell. Por ejemplo, **Get-RoleGroup** pasa a ser **Get-ccRoleGroup** en la seguridad &amp; centro de cumplimiento.
  
Aquí están todos los comandos en un único bloque. Especificar el nombre del host de dominio y, a continuación, ejecutarlos todos al mismo tiempo.
  
```
$domainHost="<domain host name, such as litware for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Import-Module MsOnline
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession -DisableNameChecking
$ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
Import-PSSession $ccSession -Prefix cc
```

Cuando esté listo para cerrar la ventana de Windows PowerShell, ejecute este comando para eliminar las sesiones activas en Skype para los negocios en línea, Exchange Online, SharePoint Online y la seguridad &amp; centro de cumplimiento de normas:
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $ccSession ; Disconnect-SPOService
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a>Versión larga (instrucciones con explicaciones detalladas)
<a name="LongVersion"> </a>

### <a name="step-1-open-windows-powershell-as-an-administrator"></a>Paso 1: Abrir Windows PowerShell como administrador
<a name="Step1"> </a>

Si está ejecutando Windows 10, Windows 8, Windows 8.1, 2016 de Windows Server, Windows Server 2012 R2 o Windows Server R2 de 2012, hacer esto:
  
1. Utilice cualquiera de estos métodos para buscar el método abreviado de **Windows PowerShell**:
    
  - En la pantalla de inicio, haga clic en un área vacía y escriba Windows PowerShell.
    
  - En el escritorio o la pantalla de inicio, presione el Windows teclas CTRL+q. En el encanto de búsqueda, escriba Windows PowerShell.
    
  - En el escritorio o la pantalla de inicio, mueva el cursor a la esquina superior derecha, o Deslizar hacia la izquierda desde el borde derecho de la pantalla para mostrar los encantos. Seleccione los bueno de búsqueda y escriba Windows PowerShell.
    
2. En los resultados, haga clic en **Windows PowerShell**y seleccione **Ejecutar como administrador**.
    
3. Si aparece el cuadro de diálogo **Control de cuentas de usuario** , seleccione **Sí** para comprobar que desea ejecutar Windows PowerShell con credenciales de administrador.
    
Si está ejecutando el SP1 de Windows 7 (o Windows Server 2008 R2 SP1), puede hacer esto:
  
1. En el menú **Inicio** , seleccione **Todos los programas** > **Accesorios** > **De Windows PowerShell**. Haga clic derecho en **Windows PowerShell**y, a continuación, seleccione **Ejecutar como administrador**.
    
2. Si aparece el cuadro de diálogo **Control de cuentas de usuario** , seleccione **Sí** para comprobar que desea ejecutar Windows PowerShell con credenciales de administrador.
    
Debe ejecutar Windows PowerShell como administrador. Si no lo hace, va a obtener un mensaje de error similar al siguiente cuando intenta importar uno de los módulos necesarios.
  
```
The specified module 'Microsoft.Online.SharePoint.Online.PowerShell' was not loaded because no valid module file was found in any directory.
```

Es la única manera de remediar la situación cerrar Windows PowerShell y reiniciarlo como administrador. Aquí es una forma rápida y sencilla de saber si está ejecutando Windows PowerShell como administrador: es el símbolo del sistema `PS C:\Windows\System32>`, no `PS C:\Users\YourUserName>`.

  
### <a name="step-2-create-a-windows-powershell-credentials-object"></a>Paso 2: Crear un objeto de credenciales de Windows PowerShell
<a name="Step2"> </a>

El objeto de credenciales proporciona una forma cifrada para pasar su nombre de usuario y contraseña a Windows PowerShell. Para crear un objeto de credenciales, ejecute el siguiente comando en Windows PowerShell.
  
```
$credential = Get-Credential
```

> [!NOTE]
>  `$credential`es una variable que almacenará el objeto de credenciales. No es necesario el nombre de la variable `$credential`, pero al hacerlo así resultará más sencillo recordar que la variable contiene el objeto de credenciales. (Y que es importante, ya que podrá utilizar esta variable varias veces). Que también resultará más fácil para seguir los ejemplos, ya que siempre se utilizará este artículo `$credential` para representar el objeto de credenciales.
  
Windows PowerShell se mostrará un cuadro de diálogo que tiene este aspecto.
  
![Cuadro de diálogo de solicitud de credenciales en blanco.](images/o365_powershell_empty_credentials_box.png)
  
Escriba el trabajo o la escuela de nombre de usuario en el cuadro **nombre de usuario** , utilizando el formato _username@domainname_ (por ejemplo, kenmyer@litwareinc.onmicrosoft.com); Escriba la contraseña en el cuadro **contraseña** ; y, a continuación, haga clic en **Aceptar**:
  
![Cuadro de diálogo de solicitud de credenciales completadas](images/o365_powershell_completed_credentials_box.png)
  
Tenga en cuenta que, como suele ser el caso, no verá a ningún tipo de confirmación que se creó el objeto de credenciales. (Windows PowerShell normalmente indica cuando cosas ir mal, pero no siempre sabrá cuando las cosas van derecho.) Si desea comprobar que se creó el objeto de credenciales, escriba lo siguiente en Windows PowerShell y, a continuación, presione ENTRAR.
  
```
$credential
```

Luego debería ver algo parecido a esto en la pantalla.
  
```
UserName                               Password
--------                               --------
kenmyer@litwareinc.onmicrosoft.com     System.Security.SecureString
```

Una cosa a tener en cuenta aquí es que el cmdlet [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618) sólo crea el objeto de credenciales; no autentica ni lo contrario Compruebe que el nombre de usuario y la contraseña son correctos. Por ejemplo, supongamos que ha escrito incorrectamente el nombre de usuario como kenmyer@litwareinc.onmicrosoft.com. Si lo hace, **Get-Credential** creará un objeto de credenciales con ese nombre de usuario y sin comprobar para ver si ese es realmente un nombre de usuario válido. No sabrá si ha creado un objeto de credenciales válidas realmente hasta que realmente utiliza dicho objeto para intentar conectarse a los servicios de Office 365.
  
### <a name="step-3-connect-to-office-365"></a>Paso 3: Conexión a Office 365
<a name="Step3"> </a>

Comenzaremos por conectarse a Office 365 propio. 
  
Lo primero que necesitamos hacer aquí es importar el módulo de Office 365 (el Microsoft Azure Active Directory módulo para Windows PowerShell). Para ello, ejecute este comando en Windows PowerShell.
  
```
Import-Module MsOnline
```

Si quiere comprobar si el módulo se importó, ejecute este comando.
  
```
Get-Module
```

En algún lugar de la lista de módulos que son devueltas por este comando debería ver algo similar a esto: `Manifest 1.0 MSOnline {Add-MsolForeignGroupToRole, Add-MsolG...}`.
  
Si ve `MSOnline` en la lista, eso significa que todo haya salido según el plan.
  
Con el objeto de credenciales creado (consulte [paso 2: crear un objeto de credenciales de Windows PowerShell](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step2)) y con el `MsOnline` módulo cargado, podemos conectarnos ahora a Office 365 mediante el cmdlet [Connect-MsolService](https://go.microsoft.com/fwlink/p/?LinkId=532375) y el siguiente comando.
  
```
Connect-MsolService -Credential $credential
```

Observe que todo lo que tienen que proporcionar es el objeto de credenciales ( `$credential`). En función de las credenciales, Office 365 se conectará automáticamente el dominio correcto. No es necesario especificar el nombre del dominio al ejecutar **MsolService de conectar**.
  
Para comprobar que realmente *está* conectado a Office 365, ejecute este comando.
  
```
Get-MsolDomain
```

A cambio, debería obtener algo similar a esto:
  
```
Name                         Status          Authentication
----                         ------          --------------
litwareinc.onmicrosoft.com   Verified        Managed
```

### <a name="step-4-connect-to-sharepoint-online"></a>Paso 4: Conectarse a SharePoint Online
<a name="Step4"> </a>

Importar el módulo de SharePoint Online con el siguiente comando:
  
```
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
```

El modificador _DisableNameChecking_ suprime esta advertencia.
  
```
WARNING: The names of some imported commands from the module 'Microsoft.Online.SharePoint.PowerShell' include unapproved verbs that might make them less discoverable. To find the commands with unapproved verbs, run the Import-Module command again with the Verbose parameter. For a list of approved verbs, type Get-Verb.
```

Para conectar con SharePoint Online, deberá suministrar dos fragmentos de información: las credenciales y la URL de su sitio de administración de SharePoint Online. La parte de credenciales es fácil: ya nos hemos almacenado en la variable `$credential` (consulte [paso 2: crear un objeto de credenciales de Windows PowerShell](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step2)). En cuanto a la dirección URL de su sitio de administración, que es bastante fácil de determinar, también. Supongamos que es el nombre de dominio de Office 365 `litwareinc.onmicrosoft.com`.
  
Para determinar la dirección URL del sitio de administración, realice lo siguiente:
  
1. Iniciar con el prefijo `https://`.
    
2. Agregar la parte del host de dominio del nombre de dominio. Por ejemplo, para `litwareinc.onmicrosoft.com`, el nombre de host de dominio es `litwareinc`. Para `contoso.onmicrosoft.com`, el nombre de host de dominio es `contoso`.
    
3. Agregar un guión (-) seguido de `admin.sharepoint.com`.
    
En otras palabras:
  
 `https://` + `litwareinc` + `-admin.sharepoint.com` = `https://litwareinc-admin.sharepoint.com`
  
Una vez construido el URL, puede utilizar esa dirección URL y el objeto de credenciales para conectarse a SharePoint Online. Llamar al cmdlet [Connect-SPOService](https://go.microsoft.com/fwlink/p/?LinkId=532436) , con un comando similar a éste.
  
```
Connect-SPOService -Url https://litwareinc-admin.sharepoint.com -credential $credential
```

Para comprobar que se ha realizado la conexión, ejecute el siguiente comando en Windows PowerShell.
  
```
Get-SPOSite
```

Debe obtener una lista de todos los sitios de SharePoint Online. Éste es un ejemplo:
  
```
Url                                       Owner          Storage Quota
---                                       -----          -------------
http://litwareinc-public.sharepoint.com/                 1000
https://litwareinc.sharepoint.com/                       1000
https://litwareinc.sharepoint.com/search                 1000
```

Los comandos de Office 365 (los que se describen en [paso 3: conectarse a Office 365](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step3)) le siguen funcionando. (Intente ejecutar **Get-MsolUser**y véalo por sí mismo). Esto significa que ahora puede administrar Office 365 y SharePoint Online desde la misma instancia de Windows PowerShell.
  
### <a name="step-5-connect-to-skype-for-business-online"></a>Paso 5: Conectarse a Skype Empresarial Online
<a name="Step5"> </a>

Conectar con Skype para los negocios en línea (y Exchange Online o la seguridad &amp; centro de cumplimiento) es diferente de la conexión a Office 365 y SharePoint Online. Eso es porque el Skype para los cmdlets de Exchange Online y negocios en línea no se instaló en el equipo, como ocurre con el Office 365 y los cmdlets de SharePoint Online. En su lugar, cada vez que inicies sesión, los cmdlets adecuados se copian temporalmente en el equipo. Cuando aprueban, los cmdlets se quitan del equipo.
  
Para conectar con Skype para los negocios en línea, debe importar el Skype para el módulo de negocios en línea. Para ello, ejecute este comando.
  
```
Import-Module SkypeOnlineConnector
```

La primera vez que lo haga, verá el siguiente mensaje de advertencia, que se puede pasar por alto.
  
```
WARNING: WSMan NetworkDelayms has been set to 30000 milliseconds. The previous value was 5000 milliseconds.
WARNING: To improve the performance of the Lync Online Connector, it is recommended that the network delay be set to
30000 milliseconds (30 seconds). However, you can use Set-WinRMNetworkDelayMS to change the network delay to any
integer value.
```

Tras importar el módulo, ejecute este comando.
  
```
$sfboSession = New-CsOnlineSession -Credential $credential
```

Hemos creado una sesión remota de PowerShell. En este caso, eso significa que nos hemos conectado a una instancia de Windows PowerShell se ejecuta en uno de los servidores de Office 365. 
  
Aunque hemos hecho una conexión a Office 365, nosotros no hemos descargado las secuencias de comandos, cmdlets y otros elementos necesarios para administrar Skype para los negocios en línea. Para ello, se debe ejecutar este comando.
  
```
Import-PSSession $sfboSession
```

Cuando se importa a la sesión de Windows PowerShell, verá una barra de progreso similar a la siguiente, una barra de progreso que informa sobre todos lo Skype para los negocios en línea cmdlets que se importa a su equipo.
  
![Barra de progreso de Lync Online.](images/o365_powershell_lync_progress_bar.png)
  
Cuando la barra de progreso desaparezca, debería obtener un resultado similar al siguiente:
  
```
ModuleType Version    Name               ExportedCommands
---------- -------    ----               ----------------
Script     1.0        tmp_swc5mp4v.1ck  {Copy-CsVoicePolicy, Disabl...
```

### <a name="step-6-connect-to-exchange-online"></a>Paso 6: Conectarse a Exchange Online
<a name="Step6"> </a>

Ejecutar este comando, que se crea una sesión remota de Windows PowerShell con Exchange Online.
  
```
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
```

> [!NOTE]
> ¿Por qué es el comando para conectarse a Exchange Online más complicado que el comando para conectar con Skype para los negocios en línea? Técnicamente, no es: ambos comandos hacen exactamente lo mismo. Sin embargo, el Skype para los negocios en línea equipo crea su propio cmdlet: **New-CsOnlineSession** , que oculta algunos de los parámetros (como _la autenticación_ y _AllowRedirection_) que se utilizan al conectarse a Exchange Online. En lugar de tener que escribir esa información manualmente, los parámetros de _autenticación_ y _AllowRedirection_ se desarrollan con eficacia para el cmdlet **New-CsOnlineSession** . Tendrá que escribir esos parámetros al conectarse a Exchange Online porque Exchange Online utiliza el cmdlet [New-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389621) estándar para conectarse a Office 365. La desventaja es que tiene que escribir algo más para ello. La ventaja es que no tienes que descargar e instalar un módulo Exchange Online.
  
Ahora todo lo que tiene que hacer es importar esta sesión remota, como hicimos con Skype para los negocios en línea.
  
```
Import-PSSession $exchangeSession -DisableNameChecking
```

Debería ver algo parecido a esto en la pantalla.
  
```
ModuleType Version  Name             ExportedCommands
---------- -------  ----             ----------------
Script     1.0      tmp_nweiqjvl.geu {Add-AvailabilityAddressSpace...
```

Ahora, intente ejecutar este comando:
  
```
Get-AcceptedDomain
```

Como resultado, verá información acerca de los dominios de Office 365 configurados para direcciones de correo electrónico de Exchange en línea.
  
```
Name            DomainName          DomainType      Default
----            ----------          ----------      -------
litwareinc.com  litwareinc.com      Authoritative   True
```

### <a name="step-7-connect-to-the-security-amp-compliance-center"></a>Paso 7: Conectar a la seguridad &amp; centro de cumplimiento
<a name="Step7"> </a>

La seguridad &amp; centro de cumplimiento es un servicio de Office 365 que le permite administrar características de cumplimiento desde una ubicación. Para obtener más información, consulte el [Centro de cumplimiento de normas de Office 365](http://technet.microsoft.com/library/fde83656-f136-448d-b250-6fa17b503e4e.aspx).
  
Las instrucciones de conexión para la seguridad &amp; centro de cumplimiento son muy similares a las de Exchange Online, pero con mayor complicación, que verá en el momento.
  
Ejecutar este comando, que se crea una sesión remota de PowerShell con la seguridad &amp; centro de cumplimiento.
  
```
$ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
```

Ahora ejecute este comando:
  
```
Import-PSSession $ccSession -Prefix cc
```

De nuevo, este comando es muy similar al comando para Exchange Online. El conmutador de _DisableNameChecking_ no es necesario porque no hay ningún verbo no aprobada en la seguridad &amp; centro de cumplimiento. Pero ¿qué pasa con ese adicionales `-Prefix cc` parámetro y valor? Que es la mayor complicación que dijimos acerca de.
  
Exchange Online y la seguridad &amp; centro de cumplimiento compartir algunos cmdlets que tienen exactamente los mismos nombres y proporcionan la misma funcionalidad. **Get-RoleGroup** es un ejemplo.
  
Así que, ¿qué sucede si se intenta importar dos sesiones que contengan cmdlets con el mismo nombre? Colisionen. Obtendrá un mensaje de advertencia amarillo grande que dice `WARNING: Proxy creation has been skipped for the following command:` seguido por la lista de cmdlets en conflicto que no se pudo importar. ¿El resultado final? Puede ejecutar **Get-RoleGroup** en Exchange Online debido a que hay conectado en primer lugar, pero no puede ejecutar **Get-RoleGroup** en la seguridad &amp; centro de cumplimiento debido a que hay conectado última y los cmdlets en conflicto se negaron a importar.
  
La forma más sencilla de resolver este problema es agregar un prefijo de texto arbitrario a la seguridad importado &amp; cmdlets de centro de cumplimiento. Lo hicimos usando el _prefijo de_ parámetro con el valor "cc" en el cmdlet **Import-PSSession** . ¿Qué hizo para nosotros? Eliminan los conflictos cambiando (ligeramente) la seguridad &amp; nombres de cmdlet de centro de cumplimiento para esta sesión. Toda la seguridad importada &amp; centro de cumplimiento cmdlets ahora comenzar con "cc" en la parte del sustantivo del nombre del cmdlet (a la derecha de la "-"). Por ejemplo, el cmdlet **Get-RoleGroup** contencioso se convierte en **Get-ccRoleGroup** para la seguridad &amp; centro de cumplimiento de normas para que no entre en conflicto con **Get RoleGroup** para Exchange Online.
  
¿El inconveniente?  *Todos los*  Seguridad &amp; nombres de cmdlet de centro de cumplimiento reciben el prefijo "cc" — incluso cmdlets únicos que no lo necesitan. Por ejemplo, **Get-ComplianceSearch** se convierte en **Get-ccComplianceSearch** aunque hay un tal cmdlet de Exchange en línea. Al considerar los beneficios de la administración de todos los servicios de Office 365 en una única sesión de Windows PowerShell es un poco de una molestia, pero no está tan mal. Recuerde agregar "cc" a los nombres de cmdlet para todos los procedimientos en la seguridad &amp; centro de cumplimiento.
  
Si todo va bien, verá algo parecido a esto:
  
```
ModuleType Version  Name             ExportedCommands
---------- -------  ----             ----------------
Script     1.0      tmp_xbbx5exr.ehm {Add-ccRoleGroupMember, Get-ccAdminAuditLogConfig, Get-ccA...
```

Ahora está libre para administrar todos los servicios de Office 365 en una única sesión de Windows PowerShell.
  
### <a name="step-8-gracefully-end-your-powershell-sessions"></a>Paso 8: Finalizar la sesiones de PowerShell
<a name="Step8"> </a>

Si sólo cierra la ventana de Windows PowerShell, su Skype para conexión remota en línea Business permanecerá activa durante los próximos 15 minutos o menos. Porque Skype para los negocios en línea limita el número de conexiones simultáneas que cualquier persona o cualquier un dominio puede tener abiertos, que podría ser un problema. Con Skype para los negocios en línea, puede tener un administrador individual, a lo sumo, tres conexiones abiertas al mismo tiempo, y un dominio puede tener un máximo de nueve conexiones abiertas. Si inicia sesión Skype para los negocios en línea y luego salga sin cerrar correctamente la sesión, esa sesión permanece abierta durante los próximos 15 minutos o menos. Como resultado, es una conexión menos disponible a usted o a otros administradores en el dominio.
  
En su lugar, vamos a cerrar las sesiones remotas Skype para los negocios en línea, Exchange Online y la seguridad &amp; cumplimiento centrar correctamente. Antes de hacerlo, ejecute este comando.
  
```
Get-PSSession
```

El cmdlet [Get-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=532437) debe mostrar que tiene abierto al menos tres sesiones remotas, uno para Skype para los negocios en línea, uno para Exchange Online y otro para la seguridad &amp; centro de cumplimiento de normas (es posible que podría tener más de tres remoto sesiones que se ejecutan, dependiendo de si ya ha utilizado esta instancia de Windows PowerShell para conectarse a otra cosa aparte de los servicios de Office 365). Debería ver algo parecido a lo siguiente.
  
```
Id Name     ComputerName     State   ConfigurationName    Availability
-- ----     ------------     -----   -----------------    ------------
 1 Session1 webdir0a.onl...  Opened  Microsoft.PowerShell    Available
 2 Session2 outlook.offi...  Opened  Microsoft.Exchange      Available
 3 Session3 ps.complianc...  Opened  Microsoft.Exchange      Available
```

Para cerrar estos tres sesiones, ejecutar estos comandos uno por uno. El primer comando cierra el Skype para la sesión de negocios en línea, la segunda cierra la sesión de Exchange Online, y el tercero cierra la seguridad &amp; sesión de centro de cumplimiento.
  
```
Remove-PSSession $sfboSession
Remove-PSSession $exchangeSession
Remove-PSSession $ccSession
```

Si ahora ejecuta el cmdlet **Get-PSSession** , debería ver nada en absoluto (a menos que tenga otras sesiones remotas de funcionamiento).
  
![Consola de Windows PowerShell sin sesiones remotas](images/o365_powershell_no_remote_sessions.png)
  
> [!NOTE]
> Si prefiere cerrar todas las sesiones remotas al mismo tiempo, puede utilizar este comando: >`Get-PSSession | Remove-PSSession`
  
Si ahora intenta ejecutar un cmdlet desde cualquiera de estas cerrado las sesiones (por ejemplo, **Get-CsMeetingConfiguration** en Skype para los negocios en línea) obtendrá un mensaje de error similar a éste.
  
```
Get-CsMeetingConfiguration : The term 'Get-CsMeetingConfiguration' is not recognized as the name of a cmdlet, function, script file, or operable program. Check the spelling of the name, or if a path was included, verify that the path is correct and try again.
```

Obtenemos el mensaje de error porque los cmdlets de Skype para los negocios en línea, Exchange Online y la seguridad &amp; centro de cumplimiento se eliminaron cuando se cierra las sesiones remotas.
  
Para cerrar la sesión en SharePoint Online, escriba este comando.
  
```
Disconnect-SPOService
```

Si intenta ejecutar el cmdlet **Get-SPOSite** , obtendrá un mensaje de error como éste.
  
```
get-sposite : No connection available. Use Connect-SPOService before running this CmdLet.
```

No se puede recuperar la información del sitio porque ya no está conectado a SharePoint Online.
  
En cuanto a su conexión a Office 365, aunque no hay un cmdlet **Connect-MsolService** , hay un cmdlet de **Desconexión MsolService** correspondiente. Así que para Office 365, simplemente cierre la ventana de Windows PowerShell. No obstante, sigue siendo una buena idea hacer esto último para que pueda correctamente desconectar de SharePoint Online, Skype para los negocios en línea, Exchange Online y la seguridad &amp; centro de cumplimiento.
  
## <a name="new-to-office-365"></a>¿Es la primera vez que usa Office 365?
<a name="LongVersion"> </a>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>Consulte también

#### 

[Administrar Office 365 con PowerShell de Office 365](manage-office-365-with-office-365-powershell.md)
  
[Introducción a PowerShell de Office 365](getting-started-with-office-365-powershell.md)
  
[Administrar SharePoint Online con PowerShell de Office 365](manage-sharepoint-online-with-office-365-powershell.md)
  
[Administrar licencias y cuentas de usuario con PowerShell de Office 365](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Usar Windows PowerShell para crear informes en Office 365](use-windows-powershell-to-create-reports-in-office-365.md)

