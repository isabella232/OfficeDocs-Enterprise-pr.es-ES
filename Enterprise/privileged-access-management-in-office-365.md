---
title: Con privilegios de acceso a la administración de Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 7/13/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Strat_O365_IP
ms.custom: Ent_Solutions
ms.assetid: ''
description: Utilice este tema para obtener más información acerca de la característica de administración de acceso con privilegios en Office 365
ms.openlocfilehash: 22286d4f91ffa0bd3c49f028681d20e36d14283d
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915395"
---
# <a name="privileged-access-management-in-office-365"></a>Con privilegios de acceso a la administración de Office 365

> [!IMPORTANT]
> En este tema se tratan instrucciones de implementación y configuración de características de la versión beta pública sólo está disponibles actualmente en Office 365 E5 y avanzada SKU de cumplimiento.

Con privilegios de acceso permite la administración de control de acceso granular a través de las tareas de administración con privilegios en Office 365.  Puede ayudar a proteger la organización de las infracciones que pueden usar cuentas con privilegios de administración existentes con acceso permanente a los datos confidenciales o acceso a la configuración de configuración crítica. Después de habilitar la administración con privilegios de acceso, los usuarios deberán solicitar acceso just-in-time para completar las tareas con privilegios elevados y con privilegios a través de un flujo de trabajo de aprobación que es altamente con ámbito y límite de tiempo. Esto proporciona a los usuarios just-suficientemente-acceso para realizar la tarea en curso, sin riesgo de exposición de datos confidenciales u opciones de configuración críticos. Habilitación de la administración de acceso con privilegios en Office 365 habilitará la organización operar con cero privilegios permanente y proporcionar un nivel de defensa contra las vulnerabilidades de seguridad que surjan debido a tales acceso administrativo permanente. 

En este tema se le guiarán a través de habilitar y configurar la administración del acceso con privilegios en su organización de Office 365 y servir como una guía de referencia de solicitud, aprobación y administración de la característica. 

## <a name="before-you-begin"></a>Antes de empezar

### <a name="limited-functionality"></a>Funcionalidad limitada
Durante la versión beta pública, con privilegios de acceso a las características de administración sólo están disponibles a través de [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) en Office 365. Con privilegios de acceso a administración trata las definiciones de tarea en el nivel de los cmdlets de administración de Exchange. En futuras Office 365 versiones acceso con privilegios estarán disponible a través del portal de administración de características y cubren los otros servicios de cargas de trabajo de Office 365.

### <a name="connecting-to-exchange-online-powershell"></a>Conectarse a Exchange Online PowerShell
Los pasos de configuración en este tema le guiará a través de habilitación y uso de access con privilegios en Office 365 con Exchange Online PowerShell. 

Siga los pasos descritos en [conectarse a Exchange Online PowerShell mediante autenticación multifactor](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell?view=exchange-ps) para conectarse a Exchange Online PowerShell con sus credenciales de Office 365 para habilitar y configurar el acceso con privilegios para su organización.

> [!NOTE]
> No es necesario habilitar la autenticación multifactor para su organización de Office 365 usar los pasos para habilitar el acceso con privilegios mientras se conecta a Exchange Online PowerShell. Conectar con la autenticación multifactor crea un token de OAuth que se usa en el acceso con privilegios para las solicitudes de firma.

## <a name="enable-and-configure-privileged-access-management"></a>Habilitar y configurar la administración con privilegios de acceso

### <a name="step-1---create-an-approvers-group"></a>Paso 1: crear el grupo del aprobador
En el Portal de administración de Office 365, seleccione **grupos** > **Agregar un grupo**, a continuación, cree un grupo de seguridad habilitado para correo para los aprobadores de acceso predeterminada con privilegios. Cuando haya terminado, seleccione **Agregar** para crear y guardar el grupo de aprobadores.

![Pantalla de aprobadores con privilegios de acceso en el portal de administración de Office 365](media/privileged-access-approvers-ui.png)

> [!NOTE] 
> En este momento, sólo los usuarios con acceso administrativo pueden aprobar las solicitudes de acceso de Office 365 privilegiada. En el futuro, cualquier usuario que forma parte del grupo de los aprobadores podrán aprobar las solicitudes de acceso.

### <a name="step-2---enable-privileged-access-in-office-365"></a>Paso 2: habilitar el acceso con privilegios en Office 365
Acceso con privilegios debe habilitarse explícitamente con el grupo de aprobador predeterminado y un conjunto de cuentas del sistema que desea que se deben excluir desde el control de acceso de administración con privilegios de acceso, inclusive. 

En Exchange Online PowerShell para habilitar el acceso con privilegios y para asignar el grupo de aprobadores, ejecute el siguiente comando:
```
Enable-ElevatedAccessControl -AdminGroup '<default approver group>' -SystemAccounts @('<systemAccountUPN1>','<systemAccountUPN2>')
```
Ejemplo:
```
Enable-ElevatedAccessControl -AdminGroup 'pamapprovers@fabrikam.onmicrosoft.com' -SystemAccounts @('sys1@fabrikamorg.onmicrosoft.com', sys2@fabrikamorg.onmicrosoft.com')
```

> [!NOTE]
> Cuentas del sistema característica está disponible para asegurarse de determinados automations dentro de las organizaciones pueden trabajar sin dependencia en acceso con privilegios, sin embargo, se recomienda que estas exclusiones se excepcionales y los autorizados deben aprobados y auditar con regularidad.

### <a name="step-3---create-an-approval-policy"></a>Paso 3: crear una directiva de aprobación
Una directiva de aprobación le permite definir los requisitos de aprobación específico con ámbito en tareas individuales. Las opciones de tipo de aprobación son **automático** o **Manual**. 

Ejecute el siguiente comando en Exchange Online PowerShell para definir una directiva de aprobación:
```
New-ElevatedAccessApprovalPolicy -Task 'Exchange\<exchange management cmdlet name>' -ApprovalType <Manual, Auto> -ApproverGroup '<default/custom approver group>'
```
Ejemplo:
```
New-ElevatedAccessApprovalPolicy -Task 'Exchange\New-MoveRequest' -ApprovalType Manual -ApproverGroup 'mbmanagers@fabrikamorg.onmicrosoft.com'
```

## <a name="using-privileged-access-in-your-office-365-organization"></a>Uso de acceso con privilegios en su organización de Office 365

### <a name="requesting-elevation-authorization-to-execute-tasks"></a>Solicitud de autorización de elevación para ejecutar tareas
Una vez habilitado, con privilegios de acceso requiere aprobaciones para ejecutar cualquier tarea que tiene una directiva de aprobación asociada definida. Los usuarios que necesiten ejecutar tareas incluidas en la una directiva de aprobación debe solicitar y recibir aprobación de acceso con el fin de tener los permisos necesarios para ejecutar la tarea.

Ejecute el siguiente comando en Exchange Online PowerShell para crear y enviar una solicitud de aprobación al grupo del aprobador:
```
New-ElevatedAccessRequest -Task 'Exchange\<exchange management cmdlet name>' -Reason '<appropriate reason>' -DurationHours <duration in hours>
```
Ejemplo:
```
New-ElevatedAccessRequest -Task 'Exchange\New-MoveRequest' -Reason 'Attempting to fix the user mailbox error' -DurationHours 4
```
### <a name="view-status-of-elevation-requests"></a>Ver el estado de las solicitudes de elevación
Una vez creada una solicitud de aprobación, estado de la solicitud de elevación puede revisarse con el asociado con el identificador de solicitud.

Ejecute el siguiente comando en Exchange Online PowerShell para ver el estado de la solicitud de aprobación para un identificador de solicitud específico:
```
Get-ElevatedAccessRequest -Identity <request ID> | select RequestStatus
```
Ejemplo:
```
Get-ElevatedAccessRequest -Identity 28560ed0-419d-4cc3-8f5b-603911cbd450 | select RequestStatus
```

### <a name="approving-an-elevation-authorization-request"></a>Aprobación de una solicitud de autorización de elevación
Cuando se crea una solicitud de aprobación, los miembros del grupo de aprobadores relevantes recibirán una notificación de correo electrónico y pueden aprobar la solicitud asociada con el identificador de solicitud. 

Ejecute el siguiente comando en Exchange Online PowerShell para aprobar una solicitud de autorización de elevación:
```
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```
Ejemplo:
```
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```
### <a name="denying-an-elevation-authorization-request"></a>La denegación de una solicitud de autorización de elevación
Cuando se crea una solicitud de aprobación, los miembros del grupo de aprobadores relevantes pueden denegar la solicitud asociada con el identificador de solicitud. 

Ejecute el siguiente comando en Exchange Online PowerShell para denegar una solicitud de autorización de elevación:
```
Deny-ElevatedAccessRequest -RequestId <request id> -Comment '<denial comment>'
```
Ejemplo:
```
Deny-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<denial comment>'
```

### <a name="running-the-task"></a>Ejecución de la tarea
Una vez se concede la aprobación, el usuario solicitante puede ejecutar la tarea prevista y va a autorizar y ejecutar la tarea en nombre de los usuarios con privilegios de acceso. La aprobación sigue siendo válida para el solicitado duración (duración predeterminada es de 4 horas), durante el cual el solicitante puede ejecutar la tarea prevista varias veces. Todas esas ejecuciones se registran y a disposición de cumplimiento de normas de auditoría y seguridad. 

### <a name="disable-privileged-access-in-office-365"></a>Deshabilitar el acceso con privilegios en Office 365
Si es necesario, puede deshabilitar la administración de acceso con privilegios en Office 365. Deshabilitar con privilegios de acceso no eliminar cualquier las directivas de aprobación asociada o grupos de aprobador.

Ejecute el siguiente comando en Exchange Online Powershell para deshabilitar el acceso con privilegios:

```
Disable-ElevatedAccessControl
```
## <a name="managed-access-to-microsoft-graph-in-microsoft-azure"></a>Acceso a administrada para Microsoft Graph en Microsoft Azure

> [!IMPORTANT]
> En esta sección se describe cómo obtener información detallada acerca de una característica que sólo está disponible en vista previa.

Acceso administrado para Microsoft Graph en Microsoft Azure es un servicio que ayuda a las organizaciones a ejercer un nivel de control sobre sus datos de Office 365 específico. Este sistema permite que los desarrolladores de aplicaciones seguir entendimiento con los datos. 

Este sistema usa acceso a Office 365 con privilegios para assert control sobre sus datos a través de su flujo de trabajo de aprobación, que permite el acceso de ámbito a los datos de Office 365 con la supervisión de la administración. Las solicitudes de datos se incluyen cuando las aplicaciones se instalan y requieren acceso a datos de Office 365.

### <a name="view-request-details"></a>Vista Detalles de la solicitud
Ver los detalles de las solicitudes de acceso para los datos de Office 365.

Ejecute el siguiente comando en Exchange Online Powershell para ver las solicitudes de datos:
```
Get-ElevatedAccessRequest | where {$_.RequestedAccess -like '*Data Access Request*'} | select RequestorUPN, Service, RequestedAccess | fl
```
Salida de ejemplo:
```
RequestorUPN    : admin@contoso.com
Service         : Office365
RequestedAccess : Data Access Request
```

### <a name="approve-data-access-requests"></a>Aprobar solicitudes de acceso a datos
Todas las solicitudes de acceso de datos se pueden aprobar a través de los cmdlets de aprobación de acceso con privilegios estándar.

Ejecute el siguiente comando en Exchange Online Powershell para aprobar todas las solicitudes de datos para el solicitante específico:

```
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```
Ejemplo:
```
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```

## <a name="getting-help-and-providing-feedback"></a>Obtener ayuda y proporcionar comentarios
Reconocemos que durante la versión beta pública es posible que encuentre un error ocasional o tiene comentarios y sugerencias sobre cómo podemos mejorar la administración del acceso con privilegios. Se el valor de sus comentarios y anima a los usuarios a compartir con nosotros:
- Envíenos sus comentarios sugerencias de ad en el [Grupo de Yammer de vista previa de Office](https://www.yammer.com/officeenterprisenda/#/threads/inGroup?type=in_group&feedId=14435206).
- Archivo de los informes de errores en la ruta de acceso de área "Office 365 con privilegios administración de acceso" en el [VSO de vista previa de Office](https://office-previews.visualstudio.com/previews).

## <a name="frequently-asked-questions"></a>Preguntas más frecuentes

### <a name="what-skus-do-i-need-to-use-privileged-access-in-office-365"></a>¿Qué SKU es necesario usar access con privilegios en Office 365?
Con privilegios de acceso de administración de Office 365 actualmente sólo está disponible para los clientes con E5 y avanzada SKU de cumplimiento.

### <a name="when-will-privileged-access-be-available-for-office-365-workloads-beyond-exchange"></a>¿Cuándo estará disponible para cargas de trabajo de Office 365 más allá de Exchange con privilegios de acceso?
Se planea ofrecer esta característica en otras cargas de trabajo de Office 365 pronto. Cuando estamos listos para compartir una escala de tiempo, estará disponible a través de la guía básica de Office 365.

### <a name="how-is-this-different-from-azure-active-directorys-privileged-identity-management"></a>¿Cómo es diferente de la administración de identidades con privilegios de Active Directory de Azure?
Con privilegios de tener acceso a la administración de Office 365 y el complemento de [administración de identidades con privilegios de Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure) mutuamente proporcionando acceso controlar con acceso just-in-time en los distintos ámbitos. Juntos, proporcionan un completo conjunto de controles para la protección de los datos.

Con privilegios de acceso se puede definir y con ámbito en el nivel de tarea, mientras que la administración de identidades AD con privilegios de Azure se aplica en el nivel de función con la capacidad de ejecutar varias tareas de administración de Office 365.  Azure AD de administración de identidades con privilegios principalmente permite administrar accesos para las funciones de AD y grupos de roles mientras con privilegios de administración de acceso en Office 365 se aplica en el nivel de tarea.

 - **Con privilegios de habilitar acceso a administración de Office 365 mientras ya está usando la administración de identidades de AD con privilegios de Azure:** Adición de administración de acceso con privilegios en Office 365 puede proporcionar una capa pormenorizada de protección y capacidad para el acceso a datos de Office 365 con privilegios de auditoría.

- **Mientras ya está usando la administración de identidades AD con privilegios de habilitación de Azure con privilegios de administración de acceso en Office 365:**  Adición de la administración de identidades con Azure AD privilegios a con privilegios de administración de acceso en Office 365 puede ampliar con privilegios de acceso a datos fuera de Office 365 que principalmente se define por función o la identidad de un usuario. 

### <a name="do-i-need-to-be-a-global-admin-to-manage-privileged-access-in-office-365"></a>¿Es necesario ser un administrador Global para administrar el acceso con privilegios en Office 365?
Durante la vista previa debe tener privilegios de administrador Global para poder administrar el acceso con privilegios en Office 365. Los usuarios que se incluyen en el grupo de los aprobadores no es necesario ser un administrador Global para revisar y aprobar las solicitudes. 

### <a name="how-is-privileged-access-management-in-office-365-related-to-customer-lockbox"></a>¿Cómo es la administración de acceso con privilegios en Office 365 relacionadas con la caja de seguridad del cliente?
[Caja de seguridad de cliente](https://support.office.com/article/Office-365-Customer-Lockbox-Requests-36f9cdd1-e64c-421b-a7e4-4a54d16440a2) permite a un nivel de control de acceso para las organizaciones para el acceso a datos por su proveedor de servicios, es decir, Microsoft. Con privilegios de acceso de control de acceso granular dentro de una organización para todas las tareas de Office 365 con privilegios permite la administración de Office 365.