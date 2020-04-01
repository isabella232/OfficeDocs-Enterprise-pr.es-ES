---
title: Descargar y ejecutar la herramienta IdFix de Office 365
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
description: Cómo descargar y ejecutar la herramienta IdFix de Office 365 para ayudar a limpiar los servicios de dominio de Active Directory (AD DS) antes de sincronizarlos con Office 365.
ms.openlocfilehash: d816abe8e93830832077c614e496576d42890d50
ms.sourcegitcommit: 7f025939c9dad676602bcd7693a8e356821fd456
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/31/2020
ms.locfileid: "43068782"
---
# <a name="download-and-run-the-office-365-idfix-tool"></a>Descargar y ejecutar la herramienta IdFix de Office 365

*Este artículo se aplica tanto a Office 365 Enterprise como a Microsoft 365 Enterprise.*

IdFix identifica errores como duplicados y problemas de formato en el dominio de servicios de dominio de Active Directory (AD DS) antes de sincronizar con Office 365. 
  
Para finalizar esta tarea correctamente, debe sentirse cómodo trabajando con objetos de usuario, grupo y contacto en AD DS.
  
Si no puede completar esta tarea, hay un par de cosas que puede hacer. Estos métodos pueden ser más sencillos, pero también pueden tardar más tiempo o tener otros inconvenientes. Son los siguientes:
  
- **Ejecutar la sincronización de directorios sin ejecutar IdFix** 

  Puede sincronizar su directorio sin usar la herramienta IdFix, pero no lo recomendamos. La corrección de errores antes de sincronizar requiere menos tiempo y suele proporcionar una transición más fluida a la nube. 

- **Contratar a un consultor** 

  Obtener ayuda experta puede poner en marcha a sus usuarios rápidamente y sincronizar su directorio. 
    
## <a name="what-you-need-to-run-idfix"></a>Qué necesita para ejecutar IdFix

La forma más sencilla de iniciar IdFix en funcionamiento es descargarlo en un equipo que se haya unido a su dominio de AD DS. Si lo desea, puede ejecutarlo en el controlador de dominio, pero no es necesario.
  
### <a name="idfix-hardware-requirements"></a>Requisitos de hardware de IdFix

El equipo en el que se descarga IdFix debe cumplir estos requisitos mínimos de hardware:
  
- 4 GB de RAM
- 2 GB de espacio en disco duro
   
### <a name="idfix-software-requirements"></a>Requisitos de software de IdFix

El equipo donde Descargue IdFix debe unirse al mismo dominio de AD DS desde el que desea sincronizar usuarios a Office 365. 

El equipo también debe tener instalado .NET Framework 4,0. Si ejecuta Windows Server 2008 o posterior, es probable que .NET Framework ya esté instalado. Si no es así, puede [Descargar .net 4,0 desde el centro de descarga](https://go.microsoft.com/fwlink/p/?LinkId=400475) o con Windows Update. 
  
### <a name="idfix-permissions-requirements"></a>Requisitos de permisos de IdFix

La cuenta de usuario que use para ejecutar IdFix debe tener acceso de lectura y escritura al dominio de AD DS.
  
Si no está seguro de si su cuenta de usuario cumple estos requisitos y no está seguro de cómo comprobarla, puede descargar y ejecutar IdFix. Si su cuenta de usuario no tiene los permisos adecuados, IdFix simplemente mostrará un error cuando intente ejecutarla.
  
## <a name="download-and-extract-idfix"></a>Descargar y extraer IdFix

Siga estas instrucciones. 
  
1. Inicie sesión en el equipo en el que desea ejecutar la herramienta IdFix.
    
2. Vaya al sitio de la [herramienta de corrección de errores de sincronización de directorios de IdFix](https://github.com/microsoft/idfix) .
    
3. Haga clic en **iniciar** en la sección **iniciar ClickOnce** para descargar el archivo zip. Abra el archivo zip.
    
4. En la ventana de **IdFix** , elija **extraer**y, a continuación, **extraer todo**. De forma predeterminada, IdFix se extrae a `C:\Users\<your user name>\Documents\IdFix`. 
    
5. Elija **Extraer**.

Los pasos pueden variar en función de la versión de Windows y el explorador de Internet.
    
## <a name="run-the-idfix-tool"></a>Ejecutar la herramienta IdFix

Después de descargar y extraer IdFix, ejecútelo para buscar problemas en su dominio de AD DS.
  
1. Inicie sesión en el equipo donde descargó IdFix con una cuenta que tenga acceso de lectura y escritura en su dominio de AD DS.
    
2. En el explorador de archivos, vaya a la ubicación donde extrajo IdFix. Si eligió la carpeta predeterminada durante la extracción, vaya a `C:\Users\<your user name>\Documents\IdFix`. 
    
3. Haga doble clic en **IdFix. exe**. 
  
4. De forma predeterminada, IdFix usa el conjunto de reglas multiinquilino para probar las entradas del directorio. Este es el conjunto de reglas correcto para la mayoría de los clientes de Office 365. Sin embargo, si es un cliente de Office 365 dedicado o internacional tráfico en las regulaciones de brazos (ITAR)), puede configurar IdFix para usar el conjunto de reglas dedicado en su lugar. Si no está seguro de qué tipo de cliente es, puede omitir este paso de manera segura. Para establecer el conjunto de reglas en dedicado, haga clic en el icono de engranaje en la barra de menús y, a continuación, elija **dedicado**.
    
5. Elija **consultar**.
    
    ![Seleccione consulta en IdFix.](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. De forma predeterminada, IdFix busca errores en todo el directorio.
    
    En función del tamaño del directorio, la ejecución de la consulta puede tardar unos minutos. Puede ver el progreso en la parte inferior de la ventana principal de la herramienta. Si hace clic en **Cancelar**, deberá reiniciar desde el principio.
  
7. Después de que IdFix complete la consulta, puede sincronizar el directorio si no hay errores. Si hay errores en el directorio, se recomienda que los solucione antes de sincronizar. Consulte [preparar atributos de directorio para la sincronización con Office 365](prepare-directory-attributes-for-synch-with-idfix.md) para obtener más información.
    
    Aunque no es obligatorio corregir los errores antes de sincronizar, se recomienda encarecidamente que, al menos, revise todos los errores devueltos por IdFix.
    
    Cada error se muestra en una fila independiente en la ventana principal de la herramienta. 
    
8. Si está de acuerdo con el cambio sugerido en la columna **Actualizar** , en la columna **acción** , seleccione qué desea hacer con IdFix para implementar el cambio y, a continuación, haga clic en **aplicar**. Al hacer clic en **aplicar**, la herramienta realiza los cambios en el directorio.
    
    No es necesario hacer clic en **aplicar** después de cada actualización. En su lugar, puede corregir varios errores antes de hacer clic en **aplicar** y IdFix los cambiará a la vez. Puede ordenar los errores por tipo de error haciendo clic en **error** en la parte superior de la columna que enumera los tipos de error. 
    
    Una estrategia consiste en corregir todos los errores del mismo tipo; por ejemplo, primero Corrija todos los duplicados y aplíquelos. A continuación, corrija los errores de formato de carácter y así sucesivamente. Cada vez que se aplican los cambios, la herramienta IdFix crea un archivo de registro independiente que se puede usar para deshacer los cambios en caso de que se cometa un error. El [registro de transacciones](idfix-transaction-log.md) se almacena en la carpeta en la que extrajo IdFix, que es _C:\Users\<su nombre de usuario> \documents\idfix_ de forma predeterminada. 
    
    ![Corregir errores en IdFix.](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. Una vez que se hayan realizado todos los cambios en el directorio, ejecute IdFix de nuevo para asegurarse de que las correcciones que ha realizado no han introducido nuevos errores. Puede repetir estos pasos tantas veces como sea necesario. Es una buena idea pasar por el proceso varias veces antes de sincronizar.
    
## <a name="additional-resources-on-idfix"></a>Recursos adicionales en IdFix 

- [Objetos y atributos admitidos y excluidos en IdFix](idfix-excluded-and-supported-objects-and-attributes.md)  
- [Registro de transacciones de IdFix de Office 365](idfix-transaction-log.md)
    
## <a name="video-training"></a>Vídeo de aprendizaje

Para obtener más información, vea la lección [instalación y uso de la herramienta IdFix](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), que le ha ofrecido LinkedIn Learning.
  

