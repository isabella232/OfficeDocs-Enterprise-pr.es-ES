---
title: Agregar varios usuarios a Office 365 a la vez - Ayuda de administración
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.date: 6/29/2018
audience: Admin
ms.topic: article
f1_keywords:
- O365P_AddUsersCSV
- O365M_AddUsersCSV
- O365E_AddUsersCSV
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOP150
- MOE150
- MED150
- GMA150
- MBS150
- GEA150
- BCS160
ms.assetid: 1f5767ed-e717-4f24-969c-6ea9d412ca88
description: 'Obtenga información sobre cómo agregar varios usuarios a Office 365 para empresas desde una lista de una hoja de cálculo u otro archivo con formato CSV. Vea un vídeo en YouTube que explica cómo agregar cuentas a Office 365. Al final de este proceso, cada usuario con una cuenta tendrá un buzón de Office 365. '
ms.openlocfilehash: a719b2626eada8abe225a6951af4a2d292667856
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2019
ms.locfileid: "38030734"
---
# <a name="add-several-users-at-the-same-time-to-office-365---admin-help"></a>Agregar varios usuarios a Office 365 a la vez. Ayuda para administradores

Todos los usuarios de su grupo deben tener una cuenta de usuario para poder iniciar sesión y acceder a servicios de Office 365, como el correo electrónico y Office. Si son muchas personas, puede agregar sus cuentas de una vez desde una hoja de cálculo de Excel u otro archivo guardado en formato CSV. [¿No tiene claro qué es un archivo CSV?](add-several-users-at-the-same-time.md#__toc316652088)
  
## <a name="add-multiple-users-to-office-365-in-the-microsoft-365-admin-center"></a>Agregar varios usuarios a Office 365 en el centro de administración de Microsoft 365

1. Inicie sesión en Office 365 con su cuenta profesional o educativa. 
    
2. En el centro de administración, **Elija** \> usuarios **activos**.
    
    ![En el centro de administración, elija usuarios y, a continuación, usuarios activos](media/12086d98-a8b4-4c48-89cf-b78ad8058ff1.png)
  
    
3. En el panel **Importar varios usuarios**, tiene la opción de descargar un archivo CSV de ejemplo con datos de ejemplo o sin rellenar. 
    
    ![In the More drop-down, choose Import multiple users](media/77df8a4a-fd00-4fbe-bf1c-d234fc1d5e93.png)
  
    Su hoja de cálculo debe incluir **exactamente los mismos encabezados de columna** que la de ejemplo (Nombre de usuario, Nombre, etc.). Si usa la plantilla, ábrala en una herramienta de edición de texto y considere la opción de no editar ningún dato de la fila 1 y escribir los datos a partir de la fila 2. 
    
    La hoja de cálculo también debe incluir valores para el nombre de usuario (por ejemplo, alberto@contoso.com) y un nombre para mostrar (por ejemplo, Alberto Hermosilla) para cada usuario. 
    
  ```
  User Name,First Name,Last Name,Display Name,Job Title,Department,Office Number,Office Phone,Mobile Phone,Fax,Address,City,State or Province,ZIP or Postal Code,Country or Region
  chris@contoso.com,Chris,Green,Chris Green,IT Manager,Information Technology,123451,123-555-1211,123-555-6641,123-555-9821,1 Microsoft way,Redmond,Wa,98052,United States
  ben@contoso.com,Ben,Andrews,Ben Andrews,IT Manager,Information Technology,123452,123-555-1212,123-555-6642,123-555-9822,1 Microsoft way,Redmond,Wa,98052,United States
  david@contoso.com,David,Longmuir,David Longmuir,IT Manager,Information Technology,123453,123-555-1213,123-555-6643,123-555-9823,1 Microsoft way,Redmond,Wa,98052,United States
  cynthia@contoso.com,Cynthia,Carey,Cynthia Carey,IT Manager,Information Technology,123454,123-555-1214,123-555-6644,123-555-9824,1 Microsoft way,Redmond,Wa,98052,United States
  melissa@contoso.com,Melissa,MacBeth,Melissa MacBeth,IT Manager,Information Technology,123455,123-555-1215,123-555-6645,123-555-9825,1 Microsoft way,Redmond,Wa,98052,United States
  
  ```

4. Escriba una ruta de acceso al archivo en el cuadro o elija **Examinar** para ir a la ubicación del archivo CSV y, a continuación, elija **Comprobar**.
    
    ![Your CSV file is verified](media/a43d49db-b2ab-4200-8ddf-0bc846ac6fe5.png)
  
    Si hay problemas con el archivo, se mostrarán en el panel. También puede descargar un archivo de registro.
    
5. En el cuadro de diálogo **Establecer opciones de usuario**, puede establecer el estado de inicio de sesión y elegir qué licencia de producto se asignará a cada uno de los usuarios. 
    
6. En el cuadro de diálogo **Ver el resultado**, puede elegir si desea enviar los resultados a su usuario o a otros usuarios (las contraseñas se mostrarán en texto sin formato). Además, puede ver cuántos usuarios se crearon y, si lo necesita, comprar más licencias para asignárselas a algunos de los nuevos usuarios. 
    
## <a name="watch-the-video"></a>Ver vídeo
<a name="bk_preview"> </a>

 Vea un breve vídeo en el que se muestra cómo agregar usuarios en masa. 
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/f4e7f161-8ae6-4264-a429-9297b539a8de?autoplay=false]
  
## <a name="next-steps"></a>Siguientes pasos
<a name="bk_preview"> </a>

- Ahora que estas personas tienen cuentas, necesitan [Descargar e instalar o reinstalar office 365 u office 2016 en un equipo PC o Mac](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658). Cada persona de su equipo puede usar Office 365 en un máximo de 5 equipos o Mac. 
    
- Cada persona también puede [configurar el correo electrónico y las aplicaciones de Office en un dispositivo móvil en un](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f) máximo de 5 tabletas y 5 teléfonos, como iPhone, iPad, y teléfonos y tabletas Android. De esta forma, puede editar archivos de Office desde cualquier lugar. 
    
    Vea [set up Office 365 for Business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) para obtener una lista completa de los pasos de configuración. 
    
## <a name="more-information-about-how-to-add-users-to-office-365"></a>Más información sobre cómo agregar usuarios a Office 365
<a name="bk_preview"> </a>

### <a name="not-sure-what-csv-format-is"></a>¿No tiene claro qué es un archivo CSV?
<a name="__toc316652088"> </a>

Un archivo CSV es un archivo con valores separados por comas. Puede crear o editar un archivo como este con cualquier editor de textos o programa de hojas de cálculo, como Excel.
  
Puede descargar [esta hoja de cálculo de muestra](https://www.microsoft.com/download/details.aspx?id=45485) como punto de partida. Recuerde que Office 365 requiere encabezados de columna en la primera fila, así que no los sustituya con ningún otro elemento. 
  
Guarde el archivo con un nuevo nombre y especifique el formato CSV.
  
![Imagen de cómo guardar un archivo de Excel en formato CSV](media/35a86ebe-63ab-4b4d-9a92-e177de33ebae.png)
  
Cuando guarde el archivo, probablemente recibirá un mensaje que le informará de que se perderán algunas características del libro si guarda el archivo en formato CSV. No pasa nada. Haga clic en **Sí** para continuar. 
  
![Imagen del mensaje que obtendría en Excel que pregunta si realmente quiere guardar el archivo como formato CSV](media/51032a81-690c-45ef-bfc5-09ea7f790e98.png)
  
### <a name="tips-for-formatting-your-spreadsheet"></a>Consejos para aplicar formato a la hoja de cálculo
<a name="__toc314595848"> </a>

- **¿Debo mantener los mismos encabezados de columna que en la hoja de cálculo de muestra?** Sí. La hoja de cálculo de muestra contiene los encabezados de columna en la primera fila. Estos encabezados son necesarios. Para cada usuario que desee agregar a Office 365, cree una fila bajo el encabezado. Si agrega, cambia o elimina cualquiera de los encabezados de columna, Office 365 podría no crear usuarios a partir de la información del archivo. 
    
- **¿Qué ocurre si no tengo toda la información requerida para cada usuario?** El nombre de usuario y el nombre para mostrar son obligatorios, y no puede agregar un nuevo usuario sin esta información. Si le falta parte de la información, como el fax, puede usar un espacio más una coma para indicar que el campo debe dejarse en blanco. 
    
- ** How small or large can the spreadsheet be? ** The spreadsheet must have at least two rows. One is for the column headings (the user data column label) and one for the user. You cannot have more than 251 rows. If you need to import more than 250 users, you can create more than one spreadsheet. 
    
- ** What languages can I use? ** When you create your spreadsheet, you can enter user data column labels in any language or characters, but you must not change the order of the labels, as shown in the sample. You can then make entries into the fields, using any language or characters, and save your file in a Unicode or UTF-8 format. 
    
- **¿Qué ocurre si voy a agregar usuarios de diferentes países o regiones?** Cree una hoja de cálculo para cada área. Deberá seguir los pases del asistente para agregar usuarios en bloque para cada una de las hojas de cálculo y dar una única ubicación a todos los usuarios incluidos en el archivo con los que trabaja. 
    
- **¿Existe algún límite de caracteres que se pueden usar?** En la siguiente tabla se muestran las etiquetas de las columnas de datos de usuario y la longitud máxima (en caracteres) para cada una en la hoja de cálculo de muestra. 
    
|**Etiquetas columnas datos usuarios**|**Longitud máxima (en caracteres)**|
|:-----|:-----|
|Nombre de usuario (obligatorio)  <br/> |79 incluida la arroba (@), en el formato nombre@dominio.\<extensión\>. El alias del usuario no debe superar los 30 caracteres y el nombre de dominio no debe superar los 48 caracteres.  <br/> |
|Nombre  <br/> |64  <br/> |
|Apellido  <br/> |64  <br/> |
|Nombre para mostrar (obligatorio)  <br/> |256  <br/> |
|Puesto  <br/> |64  <br/> |
|Departamento  <br/> |64  <br/> |
|Número del trabajo  <br/> |128  <br/> |
|Teléfono del trabajo  <br/> |64  <br/> |
|Teléfono móvil  <br/> |64  <br/> |
|Fax  <br/> |64  <br/> |
|Dirección  <br/> |1023  <br/> |
|Ciudad  <br/> |128  <br/> |
|Estado o provincia  <br/> |128  <br/> |
|Código postal  <br/> |40  <br/> |
|País o región  <br/> |128  <br/> |
   
### <a name="still-having-problems-when-adding-users-to-office-365"></a>¿Aún tiene problemas al agregar usuarios a Office 365?

- **Asegúrese una vez más de que el archivo tenga un formato correcto.** Compruebe que los encabezados de las columnas coincidan con los encabezados del archivo de muestra. Asegúrese de haber respetado los límites de longitud y de que los campos estén separados por comas. 
    
- ** If you don't see the new users in Office 365 right away, wait a few minutes. ** It can take a little while for changes to go across all the services in Office 365. 
    
## <a name="add-multiple-users-to-office-365-in-the-old-admin-center"></a>Agregar varios usuarios a Office 365 en el centro de administración anterior

1. Descargue [esta hoja de cálculo de muestra](https://www.microsoft.com/download/details.aspx?id=45485) y ábrala en Excel. 
    
    Su hoja de cálculo debe incluir **exactamente los mismos encabezados de columna** que la de ejemplo (Nombre de usuario, Nombre, etc.). Si usa la plantilla, considere la opción de no editar ningún dato de la fila 1 y escribir los datos a partir de la fila 2. 
    
    La hoja de cálculo también debe incluir valores para el nombre de usuario (por ejemplo, alberto@contoso.com) y un nombre para mostrar (por ejemplo, Alberto Hermosilla) para cada usuario. Para dejar otros campos en blanco, escriba un espacio seguido de una coma en el campo, tal y como se muestra en la siguiente ilustración. 
    
    ![Ejemplo de archivo CVS con filas en blanco especificadas](media/9c596ba1-1053-4687-a46c-c9359e9818c9.png)
  
    Si hay usuarios que trabajan en los diferentes países, deberá crear una hoja de cálculo para los usuarios de cada país. Por ejemplo, una hoja en la que se incluyan todos los que trabajan en los Estados Unidos y otra que incluya los que trabajan en Japón. Esto se debe a que la disponibilidad de los servicios de Office 365 varía según la región. 
    
    **Consejo:** antes de agregar una gran cantidad de usuarios a Office 365, sería conveniente que practicara con esta hoja de cálculo de muestra. Por ejemplo, edite la hoja de cálculo de muestra con datos de varios de sus usuarios (unos 5 o 10) y guarde el archivo con un nombre nuevo. Siga los pasos descritos en este procedimiento, compruebe los resultados, elimine las cuentas nuevas y vuelva a empezar. De este modo puede practicar obteniendo todos los datos adecuados para su caso. Consulte también [Consejos para aplicar formato a la hoja de cálculo](add-several-users-at-the-same-time.md#__toc314595848).
    
2. Inicie sesión en Office 365 con su cuenta profesional o educativa. 
    
3. Vaya al centro de administración.
    
4. For people to use Office 365 services, they need to be assigned a license. Before continuing, you might want to check that you have enough licenses for everyone listed in your spreadsheet. Choose **Billing** \> **Subscriptions** to see if you have enough. If you need to buy more licenses, choose ** Change license quantity **. Or, you can run the wizard and assign the licenses you have, then buy more licenses later and rerun the wizard. 
    
5. Ahora, vaya al asistente para agregar usuarios en bloque: elija **Usuarios** \> **Usuarios activos**. Elija ![Icono para agregar muchos usuarios a Office 365](media/3481ffea-d552-4a7f-9a3b-014504e69746.png), tal como se muestra en la siguiente ilustración. 
    
    ![Una imagen de la sección usuarios del centro de administración](media/2cd5ff86-9c0b-438e-9bb9-13b12a2675de.png)
  
    El asistente para agregar usuarios en bloque aparecerá y le mostrará paso a paso el proceso para agregar un grupo de usuarios a Office 365. 
    
6. En el paso 1: seleccionar un archivo CSV, especifique su propia hoja de cálculo, como se muestra en la siguiente ilustración.
    
    ![Paso 1 del asistente para Agregar usuarios en masa - Seleccionar archivo CSV](media/aeb837ed-1f86-427d-b038-c643c383829c.png)
  
7. En el paso 2: verificación, el asistente le indica si el contenido de la hoja de cálculo tiene el formato correcto.
    
    ![Paso 2 del asistente para Agregar usuarios en masa - Verificación](media/3fd3cd2c-44d4-4593-b02c-b87c176affb3.png)
  
8. En el paso 3: configuración, elija **Permitido** para que los usuarios incluidos en la hoja de cálculo puedan usar Office 365. Seleccione también el país o la región en la que los usuarios usarán Office 365. Recuerde si hay personas en la organización que vayan a usar Office 365 en un país diferente, cree una hoja de cálculo separada con sus nombres y vuelva a ejecutar el asistente para agregar usuarios en bloque para agregarlos. 
    
    ![Paso 3 del asistente para Agregar usuarios en masa - Configuración](media/ff12ad34-5d8b-4e89-a02f-d827a94095b3.png)
  
9. La página de asignación de licencias indica las licencias que hay disponibles. 
    
    ![Paso 4 del asistente para Agregar usuarios en masa: licencias](media/161ea34c-c67e-43be-962f-029f5426ff1b.png)
  
    Puede elegir **comprar más licencias**, pero dejará el Asistente para agregar usuarios en masa e irá a **facturación** en el centro de administración de Microsoft 365. Después de comprar más licencias, tendrá que esperar unos minutos para que se procese el pedido y, a continuación, inicie el asistente para Agregar usuarios en masa desde el principio. 
    
    Si no compra más licencias, no se crearán cuentas para todos los usuarios incluidos en la hoja de cálculo. 
    
    En este ejemplo, no compramos más licencias y continuamos con el asistente para agregar en bloque.
    
10. En el paso 5: enviar resultados, escriba las direcciones de correo electrónico de los usuarios que desee que reciban un mensaje de correo electrónico que enumere  *todos*  los nombres de usuario y las contraseñas temporales de Office 365 de las personas incluidas en la hoja de cálculo. 
    
    ![Paso 5 del asistente para Agregar usuarios en masa: enviar resultados](media/5beeb825-4ba7-4ae0-bfb5-a1f8a785ebdb.png)
  
    Se envía el siguiente mensaje de correo electrónico a todas las direcciones de correo electrónico que ha especificado en el paso 5 Enviar resultados. Este mensaje de correo electrónico indica qué cuentas se crearon. Tenga en cuenta que no se crearon cuentas para algunos usuarios debido a que no había licencias suficientes. 
    
    ![Correo electrónico de ejemplo con información de credenciales de usuario](media/0a40c612-2078-4b5b-813e-f99bc53635a6.png)
  
    Más adelante, puede agregar más licencias y volver a ejecutar el asistente para agregar usuarios en bloque con la misma hoja de cálculo. El asistente omitirá los usuarios que ya tengan cuentas. En el informe de resultados aparecerá "nombre de usuario duplicado" para indicar que la persona son esa información ya tiene una cuenta.
    
11. La página final del asistente para agregar usuarios en bloque enumera los nombres de usuario y las contraseñas temporales, tal como se muestra en la siguiente ilustración.
    
    ![Paso 6 del asistente para Agregar usuarios en masa: enviar resultados](media/0cd43832-071b-4b33-b57a-5d07959985ad.png)
  
12. Una vez haya agregado los usuarios a Office 365, debe comunicarles su información de cuenta de Office 365. Use el proceso habitual para comunicar nuevas contraseñas.
    

