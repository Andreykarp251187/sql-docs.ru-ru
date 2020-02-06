---
title: Обновление статистики | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- updating statistics
- statistics [SQL Server], updating
ms.assetid: 4b97c0b4-03ff-4cfb-9c3f-3b33290b7a2c
author: julieMSFT
ms.author: jrasnick
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 59efa5a8143d448ca322ab1b6efa86cbfa9f66d1
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "67934085"
---
# <a name="update-statistics"></a>Обновить статистику
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Обновить статистику оптимизации запросов для таблицы или индексированного представления в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] можно с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. По умолчанию оптимизатор запросов обновляет статистику по мере необходимости для усовершенствования плана запроса. В некоторых случаях можно повысить производительность запроса, выполняя обновление статистики с помощью инструкции UPDATE STATISTICS или хранимой процедуры `sp_updatestats` чаще, чем это происходит по умолчанию.  
  
 Обновление статистики гарантирует, что запросы будут компилироваться с актуальной статистикой. Однако обновление статистики вызывает перекомпиляцию запросов. Рекомендуется не обновлять статистику слишком часто, поскольку необходимо найти баланс между выигрышем в производительности за счет усовершенствованных планов запросов и потерей времени на перекомпиляцию запросов. Критерии выбора компромиссного решения зависят от приложения. UPDATE STATISTICS может использовать базу данных tempdb для сортировки образцов строк для построения статистики.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Безопасность](#Security)  
  
-   **Для обновления объекта статистики используются:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 При использовании инструкции UPDATE STATISTICS или внесении изменений в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]необходимо разрешение ALTER на таблицу или представление. При использовании процедуры `sp_updatestats`необходимо быть членом предопределенной роли сервера **sysadmin** или владельцем базы данных (**dbo**).  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-update-a-statistics-object"></a>Обновление объекта статистики  
  
1.  В **обозревателе объектов**щелкните значок «плюс», чтобы развернуть базу данных, в которой нужно обновить статистику.  
  
2.  Чтобы развернуть папку **Таблицы** , щелкните значок «плюс».  
  
3.  Щелкните значок «плюс», чтобы развернуть таблицу, в которой нужно обновить статистику.  
  
4.  Щелкните значок «плюс», чтобы развернуть папку **Статистика** .  
  
5.  Щелкните правой кнопкой мыши объект статистики, который нужно обновить, и выберите пункт **Свойства**.  
  
6.  В диалоговом окне **Свойства статистики —** _имя\_статистики_ установите флажок **Обновить статистику для этих столбцов** и затем нажмите кнопку **ОК**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
### <a name="to-update-a-specific-statistics-object"></a>Обновление указанного объекта статистики  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```sql  
    USE AdventureWorks2012;  
    GO  
    -- The following example updates the statistics for the AK_SalesOrderDetail_rowguid index of the SalesOrderDetail table.   
    UPDATE STATISTICS Sales.SalesOrderDetail AK_SalesOrderDetail_rowguid;   
    GO  
    ```  
  
### <a name="to-update-all-statistics-in-a-table"></a>Обновление всей статистики в таблице  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```sql  
    USE AdventureWorks2012;   
    GO  
    -- The following example updates the statistics for all indexes on the SalesOrderDetail table.   
    UPDATE STATISTICS Sales.SalesOrderDetail;   
    GO  
    ```  
  
Дополнительные сведения см. в статье [UPDATE STATISTICS (Transact-SQL)](../../t-sql/statements/update-statistics-transact-sql.md).  
  
### <a name="to-update-all-statistics-in-a-database"></a>Обновление всей статистики в базе данных  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```sql  
    USE AdventureWorks2012;   
    GO  
    -- The following example updates the statistics for all tables in the database.   
    EXEC sp_updatestats;  
    ```  

Дополнительные сведения см. в статье [sp_updatestats (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-updatestats-transact-sql.md).   

### <a name="automatic-index-and-statistics-management"></a>Автоматическое управление индексами и статистикой
Используйте такие решения, как [Адаптивная дефрагментация индексов](https://github.com/Microsoft/tigertoolbox/tree/master/AdaptiveIndexDefrag), чтобы автоматически управлять дефрагментацией индексов и обновлениями статистики для одной базы данных или нескольких. Эта процедура автоматически выбирает, следует ли перестроить или реорганизовать индекс, сверяясь с уровнем фрагментации и другими параметрами, и обновляет статистику на основе линейных пороговых значений.

