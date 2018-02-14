---
title: "Etiquetado y clasificación de datos en el entorno de desarrollo y pruebas de Office 365"
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
ms.assetid: 919b8fc7-b0bc-46db-91f5-37342564e01b
description: "Resumen: Configurar y demostrar la clasificación de datos y etiquetado utilizando al cliente de protección de información de Azure (AIP) en el entorno de desarrollo y prueba de Office 365."
ms.openlocfilehash: 7243acecca0dd4c39ff6ef2aecd25091f25f2f53
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="data-classification-and-labeling-in-the-office-365-devtest-environment"></a>Etiquetado y clasificación de datos en el entorno de desarrollo y pruebas de Office 365

 **Resumen:** Configurar y demostrar la clasificación de datos y etiquetado utilizando al cliente de protección de información de Azure (AIP) en el entorno de desarrollo y prueba de Office 365.
  
El cliente de protección de la información de Azure permite clasificar un documento antes de cargarlo en una carpeta de SharePoint Online en Office 365. Con las instrucciones de este artículo, instale al cliente de protección de la información de Azure y demostrar la clasificación de datos. Para obtener más información, consulte [Protección de la información de Azure](https://www.microsoft.com/cloud-platform/azure-information-protection).
  
> [!TIP]
> Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual para todos los artículos de la pila de una guía de laboratorio de prueba de nube de Microsoft.
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a>Fase 1: Crear el entorno de desarrollo y pruebas de Office 365

Siga las instrucciones en el [entorno de desarrollo y prueba de Office 365](office-365-dev-test-environment.md).
  
## <a name="phase-2-add-the-azure-information-protection-trial-subscription"></a>Fase 2: Agregar la suscripción de prueba de Azure Information Protection

En esta fase, agregue Azure protección de la información para su entorno de pruebas y desarrollo de Office 365 y habilitarlo para las cuentas de usuario. Si ha configurado el [entorno de pruebas y desarrollo de EMS y Office 365](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx), omita esta fase. La suscripción de prueba de Enterprise Mobility Suite incluye licencias de protección de la información de Azure.
  
Primero, regístrese para obtener una suscripción de prueba de Azure Information Protection.
  
### <a name="sign-up-for-an-azure-information-protection-trial-subscription"></a>Registrarse para obtener una suscripción de prueba de Azure Information Protection

1. En Internet Explorer o el explorador, vaya a [http://portal.office.com](http://portal.office.com) e iniciar sesión con su cuenta de administrador global de Office 365.
    
2. En la ficha **Página de inicio de Microsoft Office** , haga clic en el mosaico de **Admin** .
    
3. En la ficha administración de Office 365, la navegación de la izquierda, haga clic en **de facturación > adquirir servicios**.
    
4. En la página **Servicios de compra** , busque el elemento de **Azure información protección Premium P2** . Coloca el ratón sobre él y haga clic en **iniciar la versión de prueba gratuita**.
    
5. En la página **confirmar su pedido** , haga clic en **Probar ahora**.
    
6. En la página de **confirmación del pedido** , haga clic en **continuar**.
    
Después, habilite la licencia de Azure Information Protection para todas las cuentas de usuario.
  
1. En la ficha de centro de administración de Office 365, haga clic en **usuarios**.
    
2.  En la lista de cuentas de usuario, seleccione la cuenta de administrador global y, a continuación, haga clic en **Editar** para **licencias de producto**.
    
3. Activar la licencia del producto para **Azure información protección Premium P2** a **en**, haga clic en **Guardar** y, a continuación, haga clic en **Cerrar** dos veces.
    
4. Repita los pasos 2 y 3 para las demás cuentas de usuario (del Usuario 1 al Usuario 5).
    
Ahora su entorno de desarrollo y pruebas de Office 365 tiene:
  
- Suscripciones de prueba de Azure Information Protection y de Office 365 E5 Enterprise.
    
- Todas las cuentas de usuario habilitadas para usar Office 365 E5 Enterprise y Azure Information Protection.
    
## <a name="phase-3-demonstrate-data-classification"></a>Fase 3: Mostrar la clasificación de datos

En esta fase, muestra la clasificación de datos con el cliente de Azure Information Protection y la directiva de Azure Information Protection predeterminada.
  
Si está usando el entorno de desarrollo y pruebas de una empresa simulada de Office 365, debe instalar primero Office 2016 en CLIENTE1.
  
1. Utilice el explorador y vaya al [portal de Azure](http://portal.azure.com).
    
2. Haga clic en **grupos de recursos >** [nombre de grupo de los recursos] **> CLIENTE1 > conectar**.
    
3. Desde CLIENTE1, ejecute Internet Explorer, visite el portal de Office en [http://portal.office.com](http://portal.office.com)y, a continuación, inicie sesión con el nombre de la cuenta usuario5 y la contraseña.
    
4. En la ficha **Página de inicio de Microsoft Office** , haga clic en **instalar Office 2016**.
    
5. Ejecute la descarga cuando se le pida y haga clic en **Sí** cuando se lo pida Control de cuentas de usuario. Espere a que Office instalar. Cuando haya terminado, haga clic **Cerrar** dos veces.
    
Después, instale el cliente de Azure Information Protection.
  
1. En el explorador o Internet Explorer, vaya a la [página de descarga de Microsoft Azure protección de la información](https://www.microsoft.com/download/details.aspx?id=53018).
    
  - Si está usando la versión ligera del entorno de desarrollo y pruebas de Office 365, use el explorador en su equipo local.
    
  - Si está usando el entorno de desarrollo y pruebas de una empresa simulada de Office 365, ejecute Internet Explorer desde CLIENTE1.
    
2. En la página de descarga de **Microsoft Azure protección de la información** , haga clic en **Descargar**, haga clic en **AzInfoProtection.exe**y, a continuación, haga clic en **siguiente**.
    
3. Cuando se le solicite, ejecute AzInfoProtection.exe.
    
4. En el cuadro cliente **instalar la protección de la información de Azure** , haga clic en **Acepto**y, a continuación, haga clic en **Sí** cuando se lo pida Control de cuentas de usuario.
    
5. En el cuadro **finalizado correctamente** , haga clic en **Cerrar.**
    
Después, muestre la clasificación de documentos.
  
1. Haga clic en el icono de **Word** en la barra de tareas.
    
2. Cuando se le solicite, inicie sesión con el nombre de cuenta Usuario5 y la contraseña.
    
3. Si acaba de instalar Office 2016 en CLIENTE1, en el **primero lo primer** cuadro, haga clic en **Aceptar**.
    
4. Haga clic en **documento en blanco**. 
    
    Tenga en cuenta la sección de **protección** de la cinta de opciones en la ficha **Inicio** y en la fila de las clasificaciones de documento.
    
5. En el documento en blanco, escriba algunas palabras.
    
6. Haga clic en **archivo > Guardar**, escriba el nombre **BeforeAIP**y, a continuación, haga clic en **Aceptar**. 
    
7. En la fila de clases de documento, haga clic en la flecha hacia abajo para el **secreto**y, a continuación, haga clic en **Empresa todo**.
    
8. Haga clic en **archivo > Guardar como**, escriba el nombre **AfterAIP**y, a continuación, haga clic en **Aceptar**.
    
9. Haga clic en **Explorador de archivos** en la barra de tareas y, a continuación, abra la carpeta **documentos** .
    
    Tenga en cuenta los diferentes tamaños de los documentos **BeforeAIP** y **AfterAIP** . El documento AfterAIP es mayor porque contiene la información de clasificación.
    
Después, permita que todos los usuarios tengan acceso a la colección de sitios de soporte.
  
1. En la ficha **Página de inicio de Microsoft Office** , haga clic en **SharePoint**.
    
2. Desde la ficha de **SharePoint** , haga clic en la **colección de sitios de soporte técnico**.
    
3. En la parte superior derecha, haga clic en el icono de **configuración** y, a continuación, haga clic en **compartido con**.
    
4. En el **recurso compartido 'Colección de sitios de soporte'**, haga clic en **Avanzadas**.
    
5. En la lista de grupos de SharePoint, haga clic en **los miembros de colección de sitios de soporte técnico**.
    
6. En la página **personas y grupos** , haga clic en **nuevo**.
    
7. En el **recurso compartido 'Colección de sitios de soporte'**, escriba **todos**, haga clic en **todos excepto los usuarios externos**y, a continuación, haga clic en **Share.**
    
8. Cierre la ficha **usuarios y grupos** .
    
Después, inicie sesión con su cuenta Usuario5 y cargue el documento protegido por AIP a la carpeta Documentos de la colección de sitios de soporte.
  
1. En la ficha **Página de inicio de Microsoft Office** , en la parte superior derecha, haga clic en el icono de usuario y, a continuación, haga clic en **Cerrar sesión**.
    
2. Vaya a [http://portal.office.com](http://portal.office.com).
    
3. En el ** iniciar una sesión en Office 365 ** de página, haga clic en el nombre de la cuenta usuario5 e identifícate.
    
4. En la ficha **Página de inicio de Microsoft Office** , haga clic en **SharePoint > compatible con la colección de sitios**.
    
5. Haga clic en **documentos**, haga clic en **cargar**, haga clic en el documento de **AfterAIP** y, a continuación, haga clic en **Abrir**.
    
    Debe ver el documento AfterAIP.docx en la carpeta Documentos de la colección de sitios de soporte.
    
## <a name="see-also"></a>Consulte también

[Guías de entorno de pruebas de adopción de la nube (TLG)](cloud-adoption-test-lab-guides-tlgs.md)

[Office 365 y entorno de desarrollo y prueba de EMS](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)
  
[Protección de la información de Azure](https://www.microsoft.com/cloud-platform/azure-information-protection)


