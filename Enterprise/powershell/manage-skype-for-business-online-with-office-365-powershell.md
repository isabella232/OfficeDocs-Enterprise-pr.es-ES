---
title: Administrar Skype empresarial online con PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 'Resumen: Use PowerShell para Microsoft 365 para administrar directivas de Skype empresarial online, directivas por usuario y opciones de reunión.'
ms.openlocfilehash: f66b3186a5b29bbf0756a629b85c626caf2c1e36
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230446"
---
# <a name="manage-skype-for-business-online-with-powershell"></a><span data-ttu-id="c808f-103">Administrar Skype empresarial online con PowerShell</span><span class="sxs-lookup"><span data-stu-id="c808f-103">Manage Skype for Business Online with PowerShell</span></span>

<span data-ttu-id="c808f-104">*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="c808f-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="c808f-105">Una de las tareas principales de cualquier administrador de Skype Empresarial Online es administrar las directivas.</span><span class="sxs-lookup"><span data-stu-id="c808f-105">One of the primary tasks of any Skype for Business Online administrator is managing policies.</span></span> <span data-ttu-id="c808f-106">Aunque puede llevar a cabo algunas de estas tareas en el centro de administración de 365 de Microsoft, otras tareas son mucho más rápidas y fáciles en PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c808f-106">Although you can accomplish some of these tasks in the Microsoft 365 admin center, other tasks are much quicker and easier in PowerShell.</span></span> 

## <a name="before-you-start"></a><span data-ttu-id="c808f-107">Antes de comenzar</span><span class="sxs-lookup"><span data-stu-id="c808f-107">Before you start</span></span>

<span data-ttu-id="c808f-108">Descargue e instale el [módulo de conector de Skype empresarial online](https://www.microsoft.com/download/details.aspx?id=39366)y, a continuación, reinicie el equipo.</span><span class="sxs-lookup"><span data-stu-id="c808f-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/download/details.aspx?id=39366), and then restart your computer.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a><span data-ttu-id="c808f-109">Conectarse con el nombre y la contraseña de una cuenta de administrador de Skype empresarial online</span><span class="sxs-lookup"><span data-stu-id="c808f-109">Connect using a Skype for Business Online administrator account name and password</span></span>

1. <span data-ttu-id="c808f-110">Abra un símbolo del sistema de Windows PowerShell y ejecute los siguientes comandos:</span><span class="sxs-lookup"><span data-stu-id="c808f-110">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
  ```powershell
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="c808f-111">En el cuadro de diálogo **solicitud de credenciales para Windows PowerShell** , escriba el nombre y la contraseña de la cuenta de administrador en Skype empresarial online y, a continuación, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="c808f-111">In the **Windows PowerShell Credential Request** dialog box, type your Skype for Business Online administrator account name and password, and then click **OK**.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multi-factor-authentication"></a><span data-ttu-id="c808f-112">Conectarse con una cuenta de administrador de Skype empresarial online con autenticación multifactor</span><span class="sxs-lookup"><span data-stu-id="c808f-112">Connect using a Skype for Business Online administrator account with multi-factor authentication</span></span>

1. <span data-ttu-id="c808f-113">Abra un símbolo del sistema de Windows PowerShell y ejecute los siguientes comandos:</span><span class="sxs-lookup"><span data-stu-id="c808f-113">Open a Windows PowerShell command prompt and run the following commands:</span></span>

  ```powershell
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="c808f-114">Cuando se lo solicite el comando **New-CsOnlineSession** , escriba el nombre de la cuenta de administrador en Skype empresarial online.</span><span class="sxs-lookup"><span data-stu-id="c808f-114">When prompted by the **New-CsOnlineSession** command, enter your Skype for Business Online administrator account name.</span></span>

3. <span data-ttu-id="c808f-115">En el cuadro de diálogo **iniciar sesión en su cuenta** , escriba su contraseña de administrador en línea de Skype empresarial y, a continuación, haga clic en **iniciar sesión**.</span><span class="sxs-lookup"><span data-stu-id="c808f-115">In the **Sign in to your account** dialog box, type your Skype for Business Online administrator password, and then click **Sign in**.</span></span>

4. <span data-ttu-id="c808f-116">Siga las instrucciones del cuadro de diálogo **iniciar sesión en su cuenta** para proporcionar información de autenticación adicional, como un código de comprobación, y haga clic en **comprobar**.</span><span class="sxs-lookup"><span data-stu-id="c808f-116">Follow the instructions in the **Sign in to your account** dialog box to provide additional authentication information, such as a verification code, and then click **Verify**.</span></span>

<span data-ttu-id="c808f-117">Para obtener más información, vea los siguientes temas:</span><span class="sxs-lookup"><span data-stu-id="c808f-117">For more information, see the following topics:</span></span>
  
- [<span data-ttu-id="c808f-118">Administrar directivas de Skype empresarial online con PowerShell</span><span class="sxs-lookup"><span data-stu-id="c808f-118">Manage Skype for Business Online policies with PowerShell</span></span>](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [<span data-ttu-id="c808f-119">Asignar directivas de Skype empresarial online por usuario con PowerShell</span><span class="sxs-lookup"><span data-stu-id="c808f-119">Assign per-user Skype for Business Online policies with PowerShell</span></span>](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a><span data-ttu-id="c808f-120">Consulte también</span><span class="sxs-lookup"><span data-stu-id="c808f-120">See also</span></span>

[<span data-ttu-id="c808f-121">Administrar Microsoft 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="c808f-121">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="c808f-122">Introducción a PowerShell para Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="c808f-122">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)

[<span data-ttu-id="c808f-123">Referencias de cmdlets de PowerShell de Skype empresarial</span><span class="sxs-lookup"><span data-stu-id="c808f-123">Skype for Business PowerShell cmdlet references</span></span>](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

