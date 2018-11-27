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
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: Cómo instalar y ejecutar la herramienta IdFix de Office 365 para ayudar a limpiar su Active Directory antes de realizar la sincronización con Office 365.
ms.openlocfilehash: c485d8397aa32005a34b77f886b9bc8f4e857f1b
ms.sourcegitcommit: 9c493c4e18e83491d106c5e9bab55d1a89298879
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2018
ms.locfileid: "26674434"
---
# <a name="install-and-run-the-office-365-idfix-tool"></a>Instalar y ejecutar la herramienta IdFix de Office 365

IdFix identifica errores como duplicados y problemas de formato en el directorio antes de realizar la sincronización con Office 365. 
  
Para finalizar esta tarea correctamente, debe saber trabajar con objetos de usuario, grupo y contactos en Active Directory.
  
Si no se puede completar esta tarea, hay un par de otras cosas que puede hacer. Estos métodos pueden resultar más sencillo, pero también pueden tardar mucho más o tiene otros inconvenientes. Son:
  
- **Ejecutar la sincronización de directorios sin ejecutar IdFix.** Puede sincronizar su Active directory sin ejecutar la herramienta IdFix, pero no se recomienda. Corregir los errores antes de sincronizar lleva menos tiempo y a menudo proporciona una transición sin problemas a la nube. 
- **Contratar a un consultor.** Solicitar ayuda a un experto puede poner en marcha a sus usuarios y sincronizar el directorio rápidamente. 
    
## <a name="what-you-need-to-run-idfix"></a>Lo que necesita para ejecutar IdFix

La manera fácil de obtener IdFix copia de seguridad y que se está ejecutando es que lo instale en un equipo que se une a su dominio. Se puede ejecutar en el controlador de dominio si desea, pero no es necesario.
  
### <a name="idfix-hardware-requirements"></a>Requisitos de hardware de IdFix

El equipo donde instale IdFix debe cumplir estos requisitos mínimos de hardware:
  
- 4 GB de RAM
- 2 GB de espacio en disco duro
    
### <a name="idfix-software-requirements"></a>Requisitos de software de IdFix

El equipo donde instale IdFix debe estar unido al mismo dominio de Active Directory desde el que desea sincronizar los usuarios a Office 365. El equipo también debe tener instalado .NET Framework 4.0. 
  
Si ejecuta Windows Server 2008 o Windows Server 2012, probablemente ya está instalado .NET Framework. Si no, puede [descargar .NET 4.0 desde el centro de descarga](https://go.microsoft.com/fwlink/p/?LinkId=400475) o a través de Windows Update. 
  
### <a name="idfix-permissions-requirements"></a>Requisitos de permisos de IdFix

La cuenta de usuario que se utiliza para ejecutar IdFix debe tener acceso de lectura y escritura en el directorio.
  
Si no está seguro de si su cuenta de usuario cumple estos requisitos, y no está seguro de cómo comprobar, puede instalar y ejecutar IdFix. Si su cuenta de usuario no tiene los permisos adecuados, IdFix simplemente mostrará un error al intentar ejecutarlo.
  
## <a name="install-idfix"></a>Instalar IdFix

Para instalar IdFix, descargue y descomprima **IdFix.exe**: 
  
1. Inicie sesión en el equipo donde quiere instalar la herramienta IdFix.
    
2. Vaya al sitio de descarga de Microsoft para la [Herramienta de corrección de Error de sincronización de directorios de IdFix](https://go.microsoft.com/fwlink/?linkid=867219).
    
3. Elija **Descargar**.
    
4. Cuando se le solicite, elija **Ejecutar**.
    
5. En el cuadro de diálogo **WinZip Self-Extractor** , en el cuadro de texto **Descomprimir a carpeta** , escriba o busque la ubicación donde desea instalar la herramienta IdFix. De forma predeterminada, IdFix se instala en `C:\Deployment Tools\`. 
    
6. Elija **descomprima**.
    
## <a name="run-the-idfix-tool"></a>Ejecutar la herramienta IdFix

Después de instalar IdFix, ejecute la herramienta para buscar problemas en el directorio:
  
1. Con una cuenta que tenga acceso de lectura y escritura en el directorio, inicie sesión en el equipo donde ha instalado IdFix.
    
2. En el Explorador de archivos, vaya a la ubicación donde ha instalado IdFix. Si ha elegido la carpeta predeterminada durante la instalación, vaya a `C:\Deployment Tools\IdFix`.
    
3. Haga doble clic en **IdFix.exe**. 
    
    ![Elija el archivo IdFix.exe.](media/a9387bbc-991f-41c2-a500-45e3ce574285.JPG)
  
4. De forma predeterminada, IdFix utiliza la regla de varios inquilino establecer para probar las entradas en el directorio. Ésta es la regla derecha establecido para la mayoría de los clientes de Office 365. Sin embargo, si es un cliente ITAR (tráfico internacional en armas reglamentos) o un dedicados de Office 365, puede configurar IdFix para usar la regla dedicada que se establezca en su lugar. Si no está seguro de qué tipo de cliente es usted, puede omitir sin ningún riesgo este paso. Para establecer el conjunto de reglas que dedicadas, haga clic en el icono del engranaje en la barra de menús y, a continuación, elija **dedicado**.
    
5. Elija la **consulta**.
    
    ![Elija consulta en IdFix.](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. De forma predeterminada, IdFix busca errores en todo el directorio.
    
    Según el tamaño de su directorio, la ejecución de la consulta puede tardar varios minutos. Puede ver el progreso en la parte inferior de la ventana principal de la herramienta. Si hace clic en **Cancelar**, debe reiniciar desde el principio.
    
    ![Recuento de consulta y error de IdFix.](media/da0198a0-7d4d-4afe-a256-e82f1330ada5.JPG)
  
7. Una vez IdFix completada la consulta, puede seguir adelante y sincronizar el directorio si no hay errores. Si hay errores en el directorio, se recomienda solucionarlos antes de sincronizar. Si desea información más específica acerca de los tipos de errores y recomendaciones acerca de la mejor manera de corregir cada uno de ellos, vea los vínculos al final de este tema. 
    
    Aunque no es obligatorio corregir los errores antes de sincronizar, se recomienda encarecidamente revisar al menos todos los errores devueltos por IdFix.
    
    Cada error se muestra en una fila independiente en la ventana principal de la herramienta. 
    
8. Si está de acuerdo con el cambio sugerido en la columna **UPDATE**, en la columna **ACTION** seleccione lo que quiere que IdFix haga para implementar el cambio y luego haga clic en **Aplicar**. Al hacer clic en **Aplicar**, la herramienta hace los cambios en el directorio.
    
    No es necesario hacer clic en **Aplicar** después de cada actualización. En su lugar, puede corregir varios errores antes de hacer clic en **Aplicar** y IdFix las cambiará todos a la vez. Puede ordenar los errores por tipo de error al hacer clic en el **ERROR** en la parte superior de la columna que se enumera los tipos de error. 
    
    Es una estrategia corregir todos los errores del mismo tipo; Por ejemplo, corrija todos los duplicados en primer lugar y aplicarlos. A continuación, corrija los errores de formato de carácter y así sucesivamente. Cada vez que aplica los cambios, la herramienta IdFix crea un archivo de registro independiente que puede usar para deshacer los cambios en el caso de cometer un error. El [registro de transacciones](idfix-transaction-log.md) se almacena en la carpeta que ha instalado IdFix en.  _C:\Deployment Tools\IdFix_ de forma predeterminada. 
    
    ![Solucionar errores en IdFix.](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. Después de todo de los cambios se realizan en el directorio, ejecutar IdFix nuevamente para asegurarse de que las revisiones realizadas no presentan errores nuevos. Puede repetir estos pasos tantas veces como sea necesario. Es una buena idea para ir a través del proceso unas cuantas veces antes de sincronizar.
    
## <a name="i-want-to-refine-my-search-or-dig-deeper-into-the-errors-what-else-can-i-do-with-idfix"></a>Quiero limitar la búsqueda o profundizar en los errores, ¿qué más puedo hacer con IdFix?

Encontrará información detallada en los temas siguientes:
  
- [Prepare los atributos de Active directory para la sincronización con Office 365 mediante el uso de la herramienta IdFix](prepare-directory-attributes-for-synch-with-idfix.md) . Después de instalar la herramienta, saltar a este tema para obtener instrucciones más detalladas acerca de cómo ejecutar la herramienta, los errores habituales que se suelen encontrar, sugiere correcciones, ejemplos y prácticas recomendadas para qué hacer cuando tenga un gran número de errores. 
- [Referencia: Objetos y atributos admitidos y excluidos en IdFix](idfix-excluded-and-supported-objects-and-attributes.md)  
- [Referencia: Registro de transacciones de IdFix de Office 365](idfix-transaction-log.md)
    
## <a name="video-training"></a>Vídeo de aprendizaje

Para obtener más información, consulte la lección, [instalar y usar la herramienta IDFix](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), la mano de aprendizaje de LinkedIn.
  

