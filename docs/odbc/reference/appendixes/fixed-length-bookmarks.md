---
title: Закладки с фиксированной длиной | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- backward compatibility [ODBC], bookmarks
- bookmarks [ODBC]
- compatibility [ODBC], bookmarks
- fixed-length bookmarks [ODBC]
ms.assetid: cbd8185e-fb03-408f-b80b-1a2e164534fd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f90c5888a68506c056b2a56fce516080148528e7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306985"
---
# <a name="fixed-length-bookmarks"></a>Закладки фиксированной длины
Если драйвер ODBC *3. x* должен работать с приложением ODBC *2. x* , использующим закладки фиксированной длины, драйвер должен поддерживать следующее:  
  
-   SQL_UB_ON в качестве значения параметра инструкции SQL_USE_BOOKMARKS. (SQL_UB_ON не рекомендуется использовать в ODBC *3. x*.)  
  
-   Параметр инструкции SQL_GET_BOOKMARK.
