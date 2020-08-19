---
description: LOG (выражение служб SSIS)
title: LOG (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- base-10 logarithms
- LOG function
ms.assetid: f7fccace-c178-4e13-bde9-7dc4ef1d98fa
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 211797a6291145b7f1499f23c03f255f504eaf9b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88425456"
---
# <a name="log-ssis-expression"></a>LOG (выражение служб SSIS)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


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
  
## <a name="remarks"></a>Комментарии  
 Перед вычислением логарифма аргумент *numeric_expression* приводится к типу DT_R8. Дополнительные сведения см. в разделе [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
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
  
## <a name="see-also"></a>См. также  
 [EXP (выражение служб SSIS)](../../integration-services/expressions/exp-ssis-expression.md)   
 [LN (выражение служб SSIS)](../../integration-services/expressions/ln-ssis-expression.md)   
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
