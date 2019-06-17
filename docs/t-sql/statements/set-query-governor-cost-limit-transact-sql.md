---
title: SET QUERY_GOVERNOR_COST_LIMIT (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SET QUERY_GOVERNOR_COST_LIMIT
- SET_QUERY_GOVERNOR_COST_LIMIT_TSQL
- QUERY_GOVERNOR_COST_LIMIT
- QUERY_GOVERNOR_COST_LIMIT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SET QUERY_GOVERNOR_COST_LIMIT statement
- connections [SQL Server], overriding
- QUERY_GOVERNOR_COST_LIMIT option
- overriding connection values
ms.assetid: 3424bb44-6915-462d-a8d7-fe834af81387
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 18712418b84197eb80c48d4f86a8ea98092f5764
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62939831"
---
# <a name="set-querygovernorcostlimit-transact-sql"></a>SET QUERY_GOVERNOR_COST_LIMIT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Переопределяет текущее значение параметра **query governor cost limit** для текущего соединения.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET QUERY_GOVERNOR_COST_LIMIT value  
```  
  
## <a name="arguments"></a>Аргументы  
 *value*  
 Значение типа numeric или integer, указывающее максимально возможное время выполнения запроса. Значения округляются в меньшую сторону до ближайшего целого числа. Отрицательные значения округляются до 0. Если задать значение больше нуля, регулятор запросов запрещает выполнение всех запросов, оценочная стоимость которых превышает это значение. Если указать значение 0 (значение по умолчанию), регулятор запросов будет отключен, что разрешает выполнение всех запросов без ограничения времени.  
  
 Цена запроса — это предполагаемое время в секундах, которое требуется для завершения запроса в конкретной конфигурации оборудования.  
  
## <a name="remarks"></a>Remarks  
 Использование инструкции SET QUERY_GOVERNOR_COST_LIMIT относится только к текущему соединению и продолжается в течение текущего соединения. С помощью [параметра конфигурации сервера configure the query governor cost](../../database-engine/configure-windows/configure-the-query-governor-cost-limit-server-configuration-option.md) хранимой процедуры **sp_configure** можно изменить предельное значение стоимости, используемое регулятором запросов в рамках всего сервера. Дополнительные сведения о настройке этого параметра см. в разделах [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) и [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
 Значение параметра SET QUERY_GOVERNOR_COST_LIMIT устанавливается во время выполнения или запуска, но не во время синтаксического анализа.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом роли **public**.  
  
## <a name="see-also"></a>См. также:  
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)  
  
  
