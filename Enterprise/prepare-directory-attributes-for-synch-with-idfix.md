---
title: Preparación de los atributos del directorio para sincronizarlos con Office365 mediante la herramienta IdFix
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
ms.assetid: 497593cf-24c6-491c-940b-7c86dcde9de0
description: Proporciona instrucciones sobre cómo usar IdFix para preparar y limpiar el directorio local antes de sincronizar a Office 365.
ms.openlocfilehash: a4fc8af476ec8ffdd7d762796abe1ec210a1bacb
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542956"
---
# <a name="prepare-directory-attributes-for-synchronization-with-office-365-by-using-the-idfix-tool"></a>Preparación de los atributos del directorio para sincronizarlos con Office365 mediante la herramienta IdFix
Este tema contiene instrucciones detalladas acerca de cómo ejecutar la herramienta IdFix, algunos errores comunes que puede encontrar, sugiere correcciones, ejemplos y prácticas recomendadas para qué hacer si tiene un gran número de errores.
  
## <a name="fixing-errors-in-your-directory-by-using-the-idfix-gui"></a>Corregir error en el directorio mediante la GUI de IdFix
[Ejecutar la herramienta IdFix de Office 365](install-and-run-idfix.md) para buscar problemas en el directorio y, a continuación, corrija los errores en la interfaz gráfica de usuario, tal como se describe en este tema. Si la herramienta devuelve una tabla en blanco, se han detectado ningún error. Si hay una gran cantidad de problemas en el directorio, puede ser una tarea abrumadora cuando la herramienta devuelve los errores. Una forma de abordar esta necesidad es corregir todos los errores de un tipo en primer lugar y, a continuación, moverse a la siguiente, escriba. 
  
1. Antes de empezar a realizar cambios, revise las recomendaciones que presenta IdFix.
    
2. Mire por encima la lista de errores que proporciona IdFix. Puede ordenar los errores por tipo si hace clic en **ERROR** en la parte superior de la columna que enumera los tipos de errores. Si hay más de un error asociado con un solo atributo, los errores se combinan en una fila. En los casos en los que es posible, IdFix presenta una recomendación de corrección en la columna **UPDATE**. La corrección se basa en una comprobación de los otros atributos asociados con un objeto. Si bien, por lo general, son mejores alternativas que las que están en el directorio, solo usted puede decidir qué es lo mejor. 
    
3. Si IdFix tiene una sugerencia para una solución de un error de duplicación, la corrección es identificada por uno de tres indicadores al principio del valor en la columna de **actualización** , por ejemplo, `[E]john.doe@contoso.com`. Si acepta la sugerencia de, al aplicar el cambio de que la marca no se insertará en el directorio. Sólo el valor sigue la sugerencia de marca se aplicará, por ejemplo, `john.doe@contoso.com`. Si desea aceptar la sugerencia, seleccione la acción coincidente de la columna **acción** . Los indicadores indican las acciones como sigue: 
    
 - **[C]** Acción sugerida **COMPLETE**. No es necesario editar el valor.
    
 - **[E]** Acción sugerida **EDIT**. El valor debe modificarse para evitar conflictos con otro valor del directorio.
    
 - **[R]** Acción sugerida **REMOVE**. El valor es un proxy SMTP en un objeto no habilitado para correo y probablemente pueda quitarse sin problema.
    
4. Una vez que ha leído y comprendido los errores, actualice la entrada en la columna **Actualizar** con los cambios y, a continuación, en la **acción** de la columna Seleccione lo que desea IdFix que hacer para implementar el cambio. Por ejemplo, pueden tener dos usuarios un `proxyAddress` identificado como duplicado. Sólo un usuario puede usar el `proxyAddress` para la entrega de correo. Para solucionar este problema, marque la columna **acción** **completa** para el usuario con el valor correcto y, marque la columna **acción** **Quitar** para el otro usuario. Esto quita el `proxyAddress` atributo desde el usuario a quien esto `proxyAddress` no pertenece y no hace ningún cambio al usuario para el que esto `proxyAddress` es correcta.
    
## <a name="common-errors-and-fixes-detected-by-idfix"></a>Errores y correcciones frecuentes detectados por IdFix
En la tabla siguiente se describen los errores detectados por IdFix, se proporcionan las correcciones que la herramienta sugiere más frecuentemente y, en algunos casos, se proporcionan ejemplos de cómo corregirlos.

|**ERROR**|**Descripción del tipo de error**|**Corrección sugerida**|**Ejemplo**|
|:-----|:-----|:-----|:-----|
|**character** | Caracteres no válidos. El valor contiene un carácter que no es válido. | La corrección sugerida para el error que aparece en la columna **UPDATE** muestra el valor sin el carácter que no es válido.  <br/> | Un espacio al final al final de una dirección de correo válida es un carácter no válido, por ejemplo:  <br/> " `user@contoso.com` "  <br/> Un espacio al principio de una dirección de correo válida es un carácter no válido, por ejemplo:  <br/> " ` user@contoso.com `"  <br/>  El `ú` carácter es un carácter no válido. |
|**duplicate** | Entrada duplicada. El valor tiene un duplicado dentro del ámbito de la consulta. Todos los valores duplicados aparecerán como errores. | Edite o quite los valores para eliminar la duplicación. La herramienta no le sugerirá ninguna corrección para los duplicados. En cambio, deberá elegir cuál de los duplicados es el correcto y eliminar las entradas duplicadas. ||
|**format** | Error de formato. El valor infringe los requisitos de formato para el uso del atributo. | La actualización sugerida mostrará el valor sin los caracteres no válidos. Si no hay caracteres no válidos, en las columnas Update y Value aparecerá lo mismo. Debe determinar lo que realmente desea en la Actualización. La herramienta no le sugerirá ninguna corrección para todos los errores de formato. | Por ejemplo direcciones SMTP deben cumplir con la RFC 2822 y mailNickName no puede comenzar ni terminar con un punto. Para obtener más información acerca de los requisitos de formato para los atributos de Active directory, consulte "Objetos y atributos preparación de Active Directory" en [Prepare to provision a los usuarios a través de sincronización de directorios para Office 365](prepare-for-directory-synchronization.md). |
|topleveldomain  <br/> |Dominio de nivel superior. Esto se aplica a valores sujetos a formato [RFC 2822](https://go.microsoft.com/fwlink/p/?LinkId=401464) . Si el dominio de nivel superior no es enrutable internet Esto se identificó como un error. Por ejemplo, una dirección SMTP que terminan en local no es enrutable internet y hará que este error. |Cambie el valor a un dominio enrutable en internet como `.com` o `.net`. | Cambiar `myaddress@fourthcoffee.local` a `fourthcoffee.com` o en otro dominio enrutable en internet.  <br/> Para obtener instrucciones, vea [cómo preparar un dominio no se puede enrutar (por ejemplo, el dominio local) para la sincronización de Active directory](prepare-a-non-routable-domain-for-directory-synchronization.md). |
|**domainpart** | Error de parte del dominio. Esto se aplica a los valores sujetos al formato de RFC 2822. Si la parte del dominio del valor no es válida y no cumple con la RFC 2822, se generará este error. | Cambie el valor a uno que cumpla con RFC 2822. Por ejemplo, asegúrese de que no contenga espacios ni caracteres no válidos. | Cambiar `myaddress@fourth coffee.com` a `myaddress@fourthcoffee.com`. |
|**domainpart_localpart** | Error de parte local. Esto se aplica a los valores sujetos al formato de RFC 2822. Si la parte local del valor no es válida y no cumple con la RFC 2822, se generará este error. |Cambie el valor a uno que cumpla con RFC 2822. Por ejemplo, asegúrese de que no contenga espacios ni caracteres no válidos. |Cambiar `my"work"address@fourthcoffee.com` a `myworkaddress@fourthcoffee.com`. |
|**length** | Error de longitud. El valor infringe el límite de longitud establecido para el atributo. Esto surge más frecuentemente cuando se ha alterado el esquema de directorios.  | La actualización que sugiere IdFix truncará el valor a la longitud aceptada.  <br/> Asegúrese de que esto no produzca resultados no deseados. Debe revisar la corrección sugerida y cambiarla si es necesario antes de hacer clic en **Apply**. ||
|**blank**  | En blanco o error nulo. El valor infringe la restricción nula para los atributos que se van a sincronizar. Solo algunos atributos deben contener un valor. | Si es posible, la actualización sugerida aprovechará otros valores de atributo para generar un posible sustituto. ||
|**mailmatch** | Esto sólo se aplica a Office 365 dedicado. El valor no coincide con el atributo de correo. | La actualización sugerida será el valor del atributo de correo con el prefijo "SMTP:". ||
    
## <a name="operations-you-can-perform-by-using-idfix"></a>Operaciones que se pueden realizar con IdFix
Para corregir un error, seleccione una opción de la lista desplegable de **acción** . En la siguiente tabla se describe las operaciones de **acción** que puede realizar en atributos con la herramienta IdFix. Si deja en blanco la columna **acción** , la herramienta IdFix no toma ninguna acción en ese error específico en el directorio. 

|**ACCIÓN**|**Descripción de la acción**|**Ejemplo**|
|:-----|:-----|:-----|
|**COMPLETE** | El valor original es aceptable y no debe modificarse a menos que se identifique como un error. | Dos usuarios tienen el atributo proxyAddress identificado como duplicado. Solo un usuario puede usar el valor para la entrega de correo. Marque al usuario con el valor correcto como **COMPLETE**. |
|**QUITAR** | Se eliminará el valor del atributo del objeto de origen. En el caso de un atributo de varios valores, por ejemplo, `proxyAddresses`, se eliminará el valor individual que se muestra. | Dos usuarios tienen el atributo proxyAddress identificado como duplicado. Solo un usuario puede usar el valor para la entrega de correo. Marque al usuario con el valor duplicado como **REMOVE**. |
|**EDITAR** | La información de la columna de **actualización** se usará para modificar el valor del atributo. Si un valor válido de **actualización** ha se ha sugerido por IdFix, a continuación, desde la columna **acción** , seleccione **Editar** y continúe con el siguiente error. Si no le gusta la sugerencia, escriba uno nuevo en la columna de **actualización** y, a continuación, en la columna **acción** , seleccione **Editar**. ||
|**DESHACER** | Esta opción solo está disponible si ha realizado una restauración de un registro de transacciones. Si selecciona **DESHACER**, el valor del atributo se restaurará a su valor original. ||
|**FAIL** | Este valor sólo se devuelve si un valor de **actualización** tiene un conflicto con las reglas de AD DS desconocido. En este caso, puede editar el valor de la columna de **actualización de** nuevo si sabe cuál es el error. Es posible que sea necesario analizar los valores en el objeto mediante el Editor ADSI. Para obtener más información, vea [Edición de ADSI (adsiedit.msc)](https://go.microsoft.com/fwlink/p/?LinkId=401170). ||

Después de elegir una opción de **ACTION** para un error o un lote de errores, haga clic en **Apply**. Al hacer clic en **Apply**, la herramienta efectúa los cambios en el directorio. Puede proporcionar correcciones para varios errores antes de hacer clic en **Apply** y IdFix los cambiará todos al mismo tiempo.

Ejecutar IdFix nuevamente para asegurarse de que las revisiones realizadas no presentan errores nuevos. Puede repetir estos pasos tantas veces como sea necesario. Es una buena idea para ir a través del proceso unas cuantas veces antes de sincronizar.
    
## <a name="changing-the-rule-set-used-by-idfix"></a>Cambiar el conjunto de reglas que usa IdFix
De forma predeterminada, IdFix utiliza la regla de varios inquilino establecer para probar las entradas en el directorio. Ésta es la regla derecha establecido para la mayoría de Office 365 = los clientes. Sin embargo, si es un cliente ITAR (tráfico internacional en armas reglamentos) o un dedicados de Office 365, puede configurar IdFix para usar la regla dedicada que se establezca en su lugar. Si no está seguro de qué tipo de cliente es usted, puede omitir sin ningún riesgo este paso. Para establecer el conjunto de reglas que dedicadas, haga clic en el icono del engranaje en la barra de menús y, a continuación, haga clic en **dedicado**.
  
## <a name="changing-the-scope-of-the-search-used-by-idfix"></a>Cambiar el ámbito de búsqueda que usa IdFix
De forma predeterminada, IdFix busca en todo el directorio. Si lo desea, puede configurar la herramienta para que busque en un subárbol específico. Para ello, en la barra de menús, haga clic en el icono de filtrado y especifique un subárbol válido.
  
## <a name="rolling-back-your-changes-by-using-the-idfix-gui"></a>Revertir los cambios con la GUI de IdFix
Cada vez que haga clic en **Aplicar** para aplicar los cambios, la herramienta IdFix crea un archivo independiente denominado un registro de transacciones que se enumera los cambios que acaba de crear. Puede usar el registro de transacciones para revertir sólo los cambios que están en el registro más reciente en caso de que se equivoca. Si realiza un error mientras está actualizando, puede deshacer los cambios que se ha utilizado más recientemente haciendo clic en **Deshacer**. Al hacer clic en **Deshacer**, IdFix utiliza el registro de transacciones para deshacer sólo los cambios que están en el registro de transacciones más reciente. Para obtener más información acerca del uso del registro de transacciones, vea [referencia: registro de transacciones de IdFix de Office 365](idfix-transaction-log.md).