---
title: '* (Умножение) (выражение служб SSIS) | Документы Майкрософт'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- '* (multiply operator)'
- multiply operator (*)
ms.assetid: d457f052-ffbb-4485-833f-f4bed4349b69
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bc5c349835acb6211fb3d46c0bad37d377760063
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2019
ms.locfileid: "71288833"
---
# <a name="-multiply-ssis-expression"></a>* (умножение) (выражение служб SSIS)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Умножает два числовых выражения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
numeric_expression1 * numeric_expression2  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *numeric_expression1, numeric_expression2*  
 Любое допустимое выражение числовых типов данных. Дополнительные сведения см. в разделе [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Типы результата  
 Определяются типами данных обоих аргументов. Дополнительные сведения см. в разделе [Integration Services Data Types in Expressions](../../integration-services/expressions/integration-services-data-types-in-expressions.md).  
  
## <a name="remarks"></a>Remarks  
 Если один из операндов равен NULL, то результатом является значение NULL.  
  
## <a name="expression-examples"></a>Примеры выражений  
 Этот пример умножает числовые литералы.  
  
```  
5 * 6.09  
```  
  
 Этот пример увеличивает значения столбца **ListPrice** на 10 процентов.  
  
```  
ListPrice * .10  
```  
  
 Этот пример вычитает результат выражения из столбца **ListPrice** . Переменная **Discount%** должна быть заключена в квадратные скобки, поскольку имя включает символ %. Дополнительные сведения см. в разделе [Идентификаторы (службы SSIS)](../../integration-services/expressions/identifiers-ssis.md).  
  
```  
ListPrice - (ListPrice * @[Discount%])  
```  
  
## <a name="see-also"></a>См. также:  
 [Очередность и ассоциативность операторов](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Операторы (выражение служб SSIS)](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
