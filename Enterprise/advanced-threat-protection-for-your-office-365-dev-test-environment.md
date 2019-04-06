---
title: Protección contra amenazas avanzada en el entorno de desarrollo y pruebas de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 51019757-20ac-498c-b51e-cae6d41a8c08
description: 'Resumen: configure y demuestre la Protección contra amenazas avanzada de Office 365 en el entorno de desarrollo y pruebas de Office 365.'
ms.openlocfilehash: 4ef057480f0ebfb2e64529f39d0db65031b75010
ms.sourcegitcommit: 201d3338d8bbc6da9389e62e2add8a17384fab4d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "31037944"
---
# <a name="advanced-threat-protection-for-your-office-365-devtest-environment"></a>Protección contra amenazas avanzada en el entorno de desarrollo y pruebas de Office 365

 **Resumen:** configure y demuestre la Protección contra amenazas avanzada de Office 365 en el entorno de desarrollo y pruebas de Office 365.
  
La Protección contra amenazas avanzada de Office 365 (ATP) es una característica de Exchange Online Protection (EOP) que ayuda a mantener el malware fuera de su correo electrónico. Con ATP, se crean directivas en el centro de administración de Exchange (EAC) o &amp; en el centro de seguridad y cumplimiento que ayudan a los usuarios a acceder únicamente a vínculos o datos adjuntos en los correos electrónicos que se identifican como no malintencionados. Para obtener más información, consulte [Protección contra amenazas avanzada para datos adjuntos seguros y vínculos seguros](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx).
  
Con las instrucciones de este artículo puede configurar y probar ATP en una suscripción de prueba de Office 365.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>Fase 1: Crear un entorno de desarrollo y pruebas ligero o de una empresa simulada de Office 365

Si solo quiere probar ATP de manera ligera con los requisitos mínimos, siga las instrucciones indicadas en las fases 2 y 3 del [entorno de desarrollo y pruebas de Office 365](office-365-dev-test-environment.md).
  
Si desea probar ATP en una empresa simulada, siga las instrucciones que se indican en [DirSync para el entorno de desarrollo y pruebas de Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> La prueba de ATP no requiere el entorno de desarrollo y pruebas de una empresa simulada, que incluye una intranet simulada conectada a Internet y la sincronización de directorios para un bosque de servicios de dominio de Active Directory (AD DS). Aquí se ofrece como opción para que pueda probar ATP y experimentar con ella en un entorno que representa una organización típica. 
  
## <a name="phase-2-demonstrate-the-default-email-delivery-behavior-of-office-365"></a>Fase 2: demostrar el comportamiento de entrega de correo electrónico predeterminado de Office 365

En esta fase, se demuestra que antes de configurar directivas de ATP, se entrega correo electrónico potencialmente malintencionado a buzones de Office 365 sin filtrado ni mitigación.
  
1. Abra Internet Explorer e inicie sesión en la cuenta de Outlook que creó en la fase 2 del [entorno de desarrollo y pruebas de Office 365](office-365-dev-test-environment.md).
    
  - Si usa el entorno de desarrollo y pruebas ligero de Office 365, abra una sesión privada con Internet Explorer e inicie sesión desde el equipo local.
    
  - Si usa el entorno de desarrollo y pruebas de una empresa simulada de Office 365, use [Azure portal](https://portal.azure.com) para conectarse a la máquina virtual CLIENT1 y, a continuación, inicie sesión desde cliente1.
    
2. Abra el Bloc de notas y escriba algún texto.
    
3. Guarde el archivo en la carpeta Documentos con el nombre **getKeys.js**.
    
4. En la pestaña de Correo de Outlook de Internet Explorer, haga clic en **Nuevo**.
    
5. En **Para**, escriba la dirección de correo electrónico del nombre de administrador global de Office 365 de su suscripción de prueba.
    
6. En el asunto, escriba **Sus nuevas claves**.
    
7. En el cuerpo, escriba **Aquí esta el archivo**.
    
8. Haga clic en **Adjuntar**, haga doble clic en **getKeys.js** en la carpeta Documentos, haga clic en **Adjuntar como una copia** y después en **Enviar**.
    
9. Haga clic en **Nueva**.
    
10. En **Para**, escriba la dirección de correo electrónico del nombre de administrador global de Office 365 de su suscripción de prueba.
    
11. En el asunto, escriba **Nuevo sitio web de viajes**.
    
12. En el cuerpo, escriba **Alguien me ha reenviado este sitio**.
    
13. En el cuerpo, seleccione el texto **este sitio** y haga clic en el icono de hipervínculo en la barra de herramientas.
    
14. En **dirección URL**, **http://www.spamlink.contoso.com/** escriba, haga clic en **Aceptar**y, a continuación, haga clic en **Enviar**.
    
15. Abra una instancia independiente de Internet Explorer en el modo de exploración privado, vaya al centro de administración de Microsoft[https://admin.microsoft.com](https://admin.microsoft.com)365 () e inicie sesión en su suscripción de prueba de Office 365 con su cuenta de administrador global.
    
16. Desde la página principal del portal, haga clic en el mosaico de aplicaciones y después en **Correo**.
    
17. En la Bandeja de entrada, haga clic en el mensaje con el asunto **Sus nuevas claves**.
    
18. En la carpeta correo no deseado, haga clic en el mensaje con el asunto **nuevo sitio web de viajes**. En el mensaje, haga clic en el vínculo a **sitio** . Debe ver un "vaya! Internet Explorer no pudo encontrar spamlink.contoso.com. " bloque. Este es el resultado correcto porque no hay ninguna página web en esa ubicación.
    
Observe que ambos correos electrónicos potencialmente malintencionados se entregaron correctamente. El correo electrónico **Sus nuevas claves** podría contener software malintencionado no detectado y se permite al usuario hacer clic en el vínculo potencialmente malintencionado en el correo electrónico **Nuevo sitio web de viajes**.
  
## <a name="phase-3-configure-safe-attachment-and-safe-links-policies-for-atp"></a>Fase 3: Configurar directivas de vínculos y archivos adjuntos seguros de ATP

En esta fase, creará y configurará una directiva de datos adjuntos seguros para evitar que el correo electrónico con datos adjuntos potencialmente malintencionados se entregue y una directiva de vínculos seguros para evitar que los usuarios visiten direcciones URL potencialmente inseguras.
  
1. En la pestaña **Inicio de Microsoft Office** de Internet Explorer, haga clic en el icono **Administración** .
    
2. En el panel de navegación izquierdo, haga clic en **Centros de administración** y después en **Exchange**.
    
3. En el panel de navegación izquierdo de la pestaña Centro de administración de Exchange, haga clic en **amenazas avanzadas**.
    
4. Haga clic en la pestaña **datos adjuntos seguros** y después en el signo más.
    
5. En la ventana **nueva Directiva de datos adjuntos seguros** , en **nombre**, escriba **Directiva de datos adjuntos seguros: bloquear**.
    
6. Para la respuesta de malware desconocidos de **datos adjuntos seguros**, haga clic en **bloquear**.
    
7. En **Redirigir datos adjuntos al detectarlos**, haga clic en **Habilitar redirección** y escriba la dirección de correo electrónico de la cuenta de administrador global de Office 365.
    
8. En **Aplicado a**, haga clic en la flecha abajo y después en **El dominio del destinatario es**. En la ventana, haga clic en el nombre de su organización (por ejemplo, contoso.onmicrosoft.com) y, a continuación, haga clic en **Aceptar**.
    
9. Haga clic en **Guardar **. Después de la actualización, debe ver el nuevo y habilitado **Directiva de datos adjuntos seguros: bloque**.
    
10. Haga clic en la pestaña **Vínculos seguros** y después en el signo más.
    
11. En la ventana **Nueva directiva de vínculos seguros**, escriba **Directiva de vínculos seguros** en **Nombre**.
    
12. En **Seleccionar la acción para direcciones URL potencialmente malintencionadas desconocidas en mensajes**, haga clic en **Activado** y seleccione **No permitir a los usuarios hacer clic en la dirección URL original**.
    
13. En **Aplicado a**, haga clic en la flecha abajo y después en **El dominio del destinatario es**. En la ventana, haga clic en el nombre de su organización (por ejemplo, contoso.onmicrosoft.com) y, a continuación, haga clic en **Aceptar**.
    
14. Haga clic en **Guardar**. Debería ver la nueva y habilitada **Directiva de vínculos seguros**.
    
## <a name="phase-4-show-atp-in-action"></a>Fase 4: Mostrar ATP en acción

En esta fase, veremos cómo ATP se gestiona el correo electrónico malintencionado.
  
1. En la sesión de Internet Explorer que usó para enviar el correo electrónico en la fase 2, en el panel de navegación izquierdo, haga clic en **elementos enviados.**
    
2. Haga clic en el correo electrónico titulado **claves nuevas**, haga clic en el icono de flecha **** abajo y, a continuación, haga clic en reenviar.
    
3. En el nuevo mensaje, en **Para**, escriba la dirección de correo electrónico del nombre de administrador global de Office 365 de su suscripción de prueba y después haga clic en **Enviar**.
    
4. Haga clic en el correo electrónico titulado **nuevo sitio web de viajes**, haga clic en el icono de flecha abajo, haga clic en **responder a todos**y, a continuación, haga clic en **Enviar**.
    
5. Desde la instancia de Internet Explorer que usó para configurar directivas de ATP en la fase 3, haga clic en la pestaña Centro de administración de Exchange, en el mosaico de aplicaciones y en **Correo**. Verá dos nuevos mensajes de correo electrónico en la Bandeja de entrada:
    
  - Uno titulado **RV: Sus nuevas claves**
    
  - Uno titulado **RV: Nuevo sitio web de viajes**
    
6. Abra el mensaje de correo electrónico titulado **FW: nuevo sitio web de viajes** y haga clic en este vínculo de **sitio** . Debería ver "este sitio web se ha clasificado como malintencionado". bloque. Esto demuestra que ATP está impidiendo el acceso al sitio Web potencialmente malintencionado.
    
7. En la pestaña Centro de administración de Exchange de Internet Explorer, en el panel de exploración izquierdo, haga clic en **Flujo de correo**.
    
8. Haga clic en la pestaña **Seguimiento de mensajes** y después en **Buscar**.
    
9. En la ventana **Resultados de seguimiento de mensajes**, haga doble clic en el mensaje con el asunto **Sus nuevas claves**. Este mensaje se entregó correctamente a la bandeja de entrada. Cierre esta ventana.
    
10. Haga doble clic en el mensaje con el asunto **Nuevo sitio web de viajes**. Este mensaje se entregó correctamente a la bandeja de entrada. Cierre esta ventana.
    
11. Haga doble clic en el mensaje con el asunto **RV: Sus nuevas claves**. Tenga en cuenta que ATP ha procesado este mensaje y, a continuación, se entregó en la bandeja de entrada. Cierre esta ventana.
    
    > [!NOTE]
    > La finalidad de la Directiva de datos adjuntos seguros era comenzar el examen de los datos adjuntos de código malintencionado. Se permitió el dato adjunto de getKeys. js porque no se determinó que era malintencionado. Este paso muestra que ATP llevó a cabo un análisis de los datos adjuntos. 
  
12. Haga doble clic en el mensaje con el asunto **RV: Nuevo sitio web de viajes**. Tenga en cuenta que este mensaje se entregó correctamente a la bandeja de entrada.
    
Ahora puede usar este entorno para crear nuevas directivas y experimentar con ATP.
  
> [!TIP]
> Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual de todos los artículos de la pila de la Guía del entorno de pruebas de One Microsoft Cloud.
  
## <a name="see-also"></a>Vea también

[Guías del laboratorio de pruebas de adopción de la nube (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[Entorno de desarrollo y pruebas de la configuración básica](base-configuration-dev-test-environment.md)
  
[Entorno de desarrollo y pruebas de Office 365](office-365-dev-test-environment.md)
  
[Sincronización de directorios (DirSync) para el entorno de desarrollo y prueba de Office 365](dirsync-for-your-office-365-dev-test-environment.md)
  
[Seguridad de Cloud App para su entorno de desarrollo y prueba de Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[Adopción de la nube y soluciones híbridas](cloud-adoption-and-hybrid-solutions.md) 

[Protección contra amenazas avanzada para datos adjuntos seguros y vínculos seguros](https://support.office.com/article/Office-365-Advanced-Threat-Protection-E100FE7C-F2A1-4B7D-9E08-622330B83653)


