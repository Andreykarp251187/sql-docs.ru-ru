---
title: Число записей | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- record count [ODBC]
- descriptors [ODBC], record count
ms.assetid: 46eec3cc-0ecc-4980-9020-fb74a9af5730
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d4d684fb6d9614defdca3897c53c4bae9fc231a9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68138080"
---
# <a name="record-count"></a>Число записей
Поле заголовка дескриптора SQL_DESC_COUNT — от единицы индекс наибольший номер записи, которая содержит данные. Это поле не является количество все столбцы или параметры, которые привязаны. Если дескриптор выделен, начальное значение SQL_DESC_COUNT равно 0.  
  
 Драйвер принимает любое действие, для выделения и обслуживания в хранилище, он требуется для хранения информации о дескрипторе. Приложение явно не указать размер дескриптора не выделяют новых записей. Если приложение предоставляет сведения для записи дескриптор, номер которого выше, чем значение SQL_DESC_COUNT, драйвер автоматически увеличивается SQL_DESC_COUNT. Если приложение отменяет привязку записи новейшую дескриптора, драйвер автоматически уменьшается SQL_DESC_COUNT должен содержать число наивысший оставшиеся связанную запись.
