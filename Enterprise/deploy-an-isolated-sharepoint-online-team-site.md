---
title: Implementar un sitio de grupo SharePoint Online aislado
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Solutions
ms.assetid: 3033614b-e23b-4f68-9701-f62525eafaab
description: 'Resumen: Implementar un nuevo sitio de grupo SharePoint Online aislado con estas instrucciones paso a paso.'
ms.openlocfilehash: b22f9bd6ca5562f6c9632709d8afb54cd7b8d634
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="deploy-an-isolated-sharepoint-online-team-site"></a>Implementar un sitio de grupo SharePoint Online aislado

 **Resumen:** Implementar un nuevo sitio de grupo SharePoint Online aislado con estas instrucciones paso a paso.
  
Este artículo es una guía de implementación paso a paso para crear y configurar un sitio de grupo SharePoint Online aislado en Microsoft Office 365. Estos pasos supone el uso de los tres grupos de SharePoint predeterminados y niveles de permiso correspondiente, con un grupo de acceso basado en Azure Active Directory AD único para cada nivel de acceso.
  
## <a name="phase-1-create-and-populate-the-team-site-access-groups"></a>Fase 1: Crear y llenar los grupos de acceso de sitio de equipo

En esta fase, crear tres grupos de acceso AD Azure para los grupos de SharePoint tres predeterminados y rellenarlas con las cuentas de usuario apropiadas.
  
> [!NOTE]
> Los pasos siguientes se supone que todas las cuentas de usuario necesarias ya existen y se asignan las licencias correspondientes. Si no, por favor agregarlos y asignar licencias antes de continuar con el paso 1. 
  
### <a name="step-1-list-the-sharepoint-online-admins-for-the-site"></a>Paso 1: Lista de los administradores del sitio de SharePoint Online

Determinar que el conjunto de usuario cuentas correspondiente a los administradores de SharePoint Online para el sitio del grupo aislado.
  
Si está administrando cuentas de usuario y grupos mediante Office 365 y desea usar Windows PowerShell, haga una lista de usuario nombre principal (UPN) (ejemplo UPN: belindan@contoso.com).
  
### <a name="step-2-list-the-members-for-the-site"></a>Paso 2: Lista de los miembros del sitio

Determinar el conjunto de cuentas de usuario correspondientes a los miembros del sitio de grupo aislado, quienes colaborará en recursos almacenados dentro del sitio.
  
Si está administrando cuentas de usuario y grupos mediante Office 365 y desea usar PowerShell, haga una lista de los UPN. Si hay muchos de los integrantes del sitio, puede almacenar la lista de nombres principales de usuario en un archivo de texto y agregarlas todas con un único comando de PowerShell.
  
### <a name="step-3-list-the-viewers-for-the-site"></a>Paso 3: Enumere los visores del sitio

Determinar el conjunto de cuentas de usuario correspondientes a los visores del sitio del grupo aislado, quienes pueden ver los recursos almacenados en el sitio, pero no modificarlas o colaborar directamente en su contenido.
  
Si está administrando cuentas de usuario y grupos mediante Office 365 y desea usar PowerShell, haga una lista de los UPN. Si hay muchos de los integrantes del sitio, puede almacenar la lista de nombres principales de usuario en un archivo de texto y agregarlas todas con un único comando de PowerShell.
  
Los visores del sitio podrían incluir ejecutiva, abogado o entre departamentos participantes.
  
### <a name="step-4-create-the-three-access-groups-for-the-site-in-azure-ad"></a>Paso 4: Crear los grupos de tres acceso para el sitio de AD de Azure

Debe crear los siguientes grupos de acceso en Active Directory de Azure:
  
- Administradores de sitio (que contengan la lista del paso 1)
    
- Miembros del sitio (que contengan la lista del paso 2)
    
- Visores del sitio (que contengan la lista del paso 3)
    
1. En el explorador, vaya al portal de Azure en [https://portal.azure.com](https://portal.azure.com) e iniciar sesión con las credenciales de una cuenta que se ha asignado con la función de administración de usuario administrador o administrador de la empresa.
    
2. En el portal de Azure, haga clic en **Azure Active Directory > usuarios y grupos > grupos de todos los**.
    
3. En la hoja de **todos los grupos** , haga clic en **+ nuevo grupo**.
    
4. En la hoja de **grupo** :
    
  - En **nombre**, escriba el nombre del grupo.
    
  - Seleccione **asignados** en la **suscripción**.
    
  - Haga clic en **Sí** para **Habilitar Office características**.
    
5. Haga clic en **crear**y, a continuación, cierre la hoja de **grupo** .
    
6. Repita los pasos 3 a 5 para los grupos adicionales.
    
> [!NOTE]
> Debe usar el portal de Azure para crear los grupos para que tengan las características de Office habilitadas. Si un sitio de SharePoint Online aislado posterior está configurado como un sitio altamente confidencial con una etiqueta de protección de información de Azure (AIP) para cifrar archivos y asignar permisos a grupos específicos, los grupos permitidos deben haber creado con las características de Office habilitada. No puede cambiar la configuración de características de Office de un grupo de AD Azure después de que se ha creado. 
  
Aquí está la configuración resultante con los grupos de acceso de tres sitios.
  
![Los tres grupos de acceso de su implementación de un sitio de SharePoint Online aislado.](images/c2557f61-478b-4494-95e9-d79fe5909e8b.png)
  
### <a name="step-5-add-the-user-accounts-to-the-access-groups"></a>Paso 5. Agregue las cuentas de usuario a los grupos de acceso

En este paso, haga lo siguiente:
  
1. Agregar la lista de usuarios del paso 1 al grupo de acceso de administradores del sitio
    
2. Agregue la lista de usuarios del paso 2 al grupo de acceso de miembros del sitio
    
3. Agregue la lista de usuarios del paso 3 al grupo de acceso de los visores de sitio
    
Si está administrando cuentas de usuario y grupos de AD del servidor de Windows, agregar usuarios a los grupos de acceso apropiada con su usuario de AD del servidor Windows normal y procedimientos de administración de grupo y espere a que la sincronización con su suscripción de Office 365.
  
Si está administrando cuentas de usuario y grupos mediante Office 365, puede utilizar el centro de administración de Office o PowerShell. Si tiene nombres de grupo duplicado de cualquiera de los grupos de acceso, debe utilizar el centro de administración de Office.
  
Para el centro de administración de Office, inicie sesión con una cuenta de usuario que se ha asignado la función de administrador de la cuenta de usuario o administrador de la empresa y utilizar grupos para agregar las cuentas de usuario apropiadas y a los grupos de acceso apropiado.
  
Para PowerShell, primero [conecte con el módulo de Active Directory V2 PowerShell de Azure](https://go.microsoft.com/fwlink/?linkid=842218).
  
A continuación, utilice el siguiente bloque de comandos para agregar una cuenta de usuario individual a un grupo de acceso:
  
```
$userUPN="<UPN of the user account>"
$grpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

> [!TIP]
> Para un archivo de texto que contiene todos los comandos de PowerShell y un Excel hoja de trabajo de configuración que genera comandos de PowerShell basándose en su grupo y usuario nombres de cuenta, descargue el [Aislado SharePoint Online sitio Deployment Kit de equipo](https://gallery.technet.microsoft.com/Isolated-SharePoint-Online-0b364907). 
  
Si almacena el UPN de cuentas de usuario de cualquiera de los grupos de acceso de un archivo de texto, puede utilizar el siguiente bloque de comandos de PowerShell para agregarlos a la vez:
  
```
$grpName="<display name of the access group>"
$fileName="<path and name of the file containing the list of account UPNs>"
$grpID=(Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
Get-Content $fileName | ForEach { $userUPN=$_; Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID $grpID }
```

Para PowerShell, utilice el siguiente bloque de comandos para agregar un grupo individual a un grupo de acceso:
  
```
$nestedGrpName="<display name of the group to add to the access group>"
$grpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $nestedGrpName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID

```

El resultado debería ser la siguiente:
  
- El grupo de sitio administradores AD Azure contiene las cuentas de usuario de administrador de sitio o grupos
    
- Grupo de AD Azure de miembros del sitio contiene los grupos o cuentas de usuario miembros de sitio
    
- El grupo de sitio visores Azure AD contiene las cuentas de usuario o grupos que sólo se pueden ver el contenido del sitio
    
Validar la lista de miembros del grupo para cada grupo de acceso con el centro de administración de Office o con el siguiente bloque de comandos de PowerShell:
  
```
$grpName="<display name of the access group>"
Get-AzureADGroupMember -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID | Sort UserPrincipalName | Select UserPrincipalName,DisplayName,UserType
```

Aquí está la configuración resultante con los grupos de acceso de sitio de tres rellenado con cuentas de usuario o grupos.
  
![Los tres grupos de acceso completados con cuentas de usuario.](images/2320107c-dad6-4c8f-94e5-f6427c125e71.png)
  
## <a name="phase-2-create-and-configure-the-isolated-team-site"></a>Fase 2: Crear y configurar el sitio del grupo aislado

En esta fase, crear el sitio de SharePoint Online aislado y configurar los permisos para los niveles de permisos de SharePoint Online predeterminado utilizar los nuevos grupos de Azure acceso basado en AD.
  
Primero, cree el sitio de grupo SharePoint Online con estos pasos.
  
1. Iniciar sesión en el portal de Office 365 con una cuenta que se utilizará para administrar el sitio de grupo de SharePoint Online (un administrador de SharePoint Online). Para obtener ayuda, visite [dónde puede iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. En la lista de fichas, haga clic en **SharePoint**.
    
3. En la nueva ficha de **SharePoint** del explorador, haga clic en **Crear sitio +**.
    
4. En la página **crear un sitio Web** , haga clic en **sitio de equipo**.
    
5. En **nombre del sitio**, escriba un nombre para el sitio del equipo. 
    
6. En la **Descripción del sitio de equipo,** escriba una descripción opcional de la finalidad del sitio.
    
7. En **la configuración de privacidad**, seleccione **Private: sólo los miembros pueden tener acceso a este sitio**y, a continuación, haga clic en **siguiente**.
    
8. En el **que desea agregar?** panel, haga clic en **Finalizar**.
    
A continuación, desde el nuevo sitio de grupo de SharePoint Online, configurar permisos.
  
1. En la barra de herramientas, haga clic en el icono de configuración y, a continuación, haga clic en **permisos del sitio**.
    
2. En el panel **permisos de sitio** , haga clic en **configuración de permisos avanzados**.
    
3. En la nueva ficha de **permisos** del explorador, haga clic en **Configuración de solicitud de acceso**.
    
4. En el cuadro de diálogo **Configuración de las solicitudes de acceso** , desactive **Permitir miembros para compartir el sitio y archivos y carpetas individuales** y **Permitir las solicitudes de acceso** (de modo que todas las casillas de verificación está desactivadas) y, a continuación, haga clic en **Aceptar**.
    
5. En la ficha **permisos** del explorador, haga clic en ** \<nombre del sitio > miembros** en la lista.
    
6. En **personas y grupos**, haga clic en **nuevo**.
    
7. En el cuadro de diálogo **Compartir** , escriba el nombre del grupo de acceso de miembros del sitio, selecciónelo y, a continuación, haga clic en **Compartir**.
    
8. Haga clic en el botón Atrás del explorador.
    
9. Haga clic en ** \<nombre del sitio > propietarios** en la lista.
    
10. En **personas y grupos**, haga clic en **nuevo**.
    
11. En el cuadro de diálogo **Compartir** , escriba el nombre del grupo de acceso de administradores de sitio, selecciónelo y, a continuación, haga clic en **Compartir**.
    
12. Haga clic en el botón Atrás del explorador.
    
13. Haga clic en ** \<nombre del sitio > visitantes** en la lista.
    
14. En **personas y grupos**, haga clic en **nuevo**.
    
15. En el cuadro de diálogo **Compartir** , escriba el nombre del grupo de acceso de sitio visores, selecciónelo y, a continuación, haga clic en **Compartir**.
    
16. Cierre la ficha de **permisos** de tu navegador.
    
Los resultados de estos valores de permisos son:
  
- La ** \<nombre del sitio > propietarios** grupo de SharePoint contiene el grupo de acceso de administradores de sitio en el que todos los miembros tienen el nivel de permiso **control total** .
    
- La ** \<nombre del sitio > miembros** grupo de SharePoint contiene el grupo de acceso de miembros de sitio, en la que todos los miembros tienen el nivel de permisos **Editar** .
    
- La ** \<nombre del sitio > visitantes** grupo de SharePoint contiene el grupo de acceso de visores de sitio en el que todos los miembros tienen el nivel de permiso de **lectura** .
    
- Se deshabilita la capacidad de los miembros invitar a otros miembros o para los miembros solicitar acceso.
    
Aquí está la configuración resultante con los tres grupos de SharePoint para el sitio configurado para utilizar los tres grupos de acceso, que se llenan con las cuentas de usuario o los grupos de AD de Azure.
  
![La configuración final del sitio de SharePoint Online aislado con grupos de acceso y cuentas de usuario.](images/e7618971-06ab-447b-90ff-d8be3790fe63.png)
  
Usted y los miembros del sitio, a través de la pertenencia a grupos en uno de los grupos de acceso, ahora pueden colaborar utilizando los recursos del sitio.
  
## <a name="next-step"></a>Paso siguiente

Cuando necesite cambiar la pertenencia al grupo de acceso de sitio o crear una carpeta de documentos con permisos personalizados, vea [administrar un sitio de grupo SharePoint Online aislado](manage-an-isolated-sharepoint-online-team-site.md).
  
## <a name="see-also"></a>Consulte también

[Sitios de equipo de SharePoint Online aislados](isolated-sharepoint-online-team-sites.md)
  
[Diseñar un sitio de grupo SharePoint Online aislado](design-an-isolated-sharepoint-online-team-site.md)
  
[Administrar un sitio de grupo SharePoint Online aislado](manage-an-isolated-sharepoint-online-team-site.md)
  
[Soluciones de seguridad](security-solutions.md)



