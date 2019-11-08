---
title: Administrar Skype para políticas de negocios en línea con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/26/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: 'Resumen: Use Office 365 PowerShell para administrar las propiedades de la cuenta de usuario de Skype empresarial online con directivas.'
ms.openlocfilehash: 51e402922b2a357ef29e9b2628eb25fc252e5437
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2019
ms.locfileid: "38031735"
---
# <a name="manage-skype-for-business-online-policies-with-office-365-powershell"></a><span data-ttu-id="dc6ea-103">Administrar Skype para políticas de negocios en línea con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="dc6ea-103">Manage Skype for Business Online policies with Office 365 PowerShell</span></span>

 <span data-ttu-id="dc6ea-104">**Resumen:** Use Office 365 PowerShell para administrar las propiedades de la cuenta de usuario de Skype empresarial online con directivas.</span><span class="sxs-lookup"><span data-stu-id="dc6ea-104">**Summary:** Use Office 365 PowerShell to manage your Skype for Business Online user account properties with policies.</span></span>
  
<span data-ttu-id="dc6ea-105">Para administrar muchas propiedades de la cuenta de usuario de Skype empresarial online, debe especificarlas como propiedades de directivas con Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dc6ea-105">To manage many properties of user account for Skype for Business Online, you must specify them as properties of policies with Office 365 PowerShell.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="dc6ea-106">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="dc6ea-106">Before you begin</span></span>

<span data-ttu-id="dc6ea-107">Siga estas instrucciones para preparar la ejecución de los comandos (omita los pasos que ya ha completado):</span><span class="sxs-lookup"><span data-stu-id="dc6ea-107">Use these instructions to get set up to run the commands (skip the steps you have already completed):</span></span>
  
1. <span data-ttu-id="dc6ea-108">Descargue e instale el [módulo de conector de Skype empresarial online](https://www.microsoft.com/download/details.aspx?id=39366).</span><span class="sxs-lookup"><span data-stu-id="dc6ea-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/download/details.aspx?id=39366).</span></span>
    
2. <span data-ttu-id="dc6ea-109">Abra un símbolo del sistema de Windows PowerShell y ejecute los siguientes comandos:</span><span class="sxs-lookup"><span data-stu-id="dc6ea-109">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
```
Import-Module SkypeOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
  ```

<span data-ttu-id="dc6ea-110">Cuando se le solicite, escriba el nombre y la contraseña de la cuenta de administrador en línea de Skype empresarial online.</span><span class="sxs-lookup"><span data-stu-id="dc6ea-110">When prompted, enter your Skype for Business Online administrator account name and password.</span></span>
    
## <a name="manage-user-account-policies"></a><span data-ttu-id="dc6ea-111">Administrar directivas de cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="dc6ea-111">Manage user account policies</span></span>

<span data-ttu-id="dc6ea-112">Muchas de las propiedades de las cuentas de usuario de Skype empresarial online se configuran mediante directivas.</span><span class="sxs-lookup"><span data-stu-id="dc6ea-112">Many Skype for Business Online user account properties are configured by using policies.</span></span> <span data-ttu-id="dc6ea-113">Las directivas son simplemente colecciones de opciones de configuración que se pueden aplicar a uno o más usuarios.</span><span class="sxs-lookup"><span data-stu-id="dc6ea-113">Policies are simply collections of settings that can be applied to one or more users.</span></span> <span data-ttu-id="dc6ea-114">Para echar un vistazo al modo en que se ha configurado la Directiva, puede ejecutar este comando de ejemplo para la Directiva FederationAndPICDefault:</span><span class="sxs-lookup"><span data-stu-id="dc6ea-114">To take a look at how the a policy has been configured, you can run this example command for the FederationAndPICDefault policy:</span></span>
  
```
Get-CsExternalAccessPolicy -Identity "FederationAndPICDefault"
```

<span data-ttu-id="dc6ea-115">Por su parte, debería obtener algo similar a esto:</span><span class="sxs-lookup"><span data-stu-id="dc6ea-115">In turn, you should get back something similar to this:</span></span>
  
```
Identity                          : Tag:FederationAndPICDefault
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : True
EnablePublicCloudAudioVideoAccess : True
EnableOutsideAccess               : True
```

<span data-ttu-id="dc6ea-116">En este ejemplo, los valores de esta directiva determinan lo que un uso puede o no hacer cuando se trata de comunicarse con usuarios federados.</span><span class="sxs-lookup"><span data-stu-id="dc6ea-116">In this example, the values within this policy determine what a use can or cannot do when it comes to communicating with federated users.</span></span> <span data-ttu-id="dc6ea-117">Por ejemplo, la propiedad EnableOutsideAccess debe establecerse en true para que un usuario pueda comunicarse con personas fuera de la organización.</span><span class="sxs-lookup"><span data-stu-id="dc6ea-117">For example, the EnableOutsideAccess property must be set to True for a user to be able to communicate with people outside the organization.</span></span> <span data-ttu-id="dc6ea-118">Tenga en cuenta que esta propiedad no aparece en el centro de administración de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="dc6ea-118">Note that this property does not appear in the Microsoft 365 admin center.</span></span> <span data-ttu-id="dc6ea-119">En su lugar, la propiedad se establece automáticamente en true o false en función de las otras selecciones que realice.</span><span class="sxs-lookup"><span data-stu-id="dc6ea-119">Instead, the property is automatically set to True or False based on the other selections that you make.</span></span> <span data-ttu-id="dc6ea-120">Las otras dos propiedades de interés son:</span><span class="sxs-lookup"><span data-stu-id="dc6ea-120">The other two properties of interest are:</span></span>
  
- <span data-ttu-id="dc6ea-121">**EnableFederationAccess** indica si el usuario puede comunicarse con usuarios de dominios federados.</span><span class="sxs-lookup"><span data-stu-id="dc6ea-121">**EnableFederationAccess** indicates whether the user can communicate with people from federated domains.</span></span>
    
- <span data-ttu-id="dc6ea-122">**EnablePublicCloudAccess** indica si el usuario puede comunicarse con usuarios de Windows Live.</span><span class="sxs-lookup"><span data-stu-id="dc6ea-122">**EnablePublicCloudAccess** indicates whether the user can communicate with Windows Live users.</span></span>
    
<span data-ttu-id="dc6ea-123">Por lo tanto, no cambie directamente las propiedades relacionadas con la Federación de las cuentas de usuario (por ejemplo, **set-CsUser-EnableFederationAccess $true**).</span><span class="sxs-lookup"><span data-stu-id="dc6ea-123">Therefore, you don't directly change federation-related properties on user accounts (for example, **Set-CsUser -EnableFederationAccess $True**).</span></span> <span data-ttu-id="dc6ea-124">En su lugar, asigna a una cuenta una directiva de acceso externo que tiene los valores de propiedad deseados preconfigurados.</span><span class="sxs-lookup"><span data-stu-id="dc6ea-124">Instead, you assign an account an external access policy that has the desired property values preconfigured.</span></span> <span data-ttu-id="dc6ea-125">Si queremos que un usuario pueda comunicarse con usuarios federados y con usuarios de Windows Live, la cuenta de usuario debe tener asignada una directiva que permita estos tipos de comunicación.</span><span class="sxs-lookup"><span data-stu-id="dc6ea-125">If we want a user to be able to communicate with federated users and with Windows Live users, that user account must be assigned a policy that allows those types of communication.</span></span>
  
<span data-ttu-id="dc6ea-126">Si desea saber si alguien puede comunicarse con usuarios externos a la organización, debe:</span><span class="sxs-lookup"><span data-stu-id="dc6ea-126">If you want to know whether or not someone can communicate with users from outside the organization, you have to:</span></span>
  
- <span data-ttu-id="dc6ea-127">Determinar qué directiva de acceso externo se ha asignado a dicho usuario.</span><span class="sxs-lookup"><span data-stu-id="dc6ea-127">Determine which external access policy has been assigned to that user.</span></span>
    
- <span data-ttu-id="dc6ea-128">Determinar qué capacidades permite o no dicha directiva.</span><span class="sxs-lookup"><span data-stu-id="dc6ea-128">Determine which capabilities are or are not allowed by that policy.</span></span>
    
<span data-ttu-id="dc6ea-129">Por ejemplo, puede hacerlo con este comando:</span><span class="sxs-lookup"><span data-stu-id="dc6ea-129">For example, you can do that by using this command:</span></span>
  
```
Get-CsOnlineUser -Identity "Alex Darrow" | ForEach {Get-CsExternalAccessPolicy -Identity $_.ExternalAccessPolicy}
```

<span data-ttu-id="dc6ea-130">Este comando busca la directiva asignada al usuario y, a continuación, busca las funciones habilitadas o deshabilitadas en esa Directiva.</span><span class="sxs-lookup"><span data-stu-id="dc6ea-130">This command finds the policy assigned to the user, then finds the capabilities enabled or disabled within that policy.</span></span>
  
<span data-ttu-id="dc6ea-131">Para administrar las directivas de Skype empresarial online con PowerShell, consulte los cmdlets de:</span><span class="sxs-lookup"><span data-stu-id="dc6ea-131">To manage Skype for Business Online policies with PowerShell, see the cmdlets for:</span></span>

- <span data-ttu-id="dc6ea-132">[Directiva de cliente](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#client-policy-cmdlets)</span><span class="sxs-lookup"><span data-stu-id="dc6ea-132">[Client policy](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#client-policy-cmdlets)</span></span>
- <span data-ttu-id="dc6ea-133">[Directiva de conferencia](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#conferencing-policy-cmdlets)</span><span class="sxs-lookup"><span data-stu-id="dc6ea-133">[Conferencing policy](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#conferencing-policy-cmdlets)</span></span>
- <span data-ttu-id="dc6ea-134">[Directiva móvil](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#mobile-policy-cmdlets)</span><span class="sxs-lookup"><span data-stu-id="dc6ea-134">[Mobile policy](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#mobile-policy-cmdlets)</span></span>
- <span data-ttu-id="dc6ea-135">[Directiva de correo de voz en línea](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#online-voicemail-policy-cmdlets)</span><span class="sxs-lookup"><span data-stu-id="dc6ea-135">[Online Voicemail policy](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#online-voicemail-policy-cmdlets)</span></span>
- <span data-ttu-id="dc6ea-136">[Directiva de enrutamiento de voz](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#voice-routing-policy-cmdlets)</span><span class="sxs-lookup"><span data-stu-id="dc6ea-136">[Voice Routing policy](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#voice-routing-policy-cmdlets)</span></span>


> [!NOTE]
> <span data-ttu-id="dc6ea-137">Un plan de marcado de Skype empresarial online es una directiva en todos los aspectos excepto en el nombre.</span><span class="sxs-lookup"><span data-stu-id="dc6ea-137">A Skype for Business Online dial plan is a policy in every respect except the name.</span></span> <span data-ttu-id="dc6ea-138">Se ha elegido el nombre "plan de marcado" en lugar de, por ejemplo, "Directiva de marcado" para proporcionar compatibilidad con versiones anteriores de Office Communications Server y con Exchange.</span><span class="sxs-lookup"><span data-stu-id="dc6ea-138">The name "dial plan" was chosen instead of, say, "dialing policy" in order to provide backward compatibility with Office Communications Server and with Exchange.</span></span> 
  
<span data-ttu-id="dc6ea-139">Por ejemplo, para ver todas las directivas de voz disponibles para su uso, ejecute este comando:</span><span class="sxs-lookup"><span data-stu-id="dc6ea-139">For example, to look at all the voice policies available for your use, run this command:</span></span>
  
```
Get-CsVoicePolicy
```

> [!NOTE]
> <span data-ttu-id="dc6ea-140">Eso devuelve una lista de todas las directivas de voz disponibles para usted.</span><span class="sxs-lookup"><span data-stu-id="dc6ea-140">That returns a list of all the voice policies available to you.</span></span> <span data-ttu-id="dc6ea-141">No obstante, tenga en cuenta que no todas las directivas se pueden asignar a todos los usuarios.</span><span class="sxs-lookup"><span data-stu-id="dc6ea-141">Keep in mind, however, that not all policies can be assigned to all users.</span></span> <span data-ttu-id="dc6ea-142">Esto se debe a varias restricciones relacionadas con la concesión de licencias y la ubicación geográfica.</span><span class="sxs-lookup"><span data-stu-id="dc6ea-142">This is due to various restrictions involving licensing and geographic location.</span></span> <span data-ttu-id="dc6ea-143">(El denominado "ubicación de[uso](https://msdn.microsoft.com/library/azure/dn194136.aspx)"). Si desea conocer las directivas de acceso externo y las directivas de conferencia que se pueden asignar a un usuario en particular, use comandos similares a los siguientes:</span><span class="sxs-lookup"><span data-stu-id="dc6ea-143">(The so-called "[usage location](https://msdn.microsoft.com/library/azure/dn194136.aspx).") If you want to know the external access policies and the conferencing policies that can be assigned to a particular user, use commands similar to these:</span></span> 

```
Get-CsConferencingPolicy -ApplicableTo "Alex Darrow"
Get-CsExternalAccessPolicy -ApplicableTo "Alex Darrow"
```

<span data-ttu-id="dc6ea-p106">El parámetro ApplicableTo limita los datos devueltos a las directivas que se pueden asignar al usuario especificado (por ejemplo, Alex Darrow). Según las licencias y las restricciones de ubicación de uso, eso puede representar un subconjunto de todas las directivas disponibles.</span><span class="sxs-lookup"><span data-stu-id="dc6ea-p106">The ApplicableTo parameter limits the returned data to policies that can be assigned to the specified user (for example, Alex Darrow). Depending on licensing and usage location restrictions, that might represent a subset of all the available policies.</span></span> 
  
<span data-ttu-id="dc6ea-146">En algunos casos, las propiedades de las directivas no se usan con Office 365, mientras que otras solo pueden ser administradas por el personal de soporte técnico de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="dc6ea-146">In some cases, properties of policies are not used with Office 365, while others can only be managed by Microsoft support personnel.</span></span> 
  
<span data-ttu-id="dc6ea-147">Con Skype empresarial online, los usuarios deben ser administrados por una directiva de algún tipo.</span><span class="sxs-lookup"><span data-stu-id="dc6ea-147">With Skype for Business Online, users must be managed by a policy of some kind.</span></span> <span data-ttu-id="dc6ea-148">Si una propiedad relacionada con directivas válida está en blanco, significa que el usuario en cuestión se administra mediante una directiva global, que es una directiva que se aplica automáticamente a un usuario a menos que se le asigne específicamente una directiva por usuario.</span><span class="sxs-lookup"><span data-stu-id="dc6ea-148">If a valid policy-related property is blank, that means that the user in question is being managed by a global policy, which is a policy that is automatically applied to a user unless he or she is specifically assigned a per-user policy.</span></span> <span data-ttu-id="dc6ea-149">Como no vemos una directiva de cliente listada para una cuenta de usuario, ésta se administra mediante la directiva global.</span><span class="sxs-lookup"><span data-stu-id="dc6ea-149">Because we don't see a client policy listed for a user account, it is managed by the global policy.</span></span> <span data-ttu-id="dc6ea-150">Puede determinar la Directiva de cliente global con este comando:</span><span class="sxs-lookup"><span data-stu-id="dc6ea-150">You can determine the global client policy with this command:</span></span>
  
```
Get-CsClientPolicy -Identity "Global"
```

## <a name="see-also"></a><span data-ttu-id="dc6ea-151">Vea también</span><span class="sxs-lookup"><span data-stu-id="dc6ea-151">See also</span></span>

#### 

[<span data-ttu-id="dc6ea-152">Administrar Skype Empresarial Online con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="dc6ea-152">Manage Skype for Business Online with Office 365 PowerShell</span></span>](manage-skype-for-business-online-with-office-365-powershell.md)
  
[<span data-ttu-id="dc6ea-153">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="dc6ea-153">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="dc6ea-154">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="dc6ea-154">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

