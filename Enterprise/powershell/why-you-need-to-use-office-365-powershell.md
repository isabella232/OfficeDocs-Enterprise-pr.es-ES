---
title: Por qué necesita usar PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/11/2019
ms.audience: ITPro
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Office_Other
ms.assetid: b3209b1a-40c7-4ede-8e78-8a88bb2adc8a
description: 'Resumen: comprenda por qué debe usar PowerShell de Office 365 para administrar Office 365, en algunos casos de manera más eficiente y, en otros casos, por necesidad.'
ms.openlocfilehash: f63f1a2361b225eed5d771b06b07f00bba26c392
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "30574104"
---
# <a name="why-you-need-to-use-office-365-powershell"></a>Por qué necesita usar PowerShell de Office 365

 **Resumen:** comprenda por qué tiene que usar PowerShell de Office 365 para administrar Office 365, en algunos casos de manera más eficiente y, en otros casos, por necesidad.
  
Con el centro de administración de 365 de Microsoft, no solo puede administrar las cuentas de usuario y licencias de Office 365, pero también puede administrar los productos de servidor de Office 365: Exchange, Skype empresarial online y SharePoint Online. En cambio, también puede administrar estos elementos con comandos de PowerShell de Office 365 y aprovechar las ventajas que le ofrece un entorno de lenguaje de línea de comandos y scripting para ganar en velocidad, automatización y funcionalidad.
  
En este artículo, le mostraremos las formas en que puede usar PowerShell de Office 365 para administrar Office 365.
  
- Office 365 PowerShell puede revelar información adicional que no puede ver con el centro de administración de Microsoft 365
    
- Office 365 tiene características que solo se pueden configurar mediante Office 365 PowerShell
    
- PowerShell de Office 365 es excelente para realizar operaciones masivas
    
- Office 365 PowerShell es excelente en el filtrado de datos
    
- Office 365 PowerShell facilita imprimir o guardar datos
    
- PowerShell de Office 365 le permite administrar los productos del servidor
    
Antes de empezar, hay que entender que PowerShell de Office 365 es un conjunto de módulos para Windows PowerShell, un entorno de línea de comandos para plataformas y servicios basados en Windows. Este entorno crea un lenguaje de shell de comandos que se puede ampliar con módulos adicionales y ofrece una forma de ejecutar scripts y comandos simples o complejos. Por ejemplo, después de instalar los módulos de PowerShell de Office 365 y conectarse a la suscripción de Office 365, puede ejecutar este comando para hacer una lista de todos los buzones de usuario de Microsoft Exchange Online:
  
```
Get-Mailbox
```

La obtención de la lista de buzones también puede realizarse fácilmente mediante el centro de administración de Microsoft 365, pero no se puede realizar fácilmente el recuento de la cantidad de elementos de todas las listas para todos los sitios de las aplicaciones Web.
  
Tenga en cuenta que Office 365 PowerShell está diseñado para aumentar y mejorar su capacidad para administrar Office 365, no para reemplazar el centro de administración de Microsoft 365. Como administrador de Office 365, debe al menos sentirse cómodo al usar PowerShell de Office 365, porque hay algunos procedimientos de configuración que solo pueden realizarse con comandos de PowerShell de Office 365. En estos casos, deberá comprender cómo hacer lo siguiente:
  
- Instalar los módulos de PowerShell de Office 365 (se realiza una sola vez en cada equipo de administrador).
    
- Conectarse a su suscripción de Office 365 (se realiza una vez por sesión de PowerShell).
    
- Recopilar la información necesaria para ejecutar los comandos de PowerShell de Office 365 necesarios.
    
- Ejecutar los comandos de PowerShell de Office 365 correctamente.
    
Después de haber aprendido estos conocimientos básicos, no es necesario hacer una lista de los usuarios de buzones con el comando **Get-Mailbox** ni es necesario que sepa cómo crear un nuevo comando como el anterior para contar todos los elementos de todas las listas de todos los sitios para todas las aplicaciones web. Microsoft y la Comunidad de administradores de Office 365 pueden ayudarle con eso cuando sea necesario.
  
## <a name="office-365-powershell-can-reveal-additional-information-that-you-cannot-see-with-the-microsoft-365-admin-center"></a>Office 365 PowerShell puede revelar información adicional que no puede ver con el centro de administración de Microsoft 365

El centro de administración de 365 de Microsoft muestra una gran cantidad de información útil, pero esto no significa que muestre toda la información posible que Office 365 almacena en los usuarios, las licencias, los buzones de correo y los sitios. A continuación, se muestra un ejemplo de **usuarios y grupos** en el centro de administración de Microsoft 365:
  
![Ejemplo de la presentación de usuarios y grupos en el centro de administración de Microsoft 365.](media/o365-powershell-users-and-groups.png)
  
Para muchos fines, se muestra la información que necesita saber. En cambio, algunas veces necesitará más. Por ejemplo, las licencias de Office 365 (y las características de Office 365 disponibles para un usuario) dependen en parte de la ubicación geográfica del usuario. Las directivas y características que se pueden extender a un usuario que vive en los Estados Unidos tal vez no sean las mismas que las directivas y características que se pueden extender a un usuario que vive en India o en Bélgica. Puede usar el centro de administración de Microsoft 365 para determinar la ubicación geográfica de un usuario con estos pasos:
  
1. Haga doble clic en el **Nombre para mostrar** del usuario.
    
2. En el panel de presentación de las propiedades del usuario, haga clic en **Detalles**.
    
3. En la pantalla de detalles, haga clic en **Detalles adicionales**.
    
4. Desplácese hacia abajo hasta que vea el encabezado **País o región**:
    
     ![Ejemplo de la información de región de un usuario en el centro de administración de Microsoft 365.](media/o365-powershell-usage-location.png)
  
5. Escriba el nombre para mostrar y la ubicación del usuario en una hoja de papel, o cópielo y péguelo en el Bloc de notas. 
    
Debe repetir este procedimiento para cada usuario. Para muchos usuarios, esto puede ser una tarea tediosa. Con PowerShell de Office 365, puede mostrar esta información para todos los usuarios con el siguiente comando:
  
```
Get-MsolUser | Select DisplayName, UsageLocation
```

> [!NOTE]
> Este comando requiere que instale el [módulo de Windows Azure Active Directory](https://docs.microsoft.com/powershell/module/Azuread/?view=azureadps-2.0). 
  
Este es un ejemplo del resultado:
  
```
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
>  La interpretación de este comando de PowerShell de Office 365 es la siguiente: se obtienen todos los usuarios de la suscripción actual a Office 365 (**Get-MsolUser**), pero solo se muestra el nombre y la ubicación de cada usuario (**Select DisplayName, UsageLocation**).
  
Dado que PowerShell de Office 365 admite un lenguaje de shell de comandos, puede manipular aún más la información que obtiene del comando **Get-MSolUser**. Por ejemplo, tal vez le gustaría ordenar estos usuarios según su ubicación, agrupando todos los usuarios brasileños, todos los usuarios de Estados Unidos, etc. Este es el comando:
  
```
Get-MsolUser | Select DisplayName, UsageLocation | Sort UsageLocation, DisplayName
```

Este es un ejemplo del resultado:
  
```
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
>  La interpretación de este comando de PowerShell de Office 365 es la siguiente: se obtienen todos los usuarios de la suscripción actual a Office 365, pero solo se muestra el nombre y la ubicación de cada usuario, y se ordenan primero por ubicación y, después, por sus nombres (**Sort UsageLocation, DisplayName**).
  
También puede usar un filtrado adicional. Por ejemplo, si solo quiere ver información sobre los usuarios que están en Brasil, use este comando:
  
```
Get-MsolUser | Where {$_.UsageLocation -eq "BR"} | Select DisplayName, UsageLocation 
```

Este es un ejemplo del resultado:
  
```
DisplayName                                           UsageLocation
-----------                                           -------------
David Longmuir                                        BR
Fabrice Canel                                         BR
```

> [!TIP]
>  La interpretación de este comando de PowerShell de Office 365 es la siguiente: se obtienen todos los usuarios de la suscripción actual a Office 365 cuya ubicación es Brasil (**Where {$\_.UsageLocation -eq "BR"}**) y, después, se muestra el nombre y la ubicación de cada usuario.
  
 **Una nota rápida sobre dominios de mayor tamaño**
  
Si tiene un dominio muy grande, con decenas de miles de usuarios, probar algunos de los ejemplos que se muestran en este artículo introductorio podría provocar una "limitación". Esto significa que, en función de algunos factores como la potencia del equipo y el ancho de banda de red disponible, está intentando hacer demasiado a la vez. Por ello, las grandes organizaciones quizá quieran dividir algunos de estos comandos de PowerShell de Office 365 en dos comandos. Por ejemplo, este comando único devuelve todas las cuentas de usuario y muestra el nombre y la ubicación de cada usuario:
  
```
Get-MsolUser | Select DisplayName, UsageLocation
```

Esto funciona muy bien en los dominios más pequeños. No obstante, en una organización grande tal vez tenga que dividirlo en dos comandos: un comando para almacenar la información de la cuenta de usuario en una variable y otro comando para mostrar la información que se necesita. Aquí le mostramos un ejemplo:
  
```
$x = Get-MsolUser
$x | Select DisplayName, UsageLocation
```


La interpretación de este conjunto de comandos de PowerShell de Office 365 es la siguiente:
- Se obtienen todos los usuarios de la suscripción actual de Office 365 y se almacena la información en una variable denominada $x (**$x = Get-MsolUser**).
- Se muestra el contenido de la variable $x, pero solo se incluye el nombre y la ubicación de cada usuario (**$x | Select DisplayName, UsageLocation**).
  
## <a name="office-365-has-features-that-you-can-only-configure-with-office-365-powershell"></a>Office 365 tiene características que solo se pueden configurar con PowerShell de Office 365

El centro de administración de 365 de Microsoft tiene como objetivo proporcionar acceso a las tareas administrativas más comunes o relevantes que se aplican a la mayoría de las personas. Es decir, el centro de administración de Microsoft 365 se diseñó para que el administrador normal pudiera usar la herramienta para llevar a cabo las tareas de administración más comunes. Por esta definición, significa que hay algunas tareas que no se pueden completar mediante el centro de administración 365 de Microsoft.
  
Por ejemplo, el Centro de administración de Skype Empresarial Online proporciona unas cuantas opciones para crear invitaciones a reuniones personalizadas:
  
![Ejemplo de la presentación de las invitaciones a reuniones personalizadas en el centro de administración de Skype Empresarial Online](media/o365-powershell-meeting-invitation.png)
  
Con esta configuración, puede agregar un toque de personalización y profesionalidad a las invitaciones a reuniones. Sin embargo, la configuración de reuniones es mucho más que la mera creación de invitaciones a reuniones personalizadas. Por ejemplo, de forma predeterminada las reuniones permiten lo siguiente:
  
- A los usuarios anónimos obtener entrada automática a cada reunión.
    
- A los asistentes grabar la reunión.
    
- A todos los usuarios de la organización poder ser designados como moderadores cuando se unen a la reunión.
    
Estas opciones no están disponibles desde el Centro de administración de Skype Empresarial Online. Sin embargo, se pueden controlar desde PowerShell de Office 365. Este es un comando que deshabilita estas tres opciones:
  
```
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $False -AllowConferenceRecording $False -DesignateAsPresenter "None"
```

> [!NOTE]
> Para usar este comando, necesita instalar el [módulo de PowerShell de Skype Empresarial Online](https://www.microsoft.com/download/details.aspx?id=39366). 
  
> [!TIP]
>  La interpretación de este comando de PowerShell de Office 365 es la siguiente: para configurar nuevas reuniones de Skype Empresarial Online (**Set-CsMeetingConfiguration**), no permita que los usuarios anónimos puedan obtener acceso automáticamente a reuniones (**-AdmitAnonymousUsersByDefault $False**), no permita que los asistentes graben las reuniones (**-AllowConferenceRecording $False**) y no designe a todos los usuarios de la organización como moderadores (**-DesignateAsPresenter "None"**).
  
Si cambia de opinión y quiere restaurar la configuración predeterminada (habilitar todas las opciones), ejecute este comando:
  
```
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $True -AllowConferenceRecording $True -DesignateAsPresenter "Company"
```

Esto es solo un ejemplo. Hay otros más. Este es el motivo por el que usted, como administrador de Office 365, debe sentirse cómodo ejecutando comandos de PowerShell de Office 365.
  
## <a name="office-365-powershell-is-great-at-carrying-out-bulk-operations"></a>Office 365 PowerShell es excelente para llevar a cabo operaciones masivas

Históricamente, las interfaces visuales como el centro de administración de Microsoft 365 son más útiles cuando se tiene una única operación que realizar. Por ejemplo, si necesita deshabilitar una cuenta de usuario, puede usar el centro de administración de Microsoft 365 para buscar y borrar rápidamente una casilla. Esto puede ser más sencillo que realizar una operación similar en PowerShell de Office 365.
  
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
  
La alternativa es usar PowerShell de Office 365 y el siguiente comando para quitar a Ken Myer de todos los sitios:
  
```
Get-SPOSite | ForEach {Remove-SPOUser -Site $_.Url -LoginName "kenmyer@litwareinc.com"}
```

> [!NOTE]
> Para usar este comando, necesita [instalar el Shell de administración de PowerShell para la conexión a SharePoint Online](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps). 
  
> [!TIP]
>  La interpretación de este comando de PowerShell de Office 365 es la siguiente: se obtienen todos los sitios de SharePoint de la suscripción actual a Office 365 (**Get-SPOSite**) y, por cada sitio, se quita a Ken Meyer de la lista de usuarios que pueden tener acceso al sitio (**ForEach {Remove-SPOUser -Site $\_.Url -LoginName "kenmyer@litwareinc.com"}**).
  
Como le estamos diciendo a Office 365 que quite a Ken Meyer de todos los sitios, incluidos aquellos a los que no tiene acceso, la visualización de este comando mostrará errores para los sitios a los que actualmente no tiene acceso. Podemos usar una condición adicional en este comando para quitar a Ken Meyer solo de los sitios que lo tienen en la lista de inicio de sesión, pero los errores que aparecerán no perjudican a los sitios en sí. Este comando puede tardar unos minutos en ejecutarse en cientos de sitios, en lugar de horas de trabajo a través del centro de administración de Microsoft 365.
  
Este es otro ejemplo de operación masiva. Use este comando para agregar a Bonnie Kearney, una nueva administradora de SharePoint, para todos los sitios de la organización:
  
```
Get-SPOSite | ForEach {Add-SPOUser -Site $_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}
```

> [!TIP]
>  La interpretación de este comando de PowerShell de Office 365 es la siguiente: se obtienen todos los sitios de SharePoint de la suscripción actual a Office 365 y, por cada sitio, se permite el acceso de Bonnie Kearney; para hacerlo, se agrega su nombre de inicio de sesión al grupo de integrantes del sitio (**ForEach {Add-SPOUser -Site $\_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}**).
  
## <a name="office-365-powershell-is-great-at-filtering-data"></a>PowerShell de Office 365 es excelente para filtrar datos

El centro de administración de 365 de Microsoft ofrece varias formas de filtrar los datos para buscar de forma rápida y sencilla un subconjunto de información. Por ejemplo, Exchange facilita el filtrado de prácticamente cualquier propiedad de un buzón de usuario. Por ejemplo, a continuación se muestra la lista de buzones de todos los usuarios que viven en la ciudad de Bloomington:
  
![Ejemplo de cómo realizar una búsqueda avanzada en el centro de administración de Microsoft 365 para la lista de buzones para todos los usuarios que viven en la ciudad de Bloomington.](media/o365-powershell-advanced-search.png)
  
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
```

> [!TIP]
>  La interpretación de este comando de PowerShell de Office 365 es la siguiente: se obtienen todos los usuarios de la suscripción actual a Office 365 que tienen un buzón de correo en las ciudades de San Diego o Bloomington (**Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and ($\_.City -eq "San Diego" -or $\_.City -eq "Bloomington")}**) y, después, se muestra el nombre y la ciudad de cada uno de ellos (**Select DisplayName, City**).
  
Para obtener una lista de todos los buzones de personas que viven en cualquier otro lugar que no sea Bloomington, este es el comando:
  
```
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and $_.City -ne "Bloomington"} | Select DisplayName, City
```

Este es un ejemplo del resultado:
  
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
>  La interpretación de este comando de PowerShell de Office 365 es la siguiente: se obtienen todos los usuarios de la suscripción actual a Office 365 que tienen un buzón que no se encuentra en la ciudad de Bloomington (**Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and $\_.City -ne "Bloomington"}**) y, después, se muestra el nombre y la ciudad de cada uno de ellos.
  
También puede usar caracteres comodín en los filtros de PowerShell de Office 365 para que coincidan con una parte del nombre. Por ejemplo, suponga que está buscando una cuenta de usuario y lo único que recuerda es que su apellido era Anderson, Henderson o quizá era Jorgenson.
  
Puede realizar un seguimiento de ese usuario en el centro de administración de Microsoft 365 mediante la herramienta de búsqueda y llevar a cabo tres búsquedas diferentes:
  
- Una para  *Anderson* 
    
- Otra para  *Henderson* 
    
- Y otra para  *Jorgenson* 
    
Dado que los tres nombres terminan en "son", puede indicar a PowerShell de Office 365 que muestre todos los usuarios cuyo nombre termina en "son". Este es el comando:
  
```
Get-User -Filter '{LastName -like "*son"}'
```

> [!TIP]
>  La interpretación de este comando de PowerShell de Office 365 es la siguiente: se obtienen todos los usuarios de la suscripción actual a Office 365, pero se usa un filtro que solo muestra los usuarios cuyos apellidos terminan en “son” (**-Filter '{LastName -like "\*son"}'**). El asterisco (\*) representa cualquier conjunto de caracteres (que, en el caso de los apellidos del usuario, son letras).
  
## <a name="office-365-powershell-makes-it-easy-to-print-or-save-data"></a>PowerShell de Office 365 permite imprimir o guardar datos fácilmente

El centro de administración de 365 de Microsoft permite ver las listas de datos. Este es un ejemplo del Centro de administración de Skype Empresarial Online en el que se muestra una lista de los usuarios habilitados para Skype Empresarial Online:
  
![Ejemplo del centro de administración de Skype Empresarial Online que muestra una lista de usuarios que han sido habilitados para Skype Empresarial Online](media/o365-powershell-lync-users.png)
  
Para guardar la información en un archivo, debe copiarla y pegarla en un documento o en un archivo de Excel. En cualquier caso, la copia puede requerir formato adicional. Además, el centro de administración de Microsoft 365 no proporciona una forma de imprimir directamente la lista que se muestra.
  
Afortunadamente, puede usar PowerShell de Office 365 no solo para mostrar la lista, sino que puede guardarla en un archivo que puede importarse fácilmente a Excel. Este es un ejemplo de un comando para guardar datos de usuario de Skype Empresarial Online en un archivo de valores separados por comas (CSV), archivo que puede importarse fácilmente en forma de tabla a una hoja de cálculo de Excel:
  
```
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Export-Csv -Path "C:\Logs\SfBUsers.csv" -NoTypeInformation
```

Este es un ejemplo de la pantalla:
  
![Ejemplo de una tabla importada a una hoja de cálculo de Excel para los datos de usuario de Skype Empresarial Online que se ha guardado en un archivo de valores separados por comas (CSV)](media/o365-powershell-data-in-excel.png)
  
> [!TIP]
>  La interpretación de este comando de PowerShell de Office 365 es la siguiente: se obtienen todos los usuarios de Skype Empresarial Online de la suscripción actual a Office 365 (**Get-CsOnlineUser**), se obtiene solo el nombre de usuario, el UPN y la ubicación (**Select DisplayName, UserPrincipalName, UsageLocation**) y, después, se guarda esa información en el archivo CSV denominado C:\\Logs\\SfBUsers.csv (**Export-Csv -Path "C:\\Logs\\SfBUsers.csv" -NoTypeInformation**).
  
También puede usar las opciones de para guardar esta lista como archivo XML o como página HTML. De hecho, con los comandos de PowerShell adicionales, podría guardarlo directamente como archivo de Excel, con el formato personalizado que quiera. 
  
También puede enviar el resultado de un comando de PowerShell de Office 365 que muestra una lista directamente a la impresora predeterminada de Windows. A continuación se muestra un ejemplo:
  
```
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Out-Printer
```

Y este es el aspecto que tendrá el documento impreso:
  
![Ejemplo de un documento impreso que se obtuvo como resultado de un comando de PowerShell de Office 365 que aparece directamente en la impresora predeterminada de Windows.](media/o365-powershell-printed-data.png)
  
> [!TIP]
>  La interpretación de este comando de PowerShell de Office 365 es la siguiente: se obtienen todos los usuarios de Skype Empresarial Online de la suscripción actual a Office 365, solo se obtiene el nombre de usuario, el UPN y la ubicación y, después, se envía dicha información a la impresora predeterminada de Windows (**Out-Printer**).
  
El documento impreso tiene el mismo formato simple que la visualización de la ventana de comandos de PowerShell de Office 365; pero, después de crear un comando de PowerShell de Office 365 que muestre lo que necesita ver, solo tiene que agregar **| Out-Printer** al final del comando para obtener una copia impresa con la que trabajar.
  
## <a name="office-365-powershell-lets-you-manage-across-server-products"></a>PowerShell de Office 365 le permite administrar los productos del servidor

Los diferentes componentes que conforman Office 365 están diseñados para poder funcionar conjuntamente. Por ejemplo, suponga que agrega un nuevo usuario a Office 365 y, cuando lo hace, especifica información como el departamento y el número de teléfono del usuario. Dicha información estará disponible si accede a la información del usuario mediante cualquiera de los productos de servidor de Office 365: Skype Empresarial Online, Exchange o SharePoint Online.
  
Pero eso es para la información habitual que abarca el conjunto de productos. La información específica del producto (por ejemplo, la información sobre el buzón de Exchange de un usuario) normalmente no está disponible en el conjunto de aplicaciones. Por ejemplo, para saber si el buzón de un usuario está o no habilitado, esa información solo está disponible en el Centro de administración de Exchange. 
  
Suponga que quiere crear un informe que muestre la información siguiente de todos los usuarios:
  
- El nombre para mostrar del usuario
    
- Si el usuario tiene licencias para Office 365
    
- Si el buzón de Exchange del usuario se ha habilitado
    
- Si el usuario está habilitado en Skype Empresarial Online
    
Actualmente no puede usar el centro de administración de Microsoft 365 para crear un informe de este tipo fácilmente. En su lugar, tendrá que crear un documento independiente para almacenar la información, como una hoja de cálculo de Excel, y obtener todos los nombres de usuario e información de licencia del centro de administración de Microsoft 365, obtener información del buzón de correo del centro de administración de Exchange, obtener Skype Información de empresa en línea desde el centro de administración de Skype empresarial online y, después, intercalar y combinar esa información.
  
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

Este es un ejemplo del resultado:
  
```
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

Esta es la interpretación del script de PowerShell de Office 365:  
- Se obtienen todos los usuarios de la suscripción actual de Office 365 y se almacena la información en una variable denominada $x (**$x = Get-MsolUser**).
- Se inicia un bucle que se ejecuta para todos los usuarios en la variable denominada $x (**foreach ($i in $x)**).  
- Se define una variable denominada $y y se almacena la información del buzón de usuario en ella (**$y = Get-Mailbox -Identity $i.UserPrincipalName**).
- Se agrega una nueva propiedad a la información de usuario denominada IsMailBoxEnabled, que se establece en el valor de la propiedad IsMailBoxEnabled del buzón del usuario (**$i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled**).
- Se define una variable denominada $y y se almacena la información de Skype Empresarial Online del usuario en ella (**$y = Get-CsOnlineUser -Identity $i.UserPrincipalName**).
- Se agrega una nueva propiedad a la información de usuario denominada EnabledForSfB y esta se establece en el valor de la propiedad habilitada de la información de Skype Empresarial Online de usuario (**$i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled**).
- Se muestra la lista de usuarios, pero solo se incluyen el nombre de cada usuario, si tiene licencia y las dos nuevas propiedades que indican si el buzón está habilitado y si se habilitó para Skype Empresarial Online (**$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB**).
  
## <a name="see-also"></a>Consulte también

[Introducción a PowerShell de Office 365](getting-started-with-office-365-powershell.md)
  
[Administrar licencias y cuentas de usuario con PowerShell de Office 365](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Usar Windows PowerShell para crear informes en Office 365](use-windows-powershell-to-create-reports-in-office-365.md)

