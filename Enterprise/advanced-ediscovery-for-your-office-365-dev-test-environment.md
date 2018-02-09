---
title: "Exhibición avanzada de documentos electrónicos para el entorno de desarrollo y pruebas de Office 365"
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
description: 'Resumen: Configurar y demostrar eDiscovery avanzada de Office 365 con datos de ejemplo en el entorno de desarrollo y prueba de Office 365.'
ms.openlocfilehash: c55a466f05eba4e9f06ce2930dfc7c762d7fceae
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="advanced-ediscovery-for-your-office-365-devtest-environment"></a>Exhibición avanzada de documentos electrónicos para el entorno de desarrollo y pruebas de Office 365

 **Resumen:** Configurar y demostrar eDiscovery avanzada de Office 365 con datos de ejemplo en el entorno de desarrollo y prueba de Office 365.
  
EDiscovery avanzadas de Office 365 le permite buscar rápidamente y analice la información pertinente en los datos que se almacenan en Office 365, incluido el correo electrónico y documentos. Esto puede ahorrar enormes cantidades de tiempo y gastos, especialmente en situaciones de litigios. Para obtener más información, vea [Office 365 avanzada de eDiscovery](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4).
  
Con las instrucciones de este artículo, puede crear un pequeño conjunto de datos para una disputa contractual ficticia y analizarlo con la exhibición avanzada de documentos electrónicos.
  
> [!TIP]
> Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual para todos los artículos de la pila de una guía de laboratorio de prueba de nube de Microsoft.
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a>Fase 1: Crear el entorno de desarrollo y pruebas de Office 365

Si desea probar eDiscovery avanzada de una manera ligera con los requisitos mínimos, siga las instrucciones en la fase 2 y 3 de la fase del [entorno de desarrollo y prueba de Office 365](office-365-dev-test-environment.md).
  
Si desea probar eDiscovery avanzada en una empresa simulada, siga las instrucciones de [sincronización de directorios para el entorno de desarrollo y prueba de Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> Pruebas de avanzada eDiscovery no requieren el entorno simulado de enterprise, que incluye una intranet simulada conectada a Internet y sincronización de directorios para un bosque de Windows Server AD. Se proporciona aquí como una opción para que puedan realizar pruebas y experimentación en un entorno que representa una organización típica. 
  
## <a name="phase-2-create-example-data-for-advanced-ediscovery"></a>Fase 2: Crear datos de ejemplo para la exhibición avanzada de documentos electrónicos

En este procedimiento, se crean mensajes de correo electrónico que posteriormente podrá analizar en un caso de exhibición avanzada de documentos electrónicos.
  
1. Abra Internet Explorer e inicie sesión en [https://outlook.com](https://outlook.com) a la cuenta de Outlook que creó en la fase 2 del[entorno de desarrollo y prueba de Office 365](office-365-dev-test-environment.md).
    
  - Si usa el entorno de desarrollo y pruebas ligero, abra una sesión privada con Internet Explorer e inicie sesión desde el equipo local.
    
  - Si utiliza el entorno de pruebas y desarrollo empresarial simulada, usar el portal de Azure ([https://portal.azure.com](https://portal.azure.com)) para conectarse a la máquina virtual de CLIENTE1 e inicie sesión desde CLIENTE1.
    
2. En la ficha **Correo de Outlook** , haga clic en **nuevo**.
    
3. En el cuadro **para**, escriba la dirección de correo electrónico de la cuenta de User6 de su suscripción de prueba ( **user6 @.** <organization name> **. onmicrosoft.com**).
    
4. Para el asunto, escriba **prueba de correo electrónico 1**.
    
5. En el cuerpo, escriba **Tailspin contrato borrador**y, a continuación, haga clic en **Enviar**.
    
6. En la ficha **Correo de Outlook** , haga clic en **nuevo**.
    
7. En el cuadro **para**, escriba la dirección de correo electrónico de la cuenta de User6 de su suscripción de prueba.
    
8. Para el asunto, escriba **prueba de correo electrónico 2**.
    
9. En el cuerpo, escriba **comida Tailspin**y, a continuación, haga clic en **Enviar**.
    
10. En la ficha **Correo de Outlook** , haga clic en **nuevo**.
    
11. En el cuadro **para**, escriba la dirección de correo electrónico de la cuenta de User6 de su suscripción de prueba.
    
12. Para el asunto, escriba **prueba de correo electrónico 3**.
    
13. En el cuerpo, escriba **desacuerdo de Tailspin contrato**y, a continuación, haga clic en **Enviar**.
    
14. Haga clic en el icono de usuario en la esquina superior derecha y, a continuación, haga clic en **Cerrar sesión**.
    
15. Abrir una nueva pestaña e inicie sesión en el portal de Office 365 ([https://portal.office.com](https://portal.office.com)) con el nombre de cuenta y la contraseña de la cuenta de User6 de su suscripción de prueba.
    
16. En la pestaña **portal de Office 365** , haga clic en **correo**.
    
17. En la ficha **correo - User6 - Outlook** , compruebe que User6 recibido todos los tres correos electrónicos de la cuenta de correo electrónico de Outlook.
    
18. Cambie a la **pestaña portal de Office 365** para User6.
    
19. Haga clic en el icono de usuario en la esquina superior derecha y, a continuación, haga clic en **Cerrar sesión.**
    
En este procedimiento, se crean dos documentos de Word que posteriormente podrá analizar en un caso de exhibición avanzada de documentos electrónicos.
  
1. En la página de **Office** , haga clic en **iniciar sesión,** inicio de sesión con las credenciales de la cuenta de administrador global.
    
2. En una nueva pestaña, tener acceso a la dirección URL del sitio de SharePoint de producción: **https://** <fictional organization name> **.sharepoint.com/sites/production**
    
3. En la ficha de la **colección de sitios de producción** , en **los documentos**, haga clic en **Nuevo > documento de Word**.
    
4. En la página **En línea de Word** , escriba **contrato borrador de Tailspin**, espere muestra **guardada** en el título y, a continuación, cierre la ficha de página de **Word en línea** .
    
5. En la ficha de la **colección de sitios de producción** , en **los documentos**, haga clic en **Nuevo > documento de Word**.
    
6. En la ficha de **Word en línea** , escriba **Tailspin contrato disputa notas**, espere muestra **guardada** en el título y, a continuación, cierre la ficha **Word en línea** .
    
7. En la ficha de la **colección de sitios de producción** , debería ver **documento** y **Documento1** en la lista de documentos.
    
8. Cierre la ficha de la **colección de sitios de producción** .
    
## <a name="phase-3-use-advanced-ediscovery-for-a-legal-dispute"></a>Fase 3: Uso avanzado eDiscovery para un litigio legal

Desafortunadamente, un conflicto contractual entre la organización y Tailspin Toys ha alcanzado el punto de acción legal. En este procedimiento, cree y configure un caso de avanzada de eDiscovery para buscar y analizar correo electrónico y los documentos que contienen el texto "Contrato de Tailspin".
  
El proceso para utilizar la exhibición avanzada de documentos electrónicos es el siguiente:
  
- Crear una búsqueda en la seguridad &amp; centro de cumplimiento de normas, analizar sus resultados y luego prepare los resultados para eDiscovery avanzada.
    
- Cree y configure un caso en la exhibición avanzada de documentos electrónicos y analice los resultados de la búsqueda.
    
En este procedimiento, se crea una búsqueda en la seguridad &amp; centro de "Contrato de Tailspin" Busque en los resultados de cumplimiento de normas y preparar a continuación los resultados para eDiscovery avanzada.
  
1. En la pestaña **portal de Office 365** , haga clic en **Admin**.
    
2. En la exploración de la izquierda de la ficha del centro de administración, haga clic en **centros de Admin > cumplimiento de normas**.
    
3. En la **seguridad &amp; Compliance** ficha, haga clic en **permisos**.
    
4. En la lista **permisos** , haga doble clic en **Administración de la organización**.
    
5. En la ventana de **Grupo de funciones** en **miembros**, haga clic en el signo más.
    
6. En la ventana **Seleccionar miembros** , haga doble clic en el nombre de la cuenta de administrador y, a continuación, haga clic en **Aceptar**.
    
7. En la ventana de **Grupo de funciones** , haga clic en **Guardar**.
    
8. En la lista **permisos** , haga doble clic en **Administrador de eDiscovery**.
    
9. En la ventana de **Grupo de funciones** , **Administrador de eDiscovery**, haga clic en el icono de signo más.
    
10. En la ventana **Seleccionar miembros** , haga doble clic en el nombre de la cuenta de administrador y, a continuación, haga clic en **Aceptar**.
    
11. En la ventana de **Grupo de funciones** , haga clic en **Guardar**.
    
12. En la exploración de la izquierda, haga clic en **búsqueda &amp; investigación > búsqueda de contenido**.
    
13. Haga clic en el icono de signo más para agregar una búsqueda.
    
14. En la ventana **nueva búsqueda** , escriba **la búsqueda Tailspin contrato** en **nombre**.
    
15. En **¿dónde desea para buscar?**, haga clic en **Buscar en todas partes,** seleccione **Exchange**, **SharePoint**y **Las carpetas públicas**y, a continuación, haga clic en **Siguiente.**
    
16. En **¿Qué desea para buscar?**, escriba **contrato Tailspin**y, a continuación, haga clic en **Buscar**.
    
17. En la lista de búsquedas, haga clic en el nombre de **búsqueda de Tailspin contrato** .
    
18. En el panel de **búsqueda de Tailspin contrato** , haga clic en **vista previa de resultados de búsqueda** en los **resultados**. Debería ver una ventana con una lista de los dos documentos en el sitio de SharePoint de producción ( **documento** y **Documento1**) y los mensajes de **correo electrónico de prueba 1** y **3 del mensaje de prueba** a User6. Cierre la ventana.
    
19. En el panel de **búsqueda de contenido** , **analizar resultados con eDiscovery avanzada**, haga clic en **vista previa de resultados para el análisis**.
    
20. En la ventana **resultados de preparar la búsqueda para búsqueda de Tailspin contrato** , haga clic en **Finalizar** y espere a que finalice.
    
En este procedimiento, creará un nuevo caso de exhibición avanzada de documentos electrónicos y analizará los resultados de la búsqueda del contrato de Tailspin.
  
1. En la exploración de la izquierda, haga clic en **eDiscovery** bajo **búsqueda &amp; investigación**.
    
2. En el panel de **eDiscovery** , haga clic en **Ir a avanzado eDiscovery**.
    
3. En la ficha **Opciones avanzadas de eDiscovery** , haga clic en el icono de signo más para agregar un nuevo caso.
    
4. En el panel **Agregar caso** , escriba **conflicto contractual de Tailspin** en **nombre**y, a continuación, haga clic en **Aceptar**. Espere a que el caso de que se cree.
    
5. Haga doble clic en el caso de **disputa de Tailspin contrato** en la lista.
    
6. En la lista de **contenedor** , haga clic en el contenedor de **búsqueda de Tailspin contrato** y, a continuación, haga clic en **procesar**. Espere a que el procesamiento completar.
    
7. Cuando **proceso: completado** aparece en la parte inferior de la ventana, haga clic en **Resumen del proceso** de la izquierda para ver un resumen.
    
8. En la exploración superior, haga clic en **analizar**.
    
9. En la página de **configuración** , en **temas**, escriba **3** en **número máximo de temas**.
    
10. Haga clic en **analizar** y espere a que el análisis completar. Debe ver una serie de gráficos circulares con el análisis de la población objetivo, documentos, correos electrónicos y archivos adjuntos. Para obtener más información, consulte [visualización de analizar resultados](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e).
    
Ahora puede utilizar este entorno para crear nuevo contenido, nuevas búsquedas y casos, además de experimentar con la exhibición avanzada de documentos electrónicos en Office 365.
  
## <a name="see-also"></a>Consulte también

[Guías del laboratorio de pruebas de adopción de la nube (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[Entorno de desarrollo y pruebas de la configuración básica](base-configuration-dev-test-environment.md)
  
[Entorno de desarrollo y pruebas de Office 365](office-365-dev-test-environment.md)
  
[Sincronización de directorios (DirSync) para el entorno de desarrollo y pruebas de Office 365](dirsync-for-your-office-365-dev-test-environment.md)
  
[Seguridad de la aplicación de nube para su entorno de pruebas y desarrollo de Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[Adopción de la nube y soluciones híbridas](cloud-adoption-and-hybrid-solutions.md)

[EDiscovery avanzadas de Office 365](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)


