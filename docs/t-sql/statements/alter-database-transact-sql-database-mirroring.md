---
description: Зеркальное отображение базы данных ALTER DATABASE (Transact-SQL)
title: Зеркальное отображение базы данных ALTER DATABASE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 02/21/2019
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- witness [SQL Server], establishing
- manual failover [SQL Server]
- ALTER DATABASE statement, database mirroring
- database mirroring [SQL Server], Transact-SQL
ms.assetid: 27a032ef-1cf6-4959-8e67-03d28c4b3465
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 03bd40c682b2d0ad36952c7f59c2b3d95d16a5e9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88426916"
---
# <a name="alter-database-transact-sql-database-mirroring"></a>Зеркальное отображение базы данных ALTER DATABASE (Transact-SQL)

[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

> [!NOTE]
> [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Вместо этого используйте [!INCLUDE[ssHADR](../../includes/sshadr-md.md)].

Управляет зеркальным отображением базы данных. Значения, указанные с параметрами зеркального отображения базы данных, применяются к обеим копиям базы данных и к сеансу зеркального отображения базы данных в целом. В инструкции ALTER DATABASE допустим только один \<database_mirroring_option>.

> [!NOTE]
> Конфигурацию зеркального отображения базы данных рекомендуется выполнять в часы с наименьшей загрузкой, поскольку этот процесс может повлиять на производительность.

Параметры ALTER DATABASE см. в статье [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md). Параметры ALTER DATABASE SET см. в статье [Параметры ALTER DATABASE SET (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-set-options.md).

![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)

## <a name="syntax"></a>Синтаксис

```syntaxsql

ALTER DATABASE database_name
SET { <partner_option> | <witness_option> }
  <partner_option> ::=
    PARTNER { = 'partner_server'
            | FAILOVER
            | FORCE_SERVICE_ALLOW_DATA_LOSS
            | OFF
            | RESUME
            | SAFETY { FULL | OFF }
            | SUSPEND
            | TIMEOUT integer
            }
  <witness_option> ::=
    WITNESS { = 'witness_server'
            | OFF
            }
  
```

[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы

> [!IMPORTANT]
> Команда SET PARTNER или SET WITNESS может быть завершена успешно, но позднее — привести к ошибке.
> [!NOTE]
> Параметры зеркального отображения базы данных ALTER DATABASE недоступны в автономной базе данных.

*database_name* — имя изменяемой базы данных.

PARTNER \<partner_option> Управляет свойствами базы данных, которые определяют партнеров по обеспечению отработки отказа при сбоях сеанса зеркального отображения базы данных и их поведение. Некоторые параметры инструкции SET PARTNER могут быть установлены на любом участнике; другие — разграничены для основного или для зеркального сервера. Дополнительные сведения см. в следующем описании индивидуальных параметров PARTNER. Предложение SET PARTNER влияет на обе копии базы данных независимо от участника, на которого оно указывает.

Для выполнения инструкции SET PARTNER требуется, чтобы параметры STATE конечных точек обоих участников имели значение STARTED. Также учтите, что параметр ROLE конечной точки зеркального отображения базы данных каждого экземпляра сервера-участника должен быть установлен в состояние PARTNER или ALL. Сведения об указании конечной точки см. в статье [Создание конечной точки зеркального отображения базы данных с проверкой подлинности Windows (Transact-SQL)](../../database-engine/database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md). Чтобы узнать роль и состояние базы данных конечной точки зеркального отображения экземпляра сервера, выполните на этом экземпляре следующую инструкцию языка [!INCLUDE[tsql](../../includes/tsql-md.md)]:

```sql
SELECT role_desc, state_desc FROM sys.database_mirroring_endpoints
```

**\<partner_option> ::=**

> [!NOTE]
> В одном предложении SET PARTNER допустим только один аргумент \<partner_option>.

**'** _partner_server_ **'**  — указывает сетевой адрес сервера экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], чтобы задействовать его как партнера по обеспечению отработки отказа в новом сеансе зеркального отображения базы данных. Для каждого сеанса необходимы два участника: один запускается как основной сервер, второй — как зеркальный сервер. Рекомендуется, чтобы эти партнеры находились на разных компьютерах.

Этот параметр указывается один раз для сеанса на каждом участнике. Для инициализации сеанса зеркального отображения базы данных необходимо выполнить две инструкции ALTER DATABASE *database* SET PARTNER **='** _partner_server_ **'** . Их порядок важен. Вначале подключитесь к зеркальному серверу и укажите основной экземпляр сервера как *partner_server* (SET PARTNER **='** _principal_server_ **'** ). Затем подключитесь к основному серверу и укажите зеркальный экземпляр сервера как *partner_server* (SET PARTNER **='** _mirror_server_ **'** ); в результате запустится сеанс зеркального отображения базы данных между этими двумя партнерами. Дополнительные сведения см. в статье [Настройка зеркального отображения базы данных (SQL Server)](../../database-engine/database-mirroring/setting-up-database-mirroring-sql-server.md).

Значением аргумента *partner_server* является сетевой адрес сервера. Оно имеет следующий синтаксис:

TCP **://** _\<system-address>_ **:** _\<port>_

где

- *\<system-address>* — строка, такая как адрес системы, полное доменное имя или IP-адрес, однозначно идентифицирующий целевую компьютерную систему.
- *\<port>* — порт, связанный с конечной точкой зеркального отображения, принадлежащей экземпляру сервера-участника.

Дополнительные сведения см. в статье [Указание сетевого адреса сервера (зеркальное отображение базы данных)](../../database-engine/database-mirroring/specify-a-server-network-address-database-mirroring.md).

В следующем примере показано предложение SET PARTNER **='** _partner_server_ **'** :

```
'TCP://MYSERVER.mydomain.Adventure-Works.com:7777'
```

> [!IMPORTANT]
> Если сеанс установлен с помощью инструкции ALTER DATABASE, а не с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], он будет установлен с полной безопасностью транзакций по умолчанию (параметр SAFETY установлен в состояние FULL) и будет работать в режиме повышенной безопасности без возможности автоматической отработки отказа. Чтобы разрешить автоматическую отработку отказа, настройте следящий сервер для работы в режиме высокой производительности и отключите безопасность транзакций (SAFETY OFF).

FAILOVER — обеспечивает ручное переключение с основного сервера на зеркальный при сбое. Параметр FAILOVER можно указать только на основном сервере. Этот параметр допустим только в том случае, если параметр SAFETY установлен в состояние FULL (значение по умолчанию).

Для параметра FAILOVER контекстом должна быть база данных **master**.

FORCE_SERVICE_ALLOW_DATA_LOSS — переключает обслуживание базы данных на зеркальный сервер при сбое синхронизации основного сервера с базой данных или в синхронизированном состоянии, когда автоматическая отработка отказа не происходит.

Рекомендуется включать вынужденное обслуживание только в том случае, если основной сервер больше не работает. Иначе некоторые клиенты могут продолжить обращаться к оригинальной основной базе данных вместо новой основной базы данных.
Параметр FORCE_SERVICE_ALLOW_DATA_LOSS доступен только на зеркальном сервере и только при соблюдении всех следующих условий:

- основной сервер недоступен;
- параметр WITNESS установлен в состояние OFF или свидетель подключен к зеркальному серверу.

Переключайте обслуживание только в случае готовности рискнуть потерей некоторых данных для немедленного восстановления обслуживания базы данных.

При переключении обслуживания сеанс приостанавливается, сохраняя все данные в базе данных оригинального главного сервера. Как только оригинальная основная база данных начала обслуживаться и стала доступна для связи с новым основным сервером, администратор базы данных может возобновить обслуживание. При возобновлении сеанса любые неотправленные записи журнала и соответствующие обновления будут утеряны.

OFF — прекращает сеанс зеркального отображения базы данных и удаляются сведения об этом сеансе из базы данных. Значение OFF можно указать для любого из участников. Дополнительные сведения о последствиях удаления зеркального отображения базы данных см. в статье [Удаление зеркального отображения базы данных (SQL Server)](../../database-engine/database-mirroring/removing-database-mirroring-sql-server.md).

RESUME — возобновляет приостановленный сеанс зеркального отображения базы данных. Параметр RESUME можно указать только на основном сервере.

SAFETY { FULL | OFF } — устанавливает уровень безопасности транзакций. Параметр SAFETY можно указать только на основном сервере.

Значение по умолчанию FULL. При полном уровне безопасности сеанс зеркального отображения базы данных выполняется синхронно (в *режиме повышенной безопасности*). Если параметр SAFETY находится в состоянии OFF, сеанс зеркального отображения базы данных выполняется асинхронно (в *высокопроизводительном режиме*).

Поведение режима высокой безопасности частично зависит от следящего сервера, как показано далее.

- Если безопасность установлена в состояние FULL и для сеанса установлен следящий сервер, то сеанс выполняется в режиме повышенной безопасности с автоматической отработкой отказа. Когда основной сервер становится недоступным, сеанс автоматически переключается на другой ресурс при условии, что база данных находится в синхронном состоянии, а экземпляры зеркального и следящего серверов остаются подключенными друг к другу (имеют кворум). Дополнительные сведения см. в статье [Кворум. Как следящий сервер влияет на доступность базы данных (зеркальное отображение базы данных)](../../database-engine/database-mirroring/quorum-how-a-witness-affects-database-availability-database-mirroring.md).

  Если свидетель установлен для сеанса, но в настоящее время не подключен, потеря зеркального сервера вынудит основной сервер выключиться.

- Если безопасность установлена в состояние FULL, а следящий сервер находится в состоянии OFF, сеанс выполняется в режиме повышенной безопасности без возможности автоматической отработки отказа. При отказе экземпляра зеркального сервера экземпляр основного сервера остается незатронутым. При отказе экземпляра основного сервера можно переключить обслуживание на экземпляр зеркального сервера (с возможной потерей данных).

- Если параметр SAFETY установлен в состояние OFF, сеанс выполняется в высокопроизводительном режиме, в котором ни автоматическая отработка отказа, ни отработка отказа вручную не поддерживаются. Однако проблемы на зеркальном сервере не затрагивают основной сервер, и, если экземпляр основного сервера отключается, при необходимости можно переключить обслуживание (с возможной потерей данных) на экземпляр зеркального сервера, если параметр WITNESS установлен в состояние OFF или если следящий сервер в настоящее время подключен к зеркальному серверу. Дополнительные сведения о переключении обслуживания см. в подразделе «FORCE_SERVICE_ALLOW_DATA_LOSS», расположенном выше в этом разделе.

> [!IMPORTANT]
> Режим высокой производительности не предназначен для использования свидетеля. Однако всякий раз, когда параметру SAFETY присваивается значение OFF, настоятельно рекомендуется проверить, что параметр WITNESS находится в состоянии OFF.

SUSPEND приостанавливает сеанс зеркального отображения базы данных.

Значение SUSPEND можно указать на любом участнике.

TIMEOUT *integer* указывает интервал времени ожидания в секундах. Интервал времени ожидания — это максимальное время, в течение которого экземпляр сервера ожидает получения сообщения PING от другого экземпляра в сеансе зеркального отображения перед тем, как сделать вывод о том, что другой экземпляр отключен.

Параметр TIMEOUT можно указать только на основном сервере. Если этот параметр не определить, интервал времени по умолчанию — 10 секунд. При указании числа 5 или больше интервал времени ожидания будет установлен в указанное количество секунд. При указании значения интервала времени ожидания от 0 до 4 секунд интервал времени ожидания автоматически будет установлен в 5 секунд.

> [!IMPORTANT]
> Рекомендуется установить интервал времени ожидания в 10 секунд или более. При установке значения меньше 10 секунд возникает вероятность пропуска команды PING в сильно загруженной системе и вероятность ошибочного сообщения об ошибке.

Дополнительные сведения см. в статье [Possible Failures During Database Mirroring](../../database-engine/database-mirroring/possible-failures-during-database-mirroring.md).

WITNESS \<witness_option> Управляет свойствами базы данных, которые определяют свидетеля зеркального отображения базы данных. Предложение SET WITNESS влияет на обе копии базы данных, указать его можно только на основном сервере. Если для сеанса установлен свидетель, для обслуживания базы данных необходим кворум, независимо от настройки параметра SAFETY; дополнительные сведения см. в разделе [Кворум. Как следящий сервер влияет на доступность базы данных (зеркальное отображение базы данных)](../../database-engine/database-mirroring/quorum-how-a-witness-affects-database-availability-database-mirroring.md).

Рекомендуется, чтобы следящий сервер и партнеры по обеспечению отработки отказа находились на отдельных компьютерах. Сведения о следящем сервере см. в разделе [Следящий сервер зеркального отображения базы данных](../../database-engine/database-mirroring/database-mirroring-witness.md).

Для выполнения инструкции SET WITNESS параметр STATE конечных точек экземпляров основного и следящего сервера должен быть установлен в состояние STARTED. Также учтите, что параметр ROLE конечной точки зеркального отображения базы данных экземпляра следящего сервера должен быть установлен в состояние PARTNER или ALL. Сведения об определении конечной точки см. в статье [Конечная точка зеркального отображения базы данных (SQL Server)](../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md).

Чтобы узнать роль и состояние базы данных конечной точки зеркального отображения экземпляра сервера, выполните на этом экземпляре следующую инструкцию языка [!INCLUDE[tsql](../../includes/tsql-md.md)]:

```sql
SELECT role_desc, state_desc FROM sys.database_mirroring_endpoints
```

> [!NOTE]
> Свойства базы данных не могут быть установлены на свидетеле.

 **\<witness_option> ::=**

> [!NOTE]
> В одном предложении SET WITNESS допустим только один аргумент \<witness_option>.

 **'** _witness_server_ **'**  — указывает экземпляр компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)], чтобы задействовать его в качестве следящего сервера для сеанса зеркального отображения базы данных. Инструкции SET WITNESS можно указывать только на основном сервере.

В инструкции SET WITNESS **='** _witness_server_ **'** statement, the syntax of *witness_server* такой же, как синтаксис параметра *partner_server*.

OFF — удаляет свидетеля из сеанса зеркального отображения базы данных. При установке свидетеля в состояние OFF отключается автоматическая отработка отказа. Если база данных установлена в состояние FULL SAFETY, а свидетель установлен в состояние OFF, отказ зеркального сервера заставит основной сервер сделать базу данных недоступной.

## <a name="remarks"></a>Remarks

## <a name="examples"></a>Примеры

### <a name="a-creating-a-database-mirroring-session-with-a-witness"></a>A. Создание сеанса зеркального отображения базы данных со свидетелем

Установка зеркального отображения базы данных со следящим сервером требует настройки безопасности и подготовки зеркальной базы данных, а также использует инструкцию ALTER DATABASE, чтобы установить участников. Пример полного процесса установки см. в статье [Настройка зеркального отображения базы данных (SQL Server)](../../database-engine/database-mirroring/setting-up-database-mirroring-sql-server.md).

### <a name="b-manually-failing-over-a-database-mirroring-session"></a>Б. Ручной переход на другой ресурс в сеансе зеркального отображения базы данных

Отработка отказа вручную может быть инициализирована любым участником зеркального отображения базы данных. Перед переходом на другой ресурс необходимо проверить, что сервер, который считается текущим основным сервером, действительно является основным сервером. Например, для базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] на экземпляре сервера, который предположительно является основным сервером в настоящий момент, выполните следующий запрос:

```sql
SELECT db.name, m.mirroring_role_desc
FROM sys.database_mirroring m
JOIN sys.databases db
ON db.database_id = m.database_id
WHERE db.name = N'AdventureWorks2012';
GO
```

Если экземпляр сервера действительно является основным, значением `mirroring_role_desc` будет `Principal`. Если этот экземпляр сервера был зеркальным сервером, инструкция `SELECT` возвратит `Mirror`.

В следующем примере предполагается, что сервер является текущим основным сервером.

1. Ручной переход на другой ресурс участника зеркального отображения базы данных:

    ```sql
    ALTER DATABASE AdventureWorks2012 SET PARTNER FAILOVER;
    GO
    ```
  
2. Чтобы проверить результаты отработки отказа на новое зеркало, выполните следующий запрос:
  
    ```sql
    SELECT db.name, m.mirroring_role_desc
    FROM sys.database_mirroring m
    JOIN sys.databases db
    ON db.database_id = m.database_id
    WHERE db.name = N'AdventureWorks2012';
    GO
    ```
  Текущее значение параметра `mirroring_role_desc` теперь `Mirror`.

## <a name="see-also"></a>См. также:

- [CREATE DATABASE](../../t-sql/statements/create-database-transact-sql.md?view=sql-server-2017)
- [DATABASEPROPERTYEX](../../t-sql/functions/databasepropertyex-transact-sql.md)
- [sys.database_mirroring_witnesses](../../relational-databases/system-catalog-views/database-mirroring-witness-catalog-views-sys-database-mirroring-witnesses.md)
