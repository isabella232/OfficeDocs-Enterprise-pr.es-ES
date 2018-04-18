---
title: Capacidades de Multi-Geo en Exchange Online
ms.author: chrisda
author: chrisda
manager: serdars
ms.date: 4/11/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Normal
ms.assetid: ''
description: Expandir su presencia en Office 365 para varias regiones geográficas con capacidades de multi-geo en Exchange Online.
ms.openlocfilehash: 6378f8a010b790674f07150aa39cbbc38c60b7fe
ms.sourcegitcommit: 63e2844daa2863dddcd84819966a708c434e8580
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="multi-geo-capabilities-in-exchange-online"></a><span data-ttu-id="d9ead-103">Capacidades de Multi-Geo en Exchange Online</span><span class="sxs-lookup"><span data-stu-id="d9ead-103">Multi-Geo Capabilities in Exchange Online</span></span>

<span data-ttu-id="d9ead-p101">Capacidades de Multi-Geo en Office 365 permiten un único arrendatario abarcar varias ubicaciones geográficas (Geos). Cuando Multi-Geo está habilitada, los clientes pueden seleccionar la ubicación del contenido del buzón de Exchange en línea (datos en reposo) en cada usuario.</span><span class="sxs-lookup"><span data-stu-id="d9ead-p101">Multi-Geo Capabilities in Office 365 enable a single tenant to span multiple geographic locations (Geos). When Multi-Geo is enabled, customers can select the location of Exchange Online mailbox content (data at rest) on a per-user basis.</span></span>

<span data-ttu-id="d9ead-p102">La ubicación inicial del inquilino (denominada el "default" o "central" ubicación) se determina basándose en su dirección de facturación. Cuando Multi-Geo está habilitada, se pueden colocar buzones en ubicaciones adicionales "satélite" por:</span><span class="sxs-lookup"><span data-stu-id="d9ead-p102">Your initial tenant location (referred to as your "default" or "central" location) is determined based on your billing address. When Multi-Geo is enabled, you can place mailboxes in additional "satellite" locations by:</span></span>

- <span data-ttu-id="d9ead-108">Crear un nuevo buzón de Exchange Online directamente en un satélite.</span><span class="sxs-lookup"><span data-stu-id="d9ead-108">Creating a new Exchange Online mailbox directly in a satellite.</span></span>

- <span data-ttu-id="d9ead-109">Mover un buzón de Exchange en línea existente a un satélite.</span><span class="sxs-lookup"><span data-stu-id="d9ead-109">Moving an existing Exchange Online mailbox into a satellite.</span></span>

- <span data-ttu-id="d9ead-110">Incorporación de un buzón de correo desde una organización de Exchange local directamente en un satélite.</span><span class="sxs-lookup"><span data-stu-id="d9ead-110">Onboarding a mailbox from an on-premises Exchange organization directly into a satellite.</span></span>

<span data-ttu-id="d9ead-111">Las zonas siguientes están disponibles para su uso en una configuración Multi-Geo:</span><span class="sxs-lookup"><span data-stu-id="d9ead-111">The following Geos are available for use in a Multi-Geo configuration:</span></span>

- <span data-ttu-id="d9ead-112">Asia Pacífico</span><span class="sxs-lookup"><span data-stu-id="d9ead-112">Asia Pacific</span></span>

- <span data-ttu-id="d9ead-113">Australia</span><span class="sxs-lookup"><span data-stu-id="d9ead-113">Australia</span></span>

- <span data-ttu-id="d9ead-114">Canadá</span><span class="sxs-lookup"><span data-stu-id="d9ead-114">Canada</span></span>

- <span data-ttu-id="d9ead-115">Unión Europea</span><span class="sxs-lookup"><span data-stu-id="d9ead-115">European Union</span></span>

- <span data-ttu-id="d9ead-116">India (actualmente sólo está disponible para clientes con direcciones de facturación en la India)</span><span class="sxs-lookup"><span data-stu-id="d9ead-116">India (currently only available to customers with billing addresses in India)</span></span>

- <span data-ttu-id="d9ead-117">Japón</span><span class="sxs-lookup"><span data-stu-id="d9ead-117">Japan</span></span>

- <span data-ttu-id="d9ead-118">Corea</span><span class="sxs-lookup"><span data-stu-id="d9ead-118">Korea</span></span>

- <span data-ttu-id="d9ead-119">Reino Unido</span><span class="sxs-lookup"><span data-stu-id="d9ead-119">United Kingdom</span></span>

- <span data-ttu-id="d9ead-120">Estados Unidos</span><span class="sxs-lookup"><span data-stu-id="d9ead-120">United States</span></span>

## <a name="prerequisite-configuration"></a><span data-ttu-id="d9ead-121">Configuración de requisitos previos</span><span class="sxs-lookup"><span data-stu-id="d9ead-121">Prerequisite configuration</span></span>
<span data-ttu-id="d9ead-p103">Antes de empezar a utilizar capacidades de Multi-Geo en Exchange Online, Microsoft tiene que configurar a su arrendatario Exchange Online para soporte de Multi-Geo. Este proceso de configuración inicial se desencadena al solicitar licencias del Multi-Geo y normalmente debe tener menos de 30 días para completar.</span><span class="sxs-lookup"><span data-stu-id="d9ead-p103">Before you can start using Multi-Geo capabilities in Exchange Online, Microsoft needs to configure your Exchange Online tenant for Multi-Geo support. This one-time configuration process is triggered when you order Multi-Geo licenses and should typically take less than 30 days to complete.</span></span>

<span data-ttu-id="d9ead-p104">Recibirá notificaciones en el [Centro de mensajes de Office 365](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093) cuando se ha iniciado y finalizado la configuración. Configuración se activa automáticamente al adquirir licencias del Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="d9ead-p104">You'll receive notifications in the [Office 365 message center](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093) when your configuration has started and completed. Configuration is automatically triggered when you buy Multi-Geo licenses.</span></span>

## <a name="mailbox-placement-and-moves"></a><span data-ttu-id="d9ead-126">Los movimientos y colocación de buzón</span><span class="sxs-lookup"><span data-stu-id="d9ead-126">Mailbox placement and moves</span></span>
<span data-ttu-id="d9ead-127">Tras completa los pasos previos de configuración Multi-Geo, a Microsoft Exchange Online respeta el atributo **PreferredDataLocation** en objetos de usuario en AD de Azure.</span><span class="sxs-lookup"><span data-stu-id="d9ead-127">After Microsoft completes the prerequisite Multi-Geo configuration steps, Exchange Online will honor the **PreferredDataLocation** attribute on user objects in Azure AD.</span></span>

<span data-ttu-id="d9ead-p105">Exchange Online sincroniza la propiedad **PreferredDataLocation** de Azure AD en la propiedad **MailboxRegion** en el servicio de directorio de Exchange en línea. El valor de **MailboxRegion** determina el Geo donde se colocarán los buzones de usuario y cualquier archivo asociado. No es posible configurar los buzones principales de buzón y archiving de un usuario para que residan en zonas distintas. Solo Geo puede configurarse por cada objeto de usuario.</span><span class="sxs-lookup"><span data-stu-id="d9ead-p105">Exchange Online synchronizes the **PreferredDataLocation** property from Azure AD into the **MailboxRegion** property in the Exchange Online directory service. The value of **MailboxRegion** determines the Geo where user mailboxes and any associated archive mailboxes will be placed. It isn't possible to configure a user's primary mailbox and archive mailboxes to reside in different Geos. Only one Geo may be configured per user object.</span></span>

- <span data-ttu-id="d9ead-132">Cuando **PreferredDataLocation** está configurado en un usuario con un buzón existente, el buzón se moverán automáticamente a la Geo especificado.</span><span class="sxs-lookup"><span data-stu-id="d9ead-132">When **PreferredDataLocation** is configured on a user with an existing mailbox, the mailbox will be automatically moved to the specified Geo.</span></span> 

- <span data-ttu-id="d9ead-133">Cuando **PreferredDataLocation** está configurado en un usuario sin un buzón existente, el buzón se aprovisionará en el Geo especificado.</span><span class="sxs-lookup"><span data-stu-id="d9ead-133">When **PreferredDataLocation** is configured on a user without an existing mailbox, the mailbox will be provisioned into the specified Geo.</span></span> 

- <span data-ttu-id="d9ead-134">Si no se especifica ningún Geo, el buzón se colocará en el valor predeterminado de Geo.</span><span class="sxs-lookup"><span data-stu-id="d9ead-134">If no Geo is specified, the mailbox will be placed in the default Geo.</span></span>

<span data-ttu-id="d9ead-p106">**Nota**: capacidades de Multi-Geo y Skype para reuniones de negocios en línea alojado regionalmente ambos utilizan la propiedad **PreferredDataLocation** en objetos de usuario para buscar servicios. Si configura los valores de **PreferredDataLocation** en objetos de usuario para reuniones regionalmente hospedados, el buzón y OneDrive para los usuarios se moverá automáticamente a la Geo especificado después de habilita Multi-Geo en el inquilino de Office 365.</span><span class="sxs-lookup"><span data-stu-id="d9ead-p106">**Note**: Multi-Geo capabilities and Skype for Business Online regionally hosted meetings both use the **PreferredDataLocation** property on user objects to locate services. If you configure **PreferredDataLocation** values on user objects for regionally hosted meetings, the mailbox and OneDrive for those users will be automatically moved to the specified Geo after Multi-Geo is enabled on the Office 365 tenant.</span></span>

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a><span data-ttu-id="d9ead-137">Limitaciones de características para Multi-Geo en Exchange Online</span><span class="sxs-lookup"><span data-stu-id="d9ead-137">Feature limitations for Multi-Geo in Exchange Online</span></span>
1. <span data-ttu-id="d9ead-p107">Sólo los buzones de usuario, buzones de recursos (buzones de sala y equipo) y buzones compartidos admiten características de Multi-Geo. Sólo puede colocar buzones de carpetas públicas y grupos de Office 365 en Geo principal del cliente.</span><span class="sxs-lookup"><span data-stu-id="d9ead-p107">Only user mailboxes, resource mailboxes (room and equipment mailboxes), and shared mailboxes support Multi-Geo features. You can only place public folder mailboxes and Office 365 Groups in the customer's home Geo.</span></span>
 
2. <span data-ttu-id="d9ead-p108">Seguridad y cumplimiento de normas características (por ejemplo, auditoría y eDiscovery) que están disponibles en el centro de administración de Exchange (EAF) no están disponibles en las organizaciones Multi-Geo. En su lugar, debe utilizar el [Centro de cumplimiento de normas y seguridad de Office 365](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) para configurar características de seguridad y cumplimiento de normas.</span><span class="sxs-lookup"><span data-stu-id="d9ead-p108">Security and compliance features (for example, auditing and eDiscovery) that are available in the Exchange admin center (EAC) aren't available in Multi-Geo organizations. Instead, you need to use the [Office 365 Security & Compliance Center](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) to configure security and compliance features.</span></span>

3. <span data-ttu-id="d9ead-p109">Outlook para usuarios de Mac puede experimentar una pérdida temporal de acceso a su carpeta de archiving en línea mientras mueve su buzón a un nuevo Geo. Esta condición se produce cuando del usuario principal y archive los buzones están en diferentes zonas, debido a movimientos de buzones entre Geo pueden completar en diferentes momentos.</span><span class="sxs-lookup"><span data-stu-id="d9ead-p109">Outlook for Mac users may experience a temporary loss of access to their Online Archive folder while you move their mailbox to a new Geo. This condition occurs when the user's the primary and archive mailboxes are in different Geos, because cross-Geo mailbox moves may complete at different times.</span></span>

4. <span data-ttu-id="d9ead-p110">Los usuarios no pueden compartir *carpetas del buzón* a través de zonas en Outlook en el web (anteriormente conocido como Outlook Web App u OWA). Por ejemplo, un usuario de la Unión Europea no puede utilizar Outlook en el web para abrir una carpeta compartida en un buzón que se encuentra en los Estados Unidos. Sin embargo, Outlook de los usuarios de web puede abrir *otros buzones* en distintas zonas utilizando una ventana de explorador independiente como se describe en [Abrir el buzón de otra persona en una ventana de explorador independiente en Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).</span><span class="sxs-lookup"><span data-stu-id="d9ead-p110">Users can't share *mailbox folders* across Geos in Outlook on the web (formerly known as Outlook Web App or OWA). For example, a user in the European Union can't use Outlook on the web to open a shared folder in a mailbox that's located in the United States. However, Outlook on the web users can open *other mailboxes* in different Geos by using a separate browser window as described in [Open another person’s mailbox in a separate browser window in Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).</span></span>

    <span data-ttu-id="d9ead-147">**Nota**: compartir una carpeta buzón entre Geo es compatible con Outlook en Windows.</span><span class="sxs-lookup"><span data-stu-id="d9ead-147">**Note**: Cross-Geo mailbox folder sharing is supported in Outlook on Windows.</span></span>

5. <span data-ttu-id="d9ead-p111">Actualmente, no es compatible entre Geo delegación de calendario en Outlook en el web. Delegación de calendario entre Geo es compatible con Outlook en Windows.</span><span class="sxs-lookup"><span data-stu-id="d9ead-p111">Currently, cross-Geo calendar delegation isn't supported in Outlook on the web. Cross-Geo calendar delegation is supported in Outlook on Windows.</span></span>

## <a name="administration"></a><span data-ttu-id="d9ead-150">Administración</span><span class="sxs-lookup"><span data-stu-id="d9ead-150">Administration</span></span> 
<span data-ttu-id="d9ead-p112">PowerShell remoto es requerido para ver y configurar propiedades de Geo en el entorno de Office 365. Para obtener información sobre los distintos módulos de PowerShell utilizados para administrar Office 365, vea [administración de Office 365 y Exchange Online con Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6).</span><span class="sxs-lookup"><span data-stu-id="d9ead-p112">Remote PowerShell is required to view and configure Geo-related properties in your Office 365 environment. For information on various PowerShell modules used to administer Office 365, see [Managing Office 365 and Exchange Online with Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6).</span></span>

- <span data-ttu-id="d9ead-p113">Necesita el [Módulo de PowerShell de Active Directory de Microsoft Azure](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 o posterior de v1.x para ver la propiedad **PreferredDataLocation** en objetos de usuario. Para conectarse a Azure AD PowerShell, vea [conectarse a Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span><span class="sxs-lookup"><span data-stu-id="d9ead-p113">You need the [Microsoft Azure Active Directory PowerShell Module](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 or later in v1.x to see the **PreferredDataLocation** property on user objects. To connect to Azure AD PowerShell, see [Connect to Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span></span> 

- <span data-ttu-id="d9ead-155">Para conectarse a Exchange Online PowerShell, vea [conectarse a Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span><span class="sxs-lookup"><span data-stu-id="d9ead-155">To connect to Exchange Online PowerShell, see [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span></span> 

### <a name="connect-directly-to-a-specific-geo-using-exchange-online-powershell"></a><span data-ttu-id="d9ead-156">Conectar directamente a un Geo específico usando PowerShell en línea de Exchange</span><span class="sxs-lookup"><span data-stu-id="d9ead-156">Connect directly to a specific Geo using Exchange Online PowerShell</span></span>
<span data-ttu-id="d9ead-p114">Normalmente, Exchange Online PowerShell se conectará con el valor predeterminado de Geo. Sin embargo, también puede conectar directamente a zonas no predeterminada. Debido a las mejoras de rendimiento, le recomendamos conectarse directamente a la Geo no predeterminada cuando sólo administra los usuarios en ese Geo.</span><span class="sxs-lookup"><span data-stu-id="d9ead-p114">Typically, Exchange Online PowerShell will connect to the default Geo. But, you can also connect directly to non-default Geos. Because of performance improvements, we recommend connecting directly to the non-default Geo when you only manage users in that Geo.</span></span>

<span data-ttu-id="d9ead-p115">Para conectarse a un Geo específica, el parámetro *ConnectionUri* es diferente de las instrucciones de conexión normales. El resto de los comandos y los valores son los mismos. Los pasos son:</span><span class="sxs-lookup"><span data-stu-id="d9ead-p115">To connect to a specific Geo, the *ConnectionUri* parameter is different than the regular connection instructions. The rest of the commands and values are the same. The steps are:</span></span>

1. <span data-ttu-id="d9ead-163">En el equipo local, abra Windows PowerShell y ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="d9ead-163">On your local computer, open Windows PowerShell and run the following command:</span></span>
    
    ```
    $UserCredential = Get-Credential
    ```
   <span data-ttu-id="d9ead-164">En el cuadro de diálogo **Solicitud de credencial de Windows PowerShell** , escriba la contraseña o cuenta de escuela y trabajo y, a continuación, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="d9ead-164">In the **Windows PowerShell Credential Request** dialog box, type your work or school account and password, and then click **OK**.</span></span>
    
2. <span data-ttu-id="d9ead-p116">Reemplazar `<emailaddress>` con la dirección de correo electrónico de **cualquier** buzón del destino geográfico y ejecute el siguiente comando. Sus permisos en el buzón y la relación con sus credenciales en el paso 1 no son un factor; la dirección de correo electrónico simplemente indica a Exchange Online dónde conectar.</span><span class="sxs-lookup"><span data-stu-id="d9ead-p116">Replace `<emailaddress>` with the email address of **any** mailbox in the target Geo and run the following command. Your permissions on the mailbox and the relationship to your credentials in Step 1 are not a factor; the email address simply tells Exchange Online where to connect.</span></span>
  
   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   <span data-ttu-id="d9ead-167">Por ejemplo, si olga@contoso.onmicrosoft.com es la dirección de correo electrónico de un buzón válido en el Geo que desea conectarse, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="d9ead-167">For example, if olga@contoso.onmicrosoft.com is the email address of a valid mailbox in the Geo you want to connect, run the following command:</span></span>

   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```
3. <span data-ttu-id="d9ead-168">Ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="d9ead-168">Run the following command:</span></span>
    
    ```
    Import-PSSession $Session
    ```

### <a name="azure-ad-connect-version-requirements"></a><span data-ttu-id="d9ead-169">Requisitos de versión de Azure Connect de AD</span><span class="sxs-lookup"><span data-stu-id="d9ead-169">Azure AD Connect version requirements</span></span>
<span data-ttu-id="d9ead-p117">Conectar DAA versión 1.1.524.0 o posterior es el único método admitido para establecer la propiedad **PreferredDataLocation** en objetos de usuario que se sincronizan desde local de Active Directory. Para obtener instrucciones detalladas, consulte [sincronización de directorio activo Azure Connect: configurar ubicación de datos preferido de recursos de Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span><span class="sxs-lookup"><span data-stu-id="d9ead-p117">AAD Connect version 1.1.524.0 or later is the only supported method for setting the **PreferredDataLocation** property on user objects that are synchronized from on-premises Active Directory. For detailed instructions, see [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

### <a name="geo-codes"></a><span data-ttu-id="d9ead-172">Códigos de geo</span><span class="sxs-lookup"><span data-stu-id="d9ead-172">Geo Codes</span></span>
<span data-ttu-id="d9ead-p118">Utilice códigos de tres letras para especificar el Geo en la propiedad **PreferredDataLocation** . En la siguiente tabla enumera los códigos para las zonas disponibles:</span><span class="sxs-lookup"><span data-stu-id="d9ead-p118">You use three-letter codes to specify the Geo in the **PreferredDataLocation** property. The following table lists the codes for the available Geos:</span></span>

|<span data-ttu-id="d9ead-175">Geo</span><span class="sxs-lookup"><span data-stu-id="d9ead-175">Geo</span></span> |<span data-ttu-id="d9ead-176">Código</span><span class="sxs-lookup"><span data-stu-id="d9ead-176">Code</span></span> |
|---------|---------|
|<span data-ttu-id="d9ead-177">Asia y Pacífico</span><span class="sxs-lookup"><span data-stu-id="d9ead-177">Asia/Pacific</span></span> |<span data-ttu-id="d9ead-178">APC</span><span class="sxs-lookup"><span data-stu-id="d9ead-178">APC</span></span> |
|<span data-ttu-id="d9ead-179">Australia</span><span class="sxs-lookup"><span data-stu-id="d9ead-179">Australia</span></span> |<span data-ttu-id="d9ead-180">AUSTRALIA</span><span class="sxs-lookup"><span data-stu-id="d9ead-180">AUS</span></span> |
|<span data-ttu-id="d9ead-181">Canadá</span><span class="sxs-lookup"><span data-stu-id="d9ead-181">Canada</span></span> |<span data-ttu-id="d9ead-182">PUEDE</span><span class="sxs-lookup"><span data-stu-id="d9ead-182">CAN</span></span> |
|<span data-ttu-id="d9ead-183">Unión Europea</span><span class="sxs-lookup"><span data-stu-id="d9ead-183">European Union</span></span> |<span data-ttu-id="d9ead-184">EUROS</span><span class="sxs-lookup"><span data-stu-id="d9ead-184">EUR</span></span> |
|<span data-ttu-id="d9ead-185">India</span><span class="sxs-lookup"><span data-stu-id="d9ead-185">India</span></span> |<span data-ttu-id="d9ead-186">IND</span><span class="sxs-lookup"><span data-stu-id="d9ead-186">IND</span></span> |
|<span data-ttu-id="d9ead-187">Japón</span><span class="sxs-lookup"><span data-stu-id="d9ead-187">Japan</span></span> |<span data-ttu-id="d9ead-188">JPN</span><span class="sxs-lookup"><span data-stu-id="d9ead-188">JPN</span></span> |
|<span data-ttu-id="d9ead-189">Corea</span><span class="sxs-lookup"><span data-stu-id="d9ead-189">Korea</span></span> |<span data-ttu-id="d9ead-190">KOR</span><span class="sxs-lookup"><span data-stu-id="d9ead-190">KOR</span></span> |
|<span data-ttu-id="d9ead-191">Reino Unido</span><span class="sxs-lookup"><span data-stu-id="d9ead-191">United Kingdom</span></span> |<span data-ttu-id="d9ead-192">GBR</span><span class="sxs-lookup"><span data-stu-id="d9ead-192">GBR</span></span> |
|<span data-ttu-id="d9ead-193">Estados Unidos</span><span class="sxs-lookup"><span data-stu-id="d9ead-193">United States</span></span> |<span data-ttu-id="d9ead-194">NAM</span><span class="sxs-lookup"><span data-stu-id="d9ead-194">NAM</span></span> |

<span data-ttu-id="d9ead-p119">**Nota**: las propiedades **PreferredDataLocation** y **MailboxRegion** son cadenas con ninguna comprobación de errores. Si escribe un valor no válido (por ejemplo, NAN) el buzón se colocará en el valor predeterminado de Geo.</span><span class="sxs-lookup"><span data-stu-id="d9ead-p119">**Note**: The **PreferredDataLocation** and **MailboxRegion** properties are strings with no error checking. If you enter an invalid value (for example, NAN) the mailbox will be placed in the default Geo.</span></span>

### <a name="view-the-available-geos-that-are-configured-in-your-exchange-online-organization"></a><span data-ttu-id="d9ead-197">Ver las zonas disponibles que están configurados en la organización de Exchange Online</span><span class="sxs-lookup"><span data-stu-id="d9ead-197">View the available Geos that are configured in your Exchange Online organization</span></span>
<span data-ttu-id="d9ead-198">Para ver la lista de zonas configuradas en la organización de Exchange Online, ejecute el siguiente comando en Exchange Online PowerShell:</span><span class="sxs-lookup"><span data-stu-id="d9ead-198">To see the list of configured Geos in your Exchange Online organization, run the following command in Exchange Online PowerShell:</span></span>

```
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table Region
```

<span data-ttu-id="d9ead-199">El resultado del comando tiene este aspecto:</span><span class="sxs-lookup"><span data-stu-id="d9ead-199">The output of the command looks like this:</span></span>

```
Region
------
APC
AUS
CAN
EUR
GBR
JPN
KOR
NAM
```

### <a name="find-the-geo-location-of-a-mailbox"></a><span data-ttu-id="d9ead-200">Buscar la ubicación geográfica de un buzón</span><span class="sxs-lookup"><span data-stu-id="d9ead-200">Find the Geo location of a mailbox</span></span>
<span data-ttu-id="d9ead-201">El cmdlet **Get-Mailbox** en Exchange Online PowerShell muestra las propiedades siguientes relacionadas con el Geo en buzones:</span><span class="sxs-lookup"><span data-stu-id="d9ead-201">The **Get-Mailbox** cmdlet in Exchange Online PowerShell displays the following Geo-related properties on mailboxes:</span></span>

- <span data-ttu-id="d9ead-202">**Base de datos**: las 3 primeras letras del nombre de la base de datos corresponden al código geográfico, que indica dónde se encuentra el buzón.</span><span class="sxs-lookup"><span data-stu-id="d9ead-202">**Database**: The first 3 letters of the database name correspond to the Geo code, which tells you where the mailbox is currently located.</span></span>

- <span data-ttu-id="d9ead-203">**MailboxRegion**: especifica el código geográfico establecido por el administrador (sincronizado desde **PreferredDataLocation** en Azure AD).</span><span class="sxs-lookup"><span data-stu-id="d9ead-203">**MailboxRegion**: Specifies the Geo code that was set by the admin (synchronized from **PreferredDataLocation** in Azure AD).</span></span>

- <span data-ttu-id="d9ead-204">**MailboxRegionLastUpdateTime**: indica MailboxRegion se actualizaron por última vez (automática o manualmente).</span><span class="sxs-lookup"><span data-stu-id="d9ead-204">**MailboxRegionLastUpdateTime**: Indicates when MailboxRegion was last updated (either automatically or manually).</span></span>

<span data-ttu-id="d9ead-205">Para ver las propiedades de un buzón, utilice la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="d9ead-205">To see these properties for a mailbox, use the following syntax:</span></span>

```
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

<span data-ttu-id="d9ead-206">Por ejemplo, para ver la información geográfica para el buzón de chris@contoso.onmicrosoft.com, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="d9ead-206">For example, to see the Geo information for the mailbox chris@contoso.onmicrosoft.com, run the following command:</span></span>

```
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

<span data-ttu-id="d9ead-207">El resultado del comando tiene este aspecto:</span><span class="sxs-lookup"><span data-stu-id="d9ead-207">The output of the command looks like this:</span></span>

```
Database                    : EURPR03DG077-db007 
MailboxRegion               : EUR 
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM 
```

> [!NOTE]
> <span data-ttu-id="d9ead-208">Si el código geográfico en el nombre de la base de datos no coincide con el valor de **MailboxRegion** , el buzón se moverá automáticamente a la Geo especificado por el valor de **MailboxRegion** (Exchange Online busca una falta de coincidencia entre estos valores de propiedad).</span><span class="sxs-lookup"><span data-stu-id="d9ead-208">If the Geo code in the database name doesn't match **MailboxRegion** value, the mailbox will be automatically moved to the Geo specified by the **MailboxRegion** value (Exchange Online looks for a mismatch between these property values).</span></span>

### <a name="move-an-existing-cloud-mailbox-to-a-specific-geo"></a><span data-ttu-id="d9ead-209">Mover un buzón existente de nube para un específico Geo</span><span class="sxs-lookup"><span data-stu-id="d9ead-209">Move an existing cloud mailbox to a specific Geo</span></span>
<span data-ttu-id="d9ead-210">Use los cmdlets **Get-MsolUser** y **MsolUser del conjunto** del módulo de AD de Azure para Windows PowerShell para ver o especificar el Geo donde se almacenará el buzón de un usuario.</span><span class="sxs-lookup"><span data-stu-id="d9ead-210">Use the **Get-MsolUser** and **Set-MsolUser** cmdlets in the Azure AD Module for Windows PowerShell to view or specify the Geo where a user's mailbox will be stored.</span></span>

<span data-ttu-id="d9ead-211">Para ver el valor de **PreferredDataLocation** para un usuario, utilice esta sintaxis en Azure AD PowerShell:</span><span class="sxs-lookup"><span data-stu-id="d9ead-211">To view the **PreferredDataLocation** value for a user, use this syntax in Azure AD PowerShell:</span></span>

```
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

<span data-ttu-id="d9ead-212">Por ejemplo, para ver el valor de **PreferredDataLocation** de la michelle@contoso.onmicrosoft.com usuario, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="d9ead-212">For example, to see the **PreferredDataLocation** value for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

```
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

<span data-ttu-id="d9ead-213">El resultado del comando tiene este aspecto:</span><span class="sxs-lookup"><span data-stu-id="d9ead-213">The output of the command looks like this:</span></span>

```
UserPrincipalName     : michelle@contoso.onmicrosoft.com
PreferredDataLocation : EUR
```

<span data-ttu-id="d9ead-214">Para modificar el valor de **PreferredDataLocation** para un objeto de usuario sólo nube, utilice la siguiente sintaxis en Azure AD PowerShell:</span><span class="sxs-lookup"><span data-stu-id="d9ead-214">To modify the **PreferredDataLocation** value for a cloud-only user object, use the following syntax in Azure AD PowerShell:</span></span>

``` 
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoCode>
```

<span data-ttu-id="d9ead-215">Por ejemplo, para establecer el valor de **PreferredDataLocation** a la Unión Europea (en euros) para la michelle@contoso.onmicrosoft.com usuario, ejecute el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="d9ead-215">For example, to set the **PreferredDataLocation** value to the European Union (EUR) for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

``` 
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

<span data-ttu-id="d9ead-216">**Notas**:</span><span class="sxs-lookup"><span data-stu-id="d9ead-216">**Notes**:</span></span>

- <span data-ttu-id="d9ead-p120">Como se mencionó anteriormente sincronizado para objetos de usuario de Active Directory de local, no puede utilizar este procedimiento. Debe cambiar el valor de **PreferredDataLocation** con conexión DAA. Para obtener más información, consulte [sincronización de directorio activo Azure Connect: configurar ubicación de datos preferido de recursos de Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span><span class="sxs-lookup"><span data-stu-id="d9ead-p120">As mentioned previously for synchronized user objects from on-premises Active Directory, you can't use this procedure. You need to change the **PreferredDataLocation** value using AAD Connect. For more information, see [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span> 

- <span data-ttu-id="d9ead-220">¿Cuánto tiempo tarda en mover un buzón depende de varios factores:</span><span class="sxs-lookup"><span data-stu-id="d9ead-220">How long it takes to move a mailbox depends on several factors:</span></span>
 
  - <span data-ttu-id="d9ead-221">El tamaño y el tipo de buzón.</span><span class="sxs-lookup"><span data-stu-id="d9ead-221">The size and type of mailbox.</span></span>
 
  - <span data-ttu-id="d9ead-222">El número de buzones que se mueve.</span><span class="sxs-lookup"><span data-stu-id="d9ead-222">The number of mailboxes being moved.</span></span>
 
  - <span data-ttu-id="d9ead-223">La disponibilidad de los recursos de movimiento.</span><span class="sxs-lookup"><span data-stu-id="d9ead-223">The availability of move resources.</span></span>

#### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a><span data-ttu-id="d9ead-224">Deshabilitado de mover los buzones que están en retención para litigios</span><span class="sxs-lookup"><span data-stu-id="d9ead-224">Move disabled mailboxes that are on Litigation Hold</span></span>
<span data-ttu-id="d9ead-p121">Deshabilitado buzones en retención para litigios que se conservan para propósitos no se pueden mover cambiando su valor de **PreferredDataLocation** en su estado deshabilitado de eDiscovery. Para mover un buzón deshabilitado en retención para litigios:</span><span class="sxs-lookup"><span data-stu-id="d9ead-p121">Disabled mailboxes on Litigation Hold that are preserved for eDiscovery purposes can't be moved by changing their **PreferredDataLocation** value in their disabled state. To move a disabled mailbox on litigation hold:</span></span>

1. <span data-ttu-id="d9ead-227">Asignar temporalmente una licencia en el buzón.</span><span class="sxs-lookup"><span data-stu-id="d9ead-227">Temporarily assign a license to the mailbox.</span></span>

2. <span data-ttu-id="d9ead-228">Cambiar el **PreferredDataLocation**.</span><span class="sxs-lookup"><span data-stu-id="d9ead-228">Change the **PreferredDataLocation**.</span></span>

3. <span data-ttu-id="d9ead-229">Eliminar la licencia del buzón de correo después de que se ha movido a la Geo seleccionada para volver a colocarla en el estado deshabilitado.</span><span class="sxs-lookup"><span data-stu-id="d9ead-229">Remove the license from the mailbox after it has been moved to the selected Geo to put it back into the disabled state.</span></span>

### <a name="create-new-cloud-mailboxes-in-a-specific-geo"></a><span data-ttu-id="d9ead-230">Crear nuevos buzones de nube en un geográfico específico</span><span class="sxs-lookup"><span data-stu-id="d9ead-230">Create new cloud mailboxes in a specific Geo</span></span> 
<span data-ttu-id="d9ead-231">Para crear un nuevo buzón en un geográfico específico, que debe hacer cualquiera de estos pasos:</span><span class="sxs-lookup"><span data-stu-id="d9ead-231">To create a new mailbox in a specific Geo, you need to do either of these steps:</span></span>

- <span data-ttu-id="d9ead-232">Configurar el valor de **PreferredDataLocation** como se describe en la anterior sección *antes de* crear el buzón de Exchange en línea (por ejemplo, al configurar el valor de **PreferredDataLocation** en un usuario antes de asignar una licencia).</span><span class="sxs-lookup"><span data-stu-id="d9ead-232">Configure the **PreferredDataLocation** value as described in the previous section *before* the mailbox is created in Exchange Online (for example, by configuring the **PreferredDataLocation** value on a user before assigning a license).</span></span> 

- <span data-ttu-id="d9ead-233">Asignar una licencia a la vez que se establece el valor de **PreferredDataLocation** .</span><span class="sxs-lookup"><span data-stu-id="d9ead-233">Assign a license at the same time you set the **PreferredDataLocation** value.</span></span>

<span data-ttu-id="d9ead-234">Para crear un nuevo sólo nube con licencia usuario (DAA conectar sincronizado) en un geográfico específico, utilice la siguiente sintaxis en Azure AD PowerShell:</span><span class="sxs-lookup"><span data-stu-id="d9ead-234">To create a new cloud-only licensed user (not AAD Connect synchronized) in a specific Geo, use the following syntax in Azure AD PowerShell:</span></span>

```
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoCode> 
```
<span data-ttu-id="d9ead-235">Este ejemplo crea una nueva cuenta de usuario para Elizabeth Brunner con los siguientes valores:</span><span class="sxs-lookup"><span data-stu-id="d9ead-235">This example create a new user account for Elizabeth Brunner with the following values:</span></span>

- <span data-ttu-id="d9ead-236">Nombre principal de usuario: ebrunner@contoso.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="d9ead-236">User principal name: ebrunner@contoso.onmicrosoft.com</span></span>

- <span data-ttu-id="d9ead-237">Nombre: Elizabeth</span><span class="sxs-lookup"><span data-stu-id="d9ead-237">First name: Elizabeth</span></span>

- <span data-ttu-id="d9ead-238">Apellido: Arturo López</span><span class="sxs-lookup"><span data-stu-id="d9ead-238">Last name: Brunner</span></span>

- <span data-ttu-id="d9ead-239">Mostrar nombre Elizabeth Brunner</span><span class="sxs-lookup"><span data-stu-id="d9ead-239">Display name Elizabeth Brunner</span></span>

- <span data-ttu-id="d9ead-240">Contraseña: genera de forma aleatoria y se muestra en los resultados del comando (ya no estamos utilizando el parámetro de *contraseña* )</span><span class="sxs-lookup"><span data-stu-id="d9ead-240">Password: randomly-generated and shown in the results of the command (because we're not using the *Password* parameter)</span></span>

- <span data-ttu-id="d9ead-241">Licencia: contoso:ENTERPRISEPREMIUM (E5)</span><span class="sxs-lookup"><span data-stu-id="d9ead-241">License: contoso:ENTERPRISEPREMIUM (E5)</span></span>

<span data-ttu-id="d9ead-242">3-ubicación: Australia (AUS)</span><span class="sxs-lookup"><span data-stu-id="d9ead-242">3- Location: Australia (AUS)</span></span>

```
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

<span data-ttu-id="d9ead-243">Para obtener más información sobre cómo crear nuevas cuentas de usuario y buscar valores LicenseAssignment en Azure AD PowerShell, consulte [crear cuentas de usuario con Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) y [ver licencias y servicios con PowerShell de Office 365](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).</span><span class="sxs-lookup"><span data-stu-id="d9ead-243">For more information about creating new user accounts and finding LicenseAssignment values in Azure AD PowerShell, see [Create user accounts with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) and [View licenses and services with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).</span></span>

> [!NOTE]
> <span data-ttu-id="d9ead-p122">Si está utilizando Exchange PowerShell para habilitar un buzón y necesita el buzón que se creen directamente en el Geo que se especifica en **PreferredDataLocation**, necesitará utilizar un cmdlet Exchange Online como **Enable-Mailbox** o **New-Mailbox** directamente con el servicio de nube. Si utiliza el cmdlet de Exchange local **Enable-RemoteMailbox** , se creará el buzón en el valor predeterminado de Geo.</span><span class="sxs-lookup"><span data-stu-id="d9ead-p122">If you are using Exchange PowerShell to enable a mailbox and need the mailbox to be created directly in the Geo that's specified in **PreferredDataLocation**, you need to use an Exchange Online cmdlet such as **Enable-Mailbox** or **New-Mailbox** directly against the cloud service. If you use the **Enable-RemoteMailbox** on-premises Exchange cmdlet, the mailbox will be created in the default Geo.</span></span>

### <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo"></a><span data-ttu-id="d9ead-246">Existente incorporado local buzones en un geográfico específico</span><span class="sxs-lookup"><span data-stu-id="d9ead-246">Onboard existing on-premises mailboxes in a specific Geo</span></span>
<span data-ttu-id="d9ead-247">Puede utilizar las herramientas estándar de incorporación y procesos para migrar un buzón desde una organización de Exchange local para Exchange Online, que incluye el [panel de la migración en el CEF](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331)y el cmdlet [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) en Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d9ead-247">You can use the standard onboarding tools and processes to migrate a mailbox from an on-premises Exchange organization to Exchange Online, including the [Migration dashboard in the EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331), and the [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) cmdlet in Exchange Online PowerShell.</span></span>

<span data-ttu-id="d9ead-p123">El primer paso es comprobar que existe un objeto de usuario para que cada buzón onboarded y compruebe que el valor correcto de la **PreferredDataLocation** está configurado en Azure AD. Las herramientas de incorporación respetarán el valor **PreferredDataLocation** y migrarán los buzones directamente a la Geo especificado.</span><span class="sxs-lookup"><span data-stu-id="d9ead-p123">The first step is to verify a user object exists for each mailbox to be onboarded, and verify the correct **PreferredDataLocation** value is configured in Azure AD. The onboarding tools will respect the **PreferredDataLocation** value and will migrate the mailboxes directly to the specified Geo.</span></span>

<span data-ttu-id="d9ead-250">O bien, puede utilizar los pasos siguientes para buzones incorporados directamente en un geográfico específico mediante el cmdlet [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) de PowerShell en línea de Exchange.</span><span class="sxs-lookup"><span data-stu-id="d9ead-250">Or, you can use the following steps to onboard mailboxes directly in a specific Geo using the [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) cmdlet in Exchange Online PowerShell.</span></span>

1. <span data-ttu-id="d9ead-p124">Compruebe que existe el objeto de usuario para que cada buzón sea onboarded y que **PreferredDataLocation** se establece en el valor deseado en Azure AD. El valor de **PreferredDataLocation** se sincronizarán con el atributo **MailboxRegion** del objeto de usuario de correo correspondiente de Exchange en línea.</span><span class="sxs-lookup"><span data-stu-id="d9ead-p124">Verify the user object exists for each mailbox to be onboarded and that **PreferredDataLocation** is set to the desired value in Azure AD. The value of **PreferredDataLocation** will be synchronized to the **MailboxRegion** attribute of the corresponding mail user object in Exchange Online.</span></span>

2. <span data-ttu-id="d9ead-253">Conectar directamente con el satélite específico Geo mediante las instrucciones de conexión del anteriormente en este tema.</span><span class="sxs-lookup"><span data-stu-id="d9ead-253">Connect directly to the specific satellite Geo using the connection instructions from earlier in this topic.</span></span>

3. <span data-ttu-id="d9ead-254">En PowerShell de Exchange Online, almacenar las credenciales de administrador local que se utiliza para realizar una migración de buzones en una variable ejecutando el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="d9ead-254">In Exchange Online PowerShell, store the on-premises administrator credentials that's used to perform a mailbox migration in a variable by running the following command:</span></span>

    ```
    $RC = Get-Credential
    ```

4. <span data-ttu-id="d9ead-255">En PowerShell en línea de Exchange, cree un nuevo **MoveRequest de nuevo** similar al ejemplo siguiente:</span><span class="sxs-lookup"><span data-stu-id="d9ead-255">In Exchange Online PowerShell, create a new **New-MoveRequest** similar to the following example:</span></span> 

    ```
    New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
    ```

5. <span data-ttu-id="d9ead-256">Repita el paso 4 # para cada buzón que necesita para migrar desde Exchange local al satélite Geo actualmente está conectado a.</span><span class="sxs-lookup"><span data-stu-id="d9ead-256">Repeat step #4 for every mailbox you need to migrate from on-premises Exchange to the satellite Geo you are currently connected to.</span></span>

6. <span data-ttu-id="d9ead-257">Si necesita migrar buzones adicionales a un satélite diferente Geo, repita los pasos 2 a 4 para cada satélite específico geográfico.</span><span class="sxs-lookup"><span data-stu-id="d9ead-257">If you need to migrate additional mailboxes to a different satellite Geo, repeat steps 2 through 4 for each specific satellite Geo.</span></span>

### <a name="multi-geo-reporting"></a><span data-ttu-id="d9ead-258">Reporting de Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="d9ead-258">Multi-Geo Reporting</span></span>
<span data-ttu-id="d9ead-p125">**Informes de uso de Multi-Geo** en el centro de administración de Office 365 se muestra el número de usuarios por Geo. El informe muestra la distribución de usuario para el mes actual y proporciona datos históricos de los últimos 6 meses.</span><span class="sxs-lookup"><span data-stu-id="d9ead-p125">**Multi-Geo Usage Reports** in the Office 365 admin center displays the user count by Geo. The report displays user distribution for the current month and provides historical data for the past 6 months.</span></span>
 
