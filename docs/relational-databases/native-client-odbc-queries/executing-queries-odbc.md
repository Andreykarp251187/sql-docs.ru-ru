---
title: Выполнение запросов (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC applications, executing queries
- SQL Server Native Client ODBC driver, statements
- ODBC applications, statements
- SQL Server Native Client ODBC driver, queries
- queries [ODBC]
ms.assetid: d935bcba-8ce6-4159-8395-6c86431602ad
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: cb9caaa95c24a9d442f53f6ed78eda12eec667c1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67937286"
---
# <a name="executing-queries-odbc"></a>Выполнение запросов (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  После того, как приложение ODBC инициализирует дескриптор соединения и подключается к источнику данных, оно выделяет один или несколько дескрипторов инструкций на дескриптор соединения. Приложение может затем выполнить [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] инструкций с дескриптором инструкции. Общая последовательность событий при выполнении инструкции SQL.  
  
1.  Установите необходимые атрибуты инструкции.  
  
2.  Сформируйте инструкцию.  
  
3.  Выполните инструкцию.  
  
4.  Получите результирующие наборы.  
  
 После того, как приложение получит все строки во всех результирующих наборах, возвращенных инструкцией SQL, оно может выполнить другой запрос на том же дескрипторе инструкции. Если приложение определяет, что он не требуется извлекать все строки в некотором результирующем наборе, его можно отменить остаток результирующего набора с помощью вызова [SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md) или [SQLCloseCursor](../../relational-databases/native-client-odbc-api/sqlclosecursor.md).  
  
 Если в приложении ODBC необходимо несколько раз выполнить одну инструкцию SQL с различными данными, используйте маркер параметра, обозначенный вопросительным знаком (?) при построении инструкции SQL:  
  
```  
INSERT INTO MyTable VALUES (?, ?, ?)  
```  
  
 Каждый маркер параметра затем подключаются к программной переменной путем вызова [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md).  
  
 После того, как будут вызваны все инструкции SQL и обработаны их результирующие наборы, приложение освобождает дескриптор инструкции.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC для собственного клиента поддерживает несколько дескрипторов инструкций на один дескриптор соединения. Управление транзакциями осуществляется на уровне соединения, поэтому вся работа, выполняемая со всеми дескрипторами инструкций на одном дескрипторе соединения, управляется как часть одной транзакции.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Выделение дескриптора инструкции](../../relational-databases/native-client-odbc-queries/allocating-a-statement-handle.md)  
  
-   [Конструирование инструкций SQL &#40;ODBC&#41;](../../relational-databases/native-client-odbc-queries/constructing-an-sql-statement-odbc.md)  
  
-   [Конструирование инструкций SQL для курсоров](../../relational-databases/native-client-odbc-queries/constructing-sql-statements-for-cursors.md)  
  
-   [Использование параметров инструкции](../../relational-databases/native-client-odbc-queries/using-statement-parameters.md)  
  
-   [Выполнение инструкций &#40;ODBC&#41;](../../relational-databases/native-client-odbc-queries/executing-statements/executing-statements-odbc.md)  
  
-   [Освобождение дескриптора инструкции](../../relational-databases/native-client-odbc-queries/freeing-a-statement-handle.md)  
  
## <a name="see-also"></a>См. также  
 [SQL Server Native Client (ODBC)](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
