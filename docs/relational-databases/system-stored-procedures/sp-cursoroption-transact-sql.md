---
title: sp_cursoroption (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cursoroption_TSQL
- sp_cursoroption
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cursoroption
ms.assetid: 88fc1dba-f4cb-47c0-92c2-bf398f4a382e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5a686f78ea5dff8a3ea551016d9fbe9c9046b110
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62724439"
---
# <a name="spcursoroption-transact-sql"></a>sp_cursoroption (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Устанавливает параметры курсора или возвращает информацию о курсоре, созданная процедурой sp_cursoropen хранятся. sp_cursoroption вызывается указанием ID = 8 в пакете потока табличных данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_cursoroption cursor, code, value  
```  
  
## <a name="arguments"></a>Аргументы  
 *курсор*  
 — *Обрабатывать* значение, создаваемое [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и возвращаемое процедурой sp_cursoropen хранятся. *курсор* требует **int** входного значения.  
  
 *код*  
 Служит для указания различных коэффициентов возвращаемых значений курсора. *код* требует одного из следующих **int** входных значений:  
  
|Значение|Имя|Описание|  
|-----------|----------|-----------------|  
|0x0001|TEXTPTR_ONLY|Возвращает не фактические данные, а текстовый указатель для определенных назначенных столбцов типа text или image.<br /><br /> TEXTPTR_ONLY позволяет текстовые указатели для использования в качестве *дескрипторы* для объектов blob, которые можно выборочно извлечь или обновить с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] или DBLib (например) [!INCLUDE[tsql](../../includes/tsql-md.md)] READTEXT или DBLIB DBWRITETEXT).<br /><br /> Если присвоено значение «0», то все столбцы типа text или image из выбранного списка будут возвращать вместо данных текстовые указатели.|  
|0x0002|CURSOR_NAME|Назначает имя, указанное в *значение* до текущей позиции. Это, в свою очередь позволяет интерфейсу ODBC применять [!INCLUDE[tsql](../../includes/tsql-md.md)] позиционированных инструкций UPDATE и DELETE на курсоры, открываемым процедурой sp_cursoropen.<br /><br /> Строка может иметь любой символьный тип данных или UNICODE.<br /><br /> Так как [!INCLUDE[tsql](../../includes/tsql-md.md)] позиционированные инструкции UPDATE и DELETE работают по умолчанию на первой строке в крупном курсоре, sp_cursor SETPOSITION следует использовать для позиционирования курсора перед выдачей позиционированной инструкции UPDATE и DELETE.|  
|0x0003|TEXTDATA|Возвращает фактические данные, а не текстовый указатель для определенных столбцов типа text или image при последующей выборке (т. е. отменяет действие TEXTPTR_ONLY).<br /><br /> Если для определенного столбца включен режим TEXTDATA, то выполняется повторная выборка или обновление строки, и после этого можно опять присвоить значение TEXTPTR_ONLY. Как и в случае с TEXTPTR_ONLY, целочисленный параметр значения задает номер столбца. Нулевое значение возвращает все текстовые столбцы или столбцы изображений.|  
|0x0004|SCROLLOPT|Параметр прокрутки. Дополнительные сведения см. ниже в разделе «Значения кодов возврата».|  
|0x0005|CCOPT|Параметр управления параллелизмом. Дополнительные сведения см. ниже в разделе «Значения кодов возврата».|  
|0x0006|ROWCOUNT|Количество строк, находящихся в результирующем наборе.<br /><br /> Примечание. Параметр ROWCOUNT мог измениться с момента значение, возвращаемое процедурой sp_cursoropen параметр, если используется асинхронное заполнение. Если число строк неизвестно, возвращается значение -1.|  
  
 *value*  
 Определяет значение, возвращенное *кода*. *значение* является обязательным параметром, который вызывает равного 0x0001, 0x0002 или 0x0003 *кода* входного значения.  
  
> [!NOTE]  
>  Объект *код* значение 2 является строковым типом данных. Любой другой *кода* значение введенное или возвращенное *значение* должно быть целым числом.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 *Значение* параметра может возвращать одно из следующих *кода* значения.  
  
|Возвращаемое значение|Описание|  
|------------------|-----------------|  
|0x0004|SCROLLOPT|  
|0X0005|CCOPT|  
|0X0006|ROWCOUNT|  
  
 *Значение* параметр возвращает одно из следующих значений SCROLLOPT.  
  
|Возвращаемое значение|Описание|  
|------------------|-----------------|  
|0x0001|KEYSET|  
|0x0002|DYNAMIC|  
|0x0004|FORWARD_ONLY|  
|0x0008|STATIC|  
  
 *Значение* параметр возвращает одно из следующих значений CCOPT.  
  
|Возвращаемое значение|Описание|  
|------------------|-----------------|  
|0x0001|READ_ONLY|  
|0x0002|SCROLL_LOCKS|  
|0x0004 или 0x0008|OPTIMISTIC|  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sp_cursor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursor-transact-sql.md)   
 [sp_cursoropen &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursoropen-transact-sql.md)  
  
  
