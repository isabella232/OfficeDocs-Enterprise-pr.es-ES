---
title: "Información general de Contoso Corporation"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 1de16e29-ac2e-40b5-bf13-9301a51e16a8
description: 'Resumen: Comprender la empresa Contoso como un negocio y la estructura en niveles de sus oficinas en todo el mundo.'
ms.openlocfilehash: c00e7fd75f580b82f8f920b9f74551a5e5e1b328
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2018
---
# <a name="overview-of-the-contoso-corporation"></a>Información general sobre Contoso Corporation

 **Resumen:** Comprender la empresa Contoso como un negocio y la estructura en niveles de sus oficinas en todo el mundo.
  
Contoso Corporation es una empresa global con sede en París, Francia. Es una organización que agrupa la fabricación, las ventas y el soporte técnico de más de 100 000 productos.  
  
## <a name="the-contoso-corporation"></a>Contoso Corporation

Organización mundial de Contoso tiene oficinas en las siguientes ubicaciones:
  
**Figura 1: Oficinas de Contoso en el mundo**

![Oficinas de la empresa Contoso en todo el mundo](images/Contoso_Poster/Contoso_WW_Org.png)

  
En la figura 1, se muestran la sede central en París, las oficinas de los centros regionales y las oficinas satélite en varios continentes.
  
Oficinas de Contoso en el mundo siguen un diseño de tres niveles.
  
- Sede
    
    La sede de la empresa Contoso es una gran sede corporativa en las afueras de París con docenas de edificios para instalaciones administrativas, de ingeniería y fabricación. Todos los centros de datos de Contoso y su presencia en Internet se albergan en la sede de París.
    
    La sede cuenta con 15 000 empleados.
    
- Centros regionales
    
    Las oficinas de centros regionales sirven a una región específica del mundo con el 60 % de ventas y personal de soporte técnico. Cada centro regional está conectado a la sede de París con un vínculo WAN de ancho de banda alto.  
    
    Cada centro regional tiene un promedio de 2000 trabajadores.
    
- Oficinas satélite
    
    Oficinas satélite contienen 80% ventas y personal de soporte técnico y proporcionan una presencia física y a domicilio para los clientes de Contoso en ciudades clave o subregiones. Cada sucursal está conectado a un concentrador regional con un vínculo WAN de gran ancho de banda.
    
    Cada oficina satélite tiene un promedio de 250 trabajadores.
    
25% de los empleados de Contoso es sólo móvil, con un porcentaje más alto de los trabajadores móviles sólo en los centros regionales y sucursales. Proporcionar una mejor compatibilidad para los trabajadores móviles sólo es un objetivo de negocios importantes de Contoso.
  
## <a name="elements-of-contosos-implementation-of-the-microsoft-cloud"></a>Elementos de la implementación de Contoso de Microsoft la nube

Contoso arquitectos de TI han identificado los siguientes elementos al planear la adopción de las ofertas de nube de Microsoft.
  
- Conexión de red
    
    Red incluye la conectividad con las ofertas de nube de Microsoft y el ancho de banda suficiente para ser eficaz en las cargas máximas. Conectividad será a través de conexiones de Internet local y algunas estarán en toda la infraestructura de la red privada de Contoso.
    
    Para obtener más información, consulte el póster de [Redes de nube de Microsoft para Enterprise Architects](microsoft-cloud-networking-for-enterprise-architects.md) .
   
- Identidad
    
    Contoso utiliza un bosque de Windows Server AD para su proveedor de identidad interna y también se federa a proveedores de clientes y socios. Contoso debe aprovechar el conjunto interno de cuentas para las ofertas de nube de Microsoft. Acceso a aplicaciones basadas en la nube para clientes y socios debe aprovechar también proveedores de identidad de terceros.
    
    Para obtener más información, consulte el póster de [Identidad de nube de Microsoft para Enterprise Architects](microsoft-cloud-identity-for-enterprise-architects.md) .
    
- Seguridad
    
    La seguridad de datos e identidades basados en la nube debe incluir protección de datos, administración de privilegios administrativos, reconocimiento de amenazas e implementación de directivas de control y seguridad de datos.
    
    Para obtener más información, consulte el póster de [Nube de Microsoft Security for Enterprise Architects](http://aka.ms/cloudarchsecurity) .
    
- Administración
    
    La administración de aplicaciones basadas en la nube y las cargas de trabajo de SaaS necesitarán la posibilidad de mantener las opciones de configuración, los datos, las cuentas, las directivas y los permisos, así como de supervisar el estado y el rendimiento continuos. Las herramientas de administración del servidor existentes se usarán para administrar máquinas virtuales en IaaS de Azure.
    
## <a name="see-also"></a>See Also

[Contoso en la nube de Microsoft](contoso-in-the-microsoft-cloud.md)
  
[Recursos de arquitectura de TI de la nube de Microsoft](microsoft-cloud-it-architecture-resources.md)

[Mapa de ruta de Enterprise Cloud de Microsoft: Recursos para los responsables de decisiones de TI](https://sway.com/FJ2xsyWtkJc2taRD)
 


