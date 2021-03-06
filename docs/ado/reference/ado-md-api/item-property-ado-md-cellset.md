---
description: Свойство Item (многомерный объект ADO Cellset)
title: Свойство Item (объекты данных ActiveX (MD) набор ячеек) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Item
- Cellset::Item
helpviewer_keywords:
- Item property [ADO MD]
ms.assetid: 0e93d79b-b12e-4e98-889e-c2dfcca20fd0
author: rothja
ms.author: jroth
ms.openlocfilehash: 997777e853a54ae56175b4b5795087e67079813b
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88986605"
---
# <a name="item-property-ado-md-cellset"></a>Свойство Item (многомерный объект ADO Cellset)
Извлекает ячейку из набора [ячеек](./cellset-object-ado-md.md) , используя ее координаты.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Set  
Cell = Cellset.Item ( Positions)  
```  
  
## <a name="parameters"></a>Параметры  
 *Positions*  
 **VariantArray** значений, уникально указывающих ячейку. *Положение* может быть одним из следующих:  
  
-   Массив номеров позиций  
  
-   Массив имен элементов  
  
-   Порядковый номер  
  
## <a name="remarks"></a>Remarks  
 Свойство **Item** используется для возвращения объекта [ячейки](./cell-object-ado-md.md) в объекте набора [ячеек](./cellset-object-ado-md.md) . Если свойству **Item** не удается найти ячейку, соответствующую аргументу *Positions* , возникает ошибка.  
  
 Свойство **Item** является свойством по умолчанию для объекта набора **ячеек** . Следующие формы синтаксиса взаимозаменяемы:  
  
```  
  
Cellset.Item ( Positions )Cellset ( Positions )  
```  
  
 Аргумент *Positions* указывает, какая ячейка должна быть возвращена. Можно указать ячейку по порядковому номеру или по положению вдоль каждой оси. При указании ячейки по положению вдоль каждой оси можно указать числовое значение расположения или имена элементов для каждой из них.  
  
 Порядковый номер — это число, однозначно идентифицирующее одну ячейку в наборе **ячеек**. По сути, ячейки нумеруются в наборе **ячеек** , как если бы набор **ячеек** был многомерным *p*массивом, где *p* — это число осей. Адресация ячеек осуществляется по строкам. Ниже приведена формула для вычисления порядкового номера ячейки.  
  
 Если имена членов передаются как строки в **элемент**, они должны быть перечислены в порядке возрастания числовых идентификаторов осей. Внутри оси элементы должны быть перечислены в порядке возрастания вложенности измерений, то есть сначала элемент внешнего измерения, а затем элементы внутренних измерений. Каждое измерение должно быть представлено отдельной строкой, а список строк членов следует разделять запятыми.  
  
> [!NOTE]
>  Получение ячеек по имени элемента может не поддерживаться поставщиком данных. Дополнительные сведения см. в документации для поставщика.  
  
## <a name="applies-to"></a>Применение  
 [Объект Cellset (многомерные объекты ADO)](./cellset-object-ado-md.md)  
  
## <a name="see-also"></a>См. также  
 [Объект Cell (объекты данных ActiveX (MD))](./cell-object-ado-md.md)   
 [Объект Cellset (многомерные объекты ADO)](./cellset-object-ado-md.md)