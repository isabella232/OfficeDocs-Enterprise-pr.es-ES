---
title: Guía básica de soporte de Exchange 2010
ms.author: dstrome
author: dstrome
manager: laurawi
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.assetid: e150e7b9-c432-4c8d-a0ae-c11847129a7d
description: Exchange 2010 está llegando al final del soporte técnico. Use esta guía básica de planeación como guía para preparar la actualización a Exchange online o a una versión más reciente de Exchange Server local.
ms.openlocfilehash: d9dcc2120f549c55fedc78483689dbded0a4464f
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487226"
---
# <a name="exchange-2010-end-of-support-roadmap"></a>Guía básica de soporte de Exchange 2010

El **14 de enero de 2020**, el 2010 de Exchange Server será el final del soporte técnico. Si todavía no ha iniciado la migración de Exchange 2010 a Office 365 o Exchange 2016, ahora es el momento de empezar la planeación.

## <a name="what-does-end-of-support-mean"></a>¿Qué significa el fin de soporte?

Exchange Server, como casi todos los productos de Microsoft, tiene un ciclo de vida de soporte técnico durante el cual ofrecemos nuevas características, correcciones de errores, correcciones de seguridad, etc. Este ciclo de vida suele durar 10 años a partir de la fecha de lanzamiento inicial del producto y el final de este ciclo de vida se conoce como el final del soporte técnico del producto.
Cuando Exchange 2010 llegue a su fin de soporte el 14 de enero de 2020, Microsoft dejará de proporcionar:

- Soporte técnico para los problemas que pueden surgir;
- Correcciones de errores para problemas detectados y que pueden afectar a la estabilidad y la usabilidad del servidor;
- Revisiones de seguridad para las vulnerabilidades detectadas y que pueden hacer que el servidor sea vulnerable a las infracciones de seguridad;
- Las actualizaciones de zona horaria.

La instalación de Exchange 2010 seguirá ejecutándose después de esta fecha. Sin embargo, debido a los cambios mencionados anteriormente, se recomienda encarecidamente migrar desde Exchange 2010 lo antes posible.

Para obtener más información acerca de los servidores de Office 2010 cerca de la finalización del soporte técnico, vea [recursos para ayudarle a actualizar desde Office 2010 servidores y clientes](https://docs.microsoft.com/en-us/office365/enterprise/upgrade-from-office-2010-servers-and-products).

## <a name="what-are-my-options"></a>¿Qué opciones tengo?

Una vez que Exchange 2010 alcanza su fin de soporte técnico, este es un buen momento para explorar las opciones y preparar un plan de migración. Puede:

- Migre completamente a Office 365. Migre los buzones usando la migración total, mínima híbrida o híbrida completa y, a continuación, quite los servidores de Exchange locales y Active Directory.
- Migre los servidores de Exchange 2010 a Exchange 2016 en los servidores locales.

> [!IMPORTANT]
> Si su organización decide migrar buzones a Office 365 pero pretende mantener la sincronización de directorios o Azure AD Connect en su lugar para seguir administrando las cuentas de usuario desde Active Directory local, debe tener al menos un servidor de Exchange local. Si se quita el último servidor de Exchange, no podrá realizar cambios en los destinatarios de Exchange en Exchange Online. Esto se debe a que el origen de la autoridad permanece en su Active Directory local y los cambios deben realizarse allí. En este escenario, tiene las siguientes opciones:

- (**Recomendado**) Si puede migrar sus buzones a Office 365 y actualizar los servidores antes del 14 de enero de 2020, use Exchange 2010 para conectarse a Office 365 y migrar buzones de correo. A continuación, migre Exchange 2010 a Exchange 2016 y retire los servidores de Exchange 2010 restantes.
- Si no puede completar la migración de buzones y la actualización del servidor local antes del 14 de enero de 2020, actualice los servidores locales de Exchange 2010 a Exchange 2016 primero y, a continuación, use Exchange 2016 para conectarse a Office 365 y migrar los buzones de correo.

> [!NOTE]
> Aunque un poco más complicado, también puede migrar buzones a Office 365 y migrar los servidores locales de Exchange 2010 a Exchange 2016.

En las siguientes secciones se examina cada opción con más detalle.

## <a name="migrate-to-office-365"></a>Migrar a Office 365

Migrar el correo electrónico a Office 365 es la mejor y más sencilla opción para ayudarle a retirar la implementación de Exchange 2010. Con una migración a Office 365, puede realizar un solo salto de tecnología antigua a características de vanguardia, como:

- Capacidades de cumplimiento, como directivas de retención, conservación local y retención por juicio, exhibición de documentos electrónicos local y más;
- Microsoft Teams;
- Power BI;
- Bandeja de entrada prioritarios;
- Análisis de Delve;

Office 365 también recibe nuevas características y experiencias en primer lugar, y usted y sus usuarios normalmente pueden empezar a usarlas de inmediato. Además de las nuevas características, no tendrá que preocuparse por:

- Comprar y mantener hardware;
- Pagar la calefacción y el enfriamiento de los servidores;
- Mantenerse al día de las correcciones de seguridad, producto y zona horaria;
- Mantener el almacenamiento y el software para admitir los requisitos de cumplimiento;
- Actualización a una nueva versión de Exchange: siempre está en la última versión de Exchange en Office 365.

### <a name="how-should-i-migrate-to-office-365"></a>¿Cómo debo migrar a Office 365?

En función de su organización, tiene algunas opciones que le ayudarán a tener acceso a Office 365. Al elegir una opción de migración, debe tener en cuenta algunas cosas como el número de puestos o buzones que necesita mover, el tiempo que desea que dure la migración y si necesita una integración sin problemas entre la instalación local y Office 365 durante la migración. En esta tabla se muestran las opciones de migración y los factores más importantes que determinarán el método que se va a usar.

| **Opción de migración**     | **Tamaño de la organización** | **Duración**        |
|--------------------------|-----------------------|---------------------|
| Migración total        | Menos de 150 puestos  | Una semana o menos      |
| Migración híbrida mínima | Menos de 150 puestos  | Unas semanas o menos |
| Migración híbrida completa    | Más de 150 puestos   | Unas semanas o más |

En las siguientes secciones se proporciona información general sobre estos métodos. Consulte [decidir una ruta de migración](https://support.office.com/en-us/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27) para conocer los detalles de cada método.

### <a name="cutover-migration"></a>Migración total

Una migración total es una ubicación en la que, en una fecha y hora preseleccionadas, migrará todos los buzones de correo, grupos de distribución, contactos, etc. a Office 365; Cuando haya terminado, cerrará los servidores de Exchange locales y empezará a usar Office 365 exclusivamente.

El método de migración total es ideal para las organizaciones pequeñas que no tienen muchos buzones de correo, por lo que quieren ir rápidamente a Office 365 y no desean tratar con algunas de las complejidades de los otros métodos. Pero también es un poco limitado porque debe completarse en una semana o menos y porque requiere que los usuarios vuelvan a configurar sus perfiles de Outlook. Aunque la migración total puede administrar hasta 2.000 buzones de correo, se recomienda encarecidamente migrar un máximo de 150 buzones de correo con este método. Si intenta migrar más de 150 buzones de correo, podría quedarse sin tiempo para transferir todos los buzones antes de la fecha límite y el personal de soporte técnico de ti podría sobrecargarse para ayudar a los usuarios a volver a configurar Outlook.

Si está pensando en realizar una migración total, estas son algunas de las cosas que debe considerar:

- Office 365 tendrá que conectarse a los servidores de Exchange 2010 mediante Outlook Anywhere a través del puerto TCP 443;
- Todos los buzones locales se moverán a Office 365;
- Necesitará una cuenta de administrador local que tenga acceso para leer el contenido de los buzones de los usuarios;
- Los dominios aceptados de Exchange 2010 que desea usar en Office 365 deben agregarse como dominios comprobados en el servicio;
- Entre el momento en que inicie la migración y cuando comience la fase de finalización, Office 365 sincronizará periódicamente los buzones de Office 365 y locales. Esto le permite completar la migración sin preocuparse por el correo electrónico que queda en sus buzones locales;
- Los usuarios recibirán nuevas contraseñas temporales en su cuenta de Office 365 que necesitarán cambiar cuando inicien sesión en sus buzones por primera vez;
- Necesitará una licencia de Office 365 que incluya Exchange Online para cada buzón de usuario que migre;
- Los usuarios tendrán que configurar un nuevo perfil de Outlook en cada uno de sus dispositivos y descargar de nuevo el correo electrónico. La cantidad de correo electrónico que Outlook va a descargar puede variar. Para obtener más información, eche un vistazo a [cambiar la cantidad de correo que se va a mantener sin conexión](https://support.office.com/en-us/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&rs=en-US&ad=US&fromAR=1).

Para obtener más información sobre la migración total, eche un vistazo a:

- [Lo que debe saber sobre la migración total de correo electrónico a Office 365](https://support.office.com/en-us/article/What-you-need-to-know-about-a-cutover-email-migration-to-Office-365-961978ef-f434-472d-a811-1801733869da)
- [Realizar una migración total de correo electrónico a Office 365](https://support.office.com/en-us/article/Perform-a-cutover-migration-of-email-to-Office-365-9496e93c-1e59-41a8-9bb3-6e8df0cd81b4)

### <a name="minimal-hybrid-migration"></a>Migración híbrida mínima

Una migración híbrida o exprés mínima es la que tiene unos cientos de buzones de correo que desea migrar a Office 365, puede completar la migración en unas pocas semanas y no necesita ninguna de las características avanzadas de migración híbrida, como el calendario de disponibilidad compartido información.

La migración híbrida mínima es ideal para las organizaciones que necesitan más tiempo para migrar sus buzones de correo a Office 365, pero que aún planean completar la migración en unas pocas semanas. Se obtienen algunas ventajas de la migración híbrida completa más avanzada sin muchas de las complejidades. Puede controlar cuántos y qué buzones se migran en un momento dado; Los buzones de Office 365 se crearán con el nombre de usuario y las contraseñas de sus cuentas locales; y, a diferencia de las migraciones de traslado, los usuarios no tendrán que volver a crear sus perfiles de Outlook.

Si está pensando en realizar una migración híbrida mínima, estas son algunas de las cosas que debe tener en cuenta:

- Deberá realizar una sincronización de directorios de una sola vez entre los servidores locales de Active Directory y Office 365;
- Los usuarios podrán iniciar sesión en su buzón de correo de Office 365 con el mismo nombre de usuario y la misma contraseña que usaban cuando se migró el buzón de correo;
- Necesitará una licencia de Office 365 que incluya Exchange Online para cada buzón de usuario que migre;
- Los usuarios no necesitan configurar un nuevo perfil de Outlook en la mayoría de sus dispositivos (algunos teléfonos Android más antiguos podrían necesitar un nuevo perfil) y no tendrán que volver a descargar el correo electrónico.

Para obtener más información acerca de la migración híbrida mínima, eche un vistazo al uso de la [mínima implementación híbrida para migrar rápidamente buzones de Exchange a Office 365](https://support.office.com/article/Use-Minimal-Hybrid-to-quickly-migrate-Exchange-mailboxes-to-Office-365-fdecceed-0702-4af3-85be-f2a0013937ef)

### <a name="full-hybrid"></a>Híbrida completa

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

- Las migraciones híbridas completas no son adecuadas para todos los tipos de organizaciones. Debido a la complejidad de las migraciones híbridas completas, las organizaciones con menos de unos pocos cientos de buzones de correo no suelen ver las ventajas que justifican el esfuerzo y el costo necesario para configurarlos. Si esto suena como su organización, se recomienda que considere la posibilidad de realizar migraciones híbridas de transferencia o mínimas.
- Deberá configurar la sincronización de directorios mediante Azure Active Directory Connect (out) entre los servidores locales de Active Directory y Office 365;
- Los usuarios podrán iniciar sesión en su buzón de correo de Office 365 usando el mismo nombre de usuario y contraseña que usan cuando inician sesión en la red local (requiere Azure Active Directory Connect con la sincronización de contraseña y/o los servicios de Federación de Active Directory);
- Necesitará una licencia de Office 365 que incluya Exchange Online para cada buzón de usuario que migre;
- Los usuarios no necesitan configurar un nuevo perfil de Outlook en la mayoría de sus dispositivos (algunos teléfonos Android más antiguos podrían necesitar un nuevo perfil) y no tendrán que volver a descargar el correo electrónico.

> [!IMPORTANT]
> Si su organización decide migrar buzones a Office 365 pero pretende mantener la sincronización de directorios o Azure AD Connect en su lugar para seguir administrando las cuentas de usuario desde Active Directory local, debe tener al menos un servidor de Exchange local. Si se quita el último servidor de Exchange, no podrá realizar cambios en los destinatarios de Exchange en Exchange Online. Esto se debe a que el origen de la autoridad permanece en su Active Directory local y los cambios deben realizarse allí.

Si le suena una migración híbrida completa, eche un vistazo a los siguientes recursos para ayudarle con la migración:

- [Asistente para la implementación de Exchange](https://aka.ms/exdeploy)
- [Implementaciones híbridas de Exchange Server](https://technet.microsoft.com/en-us/library/jj200581%28v=exchg.150%29.aspx)
- [Asistente de configuración híbrida](https://technet.microsoft.com/en-us/library/hh529921%28v=exchg.150%29.aspx)
- [Preguntas más frecuentes acerca del asistente de configuración híbrida](https://technet.microsoft.com/en-us/library/mt488940%28v=exchg.150%29.aspx)
- [Requisitos previos para la implementación híbrida](https://technet.microsoft.com/en-us/library/hh534377%28v=exchg.150%29.aspx)

## <a name="upgrade-to-a-newer-version-of-exchange-server-on-premises"></a>Actualizar a una versión más reciente de Exchange Server local

Aunque creemos que puede lograr el mejor valor y la experiencia del usuario mediante la migración completa a Office 365, también sabemos que algunas organizaciones necesitan mantener algunos servidores de Exchange locales. Esto puede deberse a los requisitos normativos, para garantizar que los datos no se almacenan en un centro de datos ubicado en otro país, o puede deberse a que tenga una configuración o requisitos únicos que no se puedan cumplir en la nube, o bien que simplemente sea necesario que Exchange administre los buzones de la nube porque todavía usa Active Directory local. En cualquier caso en el que elija o necesite mantener Exchange local, debe asegurarse de que el entorno de Exchange 2010 se actualiza al menos Exchange 2013 o Exchange 2016 y que Exchange 2010 se ha quitado antes de la fecha de finalización del soporte técnico.

Para que la experiencia sea óptima, le recomendamos que actualice el entorno local restante a Exchange 2016. No es necesario instalar Exchange Server 2013 si desea ir directamente de Exchange Server 2010 a Exchange Server 2016.

Exchange 2016 incluye todas las características y los avances incluidos en versiones anteriores de Exchange, y es la más cercana a la experiencia disponible con Office 365 (aunque algunas características solo están disponibles en Office 365). Consulte sólo algunas de las cosas en las que falta:

| **Versión de Exchange**                     | **Funciones**                                                                                                                                                                                                                                         |
|------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Exchange 2013                            | Arquitectura simplificada que reduce el número de roles de servidor a tres (buzón de correo, acceso de cliente y transporte perimetral)                                                                                                                                        |
|                                          | Directivas de prevención de pérdida de datos (DLP) que evitan la pérdida de información confidencial                                                                                                                                                                |
|                                          | Experiencia de Outlook Web App mejorada de forma significativa                                                                                                                                                                                                    |
| Exchange 2016                            | *Características de Exchange 2013 y...*                                                                                                                                                                                                                   |
|                                          | Funciones de servidor más sencillas para solo buzones de correo y de transporte perimetral                                                                                                                                                                                   |
|                                          | DLP mejorado junto con la integración con SharePoint                                                                                                                                                                                                  |
|                                          | Resistencia de base de datos mejorada                                                                                                                                                                                                                         |
|                                          | Colaboración en documentos en línea                                                                                                                                                                                                                        |

| **Motivos**                        | **Más información**                                                                                                                                                                                                                                        |
|------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Fecha de finalización del soporte técnico                     | Al igual que Exchange 2010, cada versión de Exchange tiene su propio fin de fecha de soporte técnico:                                                                                                                                                                        |
|                                          | **Exchange 2013** -abril 2023                                                                                                                                                                                                                       |
|                                          | **Exchange 2016** -octubre 2025                                                                                                                                                                                                                     |
|                                          | Al final de la fecha de soporte técnico, lo antes que necesitará realizar otra migración. Abril de 2023 es mucho más cercana a lo que cree.                                                                                                                 |
| Ruta de migración a Exchange 2013 o 2016  | La ruta de migración de Exchange 2010 a una versión más reciente es la misma si elige Exchange 2013 o Exchange 2016:                                                                                                                              |
|                                          | Instalar Exchange 2013 o 2016 en su organización existente de Exchange 2010 mueva los servicios y otra infraestructura a Exchange 2013 o 2016 mueva los buzones de correo y las carpetas públicas a Exchange 2013 o 2016 retirar los servidores de Exchange 2010 restantes  |
| Coexistencia de versiones                      | Al migrar a Exchange 2013 o Exchange 2016, puede instalar cualquier versión en una organización existente de Exchange 2010. Esto le permite instalar uno o varios servidores Exchange 2013 o Exchange 2016 y realizar la migración.             |
| Hardware de servidor                          | Los requisitos de hardware del servidor han cambiado de Exchange 2010. Deberá asegurarse de que el hardware que va a usar es compatible. Puede obtener más información sobre los requisitos de hardware para cada versión aquí:                                      |
|                                          | [Requisitos del sistema de Exchange 2016](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx)                                                                                                                                      |
|                                          | [Requisitos del sistema de Exchange 2013](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx)                                                                                                                                      |
|                                          | Encontrarás que con las mejoras significativas en el rendimiento de Exchange y la potencia de procesamiento y capacidad de almacenamiento aumentada en los nuevos servidores, probablemente necesitarás menos servidores para admitir el mismo número de buzones.                       |
| Versión del sistema operativo                 | Las versiones de sistema operativo mínimas admitidas para cada versión son:                                                                                                                                                                                |
|                                          | **Exchange 2016** Windows Server 2012                                                                                                                                                                                                                |
|                                          | **Exchange 2013** Windows Server 2008 R2 SP1                                                                                                                                                                                                         |
|                                          | Puede encontrar más información acerca del soporte del sistema operativo en la [matriz de compatibilidad de Exchange](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).                                                                        |
| Nivel funcional del bosque de Active Directory | Los niveles de funcionalidad de bosque de Active Directory mínimos admitidos para cada versión son:                                                                                                                                                                |
|                                          | **Exchange 2016** Windows Server 2008 R2 SP1                                                                                                                                                                                                         |
|                                          | **Exchange 2013** Windows Server 2003                                                                                                                                                                                                                |
|                                          | Puede encontrar más información acerca de la compatibilidad del nivel funcional del bosque en la [matriz de compatibilidad de Exchange](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).                                                                 |
| Versiones de cliente de Office                   | Las versiones de cliente de Office mínimas admitidas para cada versión son:                                                                                                                                                                                   |
|                                          | **Exchange 2016** Office 2010 (con las actualizaciones más recientes)                                                                                                                                                                                              |
|                                          | **Exchange 2013** Office 2007 SP3                                                                                                                                                                                                                    |
|                                          | Puede encontrar más información acerca de la compatibilidad de clientes de Office en la [matriz de compatibilidad de Exchange](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).                                                                           |

Puede usar los siguientes recursos para ayudarle con la migración:

- [Asistente para la implementación de Exchange](https://aka.ms/exdeploy)
- Cambios en el esquema de Active Directory para Exchange [2016](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.150%29.aspx)
- Requisitos del sistema para Exchange [2016](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx)
- Requisitos previos para Exchange [2016](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.150%29.aspx)

## <a name="what-if-i-need-help"></a>¿Qué debo hacer si necesito ayuda?

Si va a migrar a Office 365, puede ser elegible para usar nuestro servicio Microsoft FastTrack. FastTrack proporciona los procedimientos recomendados, las herramientas y los recursos para que la migración a Office 365 sea lo más fluida posible. Lo mejor de todo es que tendrá un ingeniero de soporte real que le guiará a través de la migración, desde la planeación y el diseño hasta la migración del último buzón. Si desea saber más sobre FastTrack, eche un vistazo a [Microsoft FastTrack](https://fasttrack.microsoft.com/).

Si surgen problemas durante la migración a Office 365 y no usa FastTrack o migrar a una versión más reciente de Exchange Server, estamos aquí para ayudarle. Estos son algunos de los recursos que puede usar:

- [Comunidad de soporte técnico](https://social.technet.microsoft.com/Forums/office/en-US/home?category=exchangeserver)
- [Soporte al cliente](https://support.microsoft.com/en-us/gp/support-options-for-business)

## <a name="related-topics"></a>Temas relacionados

[Recursos que le ayudarán a actualizar desde los servidores y clientes de Office 2010](https://docs.microsoft.com/en-us/office365/enterprise/upgrade-from-office-2010-servers-and-products)

[Grupo de jubilación de Office (Microsoft Tech Community)](https://go.microsoft.com/fwlink/?linkid=842065)
