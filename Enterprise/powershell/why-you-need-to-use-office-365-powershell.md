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
# <a name="why-you-need-to-use-powershell-for-microsoft-365"></a><span data-ttu-id="adfd6-103">Por qué necesita usar PowerShell para Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="adfd6-103">Why you need to use PowerShell for Microsoft 365</span></span>

<span data-ttu-id="adfd6-104">*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="adfd6-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="adfd6-105">Con el centro de administración de 365 de Microsoft, no solo puede administrar las cuentas de usuario y licencias de Microsoft 365, pero también puede administrar los servicios de Microsoft 365 como Exchange Online, Teams y SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="adfd6-105">With the Microsoft 365 admin center, you can not only manage your Microsoft 365 user accounts and licenses, but you can also manage your Microsoft 365 services such as Exchange Online, Teams, and SharePoint Online.</span></span> <span data-ttu-id="adfd6-106">Sin embargo, también puede administrar estos elementos con comandos de PowerShell, aprovechando un entorno de línea de comandos y de lenguaje de scripting para la velocidad, la automatización y la capacidad adicional.</span><span class="sxs-lookup"><span data-stu-id="adfd6-106">However, you can also manage these elements with PowerShell commands, taking advantage of a command-line and scripting language environment for speed, automation, and additional capability.</span></span>
  
<span data-ttu-id="adfd6-107">En este artículo, le mostraremos las formas en que puede usar PowerShell para administrar Microsoft 365:</span><span class="sxs-lookup"><span data-stu-id="adfd6-107">In this article, we'll show you these ways in which you can use PowerShell to manage Microsoft 365:</span></span>
  
- <span data-ttu-id="adfd6-108">Revelar información adicional que no puede ver con el centro de administración de 365 de Microsoft</span><span class="sxs-lookup"><span data-stu-id="adfd6-108">Reveal additional information that you cannot see with the Microsoft 365 admin center</span></span>
    
- <span data-ttu-id="adfd6-109">Configurar las características y la configuración solo posible con PowerShell</span><span class="sxs-lookup"><span data-stu-id="adfd6-109">Configure features and settings only possible with PowerShell</span></span>
    
- <span data-ttu-id="adfd6-110">Realizar operaciones en masa</span><span class="sxs-lookup"><span data-stu-id="adfd6-110">Perform bulk operations</span></span>
    
- <span data-ttu-id="adfd6-111">Filtrar datos</span><span class="sxs-lookup"><span data-stu-id="adfd6-111">Filtering data</span></span>
    
- <span data-ttu-id="adfd6-112">Imprimir o guardar datos</span><span class="sxs-lookup"><span data-stu-id="adfd6-112">Print or save data</span></span>
    
- <span data-ttu-id="adfd6-113">Administrar a través de servicios</span><span class="sxs-lookup"><span data-stu-id="adfd6-113">Manage across services</span></span>
    
<span data-ttu-id="adfd6-114">Antes de empezar, comprenda que PowerShell para Microsoft 365 es un conjunto de módulos para Windows PowerShell, un entorno de línea de comandos para plataformas y servicios basados en Windows.</span><span class="sxs-lookup"><span data-stu-id="adfd6-114">Before you begin, understand that PowerShell for Microsoft 365 is a set of modules for Windows PowerShell, a command-line environment for Windows-based services and platforms.</span></span> <span data-ttu-id="adfd6-115">Este entorno crea un lenguaje de Shell de comandos que se puede extender con módulos adicionales y proporciona una forma de ejecutar comandos o scripts sencillos o complejos.</span><span class="sxs-lookup"><span data-stu-id="adfd6-115">This environment creates a command shell language that can be extended with additional modules and provides a way to execute simple or complex commands or scripts.</span></span> <span data-ttu-id="adfd6-116">Por ejemplo, después de instalar los módulos de PowerShell para Microsoft 365 y conectarse a su suscripción a Microsoft 365, puede ejecutar este comando para enumerar todos los buzones de usuario para Microsoft Exchange Online:</span><span class="sxs-lookup"><span data-stu-id="adfd6-116">For example, after you install the PowerShell for Microsoft 365 modules and connect to your Microsoft 365 subscription, you can run this command to list all of the user mailboxes for Microsoft Exchange Online:</span></span>
  
```powershell
Get-Mailbox
```

<span data-ttu-id="adfd6-117">La obtención de la lista de buzones también puede realizarse fácilmente mediante el centro de administración de Microsoft 365, pero no se puede realizar fácilmente el recuento de la cantidad de elementos de todas las listas para todos los sitios de las aplicaciones Web.</span><span class="sxs-lookup"><span data-stu-id="adfd6-117">Getting the list of mailboxes can also be easily done using the Microsoft 365 admin center, but counting the number of items in all of the lists for all of the sites for all of your web apps cannot be easily done.</span></span>
  
<span data-ttu-id="adfd6-118">Tenga en cuenta que PowerShell para Microsoft 365 está diseñado para aumentar y mejorar su capacidad para administrar Microsoft 365, no para reemplazar el centro de administración de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="adfd6-118">Please note that PowerShell for Microsoft 365 is designed to augment and enhance your ability to manage Microsoft 365, not to replace the Microsoft 365 admin center.</span></span> <span data-ttu-id="adfd6-119">Como administrador, debe estar al menos familiarizado con el uso de PowerShell para Microsoft 365 porque hay algunos procedimientos de configuración que solo se pueden realizar con PowerShell para los comandos de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="adfd6-119">As an administrator, you must become at least comfortable with using PowerShell for Microsoft 365 because there are some configuration procedures that can only be done with PowerShell for Microsoft 365 commands.</span></span> <span data-ttu-id="adfd6-120">En estos casos, deberá comprender cómo hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="adfd6-120">In these cases, you will be required to understand how to:</span></span>
  
- <span data-ttu-id="adfd6-121">Instale los módulos de PowerShell para Microsoft 365 (se realiza una sola vez para cada equipo de administrador).</span><span class="sxs-lookup"><span data-stu-id="adfd6-121">Install the PowerShell for Microsoft 365 modules (done only once for each administrator computer).</span></span>
    
- <span data-ttu-id="adfd6-122">Conéctese a su suscripción de Microsoft 365 (se realiza una vez por cada sesión de PowerShell).</span><span class="sxs-lookup"><span data-stu-id="adfd6-122">Connect to your Microsoft 365 subscription (done once for each PowerShell session).</span></span>
    
- <span data-ttu-id="adfd6-123">Recopilar la información necesaria para ejecutar los comandos de PowerShell necesarios para Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="adfd6-123">Gather the information needed to run the required PowerShell for Microsoft 365 commands.</span></span>
    
- <span data-ttu-id="adfd6-124">Ejecute correctamente los comandos de PowerShell para Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="adfd6-124">Run the PowerShell for Microsoft 365 commands successfully.</span></span>
    
<span data-ttu-id="adfd6-125">Después de haber aprendido estos conocimientos básicos, no es necesario hacer una lista de los usuarios de buzones con el comando **Get-Mailbox** ni es necesario que sepa cómo crear un nuevo comando como el anterior para contar todos los elementos de todas las listas de todos los sitios para todas las aplicaciones web.</span><span class="sxs-lookup"><span data-stu-id="adfd6-125">After learning these basic skills, you are not required to list your mailbox users with **Get-Mailbox** command, nor are you required to understand how to create a new command like the previous one to count all the items in all the lists for all of the sites for all of your web apps.</span></span> <span data-ttu-id="adfd6-126">Microsoft y la comunidad de administradores pueden ayudarle con esto según sea necesario.</span><span class="sxs-lookup"><span data-stu-id="adfd6-126">Microsoft and the community of administrators can help you with that as needed.</span></span>
  
## <a name="powershell-for-microsoft-365-can-reveal-additional-information-that-you-cannot-see-with-the-microsoft-365-admin-center"></a><span data-ttu-id="adfd6-127">PowerShell para Microsoft 365 puede revelar información adicional que no puede ver con el centro de administración de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="adfd6-127">PowerShell for Microsoft 365 can reveal additional information that you cannot see with the Microsoft 365 admin center</span></span>

<span data-ttu-id="adfd6-128">El centro de administración de 365 de Microsoft muestra una gran cantidad de información útil, pero esto no significa que muestre toda la información posible que Microsoft 365 almacena en los usuarios, las licencias, los buzones de correo y los sitios.</span><span class="sxs-lookup"><span data-stu-id="adfd6-128">The Microsoft 365 admin center displays a lot of useful information, but that doesn't mean that it displays all the possible information that Microsoft 365 stores on users, licenses, mailboxes, and sites.</span></span> <span data-ttu-id="adfd6-129">A continuación, se muestra un ejemplo de **usuarios y grupos** en el centro de administración de Microsoft 365:</span><span class="sxs-lookup"><span data-stu-id="adfd6-129">Here is an example for **users and groups** in the Microsoft 365 admin center:</span></span>
  
![Ejemplo de la presentación de usuarios y grupos en el centro de administración de Microsoft 365.](media/o365-powershell-users-and-groups.png)
  
<span data-ttu-id="adfd6-131">Para muchos fines, se muestra la información que necesita saber.</span><span class="sxs-lookup"><span data-stu-id="adfd6-131">For many purposes, this displays the information you need to know.</span></span> <span data-ttu-id="adfd6-132">En cambio, algunas veces necesitará más.</span><span class="sxs-lookup"><span data-stu-id="adfd6-132">However, there are times when you need more.</span></span> <span data-ttu-id="adfd6-133">Por ejemplo, las licencias de Microsoft 365 (y las características de Microsoft 365 disponibles para un usuario) dependen en parte de la ubicación geográfica del usuario.</span><span class="sxs-lookup"><span data-stu-id="adfd6-133">For example, Microsoft 365 licensing (and the Microsoft 365 features available to a user) depend in part on that user's geographic location.</span></span> <span data-ttu-id="adfd6-134">Las directivas y características que se pueden extender a un usuario que vive en los Estados Unidos tal vez no sean las mismas que las directivas y características que se pueden extender a un usuario que vive en India o en Bélgica.</span><span class="sxs-lookup"><span data-stu-id="adfd6-134">The policies and features you can extend to a user who lives in the United States might not be the same as the policies and features you can extend to a user who lives in India or in Belgium.</span></span> <span data-ttu-id="adfd6-135">Puede usar el centro de administración de Microsoft 365 para determinar la ubicación geográfica de un usuario con estos pasos:</span><span class="sxs-lookup"><span data-stu-id="adfd6-135">You can use the Microsoft 365 admin center to determine a user's geographic location with these steps:</span></span>
  
1. <span data-ttu-id="adfd6-136">Haga doble clic en el **Nombre para mostrar** del usuario.</span><span class="sxs-lookup"><span data-stu-id="adfd6-136">Double-click the user's **Display Name**.</span></span>
    
2. <span data-ttu-id="adfd6-137">En el panel de presentación de las propiedades del usuario, haga clic en **Detalles**.</span><span class="sxs-lookup"><span data-stu-id="adfd6-137">In the user properties display pane, click **details**.</span></span>
    
3. <span data-ttu-id="adfd6-138">En la pantalla de detalles, haga clic en **Detalles adicionales**.</span><span class="sxs-lookup"><span data-stu-id="adfd6-138">In the details display, click **additional details**.</span></span>
    
4. <span data-ttu-id="adfd6-139">Desplácese hacia abajo hasta que vea el encabezado **País o región**:</span><span class="sxs-lookup"><span data-stu-id="adfd6-139">Scroll down until you see the heading **Country or region**:</span></span>
    
     ![Ejemplo de la información de región de un usuario en el centro de administración de Microsoft 365.](media/o365-powershell-usage-location.png)
  
5. <span data-ttu-id="adfd6-141">Escriba el nombre para mostrar y la ubicación del usuario en una hoja de papel, o cópielo y péguelo en el Bloc de notas.</span><span class="sxs-lookup"><span data-stu-id="adfd6-141">Write the user's display name and location on a piece of paper, or copy and paste it into Notepad.</span></span> 
    
<span data-ttu-id="adfd6-142">Debe repetir este procedimiento para cada usuario.</span><span class="sxs-lookup"><span data-stu-id="adfd6-142">You must repeat this procedure for each user.</span></span> <span data-ttu-id="adfd6-143">Para muchos usuarios, esto puede ser una tarea tediosa.</span><span class="sxs-lookup"><span data-stu-id="adfd6-143">For many users, this can be a tedious task.</span></span> <span data-ttu-id="adfd6-144">Con PowerShell para Microsoft 365, puede mostrar esta información para todos los usuarios con el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="adfd6-144">With PowerShell for Microsoft 365, you can display this information for all of your users with the following command:</span></span>
  
```powershell
Get-AzureADUser | Select DisplayName, UsageLocation
```


>[!Note]
><span data-ttu-id="adfd6-145">PowerShell Core no es compatible con el Módulo Microsoft Azure Active Directory para Windows PowerShell ni los cmdlet que llevan **Msol** en su nombre.</span><span class="sxs-lookup"><span data-stu-id="adfd6-145">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="adfd6-146">Para seguir usando estos cmdlets, debe ejecutarlos desde Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="adfd6-146">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="adfd6-147">Este es un ejemplo del resultado:</span><span class="sxs-lookup"><span data-stu-id="adfd6-147">Here is an example of the display:</span></span>
  
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
>  <span data-ttu-id="adfd6-148">La interpretación de este comando de PowerShell es la siguiente: obtener todos los usuarios de la suscripción actual de Microsoft 365 ( **Get-AzureADUser** ), pero solo se muestra el nombre y la ubicación de cada usuario ( **Seleccione DisplayName, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="adfd6-148">The interpretation of this PowerShell command is: Get all of the users in the current Microsoft 365 subscription ( **Get-AzureADUser** ), but only display the name and location for each user ( **Select DisplayName, UsageLocation** ).</span></span>
  
<span data-ttu-id="adfd6-149">Como PowerShell para Microsoft 365 admite un lenguaje de Shell de comandos, puede seguir manipulando la información obtenida del comando **Get-AzureADUser** .</span><span class="sxs-lookup"><span data-stu-id="adfd6-149">Because PowerShell for Microsoft 365 supports a command shell language, you can further manipulate the information obtained from the **Get-AzureADUser** command.</span></span> <span data-ttu-id="adfd6-150">Por ejemplo, es posible que quiera ordenar estos usuarios por su ubicación, agrupando todos los usuarios de Brasil, todos los usuarios de Estados Unidos juntos, etc. Este es el comando:</span><span class="sxs-lookup"><span data-stu-id="adfd6-150">For example, maybe you'd like to sort these users by their location, grouping all the Brazilian users together, all the United States users together, etc. Here is the command:</span></span>
  
```powershell
Get-AzureADUser | Select DisplayName, UsageLocation | Sort UsageLocation, DisplayName
```

<span data-ttu-id="adfd6-151">Este es un ejemplo del resultado:</span><span class="sxs-lookup"><span data-stu-id="adfd6-151">Here is an example of the display:</span></span>
  
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
>  <span data-ttu-id="adfd6-152">La interpretación de este comando de PowerShell es la siguiente: obtener todos los usuarios de la suscripción actual de Microsoft 365, pero solo mostrar el nombre y la ubicación de cada usuario y ordenarlos primero por su ubicación y, a continuación, sus nombres ( **Sort UsageLocation, DisplayName** ).</span><span class="sxs-lookup"><span data-stu-id="adfd6-152">The interpretation of this PowerShell command is: Get all of the users in the current Microsoft 365 subscription, but only display the name and location for each user and sort them first by their location, and then their names ( **Sort UsageLocation, DisplayName** ).</span></span>
  
<span data-ttu-id="adfd6-p110">También puede usar un filtrado adicional. Por ejemplo, si solo quiere ver información sobre los usuarios que están en Brasil, use este comando:</span><span class="sxs-lookup"><span data-stu-id="adfd6-p110">You can also employ additional filtering. For example, if you only want to see information about users based in Brazil, use this command:</span></span>
  
```powershell
Get-AzureADUser | Where {$_.UsageLocation -eq "BR"} | Select DisplayName, UsageLocation 
```

<span data-ttu-id="adfd6-155">Este es un ejemplo del resultado:</span><span class="sxs-lookup"><span data-stu-id="adfd6-155">Here is an example of the display:</span></span>
  
```powershell
DisplayName                                           UsageLocation
-----------                                           -------------
David Longmuir                                        BR
Fabrice Canel                                         BR
```

> [!TIP]
>  <span data-ttu-id="adfd6-156">La interpretación de este comando de PowerShell es la siguiente: obtener todos los usuarios de la suscripción actual de Microsoft 365 cuya ubicación es Brasil ( **donde {$ \_ . UsageLocation-EQ "BR"}** ) y, a continuación, mostrar el nombre y la ubicación de cada usuario.</span><span class="sxs-lookup"><span data-stu-id="adfd6-156">The interpretation of this PowerShell command is: Get all of the users in the current Microsoft 365 subscription whose location is Brazil ( **Where {$\_.UsageLocation -eq "BR"}** ), then display the name and location for each user.</span></span>
  
 <span data-ttu-id="adfd6-157">**Una nota rápida sobre dominios de mayor tamaño**</span><span class="sxs-lookup"><span data-stu-id="adfd6-157">**A Quick Note Regarding Larger Domains**</span></span>
  
<span data-ttu-id="adfd6-158">Si tiene un dominio muy grande, con decenas de miles de usuarios, probar algunos de los ejemplos que se muestran en este artículo introductorio podría provocar una "limitación".</span><span class="sxs-lookup"><span data-stu-id="adfd6-158">If you have a very large domain with tens of thousands of users, trying some of the examples we show in this article could lead to "throttling."</span></span> <span data-ttu-id="adfd6-159">Esto significa que, en función de algunos factores como la potencia del equipo y el ancho de banda de red disponible, está intentando hacer demasiado a la vez.</span><span class="sxs-lookup"><span data-stu-id="adfd6-159">That means that, based on things like computing power and available network bandwidth, you're trying to do a little too much at one time.</span></span> <span data-ttu-id="adfd6-160">Por ello, es posible que las organizaciones más grandes deseen dividir algunos de estos comandos de PowerShell para Microsoft 365 en dos comandos.</span><span class="sxs-lookup"><span data-stu-id="adfd6-160">Because of that, larger organizations might want to split some of these PowerShell for Microsoft 365 commands into two commands.</span></span> <span data-ttu-id="adfd6-161">Por ejemplo, este comando único devuelve todas las cuentas de usuario y muestra el nombre y la ubicación de cada usuario:</span><span class="sxs-lookup"><span data-stu-id="adfd6-161">For example, this one command returns all the user accounts and shows the name and location for each:</span></span>
  
```powershell
Get-AzureADUser | Select DisplayName, UsageLocation
```

<span data-ttu-id="adfd6-p112">Esto funciona muy bien en los dominios más pequeños. No obstante, en una organización grande tal vez tenga que dividirlo en dos comandos: un comando para almacenar la información de la cuenta de usuario en una variable y otro comando para mostrar la información que se necesita. Aquí le mostramos un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="adfd6-p112">That works great for smaller domains. In a large organization, however, you might need to split that into two commands: one command to store the user account information in a variable and another command to display the needed information. Here is an example:</span></span>
  
```powershell
$x = Get-AzureADUser
$x | Select DisplayName, UsageLocation
```

<span data-ttu-id="adfd6-165">La interpretación de este conjunto de comandos de PowerShell es la siguiente:</span><span class="sxs-lookup"><span data-stu-id="adfd6-165">The interpretation of this set of PowerShell commands is:</span></span>
- <span data-ttu-id="adfd6-166">Obtenga todos los usuarios de la suscripción actual de Microsoft 365 y almacene la información en una variable llamada $x ( **$x = Get-AzureADUser** ).</span><span class="sxs-lookup"><span data-stu-id="adfd6-166">Get all of the users in the current Microsoft 365 subscription and store the information in a variable named $x ( **$x = Get-AzureADUser** ).</span></span>
- <span data-ttu-id="adfd6-167">Se muestra el contenido de la variable $x, pero solo se incluye el nombre y la ubicación de cada usuario (**$x | Select DisplayName, UsageLocation**).</span><span class="sxs-lookup"><span data-stu-id="adfd6-167">Display the contents of the variable $x, but only include the name and location for each user ( **$x | Select DisplayName, UsageLocation** ).</span></span>
  
## <a name="microsoft-365-has-features-that-you-can-only-configure-with-powershell-for-microsoft-365"></a><span data-ttu-id="adfd6-168">Microsoft 365 tiene características que solo se pueden configurar con PowerShell para Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="adfd6-168">Microsoft 365 has features that you can only configure with PowerShell for Microsoft 365</span></span>

<span data-ttu-id="adfd6-169">El centro de administración de 365 de Microsoft tiene como objetivo proporcionar acceso a las tareas administrativas más comunes o relevantes que se aplican a la mayoría de las personas.</span><span class="sxs-lookup"><span data-stu-id="adfd6-169">The Microsoft 365 admin center is intended to provide access to the most common or meaningful administrative tasks that apply to most people.</span></span> <span data-ttu-id="adfd6-170">Es decir, el centro de administración de Microsoft 365 se diseñó para que el administrador normal pudiera usar la herramienta para llevar a cabo las tareas de administración más comunes.</span><span class="sxs-lookup"><span data-stu-id="adfd6-170">In other words, the Microsoft 365 admin center was designed so that the typical administrator could use the tool to carry out the most common management tasks.</span></span> <span data-ttu-id="adfd6-171">Por esta definición, significa que hay algunas tareas que no se pueden completar mediante el centro de administración 365 de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="adfd6-171">By this definition, that means that there are some tasks that can't be completed by using the Microsoft 365 admin center.</span></span>
  
<span data-ttu-id="adfd6-172">Por ejemplo, el Centro de administración de Skype Empresarial Online proporciona unas cuantas opciones para crear invitaciones a reuniones personalizadas:</span><span class="sxs-lookup"><span data-stu-id="adfd6-172">For example, the Skype for Business Online Admin center provides a few options for creating custom meeting invitations:</span></span>
  
![Ejemplo de la presentación de las invitaciones a reuniones personalizadas en el centro de administración de Skype Empresarial Online](media/o365-powershell-meeting-invitation.png)
  
<span data-ttu-id="adfd6-p114">Con esta configuración, puede agregar un toque de personalización y profesionalidad a las invitaciones a reuniones. Sin embargo, la configuración de reuniones es mucho más que la mera creación de invitaciones a reuniones personalizadas. Por ejemplo, de forma predeterminada las reuniones permiten lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="adfd6-p114">With these settings, you can add a touch of personalization and professionalism to meeting invitations. However, there's more to meeting configuration settings than simply creating custom meeting invitations. For example, by default, meetings allow:</span></span>
  
- <span data-ttu-id="adfd6-177">A los usuarios anónimos obtener entrada automática a cada reunión.</span><span class="sxs-lookup"><span data-stu-id="adfd6-177">Anonymous users to gain automatic entrance to each meeting.</span></span>
    
- <span data-ttu-id="adfd6-178">A los asistentes grabar la reunión.</span><span class="sxs-lookup"><span data-stu-id="adfd6-178">Attendees to record the meeting.</span></span>
    
- <span data-ttu-id="adfd6-179">A todos los usuarios de la organización poder ser designados como moderadores cuando se unen a la reunión.</span><span class="sxs-lookup"><span data-stu-id="adfd6-179">All users from your organization to be designated as presenters when they join the meeting.</span></span>
    
<span data-ttu-id="adfd6-180">Estas opciones no están disponibles desde el Centro de administración de Skype Empresarial Online.</span><span class="sxs-lookup"><span data-stu-id="adfd6-180">These settings are not available from the Skype for Business Online Admin center.</span></span> <span data-ttu-id="adfd6-181">Sin embargo, puede controlarlos desde PowerShell para Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="adfd6-181">However, you can control them from PowerShell for Microsoft 365.</span></span> <span data-ttu-id="adfd6-182">Este es un comando que deshabilita estas tres opciones:</span><span class="sxs-lookup"><span data-stu-id="adfd6-182">Here is a command that disables these three settings:</span></span>
  
```powershell
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $False -AllowConferenceRecording $False -DesignateAsPresenter "None"
```

> [!NOTE]
> <span data-ttu-id="adfd6-183">Para usar este comando, necesita instalar el [módulo de PowerShell de Skype Empresarial Online](https://www.microsoft.com/download/details.aspx?id=39366).</span><span class="sxs-lookup"><span data-stu-id="adfd6-183">This command requires that you install the [Skype for Business Online PowerShell Module ](https://www.microsoft.com/download/details.aspx?id=39366).</span></span> 
  
> [!TIP]
>  <span data-ttu-id="adfd6-184">La interpretación de este comando de PowerShell es la siguiente: para la configuración de las nuevas reuniones de Skype empresarial online ( **set-CsMeetingConfiguration** ), deshabilite la posibilidad de que los usuarios anónimos obtengan acceso automático a las reuniones ( **-AdmitAnonymousUsersByDefault $false** ), deshabilite la capacidad de los asistentes para registrar las reuniones ( **-AllowConferenceRecording $false** **) y** no designar a todos los usuarios de la organización como moderado</span><span class="sxs-lookup"><span data-stu-id="adfd6-184">The interpretation of this PowerShell command is: For the settings for new Skype for Business Online meetings ( **Set-CsMeetingConfiguration** ), disable allowing anonymous users to gain automatic entrance to meetings ( **-AdmitAnonymousUsersByDefault $False** ), disable the ability for attendees to record meetings ( **-AllowConferenceRecording $False** ), and do not designate all users from your organization as presenters ( **-DesignateAsPresenter "None"** ).</span></span>
  
<span data-ttu-id="adfd6-185">Si cambia de opinión y quiere restaurar la configuración predeterminada (habilitar todas las opciones), ejecute este comando:</span><span class="sxs-lookup"><span data-stu-id="adfd6-185">If you change your mind and want to restore these default settings (all of them enabled), run this command:</span></span>
  
```powershell
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $True -AllowConferenceRecording $True -DesignateAsPresenter "Company"
```

<span data-ttu-id="adfd6-186">Esto es solo un ejemplo.</span><span class="sxs-lookup"><span data-stu-id="adfd6-186">This is just one example.</span></span> <span data-ttu-id="adfd6-187">Hay otras personas, por lo que usted, como administrador, debe sentirse cómodo con la ejecución de los comandos de PowerShell para Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="adfd6-187">There are others, which is why you, as an administrator, need to be comfortable with running PowerShell for Microsoft 365 commands.</span></span>
  
## <a name="powershell-for-microsoft-365-is-great-at-carrying-out-bulk-operations"></a><span data-ttu-id="adfd6-188">PowerShell para Microsoft 365 es excelente para llevar a cabo operaciones masivas</span><span class="sxs-lookup"><span data-stu-id="adfd6-188">PowerShell for Microsoft 365 is great at carrying out bulk operations</span></span>

<span data-ttu-id="adfd6-189">Históricamente, las interfaces visuales como el centro de administración de Microsoft 365 son más útiles cuando se tiene una única operación que realizar.</span><span class="sxs-lookup"><span data-stu-id="adfd6-189">Historically, visual interfaces like the Microsoft 365 admin center are most valuable when you have a single operation to perform.</span></span> <span data-ttu-id="adfd6-190">Por ejemplo, si necesita deshabilitar una cuenta de usuario, puede usar el centro de administración de Microsoft 365 para buscar y borrar rápidamente una casilla.</span><span class="sxs-lookup"><span data-stu-id="adfd6-190">For example, if you need to disable one user account, you can use the Microsoft 365 admin center to quickly locate and clear a checkbox.</span></span> <span data-ttu-id="adfd6-191">Esto puede ser más sencillo que realizar una operación similar en PowerShell.</span><span class="sxs-lookup"><span data-stu-id="adfd6-191">This can be simpler than performing a similar operation in PowerShell.</span></span>
  
<span data-ttu-id="adfd6-192">Pero si tiene que cambiar muchas cosas o algunas cosas seleccionadas dentro de un conjunto amplio de otras cosas, es posible que el centro de administración de Microsoft 365 no sea el mejor uso de su tiempo.</span><span class="sxs-lookup"><span data-stu-id="adfd6-192">But if you have to change many things or some selected things within a large set of other things, the Microsoft 365 admin center might not be the best use of your time.</span></span> <span data-ttu-id="adfd6-193">Por ejemplo, si tuviera que cambiar el prefijo en miles de números de teléfono o si necesitara quitar un usuario específico, Ken Myer, de todos sus sitios de SharePoint Online, ¿cómo lo haría en el centro de administración de Microsoft 365?</span><span class="sxs-lookup"><span data-stu-id="adfd6-193">For example, if you had to change the prefix on thousands of phone numbers or you needed to remove a specific user, Ken Myer, from all of your SharePoint Online sites, how would you do that in the Microsoft 365 admin center?</span></span>
  
<span data-ttu-id="adfd6-194">Para el último ejemplo, hay varios cientos de sitios de SharePoint Online y usted no sabe siquiera de cuáles es miembro Ken Meyer.</span><span class="sxs-lookup"><span data-stu-id="adfd6-194">For the latter example, you have several hundred SharePoint Online sites and you don't know even know which ones of which Ken Meyer is a member.</span></span> <span data-ttu-id="adfd6-195">Esto significa que tendrá que empezar en el centro de administración de 365 de Microsoft y, a continuación, llevar a cabo este procedimiento para cada sitio:</span><span class="sxs-lookup"><span data-stu-id="adfd6-195">That means you'll have to start at the Microsoft 365 admin center and then perform this procedure for each site:</span></span>
  
1. <span data-ttu-id="adfd6-196">Haga clic en la **dirección URL** del sitio.</span><span class="sxs-lookup"><span data-stu-id="adfd6-196">Click the **URL** of the site.</span></span>
    
2. <span data-ttu-id="adfd6-197">En el cuadro **propiedades de colección de sitios**, haga clic en el vínculo **Dirección del sitio web** para abrir el sitio.</span><span class="sxs-lookup"><span data-stu-id="adfd6-197">In the **site collection properties** box, click the **Web Site Address** link to open the site.</span></span>
    
3. <span data-ttu-id="adfd6-198">En el sitio, haga clic en **Compartir**.</span><span class="sxs-lookup"><span data-stu-id="adfd6-198">On the site, click **Share**.</span></span>
    
4. <span data-ttu-id="adfd6-199">En el cuadro de diálogo **Compartir**, haga clic en el vínculo que muestra todos los usuarios que tienen permisos en el sitio:</span><span class="sxs-lookup"><span data-stu-id="adfd6-199">In the **Share** dialog box click the link that shows you all the users who have permissions to the site:</span></span>
    
     ![Ejemplo de visualización de los miembros de un sitio de SharePoint Online en el centro de administración de SharePoint Online](media/o365-powershell-view-permissions.png)
  
5. <span data-ttu-id="adfd6-201">En el cuadro de diálogo **Compartido con**, haga clic en **Opciones avanzadas**.</span><span class="sxs-lookup"><span data-stu-id="adfd6-201">In the **Shared With** dialog box, click **Advanced**.</span></span>
    
6. <span data-ttu-id="adfd6-202">Desplácese por la lista de usuarios, busque y seleccione Ken Myer (suponiendo que tiene permisos en el sitio) y, a continuación, haga clic en **Quitar permisos de usuario**.</span><span class="sxs-lookup"><span data-stu-id="adfd6-202">Scroll down the list of users, find and select Ken Myer (assuming he has permissions to the site), and then click **Remove User Permissions**.</span></span>
    
<span data-ttu-id="adfd6-203">Esto puede tardar mucho tiempo para varios cientos de sitios.</span><span class="sxs-lookup"><span data-stu-id="adfd6-203">This can take a long time for several hundred sites.</span></span>
  
<span data-ttu-id="adfd6-204">La alternativa es usar PowerShell para Microsoft 365 y el siguiente comando para quitar a Ken Myer de todos los sitios:</span><span class="sxs-lookup"><span data-stu-id="adfd6-204">The alternative is to use PowerShell for Microsoft 365 and the following command to remove Ken Myer from all of your sites:</span></span>
  
```powershell
Get-SPOSite | ForEach {Remove-SPOUser -Site $_.Url -LoginName "kenmyer@litwareinc.com"}
```

> [!NOTE]
> <span data-ttu-id="adfd6-205">Este comando requiere que instale el [módulo de PowerShell de SharePoint Online](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span><span class="sxs-lookup"><span data-stu-id="adfd6-205">This command requires that you install the [SharePoint Online PowerShell module](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span> 
  
> [!TIP]
>  <span data-ttu-id="adfd6-206">La interpretación de este comando de PowerShell es la siguiente: obtener todos los sitios de SharePoint en la suscripción a Microsoft 365 actual ( **Get-SPOSite** ) y para cada sitio, quitar Ken Meyer de la lista de usuarios que pueden acceder a él ( **foreach {Remove-cónyuge-site $ \_ . URL-LoginName "kenmyer@litwareinc.com"}** ).</span><span class="sxs-lookup"><span data-stu-id="adfd6-206">The interpretation of this PowerShell command is:  Get all of the SharePoint sites in the current Microsoft 365 subscription ( **Get-SPOSite** ) and for each site, remove Ken Meyer from the list of users who can access it ( **ForEach {Remove-SPOUser -Site $\_.Url -LoginName "kenmyer@litwareinc.com"}** ).</span></span>
  
<span data-ttu-id="adfd6-207">Como estamos indicando a Microsoft 365 que elimine Ken Meyer de cada sitio, incluidos aquellos en los que no tiene acceso, la visualización de este comando mostrará errores en los sitios en los que actualmente no tiene acceso.</span><span class="sxs-lookup"><span data-stu-id="adfd6-207">Because we are telling Microsoft 365 to remove Ken Meyer from every site, including those in which he does not have access, the display of this command will show errors for those sites in which he does not currently have access.</span></span> <span data-ttu-id="adfd6-208">Podemos usar una condición adicional en este comando para quitar a Ken Meyer solo de los sitios que lo tienen en la lista de inicio de sesión, pero los errores que aparecerán no perjudican a los sitios en sí.</span><span class="sxs-lookup"><span data-stu-id="adfd6-208">We can use an additional condition on this command to remove Key Meyer only from the sites that have him in their login list, but the listed errors cause no harm to the sites themselves.</span></span> <span data-ttu-id="adfd6-209">Este comando puede tardar unos minutos en ejecutarse en cientos de sitios, en lugar de horas de trabajo a través del centro de administración de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="adfd6-209">This command might take a few minutes to run against hundreds of sites, rather than hours of working through the Microsoft 365 admin center.</span></span>
  
<span data-ttu-id="adfd6-p121">Este es otro ejemplo de operación masiva. Use este comando para agregar a Bonnie Kearney, una nueva administradora de SharePoint, para todos los sitios de la organización:</span><span class="sxs-lookup"><span data-stu-id="adfd6-p121">Here is another bulk operation example. Use this command to add Bonnie Kearney, a new SharePoint administrator, to all of the sites in the organization:</span></span>
  
```powershell
Get-SPOSite | ForEach {Add-SPOUser -Site $_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}
```

> [!TIP]
>  <span data-ttu-id="adfd6-212">La interpretación de este comando de PowerShell es la siguiente: obtener todos los sitios de SharePoint en la suscripción actual de Microsoft 365 y para cada sitio, permitir el acceso de Bonnie Kearney agregando su nombre de inicio de sesión al grupo miembros del sitio ( **foreach {Add-cónyuge-site $ \_ . URL-LoginName "bkearney@litwareinc.com"-Group "miembros"}** ).</span><span class="sxs-lookup"><span data-stu-id="adfd6-212">The interpretation of this PowerShell command is:  Get all of the SharePoint sites in the current Microsoft 365 subscription and for each site, allow Bonnie Kearney access by adding her login name to the Members group of the site ( **ForEach {Add-SPOUser -Site $\_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}** ).</span></span>
  
## <a name="powershell-for-microsoft-365-is-great-at-filtering-data"></a><span data-ttu-id="adfd6-213">PowerShell para Microsoft 365 es excelente en el filtrado de datos</span><span class="sxs-lookup"><span data-stu-id="adfd6-213">PowerShell for Microsoft 365 is great at filtering data</span></span>

<span data-ttu-id="adfd6-214">El centro de administración de 365 de Microsoft ofrece varias formas de filtrar los datos para buscar de forma rápida y sencilla un subconjunto de información.</span><span class="sxs-lookup"><span data-stu-id="adfd6-214">The Microsoft 365 admin center provides several different ways to filter your data to quickly and easily locate a targeted subset of information.</span></span> <span data-ttu-id="adfd6-215">Por ejemplo, Exchange facilita el filtrado de prácticamente cualquier propiedad de un buzón de usuario.</span><span class="sxs-lookup"><span data-stu-id="adfd6-215">For example, Exchange makes it easy to filter on practically any property of a user mailbox.</span></span> <span data-ttu-id="adfd6-216">Por ejemplo, a continuación se muestra la lista de buzones de todos los usuarios que viven en la ciudad de Bloomington:</span><span class="sxs-lookup"><span data-stu-id="adfd6-216">For example, here is the list of mailboxes for all the users who live in the city of Bloomington:</span></span>
  
![Ejemplo de cómo realizar una búsqueda avanzada en el centro de administración de Microsoft 365 para la lista de buzones para todos los usuarios que viven en la ciudad de Bloomington.](media/o365-powershell-advanced-search.png)
  
<span data-ttu-id="adfd6-p123">El Centro de administración de Exchange también le permite combinar criterios de filtro. Por ejemplo, puede buscar los buzones de correo de todas las personas que viven en Bloomington y que trabajan en el Departamento de finanzas.</span><span class="sxs-lookup"><span data-stu-id="adfd6-p123">The Exchange Admin center also lets you combine filter criteria. For example, you can find the mailboxes for all the people who live in Bloomington and who work in the Finance department.</span></span> 
  
<span data-ttu-id="adfd6-p124">Sin embargo, existen limitaciones en lo que puede hacer el Centro de administración de Exchange. Por ejemplo, tal vez le gustaría buscar los buzones de correo de las personas que viven en Bloomington o en San Diego, o los buzones de correo de todas las personas que no viven en Bloomington.</span><span class="sxs-lookup"><span data-stu-id="adfd6-p124">However, there are limitations to what you can do in the Exchange Admin center. For example, maybe you'd like to find the mailboxes of people who live in Bloomington or San Diego, or the mailboxes for all the people who don't live in Bloomington.</span></span> 
  
<span data-ttu-id="adfd6-222">Con PowerShell para Microsoft 365, puede obtener una lista de los buzones de correo de todas las personas que viven en las ciudades de Bloomington o San Diego con este comando:</span><span class="sxs-lookup"><span data-stu-id="adfd6-222">With PowerShell for Microsoft 365, you can get a list of mailboxes for all the people who live in the cities of Bloomington or San Diego with this command:</span></span>
  
```powershell
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and ($_.City -eq "San Diego" -or $_.City -eq "Bloomington")} | Select DisplayName, City
```

<span data-ttu-id="adfd6-223">Este es un ejemplo del resultado:</span><span class="sxs-lookup"><span data-stu-id="adfd6-223">Here is an example of the display:</span></span>
  
```powershell
DisplayName                              City
-----------                              ----
Alex Darrow                              San Diego
Bonnie Kearney                           San Diego
Julian Isla                              Bloomington
Rob Young                                Bloomington
```

> [!TIP]
>  <span data-ttu-id="adfd6-224">La interpretación de este comando de PowerShell es la siguiente: obtener todos los usuarios de la suscripción actual de Microsoft 365 que tienen un buzón de correo en las ciudades de San Diego o Bloomington ( **donde {$ \_ . RecipientTypeDetails-EQ "UserMailbox"-y ($ \_ . City-EQ "San Diego"-o $ \_ . City-EQ "Bloomington")}** ) y, a continuación, mostrar el nombre y la ciudad de cada ( **Select DisplayName, City** ).</span><span class="sxs-lookup"><span data-stu-id="adfd6-224">The interpretation of this PowerShell command is: Get all of the users in the current Microsoft 365 subscription who have a mailbox in the cities of either San Diego or Bloomington ( **Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and ($\_.City -eq "San Diego" -or $\_.City -eq "Bloomington")}** ), then display the name and city for each ( **Select DisplayName, City** ).</span></span>
  
<span data-ttu-id="adfd6-225">Para obtener una lista de todos los buzones de personas que viven en cualquier otro lugar que no sea Bloomington, este es el comando:</span><span class="sxs-lookup"><span data-stu-id="adfd6-225">To list all the mailboxes for people who live anywhere except Bloomington, here is the command:</span></span>
  
```powershell
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and $_.City -ne "Bloomington"} | Select DisplayName, City
```

<span data-ttu-id="adfd6-226">Este es un ejemplo del resultado:</span><span class="sxs-lookup"><span data-stu-id="adfd6-226">Here is an example of the display:</span></span>
  
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
>  <span data-ttu-id="adfd6-227">La interpretación de este comando de PowerShell es la siguiente: obtener todos los usuarios de la suscripción actual de Microsoft 365 que tienen un buzón no ubicado en la ciudad de Bloomington ( **donde {$ \_ . RecipientTypeDetails-EQ "UserMailbox"-y $ \_ . City-ne "Bloomington"}** ) y, a continuación, mostrar el nombre y la ciudad de cada uno.</span><span class="sxs-lookup"><span data-stu-id="adfd6-227">The interpretation of this PowerShell command is: Get all of the users in the current Microsoft 365 subscription who have a mailbox not located in the city of Bloomington ( **Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and $\_.City -ne "Bloomington"}** ), then display the name and city for each.</span></span>
  
<span data-ttu-id="adfd6-228">También puede usar caracteres comodín en los filtros de PowerShell para hacer coincidir parte de un nombre.</span><span class="sxs-lookup"><span data-stu-id="adfd6-228">You can also use wildcard characters in your PowerShell filters to match part of a name.</span></span> <span data-ttu-id="adfd6-229">Por ejemplo, suponga que está buscando una cuenta de usuario y lo único que recuerda es que su apellido era Anderson, Henderson o quizá era Jorgenson.</span><span class="sxs-lookup"><span data-stu-id="adfd6-229">For example, suppose you're looking for a user account, and all you can remember is that their last name was Anderson, or maybe Henderson, or maybe it was Jorgenson.</span></span>
  
<span data-ttu-id="adfd6-230">Puede realizar un seguimiento de ese usuario en el centro de administración de Microsoft 365 mediante la herramienta de búsqueda y llevar a cabo tres búsquedas diferentes:</span><span class="sxs-lookup"><span data-stu-id="adfd6-230">You could track down that user in the Microsoft 365 admin center by using the search tool and carrying out three different searches:</span></span>
  
- <span data-ttu-id="adfd6-231">Una para  *Anderson*</span><span class="sxs-lookup"><span data-stu-id="adfd6-231">One for  *Anderson*</span></span> 
    
- <span data-ttu-id="adfd6-232">Otra para  *Henderson*</span><span class="sxs-lookup"><span data-stu-id="adfd6-232">One for  *Henderson*</span></span> 
    
- <span data-ttu-id="adfd6-233">Y otra para  *Jorgenson*</span><span class="sxs-lookup"><span data-stu-id="adfd6-233">One for  *Jorgenson*</span></span> 
    
<span data-ttu-id="adfd6-234">Como todos los tres nombres terminan en "EZ", puede decirle a PowerShell que muestre todos los usuarios cuyo nombre termina en "hijo".</span><span class="sxs-lookup"><span data-stu-id="adfd6-234">Because all three of these names end in "son", you can tell PowerShell to display all the users whose name ends in "son".</span></span> <span data-ttu-id="adfd6-235">Este es el comando:</span><span class="sxs-lookup"><span data-stu-id="adfd6-235">Here is the command:</span></span>
  
```powershell
Get-User -Filter '{LastName -like "*son"}'
```

> [!TIP]
>  <span data-ttu-id="adfd6-236">La interpretación de este comando de PowerShell es la siguiente: Obtenga todos los usuarios de la suscripción actual de Microsoft 365, pero use un filtro que solo Enumere los usuarios cuyos apellidos terminen en "hijo" ( **-Filter ' {LastName-like " \* hijo"} '** ).</span><span class="sxs-lookup"><span data-stu-id="adfd6-236">The interpretation of this PowerShell command is: Get all of the users in the current Microsoft 365 subscription, but use a filter that only lists the users whose last names end in "son" ( **-Filter '{LastName -like "\*son"}'** ).</span></span> <span data-ttu-id="adfd6-237">La \* sigla de cualquier juego de caracteres, que son letras en el caso del apellido del usuario.</span><span class="sxs-lookup"><span data-stu-id="adfd6-237">The \* stands for any set of characters, which are letters in the case of the user's last name.</span></span>
  
## <a name="powershell-for-microsoft-365-makes-it-easy-to-print-or-save-data"></a><span data-ttu-id="adfd6-238">PowerShell para Microsoft 365 simplifica la tarea de imprimir o guardar datos</span><span class="sxs-lookup"><span data-stu-id="adfd6-238">PowerShell for Microsoft 365 makes it easy to print or save data</span></span>

<span data-ttu-id="adfd6-239">El centro de administración de 365 de Microsoft permite ver las listas de datos.</span><span class="sxs-lookup"><span data-stu-id="adfd6-239">The Microsoft 365 admin center lets you view lists of data.</span></span> <span data-ttu-id="adfd6-240">Este es un ejemplo del Centro de administración de Skype Empresarial Online en el que se muestra una lista de los usuarios habilitados para Skype Empresarial Online:</span><span class="sxs-lookup"><span data-stu-id="adfd6-240">Here is an example of the Skype for Business Online Admin center displaying a list of users who have been enabled for Skype for Business Online:</span></span>
  
![Ejemplo del centro de administración de Skype Empresarial Online que muestra una lista de usuarios que han sido habilitados para Skype Empresarial Online](media/o365-powershell-lync-users.png)
  
<span data-ttu-id="adfd6-242">Para guardar la información en un archivo, debe copiarla y pegarla en un documento o en un archivo de Excel.</span><span class="sxs-lookup"><span data-stu-id="adfd6-242">To save that information to a file, you must copy and paste it into a document or Excel.</span></span> <span data-ttu-id="adfd6-243">En cualquier caso, la copia puede requerir formato adicional.</span><span class="sxs-lookup"><span data-stu-id="adfd6-243">In either case, the copy might require additional formatting.</span></span> <span data-ttu-id="adfd6-244">Además, el centro de administración de Microsoft 365 no proporciona una forma de imprimir directamente la lista que se muestra.</span><span class="sxs-lookup"><span data-stu-id="adfd6-244">Additionally, the Microsoft 365 admin center does not provide a way to directly print the displayed list.</span></span>
  
<span data-ttu-id="adfd6-245">Afortunadamente, puede usar PowerShell para no solo mostrar la lista, sino que la guarda en un archivo que se puede importar fácilmente a Excel.</span><span class="sxs-lookup"><span data-stu-id="adfd6-245">Fortunately, you can use PowerShell to not only display the list, but save it to a file that can be easily imported into Excel.</span></span> <span data-ttu-id="adfd6-246">Este es un ejemplo de un comando para guardar datos de usuario de Skype Empresarial Online en un archivo de valores separados por comas (CSV), archivo que puede importarse fácilmente en forma de tabla a una hoja de cálculo de Excel:</span><span class="sxs-lookup"><span data-stu-id="adfd6-246">Here is an example command to save Skype for Business Online user data to a comma-separated values (CSV) file, a file that can be easily imported as a table in an Excel worksheet:</span></span>
  
```powershell
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Export-Csv -Path "C:\Logs\SfBUsers.csv" -NoTypeInformation
```

<span data-ttu-id="adfd6-247">Este es un ejemplo de la pantalla:</span><span class="sxs-lookup"><span data-stu-id="adfd6-247">Here is an example of the display:</span></span>
  
![Ejemplo de una tabla importada a una hoja de cálculo de Excel para los datos de usuario de Skype Empresarial Online que se ha guardado en un archivo de valores separados por comas (CSV)](media/o365-powershell-data-in-excel.png)
  
> [!TIP]
>  <span data-ttu-id="adfd6-249">La interpretación de este comando de PowerShell es la siguiente: Obtenga todos los usuarios de Skype empresarial online en la suscripción actual de Microsoft 365 ( **Get-CsOnlineUser** ), obtenga solo el nombre de usuario, el UPN y la ubicación ( **Seleccione DisplayName, UserPrincipalName, UsageLocation** ) y, a continuación, guarde dicha información en el archivo CSV denominado c: \\ logs \\SfBUsers.csv ( **Export-CSV-path "C: \\ logs \\SfBUsers.csv**</span><span class="sxs-lookup"><span data-stu-id="adfd6-249">The interpretation of this PowerShell command is: Get all of the Skype for Business Online users in the current Microsoft 365 subscription ( **Get-CsOnlineUser** ), obtain only the user name, UPN, and location ( **Select DisplayName, UserPrincipalName, UsageLocation** ), and then save that information in CSV file named C:\\Logs\\SfBUsers.csv ( **Export-Csv -Path "C:\\Logs\\SfBUsers.csv" -NoTypeInformation** ).</span></span>
  
<span data-ttu-id="adfd6-p131">También puede usar las opciones de para guardar esta lista como archivo XML o como página HTML. De hecho, con los comandos de PowerShell adicionales, podría guardarlo directamente como archivo de Excel, con el formato personalizado que quiera.</span><span class="sxs-lookup"><span data-stu-id="adfd6-p131">You can also use options to save this list as an XML file or as an HTML page. In fact, with additional PowerShell commands, you could save it directly as an Excel file, with any custom formatting you desire.</span></span> 
  
<span data-ttu-id="adfd6-252">También puede enviar el resultado de un comando de PowerShell que muestra una lista directamente en la impresora predeterminada de Windows.</span><span class="sxs-lookup"><span data-stu-id="adfd6-252">You can also send the output of a PowerShell command that displays a list directly to the default printer in Windows.</span></span> <span data-ttu-id="adfd6-253">A continuación se muestra un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="adfd6-253">Here is an example command:</span></span>
  
```powershell
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Out-Printer
```

<span data-ttu-id="adfd6-254">Y este es el aspecto que tendrá el documento impreso:</span><span class="sxs-lookup"><span data-stu-id="adfd6-254">Here's what your printed document will look like:</span></span>
  
![Ejemplo de un documento impreso que fue el resultado de un comando de PowerShell que se muestra directamente en la impresora predeterminada de Windows.](media/o365-powershell-printed-data.png)
  
> [!TIP]
>  <span data-ttu-id="adfd6-256">La interpretación de este comando de PowerShell es la siguiente: obtener todos los usuarios de Skype empresarial online en la suscripción actual de Microsoft 365, obtener solo el nombre de usuario, el UPN y la ubicación y, a continuación, enviar la información a la impresora predeterminada de Windows ( **out-Printer** ).</span><span class="sxs-lookup"><span data-stu-id="adfd6-256">The interpretation of this PowerShell command is:  Get all of the Skype for Business Online users in the current Microsoft 365 subscription, obtain only the user name, UPN, and location, and then send that information to the default Windows printer ( **Out-Printer** ).</span></span>
  
<span data-ttu-id="adfd6-257">El documento impreso tiene el mismo formato sencillo que la visualización en la ventana de comandos de PowerShell, pero una vez que haya creado un comando de PowerShell para enumerar lo que necesita, solo tiene que agregar **| Fuera** de la impresora al final del comando para obtener una copia impresa desde la que trabajar.</span><span class="sxs-lookup"><span data-stu-id="adfd6-257">The printed document has the same simple formatting as the display within the PowerShell command window, but once you have created a PowerShell command to list what you need, you just add **| Out-Printer** to the end of the command to get a hard copy to work from.</span></span>
  
## <a name="powershell-for-microsoft-365-lets-you-manage-across-server-products"></a><span data-ttu-id="adfd6-258">PowerShell para Microsoft 365 le permite administrar los productos de servidor</span><span class="sxs-lookup"><span data-stu-id="adfd6-258">PowerShell for Microsoft 365 lets you manage across server products</span></span>

<span data-ttu-id="adfd6-259">Los diferentes componentes que componen Microsoft 365 están diseñados para trabajar juntos.</span><span class="sxs-lookup"><span data-stu-id="adfd6-259">The different components that make up Microsoft 365 are designed to work together.</span></span> <span data-ttu-id="adfd6-260">Por ejemplo, supongamos que agrega un nuevo usuario a Microsoft 365 y, cuando lo hace, especifica dicha información como el Departamento y el número de teléfono del usuario.</span><span class="sxs-lookup"><span data-stu-id="adfd6-260">For example, suppose you add a new user to Microsoft 365 and, when you do, you specify such information as the user's department and phone number.</span></span> <span data-ttu-id="adfd6-261">La información estará disponible si obtiene acceso a la información del usuario mediante cualquiera de los servicios de Microsoft 365: Skype empresarial online, Exchange o SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="adfd6-261">That information will then be available if you access the user's information using any of the Microsoft 365 services: Skype for Business Online, Exchange, or SharePoint Online.</span></span>
  
<span data-ttu-id="adfd6-p134">Pero eso es para la información habitual que abarca el conjunto de productos. La información específica del producto (por ejemplo, la información sobre el buzón de Exchange de un usuario) normalmente no está disponible en el conjunto de aplicaciones. Por ejemplo, para saber si el buzón de un usuario está o no habilitado, esa información solo está disponible en el Centro de administración de Exchange.</span><span class="sxs-lookup"><span data-stu-id="adfd6-p134">But that's for common information that spans the suite of products. Product-specific information-for example, information about a user's Exchange mailbox-is typically not available across the suite. For example, if you want to know if a user's mailbox is enabled or not, that information is available only in the Exchange Admin center.</span></span> 
  
<span data-ttu-id="adfd6-265">Suponga que quiere crear un informe que muestre la información siguiente de todos los usuarios:</span><span class="sxs-lookup"><span data-stu-id="adfd6-265">Suppose you'd like to make a report that shows the following information for all your users:</span></span>
  
- <span data-ttu-id="adfd6-266">El nombre para mostrar del usuario</span><span class="sxs-lookup"><span data-stu-id="adfd6-266">The user's display name</span></span>
    
- <span data-ttu-id="adfd6-267">Si el usuario tiene licencia para Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="adfd6-267">Whether the user is licensed for Microsoft 365</span></span>
    
- <span data-ttu-id="adfd6-268">Si el buzón de Exchange del usuario se ha habilitado</span><span class="sxs-lookup"><span data-stu-id="adfd6-268">Whether the user's Exchange mailbox has been enabled</span></span>
    
- <span data-ttu-id="adfd6-269">Si el usuario está habilitado en Skype Empresarial Online</span><span class="sxs-lookup"><span data-stu-id="adfd6-269">Whether the user is enabled for Skype for Business Online</span></span>
    
<span data-ttu-id="adfd6-270">Actualmente no puede usar el centro de administración de Microsoft 365 para crear un informe de este tipo fácilmente.</span><span class="sxs-lookup"><span data-stu-id="adfd6-270">You currently cannot use the Microsoft 365 admin center to easily produce such a report.</span></span> <span data-ttu-id="adfd6-271">En su lugar, tendrá que crear un documento independiente para almacenar la información, como una hoja de cálculo de Excel, y obtener todos los nombres de usuario e información de licencia del centro de administración de Microsoft 365, obtener información del buzón del centro de administración de Exchange, obtener información de Skype empresarial online del centro de administración de Skype empresarial online y, a continuación, intercalar y combinar dicha información</span><span class="sxs-lookup"><span data-stu-id="adfd6-271">Instead, you'll have to create a separate document to store the information, like an Excel worksheet, and get all the user names and licensing information from the Microsoft 365 admin center, get mailbox information from the Exchange Admin center, get Skype for Business Online information from the Skype for Business Online Admin center, and then collate and combine that information.</span></span>
  
<span data-ttu-id="adfd6-272">La alternativa es usar un script de PowerShell para compilar dicho informe.</span><span class="sxs-lookup"><span data-stu-id="adfd6-272">The alternative is to use a PowerShell script to compile that report for you.</span></span>
  
<span data-ttu-id="adfd6-273">El siguiente script de ejemplo es más complicado que los comandos que hasta ahora hemos visto en este artículo.</span><span class="sxs-lookup"><span data-stu-id="adfd6-273">The following example script is more complicated than the commands you have seen so far in this article.</span></span> <span data-ttu-id="adfd6-274">Sin embargo, se muestra el potencial de usar PowerShell para crear vistas de información que son muy difíciles de hacer en caso contrario.</span><span class="sxs-lookup"><span data-stu-id="adfd6-274">But, it shows the potential of using PowerShell to create views of information that are very difficult to do otherwise.</span></span> <span data-ttu-id="adfd6-275">Este es el script que puede compilar y mostrar la lista necesaria:</span><span class="sxs-lookup"><span data-stu-id="adfd6-275">Here is the script that can compile and display the needed list:</span></span>
  
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

<span data-ttu-id="adfd6-276">Este es un ejemplo del resultado:</span><span class="sxs-lookup"><span data-stu-id="adfd6-276">Here is an example of the display:</span></span>
  
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

<span data-ttu-id="adfd6-277">La interpretación de este script de PowerShell es la siguiente:</span><span class="sxs-lookup"><span data-stu-id="adfd6-277">The interpretation of this PowerShell script is:</span></span>  

- <span data-ttu-id="adfd6-278">Obtenga todos los usuarios de la suscripción actual de Microsoft 365 y almacene la información en una variable llamada $x ( **$x = Get-AzureADUser** ).</span><span class="sxs-lookup"><span data-stu-id="adfd6-278">Get all of the users in the current Microsoft 365 subscription and store the information in a variable named $x ( **$x = Get-AzureADUser** ).</span></span>
- <span data-ttu-id="adfd6-279">Se inicia un bucle que se ejecuta para todos los usuarios en la variable denominada $x (**foreach ($i in $x)**).</span><span class="sxs-lookup"><span data-stu-id="adfd6-279">Start a loop that runs over all the users in the variable named $x ( **foreach ($i in $x)** ).</span></span>  
- <span data-ttu-id="adfd6-280">Se define una variable denominada $y y se almacena la información del buzón de usuario en ella (**$y = Get-Mailbox -Identity $i.UserPrincipalName**).</span><span class="sxs-lookup"><span data-stu-id="adfd6-280">Define a variable named $y and store the user's mailbox information in it ( **$y = Get-Mailbox -Identity $i.UserPrincipalName** ).</span></span>
- <span data-ttu-id="adfd6-281">Se agrega una nueva propiedad a la información de usuario denominada IsMailBoxEnabled, que se establece en el valor de la propiedad IsMailBoxEnabled del buzón del usuario (**$i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled**).</span><span class="sxs-lookup"><span data-stu-id="adfd6-281">Add a new property to the user information named IsMailBoxEnabled and set it to the value of the IsMailBoxEnabled property of the user's mailbox ( **$i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled** ).</span></span>
- <span data-ttu-id="adfd6-282">Se define una variable denominada $y y se almacena la información de Skype Empresarial Online del usuario en ella (**$y = Get-CsOnlineUser -Identity $i.UserPrincipalName**).</span><span class="sxs-lookup"><span data-stu-id="adfd6-282">Define a variable named $y and store the user's Skype for Business Online information in it ( **$y = Get-CsOnlineUser -Identity $i.UserPrincipalName** ).</span></span>
- <span data-ttu-id="adfd6-283">Se agrega una nueva propiedad a la información de usuario denominada EnabledForSfB y esta se establece en el valor de la propiedad habilitada de la información de Skype Empresarial Online de usuario (**$i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled**).</span><span class="sxs-lookup"><span data-stu-id="adfd6-283">Add a new property to the user information named EnabledForSfB and set it to the value of the Enabled property of the user's Skype for Business Online information ( **$i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled** ).</span></span>
- <span data-ttu-id="adfd6-284">Se muestra la lista de usuarios, pero solo se incluyen el nombre de cada usuario, si tiene licencia y las dos nuevas propiedades que indican si el buzón está habilitado y si se habilitó para Skype Empresarial Online (**$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB**).</span><span class="sxs-lookup"><span data-stu-id="adfd6-284">Display the list of users, but include only their name, whether they are licensed, and the two new properties that indicate whether their mailbox is enabled and whether they are enabled for Skype for Business Online ( **$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB** ).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="adfd6-285">Consulte también</span><span class="sxs-lookup"><span data-stu-id="adfd6-285">See also</span></span>

[<span data-ttu-id="adfd6-286">Introducción a PowerShell para Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="adfd6-286">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="adfd6-287">Administración de cuentas de usuario, licencias y grupos de Microsoft 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="adfd6-287">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="adfd6-288">Usar Windows PowerShell para crear informes en Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="adfd6-288">Use Windows PowerShell to create reports in Microsoft 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)

