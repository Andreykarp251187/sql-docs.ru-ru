---
title: sp_pdw_add_network_credentials (хранилище данных SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.service: sql-data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 0729eeff-ac7e-43f0-80fa-ff5346a75985
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: da1ba0db4467526ef2b54650020a899f88788648
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68008956"
---
# <a name="sppdwaddnetworkcredentials-sql-data-warehouse"></a>sp_pdw_add_network_credentials (хранилище данных SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Это сохраняет сетевые учетные данные в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] и связывает их с сервером. Например, использовать эту хранимую процедуру для предоставления [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] соответствующие разрешения на чтение/запись резервной копии и восстановления на целевом сервере, или создать резервную копию сертификата, используемый для прозрачного шифрования данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL (Transact-SQL)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_pdw_add_network_credentials 'target_server_name',  'user_name', ꞌpasswordꞌ  
```  
  
## <a name="arguments"></a>Аргументы  
 '*target_server_name*'  
 Указывает имя узла целевого сервера или IP-адрес. [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] будет доступ к этому серверу, используя учетные данные имени пользователя и пароля, передаваемое в хранимую процедуру.  
  
 Чтобы подключиться через сеть InfiniBand, использование InfiniBand IP-адреса целевого сервера.  
  
 *имя_сервера_назначения* определяется как nvarchar(337).  
  
 '*user_name*'  
 Указывает user_name, разрешениями на доступ к целевой сервер. Если учетные данные уже существует на целевом сервере, они будут обновлены для новых учетных данных.  
  
 *user_name* определяется как nvarchar (513).  
  
 "*пароль*ꞌ  
 Указывает пароль для *user_name*.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="permissions"></a>Разрешения  
 Требуется **ALTER SERVER STATE** разрешение.  
  
## <a name="error-handling"></a>Обработка ошибок  
 Произошла ошибка при добавлении учетных данных не работает на узле управления, а все вычислительные узлы.  
  
## <a name="general-remarks"></a>Общие замечания  
 Эта хранимая процедура добавляет сетевые учетные данные учетной записи NetworkService для [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. Учетная запись NetworkService выполняется каждый экземпляр SMP [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на управляющий узел и вычислительные узлы. Например при выполнении операции резервного копирования, управляющий узел и каждом вычислительном узле будет использовать учетные данные учетной записи сетевой службы для получения чтения и разрешение на запись на целевой сервер.  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-add-credentials-for-performing-a-database-backup"></a>A. Добавьте учетные данные для выполнения резервной копии базы данных  
 Следующий пример связывает имя и пароль учетных данных для seattle\david пользователя домена с целевым сервером с IP-адресом 10.172.63.255. Seattle\david пользователь имеет разрешения на чтение и запись на целевой сервер. [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] будет сохранить эти учетные данные и использовать их для чтения и записи с целевого сервера, необходимые для резервного копирования и восстановления.  
  
```  
EXEC sp_pdw_add_network_credentials '10.172.63.255', 'seattle\david', '********';  
```  
  
 Команды резервного копирования требует, что имя сервера ввести IP-адрес.  
  
> [!NOTE]  
>  Для выполнения резервного копирования базы данных через InfiniBand, обязательно используйте InfiniBand IP-адрес резервного сервера.  
  
## <a name="see-also"></a>См. также  
 [sp_pdw_remove_network_credentials &#40;хранилище данных SQL&#41;](../../relational-databases/system-stored-procedures/sp-pdw-remove-network-credentials-sql-data-warehouse.md)  
  
  

