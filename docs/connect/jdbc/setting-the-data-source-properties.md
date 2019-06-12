---
title: Установка данных свойства источника | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: f3363d05-07fc-4bf8-ae5e-2a7a968808ad
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 6804e8bb0f68ed88934e5bc86d61556b9bbbd499
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66778067"
---
# <a name="setting-the-data-source-properties"></a>Задание свойств источника данных

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Источники данных являются предпочтительным механизмом, с помощью которого создаются соединения JDBC на платформе Java в среде Enterprise Edition (Java EE). Источники данных предоставляют соединения, пулы соединений, распределенные соединения, и для этого не нужно использовать жестко запрограммированные свойства соединения на коде Java. Все источники данных [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] могут устанавливать или принимать значения всех свойств с помощью соответствующих методов задания и получения значений.

Продукты Java EE, например серверы приложений и обработчики сервлетов/JSP, как правило, позволяют настроить источники данных для доступа к базе данных. Все свойства, перечисленные в разделе [Задание свойств соединения](../../connect/jdbc/setting-the-connection-properties.md), могут быть заданы там, где конфигурация позволяет вводить свойства в виде пар "свойство=значение".

Дополнительные сведения об источниках данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в описании класса [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md). Пример использования класса SQLServerDataSource для установки подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных, см. в разделе [образец источника данных](../../connect/jdbc/data-source-sample.md).

## <a name="see-also"></a>См. также:

[Соединение с SQL Server с помощью драйвера JDBC](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)
