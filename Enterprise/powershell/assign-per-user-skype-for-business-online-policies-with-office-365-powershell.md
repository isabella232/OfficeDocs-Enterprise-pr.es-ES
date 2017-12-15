---
title: "Asignar cada usuario Skype para las políticas de negocios en línea con Office 365 PowerShell"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: DecEntMigration
ms.assetid: 36743c86-46c2-46be-b9ed-ad9d4e85d186
description: "Resumen: Uso Office 365 PowerShell para asignar a cada usuario configuración de comunicaciones con Skype para las políticas de negocios en línea."
ms.openlocfilehash: 91916b41ba420a204ecabb27eea2e451a91f6f25
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2017
---
# <a name="assign-per-user-skype-for-business-online-policies-with-office-365-powershell"></a><span data-ttu-id="c59e5-103">Asignar cada usuario Skype para las políticas de negocios en línea con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c59e5-103">Assign per-user Skype for Business Online policies with Office 365 PowerShell</span></span>

 <span data-ttu-id="c59e5-104">**Resumen:** Utilice Office 365 PowerShell para asignar a cada usuario configuración de comunicaciones con Skype para las políticas de negocios en línea.</span><span class="sxs-lookup"><span data-stu-id="c59e5-104">**Summary:** Use Office 365 PowerShell to assign per-user communication settings with Skype for Business Online policies.</span></span>
  
<span data-ttu-id="c59e5-105">Con Office 365 PowerShell es una forma eficaz de asignar a cada usuario configuración de comunicaciones con Skype para las políticas de negocios en línea.</span><span class="sxs-lookup"><span data-stu-id="c59e5-105">Using Office 365 PowerShell is an efficient way to assign per-user communication settings with Skype for Business Online policies.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="c59e5-106">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="c59e5-106">Before you begin</span></span>

<span data-ttu-id="c59e5-107">Siga estas instrucciones para obtener configurado para ejecutar los comandos (sáltese los pasos que ya ha completado):</span><span class="sxs-lookup"><span data-stu-id="c59e5-107">Use these instructions to get set up to run the commands (skip the steps you have already completed):</span></span>
  
1. <span data-ttu-id="c59e5-108">Descargue e instale el [Skype para el módulo de Business Connector en línea](https://www.microsoft.com/en-us/download/details.aspx?id=39366).</span><span class="sxs-lookup"><span data-stu-id="c59e5-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/en-us/download/details.aspx?id=39366).</span></span>
    
2. <span data-ttu-id="c59e5-109">Abra un símbolo del sistema de Windows PowerShell y ejecute los comandos siguientes:</span><span class="sxs-lookup"><span data-stu-id="c59e5-109">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
  ```
  Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
  ```
<span data-ttu-id="c59e5-110">Cuando se le solicite, escriba su Skype para contraseña y nombre de cuenta de administrador de negocios en línea.</span><span class="sxs-lookup"><span data-stu-id="c59e5-110">When prompted, enter your Skype for Business Online administrator account name and password.</span></span>
    
## <a name="updating-external-communication-settings-for-a-user-account"></a><span data-ttu-id="c59e5-111">Actualizando la configuración de la comunicación externa para una cuenta de usuario</span><span class="sxs-lookup"><span data-stu-id="c59e5-111">Updating external communication settings for a user account</span></span>

<span data-ttu-id="c59e5-p101">Suponga que desea cambiar la configuración de la comunicación externa en una cuenta de usuario. Por ejemplo, desea permitir que Alex para comunicarse con los usuarios federados (EnableFederationAccess es igual a True) pero no a los usuarios de Windows Live (EnablePublicCloudAccess es igual a falso). Para ello, debe hacer dos cosas:</span><span class="sxs-lookup"><span data-stu-id="c59e5-p101">Suppose you want to change external communication settings on a user account. For example, you want to allow Alex to communicate with federated users (EnableFederationAccess is equal to True) but not with Windows Live users (EnablePublicCloudAccess equals False). To do that, you need to do two things:</span></span>
  
1. <span data-ttu-id="c59e5-115">Buscar una directiva de acceso externo que cumpla nuestros criterios.</span><span class="sxs-lookup"><span data-stu-id="c59e5-115">Find an external access policy that meets our criteria.</span></span>
    
2. <span data-ttu-id="c59e5-116">Asignar esa directiva de acceso externo a Alex.</span><span class="sxs-lookup"><span data-stu-id="c59e5-116">Assign that external access policy to Alex.</span></span>
    
> [!NOTE]
>  <span data-ttu-id="c59e5-p102">No se puede crear una directiva personalizada todos nuestros propios. Eso es porque Skype para los negocios en línea no le permiten crear directivas personalizadas. En su lugar, debe asignar una de las directivas que se han creado específicamente para Office 365. Aquellos creados previamente las políticas incluyen: 4 políticas de cliente diferente, 224 conferencias diferentes directivas, 5 otros planes de marcado, 5 directivas de acceso externo diferente, directivas de correo de voz hospedado 1 y 4 otra voz directivas.</span><span class="sxs-lookup"><span data-stu-id="c59e5-p102">You can't create a custom policy all our own. That's because Skype for Business Online does not allow you to create custom policies. Instead, you must assign one of the policies that were created specifically for Office 365. Those pre-created policies include: 4 different client policies, 224 different conferencing policies, 5 different dial plans, 5 different external access policies, 1 hosted voicemail policy, and 4 different voice policies.</span></span>
  
<span data-ttu-id="c59e5-p103">Entonces, ¿cómo puede determinar qué directiva de acceso externo para asignar a Alex? El siguiente comando devuelve todas las directivas de acceso externo donde EnableFederationAccess está establecida en True y EnablePublicCloudAccess se establece en False:</span><span class="sxs-lookup"><span data-stu-id="c59e5-p103">So how do you determine which external access policy to assign Alex? The following command returns all the external access policies where EnableFederationAccess is set to True and EnablePublicCloudAccess is set to False:</span></span>
  
```
Get-CsExternalAccessPolicy | Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $False}
```

<span data-ttu-id="c59e5-p104">Lo que hace el comando es devolver todas las directivas que cumplan dos criterios: la propiedad EnableFederationAccess está establecida en True, y la directiva EnablePublicCloudAccess está establecida en False. A su vez, ese comando devuelve una directiva que cumpla nuestros criterios (FederationOnly). Éste es un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="c59e5-p104">What the command does is return all the policies that meet two criteria: the EnableFederationAccess property is set to True, and the EnablePublicCloudAccess policy is set to False. In turn, that command returns one policy that meets our criteria (FederationOnly). Here is an example:</span></span>
  
```
Identity                          : Tag:FederationOnly
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : False
EnablePublicCloudAudioVideoAccess : False
EnableOutsideAccess               : True
```

> [!NOTE]
> <span data-ttu-id="c59e5-p105">La directiva de identidad indica etiqueta: FederationOnly. Según parece, la etiqueta: prefijo es un remanente de trabajo previo al lanzamiento temprano realizado en Microsoft Lync 2013. En cuanto a la asignación de directivas a los usuarios, debe eliminar la etiqueta: prefijo y utilizar simplemente el nombre de la directiva: FederationOnly.</span><span class="sxs-lookup"><span data-stu-id="c59e5-p105">The policy Identity says Tag:FederationOnly. As it turns out, the Tag: prefix is a carryover from the early pre-release work done on Microsoft Lync 2013. When it comes to assigning policies to users, you should delete the Tag: prefix and use just the policy name: FederationOnly.</span></span> 
  
<span data-ttu-id="c59e5-p106">Ahora que sabe qué directiva para asignar a Alex, podemos asignar esa directiva mediante el cmdlet de [Concesión CsExternalAccessPolicy](https://go.microsoft.com/fwlink/?LinkId=523974) . Éste es un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="c59e5-p106">Now that you know which policy to assign to Alex, we can assign that policy by using the [Grant-CsExternalAccessPolicy](https://go.microsoft.com/fwlink/?LinkId=523974) cmdlet. Here is an example:</span></span>
  
```
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName "FederationOnly"
```

<span data-ttu-id="c59e5-131">Asignación de una directiva es bastante sencilla: sólo tiene que especificar la identidad del usuario y el nombre de la directiva que se asignará.</span><span class="sxs-lookup"><span data-stu-id="c59e5-131">Assigning a policy is pretty simple: you simply specify the Identity of the user and the name of the policy to be assigned.</span></span> 
  
<span data-ttu-id="c59e5-p107">Y en cuanto a las políticas y las asignaciones de directivas, no está limitado a trabajar con cuentas de usuario una vez. Por ejemplo, suponga que necesita una lista de todos los usuarios que tienen permiso para comunicarse con los socios federados y con usuarios de Windows Live. Ya se sabe que los usuarios le ha asignado la directiva de acceso de usuario externo FederationAndPICDefault. Porque sabemos, mediante la ejecución de un comando simple puede mostrar una lista de todos los usuarios. Aquí está el comando:</span><span class="sxs-lookup"><span data-stu-id="c59e5-p107">And when it comes to policies and policy assignments, you're not limited to working with user accounts one a time. For example, suppose you need a list of all the users who are allowed to communicate with federated partners and with Windows Live users. We already know that those users have been assigned the external user access policy FederationAndPICDefault. Because we know that, you can display a list of all those users by running one simple command. Here is the command:</span></span>
  
```
Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "FederationAndPICDefault"} | Select-Object DisplayName
```

<span data-ttu-id="c59e5-p108">En otras palabras, nos muestran todos los usuarios donde se establece la propiedad ExternalAccessPolicy a FederationAndPICDefault. (Y, con el fin de limitar la cantidad de información que aparece en la pantalla, use el cmdlet Select-Object para mostrar nos muestran sólo nombre para mostrar de cada usuario).</span><span class="sxs-lookup"><span data-stu-id="c59e5-p108">In other words, show us all the users where the ExternalAccessPolicy property is set to FederationAndPICDefault. (And, in order to limit the amount of information that appears onscreen, use the Select-Object cmdlet to display show us only each user's display name.)</span></span> 
  
<span data-ttu-id="c59e5-139">Para configurar todas las cuentas de usuarios para utilizar esa misma directiva, use este comando:</span><span class="sxs-lookup"><span data-stu-id="c59e5-139">To configure all our user accounts to use that same policy, use this command:</span></span>
  
```
Get-CsOnlineUser | Grant-CsExternalAccessPolicy "FederationAndPICDefault"
```

<span data-ttu-id="c59e5-140">Este comando utiliza Get-CsOnlineUser para devolver una colección de todos los usuarios que se han habilitado para Lync, entonces envía toda esa información a CsExternalAccessPolicy de la concesión, que se asigna la directiva FederationAndPICDefault para cada usuario de la colección.</span><span class="sxs-lookup"><span data-stu-id="c59e5-140">This command uses Get-CsOnlineUser to return a collection of all the users who have been enabled for Lync, then sends all that information to Grant-CsExternalAccessPolicy, which assigns the FederationAndPICDefault policy to each and every user in the collection.</span></span>
  
<span data-ttu-id="c59e5-p109">Como ejemplo adicional, supongamos que Alex previamente se ha asignado la directiva FederationAndPICDefault y ahora ha cambiado de opinión y desea que le sea administrado por la directiva global de acceso externo. No se puede asignar explícitamente la directiva global a nadie. Sólo se utiliza si no se ha asignado ninguna otra directiva por usuario. Por lo tanto, si queremos que Alex sea administrado por la directiva global, debe *desasignar* cualquier directiva por usuario previamente asignado a él. Aquí es un comando de ejemplo:</span><span class="sxs-lookup"><span data-stu-id="c59e5-p109">As an additional example, suppose you've previously assigned Alex the FederationAndPICDefault policy and now you've changed your mind and would like him to be managed by the global external access policy. You can't explicitly assign the global policy to anyone. It is only used if no other per-user policy is assigned. Therefore, if we want Alex to be managed by the global policy, you need to  *unassign*  any per-user policy previously assigned to him. Here is an example command:</span></span>
  
```
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName $Null
```

<span data-ttu-id="c59e5-p110">Este comando establece el nombre de la directiva de acceso externo asignado a Alex en un valor nulo ($Null). NULL significa "nada". En otras palabras, no se asigna ninguna directiva de acceso externo a Alex. Cuando se ha asignado ninguna directiva de acceso externo a un usuario, dicho usuario obtiene administrado por la directiva global.</span><span class="sxs-lookup"><span data-stu-id="c59e5-p110">This command sets the name of the external access policy assigned to Alex to a null value ($Null). Null means "nothing". In other words, no external access policy is assigned to Alex. When no external access policy is assigned to a user, that user then gets managed by the global policy.</span></span>
  
<span data-ttu-id="c59e5-p111">Para deshabilitar una cuenta de usuario con Windows PowerShell, usar los cmdlets de Azure Active Directory para quitar Skype de Alex para licencia de negocios en línea. Para obtener más información, vea [Deshabilitar el acceso a los servicios de Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="c59e5-p111">To disable a user account using Windows PowerShell, use the Azure Active Directory cmdlets to remove Alex's Skype for Business Online license. For more information, see [Disable access to services with Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c59e5-152">See also</span><span class="sxs-lookup"><span data-stu-id="c59e5-152">See also</span></span>

#### 

[<span data-ttu-id="c59e5-153">Administrar Skype Empresarial Online con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="c59e5-153">Manage Skype for Business Online with Office 365 PowerShell</span></span>](manage-skype-for-business-online-with-office-365-powershell.md)
  
[<span data-ttu-id="c59e5-154">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="c59e5-154">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="c59e5-155">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="c59e5-155">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

