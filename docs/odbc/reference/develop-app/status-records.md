---
description: Записи состояния
title: Записи состояния | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], diagnostic records
- status records [ODBC]
- diagnostic records [ODBC]
ms.assetid: 4a987f69-158f-4cc4-a31b-2b7dd8dcbb87
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 96d871814ac22e52eece4d6db7fff68fa2dacd48
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88482907"
---
# <a name="status-records"></a>Записи состояния
Поля в записях состояния содержат сведения об отдельных ошибках или предупреждениях, возвращаемых диспетчером драйверов, драйвером или источником данных, включая SQLSTATE, номер собственной ошибки, диагностическое сообщение, номер столбца и номер строки. Записи состояния могут создаваться только в том случае, если функция возвращает SQL_ERROR, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_NEED_DATA или SQL_STILL_EXECUTING. Полный список полей в записях состояния см. в описании функции [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md) .  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Последовательность записей состояния](../../../odbc/reference/develop-app/sequence-of-status-records.md)  
  
-   [атрибуты SQLSTATE](../../../odbc/reference/develop-app/sqlstates.md)  
  
-   [Диагностические сообщения](../../../odbc/reference/develop-app/diagnostic-messages.md)
