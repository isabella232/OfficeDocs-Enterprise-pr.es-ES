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
# <a name="add-several-users-at-the-same-time-to-office-365---admin-help"></a><span data-ttu-id="7af9b-105">Agregar varios usuarios al mismo tiempo a Office 365: ayuda para administradores</span><span class="sxs-lookup"><span data-stu-id="7af9b-105">Add several users at the same time to Office 365 - Admin Help</span></span>

<span data-ttu-id="7af9b-p102">Cada persona en su equipo necesita una cuenta de usuario antes de que pueden iniciar sesión y tener acceso a servicios de Office 365, como correo electrónico y Office. Si tiene una gran cantidad de personas, puede agregar sus cuentas a la vez desde una hoja de cálculo de Excel u otro archivo que se guardó en formato CSV. [Es no está seguro de qué formato CSV?](add-several-users-at-the-same-time.md#__toc316652088)</span><span class="sxs-lookup"><span data-stu-id="7af9b-p102">Each person on your team needs a user account before they can sign in and access Office 365 services, such as email and Office. If you have a lot of people, you can add their accounts all at once from an Excel spreadsheet or other file saved in CSV format. [Not sure what CSV format is?](add-several-users-at-the-same-time.md#__toc316652088)</span></span>
  
## <a name="add-multiple-users-to-office-365-in-the-office-365-admin-center"></a><span data-ttu-id="7af9b-109">Agregar varios usuarios a Office 365 en el centro de administración de Office 365</span><span class="sxs-lookup"><span data-stu-id="7af9b-109">Add multiple users to Office 365 in the Office 365 admin center</span></span>

1. <span data-ttu-id="7af9b-110">Inicie sesión en Office 365 con su cuenta profesional o educativa.</span><span class="sxs-lookup"><span data-stu-id="7af9b-110">Sign in to Office 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="7af9b-111">En el centro de administración de Office 365, elija **usuarios** \> **usuarios activos**.</span><span class="sxs-lookup"><span data-stu-id="7af9b-111">In the Office 365 admin center, choose **Users** \> **Active users**.</span></span>
    
    ![En el centro de administración, elija los usuarios y, a continuación, activa](media/12086d98-a8b4-4c48-89cf-b78ad8058ff1.png)
  
3. <span data-ttu-id="7af9b-113">En el desplegable **más** , elija **importar varios usuarios**.</span><span class="sxs-lookup"><span data-stu-id="7af9b-113">In the **More** drop-down, choose **Import multiple users**.</span></span>
    
4. <span data-ttu-id="7af9b-114">En el panel **importar varios usuarios** , opcionalmente, puede descargar un archivo CSV de ejemplo con o sin datos de ejemplo rellenados.</span><span class="sxs-lookup"><span data-stu-id="7af9b-114">On the **Import multiple users** panel, you can optionally download a sample CSV file with or without sample data filled in.</span></span> 
    
    ![En el desplegable más, elija importar varios usuarios](media/77df8a4a-fd00-4fbe-bf1c-d234fc1d5e93.png)
  
    <span data-ttu-id="7af9b-116">La hoja de cálculo debe incluir los **mismos encabezados de columna exacta** como el ejemplo uno (nombre de usuario, nombre, etcetera...). Si usa la plantilla, abra en una herramienta de edición de texto, como el Bloc de notas y considere la posibilidad de dejar todos los datos en la fila 1 por sí solo y sólo introducir datos en las filas 2 y a continuación.</span><span class="sxs-lookup"><span data-stu-id="7af9b-116">Your spreadsheet needs to include the **exact same column headings** as the sample one (User Name, First Name, etc...). If you use the template, open it in a text editing tool, like Notepad, and consider leaving all the data in row 1 alone, and only entering data in rows 2 and below.</span></span> 
    
    <span data-ttu-id="7af9b-117">La hoja de cálculo también debe incluir los valores para el nombre de usuario (por ejemplo, bob@contoso.com) y un nombre para mostrar (por ejemplo, Bob Kelly) para cada usuario.</span><span class="sxs-lookup"><span data-stu-id="7af9b-117">Your spreadsheet also needs to include values for the user name (like bob@contoso.com) and a display name (like Bob Kelly) for each user.</span></span> 
    
  ```
  User Name,First Name,Last Name,Display Name,Job Title,Department,Office Number,Office Phone,Mobile Phone,Fax,Address,City,State or Province,ZIP or Postal Code,Country or Region
  chris@contoso.com,Chris,Green,Chris Green,IT Manager,Information Technology,123451,123-555-1211,123-555-6641,123-555-9821,1 Microsoft way,Redmond,Wa,98052,United States
  ben@contoso.com,Ben,Andrews,Ben Andrews,IT Manager,Information Technology,123452,123-555-1212,123-555-6642,123-555-9822,1 Microsoft way,Redmond,Wa,98052,United States
  david@contoso.com,David,Longmuir,David Longmuir,IT Manager,Information Technology,123453,123-555-1213,123-555-6643,123-555-9823,1 Microsoft way,Redmond,Wa,98052,United States
  cynthia@contoso.com,Cynthia,Carey,Cynthia Carey,IT Manager,Information Technology,123454,123-555-1214,123-555-6644,123-555-9824,1 Microsoft way,Redmond,Wa,98052,United States
  melissa@contoso.com,Melissa,MacBeth,Melissa MacBeth,IT Manager,Information Technology,123455,123-555-1215,123-555-6645,123-555-9825,1 Microsoft way,Redmond,Wa,98052,United States
  
  ```

5. <span data-ttu-id="7af9b-118">Escriba una ruta de acceso de archivo en el cuadro o elija **Examinar** para vaya a la ubicación del archivo CSV, a continuación, elija **Comprobar**.</span><span class="sxs-lookup"><span data-stu-id="7af9b-118">Enter a file path into the box, or choose **Browse** to browse to the CSV file location, then choose **Verify**.</span></span>
    
    ![Se comprueba el archivo CSV](media/a43d49db-b2ab-4200-8ddf-0bc846ac6fe5.png)
  
    <span data-ttu-id="7af9b-p103">Si hay problemas con el archivo, el problema se muestra en el panel. También puede descargar un archivo de registro.</span><span class="sxs-lookup"><span data-stu-id="7af9b-p103">If there are problems with the file, the problem is displayed in the panel. You can also download a log file.</span></span>
    
6. <span data-ttu-id="7af9b-122">En el cuadro de diálogo **establecer las opciones de usuario** puede establecer el estado de inicio de sesión y elija la licencia del producto que se asignará a todos los usuarios.</span><span class="sxs-lookup"><span data-stu-id="7af9b-122">On the **Set user options** dialog you can set the sign-in status and choose the product license that will be assigned to all users.</span></span> 
    
7. <span data-ttu-id="7af9b-123">En el cuadro de diálogo **ver su resultado** puede elegir enviar los resultados a usted u otros usuarios (contraseñas estará en texto sin formato) y puede ver cuántos usuarios se han creado, y si es necesario adquirir más licencias para asignar a algunos de los nuevos usuarios.</span><span class="sxs-lookup"><span data-stu-id="7af9b-123">On the **View your result** dialog you can choose to send the results to either yourself or other users (passwords will be in plain text) and you can see how many users were created, and if you need to purchase more licenses to assign to some of the new users.</span></span> 
    
## <a name="watch-the-video"></a><span data-ttu-id="7af9b-124">Vea el vídeo</span><span class="sxs-lookup"><span data-stu-id="7af9b-124">Watch the video</span></span>
<span data-ttu-id="7af9b-125"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="7af9b-125"></span></span>

 <span data-ttu-id="7af9b-126">Vea un breve vídeo que muestra cómo masiva de agregar usuarios.</span><span class="sxs-lookup"><span data-stu-id="7af9b-126">Watch a short video that shows you how to bulk add users.</span></span> 
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/f4e7f161-8ae6-4264-a429-9297b539a8de?autoplay=false]
  
## <a name="next-steps"></a><span data-ttu-id="7af9b-127">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="7af9b-127">Next steps</span></span>
<span data-ttu-id="7af9b-128"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="7af9b-128"></span></span>

- <span data-ttu-id="7af9b-p104">Ahora que estas personas tienen cuentas, deben [descargar e instalar o volver a instalar Office 365 o 2016 de Office en un PC o Mac](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658). Cada persona en su equipo puede instalar Office 365 en hasta 5 equipos o Mac.</span><span class="sxs-lookup"><span data-stu-id="7af9b-p104">Now that these people have accounts, they need to [Download and install or reinstall Office 365 or Office 2016 on a PC or Mac](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658). Each person on your team can install Office 365 on up to 5 PCs or Macs.</span></span> 
    
- <span data-ttu-id="7af9b-p105">Cada persona también puede [configurar las aplicaciones de Office y correo electrónico en un dispositivo móvil](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f) en 5 teléfonos, por ejemplo, iPhone, iPad y teléfonos Android y tabletas y tabletas hasta 5. De este modo pueden editar los archivos de Office desde cualquier lugar.</span><span class="sxs-lookup"><span data-stu-id="7af9b-p105">Each person can also [Set up Office apps and email on a mobile device](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f) on up to 5 tablets and 5 phones, such as iPhones, iPads, and Android phones and tablets. This way they can edit Office files from anywhere.</span></span> 
    
    <span data-ttu-id="7af9b-133">Para obtener una lista de los pasos del programa de instalación-to-end, vea [configurar Office 365 para la empresa](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) .</span><span class="sxs-lookup"><span data-stu-id="7af9b-133">See [Set up Office 365 for business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) for an end-to-end list of the setup steps.</span></span> 
    
## <a name="more-information-about-how-to-add-users-to-office-365"></a><span data-ttu-id="7af9b-134">Para obtener más información acerca de cómo agregar usuarios a Office 365</span><span class="sxs-lookup"><span data-stu-id="7af9b-134">More information about how to add users to Office 365</span></span>
<span data-ttu-id="7af9b-135"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="7af9b-135"></span></span>

### <a name="not-sure-what-csv-format-is"></a><span data-ttu-id="7af9b-136">¿No está seguro de qué formato CSV es?</span><span class="sxs-lookup"><span data-stu-id="7af9b-136">Not sure what CSV format is?</span></span>
<span data-ttu-id="7af9b-137"><a name="__toc316652088"> </a></span><span class="sxs-lookup"><span data-stu-id="7af9b-137"></span></span>

<span data-ttu-id="7af9b-p106">Un archivo CSV es un archivo con valores separados por comas. Puede crear o editar un archivo similar con cualquier editor de texto o un programa de hoja de cálculo, como Excel.</span><span class="sxs-lookup"><span data-stu-id="7af9b-p106">A CSV file is a file with comma separated values. You can create or edit a file like this with any text editor or spreadsheet program, such as Excel.</span></span>
  
<span data-ttu-id="7af9b-p107">Puede descargar [esta hoja de cálculo de ejemplo](https://www.microsoft.com/en-us/download/details.aspx?id=45485) como punto de partida. Recuerde que Office 365 requiere los encabezados de columna en la primera fila por lo que no reemplazarlos con otra cosa.</span><span class="sxs-lookup"><span data-stu-id="7af9b-p107">You can download [this sample spreadsheet](https://www.microsoft.com/en-us/download/details.aspx?id=45485) as a starting point. Remember that Office 365 requires column headings in the first row so don't replace them with something else.</span></span> 
  
<span data-ttu-id="7af9b-142">Guarde el archivo con un nombre nuevo y especificar el formato CSV.</span><span class="sxs-lookup"><span data-stu-id="7af9b-142">Save the file with a new name, and specify CSV format.</span></span>
  
![Una imagen de cómo guardar un archivo de Excel en formato CSV](media/35a86ebe-63ab-4b4d-9a92-e177de33ebae.png)
  
<span data-ttu-id="7af9b-p108">Cuando guarde el archivo, probablemente obtendrá un símbolo del sistema que algunas características del libro se perderán si guarda el archivo en formato CSV. Esto es correcto. Haga clic en **Sí** para continuar.</span><span class="sxs-lookup"><span data-stu-id="7af9b-p108">When you save the file, you'll probably get a prompt that some features in your workbook will be lost if you save the file in CSV format. This is okay. Click **Yes** to continue.</span></span> 
  
![Una imagen del símbolo del sistema que se obtenga de Excel que le pregunta si realmente desea guardar el archivo como un formato CSV](media/51032a81-690c-45ef-bfc5-09ea7f790e98.png)
  
### <a name="tips-for-formatting-your-spreadsheet"></a><span data-ttu-id="7af9b-148">Sugerencias para dar formato a la hoja de cálculo</span><span class="sxs-lookup"><span data-stu-id="7af9b-148">Tips for formatting your spreadsheet</span></span>
<span data-ttu-id="7af9b-149"><a name="__toc314595848"> </a></span><span class="sxs-lookup"><span data-stu-id="7af9b-149"></span></span>

- <span data-ttu-id="7af9b-p109">**necesito los mismos encabezados de columna como se muestra en la hoja de cálculo de ejemplo?** Sí. La hoja de cálculo de ejemplo contiene los encabezados de columna en la primera fila. Estos títulos son necesarios. Para cada usuario que desee agregar a Office 365, cree una fila bajo el encabezado. Si agregar, cambiar o eliminar cualquiera de los encabezados de columna, es posible que Office 365 no pueda crear los usuarios de la información en el archivo.</span><span class="sxs-lookup"><span data-stu-id="7af9b-p109">**Do I need the same column headings as in the sample spreadsheet?** Yes. The sample spreadsheet contains column headings in the first row. These headings are required. For each user you want to add to Office 365, create a row under the heading. If you add, change, or delete any of the column headings, Office 365 might not be able to create users from the information in the file.</span></span> 
    
- <span data-ttu-id="7af9b-p110">**¿Qué ocurre si no tiene toda la información necesaria para cada usuario?** El nombre de usuario y el nombre para mostrar son necesarios, y no se puede agregar un nuevo usuario sin esta información. Si no dispone de parte de la información, como el fax, puede usar un espacio además una coma para indicar que el campo debe permanecer en blanco.</span><span class="sxs-lookup"><span data-stu-id="7af9b-p110">**What if I don't have all the information required for each user?** The user name and display name are required, and you cannot add a new user without this information. If you don't have some of the other information, such as the fax, you can use a space plus a comma to indicate that the field should remain blank.</span></span> 
    
- <span data-ttu-id="7af9b-p111">¿** Cómo pequeños o grandes puede ser la hoja de cálculo? ** La hoja de cálculo debe tener al menos dos filas. Uno es para los encabezados de columna (la etiqueta de columna de datos de usuario) y otra para el usuario. No puede tener más de 251 filas. Si necesita importar más de 250 usuarios, puede crear más de una hoja de cálculo.</span><span class="sxs-lookup"><span data-stu-id="7af9b-p111">** How small or large can the spreadsheet be? ** The spreadsheet must have at least two rows. One is for the column headings (the user data column label) and one for the user. You cannot have more than 251 rows. If you need to import more than 250 users, you can create more than one spreadsheet.</span></span> 
    
- <span data-ttu-id="7af9b-p112">** ¿Qué idiomas puedo usar? ** Cuando se crea la hoja de cálculo, puede escribir los rótulos de columna de datos de usuario en cualquier idioma o caracteres, pero no debe cambiar el orden de las etiquetas, tal como se muestra en el ejemplo. A continuación, puede realizar las entradas en los campos con cualquier lenguaje o caracteres y guarde el archivo en formato Unicode o UTF-8.</span><span class="sxs-lookup"><span data-stu-id="7af9b-p112">** What languages can I use? ** When you create your spreadsheet, you can enter user data column labels in any language or characters, but you must not change the order of the labels, as shown in the sample. You can then make entries into the fields, using any language or characters, and save your file in a Unicode or UTF-8 format.</span></span> 
    
- <span data-ttu-id="7af9b-p113">**¿Qué sucede si estoy agregando los usuarios de diferentes países o regiones?** Crear una hoja de cálculo independiente para cada área. Necesitará paso a paso a través de la mayor parte Asistente para agregar usuarios que cada hoja de cálculo, proporcionar una única ubicación de todos los usuarios incluidos en el archivo que está trabajando.</span><span class="sxs-lookup"><span data-stu-id="7af9b-p113">**What if I'm adding users from different countries or regions?** Create a separate spreadsheet for each area. You'll need to step through the Bulk add users wizard which each spreadsheet, giving a single location of all users included in the file that you're working with.</span></span> 
    
- <span data-ttu-id="7af9b-p114">**Hay un límite para el número de caracteres que puedo usar?** La siguiente tabla muestran los rótulos de columna de datos de usuario y la longitud máxima de caracteres para cada uno en la hoja de cálculo de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="7af9b-p114">**Is there a limit to the number of characters I can use?** The following table shows the user data column labels and the maximum character length for each in the sample spreadsheet.</span></span> 
    
|<span data-ttu-id="7af9b-172">**Etiqueta de columna de datos de usuario**</span><span class="sxs-lookup"><span data-stu-id="7af9b-172">**User data column label**</span></span>|<span data-ttu-id="7af9b-173">**Longitud máxima de caracteres**</span><span class="sxs-lookup"><span data-stu-id="7af9b-173">**Maximum character length**</span></span>|
|:-----|:-----|
|<span data-ttu-id="7af9b-174">Nombre de usuario (obligatorio)</span><span class="sxs-lookup"><span data-stu-id="7af9b-174">User Name (Required)</span></span>  <br/> |<span data-ttu-id="7af9b-p115">79 incluido el signo de arroba (@), con el formato name@domain. \<extensión\>. El alias del usuario no puede superar los 30 caracteres y el nombre de dominio no puede superar los 48 caracteres.</span><span class="sxs-lookup"><span data-stu-id="7af9b-p115">79 including the at sign (@), in the format name@domain.\<extension\>. The user's alias cannot exceed 30 characters, and the domain name cannot exceed 48 characters.</span></span>  <br/> |
|<span data-ttu-id="7af9b-177">Nombre</span><span class="sxs-lookup"><span data-stu-id="7af9b-177">First Name</span></span>  <br/> |<span data-ttu-id="7af9b-178">64</span><span class="sxs-lookup"><span data-stu-id="7af9b-178">64</span></span>  <br/> |
|<span data-ttu-id="7af9b-179">Apellidos</span><span class="sxs-lookup"><span data-stu-id="7af9b-179">Last Name</span></span>  <br/> |<span data-ttu-id="7af9b-180">64</span><span class="sxs-lookup"><span data-stu-id="7af9b-180">64</span></span>  <br/> |
|<span data-ttu-id="7af9b-181">Nombre para mostrar (requerido)</span><span class="sxs-lookup"><span data-stu-id="7af9b-181">Display Name (required)</span></span>  <br/> |<span data-ttu-id="7af9b-182">256</span><span class="sxs-lookup"><span data-stu-id="7af9b-182">256</span></span>  <br/> |
|<span data-ttu-id="7af9b-183">Puesto</span><span class="sxs-lookup"><span data-stu-id="7af9b-183">Job Title</span></span>  <br/> |<span data-ttu-id="7af9b-184">64</span><span class="sxs-lookup"><span data-stu-id="7af9b-184">64</span></span>  <br/> |
|<span data-ttu-id="7af9b-185">Departamento</span><span class="sxs-lookup"><span data-stu-id="7af9b-185">Department</span></span>  <br/> |<span data-ttu-id="7af9b-186">64</span><span class="sxs-lookup"><span data-stu-id="7af9b-186">64</span></span>  <br/> |
|<span data-ttu-id="7af9b-187">Número de la oficina</span><span class="sxs-lookup"><span data-stu-id="7af9b-187">Office Number</span></span>  <br/> |<span data-ttu-id="7af9b-188">128</span><span class="sxs-lookup"><span data-stu-id="7af9b-188">128</span></span>  <br/> |
|<span data-ttu-id="7af9b-189">Teléfono de la oficina</span><span class="sxs-lookup"><span data-stu-id="7af9b-189">Office Phone</span></span>  <br/> |<span data-ttu-id="7af9b-190">64</span><span class="sxs-lookup"><span data-stu-id="7af9b-190">64</span></span>  <br/> |
|<span data-ttu-id="7af9b-191">Teléfono móvil</span><span class="sxs-lookup"><span data-stu-id="7af9b-191">Mobile Phone</span></span>  <br/> |<span data-ttu-id="7af9b-192">64</span><span class="sxs-lookup"><span data-stu-id="7af9b-192">64</span></span>  <br/> |
|<span data-ttu-id="7af9b-193">Fax</span><span class="sxs-lookup"><span data-stu-id="7af9b-193">Fax</span></span>  <br/> |<span data-ttu-id="7af9b-194">64</span><span class="sxs-lookup"><span data-stu-id="7af9b-194">64</span></span>  <br/> |
|<span data-ttu-id="7af9b-195">Dirección</span><span class="sxs-lookup"><span data-stu-id="7af9b-195">Address</span></span>  <br/> |<span data-ttu-id="7af9b-196">1023</span><span class="sxs-lookup"><span data-stu-id="7af9b-196">1023</span></span>  <br/> |
|<span data-ttu-id="7af9b-197">Ciudad</span><span class="sxs-lookup"><span data-stu-id="7af9b-197">City</span></span>  <br/> |<span data-ttu-id="7af9b-198">128</span><span class="sxs-lookup"><span data-stu-id="7af9b-198">128</span></span>  <br/> |
|<span data-ttu-id="7af9b-199">Estado o provincia</span><span class="sxs-lookup"><span data-stu-id="7af9b-199">State or Province</span></span>  <br/> |<span data-ttu-id="7af9b-200">128</span><span class="sxs-lookup"><span data-stu-id="7af9b-200">128</span></span>  <br/> |
|<span data-ttu-id="7af9b-201">Código Postal</span><span class="sxs-lookup"><span data-stu-id="7af9b-201">ZIP or Postal Code</span></span>  <br/> |<span data-ttu-id="7af9b-202">40</span><span class="sxs-lookup"><span data-stu-id="7af9b-202">40</span></span>  <br/> |
|<span data-ttu-id="7af9b-203">País o región</span><span class="sxs-lookup"><span data-stu-id="7af9b-203">Country or Region</span></span>  <br/> |<span data-ttu-id="7af9b-204">128</span><span class="sxs-lookup"><span data-stu-id="7af9b-204">128</span></span>  <br/> |
   
### <a name="still-having-problems-when-adding-users-to-office-365"></a><span data-ttu-id="7af9b-205">¿Sigue teniendo problemas al agregar usuarios a Office 365?</span><span class="sxs-lookup"><span data-stu-id="7af9b-205">Still having problems when adding users to Office 365?</span></span>

- <span data-ttu-id="7af9b-p116">**Vuelva a comprobar que la hoja de cálculo tiene el formato correcto.** Compruebe los encabezados de columna para asegurarse de que coinciden con los títulos en el archivo de ejemplo. Asegúrese de que está siguiendo las reglas para longitudes de caracteres y que cada campo viene separada por una coma.</span><span class="sxs-lookup"><span data-stu-id="7af9b-p116">**Double-check that the spreadsheet is formatted correctly.** Check the column headings to make sure they match the headings in the sample file. Make sure you're following the rules for character lengths and that each field is separated by a comma.</span></span> 
    
- <span data-ttu-id="7af9b-p117">** Si no ve inmediatamente los nuevos usuarios de Office 365, espere unos minutos. ** Puede tardar un poco mientras para que los cambios ir a través de todos los servicios de Office 365.</span><span class="sxs-lookup"><span data-stu-id="7af9b-p117">** If you don't see the new users in Office 365 right away, wait a few minutes. ** It can take a little while for changes to go across all the services in Office 365.</span></span> 
    
## <a name="add-multiple-users-to-office-365-in-the-old-office-365-admin-center"></a><span data-ttu-id="7af9b-211">Agregar varios usuarios a Office 365 en el centro de administración de Office 365 antiguo</span><span class="sxs-lookup"><span data-stu-id="7af9b-211">Add multiple users to Office 365 in the old Office 365 admin center</span></span>

1. <span data-ttu-id="7af9b-212">Descargue [esta hoja de cálculo de ejemplo](https://www.microsoft.com/en-us/download/details.aspx?id=45485) y abrirlo en Excel.</span><span class="sxs-lookup"><span data-stu-id="7af9b-212">Download [this sample spreadsheet](https://www.microsoft.com/en-us/download/details.aspx?id=45485) and open it in Excel.</span></span> 
    
    <span data-ttu-id="7af9b-213">La hoja de cálculo debe incluir los **mismos encabezados de columna exacta** como el ejemplo uno (nombre de usuario, nombre, etcetera...). Si usa la plantilla, considere la posibilidad de dejar todos los datos en la fila 1 por sí solo y sólo introducir datos en las filas 2 y a continuación.</span><span class="sxs-lookup"><span data-stu-id="7af9b-213">Your spreadsheet needs to include the **exact same column headings** as the sample one (User Name, First Name, etc...). If you use the template, consider leaving all the data in row 1 alone, and only entering data in rows 2 and below.</span></span> 
    
    <span data-ttu-id="7af9b-p118">La hoja de cálculo también debe incluir los valores para el nombre de usuario (por ejemplo, bob@contoso.com) y un nombre para mostrar (por ejemplo, Bob Kelly) para cada usuario. Para dejar el resto de los campos en blanco, escriba un espacio además una coma en el campo, tal como se muestra en la ilustración siguiente.</span><span class="sxs-lookup"><span data-stu-id="7af9b-p118">Your spreadsheet also needs to include values for the user name (like bob@contoso.com) and a display name (like Bob Kelly) for each user. To leave other fields blank, enter a space plus a comma in the field as shown in the following figure.</span></span> 
    
    ![Un archivo de Currículos de ejemplo que tiene filas en blanco especificado](media/9c596ba1-1053-4687-a46c-c9359e9818c9.png)
  
    <span data-ttu-id="7af9b-p119">Si dispone de personas que trabajan en distintos países, debe crear una hoja de cálculo para los usuarios en cada país. Por ejemplo, una hoja de cálculo que se enumera todas las personas que funciona en los Estados Unidos y otro que enumera todas las personas que funciona en Japón. Esto es debido a que la disponibilidad de servicios de Office 365 varía según la región.</span><span class="sxs-lookup"><span data-stu-id="7af9b-p119">If you have people working in different countries, you'll need to create one spreadsheet for users in each country. For example, one spreadsheet that lists everyone who works in the US, and another that lists everyone who works in Japan. This is because the availability of Office 365 services varies by region.</span></span> 
    
    <span data-ttu-id="7af9b-p120">**Sugerencia:** Antes de agregar muchos usuarios a Office 365, es posible que desee práctica con la hoja de cálculo de ejemplo. Por ejemplo, editar la hoja de cálculo de ejemplo con datos para algunos de los usuarios, diga 5 o 10 y guarde el archivo con un nombre nuevo. Ejecutar a través de los pasos descritos en este procedimiento, compruebe los resultados y, a continuación, eliminar las nuevas cuentas y comenzar de nuevo. De este modo puede practicar la todos los de la derecha de datos obtención de para su situación. Desproteger también [sugerencias para dar formato a la hoja de cálculo](add-several-users-at-the-same-time.md#__toc314595848).</span><span class="sxs-lookup"><span data-stu-id="7af9b-p120">**Tip:** Before you add many users to Office 365, you might want to practice with the sample spreadsheet. For example, edit the sample spreadsheet with data for a few of your users, say 5 or 10, and save the file with a new name. Run through steps described in this procedure, check the results, and then delete the new accounts and start over again. This way you can practice getting all of the data right for your situation. Also check out [Tips for formatting your spreadsheet](add-several-users-at-the-same-time.md#__toc314595848).</span></span>
    
2. <span data-ttu-id="7af9b-225">Inicie sesión en Office 365 con su cuenta profesional o educativa.</span><span class="sxs-lookup"><span data-stu-id="7af9b-225">Sign in to Office 365 with your work or school account.</span></span> 
    
3. <span data-ttu-id="7af9b-226">Vaya al Centro de administración de Office 365.</span><span class="sxs-lookup"><span data-stu-id="7af9b-226">Go to the Office 365 admin center.</span></span>
    
4. <span data-ttu-id="7af9b-p121">Para que las personas a usar servicios de Office 365, deben asignarse una licencia. Antes de continuar, es posible que desee comprobar que dispone de suficientes licencias para todos los usuarios que aparecen en la hoja de cálculo. Elija la **facturación** \> **suscripciones** para ver si dispone de suficiente. Si necesita comprar más licencias, elija ** Cambiar la cantidad de licencias **. O bien, puede ejecutar al asistente y asignar las licencias que tiene, a continuación, compra más licencias más adelante y vuelva a ejecutar al Asistente para.</span><span class="sxs-lookup"><span data-stu-id="7af9b-p121">For people to use Office 365 services, they need to be assigned a license. Before continuing, you might want to check that you have enough licenses for everyone listed in your spreadsheet. Choose **Billing** \> **Subscriptions** to see if you have enough. If you need to buy more licenses, choose ** Change license quantity **. Or, you can run the wizard and assign the licenses you have, then buy more licenses later and rerun the wizard.</span></span> 
    
5. <span data-ttu-id="7af9b-p122">Ahora vaya a la mayor parte Asistente para agregar usuarios: elija **usuarios** \> **Usuarios activos**. Elija ![el icono de adición de muchos usuarios a Office 365](media/3481ffea-d552-4a7f-9a3b-014504e69746.png) tal como se muestra en la ilustración siguiente.</span><span class="sxs-lookup"><span data-stu-id="7af9b-p122">Now go to the Bulk add users wizard: choose **Users** \> **Active Users**. Choose ![The icon for adding many users to Office 365](media/3481ffea-d552-4a7f-9a3b-014504e69746.png) as shown in the following figure.</span></span> 
    
    ![Una imagen de la sección usuarios del centro de administración de Office 365](media/2cd5ff86-9c0b-438e-9bb9-13b12a2675de.png)
  
    <span data-ttu-id="7af9b-235">La mayor parte agregar usuarios asistente aparecerá y le guiará en el proceso de adición de un grupo de usuarios a Office 365.</span><span class="sxs-lookup"><span data-stu-id="7af9b-235">The Bulk add users wizard appears and steps you through adding a group of users to Office 365.</span></span> 
    
6. <span data-ttu-id="7af9b-236">En el paso 1: seleccione un archivo CSV, especifique su propia hoja de cálculo tal como se muestra en la ilustración siguiente.</span><span class="sxs-lookup"><span data-stu-id="7af9b-236">In Step 1 - Select a CSV file, specify your own spreadsheet as shown in the following figure.</span></span>
    
    ![Paso 1 de la mayor parte Asistente para agregar usuarios - archivo CSV Select](media/aeb837ed-1f86-427d-b038-c643c383829c.png)
  
7. <span data-ttu-id="7af9b-238">En el paso 2: comprobación, el asistente le indica si el contenido de la hoja de cálculo tiene el formato correcto.</span><span class="sxs-lookup"><span data-stu-id="7af9b-238">In Step 2 - Verification, the wizard tells you whether the content in the spreadsheet is formatted correctly.</span></span>
    
    ![Paso 2 de la mayor parte Asistente para agregar usuarios - comprobación](media/3fd3cd2c-44d4-4593-b02c-b87c176affb3.png)
  
8. <span data-ttu-id="7af9b-p123">En el paso 3: configuración, elija **permitido** para que las personas que aparecen en la hoja de cálculo puedan usar Office 365. Elija también el país en el que estas personas a usar Office 365. Recuerde que si algunas personas de la organización va a usar Office 365 en un país diferente, cree una hoja de cálculo independiente con sus nombres y la mayor parte de ejecutar Asistente para agregar usuarios a que vuelva a agregarlos.</span><span class="sxs-lookup"><span data-stu-id="7af9b-p123">In Step 3 - Settings, choose **Allowed** so that the people listed in your spreadsheet will be able to use Office 365. Also choose the country in which these people will use Office 365. Remember if some people in your organization are going to use Office 365 in a different country, create a separate spreadsheet with their names and run the Bulk add users wizard again to add them.</span></span> 
    
    ![Paso 3 de la mayor parte Asistente para agregar usuarios - configuración](media/ff12ad34-5d8b-4e89-a02f-d827a94095b3.png)
  
9. <span data-ttu-id="7af9b-244">La página asignar licencias indica cuántas licencias están disponibles.</span><span class="sxs-lookup"><span data-stu-id="7af9b-244">The assign licenses page tells you how many licenses are available.</span></span> 
    
    ![Paso 4 del Asistente para agregar usuarios de forma masiva - licencias](media/161ea34c-c67e-43be-962f-029f5426ff1b.png)
  
    <span data-ttu-id="7af9b-p124">Puede elegir **comprar más licencias**, pero deje la mayor parte Asistente para agregar usuarios y vaya a la **facturación** en el centro de administración de Office 365. Después de comprar más licencias, tendrá que esperar unos minutos para el orden que va a procesar y, a continuación, la mayor parte de inicio Asistente para agregar usuarios desde el principio.</span><span class="sxs-lookup"><span data-stu-id="7af9b-p124">You can choose **Buy more licenses**, but you'll leave the Bulk add users wizard and go to **Billing** in the Office 365 admin center. After buying more licenses, you'll have to wait a few minutes for the order to be processed and then start the Bulk add users wizard from the beginning.</span></span> 
    
    <span data-ttu-id="7af9b-248">Si no comprar más licencias, no se creará cuentas para todos los usuarios que aparecen en la hoja de cálculo.</span><span class="sxs-lookup"><span data-stu-id="7af9b-248">If you don't buy more licenses, accounts won't be created for everyone listed in your spreadsheet.</span></span> 
    
    <span data-ttu-id="7af9b-249">En este ejemplo, no comprar más licencias de prueba y continuar con la mayor parte Asistente para agregar usuarios.</span><span class="sxs-lookup"><span data-stu-id="7af9b-249">In this example, we don't buy any more licenses and continue with the Bulk add users wizard.</span></span>
    
10. <span data-ttu-id="7af9b-250">En el paso 5: los resultados se envían, escriba las direcciones de correo electrónico de las personas que desean obtener un correo electrónico que se enumera *todos los* de los nombres de usuario de Office 365 y contraseñas temporales para las personas de la hoja de cálculo.</span><span class="sxs-lookup"><span data-stu-id="7af9b-250">In Step 5 - Send Results, type the email addresses of the people who you want to get an email that lists  *all*  of the Office 365 user names and temporary passwords for the people in the spreadsheet.</span></span> 
    
    ![Paso 5 de la mayor parte Asistente para agregar usuarios - enviar resultados](media/5beeb825-4ba7-4ae0-bfb5-a1f8a785ebdb.png)
  
    <span data-ttu-id="7af9b-p125">El correo electrónico siguiente se envía a todas las direcciones de correo electrónico que se especificó en el paso 5 - enviar resultados. Este correo electrónico indica las cuentas que se crearon. Tenga en cuenta que no se han creado cuentas para algunas personas porque no hay suficientes licencias.</span><span class="sxs-lookup"><span data-stu-id="7af9b-p125">The following email is sent to all the email addresses you specified in Step 5 - Send results. This email indicates which accounts were created. Notice that accounts weren't created for some people because there weren't enough licenses.</span></span> 
    
    ![Un correo electrónico de ejemplo con información de credenciales de usuario](media/0a40c612-2078-4b5b-813e-f99bc53635a6.png)
  
    <span data-ttu-id="7af9b-p126">Puede comprar más licencias más adelante y agregar la mayor parte de volver a ejecutar el Asistente para usuarios con la misma hoja de cálculo. El asistente omite los usuarios que ya tienen cuentas; en el informe de resultados, dirá "nombre de usuario duplicado" para indicar a alguien con esa información ya tiene una cuenta.</span><span class="sxs-lookup"><span data-stu-id="7af9b-p126">You can buy more licenses later and rerun the Bulk add users wizard with the same spreadsheet. The wizard skips over the users that already have accounts; on the results report, it will say "duplicate user name" to indicate someone with that information already has an account.</span></span>
    
11. <span data-ttu-id="7af9b-258">La página final de la forma masiva agregar Asistente para los usuarios enumera los nombres de usuario y contraseñas temporales, tal como se muestra en la ilustración siguiente.</span><span class="sxs-lookup"><span data-stu-id="7af9b-258">The final page in the Bulk add users wizard lists the user names and temporary passwords, as shown in the following figure.</span></span>
    
    ![Paso 6 de la mayor parte Asistente para agregar usuarios - enviar resultados](media/0cd43832-071b-4b33-b57a-5d07959985ad.png)
  
12. <span data-ttu-id="7af9b-p127">Una vez que haya agregado a los usuarios a Office 365, es necesario indicar a ellos acerca de la información de su cuenta de Office 365. Usar el proceso normal para comunicar las nuevas contraseñas.</span><span class="sxs-lookup"><span data-stu-id="7af9b-p127">After you've added users to Office 365, you need to tell them about their Office 365 account information. Use your normal process for communicating new passwords.</span></span>
    

