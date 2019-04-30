---
title: Метод CompareBookmarks (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CompareBookmarks
- Recordset20::CompareBookmarks
- Recordset20::raw_CompareBookmarks
helpviewer_keywords:
- CompareBookmarks method [ADO]
ms.assetid: d0b64286-2cc4-4a22-8f1d-9aefeebbcbc6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 85ca76678c0d3e75a106164626c4e3c3a81bd7e9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63315979"
---
# <a name="comparebookmarks-method-ado"></a>Метод CompareBookmarks (ADO)
Сравнивает два закладки и возвращает сведения об их относительных значениях.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
result = recordset.CompareBookmarks(Bookmark1, Bookmark2)  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает [CompareEnum](../../../ado/reference/ado-api/compareenum.md) значение, указывающее положение строки относительный две записи, представленной закладок.  
  
#### <a name="parameters"></a>Параметры  
 *Закладке Bookmark1*  
 Закладка, первой строки.  
  
 *Bookmark2*  
 Закладка, второй строки.  
  
## <a name="remarks"></a>Примечания  
 Закладки необходимо применить к тому же [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта, или **записей** объекта и его [клона](../../../ado/reference/ado-api/clone-method-ado.md). Невозможно сравнить надежно закладок из разных **записей** объектов, даже если они были созданы из одного источника или команды. И не может сравнить закладок для **записей** объект, базовый поставщик не поддерживает сравнение.  
  
 Закладка, уникально определяющий строку в **записей** объекта. Используйте [закладки](../../../ado/reference/ado-api/bookmark-property-ado.md) свойство текущей строки, чтобы получить ее закладки.  
  
 Так как тип данных закладки является специфичным для каждого поставщика, ADO предоставляет его как **Variant**. Например, SQL Server закладки относятся к типу DBTYPE_R8 (**двойные**). ADO предоставит этот тип как **Variant** с подтипом **двойные**.  
  
 При сравнении закладки, ADO не пытайтесь любого типа приведения. Значения просто передает поставщику где происходит сравнение. Если передается закладки **CompareBookmarks** метод хранятся в переменных различающихся типов, он может сформировать следующие ошибка несоответствия типов: «Аргументы имеют неправильный тип, выходят за пределы допустимого диапазона или конфликтуют друг с другом.»  
  
 Закладка, которая не является допустимым или неправильно приведет к ошибке.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример метода CompareBookmarks (Visual Basic)](../../../ado/reference/ado-api/comparebookmarks-method-example-vb.md)   
 [Пример метода CompareBookmarks (Visual C++)](../../../ado/reference/ado-api/comparebookmarks-method-example-vc.md)   
 [Свойство Bookmark (ADO)](../../../ado/reference/ado-api/bookmark-property-ado.md)
