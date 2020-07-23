---
title: Implementar la sincronización de directorios de Microsoft 365 en Microsoft Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/05/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_Solutions
ms.assetid: b8464818-4325-4a56-b022-5af1dad2aa8b
description: 'Resumen: implemente Azure AD Connect en una máquina virtual en Azure para sincronizar las cuentas entre el directorio local y el inquilino de Azure AD de su suscripción a Microsoft 365.'
ms.openlocfilehash: bd1b973c60576002f110a909c0022b27f4595b81
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/22/2020
ms.locfileid: "45229976"
---
# <a name="deploy-microsoft-365-directory-synchronization-in-microsoft-azure"></a>Implementar la sincronización de directorios de Microsoft 365 en Microsoft Azure

Azure Active Directory (Azure AD) Connect (anteriormente conocido como la herramienta de sincronización de directorios, la herramienta de sincronización de directorios o la herramienta de DirSync.exe) es una aplicación que se instala en un servidor unido a un dominio para sincronizar los usuarios locales de servicios de dominio de Active Directory (AD DS) con el inquilino de Azure AD de su suscripción a Microsoft 365. Microsoft 365 usa Azure AD para su servicio de directorio. Su suscripción a Microsoft 365 incluye un inquilino de Azure AD. Este inquilino también se puede usar para la administración de las identidades de la organización con otras cargas de trabajo en la nube, incluidas otras aplicaciones SaaS y aplicaciones en Azure.

Puede instalar Azure AD Connect en un servidor local, pero también puede instalarlo en una máquina virtual en Azure por los motivos siguientes:
  
- Puede aprovisionar y configurar los servidores basados en la nube con mayor rapidez, y conseguir así que los servicios estén disponibles para los usuarios mucho antes.
- Azure ofrece mejor disponibilidad de sitios con menos esfuerzo.
- Puede reducir el número de servidores locales de su organización.

Esta solución requiere conectividad entre la red local y la red virtual de Azure. Para más información, vea [Conectar una red local con una red virtual de Microsoft Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md). 
  
> [!NOTE]
> En este artículo se describe la sincronización de un único dominio en un único bosque. Azure AD Connect sincroniza todos los dominios de AD DS de su bosque de Active Directory con Microsoft 365. Si tiene varios bosques de Active Directory para sincronizarse con Microsoft 365, consulte [la sincronización de directorios de varios bosques con escenario de inicio de sesión único](https://go.microsoft.com/fwlink/p/?LinkId=393091). 
  
## <a name="overview-of-deploying-microsoft-365-directory-synchronization-in-azure"></a>Información general sobre la implementación de la sincronización de directorios de Microsoft 365 en Azure

El siguiente diagrama muestra Azure AD Connect en ejecución en una máquina virtual en Azure (el servidor de sincronización de directorios) que sincroniza un bosque de AD DS local con una suscripción a Microsoft 365.
  
![Herramienta de Azure AD Connect en una máquina virtual en Azure que sincroniza las cuentas locales con el inquilino de Azure AD de una suscripción a Microsoft 365 con flujo de tráfico](media/CP-DirSyncOverview.png)
  
En el diagrama hay dos redes conectadas por una conexión VPN de sitio a sitio o ExpressRoute. Hay una red local donde se encuentran los controladores de dominio de AD DS y una red virtual de Azure con un servidor de sincronización de directorios, que es una máquina virtual en ejecución en [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). Hay dos flujos de tráfico principal que se originan en el servidor de sincronización de directorios:
  
-  Azure AD Connect consulta un controlador de dominio en la red local para conocer los cambios de cuentas y contraseñas.
-  Azure AD Connect envía los cambios a las cuentas y las contraseñas a la instancia de Azure AD de su suscripción a Microsoft 365. Como el servidor de sincronización de directorios está en una parte extendida de la red local, estos cambios se envían a través del servidor proxy de la red local.
    
> [!NOTE]
> En esta solución se describe la sincronización de un único dominio de Active Directory en un único bosque de Active Directory. Azure AD Connect sincroniza todos los dominios de Active Directory en el bosque de Active Directory con Microsoft 365. Si tiene varios bosques de Active Directory para sincronizarse con Microsoft 365, consulte [la sincronización de directorios de varios bosques con escenario de inicio de sesión único](https://go.microsoft.com/fwlink/p/?LinkId=393091). 
  
Existen dos pasos principales cuando implementa esta solución:
  
1. Crear una red virtual de Azure y establecer una conexión VPN de sitio a sitio en su red local. Para obtener más información, consulte [Conectar una red local con una red virtual de Microsoft Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).
    
2. Instale [Azure ad Connect](https://www.microsoft.com/download/details.aspx?id=47594) en una máquina virtual unida a un dominio en Azure y, a continuación, sincronice AD DS local con Microsoft 365. Esto conlleva lo siguiente:
    
    Crear una Máquina virtual de Azure para ejecutar Azure AD Connect.
    
    Instalar y configurar [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594).
    
    Para configurar Azure AD Connect se necesitan las credenciales (nombre de usuario y contraseña) de una cuenta de administrador de Azure AD y una cuenta de administrador empresarial de AD DS. Azure AD Connect se ejecuta inmediatamente y de manera continua para sincronizar el bosque de AD DS local con Microsoft 365.
    
Antes de implementar esta solución en producción, puede seguir las instrucciones de [la configuración básica empresarial simulada](https://docs.microsoft.com/microsoft-365/enterprise/simulated-ent-base-configuration-microsoft-365-enterprise) para establecer esta configuración como una prueba de concepto, para demostraciones o para experimentación.
  
> [!IMPORTANT]
> Cuando la configuración de Azure AD Connect se completa, no guarda las credenciales de la cuenta de administrador de organización de AD DS. 
  
> [!NOTE]
> Esta solución describe cómo sincronizar un solo bosque de AD DS con Microsoft 365. La topología descrita en este artículo solo representa una manera de implementar esta solución. La topología de la organización puede variar en función de los requisitos de red y las consideraciones de seguridad únicos. 
  
## <a name="plan-for-hosting-a-directory-sync-server-for-microsoft-365-in-azure"></a>Planeación para hospedar un servidor de sincronización de directorios para Microsoft 365 en Azure
<a name="PlanningVirtual"> </a>

### <a name="prerequisites"></a>Requisitos previos

Antes de comenzar, revise los siguientes requisitos previos para esta solución:
  
- Revise el contenido de planeación relacionado en [Planear la red virtual de Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#plan-your-azure-virtual-network).
    
- Asegúrese de que cumple todos los [requisitos previos](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#prerequisites) para configurar la red virtual de Azure.
    
- Tener una suscripción a Microsoft 365 que incluya la característica de integración de Active Directory. Para obtener información acerca de las suscripciones de Microsoft 365, vaya a la [Página de suscripción de microsoft 365](https://products.office.com/compare-all-microsoft-office-products?tab=2).
    
- Aprovisione una máquina virtual de Azure que ejecute Azure AD Connect para sincronizar el bosque de AD DS local con Microsoft 365.
    
    Debe tener las credenciales (nombres y contraseñas) de la cuenta de administrador empresarial de AD DS y una cuenta de administrador de Azure AD.
    
### <a name="solution-architecture-design-assumptions"></a>Suposiciones de diseño de la arquitectura de la solución

En la siguiente lista se describen las elecciones de diseño que se han tomado para esta solución.
  
- Esta solución usa una sola red virtual de Azure con una conexión VPN de sitio a sitio. La red virtual de Azure hospeda una sola subred que solo contiene un servidor, el servidor de sincronización de directorios que ejecuta Azure AD Connect. 
    
- En la red local, hay un controlador de dominio y servidores DNS.
    
- Azure AD Connect realiza la sincronización de hash de contraseña, en lugar de usar el inicio de sesión único. No tiene que implementar una infraestructura de los Servicios de federación de Active Directory (AD FS). Para obtener más información sobre la sincronización de hash de contraseña y las opciones de inicio de sesión único, vea [Seleccionar el método de autenticación adecuado para una solución de identidad híbrida de Azure Active Directory](https://aka.ms/auth-options).
    
Hay otras opciones de diseño adicionales que puede tener en cuenta cuando implementa esta solución en su entorno. Se incluyen las siguientes:
  
- Si hay servidores DNS en una red virtual existente de Azure, determine si desea que el servidor de sincronización de directorios los use para la resolución de nombres, en lugar de usar los servidores DNS de la red local.
    
- Si hay controladores de dominio en una red virtual existente de Azure, determine si la configuración de Sitios y servicios de Active Directory puede suponer una mejor opción. El servidor de sincronización de directorios puede consultar los controladores de dominio de la red virtual de Azure para buscar cambios en las cuentas y las contraseñas, en lugar de usar los controladores de dominio de la red local.
    
## <a name="deployment-roadmap"></a>Guía de implementación

La implementación de Azure AD Connect en una máquina virtual en Azure consta de tres fases:
  
- Fase 1: Creación y configuración de la red virtual de Azure
    
- Fase 2: Creación y configuración de la máquina virtual de Azure
    
- Fase 3: Instalar y configurar Azure AD Connect
    
Después de la implementación, también debe asignar ubicaciones y licencias para las nuevas cuentas de usuario en Microsoft 365.


### <a name="phase-1-create-and-configure-the-azure-virtual-network"></a>Fase 1: Creación y configuración de la red virtual de Azure

Para crear y configurar la red virtual de Azure, complete la [Fase 1: Preparar la red local](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-1-prepare-your-on-premises-network) y la [Fase 2: Crear la red virtual entre locales en Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-2-create-the-cross-premises-virtual-network-in-azure) del plan de implementación de [Conectar una red local a Microsoft Azure Virtual Network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).
  
Esta es la configuración resultante.
  
![Fase 1 del servidor de sincronización de directorios para Microsoft 365 hospedado en Azure](media/aab6a9a4-eb78-4d85-9b96-711e6de420d7.png)
  
En esta figura se muestra una red local conectada a una red virtual de Azure mediante una conexión de ExpressRoute o VPN de sitio a sitio.
  
### <a name="phase-2-create-and-configure-the-azure-virtual-machine"></a>Fase 2: Creación y configuración de la máquina virtual de Azure

Cree la máquina virtual en Azure con las instrucciones [Creación de la primera máquina virtual de Windows en Azure Portal](https://go.microsoft.com/fwlink/p/?LinkId=393098). Use la configuración siguiente:
  
- En el panel **Datos básicos**, seleccione la misma suscripción, ubicación y grupo de recursos que la red virtual. Registre el nombre de usuario y la contraseña en un lugar seguro. Los necesitará posteriormente para conectarse a la máquina virtual.
    
- En el panel **Elija un tamaño**, seleccione el tamaño **A2 estándar**.
    
- En la sección **Almacenamiento** del panel **Configuración**, seleccione el tipo de almacenamiento **Estándar**. En la sección **Red**, seleccione el nombre de la red virtual y la subred que van a hospedar el servidor de sincronización de directorios (no la subred de puerta de enlace). Deje todas las demás opciones con sus valores predeterminados.
    
Compruebe que el servidor de sincronización de directorios usa DNS correctamente. Para ello, compruebe su DNS interno y asegúrese de que se ha agregado un registro de dirección (A) para la máquina virtual con su dirección IP. 
  
Siga las instrucciones de [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon) (Conectarse a la máquina virtual e iniciar sesión) para conectarse al servidor de sincronización de directorios con una conexión a Escritorio remoto. Después de iniciar sesión, una la máquina virtual al dominio de AD DS local.
  
Para que Azure AD Connect obtenga acceso a recursos de Internet, hay que configurar el servidor de sincronización de directorios de modo que use el servidor proxy de la red local. Póngase en contacto con su administrador de red para conocer los pasos de configuración adicionales que debe realizar.
  
Esta es la configuración resultante.
  
![Fase 2 del servidor de sincronización de directorios para Microsoft 365 hospedado en Azure](media/9d8c9349-a207-4828-9b2b-826fe9c06af3.png)
  
En esta figura se muestra la máquina virtual del servidor de sincronización de directorios en la red virtual de Azure entre locales.
  
### <a name="phase-3-install-and-configure-azure-ad-connect"></a>Fase 3: Instalar y configurar Azure AD Connect

Haga lo siguiente:
  
1. Conéctese al servidor de sincronización de directorios mediante una conexión a Escritorio remoto con una cuenta de dominio de AD DS que tenga privilegios de administrador local. Vea [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon) (Conectarse a la máquina virtual e iniciar sesión).
    
2. Desde el servidor de sincronización de directorios, abra el artículo [configurar la sincronización de directorios para Microsoft 365](set-up-directory-synchronization.md) y siga las instrucciones para la sincronización de directorios con la sincronización de hash de contraseña.
    
> [!CAUTION]
> El programa de instalación crea la cuenta **AAD_xxxxxxxxxxxx** en la unidad organizativa (UO) de usuarios locales. No mueva ni quite esta cuenta porque entonces se producirá un error de sincronización.
  
Esta es la configuración resultante.
  
![Fase 3 del servidor de sincronización de directorios para Microsoft 365 hospedado en Azure](media/3f692b62-b77c-4877-abee-83c7edffa922.png)
  
En esta figura se muestra el servidor de sincronización de directorios con Azure AD Connect en la red virtual de Azure entre locales.
  
### <a name="assign-locations-and-licenses-to-users-in-microsoft-365"></a>Asignar ubicaciones y licencias a los usuarios en Microsoft 365

Azure AD Connect agrega cuentas a su suscripción de Microsoft 365 desde AD DS local, pero para que los usuarios inicien sesión en Microsoft 365 y usen sus servicios, las cuentas deben configurarse con una ubicación y licencias. Use estos pasos para agregar la ubicación y activar las licencias para las cuentas de usuario adecuadas:
  
1. Inicie sesión en el [centro de administración de Microsoft 365](https://admin.microsoft.com)y, a continuación, haga clic en **Administrador**.
    
2. En el panel de navegación izquierdo, haga clic en **Usuarios > Usuarios activos**.
    
3. En la lista de las cuentas de usuarios, seleccione la casilla junto al usuario que quiere activar.
    
4. En la página del usuario, haga clic en **Editar** para **Licencias de productos**.
    
5. En la página **Licencias de productos**, seleccione una ubicación para el usuario en **Ubicación** y, después, habilite las licencias adecuadas para el usuario.
    
6. Cuando finalice, haga clic en **Guardar** y, después, haga clic en **Cerrar** dos veces.
    
7. Vuelva al paso 3 para usuarios adicionales.
    
## <a name="see-also"></a>Recursos adicionales

[Adopción de la nube y soluciones híbridas](cloud-adoption-and-hybrid-solutions.yml)
  
[Conectar una red local con una red virtual de Microsoft Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)

[Descargar Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594)
  
[Configurar la sincronización de directorios para Microsoft 365](set-up-directory-synchronization.md)
  
