---
title: Использование XML в вычисляемых столбцах | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- computed columns, XML
- XML [SQL Server], computed columns
ms.assetid: 1313b889-69b4-4018-9868-0496dd83bf44
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a90f68a55b10234e0397aba480b8d78a9cea1d9c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68039119"
---
# <a name="use-xml-in-computed-columns"></a>Использование XML в вычисляемых столбцах
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Экземпляры XML могут встречаться в исходных данных для вычисляемого столбца и могут быть типом значений вычисляемого столбца. Примеры в этом разделе демонстрируют использование XML в вычисляемых столбцах.  
  
## <a name="creating-computed-columns-from-xml-columns"></a>Создание вычисляемых столбцов из XML-столбцов  
 В следующей инструкции `CREATE TABLE` столбец типа `xml` (`col2`) вычисляется из столбца `col1`:  
  
```  
CREATE TABLE T(col1 varchar(max), col2 AS CAST(col1 AS xml) )    
```  
  
 Тип данных `xml` может присутствовать в исходных данных при создании вычисляемого столбца, что демонстрирует следующая инструкция `CREATE TABLE` :  
  
```  
CREATE TABLE T (col1 xml, col2 as cast(col1 as varchar(1000) ))   
```  
  
 Пример создания вычисляемого столбца, получающего значение из столбца типа `xml` , приводится ниже. Так как методы типа данных **xml** нельзя прямо использовать при создании вычисляемых столбцов, в примере сначала определяется функция (`my_udf`), возвращающая значение для экземпляра XML. Функция является интерфейсом к методу `value()` типа `xml` . Имя функции затем указывается в инструкции `CREATE TABLE` в части, соответствующей вычисляемому столбцу.  
  
```  
CREATE FUNCTION my_udf(@var xml) returns int  
AS BEGIN   
RETURN @var.value('(/ProductDescription/@ProductModelID)[1]' , 'int')  
END  
GO  
-- Use the function in CREATE TABLE.  
CREATE TABLE T (col1 xml, col2 as dbo.my_udf(col1) )  
GO  
-- Try adding a row.   
INSERT INTO T values('<ProductDescription ProductModelID="1" />')  
GO  
-- Verify results.  
SELECT col2, col1  
FROM T  
  
```  
  
 Как и в предыдущем примере, в этом примере определяется функция, возвращающая экземпляр типа **xml** для вычисляемого столбца. В функции вызывается метод `query()` типа данных `xml` , получающий значение из параметра типа `xml` .  
  
```  
CREATE FUNCTION my_udf(@var xml)   
  RETURNS xml AS   
BEGIN   
   RETURN @var.query('ProductDescription/Features')  
END  
```  
  
 В следующей инструкции `CREATE TABLE` столбец `Col2` является вычисляемым столбцом, использующим XML-данные (элемент`<Features>` ), возвращаемые функцией:  
  
```  
CREATE TABLE T (Col1 xml, Col2 as dbo.my_udf(Col1) )  
-- Insert a row in table T.  
INSERT INTO T VALUES('  
<ProductDescription ProductModelID="1" >  
  <Features>  
    <Feature1>description</Feature1>  
    <Feature2>description</Feature2>  
  </Features>  
</ProductDescription>')  
-- Verify the results.  
SELECT *  
FROM T  
```  
  
### <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Продвижение часто используемых XML-значений с помощью вычисляемых столбцов](../../relational-databases/xml/promote-frequently-used-xml-values-with-computed-columns.md)|Описывает использование продвижения свойств в вычисляемых столбцах и таблицах свойств.|  
  
  
