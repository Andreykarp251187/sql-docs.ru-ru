---
title: С помощью сообщений | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- messages [SMO]
ms.assetid: 4037a866-4826-4c1f-890c-e7e3658adf13
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7e67d8818fb20d339c4166f606d15e0f7dbceced
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63015266"
---
# <a name="using-messages"></a>Использование сообщений
  В SMO системные сообщения представлены объектом <xref:Microsoft.SqlServer.Management.Smo.SystemMessageCollection>, принадлежащим объекту `Server`. Так как системные сообщения нельзя изменить, свойства объекта `SystemMessage` доступны только для чтения.  
  
 Определяемые пользователем сообщения представлены в SMO программно объектом <xref:Microsoft.SqlServer.Management.Smo.UserDefinedMessageCollection>. Существующие определяемые пользователем сообщения могут быть обнаружены при проходе по коллекции. Новые определяемые пользователем сообщения могут создаваться путем создания нового объекта `UserDefinedMessage` и установки соответствующих свойств.  
  
## <a name="examples"></a>Примеры  
 В следующих примерах кода для создания приложения необходимо выбрать среду программирования, шаблон программирования и язык программирования. Дополнительные сведения см. в разделе [Создание проекта SMO на Visual Basic в Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) и [Visual C создайте&#35; проекта SMO в Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="finding-a-particular-system-message-in-visual-basic"></a>Обнаружение определенного системного сообщения на языке Visual Basic  
 Пример кода показывает, как определить системное сообщение по идентификатору и отобразить его.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBMessages1](SMO How to#SMO_VBMessages1)]  -->  
  
## <a name="finding-a-particular-system-message-in-visual-c"></a>Обнаружение определенного системного сообщения на языке Visual C#  
 Пример кода показывает, как определить системное сообщение по идентификатору и отобразить его.  
  
```  
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv = new Server();  
            //Reference an existing system message using the   
            //ItemByIdAndLanguage method.   
            SystemMessage msg = default(SystemMessage);  
            msg = srv.SystemMessages.ItemByIdAndLanguage(14126, "us_english");  
            //Display the message ID and text.   
            Console.WriteLine(msg.ID.ToString() + " " + msg.Text);  
        }  
```  
  
## <a name="finding-a-particular-system-message-in-powershell"></a>Обнаружение определенного системного сообщения в PowerShell  
 Пример кода показывает, как определить системное сообщение по идентификатору и отобразить его.  
  
```  
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\  
$srv = get-item default  
  
#Get the message 14126 in US English and display it  
$msg = $srv.SystemMessages.ItemByIdAndLanguage(14126, "us_english")  
$msg.ID.ToString() + " "+ $msg.Text  
```  
  
## <a name="adding-a-new-user-defined-message-in-visual-basic"></a>Добавление нового определяемого пользователем сообщения на языке Visual Basic  
 Пример кода демонстрирует, как создать определяемое пользователем сообщение с идентификатором больше 50 000.  
  
```  
Dim mysrv As Server  
mysrv = New Server  
Dim udm As UserDefinedMessage  
udm = New UserDefinedMessage(mysrv, 50003, "us_english", 16, "Test message")  
udm.Create()  
```  
  
## <a name="adding-a-new-user-defined-message-in-visual-c"></a>Добавление нового определяемого пользователем сообщения на языке Visual C#  
 Пример кода демонстрирует, как создать определяемое пользователем сообщение с идентификатором больше 50 000.  
  
```  
{  
  
            Server mysrv = new Server();  
  
            UserDefinedMessage udm = new UserDefinedMessage(mysrv, 50030, "us_english",16, "Test message");  
            udm.Create();  
             UserDefinedMessage  msg = mysrv.UserDefinedMessages.ItemByIdAndLanguage(50030, "us_english");  
            //Display the message ID and text.   
            Console.WriteLine(msg.ID.ToString() + " " + msg.Text);  
  
        }  
```  
  
## <a name="adding-a-new-user-defined-message-in-powershell"></a>Добавление нового, определяемого пользователем сообщения в PowerShell  
 Пример кода демонстрирует, как создать определяемое пользователем сообщение с идентификатором больше 50 000.  
  
```  
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Create a new message  
  
$udm = New-Object -TypeName Microsoft.SqlServer.Management.SMO.UserDefinedMessage -argumentlist `  
$srv, 50030, "us_english", 16, "Test message"  
$udm.Create()  
$msg = $srv.UserDefinedMessages.ItemByIdAndLanguage(50030, "us_english");  
$msg  
```  
  
  
