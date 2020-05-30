---
title: Administrar Skype Empresarial Online con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/28/2018
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 'Resumen: use PowerShell de Office 365 para administrar directivas de Skype Empresarial Online, directivas por usuario y opciones de reunión.'
ms.openlocfilehash: f1a5df3802d43755e81465743b81c5fbb9fff7e0
ms.sourcegitcommit: 6c7cc6aca8713e280ae6ff51226dde9db4497401
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2020
ms.locfileid: "44415942"
---
# <a name="manage-skype-for-business-online-with-office-365-powershell"></a><span data-ttu-id="2d894-103">Administrar Skype Empresarial Online con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="2d894-103">Manage Skype for Business Online with Office 365 PowerShell</span></span>

<span data-ttu-id="2d894-104">Una de las tareas principales de cualquier administrador de Skype Empresarial Online es administrar las directivas.</span><span class="sxs-lookup"><span data-stu-id="2d894-104">One of the primary tasks of any Skype for Business Online administrator is managing policies.</span></span> <span data-ttu-id="2d894-105">Aunque puede realizar algunas de estas tareas en el Centro de administración de Microsoft 365, otras tareas son mucho más rápidas y fáciles en PowerShell de Office 365.</span><span class="sxs-lookup"><span data-stu-id="2d894-105">Although you can accomplish some of these tasks in the Microsoft 365 admin center, other tasks are much quicker and easier in Office 365 PowerShell.</span></span> 

## <a name="before-you-start"></a><span data-ttu-id="2d894-106">Antes de comenzar</span><span class="sxs-lookup"><span data-stu-id="2d894-106">Before you start</span></span>

<span data-ttu-id="2d894-107">Descargue e instale el [módulo de conector de Skype empresarial online](https://www.microsoft.com/download/details.aspx?id=39366)y, a continuación, reinicie el equipo.</span><span class="sxs-lookup"><span data-stu-id="2d894-107">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/download/details.aspx?id=39366), and then restart your computer.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a><span data-ttu-id="2d894-108">Conectarse con el nombre y la contraseña de una cuenta de administrador de Skype empresarial online</span><span class="sxs-lookup"><span data-stu-id="2d894-108">Connect using a Skype for Business Online administrator account name and password</span></span>

1. <span data-ttu-id="2d894-109">Abra un símbolo del sistema de Windows PowerShell y ejecute los siguientes comandos:</span><span class="sxs-lookup"><span data-stu-id="2d894-109">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
  ```powershell
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="2d894-110">En el cuadro de diálogo **solicitud de credenciales para Windows PowerShell** , escriba el nombre y la contraseña de la cuenta de administrador en Skype empresarial online y, a continuación, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="2d894-110">In the **Windows PowerShell Credential Request** dialog box, type your Skype for Business Online administrator account name and password, and then click **OK**.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multi-factor-authentication"></a><span data-ttu-id="2d894-111">Conectarse con una cuenta de administrador de Skype empresarial online con autenticación multifactor</span><span class="sxs-lookup"><span data-stu-id="2d894-111">Connect using a Skype for Business Online administrator account with multi-factor authentication</span></span>

1. <span data-ttu-id="2d894-112">Abra un símbolo del sistema de Windows PowerShell y ejecute los siguientes comandos:</span><span class="sxs-lookup"><span data-stu-id="2d894-112">Open a Windows PowerShell command prompt and run the following commands:</span></span>

  ```powershell
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="2d894-113">Cuando se lo solicite el comando **New-CsOnlineSession** , escriba el nombre de la cuenta de administrador en Skype empresarial online.</span><span class="sxs-lookup"><span data-stu-id="2d894-113">When prompted by the **New-CsOnlineSession** command, enter your Skype for Business Online administrator account name.</span></span>

3. <span data-ttu-id="2d894-114">En el cuadro de diálogo **iniciar sesión en su cuenta** , escriba su contraseña de administrador en línea de Skype empresarial y, a continuación, haga clic en **iniciar sesión**.</span><span class="sxs-lookup"><span data-stu-id="2d894-114">In the **Sign in to your account** dialog box, type your Skype for Business Online administrator password, and then click **Sign in**.</span></span>

4. <span data-ttu-id="2d894-115">Siga las instrucciones del cuadro de diálogo **iniciar sesión en su cuenta** para proporcionar información de autenticación adicional, como un código de comprobación, y haga clic en **comprobar**.</span><span class="sxs-lookup"><span data-stu-id="2d894-115">Follow the instructions in the **Sign in to your account** dialog box to provide additional authentication information, such as a verification code, and then click **Verify**.</span></span>

<span data-ttu-id="2d894-116">Para obtener más información, consulte los temas siguientes:</span><span class="sxs-lookup"><span data-stu-id="2d894-116">For more information, see the following topics:</span></span>
  
- [<span data-ttu-id="2d894-117">Administrar Skype para políticas de negocios en línea con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="2d894-117">Manage Skype for Business Online policies with Office 365 PowerShell</span></span>](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [<span data-ttu-id="2d894-118">Asignar cada usuario Skype para las políticas de negocios en línea con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="2d894-118">Assign per-user Skype for Business Online policies with Office 365 PowerShell</span></span>](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a><span data-ttu-id="2d894-119">Vea también</span><span class="sxs-lookup"><span data-stu-id="2d894-119">See also</span></span>

[<span data-ttu-id="2d894-120">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="2d894-120">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="2d894-121">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="2d894-121">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

[<span data-ttu-id="2d894-122">Referencias de cmdlets de PowerShell de Skype empresarial</span><span class="sxs-lookup"><span data-stu-id="2d894-122">Skype for Business PowerShell cmdlet references</span></span>](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

