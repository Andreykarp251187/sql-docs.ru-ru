---
title: Функция string-length (XQuery) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- string-length function
- fn:string-length function
ms.assetid: 7cd69c8b-cf2c-478c-b9a3-e0e14e1aa8aa
author: rothja
ms.author: jroth
ms.openlocfilehash: 12ae1efbf900a505a5f257f9684842a0ad9ff21f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68004650"
---
# <a name="functions-on-string-values---string-length"></a>Функции со строковыми значениями — string-length
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает длину строки в символах.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn:string-length() as xs:integer  
fn:string-length($arg as xs:string?) as xs:integer  
```  
  
## <a name="arguments"></a>Аргументы  
 *$arg*  
 Строка источника, длина которой подлежит вычислению.  
  
## <a name="remarks"></a>Примечания  
 Если значение *$arg* представляет собой пустую последовательность, **xs: Integer** возвращается значение 0.  
  
 Поведение суррогатных пар в функциях XQuery зависит от уровня совместимости базы данных. Если уровень совместимости 110 или выше, каждая суррогатная пара рассматривается как один символ. При более низких уровнях совместимости они рассматриваются как два символа. Дополнительные сведения см. в разделе [уровень совместимости ALTER DATABASE &#40;Transact-SQL&#41; ](../t-sql/statements/alter-database-transact-sql-compatibility-level.md) и [Collation and Unicode Support](../relational-databases/collations/collation-and-unicode-support.md).  
  
 Если значение содержит 4-байтовый символ в Юникоде, представленный двумя суррогатными символами, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] будет подсчитывать суррогатные символы по отдельности.  
  
 **String-length() языка** без параметра может использоваться только внутри предиката. Например, следующий запрос возвращает <`ROOT`> элемент:  
  
```  
DECLARE @x xml;  
SET @x='<ROOT>Hello</ROOT>';  
SELECT @x.query('/ROOT[string-length()=5]');  
```  
  
## <a name="supplementary-characters-surrogate-pairs"></a>Дополнительные символы (суррогатные пары)  
 Поведение суррогатных пар в функциях XQuery зависит от уровня совместимости базы данных и, в некоторых случаях, от URI-кода пространства имен по умолчанию для функций. Дополнительные сведения см. в подразделе «XQuery функций учитывают суррогаты» раздела [критические изменения в функциях ядра СУБД в SQL Server 2016](../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md). Также см. в разделе [уровень совместимости ALTER DATABASE &#40;Transact-SQL&#41; ](../t-sql/statements/alter-database-transact-sql-compatibility-level.md) и [Collation and Unicode Support](../relational-databases/collations/collation-and-unicode-support.md).  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, хранящимся в различных **xml** -столбец базы данных AdventureWorks.  
  
### <a name="a-using-the-string-length-xquery-function-to-retrieve-products-with-long-summary-descriptions"></a>A. Использование функции string-length() языка XQuery для получения продуктов с длинными сводными описаниями  
 Для продуктов, сводное описание длиннее 50 символов, следующий запрос получает идентификатор продукта, длину сводного описания и сводное <`Summary`> элемента.  
  
```  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' as pd)  
SELECT CatalogDescription.query('  
      <Prod ProductID= "{ /pd:ProductDescription[1]/@ProductModelID }" >  
       <LongSummary SummaryLength =   
           "{string-length(string( (/pd:ProductDescription/pd:Summary)[1] )) }" >  
           { string( (/pd:ProductDescription/pd:Summary)[1] ) }  
       </LongSummary>  
      </Prod>  
 ') as Result  
FROM Production.ProductModel  
WHERE CatalogDescription.value('string-length( string( (/pd:ProductDescription/pd:Summary)[1]))', 'decimal') > 200;  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   Условие в предложении WHERE получает только строки, в которых описания сводки, хранимые в XML-документе, длиннее 200 символов. Она использует [метод value() (тип данных XML)](../t-sql/xml/value-method-xml-data-type.md).  
  
-   Предложение SELECT просто выстраивает необходимый код XML. Она использует [метода query() (тип данных XML)](../t-sql/xml/query-method-xml-data-type.md) создать XML и указать необходимое выражение XQuery для получения данных из XML-документа.  
  
 Частичный результат:  
  
```  
Result  
-------------------  
<Prod ProductID="19">  
      <LongSummary SummaryLength="214">Our top-of-the-line competition   
             mountain bike. Performance-enhancing options include the  
             innovative HL Frame, super-smooth front suspension, and   
             traction for all terrain.  
      </LongSummary>  
</Prod>  
...  
```  
  
### <a name="b-using-the-string-length-xquery-function-to-retrieve-products-whose-warranty-descriptions-are-short"></a>Б. Использование функции string-length() языка XQuery для получения продуктов с короткими описаниями гарантии  
 Для продуктов чьи гарантийные описания меньше 20 символов в длину, следующий запрос получает XML, который включает идентификатор продукта, длину, гарантийное описание гарантии и <`Warranty`> сам элемент.  
  
 Гарантия — это одна из характеристик продукта. Необязательный <`Warranty`> дочернего элемента, следующего за после <`Features`> элемента.  
  
```  
WITH XMLNAMESPACES (  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS pd,  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain' AS wm)  
  
SELECT CatalogDescription.query('  
      for   $ProdDesc in /pd:ProductDescription,  
            $pf in $ProdDesc/pd:Features/wm:Warranty  
      where string-length( string(($pf/wm:Description)[1]) ) < 20  
      return   
          <Prod >  
             { $ProdDesc/@ProductModelID }  
             <ShortFeature FeatureDescLength =   
                             "{string-length( string(($pf/wm:Description)[1]) ) }" >  
                 { $pf }  
             </ShortFeature>  
          </Prod>  
     ') as Result  
FROM Production.ProductModel  
WHERE CatalogDescription.exist('/pd:ProductDescription')=1;  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   **pd** и **wm** являются префиксы пространств имен, используемых в этом запросе. Они определяют то же пространство имен, что используется в запрашиваемом документе;  
  
-   XQuery указывает вложенный цикл FOR. Внешний цикл обязателен, так как вы хотите получить **ProductModelID** атрибуты элемента <`ProductDescription`> элемента. Внутренний цикл FOR требуется, так как нужны только продукты, имеющие описания характеристик гарантии меньше 20 символов в длину.  
  
 Частичный результат:  
  
```  
Result  
-------------------------  
<Prod ProductModelID="19">  
  <ShortFeature FeatureDescLength="15">  
    <wm:Warranty   
       xmlns:wm="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
      <wm:WarrantyPeriod>3 years</wm:WarrantyPeriod>  
      <wm:Description>parts and labor</wm:Description>  
    </wm:Warranty>  
   </ShortFeature>  
</Prod>  
...  
```  
  
## <a name="see-also"></a>См. также  
 [Функции XQuery для типа данных XML](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
