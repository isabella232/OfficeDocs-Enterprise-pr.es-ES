---
title: Red virtual simulada entre locales en Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/09/2018
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
ms.assetid: 0a3555dc-6f96-49a5-b9e2-7760e16630b3
description: 'Resumen: cree una red virtual simulada entre locales en Microsoft Azure como un entorno de desarrollo y pruebas.'
ms.openlocfilehash: 595aa20595f43f481aaf090a14d0d7c0df000345
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2019
ms.locfileid: "34162493"
---
# <a name="simulated-cross-premises-virtual-network-in-azure"></a>Red virtual simulada entre locales en Azure

 **Resumen:** cree una red virtual simulada entre locales en Microsoft Azure como un entorno de desarrollo y pruebas.
  
En este artículo se le indicará el proceso de creación de un entorno de nube híbrida simulado con Microsoft Azure mediante dos redes virtuales de Azure. Esta es la configuración resultante. 
  
![Fase 3 del entorno de desarrollo y pruebas de la red virtual simulada entre locales, con la máquina virtual DC2 en la VNet XPrem](media/df458c56-022b-4688-ab18-056c3fd776b4.png)
  
Esta configuración simula un entorno de producción de nube híbrida de IaaS de Azure y está formada por:
  
- Una red local simulada y simplificada alojada en una red virtual de Azure (la red virtual TestLab).
    
- Una red virtual entre locales simulada y alojada en Azure (XPrem).
    
- Una relación de emparejamiento de VNet entre las dos redes virtuales.
    
- Un controlador de dominio secundario en la red virtual XPrem.
    
Estos componentes constituyen la base a partir de la cual puede: 
  
- Desarrollar y probar las aplicaciones en un entorno simulado de nube de híbrida de IaaS de Azure.
    
- Crear configuraciones de prueba de los equipos, algunos dentro de la red virtual TestLab y otros dentro de la red virtual XPrem, para simular cargas de trabajo de TI basadas en nube híbrida.
    
Existen tres fases principales para configurar el entorno de desarrollo y pruebas:
  
1. Configurar la red virtual TestLab.
    
2. Crear la red virtual entre locales.
    
3. Configurar DC2.
    
> [!NOTE]
> Esta configuración necesita una suscripción de pago de Azure. 
  
![Guías del laboratorio de pruebas de Microsoft Cloud](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual de todos los artículos en la pila de la Guía del entorno de pruebas de Office 365.
  
## <a name="phase-1-configure-the-testlab-virtual-network"></a>Fase 1: Configurar la red virtual TestLab

Siga las instrucciones que aparecen en [Configuración básica del entorno de desarrollo y pruebas](base-configuration-dev-test-environment.md) para configurar los equipos DC1, APP1 y CLIENT1 en la red virtual de Azure denominada TestLab.
  
Esta es su configuración actual. 
  
![Fase 4 de la configuración básica en Azure con la máquina virtual CLIENT1](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
## <a name="phase-2-create-the-xprem-virtual-network"></a>Fase 2: Crear la red virtual XPrem

En esta fase, creará y configurará la nueva red virtual XPrem y la conectará a la red virtual TestLab mediante un emparejamiento de VNet.
  
En primer lugar, inicie un símbolo del sistema de Azure PowerShell en el equipo local.
  
> [!NOTE]
> Los siguientes conjuntos de comandos utilizan la última versión de Azure PowerShell. Visite [Get started with Azure PowerShell cmdlets (Introducción a los cmdlets de Azure)](https://docs.microsoft.com/es-ES/powershell/azureps-cmdlets-docs/). 
  
Inicie sesión en su cuenta de Azure con este comando.
  
```
Connect-AzAccount
```

<!--
> [!TIP]
> Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-7844edd0) to get a text file that has all of the PowerShell commands in this article.
-->
  
Obtenga su nombre de suscripción mediante este comando.
  
```
Get-AzSubscription | Sort Name | Select Name
```

Configure su suscripción de Azure. Cambie todo el contenido entrecomillado, incluidos los caracteres \< y >, por los nombres correctos.
  
```
$subscrName="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName
```

Después, cree la red virtual XPrem y protéjala con un grupo de seguridad de red con estos comandos.
  
```
$rgName="<name of the resource group that you used for your TestLab virtual network>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$Testnet=New-AzVirtualNetworkSubnetConfig -Name "Testnet" -AddressPrefix 192.168.0.0/24
New-AzVirtualNetwork -Name "XPrem" -ResourceGroupName $rgName -Location $locName -AddressPrefix 192.168.0.0/16 -Subnet $Testnet -DNSServer 10.0.0.4
$rule1=New-AzNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzNetworkSecurityGroup -Name "Testnet" -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name XPrem
$nsg=Get-AzNetworkSecurityGroup -Name "Testnet" -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name "Testnet" -AddressPrefix 192.168.0.0/24 -NetworkSecurityGroup $nsg
$vnet | Set-AzVirtualNetwork
```

Después, cree la relación de emparejamiento de VNet entre las redes virtuales TestLab y XPrem con estos comandos.
  
```
$rgName="<name of the resource group that you used for your TestLab virtual network>"
$vnet1=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name TestLab
$vnet2=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name XPrem
Add-AzVirtualNetworkPeering -Name TestLab2XPrem -VirtualNetwork $vnet1 -RemoteVirtualNetworkId $vnet2.Id
Add-AzVirtualNetworkPeering -Name XPrem2TestLab -VirtualNetwork $vnet2 -RemoteVirtualNetworkId $vnet1.Id
```

Esta es su configuración actual. 
  
![Fase 2 del entorno de desarrollo y pruebas de la red virtual simulada entre locales, con la relación de emparejamiento de VNet y la VNet XPrem](media/cac5e999-69c7-4f4c-bfce-a7f4006115ef.png)
  
## <a name="phase-3-configure-dc2"></a>Fase 3: Configurar DC2

En esta fase, creará la máquina virtual de DC2 en la red virtual XPrem y, a continuación, la configurará como un controlador de dominio de réplica.
  
En primer lugar, cree una máquina virtual para DC2. Ejecute estos comandos desde el símbolo del sistema de Azure PowerShell en su equipo local.
  
```
$rgName="<your resource group name>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name XPrem -ResourceGroupName $rgName
$pip=New-AzPublicIpAddress -Name DC2-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name DC2-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress 192.168.0.4
$vm=New-AzVMConfig -VMName DC2 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for DC2."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName DC2 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "DC2-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
$diskConfig=New-AzDiskConfig -AccountType "Standard_LRS" -Location $locName -CreateOption Empty -DiskSizeGB 20
$dataDisk1=New-AzDisk -DiskName "DC2-DataDisk1" -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name "DC2-DataDisk1" -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

Después, conéctese a la nueva máquina virtual de DC2 desde [Azure Portal](https://portal.azure.com) con el nombre de cuenta y la contraseña del administrador local.
  
Después, configure una regla de Firewall de Windows para permitir el tráfico durante la prueba de conectividad básica. Desde un símbolo del sistema de Windows PowerShell con el nivel de administrador en DC2, ejecute estos comandos: 
  
```
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
ping dc1.corp.contoso.com
```

El comando ping debería devolver cuatro respuestas correctas de la dirección IP 10.0.0.4. Esta prueba para comprobar el tráfico de la relación de emparejamiento de VNet. 
  
Después, agregue el disco de datos adicional como un volumen nuevo con la letra de unidad F: con estos comandos desde el símbolo del sistema de Windows PowerShell en DC2.
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

Después, configure DC2 como un controlador de dominio de réplica para el dominio corp.contoso.com. Ejecute estos comandos desde el símbolo del sistema de Windows PowerShell en DC2.
  
```
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -Credential (Get-Credential CORP\User1) -DomainName "corp.contoso.com" -InstallDns:$true -DatabasePath "F:\NTDS" -LogPath "F:\Logs" -SysvolPath "F:\SYSVOL"
```

Tenga en cuenta que se le pedirá que proporcione la contraseña de CORP\\User1 y una contraseña del Modo de restauración de servicios de directorio (DSRM), y que reinicie DC2. 
  
Una vez que la red virtual XPrem tenga su propio servidor DNS (DC2), deberá configurarla para que utilice este servidor DNS. Ejecute estos comandos desde el símbolo del sistema de Azure PowerShell en el equipo local.
  
```
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -name "XPrem"
$vnet.DhcpOptions.DnsServers="192.168.0.4" 
Set-AzVirtualNetwork -VirtualNetwork $vnet
Restart-AzVM -ResourceGroupName $rgName -Name "DC2"
```

Desde el equipo local, vaya a Azure Portal y conéctese a DC1 con las credenciales de CORP\\User1. Para configurar el dominio CORP para que usuarios y equipos usen el controlador de dominio local para la autenticación, ejecute estos comandos desde un símbolo del sistema de Windows PowerShell de nivel de administrador en DC1.
  
```
New-ADReplicationSite -Name "TestLab" 
New-ADReplicationSite -Name "XPrem"
New-ADReplicationSubnet -Name "10.0.0.0/8" -Site "TestLab"
New-ADReplicationSubnet -Name "192.168.0.0/16" -Site "XPrem"
```

Esta es su configuración actual. 
  
![Fase 3 del entorno de desarrollo y pruebas de la red virtual simulada entre locales, con la máquina virtual DC2 en la VNet XPrem](media/df458c56-022b-4688-ab18-056c3fd776b4.png)
  
Ya puede probar el entorno simulado de nube híbrida de Azure.
  
## <a name="next-step"></a>Paso siguiente

Use este entorno de desarrollo y pruebas para simular una [granja de servidores de intranet de SharePoint Server 2016 hospedada en Azure](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx).
  
## <a name="see-also"></a>Vea también

[Entorno de desarrollo y pruebas de la configuración básica](base-configuration-dev-test-environment.md)
  
[Entorno de desarrollo y pruebas de Office 365](office-365-dev-test-environment.md)
  
[Sincronización de directorios (DirSync) para el entorno de desarrollo y pruebas de Office 365](dirsync-for-your-office-365-dev-test-environment.md)
  
[Protección contra amenazas avanzada en el entorno de desarrollo y prueba de Office 365](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
  
[Adopción de la nube y soluciones híbridas](cloud-adoption-and-hybrid-solutions.md)


