---
title: Выполнение пакетов | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- batches [ODBC], executing
- SQL statements [ODBC], batches
ms.assetid: f082c717-4f82-4820-a2fa-ba607d8fd872
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 53e1afcc780ff06d1d453f94deac984163099444
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63248283"
---
# <a name="executing-batches"></a>Выполнение пакетов
Прежде чем приложение выполняет пакет инструкций, оно сначала должно проверить ли они поддерживаются. Для этого, приложение вызывает **SQLGetInfo** с параметрами SQL_BATCH_SUPPORT SQL_PARAM_ARRAY_ROW_COUNTS и SQL_PARAM_ARRAY_SELECTS. Возвращает первый вариант ли создание число строк и результат формирования набора инструкций поддерживаются в явной пакеты и процедуры, при разбираться два последних варианта задает возвращают сведения о доступности, количество строк и результат в параметризованные выполнение.  
  
 Пакеты инструкций выполняются через **SQLExecute** или **SQLExecDirect**. Например следующий вызов выполняет явное пакет инструкций, чтобы открыть новый заказ на продажу.  
  
```  
SQLCHAR *BatchStmt =  
   "INSERT INTO Orders (OrderID, CustID, OpenDate, SalesPerson, Status)"  
      "VALUES (2002, 1001, {fn CURDATE()}, 'Garcia', 'OPEN');"  
   "INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (2002, 1, 1234, 10);"  
   "INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (2002, 2, 987, 8);"  
   "INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (2002, 3, 566, 17);"  
   "INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (2002, 4, 412, 500)";  
  
SQLExecDirect(hstmt, BatchStmt, SQL_NTS);  
```  
  
 Когда пакет создания результат выполнения инструкций, он возвращает одно или больше количества строк или результат задает. Сведения о том, как получить информацию, см. в разделе [несколько результатов](../../../odbc/reference/develop-app/multiple-results.md).  
  
 Если пакет инструкций содержит маркеры параметров, они нумеруются по возрастанию параметра, как и в любой другой инструкции. Например следующий пакет инструкций имеет параметры, которые нумеруются от 1 до 21; в первой **вставить** инструкции — нумерованных 1 по 5 и других пользователей за последние **вставить** инструкции являются нумерованных 18 до 21.  
  
```  
INSERT INTO Orders (OrderID, CustID, OpenDate, SalesPerson, Status)  
   VALUES (?, ?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
```  
  
 Дополнительные сведения о параметрах см. в разделе [параметров инструкции](../../../odbc/reference/develop-app/statement-parameters.md)далее в этом разделе.
