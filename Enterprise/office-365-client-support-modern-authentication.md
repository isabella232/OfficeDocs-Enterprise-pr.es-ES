---
title: 'Soporte técnico de aplicaciones de cliente de Office 365: autenticación moderna'
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
description: Soporte técnico de la aplicación cliente de Office 365 para la autenticación moderna.
ms.openlocfilehash: 29abfdc5a9974b3e581e08556b675a725a6076dc
ms.sourcegitcommit: b1a32e8df403143fb34eaddf116aed3595228c8c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/09/2019
ms.locfileid: "36817267"
---
# <a name="office-365-client-app-support---modern-authentication"></a>Compatibilidad con aplicaciones cliente de Office 365: autenticación moderna

La autenticación moderna habilita el inicio de sesión basado en la biblioteca de autenticación de Active Directory (ADAL) para aplicaciones cliente de Office en distintas plataformas. Esto habilita las características de inicio de sesión, como la autenticación multifactor (MFA), la tarjeta inteligente y la autenticación basada en certificados.

Obtenga más información sobre [la autenticación multifactor](https://docs.microsoft.com/azure/active-directory/authentication/multi-factor-authentication) y [la autenticación basada en certificados](https://docs.microsoft.com/azure/active-directory/active-directory-certificate-based-authentication-get-started).

## <a name="supported-platforms"></a>Plataformas compatibles

 - Escritorio de Windows 10
 - Aplicaciones modernas de Windows 10
 - Exploradores Web<sup>1</sup>
 - Android<sup>2</sup>
 - iOS
 - Os

Para obtener más información acerca de la compatibilidad de plataformas en Office 365, vea [System Requirements for office 365](https://products.office.com/office-system-requirements).

## <a name="supported-clients"></a>Clientes compatibles

Las versiones más recientes de los siguientes clientes admiten la autenticación moderna:

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Icono de acceso](media/o365-access-64x64.png) <br> [Acceso](https://products.office.com/access) | ![Icono de Azure](media/o365-azure-64x64.png) <br> [Portal <br> de Azure](https://azure.microsoft.com/features/azure-portal/) | ![Icono del portal de empresa](media/o365-microsoft-64x64.png) <br> [Portal <br> de empresa](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal) | ![Icono de Delve](media/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) | ![Icono de Dynamics 365](media/o365-dynamics365-64x64.png) <br> [Dynamics 365](https://dynamics.microsoft.com) 
| ![Icono de borde](media/o365-edge-64x64.png) <br> [Vanguardia](https://www.microsoft.com/windows/microsoft-edge) | ![Icono de Excel](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) | ![Icono de flujo](media/o365-flow-64x64.png) <br> [Flow](https://flow.microsoft.com) | ![Icono formularios](media/o365-forms-64x64.png) <br> [Forms](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) | ![Icono de Kaizala](media/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) 
| ![Icono de Office.com](media/o365-office-64x64.png) <br> [Office.com](https://www.office.com/) | ![Icono de Office 365 administrador](media/o365-o365admin-64x64.png) <br> [Office 365 <br> administrador](https://products.office.com/business/manage-office-365-admin-app) | ![Icono de lente](media/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | ![Icono de OneDrive para la empresa](media/o365-OneDrive-64x64.png) <br> [OneDrive](https://products.office.com/onedrive-for-business/online-cloud-storage) |  ![Icono de OneNote](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) 
| ![Icono de Outlook](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) | ![Icono de Planner](media/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) | ![Icono de PowerApps](media/o365-powerapps-64x64.png) <br> [PowerApps](https://powerapps.microsoft.com) | ![Icono de PowerBI](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com)| ![Icono de PowerPoint](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) 
| ![Icono de proyecto](media/o365-project-64x64.png) <br> [Project](https://products.office.com/project) | ![Icono de Publisher](media/o365-publisher-64x64.png) <br> [Publisher](https://products.office.com/publisher) | ![Icono de SharePoint](media/o365-sharepoint-64x64.png) <br> [SharePoint](https://products.office.com/sharepoint) | ![Icono de Skype empresarial](media/o365-skypeforbusiness-64x64.png) <br> [Skype <br> empresarial<sup>1</sup>](https://www.skype.com/business/) | ![Icono de StaffHub](media/o365-staffhub-64x64.png) <br> [StaffHub](https://products.office.com/microsoft-staffhub/staff-scheduling-software)
| ![Icono de notas adhesivas](media/o365-stickynotes-64x64.png) <br> [Notas rápidas](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw) | ![Icono de secuencia](media/o365-stream-64x64.png) <br> [Stream](https://stream.microsoft.com) | ![Icono de Sway](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) | ![Icono de Teams](media/o365-teams-64x64.png) <br> [Teams](https://products.office.com/microsoft-teams/group-chat-software) | ![Icono de tareas pendientes](media/o365-todo-64x64.png) <br> [Para realizar](https://todo.microsoft.com) 
| ![Icono de Visio](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Icono de la pizarra](media/o365-whiteboard-64x64.png) <br> [Pizarra<sup>1</sup>,<sup>2</sup>](https://whiteboard.microsoft.com/) | ![Icono de Word](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) | ![Icono de Yammer](media/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview) | ![Icono de Yammer](media/o365-yammer-64x64.png) <br> [Notificador de Yammer <br>](https://products.office.com/yammer/yammer-overview) |  |

## <a name="supported-powershell-modules"></a>Módulos de PowerShell compatibles

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Icono de Azure](media/o365-azure-64x64.png) <br> [PowerShell de <br> Azure ad](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0) | ![Icono de Exchange](media/o365-exchange-64x64.png) <br> [PowerShell de <br> Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) | ![Icono de SharePoint](media/o365-sharepoint-64x64.png) <br> [PowerShell de <br> SharePoint Online](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell)

> [!NOTE]
> <sup>1</sup> la compatibilidad con pizarra y Skype empresarial en Web App disponible próximamente. <br>
> <sup>2</sup> pronto estará disponible la compatibilidad con pizarra en Android.