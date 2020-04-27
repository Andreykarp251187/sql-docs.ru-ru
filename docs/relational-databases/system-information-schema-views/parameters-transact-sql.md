---
title: Параметры (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- PARAMETERS_TSQL
- PARAMETERS
dev_langs:
- TSQL
helpviewer_keywords:
- PARAMETERS view
- INFORMATION_SCHEMA.PARAMETERS view
ms.assetid: 06ded0ca-7d21-4400-864a-b801e855b257
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e6d3880c4be8925e6b85a20af1324537e3977ecc
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "68103285"
---
# <a name="parameters-transact-sql"></a>PARAMETERS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает одну строку для каждого параметра определяемой пользователем функции или хранимой процедуры, к которой может получить доступ текущий пользователь в текущей базе данных. Для функций данное представление также возвращает одну строку, содержащую сведения о возвращаемых значениях.  
  
 Чтобы получить сведения из этих представлений, укажите полное имя **INFORMATION_SCHEMA.** _view_name_.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**SPECIFIC_CATALOG**|**nvarchar (** 128 **)**|Имя каталога процедуры, для которой это является параметром.|  
|**SPECIFIC_SCHEMA**|**nvarchar (** 128 **)**|Имя схемы процедуры, для которой это является параметром.<br /><br /> <strong> \* \* Важно \* !</strong> Не используйте INFORMATION_SCHEMA представления для определения схемы объекта. Единственный надежный способ найти схему объекта — направить запрос к представлению каталога sys.objects.|  
|**SPECIFIC_NAME**|**nvarchar (** 128 **)**|Имя процедуры, для которой это является параметром.|  
|**ORDINAL_POSITION**|**int**|Порядковый номер параметра, начиная с 1. Для возвращаемого значения функции это 0.|  
|**PARAMETER_MODE**|**nvarchar (** 10 **)**|Возвращает значение IN для входного параметра, OUT для выходного параметра и INOUT для изменяемого входного параметра.|  
|**IS_RESULT**|**nvarchar (** 10 **)**|Возвращает значение YES, если результат подпрограммы является результатом выполнения функции. В противном случае возвращается значение NO.|  
|**AS_LOCATOR**|**nvarchar (** 10 **)**|Возвращает значение YES, если результат объявлен как указатель. В противном случае возвращается значение NO.|  
|**PARAMETER_NAME**|**nvarchar (** 128 **)**|Имя параметра. Если соответствует результату выполнения функции, то возвращается значение NULL.|  
|**DATA_TYPE**|**nvarchar (** 128 **)**|Тип данных, поддерживаемый системой.|  
|**CHARACTER_MAXIMUM_LENGTH**|**int**|Максимальная длина в символах для двоичных или символьных данных.<br /><br /> -1 для данных типа **XML** и больших значений. В противном случае возвращается значение NULL.|  
|**CHARACTER_OCTET_LENGTH**|**int**|Максимальная длина в байтах для двоичных или символьных данных.<br /><br /> -1 для данных типа **XML** и больших значений. В противном случае возвращается значение NULL.|  
|**COLLATION_CATALOG**|**nvarchar (** 128 **)**|Всегда возвращает значение NULL.|  
|**COLLATION_SCHEMA**|**nvarchar (** 128 **)**|Всегда возвращает значение NULL.|  
|**COLLATION_NAME**|**nvarchar (** 128 **)**|Имя параметров сортировки параметра. Если введенные данные не принадлежат ни к одному из символьных типов, возвращает значение NULL.|  
|**CHARACTER_SET_CATALOG**|**nvarchar (** 128 **)**|Имя каталога кодировки параметра. Если введенные данные не принадлежат ни к одному из символьных типов, возвращает значение NULL.|  
|**CHARACTER_SET_SCHEMA**|**nvarchar (** 128 **)**|Всегда возвращает значение NULL.|  
|**CHARACTER_SET_NAME**|**nvarchar (** 128 **)**|Имя кодировки параметра. Если введенные данные не принадлежат ни к одному из символьных типов, возвращает значение NULL.|  
|**NUMERIC_PRECISION**|**tinyint**|Точность приблизительных числовых данных, точных числовых данных, целочисленных данных или денежных данных. В противном случае возвращается значение NULL.|  
|**NUMERIC_PRECISION_RADIX**|**smallint**|Основание системы счисления точности приблизительных числовых данных, точных числовых данных, целочисленных данных или денежных данных. В противном случае возвращается значение NULL.|  
|**NUMERIC_SCALE**|**tinyint**|Масштаб приблизительных числовых данных, точных числовых данных, целочисленных данных или денежных данных. В противном случае возвращается значение NULL.|  
|**DATETIME_PRECISION**|**smallint**|Точность в долях секунды, если параметр имеет тип **DateTime** или **smalldatetime**. В противном случае возвращается значение NULL.|  
|**INTERVAL_TYPE**|**nvarchar (** 30 **)**|NULL. Зарезервировано для последующего использования.|  
|**INTERVAL_PRECISION**|**smallint**|NULL. Зарезервировано для последующего использования.|  
|**USER_DEFINED_TYPE_CATALOG**|**nvarchar (** 128 **)**|NULL. Зарезервировано для последующего использования.|  
|**USER_DEFINED_TYPE_SCHEMA**|**nvarchar (** 128 **)**|NULL. Зарезервировано для последующего использования.|  
|**USER_DEFINED_TYPE_NAME**|**nvarchar (** 128 **)**|NULL. Зарезервировано для последующего использования.|  
|**SCOPE_CATALOG**|**nvarchar (** 128 **)**|NULL. Зарезервировано для последующего использования.|  
|**SCOPE_SCHEMA**|**nvarchar (** 128 **)**|NULL. Зарезервировано для последующего использования.|  
|**SCOPE_NAME**|**nvarchar (** 128 **)**|NULL. Зарезервировано для последующего использования.|  
  
## <a name="see-also"></a>См. также  
 [Системные представления &#40;&#41;Transact-SQL](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Представления информационной схемы &#40;&#41;Transact-SQL](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys. Columns &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys. Objects &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.parameters (Transact-SQL)](../../relational-databases/system-catalog-views/sys-parameters-transact-sql.md)  
  
  
