---
title: Plan de fin del soporte técnico de Exchange 2007
ms.author: dstrome
author: dstrome
manager: laurawi
ms.date: 1/31/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.assetid: c3024358-326b-404e-9fe6-b618e54d977d
description: El 11 de abril de 2017, el 2007 del servidor de Exchange alcanzó el final del soporte técnico. Si todavía no ha iniciado la migración de Exchange 2007 a Office 365 o Exchange 2016, ahora es el momento de empezar la planeación.
ms.openlocfilehash: 08796407e41fcc249da709267301de94fc359f36
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067616"
---
# <a name="exchange-2007-end-of-support-roadmap"></a>Plan de fin del soporte técnico de Exchange 2007

El **11 de abril de 2017**, el 2007 del servidor de Exchange alcanzó el final del soporte técnico. Si todavía no ha iniciado la migración de Exchange 2007 a Office 365 o Exchange 2016, ahora es el momento de empezar la planeación. 
  
## <a name="what-does-end-of-support-mean"></a>¿Qué significa el fin de soporte?

Exchange Server, como casi todos los productos de Microsoft, tiene un ciclo de vida de soporte técnico durante el cual ofrecemos nuevas características, correcciones de errores, correcciones de seguridad, etc. Este ciclo de vida suele durar 10 años a partir de la fecha de lanzamiento inicial del producto y el final de este ciclo de vida se conoce como el final del soporte técnico del producto. Dado que Exchange 2007 ha alcanzado el final del soporte técnico el 11 de abril de 2017, Microsoft ya no ofrece:
  
- Soporte técnico para los problemas que pueden surgir;
    
- Correcciones de errores para problemas detectados y que pueden afectar a la estabilidad y la usabilidad del servidor;
    
- Revisiones de seguridad para las vulnerabilidades detectadas y que pueden hacer que el servidor sea vulnerable a las infracciones de seguridad;
    
- Las actualizaciones de zona horaria.
    
La instalación de Exchange 2007 seguirá ejecutándose después de esta fecha. Sin embargo, debido a los cambios mencionados anteriormente, se recomienda encarecidamente migrar desde Exchange 2007 lo antes posible.
  
Para obtener más información acerca de los servidores de Office 2007 cerca de la finalización del soporte técnico, vea [plan Your upgrade from office 2007 Servers and Products](upgrade-from-office-2007-servers-and-products.md).
  
## <a name="what-are-my-options"></a>¿Qué opciones tengo?

Ahora que Exchange 2007 ha llegado al final del soporte técnico, le recomendamos encarecidamente que explore las opciones y prepare un plan de migración. Puede:
  
- Migrar a Office 365 mediante la migración de transferencia, preconfigurada o híbrida;
    
- Migre los servidores de Exchange 2007 a una versión más reciente de Exchange en los servidores locales.
    
En las siguientes secciones se examina cada opción con más detalle.
  
### <a name="migrate-to-office-365"></a>Migrar a Office 365

Migrar el correo electrónico a Office 365 es la mejor y más sencilla opción para ayudarle a retirar la implementación de Exchange 2007. Con una migración a Office 365, puede realizar un solo salto de la tecnología de 10 años hasta el estado de las características de arte, como:
  
- Capacidades de cumplimiento, como directivas de retención, conservación local y retención por juicio, exhibición de documentos electrónicos local y más;
    
- Office 365 grupos;
    
- Bandeja de entrada prioritarios;
    
- Análisis de Delve;
    
- API de REST para obtener acceso mediante programación al correo electrónico, calendarios, contactos, etc.
    
Office 365 también recibe nuevas características y experiencias en primer lugar, y usted y sus usuarios normalmente pueden empezar a usarlas de inmediato. Además de las nuevas características, no tendrá que preocuparse por:
  
- Comprar y mantener hardware;
    
- Pagar la calefacción y el enfriamiento de los servidores;
    
- Mantenerse al día de las correcciones de seguridad, producto y zona horaria;
    
- Mantener el almacenamiento y el software para admitir los requisitos de cumplimiento;
    
- Actualización a una nueva versión de Exchange: siempre está en la última versión de Exchange en Office 365.
    
#### <a name="how-should-i-migrate-to-office-365"></a>¿Cómo debo migrar a Office 365?

En función de su organización, tiene algunas opciones que le ayudarán a tener acceso a Office 365. Al elegir una opción de migración, debe tener en cuenta algunas cosas como el número de puestos o buzones que necesita mover, el tiempo que desea que dure la migración y si necesita una integración sin problemas entre la instalación local y Office 365 durante la migración. En esta tabla se muestran las opciones de migración y los factores más importantes que determinarán el método que se va a usar.
  
| |
|**Opción de migración**|**Tamaño de la organización**|**Duración**|
|:-----|:-----|:-----|
|Migración total  <br/> |Menos de 150 puestos  <br/> |Una semana o menos  <br/> |
|Migración preconfigurada  <br/> |Más de 150 puestos  <br/> |Unas semanas  <br/> |
|Migración híbrida completa  <br/> |Varios cientos o miles de puestos  <br/> |Unos meses o más  <br/> |
   
En las siguientes secciones se proporciona información general sobre estos métodos. Consulte [decidir una ruta de migración](https://support.office.com/en-us/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27) para conocer los detalles de cada método. 
  
#### <a name="cutover-migration"></a>Migración total

Una migración total es una ubicación en la que, en una fecha y hora preseleccionadas, migrará todos los buzones de correo, grupos de distribución, contactos, etc. a Office 365; Cuando haya terminado, cerrará los servidores de Exchange locales y empezará a usar Office 365 exclusivamente.
  
El método de migración total es ideal para las organizaciones pequeñas que no tienen muchos buzones de correo, por lo que quieren ir rápidamente a Office 365 y no desean tratar con algunas de las complejidades de los otros métodos. Pero también es un poco limitado porque debe completarse en una semana o menos y porque requiere que los usuarios vuelvan a configurar sus perfiles de Outlook. Aunque la migración total puede administrar hasta 2.000 buzones de correo, se recomienda encarecidamente migrar un máximo de 150 buzones de correo con este método. Si intenta migrar más de 150 buzones de correo, podría quedarse sin tiempo para transferir todos los buzones antes de la fecha límite y el personal de soporte técnico de ti podría sobrecargarse para ayudar a los usuarios a volver a configurar Outlook.
  
Si está pensando en realizar una migración total, estas son algunas de las cosas que debe considerar:
  
- Office 365 tendrá que conectarse a los servidores de Exchange 2007 mediante Outlook Anywhere a través del puerto TCP 443;
    
- Todos los buzones locales se moverán a Office 365;
    
- Necesitará una cuenta de administrador local que tenga acceso para leer el contenido de los buzones de los usuarios;
    
- Los dominios aceptados de Exchange 2007 que desea usar en Office 365 deben agregarse como dominios comprobados en el servicio;
    
- Entre el momento en que inicie la migración y cuando comience la fase de finalización, Office 365 sincronizará periódicamente los buzones de Office 365 y locales. Esto le permite completar la migración sin preocuparse por el correo electrónico que queda en sus buzones locales;
    
- Los usuarios recibirán nuevas contraseñas temporales en su cuenta de Office 365 que necesitarán cambiar cuando inicien sesión en sus buzones por primera vez;
    
- Necesitará una licencia de Office 365 que incluya Exchange Online para cada buzón de usuario que migre;
    
- Los usuarios tendrán que configurar un nuevo perfil de Outlook en cada uno de sus dispositivos y descargar de nuevo el correo electrónico. La cantidad de correo electrónico que Outlook va a descargar puede variar. Para obtener más información, eche un vistazo a [cambiar la cantidad de correo que se va a mantener sin conexión](https://support.office.com/en-us/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&amp;rs=en-US&amp;ad=US&amp;fromAR=1).
    
Para obtener más información sobre la migración total, eche un vistazo a:
  
- [Lo que debe saber sobre la migración total de correo electrónico a Office 365](https://support.office.com/en-us/article/What-you-need-to-know-about-a-cutover-email-migration-to-Office-365-961978ef-f434-472d-a811-1801733869da)
    
- [Realizar una migración total de correo electrónico a Office 365](https://support.office.com/en-us/article/Perform-a-cutover-migration-of-email-to-Office-365-9496e93c-1e59-41a8-9bb3-6e8df0cd81b4)
    
#### <a name="staged-migration"></a>Migración preconfigurada

Una migración preconfigurada es una de las que tiene unos cientos o miles de buzones de correo que desea migrar a Office 365, necesita llevar una semana o más para completar la migración y no necesita ninguna de las características avanzadas de migración híbrida, como la información de disponibilidad compartida rmation.
  
La migración preconfigurada es ideal para las organizaciones que necesitan más tiempo para migrar sus buzones de correo a Office 365, pero que todavía tienen previsto completar la migración en unas pocas semanas. Puede migrar los buzones de correo en "lotes" que le permiten controlar cuántos y qué buzones se migran en un momento dado. Es posible que tenga que realizar buzones de correo por lotes de usuarios en el mismo departamento, por ejemplo, para asegurarse de que todos se mueven al mismo tiempo. O bien, puede dejar buzones ejecutivos hasta el último lote. Al igual que con las migraciones de traslado, los usuarios tendrán que volver a crear sus perfiles de Outlook.
  
Si está pensando en realizar una migración preconfigurada, tenga en cuenta lo siguiente:
  
- Office 365 tendrá que conectarse a los servidores de Exchange 2007 mediante Outlook Anywhere a través del puerto TCP 443;
    
- Necesitará una cuenta de administrador local que tenga acceso para leer el contenido de los buzones de los usuarios;
    
- Los dominios aceptados de Exchange 2007 que desea usar en Office 365 deben agregarse como dominios comprobados en el servicio;
    
- Deberá crear un archivo CSV con el nombre completo y la dirección de correo electrónico de cada buzón que desee migrar en un lote. También tendrá que incluir una nueva contraseña para cada buzón de correo que esté migrando y, a continuación, enviar su contraseña a cada usuario. Se pedirá al usuario que cambie la contraseña la primera vez que inicie sesión en su nuevo buzón de Office 365;
    
- Entre el momento en el que se inicia el lote de migración y cuando se inicia la fase de finalización, Office 365 sincronizará periódicamente los buzones de Office 365 y locales que se incluyen en el lote. Esto le permite completar la migración sin preocuparse por el correo electrónico que queda en sus buzones locales;
    
- Los usuarios recibirán nuevas contraseñas temporales en su cuenta de Office 365 que necesitarán cambiar cuando inicien sesión en su buzón por primera vez;
    
- Necesitará una licencia de Office 365 que incluya Exchange Online para cada buzón de usuario que migre;
    
- Los usuarios tendrán que configurar un nuevo perfil de Outlook en cada uno de sus dispositivos y descargar de nuevo el correo electrónico. La cantidad de correo electrónico que Outlook va a descargar puede variar. Para obtener más información, eche un vistazo a [cambiar la cantidad de correo que se va a mantener sin conexión](https://support.office.com/en-us/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&amp;rs=en-US&amp;ad=US&amp;fromAR=1).
    
Para obtener más información sobre la migración preconfigurada, eche un vistazo a:
  
- [Lo que debe saber sobre una migración preconfigurada de correo electrónico a Office 365](https://support.office.com/en-us/article/What-you-need-to-know-about-a-staged-email-migration-to-Office-365-7e2c82be-5f3d-4e36-bc6b-e5b4d411e207)
    
- [Realizar una migración preconfigurada de correo electrónico a Office 365](https://support.office.com/en-us/article/Perform-a-staged-migration-of-email-to-Office-365-83bc0b69-de47-4cc4-a57d-47e478e4894e)
    
#### <a name="full-hybrid"></a>Híbrida completa

Una migración híbrida completa es aquel en el que la organización tiene muchos cientos, hasta decenas de miles de buzones de correo y desea mover algunos o todos ellos a Office 365. Debido a que estas migraciones suelen ser más duraderas, las migraciones híbridas hacen que sea posible:
  
- Mostrar a los usuarios locales la información del calendario de disponibilidad para los usuarios de Office 365 y viceversa;
    
- Consulte una lista global de direcciones unificada que contenga destinatarios tanto en local como en Office 365;
    
- Ver las tarjetas de destinatarios de Outlook completas para todos los usuarios, independientemente de si son locales o en Office 365;
    
- Proteger la comunicación del correo electrónico entre los servidores de Exchange locales y Office 365 mediante TLS y certificados;
    
- Tratar los mensajes enviados entre servidores de Exchange locales y Office 365 como internos, lo que les permite:
    
  - Ser evaluados y procesados correctamente por agentes de transporte y cumplimiento dirigidos a mensajes internos;
    
  - Omitir los filtros contra correo no deseado.
    
Las migraciones híbridas completas son las más adecuadas para las organizaciones que esperan permanecer en una configuración híbrida durante muchos meses o más. Obtendrá las características enumeradas anteriormente en esta sección, además de la sincronización de directorios, mejores características de cumplimiento integradas y la capacidad de mover buzones de correo a y desde Office 365 mediante movimientos de buzón en línea. Office 365 se convierte en una extensión de su organización local.
  
Si está pensando en realizar una migración híbrida completa, estas son algunas de las cosas que debe tener en cuenta:
  
- Las migraciones híbridas completas no son adecuadas para todos los tipos de organizaciones. Debido a la complejidad de las migraciones híbridas completas, las organizaciones con menos de unos pocos cientos de buzones de correo no suelen ver las ventajas que justifican el esfuerzo y el costo necesario para configurarlos. Si esto suena como su organización, se recomienda que considere las migraciones de transferencia o preconfiguradas en su lugar.
    
- Deberá implementar al menos un servidor de Exchange 2013 en la organización de Exchange 2007 para que actúe como un "servidor híbrido". Este servidor se comunicará con Office 365 en nombre de los servidores de Exchange 2007;
    
- Office 365 deberá conectarse al "servidor híbrido" mediante Outlook Anywhere a través del puerto TCP 443;
    
- Deberá configurar la sincronización de directorios mediante Azure Active Directory Connect (out) entre los servidores locales de Active Directory y Office 365;
    
- Los usuarios podrán iniciar sesión en su buzón de correo de Office 365 usando el mismo nombre de usuario y contraseña que usan cuando inician sesión en la red local (requiere Azure Active Directory Connect con la sincronización de contraseña y/o los servicios de Federación de Active Directory);
    
- Necesitará una licencia de Office 365 que incluya Exchange Online para cada buzón de usuario que migre;
    
- Los usuarios no necesitan configurar un nuevo perfil de Outlook en la mayoría de sus dispositivos (algunos teléfonos Android más antiguos podrían necesitar un nuevo perfil) y no tendrán que volver a descargar el correo electrónico.
    
Si le suena una migración híbrida completa, eche un vistazo a los siguientes recursos para ayudarle con la migración:
  
- [Asistente para la implementación de Exchange](https://aka.ms/exdeploy)
    
- [Implementaciones híbridas de Exchange Server](https://technet.microsoft.com/en-us/library/jj200581%28v=exchg.150%29.aspx)
    
- [Asistente de configuración híbrida](https://technet.microsoft.com/en-us/library/hh529921%28v=exchg.150%29.aspx)
    
- [Preguntas más frecuentes acerca del asistente de configuración híbrida](https://technet.microsoft.com/en-us/library/mt488940%28v=exchg.150%29.aspx)
    
- [Requisitos previos para la implementación híbrida](https://technet.microsoft.com/en-us/library/hh534377%28v=exchg.150%29.aspx)
    
### <a name="migrate-to-a-newer-version-of-exchange-server"></a>Migrar a una versión más reciente de Exchange Server

Aunque creemos que puede lograr el mejor valor y la experiencia del usuario mediante la migración a Office 365, también sabemos que algunas organizaciones necesitan mantener su correo local. Esto puede deberse a los requisitos normativos, para garantizar que los datos no se almacenan en un centro de datos ubicado en otro país y así sucesivamente. Si opta por mantener el correo electrónico local, puede migrar el entorno de Exchange 2007 a Exchange 2010, Exchange 2013 o Exchange 2016.
  
Le recomendamos que migre a Exchange 2016 si no puede migrar a Office 365. Exchange 2016 incluye todas las características y los avances incluidos en versiones anteriores de Exchange, y es la más cercana a la experiencia disponible con Office 365 (aunque algunas características solo están disponibles en Office 365). Consulte sólo algunas de las cosas en las que falta:
  
|**Versión de Exchange**|**Funciones**|
|:-----|:-----|
|Exchange 2010  <br/> | Control de acceso basado en roles (permisos sin ACL)  <br/>  Directivas de buzón de Outlook Web Access  <br/>  Capacidad para compartir calendarios de disponibilidad y de delegado entre organizaciones  <br/> |
|Exchange 2013  <br/> | *Características de Exchange 2010 y...*  <br/>  Arquitectura simplificada que reduce el número de roles de servidor a tres (buzón de correo, acceso de cliente y transporte perimetral)  <br/>  Directivas de prevención de pérdida de datos (DLP) que evitan la pérdida de información confidencial  <br/>  Experiencia de Outlook Web App mejorada de forma significativa  <br/> |
|Exchange 2016  <br/> | *Características de Exchange 2013 y...*  <br/>  Funciones de servidor más sencillas para solo buzones de correo y de transporte perimetral  <br/>  DLP mejorado junto con la integración con SharePoint  <br/>  Resistencia de base de datos mejorada  <br/>  Colaboración en documentos en línea  <br/> |
   
#### <a name="which-version-should-i-migrate-to"></a>¿A qué versión debo migrar?

Le recomendamos que primero asuma que migrará a Exchange 2016. A continuación, use la siguiente información para confirmar su hipótesis o para descartar Exchange 2016. Si no puede migrar a Exchange 2016 por un motivo u otro, realice el mismo proceso con Exchange 2013 y así sucesivamente.
  
|**Motivos**|**Más información**|
|:-----|:-----|
|Fecha de finalización del soporte técnico  <br/> | Al igual que Exchange 2007, cada versión de Exchange tiene su propio fin de fecha de soporte técnico:  <br/> **Exchange 2010** -enero 2020  <br/> **Exchange 2013** -abril 2023  <br/> **Exchange 2016** -octubre 2025  <br/>  Al final de la fecha de soporte técnico, lo antes que necesitará realizar otra migración. 2020 de enero es mucho más cercana a lo que cree.  <br/> |
|Ruta de migración a Exchange 2010 y 2013  <br/> |Estas son las fases generales para migrar a Exchange 2010 o Exchange 2013:  <br/> Instalar Exchange 2010 o 2013 en su organización existente de Exchange 2007 mueva los servicios y otra infraestructura a Exchange 2010 o 2013 mueva los buzones de correo y las carpetas públicas a Exchange 2010 o 2013 retirar los servidores de Exchange 2007 restantes |
|Ruta de migración a Exchange 2016  <br/> |Estas son las fases generales para la migración a Exchange 2016:  <br/> Instalar Exchange 2013 en su organización existente de Exchange 2007 mover los servicios y otra infraestructura a Exchange 2013 mover buzones de correo y carpetas públicas a Exchange 2013 retirar los servidores de Exchange 2007 instalar Exchange 2016 en el existente Organización de Exchange 2013. Mueva los buzones de correo, las carpetas públicas, los servicios y la otra infraestructura a Exchange 2016 (no importa el orden). Retirar los servidores Exchange 2013 restantes > [!NOTE]> migrar de Exchange 2013 a Exchange 2016 es sencillo. Ambas versiones tienen casi los mismos requisitos de hardware. Esto, y el hecho de que estas versiones son compatibles, significa que puede reconstruir un servidor comprado para Exchange 2013 e instalar Exchange 2016 en él. Además, con los movimientos en el buzón en línea, la mayoría de los usuarios nunca verán que su buzón se desplazan fuera del servidor y después se volverán a crear con Exchange 2016.           |
|Coexistencia de versiones  <br/> | Al migrar a:  <br/> **Exchange 2016** Exchange 2016 no se puede instalar en una organización que incluya un servidor de Exchange 2007. Primero tendrá que migrar a Exchange 2010 o 2013 (se recomienda encarecidamente usar Exchange 2013), quitar todos los servidores de Exchange 2007 y, a continuación, migrar a Exchange 2016.  <br/> **Exchange 2010 o exchange 2013** Puede instalar Exchange 2010 o Exchange 2013 en una organización de Exchange 2007 existente. Esto le permite instalar uno o varios servidores Exchange 2010 o 2013 y realizar la migración.  <br/> |
|Hardware de servidor  <br/> | Los requisitos de hardware del servidor han cambiado de Exchange 2007. Deberá asegurarse de que el hardware que va a usar es compatible. Puede obtener más información sobre los requisitos de hardware para cada versión aquí:  <br/> [Requisitos del sistema de Exchange 2016](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx) <br/> [Requisitos del sistema de Exchange 2013](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx) <br/> [Requisitos del sistema de Exchange 2010](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.141%29.aspx) <br/>  Encontrarás que con las mejoras significativas en el rendimiento de Exchange y la potencia de procesamiento y capacidad de almacenamiento aumentada en los nuevos servidores, probablemente necesitarás menos servidores para admitir el mismo número de buzones.  <br/> |
|Versión del sistema operativo  <br/> | Las versiones de sistema operativo mínimas admitidas para cada versión son:  <br/> **Exchange 2016** Windows Server 2012  <br/> **Exchange 2013** Windows Server 2008 R2 SP1  <br/> **Exchange 2010** Windows Server 2008 SP2  <br/>  Puede encontrar más información acerca del soporte del sistema operativo en la [matriz de compatibilidad de Exchange](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).  <br/> |
|Nivel funcional del bosque de Active Directory  <br/> | Los niveles de funcionalidad de bosque de Active Directory mínimos admitidos para cada versión son:  <br/> **Exchange 2016** Windows Server 2008 R2 SP1  <br/> **Exchange 2013** Windows Server 2003  <br/> **Exchange 2010** Windows Server 2003  <br/>  Puede encontrar más información acerca de la compatibilidad del nivel funcional del bosque en la [matriz de compatibilidad de Exchange](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).  <br/> |
|Versiones de cliente de Office  <br/> | Las versiones de cliente de Office mínimas admitidas para cada versión son:  <br/> **Exchange 2016** Office 2010 (con las actualizaciones más recientes)  <br/> **Exchange 2013** Office 2007 SP3  <br/> **Exchange 2010** Office 2003  <br/>  Puede encontrar más información acerca de la compatibilidad de clientes de Office en la [matriz de compatibilidad de Exchange](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).  <br/> |
   
#### <a name="how-do-i-migrate"></a>¿Cómo se realiza la migración?

Si ha decidido que desea conservar el correo electrónico local, puede usar los siguientes recursos para ayudarle con la migración:
  
- [Asistente para la implementación de Exchange](https://aka.ms/exdeploy)
    
- Cambios en el esquema de Active Directory para Exchange [2016](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.150%29.aspx), [2010](https://www.microsoft.com/download/en/details.aspx?displaylang=en&amp;id=5401)
    
- Requisitos del sistema para Exchange [2016](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx), [2010](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.141%29.aspx)
    
- Requisitos previos para Exchange [2016](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.150%29.aspx), [2010](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.141%29.aspx)
    
## <a name="what-if-i-need-help"></a>¿Qué debo hacer si necesito ayuda?

Si va a migrar a Office 365, puede ser elegible para usar nuestro servicio Microsoft FastTrack. FastTrack proporciona los procedimientos recomendados, las herramientas y los recursos para que la migración a Office 365 sea lo más fluida posible. Lo mejor de todo es que tendrá un ingeniero de soporte real que le guiará a través de la migración, desde la planeación y el diseño hasta la migración del último buzón. Si desea saber más sobre FastTrack, eche un vistazo a [Microsoft FastTrack](https://fasttrack.microsoft.com/).
  
Si surgen problemas durante la migración a Office 365 y no usa FastTrack o migrar a una versión más reciente de Exchange Server, estamos aquí para ayudarle. Estos son algunos de los recursos que puede usar:
  
- [Comunidad de soporte técnico](https://social.technet.microsoft.com/Forums/office/en-US/home?category=exchangeserver)
    
- [Soporte al cliente](https://support.microsoft.com/en-us/gp/support-options-for-business)
    
## <a name="related-topics"></a>Temas relacionados

[Recursos para ayudarle a actualizar sus clientes y servidores de Office 2007](upgrade-from-office-2007-servers-and-products.md)
  
[Grupo de jubilación de Office (Microsoft Tech Community)](https://go.microsoft.com/fwlink/?linkid=842065)
  

