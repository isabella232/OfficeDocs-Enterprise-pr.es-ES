---
title: Preparar un dominio no enrutable para la sincronización de directorios
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- O365E_SetupDirSyncLocalDir
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: e7968303-c234-46c4-b8b0-b5c93c6d57a7
description: Obtenga información sobre qué hacer si tiene un dominio no routale asociado a los usuarios locales antes de sincronizar con Office 365.
ms.openlocfilehash: 013d29acdd3761793a93dab1eb8583324ba08591
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072422"
---
# <a name="prepare-a-non-routable-domain-for-directory-synchronization"></a><span data-ttu-id="fbb0f-103">Preparar un dominio no enrutable para la sincronización de directorios</span><span class="sxs-lookup"><span data-stu-id="fbb0f-103">Prepare a non-routable domain for directory synchronization</span></span>
<span data-ttu-id="fbb0f-104">Al sincronizar el directorio local con Office 365, debe tener un dominio comprobado en Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="fbb0f-104">When you synchronize your on-premises directory with Office 365 you have to have a verified domain in Azure Active Directory.</span></span> <span data-ttu-id="fbb0f-105">Solo se sincronizan los nombres principales de usuario (UPN) asociados con el dominio local.</span><span class="sxs-lookup"><span data-stu-id="fbb0f-105">Only the User Principal Names (UPN) that are associated with the on-premises domain are synchronized.</span></span> <span data-ttu-id="fbb0f-106">Sin embargo, cualquier UPN que contenga un dominio no enrutable, por ejemplo,. local (como billa@contoso. local), se sincronizará con un dominio. onmicrosoft.com (como billa@contoso.onmicrosoft.com).</span><span class="sxs-lookup"><span data-stu-id="fbb0f-106">However, any UPN that contains an non-routable domain, for example .local (like billa@contoso.local), will be synchronized to an .onmicrosoft.com domain (like billa@contoso.onmicrosoft.com).</span></span> 

<span data-ttu-id="fbb0f-107">Si actualmente usa un dominio. local para sus cuentas de usuario en Active Directory, se recomienda que los cambie para usar un dominio comprobado (por ejemplo, billa@contoso.com) para poder sincronizar correctamente con su dominio de Office 365.</span><span class="sxs-lookup"><span data-stu-id="fbb0f-107">If you currently use a .local domain for your user accounts in Active Directory it's recommended that you change them to use a verified domain (like billa@contoso.com) in order to properly sync with your Office 365 domain.</span></span>
  
## <a name="what-if-i-only-have-a-local-on-premises-domain"></a><span data-ttu-id="fbb0f-108">¿Qué ocurre si solo tengo un dominio local local?</span><span class="sxs-lookup"><span data-stu-id="fbb0f-108">What if I only have a .local on-premises domain?</span></span>

<span data-ttu-id="fbb0f-109">La herramienta más reciente que puede usar para sincronizar Active Directory con Azure Active Directory se denomina Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="fbb0f-109">The most recent tool you can use for synchronizing your Active Directory to Azure Active Directory is named Azure AD Connect.</span></span> <span data-ttu-id="fbb0f-110">Para obtener más información, consulte [Integración de las identidades locales con Azure Active Directory](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad).</span><span class="sxs-lookup"><span data-stu-id="fbb0f-110">For more information, see [Integrating your on-premises identities with Azure Active Directory](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad).</span></span>
  
<span data-ttu-id="fbb0f-111">Azure AD Connect sincroniza el UPN y la contraseña de los usuarios para que los usuarios puedan iniciar sesión con las mismas credenciales que usan localmente.</span><span class="sxs-lookup"><span data-stu-id="fbb0f-111">Azure AD Connect synchronizes your users' UPN and password so that users can sign in with the same credentials they use on-premises.</span></span> <span data-ttu-id="fbb0f-112">Sin embargo, Azure AD Connect solo sincroniza los usuarios a dominios que se comprueban mediante Office 365.</span><span class="sxs-lookup"><span data-stu-id="fbb0f-112">However, Azure AD Connect only synchronizes users to domains that are verified by Office 365.</span></span> <span data-ttu-id="fbb0f-113">Esto significa que Azure Active Directory también comprueba el dominio porque Azure Active Directory administra las identidades de Office 365.</span><span class="sxs-lookup"><span data-stu-id="fbb0f-113">This means that the domain also is verified by Azure Active Directory because Office 365 identities are managed by Azure Active Directory.</span></span> <span data-ttu-id="fbb0f-114">Es decir, el dominio tiene que ser un dominio de Internet válido (por ejemplo,. com,. org, .net,. US, etc.).</span><span class="sxs-lookup"><span data-stu-id="fbb0f-114">In other words, the domain has to be a valid Internet domain (for example, .com, .org, .net, .us, etc.).</span></span> <span data-ttu-id="fbb0f-115">Si el Active Directory interno solo usa un dominio no enrutable (por ejemplo,. local), no puede coincidir con el dominio verificado que tiene en Office 365.</span><span class="sxs-lookup"><span data-stu-id="fbb0f-115">If your internal Active Directory only uses a non-routable domain (for example, .local), this can't possibly match the verified domain you have on Office 365.</span></span> <span data-ttu-id="fbb0f-116">Puede solucionar este problema cambiando el dominio principal en su Active Directory local o agregando uno o más sufijos UPN.</span><span class="sxs-lookup"><span data-stu-id="fbb0f-116">You can fix this issue by either changing your primary domain in your on premises Active Directory, or by adding one or more UPN suffixes.</span></span>
  
### <a name="change-your-primary-domain"></a><span data-ttu-id="fbb0f-117">**Cambiar el dominio principal**</span><span class="sxs-lookup"><span data-stu-id="fbb0f-117">**Change your primary domain**</span></span>

<span data-ttu-id="fbb0f-118">Cambie el dominio principal a un dominio que haya comprobado en Office 365, por ejemplo, contoso.com.</span><span class="sxs-lookup"><span data-stu-id="fbb0f-118">Change your primary domain to a domain you have verified in Office 365, for example, contoso.com.</span></span> <span data-ttu-id="fbb0f-119">A continuación, se actualiza a contoso.com todos los usuarios que tengan el dominio contoso. local.</span><span class="sxs-lookup"><span data-stu-id="fbb0f-119">Every user that has the domain contoso.local is then updated to contoso.com.</span></span> <span data-ttu-id="fbb0f-120">Para obtener instrucciones, vea [Cómo funciona el cambio de nombre de dominio](https://go.microsoft.com/fwlink/p/?LinkId=624174).</span><span class="sxs-lookup"><span data-stu-id="fbb0f-120">For instructions, see [How Domain Rename Works](https://go.microsoft.com/fwlink/p/?LinkId=624174).</span></span> <span data-ttu-id="fbb0f-121">Sin embargo, este proceso es muy complicado y en la siguiente sección se describe una solución más sencilla.</span><span class="sxs-lookup"><span data-stu-id="fbb0f-121">This is a very involved process, however, and an easier solution is described in the following section.</span></span>
  
### <a name="add-upn-suffixes-and-update-your-users-to-them"></a><span data-ttu-id="fbb0f-122">**Agregar sufijos UPN y actualizar a los usuarios a ellos**</span><span class="sxs-lookup"><span data-stu-id="fbb0f-122">**Add UPN suffixes and update your users to them**</span></span>

<span data-ttu-id="fbb0f-123">Puede resolver el problema. local registrando los sufijos UPN nuevos o sufijos en Active Directory para que se corresponda con el dominio (o los dominios) que comprobó en Office 365.</span><span class="sxs-lookup"><span data-stu-id="fbb0f-123">You can solve the .local problem by registering new UPN suffix or suffixes in Active Directory to match the domain (or domains) you verified in Office 365.</span></span> <span data-ttu-id="fbb0f-124">Después de registrar el nuevo sufijo, actualice el usuario UPN para reemplazar el. local por el nuevo nombre de dominio por ejemplo para que una cuenta de usuario sea similar a billa@contoso.com.</span><span class="sxs-lookup"><span data-stu-id="fbb0f-124">After you register the new suffix, you update the user UPNs to replace the .local with the new domain name for example so that a user account looks like billa@contoso.com.</span></span>
  
<span data-ttu-id="fbb0f-125">Una vez que haya actualizado los UPN para usar el dominio comprobado, estará preparado para sincronizar Active Directory local con Office 365.</span><span class="sxs-lookup"><span data-stu-id="fbb0f-125">After you have updated the UPNs to use the verified domain,you are ready to synchronize your on-premises Active Directory with Office 365.</span></span>
  
 <span data-ttu-id="fbb0f-126">**Paso 1: agregar el nuevo sufijo UPN**</span><span class="sxs-lookup"><span data-stu-id="fbb0f-126">**Step 1: Add the new UPN suffix**</span></span>
  
1. <span data-ttu-id="fbb0f-127">En el servidor en el que se ejecuta servicios de dominio de Active Directory (AD DS), en el administrador del servidor, seleccione **herramientas** \> **dominios y confianzas de Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="fbb0f-127">On the server that Active Directory Domain Services (AD DS) runs on, in the Server Manager choose **Tools** \> **Active Directory Domains and Trusts**.</span></span>
    
    <span data-ttu-id="fbb0f-128">**O bien, si no tiene Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="fbb0f-128">**Or, if you don't have Windows Server 2012**</span></span>
    
    <span data-ttu-id="fbb0f-129">Presione la **tecla Windows + R** para abrir el cuadro de diálogo **Ejecutar** , escriba domain. msc y, a continuación, elija **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="fbb0f-129">Press **Windows key + R** to open the **Run** dialog, and then type in Domain.msc, and then choose **OK**.</span></span>
    
    ![Elija dominios y confianzas de Active Directory.](media/46b6e007-9741-44af-8517-6f682e0ac974.png)
  
2. <span data-ttu-id="fbb0f-131">En la ventana **dominios y confianzas de Active** Directory, haga clic con el botón secundario en **dominios y confianzas de Active**Directory y, a continuación, elija **propiedades**.</span><span class="sxs-lookup"><span data-stu-id="fbb0f-131">On the **Active Directory Domains and Trusts** window, right-click **Active Directory Domains and Trusts**, and then choose **Properties**.</span></span>
    
    ![Haga clic con el botón derecho en dominios y confianzas de ActiveDirectory y seleccione Propiedades.](media/39d20812-ffb5-4ba9-8d7b-477377ac360d.png)
  
3. <span data-ttu-id="fbb0f-133">En la ficha **sufijos UPN** , en el cuadro **sufijos UPN alternativos** , escriba el sufijo o los sufijos UPN nuevos y, después, elija **Agregar** \> **aplicación**.</span><span class="sxs-lookup"><span data-stu-id="fbb0f-133">On the **UPN Suffixes** tab, in the **Alternative UPN Suffixes** box, type your new UPN suffix or suffixes, and then choose **Add** \> **Apply**.</span></span>
    
    ![Agregar un nuevo sufijo UPN](media/a4aaf919-7adf-469a-b93f-83ef284c0915.PNG)
  
    <span data-ttu-id="fbb0f-135">Haga clic en **Aceptar** cuando termine de agregar sufijos.</span><span class="sxs-lookup"><span data-stu-id="fbb0f-135">Choose **OK** when you're done adding suffixes.</span></span> 
    
 <span data-ttu-id="fbb0f-136">**Paso 2: cambiar el sufijo UPN para los usuarios existentes**</span><span class="sxs-lookup"><span data-stu-id="fbb0f-136">**Step 2: Change the UPN suffix for existing users**</span></span>
  
1. <span data-ttu-id="fbb0f-137">En el servidor en el que se ejecutan los servicios de dominio de Active Directory (AD DS), en el administrador del servidor, seleccione **herramientas** \> **usuarios y equipos**de Active Directory Active Directory.</span><span class="sxs-lookup"><span data-stu-id="fbb0f-137">On the server that Active Directory Domain Services (AD DS) runs on, in the Server Manager choose **Tools** \> **Active Directory Active Directory Users and Computers**.</span></span>
    
    <span data-ttu-id="fbb0f-138">**O bien, si no tiene Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="fbb0f-138">**Or, if you don't have Windows Server 2012**</span></span>
    
    <span data-ttu-id="fbb0f-139">Presione la **tecla Windows + R** para abrir el cuadro de diálogo **Ejecutar** y, a continuación, escriba DSA. msc y, a continuación, haga clic en **Aceptar** .</span><span class="sxs-lookup"><span data-stu-id="fbb0f-139">Press **Windows key + R** to open the **Run** dialog, and then type in Dsa.msc, and then click **OK**</span></span>
    
2. <span data-ttu-id="fbb0f-140">Seleccione un usuario, haga clic con el botón secundario y, a continuación, elija **propiedades**.</span><span class="sxs-lookup"><span data-stu-id="fbb0f-140">Select a user, right-click, and then choose **Properties**.</span></span>
    
3. <span data-ttu-id="fbb0f-141">En la pestaña **cuenta** , en la lista desplegable sufijo UPN, elija el nuevo sufijo UPN y elija **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="fbb0f-141">On the **Account** tab, in the UPN suffix drop-down list, choose the new UPN suffix, and then choose **OK**.</span></span>
    
    ![Agregar nuevo sufijo UPN para un usuario](media/54876751-49f0-48cc-b864-2623c4835563.png)
  
4. <span data-ttu-id="fbb0f-143">Complete estos pasos para cada usuario.</span><span class="sxs-lookup"><span data-stu-id="fbb0f-143">Complete these steps for every user.</span></span>
    
   
### <a name="you-can-also-use-windows-powershell-to-change-the-upn-suffix-for-all-users"></a><span data-ttu-id="fbb0f-144">**También puede usar Windows PowerShell para cambiar el sufijo UPN para todos los usuarios**</span><span class="sxs-lookup"><span data-stu-id="fbb0f-144">**You can also use Windows PowerShell to change the UPN suffix for all users**</span></span>

<span data-ttu-id="fbb0f-145">Si tiene muchos usuarios que actualizar, es más fácil usar Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fbb0f-145">If you have a lot of users to update, it is easier to use Windows PowerShell.</span></span> <span data-ttu-id="fbb0f-146">En el siguiente ejemplo, se usan los cmdlets [Get-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312) y [set-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624313) para cambiar todos los sufijos contoso. local a contoso.com.</span><span class="sxs-lookup"><span data-stu-id="fbb0f-146">The following example uses the cmdlets [Get-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312) and [Set-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624313) to change all contoso.local suffixes to contoso.com.</span></span> 

<span data-ttu-id="fbb0f-147">Ejecute los siguientes comandos de Windows PowerShell para actualizar todos los sufijos contoso. local a contoso.com:</span><span class="sxs-lookup"><span data-stu-id="fbb0f-147">Run the following Windows PowerShell commands to update all contoso.local suffixes to contoso.com:</span></span>
    
  ```powershell
  $LocalUsers = Get-ADUser -Filter {UserPrincipalName -like '*contoso.local'} -Properties userPrincipalName -ResultSetSize $null
  $LocalUsers | foreach {$newUpn = $_.UserPrincipalName.Replace("contoso.local","contoso.com"); $_ | Set-ADUser -UserPrincipalName $newUpn}
  ```

<span data-ttu-id="fbb0f-148">Consulte [Windows PowerShell Module de Active](https://go.microsoft.com/fwlink/p/?LinkId=624314) Directory para obtener más información sobre el uso de Windows PowerShell en Active Directory.</span><span class="sxs-lookup"><span data-stu-id="fbb0f-148">See [Active Directory Windows PowerShell module](https://go.microsoft.com/fwlink/p/?LinkId=624314) to learn more about using Windows PowerShell in Active Directory.</span></span> 

