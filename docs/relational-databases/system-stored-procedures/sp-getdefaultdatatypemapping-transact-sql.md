---
title: sp_getdefaultdatatypemapping (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_getdefaultdatatypemapping_TSQL
- sp_getdefaultdatatypemapping
helpviewer_keywords:
- sp_getdefaultdatatypemapping
ms.assetid: b8401de1-f135-41d0-ba79-ce8fe1f48c00
author: stevestein
ms.author: sstein
ms.openlocfilehash: 32fe9edf5c3d8621046a27937d83f642b1689d1a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68123990"
---
# <a name="spgetdefaultdatatypemapping-transact-sql"></a>sp_getdefaultdatatypemapping (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о сопоставлении по умолчанию для указанного типа данных между [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и отличным от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных системы управления (СУБД). Эта хранимая процедура выполняется на распространителе в любой базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_getdefaultdatatypemapping [ @source_dbms = ] 'source_dbms'   
    [ , [ @source_version = ] 'source_version' ]  
        , [ @source_type = ] 'source_type'    
    [ , [ @source_length = ] source_length ]  
    [ , [ @source_precision = ] source_precision ]  
    [ , [ @source_scale = ] source_scale ]  
    [ , [ @source_nullable = ] source_nullable ]  
        , [ @destination_dbms = ] 'destination_dbms'   
    [ , [ @destination_version = ] 'destination_version' ]  
    [ , [ @destination_type = ] 'destination_type' OUTPUT ]  
    [ , [ @destination_length = ] destination_length OUTPUT ]  
    [ , [ @destination_precision = ] destination_precision OUTPUT ]  
    [ , [ @destination_scale = ] destination_scale OUTPUT ]  
    [ , [ @destination_nullable = ] source_nullable OUTPUT ]  
    [ , [ @dataloss = ] dataloss OUTPUT ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @source_dbms = ] 'source_dbms'` — Имя СУБД, из которой сопоставляются типы данных. *source_dbms* — **sysname**, и может принимать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|**MSSQLSERVER**|Источником является база данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**ORACLE**|Источником является база данных Oracle.|  
  
 Необходимо указать значение для этого параметра.  
  
`[ @source_version = ] 'source_version'` — Номер версии исходной СУБД. *source_version* — **varchar(10)** , со значением по умолчанию NULL.  
  
`[ @source_type = ] 'source_type'` — Тип данных в исходной СУБД. *source_type* — **sysname**, не имеет значения по умолчанию.  
  
`[ @source_length = ] source_length` — Длина типа данных в исходной СУБД. *source_length* — **bigint**, со значением по умолчанию NULL.  
  
`[ @source_precision = ] source_precision` — Это точность типа данных в исходной СУБД. *source_precision* — **bigint**, со значением по умолчанию NULL.  
  
`[ @source_scale = ] source_scale` Является масштаб типа данных в исходной СУБД. *source_scale* — **int**, со значением по умолчанию NULL.  
  
`[ @source_nullable = ] source_nullable` Показывает тип данных в исходной СУБД поддерживает значение NULL. *source_nullable* — **бит**, со значением по умолчанию **1**, что означает, что значения NULL допустимы.  
  
`[ @destination_dbms = ] 'destination_dbms'` — Имя целевой СУБД. *destination_dbms* — **sysname**, и может принимать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|**MSSQLSERVER**|Целевая база данных — [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**ORACLE**|Целевой является база данных Oracle.|  
|**DB2**|Целевой является база данных IBM DB2.|  
|**SYBASE**|Целевой является база данных Sybase.|  
  
 Необходимо указать значение для этого параметра.  
  
`[ @destination_version = ] 'destination_version'` Версия продукта целевой СУБД. *destination_version* — **varchar(10)** , со значением по умолчанию NULL.  
  
`[ @destination_type = ] 'destination_type' OUTPUT` Тип данных, приведенных в целевой СУБД. *destination_type* — **sysname**, со значением по умолчанию NULL.  
  
`[ @destination_length = ] destination_length OUTPUT` — Длина типа данных в целевой СУБД. *destination_length* — **bigint**, со значением по умолчанию NULL.  
  
`[ @destination_precision = ] destination_precision OUTPUT` — Это точность типа данных в целевой СУБД. *destination_precision* — **bigint**, со значением по умолчанию NULL.  
  
`[ @destination_scale = ] _destination_scaleOUTPUT` Является масштаб типа данных в целевой СУБД. *destination_scale* — **int**, со значением по умолчанию NULL.  
  
`[ @destination_nullable = ] _destination_nullableOUTPUT` Показывает тип данных в целевой СУБД поддерживает значение NULL. *destination_nullable* — **бит**, со значением по умолчанию NULL. **1** означает, что значения NULL допустимы.  
  
`[ @dataloss = ] _datalossOUTPUT` — Это, что при сопоставлении возможна потеря данных. *потери данных* — **бит**, со значением по умолчанию NULL. **1** означает, что есть вероятность потери данных.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_getdefaultdatatypemapping** используется во всех типах репликации между [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и отличным от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] СУБД.  
  
 **sp_getdefaultdatatypemapping** возвращает данные назначения по умолчанию типа, который является наиболее подходящие для заданного исходного типа данных.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять процедуру **sp_getdefaultdatatypemapping**.  
  
## <a name="see-also"></a>См. также  
 [sp_helpdatatypemap &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql.md)   
 [sp_setdefaultdatatypemapping &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-setdefaultdatatypemapping-transact-sql.md)   
 [Data Type Mapping for Oracle Publishers](../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md)   
 [IBM DB2 Subscribers](../../relational-databases/replication/non-sql/ibm-db2-subscribers.md)   
 [Подписчики Oracle](../../relational-databases/replication/non-sql/oracle-subscribers.md)  
  
  
