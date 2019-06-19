---
title: Использование PowerShell для создания группы доступности
description: Шаги для создания группы доступности Always On с помощью PowerShell.
ms.custom: seodec18
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], creating
ms.assetid: bc69a7df-20fa-41e1-9301-11317c5270d2
author: MashaMSFT
ms.author: mathoma
manager: jroth
ms.openlocfilehash: 6bc6fcad5f667b0c1224c4d1e897ae9fc30642d0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66793529"
---
# <a name="create-an-always-on-availability-group-using-powershell"></a>Использование PowerShell для создания группы доступности Always On
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В данном разделе описывается использование командлетов PowerShell для создания и настройки группы доступности AlwaysOn в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. *Группа доступности* определяет набор пользовательских баз данных, которые будут действовать при сбое как единое целое, а также набор партнеров по обеспечению отработки отказа, называемых *репликами доступности*и поддерживающих отработку отказа.  
  
> [!NOTE]  
>  Базовые сведения о группах доступности см. в разделе [Обзор групп доступности AlwaysOn (SQL Server)](~/database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md).  
  
> [!NOTE]  
>  Вместо командлетов PowerShell вы можете использовать мастер создания группы доступности или [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Дополнительные сведения см. в статьях [Использование диалогового окна "Создание группы доступности" (среда SQL Server Management Studio)](../../../database-engine/availability-groups/windows/use-the-new-availability-group-dialog-box-sql-server-management-studio.md) и [Создание группы доступности (Transact-SQL)](../../../database-engine/availability-groups/windows/create-an-availability-group-transact-sql.md).  
  
  
##  <a name="PrerequisitesRestrictions"></a> Предварительные условия, ограничения и рекомендации  
  
-   Перед созданием группы доступности необходимо, чтобы экземпляры [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , на которых находятся реплики доступности, были расположены на различных узлах одной отказоустойчивой кластеризации Windows Server (WSFC). Также необходимо обеспечить соответствие экземпляров сервера всем другим предварительным условиям для экземпляров сервера; кроме того, следует выполнить все требования [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] и ознакомиться с соответствующими рекомендациями. Для получения дополнительных сведений настоятельно рекомендуется изучить раздел [Предварительные требования, ограничения и рекомендации для групп доступности AlwaysOn (SQL Server)](~/database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md).  
  
  
##  <a name="Permissions"></a> Permissions  
 Требуется членство в фиксированной роли сервера **sysadmin** и одно из разрешений: CREATE AVAILABILITY GROUP, ALTER ANY AVAILABILITY GROUP или CONTROL SERVER.  
  
  
##  <a name="PowerShellProcedure"></a> использование PowerShell для создания и настройки групп доступности  

###  <a name="SummaryPSStatements"></a> Сводка задач и соответствующие командлеты PowerShell  
 В следующей таблице перечислены основные задачи, входящие в настройку группы доступности, и указывается, какие из них поддерживаются командлетами PowerShell. Задачи [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] должны выполняться в той последовательности, в которой они перечислены в таблице.  
  
|Задача|Командлеты PowerShell (если доступны) или инструкции Transact-SQL|Место выполнения задачи **&#42;**|  
|----------|--------------------------------------------------------------------|---------------------------------|  
|Создание конечной точки зеркального отображения базы данных (одна точка на экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] )|**New-SqlHadrEndPoint**|Выполнить на каждом экземпляре сервера, у которого нет конечной точки зеркального отображения базы данных.<br /><br /> Примечание. Для изменения существующей конечной точки зеркального отображения базы данных используйте **Set-SqlHadrEndpoint**.|  
|Создание группы доступности|Во-первых, используйте командлет **New-SqlAvailabilityReplica** с параметром **-AsTemplate** для создания объекта реплики доступности в памяти для каждой из двух реплик доступности, которые планируется включить в группу доступности.<br /><br /> Затем создайте группу доступности с помощью командлета **New-SqlAvailabilityGroup** , ссылаясь на объекты реплики доступности.|Выполнить на экземпляре сервера, где будет размещена исходная первичная реплика.|  
|Присоединить вторичную реплику к группе доступности|**Join-SqlAvailabilityGroup**|Выполнить на каждом экземпляре сервера, размещающем вторичную реплику.|  
|Подготовьте базу данных-получатель|**Backup-SqlDatabase** и **Restore-SqlDatabase**|Создайте резервные копии на экземпляре сервера, размещающем первичную реплику.<br /><br /> Восстановите резервные копии на каждом из тех экземпляров сервера, на которых размещена вторичная реплика, при помощи параметра восстановления **NoRecovery** . Если пути к файлам различны на компьютерах, на которых размещена основная реплика и целевая вторичная реплика, также следует использовать параметр восстановления **RelocateFile** .|  
|Запуск синхронизации данных с помощью присоединения каждой базы данных-получателя к группе доступности|**Add-SqlAvailabilityDatabase**|Выполнить на каждом экземпляре сервера, размещающем вторичную реплику.|  
  
 \*Для выполнения данной задачи измените каталог (**cd**) на соответствующий экземпляр или экземпляры сервера.  
  
###  <a name="PsProviderLinks"></a> Настройка и использование поставщика SQL Server PowerShell  
  
-   [Поставщик SQL Server PowerShell](../../../relational-databases/scripting/sql-server-powershell-provider.md)  
  
-   [Получение справок по SQL Server PowerShell](../../../relational-databases/scripting/get-help-sql-server-powershell.md)  
  
> [!NOTE]  
>  Чтобы просмотреть синтаксис и пример определенного командлета, воспользуйтесь командлетом **Get-Help** в среде [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell. Дополнительные сведения см. в разделе [Get Help SQL Server PowerShell](../../../relational-databases/scripting/get-help-sql-server-powershell.md).  
  
1.  Перейдите в каталог (**cd**) экземпляра сервера, на котором размещается первичная реплика.  
  
2.  Создайте объект реплики доступности в памяти для первичной реплики.  
  
3.  Создайте объект реплики доступности в памяти для каждой вторичной реплики.  
  
4.  Создайте группу доступности.  
  
    > [!NOTE]  
    >  Максимальная длина имени группы доступности составляет 128 символов.  
  
5.  Присоедините новую вторичную реплику к группе доступности. Дополнительные сведения см. в разделе [Присоединение вторичной реплики к группе доступности (SQL Server)](../../../database-engine/availability-groups/windows/join-a-secondary-replica-to-an-availability-group-sql-server.md).  
  
6.  Для каждой базы данных в группе доступности создайте базу данных-получатель путем восстановления последней резервной копии базы данных-источника с помощью инструкции RESTORE WITH NORECOVERY.  
  
7.  Присоедините каждую новую базу данных-получатель к группе доступности. Дополнительные сведения см. в статьях [Присоединение вторичной реплики к группе доступности (SQL Server)](../../../database-engine/availability-groups/windows/join-a-secondary-replica-to-an-availability-group-sql-server.md).  
  
8.  При необходимости с помощью команды Windows **dir** проверьте содержимое новой группы доступности.  
  
> [!NOTE]  
>  Если учетные записи службы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] экземпляров сервера запускаются в контексте других учетных записей пользователей домена, создайте имя входа для другого экземпляра сервера и предоставьте этому имени разрешение CONNECT для подключения к конечной точке зеркального отображения локальной базы данных.  
  
##  <a name="ExampleConfigureGroup"></a> Пример. Использование PowerShell для создания группы доступности  
 В следующем примере использования PowerShell создается и настраивается простая группа доступности с именем `MyAG` с двумя репликами доступности и с одной базой данных доступности. Пример.  
  
1.  Выполняется резервное копирование базы данных `MyDatabase` и ее журнала транзакций.  
  
2.  Выполняется восстановление базы данных `MyDatabase` и ее журнала транзакций с использованием параметра **-NoRecovery** .  
  
3.  Создается представление первичной реплики в памяти, которая будет размещена локальным экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (с именем `PrimaryComputer\Instance`).  
  
4.  Создается представление вторичной реплики в памяти, которая будет размещена локальным экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (с именем `SecondaryComputer\Instance`).  
  
5.  Создается группа доступности с именем `MyAG`.  
  
6.  Вторичная реплика присоединяется к группе доступности.  
  
7.  База данных-получатель присоединяется к группе доступности.  
  
```  
# Backup my database and its log on the primary  
Backup-SqlDatabase `  
    -Database "MyDatabase" `  
    -BackupFile "\\share\backups\MyDatabase.bak" `  
    -ServerInstance "PrimaryComputer\Instance"  
  
Backup-SqlDatabase `  
    -Database "MyDatabase" `  
    -BackupFile "\\share\backups\MyDatabase.log" `  
    -ServerInstance "PrimaryComputer\Instance" `  
    -BackupAction Log   
  
# Restore the database and log on the secondary (using NO RECOVERY)  
Restore-SqlDatabase `  
    -Database "MyDatabase" `  
    -BackupFile "\\share\backups\MyDatabase.bak" `  
    -ServerInstance "SecondaryComputer\Instance" `  
    -NoRecovery  
  
Restore-SqlDatabase `  
    -Database "MyDatabase" `  
    -BackupFile "\\share\backups\MyDatabase.log" `  
    -ServerInstance "SecondaryComputer\Instance" `  
    -RestoreAction Log `  
    -NoRecovery  
  
# Create an in-memory representation of the primary replica.  
$primaryReplica = New-SqlAvailabilityReplica `  
    -Name "PrimaryComputer\Instance" `  
    -EndpointURL "TCP://PrimaryComputer.domain.com:5022" `  
    -AvailabilityMode "SynchronousCommit" `  
    -FailoverMode "Automatic" `  
    -Version 12 `  
    -AsTemplate  
  
# Create an in-memory representation of the secondary replica.  
$secondaryReplica = New-SqlAvailabilityReplica `  
    -Name "SecondaryComputer\Instance" `  
    -EndpointURL "TCP://SecondaryComputer.domain.com:5022" `  
    -AvailabilityMode "SynchronousCommit" `  
    -FailoverMode "Automatic" `  
    -Version 12 `  
    -AsTemplate  
  
# Create the availability group  
New-SqlAvailabilityGroup `  
    -Name "MyAG" `  
    -Path "SQLSERVER:\SQL\PrimaryComputer\Instance" `  
    -AvailabilityReplica @($primaryReplica,$secondaryReplica) `  
    -Database "MyDatabase"  
  
# Join the secondary replica to the availability group.  
Join-SqlAvailabilityGroup -Path "SQLSERVER:\SQL\SecondaryComputer\Instance" -Name "MyAG"  
  
# Join the secondary database to the availability group.  
Add-SqlAvailabilityDatabase -Path "SQLSERVER:\SQL\SecondaryComputer\Instance\AvailabilityGroups\MyAG" -Database "MyDatabase"  
```  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
 **Настройка экземпляра сервера для групп доступности AlwaysOn**  
  
-   [Включение и отключение групп доступности AlwaysOn (SQL Server)](~/database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)  
  
-   [Создание конечной точки зеркального отображения базы данных для групп доступности AlwaysOn (SQL Server PowerShell)](~/database-engine/availability-groups/windows/database-mirroring-always-on-availability-groups-powershell.md)  
  
 **Настройка свойств группы доступности и реплики**  
  
-   [Смена режима доступности для реплики доступности (SQL Server)](../../../database-engine/availability-groups/windows/change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [Смена режима отработки отказа для реплики доступности (SQL Server)](../../../database-engine/availability-groups/windows/change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [Создание или настройка прослушивателя группы доступности (SQL Server)](../../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [Настройка гибкой политики отработки отказа для обеспечения контроля над автоматическим переходом на другой ресурс (группы доступности AlwaysOn)](~/database-engine/availability-groups/windows/configure-flexible-automatic-failover-policy.md)  
  
-   [Укажите URL-адрес конечной точки при добавлении или изменении реплики доступности (SQL Server)](../../../database-engine/availability-groups/windows/specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [Настройка резервного копирования в репликах доступности (SQL Server)](../../../database-engine/availability-groups/windows/configure-backup-on-availability-replicas-sql-server.md)  
  
-   [Настройка доступа только для чтения в реплике доступности (SQL Server)](../../../database-engine/availability-groups/windows/configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [Настройка маршрутизации только для чтения в группе доступности (SQL Server)](../../../database-engine/availability-groups/windows/configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [Изменение периода ожидания сеанса для реплики доступности (SQL Server)](../../../database-engine/availability-groups/windows/change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
 **Завершение настройки группы доступности**  
  
-   [Присоединение вторичной реплики к группе доступности (SQL Server)](../../../database-engine/availability-groups/windows/join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Подготовка базы данных-получателя для присоединения к группе доступности вручную (SQL Server)](../../../database-engine/availability-groups/windows/manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [Присоединение базы данных-получателя к группе доступности (SQL Server)](../../../database-engine/availability-groups/windows/join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [Создание или настройка прослушивателя группы доступности (SQL Server)](../../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md)  
  
 **Другие способы создания группы доступности**  
  
-   [Использование мастера групп доступности (среда SQL Server Management Studio)](../../../database-engine/availability-groups/windows/use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Использование диалогового окна "Создание группы доступности" (среда SQL Server Management Studio)](../../../database-engine/availability-groups/windows/use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Создание группы доступности (Transact-SQL)](../../../database-engine/availability-groups/windows/create-an-availability-group-transact-sql.md)  
  
 **Устранение неполадок с конфигурацией групп доступности AlwaysOn**  
  
-   [Поиск и устранение неисправностей конфигурации групп доступности AlwaysOn (SQL Server)](~/database-engine/availability-groups/windows/troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
-   [Устранение неполадок с операцией добавления файла, давшей сбой (группы доступности AlwaysOn)](~/database-engine/availability-groups/windows/troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="RelatedContent"></a> См. также  
  
-   **Блоги**  
  
     [Обучающая серия Always ON — HADRON. Использование рабочего пула для баз данных с HADRON](https://blogs.msdn.com/b/psssql/archive/2012/05/17/Always%20On-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
     [Настройка AlwaysOn с помощью SQL Server PowerShell](https://blogs.msdn.microsoft.com/sqlalwayson/2012/02/03/configuring-alwayson-with-sql-server-powershell/)  
  
     [Блоги команды разработчиков SQL Server Always On: официальный блог по SQL Server Always On](https://blogs.msdn.microsoft.com/sqlalwayson/)  
  
     [Блоги инженеров CSS SQL Server](https://blogs.msdn.com/b/psssql/)  
  
-   **Видеоролики**  
  
     [Microsoft SQL Server с рабочим названием Denali Always On, часть 1: вводные сведения о решении следующего поколения по обеспечению высокого уровня доступности](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [Microsoft SQL Server с рабочим названием Denali Always On, часть 2: создание критически важного решения по обеспечению высокого уровня доступности с использованием Always On](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   **Технические документы**  
  
     [Руководство по решениям режима AlwaysOn в Microsoft SQL Server для обеспечения высокой доступности и аварийного восстановления](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [Технические документы Майкрософт Microsoft по SQL Server 2012](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [Технические документы группы консультантов по SQL Server](https://techcommunity.microsoft.com/t5/DataCAT/bg-p/DataCAT/)  
  
## <a name="see-also"></a>См. также:  
 [Конечная точка зеркального отображения базы данных (SQL Server)](../../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md)   
 [Обзор групп доступности AlwaysOn (SQL Server)](~/database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)  
  
  







