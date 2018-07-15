---
title: Administrar Skype Empresarial Online con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/22/2018
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 'Resumen: use PowerShell de Office 365 para administrar directivas de Skype Empresarial Online, directivas por usuario y opciones de reunión.'
ms.openlocfilehash: f490131491a026961b0a5db312df5780483eadd9
ms.sourcegitcommit: b39b8ae3b4268d6475b54e2fdb62982b2c7d9943
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/12/2018
ms.locfileid: "20319241"
---
# <a name="manage-skype-for-business-online-with-office-365-powershell"></a><span data-ttu-id="4a993-103">Administrar Skype Empresarial Online con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="4a993-103">Manage Skype for Business Online with Office 365 PowerShell</span></span>

 <span data-ttu-id="4a993-104">**Resumen:** use PowerShell de Office 365 para administrar directivas de Skype Empresarial Online, directivas por usuario y opciones de reunión.</span><span class="sxs-lookup"><span data-stu-id="4a993-104">**Summary:** Use Office 365 PowerShell to manage Skype for Business Online policies, per-user policies, and meeting settings.</span></span>
  
<span data-ttu-id="4a993-p101">Es una de las tareas principales de cualquier Skype administrador empresarial en línea de administración de directivas. Aunque puede realizar algunas de estas tareas en el centro de administración de Office 365, otras tareas son mucho más rápido y sencillo en PowerShell de Office 365.</span><span class="sxs-lookup"><span data-stu-id="4a993-p101">One of the primary tasks of any Skype for Business Online administrator is managing policies. Although you can accomplish some of these tasks in the Office 365 Admin center, other tasks are much quicker and easier in Office 365 PowerShell.</span></span> 

## <a name="before-you-start"></a><span data-ttu-id="4a993-107">Antes de comenzar</span><span class="sxs-lookup"><span data-stu-id="4a993-107">Before you start</span></span>

<span data-ttu-id="4a993-108">Descargar e instalar el [Skype para el módulo del conector en línea de negocio](https://www.microsoft.com/en-us/download/details.aspx?id=39366)y, a continuación, reinicie el equipo si se le solicita.</span><span class="sxs-lookup"><span data-stu-id="4a993-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/en-us/download/details.aspx?id=39366), and then restart your computer if prompted.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a><span data-ttu-id="4a993-109">Conectar utilizando un Skype para el nombre de cuenta de administrador empresarial en línea y la contraseña</span><span class="sxs-lookup"><span data-stu-id="4a993-109">Connect using a Skype for Business Online administrator account name and password</span></span>

1. <span data-ttu-id="4a993-110">Abra un símbolo del sistema de Windows PowerShell y ejecute los siguientes comandos:</span><span class="sxs-lookup"><span data-stu-id="4a993-110">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
  ```
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="4a993-111">En el cuadro de diálogo **Solicitud de credenciales de Windows PowerShell** , escriba su Skype para el nombre de la cuenta de administrador empresarial en línea y la contraseña y, a continuación, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="4a993-111">In the **Windows PowerShell Credential Request** dialog box, type your Skype for Business Online administrator account name and password, and then click **OK**.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication"></a><span data-ttu-id="4a993-112">Conectar con un Skype para la cuenta de administrador empresarial en línea con la autenticación multifactor</span><span class="sxs-lookup"><span data-stu-id="4a993-112">Connect using a Skype for Business Online administrator account with multifactor authentication</span></span>

1. <span data-ttu-id="4a993-113">Abra un símbolo del sistema de Windows PowerShell y ejecute los siguientes comandos:</span><span class="sxs-lookup"><span data-stu-id="4a993-113">Open a Windows PowerShell command prompt and run the following commands:</span></span>

  ```
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="4a993-114">Cuando se le solicite el comando **New-CsOnlineSession** , escriba su Skype para el nombre de la cuenta de administrador empresarial en línea.</span><span class="sxs-lookup"><span data-stu-id="4a993-114">When prompted by the **New-CsOnlineSession** command, enter your Skype for Business Online administrator account name.</span></span>

3. <span data-ttu-id="4a993-115">En el cuadro de diálogo **iniciar sesión en su cuenta** , escriba su Skype para contraseña de administrador empresarial en línea y, a continuación, haga clic en **iniciar sesión**.</span><span class="sxs-lookup"><span data-stu-id="4a993-115">In the **Sign in to your account** dialog box, type your Skype for Business Online administrator password, and then click **Sign in**.</span></span>

4. <span data-ttu-id="4a993-116">Siga las instrucciones que aparecen en el cuadro de diálogo **iniciar sesión en su cuenta** para proporcionar información de autenticación adicionales, como un código de comprobación y, a continuación, haga clic en **Comprobar**.</span><span class="sxs-lookup"><span data-stu-id="4a993-116">Follow the instructions in the **Sign in to your account** dialog box to provide additional authentication information, such as a verification code, and then click **Verify**.</span></span>

<span data-ttu-id="4a993-117">Para obtener más información, vea los temas siguientes:</span><span class="sxs-lookup"><span data-stu-id="4a993-117">For more information, see the following topics:</span></span>
  
- [<span data-ttu-id="4a993-118">Administrar Skype para políticas de negocios en línea con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="4a993-118">Manage Skype for Business Online policies with Office 365 PowerShell</span></span>](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [<span data-ttu-id="4a993-119">Asignar cada usuario Skype para las políticas de negocios en línea con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="4a993-119">Assign per-user Skype for Business Online policies with Office 365 PowerShell</span></span>](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a><span data-ttu-id="4a993-120">Consulte también</span><span class="sxs-lookup"><span data-stu-id="4a993-120">See also</span></span>

[<span data-ttu-id="4a993-121">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="4a993-121">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="4a993-122">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="4a993-122">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

