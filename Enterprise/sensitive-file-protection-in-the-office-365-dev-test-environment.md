---
title: "Protección de archivos confidenciales en el entorno de desarrollo y pruebas de Office 365"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: TLG, Ent_TLGs
ms.assetid: 27ecff45-06a6-4629-bc45-9dab4eef3a21
description: "Resumen: Configurar y demostrar cómo Information Rights Management de Office 365 protege los archivos confidenciales, incluso cuando se registran en la colección de sitios de SharePoint Online incorrecta."
ms.openlocfilehash: 22f12143dc7cb50c19a135f51c08cb4b9bf02f38
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/13/2018
---
# <a name="sensitive-file-protection-in-the-office-365-devtest-environment"></a>Protección de archivos confidenciales en el entorno de desarrollo y pruebas de Office 365

 **Resumen:** Configurar y demostrar cómo Information Rights Management de Office 365 protege los archivos confidenciales, incluso cuando se registran en la colección de sitios de SharePoint Online incorrecta.
  
Information Rights Management (IRM) en Office 365 es un conjunto de características para proteger los documentos que se descargan de listas y bibliotecas de SharePoint Online. Los archivos descargados se cifran y contienen los permisos para abrir, copiar, guardar e imprimir que refleja la biblioteca de SharePoint Online en la que se almacenan.
  
Con las instrucciones de este artículo, habilite y pruebe IRM en Office 365 para archivos que contienen posible información confidencial en su suscripción de prueba de Office 365.
  
> [!TIP]
> Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual para todos los artículos de la pila de una guía de laboratorio de prueba de nube de Microsoft.
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a>Fase 1: Crear el entorno de desarrollo y pruebas de Office 365

Si desea probar la protección de archivos confidenciales en una manera ligera con los requisitos mínimos, siga las instrucciones en las fases 2 y 3 del [entorno de desarrollo y prueba de Office 365](office-365-dev-test-environment.md).
  
Si desea probar la protección de archivos confidenciales en una empresa simulada, siga las instrucciones de [sincronización de directorios para el entorno de desarrollo y prueba de Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> Probar la protección de archivos confidenciales no requiere el entorno de desarrollo y pruebas de una empresa simulada, que incluye una intranet simulada conectada a Internet y la sincronización de directorios para un bosque de Windows Server AD. Aquí se ofrece como opción para que pueda probar la protección de archivos confidenciales y experimentar con ella en un entorno que representa una organización típica. 
  
## <a name="phase-2-demonstrate-how-documents-from-permissions-protected-sites-can-be-leaked"></a>Fase 2: Mostrar cómo los documentos de sitios protegidos mediante permisos pueden perderse

En esta fase, muestra que un usuario puede descargar un documento de un sitio protegido mediante permisos y, después, cargarlo en un sitio que tenga permisos abiertos.
  
En primer lugar, agregue tres cuentas de usuario nuevas que representen a ejecutivos y asígneles licencias de Office 365 E5.
  
Siga las instrucciones de [conectarse a Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) para instalar los módulos de PowerShell (si es necesario) y conectarse a la nueva suscripción de Office 365 desde:
  
- Su equipo (para el entorno de desarrollo y pruebas ligero de Office 365).
    
- La máquina virtual CLIENT1 (para el entorno de desarrollo y pruebas de una empresa simulada de Office 365).
    
En el cuadro de diálogo **Solicitud de credencial de Windows PowerShell** , escriba el nombre de administrador global de Office 365 (ejemplo: jdoe@contosotoycompany.onmicrosoft.com) y la contraseña de su suscripción de prueba de Office 365.
  
Rellene el nombre de su organización (ejemplo: contosotoycompany), el código de país de dos caracteres para su ubicación y, después, ejecute los siguientes comandos desde el símbolo del sistema de Módulo Windows Azure Active Directory para Windows PowerShell:
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "ceo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CEO" -FirstName "Chief" -LastName "Executive Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

En la pantalla del comando **MsolUser de nuevo** , observe la contraseña generada para la cuenta de director general y grabarlo en un lugar seguro.
  
Ejecute los siguientes comandos desde el símbolo del sistema del Módulo de Windows Azure Active Directory para Windows PowerShell:
  
```
$userName= "cfo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CFO" -FirstName "Chief" -LastName "Financial Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

En la pantalla del comando **MsolUser de nuevo** , anote la contraseña para la cuenta de director financiero generada y grabarlo en un lugar seguro.
  
Ejecute los siguientes comandos desde el símbolo del sistema del Módulo de Windows Azure Active Directory para Windows PowerShell:
  
```
$userName= "coo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "COO" -FirstName "Chief" -LastName "Operations Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

En la pantalla del comando **MsolUser de nuevo** , tenga en cuenta la contraseña generada para la cuenta de director de operaciones y grabarla en un lugar seguro.
  
Después, cree un grupo privado de ejecutivos y agregue en él las nuevas cuentas de ejecutivo.
  
1. En el explorador, visite el portal de Office en [http://portal.office.com](http://portal.office.com) e inicie sesión a su suscripción de prueba de Office 365 con su cuenta de administrador global.
    
  - Si usa el entorno de desarrollo y pruebas ligero de Office 365, abra una sesión privada con Internet Explorer o con su explorador e inicie sesión desde el equipo local.
    
  - Si usa el entorno de desarrollo y pruebas de una empresa simulada de Office 365, use Azure Portal para conectarse a la máquina virtual CLIENTE1 e inicie sesión desde esta.
    
2. En la ficha **Página de inicio de Microsoft Office** , haga clic en **Admin > grupos > grupos de**y, a continuación, haga clic en **Agregar un grupo**.
    
3. En **Agregar un grupo**, seleccione **grupo de Office 365** para el tipo de grupo, escriba **ejecutivos** en **nombre** e **Identificador de grupo**, seleccione la opción de **privacidad** **privado** y, a continuación, haga clic en **Seleccionar propietario**.
    
4. En la lista, haga clic en el nombre de cuenta del administrador global.
    
5. Haga clic en **Agregar**y, a continuación, haga clic en **Cerrar**.
    
6. En la lista grupos, haga clic en **ejecutivos**.
    
7. Haga clic en **Editar para miembros**.
    
8. Haga clic en **Agregar miembros**. En la lista de miembros, seleccione las cuentas de usuario siguientes:
    
  - Director ejecutivo principal
    
  - Director financiero
    
  - Director de operaciones
    
9. Haga clic en **Guardar**y, a continuación, haga clic en **Cerrar**.
    
10. Cierre la ficha de **Centro de administración de Office** .
    
Después, cree una colección de sitios de ejecutivos y permita que solo tengan acceso a ella los miembros del grupo Ejecutivos.
  
1. En la ficha **Página de inicio de Microsoft Office** , haga clic en el mosaico de **Admin** .
    
2. En la ficha del **Centro de administración de Office** , haga clic en **centros de Admin > SharePoint**.
    
3. En la ficha del **Centro de administración de SharePoint** , haga clic en **Nuevo > colección de sitios privado**.
    
4. En el nuevo panel de colección de sitios, escriba **ejecutivos** en **título**, en el cuadro Dirección URL, los ejecutivos especificar el nombre de la cuenta de administrador global en **Administrador**y, a continuación, haga clic en **Aceptar**.
    
5. Espere hasta que se ha creado la nueva colección de sitios. Cuando haya finalizado, copie la dirección URL de la nueva colección de sitios de ejecutivos y pegarla en una nueva ficha del explorador.
    
6. En la parte superior derecha de la colección de sitios de **ejecutivos** , haga clic en el icono de configuración y, a continuación, haga clic en **compartido con**.
    
7. En el **recurso compartido 'Ejecutivos'**, haga clic en **Avanzadas**.
    
8. En la lista de grupos de SharePoint, haga clic en **Miembros de ejecutivos**.
    
9. En la página **personas y grupos** , haga clic en **nuevo**.
    
10. En el **recurso compartido 'Ejecutivos'**, escriba **ejecutivos**, haga clic en el grupo de **ejecutivos** y, a continuación, haga clic en **Compartir**.
    
11. Cierre la ficha **usuarios y grupos** .
    
Después, permita que todos los usuarios tengan acceso a la colección de sitios de ventas.
  
1. Desde la ficha del **Centro de administración de SharePoint** , copie la dirección URL de la colección de sitios de ventas y pegarla en una nueva ficha del explorador..
    
2. En la parte superior derecha, haga clic en el icono de configuración y, a continuación, haga clic en **compartido con**.
    
3. En el **recurso compartido 'Colección de sitios de ventas'**, haga clic en **Avanzadas**.
    
4. En la lista de grupos de SharePoint, haga clic en **los miembros de la colección de sitios de ventas**.
    
5. En la página **personas y grupos** , haga clic en **nuevo**.
    
6. En el **recurso compartido 'Colección de sitios de ventas'**, escriba **todos**, haga clic en **todos excepto los usuarios externos**y, a continuación, haga clic en **Compartir**.
    
7. Cierra las fichas de la **colección de sitios de ventas** y **SharePoint** .
    
Después, inicie sesión con una cuenta de ejecutivo y cree un documento en la colección de sitios de ejecutivos.
  
1. En la ficha **Página de inicio de Microsoft Office** , haga clic en el icono de usuario en la parte superior derecha y, a continuación, haga clic en **Cerrar sesión**.
    
2. Vaya a [http://portal.office.com](http://portal.office.com).
    
3. En la página **Office 365 iniciar sesión en** , haga clic en **usar otra cuenta**.
    
4. Escriba el nombre de la cuenta de **Director general** y su contraseña y, a continuación, haga clic en **iniciar sesión**.
    
5. En una nueva pestaña del explorador, escriba la dirección URL de la colección de sitios de ejecutivos ( **https://**\<nombre de la organización >**.sharepoint.com/sites/executives**).
    
6. Haga clic en **documentos**, haga clic en **nuevo** y, a continuación, haga clic en **Documento de Word**.
    
7. Haga clic en la barra de título y escriba **SensitiveData-BeforeIRM**.
    
8. Haga clic en el cuerpo del documento, escriba los **minutos desde la última reunión de la junta**y, a continuación, haga clic en **ejecutivos**.
    
     Debería ver **BeforeIRM.docx de SensitiveData** en la carpeta **documentos** .
    
Después, descargue una copia local del documento SensitiveData-BeforeIRM.docx y, luego, publíquelo en la colección de sitios de ventas accidentalmente.
  
1. En el equipo local, cree una nueva carpeta (por ejemplo, C:\\TLGs\\SensitiveDataTestFiles).
    
2. En la ficha de **documentos** del explorador, seleccione el documento de **BeforeIRM.docx de SensitiveData** , haga clic en los puntos suspensivos y, a continuación, haga clic en **Descargar**.
    
3. Guarde el documento **BeforeIRM.docx de SensitiveData** en la carpeta creada en el paso 1.
    
4. En una nueva pestaña del explorador, escriba la dirección URL de la colección de sitios de ventas ( **https://**\<nombre de la organización >**.sharepoint.com/sites/sales**).
    
5. Haga clic en la carpeta de **documentos** de la **colección de sitios de ventas**.
    
6. Haga clic en **cargar**y a continuación, especifique el documento **BeforeIRM.docx de SensitiveData** en la carpeta que creó en el paso 1 y, a continuación, haga clic en **Aceptar**.
    
7. Compruebe que el documento **BeforeIRM.docx de SensitiveData** está en la carpeta **documentos** .
    
8. Cierra las fichas **ventas** y **SharePoint** .
    
Después, inicie sesión como Usuario5 y pruebe a abrir el documento SensitiveData-BeforeIRM.docx en la colección de sitios de ventas.
  
1. En la ficha **Página de inicio de Microsoft Office** , haga clic en el icono de usuario en la parte superior derecha y, a continuación, haga clic en **Cerrar sesión**.
    
2. Vaya a [http://portal.office.com](http://portal.office.com).
    
3. En la página **Office 365 iniciar sesión en** , haga clic en **usar otra cuenta**.
    
4. Escriba el nombre de la cuenta usuario5 y su contraseña y, a continuación, haga clic en **iniciar sesión**.
    
5. En una nueva pestaña del explorador, escriba la dirección URL de la colección de sitios de ventas.
    
6. En la carpeta de **documentos** de la **colección de sitios de ventas**, haga clic en el documento **BeforeIRM.docx de SensitiveData** .
    
    Debe ver su contenido.
    
7. Cierra las fichas de **documentos** y **colección de sitios de ventas** .
    
Al publicar accidentalmente el documento SensitiveData-BeforeIRM.docx en la colección de sitios de ventas, el CEO ha ignorado la seguridad de los permisos de la colección de sitios de ejecutivos.
  
Para preparar Office 365 para las fases 3 y 4, habilite IRM para SharePoint Online.
  
1. En la ficha **Página de inicio de Microsoft Office** , haga clic en el icono de usuario en la parte superior derecha y, a continuación, haga clic en **Cerrar sesión**.
    
2. Vaya a [http://portal.office.com](http://portal.office.com).
    
3. En la página **Office 365 iniciar sesión en** , haga clic en el nombre de la cuenta de administrador global, escriba su contraseña y, a continuación, haga clic en **Inicio de sesión**.
    
4. En la ficha **Página de inicio de Microsoft Office** , haga clic en **Admin > centros de Admin > SharePoint**.
    
5. En la ficha del **Centro de administración de SharePoint** , haga clic en **configuración**.
    
6. En la página de **configuración** , en la sección de **Information Rights Management (IRM)** , seleccione **usar el servicio IRM especificado en la configuración**y, a continuación, seleccione **Actualizar configuración de IRM**.
    
7. Cierre la ficha de **Centro de administración de SharePoint** .
    
## <a name="phase-3-use-sharepoint-information-rights-management-with-an-office-365-private-group"></a>Fase 3: Usar SharePoint Information Rights Management con un grupo privado de Office 365

En esta fase, usa SharePoint Information Rights Management con un grupo privado de Office 365 para proteger el acceso a un documento con información confidencial, incluso cuando se ha publicado en un sitio con permisos abiertos.
  
Primero, habilite y configure IRM para la biblioteca de documentos de la colección de sitios de ejecutivos.  
  
1. En una nueva pestaña del explorador, escriba la dirección URL de la colección de sitios de ejecutivos.
    
2. Haga clic en **documentos**.
    
3. En la parte superior derecha, haga clic en el icono de configuración y, a continuación, haga clic en **configuración de la biblioteca**.
    
4. En la página de **configuración** , en **permisos y administración**, haga clic en **Information Rights Management**.
    
5. En la página **Configuración de Information Rights Management** :
    
  - Seleccione **restringir el acceso a los documentos de esta biblioteca al descargarlos**.
    
  - Para **crear un título de directiva de permisos**, escriba **ejecutivos**.
    
  - Para **Agregar una descripción de la directiva de permiso**, escriba **IRM para ejecutivos**.
    
6. Haga clic en **Mostrar opciones**.
    
7. En **establecer la configuración de la biblioteca IRM adicionales**, seleccione **no permitir a los usuarios cargar documentos que no admitan IRM**.
    
8. En **Configurar derechos de acceso de documento**, seleccione **Permitir visores para imprimir** y **visores de permitir escribir en una copia del documento descargado**.
    
9. En **Establecer grupo de protección y el intervalo de credenciales**, seleccione **Permitir protección de grupo** y para el **grupo predeterminado**, escriba **ejecutivos**.
    
10. Haga clic en **Aceptar**.
    
Después, actuando como el CEO, cargue un documento nuevo en la carpeta de documentos Ejecutivos, descárguelo y, después, cárguelo accidentalmente en la carpeta de documentos de ventas.
  
1. Abra la carpeta local donde se almacena el documento **BeforeIRM.docx de SensitiveData** .
    
2. Haga clic en **BeforeIRM.docx de SensitiveData**y, a continuación, haga clic en **Copiar**.
    
3. Pulse el botón derecho dentro de la carpeta y, a continuación, haga clic en **Pegar**.
    
4. Cambie el nombre del nuevo archivo **SensitiveData-BeforeIRM - Copy.docx** **SensitiveData AfterIRM.docx**.
    
5. Desde la ficha **Página de inicio de Microsoft Office** en el explorador, haga clic en el icono de usuario en la parte superior derecha y, a continuación, haga clic en **Cerrar sesión**.
    
6. Vaya a [http://portal.office.com](http://portal.office.com).
    
7. En la página **Office 365 iniciar sesión en** , haga clic en el nombre de la cuenta de director ejecutivo, escriba su contraseña y, a continuación, haga clic en **Inicio de sesión**.
    
8. En una nueva pestaña del explorador, escriba la dirección URL de la colección de sitios de ejecutivos.
    
9. En la página de **los documentos** , haga clic en **cargar**, especificar el documento **AfterIRM.docx de SensitiveData** en la carpeta local y, a continuación, haga clic en **Abrir**.
    
10. Seleccione el nuevo documento de **AfterIRM.docx de SensitiveData** en la página de **los documentos** , haga clic en el botón de puntos suspensivos (...) en la barra de menús y, a continuación, haga clic en **Descargar**.
    
11. Cuando se le pida, guarde el documento **AfterIRM.docx de SensitiveData** en la carpeta local, sobrescribiendo la versión original.
    
12. Cierre la ficha de la página de **los documentos** .
    
13. En una nueva pestaña del explorador, escriba la dirección URL de la colección de sitios de ventas.
    
14. Haga clic en **documentos**.
    
15. En la página de **los documentos** , haga clic en **cargar**, especificar el documento **AfterIRM.docx de SensitiveData** en la carpeta local y, a continuación, haga clic en **Abrir**.
    
16. Cierra las fichas de la **colección de sitios de ventas** y **SharePoint** .
    
Actúa como un usuario normal, a continuación, intenta tener acceso al documento de **AfterIRM.docx de SensitiveData** en la carpeta de documentos de ventas.
  
1. Desde la ficha **Página de inicio de Microsoft Office** en el explorador, haga clic en el icono de usuario en la parte superior derecha y, a continuación, haga clic en **Cerrar sesión**.
    
2. Vaya a [http://portal.office.com](http://portal.office.com).
    
3. En la página **Office 365 iniciar sesión en** , haga clic en el nombre de la cuenta usuario5, escriba su contraseña y, a continuación, haga clic en **Inicio de sesión**.
    
4. En una nueva pestaña del explorador, escriba la dirección URL de la colección de sitios de ventas.
    
5. Haga clic en **documentos**.
    
6. En la página **documentos** , abra el documento de **AfterIRM.docx de SensitiveData** .
    
    Debe ver un mensaje que diga "Word Online no puede abrir este documento porque está protegido por Information Rights Management (IRM)".  
    
7. Haga clic en **Editar en Word**. Se le pedirá si desea abrir el archivo. Haga clic en **Sí**.
    
8. Se le pedirá que el inicio de sesión. Escriba el nombre de la cuenta usuario5 y, a continuación, haga clic en **siguiente**.
    
9. Se le pedirá que proporcione la contraseña. Escriba la contraseña de la cuenta usuario5 y, a continuación, haga clic en **iniciar sesión**. 
    
    Debe ver un mensaje que diga: "No tiene las credenciales para abrir este documento".
    
10. Haga clic en **No**.
    
Otra forma de ver la protección de IRM es mirar los archivos de la carpeta local. El **AfterIRM.docx de SensitiveData** debe ser mucho mayor que el archivo **SensitiveData-BeforeIRM.docx** . Se cifra el archivo **SensitiveData-AfterIRM.docx** y ha agregado la información de la protección de IRM.
  
## <a name="see-also"></a>Consulte también

[Guías del laboratorio de pruebas de adopción de la nube (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[Entorno de desarrollo y pruebas de la configuración básica](base-configuration-dev-test-environment.md)
  
[Entorno de desarrollo y pruebas de Office 365](office-365-dev-test-environment.md)
  
[Adopción de la nube y soluciones híbridas](cloud-adoption-and-hybrid-solutions.md)


