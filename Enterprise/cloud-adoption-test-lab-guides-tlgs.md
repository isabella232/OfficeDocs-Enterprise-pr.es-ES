---
title: "Guías del laboratorio de pruebas de adopción de la nube (TLG)"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Strat_O365_Enterprise
- Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: "Resumen: Utilice estas guías de laboratorio de prueba (TLGs) de adopción de nube para configurar demostración, prueba de concepto o entornos de prueba/desarrollo para Office 365, movilidad en la empresa + seguridad (EMS), Dynamics 365 y productos de servidor de Office."
ms.openlocfilehash: 3172b6033fbb7dd79b8eb786d92a4f58886a8fd5
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="cloud-adoption-test-lab-guides-tlgs"></a>Guías del laboratorio de pruebas de adopción de la nube (TLG)

 **Resumen:** Utilice estas guías de laboratorio de prueba (TLGs) de adopción de nube para configurar demostración, prueba de concepto o entornos de prueba/desarrollo para Office 365, movilidad en la empresa + seguridad (EMS), Dynamics 365 y productos de servidor de Office.
  
TLGs ayudará a conocer rápidamente los productos de Microsoft. Son muy importantes para situaciones donde es necesario evaluar una configuración o tecnología antes de decidir si es adecuado para usted o antes de distribuirlo por los usuarios. La experiencia práctica "compilarlo a mí y funciona" le ayuda a comprender los requisitos de implementación de un nuevo producto o una solución para que pueda prever mejor para alojarlo en producción.
  
Las guías del laboratorio de pruebas también crean entornos representativos para desarrollo y pruebas de aplicaciones, también conocidos como entornos de desarrollo y pruebas.
  
![Guías de laboratorio de prueba en Microsoft Cloud](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
Antes de adentrarnos, consulte estos recursos adicionales:
  
- Ver la sesión de [experiencia con las guías de laboratorio de prueba de adopción de nube en la nube de Microsoft](https://mva.microsoft.com/en-US/training-courses/experience-the-microsoft-cloud-with-cloud-adoption-test-lab-guides-17960?l=LXNRdhSLE_1000115881 ) Microsoft Virtual Academy (sólo 22 minutos).
    
- Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual para todos los artículos de la pila de una guía de laboratorio de prueba de nube de Microsoft.
    
## <a name="office-365-devtest-environment"></a>Entorno de desarrollo y pruebas de Office 365
<a name="O365"> </a>

Use estos artículos para crear su entorno de desarrollo y pruebas de Office 365:
  
- [Entorno de desarrollo y pruebas de la configuración básica](base-configuration-dev-test-environment.md)
    
    Cree una intranet simplificada que se ejecute en los servicios de infraestructura de Azure. Este paso es opcional si quiere crear una configuración de empresa simulada.
    
- [Entorno de desarrollo y pruebas de Office 365](office-365-dev-test-environment.md)
    
    Crear una suscripción de prueba Office 365 Enterprise E5, lo que puede hacer desde el equipo o desde una intranet simplificada que se ejecutan en servicios de infraestructura de Azure.
    
- [Sincronización de directorios (DirSync) para el entorno de desarrollo y pruebas de Office 365](dirsync-for-your-office-365-dev-test-environment.md)
    
    Instale y configure Azure AD Connect para la sincronización de directorios con sincronización de contraseñas. Este paso es opcional si quiere crear una configuración de empresa simulada.
    
Para el entorno de desarrollo y prueba de Office 365, utilice estos artículos para demostrar las funciones de empresa de Office 365:
  
- [Autenticación con varios factores para el entorno de desarrollo y prueba de Office 365](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
    Configure y pruebe autenticación secundaria con un mensaje de texto enviado a su smartphone para una cuenta en su suscripción de Office 365.
    
- [Identidad federada para el entorno de desarrollo y pruebas de Office 365](federated-identity-for-your-office-365-dev-test-environment.md)
    
    Configure y demuestre autenticación federada con las cuentas de un dominio Active Directory de Windows Server.
    
- [Seguridad de la aplicación de nube para su entorno de pruebas y desarrollo de Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
    Configurar y demostrar la seguridad App de Office 365 Cloud, que permite crear directivas que supervisión y le informan de actividades sospechosas en su suscripción de Office 365.
    
- [Una protección avanzada para su entorno de pruebas y desarrollo de Office 365](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
    Configure y pruebe la Protección contra amenazas avanzada, que es una característica de Exchange Online Protection (EOP) que le ayuda a evitar el malware en el correo electrónico.
    
- [EDiscovery avanzada para su entorno de pruebas y desarrollo de Office 365](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
    Agregue datos de ejemplo y pruebe eDiscovery avanzado, que permite buscar y analizar rápidamente los datos que se almacenan en Office 365, como el correo electrónico y los documentos.
    
- [Protección de archivos confidenciales en el entorno de desarrollo y prueba de Office 365](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
    Pruebe el uso de Office 365 Information Rights Management para proteger los datos en documentos confidenciales, incluso cuando se han publicado accidentalmente en las carpetas de documentos incorrectas.
    
- [Clasificación de datos y el etiquetado en el entorno de desarrollo y prueba de Office 365](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
    Demuestre cómo el cliente de protección de información de Azure (AIP) puede utilizarse para clasificar documentos con varios niveles de seguridad.
    
- [Entorno de pruebas y desarrollo de SharePoint Online team sitio aislado](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
    Demuestre cómo crear un sitio de grupo SharePoint Online que está aislado del resto de la organización de recursos altamente confidencial.
    
## <a name="the-microsoft-365-enterprise-devtest-environment"></a>El entorno de pruebas y desarrollo empresarial de Microsoft 365
<a name="O365"> </a>

Crear un entorno de prueba/desarrollo para escenarios de [Empresa de Microsoft 365](https://docs.microsoft.com/microsoft-365-enterprise/) con estos artículos:
  
- [El entorno de pruebas y desarrollo empresarial de Microsoft 365](the-microsoft-365-enterprise-dev-test-environment.md)
    
    Crear el entorno inicial que incluye Office 365 E5, E5 EMS y un equipo que ejecuta Windows 10 Enterprise.
    
- [Directivas MAM para su entorno de pruebas y desarrollo empresarial de Microsoft 365](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
    
    Cree grupos de usuarios y directivas de administración de aplicaciones móviles (MAM) para dispositivos iOS y Android.
    
- [Inscribir a dispositivos iOS y Android en su entorno de pruebas y desarrollo de Microsoft Enterprise 365](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
    
    Inscriba dispositivos Android o iOS y adminístrelos de forma remota.
    
## <a name="office-365-and-dynamics-365-devtest-environment"></a>Entorno de desarrollo y pruebas de Office 365 y Dynamics 365
<a name="O365_D365"> </a>

Agregue una suscripción de prueba a Dynamics 365 y pruebe las características y los escenarios integrados de Office 365 y Dynamics 365 con estos artículos:
  
- [Entorno de desarrollo y pruebas de Office 365 y Dynamics 365](office-365-and-dynamics-365-dev-test-environment.md)
    
    Agregue una suscripción de prueba a Dynamics 365, así como licencias y permisos de Dynamics 365 a sus cuentas de usuario.
    
- [Integración de Exchange Online para Office 365 y Dynamics 365 dev/entorno de prueba](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md)
    
    Configurar y, a continuación, demuestre cómo Office 365 Dynamics 365 funcionan juntos y buzones de Exchange en línea.
    
## <a name="the-one-microsoft-cloud-devtest-environment"></a>El entorno de desarrollo y prueba de una nube de Microsoft
<a name="O365_D365"> </a>

Crear un entorno de pruebas y desarrollo que incluye todas las ofertas de nube de Microsoft: Office 365, Azure, EMS y Dynamics 365. Para ver las instrucciones paso a paso, vea [la nube de Microsoft de un entorno de pruebas y desarrollo](the-one-microsoft-cloud-dev-test-environment.md) .
  
## <a name="simulated-cross-premises-devtest-environments"></a>Entornos de pruebas y desarrollo simulado de varias ubicaciones
<a name="O365_D365"> </a>

Puede crear un entorno de pruebas y desarrollo simulado de varias ubicaciones que incluya una red virtual Azure y una red local simulada con estos artículos:
  
- [Red virtual de local entre simulado en Azure](simulated-cross-premises-virtual-network-in-azure.md)
    
    Cree una intranet simulada conectada a una red virtual de Azure en una configuración de la nube híbrida.
    
- [SharePoint Server 2016 de intranet en el entorno de pruebas y desarrollo de Azure](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx)
    
    Cree una granja de un solo servidor de SharePoint Server 2016 en la red virtual de Azure y pruebe la conectividad y administración desde la red local.
    
## <a name="additional-cloud-based-devtest-environments"></a>Entornos adicionales de desarrollo y pruebas basados en la nube
<a name="ADD_TLGs"> </a>

Estos son entornos adicionales de desarrollo y pruebas basados en la nube que puede crear en los servicios de infraestructura de Azure:
  
- [Entorno de desarrollo y prueba de 2016 de SharePoint Server en Azure](https://technet.microsoft.com/library/mt723354.aspx)
    
    Cree una granja de un solo servidor de SharePoint Server 2016 en los servicios de infraestructura de Azure.
    
- [Entorno de desarrollo y prueba de 2016 de Exchange en Azure](https://technet.microsoft.com/library/mt733070%28v=exchg.160%29.aspx)
    
    Cree un único servidor de Exchange 2016 en los servicios de infraestructura de Azure.
    
- [Entornos de pruebas y desarrollo de SharePoint Server 2013 en Azure](http://technet.microsoft.com/library/165de4d5-8fe6-4fbb-a15b-39a8b0a0eb23.aspx)
    
    Cree granjas de servidores básicas y de alta disponibilidad de SharePoint Server 2013 en los servicios de infraestructura de Azure.
    
**Participar en la discusión**

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


