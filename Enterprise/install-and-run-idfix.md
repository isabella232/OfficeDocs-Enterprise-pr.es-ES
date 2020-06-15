---
title: Descargar y ejecutar la herramienta IdFix de Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365E_HRCSetupAADConnectIDFixLM617036
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: Cómo descargar y ejecutar la herramienta Microsoft 365 IdFix para ayudar a limpiar los servicios de dominio de Active Directory (AD DS) antes de sincronizarlos con Microsoft 365.
ms.openlocfilehash: dde12d7e16aad8488fe067888eacdf1c80e1a037
ms.sourcegitcommit: d2a3d6eeeaa07510ee94c2bc675284d893221a95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2020
ms.locfileid: "44711600"
---
# <a name="download-and-run-the-microsoft-365-idfix-tool"></a><span data-ttu-id="d33c7-103">Descargar y ejecutar la herramienta IdFix de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="d33c7-103">Download and run the Microsoft 365 IdFix tool</span></span>

<span data-ttu-id="d33c7-104">*Este artículo se aplica tanto a Office 365 Enterprise como a Microsoft 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="d33c7-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="d33c7-105">IdFix identifica errores como duplicados y problemas de formato en el dominio de servicios de dominio de Active Directory (AD DS) antes de sincronizar con Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="d33c7-105">IdFix identifies errors such as duplicates and formatting problems in your Active Directory Domain Services (AD DS) domain before you synchronize to Microsoft 365.</span></span> 
  
<span data-ttu-id="d33c7-106">Para finalizar esta tarea correctamente, debe sentirse cómodo trabajando con objetos de usuario, grupo y contacto en AD DS.</span><span class="sxs-lookup"><span data-stu-id="d33c7-106">To finish this task successfully, you should be comfortable working with user, group, and contact objects in AD DS.</span></span>
  
<span data-ttu-id="d33c7-107">Si no puede completar esta tarea, hay un par de cosas que puede hacer.</span><span class="sxs-lookup"><span data-stu-id="d33c7-107">If you can't complete this task, there are a couple of other things you can do.</span></span> <span data-ttu-id="d33c7-108">Estos métodos pueden ser más sencillos, pero también pueden tardar más tiempo o tener otros inconvenientes.</span><span class="sxs-lookup"><span data-stu-id="d33c7-108">These methods might be easier, but they might also take longer or have other drawbacks.</span></span> <span data-ttu-id="d33c7-109">Son las siguientes:</span><span class="sxs-lookup"><span data-stu-id="d33c7-109">They are:</span></span>
  
- <span data-ttu-id="d33c7-110">**Ejecutar la sincronización de directorios sin ejecutar IdFix**</span><span class="sxs-lookup"><span data-stu-id="d33c7-110">**Run directory synchronization without running IdFix**</span></span> 

  <span data-ttu-id="d33c7-111">Puede sincronizar su directorio sin usar la herramienta IdFix, pero no lo recomendamos.</span><span class="sxs-lookup"><span data-stu-id="d33c7-111">You can synchronize your directory without using the IdFix tool, but we don't recommend it.</span></span> <span data-ttu-id="d33c7-112">La corrección de errores antes de sincronizar requiere menos tiempo y suele proporcionar una transición más fluida a la nube.</span><span class="sxs-lookup"><span data-stu-id="d33c7-112">Fixing errors before you synchronize takes less time and often provides a smoother transition to the cloud.</span></span> 

- <span data-ttu-id="d33c7-113">**Contratar a un consultor**</span><span class="sxs-lookup"><span data-stu-id="d33c7-113">**Hire a consultant**</span></span> 

  <span data-ttu-id="d33c7-114">Obtener ayuda experta puede poner en marcha a sus usuarios rápidamente y sincronizar su directorio.</span><span class="sxs-lookup"><span data-stu-id="d33c7-114">Getting expert help can get your users up and running quickly and your directory synchronized.</span></span> 
    
## <a name="what-you-need-to-run-idfix"></a><span data-ttu-id="d33c7-115">Qué necesita para ejecutar IdFix</span><span class="sxs-lookup"><span data-stu-id="d33c7-115">What you need to run IdFix</span></span>

<span data-ttu-id="d33c7-116">La forma más sencilla de iniciar IdFix en funcionamiento es descargarlo en un equipo que se haya unido a su dominio de AD DS.</span><span class="sxs-lookup"><span data-stu-id="d33c7-116">The easiest way to get IdFix up and running is to download it onto a computer that is joined to your AD DS domain.</span></span> <span data-ttu-id="d33c7-117">Si lo desea, puede ejecutarlo en el controlador de dominio, pero no es necesario.</span><span class="sxs-lookup"><span data-stu-id="d33c7-117">You can run it on the domain controller if you want, but it's not necessary.</span></span>
  
### <a name="idfix-hardware-requirements"></a><span data-ttu-id="d33c7-118">Requisitos de hardware de IdFix</span><span class="sxs-lookup"><span data-stu-id="d33c7-118">IdFix hardware requirements</span></span>

<span data-ttu-id="d33c7-119">El equipo en el que se descarga IdFix debe cumplir estos requisitos mínimos de hardware:</span><span class="sxs-lookup"><span data-stu-id="d33c7-119">The computer where you download IdFix needs to meet these minimum hardware requirements:</span></span>
  
- <span data-ttu-id="d33c7-120">4 GB de RAM</span><span class="sxs-lookup"><span data-stu-id="d33c7-120">4 GB RAM</span></span>
- <span data-ttu-id="d33c7-121">2 GB de espacio en disco duro</span><span class="sxs-lookup"><span data-stu-id="d33c7-121">2 GB of hard disk space</span></span>
   
### <a name="idfix-software-requirements"></a><span data-ttu-id="d33c7-122">Requisitos de software de IdFix</span><span class="sxs-lookup"><span data-stu-id="d33c7-122">IdFix software requirements</span></span>

<span data-ttu-id="d33c7-123">El equipo donde Descargue IdFix debe unirse al mismo dominio de AD DS desde el que desea sincronizar usuarios a Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="d33c7-123">The computer where you download IdFix needs to be joined to the same AD DS domain from which you want to synchronize users to Microsoft 365.</span></span> 

<span data-ttu-id="d33c7-124">El equipo también debe tener instalado .NET Framework 4,0.</span><span class="sxs-lookup"><span data-stu-id="d33c7-124">The computer also needs to have .NET Framework 4.0 installed.</span></span> <span data-ttu-id="d33c7-125">Si ejecuta Windows Server 2008 o posterior, es probable que .NET Framework ya esté instalado.</span><span class="sxs-lookup"><span data-stu-id="d33c7-125">If you are running Windows Server 2008 or later, the .NET Framework is probably already installed.</span></span> <span data-ttu-id="d33c7-126">Si no es así, puede [Descargar .net 4,0 desde el centro de descarga](https://go.microsoft.com/fwlink/p/?LinkId=400475) o con Windows Update.</span><span class="sxs-lookup"><span data-stu-id="d33c7-126">If not, you can [download .NET 4.0 from the download center](https://go.microsoft.com/fwlink/p/?LinkId=400475) or with Windows Update.</span></span> 
  
### <a name="idfix-permissions-requirements"></a><span data-ttu-id="d33c7-127">Requisitos de permisos de IdFix</span><span class="sxs-lookup"><span data-stu-id="d33c7-127">IdFix permissions requirements</span></span>

<span data-ttu-id="d33c7-128">La cuenta de usuario que use para ejecutar IdFix debe tener acceso de lectura y escritura al dominio de AD DS.</span><span class="sxs-lookup"><span data-stu-id="d33c7-128">The user account that you use to run IdFix must have read and write access to the AD DS domain.</span></span>
  
<span data-ttu-id="d33c7-129">Si no está seguro de si su cuenta de usuario cumple estos requisitos y no está seguro de cómo comprobarla, puede descargar y ejecutar IdFix.</span><span class="sxs-lookup"><span data-stu-id="d33c7-129">If you aren't sure if your user account meets these requirements, and you're not sure how to check, you can still download and run IdFix.</span></span> <span data-ttu-id="d33c7-130">Si su cuenta de usuario no tiene los permisos adecuados, IdFix simplemente mostrará un error cuando intente ejecutarla.</span><span class="sxs-lookup"><span data-stu-id="d33c7-130">If your user account doesn't have the right permissions, IdFix will simply display an error when you try to run it.</span></span>
  
## <a name="download-and-extract-idfix"></a><span data-ttu-id="d33c7-131">Descargar y extraer IdFix</span><span class="sxs-lookup"><span data-stu-id="d33c7-131">Download and extract IdFix</span></span>

<span data-ttu-id="d33c7-132">Siga estas instrucciones.</span><span class="sxs-lookup"><span data-stu-id="d33c7-132">Follow these instructions.</span></span> 
  
1. <span data-ttu-id="d33c7-133">Inicie sesión en el equipo en el que desea ejecutar la herramienta IdFix.</span><span class="sxs-lookup"><span data-stu-id="d33c7-133">Sign in to the computer where you want to run the IdFix tool.</span></span>
    
2. <span data-ttu-id="d33c7-134">Vaya al sitio de la [herramienta de corrección de errores de sincronización de directorios de IdFix](https://github.com/microsoft/idfix) .</span><span class="sxs-lookup"><span data-stu-id="d33c7-134">Go to the [IdFix DirSync Error Remediation Tool](https://github.com/microsoft/idfix) site.</span></span>
    
3. <span data-ttu-id="d33c7-135">Haga clic en **iniciar** en la sección **iniciar ClickOnce** para descargar el archivo zip.</span><span class="sxs-lookup"><span data-stu-id="d33c7-135">Click **launch** in the **ClickOnce Launch** section to download the zip file.</span></span> <span data-ttu-id="d33c7-136">Abra el archivo zip.</span><span class="sxs-lookup"><span data-stu-id="d33c7-136">Open the zip file.</span></span>
    
4. <span data-ttu-id="d33c7-137">En la ventana de **IdFix** , elija **extraer**y, a continuación, **extraer todo**.</span><span class="sxs-lookup"><span data-stu-id="d33c7-137">In the **IdFix** window, choose **Extract**, and then **Extract all**.</span></span> <span data-ttu-id="d33c7-138">De forma predeterminada, IdFix se extrae a `C:\Users\<your user name>\Documents\IdFix` .</span><span class="sxs-lookup"><span data-stu-id="d33c7-138">By default, IdFix is extracted to `C:\Users\<your user name>\Documents\IdFix`.</span></span> 
    
5. <span data-ttu-id="d33c7-139">Elija **Extraer**.</span><span class="sxs-lookup"><span data-stu-id="d33c7-139">Choose **Extract**.</span></span>

<span data-ttu-id="d33c7-140">Los pasos pueden variar en función de la versión de Windows y el explorador de Internet.</span><span class="sxs-lookup"><span data-stu-id="d33c7-140">Your steps might vary based on your version of Windows and your Internet browser.</span></span>
    
## <a name="run-the-idfix-tool"></a><span data-ttu-id="d33c7-141">Ejecutar la herramienta IdFix</span><span class="sxs-lookup"><span data-stu-id="d33c7-141">Run the IdFix tool</span></span>

<span data-ttu-id="d33c7-142">Después de descargar y extraer IdFix, ejecútelo para buscar problemas en su dominio de AD DS.</span><span class="sxs-lookup"><span data-stu-id="d33c7-142">After you download and extract IdFix, run it to search for problems in your AD DS domain.</span></span>
  
1. <span data-ttu-id="d33c7-143">Inicie sesión en el equipo donde descargó IdFix con una cuenta que tenga acceso de lectura y escritura en su dominio de AD DS.</span><span class="sxs-lookup"><span data-stu-id="d33c7-143">Using an account that has read/write access to your AD DS domain, sign in to the computer where you downloaded IdFix.</span></span>
    
2. <span data-ttu-id="d33c7-144">En el explorador de archivos, vaya a la ubicación donde extrajo IdFix.</span><span class="sxs-lookup"><span data-stu-id="d33c7-144">In File Explorer, go to the location where you extracted IdFix.</span></span> <span data-ttu-id="d33c7-145">Si eligió la carpeta predeterminada durante la extracción, vaya a `C:\Users\<your user name>\Documents\IdFix` .</span><span class="sxs-lookup"><span data-stu-id="d33c7-145">If you chose the default folder during extraction, go to `C:\Users\<your user name>\Documents\IdFix`.</span></span> 
    
3. <span data-ttu-id="d33c7-146">Haga doble clic en **IdFix.exe**.</span><span class="sxs-lookup"><span data-stu-id="d33c7-146">Double-click **IdFix.exe**.</span></span> 
  
4. <span data-ttu-id="d33c7-147">De forma predeterminada, IdFix usa el conjunto de reglas multiinquilino para probar las entradas del directorio.</span><span class="sxs-lookup"><span data-stu-id="d33c7-147">By default, IdFix uses the Multi-Tenant rule set to test the entries in your directory.</span></span> <span data-ttu-id="d33c7-148">Este es el conjunto de reglas correcto para la mayoría de los clientes de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="d33c7-148">This is the right rule set for most Microsoft 365 customers.</span></span> <span data-ttu-id="d33c7-149">Sin embargo, si es cliente de Microsoft 365 Dedicated or International Traffic in brazos regulatorias (ITAR)), puede configurar IdFix para usar el conjunto de reglas dedicado en su lugar.</span><span class="sxs-lookup"><span data-stu-id="d33c7-149">However, if you are a Microsoft 365 Dedicated or International Traffic in Arms Regulations (ITAR)) customer, you can configure IdFix to use the Dedicated rule set instead.</span></span> <span data-ttu-id="d33c7-150">Si no está seguro de qué tipo de cliente es, puede omitir este paso de manera segura.</span><span class="sxs-lookup"><span data-stu-id="d33c7-150">If you aren't sure what type of customer you are, you can safely skip this step.</span></span> <span data-ttu-id="d33c7-151">Para establecer el conjunto de reglas en dedicado, haga clic en el icono de engranaje en la barra de menús y, a continuación, elija **dedicado**.</span><span class="sxs-lookup"><span data-stu-id="d33c7-151">To set the rule set to Dedicated, click the gear icon in the menu bar, and then choose **Dedicated**.</span></span>
    
5. <span data-ttu-id="d33c7-152">Elija **consultar**.</span><span class="sxs-lookup"><span data-stu-id="d33c7-152">Choose **Query**.</span></span>
    
    ![Seleccione consulta en IdFix.](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. <span data-ttu-id="d33c7-154">De forma predeterminada, IdFix busca errores en todo el directorio.</span><span class="sxs-lookup"><span data-stu-id="d33c7-154">By default, IdFix searches the entire directory for errors.</span></span>
    
    <span data-ttu-id="d33c7-155">En función del tamaño del directorio, la ejecución de la consulta puede tardar unos minutos.</span><span class="sxs-lookup"><span data-stu-id="d33c7-155">Depending on the size of your directory, running the query can take a while.</span></span> <span data-ttu-id="d33c7-156">Puede ver el progreso en la parte inferior de la ventana principal de la herramienta.</span><span class="sxs-lookup"><span data-stu-id="d33c7-156">You can watch the progress at the bottom of the tool's main window.</span></span> <span data-ttu-id="d33c7-157">Si hace clic en **Cancelar**, deberá reiniciar desde el principio.</span><span class="sxs-lookup"><span data-stu-id="d33c7-157">If you click **Cancel**, you'll need to restart from the beginning.</span></span>
  
7. <span data-ttu-id="d33c7-158">Después de que IdFix complete la consulta, puede sincronizar el directorio si no hay errores.</span><span class="sxs-lookup"><span data-stu-id="d33c7-158">After IdFix completes the query, you can synchronize your directory if there are no errors.</span></span> <span data-ttu-id="d33c7-159">Si hay errores en el directorio, se recomienda que los solucione antes de sincronizar.</span><span class="sxs-lookup"><span data-stu-id="d33c7-159">If there are errors in your directory, it is recommended that you fix them before you synchronize.</span></span> <span data-ttu-id="d33c7-160">Para obtener más información, vea [preparar atributos de directorio para la sincronización con Microsoft 365](prepare-directory-attributes-for-synch-with-idfix.md) .</span><span class="sxs-lookup"><span data-stu-id="d33c7-160">See [prepare directory attributes for synchronization with Microsoft 365](prepare-directory-attributes-for-synch-with-idfix.md) for more information.</span></span>
    
    <span data-ttu-id="d33c7-161">Aunque no es obligatorio corregir los errores antes de sincronizar, se recomienda encarecidamente que, al menos, revise todos los errores devueltos por IdFix.</span><span class="sxs-lookup"><span data-stu-id="d33c7-161">While it is not mandatory to fix the errors before you synchronize, we strongly recommend that you at least review all the errors returned by IdFix.</span></span>
    
    <span data-ttu-id="d33c7-162">Cada error se muestra en una fila independiente en la ventana principal de la herramienta.</span><span class="sxs-lookup"><span data-stu-id="d33c7-162">Each error is displayed in a separate row in the tool's main window .</span></span> 
    
8. <span data-ttu-id="d33c7-163">Si está de acuerdo con el cambio sugerido en la columna **Actualizar** , en la columna **acción** , seleccione qué desea hacer con IdFix para implementar el cambio y, a continuación, haga clic en **aplicar**.</span><span class="sxs-lookup"><span data-stu-id="d33c7-163">If you agree with the suggested change in the **UPDATE** column, in the **ACTION** column select what you want IdFix to do to implement the change and then click **Apply**.</span></span> <span data-ttu-id="d33c7-164">Al hacer clic en **aplicar**, la herramienta realiza los cambios en el directorio.</span><span class="sxs-lookup"><span data-stu-id="d33c7-164">When you click **Apply**, the tool makes the changes in the directory.</span></span>
    
    <span data-ttu-id="d33c7-165">No es necesario hacer clic en **aplicar** después de cada actualización.</span><span class="sxs-lookup"><span data-stu-id="d33c7-165">You don't have to click **Apply** after each update.</span></span> <span data-ttu-id="d33c7-166">En su lugar, puede corregir varios errores antes de hacer clic en **aplicar** y IdFix los cambiará a la vez.</span><span class="sxs-lookup"><span data-stu-id="d33c7-166">Instead, you can fix several errors before you click **Apply** and IdFix will change them all at the same time.</span></span> <span data-ttu-id="d33c7-167">Puede ordenar los errores por tipo de error haciendo clic en **error** en la parte superior de la columna que enumera los tipos de error.</span><span class="sxs-lookup"><span data-stu-id="d33c7-167">You can sort the errors by error type by clicking **ERROR** at the top of the column that lists the error types.</span></span> 
    
    <span data-ttu-id="d33c7-168">Una estrategia consiste en corregir todos los errores del mismo tipo; por ejemplo, primero Corrija todos los duplicados y aplíquelos.</span><span class="sxs-lookup"><span data-stu-id="d33c7-168">One strategy is to fix all the errors of the same type; for example, fix all the duplicates first, and apply them.</span></span> <span data-ttu-id="d33c7-169">A continuación, corrija los errores de formato de carácter y así sucesivamente.</span><span class="sxs-lookup"><span data-stu-id="d33c7-169">Next, fix the character format errors, and so on.</span></span> <span data-ttu-id="d33c7-170">Cada vez que se aplican los cambios, la herramienta IdFix crea un archivo de registro independiente que se puede usar para deshacer los cambios en caso de que se cometa un error.</span><span class="sxs-lookup"><span data-stu-id="d33c7-170">Each time you apply the changes, the IdFix tool creates a separate log file that you can use to undo your changes in case you make a mistake.</span></span> <span data-ttu-id="d33c7-171">El [registro de transacciones](idfix-transaction-log.md) se almacena en la carpeta en la que extrajo IdFix, que es _C:\Users \<your user name> \Documents\IdFix_ de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="d33c7-171">The [transaction log](idfix-transaction-log.md) is stored in the folder where you extracted IdFix, which is _C:\Users\<your user name>\Documents\IdFix_ by default.</span></span> 
    
    ![Corregir errores en IdFix.](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. <span data-ttu-id="d33c7-173">Una vez que se hayan realizado todos los cambios en el directorio, ejecute IdFix de nuevo para asegurarse de que las correcciones que ha realizado no han introducido nuevos errores.</span><span class="sxs-lookup"><span data-stu-id="d33c7-173">After all of your changes are made to the directory, run IdFix again to ensure that the fixes you made didn't introduce new errors.</span></span> <span data-ttu-id="d33c7-174">Puede repetir estos pasos tantas veces como sea necesario.</span><span class="sxs-lookup"><span data-stu-id="d33c7-174">You can repeat these steps as many times as you need to.</span></span> <span data-ttu-id="d33c7-175">Es una buena idea pasar por el proceso varias veces antes de sincronizar.</span><span class="sxs-lookup"><span data-stu-id="d33c7-175">It's a good idea to go through the process a few times before you synchronize.</span></span>
    
## <a name="additional-resources-on-idfix"></a><span data-ttu-id="d33c7-176">Recursos adicionales en IdFix</span><span class="sxs-lookup"><span data-stu-id="d33c7-176">Additional resources on IdFix</span></span> 

- [<span data-ttu-id="d33c7-177">Objetos y atributos admitidos y excluidos en IdFix</span><span class="sxs-lookup"><span data-stu-id="d33c7-177">IdFix excluded and supported objects and attributes</span></span>](idfix-excluded-and-supported-objects-and-attributes.md)  
- [<span data-ttu-id="d33c7-178">Registro de transacciones de IdFix de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="d33c7-178">Microsoft 365 IdFix transaction log</span></span>](idfix-transaction-log.md)
    
## <a name="video-training"></a><span data-ttu-id="d33c7-179">Vídeos de aprendizaje</span><span class="sxs-lookup"><span data-stu-id="d33c7-179">Video training</span></span>

<span data-ttu-id="d33c7-180">Para obtener más información, vea la lección [instalación y uso de la herramienta IdFix](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), que le ha ofrecido LinkedIn Learning.</span><span class="sxs-lookup"><span data-stu-id="d33c7-180">For more information, see the lesson [Install and use the IdFix tool](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), brought to you by LinkedIn Learning.</span></span>
  

