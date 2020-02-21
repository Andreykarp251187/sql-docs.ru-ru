---
title: Данные для мобильных отчетов служб Reporting Services | Документы Майкрософт
ms.date: 02/08/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: mobile-reports
ms.topic: conceptual
ms.assetid: 91138ef8-ddb4-4ac5-a1e4-fa4cf1c58dcc
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: b6131f6bce9cb6d1c87a4a75215a906b6d097c7d
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "63129743"
---
# <a name="data-for-reporting-services-mobile-reports"></a>Data for Reporting Services mobile reports
Модель данных для [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-long.md)] очень простая. Данные импортируются в [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)] как коллекция наборов данных. Формальные отношения между наборами данных не требуются. Уточняющие запросы от одного набора к другому выполняются, если значения их ключей соответствуют. Агрегаты даты и времени обрабатываются в среде выполнения мобильных отчетов. Они совпадают для разных наборов данных, даже если степень детализации данных даты и времени в этих наборах отличается.   
  
Данные можно импортировать из двух источников:   
  
* **Локальные файлы Excel**. Выберите документ Excel и укажите, какие листы необходимо импортировать. После импорта эти данные сохраняются в определении мобильного отчета. Чтобы обновить данные из исходного файла Excel, используйте команду **Обновить данные** в правом верхнем углу вкладки **Данные** в [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)]. См. дополнительные сведения о [подготовке данных Excel для мобильных отчетов SSRS](../../reporting-services/mobile-reports/prepare-excel-data-for-reporting-services-mobile-reports.md).  
  
* **Общие наборы данных издателя мобильных отчетов для SQL Server**. Просмотрите список опубликованных наборов данных на сервере и выберите те, которые нужно добавить в мобильный отчет. Мобильные отчеты на основе данных сервера всегда остаются связанными с исходными наборами данных сервера и отражают последнее состояние данных на сервере. См. [список поддерживаемых источников данных](../report-data/data-sources-supported-by-reporting-services-ssrs.md).   
  
  См. дополнительные сведения о [получении данных из общих наборов в издателе мобильных отчетов](../../reporting-services/mobile-reports/get-data-from-shared-datasets-in-reporting-services-mobile-reports.md).  
  
После импорта данных в [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)]процедура создания и проектирования мобильных отчетов одинакова при любом источнике данных.   
  
## <a name="connect-mobile-report-elements-to-data"></a>Подключение элементов мобильного отчета к данным ##  
  
Каждый элемент издателя мобильных отчетов для SQL Server содержит один параметр данных или несколько. Например, элемент радиального датчика содержит два параметра данных: основное значение и значение для сравнения. Каждый из этих параметров указывает только на одно поле (столбец) в конкретном представлении данных.   
  
Среда выполнения мобильных отчетов предоставляет совокупные значения датчика на основе выбора пользователя. Обратите внимание, что значение для сравнения одного и того же экземпляра радиального датчика может быть привязано к полю в другом представлении данных.   
  
### <a name="see-also"></a>См. также раздел  
-  [Подготовка данных для мобильных отчетов Reporting Services](../../reporting-services/mobile-reports/prepare-data-for-reporting-services-mobile-reports.md)
- [Создание и публикация мобильных отчетов с помощью издателя мобильных отчетов SQL Server](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)  
- [Получение данных из общих наборов данных](../../reporting-services/mobile-reports/get-data-from-shared-datasets-in-reporting-services-mobile-reports.md)
- [Сохранение форматирования дат для данных служб Analysis Services в мобильных отчетах](../../reporting-services/mobile-reports/retain-date-formatting-for-analysis-services-in-mobile-reports.md) 
  
  

