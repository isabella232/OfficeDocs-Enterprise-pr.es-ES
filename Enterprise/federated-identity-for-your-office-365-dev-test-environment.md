---
title: Identidad federada para el entorno de desarrollo y pruebas de Office 365
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
- Strat_O365_Enterprise
- TLG
- Ent_TLGs
ms.assetid: 65a6d687-a16a-4415-9fd5-011ba9c5fd80
description: "Resumen: Configurar la autenticación federada para su entorno de pruebas y desarrollo de Office 365."
ms.openlocfilehash: c88019389e610a60625d6a97881249077477c4ea
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2018
---
# <a name="federated-identity-for-your-office-365-devtest-environment"></a>Identidad federada para el entorno de desarrollo y pruebas de Office 365

 **Resumen:** Configurar la autenticación federada para su entorno de pruebas y desarrollo de Office 365.
  
Office 365 admite la identidad federada. Esto significa que en lugar de realizar la validación de las credenciales de sí mismo, Office 365 se refiere el usuario que se conecta a un servidor de autenticación federados que confía en Office 365. Si las credenciales del usuario son correctas, el servidor de autenticación federada emite un token de seguridad que el cliente envía a Office 365 como prueba de la autenticación. Identidad federada permite la descarga y el escalado de autenticación para una suscripción de Office 365 y escenarios avanzados de autenticación y seguridad.
  
En este artículo, se describe cómo puede configurar la autenticación federada para el entorno de desarrollo y pruebas de Office 365, lo que proporciona el siguiente resultado:
  
**Figura 1: La autenticación federada para el entorno de desarrollo y prueba de Office 365**

![El servidor proxy de la aplicación web agregado a DirSync para el entorno de desarrollo y pruebas de Office 365](images/f50039e4-796a-42c0-bfdc-87c2026b1579.png)
  
La configuración que se muestra en la figura 1 consta de:  
  
- Una suscripción de prueba a Office 365 E5, que expira a los 30 días de su creación.
    
- Una intranet de una organización simplificada conectada a Internet, que consta de cinco máquinas virtuales en una subred de una red virtual de Azure (DC1, APP1, CLIENT1, ADFS1 y PROXY1). Azure AD Connect se ejecuta en APP1 para sincronizar la lista de cuentas del dominio de Windows Server AD con Office 365. PROXY1 recibe las solicitudes de autenticación entrantes. ADFS1 valida las credenciales con DC1 y emite tokens de seguridad.
    
Existen cinco fases para configurar este entorno de desarrollo y pruebas:
  
1. Crear el entorno de desarrollo y pruebas de una empresa simulada de Office 365 con DirSync
    
2. Crear el servidor de AD FS (ADFS1)
    
3. Crear el servidor proxy web (PROXY1)
    
4. Crear un certificado autofirmado y configurar ADFS1 y PROXY1
    
5. Configuración de Office 365 para la identidad federada
    
Para avanzar en la implementación de producción de autenticación federada para Office 365 en Azure, consulte [autenticación federados de alta disponibilidad de implementación para Office 365 en Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md).
  
> [!NOTE]
> No puede configurar este entorno de desarrollo y pruebas con una suscripción de prueba de Azure. 
  
> [!TIP]
> Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual para todos los artículos de la pila de una guía de laboratorio de prueba de nube de Microsoft.
  
## <a name="phase-1-create-the-simulated-enterprise-office-365-devtest-environment-with-dirsync"></a>Fase 1: Crear el entorno de desarrollo y pruebas de una empresa simulada de Office 365 con DirSync

Siga las instrucciones de [sincronización de directorios para el entorno de desarrollo y prueba de Office 365](dirsync-for-your-office-365-dev-test-environment.md) para crear el entorno de desarrollo/pruebas simuladas enterprise Office 365 con APP1 como el servidor de sincronización de directorios y la identidad sincronizada entre Office 365 y el anuncio de Windows Server cuentas en DC1.
  
A continuación, crear un nuevo nombre de dominio DNS público basado en su nombre de dominio actual y agregarlo a su suscripción de Office 365. Se recomienda utilizar el nombre **práctica de prueba.** \<el dominio público >. Por ejemplo, si el nombre de dominio público es contoso.com, agregue el testlab.contoso.com de nombre de dominio público.
  
Para obtener instrucciones sobre cómo crear los registros DNS correctos en tu proveedor de DNS y agregue el dominio a su suscripción de prueba de Office 365, consulte [Adición de usuarios y dominio a Office 365](https://support.office.com/article/Add-users-and-domain-to-Office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611). 
  
Esta es la configuración resultante.
  
**Figura 2: Sincronización de directorios para el entorno de desarrollo y prueba de Office 365**

![El entorno de desarrollo y prueba de Office 365 con DirSync](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
En la figura 2, se muestra DirSync para el entorno de desarrollo y pruebas de Office 365, que incluye Office 365 y las máquinas virtuales CLIENT1, APP1 y DC1 en una red virtual de Azure.
  
## <a name="phase-2-create-the-ad-fs-server"></a>Fase 2: Crear el servidor de AD FS

Un servidor de AD FS proporciona autenticación federada entre Office 365 y las cuentas del dominio corp.contoso.com hospedado en DC1.
  
Para crear una máquina virtual Azure para ADFS1, proporcione el nombre de la suscripción y el grupo de recursos y la ubicación Azure para su configuración de Base y, a continuación, ejecutar estos comandos en el símbolo del sistema de PowerShell de Azure en el equipo local.
  
```
$subscr="<your Azure subscription name>"
$rgName="<the resource group name of your Base Configuration>"
Login-AzureRMAccount
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
$staticIP="10.0.0.100"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip = New-AzureRMPublicIpAddress -Name ADFS1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic = New-AzureRMNetworkInterface -Name ADFS1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName ADFS1 -VMSize Standard_D2_v2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for ADFS1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName ADFS1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "ADFS-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!TIP]
> Haga clic [aquí](https://gallery.technet.microsoft.com/PowerShell-commands-for-f79bc2c2?redir=0) para obtener un archivo de texto que contiene todos los comandos de PowerShell en este artículo.
  
A continuación, utilizar el [portal de Azure](http://portal.azure.com) para conectarse a la máquina virtual de ADFS1 con el nombre de la cuenta Administrador local ADFS1 y la contraseña y, a continuación, abra un símbolo del sistema de Windows PowerShell.
  
Para comprobar la comunicación de red y de resolución de nombre entre ADFS1 y DC1, ejecute el comando **ping dc1.corp.contoso.com** y compruebe que hay cuatro respuestas.
  
A continuación, una la máquina virtual de ADFS1 al dominio CORP con estos comandos en un símbolo del sistema de Windows PowerShell en ADFS1.
  
```
$cred=Get-Credential -UserName "CORP\\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

Esta es la configuración resultante.
  
**Figura 3: Agregar el servidor de AD FS**

![El servidor de AD FS agregado a DirSync para el entorno de desarrollo y pruebas de Office 365](images/da82f39e-426d-41e2-842a-c13b382d63d5.png)
  
En la figura 3, se muestra la adición del servidor de ADFS1 a DirSync para el entorno de desarrollo y pruebas de Office 365.
  
## <a name="phase-3-create-the-web-proxy-server"></a>Fase 3: Crear el servidor proxy web

PROXY1 proporciona crear conexiones proxy de mensajes de autenticación entre usuarios que intentan autenticarse y ADFS1.
  
Para crear una máquina virtual de Azure para PROXY1, indique el nombre de su grupo de recursos y una ubicación de Azure y, después, ejecute estos comandos en el símbolo del sistema de Azure PowerShell en el equipo local.
  
```
$rgName="<the resource group name of your Base Configuration>"
$staticIP="10.0.0.101"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip = New-AzureRMPublicIpAddress -Name PROXY1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Static
$nic = New-AzureRMNetworkInterface -Name PROXY1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName PROXY1 -VMSize Standard_D2_v2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for PROXY1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName PROXY1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "PROXY1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> PROXY1 se asigna como una dirección IP pública estática porque creará un registro DNS público que la señale y no debe cambiarse cuando reinicie la máquina virtual de PROXY1. 
  
A continuación, agregar una regla para el grupo de seguridad de red de la subred de la red corporativa para permitir el tráfico entrante no solicitado de Internet a la dirección IP privada de PROXY1 y el puerto TCP 443. Ejecutar estos comandos en el símbolo del sistema de PowerShell de Azure en el equipo local.
  
```
$rgName="<the resource group name of your Base Configuration>"
Get-AzureRmNetworkSecurityGroup -Name CorpNet -ResourceGroupName $rgName | Add-AzureRmNetworkSecurityRuleConfig -Name "HTTPS-to-PROXY1" -Description "Allow TCP 443 to PROXY1" -Access "Allow" -Protocol "Tcp" -Direction "Inbound" -Priority 101 -SourceAddressPrefix "Internet" -SourcePortRange "*" -DestinationAddressPrefix "10.0.0.101" -DestinationPortRange "443" | Set-AzureRmNetworkSecurityGroup
```

A continuación, utilizar el [portal de Azure](http://portal.azure.com) para conectarse a la máquina virtual de PROXY1 utilizando el nombre de la cuenta Administrador local PROXY1 y la contraseña y, a continuación, abra un símbolo del sistema de Windows PowerShell PROXY1.
  
Para comprobar la comunicación de red y de resolución de nombre entre PROXY1 y DC1, ejecute el comando **ping dc1.corp.contoso.com** y compruebe que hay cuatro respuestas.
  
A continuación, una la máquina virtual de PROXY1 al dominio CORP con estos comandos en un símbolo del sistema de Windows PowerShell en PROXY1.
  
```
$cred=Get-Credential -UserName "CORP\\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

Muestre la dirección IP pública de PROXY1 con estos comandos de Azure PowerShell en el equipo local:
  
```
Write-Host (Get-AzureRMPublicIpaddress -Name "PROXY1-PIP" -ResourceGroup $rgName).IPAddress
```

A continuación, trabajar con tu proveedor de DNS público y crear un nuevo registro A DNS público para **fs.testlab.** \<el nombre de dominio > que se resuelve en la dirección IP mostrada por el comando **Write-Host** . El **fs.testlab.** \<el nombre de dominio > es en lo sucesivo denominado el *FQDN del servicio de federación* .
  
A continuación, usar el [portal de Azure](http://portal.azure.com) para conectarse a la máquina virtual de DC1 utilizando el CORP\\credenciales de Usuario1 y, a continuación, ejecute los siguientes comandos en un símbolo de Windows PowerShell de nivel de administrador:
  
```
$testZone="<the FQDN of your testlab domain from phase 1, example: testlab.contoso.com>"
$testZoneFile= $testZone + ".dns"
Add-DnsServerPrimaryZone -Name $testZone -ZoneFile $testZoneFile
Add-DnsServerResourceRecordA -Name "fs" -ZoneName $testZone -AllowUpdateAny -IPv4Address "10.0.0.100" -TimeToLive 01:00:00
```

Estos comandos crean un registro DNS A para su FQDN del Servicio de federación que las máquinas virtuales de la red virtual de Azure pueden resolver en la dirección IP privada de ADFS1.
  
Esta es la configuración resultante.
  
**Figura 4: Agregar el servidor de proxy de aplicación web**

![El servidor proxy de la aplicación web agregado a DirSync para el entorno de desarrollo y pruebas de Office 365](images/f50039e4-796a-42c0-bfdc-87c2026b1579.png)
  
En la figura 4, se muestra la adición del servidor de PROXY1.
  
## <a name="phase-4-create-a-self-signed-certificate-and-configure-adfs1-and-proxy1"></a>Fase 4: Crear un certificado autofirmado y configurar ADFS1 y PROXY1

En esta fase, crea un certificado digital autofirmado para su FQDN del Servicio de federación y configura ADFS1 y PROXY1 como una granja de servidores de AD FS.
  
En primer lugar, usar el [portal de Azure](http://portal.azure.com) para conectarse a la máquina virtual de DC1 utilizando el CORP\\símbolo credenciales de Usuario1 y abra una de Windows PowerShell de nivel de administrador.
  
A continuación, cree una cuenta de servicio de AD FS con este comando en el símbolo del sistema de Windows PowerShell en DC1:
  
```
New-ADUser -SamAccountName ADFS-Service -AccountPassword (read-host "Set user password" -assecurestring) -name "ADFS-Service" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

Tenga en cuenta que este comando le solicita que proporcione la contraseña de la cuenta. Elija una contraseña segura y guárdela en una ubicación segura. La necesitará para esta fase y para la fase 5.
  
Utilice el [portal de Azure](http://portal.azure.com) para conectarse a la máquina virtual de ADFS1 con el CORP\\credenciales de Usuario1. Abra un símbolo de Windows PowerShell de nivel de administrador en ADFS1, rellene su nombre de dominio completo del servicio de federación y ejecute estos comandos para crear un certificado autofirmado:
  
```
$fedServiceFQDN="<federation service FQDN>"
New-SelfSignedCertificate -DnsName $fedServiceFQDN -CertStoreLocation "cert:\\LocalMachine\\My"
New-Item -path c:\\Certs -type directory
New-SmbShare -name Certs -path c:\\Certs -changeaccess CORP\\User1
```

Después, use estos pasos para guardar el nuevo certificado autofirmado como un archivo.
  
1. Haga clic en **Inicio**, escriba **mmc.exe**y, a continuación, presione **ENTRAR**.
    
2. Haga clic en **archivo > Agregar o quitar Snap-in**.
    
3. En **Agregar o quitar complementos**, haga doble clic en **certificados** en la lista de complementos disponibles, haga clic en **cuenta de equipo**y, a continuación, haga clic en **siguiente**.
    
4. En **Seleccionar equipo**, haga clic en **Finalizar**y, a continuación, haga clic en **Aceptar**.
    
5. En el panel de árbol, abra **certificados (equipo Local) > Personal > certificados**.
    
6. Haga clic en el certificado con el FQDN del servicio de federación, haga clic en **todas las tareas**y, a continuación, haga clic en **Exportar**.
    
7. En la página **bienvenida** , haga clic en **siguiente**.
    
8. En la página **Exportar la clave privada** , haga clic en **Sí**y, a continuación, haga clic en **siguiente**.
    
9. En la página **Formato de archivo de exportación** , haga clic en **Exportar todas las propiedades extendidas**y, a continuación, haga clic en **siguiente**.
    
10. En la página **seguridad** , haga clic en **contraseña** y escriba una contraseña en **contraseña** y **Confirmar contraseña.**
    
11. En la página **archivo para exportar** , haga clic en **Examinar**.
    
12. Vaya a la **C:\\certificados** carpeta, escriba **SSL** en **nombre de archivo**y, a continuación, haga clic en **Guardar.**
    
13. En la página **archivo para exportar** , haga clic en **siguiente**.
    
14. En la página **Finalización del Asistente para exportación de certificados** , haga clic en **Finalizar**. Cuando se le pida, haga clic en **Aceptar**.
    
A continuación, instale el servicio de AD FS con este comando en el símbolo del sistema de Windows PowerShell en ADFS1:
  
```
Install-WindowsFeature ADFS-Federation -IncludeManagementTools
```

Espere a que termine la instalación.
  
Después, configure el servicio de AD FS con estos pasos:
  
1. Haga clic en **Inicio**y, a continuación, haga clic en el icono del **Administrador del servidor** .
    
2. En el panel de árbol del Administrador de servidores, haga clic en **AD FS**.
    
3. En la barra de herramientas en la parte superior, haga clic en el símbolo de precaución naranja y, a continuación, haga clic en **Configurar el servicio de federación en este servidor**.
    
4. En **la página el Asistente para la configuración de los servicios de federación de Active Directory,** haga clic en **siguiente**.
    
5. En la página **Conectar con AD DS** , haga clic en **siguiente**.
    
6. En la página **Especificar propiedades de servicio** :
    
  - **Certificado SSL**, haga clic en la flecha abajo y, a continuación, haga clic en el certificado con el nombre de su servicio de federación FQDN.
    
  - En **Nombre de presentación del servicio de federación**, escriba el nombre de la organización ficticia.
    
  - Haga clic en **Siguiente**.
    
7. En la página **Especificar la cuenta de servicio** , haga clic en **Seleccionar** para el **nombre de la cuenta**.
    
8. En **Seleccionar usuario o cuenta de servicio**, escriba **Servicio de ADFS**, haga clic en **Comprobar nombres**y, a continuación, haga clic en **Aceptar**.
    
9. En **Contraseña de la cuenta**, escriba la contraseña de la cuenta de servicio de ADFS y, a continuación, haga clic en **siguiente**.
    
10. En la página **Especificar base de datos de configuración** , haga clic en **siguiente**.
    
11. En la página **Opciones de revisión** , haga clic en **siguiente**.
    
12. En la página **Comprobaciones de requisito previo** , haga clic en **Configurar**.
    
13. En la página de **resultados** , haga clic en **Cerrar**.
    
14. Haga clic en **Inicio**, haga clic en el icono de energía, haga clic en **reiniciar**y, a continuación, haga clic en **continuar**.
    
Desde el [portal de Azure](http://portal.azure.com), conéctese a PROXY1 con el CORP\\las credenciales de la cuenta de Usuario1.
  
A continuación, use estos pasos para instalar el certificado autofirmado y configurar PROXY1.
  
1. Haga clic en **Inicio**, escriba **mmc.exe**y, a continuación, presione **ENTRAR**.
    
2. Haga clic en **archivo > Agregar o quitar Snap-in**.
    
3. En **Agregar o quitar complementos**, haga doble clic en **certificados** en la lista de complementos disponibles, haga clic en **cuenta de equipo**y, a continuación, haga clic en **siguiente**.
    
4. En **Seleccionar equipo**, haga clic en **Finalizar**y, a continuación, haga clic en **Aceptar**.
    
5. En el panel de árbol, abra **certificados (equipo Local) > Personal > certificados**.
    
6. Haga clic en **Personal**, haga clic en **todas las tareas**y, a continuación, haga clic en **Importar**.
    
7. En la página **bienvenida** , haga clic en **siguiente**.
    
8. En la página **archivo para importar** , escriba ** \\ \\adfs1\\certs\\ssl.pfx**y, a continuación, haga clic en **siguiente**.
    
9. En la página de **protección de clave privada** , escriba la contraseña del certificado en la **contraseña**y, a continuación, haga clic en **Siguiente.**
    
10. En la página **almacén de certificados** , haga clic en **Siguiente.**
    
11. En la página de **finalización** , haga clic en **Finalizar**.
    
12. En la página **Almacén de certificados** , haga clic en **siguiente**.
    
13. Cuando se le pida, haga clic en **Aceptar**.
    
14. En el panel de árbol, haga clic en **certificados** .
    
15. Haga clic en el certificado y, a continuación, haga clic en **Copiar**.
    
16. En el panel de árbol, abra **Trusted Root Certification Authorities > certificados**.
    
17. Mueva el puntero del mouse (ratón) debajo de la lista de certificados instalados, ratón y, a continuación, haga clic en **Pegar**.
    
Abra un símbolo del sistema de PowerShell con el nivel de administrador y ejecute el comando siguiente:
  
```
Install-WindowsFeature Web-Application-Proxy -IncludeManagementTools
```

Espere a que termine la instalación.
  
Use estos pasos para configurar el servicio proxy de aplicación web para usar ADFS1 como su servidor de federación:
  
1. Haga clic en **Inicio**y, a continuación, haga clic en **Administrador de servidores**.
    
2. En el panel de árbol, haga clic en **Acceso remoto**.
    
3. En la barra de herramientas en la parte superior, haga clic en el símbolo de precaución naranja y, a continuación, haga clic en **Abrir el Asistente para Proxy de aplicaciones Web**.
    
4. En la página **bienvenida** del Asistente para configuración de Proxy de aplicación Web, haga clic en **siguiente**.
    
5. En la página **Servidor de federación** :
    
  - Escriba el FQDN del servicio de federación en el **nombre de servicio de federación**.
    
  - Tipo de **CORP\\Usuario1** en **nombre de usuario**.
    
  - En **contraseña**, escriba la contraseña para la cuenta de Usuario1.
    
  - Haga clic en **Siguiente**.
    
6. En la página **Certificado de servidor Proxy de AD FS** , haga clic en la flecha hacia abajo, haga clic en el certificado con el servicio de federación FQDN y, a continuación, haga clic en **siguiente**.
    
7. En la página de **confirmación** , haga clic en **Configurar**.
    
8. En la página de **resultados** , haga clic en **Cerrar**.
    
## <a name="phase-5-configure-office-365-for-federated-identity"></a>Fase 5: Configurar Office 365 para la identidad federada

Utilizar el [portal de Azure](http://portal.azure.com) para conectarse a la máquina virtual de APP1 con el CORP\\las credenciales de la cuenta de Usuario1.
  
Use estos pasos para configurar Azure AD Connect y su suscripción de Office 365 para la autenticación federada:
  
1. Desde el escritorio, haga doble clic en **Azure Connect de AD**.
    
2. En la página **Bienvenido a Azure Connect de AD** , haga clic en **Configurar**.
    
3. En la página **tareas adicionales** , haga clic en **cambiar de sesión del usuario**y, a continuación, haga clic en **siguiente**.
    
4. En la página **Conectar a Azure AD** , escriba su nombre de cuenta de administrador global de Office 365 y contraseña y, a continuación, haga clic en **siguiente**.
    
5. En la página **Inicio de sesión de usuario**, haga clic en **Federación con AD FS** y, después, haga clic en **Siguiente**.
    
6. En la página de **conjunto de servidores de AD FS** , haga clic en **utilizar un conjunto existente de AD FS**, escriba **ADFS1** en el **Nombre del servidor**y, a continuación, haga clic en **siguiente**.
    
7. Cuando se le pida las credenciales del servidor, escriba las credenciales de la CORP\\Usuario1 cuenta y, a continuación, haga clic en **Aceptar**.
    
8. En la página credenciales de **Administrador de dominio** , escriba **CORP\\Usuario1** **nombre de usuario** y la contraseña de la cuenta en **contraseña**y, a continuación, haga clic en **siguiente**.
    
9. En la página **cuenta de servicio de AD FS** , escriba **CORP\\servicio de ADFS** en **Nombre de usuario de dominio** y la contraseña de la cuenta en **Contraseña de usuario de dominio**y, a continuación, haga clic en **siguiente**.
    
10. En la página de **Dominio de Active Directory de Azure** , de **dominio**, seleccione el nombre del dominio que previamente creado y agregado a su suscripción de Office 365 en la fase 1 y, a continuación, haga clic en **siguiente**.
    
11. En la página **listo para configurar** , haga clic en **Configurar**.
    
12. En la página **instalación completada** , haga clic en **Comprobar**.
    
    Debe ver mensajes que indican que tanto la configuración de Internet como la de la intranet se han comprobado.
    
13. En la página **Instalación completada**, haga clic en **Salir**.
    
Para demostrar que la autenticación federada está funcionando, haga lo siguiente:
  
1. Abra una nueva instancia privada del explorador en el equipo local y vaya a [https://portal.office.com](https://portal.office.com).
    
2. Para las credenciales de inicio de sesión, escriba **Usuario1 @**\<el dominio creado en la fase 1 >. 
    
    Por ejemplo, si el dominio de prueba es **testlab.contoso.com**, escribiría **user1@testlab.contoso.com**. Presione la tecla TAB o permitir a Office 365 puede redirigir automáticamente.
    
    Ahora debería ver una página de **la conexión es no privada** . Usted está viendo porque hay un certificado autofirmado en ADFS1 que no se puede validar el equipo de escritorio. En una implementación de producción de autenticación federada, utilizaría un certificado de una entidad de certificación de confianza y los usuarios no vería esta página.
    
3. En la página de **la conexión es no privada** , haga clic en **Avanzadas**y, a continuación, haga clic en **continuar con \<al servicio de federación FQDN >**. 
    
4. En la página con el nombre de su organización ficticia, inicie sesión con lo siguiente:
    
  - **CORP\\Usuario1** para el nombre
    
  - La contraseña de la cuenta User1
    
    Debería ver la página **Principal de Microsoft Office** .
    
Este procedimiento muestra que su suscripción de prueba de Office 365 está asociada al dominio corp.contoso.com AD de Windows Server alojado en DC1. A continuación presentamos los aspectos básicos del proceso de autenticación:
  
1. Cuando use el dominio federado que ha creado en la fase 1 en el nombre de cuenta de inicio de sesión, Office 365 redirige su explorador al FQDN del Servicio de federación y a PROXY1.
    
2. PROXY1 envía a su equipo local la página de inicio de sesión de la empresa ficticia.
    
3. Cuando usted envía CORP\\Usuario1 y la contraseña para PROXY1, lo reenvía a ADFS1.
    
4. ADFS1 valida CORP\\Usuario1 y la contraseña con DC1 y envía un token de seguridad de su equipo local.
    
5. El equipo local envía el token de seguridad a Office 365.
    
6. Office 365 valida que ese token de seguridad se haya creado mediante ADFS1 y permite el acceso.
    
Su suscripción de prueba de Office 365 ahora está configurada con la autenticación federada. Puede usar este entorno de desarrollo y pruebas para escenarios de autenticación avanzados.
  
## <a name="next-step"></a>Paso siguiente

Cuando esté listo para implementar la lista para producción, autenticación federados de alta disponibilidad para Office 365 en Azure, consulte [autenticación federados de alta disponibilidad de implementación para Office 365 en Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md).
  
## <a name="see-also"></a>Consulte también

[Guías del laboratorio de pruebas de adopción de la nube (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[Entorno de desarrollo y pruebas de la configuración básica](base-configuration-dev-test-environment.md)
  
[Entorno de desarrollo y pruebas de Office 365](office-365-dev-test-environment.md)
  
[Adopción de la nube y soluciones híbridas](cloud-adoption-and-hybrid-solutions.md)
  
[Implementar la autenticación federada de alta disponibilidad para Office 365 en Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)


