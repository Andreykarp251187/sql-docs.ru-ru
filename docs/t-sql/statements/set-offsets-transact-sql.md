---
title: SET OFFSETS (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SET_OFFSETS_TSQL
- OFFSETS_TSQL
- SET OFFSETS
- OFFSETS
dev_langs:
- TSQL
helpviewer_keywords:
- position relative to start of statement [SQL Server]
- OFFSETS option
- offsets [SQL Server]
- SET OFFSETS statement
ms.assetid: c7bcc697-0930-4630-acae-d8ccbfa4414c
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 908f4b2ecf6a75e54ccb2752d1d4864192124503
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85765754"
---
# <a name="set-offsets-transact-sql"></a>SET OFFSETS (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Возвращает смещение (позицию относительно начала инструкции) заданного ключевого слова в инструкциях [!INCLUDE[tsql](../../includes/tsql-md.md)] для приложений DB-Library.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
 
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
  
SET OFFSETS keyword_list { ON | OFF }  
```  
  
## <a name="arguments"></a>Аргументы  
 *keyword_list*  
 Разделенный запятыми список конструкций [!INCLUDE[tsql](../../includes/tsql-md.md)], который включает в себя SELECT, FROM, ORDER, TABLE, PROCEDURE, STATEMENT, PARAM и EXECUTE.  
  
## <a name="remarks"></a>Remarks  
 SET OFFSETS используется только в приложениях DB-Library.  
  
 Значение SET OFFSETS устанавливается во время синтаксического анализа, но не во время исполнения. Установка во время синтаксического анализа означает, что если инструкция SET присутствует в пакете или хранимой процедуре, то она вступает в силу независимо от того, достигает ли фактическое выполнение кода соответствующей точки. Кроме того, инструкция SET вступает в силу до выполнения любых операторов. Например, даже если инструкция SET находится в блоке инструкций IF...ELSE, вход в который не осуществляется, инструкция SET, тем не менее, действует, поскольку блок инструкций IF...ELSE подлежит синтаксическому анализу.  
  
 Если инструкция SET OFFSETS установлена в хранимой процедуре, значение SET OFFSETS восстанавливается после того, как управление выходит из этой хранимой процедуры. Поэтому инструкция SET OFFSETS, определенная в динамическом коде SQL, не действует на инструкции, следующие за инструкцией динамического SQL.  
  
 Инструкция SET PARSEONLY возвращает смещение, если параметру OFFSETS присвоено значение ON, и ошибки не возникают.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом роли **public**.  
  
## <a name="see-also"></a>См. также:  
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET PARSEONLY (Transact-SQL)](../../t-sql/statements/set-parseonly-transact-sql.md)  
  
  
