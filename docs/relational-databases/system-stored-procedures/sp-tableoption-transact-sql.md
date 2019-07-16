---
title: sp_tableoption (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 09/11/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_tableoption_TSQL
- sp_tableoption
dev_langs:
- TSQL
helpviewer_keywords:
- sp_tableoption
ms.assetid: 0a57462c-1057-4c7d-bce3-852cc898341d
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 15c3c9716adefbb95d24c9528dce8607678998c8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68096058"
---
# <a name="sptableoption-transact-sql"></a>sp_tableoption (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Устанавливает значения параметров для определяемых пользователем таблиц. sp_tableoption может использоваться для контроля внутристрокового поведения таблиц со **varchar(max)** , **nvarchar(max)** , **varbinary(max)** , **xml**, **текст**, **ntext**, **изображение**, или столбцы больших определяемых пользователем типов.  
  
> [!IMPORTANT]  
>  Параметр text in row будет исключен в следующей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Для хранения данных больших значений, мы рекомендуем использовать из **varchar(max)** , **nvarchar(max)** и **varbinary(max)** типов данных.  
  

 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_tableoption [ @TableNamePattern = ] 'table'   
     , [ @OptionName = ] 'option_name'   
     ,[ @OptionValue =] 'value'  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @TableNamePattern =] '*таблицы*"  
 Уточненное или неуточненное имя пользовательской таблицы базы данных. Если указано полное имя таблицы, включая имя базы данных, в качестве последнего должно использоваться имя текущей базы данных. Параметры таблицы нельзя установить одновременно для нескольких таблиц. *Таблица* — **nvarchar(776)** , не имеет значения по умолчанию.  
  
 [ @OptionName =] '*option_name*"  
 Название параметра таблицы. *option_name* — **varchar(35)** , без значения по умолчанию NULL. *option_name* может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|table lock on bulk load|Если отключено (по умолчанию), то процесс массовой загрузки в пользовательских таблицах получает блокировку строк. Если включено, то процесс массовой загрузки в пользовательских таблицах получает блокировку массовых обновлений.|  
|блокировка вставки строк|Больше не поддерживается.<br /><br /> Этот параметр не влияет на свойства блокировки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и включается только для совместимости существующих скриптов и процедур.|  
|text in row|При значении OFF или 0 (отключено по умолчанию) текущее поведение не меняется и в строке отсутствует блок больших двоичных объектов (BLOB).<br /><br /> При указании и @OptionValue имеет значение ON (включено) или целое число от 24 до 7 000, то новые **текст**, **ntext**, или **изображение** непосредственно в строке данных хранятся строки. Все существующие BLOB-ОБЪЕКТОВ (больших двоичных объектов: **текст**, **ntext**, или **изображение** данных) будет изменен на формат text in row при обновлении значения BLOB-ОБЪЕКТОВ. Дополнительные сведения см. в подразделе "Примечания".|  
|large value types out of row|1 = **varchar(max)** , **nvarchar(max)** , **varbinary(max)** , **xml** и хранения столбцов больших определяемого пользователем типа (UDT) в таблице вне строки, с 16-байтовым указателем на корень.<br /><br /> 0 = **varchar(max)** , **nvarchar(max)** , **varbinary(max)** , **xml** и большие значения UDT хранятся прямо в строке с данными, до предельного размера 8000 байт и пока значение умещается в записи. Если значение не умещается в записи, то указатель хранится в строке, а все остальное хранится вне строки в области хранения объектов LOB. Значение по умолчанию — 0.<br /><br /> Большой определяемого пользователем типа (UDT) применяется к: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. <br /><br /> Используйте параметр TEXTIMAGE_ON [CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md) для указания расположения для хранения типов данных большого размера. |  
|формат хранения vardecimal|**Применимо к**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Значения TRUE, ON или 1 означают, что для указанной таблицы включен формат хранения vardecimal. Значения FALSE, OFF или 0 означают, что для таблицы не включен формат хранения vardecimal. Формат хранения vardecimal можно включить только в том случае, если базы данных включен формат хранения vardecimal с помощью [sp_db_vardecimal_storage_format](../../relational-databases/system-stored-procedures/sp-db-vardecimal-storage-format-transact-sql.md). В [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версиях **vardecimal** формат является устаревшим. Вместо этого используйте сжатие ROW. Дополнительные сведения см. в разделе [Data Compression](../../relational-databases/data-compression/data-compression.md). Значение по умолчанию — 0.|  
  
 [ @OptionValue =] '*значение*"  
 Является ли *option_name* включен (TRUE, ON или 1) или выключен (FALSE, OFF или 0). *значение* — **varchar(12)** , не имеет значения по умолчанию. *значение* регистр не учитывается.  
  
 Для параметра text in row допустимыми значениями являются 0, ON, OFF или целое число в диапазоне от 24 до 7 000. Когда *значение* имеет значение ON, ограничение по умолчанию равно 256 байт.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или номер ошибки (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 Процедура sp_tableoption может использоваться только для установки значений параметра для пользовательских таблиц. Чтобы отобразить свойства таблицы, используйте OBJECTPROPERTY.  
  
 Параметр text in row процедуры sp_tableoption может быть включен или выключен только на таблицах, содержащих текстовые столбцы. Если таблица не содержит текстового столбца, в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] происходит ошибка.  
  
 Если параметр text in row включен, @OptionValue параметр позволяет пользователям задать максимальный размер хранения в строке для BLOB-ОБЪЕКТА. Значение по умолчанию равно 256 байт, но значения могут располагаться в диапазоне с 24 по 7 000 байт.  
  
 **текст**, **ntext**, или **изображение** в строке данных хранятся строки, если применяются следующие условия:  
  
-   text in row доступен;  
  
-   Длина строки не превышает предел, указанный в @OptionValue  
  
-   в строке данных достаточно места.  
  
 Если в строке данных хранятся строки BLOB, считывание и запись **текст**, **ntext**, или **изображение** строки могут быть так же быстро, как считывание и запись символьных и двоичных строк. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не требуется получать доступ к отдельным страницам для считывания или записи строки BLOB.  
  
 Если **текст**, **ntext**, или **изображение** строка превышает максимальный предел или доступное пространство в строке, указатели вместо хранятся в строке. Тем не менее применяются условия для хранения строк типа BLOB в строке. В строке данных для хранения указателей должно быть достаточно места.  
  
 Строки и указатели BLOB, хранящиеся в строке таблицы, рассматриваются так же, как строки переменной длины. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует только число байтов, необходимое для хранения строки или указателя.  
  
 Существующие строки BLOB преобразуются через некоторое время после первого включения text in row. Строки преобразуются только при обновлении. Аналогичным образом, когда текст в предела параметра строки увеличивается, **текст**, **ntext**, или **изображение** строк, уже содержащиеся в строке данных не будут преобразовываться в соответствовать новому ограничению до времени они обновляются.  
  
> [!NOTE]  
>  Отключение параметра text in row или уменьшение предела параметра потребует преобразования всех BLOB; поэтому процесс может занять много времени, в зависимости от того, какое число строк BLOB необходимо преобразовать. Во время процесса преобразования таблица блокируется.  
  
 Для табличной переменной, включая функцию, которая возвращает табличную переменную, параметр text in row включен автоматически и имеет значение параметра inline limit, по умолчанию равное 256. Этот параметр нельзя изменить.  
  
 Параметр text in row поддерживает функции TEXTPTR, WRITETEXT, UPDATETEXT и READTEXT. Пользователи могут считывать части BLOB с помощью функции SUBSTRING(), но при этом следует помнить, что внутристрочные текстовые указатели по длине и пределам чисел отличаются от других текстовых указателей.  
  
 Чтобы можно было перевести таблицу из формата хранения vardecimal обратно в формат хранения decimal, база данных должна находиться в режиме восстановления SIMPLE. Изменение режима восстановления разорвет цепочку журналов, используемую для целей резервного копирования, поэтому следует создать полную резервную копию базы данных сразу после отключения формата хранения vardecimal в таблице.  
  
 При преобразовании мелких и средних типов с большими значениями (varchar(max), nvarchar(max), или varbinary(max)) и большинство инструкций не ссылаются на столбцы типов больших значений в вашей среде, рассмотрите возможность существующий столбец типа данных LOB (text, ntext или image) Изменение **large_value_types_out_of_row** для **1** Чтобы получить оптимальную производительность. Когда **large_value_types_out_of_row** изменяется значение параметра, в существующие varchar(max), nvarchar(max), varbinary(max), и XML-значения не будут преобразованы моментально. Хранилище строк изменяется, так как они в последующем обновляются. Любые новые значения, которые добавляются в таблицу, хранятся согласно действующему параметру таблицы. Для немедленного получения результатов, либо сделать копию данных и затем снова заполните таблицу после изменения **large_value_types_out_of_row** Установка или обновление каждого столбца типы больших значений мелких и средних на самого себя, чтобы в хранилище строк в силе изменяется с параметром таблицы. Рассмотрим перестройку индексов в таблице после обновления или повторного заполнения для сжатия таблицы. 
    
  
## <a name="permissions"></a>Разрешения  
 Чтобы выполнить процедуру sp_tableoption, требуется разрешение ALTER на таблицу.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-storing-xml-data-out-of-the-row"></a>A. Хранение XML-данных вне строки  
 Следующий пример указывает, что **xml** данные в `HumanResources.JobCandidate` таблицы должны храниться вне строки.  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_tableoption 'HumanResources.JobCandidate', 'large value types out of row', 1;  
```  
  
### <a name="b-enabling-vardecimal-storage-format-on-a-table"></a>Б. Включение формата хранения vardecimal для таблицы  
 В следующем примере изменяется `Production.WorkOrderRouting` таблицу для хранения `decimal` в тип данных `vardecimal` формат хранения.  

```sql  
USE master;  
GO  
-- The database must be enabled for vardecimal storage format  
-- before a table can be enabled for vardecimal storage format  
EXEC sp_db_vardecimal_storage_format 'AdventureWorks2012', 'ON';  
GO  
USE AdventureWorks2012;  
GO  
EXEC sp_tableoption 'Production.WorkOrderRouting',   
   'vardecimal storage format', 'ON';  
```  
  
## <a name="see-also"></a>См. также  
 [sys.tables (Transact-SQL)](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)   
 [OBJECTPROPERTY (Transact-SQL)](../../t-sql/functions/objectproperty-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Хранимым процедурам ядра СУБД &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)  
  
  
