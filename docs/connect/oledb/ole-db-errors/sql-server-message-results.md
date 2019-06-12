---
title: Результаты сообщения SQL Server | Документация Майкрософт
description: результаты сообщения SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, errors
- errors [OLE DB], SQL Server message results
- OLE DB error handling, SQL Server message results
author: pmasl
ms.author: pelopes
manager: jroth
ms.openlocfilehash: 9098994ac5349fa9747c952e66eb902231956a5c
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66802852"
---
# <a name="sql-server-message-results"></a>Результаты сообщения SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Следующие инструкции [!INCLUDE[tsql](../../../includes/tsql-md.md)] не создают при работе наборы строк поставщика драйвера OLE DB для SQL Server и не возвращают количество обработанных строк:  
  
-   PRINT  
  
-   RAISERROR (со степенью серьезности 10 или ниже)  
  
-   DBCC  
  
-   SET SHOWPLAN  
  
-   SET STATISTICS  
  
 Эти инструкции либо возвращают одно или несколько информационных сообщений, либо дают указание [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] вернуть информационные сообщения вместо набора строк или результатов вычислений. При успешном выполнении возвращает S_OK, драйвер OLE DB для SQL Server, и сообщения доступны для драйвера OLE DB для SQL Server потребителя.  
  
 Драйвер OLE DB для SQL Server, возвращается значение s_ок и имеет один или несколько информационных сообщений, появляющихся после выполнения многих [!INCLUDE[tsql](../../../includes/tsql-md.md)] инструкций или при выполнении потребителем драйвера OLE DB для SQL Server функции-члена.  
  
 Потребитель драйвера OLE DB для SQL Server, разрешающий динамическую спецификацию текста запроса, должен проверять интерфейсы ошибок после каждого выполнения функции-члена независимо от значения кода возврата, наличия или отсутствия возвращенной ссылки на интерфейс **IRowset** или **IMultipleResults** или количества обработанных строк.  
  
## <a name="see-also"></a>См. также:  
 [ошибки](../../oledb/ole-db-errors/errors.md)  
  
  
