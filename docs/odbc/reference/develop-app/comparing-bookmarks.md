---
title: Сравнение закладок | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], bookmarks
- comparing bookmarks [ODBC]
- bookmarks [ODBC]
ms.assetid: ea347635-fbe3-41c1-b537-4048b7c0f7da
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 44da652ad1e52934fa48f32b1b2f88b30212ad3b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68083308"
---
# <a name="comparing-bookmarks"></a>Сравнение закладок
Поскольку закладки являются сравнимыми по байтам, их можно сравнивать на равенство или неравенство. Для этого приложение обрабатывает каждую закладку как массив байтов и сравнивает две закладки в байтах по байтам. Так как закладки гарантированно отличаются только в результирующем наборе, нет смысла сравнивать закладки, полученные из разных результирующих наборов.
