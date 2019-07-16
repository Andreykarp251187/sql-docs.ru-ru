---
title: Функция position (XQuery) | Документация Майкрософт
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
- position function
- fn:position function
ms.assetid: f1bab9e4-1715-4c06-9cb0-06c7e0c9c97f
author: rothja
ms.author: jroth
ms.openlocfilehash: de9f30c3c63030aa956366c222b7cbda94e2becb
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68038978"
---
# <a name="context-functions---position-xquery"></a>Функции контекста — position (XQuery)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает целочисленное значение, указывающее позицию контекстного элемента в последовательности обрабатываемых в данный момент элементов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn:position() as xs:integer  
```  
  
## <a name="remarks"></a>Примечания  
 В [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], **fn: position()** может использоваться только в контексте контекстно зависимого предиката. Конкретно ее можно использовать только внутри квадратных скобок ([]). Сравнение с данной функцией не приводит к снижению количества элементов в процессе статического определения типов.  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, которые хранятся в различных **xml** -столбцов в [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] базы данных.  
  
### <a name="a-using-the-position-xquery-function-to-retrieve-the-first-two-product-features"></a>A. Использование функции position() в запросе XQuery для получения первых двух характеристик продукта  
 Следующий запрос получает первые две характеристики — первые два дочерних элемента <`Features`> элемент, из описания каталога моделей продуктов. Если имеются дополнительные функции, он добавляет <`there-is-more/`> элемент к результату.  
  
```  
SELECT CatalogDescription.query('  
     declare namespace pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     <Product>   
          { /pd:ProductDescription/@ProductModelID }  
          { /pd:ProductDescription/@ProductModelName }   
          {  
            for $f in /pd:ProductDescription/pd:Features/*[position()<=2]  
            return  
            $f   
          }  
          {  
            if (count(/pd:ProductDescription/pd:Features/*) > 2)  
            then <there-is-more/>  
            else ()  
          }   
     </Product>          
') as x  
FROM Production.ProductModel  
WHERE CatalogDescription is not null  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   **Пространства имен** ключевое слово в [прологе XQuery](../xquery/modules-and-prologs-xquery-prolog.md) определяет префикс пространства имен, который используется в теле запроса.  
  
-   Текст запроса формирует XML, который содержит \<продукта > элемент с **ProductModelID** и **ProductModelName** атрибуты и характеристиками продукта, возвращаются в виде дочерних элементов.  
  
-   **Position()** функция используется в предикате для определения положения \<функции > дочерний элемент в контексте. Если он является первой или второй функцией, он возвращается.  
  
-   Инструкция IF добавляет \<there-is-more / > элемент к результату при наличии более двух характеристик в каталоге продуктов.  
  
-   Так как не для всех моделей продуктов их описание из каталога хранится в таблице, используется предложение WHERE для отсева строк, для которых значение CatalogDescriptions равно NULL.  
  
 Частичный результат:  
  
```  
<Product ProductModelID="19" ProductModelName="Mountain 100">  
  <p1:Warranty xmlns:p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
    <p1:WarrantyPeriod>3 year</p1:WarrantyPeriod>  
    <p1:Description>parts and labor</p1:Description>  
  </p1:Warranty>  
  <p2:Maintenance xmlns:p2="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
    <p2:NoOfYears>10</p2:NoOfYears>  
    <p2:Description>maintenance contact available through your dealer or  
                    any AdventureWorks retail store.</p2:Description>  
  </p2:Maintenance>  
  <there-is-more/>  
</Product>   
...  
```  
  
## <a name="see-also"></a>См. также  
 [Функции XQuery для типа данных XML](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
