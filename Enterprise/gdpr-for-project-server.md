---
title: RGPD para Project Server
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: Obtenga información sobre cómo cumplir los requisitos de RGPD en Project Server local.
ms.openlocfilehash: 6a630dc4cef2c4117e0ba25497f898d0b8da221b
ms.sourcegitcommit: aabd369fc8b397f9e738374d42d8afd18b96d469
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="gdpr-for-project-server"></a>RGPD para Project Server

Project Server usa scripts personalizados para exportar y redactar datos de usuario en Project Web App. El proceso básico es:

1.  Busque los sitios de Project Web App en la granja de servidores.

2.  Busque los proyectos en cada sitio que contiene el usuario.

3.  Exporte y revise los tipos de datos que desee revisar.

4.  Redacte los datos según sea necesario.

Estos pasos se tratan con detalle en los siguientes artículos:

- [Exportar datos de usuario de Project Server](/Project/export-user-data-from-project-server?toc=/Office365/Enterprise/toc.json)

- [Eliminar datos de usuario de Project Server](/Project/delete-user-data-from-project-server?toc=/Office365/Enterprise/toc.json)


Tenga en cuenta que Project Server está basado en SharePoint Server y registra eventos en los registros ULS de SharePoint y en la base de datos de uso.
