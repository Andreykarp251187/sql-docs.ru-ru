---
title: Копирование дескрипторов | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], copying
- copying descriptors [ODBC]
ms.assetid: 949a860d-6579-4218-882e-8c061688dd87
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7d41cd744d39113c556c4ee8bc17411b7992e596
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68002141"
---
# <a name="copying-descriptors"></a>Копирование дескрипторов
**SQLCopyDesc** функция вызывается для копирования поля один дескриптор другим дескриптором. Поля могут быть скопированы только дескриптор приложений или IPD, но не IRD. Поля можно скопировать из любого типа дескриптора. Копируются только поля, которые определены для исходной и целевой дескрипторов. **SQLCopyDesc** не копирует поле SQL_DESC_ALLOC_TYPE, поскольку невозможно изменить тип выделения дескриптора. Скопированные поля перезаписывают существующие поля.  
  
 Отменить дескриптором одной инструкции можно использовать в качестве APD другим дескриптором инструкции. Это позволяет приложению нужно скопировать строки между таблицами без копирования данных на уровне приложения. Чтобы сделать это, повторно дескриптор строки, который описывает выбранной строки таблицы используется как дескриптор параметра для параметра в инструкции INSERT. Тип сведений SQL_MAX_CONCURRENT_ACTIVITIES должен быть больше 1 для выполнения данной операции.
