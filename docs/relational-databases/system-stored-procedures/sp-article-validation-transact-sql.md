---
title: sp_article_validation (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_article_validation_TSQL
- sp_article_validation
helpviewer_keywords:
- sp_article_validation
ms.assetid: 44e7abcd-778c-4728-a03e-7e7e78d3ce22
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: be3ccf8b0c85b61f536c381e4a42d1b5e37fbacf
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62998265"
---
# <a name="sparticlevalidation-transact-sql"></a>sp_article_validation (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Инициирует запрос проверки данных для указанной статьи. Эта хранимая процедура выполняется на издателе в базе данных публикации и на подписчике в базе данных подписки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_article_validation [ @publication = ] 'publication'  
    [ , [ @article = ] 'article' ]  
    [ , [ @rowcount_only = ] type_of_check_requested ]  
    [ , [ @full_or_fast = ] full_or_fast ]  
    [ , [ @shutdown_agent = ] shutdown_agent ]  
    [ , [ @subscription_level = ] subscription_level ]  
    [ , [ @reserved = ] reserved ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'` — Имя публикации, в которой находится статья. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
`[ @article = ] 'article'` — Имя статьи для проверки. *статья* — **sysname**, не имеет значения по умолчанию.  
  
`[ @rowcount_only = ] type_of_check_requested` Указывает, если возвращается только число строк для таблицы. *type_of_check_requested* — **smallint**, значение по умолчанию **1**.  
  
 Если **0**, выполнить вычисление количества строк и [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 контрольной суммы, совместимой.  
  
 Если **1**, выполните проверку только количества строк.  
  
 Если **2**, количество строк и двоичной контрольной суммы.  
  
`[ @full_or_fast = ] full_or_fast` Метод, используемый для вычисления количества строк. *full_or_fast* — **tinyint**, и может принимать одно из следующих значений.  
  
|**Значение**|**Описание**|  
|---------------|---------------------|  
|**0**|Выполняет полный подсчет при помощи функции COUNT(*).|  
|**1**|Выполняет быстрый подсчет из **sysindexes.rows**. Подсчет строк в **sysindexes** выполняется быстрее, чем подсчет строк в фактической таблице. Тем не менее **sysindexes** обновляется в фоновом режиме, и количество строк может оказаться неточным.|  
|**2** (по умолчанию)|Выполняет условный быстрый подсчет, при котором сначала применяется быстрый метод, Если быстрый метод дает неточные результаты, переключается на полный подсчет. Если *expected_rowcount* имеет значение NULL и хранимая процедура используется для получения значения, полная функция COUNT(*) всегда используется.|  
  
`[ @shutdown_agent = ] shutdown_agent` Указывает, если агент распространителя завершен немедленно после завершения проверки. *shutdown_agent* — **бит**, значение по умолчанию **0**. Если **0**, агент распространителя не завершает работу. Если **1**, агент распространителя завершает работу после проверки статьи.  
  
`[ @subscription_level = ] subscription_level` Указывает, выбирается ли проверка с помощью набора подписчиков. *уровень_подписки* — **бит**, значение по умолчанию **0**. Если **0**, проверка применяется для всех подписчиков. Если **1**, проверка применяется только к части подписчиков, определяемой вызовами **sp_marksubscriptionvalidation** в текущую открытую транзакцию.  
  
`[ @reserved = ] reserved` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @publisher = ] 'publisher'` Указывает, отличный от [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя. *издатель* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  *издатель* не следует использовать при запросе проверки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_article_validation** используется в репликации транзакций.  
  
 **sp_article_validation** приводит сведения о проверке собрать указанной статьи и отправляет запрос на проверку в журнал транзакций. Когда агент распространителя получает этот запрос, он сравнивает сведения для проверки, указанные в запросе, с таблицей подписчика. Результаты проверки отображаются в мониторе репликации и в виде предупреждений агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="permissions"></a>Разрешения  
 Только пользователи с ВЫБЕРИТЕ все разрешения на исходную таблицу для проверяемой статьи, можно выполнить **sp_article_validation**.  
  
## <a name="see-also"></a>См. также  
 [Проверка реплицированных данных](../../relational-databases/replication/validate-data-at-the-subscriber.md)   
 [sp_marksubscriptionvalidation &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-marksubscriptionvalidation-transact-sql.md)   
 [sp_publication_validation &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-publication-validation-transact-sql.md)   
 [sp_table_validation &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-table-validation-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
