---
title: SQLGetInfo (драйвер для Access) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetInfo function [ODBC], Access Driver
- Access driver [ODBC], SQLGetInfo
ms.assetid: c226aba7-a2f4-4b32-b640-92654b40e5a7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8d71e3522ab46116e378b2ee17689a7048af04c6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68003314"
---
# <a name="sqlgetinfo-access-driver"></a>SQLGetInfo (драйвер для Access)
> [!NOTE]  
>  В этом разделе содержатся сведения, относящиеся к драйверу. Общие сведения об этой функции см. в соответствующем разделе [справочника по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLGetInfo** поддерживает тип сведений SQL_FILE_USAGE. Возвращаемое значение представляет собой 16-разрядное целое число, которое указывает, как драйвер непосредственно обрабатывает файлы в источнике данных:  
  
-   SQL_FILE_NOT_SUPPORTED — драйвер не является одноуровневый драйвером.  
  
-   SQL_FILE_TABLE — одноуровневый драйвер рассматривает файлы в источнике данных как таблицы.  
  
-   SQL_FILE_QUALIFIER — одноуровневый драйвер рассматривает файлы в источнике данных как квалификатор.  
  
 Драйвер ODBC возвращает SQL_FILE_QUALIFIER, так как каждый файл является полной базой данных.  
  
## <a name="sql_bookmark_persistence"></a>SQL_BOOKMARK_PERSISTENCE  
 SQL_BP_SCROLL &#124; SQL_BP_UPDATE [1]  
  
 [1] закладки сохраняются после фиксации, но не сохраняются после отката.  
  
## <a name="sql_convert_binary"></a>SQL_CONVERT_BINARY  
 SQL_CVT_DOUBLE &#124; SQL_CVT_FLOAT &#124; SQL_CVT_INTEGER &#124; SQL_CVT_NUMERIC &#124; SQL_CVT_REAL &#124; SQL_CVT_SMALLINT &#124; SQL_CVT_VARCHAR &#124; SQL_CVT_WVARCHAR  
  
## <a name="sql_convert_char"></a>SQL_CONVERT_CHAR  
 SQL_CVT_DOUBLE &#124; SQL_CVT_FLOAT &#124; SQL_CVT_INTEGER &#124; SQL_CVT_NUMERIC &#124; SQL_CVT_REAL &#124; SQL_CVT_SMALLINT &#124; SQL_CVT_VARCHAR &#124; SQL_CVT_WVARCHAR  
  
## <a name="sql_convert_date"></a>SQL_CONVERT_DATE  
 SQL_CVT_DOUBLE &#124; SQL_CVT_FLOAT &#124; SQL_CVT_INTEGER &#124; SQL_CVT_NUMERIC &#124; SQL_CVT_REAL &#124; SQL_CVT_SMALLINT &#124; SQL_CVT_VARCHAR &#124; SQL_CVT_WVARCHAR  
  
## <a name="sql_convert_double"></a>SQL_CONVERT_DOUBLE  
 SQL_CVT_DOUBLE &#124; SQL_CVT_FLOAT &#124; SQL_CVT_INTEGER &#124; SQL_CVT_NUMERIC &#124; SQL_CVT_REAL &#124; SQL_CVT_SMALLINT &#124; SQL_CVT_VARCHAR &#124; SQL_CVT_WVARCHAR  
  
## <a name="sql_convert_float"></a>SQL_CONVERT_FLOAT  
 SQL_CVT_DOUBLE &#124; SQL_CVT_FLOAT &#124; SQL_CVT_INTEGER &#124; SQL_CVT_NUMERIC &#124; SQL_CVT_REAL &#124; SQL_CVT_SMALLINT &#124; SQL_CVT_VARCHAR &#124; SQL_CVT_WVARCHAR  
  
## <a name="sql_convert_integer"></a>SQL_CONVERT_INTEGER  
 SQL_CVT_DOUBLE &#124; SQL_CVT_FLOAT &#124; SQL_CVT_INTEGER &#124; SQL_CVT_NUMERIC &#124; SQL_CVT_REAL &#124; SQL_CVT_SMALLINT &#124; SQL_CVT_VARCHAR &#124; SQL_CVT_WVARCHAR  
  
## <a name="sql_convert_longvarbinary"></a>SQL_CONVERT_LONGVARBINARY  
 SQL_CVT_DOUBLE &#124; SQL_CVT_FLOAT &#124; SQL_CVT_INTEGER &#124; SQL_CVT_NUMERIC &#124; SQL_CVT_REAL &#124; SQL_CVT_SMALLINT &#124; SQL_CVT_VARCHAR &#124; SQL_CVT_WVARCHAR  
  
## <a name="sql_convert_longvarchar"></a>SQL_CONVERT_LONGVARCHAR  
 SQL_CVT_DOUBLE &#124; SQL_CVT_FLOAT &#124; SQL_CVT_INTEGER &#124; SQL_CVT_NUMERIC &#124; SQL_CVT_REAL &#124; SQL_CVT_SMALLINT &#124; SQL_CVT_VARCHAR &#124; SQL_CVT_WVARCHAR  
  
## <a name="sql_convert_numeric"></a>SQL_CONVERT_NUMERIC  
 SQL_CVT_DOUBLE &#124; SQL_CVT_FLOAT &#124; SQL_CVT_INTEGER &#124; SQL_CVT_NUMERIC &#124; SQL_CVT_REAL &#124; SQL_CVT_SMALLINT &#124; SQL_CVT_VARCHAR &#124; SQL_CVT_WVARCHAR  
  
## <a name="sql_convert_real"></a>SQL_CONVERT_REAL  
 SQL_CVT_DOUBLE &#124; SQL_CVT_FLOAT &#124; SQL_CVT_INTEGER &#124; SQL_CVT_NUMERIC &#124; SQL_CVT_REAL &#124; SQL_CVT_SMALLINT &#124; SQL_CVT_VARCHAR &#124; SQL_CVT_WVARCHAR  
  
## <a name="sql_convert_smallint"></a>SQL_CONVERT_SMALLINT  
 SQL_CVT_DOUBLE &#124; SQL_CVT_FLOAT &#124; SQL_CVT_INTEGER &#124; SQL_CVT_NUMERIC &#124; SQL_CVT_REAL &#124; SQL_CVT_SMALLINT &#124; SQL_CVT_VARCHAR &#124; SQL_CVT_WVARCHAR  
  
## <a name="sql_convert_time"></a>SQL_CONVERT_TIME  
 SQL_CVT_DOUBLE &#124; SQL_CVT_FLOAT &#124; SQL_CVT_INTEGER &#124; SQL_CVT_NUMERIC &#124; SQL_CVT_REAL &#124; SQL_CVT_SMALLINT &#124; SQL_CVT_VARCHAR &#124; SQL_CVT_WVARCHAR  
  
## <a name="sql_convert_timestamp"></a>SQL_CONVERT_TIMESTAMP  
 SQL_CVT_DOUBLE &#124; SQL_CVT_FLOAT &#124; SQL_CVT_INTEGER &#124; SQL_CVT_NUMERIC &#124; SQL_CVT_REAL &#124; SQL_CVT_SMALLINT &#124; SQL_CVT_VARCHAR &#124; SQL_CVT_WVARCHAR  
  
## <a name="sql_convert_tinyint"></a>SQL_CONVERT_TINYINT  
 SQL_CVT_DOUBLE &#124; SQL_CVT_FLOAT &#124; SQL_CVT_INTEGER &#124; SQL_CVT_NUMERIC &#124; SQL_CVT_REAL &#124; SQL_CVT_SMALLINT &#124; SQL_CVT_VARCHAR &#124; SQL_CVT_WVARCHAR  
  
## <a name="sql_convert_varbinary"></a>SQL_CONVERT_VARBINARY  
 SQL_CVT_DOUBLE &#124; SQL_CVT_FLOAT &#124; SQL_CVT_INTEGER &#124; SQL_CVT_NUMERIC &#124; SQL_CVT_REAL &#124; SQL_CVT_SMALLINT &#124; SQL_CVT_VARCHAR &#124; SQL_CVT_WVARCHAR  
  
## <a name="sql_convert_varchar"></a>SQL_CONVERT_VARCHAR  
 SQL_CVT_DOUBLE &#124; SQL_CVT_FLOAT &#124; SQL_CVT_INTEGER &#124; SQL_CVT_NUMERIC &#124; SQL_CVT_REAL &#124; SQL_CVT_SMALLINT &#124; SQL_CVT_VARCHAR &#124; SQL_CVT_WVARCHAR  
  
## <a name="sql_union"></a>SQL_UNION  
 SQL_U_UNION_ALL &#124; SQL_U_UNION  
  
## <a name="sql_dbms_ver"></a>SQL_DBMS_VER  
  
|ISAM|Версия|Формат номеров версий|  
|----------|-------------|-------------------------------|  
|Microsoft Access|2.0|02.00.0000|  
||3.0|03.00.0000|  
||3.5|03.50.0000|  
||4.0|04.00.0000|  
  
> [!NOTE]  
>  Версии 1,0 и 1,1 не поддерживаются. Кроме того, в Microsoft Access версии 3,0, 7,0 и 97 нет различий в формате данных.  
  
## <a name="sql_ddl_index"></a>SQL_DDL_INDEX  
 SQL_DL_CREATE_INDEX  
  
 SQL_DL_DROP_INDEX  
  
## <a name="sql_getdata_extensions"></a>SQL_GETDATA_EXTENSIONS  
 SQL_GD_ANY_ORDER &#124; SQL_GD_ANY_COLUMN &#124; SQL_GD_BLOCK &#124; SQL_GD_BOUND  
  
## <a name="sql_keywords"></a>SQL_KEYWORDS  
 ЗНАКОВ  
  
 AUTOINCREMENT  
  
 BINARY  
  
 BOOLEAN  
  
 BYTE  
  
 ПОДПИСАН  
  
 CURRENCY  
  
 DATABASE  
  
 ИМЯ  
  
 DATETIME  
  
 ПОДОБНЫХ  
  
 дистинктров  
  
 даублефлоат  
  
 FLOAT4  
  
 FLOAT8  
  
 GENERAL  
  
 ииедаубле  
  
 ииесингле  
  
 IGNORE  
  
 IMAGE  
  
 INTEGER1  
  
 INTEGER2  
  
 INTEGER4  
  
 ЛОГИЧЕСКИЙ  
  
 LOGICAL1  
  
 LONG  
  
 лонгбинари  
  
 лонгчар  
  
 LONGTEXT  
  
 ПОЛУЧЕНА  
  
 MONEY  
  
 NOTE  
  
 NUMBER  
  
 OLECONTROL  
  
 овнеракцесс  
  
 PARAMETERS  
  
 PERCENT  
  
 PIVOT  
  
 ПРОМЕЖУТОК  
  
 ОДИН  
  
 синглефлоат  
  
 STDEV  
  
 STDEVP  
  
 STRING  
  
 TABLEID  
  
 TEXT  
  
 В начало  
  
 ПРЕОБРАЗУЕТ  
  
 унсигнедбите  
  
 VAR  
  
 VARBINARY  
  
 VARP  
  
 ДАНЕТ  
  
## <a name="sql_numeric_functions"></a>SQL_NUMERIC_FUNCTIONS  
 SQL_FN_NUM_ABS &#124; SQL_FN_NUM_ATAN &#124; SQL_FN_NUM_CEILING &#124; SQL_FN_NUM_COS &#124; SQL_FN_NUM_EXP &#124; SQL_FN_NUM_FLOOR &#124; SQL_FN_NUM_LOG &#124; SQL_FN_NUM_MOD &#124; SQL_FN_NUM_POWER &#124; SQL_FN_NUM_RAND &#124; SQL_FN_NUM_SIGN &#124; SQL_FN_NUM_SIN &#124; SQL_FN_NUM_SQRT &#124; SQL_FN_NUM_TAN  
  
## <a name="sql_oj_capabilities"></a>SQL_OJ_CAPABILITIES  
 SQL_OJ_LEFT SQL_OJ_RIGHT SQL_OJ_NOT_ORDERED SQL_OJ_INNER SQL_OJ_ALL_COMPARISON_OPS  
  
## <a name="sql_catalog_usage"></a>SQL_CATALOG_USAGE  
 SQL_QU_DML_STATEMENTS &#124; SQL_QU_TABLE_DEFINITION &#124; SQL_QU_INDEX_DEFINITION &#124; SQL_QU_PROCEDURE_INVOCATION  
  
## <a name="sql_scroll_options"></a>SQL_SCROLL_OPTIONS  
 SQL_SO_FORWARD_ONLY &#124; SQL_SO_STATIC &#124; SQL_SO_KEYSET_DRIVEN  
  
## <a name="sql_string_functions"></a>SQL_STRING_FUNCTIONS  
 SQL_FN_STR_ASCII &#124; SQL_FN_STR_CHAR &#124; SQL_FN_STR_CONCAT &#124; SQL_FN_STR_LCASE &#124; SQL_FN_STR_LEFT &#124; SQL_FN_STR_LENGTH &#124; SQL_FN_STR_LOCATE &#124; SQL_FN_STR_LOCATE_2 SQL_FN_STR_LTRIM &#124; SQL_FN_STR_RIGHT &#124; SQL_FN_STR_RTRIM &#124; SQL_FN_STR_SPACE &#124; SQL_FN_STR_SUBSTRING &#124; SQL_FN_STR_UCASE  
  
## <a name="sql_subqueries"></a>SQL_SUBQUERIES  
 SQL_SQ_COMPARISON &#124; SQL_SQ_EXISTS &#124; SQL_SQ_IN &#124; SQL_SQ_QUANTIFIED &#124; SQL_SQ_CORRELATED_SUBQUERIES  
  
## <a name="sql_timedate_functions"></a>SQL_TIMEDATE_FUNCTIONS  
 SQL_FN_TD_CURDATE &#124; SQL_FN_TD_CURTIME &#124; SQL_FN_TD_DAYOFMONTH &#124; SQL_FN_TD_DAYOFWEEK &#124; SQL_FN_TD_DAYOFYEAR &#124; SQL_FN_TD_HOUR &#124; SQL_FN_TD_MINUTE &#124; SQL_FN_TD_MONTH &#124; SQL_FN_TD_NOW &#124; SQL_FN_TD_SECOND &#124; SQL_FN_TD_WEEK &#124; SQL_FN_TD_YEAR
