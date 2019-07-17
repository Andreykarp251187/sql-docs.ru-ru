---
title: Переименование столбцов (ядро СУБД) | Документация Майкрософт
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], names
- renaming columns
- column names [SQL Server]
ms.assetid: 7c71ec9f-0180-4398-b32a-4bfb7592e75d
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 36b7c385f3722a1db86899c749ee8310e7596e1e
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727783"
---
# <a name="rename-columns-database-engine"></a>Переименование столбцов (компонент Database Engine)

[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Столбец таблицы в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] можно переименовать, используя [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].

**В этом разделе**

- **Перед началом работы**

   [Ограничения](#Restrictions)

   [безопасность](#Security)

- **Переименование столбцов с помощью:**

   [Среда SQL Server Management Studio](#SSMSProcedure)

   [Transact-SQL](#TsqlProcedure)

## <a name="BeforeYouBegin"></a> Перед началом

### <a name="Restrictions"></a> Ограничения

Переименование столбца таблицы не приводит к автоматическому переименованию ссылок на этот столбец. Необходимо вручную изменить все объекты, которые ссылаются на переименованный столбец. Например, если переименован столбец таблицы и на этот столбец имеется ссылка в триггере, то необходимо изменить триггер, указав новое имя столбца. Используйте [sys.sql_expression_dependencies](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md) , чтобы составить список зависимостей для объекта перед его переименованием.

### <a name="Security"></a> безопасность

#### <a name="Permissions"></a> Permissions

Необходимо разрешение ALTER на объект.

## <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio

### <a name="to-rename-a-column-using-object-explorer"></a>Переименование столбца в обозревателе объектов

1. В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].
2. В **обозревателе объектов**щелкните правой кнопкой мыши таблицу, в которой нужно переименовать столбцы, и выберите пункт **Переименовать**.
3. Введите новое имя столбца.

### <a name="to-rename-a-column-using-table-designer"></a>Переименование столбца в конструкторе таблиц

1. В **обозревателе объектов**щелкните правой кнопкой мыши таблицу, в которой нужно переименовать столбцы, и выберите пункт **Конструирование**.
2. В разделе **Имя столбца**выберите имя, которое нужно изменить, и введите новое.
3. В меню **Файл** выберите пункт **Сохранить** _имя_таблицы_.

> [!NOTE]
> Имя столбца можно также изменить на вкладке **Свойства столбца** . Выберите столбец, имя которого нужно изменить, и введите новое значение в поле **Имя**.

## <a name="TsqlProcedure"></a> Использование Transact-SQL

**Переименование столбца**

### <a name="to-rename-a-column"></a>Переименование столбца

В следующем примере выполняется переименование столбца `TerritoryID` в таблице `Sales.SalesTerritory` базы данных AdventureWorks на столбец `TerrID`.

```sql
EXEC sp_rename 'Sales.SalesTerritory.TerritoryID', 'TerrID', 'COLUMN';
```

Дополнительные сведения см. в разделе [sp_rename (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md).
