---
title: Uso de la red de entrega de contenido (CDN) de Office 365 con SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/22/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: bebb285f-1d54-4f79-90a5-94985afc6af8
description: Describe cómo usar la red de entrega de contenido (CDN) de Office 365 para acelerar la entrega de los activos de SharePoint Online a todos los usuarios, independientemente de dónde se encuentren o de la forma en que tengan acceso al contenido.
ms.openlocfilehash: 60016fff28ca7c71555e141ef479d32fdd6d7856
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2019
ms.locfileid: "38031435"
---
# <a name="use-the-office-365-content-delivery-network-cdn-with-sharepoint-online"></a>Uso de la red de entrega de contenido (CDN) de Office 365 con SharePoint Online

Puede usar la red de entrega de contenido (CDN) de Office 365 integrada para hospedar archivos estáticos y mejorar el rendimiento de las páginas de SharePoint Online. La CDN de Office 365 mejora el rendimiento al almacenamiento en caché los archivos estáticos más cerca de los exploradores que los solicitan, lo que ayuda a acelerar descargas y reducir la latencia. Además, la red CDN de Office 365 usa el [protocolo http/2](https://en.wikipedia.org/wiki/HTTP/2) para mejorar la compresión y la canalización http. La red CDN de Office 365 se incluye como parte de la suscripción a SharePoint Online.

> [!NOTE]
> La red CDN de Office 365 solo está disponible para los inquilinos en la nube de **producción** (en todo el mundo). Actualmente, los inquilinos de las nubes del gobierno de Estados Unidos, China y Alemania no admiten la red CDN de Office 365.

La CDN de Office 365 se compone de varias redes CDN que permite hospedar archivos estáticos en varias ubicaciones u _orígenes_ y a realizar la entrega desde redes de alta velocidad globales. Según el tipo de contenido que quiera hospedar en la CDN de Office 365, puede agregar orígenes **públicos**, **privados** o ambos. Vea [elegir si cada origen debe ser público o privado](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate) para obtener más información sobre la diferencia entre los orígenes públicos y privados.

![Diagrama conceptual de la red CDN de Office 365](media/O365-CDN/o365-cdn-flow-transparent.svg "Diagrama conceptual de la red CDN de Office 365")

Si ya está familiarizado con la forma en que las redes CDN funcionan, solo tiene que realizar algunos pasos para habilitar la red CDN de Office 365 para su inquilino. En este tema se describe cómo hacerlo. Siga leyendo para obtener información sobre cómo empezar a hospedar sus activos estáticos.

> [!TIP]
> Hay otras CDN hospedadas por Microsoft que se pueden usar con Office 365 para escenarios de uso especializados, pero que no se tratan en este tema porque quedan fuera del ámbito de la red CDN de Office 365. Para obtener más información, consulte [otros CDN de Microsoft](content-delivery-networks.md#other-microsoft-cdns).

 **Vuelva a la [planeación de red y ajuste del rendimiento para Office 365](https://aka.ms/tune).**

## <a name="overview-of-working-with-the-office-365-cdn-in-sharepoint-online"></a>Información general sobre el uso de la red CDN de Office 365 en SharePoint Online

Para configurar la red CDN de Office 365 para su organización, siga estos pasos básicos:

+ [Planeación de la implementación de la red CDN de Office 365](use-office-365-cdn-with-spo.md#plan-for-deployment-of-the-office-365-cdn)

  + [Determine qué activos estáticos desea hospedar en la red CDN](use-office-365-cdn-with-spo.md#CDNAssets).
  + [Determine dónde desea almacenar los activos](use-office-365-cdn-with-spo.md#CDNStoreAssets). Esta ubicación puede ser un sitio de SharePoint, una biblioteca o una carpeta y se denomina _origen_.
  + [Elija si cada origen debe ser público o privado](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate). Puede agregar varios orígenes de tipos públicos y privados.

+ Instalar y configurar la red CDN mediante PowerShell o la CLI de SharePoint Online

  + [Instalar y configurar la red CDN mediante el shell de administración de SharePoint Online](use-office-365-cdn-with-spo.md#CDNSetupinPShell)
  + [Instalar y configurar la red CDN mediante la CLI de Office 365](use-office-365-cdn-with-spo.md#CDNSetupinCLI)

  Cuando haya completado este paso, tendrá:

  + Habilitó la red CDN para su organización.
  + Se agregaron sus orígenes, identificando cada origen como público o privado.

Una vez que haya terminado con el programa de instalación, puede [administrar la red CDN de Office 365](use-office-365-cdn-with-spo.md#CDNManage) con el tiempo:
  
+ Adición, actualización y eliminación de activos
+ Agregar y quitar orígenes
+ Configuración de directivas de CDN
+ Si es necesario, deshabilitar la red CDN

Por último, vea [usar los activos de la red CDN](use-office-365-cdn-with-spo.md#using-your-cdn-assets) para obtener información sobre cómo obtener acceso a los recursos de la red CDN desde orígenes públicos y privados.

Consulte [Troubleshooting The Office 365 CDN](use-office-365-cdn-with-spo.md#CDNTroubleshooting) para obtener instrucciones sobre cómo resolver problemas comunes.

## <a name="plan-for-deployment-of-the-office-365-cdn"></a>Planeación de la implementación de la red CDN de Office 365

Antes de implementar la red CDN de Office 365 para su inquilino de Office 365, debe tener en cuenta los siguientes factores como parte del proceso de planeación.

  + [Determinación de los activos estáticos que desea hospedar en la red CDN](use-office-365-cdn-with-spo.md#CDNAssets)
  + [Determinar dónde desea almacenar los activos](use-office-365-cdn-with-spo.md#CDNStoreAssets)
  + [Elegir si cada origen debe ser público o privado](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)

<a name="CDNAssets"> </a>
### <a name="determine-which-static-assets-you-want-to-host-on-the-cdn"></a>Determinación de los activos estáticos que desea hospedar en la red CDN

En general, las CDN son más eficaces para hospedar _activos estáticos_o activos que no cambian muy a menudo. Una buena regla general es identificar los archivos que cumplan algunas o todas estas condiciones:

+ Archivos estáticos incrustados en una página (como scripts e imágenes) que pueden tener un impacto incremental importante en los tiempos de carga de la página
+ Archivos grandes como archivos ejecutables y archivos de instalación
+ Bibliotecas de recursos que admiten código del lado cliente

Por ejemplo, los archivos pequeños que se solicitan repetidamente como las imágenes de sitio y las secuencias de comandos pueden mejorar significativamente el rendimiento de la representación del sitio y reducir de forma incremental la carga en los sitios de SharePoint Online cuando se agregan a un origen de CDN. Los archivos de mayor tamaño, como los ejecutables de instalación, se pueden descargar desde la red CDN, lo que ofrece un impacto positivo en el rendimiento y una reducción posterior de la carga en el sitio de SharePoint Online, incluso si no se tiene acceso a ellos con tanta frecuencia.

La mejora del rendimiento para cada archivo depende de muchos factores, como la proximidad del cliente al extremo de la red CDN más cercano, las condiciones transitorias de la red local, etc. Muchos archivos estáticos son muy pequeños y se pueden descargar de Office 365 en menos de un segundo. Sin embargo, una página web puede contener muchos archivos incrustados con un tiempo de descarga acumulado de varios segundos. El servicio de estos archivos desde la red CDN puede reducir significativamente el tiempo de carga de página general. Consulte [¿Qué beneficios de rendimiento proporciona una red CDN?](content-delivery-networks.md#what-performance-gains-does-a-cdn-provide) para obtener un ejemplo.

<a name="CDNStoreAssets"> </a>
### <a name="determine-where-you-want-to-store-your-assets"></a>Determinar dónde desea almacenar los activos

La red CDN recopila los activos de una ubicación denominada _origen_. Un origen puede ser un sitio de SharePoint, una biblioteca de documentos o una carpeta a la que se pueda tener acceso mediante una dirección URL. Tiene gran flexibilidad al especificar los orígenes de su organización. Por ejemplo, puede especificar varios orígenes o un único origen donde desea colocar todos los activos de la red CDN. Puede elegir entre los orígenes públicos o privados de su organización. La mayoría de las organizaciones optarán por implementar una combinación de ambos.

Puede crear un nuevo contenedor para sus orígenes, como carpetas o bibliotecas de documentos, y agregar archivos que desee que estén disponibles desde la red CDN. Este es un buen enfoque si tiene un conjunto específico de activos que desea que esté disponible desde la red CDN y desea restringir el conjunto de activos de la red CDN solo a los archivos del contenedor.

También puede configurar una colección de sitios, un sitio, una biblioteca o una carpeta existentes como un origen, lo que hará que todos los activos elegibles del contenedor estén disponibles desde la red CDN. Antes de agregar un contenedor existente como origen, es importante asegurarse de que está al tanto de su contenido y permisos para que no exponga involuntariamente los activos al acceso anónimo o a los usuarios no autorizados.

Puede definir _directivas de CDN_ para excluir el contenido de los orígenes de la red CDN. Las directivas de CDN excluyen los activos de los orígenes públicos o privados mediante atributos como el _tipo de archivo_ y la _clasificación del sitio_, y se aplican a todos los orígenes del CdnType (privado o público) que especifique en la Directiva. Por ejemplo, si agrega un origen privado que consta de un sitio que contiene varios subsitios, puede definir una directiva para excluir los sitios marcados como **confidenciales** para que el contenido de los sitios con esa clasificación aplicada no se atienda desde la red CDN. La Directiva se aplicará al contenido de _todos los_ orígenes privados que haya agregado a la red CDN.
  
Tenga en cuenta que cuanto mayor sea el número de orígenes, mayor será el impacto en el tiempo que tarda el servicio de la red CDN en procesar las solicitudes. Le recomendamos que limite el número de orígenes tanto como sea posible.
  
<a name="CDNOriginChoosePublicPrivate"> </a>
### <a name="choose-whether-each-origin-should-be-public-or-private"></a>Elegir si cada origen debe ser público o privado

Cuando se identifica un origen, se especifica si se debe hacer _público_ o _privado_. El acceso a los activos de CDN en los orígenes públicos es anónimo y el contenido de la red CDN en los orígenes privados está protegido mediante tokens generados dinámicamente para una mayor seguridad. Independientemente de la opción que elija, Microsoft realiza todo el levantamiento en su caso cuando se trata de administrar la red CDN. Además, puede cambiar de opinión más adelante, una vez que haya configurado la red CDN y identificado sus orígenes.

Tanto las opciones públicas como las privadas proporcionan mejoras de rendimiento similares, pero cada una tiene atributos y ventajas únicos.

Se puede obtener acceso a los orígenes **públicos** de la red CDN de Office 365 de forma anónima y cualquier usuario que tenga la dirección URL para el activo podrá acceder a los recursos hospedados. Como el acceso al contenido en orígenes públicos es anónimo, solo debe usarlos para almacenar en caché contenido genérico y no confidencial, como archivos javascript, scripts, iconos e imágenes.

Los orígenes **privados** de la red CDN de Office 365 proporcionan acceso privado al contenido del usuario, como las bibliotecas de documentos de SharePoint Online, los sitios y las imágenes de propietario. El acceso al contenido de orígenes privados está protegido por tokens generados dinámicamente, por lo que solo los usuarios con permisos para la biblioteca de documentos o la ubicación de almacenamiento originales pueden tener acceso a ellos. Los orígenes privados de la red CDN de Office 365 solo se pueden usar para el contenido de SharePoint Online y solo puede tener acceso a activos en orígenes privados mediante el redireccionamiento desde su espacio empresarial de SharePoint Online.

Puede obtener más información sobre cómo el acceso de la red CDN a los activos de un origen privado trabaja en el [uso de activos en orígenes privados](use-office-365-cdn-with-spo.md#using-assets-in-private-origins).

#### <a name="attributes-and-advantages-of-hosting-assets-in-public-origins"></a>Atributos y ventajas de hospedar activos en orígenes públicos
  
+ Cualquier persona puede acceder a los activos expuestos en un origen público de forma anónima.
    > [!IMPORTANT]
    > Nunca debe poner recursos que contengan información de usuario o que se consideren confidenciales para su organización en un origen público.
+ Si elimina un activo de un origen público, el activo podría continuar disponible durante un máximo de 30 días desde la memoria caché. Sin embargo, se invalidarán los vínculos a los activos en la red CDN en 15 minutos.
+ Si hospeda hojas de estilo (archivos CSS) en un origen público, puede usar las rutas relativas y URI dentro del código. Esto significa que puede hacer referencia a la ubicación de las imágenes de fondo y otros objetos con respecto a la ubicación del activo que está llamando.
+ Aunque puede integrar una dirección URL de un origen público, no se recomienda. El motivo de esto es que, si no está disponible el acceso a la red CDN, la dirección URL no resolverá automáticamente su organización en SharePoint Online y podría producir vínculos rotos y otros errores.
+ Los tipos de archivo predeterminado que se incluyen en los orígenes públicos son: css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf y .woff. Puede especificar tipos de archivo adicionales.
+ Puede configurar una directiva para excluir los activos que han sido identificados por las clasificaciones de sitio que especifique. Por ejemplo, puede elegir excluir todos los activos que están marcados como restringidos o confidenciales aunque sean un tipo de archivo permitido y se encuentren en un origen público.

#### <a name="attributes-and-advantages-of-hosting-assets-in-private-origins"></a>Atributos y ventajas de hospedar activos en orígenes privados

+ Los orígenes privados solo pueden usarse para los activos de SharePoint Online.
+ Los usuarios solo pueden tener acceso a los activos desde un origen privado si tienen permisos de acceso al contenedor. Se impide el acceso anónimo a estos activos.
+ Los activos en orígenes privados deben remitirse desde el espacio empresarial de SharePoint Online. El acceso directo a los activos de la red CDN privada no funciona.
+ Si quita un activo del origen privado, el activo puede seguir estando disponible hasta una hora de la caché; sin embargo, se invalidarán los vínculos al activo en la red CDN en un plazo de 15 minutos a partir de la eliminación del activo.
+ Los tipos de archivo predeterminados que se incluyen en el origen privado son .gif, .ico, .jpeg, .jpg, .js y .png. Puede especificar tipos de archivo adicionales.
+ Al igual que con los orígenes públicos, puede configurar una directiva para excluir los activos que se han identificado mediante las clasificaciones de sitio que especifique incluso si usa caracteres comodín para incluir todos los activos dentro de una carpeta o una biblioteca de documentos.

Para obtener más información sobre por qué usar la red CDN de Office 365, los conceptos generales de CDN y otros CDN de Microsoft que puede usar con el inquilino de Office 365, consulte [redes de entrega de contenido](content-delivery-networks.md).

### <a name="default-cdn-origins"></a>Orígenes de red CDN predeterminados

A menos que especifique lo contrario, Office 365 configura algunos orígenes predeterminados cuando habilita la red CDN de Office 365. Si inicialmente opta por no aprovisionarlos, puede agregar estos orígenes después de completar la instalación. A menos que comprenda las consecuencias de omitir la configuración de orígenes predeterminados y tenga una razón específica para hacerlo, debería permitir que se creen al habilitar la red CDN.
  
Orígenes de red CDN privados predeterminados:
  
+ \*/userphoto.aspx
+ \*/siteassets

Orígenes de la red CDN pública predeterminada:
  
+ \*/masterpage
+ \*Biblioteca/Style
+ \*/clientsideassets

> [!NOTE]
> _clientsideassets_ es un origen público predeterminado que se agregó al servicio de la red CDN de Office 365 en diciembre de 2017. Este origen debe estar presente para que funcionen las soluciones de SharePoint Framework en la red CDN. Si habilitó la red CDN de Office 365 antes de diciembre de 2017 o si ha omitido la configuración de los orígenes predeterminados cuando habilitó la red CDN, puede Agregar este origen manualmente. Para obtener más información, vea [el elemento Web del lado cliente o la solución de SharePoint Framework no funciona](use-office-365-cdn-with-spo.md#my-client-side-web-part-or-sharepoint-framework-solution-isnt-working).

<a name="CDNSetupinPShell"> </a>
## <a name="set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell"></a>Instalar y configurar la red CDN de Office 365 mediante el shell de administración de SharePoint Online

Los procedimientos de esta sección requieren que use el shell de administración de SharePoint Online para conectarse a SharePoint Online. Para obtener instrucciones, consulte [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).

Siga estos pasos para configurar y configurar la red CDN para hospedar los activos en SharePoint Online mediante el shell de administración de SharePoint Online.

<details>
  <summary>Haga clic para expandir</summary>

### <a name="enable-your-organization-to-use-the-office-365-cdn"></a>Habilitación de la organización para que use la red CDN de Office 365

Antes de realizar cambios en la configuración de la red CDN del inquilino, debe recuperar el estado actual de la configuración de la red CDN privada en su inquilino de Office 365. Conéctese a su inquilino mediante el shell de administración de SharePoint Online:

``` powershell
Connect-SPOService -Url https://contoso-admin.sharepoint.com
```

Ahora, use el cmdlet **Get-SPOTenantCdnEnabled** para recuperar la configuración de estado de la red CDN del espacio empresarial:

``` powershell
Get-SPOTenantCdnEnabled -CdnType <Public | Private>
```

El estado de la red CDN para el CdnType especificado se mostrará en la pantalla.

Use el cmdlet **set-SPOTenantCdnEnabled** para permitir que su organización use la red CDN de Office 365. Puede habilitar a su organización para que use orígenes públicos, orígenes privados o ambos a la vez. También puede configurar la red CDN para omitir la configuración de los orígenes predeterminados al habilitarla. Siempre puede agregar estos orígenes más adelante, tal y como se describe en este tema.
  
En Windows PowerShell para SharePoint Online:

``` powershell
Set-SPOTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

Por ejemplo, para permitir que su organización use orígenes públicos y privados, escriba el siguiente comando:

``` powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

Para permitir que su organización use orígenes públicos y privados, pero omitir la configuración de los orígenes predeterminados, escriba el siguiente comando:

``` powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

Vea [orígenes de la red CDN predeterminados](use-office-365-cdn-with-spo.md#default-cdn-origins) para obtener información sobre los orígenes que se aprovisionan de forma predeterminada al habilitar la red CDN de Office 365 y el impacto potencial de omitir la configuración de orígenes predeterminados.

Para permitir que su organización use orígenes públicos, escriba el siguiente comando:

``` powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $true
```

Para permitir que su organización use orígenes privados, escriba el siguiente comando:

``` powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $true
```

Para obtener más información sobre este cmdlet, vea [set-SPOTenantCdnEnabled](https://technet.microsoft.com/library/mt790765.aspx).

<a name="Office365CDNforSPOFileType"> </a>
### <a name="change-the-list-of-file-types-to-include-in-the-office-365-cdn-optional"></a>Cambiar la lista de tipos de archivo que se van a incluir en la red CDN de Office 365 (opcional)

> [!TIP]
> Al definir los tipos de archivo con el cmdlet **set-SPOTenantCdnPolicy** , se sobrescribe la lista definida actualmente. Si desea agregar otros tipos de archivo a la lista, use primero el cmdlet para averiguar qué tipos de archivo ya están permitidos e incluirlos en la lista junto con los nuevos.
  
Use el cmdlet **set-SPOTenantCdnPolicy** para definir los tipos de archivo estáticos que se pueden hospedar en orígenes públicos y privados en la red CDN. De forma predeterminada, se permiten los tipos de activos comunes, por ejemplo,. CSS,. gif,. jpg y. js.

En Windows PowerShell para SharePoint Online:

``` powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

Por ejemplo, para permitir que la red CDN hospede archivos. CSS y. png, tendría que escribir el comando:

``` powershell
Set-SPOTenantCdnPolicy -CdnType Private -PolicyType IncludeFileExtensions -PolicyValue "CSS,PNG"
```

Para ver qué tipos de archivo están permitidos actualmente en la red CDN, use el cmdlet **Get-SPOTenantCdnPolicies** :

``` powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

Para obtener más información acerca de estos cmdlets, consulte [set-SPOTenantCdnPolicy](https://technet.microsoft.com/library/mt800839.aspx) y [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/library/mt800838.aspx).

<a name="Office365CDNforSPOSiteClassification"> </a>
### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn-optional"></a>Cambiar la lista de clasificaciones de sitio que desea excluir de la red CDN de Office 365 (opcional)

> [!TIP]
> Cuando excluya las clasificaciones de sitios con el cmdlet **set-SPOTenantCdnPolicy** , se sobrescribirá la lista definida actualmente. Si quiere excluir clasificaciones de sitios adicionales, use primero el cmdlet para averiguar qué clasificaciones ya se excluyen y, a continuación, agréguelos junto con los nuevos.

Use el cmdlet **Set-SPOTenantCdnPolicy** para excluir las clasificaciones de sitio que no desee que estén disponibles en la red CDN. De forma predeterminada, no se excluyen clasificaciones de sitio.

En Windows PowerShell para SharePoint Online:

``` powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications >"
```

Para ver qué clasificaciones de sitio están restringidas actualmente, use el cmdlet **Get-SPOTenantCdnPolicies** :

``` powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

Las propiedades que se devolverán son _IncludeFileExtensions_, _ExcludeRestrictedSiteClassifications_ y _ExcludeIfNoScriptDisabled_.

La propiedad _IncludeFileExtensions_ contiene la lista de extensiones de archivo que se servirán desde la red CDN.

> [!NOTE]
> Las extensiones de archivo predeterminadas son diferentes entre la pública y la privada.

La propiedad _ExcludeRestrictedSiteClassifications_ contiene las clasificaciones de sitio que desea excluir de la red CDN. Por ejemplo, puede excluir los sitios marcados como **confidenciales** para que el contenido de los sitios con esa clasificación aplicada no se atienda desde la red CDN.

La propiedad _ExcludeIfNoScriptDisabled_ excluye el contenido de la red CDN en función de la configuración del atributo _NoScript_ en el nivel de sitio. De forma predeterminada, el atributo _NoScript_ está establecido en **habilitado** para los sitios _modernos_ y **deshabilitado** para los sitios _clásicos_ . Esto depende de la configuración del espacio empresarial.

Para obtener más información acerca de estos cmdlets, consulte [set-SPOTenantCdnPolicy](https://technet.microsoft.com/library/mt800839.aspx) y [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/library/mt800838.aspx).

<a name="Office365CDNforSPOOrigin"> </a>
### <a name="add-an-origin-for-your-assets"></a>Adición de un origen a los activos

Use el cmdlet **Add-SPOTenantCdnOrigin** para definir un origen. Puede definir varios orígenes. El origen es una dirección URL que apunta a una biblioteca de SharePoint o la carpeta que contiene los activos que desea que se hospeden mediante la red CDN.
  
> [!IMPORTANT]
> Nunca debe poner recursos que contengan información de usuario o que se consideren confidenciales para su organización en un origen público.

``` powershell
Add-SPOTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path>
```

El valor de _path_ es la ruta de acceso relativa a la biblioteca o carpeta que contiene los activos. Puede usar caracteres comodín además de rutas relativas. Los orígenes admiten caracteres comodín que van precedidos de la dirección URL. Esto le permite crear orígenes que abarquen varios sitios. Por ejemplo, para incluir todos los activos de la carpeta MasterPages para todos los sitios como origen público en la red CDN, escriba el siguiente comando:

``` powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

+ El modificador de comodín**/** * solo se puede usar al principio de la ruta de acceso y coincidirá con todos los segmentos de dirección URL en la dirección URL especificada.
+ La ruta de acceso puede apuntar a una biblioteca de documentos, carpeta o sitio. Por ejemplo, la ruta de acceso _*/site1_ coincidirá con todas las bibliotecas de documentos del sitio.

Puede Agregar un origen con una ruta de acceso relativa específica. No se puede Agregar un origen mediante la ruta de acceso completa.

En este ejemplo se agrega un origen privado de la biblioteca siteassets en un sitio específico:

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

En este ejemplo se agrega un origen privado de la carpeta _Folder1_ en la biblioteca de activos del sitio de la colección de sitios:

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder1
```

Si hay un espacio en la ruta de acceso, puede poner la ruta entre comillas dobles o reemplazar el espacio con la codificación de la dirección URL %20. En los ejemplos siguientes se agrega un origen privado de la carpeta de la _carpeta 1_ en la biblioteca de activos del sitio de la colección de sitios:

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder%201
```

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl "sites/test/siteassets/folder 1"
```

Para obtener más información sobre este comando y su sintaxis, consulte [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/library/mt790772.aspx).

> [!NOTE]
> En orígenes privados, los activos que se compartan a partir de un origen deben tener una versión principal publicada antes de que se pueda tener acceso a ellos desde la red CDN.
  
Una vez que haya ejecutado el comando, el sistema sincroniza la configuración en el centro de recursos. Esto puede tardar hasta 15 minutos.

<a name="ExamplePublicOrigin"> </a>
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a>Ejemplo: configurar un origen público para las páginas maestras y para la biblioteca de estilos para SharePoint Online

Normalmente, estos orígenes se configuran de forma predeterminada al habilitar la red CDN de Office 365. Sin embargo, si desea habilitarlos manualmente, siga estos pasos.
  
+ Use el cmdlet **Add-SPOTenantCdnOrigin** para definir la biblioteca de estilos como un origen público.

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

+ Use el cmdlet **Add-SPOTenantCdnOrigin** para definir las páginas maestras como un origen público.

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

Para obtener más información sobre este comando y su sintaxis, consulte [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/library/mt790772.aspx).

Una vez que haya ejecutado el comando, el sistema sincroniza la configuración en el centro de recursos. Esto puede tardar hasta 15 minutos.

<a name="ExamplePrivateOrigin"> </a>
### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a>Ejemplo: configurar un origen privado para los activos del sitio, las páginas del sitio y las imágenes de publicación para SharePoint Online

+ Use el cmdlet **Add-SPOTenantCdnOrigin** para definir la carpeta activos del sitio como un origen privado.

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

+ Use el cmdlet **Add-SPOTenantCdnOrigin** para definir la carpeta páginas del sitio como un origen privado.

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

+ Use el cmdlet **Add-SPOTenantCdnOrigin** para definir la carpeta de publicación de imágenes como un origen privado.

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

Para obtener más información sobre este comando y su sintaxis, consulte [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/library/mt790772.aspx).

Una vez que haya ejecutado el comando, el sistema sincroniza la configuración en el centro de recursos. Esto puede tardar hasta 15 minutos.

<a name="ExamplePrivateOriginSiteCollection"> </a>
### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a>Ejemplo: configurar un origen privado para una colección de sitios de SharePoint Online

Use el cmdlet **Add-SPOTenantCdnOrigin** para definir una colección de sitios como un origen privado. Por ejemplo:

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

Para obtener más información sobre este comando y su sintaxis, consulte [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/library/mt790772.aspx).
  
Una vez que haya ejecutado el comando, el sistema sincroniza la configuración en el centro de recursos. Es posible que vea un mensaje de _configuración pendiente_ que se espera que el inquilino de SharePoint Online se conecte al servicio de la red CDN. Esto puede tardar hasta 15 minutos.

<a name="CDNManage"> </a>
### <a name="manage-the-office-365-cdn"></a>Administrar la red CDN de Office 365

Una vez que haya configurado la red CDN, puede realizar cambios en la configuración a medida que actualiza el contenido o según sus necesidades de cambio, tal y como se describe en esta sección.
  
<a name="Office365CDNforSPOaddremoveasset"> </a>
#### <a name="add-update-or-remove-assets-from-the-office-365-cdn"></a>Agregar, actualizar o quitar activos de la red CDN de Office 365

Una vez que haya completado los pasos de configuración, puede agregar nuevos activos y actualizar o quitar activos existentes cuando lo desee. Solo tiene que realizar los cambios en los activos de la carpeta o biblioteca de SharePoint que identificó como origen. Si agrega un nuevo activo, estará disponible inmediatamente a través de la red CDN. Sin embargo, si actualiza el activo, la nueva copia tardará hasta 15 minutos en propagarse y estar disponible en la red CDN.
  
Si necesita recuperar la ubicación del origen, puede usar el cmdlet **Get-SPOTenantCdnOrigins** . Para obtener información sobre cómo usar este cmdlet, consulte [Get-SPOTenantCdnOrigins](https://technet.microsoft.com/library/mt790770.aspx).

<a name="Office365CDNforSPORemoveOrigin"> </a>
#### <a name="remove-an-origin-from-the-office-365-cdn"></a>Quitar un origen de la red CDN de Office 365

Puede quitar el acceso a una carpeta o biblioteca de SharePoint que haya identificado como origen. Para ello, use el cmdlet **Remove-SPOTenantCdnOrigin** .

``` powershell
Remove-SPOTenantCdnOrigin -OriginUrl <path> -CdnType <Public | Private | Both>
```

Para obtener información sobre cómo usar este cmdlet, vea [Remove-SPOTenantCdnOrigin](https://technet.microsoft.com/library/mt790761.aspx).

<a name="Office365CDNforSPORemoveOrigin"> </a>
#### <a name="modify-an-origin-in-the-office-365-cdn"></a>Modificar un origen en la red CDN de Office 365

No puede modificar el origen que ha creado. En su lugar, quite el origen y, a continuación, agregue uno nuevo. Para obtener más información, vea [para quitar un origen de la red CDN de Office 365](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin) y [Agregar un origen a los activos](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin).

<a name="Office365CDNforSPODisable"> </a>
#### <a name="disable-the-office-365-cdn"></a>Deshabilitar la red CDN de Office 365

Use el cmdlet **set-SPOTenantCdnEnabled** para deshabilitar la red CDN de su organización. Si tiene los orígenes públicos y privados habilitados para la red CDN, debe ejecutar el cmdlet dos veces, como se muestra en los siguientes ejemplos.
  
Para deshabilitar el uso de orígenes públicos en la red CDN, escriba el siguiente comando:

``` powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $false
```

Para deshabilitar el uso de los orígenes privados en la red CDN, escriba el siguiente comando:

``` powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $false
```

Para obtener más información sobre este cmdlet, vea [set-SPOTenantCdnEnabled](https://technet.microsoft.com/library/mt790765.aspx).

</details>

<a name="CDNSetupinCLI"> </a>
## <a name="set-up-and-configure-the-office-365-cdn-using-the-office-365-cli"></a>Instalar y configurar la red CDN de Office 365 con la CLI de Office 365

Los procedimientos de esta sección requieren que tenga instalada la [CLI 365 de Office](https://aka.ms/o365cli). Después, conéctese al inquilino de SharePoint Online mediante el comando [spo connect](https://pnp.github.io/office365-cli/cmd/spo/connect/).

Siga estos pasos para configurar y configurar la red CDN para hospedar los activos en SharePoint Online mediante la CLI de Office 365.

<details>
  <summary>Haga clic para expandir</summary>

### <a name="enable-the-office-365-cdn"></a>Habilitar la red CDN de Office 365

Puede administrar el estado de la red CDN de Office 365 en su cuenta empresarial con el comando [spo cdn set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-set/).

Para habilitar la red CDN pública de Office 365 en su cuenta empresarial ejecute:

```sh
spo cdn set --type Public --enabled true
```

Para habilitar la red CDN de Office 365 SharePoint, ejecute:

```sh
spo cdn set --type Private --enabled true
```

#### <a name="view-the-current-status-of-the-office-365-cdn"></a>Vea el estado actual de la red CDN de Office 365.

Para comprobar si el tipo particular de la red CDN de Office 365 está habilitado o deshabilitado, use el comando [SPO CDN Get](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-get/) .

Para comprobar si la red CDN pública de Office 365 está habilitada, ejecute:

```sh
spo cdn get --type Public
```

### <a name="view-the-office-365-cdn-origins"></a>Ver los orígenes de la red CDN de Office 365

Para ver los orígenes configurados actualmente de la red CDN pública de Office 365, ejecute:

```sh
spo cdn origin list --type Public
```

Vea [orígenes de la red CDN predeterminados](use-office-365-cdn-with-spo.md#default-cdn-origins) para obtener información sobre los orígenes que se aprovisionan de forma predeterminada al habilitar la red CDN de Office 365.

### <a name="add-an-office-365-cdn-origin"></a>Agregar un origen de red CDN de Office 365

> [!IMPORTANT]
> Nunca debe poner recursos considerados confidenciales para su organización en una biblioteca de documentos de SharePoint configurada como un origen público.

Use el comando [spo cdn origin add](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-add/) definir un origen de la red CDN. Puede definir varios orígenes. El origen es una dirección URL que apunta a una biblioteca de SharePoint o la carpeta que contiene los activos que desea que se hospeden mediante la red CDN.

```sh
spo cdn origin add --type [Public | Private] --origin <path>
```

Donde `path` es la ruta de acceso relativa a la carpeta que contiene los activos. Puede usar caracteres comodín además de rutas relativas.

Para incluir todos los activos de la **Galería de páginas maestras** de todos los sitios como origen público, ejecute:

```sh
spo cdn origin add --type Public --origin */masterpage
```

Para configurar un origen privado para una colección de sitios específica, ejecute:

```sh
spo cdn origin add --type Private --origin sites/site1/siteassets
```

> [!NOTE]
> Después de agregar un origen de la red CDN, puede tardar hasta 15 minutos para poder recuperar archivos mediante el servicio de la red CDN. Puede comprobar si ya se ha habilitado el origen particular con el comando [spo cdn origin list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/).

### <a name="remove-an-office-365-cdn-origin"></a>Quitar un origen de la red CDN de Office 365

Use el comando [spo cdn origin remove](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-remove/) para eliminar un origen de la red CDN para el tipo de red CDN especificado.

Para quitar un origen público de la configuración de la red CDN, ejecute:

```sh
spo cdn origin remove --type Public --origin */masterpage
```

> [!NOTE]
> La eliminación de un origen de red CDN no afecta a los archivos almacenados en cualquier biblioteca de documentos que coincida con ese origen. Si se ha hecho referencia a estos activos mediante su dirección URL de SharePoint, SharePoint cambiará automáticamente de nuevo a la dirección URL original que apunta a la biblioteca de documentos. Sin embargo, si se ha hecho referencia a los activos mediante una dirección URL de red CDN pública, al quitar el origen se romperá el vínculo y tendrá que cambiarlo manualmente.

### <a name="modify-an-office-365-cdn-origin"></a>Modificación de un origen de red CDN de Office 365

No es posible modificar un origen de la red CDN existente. En su lugar, debe eliminar el origen de la red CDN definido anteriormente con el comando `spo cdn origin remove` y agregar uno nuevo con el comando `spo cdn origin add`.

### <a name="change-the-types-of-files-to-include-in-the-office-365-cdn"></a>Cambiar los tipos de archivos que se van a incluir en la red CDN de Office 365

De forma predeterminada, se incluyen los siguientes tipos de archivo en la red CDN: _.css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf y .woff_. Si tiene que incluir otros tipos de archivo en la red CDN, puede cambiar la configuración de la red CDN con el comando [spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/).

> [!NOTE]
> Al cambiar la lista de tipos de archivo, se sobrescribe la lista definida actualmente. Si desea incluir otros tipos de archivo, use el comando [spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) para averiguar qué tipos de archivos están configurados en este momento.

Para agregar el tipo de archivo _JSON_ a la lista predeterminada de tipos de archivo incluidos en la red CDN pública, ejecute:

```sh
spo cdn policy set --type Public --policy IncludeFileExtensions --value "CSS,EOT,GIF,ICO,JPEG,JPG,JS,MAP,PNG,SVG,TTF,WOFF,JSON"
```

### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn"></a>Cambiar la lista de clasificaciones de sitio que desea excluir de la red CDN de Office 365

Use el comando [spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) para excluir las clasificaciones de sitio que no desee que estén disponibles en la red CDN. De forma predeterminada, no se excluyen clasificaciones de sitio.

> [!NOTE]
> Al cambiar la lista de clasificaciones de sitio excluidas, se sobrescribe la lista definida actualmente. Si quiere excluir clasificaciones adicionales, use el comando [spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-list/) para averiguar qué clasificaciones están configuradas en este momento.

Para excluir los sitios clasificados como _HBI_ desde la red CDN pública, ejecute

```sh
spo cdn policy set --type Public --policy ExcludeRestrictedSiteClassifications --value "HBI"
```

### <a name="disable-the-office-365-cdn"></a>Deshabilitar la red CDN de Office 365

Para deshabilitar la red CDN de Office 365, use el comando `spo cdn set`, por ejemplo:

```sh
spo cdn set --type Public --enabled false
```

</details>

## <a name="using-your-cdn-assets"></a>Uso de los activos de la red CDN

Ahora que ha habilitado la red CDN y las directivas y los orígenes configurados, puede empezar a usar los activos de la red CDN.

Esta sección le ayudará a usar direcciones URL de la red CDN en el contenido y las páginas de SharePoint para que SharePoint redirija las solicitudes de activos en los orígenes públicos y privados a la red CDN.

+ [Actualización de vínculos a activos de la red CDN](use-office-365-cdn-with-spo.md#updating-links-to-cdn-assets)
+ [Usar activos en orígenes públicos](use-office-365-cdn-with-spo.md#using-assets-in-public-origins)
+ [Uso de activos en orígenes privados](use-office-365-cdn-with-spo.md#using-assets-in-private-origins)

Para obtener información sobre cómo usar la red CDN para hospedar elementos Web del lado cliente, vea el tema [hospedar un elemento Web del lado cliente de la red CDN de Office 365 (parte 4 de Hello World)](https://docs.microsoft.com/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn).

### <a name="updating-links-to-cdn-assets"></a>Actualización de vínculos a activos de la red CDN

Para usar activos que ha agregado a un origen, solo tiene que actualizar los vínculos al archivo original con la ruta de acceso al archivo en el origen.

+ Edite la página o el contenido que contiene vínculos a los activos que ha agregado a un origen. También puede usar uno de varios métodos para buscar y reemplazar vínculos globalmente en un sitio o una colección de sitios si desea actualizar el vínculo a un activo determinado en cualquier lugar en el que aparezca.
+ Para cada vínculo a un activo en un origen, reemplace la ruta de acceso por la ruta de acceso al archivo en el origen de la red CDN. Puede usar rutas relativas.
+ Guarde la página o el contenido.

Por ejemplo, considere la imagen _/site/SiteAssets/images/Image.png_, que ha copiado a la carpeta de la biblioteca de documentos _/site/CDN_origins/Public/_. Para usar el recurso de red CDN, reemplace la ruta de acceso original a la ubicación del archivo de imagen por la ruta de acceso al origen para que la nueva dirección URL _/site/CDN_origins/Public/Image.png_.

Si desea usar la dirección URL completa para el activo en lugar de una ruta de acceso relativa, construya el siguiente vínculo:

`https://<TenantHostName>.sharepoint.com/sites/site/CDN_origins/public/image.png`

> [!NOTE]
> En general, no se deben codificar las direcciones URL directamente en los activos en la red CDN. Sin embargo, si es necesario, puede construir manualmente direcciones URL para activos en los orígenes públicos. Para obtener más información, vea [direcciones URL de la red CDN de Hardcoding para activos públicos](use-office-365-cdn-with-spo.md#hardcoding-cdn-urls-for-public-assets).

Para obtener información sobre cómo comprobar que los activos se atienden desde la red CDN, vea [¿Cómo puedo confirmar que la red CDN atiende los activos?](use-office-365-cdn-with-spo.md#CDNConfirm) en la sección [solución de problemas de la red cdn de Office 365](use-office-365-cdn-with-spo.md#CDNTroubleshooting) .

### <a name="using-assets-in-public-origins"></a>Usar activos en orígenes públicos

La **característica de publicación** de SharePoint Online reescribe automáticamente direcciones URL de activos almacenados en orígenes públicos en sus equivalentes de CDN para que los activos se puedan atender desde el servicio de la red CDN en lugar de SharePoint.

Si su origen está en un sitio con la característica de publicación habilitada, y los activos que desea descargar en la red CDN están en una de las siguientes categorías, SharePoint rescribirá automáticamente las direcciones URL de los activos en el origen, siempre que el activo no se haya excluido por una CDN.  normativa.

A continuación, se muestra información general sobre los vínculos que la característica de publicación de SharePoint reescribe automáticamente:

+ URL de IMG/LINK/CSS en respuestas de HTML de página de publicación clásica
  + Esto incluye imágenes que han agregado autores en el contenido HTML de una página
+ URL de las imágenes del elemento web de presentación de la biblioteca de imágenes
+ Campos de imagen de los resultados de la API de REST SPList (RenderListDataAsStream)
  + Use la nueva propiedad _ImageFieldsToTryRewriteToCdnUrls_ para proporcionar una lista de campos separados por comas.
  + Admite campos de hipervínculos y campos de PublishingImage
+ Representaciones de imágenes de SharePoint

El siguiente diagrama ilustra el flujo de trabajo cuando SharePoint recibe una solicitud para una página que contiene activos de un origen público.

![Diagrama de flujo de trabajo: recuperar activos de la red CDN de Office 365 desde un origen público](media/O365-CDN/o365-cdn-public-steps-transparent.svg "Flujo de trabajo: recuperación de recursos de la red CDN de Office 365 desde un origen público")

> [!TIP]
> Si desea deshabilitar la reescritura automática de direcciones URL específicas en una página, puede desproteger la página y agregar el parámetro de la cadena de consulta. ** NoAutoReWrites = true** al final de cada vínculo que desee deshabilitar.

#### <a name="hardcoding-cdn-urls-for-public-assets"></a>Direcciones URL de CDN de Hardcoding para activos públicos

Si la característica de _publicación_ no está habilitada para un origen público o el activo no es uno de los tipos de vínculos que admite la característica de reescritura automática del servicio de red CDN, puede crear manualmente las direcciones URL en la ubicación de la red CDN de los activos y usar estas direcciones URL en el contenido.

> [!NOTE]
> No puede codificar direcciones URL de CDN con activos de un origen privado porque el token de acceso necesario que forma la última sección de la dirección URL se genera en el momento en que se solicita el recurso.

Para los activos de la red CDN pública, el formato de la dirección URL será similar al siguiente:

``` html
https://publiccdn.sharepointonline.com/<TenantHostName>/sites/site/library/asset.png
```

Reemplace **TenantHostName** por el nombre del espacio empresarial. Ejemplo:

``` html
https://publiccdn.sharepointonline.com/contoso.sharepoint.com/sites/site/library/asset.png
```

### <a name="using-assets-in-private-origins"></a>Uso de activos en orígenes privados

No se necesita ninguna configuración adicional para usar activos en orígenes privados. SharePoint Online reescribe automáticamente direcciones URL para activos en orígenes privados para que las solicitudes de dichos activos siempre se atiendan desde la red CDN. No puede crear manualmente direcciones URL a activos de CDN en orígenes privados porque estas direcciones contienen tokens que SharePoint Online debe generar automáticamente en el momento en que se solicita el activo.

El acceso a activos en orígenes privados está protegido por tokens generados dinámicamente en función de los permisos de usuario para el origen, con las advertencias descritas en las siguientes secciones. Los usuarios deben tener al menos acceso de **lectura** a los orígenes para que la red CDN represente contenido.

El siguiente diagrama ilustra el flujo de trabajo cuando SharePoint recibe una solicitud para una página que contiene activos de un origen privado.

![Diagrama de flujo de trabajo: recuperar activos de la red CDN de Office 365 de un origen privado](media/O365-CDN/o365-cdn-private-steps-transparent.svg "Flujo de trabajo: recuperar activos de la red CDN de Office 365 de un origen privado")

#### <a name="token-based-authorization-in-private-origins"></a>Autorización basada en token en orígenes privados

El acceso a los activos de orígenes privados en la red CDN de Office 365 se concede mediante tokens generados por SharePoint Online. Los usuarios que ya tienen permiso para obtener acceso a la carpeta o a la biblioteca designada por el origen reciben automáticamente tokens que permiten al usuario tener acceso al archivo en función de su nivel de permisos. Estos tokens de acceso son válidos durante 30 a 90 minutos después de que se generen para ayudar a evitar ataques de reproducción de tokens.

Una vez que se genera el token de acceso, SharePoint Online devuelve un URI personalizado al cliente que contiene dos parámetros de autorización _comer_ (token de autorización perimetral) y _OAT_ (token Authorization Authorization). La estructura de cada token es _< ' tiempo de expiración en formato de hora en tiempo de duración ' >__< >' firma segura ' _. Por ejemplo:

``` html
https://privatecdn.sharepointonline.com/contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg?eat=1486154359_cc59042c5c55c90b26a2775323c7c8112718431228fe84d568a3795a63912840&oat=1486154359_7d73c2e3ba4b7b1f97242332900616db0d4ffb04312
```

> [!NOTE]
> Cualquier persona que posea el token puede tener acceso al recurso en la red CDN. Sin embargo, las direcciones URL que contienen estos tokens de acceso solo se comparten a través de HTTPS, por lo que, a menos que un usuario final comparta explícitamente la dirección URL antes de que expire el token, el activo no será accesible para los usuarios no autorizados.

#### <a name="item-level-permissions-are-not-supported-for-assets-in-private-origins"></a>No se admiten permisos de nivel de elemento para activos en orígenes privados

Es importante tener en cuenta que SharePoint Online no admite permisos de nivel de elemento para activos en orígenes privados. Por ejemplo, para un archivo que se `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`encuentra en, los usuarios tienen acceso efectivo al archivo teniendo en cuenta las siguientes condiciones:

|Usuario  |Permisos  |Acceso efectivo  |
|---------|---------|---------|
|Usuario 1     |Tiene acceso a la carpeta1         |Puede tener acceso a image1. jpg desde la red CDN         |
|Usuario 2     |No tiene acceso a la carpeta1         |No se puede tener acceso a image1. jpg desde la red CDN         |
|Usuario 3     |No tiene acceso a la carpeta1, pero se le ha concedido el permiso explícito para obtener acceso a image1. jpg en SharePoint Online         |Puede tener acceso al elemento image1. jpg directamente desde SharePoint Online, pero no desde la red CDN.         |
|Usuario 4     |Tiene acceso a la carpeta1, pero se ha denegado explícitamente el acceso a image1. jpg en SharePoint Online         |No se puede obtener acceso al activo desde SharePoint Online, pero puede tener acceso al recurso desde la red CDN a pesar de que se le deniegue el acceso al archivo en SharePoint Online.         |

<a name="CDNTroubleshooting"> </a>
## <a name="troubleshooting-the-office-365-cdn"></a>Solución de problemas de la red CDN de Office 365

<a name="CDNConfirm"> </a>
### <a name="how-do-i-confirm-that-assets-are-being-served-by-the-cdn"></a>¿Cómo puedo confirmar que la red CDN atiende los activos?

Una vez que haya agregado los vínculos a los activos de la red CDN a una página, puede confirmar que el recurso se atiende desde la red CDN; para ello, haga clic en la imagen una vez representada y revisar la dirección URL de la imagen.

También puede usar las herramientas de desarrollo del explorador para ver la dirección URL de cada activo en una página o usar una herramienta de seguimiento de red de terceros.

> [!NOTE]
> Si usa una herramienta de red como Fiddler para probar los activos fuera de la representación del activo desde una página de SharePoint, debe agregar manualmente el encabezado de referencia "referrer: `https://yourdomain.sharepoint.com`" a la solicitud GET, donde la dirección URL es la dirección URL raíz del inquilino de SharePoint Online.

No se pueden probar direcciones URL de CDN directamente en un explorador web porque debe haber un sitio de referencia que provenga de SharePoint Online. Sin embargo, si agrega la dirección URL de los activos de la red CDN a una página de SharePoint y, a continuación, abre la página en un explorador, verá el activo de la red CDN representado en la página.

Para obtener más información sobre el uso de las herramientas de desarrollo en el explorador de Microsoft Edge, consulte [herramientas de desarrollo de Microsoft Edge](https://docs.microsoft.com/microsoft-edge/devtools-guide).

Para ver un vídeo corto hospedado en el [canal de YouTube de procedimientos y patrones para desarrolladores de SharePoint](https://aka.ms/sppnp-videos) que muestra cómo comprobar que su red CDN está funcionando, consulte [comprobar el uso de la red CDN y garantizar la conectividad de red óptima](https://www.youtube.com/watch?v=ClCtBAtGjE8&list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA&index=5).

### <a name="why-are-assets-from-a-new-origin-unavailable"></a>¿Por qué no están disponibles los activos de un nuevo origen?
Los activos en nuevos orígenes no estarán disponibles para su uso inmediatamente, ya que el registro se propagará a través de la red CDN y se cargarán los activos del origen al almacenamiento de la red CDN. El tiempo necesario para que los activos estén disponibles en la red CDN depende de cuántos activos y el tamaño de los archivos.

### <a name="my-client-side-web-part-or-sharepoint-framework-solution-isnt-working"></a>Mi elemento Web del lado cliente o solución de SharePoint Framework no funciona

Cuando se habilita la red CDN de Office 365 para orígenes públicos, el servicio de red CDN crea automáticamente estos orígenes predeterminados:

+ */MASTERPAGE
+ * BIBLIOTECA/STYLE
+ */CLIENTSIDEASSETS

Si falta el origen */clientsideassets, se producirá un error en las soluciones de SharePoint Framework y no se generará ningún mensaje de advertencia ni de error. Este origen puede faltar porque la red CDN se habilitó con el parámetro _-NoDefaultOrigins_ establecido en **$true**o porque el origen se eliminó manualmente.

Puede comprobar si el origen */CLIENTSIDEASSETS está presente con el siguiente comando de PowerShell:

``` powershell
Get-SPOTenantCdnOrigin -CdnType Public -OriginUrl */CLIENTSIDEASSETS
```

O bien, puede consultar con la CLI de Office 365:

``` powershell
spo cdn origin list
```

Para agregar el origen en PowerShell:

``` powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */CLIENTSIDEASSETS
```

Para agregar el origen en la CLI de Office 365:

``` powershell
spo cdn origin add --origin */CLIENTSIDEASSETS
```

### <a name="what-powershell-modules-and-cli-shells-do-i-need-to-work-with-the-office-365-cdn"></a>¿Qué módulos de PowerShell y shells de CLI necesito para trabajar con la red CDN de Office 365?

Puede elegir trabajar con la red CDN de Office 365 usando el módulo de PowerShell de **SharePoint Online Management Shell** o la **CLI de Office 365**.

+ [Introducción al shell de administración de SharePoint Online](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)
+ [Instalar Office 365 CLI](https://pnp.github.io/office365-cli/user-guide/installing-cli/)

## <a name="see-also"></a>Vea también

[Redes de entrega de contenido](https://aka.ms/o365cdns)

[Planeamiento de red y ajuste del rendimiento para Office 365](https://aka.ms/tune)

[Series de rendimiento de SharePoint: serie de vídeos de red CDN de Office 365](https://www.youtube.com/playlist?list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA)
