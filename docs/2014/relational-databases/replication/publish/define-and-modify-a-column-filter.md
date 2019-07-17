---
title: Определение или изменение фильтра столбцов | Документация Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server replication], column
- modifying filters, column
- modifying filters
- column filters [SQL Server replication]
ms.assetid: d7c3186a-9a8c-45d8-ab34-05beec4c26dd
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8e0c26e32425f204f7dab29aa65c66f3a11f09d7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68212128"
---
# <a name="define-and-modify-a-column-filter"></a>Определение или изменение фильтра столбцов
  В этом разделе описывается определение и изменение фильтра столбцов [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] при помощи среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
-   **Для определения и изменения фильтра столбцов используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   К некоторым столбцам фильтрация не может применяться. Дополнительные сведения см. в статье [Фильтрация опубликованных данных](filter-published-data.md). При изменении фильтра столбцов после инициализации подписок необходимо создать новый моментальный снимок и выполнить повторную инициализацию всех подписок после выполнения изменений. Дополнительные сведения о требованиях к изменениям свойств см. в статье [Изменение свойств публикации и статьи](change-publication-and-article-properties.md).  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Определение фильтров столбцов выполняется на странице **Статьи** мастера создания публикации. Дополнительные сведения об использовании мастера создания публикации см. в статье [Создание публикации](create-a-publication.md).  
  
 Определите и измените фильтры столбцов на странице **Статьи** диалогового окна **Свойства публикации — \<публикация>** . Дополнительные сведения об изменении свойств публикаций и статей см. в [этой статье](view-and-modify-publication-properties.md).  
  
#### <a name="to-define-a-column-filter"></a>Определение фильтра столбцов  
  
1.  На странице **Статьи** мастера создания публикации раскройте таблицу, которую необходимо отфильтровать, на панели **Объекты для публикации** .  
  
2.  Снимите флажки рядом со столбцами, которые необходимо отфильтровать.  
  
#### <a name="to-modify-column-filtering"></a>Изменение параметров фильтрации столбцов  
  
1.  На странице **Статьи** диалогового окна **Свойства публикации — \<публикация>** , на панели **Объекты для публикации** разверните таблицу, которую хотите отфильтровать.  
  
2.  Снимите флажки рядом со столбцами, которые необходимо отфильтровать, и проверьте, чтобы были установлены флажки для столбцов, которые должны быть включены в статью.  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 При создании статей таблицы можно определить столбцы, которые нужно включить в статью, и изменить эти столбцы после определения статьи. Можно создать и изменить фильтруемые столбцы программно с помощью хранимых процедур репликации.  
  
> [!NOTE]  
>  В следующей процедуре предполагается, что базовая таблица не изменилась. Сведения о репликации изменений, выполненных с помощью языка DDL, в опубликованные таблицы см. в статье [Внесение изменений в схемы баз данных публикации](make-schema-changes-on-publication-databases.md).  
  
#### <a name="to-define-a-column-filter-for-an-article-published-in-a-snapshot-or-transactional-publication"></a>Определение фильтра столбца для статьи, опубликованной в публикации моментальных снимков или публикации транзакций  
  
1.  Определите статью для фильтрации. Дополнительные сведения см. в статье [Define an Article](define-an-article.md).  
  
2.  На издателе в базе данных публикации выполните хранимую процедуру [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql). Столбцы для включения в статью или удаления из нее будут определены.  
  
    -   При публикации нескольких столбцов из таблицы с большим числом столбцов выполните хранимую процедуру [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql) один раз для каждого добавляемого столбца. Укажите имя столбца в параметре **@column** и значение **add** в параметре **@operation** .  
  
    -   При публикации большинства столбцов таблицы с большим числом столбцов выполните хранимую процедуру [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql), указав значение **NULL** в параметре **@column** и значение **add** в параметре **@operation** , чтобы добавить все столбцы. Затем выполните хранимую процедуру [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql)один раз для каждого исключаемого столбца, указав значение **drop** в параметре **@operation** и имя исключаемого столбца в параметре **@column** .  
  
3.  В базе данных публикации на издателе выполните процедуру [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql). Укажите имя публикации в параметре **@publication** , а имя отфильтрованной статьи — в параметре **@article** . Будут созданы объекты синхронизации для отфильтрованной статьи.  
  
#### <a name="to-change-a-column-filter-to-include-additional-columns-for-an-article-published-in-a-snapshot-or-transactional-publication"></a>Изменение фильтра столбца с целью включения дополнительных столбцов в статью, опубликованную в публикации моментальных снимков или публикации транзакций  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql) один раз для каждого добавляемого столбца. Укажите имя столбца в параметре **@column** и значение **add** в параметре **@operation** .  
  
2.  В базе данных публикации на издателе выполните процедуру [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql). Укажите имя публикации в параметре **@publication** , а имя отфильтрованной статьи — в параметре **@article** . Если у публикации есть существующие подписки, укажите в параметре **@change_active** в параметре **@change_active** . Объекты синхронизации для отфильтрованной статьи при этом будут повторно созданы.  
  
3.  Чтобы сформировать обновленный моментальный снимок, перезапустите задание агента моментальных снимков для публикации.  
  
4.  Повторная инициализация подписок. Дополнительные сведения см. в статье [Повторная инициализация подписок](../reinitialize-subscriptions.md).  
  
#### <a name="to-change-a-column-filter-to-remove-columns-for-an-article-published-in-a-snapshot-or-transactional-publication"></a>Изменение фильтра столбца с целью удаления столбцов из статьи, опубликованной в публикации моментальных снимков или публикации транзакций  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql) один раз для каждого удаляемого столбца. Укажите имя столбца в параметре **@column** и значение **drop** в параметре **@operation** .  
  
2.  В базе данных публикации на издателе выполните процедуру [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql). Укажите имя публикации в параметре **@publication** , а имя отфильтрованной статьи — в параметре **@article** . Если у публикации есть существующие подписки, укажите в параметре **@change_active** в параметре **@change_active** . Объекты синхронизации для отфильтрованной статьи при этом будут повторно созданы.  
  
3.  Чтобы сформировать обновленный моментальный снимок, перезапустите задание агента моментальных снимков для публикации.  
  
4.  Повторная инициализация подписок. Дополнительные сведения см. в статье [Повторная инициализация подписок](../reinitialize-subscriptions.md).  
  
#### <a name="to-define-a-column-filter-for-an-article-published-in-a-merge-publication"></a>Определение фильтра столбца для статьи, опубликованной в публикации слиянием  
  
1.  Определите статью для фильтрации. Дополнительные сведения см. в статье [определить статью](define-an-article.md).  
  
2.  На издателе в базе данных публикации выполните хранимую процедуру [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql). Столбцы для включения в статью или удаления из нее будут определены.  
  
    -   При публикации нескольких столбцов таблицы с большим числом столбцов выполните хранимую процедуру [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql) один раз для каждого добавляемого столбца. Укажите имя столбца в параметре **@column** и значение **add** в параметре **@operation** .  
  
    -   При публикации большинства столбцов таблицы с большим числом столбцов выполните хранимую процедуру [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql), указав значение **NULL** в параметре **@column** и значение **add** в параметре **@operation** , чтобы добавить все столбцы. Затем выполните хранимую процедуру [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql)один раз для каждого исключаемого столбца, указав значение **drop** в параметре **@operation** и имя исключаемого столбца в параметре **@column** .  
  
#### <a name="to-change-a-column-filter-to-include-additional-columns-for-an-article-published-in-a-merge-publication"></a>Изменение фильтра столбца с целью включения дополнительных столбцов в статью, опубликованную в публикации слиянием  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql) один раз для каждого добавляемого столбца. Укажите имя столбца в параметре **@column** , значение **add** в параметре **@operation** и значение **@change_active** как в параметре **@force_invalidate_snapshot** , так и в параметре **@force_reinit_subscription** .  
  
2.  Чтобы сформировать обновленный моментальный снимок, перезапустите задание агента моментальных снимков для публикации.  
  
3.  Повторная инициализация подписок. Дополнительные сведения см. в статье [Повторная инициализация подписок](../reinitialize-subscriptions.md).  
  
#### <a name="to-change-a-column-filter-to-remove-columns-for-an-article-published-in-a-merge-publication"></a>Изменение фильтра столбца с целью удаления столбцов из статьи, опубликованной в публикации слиянием  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql) один раз для каждого удаляемого столбца. Укажите имя столбца в параметре **@column** , значение **drop** в параметре **@operation** и значение **@change_active** как в параметре **@force_invalidate_snapshot** , так и в параметре **@force_reinit_subscription** .  
  
2.  Чтобы сформировать обновленный моментальный снимок, перезапустите задание агента моментальных снимков для публикации.  
  
3.  Повторная инициализация подписок. Дополнительные сведения см. в статье [Повторная инициализация подписок](../reinitialize-subscriptions.md).  
  
###  <a name="TsqlExample"></a> Примеры (Transact-SQL)  
 В этом примере репликации транзакций столбец `DaysToManufacture` удаляется из статьи, основанной на таблице `Product` .  
  
 [!code-sql[HowTo#sp_AddTranArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createtranpub.sql#sp_addtranarticle)]  
  
 В этом примере репликации слиянием столбец `CreditCardApprovalCode` удаляется из статьи, основанной на таблице `SalesOrderHeader` .  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepub.sql#sp_addmergearticle)]  
  
## <a name="see-also"></a>См. также  
 [Изменение свойств публикации и статьи](change-publication-and-article-properties.md)   
 [Фильтрация опубликованных данных](filter-published-data.md)   
 [Фильтрация опубликованных данных для репликации слиянием](../merge/filter-published-data-for-merge-replication.md)  
  
  
