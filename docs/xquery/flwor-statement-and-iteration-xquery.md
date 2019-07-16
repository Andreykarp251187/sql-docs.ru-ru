---
title: Итерация (XQuery) и инструкция FLWOR | Документация Майкрософт
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
- return clause
- FLWOR statement
- effective Boolean value [XQuery]
- multiple variable binding
- order by clause [XQuery]
- for clause [XQuery]
- where clause [XQuery]
- iterations [XQuery]
- XQuery, FLWOR statement
- EBV
ms.assetid: d7cd0ec9-334a-4564-bda9-83487b6865cb
author: rothja
ms.author: jroth
ms.openlocfilehash: 9deb87d506e167d3de3439e0a07cfbb8bc040fac
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68038900"
---
# <a name="flwor-statement-and-iteration-xquery"></a>Итерация и инструкция FLWOR (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Язык XQuery определяет синтаксис итераций инструкции FLWOR. Слово FLWOR — это сокращение от слов `for`, `let`, `where`, `order by` и `return`.  
  
 Инструкция FLWOR состоит из следующих частей.  
  
-   Одно или несколько предложений FOR, которые привязывают одну или несколько переменных-итераторов к входным последовательностям.  
  
     Входные последовательности также могут быть выражениями XQuery (например, выражениями XPath). Они являются либо последовательностями узлов, либо последовательностями атомарных значений. Последовательности атомарных значений могут быть получены с помощью литералов или функций-конструкторов. В [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] нельзя использовать построенные XML-узлы в качестве входных последовательностей.  
  
-   Необязательное предложение `let`. Это предложение присваивает значение данной переменной для конкретной итерации. Присвоенное выражение может быть выражением XQuery, например выражением XPath, и может возвращать либо последовательность узлов, либо последовательность атомарных значений. Последовательности атомарных значений могут быть получены с помощью литералов или функций-конструкторов. В [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] нельзя использовать построенные XML-узлы в качестве входных последовательностей.  
  
-   Переменная-итератор. Дополнительно для этой переменной с помощью ключевого слова `as` можно указать тип.  
  
-   Необязательное предложение `where`. Это предложение применяется в качестве предиката фильтра при итерации.  
  
-   Необязательное предложение `order by`.  
  
-   Выражение `return`. Выражение в предложении `return` конструирует результат, возвращаемый инструкцией FLWOR.  
  
 Например, следующий запрос выполняет итерацию по <`Step`> элементы в первом месте производства и возвращает строковое значение <`Step`> узлы:  
  
```sql
declare @x xml  
set @x='<ManuInstructions ProductModelID="1" ProductModelName="SomeBike" >  
<Location LocationID="L1" >  
  <Step>Manu step 1 at Loc 1</Step>  
  <Step>Manu step 2 at Loc 1</Step>  
  <Step>Manu step 3 at Loc 1</Step>  
</Location>  
<Location LocationID="L2" >  
  <Step>Manu step 1 at Loc 2</Step>  
  <Step>Manu step 2 at Loc 2</Step>  
  <Step>Manu step 3 at Loc 2</Step>  
</Location>  
</ManuInstructions>'  
SELECT @x.query('  
   for $step in /ManuInstructions/Location[1]/Step  
   return string($step)  
')  
```  
  
 Это результат:  
  
```  
Manu step 1 at Loc 1 Manu step 2 at Loc 1 Manu step 3 at Loc 1  
```  
  
 Следующий запрос похож на предыдущий, за тем исключением, что он применяется к типизированному XML-столбцу Instructions в таблице ProductModel. Запрос перебирает все производственные шаги, <`step`> элементов, на первом участке цеха для конкретного продукта.  
  
```sql
SELECT Instructions.query('  
   declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
for $Step in //AWMI:root/AWMI:Location[1]/AWMI:step  
      return  
           string($Step)   
') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   Переменная `$Step` является переменной-итератором.  
  
-   [Выражение пути](../xquery/path-expressions-xquery.md), `//AWMI:root/AWMI:Location[1]/AWMI:step`, формирует входную последовательность. Эта последовательность является последовательность <`step`> элементные узлы-потомки первого <`Location`> элементного узла.  
  
-   Необязательное предложение-предикат `where` не указано.  
  
-   `return` Выражение возвращает значение строки из <`step`> элемента.  
  
 [Функция string (XQuery)](../xquery/data-accessor-functions-string-xquery.md) используется для получения строкового значения <`step`> узла.  
  
 Частичный результат:  
  
```  
Insert aluminum sheet MS-2341 into the T-85A framing tool.   
Attach Trim Jig TJ-26 to the upper and lower right corners of   
the aluminum sheet. ....         
```  
  
 Ниже приведены примеры других допустимых входных последовательностей:  
  
```sql
declare @x xml  
set @x=''  
SELECT @x.query('  
for $a in (1, 2, 3)  
  return $a')  
-- result = 1 2 3   
  
declare @x xml  
set @x=''  
SELECT @x.query('  
for $a in   
   for $b in (1, 2, 3)  
      return $b  
return $a')  
-- result = 1 2 3  
  
declare @x xml  
set @x='<ROOT><a>111</a></ROOT>'  
SELECT @x.query('  
  for $a in (xs:string( "test"), xs:double( "12" ), data(/ROOT/a ))  
  return $a')  
-- result test 12 111  
```  
  
 В [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] разнородные последовательности не допускаются. В частности, недопустимы последовательности, содержащие и атомарные значения, и узлы.  
  
 Итерация часто применяется вместе с [конструкции XML](../xquery/xml-construction-xquery.md) синтаксис в трансформирующих XML-форматах, как показано в следующем запросе.  
  
 В образце базы данных AdventureWorks производственные инструкции хранятся в **инструкции** столбец **Production.ProductModel** таблица имеет следующую форму:  
  
```xml
<Location LocationID="10" LaborHours="1.2"   
            SetupHours=".2" MachineHours=".1">  
  <step>describes 1st manu step</step>  
   <step>describes 2nd manu step</step>  
   ...  
</Location>  
...  
```  
  
 Следующий запрос формирует новый XML <`Location`> элементы с работой по центру атрибутами цеха в качестве дочерних элементов:  
  
```xml
<Location>  
   <LocationID>10</LocationID>  
   <LaborHours>1.2</LaborHours>  
   <SetupHours>.2</SetupHours>  
   <MachineHours>.1</MachineHours>  
</Location>  
...  
```  
  
 Запрос является таковым:  
  
```sql
SELECT Instructions.query('  
     declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
        for $WC in /AWMI:root/AWMI:Location  
        return  
          <Location>  
            <LocationID> { data($WC/@LocationID) } </LocationID>  
            <LaborHours>   { data($WC/@LaborHours) }   </LaborHours>  
            <SetupHours>   { data($WC/@SetupHours) }   </SetupHours>  
            <MachineHours> { data($WC/@MachineHours) } </MachineHours>  
          </Location>  
') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   Инструкция FLWOR получает последовательность <`Location`> элементы для определенного продукта.  
  
-   [Функция data (XQuery)](../xquery/data-accessor-functions-data-xquery.md) используется для извлечения значения каждого атрибута, поэтому они будут добавлены в результирующем XML как текстовые узлы, а не как атрибуты.  
  
-   Выражение в предложении RETURN конструирует требуемый XML-документ.  
  
 Частичный результат:  
  
```xml
<Location>  
  <LocationID>10</LocationID>  
  <LaborHours>2.5</LaborHours>  
  <SetupHours>0.5</SetupHours>  
  <MachineHours>3</MachineHours>  
</Location>  
<Location>  
   ...  
<Location>  
...  
```  
  
## <a name="using-the-let-clause"></a>Использование предложения let  
 Предложение `let` может быть использовано для именования повторяющихся выражений, на которые можно ссылаться с помощью ссылок на переменные. Выражение, присвоенное переменной `let`, будет вставляться в запрос каждый раз, когда эта переменная будет упоминаться в запросе. Это означает, что инструкция будет выполнена столько раз, сколько было ссылок на выражение.  
  
 В производственных инструкциях в базе данных [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] хранятся сведения о необходимых инструментах и о местах их применения. В следующем запросе, чтобы составить список инструментов, необходимых для постройки производственной модели, а также мест, где будет нужен каждый инструмент, применяется предложение `let`.  
  
```sql
SELECT Instructions.query('  
     declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
        for $T in //AWMI:tool  
            let $L := //AWMI:Location[.//AWMI:tool[.=data($T)]]  
        return  
          <tool desc="{data($T)}" Locations="{data($L/@LocationID)}"/>  
') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
## <a name="using-the-where-clause"></a>Применение предложения where  
 Можно использовать `where` предложение для фильтрации результатов итерации. Это продемонстрировано в следующем примере.  
  
 При изготовлении велосипеда производственный процесс проходит через цепочку цехов. Для каждого цеха определена последовательность производственных операций. Следующий запрос получает только те цеха, которые занимаются изготовлением модели велосипеда и включают менее трех производственных операций, То есть они содержат менее трех <`step`> элементы.  
  
```sql
SELECT Instructions.query('  
     declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
for $WC in /AWMI:root/AWMI:Location  
      where count($WC/AWMI:step) < 3  
      return  
          <Location >  
           { $WC/@LocationID }   
          </Location>  
') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
 При рассмотрении предыдущего запроса необходимо отметить следующее.  
  
-   `where` Использует ключевое слово **count()** функцию для подсчета числа <`step`> дочерних элементов каждого цеха.  
  
-   Выражение `return` конструирует XML-документ на основании результатов итерации.  
  
 Это результат:  
  
```  
<Location LocationID="30"/>   
```  
  
 Результат выражения в предложении `where` преобразуется в логическое значение по описанным ниже правилам (в указанном порядке). Это те же правила, которые применяются к предикатам в выражениях пути, за исключением того, что в данном случае целочисленные значения недопустимы.  
  
1.  Если выражение `where` возвращает пустую последовательность, действительное логическое значение равно False.  
  
2.  Если выражение `where` возвращает одно значение простого логического типа, результатом является это действительное логическое значение.  
  
3.  Если выражение `where` возвращает последовательность, в которой содержится хотя бы один узел, действительное логическое значение равно True.  
  
4.  В остальных случаях выдается статическая ошибка.  
  
## <a name="multiple-variable-binding-in-flwor"></a>Множественная привязка переменных в инструкции FLWOR  
 В одном выражении инструкции FLWOR можно привязывать к входным последовательностям несколько переменных. В следующем примере выполняется запрос к нетипизированной переменной типа xml. Выражение FLOWR возвращает первый <`Step`> дочерний элемент в каждом <`Location`> элемента.  
  
```sql
declare @x xml  
set @x='<ManuInstructions ProductModelID="1" ProductModelName="SomeBike" >  
<Location LocationID="L1" >  
  <Step>Manu step 1 at Loc 1</Step>  
  <Step>Manu step 2 at Loc 1</Step>  
  <Step>Manu step 3 at Loc 1</Step>  
</Location>  
<Location LocationID="L2" >  
  <Step>Manu step 1 at Loc 2</Step>  
  <Step>Manu step 2 at Loc 2</Step>  
  <Step>Manu step 3 at Loc 2</Step>  
</Location>  
</ManuInstructions>'  
SELECT @x.query('  
   for $Loc in /ManuInstructions/Location,  
       $FirstStep in $Loc/Step[1]  
   return   
       string($FirstStep)  
')  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   `for` Выражение определяет `$Loc` и $`FirstStep` переменные.  
  
-   `two` Выражения, `/ManuInstructions/Location` и `$FirstStep in $Loc/Step[1]`, являются коррелируются, значения `$FirstStep` зависят от значения `$Loc`.  
  
-   Выражение, связанное с `$Loc` формирует последовательность <`Location`> элементы. Для каждого <`Location`> элемент, `$FirstStep` формирует последовательность из одного <`Step`> элемент, одноэлементное множество.  
  
-   переменная `$Loc` указана в выражении, связанном с переменной `$FirstStep`.  
  
 Это результат:  
  
```  
Manu step 1 at Loc 1   
Manu step 1 at Loc 2  
```  
  
 Следующий запрос аналогичен, за исключением того, что он указан для столбца Instructions, типизированного **xml** столбца, из **ProductModel** таблицы. [Построение XML (XQuery)](../xquery/xml-construction-xquery.md) используется для создания XML-документ.  
  
```sql
SELECT Instructions.query('  
     declare default element namespace "https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
for $WC in /root/Location,  
            $S  in $WC/step  
      return  
          <Step LocationID= "{$WC/@LocationID }" >  
            { $S/node() }  
          </Step>  
') as Result  
FROM  Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 При рассмотрении предыдущего запроса необходимо отметить следующее.  
  
-   Предложение `for` определяет две переменные: `$WC` и `$S`. Выражение, связанное с `$WC`, формирует последовательность цехов, участвующих в производстве велосипедов. Выражение пути, присвоенное переменной `$S`, формирует последовательность операций для каждого цеха, содержащегося в переменной `$WC`.  
  
-   Инструкция return конструирует XML, который содержит <`Step`> элемент, содержащий этап производства и **LocationID** атрибут.  
  
-   **Объявить пространство имен по умолчанию элемент** используется в прологе XQuery так, чтобы отображались все объявления пространства имен в результирующем XML элементом верхнего уровня. Это повышает удобочитаемость результата. Дополнительные сведения о пространствах имен по умолчанию см. в разделе [обработка пространств имен в XQuery](../xquery/handling-namespaces-in-xquery.md).  
  
 Частичный результат:  
  
```xml
<Step xmlns=  
    "https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"     
  LocationID="10">  
     Insert <material>aluminum sheet MS-2341</material> into the <tool>T-   
     85A framing tool</tool>.   
</Step>  
...  
<Step xmlns=  
      "https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"     
    LocationID="20">  
        Assemble all frame components following blueprint   
        <blueprint>1299</blueprint>.  
</Step>  
...  
```  
  
## <a name="using-the-order-by-clause"></a>Применение предложения order by  
 В языке XQuery сортировка в выражении FLWOR выполняется с помощью предложения `order by`. Сортируемые выражения, передаваемый `order by` предложение должны возвращать значения, типы которых допустимы для **gt** оператор. Каждое сортируемое выражение должно возвращать последовательность, состоящую из одного элемента. По умолчанию сортировка выполняется в порядке возрастания. Для каждого из сортируемых выражений можно указать сортировку по возрастанию или по убыванию.  
  
> [!NOTE]  
>  При сортировке сравнение символьных значений, выполняемых реализацией языка XQuery в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], всегда выполняется с использованием параметров сортировки двоичных элементов кода Юникода.  
  
 Следующий запрос получает все телефонные номера указанного заказчика из столбца AdditionalContactInfo. Результат сортируется по номеру телефона.  
  
```sql
USE AdventureWorks2012;  
GO  
SELECT AdditionalContactInfo.query('  
   declare namespace act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
   declare namespace aci="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";  
   for $a in /aci:AdditionalContactInfo//act:telephoneNumber   
   order by $a/act:number[1] descending  
   return $a  
') As Result  
FROM Person.Person  
WHERE BusinessEntityID=291;  
```  
  
 Обратите внимание, что [атомизация (XQuery)](../xquery/atomization-xquery.md) процесс получает атомарное значение элемента <`number`> элементы перед их передачей `order by`. Можно написать выражение, используя **data()** функции, но это не является обязательным.  
  
```  
order by data($a/act:number[1]) descending  
```  
  
 Это результат:  
  
```xml
<act:telephoneNumber xmlns:act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">  
  <act:number>333-333-3334</act:number>  
</act:telephoneNumber>  
<act:telephoneNumber xmlns:act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">  
  <act:number>333-333-3333</act:number>  
</act:telephoneNumber>  
```  
  
 Вместо объявления пространства имен в прологе запроса можно объявить его с помощью предложения WITH XMLNAMESPACES.  
  
```sql
WITH XMLNAMESPACES (  
   'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes' AS act,  
   'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo'  AS aci)  
  
SELECT AdditionalContactInfo.query('  
   for $a in /aci:AdditionalContactInfo//act:telephoneNumber   
   order by $a/act:number[1] descending  
   return $a  
') As Result  
FROM Person.Person  
WHERE BusinessEntityID=291;  
```  
  
 Сортировка может также выполняться по значению атрибута. Например, следующий запрос получает вновь созданные <`Location`> элементов, которые имеют атрибуты LocationID и LaborHours, отсортированных по атрибуту LaborHours в убывающем порядке. В результате цеха, имеющие максимальное число рабочих часов, будут возвращены первыми.  
  
```sql
SELECT Instructions.query('  
     declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
for $WC in /AWMI:root/AWMI:Location   
order by $WC/@LaborHours descending  
        return  
          <Location>  
             { $WC/@LocationID }   
             { $WC/@LaborHours }   
          </Location>  
') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7;  
```  
  
 Это результат:  
  
```  
<Location LocationID="60" LaborHours="4"/>  
<Location LocationID="50" LaborHours="3"/>  
<Location LocationID="10" LaborHours="2.5"/>  
<Location LocationID="20" LaborHours="1.75"/>  
<Location LocationID="30" LaborHours="1"/>  
<Location LocationID="45" LaborHours=".5"/>  
```  
  
 В следующем запросе результат сортируется по имени элемента. Запрос получает характеристики указанного продукта из каталога продукции. Характеристики являются дочерними элементами элемента <`Specifications`> элемента.  
  
```sql
SELECT CatalogDescription.query('  
     declare namespace  
 pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
      for $a in /pd:ProductDescription/pd:Specifications/*   
     order by local-name($a)  
      return $a  
    ') as Result  
FROM Production.ProductModel  
where ProductModelID=19;  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   `/p1:ProductDescription/p1:Specifications/*` Выражение возвращает дочерние элементы <`Specifications`>.  
  
-   Выражение `order by (local-name($a))` сортирует последовательность по локальной части имени элемента.  
  
 Это результат:  
  
```xml
<Color>Available in most colors</Color>  
<Material>Almuminum Alloy</Material>  
<ProductLine>Mountain bike</ProductLine>  
<RiderExperience>Advanced to Professional riders</RiderExperience>  
<Style>Unisex</Style>    
```  
  
 Узлы, в которых сортируемые выражения возвращают пустую последовательность, будут помещены в начало, как показано в следующем примере:  
  
```sql
declare @x xml  
set @x='<root>  
  <Person Name="A" />  
  <Person />  
  <Person Name="B" />  
</root>  
'  
select @x.query('  
  for $person in //Person  
  order by $person/@Name  
  return   $person  
')  
```  
  
 Это результат:  
  
```xml
<Person />  
<Person Name="A" />  
<Person Name="B" />  
```  
  
 Следующий пример показывает, каким образом можно указать несколько критериев сортировки. В этом примере запрос сортирует <`Employee`> элементы сначала по названию, а затем администратором значений атрибутов.  
  
```sql
declare @x xml  
set @x='<root>  
  <Employee ID="10" Title="Teacher"        Gender="M" />  
  <Employee ID="15" Title="Teacher"  Gender="F" />  
  <Employee ID="5" Title="Teacher"         Gender="M" />  
  <Employee ID="11" Title="Teacher"        Gender="F" />  
  <Employee ID="8" Title="Administrator"   Gender="M" />  
  <Employee ID="4" Title="Administrator"   Gender="F" />  
  <Employee ID="3" Title="Teacher"         Gender="F" />  
  <Employee ID="125" Title="Administrator" Gender="F" /></root>'  
SELECT @x.query('for $e in /root/Employee  
order by $e/@Title ascending, $e/@Gender descending  
  
  return  
     $e  
')  
```  
  
 Это результат:  
  
```xml
<Employee ID="8" Title="Administrator" Gender="M" />  
<Employee ID="4" Title="Administrator" Gender="F" />  
<Employee ID="125" Title="Administrator" Gender="F" />  
<Employee ID="10" Title="Teacher" Gender="M" />  
<Employee ID="5" Title="Teacher" Gender="M" />  
<Employee ID="11" Title="Teacher" Gender="F" />  
<Employee ID="15" Title="Teacher" Gender="F" />  
<Employee ID="3" Title="Teacher" Gender="F" />  
```  
  
### <a name="implementation-limitations"></a>Ограничения реализации  
 Существуют следующие ограничения:  
  
-   Сортируемые выражения должны быть однородно типизированы. Эта проверка выполняется статически.  
  
-   Нельзя управлять сортировкой пустых последовательностей.  
  
-   Ключевые слова empty least, empty greatest и collation в выражении `order by` не поддерживаются.  
  
## <a name="see-also"></a>См. также  
 [Выражения XQuery](../xquery/xquery-expressions.md)  
  
  
