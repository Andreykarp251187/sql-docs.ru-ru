---
title: Указание расписаний синхронизации | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [SQL Server replication], synchronizing
- scheduling synchronization [SQL Server replication]
- synchronization [SQL Server replication], schedules
- replication [SQL Server], synchronization
ms.assetid: 97f2535b-ec19-4973-823d-bcf3d5aa0216
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9bfbb62c58efea29df26cb9fc6e632bc4e2b3642
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62630799"
---
# <a name="specify-synchronization-schedules"></a>Указание расписаний синхронизации
  В данном разделе описывается процесс задания расписаний синхронизации в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]или объектов RMO. При создании подписки можно определить расписание синхронизации, управляющее запуском агента репликации для подписки. Если не указать параметры расписания, подписка использует расписание по умолчанию.  
  
 Подписки синхронизируются агентом распространителя (для репликации моментальных снимков и репликации транзакций) или агентом слияния (для репликации слиянием). Агенты могут работать непрерывно, запускаться по запросу или по расписанию.  
  
 **В этом разделе**  
  
-   **Для указания расписаний синхронизации используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Объекты Replication Management Objects (RMO)](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Укажите расписания синхронизации на странице **Расписание синхронизации** мастера создания подписки. Дополнительные сведения о доступе к этому мастеру см. в разделах [Create a Push Subscription](create-a-push-subscription.md) и [Create a Pull Subscription](create-a-pull-subscription.md).  
  
 Измените расписания синхронизации в диалоговом окне **Свойства расписания задания** , доступном из папки **Задания** в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и в окнах подробных сведений агента в мониторе репликации. Сведения о запуске монитора репликации см. в [этой статье](monitor/start-the-replication-monitor.md).  
  
 При указании расписаний из папки **Задания** используйте следующую таблицу для определения имени задания агента.  
  
|Агент|Имя задания|  
|-----------|--------------|  
|Агент слияния для подписок по запросу|**\<Издатель>-\<база данных публикации>-\<Publication> —\<подписчик>-\<субскриптиондатабасе>-\<Integer>**|  
|Агент слияния для принудительных подписок|**\<Издатель>-\<база данных публикации>-\<публикация> —\<подписчик> —\<целое число>**|  
|Агент распространителя для принудительных подписок|**\<\<\<Издатель>-база данных публикации>-публикация> — подписчик>-\<Integer>1 \<** <sup></sup>|  
|Агент распространителя для подписок по запросу|**\<\<\<\<Издатель>-база данных публикации>-publication> — подписчик>-субскриптиондатабасе>-\<GUID>2 \<** <sup></sup>|  
|Агент распространителя для принудительных подписок подписчиков серверов, отличных от подписчиков SQL Server|**\<Издатель>-\<база данных публикации>-\<публикация> —\<подписчик> —\<целое число>**|  
  
 <sup>1</sup> для принудительных подписок на публикации Oracle используется ** \<издатель>-\<Publisher**>, а не ** \<издатель>\<-база данных публикации>**  
  
 <sup>2</sup> для подписок по запросу на публикации Oracle используется ** \<издатель>-\<DistributionDatabase**>, а не ** \<издатель>\<-база данных публикации>**  
  
#### <a name="to-specify-synchronization-schedules"></a>Указание расписаний синхронизации  
  
1.  На странице **Расписание синхронизации** мастера создания подписки выберите одно из следующих значений в раскрывающемся списке **Расписание агента** для каждой создаваемой подписки:  
  
    -   **Выполнять непрерывно**  
  
    -   **Запускать только по запросу**  
  
    -   **\<Определить расписание... >**  
  
2.  Если выбран ** \<параметр определить расписание... >**, укажите расписание в диалоговом окне **Свойства расписания задания** , а затем нажмите кнопку **ОК**.  
  
3.  Завершите работу мастера.  
  
#### <a name="to-modify-a-synchronization-schedule-for-a-push-subscription-in-replication-monitor"></a>Изменение расписания синхронизации для принудительных подписок в мониторе репликации  
  
1.  На левой панели монитора репликации раскройте группу издателей, раскройте нужный издатель, а затем выберите публикацию.  
  
2.  Перейдите на вкладку **Все подписки** .  
  
3.  Щелкните правой кнопкой мыши подписку, а затем выберите **Просмотреть сведения**.  
  
4.  В окне **подписка \< SubscriptionName>** щелкните **действие**, а затем выберите ** \<ажентнаме> свойства задания**.  
  
5.  На странице **Расписания** диалогового окна **Свойства задания — \<имя_задания>** нажмите кнопку **Изменить**.  
  
6.  В диалоговом окне **Свойства расписания задания** выберите значение из раскрывающегося списка **Тип расписания** :  
  
    -   Для указания непрерывной работы агента выберите **Запускать автоматически при запуске агента SQL Server**.  
  
    -   Для указания работы агента по расписанию выберите **Периодически**.  
  
    -   Для указания запуска агента по запросу выберите **Один раз**.  
  
7.  При выборе значения **Периодически**укажите расписание для агента.  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
#### <a name="to-modify-a-synchronization-schedule-for-a-push-subscription-in-management-studio"></a>Изменение расписания синхронизации для принудительных подписок в среде Management Studio  
  
1.  Подключитесь к распространителю в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]и раскройте узел сервера.  
  
2.  Раскройте папку **Агент SQL Server** , а затем — папку **Задания** .  
  
3.  Щелкните правой кнопкой задание для агента распространителя или агента слияния, связанных с подпиской, а затем щелкните **Свойства**.  
  
4.  На странице **Расписания** диалогового окна **Свойства задания — \<имя_задания>** нажмите кнопку **Изменить**.  
  
5.  В диалоговом окне **Свойства расписания задания** выберите значение из раскрывающегося списка **Тип расписания** :  
  
    -   Для указания непрерывной работы агента выберите **Запускать автоматически при запуске агента SQL Server**.  
  
    -   Для указания работы агента по расписанию выберите **Периодически**.  
  
    -   Для указания запуска агента по запросу выберите **Один раз**.  
  
6.  При выборе значения **Периодически**укажите расписание для агента.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
#### <a name="to-modify-a-synchronization-schedule-for-a-pull-subscription-in-management-studio"></a>Изменение расписания синхронизации для подписок по запросу в среде Management Studio  
  
1.  Подключитесь к подписчику в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]и раскройте узел сервера.  
  
2.  Раскройте папку **Агент SQL Server** , а затем — папку **Задания** .  
  
3.  Щелкните правой кнопкой задание для агента распространителя или агента слияния, связанных с подпиской, а затем щелкните **Свойства**.  
  
4.  На странице **Расписания** диалогового окна **Свойства задания — \<имя_задания>** нажмите кнопку **Изменить**.  
  
5.  В диалоговом окне **Свойства расписания задания** выберите значение из раскрывающегося списка **Тип расписания** :  
  
    -   Для указания непрерывной работы агента выберите **Запускать автоматически при запуске агента SQL Server**.  
  
    -   Для указания работы агента по расписанию выберите **Периодически**.  
  
    -   Для указания запуска агента по запросу выберите **Один раз**.  
  
6.  При выборе значения **Периодически**укажите расписание для агента.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Можно определить расписание синхронизации программно с помощью хранимых процедур репликации. Эти хранимые процедуры зависят от типа репликации и типа подписки (по запросу или принудительная).  
  
 Расписание определяется следующими параметрами, поведение которых наследуется из процедуры [sp_add_schedule (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql):  
  
-   **@frequency_type**— Тип частоты, используемой при планировании агента.  
  
-   **@frequency_interval**— день недели, когда запускается агент.  
  
-   **@frequency_relative_interval**— Неделя в заданном месяце, когда агент планируется выполнять ежемесячно.  
  
-   **@frequency_recurrence_factor**— число единиц типа Frequency, которые происходят между синхронизациями.  
  
-   **@frequency_subday**— единица частоты, когда агент запускается чаще одного раза в день.  
  
-   **@frequency_subday_interval**— число единиц частоты между запусками, когда агент запускается чаще одного раза в день.  
  
-   **@active_start_time_of_day**— самое раннее время в указанном дне, когда запускается агент.  
  
-   **@active_end_time_of_day**— Последнее время в заданный день, когда запускается агент.  
  
-   **@active_start_date**— первый день, когда расписание агента будет действовать.  
  
-   **@active_end_date**— последний день, когда расписание агента будет действовать.  
  
#### <a name="to-define-the-synchronization-schedule-for-a-pull-subscription-to-a-transactional-publication"></a>Определение расписания синхронизации для подписки по запросу на публикацию транзакций  
  
1.  Создайте подписку по запросу на публикацию транзакций. Дополнительные сведения см. в статье [Создание подписки по запросу](create-a-pull-subscription.md).  
  
2.  На подписчике выполните процедуру [sp_addpullsubscription_agent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql). Укажите **@publisher**, **@publisher_db**, **@publication**и учетные [!INCLUDE[msCoName](../../includes/msconame-md.md)] данные Windows, с которыми работает агент распространения на подписчике, **@job_name** для **@password**и. Укажите описанные выше параметры синхронизации, определяющие расписание для задания агента распространителя, синхронизирующего подписку.  
  
#### <a name="to-define-the-synchronization-schedule-for-a-push-subscription-to-a-transactional-publication"></a>Определение расписания синхронизации для принудительной подписки на публикацию транзакций  
  
1.  Создайте принудительную подписку на публикацию транзакций. Дополнительные сведения см. в статье [Создание принудительной подписки](create-a-push-subscription.md).  
  
2.  На подписчике выполните процедуру [sp_addpushsubscription_agent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql). Укажите **@subscriber**, **@subscriber_db**, **@publication**и учетные данные Windows, с которыми работает агент распространения на подписчике, **@job_name** для **@password**и. Укажите описанные выше параметры синхронизации, определяющие расписание для задания агента распространителя, синхронизирующего подписку.  
  
#### <a name="to-define-the-synchronization-schedule-for-a-pull-subscription-to-a-merge-publication"></a>Определение расписания синхронизации для подписки по запросу для публикации слиянием  
  
1.  Создайте подписку по запросу на публикацию слиянием. Дополнительные сведения см. в статье [Создание подписки по запросу](create-a-pull-subscription.md).  
  
2.  Выполните процедуру [sp_addmergepullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql)на подписчике. Укажите **@publisher**, **@publisher_db**, **@publication**и учетные данные Windows, с которыми работает агент слияния на подписчике, **@job_name** для **@password**и. Укажите описанные выше параметры синхронизации, определяющие расписание для задания агента слияния, синхронизирующего подписку.  
  
#### <a name="to-define-the-synchronization-schedule-for-a-push-subscription-to-a-merge-publication"></a>Определение расписания синхронизации для принудительной подписки на публикацию слиянием  
  
1.  Создайте принудительную подписку на публикацию слиянием. Дополнительные сведения см. в статье [Создание принудительной подписки](create-a-push-subscription.md).  
  
2.  Выполните на подписчике хранимую процедуру [sp_addmergepushsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql). Укажите **@subscriber**, **@subscriber_db**, **@publication**и учетные данные Windows, с которыми работает агент слияния на подписчике, **@job_name** для **@password**и. Укажите описанные выше параметры синхронизации, определяющие расписание для задания агента слияния, синхронизирующего подписку.  
  
##  <a name="RMOProcedure"></a> При помощи объектов RMO  
 При выполнении репликации агент SQL Server производит планирование заданий для создания моментальных снимков и синхронизации подписок. Расписание заданий агента репликации может быть задано программным путем с помощью объектов RMO.  
  
> [!NOTE]  
>  Если при создании подписки в параметре `false` указано значение `CreateSyncAgentByDefault` (по умолчанию для подписок по запросу), то задание агента не создается, а параметры расписания не учитываются. В этом случае расписание синхронизации задается приложением. Дополнительные сведения см. в разделах [Create a Pull Subscription](create-a-pull-subscription.md) и [Create a Push Subscription](create-a-push-subscription.md).  
  
#### <a name="to-define-a-replication-agent-schedule-when-you-create-a-push-subscription-to-a-transactional-publication"></a>Создание нового расписания агента репликации при создании принудительной подписки на публикацию транзакций  
  
1.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.TransSubscription> для создаваемой подписки. Дополнительные сведения см. в статье [Создание принудительной подписки](create-a-push-subscription.md).  
  
2.  Перед вызовом метода <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A>установите одно или несколько из следующих полей свойства <xref:Microsoft.SqlServer.Replication.Subscription.AgentSchedule%2A> :  
  
    -   
  <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> — частота запуска агента по расписанию (например ежедневно или еженедельно);  
  
    -   
  <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> — день недели, в который запускается агент;  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A>— Неделя в заданном месяце, когда агент планируется выполнять ежемесячно.  
  
    -   
  <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> — число частотных единиц, проходящих между последовательными синхронизациями;  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A>— единица частоты, когда агент запускается чаще одного раза в день.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A>— число единиц частоты между запусками, когда агент запускается чаще одного раза в день.  
  
    -   
  <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> — время самого раннего запуска агента в заданный день;  
  
    -   
  <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> — время самого позднего запуска агента в заданный день;  
  
    -   
  <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> — первый день действия расписания агента;  
  
    -   
  <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> — последний день действия расписания агента.  
  
    > [!NOTE]  
    >  Если не задать одно из этих свойств, будет использоваться значение по умолчанию.  
  
3.  Вызовите метод <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> , чтобы создать подписку.  
  
#### <a name="to-define-a-replication-agent-schedule-when-you-create-a-pull-subscription-to-a-transactional-publication"></a>Создание расписания агента репликации при создании подписки по запросу на публикацию транзакций  
  
1.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.TransPullSubscription> для создаваемой подписки. Дополнительные сведения см. в статье [Создание подписки по запросу](create-a-pull-subscription.md).  
  
2.  Перед вызовом метода <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A>установите одно или несколько из следующих полей свойства <xref:Microsoft.SqlServer.Replication.PullSubscription.AgentSchedule%2A> :  
  
    -   
  <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> — тип интервала для запуска агента по расписанию (например ежедневно или еженедельно);  
  
    -   
  <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> — день недели, в который запускается агент;  
  
    -   
  <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> — неделя в заданном месяце, на которой запускается агент при ежемесячном режиме работы;  
  
    -   
  <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> — число частотных единиц, проходящих между последовательными синхронизациями;  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A>— единица частоты, когда агент запускается чаще одного раза в день.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A>— число единиц частоты между запусками, когда агент запускается чаще одного раза в день.  
  
    -   
  <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> — время самого раннего запуска агента в заданный день;  
  
    -   
  <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> — время самого позднего запуска агента в заданный день;  
  
    -   
  <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> — первый день действия расписания агента;  
  
    -   
  <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> — последний день действия расписания агента.  
  
    > [!NOTE]  
    >  Если не задать одно из этих свойств, будет использоваться значение по умолчанию.  
  
3.  Вызовите метод <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A> , чтобы создать подписку.  
  
#### <a name="to-define-a-replication-agent-schedule-when-you-create-a-pull-subscription-to-a-merge-publication"></a>Создание расписания агента репликации при создании подписки по запросу на публикацию слиянием  
  
1.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergePullSubscription> для создаваемой подписки. Дополнительные сведения см. в статье [Создание подписки по запросу](create-a-pull-subscription.md).  
  
2.  Перед вызовом метода <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A>установите одно или несколько из следующих полей свойства <xref:Microsoft.SqlServer.Replication.PullSubscription.AgentSchedule%2A> :  
  
    -   
  <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> — тип интервала для запуска агента по расписанию (например ежедневно или еженедельно);  
  
    -   
  <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> — день недели, в который запускается агент;  
  
    -   
  <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> — неделя в заданном месяце, на которой запускается агент при ежемесячном режиме работы;  
  
    -   
  <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> — число частотных единиц, проходящих между последовательными синхронизациями;  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A>— единица частоты, когда агент запускается чаще одного раза в день.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A>— число единиц частоты между запусками, когда агент запускается чаще одного раза в день.  
  
    -   
  <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> — время самого раннего запуска агента в заданный день;  
  
    -   
  <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> — время самого позднего запуска агента в заданный день;  
  
    -   
  <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> — первый день действия расписания агента;  
  
    -   
  <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> — последний день действия расписания агента.  
  
    > [!NOTE]  
    >  Если не задать одно из этих свойств, будет использоваться значение по умолчанию.  
  
3.  Вызовите метод <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A> , чтобы создать подписку.  
  
#### <a name="to-define-a-replication-agent-schedule-when-you-create-a-push-subscription-to-a-merge-publication"></a>Создание расписания агента репликации при создании принудительной подписки на публикацию слиянием  
  
1.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergeSubscription> для создаваемой подписки. Дополнительные сведения см. в статье [Создание принудительной подписки](create-a-push-subscription.md).  
  
2.  Перед вызовом метода <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A>установите одно или несколько из следующих полей свойства <xref:Microsoft.SqlServer.Replication.Subscription.AgentSchedule%2A> :  
  
    -   
  <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> — тип интервала для запуска агента по расписанию (например ежедневно или еженедельно);  
  
    -   
  <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> — день недели, в который запускается агент;  
  
    -   
  <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> — неделя в заданном месяце, на которой запускается агент при ежемесячном режиме работы;  
  
    -   
  <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> — число частотных единиц, проходящих между последовательными синхронизациями;  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A>— единица частоты, когда агент запускается чаще одного раза в день.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A>— число единиц частоты между запусками, когда агент запускается чаще одного раза в день.  
  
    -   
  <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> — время самого раннего запуска агента в заданный день;  
  
    -   
  <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> — время самого позднего запуска агента в заданный день;  
  
    -   
  <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> — первый день действия расписания агента;  
  
    -   
  <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> — последний день действия расписания агента.  
  
    > [!NOTE]  
    >  Если не задать одно из этих свойств, будет использоваться значение по умолчанию.  
  
3.  Вызовите метод <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> , чтобы создать подписку.  
  
###  <a name="PShellExample"></a>Пример (объекты RMO)  
 В следующем примере производится создание принудительной подписки на публикацию слиянием, а также задается расписание синхронизации указанной подписки.  
  
 [!code-csharp[HowTo#rmo_CreateMergePushSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createmergepushsub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergePushSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createmergepushsub)]  
  
## <a name="see-also"></a>См. также:  
 [Рекомендации по обеспечению безопасности репликации](security/replication-security-best-practices.md)   
 [Подписка на публикации](subscribe-to-publications.md)   
 [Синхронизация принудительной подписки](synchronize-a-push-subscription.md)   
 [Синхронизация подписки по запросу](synchronize-a-pull-subscription.md)   
 [Синхронизация данных](synchronize-data.md)  
  
  
