---
title: Exhibición avanzada de documentos electrónicos para el entorno de desarrollo y pruebas de Office 365
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
- TLG
- Ent_TLGs
ms.assetid: d4c49a6f-abfd-4d68-b353-259b4eefb033
description: 'Resumen: configure y demuestre la Exhibición avanzada de documentos electrónicos de Office 365 en el entorno de desarrollo y pruebas de Office 365.'
ms.openlocfilehash: c93900e07b8b9adbe0f1120eca77019b9dcc1eda
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897513"
---
# <a name="advanced-ediscovery-for-your-office-365-devtest-environment"></a>Exhibición avanzada de documentos electrónicos para el entorno de desarrollo y pruebas de Office 365

 **Resumen:** configure y demuestre la Exhibición avanzada de documentos electrónicos de Office 365 en el entorno de desarrollo y pruebas de Office 365.
  
EDiscovery avanzada de Office 365 le permite buscar rápidamente y analizar información relevante a través de los datos que se almacenan en Office 365, incluido el correo electrónico y documentos. Esto puede ahorrar una gran cantidad de tiempo y gastos, especialmente en situaciones de litigio. Para obtener más información, vea [Office 365 avanzada exhibición de documentos electrónicos](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4).
  
Con las instrucciones de este artículo, puede crear un pequeño conjunto de datos para una disputa contractual ficticia y analizarlo con la exhibición avanzada de documentos electrónicos.
  
> [!TIP]
> Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual de todos los artículos de la pila Guía de laboratorio de pruebas de One Microsoft Cloud.
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a>Fase 1: Crear el entorno de desarrollo y prueba de Office 365

Si desea probar avanzada exhibición de documentos electrónicos en una forma sencilla con los requisitos mínimos, siga las instrucciones que aparecen en la fase 2 y 3 de la fase del [entorno de desarrollo y prueba de Office 365](office-365-dev-test-environment.md).
  
Si desea probar avanzada exhibición de documentos electrónicos en una empresa simulada, siga las instrucciones que aparecen en la [sincronización de directorios para el entorno de desarrollo y prueba de Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> Prueba de exhibición de documentos electrónicos avanzada no requiere el entorno simulado enterprise, que incluye una intranet simulada conectada a Internet y sincronización de Active directory para un bosque de Windows Server AD. Se proporciona aquí como una opción para que pueda realizar las pruebas y la experimentación en un entorno que representa una organización típica. 
  
## <a name="phase-2-create-example-data-for-advanced-ediscovery"></a>Fase 2: Crear datos de ejemplo para la exhibición avanzada de documentos electrónicos

En este procedimiento, se crean mensajes de correo electrónico que posteriormente podrá analizar en un caso de exhibición avanzada de documentos electrónicos.
  
1. Abra Internet Explorer e iniciar sesión en [https://outlook.com](https://outlook.com) a la cuenta de Outlook que creó en la fase 2 del[entorno de desarrollo y prueba de Office 365](office-365-dev-test-environment.md).
    
  - Si usa el entorno de desarrollo y pruebas ligero, abra una sesión privada con Internet Explorer e inicie sesión desde el equipo local.
    
  - Si está utilizando el entorno de desarrollo o prueba enterprise simulado, use el portal de Azure ([https://portal.azure.com](https://portal.azure.com)) para conectarse a la máquina virtual CLIENT1 y, a continuación, iniciar sesión en desde CLIENT1.
    
2. En la pestaña **Correo de Outlook**, haga clic en **Nuevo**.
    
3. En el cuadro **para**, escriba la dirección de correo electrónico de la cuenta de User6 de su suscripción de prueba ( **user6 @.** <organization name> **. onmicrosoft.com**).
    
4. En el asunto, escriba **Correo electrónico de prueba 1**.
    
5. En el cuerpo, escriba **Proyecto de contrato de Tailspin** y, a continuación, haga clic en **Enviar**.
    
6. En la pestaña **Correo de Outlook**, haga clic en **Nuevo**.
    
7. En **Para**, escriba la dirección de correo electrónico de la cuenta de User6 de su suscripción de prueba.
    
8. En el asunto, escriba **Correo electrónico de prueba 2**.
    
9. En el cuerpo, escriba **Almuerzo de negocios de Tailspin** y, a continuación, haga clic en **Enviar**.
    
10. En la pestaña **Correo de Outlook**, haga clic en **Nuevo**.
    
11. En **Para**, escriba la dirección de correo electrónico de la cuenta de User6 de su suscripción de prueba.
    
12. En el asunto, escriba **Correo electrónico de prueba 3**.
    
13. En el cuerpo, escriba **Desacuerdo con el contrato de Tailspin** y, después, haga clic en **Enviar**.
    
14. Haga clic en el icono de usuario en la esquina superior derecha y, a continuación, haga clic en **Cerrar sesión**.
    
15. Abrir una nueva pestaña e inicie sesión en el portal de Office 365 ([https://portal.office.com](https://portal.office.com)) con el nombre de cuenta y la contraseña de la cuenta de User6 de su suscripción de prueba.
    
16. En la pestaña **Portal de Office 365**, haga clic en **Correo**.
    
17. En la ficha **correo - User6 - Outlook** , compruebe que User6 ha recibido todos los tres correos electrónicos de la cuenta de correo electrónico de Outlook.
    
18. Vuelva a la pestaña **Portal de Office 365** de User6.
    
19. Haga clic en el icono de usuario en la esquina superior derecha y después en **Cerrar sesión**.
    
En este procedimiento, se crean dos documentos de Word que posteriormente podrá analizar en un caso de exhibición avanzada de documentos electrónicos.
  
1. En la página **Office**, haga clic en **Iniciar sesión**, inicie sesión con las credenciales de su cuenta de administrador global.
    
2. En una nueva pestaña, obtener acceso a la dirección URL del sitio de SharePoint de producción: **https://** <fictional organization name> **.sharepoint.com/sites/production**
    
3. En la pestaña **Colección de sitios de producción**, en **Documentos**, haga clic en **Nuevo > Documento de Word**.
    
4. En la página de **Word Online**, escriba **Proyecto de contrato de Tailspin**, espere hasta que se muestre **Guardado** en el título y, después, cierre la pestaña de la página de **Word Online**.
    
5. En la pestaña **Colección de sitios de producción**, en **Documentos**, haga clic en **Nuevo > Documento de Word**.
    
6. 	En la pestaña de **Word Online**, escriba **Notas del conflicto del contrato de Tailspin**, espere hasta que se muestre **Guardado** en el título y, después, cierre la pestaña **Word Online**.
    
7. En la pestaña **Colección de sitios de producción**, debería ver **Documento** y **Documento1** en la lista de documentos.
    
8. Cierre la pestaña **Colección de sitios de producción**.
    
## <a name="phase-3-use-advanced-ediscovery-for-a-legal-dispute"></a>Fase 3: Uso avanzado exhibición de documentos electrónicos para un litigio legal

Desafortunadamente, un conflicto contractual entre su organización y Tailspin Toys ha alcanzado el punto de acción legal. En este procedimiento, crear y configurar un caso de exhibición de documentos electrónicos avanzadas para buscar y analizar correo electrónico y documentos que contienen el texto "Contrato Tailspin".
  
El proceso para utilizar la exhibición avanzada de documentos electrónicos es el siguiente:
  
- Crear una búsqueda en la seguridad &amp; centro de cumplimiento, analizar sus resultados y, a continuación, preparar los resultados de la exhibición de documentos electrónicos avanzadas.
    
- Cree y configure un caso en la exhibición avanzada de documentos electrónicos y analice los resultados de la búsqueda.
    
En este procedimiento, se crea una búsqueda en la seguridad &amp; cumplimiento del Centro para "Contrato Tailspin", busque en los resultados y, a continuación, preparar los resultados de la exhibición de documentos electrónicos avanzadas.
  
1. En la pestaña **Portal de Office 365**, haga clic en **Administrador**.
    
2. En el panel de navegación izquierdo de la pestaña Centro de administración, haga clic en **Centros de administración > Cumplimiento**.
    
3. En la **seguridad &amp; cumplimiento** ficha, haga clic en **permisos**.
    
4. En la lista **Permisos**, haga doble clic en **Administración de organización**.
    
5. En la ventana **Grupo de roles**, en **Miembros**, haga clic en el signo más.
    
6. En la ventana **Seleccionar miembros**, haga doble clic en el nombre de la cuenta de administrador y, a continuación, haga clic en **Aceptar**.
    
7. En la ventana **Grupo de roles **, haga clic en **Guardar**.
    
8. En la lista **Permisos**, haga doble clic en **Administrador de exhibición de documentos electrónicos **.
    
9. En la ventana **Grupo de roles**, en **Administrador de exhibición de documentos electrónicos **, haga clic en el icono de signo más.
    
10. En la ventana **Seleccionar miembros**, haga doble clic en el nombre de la cuenta de administrador y, a continuación, haga clic en **Aceptar**.
    
11. En la ventana **Grupo de roles **, haga clic en **Guardar**.
    
12. En el panel de navegación izquierdo, haga clic en **búsqueda &amp; búsqueda de contenido de investigación >**.
    
13. Haga clic en el icono de signo más para agregar una búsqueda.
    
14. En la ventana **Nueva búsqueda**, escriba **Búsqueda de contrato de Tailspin** en **Nombre**.
    
15. En **¿Dónde desea que busquemos?**, haga clic en **Buscar en todas partes,** seleccione **Exchange**, **SharePoint** y **Carpetas públicas** y, a continuación, haga clic en **Siguiente**.
    
16. En **¿Dónde desea que busquemos?**, escriba **Contrato de Tailspin** y, a continuación, haga clic en **Buscar**.
    
17. En la lista de búsquedas, haga clic en el nombre de **Búsqueda de contrato de Tailspin**.
    
18. En el panel de **búsqueda de contrato Tailspin** , haga clic en **vista previa de resultados de búsqueda** en **los resultados**. Debería ver una ventana con una lista de los dos documentos en el sitio de SharePoint de producción ( **documento** y **Documento1**) y los mensajes de **correo electrónico de prueba 1** y **prueba de correo electrónico 3** a User6. Cierre la ventana.
    
19. En el panel **Búsqueda de contenido**, en **Analizar resultados con exhibición avanzada de documentos electrónicos**, haga clic en **Vista previa de resultados para análisis**.
    
20. En la ventana **Preparar los resultados de búsqueda para la búsqueda de contrato de Tailspin**, haga clic en **Preparar** y espere a que finalice.
    
En este procedimiento, creará un nuevo caso de exhibición avanzada de documentos electrónicos y analizará los resultados de la búsqueda del contrato de Tailspin.
  
1. En el panel de navegación izquierdo, haga clic en la **exhibición de documentos electrónicos** en **búsqueda &amp; investigación**.
    
2. En el panel **Exhibición de documentos electrónicos**, haga clic en **Ir a exhibición avanzada de documentos electrónicos**.
    
3. En la pestaña **Exhibición avanzada de documentos electrónicos**, haga clic en el icono de signo más para agregar un nuevo caso.
    
4. 	En el panel **Agregar caso**, escriba **Disputa contractual de Tailspin** en **Nombre** y, a continuación, haga clic en **Aceptar**. Espere a que se cree el caso.
    
5. Haga doble clic en el caso **Disputa contractual de Tailspin** de la lista. 
    
6. En la lista de **contenedor** , haga clic en el contenedor de **búsqueda de Tailspin contrato** y, a continuación, haga clic en **proceso**. Espere a que el procesamiento para llevar a cabo.
    
7. Cuando **Proceso: completado** aparezca en la parte inferior de la ventana, haga clic en **Resumen de proceso** en la navegación izquierda para ver un resumen.
    
8. En la navegación superior, haga clic en **Analizar**.
    
9. En la página **Configuración**, en **Temas**, escriba **3** en **Número máximo de temas**.
    
10. Haga clic en **analizar** y espere a que el análisis para llevar a cabo. Debería ver una serie de gráficos circulares con el análisis de la población de destino, documentos, mensajes de correo electrónico y los datos adjuntos. Para obtener más información, vea [los resultados de la visualización de analizar](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e).
    
Ahora puede utilizar este entorno para crear nuevo contenido, nuevas búsquedas y casos, además de experimentar con la exhibición avanzada de documentos electrónicos en Office 365.
  
## <a name="see-also"></a>Vea también

[Guías del laboratorio de pruebas de adopción de la nube (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[Entorno de desarrollo y pruebas de la configuración básica](base-configuration-dev-test-environment.md)
  
[Entorno de desarrollo y pruebas de Office 365](office-365-dev-test-environment.md)
  
[Sincronización de directorios (DirSync) para el entorno de desarrollo y prueba de Office 365](dirsync-for-your-office-365-dev-test-environment.md)
  
[Seguridad de Cloud App para su entorno de desarrollo y prueba de Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[Adopción de la nube y soluciones híbridas](cloud-adoption-and-hybrid-solutions.md)

[eDiscovery avanzado de Office 365](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)


