---
title: "Proteger archivos de SharePoint Online con protección de la información de Azure"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: 5b9c8e41-25d2-436d-89bb-9aecb9ec2b80
description: "Resumen: Aplicar la protección de la información de Azure para proteger los archivos en un sitio de grupo SharePoint Online altamente confidencial."
ms.openlocfilehash: 5beba188cadc88c15ec75ed2adb4899d9b41b8ec
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="protect-sharepoint-online-files-with-azure-information-protection"></a>Proteger archivos de SharePoint Online con protección de la información de Azure

 **Resumen:** Aplicar la protección de la información de Azure para proteger los archivos en un sitio de grupo SharePoint Online altamente confidencial.
  
Utilice los pasos de este artículo para configurar la protección de la información de Azure para proporcionar cifrado y los permisos de archivos en un sitio de grupo SharePoint Online altamente confidencial. La protección de cifrado y permisos viaja con un archivo, incluso cuando se descarga desde el sitio. Para obtener más información acerca de los sitios de equipo de SharePoint Online altamente confidenciales, vea [archivos y sitios de SharePoint Online seguro](secure-sharepoint-online-sites-and-files.md).
  
> [!NOTE]
> Cuando se aplica el cifrado de protección de la información de Azure a archivos almacenados en Office 365, el servicio no puede procesar el contenido de estos archivos. Co-autoría, eDiscovery, búsqueda, Delve y otras características de colaboración no funcionan. Políticas de datos Loss Prevention (DLP) sólo pueden trabajar con los metadatos (incluidos los rótulos de Office 365), pero no el contenido de estos archivos (como números de tarjeta de crédito dentro de los archivos). 
  
En primer lugar, siga las instrucciones de [Activar Azure RMS con el centro de administración de Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365) para la suscripción de Office 365.
  
A continuación, configure la protección de la información de Azure con una nueva directiva con ámbito y Sub-etiqueta de protección y los permisos de su sitio de grupo de SharePoint Online altamente confidencial.
  
1. Iniciar sesión en el portal de Office 365 con una cuenta que tiene la función de administrador de seguridad o de la empresa. Para obtener ayuda, visite [dónde puede iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. En una ficha independiente del explorador, vaya al portal de Azure ([https://portal.azure.com](https://portal.azure.com)).
    
3. Si es la primera vez se configura la protección de la información de Azure, consulte estas [instrucciones](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).
    
4. En el panel lista, haga clic en **más servicios**, escriba la **información**y, a continuación, haga clic en **Protección de la información de Azure**.
    
5. En la hoja de **protección de la información de Azure** , haga clic en **ámbito directivas > + Agregar una nueva directiva de**.
    
6. En **nombre de directiva** y una descripción, en **Descripción**, escriba un nombre para la nueva directiva.
    
7. Haga clic en **Seleccionar qué usuarios o grupos Obtén esta directiva > usuario/grupos**, y, a continuación, seleccione el sitio acceso a miembros grupo para el sitio de grupo SharePoint Online altamente confidencial. 
    
8. Haga clic en **Seleccionar > Aceptar**.
    
9. Para la etiqueta **Altamente confidencial** , haga clic en los puntos suspensivos (...) y, a continuación, haga clic en **Agregar una etiqueta Sub**.
    
10. Escriba un nombre para la Sub-etiqueta de **nombre** y una descripción de la etiqueta de **Descripción**.
    
11. **Establecer permisos para documentos y correos electrónicos con esta etiqueta**, haga clic en **proteger**.
    
12. En la sección de **protección** , haga clic en **Azure (clave de nube)**.
    
13. En la hoja de **protección** , en **configuración de protección**, haga clic en **+ Agregar permisos**.
    
14. En la hoja de **permisos para agregar** , en **especificar usuarios y grupos**, haga clic en **+ Examinar directorio**.
    
15. En el panel de **DAA usuarios y grupos** , seleccione el grupo de acceso de miembros de sitio para el sitio de grupo SharePoint Online muy confidencial y, a continuación, haga clic en **Seleccionar**.
    
16. En **Elija el ajuste preestablecido los permisos**, desactive las casillas de verificación **Imprimir**, **Copiar y extraer contenido**y **hacia delante** .
    
17. Haga clic en **Aceptar** dos veces.
    
18. En la hoja **secundario-etiqueta** , haga clic en **Guardar**.
    
19. Cierre el nuevo blade de ámbito de la política.
    
20. En el módulo de **protección de la información de Azure - directivas de ámbito** , haga clic en **Publicar**.
    
Ésta es su configuración resultante para el sitio de grupo SharePoint Online altamente confidencial.
  
![Etiqueta de protección de información de Azure de un sitio de grupo de SharePoint Online aislado.](images/8cc92aa4-e7bc-4c2f-a4a4-3b034b21aebf.png)
  
Ahora está listo para empezar a crear documentos y protegerlas con protección de la información de Azure y la nueva etiqueta.
  
Debe [instalar al cliente de protección de la información de Azure](https://docs.microsoft.com/information-protection/rms-client/install-client-app) en el dispositivo o el equipo basado en Windows. Puede automatizar la instalación y secuencia de comandos o los usuarios pueden instalar al cliente manualmente. Consulte los siguientes recursos:
  
- [El lado del cliente de protección de la información de Azure](https://docs.microsoft.com/information-protection/rms-client/use-client)
    
- [Instalación del cliente de protección de la información de Azure](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide)
    
- [Página de descarga para una instalación manual](https://www.microsoft.com/download/details.aspx?id=53018)
    
Una vez instalado, los usuarios ejecutaron y, a continuación, inicio de sesión a partir de una aplicación de Office (como Microsoft Word) con su cuenta de Office 365. Una nueva barra de **Protección de la información** permite a los usuarios seleccionar la nueva etiqueta. Asegúrese de que los usuarios saben el sitio de grupo SharePoint Online y que la etiqueta a utilizar, para proteger sus archivos altamente confidenciales.
  
> [!NOTE]
> Si tiene varios sitios de equipo de SharePoint Online altamente confidenciales, debe crear varias directivas de protección de la información de Azure ámbito con subetiquetas con la configuración anterior, con los permisos para cada Sub-etiqueta establecer al grupo acceso de miembros del sitio de un sitio de grupo SharePoint Online específico. 
  
## <a name="see-also"></a>Consulte también

[Proteger los archivos y los sitios de SharePoint Online](secure-sharepoint-online-sites-and-files.md)
  
[Sitios de SharePoint Online seguros en un entorno de pruebas y desarrollo](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[Guía de seguridad de Microsoft para campañas políticas, las ONG y otras organizaciones de Agile](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[Adopción de la nube y soluciones híbridas](cloud-adoption-and-hybrid-solutions.md)




