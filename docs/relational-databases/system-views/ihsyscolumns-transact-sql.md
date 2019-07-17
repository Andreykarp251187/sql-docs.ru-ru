---
title: IHsyscolumns (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHsyscolumns
- IHsyscolumns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHsyscolumns view
ms.assetid: 263452f1-9708-48f0-9536-402a89e7f5bf
author: stevestein
ms.author: sstein
ms.openlocfilehash: a432685809676f997049940ea5aa1ce43dc38a60
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68029635"
---
# <a name="ihsyscolumns-transact-sql"></a>IHsyscolumns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **IHsyscolumns** представление предоставляет сведения о столбцах для статей, опубликованных из SQL Server издателем. Это представление хранится в база данных распространителя.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Имя столбца или параметра процедуры.|  
|**идентификатор**|**int**|Идентификатор объекта таблицы, к которой принадлежит столбец, или идентификатор хранимой процедуры, с которой данный параметр ассоциирован.|  
|**xtype**|**tinyint**|Тип физического хранилища из [sys.systypes &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-systypes-transact-sql.md).|  
|**typestat**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**xusertype**|**tinyint**|Идентификатор расширенного определяемого пользователем типа данных.|  
|**length**|**bigint**|Максимальная длина физического хранилища из [sys.systypes &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-systypes-transact-sql.md).|  
|**xprec**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**XScale**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**идентификатора столбца**|**int**|Идентификатор столбца или параметра.|  
|**xoffset**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**bitpos**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**Зарезервировано**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**colstat**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**cdefault**|**int**|Идентификатор значения по умолчанию для этого столбца.|  
|**Домен**|**int**|Идентификатор правила или ограничения CHECK для этого столбца.|  
|**number**|**int**|Номер подпроцедуры, если процедура сгруппирована (**0** для непроцедурных записей).|  
|**colorder**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**autoval**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**offset**|**int**|Сдвиг в строке, в которой встречается этот столбец.|  
|**collationid**|**int**|Идентификатор параметров сортировки столбца. Значение NULL для несимвольных столбцов.|  
|**language**|**int**|Идентификатор языка для столбца.|  
|**status**|**int**|Битовая карта, используемая для описания свойства столбца или параметра:<br /><br /> **0x08** = столбец допускает значения null.<br /><br /> **0x10** = заполнение символами ANSI был в силу, если **varchar** или **varbinary** были добавлены столбцы. Замыкающие пробелы сохраняются для **varchar** и замыкающие нули сохраняются для **varbinary** столбцов.<br /><br /> **0x40** = параметр является ВЫХОДНЫМ параметром.<br /><br /> **0x80** = столбец является столбцом идентификаторов.|  
|**type**|**int**|Тип физического хранилища из [sys.systypes &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-systypes-transact-sql.md).|  
|**usertype**|**tinyint**|Идентификатор типа пользовательских данных из [sys.systypes &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-systypes-transact-sql.md).|  
|**printfmt**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**prec**|**int**|Степень точности для данного столбца.|  
|**масштаб**|**int**|Шкала для данного столбца.|  
|**iscomputed**|**int**|Признак, по которому определяется, является ли столбец вычисляемым:<br /><br /> **0** = невычисляемого.<br /><br /> **1** = вычисляемый.|  
|**isoutparam**|**int**|Указывает, относится ли параметр процедуры к выходным параметрам:<br /><br /> **1** = true.<br /><br /> **0** = false.|  
|**IsNullable**|**int**|Указывает, допускает ли столбец значения NULL:<br /><br /> **1** = true.<br /><br /> **0** = false.|  
|**Параметры сортировки**|**int**|Имя параметров сортировки столбца. Значение NULL для несимвольных столбцов.|  
|**tdscollation**|**int**|Имя параметров сортировки столбца при возвращении в поток табличных данных (TDS).|  
  
## <a name="see-also"></a>См. также  
 [Разнородная репликация базы данных](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sys.columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)  
  
  
