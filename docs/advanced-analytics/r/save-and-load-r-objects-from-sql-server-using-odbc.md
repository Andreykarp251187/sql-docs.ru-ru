---
title: Сохранение и загрузка объектов R из SQL Server с помощью ODBC
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: e3d7891098727c066b05bbd9f2f23c41bbdcca59
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2019
ms.locfileid: "68714986"
---
# <a name="save-and-load-r-objects-from-sql-server-using-odbc"></a>Сохранение и загрузка объектов R из SQL Server с помощью ODBC
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Службы R Services SQL Server могут хранить сериализованные объекты R в таблице и затем загружать их оттуда по мере необходимости, при этом им не требуется перезапускать код R или переобучать модель. Такая возможность сохранения объектов R в базе данных крайне важна для таких сценариев, как обучение и сохранение модели, а также последующее ее использование для оценки или анализа.

Для повышения производительности этого критического этапа пакет **RevoScaleR** теперь содержит новые функции сериализации и десериализации, призванные значительно повысить производительность и обеспечить более компактное хранение объектов. В этой статье описываются эти функции и способы их использования.

## <a name="overview"></a>Обзор

Теперь пакет **RevoScaleR** включает новые функции, которые упрощают сохранение объектов R в SQL Server и последующее их считывание из таблицы SQL Server. В общем случае каждый вызов функции использует простое хранилище значений ключей, в котором ключ является именем объекта, а значение, связанное с ключом, — это объект varbinary R, который должен быть перемещен в таблицу или из нее.

Чтобы сохранить объекты R для SQL Server непосредственно из среды R, необходимо выполнить следующие действия.

+ установлено подключение к SQL Server с помощью источника данных *RxOdbcData* .
+ Вызов новых функций через подключение ODBC
+ При необходимости можно указать, что объект не должен быть сериализован. Затем выберите новый алгоритм сжатия, который будет использоваться вместо алгоритма сжатия по умолчанию.

По умолчанию любой объект, вызываемый из R для перемещения в SQL Server, сериализуется и сжимается. И наоборот, при загрузке объекта из таблицы SQL Server для использования в коде R объект десериализуется и распаковывается.

## <a name="list-of-new-functions"></a>Список новых функций

- `rxWriteObject` записывает объект R в SQL Server с помощью источника данных ODBC.

- `rxReadObject` считывает объект R из базы данных SQL Server с помощью источника данных ODBC.

- `rxDeleteObject` удаляет объект R из базы данных SQL Server, указанной в источнике данных ODBC. Если существует несколько объектов, на которые указывает сочетание ключа и версии, все они удаляются.

- `rxListKeys` указывает все доступные объекты в виде пар "ключ — значение". Это помогает определить имена и версии объектов R.

Для получения подробных сведений о синтаксисе каждой функции воспользуйтесь справкой R. Сведения также доступны в справочнике [по масштабируемости](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler).

## <a name="how-to-store-r-objects-in-sql-server-using-odbc"></a>Сохранение объектов R в SQL Server с помощью ODBC

Эта процедура демонстрирует, как использовать новые функции для создания модели и ее сохранения в SQL Server.

1. Настройте строку подключения для SQL Server.
   ```R
   conStr <- 'Driver={SQL Server};Server=localhost;Database=storedb;Trusted_Connection=true'
   ```
2. Создайте объект источника данных *rxOdbcData* в R с помощью этой строки подключения.
   ```R
   ds <- RxOdbcData(table="robjects", connectionString=conStr)
   ```

3. Удалите таблицу, если она уже существует и не требуется отслеживать старые версии объектов.

   ```R
   if(rxSqlServerTableExists(ds@table, ds@connectionString)) {
       rxSqlServerDropTable(ds@table, ds@connectionString)
       }
   ```
   
4. Определите таблицу, которую можно использовать для хранения двоичных объектов.

   ```R
   ddl <- paste(" CREATE TABLE [", ds@table, "] 
      (","  [id] varchar(200) NOT NULL,
       "," [value] varbinary(max),
       "," CONSTRAINT unique_id UNIQUE (id))", 
       sep = "") 
   ```
5. Откройте подключение ODBC, чтобы создать таблицу, а после завершения инструкции DDL закройте его.

   ```R
    rxOpen(ds, "w") 
    rxExecuteSQLDDL(ds, ddl) 
    rxClose(ds)
    ```
6. Создайте объекты R, которые вы хотите сохранить.

   ```R
   infertLogit <- rxLogit(case ~ age + parity + education + spontaneous + induced, 
     data = infert)
   ```
6. Используйте созданный ранее объект *RxOdbcData* , чтобы сохранить модель в базе данных.

   ```R
   rxWriteObject(ds, "logit.model", infertLogit)
   ```

## <a name="how-to-read-r-objects-from-sql-server-using-odbc"></a>Считывание объектов R из SQL Server с помощью ODBC

Эта процедура демонстрирует, как использовать новые функции для загрузки модели из SQL Server.

1. Настройте строку подключения для SQL Server.

   ```R
   conStr2 <- 'Driver={SQL Server};Server=localhost;Database=storedb;Trusted_Connection=true'
   ```
2. Создайте объект источника данных *rxOdbcData* в R с помощью этой строки подключения.

   ```R
   ds <- RxOdbcData(table="robjects", connectionString=conStr2)
   ```
3. Считайте модель из таблицы, указав имя ее объекта R.

   ```R
    infertLogit2 <- rxReadObject(ds, "logit.model")
   ```
