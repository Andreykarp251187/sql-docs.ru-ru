---
title: Функция SQLDisconnect | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLDisconnect
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLDisconnect
helpviewer_keywords:
- SQLDisconnect function [ODBC]
ms.assetid: 9e84a58e-db48-4821-a0cd-5c711fcbe36b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 444e41699c1a61acb82acc419a2f23db6142f7bb
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65537559"
---
# <a name="sqldisconnect-function"></a>Функция SQLDisconnect
**Соответствие стандартам**  
 Представленные версии: Соответствие стандартам 1.0 ODBC: ISO-92  
  
 **Сводка**  
 **SQLDisconnect** закрывает подключение, связанное с дескриптором конкретным соединением.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
SQLRETURN SQLDisconnect(  
     SQLHDBC     ConnectionHandle);  
```  
  
## <a name="arguments"></a>Аргументы  
 *ConnectionHandle*  
 [Input] Дескриптор подключения  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_INVALID_HANDLE, or SQL_STILL_EXECUTING.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLDisconnect** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, а связанное значение SQLSTATE может быть получен путем вызова **SQLGetDiagRec** с *HandleType* из SQL_ HANDLE_DBC и *обрабатывать* из *ConnectionHandle*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые **SQLDisconnect** и объясняется каждый из них в контексте этой функции; описания SQLSTATE, возвращаемых диспетчером драйверов предшествует обозначение «(DM)». Возвращается связанный с каждого значения SQLSTATE значение SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Специфические для драйвера информационное сообщение. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|01002|Ошибка во время отключения|Произошла ошибка во время отключения. Однако отключение выполнено успешно. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|08003|Соединение не открыто|Подключение (DM), указанных в аргументе *ConnectionHandle* не был открыт.|  
|25000|Недопустимое состояние транзакции|Произошла транзакции в процессе на соединение, указанное в аргументе *ConnectionHandle*. Транзакция остается активной.|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет конкретных SQLSTATE и SQLSTATE не зависящие от реализации, который был определен. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в  *\*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйвер не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY008|Операция отменена|Асинхронная обработка была включена для *ConnectionHandle*. Функция была вызвана, и перед его выполнением завершил [функция SQLCancelHandle](../../../odbc/reference/syntax/sqlcancelhandle-function.md) был вызван для *ConnectionHandle*. Затем функция был снова вызван для *ConnectionHandle*.<br /><br /> Функция была вызвана, и до завершения выполнения **SQLCancelHandle** был вызван для *ConnectionHandle* из другого потока в многопоточных приложениях.|  
|HY010|Ошибка последовательности функций|(DM) был вызван асинхронно выполняемой функции для *StatementHandle* связанные с *ConnectionHandle* и еще выполнялась при **SQLDisconnect** был вызывается.<br /><br /> (DM) асинхронно выполняемой функции (не такой) был вызван для *ConnectionHandle* и еще выполнялась при вызове этой функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, или **SQLSetPos** был вызван для *StatementHandle*  связанные с *ConnectionHandle* и возвращается значение SQL_NEED_DATA. Эта функция был вызван перед отправкой данных для всех параметров данных времени выполнения или столбцов.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, так как базовые объекты памяти оказываются недоступны, возможно из-за нехватки памяти.|  
|HY117|Подключение будет приостановлена из-за состояние транзакции неизвестно. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки, см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Время ожидания подключения истекло|Время ожидания подключения истекло раньше, чем ответил на запрос источника данных, а подключение по-прежнему активна. Период времени ожидания задается с помощью **SQLSetConnectAttr**, sql_attr_connection_timeout не учитывается.|  
|IM001|Драйвер не поддерживает эту функцию|Драйвер (DM), связанные с *ConnectionHandle* не поддерживает функцию.|  
|IM017|Опрос недоступен в режиме асинхронное уведомление|Каждый раз, когда используется модель уведомлений, отключен опроса.|  
|IM018|**SQLCompleteAsync** не был вызван для завершения предыдущей асинхронной операции на этот дескриптор.|Если предыдущий вызов функции в дескриптор возвращает SQL_STILL_EXECUTING, и если включен режим уведомлений, **SQLCompleteAsync** должен вызываться с дескриптором постобработки и завершить операцию.|  
  
## <a name="comments"></a>Комментарии  
 Если приложение вызывает **SQLDisconnect** после **SQLBrowseConnect** возвращает SQL_NEED_DATA и до возвращения другого кода возврата, драйвер отменяет соединение с обзора процесса и возвращает подключение неподключенный состоянии.  
  
 Если приложение вызывает **SQLDisconnect** есть незавершенной транзакцией, связанной с дескриптором соединения, драйвер возвращает SQLSTATE 25000 (недопустимое состояние транзакции), указывает, что транзакции без изменений и, при открытом соединении. Незавершенная транзакция — это приложения, не зафиксирована или откатана с **SQLEndTran**.  
  
 Если приложение вызывает **SQLDisconnect** перед его освободит все операторы, связанные с подключением, драйвер, после его успешного отключается от источника данных, освобождает этих инструкций и все дескрипторы, которые были явно выделенные при соединении. Тем не менее, если один или несколько инструкций, связанный с подключением по-прежнему выполняются асинхронно, **SQLDisconnect** возвращает ошибку SQL_ERROR со значением SQLSTATE HY010 (функционировать ошибка последовательности). Кроме того **SQLDisconnect** , чтобы освободить все связанные инструкции и все дескрипторы, которые были явным образом выделены в соединении, если соединение находится в приостановленном состоянии, или если **SQLDisconnect** был успешно отменено **SQLCancelHandle**.  
  
 Сведения о способе использования приложением **SQLDisconnect**, см. в разделе [отключение от источника данных или драйвера](../../../odbc/reference/develop-app/disconnecting-from-a-data-source-or-driver.md).  
  
## <a name="disconnecting-from-a-pooled-connection"></a>Отключение от соединение из пула  
 Если включено использование пулов соединений для совместно используемой среде, и приложение вызывает **SQLDisconnect** для подключения в этой среде, соединение возвращается в пул подключений и по-прежнему доступен для других компонентов, с помощью одной общей среде.  
  
## <a name="code-example"></a>Пример кода  
 См. в разделе [образец программы ODBC](../../../odbc/reference/sample-odbc-program.md), [функция SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md), и [функция SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Выделение дескриптора|[Функция SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Подключение к источнику данных|[Функция SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|Подключение к источнику данных с помощью соединения строки или в диалоговом окне|[Функция SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|Выполнение операции фиксации или отката|[Функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|Освобождение дескриптора соединения|[Функция SQLFreeConnect](../../../odbc/reference/syntax/sqlfreeconnect-function.md)|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
