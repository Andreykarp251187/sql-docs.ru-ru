---
title: Уровни соответствия SQL (драйвер ODBC для Oracle) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- conformance levels [ODBC], SQL
- SQL conformance levels [ODBC]
- ODBC driver for Oracle [ODBC], conformance levels
ms.assetid: 077a6c6a-2c57-42c9-a4fd-4cf0e65cf7e2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c0bf63b831dace7678f5d3fdf952a9d6d5f60aa6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63313391"
---
# <a name="sql-conformance-levels-odbc-driver-for-oracle"></a>Уровень соответствия SQL (драйвер ODBC для Oracle)
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемого корпорацией Oracle.  
  
 Драйвер ODBC для Oracle поддерживает минимальную SQL-грамматику и базовую SQL-грамматику и также поддерживает следующие расширения ODBC SQL:  
  
-   Date, time и timestamp данных  
  
-   Слева и правые внешние соединения  
  
-   Числовые функции:  
  
    |||||  
    |-|-|-|-|  
    |Abs|Журнал|round|tan|  
    |верхний предел|LOG10|second|truncate|  
    |Cos|Mod|вход||  
    |Exp|PI|sin||  
    |функция FLOOR|Power|SQRT||  
  
-   Функции даты:  
  
    |||||  
    |-|-|-|-|  
    |Функция Curdate|DayOfWeek|MonthName|second|  
    |Функция Curtime|День года|minute|week|  
    |Функция Dayname|Час|Теперь|year|  
    |День месяца|Месяц|Квартал||  
  
-   Строковые функции:  
  
    |||||  
    |-|-|-|-|  
    |ASCII|Слева|Правильно|UCase|  
    |CHAR|Длина|RTRIM||  
    |Concat|Ltrim|SOUNDEX||  
    |Lcase|Заменить|substring||  
  
-   Функция преобразования типа:  
  
    ||  
    |-|  
    |Преобразовать|  
  
-   Системные функции:  
  
    ||  
    |-|  
    |Ifnull|  
    |Пользовательская|
