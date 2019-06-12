---
title: С помощью инструкции SQL с параметрами | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 3202b88f-ce13-44dd-982c-c6a3b0260378
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 2c2647b4737268a1550bd9e45deb9557ecc0f81d
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66790128"
---
# <a name="using-an-sql-statement-with-parameters"></a>Использование инструкции SQL с параметрами

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Для работы с данными в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с использованием инструкции SQL, содержащей параметры IN, можно воспользоваться методом [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverpreparedstatement.md) класса [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) для возврата результирующего набора [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md), который будет содержать запрошенные данные. Для этого сначала нужно создать объект SQLServerPreparedStatement с помощью метода [prepareStatement](../../connect/jdbc/reference/preparestatement-method-sqlserverconnection.md) класса [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md).

При создании инструкции SQL параметры IN определяются с использованием «?» (вопросительного знака), действующего как заполнитель для значений параметров, которые позже будут переданы в инструкцию SQL. Чтобы задать значение для параметра, можно использовать один из методов задания класса SQLServerPreparedStatement. Используемый метод задания определяется типом данных того значения, которое надо передать в инструкцию SQL.

Во время передачи значения методу задания следует указать не только фактическое значение, которое будет использоваться в инструкции SQL, но также порядковый номер параметра в инструкции SQL. Например, если инструкция SQL содержит единственный параметр, его порядковый номер будет 1. Если инструкция содержит два параметра, порядковый номер первого значения будет 1, а второго — 2.

В приведенном ниже примере открытое соединение с образцом базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] передается в функцию, создается и запускается подготовленная инструкция SQL с единственным значением параметра типа String, а затем результаты считываются из результирующего набора.

[!code[JDBC#UsingSQLWithParams1](../../connect/jdbc/codesnippet/Java/using-an-sql-statement-w_1_1.java)]

## <a name="see-also"></a>См. также:

[Использование инструкций в SQL](../../connect/jdbc/using-statements-with-sql.md)
