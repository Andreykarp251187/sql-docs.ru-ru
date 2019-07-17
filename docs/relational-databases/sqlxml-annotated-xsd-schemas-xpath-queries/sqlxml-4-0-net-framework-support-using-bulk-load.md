---
title: Использование массовой загрузки SQLXML в среде .NET | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, XML Bulk Load
- XML Bulk Load [SQLXML], .NET environment
- .NET Framework [SQLXML], XML Bulk Load
- bulk load [SQLXML], .NET environment
ms.assetid: b85df83b-ba56-43bf-bcdf-b2a6fca43276
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ed725ac58b7224ad157dd7b5d06b3b522395023b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68220388"
---
# <a name="sqlxml-40-net-framework-support---using-bulk-load"></a>Поддержка SQLXML 4.0 на платформе .NET Framework — использование массовой загрузки
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  В этом разделе объясняется, как можно использовать функциональность массовой загрузки XML в среде .NET. Подробные сведения о массовой загрузке XML см. в разделе [выполнении массовой загрузки XML-данных &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md).  
  
 Для использования объекта COM массовой загрузки SQLXML в управляемой среде необходимо добавить в этот объект ссылку на проект. Это сформирует управляемый интерфейс оболочки объекта массовой загрузки COM.  
  
> [!NOTE]  
>  Управляемая массовая загрузка XML не работает с управляемыми потоками и требует оболочки собственных потоков. Компонент массовой загрузки SQLXML не будет запущен в многопоточной среде (атрибут '[MTAThread]'). При попытке запустить компонент массовой загрузки в многопоточной среде, вы получаете исключение InvalidCastException со следующими дополнительными сведениями: «Ошибка QueryInterface для интерфейса SQLXMLBULKLOADLib.ISQLXMLBulkLoad». Обойти это можно сделать объект, содержащий Массовая загрузка объекта одним потоком доступ (например, с помощью **[STAThread]** атрибута, как показано в примере).  
  
 Этот раздел содержит образец реализации приложения на языке C# для массовой загрузки XML-данных в базу данных. Чтобы создать образец реализации, выполните следующие шаги.  
  
1.  Создайте следующие таблицы:  
  
    ```  
    CREATE TABLE Ord (  
             OrderID     int identity(1,1)  PRIMARY KEY,  
             CustomerID  varchar(5))  
    GO  
    CREATE TABLE Product (  
             ProductID   int identity(1,1) PRIMARY KEY,  
             ProductName varchar(20))  
    GO  
    CREATE TABLE OrderDetail (  
           OrderID     int FOREIGN KEY REFERENCES Ord(OrderID),  
           ProductID   int FOREIGN KEY REFERENCES Product(ProductID),  
                       CONSTRAINT OD_key PRIMARY KEY (OrderID, ProductID))  
    GO  
    ```  
  
2.  Сохраните в файле (schema.xml) следующую схему:  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
    <xsd:annotation>  
      <xsd:appinfo>  
        <sql:relationship name="OrderOD"  
              parent="Ord"  
              parent-key="OrderID"  
              child="OrderDetail"  
              child-key="OrderID" />  
  
        <sql:relationship name="ODProduct"  
              parent="OrderDetail"  
              parent-key="ProductID"  
              child="Product"  
              child-key="ProductID"   
              inverse="true"/>  
      </xsd:appinfo>  
    </xsd:annotation>  
  
      <xsd:element name="Order" sql:relation="Ord"   
                                sql:key-fields="OrderID" >  
       <xsd:complexType>  
         <xsd:sequence>  
            <xsd:element name="Product" sql:relation="Product"   
                         sql:key-fields="ProductID"  
                         sql:relationship="OrderOD ODProduct">  
              <xsd:complexType>  
                 <xsd:attribute name="ProductID" type="xsd:int" />  
                 <xsd:attribute name="ProductName" type="xsd:string" />  
              </xsd:complexType>  
            </xsd:element>  
         </xsd:sequence>  
            <xsd:attribute name="OrderID"   type="xsd:integer" />   
            <xsd:attribute name="CustomerID"   type="xsd:string" />  
        </xsd:complexType>  
      </xsd:element>  
    </xsd:schema>  
    ```  
  
3.  Сохраните в файле (data.xml) следующий образец XML-документа:  
  
    ```  
    <ROOT>    
      <Order OrderID="11" CustomerID="ALFKI">  
        <Product ProductID="11" ProductName="Chai" />  
        <Product ProductID="22" ProductName="Chang" />  
      </Order>  
      <Order OrderID="22" CustomerID="ANATR">  
         <Product ProductID="33" ProductName="Aniseed Syrup" />  
        <Product ProductID="44" ProductName="Gumbo Mix" />  
      </Order>  
    </ROOT>  
    ```  
  
4.  Запустите среду Visual Studio.  
  
5.  Создайте приложение командной строки на языке C#.  
  
6.  Из **проекта** меню, выберите **добавить ссылку**.  
  
7.  В **COM** выберите **тип массовой загрузки SQLXML 4.0 библиотеке** (xblkld4.dll) и нажмите кнопку **ОК**. Вы увидите **Interop.SQLXMLBULKLOADLib** сборке, созданной в проекте.  
  
8.  Замените метод Main() на следующий код. Обновление **ConnectionString** свойство и путь к файлу в файлы схемы и данных.  
  
    ```  
    [STAThread]  
       static void Main(string[] args)  
       {     
             try  
             {  
                SQLXMLBULKLOADLib.SQLXMLBulkLoad4Class objBL = new SQLXMLBULKLOADLib.SQLXMLBulkLoad4Class();  
                objBL.ConnectionString = "Provider=sqloledb;server=server;database=databaseName;integrated security=SSPI";  
                objBL.ErrorLogFile = "error.xml";  
                objBL.KeepIdentity = false;  
                objBL.Execute ("schema.xml","data.xml");  
             }  
             catch(Exception e)  
             {  
             Console.WriteLine(e.ToString());  
             }  
       }  
    ```  
  
9. Для загрузки XML в создаваемую таблицу постройте и запустите проект.  
  
    > [!NOTE]  
    >  Ссылку на компонент массовой загрузки (xblkld4.dll) можно также добавить при помощи средства tlbimp.exe, которое доступно как часть платформы .NET Framework. Это средство создает управляемую оболочку для собственной DLL-библиотеки (xblkld4.dll), которую затем можно использовать в любом проекте .NET. Пример:  
  
    ```  
    c:\>tlbimp xblkld4.dll  
    ```  
  
     Это средство создает DLL-библиотеку управляемой оболочки (SQLXMLBULKLOADLib.dll), которую можно использовать в проекте платформы .NET Framework. В .NET Framework ссылка на проект добавляется к вновь созданной DLL-библиотеке.  
  
## <a name="see-also"></a>См. также  
 [Выполнение массовой загрузки XML-данных &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md)  
  
  
