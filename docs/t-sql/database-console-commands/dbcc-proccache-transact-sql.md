---
title: DBCC PROCCACHE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 11/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DBCC PROCCACHE
- DBCC_PROCCACHE_TSQL
- PROCCACHE_TSQL
- PROCCACHE
dev_langs:
- TSQL
helpviewer_keywords:
- procedure cache [SQL Server]
- displaying procedure cache information
- DBCC PROCCACHE statement
ms.assetid: 7a4f9f8a-13ff-4bf2-ba29-c17012a23659
author: pmasl
ms.author: umajay
ms.openlocfilehash: d021905cfd1a75a35487499ef383d6e0a78c8323
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85685476"
---
# <a name="dbcc-proccache-transact-sql"></a>DBCC PROCCACHE (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Отображает сведения о кэше процедур в табличном формате.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
DBCC PROCCACHE [ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>Аргументы  
 WITH  
 Позволяет указывать параметры.  
  
 NO_INFOMSGS  
 Подавляет все информационные сообщения с уровнями серьезности от 0 до 10.  
  
## <a name="remarks"></a>Remarks  
Кэш процедур служит для кэширования скомпилированных и исполняемых планов с целью ускорить выполнение пакетов. Элементы кэша процедур находятся на уровне пакета. Кэш процедур содержит следующие записи:
-   Скомпилированные планы  
-   Планы выполнения  
-   Дерево алгебризатора  
-   Расширенные процедуры  
  
## <a name="result-sets"></a>Результирующие наборы  
В следующей таблице описаны столбцы в результирующем наборе.
  
|Имя столбца|Description|  
|-----------------|-----------------|  
|**num proc buffs**|Общее количество страниц, используемое всеми записями кэша процедур.|  
|**num proc buffs used**|Общее число страниц, занятых всеми используемыми в данный момент записями.|  
|**num proc buffs active**|Только для обратной совместимости. Общее число страниц, занятых всеми используемыми в данный момент записями.|  
|**proc cache size**|Общее число элементов в кэше процедур.|  
|**proc cache used**|Общее число элементов, используемых в настоящий момент.|  
|**proc cache active**|Только для обратной совместимости. Общее число элементов, используемых в настоящий момент.|  
  
## <a name="permissions"></a>Разрешения  
Необходимо быть членом предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** .
  
## <a name="see-also"></a>См. также:  
[DBCC (Transact-SQL)](../../t-sql/database-console-commands/dbcc-transact-sql.md)
  
  
