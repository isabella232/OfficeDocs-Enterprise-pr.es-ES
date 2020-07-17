---
title: Administrar inquilinos de Microsoft 365 con Windows PowerShell para asociados con permiso de acceso delegado (DAP)
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: f92d5116-5b66-4150-ad20-1452fc3dd712
description: 'Resumen: use Windows PowerShell para Microsoft 365 para administrar los arrendamientos de clientes.'
ms.openlocfilehash: a57f66ec02f5ba69006c17a9cf734e622017b8fb
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998236"
---
# <a name="manage-microsoft-365-tenants-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>Administrar inquilinos de Microsoft 365 con Windows PowerShell para asociados con permiso de acceso delegado (DAP)

Windows PowerShell permite la sindicación y los partners del proveedor de soluciones en la nube (CSP) para administrar fácilmente e informar sobre la configuración de la arrendamiento de clientes que no está disponible en el centro de administración de Microsoft 365. Tenga en cuenta que los permisos Administrar en nombre de (AOBO) son necesarios para que la cuenta de administrador del asociado se conecte a los inquilinos del cliente.
  
Los asociados con permiso de acceso delegado (DAP) son asociados de sindicación y proveedor de soluciones en la nube (CSP). Con frecuencia son los proveedores de red o de telecomunicaciones para otras compañías. Incluyen las suscripciones de Microsoft 365 en sus ofertas de servicio para sus clientes. Cuando venden una suscripción de 365 de Microsoft, se les conceden automáticamente permisos de administración en nombre de (AOBO) a los arrendamientos de clientes para que puedan administrar y informar sobre los arrendamientos de clientes.
## <a name="what-do-you-need-to-know-before-you-begin"></a>¿Qué necesita saber antes de comenzar?

Los procedimientos de este tema requieren conectarse a Windows PowerShell para Office 365. Para obtener instrucciones, vea [Conectarse a PowerShell de Office 365](connect-to-office-365-powershell.md).
  
Necesita también las credenciales del administrador de inquilinos del asociado.
  
## <a name="what-do-you-want-to-do"></a>¿Qué quiere hacer?

### <a name="list-all-tenant-ids"></a>List all tenant IDs

> [!NOTE]
> Si tiene más de 500 inquilinos, limite la sintaxis del cmdlet con  _-All_ o _-MaxResultsParameter_. Esto se aplica a otros cmdlets que pueden dar un resultado de gran tamaño, como **Get-MsolUser**.
  
Para obtener una lista de todos los identificadores de inquilinos de cliente a los que tiene acceso, ejecute este comando.
  
```
Get-MsolPartnerContract -All | Select-Object TenantId
```

Se mostrará una lista de todos los inquilinos de clientes por **TenantId**.

>[!Note]
>PowerShell Core no es compatible con el Módulo Microsoft Azure Active Directory para Windows PowerShell ni los cmdlet que llevan **Msol** en su nombre. Para seguir usando estos cmdlets, debe ejecutarlos desde Windows PowerShell.
>
  
### <a name="get-a-tenant-id-by-using-the-domain-name"></a>Obtener un identificador de inquilino a través del nombre de dominio

Para obtener el **TenantId** para un inquilino de cliente específico por nombre de dominio, ejecute este comando. Reemplace _<domainname.onmicrosoft.com>_ por el nombre de dominio real del inquilino de cliente que desea.
  
```
Get-MsolPartnerContract -DomainName <domainname.onmicrosoft.com> | Select-Object TenantId
```

### <a name="list-all-domains-for-a-tenant"></a>Hacer una lista de todos los dominios de un inquilino

Para obtener todos los dominios de cualquier inquilino de cliente, ejecute este comando. Reemplace el  _<customer TenantId value>_ por el valor real.
  
```
Get-MsolDomain -TenantId <customer TenantId value>
```

Si registró dominios adicionales, se devolverán todos los dominios asociados al **TenantId** del cliente.
  
### <a name="get-a-mapping-of-all-tenants-and-registered-domains"></a>Obtener una asignación de todos los inquilinos y los dominios registrados

Los comandos de Windows PowerShell para Office 365 presentados anteriormente le mostraron cómo recuperar identificadores de inquilinos o dominios, pero no ambos al mismo tiempo y sin ninguna asignación clara entre todos ellos. Este comando genera una lista de todos los identificadores de inquilinos de clientes y sus dominios.
  
```
$Tenants = Get-MsolPartnerContract -All; $Tenants | foreach {$Domains = $_.TenantId; Get-MsolDomain -TenantId $Domains | fl @{Label="TenantId";Expression={$Domains}},name}
```

### <a name="get-all-users-for-a-tenant"></a>Obtener todos los usuarios de un inquilino

Se mostrarán los estados **UserPrincipalName**, **DisplayName** y **isLicensed** para todos los usuarios de un inquilino en particular. Reemplace el _<customer TenantId value>_ por el valor real.
  
```
Get-MsolUser -TenantID <customer TenantId value>
```

### <a name="get-all-details-about-a-user"></a>Obtener todos los detalles acerca de un usuario

Si desea ver todas las propiedades de un usuario concreto, ejecute este comando. Reemplace el  _<customer TenantId value>_ y el _<user principal name value>_ por los valores reales.
  
```
Get-MsolUser -TenantId <customer TenantId value> -UserPrincipalName <user principal name value>
```

### <a name="add-users-set-options-and-assign-licenses"></a>Agregar usuarios, establecer opciones y asignar licencias

La creación, la configuración y la concesión de licencias en masa de los usuarios de Microsoft 365 es particularmente eficiente mediante el uso de Windows PowerShell para Office 365. En este proceso de dos pasos, primero se crean entradas para todos los usuarios que desea agregar a un archivo de valores separados por comas (CSV) y, a continuación, se importa dicho archivo con Windows PowerShell para Office 365. 
  
#### <a name="create-a-csv-file"></a>Crear un archivo CSV

Cree un archivo CSV con este formato:
  
-  `UserPrincipalName,FirstName,LastName,DisplayName,Password,TenantId,UsageLocation,LicenseAssignment`
    
donde:
  
- **UsageLocation**: El valor de esto es el código de país/región ISO de dos letras del usuario. Los códigos de país/región pueden buscarse en la[Plataforma de exploración en línea ISO](https://go.microsoft.com/fwlink/p/?LinkId=532703). Por ejemplo, el código para Estados Unidos es US y el código para Brasil es BR. 
    
- **LicenseAssignment**: el valor usa este formato: `syndication-account:<PROVISIONING_ID>`. Por ejemplo, si va a asignar licencias de O365_Business_Premium de usuarios de inquilino de cliente, el valor de **LicenseAssignment** se asemejará a: **syndication-account:O365_Business_Premium**. Encontrará los PROVISIONING_IDs en el portal de asociados de redifusión web al que tiene acceso como asociado de redifusión web o CSP.
    
#### <a name="import-the-csv-file-and-create-the-users"></a>Importar el archivo CSV y crear los usuarios

Una vez que el archivo CSV esté creado, ejecute este comando para crear cuentas de usuario con contraseñas sin fecha de expiración que el usuario debe cambiar en el primer inicio de sesión y que asigna la licencia que el usuario especifique. Asegúrese de reemplazar el nombre de archivo CSV correcto.
  
```
Import-Csv .\FILENAME.CSV | foreach {New-MsolUser -UserPrincipalName $_.UserPrincipalName -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -Password $_.Password -UsageLocation $_.UsageLocation -LicenseAssignment $_.LicenseAssignment -ForceChangePassword:$true -PasswordNeverExpires:$true -TenantId $_.TenantId}
```

## <a name="see-also"></a>Consulte también

#### 

[Ayuda para asociados](https://go.microsoft.com/fwlink/p/?LinkId=533477)

