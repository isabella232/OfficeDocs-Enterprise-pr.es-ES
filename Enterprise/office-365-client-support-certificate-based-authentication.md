---
title: 'Compatibilidad con aplicaciones cliente de Office 365: autenticación basada en certificados'
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: Office 365 Administration
localization_priority: Normal
ms.collection:
- Strat_O365_Enterprise
- M365-subscription-management
search.appverid:
- MET150
description: Office 365 Client App Support for Certificate-Based Authentication.
ms.openlocfilehash: 88bc59934399588f0a5c682c6b136ad0948ecd52
ms.sourcegitcommit: 9c6e31204aa326c31d60befe80e610f702e65800
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/14/2019
ms.locfileid: "33990937"
---
# <a name="office-365-client-app-support--certificate-based-authentication"></a>Compatibilidad con aplicaciones cliente de Office 365: autenticación basada en certificados

La autenticación basada en certificados permite autenticar a Azure Active Directory con un certificado de cliente en dispositivos Windows, Android o iOS. La configuración de esta característica elimina la necesidad de escribir una combinación de nombre de usuario y contraseña en determinadas aplicaciones de correo y Microsoft Office en el dispositivo móvil.

Obtenga más información acerca de [la autenticación basada en certificados](https://docs.microsoft.com/azure/active-directory/authentication/active-directory-certificate-based-authentication-get-started).

## <a name="supported-platforms"></a>Plataformas compatibles

 - Escritorio de Windows 10<sup>2</sup>
 - Aplicaciones modernas de Windows 10
 - Exploradores Web
 - Android
 - iOS
 - macOS<sup>1</sup> <sup>2</sup>

Para obtener más información acerca de la compatibilidad de plataformas en Office 365, vea [System Requirements for office 365](https://products.office.com/office-system-requirements).

## <a name="supported-clients"></a>Clientes compatibles

Las versiones más recientes de los siguientes clientes admiten la autenticación basada en certificados:

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Icono de acceso](media/o365-access-64x64.png) <br> [Acceso](https://products.office.com/access) | ![Icono de Azure](media/o365-azure-64x64.png) <br> [Portal de <br> Azure ad](https://azure.microsoft.com/features/azure-portal/) | ![Icono del portal de empresa](media/o365-microsoft-64x64.png) <br> [Portal <br> de empresa](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal) | ![Icono de Delve](media/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) | ![Icono de Dynamics 365](media/o365-dynamics365-64x64.png) <br> [Dynamics 365](https://dynamics.microsoft.com) 
| ![Icono de borde](media/o365-edge-64x64.png) <br> [Vanguardia](https://www.microsoft.com/windows/microsoft-edge) | ![Icono de Excel](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) | ![Icono de flujo](media/o365-flow-64x64.png) <br> [Flow](https://flow.microsoft.com) | ![Icono formularios](media/o365-forms-64x64.png) <br> [Forms](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) | ![Icono de Kaizala](media/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) 
| ![Icono de Office 365 administrador](media/o365-o365admin-64x64.png) <br> [Office 365 <br> administrador](https://products.office.com/business/manage-office-365-admin-app) | ![Icono de lente](media/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | ![Icono de OneDrive para la empresa](media/o365-OneDrive-64x64.png) <br> [OneDrive<sup>1</sup>](https://products.office.com/onedrive-for-business/online-cloud-storage) |  ![Icono de OneNote](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Icono de Outlook](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) 
| ![Icono de Planner](media/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) | ![Icono de PowerApps](media/o365-powerapps-64x64.png) <br> [PowerApps](https://powerapps.microsoft.com) | ![Icono de PowerBI](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com)| ![Icono de PowerPoint](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![Icono de proyecto](media/o365-project-64x64.png) <br> [Project](https://products.office.com/project) 
| ![Icono de Publisher](media/o365-publisher-64x64.png) <br> [Publisher](https://products.office.com/publisher) | ![Icono de SharePoint](media/o365-sharepoint-64x64.png) <br> [SharePoint](https://products.office.com/sharepoint) | ![Icono de Skype empresarial](media/o365-skypeforbusiness-64x64.png) <br> [Skype <br> empresarial](https://www.skype.com/business/) | ![Icono de notas adhesivas](media/o365-stickynotes-64x64.png) <br> [Notas rápidas](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw) | ![Icono de secuencia](media/o365-stream-64x64.png) <br> [Stream](https://stream.microsoft.com) 
| ![Icono de Sway](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) | ![Icono de Teams](media/o365-teams-64x64.png) <br> [Teams](https://products.office.com/microsoft-teams/group-chat-software) | ![Icono de tarea pendiente](media/o365-todo-64x64.png) <br> [To-Do](https://todo.microsoft.com) | ![Icono de Visio](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Icono de Word](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) 
| ![Icono de Yammer](media/o365-yammer-64x64.png) <br> [Yammer<sup>2</sup>](https://products.office.com/yammer/yammer-overview) |

## <a name="supported-powershell-modules"></a>Módulos de PowerShell compatibles

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Icono de Azure](media/o365-azure-64x64.png) <br> [PowerShell de <br> Azure ad](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0) | ![Icono de Exchange](media/o365-exchange-64x64.png) <br> [PowerShell de <br> Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) | ![Icono de SharePoint](media/o365-sharepoint-64x64.png) <br> [PowerShell de <br> SharePoint Online](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell)

> [!NOTE]
> <sup>1</sup> pronto estará disponible la compatibilidad con OneDrive en MacOS. <br>
> <sup>2</sup> pronto estará disponible la compatibilidad con Yammer en escritorio de Windows y MacOS.