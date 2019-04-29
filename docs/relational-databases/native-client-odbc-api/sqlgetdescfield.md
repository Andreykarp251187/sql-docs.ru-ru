---
title: SQLGetDescField | Документация Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLGetDescField function
ms.assetid: 3e59a37a-28ee-4c91-8968-7fe3b966739d
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 410aec64f1a10f8deaf7923fedda8b79c114eef3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63014493"
---
# <a name="sqlgetdescfield"></a>SQLGetDescField
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента предоставляет поля дескриптора для дескрипторе строки реализации (IRD) только. В IRD [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ссылки на поля дескриптора атрибуты столбца специфические для драйвера. Дополнительные сведения о полном списке поля дескриптора доступны специфические для драйвера, см. в разделе [SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md).  
  
 Поля дескриптора, содержащие строки идентификатора столбца, часто являются строками нулевой длины. Все специфические для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] значения поля дескриптора доступны только для чтения.  
  
 Как и атрибуты, полученные с помощью SQLColAttribute, поля дескриптора, что атрибуты на уровне строк отчета (такие как SQL_CA_SS_COMPUTE_ID) сообщаются для всех столбцов в результирующем наборе.  
  
## <a name="sqlgetdescfield-and-table-valued-parameters"></a>Функция SQLGetDescField и возвращающие табличные значения параметры  
 SQLGetDescField можно использовать для получения значений для расширенных атрибутов возвращающих табличные значения параметров и столбцов возвращающих табличные значения параметра. Дополнительные сведения о возвращающих табличные значения параметров, см. в разделе [возвращающего табличное значение параметров &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlgetdescfield-support-for-enhanced-date-and-time-features"></a>Поддержка функции SQLGetDescField для усовершенствованных функций даты-времени  
 Сведения о полях дескриптора, доступных с типами новые даты и времени, см. в разделе [метаданные параметров и результатов](../../relational-databases/native-client-odbc-date-time/metadata-parameter-and-result.md).  
  
 Дополнительные сведения см. в разделе [время улучшения функций даты и &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
 Начиная с версии [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], может возвращать SQLGetDescField **SQL_C_SS_TIME2** (для **время** типов) или **SQL_C_SS_TIMESTAMPOFFSET** (для  **DateTimeOffset**) вместо **SQL_C_BINARY**, если приложение использует ODBC 3.8.  
  
## <a name="sqlgetdescfield-support-for-large-clr-udts"></a>Поддержка функции SQLGetDescField для больших определяемых пользователем типов данных CLR  
 **SQLGetDescField** поддерживает большие определяемые пользователем типы CLR (UDT). Дополнительные сведения см. в разделе [Large CLR User-Defined типы &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="sqlgetdescfield-support-for-sparse-columns"></a>Поддержка функции SQLGetDescField Support для разреженных столбцов  
 SQLGetDescField может использоваться для запроса новому IRD-полю SQL_CA_SS_IS_COLUMN_SET, чтобы определить, является ли столбец **column_set** столбца.  
  
 Дополнительные сведения см. в разделе [Поддержка разреженных столбцов &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sparse-columns-support-odbc.md).  
  
## <a name="example"></a>Пример  
  
```  
typedef struct tagCOMPUTEBYLIST  
    {  
    SQLSMALLINT nBys;  
    SQLSMALLINT aByList[1];  
    } COMPUTEBYLIST;  
typedef COMPUTEBYLIST* PCOMPUTEBYLIST;   
  
SQLHDESC    hIRD;   
SQLINTEGER  cbIRD;   
SQLINTEGER  nSet = 0;   
  
// . . .  
// Execute a statement that contains a COMPUTE clause,  
//  then get the descriptor handle of the IRD and  
//  get some IRD values.  
  
SQLGetStmtAttr(g_hStmt, SQL_ATTR_IMP_ROW_DESC,  
    (SQLPOINTER) &hIRD, sizeof(SQLHDESC), &cbIRD);  
  
// For statement-wide column attributes, any  
//  descriptor record will do. You know that 1 exists,  
//  so use it.  
SQLGetDescField(hIRD, 1, SQL_CA_SS_NUM_COMPUTES,  
    (SQLPOINTER) &nComputes, SQL_IS_INTEGER, &cbIRD);  
  
if (nSet == 0)  
    {  
    SQLINTEGER      nOrderID;  
  
    printf_s("Normal result set.\n");  
  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        SQLGetDescField(hIRD, nCol+1,  
            SQL_CA_SS_COLUMN_ORDER,  
            (SQLPOINTER) &nOrderID, SQL_IS_INTEGER,  
            &cbIRD);  
  
        if (nOrderID != 0)  
            {  
            printf_s("Col in ORDER BY, pos: %ld",  
                nOrderID);  
            }  
            printf_s("\n");  
        }  
  
    printf_s("\n");  
    }  
else  
    {  
    PCOMPUTEBYLIST  pByList;  
    SQLSMALLINT     nBy;  
    SQLINTEGER      nColID;  
  
    printf_s("Computed result set number: %lu\n",  
        nSet);  
  
    SQLGetDescField(hIRD, 1, SQL_CA_SS_COMPUTE_BYLIST,  
        (SQLPOINTER) &pByList, SQL_IS_INTEGER,  
        &cbIRD);  
  
    if (pByList != NULL)  
        {  
        printf_s("Clause ordered by columns: ");  
        for (nBy = 0; nBy < pByList->nBys; )  
            {  
            printf_s("%u", pByList->aByList[nBy]);  
            nBy++;  
  
            if (nBy == pByList->nBys)  
                {  
                printf_s("\n");  
                }  
            else  
                {  
                printf_s(", ");  
                }  
            }  
        }  
    else  
        {  
        printf_s("Compute clause set not ordered.\n");  
        }  
  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        SQLGetDescField(hIRD, nCol+1,  
            SQL_CA_SS_COLUMN_ID, (SQLPOINTER) &nColID,  
            SQL_IS_INTEGER, &cbIRD);  
        printf_s("ColumnID: %lu, nColID);  
        }  
    printf_s("\n");  
    }  
  
if (SQLMoreResults(g_hStmt) == SQL_SUCCESS)  
    {  
    // Determine the result set indicator.  
    SQLGetDescField(hIRD, 1, SQL_CA_SS_COMPUTE_ID,  
        (SQLPOINTER) &nSet, SQL_IS_INTEGER, &cbIRD);  
    }  
```  
  
## <a name="see-also"></a>См. также  
 [Функция SQLGetDescField](https://go.microsoft.com/fwlink/?LinkId=59351)   
 [Подробные сведения о реализации API-интерфейсов ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
