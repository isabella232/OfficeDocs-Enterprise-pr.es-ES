---
title: Inicio rápido de la red de entrega de contenido (CDN) de Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 06/04/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
description: Inicio rápido de la red de entrega de contenido (CDN) de Office 365
ms.openlocfilehash: 4abaaa5545bc807c4da297c66fd9ad1fb188adc7
ms.sourcegitcommit: 576c3dbdef535f952a861197dea5348908da9504
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "44561930"
---
# <a name="office-365-content-delivery-network-cdn-quickstart"></a>Inicio rápido de la red de entrega de contenido (CDN) de Office 365

Puede usar la red de entrega de **contenido (CDN) de Office 365** integrada para hospedar activos estáticos (imágenes, JavaScript, hojas de estilos, archivos WOFF) para proporcionar un mejor rendimiento en las páginas de SharePoint Online. La CDN de Office 365 mejora el rendimiento al almacenamiento en caché los archivos estáticos más cerca de los exploradores que los solicitan, lo que ayuda a acelerar descargas y reducir la latencia. Además, la red CDN de Office 365 usa el protocolo HTTP/2 para mejorar la compresión y la canalización HTTP. La red CDN de Office 365 se incluye como parte de la suscripción a SharePoint Online.

Para obtener una guía de información más detallada [, vea usar la red de entrega de contenido (CDN) de Office 365 con SharePoint Online](use-office-365-cdn-with-spo.md).

>[!NOTE]
>La red CDN de Office 365 solo está disponible para los inquilinos en la nube de producción (en todo el mundo). Actualmente, los inquilinos de las nubes del gobierno de Estados Unidos, China y Alemania no admiten la red CDN de Office 365.

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-identify-items-not-in-cdn"></a>Usar la herramienta diagnósticos de página para SharePoint para identificar elementos que no se encuentran en la red CDN

Puede usar la extensión **diagnóstico de página para el explorador de herramientas de SharePoint** para enumerar fácilmente activos en las páginas de SharePoint Online que se pueden agregar a un origen de la red CDN.

La **herramienta diagnósticos de página para SharePoint** es una extensión de explorador para los nuevos exploradores de Microsoft Edge ( https://www.microsoft.com/edge) y Chrome que analizan las páginas del portal moderno de SharePoint Online y del sitio de publicación clásico. La herramienta le ofrece un informe para cada página analizada en el que se muestra el rendimiento de la página respecto a un conjunto definido de criterios de rendimiento. Para instalar e informarse de la herramienta Diagnóstico de página de SharePoint, visite [Usar la herramienta Diagnóstico de página para SharePoint Online](https://aka.ms/perftool).

Cuando ejecuta la herramienta diagnósticos de página para SharePoint en una página de SharePoint Online, puede hacer clic en la pestaña **pruebas de diagnóstico** para ver una lista de los activos que no se hospedan en la red CDN. Estos activos se enumerarán en la comprobación de la **red de entrega de contenido (CDN)** , tal como se muestra en la captura de pantalla siguiente.

![Diagnósticos de página](media/page-diagnostics-for-spo/pagediag-results-general.PNG)

>[!NOTE]
>La herramienta de Diagnóstico de páginas solo funciona para SharePoint Online y no se puede usar en una página del sistema de SharePoint. 

## <a name="cdn-overview"></a>Información general de CDN

La red CDN de Office 365 está diseñada para optimizar el rendimiento de los usuarios mediante la distribución de objetos de acceso frecuente como imágenes y archivos JavaScript a través de una red global de alta velocidad, lo que reduce el tiempo de carga de la página y proporciona acceso a los objetos hospedados lo más cerca posible al usuario. La red CDN recopila los activos de una ubicación denominada _origen_. Un origen puede ser un sitio de SharePoint, una biblioteca de documentos o una carpeta a la que se pueda tener acceso mediante una dirección URL.

La red CDN de Office 365 se divide en dos tipos básicos:

- La **red CDN pública** está diseñada para usarse para JS (JavaScript), CSS (StyleSheets), archivo de fuentes web (Woff, WOFF2) y imágenes no registradas como logotipos de la compañía.
- La **red CDN privada** está diseñada para usarse para imágenes (PNG, JPG, JPEG, etc.).

Puede elegir entre los orígenes públicos o privados de su organización. La mayoría de las organizaciones optarán por implementar una combinación de ambos. Tanto las opciones públicas como las privadas proporcionan mejoras de rendimiento similares, pero cada una tiene atributos y ventajas únicos. Para obtener más información acerca de los orígenes de CDN públicos y privados, vea [elegir si cada origen debe ser público o privado](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate).

## <a name="how-to-enable-public-and-private-cdn-with-the-default-configuration"></a>Cómo habilitar la red CDN pública y privada con la configuración predeterminada
Antes de realizar cambios en la configuración de la red CDN del inquilino, debe comprobar que cumple con las directivas de cumplimiento, seguridad y privacidad de la organización.

Para obtener opciones de configuración más detalladas, o si ya ha habilitado la red CDN y desea agregar ubicaciones (orígenes) adicionales, consulte la sección [set up and configure The Office 365 CDN by Using the SharePoint Online Management Shell](use-office-365-cdn-with-spo.md#set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell) .

Conéctese a su inquilino mediante el shell de administración de SharePoint Online:

```PowerShell
Connect-SPOService -Url https://<YourTenantName>-admin.sharepoint.com
```

Para permitir que su organización use los orígenes públicos y privados con la configuración predeterminada, escriba el siguiente comando:

```PowerShell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

El resultado de estos cmdlets debería ser similar al siguiente:

![Resultado de set-SPOTenantCdnEnabled](media/O365-CDN/o365-cdn-enable-output.png)

## <a name="see-also"></a>Vea también

[Usar la herramienta de diagnóstico de página para SharePoint Online](https://aka.ms/perftool)

[Uso de la red de entrega de contenido (CDN) de Office 365 con SharePoint Online](use-office-365-cdn-with-spo.md)

[Redes de entrega de contenido](https://aka.ms/o365cdns)

[Planeamiento de red y ajuste del rendimiento para Office 365](https://aka.ms/tune)

[Series de rendimiento de SharePoint: serie de vídeos de red CDN de Office 365](https://www.youtube.com/playlist?list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA)
