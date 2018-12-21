---
title: Final de Exchange 2010 de guía básica de soporte técnico
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
description: Exchange 2010 se está acercando a fin de soporte. Use esta guía de planeación como una guía para preparar la actualización a Exchange Online o una versión más reciente de Exchange Server local.
ms.openlocfilehash: d9dcc2120f549c55fedc78483689dbded0a4464f
ms.sourcegitcommit: b45ad32a0a421d9834424e02838b6f941c259b9b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2018
ms.locfileid: "27382701"
---
# <a name="exchange-2010-end-of-support-roadmap"></a>Final de Exchange 2010 de guía básica de soporte técnico

En **el 14 de enero de 2020**, Exchange Server 2010 se llegar a fin de soporte. Si aún no ha empezado la migración desde Exchange 2010 a Office 365 o Exchange 2016, ahora es el momento de empezar la planificación.

## <a name="what-does-end-of-support-mean"></a>¿Qué final hace de Media de soporte técnico?

Exchange Server, al igual que casi todos los productos de Microsoft, tiene un ciclo de vida de soporte técnico durante el cual se proporcionan las nuevas características, correcciones de errores, las revisiones de seguridad y así sucesivamente. Este ciclo de vida dura normalmente de 10 años desde la fecha de lanzamiento del producto, y el final de este ciclo de vida se conoce como fin del producto del soporte. Cuando Exchange 2010 alcanza su fin del soporte en el 14 de enero de 2020, Microsoft ya no proporcionará:

- Soporte técnico para problemas que puedan surgir;
- Correcciones de errores para los problemas que se descubren y que puede afectar a la estabilidad y la facilidad de uso del servidor;
- Revisiones de seguridad para las vulnerabilidades de seguridad que se descubren y que puede hacer el servidor vulnerable a infracciones de seguridad;
- Actualizaciones de zona horaria.

La instalación de Exchange 2010 continuará ejecutándose después de esta fecha. Sin embargo, debido a los cambios enumerados anteriormente, se recomienda encarecidamente que migre desde Exchange 2010 tan pronto como sea posible.

Para obtener más información acerca de los servidores de Office 2010 llega al final de soporte técnico, vea [recursos para ayudarle a actualizar de Office 2010 servidores y clientes](https://docs.microsoft.com/en-us/office365/enterprise/upgrade-from-office-2010-servers-and-products).

## <a name="what-are-my-options"></a>¿Cuáles son las opciones de mi?

Con Exchange 2010 llegando a su fin de soporte, esto es un buen momento para examinar las opciones y preparar un plan de migración. Puedes:

- Migrar completamente a Office 365. Migrar buzones de correo con híbrida traslado, mínima o migración híbrida completa, a continuación, quitar local los servidores de Exchange y Active Directory.
- Migrar sus servidores Exchange 2010 a Exchange 2016 en los servidores locales.

> [!IMPORTANT]
> Si la organización decide migrar buzones a Office 365 pero se propone mantener la sincronización de directorios o Azure Connect de AD en contexto para continuar la administración de cuentas de usuario de Active Directory local, debe mantener al menos un Exchange server local. Si se quita el último servidor de Exchange, no podrá realizar cambios en los destinatarios de Exchange en Exchange Online. Esto es debido a que el origen de autoridad permanece en su Active Directory local y los cambios que necesite realizarse allí. En este escenario, tiene las siguientes opciones:

- (**Recomendado**) Si puede migrar los buzones de correo a Office 365 y actualizar los servidores por el 14 de enero de 2020, use Exchange 2010 para conectarse a Office 365 y migrar buzones de correo. A continuación, migrar Exchange 2010 a Exchange 2016 y dar de baja los servidores de Exchange 2010 restantes.
- Si no se puede completar la migración de buzones de correo y actualización del servidor local mediante el 14 de enero de 2020, actualizar los servidores de Exchange 2010 local a Exchange 2016 en primer lugar, a continuación, use Exchange 2016 para conectarse a Office 365 y migrar buzones de correo.

> [!NOTE]
> Mientras un poco más complicado, se pueden migrar buzones a Office 365 durante la migración de los servidores de Exchange 2010 local a Exchange 2016.

En las secciones siguientes exploración cada opción con más detalle.

## <a name="migrate-to-office-365"></a>Migrar a Office 365

Migrar su correo electrónico a Office 365 es la opción más sencilla y los procedimientos que le ayudarán a retirar su implementación de Exchange 2010. Con una migración a Office 365, puede realizar un único salto de tecnología antigua a las características de última generación, como:

- Capacidades de cumplimiento de normas, como las directivas de retención en contexto y la suspensión por litigio, en contexto exhibición de documentos electrónicos y mucho más;
- Equipos de Microsoft;
- Power BI;
- Bandeja de entrada reducido;
- Profundizar análisis;

Office 365 también obtiene nuevas características y experiencias de primera y usted y los usuarios normalmente pueden empezar utilizar de inmediato. Además de las características nuevas, no tendrá que preocuparse acerca de:

- Compra y el mantenimiento de hardware;
- Prestando para calefacción y refrigeración de los servidores;
- Mantener actualizados en las revisiones de seguridad, productos y zona horaria;
- Mantenimiento de almacenamiento de información y software para satisfacer los requisitos de cumplimiento de normas;
- Actualizar a una nueva versión de Exchange - está siempre en la versión más reciente de Exchange en Office 365.

### <a name="how-should-i-migrate-to-office-365"></a>¿Cómo debo migrar a Office 365?

Dependiendo de la organización, tiene varias opciones que le ayudará a empezar a Office 365. Al elegir una opción de migración, debe tener en cuenta algunas cosas como el número de puestos o que tenga que mover los buzones de correo, ¿durante cuánto tiempo desea que la migración a último y si necesita una integración perfecta entre su instalación local y Office 365 durante la migración. Esta tabla muestra las opciones de migración y los factores más importantes que determinan el método que va a utilizar.

| **Opción de migración**     | **Tamaño de la organización** | **Duration**        |
|--------------------------|-----------------------|---------------------|
| Migración total        | Menos de 150 puestos  | Una semana o menos      |
| Migración híbrida mínima | Menos de 150 puestos  | Unas cuantas semanas o menos |
| Migración completa híbrida    | Más de 150 puestos   | Unas cuantas semanas o más |

En las secciones siguientes proporcionan una visión general de estos métodos. Desproteger [Decide en una ruta de migración](https://support.office.com/en-us/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27) para conocer los detalles de cada método.

### <a name="cutover-migration"></a>Migración total

Migración de transferencia es donde, en un previa a la fecha y hora seleccionadas, se migra el todos los buzones de correo, grupos de distribución, contactos y así sucesivamente, a Office 365; Cuando haya terminado, podrá apagar los servidores de Exchange local y empezar a usar Office 365 exclusivamente.

El método de migración de traslado es ideal para las organizaciones pequeñas que no tengan muy muchos buzones, desea obtener acceso rápidamente a Office 365 y no desea abordar los problemas con algunas de la complejidad de los otros métodos. Pero que también un poco limitado porque se debería poder finalizar en una semana o menos y, ya que requiere que los usuarios volver a configurar los perfiles de Outlook. Mientras que la migración de traslado puede controlar hasta 2.000 buzones de correo, se recomienda que migrar un máximo de 150 buzones con este método. Si intenta migrar los buzones de más de 150, podría ejecutar agotó el tiempo para transferir todos los buzones antes de la fecha límite de y el soporte de TI puede obtener personal sobrecargado ayudar a los usuarios volver a configurar Outlook.

Si está pensando acerca de cómo realizar una migración de traslado, presentamos algunas cuestiones que tener en tenga en cuenta:

- Office 365 será necesario para conectarse a los servidores de Exchange 2010 con Outlook en cualquier lugar a través del puerto TCP 443;
- Todos los buzones locales se moverán a Office 365;
- Necesitará una cuenta de administrador local que tiene acceso para leer el contenido de los buzones de los usuarios;
- La Exchange 2010 aceptado dominios que desea usar en Office 365 deben agregarse como dominios verificados en el servicio;
- Entre el tiempo de inicio de la migración y cuando comience la fase de finalización, Office 365 se sincronizarán periódicamente los buzones locales y Office 365. Esto permite a completar la migración sin preocuparse por correo electrónico que se quede en los buzones de correo local;
- Los usuarios recibirán nuevas contraseñas temporales para su cuenta de Office 365 que necesitan cambiar cuando inician sesión en sus buzones de correo por primera vez;
- Necesitará una licencia de Office 365 que incluye Exchange Online para cada buzón de usuario que migre;
- Los usuarios necesitan configurar un nuevo perfil de Outlook en cada uno de sus dispositivos y descargar su correo electrónico de nuevo. La cantidad de correo electrónico que Outlook descargará puede variar. Para obtener más información, eche un vistazo de [cambiar cuánto correo para mantener sin conexión](https://support.office.com/en-us/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&rs=en-US&ad=US&fromAR=1).

Para obtener más información acerca de la migración de traslado, eche un vistazo:

- [Lo que necesita saber acerca de una migración de transferencia de correo electrónico a Office 365](https://support.office.com/en-us/article/What-you-need-to-know-about-a-cutover-email-migration-to-Office-365-961978ef-f434-472d-a811-1801733869da)
- [Realizar una migración de transferencia de correo electrónico a Office 365](https://support.office.com/en-us/article/Perform-a-cutover-migration-of-email-to-Office-365-9496e93c-1e59-41a8-9bb3-6e8df0cd81b4)

### <a name="minimal-hybrid-migration"></a>Migración híbrida mínima

Híbrido mínima o express, migración es uno en el que tiene unos cientos de buzones que desea migrar a Office 365, puede completar la migración dentro de un par de semanas y no es necesario cualquiera de las características de migración híbrida avanzadas al igual que el calendario compartido de la información de disponibilidad información.

Migración híbrida mínimo es ideal para las organizaciones que necesitan para tomar más tiempo para migrar sus buzones de correo a Office 365, pero aún plan para completar la migración dentro de un par de semanas. Obtener algunas de las ventajas de la migración completa híbrida más avanzada sin muchas de la complejidad. Puede controlar cuántos y qué, buzones de correo se migran en un momento dado; Buzones de correo de Office 365 se creará con el nombre de usuario y las contraseñas de sus cuentas locales; y, a diferencia de las migraciones de transferencia, los usuarios no será necesario volver a crear sus perfiles de Outlook.

Si está pensando acerca de cómo realizar la migración híbrida mínimo, a continuación presentamos algunas cosas que se deben considerar:

- Necesita realizar una sincronización de directorios única entre los servidores de Active Directory local y Office 365;
- Los usuarios podrán iniciar sesión en su buzón de Office 365 con el mismo nombre de usuario y contraseña que se estaban utilizando cuando se migró su buzón;
- Necesitará una licencia de Office 365 que incluye Exchange Online para cada buzón de usuario que migre;
- Los usuarios no es necesario configurar un nuevo perfil de Outlook en la mayoría de sus dispositivos (algunos teléfonos Android más antiguos es posible que necesite un nuevo perfil) y no es necesario volver a descargar su correo electrónico.

Para obtener más información acerca de la migración híbrida mínima, eche un vistazo a [Uso híbrido mínima para migrar rápidamente los buzones de Exchange a Office 365](https://support.office.com/article/Use-Minimal-Hybrid-to-quickly-migrate-Exchange-mailboxes-to-Office-365-fdecceed-0702-4af3-85be-f2a0013937ef)

### <a name="full-hybrid"></a>Híbrido completa

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

- Migraciones híbridas completa no están adaptadas a todos los tipos de organizaciones. Debido a la complejidad de migraciones híbridas completa, las organizaciones con unos pocos cientos de buzones normalmente no ven las ventajas que justifican el esfuerzo y el costo necesarios para configurar una lista. Si esto suena como su organización, se recomienda que tenga en cuenta las migraciones de transferencia o mínima híbrida en su lugar;
- Necesita configurar la sincronización de directorios con Azure Active Directory Connect (AADConnect) entre los servidores de Active Directory local y Office 365;
- Los usuarios podrán iniciar sesión en su buzón de Office 365 con el mismo nombre de usuario y contraseña que se utilizan cuando inician sesión en la red local (requiere Azure Active Directory conectarse con la sincronización de contraseña o los servicios de federación de Active Directory);
- Necesitará una licencia de Office 365 que incluye Exchange Online para cada buzón de usuario que migre;
- Los usuarios no es necesario configurar un nuevo perfil de Outlook en la mayoría de sus dispositivos (algunos teléfonos Android más antiguos es posible que necesite un nuevo perfil) y no es necesario volver a descargar su correo electrónico.

> [!IMPORTANT]
> Si la organización decide migrar buzones a Office 365 pero se propone mantener la sincronización de directorios o Azure Connect de AD en contexto para continuar la administración de cuentas de usuario de Active Directory local, debe mantener al menos un Exchange server local. Si se quita el último servidor de Exchange, no podrá realizar cambios en los destinatarios de Exchange en Exchange Online. Esto es debido a que el origen de autoridad permanece en su Active Directory local y los cambios que necesite realizarse allí.

Si un sonidos de migración híbrida completa adecuada para usted, eche un vistazo a los siguientes recursos para ayudarle con la migración:

- [Asistente de implementación de Exchange](https://aka.ms/exdeploy)
- [Implementaciones híbridas de Exchange Server](https://technet.microsoft.com/en-us/library/jj200581%28v=exchg.150%29.aspx)
- [Asistente de configuración híbrida](https://technet.microsoft.com/en-us/library/hh529921%28v=exchg.150%29.aspx)
- [Preguntas más frecuentes acerca del asistente de configuración híbrida](https://technet.microsoft.com/en-us/library/mt488940%28v=exchg.150%29.aspx)
- [Requisitos previos para la implementación híbrida](https://technet.microsoft.com/en-us/library/hh534377%28v=exchg.150%29.aspx)

## <a name="upgrade-to-a-newer-version-of-exchange-server-on-premises"></a>Actualizar a una versión más reciente de Exchange Server local

Aunque creemos encarecidamente que puede lograr la mejor experiencia de usuario y valor al migrar completamente a Office 365, también sabemos que algunas organizaciones necesitan mantener algunos servidores de Exchange local. Esto podría ser debido a los requisitos legales, para garantizar los datos no se almacenan en un centro de datos que se encuentra en otro país, o podría ser debido a que tiene una configuración única o los requisitos que no se cumplen en la nube, o podría ser simplemente que necesita a Exchange administrar los buzones de correo en la nube debido a que aún usar Active Directory local. En cualquier caso para que usted elija o necesita mantener Exchange local, debe asegurarse de su entorno de Exchange 2010 se actualiza al menos Exchange 2013 o 2016 de Exchange y Exchange 2010 se ha quitado antes de la fecha de fin de soporte.

Para la mejor experiencia, se recomienda que actualice su entorno local restantes a 2016 de Exchange. No es necesario instalar Exchange Server 2013 si desea ir directamente desde Exchange Server 2010 a Exchange Server 2016.

Exchange 2016 incluye todas las características y los avances que se incluye con las versiones anteriores de Exchange, y más aproxime la experiencia disponible con Office 365 (aunque algunas características sólo están disponibles en Office 365). Desproteger sólo algunas de las cosas que ha sido falta participar en:

| **Versión de Exchange**                     | **Características**                                                                                                                                                                                                                                         |
|------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Exchange 2013                            | Arquitectura simplificada reduce el número de roles de servidor a tres (transporte perimetral del buzón de correo, acceso de cliente,)                                                                                                                                        |
|                                          | Directivas de prevención de pérdida de datos (DLP) que ayudan a mantener la pérdida de información confidencial                                                                                                                                                                |
|                                          | Significativamente experiencia mejorada de Outlook Web App                                                                                                                                                                                                    |
| Exchange 2016                            | *Las características de Exchange 2013 y...*                                                                                                                                                                                                                   |
|                                          | Aún más los roles de servidor simplificada para acaba de buzón de correo y transporte perimetral                                                                                                                                                                                   |
|                                          | DLP mejorada junto con la integración con SharePoint                                                                                                                                                                                                  |
|                                          | Resistencia mejorada de la base de datos                                                                                                                                                                                                                         |
|                                          | Colaboración en documentos en línea                                                                                                                                                                                                                        |

| **Consideración**                        | **Obtener más información**                                                                                                                                                                                                                                        |
|------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Final de fechas de soporte técnico                     | Al igual que Exchange 2010, cada versión de Exchange tiene su propio final de la fecha de soporte técnico:                                                                                                                                                                        |
|                                          | **Exchange 2013** - de 2023 de abril                                                                                                                                                                                                                       |
|                                          | **Exchange 2016** - de 2025 de octubre                                                                                                                                                                                                                     |
|                                          | Cuanto antes el final de la fecha de soporte, antes debe realizar otra migración. Abril de 2023 es mucho más cerca de lo que se imagina!                                                                                                                 |
| Ruta de migración a Exchange 2013 o 2016  | La ruta de migración de Exchange 2010 a una versión más reciente es el mismo, puede optar por Exchange 2013 o 2016 de Exchange:                                                                                                                              |
|                                          | Instalar Exchange 2013 o 2016 en los servicios de movimiento de organización de Exchange 2010 existentes y otra infraestructura de Exchange 2013 o 2016 mover buzones y carpetas públicas a Exchange 2013 o retiro de 2016 resto de servidores de Exchange 2010  |
| Coexistencia de versión                      | Al migrar a Exchange 2013 o 2016 de Exchange, puede instalar cualquiera de las versiones en una organización existente de Exchange 2010. Esto le permite instalar a uno o varios servidores de Exchange 2013 o 2016 de Exchange y realizar la migración.             |
| Hardware de servidor                          | Han cambiado los requisitos de hardware de servidor de Exchange 2010. Necesitará para asegurarse de que el hardware que se va a usar es compatible. Puede encontrar más información acerca de los requisitos de hardware para cada versión aquí:                                      |
|                                          | [Requisitos del sistema de Exchange 2016](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx)                                                                                                                                      |
|                                          | [Requisitos del sistema de Exchange 2013](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx)                                                                                                                                      |
|                                          | Encontrará que con las mejoras significativas en el rendimiento de Exchange y la mayor eficacia de los sistemas y la capacidad de almacenamiento en los servidores más recientes, que probablemente tendrá menos servidores para admitir el mismo número de buzones de correo.                       |
| Versión del sistema operativo                 | Las versiones de sistema operativo mínimo compatible para cada versión son:                                                                                                                                                                                |
|                                          | **Exchange 2016** Windows Server 2012                                                                                                                                                                                                                |
|                                          | **Exchange 2013** Windows Server 2008 R2 SP1                                                                                                                                                                                                         |
|                                          | Puede encontrar más información acerca de la compatibilidad con el sistema operativo en la [Matriz de compatibilidad de Exchange](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).                                                                        |
| Nivel funcional de bosque de Active Directory | El mínimo compatible Active Directory niveles funcionales del bosque para cada versión son:                                                                                                                                                                |
|                                          | **Exchange 2016** Windows Server 2008 R2 SP1                                                                                                                                                                                                         |
|                                          | **Exchange 2013** Windows Server 2003                                                                                                                                                                                                                |
|                                          | Puede encontrar más información acerca de la compatibilidad de nivel funcional de bosque en [Matriz de compatibilidad de Exchange](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).                                                                 |
| Versiones de cliente de Office                   | Las versiones de cliente de Office compatibles como mínimas para cada versión son:                                                                                                                                                                                   |
|                                          | **Exchange 2016** Office 2010 (con las actualizaciones más recientes)                                                                                                                                                                                              |
|                                          | **Exchange 2013** SP3 de 2007 Office                                                                                                                                                                                                                    |
|                                          | Puede encontrar más información acerca de la compatibilidad con clientes de Office en la [Matriz de compatibilidad de Exchange](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).                                                                           |

Puede usar los siguientes recursos para ayudarle con la migración:

- [Asistente de implementación de Exchange](https://aka.ms/exdeploy)
- Cambios de esquema de Active Directory para Exchange [2016](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.160%29.aspx), [de 2013](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.150%29.aspx)
- Requisitos del sistema para Exchange [2016](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx), [de 2013](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx)
- Requisitos previos para Exchange [2016](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.160%29.aspx), [de 2013](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.150%29.aspx)

## <a name="what-if-i-need-help"></a>¿Qué ocurre si necesita ayuda?

Si realiza la migración a Office 365, es posible que optan a utilizar nuestro servicio Microsoft FastTrack. FastTrack proporciona procedimientos recomendados, herramientas y recursos para realizar la migración a Office 365 es tan transparente como sea posible. Lo mejor de todo, tendrá un ingeniero de soporte real que le guiarán a través de la migración, desde la planificación y diseño completamente a migrar su buzón de correo última. Si desea saber más acerca de FastTrack, eche un vistazo en [FastTrack de Microsoft](https://fasttrack.microsoft.com/).

Si se ejecuta en los problemas durante la migración a Office 365 y que no esté utilizando FastTrack o la migración a una versión más reciente de Exchange Server, ya que estamos aquí para ayudar a. A continuación presentamos algunos recursos que puede utilizar:

- [Comunidad técnica](https://social.technet.microsoft.com/Forums/office/en-US/home?category=exchangeserver)
- [Soporte al cliente](https://support.microsoft.com/en-us/gp/support-options-for-business)

## <a name="related-topics"></a>Temas relacionados

[Recursos que le ayudarán a actualizar de Office 2010 de los clientes y servidores](https://docs.microsoft.com/en-us/office365/enterprise/upgrade-from-office-2010-servers-and-products)

[Grupo de retirada de Office (Microsoft Tech Comunidad)](https://go.microsoft.com/fwlink/?linkid=842065)
