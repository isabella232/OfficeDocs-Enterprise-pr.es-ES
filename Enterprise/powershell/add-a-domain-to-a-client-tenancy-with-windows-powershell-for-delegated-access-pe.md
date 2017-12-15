---
title: Agregar un dominio a un arrendamiento de cliente con Windows PowerShell para asociados con permiso de acceso delegado (DAP)
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: DecEntMigration
ms.assetid: f49b4d24-9aa0-48a6-95dd-6bae9cf53d2c
description: 'Resumen: Use Windows PowerShell para Office 365 para agregar un nombre de dominio alternativo a un inquilino de cliente existente.'
ms.openlocfilehash: 182750a5706dbb23c6207c6bd63334cbf2a2a795
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2017
---
# <a name="add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-permission-dap-partners"></a>Agregar un dominio a un arrendamiento de cliente con Windows PowerShell para asociados con permiso de acceso delegado (DAP)

 **Resumen:** Uso de Windows PowerShell para Office 365 agregar un nombre de dominio alternativo a un arrendatario de cliente existente.
  
Puede crear y asociar nuevos dominios con el arrendamiento del cliente con Windows PowerShell para Office 365 más rápido que con el Centro de administración de Office 365.
  
Los asociados con permiso de acceso delegado (DAP) son asociados de sindicación y proveedor de soluciones en la nube (CSP). Con frecuencia son los proveedores de red o de telecomunicaciones para otras compañías. Empaquetan las suscripciones de Office 365 en sus ofertas de servicio a sus clientes. Cuando se vende una suscripción a Office 365, automáticamente se les conceden permisos Administrar en nombre de (AOBO) a losarrendamientos de cliente para que puedan administrar y notificar los arrendamientos de cliente.
## <a name="what-do-you-need-to-know-before-you-begin"></a>¿Qué necesita saber antes de comenzar?

UNRESOLVED_TOKEN_VAL(GENL_O365_PowerShell_BeforeYouBegin)
  
También necesitará la siguiente información:
  
- Necesitará el nombre de dominio completo (FQDN) que desea el cliente.
    
- Necesita el **TenantId** del cliente.
    
- El FQDN debe estar registrado con un registrador del servicio de nombres de dominio (DNS), como GoDaddy. Para obtener más información sobre cómo registrar públicamente un nombre de dominio, vea [Cómo comprar un nombre de dominio](https://go.microsoft.com/fwlink/p/?LinkId=532541).
    
- Necesita saber cómo agregar un registro TXT a la zona DNS registrada para su registrador DNS. Para obtener más información sobre cómo agregar un registro TXT, vea [Crear DNS en proveedores de hospedaje DNS para Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542). Si esos procedimientos no funcionan, necesitará encontrar los procedimientos de su registrador DNS.
    
## <a name="create-domains"></a>Crear dominios

 Sus clientes probablemente le pedirán crear dominios adicionales para asociar con su arrendamiento, ya que no desean que el dominio predeterminado <domain>.onmicrosoft.com sea el dominio principal que represente su identidad corporativa en el mundo. En este procedimiento se explica cómo crear un nuevo dominio asociado con el arrendamiento de su cliente.
  
> [!NOTE]
> Para realizar algunas de estas operaciones, la cuenta de administrador de asociado con la que inicie sesión debe establecerse en **Administración completa** para la opción **Asignar acceso administrativo a las compañías a las que proporciona soporte técnico** que se encuentra en la información de la cuenta de administrador en el Centro de administración de Office 365. Para obtener más información sobre cómo administrar roles de administrador de asociado, vea[Asociados: Ofrecer administración delegada](https://go.microsoft.com/fwlink/p/?LinkId=532435). 
  
### <a name="create-the-domain-in-azure-active-directory"></a>Crear el dominio en Azure Active Directory

Este comando crea el dominio en Azure Active Directory, pero no lo asocia al dominio registrado públicamente. Eso sucede cuando le demuestra a Microsoft Office 365 para empresas que es propietario del dominio registrado públicamente.
  
```
New-MsolDomain -TenantId <customer TenantId> -Name <FQDN of new domain>
```

### <a name="get-the-data-for-the-dns-txt-verification-record"></a>Obtener los datos para la verificación del registro TXT de DNS

 Office 365 generará los datos específicos que necesita colocar en el registro de comprobación de TXT de DNS. Para obtener los datos, ejecute este comando.
  
```
Get-MsolDomainVerificationDNS -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

Se obtendrá el siguiente resultado:
  
 `Label: domainname.com`
  
 `Text: MS=ms########`
  
 `Ttl: 3600`
  
> [!NOTE]
> Necesitará este texto para crear el registro TXT en la zona DNS registrada públicamente. Asegúrese de copiarlo y guardarlo. 
  
### <a name="add-a-txt-record-to-the-publically-registered-dns-zone"></a>Agregar un registro TXT a la zona DNS registrada públicamente

Antes de que Office 365 empiece a aceptar tráfico que se dirigirá al nombre de dominio registrado públicamente, debe demostrar que tiene permisos de administrador sobre el dominio. Demuestre que el dominio le pertenece mediante la creación de un registro TXT en el dominio. Un registro TXT no hace nada en su dominio y puede eliminarse una vez que se establezca su propiedad del dominio. Para crear los registros TXT, siga los procedimientos en [Crear DNS en proveedores de hospedaje DNS para Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542). Si esos procedimientos no funcionan, necesitará encontrar los procedimientos de su registrador DNS.
  
Confirme la creación correcta del registro TXT mediante nslookup. Siga esta sintaxis.
  
```
nslookup -type=TXT <FQDN of registered domain>
```

Se obtendrá el siguiente resultado:
  
 `Non-authoritative answer:`
  
 `FQDN of the registered domain`
  
 `text=MS=ms########`
  
### <a name="validate-domain-ownership-in-office-365"></a>Validar la propiedad del dominio en Office 365

En este último paso, el usuario valida en Office 365 que es el propietario del dominio registrado públicamente. Después de este paso, Office 365 empezará a aceptar tráfico enrutado al nuevo nombre de dominio. Para completar la creación del dominio y el proceso de registro, ejecute este comando. 
  
```
Confirm-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

Este comando no devolverá ningún resultado, por lo tanto, para confirmar que funcionó, ejecute este comando.
  
```
Get-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

Se mostrará un resultado semejante a
  
||||
|:-----|:-----|:-----|
| `Name` <br/> | `Status` <br/> | `Authentication` <br/> |
| `FQDN of new domain` <br/> | `Verified` <br/> | `Managed` <br/> |
   
## <a name="see-also"></a>See also

#### 

[Ayuda para asociados](https://go.microsoft.com/fwlink/p/?LinkID=533477)
