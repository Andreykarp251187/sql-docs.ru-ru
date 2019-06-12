---
title: Пространственных типах данных образец для драйвера MSSQL JDBC | Документация Майкрософт
ms.custom: ''
ms.date: 07/30/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: b05182b5dbed154aafd86feec9f73e433f569791
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66798347"
---
# <a name="spatial-data-types-sample"></a>Образец пространственных типов данных

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Это [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] пример приложения демонстрирует для создания, вставки и извлечения пространственных типов данных (Geometry и Geography).
  
Файл кода для этого примера с именем SpatialDataTypes.java находится в следующей папке:  

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples\datatypes  
```

## <a name="requirements"></a>Требования  

Чтобы запустить этот пример приложения, необходимо включить в параметр classpath путь к файлу mssql-jdbc.jar. Дополнительные сведения о том, как путь к классу см. в разделе [с помощью драйвера JDBC](../../connect/jdbc/using-the-jdbc-driver.md).  

> [!NOTE]  
> Драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] включает файлы библиотек классов mssql-jdbc, которые используются в зависимости от выбранных параметров среды выполнения Java (JRE). Для получения дополнительных сведений о том, какой JAR-файл выбрать, см. статью [Требования к системе для драйвера JDBC](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  
  
## <a name="example"></a>Пример

В следующем примере образец кода создает таблицу с именем SpatialDataTypesTable_JDBC_Sample, которая содержит столбцы «Геометрия» и «География».

Пример сначала создает объекты «Геометрия» и «География» из хорошо-Known-Text (WKT) представляет ТОЧКУ. Для сопоставления данных для каждого столбца, соответствующим образом используется SQLServerPreparedStatement с параметризованным запросом.

Наконец в примере вставляет данные в таблице и извлекает его. Данные отображаются в виде WKT.

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;
import java.sql.Statement;
import com.microsoft.sqlserver.jdbc.Geography;
import com.microsoft.sqlserver.jdbc.Geometry;
import com.microsoft.sqlserver.jdbc.SQLServerPreparedStatement;
import com.microsoft.sqlserver.jdbc.SQLServerResultSet;

public class SpatialDataTypes {

    private static String tableName = "SpatialDataTypesTable_JDBC_Sample";

    public static void main(String[] args) {

        // Create a variable for the connection string.
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=<database>;user=<user>;password=<password>";
        // Establish the connection.
        try (Connection con = DriverManager.getConnection(connectionUrl); Statement stmt = con.createStatement();) {
            dropAndCreateTable(stmt);

            // TODO: Implement Sample code
            String geoWKT = "POINT(3 40 5 6)";
            Geometry geomWKT = Geometry.STGeomFromText(geoWKT, 0);
            Geography geogWKT = Geography.STGeomFromText(geoWKT, 4326);

            try (SQLServerPreparedStatement pstmt = (SQLServerPreparedStatement) con
                    .prepareStatement("insert into " + tableName + " values (?, ?)");) {
                pstmt.setGeometry(1, geomWKT);
                pstmt.setGeography(2, geogWKT);
                pstmt.execute();

                SQLServerResultSet rs = (SQLServerResultSet) stmt.executeQuery("select * from " + tableName);
                rs.next();

                System.out.println("Geometry data: " + rs.getGeometry(1));
                System.out.println("Geography data: " + rs.getGeography(2));
            }
        } catch (Exception e) {
            e.printStackTrace();
        }
    }

    private static void dropAndCreateTable(Statement stmt) throws SQLException {
        stmt.executeUpdate("if object_id('" + tableName + "','U') is not null" + " drop table " + tableName);

        stmt.executeUpdate("Create table " + tableName + " (c1 geometry, c2 geography)");
    }
}
```

## <a name="see-also"></a>См. также:  

[Работа с типами данных JDBC](../../connect/jdbc/working-with-data-types-jdbc.md)  
  
