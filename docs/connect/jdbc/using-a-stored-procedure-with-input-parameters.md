---
title: Использование хранимых процедур с входными параметрами | Документация Майкрософт
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8f491b70-7d1b-42bd-964f-9a8b86af5eaa
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6c84e4081b9369d504d173387c6944b06d927c9c
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2019
ms.locfileid: "69026903"
---
# <a name="using-a-stored-procedure-with-input-parameters"></a>Использование хранимых процедур с входными параметрами

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Хранимая процедура [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которую можно вызвать, содержит один или несколько параметров IN, то есть параметров, которые могут быть использованы для передачи данных в хранимую процедуру. В [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] предусмотрен класс [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md), который может быть использован для вызова этого вида хранимых процедур и обработки возвращаемых ими данных.

При использовании драйвера JDBC для вызова хранимой процедуры с параметрами IN следует использовать escape-последовательность SQL `call` вместе с методом [prepareCall](../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md) класса [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md). Ниже приводится синтаксис escape-последовательности `call` с параметрами IN.

`{call procedure-name[([parameter][,[parameter]]...)]}`

> [!NOTE]  
> Дополнительные сведения о escape-последовательностях SQL см. в разделе [использование escape](../../connect/jdbc/using-sql-escape-sequences.md)-последовательностей SQL.

При создании escape-последовательности `call` укажите параметры IN при помощи (символ вопросительного знака (?)). Этот символ выполняет роль заполнителя для значений параметра, которые будут переданы хранимой процедуре. Чтобы указать значение для параметра, можно использовать один из методов задания класса SQLServerPreparedStatement. Метод задания, который можно использовать, определяется типом данных параметра IN.

Во время передачи значения методу задания следует указать не только фактическое значение, которое будет использоваться в параметре, но также порядковый номер параметра в хранимой процедуре. Например, если хранимая процедура содержит единственный параметр IN, его порядковый номер будет 1. Если хранимая процедура содержит два параметра, порядковый номер первого значения будет 1, а второго — 2.

В качестве примера вызова хранимой процедуры, содержащей параметр IN, используйте хранимую процедуру uspGetEmployeeManagers в образце базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]. Эта хранимая процедура принимает один параметр входных данных с именем EmployeeID, который является целым значением, и возвращает рекурсивный список служащих и их менеджеров на основе указанного EmployeeID. Ниже приводится код Java для вызова этой хранимой процедуры.

```java
public static void executeSprocInParams(Connection con) throws SQLException {  
    try(PreparedStatement pstmt = con.prepareStatement("{call dbo.uspGetEmployeeManagers(?)}"); ) {  

        pstmt.setInt(1, 50);  
        ResultSet rs = pstmt.executeQuery();  

        while (rs.next()) {  
            System.out.println("EMPLOYEE:");  
            System.out.println(rs.getString("LastName") + ", " + rs.getString("FirstName"));  
            System.out.println("MANAGER:");  
            System.out.println(rs.getString("ManagerLastName") + ", " + rs.getString("ManagerFirstName"));  
            System.out.println();  
        }  
    }
}
```

## <a name="see-also"></a>См. также раздел

[Использование инструкций с хранимыми процедурами](../../connect/jdbc/using-statements-with-stored-procedures.md)
