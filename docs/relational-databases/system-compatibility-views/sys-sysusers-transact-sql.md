---
title: sys.sysusers (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sysusers
- sys.sysusers_TSQL
- sysusers_TSQL
- sysusers
dev_langs:
- TSQL
helpviewer_keywords:
- sysusers system table
- sys.sysusers compatibility view
ms.assetid: 5f0e6a8d-c983-44f6-97e9-aab5bff67d18
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1b8bec28a2e7778a449cb36aeee81481a311c6b9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68018058"
---
# <a name="syssysusers-transact-sql"></a>sys.sysusers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Содержит по одной строке для каждого [!INCLUDE[msCoName](../../includes/msconame-md.md)] пользователя Windows, группа Windows, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пользователя, или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] роли в базе данных.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**UID**|**smallint**|Идентификатор пользователя, уникальный в этой базе данных.<br /><br /> 1 = владелец базы данных.<br /><br /> Вызывает переполнение или возвращает значение NULL, если количество пользователей и ролей превышает 32 767.|  
|**status**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**name**|**sysname**|Имя пользователя или группы, уникальное в этой базе данных.|  
|**ИД безопасности**|**varbinary(85)**|Идентификатор безопасности для этой записи.|  
|**Роли**|**varbinary(2048)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**CREATEDATE**|**datetime**|Дата добавления этой учетной записи.|  
|**updatedate**|**datetime**|Дата последнего изменения учетной записи.|  
|**altuid**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]<br /><br /> Вызывает переполнение или возвращает значение NULL, если количество пользователей и ролей превышает 32 767.|  
|**password**|**varbinary(256)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**gid**|**smallint**|Идентификатор группы, к которой принадлежит пользователь. Если **uid** совпадает со значением **gid**, эта запись определяет группу. Вызывает переполнение или возвращает значение NULL, если общее количество групп и пользователей превышает 32 767.|  
|**Environ-**|**varchar(255)**|Зарезервировано.|  
|**hasdbaccess**|**int**|1 = учетная запись обладает правами доступа к базе данных.|  
|**islogin**|**int**|1 = учетная запись входа представляет группу Windows, пользователя Windows или пользователя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], обладающего учетной записью для входа.|  
|**Isntname**|**int**|1 = учетная запись представляет группу или пользователя Windows.|  
|**Isntgroup**|**int**|1 = учетная запись представляет группу Windows.|  
|**isntuser**|**int**|1 = учетная запись представляет пользователя Windows.|  
|**issqluser**|**int**|1 = учетная запись представляет пользователя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**isaliased**|**int**|1 = учетная запись представляет псевдоним другого пользователя.|  
|**issqlrole**|**int**|1 = учетная запись представляет роль [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**isapprole**|**int**|1 = учетная запись представляет роль приложения.|  
  
## <a name="see-also"></a>См. также  
 [Сопоставление системных таблиц с системными представлениями &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Представления совместимости (Transact-SQL)](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
