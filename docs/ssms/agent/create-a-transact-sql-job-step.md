---
title: Создание шага задания Transact-SQL
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL job step
- job steps [Transact-SQL]
- SQL Server Agent jobs, Transact-SQL step
ms.assetid: 69c571a7-debe-4063-9d38-e4b6a1e8e84c
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 207f7c3cd226ba5fe2bd8d5b708e820d63dd0b2c
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "75245838"
---
# <a name="create-a-transact-sql-job-step"></a>Создание шага задания Transact-SQL
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

В этом разделе описано, как создать шаг задания агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], который исполняет скрипты [!INCLUDE[tsql](../../includes/tsql-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] или управляющих объектов SQL Server.  
  
Эти скрипты шагов задания могут вызывать хранимые процедуры и расширенные хранимые процедуры. Один шаг задания [!INCLUDE[tsql](../../includes/tsql-md.md)] может содержать несколько пакетов и команд GO. Дополнительные сведения о создании заданий см. в разделе [Создание заданий](../../ssms/agent/create-jobs.md).  
  
## <a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="Security"></a>безопасность  
Дополнительные сведения см. в разделе [Обеспечение безопасности агента SQL Server](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-create-a-transact-sql-job-step"></a>Создание шага задания Transact-SQL  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]и разверните его.  
  
2.  Разверните **Агент SQL Server**, создайте задание или щелкните правой кнопкой мыши существующее задание и выберите пункт **Свойства**.  
  
3.  В диалоговом окне **Свойства задания** выберите страницу **Шаги** и нажмите кнопку **Добавить**.  
  
4.  В диалоговом окне **Новый шаг задания** введите **имя шага**задания.  
  
5.  В списке **Тип** выберите **Скрипт Transact-SQL (TSQL)** .  
  
6.  На панели **Команда** введите пакет команд [!INCLUDE[tsql](../../includes/tsql-md.md)] или нажмите кнопку **Открыть** и выберите файл [!INCLUDE[tsql](../../includes/tsql-md.md)] , используемый в качестве команды.  
  
7.  Нажмите кнопку **Синтаксический анализ** для проверки синтаксиса.  
  
8.  Если синтаксис правильный, появится сообщение «Синтаксический анализ успешно завершен». При обнаружении ошибки исправьте ее.  
  
9. Щелкните вкладку **Дополнительно** , чтобы задать следующие параметры шага задания: какое действие необходимо выполнить при успешном или неуспешном выполнении шага задания, сколько раз агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен пытаться выполнить шаг задания, а также файл или таблицу, куда агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может записывать результат выполнения шага задания. Только члены предопределенной роли сервера **sysadmin** могут записывать выходные данные шага задания в файл операционной системы. В таблицу выходные данные могут записывать все пользователи агента SQL Server.  
  
10. Если члену предопределенной роли сервера **sysadmin** нужно выполнить шаг задания в контексте другого имени входа SQL, ему следует выбрать имя входа SQL из списка **Выполнять от имени** .  
  
## <a name="TSQL"></a>Использование Transact-SQL  
  
#### <a name="to-create-a-transact-sql-job-step"></a>Создание шага задания Transact-SQL  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- creates a job step that uses Transact-SQL  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Set database to read only',  
        @subsystem = N'TSQL',  
        @command = N'ALTER DATABASE SALES SET READ_ONLY',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    ```  
  
Дополнительные сведения см. в разделе [sp_add_jobstep (Transact-SQL)](https://msdn.microsoft.com/97900032-523d-49d6-9865-2734fba1c755).  
  
## <a name="SMO"></a>Использование управляющих объектов SQL Server  
**Создание шага задания Transact-SQL**  
  
Воспользуйтесь классом **JobStep** на любом языке программирования, таком как Visual Basic, Visual C# или PowerShell.  
  
