---
title: Обнаружение метаданных | Документация Майкрософт
description: Обнаружение метаданных в OLE DB Driver for SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 95f3d5aad2705645cc58c1b4a85e40ad9e5b0d26
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86006926"
---
# <a name="metadata-discovery"></a>Обнаружение метаданных
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Улучшенное обнаружение метаданных в [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] позволяет гарантировать, что в приложениях драйвера OLE DB для SQL Server метаданные столбца или параметра, возвращенные в результате выполнения запроса, будут полностью соответствовать формату метаданных, указанному до выполнения запроса, или будут совместимы с ним. Если формат метаданных, возвращенных в результате выполнения запроса, будет несовместим с форматом, указанным до выполнения запроса, возвращается ошибка.  
  
 В функциях bcp, а также интерфейсах IBCPSession и IBCPSession2 теперь можно задавать отложенное чтение (отложенное обнаружение метаданных), чтобы избежать обнаружения метаданных для операций с параметром queryout. Это позволяет повысить производительность и устранить ошибки обнаружения метаданных.  
  
 Если при разработке приложения с помощью драйвера OLE DB для SQL Server выполняется подключение к серверу с версией, более ранней, чем [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], функция обнаружения метаданных будет соответствовать версии сервера.  
  
## <a name="remarks"></a>Remarks   
 В [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] были изменены следующие методы OLE DB, которые теперь обеспечивают улучшенное обнаружение метаданных:  
  
-   IColumnsInfo::GetColumnInfo  
  
-   IColumnsRowset::GetColumnsRowset  
  
-   ICommandWithParameters::GetParameterInfo (дополнительные сведения см. в разделе документации [ICommandWithParameters](../../oledb/ole-db-interfaces/icommandwithparameters.md)).  
  
 Повышение производительности также заметно при указании формата метаданных с помощью метода IBCPSession::BCPSetBulkMode.  
  
 Улучшенное обнаружение метаданных в OLE DB Driver for SQL Server стало возможным благодаря добавлению в [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] двух хранимых процедур:  
  
-   sp_describe_first_result_set  
  
-   sp_describe_undeclared_parameters  
  
## <a name="see-also"></a>См. также:  
 [Возможности драйвера OLE DB для SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
