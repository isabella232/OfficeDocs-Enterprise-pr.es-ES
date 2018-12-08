---
title: Capacidades de Multi-Geo en Exchange Online
ms.author: chrisda
author: chrisda
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Normal
ms.assetid: ''
description: Expanda su información de presencia de Office 365 a varias regiones geográficas con multi-ubican las capacidades de Exchange Online.
ms.openlocfilehash: 6acd2ffab1f35b74d06d6ab5f7bfcbf70f88f8b4
ms.sourcegitcommit: 03bb9edd52b1b7cd49791baf90645828b89b32b5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2018
ms.locfileid: "27200743"
---
# <a name="multi-geo-capabilities-in-exchange-online"></a><span data-ttu-id="28701-103">Capacidades de Multi-Geo en Exchange Online</span><span class="sxs-lookup"><span data-stu-id="28701-103">Multi-Geo Capabilities in Exchange Online</span></span>

<span data-ttu-id="28701-p101">Capacidades de Multi-ubican en Office 365 habilitar un inquilino único abarcar varias ubicaciones geográficas. Al multi-ubican está habilitada, los clientes pueden seleccionar la ubicación del contenido del buzón Exchange Online (datos en reposo) por usuario.</span><span class="sxs-lookup"><span data-stu-id="28701-p101">Multi-Geo Capabilities in Office 365 enable a single tenant to span multiple geographic locations. When multi-geo is enabled, customers can select the location of Exchange Online mailbox content (data at rest) on a per-user basis.</span></span>

<span data-ttu-id="28701-p102">La ubicación inicial de inquilinos (denominada la ubicación central) se determina en función de su dirección de facturación. Cuando está habilitada la multi-ubican, puede poner los buzones de correo en ubicaciones de satélite adicionales por:</span><span class="sxs-lookup"><span data-stu-id="28701-p102">Your initial tenant location (referred to as the central location) is determined based on your billing address. When multi-geo is enabled, you can place mailboxes in additional satellite locations by:</span></span>

- <span data-ttu-id="28701-108">Creación de un nuevo buzón de Exchange Online directamente en una ubicación de satélite.</span><span class="sxs-lookup"><span data-stu-id="28701-108">Creating a new Exchange Online mailbox directly in a satellite location.</span></span>

- <span data-ttu-id="28701-109">Mover un buzón de Exchange Online existente en una ubicación de satélite.</span><span class="sxs-lookup"><span data-stu-id="28701-109">Moving an existing Exchange Online mailbox into a satellite location.</span></span>

- <span data-ttu-id="28701-110">Incorporación de un buzón de correo desde una organización de Exchange local directamente en una ubicación de satélite.</span><span class="sxs-lookup"><span data-stu-id="28701-110">Onboarding a mailbox from an on-premises Exchange organization directly into a satellite location.</span></span>

<span data-ttu-id="28701-111">Las siguientes ubicaciones ubican están disponibles para su uso en una configuración de Multi-Geo:</span><span class="sxs-lookup"><span data-stu-id="28701-111">The following geo locations are available for use in a Multi-Geo configuration:</span></span>

- <span data-ttu-id="28701-112">Asia Pacífico</span><span class="sxs-lookup"><span data-stu-id="28701-112">Asia Pacific</span></span>

- <span data-ttu-id="28701-113">Australia</span><span class="sxs-lookup"><span data-stu-id="28701-113">Australia</span></span>

- <span data-ttu-id="28701-114">Canadá</span><span class="sxs-lookup"><span data-stu-id="28701-114">Canada</span></span>

- <span data-ttu-id="28701-115">Unión Europea</span><span class="sxs-lookup"><span data-stu-id="28701-115">European Union</span></span>

- <span data-ttu-id="28701-116">Francia</span><span class="sxs-lookup"><span data-stu-id="28701-116">France</span></span>

- <span data-ttu-id="28701-117">India</span><span class="sxs-lookup"><span data-stu-id="28701-117">India</span></span>

- <span data-ttu-id="28701-118">Japón</span><span class="sxs-lookup"><span data-stu-id="28701-118">Japan</span></span>

- <span data-ttu-id="28701-119">Corea</span><span class="sxs-lookup"><span data-stu-id="28701-119">Korea</span></span>

- <span data-ttu-id="28701-120">Reino Unido</span><span class="sxs-lookup"><span data-stu-id="28701-120">United Kingdom</span></span>

- <span data-ttu-id="28701-121">Estados Unidos</span><span class="sxs-lookup"><span data-stu-id="28701-121">United States</span></span>

## <a name="prerequisite-configuration"></a><span data-ttu-id="28701-122">Configuración de requisitos previos</span><span class="sxs-lookup"><span data-stu-id="28701-122">Prerequisite configuration</span></span>
<span data-ttu-id="28701-p103">Antes de empezar a usar las capacidades de Multi-Geo en Exchange Online, Microsoft tiene que configurar a su inquilino de Exchange Online para ofrecer compatibilidad con multi-ubican. Este proceso de configuración de una sola vez se desencadena después de haber ordenado que Office 365 Multi-Geo y las licencias se muestran en el inquilino. Este proceso de configuración única normalmente debe tardar menos de 30 días en completarse. Para solicitar Office 365 Multi-ubican, póngase en contacto con su representante de Microsoft. Para obtener más información, consulte https://aka.ms/Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="28701-p103">Before you can start using Multi-Geo capabilities in Exchange Online, Microsoft needs to configure your Exchange Online tenant for multi-geo support. This one-time configuration process is triggered after you order Office 365 Multi-Geo and the licenses show up in your tenant. This one-time configuration process should typically take less than 30 days to complete. To order Office 365 Multi-Geo, contact your Microsoft representative. For more information, see https://aka.ms/Multi-Geo.</span></span>

<span data-ttu-id="28701-p104">Recibirá notificaciones en el [Centro de mensajes de Office 365](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093) cuando haya finalizado la configuración. Configuración se activa automáticamente una vez que las licencias de multi-ubican aparezcan en el inquilino.</span><span class="sxs-lookup"><span data-stu-id="28701-p104">You'll receive notifications in the [Office 365 message center](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093) when your configuration has completed. Configuration is automatically triggered once your multi-geo licenses show up in your tenant.</span></span>

## <a name="mailbox-placement-and-moves"></a><span data-ttu-id="28701-130">Se desplaza y colocación de buzón de correo</span><span class="sxs-lookup"><span data-stu-id="28701-130">Mailbox placement and moves</span></span>
<span data-ttu-id="28701-131">Después de que Microsoft lleva a cabo los pasos de configuración de multi-ubican necesario como requisito previo, Exchange Online respeta el atributo **PreferredDataLocation** en objetos de usuario en Azure AD.</span><span class="sxs-lookup"><span data-stu-id="28701-131">After Microsoft completes the prerequisite multi-geo configuration steps, Exchange Online will honor the **PreferredDataLocation** attribute on user objects in Azure AD.</span></span>

<span data-ttu-id="28701-p105">Exchange Online se sincroniza la propiedad **PreferredDataLocation** de Azure AD en la propiedad **MailboxRegion** en el servicio de directorio Exchange Online. El valor de **MailboxRegion** determina el ubican donde se colocará los buzones de usuario y cualquier archivo asociado. No es posible configurar los buzones principales de buzón de correo y de archivo de un usuario para residen en ubican diferentes ubicaciones. Se puede configurar una única ubicación ubican por objeto de usuario.</span><span class="sxs-lookup"><span data-stu-id="28701-p105">Exchange Online synchronizes the **PreferredDataLocation** property from Azure AD into the **MailboxRegion** property in the Exchange Online directory service. The value of **MailboxRegion** determines the Geo where user mailboxes and any associated archive mailboxes will be placed. It is not possible to configure a user's primary mailbox and archive mailboxes to reside in different geo locations. Only one geo location may be configured per user object.</span></span>

- <span data-ttu-id="28701-136">Cuando **PreferredDataLocation** está configurado en un usuario con un buzón existente, el buzón de correo se coloque en una cola de reubicación y se mueve automáticamente a la ubicación geográfica especificada.</span><span class="sxs-lookup"><span data-stu-id="28701-136">When **PreferredDataLocation** is configured on a user with an existing mailbox, the mailbox will be put into a relocation queue and automatically moved to the specified geo location.</span></span> 

- <span data-ttu-id="28701-137">Cuando **PreferredDataLocation** está configurado en un usuario sin un buzón existente, se aprovisionará el buzón de correo en la ubicación geográfica especificada.</span><span class="sxs-lookup"><span data-stu-id="28701-137">When **PreferredDataLocation** is configured on a user without an existing mailbox, the mailbox will be provisioned into the specified geo location.</span></span> 

- <span data-ttu-id="28701-138">Cuando no se especifica **PreferredDataLocation** en un usuario, el buzón de correo se colocará en la ubicación central.</span><span class="sxs-lookup"><span data-stu-id="28701-138">When **PreferredDataLocation** is not specified on a user, the mailbox will be placed in the central location.</span></span>

- <span data-ttu-id="28701-139">Si el código de **PreferredDataLocation** es incorrecto (por ejemplo, un tipo de NAN en lugar del nombre), el buzón de correo se colocará en la ubicación central.</span><span class="sxs-lookup"><span data-stu-id="28701-139">If the **PreferredDataLocation** code is incorrect (e.g. a type of NAN instead of NAM), the mailbox will be placed in the central location.</span></span>

<span data-ttu-id="28701-p106">**Nota**: multi-ubican capacidades y Skype para profesionales reuniones en línea hospedado regional ambos usan la propiedad **PreferredDataLocation** en objetos de usuario para localizan los servicios. Si configura los valores de **PreferredDataLocation** en objetos de usuario para las reuniones de ámbito regional hospedados, el buzón de correo para esos usuarios se moverá automáticamente a la ubicación especificada ubican después de habilita multi-ubican en el inquilino de Office 365.</span><span class="sxs-lookup"><span data-stu-id="28701-p106">**Note**: multi-geo capabilities and Skype for Business Online regionally hosted meetings both use the **PreferredDataLocation** property on user objects to locate services. If you configure **PreferredDataLocation** values on user objects for regionally hosted meetings, the mailbox for those users will be automatically moved to the specified geo location after multi-geo is enabled on the Office 365 tenant.</span></span>

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a><span data-ttu-id="28701-142">Limitaciones de características para Multi-Geo en Exchange Online</span><span class="sxs-lookup"><span data-stu-id="28701-142">Feature limitations for Multi-Geo in Exchange Online</span></span>
1. <span data-ttu-id="28701-p107">Sólo buzones de usuario, buzones de recursos (buzones de correo de sala y equipamiento) y buzones compartidos admiten características de multi-ubican. Públicas buzones de carpetas y grupos de Office 365 permanecen en la ubicación central.</span><span class="sxs-lookup"><span data-stu-id="28701-p107">Only user mailboxes, resource mailboxes (room and equipment mailboxes), and shared mailboxes support multi-geo features. Public Folder Mailboxes and Office 365 Groups remain in the central location.</span></span>
 
2. <span data-ttu-id="28701-p108">Seguridad y cumplimiento de normas características (por ejemplo, auditoría y exhibición de documentos electrónicos) que están disponibles en el centro de administración de Exchange (EAC) no están disponibles en las organizaciones multi-ubican. En su lugar, debe usar el [Centro de cumplimiento y seguridad de Office 365](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) para configurar las características de seguridad y cumplimiento de normas.</span><span class="sxs-lookup"><span data-stu-id="28701-p108">Security and compliance features (for example, auditing and eDiscovery) that are available in the Exchange admin center (EAC) aren't available in multi-geo organizations. Instead, you need to use the [Office 365 Security & Compliance Center](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) to configure security and compliance features.</span></span>

3. <span data-ttu-id="28701-p109">Outlook para los usuarios de Mac puede experimentar una pérdida temporal de acceso a su carpeta de archivo en línea mientras su buzón se mueve a una nueva ubicación geográfica. Esta condición se produce cuando del usuario principal y buzones de archivo se encuentran en ubicaciones diferentes ubican, debido a que los movimientos de buzones entre ubican pueden completar en momentos diferentes.</span><span class="sxs-lookup"><span data-stu-id="28701-p109">Outlook for Mac users may experience a temporary loss of access to their Online Archive folder while you move their mailbox to a new geo location. This condition occurs when the user's the primary and archive mailboxes are in different geo locations, because cross-Geo mailbox moves may complete at different times.</span></span>

4. <span data-ttu-id="28701-p110">Los usuarios no pueden compartir *las carpetas de buzón de correo* en las ubicaciones de ubican en Outlook en el web (anteriormente conocido como Outlook Web App u OWA). Por ejemplo, un usuario en la Unión Europea no puede usar Outlook en la web para abrir una carpeta compartida en un buzón que se encuentra en los Estados Unidos. Sin embargo, Outlook en los usuarios de Web puede abrir *otros buzones de correo* en diferentes zonas mediante el uso de una ventana del explorador independiente como se describe en [Abra el buzón de otra persona en una ventana del explorador independiente en Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).</span><span class="sxs-lookup"><span data-stu-id="28701-p110">Users can't share *mailbox folders* across geo locations in Outlook on the web (formerly known as Outlook Web App or OWA). For example, a user in the European Union can't use Outlook on the web to open a shared folder in a mailbox that's located in the United States. However, Outlook on the Web users can open *other mailboxes* in different Geos by using a separate browser window as described in [Open another person’s mailbox in a separate browser window in Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).</span></span>

    <span data-ttu-id="28701-152">**Nota**: compartir una carpeta buzón entre geo se admite en Outlook en Windows.</span><span class="sxs-lookup"><span data-stu-id="28701-152">**Note**: Cross-geo mailbox folder sharing is supported in Outlook on Windows.</span></span>

## <a name="administration"></a><span data-ttu-id="28701-153">Administración</span><span class="sxs-lookup"><span data-stu-id="28701-153">Administration</span></span> 
<span data-ttu-id="28701-p111">PowerShell remoto es necesario para ver y configurar las propiedades de múltiples ubican en el entorno de Office 365. Para obtener información sobre los distintos módulos de PowerShell que se utiliza para Office 365, vea [administración de Office 365 y Exchange Online con Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6).</span><span class="sxs-lookup"><span data-stu-id="28701-p111">Remote PowerShell is required to view and configure multi geo properties in your Office 365 environment. For information on various PowerShell modules used to administer Office 365, see [Managing Office 365 and Exchange Online with Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6).</span></span>

- <span data-ttu-id="28701-p112">Necesitará el [Módulo de PowerShell de Microsoft Azure Active Directory](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 o más adelante en v1.x para ver la propiedad **PreferredDataLocation** en objetos de usuario. Objetos de usuario sincronizados a través de AAD conectar en AAD no pueden tener su valor **PreferredDataLocation** modificar directamente a través de PowerShell AAD. Objetos de usuario solo en nube pueden modificarse a través de PowerShell AAD. Para conectarse a AD de Windows Azure PowerShell, vea [Connect to Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span><span class="sxs-lookup"><span data-stu-id="28701-p112">You need the [Microsoft Azure Active Directory PowerShell Module](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 or later in v1.x to see the **PreferredDataLocation** property on user objects. User objects synchronized via AAD Connect into AAD cannot have their **PreferredDataLocation** value directly modified via AAD PowerShell. Cloud-only user objects can be modified via AAD PowerShell. To connect to Azure AD PowerShell, see [Connect to Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span></span> 

- <span data-ttu-id="28701-160">Para conectarse a Exchange Online PowerShell, vea [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span><span class="sxs-lookup"><span data-stu-id="28701-160">To connect to Exchange Online PowerShell, see [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span></span> 

### <a name="connect-directly-to-a-specific-geo-using-exchange-online-powershell"></a><span data-ttu-id="28701-161">Conectar directamente a un ubican específica con Exchange Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="28701-161">Connect directly to a specific Geo using Exchange Online PowerShell</span></span>
<span data-ttu-id="28701-p113">Normalmente, Exchange Online PowerShell se conectará a la ubicación predeterminada de geo. Sin embargo, también puede conectarse directamente a ubicaciones ubican no predeterminado. Debido a las mejoras de rendimiento, se recomienda conectarse directamente a la ubicación no predeterminada ubican al administrar sólo los usuarios de esa ubicación geográfica.</span><span class="sxs-lookup"><span data-stu-id="28701-p113">Typically, Exchange Online PowerShell will connect to the default geo location. But, you can also connect directly to non-default geo locations. Because of performance improvements, we recommend connecting directly to the non-default geo location when you only manage users in that geo location.</span></span>

<span data-ttu-id="28701-p114">Para conectarse a un ubican específica, el parámetro *ConnectionUri* es diferente de las instrucciones de conexión regular. El resto de los comandos y los valores son los mismos. Los pasos son:</span><span class="sxs-lookup"><span data-stu-id="28701-p114">To connect to a specific Geo, the *ConnectionUri* parameter is different than the regular connection instructions. The rest of the commands and values are the same. The steps are:</span></span>

1. <span data-ttu-id="28701-168">En el equipo local, abra Windows PowerShell y ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="28701-168">On your local computer, open Windows PowerShell and run the following command:</span></span>
    
    ```
    $UserCredential = Get-Credential
    ```
   <span data-ttu-id="28701-169">En el cuadro de diálogo **Solicitud de credenciales de Windows PowerShell** , escriba su trabajo o escuela cuenta y su contraseña y, a continuación, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="28701-169">In the **Windows PowerShell Credential Request** dialog box, type your work or school account and password, and then click **OK**.</span></span>
    
2. <span data-ttu-id="28701-p115">Reemplace `<emailaddress>` con la dirección de correo electrónico de **cualquier** buzón de correo en la ubicación de destino geo y ejecute el comando siguiente. Los permisos en el buzón de correo y la relación con sus credenciales en el paso 1 no son un factor; la dirección de correo electrónico simplemente indica a Exchange Online dónde debe conectarse.</span><span class="sxs-lookup"><span data-stu-id="28701-p115">Replace `<emailaddress>` with the email address of **any** mailbox in the target geo location and run the following command. Your permissions on the mailbox and the relationship to your credentials in Step 1 are not a factor; the email address simply tells Exchange Online where to connect.</span></span>
  
   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   <span data-ttu-id="28701-172">Por ejemplo, si olga@contoso.onmicrosoft.com es la dirección de correo electrónico de un buzón de correo válido en el Geo va a conectar, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="28701-172">For example, if olga@contoso.onmicrosoft.com is the email address of a valid mailbox in the Geo you want to connect, run the following command:</span></span>

   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```
3. <span data-ttu-id="28701-173">Ejecute el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="28701-173">Run the following command:</span></span>
    
    ```
    Import-PSSession $Session
    ```

### <a name="azure-ad-connect-version-requirements"></a><span data-ttu-id="28701-174">Requisitos de versión de Azure Connect de AD</span><span class="sxs-lookup"><span data-stu-id="28701-174">Azure AD Connect version requirements</span></span>
<span data-ttu-id="28701-p116">Conectar AAD versión 1.1.524.0 o posterior es el único método admitido para establecer la propiedad **PreferredDataLocation** en los objetos de usuario que se sincronizan desde Active Directory local. Objetos de usuario sincronizados a través de AAD conectar en AAD no pueden tener su valor **PreferredDataLocation** modificar directamente a través de PowerShell AAD. Objetos de usuario solo en nube pueden modificarse a través de PowerShell AAD. Para obtener instrucciones detalladas, consulte [sincronización de Azure Active Directory Connect: configurar la ubicación de datos preferido para recursos de Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span><span class="sxs-lookup"><span data-stu-id="28701-p116">AAD Connect version 1.1.524.0 or later is the only supported method for setting the **PreferredDataLocation** property on user objects that are synchronized from on-premises Active Directory. User objects synchronized via AAD Connect into AAD cannot have their **PreferredDataLocation** value directly modified via AAD PowerShell. Cloud-only user objects can be modified via AAD PowerShell. For detailed instructions, see [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

### <a name="geo-codes"></a><span data-ttu-id="28701-179">Códigos de geo</span><span class="sxs-lookup"><span data-stu-id="28701-179">Geo Codes</span></span>
<span data-ttu-id="28701-p117">Use los códigos de tres letras para especificar el ubican en la propiedad **PreferredDataLocation** . En la siguiente tabla se enumera los códigos de las zonas disponibles:</span><span class="sxs-lookup"><span data-stu-id="28701-p117">You use three-letter codes to specify the Geo in the **PreferredDataLocation** property. The following table lists the codes for the available Geos:</span></span>

|<span data-ttu-id="28701-182">Geo</span><span class="sxs-lookup"><span data-stu-id="28701-182">Geo</span></span> |<span data-ttu-id="28701-183">Código</span><span class="sxs-lookup"><span data-stu-id="28701-183">Code</span></span> |
|---------|---------|
|<span data-ttu-id="28701-184">Asia Pacífico</span><span class="sxs-lookup"><span data-stu-id="28701-184">Asia/Pacific</span></span> |<span data-ttu-id="28701-185">APC</span><span class="sxs-lookup"><span data-stu-id="28701-185">APC</span></span> |
|<span data-ttu-id="28701-186">Australia</span><span class="sxs-lookup"><span data-stu-id="28701-186">Australia</span></span> |<span data-ttu-id="28701-187">AUS</span><span class="sxs-lookup"><span data-stu-id="28701-187">AUS</span></span> |
|<span data-ttu-id="28701-188">Canadá</span><span class="sxs-lookup"><span data-stu-id="28701-188">Canada</span></span> |<span data-ttu-id="28701-189">CAN</span><span class="sxs-lookup"><span data-stu-id="28701-189">CAN</span></span> |
|<span data-ttu-id="28701-190">Unión Europea</span><span class="sxs-lookup"><span data-stu-id="28701-190">European Union</span></span> |<span data-ttu-id="28701-191">EUR</span><span class="sxs-lookup"><span data-stu-id="28701-191">EUR</span></span> |
|<span data-ttu-id="28701-192">Francia</span><span class="sxs-lookup"><span data-stu-id="28701-192">France</span></span> |<span data-ttu-id="28701-193">FRA</span><span class="sxs-lookup"><span data-stu-id="28701-193">FRA</span></span>|
|<span data-ttu-id="28701-194">India</span><span class="sxs-lookup"><span data-stu-id="28701-194">India</span></span> |<span data-ttu-id="28701-195">IND</span><span class="sxs-lookup"><span data-stu-id="28701-195">IND</span></span> |
|<span data-ttu-id="28701-196">Japón</span><span class="sxs-lookup"><span data-stu-id="28701-196">Japan</span></span> |<span data-ttu-id="28701-197">JPN</span><span class="sxs-lookup"><span data-stu-id="28701-197">JPN</span></span> |
|<span data-ttu-id="28701-198">Corea</span><span class="sxs-lookup"><span data-stu-id="28701-198">Korea</span></span> |<span data-ttu-id="28701-199">KOR</span><span class="sxs-lookup"><span data-stu-id="28701-199">KOR</span></span> |
|<span data-ttu-id="28701-200">Reino Unido</span><span class="sxs-lookup"><span data-stu-id="28701-200">United Kingdom</span></span> |<span data-ttu-id="28701-201">GBR</span><span class="sxs-lookup"><span data-stu-id="28701-201">GBR</span></span> |
|<span data-ttu-id="28701-202">Estados Unidos</span><span class="sxs-lookup"><span data-stu-id="28701-202">United States</span></span> |<span data-ttu-id="28701-203">NAM</span><span class="sxs-lookup"><span data-stu-id="28701-203">NAM</span></span> |

<span data-ttu-id="28701-p118">**Nota**: las propiedades **PreferredDataLocation** y **MailboxRegion** son cadenas con ninguna comprobación de errores. Si escribe un valor no válido (por ejemplo, NAN) el buzón de correo se colocará en el valor predeterminado ubican.</span><span class="sxs-lookup"><span data-stu-id="28701-p118">**Note**: The **PreferredDataLocation** and **MailboxRegion** properties are strings with no error checking. If you enter an invalid value (for example, NAN) the mailbox will be placed in the default Geo.</span></span>

### <a name="view-the-available-geos-that-are-configured-in-your-exchange-online-organization"></a><span data-ttu-id="28701-206">Ver las zonas disponibles que están configurados en la organización de Exchange Online</span><span class="sxs-lookup"><span data-stu-id="28701-206">View the available Geos that are configured in your Exchange Online organization</span></span>
<span data-ttu-id="28701-207">Para ver la lista de zonas configuradas en la organización de Exchange Online, ejecute el siguiente comando en Exchange Online PowerShell:</span><span class="sxs-lookup"><span data-stu-id="28701-207">To see the list of configured Geos in your Exchange Online organization, run the following command in Exchange Online PowerShell:</span></span>

```
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table
```

<span data-ttu-id="28701-208">El resultado del comando tiene este aspecto:</span><span class="sxs-lookup"><span data-stu-id="28701-208">The output of the command looks like this:</span></span>

```
APC
AUS
CAN
EUR
FRA
GBR
JPN
KOR
NAM
```

### <a name="view-the-default-geo-for-your-exchange-online-organization"></a><span data-ttu-id="28701-209">Ver el valor predeterminado Geo para la organización de Exchange Online</span><span class="sxs-lookup"><span data-stu-id="28701-209">View the default Geo for your Exchange Online organization</span></span>
<span data-ttu-id="28701-210">Para ver la ubican predeterminada de la organización de Exchange Online, ejecute el siguiente comando en Exchange Online PowerShell:</span><span class="sxs-lookup"><span data-stu-id="28701-210">To view the default geo of your Exchange Online organization, run the following command in Exchange Online PowerShell:</span></span>

```
Get-OrganizationConfig | Select DefaultMailboxRegion
```

<span data-ttu-id="28701-211">El resultado del comando tiene este aspecto:</span><span class="sxs-lookup"><span data-stu-id="28701-211">The output of the command looks like this:</span></span>

```
DefaultMailboxRegion
--------------------
NAM
```


### <a name="find-the-geo-location-of-a-mailbox"></a><span data-ttu-id="28701-212">Busque la ubicación geográfica de un buzón de correo</span><span class="sxs-lookup"><span data-stu-id="28701-212">Find the Geo location of a mailbox</span></span>
<span data-ttu-id="28701-213">El cmdlet **Get-Mailbox** en Exchange Online PowerShell muestra el siguiente multi-ubican relacionados con las propiedades de buzones de correo:</span><span class="sxs-lookup"><span data-stu-id="28701-213">The **Get-Mailbox** cmdlet in Exchange Online PowerShell displays the following multi-geo related properties on mailboxes:</span></span>

- <span data-ttu-id="28701-p119">**Base de datos**: el primero 3 letras del nombre de base de datos se corresponden con el código ubican, que indica donde se encuentra actualmente el buzón de correo. Propiedad debe utilizarse para buzones de archivo en línea la **ArchiveDatabase** .</span><span class="sxs-lookup"><span data-stu-id="28701-p119">**Database**: The first 3 letters of the database name correspond to the Geo code, which tells you where the mailbox is currently located. For Online Archive Mailboxes the **ArchiveDatabase** property should be used.</span></span>

- <span data-ttu-id="28701-216">**MailboxRegion**: especifica el código de ubicación geográfica que se ha establecido por el administrador (sincronizado desde **PreferredDataLocation** en Azure AD).</span><span class="sxs-lookup"><span data-stu-id="28701-216">**MailboxRegion**: Specifies the geo location code that was set by the admin (synchronized from **PreferredDataLocation** in Azure AD).</span></span>

- <span data-ttu-id="28701-217">**MailboxRegionLastUpdateTime**: indica cuándo se actualizó por última vez las MailboxRegion (automático o manual).</span><span class="sxs-lookup"><span data-stu-id="28701-217">**MailboxRegionLastUpdateTime**: Indicates when MailboxRegion was last updated (either automatically or manually).</span></span>

<span data-ttu-id="28701-218">Para ver estas propiedades para un buzón de correo, use la siguiente sintaxis:</span><span class="sxs-lookup"><span data-stu-id="28701-218">To see these properties for a mailbox, use the following syntax:</span></span>

```
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

<span data-ttu-id="28701-219">Por ejemplo, para ver la información de Geo para el buzón de correo chris@contoso.onmicrosoft.com, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="28701-219">For example, to see the Geo information for the mailbox chris@contoso.onmicrosoft.com, run the following command:</span></span>

```
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

<span data-ttu-id="28701-220">El resultado del comando tiene este aspecto:</span><span class="sxs-lookup"><span data-stu-id="28701-220">The output of the command looks like this:</span></span>

```
Database                    : EURPR03DG077-db007 
MailboxRegion               : EUR 
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM 
```

> <span data-ttu-id="28701-221">**Nota:** Si el código de ubicación geográfica en el nombre de la base de datos no coincide con el valor de **MailboxRegion** , el buzón de correo será automáticamente pueden colocarse en una cola de reubicación y se mueve a la ubicación geográfica especificada por el valor de **MailboxRegion** (Exchange Online busca un Error de coincidencia entre estos valores de propiedad).</span><span class="sxs-lookup"><span data-stu-id="28701-221">**Note:** If the geo location code in the database name doesn't match **MailboxRegion** value, the mailbox will be automatically be put into a relocation queue and moved to the geo location specified by the **MailboxRegion** value (Exchange Online looks for a mismatch between these property values).</span></span>

### <a name="move-an-existing-cloud-only-mailbox-to-a-specific-geo"></a><span data-ttu-id="28701-222">Mover un buzón de nube existente a un ubican específico</span><span class="sxs-lookup"><span data-stu-id="28701-222">Move an existing cloud-only mailbox to a specific Geo</span></span>
<span data-ttu-id="28701-p120">Un usuario sólo en la nube es un usuario no sincronizar en el inquilino a través de AAD conectar. Este usuario se creó directamente en Azure AD. Use los cmdlets **Get-MsolUser** y **Set-MsolUser** en el módulo de AD de Azure para Windows PowerShell para ver o especificar la ubican donde se almacenará el buzón de un usuario sólo en la nube.</span><span class="sxs-lookup"><span data-stu-id="28701-p120">A cloud-only user is a user not syncrhonized to the tenant via AAD Connect. This user was created directly in Azure AD. Use the **Get-MsolUser** and **Set-MsolUser** cmdlets in the Azure AD Module for Windows PowerShell to view or specify the Geo where a cloud-only user's mailbox will be stored.</span></span>

<span data-ttu-id="28701-226">Para ver el valor de **PreferredDataLocation** para un usuario, use esta sintaxis en Azure AD PowerShell:</span><span class="sxs-lookup"><span data-stu-id="28701-226">To view the **PreferredDataLocation** value for a user, use this syntax in Azure AD PowerShell:</span></span>

```
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

<span data-ttu-id="28701-227">Por ejemplo, para ver el valor de **PreferredDataLocation** para el usuario michelle@contoso.onmicrosoft.com, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="28701-227">For example, to see the **PreferredDataLocation** value for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

```
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

<span data-ttu-id="28701-228">El resultado del comando tiene este aspecto:</span><span class="sxs-lookup"><span data-stu-id="28701-228">The output of the command looks like this:</span></span>

```
UserPrincipalName     : michelle@contoso.onmicrosoft.com
PreferredDataLocation : EUR
```

<span data-ttu-id="28701-229">Para modificar el valor de **PreferredDataLocation** para un objeto de usuario sólo en la nube, use la siguiente sintaxis en Azure AD PowerShell:</span><span class="sxs-lookup"><span data-stu-id="28701-229">To modify the **PreferredDataLocation** value for a cloud-only user object, use the following syntax in Azure AD PowerShell:</span></span>

``` 
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoCode>
```

<span data-ttu-id="28701-230">Por ejemplo, para establecer el valor de **PreferredDataLocation** en el ubican Unión Europea (EUR) para el usuario michelle@contoso.onmicrosoft.com, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="28701-230">For example, to set the **PreferredDataLocation** value to the European Union (EUR) geo for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

``` 
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

<span data-ttu-id="28701-231">**Notas**:</span><span class="sxs-lookup"><span data-stu-id="28701-231">**Notes**:</span></span>

- <span data-ttu-id="28701-p121">Como se ha mencionado anteriormente no puede usar este procedimiento sincronizada para objetos de usuario de Active Directory local. Debe cambiar el valor de **PreferredDataLocation** mediante AAD conectar. Para obtener más información, vea [sincronización de Azure Active Directory Connect: configurar la ubicación de datos preferido para recursos de Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span><span class="sxs-lookup"><span data-stu-id="28701-p121">As mentioned previously you cannot use this procedure for synchronized user objects from on-premises Active Directory. You need to change the **PreferredDataLocation** value using AAD Connect. For more information, see [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span> 

- <span data-ttu-id="28701-235">Cuánto tiempo tarda para reubicar un mailboxfrom que su ubican actual a la nueva ubicación deseada ubican depende de varios factores:</span><span class="sxs-lookup"><span data-stu-id="28701-235">How long it takes to relocate a mailboxfrom its current geo to the new desired geo location depends on several factors:</span></span>
 
  - <span data-ttu-id="28701-236">El tamaño y el tipo de buzón de correo.</span><span class="sxs-lookup"><span data-stu-id="28701-236">The size and type of mailbox.</span></span>
 
  - <span data-ttu-id="28701-237">El número de buzones que se va a mover.</span><span class="sxs-lookup"><span data-stu-id="28701-237">The number of mailboxes being moved.</span></span>
 
  - <span data-ttu-id="28701-238">La disponibilidad de recursos de movimiento.</span><span class="sxs-lookup"><span data-stu-id="28701-238">The availability of move resources.</span></span>

#### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a><span data-ttu-id="28701-239">Move deshabilita los buzones de correo que se encuentran en suspensión por litigio</span><span class="sxs-lookup"><span data-stu-id="28701-239">Move disabled mailboxes that are on Litigation Hold</span></span>
<span data-ttu-id="28701-p122">Deshabilita los buzones en suspensión por litigio que se conservan para exhibición de documentos electrónicos con fines no se puede mover mediante la modificación de su valor de **PreferredDataLocation** en su estado deshabilitado. Para mover un buzón deshabilitado en juicio:</span><span class="sxs-lookup"><span data-stu-id="28701-p122">Disabled mailboxes on Litigation Hold that are preserved for eDiscovery purposes cannot be moved by changing their **PreferredDataLocation** value in their disabled state. To move a disabled mailbox on litigation hold:</span></span>

1. <span data-ttu-id="28701-242">Asignar temporalmente una licencia para el buzón de correo.</span><span class="sxs-lookup"><span data-stu-id="28701-242">Temporarily assign a license to the mailbox.</span></span>

2. <span data-ttu-id="28701-243">Cambiar el **PreferredDataLocation**.</span><span class="sxs-lookup"><span data-stu-id="28701-243">Change the **PreferredDataLocation**.</span></span>

3. <span data-ttu-id="28701-244">Quitar la licencia desde el buzón de correo después de que se ha movido a la ubicación geográfica seleccionada para volver a colocarla en el estado deshabilitado.</span><span class="sxs-lookup"><span data-stu-id="28701-244">Remove the license from the mailbox after it has been moved to the selected geo location to put it back into the disabled state.</span></span>

### <a name="create-new-cloud-mailboxes-in-a-specific-geo"></a><span data-ttu-id="28701-245">Crear nuevos buzones de correo en la nube en un ubican específico</span><span class="sxs-lookup"><span data-stu-id="28701-245">Create new cloud mailboxes in a specific Geo</span></span> 
<span data-ttu-id="28701-246">Para crear un nuevo buzón de correo en una ubicación específica ubican, necesita realizar cualquiera de estos pasos:</span><span class="sxs-lookup"><span data-stu-id="28701-246">To create a new mailbox in a specific geo location, you need to do either of these steps:</span></span>

- <span data-ttu-id="28701-p123">Configure el valor de **PreferredDataLocation** como se describe en la anterior sección *antes de* que crear el buzón en Exchange Online. Por ejemplo, configure el valor de **PreferredDataLocation** en un usuario antes de asignar una licencia.</span><span class="sxs-lookup"><span data-stu-id="28701-p123">Configure the **PreferredDataLocation** value as described in the previous section *before* the mailbox is created in Exchange Online. For example, configure the **PreferredDataLocation** value on a user before assigning a license.</span></span> 

- <span data-ttu-id="28701-249">Asignar una licencia al mismo tiempo, que se establece el valor de **PreferredDataLocation** .</span><span class="sxs-lookup"><span data-stu-id="28701-249">Assign a license at the same time you set the **PreferredDataLocation** value.</span></span>

<span data-ttu-id="28701-250">Para crear un nuevo solo en nube con licencia usuario (no AAD conectarse sincronizado) en un ubican específica, use la siguiente sintaxis en Azure AD PowerShell:</span><span class="sxs-lookup"><span data-stu-id="28701-250">To create a new cloud-only licensed user (not AAD Connect synchronized) in a specific Geo, use the following syntax in Azure AD PowerShell:</span></span>

```
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoCode> 
```
<span data-ttu-id="28701-251">En este ejemplo se crea una nueva cuenta de usuario para Elizabeth Brunner con los siguientes valores:</span><span class="sxs-lookup"><span data-stu-id="28701-251">This example create a new user account for Elizabeth Brunner with the following values:</span></span>

- <span data-ttu-id="28701-252">Nombre principal de usuario: ebrunner@contoso.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="28701-252">User principal name: ebrunner@contoso.onmicrosoft.com</span></span>

- <span data-ttu-id="28701-253">Nombre: Elizabeth</span><span class="sxs-lookup"><span data-stu-id="28701-253">First name: Elizabeth</span></span>

- <span data-ttu-id="28701-254">Apellido: Arturo López</span><span class="sxs-lookup"><span data-stu-id="28701-254">Last name: Brunner</span></span>

- <span data-ttu-id="28701-255">Nombre para mostrar Elizabeth Brunner</span><span class="sxs-lookup"><span data-stu-id="28701-255">Display name Elizabeth Brunner</span></span>

- <span data-ttu-id="28701-256">Contraseña: genera de forma aleatoria y se muestra en los resultados del comando (debido a que no estamos utilizando el parámetro *Password* )</span><span class="sxs-lookup"><span data-stu-id="28701-256">Password: randomly-generated and shown in the results of the command (because we're not using the *Password* parameter)</span></span>

- <span data-ttu-id="28701-257">Licencia: contoso:ENTERPRISEPREMIUM (E5)</span><span class="sxs-lookup"><span data-stu-id="28701-257">License: contoso:ENTERPRISEPREMIUM (E5)</span></span>

- <span data-ttu-id="28701-258">Ubicación: Australia (Australia)</span><span class="sxs-lookup"><span data-stu-id="28701-258">Location: Australia (AUS)</span></span>

```
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

<span data-ttu-id="28701-259">Para obtener más información sobre cómo crear nuevas cuentas de usuario y búsqueda de valores de LicenseAssignment en Azure AD PowerShell, vea [crear cuentas de usuario con Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) y [ver licencias y servicios con PowerShell de Office 365](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).</span><span class="sxs-lookup"><span data-stu-id="28701-259">For more information about creating new user accounts and finding LicenseAssignment values in Azure AD PowerShell, see [Create user accounts with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) and [View licenses and services with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).</span></span>

> <span data-ttu-id="28701-p124">**Nota:** Si usa Exchange Online PowerShell para habilitar un buzón de correo y necesita el buzón de correo que se creará directamente en el ubican que se especifica en **PreferredDataLocation**, debe usar un cmdlet de Exchange Online como **Enable-Mailbox** o \*\*New-Mailbox \*\*directamente en el servicio de nube. Si usa el cmdlet de Exchange local **Enable-RemoteMailbox** , se creará el buzón de correo en el valor predeterminado ubican.</span><span class="sxs-lookup"><span data-stu-id="28701-p124">**Note:** If you are using Exchange Online PowerShell to enable a mailbox and need the mailbox to be created directly in the Geo that's specified in **PreferredDataLocation**, you need to use an Exchange Online cmdlet such as **Enable-Mailbox** or **New-Mailbox** directly against the cloud service. If you use the **Enable-RemoteMailbox** on-premises Exchange cmdlet, the mailbox will be created in the default Geo.</span></span>

### <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo"></a><span data-ttu-id="28701-262">Incorporado existentes buzones locales en un ubican específico</span><span class="sxs-lookup"><span data-stu-id="28701-262">Onboard existing on-premises mailboxes in a specific Geo</span></span>
<span data-ttu-id="28701-263">Puede usar las herramientas de incorporación estándar y procesos para migrar un buzón de correo de una organización de Exchange local a Exchange Online, incluido el [panel de la migración en el EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331)y el cmdlet [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) en Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="28701-263">You can use the standard onboarding tools and processes to migrate a mailbox from an on-premises Exchange organization to Exchange Online, including the [Migration dashboard in the EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331), and the [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) cmdlet in Exchange Online PowerShell.</span></span>

<span data-ttu-id="28701-p125">El primer paso es comprobar que existe un objeto de usuario para que cada buzón de correo ser onboarded y compruebe que el valor correcto de **PreferredDataLocation** está configurado en Azure AD. Las herramientas de incorporación respetarán el valor **PreferredDataLocation** y migrarán los buzones de correo directamente a la ubican especificado.</span><span class="sxs-lookup"><span data-stu-id="28701-p125">The first step is to verify a user object exists for each mailbox to be onboarded, and verify the correct **PreferredDataLocation** value is configured in Azure AD. The onboarding tools will respect the **PreferredDataLocation** value and will migrate the mailboxes directly to the specified Geo.</span></span>

<span data-ttu-id="28701-266">O bien, puede usar los siguientes pasos para los buzones de correo incorporados directamente en una ubicación geográfica específica mediante el cmdlet [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) en Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="28701-266">Or, you can use the following steps to onboard mailboxes directly in a specific geo location using the [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) cmdlet in Exchange Online PowerShell.</span></span>

1. <span data-ttu-id="28701-p126">Compruebe si que existe el objeto de usuario para que cada buzón de correo ser onboarded y que **PreferredDataLocation** está establecida en el valor deseado de Azure AD. El valor de **PreferredDataLocation** se sincronizarán con el atributo **MailboxRegion** del objeto de usuario correspondiente de correo en Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="28701-p126">Verify the user object exists for each mailbox to be onboarded and that **PreferredDataLocation** is set to the desired value in Azure AD. The value of **PreferredDataLocation** will be synchronized to the **MailboxRegion** attribute of the corresponding mail user object in Exchange Online.</span></span>

2. <span data-ttu-id="28701-269">Conectarse directamente al satélite específico ubican siguiendo las instrucciones de conexión desde anteriormente en este tema.</span><span class="sxs-lookup"><span data-stu-id="28701-269">Connect directly to the specific satellite Geo using the connection instructions from earlier in this topic.</span></span>

3. <span data-ttu-id="28701-270">En Exchange Online PowerShell, almacenar las credenciales de administrador local que se utiliza para realizar una migración de buzones de correo en una variable, ejecute el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="28701-270">In Exchange Online PowerShell, store the on-premises administrator credentials that's used to perform a mailbox migration in a variable by running the following command:</span></span>

    ```
    $RC = Get-Credential
    ```

4. <span data-ttu-id="28701-271">En Exchange Online PowerShell, cree un nuevo **New-MoveRequest** similar al siguiente ejemplo:</span><span class="sxs-lookup"><span data-stu-id="28701-271">In Exchange Online PowerShell, create a new **New-MoveRequest** similar to the following example:</span></span> 

    ```
    New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
    ```

5. <span data-ttu-id="28701-272">Repita el paso 4 # para cada buzón que necesita para migrar de Exchange local a la ubicación de satélite que está actualmente conectado.</span><span class="sxs-lookup"><span data-stu-id="28701-272">Repeat step #4 for every mailbox you need to migrate from on-premises Exchange to the satellite location you are currently connected to.</span></span>

6. <span data-ttu-id="28701-273">Si necesita migrar buzones de correo adicionales a una ubicación diferente de satélite, repita los pasos del 2 al 4 para cada ubicación de satélite específicos.</span><span class="sxs-lookup"><span data-stu-id="28701-273">If you need to migrate additional mailboxes to a different satellite location, repeat steps 2 through 4 for each specific satellite location.</span></span>

### <a name="multi-geo-reporting"></a><span data-ttu-id="28701-274">Multi-ubican informes</span><span class="sxs-lookup"><span data-stu-id="28701-274">Multi-Geo Reporting</span></span>
<span data-ttu-id="28701-p127">**Multi-ubican los informes de uso** en el centro de administración de Office 365 muestra el recuento de usuarios por ubicación geográfica. El informe muestra la distribución de usuario para el mes actual y proporciona datos históricos de los últimos 6 meses.</span><span class="sxs-lookup"><span data-stu-id="28701-p127">**Multi-Geo Usage Reports** in the Office 365 admin center displays the user count by geo location. The report displays user distribution for the current month and provides historical data for the past 6 months.</span></span>
