---
title: Entorno de desarrollo y pruebas de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/02/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 4f6035b8-2da3-4cf9-9657-5284d6364f7a
description: 'Resumen: use esta Guías del entorno de pruebas para crear una suscripción de prueba de Office 365 para evaluación, pruebas o desarrollo.'
ms.openlocfilehash: 2f1856d203e892c98b44ccc1dbe1598d527165de
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2019
ms.locfileid: "34162513"
---
# <a name="office-365-devtest-environment"></a>Entorno de desarrollo y pruebas de Office 365

 **Resumen:** use esta Guías del entorno de pruebas para crear una suscripción de prueba de Office 365 para evaluación, pruebas o desarrollo.
  
Puede usar una suscripción de prueba de Office 365 y crear un entorno de desarrollo y pruebas de Office 365 para las aplicaciones o para demostrar las características y funcionalidades de Office 365. Existen dos versiones:
  
- El entorno de desarrollo y pruebas ligero de Office 365 consiste en una suscripción de prueba de Office 365 a la que puede tener acceso desde su equipo principal.
    
    Use este entorno cuando quiera demostrar rápidamente una característica. Para el entorno de desarrollo y pruebas ligero de Office 365, complete solo las fases 2 y 3 de este artículo.
    
- El entorno de desarrollo y pruebas de una empresa simulada de Office 365 consiste en una suscripción de prueba a Office 365 y una intranet simplificada de una organización conectada a Internet, que se hospeda en los servicios de infraestructura de Microsoft Azure. Puede crear esta configuración completamente en la nube de Microsoft.
    
    Use este entorno cuando quiera demostrar una característica o una aplicación en un entorno que parece una red típica de la organización conectada a Internet, o para las características que requieran este tipo de entorno. Para el entorno de desarrollo y pruebas de una empresa simulada de Office 365, complete las fases 1, 2 y 3 de este artículo.
    
> [!NOTE]
> Es posible que quiera imprimir este artículo para anotar los valores específicos que necesite para usar este entorno durante los 30 días de la suscripción de prueba a Office 365. Puede extender fácilmente la suscripción de prueba otros 30 días. Para un entorno de pruebas y desarrollo permanente, cree una nueva suscripción de pago con un número reducido de licencias. 
  
![Guías del laboratorio de pruebas de Microsoft Cloud](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual de todos los artículos en la pila de la Guía del laboratorio de pruebas de Office 365.
  
## <a name="phase-1-create-the-base-configuration-in-azure"></a>Fase 1: Crear la configuración básica de Azure

Siga las instrucciones que se indican en [Configuración básica del entorno de desarrollo y pruebas](base-configuration-dev-test-environment.md).
  
Necesitará una suscripción de Azure. Para esta configuración, puede usar una [prueba gratuita de Azure](https://azure.microsoft.com/pricing/free-trial/). Si tiene una suscripción de MSDN o Visual Studio, vea [Crédito mensual de Azure para suscriptores de Visual Studio](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).
  
Esta es la configuración resultante.
  
![Configuración básica del entorno de desarrollo y pruebas en Azure](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)


  
Esta configuración básica se compone de las máquinas virtuales DC1, APP1 y CLIENTE1 en una subred de una red virtual de Azure.
  
## <a name="phase-2-create-an-office-365-trial-subscription"></a>Fase 2: Crear una suscripción de prueba a Office 365

Para iniciar la suscripción de prueba a Office 365 E5, primero necesita el nombre de una compañía ficticia y una nueva cuenta Microsoft.
  
1. Le recomendamos que use una variante del nombre de la compañía Contoso para el nombre de su compañía, que es una compañía ficticia usada en contenido de ejemplo de Microsoft, pero no es imprescindible. Anote aquí el nombre de la compañía ficticia: ![](./media/Common-Images/TableLine.png)
    
2. Para registrarse para obtener una nueva cuenta Microsoft, vaya a [https://outlook.com](https://outlook.com) y cree una cuenta con una nueva cuenta y una dirección de correo electrónico. Usará esta cuenta para suscribirse a Office 365.
    
  - Anote aquí el nombre y los apellidos de la nueva cuenta: ![](./media/Common-Images/TableLine.png)
    
  - Anote aquí la dirección de la nueva cuenta de correo electrónico: ![](./media/Common-Images/TableLine.png)@outlook.com
    
### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a>Registrarse para una suscripción de prueba a Office 365 E5

1. Para el entorno de desarrollo y pruebas ligero de Office 365, abra un explorador de Internet en el equipo y vaya a [https://aka.ms/e5trial](https://aka.ms/e5trial). 
    
    Para el entorno de desarrollo y pruebas de Office 365 de la empresa ficticia, conéctese a CLIENTE1 con la cuenta CORP\Usuario1 desde Azure Portal.

    En la pantalla Inicio, ejecute Microsoft Edge y vaya a [https://aka.ms/e5trial](https://aka.ms/e5trial).
    
2. En la página **Bienvenido. Permítanos conocerle**, especifique:
    
  - Su ubicación física
    
  - El nombre y apellidos de la nueva cuenta de Microsoft
    
  - La dirección de la nueva cuenta de correo
    
  - El número de teléfono del trabajo
    
  - El nombre de la compañía ficticia
    
  - El tamaño de la organización (250 a 999 personas)
    
3. Haga clic en **Un solo paso más**.
    
4. En la página **Crear su id. de usuario**, escriba un nombre de usuario basado en la nueva dirección de correo, la empresa ficticia después del signo @ (quite todos los espacios en el nombre) y una contraseña (dos veces) para esta nueva cuenta de Office 365. 
    
    Anote en un lugar seguro la contraseña que escriba.
    
    Anote aquí el nombre de la compañía ficticia, que se denominará **nombre de la organización**: ![](./media/Common-Images/TableLine.png)
    
5. Haga clic en **Crear mi cuenta**.
    
6. En la página **Demuestre. Que. No. Es. Un. Robot.**, escriba el número de teléfono de su teléfono compatible con texto y, después, haga clic en **Enviarme un mensaje**.
    
7. Escriba el código de verificación del mensaje de texto recibido y, después, haga clic en **Siguiente**.
    
8. Anote aquí la URL de la página de inicio de sesión (seleccionar y copiar): ![](./media/Common-Images/TableLine.png)
    
9. Anote aquí el identificador de usuario (seleccionar y copiar): ![](./media/Common-Images/TableLine.png).onmicrosoft.com
    
    Este valor se denominará **nombre de administrador global de Office 365**.
    
10. Cuando vea **Ya está listo**, haga clic.
    
11. En la página siguiente, espere hasta que Office 365 complete la configuración y estén disponibles todos los iconos.
    
Verá la página principal del portal de Office 365, desde donde puede obtener acceso a servicios de Office Online y al Centro de administración de Microsoft 365.
  
Para el entorno de desarrollo y pruebas de una empresa ficticia de Office 365, aquí se muestra la configuración resultante.
  
![El entorno de desarrollo y pruebas de Office 365](media/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
Esta configuración se compone de: 
  
- Las máquinas virtuales DC1, APP1 y CLIENTE1 en una subred de una red virtual de Azure.
    
- Una suscripción de prueba a Office 365 E5.
    
## <a name="phase-3-configure-your-office-365-trial-subscription"></a>Fase 3: Configurar la suscripción de prueba de Office 365

En esta fase, se configura la suscripción a Office 365 con usuarios adicionales y se les asignan licencias de Office 365 E5.
  
Siga las instrucciones que se indican en [Conectarse a PowerShell de Office 365](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-azure-active-directory-powershell-for-graph-module) para conectarse a su suscripción de Office 365 con el módulo Azure Active Directory PowerShell para Graph desde:
  
- Su equipo (para el entorno de desarrollo y pruebas ligero de Office 365).
    
- La máquina virtual CLIENTE1 (para el entorno de desarrollo y pruebas de una empresa ficticia de Office 365).
    
 En el cuadro de diálogo Solicitud de credenciales para Windows PowerShell, escriba el nombre de administrador global de Office 365 (por ejemplo, svalladares@contosotoycompany.onmicrosoft.com) y la contraseña.
  
Rellene el nombre de la organización (ejemplo: contosotoycompany), el código de país de dos caracteres para su ubicación, la contraseña de cuenta común y, después, ejecute los comandos siguientes desde el símbolo del sistema de PowerShell:

```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$commonPW="<common user account password>"
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPW

$userUPN= "user2@" + $orgName + ".onmicrosoft.com"
New-AzureADUser -DisplayName "User 2" -GivenName User -SurName 2 -UserPrincipalName $userUPN -UsageLocation $loc -AccountEnabled $true -PasswordProfile $PasswordProfile -MailNickName "user2"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value "ENTERPRISEPREMIUM" -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign

$userUPN= "user3@" + $orgName + ".onmicrosoft.com"
New-AzureADUser -DisplayName "User 3" -GivenName User -SurName 3 -UserPrincipalName $userUPN -UsageLocation $loc -AccountEnabled $true -PasswordProfile $PasswordProfile -MailNickName "user3"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value "ENTERPRISEPREMIUM" -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign

$userUPN= "user4@" + $orgName + ".onmicrosoft.com"
New-AzureADUser -DisplayName "User 4" -GivenName User -SurName 4 -UserPrincipalName $userUPN -UsageLocation $loc -AccountEnabled $true -PasswordProfile $PasswordProfile -MailNickName "user4"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value "ENTERPRISEPREMIUM" -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

<!--
> [!TIP]
> Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-fe3d7a34) to get a text file that has all the PowerShell commands in this article.
-->

  
## <a name="phase-4-create-three-new-sharepoint-online-team-sites-optional"></a>Fase 4: Crear tres sitios de grupo de SharePoint Online (opcional)

En esta fase, configurará un conjunto de sitios de equipo de SharePoint Online.
  
1. Instale el [Shell de administración de SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=255251) (la versión x64).
    
2. Haga clic en **Inicio**, escriba **sharepoint** y después haga clic en **Shell de administración de SharePoint Online**.
    
3. Rellene el nombre de su organización (ejemplo: contosotoycompany) y después ejecute los comandos siguientes desde el símbolo del sistema del Shell de administración de SharePoint Online para conectar con el servicio de SharePoint Online
```
$orgName="<organization name>"
$spURL="https://" + $orgName + "-admin.sharepoint.com"
Connect-SPOService -Url $spURL
```

4. En el cuadro de diálogo **Shell de administración de Microsoft SharePoint Online**, escriba el nombre del administrador global de Office 365 (por ejemplo, svalladares@contosotoycompany.onmicrosoft.com) y la contraseña y, después, haga clic en **Iniciar sesión**.
    
5. Para crear tres sitios de grupo (Ventas, Producción y Soporte técnico), rellene el nombre de administrador global de Office 365 y, después, ejecute los comandos siguientes desde el símbolo del sistema del Shell de administración de SharePoint Online:
    
  ```
  $owner = "<global administrator account name>"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/sales"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Sales site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/production"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Production site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/support"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Support site collection" -Template "STS#0"
  ```

6. Ejecute este comando para mostrar una lista de las direcciones URL de estos sitios nuevos:
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

7. En Internet Explorer, escriba la dirección URL del sitio de Producción para ver el sitio de grupo predeterminado de SharePoint Online para el departamento de Producción.
    
## <a name="record-values-for-future-reference"></a>Anote los valores para futuras referencias

Anote estos valores para trabajar con o implementar Guías del entorno de pruebas adicionales en este entorno de prueba:
  
- Nombre del administrador global de Office 365: ![](./media/Common-Images/TableLine.png).onmicrosoft.com (del paso 9 de la fase 2)
    
    Guarde también la contraseña de esta cuenta en una ubicación segura.
    
- Nombre de la organización de la suscripción de prueba: ![](./media/Common-Images/TableLine.png) (del paso 4 de la fase 2)
    
- Para mostrar las cuentas de los usuarios 2, 3, 4 y 5, ejecute los siguientes comandos desde el símbolo del sistema del Módulo de Windows Azure Active Directory para Windows PowerShell.
    
  ```
  Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName
  ```

    Anote aquí los nombres de las cuentas:
    
  - Nombre de la cuenta de usuario 2: usuario2@![](./media/Common-Images/TableLine.png).onmicrosoft.com
    
  - Nombre de la cuenta de usuario 3: usuario3@![](./media/Common-Images/TableLine.png).onmicrosoft.com
    
  - Nombre de la cuenta de usuario 4: usuario4@![](./media/Common-Images/TableLine.png).onmicrosoft.com
    
  - Nombre de la cuenta de usuario 5: usuario5@![](./media/Common-Images/TableLine.png).onmicrosoft.com
    
    Guarde también las contraseñas de estas cuentas en una ubicación segura.
    
- (opcional) Para mostrar las direcciones URL de los sitios de grupo de Ventas, Producción y Soporte técnico, ejecute el comando siguiente desde el símbolo del sistema del Shell de administración de SharePoint Online:
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

  - Dirección URL del sitio de producción: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/production
    
  - Dirección URL del sitio de ventas: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/sales
    
  - Dirección URL del sitio de soporte técnico: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/support
    
## <a name="next-steps"></a>Pasos siguientes

Use estos artículos adicionales en el entorno de desarrollo y pruebas de Office 365:
  
- [Configurar la sincronización de directorios para el entorno de desarrollo y pruebas de Office 365](dirsync-for-your-office-365-dev-test-environment.md)
    
- [Autenticación multifactor para el entorno de desarrollo y pruebas de Office 365](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
- [Identidad federada para el entorno de desarrollo y pruebas de Office 365](federated-identity-for-your-office-365-dev-test-environment.md)
    
- [Protección contra amenazas avanzada en el entorno de desarrollo y prueba de Office 365](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
- [eDiscovery avanzado para el entorno de desarrollo y pruebas de Office 365](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
- [Protección de archivos confidenciales en el entorno de desarrollo y pruebas de Office 365](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
- [Sitio de grupo de SharePoint Online aislado en el entorno de desarrollo y pruebas](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
- [Etiquetado y clasificación de datos en el entorno de desarrollo y pruebas de Office 365](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
## <a name="see-also"></a>Vea también

- [Guías del entorno de pruebas de adopción de la nube (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
- [Adopción de la nube y soluciones híbridas](cloud-adoption-and-hybrid-solutions.md)


