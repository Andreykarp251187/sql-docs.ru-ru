---
title: XQuery Prolog | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- XQuery, prolog
- prolog
- namespaces [XQuery]
- default namespace declarations
ms.assetid: 03924684-c5fd-44dc-8d73-c6ab90f5e069
author: rothja
ms.author: jroth
ms.openlocfilehash: 84f4093fe9c4693c50d6ae89c7b2ba111191db9d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67946609"
---
# <a name="modules-and-prologs---xquery-prolog"></a>Модули и прологи — пролог XQuery
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Запрос XQuery состоит из пролога и текста запроса. Пролог XQuery является набором объявлений и определений, создающим требуемую для обработки запроса среду. На сервере SQL Server, в прологе XQuery могут содержаться объявления пространств имен. Текст запроса XQuery состоит из последовательности выражений, которые определяют желаемый результат запроса.  
  
 Например, следующий запрос XQuery задан для столбца Instructions **xml** тип, который хранит промышленные инструкции в формате XML. Запрос получает инструкции по производству продукта для производственного цеха `10`. `query()` Метод **xml** тип данных используется для определения запроса XQuery.  
  
```  
SELECT Instructions.query('declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";           
    /AWMI:root/AWMI:Location[@LocationID=10]  
') AS Result   
FROM  Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   Пролог XQuery содержит объявление префикса (AWMI) пространства имен `(namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";`.  
  
-   Ключевое слово `declare namespace` определяет префикс пространств имен, который впоследствии используется в теле запроса.  
  
-   `/AWMI:root/AWMI:Location[@LocationID="10"]` является текстом запроса.  
  
## <a name="namespace-declarations"></a>Объявление пространств имен  
 Объявление пространств имен задает префикс и связывает его с URI-кодом пространства имен, как показано в следующем запросе. В запросе `CatalogDescription` — **xml** столбец типа.  
  
 В определенном запросе XQuery для этого столбца пролог запроса определяет объявление `declare namespace`, которое связывает префикс `PD`, описание продукта с URI-кодом пространства имен. Затем этот префикс используется в теле запроса вместо URI-кода пространства имен. Узлы результирующего XML находятся в пространстве имен, связанном с URI-кодом пространства имен.  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
         /PD:ProductDescription/PD:Summary   
    ') as Result  
FROM Production.ProductModel  
where ProductModelID=19  
```  
  
 Чтобы упростить понимание запроса, можно объявлять пространства имен при помощи WITH XMLNAMESPACES, а не путем объявления префиксов и пространств имен, связанных в прологе запроса при помощи `declare namespace`.  
  
```  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS PD)  
  
SELECT CatalogDescription.query('  
         /PD:ProductDescription/PD:Summary   
    ') as Result  
FROM Production.ProductModel  
where ProductModelID=19  
```  
  
 Дополнительные сведения см. в разделе, [добавление пространств имен в запросы с WITH XMLNAMESPACES](../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md).  
  
### <a name="default-namespace-declaration"></a>Установленные по умолчанию объявления пространств имен  
 Вместо объявления префикса пространства при помощи объявления `declare namespace` можно использовать объявление `declare default element namespace` для привязки заданного по умолчанию пространства имен к именам элементов. В этом случае не нужно задавать префикс.  
  
 В следующем примере выражение пути в теле запроса не определяет префикс пространства имен. По умолчанию все имена элементов, принадлежащие заданному по умолчанию пространству имен, определяются в прологе.  
  
```  
SELECT CatalogDescription.query('  
     declare default element namespace  "https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
        /ProductDescription/Summary   
    ') as Result  
FROM  Production.ProductModel  
WHERE ProductModelID=19   
```  
  
 Можно объявить заданное по умолчанию пространство имен при помощи WITH XMLNAMESPACES:  
  
```  
WITH XMLNAMESPACES (DEFAULT 'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription')  
SELECT CatalogDescription.query('  
        /ProductDescription/Summary   
    ') as Result  
FROM  Production.ProductModel  
WHERE ProductModelID=19   
```  
  
## <a name="see-also"></a>См. также  
 [Добавление пространств имен в запросы с WITH XMLNAMESPACES](../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md)  
  
  
