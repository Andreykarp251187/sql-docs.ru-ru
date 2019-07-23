---
title: Пример считывания данных большого объема с помощью хранимых процедур | Документы Майкрософт
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 58c76635-a117-4661-8781-d6cb231c5809
author: MightyPen
ms.author: genemi
ms.openlocfilehash: cbf339845bd23f1beb4f5cd0f3b3a380689a3120
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67956120"
---
# <a name="reading-large-data-with-stored-procedures-sample"></a>Образец считывания данных большого объема с помощью хранимых процедур

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

В этом примере приложения, использующего драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], показано получение большого параметра OUT из хранимой процедуры.

Файл кода для этого образца имеет имя ExecuteStoredProcedure.java и находится в следующей папке:

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples\adaptive
```

## <a name="requirements"></a>Требования

Для запуска этого образца приложения также потребуется доступ к образцу базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]. Необходимо также включить в параметр classpath путь к файлу mssql-jdbc.jar. Дополнительные сведения о настройке подкаталогов классов см. в разделе [Использование драйвера JDBC](../../connect/jdbc/using-the-jdbc-driver.md).

> [!NOTE]  
> Драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] включает файлы библиотек классов mssql-jdbc, которые используются в зависимости от выбранных параметров среды выполнения Java (JRE). Для получения дополнительных сведений о том, какой JAR-файл выбрать, см. статью [Требования к системе для драйвера JDBC](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).

В примере создается необходимая хранимая процедура в [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] образце базы данных:

## <a name="example"></a>Пример

В следующем примере образец кода будет использоваться для соединения с базой данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]. Затем образец кода создает образцы данных и обновляет таблицу Production.Document с помощью параметризированного запроса. Затем в образце кода включается режим адаптивной буферизации с помощью метода [getResponseBuffering](../../connect/jdbc/reference/getresponsebuffering-method-sqlserverstatement.md) класса [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) и выполняется хранимая процедура GetLargeDataValue. Начиная с версии драйвера JDBC 2.0 свойство соединения responseBuffering по умолчанию имеет значение "adaptive".

Наконец, в образце кода выводятся возвращенные данные с параметрами OUT и демонстрируется использование методов `mark` и `reset` в потоке для повторного считывания любого фрагмента данных.

[!code[JDBC#UsingAdaptiveBuffering2](../../connect/jdbc/codesnippet/Java/reading-large-data-with-_1_1.java)]

## <a name="see-also"></a>См. также:

[Работа с большими объемами данных](../../connect/jdbc/working-with-large-data.md)
