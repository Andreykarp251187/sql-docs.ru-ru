---
title: Метод createBlob (SQLServerConnection) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 630a93b0-6e3c-4255-a007-1097ce0ee243
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 38c4ccf19e42946506b274cdef2058726ccfe407
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66768262"
---
# <a name="createblob-method-sqlserverconnection"></a>Метод createBlob (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Создает объект BLOB-объект, не содержащий данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.Blob createBlob()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Большого двоичного объекта.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод createBlob указывается с помощью метода createBlob в интерфейсе java.sql.Connection.  
  
 Этот метод исключает необходимость в [конструктор SQLServerBlob &#40;SQLServerConnection, byte&#41;](../../../connect/jdbc/reference/sqlserverblob-constructor-sqlserverconnection-byte.md).  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
