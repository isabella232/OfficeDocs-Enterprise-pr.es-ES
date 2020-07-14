---
title: Modelos de arquitectura para SharePoint, Exchange, Skype Empresarial y Lync
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/16/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- SPO_Content
f1.keywords:
- CSH
ms.custom:
- Ent_Architecture
ms.assetid: 5b49fa68-f8f2-4705-af96-5f5475e8539a
search.appverid:
- MET150
description: 'Resumen: Obtenga los pósteres de TI que describen los modelos de arquitectura, la implementación y las opciones de plataforma de SharePoint, Exchange, Skype Empresarial y Lync.'
ms.openlocfilehash: 9e6e4f2b32bb2e5b39f8891d8acddc0699cdbf8d
ms.sourcegitcommit: d8ca7017b25d5ddc2771e662e02b62ff2058383b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2020
ms.locfileid: "45102568"
---
# <a name="architectural-models-for-sharepoint-exchange-skype-for-business-and-lync"></a>Modelos de arquitectura para SharePoint, Exchange, Skype Empresarial y Lync

En estos pósteres de TI, se describen los modelos de arquitectura y las opciones de implementación de SharePoint, Exchange, Skype Empresarial y Lync y se proporciona información de diseño para implementar SharePoint en Microsoft Azure.
  
Con Microsoft 365, puede ofrecer servicios de colaboración y comunicación que los usuarios conocen como un servicio basado en la nube. Aparte algunas excepciones, la experiencia de usuario es igual tanto si mantiene una implementación local como si usa Microsoft 365. Esta experiencia de usuario unificada hace que sea menos sencillo decidir dónde colocar cada carga de trabajo y plantea preguntas como:
  
- ¿Cómo se determina qué opción de plataforma elegir para las cargas de trabajo individuales?
    
- ¿Tiene sentido conservar los servicios locales?
    
- ¿En qué escenario resulta adecuada una implementación híbrida?
    
- ¿Cómo encaja Microsoft Azure en este contexto?
    
- ¿Cuáles son las configuraciones compatibles para las cargas de trabajo de Office Server en Azure?
    
> [!TIP]
> Most of the posters on this page are available in multiple languages, including Chinese, English, French, German, Italian, Japanese, Korean, Portuguese, Russian, and Spanish. To download a poster in one of these languages, click the **More languages** link for that poster.
  
Let us know what you think! Send us email at [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com). 
  
Esta página vincula a los pósteres siguientes:
  
- **Pósteres de modelos de arquitectura** Puede usar estos recursos para determinar la plataforma y configuración ideales para SharePoint 2016 y Skype Empresarial 2015.
    
  - [Modelos de arquitectura de Microsoft SharePoint 2016](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2016_ArchModel)
    
  - [Bases de datos de SharePoint Server 2016](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2016_Databases)
    
  - [Modelos de arquitectura de Microsoft Skype Empresarial 2015](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SfB2015_ArchModel)
    
- **Pósteres de opciones de plataforma** Puede usar estos recursos para determinar la plataforma y configuración ideales para SharePoint 2013, Exchange 2013 y Lync 2013.
    
  - [Opciones de plataforma para SharePoint 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2013_Options)
    
  - [Opciones de plataforma para Exchange 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Exch2013_options)
    
  - [Opciones de plataforma para Lync 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Lync2013_Options)
    
- **Pósteres de soluciones de SharePoint Server 2013 en Azure** Puede usar estos pósteres de TI para determinar el diseño y la configuración de las cargas de trabajo de SharePoint Server 2013 en los servicios de infraestructura de Azure.
    
  - [Sitios de Internet en Microsoft Azure con SharePoint Server 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Azure_sharepoint2013)
    
  - [Ejemplo de diseño: Sitios de Internet en Microsoft Azure para SharePoint 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#DesignSampleInternetSites)
    
  - [Recuperación ante desastres de SharePoint en Microsoft Azure](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#sharepoint_recovery_Azure)
    
## <a name="architectural-models-posters"></a>Pósteres de modelos de arquitectura

These new IT posters for SharePoint 2016 and Skype for Business 2015 provide a way to compare the various deployment methods in an easy-to-print format. Each poster provides a list of all the configurations or platform options available and gives you the following information for each option:
  
- **Introducción** Un breve resumen de la plataforma que incluye un diagrama conceptual.
    
- **Ideal para** Escenarios comunes idóneos para la plataforma en particular.
    
- **Requisitos de licencia** Licencias necesarias para realizar la implementación.
    
- **Tareas de arquitectura** Decisiones que debe tomar como arquitecto.
    
- **Tareas o responsabilidades de profesionales de TI** Responsabilidades diarias que el personal de TI necesita planear.
    
<a name="SP2016_ArchModel"> </a>
### <a name="microsoft-sharepoint-2016-architectural-models"></a>Modelos de arquitectura de Microsoft SharePoint 2016

|**Elemento**|**Descripción**|
|:-----|:-----|
|[![Miniatura del póster de modelos de arquitectura de SharePoint 2016](media/7d3e590c-1f3b-42cf-920d-9edac8fa3e04.png)](https://www.microsoft.com/download/details.aspx?id=52650) <br/> [PDF](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.pdf)  \| [Visio](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.vsdx)  \| [Más idiomas](https://www.microsoft.com/download/details.aspx?id=52650) <br/> | En este póster de TI, se describen las configuraciones locales de SharePoint Online, Microsoft Azure y SharePoint que los responsables de la toma de decisiones empresariales y los arquitectos de soluciones necesitan conocer. <br/><br/> - **SharePoint Online (SaaS)**: consuma SharePoint a través de un modelo de suscripción de software como servicio (SaaS). <br/> - **Entorno híbrido de SharePoint**: mueva los sitios y las aplicaciones de SharePoint a la nube a su propio ritmo. <br/> - **SharePoint in Azure (IaaS)** - You extend your on-premises environment into Microsoft Azure and deploy SharePoint 2016 Servers there. (This is recommended for High Availability/Disaster Recovery and dev/test environments.) <br/> - **SharePoint local**: planee, implemente, mantenga y personalice el entorno de SharePoint en un centro de datos mantenido por usted. <br/> |
   
<a name="SP2016_Databases"> </a>
### <a name="sharepoint-server-2016-databases"></a>Bases de datos de SharePoint Server 2016

|**Elemento**|**Descripción**|
|:-----|:-----|
|[![Miniatura del póster de bases de datos de SharePoint Server 2016](media/c53e9de7-3bf8-446d-8766-e6700c8dd8e1.png)          ](https://www.microsoft.com/download/details.aspx?id=55041) <br/> [PDF](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.pdf)  \| [Visio](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.vsdx)  \| [Más idiomas](https://www.microsoft.com/download/details.aspx?id=55041) <br/> | This IT poster is a quick reference guide for SharePoint Server 2016 databases. Each database has the following details: <br/><br/> - Tamaño <br/> - Instrucciones de escalado <br/> - Patrones de E/S <br/> - Requisitos <br/><br/>  The first page has the SharePoint system databases and the service applications that have multiple databases. The second page shows all of the service applications that have single databases. <br/><br/>  Para obtener más información sobre las bases de datos de SharePoint Server 2016, consulte [Tipos y descripciones de bases de datos en SharePoint Server 2016](https://docs.microsoft.com/SharePoint/technical-reference/database-types-and-descriptions) <br/> |
   
<a name="SfB2015_ArchModel"> </a>
### <a name="microsoft-skype-for-business-2015-architectural-models"></a>Modelos de arquitectura de Microsoft Skype Empresarial 2015

|**Elemento**|**Descripción**|
|:-----|:-----|
|[![Miniatura del póster de modelos de arquitectura de Skype Empresarial](media/132288c0-6ae4-4394-88ab-b57dae367714.png)          ](https://www.microsoft.com/download/details.aspx?id=55022) <br/> [PDF](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.pdf)  \| [Visio](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.vsd)  \| [Más idiomas](https://www.microsoft.com/download/details.aspx?id=55022) <br/> |Este póster describe las configuraciones de Skype Empresarial Online, local, híbrido, PBX en la nube y de integración con Exchange y SharePoint que los responsables de la toma de decisiones empresariales y los arquitectos de soluciones necesitan conocer. <br/><br/> Está destinado a los profesionales de TI y pretende dar a conocer los distintos modelos de arquitectura básicos para el consumo de Skype Empresarial Online y Skype Empresarial local. <br/><br/>Start with whichever configuration best suits your organization's needs and future plans. Consider and use others as needed. For example, you might want to consider integration with Exchange and SharePoint or a solution that takes advantage of Microsoft's Cloud PBX offering.  <br/> |
   
## <a name="platform-options-posters"></a>Pósteres de opciones de plataforma

These IT posters for SharePoint 2013, Exchange 2013, and Lync 2013 provide a way to compare the various deployment methods at a single glance in a large poster format. Each poster provides a list of all the configurations or platform options available and gives you the following information for each option:
  
- **Introducción** Un breve resumen de la plataforma que incluye un diagrama conceptual.
    
- **Ideal para** Escenarios comunes idóneos para la plataforma en particular.
    
- **Requisitos de licencia** Licencias necesarias para realizar la implementación.
    
- **Tareas de arquitectura** Decisiones que debe tomar como arquitecto.
    
- **Tareas o responsabilidades de profesionales de TI** Responsabilidades diarias que el personal de TI necesita planear.
    
<a name="SP2013_Options"> </a>
## <a name="sharepoint-2013-platform-options"></a>Opciones de plataforma para SharePoint 2013

****

|**Elemento**|**Descripción**|
|:-----|:-----|
|[![Imagen en miniatura de las opciones de la plataforma de SharePoint 2013](media/SP-PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=40332) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=324594)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=324593)  \| [Más idiomas](https://www.microsoft.com/download/details.aspx?id=40332) <br/> |Para los responsables de la toma de decisiones y arquitectos, en este modelo se muestran las opciones de plataforma para SharePoint 2013, SharePoint en Microsoft 365, implementación local híbrida con Microsoft 365, Azure e implementaciones solo locales. Incluye una descripción general de cada arquitectura, recomendaciones, requisitos de licencia y listas de tareas de arquitecto y profesional de TI para cada plataforma. Se resaltan varias soluciones de SharePoint en Azure. <br/> |
   
<a name="Exch2013_options"> </a>
## <a name="exchange-2013-platform-options"></a>Opciones de plataforma para Exchange 2013

****

|**Elemento**|**Descripción**|
|:-----|:-----|
|[![Imagen en miniatura de las opciones de la plataforma de Exchange](media/ITPro-Other-Exchange2013PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=42676) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkID=398740)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkID=398742)  \| [Más idiomas](https://www.microsoft.com/download/details.aspx?id=42676) <br/> |Para los responsables de la toma de decisiones y arquitectos, en este modelo se describen las opciones de plataforma disponibles para Exchange 2013. Los clientes pueden elegir entre Exchange Online con Microsoft 365, Exchange híbrido, Exchange Server local y Exchange hospedado. El póster incluye información de cada opción arquitectónica, incluidos los escenarios más ideales de cada una, los requisitos de licencias y las responsabilidades de los profesionales de TI. <br/> |
   
<a name="Lync2013_Options"> </a>
## <a name="lync-2013-platform-options"></a>Opciones de plataforma para Lync 2013

****

|**Elemento**|**Descripción**|
|:-----|:-----|
|[![Imagen en miniatura de las opciones de la plataforma de Lync](media/Lync-PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41677) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkID=391837)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkID=391839)  \| [Más idiomas](https://www.microsoft.com/download/details.aspx?id=41677) <br/> |Para los responsables de la toma de decisiones y arquitectos, en este modelo se describen las opciones de plataforma disponibles para Lync 2013. Los clientes pueden elegir entre Lync Online con Microsoft 365, Lync híbrido, Lync Server local y Lync hospedado. El póster de TI incluye información de cada opción arquitectónica, incluidos los escenarios más ideales de cada una, los requisitos de licencias y las responsabilidades de los profesionales de TI.  <br/> |
   
<a name="Lync2013_Options"> </a>
## <a name="sharepoint-in-azure-solutions-posters"></a>Pósteres de soluciones de SharePoint en Azure

En estos pósteres de TI se muestran soluciones basadas en Azure con SharePoint Server 2013 en un formato de póster grande.
  
<a name="Azure_sharepoint2013"> </a>
### <a name="internet-sites-in-microsoft-azure-using-sharepoint-server-2013"></a>Sitios de Internet en Microsoft Azure con SharePoint Server 2013

****

|**Elemento**|**Descripción**|
|:-----|:-----|
|[![Imagen de sitios de Internet en Azure con SharePoint](media/MS-AZ-SPInternetSites.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41992) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)  \| [Más idiomas](https://www.microsoft.com/download/details.aspx?id=41992) <br/> |En este póster se resumen las actividades de diseño claves y las elecciones de arquitecturas recomendadas para sitios accesibles desde Internet en Azure.  <br/><br/> Para obtener más información, consulte los siguientes artículos:  <br/><br/> - [Sitios de Internet en Microsoft Azure con SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md) <br/> - [Arquitecturas de Microsoft Azure para SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) <br/> |
   
<a name="DesignSampleInternetSites"> </a>
### <a name="design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a>Ejemplo de diseño: Sitios de Internet en Microsoft Azure para SharePoint 2013

****

|**Elemento**|**Descripción**|
|:-----|:-----|
|[![Imagen de la muestra de diseño: sitios de Internet en Microsoft Azure para SharePoint 2013](media/MS-AZ-InternetSitesDesignSample.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41991) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)  \| [Más idiomas](https://www.microsoft.com/download/details.aspx?id=41991) <br/> |Use este ejemplo de diseño como punto de partida para su propio sitio de arquitectura accesible desde Internet en Azure con SharePoint Server 2013. <br/><br/> Para obtener más información, consulte los siguientes artículos:  <br/><br/> - [Sitios de Internet en Microsoft Azure con SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md) <br/> - [Arquitecturas de Microsoft Azure para SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) <br/> |
   
<a name="sharepoint_recovery_Azure"> </a>
### <a name="sharepoint-disaster-recovery-to-microsoft-azure"></a>Recuperación ante desastres de SharePoint en Microsoft Azure

****

|**Elemento**|**Descripción**|
|:-----|:-----|
|[![Proceso de recuperación ante desastres de SharePoint en Azure](media/SP-DR-Azure.png)          ](https://www.microsoft.com/download/details.aspx?id=41993) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392554)  \| [Más idiomas](https://www.microsoft.com/download/details.aspx?id=41993) <br/> |En este póster de TI se muestran los principios de arquitectura de un entorno de recuperación ante desastres en Azure. <br/><br/> Para obtener más información, consulte los siguientes artículos:  <br/><br/> - [Recuperación ante desastres de SharePoint Server 2013 en Microsoft Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md) <br/> - [Arquitecturas de Microsoft Azure para SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) <br/> |
   
## <a name="see-also"></a>Vea también

[Adopción de la nube y soluciones híbridas](cloud-adoption-and-hybrid-solutions.yml)
  
[Recursos de arquitectura de TI de Microsoft Cloud](microsoft-cloud-it-architecture-resources.md)
  
[Guías de entornos de pruebas de Microsoft 365 para empresas](https://docs.microsoft.com/microsoft-365/enterprise/m365-enterprise-test-lab-guides)
  
[Soluciones híbridas](hybrid-solutions.md)

