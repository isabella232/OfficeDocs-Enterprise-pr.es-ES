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
# <a name="add-several-users-at-the-same-time-to-office-365---admin-help"></a><span data-ttu-id="58294-105">Agregar varios usuarios a Office 365 a la vez. Ayuda para administradores</span><span class="sxs-lookup"><span data-stu-id="58294-105">Add several users at the same time to Office 365 - Admin Help</span></span>

<span data-ttu-id="58294-p102">Todos los usuarios de su grupo deben tener una cuenta de usuario para poder iniciar sesión y acceder a servicios de Office 365, como el correo electrónico y Office. Si son muchas personas, puede agregar sus cuentas de una vez desde una hoja de cálculo de Excel u otro archivo guardado en formato CSV. [¿No tiene claro qué es un archivo CSV?](add-several-users-at-the-same-time.md#__toc316652088)</span><span class="sxs-lookup"><span data-stu-id="58294-p102">Each person on your team needs a user account before they can sign in and access Office 365 services, such as email and Office. If you have a lot of people, you can add their accounts all at once from an Excel spreadsheet or other file saved in CSV format. [Not sure what CSV format is?](add-several-users-at-the-same-time.md#__toc316652088)</span></span>
  
## <a name="add-multiple-users-to-office-365-in-the-microsoft-365-admin-center"></a><span data-ttu-id="58294-109">Agregar varios usuarios a Office 365 en el centro de administración de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="58294-109">Add multiple users to Office 365 in the Microsoft 365 admin center</span></span>

1. <span data-ttu-id="58294-110">Inicie sesión en Office 365 con su cuenta profesional o educativa.</span><span class="sxs-lookup"><span data-stu-id="58294-110">Sign in to Office 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="58294-111">En el centro de administración, **Elija** \> usuarios **activos**.</span><span class="sxs-lookup"><span data-stu-id="58294-111">In the admin center, choose **Users** \> **Active users**.</span></span>
    
    ![En el centro de administración, elija usuarios y, a continuación, usuarios activos](media/12086d98-a8b4-4c48-89cf-b78ad8058ff1.png)
  
    
3. <span data-ttu-id="58294-113">En el panel **Importar varios usuarios**, tiene la opción de descargar un archivo CSV de ejemplo con datos de ejemplo o sin rellenar.</span><span class="sxs-lookup"><span data-stu-id="58294-113">On the **Import multiple users** panel, you can optionally download a sample CSV file with or without sample data filled in.</span></span> 
    
    ![In the More drop-down, choose Import multiple users](media/77df8a4a-fd00-4fbe-bf1c-d234fc1d5e93.png)
  
    <span data-ttu-id="58294-115">Su hoja de cálculo debe incluir **exactamente los mismos encabezados de columna** que la de ejemplo (Nombre de usuario, Nombre, etc.). Si usa la plantilla, ábrala en una herramienta de edición de texto y considere la opción de no editar ningún dato de la fila 1 y escribir los datos a partir de la fila 2.</span><span class="sxs-lookup"><span data-stu-id="58294-115">Your spreadsheet needs to include the **exact same column headings** as the sample one (User Name, First Name, etc...). If you use the template, open it in a text editing tool, like Notepad, and consider leaving all the data in row 1 alone, and only entering data in rows 2 and below.</span></span> 
    
    <span data-ttu-id="58294-116">La hoja de cálculo también debe incluir valores para el nombre de usuario (por ejemplo, alberto@contoso.com) y un nombre para mostrar (por ejemplo, Alberto Hermosilla) para cada usuario.</span><span class="sxs-lookup"><span data-stu-id="58294-116">Your spreadsheet also needs to include values for the user name (like bob@contoso.com) and a display name (like Bob Kelly) for each user.</span></span> 
    
  ```
  User Name,First Name,Last Name,Display Name,Job Title,Department,Office Number,Office Phone,Mobile Phone,Fax,Address,City,State or Province,ZIP or Postal Code,Country or Region
  chris@contoso.com,Chris,Green,Chris Green,IT Manager,Information Technology,123451,123-555-1211,123-555-6641,123-555-9821,1 Microsoft way,Redmond,Wa,98052,United States
  ben@contoso.com,Ben,Andrews,Ben Andrews,IT Manager,Information Technology,123452,123-555-1212,123-555-6642,123-555-9822,1 Microsoft way,Redmond,Wa,98052,United States
  david@contoso.com,David,Longmuir,David Longmuir,IT Manager,Information Technology,123453,123-555-1213,123-555-6643,123-555-9823,1 Microsoft way,Redmond,Wa,98052,United States
  cynthia@contoso.com,Cynthia,Carey,Cynthia Carey,IT Manager,Information Technology,123454,123-555-1214,123-555-6644,123-555-9824,1 Microsoft way,Redmond,Wa,98052,United States
  melissa@contoso.com,Melissa,MacBeth,Melissa MacBeth,IT Manager,Information Technology,123455,123-555-1215,123-555-6645,123-555-9825,1 Microsoft way,Redmond,Wa,98052,United States
  
  ```

4. <span data-ttu-id="58294-117">Escriba una ruta de acceso al archivo en el cuadro o elija **Examinar** para ir a la ubicación del archivo CSV y, a continuación, elija **Comprobar**.</span><span class="sxs-lookup"><span data-stu-id="58294-117">Enter a file path into the box, or choose **Browse** to browse to the CSV file location, then choose **Verify**.</span></span>
    
    ![Your CSV file is verified](media/a43d49db-b2ab-4200-8ddf-0bc846ac6fe5.png)
  
    <span data-ttu-id="58294-p103">Si hay problemas con el archivo, se mostrarán en el panel. También puede descargar un archivo de registro.</span><span class="sxs-lookup"><span data-stu-id="58294-p103">If there are problems with the file, the problem is displayed in the panel. You can also download a log file.</span></span>
    
5. <span data-ttu-id="58294-121">En el cuadro de diálogo **Establecer opciones de usuario**, puede establecer el estado de inicio de sesión y elegir qué licencia de producto se asignará a cada uno de los usuarios.</span><span class="sxs-lookup"><span data-stu-id="58294-121">On the **Set user options** dialog you can set the sign-in status and choose the product license that will be assigned to all users.</span></span> 
    
6. <span data-ttu-id="58294-122">En el cuadro de diálogo **Ver el resultado**, puede elegir si desea enviar los resultados a su usuario o a otros usuarios (las contraseñas se mostrarán en texto sin formato). Además, puede ver cuántos usuarios se crearon y, si lo necesita, comprar más licencias para asignárselas a algunos de los nuevos usuarios.</span><span class="sxs-lookup"><span data-stu-id="58294-122">On the **View your result** dialog you can choose to send the results to either yourself or other users (passwords will be in plain text) and you can see how many users were created, and if you need to purchase more licenses to assign to some of the new users.</span></span> 
    
## <a name="watch-the-video"></a><span data-ttu-id="58294-123">Ver vídeo</span><span class="sxs-lookup"><span data-stu-id="58294-123">Watch the video</span></span>
<span data-ttu-id="58294-124"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="58294-124"></span></span>

 <span data-ttu-id="58294-125">Vea un breve vídeo en el que se muestra cómo agregar usuarios en masa.</span><span class="sxs-lookup"><span data-stu-id="58294-125">Watch a short video that shows you how to bulk add users.</span></span> 
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/f4e7f161-8ae6-4264-a429-9297b539a8de?autoplay=false]
  
## <a name="next-steps"></a><span data-ttu-id="58294-126">Siguientes pasos</span><span class="sxs-lookup"><span data-stu-id="58294-126">Next steps</span></span>
<span data-ttu-id="58294-127"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="58294-127"></span></span>

- <span data-ttu-id="58294-128">Ahora que estas personas tienen cuentas, necesitan [Descargar e instalar o reinstalar office 365 u office 2016 en un equipo PC o Mac](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658).</span><span class="sxs-lookup"><span data-stu-id="58294-128">Now that these people have accounts, they need to [Download and install or reinstall Office 365 or Office 2016 on a PC or Mac](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658).</span></span> <span data-ttu-id="58294-129">Cada persona de su equipo puede usar Office 365 en un máximo de 5 equipos o Mac.</span><span class="sxs-lookup"><span data-stu-id="58294-129">Each person on your team can install Office 365 on up to 5 PCs or Macs.</span></span> 
    
- <span data-ttu-id="58294-130">Cada persona también puede [configurar el correo electrónico y las aplicaciones de Office en un dispositivo móvil en un](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f) máximo de 5 tabletas y 5 teléfonos, como iPhone, iPad, y teléfonos y tabletas Android.</span><span class="sxs-lookup"><span data-stu-id="58294-130">Each person can also [Set up Office apps and email on a mobile device](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f) on up to 5 tablets and 5 phones, such as iPhones, iPads, and Android phones and tablets.</span></span> <span data-ttu-id="58294-131">De esta forma, puede editar archivos de Office desde cualquier lugar.</span><span class="sxs-lookup"><span data-stu-id="58294-131">This way they can edit Office files from anywhere.</span></span> 
    
    <span data-ttu-id="58294-132">Vea [set up Office 365 for Business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) para obtener una lista completa de los pasos de configuración.</span><span class="sxs-lookup"><span data-stu-id="58294-132">See [Set up Office 365 for business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) for an end-to-end list of the setup steps.</span></span> 
    
## <a name="more-information-about-how-to-add-users-to-office-365"></a><span data-ttu-id="58294-133">Más información sobre cómo agregar usuarios a Office 365</span><span class="sxs-lookup"><span data-stu-id="58294-133">More information about how to add users to Office 365</span></span>
<span data-ttu-id="58294-134"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="58294-134"></span></span>

### <a name="not-sure-what-csv-format-is"></a><span data-ttu-id="58294-135">¿No tiene claro qué es un archivo CSV?</span><span class="sxs-lookup"><span data-stu-id="58294-135">Not sure what CSV format is?</span></span>
<span data-ttu-id="58294-136"><a name="__toc316652088"> </a></span><span class="sxs-lookup"><span data-stu-id="58294-136"></span></span>

<span data-ttu-id="58294-p106">Un archivo CSV es un archivo con valores separados por comas. Puede crear o editar un archivo como este con cualquier editor de textos o programa de hojas de cálculo, como Excel.</span><span class="sxs-lookup"><span data-stu-id="58294-p106">A CSV file is a file with comma separated values. You can create or edit a file like this with any text editor or spreadsheet program, such as Excel.</span></span>
  
<span data-ttu-id="58294-p107">Puede descargar [esta hoja de cálculo de muestra](https://www.microsoft.com/download/details.aspx?id=45485) como punto de partida. Recuerde que Office 365 requiere encabezados de columna en la primera fila, así que no los sustituya con ningún otro elemento.</span><span class="sxs-lookup"><span data-stu-id="58294-p107">You can download [this sample spreadsheet](https://www.microsoft.com/download/details.aspx?id=45485) as a starting point. Remember that Office 365 requires column headings in the first row so don't replace them with something else.</span></span> 
  
<span data-ttu-id="58294-141">Guarde el archivo con un nuevo nombre y especifique el formato CSV.</span><span class="sxs-lookup"><span data-stu-id="58294-141">Save the file with a new name, and specify CSV format.</span></span>
  
![Imagen de cómo guardar un archivo de Excel en formato CSV](media/35a86ebe-63ab-4b4d-9a92-e177de33ebae.png)
  
<span data-ttu-id="58294-p108">Cuando guarde el archivo, probablemente recibirá un mensaje que le informará de que se perderán algunas características del libro si guarda el archivo en formato CSV. No pasa nada. Haga clic en **Sí** para continuar.</span><span class="sxs-lookup"><span data-stu-id="58294-p108">When you save the file, you'll probably get a prompt that some features in your workbook will be lost if you save the file in CSV format. This is okay. Click **Yes** to continue.</span></span> 
  
![Imagen del mensaje que obtendría en Excel que pregunta si realmente quiere guardar el archivo como formato CSV](media/51032a81-690c-45ef-bfc5-09ea7f790e98.png)
  
### <a name="tips-for-formatting-your-spreadsheet"></a><span data-ttu-id="58294-147">Consejos para aplicar formato a la hoja de cálculo</span><span class="sxs-lookup"><span data-stu-id="58294-147">Tips for formatting your spreadsheet</span></span>
<span data-ttu-id="58294-148"><a name="__toc314595848"> </a></span><span class="sxs-lookup"><span data-stu-id="58294-148"></span></span>

- <span data-ttu-id="58294-p109">**¿Debo mantener los mismos encabezados de columna que en la hoja de cálculo de muestra?** Sí. La hoja de cálculo de muestra contiene los encabezados de columna en la primera fila. Estos encabezados son necesarios. Para cada usuario que desee agregar a Office 365, cree una fila bajo el encabezado. Si agrega, cambia o elimina cualquiera de los encabezados de columna, Office 365 podría no crear usuarios a partir de la información del archivo.</span><span class="sxs-lookup"><span data-stu-id="58294-p109">**Do I need the same column headings as in the sample spreadsheet?** Yes. The sample spreadsheet contains column headings in the first row. These headings are required. For each user you want to add to Office 365, create a row under the heading. If you add, change, or delete any of the column headings, Office 365 might not be able to create users from the information in the file.</span></span> 
    
- <span data-ttu-id="58294-p110">**¿Qué ocurre si no tengo toda la información requerida para cada usuario?** El nombre de usuario y el nombre para mostrar son obligatorios, y no puede agregar un nuevo usuario sin esta información. Si le falta parte de la información, como el fax, puede usar un espacio más una coma para indicar que el campo debe dejarse en blanco.</span><span class="sxs-lookup"><span data-stu-id="58294-p110">**What if I don't have all the information required for each user?** The user name and display name are required, and you cannot add a new user without this information. If you don't have some of the other information, such as the fax, you can use a space plus a comma to indicate that the field should remain blank.</span></span> 
    
- <span data-ttu-id="58294-p111">\*\* How small or large can the spreadsheet be? \*\* The spreadsheet must have at least two rows. One is for the column headings (the user data column label) and one for the user. You cannot have more than 251 rows. If you need to import more than 250 users, you can create more than one spreadsheet.</span><span class="sxs-lookup"><span data-stu-id="58294-p111">\*\* How small or large can the spreadsheet be? \*\* The spreadsheet must have at least two rows. One is for the column headings (the user data column label) and one for the user. You cannot have more than 251 rows. If you need to import more than 250 users, you can create more than one spreadsheet.</span></span> 
    
- <span data-ttu-id="58294-p112">\*\* What languages can I use? \*\* When you create your spreadsheet, you can enter user data column labels in any language or characters, but you must not change the order of the labels, as shown in the sample. You can then make entries into the fields, using any language or characters, and save your file in a Unicode or UTF-8 format.</span><span class="sxs-lookup"><span data-stu-id="58294-p112">\*\* What languages can I use? \*\* When you create your spreadsheet, you can enter user data column labels in any language or characters, but you must not change the order of the labels, as shown in the sample. You can then make entries into the fields, using any language or characters, and save your file in a Unicode or UTF-8 format.</span></span> 
    
- <span data-ttu-id="58294-p113">**¿Qué ocurre si voy a agregar usuarios de diferentes países o regiones?** Cree una hoja de cálculo para cada área. Deberá seguir los pases del asistente para agregar usuarios en bloque para cada una de las hojas de cálculo y dar una única ubicación a todos los usuarios incluidos en el archivo con los que trabaja.</span><span class="sxs-lookup"><span data-stu-id="58294-p113">**What if I'm adding users from different countries or regions?** Create a separate spreadsheet for each area. You'll need to step through the Bulk add users wizard which each spreadsheet, giving a single location of all users included in the file that you're working with.</span></span> 
    
- <span data-ttu-id="58294-p114">**¿Existe algún límite de caracteres que se pueden usar?** En la siguiente tabla se muestran las etiquetas de las columnas de datos de usuario y la longitud máxima (en caracteres) para cada una en la hoja de cálculo de muestra.</span><span class="sxs-lookup"><span data-stu-id="58294-p114">**Is there a limit to the number of characters I can use?** The following table shows the user data column labels and the maximum character length for each in the sample spreadsheet.</span></span> 
    
|<span data-ttu-id="58294-171">**Etiquetas columnas datos usuarios**</span><span class="sxs-lookup"><span data-stu-id="58294-171">**User data column label**</span></span>|<span data-ttu-id="58294-172">**Longitud máxima (en caracteres)**</span><span class="sxs-lookup"><span data-stu-id="58294-172">**Maximum character length**</span></span>|
|:-----|:-----|
|<span data-ttu-id="58294-173">Nombre de usuario (obligatorio)</span><span class="sxs-lookup"><span data-stu-id="58294-173">User Name (Required)</span></span>  <br/> |<span data-ttu-id="58294-p115">79 incluida la arroba (@), en el formato nombre@dominio.\<extensión\>. El alias del usuario no debe superar los 30 caracteres y el nombre de dominio no debe superar los 48 caracteres.</span><span class="sxs-lookup"><span data-stu-id="58294-p115">79 including the at sign (@), in the format name@domain.\<extension\>. The user's alias cannot exceed 30 characters, and the domain name cannot exceed 48 characters.</span></span>  <br/> |
|<span data-ttu-id="58294-176">Nombre</span><span class="sxs-lookup"><span data-stu-id="58294-176">First Name</span></span>  <br/> |<span data-ttu-id="58294-177">64</span><span class="sxs-lookup"><span data-stu-id="58294-177">64</span></span>  <br/> |
|<span data-ttu-id="58294-178">Apellido</span><span class="sxs-lookup"><span data-stu-id="58294-178">Last Name</span></span>  <br/> |<span data-ttu-id="58294-179">64</span><span class="sxs-lookup"><span data-stu-id="58294-179">64</span></span>  <br/> |
|<span data-ttu-id="58294-180">Nombre para mostrar (obligatorio)</span><span class="sxs-lookup"><span data-stu-id="58294-180">Display Name (required)</span></span>  <br/> |<span data-ttu-id="58294-181">256</span><span class="sxs-lookup"><span data-stu-id="58294-181">256</span></span>  <br/> |
|<span data-ttu-id="58294-182">Puesto</span><span class="sxs-lookup"><span data-stu-id="58294-182">Job Title</span></span>  <br/> |<span data-ttu-id="58294-183">64</span><span class="sxs-lookup"><span data-stu-id="58294-183">64</span></span>  <br/> |
|<span data-ttu-id="58294-184">Departamento</span><span class="sxs-lookup"><span data-stu-id="58294-184">Department</span></span>  <br/> |<span data-ttu-id="58294-185">64</span><span class="sxs-lookup"><span data-stu-id="58294-185">64</span></span>  <br/> |
|<span data-ttu-id="58294-186">Número del trabajo</span><span class="sxs-lookup"><span data-stu-id="58294-186">Office Number</span></span>  <br/> |<span data-ttu-id="58294-187">128</span><span class="sxs-lookup"><span data-stu-id="58294-187">128</span></span>  <br/> |
|<span data-ttu-id="58294-188">Teléfono del trabajo</span><span class="sxs-lookup"><span data-stu-id="58294-188">Office Phone</span></span>  <br/> |<span data-ttu-id="58294-189">64</span><span class="sxs-lookup"><span data-stu-id="58294-189">64</span></span>  <br/> |
|<span data-ttu-id="58294-190">Teléfono móvil</span><span class="sxs-lookup"><span data-stu-id="58294-190">Mobile Phone</span></span>  <br/> |<span data-ttu-id="58294-191">64</span><span class="sxs-lookup"><span data-stu-id="58294-191">64</span></span>  <br/> |
|<span data-ttu-id="58294-192">Fax</span><span class="sxs-lookup"><span data-stu-id="58294-192">Fax</span></span>  <br/> |<span data-ttu-id="58294-193">64</span><span class="sxs-lookup"><span data-stu-id="58294-193">64</span></span>  <br/> |
|<span data-ttu-id="58294-194">Dirección</span><span class="sxs-lookup"><span data-stu-id="58294-194">Address</span></span>  <br/> |<span data-ttu-id="58294-195">1023</span><span class="sxs-lookup"><span data-stu-id="58294-195">1023</span></span>  <br/> |
|<span data-ttu-id="58294-196">Ciudad</span><span class="sxs-lookup"><span data-stu-id="58294-196">City</span></span>  <br/> |<span data-ttu-id="58294-197">128</span><span class="sxs-lookup"><span data-stu-id="58294-197">128</span></span>  <br/> |
|<span data-ttu-id="58294-198">Estado o provincia</span><span class="sxs-lookup"><span data-stu-id="58294-198">State or Province</span></span>  <br/> |<span data-ttu-id="58294-199">128</span><span class="sxs-lookup"><span data-stu-id="58294-199">128</span></span>  <br/> |
|<span data-ttu-id="58294-200">Código postal</span><span class="sxs-lookup"><span data-stu-id="58294-200">ZIP or Postal Code</span></span>  <br/> |<span data-ttu-id="58294-201">40</span><span class="sxs-lookup"><span data-stu-id="58294-201">40</span></span>  <br/> |
|<span data-ttu-id="58294-202">País o región</span><span class="sxs-lookup"><span data-stu-id="58294-202">Country or Region</span></span>  <br/> |<span data-ttu-id="58294-203">128</span><span class="sxs-lookup"><span data-stu-id="58294-203">128</span></span>  <br/> |
   
### <a name="still-having-problems-when-adding-users-to-office-365"></a><span data-ttu-id="58294-204">¿Aún tiene problemas al agregar usuarios a Office 365?</span><span class="sxs-lookup"><span data-stu-id="58294-204">Still having problems when adding users to Office 365?</span></span>

- <span data-ttu-id="58294-p116">**Asegúrese una vez más de que el archivo tenga un formato correcto.** Compruebe que los encabezados de las columnas coincidan con los encabezados del archivo de muestra. Asegúrese de haber respetado los límites de longitud y de que los campos estén separados por comas.</span><span class="sxs-lookup"><span data-stu-id="58294-p116">**Double-check that the spreadsheet is formatted correctly.** Check the column headings to make sure they match the headings in the sample file. Make sure you're following the rules for character lengths and that each field is separated by a comma.</span></span> 
    
- <span data-ttu-id="58294-p117">\*\* If you don't see the new users in Office 365 right away, wait a few minutes. \*\* It can take a little while for changes to go across all the services in Office 365.</span><span class="sxs-lookup"><span data-stu-id="58294-p117">\*\* If you don't see the new users in Office 365 right away, wait a few minutes. \*\* It can take a little while for changes to go across all the services in Office 365.</span></span> 
    
## <a name="add-multiple-users-to-office-365-in-the-old-admin-center"></a><span data-ttu-id="58294-210">Agregar varios usuarios a Office 365 en el centro de administración anterior</span><span class="sxs-lookup"><span data-stu-id="58294-210">Add multiple users to Office 365 in the old admin center</span></span>

1. <span data-ttu-id="58294-211">Descargue [esta hoja de cálculo de muestra](https://www.microsoft.com/download/details.aspx?id=45485) y ábrala en Excel.</span><span class="sxs-lookup"><span data-stu-id="58294-211">Download [this sample spreadsheet](https://www.microsoft.com/download/details.aspx?id=45485) and open it in Excel.</span></span> 
    
    <span data-ttu-id="58294-212">Su hoja de cálculo debe incluir **exactamente los mismos encabezados de columna** que la de ejemplo (Nombre de usuario, Nombre, etc.). Si usa la plantilla, considere la opción de no editar ningún dato de la fila 1 y escribir los datos a partir de la fila 2.</span><span class="sxs-lookup"><span data-stu-id="58294-212">Your spreadsheet needs to include the **exact same column headings** as the sample one (User Name, First Name, etc...). If you use the template, consider leaving all the data in row 1 alone, and only entering data in rows 2 and below.</span></span> 
    
    <span data-ttu-id="58294-p118">La hoja de cálculo también debe incluir valores para el nombre de usuario (por ejemplo, alberto@contoso.com) y un nombre para mostrar (por ejemplo, Alberto Hermosilla) para cada usuario. Para dejar otros campos en blanco, escriba un espacio seguido de una coma en el campo, tal y como se muestra en la siguiente ilustración.</span><span class="sxs-lookup"><span data-stu-id="58294-p118">Your spreadsheet also needs to include values for the user name (like bob@contoso.com) and a display name (like Bob Kelly) for each user. To leave other fields blank, enter a space plus a comma in the field as shown in the following figure.</span></span> 
    
    ![Ejemplo de archivo CVS con filas en blanco especificadas](media/9c596ba1-1053-4687-a46c-c9359e9818c9.png)
  
    <span data-ttu-id="58294-p119">Si hay usuarios que trabajan en los diferentes países, deberá crear una hoja de cálculo para los usuarios de cada país. Por ejemplo, una hoja en la que se incluyan todos los que trabajan en los Estados Unidos y otra que incluya los que trabajan en Japón. Esto se debe a que la disponibilidad de los servicios de Office 365 varía según la región.</span><span class="sxs-lookup"><span data-stu-id="58294-p119">If you have people working in different countries, you'll need to create one spreadsheet for users in each country. For example, one spreadsheet that lists everyone who works in the US, and another that lists everyone who works in Japan. This is because the availability of Office 365 services varies by region.</span></span> 
    
    <span data-ttu-id="58294-p120">**Consejo:** antes de agregar una gran cantidad de usuarios a Office 365, sería conveniente que practicara con esta hoja de cálculo de muestra. Por ejemplo, edite la hoja de cálculo de muestra con datos de varios de sus usuarios (unos 5 o 10) y guarde el archivo con un nombre nuevo. Siga los pasos descritos en este procedimiento, compruebe los resultados, elimine las cuentas nuevas y vuelva a empezar. De este modo puede practicar obteniendo todos los datos adecuados para su caso. Consulte también [Consejos para aplicar formato a la hoja de cálculo](add-several-users-at-the-same-time.md#__toc314595848).</span><span class="sxs-lookup"><span data-stu-id="58294-p120">**Tip:** Before you add many users to Office 365, you might want to practice with the sample spreadsheet. For example, edit the sample spreadsheet with data for a few of your users, say 5 or 10, and save the file with a new name. Run through steps described in this procedure, check the results, and then delete the new accounts and start over again. This way you can practice getting all of the data right for your situation. Also check out [Tips for formatting your spreadsheet](add-several-users-at-the-same-time.md#__toc314595848).</span></span>
    
2. <span data-ttu-id="58294-224">Inicie sesión en Office 365 con su cuenta profesional o educativa.</span><span class="sxs-lookup"><span data-stu-id="58294-224">Sign in to Office 365 with your work or school account.</span></span> 
    
3. <span data-ttu-id="58294-225">Vaya al centro de administración.</span><span class="sxs-lookup"><span data-stu-id="58294-225">Go to the admin center.</span></span>
    
4. <span data-ttu-id="58294-p121">For people to use Office 365 services, they need to be assigned a license. Before continuing, you might want to check that you have enough licenses for everyone listed in your spreadsheet. Choose **Billing** \> **Subscriptions** to see if you have enough. If you need to buy more licenses, choose \*\* Change license quantity \*\*. Or, you can run the wizard and assign the licenses you have, then buy more licenses later and rerun the wizard.</span><span class="sxs-lookup"><span data-stu-id="58294-p121">For people to use Office 365 services, they need to be assigned a license. Before continuing, you might want to check that you have enough licenses for everyone listed in your spreadsheet. Choose **Billing** \> **Subscriptions** to see if you have enough. If you need to buy more licenses, choose \*\* Change license quantity \*\*. Or, you can run the wizard and assign the licenses you have, then buy more licenses later and rerun the wizard.</span></span> 
    
5. <span data-ttu-id="58294-p122">Ahora, vaya al asistente para agregar usuarios en bloque: elija **Usuarios** \> **Usuarios activos**. Elija ![Icono para agregar muchos usuarios a Office 365](media/3481ffea-d552-4a7f-9a3b-014504e69746.png), tal como se muestra en la siguiente ilustración.</span><span class="sxs-lookup"><span data-stu-id="58294-p122">Now go to the Bulk add users wizard: choose **Users** \> **Active Users**. Choose ![The icon for adding many users to Office 365](media/3481ffea-d552-4a7f-9a3b-014504e69746.png) as shown in the following figure.</span></span> 
    
    ![Una imagen de la sección usuarios del centro de administración](media/2cd5ff86-9c0b-438e-9bb9-13b12a2675de.png)
  
    <span data-ttu-id="58294-234">El asistente para agregar usuarios en bloque aparecerá y le mostrará paso a paso el proceso para agregar un grupo de usuarios a Office 365.</span><span class="sxs-lookup"><span data-stu-id="58294-234">The Bulk add users wizard appears and steps you through adding a group of users to Office 365.</span></span> 
    
6. <span data-ttu-id="58294-235">En el paso 1: seleccionar un archivo CSV, especifique su propia hoja de cálculo, como se muestra en la siguiente ilustración.</span><span class="sxs-lookup"><span data-stu-id="58294-235">In Step 1 - Select a CSV file, specify your own spreadsheet as shown in the following figure.</span></span>
    
    ![Paso 1 del asistente para Agregar usuarios en masa - Seleccionar archivo CSV](media/aeb837ed-1f86-427d-b038-c643c383829c.png)
  
7. <span data-ttu-id="58294-237">En el paso 2: verificación, el asistente le indica si el contenido de la hoja de cálculo tiene el formato correcto.</span><span class="sxs-lookup"><span data-stu-id="58294-237">In Step 2 - Verification, the wizard tells you whether the content in the spreadsheet is formatted correctly.</span></span>
    
    ![Paso 2 del asistente para Agregar usuarios en masa - Verificación](media/3fd3cd2c-44d4-4593-b02c-b87c176affb3.png)
  
8. <span data-ttu-id="58294-p123">En el paso 3: configuración, elija **Permitido** para que los usuarios incluidos en la hoja de cálculo puedan usar Office 365. Seleccione también el país o la región en la que los usuarios usarán Office 365. Recuerde si hay personas en la organización que vayan a usar Office 365 en un país diferente, cree una hoja de cálculo separada con sus nombres y vuelva a ejecutar el asistente para agregar usuarios en bloque para agregarlos.</span><span class="sxs-lookup"><span data-stu-id="58294-p123">In Step 3 - Settings, choose **Allowed** so that the people listed in your spreadsheet will be able to use Office 365. Also choose the country in which these people will use Office 365. Remember if some people in your organization are going to use Office 365 in a different country, create a separate spreadsheet with their names and run the Bulk add users wizard again to add them.</span></span> 
    
    ![Paso 3 del asistente para Agregar usuarios en masa - Configuración](media/ff12ad34-5d8b-4e89-a02f-d827a94095b3.png)
  
9. <span data-ttu-id="58294-243">La página de asignación de licencias indica las licencias que hay disponibles.</span><span class="sxs-lookup"><span data-stu-id="58294-243">The assign licenses page tells you how many licenses are available.</span></span> 
    
    ![Paso 4 del asistente para Agregar usuarios en masa: licencias](media/161ea34c-c67e-43be-962f-029f5426ff1b.png)
  
    <span data-ttu-id="58294-245">Puede elegir **comprar más licencias**, pero dejará el Asistente para agregar usuarios en masa e irá a **facturación** en el centro de administración de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="58294-245">You can choose **Buy more licenses**, but you'll leave the Bulk add users wizard and go to **Billing** in the Microsoft 365 admin center.</span></span> <span data-ttu-id="58294-246">Después de comprar más licencias, tendrá que esperar unos minutos para que se procese el pedido y, a continuación, inicie el asistente para Agregar usuarios en masa desde el principio.</span><span class="sxs-lookup"><span data-stu-id="58294-246">After buying more licenses, you'll have to wait a few minutes for the order to be processed and then start the Bulk add users wizard from the beginning.</span></span> 
    
    <span data-ttu-id="58294-247">Si no compra más licencias, no se crearán cuentas para todos los usuarios incluidos en la hoja de cálculo.</span><span class="sxs-lookup"><span data-stu-id="58294-247">If you don't buy more licenses, accounts won't be created for everyone listed in your spreadsheet.</span></span> 
    
    <span data-ttu-id="58294-248">En este ejemplo, no compramos más licencias y continuamos con el asistente para agregar en bloque.</span><span class="sxs-lookup"><span data-stu-id="58294-248">In this example, we don't buy any more licenses and continue with the Bulk add users wizard.</span></span>
    
10. <span data-ttu-id="58294-249">En el paso 5: enviar resultados, escriba las direcciones de correo electrónico de los usuarios que desee que reciban un mensaje de correo electrónico que enumere  *todos*  los nombres de usuario y las contraseñas temporales de Office 365 de las personas incluidas en la hoja de cálculo.</span><span class="sxs-lookup"><span data-stu-id="58294-249">In Step 5 - Send Results, type the email addresses of the people who you want to get an email that lists  *all*  of the Office 365 user names and temporary passwords for the people in the spreadsheet.</span></span> 
    
    ![Paso 5 del asistente para Agregar usuarios en masa: enviar resultados](media/5beeb825-4ba7-4ae0-bfb5-a1f8a785ebdb.png)
  
    <span data-ttu-id="58294-p125">Se envía el siguiente mensaje de correo electrónico a todas las direcciones de correo electrónico que ha especificado en el paso 5 Enviar resultados. Este mensaje de correo electrónico indica qué cuentas se crearon. Tenga en cuenta que no se crearon cuentas para algunos usuarios debido a que no había licencias suficientes.</span><span class="sxs-lookup"><span data-stu-id="58294-p125">The following email is sent to all the email addresses you specified in Step 5 - Send results. This email indicates which accounts were created. Notice that accounts weren't created for some people because there weren't enough licenses.</span></span> 
    
    ![Correo electrónico de ejemplo con información de credenciales de usuario](media/0a40c612-2078-4b5b-813e-f99bc53635a6.png)
  
    <span data-ttu-id="58294-p126">Más adelante, puede agregar más licencias y volver a ejecutar el asistente para agregar usuarios en bloque con la misma hoja de cálculo. El asistente omitirá los usuarios que ya tengan cuentas. En el informe de resultados aparecerá "nombre de usuario duplicado" para indicar que la persona son esa información ya tiene una cuenta.</span><span class="sxs-lookup"><span data-stu-id="58294-p126">You can buy more licenses later and rerun the Bulk add users wizard with the same spreadsheet. The wizard skips over the users that already have accounts; on the results report, it will say "duplicate user name" to indicate someone with that information already has an account.</span></span>
    
11. <span data-ttu-id="58294-257">La página final del asistente para agregar usuarios en bloque enumera los nombres de usuario y las contraseñas temporales, tal como se muestra en la siguiente ilustración.</span><span class="sxs-lookup"><span data-stu-id="58294-257">The final page in the Bulk add users wizard lists the user names and temporary passwords, as shown in the following figure.</span></span>
    
    ![Paso 6 del asistente para Agregar usuarios en masa: enviar resultados](media/0cd43832-071b-4b33-b57a-5d07959985ad.png)
  
12. <span data-ttu-id="58294-p127">Una vez haya agregado los usuarios a Office 365, debe comunicarles su información de cuenta de Office 365. Use el proceso habitual para comunicar nuevas contraseñas.</span><span class="sxs-lookup"><span data-stu-id="58294-p127">After you've added users to Office 365, you need to tell them about their Office 365 account information. Use your normal process for communicating new passwords.</span></span>
    

