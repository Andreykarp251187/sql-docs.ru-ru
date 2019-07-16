---
title: Функция concat (XQuery) | Документация Майкрософт
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:concat function
- concat function [XQuery]
ms.assetid: d50afd20-a297-445e-be9e-13b48017e7ca
author: rothja
ms.author: jroth
ms.openlocfilehash: 063eca49a6a4d69e84e8a3d05221b632d0690bef
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68099829"
---
# <a name="functions-on-string-values---concat"></a>Функции со строковыми значениями — concat
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Принимает от нуля и более строк и возвращает строку, содержащую результат сцепления переданных аргументов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn:concat ($string as xs:string?  
           ,$string as xs:string?  
           [, ...]) as xs:string  
```  
  
## <a name="arguments"></a>Аргументы  
 *$string*  
 Необязательная строка для сцепления.  
  
## <a name="remarks"></a>Примечания  
 Функции требуется как минимум два аргумента. Если в качестве аргумента передана пустая последовательность, она трактуется как строка нулевой длины.  
  
## <a name="supplementary-characters-surrogate-pairs"></a>Дополнительные символы (суррогатные пары)  
 Поведение суррогатных пар в функциях XQuery зависит от уровня совместимости базы данных и, в некоторых случаях, от URI-кода пространства имен по умолчанию для функций. Дополнительные сведения см. в подразделе «XQuery функций учитывают суррогаты» раздела [критические изменения в функциях ядра СУБД в SQL Server 2016](../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md). Также см. в разделе [уровень совместимости ALTER DATABASE &#40;Transact-SQL&#41; ](../t-sql/statements/alter-database-transact-sql-compatibility-level.md) и [Collation and Unicode Support](../relational-databases/collations/collation-and-unicode-support.md).  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, которые хранятся в различных **xml** столбцов типа в базе данных AdventureWorks.  
  
### <a name="a-using-the-concat-xquery-function-to-concatenate-strings"></a>A. Применение функции concat() языка XQuery для объединения строк  
 Для указанного изделия запрос возвращает строку, полученную сцеплением гарантийного строка и гарантийных обязательств. В документе описания каталога <`Warranty`> элемент состоит из <`WarrantyPeriod`> и <`Description`> дочерних элементов.  
  
```  
WITH XMLNAMESPACES (  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS pd,  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain' AS wm)  
SELECT CatalogDescription.query('  
    <Product   
        ProductModelID= "{ (/pd:ProductDescription/@ProductModelID)[1] }"  
        ProductModelName = "{ sql:column("PD.Name") }" >  
        {   
          concat( string((/pd:ProductDescription/pd:Features/wm:Warranty/wm:WarrantyPeriod)[1]), "-",  
                  string((/pd:ProductDescription/pd:Features/wm:Warranty/wm:Description)[1]))   
         }   
     </Product>  
 ') as Result  
FROM Production.ProductModel PD  
WHERE  PD.ProductModelID=28  
  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   В предложении SELECT CatalogDescription является **xml** столбец типа. Таким образом [метода query() (тип данных XML)](../t-sql/xml/query-method-xml-data-type.md), то есть Instructions.Query(). Инструкция XQuery задана как аргумент метода query.  
  
-   Запрос к документу выполняется при использовании пространства имен, Таким образом **пространства имен** ключевое слово используется для определения префикса пространства имен. Дополнительные сведения см. в разделе [прологе XQuery](../xquery/modules-and-prologs-xquery-prolog.md).  
  
 Это результат:  
  
```  
<Product ProductModelID="28" ProductModelName="Road-450">1 year-parts and labor</Product>  
```  
  
 Приведенный запрос получает сведения об указанном изделии. Следующий запрос получает те же сведения по всем изделиям, для которых имеются описания каталога XML. **Exist()** метод **xml** типа данных в предложении WHERE возвращает True, если XML-документ в строках <`ProductDescription`> элемента.  
  
```  
WITH XMLNAMESPACES (  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS pd,  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain' AS wm)  
  
SELECT CatalogDescription.query('  
    <Product   
        ProductModelID= "{ (/pd:ProductDescription/@ProductModelID)[1] }"   
        ProductName = "{ sql:column("PD.Name") }" >  
        {   
          concat( string((/pd:ProductDescription/pd:Features/wm:Warranty/wm:WarrantyPeriod)[1]), "-",  
                  string((/pd:ProductDescription/pd:Features/wm:Warranty/wm:Description)[1]))   
         }   
     </Product>  
 ') as Result  
FROM Production.ProductModel PD  
WHERE CatalogDescription.exist('//pd:ProductDescription ') = 1  
  
```  
  
 Обратите внимание, что логическое значение, возвращаемое функцией **exist()** метод **xml** сравнивается со значением 1.  
  
### <a name="implementation-limitations"></a>Ограничения реализации  
 Существуют следующие ограничения:  
  
-   **Concat()** функции в SQL Server принимает только значения типа xs: String. Все остальные значения должны быть явно приведены в xs:string или xdt:untypedAtomic.  
  
## <a name="see-also"></a>См. также  
 [Функции XQuery для типа данных XML](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
