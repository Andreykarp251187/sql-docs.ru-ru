---
description: Подготовленное выполнение
title: Подготовленное выполнение | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- deferred statement preparation
- prepared execution [ODBC]
- SQLPrepare function
- ODBC applications, statements
- SQLExecute function
- statements [ODBC], prepared execution
ms.assetid: f3a9d32b-6cd7-4f0c-b38d-c8ccc4ee40c3
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 721b2377f5539a4ee047816da6e5ecb5bc2fe213
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88486787"
---
# <a name="prepared-execution"></a>Подготовленное выполнение
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  API-интерфейс ODBC определяет подготовленное выполнение как способ уменьшить расходы на синтаксический анализ и компиляцию, связанные с повторным выполнением инструкции [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Приложение строит строку символов, содержащую инструкцию SQL, а затем выполняет ее в два этапа. Он вызывает [функцию SQLPrepare](https://go.microsoft.com/fwlink/?LinkId=59360) один раз, чтобы инструкция была проанализирована и скомпилирована в план выполнения с помощью [!INCLUDE[ssDE](../../../includes/ssde-md.md)] . Затем он вызывает **SQLExecute** для каждого выполнения подготовленного плана выполнения. Это снижает расход ресурсов на синтаксический анализ и компиляцию при каждом выполнении. Подготовленное выполнение часто используется приложениями для многократного выполнения параметризованных инструкций SQL.  
  
 В большинстве баз данных подготовленное выполнение инструкций, которые выполняются более трех или четырех раз, быстрее, чем прямое выполнение, в первую очередь потому, что инструкция компилируется только один раз, в то время как инструкции, выполняемые прямо, компилируются при каждом выполнении. Подготовленное выполнение может также снизить объем сетевого трафика, поскольку драйвер при каждом выполнении инструкции может передавать источнику данных идентификатор плана выполнения и значения параметров, а не целую инструкцию SQL.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] сокращается разница в производительности между прямым и подготовленным выполнением с помощью улучшенных алгоритмов для обнаружения и повторного использования планов выполнения из **SQLExecDirect**. В результате некоторые преимущества производительности выполнения подготовленных инструкций распространяются на прямое выполнение инструкций. Дополнительные сведения см. в разделе [прямое выполнение](../../../relational-databases/native-client-odbc-queries/executing-statements/direct-execution.md).  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] также обеспечивает собственную поддержку подготовленного выполнения. План выполнения строится на основе **SQLPrepare** и более поздних версий при вызове **SQLExecute** . Поскольку [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не требуется создавать временные хранимые процедуры в **SQLPrepare**, дополнительные издержки на системные таблицы в **базе данных tempdb**отсутствуют.  
  
 По соображениям производительности подготовка инструкции откладывается до вызова **SQLExecute** или операции метасвойства (например, [SQLDescribeCol](../../../relational-databases/native-client-odbc-api/sqldescribecol.md) или [SQLDescribeParam](../../../relational-databases/native-client-odbc-api/sqldescribeparam.md) в ODBC). Это поведение по умолчанию. Любые ошибки в подготавливаемой инструкции неизвестны до выполнения инструкции или до выполнения операции над метасвойством. Установив атрибут инструкции SQL_SOPT_SS_DEFER_PREPARE в специфичное для ODBC-драйвера собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] значение SQL_DP_OFF, можно отключить это поведение по умолчанию.  
  
 В случае отложенной подготовки вызов метода **SQLDescribeCol** или **SQLDescribeParam** перед вызовом **SQLExecute** создает дополнительный обмен данными с сервером. В **SQLDescribeCol**драйвер УДАЛЯЕТ предложение WHERE из запроса и отправляет его на сервер с параметром SET FMTONLY ON для получения описания столбцов в первом результирующем наборе, возвращенном запросом. В **SQLDescribeParam**драйвер вызывает сервер, чтобы получить описание выражений или столбцов, на которые ссылаются маркеры параметров в запросе. Этот метод также имеет несколько ограничений, таких как невозможность обработки параметров вложенных запросов.  
  
 Чрезмерное использование **SQLPrepare** с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвером ODBC для собственного клиента снижает производительность, особенно при подключении к более ранним версиям SQL Server. Не следует использовать подготовленное выполнение для инструкций, исполняемых один раз. Подготовленное выполнение медленнее, чем прямое выполнение, для однократного выполнения инструкции, потому что оно требует дополнительного обращения клиента к серверу. В предыдущих версиях [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] оно также создает временную хранимую процедуру.  
  
 В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] подготовленные инструкции нельзя применять для создания временных объектов.  
  
 Некоторые ранние приложения ODBC использовались **SQLPrepare** в любое время [SQLBindParameter](../../../relational-databases/native-client-odbc-api/sqlbindparameter.md) . **SQLBindParameter** не требует использования **SQLPrepare**, его можно использовать с **SQLExecDirect**. Например, используйте **SQLExecDirect** с **SQLBindParameter** для получения кода возврата или выходных параметров из хранимой процедуры, которая выполняется только один раз. Не используйте **SQLPrepare** с **SQLBindParameter** , если одна и та же инструкция не будет выполняться несколько раз.  
  
## <a name="see-also"></a>См. также:  
 [Исполнение инструкций &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-queries/executing-statements/executing-statements-odbc.md)  
  
  
