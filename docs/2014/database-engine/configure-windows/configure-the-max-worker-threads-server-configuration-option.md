---
title: Настройка параметра конфигурации сервера max worker threads | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- worker threads [SQL Server]
- max worker threads option
ms.assetid: abeadfa4-a14d-469a-bacf-75812e48fac1
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 5d4aae8a264bd77d51c3365183ee510043ae814b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62787611"
---
# <a name="configure-the-max-worker-threads-server-configuration-option"></a>Настройка параметра конфигурации сервера max worker threads
  В этом разделе описываются способы настройки параметра конфигурации сервера **max worker threads** в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Параметр **max worker threads** используется для установки количества рабочих потоков, доступных процессам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используются собственные службы для потоков операционных систем, поэтому один или несколько потоков одновременно поддерживают все сети, которые поддерживает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , еще один поток обрабатывает контрольные точки базы данных, а пул потоков обрабатывает запросы от всех пользователей. Значение по умолчанию для параметра **max worker threads** — 0. Это позволяет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] автоматически настраивать количество рабочих потоков при запуске. Настройка по умолчанию является оптимальной для большинства систем. Но иногда, в зависимости от конфигурации системы, установка параметра **max worker threads** в другое определенное значение может улучшить производительность.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Рекомендации](#Recommendations)  
  
     [Безопасность](#Security)  
  
-   **Настройка параметра max worker threads с помощью различных средств.**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Дальнейшие действия.**  [После настройки параметра max worker threads](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Если реальное количество запросов меньше значения, заданного параметром **max worker threads**, каждый запрос обрабатывается одним потоком. Однако если реальное количество потоков превышает число, заданное параметром **max worker threads**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует пул рабочих потоков, так что следующий доступный рабочий поток сможет обработать запрос.  
  
###  <a name="Recommendations"></a> Рекомендации  
  
-   Этот параметр является дополнительным и его следует изменять только опытным администраторам баз данных или сертифицированным техническим специалистам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Пул потоков помогает оптимизировать производительность при подключении к серверу большого числа пользователей. Обычно для каждого запроса в операционной системе создается отдельный поток. Однако в случае сотен соединений с сервером, использование одного потока на каждый запрос приводит к потреблению большого числа системных ресурсов. Параметр **max worker threads** позволяет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создавать пул рабочих потоков, чтобы обслужить большое число запросов, что улучшает производительность.  
  
-   В следующей таблице показано автоматически настраиваемое максимальное число рабочих потоков для различных сочетаний процессоров и версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    |Число процессоров|32-разрядный компьютер|64-разрядный компьютер|  
    |--------------------|----------------------|----------------------|  
    |\< — 4 процессора|256|512|  
    |8 процессоров|288|576|  
    |16 процессоров|352|704|  
    |32 процессора|480|960|  
    |64 процессора|736|1472|  
    |128 процессоров|4224|4480|  
    |256 процессоров|8320|8576|  
  
    > [!NOTE]  
    >  Рекомендации по использованию процессоров в количестве, превышающем 64, см. в разделе [Рекомендации по использованию SQL Server на компьютерах, которые имеют более 64 процессоров](https://technet.microsoft.com/library/ee210547\(SQL.105\).aspx).  
  
    > [!WARNING]  
    >  Для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , работающего в 32-разрядном компьютере, рекомендуется ограничить число рабочих потоков до 1024.  
  
-   Если все рабочие потоки заняты выполнением длительных запросов, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может не отвечать на другие запросы, пока один из потоков не завершит работу и не станет доступным. Хотя это и не ошибка, такое поведение иногда нежелательно. Если процесс не отвечает и новые запросы не могут быть обработаны, подключитесь к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] через выделенное административное соединение (DAC) и уничтожьте процесс. Во избежание этого увеличьте максимальное число потоков управления.  
  
 Параметр конфигурации сервера **max worker threads** не учитывает потоки, которые необходимы для всех системных задач, таких как группы доступности, компонент Service Broker, диспетчер блокировок и другие.  Если число настроенных потоков превышается, то следующий запрос будет содержать сведения о системных задачах, породивших дополнительные потоки.  
  
```  
SELECT  
s.session_id,  
r.command,  
r.status,  
r.wait_type,  
r.scheduler_id,  
w.worker_address,  
w.is_preemptive,  
w.state,  
t.task_state,  
t.session_id,  
t.exec_context_id,  
t.request_id  
FROM sys.dm_exec_sessions AS s  
INNERJOIN sys.dm_exec_requests AS r  
    ON s.session_id = r.session_id  
INNER JOIN sys.dm_os_tasks AS t  
    ON r.task_address = t.task_address  
INNER JOIN sys.dm_os_workers AS w  
    ON t.worker_address = w.worker_address  
WHERE s.is_user_process = 0;  
  
```  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Разрешения на выполнение хранимой процедуры **sp_configure** без параметров или только с первым параметром по умолчанию предоставляются всем пользователям. Для выполнения процедуры **sp_configure** с обоими параметрами для изменения параметра конфигурации или запуска инструкции RECONFIGURE необходимо иметь разрешение ALTER SETTINGS на уровне сервера. Разрешение ALTER SETTINGS неявным образом предоставлено предопределенным ролям сервера **sysadmin** и **serveradmin** .  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-configure-the-max-worker-threads-option"></a>Настройка параметра max worker threads  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши сервер и выберите пункт **Свойства**.  
  
2.  Щелкните узел **Процессоры** .  
  
3.  В поле **max worker threads (максимальное число рабочих потоков** ) введите или выберите значение от 128 до 32767.  
  
     Используйте параметр **max worker threads** для установки количества рабочих потоков, доступных процессам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Значение по умолчанию параметра **max worker threads** является оптимальным для большинства систем. Но в зависимости от конфигурации системы установка параметра **max worker threads** в меньшее значение может улучшить производительность.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-configure-the-max-worker-threads-option"></a>Настройка параметра max worker threads  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере описывается использование процедуры [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) для задания значения параметра `max worker threads` равным `900`.  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'max worker threads', 900 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 Дополнительные сведения см. в разделе [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md).  
  
##  <a name="FollowUp"></a> Дальнейшие действия. После настройки параметра "Максимальное количество рабочих потоков"  
 Изменения вступят в силу немедленно без необходимости перезапуска компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] .  
  
## <a name="see-also"></a>См. также:  
 [RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [Диагностическое соединение для администраторов баз данных](diagnostic-connection-for-database-administrators.md)  
  
  
