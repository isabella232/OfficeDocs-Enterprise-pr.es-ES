---
title: Soporte técnico de Microsoft 365 Client App-acceso condicional
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: Office 365 Administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_Enterprise
- M365-subscription-management
f1.keywords:
- NOCSH
description: Descripción de la compatibilidad con aplicaciones cliente de Microsoft 365 para el acceso condicional
ms.openlocfilehash: 6081af2ad3bca69978a10baabeae0a13d783f0ae
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998508"
---
# <a name="microsoft-365-client-app-support--conditional-access"></a>Soporte técnico de Microsoft 365 Client App-acceso condicional

En el lugar de trabajo moderno, los usuarios pueden tener acceso a los recursos de la organización usando varios dispositivos y aplicaciones desde cualquier lugar. Como resultado, simplemente centrarse en quién puede tener acceso a un recurso ya no es suficiente. La organización también debe admitir cómo y dónde se obtiene acceso a un recurso en su infraestructura de control de acceso.

Con el dispositivo de Azure Active Directory (Azure AD), la ubicación y el acceso condicional basado en autenticación multifactor, puede cumplir con este nuevo requisito. El acceso condicional es una función de Azure AD que le permite aplicar controles en el acceso a las aplicaciones de su entorno, basados en condiciones específicas y administrados desde una ubicación central.

Obtenga más información sobre el [acceso condicional de Azure AD](https://docs.microsoft.com/azure/active-directory/conditional-access/).

## <a name="supported-platforms"></a>Plataformas compatibles

 - Escritorio de Windows 10
 - Aplicaciones modernas de Windows 10
 - Exploradores Web
 - Android
 - iOS
 - macOS<sup>1</sup>

Para obtener más información acerca de la compatibilidad de plataformas de Microsoft 365, vea [requisitos del sistema para microsoft 365](https://products.office.com/office-system-requirements).

## <a name="supported-clients"></a>Clientes compatibles

Las versiones más recientes de los siguientes clientes admiten el acceso condicional:

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Icono de Azure](media/o365-azure-64x64.png) <br> [Portal de Azure AD <br>](https://azure.microsoft.com/features/azure-portal/) | ![Icono de Access](media/o365-access-64x64.png) <br> [Access](https://products.office.com/access) | ![Icono del portal de empresa](media/o365-microsoft-64x64.png) <br> [Portal de empresa <br>](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal)  | ![Icono de Cortana](media/o365-cortana-64x64.png) <br> [Cortana](https://www.microsoft.com/cortana) | ![Icono de Delve](media/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) 
| ![Icono de Dynamics 365](media/o365-dynamics365-64x64.png) <br> [Dynamics 365](https://dynamics.microsoft.com) | ![Icono de borde](media/o365-edge-64x64.png) <br> [Microsoft Edge](https://www.microsoft.com/windows/microsoft-edge) | ![Icono de Exchange](media/o365-exchange-64x64.png) <br> [Exchange](https://products.office.com/exchange/exchange-online) | ![Icono de Excel](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) | ![Icono de formularios](media/o365-forms-64x64.png) <br> [Formularios](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) 
| ![Icono de Kaizala](media/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) | ![Icono de Office.com](media/o365-office-64x64.png) <br> [Office.com](https://www.office.com/) | ![Icono de lente](media/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | ![Icono de Office 365 administrador](media/o365-o365admin-64x64.png) <br> [Administrador de Microsoft 365 <br>](https://products.office.com/business/manage-office-365-admin-app) | ![Icono de OneDrive para la empresa](media/o365-OneDrive-64x64.png) <br> [OneDrive<sup>1</sup>](https://products.office.com/onedrive-for-business/online-cloud-storage) 
| ![Icono de OneNote](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Icono de Outlook](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) | ![Icono de Planificador](media/o365-planner-64x64.png) <br> [Planificador](https://products.office.com/business/task-management-software) | ![Icono de PowerApps](media/o365-powerapps-64x64.png) <br> [PowerApps](https://powerapps.microsoft.com) | ![Icono de automatización de energía](media/o365-flow-64x64.png) <br> [<br>Automatizar la alimentación](https://flow.microsoft.com)
| ![Icono de PowerBI](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com) | ![Icono de PowerPoint](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![Icono de proyecto](media/o365-project-64x64.png) <br> [Proyecto](https://products.office.com/project) | ![Icono de Publisher](media/o365-publisher-64x64.png) <br> [Publisher](https://products.office.com/publisher) | ![Icono de SharePoint](media/o365-sharepoint-64x64.png) <br> [SharePoint](https://products.office.com/sharepoint) 
| ![Icono de Skype Empresarial](media/o365-skypeforbusiness-64x64.png) <br> [Skype <br> empresarial](https://www.skype.com/business/) | ![Icono de notas adhesivas](media/o365-stickynotes-64x64.png) <br> [Notas rápidas](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw) | ![Icono de secuencia](media/o365-stream-64x64.png) <br> [Secuencia](https://stream.microsoft.com) | ![Icono de Sway](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) | ![Icono de Teams](media/o365-teams-64x64.png) <br> [Teams](https://products.office.com/microsoft-teams/group-chat-software) 
| ![Icono de tareas pendientes](media/o365-todo-64x64.png) <br> [Acciones que realizar](https://todo.microsoft.com) | ![Icono de Visio](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Icono de Word](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) | ![Icono de Yammer](media/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview)

## <a name="supported-powershell-modules"></a>Módulos de PowerShell compatibles

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Icono de Azure](media/o365-azure-64x64.png) <br> [PowerShell de Azure AD <br>](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0) | ![Icono de Exchange](media/o365-exchange-64x64.png) <br> [PowerShell de Exchange Online <br>](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) | ![Icono de SharePoint](media/o365-sharepoint-64x64.png) <br> [PowerShell de SharePoint Online <br>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

> [!NOTE]
> <sup>1</sup> pronto estará disponible la compatibilidad con OneDrive en MacOS.

## <a name="see-also"></a>Ver también

[Información general de Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
