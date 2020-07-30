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
# <a name="download-and-run-the-microsoft-365-idfix-tool"></a>Descargar y ejecutar la herramienta IdFix de Microsoft 365

*Este artículo aplica tanto a Office 365 Enterprise como a Microsoft 365 Enterprise*

IdFix identifica errores como duplicados y problemas de formato en el dominio de los servicios de dominio de Active Directory (AD DS) antes de sincronizar con Microsoft 365. 
  
Para terminar esta tarea correctamente, debe sentirse cómodo trabajando con objetos de usuario, grupo y contacto en AD DS.
  
Si no puede completar esta tarea, hay otras cosas que puede hacer. Es posible que estos métodos sean más fáciles, pero también pueden tardar más tiempo o tener otras desventajas. Son las siguientes:
  
- **Ejecutar la sincronización de directorios sin ejecutar IdFix** 

  Puede sincronizar su directorio sin usar la herramienta IdFix, pero no lo recomendamos. Corregir los errores antes de sincronizar lleva menos tiempo y suele facilitar la transición a la nube. 

- **Contratar a un consultor** 

  Solicitar ayuda a un experto puede poner en marcha a sus usuarios rápidamente y sincronizar el directorio. 
    
## <a name="what-you-need-to-run-idfix"></a>Qué se necesita para ejecutar IdFix

La manera más fácil de poner en marcha IdFix es descargarla en un equipo que esté unido a su dominio de AD DS. Puede ejecutarla en el controlador de dominio si quiere, pero no es necesario.
  
### <a name="idfix-hardware-requirements"></a>Requisitos de hardware de IdFix

El equipo donde descargue IdFix debe cumplir estos requisitos de hardware mínimos:
  
- 4 GB de RAM
- 2 GB de espacio en disco duro.
   
### <a name="idfix-software-requirements"></a>Requisitos de software de IdFix

El equipo donde descargue IdFix necesita estar unido al mismo dominio de AD DS desde el que desea sincronizar usuarios a Microsoft 365. 

El equipo también debe tener .NET Framework 4.0 instalado. Si está ejecutando Windows Server 2008 o posterior, probablemente .NET Framework ya está instalado. Si no es así, puede [descargar .NET 4.0 desde el centro de descarga](https://go.microsoft.com/fwlink/p/?LinkId=400475) o con Windows Update. 
  
### <a name="idfix-permissions-requirements"></a>Requisitos de permisos de IdFix

La cuenta de usuario que use para ejecutar IdFix debe tener acceso de lectura y escritura al dominio de AD DS.
  
Si no está seguro de si su cuenta de usuario cumple con estos requisitos y no sabe cómo comprobarlo, igual puede descargar y ejecutar IdFix. Si su cuenta de usuario no tiene los permisos adecuados, IdFix mostrará un error al intentar ejecutarla.
  
## <a name="download-and-extract-idfix"></a>Descargar y extraer IdFix

Siga estas instrucciones. 
  
1. Inicie sesión en el equipo donde quiere ejecutar la herramienta IdFix.
    
2. Vaya al sitio [herramienta de corrección de errores de sincronización de directorios de IdFix](https://github.com/microsoft/idfix).
    
3. Haga clic en **iniciar** en la sección **inicio de ClickOnce** para descargar el archivo zip. Abra el archivo zip.
    
4. En la ventana **IdFix**, elija **Extraer**y, a continuación, **Extraer todo**. De manera predeterminada, IdFix se extrae a `C:\Users\<your user name>\Documents\IdFix`. 
    
5. Elija **Extraer**.

Los pasos pueden variar en función de su versión de Windows y de su explorador de Internet.
    
## <a name="run-the-idfix-tool"></a>Ejecutar la herramienta IdFix

Después de descargar y extraer IdFix, ejecútela para buscar problemas en el dominio de AD DS.
  
1. Inicie sesión en el equipo en el que descargó IdFix con una cuenta que tenga acceso de lectura y escritura al dominio de AD DS.
    
2. En el Explorador de archivos, vaya a la ubicación donde extrajo IdFix. Si eligió la carpeta predeterminada durante la extracción, vaya a `C:\Users\<your user name>\Documents\IdFix`. 
    
3. Haga doble clic en **IdFix.exe**. 
  
4. De forma predeterminada, IdFix usa el conjunto de reglas multiempresa para probar las entradas del directorio. Este es el conjunto de reglas apropiado para la mayoría de los clientes de Microsoft 365. Sin embargo, si es un cliente de Microsoft 365 dedicado o ITAR (Reglamento internacional de tráfico de armas), puede configurar IdFix para usar el conjunto de reglas Dedicado en su lugar. Si no está seguro de qué tipo de cliente es, puede omitir este paso de forma segura. Para establecer el conjunto de reglas como Dedicado, haga clic en el icono de engranaje en la barra de menús y luego elija **Dedicado**.
    
5. Elija **Consultar**.
    
    ![Seleccione una consulta en IdFix.](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. De forma predeterminada, IdFix busca errores en todo el directorio.
    
    El tiempo que se tarde en ejecutar la consulta depende del tamaño del directorio. Puede ver el progreso en la parte inferior de la ventana principal de la herramienta. Si hace clic en **Cancelar**, tendrá que volver al principio.
  
7. Cuando IdFix termine la consulta, podrá sincronizar su directorio si no hay errores. Si hay errores en el directorio, se recomienda corregirlos antes de sincronizar. Para obtener más información, consulte [preparar los atributos del directorio para la sincronización con Microsoft 365](prepare-directory-attributes-for-synch-with-idfix.md).
    
    Aunque no es obligatorio corregir los errores antes de sincronizar, se recomienda encarecidamente al menos revisar todos los errores devueltos por IdFix. 
    
    Cada error se muestra en una fila distinta en la ventana principal de la herramienta. 
    
8. Si está de acuerdo con el cambio sugerido en la columna **ACTUALIZACIÓN**, en la columna **ACCIÓN** seleccione lo que quiere que IdFix haga para implementar el cambio y luego haga clic en **Aplicar**. Al hacer clic en **Aplicar**, la herramienta realiza los cambios en el directorio.
    
    No tiene que hacer clic en **Aplicar** luego de cada actualización. En su lugar, puede corregir varios errores antes de hacer clic en **Aplicar** y IdFix los cambiará todos al mismo tiempo. Puede ordenar los errores por tipo de error al hacer clic en **ERROR** en la parte superior de la columna que enumera los tipos de error. 
    
    Una estrategia consiste en corregir todos los errores del mismo tipo; por ejemplo, corrija todos los duplicados primero y luego aplíquelos. A continuación, corrija los errores de formato de carácter y así sucesivamente.  Cada vez que aplica los cambios, la herramienta IdFix crea un archivo de registro independiente que puede usar para deshacer los cambios si se equivoca. El [registro de transacciones](idfix-transaction-log.md) se almacena en la carpeta donde extrajo IdFix, que es de forma predeterminada _C:\Users\<your user name>\Documents\IdFix_. 
    
    ![Corrección de errores en IdFix.](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. Después de hacer todos los cambios en el directorio, ejecute IdFix otra vez para garantizar que las correcciones realizadas no contienen nuevos errores. Puede repetir estos pasos la cantidad de veces que sean necesarias. Una buena idea es repetir el proceso un par de veces antes de sincronizar.
    
## <a name="additional-resources-on-idfix"></a>Recursos adicionales en IdFix 

- [Objetos y atributos admitidos y excluidos en IdFix](idfix-excluded-and-supported-objects-and-attributes.md)  
- [Registro de transacciones de IdFix de Microsoft 365](idfix-transaction-log.md)
    
