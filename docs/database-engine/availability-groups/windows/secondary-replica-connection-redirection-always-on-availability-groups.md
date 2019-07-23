---
title: Перенаправление подключения с правами на чтение и запись с вторичной реплики SQL Server на первичную (группы доступности AlwaysOn) | Документация Майкрософт
ms.custom: ''
ms.date: 01/09/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: article
helpviewer_keywords:
- connection access to availability replicas
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], readable secondary replicas
- active secondary replicas [SQL Server], read-only access to
- readable secondary replicas
- Availability Groups [SQL Server], active secondary replicas
ms.assetid: ''
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 181dd36096daacc5a1c3787cdd21cb9619d87491
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68014198"
---
# <a name="secondary-to-primary-replica-readwrite-connection-redirection-always-on-availability-groups"></a>Перенаправление подключения с правами на чтение и запись с вторичной на первичную реплику (группы доступности AlwaysOn)

[!INCLUDE[appliesto](../../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[!INCLUDE[sssqlv15-md](../../../includes/sssqlv15-md.md)] CTP 2.0 реализует *перенаправление подключения с правами на чтение и запись с вторичной на первичную реплику* для групп доступности AlwaysOn. Перенаправление подключения с правами на чтение и запись можно использовать на любой платформе операционной системы. Это позволяет направлять подключения клиентских приложений к первичной реплике независимо от целевого сервера, указанного в строке подключения. 

Например, строка подключения может направлять к вторичной реплике. В зависимости от настройки реплики группы доступности и параметров в строке подключения, подключение может автоматически перенаправляться к первичной реплике. 

## <a name="use-cases"></a>Способы применения

В версиях до [!INCLUDE[sssqlv15-md](../../../includes/sssqlv15-md.md)] прослушиватель группы доступности и соответствующий кластерный ресурс перенаправляют трафик пользователя к первичной реплике, чтобы обеспечить повторное подключение после отработки отказа. [!INCLUDE[sssqlv15-md](../../../includes/sssqlv15-md.md)] по-прежнему поддерживает функциональные возможности прослушивателя группы доступности и добавляет перенаправление подключения реплики для сценариев, которые не содержат прослушиватель. Пример:

* Кластерная технология, с которой интегрируются группы доступности SQL Server, не поддерживает такую возможность, как прослушиватель. 
* Конфигурации с несколькими подсетями, например в облаке или с плавающим IP-адресом нескольких подсетей, с Pacemaker, где конфигурации становятся сложными, что может привести к ошибкам и затруднить их исправление из-за нескольких включенных компонентов.
* В сценариях с масштабированием для чтения или аварийным восстановлением с типом кластера — `NONE`, так как отсутствует простой механизм для обеспечения прозрачного повторного подключения при переходе на другой ресурс вручную.

## <a name="requirement"></a>Требование

Чтобы подключение с правами на чтение и запись перенаправить с вторичной реплики:
* Вторичная реплика должна быть подключена к Интернету. 
* Спецификация реплики `PRIMARY_ROLE` должна включать `READ_WRITE_ROUTING_URL`.
* Строка подключения должна определять `ApplicationIntent` как `ReadWrite`, что является значением по умолчанию.

## <a name="set-readwriteroutingurl-option"></a>Установка параметра READ_WRITE_ROUTING_URL

Чтобы настроить перенаправление подключения с правами на чтение и запись, задайте `READ_WRITE_ROUTING_URL` для первичной реплики при создании группы доступности. 

В [!INCLUDE[sssqlv15-md](../../../includes/sssqlv15-md.md)] в спецификацию `<add_replica_option>` был добавлен параметр `READ_WRITE_ROUTING_URL`. См. следующие статьи: 

* [CREATE AVAILABILITY GROUP](../../../t-sql/statements/create-availability-group-transact-sql.md)
* [ALTER AVAILABILITY GROUP](../../../t-sql/statements/alter-availability-group-transact-sql.md)


### <a name="primaryrolereadwriteroutingurl-not-set-default"></a>PRIMARY_ROLE(READ_WRITE_ROUTING_URL) не задан (по умолчанию) 

По умолчанию перенаправление подключения с правами на чтение и запись не задано для реплики. Метод обработки запросов на подключение во вторичной реплике зависит от того, разрешает ли вторичная реплика подключения и задан ли в строке подключения параметр `ApplicationIntent`. В следующей таблице показано, как вторичная реплика обрабатывает подключения на основе `SECONDARY_ROLE (ALLOW CONNECTIONS = )` и `ApplicationIntent`.

||`SECONDARY_ROLE (ALLOW CONNECTIONS = NO)`|`SECONDARY_ROLE (ALLOW CONNECTIONS = READ_ONLY)`|`SECONDARY_ROLE (ALLOW CONNECTIONS = ALL)`|
|-----|-----|-----|-----|
|`ApplicationIntent=ReadWrite`<br/> По умолчанию|Сбой подключений|Сбой подключений|Успешные подключения<br/>Успешные операции чтения<br/>Сбой операций записи|
|`ApplicationIntent=ReadOnly`|Сбой подключений|Успешные подключения|Успешные подключения

В приведенной выше таблице показана реакция на событие по умолчанию, которая совпадает с версиями SQL Server до [!INCLUDE[sssqlv15-md](../../../includes/sssqlv15-md.md)]. 

### <a name="primaryrolereadwriteroutingurl-set"></a>PRIMARY_ROLE(READ_WRITE_ROUTING_URL) задан 

После установки перенаправления подключения с правами на чтение и запись реплика обрабатывает запросы на подключение по-другому. Реакция на событие подключения по-прежнему зависит от параметров `SECONDARY_ROLE (ALLOW CONNECTIONS = )` и `ApplicationIntent`. В следующей таблице показано, как вторичная реплика с заданным параметром `READ_WRITE_ROUTING` обрабатывает подключения на основе `SECONDARY_ROLE (ALLOW CONNECTIONS = )` и `ApplicationIntent`.

||`SECONDARY_ROLE (ALLOW CONNECTIONS = NO)`|`SECONDARY_ROLE (ALLOW CONNECTIONS = READ_ONLY)`|`SECONDARY_ROLE (ALLOW CONNECTIONS = ALL)`|
|-----|-----|-----|-----|
|`ApplicationIntent=ReadWrite`<br/>По умолчанию|Сбой подключений|Сбой подключений|Перенаправление подключений к первичной реплике|
|`ApplicationIntent=ReadOnly`|Сбой подключений|Успешные подключения|Успешные подключения

В приведенной выше таблице показано, что когда для первичной реплики задан параметр `READ_WRITE_ROUTING_URL`, то вторичная реплика будет перенаправлять подключения к первичной реплике, если задан параметр `SECONDARY_ROLE (ALLOW CONNECTIONS = ALL)` и подключение указывает `ReadWrite`.

## <a name="example"></a>Пример 

В этом примере группа доступности содержит три реплики:
* Первичная реплика на компьютере COMPUTER01.
* Синхронная вторичная реплика на компьютере COMPUTER02.
* Синхронная вторичная реплика на компьютере COMPUTER03.

На следующем рисунке представлена группа доступности.

![Исходная группа доступности](media/replica-connection-redirection-always-on-availability-groups/01_originalAG.png)

Следующий сценарий Transact-SQL создает группу доступности. В этом примере для каждой реплики указан `READ_WRITE_ROUTING_URL`.
```sql
CREATE AVAILABILITY GROUP MyAg   
     WITH ( CLUSTER_TYPE =  NONE )  
   FOR   
     DATABASE  <Database1>   
   REPLICA ON   
      'COMPUTER01' WITH   
         (  
         ENDPOINT_URL = 'TCP://COMPUTER01.<domain>.<tld>:5022',  
         AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,  
         FAILOVER_MODE = MANUAL,  
         SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL,   
            READ_ONLY_ROUTING_URL = 'TCP://COMPUTER01.<domain>.<tld>:1433' ),
         PRIMARY_ROLE (ALLOW_CONNECTIONS = READ_WRITE,   
            READ_ONLY_ROUTING_LIST = (COMPUTER02, COMPUTER03),
            READ_WRITE_ROUTING_URL = 'TCP://COMPUTER01.<domain>.<tld>:1433' )   
         SESSION_TIMEOUT = 10  
         ),   
      'COMPUTER02' WITH   
         (  
         ENDPOINT_URL = 'TCP://COMPUTER02.<domain>.<tld>:5022',  
         AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,  
         FAILOVER_MODE = MANUAL, 
         SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL,   
            READ_ONLY_ROUTING_URL = 'TCP://COMPUTER02.<domain>.<tld>:1433' ),  
         PRIMARY_ROLE (ALLOW_CONNECTIONS = READ_WRITE,   
            READ_ONLY_ROUTING_LIST = (COMPUTER01, COMPUTER03),  
            READ_WRITE_ROUTING_URL = 'TCP://COMPUTER02.<domain>.<tld>:1433' )   
         SESSION_TIMEOUT = 10  
         ),   
      'COMPUTER03' WITH   
         (  
         ENDPOINT_URL = 'TCP://COMPUTER03.<domain>.<tld>:5022',  
         AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,  
         FAILOVER_MODE = MANUAL,  
         SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL,   
            READ_ONLY_ROUTING_URL = 'TCP://COMPUTER03.<domain>.<tld>:1433' ),  
         PRIMARY_ROLE (ALLOW_CONNECTIONS = READ_WRITE,   
            READ_ONLY_ROUTING_LIST = (COMPUTER01, COMPUTER02),  
            READ_WRITE_ROUTING_URL = 'TCP://COMPUTER03.<domain>.<tld>:1433' )  
         SESSION_TIMEOUT = 10  
         );
GO  
```
   - `<domain>.<tld>`
      - Домен и домен верхнего уровня полного доменного имени. Например, `corporation.com`.


### <a name="connection-behaviors"></a>Реакции на событие подключения

На следующей схеме клиентское приложение подключается к компьютеру COMPUTER02 с заданным параметром `ApplicationIntent=ReadWrite`. Подключение перенаправляется к первичной реплике. 

![Исходная группа доступности](media/replica-connection-redirection-always-on-availability-groups/02_redirectionAG.png)

Вторичная реплика перенаправляет вызовы чтения и записи к первичной реплике. Подключение на чтения и запись к одной из реплик будет перенаправлено к первичной реплике. 

На следующей схеме для первичной реплики выполнена отработка отказа вручную на компьютер COMPUTER02. Клиентское приложение подключается к компьютеру COMPUTER01 с заданным параметром `ApplicationIntent=ReadWrite`. Подключение перенаправляется к первичной реплике. 

![Исходная группа доступности](media/replica-connection-redirection-always-on-availability-groups/03_redirectionAG.png)


## <a name="sql-server-instance-offline"></a>Экземпляр SQL Server в автономном режиме

Если экземпляр SQL Server, указанный в строке подключения, недоступен (простой), то произойдет сбой подключения, независимо от роли реплики на целевом сервере. Чтобы избежать длительного простоя приложения, в строке подключения нужно настроить альтернативного партнера для отработки отказа (`FailoverPartner`). Приложение должно реализовать логику повторных попыток для охвата первичных и вторичных реплик, не подключенных к сети, во время фактической отработки отказа. Сведения о строках подключения см. в статье о [свойстве SqlConnection.ConnectionString](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnection.connectionstring.aspx).

## <a name="see-also"></a>См. также:

[Обзор групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 
[Сведения о доступе клиентского подключения к репликам доступности (SQL Server)](../../../database-engine/availability-groups/windows/about-client-connection-access-to-availability-replicas-sql-server.md)   

[Прослушиватели групп доступности, возможность подключения клиентов и отработка отказа приложений (SQL Server)](../../../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md) 
