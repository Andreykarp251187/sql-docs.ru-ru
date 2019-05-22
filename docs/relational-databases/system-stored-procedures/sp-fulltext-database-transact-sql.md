---
title: sp_fulltext_database (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_fulltext_database_TSQL
- sp_fulltext_database
dev_langs:
- TSQL
helpviewer_keywords:
- sp_fulltext_database
ms.assetid: eeb1e151-eb00-484c-8fd1-5641e621ffc6
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ef93c354333bd4a99fedc83cb950021367a6cc2f
ms.sourcegitcommit: 5ed48c7dc6bed153079bc2b23a1e0506841310d1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/21/2019
ms.locfileid: "65983039"
---
# <a name="spfulltextdatabase-transact-sql"></a>sp_fulltext_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Не влияет на полнотекстовые каталоги в [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версиях и поддерживается только для обеспечения обратной совместимости. **sp_fulltext_database** не отключает механизм полнотекстового поиска для конкретной базы данных. В [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] полнотекстовое индексирование всегда включено для всех баз данных, созданных пользователем.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Вместо этого используйте [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_fulltext_database [@action=] 'action'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @action = ] 'action'` — Это действие, которое должно быть выполнено. **Действие** — **varchar(20)**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**enable**|Поддерживается только для обеспечения обратной совместимости. Не действует на полнотекстовые каталоги в [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версиях.|  
|**Отключить**|Поддерживается только для обеспечения обратной совместимости. Не действует на полнотекстовые каталоги в [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версиях.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Примечания  
 В [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версиях полнотекстовое индексирование отключить нельзя. Отключение полнотекстового индексирования не удаляет строки из **sysfulltextcatalogs** и не означает, что таблицы с поддержкой полнотекстового поиска, больше не помечаются для полнотекстового индексирования. Все определения полнотекстовых метаданных продолжают храниться в системных таблицах.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера и **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_fulltext_database**.  
  
## <a name="see-also"></a>См. также  
 [DATABASEPROPERTYEX (Transact-SQL)](../../t-sql/functions/databasepropertyex-transact-sql.md)   
 [FULLTEXTSERVICEPROPERTY (Transact-SQL)](../../t-sql/functions/fulltextserviceproperty-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
