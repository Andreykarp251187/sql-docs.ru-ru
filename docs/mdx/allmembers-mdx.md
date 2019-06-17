---
title: AllMembers (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 92cde0acf07f62d0678da6dd96efa707dedc1a1f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63066252"
---
# <a name="allmembers-mdx"></a>AllMembers (многомерные выражения)


  Вычисляет выражение иерархии или уровня и возвращает набор, содержащий все элементы заданной иерархии или уровня, включая все вычисляемые элементы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Hierarchy syntax  
Hierarchy_Expression.AllMembers  
  
Level syntax  
Level_Expression.AllMembers  
```  
  
## <a name="arguments"></a>Аргументы  
 *Hierarchy_Expression*  
 Допустимое многомерное выражение, возвращающее иерархию.  
  
 *Level_Expression*  
 Допустимое многомерное выражение, возвращающее уровень.  
  
## <a name="remarks"></a>Примечания  
 **AllMembers** функция возвращает набор, содержащий все элементы, включая вычисляемые, заданной иерархии или уровня. **AllMembers** функция возвращает вычисляемые элементы, даже если заданной иерархии или уровне нет видимых элементов.  
  
> [!IMPORTANT]  
>  Если измерение содержит единственную видимую иерархию, на нее можно сослаться по имени измерения или по имени иерархии, поскольку имя измерения в этом случае разрешается в единственную видимую иерархию. Например, многомерное выражение `Measures.AllMembers` является допустимым, поскольку измерение Measures разрешается в единственную видимую иерархию.  
  
> [!NOTE]  
>  **AllMembers** функция семантически аналогична методу [AddCalculatedMembers (многомерные Выражения)](../mdx/addcalculatedmembers-mdx.md) функции.  
  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает все элементы в [`Date].[Calendar Year]` иерархии атрибута по оси столбцов, это включает в себя вычисляемые элементы и набор всех потомков `[Product].[Model Name]` иерархии на оси строк из атрибута **Adventure Works** куба.  
  
```  
SELECT  
   [Date].[Calendar Year].AllMembers ON COLUMNS,  
   [Product].[Model Name].Children ON ROWS  
FROM  
   [Adventure Works]  
```  
  
 Следующий пример возвращает все элементы в **меры** измерения на оси столбцов, сюда входят все вычисляемые элементы и набор всех потомков `[Product].[Model Name]` иерархии на оси строк атрибута из **Adventure Works** куба.  
  
```  
SELECT  
    Measures.AllMembers ON COLUMNS,  
    [Product].[Model Name].Children ON ROWS  
FROM  
    [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также  
 [AddCalculatedMembers (многомерные выражения)](../mdx/addcalculatedmembers-mdx.md)   
 [Children (многомерные выражения)](../mdx/children-mdx.md)   
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
