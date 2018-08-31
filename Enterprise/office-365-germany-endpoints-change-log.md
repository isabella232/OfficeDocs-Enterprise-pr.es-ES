---
title: Registro de cambios de los extremos de Alemania de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 8/13/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
search.appverid: MOE150
ms.assetid: 980041c9-7984-44b2-95f0-af66743543a1
ms.openlocfilehash: e77d6fc3b8136f39ed75ef21b0ff417a4ad6465a
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542938"
---
# <a name="office-365-germany-endpoints-change-log"></a>Registro de cambios de los extremos de Alemania de Office 365

*Se aplica a: Administración de Office 365*

## <a name="list-of-changes-to-the-endpoints-required-for-office-365-germany"></a>Lista de los cambios realizados en los extremos necesarios para Office 365 Alemania

En la siguiente tabla se enumera los cambios realizados en [los extremos de Office 365 Alemania](office-365-germany-endpoints.md).
  
|**Fecha**|**Cambio**|
|:-----|:-----|
|24/1/2017  <br/> |Publicación inicial de artículo.  <br/> |
|28/2/2017  <br/> |Adición de nombres de dominio 3 completos; 1 / [eficaz 4/1/2017. Obligatorio: Portal de Office 365 y compartidos. ExpressRoute: no. www.Office.de], 2 / [eficaz 4/1/2017. Obligatorio: Portal de Office 365 y compartidos. ExpressRoute: no. Office.de], 3 / [eficaz 4/1/2017. Obligatorio: Portal de Office 365 y compartidos. ExpressRoute: no. officehome.msocdn.de]. notas: adición de adicionales Portal FQDN. adición de 2 IP_Sets; 1 / [eficaz 4/1/2017. Obligatorio: Portal de Office 365 y compartidos. ExpressRoute: Nº 51.5.245.67/32], 2 / [eficaz 4/1/2017. Obligatorio: Portal de Office 365 y compartidos. ExpressRoute: Nº 51.4.227.178/32]. Notas: Adición de extremos de Portal adicionales. Adición de 2 IP_Sets; 1 / [eficaz 4/1/2017. Obligatorio: Portal de Office 365 y compartidos. ExpressRoute: Nº 2a01:4180:2001::92], 2 / [eficaz 4/1/2017. Obligatorio: Portal de Office 365 y compartidos. ExpressRoute: Nº 2a01:4180:2401::11f]. Notas: Adición de extremos de Portal adicionales.  <br/> |
|8/3/2017  <br/> |Adición de nombres de dominio completos 1; 1 / [eficaz 3/8/2017. Obligatorio: OneDrive para la empresa. ExpressRoute: no. spoprod-a.akamaihd.net]. Notas: Adición de extremos CDN adicionales.  <br/> |
|31/3/2017  <br/> |Adición de nombres de dominio 3 completos; 1 / [eficaz 5/1/2017. Obligatorio: Online híbrido de SharePoint. \*. search.production.de.azuretrafficmanager.de], 2 / [eficaz 5/1/2017. Obligatorio: Online híbrido de SharePoint. Login.microsoftonline.de], 3 / [eficaz 5/1/2017. Obligatorio: Online híbrido de SharePoint. provisioningapi.microsoftonline.de]. notas: híbrido de Sharepoint de adición de nombres de dominio completos.  <br/> |
|1/6/2017  <br/> |Adición de nombres de dominio 2 completos eficaz 1/7/2017  <br/> shellprod.msocdn.de  <br/> R1.res.office365.com  <br/> |
|26/6/2017  <br/> |Reemplaza la detección automática\*. outlook.de con Autodiscover.outlook.de y outlook.office.de de detección automática.  <br/> |
|29/9/2017  <br/> |Adición de nombres de dominio 3 completos; 1 / [eficaz 11/1/2017.  <br/> cegsignup.Microsoft.de  <br/> negsignup.Microsoft.de  <br/> \*. svc.ms  <br/> |
|16/1/2018  <br/> |Adición de nombres de dominio completos 1; 1 / [eficaz 2/1/2018. Obligatorio: Portal de Office 365. ExpressRoute: no. webshell.Suite.Office.de]. notas: adición de FQDN adicional de consola del conjunto de aplicaciones de Office 365. Adición de 4 IP_Sets; 1 / [eficaz 2/1/2018. Obligatorio: Portal de Office 365. ExpressRoute: Nº 51.5.242.163/32], 2 / [eficaz 2/1/2018. Obligatorio: Portal de Office 365. ExpressRoute: Nº 51.4.226.115/32], 3 / [eficaz 2/1/2018. Obligatorio: Portal de Office 365. ExpressRoute: Nº 2a01:4180:2401::33b / 4 / [eficaz 2/1/2018. Obligatorio: Portal de Office 365. ExpressRoute: Nº 2a01:4180:2001::234 / notas: adición de direcciones IP adicionales para shell de conjunto de aplicaciones de Office 365.  <br/> |
|5/2/2018  <br/> |Agregar 1 FQDN; 1 / [eficaz 3/1/2018. Obligatorio: Portal y compartidos. ExpressRoute: Sí. webshell.Suite.Office.de]. notas: agregar una dirección URL para el Portal y adición de 2 IP_Sets; compartidos y los FQDN. 1 / [eficaz 3/1/2018. Obligatorio: Portal y compartidos. ExpressRoute: Sí. 51.5.242.163/32]., 2 / [eficaz 3/1/2018. Obligatorio: Portal y compartidos. ExpressRoute: Sí. 51.4.226.115/32]. Notas: Agregar un nuevo prefijos de Portal y compartidos. Adición de 2 IP_Sets; 1 / [eficaz 3/1/2018. Obligatorio: Portal y compartidos. ExpressRoute: Sí. 2a01:4180:2401::33b / 128]., 2 / [eficaz 3/1/2018. Obligatorio: Portal y compartidos. ExpressRoute: Sí. 2a01:4180:2001::234 / 128]. Notas: Agregar un nuevo prefijos de Portal y compartidos. Adición de 1 IP_Sets; 1 / [eficaz 3/1/2018. Obligatorio: Office Online. ExpressRoute: Sí. 51.18.16.0/23]. Notas: Adición de un nuevo prefijo para Office Online.  <br/> |
|15/3/2018  <br/> |Adición de 1 IP_Set; 1 / [eficaz 4/15/2018. Obligatorio: Office 365 ProPlus. ExpressRoute: Nº 51.18.0.0/21]. Notas: Adición de un extremo de Office 365 ProPlus.  <br/> |
|2/7/2018  <br/> |Eliminación de 1 FQDN; 1 / [eficaz 8/1/2018. Obligatorio: OneDrive para la empresa. ExpressRoute: no. Login.microsoftonline.de]. notas: eliminación de OneDrive para el extremo de negocio. Eliminación de 11 FQDN; 1 / [eficaz 8/1/2018. Obligatorio: Office Mobile. ExpressRoute: Nº https://excelps.osi.office.de/exlps/excelprint.svc/exlPrint], 2 / [eficaz 8/1/2018. Obligatorio: Office Mobile. ExpressRoute: Nº https://wordps.osi.office.de/wrdps/wordprint.svc/wrdprint], 3 / [eficaz 8/1/2018. Obligatorio: Office Mobile. ExpressRoute: Nº https://wordcs.osi.office.de/wordauto/wordautomation.svc/wordautomation], 4 / [eficaz 8/1/2018. Obligatorio: Office Mobile. ExpressRoute: Nº https://wordcs.osi.office.de/wordauto/wordautomation.svc/rest], 5 / [eficaz 8/1/2018. Obligatorio: Office Mobile. ExpressRoute: Nº https://pptps.osi.office.de/pptps/powerpointprint.svc/PptPrint], 6 / [eficaz 8/1/2018. Obligatorio: Office Mobile. ExpressRoute: Nº https://pptcs.osi.office.de/pptauto/PowerpointAutomation.svc/PptAutomation], 7 / [eficaz 8/1/2018. Obligatorio: Office Mobile. ExpressRoute: Nº https://pptcs.osi.office.de/pptauto/PowerpointAutomation.svc/rest], 8 / [eficaz 8/1/2018. Obligatorio: Office Mobile. ExpressRoute: Nº https://ols.osi.office.de/], 9 / [eficaz 8/1/2018. Obligatorio: Office Mobile. ExpressRoute: Nº https://ols.osi.office.de/olsc/OlsClient.svc/OlsClient], 10 / [eficaz 8/1/2018. Obligatorio: Office Mobile. ExpressRoute: Nº https://excelcs.osi.office.de/xlauto/excelautomation.svc/XlAutomation], 11 / [eficaz 8/1/2018. Obligatorio: Office Mobile. ExpressRoute: Nº https://excelcs.osi.office.de/xlauto/excelautomation.svc/rest]. Notas: Eliminación de extremos de Office Mobile.  <br/> |
   

