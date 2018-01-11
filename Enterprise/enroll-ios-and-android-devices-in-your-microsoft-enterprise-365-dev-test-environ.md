---
title: Inscribir a dispositivos iOS y Android en su entorno de pruebas y desarrollo de Microsoft Enterprise 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: "Resumen: Utilice a esta guía de laboratorio de prueba para inscribir dispositivos en su entorno de pruebas y desarrollo de Microsoft 365 y administrar de forma remota."
ms.openlocfilehash: 71d04b0d2a59683ff09ad4256ed8fc82e89e876a
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2018
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-devtest-environment"></a>Inscribir a dispositivos iOS y Android en su entorno de pruebas y desarrollo de Microsoft Enterprise 365

 **Resumen:** Utilice a esta guía de laboratorio de prueba para inscribir dispositivos en su entorno de pruebas y desarrollo de Microsoft 365 y administrar de forma remota.
  
La Suite Microsoft de movilidad empresarial (EMS) ayuda a mantener la productividad con sus aplicaciones favoritas y dispositivos mientras protege los datos de la organización de sus empleados. Para obtener más información, vea [seguridad (EMS) + de movilidad en la empresa](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).
  
Si necesita aplicar la seguridad en el nivel del dispositivo, debe inscribir dispositivos en Microsoft Intune. La inscripción de dispositivos no solo le ayuda a administrar dispositivos de propiedad corporativa, sino también dispositivos personales (BYOD) y compartidos, según las directivas legales de su organización.
  
Siguiendo las instrucciones proporcionadas en este artículo, podrá inscribirse y probar las capacidades de administración básica de dispositivos móviles para dispositivos iOS y Android en su entorno de pruebas y desarrollo de Microsoft 365.
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a>Fase 1: Crear el entorno de pruebas y desarrollo de Microsoft 365

Siga las instrucciones en el [entorno de desarrollo y prueba el Microsoft 365 Enterprise](the-microsoft-365-enterprise-dev-test-environment.md).
  
## <a name="phase-2-customize-the-microsoft-intune-company-portal-app"></a>Fase 2: Personalizar la aplicación del portal de empresa de Microsoft Intune

Use estos pasos para personalizar la aplicación de portal de empresa de Microsoft Intune para su compañía ficticia:
  
1. En una nueva ficha, abra la consola de administración de Microsoft Intune ([https://manage.microsoft.com](https://manage.microsoft.com)).
    
2. Haga clic en **Administrador** del panel de exploración y, a continuación, haga clic en **Administración de dispositivos móviles** en el panel de **administración** .
    
3. En la lista **tareas** , seleccione **Establecer órgano de gestión de dispositivos móviles**. Asegúrese de que está establecido para **Microsoft Intune**.
    
4. En el panel de **administración** , haga clic en **Portal de la empresa**.
    
5. En el panel de **Portal de empresa** , configure las siguientes opciones:
    
  - Nombre de la empresa: \<nombre de su compañía ficticia >
    
  - Nombre contacto del departamento de TI: **usuario5**
    
  - Número de teléfono del departamento de TI: **555-1234**
    
  - Dirección de correo electrónico del departamento de TI: **usuario5 @**\<nombre de la organización ficticia > **. onmicrosoft.com** (la dirección de correo electrónico de la cuenta de usuario5)
    
6. En **personalización**, seleccione **verde** en los **colores del tema**.
    
7. Haga clic en **Guardar**.
    
A continuación, instalará la aplicación del portal de empresa de Microsoft Intune e inscribirá un dispositivo iOS o Android. Además, probará la funcionalidad de administración básica de la consola de administración de Microsoft Intune.
  
## <a name="phase-3-for-ios-devices-only-enroll-and-manage-an-ios-device"></a>Fase 3 (solo para dispositivos iOS): Inscribir y administrar un dispositivo iOS

Para inscribir un dispositivo iOS para su administración en Intune, necesita lo siguiente:
  
- Un dispositivo iOS como un iPhone o iPad de Apple.
    
- Conocimiento de la contraseña del dispositivo iOS.
    
- Un ID de Apple (nombre de cuenta y contraseña). Si ya tiene uno, vaya a la [página Web de ID de Apple](https://appleid.apple.com/#!&amp;page=signin) y haga clic en **crear su ID de Apple**. Crear un ID de Apple correspondiente a la cuenta de administrador global de la suscripción de Office 365. Registrar su nuevo nombre de cuenta de Apple ID y la contraseña en un lugar seguro.
    
Se requiere un certificado de Apple Push Notification Service (APN) para que Intune administre dispositivos iOS y Mac. Una vez que el certificado se haya agregado a Intune, los usuarios podrán instalar la aplicación del portal de empresa de Microsoft Intune para inscribir sus dispositivos o el administrador podrá configurar la administración de dispositivos iOS de propiedad corporativa.
  
Es necesario un archivo de solicitud de firma de certificado para solicitar un certificado de relación de confianza desde el Portal de certificados push de Apple. Para obtener un archivo de solicitud de firma de certificado:
  
1. En la consola de administración Microsoft Intune, haga clic en **Administrador** del panel de exploración.
    
    En el panel de **administración** , abra **Mobile Device Management > iOS y Mac OS X**y, a continuación, haga clic en **cargar un certificado APN** en **tareas**. 
    
2. En el panel **cargar un certificado APN** , haga clic en **Descargar la solicitud de certificado de APN**. Guardar el certificado de firma de archivo de solicitud (.csr) localmente con el nombre de **desarrollo y pruebas**.
    
Para obtener un certificado de Apple Push Notification Service:
  
1. Abrir una nueva pestaña, vaya al [Portal de certificados Push de Apple](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2)e iniciar sesión con su ID de Apple.
    
2. En la página **Introducción** , haga clic en **crear un certificado**.
    
3. En la página **Condiciones de uso** , seleccione **he leído y acepta estos términos y condiciones**y, a continuación, haga clic en **Aceptar**.
    
4. En la página **crear un certificado nuevo de inserción** , haga clic en **Examinar** y, a continuación, haga clic en **cargar** **dev test.csr** guardado el archivo en el procedimiento anterior. Cuando se le pida para abrir un archivo json, guárdelo en la misma carpeta donde está almacenado el archivo dev-test.csr.
    
5. Abra el [Portal certificados Push de Apple](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2) en una ficha diferente y para los **certificados para los servidores de otros fabricantes**, haga clic en **Descargar**.
    
6. Cuando se le pida para abrir un archivo .pem, guárdelo con el nombre **test.pem de desarrollo** en la misma carpeta donde está almacenado el archivo dev-test.csr. Éste es el certificado de APN.
    
Para cargar el certificado de APNs en Intune:
  
1. En la ficha de la consola de administración de Microsoft Intune, en la página **cargar un certificado APN** , haga clic en **cargar el certificado APN**.
    
2. Haga clic en **Examinar** y especifique el archivo **dev-test.pem** .
    
3. Haga clic en **Abrir**, escriba su nombre de cuenta de ID de Apple y, a continuación, haga clic en **cargar**. Debería ver un mensaje **listo para la inscripción** en la página **iOS y X MaxOS configuración de dispositivo móvil** .
    
Con el certificado de APNs instalado, Intune ahora puede inscribir y administrar dispositivos iOS insertando directivas en los dispositivos móviles inscritos.
  
Para descargar la aplicación del portal de empresa de Microsoft Intune e inscribir el dispositivo iOS:
  
1. En el dispositivo iOS, inicie sesión con su Apple ID.
    
2. Abra la aplicación **Tienda de Apple** .
    
3. Escriba **intune** en el cuadro de búsqueda y en el **Portal de empresa de Microsoft Intune**, entonces **obtener**y, a continuación, **instalar**.
    
4. Después de que instale, puntee en **Abrir**.
    
5. En la pantalla de **Portal de empresa Intune** , inicie sesión con su cuenta de administrador global de Office 365.
    
6. En la pantalla de **Configuración de acceso de la compañía** , puntee en **Iniciar**y, a continuación, puntee dos veces en **continuar** .
    
7. En la **lo que viene a continuación?** de la pantalla, puntee en **Enroll**.
    
8. En la **Administrador del dispositivo Activate?** de la pantalla, puntee en **Activar**.
    
9. En la pantalla de **Perfil de administración** , puntee en **instalar**.
    
10. En **Introducir contraseña**, escriba la contraseña del dispositivo iOS.
    
11. En la pantalla **lo que viene a continuación** , puntee en **Enroll**.
    
12. En **Instalar perfil**, puntee en **instalar**.
    
13. En la página de **Advertencia** , puntee en **instalar**.
    
14. En la **Administración remota**, puntee en **Confiar**.
    
15. Puntee en **hecho** para completar el proceso de inscripción.
    
16. Cuando se le pida para **Abrir esta página en "Portal Comp"?**, puntee en **Abrir**.
    
17. En la pantalla de **Configuración de acceso de la compañía** , puntee en **Iniciar**y, a continuación, en **hecho**.
    
18. En la pantalla principal de la aplicación del portal de empresa de Microsoft Intune, debería ver:
    
  - Un banner verde.
    
  - El nombre de la compañía ficticia en la esquina superior izquierda.
    
  - El nombre del dispositivo iOS aparece en **Mis dispositivos**.
    
  - En la sección de **asistencia técnica** , el **Nombre del contacto** del **usuario5** con el número de teléfono **555-1234** y un botón de **contacto por correo electrónico** .
    
Microsoft Intune proporciona capacidades de restablecimiento de código de acceso y bloqueo remoto. Si alguien pierde su dispositivo, puede bloquearlo de forma remota. Si alguien olvida su código de acceso, puede eliminar el código de forma remota.
  
Para bloquear de forma remota un dispositivo iOS:
  
1. Desde el equipo de administración, en la ficha de consola de administración Microsoft Intune del explorador, haga clic en **grupos** en la exploración de la izquierda.
    
2. En el panel de **grupos** , abra **todos los dispositivos > dispositivos móviles todos > todos los dispositivos administrados de Direct**.
    
3. En el panel de **Todos los dispositivos administrados de directa** , haga clic en la ficha **dispositivos** .
    
4. En la lista de dispositivos, haga clic en su dispositivo iOS.  
    
5. En su dispositivo iOS, asegúrese de que está en la pantalla principal.  
    
6. Desde el equipo de administración, en la barra de tareas, haga clic en **tareas remotas > bloqueo remoto**. Observe el dispositivo iOS mientras se cambia a la pantalla de bloqueo.
    
Para eliminar el código de acceso:
  
1. Desde el equipo de administración, en el panel de **Todos los dispositivos administrados de directa** , haga clic en la ficha **dispositivos** .
    
2. En la lista, haga clic en el dispositivo iOS. En la barra de tareas, haga clic en **tareas remotas > Restablecer contraseña**. Espere un minuto.
    
3. Desde el dispositivo iOS, desbloquéelo y observe que ya no es un código de acceso. Para cambiar la contraseña de nuevo, vaya a **configuración**y, a continuación, **código de acceso**.
    
## <a name="phase-3-for-android-devices-only-enroll-and-manage-an-android-device"></a>Fase 3 (solo para dispositivos Android): Inscribir y administrar un dispositivo Android

Necesita lo siguiente para inscribir un dispositivo Android para su administración en Intune:
  
- Un dispositivo Android.
    
- Conocimiento de la contraseña del dispositivo.
    
Para descargar la aplicación del portal de empresa de Intune e inscribir el dispositivo Android:
  
1. Desde tu dispositivo Android, vaya a la **Tienda de Google Play**y, a continuación, puntee en **Empezar**.
    
2. Escriba **intune** en el cuadro Buscar y, a continuación, puntee en **intune portal de la compañía** en los resultados de la búsqueda.
    
3. Puntee en el elemento de **Portal de empresa Intune** y, a continuación, en **instalar**.
    
4. En la pantalla **para completar la instalación de cuenta** , puntee en **continuar**y, a continuación, **Omitir**.
    
5. En el **Portal de la empresa Intune**, puntee en **Aceptar**. El instala la aplicación.
    
6. Puntee en **Abrir**y, a continuación, puntee en **iniciar sesión**.
    
7. En la pantalla de **Portal de empresa Intune** , inicie sesión con su cuenta de administrador global de Office 365.
    
8. En la pantalla de **Configuración de acceso de la compañía** , puntee dos veces **empezar**y, a continuación, en **continuar** .
    
9. En la **lo que viene a continuación?** de la pantalla, puntee en **Enroll**.
    
10. En la **Administrador del dispositivo Activate?** de la pantalla, puntee en **Activate.**
    
11. En la pantalla de la **Política de privacidad** , seleccione **reconozco** y, a continuación, puntee en **Confirmar**. Espere a que el proceso de inscripción completar.
    
12. En la pantalla de **Configuración de acceso de la compañía** , puntee en **continuar**y, a continuación, en **hecho**.
    
13. En la pantalla principal de la aplicación del portal de empresa de Microsoft Intune, debería ver un banner de color verde y el nombre de su compañía ficticia en la parte superior izquierda.
    
14. Puntee en **Mis dispositivos**. Debería ver el nombre del dispositivo Android en la lista.
    
15. Puntee en **el contacto TI**. Debería ver el número de teléfono de **555-1234**, un botón de **contacto por correo electrónico** , y póngase en contacto con la TI de **usuario5**.
    
Microsoft Intune proporciona capacidades de restablecimiento de código de acceso y bloqueo remoto. Si alguien pierde su dispositivo, puede bloquearlo de forma remota. Si alguien olvida su código de acceso, puede restablecerlo de forma remota.
  
Para bloquear de forma remota un dispositivo Android:
  
1. Desde el equipo de administración, en la ficha de consola de administración Microsoft Intune del explorador, haga clic en **grupos** en la exploración de la izquierda.
    
2. En el panel de **grupos** , abra **todos los dispositivos > dispositivos móviles todos > todos los dispositivos administrados de Direct**.
    
3. En el panel de **Todos los dispositivos administrados de directa** , haga clic en la ficha **dispositivos** .
    
4. En la lista de dispositivos, haga clic en su dispositivo Android.  
    
5. En su dispositivo Android, asegúrese de que está en la pantalla principal.  
    
6. Desde el equipo de administración, en la barra de tareas, haga clic en **tareas remotas > bloqueo remoto**. Cuando se le pida, haga clic en **Sí**.
    
7. Observe su dispositivo Android mientras cambia a la pantalla de bloqueo.
    
Cuando se restablece la contraseña para los dispositivos Android, el portal de administración Intune genera y configura una contraseña segura.
  
Para restablecer el código de acceso de forma remota:
  
1. Desde el equipo de administración, en la ficha de consola de administración Microsoft Intune del explorador, en el panel de **Todos los dispositivos administrados de directa** , haga clic en el dispositivo Android.
    
2. En la barra de tareas, haga clic en **tareas remotas > Restablecer contraseña**.
    
3. En la **tarea remota: restablecer contraseña** pregunta, haga clic en **Sí**. Espere un minuto.
    
4. En el panel de **Todos los dispositivos administrados de directa** , haga clic en **Ver propiedades**.
    
5. Bajo **Restablecer contraseña**, tenga en cuenta la nueva contraseña.
    
6. En su dispositivo Android, introduzca el nuevo código de acceso en la pantalla de bloqueo.  
    
7. Para cambiar la contraseña de nuevo, vaya a **configuración**, puntee en el **dispositivo**, puntee en la **pantalla de bloqueo**, escriba la nueva contraseña, puntee en **bloqueo de pantalla**y, a continuación, su elección para el código de acceso.
    
> [!TIP]
> Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual de todos los artículos en la pila de la Guía del entorno de pruebas de One Microsoft Cloud.
  
## <a name="see-also"></a>Consulte también

[El entorno de pruebas y desarrollo empresarial de Microsoft 365](the-microsoft-365-enterprise-dev-test-environment.md)
  
[Directivas MAM para su entorno de pruebas y desarrollo empresarial de Microsoft 365](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[Guías de entorno de pruebas de adopción de la nube (TLG)](cloud-adoption-test-lab-guides-tlgs.md)

[Movilidad en la empresa + seguridad (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


