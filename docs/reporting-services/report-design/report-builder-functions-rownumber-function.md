---
title: Функция RowNumber (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 9d718ba8-d323-49fb-aac8-e7013a117b75
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: e918a674b48eeb34fad7ea660b7e907fc9dcb44b
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "65577189"
---
# <a name="report-builder-functions---rownumber-function"></a>Функции построителя отчетов — функция RowNumber
  Возвращает текущее количество строк в указанной области.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
RowNumber(scope)  
```  
  
#### <a name="parameters"></a>Параметры  
 *область*  
 (**String**) Имя набора данных, области данных, группирования или значение NULL (**Nothing** в [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]), указывающее контекст, в котором вычисляется количество строк. Значение**Nothing** указывает самый внешний контекст, обычно набор данных отчета.  
  
## <a name="remarks"></a>Remarks  
 Функция**RowNumber** возвращает текущее значение счетчика строк в указанной области подобно тому, как функция [RunningValue](../../reporting-services/report-design/report-builder-functions-runningvalue-function.md) возвращает текущее значение агрегатной функции. При указании области указывается и момент, когда счетчик строк сбрасывается в значение 1.  
  
 Значение*scope* не может быть выражением. Значение*scope* должно быть содержащей областью. Типичными областями — от самой внешней до самой внутренней — являются набор данных отчета, область данных, группы строк и столбцов.  
  
 Чтобы увеличить значения по столбцам, укажите область, являющуюся именем группы столбцов. Чтобы увеличить числа в строках, укажите область, являющуюся именем группы строк.  
  
> [!NOTE]  
>  Не поддерживается включение агрегатов, которые в одном выражении указывают и группу строк, и группу столбцов.  
  
 Дополнительные сведения см. в разделах [Справочник по агрегатным функциям (построитель отчетов и службы SSRS)](../../reporting-services/report-design/report-builder-functions-aggregate-functions-reference.md) и [Область выражения для суммирования, агрегатных функций и встроенных коллекций (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
## <a name="code-example"></a>Пример кода  
 Ниже приведено выражение, которое можно использовать в свойстве **BackgroundColor** строки сведений области данных табликса, чтобы изменять цвет строк со сведениями для каждой группы, всегда начиная с белого.  
  
```  
=IIF(RowNumber("GroupbyCategory") Mod 2, "White", "PaleGreen")  
```  
  
## <a name="see-also"></a>См. также:  
 [Использование выражений в отчетах (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Примеры выражений (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Типы данных в выражениях (построитель отчетов и службы SSRS)](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [Область выражения для суммирования, агрегатных функций и встроенных коллекций (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
