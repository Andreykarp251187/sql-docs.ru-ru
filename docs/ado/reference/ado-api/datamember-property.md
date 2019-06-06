---
title: Свойство DataMember | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset20::DataMember
helpviewer_keywords:
- DataMember property
ms.assetid: 2c8fb09e-10ad-49b5-ab41-2603771780d9
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 9de69478469a6bd177d12beab96e199b4720f3f5
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66695482"
---
# <a name="datamember-property"></a>Свойство DataMember
Указывает имя элемента данных, которые будут извлечены из [записей](../../../ado/reference/ado-api/recordset-object-ado.md) ссылается [DataSource](../../../ado/reference/ado-api/datasource-property-ado.md) свойство.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **строка** значение. Имя не учитывается регистр.  
  
## <a name="remarks"></a>Примечания  
 Это свойство используется для создания элементов управления с привязкой данных в среде данных. Поддерживает среду данных наборами данных (источники данных), содержащий именованные объекты (члены данных), на которые будет представлена в виде [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта.  
  
 **DataMember** и **DataSource** свойства, которые должны использоваться совместно.  
  
 **DataMember** свойство определяет, какой объект, указанный параметром **DataSource** свойство будет представлена в виде **записей** объекта. **Записей** объект должен быть закрыт, прежде чем это свойство имеет значение. Ошибка создается в том случае, если **DataMember** свойство не задано до **DataSource** свойство, или если **DataMember** имя не распознается средой объекта, указанного в **DataSource** свойство.  
  
## <a name="usage"></a>Использование  
  
```  
Dim rs as New ADODB.Recordset  
rs.DataMember = "Command"     'Name of the rowset to bind to  
Set rs.DataSource = myDE      'Name of the object containing an IRowset  
```  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство DataSource (ADO)](../../../ado/reference/ado-api/datasource-property-ado.md)
