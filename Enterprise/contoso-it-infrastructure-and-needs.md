---
title: Infraestructura y necesidades de TI de Contoso
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 5d6a58b8-bec3-4629-9737-8733c7b7ec92
description: "Resumen: Comprender la estructura básica de la infraestructura de TI local de Contoso y cómo sus necesidades de negocio pueden cumplirse mediante ofertas de nube de Microsoft."
ms.openlocfilehash: 98ead7ffa3164c3cd57ec50def836b690881ba63
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2017
---
# <a name="contosos-it-infrastructure-and-needs"></a>Infraestructura y necesidades de TI de Contoso

 **Resumen:** Comprender la estructura básica de la infraestructura de TI local de Contoso y cómo sus necesidades de negocio pueden cumplirse mediante ofertas de nube de Microsoft.
  
Contoso está en proceso de transición de una infraestructura de TI centralizada local a una infraestructura de nube inclusiva que incorpora las cargas de trabajo de productividad del personal, las aplicaciones y los escenarios híbridos basados en la nube.
  
## <a name="contosos-existing-it-infrastructure"></a>Infraestructura de TI existente de Contoso

Contoso usa una infraestructura de TI local mayoritariamente centralizada, con centros de datos de aplicaciones en la sede de París.
  
**Figura 1: Infraestructura de TI existente de Contoso**

![Infraestructura de TI existente de Contoso](images/Contoso_Poster/Existing_IT.png)
  
La figura 1 muestra una oficina central con centros de datos de aplicaciones, una red perimetral e Internet.
  
En la red perimetral de Contoso, los distintos conjuntos de servidores proporcionan lo siguiente:
  
- Acceso remoto al proxy web y a la intranet de Contoso para los trabajadores de la sede de París.
    
- Hospedaje del sitio web público de Contoso, desde el cual los clientes pueden solicitar productos, piezas o suministros.
    
- Hospedaje de la extranet de partners de Contoso para la colaboración y comunicación de los partners.
    
## <a name="contosos-business-needs"></a>Necesidades de negocio de Contoso

Estas son las necesidades de negocio de Contoso en orden de prioridad:
  
1. Cumplir los requisitos normativos regionales
    
    Para evitar multas y mantener buenas relaciones con los gobiernos locales, Contoso debe garantizar el cumplimiento de las normas de almacenamiento y cifrado de datos.
    
2. Mejorar la administración de proveedores y partners
    
    La extranet de partners está quedando anticuada y es cara de mantener. Contoso quiere reemplazarla por una solución basada en la nube que use la autenticación federada.
    
3. Mejorar la productividad de los empleados móviles, la administración de dispositivos y el acceso
    
    El personal exclusivamente móvil de Contoso se está expandiendo y se requiere la administración de dispositivos para garantizar la protección de la propiedad intelectual y un acceso más eficiente a los recursos.
    
4. Reducir la infraestructura de acceso remoto
    
    Al mover a la nube recursos a los que los trabajadores remotos tienen acceso con frecuencia, Contoso ahorrará dinero gracias a la reducción de los costos de mantenimiento y soporte técnico de su solución de acceso remoto.
    
5. Reducir verticalmente los centros de datos locales
    
    Los centros de datos de Contoso contienen cientos de servidores, algunos de los cuales ejecutan funciones de archivo o heredadas que desvían la atención del personal de TI del mantenimiento de unas cargas de trabajo de alto valor empresarial.
    
6. Escalar verticalmente los recursos informáticos y de almacenamiento para el procesamiento de fin de trimestre
    
    El procesamiento de la contabilidad financiera de fin de trimestre y la proyección, junto con la administración del inventario, requiere aumentos a corto plazo en servidores y almacenamiento.
    
## <a name="mapping-contosos-business-needs-to-microsofts-cloud-offerings"></a>Asignación de las necesidades de negocio de Contoso a las ofertas de nube de Microsoft

Basándose en un análisis de las ofertas de nube de Microsoft, el departamento de TI de Contoso determinó la asignación siguiente:
  
|**Software como servicio (SaaS)**|**Plataforma como servicio (PaaS de Azure).**|**Infraestructura como servicio (IaaS de Azure).**|
|:-----|:-----|:-----|
|**Office 365:** aplicaciones de productividad personal y de grupo principales en la nube. <br/> Necesidades de negocio: 1 3 5  <br/> |Hospedar sistemas de información y documentos de ventas y soporte técnico mediante aplicaciones basadas en la nube.  <br/> Necesidad de negocio: 3  <br/> |Mover los sistemas de archivo y heredados a servidores basados en la nube.  <br/> Necesidad de negocio: 5  <br/> |
|**Dynamics 365:** Usar la administración basada en la nube de clientes y proveedores. Quitar la extranet de partners en la red perimetral.<br/> Necesidad de negocio: 2  <br/> |Las aplicaciones móviles están basadas en la nube, en lugar de en el centro de datos de París.  <br/> Necesidades de negocio: 3 4  <br/> |Migrar las aplicaciones que se usan poco fuera de los centros de datos locales.  <br/> Necesidad de negocio: 5  <br/> |
|**Intune/EMS:** administrar dispositivos iOS y Android. <br/> Necesidad de negocio: 3  <br/> ||Agregar almacenamiento y servidores temporales para satisfacer las necesidades de procesamiento de fin de trimestre.  <br/> Necesidad de negocio: 6  <br/> |
   
## <a name="see-also"></a>See Also

[Contoso en la nube de Microsoft](contoso-in-the-microsoft-cloud.md)
  
[Recursos de arquitectura de TI de la nube de Microsoft](microsoft-cloud-it-architecture-resources.md)

[Mapa de ruta de Enterprise Cloud de Microsoft: Recursos para los responsables de decisiones de TI](https://sway.com/FJ2xsyWtkJc2taRD)


