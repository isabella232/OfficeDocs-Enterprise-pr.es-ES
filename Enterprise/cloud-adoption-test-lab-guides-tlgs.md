---
title: Guías del laboratorio de pruebas de adopción de la nube (TLG)
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: 'Resumen: Con estas Guías del laboratorio de pruebas (TLG) para la adopción de la nube, podrá configurar entornos de demostración o de desarrollo y pruebas para los productos Office 365, Enterprise Mobility + Security (EMS), Dynamics 365 y Office Server.'
ms.openlocfilehash: 1ca74f7fdb83cf730c4f6d003c9f9e325299f33d
ms.sourcegitcommit: 8fcf6fd9f0c45a5445654ef811410fca3f4f5512
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2018
ms.locfileid: "19193680"
---
# <a name="cloud-adoption-test-lab-guides-tlgs"></a>Guías del laboratorio de pruebas de adopción de la nube (TLG)

 **Resumen:** Con estas Guías del laboratorio de pruebas (TLG) para la adopción de la nube, podrá configurar entornos de demostración o de desarrollo y pruebas para los productos Office 365, Enterprise Mobility + Security (EMS), Dynamics 365 y Office Server.
  
Las guías del laboratorio de pruebas le permiten conocer los productos Microsoft de manera rápida. Son ideales para las situaciones en las que necesita evaluar una tecnología o configuración antes de decidir si es adecuada o antes de implementarla en los equipos de los usuarios. Esta experiencia práctica de "yo la compilo y me funciona" le permitirá entender los requisitos de implementación de un nuevo producto o solución, de modo que pueda planear mejor el hospedaje en la producción.
  
Las guías del laboratorio de pruebas también crean entornos representativos para desarrollo y pruebas de aplicaciones, también conocidos como entornos de desarrollo y pruebas.
  
![Guías de laboratorio de prueba en Microsoft Cloud](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
Vea estos recursos adicionales antes de lanzarse:
  
- Vea la sesión [Conozca la Microsoft Cloud con las Guías del laboratorio de pruebas de adopción de la nube](https://mva.microsoft.com/en-US/training-courses/experience-the-microsoft-cloud-with-cloud-adoption-test-lab-guides-17960?l=LXNRdhSLE_1000115881 ) de la Academia Virtual de Microsoft (solo 22 minutos).
    
- Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual de todos los artículos en la pila de la Guía del entorno de pruebas de One Microsoft Cloud.
    
## <a name="office-365-devtest-environment"></a>Entorno de desarrollo y pruebas de Office 365

Use estos artículos para crear su entorno de desarrollo y pruebas de Office 365:
  
- [Entorno de desarrollo y pruebas de la configuración básica](base-configuration-dev-test-environment.md)
    
    Cree una intranet simplificada que se ejecute en los servicios de infraestructura de Azure. Este paso es opcional si quiere crear una configuración de empresa simulada.
    
- [Entorno de desarrollo y pruebas de Office 365](office-365-dev-test-environment.md)
    
    Cree una suscripción de prueba de Office 365 Enterprise E5, que puede realizar desde su equipo o desde una intranet simplificada que se ejecute en los servicios de infraestructura de Azure.
    
- [Sincronización de directorios (DirSync) para el entorno de desarrollo y pruebas de Office 365](dirsync-for-your-office-365-dev-test-environment.md)
    
    Instale y configure Azure AD Connect para la sincronización de directorios con sincronización de contraseñas. Este paso es opcional si quiere crear una configuración de empresa simulada.
    
Para el entorno de desarrollo y pruebas de Office 365, use estos artículos para probar las características empresariales de Office 365:
  
- [Autenticación multifactor para el entorno de desarrollo y pruebas de Office 365](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
    Configure y pruebe autenticación secundaria con un mensaje de texto enviado a su smartphone para una cuenta en su suscripción de Office 365.
    
- [Identidad federada para el entorno de desarrollo y pruebas de Office 365](federated-identity-for-your-office-365-dev-test-environment.md)
    
    Configure y demuestre autenticación federada con las cuentas de un dominio Active Directory de Windows Server.
    
- [Seguridad de Could App para su entorno de desarrollo y pruebas de Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
    Configure y pruebe la Seguridad de Cloud App de Office 365, que le permite crear directivas que supervisan e informan de actividades sospechosas en su suscripción de Office 365.
    
- [Protección contra amenazas avanzada en el entorno de desarrollo y pruebas de Office 365](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
    Configure y pruebe la Protección contra amenazas avanzada, que es una característica de Exchange Online Protection (EOP), que le ayuda a evitar el malware en el correo electrónico.
    
- [Exhibición avanzada de documentos electrónicos para el entorno de desarrollo y pruebas de Office 365](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
    Agregue datos de ejemplo y pruebe eDiscovery avanzado, que permite buscar y analizar rápidamente los datos que se almacenan en Office 365, como el correo electrónico y los documentos.
    
- [Protección de archivos confidenciales en el entorno de desarrollo y pruebas de Office 365](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
    Pruebe el uso de Office 365 Information Rights Management para proteger los datos en documentos confidenciales, incluso cuando se han publicado accidentalmente en las carpetas de documentos incorrectas.
    
- [Etiquetado y clasificación de datos en el entorno de desarrollo y pruebas de Office 365](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
    Muestre cómo el cliente de Azure Information Protection (AIP) puede usarse para clasificar documentos con varios niveles de seguridad.
    
- [Sitio de grupo de SharePoint Online aislado en su entorno para desarrollo y pruebas](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
    Mostrar cómo crear un sitio de grupo de SharePoint Online aislado del resto de la organización para los recursos privados o muy confidenciales.
    
## <a name="the-microsoft-365-enterprise-devtest-environment"></a>Entorno de desarrollo y pruebas de Microsoft 365 Enterprise

Cree un entorno de desarrollo y pruebas para los escenarios de [Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365-enterprise/) con estos artículos:
  
- [Entorno de pruebas y desarrollo de Microsoft 365 Enterprise](the-microsoft-365-enterprise-dev-test-environment.md)
    
    Crear el entorno inicial que incluye Office 365 E5, EMS E5 y un Windows 10 Enterprise de ordenador.
    
- [Directivas MAM para sus entornos de desarrollo y prueba de Microsoft 365](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
    
    Cree grupos de usuarios y directivas de administración de aplicaciones móviles (MAM) para dispositivos iOS y Android.
    
- [Inscriba sus dispositvos iOS y Android en su entorno de desarrollo y prueba de Microsoft Enterprise 365](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
    
    Inscriba dispositivos Android o iOS y adminístrelos de forma remota.
    
## <a name="office-365-and-dynamics-365-devtest-environment"></a>Entorno de desarrollo y pruebas de Office 365 y Dynamics 365

Agregue una suscripción de prueba a Dynamics 365 y pruebe las características y los escenarios integrados de Office 365 y Dynamics 365 con estos artículos:
  
- [Entorno de desarrollo y pruebas de Office 365 y Dynamics 365](office-365-and-dynamics-365-dev-test-environment.md)
    
    Agregue una suscripción de prueba a Dynamics 365, así como licencias y permisos de Dynamics 365 a sus cuentas de usuario.
    
- [Integración de Exchange Online para su entorno de desarrollo y pruebas y de Office 365 y 365 de Dynamics](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md)
    
    Configure y muestre cómo Office 365 y Dynamics 365 colaboran en los buzones de Exchange Online.
    
## <a name="the-one-microsoft-cloud-devtest-environment"></a>El entorno de desarrollo y pruebas de One Microsoft Cloud

Crear un entorno de desarrollo y prueba que incluya todas las ofertas de la nube Microsoft: Office 365, Azure, EMS y Dynamics 365. Vea [el entorno de desarrollo y prueba de One Microsoft Cloud](the-one-microsoft-cloud-dev-test-environment.md) para las instrucciones paso a paso.
  
## <a name="simulated-cross-premises-devtest-environments"></a>Entornos de pruebas y desarrollo simulado de varias ubicaciones

Puede crear un entorno de pruebas y desarrollo simulado de varias ubicaciones que incluya una red virtual Azure y una red local simulada con estos artículos:
  
- [Red virtual entre locales simulada en Azure](simulated-cross-premises-virtual-network-in-azure.md)
    
    Cree una intranet simulada conectada a una red virtual de Azure en una configuración de la nube híbrida.
    
- [Intranet SharePoint Server 2016 en entorno de prueba y desarrollo de Azure](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx)
    
    Cree una granja de un solo servidor de SharePoint Server 2016 en la red virtual de Azure y pruebe la conectividad y administración desde la red local.
    
## <a name="additional-cloud-based-devtest-environments"></a>Entornos adicionales de desarrollo y pruebas basados en la nube

Estos son entornos adicionales de desarrollo y pruebas basados en la nube que puede crear en los servicios de infraestructura de Azure:
  
- [Entorno de desarrollo y pruebas de SharePoint Server 2016 en Azure](https://technet.microsoft.com/library/mt723354.aspx)
    
    Cree una granja de un solo servidor de SharePoint Server 2016 en los servicios de infraestructura de Azure.
    
- [Entorno de desarrollo y pruebas de Exchange 2016 en Azure](https://technet.microsoft.com/library/mt733070%28v=exchg.160%29.aspx)
    
    Cree un único servidor de Exchange 2016 en los servicios de infraestructura de Azure.
    
- [Entorno de desarrollo y pruebas de SharePoint Server 2013 en Azure](http://technet.microsoft.com/library/165de4d5-8fe6-4fbb-a15b-39a8b0a0eb23.aspx)
    
    Cree granjas de servidores básicas y de alta disponibilidad de SharePoint Server 2013 en los servicios de infraestructura de Azure.
    
**Participar en el debate**

|**Póngase en contacto con nosotros**|**Descripción**|
|:-----|:-----|
|**¿Qué soluciones necesita?** <br/> |Estamos creando contenido para soluciones que abarcan varios productos y servicios de Microsoft. Díganos qué piensa sobre nuestras soluciones entre servidores o solicite soluciones específicas por correo electrónico a [MODAcontent@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).<br/> |
|**Participe en la discusión sobre soluciones** <br/> |Si es un apasionado de las soluciones basadas en la nube, puede unirse a Cloud Adoption Advisory Board (CAAB) para conectarse a una interesante comunidad de mayor tamaño formada por desarrolladores de contenido de Microsoft, profesionales del sector y clientes de todo el mundo. Para unirse, agregue a su usuario como miembro del [espacio CAAB (Cloud Adoption Advisory Board)](https://aka.ms/caab) de Microsoft Tech Community y envíenos un correo electrónico a [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Cualquiera puede leer contenido relacionado con la comunidad en el [blog de CAAB](https://blogs.technet.com/b/solutions_advisory_board/). Pero los miembros de CAAB reciben invitaciones a seminarios web privados donde se describen nuevos recursos y soluciones de adopción de la nube.  <br/> |
|**Obtenga los archivos de arte que ve aquí** <br/> |Si quiere recibir una copia editable de las ilustraciones que se muestran en este artículo, estaremos encantados de enviárselas. Envíe su solicitud por correo electrónico, incluida la dirección URL y el título de la ilustración, a [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).  <br/> |
   
## <a name="see-also"></a>Consulte también

<a name="ADD_TLGs"> </a>

[Adopción de la nube y soluciones híbridas](cloud-adoption-and-hybrid-solutions.md)
  
[Recursos de arquitectura de TI de la nube de Microsoft](microsoft-cloud-it-architecture-resources.md)
  
[Modelos de arquitectura para SharePoint, Exchange, Skype Empresarial y Lync](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[Soluciones híbridas](hybrid-solutions.md)


