---
title: Planeación de la migración y red para Office 365
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
ms.audience: Admin
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
description: Contiene vínculos a información sobre la planeación de la red y las pruebas y migración a Office 365.
ms.openlocfilehash: e2434a65b48c12f38d7371a569ba8e0bc282ae06
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223062"
---
# <a name="network-and-migration-planning-for-office-365"></a>Planeación de la migración y red para Office 365

Este artículo contiene vínculos a información acerca de la planeación y pruebas de red y migración a Office 365.
  
Antes de implementar por primera vez o migrar a Office 365, puede usar la información de estos temas para calcular el ancho de banda que necesita y, a continuación, probar y verificar que tiene suficiente ancho de banda para implementar o migrar a Office 365.

||
|:-----|
| En este artículo forma parte de la [planeación de la red y ajuste del rendimiento de Office 365](https://aka.ms/tune).|

|||
|:-----|:-----|
|![Consulte red de nube de Microsoft para póster arquitectos de empresa](media/3094be9f-2407-4fa5-896d-aa66ef7b9bb9.png)|Para que los pasos para optimizar el rendimiento de la red Office 365 y otras plataformas de nube de Microsoft y los servicios, vea el póster de [Microsoft en la nube de la red para arquitectos de la empresa](https://aka.ms/cloudarchnetworking) . |
   
## <a name="estimate-network-bandwidth-requirements"></a>Estimar los requisitos de ancho de banda de la red
<a name="EstimateBandwidthRequirements"> </a>

Con Office 365 puede aumentar la utilización del circuito de internet de su organización. Es importante determinar si la cantidad de ancho de banda disponible actualmente es suficiente para controlar el aumento estimado una vez que Office 365 es totalmente implementado dejando al menos el 20% capacidad para tratar los más ocupados de días.
  
Para calcular el ancho de banda, siga estos pasos:
  
1. Evaluar el número de clientes que utilizará cada salida de Internet. Dejar que nuestra red multi-terabit controle tanta información de la conexión como sea posible. 
    
2. Determinar qué servicios de Office 365 y características estarán disponibles para los clientes puedan usar. Probablemente tendrá grupos de personas con distintos servicios o perfiles de uso.
    
3. Medir el uso de red para un grupo piloto de los clientes. Asegúrese de que los clientes pilotos son representante de los diferentes perfiles de personas de la organización, así como las distintas ubicaciones geográficas. Puede comprobar los resultados obtenidos con nuestros antiguo calculadoras de forma entre para [Exchange ](https://go.microsoft.com/fwlink/p/?LinkId=321550)y [Skype para la empresa](https://go.microsoft.com/fwlink/p/?LinkId=321551) o el [caso práctico](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365) que se realizaron en nuestra propia red. 
    
4. Utilice las medidas del grupo piloto para extrapolar las necesidades de toda la organización y volver a probar para validar las estimaciones antes de realizar cualquier cambio en la red.
    
## <a name="test-your-existing-network"></a>Probar la red existente
<a name="calculators"> </a>

 **Herramientas de red.** Probar y validar el ancho de banda de Internet para determinar las restricciones de descarga, carga y latencia. Estas herramientas le ayudará a determinar las capacidades de la red para la migración, así como una vez que está totalmente implementado. 
  
- [Analizador de mensaje de Microsoft](https://technet.microsoft.com/library/jj649776.aspx): mensaje Analyzer es una herramienta eficaz para solucionar los problemas de red. Analizador de mensaje captura, muestra y analiza el tráfico de mensajería basada en el protocolo y los mensajes del sistema. Analizador de mensaje también permite importar, agregadas y analizar datos de archivos de registro y seguimiento.
    
- [Analizador de conectividad remota de Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=517243): comprueba la conectividad en el entorno de Exchange Online.
    
- Use [el Asistente de recuperación para Office 365 y de soporte técnico de Microsoft](https://diagnostics.office.com/#/Download?env=SOC) para solucionar problemas de Outlook y Office 365. 
    
## <a name="best-practices-for-network-planning-and-improving-migration-performance-for-office-365"></a>Best practices for network planning and improving migration performance for Office 365
<a name="BestPractices"> </a>

Profundizar un poco más en estos procedimientos recomendados para obtener más información acerca de cómo mejorar la experiencia de Office 365.
  
1. ¿Desea empezar a ayudar a los usuarios inmediatamente? Para obtener sugerencias sobre el uso de Office 365, incluidos SharePoint Online, Exchange Online y Lync Online, cuando la red no está cooperación acaba, vea [procedimientos recomendados para usar Office 365 en una red lenta](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) . Este artículo contiene vínculos a las cargas de contenido de TechNet y Support.office.com para optimizar su experiencia de Office 365 e incluye información en formas sencillas para personalizar las páginas web y cómo establecer la configuración de Internet Explorer para la mejor experiencia de Office 365. 
    
2. Lea los [Principios de conectividad de red de Office 365](https://aka.ms/o365networkingprinciples) para comprender los principios de conectividad para administrar el tráfico de Office 365 y obtener el mejor rendimiento posible de forma segura. En este artículo le ayudará a comprender las instrucciones más reciente para optimizar de forma segura conectividad de red de Office 365. 
    
3. Mejorar el rendimiento de la migración de correo mediante la administración de cuidadosamente la programación de actualizaciones de Windows. Puede actualizar los equipos cliente en lotes y asegúrese de que todos los equipos cliente se actualicen antes de migrar a Office 365 para regular el uso de ancho de banda de red. Para obtener más información, vea [actualizar de forma manual y configurar escritorios de Office 365 para obtener las actualizaciones más recientes](https://support.microsoft.com/gp/office-2013-365-update).
    
4. El tráfico de red de Office 365 funciona mejor cuando se trata como un servicio de Internet de confianza y permitidos para el desvío de gran parte de la digitalización que algunas organizaciones se coloque en el tráfico de red a los servicios de Internet no son de confianza y filtrado tradicional. Normalmente, esto incluye quitar saliente de procesamiento como la autenticación de usuario de proxy y la inspección de paquetes, así como asegurarse de salida local a Internet con la traducción de direcciones de red (NAT) adecuada y suficiente capacidad de ancho de banda para controlar el mayor solicitudes de red. Hacer referencia a [los extremos de administración de Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)para obtener instrucciones adicionales sobre la configuración de la red para administrar Office 365 como un servicio de Internet de confianza en la red.
    
1. Asegúrese de que [los extremos de administración de Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a). El tráfico adicional que se va a Office 365 da como resultado un aumento de conexiones de proxy de salida, así como un aumento del tráfico seguro a través de TLS/SSL.
    
2. Si los servidores proxy de salida requieren autenticación de usuario puede experimentar una conexión lenta o una pérdida de funcionalidad. Omitir el requisito de autenticación para los dominios de Office 365 puede reducir esta sobrecarga.
    
3. Si tiene gran cantidad de calendarios y buzones compartidos, puede ver un incremento en la cantidad de conexiones desde Outlook a Exchange. Por ejemplo, el cliente de Outlook puede abrir hasta un máximo de dos conexiones adicionales para cada calendario compartido en uso. En este caso, asegúrese de que el proxy de salida pueda manejar las conexiones o esquive el proxy para las conexiones a Office 365 para Outlook.
    
4. Determinar el número máximo de dispositivos admitidos para una dirección IP pública y cómo equilibrar la carga entre varias direcciones IP. Para obtener más información, vea [admitir NAT con Office 365](nat-support-with-office-365.md).
    
5. Si se está inspeccionando las conexiones salientes desde los equipos de la red, omitiendo este filtrado a los dominios de Office 365 mejorará conectividad y rendimiento. Además, omitir la inspección de salida a menudo elimina la necesidad de una sola salida de Internet y permite la salida de Internet local para Office 365 dirigido a las solicitudes de red.
    
6. Algunos clientes encontrarán la configuración de la red interna puede afectar al rendimiento. Negociación automática o la detección automática de red de configuración como el tamaño de transmisión máxima (MTU) de la unidad, y las rutas debajo del nivel óptimas a Internet son sitios comunes para buscar.
    
## <a name="network-planning-reference-for-office-365"></a>Referencia de planeación de red para Office 365
<a name="NetReference"> </a>

Estos temas contienen información detallada de referencia de red de Office 365.
  
- [Administración de extremos de Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
    
- [Conectividad de clientes](client-connectivity.md)
    
- [Redes de entrega de contenido](content-delivery-networks.md)
    
- [Registros de sistema de nombres de dominio externos para Office 365](external-domain-name-system-records.md)
    
- [Compatibilidad con IPv6 en servicios de Office 365](ipv6-support.md)
    
- [Principios de conectividad de red de Office 365](https://aka.ms/o365networkingprinciples)
    
- [Microsoft Virtual Academy: Administración de rendimiento Office 365](https://mva.microsoft.com/en-us/training-courses/office-365-performance-management-8416)
    
- [Redes de vídeo de Office 365 preguntas más frecuentes (P+F)](office-365-video-networking-faq.md)
    
- [Planificación de dispositivos de red que se conecten a servicios de Office 365](plan-for-network-devices.md)
    
- [Asesores de implementación para servicios de Office 365](deployment-advisors-for-office-365.md)
    

