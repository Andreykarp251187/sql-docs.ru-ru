---
description: ISSCommandWithParameters (поставщик собственного клиента OLE DB)
title: ISSCommandWithParameters (поставщик собственного клиента OLE DB)
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- ISSCommandWithParameters (OLE DB)
apitype: COM
helpviewer_keywords:
- ISSCommandWithParameters interface
ms.assetid: 3419b7f3-36a3-4863-816e-e641e4e90496
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 896926a74bff62ccc84c3a80ad0169dd97858524
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88490781"
---
# <a name="isscommandwithparameters-native-client-ole-db-provider"></a>ISSCommandWithParameters (поставщик собственного клиента OLE DB)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Интерфейс**ISSCommandWithParameters** обеспечивает поддержку [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML и определяемых пользователем типов данных. Этот дополнительный интерфейс наследует основной интерфейс OLE DB, **ICommandWithParameters**. Помимо трех методов, наследуемых из интерфейса **ICommandWithParameters**( **GetParameterInfo**, **MapParameterNames**и **SetParameterInfo**), интерфейс **ISSCommandWithParameters** содержит два новых метода, которые используются для обработки серверных типов данных.  
  
> [!NOTE]  
>   Интерфейс **ISSCommandWithParameters** может использоваться при применении компонентов службы, однако сами компоненты службы этот интерфейс не используют.  
  
|Метод|Description|  
|------------|-----------------|  
|[ISSCommandWithParameters::GetParameterProperties (OLE DB)](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-getparameterproperties-ole-db.md)|Возвращает одну структуру набора свойств **SSPARAMPROPS** в массиве для каждого определяемого пользователем типа данных или XML-параметра, переданного команде, однако для других типов параметров не возвращается ничего.|  
|[ISSCommandWithParameters::SetParameterProperties (OLE DB)](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-setparameterproperties-ole-db.md)|Задает свойства параметров для каждого параметра в отдельности по порядковому номеру либо задает свойства всех параметров сразу путем указания массива структур **SSPARAMPROPS** .|  
  
## <a name="see-also"></a>См. также:  
 [Интерфейсы (OLE DB)](https://msdn.microsoft.com/library/34c33364-8538-45db-ae41-5654481cda93)   
 [Использование типов данных XML](../../relational-databases/native-client/features/using-xml-data-types.md)   
 [Использование определяемых пользователем типов](../../relational-databases/native-client/features/using-user-defined-types.md)  
  
  
