---
title: Administrar Skype para políticas de negocios en línea con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: 'Resumen: Uso Office 365 PowerShell para administrar su Skype para los negocios en línea propiedades de cuenta de usuario con las directivas.'
ms.openlocfilehash: 6698bd43b2a55e1c98fbe8e536a46e2de604b4d2
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2018
ms.locfileid: "17114919"
---
# <a name="manage-skype-for-business-online-policies-with-office-365-powershell"></a><span data-ttu-id="693e3-103">Administrar Skype para políticas de negocios en línea con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="693e3-103">Manage Skype for Business Online policies with Office 365 PowerShell</span></span>

 <span data-ttu-id="693e3-104">**Resumen:** Utilice Office 365 PowerShell para administrar su Skype para los negocios en línea propiedades de cuenta de usuario con las directivas.</span><span class="sxs-lookup"><span data-stu-id="693e3-104">**Summary:** Use Office 365 PowerShell to manage your Skype for Business Online user account properties with policies.</span></span>
  
<span data-ttu-id="693e3-105">Para administrar muchas de las propiedades de cuenta de usuario de Skype para los negocios en línea, debe especificar como propiedades de directivas de Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="693e3-105">To manage many properties of user account for Skype for Business Online, you must specify them as properties of policies with Office 365 PowerShell.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="693e3-106">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="693e3-106">Before you begin</span></span>

<span data-ttu-id="693e3-107">Siga estas instrucciones para obtener configurado para ejecutar los comandos (sáltese los pasos que ya ha completado):</span><span class="sxs-lookup"><span data-stu-id="693e3-107">Use these instructions to get set up to run the commands (skip the steps you have already completed):</span></span>
  
1. <span data-ttu-id="693e3-108">Descargue e instale el [Skype para el módulo de Business Connector en línea](https://www.microsoft.com/en-us/download/details.aspx?id=39366).</span><span class="sxs-lookup"><span data-stu-id="693e3-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/en-us/download/details.aspx?id=39366).</span></span>
    
2. <span data-ttu-id="693e3-109">Abra un símbolo del sistema de Windows PowerShell y ejecute los comandos siguientes:</span><span class="sxs-lookup"><span data-stu-id="693e3-109">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
```
Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
  ```

<span data-ttu-id="693e3-110">Cuando se le solicite, escriba su Skype para contraseña y nombre de cuenta de administrador de negocios en línea.</span><span class="sxs-lookup"><span data-stu-id="693e3-110">When prompted, enter your Skype for Business Online administrator account name and password.</span></span>
    
## <a name="manage-user-account-policies"></a><span data-ttu-id="693e3-111">Administrar las directivas de cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="693e3-111">Manage user account policies</span></span>

<span data-ttu-id="693e3-p101">Muchos Skype para los negocios en línea propiedades de cuenta de usuario se configuran mediante directivas. Las directivas son simplemente colecciones de configuraciones que se pueden aplicar a uno o más usuarios. Echar un vistazo a cómo se ha configurado una directiva, puede ejecutar este comando de ejemplo para la directiva de FederationAndPICDefault:</span><span class="sxs-lookup"><span data-stu-id="693e3-p101">Many Skype for Business Online user account properties are configured by using policies. Policies are simply collections of settings that can be applied to one or more users. To take a look at how the a policy has been configured, you can run this example command for the FederationAndPICDefault policy:</span></span>
  
```
Get-CsExternalAccessPolicy -Identity "FederationAndPICDefault"
```

<span data-ttu-id="693e3-115">A su vez, debería obtener algo similar a esto:</span><span class="sxs-lookup"><span data-stu-id="693e3-115">In turn, you should get back something similar to this:</span></span>
  
```
Identity                          : Tag:FederationAndPICDefault
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : True
EnablePublicCloudAudioVideoAccess : True
EnableOutsideAccess               : True
```

<span data-ttu-id="693e3-p102">En este ejemplo, los valores de esta directiva determinan lo que se puede utilizar o no pueden hacer cuando se trata de comunicarse con los usuarios federados. Por ejemplo, la propiedad EnableOutsideAccess debe establecerse en True para que un usuario pueda comunicarse con personas ajenas a la organización. Tenga en cuenta que esta propiedad no aparece en el centro de administración de Office 365. En su lugar, la propiedad se establece automáticamente en True o False según las selecciones realizadas. Las otras dos propiedades de interés son:</span><span class="sxs-lookup"><span data-stu-id="693e3-p102">In this example, the values within this policy determine what a use can or cannot do when it comes to communicating with federated users. For example, the EnableOutsideAccess property must be set to True for a user to be able to communicate with people outside the organization. Note that this property does not appear in the Office 365 Admin center. Instead, the property is automatically set to True or False based on the other selections that you make. The other two properties of interest are:</span></span>
  
- <span data-ttu-id="693e3-121">**EnableFederationAccess** indica si el usuario puede comunicarse con usuarios de dominios federados.</span><span class="sxs-lookup"><span data-stu-id="693e3-121">**EnableFederationAccess** indicates whether the user can communicate with people from federated domains.</span></span>
    
- <span data-ttu-id="693e3-122">**EnablePublicCloudAccess** indica si el usuario puede comunicarse con los usuarios de Windows Live.</span><span class="sxs-lookup"><span data-stu-id="693e3-122">**EnablePublicCloudAccess** indicates whether the user can communicate with Windows Live users.</span></span>
    
<span data-ttu-id="693e3-p103">Por lo tanto, no cambia las propiedades relacionadas con la federación en las cuentas de usuario (por ejemplo, el **Conjunto CsUser-EnableFederationAccess $True**) directamente. En su lugar, asigne una cuenta de una directiva de acceso externo que tiene los valores de la propiedad deseada preconfigurados. Si queremos que un usuario pueda comunicarse con los usuarios federados y con usuarios de Windows Live, esa cuenta de usuario debe asignarse una directiva que permite a esos tipos de comunicación.</span><span class="sxs-lookup"><span data-stu-id="693e3-p103">Therefore, you don't directly change federation-related properties on user accounts (for example, **Set-CsUser -EnableFederationAccess $True**). Instead, you assign an account an external access policy that has the desired property values preconfigured. If we want a user to be able to communicate with federated users and with Windows Live users, that user account must be assigned a policy that allows those types of communication.</span></span>
  
<span data-ttu-id="693e3-126">Si desea saber si alguien puede comunicarse con los usuarios de fuera de la organización, deberá:</span><span class="sxs-lookup"><span data-stu-id="693e3-126">If you want to know whether or not someone can communicate with users from outside the organization, you have to:</span></span>
  
- <span data-ttu-id="693e3-127">Determinar qué directiva de acceso externo se ha asignado a dicho usuario.</span><span class="sxs-lookup"><span data-stu-id="693e3-127">Determine which external access policy has been assigned to that user.</span></span>
    
- <span data-ttu-id="693e3-128">Determinar qué capacidades permite o no dicha directiva.</span><span class="sxs-lookup"><span data-stu-id="693e3-128">Determine which capabilities are or are not allowed by that policy.</span></span>
    
<span data-ttu-id="693e3-129">Por ejemplo, se puede hacer mediante este comando:</span><span class="sxs-lookup"><span data-stu-id="693e3-129">For example, you can do that by using this command:</span></span>
  
```
Get-CsOnlineUser -Identity "Alex Darrow" | ForEach {Get-CsExternalAccessPolicy -Identity $_.ExternalAccessPolicy}
```

<span data-ttu-id="693e3-130">Este comando busca la directiva asignada para el usuario, busca después las funciones habilitada o deshabilitan en esa directiva.</span><span class="sxs-lookup"><span data-stu-id="693e3-130">This command finds the policy assigned to the user, then finds the capabilities enabled or disabled within that policy.</span></span>
  
<span data-ttu-id="693e3-p104">Tenga en cuenta que no hay ningún cmdlets para crear o modificar las directivas. Debe utilizar las directivas previamente proporcionadas por Office 365. Si desea echar un vistazo a las diferentes directivas disponibles, puede utilizar estos comandos:</span><span class="sxs-lookup"><span data-stu-id="693e3-p104">Note that there are no cmdlets for creating or for modifying policies. You must use the policies pre-supplied by Office 365. If you want to take a look at the different policies available, you can use these commands:</span></span>
  
- <span data-ttu-id="693e3-134">Get-CsClientPolicy</span><span class="sxs-lookup"><span data-stu-id="693e3-134">Get-CsClientPolicy</span></span>       
- <span data-ttu-id="693e3-135">Get-CsConferencingPolicy</span><span class="sxs-lookup"><span data-stu-id="693e3-135">Get-CsConferencingPolicy</span></span>        
- <span data-ttu-id="693e3-136">Get-CsDialPlan</span><span class="sxs-lookup"><span data-stu-id="693e3-136">Get-CsDialPlan</span></span>            
- <span data-ttu-id="693e3-137">Get-CsExternalAccessPolicy</span><span class="sxs-lookup"><span data-stu-id="693e3-137">Get-CsExternalAccessPolicy</span></span>                         
- <span data-ttu-id="693e3-138">Get-CsHostedVoicemailPolicy</span><span class="sxs-lookup"><span data-stu-id="693e3-138">Get-CsHostedVoicemailPolicy</span></span>                        
- <span data-ttu-id="693e3-139">Get-CsPresencePolicy</span><span class="sxs-lookup"><span data-stu-id="693e3-139">Get-CsPresencePolicy</span></span>                               
- <span data-ttu-id="693e3-140">Get-CsVoicePolicy</span><span class="sxs-lookup"><span data-stu-id="693e3-140">Get-CsVoicePolicy</span></span>                                  

> [!NOTE]
> <span data-ttu-id="693e3-p105">Un Skype para el plan de marcado de los negocios en línea es una directiva en todos los aspectos excepto el nombre. Se ha elegido el nombre "plan de marcado" en lugar de, digamos, "Directiva de marcado" con el fin de proporcionar compatibilidad con Office Communications Server y Exchange.</span><span class="sxs-lookup"><span data-stu-id="693e3-p105">A Skype for Business Online dial plan is a policy in every respect except the name. The name "dial plan" was chosen instead of, say, "dialing policy" in order to provide backward compatibility with Office Communications Server and with Exchange.</span></span> 
  
<span data-ttu-id="693e3-143">Por ejemplo, para buscar en todos las directivas de voz disponibles para su uso, ejecute este comando:</span><span class="sxs-lookup"><span data-stu-id="693e3-143">For example, to look at all the voice policies available for your use, run this command:</span></span>
  
```
Get-CsVoicePolicy
```

> [!NOTE]
> <span data-ttu-id="693e3-p106">Devuelve una lista de todas las directivas de voz disponibles para usted. Tenga en cuenta, sin embargo, que no todas las directivas pueden asignarse a todos los usuarios. Esto es debido a diversas restricciones que implican la ubicación geográfica y con licencia. (Llamados "[ubicación de uso](https://msdn.microsoft.com/en-us/library/azure/dn194136.aspx).") Si desea conocer las directivas de acceso externo y las directivas de conferencias que pueden asignarse a un usuario concreto, utilice comandos similares a éstos:</span><span class="sxs-lookup"><span data-stu-id="693e3-p106">That returns a list of all the voice policies available to you. Keep in mind, however, that not all policies can be assigned to all users. This is due to various restrictions involving licensing and geographic location. (The so-called "[usage location](https://msdn.microsoft.com/en-us/library/azure/dn194136.aspx).") If you want to know the external access policies and the conferencing policies that can be assigned to a particular user, use commands similar to these:</span></span> 

```
Get-CsConferencingPolicy -ApplicableTo "Alex Darrow"
Get-CsExternalAccessPolicy -ApplicableTo "Alex Darrow"
```

<span data-ttu-id="693e3-p107">El parámetro ApplicableTo limita los datos devueltos a las directivas que se pueden asignar al usuario especificado (por ejemplo, Alex Darrow). Según las licencias y las restricciones de ubicación de uso, eso puede representar un subconjunto de todas las directivas disponibles.</span><span class="sxs-lookup"><span data-stu-id="693e3-p107">The ApplicableTo parameter limits the returned data to policies that can be assigned to the specified user (for example, Alex Darrow). Depending on licensing and usage location restrictions, that might represent a subset of all the available policies.</span></span> 
  
<span data-ttu-id="693e3-150">En algunos casos, las propiedades de directivas no se utilizan con Office 365, mientras que otros sólo pueden administrarse por personal de soporte técnico de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="693e3-150">In some cases, properties of policies are not used with Office 365, while others can only be managed by Microsoft support personnel.</span></span> 
  
<span data-ttu-id="693e3-p108">Con Skype para los negocios en línea, los usuarios deben administrarse mediante una directiva de algún tipo. Si una propiedad válida relacionadas con la política está en blanco, significa que el usuario en cuestión está administrando una directiva global, que es una directiva que se aplica automáticamente a un usuario, a menos que él o ella se asigna específicamente una directiva por usuario. Porque no vemos una directiva de cliente para una cuenta de usuario, se administra la directiva global. Puede determinar la directiva de cliente global con este comando:</span><span class="sxs-lookup"><span data-stu-id="693e3-p108">With Skype for Business Online, users must be managed by a policy of some kind. If a valid policy-related property is blank, that means that the user in question is being managed by a global policy, which is a policy that is automatically applied to a user unless he or she is specifically assigned a per-user policy. Because we don't see a client policy listed for a user account, it is managed by the global policy. You can determine the global client policy with this command:</span></span>
  
```
Get-CsClientPolicy -Identity "Global"
```

## <a name="see-also"></a><span data-ttu-id="693e3-155">Consulte también</span><span class="sxs-lookup"><span data-stu-id="693e3-155">See also</span></span>

#### 

[<span data-ttu-id="693e3-156">Administrar Skype Empresarial Online con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="693e3-156">Manage Skype for Business Online with Office 365 PowerShell</span></span>](manage-skype-for-business-online-with-office-365-powershell.md)
  
[<span data-ttu-id="693e3-157">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="693e3-157">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="693e3-158">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="693e3-158">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

