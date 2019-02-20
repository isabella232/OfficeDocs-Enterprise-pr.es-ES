---
title: Instalar y ejecutar la herramienta IdFix de Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: get-started-article
f1_keywords:
- O365E_HRCSetupAADConnectIDFixLM617036
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: Cómo instalar y ejecutar la herramienta IdFix de Office 365 para ayudar a limpiar Active Directory antes de sincronizarlo con Office 365.
ms.openlocfilehash: a35b2a476f2b30eccc955b980eda6315b146af27
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085409"
---
# <a name="install-and-run-the-office-365-idfix-tool"></a><span data-ttu-id="f4fcc-103">Instalar y ejecutar la herramienta IdFix de Office 365</span><span class="sxs-lookup"><span data-stu-id="f4fcc-103">Install and run the Office 365 IdFix tool</span></span>

<span data-ttu-id="f4fcc-104">IdFix identifica errores como duplicados y problemas de formato en su directorio antes de sincronizar con Office 365.</span><span class="sxs-lookup"><span data-stu-id="f4fcc-104">IdFix identifies errors such as duplicates and formatting problems in your directory before you synchronize to Office 365.</span></span> 
  
<span data-ttu-id="f4fcc-105">Para finalizar esta tarea correctamente, debe sentirse cómodo trabajando con objetos de usuario, grupo y contacto en Active Directory.</span><span class="sxs-lookup"><span data-stu-id="f4fcc-105">To finish this task successfully, you should be comfortable working with user, group, and contact objects in Active Directory.</span></span>
  
<span data-ttu-id="f4fcc-p101">Si no puede completar esta tarea, hay un par de cosas que puede hacer. Estos métodos pueden ser más sencillos, pero también pueden tardar más tiempo o tener otros inconvenientes. Son los siguientes:</span><span class="sxs-lookup"><span data-stu-id="f4fcc-p101">If you can't complete this task, there are a couple of other things you can do. These methods might be easier, but they might also take longer or have other drawbacks. They are:</span></span>
  
- <span data-ttu-id="f4fcc-p102">**Ejecutar la sincronización de directorios sin ejecutar IdFix.** Puede sincronizar el directorio sin ejecutar la herramienta IdFix, pero no lo recomendamos. La corrección de errores antes de sincronizar requiere menos tiempo y suele proporcionar una transición más fluida a la nube.</span><span class="sxs-lookup"><span data-stu-id="f4fcc-p102">**Run directory synchronization without running IdFix.** You can synchronize your directory without running the IdFix tool, but we don't recommend it. Fixing errors before you synchronize takes less time and often provides a smoother transition to the cloud.</span></span> 
- <span data-ttu-id="f4fcc-p103">**Contratar a un consultor.** Solicitar ayuda a un experto puede poner en marcha a sus usuarios y sincronizar el directorio rápidamente.</span><span class="sxs-lookup"><span data-stu-id="f4fcc-p103">**Hire a consultant.** Getting expert help can get your users up and running quickly and your directory synchronized.</span></span> 
    
## <a name="what-you-need-to-run-idfix"></a><span data-ttu-id="f4fcc-114">Lo que necesita para ejecutar IdFix</span><span class="sxs-lookup"><span data-stu-id="f4fcc-114">What you need to run IdFix</span></span>

<span data-ttu-id="f4fcc-p104">La forma más sencilla de obtener un IdFix y ejecutarlo es instalarlo en un equipo que se haya unido a su dominio. Si lo desea, puede ejecutarlo en el controlador de dominio, pero no es necesario.</span><span class="sxs-lookup"><span data-stu-id="f4fcc-p104">The easiest way to get IdFix up and running is to install it on a computer that is joined to your domain. You can run it on the domain controller if you want, but it's not necessary.</span></span>
  
### <a name="idfix-hardware-requirements"></a><span data-ttu-id="f4fcc-117">Requisitos de hardware de IdFix</span><span class="sxs-lookup"><span data-stu-id="f4fcc-117">IdFix hardware requirements</span></span>

<span data-ttu-id="f4fcc-118">El equipo donde instale IdFix debe cumplir estos requisitos mínimos de hardware:</span><span class="sxs-lookup"><span data-stu-id="f4fcc-118">The computer where you install IdFix needs to meet these minimum hardware requirements:</span></span>
  
- <span data-ttu-id="f4fcc-119">4 GB de RAM</span><span class="sxs-lookup"><span data-stu-id="f4fcc-119">4 GB RAM</span></span>
- <span data-ttu-id="f4fcc-120">2 GB de espacio en disco duro</span><span class="sxs-lookup"><span data-stu-id="f4fcc-120">2 GB of hard disk space</span></span>
    
### <a name="idfix-software-requirements"></a><span data-ttu-id="f4fcc-121">Requisitos de software de IdFix</span><span class="sxs-lookup"><span data-stu-id="f4fcc-121">IdFix software requirements</span></span>

<span data-ttu-id="f4fcc-p105">El equipo donde instale IdFix debe unirse al mismo dominio de Active Directory desde el que desea sincronizar usuarios con Office 365. El equipo también debe tener instalado .NET Framework 4,0.</span><span class="sxs-lookup"><span data-stu-id="f4fcc-p105">The computer where you install IdFix needs to be joined to the same Active Directory domain from which you want to synchronize users to Office 365. The computer also needs to have .NET Framework 4.0 installed.</span></span> 
  
<span data-ttu-id="f4fcc-p106">Si ejecuta Windows Server 2008 o Windows Server 2012, es probable que .NET Framework ya esté instalado. Si no es así, puede [Descargar .net 4,0 desde el centro de descarga](https://go.microsoft.com/fwlink/p/?LinkId=400475) o a través de Windows Update.</span><span class="sxs-lookup"><span data-stu-id="f4fcc-p106">If you are running Windows Server 2008 or Windows Server 2012, then .NET Framework is probably already installed. If not, you can [download .NET 4.0 from the download center](https://go.microsoft.com/fwlink/p/?LinkId=400475) or via Windows Update.</span></span> 
  
### <a name="idfix-permissions-requirements"></a><span data-ttu-id="f4fcc-126">Requisitos de permisos de IdFix</span><span class="sxs-lookup"><span data-stu-id="f4fcc-126">IdFix permissions requirements</span></span>

<span data-ttu-id="f4fcc-127">La cuenta de usuario que se utiliza para ejecutar IdFix debe tener acceso de lectura y escritura en el directorio.</span><span class="sxs-lookup"><span data-stu-id="f4fcc-127">The user account that you use to run IdFix needs to have read/write access to the directory.</span></span>
  
<span data-ttu-id="f4fcc-p107">Si no está seguro de si su cuenta de usuario cumple estos requisitos y no está seguro de cómo comprobarla, puede instalar y ejecutar IdFix. Si su cuenta de usuario no tiene los permisos adecuados, IdFix simplemente mostrará un error cuando intente ejecutarla.</span><span class="sxs-lookup"><span data-stu-id="f4fcc-p107">If you aren't sure if your user account meets these requirements, and you're not sure how to check, you can still install and run IdFix. If your user account doesn't have the right permissions, IdFix will simply display an error when you try to run it.</span></span>
  
## <a name="install-idfix"></a><span data-ttu-id="f4fcc-130">Instalar IdFix</span><span class="sxs-lookup"><span data-stu-id="f4fcc-130">Install IdFix</span></span>

<span data-ttu-id="f4fcc-131">Para instalar IdFix, descargue y descomprima **idfix. exe**:</span><span class="sxs-lookup"><span data-stu-id="f4fcc-131">To install IdFix, download and unzip **IdFix.exe**:</span></span> 
  
1. <span data-ttu-id="f4fcc-132">Inicie sesión en el equipo donde quiere instalar la herramienta IdFix.</span><span class="sxs-lookup"><span data-stu-id="f4fcc-132">Log on to the computer where you want to install the IdFix tool.</span></span>
    
2. <span data-ttu-id="f4fcc-133">Vaya al sitio de descarga de Microsoft para la [herramienta de corrección de errores de sincronización de directorios de IdFix](https://go.microsoft.com/fwlink/?linkid=867219).</span><span class="sxs-lookup"><span data-stu-id="f4fcc-133">Go to the Microsoft download site for the [IdFix DirSync Error Remediation Tool](https://go.microsoft.com/fwlink/?linkid=867219).</span></span>
    
3. <span data-ttu-id="f4fcc-134">Elija **Descargar**.</span><span class="sxs-lookup"><span data-stu-id="f4fcc-134">Choose **Download**.</span></span>
    
4. <span data-ttu-id="f4fcc-135">Cuando se le pida, elija **Ejecutar**.</span><span class="sxs-lookup"><span data-stu-id="f4fcc-135">When prompted, choose **Run**.</span></span>
    
5. <span data-ttu-id="f4fcc-p108">En el cuadro de diálogo **WinZip Self-Extractor** , en el cuadro de texto **descomprimir en carpeta** , escriba o busque la ubicación en la que desea instalar la herramienta IdFix. De forma predeterminada, IdFix se instala `C:\Deployment Tools\`en.</span><span class="sxs-lookup"><span data-stu-id="f4fcc-p108">On the **WinZip Self-Extractor** dialog box, in the **Unzip to folder** text box, type or browse to the location where you want to install the IdFix tool. By default, IdFix is installed into `C:\Deployment Tools\`.</span></span> 
    
6. <span data-ttu-id="f4fcc-138">Elija **descomprimir**.</span><span class="sxs-lookup"><span data-stu-id="f4fcc-138">Choose **Unzip**.</span></span>
    
## <a name="run-the-idfix-tool"></a><span data-ttu-id="f4fcc-139">Ejecutar la herramienta IdFix</span><span class="sxs-lookup"><span data-stu-id="f4fcc-139">Run the IdFix tool</span></span>

<span data-ttu-id="f4fcc-140">Después de instalar IdFix, ejecute la herramienta para buscar problemas en el directorio:</span><span class="sxs-lookup"><span data-stu-id="f4fcc-140">After you install IdFix, run the tool to search for problems in your directory:</span></span>
  
1. <span data-ttu-id="f4fcc-141">Con una cuenta que tenga acceso de lectura y escritura en el directorio, inicie sesión en el equipo donde ha instalado IdFix.</span><span class="sxs-lookup"><span data-stu-id="f4fcc-141">Using an account that has read/write access to the directory, log on to the computer where you installed IdFix.</span></span>
    
2. <span data-ttu-id="f4fcc-p109">En el explorador de archivos, vaya a la ubicación en la que ha instalado IdFix. Si eligió la carpeta predeterminada durante la instalación, vaya a `C:\Deployment Tools\IdFix`.</span><span class="sxs-lookup"><span data-stu-id="f4fcc-p109">In File Explorer, go to the location where you installed IdFix. If you chose the default folder during installation, go to `C:\Deployment Tools\IdFix`.</span></span>
    
3. <span data-ttu-id="f4fcc-144">Haga doble clic en **IdFix.exe**.</span><span class="sxs-lookup"><span data-stu-id="f4fcc-144">Double-click **IdFix.exe**.</span></span> 
    
    ![Elija el archivo IdFix. exe.](media/a9387bbc-991f-41c2-a500-45e3ce574285.JPG)
  
4. <span data-ttu-id="f4fcc-p110">De forma predeterminada, IdFix usa el conjunto de reglas multiInquilino para probar las entradas del directorio. Este es el conjunto de reglas correcto para la mayoría de los clientes de Office 365. Sin embargo, si es cliente de Office 365 dedicado o ITAR (tráfico internacional en las regulaciones de brazos), puede configurar IdFix para usar el conjunto de reglas dedicado en su lugar. Si no está seguro de qué tipo de cliente es, puede omitir este paso de manera segura. Para establecer el conjunto de reglas en dedicado, haga clic en el icono de engranaje en la barra de menús y, a continuación, elija **dedicado**.</span><span class="sxs-lookup"><span data-stu-id="f4fcc-p110">By default, IdFix uses the Multi-Tenant rule set to test the entries in your directory. This is the right rule set for most Office 365 customers. However, if you are an Office 365 Dedicated or ITAR (International Traffic in Arms Regulations) customer, you can configure IdFix to use the Dedicated rule set instead. If you aren't sure what type of customer you are, you can safely skip this step. To set the rule set to Dedicated, click the gear icon in the menu bar and then choose **Dedicated**.</span></span>
    
5. <span data-ttu-id="f4fcc-151">Elija **consultar**.</span><span class="sxs-lookup"><span data-stu-id="f4fcc-151">Choose **Query**.</span></span>
    
    ![Seleccione consulta en IdFix.](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. <span data-ttu-id="f4fcc-153">De forma predeterminada, IdFix busca errores en todo el directorio.</span><span class="sxs-lookup"><span data-stu-id="f4fcc-153">By default, IdFix searches the entire directory for errors.</span></span>
    
    <span data-ttu-id="f4fcc-p111">En función del tamaño del directorio, la ejecución de la consulta puede tardar unos minutos. Puede ver el progreso en la parte inferior de la ventana principal de la herramienta. Si hace clic en **Cancelar**, deberá reiniciar desde el principio.</span><span class="sxs-lookup"><span data-stu-id="f4fcc-p111">Depending on the size of your directory, running the query can take a while. You can watch the progress at the bottom of the tool's main window. If you click **Cancel**, you'll need to restart from the beginning.</span></span>
    
    ![Número de consultas y errores de IdFix.](media/da0198a0-7d4d-4afe-a256-e82f1330ada5.JPG)
  
7. <span data-ttu-id="f4fcc-p112">Después de que IdFix complete la consulta, puede seguir adelante y sincronizar su directorio si no hay errores. Si hay errores en el directorio, se recomienda que los solucione antes de sincronizar. Si desea información más específica acerca de los tipos de errores y las recomendaciones sobre la mejor manera de solucionarlos, vea los vínculos que se encuentra al final de este tema.</span><span class="sxs-lookup"><span data-stu-id="f4fcc-p112">After IdFix completes the query, you can go ahead and synchronize your directory if there are no errors. If there are errors in your directory, it is recommended that you fix them before you synchronize. If you want more specific information about types of errors and recommendations about the best way to fix each of them, see the links at the end of this topic.</span></span> 
    
    <span data-ttu-id="f4fcc-161">Aunque no es obligatorio corregir los errores antes de sincronizar, se recomienda encarecidamente revisar al menos todos los errores devueltos por IdFix.</span><span class="sxs-lookup"><span data-stu-id="f4fcc-161">While it is not mandatory to fix the errors before you synchronize, we strongly recommend that you at least review all the errors returned by IdFix.</span></span>
    
    <span data-ttu-id="f4fcc-162">Cada error se muestra en una fila independiente en la ventana principal de la herramienta.</span><span class="sxs-lookup"><span data-stu-id="f4fcc-162">Each error is displayed in a separate row in the tool's main window .</span></span> 
    
8. <span data-ttu-id="f4fcc-p113">Si está de acuerdo con el cambio sugerido en la columna **UPDATE**, en la columna **ACTION** seleccione lo que quiere que IdFix haga para implementar el cambio y luego haga clic en **Aplicar**. Al hacer clic en **Aplicar**, la herramienta hace los cambios en el directorio.</span><span class="sxs-lookup"><span data-stu-id="f4fcc-p113">If you agree with the suggested change in the **UPDATE** column, in the **ACTION** column select what you want IdFix to do to implement the change and then click **Apply**. When you click **Apply**, the tool makes the changes in the directory.</span></span>
    
    <span data-ttu-id="f4fcc-p114">No es necesario hacer clic en **aplicar** después de cada actualización. En su lugar, puede corregir varios errores antes de hacer clic en **aplicar** y IdFix los cambiará a la vez. Puede ordenar los errores por tipo de error haciendo clic en **error** en la parte superior de la columna que enumera los tipos de error.</span><span class="sxs-lookup"><span data-stu-id="f4fcc-p114">You don't have to click **Apply** after each update. Instead, you can fix several errors before you click **Apply** and IdFix will change them all at the same time. You can sort the errors by error type by clicking **ERROR** at the top of the column that lists the error types.</span></span> 
    
    <span data-ttu-id="f4fcc-p115">Una estrategia consiste en corregir todos los errores del mismo tipo; por ejemplo, primero Corrija todos los duplicados y aplíquelos. A continuación, corrija los errores de formato de carácter y así sucesivamente. Cada vez que se aplican los cambios, la herramienta IdFix crea un archivo de registro independiente que se puede usar para deshacer los cambios en caso de que se cometa un error. El [registro de transacciones](idfix-transaction-log.md) se almacena en la carpeta en la que ha instalado IdFix.  _C:\Deployment Tools\IdFix_ de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="f4fcc-p115">One strategy is to fix all the errors of the same type; for example, fix all the duplicates first, and apply them. Next, fix the character format errors, and so on. Each time you apply the changes, the IdFix tool creates a separate log file that you can use to undo your changes in case you make a mistake. The [transaction log](idfix-transaction-log.md) is stored in the folder that you installed IdFix in.  _C:\Deployment Tools\IdFix_ by default.</span></span> 
    
    ![Corregir errores en IdFix.](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. <span data-ttu-id="f4fcc-p116">Una vez que se hayan realizado todos los cambios en el directorio, ejecute IdFix de nuevo para asegurarse de que las correcciones que ha realizado no han introducido nuevos errores. Puede repetir estos pasos tantas veces como sea necesario. Es una buena idea pasar por el proceso varias veces antes de sincronizar.</span><span class="sxs-lookup"><span data-stu-id="f4fcc-p116">After all of your changes are made to the directory, run IdFix again to ensure that the fixes you made didn't introduce new errors. You can repeat these steps as many times as you need to. It's a good idea to go through the process a few times before you synchronize.</span></span>
    
## <a name="i-want-to-refine-my-search-or-dig-deeper-into-the-errors-what-else-can-i-do-with-idfix"></a><span data-ttu-id="f4fcc-177">Quiero limitar la búsqueda o profundizar en los errores, ¿qué más puedo hacer con IdFix?</span><span class="sxs-lookup"><span data-stu-id="f4fcc-177">I want to refine my search or dig deeper into the errors, what else can I do with IdFix?</span></span>

<span data-ttu-id="f4fcc-178">Encontrará información detallada en los temas siguientes:</span><span class="sxs-lookup"><span data-stu-id="f4fcc-178">More in-depth information is available from these topics:</span></span>
  
- <span data-ttu-id="f4fcc-p117">[Preparar atributos de directorio para la sincronización con Office 365 mediante la herramienta IdFix](prepare-directory-attributes-for-synch-with-idfix.md) . Una vez instalada la herramienta, vaya a este tema para obtener instrucciones más detalladas sobre cómo ejecutar la herramienta, los errores comunes que encontrará, las correcciones sugeridas, los ejemplos y los procedimientos recomendados para lo que debe hacer cuando tiene un gran número de errores.</span><span class="sxs-lookup"><span data-stu-id="f4fcc-p117">[Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md) . After you have installed the tool, jump to this topic for more detailed instructions about running the tool, common errors you will encounter, suggested fixes, examples, and best practices for what to do when you have a large number of errors.</span></span> 
- [<span data-ttu-id="f4fcc-181">Referencia: Objetos y atributos admitidos y excluidos en IdFix</span><span class="sxs-lookup"><span data-stu-id="f4fcc-181">Reference: IdFix excluded and supported objects and attributes</span></span>](idfix-excluded-and-supported-objects-and-attributes.md)  
- [<span data-ttu-id="f4fcc-182">Referencia: Registro de transacciones de IdFix de Office 365</span><span class="sxs-lookup"><span data-stu-id="f4fcc-182">Reference: Office 365 IdFix transaction log</span></span>](idfix-transaction-log.md)
    
## <a name="video-training"></a><span data-ttu-id="f4fcc-183">Vídeo de aprendizaje</span><span class="sxs-lookup"><span data-stu-id="f4fcc-183">Video training</span></span>

<span data-ttu-id="f4fcc-184">Para obtener más información, vea la lección [instalación y uso de la herramienta IDFix](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), que le ha ofrecido LinkedIn Learning.</span><span class="sxs-lookup"><span data-stu-id="f4fcc-184">For more information, see the lesson [Install and use the IDFix tool](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), brought to you by LinkedIn Learning.</span></span>
  

