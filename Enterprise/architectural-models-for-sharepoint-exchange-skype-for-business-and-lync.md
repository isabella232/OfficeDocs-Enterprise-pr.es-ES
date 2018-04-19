---
title: Modelos de arquitectura para SharePoint, Exchange, Skype Empresarial y Lync
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/11/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Architecture
ms.assetid: 5b49fa68-f8f2-4705-af96-5f5475e8539a
description: 'Resumen: Obtener los pósteres de TI que describen los modelos arquitectónicos, implementación y opciones de plataforma para SharePoint, Exchange, Skype para empresas y Lync.'
ms.openlocfilehash: ac3ba3f8a0786ec28c9aa6099f288811802bd92d
ms.sourcegitcommit: 62c0630cc0d2611710e73e0592bddfe093e00783
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="architectural-models-for-sharepoint-exchange-skype-for-business-and-lync"></a>Modelos de arquitectura para SharePoint, Exchange, Skype Empresarial y Lync

 **Resumen:** Obtener los pósteres de TI que describen los modelos arquitectónicos, implementación y opciones de plataforma para SharePoint, Exchange, Skype para empresas y Lync.
  
En estos pósteres de TI, se describen los modelos de arquitectura y las opciones de implementación de SharePoint, Exchange, Skype Empresarial y Lync y se proporciona información de diseño para implementar SharePoint en Microsoft Azure.
  
Con Office 365, puede proporcionar los servicios de colaboración y comunicación que los usuarios están familiarizados con como un servicio basado en cloud. Con unas pocas excepciones, la experiencia del usuario sigue siendo el mismo si está manteniendo una implementación local o mediante Office 365. Esta experiencia de usuario unificada que simplifica menor decidir dónde colocar cada carga de trabajo y plantea preguntas como:
  
- ¿Cómo se determina qué opción de plataforma elegir para las cargas de trabajo individuales?
    
- ¿Tiene sentido conservar los servicios locales?
    
- ¿Qué es un escenario donde resulta adecuada una implementación híbrida?
    
- ¿Cómo encaja Microsoft Azure en la imagen?
    
- ¿Cuáles son las configuraciones admitidas para las cargas de trabajo de Office Server en Azure?
    
> [!TIP]
> La mayoría de los pósteres de esta página están disponibles en varios idiomas, incluidos chino, inglés, francés, alemán, italiano, japonés, coreano, portugués, ruso y español. Para descargar un póster en uno de estos idiomas, haga clic en el vínculo **Más idiomas** del póster en cuestión.
  
Queremos conocer su opinión. Envíenos un correo electrónico a [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com). 
  
Esta página vincula a los pósteres siguientes:
  
- **Pósteres de modelos de arquitectura** Puede utilizar estos recursos para determinar la configuración de SharePoint 2016 y Skype para negocios 2015 y plataforma ideal.
    
  - [Modelos arquitectónicos de 2016 de Microsoft SharePoint](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2016_ArchModel)
    
  - [Vista previa de Multi-Geo para OneDrive en Office 365](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#MultiGeoO365ODB)
    
  - [Bases de datos de SharePoint Server de 2016](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2016_Databases)
    
  - [Microsoft Skype para modelos arquitectónicos de negocios 2015](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SfB2015_ArchModel)
    
- **Carteles de opciones de plataforma** Puede utilizar estos recursos para determinar la plataforma ideal y configuración para Lync 2013, 2013 de Exchange y SharePoint 2013.
    
  - [Opciones de plataforma SharePoint 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2013_Options)
    
  - [Opciones de plataformas de intercambio de 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Exch2013_options)
    
  - [Opciones de plataformas de 2013 de Lync](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Lync2013_Options)
    
- **SharePoint Server 2013 en carteles de soluciones de Azure** Puede utilizar estos pósteres de TI para determinar el diseño y la configuración de las cargas de trabajo de SharePoint Server 2013 en servicios de infraestructura de Azure.
    
  - [Sitios de Internet de Microsoft Azure mediante SharePoint Server 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Azure_sharepoint2013)
    
  - [Ejemplo de diseño: sitios de Internet de Microsoft Azure para SharePoint 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#DesignSampleInternetSites)
    
  - [Recuperación ante desastres de SharePoint para Microsoft Azure](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#sharepoint_recovery_Azure)
    
## <a name="architectural-models-posters"></a>Pósteres de modelos de arquitectura

En estos nuevos pósteres de TI de SharePoint 2016 y Skype Empresarial 2015, se proporciona una forma de comparar los distintos métodos de implementación en un formato fácil de imprimir. En cada póster, se proporciona una lista de todas las configuraciones u opciones de plataforma disponibles y le ofrece la siguiente información para cada opción:
  
- **Información general** Un breve resumen de la plataforma, incluyendo un diagrama conceptual.
    
- **Mejor para** Escenarios comunes que son ideales para una plataforma concreta.
    
- **Requisitos de licencia** Las licencias que necesita para la implementación.
    
- **Tareas de arquitectura** Las decisiones que debe tomar un arquitecto.
    
- **Tareas de IT Pro o responsabilidades** Las responsabilidades diarias que su personal de TI tiene que planear.
    
### <a name="microsoft-sharepoint-2016-architectural-models"></a>Modelos de arquitectura de Microsoft SharePoint 2016
<a name="SP2016_ArchModel"> </a>

|**Elemento**|**Descripción**|
|:-----|:-----|
|[![Vista en miniatura para el póster de modelos de arquitectura de SharePoint 2016](images/7d3e590c-1f3b-42cf-920d-9edac8fa3e04.png)          ](https://www.microsoft.com/download/details.aspx?id=52650) <br/> ![Archivo PDF](images/ITPro_Other_PDFicon.png)[PDF](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.pdf)  \| ![Archivo de Visio](images/ITPro_Other_VisioIcon.jpg)[Visio](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.vsdx)  \| ![Vea una página con versiones en otros idiomas](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[Más idiomas](https://www.microsoft.com/download/details.aspx?id=52650) <br/> | En este póster de TI, se describen las configuraciones locales de SharePoint Online, Microsoft Azure y SharePoint que los responsables de la toma de decisiones empresariales y los arquitectos de soluciones necesitan conocer. <br/><br/> - **SharePoint Online (SaaS)** - SharePoint consumir a través de un Software como un modelo de suscripción de servicio (SaaS). <br/> - **Híbrido de SharePoint** - mover los sitios de SharePoint y aplicaciones a la nube a su propio ritmo. <br/> - **SharePoint en Azure (IaaS)** : ampliar el entorno local en Microsoft Azure y distribuir servidores de 2016 de SharePoint no existe. (Se recomienda para entornos de alta disponibilidad y recuperación ante desastres y prueba/desarrollo).<br/> - **SharePoint local** - planificar, implementar, mantener y personalizar el entorno de SharePoint en un centro de datos que se conservan. <br/> |
   
### <a name="multi-geo-preview-for-onedrive-in-office-365"></a>Vista previa de Multi-Geo para OneDrive en Office 365
<a name="MultiGeoO365ODB"> </a>

|**Elemento**|**Descripción**|
|:-----|:-----|
|[![OneDrive Multi-Geo en modelo de Office 365](images/c6c1b7cd-7833-46fb-9eec-c12150c260d9.png)          ](http://download.microsoft.com/download/0/5/9/0594634F-7893-4201-938A-C2FF2F21B655/Multi-Geo-ODB.pdf) <br/> ![Archivo PDF](images/ITPro_Other_PDFicon.png)[PDF](http://download.microsoft.com/download/0/5/9/0594634F-7893-4201-938A-C2FF2F21B655/Multi-Geo-ODB.pdf)  \| ![Archivo de Visio](images/ITPro_Other_VisioIcon.jpg)[Visio](http://download.microsoft.com/download/0/5/9/0594634F-7893-4201-938A-C2FF2F21B655/Multi-Geo-ODB.vsdx) <br/> | Este póster es un resumen de una página de OneDrive Multi-Geo en Office 365, que se encuentra actualmente en la vista previa. Este modelo incluye:<br/><br/> -Beneficios <br/> -Pasos para la implementación <br/> -Un ejemplo de configuración <br/><br/>  Para obtener más información acerca de la vista previa de Multi-Geo para OneDrive en Office 365, haga clic en [aquí](https://aka.ms/onedrivemultigeo).  <br/> |
   
### <a name="sharepoint-server-2016-databases"></a>Bases de datos de SharePoint Server 2016
<a name="SP2016_Databases"> </a>

|**Elemento**|**Descripción**|
|:-----|:-----|
|[![Vista en miniatura para el póster de bases de datos de SharePoint Server de 2016](images/c53e9de7-3bf8-446d-8766-e6700c8dd8e1.png)          ](https://www.microsoft.com/download/details.aspx?id=55041) <br/> ![Archivo PDF](images/ITPro_Other_PDFicon.png)[PDF](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.pdf)  \| ![Archivo de Visio](images/ITPro_Other_VisioIcon.jpg)[Visio](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.vsdx)  \| ![Vea una página con versiones en otros idiomas](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[Más idiomas](https://www.microsoft.com/download/details.aspx?id=55041) <br/> | Este póster de TI es una guía de referencia rápida para bases de datos de SharePoint Server 2016. Cada base de datos tiene los detalles siguientes:<br/><br/> -Tamaño <br/> -Guía de escalamiento <br/> : Patrones de I/O <br/> -Requisitos <br/><br/>  La primera página contiene las bases de datos del sistema de SharePoint y las aplicaciones de servicio que tienen varias bases de datos. La segunda página muestra todas las aplicaciones de servicio que tienen bases de datos.<br/><br/>  Para obtener más información acerca de las bases de datos de SharePoint Server 2016, vea [tipos de base de datos y descripciones en SharePoint Server 2016](https://technet.microsoft.com/en-us/library/cc678868%28v=office.16%29.aspx) <br/> |
   
### <a name="microsoft-skype-for-business-2015-architectural-models"></a>Modelos de arquitectura de Microsoft Skype Empresarial 2015
<a name="SfB2015_ArchModel"> </a>

|**Elemento**|**Descripción**|
|:-----|:-----|
|[![Vista en miniatura para el Skype para póster de modelos arquitectónicos de negocio](images/132288c0-6ae4-4394-88ab-b57dae367714.png)          ](https://www.microsoft.com/download/details.aspx?id=55022) <br/> ![Archivo PDF](images/ITPro_Other_PDFicon.png)[PDF](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.pdf)  \| ![Archivo de Visio](images/ITPro_Other_VisioIcon.jpg)[Visio](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.vsd)  \| ![Vea una página con versiones en otros idiomas](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[Más idiomas](https://www.microsoft.com/download/details.aspx?id=55022) <br/> |Este póster describe el Skype para los negocios en línea, locales, híbrido, nube PBX y la integración con Exchange y SharePoint configuraciones que los empresarios y arquitectos de soluciones necesitan conocer. <br/><br/> Está destinado a la audiencia de profesionales de TI a incrementar la sensibilización de los diferentes modelos de arquitectura fundamentales a través del cual pueden consumirse Skype para los negocios en línea y Skype para empresas en instalaciones. <br/><br/>Comience con cualquier configuración que mejor se adapte a las necesidades de su organización y los planes futuros. Considere y utilice otros según sea necesario. Por ejemplo, que desea tener en cuenta la integración con Exchange y SharePoint o una solución que aprovecha las ventajas de la oferta de PBX de nube de Microsoft.  <br/> |
   
## <a name="platform-options-posters"></a>Pósteres de opciones de plataforma

En estos pósteres de TI de SharePoint 2013, Exchange 2013 y Lync 2013, se proporciona una forma de comparar los distintos métodos de implementación en un solo vistazo en un formato de póster grande. En cada póster, se proporciona una lista de todas las configuraciones u opciones de plataforma disponibles y le ofrece la siguiente información para cada opción:
  
- **Información general** Un breve resumen de la plataforma, incluyendo un diagrama conceptual.
    
- **Mejor para** Escenarios comunes que son ideales para una plataforma concreta.
    
- **Requisitos de licencia** Las licencias que necesita para la implementación.
    
- **Tareas de arquitectura** Las decisiones que debe tomar un arquitecto.
    
- **Tareas de IT Pro o responsabilidades** Las responsabilidades diarias que su personal de TI tiene que planear.
    
## <a name="sharepoint-2013-platform-options"></a>Opciones de plataforma para SharePoint 2013
<a name="SP2013_Options"> </a>

****

|**Elemento**|**Descripción**|
|:-----|:-----|
|[![Imagen en miniatura de opciones de plataformas SharePoint 2013](images/SP_PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=40332) <br/> ![Archivo PDF](images/ITPro_Other_PDFicon.png)[PDF](http://go.microsoft.com/fwlink/p/?LinkId=324594)  \| ![Archivo de Visio](images/ITPro_Other_VisioIcon.jpg)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=324593)  \| ![Vea una página con versiones en otros idiomas](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[Más idiomas](https://www.microsoft.com/download/details.aspx?id=40332) <br/> |Para tomar decisiones empresariales (BDMs) y arquitectos, este modelo muestra las opciones de plataforma para 2013 de SharePoint, SharePoint en Office 365, híbrido local con implementaciones sólo local, Azure y Office 365. Incluye una visión general de cada arquitectura, recomendaciones, requisitos de licencia y listas de tareas de IT Pro para cada plataforma y arquitecto. Se resaltan varias soluciones de SharePoint en Azure.<br/><br/>Para una versión de texto accesible de este póster, consulte el [diagrama accesible - opciones de plataformas de Microsoft SharePoint de 2013](accessible-diagrammicrosoft-sharepoint-2013-platform-options.md).  <br/> |
   
## <a name="exchange-2013-platform-options"></a>Opciones de plataforma para Exchange 2013
<a name="Exch2013_options"> </a>

****

|**Elemento**|**Descripción**|
|:-----|:-----|
|[![Imagen en miniatura de las opciones de plataforma de Exchange](images/ITPro_Other_Exchange2013PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=42676) <br/> ![Archivo PDF](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkID=398740)  \| ![Archivo de Visio](images/ITPro_Other_VisioIcon.jpg)[Visio](https://go.microsoft.com/fwlink/p/?LinkID=398742)  \| ![Vea una página con versiones en otros idiomas](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[Más idiomas](https://www.microsoft.com/download/details.aspx?id=42676) <br/> |Para los arquitectos y los BDMs, este modelo describe las opciones de plataforma disponible para Exchange de 2013. Los clientes pueden elegir entre Exchange Online con Office 365, híbrido de Exchange, Exchange Server local y Exchange alojado. El póster incluye detalles acerca de cada opción de arquitectura, incluyendo los escenarios más adecuados para cada uno, los requisitos de licencia y responsabilidades IT Pro.<br/><br/>Para una versión de texto accesible de este póster, consulte el [diagrama accesible - opciones de plataformas de Microsoft Exchange de 2013](accessible-diagrammicrosoft-exchange-2013-platform-options.md).  <br/> |
   
## <a name="lync-2013-platform-options"></a>Opciones de plataforma para Lync 2013
<a name="Lync2013_Options"> </a>

****

|**Elemento**|**Descripción**|
|:-----|:-----|
|[![Imagen en miniatura de opciones de plataformas de Lync](images/Lync_PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41677) <br/> ![Archivo PDF](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkID=391837)  \| ![Archivo de Visio](images/ITPro_Other_VisioIcon.jpg)[Visio](https://go.microsoft.com/fwlink/p/?LinkID=391839)  \| ![Vea una página con versiones en otros idiomas](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[Más idiomas](https://www.microsoft.com/download/details.aspx?id=41677) <br/> |Para los arquitectos y los responsables de la toma de decisiones, en este modelo, se describen las opciones de plataforma que hay disponibles para Lync 2013. Los clientes pueden elegir entre Lync Online con Office 365, Lync híbrido, Lync Server local y Lync hospedado. El póster de TI incluye información detallada para cada opción de arquitectura, incluidos los escenarios más adecuados para cada una de ellas, los requisitos de licencia y las responsabilidades de los profesionales de TI.  <br/> |
   
## <a name="sharepoint-in-azure-solutions-posters"></a>Pósteres de soluciones de SharePoint en Azure
<a name="Lync2013_Options"> </a>

Estos pósteres de TI mostrar soluciones basadas en Azure mediante SharePoint Server 2013 en un formato de cartel grande.
  
### <a name="internet-sites-in-microsoft-azure-using-sharepoint-server-2013"></a>Sitios de Internet en Microsoft Azure con SharePoint Server 2013
<a name="Azure_sharepoint2013"> </a>

****

|**Elemento**|**Descripción**|
|:-----|:-----|
|[![Imagen de sitios de Internet en Azure usando SharePoint](images/MS_AZ_SPInternetSites.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41992) <br/> ![Archivo PDF](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)  \| ![Archivo de Visio](images/ITPro_Other_VisioIcon.jpg)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)  \| ![Vea una página con versiones en otros idiomas](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[Más idiomas](https://www.microsoft.com/download/details.aspx?id=41992) <br/> |Este póster describe las actividades clave en el diseño y recomienda alternativas de arquitectura para sitios de Internet en Azure. Para una versión de texto accesible de este póster, consulte el [diagrama accesible - sitios de Internet de Microsoft Azure para 2013 de SharePoint](accessible-diagraminternet-sites-in-microsoft-azure-for-sharepoint-2013.md).<br/><br/> Para obtener más información, vea los siguientes artículos:  <br/><br/> - [Sitios de Internet de Microsoft Azure mediante SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md) <br/> - [Arquitecturas de Microsoft Azure para SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) <br/> |
   
### <a name="design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a>Ejemplo de diseño: Sitios de Internet en Microsoft Azure para SharePoint 2013
<a name="DesignSampleInternetSites"> </a>

****

|**Elemento**|**Descripción**|
|:-----|:-----|
|[![Imagen del ejemplo de diseño: sitios de Internet en Azure para SharePoint Server 2013](images/MS_AZ_InternetSitesDesignSample.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41991) <br/> ![Archivo PDF](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| ![Archivo de Visio](images/ITPro_Other_VisioIcon.jpg)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)  \| ![Vea una página con versiones en otros idiomas](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[Más idiomas](https://www.microsoft.com/download/details.aspx?id=41991) <br/> |Para utilizar este ejemplo de diseño como punto de partida para su propio sitio de arquitectura orientada a Internet en Azure mediante SharePoint Server 2013. Para una versión de texto accesible de este póster, consulte [accesible diagrama - ejemplo de diseño: sitios de Internet de Microsoft Azure para SharePoint 2013](accessible-diagramdesign-sample-internet-sites-in-microsoft-azure-for-sharepoint.md).<br/><br/> Para obtener más información, vea los siguientes artículos:  <br/><br/> - [Sitios de Internet de Microsoft Azure mediante SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md) <br/> - [Arquitecturas de Microsoft Azure para SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) <br/> |
   
### <a name="sharepoint-disaster-recovery-to-microsoft-azure"></a>Recuperación ante desastres de SharePoint en Microsoft Azure
<a name="sharepoint_recovery_Azure"> </a>

****

|**Elemento**|**Descripción**|
|:-----|:-----|
|[![Proceso de recuperación ante desastres de SharePoint en Azure](images/SP_DR_Azure.png)          ](https://www.microsoft.com/download/details.aspx?id=41993) <br/> ![Archivo PDF](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555)  \| ![Archivo de Visio](images/ITPro_Other_VisioIcon.jpg)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392554)  \| ![Vea una página con versiones en otros idiomas](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[Más idiomas](https://www.microsoft.com/download/details.aspx?id=41993) <br/> |Este póster de TI ilustra los principios de la arquitectura de un entorno de recuperación ante desastres en Azure. Para una versión de texto accesible de este póster, consulte el [diagrama accesible - recuperación ante desastres de SharePoint para Microsoft Azure](accessible-diagramsharepoint-disaster-recovery-to-microsoft-azure.md).<br/><br/> Para obtener más información, vea los siguientes artículos:  <br/><br/> - [Recuperación de desastres de 2013 de SharePoint Server en Microsoft Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md) <br/> - [Arquitecturas de Microsoft Azure para SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) <br/> |
   
## <a name="see-also"></a>Concepts

<a name="Lync2013_Options"> </a>

[Adopción de la nube y soluciones híbridas](cloud-adoption-and-hybrid-solutions.md)
  
[Recursos de arquitectura de TI de la nube de Microsoft](microsoft-cloud-it-architecture-resources.md)
  
[Guías de entorno de pruebas de adopción de la nube (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[Soluciones híbridas](hybrid-solutions.md)




