---
title: LOG (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- base-10 logarithms
- LOG function
ms.assetid: f7fccace-c178-4e13-bde9-7dc4ef1d98fa
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: fde9e5cdaea245fd0b99820a89a4466e2d669fdf
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62769070"
---
# <a name="log-ssis-expression"></a>LOG (выражение служб SSIS)
  Возвращает десятичный логарифм числового выражения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
LOG(numeric_expression)  
```  
  
## <a name="arguments"></a>Аргументы  
 *numeric_expression*  
 Допустимое ненулевое и неотрицательное числовое выражение.  
  
## <a name="result-types"></a>Типы результата  
 DT_R8  
  
## <a name="remarks"></a>Remarks  
 Перед вычислением логарифма аргумент *numeric_expression* приводится к типу DT_R8. Дополнительные сведения см. в разделе [Integration Services Data Types](../data-flow/integration-services-data-types.md).  
  
 Если вычисленное значение *numeric_expression* является нулем или отрицательным значением, возвращается результат NULL.  
  
## <a name="expression-examples"></a>Примеры выражений  
 В этом примере используется числовой литерал. Функция возвращает значение 1,988291341907488.  
  
```  
LOG(97.34)  
```  
  
 Этот пример использует столбец **Length**. Если значением столбца является 101,24, функция возвращает 2,005352136486217.  
  
```  
LOG(Length)   
```  
  
 Этот пример использует переменную **Length**. Тип данных переменной должен быть numeric либо выражение должно включать явное приведение к типу данных [!INCLUDE[ssIS](../../includes/ssis-md.md)] numeric. При параметре **Length** равном 234,567 функция возвращает 2,370266913465859.  
  
```  
LOG(@Length)   
```  
  
## <a name="see-also"></a>См. также:  
 [EXP (выражение служб SSIS)](exp-ssis-expression.md)   
 [LN (выражение служб SSIS)](ln-ssis-expression.md)   
 [Функции (выражение служб SSIS)](functions-ssis-expression.md)  
  
  
