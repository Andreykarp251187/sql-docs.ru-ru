---
title: Соединение и извлечение данных | Документация Майкрософт
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ce43cc20-46a3-42ff-a3fb-75ad1ed10e08
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: c87089b59855ef2c68a9e3b1051ed39850d7b17e
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66770065"
---
# <a name="connecting-and-retrieving-data"></a>Соединение и извлечение данных

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

При работе с драйвером [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] есть два основных способа установить подключение к базе данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Во-первых, можно задать свойства подключения в URL-адресе подключения, а затем вызвать метод getConnection класса DriverManager для возвращения объекта [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).  
  
> [!NOTE]  
> Список свойств соединения, поддерживаемых драйвером JDBC, см. в разделе [заданию свойств соединения](../../../connect/jdbc/setting-the-connection-properties.md).  
  
По второму методу свойства подключения определяются с помощью методов задания класса [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) и последующего вызова метода [getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md), возвращающего объект SQLServerConnection.  
  
В разделах этой статьи описаны различные способы подключения к базе данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и показаны приемы для извлечения данных.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Пример URL-адреса подключения](../../../connect/jdbc/code-samples/connection-url-sample.md)|Описывает подключение к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] по URL-адресу и последующее использование инструкции SQL для извлечения данных.|  
|[Пример источника данных](../../../connect/jdbc/code-samples/data-source-sample.md)|Описывается порядок использования источника данных для соединения с SQL Server и последующего использования хранимой процедуры для извлечения данных.|  
  
## <a name="see-also"></a>См. также:

[Пример приложений драйвера JDBC](../../jdbc/code-samples/sample-jdbc-driver-applications.md)
  
