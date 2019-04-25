---
title: Использовать T-SQL (CREATE EXTERNAL LIBRARY), чтобы установить пакеты R - служб машинного обучения SQL Server
description: Добавление новых пакетов R в SQL Server 2016 R Services или служб SQL Server 2017 машинного обучения (в базе данных).
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/30/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: b59f15ace1dc96af537486336e76a209f1c85da7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62507036"
---
# <a name="use-t-sql-create-external-library-to-install-r-packages-on-sql-server"></a>Использование T-SQL (CREATE EXTERNAL LIBRARY) для установки пакетов R на SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье описывается установка новых пакетов R в экземпляре SQL Server, где включена машинного обучения. Существует несколько подходов для выбора. С помощью T-SQL лучше всего подходит для администраторов сервера, кто не знаком с R.

**Область применения:**  [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

[CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) инструкция делает возможным добавление пакета или набора пакетов экземпляра или определенной базы данных без выполнения R или Python code напрямую. Тем не менее этот метод требует подготовки пакета и разрешения дополнительные базы данных.

+ Все пакеты должен быть доступен в виде локального ZIP-файла, а не Скачанный по запросу из Интернета.

+ Все зависимости необходимо определить по имени и версии и включены в ZIP-файл. Инструкция завершается неудачно, если необходимые пакеты недоступны, включая зависимости пакетов подчиненных. 

+ Будьте **db_owner** или иметь разрешение CREATE EXTERNAL LIBRARY в роли базы данных. Дополнительные сведения см. в разделе [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql).

## <a name="download-packages-in-archive-format"></a>Скачивание пакетов в формат архива

При установке одного пакета, скачайте пакет в формате ZIP.

Очень часто Установка нескольких пакетов из-за зависимости пакетов. Если пакет требует других пакетов, необходимо убедиться, что все они доступны друг к другу во время установки. Мы рекомендуем [Создание локального репозитория](create-a-local-package-repository-using-minicran.md) с помощью [miniCRAN](https://andrie.github.io/miniCRAN/) сборка полный набор пакетов, а также [igraph](https://igraph.org/r/) для анализа зависимостей пакетов. Неправильная версия пакета установки, или пропуск зависимость пакета может вызвать инструкцию CREATE EXTERNAL LIBRARY, переход на другой. 

## <a name="copy-the-file-to-a-local-folder"></a>Скопируйте файл в локальную папку

Скопируйте ZIP-файл, содержащий все пакеты в локальную папку на сервере. Если у вас нет доступа к файловой системе на сервере, можно также передать полный пакет как переменную, с использованием двоичного формата. Дополнительные сведения см. в разделе [CREATE EXTERNAL LIBRARY](../../t-sql/statements/create-external-library-transact-sql.md).

## <a name="run-the-statement-to-upload-packages"></a>Выполните инструкцию, чтобы отправить пакеты

Откройте **запроса** окно, используя учетную запись с правами администратора.

Выполните инструкцию T-SQL `CREATE EXTERNAL LIBRARY` для передачи коллекции ZIP-пакета в базе данных.

Например, следующая инструкция имена как источник типа, содержащее репозитория miniCRAN **randomForest** пакет, вместе с зависимостями. 

```sql
CREATE EXTERNAL LIBRARY randomForest
FROM (CONTENT = 'C:\Temp\Rpackages\randomForest_4.6-12.zip')
WITH (LANGUAGE = 'R');
```

Нельзя использовать произвольное имя; Внешняя библиотека имя должно иметь имя, которое вы будете использовать при загрузке или вызова пакета.

## <a name="verify-package-installation"></a>Проверка установки пакета

Если библиотека создана успешно, при запуске пакета в SQL Server, путем ее вызова внутри хранимой процедуры.
    
```sql
EXEC sp_execute_external_script
@language =N'R',
@script=N'library(randomForest)'
```

## <a name="see-also"></a>См. также

+ [Получение сведений о пакете](determine-which-packages-are-installed-on-sql-server.md)
+ [Учебники по R](../tutorials/sql-server-r-tutorials.md)
+ [Практические руководства](sql-server-machine-learning-tasks.md)