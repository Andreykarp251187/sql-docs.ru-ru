---
title: Пример. Указание директивы XMLTEXT | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- XMLTEXT directive
ms.assetid: e78008ec-51e8-4fd1-b86f-1058a781de17
author: rothja
ms.author: jroth
ms.openlocfilehash: 541e214399a0f91c63c5cf053f5a99dafe9fb837
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85013336"
---
# <a name="example-specifying-the-xmltext-directive"></a>Пример. Указание директивы XMLTEXT
  Этот пример иллюстрирует, как при помощи директивы `XMLTEXT` в инструкции `SELECT`, использующей режим EXPLICIT, осуществляется обращение к данным столбца Overflow.  
  
 Рассмотрим таблицу `Person` . В этой таблице имеется столбец `Overflow` , в котором хранится неиспользуемая часть XML-документа.  
  
```  
USE tempdb;  
GO  
CREATE TABLE Person(PersonID varchar(5), PersonName varchar(20), Overflow nvarchar(200));  
GO  
INSERT INTO Person VALUES   
    ('P1','Joe',N'<SomeTag attr1="data">content</SomeTag>')  
   ,('P2','Joe',N'<SomeTag attr2="data"/>')  
   ,('P3','Joe',N'<SomeTag attr3="data" PersonID="P">content</SomeTag>');  
```  
  
 Этот запрос извлекает столбцы из таблицы `Person` . Для столбца `Overflow` значение *AttributeName* не задано, но значение *directive* установлено в `XMLTEXT` как часть, предоставляющая имя столбца универсальной таблицы.  
  
```  
SELECT 1 as Tag, NULL as parent,  
       PersonID as [Parent!1!PersonID],  
       PersonName as [Parent!1!PersonName],  
       Overflow as [Parent!1!!XMLTEST] -- No AttributeName; XMLTEXT directive  
FROM Person  
FOR XML EXPLICIT;  
```  
  
 В результирующем XML-документе:  
  
-   Так как значение *AttributeName* для столбца `Overflow` не указано, а директива `xmltext` указана, атрибуты элемента <`overflow`> добавляются в список атрибутов содержащего его элемента <`Parent`>.  
  
-   Так как атрибут `PersonID` элемента <`xmltext`> конфликтует с атрибутом `PersonID`, извлеченным на том же уровне элемента, атрибут элемента <`xmltext`> не учитывается, даже если `PersonID` имеет значение NULL. Обычно атрибут замещает атрибут с тем же именем при переполнении.  
  
 Результат:  
  
 `<Parent PersonID="P1" PersonName="Joe" attr1="data">content</Parent>`  
  
 `<Parent PersonID="P2" PersonName="Joe" attr2="data"></Parent>`  
  
 `<Parent PersonID="P3" PersonName="Joe" attr3="data">content</Parent>`  
  
 Если элементы Overflow имеют вложенные элементы и указан тот же запрос, вложенные элементы в столбце `Overflow` добавляются как вложенные элементы содержащего его элемента <`Parent`>.  
  
 Например, можно изменить данные в таблице `Person` так, чтобы столбец `Overflow` имел вложенные элементы.  
  
```  
USE tempdb;  
GO  
TRUNCATE TABLE Person;  
GO  
INSERT INTO Person VALUES   
    ('P1','Joe',N'<SomeTag attr1="data">content</SomeTag>')  
   ,('P2','Joe',N'<SomeTag attr2="data"/>')  
    ,('P3','Joe',N'<SomeTag attr3="data" PersonID="P"><name>PersonName</name></SomeTag>');  
```  
  
 Если выполнен тот же запрос, вложенные элементы элемента <`xmltext`> добавляются как вложенные элементы содержащего его элемента <`Parent`>:  
  
```  
SELECT 1 as Tag, NULL as parent,  
       PersonID as [Parent!1!PersonID],  
       PersonName as [Parent!1!PersonName],  
       Overflow as [Parent!1!!XMLTEXT] -- no AttributeName, XMLTEXT directive  
FROM Person  
FOR XML EXPLICIT;  
```  
  
 Результат:  
  
 `<Parent PersonID="P1" PersonName="Joe" attr1="data">content</Parent>`  
  
 `<Parent PersonID="P2" PersonName="Joe" attr2="data"></Parent>`  
  
 `<Parent PersonID="P3" PersonName="Joe" attr3="data">`  
  
 `<name>PersonName</name>`  
  
 `</Parent>`  
  
 Если указано значение *AttributeName* вместе с директивой `xmltext`, атрибуты элемента <`overflow`> добавляются как атрибуты вложенных элементов содержащего его элемента <`Parent`>. Имя, указанное для *attributeName* , преобразуется в имя подэлемента.  
  
 В этом запросе, *attributeName*, <`overflow`>, указывается вместе с `xmltext` директивой:  
  
```  
SELECT 1 as Tag, NULL as parent,  
       PersonID as [Parent!1!PersonID],  
       PersonName as [Parent!1!PersonName],  
       Overflow as [Parent!1!overflow!XMLTEXT] -- Overflow is AttributeName  
                      -- XMLTEXT is a directive  
FROM Person  
FOR XML EXPLICIT  
```  
  
 Результат:  
  
 `<Parent PersonID="P1" PersonName="Joe">`  
  
 `<overflow attr1="data">content</overflow>`  
  
 `</Parent>`  
  
 `<Parent PersonID="P2" PersonName="Joe">`  
  
 `<overflow attr2="data" />`  
  
 `</Parent>`  
  
 `<Parent PersonID="P3" PersonName="Joe">`  
  
 `<overflow attr3="data" PersonID="P">`  
  
 `<name>PersonName</name>`  
  
 `</overflow>`  
  
 `</Parent>`  
  
 В этом элементе запроса значение *directive* задано для атрибута `PersonName` . Это приводит к тому, что элемент `PersonName` добавляется в качестве вложенного элемента в содержащий его элемент <`Parent`>. Атрибуты <`xmltext`> все так же добавляются к окружению элемента <`Parent`>. Содержание элемента <`overflow`> и вложенные элементы добавляются в начало других вложенных элементов содержащих их элементов <`Parent`>.  
  
```  
SELECT 1      AS Tag, NULL as parent,  
       PersonID   AS [Parent!1!PersonID],  
       PersonName AS [Parent!1!PersonName!element], -- element directive  
       Overflow   AS [Parent!1!!XMLTEXT]  
FROM Person  
FOR XML EXPLICIT;  
```  
  
 Результат:  
  
 `<Parent PersonID="P1" attr1="data">content<PersonName>Joe</PersonName>`  
  
 `</Parent>`  
  
 `<Parent PersonID="P2" attr2="data">`  
  
 `<PersonName>Joe</PersonName>`  
  
 `</Parent>`  
  
 `<Parent PersonID="P3" attr3="data">`  
  
 `<name>PersonName</name>`  
  
 `<PersonName>Joe</PersonName>`  
  
 `</Parent>`  
  
 Если в данных столбца `XMLTEXT` содержатся атрибуты корневого элемента, эти атрибуты не показываются в XML-схеме данных, а средство синтаксического анализа MSXML не проверяет результирующий фрагмент XML-документа. Пример:  
  
```  
SELECT 1 AS Tag,  
       0 ASParent,  
       N'<overflow a="1"/>' AS 'overflow!1!!xmltext'  
FOR XML EXPLICIT, xmldata;  
```  
  
 Результат. Обратите внимание, что в возвращаемой схеме атрибут переполнения `a` отсутствует:  
  
 `<Schema name="Schema2"`  
  
 `xmlns="urn:schemas-microsoft-com:xml-data"`  
  
 `xmlns:dt="urn:schemas-microsoft-com:datatypes">`  
  
 `<ElementType name="overflow" content="mixed" model="open">`  
  
 `</ElementType>`  
  
 `</Schema>`  
  
 `<overflow xmlns="x-schema:#Schema2" a="1">`  
  
 `</overflow>`  
  
## <a name="see-also"></a>См. также:  
 [Использование режима EXPLICIT с предложением FOR XML](use-explicit-mode-with-for-xml.md)  
  
  
