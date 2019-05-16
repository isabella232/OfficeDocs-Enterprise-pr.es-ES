---
title: Planeación de la migración y la red para Office 365
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132
description: Contiene vínculos a información acerca de la planeación y las pruebas de red, y la migración a Office 365.
ms.openlocfilehash: a32a8584f1aada7e2b82451d520f72bb7577bc4b
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069926"
---
# <a name="network-and-migration-planning-for-office-365"></a>Planeación de la migración y la red para Office 365

Este artículo contiene vínculos a información acerca de la planeación y las pruebas de red, y la migración a Office 365.
  
Antes de implementar por primera vez o migrar a Office 365, puede usar la información de estos temas para calcular el ancho de banda que necesita y, después, para probar y comprobar que tiene suficiente ancho de banda para implementar o migrar a Office 365.

||
|:-----|
| Este artículo forma parte de la planeación de [red y el ajuste del rendimiento de Office 365](https://aka.ms/tune).|

|||
|:-----|:-----|
|![Consulte el póster Microsoft Cloud Networking for Enterprise Architects](media/3094be9f-2407-4fa5-896d-aa66ef7b9bb9.png)|Para conocer los pasos para optimizar la red para Office 365 y otras plataformas y servicios en la nube de Microsoft, consulte el póster [Microsoft Cloud Networking for Enterprise Architects](https://aka.ms/cloudarchnetworking) . |
   
## <a name="estimate-network-bandwidth-requirements"></a>Estimación de los requisitos de ancho de banda de red
<a name="EstimateBandwidthRequirements"> </a>

El uso de Office 365 puede aumentar la utilización del circuito de Internet de su organización. Es importante determinar si la cantidad de ancho de banda disponible actualmente es suficiente para controlar el aumento estimado una vez que Office 365 se ha implementado completamente y que tiene al menos un 20% de capacidad para manejar los días más ocupados.
  
Para calcular el ancho de banda, siga estos pasos:
  
1. Evalúe el número de clientes que usarán cada salida de Internet. Permita que nuestro controlador de red multiterabit sea la mayor parte posible de la conexión. 
    
2. Determine qué servicios y características de Office 365 estarán disponibles para que los usen los clientes. Probablemente tendrá grupos de personas con diferentes servicios o perfiles de uso.
    
3. Mida el uso de red para un grupo piloto de clientes. Asegúrese de que los clientes piloto son representativos de los diferentes perfiles de las personas de la organización, así como las distintas ubicaciones geográficas. Puede realizar una comprobación cruzada de sus resultados con respecto a nuestras antiguas calculadoras para [Exchange ](https://go.microsoft.com/fwlink/p/?LinkId=321550)y [Skype empresarial](https://go.microsoft.com/fwlink/p/?LinkId=321551) , o al [caso práctico](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365) que hicimos en nuestra propia red. 
    
4. Use las medidas del grupo piloto para extrapolar las necesidades de toda la organización y vuelva a probar para validar las estimaciones antes de realizar cambios en la red.
    
## <a name="test-your-existing-network"></a>Probar la red existente
<a name="calculators"> </a>

 **Herramientas de red.** Pruebe y valide el ancho de banda de Internet para determinar las restricciones de descarga, carga y latencia. Estas herramientas le ayudarán a determinar las capacidades de su red para la migración, así como una vez que se haya implementado por completo. 
  
- [Analizador de mensajes de Microsoft](https://technet.microsoft.com/library/jj649776.aspx): analizador de mensajes es una herramienta eficaz para la solución de problemas de red. El analizador de mensajes captura, muestra y analiza el tráfico de mensajería basado en protocolo y los mensajes del sistema. El analizador de mensajes también le permite importar, agregar y analizar datos de archivos de registro y de seguimiento.
    
- [Analizador de conectividad remota de Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=517243): comprueba la conectividad en su entorno de Exchange Online.
    
- Use el [Asistente para soporte y recuperación de Microsoft para Office 365](https://diagnostics.office.com/#/Download?env=SOC) para solucionar problemas de Outlook y Office 365. 
    
## <a name="best-practices-for-network-planning-and-improving-migration-performance-for-office-365"></a>Procedimientos recomendados para planear la red y mejorar el rendimiento de la migración para Office 365
<a name="BestPractices"> </a>

Profundizar un poco más en estos procedimientos recomendados para obtener más información sobre cómo mejorar la experiencia de Office 365.
  
1. ¿Desea empezar a ayudar a los usuarios de inmediato? Consulte los [procedimientos recomendados para usar office 365 en una red lenta](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) para obtener sugerencias sobre cómo usar Office 365, incluidos SharePoint Online, Exchange Online y Lync Online, cuando la red no está cooperando. En este artículo se proporciona información sobre la carga de contenido en TechNet y Support.office.com para optimizar la experiencia de Office 365 y se incluye información sobre métodos sencillos para personalizar las páginas web y cómo establecer la configuración de Internet Explorer para la mejor experiencia de Office 365. 
    
2. Lea los [principios de conectividad de red de office 365](https://aka.ms/o365networkingprinciples) para comprender los principios de conectividad para administrar de forma segura el tráfico de Office 365 y obtener el mejor rendimiento posible. Este artículo le ayudará a comprender las instrucciones más recientes para optimizar de manera segura la conectividad de red de Office 365. 
    
3. Mejorar el rendimiento de la migración de correo mediante la administración minuciosa de la programación de actualizaciones de Windows. Puede actualizar los equipos cliente en lotes y asegurarse de que se actualizan todos los equipos cliente antes de migrar a Office 365 para regular el uso del ancho de banda de red. Para obtener más información, vea [actualizar manualmente y configurar escritorios para Office 365 para obtener las actualizaciones más recientes](https://support.microsoft.com/gp/office-2013-365-update).
    
4. El tráfico de red de Office 365 funciona mejor cuando se trata como un servicio de Internet de confianza y permite omitir la mayor parte del filtrado y el análisis tradicionales que algunas organizaciones colocan en el tráfico de red a los servicios de Internet que no son de confianza. Esto suele incluir la eliminación del procesamiento de salida, como la autenticación de usuario de proxy y la inspección de paquetes, además de garantizar la salida local a Internet con la traducción de direcciones de red (NAT) adecuada y la capacidad de ancho de banda suficiente para controlar el mayor solicitudes de red. Consulte [Administración de puntos de conexión de office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)para obtener más información sobre cómo configurar la red para administrar Office 365 como un servicio de Internet de confianza en la red.
    
1. Garantizar la [Administración de puntos de conexión de Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a). El tráfico adicional dirigido a Office 365 da como resultado un aumento de las conexiones de proxy salientes, así como un aumento en el tráfico seguro a través de TLS/SSL.
    
2. Si los servidores proxy salientes requieren la autenticación del usuario, puede experimentar una conectividad lenta o una pérdida de funcionalidad. Omitir el requisito de autenticación para los dominios de Office 365 puede reducir esta sobrecarga.
    
3. Si tiene un gran número de calendarios y buzones compartidos, es posible que vea un aumento en el número de conexiones de Outlook a Exchange. Por ejemplo, el cliente de Outlook puede abrir hasta dos conexiones adicionales para cada calendario compartido en uso. En esta situación, asegúrese de que el proxy de salida puede controlar las conexiones, o bien, pase por alto el proxy para las conexiones a Office 365 para Outlook.
    
4. Determine el número máximo de dispositivos admitidos para una dirección IP pública y cómo equilibrar la carga entre varias direcciones IP. Para obtener más información, consulte [Compatibilidad de NAT con Office 365](nat-support-with-office-365.md).
    
5. Si va a inspeccionar las conexiones de salida de los equipos de la red, al omitir este filtrado a los dominios de Office 365 mejorará la conectividad y el rendimiento. Además, al omitir la inspección saliente, a menudo se elimina la necesidad de una sola salida de Internet y se habilita la salida de Internet local para las solicitudes de red dirigidas a Office 365.
    
6. Algunos clientes encuentran una configuración de red interna puede afectar al rendimiento. La configuración como el tamaño de la unidad de transmisión máxima (MTU), la autodetección de red o la detección automática, y las rutas secundarias subóptimas a Internet son lugares comunes en los que buscar.
    
## <a name="network-planning-reference-for-office-365"></a>Referencia de planeación de red para Office 365
<a name="NetReference"> </a>

Estos temas contienen información detallada de referencia de la red de Office 365.
  
- [Administrar puntos de conexión de Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
    
- [Conectividad de clientes](client-connectivity.md)
    
- [Redes de entrega de contenido](content-delivery-networks.md)
    
- [Registros externos del Sistema de nombres de dominio para Office 365](external-domain-name-system-records.md)
    
- [Compatibilidad con IPv6 en servicios de Office 365](ipv6-support.md)
    
- [Principios de conectividad de red de Office 365](https://aka.ms/o365networkingprinciples)
    
- [Preguntas más frecuentes (FAQ) de Office 365 video Networking](office-365-video-networking-faq.md)
    
- [Planificación de dispositivos de red que se conecten a servicios de Office 365](plan-for-network-devices.md)
    
- [Asesores de implementación para servicios de Office 365](deployment-advisors-for-office-365.md)
    

