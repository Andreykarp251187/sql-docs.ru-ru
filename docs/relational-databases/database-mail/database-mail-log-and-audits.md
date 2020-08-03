---
title: Ведение журнала и аудит компонента Database Mail | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- auditing [SQL Server]
- Database Mail [SQL Server], auditing
- logs [Database Mail]
- audits [SQL Server], Database Mail
- Database Mail [SQL Server], logging
ms.assetid: 846589ee-5fe5-4ab3-b335-0c253e569f99
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4354def42884887539693073bf3108d7227170de
ms.sourcegitcommit: 99f61724de5edf6640efd99916d464172eb23f92
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87363574"
---
# <a name="database-mail-log-and-audits"></a>Ведение журнала и аудит компонента Database Mail
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
  Регистрация в Database Mail спроектирована таким образом, чтобы обеспечить способ локализации и исправления неполадок. Компонент Database Mail хранит сведения о регистрации в базе данных **msdb** . Сведения о содержимом сообщений электронной почты Database Mail, их состояниях, а также о любых полученных сообщениях, например сообщениях об ошибках, регистрируются в Database Mail и могут использоваться для аудита или обеспечения безопасности.  
  
## <a name="database-mail-logs"></a>Журналы компонента Database Mail  
 Таблицы в базе данных **msdb** записывают журнал из [Database Mail External Program](../../relational-databases/database-mail/database-mail-external-program.md). [Представления компонента Database Mail (Transact-SQL)](../../relational-databases/system-catalog-views/database-mail-views-transact-sql.md) позволяют устранять неполадки в таблицах. В представлении [sysmail_event_log (Transact-SQL)](../../relational-databases/system-catalog-views/sysmail-event-log-transact-sql.md) отображаются ошибки, если компонент Service Broker не может запустить внешнюю программу, если в этой внешней программе возникли ошибки при работе с сетью или сервер SMTP отказался принять сообщение электронной почты. В случае события, которое внешняя программа не может записать в таблицы **msdb** , она записывает ошибки в журнал событий приложений Windows.  
  
 Внутренние таблицы в базе данных **msdb** содержат электронные сообщения и вложения, присланные компонентом Database Mail, а также текущее состояние каждого сообщения. Компонент Database Mail обновляет эти таблицы при каждом обработанном сообщении.  
  
## <a name="database-mail-auditing-tasks"></a>Задачи аудита компонента Database Mail  
  
|Обзор журналов компонента Database Mail и управление ими|Ссылка на раздел|  
|-|-|  
|Проверьте состояние доставки отдельного сообщения|[Проверка состояния сообщений электронной почты, отправленных с помощью компонента Database Mail](../../relational-databases/database-mail/check-the-status-of-e-mail-messages-sent-with-database-mail.md)|  
|Очистите сообщения, вложения и записи журнала компонента Database Mail|[sysmail_delete_mailitems_sp (Transact-SQL)](../../relational-databases/system-stored-procedures/sysmail-delete-mailitems-sp-transact-sql.md)<br /><br /> [sysmail_delete_log_sp (Transact-SQL)](../../relational-databases/system-stored-procedures/sysmail-delete-log-sp-transact-sql.md)|  
|Заархивируйте сообщения и журналы компонента Database Mail|[Создание задания агента SQL Server по архивации сообщений и журналов событий компонента Database Mail](../../relational-databases/database-mail/create-a-sql-server-agent-job-to-archive-database-mail-messages-and-event-logs.md)|  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение за использованием ресурсов (системный монитор)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
