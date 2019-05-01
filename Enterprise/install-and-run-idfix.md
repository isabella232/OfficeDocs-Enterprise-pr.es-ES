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
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/30/2019
ms.locfileid: "33488026"
---
# <a name="install-and-run-the-office-365-idfix-tool"></a>Instalar y ejecutar la herramienta IdFix de Office 365

IdFix identifica errores como duplicados y problemas de formato en su directorio antes de sincronizar con Office 365. 
  
Para finalizar esta tarea correctamente, debe sentirse cómodo trabajando con objetos de usuario, grupo y contacto en Active Directory.
  
Si no puede completar esta tarea, hay un par de cosas que puede hacer. Estos métodos pueden ser más sencillos, pero también pueden tardar más tiempo o tener otros inconvenientes. Son los siguientes:
  
- **Ejecutar la sincronización de directorios sin ejecutar IdFix.** Puede sincronizar el directorio sin ejecutar la herramienta IdFix, pero no lo recomendamos. La corrección de errores antes de sincronizar requiere menos tiempo y suele proporcionar una transición más fluida a la nube. 
- **Contratar a un consultor.** Obtener ayuda experta puede poner en marcha a sus usuarios rápidamente y sincronizar su directorio. 
    
## <a name="what-you-need-to-run-idfix"></a>Qué necesita para ejecutar IdFix

La forma más sencilla de obtener un IdFix y ejecutarlo es instalarlo en un equipo que se haya unido a su dominio. Si lo desea, puede ejecutarlo en el controlador de dominio, pero no es necesario.
  
### <a name="idfix-hardware-requirements"></a>Requisitos de hardware de IdFix

El equipo donde instale IdFix debe cumplir estos requisitos mínimos de hardware:
  
- 4 GB de RAM
- 2 GB de espacio en disco duro
    
### <a name="idfix-software-requirements"></a>Requisitos de software de IdFix

El equipo donde instale IdFix debe unirse al mismo dominio de Active Directory desde el que desea sincronizar usuarios con Office 365. El equipo también debe tener instalado .NET Framework 4,0. 
  
Si ejecuta Windows Server 2008 o Windows Server 2012, es probable que .NET Framework ya esté instalado. Si no es así, puede [Descargar .net 4,0 desde el centro de descarga](https://go.microsoft.com/fwlink/p/?LinkId=400475) o a través de Windows Update. 
  
### <a name="idfix-permissions-requirements"></a>Requisitos de permisos de IdFix

La cuenta de usuario que usa para ejecutar IdFix debe tener acceso de lectura y escritura en el directorio.
  
Si no está seguro de si su cuenta de usuario cumple estos requisitos y no está seguro de cómo comprobarla, puede instalar y ejecutar IdFix. Si su cuenta de usuario no tiene los permisos adecuados, IdFix simplemente mostrará un error cuando intente ejecutarla.
  
## <a name="install-idfix"></a>Instalar IdFix

Para instalar IdFix, descargue y descomprima **idfix. exe**: 
  
1. Inicie sesión en el equipo donde desea instalar la herramienta IdFix.
    
2. Vaya al sitio de descarga de Microsoft para la [herramienta de corrección de errores de sincronización de directorios de IdFix](https://go.microsoft.com/fwlink/?linkid=867219).
    
3. Elija **Descargar**.
    
4. Cuando se le pida, elija **Ejecutar**.
    
5. En el cuadro de diálogo **WinZip Self-Extractor** , en el cuadro de texto **descomprimir en carpeta** , escriba o busque la ubicación en la que desea instalar la herramienta IdFix. De forma predeterminada, IdFix se instala `C:\Deployment Tools\`en. 
    
6. Elija **descomprimir**.
    
## <a name="run-the-idfix-tool"></a>Ejecutar la herramienta IdFix

Después de instalar IdFix, ejecute la herramienta para buscar problemas en el directorio:
  
1. Con una cuenta que tenga acceso de lectura y escritura en el directorio, inicie sesión en el equipo en el que ha instalado IdFix.
    
2. En el explorador de archivos, vaya a la ubicación en la que ha instalado IdFix. Si eligió la carpeta predeterminada durante la instalación, vaya a `C:\Deployment Tools\IdFix`.
    
3. Haga doble clic en **IdFix. exe**. 
    
    ![Elija el archivo IdFix. exe.](media/a9387bbc-991f-41c2-a500-45e3ce574285.JPG)
  
4. De forma predeterminada, IdFix usa el conjunto de reglas multiInquilino para probar las entradas del directorio. Este es el conjunto de reglas correcto para la mayoría de los clientes de Office 365. Sin embargo, si es cliente de Office 365 dedicado o ITAR (tráfico internacional en las regulaciones de brazos), puede configurar IdFix para usar el conjunto de reglas dedicado en su lugar. Si no está seguro de qué tipo de cliente es, puede omitir este paso de manera segura. Para establecer el conjunto de reglas en dedicado, haga clic en el icono de engranaje en la barra de menús y, a continuación, elija **dedicado**.
    
5. Elija **consultar**.
    
    ![Seleccione consulta en IdFix.](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. De forma predeterminada, IdFix busca errores en todo el directorio.
    
    En función del tamaño del directorio, la ejecución de la consulta puede tardar unos minutos. Puede ver el progreso en la parte inferior de la ventana principal de la herramienta. Si hace clic en **Cancelar**, deberá reiniciar desde el principio.
    
    ![Número de consultas y errores de IdFix.](media/da0198a0-7d4d-4afe-a256-e82f1330ada5.JPG)
  
7. Después de que IdFix complete la consulta, puede seguir adelante y sincronizar su directorio si no hay errores. Si hay errores en el directorio, se recomienda que los solucione antes de sincronizar. Si desea información más específica acerca de los tipos de errores y las recomendaciones sobre la mejor manera de solucionarlos, vea los vínculos que se encuentra al final de este tema. 
    
    Aunque no es obligatorio corregir los errores antes de sincronizar, se recomienda encarecidamente que, al menos, revise todos los errores devueltos por IdFix.
    
    Cada error se muestra en una fila independiente en la ventana principal de la herramienta. 
    
8. Si está de acuerdo con el cambio sugerido en la columna **Actualizar** , en la columna **acción** , seleccione qué desea hacer con IdFix para implementar el cambio y, a continuación, haga clic en **aplicar**. Al hacer clic en **aplicar**, la herramienta realiza los cambios en el directorio.
    
    No es necesario hacer clic en **aplicar** después de cada actualización. En su lugar, puede corregir varios errores antes de hacer clic en **aplicar** y IdFix los cambiará a la vez. Puede ordenar los errores por tipo de error haciendo clic en **error** en la parte superior de la columna que enumera los tipos de error. 
    
    Una estrategia consiste en corregir todos los errores del mismo tipo; por ejemplo, primero Corrija todos los duplicados y aplíquelos. A continuación, corrija los errores de formato de carácter y así sucesivamente. Cada vez que se aplican los cambios, la herramienta IdFix crea un archivo de registro independiente que se puede usar para deshacer los cambios en caso de que se cometa un error. El [registro de transacciones](idfix-transaction-log.md) se almacena en la carpeta en la que ha instalado IdFix.  _C:\Deployment Tools\IdFix_ de forma predeterminada. 
    
    ![Corregir errores en IdFix.](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. Una vez que se hayan realizado todos los cambios en el directorio, ejecute IdFix de nuevo para asegurarse de que las correcciones que ha realizado no han introducido nuevos errores. Puede repetir estos pasos tantas veces como sea necesario. Es una buena idea pasar por el proceso varias veces antes de sincronizar.
    
## <a name="i-want-to-refine-my-search-or-dig-deeper-into-the-errors-what-else-can-i-do-with-idfix"></a>Quiero restringir la búsqueda o profundizar en los errores, ¿qué más puedo hacer con IdFix?

Encontrará información detallada en estos temas:
  
- [Preparar atributos de directorio para la sincronización con Office 365 mediante la herramienta IdFix](prepare-directory-attributes-for-synch-with-idfix.md) . Una vez instalada la herramienta, vaya a este tema para obtener instrucciones más detalladas sobre cómo ejecutar la herramienta, los errores comunes que encontrará, las correcciones sugeridas, los ejemplos y los procedimientos recomendados para lo que debe hacer cuando tiene un gran número de errores. 
- [Referencia: objetos y atributos admitidos y excluidos en IdFix](idfix-excluded-and-supported-objects-and-attributes.md)  
- [Referencia: registro de transacciones de IdFix de Office 365](idfix-transaction-log.md)
    
## <a name="video-training"></a>Vídeo de aprendizaje

Para obtener más información, vea la lección [instalación y uso de la herramienta IDFix](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), que le ha ofrecido LinkedIn Learning.
  

