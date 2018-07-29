---
title: Plan de fin del soporte técnico de Exchange 2007
ms.author: dstrome
author: dstrome
manager: laurawi
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.assetid: c3024358-326b-404e-9fe6-b618e54d977d
description: En el 11 de abril de 2017, Exchange Server 2007 había alcanzado el final de soporte técnico. Si aún no ha empezado la migración de Exchange 2007 a Office 365 o Exchange 2016, ahora es el momento de empezar la planificación.
ms.openlocfilehash: 4bb8933977c280b4bfaa686e858fc818a1dc4ace
ms.sourcegitcommit: a9c84d02e94c99ff6b1099b4a9ae695be08210e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/25/2018
ms.locfileid: "21169812"
---
# <a name="exchange-2007-end-of-support-roadmap"></a>Plan de fin del soporte técnico de Exchange 2007

En **el 11 de abril de 2017**, Exchange Server 2007 había alcanzado el final de soporte técnico. Si aún no ha empezado la migración de Exchange 2007 a Office 365 o Exchange 2016, ahora es el momento de empezar la planificación. 
  
## <a name="what-does-end-of-support-mean"></a>¿Qué final hace de Media de soporte técnico?

Exchange Server, al igual que casi todos los productos de Microsoft, tiene un ciclo de vida de soporte técnico durante el cual se proporcionan las nuevas características, correcciones de errores, las revisiones de seguridad y así sucesivamente. Este ciclo de vida dura normalmente de 10 años desde la fecha de lanzamiento del producto, y el final de este ciclo de vida se conoce como fin del producto del soporte. Puesto que Exchange 2007 alcanza su fin del soporte en el 11 de abril de 2017, Microsoft ya no proporciona:
  
- Soporte técnico para problemas que puedan surgir;
    
- Correcciones de errores para los problemas que se descubren y que puede afectar a la estabilidad y la facilidad de uso del servidor;
    
- Revisiones de seguridad para las vulnerabilidades de seguridad que se descubren y que puede hacer el servidor vulnerable a infracciones de seguridad;
    
- Actualizaciones de zona horaria.
    
La instalación de Exchange 2007 continuará ejecutándose después de esta fecha. Sin embargo, debido a los cambios enumerados anteriormente, se recomienda encarecidamente que migre desde Exchange 2007 tan pronto como sea posible.
  
Para obtener más información acerca de los servidores de Office 2007 que se llega al final de soporte técnico, vea [Planear la actualización de los servidores de Office 2007 y productos](upgrade-from-office-2007-servers-and-products.md).
  
## <a name="what-are-my-options"></a>¿Cuáles son las opciones de mi?

Ahora que Exchange 2007 ha alcanzado el final de su soporte, recomendamos encarecidamente que explorar sus opciones y preparar un plan de migración. Puedes:
  
- Migrar a Office 365 utilizando la transferencia, por fases o migración híbrida;
    
- Migrar los servidores de Exchange 2007 a una versión más reciente de Exchange en los servidores locales.
    
En las secciones siguientes exploración cada opción con más detalle.
  
### <a name="migrate-to-office-365"></a>Migrar a Office 365

Migrar su correo electrónico a Office 365 es la opción más sencilla y los procedimientos que le ayudarán a retirar la implementación de Exchange 2007. Con una migración a Office 365, puede realizar un único salto de tecnología de 10 años a las características de estado de la técnica, como:
  
- Capacidades de cumplimiento de normas, como las directivas de retención en contexto y la suspensión por litigio, en contexto exhibición de documentos electrónicos y mucho más;
    
- Grupos de Office 365;
    
- Bandeja de entrada reducido;
    
- Profundizar análisis;
    
- API de REST para el acceso mediante programación a correo electrónico, calendarios, contactos y así sucesivamente.
    
Office 365 también obtiene nuevas características y experiencias de primera y usted y los usuarios normalmente pueden empezar utilizar de inmediato. Además de las características nuevas, no tendrá que preocuparse acerca de:
  
- Compra y el mantenimiento de hardware;
    
- Prestando para calefacción y refrigeración de los servidores;
    
- Mantener actualizados en las revisiones de seguridad, productos y zona horaria;
    
- Mantenimiento de almacenamiento de información y software para satisfacer los requisitos de cumplimiento de normas;
    
- Actualizar a una nueva versión de Exchange - está siempre en la versión más reciente de Exchange en Office 365.
    
#### <a name="how-should-i-migrate-to-office-365"></a>¿Cómo debo migrar a Office 365?

Dependiendo de la organización, tiene varias opciones que le ayudará a empezar a Office 365. Al elegir una opción de migración, debe tener en cuenta algunas cosas como el número de puestos o que tenga que mover los buzones de correo, ¿durante cuánto tiempo desea que la migración a último y si necesita una integración perfecta entre su instalación local y Office 365 durante la migración. Esta tabla muestra las opciones de migración y los factores más importantes que determinan el método que va a utilizar.
  
| |
|**Opción de migración**|**Tamaño de la organización**|**Duration**|
|:-----|:-----|:-----|
|Migración total  <br/> |Menos de 150 puestos  <br/> |Una semana o menos  <br/> |
|Migración preconfigurada  <br/> |Más de 150 puestos  <br/> |Unas cuantas semanas  <br/> |
|Migración completa híbrida  <br/> |Varios cientos a miles de puestos  <br/> |Unos meses o más  <br/> |
   
En las secciones siguientes proporcionan una visión general de estos métodos. Desproteger [Decide en una ruta de migración](https://support.office.com/en-us/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27) para conocer los detalles de cada método. 
  
#### <a name="cutover-migration"></a>Migración total

Migración de transferencia es donde, en un previa a la fecha y hora seleccionadas, se migra el todos los buzones de correo, grupos de distribución, contactos y así sucesivamente, a Office 365; Cuando haya terminado, podrá apagar los servidores de Exchange local y empezar a usar Office 365 exclusivamente.
  
El método de migración de traslado es ideal para las organizaciones pequeñas que no tengan muy muchos buzones, desea obtener acceso rápidamente a Office 365 y no desea abordar los problemas con algunas de la complejidad de los otros métodos. Pero que también un poco limitado porque se debería poder finalizar en una semana o menos y, ya que requiere que los usuarios volver a configurar los perfiles de Outlook. Mientras que la migración de traslado puede controlar hasta 2.000 buzones de correo, se recomienda que migrar un máximo de 150 buzones con este método. Si intenta migrar los buzones de más de 150, podría ejecutar agotó el tiempo para transferir todos los buzones antes de la fecha límite de y el soporte de TI puede obtener personal sobrecargado ayudar a los usuarios volver a configurar Outlook.
  
Si está pensando acerca de cómo realizar una migración de traslado, presentamos algunas cuestiones que tener en tenga en cuenta:
  
- Office 365 será necesario para conectarse a los servidores de Exchange 2007 mediante Outlook en cualquier lugar a través del puerto TCP 443;
    
- Todos los buzones locales se moverán a Office 365;
    
- Necesitará una cuenta de administrador local que tiene acceso para leer el contenido de los buzones de los usuarios;
    
- Exchange 2007 aceptado dominios que desea usar en Office 365 deben agregarse como dominios verificados en el servicio;
    
- Entre el tiempo de inicio de la migración y cuando comience la fase de finalización, Office 365 se sincronizarán periódicamente los buzones locales y Office 365. Esto permite a completar la migración sin preocuparse por correo electrónico que se quede en los buzones de correo local;
    
- Los usuarios recibirán nuevas contraseñas temporales para su cuenta de Office 365 que necesitan cambiar cuando inician sesión en sus buzones de correo por primera vez;
    
- Necesitará una licencia de Office 365 que incluye Exchange Online para cada buzón de usuario que migre;
    
- Los usuarios necesitan configurar un nuevo perfil de Outlook en cada uno de sus dispositivos y descargar su correo electrónico de nuevo. La cantidad de correo electrónico que Outlook descargará puede variar. Para obtener más información, eche un vistazo de [cambiar cuánto correo para mantener sin conexión](https://support.office.com/en-us/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&amp;rs=en-US&amp;ad=US&amp;fromAR=1).
    
Para obtener más información acerca de la migración de traslado, eche un vistazo:
  
- [Lo que debe saber sobre la migración total de correo electrónico a Office 365](https://support.office.com/en-us/article/What-you-need-to-know-about-a-cutover-email-migration-to-Office-365-961978ef-f434-472d-a811-1801733869da)
    
- [Realizar una migración de transferencia de correo electrónico a Office 365](https://support.office.com/en-us/article/Perform-a-cutover-migration-of-email-to-Office-365-9496e93c-1e59-41a8-9bb3-6e8df0cd81b4)
    
#### <a name="staged-migration"></a>Migración preconfigurada

Una migración por fases es uno que tenga unos pocos cientos o unos miles de buzones que desea migrar a Office 365, debe realizar una semana o más para completar la migración, y no necesita ninguna de las características de migración híbrida avanzada le gusta información de calendario de la información de disponibilidad compartida rmation.
  
Migración por fases es ideal para las organizaciones que necesitan más tiempo para migrar sus buzones de correo a Office 365, pero aún planear completar la migración dentro de un par de semanas. Puede migrar los buzones de correo en "lotes" que permiten controlar cuántos y qué, se migran los buzones de correo en un momento dado. Es posible que por lotes buzones de correo de los usuarios en el mismo departamento, por ejemplo, para asegurarse de todos los mueven al mismo tiempo. O bien, es posible que deje los buzones de correo ejecutivos hasta el último lote. Como con las migraciones de transferencia, los usuarios necesitan volver a crear sus perfiles de Outlook.
  
Si está pensando acerca de cómo realizar una migración por fases, a continuación presentamos algunas cosas que se deben considerar:
  
- Office 365 será necesario para conectarse a los servidores de Exchange 2007 mediante Outlook en cualquier lugar a través del puerto TCP 443;
    
- Necesitará una cuenta de administrador local que tiene acceso para leer el contenido de los buzones de los usuarios;
    
- Exchange 2007 aceptado dominios que desea usar en Office 365 deben agregarse como dominios verificados en el servicio;
    
- Debe crear un archivo CSV con el nombre completo y dirección de cada buzón que desee migrar en un lote de correo electrónico. También necesitará incluir una nueva contraseña para cada buzón que se está migrando y, a continuación, envíe su contraseña para cada usuario. El usuario le pedirá que cambie la contraseña la primera vez que inicie sesión su nuevo buzón de Office 365;
    
- Entre el momento en que se inicie el lote de migración y cuando comience la fase de finalización, Office 365 se sincronizarán periódicamente los buzones de correo de Office 365 y local incluidas en el lote. Esto permite a completar la migración sin preocuparse por correo electrónico que se quede en los buzones de correo local;
    
- Los usuarios recibirán nuevas contraseñas temporales para su cuenta de Office 365 que necesitan cambiar cuando inician sesión en sus buzones de correo por primera vez;
    
- Necesitará una licencia de Office 365 que incluye Exchange Online para cada buzón de usuario que migre;
    
- Los usuarios necesitan configurar un nuevo perfil de Outlook en cada uno de sus dispositivos y descargar su correo electrónico de nuevo. La cantidad de correo electrónico que Outlook descargará puede variar. Para obtener más información, eche un vistazo de [cambiar cuánto correo para mantener sin conexión](https://support.office.com/en-us/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&amp;rs=en-US&amp;ad=US&amp;fromAR=1).
    
Para obtener más información acerca de la migración por fases, eche un vistazo:
  
- [Lo que necesita saber acerca de una migración por fases de correo electrónico a Office 365](https://support.office.com/en-us/article/What-you-need-to-know-about-a-staged-email-migration-to-Office-365-7e2c82be-5f3d-4e36-bc6b-e5b4d411e207)
    
- [Realizar una migración por fases de correo electrónico a Office 365](https://support.office.com/en-us/article/Perform-a-staged-migration-of-email-to-Office-365-83bc0b69-de47-4cc4-a57d-47e478e4894e)
    
#### <a name="full-hybrid"></a>Híbrido completa

Migración híbrida completa es uno que su organización tiene varios cientos, hasta decenas de miles de buzones de correo y desea mover algunas o todas ellas a Office 365. Dado que estas migraciones son normalmente a largo plazo, migraciones híbridas hacen posible:
  
- Mostrar la información del calendario de disponibilidad para los usuarios de los usuarios locales en Office 365 y viceversa.
    
- Ver una lista de direcciones globales unificadas que contiene a los destinatarios en local y Office 365;
    
- Ver tarjetas de destinatarios de Outlook completas para todos los usuarios, independientemente de si local o en Office 365;
    
- Proteger la comunicación de correo electrónico entre los servidores de Exchange locales y Office 365 mediante TLS y certificados;
    
- Tratar los mensajes enviados entre los servidores de Exchange locales y Office 365 como interno, lo que les permite:
    
  - Correctamente se evalúen y procesados por agentes de transporte y cumplimiento de normas identificación de mensajes internos;
    
  - Omitir filtros contra correo no deseados.
    
Migraciones híbridas completa son mejores para las organizaciones que esperan a permanecer en una configuración híbrida durante muchos meses o más. Obtendrá las características enumeradas anteriormente en esta sección, además de sincronización de directorios, mejor las características de cumplimiento integrada y la capacidad de mover los buzones de correo a y desde Office 365 con movimientos de buzones en línea. Office 365 se convierte en una extensión de la organización local.
  
Si está pensando acerca de cómo realizar una migración completa híbrida, estas son algunas cosas que se deben considerar:
  
- Migraciones híbridas completa no están adaptadas a todos los tipos de organizaciones. Debido a la complejidad de migraciones híbridas completa, las organizaciones con unos pocos cientos de buzones normalmente no ven las ventajas que justifican el esfuerzo y el costo necesarios para configurar una lista. Si esto suena como su organización, se recomienda que tenga en cuenta las migraciones Cutover o etapas en su lugar;
    
- Debe implementar al menos un servidor de Exchange 2013 en la organización de Exchange 2007 para que actúe como un "servidor híbrido". Este servidor se comunicará con Office 365 en nombre de sus servidores Exchange 2007;
    
- Office 365 será necesario para conectarse a la "servidor híbrido" utilizando Outlook en cualquier lugar a través del puerto TCP 443;
    
- Necesita configurar la sincronización de directorios con Azure Active Directory Connect (AADConnect) entre los servidores de Active Directory local y Office 365;
    
- Los usuarios podrán iniciar sesión en su buzón de Office 365 con el mismo nombre de usuario y contraseña que se utilizan cuando inician sesión en la red local (requiere Azure Active Directory conectarse con la sincronización de contraseña o los servicios de federación de Active Directory);
    
- Necesitará una licencia de Office 365 que incluye Exchange Online para cada buzón de usuario que migre;
    
- Los usuarios no es necesario configurar un nuevo perfil de Outlook en la mayoría de sus dispositivos (algunos teléfonos Android más antiguos es posible que necesite un nuevo perfil) y no es necesario volver a descargar su correo electrónico.
    
Si un sonidos de migración híbrida completa adecuada para usted, eche un vistazo a los siguientes recursos para ayudarle con la migración:
  
- [Asistente de implementación de Exchange](https://aka.ms/exdeploy)
    
- [Implementaciones híbridas de Exchange Server](https://technet.microsoft.com/en-us/library/jj200581%28v=exchg.150%29.aspx)
    
- [Asistente de configuración híbrida](https://technet.microsoft.com/en-us/library/hh529921%28v=exchg.150%29.aspx)
    
- [Preguntas más frecuentes del asistente de configuración híbrida](https://technet.microsoft.com/en-us/library/mt488940%28v=exchg.150%29.aspx)
    
- [Requisitos previos de implementación híbrida](https://technet.microsoft.com/en-us/library/hh534377%28v=exchg.150%29.aspx)
    
### <a name="migrate-to-a-newer-version-of-exchange-server"></a>Migrar a una versión más reciente de Exchange Server

Aunque creemos encarecidamente que puede lograr la mejor experiencia de usuario y el valor mediante la migración a Office 365, también sabemos que algunas organizaciones necesitan mantener su correo electrónico local. Esto podría ser debido a los requisitos legales garantizar que la información no se almacena en un centro de datos que se encuentra en otro país y así sucesivamente. Si opta por mantener su correo electrónico local, puede migrar el entorno de Exchange 2007 a Exchange 2010, Exchange 2013 o 2016 de Exchange.
  
Se recomienda migrar a Exchange 2016 si no se puede migrar a Office 365. Exchange 2016 incluye todas las características y los avances que se incluye con las versiones anteriores de Exchange, y más aproxime la experiencia disponible con Office 365 (aunque algunas características sólo están disponibles en Office 365). Desproteger sólo algunas de las cosas que ha sido falta participar en:
  
|**Versión de Exchange**|**Características**|
|:-----|:-----|
|Exchange 2010  <br/> | Función Based Access Control (permisos sin ACL)  <br/>  Directivas de buzón de correo de Outlook Web Access  <br/>  Capacidad para compartir libre/ocupado y delegar calendarios entre las organizaciones  <br/> |
|Exchange 2013  <br/> | *Las características de Exchange 2010 y...*  <br/>  Arquitectura simplificada reduce el número de roles de servidor a tres (transporte perimetral del buzón de correo, acceso de cliente,)  <br/>  Directivas de prevención de pérdida de datos (DLP) que ayudan a mantener la pérdida de información confidencial  <br/>  Significativamente experiencia mejorada de Outlook Web App  <br/> |
|Exchange 2016  <br/> | *Las características de Exchange 2013 y...*  <br/>  Aún más los roles de servidor simplificada para acaba de buzón de correo y transporte perimetral  <br/>  DLP mejorada junto con la integración con SharePoint  <br/>  Resistencia mejorada de la base de datos  <br/>  Colaboración en documentos en línea  <br/> |
   
#### <a name="which-version-should-i-migrate-to"></a>¿Qué versión debo migrar a?

Se recomienda que inicialmente asumir que migre a Exchange 2016. A continuación, use la siguiente información para confirmar su suposición o para la regla de 2016 de Exchange. Si no se puede migrar a Exchange 2016 por una razón u otra, el mismo proceso con Exchange 2013 y así sucesivamente.
  
|**Consideración**|**Más información**|
|:-----|:-----|
|Final de fechas de soporte técnico  <br/> | Al igual que Exchange 2007, cada versión de Exchange tiene su propio final de la fecha de soporte técnico:  <br/> **Exchange 2010** - enero de 2020  <br/> **Exchange 2013** - de 2023 de abril  <br/> **Exchange 2016** - de 2025 de octubre  <br/>  Cuanto antes el final de la fecha de soporte, antes debe realizar otra migración. Enero de 2020 es mucho más cerca de lo que se imagina!<br/> |
|Ruta de migración a Exchange 2010 y 2013  <br/> |Éstas son las fases generales para migrar a Exchange 2010 o 2013 de Exchange:  <br/> Instalar Exchange 2010 o 2013 en los servicios de movimiento de organización de Exchange 2007 existentes y otra infraestructura de Exchange 2010 o 2013 mover buzones y carpetas públicas a Exchange 2010 o el resto de servidores de Exchange 2007 de retiro de 2013 |
|Ruta de migración a Exchange 2016  <br/> |Éstas son las fases generales para migrar a Exchange 2016:  <br/> Instalar Exchange 2013 en los servicios de movimiento de organización de Exchange 2007 existentes y otra infraestructura de Exchange 2013 mover buzones y de carpetas públicas a Exchange 2013 retiro restante instalar 2016 de Exchange de servidores de Exchange 2007 en su existentes Organización de Exchange 2013. Mover los buzones de correo, carpetas públicas, servicios y otro infraestructura a 2016 de Exchange (el orden no importa). Retirar servidores de Exchange 2013 restantes > [!NOTE]> migración desde Exchange 2013 a Exchange 2016 es sencillo. Ambas versiones tienen casi los mismos requisitos de hardware. Esto y el hecho de que estas versiones son por lo que significa que compatible con, puede volver a generar un servidor comprado para Exchange 2013 e instalar Exchange 2016 en él. Y con movimiento de buzones, mayoría de los usuarios nunca observará su buzón que se va a mover el servidor y, a continuación, vuelva una vez que haya reconstrucción con Exchange 2016.           |
|Coexistencia de versión  <br/> | Al migrar a:  <br/> **Exchange 2016** 2016 de Exchange no se puede instalar en una organización que incluye un servidor de Exchange 2007. En primer lugar necesitará para migrar a Exchange 2010 o 2013 (se recomienda encarecidamente Exchange 2013), quitar todos los servidores de Exchange 2007 y, a continuación, migrar a Exchange 2016.<br/> **Exchange 2010 o Exchange 2013** Puede instalar Exchange 2010 o Exchange 2013 en una organización existente de Exchange 2007. Esto permite instalar uno o más Exchange 2010 o 2013 servidores y llevar a cabo la migración.<br/> |
|Hardware de servidor  <br/> | Han cambiado los requisitos de hardware de servidor de Exchange 2007. Necesitará para asegurarse de que el hardware que se va a usar es compatible. Puede encontrar más información acerca de los requisitos de hardware para cada versión aquí:<br/> [Requisitos del sistema de Exchange 2016](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx) <br/> [Requisitos del sistema de Exchange 2013](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx) <br/> [Requisitos del sistema de Exchange 2010](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.141%29.aspx) <br/>  Encontrará que con las mejoras significativas en el rendimiento de Exchange y la mayor eficacia de los sistemas y la capacidad de almacenamiento en los servidores más recientes, que probablemente tendrá menos servidores para admitir el mismo número de buzones de correo.  <br/> |
|Versión del sistema operativo  <br/> | Las versiones de sistema operativo mínimo compatible para cada versión son:  <br/> **Exchange 2016** Windows Server 2012  <br/> **Exchange 2013** Windows Server 2008 R2 SP1  <br/> **Exchange 2010** Windows Server 2008 SP2  <br/>  Puede encontrar más información acerca de la compatibilidad con el sistema operativo en la [Matriz de compatibilidad de Exchange](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).  <br/> |
|Nivel funcional de bosque de Active Directory  <br/> | El mínimo compatible Active Directory niveles funcionales del bosque para cada versión son:  <br/> **Exchange 2016** Windows Server 2008 R2 SP1  <br/> **Exchange 2013** Windows Server 2003  <br/> **Exchange 2010** Windows Server 2003  <br/>  Puede encontrar más información acerca de la compatibilidad de nivel funcional de bosque en [Matriz de compatibilidad de Exchange](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).  <br/> |
|Versiones de cliente de Office  <br/> | Las versiones de cliente de Office compatibles como mínimas para cada versión son:  <br/> **Exchange 2016** Office 2010 (con las actualizaciones más recientes)  <br/> **Exchange 2013** SP3 de 2007 Office  <br/> **Exchange 2010** Office 2003  <br/>  Puede encontrar más información acerca de la compatibilidad con clientes de Office en la [Matriz de compatibilidad de Exchange](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).  <br/> |
   
#### <a name="how-do-i-migrate"></a>¿Cómo puedo migrar?

Si ha decidido que desea mantener su correo electrónico local, puede usar los siguientes recursos para ayudarle con la migración:
  
- [Asistente de implementación de Exchange](https://aka.ms/exdeploy)
    
- Cambios de esquema de Active Directory para Exchange [2016](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.150%29.aspx), [2010](https://www.microsoft.com/download/en/details.aspx?displaylang=en&amp;id=5401)
    
- Requisitos del sistema para Exchange [2016](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx), [2010](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.141%29.aspx)
    
- Requisitos previos para Exchange [2016](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.150%29.aspx), [2010](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.141%29.aspx)
    
## <a name="what-if-i-need-help"></a>¿Qué ocurre si necesita ayuda?

Si realiza la migración a Office 365, es posible que optan a utilizar nuestro servicio Microsoft FastTrack. FastTrack proporciona procedimientos recomendados, herramientas y recursos para realizar la migración a Office 365 es tan transparente como sea posible. Lo mejor de todo, tendrá un ingeniero de soporte real que le guiarán a través de la migración, desde la planificación y diseño completamente a migrar su buzón de correo última. Si desea saber más acerca de FastTrack, eche un vistazo en [FastTrack de Microsoft](https://fasttrack.microsoft.com/).
  
Si se ejecuta en los problemas durante la migración a Office 365 y que no esté utilizando FastTrack o la migración a una versión más reciente de Exchange Server, ya que estamos aquí para ayudar a. A continuación presentamos algunos recursos que puede utilizar:
  
- [Comunidad técnica](https://social.technet.microsoft.com/Forums/office/en-US/home?category=exchangeserver)
    
- [Soporte al cliente](https://support.microsoft.com/en-us/gp/support-options-for-business)
    
## <a name="related-topics"></a>Temas relacionados

[Recursos que le ayudarán a actualizar los servidores de Office 2007 y clientes](upgrade-from-office-2007-servers-and-products.md)
  
[Grupo de retirada de Office (Microsoft Tech Comunidad)](https://go.microsoft.com/fwlink/?linkid=842065)
  

