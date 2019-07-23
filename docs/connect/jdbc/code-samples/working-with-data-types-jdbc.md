---
title: Работа с типами данных (JDBC) | Документация Майкрософт
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b39f44d0-3710-4bc6-880c-35bd8c10a734
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f49cdf12c4aaca9633670f7688783407acb05342
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67957046"
---
# <a name="working-with-data-types-jdbc"></a>Работа с типами данных (JDBC)

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

Основная функция [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] — предоставить разработчикам на Java доступ к данным в базах [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. С этой целью драйвер JDBC контролирует преобразование между типами данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и типами и объектами языка Java.  
  
> [!NOTE]  
> Подробные сведения о типах данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и драйвера JDBC, в том числе об их отличиях и о преобразовании в типы данных языка Java, см. в статье [Основные сведения о типах данных драйвера JDBC](../../../connect/jdbc/understanding-the-jdbc-driver-data-types.md).  
  
Для совместимости с типами данных SQL Server драйвер JDBC предоставляет методы get\<Type> и set\<Type> для классов [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) и [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md), а также методы get\<Type> и update\<Type> для класса [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md). Применяемый метод зависит от типа обрабатываемых данных, а также от использования либо результирующих наборов, либо запросов.  
  
В этом разделе описано использование типов данных драйвера JDBC для доступа к данным [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в приложениях Java.  
  
## <a name="in-this-section"></a>в этом разделе  
  
| Раздел                                                                         | Описание                                                                                                                                                                                                                                                  |
| ----------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [Пример базовых типов данных](../../../connect/jdbc/code-samples/basic-data-types-sample.md)   | Описывает использование методов получения результирующих наборов для извлечения значений с базовыми типами данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], а также применение методов обновления результирующего набора для изменения этих значений.                                             |
| [Пример типа данных SQLXML](../../../connect/jdbc/code-samples/sqlxml-data-type-sample.md)   | Описывает сохранение данных XML в реляционной базе данных, их извлечение из базы и выполнение их анализа с помощью типа данных Java **SQLXML**.                                                                                   |
| [Пример пространственных типов данных](../../../connect/jdbc/code-samples/spatial-data-types-sample.md) | Описывает хранение пространственных типов данных в SQL Server и получение этих типов обратно из SQL Server. Также обсуждается использование только что определенных классов **Geometry** и **Geography** из драйвера для управления ссылками на Java этих типов данных. |
  
## <a name="see-also"></a>См. также:

[Пример приложений драйвера JDBC](../../../connect/jdbc/code-samples/sample-jdbc-driver-applications.md)  
