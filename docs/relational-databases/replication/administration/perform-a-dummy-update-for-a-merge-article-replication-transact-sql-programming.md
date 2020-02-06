---
title: Фиктивное обновление статьи слияния (хранимая процедура репликации)
description: Используйте хранимые процедуры репликации Transact-SQL для выполнения фиктивного обновления статьи слияния, используемой в репликации слиянием.
ms.custom: seo-lt-2019
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- sp_mergedummyupdate
- dummy updates [SQL Server replication]
ms.assetid: 2f339210-4d85-4843-bd94-e86f7100d3ef
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 05c3a91d647819126261f0637e0de24d0ce3e4fd
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "75322041"
---
# <a name="perform-a-dummy-update-for-a-merge-article-replication-transact-sql-programming"></a>выполнить фиктивное обновление для статьи репликации слиянием (программирование репликации на языке Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Триггеры являются частью процесса репликации слиянием. При обновлении опубликованной таблицы, срабатывают триггеры Update. В некоторых случаях данные могут обновляться без срабатывания триггеров, например, при выполнении операций WRITETEXT и UPDATETEXT. В таких случаях для репликации изменения необходимо явно добавить фиктивную инструкцию UPDATE. Это можно сделать с помощью хранимых процедур репликации.  
  
### <a name="to-add-a-dummy-update-statement"></a>Добавление фиктивной инструкции UPDATE  
  
1.  Выполните операцию (например UPDATETEXT) для строки таблицы, опубликованной в репликации слияния, требующую фиктивного обновления.  
  
2.  На сервере (издателя или подписчика) в той базе данных, где было сделано изменение, выполните процедуру [sp_mergedummyupdate &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-mergedummyupdate-transact-sql.md). Укажите в параметре `@source_object` таблицу, в которой было сделано изменение, а в параметре `@rowguid` — уникальный идентификатор измененной строки.  
  
3.  Синхронизируйте подписку для репликации измененной строки.  
  
  
