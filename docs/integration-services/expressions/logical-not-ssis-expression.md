---
title: '! (логическое НЕ) (выражение служб SSIS) | Документы Майкрософт'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- logical Not (!)
- '! (logical Not)'
ms.assetid: d5c4d1e1-7be4-4d25-bcd9-5b6ddb53b3b3
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: ca8a649e1e60ffd44047377ed1b8eaaaba0569aa
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/16/2019
ms.locfileid: "65725202"
---
# <a name="-logical-not-ssis-expression"></a>! (логическое НЕ) (выражение служб SSIS)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Инвертирует логический операнд.  
  
> [!NOTE]  
>  ! Оператор «!» не может использоваться вместе с другими операторами. Например, нельзя объединить оператор «!» и оператор > в один оператор «!>» .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
!boolean_expression  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *boolean_expression*  
 Является любое допустимое выражение, результатом которого является логическое значение. Дополнительные сведения см. в разделе [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Типы результата  
 DT_BOOL  
  
## <a name="remarks"></a>Remarks  
 Следующая таблица демонстрирует результаты выполнения «!» операции.  
  
|Исходное логическое выражение|После выполнения оператора «!» оператор|  
|---------------------------------|------------------------------------|  
|TRUE|FALSE|  
|NULL|NULL|  
|FALSE|TRUE|  
  
## <a name="expression-examples"></a>Примеры выражений  
 В результате выполнения данного выражения получается значение FALSE, если столбец **Color** имеет значение "red".  
  
```  
!(Color == "red")  
```  
  
 В результате выполнения данного выражения получается значение TRUE, если значение переменной **MonthNumber** совпадает со значением переменной, представляющей номер текущего месяца. Дополнительные сведения см. в разделе [MONTH (выражение служб SSIS)](../../integration-services/expressions/month-ssis-expression.md) and [GETDATE (выражение служб SSIS)](../../integration-services/expressions/getdate-ssis-expression.md).  
  
```  
!(@MonthNumber != MONTH(GETDATE())  
```  
  
## <a name="see-also"></a>См. также:  
 [Очередность и ассоциативность операторов](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Операторы (выражение служб SSIS)](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
