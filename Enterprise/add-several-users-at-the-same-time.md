---
title: Agregar varios usuarios a Office 365 a la vez - Ayuda de administración
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
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
ms.openlocfilehash: 283a45750c6b5d51f96dae2cac12acf3f47b98fe
ms.sourcegitcommit: 19e306dcc32f32387202f799d5f7ef82bae926b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/04/2019
ms.locfileid: "39825202"
---
# <a name="add-several-users-at-the-same-time-to-office-365---admin-help"></a><span data-ttu-id="3595d-105">Agregar varios usuarios a Office 365 a la vez. Ayuda para administradores</span><span class="sxs-lookup"><span data-stu-id="3595d-105">Add several users at the same time to Office 365 - Admin Help</span></span>

<span data-ttu-id="3595d-p102">Todos los usuarios de su grupo deben tener una cuenta de usuario para poder iniciar sesión y acceder a servicios de Office 365, como el correo electrónico y Office. Si son muchas personas, puede agregar sus cuentas de una vez desde una hoja de cálculo de Excel u otro archivo guardado en formato CSV. [¿No tiene claro qué es un archivo CSV?](add-several-users-at-the-same-time.md#__toc316652088)</span><span class="sxs-lookup"><span data-stu-id="3595d-p102">Each person on your team needs a user account before they can sign in and access Office 365 services, such as email and Office. If you have a lot of people, you can add their accounts all at once from an Excel spreadsheet or other file saved in CSV format. [Not sure what CSV format is?](add-several-users-at-the-same-time.md#__toc316652088)</span></span>
  
> [!NOTE] 
> <span data-ttu-id="3595d-109">Si no usa el nuevo Centro de administración de Microsoft 365, puede activarlo seleccionando **Probar el nuevo centro de administración** ubicado en la parte superior de la página de inicio.</span><span class="sxs-lookup"><span data-stu-id="3595d-109">If you're not using the new Microsoft 365 admin center, you can turn it on by selecting the **Try the new admin center** toggle located at the top of the Home page.</span></span>

## <a name="add-multiple-users-to-office-365-in-the-microsoft-365-admin-center"></a><span data-ttu-id="3595d-110">Agregar varios usuarios a Office 365 en el centro de administración de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="3595d-110">Add multiple users to Office 365 in the Microsoft 365 admin center</span></span>

1. <span data-ttu-id="3595d-111">Inicie sesión en Office 365 con su cuenta profesional o educativa.</span><span class="sxs-lookup"><span data-stu-id="3595d-111">Sign in to Office 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="3595d-112">En el centro de administración, **Elija** \> usuarios **activos**.</span><span class="sxs-lookup"><span data-stu-id="3595d-112">In the admin center, choose **Users** \> **Active users**.</span></span>

3. <span data-ttu-id="3595d-113">Seleccione **agregar varios usuarios**.</span><span class="sxs-lookup"><span data-stu-id="3595d-113">Select **Add multiple users**.</span></span>

4. <span data-ttu-id="3595d-114">En el panel **Importar varios usuarios**, tiene la opción de descargar un archivo CSV de ejemplo con datos de ejemplo o sin rellenar.</span><span class="sxs-lookup"><span data-stu-id="3595d-114">On the **Import multiple users** panel, you can optionally download a sample CSV file with or without sample data filled in.</span></span> 
    
    <span data-ttu-id="3595d-115">Su hoja de cálculo debe incluir **exactamente los mismos encabezados de columna** que la de ejemplo (Nombre de usuario, Nombre, etc.). Si usa la plantilla, ábrala en una herramienta de edición de texto y considere la opción de no editar ningún dato de la fila 1 y escribir los datos a partir de la fila 2.</span><span class="sxs-lookup"><span data-stu-id="3595d-115">Your spreadsheet needs to include the **exact same column headings** as the sample one (User Name, First Name, etc...). If you use the template, open it in a text editing tool, like Notepad, and consider leaving all the data in row 1 alone, and only entering data in rows 2 and below.</span></span> 
    
    <span data-ttu-id="3595d-116">La hoja de cálculo también debe incluir valores para el nombre de usuario (por ejemplo, alberto@contoso.com) y un nombre para mostrar (por ejemplo, Alberto Hermosilla) para cada usuario.</span><span class="sxs-lookup"><span data-stu-id="3595d-116">Your spreadsheet also needs to include values for the user name (like bob@contoso.com) and a display name (like Bob Kelly) for each user.</span></span> 
    
  ```
  User Name,First Name,Last Name,Display Name,Job Title,Department,Office Number,Office Phone,Mobile Phone,Fax,Address,City,State or Province,ZIP or Postal Code,Country or Region
  chris@contoso.com,Chris,Green,Chris Green,IT Manager,Information Technology,123451,123-555-1211,123-555-6641,123-555-9821,1 Microsoft way,Redmond,Wa,98052,United States
  ben@contoso.com,Ben,Andrews,Ben Andrews,IT Manager,Information Technology,123452,123-555-1212,123-555-6642,123-555-9822,1 Microsoft way,Redmond,Wa,98052,United States
  david@contoso.com,David,Longmuir,David Longmuir,IT Manager,Information Technology,123453,123-555-1213,123-555-6643,123-555-9823,1 Microsoft way,Redmond,Wa,98052,United States
  cynthia@contoso.com,Cynthia,Carey,Cynthia Carey,IT Manager,Information Technology,123454,123-555-1214,123-555-6644,123-555-9824,1 Microsoft way,Redmond,Wa,98052,United States
  melissa@contoso.com,Melissa,MacBeth,Melissa MacBeth,IT Manager,Information Technology,123455,123-555-1215,123-555-6645,123-555-9825,1 Microsoft way,Redmond,Wa,98052,United States
  
  ```

5. <span data-ttu-id="3595d-117">Escriba una ruta de acceso al archivo en el cuadro o elija **Examinar** para ir a la ubicación del archivo CSV y, a continuación, elija **Comprobar**.</span><span class="sxs-lookup"><span data-stu-id="3595d-117">Enter a file path into the box, or choose **Browse** to browse to the CSV file location, then choose **Verify**.</span></span>
  
    <span data-ttu-id="3595d-p103">Si hay problemas con el archivo, se mostrarán en el panel. También puede descargar un archivo de registro.</span><span class="sxs-lookup"><span data-stu-id="3595d-p103">If there are problems with the file, the problem is displayed in the panel. You can also download a log file.</span></span>
    
5. <span data-ttu-id="3595d-120">En el cuadro de diálogo **Establecer opciones de usuario**, puede establecer el estado de inicio de sesión y elegir qué licencia de producto se asignará a cada uno de los usuarios.</span><span class="sxs-lookup"><span data-stu-id="3595d-120">On the **Set user options** dialog you can set the sign-in status and choose the product license that will be assigned to all users.</span></span> 
    
6. <span data-ttu-id="3595d-121">En el cuadro de diálogo **Ver el resultado**, puede elegir si desea enviar los resultados a su usuario o a otros usuarios (las contraseñas se mostrarán en texto sin formato). Además, puede ver cuántos usuarios se crearon y, si lo necesita, comprar más licencias para asignárselas a algunos de los nuevos usuarios.</span><span class="sxs-lookup"><span data-stu-id="3595d-121">On the **View your result** dialog you can choose to send the results to either yourself or other users (passwords will be in plain text) and you can see how many users were created, and if you need to purchase more licenses to assign to some of the new users.</span></span> 

## <a name="next-steps"></a><span data-ttu-id="3595d-122">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="3595d-122">Next steps</span></span>
<span data-ttu-id="3595d-123"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="3595d-123"></span></span>

- <span data-ttu-id="3595d-124">Ahora que estas personas tienen cuentas, necesitan [Descargar e instalar o reinstalar office 365 u office 2016 en un equipo PC o Mac](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658).</span><span class="sxs-lookup"><span data-stu-id="3595d-124">Now that these people have accounts, they need to [Download and install or reinstall Office 365 or Office 2016 on a PC or Mac](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658).</span></span> <span data-ttu-id="3595d-125">Cada persona de su equipo puede usar Office 365 en un máximo de 5 equipos o Mac.</span><span class="sxs-lookup"><span data-stu-id="3595d-125">Each person on your team can install Office 365 on up to 5 PCs or Macs.</span></span> 
    
- <span data-ttu-id="3595d-126">Cada persona también puede [configurar el correo electrónico y las aplicaciones de Office en un dispositivo móvil en un](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f) máximo de 5 tabletas y 5 teléfonos, como iPhone, iPad, y teléfonos y tabletas Android.</span><span class="sxs-lookup"><span data-stu-id="3595d-126">Each person can also [Set up Office apps and email on a mobile device](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f) on up to 5 tablets and 5 phones, such as iPhones, iPads, and Android phones and tablets.</span></span> <span data-ttu-id="3595d-127">De esta forma, puede editar archivos de Office desde cualquier lugar.</span><span class="sxs-lookup"><span data-stu-id="3595d-127">This way they can edit Office files from anywhere.</span></span> 
    
    <span data-ttu-id="3595d-128">Vea [set up Office 365 for Business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) para obtener una lista completa de los pasos de configuración.</span><span class="sxs-lookup"><span data-stu-id="3595d-128">See [Set up Office 365 for business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) for an end-to-end list of the setup steps.</span></span> 
    
## <a name="more-information-about-how-to-add-users-to-office-365"></a><span data-ttu-id="3595d-129">Más información sobre cómo agregar usuarios a Office 365</span><span class="sxs-lookup"><span data-stu-id="3595d-129">More information about how to add users to Office 365</span></span>
<span data-ttu-id="3595d-130"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="3595d-130"></span></span>

### <a name="not-sure-what-csv-format-is"></a><span data-ttu-id="3595d-131">¿No tiene claro qué es un archivo CSV?</span><span class="sxs-lookup"><span data-stu-id="3595d-131">Not sure what CSV format is?</span></span>
<span data-ttu-id="3595d-132"><a name="__toc316652088"> </a></span><span class="sxs-lookup"><span data-stu-id="3595d-132"></span></span>

<span data-ttu-id="3595d-p106">Un archivo CSV es un archivo con valores separados por comas. Puede crear o editar un archivo como este con cualquier editor de textos o programa de hojas de cálculo, como Excel.</span><span class="sxs-lookup"><span data-stu-id="3595d-p106">A CSV file is a file with comma separated values. You can create or edit a file like this with any text editor or spreadsheet program, such as Excel.</span></span>
  
<span data-ttu-id="3595d-p107">Puede descargar [esta hoja de cálculo de muestra](https://www.microsoft.com/download/details.aspx?id=45485) como punto de partida. Recuerde que Office 365 requiere encabezados de columna en la primera fila, así que no los sustituya con ningún otro elemento.</span><span class="sxs-lookup"><span data-stu-id="3595d-p107">You can download [this sample spreadsheet](https://www.microsoft.com/download/details.aspx?id=45485) as a starting point. Remember that Office 365 requires column headings in the first row so don't replace them with something else.</span></span> 
  
<span data-ttu-id="3595d-137">Guarde el archivo con un nuevo nombre y especifique el formato CSV.</span><span class="sxs-lookup"><span data-stu-id="3595d-137">Save the file with a new name, and specify CSV format.</span></span>
  
![Imagen de cómo guardar un archivo de Excel en formato CSV](media/35a86ebe-63ab-4b4d-9a92-e177de33ebae.png)
  
<span data-ttu-id="3595d-p108">Cuando guarde el archivo, probablemente recibirá un mensaje que le informará de que se perderán algunas características del libro si guarda el archivo en formato CSV. No pasa nada. Haga clic en **Sí** para continuar.</span><span class="sxs-lookup"><span data-stu-id="3595d-p108">When you save the file, you'll probably get a prompt that some features in your workbook will be lost if you save the file in CSV format. This is okay. Click **Yes** to continue.</span></span> 
  
![Imagen del mensaje que obtendría en Excel que pregunta si realmente quiere guardar el archivo como formato CSV](media/51032a81-690c-45ef-bfc5-09ea7f790e98.png)
  
### <a name="tips-for-formatting-your-spreadsheet"></a><span data-ttu-id="3595d-143">Consejos para aplicar formato a la hoja de cálculo</span><span class="sxs-lookup"><span data-stu-id="3595d-143">Tips for formatting your spreadsheet</span></span>
<span data-ttu-id="3595d-144"><a name="__toc314595848"> </a></span><span class="sxs-lookup"><span data-stu-id="3595d-144"></span></span>

- <span data-ttu-id="3595d-p109">**¿Debo mantener los mismos encabezados de columna que en la hoja de cálculo de muestra?** Sí. La hoja de cálculo de muestra contiene los encabezados de columna en la primera fila. Estos encabezados son necesarios. Para cada usuario que desee agregar a Office 365, cree una fila bajo el encabezado. Si agrega, cambia o elimina cualquiera de los encabezados de columna, Office 365 podría no crear usuarios a partir de la información del archivo.</span><span class="sxs-lookup"><span data-stu-id="3595d-p109">**Do I need the same column headings as in the sample spreadsheet?** Yes. The sample spreadsheet contains column headings in the first row. These headings are required. For each user you want to add to Office 365, create a row under the heading. If you add, change, or delete any of the column headings, Office 365 might not be able to create users from the information in the file.</span></span> 
    
- <span data-ttu-id="3595d-p110">**¿Qué ocurre si no tengo toda la información requerida para cada usuario?** El nombre de usuario y el nombre para mostrar son obligatorios, y no puede agregar un nuevo usuario sin esta información. Si le falta parte de la información, como el fax, puede usar un espacio más una coma para indicar que el campo debe dejarse en blanco.</span><span class="sxs-lookup"><span data-stu-id="3595d-p110">**What if I don't have all the information required for each user?** The user name and display name are required, and you cannot add a new user without this information. If you don't have some of the other information, such as the fax, you can use a space plus a comma to indicate that the field should remain blank.</span></span> 
    
- <span data-ttu-id="3595d-p111">\*\* How small or large can the spreadsheet be? \*\* The spreadsheet must have at least two rows. One is for the column headings (the user data column label) and one for the user. You cannot have more than 251 rows. If you need to import more than 250 users, you can create more than one spreadsheet.</span><span class="sxs-lookup"><span data-stu-id="3595d-p111">\*\* How small or large can the spreadsheet be? \*\* The spreadsheet must have at least two rows. One is for the column headings (the user data column label) and one for the user. You cannot have more than 251 rows. If you need to import more than 250 users, you can create more than one spreadsheet.</span></span> 
    
- <span data-ttu-id="3595d-p112">\*\* What languages can I use? \*\* When you create your spreadsheet, you can enter user data column labels in any language or characters, but you must not change the order of the labels, as shown in the sample. You can then make entries into the fields, using any language or characters, and save your file in a Unicode or UTF-8 format.</span><span class="sxs-lookup"><span data-stu-id="3595d-p112">\*\* What languages can I use? \*\* When you create your spreadsheet, you can enter user data column labels in any language or characters, but you must not change the order of the labels, as shown in the sample. You can then make entries into the fields, using any language or characters, and save your file in a Unicode or UTF-8 format.</span></span> 
    
- <span data-ttu-id="3595d-p113">**¿Qué ocurre si voy a agregar usuarios de diferentes países o regiones?** Cree una hoja de cálculo para cada área. Deberá seguir los pases del asistente para agregar usuarios en bloque para cada una de las hojas de cálculo y dar una única ubicación a todos los usuarios incluidos en el archivo con los que trabaja.</span><span class="sxs-lookup"><span data-stu-id="3595d-p113">**What if I'm adding users from different countries or regions?** Create a separate spreadsheet for each area. You'll need to step through the Bulk add users wizard which each spreadsheet, giving a single location of all users included in the file that you're working with.</span></span> 
    
- <span data-ttu-id="3595d-p114">**¿Existe algún límite de caracteres que se pueden usar?** En la siguiente tabla se muestran las etiquetas de las columnas de datos de usuario y la longitud máxima (en caracteres) para cada una en la hoja de cálculo de muestra.</span><span class="sxs-lookup"><span data-stu-id="3595d-p114">**Is there a limit to the number of characters I can use?** The following table shows the user data column labels and the maximum character length for each in the sample spreadsheet.</span></span> 
    
|<span data-ttu-id="3595d-167">**Etiquetas columnas datos usuarios**</span><span class="sxs-lookup"><span data-stu-id="3595d-167">**User data column label**</span></span>|<span data-ttu-id="3595d-168">**Longitud máxima (en caracteres)**</span><span class="sxs-lookup"><span data-stu-id="3595d-168">**Maximum character length**</span></span>|
|:-----|:-----|
|<span data-ttu-id="3595d-169">Nombre de usuario (obligatorio)</span><span class="sxs-lookup"><span data-stu-id="3595d-169">User Name (Required)</span></span>  <br/> |<span data-ttu-id="3595d-p115">79 incluida la arroba (@), en el formato nombre@dominio.\<extensión\>. El alias del usuario no debe superar los 30 caracteres y el nombre de dominio no debe superar los 48 caracteres.</span><span class="sxs-lookup"><span data-stu-id="3595d-p115">79 including the at sign (@), in the format name@domain.\<extension\>. The user's alias cannot exceed 30 characters, and the domain name cannot exceed 48 characters.</span></span>  <br/> |
|<span data-ttu-id="3595d-172">Nombre</span><span class="sxs-lookup"><span data-stu-id="3595d-172">First Name</span></span>  <br/> |<span data-ttu-id="3595d-173">64</span><span class="sxs-lookup"><span data-stu-id="3595d-173">64</span></span>  <br/> |
|<span data-ttu-id="3595d-174">Apellido</span><span class="sxs-lookup"><span data-stu-id="3595d-174">Last Name</span></span>  <br/> |<span data-ttu-id="3595d-175">64</span><span class="sxs-lookup"><span data-stu-id="3595d-175">64</span></span>  <br/> |
|<span data-ttu-id="3595d-176">Nombre para mostrar (obligatorio)</span><span class="sxs-lookup"><span data-stu-id="3595d-176">Display Name (required)</span></span>  <br/> |<span data-ttu-id="3595d-177">256</span><span class="sxs-lookup"><span data-stu-id="3595d-177">256</span></span>  <br/> |
|<span data-ttu-id="3595d-178">Puesto</span><span class="sxs-lookup"><span data-stu-id="3595d-178">Job Title</span></span>  <br/> |<span data-ttu-id="3595d-179">64</span><span class="sxs-lookup"><span data-stu-id="3595d-179">64</span></span>  <br/> |
|<span data-ttu-id="3595d-180">Departamento</span><span class="sxs-lookup"><span data-stu-id="3595d-180">Department</span></span>  <br/> |<span data-ttu-id="3595d-181">64</span><span class="sxs-lookup"><span data-stu-id="3595d-181">64</span></span>  <br/> |
|<span data-ttu-id="3595d-182">Número del trabajo</span><span class="sxs-lookup"><span data-stu-id="3595d-182">Office Number</span></span>  <br/> |<span data-ttu-id="3595d-183">128</span><span class="sxs-lookup"><span data-stu-id="3595d-183">128</span></span>  <br/> |
|<span data-ttu-id="3595d-184">Teléfono del trabajo</span><span class="sxs-lookup"><span data-stu-id="3595d-184">Office Phone</span></span>  <br/> |<span data-ttu-id="3595d-185">64</span><span class="sxs-lookup"><span data-stu-id="3595d-185">64</span></span>  <br/> |
|<span data-ttu-id="3595d-186">Teléfono móvil</span><span class="sxs-lookup"><span data-stu-id="3595d-186">Mobile Phone</span></span>  <br/> |<span data-ttu-id="3595d-187">64</span><span class="sxs-lookup"><span data-stu-id="3595d-187">64</span></span>  <br/> |
|<span data-ttu-id="3595d-188">Fax</span><span class="sxs-lookup"><span data-stu-id="3595d-188">Fax</span></span>  <br/> |<span data-ttu-id="3595d-189">64</span><span class="sxs-lookup"><span data-stu-id="3595d-189">64</span></span>  <br/> |
|<span data-ttu-id="3595d-190">Dirección</span><span class="sxs-lookup"><span data-stu-id="3595d-190">Address</span></span>  <br/> |<span data-ttu-id="3595d-191">1023</span><span class="sxs-lookup"><span data-stu-id="3595d-191">1023</span></span>  <br/> |
|<span data-ttu-id="3595d-192">Ciudad</span><span class="sxs-lookup"><span data-stu-id="3595d-192">City</span></span>  <br/> |<span data-ttu-id="3595d-193">128</span><span class="sxs-lookup"><span data-stu-id="3595d-193">128</span></span>  <br/> |
|<span data-ttu-id="3595d-194">Estado o provincia</span><span class="sxs-lookup"><span data-stu-id="3595d-194">State or Province</span></span>  <br/> |<span data-ttu-id="3595d-195">128</span><span class="sxs-lookup"><span data-stu-id="3595d-195">128</span></span>  <br/> |
|<span data-ttu-id="3595d-196">Código postal</span><span class="sxs-lookup"><span data-stu-id="3595d-196">ZIP or Postal Code</span></span>  <br/> |<span data-ttu-id="3595d-197">40</span><span class="sxs-lookup"><span data-stu-id="3595d-197">40</span></span>  <br/> |
|<span data-ttu-id="3595d-198">País o región</span><span class="sxs-lookup"><span data-stu-id="3595d-198">Country or Region</span></span>  <br/> |<span data-ttu-id="3595d-199">128</span><span class="sxs-lookup"><span data-stu-id="3595d-199">128</span></span>  <br/> |
   
### <a name="still-having-problems-when-adding-users-to-office-365"></a><span data-ttu-id="3595d-200">¿Aún tiene problemas al agregar usuarios a Office 365?</span><span class="sxs-lookup"><span data-stu-id="3595d-200">Still having problems when adding users to Office 365?</span></span>

- <span data-ttu-id="3595d-p116">**Asegúrese una vez más de que el archivo tenga un formato correcto.** Compruebe que los encabezados de las columnas coincidan con los encabezados del archivo de muestra. Asegúrese de haber respetado los límites de longitud y de que los campos estén separados por comas.</span><span class="sxs-lookup"><span data-stu-id="3595d-p116">**Double-check that the spreadsheet is formatted correctly.** Check the column headings to make sure they match the headings in the sample file. Make sure you're following the rules for character lengths and that each field is separated by a comma.</span></span> 
    
- <span data-ttu-id="3595d-204">**Si no ve los nuevos usuarios en Office 365 inmediatamente, espere unos minutos.**</span><span class="sxs-lookup"><span data-stu-id="3595d-204">**If you don't see the new users in Office 365 right away, wait a few minutes.**</span></span> <span data-ttu-id="3595d-205">Los cambios pueden tardar un poco en llegar a todos los servicios de Office 365.</span><span class="sxs-lookup"><span data-stu-id="3595d-205">It can take a little while for changes to go across all the services in Office 365.</span></span> 
    
## <a name="related-articles"></a><span data-ttu-id="3595d-206">Artículos relacionados</span><span class="sxs-lookup"><span data-stu-id="3595d-206">Related articles</span></span>

[<span data-ttu-id="3595d-207">Agregar usuarios individualmente o de forma masiva a Office 365</span><span class="sxs-lookup"><span data-stu-id="3595d-207">Add users individually or in bulk to Office 365</span></span>](https://docs.microsoft.com/office365/admin/add-users/add-users)




