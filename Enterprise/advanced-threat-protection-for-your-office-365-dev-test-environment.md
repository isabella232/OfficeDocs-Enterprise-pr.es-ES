---
title: "Protección contra amenazas avanzada en el entorno de desarrollo y pruebas de Office 365"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 51019757-20ac-498c-b51e-cae6d41a8c08
description: "Resumen: Configurar y demostrar la protección de amenazas avanzadas de Office 365 en su entorno de pruebas y desarrollo de Office 365."
ms.openlocfilehash: bc703bd01f3430a01810795b9d2ccea9e4ac9bc0
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="advanced-threat-protection-for-your-office-365-devtest-environment"></a>Protección contra amenazas avanzada en el entorno de desarrollo y pruebas de Office 365

 **Resumen:** Configurar y demostrar la protección de amenazas avanzadas de Office 365 en su entorno de pruebas y desarrollo de Office 365.
  
Protección de amenazas avanzadas de Office 365 (ATP) es una característica de Exchange Online Protection (elevación de privilegios) que ayuda a mantener el malware fuera de su correo electrónico. Con ATP, crear directivas en el centro de administración de Exchange (EAF) o la seguridad &amp; centro de cumplimiento de normas que ayudan a asegurar el acceso de los usuarios sólo vínculos o datos adjuntos en mensajes de correo electrónico que se identifican como no malintencionado. Para obtener más información, consulte [protección avanzada para los datos adjuntos seguros y vínculos seguros](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx).
  
Con las instrucciones de este artículo puede configurar y probar ATP en una suscripción de prueba de Office 365.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>Fase 1: Crear un entorno de desarrollo y pruebas ligero o de una empresa simulada de Office 365

Si desea probar ATP de una manera ligera con los requisitos mínimos, siga las instrucciones en las fases 2 y 3 del [entorno de desarrollo y prueba de Office 365](office-365-dev-test-environment.md).
  
Si desea probar ATP en una empresa simulada, siga las instrucciones de [sincronización de directorios para el entorno de desarrollo y prueba de Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> La realización de pruebas en ATP no requiere el entorno de desarrollo y pruebas de una empresa simulada, que incluye una intranet simulada conectada a Internet y la sincronización de directorios para un bosque de Windows Server AD. Aquí se ofrece como opción para que pueda probar ATP y experimentar con ella en un entorno que representa una organización típica. 
  
## <a name="phase-2-demonstrate-the-default-email-delivery-behavior-of-office-365"></a>Fase 2: Demostrar el comportamiento de entrega de correo electrónico predeterminado de Office 365

En esta fase, se demuestra que antes de configurar directivas de ATP, se entrega correo electrónico potencialmente malintencionado a buzones de Office 365 sin filtrado ni mitigación.
  
1. Abra Internet Explorer e inicie sesión en la cuenta de Outlook que creó en la fase 2 del [entorno de desarrollo y prueba de Office 365](office-365-dev-test-environment.md).
    
  - Si usa el entorno de desarrollo y pruebas ligero de Office 365, abra una sesión privada con Internet Explorer e inicie sesión desde el equipo local.
    
  - Si utiliza el entorno de desarrollo/pruebas simuladas enterprise Office 365, usar el [portal de Azure](https://portal.azure.com) para conectarse a la máquina virtual de CLIENTE1 e inicie sesión desde CLIENTE1.
    
2. Abra el Bloc de notas y escriba algún texto.
    
3. Guarde el archivo en la carpeta de documentos como **getKeys.js**.
    
4. Desde la ficha de correo de Outlook de Internet Explorer, haga clic en **nuevo**.
    
5. En el cuadro **para**, escriba la dirección de correo electrónico del nombre de administrador global de Office 365 de su suscripción de prueba.
    
6. Para el asunto, escriba **sus claves nuevas**.
    
7. En el cuerpo, escriba **que éste es el archivo**.
    
8. Haga clic en **asociar**, haga doble clic en **getKeys.js** en la carpeta documentos, haga clic en **Adjuntar como una copia**y, a continuación, haga clic en **Enviar**.
    
9. Haga clic en **nuevo**.
    
10. En el cuadro **para**, escriba la dirección de correo electrónico del nombre de administrador global de Office 365 de su suscripción de prueba.
    
11. Para el asunto, escriba **nuevo sitio web de viaje**.
    
12. En el cuerpo, escriba **que alguien me ha reenviado este sitio**.
    
13. En el cuerpo, seleccione el texto de **este sitio** y haga clic en el icono de hipervínculo en la barra de herramientas.
    
14. En **URL**, escriba **http://www.spamlink.contoso.com/**, haga clic en **Aceptar**y, a continuación, haga clic en **Enviar**.
    
15. Abrir una instancia independiente de Internet Explorer en el modo de exploración privado, vaya al portal de Office 365 ([https://portal.office.com](https://portal.office.com)) e iniciar sesión en su suscripción de prueba de Office 365 con su cuenta de administrador global.
    
16. Desde la página principal del portal, haga clic en el mosaico de aplicaciones y, a continuación, haga clic en **correo**.
    
17. En la Bandeja de entrada, haga clic en el mensaje con el asunto de **las nuevas claves**.
    
18. En la carpeta de correo no deseado, haga clic en el mensaje con el asunto **nuevo sitio web de viaje**. En el mensaje, haga clic en el vínculo de **este sitio** . Debería ver un "¡UY! Página de Internet Explorer no pudo encontrar spamlink.contoso.com.". Esto es el resultado correcto, porque no hay ninguna página web en esa ubicación.
    
Observe que ambos de estos correos electrónicos potencialmente malintencionados se entregaron correctamente. El correo electrónico de **tus nuevas claves** podría contener software malintencionado no detectado y se permite al usuario hacer clic en el vínculo en el correo electrónico **nuevo viaje sitio web** potencialmente malintencionado.
  
## <a name="phase-3-configure-safe-attachment-and-safe-links-policies-for-atp"></a>Fase 3: Configurar directivas de vínculos y archivos adjuntos seguros de ATP

En esta fase, creará y configurará una directiva de datos adjuntos seguros para evitar que el correo electrónico con datos adjuntos potencialmente malintencionados se entregue y una directiva de vínculos seguros para evitar que los usuarios visiten direcciones URL potencialmente inseguras.
  
1. En la ficha **Página de inicio de Microsoft Office** de Internet Explorer, haga clic en el mosaico de **Admin** .
    
2. En la exploración de la izquierda, haga clic en **centros de Admin**y, a continuación, en **Exchange**.
    
3. En la exploración de la izquierda de la ficha de centro de administración de Exchange, haga clic en **amenazas avanzadas**.
    
4. Haga clic en la ficha **archivos adjuntos seguros** y, a continuación, haga clic en el signo más.
    
5. En la ventana de la **nueva política de archivos adjuntos seguros** , en **nombre**, escriba **Directiva de datos adjuntos seguros - bloque**.
    
6. **Respuesta de los datos adjuntos seguros contra malware desconocido**, haga clic en **Bloquear**.
    
7. Para **redirigir los datos adjuntos en la detección**, haga clic en **Habilitar la redirección** y escriba la dirección de correo electrónico de la cuenta de administrador global de Office 365.
    
8. Para **se aplica a**, haga clic en la flecha abajo y, a continuación, haga clic en **el dominio del destinatario es**. En la ventana, haga clic en el nombre de su organización (por ejemplo, contoso.onmicrosoft.com) y, a continuación, haga clic en **Aceptar**.
    
9. Haga clic en **Guardar**. Después de la actualización, debe ver el nuevo y habilita la **Política de archivos adjuntos seguros - bloque**.
    
10. Haga clic en la ficha **vínculos seguros** y, a continuación, haga clic en el signo más.
    
11. En la ventana de la **nueva directiva de vínculos seguros** , en **nombre**, escriba **Directiva de enlace seguro**.
    
12. Para **Seleccionar la acción de direcciones URL malintencionadas desconocidas en mensajes**, haga clic **en**y, a continuación, seleccione **no permitir a los usuarios hacer clic en a la dirección URL original**.
    
13. Para **se aplica a**, haga clic en la flecha abajo y, a continuación, haga clic en **el dominio del destinatario es**. En la ventana, haga clic en el nombre de su organización (por ejemplo, contoso.onmicrosoft.com) y, a continuación, haga clic en **Aceptar**.
    
14. Haga clic en **Guardar**. Debería ver la nueva y había habilitada la **Directiva de enlace seguro**.
    
## <a name="phase-4-show-atp-in-action"></a>Fase 4: Mostrar ATP en acción

En esta fase, veremos cómo ATP se gestiona el correo electrónico malintencionado.
  
1. En la instancia de Internet Explorer que se utiliza para enviar el correo electrónico en la fase 2, en la exploración de la izquierda, haga clic en **elementos enviados.**
    
2. Haga clic en el mensaje titulado **las claves nuevas**, haga clic en el icono de flecha hacia abajo y, a continuación, haga clic en **Reenviar**.
    
3. Para el mensaje nuevo, en el cuadro **para**, escriba la dirección de correo electrónico del nombre de administrador global de Office 365 de su suscripción de prueba y, a continuación, haga clic en **Enviar**.
    
4. Haga clic en el mensaje titulado **viaje de nuevo sitio web**, haga clic en el icono de flecha hacia abajo, haga clic en **responder a todos**y, a continuación, haga clic en **Enviar**.
    
5. Desde la instancia de Internet Explorer que utiliza para configurar directivas de ATP en la fase 3, haga clic en la ficha de centro de administración de Exchange, haga clic en el mosaico de aplicaciones y, a continuación, haga clic en **correo**. Verá dos nuevos mensajes de correo electrónico en la Bandeja de entrada:
    
  - Uno titulado **Fw: las claves nuevo**
    
  - Uno titulado **Fw: nuevo sitio web de viajes**
    
6. Abra el mensaje de correo electrónico titulado **Fw: nuevo sitio web de viajes** y haga clic en el vínculo de **este sitio** . Debería ver una página "este sitio Web ha sido clasificada como malintencionados.". Esto demuestra que una ATP impide tener acceso al sitio web potencialmente malintencionados.
    
7. En la ficha de centro de administración de Exchange de Internet Explorer, en la exploración de la izquierda, haga clic en **el flujo de correo**.
    
8. Haga clic en la ficha **seguimiento del mensaje** y, a continuación, haga clic en **Buscar**.
    
9. En la ventana de **Resultados de seguimiento de mensajes** , haga doble clic en el mensaje con el asunto de **las nuevas claves**. Este mensaje se entregó correctamente a la Bandeja de entrada. Cerrar esta ventana.
    
10. Haga doble clic en el mensaje con el asunto **nuevo sitio web de viaje**. Este mensaje se entregó correctamente a la Bandeja de entrada. Cerrar esta ventana.
    
11. Haga doble clic en el mensaje con el asunto **Fw: las claves nuevo**. Observe cómo este mensaje procesó por ATP y, después, se enviarán a la Bandeja de entrada. Cerrar esta ventana.
    
    > [!NOTE]
    > El propósito de la política de archivos adjuntos seguros era comenzar el análisis de archivos adjuntos malintencionados. Los datos adjuntos de getKeys.js estaba permitido porque no se determinó malintencionada. Este paso muestra que ATP realizó un análisis de los datos adjuntos. 
  
12. Haga doble clic en el mensaje con el asunto **Fw: nuevo sitio web**. Tenga en cuenta que este mensaje se entregó correctamente a la Bandeja de entrada.
    
Ahora puede usar este entorno para crear nuevas directivas y experimentar con ATP.
  
> [!TIP]
> Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual para todos los artículos de la pila de una guía de laboratorio de prueba de nube de Microsoft.
  
## <a name="see-also"></a>Consulte también

[Guías del laboratorio de pruebas de adopción de la nube (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[Entorno de desarrollo y pruebas de la configuración básica](base-configuration-dev-test-environment.md)
  
[Entorno de desarrollo y pruebas de Office 365](office-365-dev-test-environment.md)
  
[Sincronización de directorios (DirSync) para el entorno de desarrollo y pruebas de Office 365](dirsync-for-your-office-365-dev-test-environment.md)
  
[Seguridad de la aplicación de nube para su entorno de pruebas y desarrollo de Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[Adopción de la nube y soluciones híbridas](cloud-adoption-and-hybrid-solutions.md) 

[Protección avanzada para los datos adjuntos seguros y vínculos seguros](https://support.office.com/article/Office-365-Advanced-Threat-Protection-E100FE7C-F2A1-4B7D-9E08-622330B83653)


