---
title: Protección de archivos confidenciales en el entorno de desarrollo y pruebas de Office 365
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
ms.assetid: 27ecff45-06a6-4629-bc45-9dab4eef3a21
description: 'Resumen: Configurar y demostrar cómo Information Rights Management de Office 365 protege los archivos confidenciales, incluso cuando se hayan registrado para la colección de sitios de SharePoint Online incorrecta.'
ms.openlocfilehash: d866c8ef9d81ec3a80c466040dab34de8af2c1de
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915705"
---
# <a name="sensitive-file-protection-in-the-office-365-devtest-environment"></a>Protección de archivos confidenciales en el entorno de desarrollo y pruebas de Office 365

 **Resumen:** Configurar y demostrar cómo Information Rights Management de Office 365 protege los archivos confidenciales, incluso cuando se hayan registrado para la colección de sitios de SharePoint Online incorrecta.
  
Information Rights Management (IRM) en Office 365 es un conjunto de características para proteger los documentos que se descargan de listas y bibliotecas de SharePoint Online. Los archivos descargados se cifran y contienen los permisos para abrir, copiar, guardar e imprimir que refleja la biblioteca de SharePoint Online en la que se almacenan.
  
Con las instrucciones de este artículo, habilite y pruebe IRM en Office 365 para archivos que contienen posible información confidencial en su suscripción de prueba de Office 365.
  
> [!TIP]
> Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual de todos los artículos en la pila de la Guía del entorno de pruebas de One Microsoft Cloud.
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a>Fase 1: Crear el entorno de desarrollo y pruebas de Office 365

Si solo quiere probar la protección de archivos confidenciales de forma ligera con los requisitos mínimos, siga las instrucciones indicadas en las fases 2 y 3 de [Office 365 dev/test environment](office-365-dev-test-environment.md).
  
Si quiere probar la protección de archivos confidenciales en una empresa simulada, siga las instrucciones indicadas en [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> Probar la protección de archivos confidenciales no requiere el entorno de desarrollo y pruebas de una empresa simulada, que incluye una intranet simulada conectada a Internet y la sincronización de directorios para un bosque de Windows Server AD. Aquí se ofrece como opción para que pueda probar la protección de archivos confidenciales y experimentar con ella en un entorno que representa una organización típica. 
  
## <a name="phase-2-demonstrate-how-documents-from-permissions-protected-sites-can-be-leaked"></a>Fase 2: Mostrar cómo los documentos de sitios protegidos mediante permisos pueden perderse

En esta fase, muestra que un usuario puede descargar un documento de un sitio protegido mediante permisos y, después, cargarlo en un sitio que tenga permisos abiertos.
  
En primer lugar, agregue tres cuentas de usuario nuevas que representen a ejecutivos y asígneles licencias de Office 365 E5.
  
Use las instrucciones en [conectarse a Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) para instalar los módulos de PowerShell (si es necesario) y conectarse a la nueva suscripción de Office 365 desde:
  
- Su equipo (para el entorno de desarrollo y pruebas ligero de Office 365).
    
- La máquina virtual CLIENTE1 (para el entorno de desarrollo y pruebas de una empresa ficticia de Office 365).
    
En el cuadro de diálogo **Solicitud de credenciales para Windows PowerShell**, escriba el nombre de administrador global de Office 365 (ejemplo: jdoe@contosotoycompany.onmicrosoft.com) y la contraseña de su suscripción de prueba de Office 365.
  
Rellene el nombre de su organización (ejemplo: contosotoycompany), el código de país de dos caracteres para su ubicación y, después, ejecute los siguientes comandos desde el símbolo del sistema de Módulo Windows Azure Active Directory para Windows PowerShell:
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "ceo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CEO" -FirstName "Chief" -LastName "Executive Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

Desde la pantalla del comando **New-MsolUser**, anote la contraseña generada para la cuenta de CEO y guárdela en un lugar seguro.
  
Ejecute los siguientes comandos desde el símbolo del sistema del Módulo de Windows Azure Active Directory para Windows PowerShell:
  
```
$userName= "cfo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CFO" -FirstName "Chief" -LastName "Financial Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

Desde la pantalla del comando **New-MsolUser**, anote la contraseña generada para la cuenta de CFO y guárdela en un lugar seguro.
  
Ejecute los siguientes comandos desde el símbolo del sistema del Módulo de Windows Azure Active Directory para Windows PowerShell:
  
```
$userName= "coo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "COO" -FirstName "Chief" -LastName "Operations Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

Desde la pantalla del comando **New-MsolUser**, anote la contraseña generada para la cuenta de COO y guárdela en un lugar seguro.
  
Después, cree un grupo privado de ejecutivos y agregue en él las nuevas cuentas de ejecutivo.
  
1. En el explorador, vaya al portal de Office en [http://portal.office.com](http://portal.office.com) e inicie sesión en su suscripción de prueba de Office 365 con su cuenta de administrador global.
    
  - Si usa el entorno de desarrollo y pruebas ligero de Office 365, abra una sesión privada con Internet Explorer o con su explorador e inicie sesión desde el equipo local.
    
  - Si usa el entorno de desarrollo y pruebas de una empresa simulada de Office 365, use Azure Portal para conectarse a la máquina virtual CLIENTE1 e inicie sesión desde esta.
    
2. En la pestaña **Página principal de Microsoft Office**, haga clic en **Administración > Grupos > Grupos** y, después, haga clic en **Agregar un grupo**.
    
3. En **Agregar un grupo**, seleccione **Grupo de Office 365** para el tipo de grupo, escriba **Ejecutivos** en **Nombre** e **Id. de grupo**, seleccione **Privada** para **Privacidad** y, después, haga clic en **Seleccionar propietario**.
    
4. En la lista, haga clic en el nombre de cuenta del administrador global.
    
5. Haga clic en **Agregar** y, después, en **Cerrar**.
    
6. En la lista de grupos, haga clic en **Ejecutivos**.
    
7. Haga clic en **Edición de miembros**.
    
8. Haga clic en **Agregar miembros**. En la lista de miembros, seleccione las siguientes cuentas de usuario:
    
  - Director ejecutivo principal
    
  - Director financiero
    
  - Director de operaciones
    
9. Haga clic en **Guardar** y, después, en **Cerrar**.
    
10. Cierre la pestaña **Centro de administración de Office**.
    
Después, cree una colección de sitios de ejecutivos y permita que solo tengan acceso a ella los miembros del grupo Ejecutivos.
  
1. En la pestaña **Página principal de Microsoft Office**, haga clic en el icono de **Administración**.
    
2. En la ficha del **Centro de administración de Office** , haga clic en **centros de administración > SharePoint**.
    
3. En la ficha del **Centro de administración de SharePoint** , haga clic en **Nuevo > colección de sitios privados**.
    
4. En el panel de colección de sitios nueva, escriba **los ejecutivos** en **título**, los ejecutivos en el cuadro Dirección URL, especifique el nombre de la cuenta de administrador global en **Administrador**y, a continuación, haga clic en **Aceptar**.
    
5. Espere hasta que se ha creado la nueva colección de sitios. Cuando haya terminado, copie la dirección URL de la nueva colección de sitios de los ejecutivos y péguelo en una nueva ficha del explorador.
    
6. En la esquina superior derecha de la colección de sitios **Ejecutivos**, haga clic en el icono Configuración y, después, en **Compartido con**.
    
7. En el **recurso compartido 'Los ejecutivos'**, haga clic en **Avanzadas**.
    
8. En la lista de grupos de SharePoint, haga clic en **Miembros ejecutivos**.
    
9. En la página **Personas y grupos**, haga clic en **Nuevo**.
    
10. En **recurso compartido de 'ejecutivos de '**, escriba **los ejecutivos**, haga clic en el grupo de **los ejecutivos** y, a continuación, haga clic en **Compartir**.
    
11. Cierre la ficha **personas y grupos** .
    
Después, permita que todos los usuarios tengan acceso a la colección de sitios de ventas.
  
1. Desde la ficha del **Centro de administración de SharePoint** , copie la dirección URL de la colección de sitios de ventas y péguelo en una nueva ficha del explorador..
    
2. En la parte superior derecha, haga clic en el icono de configuración y, a continuación, haga clic en **compartido con**.
    
3. En **recurso compartido de 'Colección de sitios de ventas'**, haga clic en **Avanzadas**.
    
4. En la lista de grupos de SharePoint, haga clic en **Miembros de la colección de sitios de ventas**.
    
5. En la página **Personas y grupos**, haga clic en **Nuevo**.
    
6. En **recurso compartido de 'Colección de sitios de ventas'**, escriba **todos los usuarios**, haga clic en **todos excepto los usuarios externos**y, a continuación, haga clic en **Compartir**.
    
7. Cierre las pestañas **Colección de sitios de ventas** y **SharePoint**.
    
Después, inicie sesión con una cuenta de ejecutivo y cree un documento en la colección de sitios de ejecutivos.
  
1. En la pestaña **Página principal de Microsoft Office**, haga clic en el icono de usuario en la esquina superior derecha y, después, en **Cerrar sesión**.
    
2. Vaya a [http://portal.office.com](http://portal.office.com).
    
3. En la página **Office 365 iniciar sesión** , haga clic en **usar otra cuenta**.
    
4. Escriba el nombre de cuenta **CEO** y su contraseña y, luego, haga clic en **Iniciar sesión**.
    
5. En una nueva ficha del explorador, escriba la dirección URL de la colección de sitios de los ejecutivos ( **https://**\<nombre de la organización >**.sharepoint.com/sites/executives**).
    
6. Haga clic en **documentos**, haga clic en **nuevo** y, a continuación, haga clic en **Documento de Word**.
    
7. Haga clic en la barra de título y escriba **SensitiveData-BeforeIRM**.
    
8. Haga clic en el cuerpo del documento, escriba **Minutos desde la última reunión del consejo de dirección** y, después, haga clic en **Ejecutivos**.
    
      Debe ver **SensitiveData-BeforeIRM.docx** en la carpeta **Documentos**.
    
Después, descargue una copia local del documento SensitiveData-BeforeIRM.docx y, luego, publíquelo en la colección de sitios de ventas accidentalmente.
  
1. En el equipo local, cree una nueva carpeta (por ejemplo, C:\\Tlg\\SensitiveDataTestFiles).
    
2. En la pestaña **Documentos** de su explorador, seleccione el documento **SensitiveData-BeforeIRM.docx**, haga clic en los puntos suspensivos y, después, en **Descargar**.
    
3. Almacene el documento **SensitiveData-BeforeIRM.docx** en la carpeta que se ha creado en el paso 1.
    
4. En una nueva ficha del explorador, escriba la dirección URL de la colección de sitios de ventas ( **https://**\<nombre de la organización >**.sharepoint.com/sites/sales**).
    
5. Haga clic en la carpeta **Documentos** de la **Colección de sitios de ventas**.
    
6. Haga clic en **Cargar**, especifique el documento **SensitiveData-BeforeIRM.docx** en la carpeta que se ha creado en el paso 1 y, después, haga clic en **Aceptar**.
    
7. Compruebe que el documento **SensitiveData-BeforeIRM.docx** se encuentra en la carpeta **Documentos**.
    
8. Cierre las pestañas **Ventas** y **SharePoint**.
    
Después, inicie sesión como Usuario5 y pruebe a abrir el documento SensitiveData-BeforeIRM.docx en la colección de sitios de ventas.
  
1. En la pestaña **Página principal de Microsoft Office**, haga clic en el icono de usuario en la esquina superior derecha y, después, en **Cerrar sesión**.
    
2. Vaya a [http://portal.office.com](http://portal.office.com).
    
3. En la página **Office 365 iniciar sesión** , haga clic en **usar otra cuenta**.
    
4. Escriba el nombre de cuenta del Usuario5 y su contraseña y, después, haga clic en **Iniciar sesión**.
    
5. En una nueva ficha del explorador, escriba la dirección URL de la colección de sitios de ventas.
    
6. En la carpeta **Documentos** de la **Colección de sitios de ventas**, haga clic en el documento **SensitiveData-BeforeIRM.docx**. 
    
    Debe ver su contenido.
    
7. Cierre las pestañas **Documentos** y **Colección de sitios de ventas**.
    
Al publicar accidentalmente el documento SensitiveData-BeforeIRM.docx en la colección de sitios de ventas, el CEO ha ignorado la seguridad de los permisos de la colección de sitios de ejecutivos.
  
Para preparar Office 365 para las fases 3 y 4, habilite IRM para SharePoint Online.
  
1. En la pestaña **Página principal de Microsoft Office**, haga clic en el icono de usuario en la esquina superior derecha y, después, en **Cerrar sesión**.
    
2. Vaya a [http://portal.office.com](http://portal.office.com).
    
3. En la página **Inicio de sesión en Office 365**, haga clic en el nombre de cuenta del administrador global, escriba su contraseña y, después, haga clic en **Iniciar sesión**.
    
4. En la pestaña **Página principal de Microsoft Office**, haga clic en **Administración > Centros de administración > SharePoint**.
    
5. En la pestaña **Centro de administración de SharePoint**, haga clic en **Configuración**.
    
6. En la página **Configuración**, en la sección **Information Rights Management (IRM)**, seleccione **Use el servicio de IRM especificado en la configuración** y, después, seleccione **Actualizar configuración de IRM**.
    
7. Cierre la pestaña **Centro de administración de SharePoint**.
    
## <a name="phase-3-use-sharepoint-information-rights-management-with-an-office-365-private-group"></a>Fase 3: Usar SharePoint Information Rights Management con un grupo privado de Office 365

En esta fase, usa SharePoint Information Rights Management con un grupo privado de Office 365 para proteger el acceso a un documento con información confidencial, incluso cuando se ha publicado en un sitio con permisos abiertos.
  
Primero, habilite y configure IRM para la biblioteca de documentos de la colección de sitios de ejecutivos.  
  
1. En una nueva ficha del explorador, escriba la dirección URL de la colección de sitios de los ejecutivos.
    
2. Haga clic en **Documentos**.
    
3. En la esquina superior derecha, haga clic en el icono de configuración y, después, en **Configuración de la biblioteca**.
    
4. En la página **Configuración**, en **Permisos y administración**, haga clic en **Information Rights Management**.
    
5. En la página de **Configuración de Information Rights Management**:
    
  - Seleccione **Restringir permisos de acceso a los documentos de esta biblioteca al descargarlos**.
    
  - En **Crear un título de directiva de permisos**, escriba **Ejecutivos**.
    
  - En **Agregar una descripción de la directiva de permisos**, escriba **IRM para ejecutivos**.
    
6. Haga clic en **Mostrar opciones**.
    
7. En **Definir configuración adicional de la biblioteca de IRM**, seleccione **No permitir a los usuarios cargar documentos que no admitan IRM**.
    
8. En **Configurar derechos de acceso de documentos**, seleccione **Permitir que los lectores impriman** y **Permitir a los lectores escribir en una copia del documento descargado**.
    
9. En **Establecer la protección de grupos y el intervalo de credenciales**, seleccione **Permitir la protección de grupos** y, para **Grupo predeterminado**, escriba **Ejecutivos**.
    
10. Haga clic en **Aceptar**.
    
Después, actuando como el CEO, cargue un documento nuevo en la carpeta de documentos Ejecutivos, descárguelo y, después, cárguelo accidentalmente en la carpeta de documentos de ventas.
  
1. Abra la carpeta local donde ha almacenado el documento **SensitiveData-BeforeIRM.docx**.
    
2. 	Haga clic con el botón derecho en **SensitiveData-BeforeIRM.docx** y, después, haga clic en **Copiar**.
    
3. Haga clic con el botón derecho dentro de la carpeta y, después, en **Pegar**.
    
4. Cambie el nombre del nuevo archivo **SensitiveData-BeforeIRM - Copy.docx** **SensitiveData-AfterIRM.docx**.
    
5. Desde la pestaña **Página principal de Microsoft Office** de su explorador, haga clic en el icono de usuario en la esquina superior derecha y, después, en **Cerrar sesión**.
    
6. Vaya a [http://portal.office.com](http://portal.office.com).
    
7. En la página **Inicio de sesión en Office 365**, haga clic en el nombre de cuenta del CEO, escriba su contraseña y, después, haga clic en **Iniciar sesión**.
    
8. En una nueva ficha del explorador, escriba la dirección URL de la colección de sitios de los ejecutivos.
    
9. En la página **Documentos**, haga clic en **Cargar**, especifique el documento **SensitiveData-AfterIRM.docx** de su carpeta local y, después, haga clic en **Abrir**.
    
10. Seleccione el nuevo documento **SensitiveData-AfterIRM.docx** en la página **Documentos**, haga clic en los puntos suspensivos (...) de la barra de menús y, después, haga clic en **Descargar**.
    
11. Cuando se le solicite, guarde el documento **SensitiveData-AfterIRM.docx** en su carpeta local, sobrescribiendo la versión original.
    
12. Cierre la pestaña de la página **Documentos**.
    
13. En una nueva ficha del explorador, escriba la dirección URL de la colección de sitios de ventas.
    
14. Haga clic en **Documentos**.
    
15. En la página **Documentos**, haga clic en **Cargar**, especifique el documento **SensitiveData-AfterIRM.docx** de su carpeta local y, después, haga clic en **Abrir**.
    
16. Cierre las pestañas **Colección de sitios de ventas** y **SharePoint**.
    
Después, actuando como un usuario normal, intente acceder al documento **SensitiveData-AfterIRM.docx** de la carpeta de documentos de ventas.
  
1. Desde la pestaña **Página principal de Microsoft Office** de su explorador, haga clic en el icono de usuario en la esquina superior derecha y, después, en **Cerrar sesión**.
    
2. Vaya a [http://portal.office.com](http://portal.office.com).
    
3. En la página **Office 365 iniciar sesión** , haga clic en el nombre de la cuenta User5, escriba su contraseña y, a continuación, haga clic en **Inicio de sesión**.
    
4. En una nueva ficha del explorador, escriba la dirección URL de la colección de sitios de ventas.
    
5. Haga clic en **Documentos**.
    
6. En la página **Documentos**, abra el documento **SensitiveData-AfterIRM.docx**. 
    
    Debe ver un mensaje que diga "Word Online no puede abrir este documento porque está protegido por Information Rights Management (IRM)".  
    
7. Haga clic en **Editar en Word**. Se le solicitará si quiere abrir el archivo. Haga clic en **Sí**.
    
8. Se le solicitará que inicie sesión. Escriba el nombre de cuenta de la cuenta del Usuario5 y, después, haga clic en **Siguiente**.
    
9. Se le solicitará que proporcione la contraseña. Escriba la contraseña de la cuenta del Usuario5 y, después, haga clic en **Iniciar sesión**.  
    
    Debe ver un mensaje que diga: "No tiene las credenciales para abrir este documento".
    
10. Haga clic en **No**.
    
Otra manera de ver la protección de IRM es mirar los archivos de su carpeta local. El documento **SensitiveData-AfterIRM.docx** debe ser mucho más grande que el archivo **SensitiveData-BeforeIRM.docx**. El archivo **SensitiveData-AfterIRM.docx** está cifrado y se ha agregado información de protección de IRM en él.
  
## <a name="see-also"></a>Vea también

[Guías del laboratorio de pruebas de adopción de la nube (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[Entorno de desarrollo y pruebas de la configuración básica](base-configuration-dev-test-environment.md)
  
[Entorno de desarrollo y prueba de Office 365](office-365-dev-test-environment.md)
  
[Adopción de la nube y soluciones híbridas](cloud-adoption-and-hybrid-solutions.md)


