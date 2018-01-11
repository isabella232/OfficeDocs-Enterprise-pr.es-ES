---
title: Eliminar licencias de cuentas de usuario con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: "Explica cómo utilizar Office 365 PowerShell para quitar licencias de Office 365 que se asignaron previamente a los usuarios."
ms.openlocfilehash: d419aab9b3287364567e03accdfb2e687eacb0de
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2018
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a>Eliminar licencias de cuentas de usuario con PowerShell de Office 365

**Resumen:** Explica cómo utilizar Office 365 PowerShell para quitar licencias de Office 365 que se asignaron previamente a los usuarios.
  
## <a name="before-you-begin"></a>Antes de empezar

- Los procedimientos de este tema requieren conectarse a PowerShell de Office 365. Para obtener instrucciones, vea [Conectarse a PowerShell de Office 365](connect-to-office-365-powershell.md).
    
- Para ver la información de licencia ( **AccountSkuID** ) del plan de la organización, consulte los temas siguientes:
    
  - [Ver las licencias y los servicios con PowerShell de Office 365](view-licenses-and-services-with-office-365-powershell.md)
    
  - [Ver los detalles del servicio y la licencia de la cuenta con PowerShell de Office 365](view-account-license-and-service-details-with-office-365-powershell.md)
    
- Si usa el cmdlet **Get-MsolUser** sin usar el parámetro _All_, solo se devuelven las 500 primeras cuentas.
    
## <a name="the-short-version-instructions-without-explanations"></a>Versión corta (instrucciones sin explicaciones)
<a name="ShortVersion"> </a>

En esta sección se presentan los procedimientos sin explicaciones superfluas. Si tiene preguntas o desea obtener más información, puede leer el resto del tema.
  
Para quitar licencias de una cuenta de usuario existente, utilice la sintaxis siguiente:
  
```
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

Este ejemplo quita la `litwareinc:ENTERPRISEPACK` una licencia (Office 365 Enterprise E3) de la cuenta de usuario BelindaN@litwareinc.com.
  
```
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

Para quitar licencias de un grupo de usuarios con licencia existentes, utilice uno de los métodos siguientes:
  
- **Filtrar las cuentas basadas en un atributo de cuenta existente** Para ello, utilice la sintaxis siguiente:
    
```
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

Este ejemplo quita el `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licencias de todas las cuentas de los usuarios del departamento de ventas en los Estados Unidos.
    
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- **Usar una lista de cuentas específicas** Para ello, siga estos pasos:
    
1. Cree y guarde un archivo de texto que contenga una cuenta en cada línea de esta manera:
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. Utilice la sintaxis siguiente:
    
  ```
  Get-Content "<FileNameAndPath>" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
  ```

Este ejemplo quita el `litwareinc:ENTERPRISEPACK` licencia (Office 365 Enterprise E3) de las cuentas de usuario definido en el archivo de texto C:\My Documents\Accounts.txt.
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  ```

Para quitar las licencias de todas las cuentas de usuario, utilice la sintaxis siguiente:
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

Este ejemplo quita el `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) una licencia de todo lo existente licencia de cuentas de usuario.
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a>Versión larga (instrucciones con explicaciones detalladas)
<a name="LongVersion"> </a>

Nada es para siempre, y esto incluye licencias de Office 365: tarde o temprano, llegará un momento cuando necesite quitar una licencia de una cuenta de usuario. Tal vez el usuario se va de baja; tal vez el usuario ya no necesita la licencia; Bueno, quizás - hay obviamente varios motivos de por qué desea quitar una licencia de usuario.
  
Antes de cualquier otra es importante destacar que al eliminar una licencia requiere que, así, eliminar la licencia: deshabilitar todos los servicios en una licencia no es lo mismo que al eliminar una licencia. Por ejemplo, supongamos que hemos utilizado nuestras licencias de Office 365; en otras palabras, no hay disponible ningún tipo de licencias. Decide seguir el procedimiento en [Deshabilitar el acceso a los servicios de Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md) para deshabilitar todos los servicios, digamos, en cuenta de Belinda Newman. ¿Una vez que hacemos que, cuántas licencias tendremos disponible para nosotros? Correcto: cero. Sí, el procedimiento de este tema va a *Deshabilitar* todos los servicios de licencia de Belinda, pero no deshabilitará (es decir, eliminar) la licencia de sí mismo. La licencia seguirán siendo válida y aún se asignará a Belinda Newman. Ella sólo podrá utilizar esa licencia para acceder a los servicios de Office 365.
  
Y que es importante: si desea eliminar una licencia de un usuario primero debe *Quitar* la licencia. Deshabilitar todos los servicios se impide al usuario iniciar sesión en Office 365, pero no libere su licencia. Si desea volver a tomar una licencia que está actualmente asignada a un usuario que necesite ejecutar un comando similar a este, un comando que utiliza el parámetro _RemoveLicenses_ para quitar la licencia asignada previamente a Belinda:
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

Ejecutar ese comando y Belinda Newman ya no se tiene licencia para utilizar Office 365.
  
> [!NOTE]
> Como puede ver, cuando se utiliza el parámetro _RemoveLicenses_ que debe especificar el nombre de la licencia que se va a quitar. Si no está seguro de qué plan de licencias utilizado para asignar una licencia para el usuario sólo tiene que ejecutar un comando como éste:`Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Format-List DisplayName,Licenses`
  
Para comprobar que realmente se ha quitado la licencia, use Get-MsolUser para comprobar la cuenta del usuario en cuestión:
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

Si todo ha ido según el plan, ahora se establecerá la propiedad de **isLicensed** de Belinda `False`:
  
```
UserPrincipalName            DisplayName         isLicensed
-----------------            -----------         ----------
BelindaN@litwareinc.com      Newman, Belinda     False
```

Otra forma de liberar una licencia es mediante la eliminación de la cuenta de usuario. Para obtener más información, vea [eliminar y restaurar cuentas de usuario con Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).
  
## <a name="see-also"></a>Consulte también

Vea los siguientes temas adicionales acerca de cómo administrar usuarios con Office 365 PowerShell:
  
- [Crear cuentas de usuario con PowerShell de Office 365](create-user-accounts-with-office-365-powershell.md)
    
- [Eliminar y restaurar cuentas de usuario con PowerShell de Office 365](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Bloquear cuentas de usuario con PowerShell de Office 365](block-user-accounts-with-office-365-powershell.md)
    
- [Asignar licencias a cuentas de usuario con PowerShell de Office 365](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
Para obtener más información sobre los cmdlets que se usan en estos procedimientos, consulte los siguientes temas:
  
- [Get-Content](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Set-MsolUserLicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
## <a name="new-to-office-365"></a>¿Es la primera vez que usa Office 365?

||
|:-----|
|![El icono reducido de LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **¿Es la primera vez que usa Office 365?**         LinkedIn Learning pone a su disposición vídeos gratuitos de cursos de [Office 365 admins and IT pros](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5). |
   

