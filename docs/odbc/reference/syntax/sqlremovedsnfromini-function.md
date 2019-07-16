---
title: Функция SQLRemoveDSNFromIni | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLRemoveDSNFromIni
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLRemoveDSNFromIni
helpviewer_keywords:
- SQLRemoveDSNFromIni function [ODBC]
ms.assetid: bb2e8273-7b61-4113-bfc8-f7ccc607c811
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4cc83a8cafffc9b5d1166df76d91ce4c63f0b858
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68024528"
---
# <a name="sqlremovedsnfromini-function"></a>Функция SQLRemoveDSNFromIni
**Соответствие стандартам**  
 Представленные версии: ODBC 1.0  
  
 **Сводка**  
 **SQLRemoveDSNFromIni** удаляет источник данных из информации о системе.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
BOOL SQLRemoveDSNFromIni(  
     LPCSTR   lpszDSN);  
```  
  
## <a name="arguments"></a>Аргументы  
 *lpszDSN*  
 [Вход] Имя источника данных для удаления.  
  
## <a name="returns"></a>Возвращает  
 Функция возвращает значение TRUE, если он удаляет источник данных или источник данных не в файле Odbc.ini. Возвращается значение FALSE, если не удается удалить источник данных.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLRemoveDSNFromIni** возвращает значение FALSE, связанным  *\*pfErrorCode* значение можно получить, вызвав **SQLInstallerError**. В следующей таблице перечислены *\*pfErrorCode* значения, которые могут быть возвращены **SQLInstallerError** и объясняется каждый из них в контексте этой функции.  
  
|*\*pfErrorCode*|Ошибка|Описание|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Ошибки общие установщика|Произошла ошибка для которой нет ошибок определенных установщика.|  
|ODBC_ERROR_INVALID_DSN|Недопустимое имя источника данных|*LpszDSN* предоставил недопустимый аргумент.|  
|ODBC_ERROR_REQUEST_FAILED|Не удалось выполнить запрос|Программа установки не удалось удалить сведения источника данных из реестра.|  
|ODBC_ERROR_OUT_OF_MEM|Недостаточно памяти|Программа установки не удалось выполнить функцию из-за нехватки памяти.|  
  
## <a name="comments"></a>Комментарии  
 **SQLRemoveDSNFromIni** удаляет имя источника данных в разделе [источники данных ODBC], информация о системе. Он также удаляет из сведения о системном разделе спецификации источника данных.  
  
 Эта функция должна вызываться только из библиотеки установки драйвера.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Добавление, изменение или удаление источника данных|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)|  
|Добавление, изменение или удаление источника данных|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|Удаление источника данных по умолчанию|[SQLRemoveDefaultDataSource](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)|  
|Добавление имени источника данных в сведения о системе|[SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|
