---
title: Удаление метода (коллекция Parameters ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _DynaCollection::Delete
- _DynaCollection::raw_Delete
helpviewer_keywords:
- Delete method [ADO]
ms.assetid: 160c575e-df63-4ade-a2d3-5fd8f72e70cc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8864ac47f3fa212cc6c204cc79d587b8952512cd
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63140165"
---
# <a name="delete-method-ado-parameters-collection"></a>Метод Delete (коллекция Parameters ADO)
Удаляет объект из [параметры](../../../ado/reference/ado-api/parameters-collection-ado.md) коллекции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Parameters.Delete Index  
```  
  
#### <a name="parameters"></a>Параметры  
 *Index*  
 Объект **строка** значение, содержащее имя объекта, удалить или порядковый номер объекта (индекс) в коллекции.  
  
## <a name="remarks"></a>Примечания  
 С помощью **удалить** метод коллекции позволяет удалить один из объектов в коллекции. Этот метод доступен только на **параметры** коллекцию [команда](../../../ado/reference/ado-api/command-object-ado.md) объекта. Необходимо использовать [параметр](../../../ado/reference/ado-api/parameter-object.md) объекта [имя](../../../ado/reference/ado-api/name-property-ado.md) свойство или его индекс коллекции, при вызове **удалить** объекта метод – это переменная не является допустимым аргументом.  
  
## <a name="applies-to"></a>Объект применения  
 [Коллекция Parameters (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Метод Delete (коллекция Fields ADO)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [Удаление метода (объект Recordset ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [Метод DeleteRecord (ADO)](../../../ado/reference/ado-api/deleterecord-method-ado.md)
