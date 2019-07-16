---
title: managed_backup.fn_backup_db_config (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- smart_admin.fn_backup_db_config
- smart_admin.fn_backup_db_config_TSQL
- fn_backup_db_config
- fn_backup_db_config_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- smart_admin.fn_backup_db_config
- fn_backup_db_config
ms.assetid: 7c755d8a-64dd-44b2-be5e-735d30758900
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a23f8eb64ae99b999cdf6b16f1c888383a88c147
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68067781"
---
# <a name="managedbackupfnbackupdbconfig-transact-sql"></a>managed_backup.fn_backup_db_config (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Возвращает 0, 1 или более строк с параметрами конфигурации «[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]». Возвращает 1 строку для указанной базы данных или возвращает все базы данных из экземпляра, в которых настроено «[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]».  
  
 Эта хранимая процедура используется для просмотра или определения текущих параметров конфигурации «[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]» для базы данных или всех баз данных на экземпляре SQL Server.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
managed_backup.fn_backup_db_config ('database_name' | '' | NULL)  
```  
  
##  <a name="Arguments"></a> Аргументы  
 @db_name  
 Имя базы данных. @db_name Параметр **SYSNAME**. Если в этом параметре передается пустая строка или значение NULL, возвращаются сведения обо всех базах данных на экземпляре SQL Server.  
  
## <a name="table-returned"></a>Возвращаемая таблица  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|db_name|SYSNAME|Имя базы данных.|  
|db_guid|UNIQUEIDENTIFIER|Уникальный идентификатор базы данных.|  
|is_availability_database|BIT|Указывает, участвует ли база данных в группе доступности. Значение 1 указывает, что база данных является базой данных доступности, 0 — что не является.|  
|is_dropped|BIT|Значение 1 указывает на то, что данная база данных удалена.|  
|credential_name|SYSNAME|Имя объекта учетных данных SQL, который используется для проверки подлинности учетной записи хранения. Значение NULL указывает, что учетные данные SQL не заданы.|  
|retention_days|INT|Текущий срок хранения в днях. Значение NULL указывает, что настройка «[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]» для этой базы данных не производилась.|  
|is_managed_backup_enabled|INT|Показывает, включено ли для базы данных «[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]». Значение 1 указывает, что «[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]» для этой базы данных в настоящий момент включено, а значение 0 — что «[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]» выключено.|  
|storage_url|NVARCHAR(1024)|URL-адрес учетной записи хранения.|  
|Encryption_algorithm|NCHAR(20)|Возвращает текущий алгоритм шифрования, используемый для шифрования резервной копии.|  
|Encryptor_type|NCHAR(15)|Возвращает настройки шифратора: сертификат или асимметричный ключ.|  
|Encryptor_name|NCHAR(max_length_of_cert/asymm_key_name)|Имя сертификата или асимметричного ключа.|  
  
## <a name="security"></a>Безопасность  
  
### <a name="permissions"></a>Разрешения  
 Требуется членство в **db_backupoperator** роли базы данных с **ALTER ANY CREDENTIAL** разрешения. Пользователь не должен быть запрещен **VIEW ANY DEFINITION** разрешения.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] конфигурации для «TestDB»  
  
 Для каждого фрагмента кода в поле атрибута языка выберите «tsql».  
  
```  
Use msdb  
GO  
SELECT * FROM managed_backup.fn_backup_db_config('TestDB')  
```  
  
 В следующем примере возвращается конфигурация «[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]» для всех баз данных в экземпляре SQL Server, где выполняется пример.  
  
```  
Use msdb  
GO  
SELECT * FROM managed_backup.fn_backup_db_config (NULL)  
```  
  
  
