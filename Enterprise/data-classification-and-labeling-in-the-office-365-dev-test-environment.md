---
title: Etiquetado y clasificación de datos en el entorno de desarrollo y pruebas de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 919b8fc7-b0bc-46db-91f5-37342564e01b
description: 'Resumen: Configurar y mostrar el etiquetado y la clasificación de datos con el cliente de Azure Information Protection (AIP) en el entorno de desarrollo y pruebas de Office 365.'
ms.openlocfilehash: 66bdbb74ae88e10d5aa4fce2173f9a2b88a15e9b
ms.sourcegitcommit: 682b180061dc63cd602bee567d5414eae6942572
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2019
ms.locfileid: "31741356"
---
# <a name="data-classification-and-labeling-in-the-office-365-devtest-environment"></a>Etiquetado y clasificación de datos en el entorno de desarrollo y pruebas de Office 365

 **Resumen:** Configurar y mostrar el etiquetado y la clasificación de datos con el cliente de Azure Information Protection (AIP) en el entorno de desarrollo y pruebas de Office 365.
  
El cliente de Azure Information Protection le permite clasificar un documento antes de cargarlo en una carpeta de SharePoint Online en Office 365. Con las instrucciones de este artículo, puede instalar el cliente de Azure Information Protection y mostrar la clasificación de datos. Para obtener más información, consulte [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection).
  
> [!TIP]
> Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual de todos los artículos en la pila de la guía del entorno de pruebas de Office 365.
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a>Fase 1: Crear el entorno de desarrollo y pruebas de Office 365

Siga las instrucciones de [Office 365 dev/test environment](office-365-dev-test-environment.md).
  
## <a name="phase-2-add-the-azure-information-protection-trial-subscription"></a>Fase 2: Agregar la suscripción de prueba de Azure Information Protection

En esta fase, agregue Azure Information Protection a su entorno de desarrollo y pruebas de Office 365 y habilítelo para sus cuentas de usuario. Si ha configurado el [Office 365 and EMS dev/test environment](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx), omita esta fase. La suscripción de prueba de Enterprise Mobility Suite incluye licencias de Azure Information Protection.
  
Primero, regístrese para obtener una suscripción de prueba de Azure Information Protection.
  
### <a name="sign-up-for-an-azure-information-protection-trial-subscription"></a>Registrarse para obtener una suscripción de prueba de Azure Information Protection

1. En Internet Explorer o en su explorador, vaya [http://admin.microsoft.com](http://admin.microsoft.com) a e inicie sesión con su cuenta de administrador global de Office 365.
    
2. En la pestaña **Página principal de Microsoft Office**, haga clic en el icono de **Administración**.
    
3. En la pestaña Administración de Office 365, en el panel de navegación izquierdo, haga clic en **Facturación > Servicios de compra**.
    
4. En la página **Servicios de compra**, busque el elemento **Azure Information Protection Premium P2**. Mueva el puntero sobre el elemento y haga clic en **Iniciar prueba gratuita**.
    
5. En la página **Confirmar pedido**, haga clic en **Probar ahora**.
    
6. En la página **Recibo del pedido**, haga clic en **Continuar**.
    
Después, habilite la licencia de Azure Information Protection para todas las cuentas de usuario.
  
1. En la pestaña Centro de administración de 365 de Microsoft, haga clic en **usuarios**.
    
2.   En la lista de cuentas de usuario, seleccione la cuenta del administrador global y, después, haga clic en **Editar** para **Licencias de productos**.
    
3. 	Establezca la licencia de producto de **Azure Information Protection Premium P2** en **Activada**, haga clic en **Guardar** y, después, haga clic en **Cerrar** dos veces.
    
4. Repita los pasos 2 y 3 para las demás cuentas de usuario (del Usuario 1 al Usuario 5).
    
Ahora su entorno de desarrollo y pruebas de Office 365 tiene:
  
- Suscripciones de prueba de Azure Information Protection y de Office 365 E5 Enterprise.
    
- Todas las cuentas de usuario habilitadas para usar Office 365 E5 Enterprise y Azure Information Protection.
    
## <a name="phase-3-demonstrate-data-classification"></a>Fase 3: Mostrar la clasificación de datos

En esta fase, muestra la clasificación de datos con el cliente de Azure Information Protection y la directiva de Azure Information Protection predeterminada.
  
Si está usando el entorno de desarrollo y pruebas de una empresa simulada de Office 365, debe instalar primero Office 2016 en CLIENTE1.
  
1. Use el explorador y vaya a [Azure portal](http://portal.azure.com).
    
2. 	Haga clic en **Grupos de recursos** [el nombre del grupo de recursos] **> CLIENTE1 > Conectar**.
    
3. Desde cliente1, ejecute Internet Explorer, vaya al portal de Office en [http://admin.microsoft.com](http://admin.microsoft.com)y, a continuación, inicie sesión con el nombre de cuenta usuario5 y la contraseña.
    
4. 	En la pestaña **Página principal de Microsoft Office**, haga clic en **Instalar Office 2016**.
    
5. 	Ejecute la descarga cuando se le solicite y haga clic en **Sí** cuando se lo pida el Control de cuentas de usuario. Espere a que Office se instale. Una vez completado el proceso, haga clic en **Cerrar** dos veces.
    
Después, instale el cliente de Azure Information Protection.
  
1. En el explorador o en Internet Explorer, vaya a la [Página de descarga de Microsoft Azure Information Protection](https://www.microsoft.com/download/details.aspx?id=53018).
    
  - Si está usando la versión ligera del entorno de desarrollo y pruebas de Office 365, use el explorador en su equipo local.
    
  - Si está usando el entorno de desarrollo y pruebas de una empresa simulada de Office 365, ejecute Internet Explorer desde CLIENTE1.
    
2. En la página de descarga de **Microsoft Azure Information Protection**, haga clic en **Descargar**, en **AzInfoProtection.exe** y, después, en **Siguiente**.
    
3. Cuando se le solicite, ejecute AzInfoProtection.exe.
    
4. En el cuadro **Instalar el cliente de Azure Information Protection**, haga clic en **Acepto** y, después, en **Sí** cuando se lo pida el Control de cuentas de usuario.
    
5. En el cuadro **Completado correctamente**, haga clic en **Cerrar**.
    
Después, muestre la clasificación de documentos.
  
1. Haga clic en el icono **Word** en la barra de tareas.
    
2. Cuando se le solicite, inicie sesión con el nombre de cuenta Usuario5 y la contraseña.
    
3. Si acaba de instalar Office 2016 en CLIENTE1, en el cuadro **Lo primero es lo primero**, haga clic en **Aceptar**.
    
4. Haga clic en **Documento en blanco**.  
    
    Tenga en cuenta la sección **Protección** de la cinta de opciones en la pestaña **Inicio** y la fila de clasificaciones de documentos.
    
5. En el documento en blanco, escriba algunas palabras.
    
6. Haga clic en **Archivo > Guardar**, escriba el nombre **BeforeAIP** y, después, haga clic en **Aceptar**.  
    
7. En la fila de clases de documentos, haga clic en la flecha hacia abajo para **Secreto** y, después, haga clic en **Toda la compañía**.
    
8. Haga clic en **Archivo > Guardar como**, escriba el nombre **AfterAIP** y, después, haga clic en **Aceptar**.
    
9. Haga clic en **Explorador de archivos** en la barra de tareas y, después, abra la carpeta **Documentos**.
    
    Tenga en cuenta los tamaños de archivo diferentes de los documentos **BeforeAIP** y **AfterAIP**. El documento AfterAIP es más grande porque tiene la información de clasificación.
    
Después, permita que todos los usuarios tengan acceso a la colección de sitios de soporte.
  
1. 	En la pestaña **Página principal de Microsoft Office**, haga clic en **SharePoint**.
    
2. Desde la pestaña **SharePoint**, haga clic en **Colección de sitios de soporte**.
    
3. En la esquina superior derecha, haga clic en el icono **Configuración** y, después, en **Compartido con**.
    
4. En **compartir "colección de sitios de soporte"**, haga clic en **Opciones avanzadas**.
    
5. En la lista de grupos de SharePoint, haga clic en **Miembros de la colección de sitios de soporte**.
    
6. En la página **Personas y grupos**, haga clic en **Nuevo**.
    
7. En **compartir "colección de sitios de soporte"**, escriba **todos**, haga clic en **todos excepto los usuarios externos**y, a continuación, haga clic en **compartir.**
    
8. Cierre la pestaña **Personas y grupos**.
    
Después, inicie sesión con su cuenta Usuario5 y cargue el documento protegido por AIP a la carpeta Documentos de la colección de sitios de soporte.
  
1. En la pestaña **Página principal de Microsoft Office**, en la esquina superior derecha, haga clic en el icono de usuario y, después, en **Cerrar sesión**.
    
2. Vaya a [http://admin.microsoft.com](http://admin.microsoft.com).
    
3. En la página **Office 365 de inicio de sesión** , haga clic en el nombre de cuenta usuario5 e inicie sesión.
    
4. En la pestaña **Página principal de Microsoft Office**, haga clic en **SharePoint > colección de sitios de soporte**.
    
5. Haga clic en **Documentos**, en **Cargar**, en el documento **AfterAIP** y, después, haga clic en **Abrir**.
    
    Debe ver el documento AfterAIP.docx en la carpeta Documentos de la colección de sitios de soporte.
    
## <a name="see-also"></a>Vea también

[Guías del laboratorio de pruebas de adopción de la nube (TLG)](cloud-adoption-test-lab-guides-tlgs.md)

[Entorno de desarrollo y pruebas de Office 365 y EMS](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)
  
[Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection)


