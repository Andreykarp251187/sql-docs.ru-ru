---
title: Экранирование идентификаторов SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: 8a73e945-daa6-4e5d-93da-10f000f1f3a2
author: markingmyname
ms.author: maghan
ms.openlocfilehash: c196b316424c941cba52eb50c61c82ca772ba18c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67951707"
---
# <a name="escape-sql-server-identifiers"></a>Применение escape-символов к идентификаторам SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Часто можно использовать экранирующий символ обратной кавычки (`) для escape-символов, применение которых допускается в идентификаторах с разделителями [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], но не в именах путей Windows PowerShell. Тем не менее экранирование некоторых символов невозможно. Например, в среде Windows PowerShell нельзя экранировать символ двоеточия (:). Идентификаторы с этим символом должны быть закодированы. Кодировка более надежна, чем экранирование, поскольку действует для всех символов.  

> [!NOTE]
> Существует два модуля SQL Server PowerShell — **SqlServer** и **SQLPS**. Модуль **SQLPS** входит в состав установки SQL Server (для обеспечения обратной совместимости), но больше не обновляется. Самым актуальным модулем PowerShell является модуль **SqlServer**. Модуль **SqlServer** содержит обновленные версии командлетов в **SQLPS**, а также новые командлеты для поддержки последних функций SQL.
> Предыдущие версии модуля **SqlServer** *входили* в состав среды SQL Server Management Studio (SSMS), но только с SSMS версий 16.x. Для работы PowerShell с SSMS 17.0 и более поздних версий необходимо установить модуль **SqlServer** из коллекции PowerShell.
> Сведения об установке модуля **SqlServer** см. в статье [Установка компонентов SQL Server PowerShell](download-sql-server-ps-module.md).

Символ обратной кавычки (`) обычно расположен на клавише в верхнем левом углу клавиатуры, под клавишей ESC.  
  
## <a name="examples"></a>Примеры  
 Ниже приведен пример экранирования символа #:  
  
```  
cd SQLSERVER:\SQL\MyComputer\MyInstance\MyDatabase\MySchema\`#MyTempTable  
```  
  
 Это пример экранирования скобок при указании (local) в качестве имени компьютера:  
  
```  
Set-Location SQLSERVER:\SQL\`(local`)\DEFAULT  
```  
  
## <a name="see-also"></a>См. также:  
 [Идентификаторы SQL Server в PowerShell](sql-server-identifiers-in-powershell.md)   
 [SQL Server PowerShell, поставщик](sql-server-powershell-provider.md)   
 [SQL Server PowerShell](sql-server-powershell.md)  
  
  
