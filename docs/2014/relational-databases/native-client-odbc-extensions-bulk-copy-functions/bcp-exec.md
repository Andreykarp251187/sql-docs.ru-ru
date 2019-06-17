---
title: bcp_exec | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_exec
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_exec function
ms.assetid: b23ea2cc-8545-4873-b0c1-57e76b0a3a7b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1d5ce458ea8f5874620ea0561eeea5c6ff8e56bb
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62689037"
---
# <a name="bcpexec"></a>bcp_exec
  Выполняет полное массовое копирование данных из пользовательского файла в таблицу базы данных или обратно.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
RETCODE bcp_exec (  
HDBC   
hdbc  
,  
LPDBINT   
pnRowsProcessed  
);  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *HDBC*  
 Дескриптор соединения ODBC с поддержкой массового копирования.  
  
 *pnRowsProcessed*  
 Указатель на переменную DBINT. Функция **bcp_exec** заполняет DBINT числом успешно скопированных строк. Если значение параметра *pnRowsProcessed* равно NULL, то оно не учитывается функцией **bcp_exec**.  
  
## <a name="returns"></a>Возвращает  
 SUCCEED, SUCCEED_ASYNC или FAIL. Функция **bcp_exec** возвращает значение SUCCEED, если были скопированы все строки. Если асинхронная операция массового копирование еще не завершена, то функция**bcp_exec** возвращает значение SUCCEED_ASYNC. Функция**bcp_exec** возвращает значение FAIL, если возникла неисправимая ошибка либо если число ошибочных строк достигло значения, заданного в параметре BCPMAXERRS с помощью программы [bcp_control](bcp-control.md). Значение BCPMAXERRS по умолчанию равно 10. Параметр BCPMAXERRS относится только к синтаксическим ошибкам, обнаруживаемым поставщиком при чтении строк из файла данных (а не к строкам, отправляемым на сервер). Сервер прерывает выполнение пакета при обнаружении ошибки в строке. Проверьте параметр *pnRowsProcessed* , чтобы получить число успешно скопированных строк.  
  
## <a name="remarks"></a>Примечания  
 Эта функция копирует данные из пользовательского файла в таблицу базы данных или наоборот в зависимости от значения параметра *eDirection* в функции [bcp_init](bcp-init.md).  
  
 Перед вызовом функции **bcp_exec**необходимо вызвать функцию **bcp_init** с допустимым именем пользовательского файла. Несоблюдение этого правила приведет к ошибке.  
  
 Функция**bcp_exec** представляет собой только функцию массового копирования, которая с большой долей вероятности остается необработанной в течение неограниченного отрезка времени. Вот почему это единственная функция массового копирования, поддерживающая асинхронный режим. Для установки асинхронного режима используется функция [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) , чтобы выставить атрибуту SQL_ATTR_ASYNC_ENABLE значение SQL_ASYNC_ENABLE_ON перед вызовом функции **bcp_exec**. Для проверки завершения копирования необходимо вызвать функцию **bcp_exec** с такими же параметрами. Если массовое копирование еще не завершено, функция **bcp_exec** возвращает значение SUCCEED_ASYNC. Она также возвращает в параметре *pnRowsProcessed* состояние счетчика числа строк, которые были отправлены серверу. Строки, отправленные на сервер, не фиксируются до тех пор, пока не будет достигнут конец пакета.  
  
 Сведения о важных изменениях в массовом копировании, начиная с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], см. в разделе [выполнение операций массового копирования &#40;ODBC&#41;](../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md).  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует использование функции **bcp_exec**:  
  
```  
// Variables like henv not specified.  
HDBC      hdbc;  
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
if (bcp_init(hdbc, _T("pubs..authors"), _T("authors.sav"), NULL, DB_OUT)  
   == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Now, execute the bulk copy.   
if (bcp_exec(hdbc, &nRowsProcessed) == FAIL)  
   {  
   if (nRowsProcessed == -1)  
      {  
      printf_s("No rows processed on bulk copy execution.\n");  
      }  
   else  
      {  
      printf_s("Incomplete bulk copy.   Only %ld row%s copied.\n",  
         nRowsProcessed, (nRowsProcessed == 1) ? "": "s");  
      }  
   return;  
   }  
  
printf_s("%ld rows processed.\n", nRowsProcessed);  
  
// Carry on.  
```  
  
## <a name="see-also"></a>См. также  
 [Функции массового копирования](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
