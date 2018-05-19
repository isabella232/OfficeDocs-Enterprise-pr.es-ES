---
title: Entorno de desarrollo y prueba de Microsoft 365 Enterprise
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 6f916a77-301c-4be2-b407-6cec4d80df76
description: 'Resumen: Use esta guía del laboratorio de pruebas para crear un entorno de desarrollo y prueba que incluya Office 365 E5, Enterprise Mobility + Security (EMS) E5 y un equipo con Windows 10 Enterprise.'
ms.openlocfilehash: 5a4c23b3bde309a75a61e574e91823ecdd4629fe
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2018
---
# <a name="the-microsoft-365-enterprise-devtest-environment"></a>Entorno de desarrollo y prueba de Microsoft 365 Enterprise

 **Resumen:** Use esta guía del laboratorio de pruebas para crear un entorno de desarrollo y prueba que incluya Office 365 E5, Enterprise Mobility + Security (EMS) E5 y un equipo con Windows 10 Enterprise.
  
En este artículo se ofrecen instrucciones paso a paso para crear un entorno simplificado para probar las características y funcionalidades de [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise).
  
## <a name="phase-1-create-your-office-365-e5-subscription"></a>Fase 1: Crear la suscripción de Office 365 E5

Siga los pasos los pasos 2 y 3 del [entorno de desarrollo y prueba de Office 365](office-365-dev-test-environment.md) para crear un entorno de desarrollo y prueba ligero de Office 365, tal y como se muestra en la figura 1.
  
**Figura 1: Suscripción de Office 365 E5 con las cuentas de usuario y de espacio empresarial de Azure Active Directory (AD)**

![Fase 1 del entorno de desarrollo y prueba de Microsoft 3656 Enterprise](images/65bb027b-fb59-46eb-aec2-38c0af425168.png)

> [!NOTE]
> La duración de la suscripción de prueba de Office 365 E5 es de 30 días, que puede ampliarse fácilmente a 60 días. Si quiere usar un entorno de desarrollo y prueba permanente, cree una suscripción de pago con un número reducido de licencias. 
  
## <a name="phase-2-add-ems"></a>Fase 2: Agregar EMS

En esta fase se inscribe en la suscripción de evaluación de EMS E5 y la agrega a la misma organización de la suscripción de evaluación de Office 365 E5.
  
En primer lugar, agregue la suscripción de evaluación de EMS E5 y asigne una licencia EMS a su cuenta de administrador global.
  
1. Con una instancia privada de un explorador de Internet, inicie sesión en el portal de Office 365 con las credenciales de la cuenta de administrador global. Para obtener ayuda, vea [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4) (Dónde iniciar sesión en Office 365).
    
2. Haga clic en el icono **Administrador**.
    
3. En el panel de navegación izquierdo de la pestaña **Centro de administración de Office** del explorador, haga clic en **Facturación > Servicios de compra**.
    
4. En la página **Servicios de compra**, busque el elemento **Enterprise Mobility + Security E5**. Mantenga el puntero del mouse sobre ese elemento y haga clic en **Iniciar prueba gratuita**.
    
5. En la página **Confirmar pedido**, haga clic en **Probar ahora**.
    
6. En la página **Recibo del pedido**, haga clic en **Continuar**.
    
7. En el panel de navegación izquierdo de la pestaña **Centro de administración de Office 365** del explorador, haga clic en **Usuarios > Usuarios activos**.
    
8. Haga clic en la cuenta de administrador global y luego en **Editar** para **Licencias de productos**.
    
9. En el panel **Licencias de productos**, cambie la licencia del producto de **Enterprise Mobility + Security E5** a **Activada**, seleccione **Guardar** y, después, haga clic en **Cerrar** dos veces.
    
> [!NOTE]
> La suscripción de prueba a Enterprise Mobility + Security E5 tiene una duración de 90 días. Si quiere usar un entorno de pruebas y desarrollo permanente, cree una nueva suscripción de pago con un número reducido de licencias. 
  
 ***Si ha completado la fase 3 del*** [entorno de desarrollo y prueba de Office 365](office-365-dev-test-environment.md), repita los pasos 8 y 9 del procedimiento anterior para las demás cuentas (usuario 2, usuario 3, usuario 4 y usuario 5).
  
Ahora su entorno de desarrollo y prueba tiene:
  
- Suscripciones de evaluación de Office 365 E5 Enterprise y EMS E5 que comparten el mismo espacio empresarial de AD Azure con la lista de cuentas de usuario.
- Todas las cuentas de usuario adecuadas (ya sea solo la cuenta de administrador global o las cinco cuentas de usuario) están habilitadas para usar Office 365 E5 y EMS E5.
    
La figura 2 muestra la configuración resultante, que agrega EMS.
  
**Figura 2: Adición de la suscripción de evaluación de EMS**

![Fase 2 del entorno de desarrollo y prueba Microsoft 3656 Enterprise](images/8a01a483-3de2-41f3-a845-141c7edd0cb0.png)
  
## <a name="phase-3-create-a-windows-10-enterprise-computer"></a>Fase 3: Crear un equipo con Windows 10 Enterprise

En esta fase se crea un equipo independiente con Windows 10 Enterprise.
  
### <a name="physical-computer"></a>Equipo físico

Obtenga un equipo personal e instale Windows 10 Enterprise en él. Puede descargar la versión de evaluación de Windows 10 Enterprise [aquí](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).
  
### <a name="virtual-machine"></a>Máquina virtual

Cree una máquina virtual con el hipervisor que prefiera e instale Windows 10 Enterprise en ella. Puede descargar la versión de evaluación de Windows 10 Enterprise [aquí](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).
  
### <a name="virtual-machine-in-azure"></a>Máquina virtual de Azure

Para crear una máquina virtual con Windows 10 en Microsoft Azure ***debe tener una suscripción basada en Visual Studio***, que tiene acceso a la imagen de Windows 10 Enterprise. Otros tipos de suscripciones de Azure, como las suscripciones de evaluación y suscripciones de pago, no tienen acceso a esta imagen.
  
> [!NOTE]
> Los siguientes grupos de comandos usan la versión más reciente de Azure PowerShell. Vea [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/) (Introducción a los cmdlets de Azure PowerShell). Estos conjuntos de comandos compilan una máquina virtual con Windows 10 Enterprise llamada WIN10 y toda la infraestructura necesaria, que incluye un grupo de recursos, una cuenta de almacenamiento y una red virtual. Si ya está familiarizado con los servicios de infraestructura de Azure, adapte estas instrucciones para que se ajusten a la infraestructura implementada actualmente. 
  
En primer lugar, abra un símbolo del sistema de Microsoft PowerShell.
  
Inicie sesión en su cuenta de Azure con el siguiente comando.
  
```
Login-AzureRMAccount
```

Obtenga su nombre de suscripción mediante el comando siguiente.
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

Configure su suscripción de Azure. Cambie todo el contenido entrecomillado, incluidos los caracteres \< y >, por los nombres correctos.
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

Después, cree un nuevo grupo de recursos. Para determinar un nombre único de grupo de recursos, use este comando a fin de enumerar los grupos de recursos existentes.
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

Cree el nuevo grupo de recursos con estos comandos. Reemplace todo el contenido entrecomillado, incluidos los caracteres \< y > , por los nombres correctos.
  
```
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

Después, cree una red virtual y la máquina virtual WIN10 con estos comandos. Cuando se le pida, indique el nombre y contraseña de la cuenta de administrador local para WIN10 y guárdelos en un lugar seguro.
  
```
$corpnetSubnet=New-AzureRMVirtualNetworkSubnetConfig -Name Corpnet -AddressPrefix 10.0.0.0/24
New-AzureRMVirtualNetwork -Name "M365Ent-TestLab" -ResourceGroupName $rgName -Location $locName -AddressPrefix 10.0.0.0/8 -Subnet $corpnetSubnet
$rule1=New-AzureRMNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name "M365Ent-TestLab"
$nsg=Get-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name Corpnet -AddressPrefix "10.0.0.0/24" -NetworkSecurityGroup $nsg
$pip=New-AzureRMPublicIpAddress -Name WIN10-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name WIN10-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzureRMVMConfig -VMName WIN10 -VMSize Standard_D1_V2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for WIN10."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName WIN10 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsDesktop -Offer Windows-10 -Skus RS3-Pro -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name WIN10-TestLab-OSDisk -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

## <a name="phase-4-join-your-windows-10-computer-to-azure-ad"></a>Fase 4: Unir el equipo con Windows 10 a Azure AD

Después de crear la máquina física o virtual con Windows 10 Enterprise, inicie sesión con una cuenta de administrador local.
  
> [!NOTE]
> En una máquina virtual en Azure, conéctese con [estas instrucciones](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon). Inicie sesión con las credenciales de la cuenta de administrador local. 
  
Después, una el equipo WIN10 al espacio empresarial de Azure AD de las suscripciones de Office 365 y EMS.
  
1. En el escritorio del equipo WIN10, haga clic en **Inicio > Configuración > Cuentas > Obtener acceso a trabajo o escuela > Conectarse**.
    
2. En el cuadro de diálogo **Set up a work or school account** (Configurar una cuenta profesional o educativa), haga clic en **Join this device to Azure Active Directory** (Unir este dispositivo a Azure Active Directory).
    
3. En **Cuenta profesional o educativa**, escriba el nombre de la cuenta de administrador global de la suscripción de Office 365 y luego haga clic en **Siguiente**.
    
4. En **Escribir contraseña**, escriba la contraseña de la cuenta de administrador global y luego haga clic en **Iniciar sesión**.
    
5. Cuando se le pida que confirme que es su organización, haga clic en **Unir** y luego en **Listo**.
    
6. Cierre la ventana de configuración.
    
Después, instale Office 2016 en el equipo WIN10.
  
1. Abra el explorador de Microsoft Edge e inicie sesión en el portal de Office 365 con las credenciales de la cuenta de administrador global. Para obtener ayuda, vea [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4) (Dónde iniciar sesión en Office 365).
    
2. En la pestaña **Inicio de Microsoft Office**, haga clic en **Instalar Office 2016**.
    
3. Cuando se le pregunte qué hacer, haga clic en **Ejecutar** y luego en **Sí** para **Control de cuentas de usuario**.
    
4. Espere a que se complete la instalación de Office. Cuando vea **You're all set!** (¡Ya está listo!), haga clic en **Cerrar** dos veces.
    
La figura 3 muestra el entorno resultante, que incluye el equipo WIN10 que se ha unido al espacio empresarial de Azure AD de las suscripciones de Office 365 y EMS.
  
**Figura 3: Adición de la cuenta del equipo WIN10 al espacio empresarial de Azure AD**

![Fase 4 del entorno de desarrollo y prueba Microsoft 3656 Enterprise](images/20680f6a-f77e-4333-aaa9-f7cf5e4b0d03.png)
  
Ahora está preparado para experimentar con otras características de [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise).
  
## <a name="next-steps"></a>Siguientes pasos

Use estos artículos adicionales para explorar las características de Microsoft 365 Enterprise:
  
- [Agregar directivas de administración de aplicaciones móviles (MAM)](https://technet.microsoft.com/library/mt764059.aspx)
    
- [Inscribir dispositivos iOS y Android](https://technet.microsoft.com/library/mt743077.aspx)
    
- [Configure and test Advanced Security Management](https://technet.microsoft.com/library/mt757250.aspx) (Configurar y probar la administración de seguridad avanzada)
    
- [Configure and test Advanced Threat Protection](https://technet.microsoft.com/library/mt490479.aspx) (Configurar y probar la protección contra amenazas avanzada)
    
## <a name="see-also"></a>Vea también

- [Documentación y recursos de Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365-enterprise/)
- [Implementar Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365/enterprise/deploy-microsoft-365-enterprise)
- [Entorno de desarrollo y prueba de One Microsoft Cloud](the-one-microsoft-cloud-dev-test-environment.md)
- [Guías del laboratorio de pruebas de adopción de la nube (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
