---
title: Compatibilidad con aplicaciones cliente de Office 365 - acceso condicional
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 7/17/2018
audience: ITPro
ms.topic: article
ms.service: Office 365 Administration
localization_priority: None
ms.collection: Strat_O365_Enterprise
description: Comprender la compatibilidad con aplicaciones cliente de Office 365 para el acceso condicional
ms.openlocfilehash: f9a1b4c022b00569a392d7f50bfcae583847ea3c
ms.sourcegitcommit: 4e654517825b74a3bbe171b915b134ba49231e2e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/30/2018
ms.locfileid: "21541970"
---
# <a name="office-365-client-app-support---conditional-access"></a>Compatibilidad con aplicaciones cliente de Office 365 - acceso condicional

En el lugar de trabajo moderno, los usuarios pueden tener acceso a los recursos de su organización utilizando una gran variedad de aplicaciones y dispositivos desde prácticamente cualquier lugar. Como resultado, sólo se centra en quién puede tener acceso a un recurso no es suficiente. La organización debe admitir también cómo y dónde se está teniendo acceso a un recurso en su infraestructura de control de acceso. Con Azure AD dispositivo, la ubicación y acceso condicional basada en la autenticación con varios factores, puede satisfacer este requisito nuevo. Acceso condicional es una capacidad de Azure Active Directory que le permite aplicar controles en el acceso a las aplicaciones en su entorno, todas basada en condiciones específicas y administrar desde una ubicación central. 

Obtenga más información sobre [basadas en dispositivos](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-policy-connected-applications), [según la ubicación](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-locations)y acceso condicional [basado en MFA](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-conditions#users-and-groups) .

## <a name="supported-platforms"></a>Plataformas compatibles

 - Escritorio de Windows 10
 - Aplicaciones de Windows 10 moderno
 - Explorador web
 - Android
 - iOS
 - Mac OS<sup>1</sup>

## <a name="supported-clients"></a>Clientes compatibles

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Icono de profundizar](images/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) | ![Icono de Excel](images/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) | ![Icono de flujo](images/o365-flow-64x64.png) <br> [Flow](https://flow.microsoft.com) | ![Icono de formularios](images/o365-forms-64x64.png) <br> [Formularios](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) | ![Icono de Kaizala](images/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) 
| ![Icono de administración de Office 365](images/o365-o365admin-64x64.png) <br> [Office 365 <br> Admin](https://products.office.com/business/manage-office-365-admin-app) | ![OneDrive para el icono de negocio](images/o365-OneDrive-64x64.png) <br> [OneDrive](https://products.office.com/onedrive-for-business/online-cloud-storage) | ![Icono de OneNote](images/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Icono de Outlook](images/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) | ![Icono de organizador](images/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) 
| ![Icono de PowerBI](images/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com) | ![Icono de PowerPoint](images/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![Icono de proyecto](images/o365-project-64x64.png) <br> [Project](https://products.office.com/project) | ![Icono de SharePoint](images/o365-sharepoint-64x64.png) <br> [<sup>1</sup> de SharePoint](https://products.office.com/sharepoint) | ![Skype para el icono de negocio](images/o365-skypeforbusiness-64x64.png) <br> [Skype para <br> empresarial](https://www.skype.com/business/) 
| ![Icono de StaffHub](images/o365-staffhub-64x64.png) <br> [StaffHub](https://products.office.com/microsoft-staffhub/staff-scheduling-software) | ![Icono de secuencia](images/o365-stream-64x64.png) <br> [Secuencia](https://stream.microsoft.com) | ![Influir hora de elegir icono](images/o365-sway-64x64.png) <br> [Sway](https://sway.com) | ![Icono de equipos](images/o365-teams-64x64.png) <br> [Teams](https://products.office.com/microsoft-teams/group-chat-software) | ![Icono de tareas pendientes](images/o365-todo-64x64.png) <br> [To-Do](https://todo.microsoft.com) 
| ![Icono de Visio](images/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Icono de Word](images/o365-word-64x64.png) <br> [Word](https://products.office.com/word) | ![Icono de yammer](images/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview)

> [!NOTE]
> <sup>1</sup> admite la aplicación de SharePoint en Mac OS próximamente.