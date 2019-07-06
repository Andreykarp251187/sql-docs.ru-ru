---
title: Выполнение дельты с использованием ADO (SQLXML 4.0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- providers [SQLXML], SQLOLEDB Provider
- ADO [SQLXML]
- SQLXMLOLEDB Provider, DiffGrams
- data providers [SQLXML], SQLOLEDB Provider
- DiffGrams [SQLXML], ADO
ms.assetid: 741fce82-de83-4923-86eb-30acb5b9a5e6
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3880573328f7143b90033f04e84ba1bd76eed654
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/05/2019
ms.locfileid: "67583930"
---
# <a name="executing-a-diffgram-by-using-ado-sqlxml-40"></a>Выполнение дельты с использованием ADO (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Следующее приложение на языке [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic использует ADO для установки соединения с экземпляром Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и выполняет DiffGram. В этом приложении дельты и схема XSD хранятся в файле. Приложение загружает DiffGram из заданного файла. Можно использовать любые дельты (и связанной схемы XSD) описано в разделе [примеры дельт](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/diffgram/diffgram-examples-sqlxml-4-0.md).  
  
 Ниже приводится последовательность действий в образце приложения.  
  
-   **Conn** объекта (**ADODB. Подключение**) устанавливает соединение с запущенным экземпляром сервера SQL на конкретном сервере.  
  
-   **Cmd** объекта (**ADODB.Command**) выполняется в рамках установленного подключения.  
  
-   В качестве диалекта команды задано значение DBGUID_MSSQLXML.  
  
-   Дельта копируется в поток команды (**strmIn**) из файла.  
  
-   Выходной поток команды присваивается **StrmOut** объекта (**ADODB. Stream**), который получает все возвращаемых данных.  
  
-   При использовании поставщика SQLOLEDB вы по умолчанию получаете функциональность Microsoft SQLXML, предоставляемую библиотекой Sqlxmlx.dll. Чтобы использовать библиотеку Sqlxml4.dll с поставщиком SQLOLEDB, **SQLXML Version** свойству должно быть присвоено **SQLXML.4.0** на поставщик SQLOLEDB **подключения** объекта.  
  
-   Команда (дельта) будет выполнена.  
  
 Следующий код представляет собой образец приложения.  
  
> [!NOTE]  
>  В коде необходимо задать имя экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в строке соединения.  
  
```  
Private Sub Command1_Click()  
  Dim cmd As New ADODB.Command  
  Dim conn As New ADODB.Connection  
  Dim strmOut As New ADODB.Stream  
  Dim strmIn As New ADODB.Stream  
  
  'Open a connection to SQL Server.  
  conn.Provider = "SQLOLEDB"  
  conn.Open "server=SqlServerName; database=tempdb; Integrated Security=SSPI; "  
  conn.Properties("SQLXML Version") = "SQLXML.4.0"  
  Set cmd.ActiveConnection = conn  
  strmIn.Open  
  strmIn.Charset = "UTF-8"  
  strmIn.LoadFromFile "C:\SomeFilePath\SampleDiffGram.xml"  
  strmIn.Position = 0  
  Set cmd.CommandStream = strmIn  
  
  strmOut.Open  
  cmd.Properties("Output Stream").Value = strmOut  
  cmd.Properties("Output Encoding").Value = "UTF-8"  
  
  cmd.Dialect = "{5d531cb2-e6ed-11d2-b252-00c04f681b71}"  
  cmd.Properties("Mapping Schema") = "C:\SomeFilePath\SampleDiffGram.xml"  
  cmd.Execute , , adExecuteStream  
  strmOut.Position = 0  
  Set cmd = Nothing  
  strmOut.Charset = "UTF-8"  
  strmOut.SaveToFile "C:\DropIt.txt", adSaveCreateOverWrite  
  strmOut.Close  
  Set strmOut = Nothing  
  
End Sub  
```  
  
### <a name="to-test-the-diffgram"></a>Проверка дельты  
  
1.  В папку на компьютере, скопируйте любой из дельту и соответствующую схему XSD из одного из примеров в [примеры дельт](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/diffgram/diffgram-examples-sqlxml-4-0.md).  
  
2.  Откройте Visual Basic и создайте проект стандартного исполняемого файла.  
  
3.  Добавьте эти ссылки в проект:  
  
    ```  
    Microsoft ActiveX Data Objects 2.8 Library  
    ```  
  
4.  В области элементов щелкните **CommandButton**, а затем нарисуйте кнопку в форме.  
  
5.  Дважды нажмите кнопку, чтобы изменить ее код, и добавьте код приложения из раздела.  
  
6.  Отредактируйте код, чтобы в нем указывались имена файлов DiffGram и XSD. Также отредактируйте строку соединения.  
  
7.  Запустите приложение. Результат выполнения зависит от типа DiffGram.  

[!INCLUDE[freshInclude](../../../includes/paragraph-content/fresh-note-steps-feedback.md)]

