---
title: Системные хранимые процедуры (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 02/21/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sql13.TSQLSysNoExpandPortal.f1
- sql13.TSQLSysNoExpandPortal.f1_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- stored procedures [SQL Server]
- APIs [SQL Server]
- stored procedures [SQL Server], categories
- system stored procedures [SQL Server], categories
- system stored procedures [SQL Server]
ms.assetid: a5c4d5b8-5a24-4a2d-99b4-d003b546ee3a
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 020d75e780dcc2036b70348fa57cf1007ce0e401
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68037319"
---
# <a name="system-stored-procedures-transact-sql"></a>Системные хранимые процедуры (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  В [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] многие задачи администрирования и сбора информации можно выполнять с помощью системных хранимых процедур. Системные хранимые процедуры объединяются в категории, перечисленные в следующей таблице.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Категория|Description|  
|--------------|-----------------|  
|[Активные хранимые процедуры георепликации](https://msdn.microsoft.com/library/81658ee4-4422-4d73-bf7a-86a07422cb0d)|Используется для управления конфигурациями активной георепликации в базе данных SQL Azure|  
|[Хранимые процедуры для работы с каталогом](../../relational-databases/system-stored-procedures/catalog-stored-procedures-transact-sql.md)|Используются для реализации функций словаря данных ODBC и изоляции ODBC-приложений от изменений во внутренних системных таблицах.|  
|[Хранимые процедуры системы отслеживания измененных данных](../../relational-databases/system-stored-procedures/change-data-capture-stored-procedures-transact-sql.md)|Используются для включения, отключения или подготовки отчетов об объектах системы отслеживания измененных данных.|  
|[Хранимые процедуры для работы с курсорами](../../relational-databases/system-stored-procedures/cursor-stored-procedures-transact-sql.md)|Используются для реализации переменной функциональности курсоров.|  
|[Хранимые процедуры сборщика данных](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)|Используется для работы со сборщиком данных и следующими компонентами: наборами элементов сбора, элементами коллекций и типами коллекций.|  
|[Хранимые процедуры для работы с ядром СУБД](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)|Используются для выполнения общих задач по обслуживанию компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].|  
|[Database Mail хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)|Используются для работы с электронной почтой в пределах экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Хранимые процедуры для работы с планами обслуживания базы данных](../../relational-databases/system-stored-procedures/database-maintenance-plan-stored-procedures-transact-sql.md)|Используются для выполнения основных задач, необходимых для управления производительностью базы данных.|  
|[Хранимые процедуры для работы с распределенными запросами](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)|Используются для реализации распределенных запросов и управления ими.|  
|[Хранимые процедуры FILESTREAM и FileTable &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/54beca08-c012-4ebd-aa68-d8a10d221b64)|Используется для настройки и управления функциями FILESTREAM и FileTable.|  
|[Правила брандмауэра хранимые процедуры &#40;базе данных SQL Azure&#41;](../../relational-databases/system-stored-procedures/firewall-rules-stored-procedures-azure-sql-database.md)|Используется для настройки брандмауэра базы данных SQL Azure.|  
|[Хранимые процедуры для работы с полнотекстовым поиском](../../relational-databases/system-stored-procedures/full-text-search-and-semantic-search-stored-procedures-transact-sql.md)|Используются для создания полнотекстовых индексов и запросов к ним.|  
|[Общие расширенные хранимые процедуры](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)|Используются, чтобы предоставить внешним программам интерфейс к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для выполнения различных задач обслуживания.|  
|[Хранимые процедуры для работы с доставкой журналов](../../relational-databases/system-stored-procedures/log-shipping-stored-procedures-transact-sql.md)|Используются для создания, изменения и отслеживания конфигураций доставки журналов.|  
|[Хранимые процедуры хранилища управляющих данных &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/management-data-warehouse-stored-procedures-transact-sql.md)|Используется для настройки хранилища управляющих данных.|  
|[Хранимые процедуры OLE Automation](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)|Используются, чтобы включить стандартные объекты OLE-автоматизации использования в стандартном пакете [!INCLUDE[tsql](../../includes/tsql-md.md)].|  
|[Хранимые процедуры управления на основе политики](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)|Используется для управления на основе политики.|  
|[Хранимые процедуры PolyBase](https://msdn.microsoft.com/library/a522b303-bd1b-410b-92d1-29c950a15ede)|Добавление или удаление компьютера из масштабируемой группы Polybase.|  
|[Хранимые процедуры хранилища запросов &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)|Используется для настройки производительности.|  
|[Хранимые процедуры репликации](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)|Используются для управления репликацией.|  
|[Хранимые процедуры для обеспечения безопасности](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)|Используются для управления безопасностью.|  
|[Хранимые процедуры резервного копирования моментальных снимков](https://msdn.microsoft.com/library/c278db87-5770-4037-a1e6-b9853a943339)|Используется для удаления резервной копии FILE_SNAPSHOT вместе со всеми ее моментальными снимками или для удаления отдельного моментального снимка файла резервной копии.|  
|[Хранимые процедуры пространственного индекса ](https://msdn.microsoft.com/library/1be0f34e-3d5a-4a1f-9299-bd482362ec7a)|Используется для анализа и повышения производительности пространственных индексов.|  
|[Хранимые процедуры для работы с агентом SQL Server](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)|Используются приложением [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] для наблюдения за производительностью и активностью.|  
|[Хранимые процедуры для работы с приложением SQL Server Profiler](../../relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql.md)|Используются агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для управления запланированных или зависящих от событий действий.|  
|[Stretch Database хранимых процедур](../../relational-databases/system-stored-procedures/stretch-database-extended-stored-procedures-transact-sql.md)|Используется для управления Stretch Database.|  
|[Хранимые процедуры временных таблиц](https://msdn.microsoft.com/library/f28ca74e-7876-4592-b794-e78e3690fff6)|Использование для временных таблиц|  
|[Хранимые процедуры для работы с XML](../../relational-databases/system-stored-procedures/xml-stored-procedures-transact-sql.md)|Используются для работы с текстом в формате XML.|  
  
> [!NOTE]  
>  Если не оговорено другое, все системные хранимые процедуры возвращают значение 0, что означает успешное выполнение процедуры. Для сигнализации об ошибке возвращается ненулевое значение.  
  
## <a name="api-system-stored-procedures"></a>Системные хранимые процедуры для работы с API  
 Пользователи, запускающие приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] для приложений ADO, OLE DB и ODBC, могут заметить, что эти приложения используют системные хранимые процедуры, не описанные в справочнике по [!INCLUDE[tsql](../../includes/tsql-md.md)]. Эти хранимые процедуры используются [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщиком собственного клиента OLE DB и драйвером ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента для реализации функций API базы данных. Эти хранимые процедуры — всего лишь механизм, задействованный поставщиком или драйвером для передачи запросов пользователя экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Они предназначены только для внутреннего использования поставщиком или драйвером. Явное обращение из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]приложения на основе не поддерживается.  
  
 Хранимые процедуры sp_createorphan и sp_droporphans используются для обработки в ODBC **ntext**, **Text**и **Image** .  
  
 Хранимая процедура sp_reset_connection используется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для поддержки вызовов в транзакциях удаленных хранимых процедур. Кроме того, эта хранимая процедура инициирует события Audit Login и Audit Logout при повторном использовании соединения из пула соединений.  
  
 Системные хранимые процедуры в следующих таблицах используются внутри экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или через клиентские API и не предназначены для общего пользования. Они подвержены изменению, и совместимость не гарантируется.  
  
 Следующие хранимые процедуры описаны в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
|||  
|-|-|  
|sp_catalogs|sp_column_privileges, хранимая процедура|  
|sp_column_privileges_ex|sp_columns|  
|sp_columns_ex|sp_databases|  
|sp_cursor|sp_cursorclose|  
|sp_cursorexecute|sp_cursorfetch|  
|sp_cursoroption|sp_cursoropen|  
|sp_cursorprepare|sp_cursorprepexec|  
|sp_cursorunprepare|sp_execute|  
|sp_datatype_info|sp_fkeys|  
|sp_foreignkeys|sp_indexes|  
|sp_pkeys, хранимая процедура|sp_primarykeys|  
|sp_prepare|sp_prepexec|  
|sp_prepexecrpc|sp_unprepare|  
|sp_server_info|sp_special_columns|  
|sp_sproc_columns|sp_statistics|  
|sp_table_privileges|sp_table_privileges_ex|  
|sp_tables|sp_tables_ex|  
  
 Следующие хранимые процедуры в документации не описаны:  
  
|||  
|-|-|  
|sp_assemblies_rowset|sp_assemblies_rowset_rmt|  
|sp_assemblies_rowset2|sp_assembly_dependencies_rowset|  
|sp_assembly_dependencies_rowset_rmt|sp_assembly_dependencies_rowset2|  
|sp_bcp_dbcmptlevel|sp_catalogs_rowset|  
|sp_catalogs_rowset;2|sp_catalogs_rowset;5|  
|sp_catalogs_rowset_rmt|sp_catalogs_rowset2|  
|sp_check_constbytable_rowset|sp_check_constbytable_rowset;2|  
|sp_check_constbytable_rowset2|sp_check_constraints_rowset|  
|sp_check_constraints_rowset;2|sp_check_constraints_rowset2|  
|sp_column_privileges_rowset|sp_column_privileges_rowset;2|  
|sp_column_privileges_rowset;5|sp_column_privileges_rowset_rmt|  
|sp_column_privileges_rowset2|sp_columns_90|  
|sp_columns_90_rowset|sp_columns_90_rowset_rmt|  
|sp_columns_90_rowset2|sp_columns_ex_90|  
|sp_columns_rowset|sp_columns_rowset;2|  
|sp_columns_rowset;5|sp_columns_rowset_rmt|  
|sp_columns_rowset2|sp_constr_col_usage_rowset|  
|sp_datatype_info_90|sp_ddopen;1|  
|sp_ddopen;10|sp_ddopen;11|  
|sp_ddopen;12|sp_ddopen;13|  
|sp_ddopen;2|sp_ddopen;3|  
|sp_ddopen;4|sp_ddopen;5|  
|sp_ddopen;6|sp_ddopen;7|  
|sp_ddopen;8|sp_ddopen;9|  
|sp_foreign_keys_rowset|sp_foreign_keys_rowset;2|  
|sp_foreign_keys_rowset;3|sp_foreign_keys_rowset;5|  
|sp_foreign_keys_rowset_rmt|sp_foreign_keys_rowset2|  
|sp_foreign_keys_rowset3|sp_indexes_90_rowset|  
|sp_indexes_90_rowset_rmt|sp_indexes_90_rowset2|  
|sp_indexes_rowset|sp_indexes_rowset;2|  
|sp_indexes_rowset;5|sp_indexes_rowset_rmt|  
|sp_indexes_rowset2|sp_linkedservers_rowset|  
|sp_linkedservers_rowset;2|sp_linkedservers_rowset2|  
|sp_oledb_database|sp_oledb_defdb|  
|sp_oledb_deflang|sp_oledb_language|  
|sp_oledb_ro_usrname|sp_primary_keys_rowset|  
|sp_primary_keys_rowset;2|sp_primary_keys_rowset;3|  
|sp_primary_keys_rowset;5|sp_primary_keys_rowset_rmt|  
|sp_primary_keys_rowset2|sp_procedure_params_90_rowset|  
|sp_procedure_params_90_rowset2|sp_procedure_params_rowset|  
|sp_procedure_params_rowset;2|sp_procedure_params_rowset2|  
|sp_procedures_rowset|sp_procedures_rowset;2|  
|sp_procedures_rowset2|sp_provider_types_90_rowset|  
|sp_provider_types_rowset|sp_schemata_rowset|  
|sp_schemata_rowset;3|sp_special_columns_90|  
|sp_sproc_columns_90|sp_statistics_rowset|  
|sp_statistics_rowset;2|sp_statistics_rowset2|  
|sp_stored_procedures|sp_table_constraints_rowset|  
|sp_table_constraints_rowset;2|sp_table_constraints_rowset2|  
|sp_table_privileges_rowset|sp_table_privileges_rowset;2|  
|sp_table_privileges_rowset;5|sp_table_privileges_rowset_rmt|  
|sp_table_privileges_rowset2|sp_table_statistics_rowset|  
|sp_table_statistics_rowset;2|sp_table_statistics2_rowset|  
|sp_tablecollations|sp_tablecollations_90|  
|sp_tables_info_90_rowset|sp_tables_info_90_rowset_64|  
|sp_tables_info_90_rowset2|sp_tables_info_90_rowset2_64|  
|sp_tables_info_rowset|sp_tables_info_rowset;2|  
|sp_tables_info_rowset_64|sp_tables_info_rowset_64;2|  
|sp_tables_info_rowset2|sp_tables_info_rowset2_64|  
|sp_tables_rowset;2|sp_tables_rowset;5|  
|sp_tables_rowset_rmt|sp_tables_rowset2|  
|sp_usertypes_rowset|sp_usertypes_rowset_rmt|  
|sp_usertypes_rowset2|sp_views_rowset|  
|sp_views_rowset2|sp_xml_schema_rowset|  
|sp_xml_schema_rowset2||  
  
## <a name="see-also"></a>См. также:  
 [Создание процедуры &#40;Transact-SQL&#41;](../../t-sql/statements/create-procedure-transact-sql.md)   
 [&#40;ядро СУБД хранимых процедур&#41;](../../relational-databases/stored-procedures/stored-procedures-database-engine.md)   
 [Выполнение хранимых процедур &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/stored-procedures-running.md)   
 [Выполнение хранимых процедур](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)   
 [Ядро СУБД хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Выполнение хранимых процедур](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
  
