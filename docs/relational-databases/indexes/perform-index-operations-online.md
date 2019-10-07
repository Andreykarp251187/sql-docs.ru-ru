---
title: Выполнение операций с индексами в сети | Документация Майкрософт
ms.custom: ''
ms.date: 02/17/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- index online operations [SQL Server]
- online index operations
- ONLINE option
ms.assetid: 1e43537c-bf67-4db3-9908-3cb45c6fdaa1
author: MikeRayMSFT
ms.author: mikeray
ms.prod_service: table-view-index, sql-database
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 914d2a3bfd73c76fc89b1ca6ed0302f32e0a4d32
ms.sourcegitcommit: 445842da7c7d216b94a9576e382164c67f54e19a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/30/2019
ms.locfileid: "71680788"
---
# <a name="perform-index-operations-online"></a>Выполнение операции с индексами в сети
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  В этом разделе описывается создание, перестроение и удаление индексов в режиме «в сети» в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и [!INCLUDE[tsql](../../includes/tsql-md.md)]. Параметр ONLINE разрешает одновременный доступ пользователей к базовой таблице или данным кластеризованного индекса и всем связанным некластеризованным индексам во время выполнения этих операций с индексами. Например, пока пользователь перестраивает кластеризованный индекс, он и другие пользователи могут продолжать обновление базовых данных и осуществлять к ним запросы. Если операции языка описания данных DDL (DDL), такие как построение или перестроение кластеризованного индекса, выполняются в режиме «вне сети», то они удерживают монопольные блокировки на базовые данные и связанные индексы. Это предотвращает изменение базовых данных и осуществление запросов к ним до завершения операции с индексами.  
  
> [!NOTE]  
>  Операции с индексами в сети доступны не во всех выпусках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения см. в статье "Возможности, поддерживаемые различными выпусками SQL Server 2016".  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [безопасность](#Security)  
  
-   **Для перестроения индекса в режиме «в сети» используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Рекомендуется выполнять операции с индексами в сети в производственной среде, работающей 24 часа в сутки и семь дней в неделю, когда имеется насущная необходимость одновременных действий пользователей во время выполнения операций с индексами.  
  
-   Параметр ONLINE доступен в следующих инструкциях языка [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
    -   [CREATE INDEX](../../t-sql/statements/create-index-transact-sql.md)  
  
    -   [ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md)  
  
    -   [DROP INDEX](../../t-sql/statements/drop-index-transact-sql.md)  
  
    -   [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) (чтобы добавить или удалить ограничения UNIQUE или PRIMARY KEY с параметром индекса CLUSTERED)  
  
-   Дополнительные ограничения и ограничения, касающиеся создания, восстановления или удаления индексов в режиме "в сети", см. в разделе [Инструкции по операциям с индексами в сети](../../relational-databases/indexes/guidelines-for-online-index-operations.md).  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Необходимо разрешение ALTER для таблицы или представления.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-rebuild-an-index-online"></a>Перестроение индекса в режиме «в сети»  
  
1.  В обозревателе объектов щелкните знак «плюс», чтобы развернуть базу данных, содержащую таблицу, в которой необходимо перестроить индекс в режиме «в сети».  
  
2.  Разверните папку **Таблицы**.  
  
3.  Щелкните знак «плюс», чтобы развернуть таблицу, в которой необходимо перестроить индекс в режиме «в сети».  
  
4.  Разверните папку **Индексы** .  
  
5.  Щелкните правой кнопкой мыши индекс, который нужно перестроить в режиме "в сети", и выберите **Свойства**.  
  
6.  В разделе **Выбор страницы**щелкните **Параметры**.  
  
7.  Выберите свойство **Разрешить обработку DML в сети**и выберите из списка значение **True** .  
  
8.  Нажмите кнопку **ОК**.  
  
9. Щелкните правой кнопкой мыши индекс, который нужно перестроить в режиме "в сети", и выберите пункт **Перестроить**.  
  
10. В диалоговом окне **Перестроение индексов** убедитесь, что нужный индекс приведен в сетке **Индексы для перестройки** и нажмите кнопку **ОК**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
### <a name="to-create-rebuild-or-drop-an-index-online"></a>Создание, перестроение и удаление индекса в режиме «в сети»  
  
В следующем примере показано, как перестроить имеющийся онлайн-индекс в базе данных AdventureWorks.

```sql
ALTER INDEX AK_Employee_NationalIDNumber
    ON HumanResources.Employee
    REBUILD WITH (ONLINE = ON);
```  
  
В следующем примере кластеризованный индекс удаляется в режиме в сети и результирующая таблица (куча) перемещается в файловую группу `NewGroup` с использованием предложения `MOVE TO` . Представления каталога `sys.indexes`, `sys.tables`и `sys.filegroups` запрашиваются для проверки размещения индекса и таблицы в файловых группах до и после перемещения.  
  
[!code-sql[IndexDDL#DropIndex4](../../relational-databases/indexes/codesnippet/tsql/perform-index-operations_1.sql)]  
  
Дополнительные сведения см. в статье [ALTER INDEX (Transact-SQL)](../../t-sql/statements/alter-index-transact-sql.md).  
