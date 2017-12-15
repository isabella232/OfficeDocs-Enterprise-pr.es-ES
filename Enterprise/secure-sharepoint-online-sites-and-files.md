---
title: Proteger los archivos y los sitios de SharePoint Online
ms.author: bcarter
author: bcarter
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: concetpual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
- Ent_Architecture
ms.assetid: 1d51bd87-17bf-457c-b698-61821de3afa0
description: "Resumen: Recomendaciones de configuración para proteger los archivos en SharePoint Online y Office 365."
ms.openlocfilehash: 0657ff5f3b6668d8cd5ae361bd890ef35c23608b
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2017
---
# <a name="secure-sharepoint-online-sites-and-files"></a>Proteger los archivos y los sitios de SharePoint Online

 **Resumen:** Recomendaciones de configuración para proteger los archivos en SharePoint Online y Office 365.
  
En este artículo se ofrece recomendaciones para configurar sitios de equipo de SharePoint Online y protección de archivos que equilibra la seguridad con la facilidad de colaboración. Este artículo define cuatro configuraciones distintas, a partir de un sitio público dentro de su organización con las directivas de uso compartidas más abiertas. Cada configuración adicional representa un paso significativo de protección, pero se reduce la capacidad de acceso y colaborar en los recursos para el conjunto pertinente de los usuarios. Utilice estas recomendaciones como punto de partida y ajustar las configuraciones para satisfacer las necesidades de su organización. 
  
Las configuraciones en este artículo se alinean con las recomendaciones de Microsoft para tres niveles de protección de datos, identidades y dispositivos:
  
- Protección básica
    
- Protección confidencial
    
- Protección altamente confidencial
    
Para obtener más información acerca de estos niveles y capacidades recomendadas para cada nivel, consulte los siguientes recursos. 
  
- [Identidad y protección de dispositivos para Office 365](microsoft-cloud-it-architecture-resources.md#BKMK_O365IDP)
    
- [Soluciones de protección de archivos en Office 365](microsoft-cloud-it-architecture-resources.md#BKMK_O365fileprotect)
    
## <a name="capability-overview"></a>Resumen de la capacidad

Recomendaciones para los sitios de SharePoint Online equipo dibujar en una variedad de capacidades de Office 365. Sitios altamente confidencial, se recomienda la protección de la información de Azure. Esto se incluye en la movilidad en la empresa + seguridad (EMS). 
  
La ilustración siguiente muestra las configuraciones recomendadas para cuatro sitios de equipo de SharePoint Online.
  
![Configuración recomendada para sitios de SharePoint](images/ad0dcd70-f6f5-465c-8d16-1889481ca07a.png)
  
Tal como se muestra:
  
- Protección básica incluye dos opciones para sitios de equipo de SharePoint Online: un sitio público y sitio privado. Sitios públicos pueden ser detectados y acceso a alguien de la organización. Sitios privados sólo pueden ser detectados y tener acceso a los miembros del sitio. Ambas de estas configuraciones de sitio permiten compartir fuera del grupo. 
    
- Protección altamente confidencial y sensible en los sitios son sitios privados con acceso limitado sólo a los miembros de grupos específicos.
    
- Etiquetas de Office 365 proporcionan una manera de clasificar los datos con un nivel de protección necesaria. Cada uno de los sitios de equipo de SharePoint Online se configuran automáticamente archivos de etiqueta en bibliotecas de documentos con una etiqueta predeterminada para el sitio. Correspondientes a las configuraciones de cuatro sitios, las etiquetas en este ejemplo son internos Public, Private, sensible y altamente confidencial. Los usuarios pueden cambiar las etiquetas, pero esta configuración asegura que todos los archivos reciban una etiqueta default.
    
- Las políticas de prevención (DLP) de pérdida de datos se configuran para que las etiquetas altamente confidencial Office 365 y sensibles a advertir o impedir que los usuarios cuando intentan enviar estos tipos de archivos fuera de la organización.
    
- Para los sitios configurados con protección altamente confidencial, protección de la información de Azure cifra y concede permisos para los archivos.
    
## <a name="tenant-wide-settings-for-sharepoint-online-and-onedrive-for-business"></a>Configuración de inquilinos todo para SharePoint Online y OneDrive para el negocio

SharePoint Online y OneDrive para los negocios incluyen la configuración de todo el inquilino que afectan a todos los sitios y los usuarios. Algunas de estas opciones pueden ajustarse en el nivel del sitio para que sea más restrictivo (pero no inferior). Esta sección trata la configuración inquilinos que afectan a la seguridad y la colaboración. 
  
### <a name="sharing"></a>Uso compartido

Para esta solución, se recomienda la siguiente configuración de inquilinos:
  
- Mantenga la predeterminada compartir directiva que permita el uso compartido con todos los tipos de cuenta, incluido el uso compartido de anónimo.
    
- Establecer vínculos anónimos caduque, si lo desea.
    
- Cambiar el tipo de vínculo predeterminado para compartir como interna. Esto ayuda a prevenir la pérdida accidental de datos fuera de la organización.
    
Aunque pueda parecer poco intuitiva para permitir el uso compartido externo, este enfoque proporciona más control sobre comparado con el envío de archivos por correo electrónico el uso compartido de archivos. SharePoint Online y Outlook colaboran para proporcionar colaboración segura de archivos. 
  
- De forma predeterminada, Outlook comparte un vínculo a un archivo en lugar de enviar el archivo por correo electrónico. 
    
- SharePoint Online y OneDrive para el negocio facilitan compartir vínculos a archivos con colaboradores que están tanto dentro como fuera de la organización
    
También tiene los controles y regulan el intercambio externo. Por ejemplo, puede:
  
- Deshabilitar un vínculo de invitado anónimo.
    
- Revocar el acceso de usuario a un sitio.
    
- Vea quién tiene acceso a un sitio específico o un documento.
    
- Establecer vínculos para compartir anónimo a punto de caducar (establecer el arrendatario).
    
- Limitar quién puede compartir fuera de su organización (establecer el arrendatario).
    
### <a name="use-external-sharing-together-with-data-loss-prevention-dlp"></a>Uso externo compartiendo junto con la prevención de pérdidas de datos (DLP)

Si no desea permitir compartir externos, los usuarios con una empresa necesitan encontrará métodos y herramientas alternativas. Microsoft recomienda que combinar compartir externo con las directivas de DLP para proteger los archivos confidenciales y altamente confidenciales.
  
### <a name="device-access-settings"></a>Configuración de acceso de dispositivo

Configuración de acceso de dispositivo para SharePoint Online y OneDrive para el negocio permite determinar si el acceso está limitado a sólo explorador (no se pueden descargar archivos) o si se bloquea el acceso. Estos valores están actualmente en la primera versión y aplican todo el arrendatario. Próximamente es la capacidad de configurar las directivas de acceso de dispositivo en el nivel de sitio. Para esta solución, se recomienda no utilizar configuración de acceso de dispositivo que se aplican a todo el arrendatario.
  
Para utilizar la configuración de acceso de dispositivo mientras se encuentran en la primera versión: [Configurar el estándar o las primeras opciones liberar en Office 365](https://support.office.com/article/Set-up-the-Standard-or-First-Release-options-in-Office-365-3B3ADFA4-1777-4FF0-B606-FB8732101F47).
  
### <a name="onedrive-for-business"></a>OneDrive para la Empresa

Visite estos valores para decidir si desea cambiar la configuración predeterminada para la OneDrive de los sitios comerciales. Actualmente, la configuración de acceso de uso compartido y el dispositivo se duplica desde el centro de administración de SharePoint Online y se aplica a ambos entornos.
  
## <a name="sharepoint-team-site-configuration"></a>Configuración de sitio de SharePoint team

La tabla siguiente resume la configuración para cada uno de los sitios de equipo descritos anteriormente en este artículo. Utilice estas configuraciones como recomendaciones de punto de partida y ajustar los tipos de sitio y configuraciones para satisfacer las necesidades de su organización. No todas las organizaciones deben cada tipo de sitio. Sólo un pequeño número de organizaciones requiere protección altamente confidencial.
  
||||||
|:-----|:-----|:-----|:-----|:-----|
||**Protección básica #1** <br/> |**Protección básica #2** <br/> |**Protección confidencial** <br/> |**Altamente confidencial** <br/> |
|Descripción  <br/> |Abra el descubrimiento y la colaboración dentro de la organización.  <br/> |Sitio privado y grupo con uso compartido permitido fuera del grupo.  <br/> |Sitio aislado, en el que se definen los niveles de acceso por la pertenencia a grupos específicos. Sólo se permite el uso compartido a los miembros del sitio. DLP advierte a los usuarios al intentar enviar archivos fuera de la organización.  <br/> |Sitio aislado + cifrado de archivos y permisos con protección de la información de Azure. DLP impide que los usuarios envíen archivos fuera de la organización.  <br/> |
|Sitio de grupo privado o público  <br/> |Público  <br/> |Privada  <br/> |Privada  <br/> |Privada  <br/> |
|¿Quién tiene acceso?  <br/> |Todos los miembros de la organización, incluidos los usuarios de B2B y los invitados.  <br/> |Miembros del sitio sólo. Otros usuarios pueden solicitar el acceso.  <br/> |Miembros del sitio sólo. Otros usuarios pueden solicitar el acceso.  <br/> |Sólo los miembros. Otros usuarios no pueden solicitar el acceso.  <br/> |
|Controles de nivel de sitio para compartir  <br/> |Compartir permitidos con nadie. La configuración predeterminada.  <br/> |Compartir permitidos con nadie. La configuración predeterminada.  <br/> |Los miembros no pueden compartir el acceso al sitio.  <br/> Que no sean miembros pueden solicitar acceso al sitio, pero estas solicitudes deben solucionarse por un administrador del sitio.  <br/> |Los miembros no pueden compartir el acceso al sitio.  <br/> Que no sean miembros no pueden solicitar acceso al sitio o al contenido.  <br/> |
|Controles de acceso de dispositivo de nivel de sitio  <br/> |No hay controles adicionales.  <br/> |No hay controles adicionales.  <br/> |Controles de nivel de sitio son muy pronto, lo que impide que los usuarios descargar archivos en dispositivos combinados no conformes o no sea de dominio. Esto permite el acceso sólo mediante navegador de todos los demás dispositivos.  <br/> |Controles de nivel de sitio son muy pronto, que bloquea la descarga de archivos a dispositivos combinados no conformes o no sea de dominio.  <br/> |
|Etiquetas de Office 365  <br/> |Público interno  <br/> |Privada  <br/> |Confidencial  <br/> |Altamente confidencial  <br/> |
|Directivas de DLP  <br/> |||Advertir a los usuarios enviar archivos etiquetados como delicada fuera de la organización.  <br/> Para bloquear el intercambio externo de tipos de datos confidenciales, como números de tarjetas de crédito u otros datos personales, puede configurar directivas DLP adicionales para estos tipos de datos (incluidos los tipos de datos personalizados que configura).  <br/> |Impedir que los usuarios envíen archivos etiquetados como altamente confidenciales fuera de la organización. Permitir a los usuarios reemplazar esto proporcionando justificación, incluidos los que están compartiendo el archivo con.  <br/> |
|Azure Information Protection  <br/> ||||Utilice la protección de la información de Azure para cifrar automáticamente y conceder permisos a los archivos. Esta protección se desplaza con los archivos en caso de se produzca la pérdida.  <br/> Office 365 no puede leer los archivos cifrados con protección de la información de Azure. Además, las directivas de DLP sólo pueden trabajar con los metadatos (incluidas etiquetas), pero no el contenido de estos archivos (como números de tarjeta de crédito dentro de los archivos).  <br/> |
   
Para que los pasos para implementar los cuatro tipos diferentes de sitios de SharePoint Online team en esta solución, vea [implementar SharePoint Online sitios para tres niveles de protección](deploy-sharepoint-online-sites-for-three-tiers-of-protection.md). Para que los pasos para crear un entorno de pruebas y desarrollo, consulte [sitios seguro en línea de SharePoint en un entorno de pruebas y desarrollo](secure-sharepoint-online-sites-in-a-dev-test-environment.md). 
  
## <a name="office-365-classification-and-labels"></a>Las etiquetas y la clasificación de office 365

Con las etiquetas de Office 365 se recomienda para entornos con datos confidenciales. Después de configurar y publicar Office 365 etiquetas:
  
- Puede aplicar una etiqueta predeterminada a una biblioteca de documentos en un sitio de grupo SharePoint Online, para que todos los documentos de dicha biblioteca Obtén la etiqueta predeterminada. 
    
- Puede aplicar etiquetas al contenido automáticamente si coincide con las condiciones específicas.
    
- Puede aplicar las directivas de DLP se basan en etiquetas de Office 365.
    
- Personas de la organización pueden aplicar una etiqueta manualmente al contenido en Outlook en el web, Outlook 2010 y posterior, OneDrive para grupos de trabajo, SharePoint Online y Office 365. Los usuarios suelen conocer mejor qué tipo de contenido están trabajando, para que pueda clasificarlos y aplicará la correspondiente directiva de DLP.
    
![Configuración recomendada para sitios de SharePoint](images/7fed0126-ab4a-4480-922c-681970642339.png)
  
Como se muestra, esta solución incluye la creación de las etiquetas siguientes:
  
- Altamente confidencial
    
- Confidencial
    
- Privada
    
- Público interno
    
Estas etiquetas se asignan a los sitios recomendados en las ilustraciones y los gráficos anteriormente en este artículo. Esta solución recomienda la configuración de directivas DLP para ayudar a evitar la pérdida de archivos etiquetados como altamente confidenciales y sensibles.
  
Para que los pasos para configurar las etiquetas de Office 365 y las directivas de DLP en esta solución, vea [proteger SharePoint Online archivos con etiquetas de Office 365 y DLP](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md).
  
## <a name="azure-information-protection"></a>Azure Information Protection

Utilizar protección de la información de Azure para aplicar las etiquetas y las protecciones que siguen los archivos dondequiera que vayan. Para esta solución, se recomienda que utilizar una directiva de protección de la información de Azure con ámbito y una etiqueta dentro de la etiqueta altamente confidencial para cifrar y conceder permisos a los archivos que necesitan ser protegidos con el mayor nivel de seguridad. 
  
Tenga en cuenta que cuando se aplica el cifrado de protección de la información de Azure a archivos almacenados en Office 365, el servicio no puede procesar el contenido de estos archivos. Co-autoría, eDiscovery, búsqueda, Delve y otras características de colaboración no funcionan. Las directivas de DLP sólo pueden trabajar con los metadatos (incluidos los rótulos de Office 365), pero no el contenido de estos archivos (como números de tarjeta de crédito dentro de los archivos).
  
![Azure Information Protection está configurada en Azure y las etiquetas aparecen en la barra de herramientas de cliente](images/1266a7a0-5078-49ab-bbf1-b0cf41451f62.png)
  
Tal como se muestra:
  
- Configurar las directivas de protección de la información de Azure y etiquetas en el portal de Microsoft Azure. Se recomienda configurar una etiqueta dentro de una política de protección de la información de Azure con ámbito.
    
- Protección de la información de Azure etiquetas mostrar encima como una barra de **protección de la información** en las aplicaciones de Office.
    
### <a name="adding-permissions-for-external-users"></a>Agregar permisos para usuarios externos

Hay dos formas de conceder a los usuarios externos el acceso a archivos protegidos con protección de la información de Azure. En ambos casos, los usuarios externos deben tener una cuenta de Azure AD. Si los usuarios externos no son miembros de una organización que utiliza AD Azure, pueden obtener una cuenta de Azure AD como individuo mediante el uso de esta página: [https://aka.ms/aip-signup](https://aka.ms/aip-signup).
  
- Agregar usuarios externos a un grupo de AD de Azure que se utiliza para configurar la protección para una etiqueta
    
     Debe agregar la cuenta como usuario en el directorio B2B. Puede tardar un par de horas para el [almacenamiento en caché de Azure Rights Management de pertenencia de grupo](https://docs.microsoft.com/information-protection/plan-design/prepare#group-membership-caching-by-azure-rights-management). Con este método, los permisos se conceden a todos los archivos protegidos con la etiqueta (incluso archivos protegidos antes de agrega un usuario al grupo AD Azure).
    
- Agregar usuarios externos directamente a la protección de etiqueta
    
     Puede agregar todos los usuarios de una organización (por ejemplo, Fabrikam.com), un grupo de AD Azure (por ejemplo, un grupo de finanzas dentro de una organización) o un usuario individual. Por ejemplo, puede agregar un equipo externo de los reguladores para la protección de una etiqueta. Con este método, los permisos se conceden sólo para archivos protegidos con la etiqueta después de agrega la entidad externa a la protección.
    
### <a name="deploying-and-using-azure-information-protection"></a>Implementar y utilizar la protección de la información de Azure

Para que los pasos para configurar la protección de la información de Azure en esta solución, vea [proteger SharePoint Online archivos con protección de la información de Azure](protect-sharepoint-online-files-with-azure-information-protection.md).
  
## <a name="see-also"></a>See Also

[Guía de seguridad de Microsoft para campañas políticas, las ONG y otras organizaciones de Agile](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[Soluciones de seguridad](security-solutions.md)
  
[Adopción de la nube y soluciones híbridas](cloud-adoption-and-hybrid-solutions.md)
  
[Sitios de SharePoint Online seguros en un entorno de pruebas y desarrollo](secure-sharepoint-online-sites-in-a-dev-test-environment.md)



