---
title: Divide (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- / (divide)
- divide operator (/)
ms.assetid: 5bde9223-872d-443e-8a27-57735e1d8f3d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7341a6dad3633b95882ba1b06e5f27e8c7af50db
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "71289919"
---
# <a name="divide-ssis-expression"></a>Деление (выражение служб SSIS)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Делит первое числовое выражение на второе.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dividend / divisor  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *dividend*  
 Делимое числовое выражение. *dividend* может быть любым допустимым числовым выражением. Дополнительные сведения см. в разделе [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
 *divisor*  
 Числовое выражение, на которое делится делимое. *divisor* может быть любым допустимым числовым выражением, отличным от нуля.  
  
## <a name="result-types"></a>Типы результата  
 Определяются типами данных обоих аргументов. Дополнительные сведения см. в разделе [Integration Services Data Types in Expressions](../../integration-services/expressions/integration-services-data-types-in-expressions.md).  
  
## <a name="remarks"></a>Remarks  
 Если один из операндов равен NULL, то результатом является значение NULL.  
  
 Деление на ноль недопустимо. В зависимости от того, как вычисляется подвыражение *divisor* , возникает одна из следующих ошибок:  
  
-   Если подвыражение *divisor* , результатом которого является ноль, является константой, то ошибка появляется во время разработки, и в результате файл не проходит проверку правильности.  
  
-   Если подвыражение *divisor* , результатом которого является ноль, содержит переменные, но не содержит входных столбцов, то компонент, которому принадлежит выражение, прерывает предварительную проверку правильности, которая производится перед выполнением пакета.  
  
-   Если вложенное выражение *divisor* , результатом которого является ноль, содержит входные столбцы, то во время выполнения возникает ошибка, которая обрабатывается в соответствии с правилами потока ошибок компонента потока данных.  
  
## <a name="expression-examples"></a>Примеры выражений  
 Этот пример делит два числовых литерала.  
  
```  
25 / 5  
```  
  
 Этот пример делит значения в столбце **ListPrice** на значения в столбце **StandardCost** .  
  
```  
ListPrice / StandardCost  
```  
  
## <a name="see-also"></a>См. также:  
 [Очередность и ассоциативность операторов](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Операторы (выражение служб SSIS)](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
