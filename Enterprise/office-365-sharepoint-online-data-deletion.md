---
title: Eliminación de datos de SharePoint Online de Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
f1.keywords:
- NOCSH
description: Una explicación de la eliminación de datos en SharePoint Online.
ms.openlocfilehash: f67fcedcb4454b06e47df12338445d07af2aa3e3
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997820"
---
# <a name="sharepoint-online-data-deletion-in-microsoft-365"></a><span data-ttu-id="80554-103">Eliminación de datos de SharePoint Online en Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="80554-103">SharePoint Online Data Deletion in Microsoft 365</span></span>

<span data-ttu-id="80554-104">SharePoint Online almacena objetos como código abstracto dentro de las bases de datos de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="80554-104">SharePoint Online stores objects as abstracted code within application databases.</span></span> <span data-ttu-id="80554-105">Cuando un usuario carga un archivo en SharePoint Online, ese archivo se desensambla y se traduce a código de aplicación y se almacena en varias tablas en varias bases de datos.</span><span class="sxs-lookup"><span data-stu-id="80554-105">When a user uploads a file to SharePoint Online, that file is disassembled and translated into application code and stored in multiple tables across multiple databases.</span></span> <span data-ttu-id="80554-106">En SharePoint Online, todo el contenido que carga un cliente se divide en fragmentos, cifrados (potencialmente con varias claves AES 256-bit), y distribuidos en el centro de datos.</span><span class="sxs-lookup"><span data-stu-id="80554-106">In SharePoint Online, all content that a customer uploads is broken into chunks, encrypted (potentially with multiple AES 256-bit keys), and distributed across the datacenter.</span></span> <span data-ttu-id="80554-107">Para obtener información específica sobre el proceso de fragmentación y cifrado, vea [cifrado en la nube de Microsoft](https://docs.microsoft.com/microsoft-365/compliance/office-365-encryption-in-the-microsoft-cloud-overview).</span><span class="sxs-lookup"><span data-stu-id="80554-107">For specific details about the chunking and encryption process, see [Encryption in the Microsoft Cloud](https://docs.microsoft.com/microsoft-365/compliance/office-365-encryption-in-the-microsoft-cloud-overview).</span></span> 

<span data-ttu-id="80554-108">En SharePoint Online, los elementos se conservan durante 93 días desde el momento en que los elimina de su ubicación original.</span><span class="sxs-lookup"><span data-stu-id="80554-108">In SharePoint Online, items are retained for 93 days from the time you delete them from their original location.</span></span> <span data-ttu-id="80554-109">Permanecen en la papelera de reciclaje del sitio todo el tiempo, a menos que alguien las elimine o vacíe dicha papelera de reciclaje.</span><span class="sxs-lookup"><span data-stu-id="80554-109">They stay in the site Recycle Bin the entire time, unless someone deletes them from there or empties that Recycle Bin.</span></span> <span data-ttu-id="80554-110">En ese caso, los elementos se dirigen a la papelera de reciclaje de la colección de sitios, donde permanecen durante el resto de los 93 días.</span><span class="sxs-lookup"><span data-stu-id="80554-110">In that case, the items go to the site collection Recycle Bin, where they stay for the remainder of the 93 days.</span></span> <span data-ttu-id="80554-111">Para obtener información sobre cómo restaurar elementos eliminados, vea [Restaurar elementos en la papelera de reciclaje de un sitio de SharePoint](https://support.office.com/article/6df466b6-55f2-4898-8d6e-c0dff851a0be#ID0EAADAAA=Online
) y [Restaurar elementos eliminados de la papelera de reciclaje de la colección de sitios](https://support.office.com/article/5fa924ee-16d7-487b-9a0a-021b9062d14b).</span><span class="sxs-lookup"><span data-stu-id="80554-111">For info about restoring deleted items, see [Restore items in the Recycle Bin of a SharePoint site](https://support.office.com/article/6df466b6-55f2-4898-8d6e-c0dff851a0be#ID0EAADAAA=Online
) and [Restore deleted items from the site collection recycle bin](https://support.office.com/article/5fa924ee-16d7-487b-9a0a-021b9062d14b).</span></span> <span data-ttu-id="80554-112">El tiempo de retención de la papelera de reciclaje no se puede configurar en SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="80554-112">The Recycle Bin retention time is not configurable in SharePoint Online.</span></span>

<span data-ttu-id="80554-113">Cuando se elimina una colección de sitios, también se elimina la jerarquía de los sitios de la colección y todo el contenido de los mismos:</span><span class="sxs-lookup"><span data-stu-id="80554-113">When you delete a site collection, you're also deleting the hierarchy of sites in the collection, and all content within them:</span></span>

- <span data-ttu-id="80554-114">Documentos y bibliotecas de documentos</span><span class="sxs-lookup"><span data-stu-id="80554-114">Documents and document libraries</span></span>
- <span data-ttu-id="80554-115">Listas y datos de lista</span><span class="sxs-lookup"><span data-stu-id="80554-115">Lists and list data</span></span>
- <span data-ttu-id="80554-116">Opciones de configuración del sitio</span><span class="sxs-lookup"><span data-stu-id="80554-116">Site configuration settings</span></span>
- <span data-ttu-id="80554-117">Información de roles y seguridad relacionada con el sitio o sus subsitios</span><span class="sxs-lookup"><span data-stu-id="80554-117">Role and security information that is related to the site or its subsites</span></span>
- <span data-ttu-id="80554-118">Subsitios del sitio web de nivel superior, su contenido e información de usuario</span><span class="sxs-lookup"><span data-stu-id="80554-118">Subsites of the top-level website, their contents, and user information</span></span>

<span data-ttu-id="80554-119">Si elimina por error una colección de sitios, puede restaurarla un administrador global o de SharePoint con el centro de administración de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="80554-119">If you accidentally delete a site collection, it can be restored by a global or SharePoint admin using the SharePoint admin center.</span></span>

<span data-ttu-id="80554-120">Las colecciones de sitios eliminadas se conservan durante 93 días.</span><span class="sxs-lookup"><span data-stu-id="80554-120">Deleted site collections are retained for 93 days.</span></span> <span data-ttu-id="80554-121">Después de 93 días, los sitios y todo su contenido y configuración se eliminan de forma permanente, incluidas las listas, las bibliotecas, las páginas y los subsitios.</span><span class="sxs-lookup"><span data-stu-id="80554-121">After 93 days, sites and all their content and settings are permanently deleted, including lists, libraries, pages, and any subsites.</span></span>

<span data-ttu-id="80554-122">La eliminación de hardware se produce cuando un usuario depura elementos eliminados de la papelera de reciclaje de la colección de sitios, cuando expiran los períodos de retención y copia de seguridad, o cuando un administrador elimina permanentemente una colección de sitios con el [cmdlet Remove-SPODeletedSite](/powershell/module/sharepoint-online/Remove-SPODeletedSite?view=sharepoint-ps).</span><span class="sxs-lookup"><span data-stu-id="80554-122">Hard deletion occurs when a user purges deleted items from the site collection Recycle Bin, when the retention and backup periods expire, or when an administrator permanently deletes a site collection using the [Remove-SPODeletedSite cmdlet](/powershell/module/sharepoint-online/Remove-SPODeletedSite?view=sharepoint-ps).</span></span> <span data-ttu-id="80554-123">Cuando un usuario elimina (elimina o purga permanentemente) contenido de SharePoint Online, también se eliminan todas las claves de cifrado de los fragmentos eliminados.</span><span class="sxs-lookup"><span data-stu-id="80554-123">When a user hard deletes (permanently deletes, or purges) content from SharePoint Online, all encryption keys for the deleted chunks are also deleted.</span></span> <span data-ttu-id="80554-124">Los bloques de los discos que anteriormente almacenaban los fragmentos eliminados se marcan como no usados y disponibles para volver a usarlos.</span><span class="sxs-lookup"><span data-stu-id="80554-124">The blocks on the disks that previously stored the deleted chunks are marked as unused and available for re-use.</span></span>
