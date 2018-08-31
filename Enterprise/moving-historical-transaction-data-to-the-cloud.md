---
title: Mover datos de transacción históricos a la nube
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 3e9c405a-415b-4584-aa7e-f2489299c457
description: 'Resumen: Cómo Contoso ha implementado SQL Server Stretch Database para reducir sus necesidades de almacenamiento de datos locales y los costos de ejecución diarios.'
ms.openlocfilehash: 791b5d4f14ba7246221cf9b459c31c9ba1b54099
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915725"
---
# <a name="moving-historical-transaction-data-to-the-cloud"></a>Mover datos de transacción históricos a la nube

 **Resumen:** Cómo Contoso ha implementado SQL Server Stretch Database para reducir sus necesidades de almacenamiento de datos locales y los costos de ejecución diarios.
  
El sistema de almacenamiento empresarial de Contoso almacena una gran cantidad de datos de transacción históricos para adaptarse a los requisitos reglamentarios y para las investigaciones de marketing y análisis de BI de tendencias de gasto. Contoso también necesita restaurar los datos archivados de una cinta magnética; un proceso muy largo. El hardware en el sistema de almacenamiento empresarial de Contoso estaba llegando al final de su ciclo de vida y reemplazarlo resultaría muy costoso. 
  
Como parte de su necesidad empresarial de reducir verticalmente sus centros de datos locales, Contoso ha decidido actualizar a SQL Server 2016 por la característica híbrida de Stretch Database y su perfecta integración con Azure. Stretch Database permite que Contoso mueva los datos inactivos en sus tablas desde el entorno local al almacenamiento en la nube, lo que libera espacio en el disco local y reduce el mantenimiento. Los datos inactivos y activos se encuentran en las mismas tablas y siempre están disponibles para las aplicaciones, los usuarios y el mantenimiento, como copias de seguridad y restauraciones. En la figura 1 se muestra Stretch Database.
  
**Figura 1: SQL Server Stretch Database**

![SQL Server Stretch Database como solución de datos híbrido](media/Contoso-Poster/StretchDB01.png)
  
En la figura 1 se muestra cómo un cliente de SQL envía consultas de T-SQL a un servidor que ejecuta SQL Server 2016, que las reenvía a Azure SQL Stretch Database en PaaS de Azure.
  
Para obtener más información, consulte [Stretch Database](https://msdn.microsoft.com/library/dn935011.aspx).
  
Contoso ha usado estos pasos para mover sus datos históricos a la nube:
  
1. Analizar bases de datos
    
    Se ha realizado un análisis de las tablas de las bases de datos que pretenden moverse a la nube y se han solucionado los problemas. El nuevo Stretch Database Advisor les proporciona información general completa de lo que pueden esperar de todas las características de SQL Server 2016, incluidas las tablas que tienen datos inactivos que podrían extenderse.
    
2. Actualización
    
    Se han actualizado los servidores SQL Server existentes en el centro de datos de la sede central de París a SQL Server 2016.
    
3. Migrar datos inactivos a la nube
    
    Con SQL Management Studio han identificado las bases de datos que se van a extender y las tablas que se van a migrar a instancias de Stretch Database en Azure. Con el paso del tiempo y en segundo plano, SQL Server 2016 ha movido los datos históricos a las bases de datos de Stretch Database en Azure.
    
Aquí se muestra la configuración resultante para un servidor que ejecuta SQL Server 2016 en la sede central de París.
  
**Figura 2: Usar Stretch Database en un servidor del centro de datos de Contoso**

![SQL Server Stretch Database de configuración de Contoso para un solo equipo que ejecuta SQL Server](media/Contoso-Poster/StretchDB02.png)

  
En la figura 2 se muestra cómo las consultas de usuario en un servidor de aplicaciones del centro de datos de Contoso se convierten en consultas SQL que se pasan a Azure SQL Stretch Database en PaaS de Azure.
  
Los usuarios tienen acceso a los datos mediante consultas y aplicaciones existentes. Las directivas de acceso siguen siendo las mismas. Además, no se necesitan copias de seguridad en cinta. El mantenimiento consiste en realizar copias de seguridad y restaurar datos activos.
  
Después de implementar Stretch Database, Contoso:
  
- Ha reducido sus necesidades de almacenamiento de datos locales en un 85 %.
    
- Ha realizado la actualización del sistema de almacenamiento empresarial y la dependencia de archivos de cinta magnética innecesarios.
    
- Ha reducido sus costos de ejecución diarios de manera significativa.
    
## <a name="see-also"></a>Vea también

[Escenarios empresariales para Contoso Corporation](enterprise-scenarios-for-the-contoso-corporation.md)
  
[Contoso en la nube de Microsoft](contoso-in-the-microsoft-cloud.md)
  
[Recursos de arquitectura de TI de la nube de Microsoft](microsoft-cloud-it-architecture-resources.md)

[Stretch Database](https://msdn.microsoft.com/library/dn935011.aspx)
  
[Mapa de ruta de Enterprise Cloud de Microsoft: Recursos para los responsables de la toma de decisiones de TI](https://sway.com/FJ2xsyWtkJc2taRD)




