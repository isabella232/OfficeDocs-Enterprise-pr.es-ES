---
title: 'Recuperar elementos eliminados en un buzón de usuario: ayuda para administradores'
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: eb15194b-63ec-41b0-8d90-1823d3f558e4
description: 'En este artículo está dirigido a administradores. ¿Un usuario eliminar permanentemente los elementos de su buzón de Outlook? El usuario copia lo solicite, pero no puede recuperarlos. Es posible que pueda recuperar los elementos purgados si aún no se han quitado permanentemente el buzón del usuario. '
ms.openlocfilehash: abfc0a1a35d8e694197e12d05a2206dd4e3eb37a
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542764"
---
# <a name="recover-deleted-items-in-a-user-mailbox---admin-help"></a>Recuperar elementos eliminados en un buzón de usuario: ayuda para administradores

**Este artículo está dirigido a administradores. Está intentando recuperar elementos eliminados en su propio buzón de correo?** Pruebe con uno de los procedimientos siguientes:
- [Recuperación de elementos eliminados en Outlook para Windows](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)
- [Recuperar elementos eliminados o correo electrónico en Outlook Web App](https://support.office.com/article/c3d8fc15-eeef-4f1c-81df-e27964b7edd4)
- [Restauración de los mensajes de correo electrónico eliminados en Outlook en el web](https://support.office.com/article/a8ca78ac-4721-4066-95dd-571842e9fb11)
- [Outlook.com](https://go.microsoft.com/fwlink/p/?LinkID=623435)
   
¿Un usuario eliminar permanentemente los elementos de su buzón de Outlook? El usuario copia lo solicite, pero no puede recuperarlos. Es posible que pueda recuperar los elementos purgados si aún no se han quitado permanentemente el buzón del usuario. Hacerlo mediante la herramienta de exhibición de documentos electrónicos en contexto en Exchange Online para buscar correo electrónico eliminado y otros elementos y como contactos, citas de calendario y tareas, en el buzón del usuario. Si observa los elementos eliminados, puede exportarlos a un archivo PST (también denominado un archivo de datos de Outlook), que el usuario, a continuación, puede usar para restaurar los elementos en su buzón.
  
Estos son los pasos para recuperar los elementos eliminados en el buzón del usuario. ¿Cuánto tiempo tardará esto? La primera vez puede tardar 20 o 30 minutos para completar todos los pasos, según el número de elementos está intentando recuperar.
  
> [!NOTE]
> Tiene que ser un **Administrador de Exchange** o un **Administrador Global** en Office 365 o ser miembro del grupo de roles de administración de la organización de Exchange en línea para llevar a cabo los pasos de este artículo. Para obtener más información, vea [roles de administrador acerca de Office 365](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d). 
  
## <a name="step-1-assign-yourself-ediscovery-permissions"></a>Paso 1: Asignar permisos de exhibición de documentos electrónicos
<a name="step1"> </a>

El primer paso consiste en asignar usted mismo los permisos necesarios en Exchange Online por lo que puede usar la herramienta de exhibición de documentos electrónicos en contexto para buscar el buzón de un usuario. Solo tiene que hacer esto una vez. Si tiene que buscar otro buzón en el futuro, puede omitir este paso.
  
1. [Where iniciar sesión en Office 365 para la empresa](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) con su cuenta de trabajo o escuela. 
    
2. Seleccione el icono del selector de aplicación ![el icono del selector de aplicación en Office 365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) en la superior izquierda y haga clic en **Admin**.
    
3. En la izquierda en el centro de administración de Office 365, expanda **centros de administración**y, a continuación, haga clic en **Exchange**.
    
    ![Lista del centro de administración](media/7d308eb7-ba63-4156-a845-3770facc5de4.PNG)
  
4. En el centro de administración de Exchange, haga clic en **permisos**y, a continuación, haga clic en **roles de administrador**.
    
5. En la vista de lista, seleccione **Administración de detección**y, a continuación, haga clic en **Editar**![icono Editar](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif).
    
    ![Agregarse a sí mismo al grupo de funciones de administración de detección en el EAC](media/e5c98e93-d6a0-40c5-a143-bac956eedaa7.png)
  
6. En el **Grupo de roles**, en **miembros**, haga clic en **Agregar**![icono Agregar](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).
    
7. En **Seleccionar miembros**, seleccione usted mismo de la lista de nombres, haga clic en **Agregar**y, a continuación, haga clic en **Aceptar**.
    
    > [!NOTE]
    > También puede agregar un grupo que es un miembro de, como administración de la organización o TenantAdmins. Si agrega un grupo, se asignará a otros miembros del grupo de los permisos necesarios para ejecutar la herramienta de exhibición de documentos electrónicos en contexto. 
  
8. En **Grupo de roles**, haga clic en **Guardar**.
    
9. Cerrar la sesión de Office 365.
    
    Se debe cerrar la sesión antes de iniciar el paso siguiente para que los nuevos permisos surta efecto.
    
> [!CAUTION]
> Los miembros del grupo de roles de administración de detección pueden tener acceso a contenido de mensaje confidencial. Esto incluye la búsqueda de todos los buzones en la organización, obtener una vista previa de los resultados de búsqueda (y otros elementos del buzón de correo), copiar los resultados a un buzón de detección y exportar los resultados de búsqueda a un archivo PST. 
  
[Return to top](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-2-search-the-users-mailbox-for-deleted-items"></a>Paso 2: Buscar el buzón del usuario para los elementos eliminados
<a name="step2"> </a>

Cuando se ejecuta una búsqueda de exhibición de documentos electrónicos en contexto, la carpeta elementos recuperables en el buzón de correo que buscar, automáticamente se incluye en la búsqueda. La carpeta elementos recuperables es donde se almacenan los elementos eliminados de forma permanente hasta que está purgar (quita permanentemente) desde el buzón de correo. Por lo tanto, si todavía no se han purgado un elemento, debe ser capaz de encontrar mediante la herramienta de exhibición de documentos electrónicos en contexto.
  
1. [Where iniciar sesión en Office 365 para la empresa](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) con su cuenta de trabajo o escuela. 
    
2. Seleccione el icono del selector de aplicación ![el icono del selector de aplicación en Office 365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) en la superior izquierda y haga clic en **Admin**.
    
3. En la izquierda en el centro de administración de Office 365, expanda **administración**y, a continuación, haga clic en **Exchange**.
    
4. En el centro de administración de Exchange, haga clic en **administración de cumplimiento**, haga clic en **en-exhibición de documentos electrónicos &amp; suspensión**y, a continuación, haga clic en **nuevo**![icono Agregar](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).
    
    ![En el CEF, en la página de administración de cumplimiento, haga clic en la exhibición de documentos electrónicos en contexto y retención](media/9d9ff0f5-b9be-45b8-8b5e-6037a856b0a8.png)
  
5. En la página **nombre y descripción** , escriba un nombre para la búsqueda (por ejemplo, el nombre del usuario que va a recuperar el correo electrónico para), una descripción opcional y, a continuación, haga clic en **siguiente**.
    
6. En la página de **los buzones de correo** , haga clic en **especificar los buzones de correo para buscar**y, a continuación, haga clic en **Agregar**![icono Agregar](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).
    
    ![Haga clic en especificar los buzones de correo para buscar para buscar un buzón de correo específicas](media/83879a40-5e5c-49a8-be3b-c0023d197588.png)
  
7. Busque y seleccione el nombre del usuario que va a recuperar el correo electrónico eliminado para, haga clic en **Agregar**y, a continuación, haga clic en **Aceptar**.
    
8. Haga clic en **Siguiente**.
    
    Se abrirá la página de **consulta de búsqueda** . Esto es donde se definen los criterios de búsqueda que le ayudará a encontrar los elementos que faltan en el buzón del usuario. 
    
9. En la página **Consulta de búsqueda**, complete los campos siguientes: 
    
  - **Incluir todo el contenido** Seleccione esta opción para incluir todo el contenido en el buzón del usuario en los resultados de búsqueda. Si selecciona esta opción, no puede especificar criterios de búsqueda adicionales. 
    
  - **Filtro basado en criterios** Seleccione esta opción para especificar los criterios de búsqueda, incluidas las palabras clave, iniciar y finalizar las fechas, remitente y las direcciones de destinatario y tipos de mensajes. 
    
    ![Crear una búsqueda basada en criterios como palabras clave, intervalo de fechas, los destinatarios y tipos de mensajes](media/ee47b833-9122-46a0-85e6-fcbe25be0dd5.png)
  
|**Campo**|**Utilice esta página para...**|
|:-----|:-----|
|![Número uno en un círculo rosado](media/a4da261d-2516-48c5-b58a-9c452b9086b8.png)           <br/> |Especificar las palabras clave, intervalo de fechas, los destinatarios y tipos de mensajes.  <br/> |
|![Número dos en un círculo rosado.](media/de3c1ab4-4f01-4026-b1ba-3265bdb32a89.png)           <br/> |Para los mensajes con las palabras clave o frases de búsqueda y usar operadores lógicos, como **AND** u **OR**.  <br/> |
|![Número tres en un círculo rosado.](media/60fa378c-6ac1-4cbd-a782-2fa7ca619dc6.png)           <br/> |Buscar los mensajes enviados o recibidos dentro de un intervalo de fechas.  <br/> |
|![Número 4 en un círculo rosado.](media/1a0ff2ce-0942-405a-94e3-9bfeb1e5059e.png)           <br/> |Buscar mensajes del recibidos o enviados a personas específicas.  <br/> |
|![Número cinco en un círculo rosado.](media/878cc815-0165-49ba-a1ee-9236e5980403.png)           <br/> |Buscar todos los tipos de mensajes o seleccione los que desee.  <br/> |
   
    > [!TIP]
    >  Here's a few tips about how to build a search query to find missing items. Try to get as much information from the user to help you create a search query so you can find what you're looking for. >  If you not sure how to find a missing message, consider using the **Include all content** option. The search results will include all items in the user's Recoverable Items folder, including the hidden folder (called the Purges folder) that contain items that have been purged by the user. Then you can go to Step 3, copy the results to a discovery mailbox, and look at the message in the hidden folder. >  If you know approximately when the missing message was originally sent or received by the user, use the **Specify start date** and **Specify end date** options to provide a date range. This will return all messages sent or received by the user within that date range. Specifying a date range is a really good way to narrow the search results. >  If you know who sent the missing email, use the **From** box to specify this sender. >  If you want to narrow the search results to different types of mailbox items, click **Select message types**, click **Select the message types to search**, and then choose a specific message type to search for. For example, you can search only for calendar items or contacts. Here's a screenshot of the different message types you can search for; the default is to search for all message types. 
  
    Click **Next** when you've completed the **Search query** page. 
    
10. En la página **configuración de retención en contexto** , haga clic en **Finalizar** para iniciar la búsqueda. Para recuperar el correo electrónico eliminado, no hay ningún motivo para colocar el buzón del usuario en suspensión. 
    
    Después de iniciar la búsqueda, Exchange mostrará una estimación del tamaño total y el número de elementos que será devuelto por la búsqueda en función de los criterios especificados.
    
11. Seleccione la búsqueda que acaba de crear y haga clic en **Actualizar**![actualizar](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) para actualizar la información que se muestra en el panel de detalles. El estado de **Estimación se ha realizado correctamente** indica que la búsqueda ha finalizado. Exchange también muestra una estimación del número total de elementos (y su tamaño) que se encuentra por la búsqueda en función de los criterios de búsqueda que se especificó en el paso 9. 
    
12. En el panel de detalles, haga clic en **vista previa de resultados de búsqueda** para ver los elementos que se han encontrado. Esto puede ayudar a identificar los elementos que está buscando. Si encuentra el elemento o elementos que se intenta recuperar, vaya al paso 4 para exportar los resultados de búsqueda a un archivo PST. 
    
    ![Haga clic en vista previa de resultados de búsqueda para ver el elemento que está intentando recuperar](media/a2cea921-dafa-45d6-97d4-ae45a226b8d3.png)
  
13. Si no encuentra lo busca, puede revisar los criterios de búsqueda mediante la selección de la búsqueda, haga clic en **Editar**![icono Editar](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif)y, a continuación, haga clic en **consulta de búsqueda**. Cambiar los criterios de búsqueda y, a continuación, vuelva a ejecutar la búsqueda.
    
[Return to top](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="optional-step-3-copy-the-search-results-to-a-discovery-mailbox"></a>(Opcional) Paso 3: Copiar los resultados de búsqueda en un buzón de detección
<a name="step3"> </a>

Si no puede encontrar un elementos por obtener una vista previa de los resultados de búsqueda o si desea ver los elementos que están en la carpeta del usuario elementos recuperables, a continuación, puede copiar los resultados de búsqueda en un buzón especial (denominado un buzón de detección) y, a continuación, abra ese buzón de correo en Outlook en el web t o ver los elementos reales. El mejor motivo para copiar los resultados de búsqueda es por lo que puede ver los elementos en la carpeta del usuario elementos recuperables. Más probable es que el elemento que está intentando recuperar se encuentra en la subcarpeta de purga. 
  
1. En el centro de administración de Exchange, vaya a **administración de cumplimiento** \> **exhibición de documentos electrónicos en contexto &amp; suspensión**.
    
2. En la lista de búsquedas, seleccione la búsqueda que creó en el paso 2.
    
3. Haga clic en **búsqueda**![búsqueda](media/c94e8591-7044-4650-a0d1-c57c0633ab4f.png)y, a continuación, haga clic en **copiar los resultados de búsqueda** de la lista desplegable. 
    
    ![Haga clic en Buscar y, a continuación, haga clic en copiar los resultados de búsqueda](media/7888df82-94b4-4e44-8a53-f66854dc7c86.png)
  
4. En la página **Copiar los resultados de búsqueda** , haga clic en **Examinar**.
    
    ![Deje las casillas de verificación no está seleccionada cuando la recuperación de elementos eliminados](media/37f27999-a5b2-4fed-87e2-bad6dc23cdae.png)
  
5. En **Nombre para mostrar**, haga clic en **El buzón de correo de detección de búsqueda**y, a continuación, haga clic en **Aceptar**.
    
    ![Copiar los resultados de búsqueda en el buzón de búsqueda de detección predeterminado](media/36e8ef47-0035-4982-9ed6-426719c5f9ec.png)
  
    > [!NOTE]
    > El buzón de búsqueda de detección es un buzón de correo de detección predeterminado que se crea automáticamente en la organización de Office 365. 
  
6. Copia en la página **Copiar los resultados de búsqueda** , haga clic en **Copiar** para iniciar el proceso para copiar los resultados de búsqueda en el buzón de búsqueda de detección. 
    
    ![Haga clic en Copiar para copiar los resultados de búsqueda en el buzón de búsqueda de detección](media/71307a9d-f7a1-4e01-ae37-1d49040cc3fd.png)
  
7. Haga clic en **Actualizar**![actualizar](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) para actualizar la información sobre el estado de copia que se muestra en el panel de detalles. 
    
8. Cuando se complete la copia, haga clic en **Abrir** para abrir el buzón de búsqueda de detección para ver los resultados de búsqueda. 
    
    ![Haga clic en Abrir para ir al buzón de búsqueda de detección para ver los resultados de búsqueda](media/6cc81e0f-ceed-4464-9040-79b6f920de35.png)
  
    Los resultados de búsqueda que se copian en el buzón de búsqueda de detección se colocan en una carpeta que tiene el mismo nombre que la búsqueda de exhibición de documentos electrónicos en contexto. Puede hacer clic en una carpeta para mostrar los elementos de esa carpeta.
    
    ![Resultados de búsqueda en el buzón de correo de la búsqueda de detección; sólo se pueden recuperar los elementos de la carpeta de purga por un administrador](media/2ef8e5fb-3e63-4f62-938e-307efe9f6998.gif)
  
    Cuando se ejecuta una búsqueda, también se busca en la carpeta del usuario elementos recuperables. Esto significa que si los elementos de la carpeta elementos recuperables cumplen los criterios de búsqueda, se incluyen en los resultados de búsqueda. Elementos de la carpeta de eliminaciones son los elementos que el usuario eliminado de forma permanente (mediante la eliminación de un elemento desde la carpeta Elementos eliminados o seleccionándolo y presionando la tecla **MAYÚS + SUPR**. Un usuario puede usar la herramienta de recuperar elementos eliminados en Outlook o Outlook en la web para recuperar los elementos en la carpeta de eliminaciones. Elementos de la carpeta de purga son los elementos que el usuario se purga mediante la herramienta de recuperar elementos eliminados o elementos que se han purgado automáticamente por una directiva aplicada al buzón. En cualquier caso, sólo un administrador puede recuperar los elementos en la carpeta de purga. 
    
    > [!TIP]
    > Si un usuario no puede encontrar un elemento eliminado mediante la herramienta de elementos recuperables, pero sigue siendo recuperable que el elemento (lo que significa no haya sido eliminado con permanentemente desde el buzón de correo), lo más probable es que está en la carpeta de purga. Por lo tanto, asegúrese de buscar en la carpeta de purga para el elemento eliminado que está intentando recuperar para un usuario. 
  
[Return to top](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-4-export-the-search-results-to-a-pst-file"></a>Paso 4: Exportar los resultados de búsqueda a un archivo PST
<a name="step4"> </a>

Una vez que encuentre el elemento que está intentando recuperar para un usuario, el siguiente paso es exportar los resultados de la búsqueda que ejecutó en el paso 2 a un archivo PST. El usuario utilizará este archivo PST en el paso siguiente para restaurar el elemento eliminado en su buzón.
  
1. En el centro de administración de Exchange, vaya a **administración de cumplimiento** \> **exhibición de documentos electrónicos en contexto &amp; suspensión**.
    
2. En la lista de búsquedas, seleccione la búsqueda que creó en el paso 2.
    
3. Haga clic en **Exportar a un archivo PST**.
    
    ![Haga clic en Exportar a un archivo PST](media/4e59ae17-4541-43f4-a6d1-1f8b9ba9404b.png)
  
4. Si le pide para instalar la herramienta de exportación de exhibición de documentos, haga clic en **Ejecutar**.
    
5. En la herramienta de exportación de PST de eDiscovery, haga clic en **Examinar** para especificar la ubicación donde desea descargar el archivo PST. 
    
    ![La herramienta de exportación de PST de exhibición de documentos electrónicos](media/17274d27-992e-4034-8133-8f793f554e6c.png)
  
    Puede pasar por alto las opciones para habilitar la desduplicación e incluir buscar elementos.
    
6. Haga clic en **Iniciar** para descargar el archivo PST en el equipo. 
    
    La **herramienta de exportación de PST de exhibición de documentos** muestra información de estado sobre el proceso de exportación. Una vez finalizada la exportación, se puede tener acceso al archivo en la ubicación donde descargó. 
    
[Return to top](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-5-restore-the-recovered-items-to-the-users-mailbox"></a>Paso 5: Restaurar los elementos recuperados en el buzón del usuario
<a name="step5"> </a>

El último paso es usar el archivo PST que se exportó en el paso 4 para restaurar los elementos recuperados en el buzón del usuario. Después de enviar el archivo PST al usuario, en el resto de este paso se realiza por el usuario para abrir el archivo PST y, a continuación, mover los elementos recuperados a otra carpeta en su buzón. Para obtener instrucciones paso a paso, también puede enviar al usuario un vínculo para este tema: [Abrir y cerrar archivos de datos de Outlook (.pst)](https://support.office.com/article/381b776d-7511-45a0-953a-0935c79d24f2). O bien, puede enviar al usuario un vínculo a la sección [restaurar los elementos a un buzón mediante un archivo PST eliminados](recover-deleted-items-in-a-mailbox.md#restoredeleteditems) más adelante y pídales que lleve a cabo estos pasos. 
  
 **Enviar el archivo PST al usuario**
  
El paso final que necesita para llevar a cabo está enviando el archivo PST que se exportó en el paso 4 para el usuario. Hay varias formas de hacer esto:
  
- Adjunte el archivo PST a un mensaje de correo electrónico. Si Outlook está configurado para los archivos PST de bloque, tendrá el archivo zip y, a continuación, se adjunta al mensaje. Aquí es cómo:
    
1. En el Explorador de Windows o el Explorador de archivos, busque el archivo PST.
    
2. Haga clic en el archivo y, a continuación, seleccione **Enviar a** \> **carpeta comprimida (zip)**. Windows crea un nuevo archivo zip y se le da un nombre idéntico como el archivo PST.
    
3. Adjuntar el archivo comprimido de PST a un mensaje de correo electrónico y enviarlo al usuario, que, a continuación, puede descomprimir el archivo haciendo clic en él.
    
- Copie el archivo PST en una carpeta compartida que el usuario puede tener acceso y recuperarlo.
    
Los pasos descritos en la siguiente sección se realizan por el usuario para restaurar los elementos eliminados en su buzón.
  
 **Restaurar los elementos eliminados en un buzón con un archivo PST**
  
Se debe usar la aplicación de escritorio de Outlook para restaurar un elemento eliminado mediante un archivo PST. No puede usar Outlook Web App o Outlook en la web para abrir un archivo PST.
  
1. En Outlook 2013 o 2016 de Outlook, haga clic en la pestaña **archivo** . 
    
2. Haga clic en **abiertos &amp; exportar**y, a continuación, haga clic en **Abrir archivo de datos de Outlook**.
    
3. Vaya a la ubicación donde guardó el archivo PST que envían el administrador.
    
4. Seleccione el archivo PST y, a continuación, haga clic en **Abrir**.
    
    El archivo PST aparece en la barra de navegación de la izquierda en Outlook.
    
    ![El archivo PST aparece en la barra de navegación de la izquierda en Outlook](media/c9389392-d08a-4aa7-848c-4986d448b0f2.png)
  
5. Haga clic en las flechas para expandir el archivo PST y las carpetas debajo de él para buscar el elemento que desea recuperar.
    
    ![Buscar en la carpeta de purga para el elemento que desea recuperar](media/d4e372d9-ac23-4e95-8639-d8da690fefa7.png)
  
    > [!TIP]
    > Buscar en la carpeta de purga para el elemento que desea recuperar. Esto es una carpeta oculta que purgarán se mueven los elementos a. Es probable que es el elemento que se encuentra el administrador recuperado en esta carpeta. 
  
6. Haga clic en el elemento que desea recuperar y, a continuación, haga clic en **mover** \> **Otra carpeta**.
    
    ![Haga clic en mover y, a continuación, seleccionar otra carpeta](media/090063df-2aa0-444a-8e47-abd6fe6cf7a8.png)
  
7. Para mover el elemento a la Bandeja de entrada, haga clic en la **Bandeja de entrada**y, a continuación, haga clic en **Aceptar**.
    
    **Sugerencia:** Para recuperar otros tipos de elementos, realice una de las siguientes opciones: 
    
  - Para recuperar un elemento de calendario, haga clic en él y, a continuación, haga clic en **mover** \> **Otra carpeta** \> **calendario**.
    
  - Para recuperar un contacto, haga clic en él y, a continuación, haga clic en **mover** \> **Otra carpeta** \> **contactos**.
    
  - Para recuperar una tarea, haga clic en él y, a continuación, haga clic en **mover** \> **Otra carpeta** \> **tareas**.
    
![Seleccione una carpeta para mover otros tipos de elementos](media/f8290131-43f2-46f1-bc07-228c2d83b96c.png)
  
    Note that calendar items, contacts, and tasks are located directly in the Purges folder, and not in a Calendar, Contacts, or Tasks subfolder. However, you can sort by **Type** to group similar types of items. 
    
8. Cuando haya terminado de recuperación de elementos eliminados, haga clic en el archivo PST en la barra de navegación de la izquierda y seleccione **Cerrar "nombre del archivo PST"**.
    
[Return to top](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="more-information"></a>Más información
<a name="moreinfo"> </a>

- Es posible que un usuario recuperar un elemento eliminado de forma permanente si no ha caducado el período de retención de elementos eliminados para el elemento. Como administrador, es posible que deba especificados cuánto tiempo los elementos en la carpeta elementos recuperables están disponibles para la recuperación. Por ejemplo, puede haber una directiva que elimina cualquier cosa que ha sido en la carpeta Elementos eliminados de un usuario para 30 días y otra directiva que permite a los usuarios recuperar los elementos en la carpeta elementos recuperables hasta otro 14 días. Sin embargo, después de este 14 días, es posible que aún podrá recuperar un elemento en el buzón del usuario mediante los procedimientos descritos en este tema.
    
- Los usuarios pueden recuperar un elemento eliminado si no ha purgado y si no ha caducado el período de retención de elementos eliminados de ese elemento. Para ayudar a los usuarios recuperar elementos eliminados en sus buzones de correo, elija a uno de los siguientes temas:
    
  - [Recuperación de elementos eliminados en Outlook para Windows](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)
    
  - [Recuperar elementos eliminados en Outlook 2010](https://support.office.com/article/cd9dfe12-8e8c-4a21-bbbf-4bd103a3f1fe)
    
  - [Recuperar elementos eliminados o correo electrónico en Outlook Web App](https://support.office.com/article/c3d8fc15-eeef-4f1c-81df-e27964b7edd4)
    
  - [Restauración de los mensajes de correo electrónico eliminados en Outlook en el web](https://support.office.com/article/a8ca78ac-4721-4066-95dd-571842e9fb11)
    
  - [Recuperación de un contacto eliminado en Outlook](https://support.office.com/article/51c83288-6888-4dcd-8c99-4932daabf643)
    
  - [Restauración de los mensajes de correo electrónico eliminados en Outlook.com](https://go.microsoft.com/fwlink/p/?LinkID=623435)
    
[Return to top](recover-deleted-items-in-a-mailbox.md#__top)
  

