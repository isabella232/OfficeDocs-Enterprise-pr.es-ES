---
title: Preparar un dominio no enrutable para la sincronización de directorios
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365E_SetupDirSyncLocalDir
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: e7968303-c234-46c4-b8b0-b5c93c6d57a7
description: Obtenga información sobre qué hacer si tiene un dominio no routale asociado a los usuarios locales antes de sincronizar con Microsoft 365.
ms.openlocfilehash: 148d7e1abdeeeea11c838697bbc957e2937ea7f8
ms.sourcegitcommit: c112869b3ecc0f574b7054ee1edc8c57132f8237
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2020
ms.locfileid: "44736018"
---
# <a name="prepare-a-non-routable-domain-for-directory-synchronization"></a>Preparar un dominio no enrutable para la sincronización de directorios
Al sincronizar el directorio local con Microsoft 365, debe tener un dominio comprobado en Azure Active Directory (Azure AD). Solo se sincronizan los nombres principales de usuario (UPN) asociados con el dominio local. Sin embargo, cualquier UPN que contenga un dominio no enrutable, por ejemplo,. local (como billa@contoso. local), se sincronizará con un dominio. onmicrosoft.com (como billa@contoso.onmicrosoft.com). 

Si actualmente usa un dominio. local para sus cuentas de usuario en servicios de dominio de Active Directory (AD DS), se recomienda que los cambie para usar un dominio comprobado (como billa@contoso.com) para poder sincronizar correctamente con su dominio de Microsoft 365.
  
## <a name="what-if-i-only-have-a-local-on-premises-domain"></a>¿Qué ocurre si solo tengo un dominio local local?

La herramienta más reciente que puede usar para sincronizar AD DS con Azure AD se denomina Azure AD Connect. Para obtener más información, consulte [integración de las identidades locales con Azure ad](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad).
  
Azure AD Connect sincroniza el UPN y la contraseña de los usuarios para que los usuarios puedan iniciar sesión con las mismas credenciales que usan localmente. Sin embargo, Azure AD Connect solo sincroniza los usuarios a dominios que se comprueban con Microsoft 365. Esto significa que Azure AD también comprueba el dominio porque Azure ad administra las identidades 365 de Microsoft. Es decir, el dominio tiene que ser un dominio de Internet válido (por ejemplo,. com,. org, .net,. US, etc.). Si el DS interno de AD solo usa un dominio no enrutable (por ejemplo,. local), esto no puede coincidir con el dominio verificado que tiene en Microsoft 365. Puede solucionar este problema cambiando el dominio principal en su AD DS local o agregando uno o más sufijos UPN.
  
### <a name="change-your-primary-domain"></a>**Cambiar el dominio principal**

Cambie el dominio principal a un dominio que haya comprobado en Microsoft 365, por ejemplo, contoso.com. A continuación, se actualiza a contoso.com todos los usuarios que tengan el dominio contoso. local. Para obtener instrucciones, vea [Cómo funciona el cambio de nombre de dominio](https://go.microsoft.com/fwlink/p/?LinkId=624174). Sin embargo, este proceso es muy complicado y en la siguiente sección se describe una solución más sencilla.
  
### <a name="add-upn-suffixes-and-update-your-users-to-them"></a>**Agregar sufijos UPN y actualizar a los usuarios a ellos**

Puede resolver el problema. local registrando los sufijos UPN nuevos o sufijos en AD DS para que se correspondan con el dominio (o los dominios) que comprobó en Microsoft 365. Después de registrar el nuevo sufijo, actualice el usuario UPN para reemplazar el. local por el nuevo nombre de dominio por ejemplo para que una cuenta de usuario sea similar a billa@contoso.com.
  
Una vez que haya actualizado los UPN para usar el dominio comprobado, estará preparado para sincronizar AD DS local con Microsoft 365.
  
 **Paso 1: agregar el nuevo sufijo UPN**
  
1. En el controlador de dominio de AD DS, en el administrador de servidores, seleccione **herramientas** \> **dominios y confianzas de Active Directory**.
    
    **O bien, si no tiene Windows Server 2012**
    
    Presione la **tecla Windows + R** para abrir el cuadro de diálogo **Ejecutar** , escriba domain. msc y, a continuación, elija **Aceptar**.
    
    ![Elija dominios y confianzas de Active Directory.](media/46b6e007-9741-44af-8517-6f682e0ac974.png)
  
2. En la ventana **dominios y confianzas de Active** Directory, haga clic con el botón secundario en **dominios y confianzas de Active**Directory y, a continuación, elija **propiedades**.
    
    ![Haga clic con el botón secundario en dominios y confianzas de Active Directory y seleccione Propiedades.](media/39d20812-ffb5-4ba9-8d7b-477377ac360d.png)
  
3. En la ficha **sufijos UPN** , en el cuadro **sufijos UPN alternativos** , escriba el sufijo o los sufijos UPN nuevos y, después, elija **Agregar** \> **aplicación**.
    
    ![Agregar un nuevo sufijo UPN](media/a4aaf919-7adf-469a-b93f-83ef284c0915.PNG)
  
    Haga clic en **Aceptar** cuando termine de agregar sufijos. 
    
 **Paso 2: cambiar el sufijo UPN para los usuarios existentes**
  
1. En el controlador de dominio de AD DS, en el administrador de servidores, seleccione **herramientas** \> **usuarios y equipos de Active Directory**.
    
    **O bien, si no tiene Windows Server 2012**
    
    Presione la **tecla Windows + R** para abrir el cuadro de diálogo **Ejecutar** y, a continuación, escriba DSA. msc y, a continuación, haga clic en **Aceptar** .
    
2. Seleccione un usuario, haga clic con el botón secundario y, a continuación, elija **propiedades**.
    
3. En la pestaña **cuenta** , en la lista desplegable sufijo UPN, elija el nuevo sufijo UPN y elija **Aceptar**.
    
    ![Agregar nuevo sufijo UPN para un usuario](media/54876751-49f0-48cc-b864-2623c4835563.png)
  
4. Complete estos pasos para cada usuario.
    
   
### <a name="you-can-also-use-windows-powershell-to-change-the-upn-suffix-for-all-users"></a>**También puede usar Windows PowerShell para cambiar el sufijo UPN para todos los usuarios**

Si tiene muchos usuarios que actualizar, es más fácil usar Windows PowerShell. En el siguiente ejemplo, se usan los cmdlets [Get-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312) y [set-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624313) para cambiar todos los sufijos contoso. local a contoso.com. 

Opuestos ejemplo, podría ejecutar los siguientes comandos de Windows PowerShell para actualizar todos los sufijos contoso. local a contoso.com:
    
  ```powershell
  $LocalUsers = Get-ADUser -Filter "UserPrincipalName -like '*contoso.local'" -Properties userPrincipalName -ResultSetSize $null
  $LocalUsers | foreach {$newUpn = $_.UserPrincipalName.Replace("@contoso.local","@contoso.com"); $_ | Set-ADUser -UserPrincipalName $newUpn}
  ```

Consulte [Windows PowerShell Module de Active](https://go.microsoft.com/fwlink/p/?LinkId=624314) Directory para obtener más información sobre el uso de Windows POWERSHELL en AD DS. 

