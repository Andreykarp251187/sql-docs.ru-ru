---
title: Повторяющийся функции | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- duplicated functions [ODBC]
- compatibility [ODBC], duplicated functions
- ODBC drivers [ODBC], backward compatibility
- functions [ODBC], duplicated functions
- backward compatibility [ODBC], duplicated functions
ms.assetid: 641b16bc-f791-46d8-b093-31736473fe3d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ca73b5b9b41c99bd6db8e6181fa3582cae47c1d1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68046902"
---
# <a name="duplicated-features"></a>Повторяющиеся функции
Следующие ODBC *2.x* дублирования функций в ODBC *3.x* функции. В результате ODBC *2.x* функции являются устаревшими в ODBC *3.x*. ODBC *3.x* функции называются замещающих функций.  
  
 Если приложение использует устаревшие ODBC *2.x* функции и базового драйвера — ODBC *3.x* драйвера, диспетчер драйверов сопоставляет вызов функции соответствующую функцию замены. Единственное исключение для этого правила — **SQLExtendedFetch**. (См. в разделе сноска в конце следующей таблице.) Дополнительные сведения об этих сопоставлениях см. в разделе [сопоставление устаревшей функции](../../../odbc/reference/appendixes/mapping-deprecated-functions.md) в приложении G: Рекомендации по драйверов для обеспечения обратной совместимости.  
  
 Когда приложение использует функцию замены и базового драйвера ODBC *2.x* драйвера, диспетчер драйверов сопоставляет вызов функции соответствующая функция не рекомендуется.  
  
|ODBC *2.x* функции|ODBC *3.x* функции|  
|-------------------------|-------------------------|  
|**SQLAllocConnect**|**SQLAllocHandle**|  
|**SQLAllocEnv**|**SQLAllocHandle**|  
|**SQLAllocStmt**|**SQLAllocHandle**|  
|**SQLColAttributes**|**SQLColAttribute**|  
|**SQLError**|**SQLGetDiagRec**|  
|**SQLExtendedFetch**[1]|**SQLFetchScroll**|  
|**SQLFreeConnect**|**SQLFreeHandle**|  
|**SQLFreeEnv**|**SQLFreeHandle**|  
|**SQLGetConnectOption**|**SQLGetConnectAttr**|  
|**SQLGetStmtOption**|**SQLGetStmtAttr**|  
|**SQLParamOptions**|**SQLSetStmtAttr**, **SQLGetStmtAttr**|  
|**SQLSetConnectOption**|**SQLSetConnectAttr**|  
|**SQLSetParam**|**SQLBindParameter**|  
|**SQLSetStmtOption**|**SQLSetStmtAttr**|  
|**SQLTransact**|**SQLEndTran**|  
  
 [1] функция **SQLExtendedFetch** является продублированные функции; **SQLFetchScroll** предоставляет те же функциональные возможности в ODBC *3.x*. Тем не менее, диспетчер драйверов не соответствует **SQLExtendedFetch** для **SQLFetchScroll** при переходе от ODBC *3.x* драйвера. Дополнительные сведения см. в разделе [the Driver Manager назначение](../../../odbc/reference/appendixes/what-the-driver-manager-does.md) в приложении G: Рекомендации по драйверов для обеспечения обратной совместимости. Сопоставляет диспетчера драйверов **SQLFetchScroll** для **SQLExtendedFetch** при переходе от ODBC *2.x* драйвера.  
  
> [!NOTE]
>  Функция **SQLBindParam** является особым случаем. **SQLBindParam** является продублированные функции. Это не ODBC *2.x* функция, но функция, которая присутствует в стандартах Open Group и ISO. Функциональные возможности, предоставляемые этой функцией полностью включена в группу по **SQLBindParameter**. Таким образом, диспетчер драйверов сопоставляет вызов **SQLBindParam** для **SQLBindParameter** при базового драйвера ODBC *3.x* драйвера. Однако в том случае, если базового драйвера равно ODBC *2.x* драйвера, диспетчер драйверов не выполняет это сопоставление.
