---
title: ~ (битовое НЕ) (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- bitwise NOT (~)
- ~ (bitwise NOT)
ms.assetid: e4413ddd-0d0e-40c3-9c76-b5ce323218ec
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 4c07444ff1dd425671fbc17176fc3aa94e0705bd
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/16/2019
ms.locfileid: "65725600"
---
# <a name="-bitwise-not-ssis-expression"></a>~ (битовое НЕ) (выражение служб SSIS)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Выполняет битовую инверсию целого числа. Этот оператор может быть применен к целочисленному типу данных со знаком или без знака.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
~integer_expression  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *integer_expression*  
 Любое допустимое выражение целочисленного типа данных. *integer*_*expression* — целое число, которое преобразуется в двоичное число для побитовой операции. Дополнительные сведения см. в разделе [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Типы результата  
 Возвращает тип данных *integer_expression*.  
  
## <a name="remarks"></a>Remarks  
 None  
  
## <a name="expression-examples"></a>Примеры выражений  
 Этот пример выполняет операцию битового ~ (NOT) над числом 170 (0000 0000 1010 1010). Число целого типа со знаком.  
  
```  
  
~ 170  
```  
  
 Результат вычисления выражения — 170 (1111111101010101).  
  
 0000000010101010  
  
 ---------------------\-  
  
 1111111101010101  
  
## <a name="see-also"></a>См. также:  
 [Очередность и ассоциативность операторов](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Операторы (выражение служб SSIS)](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
