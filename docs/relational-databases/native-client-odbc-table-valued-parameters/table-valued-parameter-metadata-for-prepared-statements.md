---
title: Метаданные возвращающего табличное значение параметра для подготовленных инструкций | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), metadata for prepared statements
ms.assetid: fd2fc705-2e98-4011-9822-c7e6cca4a535
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a5f7889d7fde9bb3c6f8ecf2d92f9aaa6b2b2842
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68129021"
---
# <a name="table-valued-parameter-metadata-for-prepared-statements"></a>Метаданные возвращающего табличное значение параметра для подготовленных инструкций
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Приложение может получить метаданные для заготовленного вызова процедуры через SQLNumParams и SQLDescribeParam. Для возвращающих табличные значения параметров *DataTypePtr* устанавливается в значение SQL_SS_TABLE. Дополнительные метаданные доступна через SQLGetDescField для SQL_CA_SS_TYPE_NAME, sql_ca_ss_type_catalog_name и sql_ca_ss_type_schema_name.  
  
 SQL_CA_SS_TYPE_NAME, sql_ca_ss_type_catalog_name и sql_ca_ss_type_schema_name могут использоваться с SQLColumns для получения метаданных столбца для табличных типов, связанных с возвращающих табличное значение параметрами. В этом случае SQL_SOPT_SS_NAME_SCOPE необходимо установить в значение SQL_SS_NAME_SCOPE_TABLE_TYPE перед вызовом SQLColumns. После получения метаданных столбца, соответствующего возвращающему табличное значение параметру, параметр SQL_SOPT_SS_NAME_SCOPE необходимо установить обратно в значение по умолчанию — SQL_SS_NAME_SCOPE_TABLE.  
  
 Параметры SQL_CA_SS_TYPE_NAME, SQL_CA_SS_TYPE_CATALOG_NAME и SQL_CA_SS_TYPE_SCHEMA_NAME также могут использоваться с параметрами определяемых пользователем типов данных CLR.  
  
 Для подготовленных инструкций, не являющихся вызовами хранимых процедур, нельзя получить метаданные возвращающего табличные значения параметра. При попытке выполнения данного действия приложение возвращает ошибку SQL_ERROR с кодом SQLSTATE 42000 и сообщение «Синтаксическая ошибка или нарушение доступа».  
  
## <a name="see-also"></a>См. также  
 [Возвращающие табличные значения параметров &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
