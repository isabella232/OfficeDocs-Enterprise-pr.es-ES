---
title: Recuperar elementos eliminados en un buzón de usuario. Ayuda para administradores
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 6/29/2018
audience: Admin
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
description: 'Este artículo está destinado a los administradores. ¿Un usuario elimina permanentemente los elementos de su buzón de Outlook? El usuario desea volver a hacerlo, pero no puede recuperarlos. Es posible que pueda recuperar los elementos purgados si no se han quitado permanentemente del buzón de correo del usuario. '
ms.openlocfilehash: 85086288d6bb153f584aa0a527100eb2d7b7de96
ms.sourcegitcommit: 8027254ab4b9ed44a5b0c336f714049859f93f3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2019
ms.locfileid: "38308605"
---
# <a name="recover-deleted-items-in-a-user-mailbox---admin-help"></a>Recuperar elementos eliminados en un buzón de usuario. Ayuda para administradores

**Este artículo está destinado a los administradores. ¿Está tratando de recuperar elementos eliminados en su propio buzón?** Pruebe con uno de los siguientes procedimientos:
- [Recuperación de elementos eliminados en Outlook para Windows](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)
- [Recuperar elementos eliminados o correo electrónico en Outlook Web App](https://support.office.com/article/c3d8fc15-eeef-4f1c-81df-e27964b7edd4)
- [Restaurar mensajes de correo electrónico eliminados en Outlook en la web](https://support.office.com/article/a8ca78ac-4721-4066-95dd-571842e9fb11)
- [Outlook.com](https://go.microsoft.com/fwlink/p/?LinkID=623435)
   
¿Un usuario elimina permanentemente los elementos de su buzón de Outlook? El usuario desea volver a hacerlo, pero no puede recuperarlos. Es posible que pueda recuperar los elementos purgados si no se han quitado permanentemente del buzón de correo del usuario. Para ello, use la herramienta de exhibición de documentos electrónicos local en Exchange Online para buscar correos electrónicos eliminados y otros elementos (como contactos, citas del calendario y tareas) en el buzón de un usuario. Si encuentra los elementos eliminados, puede exportarlos a un archivo PST (también denominado archivo de datos de Outlook), que el usuario puede usar para restaurar los elementos de nuevo en su buzón.
  
Estos son los pasos para recuperar los elementos eliminados en el buzón de un usuario. ¿Cuánto tiempo se tardará? La primera vez puede tardar 20 o 30 minutos en completar todos los pasos, en función de cuántos elementos esté intentando recuperar.
  
> [!NOTE]
> Debe ser **Administrador de Exchange** o **Administrador Global** de Office 365 o ser miembro del grupo de roles de administración de la organización en Exchange Online para realizar los pasos descritos en este artículo. Para obtener más información, vea [Información sobre los roles de administrador de Office 365](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d). 
  
## <a name="step-1-assign-yourself-ediscovery-permissions"></a>Paso 1: asignar permisos de exhibición de documentos electrónicos
<a name="step1"> </a>

El primer paso es asignarse a sí mismo los permisos necesarios en Exchange Online para poder usar la herramienta de exhibición de documentos electrónicos local para buscar en el buzón de correo de un usuario. Solo tiene que hacer esto una vez. Si tiene que buscar en otro buzón de correo en el futuro, puede omitir este paso.
  
1. [Where to sign in to Office 365 for business](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) con su cuenta profesional o educativa. 
    
2. Seleccione el icono ![del iniciador de aplicaciones el icono del iniciador de aplicaciones de Office 365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) en la esquina superior izquierda y haga clic en **Administrador**.
    
3. En el centro de administración de Microsoft 365, en el panel de navegación izquierdo, expanda **centros de administración**y, a continuación, haga clic en **Exchange**.
    
    ![Lista del centro de administración](media/7d308eb7-ba63-4156-a845-3770facc5de4.PNG)
  
4. En el centro de administración de Exchange, haga clic en **permisos**y, a continuación, en **roles de administrador**.
    
5. En la vista de lista, **Seleccione Administración de detección**y, a continuación, haga clic en **Editar**![icono](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif)de edición.
    
    ![Agregarse al grupo de roles de administración de detección en el EAC](media/e5c98e93-d6a0-40c5-a143-bac956eedaa7.png)
  
6. En **grupo de roles**, **en miembros**, haga clic en](media/8ee52980-254b-440b-99a2-18d068de62d3.gif) **Agregar**![icono de agregar.
    
7. En **seleccionar miembros**, seleccione usted en la lista de nombres, haga clic en **Agregar**y, a continuación, haga clic en **Aceptar**.
    
    > [!NOTE]
    > También puede Agregar un grupo del que sea miembro, como administración de la organización o TenantAdmins. Si agrega un grupo, se asignará a otros miembros del grupo los permisos necesarios para ejecutar la herramienta de exhibición de documentos electrónicos local. 
  
8. En **grupo de roles**, haga clic en **Guardar**.
    
9. Cierre la sesión de Office 365.
    
    Tiene que cerrar sesión antes de iniciar el siguiente paso para que se apliquen los nuevos permisos.
    
> [!CAUTION]
> Los miembros del grupo de roles Discovery Management pueden tener acceso al contenido de mensajes confidenciales. Esto incluye buscar en todos los buzones de la organización, obtener una vista previa de los resultados de la búsqueda (y otros elementos del buzón de correo), copiar los resultados en un buzón de correo de detección y exportar los resultados de la búsqueda a un archivo PST. 
  
[Return to top](recover-deleted-items-in-a-mailbox.md)
  
## <a name="step-2-search-the-users-mailbox-for-deleted-items"></a>Paso 2: buscar en el buzón del usuario los elementos eliminados
<a name="step2"> </a>

Cuando se ejecuta una búsqueda de exhibición de documentos electrónicos local, la carpeta elementos recuperables del buzón en el que se realiza la búsqueda se incluye automáticamente en la búsqueda. La carpeta elementos recuperables es donde se almacenan los elementos eliminados permanentemente hasta que se purgan (se quitan permanentemente) del buzón. Por lo tanto, si no se ha purgado un elemento, debería poder encontrarlo mediante la herramienta de exhibición de documentos electrónicos local.
  
1. [Where to sign in to Office 365 for business](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) con su cuenta profesional o educativa. 
    
2. Seleccione el icono ![del iniciador de aplicaciones el icono del iniciador de aplicaciones de Office 365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) en la esquina superior izquierda y haga clic en **Administrador**.
    
3. En el centro de administración de Microsoft 365, en el panel de navegación izquierdo, expanda **Administración**y, a continuación, haga clic en **Exchange**.
    
4. En el centro de administración de Exchange, haga clic en **Administración de cumplimiento**, haga clic en **conservación de &amp; exhibición de**documentos electrónicos local y, a continuación, haga clic en **nuevo**![icono](media/8ee52980-254b-440b-99a2-18d068de62d3.gif)agregar.
    
    ![En la página Administración de cumplimiento de la EAC, haga clic en exhibición de documentos electrónicos local y retención.](media/9d9ff0f5-b9be-45b8-8b5e-6037a856b0a8.png)
  
5. En la página **nombre y descripción** , escriba un nombre para la búsqueda (por ejemplo, el nombre del usuario del que está recuperando el correo electrónico), una descripción opcional y, a continuación, haga clic en **siguiente**.
    
6. En la página **buzones** , haga clic en **especificar buzones para buscar**y, a continuación,](media/8ee52980-254b-440b-99a2-18d068de62d3.gif)haga clic en **Agregar**![icono de agregar.
    
    ![Haga clic en especificar buzones para buscar en un buzón de manifiestan](media/83879a40-5e5c-49a8-be3b-c0023d197588.png)
  
7. Busque y seleccione el nombre del usuario para el que está recuperando el correo electrónico eliminado, haga clic en **Agregar**y, a continuación, haga clic en **Aceptar**.
    
8. Haga clic en **Siguiente**.
    
    Se muestra la página de **consulta de búsqueda** . Aquí es donde define los criterios de búsqueda que le ayudarán a encontrar los elementos que faltan en el buzón del usuario. 
    
9. En la página **Consulta de búsqueda**, complete los campos siguientes: 
    
  - **Incluir todo el contenido** Seleccione esta opción para incluir todo el contenido en el buzón del usuario en los resultados de la búsqueda. Si selecciona esta opción, no puede especificar más criterios de búsqueda. 
    
  - **Filtrado basado en criterios** Seleccione esta opción para especificar los criterios de búsqueda, incluidas palabras clave, fechas de inicio y finalización, direcciones de remitente y destinatario, y tipos de mensaje. 
    
    ![Crear un quiera basado en criterios como palabras clave, intervalo de fechas, destinatarios y tipos de mensajes](media/ee47b833-9122-46a0-85e6-fcbe25be0dd5.png)
  
|**Field**|**Use esta para...**|
|:-----|:-----|
|![Número uno en un círculo rosa](media/a4da261d-2516-48c5-b58a-9c452b9086b8.png)           <br/> |Especifique palabras clave, un intervalo de fechas, destinatarios y tipos de mensaje.  <br/> |
|![Número dos en un círculo rosa.](media/de3c1ab4-4f01-4026-b1ba-3265bdb32a89.png)           <br/> |Busque mensajes con palabras clave o frases y use operadores lógicos como **y** o **o**.  <br/> |
|![Número 3 en un círculo rosa.](media/60fa378c-6ac1-4cbd-a782-2fa7ca619dc6.png)           <br/> |Buscar mensajes enviados o recibidos en un intervalo de fechas.  <br/> |
|![Número 4 en un círculo rosa.](media/1a0ff2ce-0942-405a-94e3-9bfeb1e5059e.png)           <br/> |Buscar mensajes recibidos o enviados a personas específicas.  <br/> |
|![Número cinco en un círculo rosa.](media/878cc815-0165-49ba-a1ee-9236e5980403.png)           <br/> |Busque todos los tipos de mensajes o seleccione unos específicos.  <br/> |
   
   > [!TIP]
   >  Estas son algunas sugerencias sobre cómo crear una consulta de búsqueda para encontrar los elementos que faltan. Intente obtener toda la información del usuario para ayudarle a crear una consulta de búsqueda para que pueda encontrar lo que está buscando. Si no está seguro de cómo encontrar un mensaje que falta, considere la posibilidad de usar la opción **incluir todo el contenido** . Los resultados de la búsqueda incluirán todos los elementos de la carpeta elementos recuperables del usuario, incluida la carpeta oculta (denominada la carpeta purga) que contiene elementos purgados por el usuario. A continuación, puede ir al paso 3, copiar los resultados en un buzón de correo de detección y ver el mensaje en la carpeta oculta. Si sabe aproximadamente Cuándo el usuario envió o recibió originalmente el mensaje que falta, use las opciones **especificar fecha de inicio** y **especificar fecha de finalización** para proporcionar un intervalo de fechas. Se devolverán todos los mensajes enviados o recibidos por el usuario dentro del intervalo de fechas. Especificar un intervalo de fechas es una buena forma de restringir los resultados de la búsqueda. Si sabe quién envió el correo electrónico que falta, use el cuadro **de** para especificar a este remitente. Si desea restringir los resultados de la búsqueda a diferentes tipos de elementos del buzón de correo, haga clic en **seleccionar tipos de mensajes**, haga clic en **seleccionar los tipos de mensajes para buscar**y, a continuación, elija un tipo de mensaje específico para buscar. Por ejemplo, puede buscar sólo en los elementos de calendario o los contactos. Esta es una captura de pantalla de los diferentes tipos de mensajes que puede buscar; el valor predeterminado es buscar todos los tipos de mensajes. 
  
   Haga clic en **siguiente** cuando haya completado la página de **consulta de búsqueda** . 
    
10. En la página **configuración de conservación local** , haga clic en **Finalizar** para iniciar la búsqueda. Para recuperar el correo electrónico eliminado, no hay razón para poner el buzón de correo del usuario en retención. 
    
    Una vez iniciada la búsqueda, Exchange mostrará una estimación del tamaño y la cantidad totales de elementos que devolverá la búsqueda en función de los criterios especificados.
    
11. Seleccione la búsqueda que acaba de crear y ****![haga clic](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) en actualizar actualización para actualizar la información que se muestra en el panel de detalles. El estado de **Estimated Succeeded** indica que la búsqueda ha finalizado. Exchange también muestra una estimación del número total de elementos (y su tamaño) encontrados por la búsqueda en función de los criterios de búsqueda especificados en el paso 9. 
    
12. En el panel de detalles, haga clic en **vista previa de resultados** de la búsqueda para ver los elementos que se encontraron. Esto puede ayudarle a identificar los elementos que está buscando. Si encuentra los elementos que está intentando recuperar, vaya al paso 4 para exportar los resultados de la búsqueda a un archivo PST. 
    
    ![Haga clic en vista previa de resultados de búsqueda para ver el elemento que está intentando recuperar](media/a2cea921-dafa-45d6-97d4-ae45a226b8d3.png)
  
13. Si no encuentra lo que está buscando, puede revisar los criterios de búsqueda seleccionando la búsqueda, haciendo clic en **Editar**![icono](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif)editar y, a continuación, haciendo clic en **consulta de búsqueda**. Cambie los criterios de búsqueda y vuelva a ejecutar la búsqueda.
    
[Return to top](recover-deleted-items-in-a-mailbox.md)
  
## <a name="optional-step-3-copy-the-search-results-to-a-discovery-mailbox"></a>Opcional Paso 3: copiar los resultados de la búsqueda en un buzón de correo de detección
<a name="step3"> </a>

Si no puede encontrar un elemento al obtener una vista previa de los resultados de la búsqueda o si desea ver qué elementos se encuentran en la carpeta elementos recuperables del usuario, puede copiar los resultados de la búsqueda en un buzón especial (denominado buzón de correo de detección) y, a continuación, abrir el buzón en Outlook en la web t o ver los elementos reales. La mejor razón para copiar los resultados de la búsqueda es que pueda ver los elementos de la carpeta elementos recuperables del usuario. Es muy probable que el elemento que está intentando recuperar se encuentre en la subcarpeta depuraciones. 
  
1. En el centro de administración de Exchange, vaya a **conservación de exhibición &amp; de documentos electrónicos local de** **Administración** \> de cumplimiento.
    
2. En la lista de búsquedas, seleccione la búsqueda que ha creado en el paso 2.
    
3. Haga clic **en buscar búsqueda**y, a continuación, haga clic en **copiar resultados de búsqueda** en la lista desplegable.![](media/c94e8591-7044-4650-a0d1-c57c0633ab4f.png) 
    
    ![Haga clic en buscar y, a continuación, en copiar resultados de búsqueda](media/7888df82-94b4-4e44-8a53-f66854dc7c86.png)
  
4. En la página **copiar resultados de búsqueda** , haga clic en **examinar**.
    
    ![Deje las casillas desactivadas al recuperar los elementos eliminados](media/37f27999-a5b2-4fed-87e2-bad6dc23cdae.png)
  
5. En **nombre para mostrar**, haga clic en **buzón de búsqueda de detección**y, a continuación, en **Aceptar**.
    
    ![Copiar los resultados de la búsqueda en el buzón de búsqueda de detección predeterminado](media/36e8ef47-0035-4982-9ed6-426719c5f9ec.png)
  
    > [!NOTE]
    > El buzón de búsqueda de detección es un buzón de correo de detección predeterminado que se crea automáticamente en su organización de Office 365. 
  
6. De nuevo en la página **copiar resultados de búsqueda** , haga clic en **copiar** para iniciar el proceso de copia de los resultados de la búsqueda en el buzón de búsqueda de detección. 
    
    ![Haga clic en copiar para copiar los resultados de la búsqueda en el buzón de búsqueda de detección](media/71307a9d-f7a1-4e01-ae37-1d49040cc3fd.png)
  
7. Haga ****![clic en](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) actualizar actualización para actualizar la información sobre el estado de copia que se muestra en el panel de detalles. 
    
8. Una vez completada la copia, haga clic en **abrir** para abrir el buzón de búsqueda de detección para ver los resultados de la búsqueda. 
    
    ![Haga clic en abrir para ir al buzón de búsqueda de detección para ver los resultados de la búsqueda](media/6cc81e0f-ceed-4464-9040-79b6f920de35.png)
  
    Los resultados de la búsqueda que se copian en el buzón de búsqueda de detección se colocan en una carpeta que tiene el mismo nombre que la búsqueda de exhibición de documentos electrónicos local. Puede hacer clic en una carpeta para mostrar los elementos de esa carpeta.
    
    ![Resultados de búsqueda en el buzón de búsqueda de detección; los elementos de la carpeta purgas solo los puede recuperar un administrador](media/2ef8e5fb-3e63-4f62-938e-307efe9f6998.gif)
  
    Cuando se ejecuta una búsqueda, también se busca en la carpeta elementos recuperables del usuario. Esto significa que si los elementos de la carpeta elementos recuperables cumplen los criterios de búsqueda, se incluirán en los resultados de la búsqueda. Los elementos de la carpeta eliminaciones son elementos eliminados permanentemente por el usuario (eliminando un elemento de la carpeta elementos eliminados o seleccionándolo y presionando **Mayús + Supr**. Un usuario puede usar la herramienta recuperar elementos eliminados de Outlook o Outlook en la web para recuperar elementos de la carpeta eliminaciones. Los elementos de la carpeta purgas son elementos que el usuario ha purgado mediante la herramienta recuperar elementos eliminados o elementos que una directiva ha aplicado automáticamente al buzón. En cualquier caso, solo un administrador puede recuperar elementos de la carpeta depuraciones. 
    
    > [!TIP]
    > Si un usuario no encuentra un elemento eliminado mediante la herramienta elementos recuperables, pero ese elemento todavía se puede recuperar (lo que significa que no se ha quitado de forma permanente del buzón de correo), es más probable que se encuentre en la carpeta depuraciones. Por lo tanto, asegúrese de buscar en la carpeta purgas el elemento eliminado que está intentando recuperar para un usuario. 
  
[Return to top](recover-deleted-items-in-a-mailbox.md)
  
## <a name="step-4-export-the-search-results-to-a-pst-file"></a>Paso 4: exportar los resultados de la búsqueda a un archivo PST
<a name="step4"> </a>

Una vez que encuentre el elemento que está intentando recuperar para un usuario, el siguiente paso consiste en exportar los resultados de la búsqueda que ejecutó en el paso 2 a un archivo PST. El usuario usará este archivo PST en el siguiente paso para restaurar el elemento eliminado en su buzón de correo.
  
1. En el centro de administración de Exchange, vaya a **conservación de exhibición &amp; de documentos electrónicos local de** **Administración** \> de cumplimiento.
    
2. En la lista de búsquedas, seleccione la búsqueda que ha creado en el paso 2.
    
3. Haga clic en **exportar a un archivo pst**.
    
    ![Haga clic en exportar a un archivo PST](media/4e59ae17-4541-43f4-a6d1-1f8b9ba9404b.png)
  
4. Si se le pide que instale la herramienta de exportación de exhibición de documentos electrónicos, haga clic en **Ejecutar**.
    
5. En la herramienta de exportación de PST de eDiscovery, haga clic en **examinar** para especificar la ubicación en la que desea descargar el archivo pst. 
    
    ![La herramienta de exportación de PST de eDiscovery](media/17274d27-992e-4034-8133-8f793f554e6c.png)
  
    Puede omitir las opciones para habilitar la desduplicación e incluir elementos no aptos para la búsqueda.
    
6. Haga clic en **iniciar** para descargar el archivo pst en su equipo. 
    
    La **herramienta de exportación de PST de eDiscovery** muestra información de estado sobre el proceso de exportación. Una vez completada la exportación, puede tener acceso al archivo en la ubicación donde se ha descargado. 
    
[Return to top](recover-deleted-items-in-a-mailbox.md)
  
## <a name="step-5-restore-the-recovered-items-to-the-users-mailbox"></a>Paso 5: restaurar los elementos recuperados en el buzón de correo del usuario
<a name="step5"> </a>

El último paso consiste en usar el archivo PST que se exportó en el paso 4 para restaurar los elementos recuperados en el buzón de correo del usuario. Después de enviar el archivo PST al usuario, el resto de este paso es realizado por el usuario para abrir el archivo PST y mover los elementos recuperados a otra carpeta en su buzón. Para obtener instrucciones paso a paso, también puede enviar al usuario un vínculo a este tema: [abrir y cerrar archivos de datos de Outlook (. pst)](https://support.office.com/article/381b776d-7511-45a0-953a-0935c79d24f2). O bien, puede enviar un vínculo al usuario a la siguiente sección [Restaurar elementos eliminados a un buzón de correo mediante un archivo pst](recover-deleted-items-in-a-mailbox.md#restoredeleteditems) a continuación y pedirle que realice estos pasos. 
  
 **Enviar el archivo PST al usuario**
  
El último paso que debe realizar es enviar al usuario el archivo PST que se exportó en el paso 4. Hay varias formas de hacerlo:
  
- Adjunte el archivo PST a un mensaje de correo electrónico. Si Outlook está configurado para bloquear los archivos PST, tendrá que comprimir el archivo y, a continuación, adjuntarlo al mensaje. A continuación se describe cómo:
    
1. En el explorador de Windows o en el explorador de archivos, vaya al archivo PST.
    
2. Haga clic con el botón derecho en el archivo y, después, seleccione **Enviar a** \> **carpeta comprimida (en zip)**. Windows crea un nuevo archivo zip y le asigna el mismo nombre que el archivo PST.
    
3. Adjunte el archivo PST comprimido a un mensaje de correo electrónico y envíelo al usuario, quien podrá descomprimir el archivo simplemente haciendo clic en él.
    
- Copie el archivo PST en una carpeta compartida al que el usuario pueda tener acceso y recuperarlo.
    
Los pasos de la siguiente sección son realizados por el usuario para restaurar los elementos eliminados en su buzón de correo.
  
 <a name="restoredeleteditems"></a>
**Restaurar elementos eliminados en un buzón con un archivo PST**
  
Tiene que usar la aplicación de escritorio de Outlook para restaurar un elemento eliminado mediante un archivo PST. No puede usar Outlook Web App u Outlook en la web para abrir un archivo PST.
  
1. En Outlook 2013 o en Outlook 2016, haga clic en la pestaña **archivo** . 
    
2. Haga clic en ** &amp; abrir exportar**y, a continuación, en **Abrir archivo de datos de Outlook**.
    
3. Vaya a la ubicación donde guardó el archivo PST que envió el administrador.
    
4. Seleccione el archivo PST y, a continuación, haga clic en **abrir**.
    
    El archivo PST aparece en la barra de navegación izquierda en Outlook.
    
    ![El archivo PST aparece en la barra de navegación izquierda en Outlook](media/c9389392-d08a-4aa7-848c-4986d448b0f2.png)
  
5. Haga clic en las flechas para expandir el archivo PST y las carpetas que hay debajo para localizar el elemento que desea recuperar.
    
    ![Busque en la carpeta purgas el elemento que desee recuperar](media/d4e372d9-ac23-4e95-8639-d8da690fefa7.png)
  
    > [!TIP]
    > Busque en la carpeta purgas el elemento que desee recuperar. Se trata de una carpeta oculta a la que se mueven los elementos purgados. Es probable que el elemento que el administrador haya recuperado esté en esta carpeta. 
  
6. Haga clic con el botón secundario en el elemento que desee recuperar y, a continuación, haga clic en **mover** \> **otra carpeta**.
    
    ![Haga clic en mover y, a continuación, seleccione otra carpeta](media/090063df-2aa0-444a-8e47-abd6fe6cf7a8.png)
  
7. Para mover el elemento a la bandeja de entrada, haga clic en **bandeja de entrada**y, a continuación, en **Aceptar**.
    
    **Sugerencia:** Para recuperar otros tipos de elementos, realice una de las siguientes acciones: 
    
  - Para recuperar un elemento de calendario, haga clic con el botón secundario en él y, a continuación, haga clic en **mover** \> **calendario**de **otras carpetas** \> .
    
  - Para recuperar un contacto, haga clic en él con el botón derecho y, a continuación, haga clic en **mover** \> **otros** \> **contactos**de carpeta.
    
  - Para recuperar una tarea, haga clic con el botón secundario en ella y, a continuación, haga clic en **mover** \> **otras** \> **tareas**de carpeta.
    
![Seleccionar una carpeta para mover otros tipos de elementos](media/f8290131-43f2-46f1-bc07-228c2d83b96c.png)
  
   > [!NOTE]
   > Los elementos de calendario, los contactos y las tareas se encuentran directamente en la carpeta purgas y no en una subcarpeta calendario, contactos o tareas. Sin embargo, puede ordenar por **tipo** para agrupar tipos similares de elementos. 
    
8. Cuando haya terminado de recuperar los elementos eliminados, haga clic con el botón derecho en el archivo PST en la barra de navegación izquierda y seleccione **Cerrar "nombre de archivo pst"**.
    
[Return to top](recover-deleted-items-in-a-mailbox.md)
  
## <a name="more-information"></a>Más información
<a name="moreinfo"> </a>

- Es posible que un usuario pueda recuperar un elemento eliminado permanentemente si el período de retención de elementos eliminados para el elemento no ha expirado. Como administrador, es posible que haya especificado el tiempo que los elementos de la carpeta elementos recuperables estarán disponibles para la recuperación. Por ejemplo, puede haber una directiva que elimine todo lo que haya en la carpeta elementos eliminados de un usuario durante 30 días y otra directiva que permita a los usuarios recuperar los elementos de la carpeta elementos recuperables durante un máximo de 14 días. Sin embargo, después de estos 14 días, es posible que pueda recuperar un elemento en el buzón de un usuario mediante los procedimientos de este tema.
    
- Los usuarios pueden recuperar un elemento eliminado si todavía no se ha purgado y si no ha expirado el período de retención de elementos eliminados para ese elemento. Para ayudar a los usuarios a recuperar los elementos eliminados en su buzón de correo, señale a uno de los siguientes temas:
    
  - [Recuperación de elementos eliminados en Outlook para Windows](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)
    
  - [Recuperar elementos eliminados en Outlook 2010](https://support.office.com/article/cd9dfe12-8e8c-4a21-bbbf-4bd103a3f1fe)
    
  - [Recuperar elementos eliminados o correo electrónico en Outlook Web App](https://support.office.com/article/c3d8fc15-eeef-4f1c-81df-e27964b7edd4)
    
  - [Restaurar mensajes de correo electrónico eliminados en Outlook en la web](https://support.office.com/article/a8ca78ac-4721-4066-95dd-571842e9fb11)
    
  - [Recuperar un contacto eliminado en Outlook](https://support.office.com/article/51c83288-6888-4dcd-8c99-4932daabf643)
    
  - [Restaurar mensajes de correo electrónico eliminados en Outlook.com](https://go.microsoft.com/fwlink/p/?LinkID=623435)
    
[Return to top](recover-deleted-items-in-a-mailbox.md)
  

