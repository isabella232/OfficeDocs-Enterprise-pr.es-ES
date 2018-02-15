---
title: Asignar licencias a cuentas de usuario con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
description: "Se explica cómo usar PowerShell de Office 365 para asignar una licencia de Office 365 a los usuarios sin licencia."
ms.openlocfilehash: 688e2775e7a028cd9dbe0c8ea27a7f3a453b5279
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="6fbc4-103">Asignar licencias a cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="6fbc4-103">Assign licenses to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="6fbc4-104">**Resumen:** se explica cómo usar PowerShell de Office 365 para asignar una licencia de Office 365 a los usuarios sin licencia.</span><span class="sxs-lookup"><span data-stu-id="6fbc4-104">**Summary:**  Explains how to use Office 365 PowerShell assign an Office 365 license to unlicensed users.</span></span>
  
<span data-ttu-id="6fbc4-p101">Es importante asignar licencias a las cuentas de usuario de Office 365, ya que los usuarios no pueden usar ningún servicio de Office 365 hasta que su cuenta tenga una licencia. Puede usar PowerShell de Office 365 para asignar de forma eficiente licencias a cuentas sin licencia, especialmente a varias cuentas.</span><span class="sxs-lookup"><span data-stu-id="6fbc4-p101">Licensing user accounts in Office 365 is important, because users can't use any Office 365 services until their account has been licensed. You can use Office 365 PowerShell to efficiently assign licenses to unlicensed accounts, especially multiple accounts.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="6fbc4-107">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="6fbc4-107">Before you begin</span></span>
<span data-ttu-id="6fbc4-108"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="6fbc4-108"><a name="RTT"> </a></span></span>

- <span data-ttu-id="6fbc4-p102">Los procedimientos de este tema requieren conectarse a PowerShell de Office 365. Para obtener instrucciones, vea [Conectarse a PowerShell de Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="6fbc4-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="6fbc4-p103">Use el cmdlet **Get-MsolAccountSku** para ver los planes de licencias disponibles y el número de licencias disponibles en cada plan de la organización. El número de licencias disponibles en cada plan es **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. Para obtener más información sobre los planes de licencias, las licencias y los servicios, vea [Ver licencias y servicios con PowerShell de Office 365](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="6fbc4-p103">Use the **Get-MsolAccountSku** cmdlet to view the available licensing plans and the number of available licenses in each plan in your organization. The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. For more information about licensing plans, licenses, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="6fbc4-114">Para buscar las cuentas sin licencia de la organización, ejecute el comando `Get-MsolUser -All -UnlicensedUsersOnly`.</span><span class="sxs-lookup"><span data-stu-id="6fbc4-114">To find the unlicensed accounts in your organization, run the command  `Get-MsolUser -All -UnlicensedUsersOnly`</span></span>
    
- <span data-ttu-id="6fbc4-p104">Solo puede asignar licencias a cuentas de usuario que tengan la propiedad **UsageLocation** establecida en un código de país ISO 3166-1 alpha-2 válido. Por ejemplo, “US” para Estados Unidos y “FR” para Francia. Algunos servicios de Office 365 no están disponibles en determinados países. Para obtener más información, vea [Sobre las restricciones de licencia](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span><span class="sxs-lookup"><span data-stu-id="6fbc4-p104">You can assign licenses only to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. Some Office 365 services aren't available in certain countries. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
    <span data-ttu-id="6fbc4-p105">Para buscar cuentas que no tengan un valor **UsageLocation**, ejecute el comando `Get-MsolUser -All | where {$_.UsageLocation -eq $null}`. Para establecer el valor **UsageLocation** en una cuenta, utilice la sintaxis `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`. Por ejemplo, `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`.</span><span class="sxs-lookup"><span data-stu-id="6fbc4-p105">To find accounts that don't have a **UsageLocation** value, run the command `Get-MsolUser -All | where {$_.UsageLocation -eq $null}`. To set the **UsageLocation** value on an account, use the syntax `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`. For example,  `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`.</span></span>
    
- <span data-ttu-id="6fbc4-122">Si usa el cmdlet **Get-MsolUser** sin el parámetro `-All`, solo se devuelven las 500 primeras cuentas.</span><span class="sxs-lookup"><span data-stu-id="6fbc4-122">If you use the **Get-MsolUser** cmdlet without using the `-All` parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="6fbc4-123">Versión corta (instrucciones sin explicaciones)</span><span class="sxs-lookup"><span data-stu-id="6fbc4-123">The short version (instructions without explanations)</span></span>
<span data-ttu-id="6fbc4-124"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="6fbc4-124"><a name="ShortVersion"> </a></span></span>

<span data-ttu-id="6fbc4-p106">En esta sección, se presentan los procedimientos sin explicaciones detalladas. Si tiene preguntas o quiere obtener más información, lea el resto del tema.</span><span class="sxs-lookup"><span data-stu-id="6fbc4-p106">This section presents the procedures without detailed explanation. If you have questions or want more information, you can read rest of the topic.</span></span>
  
<span data-ttu-id="6fbc4-127">Para asignar una licencia a un usuario, use la sintaxis siguiente en PowerShell de Office 365:</span><span class="sxs-lookup"><span data-stu-id="6fbc4-127">To assign a license to a user, use the following syntax in Office 365 PowerShell:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="6fbc4-128">En este ejemplo, se asigna una licencia desde el plan de licencias `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) al usuario sin licencia `belindan@litwareinc.com`.</span><span class="sxs-lookup"><span data-stu-id="6fbc4-128">This example assigns a license from the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan to the unlicensed user `belindan@litwareinc.com`.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="6fbc4-129">Para asignar una licencia a varios usuarios sin licencia, use la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="6fbc4-129">To assign a license to many unlicensed users, use the following syntax:</span></span>
  
```
$x = Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>]; $x | foreach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```

 <span data-ttu-id="6fbc4-130">**Notas**</span><span class="sxs-lookup"><span data-stu-id="6fbc4-130">**Notes**</span></span>
  
- <span data-ttu-id="6fbc4-131">No se pueden asignar varias licencias a un usuario desde el mismo plan de licencias.</span><span class="sxs-lookup"><span data-stu-id="6fbc4-131">You can't assign multiple licenses to a user from the same licensing plan.</span></span>
    
- <span data-ttu-id="6fbc4-132">Si no dispone de licencias suficientes, las licencias se asignan a los usuarios en el orden en que los devuelve el cmdlet **Get-MsolUser** hasta que se agoten las licencias disponibles.</span><span class="sxs-lookup"><span data-stu-id="6fbc4-132">If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
    
<span data-ttu-id="6fbc4-133">En este ejemplo, se asignan licencias desde el plan de licencias `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) a todos los usuarios sin licencia.</span><span class="sxs-lookup"><span data-stu-id="6fbc4-133">This example assigns licenses from the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan to all unlicensed users.</span></span>
  
```
$AllUn = Get-MsolUser -All -UnlicensedUsersOnly; $AllUn | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

<span data-ttu-id="6fbc4-134">En este ejemplo se asignan esas mismas licencias a los usuarios sin licencia del departamento de ventas de los Estados Unidos.</span><span class="sxs-lookup"><span data-stu-id="6fbc4-134">This example assigns those same licenses to unlicensed users in the Sales department in the United States.</span></span>
  
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly; $USSales | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="6fbc4-135">Versión larga (instrucciones con explicaciones detalladas)</span><span class="sxs-lookup"><span data-stu-id="6fbc4-135">The long version (instructions with detailed explanations)</span></span>
<span data-ttu-id="6fbc4-136"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="6fbc4-136"><a name="LongVersion"> </a></span></span>

<span data-ttu-id="6fbc4-p107">Tal y como se explica en el artículo [Ver los usuarios con licencia y sin licencia con PowerShell de Office 365](view-licensed-and-unlicensed-users-with-office-365-powershell.md), se puede dar la situación de tener usuarios con cuentas de usuario de Office 365 válidas, pero para los que no se haya emitido una licencia de Office 365. Esto quiere decir que, con cuenta válida o sin ella, estos usuarios no podrán iniciar sesión en Office 365. Y, si no pueden iniciar sesión, tampoco podrán disfrutar de ninguno de los servicios de Office 365.</span><span class="sxs-lookup"><span data-stu-id="6fbc4-p107">As noted in the article [View licensed and unlicensed users with Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md), it's possible to have users who have valid Office 365 user accounts, but who have not been issued an Office 365 license. That means that, valid account or no valid account, those users will not be able to log on to Office 365. And if you can't log on, you can't take advantage of any Office 365 services.</span></span>
  
<span data-ttu-id="6fbc4-140">El citado artículo también señala que podemos devolver una lista de cuentas de usuario sin licencia mediante la ejecución de este comando:</span><span class="sxs-lookup"><span data-stu-id="6fbc4-140">The aforementioned article also noted that we can return a list of unlicensed user accounts by running this command:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="6fbc4-141">Este comando devuelve información sobre qué usuarios se encuentran actualmente sin licencia de Office 365:</span><span class="sxs-lookup"><span data-stu-id="6fbc4-141">That command returns information about any users who are not currently licensed for Office 365:</span></span>
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  False
```

<span data-ttu-id="6fbc4-p108">Como puede ver, tenemos un usuario sin licencia: Belinda Newman. ¿Cómo asignamos a Belinda una licencia de Office 365?</span><span class="sxs-lookup"><span data-stu-id="6fbc4-p108">As you can see, we have one unlicensed user: Belinda Newman. So how do we go about assigning Belinda an Office 365 license?</span></span>
  
<span data-ttu-id="6fbc4-144">Para empezar, ejecutaremos el cmdlet **Get-MsolAccountSku**, que se describe en el artículo [Ver licencias y servicios con PowerShell de Office 365](view-licenses-and-services-with-office-365-powershell.md):</span><span class="sxs-lookup"><span data-stu-id="6fbc4-144">For starters, we're going to run the **Get-MsolAccountSku** cmdlet discussed in the article [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md):</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="6fbc4-145">El comando devuelve unos datos similares a estos:</span><span class="sxs-lookup"><span data-stu-id="6fbc4-145">That command returns data similar to this:</span></span>
  
```
AccountSkuId               ActiveUnits    WarningUnits   ConsumedUnits
------------               -----------    ------------   -------------
litwareinc:ENTERPRISEPACK  25             0              24
```

<span data-ttu-id="6fbc4-p109">¿Por qué hemos ejecutado **Get-MsolAccountSku**? (“Sku”, en caso de que se lo esté preguntando, es la abreviatura en inglés de “referencia de almacén”. Para nuestros fines, es jerga comercial de “producto”). La ejecución de **Get-MsolAccountSku** responde a dos motivos. En primer lugar, debemos asegurarnos de que disponemos de una licencia para asignar a Belinda. ¿Tenemos licencias disponibles para asignar? Para averiguarlo, tomamos el valor de la propiedad **ActiveUnits** (25) y le restamos los valores de las propiedades **WarningUnits** (0) y **ConsumedUnits** (24):</span><span class="sxs-lookup"><span data-stu-id="6fbc4-p109">Why did we run **Get-MsolAccountSku** ? ("Sku," in case you're wondering, is short for "stock-keeping unit." For our purposes, that's just business-speak for "product.") There are two reasons why we ran **Get-MsolAccountSku**. First, we need to make sure we actually have a license to assign Belinda. Do we have any licenses we can assign her? To determine that, we take the value of **ActiveUnits** property (25) and subtract the values of the **WarningUnits** (0) and **ConsumedUnits** (24) properties:</span></span>
  
 `25 - 0 - 24 = 1`
  
<span data-ttu-id="6fbc4-p110">La propiedad **ActiveUnits** nos dice cuántas licencias hemos adquirido, y el valor combinado de **WarningUnits** y **ConsumedUnits** nos indica cuántas licencias están en uso actualmente. Si restamos el número de licencias asignadas al número de licencias adquiridas, sabremos cuántas licencias siguen estando disponibles. Por suerte, tenemos una licencia disponible para su distribución:</span><span class="sxs-lookup"><span data-stu-id="6fbc4-p110">The **ActiveUnits** property tells us how many licenses we've purchased, and the combined value of **WarningUnits** and **ConsumedUnits** tells us how many licenses are currently in use. If we subtract the number of licenses already spoken for from the number of licenses we purchased, we'll know how many licenses are still available. As luck would have it, we have one license available for distribution:</span></span>
  
 `25 - 0 - 24 = 1`
  
<span data-ttu-id="6fbc4-p111">En segundo lugar, para poder asignar una nueva licencia a Belinda, necesitamos saber el nombre de nuestro plan de licencias (es decir, necesitamos conocer el **AccountSkuId**). En este caso, es fácil: solo tenemos un único plan de licencias (`litwareinc:ENTERPRISEPACK`). Sin embargo, tenga en cuenta que una organización puede tener varios planes de licencias. En ese caso, **Get-MsolAccountSku** devuelve dos **AccountSkuIds** diferentes, y tendrá que elegir el plan de licencias correspondiente al asignar licencias. Por ahora, sin embargo, vamos a seguir con el caso más sencillo y suponer que hay un solo plan de licencias.</span><span class="sxs-lookup"><span data-stu-id="6fbc4-p111">Second, in order to assign Belinda a new license we need to know the name of our licensing plan (that is, we need to know the **AccountSkuId** ). In this case, that's easy: we only have a single licensing plan ( `litwareinc:ENTERPRISEPACK`). Note, however, that it's possible for an organization to have multiple licensing plans. In that case, **Get-MsolAccountSku** would return two different **AccountSkuIds**, and you would need to pick the appropriate licensing plan when assigning licenses. For now, though, we're going to stick with the simplest case, and assume we have just one licensing plan.</span></span>
  
<span data-ttu-id="6fbc4-p112">Entonces, *¿cómo* asignamos a Belinda Newman una nueva licencia? Así:</span><span class="sxs-lookup"><span data-stu-id="6fbc4-p112">So then how  *do*  we assign Belinda Newman a new license? Like this:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "BelindaN@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="6fbc4-162">Esto es lo que tiene que hacer: simplemente llame al cmdlet **Set-MsolUserLicense**, asegurándose de especificar el parámetro _UserPrincipalName_ para el usuario y el plan de licencias correspondiente.</span><span class="sxs-lookup"><span data-stu-id="6fbc4-162">That's also you have to do: just call the **Set-MsolUserLicense** cmdlet, making sure that you specify the _UserPrincipalName_ parameter for the user and the appropriate licensing plan.</span></span>
  
<span data-ttu-id="6fbc4-163">Cuando **Set-MsolUserLicense** termine de ejecutarse, verá algo parecido a esto en la pantalla:</span><span class="sxs-lookup"><span data-stu-id="6fbc4-163">When **Set-MsolUserLicense** finishes running, you'll see something similar to this onscreen:</span></span>
  
 `PS C:\\windows\\system32>`
  
<span data-ttu-id="6fbc4-p113">En otras palabras, parecerá que no sucedió nada. Para comprobar que se asignó una licencia al usuario, ejecute un comando como el siguiente:</span><span class="sxs-lookup"><span data-stu-id="6fbc4-p113">In other words, it won't look like anything has happened. To verify that the user has been assigned a license, run a command like the following:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.com"
```

<span data-ttu-id="6fbc4-166">Si todo funcionó como se esperaba, debería ver que la propiedad isLicensed de Belinda ahora se establece en “true”:</span><span class="sxs-lookup"><span data-stu-id="6fbc4-166">If everything worked as expected, you should see that Belinda's isLicensed property is now set to True:</span></span>
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  True
```

> [!SECURITY NOTE]<span data-ttu-id="6fbc4-p114"> Y ahora una buena pregunta: ¿qué pasa si comete un error e intenta asignar una licencia a un usuario que ya tiene una? ¿Acabará concediendo dos licencias a un solo usuario? > ¿La respuesta rápida? No; Office 365 no le permitirá asignar más de una licencia al mismo usuario. (Es decir, no le permitirá asignar más de una licencia del mismo plan de licencias). Si intenta hacerlo, se producirá un error en el comando con el siguiente mensaje de error: > `Set-MsolUserLicense : Unable to assign this license because it is invalid. Use the Get-MsolAccountSku cmdlet to retrieve a list of valid licenses.` > Ciertamente, ese mensaje de error es un poco engañoso: no es que la licencia no sea válida, es que se asignó a un usuario que ya *tiene* una licencia. Pero, dejando de lado el mensaje de error, lo importante es que un usuario no acabe con varias licencias.</span><span class="sxs-lookup"><span data-stu-id="6fbc4-p114"> Good question: what if you made a mistake and tried to assign a license to a user who already has a license? Will you end up giving two licenses to a single user? > The quick answer? No; Office 365 won't let you assign more than one license to the same user. (Well, more than one license from the same licensing plan, that is.) If you try to do that your command will fail with the following error message: >  `Set-MsolUserLicense : Unable to assign this license because it is invalid. Use the Get-MsolAccountSku cmdlet to retrieve a list of valid licenses.`> Admittedly, that error message is a tiny bit misleading: the license isn't really invalid, it's just being assigned to a user who already  *has*  a license. But, error message aside, the important thing is that one user won't end up with multiple licenses.</span></span>
  
<span data-ttu-id="6fbc4-p115">Como ha visto, es muy fácil usar PowerShell de Office 365 para asignar una única licencia a un único usuario. Y esto nos lleva a una pregunta obvia: ¿no sería igual de fácil, o quizás aún más fácil, usar el Centro de administración de Office 365 para asignar una única licencia a un único usuario? Bueno, quizá; eso depende, en parte, de si se siente más cómodo usando Windows PowerShell o usando el Centro de administración de Office 365. Sin embargo, donde Windows PowerShell realmente destaca es cuando hay que asignar varias licencias a varios usuarios. Por ejemplo, este comando asigna una licencia de Office 365 a cualquiera de los usuarios que aún no tienen una licencia:</span><span class="sxs-lookup"><span data-stu-id="6fbc4-p115">As you've just seen, it's very easy to use Office 365 PowerShell to assign a single license to a single user. And that leads to an obvious question: wouldn't it be just as easy, maybe even easier, to use the Office 365 admin center to assign a single license to a single user? Well, maybe; that depends, in part, on whether you're more comfortable using Windows PowerShell or more comfortable using the Office 365 admin center. Where Windows PowerShell really shines, however, is when you need to assign multiple licenses to multiple users. For example, this command assigns an Office 365 license to any of your users that don't already have a license:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="6fbc4-p116">En el comando anterior, usamos **Get-MsolUser** y el parámetro _UnlicensedUsersOnly_ para devolver una colección de todas las cuentas de usuario sin licencia. Después pasamos esa colección al cmdlet **Set-MsolUserLicense**. A su vez, **Set-MsolUserLicense** asigna una licencia (tomada del plan de licencias de `litwareinc:ENTERPRISEPACK`) a cada usuario de la colección.</span><span class="sxs-lookup"><span data-stu-id="6fbc4-p116">In the preceding command, we use **Get-MsolUser** and the _UnlicensedUsersOnly_ parameter to return a collection of all the unlicensed user accounts. We then pass that collection to the **Set-MsolUserLicense** cmdlet; in turn, **Set-MsolUserLicense** assigns a license (taken from the `litwareinc:ENTERPRISEPACK` licensing plan) to each user in the collection.</span></span>
  
<span data-ttu-id="6fbc4-p117">Pero ¿qué sucede si tiene 5 usuarios sin licencia y solo una licencia disponible? En ese caso, **Set-MsolUserLicense** concederá la licencia disponible al primer usuario devuelto por **Get-MsolUser**. **Set-MsolUserLicense** intentará diligentemente asignar una licencia a los otros cuatro usuarios, pero los cuatro intentos generarán un error junto con el siguiente mensaje:</span><span class="sxs-lookup"><span data-stu-id="6fbc4-p117">Ah, but what if you have 5 unlicensed users but only one available license? In that case **Set-MsolUserLicense** will give the available license to the first user returned by **Get-MsolUser**. **Set-MsolUserLicense** will then dutifully try to assign a license to the other four users, but all four of those attempts will fail along with the following error message:</span></span>
  
 `Set-MsolUserLicense : Unable to assign this license because the number of allowed licenses have been assigned.`
  
<span data-ttu-id="6fbc4-p118">En otras palabras, el cmdlet MsolUserLicense no solo fallará ahí. Intentará asignar tantas licencias como sea posible. Será entonces cuando se produzca el error.</span><span class="sxs-lookup"><span data-stu-id="6fbc4-p118">In other words, Set-MsolUserLicense won't just fail. Instead, it will assign as many licenses as it can. Only then will it fail.</span></span>
  
<span data-ttu-id="6fbc4-p119">Vamos a poner otro ejemplo. Supongamos que quiere asignar una licencia a todos los usuarios del departamento de ventas. Pan comido:</span><span class="sxs-lookup"><span data-stu-id="6fbc4-p119">Let's try another example. Maybe you'd like to assign a license to all the users in the Sales department. No problem:</span></span>
  
```
Get-MsolUser -All -Department "Sales" | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="6fbc4-189">O bien, si realmente quiere ponerse sofisticado, y quiere mantener los mensajes de error y el procesamiento informático al mínimo, limítese a asignar una licencia a los usuarios sin licencia del departamento de ventas:</span><span class="sxs-lookup"><span data-stu-id="6fbc4-189">Or, if you want to get really fancy, and if you want to keep error messages and computing processing to a minimum, just assigned a license to unlicensed users from the Sales department:</span></span>
  
```
Get-MsolUser -All -Department "Sales" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="6fbc4-p120">Después de todo, no tiene ningún sentido tratar de conceder licencias a los usuarios que ya disponen de una. Como ya hemos visto, no funcionará.</span><span class="sxs-lookup"><span data-stu-id="6fbc4-p120">After all, there's no point trying to license users who already have a license. As we've already seen, that won't work.</span></span>
  
<span data-ttu-id="6fbc4-p121">Este es otro ejemplo. Tal vez le gustaría conceder licencias a todos los usuarios de EE. UU. que actualmente no cuentan con una licencia de Office 365. En ese caso:</span><span class="sxs-lookup"><span data-stu-id="6fbc4-p121">Here's another example. Maybe you'd like to license all the US users who don't currently have an Office 365 license. In that case:</span></span>
  
```
Get-MsolUser -All -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="6fbc4-195">Y así sucesivamente.</span><span class="sxs-lookup"><span data-stu-id="6fbc4-195">And so on and so on.</span></span>
  
> [!NOTE]
> <span data-ttu-id="6fbc4-p122">¿Cuánto tiempo se necesita para ejecutar un comando que, por ejemplo, emita licencias para todos los usuarios sin licencia? Es difícil de responder: depende de todo, desde el número de usuarios que tenga hasta la velocidad de la conexión de red. Si tiene que conceder licencias a unos cientos de usuarios, será razonablemente rápido (es decir, no debería tardar más de uno o dos minutos). Si tiene que conceder licencias a 10 000 usuarios, obviamente tardará un poco más. Pero no tardaría tanto tiempo como en el caso de querer asignar licencias a 10 000 usuarios mediante el Centro de administración de Office 365.</span><span class="sxs-lookup"><span data-stu-id="6fbc4-p122">How long does it take to run a command that, say, issues licenses to all your unlicensed users? That's difficult to say: it depends on everything from the number of users you have to the speed of your network connection. If you have a couple hundred users to license this will go reasonably quickly (that is, it shouldn't take more than a minute or two). If you have 10,000 users to license it will obviously take a little longer. But nowhere near as long as it would take to assign licenses to 10,000 users by using the Office 365 admin center.</span></span> 
  
<span data-ttu-id="6fbc4-p123">Y, ya que estamos tratando este asunto, es importante resaltar algo con lo que debemos tener cuidado al asignar licencias: si un usuario no tiene un valor configurado para la propiedad **UsageLocation**, no podrá asignarle a dicho usuario una licencia de Office 365. En su lugar, recibirá un mensaje de error similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="6fbc4-p123">As long as we're on the subject, here's something you need to watch out for when assigning licenses: if a user does not have a value configured for the **UsageLocation** property you won't be able to assign that user an Office 365 license. Instead, you'll get an error message similar to this:</span></span>
  
 `Set-MsolUserLicense : You must provide a required property: Parameter name: UsageLocation`
  
<span data-ttu-id="6fbc4-p124">De una manera un poco indirecta, este mensaje de error indica que el usuario en cuestión no tiene asignada la propiedad **UsageLocation**. Como habrá adivinado, la propiedad **UsageLocation** (que indica la región o el país en el que el usuario suele usar Office 365) es extremadamente importante. ¿Por qué? Porque los servicios disponibles para un usuario dependen no solo del paquete de licencias que haya adquirido, sino también del lugar en el que viva el usuario. Debido a reglas y normativas locales, algunos servicios tal vez no estén disponibles para algunos usuarios. Si un usuario no tiene **UsageLocation**, Office 365 no tiene manera de saber qué servicios pueden exponerse legalmente a dicho usuario. Por lo tanto, Office 365 no puede ofrecer servicios a dicho usuario, al menos no hasta que se haya especificado la propiedad **UsageLocation**.</span><span class="sxs-lookup"><span data-stu-id="6fbc4-p124">In somewhat-roundabout fashion, this error message tells us that the user in question has not been assigned a **UsageLocation**. As you might have guessed, the **UsageLocation** property (which indicates the region or country where the user typically uses Office 365) is extremely important. Why? That's because the services available to a user depend not only on the licensing pack that you purchased but also on where the user lives: due to local rules and regulations, some services might not be available to some users. If a user doesn't have a **UsageLocation**, Office 365 has no way of knowing which services can legally be exposed to that user. Therefore, Office 365 can't offer any services to that user, at least not until the **UsageLocation** has been specified.</span></span>
  
> [!NOTE]
> <span data-ttu-id="6fbc4-p125">Al configurar una cuenta de usuario, sabrá inmediatamente si hay restricciones de licencia asociadas a una parte determinada del mundo. Por ejemplo, si cambia la propiedad **UsageLocation** de un usuario con licencia a Irán (`IR`), se producirá un error en el comando con este mensaje de error: `Set-MsolUser : Unable to update license for this user. One or more of the assigned service plans is not available in this user's country. Prohibited Service Plans: EXCHANGE_S_ENTERPRISE, SHAREPOINTENTERPRISE, SHAREPOINTWAC, MCOSTANDARD, OFFICESUBSCRIPTION, RMS_S_ENTERPRISE. Specific service plans can be disabled for a user by using the licenseoptions parameter.` > Esto se debe a que Office 365 no está disponible actualmente para los usuarios de Irán. Para obtener más información, vea [Sobre las restricciones de licencia](https://go.microsoft.com/fwlink/p/?LinkId=691730). Por cierto, Office 365 usa los códigos de país de dos letras producidos por la Organización Internacional de Normalización (ISO). Encontrará dichos códigos en el [sitio web de ISO](https://go.microsoft.com/fwlink/p/?LinkId=84073).</span><span class="sxs-lookup"><span data-stu-id="6fbc4-p125">When you configure a user account you'll know immediately if there are any license restrictions associated with the specified part of the world. For example, if you change the **UsageLocation** for a licensed user to Iran ( `IR`), the command will fail with this error message: `Set-MsolUser : Unable to update license for this user. One or more of the assigned service plans is not available in this user's country. Prohibited Service Plans: EXCHANGE_S_ENTERPRISE, SHAREPOINTENTERPRISE, SHAREPOINTWAC, MCOSTANDARD, OFFICESUBSCRIPTION, RMS_S_ENTERPRISE. Specific service plans can be disabled for a user by using the licenseoptions parameter.`> That's because Office 365 is not currently available to users in Iran. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730). Incidentally, Office 365 uses the two-letter country codes produced by the International Organization for Standardization (ISO). You can find those codes on the [ISO web site](https://go.microsoft.com/fwlink/p/?LinkId=84073).</span></span> 
  
<span data-ttu-id="6fbc4-214">Si quiere comprobar si un usuario determinado tiene una propiedad **UsageLocation**, puede usar un comando similar a este:</span><span class="sxs-lookup"><span data-stu-id="6fbc4-214">If you want to verify that a given user has a **UsageLocation** you can use a command similar to this one:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.com" | Select-Object UsageLocation
```

<span data-ttu-id="6fbc4-215">Como alternativa, puede devolver una lista de todos los usuarios que no tienen una propiedad **UsageLocation** con este comando:</span><span class="sxs-lookup"><span data-stu-id="6fbc4-215">Alternatively, you can return a list of all the users who don't have a **UsageLocation** by using this command:</span></span>
  
```
Get-MsolUser -All | Where-Object {$_.UsageLocation -eq $null}
```

> [!NOTE]
> <span data-ttu-id="6fbc4-p126">Al asignar una licencia a un usuario, este tendrá acceso de forma predeterminada a todos los servicios de Office 365 a los que tenga acceso la organización. Por ejemplo, si compró licencias de Office 365 Enterprise E3, el usuario al que asignó la licencia tendrá acceso de forma automática a servicios como Exchange Online, Skype Empresarial Online y SharePoint Online. Si prefiere limitar el acceso de un usuario a dichos servicios (por ejemplo, que tenga acceso a SharePoint Online, pero *no* a Exchange Online ni Skype Empresarial Online), vea el artículo [Deshabilitar el acceso a servicios con PowerShell de Office 365](disable-access-to-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="6fbc4-p126">When you assign a license to a user that user will, by default, be given access to all the Office 365 services that your organization has access to. For example, if you purchased licenses for Office 365 Enterprise E3, your newly-licensed user will automatically be granted access to services like Exchange Online, Skype for Business Online, and SharePoint Online. If you would prefer to limit a user's access to those services (for example, you might want a user to have access to SharePoint Online but  *not*  to Exchange Online and Skype for Business Online) then see the article [Disable access to services with Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md).</span></span> 
  
## <a name="new-to-office-365"></a><span data-ttu-id="6fbc4-219">¿Es la primera vez que usa Office 365?</span><span class="sxs-lookup"><span data-stu-id="6fbc4-219">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="6fbc4-220">Vea también</span><span class="sxs-lookup"><span data-stu-id="6fbc4-220">See Also</span></span>
<span data-ttu-id="6fbc4-221"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="6fbc4-221"><a name="SeeAlso"> </a></span></span>

<span data-ttu-id="6fbc4-222">Vea los siguientes temas adicionales acerca de cómo administrar usuarios con Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="6fbc4-222">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="6fbc4-223">Crear cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="6fbc4-223">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="6fbc4-224">Eliminar y restaurar cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="6fbc4-224">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="6fbc4-225">Bloquear cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="6fbc4-225">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="6fbc4-226">Eliminar licencias de cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="6fbc4-226">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="6fbc4-227">Para obtener más información sobre los cmdlets que se usan en estos procedimientos, consulte los siguientes temas:</span><span class="sxs-lookup"><span data-stu-id="6fbc4-227">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="6fbc4-228">Get-MsolAccountSku</span><span class="sxs-lookup"><span data-stu-id="6fbc4-228">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [<span data-ttu-id="6fbc4-229">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="6fbc4-229">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="6fbc4-230">Set-MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="6fbc4-230">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="6fbc4-231">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="6fbc4-231">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="6fbc4-232">Select-Object</span><span class="sxs-lookup"><span data-stu-id="6fbc4-232">Select-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [<span data-ttu-id="6fbc4-233">Where-Object</span><span class="sxs-lookup"><span data-stu-id="6fbc4-233">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

