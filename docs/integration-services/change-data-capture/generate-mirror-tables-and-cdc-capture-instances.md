---
title: Создание экземпляров зеркальных таблиц и отслеживание CDC | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- mirTab
ms.assetid: 260c1617-eecc-4007-a84d-3c5778ce46b6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f5b462a03b15042c6fbb801b121bb04a07b7966b
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86921607"
---
# <a name="generate-mirror-tables-and-cdc-capture-instances"></a>Создание экземпляров зеркальных таблиц и отслеживание CDC

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Страница формирования зеркальных таблиц используется для создания зеркальных таблиц для таблиц, включенных в экземпляр CDC.  
  
 Нажмите кнопку **Выполнить** , чтобы создать зеркальные таблицы. Процесс создания каждой таблицы отображается на экране, а по его окончании выдается сообщение, в котором говорится, была ли таблица создана успешно. Если возникли ошибки, нажмите кнопку **Сведения** , чтобы открыть диалоговое окно с описанием ошибки.  
  
 Если какую-либо таблицу создать не удалось, то можно либо продолжить выполнение, либо удалить таблицу, которую не удалось создать, а затем продолжить работу. После завершения работы мастера можно решить, следует ли исправить таблицу в базе данных-источнике Oracle или не использовать ее в экземпляре CDC. Если выбрано исправление таблицы, то ее можно будет добавить через [Edit Tables](../../integration-services/change-data-capture/edit-tables.md).  
  
 Нажмите кнопку **Далее** , чтобы открыть страницу [Finish](../../integration-services/change-data-capture/finish.md) .  
  
## <a name="see-also"></a>См. также:  
 [Как создать экземпляр базы данных изменений SQL Server](../../integration-services/change-data-capture/how-to-create-the-sql-server-change-database-instance.md)  
  
  
