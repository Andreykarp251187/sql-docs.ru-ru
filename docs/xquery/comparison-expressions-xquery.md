---
title: Сравнение Выражений (X-Кикери) Документы Майкрософт
description: Узнайте, как использовать выражения сравнения X's, которые содержат операторы сравнения общих, значений, узлов и узлов.
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
- node comparison operators [XQuery]
- comparison expressions [XQuery]
- node order comparison operators [XQuery]
- expressions [XQuery], comparison
- comparison operators [XQuery]
- value comparison operators
ms.assetid: dc671348-306f-48ef-9e6e-81fc3c7260a6
author: rothja
ms.author: jroth
ms.openlocfilehash: 082fb2d1afdfa8824ea6f3d6e7bd3e4c484e281e
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388169"
---
# <a name="comparison-expressions-xquery"></a>Выражения сравнения (XQuery)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Язык XQuery предоставляет следующие типы операторов сравнения:  
  
-   общие операторы сравнения;  
  
-   операторы сравнения значений;  
  
-   операторы сравнения узлов;  
  
-   операторы сравнения порядка узлов.  
  
## <a name="general-comparison-operators"></a>Общие операторы сравнения  
 Общие операторы сравнения могут быть использованы для сравнения атомарных значений, последовательностей или любого их сочетания.  
  
 Общие операторы определены в представленной ниже таблице.  
  
|Оператор|Описание|  
|--------------|-----------------|  
|=|Равно|  
|!=|Не равно|  
|\<|Меньше чем|  
|>|Больше|  
|\<=|Меньше или равно|  
|>=|Больше или равно|  
  
 При сравнении двух последовательностей с помощью общих операторов сравнения, когда во второй последовательности существует значение, при сравнении которого со значением в первой последовательности возвращается результат True, то итоговым результатом будет значение True. В противном случае общим результатом будет значение False. Например: выражение (1, 2, 3) = (3, 4) имеет значение True, потому что значение 3 встречается в обеих последовательностях.  
  
```  
declare @x xml  
set @x=''  
select @x.query('(1,2,3) = (3,4)')    
```  
  
 Сравнение предполагает, что значения относятся к сравниваемым типам. Точнее, выполняется их статическая проверка. При сравнении чисел может возникать продвижение числового типа. Например: если десятичное значение 10 сравнивается со значением 1e1 типа double, десятичное значение преобразуется в тип double. Обратите внимание, что эти результаты могут быть неточными, так как сравнения типа double точными быть не могут.  
  
 Если одно из значений является нетипизированным, оно приводится к типу другого значения. В следующем примере значение 7 рассматривается как целое. Перед сравнением нетипизированное значение /a[1] преобразовывается в целое. Сравнение целых чисел возвращает значение True.  
  
```  
declare @x xml  
set @x='<a>6</a>'  
select @x.query('/a[1] < 7')  
```  
  
 И наоборот: если нетипизированное значение сравнивается со строкой или другим нетипизированным значением, оно приводится к значению xs:string. В следующем запросе строка «6» сравнивается со строкой «17». Этот запрос возвращает значение False, так как выполняется сравнение строк.  
  
```  
declare @x xml  
set @x='<a>6</a>'  
select @x.query('/a[1] < "17"')  
```  
  
 Следующий запрос возвращает небольшие изображения модели продуктов из каталога продуктов, представленного в образце базы данных AdventureWorks. Запрос сравнивает последовательность атомарных значений, возвращаемых `PD:ProductDescription/PD:Picture/PD:Size` с одноэлементной последовательностью «small». Если сравнение верно, оно возвращает\> элемент <Picture.  
  
```  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS PD)  
SELECT CatalogDescription.query('         
    for $P in /PD:ProductDescription/PD:Picture[PD:Size = "small"]         
    return $P') as Result         
FROM   Production.ProductModel         
WHERE  ProductModelID=19         
```  
  
 Следующий запрос сравнивает последовательность телефонных\> номеров в <элементов числа строки буквально "112-111-1111". Запрос сравнивает последовательность элементов телефонных номеров в столбце AdditionalContactInfo, чтобы определить существует ли в документе конкретный телефонный номер для конкретного заказчика.  
  
```  
WITH XMLNAMESPACES (  
  'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes' AS act,  
  'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo' AS aci)  
  
SELECT AdditionalContactInfo.value('         
   /aci:AdditionalContactInfo//act:telephoneNumber/act:number = "112-111-1111"', 'nvarchar(10)') as Result         
FROM Person.Contact         
WHERE ContactID=1         
```  
  
 Запрос возвращает значение True. Это означает, что номер в документе существует. Следующий запрос является незначительной модификацией предыдущего. В нем значения телефонных номеров, получаемых из документа, сравниваются с последовательностью из двух значений телефонных номеров. Если сравнение верно, элемент\> <числа возвращается.  
  
```  
WITH XMLNAMESPACES (  
  'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes' AS act,  
  'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo' AS aci)  
  
SELECT AdditionalContactInfo.query('         
  if (/aci:AdditionalContactInfo//act:telephoneNumber/act:number = ("222-222-2222","112-111-1111"))         
  then          
     /aci:AdditionalContactInfo//act:telephoneNumber/act:number         
  else         
    ()') as Result         
FROM Person.Contact         
WHERE ContactID=1  
  
```  
  
 Результат:  
  
```  
\<act:number   
  xmlns:act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">  
    111-111-1111  
\</act:number>  
\<act:number   
  xmlns:act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">  
    112-111-1111  
\</act:number>   
```  
  
## <a name="value-comparison-operators"></a>Операторы сравнения значений  
 Операторы сравнения значений используются для сравнения атомарных значений. Обратите внимание, что вместо операторов сравнения значений в запросах можно использовать общие операторы сравнения.  
  
 Операторы сравнения значений определены в следующей таблице.  
  
|Оператор|Описание|  
|--------------|-----------------|  
|eq|Равно|  
|ne|Не равно|  
|lt|Меньше чем|  
|gt|Больше|  
|le|Меньше или равно|  
|ge|Больше или равно|  
  
 Если согласно выбранному оператору два значения сравнивают одно и тоже, выражение возвратит True. В противном случае будет возвращено False. Если какое-либо из значений является пустой последовательностью, результатом выражения будет False.  
  
 Эти операторы работают только для одноэлементных атомарных значений. Таким образом, нельзя указать последовательность в качестве одного из операндов.  
  
 Например, следующий запрос \<извлекает элементы Picture> для модели продукта, где размер изображения "небольшой:  
  
```  
SELECT CatalogDescription.query('         
              declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";         
              for $P in /PD:ProductDescription/PD:Picture[PD:Size eq "small"]         
              return         
                    $P         
             ') as Result         
FROM Production.ProductModel         
WHERE ProductModelID=19         
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   Инструкция `declare namespace` определяет префикс пространства имен, который затем используется в запросе.  
  
-   Значение \<элемента размера> сравнивается с указанным атомным значением "малым".  
  
-   Обратите внимание, что, поскольку операторы значений работают только на атомных значениях, функция **данных()** неявно используется для получения значения узла. То есть функция `data($P/PD:Size) eq "small"` выдает тот же результат.  
  
 Результат:  
  
```  
\<PD:Picture   
  xmlns:PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">  
  \<PD:Angle>front\</PD:Angle>  
  \<PD:Size>small\</PD:Size>  
  \<PD:ProductPhotoID>31\</PD:ProductPhotoID>  
\</PD:Picture>  
```  
  
 Обратите внимание, что правила продвижения типа для сравнений значений такие же, как и для общих сравнений. Кроме того, при сравнениях значений [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] применяет к нетипизированным значениям те же правила приведения, что используются при выполнении общих сравнений. И напротив, по правилам в спецификации XQuery при выполнении сравнений значений нетипизированное значение всегда приводится к значению xs:string.  
  
## <a name="node-comparison-operator"></a>Операторы сравнения узлов  
 Оператор сравнения узлов, **применяется**только к типам узлов. Возвращаемый им результат указывает, представляют ли два переданных как операнды узла в исходном документе один узел. Этот оператор возвращает значение True, если два операнда являются одним узлом. В противном случае возвращается значение False.  
  
 Следующий запрос проверяет, является ли 10-й участок цеха первым в производственном процессе определенной модели продукта.  
  
```  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions' AS AWMI)  
  
SELECT ProductModelID, Instructions.query('         
    if (  (//AWMI:root/AWMI:Location[@LocationID=10])[1]         
          is          
          (//AWMI:root/AWMI:Location[1])[1] )          
    then         
          <Result>equal</Result>         
    else         
          <Result>Not-equal</Result>         
         ') as Result         
FROM Production.ProductModel         
WHERE ProductModelID=7           
```  
  
 Результат:  
  
```  
ProductModelID       Result          
-------------- --------------------------  
7              <Result>equal</Result>      
```  
  
## <a name="node-order-comparison-operators"></a>Операторы сравнения порядка узлов  
 Операторы сравнения порядка узлов сравнивают пары узлов, исходя из их позиций в документе.  
  
 На основе порядка документа выполняются следующие сравнения:  
  
-   `<<`: В порядке документа предшествует **operand 2.** **operand 2**  
  
-   `>>`: Следует ли **операнду 1** **в** порядке документа.  
  
 Следующий запрос возвращается Правда, если \<описание каталога продукта имеет \<элемент гарантии>, появляющийся перед элементом обслуживания> в заказе документа для конкретного продукта.  
  
```  
WITH XMLNAMESPACES (  
  'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS PD,  
  'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain' AS WM)  
  
SELECT CatalogDescription.value('  
     (/PD:ProductDescription/PD:Features/WM:Warranty)[1] <<   
           (/PD:ProductDescription/PD:Features/WM:Maintenance)[1]', 'nvarchar(10)') as Result  
FROM  Production.ProductModel  
where ProductModelID=19  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   В запросе используется метод **значения ()** типа данных **xml.**  
  
-   Результат Boolean запроса преобразуется в **nvarchar (10)** и возвращается.  
  
-   Запрос возвращает значение True.  
  
## <a name="see-also"></a>См. также:  
 [Система типа &#40;&#41;X','](../xquery/type-system-xquery.md)   
 [Выражения языка XQuery](../xquery/xquery-expressions.md)  
  
  
