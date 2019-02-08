---
title: Usar la red de entrega de contenido de Office 365 con SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: bebb285f-1d54-4f79-90a5-94985afc6af8
description: Se describe el uso integradas Content Delivery Network de Office 365 (CDN) para acelerar la entrega de los activos de SharePoint Online para todos los usuarios independientemente de dónde se encuentren o cómo tener acceso a su contenido.
ms.openlocfilehash: fd118e8df404961e1c35c6297a788397f810d1a2
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "29547118"
---
# <a name="use-the-office-365-content-delivery-network-with-sharepoint-online"></a>Usar la red de entrega de contenido de Office 365 con SharePoint Online

Puede hospedar estáticos activos en la red de entrega de contenido (CDN) de Office 365 para proporcionar un mejor rendimiento para las páginas de SharePoint Online. Activos estáticos son archivos que no cambian muy a menudo, como imágenes, vídeo y audio, hojas de estilos, fuentes y archivos de JavaScript. La CDN funciona como un proxy de almacenamiento en memoria caché distribuido geográficamente, al almacenar en caché estáticos activos más cerca de los exploradores que lo soliciten. 
  
Si ya está familiarizado con el modo en que las CDN funcionen, sólo necesita para llevar a cabo algunos pasos para configurarla. En este tema se describe cómo. Siga leyendo para obtener información acerca de la CDN de Office 365 y cómo empezar a usar los activos de estáticos de hospedaje.
  
 **Realizar una copia de Head a la [planeación de la red y ajuste del rendimiento de Office 365](https://aka.ms/tune).**
  
## <a name="office-365-cdn-basics"></a>Conceptos básicos de CDN de Office 365

La CDN de Office 365 se incluye como parte de su suscripción de SharePoint Online. No es necesario que pagar por él. Office 365 proporciona acceso público y soporte técnico para ambos privado y permite a los activos estática de host en varias ubicaciones u orígenes. La CDN de Office 365 no es la misma que la CDN de Azure. Si necesita obtener más información acerca de por qué usar una CDN o acerca de los conceptos generales de CDN, vea [redes de entrega de contenido](content-delivery-networks.md).
  
## <a name="how-the-cdn-grants-access-to-end-users"></a>Cómo la CDN concede acceso a los usuarios finales

Acceso privado a activos estáticos en la CDN de Office 365 se concede por tokens generados por SharePoint Online. Los usuarios que ya tienen permiso para obtener acceso a la carpeta o biblioteca designado por el origen se les otorgará automáticamente los tokens. SharePoint Online admite los permisos de nivel de elemento para la CDN.
  
Por ejemplo, para un archivo que se encuentra en `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`, dado lo siguiente:
  
- El usuario 1 tiene acceso a Carpeta1 y a image1.jpg
    
- El usuario 2 no tiene acceso a carpeta1
    
- 3 de usuario no tiene acceso a carpeta1 pero se concede permiso explícito para tener acceso a image1.jpg a través de SharePoint Online
    
- Usuario 4 tiene acceso a carpeta1, pero tiene denegado explícitamente el acceso a image1.jpg
    
A continuación, las siguientes condiciones es verdadera:
  
- El usuario 1 y 4 de usuario podrán tener acceso a image1.jpg a través de la red CDN.
    
- El usuario 2 y 3 de usuario no podrá tener acceso a image1.jpg a través de la red CDN.
    
    Sin embargo, 3 de usuario puede tener acceso a la image1.jpg activos directamente a través de SharePoint Online mientras 4 de usuario no se puede obtener acceso a los activos a través de SharePoint Online.
    
## <a name="overview-of-working-with-the-office-365-cdn"></a>Información general de trabajar con la CDN de Office 365

Para configurar la CDN de Office 365, siga estos pasos básicos:
  
- Planeación de la implementación de CDN:
    
  - Determinar qué activos estáticos que desea hospedar en la CDN de Office 365. Para obtener información detallada acerca de cómo realizar estas opciones, consulte [las redes de entrega de contenido](content-delivery-networks.md).
    
  - [Determine dónde desea almacenar los activos](use-office-365-cdn-with-spo.md#CDNStoreAssets). Esta ubicación es una carpeta o biblioteca de SharePoint y se llama a un origen.
    
  - Determinar si los activos deben hacerse públicos o mantener como privados. Hacerlo cuando se [Elija si cada origen debe ser público o privado](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate). Si lo desea, puede tener varios orígenes en la que algunas son públicas, y algunas son privados.
    
- [Establecer de seguridad y configurar la CDN de Office 365 mediante el Shell de administración de SharePoint Online](use-office-365-cdn-with-spo.md#CDNSetupinPShell). Cuando haya terminado este paso, debe:
    
  - Habilita la CDN para su organización.
    
  - Se agregó las orígenes. Identificar cada origen como público o privado.
    
Una vez haya terminado con el programa de instalación, [Administrar la CDN de Office 365](use-office-365-cdn-with-spo.md#CDNManage) a través del tiempo por: 
  
- Agregar, actualizar y eliminación de activos
    
- Agregar y quitar orígenes
    
- Configuración de directivas de CDN
    
- Si es necesario, deshabilitar la CDN de Office 365
    
## <a name="determine-where-you-want-to-store-your-assets"></a>Determine dónde desea almacenar los activos de

La CDN de captura los activos desde una ubicación que se denomina un origen. Para Office 365, un origen es una biblioteca de SharePoint o la carpeta que sea accesible para una dirección URL. Tener gran flexibilidad al especificar orígenes para su organización. Por ejemplo, puede especificar varios orígenes, o bien, un único origen donde desea colocar todos los activos de CDN. Puede elegir tener orígenes públicos o privados para su organización. La mayoría de las organizaciones se optan por implementar una combinación de ambas.
  
Si define cientos de orígenes, probablemente tendrá un impacto negativo en el tiempo que se tarda en procesar las solicitudes. Se recomienda que si tiene más de aproximadamente 100 orígenes es posible que desee reconsiderar la arquitectura.
  
## <a name="choose-whether-each-origin-should-be-public-or-private"></a>Elija si cada origen debe ser público o privado

Al identificar un origen, se especifica si se debe establecer público o privado. Independientemente de la opción que elija, Microsoft hace todo el trabajo pesado por usted lo que respecta a la administración de la CDN de sí mismo. Además, puede cambiar de opinión más adelante, después de configurar la CDN e identificado los orígenes.
  
Opciones públicas y privadas proporcionan mejoras de rendimiento, pero cada uno tiene ventajas y atributos únicos.
  
 **Los atributos y las ventajas de los activos en un origen público de hospedaje**
  
- Forma anónima son accesibles para todos los activos expuestos en un origen público.
    
    > [!IMPORTANT]
    > Si se identifica un origen público en su CDN, nunca debe colocar los recursos que se consideran confidenciales de su organización en un origen público o biblioteca de SharePoint Online. 
  
- Si quita un activo de un origen público, puede continuar el activo esté disponible para un máximo de 30 días desde la memoria caché; Sin embargo, se invalidará vínculos a los activos en la CDN dentro de 15 minutos.
    
- Al hospedar hojas de estilos (archivos CSS) en un origen pública, puede usar rutas de acceso relativas y URI dentro del código. Esto significa que puede hacer referencia a la ubicación de las imágenes de fondo y otros objetos con relación a la ubicación de los activos que se está llamando a.
    
- Mientras que puede codificar dirección URL de un origen pública, si lo hace por lo que no se recomienda. El motivo es que si el acceso a la red CDN deja de estar disponible, la dirección URL no se puede resolver automáticamente a la organización en SharePoint Online y que podría provocar la ruptura de vínculos y otros errores.
    
- Los tipos de archivo predeterminados que se incluyen para orígenes públicas son .css, .eot, .gif, .ico, .jpeg, .jpg, .js, Map, .png, .svg, .ttf y .woff. Puede especificar los tipos de archivo adicionales.
    
- Si lo desea, puede configurar una directiva para excluir los activos que se han identificado por clasificaciones de sitio que especifique. Por ejemplo, puede elegir excluir todos los activos que están marcados como "restringido" o "confidential" incluso si son un tipo de archivo permitido y se encuentran en un origen público.
    
 **Los atributos y las ventajas de los activos en un origen privado de hospedaje**
  
- Los usuarios solo pueden obtener acceso los activos desde un origen privado si están autorizados para hacerlo. No se les permita el acceso anónimo a estos activos.
    
- Si quita un activo desde el origen privado, puede continuar el activo esté disponible para hasta una hora de la memoria caché; Sin embargo, se invalidará vínculos a los activos en la CDN dentro de 15 minutos.
    
- Los tipos de archivo predeterminados que se incluyen para orígenes privadas son .gif, .ico, .jpeg, .jpg, .js y .png. Puede especificar los tipos de archivo adicionales.
    
- Al igual que orígenes públicas, puede configurar una directiva para excluir los activos que se han identificado por las clasificaciones de sitio que especifique incluso si usar caracteres comodín para incluir todos los activos dentro de una carpeta o una biblioteca de sitios.
    
## <a name="default-office-365-cdn-origins"></a>Orígenes de Office 365 CDN predeterminada

A menos que se especifique lo contrario, Office 365 configura algunos orígenes predeterminada para usted cuando se habilita la CDN de Office 365. Si excluir inicialmente, puede agregar estos orígenes después de completar el programa de instalación.
  
De forma predeterminada privados orígenes:
  
- \*/userphoto.aspx
    
- \*/siteassets
    
De forma predeterminada públicas orígenes:
  
- \*/MasterPage
    
- \*biblioteca de Sheets

> [!NOTE]
> Clientsideassets es un origen pública predeterminada que se ha agregado en Dic de 2017 que, si tenía una CDN pública antes de ese momento, no verá la entrada agrega automáticamente, pero si ha creado más adelante, verá este cambio automáticamente. Si desea leer un ejemplo del uso de este origen CDN, vea: [Host el elemento web de cliente de Office 365 CDN (parte 4 de Hello World)](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)
    
## <a name="set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell"></a>Instalar y configurar la CDN de Office 365 mediante el uso de la consola de administración de SharePoint Online

Los procedimientos de este tema requieren que se va a usar el Shell de administración de SharePoint Online para conectarse a SharePoint Online. Para obtener instrucciones, vea [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).
  
Complete estos pasos para instalar y configurar la CDN de Office 365 para hospedar los activos de estáticos en SharePoint Online.
  
### <a name="to-enable-your-organization-to-use-the-office-365-cdn"></a>Para habilitar la organización usar la CDN de Office 365

Use el cmdlet **Set-SPOTenantCdnEnabled** para habilitar la organización usar la CDN de Office 365. Puede habilitar a usar orígenes públicas, orígenes privadas o ambos, con la CDN de su organización. También puede configurar la CDN de Office 365 para omitir la configuración de orígenes de forma predeterminada cuando se habilita. Siempre puede agregar estos orígenes más adelante, tal como se describe en este tema. 
  
En Windows Powershell para SharePoint Online:
  
```
Set-SPOTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

Por ejemplo, para habilitar a usar orígenes públicos y privados con la CDN de su organización, escriba el siguiente comando:
  
```
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

Para habilitar la organización usar orígenes públicos y privados con la CDN pero omitir la configuración de los orígenes de forma predeterminada, escriba el siguiente comando:
  
```
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

Para habilitar a usar orígenes públicas con la CDN de su organización, escriba el siguiente comando:
  
```
Set-SPOTenantCdnEnabled -CdnType Public -Enable $true
```

Para habilitar a usar orígenes privadas con la CDN de su organización, escriba el siguiente comando:
  
```
Set-SPOTenantCdnEnabled -CdnType Private -Enable $true
```

Para obtener más información acerca de este cmdlet, vea [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).
  
### <a name="optional-to-change-the-list-of-file-types-to-include-in-the-office-365-cdn"></a>(Opcional) Para cambiar la lista de tipos de archivo que deben incluirse en la CDN de Office 365
<a name="Office365CDNforSPOFileType"> </a>

> [!TIP]
> Al definir tipos de archivo mediante el cmdlet **Set-SPOTenantCdnPolicy** , sobrescribir la lista definida actualmente. Si desea agregar otros tipos de archivo a la lista, use el cmdlet en primer lugar para averiguar qué tipos de archivo que ya están permitidos e incluyen en la lista junto con las nuevas. 
  
Use el cmdlet **Set-SPOTenantCdnPolicy** para definir tipos de archivos estáticos que se pueden hospedar orígenes públicos y privados en la CDN. De forma predeterminada, se permiten tipos comunes de activos para .js, .gif, .jpg y .css de ejemplo. 
  
En Windows PowerShell para SharePoint Online:
  
```
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

Para ver qué tipos de archivo se permiten actualmente por la CDN, use el cmdlet **Get-SPOTenantCdnPolicies** : 
  
```
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

Para obtener más información acerca de estos cmdlets, consulte [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) y [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).
  
### <a name="optional-to-change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn"></a>(Opcional) Para cambiar la lista de clasificaciones de sitio que desea excluir desde la CDN de Office 365
<a name="Office365CDNforSPOSiteClassification"> </a>

> [!TIP]
> Cuando se excluyen las clasificaciones de sitio mediante el cmdlet **Set-SPOTenantCdnPolicy** , sobrescribir la lista definida actualmente. Si desea excluir las clasificaciones de sitios adicionales, use el cmdlet en primer lugar para averiguar qué clasificaciones están ya excluidas y agregarlos a continuación, junto con las nuevas. 
  
Use el cmdlet **Set-SPOTenantCdnPolicy** para excluir las clasificaciones de sitio que no desea que esté disponible a través de la red CDN. De forma predeterminada, no se excluyen ningún clasificaciones de sitio. 
  
En Windows PowerShell para SharePoint Online:
  
```
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications >"
```

Para ver qué clasificaciones de sitio están actualmente restringidas, use el cmdlet **Get-SPOTenantCdnPolicies** : 
  
```
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

Para obtener más información acerca de estos cmdlets, consulte [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) y [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).
  
### <a name="to-add-an-origin-for-your-assets"></a>Para agregar un origen de los activos
<a name="Office365CDNforSPOOrigin"> </a>

Use el cmdlet **Add-SPOTenantCdnOrigin** para definir un origen. Puede definir varios orígenes. El origen es una dirección URL que apunta a una biblioteca de SharePoint o la carpeta que contiene los activos que desea que se hospeda la CDN. 
  
> [!IMPORTANT]
> Si se identifica un origen público en su CDN, nunca debe colocar los recursos que se consideran confidenciales de su organización en el origen público o la biblioteca de SharePoint Online. 
  
```
Add-SPOTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path >
```

Donde ruta de acceso es la ruta de acceso a la carpeta que contiene los activos. Puede usar caracteres comodín además de rutas de acceso relativas. Por ejemplo, para incluir todos los activos en la carpeta masterpages para todos los sitios como un origen público dentro de la red CDN, escriba el siguiente comando:
  
```
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

Para obtener más información acerca de este comando y su sintaxis, consulte [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).
  
Una vez que haya ejecutado el comando, el sistema sincroniza la configuración en el centro de datos. Esto tarda 15 minutos.
  
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a>Ejemplo: Configurar un origen público para las páginas maestras y para la biblioteca de estilos de SharePoint Online
<a name="ExamplePublicOrigin"> </a>

Normalmente, estos orígenes se configuran para de forma predeterminada cuando se habilitan orígenes públicas para la CDN de Office 365. Sin embargo, si desea habilitarlos manualmente, siga estos pasos.
  
- Use el cmdlet **Add-SPOTenantCdnOrigin** para definir la biblioteca de estilos como un origen público dentro de la CDN de Office 365. 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

- Use el cmdlet **Add-SPOTenantCdnOrigin** para definir las páginas maestras como un origen público dentro de la CDN de Office 365. 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

- Para obtener más información acerca de este comando y su sintaxis, consulte [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).
    
    Una vez que haya ejecutado el comando, el sistema sincroniza la configuración en el centro de datos. Esto tarda 15 minutos.
    
### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a>Ejemplo: Configurar un origen privado para los activos del sitio, las páginas del sitio e imágenes de publicación de SharePoint Online
<a name="ExamplePrivateOrigin"> </a>

- Use el cmdlet **Add-SPOTenantCdnOrigin** para definir la carpeta de activos de sitios como un origen privado dentro de la CDN de Office 365. 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

- Use el cmdlet **Add-SPOTenantCdnOrigin** para definir la carpeta de páginas de sitio como un origen privado dentro de la CDN de Office 365. 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

- Use el cmdlet **Add-SPOTenantCdnOrigin** para definir la carpeta de imágenes de publicación como un origen privado dentro de la CDN de Office 365. 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

    Para obtener más información acerca de este comando y su sintaxis, consulte [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).
    
    Una vez que haya ejecutado el comando, el sistema sincroniza la configuración en el centro de datos. Esto tarda 15 minutos.
    
### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a>Ejemplo: Configurar un origen privado para una colección de sitios de SharePoint Online
<a name="ExamplePrivateOriginSiteCollection"> </a>

Use el cmdlet **Add-SPOTenantCdnOrigin** para definir una colección de sitios como un origen privado dentro de la CDN de Office 365. Por ejemplo, 
  
```
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

Para obtener más información acerca de este comando y su sintaxis, consulte [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).
  
Una vez que haya ejecutado el comando, el sistema sincroniza la configuración en el centro de datos. Esto tarda 15 minutos.
  
## <a name="manage-the-office-365-cdn"></a>Administrar Office 365 CDN
<a name="CDNManage"> </a>

Una vez haya configurado la CDN, puede realizar los cambios en la configuración como actualizar contenido o a medida que cambian las necesidades, tal como se describe en esta sección.
  
### <a name="to-add-update-or-remove-assets-from-the-office-365-cdn"></a>Para agregar, actualizar o quitar activos desde la CDN de Office 365
<a name="Office365CDNforSPOaddremoveasset"> </a>

Una vez que haya completado los pasos del programa de instalación, puede agregar nuevos activos y actualizar o quitar activos existentes siempre que lo desee. Simplemente, realice los cambios en los activos de la carpeta o biblioteca de SharePoint que ha identificado como un origen. Si agrega un nuevo activo, está disponible a través de la red CDN inmediatamente. Sin embargo, si actualiza los activos, se tardará hasta 15 minutos para la nueva copia propagar y dejarán de estar disponibles en la red CDN.
  
Si necesita recuperar la ubicación del origen, puede usar el cmdlet **Get-SPOTenantCdnOrigins** . Para obtener información acerca de cómo usar este cmdlet, vea [Get-SPOTenantCdnOrigins](https://technet.microsoft.com/en-us/library/mt790770.aspx).
  
### <a name="to-remove-an-origin-from-the-office-365-cdn"></a>Para quitar un origen desde la CDN de Office 365
<a name="Office365CDNforSPORemoveOrigin"> </a>

Si necesita, puede quitar el acceso a una carpeta o biblioteca de SharePoint que ha identificado como un origen. Para ello, use el cmdlet **Remove-SPOTenantCdnOrigin** . Para obtener información acerca de cómo usar este cmdlet, vea [Remove-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790761.aspx).
  
### <a name="to-modify-an-origin-in-the-office-365-cdn"></a>Para modificar un origen en la CDN de Office 365
<a name="Office365CDNforSPORemoveOrigin"> </a>

No se puede modificar un origen que se ha creado. En su lugar, quite el origen y, a continuación, agregar una nueva. Para obtener más información, vea [para quitar un origen desde la CDN de Office 365](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin) y [para agregar un origen para los activos](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin).
  
### <a name="to-disable-the-office-365-cdn"></a>Para deshabilitar la CDN de Office 365
<a name="Office365CDNforSPODisable"> </a>

Use el cmdlet **Set-SPOTenantCdnEnabled** para deshabilitar la CDN para su organización. Si dispone de los orígenes públicos y privados habilitados para la CDN, debe ejecutar el cmdlet dos veces como se muestra en los ejemplos siguientes. 
  
Para deshabilitar el uso de orígenes públicas en la CDN de Windows Powershell para SharePoint Online, escriba el siguiente comando:
  
```
Set-SPOTenantCdnEnabled -CdnType Public -Enable $false
```

Para deshabilitar el uso de los orígenes de privada en la red CDN, escriba el siguiente comando:
  
```
Set-SPOTenantCdnEnabled -CdnType Private -Enable $false
```

Para obtener más información acerca de este cmdlet, vea [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).
  
## <a name="troubleshooting-your-office-365-cdn-configuration"></a>Solución de problemas de la configuración de Office 365 CDN
<a name="CDNManage"> </a>

El extremo no inmediatamente estará disponible para su uso, como sea necesario hora para el registro en propagarse a través de la red CDN. Configuración tarda 15 minutos.
  

