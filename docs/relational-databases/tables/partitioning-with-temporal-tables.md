---
title: Секционирование с помощью темпоральных таблиц | Документация Майкрософт
ms.custom: ''
ms.date: 04/26/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
ms.assetid: 313714b8-4ad1-4c14-93a3-7f628a334a51
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3d75e7f889ff7e1042643c5990a9b2313303d1b8
ms.sourcegitcommit: f018eb3caedabfcde553f9a5fc9c3e381c563f1a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2019
ms.locfileid: "74165687"
---
# <a name="partitioning-with-temporal-tables"></a>Секционирование с помощью темпоральных таблиц

[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Секционирование в текущей и прежней таблицах можно использовать независимо друг от друга. Но с помощью секционирования нельзя изменить содержание данных без системного управления версиями.

> [!NOTE]
> До выхода SQL Server 2016 с пакетом обновления 1 (SP1) функция секционирования была доступна только в выпусках Enterprise Edition. В SQL Server 2016 с пакетом обновления 1 (SP1) и более поздних версиях секционирование поддерживается во всех выпусках.

- **Для текущей таблицы:**

  - **SWITCH IN** в текущую таблицу позволяет упростить загрузку данных и выполнение запросов, если **SYSTEM_VERSIONING** имеет значение **ON**
  - **SWITCH OUT** использовать нельзя, если **SYSTEM_VERSIONING** имеет значение **ON**

- **Для прежней таблицы:**

  - **SWITCH OUT** из прежней таблицы можно выполнить для очистки ненужной части данных, если **SYSTEM_VERSIONING** имеет значение **ON** .
  - **SWITCH IN** нельзя использовать, если **SYSTEM_VERSIONING** имеет значение **ON** , так как это может нарушить согласованность темпоральных данных.

## <a name="next-steps"></a>Дальнейшие действия

- [Темпоральные таблицы](../../relational-databases/tables/temporal-tables.md)
- [Приступая к работе c темпоральными таблицами с системным управлением версиями](../../relational-databases/tables/getting-started-with-system-versioned-temporal-tables.md)
- [Проверка согласованности системной темпоральной таблицы](../../relational-databases/tables/temporal-table-system-consistency-checks.md)
- [Рекомендации и ограничения для темпоральной таблицы](../../relational-databases/tables/temporal-table-considerations-and-limitations.md)
- [Безопасность темпоральной таблицы](../../relational-databases/tables/temporal-table-security.md)
- [Управление хранением данных журнала в темпоральных таблицах с системным управлением версиями](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)
- [Темпоральные таблицы с системным управлением версиями и таблицы, оптимизированные для памяти](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)
- [Представления и функции метаданных для временной таблицы](../../relational-databases/tables/temporal-table-metadata-views-and-functions.md)
