---
title: '!= (не равно) (выражение служб SSIS) | Документы Майкрософт'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- unequal operator (!=)
- '!= (not equal to)'
ms.assetid: fad20e85-c0e6-42bf-af70-2bc80ee09be5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 67aa61e65bc89246cfb0c685d08a32371a5fc4df
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2019
ms.locfileid: "71287906"
---
# <a name="-unequal-ssis-expression"></a>!= (не равно) (выражение служб SSIS)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Осуществляет сравнение для определения того, выполняется ли условие неравенства двух выражений с совместимыми типами данных. Перед проведением сравнения средство оценки выражений автоматически преобразует большинство типов данных.  
  
 Однако для успешного выполнения выражения некоторые типы данных требуют, чтобы выражение включало в себя явное приведение. Дополнительные сведения о допустимых приведениях типов данных см. в разделе [Приведение (выражение служб SSIS)](../../integration-services/expressions/cast-ssis-expression.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
expression1 != expression2  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression1, expression2*  
 Любое допустимое выражение.  
  
## <a name="result-types"></a>Типы результата  
 DT_BOOL  
  
## <a name="remarks"></a>Remarks  
 Если какое-нибудь выражение имеет значение NULL, то результат сравнения будет NULL. Если оба выражения имеют значение NULL, то результат будет NULL.  
  
 Наборы выражений *expression1* и *expression2*должны удовлетворять одному из следующих правил:  
  
-   **Числовой** Как *expression1* , так и *expression2* должны иметь числовой тип данных. В соответствии с правилами неявных числовых преобразований, выполняемых средством оценки выражений, пересечением типов данных должен быть целочисленный тип данных. NULL не может быть значением пересечения двух числовых типов данных. Дополнительные сведения см. в разделе [Integration Services Data Types in Expressions](../../integration-services/expressions/integration-services-data-types-in-expressions.md).  
  
-   **Символьный** . Значения выражений *expression1* и *expression2* должны иметь тип данных DT_STR или DT_WSTR. Вычисленные значения этих двух выражений могут иметь различные строковые типы данных.  
  
    > [!NOTE]  
    >  Сравнения строк производятся с учетом регистра, диакритических знаков, японской азбуки и ширины символов.  
  
-   **Дата, время или дата и время**. Значения выражений *expression1* и *expression2* должны иметь один из следующих типов данных: DT_DBDATE, DT_DATE, DT_DBTIME, DT_DBTIME2, DT_DBTIMESTAMP, DT_DBTIMESTAMP2, DT_DBTIMESTAPMOFFSET или DT_FILETIME.  
  
    > [!NOTE]  
    >  Система не поддерживает сравнения выражений, значения которых имеют тип данных даты, времени или даты-времени. Возникнет ошибка.  
  
     При сравнении выражений система применяет следующие правила преобразования (в порядке их перечисления).  
  
    -   Если значения двух выражений имеют один и тот же тип данных, выполняется сравнение для этого типа.  
  
    -   Если значение одного из выражений имеет тип данных DT_DBTIMESTAMPOFFSET, то другое будет неявно преобразовано в тип данных DT_DBTIMESTAMPOFFSET, после чего будет произведено сравнение для этого типа. Дополнительные сведения см. в разделе [Integration Services Data Types in Expressions](../../integration-services/expressions/integration-services-data-types-in-expressions.md).  
  
    -   Если значение одного из выражений имеет тип данных DT_DBTIMESTAMP2, то другое будет неявно преобразовано в тип данных DT_DBTIMESTAMP2, после чего будет произведено сравнение для этого типа.  
  
    -   Если значение одного из выражений имеет тип данных DT_DBTIME2, то другое будет неявно преобразовано в тип данных DT_DBTIME2, после чего будет произведено сравнение для этого типа.  
  
    -   Если значение одного из выражений имеет тип данных, отличный от DT_DBTIMESTAMPOFFSET, DT_DBTIMESTAMP2 или DT_DBTIME2, то перед началом сравнения значения будут преобразованы в тип данных DT_DBTIMESTAMP.  
  
     При сравнении выражений система исходит из следующих предположений.  
  
    -   Если оба выражения имеют тип данных, включающий доли секунды, то предполагается, что для типа, имеющего меньшее число разрядов, в недостающих разрядах содержатся нули.  
  
    -   Если оба выражения имеют тип даты, но смещение часового пояса присутствует только у одного из них, то предполагается, что дата без смещения выражена по Гринвичу (UTC).  
  
-   **Логический** Значения *expression1* и *expression2* должны иметь логический тип данных.  
  
-   **GUID** . Значения выражений *expression1* и *expression2* должны иметь тип данных DT_GUID.  
  
-   **Двоичный** . Значения выражений *expression1* и *expression2* должны иметь тип данных DT_BYTES.  
  
-   **Большой двоичный объект**. Значения выражений *expression1* и *expression2* должны иметь один и тот же тип данных больших двоичных объектов (BLOB): DT_TEXT, DT_NTEXT или DT_IMAGE.  
  
 Дополнительные сведения о типах данных см. в разделе [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="expression-examples"></a>Примеры выражений  
 Этот пример возвращает значение TRUE, только если текущая дата не равна 4 июля 2003 года. Дополнительные сведения см. в разделе [GETDATE (выражение служб SSIS)](../../integration-services/expressions/getdate-ssis-expression.md).  
  
```  
"7/4/2003" != GETDATE()  
```  
  
 В этом примере получится TRUE, если значение столбца **ListPrice** не равно 500.  
  
```  
ListPrice != 500  
```  
  
 В данном примере используется переменная **LPrice**. Он возвращает TRUE, если значение **LPrice** не равно 500. Чтобы выполнился синтаксический анализ выражения, тип данных этой переменной должен быть числовым.  
  
```  
@LPrice != 500  
```  
  
## <a name="see-also"></a>См. также:  
 [= = (равно) (выражение служб SSIS)](../../integration-services/expressions/equal-ssis-expression.md)   
 [Очередность и ассоциативность операторов](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Операторы (выражение служб SSIS)](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
