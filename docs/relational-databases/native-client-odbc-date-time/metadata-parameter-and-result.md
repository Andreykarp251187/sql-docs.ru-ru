---
title: Метаданные параметра и результата Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- metadata [ODBC]
ms.assetid: 1518e6e5-a6a8-4489-b779-064c5624df53
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8ba66c950f25663dabc3c0c46f83a7589df300ca
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304095"
---
# <a name="metadata---parameter-and-result"></a>Метаданные — параметры и результаты
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  В этом разделе приведено описание того, какие данные возвращаются в полях дескриптора параметра реализации (IPD) и дескриптора строки реализации (IRD) для типов данных даты и времени.  
  
## <a name="information-returned-in-ipd-fields"></a>Информация, возвращаемая в полях IPD  
 В полях IPD происходит возврат следующей информации:  
  
|Тип параметра|Дата|time|smalldatetime|DATETIME|datetime2|datetimeoffset|  
|--------------------|----------|----------|-------------------|--------------|---------------|--------------------|  
|SQL_DESC_CASE_SENSITIVE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_CONCISE_TYPE|SQL_TYPE_DATE|SQL_SS_TIME2|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_SS_TIMESTAMPOFFSET|  
|SQL_DESC_DATETIME_INTERVAL_CODE|SQL_CODE_DATE|0|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|0|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|10|8,10..16|16|23|19, 21..27|26, 28..34|  
|SQL_DESC_FIXED_PREC_SCALE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_LENGTH|10|8,10..16|16|23|19, 21..27|26, 28..34|  
|SQL_DESC_OCTET_LENGTH|6|12|4|8|16|20|  
|SQL_DESC_PRECISION|0|0..7|0|3|0..7|0..7|  
|SQL_DESC_SCALE|0|0..7|0|3|0..7|0..7|  
|SQL_DESC_TYPE|SQL_TYPE_DATE|SQL_SS_TYPE_TIME2|SQL_DATETIME|SQL_DATETIME|SQL_DATETIME|SQL_SS_TIMESTAMPOFFSET|  
|SQL_DESC_TYPE_NAME|**Дата**|**time**|**smalldatetime** в IRD, **datetime2** в IPD|**время наступления дат** в IRD, **datetime2** в IPD|**datetime2**|datetimeoffset|  
|SQL_CA_SS_VARIANT_TYPE|SQL_C_TYPE_DATE|SQL_C_TYPE_BINARY|SQL_C_TYPE_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|SQL_C_TYPE_BINARY|  
|SQL_CA_SS_VARIANT_SQL_TYPE|SQL_TYPE_DATE|SQL_SS_TIME2|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_SS_TIMESTAMPOFFSET|  
|SQL_CA_SS_SERVER_TYPE|Н/Д|Н/Д|SQL_SS_TYPE_SMALLDATETIME|SQL_SS_TYPE_DATETIME|SQL_SS_TYPE_DEFAULT|Н/Д|  
  
 Иногда возникают нарушения непрерывности значений диапазона. Например, в диапазоне 8,10...16 отсутствует 9. Это следствие добавления десятичной запятой, когда точность в долях секунды выше нуля.  
  
 **datetime2** возвращается в качестве имени типа для **небольшого времени и** **времени даты,** поскольку драйвер использует это как общий тип для передачи всех **SQL_TYPE_TIMESTAMP** значений на сервер.  
  
 SQL_CA_SS_VARIANT_SQL_TYPE — это новое поле дескриптора. Это поле было добавлено в IRD и IPD, чтобы приложения могли указывать тип значения, связанный с столбиками и параметрами **sqlvariant** (SQL_SSVARIANT)  
  
 SQL_CA_SS_SERVER_TYPE — это новое поле (только для IPD), позволяющее в приложениях управлять способом привязки в качестве SQL_TYPE_TYPETIMESTAMP (или в качестве SQL_SS_VARIANT с типом SQL_C_TYPE_TIMESTAMP языка C) параметров, передаваемых на сервер. Если SQL_DESC_CONCISE_TYPE SQL_TYPE_TIMESTAMP (или является SQL_SS_VARIANT, а тип C является SQL_C_TYPE_TIMESTAMP), когда называется S'L'LExecute или S'LExecDirect, значение SQL_CA_SS_SERVER_TYPE определяет табулярный поток данных (TDS) тип значения параметра, а именно:  
  
|Значение SQL_CA_SS_SERVER_TYPE|Допустимые значения для SQL_DESC_PRECISION|Допустимые значения для SQL_DESC_LENGTH|Тип потока табличных данных|  
|----------------------------------------|-------------------------------------------|----------------------------------------|--------------|  
|SQL_SS_TYPE_DEFAULT|0..7|19, 21..27|**datetime2**|  
|SQL_SS_TYPE_SMALLDATETIME|0|19|**smalldatetime**|  
|SQL_SS_TYPE_DATETIME|3|23|**datetime**|  
  
 Значение по умолчанию SQL_CA_SS_SERVER_TYPE равно SQL_SS_TYPE_DEFAULT. Настройки SQL_DESC_PRECISION и SQL_DESC_LENGTH проверяются с учетом значения SQL_CA_SS_SERVER_TYPE, как описано в приведенной выше таблице. Если эта проверка завершается неудачно, то происходит возврат значения SQL_ERROR и в журнал вносится диагностическая запись с кодом SQLSTATE (равным 07006) и сообщением «Нарушение атрибута ограниченного типа данных». Возврат этой ошибки происходит также, если параметру SQL_CA_SS_SERVER_TYPE присвоено значение, отличное от SQL_SS_TYPE DEFAULT, а параметр DESC_CONCISE_TYPE не равен SQL_TYPE_TIMESTAMP. Эти проверки осуществляются при проведении проверки согласованности дескриптора, например, в следующих случаях.  
  
-   Если изменяется значение SQL_DESC_DATA_PTR.  
  
-   Во время подготовки или выполнения (при вызове функций SQLExecute, SQLExecDirect, SQLSetPos или SQLBulkOperations).  
  
-   Когда приложение заставляет неотложенную подготовку, позвонив в S'LPrepare с отсроченной подготовкой с отключенной, или позвонив в S'LNumResultCols, S'LDescribeCol или S'LDescribeParam для заявления, которое подготовлено, но не выполнено.  
  
 Когда SQL_CA_SS_SERVER_TYPE устанавливается вызовом в S'LSetDescField, его значение должно быть SQL_SS_TYPE_DEFAULT, SQL_SS_TYPE_SMALLDATETIME или SQL_SS_TYPE_DATETIME. В противном случае происходит возврат значения SQL_ERROR, и в журнал вносится диагностическая запись с кодом SQLState (равным HY092) и сообщением «Неверный атрибут или идентификатор параметра».  
  
 Атрибут SQL_CA_SS_SERVER_TYPE может использоваться приложениями, которые зависят от функциональности, поддерживаемой **временем даты** и **небольшим временем дат,** но не **datetime2.** Например, **datetime2** требует использования функций **dateadd** и **dateiif,** в то время как **дата** и **малое время датаа** также позволяют арифметические операторы. В большинстве приложений необходимость в этом атрибуте отсутствует, поэтому следует избегать его применения.  
  
## <a name="information-returned-in-ird-fields"></a>Информация, возвращаемая в полях IRD  
 В полях IRD возвращаются следующие сведения:  
  
|Тип столбца|Дата|time|smalldatetime|DATETIME|datetime2|datetimeoffset|  
|-----------------|----------|----------|-------------------|--------------|---------------|--------------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_CASE_SENSITIVE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_CONCISE_TYPE|SQL_TYPE_DATE|SQL_SS_TIME2|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_SS_TIMESTAMPOFFSET|  
|SQL_DESC_DATETIME_INTERVAL_CODE|SQL_CODE_DATE|0|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|0|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|10|8,10..16|16|23|19, 21..27|26, 28..34|  
|SQL_DESC_DISPLAY_SIZE|10|8,10..16|16|23|19, 21..27|26, 28..34|  
|SQL_DESC_FIXED_PREC_SCALE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_LENGTH|10|8,10..16|16|2|19, 21..27|26, 28..34|  
|SQL_DESC_LITERAL_PREFIX|'|'|'|'|'|'|  
|SQL_DESC_LITERAL_SUFFIX|'|'|'|'|'|'|  
|SQL_DESC_LOCAL_TYPE_NAME|**Дата**|**time**|**smalldatetime**|**datetime**|**datetime2**|datetimeoffset|  
|SQL_DESC_OCTET_LENGTH|6|12|4|8|16|20|  
|SQL_DESC_PRECISION|0|0..7|0|3|0..7|0..7|  
|SQL_DESC_SCALE|0|0..7|0|3|0..7|0..7|  
|SQL_DESC_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|  
|SQL_DESC_TYPE|SQL_DATETIME|SQL_SS_TIME2|SQL_DATETIME|SQL_DATETIME|SQL_DATETIME|SQL_SS_TIMESTAMPOFFSET|  
|SQL_DESC_TYPE_NAME|**Дата**|**time**|**smalldatetime**|**datetime**|**datetime2**|datetimeoffset|  
|SQL_DESC_UNSIGNED|SQL_TRUE|SQL_TRUE|SQL_TRUE|SQL_TRUE|SQL_TRUE|SQL_TRUE|  
  
## <a name="see-also"></a>См. также:  
 [Метаданные &#40;&#41;ODBC](https://msdn.microsoft.com/library/99133efc-b1f2-46e9-8203-d90c324a8e4c)  
  
  
