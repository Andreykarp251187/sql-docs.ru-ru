---
title: Выгрузка расширенной хранимой процедуры DLL | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], unloading
- unloading extended stored procedures
ms.assetid: 4c75ab14-af54-4965-b376-8d75d385c941
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 2772c8d6470f9ad6eb5e8b7cadb6dedd136bd48b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63137585"
---
# <a name="unloading-an-extended-stored-procedure-dll"></a>Выгрузка DLL-библиотеки расширенной хранимой процедуры
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Пользуйтесь вместо этого интеграцией со средой CLR.  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] загружает библиотеку DLL расширенной хранимой процедуры, как только выполняется вызов одной из функций библиотеки DLL. DLL-библиотека остается загруженной до тех пор, пока не выключается сервер или системный администратор не выгружает ее с помощью инструкции DBCC. Например, следующая команда выгружает **xp_hello.dll**, позволяя системному администратору, чтобы скопировать новую версию этого файла в каталог без завершения работы сервера:  
  
```  
DBCC xp_hello(FREE)  
```  
  
## <a name="see-also"></a>См. также  
 [DBCC dllname &#40;бесплатный&#41; &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-dllname-free-transact-sql)  
  
  
