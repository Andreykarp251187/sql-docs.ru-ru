---
title: Настройка задания набора транзакций для издателя Oracle (Программирование репликации Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- sp_publisherproperty
- Oracle publishing [SQL Server replication], configuring
ms.assetid: beea1a5c-0053-4971-a68f-0da53063fcbb
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 48282f08df588f54b6f03a0b99c58a2f0cf039ac
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2019
ms.locfileid: "67793543"
---
# <a name="configure-the-transaction-set-job-for-an-oracle-publisher-replication-transact-sql-programming"></a>настроить задание набора транзакции для издателя Oracle (программирование репликации на языке Transact-SQL)
  **Xactset** – это задание базы данных Oracle, создаваемое репликацией, которая выполняется на издателе Oracle и создает наборы транзакций, когда агент чтения журнала не подключен к издателю. Включить и настроить это задание можно программным способом с распространителя с помощью хранимых процедур репликации. Дополнительные сведения см. в статье [Настройка производительности для издателей Oracle](../non-sql/performance-tuning-for-oracle-publishers.md).  
  
### <a name="to-enable-the-transaction-set-job"></a>Включение задания наборов транзакций  
  
1.  На издателе Oracle задайте достаточно большое значение параметра инициализации **job_queue_processes** , чтобы могло выполняться задание «Xactset». Дополнительные сведения об этом параметре см. в документации по базе данных для издателя Oracle.  
  
2.  На распространителе выполните хранимую процедуру [sp_publisherproperty (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql). Укажите имя издателя Oracle в параметре  **\@издателя**, значение `xactsetbatching` для  **\@propertyname**и значение `enabled` для  **\@propertyvalue**.  
  
3.  На распространителе выполните хранимую процедуру [sp_publisherproperty (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql). Укажите имя издателя Oracle в параметре  **\@издателя**, значение `xactsetjobinterval` для  **\@propertyname**и интервал запуска задания в минутах для  **\@propertyvalue**.  
  
4.  На распространителе выполните хранимую процедуру [sp_publisherproperty (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql). Укажите имя издателя Oracle в параметре  **\@издателя**, значение `xactsetjob` для  **\@propertyname**и значение `enabled` для  **\@propertyvalue**.  
  
### <a name="to-configure-the-transaction-set-job"></a>Настройка задания набора транзакций  
  
1.  На распространителе выполните хранимую процедуру [sp_publisherproperty (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql) (необязательно). Укажите имя издателя Oracle в параметре  **\@издателя**. Система выдаст свойства задания **Xactset** на издателе.  
  
2.  На распространителе выполните хранимую процедуру [sp_publisherproperty (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql). Укажите имя издателя Oracle в параметре  **\@издателя**, имя, устанавливаемое для свойства транзакций  **\@propertyname**и новое значение  **\@propertyvalue**.  
  
3.  Повторите шаг 2 для каждого устанавливаемого свойства задания набора транзакций (необязательно). При изменении `xactsetjobinterval` необходимо перезапустить задание на издателе Oracle для нового интервала вступили в силу.  
  
### <a name="to-view-properties-of-the-transaction-set-job"></a>Просмотр свойств задания набора транзакций  
  
1.  На распространителе выполните процедуру [sp_helpxactsetjob](/sql/relational-databases/system-stored-procedures/sp-helpxactsetjob-transact-sql). Укажите имя издателя Oracle в параметре  **\@издателя**.  
  
### <a name="to-disable-the-transaction-set-job"></a>Отключение задания набора транзакций  
  
1.  На распространителе выполните хранимую процедуру [sp_publisherproperty (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql). Укажите имя издателя Oracle в параметре  **\@издателя**, значение `xactsetjob` для  **\@propertyname**и значение `disabled` для  **\@propertyvalue**.  
  
## <a name="example"></a>Пример  
 В следующем примере включается задание `Xactset` и устанавливается интервал запуска, равный трем минутам.  
  
 [!code-sql[HowTo#sp_enable_xactsetjob](../../../snippets/tsql/SQL15/replication/howto/tsql/enablexactsetjob.sql#sp_enable_xactsetjob)]  
  
## <a name="see-also"></a>См. также  
 [Настройка производительности для издателей Oracle](../non-sql/performance-tuning-for-oracle-publishers.md)   
 [Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md)  
  
  
