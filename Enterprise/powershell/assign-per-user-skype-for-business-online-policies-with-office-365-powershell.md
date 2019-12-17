---
title: Asignar cada usuario Skype para las políticas de negocios en línea con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 36743c86-46c2-46be-b9ed-ad9d4e85d186
description: 'Resumen: Use Office 365 PowerShell para asignar configuraciones de comunicación por usuario con directivas de Skype empresarial online.'
ms.openlocfilehash: e425c3f0bc6253550b1be2081df89e535da811f4
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072262"
---
# <a name="assign-per-user-skype-for-business-online-policies-with-office-365-powershell"></a><span data-ttu-id="bf8fe-103">Asignar cada usuario Skype para las políticas de negocios en línea con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="bf8fe-103">Assign per-user Skype for Business Online policies with Office 365 PowerShell</span></span>

<span data-ttu-id="bf8fe-104">El uso de Office 365 PowerShell es una forma eficaz de asignar configuraciones de comunicación por usuario con directivas de Skype empresarial online.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-104">Using Office 365 PowerShell is an efficient way to assign per-user communication settings with Skype for Business Online policies.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="bf8fe-105">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="bf8fe-105">Before you begin</span></span>

<span data-ttu-id="bf8fe-106">Siga estas instrucciones para preparar la ejecución de los comandos (omita los pasos que ya ha completado):</span><span class="sxs-lookup"><span data-stu-id="bf8fe-106">Use these instructions to get set up to run the commands (skip the steps you have already completed):</span></span>
  
1. <span data-ttu-id="bf8fe-107">Descargue e instale el [módulo de conector de Skype empresarial online](https://www.microsoft.com/download/details.aspx?id=39366).</span><span class="sxs-lookup"><span data-stu-id="bf8fe-107">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/download/details.aspx?id=39366).</span></span>
    
2. <span data-ttu-id="bf8fe-108">Abra un símbolo del sistema de Windows PowerShell y ejecute los siguientes comandos:</span><span class="sxs-lookup"><span data-stu-id="bf8fe-108">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
```powershell
Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
```

<span data-ttu-id="bf8fe-109">Cuando se le solicite, escriba el nombre y la contraseña de la cuenta de administrador en línea de Skype empresarial online.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-109">When prompted, enter your Skype for Business Online administrator account name and password.</span></span>
    
## <a name="updating-external-communication-settings-for-a-user-account"></a><span data-ttu-id="bf8fe-110">Actualización de la configuración de comunicación externa para una cuenta de usuario</span><span class="sxs-lookup"><span data-stu-id="bf8fe-110">Updating external communication settings for a user account</span></span>

<span data-ttu-id="bf8fe-111">Supongamos que desea cambiar la configuración de comunicación externa en una cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-111">Suppose you want to change external communication settings on a user account.</span></span> <span data-ttu-id="bf8fe-112">Por ejemplo, desea permitir que Alex se comunique con los usuarios federados (EnableFederationAccess es igual a true) pero no con los usuarios de Windows Live (EnablePublicCloudAccess es igual a false).</span><span class="sxs-lookup"><span data-stu-id="bf8fe-112">For example, you want to allow Alex to communicate with federated users (EnableFederationAccess is equal to True) but not with Windows Live users (EnablePublicCloudAccess equals False).</span></span> <span data-ttu-id="bf8fe-113">Para ello, debe hacer dos cosas:</span><span class="sxs-lookup"><span data-stu-id="bf8fe-113">To do that, you need to do two things:</span></span>
  
1. <span data-ttu-id="bf8fe-114">Buscar una directiva de acceso externo que cumpla nuestros criterios.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-114">Find an external access policy that meets our criteria.</span></span>
    
2. <span data-ttu-id="bf8fe-115">Asignar esa directiva de acceso externo a Alex.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-115">Assign that external access policy to Alex.</span></span>
    
> [!NOTE]
>  <span data-ttu-id="bf8fe-116">No se puede crear una directiva personalizada todo lo mismo.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-116">You can't create a custom policy all our own.</span></span> <span data-ttu-id="bf8fe-117">Esto se debe a que Skype empresarial online no permite crear directivas personalizadas.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-117">That's because Skype for Business Online does not allow you to create custom policies.</span></span> <span data-ttu-id="bf8fe-118">En su lugar, debe asignar una de las directivas creadas específicamente para Office 365.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-118">Instead, you must assign one of the policies that were created specifically for Office 365.</span></span> <span data-ttu-id="bf8fe-119">Estas directivas predefinidas incluyen: 4 directivas de cliente diferentes, 224 distintas directivas de conferencia, 5 planes de marcado diferentes, 5 directivas de acceso externo diferentes, una directiva de correo de voz hospedado y 4 directivas de voz distintas.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-119">Those pre-created policies include: 4 different client policies, 224 different conferencing policies, 5 different dial plans, 5 different external access policies, 1 hosted voicemail policy, and 4 different voice policies.</span></span>
  
<span data-ttu-id="bf8fe-120">¿Cómo se determina qué directiva de acceso externo asignara Alex?</span><span class="sxs-lookup"><span data-stu-id="bf8fe-120">So how do you determine which external access policy to assign Alex?</span></span> <span data-ttu-id="bf8fe-121">El siguiente comando devuelve todas las directivas de acceso externo donde EnableFederationAccess se establece en True y EnablePublicCloudAccess se establece en False:</span><span class="sxs-lookup"><span data-stu-id="bf8fe-121">The following command returns all the external access policies where EnableFederationAccess is set to True and EnablePublicCloudAccess is set to False:</span></span>
  
```powershell
Get-CsExternalAccessPolicy | Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $False}
```

<span data-ttu-id="bf8fe-122">Lo que hace el comando devuelve todas las directivas que cumplen dos criterios: la propiedad EnableFederationAccess se establece en true y la Directiva EnablePublicCloudAccess se establece en false.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-122">What the command does is return all the policies that meet two criteria: the EnableFederationAccess property is set to True, and the EnablePublicCloudAccess policy is set to False.</span></span> <span data-ttu-id="bf8fe-123">A su vez, el comando devuelve una directiva que cumple nuestros criterios (FederationOnly).</span><span class="sxs-lookup"><span data-stu-id="bf8fe-123">In turn, that command returns one policy that meets our criteria (FederationOnly).</span></span> <span data-ttu-id="bf8fe-124">Aquí le mostramos un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="bf8fe-124">Here is an example:</span></span>
  
```powershell
Identity                          : Tag:FederationOnly
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : False
EnablePublicCloudAudioVideoAccess : False
EnableOutsideAccess               : True
```

> [!NOTE]
> <span data-ttu-id="bf8fe-125">La identidad de la Directiva dice etiqueta: FederationOnly.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-125">The policy Identity says Tag:FederationOnly.</span></span> <span data-ttu-id="bf8fe-126">Como resultado, el prefijo de etiqueta es un remanente del trabajo anterior de la versión preliminar que se hizo en Microsoft Lync 2013.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-126">As it turns out, the Tag: prefix is a carryover from the early pre-release work done on Microsoft Lync 2013.</span></span> <span data-ttu-id="bf8fe-127">Cuando se trata de asignar directivas a los usuarios, debe eliminar el prefijo de etiqueta y usar únicamente el nombre de directiva: FederationOnly.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-127">When it comes to assigning policies to users, you should delete the Tag: prefix and use just the policy name: FederationOnly.</span></span> 
  
<span data-ttu-id="bf8fe-128">Ahora que ya sabe qué directiva asignar a Alex, podemos asignar esa Directiva mediante el cmdlet [Grant-CsExternalAccessPolicy](https://go.microsoft.com/fwlink/?LinkId=523974) .</span><span class="sxs-lookup"><span data-stu-id="bf8fe-128">Now that you know which policy to assign to Alex, we can assign that policy by using the [Grant-CsExternalAccessPolicy](https://go.microsoft.com/fwlink/?LinkId=523974) cmdlet.</span></span> <span data-ttu-id="bf8fe-129">Aquí le mostramos un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="bf8fe-129">Here is an example:</span></span>
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName "FederationOnly"
```

<span data-ttu-id="bf8fe-130">La asignación de una directiva es muy sencilla: simplemente especifique la identidad del usuario y el nombre de la Directiva que se va a asignar.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-130">Assigning a policy is pretty simple: you simply specify the Identity of the user and the name of the policy to be assigned.</span></span> 
  
<span data-ttu-id="bf8fe-131">En lo que se refiere a las directivas y asignaciones de directivas, no se limita a trabajar con cuentas de usuario una vez.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-131">And when it comes to policies and policy assignments, you're not limited to working with user accounts one a time.</span></span> <span data-ttu-id="bf8fe-132">Por ejemplo, supongamos que necesita una lista de todos los usuarios que tienen permiso para comunicarse con los socios federados y los usuarios de Windows Live.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-132">For example, suppose you need a list of all the users who are allowed to communicate with federated partners and with Windows Live users.</span></span> <span data-ttu-id="bf8fe-133">Ya sabemos que a esos usuarios se les ha asignado la directiva de acceso de usuario externo FederationAndPICDefault.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-133">We already know that those users have been assigned the external user access policy FederationAndPICDefault.</span></span> <span data-ttu-id="bf8fe-134">Como sabemos, puede mostrar una lista de todos los usuarios mediante la ejecución de un comando sencillo.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-134">Because we know that, you can display a list of all those users by running one simple command.</span></span> <span data-ttu-id="bf8fe-135">Este es el comando:</span><span class="sxs-lookup"><span data-stu-id="bf8fe-135">Here is the command:</span></span>
  
```powershell
Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "FederationAndPICDefault"} | Select-Object DisplayName
```

<span data-ttu-id="bf8fe-136">En otras palabras, veremos a todos los usuarios donde la propiedad ExternalAccessPolicy se establece en FederationAndPICDefault.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-136">In other words, show us all the users where the ExternalAccessPolicy property is set to FederationAndPICDefault.</span></span> <span data-ttu-id="bf8fe-137">(Y, para limitar la cantidad de información que aparece en la pantalla, use el cmdlet Select-Object para mostrar solo el nombre para mostrar de cada usuario).</span><span class="sxs-lookup"><span data-stu-id="bf8fe-137">(And, in order to limit the amount of information that appears onscreen, use the Select-Object cmdlet to display show us only each user's display name.)</span></span> 
  
<span data-ttu-id="bf8fe-138">Para configurar todas las cuentas de usuario para que usen la misma directiva, use este comando:</span><span class="sxs-lookup"><span data-stu-id="bf8fe-138">To configure all our user accounts to use that same policy, use this command:</span></span>
  
```powershell
Get-CsOnlineUser | Grant-CsExternalAccessPolicy "FederationAndPICDefault"
```

<span data-ttu-id="bf8fe-139">Este comando usa Get-CsOnlineUser para devolver una colección de todos los usuarios que se han habilitado para Lync y, a continuación, envía toda la información a Grant-CsExternalAccessPolicy, que asigna la Directiva FederationAndPICDefault a todos y cada uno de los usuarios de la colección.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-139">This command uses Get-CsOnlineUser to return a collection of all the users who have been enabled for Lync, then sends all that information to Grant-CsExternalAccessPolicy, which assigns the FederationAndPICDefault policy to each and every user in the collection.</span></span>
  
<span data-ttu-id="bf8fe-140">Por ejemplo, supongamos que anteriormente ha asignado a Alex la Directiva FederationAndPICDefault y que ahora ha cambiado de opinión y desea que se administre mediante la directiva global de acceso externo.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-140">As an additional example, suppose you've previously assigned Alex the FederationAndPICDefault policy and now you've changed your mind and would like him to be managed by the global external access policy.</span></span> <span data-ttu-id="bf8fe-141">No se puede asignar explícitamente la directiva global a nadie.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-141">You can't explicitly assign the global policy to anyone.</span></span> <span data-ttu-id="bf8fe-142">Solo se usa si no se ha asignado ninguna otra directiva por usuario.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-142">It is only used if no other per-user policy is assigned.</span></span> <span data-ttu-id="bf8fe-143">Por lo tanto, si queremos que Alex administre la directiva global, debe *anular la asignación* de la Directiva por usuario que se le haya asignado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-143">Therefore, if we want Alex to be managed by the global policy, you need to  *unassign*  any per-user policy previously assigned to him.</span></span> <span data-ttu-id="bf8fe-144">A continuación se muestra un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="bf8fe-144">Here is an example command:</span></span>
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName $Null
```

<span data-ttu-id="bf8fe-145">Este comando establece el nombre de la Directiva de acceso externo asignada a Alex en un valor nulo ($Null).</span><span class="sxs-lookup"><span data-stu-id="bf8fe-145">This command sets the name of the external access policy assigned to Alex to a null value ($Null).</span></span> <span data-ttu-id="bf8fe-146">Null significa "Nothing".</span><span class="sxs-lookup"><span data-stu-id="bf8fe-146">Null means "nothing".</span></span> <span data-ttu-id="bf8fe-147">Es decir, no se asigna ninguna directiva de acceso externo a Alex.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-147">In other words, no external access policy is assigned to Alex.</span></span> <span data-ttu-id="bf8fe-148">Cuando no se asigna ninguna directiva de acceso externo a un usuario, dicho usuario se administra mediante la directiva global.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-148">When no external access policy is assigned to a user, that user then gets managed by the global policy.</span></span>
  
<span data-ttu-id="bf8fe-149">Para deshabilitar una cuenta de usuario con Windows PowerShell, use los cmdlets de Azure Active Directory para quitar la licencia de Skype empresarial online de Alex.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-149">To disable a user account using Windows PowerShell, use the Azure Active Directory cmdlets to remove Alex's Skype for Business Online license.</span></span> <span data-ttu-id="bf8fe-150">Para obtener más información, vea [deshabilitar el acceso a servicios con Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="bf8fe-150">For more information, see [Disable access to services with Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="bf8fe-151">Vea también</span><span class="sxs-lookup"><span data-stu-id="bf8fe-151">See also</span></span>

[<span data-ttu-id="bf8fe-152">Administrar Skype Empresarial Online con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="bf8fe-152">Manage Skype for Business Online with Office 365 PowerShell</span></span>](manage-skype-for-business-online-with-office-365-powershell.md)
  
[<span data-ttu-id="bf8fe-153">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="bf8fe-153">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="bf8fe-154">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="bf8fe-154">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

