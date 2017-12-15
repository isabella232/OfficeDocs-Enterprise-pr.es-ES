---
title: "Por qué necesita usar PowerShell de Office 365"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- DecEntMigration
ms.assetid: b3209b1a-40c7-4ede-8e78-8a88bb2adc8a
description: "Resumen: comprenda por qué debe usar PowerShell de Office 365 para administrar Office 365, en algunos casos de manera más eficiente y, en otros casos, por necesidad."
ms.openlocfilehash: 46295ed851f24b16f775fd48dc8cdfbce39bf76c
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2017
---
# <a name="why-you-need-to-use-office-365-powershell"></a>Por qué necesita usar PowerShell de Office 365

 **Resumen:** Comprender por qué debe utilizar Office 365 PowerShell para administrar Office 365, en algunos casos más eficaz y, en otros casos por necesidad.
  
Con Centro de administración de Office 365, no solo puede administrar las cuentas de usuario y licencias de Office 365, sino que también puede administrar los productos del servidor de Office 365: Exchange, Skype Empresarial Online y SharePoint Online. En cambio, también puede administrar estos elementos con comandos de PowerShell de Office 365 y aprovechar las ventajas que le ofrece un entorno de lenguaje de línea de comandos y scripting para ganar en velocidad, automatización y funcionalidad.
  
En este artículo, le mostraremos las formas en que puede usar PowerShell de Office 365 para administrar Office 365.
  
- PowerShell de Office 365 puede revelar información adicional que no puede ver con Centro de administración de Office 365
    
- Office 365 contiene características que solo pueden configurarse usando PowerShell de Office 365
    
- PowerShell de Office 365 es excelente para realizar operaciones masivas
    
- PowerShell de Office 365 es excelente en el filtrado de datos
    
- PowerShell de Office 365 facilita imprimir o guardar datos
    
- PowerShell de Office 365 le permite administrar todos los productos de servidor
    
Antes de empezar, hay que entender que PowerShell de Office 365 es un conjunto de módulos para Windows PowerShell, un entorno de línea de comandos para plataformas y servicios basados en Windows. Este entorno crea un lenguaje de shell de comandos que se puede ampliar con módulos adicionales y ofrece una forma de ejecutar scripts y comandos simples o complejos. Por ejemplo, después de instalar los módulos de PowerShell de Office 365 y conectarse a la suscripción de Office 365, puede ejecutar este comando para hacer una lista de todos los buzones de usuario de Microsoft Exchange Online:
  
```
Get-Mailbox
```

También puede ejecutar este comando para calcular el número de elementos de todas las listas de todos los sitios de todas las aplicaciones web en SharePoint Online:
  
```
Get-SPOSite -Limit All | Get-SPWeb -Limit All | % {$_.Lists} | ? {$_ -is [Microsoft.SharePoint.SPDocumentLibrary]} | % {$total+= $_.ItemCount}; $total
```

También se puede obtener fácilmente la lista de buzones mediante el Centro de administración de Office 365, pero el recuento de elementos de todas las listas de todos los sitios de todas las aplicaciones web no puede realizarse tan fácilmente.
  
Tenga en cuenta que PowerShell de Office 365 está diseñado para aumentar y mejorar su capacidad de administrar Office 365, no para sustituir el Centro de administración de Office 365. Como administrador de Office 365, debe al menos sentirse cómodo al usar PowerShell de Office 365, porque hay algunos procedimientos de configuración que solo pueden realizarse con comandos de PowerShell de Office 365. En estos casos, deberá comprender cómo hacer lo siguiente:
  
- Instalar los módulos de PowerShell de Office 365 (se realiza una sola vez en cada equipo de administrador).
    
- Conectarse a su suscripción de Office 365 (se realiza una vez por sesión de PowerShell).
    
- Recopilar la información necesaria para ejecutar los comandos de PowerShell de Office 365 necesarios.
    
- Ejecutar los comandos de PowerShell de Office 365 correctamente.
    
Después de haber aprendido estos conocimientos básicos, no es necesario hacer una lista de los usuarios de buzones con el comando **Get-Mailbox** ni es necesario que sepa cómo crear un nuevo comando como el anterior para contar todos los elementos de todas las listas de todos los sitios para todas las aplicaciones web. Microsoft y la Comunidad de administradores de Office 365 pueden ayudarle con eso cuando sea necesario.
  
## <a name="office-365-powershell-can-reveal-additional-information-that-you-cannot-see-with-the-office-365-admin-center"></a>PowerShell de Office 365 puede revelar información adicional que no puede ver con Centro de administración de Office 365
<a name="reveal"> </a>

El Centro de administración de Office 365 muestra una gran cantidad de información útil, pero eso no significa que muestre toda la información posible que Office 365 almacena en usuarios, licencias, buzones de correo y sitios. Este es un ejemplo de **usuarios y grupos** en el Centro de administración de Office 365:
  
![Ejemplo de la presentación de los usuarios y grupos en el centro de administración de Office 365](images/o365_powershell_users_and_groups.png)
  
Para muchos fines, se muestra la información que necesita saber. En cambio, algunas veces necesitará más. Por ejemplo, las licencias de Office 365 (así como las características de Office 365 disponibles para un determinado usuario) dependen en parte de la ubicación geográfica del usuario. Las directivas y características que se pueden extender a un usuario que vive en los Estados Unidos tal vez no sean las mismas que las directivas y características que se pueden extender a un usuario que vive en India o en Bélgica. Puede usar el Centro de administración de Office 365 para determinar la ubicación geográfica de un usuario con estos pasos:
  
1. Haga doble clic en el **Nombre para mostrar** del usuario.
    
2. En el panel de presentación de las propiedades del usuario, haga clic en **Detalles**.
    
3. En la pantalla de detalles, haga clic en **Detalles adicionales**.
    
4. Desplácese hacia abajo hasta que vea el encabezado **País o región**:
    
     ![Ejemplo de la información de la región de un usuario en el centro de administración de Office 365](images/o365_powershell_usage_location.png)
  
5. Escriba el nombre para mostrar y la ubicación del usuario en una hoja de papel, o cópielo y péguelo en el Bloc de notas. 
    
Debe repetir este procedimiento para cada usuario. Para muchos usuarios, esto puede ser una tarea tediosa. Con PowerShell de Office 365, puede mostrar esta información para todos los usuarios con el siguiente comando:
  
```
Get-MsolUser | Select DisplayName, UsageLocation
```

> [!NOTE]
> Este comando requiere que instale el [módulo de Windows Azure Active Directory](https://technet.microsoft.com/en-us/library/jj151815.aspx). 
  
Este es un ejemplo de la pantalla:
  
```
DisplayName                               UsageLocation
-----------                               -------------
Zrinka Makovac                            US
Bonnie Kearney                            GB
Fabrice Canel                             BR
Brian Johnson (TAILSPIN)                  US
Anne Wallace                              US
Alex Darrow                               US
David Longmuir                            BR
```

> [!TIP]
>  La interpretación de este comando de Office 365 PowerShell: obtener todos los usuarios en la suscripción de Office 365 actual ( **Get-MsolUser** ), pero sólo mostrarán el nombre y la ubicación de cada usuario ( **Seleccione DisplayName, UsageLocation** ).
  
Dado que PowerShell de Office 365 admite un lenguaje de shell de comandos, puede manipular aún más la información que obtiene del comando **Get-MSolUser**. Por ejemplo, tal vez le gustaría ordenar estos usuarios según su ubicación, agrupando todos los usuarios brasileños, todos los usuarios de Estados Unidos, etc. Este es el comando:
  
```
Get-MsolUser | Select DisplayName, UsageLocation | Sort UsageLocation, DisplayName
```

Este es un ejemplo de la pantalla:
  
```
DisplayName                                 UsageLocation
-----------                                 -------------
David Longmuir                              BR
Fabrice Canel                               BR
Bonnie Kearney                              GB
Alex Darrow                                 US
Anne Wallace                                US
Brian Johnson (TAILSPIN)                    US
Zrinka Makovac                              US
```

> [!TIP]
>  La interpretación de este comando de Office 365 PowerShell: obtener todos los usuarios en la suscripción de Office 365 actual, pero sólo muestra el nombre y la ubicación para cada usuario y ordenar primero por su ubicación y, a continuación, sus nombres ( **UsageLocation de ordenación, DisplayName** ).
  
También puede usar un filtrado adicional. Por ejemplo, si solo quiere ver la información sobre los usuarios que están en Brasil, use este comando:
  
```
Get-MsolUser | Where {$_.UsageLocation -eq "BR"} | Select DisplayName, UsageLocation 
```

Este es un ejemplo de la pantalla:
  
```
DisplayName                                           UsageLocation
-----------                                           -------------
David Longmuir                                        BR
Fabrice Canel                                         BR
```

> [!TIP]
>  La interpretación de este comando de Office 365 PowerShell: obtener todos los usuarios en la suscripción de Office 365 actual cuya ubicación es Brasil ( **donde {$\_. UsageLocation - eq "BR"}** ), a continuación, muestre el nombre y la ubicación de cada usuario.
  
 **Una nota rápida sobre dominios más grandes**
  
Si tiene un dominio muy grande, con decenas de miles de usuarios, probar algunos de los ejemplos que se muestran en este artículo introductorio podría provocar una "limitación". Esto significa que, en función de algunos factores como la potencia del equipo y el ancho de banda de red disponible, está intentando hacer demasiado a la vez. Por ello, las grandes organizaciones quizá quieran dividir algunos de estos comandos de PowerShell de Office 365 en dos comandos. Por ejemplo, este comando único devuelve todas las cuentas de usuario y muestra el nombre y la ubicación de cada usuario:
  
```
Get-MsolUser | Select DisplayName, UsageLocation
```

Esto funciona muy bien en los dominios más pequeños. No obstante, en una organización grande tal vez tenga que dividirlo en dos comandos: un comando para almacenar la información de la cuenta de usuario en una variable y otro comando para mostrar la información que se necesita. Aquí le mostramos un ejemplo:
  
```
$x = Get-MsolUser
$x | Select DisplayName, UsageLocation
```


La interpretación de este conjunto de comandos de PowerShell de Office 365 es:
- Obtener todos los usuarios de la suscripción actual de Office 365 y almacenar la información en una variable denominada $x ( **$x = Get-MsolUser** ).
- Mostrar el contenido de la variable $x, pero incluir sólo el nombre y la ubicación de cada usuario ( **$x | Seleccione DisplayName, UsageLocation** ).
  
## <a name="office-365-has-features-that-you-can-only-configure-with-office-365-powershell"></a>Office 365 contiene características que solo pueden configurarse mediante PowerShell de Office 365
<a name="only"> </a>

El Centro de administración de Office 365 está diseñado para proporcionar acceso a las tareas administrativas más comunes o importantes aplicables a la mayoría de los usuarios. En otras palabras, el Centro de administración de Office 365 se ha diseñado para que el administrador común pueda usar la herramienta y llevar a cabo las tareas de administración más habituales. Por definición, esto significa que hay algunas tareas que no se pueden realizar con el Centro de administración de Office 365.
  
Por ejemplo, el Centro de administración de Skype Empresarial Online proporciona unas cuantas opciones para crear invitaciones a reuniones personalizadas:
  
![Ejemplo de la presentación de las invitaciones a reuniones personalizadas en el centro de administración de Skype Empresarial Online](images/o365_powershell_meeting_invitation.png)
  
Con esta configuración, puede agregar un toque de personalización y profesionalidad a las invitaciones a reuniones. Sin embargo, la configuración de reuniones es mucho más que la mera creación de invitaciones a reuniones personalizadas. Por ejemplo, de forma predeterminada las reuniones permiten lo siguiente:
  
- A los usuarios anónimos obtener entrada automática a cada reunión.
    
- A los asistentes grabar la reunión.
    
- A todos los usuarios de la organización poder ser designados como moderadores cuando se unen a la reunión.
    
Estas opciones no están disponibles desde el Centro de administración de Skype Empresarial Online. Sin embargo, se pueden controlar desde PowerShell de Office 365. Este es un comando que deshabilita estas tres opciones:
  
```
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $False -AllowConferenceRecording $False -DesignateAsPresenter "None"
```

> [!NOTE]
> Este comando requiere que instale el [Módulo de Powershell para Skype Empresarial Online ](https://www.microsoft.com/download/details.aspx?id=39366). 
  
> [!TIP]
>  La interpretación de este comando de Office 365 PowerShell es: para la configuración de nuevo Skype para reuniones en línea de negocios ( **Conjunto CsMeetingConfiguration** ), deshabilitar permitiendo a los usuarios anónimos obtener la entrada automática de reuniones ( **- $False AdmitAnonymousUsersByDefault** ), deshabilitar la capacidad de los asistentes a las reuniones de registro ( **AllowConferenceRecording - $False** ) y designar todos los usuarios de su organización como moderadores ( **- DesignateAsPresenter "Ninguno"** ).
  
Si cambia de opinión y quiere restaurar la configuración predeterminada (todos ellos habilitados), ejecute este comando:
  
```
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $True -AllowConferenceRecording $True -DesignateAsPresenter "Company"
```

Esto es solo un ejemplo. Hay otros más. Este es el motivo por el que usted, como administrador de Office 365, debe sentirse cómodo ejecutando comandos de PowerShell de Office 365.
  
## <a name="office-365-powershell-is-great-at-carrying-out-bulk-operations"></a>PowerShell de Office 365 es excelente para llevar a cabo operaciones masivas
<a name="bulk"> </a>

Tradicionalmente, las interfaces visuales como el Centro de administración de Office 365 son muy útiles cuando tiene que llevar a cabo una sola operación. Por ejemplo, si necesita deshabilitar una cuenta de usuario, puede usar el Centro de administración de Office 365 para localizar de forma rápida y desactivar una casilla. Esto puede ser más sencillo que realizar una operación similar en PowerShell de Office 365.
  
Pero si tiene que cambiar muchas cosas, o algunas cosas seleccionadas dentro de un conjunto grande de otras cosas, el Centro de administración de Office 365 puede que no sea la mejor forma de sacar partido a su tiempo. Por ejemplo, si tuviera que cambiar el prefijo de miles de números de teléfono o quitar a un usuario específico, Ken Myer, de todos los sitios de SharePoint Online, ¿cómo haría esto en el Centro de administración de Office 365?
  
Para el último ejemplo, hay varios cientos de sitios de SharePoint Online y usted no sabe siquiera de cuáles es miembro Ken Meyer. Esto significa que tendrá que comenzar en el Centro de administración de Office 365 y luego realizar este procedimiento para cada sitio:
  
1. Haga clic en la **dirección URL** del sitio.
    
2. En el cuadro **propiedades de colección de sitios**, haga clic en el vínculo **Dirección del sitio web** para abrir el sitio.
    
3. En el sitio, haga clic en **Compartir**.
    
4. En el cuadro de diálogo **Compartir**, haga clic en el vínculo que muestra todos los usuarios que tienen permisos en el sitio:
    
     ![Ejemplo de visualización de los miembros de un sitio de SharePoint Online en el centro de administración de SharePoint Online](images/o365_powershell_view_permissions.png)
  
5. En el cuadro de diálogo **Compartido con**, haga clic en **Opciones avanzadas**.
    
6. Desplácese por la lista de usuarios, busque y seleccione Ken Myer (suponiendo que tiene permisos en el sitio) y, a continuación, haga clic en **Quitar permisos de usuario**.
    
Esto puede tardar mucho tiempo para varios cientos de sitios.
  
La alternativa es usar PowerShell de Office 365 y el siguiente comando para quitar a Ken Myer de todos los sitios:
  
```
Get-SPOSite | ForEach {Remove-SPOUser -Site $_.Url -LoginName "kenmyer@litwareinc.com"}
```

> [!NOTE]
> Este comando requiere la instalación de [SharePoint Online PowerShell](https://technet.microsoft.com/library/fp161372.aspx). 
  
> [!TIP]
>  La interpretación de este comando de Office 365 PowerShell: obtener todos los sitios de SharePoint en la suscripción de Office 365 actual ( **Get-SPOSite** ) y para cada sitio, quitar Ken Meyer de la lista de usuarios que pueden tener acceso a él ( **ForEach {Remove-SPOUser - Sitio $\_. URL - LoginName "kenmyer@litwareinc.com"}** ).
  
Como le estamos diciendo a Office 365 que quite a Ken Meyer de todos los sitios, incluidos aquellos a los que no tiene acceso, la visualización de este comando mostrará errores para los sitios a los que actualmente no tiene acceso. Podemos usar una condición adicional en este comando para quitar a Ken Meyer solo de los sitios que lo tienen en la lista de inicio de sesión, pero los errores que aparecerán no perjudican a los sitios en sí. Este comando puede tardar unos minutos en ejecutarse en cientos de sitios y ahorra horas de trabajo en el Centro de administración de Office 365.
  
Este es otro ejemplo de operación masiva. Use este comando para agregar a Bonnie Kearney, una nueva administradora de SharePoint, para todos los sitios de la organización:
  
```
Get-SPOSite | ForEach {Add-SPOUser -Site $_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}
```

> [!TIP]
>  La interpretación de este comando de Office 365 PowerShell: obtener todos los sitios de SharePoint en la suscripción de Office 365 actual y para cada sitio, permitir el acceso de Bonnie Kearney agregando su nombre de inicio de sesión para el grupo de miembros del sitio ( **ForEach {Add-SPOUser-sitio $\_. URL - LoginName "bkearney@litwareinc.com"-grupo "Miembros"}** ).
  
## <a name="office-365-powershell-is-great-at-filtering-data"></a>PowerShell de Office 365 es excelente en el filtrado de datos
<a name="filter"> </a>

El Centro de administración de Office 365 proporciona varias formas de filtrar los datos para ubicar rápida y fácilmente un subconjunto de información específica. Por ejemplo, Exchange facilita el filtrado de prácticamente cualquier propiedad de un buzón de usuario. Por ejemplo, a continuación se muestra la lista de buzones de todos los usuarios que viven en la ciudad de Bloomington:
  
![Ejemplo de hacer una búsqueda avanzada en el centro de administración de Office 365 para la lista de buzones de correo para todos los usuarios que viven en la ciudad de Bloomington](images/o365_powershell_advanced_search.png)
  
El Centro de administración de Exchange también le permite combinar criterios de filtro. Por ejemplo, puede buscar los buzones de correo de todas las personas que viven en Bloomington y que trabajan en el Departamento de finanzas. 
  
Sin embargo, existen limitaciones en lo que puede hacer el Centro de administración de Exchange. Por ejemplo, tal vez le gustaría buscar los buzones de correo de las personas que viven en Bloomington o en San Diego, o los buzones de correo de todas las personas que no viven en Bloomington. 
  
Con PowerShell de Office 365, puede obtener una lista de buzones de correo de todas las personas que viven en las ciudades de Bloomington o San Diego con este comando:
  
```
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and ($_.City -eq "San Diego" -or $_.City -eq "Bloomington")} | Select DisplayName, City
```

Este es un ejemplo de la pantalla:
  
```
DisplayName                              City
-----------                              ----
Alex Darrow                              San Diego
Bonnie Kearney                           San Diego
Julian Isla                              Bloomington
Rob Young                                Bloomington
Zrinka Makovac                           San Diego
```

> [!TIP]
>  La interpretación de este comando de Office 365 PowerShell: obtener todos los usuarios en la suscripción de Office 365 actual que tiene un buzón en las ciudades de San Diego o Bloomington ( **donde {$\_. RecipientTypeDetails - eq "UserMailbox"- y ($\_. Ciudad - eq "San Diego"- o $\_. Ciudad - eq "Bloomington")}** ), a continuación, muestre el nombre y la ciudad de cada ( **Seleccione DisplayName, ciudad** ).
  
Para obtener una lista de todos los buzones de personas que viven en cualquier otro lugar que no sea Bloomington, este es el comando:
  
```
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and $_.City -ne "Bloomington"} | Select DisplayName, City
```

Este es un ejemplo de la pantalla:
  
```
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
>  La interpretación de este comando de Office 365 PowerShell: obtener todos los usuarios en la suscripción de Office 365 actual que tienen un buzón no se encuentra en la ciudad de Bloomington ( **donde {$\_. RecipientTypeDetails - eq "UserMailbox"- y $\_. Ciudad - ne "Bloomington"}** ), a continuación, muestre el nombre y la ciudad para cada uno.
  
También puede usar caracteres comodín en los filtros de PowerShell de Office 365 para que coincidan con una parte del nombre. Por ejemplo, suponga que está buscando una cuenta de usuario y lo único que recuerda es que su apellido era Anderson, Henderson o quizá era Jorgenson.
  
Puede realizar un seguimiento de ese usuario en el Centro de administración de Office 365 mediante la herramienta de búsqueda y llevar a cabo tres búsquedas diferentes:
  
- Una para  *Anderson* 
    
- Otra para  *Henderson* 
    
- Y otra para  *Jorgenson* 
    
Dado que los tres nombres terminan en "son", puede indicar a PowerShell de Office 365 que muestre todos los usuarios cuyo nombre termina en "son". Este es el comando:
  
```
Get-User -Filter '{LastName -like "*son"}'
```

> [!TIP]
>  La interpretación de este comando de Office 365 PowerShell: obtener todos los usuarios de la suscripción actual de Office 365, pero usar un filtro que sólo muestra los usuarios cuyos apellidos terminan en "EZ" ( **-filtro ' {LastName-como "\*hijo"}'** ). El \* significa cualquier conjunto de caracteres que son letras en el caso de los apellidos del usuario.
  
## <a name="office-365-powershell-makes-it-easy-to-print-or-save-data"></a>PowerShell de Office 365 facilita imprimir o guardar datos
<a name="printsave"> </a>

El Centro de administración de Office 365 permite ver listas de datos. Este es un ejemplo del Centro de administración de Skype Empresarial Online en el que se muestra una lista de los usuarios habilitados para Skype Empresarial Online:
  
![Ejemplo del centro de administración de Skype Empresarial Online que muestra una lista de usuarios que han sido habilitados para Skype Empresarial Online](images/o365_powershell_lync_users.png)
  
Para guardar la información en un archivo, debe copiarla y pegarla en un documento o en un archivo de Excel. En cualquier caso, la copia puede requerir formato adicional. Además, el Centro de administración de Office 365 no proporciona ninguna forma de imprimir directamente la lista que aparece.
  
Afortunadamente, puede usar PowerShell de Office 365 no solo para mostrar la lista, sino que puede guardarla en un archivo que puede importarse fácilmente a Excel. Este es un ejemplo de un comando para guardar datos de usuario de Skype Empresarial Online en un archivo de valores separados por comas (CSV), archivo que puede importarse fácilmente en forma de tabla a una hoja de cálculo de Excel:
  
```
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Export-Csv -Path "C:\\Logs\\SfBUsers.csv" -NoTypeInformation
```

Este es un ejemplo de la pantalla:
  
![Ejemplo de una tabla importada a una hoja de cálculo de Excel para los datos de usuario de Skype Empresarial Online que se ha guardado en un archivo de valores separados por comas (CSV)](images/o365_powershell_data_in_excel.png)
  
> [!TIP]
>  La interpretación de este comando de Office 365 PowerShell: obtener todos lo Skype para usuarios de negocios en línea en la suscripción de Office 365 actual ( **Get-CsOnlineUser** ), obtener el nombre de usuario, UPN y ubicación ( **Seleccione DisplayName, UserPrincipalName, UsageLocation** ) y, a continuación, guardar que información en un archivo CSV denominado C:\\registros\\SfBUsers.csv ( **Export-Csv-Path "C:\\registros\\SfBUsers.csv" - NoTypeInformation** ).
  
También puede usar las opciones de para guardar esta lista como archivo XML o como página HTML. De hecho, con los comandos de PowerShell adicionales, podría guardarlo directamente como archivo de Excel, con el formato personalizado que quiera. 
  
También puede enviar el resultado de un comando de PowerShell de Office 365 que muestra una lista directamente a la impresora predeterminada de Windows. A continuación se muestra un ejemplo:
  
```
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Out-Printer
```

Y este es el aspecto que tendrá el documento impreso:
  
![Ejemplo de un documento impreso que fue el resultado de un comando de Office 365 PowerShell que aparece directamente en la impresora predeterminada de Windows](images/o365_powershell_printed_data.png)
  
> [!TIP]
>  La interpretación de este comando de Office 365 PowerShell: obtener todos lo Skype para usuarios de negocios en línea en la suscripción de Office 365 actual, obtener sólo el nombre de usuario, el UPN y la ubicación y, a continuación, enviar dicha información a la impresora de Windows predeterminada ( ** Out-Printer** ).
  
El documento impreso tiene el mismo formato simple como la visualización de la ventana de comandos de PowerShell de Office 365, pero una vez que haya creado un comando de Office 365 PowerShell para ver lo que necesita, sólo tiene que agregar **| Hacia fuera-impresora** al final del comando para obtener una copia impresa para trabajar desde.
  
## <a name="office-365-powershell-lets-you-manage-across-server-products"></a>PowerShell de Office 365 le permite administrar todos los productos de servidor
<a name="printsave"> </a>

Los diferentes componentes que conforman Office 365 están diseñados para poder funcionar conjuntamente. Por ejemplo, suponga que agrega un nuevo usuario a Office 365 y, cuando lo hace, especifica información como el departamento y el número de teléfono del usuario. Dicha información estará disponible si accede a la información del usuario mediante cualquiera de los productos de servidor de Office 365: Skype Empresarial Online, Exchange o SharePoint Online.
  
Pero eso es para la información habitual que abarca el conjunto de productos. La información específica del producto (por ejemplo, la información sobre el buzón de Exchange de un usuario) normalmente no está disponible en el conjunto de aplicaciones. Por ejemplo, para saber si el buzón de un usuario está o no habilitado, esa información solo está disponible en el Centro de administración de Exchange. 
  
Suponga que quiere crear un informe que muestre la información siguiente de todos los usuarios:
  
- El nombre para mostrar del usuario
    
- Si el usuario tiene licencias para Office 365
    
- Si el buzón de Exchange del usuario se ha habilitado
    
- Si el usuario está habilitado en Skype Empresarial Online
    
Actualmente, es posible usar el Centro de administración de Office 365 para crear un informe con facilidad. Por el contrario, tendrá que crear un documento independiente para almacenar la información, por ejemplo, una hoja de cálculo de Excel, y obtener todos los nombres de usuario y la información de licencia del Centro de administración de Office 365, obtener información del buzón del Centro de administración de Exchange, obtener información de Skype Empresarial Online del Centro de administración de Skype Empresarial Online y luego intercalar y combinar esa información.
  
La alternativa es usar un script de PowerShell de Office 365 para compilar dicho informe.
  
El siguiente script de ejemplo es más complicado que los comandos que hasta ahora hemos visto en este artículo. Pero muestra la posibilidad de usar PowerShell de Office 365 para crear vistas de información que son muy difíciles de obtener de otra forma. Este es el script que puede compilar y mostrar la lista necesaria:
  
```
$x = Get-MsolUser

foreach ($i in $x)
    {
      $y = Get-Mailbox -Identity $i.UserPrincipalName
      $i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled

      $y = Get-CsOnlineUser -Identity $i.UserPrincipalName
      $i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled
    }

$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB
```

Este es un ejemplo de la pantalla:
  
```
DisplayName             IsLicensed   IsMailboxEnabled   EnabledForSfB
-----------             ----------   ----------------   --------------
Zrinka Makovac          True         True               True
Bonnie Kearney          True         True               True
Fabrice Canel           True         True               True
Brian Johnson           False        True               False
Anne Wallace            True         True               True
Alex Darrow             True         True               True
David Longmuir          True         True               True
Katy Jordan             False        True               False
Molly Dempsey           False        True               False
```

La interpretación de esta secuencia de comandos de PowerShell de Office 365 es:  
- Obtener todos los usuarios de la suscripción actual de Office 365 y almacenar la información en una variable denominada $x ( **$x = Get-MsolUser** ).
- Iniciar un bucle que se ejecuta a través de todos los usuarios en la variable denominada $x ( **foreach ($i en $x)** ).  
- Definir una variable denominada $y y almacenar la información del buzón del usuario en él ( **$y = Get-Mailbox-Identity $i.UserPrincipalName** ).
- Agregar una nueva propiedad a la información de usuario denominada IsMailBoxEnabled y establecerla en el valor de la propiedad IsMailBoxEnabled del buzón del usuario ( **$i | Add-Member - MemberType NoteProperty-Name IsMailboxEnabled-valor $y.IsMailboxEnabled** ).
- Definir una variable denominada $y y almacenar Skype del usuario para obtener información de negocios en línea en él ( **$y = Get-CsOnlineUser-$i.UserPrincipalName identidad** ).
- Agregar una nueva propiedad a la información de usuario denominada EnabledForSfB y establecerla en el valor de la propiedad Enabled de Skype del usuario para obtener información en línea de negocio ( **$i | Add-Member - MemberType NoteProperty-Name EnabledForSfB-valor $y.Enabled** ).
- Mostrar la lista de usuarios, pero incluir sólo su nombre, si se conceden bajo licencia y las dos nuevas propiedades que indican si su buzón está habilitado y si están habilitados para Skype para los negocios en línea ( **$x | Seleccione DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB** ).
  
## <a name="see-also"></a>See also


#### 

[Introducción a PowerShell de Office 365](getting-started-with-office-365-powershell.md)
  
[Administrar licencias y cuentas de usuario con PowerShell de Office 365](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Usar Windows PowerShell para crear informes en Office 365](use-windows-powershell-to-create-reports-in-office-365.md)
