---
title: "Configurar grupos y usuarios de un entorno de pruebas y desarrollo de campaña política"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: None
ms.custom: Strat_O365_Enterprise
ms.assetid: 0e22bcf3-bad3-42a4-b44f-276e0cf4790f
description: "Resumen: Crear suscripciones de prueba de seguridad (EMS) + Office 365 y movilidad en la empresa con usuarios y grupos para un entorno de pruebas y desarrollo de campaña política."
ms.openlocfilehash: 25d03e0aa521c8fdbf20c2dc3ff2fc46e1aabe2f
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="configure-groups-and-users-for-a-political-campaign-devtest-environment"></a>Configurar grupos y usuarios de un entorno de pruebas y desarrollo de campaña política

 **Resumen:** Crear suscripciones de prueba de seguridad (EMS) + Office 365 y movilidad en la empresa con usuarios y grupos para un entorno de pruebas y desarrollo de campaña política.
  
Utilice las instrucciones de este artículo para crear un entorno de pruebas y desarrollo que incluye las cuentas de usuario simplificado y grupos para la solución de [Microsoft Security Guidance for campañas políticos, las ONG y otras organizaciones ágiles](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) .
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a>Fase 1: Crear el entorno de desarrollo y pruebas de Office 365

En esta fase, se puede obtener las suscripciones de prueba de Office 365 E5 + E5 (EMS) de seguridad para una organización ficticia que representa una campaña política y movilidad en la empresa.
  
En primer lugar, siga las instrucciones en la **fase 2** del [entorno de desarrollo y prueba de Office 365](office-365-dev-test-environment.md).
  
A continuación, registrarse para la suscripción de prueba de EMS E5 y agregarlo a la misma organización que su suscripción de prueba de Office 365.
  
1. Si es necesario, iniciar sesión en el portal de Office 365 con las credenciales de la cuenta de administrador global de su suscripción de prueba. Para obtener ayuda, visite [dónde puede iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Haga clic en el mosaico de **Admin** .
    
3. En la ficha del **Centro de administración de Office** en el explorador, en la exploración de la izquierda, haga clic en **de facturación > adquirir servicios**.
    
4. En la página **Servicios de compra** , busque el elemento de **seguridad E5 + de movilidad en la empresa** . Sitúe el puntero del mouse sobre él y haga clic en **iniciar la versión de prueba gratuita**.
    
5. En la página **confirmar su pedido** , haga clic en **Probar ahora**.
    
6. En la página de **confirmación del pedido** , haga clic en **continuar**.
    
A continuación, habilite la licencia EMS E5 de la cuenta de administrador global.
  
1. En la ficha del **Centro de administración de Office 365** en el explorador, en la exploración de la izquierda, haga clic en **los usuarios > usuarios activos**.
    
2. Haga clic en la cuenta de administrador global y, a continuación, haga clic en **Editar** para **licencias de producto**.
    
3. En el panel de **licencias de producto** , activar la licencia del producto de **movilidad en la empresa + seguridad E5** en **On**, haga clic en **Guardar** y, a continuación, haga clic en **Cerrar** dos veces.
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups"></a>Fase 2: Crear y configurar los grupos de Azure de Active Directory (AD)

En esta fase, cree y configure los grupos de AD Azure para su campaña.
  
Primero, cree un conjunto de grupos para una campaña política típico con el portal de Azure.
  
1. En una ficha independiente en el explorador, vaya al portal de Azure en [https://portal.azure.com](https://portal.azure.com). Si es necesario, inicie sesión con las credenciales de la cuenta de administrador global para la suscripción de prueba de Office 365 E5.
    
2. En el portal de Azure, haga clic en **Azure Active Directory > usuarios y grupos > grupos de todos los**.
    
3. Realice los pasos siguientes para cada nombre de grupo en esta lista:
    
  - Director y el personal estratégico
    
  - Personal de TI
    
  - Personal de análisis
    
  - Personal de base regular
    
  - Personal de operaciones
    
  - Personal de campo
    
1. En la hoja de **todos los grupos** , haga clic en **+ nuevo grupo**.
    
2. En **nombre**, escriba el nombre del grupo de la lista.
    
3. Seleccione **usuario dinámica** de **pertenencia**.
    
4. Haga clic en **Sí** para **Habilitar Office características**.
    
5. Haga clic en **Agregar de consulta dinámica**.
    
6. En **Agregue usuarios donde**, seleccione **departamento**.
    
7. En el siguiente campo, seleccione **igual a**.
    
8. En el siguiente campo, escriba el nombre del grupo de la lista.
    
9. Haga clic en **Agregar consulta**y, a continuación, haga clic en **crear**.
    
10. Haga clic en **usuarios y grupos: todos los grupos**.
    
A continuación, configure los grupos para que los miembros se asignan automáticamente licencias Office 365 E5 y E5 EMS.
  
1. En el portal de Azure, haga clic en **Azure Active Directory > licencias > todos los productos**.
    
2. En la lista, seleccione **seguridad E5 + de movilidad en la empresa** y **E5 Enterprise de Office 365**y, a continuación, haga clic en **+ asignar**.
    
3. En la hoja **asignar licencias** , haga clic en **usuarios y grupos**.
    
4. En la lista de grupos, seleccione lo siguiente:
    
  - Personal de análisis
    
  - Personal de campo
    
  - Personal de TI
    
  - Personal de operaciones
    
  - Personal de base regular
    
  - Director y el personal estratégico
    
5. Haga clic en **Seleccionar**y, a continuación, haga clic en **asignar**.
    
6. Cierre la ficha portal Azure en el explorador.
    
## <a name="phase-3-add-your-user-accounts"></a>Fase 3: Agregar las cuentas de usuario

En esta fase, debe agregar las cuentas de usuario de ejemplo para su campaña política.
  
En primer lugar, puede [Conectar con el módulo de Active Directory V2 PowerShell de Azure](https://go.microsoft.com/fwlink/?linkid=842218).
  
A continuación, rellene el nombre de su organización, su ubicación y una contraseña común y, a continuación, ejecutar estos comandos desde el símbolo del sistema de PowerShell o el entorno de secuencias de comandos integrado (ISE):
  
```
$orgName="<organization name, such as contoso for the contoso.onmicrosoft.com trial subscription domain name>"
$location="<the ISO ALPHA2 country code, such as US for the United States>"
$commonPassword="<common password for all the new accounts>"

$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPassword

$deptName="Senior and strategic staff"
$userNames=@("Candidate","ChiefOfStaff","Strategic1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="IT staff"
$userNames=@("ITAdmin1","ITAdmin2") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Analytics staff"
$userNames=@("DataScientist1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Regular core staff"
$userNames=@("Regular1","Regular2") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Operations staff"
$userNames=@("Operations1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Field staff"
$userNames=@("FieldConsultant1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }

```

> [!IMPORTANT]
> El uso de una contraseña común aquí es para la automatización y la facilidad de configuración para un entorno de pruebas y desarrollo. Esto no es recomendable para las suscripciones de producción. Cuando se inscribe en cada una de estas nuevas cuentas de usuario, se le pedirá que cambie la contraseña. 
  
Siga estos pasos para comprobar que pertenencia a un grupo dinámico y basado en el grupo de licencias funciona correctamente.
  
1. Desde la ficha **Página de inicio de Microsoft Office** del explorador, haga clic en el mosaico de **Admin** .
    
2. Desde la ficha del **Centro de administración de Office** nueva del explorador, haga clic en **usuarios**.
    
3. En la lista de usuarios, haga clic en **candidato**.
    
4. En el panel que muestra las propiedades de la cuenta de usuario de **candidato** , compruebe lo siguiente:
    
  - Es un miembro del grupo **jefe y personal estratégico** (en **pertenencia a grupos**).
    
  - Se le ha asignado las licencias de **movilidad en la empresa + seguridad E5** y **E5 Enterprise de Office 365** (en **licencias de producto**).
    
5. Cierre el panel de cuenta de usuario de **candidato** .
    
## <a name="record-values-for-future-reference"></a>Anote los valores para futuras referencias

Registre estos valores para trabajar con el Office 365 y EMS suscripciones de prueba para este entorno de pruebas y desarrollo:
  
- Nombre de la organización de su suscripción de prueba: ___ 
    
    Por ejemplo, el nombre de dominio de suscripción de prueba de contoso.onmicrosoft.com, el nombre de la organización es "contoso".
    
- El nombre de administrador global de Office 365: ___.onmicrosoft.com
    
    Registre la contraseña para esta cuenta y la contraseña inicial común para las otras cuentas de usuario en una ubicación segura.
    
## <a name="next-step"></a>Paso siguiente

Crear los cuatro tipos diferentes de sitios de SharePoint Online team en este entorno de pruebas y desarrollo con [crear sitios de equipo en un entorno de pruebas y desarrollo de campaña política](create-team-sites-in-a-political-campaign-dev-test-environment.md).
  
## <a name="see-also"></a>Consulte también

[Guía de seguridad de Microsoft para campañas políticas, las ONG y otras organizaciones de Agile](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[Crear sitios de equipo en un entorno de pruebas y desarrollo de campaña política](create-team-sites-in-a-political-campaign-dev-test-environment.md)
  
[Guías de entorno de pruebas de adopción de la nube (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[Adopción de la nube y soluciones híbridas](cloud-adoption-and-hybrid-solutions.md)




