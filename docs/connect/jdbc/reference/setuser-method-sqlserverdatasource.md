---
title: Метод setUser (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setUser
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: d2ea7906-2d10-438d-aa51-f576eea923c7
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 13ea4a88b4b7a233695e134ef79daccd608d5813
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66773211"
---
# <a name="setuser-method-sqlserverdatasource"></a>Метод setUser (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает имя пользователя, используемое для соединения с источником данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setUser(java.lang.String user)  
```  
  
#### <a name="parameters"></a>Параметры  
 *user*  
  
 Значение типа **String**, содержащее имя пользователя.  
  
## <a name="remarks"></a>Remarks  
 Метод setUser задает имя пользователя, которое будет использоваться для соединения с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Если значение имени пользователя не задано, метод [getUser](../../../connect/jdbc/reference/getuser-method-sqlserverdatasource.md) возвращает значение NULL по умолчанию.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
