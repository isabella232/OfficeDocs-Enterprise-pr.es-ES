---
title: Asignar directivas de Skype empresarial online por usuario con PowerShell para Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/16/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.assetid: 36743c86-46c2-46be-b9ed-ad9d4e85d186
description: 'Resumen: Use PowerShell para Microsoft 365 para asignar configuraciones de comunicación por usuario con directivas de Skype empresarial online.'
ms.openlocfilehash: a5850c24f991161ec1de817d5b3f5037e9526767
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606466"
---
# <a name="assign-per-user-skype-for-business-online-policies-with-powershell-for-microsoft-365"></a><span data-ttu-id="e4ed3-103">Asignar directivas de Skype empresarial online por usuario con PowerShell para Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="e4ed3-103">Assign per-user Skype for Business Online policies with PowerShell for Microsoft 365</span></span>

<span data-ttu-id="e4ed3-104">*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="e4ed3-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="e4ed3-105">El uso de PowerShell para Microsoft 365 es una forma eficaz de asignar configuraciones de comunicación por usuario con directivas de Skype empresarial online.</span><span class="sxs-lookup"><span data-stu-id="e4ed3-105">Using PowerShell for Microsoft 365 is an efficient way to assign per-user communication settings with Skype for Business Online policies.</span></span>
  
## <a name="prepare-to-run-the-powershell-commands"></a><span data-ttu-id="e4ed3-106">Preparar la ejecución de los comandos de PowerShell</span><span class="sxs-lookup"><span data-stu-id="e4ed3-106">Prepare to run the PowerShell commands</span></span>

<span data-ttu-id="e4ed3-107">Siga estas instrucciones para preparar la ejecución de los comandos (omita los pasos que ya ha completado):</span><span class="sxs-lookup"><span data-stu-id="e4ed3-107">Use these instructions to get set up to run the commands (skip the steps you have already completed):</span></span>
  
1. <span data-ttu-id="e4ed3-108">Descargue e instale el [módulo de conector de Skype empresarial online](https://www.microsoft.com/download/details.aspx?id=39366).</span><span class="sxs-lookup"><span data-stu-id="e4ed3-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/download/details.aspx?id=39366).</span></span>
    
2. <span data-ttu-id="e4ed3-109">Abra el símbolo del sistema de Windows PowerShell y ejecute los siguientes comandos:</span><span class="sxs-lookup"><span data-stu-id="e4ed3-109">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
```powershell
Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
```

<span data-ttu-id="e4ed3-110">Cuando se le solicite, escriba el nombre y la contraseña de la cuenta de administrador en línea de Skype empresarial online.</span><span class="sxs-lookup"><span data-stu-id="e4ed3-110">When prompted, enter your Skype for Business Online administrator account name and password.</span></span>
    
## <a name="updating-external-communication-settings-for-a-user-account"></a><span data-ttu-id="e4ed3-111">Actualización de la configuración de comunicación externa para una cuenta de usuario</span><span class="sxs-lookup"><span data-stu-id="e4ed3-111">Updating external communication settings for a user account</span></span>

<span data-ttu-id="e4ed3-112">Supongamos que desea cambiar la configuración de comunicación externa en una cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="e4ed3-112">Suppose you want to change external communication settings on a user account.</span></span> <span data-ttu-id="e4ed3-113">Por ejemplo, desea permitir que Alex se comunique con los usuarios federados (EnableFederationAccess es igual a true) pero no con los usuarios de Windows Live (EnablePublicCloudAccess es igual a false).</span><span class="sxs-lookup"><span data-stu-id="e4ed3-113">For example, you want to allow Alex to communicate with federated users (EnableFederationAccess is equal to True) but not with Windows Live users (EnablePublicCloudAccess equals False).</span></span> <span data-ttu-id="e4ed3-114">Para ello, debe hacer dos cosas:</span><span class="sxs-lookup"><span data-stu-id="e4ed3-114">To do that, you need to do two things:</span></span>
  
1. <span data-ttu-id="e4ed3-115">Buscar una directiva de acceso externo que cumpla nuestros criterios.</span><span class="sxs-lookup"><span data-stu-id="e4ed3-115">Find an external access policy that meets our criteria.</span></span>
    
2. <span data-ttu-id="e4ed3-116">Asignar esa directiva de acceso externo a Alex.</span><span class="sxs-lookup"><span data-stu-id="e4ed3-116">Assign that external access policy to Alex.</span></span>
    
<span data-ttu-id="e4ed3-117">¿Cómo se determina qué directiva de acceso externo se asigna a Alex?</span><span class="sxs-lookup"><span data-stu-id="e4ed3-117">How do you determine which external access policy to assign Alex?</span></span> <span data-ttu-id="e4ed3-118">El siguiente comando devuelve todas las directivas de acceso externo donde EnableFederationAccess se establece en True y EnablePublicCloudAccess se establece en False:</span><span class="sxs-lookup"><span data-stu-id="e4ed3-118">The following command returns all the external access policies where EnableFederationAccess is set to True and EnablePublicCloudAccess is set to False:</span></span>
  
```powershell
Get-CsExternalAccessPolicy -Include All| Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $False}
```

<span data-ttu-id="e4ed3-119">A menos que haya creado instancias personalizadas de ExternalAccessPolicy, el comando devolverá una directiva que cumpla nuestros criterios (FederationOnly).</span><span class="sxs-lookup"><span data-stu-id="e4ed3-119">Unless you have created any custom instances of ExternalAccessPolicy, that command returns one policy that meets our criteria (FederationOnly).</span></span> <span data-ttu-id="e4ed3-120">Aquí le mostramos un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="e4ed3-120">Here is an example:</span></span>
  
```powershell
Identity                          : Tag:FederationOnly
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : False
EnablePublicCloudAudioVideoAccess : False
EnableOutsideAccess               : True
```

<span data-ttu-id="e4ed3-121">Ahora que ya sabe qué directiva asignar a Alex, podemos asignar esa Directiva mediante el cmdlet [Grant-CsExternalAccessPolicy](https://go.microsoft.com/fwlink/?LinkId=523974) .</span><span class="sxs-lookup"><span data-stu-id="e4ed3-121">Now that you know which policy to assign to Alex, we can assign that policy by using the [Grant-CsExternalAccessPolicy](https://go.microsoft.com/fwlink/?LinkId=523974) cmdlet.</span></span> <span data-ttu-id="e4ed3-122">Aquí le mostramos un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="e4ed3-122">Here is an example:</span></span>
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName "FederationOnly"
```

<span data-ttu-id="e4ed3-123">La asignación de una directiva es muy sencilla: simplemente especifique la identidad del usuario y el nombre de la Directiva que se va a asignar.</span><span class="sxs-lookup"><span data-stu-id="e4ed3-123">Assigning a policy is pretty simple: you simply specify the Identity of the user and the name of the policy to be assigned.</span></span> 
  
<span data-ttu-id="e4ed3-124">En lo que se refiere a las directivas y asignaciones de directivas, no se limita a trabajar con cuentas de usuario una vez.</span><span class="sxs-lookup"><span data-stu-id="e4ed3-124">And when it comes to policies and policy assignments, you're not limited to working with user accounts one a time.</span></span> <span data-ttu-id="e4ed3-125">Por ejemplo, supongamos que necesita una lista de todos los usuarios que tienen permiso para comunicarse con los socios federados y los usuarios de Windows Live.</span><span class="sxs-lookup"><span data-stu-id="e4ed3-125">For example, suppose you need a list of all the users who are allowed to communicate with federated partners and with Windows Live users.</span></span> <span data-ttu-id="e4ed3-126">Ya sabemos que a esos usuarios se les ha asignado la directiva de acceso de usuario externo FederationAndPICDefault.</span><span class="sxs-lookup"><span data-stu-id="e4ed3-126">We already know that those users have been assigned the external user access policy FederationAndPICDefault.</span></span> <span data-ttu-id="e4ed3-127">Como sabemos, puede mostrar una lista de todos los usuarios mediante la ejecución de un comando sencillo.</span><span class="sxs-lookup"><span data-stu-id="e4ed3-127">Because we know that, you can display a list of all those users by running one simple command.</span></span> <span data-ttu-id="e4ed3-128">Este es el comando:</span><span class="sxs-lookup"><span data-stu-id="e4ed3-128">Here is the command:</span></span>
  
```powershell
Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "FederationAndPICDefault"} | Select-Object DisplayName
```

<span data-ttu-id="e4ed3-129">En otras palabras, veremos a todos los usuarios donde la propiedad ExternalAccessPolicy se establece en FederationAndPICDefault.</span><span class="sxs-lookup"><span data-stu-id="e4ed3-129">In other words, show us all the users where the ExternalAccessPolicy property is set to FederationAndPICDefault.</span></span> <span data-ttu-id="e4ed3-130">(Y, para limitar la cantidad de información que aparece en la pantalla, use el cmdlet Select-Object para mostrar solo el nombre para mostrar de cada usuario).</span><span class="sxs-lookup"><span data-stu-id="e4ed3-130">(And, in order to limit the amount of information that appears onscreen, use the Select-Object cmdlet to display show us only each user's display name.)</span></span> 
  
<span data-ttu-id="e4ed3-131">Para configurar todas las cuentas de usuario para que usen la misma directiva, use este comando:</span><span class="sxs-lookup"><span data-stu-id="e4ed3-131">To configure all our user accounts to use that same policy, use this command:</span></span>
  
```powershell
Get-CsOnlineUser | Grant-CsExternalAccessPolicy "FederationAndPICDefault"
```

<span data-ttu-id="e4ed3-132">Este comando usa Get-CsOnlineUser para devolver una colección de todos los usuarios que se han habilitado para Lync y, a continuación, envía toda la información a Grant-CsExternalAccessPolicy, que asigna la Directiva FederationAndPICDefault a todos y cada uno de los usuarios de la colección.</span><span class="sxs-lookup"><span data-stu-id="e4ed3-132">This command uses Get-CsOnlineUser to return a collection of all the users who have been enabled for Lync, then sends all that information to Grant-CsExternalAccessPolicy, which assigns the FederationAndPICDefault policy to each and every user in the collection.</span></span>
  
<span data-ttu-id="e4ed3-133">Por ejemplo, supongamos que anteriormente ha asignado a Alex la Directiva FederationAndPICDefault y que ahora ha cambiado de opinión y desea que se administre mediante la directiva global de acceso externo.</span><span class="sxs-lookup"><span data-stu-id="e4ed3-133">As an additional example, suppose you've previously assigned Alex the FederationAndPICDefault policy and now you've changed your mind and would like him to be managed by the global external access policy.</span></span> <span data-ttu-id="e4ed3-134">No se puede asignar explícitamente la directiva global a nadie.</span><span class="sxs-lookup"><span data-stu-id="e4ed3-134">You can't explicitly assign the global policy to anyone.</span></span> <span data-ttu-id="e4ed3-135">En su lugar, se usa la directiva global para un usuario determinado si no hay una directiva por usuario asignada al usuario.</span><span class="sxs-lookup"><span data-stu-id="e4ed3-135">Instead, the global policy is used for a given user if no per-user policy is assigned to that user.</span></span> <span data-ttu-id="e4ed3-136">Por lo tanto, si queremos que Alex administre la directiva global, debe *anular la asignación* de la Directiva por usuario que se le haya asignado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="e4ed3-136">Therefore, if we want Alex to be managed by the global policy, you need to  *unassign*  any per-user policy previously assigned to him.</span></span> <span data-ttu-id="e4ed3-137">A continuación se muestra un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="e4ed3-137">Here is an example command:</span></span>
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName $Null
```

<span data-ttu-id="e4ed3-138">Este comando establece el nombre de la Directiva de acceso externo asignada a Alex en un valor nulo ($Null).</span><span class="sxs-lookup"><span data-stu-id="e4ed3-138">This command sets the name of the external access policy assigned to Alex to a null value ($Null).</span></span> <span data-ttu-id="e4ed3-139">Null significa "Nothing".</span><span class="sxs-lookup"><span data-stu-id="e4ed3-139">Null means "nothing".</span></span> <span data-ttu-id="e4ed3-140">Es decir, no se asigna ninguna directiva de acceso externo a Alex.</span><span class="sxs-lookup"><span data-stu-id="e4ed3-140">In other words, no external access policy is assigned to Alex.</span></span> <span data-ttu-id="e4ed3-141">Cuando no se asigna ninguna directiva de acceso externo a un usuario, dicho usuario se administra mediante la directiva global.</span><span class="sxs-lookup"><span data-stu-id="e4ed3-141">When no external access policy is assigned to a user, that user then gets managed by the global policy.</span></span>
  

## <a name="managing-large-numbers-of-users"></a><span data-ttu-id="e4ed3-142">Administración de grandes cantidades de usuarios</span><span class="sxs-lookup"><span data-stu-id="e4ed3-142">Managing large numbers of users</span></span>

<span data-ttu-id="e4ed3-143">Para administrar un gran número de usuarios (1000 o más), debe procesar los comandos mediante un bloque de script mediante el cmdlet [Invoke-Command](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/invoke-command?view=powershell-7) .</span><span class="sxs-lookup"><span data-stu-id="e4ed3-143">To manage large numbers of users (1000 or more), you need to batch the commands via a script block using the [Invoke-Command](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/invoke-command?view=powershell-7) cmdlet.</span></span>  <span data-ttu-id="e4ed3-144">En los ejemplos anteriores, cada vez que se ejecuta un cmdlet, debe configurar la llamada y, a continuación, esperar el resultado antes de volver a enviarlo.</span><span class="sxs-lookup"><span data-stu-id="e4ed3-144">In previous examples, each time a cmdlet is executed, it must set up the call and then wait for the result before sending it back.</span></span>  <span data-ttu-id="e4ed3-145">Cuando se usa un bloque de script, esto permite que se ejecuten los cmdlets de forma remota y, una vez finalizado, se devuelven los datos.</span><span class="sxs-lookup"><span data-stu-id="e4ed3-145">When using a script block, this allows the cmdlets to be executed remotely, and once completed, send the data back.</span></span> 

```powershell
Import-Module LyncOnlineConnector
$sfbSession = New-CsOnlineSession
$users = Get-CsOnlineUser -Filter { ClientPolicy -eq $null } -ResultSize 500

$batch = 50
$filter = ''
$total = $users.Count
$count = 0
    $users | ForEach-Object {
    $upn = $_.UserPrincipalName
    $filter += "(UserPrincipalName -eq '$upn')"
    $batch--
    $count++
    if (($batch -eq 0) -or ($count -eq $total)) {
        $filterSB=[ScriptBlock]::Create($filter)
        Invoke-Command -Session $s -ScriptBlock {param($f) Get-CsOnlineUser -filter $f | Grant-CsClientPolicy -PolicyName "ClientPolicyNoIMURL" -Passthru | Grant-CsExternalAccessPolicy -PolicyName "FederationAndPICDefault"} -ArgumentList $filterSB

        # Reset
        $batch = 50
        $filter = ''
    } else {
        $filter += " -or "
    }
}
```

<span data-ttu-id="e4ed3-146">Esto buscará 500 usuarios a la vez que no tienen una directiva de cliente.</span><span class="sxs-lookup"><span data-stu-id="e4ed3-146">This will find 500 users at a time who do not have a client policy.</span></span> <span data-ttu-id="e4ed3-147">Se le concederá la Directiva de cliente "ClientPolicyNoIMURL" y la Directiva de acceso externo "FederationAndPicDefault".</span><span class="sxs-lookup"><span data-stu-id="e4ed3-147">It will grant them the client policy "ClientPolicyNoIMURL" and the external access policy "FederationAndPicDefault".</span></span> <span data-ttu-id="e4ed3-148">Los resultados se procesan por lotes en grupos de 50 y, a continuación, cada lote de 50 se envía al equipo remoto.</span><span class="sxs-lookup"><span data-stu-id="e4ed3-148">The results are batched into groups of 50 and each batch of 50 is then sent to the remote machine.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e4ed3-149">Ver también</span><span class="sxs-lookup"><span data-stu-id="e4ed3-149">See also</span></span>

[<span data-ttu-id="e4ed3-150">Administrar Skype Empresarial Online con PowerShell</span><span class="sxs-lookup"><span data-stu-id="e4ed3-150">Manage Skype for Business Online with PowerShell</span></span>](manage-skype-for-business-online-with-office-365-powershell.md)
  
[<span data-ttu-id="e4ed3-151">Administrar Microsoft 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="e4ed3-151">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="e4ed3-152">Introducción a PowerShell para Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="e4ed3-152">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)
