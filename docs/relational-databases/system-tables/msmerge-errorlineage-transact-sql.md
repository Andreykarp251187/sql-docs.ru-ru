---
title: MSmerge_errorlineage (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_errorlineage_TSQL
- MSmerge_errorlineage
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_errorlineage system table
ms.assetid: 3bcbd328-c958-4cd4-a573-3c35539fa919
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1c3191191a9830a38a177ba3a3c353e5c34dedba
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68044757"
---
# <a name="msmergeerrorlineage-transact-sql"></a>MSmerge_errorlineage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_errorlineage** таблица содержит строки, которые были удалены на подписчике, но удаление которых не распространяются на издатель. Эта таблица хранится в базах данных публикации и подписки.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**tablenick**|**int**|Целочисленное значение, присваиваемое таблице, публикуемой для выполнения репликации слиянием. Соответствует полю псевдоним в **sysmergearticles** таблицы.|  
|**столбец ROWGUID**|**uniqueidentifier**|Идентификатор строки.|  
|**журнала обращений и преобразований**|**Varbinary(501)**|Хранит список обновлений строки подписчиками и издателями. Используется для выявления и разрешения конфликтных ситуаций.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
