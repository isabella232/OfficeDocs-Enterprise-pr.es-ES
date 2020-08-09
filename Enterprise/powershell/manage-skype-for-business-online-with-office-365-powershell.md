---
title: Administrar Skype Empresarial Online con PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 'Resumen: Use PowerShell para Microsoft 365 para administrar las directivas de Skype Empresarial Online, directivas por usuario y opciones de reunión.'
ms.openlocfilehash: 10587dad171c3df9de6985ad314bc1791080b8a1
ms.sourcegitcommit: 839236443410eb804372c4aae969ac9a82ba683b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2020
ms.locfileid: "46592214"
---
# <a name="manage-skype-for-business-online-with-powershell"></a><span data-ttu-id="1b139-103">Administrar Skype Empresarial Online con PowerShell</span><span class="sxs-lookup"><span data-stu-id="1b139-103">Manage Skype for Business Online with PowerShell</span></span>

<span data-ttu-id="1b139-104">*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="1b139-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="1b139-105">Una de las tareas principales de cualquier administrador de Skype Empresarial Online es administrar directivas.</span><span class="sxs-lookup"><span data-stu-id="1b139-105">One of the primary tasks of any Skype for Business Online administrator is managing policies.</span></span> <span data-ttu-id="1b139-106">Aunque puede realizar algunas de estas tareas en el Centro de administración de Microsoft 365, otras tareas son mucho más rápidas y fáciles en PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1b139-106">Although you can accomplish some of these tasks in the Microsoft 365 admin center, other tasks are much quicker and easier in PowerShell.</span></span> 

## <a name="before-you-start"></a><span data-ttu-id="1b139-107">Antes de comenzar</span><span class="sxs-lookup"><span data-stu-id="1b139-107">Before you start</span></span>

<span data-ttu-id="1b139-108">Descargar e instalar el [módulo de conector de Skype Empresarial Online](https://www.microsoft.com/download/details.aspx?id=39366), y luego reiniciar el equipo.</span><span class="sxs-lookup"><span data-stu-id="1b139-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/download/details.aspx?id=39366), and then restart your computer.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a><span data-ttu-id="1b139-109">Conectarse con el nombre y contraseña de una cuenta de administrador de Skype Empresarial Online.</span><span class="sxs-lookup"><span data-stu-id="1b139-109">Connect using a Skype for Business Online administrator account name and password</span></span>

1. <span data-ttu-id="1b139-110">Abra el símbolo del sistema de Windows PowerShell y ejecute los siguientes comandos:</span><span class="sxs-lookup"><span data-stu-id="1b139-110">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
   ```powershell
   Import-Module SkypeOnlineConnector
   $userCredential = Get-Credential
   $sfbSession = New-CsOnlineSession -Credential $userCredential
   Import-PSSession $sfbSession
   ```

2. <span data-ttu-id="1b139-111">En el cuadro de diálogo **Solicitud de credenciales para Windows PowerShell**, escriba el nombre y la contraseña de su cuenta de administrador de Skype Empresarial Online y, a continuación, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="1b139-111">In the **Windows PowerShell Credential Request** dialog box, type your Skype for Business Online administrator account name and password, and then click **OK**.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multi-factor-authentication"></a><span data-ttu-id="1b139-112">Conectarse con una cuenta de administrador de Skype Empresarial Online mediante la autenticación multifactor.</span><span class="sxs-lookup"><span data-stu-id="1b139-112">Connect using a Skype for Business Online administrator account with multi-factor authentication</span></span>

1. <span data-ttu-id="1b139-113">Abra el símbolo del sistema de Windows PowerShell y ejecute los siguientes comandos:</span><span class="sxs-lookup"><span data-stu-id="1b139-113">Open a Windows PowerShell command prompt and run the following commands:</span></span>

   ```powershell
   Import-Module SkypeOnlineConnector
   $sfbSession = New-CsOnlineSession
   Import-PSSession $sfbSession
   ```

2. <span data-ttu-id="1b139-114">Cuando aparezca el comando **New-CsOnlineSession**, escriba el nombre de su cuenta de administrador de Skype Empresarial Online.</span><span class="sxs-lookup"><span data-stu-id="1b139-114">When prompted by the **New-CsOnlineSession** command, enter your Skype for Business Online administrator account name.</span></span>

3. <span data-ttu-id="1b139-115">En el cuadro de diálogo **Iniciar sesión en su cuenta**, escriba la contraseña de administrador de Skype Empresarial Online y, a continuación, haga clic en **Iniciar sesión**.</span><span class="sxs-lookup"><span data-stu-id="1b139-115">In the **Sign in to your account** dialog box, type your Skype for Business Online administrator password, and then click **Sign in**.</span></span>

4. <span data-ttu-id="1b139-116">Siga las instrucciones del cuadro de diálogo **Iniciar sesión en su cuenta** para proporcionar información de autenticación adicional, como el código de verificación, y luego haga clic en **Verificar**.</span><span class="sxs-lookup"><span data-stu-id="1b139-116">Follow the instructions in the **Sign in to your account** dialog box to provide additional authentication information, such as a verification code, and then click **Verify**.</span></span>

<span data-ttu-id="1b139-117">Para obtener más información, consulte los siguientes temas:</span><span class="sxs-lookup"><span data-stu-id="1b139-117">For more information, see the following topics:</span></span>
  
- [<span data-ttu-id="1b139-118">Administrar las directivas de Skype Empresarial Online con PowerShell</span><span class="sxs-lookup"><span data-stu-id="1b139-118">Manage Skype for Business Online policies with PowerShell</span></span>](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [<span data-ttu-id="1b139-119">Asignar directivas a cada usuario de Skype Empresarial Online con PowerShell</span><span class="sxs-lookup"><span data-stu-id="1b139-119">Assign per-user Skype for Business Online policies with PowerShell</span></span>](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a><span data-ttu-id="1b139-120">Consulte también</span><span class="sxs-lookup"><span data-stu-id="1b139-120">See also</span></span>

[<span data-ttu-id="1b139-121">Administrar Microsoft 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="1b139-121">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="1b139-122">Introducción a PowerShell para Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="1b139-122">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)

[<span data-ttu-id="1b139-123">Referencias de cmdlet de PowerShell de Skype Empresarial</span><span class="sxs-lookup"><span data-stu-id="1b139-123">Skype for Business PowerShell cmdlet references</span></span>](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

