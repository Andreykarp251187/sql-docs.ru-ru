---
title: Создание файлов подключения к серверу (AccessToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 08/17/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 829153be-aa8e-4162-87e8-69882feecf19
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 03d622c50a8760bbf1767bc8a4f79e215773695f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68006607"
---
# <a name="creating-the-server-connection-files-accesstosql"></a>Создание файлов подключения к (AccessToSQL) сервера
Сведения о сервере может быть указано в разделе "серверы" файла скрипта. Сведения о сервере также можно указать в файле подключения отдельный сервер. Параметр командной строки файла подключения к серверу — `-c <serverconnectionfile>`. Если один и тот же идентификатор сервера присутствует в файлах подключения и скрипт и сервер, считается определение сервера в файле скрипта.  
  
```xml  
<!--Sample of server connection file commands -->  
<!--Connection to SQL Server-->  
  
<sql-server name="target_3">  
  
  <sql-server-authentication>  
  
    <server value="$TargetServerName$"/>  
  
    <database value="$TargetDB$"/>  
  
    <user-id value="$TargetUserName$"/>  
  
    <password value="$TargetPassword$"/>  
  
    <encrypt value="true"/>  
  
    <trust-server-certificate value="true"/>  
  
  </sql-server-authentication>  
  
</sql-server>  
```  
  
```xml  
<!--Connection to SQL Azure-->  
  
<sql-azure name="target_azure">  
  
  <server value="$TargetAzureServerName$"/>  
  
  <database value="$TargetAzureDB$"/>  
  
  <user-id value="$TargetAzureUserName$"/>  
  
  <password value="$TargetAzurePassword$"/>  
  
</sql-azure>  
```  
  
## <a name="server-connection-file-validation"></a>Проверка файла подключения сервера  
Пользователь может просто проверять его/ее файл подключения сервера соответствие файлу определения схемы **«A2SSConsoleScriptServersSchema.xsd»** доступны в папке «Схемы».  
  
## <a name="next-step"></a>Следующий шаг  
Следующий шаг в работе консоли — [выполнение команд консоли SSMA &#40;AccessToSQL&#41;](../../ssma/access/executing-the-ssma-console-accesstosql.md)  
  
## <a name="see-also"></a>См. также  
[Выполнение команд консоли SSMA (доступ)](https://msdn.microsoft.com/aa1bf665-8dc0-4259-b36f-46ae67197a43)  
  
