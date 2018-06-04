---
title: Protección de archivos de SharePoint Online con Azure Information Protection
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: 5b9c8e41-25d2-436d-89bb-9aecb9ec2b80
description: 'Resumen: aplique Azure Information Protection para proteger los archivos en un sitio de grupo de SharePoint Online altamente confidencial.'
ms.openlocfilehash: bab799a784cac579c92fb06ea17592d85fd59af2
ms.sourcegitcommit: 29c8571ca4912549bac55ec9d1642d21eba5b0e4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2018
ms.locfileid: "19168504"
---
# <a name="protect-sharepoint-online-files-with-azure-information-protection"></a>Protección de archivos de SharePoint Online con Azure Information Protection

 **Resumen:** aplique Azure Information Protection para proteger los archivos en un sitio de grupo de SharePoint Online altamente confidencial.
  
Siga los pasos que se indican en este artículo para configurar Azure Information Protection para ofrecer cifrado y permisos para archivos en un sitio de grupo de SharePoint Online altamente confidencial. La protección del cifrado y los permisos viaja con los archivos, incluso cuando se descarguen del sitio. Para obtener más información sobre los sitios de grupo de SharePoint Online altamente confidenciales, vea [Proteger archivos y sitios de SharePoint Online](secure-sharepoint-online-sites-and-files.md).
  
> [!NOTE]
> Cuando se aplica el cifrado de Azure Information Protection a los archivos almacenados en Office 365, el servicio no puede procesar el contenido de estos archivos. No funcionan algunas características de colaboración, como la coautoría, eDiscovery, la búsqueda y Delve. Las directivas de prevención de pérdida de datos (DLP) solo pueden trabajar con los metadatos (incluidas las etiquetas de Office 365), pero no con el contenido de estos archivos (por ejemplo, números de tarjeta de crédito incluidos en los archivos). 
  
Primero, siga las instrucciones que se indican en [Activar Azure RMS desde el Centro de administración de Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365) para su suscripción de Office 365.
  
Después, siga estos pasos para configurar Azure Information Protection con una nueva directiva con ámbito y una subetiqueta para la protección y los permisos relacionados con el sitio de grupo de SharePoint Online altamente confidencial.
  
1. Inicie sesión en el portal de Office 365 con una cuenta que tenga el rol Administrador de seguridad o Administrador de la compañía. Para obtener ayuda, vea [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4) (Dónde iniciar sesión en Office 365).
    
2. En una pestaña independiente del explorador, vaya a Azure Portal ([https://portal.azure.com](https://portal.azure.com)).
    
3. Si es la primera vez que configura Azure Information Protection, vea [estas instrucciones](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).
    
4. En el panel de lista, haga clic en **Más servicios**, escriba **information** y haga clic en **Azure Information Protection**.
    
5. En la hoja **Azure Information Protection**, haga clic en **Directivas con ámbito > + Agregar una directiva**.
    
6. Escriba un nombre de la nueva directiva en **Nombre de la directiva** y una descripción en **Descripción**.
    
7. Haga clic en **Seleccionar a qué usuarios o grupos se aplica esta directiva > Usuarios o grupos** y, luego, seleccione el grupo de acceso de los miembros del sitio para su sitio de grupo de SharePoint Online extremadamente confidencial. 
    
8. Haga clic en **Seleccionar > Aceptar**.
    
9. Para la etiqueta **Extremadamente confidencial**, haga clic en el botón de puntos suspensivos (...) y, luego, en **Agregar una subetiqueta**.
    
10. Escriba un nombre para la subetiqueta en **Nombre** y una descripción en **Descripción**.
    
11. En **Establecer permisos para documentos y correos electrónicos que contengan esta etiqueta**, haga clic en **Proteger**.
    
12. En la sección **Protección**, haga clic en **Azure (clave de nube)**.
    
13. En la hoja **Protección**, en **Configuración de protección**, haga clic en **+ Agregar permisos**.
    
14. En la hoja **Agregar permisos**, en **Especificar usuarios y grupos**, haga clic en **+ Examinar directorio**.
    
15. En el panel **Usuarios y grupos de AAD**, seleccione el grupo de acceso de miembros del sitio para el sitio de grupo de SharePoint Online extremadamente confidencial y haga clic en **Seleccionar**.
    
16. En **Elegir permisos entre los preestablecidos**, desactive las casillas **Imprimir**, **Copiar y extraer contenido** y **Reenviar**.
    
17. Haga clic en **Aceptar** dos veces.
    
18. En la hoja **Subetiqueta**, haga clic en **Guardar**.
    
19. Cierre la nueva hoja de directiva con ámbito.
    
20. En la hoja **Azure Information Protection: Directivas con ámbito**, haga clic en **Publicar**.
    
Esta es la configuración resultante del sitio de grupo de SharePoint Online altamente confidencial.
  
![Etiqueta de Azure Information Protection de un sitio de grupo de SharePoint Online aislado.](images/8cc92aa4-e7bc-4c2f-a4a4-3b034b21aebf.png)
  
Ya está listo para empezar a crear documentos y protegerlos con Azure Information Protection y su nueva etiqueta.
  
Necesita [instalar el cliente de Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/install-client-app) en el dispositivo o equipo basado en Windows. Puede generar scripts y automatizar la instalación, o bien los usuarios pueden instalar el cliente de forma manual. Vea los recursos siguientes:
  
- [El lado cliente de Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/use-client)
    
- [Instalación del cliente de Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide)
    
- [Página de descarga para la instalación manual](https://www.microsoft.com/download/details.aspx?id=53018)
    
Cuando se complete la instalación, los usuarios ejecutarán y, después, iniciarán sesión desde una aplicación de Office (como Microsoft Word) con su cuenta de Office 365. Una nueva barra de **Information Protection** permite a los usuarios seleccionar la nueva etiqueta. Asegúrese de que los usuarios conozcan el sitio de grupo de SharePoint Online y la etiqueta que necesitan usar para proteger sus archivos altamente confidenciales.
  
> [!NOTE]
> Si tiene varios sitios de grupo de SharePoint Online extremadamente confidenciales, deberá crear varias directivas con ámbito de Azure Information Protection que contengan subetiquetas con la configuración anterior, con los permisos de cada subetiqueta establecidos en el grupo de acceso de miembros de sitio de un equipo de grupo concreto de SharePoint Online. 
  
## <a name="see-also"></a>Vea también

[Protección de archivos y sitios de SharePoint Online](secure-sharepoint-online-sites-and-files.md)
  
[Proteger sitios de SharePoint Online en un entorno de desarrollo y pruebas](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[Guía de seguridad de Microsoft para campañas políticas, ONG y otras organizaciones ágiles](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[Adopción de la nube y soluciones híbridas](cloud-adoption-and-hybrid-solutions.md)




