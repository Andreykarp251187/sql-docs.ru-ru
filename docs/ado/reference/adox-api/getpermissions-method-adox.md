---
title: Метод GetPermissions (ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _User25::GetPermissions
- _Group25::raw_GetPermissions
- _Group25::GetPermissions
- _User25::raw_GetPermissions
helpviewer_keywords:
- GetPermissions method [ADOX]
ms.assetid: df201c1f-c76a-465d-98f0-83b7fc36e6e3
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 8bff406485266af99a1c2538a4df237fd5bf43bb
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66712090"
---
# <a name="getpermissions-method-adox"></a>Метод GetPermissions (ADOX)
Возвращает разрешения для [группы](../../../ado/reference/adox-api/group-object-adox.md) или [пользователя](../../../ado/reference/adox-api/user-object-adox.md) на объект или объект контейнера.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ReturnValue=GroupOrUser.GetPermissions(Name, ObjectType    [,ObjectTypeId])  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **Long** значение, указывающее Битовая маска, содержащая разрешения, которые группа или пользователь оказывает на данный объект. Это значение может быть один или несколько [RightsEnum](../../../ado/reference/adox-api/rightsenum.md) константы.  
  
#### <a name="parameters"></a>Параметры  
 *Name*  
 Объект **Variant** значение, указывающее имя объекта, для которого задаются разрешения. Задайте *имя* в значение null, если вы хотите получить разрешения для контейнера объекта.  
  
 *ObjectType*  
 Объект **Long** значение, которое может быть одним из [ObjectTypeEnum](../../../ado/reference/adox-api/objecttypeenum.md) константы, которое указывает тип объекта, для которого необходимо получить разрешения.  
  
 *ObjectTypeId*  
 Необязательный параметр. Объект **Variant** значение, которое указывает идентификатор GUID для типа объекта поставщика, не определенных в спецификации OLE DB. Этот параметр является обязательным, если *ObjectType* присваивается **adPermObjProviderSpecific**; в противном случае он не используется.  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Объект Group (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)|[Объект User (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)|  
  
## <a name="see-also"></a>См. также  
 [GetPermissions и SetPermissions методы (Visual Basic)](../../../ado/reference/adox-api/getpermissions-and-setpermissions-methods-example-vb.md)   
 [Свойство Name (ADOX)](../../../ado/reference/adox-api/name-property-adox.md)   
 [Метод SetPermissions (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)
