---
title: Репликация изменений схемы | Документация Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], schema changes
- schemas [SQL Server replication], replicating changes
ms.assetid: c09007f0-9374-4f60-956b-8a87670cd043
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a436eb86fdaad06e97da94e821d50437e6d938ee
ms.sourcegitcommit: 636c02bd04f091ece934e78640b2363d88cac28d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2019
ms.locfileid: "67860576"
---
# <a name="replicate-schema-changes"></a>Репликация изменений схемы
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этом разделе описывается процесс репликации изменений схемы в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 Если в опубликованную статью внести следующие изменения схемы, они по умолчанию распространяются на подписчики [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
-   ALTER TABLE  
  
-   ALTER VIEW  
  
-   ALTER PROCEDURE  
  
-   ALTER FUNCTION  
  
-   ALTER TRIGGER  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
-   **Для репликации изменений схемы используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Инструкция ALTER TABLE ... DROP COLUMN всегда реплицируется для всех подписчиков, чьи подписки содержат удаляемые столбцы, даже при отключенной репликации изменений схемы.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Если реплицировать изменения схемы для публикации не требуется, отключите репликацию изменений схемы в диалоговом окне **Свойства публикации — \<публикация>** . Дополнительные сведения о доступе к этому диалоговому окну см. в разделе [Просмотр и изменение свойств публикации](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### <a name="to-disable-replication-of-schema-changes"></a>Отключение репликации изменений схемы  
  
1.  На странице **Параметры подписки** диалогового окна **Свойства публикации — \<публикация>** установите для свойства **Реплицировать изменения схемы** значение **False**.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

[!INCLUDE[freshInclude](../../../includes/paragraph-content/fresh-note-steps-feedback.md)]

     To propagate only specific schema changes, set the property to **True** before a schema change, and then set it to **False** after the change is made. Conversely, to propagate most schema changes, but not a given change, set the property to **False** before the schema change, and then set it to **True** after the change is made.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Можно использовать хранимые процедуры репликации для указания, следует ли реплицировать эти изменения схемы. Используемая хранимая процедура зависит от типа публикации.  
  
#### <a name="to-create-a-snapshot-or-transactional-publication-that-does-not-replicate-schema-changes"></a>Создание публикации моментальных снимков или публикации транзакций без репликации изменений схемы  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addpublication (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md), указав в параметре **@replicate_ddl** значение **0**. Дополнительные сведения см. в разделе [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md).  
  
#### <a name="to-create-a-merge-publication-that-does-not-replicate-schema-changes"></a>Создание публикации слиянием без репликации изменений схемы  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addmergepublication (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md), указав в параметре **@replicate_ddl** значение **0**. Дополнительные сведения см. в разделе [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md).  
  
#### <a name="to-temporarily-disable-replicating-schema-changes-for-a-snapshot-or-transactional-publication"></a>Временное отключение репликации изменений схемы для публикации моментальных снимков или публикации транзакций  
  
1.  Для публикации с репликацией изменений схемы выполните процедуру [sp_changepublication (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md), указав в параметре **@property** значение **replicate_ddl**, а в параметре **@value** — значение **0**.  
  
2.  Выполните команду DDL на опубликованном объекте.  
  
3.  (Необязательно.) Для повторного включения репликации изменений схемы выполните процедуру [sp_changepublication (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md), указав в параметре **@property** значение **replicate_ddl**, а в параметре **@value** — значение **1**.  
  
#### <a name="to-temporarily-disable-replicating-schema-changes-for-a-merge-publication"></a>Временное отключение репликации изменений схемы для публикации слиянием  
  
1.  Для публикации с репликацией изменений схемы выполните процедуру [sp_changemergepublication (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md), указав в параметре **@property** значение **replicate_ddl**, а в параметре **@value** — значение **0**.  
  
2.  Выполните команду DDL на опубликованном объекте.  
  
3.  (Необязательно.) Для повторного включения репликации изменений схемы выполните процедуру [sp_changemergepublication (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md), указав в параметре **@property** значение **replicate_ddl**, а в параметре **@value** — значение **1**.  
  
## <a name="see-also"></a>См. также:  
 [Внесение изменений в схемы баз данных публикации](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)   
 [Внесение изменений в схемы баз данных публикации](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)  
  
  
