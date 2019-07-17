---
title: tablediff Utility | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- comparing data
- tablediff utility
- tables [SQL Server replication]
- table comparisons [SQL Server]
- command prompt utilities [SQL Server], tablediff
- troubleshooting [SQL Server replication], non-convergence
- non-convergence [SQL Server]
ms.assetid: 3c3cb865-7a4d-4d66-98f2-5935e28929fc
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cb8b8bec38b428ca7b2eea5166867141b34a2405
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68185976"
---
# <a name="tablediff-utility"></a>tablediff, программа
  Служебная программа **tablediff** используется для сравнения данных в двух таблицах на расхождение и особенно полезна для устранения несоответствия данных в топологии репликации. Эта программа может запускаться из командной строки или из пакетного файла и служит для выполнения следующих задач:  
  
-   Построчное сравнение исходной таблицы в экземпляре [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , выступающем в качестве издателя репликации, и целевой таблицы в одном или нескольких экземплярах [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , выступающих в качестве подписчиков репликации.  
  
-   Быстрое сравнение, сравнивающее только схемы и количество строк.  
  
-   Сравнение на уровне столбцов.  
  
-   Формирование скрипта [!INCLUDE[tsql](../includes/tsql-md.md)] для исправления несоответствий на целевом сервере и обеспечения конвергенции исходной и целевой таблиц.  
  
-   Запись результатов операции в файл вывода или в таблицу целевой базы данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
      tablediff   
[ -? ] |   
{  
        -sourceserversource_server_name[\instance_name]  
        -sourcedatabasesource_database-sourcetablesource_table_name   
    [ -sourceschemasource_schema_name ]  
    [ -sourcepasswordsource_password ]  
    [ -sourceusersource_login ]  
    [ -sourcelocked ]  
        -destinationserverdestination_server_name[\instance_name]  
        -destinationdatabasesubscription_database-destinationtabledestination_table   
    [ -destinationschemadestination_schema_name ]  
    [ -destinationpassworddestination_password ]  
    [ -destinationuserdestination_login ]  
    [ -destinationlocked ]  
    [ -blarge_object_bytes ]   
    [ -bfnumber_of_statements ]   
    [ -c ]   
    [ -dt ]   
    [ -ettable_name ]   
    [ -f [ file_name ] ]   
    [ -ooutput_file_name ]   
    [ -q ]   
    [ -rcnumber_of_retries ]   
    [ -riretry_interval ]   
    [ -strict ]  
    [ -tconnection_timeouts ]   
}  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **-?** ]  
 Возвращает список поддерживаемых параметров.  
  
 **-sourceserver** *имя_исходного_сервера*[ **\\** _имя_экземпляра_]  
 Имя исходного сервера. Укажите _источника\_server\_имя_ для экземпляра по умолчанию [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Укажите _источника\_server\_имя_ **\\** _экземпляр\_имя_ для именованного экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 **-sourcedatabase** *база_данных_источник*  
 Имя базы данных-источника.  
  
 **-sourcetable** *имя_исходной_таблицы*  
 Имя проверяемой исходной таблицы.  
  
 **-sourceschema** *имя_исходной_схемы*  
 Владелец схемы исходной таблицы. Владельцем таблицы по умолчанию считается dbo.  
  
 **-sourcepassword** *исходный_пароль*  
 Пароль для имени входа, используемого для подключения к исходному серверу с помощью проверки подлинности [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
> [!IMPORTANT]  
>  По возможности указывайте учетные данные во время выполнения. Если необходимо хранить учетные данные в файле скрипта, необходимо обеспечить его безопасность, чтобы предотвратить несанкционированный доступ.  
  
 **-sourceuser** *исходное_имя_входа*  
 Имя входа, используемое для подключения к исходному серверу с помощью проверки подлинности [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Если *исходное_имя_входа* не указано, для соединения с исходным сервером используется проверка подлинности Windows. [!INCLUDE[ssNoteWinAuthentication](../includes/ssnotewinauthentication-md.md)]  
  
 **-sourcelocked**  
 Исходная таблица блокируется в ходе сравнения при помощи табличных подсказок TABLOCK и HOLDLOCK.  
  
 **-destinationserver** *имя_целевого_сервера*[ **\\** _экземпляр\_имя_]  
 Имя целевого сервера. Укажите *имя_целевого_сервера* для экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]по умолчанию. Укажите _назначения\_server\_имя_ **\\** _экземпляр\_имя_ для именованного экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 **-destinationdatabase** *база_данных_подписки*  
 Имя целевой базы данных.  
  
 **-destinationtable** *целевая_таблица*  
 Имя целевой таблицы.  
  
 **-destinationschema** *имя_целевой_схемы*  
 Владелец схемы целевой таблицы. Владельцем таблицы по умолчанию считается dbo.  
  
 **-destinationpassword** *целевой_пароль*  
 Пароль для имени входа, используемого для подключения к целевому серверу с помощью проверки подлинности [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
> [!IMPORTANT]  
>  По возможности указывайте учетные данные во время выполнения. Если необходимо хранить учетные данные в файле скрипта, необходимо обеспечить его безопасность, чтобы предотвратить несанкционированный доступ.  
  
 **-destinationuser** *целевое_имя_входа*  
 Имя входа, используемое для подключения к целевому серверу с помощью проверки подлинности [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Если *целевое_имя_входа* не указано, для соединения с исходным сервером используется проверка подлинности Windows. [!INCLUDE[ssNoteWinAuthentication](../includes/ssnotewinauthentication-md.md)]  
  
 **-destinationlocked**  
 Целевая таблица блокируется в ходе сравнения при помощи табличных указаний TABLOCK и HOLDLOCK.  
  
 **-b** *число_байтов_больших_объектов*  
 Число байтов для сравнения столбцов, содержащих данные типа больших объектов, к которым относятся: `text`, `ntext`, `image`, `varchar(max)`, `nvarchar(max)` и `varbinary(max)`. *число_байтов_больших_объектов* по умолчанию имеет размер столбца. Любые данные, размер которых превышает значение *число_байтов_больших_объектов* , не учитываются при сравнении.  
  
 **-bf**  *число_инструкций*  
 Число инструкций [!INCLUDE[tsql](../includes/tsql-md.md)] для записи в текущий файл скрипта [!INCLUDE[tsql](../includes/tsql-md.md)] при использовании параметра **-f** . Когда число инструкций [!INCLUDE[tsql](../includes/tsql-md.md)] превышает значение *число_инструкций*, создается новый файл скрипта [!INCLUDE[tsql](../includes/tsql-md.md)] .  
  
 **-c**  
 Сравнение на уровне столбцов.  
  
 **-dt**  
 Удаление таблицы результатов, указанной в аргументе *имя_таблицы*, если она уже существует.  
  
 **-et** *имя_таблицы*  
 Имя создаваемой таблицы результатов. Если таблица уже существует, необходимо использовать аргумент **-DT** , иначе операция завершится ошибкой.  
  
 **-f** [ *имя_файла* ]  
 Формирует скрипт [!INCLUDE[tsql](../includes/tsql-md.md)] , по которому обеспечивается конвергенция таблицы на целевом сервере и таблицы на исходном сервере. Можно дополнительно указать имя и путь для создаваемого файла скрипта [!INCLUDE[tsql](../includes/tsql-md.md)] . Если параметр *имя_файла* не указан, файл скрипта [!INCLUDE[tsql](../includes/tsql-md.md)] создается в каталоге, в котором запущена данная программа.  
  
 **-o** *имя_выходного_файла*  
 Полное имя и путь файла вывода.  
  
 **-q**  
 Быстрое сравнение, сравнивающее только схемы и количество строк.  
  
 **-rc** *число_повторных_попыток*  
 Количество попыток повтора программой неудачно завершившейся операции.  
  
 **-ri**  *интервал_повтора*  
 Интервал в секундах между повторными попытками.  
  
 **-strict**  
 Строгая проверка исходной и целевой схем.  
  
 **-t** *время_ожидания_соединения*  
 Устанавливает время ожидания в секундах для соединений с исходным сервером и целевым сервером.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
|Значение|Описание|  
|-----------|-----------------|  
|**0**|Success|  
|**1**|Критическая ошибка|  
|**2**|Различия таблиц|  
  
## <a name="remarks"></a>Примечания  
 Служебную программу **tablediff** нельзя использовать для обращения к серверам, отличным от[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 Таблицы со столбцами с данными типа `sql_variant` не поддерживаются.  
  
 По умолчанию служебная программа **tablediff** поддерживает перечисленные ниже сопоставления типов данных между исходными и целевыми столбцами.  
  
|Тип данных источника|Тип данных назначения|  
|----------------------|---------------------------|  
|`tinyint`|`smallint`, `int` или `bigint`|  
|`smallint`|`int` или `bigint`|  
|`int`|`bigint`|  
|`timestamp`|`varbinary`|  
|`varchar(max)`|`text`|  
|`nvarchar(max)`|`ntext`|  
|`varbinary(max)`|`image`|  
|`text`|`varchar(max)`|  
|`ntext`|`nvarchar(max)`|  
|`image`|`varbinary(max)`|  
  
 Параметр **-strict** запрещает такое сопоставление и выполняет строгую проверку.  
  
 Исходная таблица при данном сравнении должна содержать хотя бы один столбец первичного ключа, столбец идентификаторов или столбец ROWGUID. При использовании параметра **-strict** целевая таблица также должна содержать столбец первичного ключа, столбец идентификаторов или столбец ROWGUID.  
  
 Скрипт [!INCLUDE[tsql](../includes/tsql-md.md)] , создаваемый для приведения целевой таблицы в состояние конвергенции, не включает следующие типы данных:  
  
-   `varchar(max)`  
  
-   `nvarchar(max)`  
  
-   `varbinary(max)`  
  
-   `timestamp`  
  
-   **xml**  
  
-   `text`  
  
-   `ntext`  
  
-   `image`  
  
## <a name="permissions"></a>Разрешения  
 Для сравнения таблиц на сравниваемые объекты таблиц необходимо иметь разрешения SELECT ALL.  
  
 Для использования параметра **-et** необходимо быть членом предопределенной роли базы данных db_owner или как минимум иметь разрешение CREATE TABLE в базе данных подписки и разрешение ALTER на схему конечного владельца на целевом сервере.  
  
 Для использования параметра **-dt** необходимо быть членом предопределенной роли базы данных db_owner или как минимум иметь разрешение ALTER на схему конечного владельца на целевом сервере.  
  
 Чтобы использовать параметр **-o** или **-f** , необходимо иметь разрешения на запись в указанный каталог файлов.  
  
## <a name="see-also"></a>См. также  
 [Сравнение реплицируемых таблиц на предмет различий (программирование репликации)](../relational-databases/replication/administration/compare-replicated-tables-for-differences-replication-programming.md)  
  
  
