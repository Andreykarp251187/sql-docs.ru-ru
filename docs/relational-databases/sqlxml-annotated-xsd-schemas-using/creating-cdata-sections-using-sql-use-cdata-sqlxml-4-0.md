---
title: Создание разделов CDATA с использованием sql:use-cdata (S'LXML)
description: Узнайте, как создать разделы CDATA в s'LXML 4.0, используя аннотацию sql:use-cdata, чтобы избежать блоков текста, содержащих символы разметки.
ms.date: 01/11/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- markup characters [SQLXML]
- special characters [SQLXML]
- use-cdata annotation
- plain text [SQLXML]
- CDATA sections
- escaping blocks of text [SQLXML]
- annotated XSD schemas, CDATA sections
- sql:use-cdata
ms.assetid: 26d2b9dc-f857-44ff-bcd4-aaf64ff809d0
author: MightyPen
ms.author: genemi
ms.reviewer: ''
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: aa359c1c1e855c3652d7c6486d3993f588bae46d
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388194"
---
# <a name="creating-cdata-sections-using-sqluse-cdata-sqlxml-40"></a>Создание разделов CDATA с использованием sql:use-cdata (SQLXML 4.0)

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  В XML разделы CDATA используются для экранирования блоков текста, содержащих символы, которые в противном случае распознаются как символы разметки.  
  
 База данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в корпорации Майкрософт иногда может содержать символы, которые рассматриваются как символы разметки с помощью парора XML; например, угловые скобки (< и >), символ меньше, чем или равный символ (<q) и амперсанд (&) рассматриваются как символы разметки. Но специальные символы такого типа можно заключить в раздел CDATA во избежание их обработки в качестве символов разметки. Текст в разделе CDATA обрабатывается средством синтаксического анализа XML как простой текст.  
  
 Аннотация **sql:use-cdata** используется для указания того, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] что возвращенные данные должны быть завернуты в раздел CDATA (т.е. указывается, следует ли приклеивать значение из столбца, указанного **sql:field).** Аннотация **sql:использование-cdata** может быть указана только на элементах, которые отображают на столбце базы данных.  
  
 **Sql: Аннотация использования-кданных** занимает значение Boolean (0 - ложный, 1 - правда). Допустимые значения: 0, 1, true и false.  
  
 Эта аннотация не может быть использована с типами **атрибутов sql:url-код или** на ID, IDREF, IDREFS, NMTOKEN и NMTOKENS.  
  
## <a name="examples"></a>Примеры  
 Чтобы создать рабочие образцы на основе следующих примеров, необходимо выполнить определенные требования. Для получения дополнительной информации [см.](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md)  
  
### <a name="a-specifying-sqluse-cdata-on-an-element"></a>A. Указание заметки sql:use-cdata для элемента  
 В следующей **схеме, sql:использование-cdata** устанавливается на 1 (Правда) для ** \<AddressLine1>** в ** \<элементе Адрес>.** В результате этого данные возвращаются в разделе CDATA.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Address"   
               sql:relation="Person.Address"   
               sql:key-fields="AddressID" >  
   <xsd:complexType>  
        <xsd:sequence>  
          <xsd:element name="AddressID"  type="xsd:string" />  
          <xsd:element name="AddressLine1" type="xsd:string"   
                       sql:use-cdata="1" />  
        </xsd:sequence>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Проверка образца запроса XPath к схеме  
  
1.  Скопируйте приведенный выше код схемы и вставьте его в текстовый файл. Сохраните этот файл с именем UseCData.xml.  
  
2.  Скопируйте следующий шаблон и вставьте его в текстовый файл. Сохраните этот файл под именем UseCDataT.xml в том же каталоге, в котором был сохранен файл UseCData.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="UseCData.xml">  
            /Address[AddressID < 11]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Путь к каталогу схемы сопоставления (файл UseCData.xml) задается относительно каталога, в котором сохранен шаблон. Можно также задать абсолютный путь, например:  
  
    ```  
    mapping-schema="C:\SqlXmlTest\UseCData.xml"  
    ```  
  
3.  Создайте и запустите тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs), чтобы выполнить шаблон.  
  
     Для получения дополнительной [информации см.](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)  
  
 Ниже приведен частичный результирующий набор.  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
  <Address>   
    <AddressID>1</CustomerID>   
    <AddressLine1>   
      <![CDATA[ 1970 Napa Ct.  ]]>   
    </AddressLine1>   
  </Address>  
  <Address>  
    <AddressLine1>   
      <![CDATA[ 9833 Mt. Dias Blv. ]]>   
    </AddressLine1>   
  </Address>  
  ...  
</ROOT>  
```  
  
  
