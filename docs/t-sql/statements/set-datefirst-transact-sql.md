---
title: SET DATEFIRST (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SET DATEFIRST
- SET_DATEFIRST_TSQL
- DATEFIRST_TSQL
- DATEFIRST
dev_langs:
- TSQL
helpviewer_keywords:
- first day of week [SQL Server]
- day of week [SQL Server]
- SET DATEFIRST option [SQL Server]
- DATEFIRST option [SQL Server]
- weekdays [SQL Server]
- options [SQL Server], date
ms.assetid: 6b0d0e52-8ac1-4f88-b091-f98d6fb8574a
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 19019a0493ef20aac9ab51090d64646d5d626185
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68041801"
---
# <a name="set-datefirst-transact-sql"></a>SET DATEFIRST (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Устанавливает первый день недели в виде числа от 1 до 7.  
  
 Обзор всех типов данных и функций даты и времени в языке [!INCLUDE[tsql](../../includes/tsql-md.md)] см. в статье [Типы данных и функции даты и времени (Transact-SQL)](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
SET DATEFIRST { number | @number_var }   
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
SET DATEFIRST 7 ;  
```  
  
## <a name="arguments"></a>Аргументы  
 *number* |  **@** _number_var_  
 Целочисленное значение, указывающее первый день недели. Может быть одним из указанных далее.  
  
|Значение|Первый день недели|  
|-----------|------------------------------|  
|**1**|Понедельник|  
|**2**|Вторник|  
|**3**|Среда|  
|**4**|Четверг|  
|**5**|Пятница|  
|**6**|Суббота|  
|**7** (по умолчанию, американский английский)|Воскресенье|  
  
## <a name="remarks"></a>Примечания  
 Для просмотра текущего значения SET DATEFIRST используется функция [@@DATEFIRST](../../t-sql/functions/datefirst-transact-sql.md).  
  
 Аргумент функции SET DATEFIRST устанавливается во время выполнения или запуска, а не во время синтаксического анализа.  
  
 Указание SET DATEFIRST не влияет на DATEDIFF. DATEDIFF всегда считает воскресенье первым днем недели, чтобы обеспечить детерминизм работы функции.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом роли **public**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере отображается день недели для даты и показан результат изменения параметра `DATEFIRST`.  
  
```  
-- SET DATEFIRST to U.S. English default value of 7.  
SET DATEFIRST 7;  
  
SELECT CAST('1999-1-1' AS datetime2) AS SelectDate  
    ,DATEPART(dw, '1999-1-1') AS DayOfWeek;  
-- January 1, 1999 is a Friday. Because the U.S. English default   
-- specifies Sunday as the first day of the week, DATEPART of 1999-1-1  
-- (Friday) yields a value of 6, because Friday is the sixth day of the   
-- week when you start with Sunday as day 1.  
  
SET DATEFIRST 3;  
-- Because Wednesday is now considered the first day of the week,  
-- DATEPART now shows that 1999-1-1 (a Friday) is the third day of the   
-- week. The following DATEPART function should return a value of 3.  
SELECT CAST('1999-1-1' AS datetime2) AS SelectDate  
    ,DATEPART(dw, '1999-1-1') AS DayOfWeek;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)  
  
  

