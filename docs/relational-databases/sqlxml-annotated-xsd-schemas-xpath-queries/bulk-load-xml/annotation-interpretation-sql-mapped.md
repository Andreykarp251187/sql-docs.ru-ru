---
title: 'SQL: mapped (SQLXML 4.0) | Документация Майкрософт'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- mapped annotation
- element mapping [SQLXML], XML Bulk Load
- attribute mapping [SQLXML], XML Bulk Load
- overflow data [SQLXML]
- sql:mapped
- column mapping [SQLXML]
ms.assetid: 7042741e-ce4d-4912-9c4a-d77194a028fc
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: aa5370e91aa5a8f5012a9c8f35f3fb98b3b3e726
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/05/2019
ms.locfileid: "67581914"
---
# <a name="annotation-interpretation---sqlmapped"></a>Интерпретация заметки — sql:mapped
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Массовая загрузка XML обрабатывает **sql: сопоставлены** является заметки в схемах XSD, ожидается, если схема сопоставления задает **sql: сопоставлены = «false»** для любого элемента или атрибута, Массовая загрузка XML не поддерживает Попытка сохранить связанные данные в соответствующем столбце.  
  
 Массовая загрузка XML пропускает элементы и атрибуты, которые не сопоставлены (поскольку они не описаны в схеме, или они помечены в схеме XSD с **sql: сопоставлены = «false»** ). Все несопоставленные данные попадают в столбце переполнения, если такой столбец задается с помощью **SQL: Overflow-поле**.  
  
 В качестве примера рассмотрим следующую схему XSD.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:element name="ROOT" sql:is-constant="1">  
<xsd:complexType>  
<xsd:sequence>  
  <xsd:element name="Customers" sql:relation="Cust"  
                                sql:overflow-field="OverflowColumn" >  
   <xsd:complexType>  
       <xsd:attribute name="CustomerID"  type="xsd:integer" />  
       <xsd:attribute name="CompanyName" type="xsd:string" />  
       <xsd:attribute name="City"        type="xsd:string" />  
       <xsd:attribute name="HomePhone"   type="xsd:string"   
                                       sql:mapped="false" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:sequence>  
</xsd:complexType>  
</xsd:element>  
</xsd:schema>  
```  
  
 Так как **HomePhone** атрибут задает **sql: сопоставлены = «false»** , Массовая загрузка XML не сопоставляет этот атрибут в соответствующий столбец. В схеме XSD определяется столбец переполнения (**OverflowColumn**) в который Массовая загрузка сохраняет невостребованные данные.  
  
### <a name="to-test-a-working-sample"></a>Проверка рабочего образца  
  
1.  Создайте следующую таблицу в **tempdb** базы данных:  
  
    ```  
    USE tempdb  
    CREATE TABLE Cust  
              (CustomerID     int         PRIMARY KEY,  
               CompanyName    varchar(20) NOT NULL,  
               City           varchar(20) DEFAULT 'Seattle',  
               OverflowColumn nvarchar(200))  
    GO  
    ```  
  
2.  Сохраните схему, приведенную в этом примере, в файле SampleSchema.xml.  
  
3.  Сохраните следующий образец XML-данных в файле SampleXMLData.xml.  
  
    ```  
    <ROOT>  
      <Customers CustomerID="1111" CompanyName="Sean Chai"   
                 City="NY" HomePhone="111-1111" />  
      <Customers CustomerID="1112" CompanyName="Dont Know"   
                 City="LA" HomePhone="222-2222" />  
    </ROOT>  
    ```  
  
4.  Чтобы выполнить массовую загрузку XML-данных, сохраните этот пример на языке [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic Scripting Edition (VBScript) в файле Sample.vbs и выполните его.  

[!INCLUDE[freshInclude](../../../includes/paragraph-content/fresh-note-steps-feedback.md)]

    ```  
    set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
    objBL.ErrorLogFile = "c:\error.log"  
    objBL.CheckConstraints=True  
    objBL.Execute "c:\SampleSchema.xml", "c:\SampleXMLData.xml"  
    set objBL=Nothing  
    ```  
  
 Эквивалентная схема XDR:  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:sql="urn:schemas-microsoft-com:xml-sql" >   
   <ElementType name="ROOT" sql:is-constant="1">  
      <element type="Customers" />  
   </ElementType>  
   <ElementType name="Customers" sql:relation="Cust"  
                             sql:overflow-field="OverflowColumn" >  
      <AttributeType name="CustomerID" />  
      <AttributeType name="CompanyName"  />  
      <AttributeType name="City"  />  
      <AttributeType name="HomePhone" />  
      <attribute type="CustomerID"  />  
      <attribute type="CompanyName"  />  
      <attribute type="City" />  
      <attribute type="HomePhone" sql:map-field="0" />  
   </ElementType>  
</Schema>  
```  
  
  
