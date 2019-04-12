---
title: Identidad federada para el entorno de desarrollo y prueba de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/09/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 65a6d687-a16a-4415-9fd5-011ba9c5fd80
description: 'Resumen: Configure la autenticación federada para su entorno de desarrollo y prueba de Office 365.'
ms.openlocfilehash: f09aa66fb3183ffa924d6211fb7fa36e7de095eb
ms.sourcegitcommit: 682b180061dc63cd602bee567d5414eae6942572
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2019
ms.locfileid: "31741427"
---
# <a name="federated-identity-for-your-office-365-devtest-environment"></a><span data-ttu-id="eb167-103">Identidad federada para el entorno de desarrollo y prueba de Office 365</span><span class="sxs-lookup"><span data-stu-id="eb167-103">Federated identity for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="eb167-104">**Resumen:** Configurar la autenticación federada para su entorno de desarrollo y prueba de Office 365.</span><span class="sxs-lookup"><span data-stu-id="eb167-104">**Summary:** Configure federated authentication for your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="eb167-p101">Office 365 admite la identidad federada. Esto significa que, en lugar de realizar la validación de las credenciales él mismo, Office 365 dirige al usuario que se conecta a un servidor de autenticación federada en el que Office 365 confía. Si las credenciales del usuario son correctas, el servidor de autenticación federada emite un token de seguridad que el cliente envía luego a Office 365 como prueba de autenticación. La identidad federada permite la descarga y el escalado vertical de autenticación para una suscripción de Office 365 y escenarios avanzados de seguridad y autenticación.</span><span class="sxs-lookup"><span data-stu-id="eb167-p101">Office 365 supports federated identity. This means that instead of performing the validation of credentials itself, Office 365 refers the connecting user to a federated authentication server that Office 365 trusts. If the user's credentials are correct, the federated authentication server issues a security token that the client then sends to Office 365 as proof of authentication. Federated identity allows for the offloading and scaling up of authentication for an Office 365 subscription and advanced authentication and security scenarios.</span></span>
  
<span data-ttu-id="eb167-109">En este artículo, se describe cómo puede configurar la autenticación federada para el entorno de desarrollo y prueba de Office 365, lo que se traduce en el siguiente resultado:</span><span class="sxs-lookup"><span data-stu-id="eb167-109">This article describes how you can configure federated authentication for the Office 365 dev/test environment, resulting in the following:</span></span>
  
**<span data-ttu-id="eb167-110">Figura 1: Autenticación federada para el entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="eb167-110">Figure 1: The federated authentication for Office 365 dev/test environment</span></span>**

![La autenticación federada para el entorno de desarrollo y pruebas de Office 365](media/f50039e4-796a-42c0-bfdc-87c2026b1579.png)
  
<span data-ttu-id="eb167-112">La configuración que se muestra en la figura 1 consta de:</span><span class="sxs-lookup"><span data-stu-id="eb167-112">The configuration shown in Figure 1 consists of:</span></span> 
  
- <span data-ttu-id="eb167-113">Una suscripción de prueba a Office 365 E5, que expira a los 30 días de su creación.</span><span class="sxs-lookup"><span data-stu-id="eb167-113">An Office 365 E5 Trial Subscription, which expires 30 days from when you create it.</span></span>
    
- <span data-ttu-id="eb167-p102">Una intranet de una organización simplificada conectada a Internet que consta de cinco máquinas virtuales en una subred de una red virtual de Azure (DC1, APP1, CLIENT1, ADFS1 y PROXY1). Azure AD Connect se ejecuta en APP1 para sincronizar la lista de cuentas del dominio de Active Directory Domain Services con Office 365. PROXY1 recibe las solicitudes de autenticación entrantes. ADFS1 valida las credenciales con DC1 y emite tokens de seguridad.</span><span class="sxs-lookup"><span data-stu-id="eb167-p102">A simplified organization intranet connected to the Internet, consisting of five virtual machines on a subnet of an Azure virtual network (DC1, APP1, CLIENT1, ADFS1, and PROXY1). Azure AD Connect runs on APP1 to synchronize the list of accounts in the Windows Server AD domain to Office 365. PROXY1 receives the incoming authentication requests. ADFS1 validates credentials with DC1 and issues security tokens.</span></span>
    
<span data-ttu-id="eb167-118">Existen cinco fases para configurar este entorno de desarrollo y pruebas:</span><span class="sxs-lookup"><span data-stu-id="eb167-118">There are five phases to setting up this dev/test environment:</span></span>
  
1. <span data-ttu-id="eb167-119">Crear el entorno de desarrollo y pruebas de una empresa simulada de Office 365 con DirSync</span><span class="sxs-lookup"><span data-stu-id="eb167-119">Create the simulated enterprise Office 365 dev/test environment with DirSync.</span></span>
    
2. <span data-ttu-id="eb167-120">Crear el servidor de AD FS (ADFS1)</span><span class="sxs-lookup"><span data-stu-id="eb167-120">Create the AD FS server (ADFS1).</span></span>
    
3. <span data-ttu-id="eb167-121">Crear el servidor proxy web (PROXY1)</span><span class="sxs-lookup"><span data-stu-id="eb167-121">Create the web proxy server (PROXY1).</span></span>
    
4. <span data-ttu-id="eb167-122">Crear un certificado autofirmado y configurar ADFS1 y PROXY1</span><span class="sxs-lookup"><span data-stu-id="eb167-122">Create a self-signed certificate and configure ADFS1 and PROXY1.</span></span>
    
5. <span data-ttu-id="eb167-123">Configurar Office 365 con identidad federada</span><span class="sxs-lookup"><span data-stu-id="eb167-123">Configure Office 365 for federated identity.</span></span>
    
<span data-ttu-id="eb167-124">Para realizar una implementación de producción de autenticación federada para Office 365 en Azure, consulte [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md).</span><span class="sxs-lookup"><span data-stu-id="eb167-124">To step through a production deployment of federated authentication for Office 365 in Azure, see [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="eb167-125">No puede configurar este entorno de desarrollo y prueba con una suscripción de evaluación de Azure.</span><span class="sxs-lookup"><span data-stu-id="eb167-125">You cannot configure this dev/test environment with an Azure Trial subscription.</span></span> 
  
> [!TIP]
> <span data-ttu-id="eb167-126">Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual de todos los artículos en la pila de la Guía del laboratorio de pruebas de Office 365.</span><span class="sxs-lookup"><span data-stu-id="eb167-126">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Microsoft 365 Enterprise Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-the-simulated-enterprise-office-365-devtest-environment-with-dirsync"></a><span data-ttu-id="eb167-127">Fase 1: Crear el entorno de desarrollo y prueba de una empresa simulada de Office 365 con DirSync</span><span class="sxs-lookup"><span data-stu-id="eb167-127">Phase 1: Create the simulated enterprise Office 365 dev/test environment with DirSync</span></span>

<span data-ttu-id="eb167-128">Siga las instrucciones de [Sincronización de directorios para el entorno de desarrollo y pruebas de Office 365](dirsync-for-your-office-365-dev-test-environment.md) para crear el entorno de desarrollo y pruebas de una empresa simulada de Office 365 con APP1 como servidor de DirSync y la identidad sincronizada entre Office 365 y las cuentas de AD DS en DC1.</span><span class="sxs-lookup"><span data-stu-id="eb167-128">Follow the instructions in [Directory synchronization for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md) to create the simulated enterprise Office 365 dev/test environment with APP1 as the DirSync server and synchronized identity between Office 365 and the Windows Server AD accounts on DC1.</span></span>
  
<span data-ttu-id="eb167-p103">Después, cree un nombre de dominio DNS público en función de su nombre de dominio actual y agréguelo a su suscripción de Office 365. Se recomienda usar el nombre **testlab.**\<su dominio público>. Por ejemplo, si su nombre de dominio público es contoso.com, agregue el nombre de dominio público testlab.contoso.com.</span><span class="sxs-lookup"><span data-stu-id="eb167-p103">Next, create a new public DNS domain name based on your current domain name and add it to your Office 365 subscription. We recommend using the name **testlab.**\<your public domain>. For example, if your public domain name is contoso.com, add the public domain name testlab.contoso.com.</span></span>
  
<span data-ttu-id="eb167-132">Para obtener instrucciones sobre cómo crear los registros DNS correctos en su proveedor DNS y agregar el dominio a la suscripción de evaluación de Office 365, vea [Agregar usuarios y un dominio con el asistente de configuración a Office 365](https://support.office.com/article/Add-users-and-domain-to-Office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611).</span><span class="sxs-lookup"><span data-stu-id="eb167-132">For instructions on how to create the correct DNS records in your DNS provider and add the domain to your Office 365 trial subscription, see [Add users and domain to Office 365](https://support.office.com/article/Add-users-and-domain-to-Office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611).</span></span> 
  
<span data-ttu-id="eb167-133">Este es el resultado de la configuración.</span><span class="sxs-lookup"><span data-stu-id="eb167-133">Here is your resulting configuration.</span></span>
  
**<span data-ttu-id="eb167-134">Figura 2: Sincronización de directorios para el entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="eb167-134">Figure 2: Directory synchronization for the Office 365 dev/test environment</span></span>**

![Entorno de desarrollo y pruebas de Office 365 con sincronización de directorios](media/be5b37b0-f832-4878-b153-436c31546e21.png)
  
<span data-ttu-id="eb167-136">En la figura 2, se muestra la sincronización de directorios para el entorno de desarrollo y prueba de Office 365, que incluye Office 365 y las máquinas virtuales CLIENT1, APP1 y DC1 en una red virtual de Azure.</span><span class="sxs-lookup"><span data-stu-id="eb167-136">Figure 2 shows the directory synchronizationc for Office 365 dev/test environment, which includes Office 365 and CLIENT1, APP1, and DC1 virtual machines in an Azure virtual network.</span></span>
  
## <a name="phase-2-create-the-ad-fs-server"></a><span data-ttu-id="eb167-137">Fase 2: Crear el servidor de AD FS</span><span class="sxs-lookup"><span data-stu-id="eb167-137">Phase 2: Create the AD FS server</span></span>

<span data-ttu-id="eb167-138">Un servidor de AD FS proporciona autenticación federada entre Office 365 y las cuentas del dominio corp.contoso.com hospedado en DC1.</span><span class="sxs-lookup"><span data-stu-id="eb167-138">An AD FS server provides federated authentication between Office 365 and the accounts in the corp.contoso.com domain hosted on DC1.</span></span>
  
<span data-ttu-id="eb167-139">Para crear una máquina virtual de Azure para ADFS1, indique el nombre de la suscripción y del grupo de recursos y una ubicación de Azure para la configuración básica. Después, ejecute estos comandos en el símbolo del sistema de Azure PowerShell en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="eb167-139">To create an Azure virtual machine for ADFS1, fill in the name of your subscription and the resource group and Azure location for your Base Configuration, and then run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$subscrName="<your Azure subscription name>"
$rgName="<the resource group name of your Base Configuration>"
Connect-AzAccount
Select-AzSubscription -SubscriptionName $subscrName
$staticIP="10.0.0.100"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip = New-AzPublicIpAddress -Name ADFS1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic = New-AzNetworkInterface -Name ADFS1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName ADFS1 -VMSize Standard_D2_v2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for ADFS1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName ADFS1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "ADFS-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```
<!--
> [!TIP]
> Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-f79bc2c2?redir=0) for a text file that has all the PowerShell commands in this article.
-->
  
<span data-ttu-id="eb167-140">Después, vaya a [Azure Portal](http://portal.azure.com) para conectarse a la máquina virtual de ADFS1 con el nombre y contraseña de la cuenta de administrador local de ADFS1 y abra un símbolo del sistema de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eb167-140">Next, use the [Azure portal](http://portal.azure.com) to connect to the ADFS1 virtual machine using the ADFS1 local administrator account name and password, and then open a Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="eb167-141">Para comprobar la comunicación de red y la resolución de nombres entre ADFS1 y DC1, ejecute el comando **ping dc1.corp.contoso.com** y compruebe que hay cuatro respuestas.</span><span class="sxs-lookup"><span data-stu-id="eb167-141">To check name resolution and network communication between ADFS1 and DC1, run the **ping dc1.corp.contoso.com** command and check that there are four replies.</span></span>
  
<span data-ttu-id="eb167-142">A continuación, una la máquina virtual de ADFS1 al dominio CORP con estos comandos en un símbolo del sistema de Windows PowerShell en ADFS1.</span><span class="sxs-lookup"><span data-stu-id="eb167-142">Next, join the ADFS1 virtual machine to the CORP domain with these commands at the Windows PowerShell prompt on ADFS1.</span></span>
  
```
$cred=Get-Credential -UserName "CORP\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

<span data-ttu-id="eb167-143">Este es el resultado de la configuración.</span><span class="sxs-lookup"><span data-stu-id="eb167-143">Here is your resulting configuration.</span></span>
  
**<span data-ttu-id="eb167-144">Figura 3: Adición del servidor de AD FS</span><span class="sxs-lookup"><span data-stu-id="eb167-144">Figure 3: Adding the AD FS server</span></span>**

![Servidor de AD FS agregado a DirSync para el entorno de desarrollo y prueba de Office 365](media/da82f39e-426d-41e2-842a-c13b382d63d5.png)
  
<span data-ttu-id="eb167-146">En la figura 3, se muestra la adición del servidor de ADFS1 a DirSync para el entorno de desarrollo y prueba de Office 365.</span><span class="sxs-lookup"><span data-stu-id="eb167-146">Figure 3 shows the addition of the ADFS1 server to the DirSync for Office 365 dev/test environment.</span></span>
  
## <a name="phase-3-create-the-web-proxy-server"></a><span data-ttu-id="eb167-147">Fase 3: Crear el servidor proxy web</span><span class="sxs-lookup"><span data-stu-id="eb167-147">Phase 3: Create the web proxy server</span></span>

<span data-ttu-id="eb167-148">PROXY1 permite crear conexiones proxy de mensajes de autenticación entre usuarios que intentan autenticarse y ADFS1.</span><span class="sxs-lookup"><span data-stu-id="eb167-148">PROXY1 provides proxying of authentication messages between users trying to authenticate and ADFS1.</span></span>
  
<span data-ttu-id="eb167-149">Para crear una máquina virtual de Azure para PROXY1, indique el nombre de su grupo de recursos y una ubicación de Azure y, después, ejecute estos comandos en el símbolo del sistema de Azure PowerShell en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="eb167-149">To create an Azure virtual machine for PROXY1, fill in the name of your resource group and Azure location, and then run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<the resource group name of your Base Configuration>"
$staticIP="10.0.0.101"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip = New-AzPublicIpAddress -Name PROXY1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Static
$nic = New-AzNetworkInterface -Name PROXY1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName PROXY1 -VMSize Standard_D2_v2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for PROXY1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName PROXY1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "PROXY1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> <span data-ttu-id="eb167-150">PROXY1 se asigna como una dirección IP pública estática porque creará un registro DNS público que la señale y no debe cambiarse cuando reinicie la máquina virtual de PROXY1.</span><span class="sxs-lookup"><span data-stu-id="eb167-150">PROXY1 is assigned a static public IP address because you will create a public DNS record that points to it and it must not change when you restart the PROXY1 virtual machine.</span></span> 
  
<span data-ttu-id="eb167-p104">Después, agregue una regla al grupo de seguridad de red para que la subred CorpNet permita tráfico entrante no solicitado desde Internet a la dirección IP privada de PROXY1 y al puerto TCP 443. Ejecute estos comandos desde el símbolo del sistema de Azure PowerShell en su equipo local.</span><span class="sxs-lookup"><span data-stu-id="eb167-p104">Next, add a rule to the network security group for the CorpNet subnet to allow unsolicited inbound traffic from the Internet to PROXY1's private IP address and TCP port 443. Run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<the resource group name of your Base Configuration>"
Get-AzNetworkSecurityGroup -Name CorpNet -ResourceGroupName $rgName | Add-AzNetworkSecurityRuleConfig -Name "HTTPS-to-PROXY1" -Description "Allow TCP 443 to PROXY1" -Access "Allow" -Protocol "Tcp" -Direction "Inbound" -Priority 101 -SourceAddressPrefix "Internet" -SourcePortRange "*" -DestinationAddressPrefix "10.0.0.101" -DestinationPortRange "443" | Set-AzNetworkSecurityGroup
```

<span data-ttu-id="eb167-153">Después, use [Azure Portal](http://portal.azure.com) para conectarse a la máquina virtual de PROXY1 con el nombre y contraseña de la cuenta de administrador local de PROXY1 y luego abra un símbolo del sistema de Windows PowerShell en PROXY1.</span><span class="sxs-lookup"><span data-stu-id="eb167-153">Next, use the [Azure portal](http://portal.azure.com) to connect to the PROXY1 virtual machine using the PROXY1 local administrator account name and password, and then open a Windows PowerShell command prompt on PROXY1.</span></span>
  
<span data-ttu-id="eb167-154">Para comprobar la comunicación de red y la resolución de nombres entre PROXY1 y DC1, ejecute el comando **ping dc1.corp.contoso.com** y compruebe que hay cuatro respuestas.</span><span class="sxs-lookup"><span data-stu-id="eb167-154">To check name resolution and network communication between PROXY1 and DC1, run the **ping dc1.corp.contoso.com** command and check that there are four replies.</span></span>
  
<span data-ttu-id="eb167-155">A continuación, una la máquina virtual de PROXY1 al dominio CORP con estos comandos en un símbolo del sistema de Windows PowerShell en PROXY1.</span><span class="sxs-lookup"><span data-stu-id="eb167-155">Next, join the PROXY1 virtual machine to the CORP domain with these commands at the Windows PowerShell prompt on PROXY1.</span></span>
  
```
$cred=Get-Credential -UserName "CORP\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

<span data-ttu-id="eb167-156">Muestre la dirección IP pública de PROXY1 con estos comandos de Azure PowerShell en el equipo local:</span><span class="sxs-lookup"><span data-stu-id="eb167-156">Display the public IP address of PROXY1 with these Azure PowerShell commands on your local computer:</span></span>
  
```
Write-Host (Get-AzPublicIpaddress -Name "PROXY1-PIP" -ResourceGroup $rgName).IPAddress
```

<span data-ttu-id="eb167-p105">Después, trabaje con su proveedor de DNS público y cree un nuevo registro DNS A público para **fs.testlab.**\<su nombre de dominio DNS> que se resuelva en la dirección IP mostrada mediante el comando **Write-Host**. En lo sucesivo, se hace referencia a **fs.testlab.**\<su nombre de dominio DNS> como FQDN del *Servicio de federación*.</span><span class="sxs-lookup"><span data-stu-id="eb167-p105">Next, work with your public DNS provider and create a new public DNS A record for **fs.testlab.**\<your DNS domain name> that resolves to the IP address displayed by the **Write-Host** command. The **fs.testlab.**\<your DNS domain name> is hereafter referred to as the  *federation service FQDN*  .</span></span>
  
<span data-ttu-id="eb167-159">Después, use [Azure Portal](http://portal.azure.com) para conectarse a la máquina virtual de DC1 con las credenciales de CORP\\User1 y ejecute los siguientes comandos en un símbolo del sistema de Windows PowerShell con nivel de administrador:</span><span class="sxs-lookup"><span data-stu-id="eb167-159">Next, use the [Azure portal](http://portal.azure.com) to connect to the DC1 virtual machine using the CORP\\User1 credentials, and then run the following commands at an administrator-level Windows PowerShell command prompt:</span></span>
  
```
$testZone="<the FQDN of your testlab domain from phase 1, example: testlab.contoso.com>"
$testZoneFile= $testZone + ".dns"
Add-DnsServerPrimaryZone -Name $testZone -ZoneFile $testZoneFile
Add-DnsServerResourceRecordA -Name "fs" -ZoneName $testZone -AllowUpdateAny -IPv4Address "10.0.0.100" -TimeToLive 01:00:00
```

<span data-ttu-id="eb167-160">Estos comandos crean un registro DNS A para su FQDN del Servicio de federación que las máquinas virtuales de la red virtual de Azure pueden resolver en la dirección IP privada de ADFS1.</span><span class="sxs-lookup"><span data-stu-id="eb167-160">These commands create a DNS A record for your federation service FQDN that virtual machines on the Azure virtual network can resolve to ADFS1's private IP address.</span></span>
  
<span data-ttu-id="eb167-161">Este es el resultado de la configuración.</span><span class="sxs-lookup"><span data-stu-id="eb167-161">Here is your resulting configuration.</span></span>
  
**<span data-ttu-id="eb167-162">Figura 4: Adición del servidor proxy de aplicación web</span><span class="sxs-lookup"><span data-stu-id="eb167-162">Figure 4: Adding the web application proxy server</span></span>**

![Servidor proxy de la aplicación web agregado a DirSync para el entorno de desarrollo y prueba de Office 365](media/f50039e4-796a-42c0-bfdc-87c2026b1579.png)
  
<span data-ttu-id="eb167-164">En la figura 4, se muestra la adición del servidor PROXY1.</span><span class="sxs-lookup"><span data-stu-id="eb167-164">Figure 4 shows the addition of the PROXY1 server.</span></span>
  
## <a name="phase-4-create-a-self-signed-certificate-and-configure-adfs1-and-proxy1"></a><span data-ttu-id="eb167-165">Fase 4: Crear un certificado autofirmado y configurar ADFS1 y PROXY1</span><span class="sxs-lookup"><span data-stu-id="eb167-165">Phase 4: Create a self-signed certificate and configure ADFS1 and PROXY1</span></span>

<span data-ttu-id="eb167-166">En esta fase, crea un certificado digital autofirmado para su FQDN del Servicio de federación y configura ADFS1 y PROXY1 como una granja de servidores de AD FS.</span><span class="sxs-lookup"><span data-stu-id="eb167-166">In this phase, you create a self-signed digital certificate for your federation service FQDN and configure ADFS1 and PROXY1 as an AD FS farm.</span></span>
  
<span data-ttu-id="eb167-167">En primer lugar, use [Azure Portal](http://portal.azure.com) para conectarse a la máquina virtual de DC1 con las credenciales de CORP\\User1 y luego abra un símbolo del sistema de Windows PowerShell con nivel de administrador. </span><span class="sxs-lookup"><span data-stu-id="eb167-167">First, use the [Azure portal](http://portal.azure.com) to connect to the DC1 virtual machine using the CORP\\User1 credentials, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="eb167-168">Después, cree una cuenta de servicio de AD FS con este comando en el símbolo del sistema de Windows PowerShell en DC1:</span><span class="sxs-lookup"><span data-stu-id="eb167-168">Next, create AD FS service account with this command at the Windows PowerShell command prompt on DC1:</span></span>
  
```
New-ADUser -SamAccountName ADFS-Service -AccountPassword (read-host "Set user password" -assecurestring) -name "ADFS-Service" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

<span data-ttu-id="eb167-p106">Tenga en cuenta que este comando le solicita que proporcione la contraseña de la cuenta. Elija una contraseña segura y guárdela en una ubicación segura. La necesitará para esta fase y para la fase 5.</span><span class="sxs-lookup"><span data-stu-id="eb167-p106">Note that this command prompts you to supply the account password. Choose a strong password and record it in a secured location. You will need it for this phase and Phase 5.</span></span>
  
<span data-ttu-id="eb167-p107">Use [Azure Portal](http://portal.azure.com) para conectarse a la máquina virtual de ADFS1 con las credenciales de CORP\\User1. Abra un símbolo del sistema de Windows PowerShell con nivel de administrador en ADFS1, indique el FQDN del Servicio de federación y luego ejecute estos comandos para crear un certificado autofirmado:</span><span class="sxs-lookup"><span data-stu-id="eb167-p107">Use the [Azure portal](http://portal.azure.com) to connect to the ADFS1 virtual machine using the CORP\\User1 credentials. Open an administrator-level Windows PowerShell command prompt on ADFS1, fill in your federation service FQDN, and then run these commands to create a self-signed certificate:</span></span>
  
```
$fedServiceFQDN="<federation service FQDN>"
New-SelfSignedCertificate -DnsName $fedServiceFQDN -CertStoreLocation "cert:\LocalMachine\My"
New-Item -path c:\Certs -type directory
New-SmbShare -name Certs -path c:\Certs -changeaccess CORP\User1
```

<span data-ttu-id="eb167-174">Después, use estos pasos para guardar el nuevo certificado autofirmado como archivo.</span><span class="sxs-lookup"><span data-stu-id="eb167-174">Next, use these steps to save the new self-signed certificate as a file.</span></span>
  
1. <span data-ttu-id="eb167-175">Haga clic en **Inicio**, escriba**mmc.exe** y presione **Entrar**.</span><span class="sxs-lookup"><span data-stu-id="eb167-175">Click **Start**, type **mmc.exe**, and then press **Enter**.</span></span>
    
2. <span data-ttu-id="eb167-176">Haga clic en **Archivo > Agregar o quitar complemento**.</span><span class="sxs-lookup"><span data-stu-id="eb167-176">Click **File > Add/Remove Snap-in**.</span></span>
    
3. <span data-ttu-id="eb167-177">En **Agregar o quitar complementos**, haga doble clic en **Certificados** en la lista de complementos disponibles, haga clic en **Cuenta de equipo** y luego en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="eb167-177">In **Add or Remove Snap-ins**, double-click **Certificates** in the list of available snap-ins, click **Computer account**, and then click **Next**.</span></span>
    
4. <span data-ttu-id="eb167-178">En **Seleccionar equipo**, haga clic en **Finalizar** y luego en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="eb167-178">In **Select Computer**, click **Finish**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="eb167-179">En el panel de árbol, abra **Certificados (equipo local) > Personal > Certificados**.</span><span class="sxs-lookup"><span data-stu-id="eb167-179">In the tree pane, open **Certificates (Local Computer) > Personal > Certificates**.</span></span>
    
6. <span data-ttu-id="eb167-180">Haga clic con el botón derecho en el certificado con su FQDN del Servicio de federación, haga clic en **Todas las tareas** y luego en **Exportar**.</span><span class="sxs-lookup"><span data-stu-id="eb167-180">Right-click the certificate with your federation service FQDN, click **All tasks**, and then click **Export**.</span></span>
    
7. <span data-ttu-id="eb167-181">En la página de **bienvenida**, haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="eb167-181">On the **Welcome** page, click **Next**.</span></span>
    
8. <span data-ttu-id="eb167-182">En la página **Exportar clave privada**, haga clic en **Sí** y luego en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="eb167-182">On the **Export Private Key** page, click **Yes**, and then click **Next**.</span></span>
    
9. <span data-ttu-id="eb167-183">En la página **Formato de archivo de exportación**, haga clic en **Exportar todas las propiedades extendidas** y luego en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="eb167-183">On the **Export File Format** page, click **Export all extended properties**, and then click **Next**.</span></span>
    
10. <span data-ttu-id="eb167-184">En la página **Seguridad**, haga clic en **Contraseña** y escriba una contraseña en **Contraseña** y **Confirmar contraseña**.</span><span class="sxs-lookup"><span data-stu-id="eb167-184">On the **Security** page, click **Password** and type a password in **Password** and **Confirm password.**</span></span>
    
11. <span data-ttu-id="eb167-185">En la página **Archivo que se va a exportar**, haga clic en **Examinar**.</span><span class="sxs-lookup"><span data-stu-id="eb167-185">On the **File to Export** page, click **Browse**.</span></span>
    
12. <span data-ttu-id="eb167-186">Vaya a la carpeta **C:\\Certs**, escriba **SSL** en **Nombre de archivo** y luego haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="eb167-186">Browse to the **C:\\Certs** folder, type **SSL** in **File name**, and then click **Save.**</span></span>
    
13. <span data-ttu-id="eb167-187">En la página **Archivo que se va a exportar**, haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="eb167-187">On the **File to Export** page, click **Next**.</span></span>
    
14. <span data-ttu-id="eb167-p108">En la página **Finalización del Asistente para exportación de certificados**, haga clic en **Finalizar**. Cuando se le solicite, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="eb167-p108">On the **Completing the Certificate Export Wizard** page, click **Finish**. When prompted, click **OK**.</span></span>
    
<span data-ttu-id="eb167-190">Después, instale el servicio de AD FS con este comando en el símbolo del sistema de Windows PowerShell en ADFS1:</span><span class="sxs-lookup"><span data-stu-id="eb167-190">Next, install the AD FS service with this command at the Windows PowerShell command prompt on ADFS1:</span></span>
  
```
Install-WindowsFeature ADFS-Federation -IncludeManagementTools
```

<span data-ttu-id="eb167-191">Espere a que termine la instalación.</span><span class="sxs-lookup"><span data-stu-id="eb167-191">Wait for the installation to complete.</span></span>
  
<span data-ttu-id="eb167-192">Después, configure el servicio de AD FS con estos pasos:</span><span class="sxs-lookup"><span data-stu-id="eb167-192">Next, configure the AD FS service with these steps:</span></span>
  
1. <span data-ttu-id="eb167-193">Haga clic en **Inicio** y luego en el icono **Administrador de servidores**.</span><span class="sxs-lookup"><span data-stu-id="eb167-193">Click **Start**, and then click the **Server Manager** icon.</span></span>
    
2. <span data-ttu-id="eb167-194">En el panel de árbol del Administrador de servidores, haga clic en **AD FS**.</span><span class="sxs-lookup"><span data-stu-id="eb167-194">In the tree pane of Server Manager, click **AD FS**.</span></span>
    
3. <span data-ttu-id="eb167-195">En la barra de herramientas de la parte superior, haga clic en el símbolo de advertencia naranja y luego en **Configure el servicio de federación en este servidor**.</span><span class="sxs-lookup"><span data-stu-id="eb167-195">In the tool bar at the top, click the orange caution symbol, and then click **Configure the federation service on this server**.</span></span>
    
4. <span data-ttu-id="eb167-196">En la página **principal** del Asistente para la configuración de los Servicios de federación de Active Directory, haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="eb167-196">On the **Welcome** page of the Active Directory Federation Services Configuration Wizard, click **Next**.</span></span>
    
5. <span data-ttu-id="eb167-197">En la página **Conectarse a AD DS**, haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="eb167-197">On the **Connect to AD DS** page, click **Next**.</span></span>
    
6. <span data-ttu-id="eb167-198">En la página **Especificar propiedades del servicio**:</span><span class="sxs-lookup"><span data-stu-id="eb167-198">On the **Specify Service Properties** page:</span></span>
    
  - <span data-ttu-id="eb167-199">En **Certificado SSL**, haga clic en la flecha abajo y luego en el certificado con el nombre del FQDN del Servicio de federación.</span><span class="sxs-lookup"><span data-stu-id="eb167-199">For **SSL Certificate**, click the down arrow, and then click the certificate with the name of your federation service FQDN.</span></span>
    
  - <span data-ttu-id="eb167-200">En **Nombre para mostrar del Servicio de federación**, escriba el nombre de la organización ficticia.</span><span class="sxs-lookup"><span data-stu-id="eb167-200">In **Federation Service Display Name**, type the name of your fictional organization.</span></span>
    
  - <span data-ttu-id="eb167-201">Haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="eb167-201">Click **Next**.</span></span>
    
7. <span data-ttu-id="eb167-202">En la página **Especificar cuenta de servicio**, haga clic en **Seleccionar** para **Nombre de cuenta**.</span><span class="sxs-lookup"><span data-stu-id="eb167-202">On the **Specify Service Account** page, click **Select** for **Account name**.</span></span>
    
8. <span data-ttu-id="eb167-203">En **Seleccionar usuario o cuenta de servicio**, escriba **Servicio ADFS**, haga clic en **Comprobar nombres** y luego en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="eb167-203">In **Select User or Service Account**, type **ADFS-Service**, click **Check Names**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="eb167-204">En **Contraseña de cuenta**, escriba la contraseña para la cuenta del servicio ADFS y luego en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="eb167-204">In **Account Password**, type the password for the ADFS-Service account, and then click **Next**.</span></span>
    
10. <span data-ttu-id="eb167-205">En la página **Especificar base de datos de configuración**, haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="eb167-205">On the **Specify Configuration Database** page, click **Next**.</span></span>
    
11. <span data-ttu-id="eb167-206">En la página **Revisar opciones**, haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="eb167-206">On the **Review Options** page, click **Next**.</span></span>
    
12. <span data-ttu-id="eb167-207">En la página **Comprobaciones de requisitos previos**, haga clic en **Configurar**.</span><span class="sxs-lookup"><span data-stu-id="eb167-207">On the **Pre-requisite Checks** page, click **Configure**.</span></span>
    
13. <span data-ttu-id="eb167-208">En la página **Resultados**, haga clic en **Cerrar**.</span><span class="sxs-lookup"><span data-stu-id="eb167-208">On the **Results** page, click **Close**.</span></span>
    
14. <span data-ttu-id="eb167-209">Haga clic en **Inicio**, en el icono de encendido/apagado, en **Reiniciar** y luego en **Continuar**.</span><span class="sxs-lookup"><span data-stu-id="eb167-209">Click **Start**, click the power icon, click **Restart**, and then click **Continue**.</span></span>
    
<span data-ttu-id="eb167-210">Desde [Azure Portal](http://portal.azure.com), conéctese a PROXY1 con las credenciales de la cuenta CORP\\User1.</span><span class="sxs-lookup"><span data-stu-id="eb167-210">From the [Azure portal](http://portal.azure.com), connect to PROXY1 with the CORP\\User1 account credentials.</span></span>
  
<span data-ttu-id="eb167-211">Después, siga estos pasos para instalar el certificado autofirmado y configurar PROXY1.</span><span class="sxs-lookup"><span data-stu-id="eb167-211">Next, use these steps to install the self-signed certificate and configure PROXY1.</span></span>
  
1. <span data-ttu-id="eb167-212">Haga clic en **Inicio**, escriba**mmc.exe** y presione **Entrar**.</span><span class="sxs-lookup"><span data-stu-id="eb167-212">Click **Start**, type **mmc.exe**, and then press **Enter**.</span></span>
    
2. <span data-ttu-id="eb167-213">Haga clic en **Archivo > Agregar o quitar complemento**.</span><span class="sxs-lookup"><span data-stu-id="eb167-213">Click **File > Add/Remove Snap-in**.</span></span>
    
3. <span data-ttu-id="eb167-214">En **Agregar o quitar complementos**, haga doble clic en **Certificados** en la lista de complementos disponibles, haga clic en **Cuenta de equipo** y luego en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="eb167-214">In **Add or Remove Snap-ins**, double-click **Certificates** in the list of available snap-ins, click **Computer account**, and then click **Next**.</span></span>
    
4. <span data-ttu-id="eb167-215">En **Seleccionar equipo**, haga clic en **Finalizar** y luego en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="eb167-215">In **Select Computer**, click **Finish**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="eb167-216">En el panel de árbol, abra **Certificados (equipo local) > Personal > Certificados**.</span><span class="sxs-lookup"><span data-stu-id="eb167-216">In the tree pane, open **Certificates (Local Computer) > Personal > Certificates**.</span></span>
    
6. <span data-ttu-id="eb167-217">Haga clic con el botón derecho en **Personal**, haga clic en **Todas las tareas** y luego en **Importar**.</span><span class="sxs-lookup"><span data-stu-id="eb167-217">Right-click **Personal**, click **All tasks**, and then click **Import**.</span></span>
    
7. <span data-ttu-id="eb167-218">En la página de **bienvenida**, haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="eb167-218">On the **Welcome** page, click **Next**.</span></span>
    
8. <span data-ttu-id="eb167-219">En la página **Archivo para importar**, escriba **\\\\adfs1\\certs\\ssl.pfx** y luego haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="eb167-219">On the **File to Import** page, type **\\\\adfs1\\certs\\ssl.pfx**, and then click **Next**.</span></span>
    
9. <span data-ttu-id="eb167-220">En la página **Protección de clave privada**, escriba la contraseña de certificado en **Contraseña** y luego haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="eb167-220">On the **Private key protection** page, type the certificate password in **Password**, and then click **Next.**</span></span>
    
10. <span data-ttu-id="eb167-221">En la página **Almacén de certificados**, haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="eb167-221">On the **Certificate store** page, click **Next.**</span></span>
    
11. <span data-ttu-id="eb167-222">En la página **Completando**, haga clic en **Finalizar**.</span><span class="sxs-lookup"><span data-stu-id="eb167-222">On the **Completing** page, click **Finish**.</span></span>
    
12. <span data-ttu-id="eb167-223">En la página **Almacén de certificados**, haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="eb167-223">On the **Certificate Store** page, click **Next**.</span></span>
    
13. <span data-ttu-id="eb167-224">Cuando se le solicite, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="eb167-224">When prompted, click **OK**.</span></span>
    
14. <span data-ttu-id="eb167-225">Haga clic en **Certificados** en el panel de árbol.</span><span class="sxs-lookup"><span data-stu-id="eb167-225">Click **Certificates** in the tree pane.</span></span>
    
15. <span data-ttu-id="eb167-226">Haga clic con el botón derecho en el certificado y luego haga clic en **Copiar**.</span><span class="sxs-lookup"><span data-stu-id="eb167-226">Right-click the certificate, and then click **Copy**.</span></span>
    
16. <span data-ttu-id="eb167-227">En el panel de árbol, abra **Entidades de certificación raíz de confianza > Certificados**.</span><span class="sxs-lookup"><span data-stu-id="eb167-227">In the tree pane, open **Trusted Root Certification Authorities > Certificates**.</span></span>
    
17. <span data-ttu-id="eb167-228">Mueva el puntero del mouse debajo de la lista de certificados instalados, haga clic con el botón derecho y luego haga clic en **Pegar**.</span><span class="sxs-lookup"><span data-stu-id="eb167-228">Move your mouse pointer below the list of installed certificates, right-click, and then click **Paste**.</span></span>
    
<span data-ttu-id="eb167-229">Abra un símbolo del sistema de PowerShell con el nivel de administrador y ejecute el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="eb167-229">Open an administrator-level PowerShell command prompt and run the following command:</span></span>
  
```
Install-WindowsFeature Web-Application-Proxy -IncludeManagementTools
```

<span data-ttu-id="eb167-230">Espere a que termine la instalación.</span><span class="sxs-lookup"><span data-stu-id="eb167-230">Wait for the installation to complete.</span></span>
  
<span data-ttu-id="eb167-231">Use estos pasos para configurar el servicio proxy de aplicación web para usar ADFS1 como su servidor de federación:</span><span class="sxs-lookup"><span data-stu-id="eb167-231">Use these steps to configure the web application proxy service to use ADFS1 as its federation server:</span></span>
  
1. <span data-ttu-id="eb167-232">Haga clic en **Iniciar** y luego en **Administrador del servidor**.</span><span class="sxs-lookup"><span data-stu-id="eb167-232">Click **Start**, and then click **Server Manager**.</span></span>
    
2. <span data-ttu-id="eb167-233">En el panel de árbol, haga clic en **Acceso remoto**.</span><span class="sxs-lookup"><span data-stu-id="eb167-233">In the tree pane, click **Remote Access**.</span></span>
    
3. <span data-ttu-id="eb167-234">En la barra de herramientas de la parte superior, haga clic en el símbolo de advertencia naranja y luego en **Abrir el Asistente para proxy de aplicación web**.</span><span class="sxs-lookup"><span data-stu-id="eb167-234">In the tool bar at the top, click the orange caution symbol, and then click **Open the Web Application Proxy Wizard**.</span></span>
    
4. <span data-ttu-id="eb167-235">En la página **principal** del Asistente para configuración de Proxy de aplicación web, haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="eb167-235">On the **Welcome** page of the Web Application Proxy Configuration Wizard, click **Next**.</span></span>
    
5. <span data-ttu-id="eb167-236">En la página **Servidor de federación**:</span><span class="sxs-lookup"><span data-stu-id="eb167-236">On the **Federation Server** page:</span></span>
    
  - <span data-ttu-id="eb167-237">Escriba su FQDN del Servicio de federación en **Nombre del Servicio de federación**.</span><span class="sxs-lookup"><span data-stu-id="eb167-237">Type your federation service FQDN in **Federation service name**.</span></span>
    
  - <span data-ttu-id="eb167-238">Escriba **CORP\\User1** en **Nombre de usuario**.</span><span class="sxs-lookup"><span data-stu-id="eb167-238">Type **CORP\\User1** in **User name**.</span></span>
    
  - <span data-ttu-id="eb167-239">Escriba la contraseña de la cuenta User1 en **Contraseña**.</span><span class="sxs-lookup"><span data-stu-id="eb167-239">Type the password for the User1 account in **Password**.</span></span>
    
  - <span data-ttu-id="eb167-240">Haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="eb167-240">Click **Next**.</span></span>
    
6. <span data-ttu-id="eb167-241">En la página **Certificado de proxy de AD FS**, haga clic en la flecha abajo, en el certificado con su FQDN del Servicio de federación y luego en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="eb167-241">On the **AD FS Proxy Certificate** page, click the down arrow, click the certificate with your federation service FQDN, and then click **Next**.</span></span>
    
7. <span data-ttu-id="eb167-242">En la página **Confirmación**, haga clic en **Configurar**.</span><span class="sxs-lookup"><span data-stu-id="eb167-242">On the **Confirmation** page, click **Configure**.</span></span>
    
8. <span data-ttu-id="eb167-243">En la página **Resultados**, haga clic en **Cerrar**.</span><span class="sxs-lookup"><span data-stu-id="eb167-243">On the **Results** page, click **Close**.</span></span>
    
## <a name="phase-5-configure-office-365-for-federated-identity"></a><span data-ttu-id="eb167-244">Fase 5: Configurar Office 365 con identidad federada</span><span class="sxs-lookup"><span data-stu-id="eb167-244">Phase 5: Configure Office 365 for federated identity</span></span>

<span data-ttu-id="eb167-245">Use [Azure Portal](http://portal.azure.com) para conectarse a la máquina virtual de APP1 con las credenciales de la cuenta CORP\\User1.</span><span class="sxs-lookup"><span data-stu-id="eb167-245">Use the [Azure portal](http://portal.azure.com) to connect to the APP1 virtual machine with the CORP\\User1 account credentials.</span></span>
  
<span data-ttu-id="eb167-246">Siga estos pasos para configurar Azure AD Connect y la suscripción de Office 365 con autenticación federada:</span><span class="sxs-lookup"><span data-stu-id="eb167-246">Use these steps to configure Azure AD Connect and your Office 365 subscription for federated authentication:</span></span>
  
1. <span data-ttu-id="eb167-247">En el escritorio, haga doble clic en **Azure AD Connect**.</span><span class="sxs-lookup"><span data-stu-id="eb167-247">From the desktop, double-click **Azure AD Connect**.</span></span>
    
2. <span data-ttu-id="eb167-248">En la página **Bienvenido a Azure AD Connect**, haga clic en **Configurar**.</span><span class="sxs-lookup"><span data-stu-id="eb167-248">On the **Welcome to Azure AD Connect** page, click **Configure**.</span></span>
    
3. <span data-ttu-id="eb167-249">En la página **Tareas adicionales**, haga clic en **Cambiar inicio de sesión de usuario** y luego en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="eb167-249">On the **Additional tasks** page, click **Change user sign-in**, and then click **Next**.</span></span>
    
4. <span data-ttu-id="eb167-250">En la página **Conectar con Azure AD**, escriba el nombre y contraseña de la cuenta de administrador global de Office 365 y luego haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="eb167-250">On the **Connect to Azure AD** page, type your Office 365 global administrator account name and password, and then click **Next**.</span></span>
    
5. <span data-ttu-id="eb167-251">En la página **Inicio de sesión de usuario**, haga clic en **Federación con AD FS** y luego en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="eb167-251">On the **User sign-in** page, click **Federation with AD FS**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="eb167-252">En la página **Granja de AD FS**, haga clic en **Usar una granja de AD FS**, escriba **ADFS1** en **Nombre del servidor** y luego haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="eb167-252">On the **AD FS farm** page, click **Use an existing AD FS farm**, type **ADFS1** in **Server Name**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="eb167-253">Cuando le soliciten las credenciales del servidor, escriba las credenciales de la cuenta CORP\\User1 y luego haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="eb167-253">When prompted for server credentials, enter the credentials of the CORP\\User1 account, and then click **OK**.</span></span>
    
8. <span data-ttu-id="eb167-254">En la página de credenciales **Administrador de dominio**, escriba **CORP\\User1** en **Nombre de usuario** y la contraseña de la cuenta en **Contraseña** y luego haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="eb167-254">On the **Domain Administrator** credentials page, type **CORP\\User1** in **Username** and the account password in **Password**, and then click **Next**.</span></span>
    
9. <span data-ttu-id="eb167-255">En la página **Cuenta del servicio AD FS**, escriba **CORP\\ADFS-Service** en **Nombre de usuario de dominio** y la contraseña de la cuenta en **Contraseña de usuario de dominio** y luego haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="eb167-255">On the **AD FS service account** page, type **CORP\\ADFS-Service** in **Domain Username** and the account password in **Domain User Password**, and then click **Next**.</span></span>
    
10. <span data-ttu-id="eb167-256">En la página **Dominio de Azure AD**, en **Dominio**, seleccione el nombre del dominio que ha creado y agregado anteriormente a la suscripción de Office 365 en la fase 1 y, después, haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="eb167-256">On the **Azure AD Domain** page, in **Domain**, select the name of the domain you previously created and added to your Office 365 subscription in Phase 1, and then click **Next**.</span></span>
    
11. <span data-ttu-id="eb167-257">En la página **Listo para configurar**, haga clic en **Configurar**.</span><span class="sxs-lookup"><span data-stu-id="eb167-257">On the **Ready to configure** page, click **Configure**.</span></span>
    
12. <span data-ttu-id="eb167-258">En la página **Instalación completada**, haga clic en **Comprobar**.</span><span class="sxs-lookup"><span data-stu-id="eb167-258">On the **Installation complete** page, click **Verify**.</span></span>
    
    <span data-ttu-id="eb167-259">Debe ver mensajes que indican que tanto la configuración de Internet como la de la intranet se han comprobado.</span><span class="sxs-lookup"><span data-stu-id="eb167-259">You should see messages indicating that both the intranet and Internet configuration was verified.</span></span>
    
13. <span data-ttu-id="eb167-260">En la página **Instalación completada**, haga clic en **Salir**.</span><span class="sxs-lookup"><span data-stu-id="eb167-260">On the **Installation complete** page, click **Exit**.</span></span>
    
<span data-ttu-id="eb167-261">Para demostrar que la autenticación federada funciona:</span><span class="sxs-lookup"><span data-stu-id="eb167-261">To demonstrate that federated authentication is working:</span></span>
  
1. <span data-ttu-id="eb167-262">Abra una nueva instancia privada del explorador en el equipo local y vaya a[https://admin.microsoft.com](https://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="eb167-262">Open a new private instance of your browser on your local computer and go to [https://admin.microsoft.com](https://admin.microsoft.com).</span></span>
    
2. <span data-ttu-id="eb167-263">Para obtener las credenciales de inicio de sesión, escriba **user1@**\<el dominio que creado en la fase 1>.</span><span class="sxs-lookup"><span data-stu-id="eb167-263">For the sign-in credentials, type **user1@**\<the domain created in Phase 1>.</span></span> 
    
    <span data-ttu-id="eb167-p109">Por ejemplo, si el dominio de prueba es **testlab.contoso.com**, escribirá **user1@testlab.contoso.com**. Presione la tecla TAB o permita que Office 365 lo redirija automáticamente.</span><span class="sxs-lookup"><span data-stu-id="eb167-p109">For example, if your test domain is testlab.contoso.com, you would type user1@testlab.contoso.com. Press TAB or allow Office 365 to automatically redirect you.</span></span>
    
    <span data-ttu-id="eb167-p110">Ahora debe ver una página **Su conexión no es privada**. Está viendo esto porque ha instalado un certificado autofirmado en ADFS1 que su equipo de escritorio no puede validar. En una implementación de producción de autenticación federada, usará un certificado de una entidad de certificación de confianza y sus usuarios no verán esta página.</span><span class="sxs-lookup"><span data-stu-id="eb167-p110">You should now see a **Your connection is not private** page. You are seeing this because you installed a self-signed certificate on ADFS1 that your desktop computer cannot validate. In a production deployment of federated authentication, you would use a certificate from a trusted certification authority and your users would not see this page.</span></span>
    
3. <span data-ttu-id="eb167-269">En la página **Su conexión no es privada**, haga clic en **Avanzadas** y luego en **Continuar con \<su FQDN del Servicio de federación>**.</span><span class="sxs-lookup"><span data-stu-id="eb167-269">On the **Your connection is not private** page, click **Advanced**, and then click **Proceed to \<your federation service FQDN>**.</span></span> 
    
4. <span data-ttu-id="eb167-270">En la página con el nombre de su organización ficticia, inicie sesión con lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="eb167-270">On the page with the name of your fictional organization, sign in with the following:</span></span>
    
  - <span data-ttu-id="eb167-271">**CORP\\User1** como nombre</span><span class="sxs-lookup"><span data-stu-id="eb167-271">**CORP\\User1** for the name</span></span>
    
  - <span data-ttu-id="eb167-272">Contraseña de la cuenta User1</span><span class="sxs-lookup"><span data-stu-id="eb167-272">The password for the User1 account</span></span>
    
    <span data-ttu-id="eb167-273">Debe ver la página **principal de Microsoft Office**.</span><span class="sxs-lookup"><span data-stu-id="eb167-273">You should see the **Microsoft Office Home** page.</span></span>
    
<span data-ttu-id="eb167-p111">En este procedimiento, se muestra que su suscripción de prueba de Office 365 está federada con el dominio corp.contoso.com de AD DS hospedado en DC1. Estos son los conceptos básicos del proceso de autenticación:</span><span class="sxs-lookup"><span data-stu-id="eb167-p111">This procedure demonstrates that your Office 365 trial subscription is federated with the Windows Server AD corp.contoso.com domain hosted on DC1. Here are the basics of the authentication process:</span></span>
  
1. <span data-ttu-id="eb167-276">Cuando use el dominio federado que ha creado en la fase 1 en el nombre de cuenta de inicio de sesión, Office 365 redirige su explorador al FQDN del Servicio de federación y a PROXY1.</span><span class="sxs-lookup"><span data-stu-id="eb167-276">When you use the federated domain that you created in Phase 1 within the sign-in account name, Office 365 redirects your browser to your federation service FQDN and PROXY1.</span></span>
    
2. <span data-ttu-id="eb167-277">PROXY1 envía a su equipo local la página de inicio de sesión de la compañía ficticia.</span><span class="sxs-lookup"><span data-stu-id="eb167-277">PROXY1 sends your local computer the fictional company sign-in page.</span></span>
    
3. <span data-ttu-id="eb167-278">Cuando envía CORP\\User1 y la contraseña a PROXY1, estos se reenvían a ADFS1.</span><span class="sxs-lookup"><span data-stu-id="eb167-278">When you send CORP\\User1 and the password to PROXY1, it forwards them to ADFS1.</span></span>
    
4. <span data-ttu-id="eb167-279">ADFS1 valida CORP\\User1 y la contraseña con DC1 y envía a su equipo local un token de seguridad.</span><span class="sxs-lookup"><span data-stu-id="eb167-279">ADFS1 validates CORP\\User1 and the password with DC1 and sends your local computer a security token.</span></span>
    
5. <span data-ttu-id="eb167-280">El equipo local envía el token de seguridad a Office 365.</span><span class="sxs-lookup"><span data-stu-id="eb167-280">Your local computer sends the security token to Office 365.</span></span>
    
6. <span data-ttu-id="eb167-281">Office 365 valida que ese token de seguridad se haya creado mediante ADFS1 y permite el acceso.</span><span class="sxs-lookup"><span data-stu-id="eb167-281">Office 365 validates that the security token was created by ADFS1 and allows access.</span></span>
    
<span data-ttu-id="eb167-p112">Su suscripción de evaluación de Office 365 ahora está configurada con la autenticación federada. Puede usar este entorno de desarrollo y prueba para escenarios de autenticación avanzados.</span><span class="sxs-lookup"><span data-stu-id="eb167-p112">Your Office 365 trial subscription is now configured with federated authentication. You can use this dev/test environment for advanced authentication scenarios.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="eb167-284">Paso siguiente</span><span class="sxs-lookup"><span data-stu-id="eb167-284">Next Step</span></span>

<span data-ttu-id="eb167-285">Cuando esté listo para implementar la autenticación federada de alta disponibilidad preparada para producción de Office 365 en Azure, consulte [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md).</span><span class="sxs-lookup"><span data-stu-id="eb167-285">When you are ready to deploy production-ready, high availability federated authentication for Office 365 in Azure, see [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="eb167-286">Vea también</span><span class="sxs-lookup"><span data-stu-id="eb167-286">See Also</span></span>

[<span data-ttu-id="eb167-287">Guías del laboratorio de pruebas de adopción de la nube (TLG)</span><span class="sxs-lookup"><span data-stu-id="eb167-287">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="eb167-288">Entorno de desarrollo y pruebas de la configuración básica</span><span class="sxs-lookup"><span data-stu-id="eb167-288">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="eb167-289">Entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="eb167-289">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="eb167-290">Adopción de la nube y soluciones híbridas</span><span class="sxs-lookup"><span data-stu-id="eb167-290">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="eb167-291">Implementar la autenticación federada de alta disponibilidad para Office 365 en Azure</span><span class="sxs-lookup"><span data-stu-id="eb167-291">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)


