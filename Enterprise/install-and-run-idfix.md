---
title: Descargar y ejecutar la herramienta IdFix de Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Priority
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
description: Cómo descargar y ejecutar la herramienta IdFix de Microsoft 365 para ayudar a limpiar los servicios de dominio de Active Directory (AD DS) antes de sincronizarlos con Microsoft 365.
ms.openlocfilehash: beef13857ad00806cc3e62aedd7a1b3c48bfe4c0
ms.sourcegitcommit: d9abb99b336170f07b8f3f6d00fac19ad2159d3a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/28/2020
ms.locfileid: "46502665"
---
# <a name="download-and-run-the-microsoft-365-idfix-tool"></a><span data-ttu-id="79442-103">Descargar y ejecutar la herramienta IdFix de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="79442-103">Download and run the Microsoft 365 IdFix tool</span></span>

<span data-ttu-id="79442-104">*Este artículo aplica tanto a Office 365 Enterprise como a Microsoft 365 Enterprise*</span><span class="sxs-lookup"><span data-stu-id="79442-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="79442-105">IdFix identifica errores como duplicados y problemas de formato en el dominio de los servicios de dominio de Active Directory (AD DS) antes de sincronizar con Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="79442-105">IdFix identifies errors such as duplicates and formatting problems in your Active Directory Domain Services (AD DS) domain before you synchronize to Microsoft 365.</span></span> 
  
<span data-ttu-id="79442-106">Para terminar esta tarea correctamente, debe sentirse cómodo trabajando con objetos de usuario, grupo y contacto en AD DS.</span><span class="sxs-lookup"><span data-stu-id="79442-106">To finish this task successfully, you should be comfortable working with user, group, and contact objects in AD DS.</span></span>
  
<span data-ttu-id="79442-107">Si no puede completar esta tarea, hay otras cosas que puede hacer.</span><span class="sxs-lookup"><span data-stu-id="79442-107">If you can't complete this task, there are a couple of other things you can do.</span></span> <span data-ttu-id="79442-108">Es posible que estos métodos sean más fáciles, pero también pueden tardar más tiempo o tener otras desventajas.</span><span class="sxs-lookup"><span data-stu-id="79442-108">These methods might be easier, but they might also take longer or have other drawbacks.</span></span> <span data-ttu-id="79442-109">Son las siguientes:</span><span class="sxs-lookup"><span data-stu-id="79442-109">They are:</span></span>
  
- <span data-ttu-id="79442-110">**Ejecutar la sincronización de directorios sin ejecutar IdFix**</span><span class="sxs-lookup"><span data-stu-id="79442-110">**Run directory synchronization without running IdFix**</span></span> 

  <span data-ttu-id="79442-111">Puede sincronizar su directorio sin usar la herramienta IdFix, pero no lo recomendamos.</span><span class="sxs-lookup"><span data-stu-id="79442-111">You can synchronize your directory without using the IdFix tool, but we don't recommend it.</span></span> <span data-ttu-id="79442-112">Corregir los errores antes de sincronizar lleva menos tiempo y suele facilitar la transición a la nube.</span><span class="sxs-lookup"><span data-stu-id="79442-112">Fixing errors before you synchronize takes less time and often provides a smoother transition to the cloud.</span></span> 

- <span data-ttu-id="79442-113">**Contratar a un consultor**</span><span class="sxs-lookup"><span data-stu-id="79442-113">**Hire a consultant**</span></span> 

  <span data-ttu-id="79442-114">Solicitar ayuda a un experto puede poner en marcha a sus usuarios rápidamente y sincronizar el directorio.</span><span class="sxs-lookup"><span data-stu-id="79442-114">Getting expert help can get your users up and running quickly and your directory synchronized.</span></span> 
    
## <a name="what-you-need-to-run-idfix"></a><span data-ttu-id="79442-115">Qué se necesita para ejecutar IdFix</span><span class="sxs-lookup"><span data-stu-id="79442-115">What you need to run IdFix</span></span>

<span data-ttu-id="79442-116">La manera más fácil de poner en marcha IdFix es descargarla en un equipo que esté unido a su dominio de AD DS.</span><span class="sxs-lookup"><span data-stu-id="79442-116">The easiest way to get IdFix up and running is to download it onto a computer that is joined to your AD DS domain.</span></span> <span data-ttu-id="79442-117">Puede ejecutarla en el controlador de dominio si quiere, pero no es necesario.</span><span class="sxs-lookup"><span data-stu-id="79442-117">You can run it on the domain controller if you want, but it's not necessary.</span></span>
  
### <a name="idfix-hardware-requirements"></a><span data-ttu-id="79442-118">Requisitos de hardware de IdFix</span><span class="sxs-lookup"><span data-stu-id="79442-118">IdFix hardware requirements</span></span>

<span data-ttu-id="79442-119">El equipo donde descargue IdFix debe cumplir estos requisitos de hardware mínimos:</span><span class="sxs-lookup"><span data-stu-id="79442-119">The computer where you download IdFix needs to meet these minimum hardware requirements:</span></span>
  
- <span data-ttu-id="79442-120">4 GB de RAM</span><span class="sxs-lookup"><span data-stu-id="79442-120">4 GB RAM</span></span>
- <span data-ttu-id="79442-121">2 GB de espacio en disco duro.</span><span class="sxs-lookup"><span data-stu-id="79442-121">2 GB of hard disk space</span></span>
   
### <a name="idfix-software-requirements"></a><span data-ttu-id="79442-122">Requisitos de software de IdFix</span><span class="sxs-lookup"><span data-stu-id="79442-122">IdFix software requirements</span></span>

<span data-ttu-id="79442-123">El equipo donde descargue IdFix necesita estar unido al mismo dominio de AD DS desde el que desea sincronizar usuarios a Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="79442-123">The computer where you download IdFix needs to be joined to the same AD DS domain from which you want to synchronize users to Microsoft 365.</span></span> 

<span data-ttu-id="79442-124">El equipo también debe tener .NET Framework 4.0 instalado.</span><span class="sxs-lookup"><span data-stu-id="79442-124">The computer also needs to have .NET Framework 4.0 installed.</span></span> <span data-ttu-id="79442-125">Si está ejecutando Windows Server 2008 o posterior, probablemente .NET Framework ya está instalado.</span><span class="sxs-lookup"><span data-stu-id="79442-125">If you are running Windows Server 2008 or later, the .NET Framework is probably already installed.</span></span> <span data-ttu-id="79442-126">Si no es así, puede [descargar .NET 4.0 desde el centro de descarga](https://go.microsoft.com/fwlink/p/?LinkId=400475) o con Windows Update.</span><span class="sxs-lookup"><span data-stu-id="79442-126">If not, you can [download .NET 4.0 from the download center](https://go.microsoft.com/fwlink/p/?LinkId=400475) or with Windows Update.</span></span> 
  
### <a name="idfix-permissions-requirements"></a><span data-ttu-id="79442-127">Requisitos de permisos de IdFix</span><span class="sxs-lookup"><span data-stu-id="79442-127">IdFix permissions requirements</span></span>

<span data-ttu-id="79442-128">La cuenta de usuario que use para ejecutar IdFix debe tener acceso de lectura y escritura al dominio de AD DS.</span><span class="sxs-lookup"><span data-stu-id="79442-128">The user account that you use to run IdFix must have read and write access to the AD DS domain.</span></span>
  
<span data-ttu-id="79442-129">Si no está seguro de si su cuenta de usuario cumple con estos requisitos y no sabe cómo comprobarlo, igual puede descargar y ejecutar IdFix.</span><span class="sxs-lookup"><span data-stu-id="79442-129">If you aren't sure if your user account meets these requirements, and you're not sure how to check, you can still download and run IdFix.</span></span> <span data-ttu-id="79442-130">Si su cuenta de usuario no tiene los permisos adecuados, IdFix mostrará un error al intentar ejecutarla.</span><span class="sxs-lookup"><span data-stu-id="79442-130">If your user account doesn't have the right permissions, IdFix will simply display an error when you try to run it.</span></span>
  
## <a name="download-and-extract-idfix"></a><span data-ttu-id="79442-131">Descargar y extraer IdFix</span><span class="sxs-lookup"><span data-stu-id="79442-131">Download and extract IdFix</span></span>

<span data-ttu-id="79442-132">Siga estas instrucciones.</span><span class="sxs-lookup"><span data-stu-id="79442-132">Follow these instructions.</span></span> 
  
1. <span data-ttu-id="79442-133">Inicie sesión en el equipo donde quiere ejecutar la herramienta IdFix.</span><span class="sxs-lookup"><span data-stu-id="79442-133">Sign in to the computer where you want to run the IdFix tool.</span></span>
    
2. <span data-ttu-id="79442-134">Vaya al sitio [herramienta de corrección de errores de sincronización de directorios de IdFix](https://github.com/microsoft/idfix).</span><span class="sxs-lookup"><span data-stu-id="79442-134">Go to the [IdFix DirSync Error Remediation Tool](https://github.com/microsoft/idfix) site.</span></span>
    
3. <span data-ttu-id="79442-135">Haga clic en **iniciar** en la sección **inicio de ClickOnce** para descargar el archivo zip.</span><span class="sxs-lookup"><span data-stu-id="79442-135">Click **launch** in the **ClickOnce Launch** section to download the zip file.</span></span> <span data-ttu-id="79442-136">Abra el archivo zip.</span><span class="sxs-lookup"><span data-stu-id="79442-136">Open the zip file.</span></span>
    
4. <span data-ttu-id="79442-137">En la ventana **IdFix**, elija **Extraer**y, a continuación, **Extraer todo**.</span><span class="sxs-lookup"><span data-stu-id="79442-137">In the **IdFix** window, choose **Extract**, and then **Extract all**.</span></span> <span data-ttu-id="79442-138">De manera predeterminada, IdFix se extrae a `C:\Users\<your user name>\Documents\IdFix`.</span><span class="sxs-lookup"><span data-stu-id="79442-138">By default, IdFix is extracted to `C:\Users\<your user name>\Documents\IdFix`.</span></span> 
    
5. <span data-ttu-id="79442-139">Elija **Extraer**.</span><span class="sxs-lookup"><span data-stu-id="79442-139">Choose **Extract**.</span></span>

<span data-ttu-id="79442-140">Los pasos pueden variar en función de su versión de Windows y de su explorador de Internet.</span><span class="sxs-lookup"><span data-stu-id="79442-140">Your steps might vary based on your version of Windows and your Internet browser.</span></span>
    
## <a name="run-the-idfix-tool"></a><span data-ttu-id="79442-141">Ejecutar la herramienta IdFix</span><span class="sxs-lookup"><span data-stu-id="79442-141">Run the IdFix tool</span></span>

<span data-ttu-id="79442-142">Después de descargar y extraer IdFix, ejecútela para buscar problemas en el dominio de AD DS.</span><span class="sxs-lookup"><span data-stu-id="79442-142">After you download and extract IdFix, run it to search for problems in your AD DS domain.</span></span>
  
1. <span data-ttu-id="79442-143">Inicie sesión en el equipo en el que descargó IdFix con una cuenta que tenga acceso de lectura y escritura al dominio de AD DS.</span><span class="sxs-lookup"><span data-stu-id="79442-143">Using an account that has read/write access to your AD DS domain, sign in to the computer where you downloaded IdFix.</span></span>
    
2. <span data-ttu-id="79442-144">En el Explorador de archivos, vaya a la ubicación donde extrajo IdFix.</span><span class="sxs-lookup"><span data-stu-id="79442-144">In File Explorer, go to the location where you extracted IdFix.</span></span> <span data-ttu-id="79442-145">Si eligió la carpeta predeterminada durante la extracción, vaya a `C:\Users\<your user name>\Documents\IdFix`.</span><span class="sxs-lookup"><span data-stu-id="79442-145">If you chose the default folder during extraction, go to `C:\Users\<your user name>\Documents\IdFix`.</span></span> 
    
3. <span data-ttu-id="79442-146">Haga doble clic en **IdFix.exe**.</span><span class="sxs-lookup"><span data-stu-id="79442-146">Double-click **IdFix.exe**.</span></span> 
  
4. <span data-ttu-id="79442-147">De forma predeterminada, IdFix usa el conjunto de reglas multiempresa para probar las entradas del directorio.</span><span class="sxs-lookup"><span data-stu-id="79442-147">By default, IdFix uses the Multi-Tenant rule set to test the entries in your directory.</span></span> <span data-ttu-id="79442-148">Este es el conjunto de reglas apropiado para la mayoría de los clientes de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="79442-148">This is the right rule set for most Microsoft 365 customers.</span></span> <span data-ttu-id="79442-149">Sin embargo, si es un cliente de Microsoft 365 dedicado o ITAR (Reglamento internacional de tráfico de armas), puede configurar IdFix para usar el conjunto de reglas Dedicado en su lugar.</span><span class="sxs-lookup"><span data-stu-id="79442-149">However, if you are a Microsoft 365 Dedicated or International Traffic in Arms Regulations (ITAR)) customer, you can configure IdFix to use the Dedicated rule set instead.</span></span> <span data-ttu-id="79442-150">Si no está seguro de qué tipo de cliente es, puede omitir este paso de forma segura.</span><span class="sxs-lookup"><span data-stu-id="79442-150">If you aren't sure what type of customer you are, you can safely skip this step.</span></span> <span data-ttu-id="79442-151">Para establecer el conjunto de reglas como Dedicado, haga clic en el icono de engranaje en la barra de menús y luego elija **Dedicado**.</span><span class="sxs-lookup"><span data-stu-id="79442-151">To set the rule set to Dedicated, click the gear icon in the menu bar, and then choose **Dedicated**.</span></span>
    
5. <span data-ttu-id="79442-152">Elija **Consultar**.</span><span class="sxs-lookup"><span data-stu-id="79442-152">Choose **Query**.</span></span>
    
    ![Seleccione una consulta en IdFix.](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. <span data-ttu-id="79442-154">De forma predeterminada, IdFix busca errores en todo el directorio.</span><span class="sxs-lookup"><span data-stu-id="79442-154">By default, IdFix searches the entire directory for errors.</span></span>
    
    <span data-ttu-id="79442-155">El tiempo que se tarde en ejecutar la consulta depende del tamaño del directorio.</span><span class="sxs-lookup"><span data-stu-id="79442-155">Depending on the size of your directory, running the query can take a while.</span></span> <span data-ttu-id="79442-156">Puede ver el progreso en la parte inferior de la ventana principal de la herramienta.</span><span class="sxs-lookup"><span data-stu-id="79442-156">You can watch the progress at the bottom of the tool's main window.</span></span> <span data-ttu-id="79442-157">Si hace clic en **Cancelar**, tendrá que volver al principio.</span><span class="sxs-lookup"><span data-stu-id="79442-157">If you click **Cancel**, you'll need to restart from the beginning.</span></span>
  
7. <span data-ttu-id="79442-158">Cuando IdFix termine la consulta, podrá sincronizar su directorio si no hay errores.</span><span class="sxs-lookup"><span data-stu-id="79442-158">After IdFix completes the query, you can synchronize your directory if there are no errors.</span></span> <span data-ttu-id="79442-159">Si hay errores en el directorio, se recomienda corregirlos antes de sincronizar.</span><span class="sxs-lookup"><span data-stu-id="79442-159">If there are errors in your directory, it is recommended that you fix them before you synchronize.</span></span> <span data-ttu-id="79442-160">Para obtener más información, consulte [preparar los atributos del directorio para la sincronización con Microsoft 365](prepare-directory-attributes-for-synch-with-idfix.md).</span><span class="sxs-lookup"><span data-stu-id="79442-160">See [prepare directory attributes for synchronization with Microsoft 365](prepare-directory-attributes-for-synch-with-idfix.md) for more information.</span></span>
    
    <span data-ttu-id="79442-161">Aunque no es obligatorio corregir los errores antes de sincronizar, se recomienda encarecidamente al menos revisar todos los errores devueltos por IdFix. </span><span class="sxs-lookup"><span data-stu-id="79442-161">While it is not mandatory to fix the errors before you synchronize, we strongly recommend that you at least review all the errors returned by IdFix.</span></span>
    
    <span data-ttu-id="79442-162">Cada error se muestra en una fila distinta en la ventana principal de la herramienta.</span><span class="sxs-lookup"><span data-stu-id="79442-162">Each error is displayed in a separate row in the tool's main window .</span></span> 
    
8. <span data-ttu-id="79442-163">Si está de acuerdo con el cambio sugerido en la columna **ACTUALIZACIÓN**, en la columna **ACCIÓN** seleccione lo que quiere que IdFix haga para implementar el cambio y luego haga clic en **Aplicar**.</span><span class="sxs-lookup"><span data-stu-id="79442-163">If you agree with the suggested change in the **UPDATE** column, in the **ACTION** column select what you want IdFix to do to implement the change and then click **Apply**.</span></span> <span data-ttu-id="79442-164">Al hacer clic en **Aplicar**, la herramienta realiza los cambios en el directorio.</span><span class="sxs-lookup"><span data-stu-id="79442-164">When you click **Apply**, the tool makes the changes in the directory.</span></span>
    
    <span data-ttu-id="79442-165">No tiene que hacer clic en **Aplicar** luego de cada actualización.</span><span class="sxs-lookup"><span data-stu-id="79442-165">You don't have to click **Apply** after each update.</span></span> <span data-ttu-id="79442-166">En su lugar, puede corregir varios errores antes de hacer clic en **Aplicar** y IdFix los cambiará todos al mismo tiempo.</span><span class="sxs-lookup"><span data-stu-id="79442-166">Instead, you can fix several errors before you click **Apply** and IdFix will change them all at the same time.</span></span> <span data-ttu-id="79442-167">Puede ordenar los errores por tipo de error al hacer clic en **ERROR** en la parte superior de la columna que enumera los tipos de error.</span><span class="sxs-lookup"><span data-stu-id="79442-167">You can sort the errors by error type by clicking **ERROR** at the top of the column that lists the error types.</span></span> 
    
    <span data-ttu-id="79442-168">Una estrategia consiste en corregir todos los errores del mismo tipo; por ejemplo, corrija todos los duplicados primero y luego aplíquelos.</span><span class="sxs-lookup"><span data-stu-id="79442-168">One strategy is to fix all the errors of the same type; for example, fix all the duplicates first, and apply them.</span></span> <span data-ttu-id="79442-169">A continuación, corrija los errores de formato de carácter y así sucesivamente. </span><span class="sxs-lookup"><span data-stu-id="79442-169">Next, fix the character format errors, and so on.</span></span> <span data-ttu-id="79442-170">Cada vez que aplica los cambios, la herramienta IdFix crea un archivo de registro independiente que puede usar para deshacer los cambios si se equivoca.</span><span class="sxs-lookup"><span data-stu-id="79442-170">Each time you apply the changes, the IdFix tool creates a separate log file that you can use to undo your changes in case you make a mistake.</span></span> <span data-ttu-id="79442-171">El [registro de transacciones](idfix-transaction-log.md) se almacena en la carpeta donde extrajo IdFix, que es de forma predeterminada _C:\Users\<your user name>\Documents\IdFix_.</span><span class="sxs-lookup"><span data-stu-id="79442-171">The [transaction log](idfix-transaction-log.md) is stored in the folder where you extracted IdFix, which is _C:\Users\<your user name>\Documents\IdFix_ by default.</span></span> 
    
    ![Corrección de errores en IdFix.](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. <span data-ttu-id="79442-173">Después de hacer todos los cambios en el directorio, ejecute IdFix otra vez para garantizar que las correcciones realizadas no contienen nuevos errores.</span><span class="sxs-lookup"><span data-stu-id="79442-173">After all of your changes are made to the directory, run IdFix again to ensure that the fixes you made didn't introduce new errors.</span></span> <span data-ttu-id="79442-174">Puede repetir estos pasos la cantidad de veces que sean necesarias.</span><span class="sxs-lookup"><span data-stu-id="79442-174">You can repeat these steps as many times as you need to.</span></span> <span data-ttu-id="79442-175">Una buena idea es repetir el proceso un par de veces antes de sincronizar.</span><span class="sxs-lookup"><span data-stu-id="79442-175">It's a good idea to go through the process a few times before you synchronize.</span></span>
    
## <a name="additional-resources-on-idfix"></a><span data-ttu-id="79442-176">Recursos adicionales en IdFix</span><span class="sxs-lookup"><span data-stu-id="79442-176">Additional resources on IdFix</span></span> 

- [<span data-ttu-id="79442-177">Objetos y atributos admitidos y excluidos en IdFix</span><span class="sxs-lookup"><span data-stu-id="79442-177">IdFix excluded and supported objects and attributes</span></span>](idfix-excluded-and-supported-objects-and-attributes.md)  
- [<span data-ttu-id="79442-178">Registro de transacciones de IdFix de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="79442-178">Microsoft 365 IdFix transaction log</span></span>](idfix-transaction-log.md)
    
