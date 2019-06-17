---
title: sys.dm_server_services (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 01/07/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_server_services
- sys.dm_server_services
- sys.dm_server_services_TSQL
- dm_server_services_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_server_services dynamic management view
ms.assetid: 3f0defd0-478d-4e7f-96be-8795c9de4e3f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8acb2fae0aa0edadf1995a0a103ff60b66a912a9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62686223"
---
# <a name="sysdmserverservices-transact-sql"></a>sys.dm_server_services (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о службах SQL Server, полнотекстового поиска и агента SQL Server в текущем экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Это динамическое административное представление позволяет получить сведения о состоянии данных служб.  
  
 
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|servicename|**nvarchar(256)**|Имя [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], полнотекстового поиска, или служба агента SQL Server. Не может иметь значение null.|  
|startup_type|**int**|Показывает режим запуска службы. Ниже приведены возможные значения и их соответствующие описания.<br /><br /> 0: Другое<br />1: Другое<br />2: Автоматически<br />3: Вручную<br />4: Выключено<br /><br /> Допускает значение NULL.|  
|startup_desc|**nvarchar(256)**|Описывает режим запуска службы. Ниже приведены возможные значения и их соответствующие описания.<br /><br /> Другие: Другой (при загрузке)<br />Другие: Другой (при запуске системы)<br />Автоматически: Автозапуск<br />Вручную: Запуск по требованию<br />Отключено: Выключено<br /><br /> Не может иметь значение null.|  
|status|**int**|Показывает текущее состояние службы. Ниже приведены возможные значения и их соответствующие описания.<br /><br /> 1: Остановлена<br />2: Другое (ожидает запуска)<br />3: Другое (ждет остановки)<br />4: Запущен<br />5: Другие (ждет продолжения)<br />6: Другое (ждет приостановки)<br />7: Пауза<br /><br /> Допускает значение NULL.|  
|status_desc|**nvarchar(256)**|Описывает текущее состояние службы. Ниже приведены возможные значения и их соответствующие описания.<br /><br /> Остановлено: Служба остановлена.<br />Другое (отложенный запуск): Служба находится в процессе запуска.<br />Другое (отложенная остановка): Служба находится в процессе остановки.<br />Под управлением: Служба выполняется.<br />Другие (отложенное возобновление): Служба находится в состоянии ожидания.<br />Другое (ждет приостановки): Служба находится в процессе приостановки.<br />Приостановлено: Служба приостановлена.<br /><br /> Не может иметь значение null.|  
|process_id|**int**|Идентификатор процесса службы. Не может иметь значение null.|  
|last_startup_time|**datetimeoffset(7)**|Дата и время последнего запуска службы. Допускает значение NULL.|  
|service_account|**nvarchar(256)**|Учетная запись, имеющая право управлять этой службой. Данная учетная запись может запускать и останавливать службу или изменять ее свойства. Не может иметь значение null.|  
|filename|**nvarchar(256)**|Полный путь и имя исполняемого файла службы. Не может иметь значение null.|  
|is_clustered|**nvarchar(1)**|Указывает, установлена ли служба в качестве ресурса кластеризованного сервера. Не может иметь значение null.|  
|cluster_nodename|**nvarchar(256)**|Имя узла кластера, на котором установлена служба. Допускает значение NULL.|
|instant_file_initialization_enabled|**nvarchar(1)**|Указывает, включена ли Мгновенная инициализация файлов для [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] службы.<br /><br />Y = Мгновенная инициализация файлов включено для службы.<br /><br />N = Мгновенная инициализация файлов отключена для службы.<br /><br /> Допускает значение NULL.<br /><br /> **Примечание.** Не применяется к другим службам, например агент SQL Server.<br /><br /> **Применимо к:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (Начиная с [!INCLUDE[sssql11](../../includes/sssql11-md.md)] SP4, и [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]).|  

## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Разрешения  
 Необходимо разрешение `VIEW SERVER STATE` на сервере.  
  
## <a name="see-also"></a>См. также  
 [sys.dm_server_registry &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-registry-transact-sql.md)  
  
