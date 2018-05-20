---
title: Información general de Contoso Corporation
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
description: 'Resumen: Conozca la Contoso Corporation como una empresa y la estructura en niveles de sus oficinas de todo el mundo.'
ms.openlocfilehash: 30a6dd23271fbbd5599053b934e6a1af9dc14d12
ms.sourcegitcommit: 8fcf6fd9f0c45a5445654ef811410fca3f4f5512
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2018
---
# <a name="overview-of-the-contoso-corporation"></a>Información general sobre Contoso Corporation

 **Resumen:** Comprender el Contoso Corporation como una empresa y la estructura en niveles de sus oficinas de todo el mundo.
  
Contoso Corporation es una empresa global con sede en París, Francia. Es una organización que agrupa la fabricación, las ventas y el soporte técnico de más de 100 000 productos.  
  
## <a name="the-contoso-corporation"></a>Contoso Corporation

Organización en todo el mundo de Contoso tiene oficinas en las siguientes ubicaciones:
  
**En la figura 1: Oficinas de Contoso todo el mundo**

![Oficinas de la empresa Contoso en todo el mundo](images/Contoso_Poster/Contoso_WW_Org.png)

  
En la figura 1, se muestran la sede central en París, las oficinas de los centros regionales y las oficinas satélite en varios continentes.
  
Las oficinas de Contoso todo el mundo siguen un diseño de tres niveles.
  
- Sede
    
    La oficina central de Contoso Corporation es un campus corporativo grande en las afueras de París con docenas de edificios para las instalaciones de fabricación, ingeniería y administrativas. Todos los centros de datos de Contoso y su presencia en Internet se alojan en las sedes centrales de París.
    
    La sede cuenta con 15 000 empleados.
    
- Centros regionales
    
    Las oficinas de centros regionales sirven a una región específica del mundo con el 60 % de ventas y personal de soporte técnico. Cada centro regional está conectado a la sede de París con un vínculo WAN de ancho de banda alto.  
    
    Cada centro regional tiene un promedio de 2000 trabajadores.
    
- Oficinas satélite
    
    Oficinas satélites contienen 80% ventas y personal de soporte técnico y proporcionan una presencia física y en el sitio para los clientes de Contoso en claves ciudades o regiones subcaracterística. Cada oficina satélite está conectado a un concentrador regional con un vínculo WAN de ancho de banda alto.
    
    Cada oficina satélite tiene un promedio de 250 trabajadores.
    
25% del personal de Contoso es de sólo mobile, con un porcentaje más alto de los trabajadores solo mobile en los concentradores regionales y oficinas satélites. Proporcionar una mejor compatibilidad para los trabajadores solo mobile es un objetivo empresarial importante para Contoso.
  
## <a name="elements-of-contosos-implementation-of-the-microsoft-cloud"></a>Elementos de implementación de Contoso de Microsoft en la nube

Contoso arquitectos de TI han identificado los siguientes elementos al planear la adopción de las ofertas de nube de Microsoft.
  
- Redes
    
    Redes incluyen la conectividad con las ofertas de nube de Microsoft y ancho de banda suficiente para ser eficaz en las cargas máximas. Algunos conectividad será a través de conexiones de Internet locales y algunas estará en toda la infraestructura de red privada de Contoso.
    
    Para obtener más información, vea el póster de [Microsoft en la nube de la red para arquitectos de la empresa](microsoft-cloud-networking-for-enterprise-architects.md) .
   
- Identidad
    
    Contoso utiliza un bosque de Windows Server AD para su proveedor de identidad interna y también permite la federación con proveedores de terceros para clientes y socios. Contoso debe aprovechar el conjunto interno de cuentas para las ofertas de nube de Microsoft. Acceso a aplicaciones basadas en la nube para los clientes y socios debe aprovechar así como los proveedores de identidad de terceros.
    
    Para obtener más información, vea el póster de [Identidad de nube de Microsoft para arquitectos de la empresa](microsoft-cloud-it-architecture-resources.md#identity) .
    
- Seguridad
    
    La seguridad de datos e identidades basados en la nube debe incluir protección de datos, administración de privilegios administrativos, reconocimiento de amenazas e implementación de directivas de control y seguridad de datos.
    
    Para obtener más información, vea el póster de [Seguridad de Microsoft en la nube para arquitectos de la empresa](http://aka.ms/cloudarchsecurity) .
    
- Administración
    
    La administración de aplicaciones basadas en la nube y las cargas de trabajo de SaaS necesitarán la posibilidad de mantener las opciones de configuración, los datos, las cuentas, las directivas y los permisos, así como de supervisar el estado y el rendimiento continuos. Las herramientas de administración del servidor existentes se usarán para administrar máquinas virtuales en IaaS de Azure.
    
## <a name="see-also"></a>See Also

[Contoso en la nube de Microsoft](contoso-in-the-microsoft-cloud.md)
  
[Recursos de arquitectura de TI de la nube de Microsoft](microsoft-cloud-it-architecture-resources.md)

[Mapa de ruta de Enterprise Cloud de Microsoft: Recursos para los responsables de decisiones de TI](https://sway.com/FJ2xsyWtkJc2taRD)
 


