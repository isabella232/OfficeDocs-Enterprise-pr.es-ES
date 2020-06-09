---
title: 'Soporte de aplicaciones cliente de Office 365: Inicio de sesión único'
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
f1.keywords:
- NOCSH
description: Compatibilidad con aplicaciones cliente de Office 365 para inicio de sesión único (Single Sign-on).
ms.openlocfilehash: 8d6ba1701d9981bb5833bd6cf6ace641d5a27181
ms.sourcegitcommit: 576c3dbdef535f952a861197dea5348908da9504
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "44619336"
---
# <a name="office-365-client-app-support--single-sign-on"></a>Soporte de aplicaciones cliente de Office 365: Inicio de sesión único

*Este artículo se aplica tanto a Office 365 Enterprise como a Microsoft 365 Enterprise.*

El inicio de sesión único (SSO) agrega seguridad y comodidad cuando los usuarios inician sesión en aplicaciones de Azure Active Directory (Azure AD). Con el inicio de sesión único, los usuarios inician sesión una vez con una cuenta para tener acceso a dispositivos Unidos a un dominio, recursos de la compañía, software como aplicaciones de servicio (SaaS) y aplicaciones Web.

Obtenga más información sobre [el inicio de sesión único](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).

## <a name="supported-platforms"></a>Plataformas compatibles

 - Escritorio de Windows 10<sup>2</sup>
 - Aplicaciones modernas de Windows 10
 - Exploradores Web
 - Android<sup>3</sup>
 - iOS<sup>1</sup>
 - macOS<sup>4</sup>

Para obtener más información acerca de la compatibilidad de plataformas en Office 365, vea [System Requirements for office 365](https://products.office.com/office-system-requirements).

## <a name="supported-clients"></a>Clientes compatibles

Las versiones más recientes de los siguientes clientes admiten el inicio de sesión único:

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Icono de Access](media/o365-access-64x64.png) <br> [Access](https://products.office.com/access) | ![Icono del portal de empresa](media/o365-microsoft-64x64.png) <br> [<br>Portal<sup>de empresa 3, 4</sup>](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal) | ![Icono de Delve](media/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) | ![Icono de borde](media/o365-edge-64x64.png) <br> [Edge<sup>1</sup>](https://www.microsoft.com/windows/microsoft-edge) | ![Icono de Excel](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) 
| ![Icono de Kaizala](media/o365-kaizala-64x64.png) <br> [Kaizala<sup>1</sup>](https://products.office.com/en/business/microsoft-kaizala) | ![Icono de Office.com](media/o365-office-64x64.png) <br> [Office.com](https://www.office.com/) | ![Icono de lente](media/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | ![Icono de OneDrive para la empresa](media/o365-OneDrive-64x64.png) <br> [OneDrive](https://products.office.com/onedrive-for-business/online-cloud-storage) | ![Icono de OneNote](media/o365-OneNote-64x64.png) <br> [OneNote<sup>2</sup>](https://products.office.com/onenote) 
| ![Icono de Outlook](media/o365-outlook-64x64.png) <br> [Outlook<sup>4</sup>](https://products.office.com/outlook) | ![Icono de Planificador](media/o365-planner-64x64.png) <br> [Planificador](https://products.office.com/business/task-management-software) | ![Icono de automatización de energía](media/o365-flow-64x64.png) <br> [<br>Automatizar la alimentación](https://flow.microsoft.com) | ![Icono de PowerBI](media/o365-powerbi-64x64.png) <br> [Power BI<sup>2</sup>](https://powerbi.microsoft.com)| ![Icono de PowerPoint](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) 
| ![Icono de proyecto](media/o365-project-64x64.png) <br> [Proyecto](https://products.office.com/project) | ![Icono de Publisher](media/o365-publisher-64x64.png) <br> [Publisher](https://products.office.com/publisher) | ![Icono de SharePoint](media/o365-sharepoint-64x64.png) <br> [SharePoint](https://products.office.com/sharepoint) | ![Icono de notas adhesivas](media/o365-stickynotes-64x64.png) <br> [Notas rápidas](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw)  | ![Icono de Sway](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) 
| ![Icono de Teams](media/o365-teams-64x64.png) <br> [Teams<sup>2, 4</sup>](https://products.office.com/microsoft-teams/group-chat-software) | ![Icono de tareas pendientes](media/o365-todo-64x64.png) <br> [Acciones que realizar](https://todo.microsoft.com) | ![Icono de Visio](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Icono de pizarra](media/o365-whiteboard-64x64.png) <br> [Pizarra<sup>3</sup>](https://whiteboard.microsoft.com/) | ![Icono de Word](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) 
| ![Icono de Yammer](media/o365-yammer-64x64.png) <br> [Yammer<sup>2</sup>](https://products.office.com/yammer/yammer-overview) |

## <a name="supported-powershell-modules"></a>Módulos de PowerShell compatibles

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Icono de Azure](media/o365-azure-64x64.png) <br> [PowerShell de Azure AD <br>](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0) | ![Icono de Exchange](media/o365-exchange-64x64.png) <br> [PowerShell de Exchange Online <br>](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) | ![Icono de SharePoint](media/o365-sharepoint-64x64.png) <br> [PowerShell de SharePoint Online <br>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

> [!NOTE]
> <sup>1</sup> el soporte para Edge y Kaizala en iOS disponible próximamente. <br>
> <sup>2</sup> pronto estará disponible la compatibilidad con OneNote, PowerBI, Teams y Yammer en el escritorio de Windows 10. <br>
> <sup>3</sup> pronto estará disponible la compatibilidad con pizarra en Android. <br>
> <sup>4</sup> pronto estarán disponibles las ayudas para Outlook, Microsoft Teams y el portal de la empresa en MacOS. <br>

## <a name="see-also"></a>Consulte también

[Información general de Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
