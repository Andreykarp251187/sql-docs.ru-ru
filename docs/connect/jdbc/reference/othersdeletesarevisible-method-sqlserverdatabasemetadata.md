---
title: Метод othersDeletesAreVisible (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.othersDeletesAreVisible
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c4692a8c-e6b7-4edc-9dad-7af816988de5
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 421de1ae536c6bc0ff25f573f131f048df978c3d
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66789194"
---
# <a name="othersdeletesarevisible-method-sqlserverdatabasemetadata"></a>Метод othersDeletesAreVisible (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение, определяющее, являются ли видимыми операции удаления, выполненные другими пользователями.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean othersDeletesAreVisible(int type)  
```  
  
#### <a name="parameters"></a>Параметры  
 *type*  
  
 Значение типа **int**, указывающее тип результирующего набора. Оно может быть равно следующим значениям, определенным в java.sql.ResultSet или SQLServerResultSet:  
  
## <a name="javasqlresultset-types"></a>Типы java.sql.ResultSet  
 TYPE_FORWARD_ONLY  
  
 TYPE_SCROLL_SENSITIVE  
  
 TYPE_SCROLL_INSENSITIVE  
  
## <a name="sqlserverresultset-types"></a>Типы SQLServerResultSet  
 TYPE_SS_SCROLL_STATIC  
  
 TYPE_SS_SCROLL_KEYSET  
  
 TYPE_SS_DIRECT_FORWARD_ONLY  
  
 TYPE_SS_SERVER_CURSOR_FORWARD_ONLY  
  
 TYPE_SS_SCROLL_DYNAMIC  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если операции удаления видимы. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод othersDeletesAreVisible указывается с помощью метода othersDeletesAreVisible в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
