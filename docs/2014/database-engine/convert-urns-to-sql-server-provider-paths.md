---
title: Преобразование универсальных имен ресурса в пути поставщика SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c9b1b8f1-b117-4e87-9704-2170f62c5c8b
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 3160e5e6a70344d0340b0b14db822c7089b60680
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84934578"
---
# <a name="convert-urns-to-sql-server-provider-paths"></a>Преобразование универсальных имен ресурса в пути поставщика SQL Server
  Модель объектов управления [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] создает унифицированные имена ресурсов (URN) для своих объектов. Каждое универсальное имя ресурса (URN) однозначно определяет объект SMO и может быть преобразовано в путь поставщика SQL Server PowerShell с помощью командлета `Convert-UrnToPath`.  
  
## <a name="converting-urns-to-paths"></a>Преобразование имен URN в пути  
 Каждое имя URN содержит ту же информацию, что и путь к объекту, но представленную в другой форме. Например, ниже показан путь к таблице:  
  
 SQLSERVER:\SQL\MyComputer\DEFAULT\Databases\AdventureWorks2012\Tables\Person.Address  
  
 А ниже приведено имя URN, указывающее на тот же объект:  
  
 Server[@Name='MyComputer']\Database[@Name='AdventureWorks2012']\Table[@Name='Address' and @Schema='Person']  
  
 Если объект SMO создан в скрипте PowerShell, можно узнать универсальное имя ресурса объекта из свойства `Urn`, а затем использовать командлет `Convert-UrnToPath` для преобразования строки универсального имени ресурса объекта SMO в путь Windows PowerShell. Затем можно использовать поставщик для перехода в различные точки на пути.  
  
 Если имена узлов содержат дополнительные символы, которые не поддерживаются в именах путей Windows PowerShell, командлет `Convert-UrnToPath` преобразует их в шестнадцатеричное представление. Например, строка «My:Table» возвращается как «My%3ATable».  
  
 Чтобы ознакомиться с примерами использования этого командлета, выполните в среде Windows PowerShell:  
  
```powershell
Get-Help Convert-UrnToPath -Examples  
```  
  
## <a name="see-also"></a>См. также:  
 [Выражения запросов и универсальные имена ресурсов](../powershell/query-expressions-and-uniform-resource-names.md)   
 [Поставщик SQL Server PowerShell](../powershell/sql-server-powershell-provider.md)   
 [SQL Server PowerShell](../powershell/sql-server-powershell.md)  
