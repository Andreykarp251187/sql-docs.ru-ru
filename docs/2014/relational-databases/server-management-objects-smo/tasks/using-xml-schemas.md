---
title: Использование схем XML | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- XML [SMO]
ms.assetid: 9d04de01-efeb-4b2d-8c28-3234bc7ff2f3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f65643152bb069c703fe3a63e58ad669f3d3e322
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62626867"
---
# <a name="using-xml-schemas"></a>Использование схем XML
  Программирование XML в SMO ограничено предоставлением типов данных XML, пространств имен XML и простым индексированием по столбцам данных XML.  
  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] предоставляет собственный формат хранения для экземпляров XML-документов. Схемы XML позволяют определять сложные типы данных XML, которые можно использовать для проверки XML-документов с целью обеспечения целостности данных. Схема XML определяется в объекте <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection>.  
  
## <a name="example"></a>Пример  
 Чтобы использовать какой-либо из представленных примеров кода, нужно выбрать среду, шаблон и язык программирования, с помощью которых будет создаваться приложение. Дополнительные сведения см. в разделе [Создание проекта SMO на Visual Basic в Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) или [Visual C создайте&#35; проекта SMO в Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-an-xml-schema-in-visual-basic"></a>Создание схемы XML на языке Visual Basic  
 В этом примере кода показано создание схемы XML с помощью объекта <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection>. Свойство <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection.Text%2A>, определяющее коллекцию схем XML, содержит несколько двойных кавычек. Они заменяются строкой `chr(34)` .  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBXMLSchema1](SMO How to#SMO_VBXMLSchema1)]  -->  
  
## <a name="creating-an-xml-schema-in-visual-c"></a>Создание схемы XML на языке Visual C#  
 В этом примере кода показано создание схемы XML с помощью объекта <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection>. Свойство <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection.Text%2A>, определяющее коллекцию схем XML, содержит несколько двойных кавычек. Они заменяются строкой `chr(34)` .  
  
```  
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv = default(Server);  
            srv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database db = default(Database);  
            db = srv.Databases["AdventureWorks2012"];  
            //Define an XmlSchemaCollection object by supplying the parent  
            // database and name arguments in the constructor.   
            XmlSchemaCollection xsc = default(XmlSchemaCollection);  
            xsc = new XmlSchemaCollection(db, "MySampleCollection");  
            xsc.Text = "<schema xmlns=" + Strings.Chr(34) + "http://www.w3.org/2001/XMLSchema" + Strings.Chr(34) + " xmlns:ns=" + Strings.Chr(34) + "http://ns" + Strings.Chr(34) + "><element name=" + Strings.Chr(34) + "e" + Strings.Chr(34) + " type=" + Strings.Chr(34) + "dateTime" + Strings.Chr(34) + "/></schema>";  
            //Create the XML schema collection on the instance of SQL Server.   
            xsc.Create();  
        }  
```  
  
## <a name="creating-an-xml-schema-in-powershell"></a>Создание схемы XML в PowerShell  
 В этом примере кода показано создание схемы XML с помощью объекта <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection>. Свойство <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection.Text%2A>, определяющее коллекцию схем XML, содержит несколько двойных кавычек. Они заменяются строкой `chr(34)` .  
  
```  
#Get a server object which corresponds to the default instance replace LocalMachine with the physical server  
cd \sql\LocalHost  
$srv = get-item default  
  
#Reference the AdventureWorks database.  
$db = $srv.Databases["AdventureWorks2012"]  
  
#Create a new schema collection  
$xsc = New-Object -TypeName Microsoft.SqlServer.Management.SMO.XmlSchemaCollection `  
-argumentlist $db,"MySampleCollection"  
  
#Add the xml  
$dq = '"' # the double quote character  
$xsc.Text = "<schema xmlns=" + $dq + "http://www.w3.org/2001/XMLSchema" + $dq + `  
"  xmlns:ns=" + $dq + "http://ns" + $dq + "><element name=" + $dq + "e" + $dq +`  
 " type=" + $dq + "dateTime" + $dq + "/></schema>"  
  
#Create the XML schema collection on the instance of SQL Server.  
$xsc.Create()  
```  
  
  
