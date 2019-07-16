---
title: Функция SQLColAttribute | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLColAttribute
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLColAttribute
helpviewer_keywords:
- SQLColAttribute function [ODBC]
ms.assetid: 8c45c598-cb01-4789-a571-e93619a18ed9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c4577b97c827d527422fe2448656496d7c196c40
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68118703"
---
# <a name="sqlcolattribute-function"></a>Функция SQLColAttribute
**Соответствие стандартам**  
 Представленные версии: ODBC 3.0 стандартов соответствия: ISO-92  
  
 **Сводка**  
 **SQLColAttribute** возвращает данные дескриптора для столбца в результирующем наборе. Сведения о дескрипторе возвращается как символьная строка, значение дескриптора зависящего или целочисленное значение.  
  
> [!NOTE]  
>  Дополнительные сведения о какие диспетчера драйверов сопоставляет эту функцию, чтобы при ODBC 3. *x* при работе с ODBC 2. *x* драйвера, см. в разделе [сопоставление замещающих функций для обеспечения обратной совместимости приложений](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
SQLRETURN SQLColAttribute (  
      SQLHSTMT        StatementHandle,  
      SQLUSMALLINT    ColumnNumber,  
      SQLUSMALLINT    FieldIdentifier,  
      SQLPOINTER      CharacterAttributePtr,  
      SQLSMALLINT     BufferLength,  
      SQLSMALLINT *   StringLengthPtr,  
      SQLLEN *        NumericAttributePtr);  
```  
  
## <a name="arguments"></a>Аргументы  
 *StatementHandle*  
 [Вход] Дескриптор инструкции.  
  
 *ColumnNumber*  
 [Вход] Номер записи в IRD, из которого будет извлекаться значение поля. Этот аргумент соответствует номер столбца, данные результата, упорядоченные последовательно в порядке возрастания столбца, начиная с 1. Столбцы могут быть описаны в любом порядке.  
  
 В этом аргументе можно указать столбец 0, но все значения, кроме SQL_DESC_TYPE и SQL_DESC_OCTET_LENGTH будет возвращать неопределенные значения.  
  
 *FieldIdentifier*  
 [Вход] Дескриптор. Этот дескриптор определяет, какое поле в IRD должны запрашиваться (например, SQL_COLUMN_TABLE_NAME).  
  
 *CharacterAttributePtr*  
 [Выход] Указатель на буфер, в которую будет возвращено значение в *FieldIdentifier* поле *ColumnNumber* строки ird, если поле является символьной строкой. В противном случае поле не используется.  
  
 Если *CharacterAttributePtr* имеет значение NULL, *StringLengthPtr* по-прежнему возвращает общее число байтов (за исключением символа конечное значение null для символьных данных) для возврата в буфере Указывает *CharacterAttributePtr*.  
  
 *BufferLength*  
 [Вход] Если *FieldIdentifier* представляет собой поле, определенных для ODBC и *CharacterAttributePtr* указывает на строку символов или бинарный буфер, данный аргумент должен иметь длину \*  *CharacterAttributePtr*. Если *FieldIdentifier* представляет собой поле, определенных для ODBC и \* *CharacterAttribute*Ptr должно быть целым числом, то это поле пропускается. Если  *\*CharacterAttributePtr* строка в Юникоде (при вызове **SQLColAttributeW**), *BufferLength* аргумент должен быть четным числом. Если *FieldIdentifier* является полем, определяемым драйвером, приложение указывает характер поле для диспетчера драйверов, задав *BufferLength* аргумент. *BufferLength* может иметь следующие значения:  
  
-   Если *CharacterAttributePtr* — это указатель на указатель, *BufferLength* должно иметь значение SQL_IS_POINTER.  
  
-   Если *CharacterAttributePtr* — это указатель на строку символов *BufferLength* длина буфера.  
  
-   Если *CharacterAttributePtr* является результатом SQL_LEN_BINARY_ATTR указатель бинарный буфер местах приложения (*длина*) в макрос *BufferLength*. Это размещает отрицательное значение в *BufferLength*.  
  
-   Если *CharacterAttributePtr* является указателем на тип данных фиксированной длины, *BufferLength* должно быть одно из следующих: SQL_IS_INTEGER, SQL_IS_UNINTEGER, SQL_SMALLINT или SQLUSMALLINT.  
  
 *StringLengthPtr*  
 [Выход] Указатель на буфер, в которую будет возвращено общее число байтов (за исключением байтов конечное значение null для символьных данных) для возврата в **CharacterAttributePtr*.  
  
 Для символьных данных, если количество байтов, доступных для возврата больше или равно *BufferLength*, данные дескриптора в \* *CharacterAttributePtr* усекается до  *BufferLength* минус длина знак завершения null и заканчивается нулевым байтом драйвером.  
  
 Для всех других типов данных, значение *BufferLength* игнорируется и драйвер предполагает, что размер **CharacterAttributePtr* 32 бита.  
  
 *NumericAttributePtr*  
 [Выход] Указатель на буфер целое число, в которую будет возвращено значение в *FieldIdentifier* поле *ColumnNumber* строки ird, если поле является числовой дескриптор типа, например SQL_DESC_COLUMN_LENGTH. В противном случае поле не используется. Обратите внимание на то, что некоторые драйверы могут вести запись только в нижнем 32-разрядном или 16-разрядное буфера и оставьте без изменений бит высокого порядка. Таким образом приложения следует инициализировать значение 0, перед вызовом этой функции.  
  
## <a name="returns"></a>Возвращает  
 Значение SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLColAttribute** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, можно получить путем вызова связанного значения SQLSTATE **SQLGetDiagRec** с *HandleType*значение SQL_HANDLE_STMT и *обрабатывать* из *StatementHandle*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые **SQLColAttribute** и объясняется каждый из них в контексте этой функции; описания SQLSTATE, возвращаемых диспетчером драйверов предшествует обозначение «(DM)». Возвращается связанный с каждого значения SQLSTATE значение SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Специфические для драйвера информационное сообщение. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|01004|Усечение данных строки справа|Буфер \* *CharacterAttributePtr* не достаточно для возврата всей строки, поэтому строковое значение усечено. Длина неусеченный строковое значение возвращается в **StringLengthPtr*. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|07005|Подготовленной инструкции не *спецификацией курсора.*|Инструкция, связанная с *StatementHandle* не вернул результирующий набор и *FieldIdentifier* не SQL_DESC_COUNT. Нет столбцов для описания.|  
|07009|Недопустимый индекс дескриптора|(DM) значение, заданное для *ColumnNumber* равно 0, и атрибут инструкции SQL_ATTR_USE_BOOKMARKS SQL_UB_OFF.<br /><br /> Значение, указанное для аргумента *ColumnNumber* поданных единиц превысил количество столбцов в результирующем наборе.|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет конкретных SQLSTATE и SQLSTATE не зависящие от реализации, который был определен. Сообщение об ошибке, возвращенные **SQLGetDiagField** из диагностические данные структура описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйвер не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY008|Операция отменена|Асинхронная обработка была включена для *StatementHandle*. Функция была вызвана, и до его завершения выполнения, **SQLCancel** или **SQLCancelHandle** был вызван для *StatementHandle*. Затем функция был снова вызван для *StatementHandle*.<br /><br /> Функция была вызвана, и до его завершения выполнения, **SQLCancel** или **SQLCancelHandle** был вызван для *StatementHandle* из другого потока в многопоточные приложения.|  
|HY010|Ошибка последовательности функций|(DM) был вызван асинхронно выполняемой функции для дескриптора соединения, связанный с *StatementHandle*. Эта функция aynchronous еще выполнялась при вызове SQLColAttribute.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, или **SQLMoreResults** был вызван для *StatementHandle* и возвращается SQL_PARAM_DATA_ ДОСТУПНО. Прежде чем данные были получены для всех параметров потоковой вызове этой функции.<br /><br /> (DM), что функция была вызвана до вызова метода **SQLPrepare**, **SQLExecDirect**, или функции каталога для *StatementHandle*.<br /><br /> (DM) асинхронно выполняемой функции (не такой) был вызван для *StatementHandle* и еще выполнялась при вызове этой функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, или **SQLSetPos** был вызван для  *StatementHandle* и возвращается значение SQL_NEED_DATA. Эта функция был вызван перед отправкой данных для всех параметров данных времени выполнения или столбцов.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, так как базовые объекты памяти оказываются недоступны, возможно из-за нехватки памяти.|  
|HY090|Недопустимая длина строки или буфера|(DM)  *\*CharacterAttributePtr* представляет собой строку символов и *BufferLength* меньше, чем 0, но не равно SQL_NTS.|  
|HY091|Недопустимый идентификатор поля дескриптора|Значение, указанное для аргумента *FieldIdentifier* не является одним из определенных значений, а не значение, определяемое реализацией.|  
|HY117|Подключение будет приостановлена из-за состояние транзакции неизвестно. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки, см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Драйвер не поддерживает|Значение, указанное для аргумента *FieldIdentifier* не поддерживается драйвером.|  
|HYT01|Время ожидания подключения истекло|Время ожидания подключения истекло раньше, чем ответил на запрос источника данных. Период времени ожидания задается с помощью **SQLSetConnectAttr**, sql_attr_connection_timeout не учитывается.|  
|IM001|Драйвер не поддерживает эту функцию|Драйвер (DM), связанные с *StatementHandle* не поддерживает функцию.|  
|IM017|Опрос недоступен в режиме асинхронное уведомление|Каждый раз, когда используется модель уведомлений, отключен опроса.|  
|IM018|**SQLCompleteAsync** не был вызван для завершения предыдущей асинхронной операции на этот дескриптор.|Если предыдущий вызов функции в дескриптор возвращает SQL_STILL_EXECUTING, и если включен режим уведомлений, **SQLCompleteAsync** должен вызываться с дескриптором постобработки и завершить операцию.|  
  
 При вызове после **SQLPrepare** и перед **SQLExecute**, **SQLColAttribute** может возвращать любой SQLSTATE, которые могут быть возвращены с **SQLPrepare**или **SQLExecute**зависимости от того, если источник данных принимает инструкции SQL, связанные с *StatementHandle*.  
  
 Для повышения производительности, приложение не должно вызывать **SQLColAttribute** перед выполнением инструкции.  
  
## <a name="comments"></a>Комментарии  
 Сведения об использовании сведений, полученных с помощью приложений **SQLColAttribute**, см. в разделе [результирующий набор метаданных](../../../odbc/reference/develop-app/result-set-metadata.md).  
  
 **SQLColAttribute** возвращает сведения либо в \* *NumericAttributePtr* или в \* *CharacterAttributePtr*. Целое число сведения возвращаются в \* *NumericAttributePtr* как значение SQLLEN; все другие форматы сведения возвращаются в \* *CharacterAttributePtr*. Если информация возвращается в \* *NumericAttributePtr*, драйвер пропускает *CharacterAttributePtr*, *BufferLength*, и  *StringLengthPtr*. Если информация возвращается в \* *CharacterAttributePtr*, драйвер пропускает *NumericAttributePtr*.  
  
 **SQLColAttribute** возвращает значения из полей дескриптора IRD. Функция вызывается с помощью дескриптора инструкции, а не дескриптора. Значения, возвращаемые методом **SQLColAttribute** для *FieldIdentifier* значения, описанные далее в этом разделе также можно получить, вызвав **SQLGetDescField** с соответствующий дескриптор IRD.  
  
 В настоящее время определены дескриптор поля, используемая версия ODBC, в котором они были введены, а также аргументы, в которых возвращаются сведения об их позже в этом разделе; Дополнительные типы дескрипторов может быть уточнен драйверы, чтобы воспользоваться преимуществами различных источников данных.  
  
 ODBC 3. *x* драйвер должен возвращать значение для каждого из полей дескриптора. Если поле дескриптора не применяется к источнику драйвера или данных, и если не указано иное, драйвер возвращает 0 в \* *StringLengthPtr* или пустая строка в **CharacterAttributePtr*.  
  
## <a name="backward-compatibility"></a>Backward Compatibility  
 ODBC 3. *x* функция **SQLColAttribute** заменяет устаревшие ODBC 2. *x* функция **SQLColAttributes**. При сопоставлении **SQLColAttributes** для **SQLColAttribute** (когда ODBC 2. *x* при работе с ODBC 3. *x* драйвер), или сопоставление **SQLColAttribute** для **SQLColAttributes** (когда ODBC 3. *x* при работе с ODBC 2. *x* драйвер), диспетчер драйверов либо передает значение *FieldIdentifier* , сопоставляет его новое значение или возвращает ошибку, как показано ниже:  
  
> [!NOTE]  
>  Префикс, используемый в *FieldIdentifier* значения в ODBC 3. *x* было изменено с, используемых в ODBC 2. *x*. Новый префикс — «SQL_DESC»; старый префикс был «SQL_COLUMN».  
  
-   Если **#define** значение ODBC 2. *x* *FieldIdentifier* совпадает со значением **#define** значение ODBC 3. *x* *FieldIdentifier*, просто передается значение при вызове функции.  
  
-   **#Define** значения ODBC 2. *x* *FieldIdentifiers* SQL_COLUMN_LENGTH SQL_COLUMN_PRECISION и SQL_COLUMN_SCALE отличаются от **#define** значения ODBC 3. *x* *FieldIdentifiers* SQL_DESC_PRECISION SQL_DESC_SCALE и SQL_DESC_LENGTH. ODBC 2. *x* драйвер должен поддерживать только ODBC 2. *x* значения. ODBC 3. *x* драйвер должен поддерживать значения «SQL_COLUMN» и «SQL_DESC» для этих трех *FieldIdentifiers*. Эти значения отличаются, так как точность, масштаб и длина определяются по-другому в ODBC 3. *x* в ODBC 2. *x*. Дополнительные сведения см. в разделе [размер столбца, десятичных разрядов, длительность октета передачи и отображаемый размер](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md).  
  
-   Если **#define** значение ODBC 2. *x* *FieldIdentifier* отличается от **#define** значение ODBC 3. *x* *FieldIdentifier*, как происходит с числом, имя и значения NULL, значение в вызове функции сопоставлен с соответствующим значением. Например, SQL_COLUMN_COUNT сопоставляется SQL_DESC_COUNT, а SQL_DESC_COUNT сопоставляется SQL_COLUMN_COUNT, в зависимости от направления сопоставления.  
  
-   Если *FieldIdentifier* новое значение в ODBC 3. *x*, для которой было без соответствующего значения в ODBC 2. *x*, он не будет сопоставляться при ODBC 3. *x* приложение использует его в вызове **SQLColAttribute** в ODBC 2. *x* драйвер и вызов вернет SQLSTATE HY091 (недопустимый идентификатор поля дескриптора).  
  
 В следующей таблице перечислены типы дескрипторов, возвращенный **SQLColAttribute**. Тип для *NumericAttributePtr* значения — **SQLLEN \*** .  
  
|*FieldIdentifier*|Information<br /><br /> возвращается в|Описание|  
|-----------------------|---------------------------------|-----------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE (ODBC 1.0)|*NumericAttributePtr*|SQL_TRUE, если столбец является столбцом с автоматическим приращением.<br /><br /> Значение SQL_FALSE, если столбец не является столбцом с автоматическим приращением, или не является числом.<br /><br /> Это поле является допустимым для только столбцы типа числовых данных. Приложение может вставлять значение в строку, содержащую столбец «Автоувеличение», но обычно не удается обновить значения в столбце.<br /><br /> При внесении вставки в столбец «Автоувеличение», уникальное значение вставляется в столбец во время операции вставки. Приращение не определен, но — это данные, зависящие от источника. Приложения не должен предполагать, что столбец autoincrement начинается в любой определенный момент или с шагом по любой определенное значение.|  
|SQL_DESC_BASE_COLUMN_NAME (ODBC 3.0)|*CharacterAttributePtr*|Имя базового столбца для результирующего набора столбцов. Если имя базового столбца не существует (как в случае столбцы, являющиеся выражениями), то эта переменная содержит пустую строку.<br /><br /> Эти сведения возвращаются из поля записи SQL_DESC_BASE_COLUMN_NAME ird, предназначенного только для чтения.|  
|SQL_DESC_BASE_TABLE_NAME (ODBC 3.0)|*CharacterAttributePtr*|Имя базовой таблицы, содержащей столбец. Если имя базовой таблицы не могут быть определены или не применяется, то эта переменная содержит пустую строку.<br /><br /> Эти сведения возвращаются из поля записи SQL_DESC_BASE_TABLE_NAME ird, предназначенного только для чтения.|  
|SQL_DESC_CASE_SENSITIVE (ODBC 1.0)|*NumericAttributePtr*|SQL_TRUE, если столбец обрабатывается как с учетом регистра для сортировки и сравнений.<br /><br /> Если столбец не обрабатывается, как с учетом регистра для сортировки и сравнений или является символьным значение SQL_FALSE.|  
|SQL_DESC_CATALOG_NAME (ODBC 2.0)|*CharacterAttributePtr*|Каталог таблицы, содержащей столбец. Возвращаемое значение зависит от реализации, если столбец является выражением, или если столбец является частью представления. Если источник данных не поддерживает каталоги или невозможно определить имя каталога, возвращается пустая строка. Это поле записи VARCHAR не должна превышать 128 символов.|  
|SQL_DESC_CONCISE_TYPE (ODBC 1.0)|*NumericAttributePtr*|Тип данных, краткими.<br /><br /> Для типов данных даты и времени и интервала это поле возвращает тип краткими данных; Например, SQL_TYPE_TIME или SQL_INTERVAL_YEAR. (Дополнительные сведения см. в разделе [данных идентификаторы и дескрипторы типов](../../../odbc/reference/appendixes/data-type-identifiers-and-descriptors.md) в приложение г Типы данных).<br /><br /> Эти сведения возвращаются из поля записи SQL_DESC_CONCISE_TYPE IRD.|  
|SQL_DESC_COUNT (ODBC 1.0)|*NumericAttributePtr*|Число столбцов, доступных в результирующем наборе. Возвращает 0, если отсутствуют столбцы в результирующем наборе. Значение в *ColumnNumber* аргумент учитывается.<br /><br /> Эти сведения возвращаются из поля заголовка SQL_DESC_COUNT IRD.|  
|СТОЛБЦОВ SQL_DESC_DISPLAY_SIZE (ODBC 1.0)|*NumericAttributePtr*|Максимальное количество символов, необходимых для отображения данных из столбца. Дополнительные сведения о размерах дисплея, см. в разделе [размер столбца, десятичных разрядов, длительность октета передачи и отображения размер](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) в приложение г Типы данных.|  
|SQL_DESC_FIXED_PREC_SCALE (ODBC 1.0)|*NumericAttributePtr*|SQL_TRUE, если столбец имеет фиксированные точность и масштаб ненулевое значение, зависящие от источника данных.<br /><br /> Значение SQL_FALSE, если столбец имеет фиксированные точность и масштаб ненулевое значение, зависящие от источника данных.|  
|SQL_DESC_LABEL (ODBC 2.0)|*CharacterAttributePtr*|Метки столбца или заголовок. Например столбец с именем EmpName может называться имя сотрудника или может быть помечено с псевдонимом.<br /><br /> Если столбец не содержит метку, возвращается имя столбца. Если столбец является без метки и без имени, возвращается пустая строка.|  
|SQL_DESC_LENGTH (ODBC 3.0)|*NumericAttributePtr*|Числовое значение, либо длина максимальное или фактического символа символьных данных строкового или двоичного типа. Это максимальное количество символов для типа данных фиксированной длины или длина Фактический символ для типа данных переменной длины. Его значение всегда исключает байта конечное значение null, который заканчивается символьной строки.<br /><br /> Эти сведения возвращаются из поля записи SQL_DESC_LENGTH IRD.<br /><br /> Дополнительные сведения о длине см. в разделе [размер столбца, десятичных разрядов, длительность октета передачи и отображаемый размер](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) в приложение г Типы данных.|  
|SQL_DESC_LITERAL_PREFIX (ODBC 3.0)|*CharacterAttributePtr*|Это поле записи VARCHAR(128) содержит символ или символы, которые драйвер распознает как префикс для литерала этого типа данных. Это поле содержит пустую строку для типа данных, для которого префикс литерала не применимо. Дополнительные сведения см. в разделе [литерала префиксы и суффиксы](../../../odbc/reference/develop-app/literal-prefixes-and-suffixes.md).|  
|SQL_DESC_LITERAL_SUFFIX (ODBC 3.0)|*CharacterAttributePtr*|Это поле записи VARCHAR(128) содержит символ или символы, которые драйвер распознает в качестве суффикса для литерала этого типа данных. Это поле содержит пустую строку для типа данных, для которого литеральный суффикс не применимо. Дополнительные сведения см. в разделе [литерала префиксы и суффиксы](../../../odbc/reference/develop-app/literal-prefixes-and-suffixes.md).|  
|SQL_DESC_LOCAL_TYPE_NAME (ODBC 3.0)|*CharacterAttributePtr*|Это поле записи VARCHAR(128) содержит все локализованные (собственное) название языка для типа данных, который может отличаться от стандартное имя типа данных. Если не локализованное имя, возвращается пустая строка. Это поле является только в целях отображения. Набор символов строки зависящего от языкового стандарта и обычно является кодировка по умолчанию сервера.|  
|SQL_DESC_NAME (ODBC 3.0)|*CharacterAttributePtr*|Псевдоним столбца, если он применяется. Если псевдоним столбца не применимо, возвращается имя столбца. В любом случае SQL_DESC_UNNAMED имеет значение SQL_NAMED. Если отсутствует имя столбца или псевдоним столбца, возвращается пустая строка и SQL_DESC_UNNAMED присваивается SQL_UNNAMED.<br /><br /> Эти сведения возвращаются из поля записи SQL_DESC_NAME IRD.|  
|SQL_DESC_NULLABLE (ODBC 3.0)|*NumericAttributePtr*|SQL_ значение NULL, если столбец может иметь значения NULL; SQL_NO_NULLS, если столбец не имеет значения NULL; или SQL_NULLABLE_UNKNOWN, если неизвестно, допускает ли столбец значения NULL.<br /><br /> Эти сведения возвращаются из поля записи SQL_DESC_NULLABLE IRD.|  
|SQL_DESC_NUM_PREC_RADIX (ODBC 3.0)|*NumericAttributePtr*|Если тип данных в поле SQL_DESC_TYPE имеет тип приблизительных числовых данных, это поле SQLINTEGER содержит значение 2, так как поле SQL_DESC_PRECISION содержит количество битов. Если тип данных в поле SQL_DESC_TYPE типа точных числовых данных, это поле содержит значение 10, так как поле SQL_DESC_PRECISION содержит количество цифр дробной части. Это поле имеет значение 0 для всех типов нечисловые данные.|  
|SQL_DESC_OCTET_LENGTH (ODBC 3.0)|*NumericAttributePtr*|Длина строкового или двоичного символьными данными в байтах. Для фиксированной длины символьных или двоичных типов это фактическая длина в байтах. Для переменной длины символьных или двоичных типов это максимальная длина в байтах. Это значение не включает знак завершения null.<br /><br /> Эти сведения возвращаются из поля записи SQL_DESC_OCTET_LENGTH IRD.<br /><br /> Дополнительные сведения о длине см. в разделе [размер столбца, десятичных разрядов, длительность октета передачи и отображаемый размер](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) в приложение г Типы данных.|  
|SQL_DESC_PRECISION (ODBC 3.0)|*NumericAttributePtr*|Числовое значение, обозначает применимо точность для числового типа данных. Для типов данных, SQL_TYPE_TIME SQL_TYPE_TIMESTAMP, и все типы данных интервала представляющие интервал времени, его значение является применимо точность долей секунды в значении.<br /><br /> Эти сведения возвращаются из поля записи SQL_DESC_PRECISION IRD.|  
|SQL_DESC_SCALE (ODBC 3.0)|*NumericAttributePtr*|Числовое значение, которое применимо масштаб для числового типа данных. Для типов данных DECIMAL и NUMERIC это заданного масштаба. Он не определен для всех других типов данных.<br /><br /> Эти сведения возвращаются из поля записи IRD МАСШТАБИРОВАНИЯ.|  
|SQL_DESC_SCHEMA_NAME (ODBC 2.0)|*CharacterAttributePtr*|Схема таблицы, содержащей столбец. Возвращаемое значение зависит от реализации, если столбец является выражением, или если столбец является частью представления. Если источник данных не поддерживает схемы или имя схемы не может быть определено, возвращается пустая строка. Это поле записи VARCHAR не должна превышать 128 символов.|  
|SQL_DESC_SEARCHABLE (ODBC 1.0)|*NumericAttributePtr*|SQL_PRED_NONE, если столбец не может использоваться в предложении WHERE. (Это то же самое значение SQL_UNSEARCHABLE ODBC 2. *x*.)<br /><br /> SQL_PRED_CHAR, если столбец может использоваться в предложении WHERE, но только с предикатом LIKE. (Это то же самое значение SQL_LIKE_ONLY ODBC 2. *x*.)<br /><br /> SQL_PRED_BASIC, если столбец может использоваться в предложении WHERE, со всеми операторами сравнения, за исключением LIKE. (Это то же самое значение SQL_EXCEPT_LIKE ODBC 2. *x*.)<br /><br /> SQL_PRED_SEARCHABLE, если столбец может использоваться в предложении WHERE с любым оператором сравнения.<br /><br /> Столбцы типа SQL_LONGVARCHAR и обычно возвращаемое SQL_PRED_CHAR SQL_LONGVARBINARY.|  
|SQL_DESC_TABLE_NAME (ODBC 2.0)|*CharacterAttributePtr*|Имя таблицы, содержащей столбец. Возвращаемое значение зависит от реализации, если столбец является выражением, или если столбец является частью представления.<br /><br /> Если имя таблицы не может быть определен, возвращается пустая строка.|  
|SQL_DESC_TYPE (ODBC 3.0)|*NumericAttributePtr*|Числовое значение, указывающее тип данных SQL.<br /><br /> Когда *ColumnNumber* равен 0, возвращается SQL_BINARY для закладок переменной длины и SQL_INTEGER возвращается для закладки фиксированной длины.<br /><br /> Для типов данных даты и времени и интервала это поле возвращает тип подробные данные: SQL_DATETIME или SQL_INTERVAL. (Дополнительные сведения см. в разделе [данных идентификаторы и дескрипторы типов](../../../odbc/reference/appendixes/data-type-identifiers-and-descriptors.md) в приложение г Типы данных.<br /><br /> Эти сведения возвращаются из поля записи SQL_DESC_TYPE IRD. **Примечание.**  Для работы с ODBC 2. *x* драйверы, вместо этого используйте SQL_DESC_CONCISE_TYPE.|  
|SQL_DESC_TYPE_NAME (ODBC 1.0)|*CharacterAttributePtr*|Имя типа данных зависит от источника данных; Например «CHAR», «VARCHAR», «Деньги», «LONG VARBINARY» или «() CHAR FOR BIT DATA».<br /><br /> Если тип неизвестен, возвращается пустая строка.|  
|SQL_DESC_UNNAMED (ODBC 3.0)|*NumericAttributePtr*|SQL_NAMED или SQL_UNNAMED. Если поле SQL_DESC_NAME IRD содержит псевдоним столбца или имя столбца, возвращается SQL_NAMED. Если нет, имя столбца или псевдоним столбца, возвращается SQL_UNNAMED.<br /><br /> Эти сведения возвращаются из поля записи SQL_DESC_UNNAMED IRD.|  
|SQL_DESC_UNSIGNED (ODBC 1.0)|*NumericAttributePtr*|SQL_TRUE, если столбец является или без знака (не числовое).<br /><br /> Значение SQL_FALSE, если столбец имеет подписи.|  
|SQL_DESC_UPDATABLE (ODBC 1.0)|*NumericAttributePtr*|Описывается столбец значения для определенных констант:<br /><br /> SQL_ATTR_READONLY SQL_ATTR_WRITE SQL_ATTR_READWRITE_UNKNOWN<br /><br /> SQL_DESC_UPDATABLE описывает возможность обновления столбца в результирующем наборе, не столбец в базовой таблице. Возможность обновления базового столбца, на котором основан столбец результирующего набора может отличаться от значения в этом поле. Является ли столбец обновляемых могут основываться на тип данных, права доступа пользователя и определения результирующего набора, сам. Если неясно, является ли столбец можно обновлять, SQL_ATTR_READWRITE_UNKNOWN должно быть возвращено.|  
  
 **SQLColAttribute** — это расширяемая альтернатива **SQLDescribeCol**. **SQLDescribeCol** возвращает фиксированный набор на основе SQL ANSI-89 данные дескриптора. **SQLColAttribute** позволяет получить доступ к более широкий набор дескриптор сведений, доступных в ANSI SQL-92 и СУБД поставщика расширений.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Привязка к столбцу в результирующем наборе буфер|[Функция SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Отмена обработка инструкций|[Функция SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Возврат сведений о столбце в результирующий набор|[Функция SQLDescribeCol](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|Блока данных или прокрутке результирующего набора|[Функция SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Получение нескольких строк данных|[Функция SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
  
## <a name="example"></a>Пример  
 В следующем примере кода не позволяет освободить дескрипторы и подключения. См. в разделе [SQLFreeHandle, функция](../../../odbc/reference/syntax/sqlfreehandle-function.md), [образец программы ODBC](../../../odbc/reference/sample-odbc-program.md), и [SQLFreeStmt, функция](../../../odbc/reference/syntax/sqlfreestmt-function.md) примеры кода для освобождения дескрипторов и инструкций.  
  
```cpp  
// SQLColAttibute.cpp  
// compile with: user32.lib odbc32.lib  
  
#define UNICODE  
  
#include <windows.h>  
#include <sqlext.h>  
#include <strsafe.h>  
  
struct DataBinding {  
   SQLSMALLINT TargetType;  
   SQLPOINTER TargetValuePtr;  
   SQLINTEGER BufferLength;  
   SQLLEN StrLen_or_Ind;  
};  
  
void printStatementResult(SQLHSTMT hstmt) {  
   int bufferSize = 1024, i;  
   SQLRETURN retCode;  
   SQLSMALLINT numColumn = 0, bufferLenUsed;
   
   retCode = SQLNumResultCols(hstmt, &numColumn);  
   
   SQLPOINTER* columnLabels = (SQLPOINTER *)malloc( numColumn * sizeof(SQLPOINTER*) );  
   struct DataBinding* columnData = (struct DataBinding*)malloc( numColumn * sizeof(struct DataBinding) );  
  
   printf( "Columns from that table:\n" );  
   for ( i = 0 ; i < numColumn ; i++ ) {  
      columnLabels[i] = (SQLPOINTER)malloc( bufferSize*sizeof(char) );  
  
      retCode = SQLColAttribute(hstmt, (SQLUSMALLINT)i + 1, SQL_DESC_LABEL, columnLabels[i], (SQLSMALLINT)bufferSize, &bufferLenUsed, NULL);  
      wprintf( L"Column %d: %s\n", i, (wchar_t*)columnLabels[i] );  
   }  
  
   // allocate memory for the binding  
   for ( i = 0 ; i < numColumn ; i++ ) {  
      columnData[i].TargetType = SQL_C_CHAR;  
      columnData[i].BufferLength = (bufferSize+1);  
      columnData[i].TargetValuePtr = malloc( sizeof(unsigned char)*columnData[i].BufferLength );  
   }  
  
   // setup the binding   
   for ( i = 0 ; i < numColumn ; i++ ) {  
      retCode = SQLBindCol(hstmt, (SQLUSMALLINT)i + 1, columnData[i].TargetType,   
         columnData[i].TargetValuePtr, columnData[i].BufferLength, &(columnData[i].StrLen_or_Ind));  
   }  
  
   printf( "Data from that table:\n" );  
   // fetch the data and print out the data  
   for ( retCode = SQLFetch(hstmt) ; retCode == SQL_SUCCESS || retCode == SQL_SUCCESS_WITH_INFO ; retCode = SQLFetch(hstmt) ) {  
      int j;  
      for ( j = 0 ; j < numColumn ; j++ )  
         wprintf( L"%s: %hs\n", columnLabels[j], columnData[j].TargetValuePtr );  
      printf( "\n" );  
   }  
   printf( "\n" );   
}  
  
int main() {  
   int bufferSize = 1024, i, count = 1, numCols = 5;  
   wchar_t firstTableName[1024], * dbName = (wchar_t *)malloc( sizeof(wchar_t)*bufferSize ), * userName = (wchar_t *)malloc( sizeof(wchar_t)*bufferSize );  
   HWND desktopHandle = GetDesktopWindow();   // desktop's window handle  
   SQLWCHAR connStrbuffer[1024];  
   SQLSMALLINT connStrBufferLen, bufferLen;  
   SQLRETURN retCode;  
  
   SQLHENV henv = NULL;   // Environment     
   SQLHDBC hdbc = NULL;   // Connection handle  
   SQLHSTMT hstmt = NULL;   // Statement handle  
  
   struct DataBinding* catalogResult = (struct DataBinding*) malloc( numCols * sizeof(struct DataBinding) );  
   SQLWCHAR* selectAllQuery = (SQLWCHAR *)malloc( sizeof(SQLWCHAR) * bufferSize );  
  
   // connect to database  
   retCode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
   retCode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLCHAR *)(void*)SQL_OV_ODBC3, -1);  
   retCode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
   retCode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)10, 0);  
   retCode = SQLDriverConnect(hdbc, desktopHandle, L"Driver={SQL Server}", SQL_NTS, connStrbuffer, 1025, &connStrBufferLen, SQL_DRIVER_PROMPT);  
   retCode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
  
   // display the database information  
   retCode = SQLGetInfo(hdbc, SQL_DATABASE_NAME, dbName, (SQLSMALLINT)bufferSize, (SQLSMALLINT *)&bufferLen);  
   retCode = SQLGetInfo(hdbc, SQL_USER_NAME, userName, (SQLSMALLINT)bufferSize, &bufferLen);  
  
   for ( i = 0 ; i < numCols ; i++ ) {  
      catalogResult[i].TargetType = SQL_C_CHAR;  
      catalogResult[i].BufferLength = (bufferSize + 1);  
      catalogResult[i].TargetValuePtr = malloc( sizeof(unsigned char)*catalogResult[i].BufferLength );  
   }  
  
   // Set up the binding. This can be used even if the statement is closed by closeStatementHandle  
   for ( i = 0 ; i < numCols ; i++ )  
      retCode = SQLBindCol(hstmt, (SQLUSMALLINT)i + 1, catalogResult[i].TargetType, catalogResult[i].TargetValuePtr, catalogResult[i].BufferLength, &(catalogResult[i].StrLen_or_Ind));  
  
   retCode = SQLTables( hstmt, (SQLWCHAR*)SQL_ALL_CATALOGS, SQL_NTS, L"", SQL_NTS, L"", SQL_NTS, L"", SQL_NTS );  
   retCode = SQLFreeStmt(hstmt, SQL_CLOSE);  
  
   retCode = SQLTables( hstmt, dbName, SQL_NTS, userName, SQL_NTS, L"%", SQL_NTS, L"TABLE", SQL_NTS );  
  
   for ( retCode = SQLFetch(hstmt) ; retCode == SQL_SUCCESS || retCode == SQL_SUCCESS_WITH_INFO ; retCode = SQLFetch(hstmt), ++count )  
      if ( count == 1 )  
         StringCchPrintfW( firstTableName, 1024, L"%hs", catalogResult[2].TargetValuePtr );  
   retCode = SQLFreeStmt(hstmt, SQL_CLOSE);  
  
   wprintf( L"Select all data from the first table (%s)\n", firstTableName );  
   StringCchPrintfW( selectAllQuery, bufferSize, L"SELECT * FROM %s", firstTableName );  
  
   retCode = SQLExecDirect(hstmt, selectAllQuery, SQL_NTS);  
   printStatementResult(hstmt);  
}  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)   
 [Образец программы ODBC](../../../odbc/reference/sample-odbc-program.md)
