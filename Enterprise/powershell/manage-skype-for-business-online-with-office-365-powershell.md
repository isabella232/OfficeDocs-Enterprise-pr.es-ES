---
title: Administrar Skype Empresarial Online con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/13/2018
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 'Resumen: use PowerShell de Office 365 para administrar directivas de Skype Empresarial Online, directivas por usuario y opciones de reunión.'
ms.openlocfilehash: 33c7247686cc8eb308b8db6d4900c89f693004fb
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068736"
---
# <a name="manage-skype-for-business-online-with-office-365-powershell"></a><span data-ttu-id="a8fa1-103">Administrar Skype Empresarial Online con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="a8fa1-103">Manage Skype for Business Online with Office 365 PowerShell</span></span>

 <span data-ttu-id="a8fa1-104">**Resumen:** use PowerShell de Office 365 para administrar directivas de Skype Empresarial Online, directivas por usuario y opciones de reunión.</span><span class="sxs-lookup"><span data-stu-id="a8fa1-104">**Summary:** Use Office 365 PowerShell to manage Skype for Business Online policies, per-user policies, and meeting settings.</span></span>
  
<span data-ttu-id="a8fa1-105">Una de las tareas principales de cualquier administrador de Skype Empresarial Online es administrar las directivas.</span><span class="sxs-lookup"><span data-stu-id="a8fa1-105">One of the primary tasks of any Skype for Business Online administrator is managing policies.</span></span> <span data-ttu-id="a8fa1-106">Aunque puede realizar algunas de estas tareas en el centro de administración de Office 365, otras tareas son mucho más rápidas y sencillas en PowerShell de Office 365.</span><span class="sxs-lookup"><span data-stu-id="a8fa1-106">Although you can accomplish some of these tasks in the Office 365 Admin center, other tasks are much quicker and easier in Office 365 PowerShell.</span></span> 

## <a name="before-you-start"></a><span data-ttu-id="a8fa1-107">Antes de comenzar</span><span class="sxs-lookup"><span data-stu-id="a8fa1-107">Before you start</span></span>

<span data-ttu-id="a8fa1-108">Descargue e instale el [módulo de conector de Skype empresarial online](https://www.microsoft.com/en-us/download/details.aspx?id=39366)y, a continuación, reinicie el equipo si se le pide.</span><span class="sxs-lookup"><span data-stu-id="a8fa1-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/en-us/download/details.aspx?id=39366), and then restart your computer if prompted.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a><span data-ttu-id="a8fa1-109">Conectarse con el nombre y la contraseña de una cuenta de administrador de Skype empresarial online</span><span class="sxs-lookup"><span data-stu-id="a8fa1-109">Connect using a Skype for Business Online administrator account name and password</span></span>

1. <span data-ttu-id="a8fa1-110">Abra un símbolo del sistema de Windows PowerShell y ejecute los siguientes comandos:</span><span class="sxs-lookup"><span data-stu-id="a8fa1-110">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
  ```
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="a8fa1-111">En el cuadro de diálogo solicitud de credenciales para **Windows PowerShell** , escriba el nombre y la contraseña de la cuenta de administrador en Skype empresarial online y, a continuación, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="a8fa1-111">In the **Windows PowerShell Credential Request** dialog box, type your Skype for Business Online administrator account name and password, and then click **OK**.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication"></a><span data-ttu-id="a8fa1-112">Conectarse con una cuenta de administrador de Skype empresarial online con la autenticación multifactor</span><span class="sxs-lookup"><span data-stu-id="a8fa1-112">Connect using a Skype for Business Online administrator account with multifactor authentication</span></span>

1. <span data-ttu-id="a8fa1-113">Abra un símbolo del sistema de Windows PowerShell y ejecute los siguientes comandos:</span><span class="sxs-lookup"><span data-stu-id="a8fa1-113">Open a Windows PowerShell command prompt and run the following commands:</span></span>

  ```
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="a8fa1-114">Cuando se lo solicite el comando **New-CsOnlineSession** , escriba el nombre de la cuenta de administrador en Skype empresarial online.</span><span class="sxs-lookup"><span data-stu-id="a8fa1-114">When prompted by the **New-CsOnlineSession** command, enter your Skype for Business Online administrator account name.</span></span>

3. <span data-ttu-id="a8fa1-115">En el cuadro de diálogo **iniciar sesión en su cuenta** , escriba su contraseña de administrador en línea de Skype empresarial y, a continuación, haga clic en **iniciar sesión**.</span><span class="sxs-lookup"><span data-stu-id="a8fa1-115">In the **Sign in to your account** dialog box, type your Skype for Business Online administrator password, and then click **Sign in**.</span></span>

4. <span data-ttu-id="a8fa1-116">Siga las instrucciones del cuadro de diálogo **iniciar sesión en su cuenta** para proporcionar información de autenticación adicional, como un código de comprobación, y haga clic en **comprobar**.</span><span class="sxs-lookup"><span data-stu-id="a8fa1-116">Follow the instructions in the **Sign in to your account** dialog box to provide additional authentication information, such as a verification code, and then click **Verify**.</span></span>

<span data-ttu-id="a8fa1-117">Para obtener más información, consulte los temas siguientes:</span><span class="sxs-lookup"><span data-stu-id="a8fa1-117">For more information, see the following topics:</span></span>
  
- [<span data-ttu-id="a8fa1-118">Administrar Skype para políticas de negocios en línea con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a8fa1-118">Manage Skype for Business Online policies with Office 365 PowerShell</span></span>](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [<span data-ttu-id="a8fa1-119">Asignar cada usuario Skype para las políticas de negocios en línea con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a8fa1-119">Assign per-user Skype for Business Online policies with Office 365 PowerShell</span></span>](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a><span data-ttu-id="a8fa1-120">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a8fa1-120">See also</span></span>

[<span data-ttu-id="a8fa1-121">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="a8fa1-121">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="a8fa1-122">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="a8fa1-122">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

[<span data-ttu-id="a8fa1-123">Referencias de cmdlets de PowerShell de Skype empresarial</span><span class="sxs-lookup"><span data-stu-id="a8fa1-123">Skype for Business PowerShell cmdlet references</span></span>](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

