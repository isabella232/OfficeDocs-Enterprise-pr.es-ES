---
title: Preparar un dominio que no sean enrutables para sincronización de directorios
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365E_SetupDirSyncLocalDir
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: e7968303-c234-46c4-b8b0-b5c93c6d57a7
description: Obtenga información sobre qué hacer si tiene un dominio que no sean routale asociado con los usuarios locales antes de sincronizar con Office 365.
ms.openlocfilehash: 62779ba879522177ba15a491644ab42f5961ece0
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542971"
---
# <a name="prepare-a-non-routable-domain-for-directory-synchronization"></a><span data-ttu-id="d16d9-103">Preparar un dominio que no sean enrutables para sincronización de directorios</span><span class="sxs-lookup"><span data-stu-id="d16d9-103">Prepare a non-routable domain for directory synchronization</span></span>
<span data-ttu-id="d16d9-p101">Al sincronizar el directorio local con Office 365 necesita tener un dominio verificado en Azure Active Directory. Sólo el usuario Principal nombres (UPN) que están asociados con el dominio local se sincronizan. Sin embargo, cualquier UPN que contiene un dominio que no sean enrutables, por ejemplo local (como billa@contoso.local), se sincronizará con un. dominio onmicrosoft.com (como billa@contoso.onmicrosoft.com).</span><span class="sxs-lookup"><span data-stu-id="d16d9-p101">When you synchronize your on-premises directory with Office 365 you have to have a verified domain in Azure Active Directory. Only the User Principal Names (UPN) that are associated with the on-premises domain are synchronized. However, any UPN that contains an non-routable domain, for example .local (like billa@contoso.local), will be synchronized to an .onmicrosoft.com domain (like billa@contoso.onmicrosoft.com).</span></span> 

<span data-ttu-id="d16d9-107">Si actualmente usa un dominio local para las cuentas de usuario en Active Directory, se recomienda cambiarlos para utilizar un dominio comprobado (como billa@contoso.com) con el fin de sincronizar correctamente con su dominio de Office 365.</span><span class="sxs-lookup"><span data-stu-id="d16d9-107">If you currently use a .local domain for your user accounts in Active Directory it's recommended that you change them to use a verified domain (like billa@contoso.com) in order to properly sync with your Office 365 domain.</span></span>
  
## <a name="what-if-i-only-have-a-local-on-premises-domain"></a><span data-ttu-id="d16d9-108">¿Qué ocurre si sólo tiene un dominio local de local?</span><span class="sxs-lookup"><span data-stu-id="d16d9-108">What if I only have a .local on-premises domain?</span></span>

<span data-ttu-id="d16d9-p102">La herramienta más reciente que puede utilizar para la sincronización de Active Directory para Azure Active Directory se denomina Connect de Azure AD. Para obtener más información, vea [integración de sus identidades local con Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=624168).</span><span class="sxs-lookup"><span data-stu-id="d16d9-p102">The most recent tool you can use for synchronizing your Active Directory to Azure Active Directory is named Azure AD Connect. For more information, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=624168).</span></span>
  
<span data-ttu-id="d16d9-p103">Conectar de Azure AD sincroniza UPN y la contraseña de los usuarios para que los usuarios pueden iniciar sesión con las mismas credenciales que usan local. Sin embargo, Azure Connect AD sincroniza sólo a los usuarios de dominios que se comprueban por Office 365. Esto significa que el dominio también se comprueba Azure Active Directory porque se administran las identidades de Office 365 Azure Active Directory. En otras palabras, el dominio debe ser un dominio de Internet válido (por ejemplo, .com, .org,. NET, .us, etcetera). Si su Active Directory interno sólo usa un dominio no se puede enrutar (por ejemplo, local), posiblemente esto no puede coincidir con el dominio verificado que tiene en Office 365. Puede solucionar este problema cambiando el dominio principal en sus instalaciones en Active Directory o mediante la adición de uno o varios sufijos UPN.</span><span class="sxs-lookup"><span data-stu-id="d16d9-p103">Azure AD Connect synchronizes your users' UPN and password so that users can sign in with the same credentials they use on-premises. However, Azure AD Connect only synchronizes users to domains that are verified by Office 365. This means that the domain also is verified by Azure Active Directory because Office 365 identities are managed by Azure Active Directory. In other words, the domain has to be a valid Internet domain (for example, .com, .org, .net, .us, etc.). If your internal Active Directory only uses a non-routable domain (for example, .local), this can't possibly match the verified domain you have on Office 365. You can fix this issue by either changing your primary domain in your on premises Active Directory, or by adding one or more UPN suffixes.</span></span>
  
### <a name="change-your-primary-domain"></a><span data-ttu-id="d16d9-117">**Cambiar su dominio principal**</span><span class="sxs-lookup"><span data-stu-id="d16d9-117">**Change your primary domain**</span></span>

<span data-ttu-id="d16d9-p104">Cambie su dominio principal a un dominio que se haya comprobado en Office 365, por ejemplo, contoso.com. A continuación, se actualiza cada usuario que tiene el dominio contoso.local a contoso.com. Para obtener instrucciones, vea [Funcionamiento de la cambiar el nombre de dominio](https://go.microsoft.com/fwlink/p/?LinkId=624174). Sin embargo, esto es un proceso muy implicado, y una solución más fácil es [UPN agregar sufijos y actualizar los usuarios a ellos](prepare-a-non-routable-domain-for-directory-synchronization.md#bk_register), como se muestra en la siguiente sección.</span><span class="sxs-lookup"><span data-stu-id="d16d9-p104">Change your primary domain to a domain you have verified in Office 365, for example, contoso.com. Every user that has the domain contoso.local is then updated to contoso.com. For instructions, see [How Domain Rename Works](https://go.microsoft.com/fwlink/p/?LinkId=624174). This is a very involved process, however, and an easier solution is to [Add UPN suffixes and update your users to them](prepare-a-non-routable-domain-for-directory-synchronization.md#bk_register), as shown in the following section.</span></span>
  
### <a name="add-upn-suffixes-and-update-your-users-to-them"></a><span data-ttu-id="d16d9-122">**Agregar sufijos UPN y actualizar los usuarios a ellos**</span><span class="sxs-lookup"><span data-stu-id="d16d9-122">**Add UPN suffixes and update your users to them**</span></span>

<span data-ttu-id="d16d9-p105">Puede resolver el problema. local mediante el registro de nuevo sufijo UPN o sufijos en Active Directory para que coincida con el dominio (o dominios) ha verificado en Office 365. Después de registrar el nuevo sufijo, actualice el usuario UPN para reemplazar el local con el nuevo nombre de dominio, por ejemplo, para que una cuenta de usuario tiene el aspecto billa@contoso.com.</span><span class="sxs-lookup"><span data-stu-id="d16d9-p105">You can solve the .local problem by registering new UPN suffix or suffixes in Active Directory to match the domain (or domains) you verified in Office 365. After you register the new suffix, you update the user UPNs to replace the .local with the new domain name for example so that a user account looks like billa@contoso.com.</span></span>
  
<span data-ttu-id="d16d9-125">Después de haber actualizado el UPN para usar el dominio verificado, está listo para sincronizar su Active Directory local con Office 365.</span><span class="sxs-lookup"><span data-stu-id="d16d9-125">After you have updated the UPNs to use the verified domain,you are ready to synchronize your on-premises Active Directory with Office 365.</span></span>
  
 <span data-ttu-id="d16d9-126">**Paso 1: Agregar un nuevo sufijo UPN**</span><span class="sxs-lookup"><span data-stu-id="d16d9-126">**Step 1: Add the new UPN suffix**</span></span>
  
1. <span data-ttu-id="d16d9-127">En el servidor que ejecuta los servicios de dominio de Active Directory (AD DS) en, en el administrador del servidor, elija **Herramientas** \> **y confianzas de dominios de Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="d16d9-127">On the server that Active Directory Domain Services (AD DS) runs on, in the Server Manager choose **Tools** \> **Active Directory Domains and Trusts**.</span></span>
    
    <span data-ttu-id="d16d9-128">**O bien, si no dispone de Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="d16d9-128">**Or, if you don't have Windows Server 2012**</span></span>
    
    <span data-ttu-id="d16d9-129">Presione la **tecla de Windows + R** para abrir el cuadro de diálogo **Ejecutar** y, a continuación, escriba en Domain.msc y, a continuación, elija **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="d16d9-129">Press **Windows key + R** to open the **Run** dialog, and then type in Domain.msc, and then choose **OK**.</span></span>
    
    ![Elija relaciones de confianza y dominios de Active Directory.](media/46b6e007-9741-44af-8517-6f682e0ac974.png)
  
2. <span data-ttu-id="d16d9-131">En la ventana **y confianzas de dominios de Active Directory** , secundario **y confianzas de dominios de Active Directory**y, a continuación, elija **Propiedades**.</span><span class="sxs-lookup"><span data-stu-id="d16d9-131">On the **Active Directory Domains and Trusts** window, right-click **Active Directory Domains and Trusts**, and then choose **Properties**.</span></span>
    
    ![El botón secundario ActiveDirectory dominios y confianzas y elija Propiedades](media/39d20812-ffb5-4ba9-8d7b-477377ac360d.png)
  
3. <span data-ttu-id="d16d9-133">En la ficha **Sufijos UPN** , en el cuadro **Sufijos UPN de alternativa** , escriba el nuevo sufijo UPN o sufijos y, a continuación, elija **Agregar** \> **Aplicar**.</span><span class="sxs-lookup"><span data-stu-id="d16d9-133">On the **UPN Suffixes** tab, in the **Alternative UPN Suffixes** box, type your new UPN suffix or suffixes, and then choose **Add** \> **Apply**.</span></span>
    
    ![Agregar un nuevo sufijo UPN](media/a4aaf919-7adf-469a-b93f-83ef284c0915.PNG)
  
    <span data-ttu-id="d16d9-135">Elija **Aceptar** cuando haya terminado de agregar sufijos.</span><span class="sxs-lookup"><span data-stu-id="d16d9-135">Choose **OK** when you're done adding suffixes.</span></span> 
    
 <span data-ttu-id="d16d9-136">**Paso 2: Cambiar el sufijo UPN para los usuarios existentes**</span><span class="sxs-lookup"><span data-stu-id="d16d9-136">**Step 2: Change the UPN suffix for existing users**</span></span>
  
1. <span data-ttu-id="d16d9-137">En el servidor que ejecuta los servicios de dominio de Active Directory (AD DS) en, en el administrador del servidor, elija **Herramientas** \> **y equipos de Active Directory Active Directory Users**.</span><span class="sxs-lookup"><span data-stu-id="d16d9-137">On the server that Active Directory Domain Services (AD DS) runs on, in the Server Manager choose **Tools** \> **Active Directory Active Directory Users and Computers**.</span></span>
    
    <span data-ttu-id="d16d9-138">**O bien, si no dispone de Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="d16d9-138">**Or, if you don't have Windows Server 2012**</span></span>
    
    <span data-ttu-id="d16d9-139">Presione la **tecla de Windows + R** para abrir el cuadro de diálogo **Ejecutar** y, a continuación, escriba dsa.msc y, a continuación, haga clic en **Aceptar**</span><span class="sxs-lookup"><span data-stu-id="d16d9-139">Press **Windows key + R** to open the **Run** dialog, and then type in Dsa.msc, and then click **OK**</span></span>
    
2. <span data-ttu-id="d16d9-140">Seleccione un usuario, con el botón secundario y, a continuación, elija **Propiedades**.</span><span class="sxs-lookup"><span data-stu-id="d16d9-140">Select a user, right-click, and then choose **Properties**.</span></span>
    
3. <span data-ttu-id="d16d9-141">En la ficha de **cuenta** , en la lista desplegable de sufijos UPN, seleccione el sufijo UPN nuevo y, a continuación, elija **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="d16d9-141">On the **Account** tab, in the UPN suffix drop-down list, choose the new UPN suffix, and then choose **OK**.</span></span>
    
    ![Agregar un sufijo UPN nuevo para un usuario](media/54876751-49f0-48cc-b864-2623c4835563.png)
  
4. <span data-ttu-id="d16d9-143">Siga estos pasos para cada usuario.</span><span class="sxs-lookup"><span data-stu-id="d16d9-143">Complete these steps for every user.</span></span>
    
    <span data-ttu-id="d16d9-144">De forma alternativa masiva de actualización el UPN sufijos [también se puede usar Windows PowerShell para cambiar el sufijo UPN para todos los usuarios](prepare-a-non-routable-domain-for-directory-synchronization.md#BK_Posh).</span><span class="sxs-lookup"><span data-stu-id="d16d9-144">Alternately you can bulk update the UPN suffixes [You can also use Windows PowerShell to change the UPN suffix for all users](prepare-a-non-routable-domain-for-directory-synchronization.md#BK_Posh).</span></span>
    
### <a name="you-can-also-use-windows-powershell-to-change-the-upn-suffix-for-all-users"></a><span data-ttu-id="d16d9-145">**También puede usar Windows PowerShell para cambiar el sufijo UPN para todos los usuarios**</span><span class="sxs-lookup"><span data-stu-id="d16d9-145">**You can also use Windows PowerShell to change the UPN suffix for all users**</span></span>

<span data-ttu-id="d16d9-p106">Si tiene una gran cantidad de usuarios que se debe actualizar, es más fácil de usar Windows PowerShell. En el ejemplo siguiente se utiliza los cmdlets [Get-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312) y [Set-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624313) para cambiar todos los sufijos de contoso.local a contoso.com.</span><span class="sxs-lookup"><span data-stu-id="d16d9-p106">If you have a lot of users to update, it is easier to use Windows PowerShell. The following example uses the cmdlets [Get-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312) and [Set-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624313) to change all contoso.local suffixes to contoso.com.</span></span> 

<span data-ttu-id="d16d9-148">Ejecute los siguientes comandos de Windows PowerShell para actualizar todos los sufijos de contoso.local a contoso.com:</span><span class="sxs-lookup"><span data-stu-id="d16d9-148">Run the following Windows PowerShell commands to update all contoso.local suffixes to contoso.com:</span></span>
    
  ```
  $LocalUsers = Get-ADUser -Filter {UserPrincipalName -like '*contoso.local'} -Properties userPrincipalName -ResultSetSize $null
  ```

  ```
  $LocalUsers | foreach {$newUpn = $_.UserPrincipalName.Replace("contoso.local","contoso.com"); $_ | Set-ADUser -UserPrincipalName $newUpn}
  ```
<span data-ttu-id="d16d9-149">Consulte el [módulo de Active Directory de Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=624314) para obtener más información acerca del uso de Windows PowerShell en Active Directory.</span><span class="sxs-lookup"><span data-stu-id="d16d9-149">See [Active Directory Windows PowerShell module](https://go.microsoft.com/fwlink/p/?LinkId=624314) to learn more about using Windows PowerShell in Active Directory.</span></span> 

