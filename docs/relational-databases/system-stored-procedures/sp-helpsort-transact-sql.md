---
title: sp_helpsort (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpsort_TSQL
- sp_helpsort
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpsort
ms.assetid: 2a88d079-3755-43cb-8a54-97d0114149e6
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 511b5b8f01a96f860d9f0c4266f92b323e6f1240
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67997354"
---
# <a name="sphelpsort-transact-sql"></a>sp_helpsort (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Показывает порядок сортировки и кодировку для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpsort  
```  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Возвращает параметры сортировки по умолчанию для сервера.  
  
## <a name="remarks"></a>Примечания  
 Если экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] устанавливается вместе с параметрами сортировки, указанными на совместимость с предшествующими [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], **sp_helpsort** возвращает пустые результаты. В этом случае можно определить параметры сортировки путем запроса объекта SERVERPROPERTY, например: `SELECT SERVERPROPERTY ('Collation');`.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом роли **public**.  
  
## <a name="examples"></a>Примеры  
 Следующий пример отображает имя порядка сортировки по умолчанию сервера, его кодировку и основные значения сортировки.  
  
```  
sp_helpsort;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Server default collation`  
  
 `------------------------`  
  
 `Latin1-General, case-sensitive, accent-sensitive, kanatype-insensitive, width-insensitive for Unicode Data, SQL Server Sort Order 51 on Code Page 1252 for non-Unicode Data.`  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Хранимым процедурам ядра СУБД &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [COLLATE (Transact-SQL)](~/t-sql/statements/collations.md)   
 [sys.fn_helpcollations (Transact-SQL)](../../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md)   
 [SERVERPROPERTY (Transact-SQL)](../../t-sql/functions/serverproperty-transact-sql.md)  
  
  
