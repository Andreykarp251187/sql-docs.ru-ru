---
title: bcp_control | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_control
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_control function
ms.assetid: 32187282-1385-4c52-9134-09f061eb44f5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 323ea04d32501f04156ffa81452fad5e5cf86664
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62689509"
---
# <a name="bcpcontrol"></a>bcp_control
  Изменяет значения по умолчанию различных параметров управления для массового копирования между файлом и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
RETCODE bcp_control (  
HDBC   
hdbc  
,  
INT   
eOption  
,  
void*   
iValue  
);  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *HDBC*  
 Дескриптор соединения ODBC с поддержкой массового копирования.  
  
 *eOption*  
 Принимает одно из следующих значений.  
  
 BCPABORT  
 Останавливает текущую операцию массового копирования. Вызовите **bcp_control** с *eOption* значения BCPABORT из другого потока, чтобы остановить выполняющуюся операцию массового копирования. *IValue* параметр учитывается.  
  
 BCPBATCH  
 Число строк в пакете. Значение по умолчанию — 0, что указывает либо все строки в таблице при извлечении данных, либо все строки в пользовательском файле данных, когда данные копируются в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если задать для этого параметра значение меньше 1, то значению BCPBATCH будет установлено значение по умолчанию.  
  
 BCPDELAYREADFMT  
 Логическое значение. Если задано значение true, приведет к [bcp_readfmt](bcp-readfmt.md) для чтения во время выполнения. Если false (по умолчанию), bcp_readfmt будет сразу же считать файл форматирования. Если BCPDELAYREADFMT имеет значение true и вызывается bcp_columns или bcp_setcolfmt, возникнет ошибка последовательности.  
  
 Ошибка последовательности также возникнет при вызове метода `bcp_control(hdbc,` BCPDELAYREADFMT`, (void *)FALSE)` после вызова метода `bcp_control(hdbc,` BCPDELAYREADFMT`, (void *)TRUE)` и bcp_writefmt.  
  
 Дополнительные сведения см. в разделе [Обнаружение метаданных](../native-client/features/metadata-discovery.md).  
  
 BCPFILECP  
 *iValue* содержит номер кодовой страницы для файла данных. Можно указать номер кодовой страницы, например 1252 или 850, либо одно из следующих значений.  
  
 BCPFILE_ACP: данные в файле, находятся в Microsoft Windows?? кодовая страница клиента.  
  
 BCPFILE_OEMCP: данные в файле хранятся в кодовой странице изготовителя оборудования (OEM) клиента (по умолчанию).  
  
 BCPFILE_RAW: данные в файле хранятся в кодовой странице [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 BCPFILEFMT  
 Номер версии для формата файла данных. Может иметь значение 80 ([!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]), 90 ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]), 100 ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] или [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]), 110 ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) или 120 ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]). 120 используется по умолчанию. Это может оказаться полезным при экспорте или импорте данных в форматах, которые поддерживались прежними версиями сервера. Например, для импорта данных, который был получен из текстового столбца в [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] сервера в **varchar(max)** столбца в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] или более поздней версии, следует указать значение 80. Аналогично при указании значения 80 при экспорте данных из **varchar(max)** столбец, он будет сохранен так же, как сохраняются текстовые столбцы в [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] форматирования и можно импортировать в текстовый столбец [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] сервера.  
  
 BCPFIRST  
 Первая строка данных, копируемых в файл или таблицу. Значение по умолчанию равно 1. Если задать для этого параметра значение меньше 1, то будет установлено значение по умолчанию.  
  
 BCPFIRSTEX  
 В операциях bcp out задает первую строку таблицы базы данных для копирования в файл данных.  
  
 В операциях bcp in задает первую строку файла данных для копирования в таблицу базы данных.  
  
 *IValue* параметр должен быть адрес 64-разрядное целое число со знаком, величину. Максимальное значение, передаваемое в BCPFIRSTEX, составляет 2^63-1.  
  
 BCPFMTXML  
 Указывает, что формируемый файл форматирования должен быть в формате XML. По умолчанию эта настройка отключена.  
  
 XML-файлы форматирования обеспечивают большую гибкость, но имеют некоторые ограничения. Например, нельзя одновременно указать префикс и признак конца для поля, что было возможно в более старых файлах форматирования.  
  
> [!NOTE]  
>  XML-файлы форматирования поддерживаются только при установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] вместе с собственным клиентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 BCPHINTS  
 *iValue* содержит символьной строки sqltchar. Адресуемая строка задает указания для обработки массового копирования [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или инструкцию Transact-SQL, которая возвращает результирующий набор. Если задана инструкция Transact-SQL, которая возвращает несколько результирующих наборов, все результирующие наборы после первого пропускаются. Дополнительные сведения об указаниях обработки массового копирования, см. в разделе [служебная программа bcp](../../tools/bcp-utility.md).  
  
 BCPKEEPIDENTITY  
 Когда *iValue* имеет значение TRUE, указывает, что функции массового копирования вставляют значения данных, предоставленные для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] столбцов, определенных с ограничением identity. Входной файл должен содержать значения для столбцов идентификаторов. Если эти значения не заданы, то для вставляемых строк создаются новые значения идентификаторов. Данные в файле, предназначенные для столбцов идентификаторов, не учитываются.  
  
 BCPKEEPNULLS  
 Указывает, будут ли пустые значения данных в файле преобразовываться в значения NULL в таблице [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Когда *iValue* имеет значение TRUE, пустые значения будут преобразовываться в значение NULL в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы. По умолчанию пустые значения преобразовываются в значения по умолчанию для столбца в таблице [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , если значение по умолчанию существует.  
  
 BCPLAST  
 Последняя строка для копирования. По умолчанию установлено копирование всех строк; если задать для этого параметра значение меньше 1, то ему будет установлено значение по умолчанию.  
  
 BCPLASTEX  
 В операциях bcp out задает последнюю строку таблицы базы данных для копирования в файл данных.  
  
 В операциях bcp in задает последнюю строку файла данных для копирования в таблицу базы данных.  
  
 *IValue* параметр должен быть адрес 64-разрядное целое число со знаком, величину. Максимальное значение, передаваемое в BCPLASTEX, составляет 2^63-1.  
  
 BCPMAXERRS  
 Число ошибок, после которого произойдет сбой операции массового копирования. Значение по умолчанию — 10. Этот параметр сбрасывается в значение меньше 1 к значению по умолчанию. В операции массового копирования допускается не более 65 535 ошибок. Если выполнить попытку установить этот параметр в значение, превышающее 65 535, будет установлено значение 65 535.  
  
 BCPODBC  
 Если значение равно TRUE, указывает, что **datetime** и **smalldatetime** будет использовать значения, сохраняемые в символьном формате, управляющие последовательности ODBC timestamp префикс и суффикс. Параметр BCPODBC применяется только к BCP_OUT.  
  
 Если задано значение FALSE, **datetime** значение, представляющее 1 января 1997 преобразуется в символьную строку: 1997-01-01 00:00:00.000. При значении TRUE же **datetime** интерпретируется так: {ts "00:00:00.000 1997-01-01"}.  
  
 BCPROWCOUNT  
 Возвращает число строк, на которые распространяется действие текущей (или последней) операции bcp.  
  
 BCPTEXTFILE  
 Значение TRUE указывает, что файл данных является текстовым, а не двоичным файлом. Если файл является текстовым, BCP определяет, является ли его кодировка кодировкой Юникод, путем проверки байтового маркера Юникода в первых двух байтах файла данных.  
  
 BCPUNICODEFILE  
 В значении TRUE указывает, что входной файл является файлом в кодировке Юникод.  
  
 *iValue*  
 Значение для указанного *eOption*. *iValue* (longlong приведенным к ПУСТОМУ) целое число приводится к указателю void, чтобы обеспечить для расширения до 64-разрядных значений в будущем.  
  
## <a name="returns"></a>Возвращает  
 SUCCEED или FAIL.  
  
## <a name="remarks"></a>Примечания  
 Эта функция задает различные параметры управления для операций массового копирования, включая число ошибок, после которого массовое копирование будет отменено, номера первой и последней строк для копирования из файла данных, а также размер пакета.  
  
 Эта функция также используется для указания инструкции SELECT при массовом копировании результирующего набора инструкции SELECT из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Задайте *eOption* значение BCPHINTS, а также набор *iValue* указатель на строку SQLTCHAR, содержащую инструкцию SELECT.  
  
 Эти параметры управления имеют значение только при копировании между пользовательским файлом и таблицей [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Параметры управления никак не влияет на строки, скопированные [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с [bcp_sendrow](bcp-sendrow.md).  
  
## <a name="example"></a>Пример  
  
```  
// Variables like henv not specified.  
SQLHDBC      hdbc;  
DBINT      nRowsProcessed;  
  
// Application initiation, get an ODBC environment handle, allocate the  
// hdbc, and so on.  
...   
  
// Enable bulk copy prior to connecting on allocated hdbc.  
SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP, (SQLPOINTER) SQL_BCP_ON,  
   SQL_IS_INTEGER);  
  
// Connect to the data source, return on error.  
if (!SQL_SUCCEEDED(SQLConnect(hdbc, _T("myDSN"), SQL_NTS,  
   _T("myUser"), SQL_NTS, _T("myPwd"), SQL_NTS)))  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Initialize bulk copy.   
if (bcp_init(hdbc, _T("address"), _T("address.add"), _T("addr.err"),  
   DB_IN) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Set the number of rows per batch.   
if (bcp_control(hdbc, BCPBATCH, (void*) 1000) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Set file column count.   
if (bcp_columns(hdbc, 1) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Set the file format.   
if (bcp_colfmt(hdbc, 1, 0, 0, SQL_VARLEN_DATA, '\n', 1, 1)  
   == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Execute the bulk copy.   
if (bcp_exec(hdbc, &nRowsProcessed) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
printf_s("%ld rows processed by bulk copy.", nRowsProcessed);  
  
```  
  
## <a name="see-also"></a>См. также  
 [Функции массового копирования](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
