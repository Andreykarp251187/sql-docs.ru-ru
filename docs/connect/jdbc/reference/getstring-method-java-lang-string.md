---
title: Метод getString (java.lang.String) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getString (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f67371e0-e879-4188-85fc-ecb85f0be2a9
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 114eaa8b3300f5e0785a3bac389eb00d4d5ee7ec
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66773724"
---
# <a name="getstring-method-javalangstring"></a>Метод getString (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает значение заданного параметра в виде значения типа данных **String** на языке программирования Java по заданному имени параметра.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.String getString(java.lang.String sCol)  
```  
  
#### <a name="parameters"></a>Параметры  
 *sCol*  
  
 Значение типа **String**, содержащее имя параметра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение типа **String**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getString определен с помощью метода getString в интерфейсе java.sql.CallableStatement.  
  
 Все столбцы в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] можно возвращать в виде строковых значений. Это значит, что можно возвращать строковое представление всех числовых и символьных типов, а также шестнадцатеричное представление двоичных столбцов, таких как binary, varbinary, varbinary(max), image, timestamp и uniqueidentifier.  
  
 Типы, зависящие от расположения, такие как money, smallmoney, datetime, smalldatetime, float, real, decimal и numeric, возвращают канонический формат toString() для базового значения типа.  
  
 Определяемые пользователем типы возвращаются в виде шестнадцатеричных строковых значений.  
  
## <a name="see-also"></a>См. также:  
 [Метод getString (SQLServerCallableStatement)](../../../connect/jdbc/reference/getstring-method-sqlservercallablestatement.md)   
 [Элементы SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Класс SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
