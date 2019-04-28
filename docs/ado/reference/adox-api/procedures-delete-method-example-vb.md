---
title: Процедуры удаления пример метода (Visual Basic) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- Delete method [ADOX], Visual Basic example
ms.assetid: 94f1ac93-e778-4a40-a85e-94bce5316ac7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d75b8b66157ee46b423800a430d4cef30d28359a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62709116"
---
# <a name="procedures-delete-method-example-vb"></a>Пример метода Delete коллекции Procedures (Visual Basic)
Следующий код демонстрирует удаление процедуры с помощью [удалить](../../../ado/reference/adox-api/delete-method-adox-collections.md) метод [процедуры](../../../ado/reference/adox-api/procedures-collection-adox.md) коллекции.  
  
```  
' BeginDeleteProcedureVB  
Sub Main()  
    On Error GoTo DeleteProcedureError  
  
    Dim cat As New ADOX.Catalog  
  
    ' Open the catalog.  
    cat.ActiveConnection = _  
        "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source='Northwind.mdb';"  
  
    ' Delete the procedure.  
    cat.Procedures.Delete "CustomerById"  
  
    'Clean up.  
    Set cat.ActiveConnection = Nothing  
    Set cat = Nothing  
    Exit Sub  
  
DeleteProcedureError:  
    Set cat = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndDeleteProcedureVB  
```  
  
## <a name="see-also"></a>См. также  
 [Свойство ActiveConnection (ADOX)](../../../ado/reference/adox-api/activeconnection-property-adox.md)   
 [Объект Catalog (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Удаление метода (коллекции ADOX)](../../../ado/reference/adox-api/delete-method-adox-collections.md)   
 [Объект Procedure (ADOX)](../../../ado/reference/adox-api/procedure-object-adox.md)   
 [Коллекция Procedures (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)
