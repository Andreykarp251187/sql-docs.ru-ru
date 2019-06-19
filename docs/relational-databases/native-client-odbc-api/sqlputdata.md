---
title: SQLPutData | Документация Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLPutData function
ms.assetid: d39aaa5b-7fbc-4315-a7f2-5a7787e04f25
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c8c8755b100fcfbdb8c1ca9e067a79eb09bd37ba
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63014282"
---
# <a name="sqlputdata"></a>SQLPutData
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Применяются следующие ограничения при использовании функции SQLPutData для отправки более чем 65 535 байт данных (для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версии 4.21a) или 400 КБ данных (для SQL Server версии 6.0 и более поздние версии) для SQL_LONGVARCHAR (**текст**), SQL_WLONGVARCHAR (**ntext**) или SQL_LONGVARBINARY (**изображение**) столбец:  
  
-   Может быть упоминаемого параметра *insert_value* в инструкции INSERT.  
  
-   Может быть упоминаемого параметра *выражение* в предложении SET инструкции UPDATE.  
  
 Отмена последовательности вызовов SQLPutData, которые предоставляют данные в блоках на сервер под управлением [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] вызывает частичное обновление значения столбца при использовании версии 6.5 или более ранней версии. **Текст**, **ntext**, или **изображение** столбцу, который был указан при вызове SQLCancel задано на промежуточное значение заполнителя.  
  
> [!NOTE]  
>  Драйвер ODBC собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает соединение с версией [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.5 и более ранней.  
  
## <a name="diagnostics"></a>Диагностика  
 Имеется один [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственный клиент определенных SQLSTATE для SQLPutData:  
  
|SQLSTATE|Ошибка|Описание|  
|--------------|-----------|-----------------|  
|22026|Строковые данные, несовпадение длины|Если длина данных в байтах для отправляемых был указан приложением, например, параметром SQL_LEN_DATA_AT_EXEC (*n*) где *n* больше 0, общее число байтов, передаваемых приложением через SQLPutData должно соответствовать указанной длине.|  
  
## <a name="sqlputdata-and-table-valued-parameters"></a>Функция SQLPutData и параметры, возвращающие табличные значения  
 SQLPutData используется приложением, при использовании переменной привязки строки с помощью возвращающих табличные значения параметров. *StrLen_Or_Ind* параметр указывает, что она готова для драйвера для сбора данных для следующей строки или строк данных возвращающего табличное значение параметра, или что больше нет строк доступны:  
  
-   Значение, большее 0, указывает на доступность следующего набора значений строки.  
  
-   Значение 0 указывает, что строк для отправки больше нет.  
  
-   Значение меньше 0 является ошибочным и приводит к внесению в журнал диагностической записи со значением SQLState, равным HY090, и сообщением «Недопустимая длина строки или буфера».  
  
 *DataPtr* параметр учитывается, но должно быть присвоено значение отличное от NULL. Дополнительные сведения см. в разделе на привязка строк возвращающего табличное значение Параметра переменной в [привязки и Data Transfer of Table-Valued параметры и значения столбцов](../../relational-databases/native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md).  
  
 Если *StrLen_Or_Ind* имеет значение, отличное от SQL_DEFAULT_PARAM, или число между 0 и SQL_PARAMSET_SIZE (то есть *ColumnSize* функции SQLBindParameter), является ошибкой. В результате этой ошибки функция SQLPutData возвращает SQL_ERROR: SQLSTATE = HY090, «Недопустимая длина строки или буфера».  
  
 Дополнительные сведения о возвращающих табличные значения параметров, см. в разделе [возвращающего табличное значение параметров &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlputdata-support-for-enhanced-date-and-time-features"></a>Поддержка функции SQLPutData для улучшенных функций даты-времени  
 Значения параметров, типов даты времени преобразуются в том случае, как описано в разделе [преобразования из C в SQL](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md).  
  
 Дополнительные сведения см. в разделе [время улучшения функций даты и &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlputdata-support-for-large-clr-udts"></a>Поддержка функции SQLPutData для больших определяемых пользователем типов данных CLR  
 **SQLPutData** поддерживает большие определяемые пользователем типы CLR (UDT). Дополнительные сведения см. в разделе [Large CLR User-Defined типы &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [SQLPutData, функция](https://go.microsoft.com/fwlink/?LinkId=59365)   
 [Подробные сведения о реализации API-интерфейсов ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
