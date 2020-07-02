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

The procedures in this topic require you to connect to Windows PowerShell for Office 365. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).
  
Necesita también las credenciales del administrador de inquilinos del asociado.
  
## <a name="what-do-you-want-to-do"></a>¿Qué quiere hacer?

### <a name="list-all-tenant-ids"></a>List all tenant IDs

> [!NOTE]
> If you have more than 500 tenants, scope the cmdlet syntax with either  _-All_ or _-MaxResultsParameter_. This applies to other cmdlets that can give a large output, such as **Get-MsolUser**.
  
Para obtener una lista de todos los identificadores de inquilinos de cliente a los que tiene acceso, ejecute este comando.
  
```
Get-MsolPartnerContract -All | Select-Object TenantId
```

Se mostrará una lista de todos los inquilinos de clientes por **TenantId**.

>[!Note]
>PowerShell Core no es compatible con el Módulo Microsoft Azure Active Directory para Windows PowerShell ni los cmdlet que llevan **Msol** en su nombre. Para seguir usando estos cmdlets, debe ejecutarlos desde Windows PowerShell.
>
  
### <a name="get-a-tenant-id-by-using-the-domain-name"></a>Obtener un identificador de inquilino a través del nombre de dominio

To get the **TenantId** for a specific customer tenant by domain name, run this command. Replace _<domainname.onmicrosoft.com>_ with the actual domain name of the customer tenant that you want.
  
```
Get-MsolPartnerContract -DomainName <domainname.onmicrosoft.com> | Select-Object TenantId
```

### <a name="list-all-domains-for-a-tenant"></a>Hacer una lista de todos los dominios de un inquilino

To get all domains for any one customer tenant, run this command. Replace  _<customer TenantId value>_ with the actual value.
  
```
Get-MsolDomain -TenantId <customer TenantId value>
```

Si registró dominios adicionales, se devolverán todos los dominios asociados al **TenantId** del cliente.
  
### <a name="get-a-mapping-of-all-tenants-and-registered-domains"></a>Obtener una asignación de todos los inquilinos y los dominios registrados

The previous Windows PowerShell for Office 365 commands showed you how to retrieve either tenant IDs or domains but not both at the same time, and with no clear mapping between them all. This command generates a listing of all your customer tenant IDs and their domains.
  
```
$Tenants = Get-MsolPartnerContract -All; $Tenants | foreach {$Domains = $_.TenantId; Get-MsolDomain -TenantId $Domains | fl @{Label="TenantId";Expression={$Domains}},name}
```

### <a name="get-all-users-for-a-tenant"></a>Obtener todos los usuarios de un inquilino

This will display the **UserPrincipalName**, the **DisplayName**, and the **isLicensed** status for all users for a particular tenant. Replace _<customer TenantId value>_ with the actual value.
  
```
Get-MsolUser -TenantID <customer TenantId value>
```

### <a name="get-all-details-about-a-user"></a>Obtener todos los detalles acerca de un usuario

If you want to see all the properties of a particular user, run this command. Replace  _<customer TenantId value>_ and _<user principal name value>_ with the actual values.
  
```
Get-MsolUser -TenantId <customer TenantId value> -UserPrincipalName <user principal name value>
```

### <a name="add-users-set-options-and-assign-licenses"></a>Agregar usuarios, establecer opciones y asignar licencias

La creación, la configuración y la concesión de licencias en masa de los usuarios de Microsoft 365 es particularmente eficiente mediante el uso de Windows PowerShell para Office 365. En este proceso de dos pasos, primero se crean entradas para todos los usuarios que desea agregar a un archivo de valores separados por comas (CSV) y, a continuación, se importa dicho archivo con Windows PowerShell para Office 365. 
  
#### <a name="create-a-csv-file"></a>Crear un archivo CSV

Cree un archivo CSV con este formato:
  
-  `UserPrincipalName,FirstName,LastName,DisplayName,Password,TenantId,UsageLocation,LicenseAssignment`
    
donde:
  
- **UsageLocation**: The value for this is the two-letter ISO country/region code of the user. The country/region codes can be looked up at the[ISO Online Browsing Platform](https://go.microsoft.com/fwlink/p/?LinkId=532703). For example, the code for the United States is US, and the code for Brazil is BR. 
    
- **LicenseAssignment**: The value for this uses this format: `syndication-account:<PROVISIONING_ID>`. For example, if you are assigning customer tenant users O365_Business_Premium licenses, the **LicenseAssignment** value looks like this: **syndication-account:O365_Business_Premium**. You will find the PROVISIONING_IDs in the Syndication Partner Portal that you have access to as a Syndication or CSP partner.
    
#### <a name="import-the-csv-file-and-create-the-users"></a>Importar el archivo CSV y crear los usuarios

After you have your CSV file created, run this command to create user accounts with non-expiring passwords that the user must change at first sign-in and that assigns the license you specify. Be sure to substitute the correct CSV file name.
  
```
Import-Csv .\FILENAME.CSV | foreach {New-MsolUser -UserPrincipalName $_.UserPrincipalName -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -Password $_.Password -UsageLocation $_.UsageLocation -LicenseAssignment $_.LicenseAssignment -ForceChangePassword:$true -PasswordNeverExpires:$true -TenantId $_.TenantId}
```

## <a name="see-also"></a>Consulte también

#### 

[Ayuda para asociados](https://go.microsoft.com/fwlink/p/?LinkId=533477)

