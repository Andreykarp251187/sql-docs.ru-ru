---
title: Hierarchize (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4478fb9657ef4577bcae8b5641f53154b2a0486c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63224898"
---
# <a name="hierarchize-mdx"></a>Hierarchize (многомерные выражения)


  Упорядочивает элементы набора в иерархии.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Hierarchize(Set_Expression [ , POST ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
## <a name="remarks"></a>Примечания  
 **Hierarchize** функция организует элементы указанного набора в иерархическом порядке. Повторяющиеся элементы всегда сохраняются.  
  
-   Если **POST** не указан, функция сортирует элементы уровня в естественном порядке. Естественным порядком является порядок следования элементов в иерархии по умолчанию, если не заданы другие условия сортировки. Потомки следуют сразу после своих предков.  
  
-   Если **POST** указано, **Hierarchize** функция сортирует элементы уровня в искусственном порядке. Другими словами, дочерние элементы предшествуют своим родителям.  
  
## <a name="example"></a>Пример  
 В следующем примере детализируется обобщением элемент Canada. **Hierarchize** функция используется для организации элементов указанного набора в иерархическом порядке, который необходим **DrillUpMember** функции.  
  
```  
SELECT DrillUpMember   
   (  
      Hierarchize  
         (  
            {[Geography].[Geography].[Country].[Canada]  
            ,[Geography].[Geography].[Country].[United States]  
            ,[Geography].[Geography].[State-Province].[Alberta]  
            ,[Geography].[Geography].[State-Province].[Brunswick]  
            ,[Geography].[Geography].[State-Province].[Colorado]   
            }  
         ), {[Geography].[Geography].[Country].[United States]}  
   )  
ON 0  
FROM [Adventure Works]  
```  
  
 В следующем примере возвращается сумма `Measures.[Order Quantity]` член, вычисленная за первые девять месяцев 2003, содержащихся в `Date` измерения, от **Adventure Works** куба. **PeriodsToDate** функции определяются кортежи в наборе, по которому передается функции Aggregate. **Hierarchize** функция упорядочивает элементы указанного набора элементы из измерения Product в иерархическом порядке.  
  
```  
WITH MEMBER Measures.[Declining Reseller Sales] AS Count  
   (Filter  
      (Existing  
         (Reseller.Reseller.Reseller),   
            [Measures].[Reseller Sales Amount] <   
               ([Measures].[Reseller Sales Amount],[Date].Calendar.PrevMember)  
        )  
    )  
MEMBER [Geography].[State-Province].x AS Aggregate   
( {[Geography].[State-Province].&[WA]&[US],   
   [Geography].[State-Province].&[OR]&[US] }   
)  
SELECT NON EMPTY HIERARCHIZE   
   (AddCalculatedMembers   
      ({DrillDownLevel  
         ({[Product].[All Products]})}  
        )  
    ) DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS   
FROM [Adventure Works]  
WHERE ([Geography].[State-Province].x,   
   [Date].[Calendar].[Calendar Quarter].&[2003]&[4],  
   [Measures].[Declining Reseller Sales])  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
