---
title: 'Agregar varios usuarios al mismo tiempo a Office 365: ayuda para administradores'
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.date: 6/29/2018
ms.audience: Admin
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
description: 'Obtenga información sobre cómo agregar varios usuarios a Office 365 para profesionales de una lista en una hoja de cálculo o de otro CSV con formato de archivo. Vea un vídeo de YouTube que se explica cómo agregar cuentas a Office 365. Al final de este proceso, cada usuario con una cuenta tendrá un buzón de Office 365. '
ms.openlocfilehash: 1f91821ee552b59201ca01bdbce7edc0406929d6
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542749"
---
# <a name="add-several-users-at-the-same-time-to-office-365---admin-help"></a>Agregar varios usuarios al mismo tiempo a Office 365: ayuda para administradores

Cada persona en su equipo necesita una cuenta de usuario antes de que pueden iniciar sesión y tener acceso a servicios de Office 365, como correo electrónico y Office. Si tiene una gran cantidad de personas, puede agregar sus cuentas a la vez desde una hoja de cálculo de Excel u otro archivo que se guardó en formato CSV. [Es no está seguro de qué formato CSV?](add-several-users-at-the-same-time.md#__toc316652088)
  
## <a name="add-multiple-users-to-office-365-in-the-office-365-admin-center"></a>Agregar varios usuarios a Office 365 en el centro de administración de Office 365

1. Inicie sesión en Office 365 con su cuenta profesional o educativa. 
    
2. En el centro de administración de Office 365, elija **usuarios** \> **usuarios activos**.
    
    ![En el centro de administración, elija los usuarios y, a continuación, activa](media/12086d98-a8b4-4c48-89cf-b78ad8058ff1.png)
  
3. En el desplegable **más** , elija **importar varios usuarios**.
    
4. En el panel **importar varios usuarios** , opcionalmente, puede descargar un archivo CSV de ejemplo con o sin datos de ejemplo rellenados. 
    
    ![En el desplegable más, elija importar varios usuarios](media/77df8a4a-fd00-4fbe-bf1c-d234fc1d5e93.png)
  
    La hoja de cálculo debe incluir los **mismos encabezados de columna exacta** como el ejemplo uno (nombre de usuario, nombre, etcetera...). Si usa la plantilla, abra en una herramienta de edición de texto, como el Bloc de notas y considere la posibilidad de dejar todos los datos en la fila 1 por sí solo y sólo introducir datos en las filas 2 y a continuación. 
    
    La hoja de cálculo también debe incluir los valores para el nombre de usuario (por ejemplo, bob@contoso.com) y un nombre para mostrar (por ejemplo, Bob Kelly) para cada usuario. 
    
  ```
  User Name,First Name,Last Name,Display Name,Job Title,Department,Office Number,Office Phone,Mobile Phone,Fax,Address,City,State or Province,ZIP or Postal Code,Country or Region
  chris@contoso.com,Chris,Green,Chris Green,IT Manager,Information Technology,123451,123-555-1211,123-555-6641,123-555-9821,1 Microsoft way,Redmond,Wa,98052,United States
  ben@contoso.com,Ben,Andrews,Ben Andrews,IT Manager,Information Technology,123452,123-555-1212,123-555-6642,123-555-9822,1 Microsoft way,Redmond,Wa,98052,United States
  david@contoso.com,David,Longmuir,David Longmuir,IT Manager,Information Technology,123453,123-555-1213,123-555-6643,123-555-9823,1 Microsoft way,Redmond,Wa,98052,United States
  cynthia@contoso.com,Cynthia,Carey,Cynthia Carey,IT Manager,Information Technology,123454,123-555-1214,123-555-6644,123-555-9824,1 Microsoft way,Redmond,Wa,98052,United States
  melissa@contoso.com,Melissa,MacBeth,Melissa MacBeth,IT Manager,Information Technology,123455,123-555-1215,123-555-6645,123-555-9825,1 Microsoft way,Redmond,Wa,98052,United States
  
  ```

5. Escriba una ruta de acceso de archivo en el cuadro o elija **Examinar** para vaya a la ubicación del archivo CSV, a continuación, elija **Comprobar**.
    
    ![Se comprueba el archivo CSV](media/a43d49db-b2ab-4200-8ddf-0bc846ac6fe5.png)
  
    Si hay problemas con el archivo, el problema se muestra en el panel. También puede descargar un archivo de registro.
    
6. En el cuadro de diálogo **establecer las opciones de usuario** puede establecer el estado de inicio de sesión y elija la licencia del producto que se asignará a todos los usuarios. 
    
7. En el cuadro de diálogo **ver su resultado** puede elegir enviar los resultados a usted u otros usuarios (contraseñas estará en texto sin formato) y puede ver cuántos usuarios se han creado, y si es necesario adquirir más licencias para asignar a algunos de los nuevos usuarios. 
    
## <a name="watch-the-video"></a>Vea el vídeo
<a name="bk_preview"> </a>

 Vea un breve vídeo que muestra cómo masiva de agregar usuarios. 
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/f4e7f161-8ae6-4264-a429-9297b539a8de?autoplay=false]
  
## <a name="next-steps"></a>Pasos siguientes
<a name="bk_preview"> </a>

- Ahora que estas personas tienen cuentas, deben [descargar e instalar o volver a instalar Office 365 o 2016 de Office en un PC o Mac](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658). Cada persona en su equipo puede instalar Office 365 en hasta 5 equipos o Mac. 
    
- Cada persona también puede [configurar las aplicaciones de Office y correo electrónico en un dispositivo móvil](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f) en 5 teléfonos, por ejemplo, iPhone, iPad y teléfonos Android y tabletas y tabletas hasta 5. De este modo pueden editar los archivos de Office desde cualquier lugar. 
    
    Para obtener una lista de los pasos del programa de instalación-to-end, vea [configurar Office 365 para la empresa](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) . 
    
## <a name="more-information-about-how-to-add-users-to-office-365"></a>Para obtener más información acerca de cómo agregar usuarios a Office 365
<a name="bk_preview"> </a>

### <a name="not-sure-what-csv-format-is"></a>¿No está seguro de qué formato CSV es?
<a name="__toc316652088"> </a>

Un archivo CSV es un archivo con valores separados por comas. Puede crear o editar un archivo similar con cualquier editor de texto o un programa de hoja de cálculo, como Excel.
  
Puede descargar [esta hoja de cálculo de ejemplo](https://www.microsoft.com/en-us/download/details.aspx?id=45485) como punto de partida. Recuerde que Office 365 requiere los encabezados de columna en la primera fila por lo que no reemplazarlos con otra cosa. 
  
Guarde el archivo con un nombre nuevo y especificar el formato CSV.
  
![Una imagen de cómo guardar un archivo de Excel en formato CSV](media/35a86ebe-63ab-4b4d-9a92-e177de33ebae.png)
  
Cuando guarde el archivo, probablemente obtendrá un símbolo del sistema que algunas características del libro se perderán si guarda el archivo en formato CSV. Esto es correcto. Haga clic en **Sí** para continuar. 
  
![Una imagen del símbolo del sistema que se obtenga de Excel que le pregunta si realmente desea guardar el archivo como un formato CSV](media/51032a81-690c-45ef-bfc5-09ea7f790e98.png)
  
### <a name="tips-for-formatting-your-spreadsheet"></a>Sugerencias para dar formato a la hoja de cálculo
<a name="__toc314595848"> </a>

- **necesito los mismos encabezados de columna como se muestra en la hoja de cálculo de ejemplo?** Sí. La hoja de cálculo de ejemplo contiene los encabezados de columna en la primera fila. Estos títulos son necesarios. Para cada usuario que desee agregar a Office 365, cree una fila bajo el encabezado. Si agregar, cambiar o eliminar cualquiera de los encabezados de columna, es posible que Office 365 no pueda crear los usuarios de la información en el archivo. 
    
- **¿Qué ocurre si no tiene toda la información necesaria para cada usuario?** El nombre de usuario y el nombre para mostrar son necesarios, y no se puede agregar un nuevo usuario sin esta información. Si no dispone de parte de la información, como el fax, puede usar un espacio además una coma para indicar que el campo debe permanecer en blanco. 
    
- ¿** Cómo pequeños o grandes puede ser la hoja de cálculo? ** La hoja de cálculo debe tener al menos dos filas. Uno es para los encabezados de columna (la etiqueta de columna de datos de usuario) y otra para el usuario. No puede tener más de 251 filas. Si necesita importar más de 250 usuarios, puede crear más de una hoja de cálculo. 
    
- ** ¿Qué idiomas puedo usar? ** Cuando se crea la hoja de cálculo, puede escribir los rótulos de columna de datos de usuario en cualquier idioma o caracteres, pero no debe cambiar el orden de las etiquetas, tal como se muestra en el ejemplo. A continuación, puede realizar las entradas en los campos con cualquier lenguaje o caracteres y guarde el archivo en formato Unicode o UTF-8. 
    
- **¿Qué sucede si estoy agregando los usuarios de diferentes países o regiones?** Crear una hoja de cálculo independiente para cada área. Necesitará paso a paso a través de la mayor parte Asistente para agregar usuarios que cada hoja de cálculo, proporcionar una única ubicación de todos los usuarios incluidos en el archivo que está trabajando. 
    
- **Hay un límite para el número de caracteres que puedo usar?** La siguiente tabla muestran los rótulos de columna de datos de usuario y la longitud máxima de caracteres para cada uno en la hoja de cálculo de ejemplo. 
    
|**Etiqueta de columna de datos de usuario**|**Longitud máxima de caracteres**|
|:-----|:-----|
|Nombre de usuario (obligatorio)  <br/> |79 incluido el signo de arroba (@), con el formato name@domain. \<extensión\>. El alias del usuario no puede superar los 30 caracteres y el nombre de dominio no puede superar los 48 caracteres.  <br/> |
|Nombre  <br/> |64  <br/> |
|Apellidos  <br/> |64  <br/> |
|Nombre para mostrar (requerido)  <br/> |256  <br/> |
|Puesto  <br/> |64  <br/> |
|Departamento  <br/> |64  <br/> |
|Número de la oficina  <br/> |128  <br/> |
|Teléfono de la oficina  <br/> |64  <br/> |
|Teléfono móvil  <br/> |64  <br/> |
|Fax  <br/> |64  <br/> |
|Dirección  <br/> |1023  <br/> |
|Ciudad  <br/> |128  <br/> |
|Estado o provincia  <br/> |128  <br/> |
|Código Postal  <br/> |40  <br/> |
|País o región  <br/> |128  <br/> |
   
### <a name="still-having-problems-when-adding-users-to-office-365"></a>¿Sigue teniendo problemas al agregar usuarios a Office 365?

- **Vuelva a comprobar que la hoja de cálculo tiene el formato correcto.** Compruebe los encabezados de columna para asegurarse de que coinciden con los títulos en el archivo de ejemplo. Asegúrese de que está siguiendo las reglas para longitudes de caracteres y que cada campo viene separada por una coma. 
    
- ** Si no ve inmediatamente los nuevos usuarios de Office 365, espere unos minutos. ** Puede tardar un poco mientras para que los cambios ir a través de todos los servicios de Office 365. 
    
## <a name="add-multiple-users-to-office-365-in-the-old-office-365-admin-center"></a>Agregar varios usuarios a Office 365 en el centro de administración de Office 365 antiguo

1. Descargue [esta hoja de cálculo de ejemplo](https://www.microsoft.com/en-us/download/details.aspx?id=45485) y abrirlo en Excel. 
    
    La hoja de cálculo debe incluir los **mismos encabezados de columna exacta** como el ejemplo uno (nombre de usuario, nombre, etcetera...). Si usa la plantilla, considere la posibilidad de dejar todos los datos en la fila 1 por sí solo y sólo introducir datos en las filas 2 y a continuación. 
    
    La hoja de cálculo también debe incluir los valores para el nombre de usuario (por ejemplo, bob@contoso.com) y un nombre para mostrar (por ejemplo, Bob Kelly) para cada usuario. Para dejar el resto de los campos en blanco, escriba un espacio además una coma en el campo, tal como se muestra en la ilustración siguiente. 
    
    ![Un archivo de Currículos de ejemplo que tiene filas en blanco especificado](media/9c596ba1-1053-4687-a46c-c9359e9818c9.png)
  
    Si dispone de personas que trabajan en distintos países, debe crear una hoja de cálculo para los usuarios en cada país. Por ejemplo, una hoja de cálculo que se enumera todas las personas que funciona en los Estados Unidos y otro que enumera todas las personas que funciona en Japón. Esto es debido a que la disponibilidad de servicios de Office 365 varía según la región. 
    
    **Sugerencia:** Antes de agregar muchos usuarios a Office 365, es posible que desee práctica con la hoja de cálculo de ejemplo. Por ejemplo, editar la hoja de cálculo de ejemplo con datos para algunos de los usuarios, diga 5 o 10 y guarde el archivo con un nombre nuevo. Ejecutar a través de los pasos descritos en este procedimiento, compruebe los resultados y, a continuación, eliminar las nuevas cuentas y comenzar de nuevo. De este modo puede practicar la todos los de la derecha de datos obtención de para su situación. Desproteger también [sugerencias para dar formato a la hoja de cálculo](add-several-users-at-the-same-time.md#__toc314595848).
    
2. Inicie sesión en Office 365 con su cuenta profesional o educativa. 
    
3. Vaya al Centro de administración de Office 365.
    
4. Para que las personas a usar servicios de Office 365, deben asignarse una licencia. Antes de continuar, es posible que desee comprobar que dispone de suficientes licencias para todos los usuarios que aparecen en la hoja de cálculo. Elija la **facturación** \> **suscripciones** para ver si dispone de suficiente. Si necesita comprar más licencias, elija ** Cambiar la cantidad de licencias **. O bien, puede ejecutar al asistente y asignar las licencias que tiene, a continuación, compra más licencias más adelante y vuelva a ejecutar al Asistente para. 
    
5. Ahora vaya a la mayor parte Asistente para agregar usuarios: elija **usuarios** \> **Usuarios activos**. Elija ![el icono de adición de muchos usuarios a Office 365](media/3481ffea-d552-4a7f-9a3b-014504e69746.png) tal como se muestra en la ilustración siguiente. 
    
    ![Una imagen de la sección usuarios del centro de administración de Office 365](media/2cd5ff86-9c0b-438e-9bb9-13b12a2675de.png)
  
    La mayor parte agregar usuarios asistente aparecerá y le guiará en el proceso de adición de un grupo de usuarios a Office 365. 
    
6. En el paso 1: seleccione un archivo CSV, especifique su propia hoja de cálculo tal como se muestra en la ilustración siguiente.
    
    ![Paso 1 de la mayor parte Asistente para agregar usuarios - archivo CSV Select](media/aeb837ed-1f86-427d-b038-c643c383829c.png)
  
7. En el paso 2: comprobación, el asistente le indica si el contenido de la hoja de cálculo tiene el formato correcto.
    
    ![Paso 2 de la mayor parte Asistente para agregar usuarios - comprobación](media/3fd3cd2c-44d4-4593-b02c-b87c176affb3.png)
  
8. En el paso 3: configuración, elija **permitido** para que las personas que aparecen en la hoja de cálculo puedan usar Office 365. Elija también el país en el que estas personas a usar Office 365. Recuerde que si algunas personas de la organización va a usar Office 365 en un país diferente, cree una hoja de cálculo independiente con sus nombres y la mayor parte de ejecutar Asistente para agregar usuarios a que vuelva a agregarlos. 
    
    ![Paso 3 de la mayor parte Asistente para agregar usuarios - configuración](media/ff12ad34-5d8b-4e89-a02f-d827a94095b3.png)
  
9. La página asignar licencias indica cuántas licencias están disponibles. 
    
    ![Paso 4 del Asistente para agregar usuarios de forma masiva - licencias](media/161ea34c-c67e-43be-962f-029f5426ff1b.png)
  
    Puede elegir **comprar más licencias**, pero deje la mayor parte Asistente para agregar usuarios y vaya a la **facturación** en el centro de administración de Office 365. Después de comprar más licencias, tendrá que esperar unos minutos para el orden que va a procesar y, a continuación, la mayor parte de inicio Asistente para agregar usuarios desde el principio. 
    
    Si no comprar más licencias, no se creará cuentas para todos los usuarios que aparecen en la hoja de cálculo. 
    
    En este ejemplo, no comprar más licencias de prueba y continuar con la mayor parte Asistente para agregar usuarios.
    
10. En el paso 5: los resultados se envían, escriba las direcciones de correo electrónico de las personas que desean obtener un correo electrónico que se enumera *todos los* de los nombres de usuario de Office 365 y contraseñas temporales para las personas de la hoja de cálculo. 
    
    ![Paso 5 de la mayor parte Asistente para agregar usuarios - enviar resultados](media/5beeb825-4ba7-4ae0-bfb5-a1f8a785ebdb.png)
  
    El correo electrónico siguiente se envía a todas las direcciones de correo electrónico que se especificó en el paso 5 - enviar resultados. Este correo electrónico indica las cuentas que se crearon. Tenga en cuenta que no se han creado cuentas para algunas personas porque no hay suficientes licencias. 
    
    ![Un correo electrónico de ejemplo con información de credenciales de usuario](media/0a40c612-2078-4b5b-813e-f99bc53635a6.png)
  
    Puede comprar más licencias más adelante y agregar la mayor parte de volver a ejecutar el Asistente para usuarios con la misma hoja de cálculo. El asistente omite los usuarios que ya tienen cuentas; en el informe de resultados, dirá "nombre de usuario duplicado" para indicar a alguien con esa información ya tiene una cuenta.
    
11. La página final de la forma masiva agregar Asistente para los usuarios enumera los nombres de usuario y contraseñas temporales, tal como se muestra en la ilustración siguiente.
    
    ![Paso 6 de la mayor parte Asistente para agregar usuarios - enviar resultados](media/0cd43832-071b-4b33-b57a-5d07959985ad.png)
  
12. Una vez que haya agregado a los usuarios a Office 365, es necesario indicar a ellos acerca de la información de su cuenta de Office 365. Usar el proceso normal para comunicar las nuevas contraseñas.
    

