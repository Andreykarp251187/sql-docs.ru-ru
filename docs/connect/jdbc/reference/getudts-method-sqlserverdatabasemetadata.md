---
title: Метод getUDTs (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getUDTs
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c4396453-dcb0-4132-8325-06b3c7896b3b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f51e5345cf7c7b78a0a3a37220927000af7d0fa7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67978421"
---
# <a name="getudts-method-sqlserverdatabasemetadata"></a>Метод getUDTs (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает описание определяемых пользователем типов, определенных в конкретной схеме.  
  
> [!NOTE]  
>  В настоящее время этот метод не поддерживается с помощью [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]. При использовании этот метод всегда возвращает пустой результирующий набор.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.ResultSet getUDTs(java.lang.String catalog,  
                                  java.lang.String schemaPattern,  
                                  java.lang.String typeNamePattern,  
                                  int[] types)  
```  
  
#### <a name="parameters"></a>Параметры  
 *catalog*  
  
 Значение типа **String**, содержащее имя каталога.  
  
 *счемапаттерн*  
  
 Значение типа **String**, содержащее шаблон имени схемы.  
  
 *typeNamePattern*  
  
 Значение **String**, содержащее шаблон имени типа.  
  
 *types*  
  
 Массив целочисленных значений, содержащий включаемые типы данных. Значение «null» указывает на то, что должны быть включены все типы данных.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getUDTs определен с помощью метода getUDTs в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
