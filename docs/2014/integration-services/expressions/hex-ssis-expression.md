---
title: HEX (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- hexadecimal data
- HEX function
ms.assetid: f5d471ee-aeef-421c-b6e1-55b9676c3842
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6605fb7e0aadcd3ada4e48f3d4e78f7a808bcc46
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85428521"
---
# <a name="hex-ssis-expression"></a>HEX (выражение служб SSIS)
  Возвращает строку, представляющую собой шестнадцатеричное значение целого числа.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HEX(integer_expression)  
```  
  
## <a name="arguments"></a>Аргументы  
 *integer_expression*  
 Целое со знаком или беззнаковое целое.  
  
## <a name="result-types"></a>Типы результата  
 DT_WSTR  
  
## <a name="remarks"></a>Remarks  
 HEX возвращает значение null, если *integer_expression* имеет значение NULL.  
  
 Аргумент *integer_expression* должен выдавать целое число. Дополнительные сведения см. в разделе [Integration Services Data Types](../data-flow/integration-services-data-types.md).  
  
 Возвращаемый результат не включает квалификаторы, например префикс 0х. Для включения префикса используйте оператор + (сцепление). Дополнительные сведения см. в разделе [+ (Объединение) (выражение SSIS)](concatenate-ssis-expression.md).  
  
 Буквы A–F, используемые в шестнадцатеричной нотации, записываются в верхнем регистре.  
  
 Длина возвращаемой строки для целых типов данных:  
  
-   DT_I1 и DT_UI1 возвращают строку не более 2 символов.  
  
-   DT_I2 и DT_UI2 возвращают строку не более 4 символов.  
  
-   DT_I4 и DT_UI4 возвращают строку не более 8 символов.  
  
-   DT_I8 и DT_UI8 возвращают строку длиной не более 16 символов.  
  
## <a name="expression-examples"></a>Примеры выражений  
 В этом примере используется числовой литерал. Функция возвращает значение 190.  
  
```  
HEX(400)   
```  
  
 Этот пример использует столбец **ReorderPoint** . Тип данных этого столбца — `smallint`. Если значение **ReorderPoint** равно 750, функция возвращает 2EE.  
  
```  
HEX(ReorderPoint)   
```  
  
 Этот пример использует системную переменную **LocaleID**. Если значение **LocaleID** равно 1049, функция возвращает 419.  
  
```  
HEX(@LocaleID)  
```  
  
## <a name="see-also"></a>См. также:  
 [Функции (выражение служб SSIS)](functions-ssis-expression.md)  
  
  
