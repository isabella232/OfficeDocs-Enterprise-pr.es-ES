---
title: Exhibición avanzada de documentos electrónicos para el entorno de desarrollo y pruebas de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: d4c49a6f-abfd-4d68-b353-259b4eefb033
description: 'Resumen: configure y demuestre la Exhibición avanzada de documentos electrónicos de Office 365 en el entorno de desarrollo y pruebas de Office 365.'
ms.openlocfilehash: dbd03c1a75b63f4fdaff49db47c8d415f267aaf3
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2019
ms.locfileid: "38030674"
---
# <a name="advanced-ediscovery-for-your-office-365-devtest-environment"></a>eDiscovery avanzado para el entorno de desarrollo y pruebas de Office 365

 **Resumen:** configure y demuestre la Exhibición avanzada de documentos electrónicos de Office 365 en el entorno de desarrollo y pruebas de Office 365.
  
Office 365 Advanced eDiscovery le permite encontrar y analizar rápidamente información relevante en todos los datos que se almacenan en Office 365, incluidos el correo electrónico y los documentos. Esto puede ahorrarle muchísimo tiempo y dinero, especialmente en situaciones de litigios. Para obtener más información, consulte [Exhibición de documentos electrónicos avanzada de Office 365](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4).
  
Con las instrucciones de este artículo, puede crear un pequeño conjunto de datos para una disputa contractual ficticia y analizarlo con la exhibición avanzada de documentos electrónicos.
  
> [!TIP]
> Haga clic [aquí](https://aka.ms/catlgstack) para ver un mapa visual de todos los artículos en la pila de la Guía del laboratorio de pruebas de Office 365.
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a>Fase 1: Crear el entorno de desarrollo y prueba de Office 365

Si solo quiere probar la exhibición avanzada de documentos electrónicos de manera ligera con los requisitos mínimos, siga las instrucciones de la fase 2 y la fase 3 del [entorno de desarrollo y pruebas de Office 365](office-365-dev-test-environment.md).
  
Si desea probar la exhibición avanzada de documentos electrónicos en una empresa simulada, siga las instrucciones que se indican en [DirSync para el entorno de desarrollo y pruebas de Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> La prueba de eDiscovery avanzado no requiere el entorno empresarial simulado, que incluye una intranet simulada conectada a Internet y la sincronización de directorios para un bosque de servicios de dominio de Active Directory (AD DS). Se proporciona aquí como una opción para que pueda realizar pruebas y experimentación en un entorno que represente una organización típica. 
  
## <a name="phase-2-create-example-data-for-advanced-ediscovery"></a>Fase 2: Crear datos de ejemplo para la exhibición avanzada de documentos electrónicos

En este procedimiento, se crean mensajes de correo electrónico que posteriormente podrá analizar en un caso de exhibición avanzada de documentos electrónicos.
  
1. Abra Internet Explorer e inicie sesión [https://outlook.com](https://outlook.com) en la cuenta de Outlook que creó en la fase 2 del entorno de[desarrollo y pruebas de Office 365](office-365-dev-test-environment.md).
    
  - Si usa el entorno de desarrollo y pruebas ligero, abra una sesión privada con Internet Explorer e inicie sesión desde el equipo local.
    
  - Si usa el entorno de desarrollo y pruebas de una empresa simulada, use Azure portal ([https://portal.azure.com](https://portal.azure.com)) para conectarse a la máquina virtual CLIENT1 y, a continuación, inicie sesión desde cliente1.
    
2. En la pestaña **Correo de Outlook**, haga clic en **Nuevo**.
    
3. En **para**, escriba la dirección de correo electrónico de la cuenta de User6 de su suscripción de prueba ( **user6@.**<organization name> **. onmicrosoft.com**).
    
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
    
14. Haga clic en el icono de usuario en la esquina superior derecha y después en **Cerrar sesión**.
    
15. Abra una nueva pestaña e inicie sesión en el portal de Office 365[https://www.office.com](https://www.office.com)() con el nombre de cuenta y la contraseña de la cuenta de User6 de su suscripción de prueba.
    
16. En la pestaña **Portal de Office 365**, haga clic en **Correo**.
    
17. En la pestaña **correo-User6-Outlook** , compruebe que User6 haya recibido los tres correos electrónicos de la cuenta de correo electrónico de Outlook.
    
18. Vuelva a la pestaña **Portal de Office 365** de User6.
    
19. Haga clic en el icono de usuario en la esquina superior derecha y después en **Cerrar sesión**.
    
En este procedimiento, se crean dos documentos de Word que posteriormente podrá analizar en un caso de exhibición avanzada de documentos electrónicos.
  
1. En la página **Office**, haga clic en **Iniciar sesión**, inicie sesión con las credenciales de su cuenta de administrador global.
    
2. En una pestaña nueva, obtenga acceso a la dirección URL de su sitio de SharePoint de producción: **https://** <fictional organization name> **. SharePoint.com/sites/Production**
    
3. En la pestaña **Colección de sitios de producción**, en **Documentos**, haga clic en **Nuevo > Documento de Word**.
    
4. En la página de **Word** , **Escriba proyecto de contrato de Tailspin**, espere hasta que se muestre **guardado** en el título y, a continuación, cierre la ficha Página de **Word** .
    
5. En la pestaña **Colección de sitios de producción**, en **Documentos**, haga clic en **Nuevo > Documento de Word**.
    
6. En la pestaña **Word** , escriba **notas del conflicto del contrato de Tailspin**, espere hasta que se muestre **guardado** en el título y, a continuación, cierre la pestaña **Word** .
    
7. En la pestaña **Colección de sitios de producción**, debería ver **Documento** y **Documento1** en la lista de documentos.
    
8. Cierre la pestaña **Colección de sitios de producción**.
    
## <a name="phase-3-use-advanced-ediscovery-for-a-legal-dispute"></a>Fase 3: usar la exhibición avanzada de documentos electrónicos para una disputa legal

Desafortunadamente, una disputa contractual entre su organización y Tailspin Toys ha llegado al punto de una acción legal. En este procedimiento, creará y configurará un caso avanzado de eDiscovery para buscar y analizar el correo electrónico y los documentos que contengan el texto "contrato de Tailspin".
  
El proceso para utilizar la exhibición avanzada de documentos electrónicos es el siguiente:
  
- Crear una búsqueda en el centro &amp; de seguridad y cumplimiento, analizar los resultados y, a continuación, preparar los resultados para la exhibición avanzada de documentos electrónicos.
    
- Cree y configure un caso en la exhibición avanzada de documentos electrónicos y analice los resultados de la búsqueda.
    
En este procedimiento, creará una búsqueda en el centro &amp; de seguridad y cumplimiento para "contrato de Tailspin", examinará los resultados y luego preparará los resultados para la exhibición avanzada de documentos electrónicos.
  
1. En la pestaña **Portal de Office 365**, haga clic en **Administrador**.
    
2. En el panel de navegación izquierdo de la pestaña Centro de administración, haga clic en **Centros de administración > Cumplimiento**.
    
3. En la **pestaña &amp; seguridad y cumplimiento** , haga clic en **permisos**.
    
4. En la lista **Permisos**, haga doble clic en **Administración de organización**.
    
5. En la ventana **Grupo de roles**, en **Miembros**, haga clic en el signo más.
    
6. En la ventana **Seleccionar miembros**, haga doble clic en el nombre de la cuenta de administrador y, a continuación, haga clic en **Aceptar**.
    
7. En la ventana **Grupo de roles **, haga clic en **Guardar**.
    
8. En la lista **Permisos**, haga doble clic en **Administrador de exhibición de documentos electrónicos **.
    
9. En la ventana **Grupo de roles**, en **Administrador de exhibición de documentos electrónicos **, haga clic en el icono de signo más.
    
10. En la ventana **Seleccionar miembros**, haga doble clic en el nombre de la cuenta de administrador y, a continuación, haga clic en **Aceptar**.
    
11. En la ventana **Grupo de roles **, haga clic en **Guardar**.
    
12. En el panel de navegación izquierdo, haga clic en **investigación de búsqueda &amp; > búsqueda de contenido**.
    
13. Haga clic en el icono de signo más para agregar una búsqueda.
    
14. En la ventana **Nueva búsqueda**, escriba **Búsqueda de contrato de Tailspin** en **Nombre**.
    
15. En **¿Dónde desea que busquemos?**, haga clic en **Buscar en todas partes,** seleccione **Exchange**, **SharePoint** y **Carpetas públicas** y, a continuación, haga clic en **Siguiente**.
    
16. En **¿Dónde desea que busquemos?**, escriba **Contrato de Tailspin** y, a continuación, haga clic en **Buscar**.
    
17. En la lista de búsquedas, haga clic en el nombre de **Búsqueda de contrato de Tailspin**.
    
18. En el panel **Búsqueda de contrato de Tailspin**, haga clic en **Vista previa de los resultados de búsqueda** en **Resultados**. Debería ver una ventana con una lista de los dos documentos en el sitio de SharePoint de producción ( **Document** y **Document1**) y el **correo electrónico de prueba 1** y los correos electrónicos de **prueba 3** en User6. Cierre la ventana.
    
19. En el panel **Búsqueda de contenido**, en **Analizar resultados con exhibición avanzada de documentos electrónicos**, haga clic en **Vista previa de resultados para análisis**.
    
20. En la ventana **Preparar los resultados de búsqueda para la búsqueda de contrato de Tailspin**, haga clic en **Preparar** y espere a que finalice.
    
En este procedimiento, creará un nuevo caso de exhibición avanzada de documentos electrónicos y analizará los resultados de la búsqueda del contrato de Tailspin.
  
1. En el panel de navegación izquierdo, haga clic en **eDiscovery** en **investigación de búsqueda &amp; **.
    
2. En el panel **Exhibición de documentos electrónicos**, haga clic en **Ir a exhibición avanzada de documentos electrónicos**.
    
3. En la pestaña **Exhibición avanzada de documentos electrónicos**, haga clic en el icono de signo más para agregar un nuevo caso.
    
4. 	En el panel **Agregar caso**, escriba **Disputa contractual de Tailspin** en **Nombre** y, a continuación, haga clic en **Aceptar**. Espere a que se cree el caso.
    
5. Haga doble clic en el caso **Disputa contractual de Tailspin** de la lista. 
    
6. En la lista **contenedor** , haga clic en el contenedor de **búsqueda de contratos de Tailspin** y, a continuación, haga clic en **procesar**. Espere a que el procesamiento se complete.
    
7. Cuando **Proceso: completado** aparezca en la parte inferior de la ventana, haga clic en **Resumen de proceso** en la navegación izquierda para ver un resumen.
    
8. En la navegación superior, haga clic en **Analizar**.
    
9. En la página **Configuración**, en **Temas**, escriba **3** en **Número máximo de temas**.
    
10. Haga clic en **Analizar** y espere a que el análisis se complete. Debería ver una serie de gráficos circulares con el análisis de la población objetivo, los documentos, los correos electrónicos y los datos adjuntos. Para obtener más información, consulte [Viewing Analyze Results](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e).
    
Ahora puede utilizar este entorno para crear nuevo contenido, nuevas búsquedas y casos, además de experimentar con la exhibición avanzada de documentos electrónicos en Office 365.
  
## <a name="see-also"></a>Vea también

[Guías del laboratorio de pruebas de adopción de la nube (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[Entorno de desarrollo y pruebas de la configuración básica](base-configuration-dev-test-environment.md)
  
[Entorno de desarrollo y pruebas de Office 365](office-365-dev-test-environment.md)
  
[Sincronización de directorios (DirSync) para el entorno de desarrollo y pruebas de Office 365](dirsync-for-your-office-365-dev-test-environment.md)
  
[Adopción de la nube y soluciones híbridas](cloud-adoption-and-hybrid-solutions.md)

[eDiscovery avanzado de Office 365](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)


