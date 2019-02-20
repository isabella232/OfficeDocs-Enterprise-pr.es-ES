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
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: 497593cf-24c6-491c-940b-7c86dcde9de0
description: Proporciona instrucciones sobre cómo usar IdFix para preparar y limpiar el directorio local antes de sincronizar con Office 365.
ms.openlocfilehash: cdfee8178f731d20c799f550d1dacb0a04a72cae
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085099"
---
# <a name="prepare-directory-attributes-for-synchronization-with-office-365-by-using-the-idfix-tool"></a>Preparación de los atributos del directorio para sincronizarlos con Office365 mediante la herramienta IdFix
Este tema contiene instrucciones detalladas sobre cómo ejecutar la herramienta IdFix, algunos errores comunes que puede encontrar, correcciones sugeridas, ejemplos y procedimientos recomendados para lo que debe hacer si tiene un gran número de errores.
  
## <a name="fixing-errors-in-your-directory-by-using-the-idfix-gui"></a>Corregir error en el directorio mediante la GUI de IdFix
[Ejecute la herramienta IdFix de Office 365](install-and-run-idfix.md) para buscar problemas en el directorio y, a continuación, corrija los errores en la interfaz gráfica de usuario, tal y como se describe en este tema. Si la herramienta devuelve una tabla en blanco, entonces no se detectó ningún error. Si hay muchos problemas en el directorio, puede resultar abrumador cuando la herramienta devuelve los errores. Una forma de abordar esto es corregir todos los errores de un tipo en primer lugar y, a continuación, ir al siguiente tipo. 
  
1. Antes de empezar a realizar cambios, revise las recomendaciones que presenta IdFix.
    
2. Mire por encima la lista de errores que proporciona IdFix. Puede ordenar los errores por tipo si hace clic en **ERROR** en la parte superior de la columna que enumera los tipos de errores. Si hay más de un error asociado con un solo atributo, los errores se combinan en una fila. En los casos en los que es posible, IdFix presenta una recomendación de corrección en la columna **UPDATE**. La corrección se basa en una comprobación de los otros atributos asociados con un objeto. Si bien, por lo general, son mejores alternativas que las que están en el directorio, solo usted puede decidir qué es lo mejor. 
    
3. Si IdFix tiene una sugerencia para corregir un error de duplicación, la corrección se identifica mediante uno de los tres indicadores que hay al principio del valor en la columna **Actualizar** , por ejemplo `[E]john.doe@contoso.com`,. Si acepta la sugerencia, cuando aplique el cambio, la marca no se insertará en el directorio. Sólo se aplicará el valor que sigue a la marca de sugerencia, `john.doe@contoso.com`por ejemplo,. Si desea aceptar la sugerencia, seleccione la acción correspondiente en la columna **acción** . Las marcas indican las acciones siguientes: 
    
 - **[C]** Acción sugerida **COMPLETE**. No es necesario editar el valor.
    
 - **[E]** Acción sugerida **EDIT**. El valor debe modificarse para evitar conflictos con otro valor del directorio.
    
 - **[R]** Acción sugerida **REMOVE**. El valor es un proxy SMTP en un objeto no habilitado para correo y probablemente pueda quitarse sin problema.
    
4. Una vez que haya leído y comprendido los errores, actualice la entrada en la columna **Actualizar** con los cambios y, a continuación, en la columna **acción** , seleccione lo que quiere que IdFix haga para implementar el cambio. Por ejemplo, dos usuarios pueden tener `proxyAddress` identificado como duplicado. Solo un usuario puede usar el `proxyAddress` para la entrega de correo. Para solucionar esto, marque la **** columna acción **completada** para el usuario con el valor correcto y marque la **** columna acción **quitar** para el otro usuario. De este modo `proxyAddress` , se quita el atributo del usuario `proxyAddress` al que no pertenece y no se realiza ningún cambio en el usuario `proxyAddress` para el que es correcto.
    
## <a name="common-errors-and-fixes-detected-by-idfix"></a>Errores y correcciones frecuentes detectados por IdFix
En la tabla siguiente se describen los errores detectados por IdFix, se proporcionan las correcciones que la herramienta sugiere más frecuentemente y, en algunos casos, se proporcionan ejemplos de cómo corregirlos.

|**ERROR**|**Descripción del tipo de error**|**Corrección sugerida**|**Ejemplo**|
|:-----|:-----|:-----|:-----|
|**character** | Caracteres no válidos. El valor contiene un carácter que no es válido. | La corrección sugerida para el error que aparece en la columna **UPDATE** muestra el valor sin el carácter que no es válido.  <br/> | Un espacio al final de una dirección de correo válida es un carácter no válido, por ejemplo:  <br/> " `user@contoso.com` "  <br/> Un espacio inicial al principio de una dirección de correo válida es un carácter no válido, por ejemplo:  <br/> " ` user@contoso.com `"  <br/>  El `ú` carácter es un carácter no válido. |
|**duplicate** | Entrada duplicada. El valor tiene un duplicado dentro del ámbito de la consulta. Todos los valores duplicados aparecerán como errores. | Edite o quite los valores para eliminar la duplicación. La herramienta no le sugerirá ninguna corrección para los duplicados. En cambio, deberá elegir cuál de los duplicados es el correcto y eliminar las entradas duplicadas. ||
|**format** | Error de formato. El valor infringe los requisitos de formato para el uso del atributo. | La actualización sugerida mostrará el valor sin los caracteres no válidos. Si no hay caracteres no válidos, en las columnas Update y Value aparecerá lo mismo. Debe determinar lo que realmente desea en la Actualización. La herramienta no le sugerirá ninguna corrección para todos los errores de formato. | Por ejemplo, las direcciones SMTP deben cumplir con RFC 2822 y mailNickName no pueden empezar ni terminar con un punto. Para obtener más información acerca de los requisitos de formato para los atributos de directorio, consulte "preparación de objetos y atributos de directorio" en [Prepárese para aprovisionar usuarios a través de la sincronización de directorios a Office 365](prepare-for-directory-synchronization.md). |
|topleveldomain  <br/> |Dominio de nivel superior. Esto se aplica a los valores sujetos al formato [RFC 2822](https://go.microsoft.com/fwlink/p/?LinkId=401464) . Si el dominio de nivel superior no es enrutable a Internet, se identificará como un error. Por ejemplo, una dirección SMTP que termina en. local no es enrutable a Internet y podría provocar este error. |Cambie el valor a un dominio enrutable de Internet `.com` como `.net`o. | Cambiar `myaddress@fourthcoffee.local` a `fourthcoffee.com` u otro dominio enrutable de Internet.  <br/> Para obtener instrucciones, vea [Cómo preparar un dominio no enrutable (por ejemplo, el dominio. local) para la sincronización de directorios](prepare-a-non-routable-domain-for-directory-synchronization.md). |
|**domainpart** | Error de parte del dominio. Esto se aplica a los valores sujetos al formato de RFC 2822. Si la parte del dominio del valor no es válida y no cumple con la RFC 2822, se generará este error. | Cambie el valor por uno que cumpla con RFC 2822. Por ejemplo, asegúrese de que no contiene espacios ni caracteres no válidos. | Cambie `myaddress@fourth coffee.com` a `myaddress@fourthcoffee.com`. |
|**domainpart_localpart** | Error de parte local. Esto se aplica a los valores sujetos al formato de RFC 2822. Si la parte local del valor no es válida y no cumple con la RFC 2822, se generará este error. |Cambie el valor por uno que cumpla con RFC 2822. Por ejemplo, asegúrese de que no contiene espacios ni caracteres no válidos. |Cambie `my"work"address@fourthcoffee.com` a `myworkaddress@fourthcoffee.com`. |
|**length** | Error de longitud. El valor infringe el límite de longitud establecido para el atributo. Esto surge más frecuentemente cuando se ha alterado el esquema de directorios.  | La actualización que sugiere IdFix truncará el valor a la longitud aceptada.  <br/> Asegúrese de que esto no produzca resultados no deseados. Debe revisar la corrección sugerida y cambiarla si es necesario antes de hacer clic en **Apply**. ||
|**blank**  | En blanco o error nulo. El valor infringe la restricción nula para los atributos que se van a sincronizar. Solo algunos atributos deben contener un valor. | Si es posible, la actualización sugerida aprovechará otros valores de atributo para generar un posible sustituto. ||
|**mailmatch** | Esto se aplica únicamente a Office 365 dedicado. El valor no coincide con el atributo de correo. | La actualización sugerida será el valor de atributo de correo con el prefijo "SMTP:". ||
    
## <a name="operations-you-can-perform-by-using-idfix"></a>Operaciones que se pueden realizar con IdFix
Para corregir un error, seleccione una opción de la lista desplegable **acción** . En la tabla siguiente se describen las operaciones de **acciones** que se pueden realizar en los atributos mediante la herramienta IdFix. Si deja la columna de **acción** vacía, la herramienta IdFix no llevará a cabo ninguna acción sobre ese error específico en el directorio. 

|**ACCIONA**|**Descripción de la acción**|**Ejemplo**|
|:-----|:-----|:-----|
|**COMPLETE** | El valor original es aceptable y no debe modificarse a menos que se identifique como un error. | Dos usuarios tienen el atributo proxyAddress identificado como duplicado. Solo un usuario puede usar el valor para la entrega de correo. Marque al usuario con el valor correcto como **COMPLETE**. |
|**Quite** | El valor de atributo se eliminará del objeto de origen. En el caso de un atributo de varios valores, por ejemplo `proxyAddresses`, solo se eliminará el valor individual que se muestra. | Dos usuarios tienen el atributo proxyAddress identificado como duplicado. Solo un usuario puede usar el valor para la entrega de correo. Marque al usuario con el valor duplicado como **REMOVE**. |
|**EDITAR** | La información de la columna **Actualizar** se utilizará para modificar el valor del atributo. Si IdFix ha sugerido un valor de **actualización** válido, a continuación, en la columna **acción** , seleccione **Editar** y continúe con el siguiente error. Si no le gusta la sugerencia, escriba una nueva en la columna **Actualizar** y, a continuación, en la columna **acción** , seleccione **Editar**. ||
|**VERSIÓN** | Esta opción solo está disponible si ha realizado una restauración de un registro de transacciones. Si selecciona **DESHACER**, el valor del atributo se restaurará a su valor original. ||
|**FAIL** | Este valor solo se devuelve si un valor de **actualización** tiene un conflicto desconocido con las reglas de AD DS. En este caso, puede volver a editar el valor en la columna **Actualizar** si sabe cuál es el error. Puede que sea necesario analizar los valores del objeto mediante el editor ADSI. Para obtener más información, consulte [edición de ADSI (AdsiEdit. msc)](https://go.microsoft.com/fwlink/p/?LinkId=401170). ||

Después de elegir una opción de **ACTION** para un error o un lote de errores, haga clic en **Apply**. Al hacer clic en **Apply**, la herramienta efectúa los cambios en el directorio. Puede proporcionar correcciones para varios errores antes de hacer clic en **Apply** y IdFix los cambiará todos al mismo tiempo.

Ejecute de nuevo IdFix para asegurarse de que las correcciones que ha realizado no han introducido nuevos errores. Puede repetir estos pasos tantas veces como sea necesario. Es una buena idea pasar por el proceso varias veces antes de sincronizar.
    
## <a name="changing-the-rule-set-used-by-idfix"></a>Cambiar el conjunto de reglas que usa IdFix
De forma predeterminada, IdFix usa el conjunto de reglas multiInquilino para probar las entradas del directorio. Este es el conjunto de reglas correcto para la mayoría de los clientes de Office 365 =. Sin embargo, si es cliente de Office 365 dedicado o ITAR (tráfico internacional en las regulaciones de brazos), puede configurar IdFix para usar el conjunto de reglas dedicado en su lugar. Si no está seguro de qué tipo de cliente es, puede omitir este paso de manera segura. Para establecer el conjunto de reglas en dedicado, haga clic en el icono de engranaje en la barra de menús y, a continuación, haga clic en **dedicado**.
  
## <a name="changing-the-scope-of-the-search-used-by-idfix"></a>Cambiar el ámbito de búsqueda que usa IdFix
De forma predeterminada, IdFix busca en todo el directorio. Si lo desea, puede configurar la herramienta para que busque en un subárbol específico. Para ello, en la barra de menús, haga clic en el icono de filtrado y especifique un subárbol válido.
  
## <a name="rolling-back-your-changes-by-using-the-idfix-gui"></a>Revertir los cambios con la GUI de IdFix
Cada vez que haga clic en **aplicar** para aplicar los cambios, la herramienta IdFix crea un archivo independiente denominado registro de transacciones que enumera los cambios que acaba de realizar. Puede usar el registro de transacciones para revertir solo los cambios que se encuentran en el registro más reciente en caso de que comete un error. Si comete un error durante la actualización, puede deshacer los cambios aplicados más recientemente haciendo clic en **Deshacer**. Al hacer clic **** en deshacer, IdFix usa el registro de transacciones para revertir solo los cambios que se encuentran en el registro de transacciones más reciente. Para obtener más información acerca del uso del registro de transacciones, vea [Referencia: registro de transacciones de IdFix de Office 365](idfix-transaction-log.md).