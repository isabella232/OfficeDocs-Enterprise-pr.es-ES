---
title: Por qué necesita usar PowerShell para Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: ''
ms.assetid: b3209b1a-40c7-4ede-8e78-8a88bb2adc8a
description: 'Resumen: comprenda por qué debe usar PowerShell para administrar Microsoft 365, en algunos casos de manera más eficiente y, en otros casos, por necesidad.'
ms.openlocfilehash: ba786acd8b5ad08bad97b11812f0180004e55cb6
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/22/2020
ms.locfileid: "45229866"
---
# <a name="why-you-need-to-use-powershell-for-microsoft-365"></a>Por qué necesita usar PowerShell para Microsoft 365

*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*

Con el centro de administración de 365 de Microsoft, no solo puede administrar las cuentas de usuario y licencias de Microsoft 365, pero también puede administrar los servicios de Microsoft 365 como Exchange Online, Teams y SharePoint Online. Sin embargo, también puede administrar estos elementos con comandos de PowerShell, aprovechando un entorno de línea de comandos y de lenguaje de scripting para la velocidad, la automatización y la capacidad adicional.
  
En este artículo, le mostraremos las formas en que puede usar PowerShell para administrar Microsoft 365:
  
- Revelar información adicional que no puede ver con el centro de administración de 365 de Microsoft
    
- Configurar las características y la configuración solo posible con PowerShell
    
- Realizar operaciones en masa
    
- Filtrar datos
    
- Imprimir o guardar datos
    
- Administrar a través de servicios
    
Antes de empezar, comprenda que PowerShell para Microsoft 365 es un conjunto de módulos para Windows PowerShell, un entorno de línea de comandos para plataformas y servicios basados en Windows. Este entorno crea un lenguaje de Shell de comandos que se puede extender con módulos adicionales y proporciona una forma de ejecutar comandos o scripts sencillos o complejos. Por ejemplo, después de instalar los módulos de PowerShell para Microsoft 365 y conectarse a su suscripción a Microsoft 365, puede ejecutar este comando para enumerar todos los buzones de usuario para Microsoft Exchange Online:
  
```powershell
Get-Mailbox
```

La obtención de la lista de buzones también puede realizarse fácilmente mediante el centro de administración de Microsoft 365, pero no se puede realizar fácilmente el recuento de la cantidad de elementos de todas las listas para todos los sitios de las aplicaciones Web.
  
Tenga en cuenta que PowerShell para Microsoft 365 está diseñado para aumentar y mejorar su capacidad para administrar Microsoft 365, no para reemplazar el centro de administración de Microsoft 365. Como administrador, debe estar al menos familiarizado con el uso de PowerShell para Microsoft 365 porque hay algunos procedimientos de configuración que solo se pueden realizar con PowerShell para los comandos de Microsoft 365. En estos casos, deberá comprender cómo hacer lo siguiente:
  
- Instale los módulos de PowerShell para Microsoft 365 (se realiza una sola vez para cada equipo de administrador).
    
- Conéctese a su suscripción de Microsoft 365 (se realiza una vez por cada sesión de PowerShell).
    
- Recopilar la información necesaria para ejecutar los comandos de PowerShell necesarios para Microsoft 365.
    
- Ejecute correctamente los comandos de PowerShell para Microsoft 365.
    
Después de haber aprendido estos conocimientos básicos, no es necesario hacer una lista de los usuarios de buzones con el comando **Get-Mailbox** ni es necesario que sepa cómo crear un nuevo comando como el anterior para contar todos los elementos de todas las listas de todos los sitios para todas las aplicaciones web. Microsoft y la comunidad de administradores pueden ayudarle con esto según sea necesario.
  
## <a name="powershell-for-microsoft-365-can-reveal-additional-information-that-you-cannot-see-with-the-microsoft-365-admin-center"></a>PowerShell para Microsoft 365 puede revelar información adicional que no puede ver con el centro de administración de Microsoft 365

El centro de administración de 365 de Microsoft muestra una gran cantidad de información útil, pero esto no significa que muestre toda la información posible que Microsoft 365 almacena en los usuarios, las licencias, los buzones de correo y los sitios. A continuación, se muestra un ejemplo de **usuarios y grupos** en el centro de administración de Microsoft 365:
  
![Ejemplo de la presentación de usuarios y grupos en el centro de administración de Microsoft 365.](media/o365-powershell-users-and-groups.png)
  
Para muchos fines, se muestra la información que necesita saber. En cambio, algunas veces necesitará más. Por ejemplo, las licencias de Microsoft 365 (y las características de Microsoft 365 disponibles para un usuario) dependen en parte de la ubicación geográfica del usuario. Las directivas y características que se pueden extender a un usuario que vive en los Estados Unidos tal vez no sean las mismas que las directivas y características que se pueden extender a un usuario que vive en India o en Bélgica. Puede usar el centro de administración de Microsoft 365 para determinar la ubicación geográfica de un usuario con estos pasos:
  
1. Haga doble clic en el **Nombre para mostrar** del usuario.
    
2. En el panel de presentación de las propiedades del usuario, haga clic en **Detalles**.
    
3. En la pantalla de detalles, haga clic en **Detalles adicionales**.
    
4. Desplácese hacia abajo hasta que vea el encabezado **País o región**:
    
     ![Ejemplo de la información de región de un usuario en el centro de administración de Microsoft 365.](media/o365-powershell-usage-location.png)
  
5. Escriba el nombre para mostrar y la ubicación del usuario en una hoja de papel, o cópielo y péguelo en el Bloc de notas. 
    
Debe repetir este procedimiento para cada usuario. Para muchos usuarios, esto puede ser una tarea tediosa. Con PowerShell para Microsoft 365, puede mostrar esta información para todos los usuarios con el siguiente comando:
  
```powershell
Get-AzureADUser | Select DisplayName, UsageLocation
```


>[!Note]
>PowerShell Core no es compatible con el Módulo Microsoft Azure Active Directory para Windows PowerShell ni los cmdlet que llevan **Msol** en su nombre. Para seguir usando estos cmdlets, debe ejecutarlos desde Windows PowerShell.
>

Este es un ejemplo del resultado:
  
```powershell
DisplayName                               UsageLocation
-----------                               -------------
Bonnie Kearney                            GB
Fabrice Canel                             BR
Brian Johnson (TAILSPIN)                  US
Anne Wallace                              US
Alex Darrow                               US
David Longmuir                            BR
```

> [!TIP]
>  La interpretación de este comando de PowerShell es la siguiente: obtener todos los usuarios de la suscripción actual de Microsoft 365 ( **Get-AzureADUser** ), pero solo se muestra el nombre y la ubicación de cada usuario ( **Seleccione DisplayName, UsageLocation** ).
  
Como PowerShell para Microsoft 365 admite un lenguaje de Shell de comandos, puede seguir manipulando la información obtenida del comando **Get-AzureADUser** . Por ejemplo, es posible que quiera ordenar estos usuarios por su ubicación, agrupando todos los usuarios de Brasil, todos los usuarios de Estados Unidos juntos, etc. Este es el comando:
  
```powershell
Get-AzureADUser | Select DisplayName, UsageLocation | Sort UsageLocation, DisplayName
```

Este es un ejemplo del resultado:
  
```powershell
DisplayName                                 UsageLocation
-----------                                 -------------
David Longmuir                              BR
Fabrice Canel                               BR
Bonnie Kearney                              GB
Alex Darrow                                 US
Anne Wallace                                US
Brian Johnson (TAILSPIN)                    US
```

> [!TIP]
>  La interpretación de este comando de PowerShell es la siguiente: obtener todos los usuarios de la suscripción actual de Microsoft 365, pero solo mostrar el nombre y la ubicación de cada usuario y ordenarlos primero por su ubicación y, a continuación, sus nombres ( **Sort UsageLocation, DisplayName** ).
  
También puede usar un filtrado adicional. Por ejemplo, si solo quiere ver información sobre los usuarios que están en Brasil, use este comando:
  
```powershell
Get-AzureADUser | Where {$_.UsageLocation -eq "BR"} | Select DisplayName, UsageLocation 
```

Este es un ejemplo del resultado:
  
```powershell
DisplayName                                           UsageLocation
-----------                                           -------------
David Longmuir                                        BR
Fabrice Canel                                         BR
```

> [!TIP]
>  La interpretación de este comando de PowerShell es la siguiente: obtener todos los usuarios de la suscripción actual de Microsoft 365 cuya ubicación es Brasil ( **donde {$ \_ . UsageLocation-EQ "BR"}** ) y, a continuación, mostrar el nombre y la ubicación de cada usuario.
  
 **Una nota rápida sobre dominios de mayor tamaño**
  
Si tiene un dominio muy grande, con decenas de miles de usuarios, probar algunos de los ejemplos que se muestran en este artículo introductorio podría provocar una "limitación". Esto significa que, en función de algunos factores como la potencia del equipo y el ancho de banda de red disponible, está intentando hacer demasiado a la vez. Por ello, es posible que las organizaciones más grandes deseen dividir algunos de estos comandos de PowerShell para Microsoft 365 en dos comandos. Por ejemplo, este comando único devuelve todas las cuentas de usuario y muestra el nombre y la ubicación de cada usuario:
  
```powershell
Get-AzureADUser | Select DisplayName, UsageLocation
```

Esto funciona muy bien en los dominios más pequeños. No obstante, en una organización grande tal vez tenga que dividirlo en dos comandos: un comando para almacenar la información de la cuenta de usuario en una variable y otro comando para mostrar la información que se necesita. Aquí le mostramos un ejemplo:
  
```powershell
$x = Get-AzureADUser
$x | Select DisplayName, UsageLocation
```

La interpretación de este conjunto de comandos de PowerShell es la siguiente:
- Obtenga todos los usuarios de la suscripción actual de Microsoft 365 y almacene la información en una variable llamada $x ( **$x = Get-AzureADUser** ).
- Se muestra el contenido de la variable $x, pero solo se incluye el nombre y la ubicación de cada usuario (**$x | Select DisplayName, UsageLocation**).
  
## <a name="microsoft-365-has-features-that-you-can-only-configure-with-powershell-for-microsoft-365"></a>Microsoft 365 tiene características que solo se pueden configurar con PowerShell para Microsoft 365

El centro de administración de 365 de Microsoft tiene como objetivo proporcionar acceso a las tareas administrativas más comunes o relevantes que se aplican a la mayoría de las personas. Es decir, el centro de administración de Microsoft 365 se diseñó para que el administrador normal pudiera usar la herramienta para llevar a cabo las tareas de administración más comunes. Por esta definición, significa que hay algunas tareas que no se pueden completar mediante el centro de administración 365 de Microsoft.
  
Por ejemplo, el Centro de administración de Skype Empresarial Online proporciona unas cuantas opciones para crear invitaciones a reuniones personalizadas:
  
![Ejemplo de la presentación de las invitaciones a reuniones personalizadas en el centro de administración de Skype Empresarial Online](media/o365-powershell-meeting-invitation.png)
  
Con esta configuración, puede agregar un toque de personalización y profesionalidad a las invitaciones a reuniones. Sin embargo, la configuración de reuniones es mucho más que la mera creación de invitaciones a reuniones personalizadas. Por ejemplo, de forma predeterminada las reuniones permiten lo siguiente:
  
- A los usuarios anónimos obtener entrada automática a cada reunión.
    
- A los asistentes grabar la reunión.
    
- A todos los usuarios de la organización poder ser designados como moderadores cuando se unen a la reunión.
    
Estas opciones no están disponibles desde el Centro de administración de Skype Empresarial Online. Sin embargo, puede controlarlos desde PowerShell para Microsoft 365. Este es un comando que deshabilita estas tres opciones:
  
```powershell
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $False -AllowConferenceRecording $False -DesignateAsPresenter "None"
```

> [!NOTE]
> Para usar este comando, necesita instalar el [módulo de PowerShell de Skype Empresarial Online](https://www.microsoft.com/download/details.aspx?id=39366). 
  
> [!TIP]
>  La interpretación de este comando de PowerShell es la siguiente: para la configuración de las nuevas reuniones de Skype empresarial online ( **set-CsMeetingConfiguration** ), deshabilite la posibilidad de que los usuarios anónimos obtengan acceso automático a las reuniones ( **-AdmitAnonymousUsersByDefault $false** ), deshabilite la capacidad de los asistentes para registrar las reuniones ( **-AllowConferenceRecording $false** **) y** no designar a todos los usuarios de la organización como moderado
  
Si cambia de opinión y quiere restaurar la configuración predeterminada (habilitar todas las opciones), ejecute este comando:
  
```powershell
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $True -AllowConferenceRecording $True -DesignateAsPresenter "Company"
```

Esto es solo un ejemplo. Hay otras personas, por lo que usted, como administrador, debe sentirse cómodo con la ejecución de los comandos de PowerShell para Microsoft 365.
  
## <a name="powershell-for-microsoft-365-is-great-at-carrying-out-bulk-operations"></a>PowerShell para Microsoft 365 es excelente para llevar a cabo operaciones masivas

Históricamente, las interfaces visuales como el centro de administración de Microsoft 365 son más útiles cuando se tiene una única operación que realizar. Por ejemplo, si necesita deshabilitar una cuenta de usuario, puede usar el centro de administración de Microsoft 365 para buscar y borrar rápidamente una casilla. Esto puede ser más sencillo que realizar una operación similar en PowerShell.
  
Pero si tiene que cambiar muchas cosas o algunas cosas seleccionadas dentro de un conjunto amplio de otras cosas, es posible que el centro de administración de Microsoft 365 no sea el mejor uso de su tiempo. Por ejemplo, si tuviera que cambiar el prefijo en miles de números de teléfono o si necesitara quitar un usuario específico, Ken Myer, de todos sus sitios de SharePoint Online, ¿cómo lo haría en el centro de administración de Microsoft 365?
  
Para el último ejemplo, hay varios cientos de sitios de SharePoint Online y usted no sabe siquiera de cuáles es miembro Ken Meyer. Esto significa que tendrá que empezar en el centro de administración de 365 de Microsoft y, a continuación, llevar a cabo este procedimiento para cada sitio:
  
1. Haga clic en la **dirección URL** del sitio.
    
2. En el cuadro **propiedades de colección de sitios**, haga clic en el vínculo **Dirección del sitio web** para abrir el sitio.
    
3. En el sitio, haga clic en **Compartir**.
    
4. En el cuadro de diálogo **Compartir**, haga clic en el vínculo que muestra todos los usuarios que tienen permisos en el sitio:
    
     ![Ejemplo de visualización de los miembros de un sitio de SharePoint Online en el centro de administración de SharePoint Online](media/o365-powershell-view-permissions.png)
  
5. En el cuadro de diálogo **Compartido con**, haga clic en **Opciones avanzadas**.
    
6. Desplácese por la lista de usuarios, busque y seleccione Ken Myer (suponiendo que tiene permisos en el sitio) y, a continuación, haga clic en **Quitar permisos de usuario**.
    
Esto puede tardar mucho tiempo para varios cientos de sitios.
  
La alternativa es usar PowerShell para Microsoft 365 y el siguiente comando para quitar a Ken Myer de todos los sitios:
  
```powershell
Get-SPOSite | ForEach {Remove-SPOUser -Site $_.Url -LoginName "kenmyer@litwareinc.com"}
```

> [!NOTE]
> Este comando requiere que instale el [módulo de PowerShell de SharePoint Online](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps). 
  
> [!TIP]
>  La interpretación de este comando de PowerShell es la siguiente: obtener todos los sitios de SharePoint en la suscripción a Microsoft 365 actual ( **Get-SPOSite** ) y para cada sitio, quitar Ken Meyer de la lista de usuarios que pueden acceder a él ( **foreach {Remove-cónyuge-site $ \_ . URL-LoginName "kenmyer@litwareinc.com"}** ).
  
Como estamos indicando a Microsoft 365 que elimine Ken Meyer de cada sitio, incluidos aquellos en los que no tiene acceso, la visualización de este comando mostrará errores en los sitios en los que actualmente no tiene acceso. Podemos usar una condición adicional en este comando para quitar a Ken Meyer solo de los sitios que lo tienen en la lista de inicio de sesión, pero los errores que aparecerán no perjudican a los sitios en sí. Este comando puede tardar unos minutos en ejecutarse en cientos de sitios, en lugar de horas de trabajo a través del centro de administración de Microsoft 365.
  
Este es otro ejemplo de operación masiva. Use este comando para agregar a Bonnie Kearney, una nueva administradora de SharePoint, para todos los sitios de la organización:
  
```powershell
Get-SPOSite | ForEach {Add-SPOUser -Site $_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}
```

> [!TIP]
>  La interpretación de este comando de PowerShell es la siguiente: obtener todos los sitios de SharePoint en la suscripción actual de Microsoft 365 y para cada sitio, permitir el acceso de Bonnie Kearney agregando su nombre de inicio de sesión al grupo miembros del sitio ( **foreach {Add-cónyuge-site $ \_ . URL-LoginName "bkearney@litwareinc.com"-Group "miembros"}** ).
  
## <a name="powershell-for-microsoft-365-is-great-at-filtering-data"></a>PowerShell para Microsoft 365 es excelente en el filtrado de datos

El centro de administración de 365 de Microsoft ofrece varias formas de filtrar los datos para buscar de forma rápida y sencilla un subconjunto de información. Por ejemplo, Exchange facilita el filtrado de prácticamente cualquier propiedad de un buzón de usuario. Por ejemplo, a continuación se muestra la lista de buzones de todos los usuarios que viven en la ciudad de Bloomington:
  
![Ejemplo de cómo realizar una búsqueda avanzada en el centro de administración de Microsoft 365 para la lista de buzones para todos los usuarios que viven en la ciudad de Bloomington.](media/o365-powershell-advanced-search.png)
  
El Centro de administración de Exchange también le permite combinar criterios de filtro. Por ejemplo, puede buscar los buzones de correo de todas las personas que viven en Bloomington y que trabajan en el Departamento de finanzas. 
  
Sin embargo, existen limitaciones en lo que puede hacer el Centro de administración de Exchange. Por ejemplo, tal vez le gustaría buscar los buzones de correo de las personas que viven en Bloomington o en San Diego, o los buzones de correo de todas las personas que no viven en Bloomington. 
  
Con PowerShell para Microsoft 365, puede obtener una lista de los buzones de correo de todas las personas que viven en las ciudades de Bloomington o San Diego con este comando:
  
```powershell
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and ($_.City -eq "San Diego" -or $_.City -eq "Bloomington")} | Select DisplayName, City
```

Este es un ejemplo del resultado:
  
```powershell
DisplayName                              City
-----------                              ----
Alex Darrow                              San Diego
Bonnie Kearney                           San Diego
Julian Isla                              Bloomington
Rob Young                                Bloomington
```

> [!TIP]
>  La interpretación de este comando de PowerShell es la siguiente: obtener todos los usuarios de la suscripción actual de Microsoft 365 que tienen un buzón de correo en las ciudades de San Diego o Bloomington ( **donde {$ \_ . RecipientTypeDetails-EQ "UserMailbox"-y ($ \_ . City-EQ "San Diego"-o $ \_ . City-EQ "Bloomington")}** ) y, a continuación, mostrar el nombre y la ciudad de cada ( **Select DisplayName, City** ).
  
Para obtener una lista de todos los buzones de personas que viven en cualquier otro lugar que no sea Bloomington, este es el comando:
  
```powershell
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and $_.City -ne "Bloomington"} | Select DisplayName, City
```

Este es un ejemplo del resultado:
  
```powershell
DisplayName                               City
-----------                               ----
MOD Administrator                         Redmond
Alex Darrow                               San Diego
Allie Bellew                              Bellevue
Anne Wallace                              Louisville
Aziz Hassouneh                            Cairo
Belinda Newman                            Charlotte
Bonnie Kearney                            San Diego
David Longmuir                            Waukesha
Denis Dehenne                             Birmingham
Garret Vargas                             Seattle
Garth Fort                                Tulsa
Janet Schorr                              Bellevue
```

> [!TIP]
>  La interpretación de este comando de PowerShell es la siguiente: obtener todos los usuarios de la suscripción actual de Microsoft 365 que tienen un buzón no ubicado en la ciudad de Bloomington ( **donde {$ \_ . RecipientTypeDetails-EQ "UserMailbox"-y $ \_ . City-ne "Bloomington"}** ) y, a continuación, mostrar el nombre y la ciudad de cada uno.
  
También puede usar caracteres comodín en los filtros de PowerShell para hacer coincidir parte de un nombre. Por ejemplo, suponga que está buscando una cuenta de usuario y lo único que recuerda es que su apellido era Anderson, Henderson o quizá era Jorgenson.
  
Puede realizar un seguimiento de ese usuario en el centro de administración de Microsoft 365 mediante la herramienta de búsqueda y llevar a cabo tres búsquedas diferentes:
  
- Una para  *Anderson* 
    
- Otra para  *Henderson* 
    
- Y otra para  *Jorgenson* 
    
Como todos los tres nombres terminan en "EZ", puede decirle a PowerShell que muestre todos los usuarios cuyo nombre termina en "hijo". Este es el comando:
  
```powershell
Get-User -Filter '{LastName -like "*son"}'
```

> [!TIP]
>  La interpretación de este comando de PowerShell es la siguiente: Obtenga todos los usuarios de la suscripción actual de Microsoft 365, pero use un filtro que solo Enumere los usuarios cuyos apellidos terminen en "hijo" ( **-Filter ' {LastName-like " \* hijo"} '** ). La \* sigla de cualquier juego de caracteres, que son letras en el caso del apellido del usuario.
  
## <a name="powershell-for-microsoft-365-makes-it-easy-to-print-or-save-data"></a>PowerShell para Microsoft 365 simplifica la tarea de imprimir o guardar datos

El centro de administración de 365 de Microsoft permite ver las listas de datos. Este es un ejemplo del Centro de administración de Skype Empresarial Online en el que se muestra una lista de los usuarios habilitados para Skype Empresarial Online:
  
![Ejemplo del centro de administración de Skype Empresarial Online que muestra una lista de usuarios que han sido habilitados para Skype Empresarial Online](media/o365-powershell-lync-users.png)
  
Para guardar la información en un archivo, debe copiarla y pegarla en un documento o en un archivo de Excel. En cualquier caso, la copia puede requerir formato adicional. Además, el centro de administración de Microsoft 365 no proporciona una forma de imprimir directamente la lista que se muestra.
  
Afortunadamente, puede usar PowerShell para no solo mostrar la lista, sino que la guarda en un archivo que se puede importar fácilmente a Excel. Este es un ejemplo de un comando para guardar datos de usuario de Skype Empresarial Online en un archivo de valores separados por comas (CSV), archivo que puede importarse fácilmente en forma de tabla a una hoja de cálculo de Excel:
  
```powershell
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Export-Csv -Path "C:\Logs\SfBUsers.csv" -NoTypeInformation
```

Este es un ejemplo de la pantalla:
  
![Ejemplo de una tabla importada a una hoja de cálculo de Excel para los datos de usuario de Skype Empresarial Online que se ha guardado en un archivo de valores separados por comas (CSV)](media/o365-powershell-data-in-excel.png)
  
> [!TIP]
>  La interpretación de este comando de PowerShell es la siguiente: Obtenga todos los usuarios de Skype empresarial online en la suscripción actual de Microsoft 365 ( **Get-CsOnlineUser** ), obtenga solo el nombre de usuario, el UPN y la ubicación ( **Seleccione DisplayName, UserPrincipalName, UsageLocation** ) y, a continuación, guarde dicha información en el archivo CSV denominado c: \\ logs \\SfBUsers.csv ( **Export-CSV-path "C: \\ logs \\SfBUsers.csv**
  
También puede usar las opciones de para guardar esta lista como archivo XML o como página HTML. De hecho, con los comandos de PowerShell adicionales, podría guardarlo directamente como archivo de Excel, con el formato personalizado que quiera. 
  
También puede enviar el resultado de un comando de PowerShell que muestra una lista directamente en la impresora predeterminada de Windows. A continuación se muestra un ejemplo:
  
```powershell
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Out-Printer
```

Y este es el aspecto que tendrá el documento impreso:
  
![Ejemplo de un documento impreso que fue el resultado de un comando de PowerShell que se muestra directamente en la impresora predeterminada de Windows.](media/o365-powershell-printed-data.png)
  
> [!TIP]
>  La interpretación de este comando de PowerShell es la siguiente: obtener todos los usuarios de Skype empresarial online en la suscripción actual de Microsoft 365, obtener solo el nombre de usuario, el UPN y la ubicación y, a continuación, enviar la información a la impresora predeterminada de Windows ( **out-Printer** ).
  
El documento impreso tiene el mismo formato sencillo que la visualización en la ventana de comandos de PowerShell, pero una vez que haya creado un comando de PowerShell para enumerar lo que necesita, solo tiene que agregar **| Fuera** de la impresora al final del comando para obtener una copia impresa desde la que trabajar.
  
## <a name="powershell-for-microsoft-365-lets-you-manage-across-server-products"></a>PowerShell para Microsoft 365 le permite administrar los productos de servidor

Los diferentes componentes que componen Microsoft 365 están diseñados para trabajar juntos. Por ejemplo, supongamos que agrega un nuevo usuario a Microsoft 365 y, cuando lo hace, especifica dicha información como el Departamento y el número de teléfono del usuario. La información estará disponible si obtiene acceso a la información del usuario mediante cualquiera de los servicios de Microsoft 365: Skype empresarial online, Exchange o SharePoint Online.
  
Pero eso es para la información habitual que abarca el conjunto de productos. La información específica del producto (por ejemplo, la información sobre el buzón de Exchange de un usuario) normalmente no está disponible en el conjunto de aplicaciones. Por ejemplo, para saber si el buzón de un usuario está o no habilitado, esa información solo está disponible en el Centro de administración de Exchange. 
  
Suponga que quiere crear un informe que muestre la información siguiente de todos los usuarios:
  
- El nombre para mostrar del usuario
    
- Si el usuario tiene licencia para Microsoft 365
    
- Si el buzón de Exchange del usuario se ha habilitado
    
- Si el usuario está habilitado en Skype Empresarial Online
    
Actualmente no puede usar el centro de administración de Microsoft 365 para crear un informe de este tipo fácilmente. En su lugar, tendrá que crear un documento independiente para almacenar la información, como una hoja de cálculo de Excel, y obtener todos los nombres de usuario e información de licencia del centro de administración de Microsoft 365, obtener información del buzón del centro de administración de Exchange, obtener información de Skype empresarial online del centro de administración de Skype empresarial online y, a continuación, intercalar y combinar dicha información
  
La alternativa es usar un script de PowerShell para compilar dicho informe.
  
El siguiente script de ejemplo es más complicado que los comandos que hasta ahora hemos visto en este artículo. Sin embargo, se muestra el potencial de usar PowerShell para crear vistas de información que son muy difíciles de hacer en caso contrario. Este es el script que puede compilar y mostrar la lista necesaria:
  
```powershell
$x = Get-AzureADUser

foreach ($i in $x)
    {
      $y = Get-Mailbox -Identity $i.UserPrincipalName
      $i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled

      $y = Get-CsOnlineUser -Identity $i.UserPrincipalName
      $i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled
    }

$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB
```

Este es un ejemplo del resultado:
  
```powershell
DisplayName             IsLicensed   IsMailboxEnabled   EnabledForSfB
-----------             ----------   ----------------   --------------
Bonnie Kearney          True         True               True
Fabrice Canel           True         True               True
Brian Johnson           False        True               False
Anne Wallace            True         True               True
Alex Darrow             True         True               True
David Longmuir          True         True               True
Katy Jordan             False        True               False
Molly Dempsey           False        True               False
```

La interpretación de este script de PowerShell es la siguiente:  

- Obtenga todos los usuarios de la suscripción actual de Microsoft 365 y almacene la información en una variable llamada $x ( **$x = Get-AzureADUser** ).
- Se inicia un bucle que se ejecuta para todos los usuarios en la variable denominada $x (**foreach ($i in $x)**).  
- Se define una variable denominada $y y se almacena la información del buzón de usuario en ella (**$y = Get-Mailbox -Identity $i.UserPrincipalName**).
- Se agrega una nueva propiedad a la información de usuario denominada IsMailBoxEnabled, que se establece en el valor de la propiedad IsMailBoxEnabled del buzón del usuario (**$i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled**).
- Se define una variable denominada $y y se almacena la información de Skype Empresarial Online del usuario en ella (**$y = Get-CsOnlineUser -Identity $i.UserPrincipalName**).
- Se agrega una nueva propiedad a la información de usuario denominada EnabledForSfB y esta se establece en el valor de la propiedad habilitada de la información de Skype Empresarial Online de usuario (**$i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled**).
- Se muestra la lista de usuarios, pero solo se incluyen el nombre de cada usuario, si tiene licencia y las dos nuevas propiedades que indican si el buzón está habilitado y si se habilitó para Skype Empresarial Online (**$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB**).
  
## <a name="see-also"></a>Consulte también

[Introducción a PowerShell para Microsoft 365](getting-started-with-office-365-powershell.md)
  
[Administración de cuentas de usuario, licencias y grupos de Microsoft 365 con PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Usar Windows PowerShell para crear informes en Microsoft 365](use-windows-powershell-to-create-reports-in-office-365.md)

