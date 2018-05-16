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
description: Expanda su información de presencia de Office 365 a varias regiones geográficas con multi-ubican las capacidades de Exchange Online.
ms.openlocfilehash: ea00ab52142e92e122273ab4ba718e98bd94b572
ms.sourcegitcommit: 12d3223cc2d6bf39a8960409a923254e1790fd2f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2018
---
# <a name="multi-geo-capabilities-in-exchange-online"></a><span data-ttu-id="c03a2-103">Capacidades de Multi-Geo en Exchange Online</span><span class="sxs-lookup"><span data-stu-id="c03a2-103">Multi-Geo Capabilities in Exchange Online</span></span>

<span data-ttu-id="c03a2-p101">Capacidades de Multi-ubican en Office 365 habilitar un inquilino único abarcar varias ubicaciones geográficas (zonas). Al Multi-ubican está habilitada, los clientes pueden seleccionar la ubicación del contenido del buzón Exchange Online (datos en reposo) por usuario.</span><span class="sxs-lookup"><span data-stu-id="c03a2-p101">Multi-Geo Capabilities in Office 365 enable a single tenant to span multiple geographic locations (Geos). When Multi-Geo is enabled, customers can select the location of Exchange Online mailbox content (data at rest) on a per-user basis.</span></span>

<span data-ttu-id="c03a2-p102">La ubicación inicial de inquilinos (denominada el "default" o "central" ubicación) se determina en función de su dirección de facturación. Cuando está habilitada la Multi-ubican, puede poner los buzones de correo en ubicaciones adicionales "satélite" por:</span><span class="sxs-lookup"><span data-stu-id="c03a2-p102">Your initial tenant location (referred to as your "default" or "central" location) is determined based on your billing address. When Multi-Geo is enabled, you can place mailboxes in additional "satellite" locations by:</span></span>

- <span data-ttu-id="c03a2-108">Creación de un nuevo buzón de Exchange Online directamente en un satélite.</span><span class="sxs-lookup"><span data-stu-id="c03a2-108">Creating a new Exchange Online mailbox directly in a satellite.</span></span>

- <span data-ttu-id="c03a2-109">Mover un buzón de Exchange Online existente en un satélite.</span><span class="sxs-lookup"><span data-stu-id="c03a2-109">Moving an existing Exchange Online mailbox into a satellite.</span></span>

- <span data-ttu-id="c03a2-110">Incorporación de un buzón de correo desde una organización de Exchange local directamente en un satélite.</span><span class="sxs-lookup"><span data-stu-id="c03a2-110">Onboarding a mailbox from an on-premises Exchange organization directly into a satellite.</span></span>

<span data-ttu-id="c03a2-111">Las zonas siguientes están disponibles para su uso en una configuración de Multi-Geo:</span><span class="sxs-lookup"><span data-stu-id="c03a2-111">The following Geos are available for use in a Multi-Geo configuration:</span></span>

- <span data-ttu-id="c03a2-112">Asia Pacífico</span><span class="sxs-lookup"><span data-stu-id="c03a2-112">Asia Pacific</span></span>

- <span data-ttu-id="c03a2-113">Australia</span><span class="sxs-lookup"><span data-stu-id="c03a2-113">Australia</span></span>

- <span data-ttu-id="c03a2-114">Canadá</span><span class="sxs-lookup"><span data-stu-id="c03a2-114">Canada</span></span>

- <span data-ttu-id="c03a2-115">Unión Europea</span><span class="sxs-lookup"><span data-stu-id="c03a2-115">European Union</span></span>

- <span data-ttu-id="c03a2-116">India (actualmente sólo está disponible para clientes con direcciones de facturación en India)</span><span class="sxs-lookup"><span data-stu-id="c03a2-116">India (currently only available to customers with billing addresses in India)</span></span>

- <span data-ttu-id="c03a2-117">Japón</span><span class="sxs-lookup"><span data-stu-id="c03a2-117">Japan</span></span>

- <span data-ttu-id="c03a2-118">Corea</span><span class="sxs-lookup"><span data-stu-id="c03a2-118">Korea</span></span>

- <span data-ttu-id="c03a2-119">Reino Unido</span><span class="sxs-lookup"><span data-stu-id="c03a2-119">United Kingdom</span></span>

- <span data-ttu-id="c03a2-120">Estados Unidos</span><span class="sxs-lookup"><span data-stu-id="c03a2-120">United States</span></span>

## <a name="prerequisite-configuration"></a><span data-ttu-id="c03a2-121">Configuración de requisitos previos</span><span class="sxs-lookup"><span data-stu-id="c03a2-121">Prerequisite configuration</span></span>
<span data-ttu-id="c03a2-p103">Antes de empezar a usar las capacidades de Multi-Geo en Exchange Online, Microsoft tiene que configurar a su inquilino de Exchange Online para ofrecer compatibilidad con Multi-ubican. Este proceso de configuración de una sola vez se desencadena cuando pedir licencias Multi-Geo y normalmente debe tardar menos de 30 días en completarse.</span><span class="sxs-lookup"><span data-stu-id="c03a2-p103">Before you can start using Multi-Geo capabilities in Exchange Online, Microsoft needs to configure your Exchange Online tenant for Multi-Geo support. This one-time configuration process is triggered when you order Multi-Geo licenses and should typically take less than 30 days to complete.</span></span>

<span data-ttu-id="c03a2-p104">Recibirá notificaciones en el [Centro de mensajes de Office 365](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093) cuando la configuración se ha iniciado y completado. Configuración se desencadena automáticamente cuando comprar licencias de Multi-ubican.</span><span class="sxs-lookup"><span data-stu-id="c03a2-p104">You'll receive notifications in the [Office 365 message center](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093) when your configuration has started and completed. Configuration is automatically triggered when you buy Multi-Geo licenses.</span></span>

## <a name="mailbox-placement-and-moves"></a><span data-ttu-id="c03a2-126">Se desplaza y colocación de buzón de correo</span><span class="sxs-lookup"><span data-stu-id="c03a2-126">Mailbox placement and moves</span></span>
<span data-ttu-id="c03a2-127">Después de que Microsoft lleva a cabo los pasos de configuración de Multi-ubican necesario como requisito previos, Exchange Online respeta el atributo **PreferredDataLocation** en objetos de usuario en Azure AD.</span><span class="sxs-lookup"><span data-stu-id="c03a2-127">After Microsoft completes the prerequisite Multi-Geo configuration steps, Exchange Online will honor the **PreferredDataLocation** attribute on user objects in Azure AD.</span></span>

<span data-ttu-id="c03a2-p105">Exchange Online se sincroniza la propiedad **PreferredDataLocation** de Azure AD en la propiedad **MailboxRegion** en el servicio de directorio Exchange Online. El valor de **MailboxRegion** determina el ubican donde se colocará los buzones de usuario y cualquier archivo asociado. No es posible configurar los buzones principales de buzón de correo y de archivo de un usuario para que residan en diferentes zonas. Se puede configurar ubican sólo una por cada objeto de usuario.</span><span class="sxs-lookup"><span data-stu-id="c03a2-p105">Exchange Online synchronizes the **PreferredDataLocation** property from Azure AD into the **MailboxRegion** property in the Exchange Online directory service. The value of **MailboxRegion** determines the Geo where user mailboxes and any associated archive mailboxes will be placed. It isn't possible to configure a user's primary mailbox and archive mailboxes to reside in different Geos. Only one Geo may be configured per user object.</span></span>

- <span data-ttu-id="c03a2-132">Cuando **PreferredDataLocation** está configurado en un usuario con un buzón existente, el buzón de correo se moverán automáticamente a la ubican especificado.</span><span class="sxs-lookup"><span data-stu-id="c03a2-132">When **PreferredDataLocation** is configured on a user with an existing mailbox, the mailbox will be automatically moved to the specified Geo.</span></span> 

- <span data-ttu-id="c03a2-133">Cuando **PreferredDataLocation** está configurado en un usuario sin un buzón existente, el buzón de correo se aprovisionará en el ubican especificado.</span><span class="sxs-lookup"><span data-stu-id="c03a2-133">When **PreferredDataLocation** is configured on a user without an existing mailbox, the mailbox will be provisioned into the specified Geo.</span></span> 

- <span data-ttu-id="c03a2-134">Si no se especifica ningún ubican, el buzón de correo se colocará en el valor predeterminado ubican.</span><span class="sxs-lookup"><span data-stu-id="c03a2-134">If no Geo is specified, the mailbox will be placed in the default Geo.</span></span>

<span data-ttu-id="c03a2-p106">**Nota**: Multi-ubican capacidades y Skype para profesionales reuniones en línea hospedado regional ambos usan la propiedad **PreferredDataLocation** en objetos de usuario para localizan los servicios. Si configura los valores de **PreferredDataLocation** en objetos de usuario para las reuniones de ámbito regional hospedados, el buzón de correo para esos usuarios se moverá automáticamente a la ubican especificado después de habilita Multi-ubican en el inquilino de Office 365.</span><span class="sxs-lookup"><span data-stu-id="c03a2-p106">**Note**: Multi-Geo capabilities and Skype for Business Online regionally hosted meetings both use the **PreferredDataLocation** property on user objects to locate services. If you configure **PreferredDataLocation** values on user objects for regionally hosted meetings, the mailbox for those users will be automatically moved to the specified Geo after Multi-Geo is enabled on the Office 365 tenant.</span></span>

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a><span data-ttu-id="c03a2-137">Limitaciones de características para Multi-Geo en Exchange Online</span><span class="sxs-lookup"><span data-stu-id="c03a2-137">Feature limitations for Multi-Geo in Exchange Online</span></span>
1. <span data-ttu-id="c03a2-p107">Sólo buzones de usuario, buzones de recursos (buzones de correo de sala y equipamiento) y buzones compartidos admiten características de Multi-ubican. Sólo puede colocar buzones de carpetas públicas y grupos de Office 365 en ubican principal del cliente.</span><span class="sxs-lookup"><span data-stu-id="c03a2-p107">Only user mailboxes, resource mailboxes (room and equipment mailboxes), and shared mailboxes support Multi-Geo features. You can only place public folder mailboxes and Office 365 Groups in the customer's home Geo.</span></span>
 
2. <span data-ttu-id="c03a2-p108">Seguridad y cumplimiento de normas características (por ejemplo, auditoría y exhibición de documentos electrónicos) que están disponibles en el centro de administración de Exchange (EAC) no están disponibles en las organizaciones Multi-ubican. En su lugar, debe usar el [Centro de cumplimiento y seguridad de Office 365](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) para configurar las características de seguridad y cumplimiento de normas.</span><span class="sxs-lookup"><span data-stu-id="c03a2-p108">Security and compliance features (for example, auditing and eDiscovery) that are available in the Exchange admin center (EAC) aren't available in Multi-Geo organizations. Instead, you need to use the [Office 365 Security & Compliance Center](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) to configure security and compliance features.</span></span>

3. <span data-ttu-id="c03a2-p109">Outlook para los usuarios de Mac puede experimentar una pérdida temporal de acceso a su carpeta de archivo en línea mientras mover sus buzones de correo a un nuevo ubican. Esta condición se produce cuando la principal del usuario y buzones de archivo se encuentran en diferentes zonas, debido a que los movimientos de buzones entre ubican pueden completar en momentos diferentes.</span><span class="sxs-lookup"><span data-stu-id="c03a2-p109">Outlook for Mac users may experience a temporary loss of access to their Online Archive folder while you move their mailbox to a new Geo. This condition occurs when the user's the primary and archive mailboxes are in different Geos, because cross-Geo mailbox moves may complete at different times.</span></span>

4. <span data-ttu-id="c03a2-p110">Los usuarios no pueden compartir *las carpetas de buzón de correo* entre zonas en Outlook, en la web (anteriormente conocido como Outlook Web App u OWA). Por ejemplo, un usuario en la Unión Europea no puede usar Outlook en la web para abrir una carpeta compartida en un buzón que se encuentra en los Estados Unidos. Sin embargo, Outlook en los usuarios de web puede abrir *otros buzones de correo* en diferentes zonas mediante el uso de una ventana del explorador independiente como se describe en [Abra el buzón de otra persona en una ventana del explorador independiente en Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).</span><span class="sxs-lookup"><span data-stu-id="c03a2-p110">Users can't share *mailbox folders* across Geos in Outlook on the web (formerly known as Outlook Web App or OWA). For example, a user in the European Union can't use Outlook on the web to open a shared folder in a mailbox that's located in the United States. However, Outlook on the web users can open *other mailboxes* in different Geos by using a separate browser window as described in [Open another person’s mailbox in a separate browser window in Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).</span></span>

    <span data-ttu-id="c03a2-147">**Nota**: compartir una carpeta buzón entre Geo se admite en Outlook en Windows.</span><span class="sxs-lookup"><span data-stu-id="c03a2-147">**Note**: Cross-Geo mailbox folder sharing is supported in Outlook on Windows.</span></span>

5. <span data-ttu-id="c03a2-p111">Actualmente, no es compatible entre ubican delegación de calendario en Outlook en el web. Delegación de calendario entre Geo se admite en Outlook en Windows.</span><span class="sxs-lookup"><span data-stu-id="c03a2-p111">Currently, cross-Geo calendar delegation isn't supported in Outlook on the web. Cross-Geo calendar delegation is supported in Outlook on Windows.</span></span>

## <a name="administration"></a><span data-ttu-id="c03a2-150">Administración</span><span class="sxs-lookup"><span data-stu-id="c03a2-150">Administration</span></span> 
<span data-ttu-id="c03a2-p112">PowerShell remoto es necesario para ver y configurar las propiedades relacionadas con ubican en el entorno de Office 365. Para obtener información sobre los distintos módulos de PowerShell que se utiliza para Office 365, vea [administración de Office 365 y Exchange Online con Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6).</span><span class="sxs-lookup"><span data-stu-id="c03a2-p112">Remote PowerShell is required to view and configure Geo-related properties in your Office 365 environment. For information on various PowerShell modules used to administer Office 365, see [Managing Office 365 and Exchange Online with Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6).</span></span>

- <span data-ttu-id="c03a2-p113">Necesitará el [Módulo de PowerShell de Microsoft Azure Active Directory](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 o más adelante en v1.x para ver la propiedad **PreferredDataLocation** en objetos de usuario. Para conectarse a AD de Windows Azure PowerShell, vea [Connect to Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span><span class="sxs-lookup"><span data-stu-id="c03a2-p113">You need the [Microsoft Azure Active Directory PowerShell Module](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 or later in v1.x to see the **PreferredDataLocation** property on user objects. To connect to Azure AD PowerShell, see [Connect to Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span></span> 

- <span data-ttu-id="c03a2-155">Para conectarse a Exchange Online PowerShell, vea [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span><span class="sxs-lookup"><span data-stu-id="c03a2-155">To connect to Exchange Online PowerShell, see [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span></span> 

### <a name="connect-directly-to-a-specific-geo-using-exchange-online-powershell"></a><span data-ttu-id="c03a2-156">Conectar directamente a un ubican específica con Exchange Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="c03a2-156">Connect directly to a specific Geo using Exchange Online PowerShell</span></span>
<span data-ttu-id="c03a2-p114">Normalmente, Exchange Online PowerShell se conectará a la predeterminada ubican. Sin embargo, también puede conectarse directamente a zonas no predeterminado. Debido a las mejoras de rendimiento, se recomienda conectarse directamente a la ubican no predeterminado al administrar sólo los usuarios de ese ubican.</span><span class="sxs-lookup"><span data-stu-id="c03a2-p114">Typically, Exchange Online PowerShell will connect to the default Geo. But, you can also connect directly to non-default Geos. Because of performance improvements, we recommend connecting directly to the non-default Geo when you only manage users in that Geo.</span></span>

<span data-ttu-id="c03a2-p115">Para conectarse a un ubican específica, el parámetro *ConnectionUri* es diferente de las instrucciones de conexión regular. El resto de los comandos y los valores son los mismos. Los pasos son:</span><span class="sxs-lookup"><span data-stu-id="c03a2-p115">To connect to a specific Geo, the *ConnectionUri* parameter is different than the regular connection instructions. The rest of the commands and values are the same. The steps are:</span></span>

1. <span data-ttu-id="c03a2-163">En el equipo local, abra Windows PowerShell y ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="c03a2-163">On your local computer, open Windows PowerShell and run the following command:</span></span>
    
    ```
    $UserCredential = Get-Credential
    ```
   <span data-ttu-id="c03a2-164">En el cuadro de diálogo **Solicitud de credenciales de Windows PowerShell** , escriba su trabajo o escuela cuenta y su contraseña y, a continuación, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="c03a2-164">In the **Windows PowerShell Credential Request** dialog box, type your work or school account and password, and then click **OK**.</span></span>
    
2. <span data-ttu-id="c03a2-p116">Reemplace `<emailaddress>` con la dirección de correo electrónico de **cualquier** buzón de correo en el destino Geo y ejecute el comando siguiente. Los permisos en el buzón de correo y la relación con sus credenciales en el paso 1 no son un factor; la dirección de correo electrónico simplemente indica a Exchange Online dónde debe conectarse.</span><span class="sxs-lookup"><span data-stu-id="c03a2-p116">Replace `<emailaddress>` with the email address of **any** mailbox in the target Geo and run the following command. Your permissions on the mailbox and the relationship to your credentials in Step 1 are not a factor; the email address simply tells Exchange Online where to connect.</span></span>
  
   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   <span data-ttu-id="c03a2-167">Por ejemplo, si olga@contoso.onmicrosoft.com es la dirección de correo electrónico de un buzón de correo válido en el Geo va a conectar, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="c03a2-167">For example, if olga@contoso.onmicrosoft.com is the email address of a valid mailbox in the Geo you want to connect, run the following command:</span></span>

   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```
3. <span data-ttu-id="c03a2-168">Ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="c03a2-168">Run the following command:</span></span>
    
    ```
    Import-PSSession $Session
    ```

### <a name="azure-ad-connect-version-requirements"></a><span data-ttu-id="c03a2-169">Requisitos de versión de Azure Connect de AD</span><span class="sxs-lookup"><span data-stu-id="c03a2-169">Azure AD Connect version requirements</span></span>
<span data-ttu-id="c03a2-p117">Conectar AAD versión 1.1.524.0 o posterior es el único método admitido para establecer la propiedad **PreferredDataLocation** en los objetos de usuario que se sincronizan desde Active Directory local. Para obtener instrucciones detalladas, consulte [sincronización de Azure Active Directory Connect: configurar la ubicación de datos preferido para recursos de Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span><span class="sxs-lookup"><span data-stu-id="c03a2-p117">AAD Connect version 1.1.524.0 or later is the only supported method for setting the **PreferredDataLocation** property on user objects that are synchronized from on-premises Active Directory. For detailed instructions, see [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

### <a name="geo-codes"></a><span data-ttu-id="c03a2-172">Códigos de geo</span><span class="sxs-lookup"><span data-stu-id="c03a2-172">Geo Codes</span></span>
<span data-ttu-id="c03a2-p118">Use los códigos de tres letras para especificar el ubican en la propiedad **PreferredDataLocation** . En la siguiente tabla se enumera los códigos de las zonas disponibles:</span><span class="sxs-lookup"><span data-stu-id="c03a2-p118">You use three-letter codes to specify the Geo in the **PreferredDataLocation** property. The following table lists the codes for the available Geos:</span></span>

|<span data-ttu-id="c03a2-175">Geo</span><span class="sxs-lookup"><span data-stu-id="c03a2-175">Geo</span></span> |<span data-ttu-id="c03a2-176">Código</span><span class="sxs-lookup"><span data-stu-id="c03a2-176">Code</span></span> |
|---------|---------|
|<span data-ttu-id="c03a2-177">Asia Pacífico</span><span class="sxs-lookup"><span data-stu-id="c03a2-177">Asia/Pacific</span></span> |<span data-ttu-id="c03a2-178">APC</span><span class="sxs-lookup"><span data-stu-id="c03a2-178">APC</span></span> |
|<span data-ttu-id="c03a2-179">Australia</span><span class="sxs-lookup"><span data-stu-id="c03a2-179">Australia</span></span> |<span data-ttu-id="c03a2-180">AUSTRALIA</span><span class="sxs-lookup"><span data-stu-id="c03a2-180">AUS</span></span> |
|<span data-ttu-id="c03a2-181">Canadá</span><span class="sxs-lookup"><span data-stu-id="c03a2-181">Canada</span></span> |<span data-ttu-id="c03a2-182">PUEDE</span><span class="sxs-lookup"><span data-stu-id="c03a2-182">CAN</span></span> |
|<span data-ttu-id="c03a2-183">Unión Europea</span><span class="sxs-lookup"><span data-stu-id="c03a2-183">European Union</span></span> |<span data-ttu-id="c03a2-184">EUROS</span><span class="sxs-lookup"><span data-stu-id="c03a2-184">EUR</span></span> |
|<span data-ttu-id="c03a2-185">India</span><span class="sxs-lookup"><span data-stu-id="c03a2-185">India</span></span> |<span data-ttu-id="c03a2-186">IND</span><span class="sxs-lookup"><span data-stu-id="c03a2-186">IND</span></span> |
|<span data-ttu-id="c03a2-187">Japón</span><span class="sxs-lookup"><span data-stu-id="c03a2-187">Japan</span></span> |<span data-ttu-id="c03a2-188">JAPONÉS</span><span class="sxs-lookup"><span data-stu-id="c03a2-188">JPN</span></span> |
|<span data-ttu-id="c03a2-189">Corea</span><span class="sxs-lookup"><span data-stu-id="c03a2-189">Korea</span></span> |<span data-ttu-id="c03a2-190">COREANO</span><span class="sxs-lookup"><span data-stu-id="c03a2-190">KOR</span></span> |
|<span data-ttu-id="c03a2-191">Reino Unido</span><span class="sxs-lookup"><span data-stu-id="c03a2-191">United Kingdom</span></span> |<span data-ttu-id="c03a2-192">GBR</span><span class="sxs-lookup"><span data-stu-id="c03a2-192">GBR</span></span> |
|<span data-ttu-id="c03a2-193">Estados Unidos</span><span class="sxs-lookup"><span data-stu-id="c03a2-193">United States</span></span> |<span data-ttu-id="c03a2-194">NOMBRE</span><span class="sxs-lookup"><span data-stu-id="c03a2-194">NAM</span></span> |

<span data-ttu-id="c03a2-p119">**Nota**: las propiedades **PreferredDataLocation** y **MailboxRegion** son cadenas con ninguna comprobación de errores. Si escribe un valor no válido (por ejemplo, NAN) el buzón de correo se colocará en el valor predeterminado ubican.</span><span class="sxs-lookup"><span data-stu-id="c03a2-p119">**Note**: The **PreferredDataLocation** and **MailboxRegion** properties are strings with no error checking. If you enter an invalid value (for example, NAN) the mailbox will be placed in the default Geo.</span></span>

### <a name="view-the-available-geos-that-are-configured-in-your-exchange-online-organization"></a><span data-ttu-id="c03a2-197">Ver las zonas disponibles que están configurados en la organización de Exchange Online</span><span class="sxs-lookup"><span data-stu-id="c03a2-197">View the available Geos that are configured in your Exchange Online organization</span></span>
<span data-ttu-id="c03a2-198">Para ver la lista de zonas configuradas en la organización de Exchange Online, ejecute el siguiente comando en Exchange Online PowerShell:</span><span class="sxs-lookup"><span data-stu-id="c03a2-198">To see the list of configured Geos in your Exchange Online organization, run the following command in Exchange Online PowerShell:</span></span>

```
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table Region
```

<span data-ttu-id="c03a2-199">El resultado del comando tiene este aspecto:</span><span class="sxs-lookup"><span data-stu-id="c03a2-199">The output of the command looks like this:</span></span>

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

### <a name="find-the-geo-location-of-a-mailbox"></a><span data-ttu-id="c03a2-200">Busque la ubicación geográfica de un buzón de correo</span><span class="sxs-lookup"><span data-stu-id="c03a2-200">Find the Geo location of a mailbox</span></span>
<span data-ttu-id="c03a2-201">El cmdlet **Get-Mailbox** en Exchange Online PowerShell muestra las siguientes propiedades relacionadas con ubican en los buzones de correo:</span><span class="sxs-lookup"><span data-stu-id="c03a2-201">The **Get-Mailbox** cmdlet in Exchange Online PowerShell displays the following Geo-related properties on mailboxes:</span></span>

- <span data-ttu-id="c03a2-202">**Base de datos**: el primero 3 letras del nombre de base de datos se corresponden con el código ubican, que indica donde se encuentra actualmente el buzón de correo.</span><span class="sxs-lookup"><span data-stu-id="c03a2-202">**Database**: The first 3 letters of the database name correspond to the Geo code, which tells you where the mailbox is currently located.</span></span>

- <span data-ttu-id="c03a2-203">**MailboxRegion**: especifica el código ubican establecido por el administrador (sincronizado desde **PreferredDataLocation** en Azure AD).</span><span class="sxs-lookup"><span data-stu-id="c03a2-203">**MailboxRegion**: Specifies the Geo code that was set by the admin (synchronized from **PreferredDataLocation** in Azure AD).</span></span>

- <span data-ttu-id="c03a2-204">**MailboxRegionLastUpdateTime**: indica cuándo se actualizó por última vez las MailboxRegion (automático o manual).</span><span class="sxs-lookup"><span data-stu-id="c03a2-204">**MailboxRegionLastUpdateTime**: Indicates when MailboxRegion was last updated (either automatically or manually).</span></span>

<span data-ttu-id="c03a2-205">Para ver estas propiedades para un buzón de correo, use la siguiente sintaxis:</span><span class="sxs-lookup"><span data-stu-id="c03a2-205">To see these properties for a mailbox, use the following syntax:</span></span>

```
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

<span data-ttu-id="c03a2-206">Por ejemplo, para ver la información de Geo para el buzón de correo chris@contoso.onmicrosoft.com, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="c03a2-206">For example, to see the Geo information for the mailbox chris@contoso.onmicrosoft.com, run the following command:</span></span>

```
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

<span data-ttu-id="c03a2-207">El resultado del comando tiene este aspecto:</span><span class="sxs-lookup"><span data-stu-id="c03a2-207">The output of the command looks like this:</span></span>

```
Database                    : EURPR03DG077-db007 
MailboxRegion               : EUR 
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM 
```

> [!NOTE]
> <span data-ttu-id="c03a2-208">Si el código ubican en el nombre de la base de datos no coincide con el valor de **MailboxRegion** , el buzón de correo se moverán automáticamente a la ubican especificado por el valor de **MailboxRegion** (Exchange Online tiene el mismo aspecto para un error de coincidencia entre estos valores de propiedad).</span><span class="sxs-lookup"><span data-stu-id="c03a2-208">If the Geo code in the database name doesn't match **MailboxRegion** value, the mailbox will be automatically moved to the Geo specified by the **MailboxRegion** value (Exchange Online looks for a mismatch between these property values).</span></span>

### <a name="move-an-existing-cloud-mailbox-to-a-specific-geo"></a><span data-ttu-id="c03a2-209">Mover un buzón de la nube existente a un ubican específico</span><span class="sxs-lookup"><span data-stu-id="c03a2-209">Move an existing cloud mailbox to a specific Geo</span></span>
<span data-ttu-id="c03a2-210">Use los cmdlets **Get-MsolUser** y **Set-MsolUser** en el módulo de AD de Azure para Windows PowerShell para ver o especificar la ubican donde se almacenará el buzón de un usuario.</span><span class="sxs-lookup"><span data-stu-id="c03a2-210">Use the **Get-MsolUser** and **Set-MsolUser** cmdlets in the Azure AD Module for Windows PowerShell to view or specify the Geo where a user's mailbox will be stored.</span></span>

<span data-ttu-id="c03a2-211">Para ver el valor de **PreferredDataLocation** para un usuario, use esta sintaxis en Azure AD PowerShell:</span><span class="sxs-lookup"><span data-stu-id="c03a2-211">To view the **PreferredDataLocation** value for a user, use this syntax in Azure AD PowerShell:</span></span>

```
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

<span data-ttu-id="c03a2-212">Por ejemplo, para ver el valor de **PreferredDataLocation** para el usuario michelle@contoso.onmicrosoft.com, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="c03a2-212">For example, to see the **PreferredDataLocation** value for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

```
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

<span data-ttu-id="c03a2-213">El resultado del comando tiene este aspecto:</span><span class="sxs-lookup"><span data-stu-id="c03a2-213">The output of the command looks like this:</span></span>

```
UserPrincipalName     : michelle@contoso.onmicrosoft.com
PreferredDataLocation : EUR
```

<span data-ttu-id="c03a2-214">Para modificar el valor de **PreferredDataLocation** para un objeto de usuario sólo en la nube, use la siguiente sintaxis en Azure AD PowerShell:</span><span class="sxs-lookup"><span data-stu-id="c03a2-214">To modify the **PreferredDataLocation** value for a cloud-only user object, use the following syntax in Azure AD PowerShell:</span></span>

``` 
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoCode>
```

<span data-ttu-id="c03a2-215">Por ejemplo, para establecer el valor de **PreferredDataLocation** a la Unión Europea (EUR) para el usuario michelle@contoso.onmicrosoft.com, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="c03a2-215">For example, to set the **PreferredDataLocation** value to the European Union (EUR) for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

``` 
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

<span data-ttu-id="c03a2-216">**Notas**:</span><span class="sxs-lookup"><span data-stu-id="c03a2-216">**Notes**:</span></span>

- <span data-ttu-id="c03a2-p120">Como se mencionó anteriormente sincronizada para objetos de usuario de Active Directory local, no puede usar este procedimiento. Debe cambiar el valor de **PreferredDataLocation** mediante AAD conectar. Para obtener más información, vea [sincronización de Azure Active Directory Connect: configurar la ubicación de datos preferido para recursos de Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span><span class="sxs-lookup"><span data-stu-id="c03a2-p120">As mentioned previously for synchronized user objects from on-premises Active Directory, you can't use this procedure. You need to change the **PreferredDataLocation** value using AAD Connect. For more information, see [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span> 

- <span data-ttu-id="c03a2-220">Cuánto tiempo tarda para mover un buzón de correo depende de varios factores:</span><span class="sxs-lookup"><span data-stu-id="c03a2-220">How long it takes to move a mailbox depends on several factors:</span></span>
 
  - <span data-ttu-id="c03a2-221">El tamaño y el tipo de buzón de correo.</span><span class="sxs-lookup"><span data-stu-id="c03a2-221">The size and type of mailbox.</span></span>
 
  - <span data-ttu-id="c03a2-222">El número de buzones que se va a mover.</span><span class="sxs-lookup"><span data-stu-id="c03a2-222">The number of mailboxes being moved.</span></span>
 
  - <span data-ttu-id="c03a2-223">La disponibilidad de recursos de movimiento.</span><span class="sxs-lookup"><span data-stu-id="c03a2-223">The availability of move resources.</span></span>

#### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a><span data-ttu-id="c03a2-224">Move deshabilita los buzones de correo que se encuentran en suspensión por litigio</span><span class="sxs-lookup"><span data-stu-id="c03a2-224">Move disabled mailboxes that are on Litigation Hold</span></span>
<span data-ttu-id="c03a2-p121">Deshabilita los buzones en suspensión por litigio que se conservan para exhibición de documentos electrónicos con fines no se puede mover mediante la modificación de su valor de **PreferredDataLocation** en su estado deshabilitado. Para mover un buzón deshabilitado en juicio:</span><span class="sxs-lookup"><span data-stu-id="c03a2-p121">Disabled mailboxes on Litigation Hold that are preserved for eDiscovery purposes can't be moved by changing their **PreferredDataLocation** value in their disabled state. To move a disabled mailbox on litigation hold:</span></span>

1. <span data-ttu-id="c03a2-227">Asignar temporalmente una licencia para el buzón de correo.</span><span class="sxs-lookup"><span data-stu-id="c03a2-227">Temporarily assign a license to the mailbox.</span></span>

2. <span data-ttu-id="c03a2-228">Cambiar el **PreferredDataLocation**.</span><span class="sxs-lookup"><span data-stu-id="c03a2-228">Change the **PreferredDataLocation**.</span></span>

3. <span data-ttu-id="c03a2-229">Quitar la licencia el buzón de correo después de se ha movido a la ubican seleccionado para volver a colocarla en el estado deshabilitado.</span><span class="sxs-lookup"><span data-stu-id="c03a2-229">Remove the license from the mailbox after it has been moved to the selected Geo to put it back into the disabled state.</span></span>

### <a name="create-new-cloud-mailboxes-in-a-specific-geo"></a><span data-ttu-id="c03a2-230">Crear nuevos buzones de correo en la nube en un ubican específico</span><span class="sxs-lookup"><span data-stu-id="c03a2-230">Create new cloud mailboxes in a specific Geo</span></span> 
<span data-ttu-id="c03a2-231">Para crear un nuevo buzón de correo en un ubican específico, necesita realizar cualquiera de estos pasos:</span><span class="sxs-lookup"><span data-stu-id="c03a2-231">To create a new mailbox in a specific Geo, you need to do either of these steps:</span></span>

- <span data-ttu-id="c03a2-232">Configure el valor de **PreferredDataLocation** como se describe en la anterior sección *antes de* crear el buzón en Exchange Online (por ejemplo, configurando el valor de **PreferredDataLocation** en un usuario antes de asignar una licencia).</span><span class="sxs-lookup"><span data-stu-id="c03a2-232">Configure the **PreferredDataLocation** value as described in the previous section *before* the mailbox is created in Exchange Online (for example, by configuring the **PreferredDataLocation** value on a user before assigning a license).</span></span> 

- <span data-ttu-id="c03a2-233">Asignar una licencia al mismo tiempo, que se establece el valor de **PreferredDataLocation** .</span><span class="sxs-lookup"><span data-stu-id="c03a2-233">Assign a license at the same time you set the **PreferredDataLocation** value.</span></span>

<span data-ttu-id="c03a2-234">Para crear un nuevo solo en nube con licencia usuario (no AAD conectarse sincronizado) en un ubican específica, use la siguiente sintaxis en Azure AD PowerShell:</span><span class="sxs-lookup"><span data-stu-id="c03a2-234">To create a new cloud-only licensed user (not AAD Connect synchronized) in a specific Geo, use the following syntax in Azure AD PowerShell:</span></span>

```
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoCode> 
```
<span data-ttu-id="c03a2-235">En este ejemplo se crea una nueva cuenta de usuario para Elizabeth Brunner con los siguientes valores:</span><span class="sxs-lookup"><span data-stu-id="c03a2-235">This example create a new user account for Elizabeth Brunner with the following values:</span></span>

- <span data-ttu-id="c03a2-236">Nombre principal de usuario: ebrunner@contoso.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="c03a2-236">User principal name: ebrunner@contoso.onmicrosoft.com</span></span>

- <span data-ttu-id="c03a2-237">Nombre: Elizabeth</span><span class="sxs-lookup"><span data-stu-id="c03a2-237">First name: Elizabeth</span></span>

- <span data-ttu-id="c03a2-238">Apellido: Arturo López</span><span class="sxs-lookup"><span data-stu-id="c03a2-238">Last name: Brunner</span></span>

- <span data-ttu-id="c03a2-239">Nombre para mostrar Elizabeth Brunner</span><span class="sxs-lookup"><span data-stu-id="c03a2-239">Display name Elizabeth Brunner</span></span>

- <span data-ttu-id="c03a2-240">Contraseña: genera de forma aleatoria y se muestra en los resultados del comando (debido a que no estamos utilizando el parámetro *Password* )</span><span class="sxs-lookup"><span data-stu-id="c03a2-240">Password: randomly-generated and shown in the results of the command (because we're not using the *Password* parameter)</span></span>

- <span data-ttu-id="c03a2-241">Licencia: contoso:ENTERPRISEPREMIUM (E5)</span><span class="sxs-lookup"><span data-stu-id="c03a2-241">License: contoso:ENTERPRISEPREMIUM (E5)</span></span>

<span data-ttu-id="c03a2-242">Ubicación de 3: Australia (Australia)</span><span class="sxs-lookup"><span data-stu-id="c03a2-242">3- Location: Australia (AUS)</span></span>

```
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

<span data-ttu-id="c03a2-243">Para obtener más información sobre cómo crear nuevas cuentas de usuario y búsqueda de valores de LicenseAssignment en Azure AD PowerShell, vea [crear cuentas de usuario con Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) y [ver licencias y servicios con PowerShell de Office 365](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).</span><span class="sxs-lookup"><span data-stu-id="c03a2-243">For more information about creating new user accounts and finding LicenseAssignment values in Azure AD PowerShell, see [Create user accounts with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) and [View licenses and services with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).</span></span>

> [!NOTE]
> <span data-ttu-id="c03a2-p122">Si usa Exchange PowerShell para habilitar un buzón de correo y necesita el buzón de correo que se creará directamente en el ubican que se especifica en **PreferredDataLocation**, debe usar un cmdlet de Exchange Online como **Enable-Mailbox** o **New-Mailbox** directamente en el servicio de nube. Si usa el cmdlet de Exchange local **Enable-RemoteMailbox** , se creará el buzón de correo en el valor predeterminado ubican.</span><span class="sxs-lookup"><span data-stu-id="c03a2-p122">If you are using Exchange PowerShell to enable a mailbox and need the mailbox to be created directly in the Geo that's specified in **PreferredDataLocation**, you need to use an Exchange Online cmdlet such as **Enable-Mailbox** or **New-Mailbox** directly against the cloud service. If you use the **Enable-RemoteMailbox** on-premises Exchange cmdlet, the mailbox will be created in the default Geo.</span></span>

### <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo"></a><span data-ttu-id="c03a2-246">Incorporado existentes buzones locales en un ubican específico</span><span class="sxs-lookup"><span data-stu-id="c03a2-246">Onboard existing on-premises mailboxes in a specific Geo</span></span>
<span data-ttu-id="c03a2-247">Puede usar las herramientas de incorporación estándar y procesos para migrar un buzón de correo de una organización de Exchange local a Exchange Online, incluido el [panel de la migración en el EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331)y el cmdlet [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) en Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c03a2-247">You can use the standard onboarding tools and processes to migrate a mailbox from an on-premises Exchange organization to Exchange Online, including the [Migration dashboard in the EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331), and the [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) cmdlet in Exchange Online PowerShell.</span></span>

<span data-ttu-id="c03a2-p123">El primer paso es comprobar que existe un objeto de usuario para que cada buzón de correo ser onboarded y compruebe que el valor correcto de **PreferredDataLocation** está configurado en Azure AD. Las herramientas de incorporación respetarán el valor **PreferredDataLocation** y migrarán los buzones de correo directamente a la ubican especificado.</span><span class="sxs-lookup"><span data-stu-id="c03a2-p123">The first step is to verify a user object exists for each mailbox to be onboarded, and verify the correct **PreferredDataLocation** value is configured in Azure AD. The onboarding tools will respect the **PreferredDataLocation** value and will migrate the mailboxes directly to the specified Geo.</span></span>

<span data-ttu-id="c03a2-250">O bien, puede usar los siguientes pasos para los buzones de correo incorporados directamente en un ubican específico mediante el cmdlet [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) en Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c03a2-250">Or, you can use the following steps to onboard mailboxes directly in a specific Geo using the [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) cmdlet in Exchange Online PowerShell.</span></span>

1. <span data-ttu-id="c03a2-p124">Compruebe si que existe el objeto de usuario para que cada buzón de correo ser onboarded y que **PreferredDataLocation** está establecida en el valor deseado de Azure AD. El valor de **PreferredDataLocation** se sincronizarán con el atributo **MailboxRegion** del objeto de usuario correspondiente de correo en Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="c03a2-p124">Verify the user object exists for each mailbox to be onboarded and that **PreferredDataLocation** is set to the desired value in Azure AD. The value of **PreferredDataLocation** will be synchronized to the **MailboxRegion** attribute of the corresponding mail user object in Exchange Online.</span></span>

2. <span data-ttu-id="c03a2-253">Conectarse directamente al satélite específico ubican siguiendo las instrucciones de conexión desde anteriormente en este tema.</span><span class="sxs-lookup"><span data-stu-id="c03a2-253">Connect directly to the specific satellite Geo using the connection instructions from earlier in this topic.</span></span>

3. <span data-ttu-id="c03a2-254">En Exchange Online PowerShell, almacenar las credenciales de administrador local que se utiliza para realizar una migración de buzones de correo en una variable, ejecute el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="c03a2-254">In Exchange Online PowerShell, store the on-premises administrator credentials that's used to perform a mailbox migration in a variable by running the following command:</span></span>

    ```
    $RC = Get-Credential
    ```

4. <span data-ttu-id="c03a2-255">En Exchange Online PowerShell, cree un nuevo **New-MoveRequest** similar al siguiente ejemplo:</span><span class="sxs-lookup"><span data-stu-id="c03a2-255">In Exchange Online PowerShell, create a new **New-MoveRequest** similar to the following example:</span></span> 

    ```
    New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
    ```

5. <span data-ttu-id="c03a2-256">Repita el paso 4 # para cada buzón de correo que necesita para migrar desde Exchange local al satélite ubican está actualmente conectado.</span><span class="sxs-lookup"><span data-stu-id="c03a2-256">Repeat step #4 for every mailbox you need to migrate from on-premises Exchange to the satellite Geo you are currently connected to.</span></span>

6. <span data-ttu-id="c03a2-257">Si necesita migrar buzones de correo adicionales a un satélite diferente ubican, repita los pasos del 2 al 4 para cada satélite específico ubican.</span><span class="sxs-lookup"><span data-stu-id="c03a2-257">If you need to migrate additional mailboxes to a different satellite Geo, repeat steps 2 through 4 for each specific satellite Geo.</span></span>

### <a name="multi-geo-reporting"></a><span data-ttu-id="c03a2-258">Multi-ubican informes</span><span class="sxs-lookup"><span data-stu-id="c03a2-258">Multi-Geo Reporting</span></span>
<span data-ttu-id="c03a2-p125">**Multi-ubican los informes de uso** en el centro de administración de Office 365 muestra el recuento de usuarios por ubican. El informe muestra la distribución de usuario para el mes actual y proporciona datos históricos de los últimos 6 meses.</span><span class="sxs-lookup"><span data-stu-id="c03a2-p125">**Multi-Geo Usage Reports** in the Office 365 admin center displays the user count by Geo. The report displays user distribution for the current month and provides historical data for the past 6 months.</span></span>
 
