---
title: Столбцы без имени | Документация Майкрософт
description: Узнайте, как SQL Server обрабатывает столбцы без имени при создании XML.
ms.custom: ''
ms.date: 08/01/2020
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns without
ms.assetid: 440de44e-3a56-4531-b4e4-1533ca933cac
author: rothja
ms.author: jroth
ms.openlocfilehash: 878f1a89240f8df02eaafb34cef09540b884b614
ms.sourcegitcommit: 7035d9471876c70b99c58bf9b46af5cce6e9c66c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2020
ms.locfileid: "87523446"
---
# <a name="columns-without-a-name"></a>Столбцы без имени
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  Любой столбец, не имеющий имени, будет встроенным. Например, вычисляемые столбцы или вложенные скалярные запросы, в которых не задан псевдоним столбца, формируют столбцы без имени. Если столбец имеет тип данных **xml** , в него помещается содержимое экземпляра этого типа данных. В противном случае содержимое столбца вставляется как текстовый узел.  
  
```sql
SELECT 2+2  
FOR XML PATH  
```  
  
 Создание этого XML. По умолчанию для каждой строки в наборе строк в итоговом XML-документе формируется элемент `<row>`. То же самое происходит в режиме RAW.  
  
 `<row>4</row>`  
  
 Следующий запрос возвращает набор строк с тремя столбцами. Третий столбец, без названия, содержит XML-данные. Режим PATH вставляет экземпляр типа xml.  
  
```sql
USE AdventureWorks2012;  
GO  
SELECT ProductModelID,  
       Name,  
       Instructions.query(
           'declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
            /MI:root/MI:Location   
           ')   
FROM Production.ProductModel  
WHERE ProductModelID=7  
FOR XML PATH ;  
GO  
```  
  
 Частичный результат:  
  
```xml
<row>
  <ProductModelID>7</ProductModelID>
  <Name>HL Touring Frame</Name>
  <MI:Location ...LocationID="10" ...></MI:Location>
  <MI:Location ...LocationID="20" ...></MI:Location>
  ...
</row>
```

## <a name="see-also"></a>См. также:  
 [Использование режима PATH совместно с FOR XML](../../relational-databases/xml/use-path-mode-with-for-xml.md)  
  
  
