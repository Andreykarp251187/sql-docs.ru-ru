---
title: PRINT (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- PRINT_TSQL
- PRINT
dev_langs:
- TSQL
helpviewer_keywords:
- PRINT statement
- user-defined messages [SQL Server]
- messages [SQL Server], PRINT statement
- displaying user-defined messages
- viewing user-defined messages
- conditionally returning messages [SQL Server]
ms.assetid: 32ba0729-c4b5-4cfb-a5aa-e8b9402be028
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: cc83aca49b6147835353538d809be121756ecda6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68072403"
---
# <a name="print-transact-sql"></a>PRINT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает клиенту пользовательское сообщение.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
PRINT msg_str | @local_variable | string_expr  
```  
  
## <a name="arguments"></a>Аргументы  
 *msg_str*  
 Символьная строка или строковая константа Юникода. Дополнительные сведения см. в статье [Константы (Transact-SQL)](../../t-sql/data-types/constants-transact-sql.md).  
  
 **@** *local_variable*  
 Переменная любого допустимого символьного типа данных. Аргумент **@** _local\_variable_ должен иметь тип **char**, **nchar**, **varchar** или **nvarchar** либо должен неявно преобразовываться в эти типы данных.  
  
 *string_expr*  
 Выражение, возвращающее строку. Может содержать объединенные буквенные значения, функции и переменные. Дополнительные сведения см. в разделе [Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md).  
  
## <a name="remarks"></a>Remarks  
 Строка сообщения может иметь длину до 8 000 символов для строки, отличной от Юникода, и 4 000 символов для строки в Юникоде. Более длинные строки усекаются. Типы данных **varchar(max)** и **nvarchar(max)** усекаются до типов данных, которые не длиннее **varchar(8000)** и **nvarchar(4000)** .  
  
 Для возвращения сообщений можно также использовать функцию RAISERROR. Преимущества функции RAISERROR перед функцией PRINT:  
  
-   функция RAISERROR поддерживает вставку аргументов в строку сообщения об ошибке с помощью механизма, основанного на функции printf из стандартной библиотеки языка С;  
  
-   в дополнение к текстовому сообщению, функция RAISERROR может в сообщении указать уникальный номер ошибки, степень ее серьезности и код состояния;  
  
-   функция RAISERROR может быть использована для возвращения пользовательских сообщений, созданных с помощью системной хранимой процедуры sp_addmessage.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-conditionally-executing-print-if-exists"></a>A. Печать, выполняемая по условию (IF EXISTS)  
 В следующем примере инструкция `PRINT` применяется для возвращения сообщения по условию.  
  
```  
IF @@OPTIONS & 512 <> 0  
    PRINT N'This user has SET NOCOUNT turned ON.';  
ELSE  
    PRINT N'This user has SET NOCOUNT turned OFF.';  
GO  
```  
  
### <a name="b-building-and-displaying-a-string"></a>Б. Построение и отображение строки  
 В следующем примере результаты функции `GETDATE` преобразуются в тип данных `nvarchar` и объединяются с текстовой строкой для последующего возврата функцией `PRINT`.  
  
```  
-- Build the message text by concatenating  
-- strings and expressions.  
PRINT N'This message was printed on '  
    + RTRIM(CAST(GETDATE() AS nvarchar(30)))  
    + N'.';  
GO  
-- This example shows building the message text  
-- in a variable and then passing it to PRINT.  
-- This was required in SQL Server 7.0 or earlier.  
DECLARE @PrintMessage nvarchar(50);  
SET @PrintMessage = N'This message was printed on '  
    + RTRIM(CAST(GETDATE() AS nvarchar(30)))  
    + N'.';  
PRINT @PrintMessage;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-conditionally-executing-print"></a>В. Печать, выполняемая по условию  
 В следующем примере инструкция `PRINT` применяется для возвращения сообщения по условию.  
  
```  
IF DB_ID() = 1  
    PRINT N'The current database is master.';  
ELSE  
    PRINT N'The current database is not master.';  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [DECLARE @local_variable (Transact-SQL)](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
 [RAISERROR (Transact-SQL)](../../t-sql/language-elements/raiserror-transact-sql.md)  
  
  

