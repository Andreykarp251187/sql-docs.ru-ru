---
title: Программы командной строки SQL (ядро СУБД) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- command prompt utilities [SQL Server]
- command prompt utilities [SQL Server], about command prompt utilities
- command prompt [SQL Server]
- utilities [SQL Server], command prompt
- command prompt [SQL Server], utilities
ms.assetid: 48364bd9-6ea7-45e9-a332-acf3d81bbfae
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: bf6b699c7ff8830d1f74d14a077a4d0cb4e68116
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62723485"
---
# <a name="sql-command-prompt-utilities-database-engine"></a>Программы командной строки SQL (ядро СУБД)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Программы командной строки позволяют вносить в скрипт операции [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . В следующей таблице содержится список программ командной строки, поставляемых вместе с [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  

Сведения о *основной* SQL графического пользовательского интерфейса и средства командной строки, см. в разделе [Общие сведения о средствах SQL](overview-sql-tools.md).

  
|**Служебная программа**|**Описание**|**Установлена в**|  
|-----------------|---------------------|----------------------|  
|[Программа bcp](../tools/bcp-utility.md)|Используется для копирования данных между экземпляром [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и файлом данных в указанном пользователем формате.|\<*диск*:>\Program Files\\[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]\Client SDK\ODBC\110\Tools\Binn|  
|[dta Utility](../tools/dta/dta-utility.md)|Используется для анализа рабочей нагрузки и дает рекомендации по структурам физического проектирования, чтобы оптимизировать производительность сервера с этой рабочей нагрузкой.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Программа dtexec](../integration-services/packages/dtexec-utility.md)|Используется для настройки и выполнения пакета служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Версия этой программы с пользовательским интерфейсом называется **DTExecUI**. Она вызывает служебную программу для запуска пакетов.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]DTS\Binn|  
|[Программа dtutil](../integration-services/dtutil-utility.md)|Используется для управления пакетами служб SSIS.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]DTS\Binn|  
|[Развертывание решений моделей с использованием программы развертывания](../analysis-services/multidimensional-models/deploy-model-solutions-with-the-deployment-utility.md)|Используется для развертывания проектов служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] на экземплярах служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn\VShell\Common7\IDE|   
|[Программа osql](../tools/osql-utility.md)|Позволяет вводить инструкции [!INCLUDE[tsql](../includes/tsql-md.md)] , системные процедуры и файлы скрипта в командной строке.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Приложение SQL Profiler](../tools/profiler-utility.md)|Используется для запуска приложения среды [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] из командной строки.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Служебная программа RS.exe (SSRS)](../reporting-services/tools/rs-exe-utility-ssrs.md)|Используется для запуска скриптов, предназначенных для управления серверами отчетов служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Программа rsconfig (SSRS)](../reporting-services/tools/rsconfig-utility-ssrs.md)|Используется для настройки соединения сервера отчетов.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Программа rskeymgmt (SSRS)](../reporting-services/tools/rskeymgmt-utility-ssrs.md)|Используется для управления ключами шифрования на сервере отчетов.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Приложение sqlagent90](../tools/sqlagent90-application.md)|Используется для запуска агента [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] из командной строки.|\<диск>:\Program Files\Microsoft SQL Server\\<*имя_экземпляра*>\MSSQL\Binn|  
|[Программа sqlcmd](../tools/sqlcmd-utility.md)|Позволяет вводить инструкции [!INCLUDE[tsql](../includes/tsql-md.md)] , системные процедуры и файлы скрипта в командной строке.|\<*диск*:>\Program Files\\[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]\Client SDK\ODBC\110\Tools\Binn|  
|[Программа SQLdiag](../tools/sqldiag-utility.md)|Используется для сбора диагностических сведений для службы поддержки пользователей [!INCLUDE[msCoName](../includes/msconame-md.md)] .|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Приложение sqllogship](../tools/sqllogship-application.md)|Используется приложениями для выполнения операций резервирования, копирования и восстановления, а также связанных с ними задач очистки в конфигурации доставки журналов без запуска соответствующих заданий.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Программа SqlLocalDB](../tools/sqllocaldb-utility.md)|Режим выполнения [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , рассчитанный на разработчиков программ.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn\|  
|[Программа sqlmaint](../tools/sqlmaint-utility.md)|Служит для выполнения планов обслуживания баз данных, созданных в предыдущих версиях [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|\<диск>:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn|  
|[Программа sqlps](../tools/sqlps-utility.md)|Используется для выполнения команд и скриптов PowerShell. Загружает и регистрирует командлеты и поставщика PowerShell [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Приложение sqlservr](../tools/sqlservr-application.md)|Служит для запуска и остановки экземпляра компонента [!INCLUDE[ssDE](../includes/ssde-md.md)] из командной строки при устранении неполадок.|\<диск>:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn|  
|[Программа SSMS](../tools/sql-server-management-studio/ssms-utility.md)|Используется для запуска приложения среды [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] из командной строки.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn\VSShell\Common7\IDE|  
|[Программа tablediff](../tools/tablediff-utility.md)|Используется для сравнения данных в двух таблицах, чтобы обнаружить отсутствие конвергенции. Это полезно для устранения неполадок в топологии репликации.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]COM|  

## <a name="command-prompt-utilities-syntax-conventions"></a>Соглашения о синтаксисе программ командной строки  
  
|**Обозначение**|**Используется для**|  
|--------------------|------------------|  
|ВЕРХНИЙ РЕГИСТР|Инструкции и термины, используемые на уровне операционной системы.|  
|`monospace`|Образцы команд и программного кода.|  
|*курсив*|Параметры, указываемые пользователем.|  
|**полужирный**|Команды, параметры и другие элементы синтаксиса, которые должны в точности соответствовать примеру.|  
  
## <a name="see-also"></a>См. также:  
 [Агент распространения репликации](../relational-databases/replication/agents/replication-distribution-agent.md)   
 [Агент чтения журнала репликации](../relational-databases/replication/agents/replication-log-reader-agent.md)   
 [Агент слияния репликации](../relational-databases/replication/agents/replication-merge-agent.md)   
 [Агент чтения очереди репликации](../relational-databases/replication/agents/replication-queue-reader-agent.md)   
 [Агент моментальных снимков репликации](../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
  
