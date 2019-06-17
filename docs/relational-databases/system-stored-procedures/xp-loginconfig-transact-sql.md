---
title: xp_loginconfig (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- xp_loginconfig_TSQL
- xp_loginconfig
dev_langs:
- TSQL
helpviewer_keywords:
- xp_loginconfig
ms.assetid: d380e799-2857-408a-bcbf-5e73a8e6aa5a
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 8590a33f870dc14ac34118ce5e655acc6e67f257
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62645110"
---
# <a name="xploginconfig-transact-sql"></a>xp_loginconfig (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о конфигурации безопасности входа в систему для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
xp_loginconfig ['config_name']  
```  
  
## <a name="arguments"></a>Аргументы  
 **"** *config_name* **"**  
 Отображаемое значение конфигурации. Если *config_name* — не указано, выводятся все значения параметров конфигурации. *config_name* — **sysname**, значение по умолчанию NULL, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**режим входа**|Режим безопасности имени входа в систему. Возможные значения: **Mixed** и **проверки подлинности Windows**.<br /><br /> Заменяется на:<br /><br /> `SELECT SERVERPROPERTY('IsIntegratedSecurityOnly'); GO`|  
|**Имя входа по умолчанию**|Имя идентификатора входа сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по умолчанию для авторизованных пользователей доверенных подключений (для пользователей без соответствующего имени входа). Имя входа по умолчанию является **гостевой**. Данное значение предоставляется для обеспечения обратной совместимости.|  
|**Домен по умолчанию**|Имя домена Windows по умолчанию для сетевых пользователей доверенных подключений. Доменом по умолчанию является домен компьютера Windows, на котором выполняется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Данное значение предоставляется для обеспечения обратной совместимости.|  
|**уровень аудита**|Уровень аудита. Возможные значения: **none**, **успех**, **сбоя**, и **все**. Результаты аудита записываются в журнал ошибок и в окно просмотра событий Windows.|  
|**Имя узла набора**|Указывает, заменяется ли имя узла из учетной записи клиента на сетевое имя пользователя Windows. Возможные значения: **true** или **false**. Если это значение задано, сетевое имя пользователя отображается в выходных данных из **sp_who**.|  
|**сопоставить _**|Сообщает, какие специальные символы Windows поставлены в соответствие допустимому символу подчеркивания (_) сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Возможные значения: **разделителя домена** (по умолчанию), **пространства**, **null**, или любой единичный символ. Данное значение предоставляется для обеспечения обратной совместимости.|  
|**$ карты**|Сообщает, какие специальные символы Windows поставлены в соответствие допустимому символу знака доллара ($) сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Возможные значения: **разделителя домена**, **пространства**, **null**, или любой единичный символ. По умолчанию используется **пространства**. Данное значение предоставляется для обеспечения обратной совместимости.|  
|**сопоставить #**|Сообщает, какие специальные символы Windows поставлены в соответствие допустимому символу знака «решетка» (#) сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Возможные значения: **разделителя домена**, **пространства**, **null**, или любой единичный символ. Значение по умолчанию — дефис (-). Данное значение предоставляется для обеспечения обратной совместимости.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Параметр конфигурации|  
|**значение параметра конфигурации**|**sysname**|Значение параметра конфигурации|  
  
## <a name="remarks"></a>Примечания  
 **xp_loginconfig** не может использоваться для задания значений конфигурации.  
  
 Определение режима входа и уровня аудита производится в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## <a name="permissions"></a>Разрешения  
 Требует разрешения CONTROL на **master** базы данных.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-how-to-report-all-configuration-values"></a>A. Отчет со значениями всех параметров конфигурации  
 В следующем примере выводятся все текущие значения параметров конфигурации.  
  
```  
EXEC xp_loginconfig;  
GO  
```  
  
### <a name="b-how-to-report-a-specific-configuration-value"></a>Б. Отчет со значением конкретного параметра конфигурации  
 В следующем примере выводится значение режима входа в систему.  
  
```  
EXEC xp_loginconfig 'login mode';  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимая процедура sp_denylogin (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-denylogin-transact-sql.md)   
 [Хранимая процедура sp_grantlogin (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Хранимая процедура sp_revokelogin (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-revokelogin-transact-sql.md)   
 [xp_logininfo &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/xp-logininfo-transact-sql.md)  
  
  
