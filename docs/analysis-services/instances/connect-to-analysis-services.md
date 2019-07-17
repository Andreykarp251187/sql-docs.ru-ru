---
title: Подключение к службам Analysis Services | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 84a37af402d691ee7507fe923a6ae765b622631f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68181886"
---
# <a name="connect-to-analysis-services"></a>Подключение к службам Analysis Services
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  В этом разделе содержатся сведения о свойствах строки подключения, клиентских библиотеках, используемых для подключений, методах проверки подлинности, поддерживаемых службами Analysis Services, настройке и отмене подключений перед переводом сервера в автономный режим.  

Дополнительные сведения о подключении к службам Azure Analysis Services, см. в разделе [соединиться с сервером](https://docs.microsoft.com/azure/analysis-services/analysis-services-connect).
  
## <a name="analysis-services-connections"></a>Подключение к службами Analysis Services  
 В службах Analysis Services в качестве протокола связи используется сетевой протокол TCP и XML для аналитики (XMLA). На самом низком уровне все клиентские библиотеки, предоставленные с помощью служб Analysis Services, реализуют схему связи "XMLA по TCP". Несмотря на возможность создания приложений на основе необработанного кода XMLA, большинство приложений и разработчиков приложений задействуют библиотеки, чтобы использовать преимущества объектных моделей и кода. Для клиентских подключений к службам Analysis Services можно использовать IIS как промежуточное подключение, если не удается использовать TCP через стек. Одно из преимуществ использования доступа по протоколу HTTP через IIS — возможность подключения из приложений, которые передают учетные данные в строке подключения.  
  
 Если речь идет о подключении, неизбежно рассматривается проверка подлинности. В отличие от других компонентов SQL Server, службы Analysis Services поддерживают только учетные данные Windows. В серверном подключении к службам Analysis Services нельзя использовать проверку подлинности базы данных SQL Server, проверку подлинности утверждений, проверку подлинности на основе форм или дайджест. Подробные сведения о проверке подлинности приведены в этом разделе.  
  
##  <a name="bkmk_clientApps"></a> Задачи подключения  
  
|Ссылка|Описание задачи|  
|----------|----------------------|  
|[Подключение из клиентских приложений (службы Analysis Services)](../../analysis-services/instances/connect-from-client-applications-analysis-services.md)|Пользователи, не имеющие опыта работы со службами Analysis Services, должны прочитать этот раздел, прежде чем приступать к работе со средствами и приложениями, которые наиболее часто используются со службами Analysis Services.|  
|[Свойства строки подключения (службы Analysis Services)](../../analysis-services/instances/connection-string-properties-analysis-services.md)|Службы Analysis Services включают множество свойств сервера и базы данных, позволяющих настроить соединение для конкретного приложения, независимо от настройки экземпляра или базы данных.|  
|[Методики проверки подлинности, поддерживаемые службами Analysis Services](../../analysis-services/instances/authentication-methodologies-supported-by-analysis-services.md)|Этот раздел представляет собой краткое введение в методы проверки подлинности, используемые службами Analysis services.|  
|[Настройка служб Analysis Services для ограниченного делегирования Kerberos](../../analysis-services/instances/configure-analysis-services-for-kerberos-constrained-delegation.md)|Для многих решений бизнес-аналитики требуется олицетворение, чтобы гарантировать, что каждый пользователь получает только разрешенные данные. В этом разделе рассматриваются требования для использования олицетворения. В этом разделе также приводится описание действий по настройке служб Analysis Services для ограниченного делегирования Kerberos.|  
|[Регистрация имени участника-службы для экземпляра служб Analysis Services](../../analysis-services/instances/spn-registration-for-an-analysis-services-instance.md)|Для проверки подлинности Kerberos требуется имя участника-службы, которая олицетворяет или делегирует удостоверения пользователя в многосерверных решениях. Сведения в этом разделе позволяют получить представление о разработке и шагах для регистрации имени участника-службы для служб Analysis Services.|  
|[Настройка HTTP-доступа к службам Analysis Services в службах Internet Information Services (IIS) 8.0](../../analysis-services/instances/configure-http-access-to-analysis-services-on-iis-8-0.md)|Обычная проверка подлинности и кросс-доменные границы — две веские причины для настройки служб Analysis Services для доступа по протоколу HTTP.|  
|[Поставщики данных, используемые для соединений со службами Analysis Services](../../analysis-services/instances/data-providers-used-for-analysis-services-connections.md)|Службы Analysis Services предоставляют три клиентские библиотеки для доступа к операциям на сервере или данным служб Analysis Services. Этот раздел содержит краткое введение в ADOMD.NET, службы Analysis Services (AMO) и работу поставщика OLE DB для служб Analysis Services (MSOLAP).|  
|[Отключение пользователей и сеансов на сервере служб Analysis Services](../../analysis-services/instances/disconnect-users-and-sessions-on-analysis-services-server.md)|Сбросьте существующие сеансы и соединения, прежде чем переводить сервер в режим «вне сети» или выполнять базовые тесты производительности.|  
  
## <a name="see-also"></a>См. также  
 [Настройка после установки (службы Analysis Services)](../../analysis-services/instances/post-install-configuration-analysis-services.md)   
 [Свойства сервера в службах Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
  
  
