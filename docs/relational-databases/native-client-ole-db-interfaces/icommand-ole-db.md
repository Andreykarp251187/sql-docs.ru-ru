---
title: ICommand (OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ICommand [SQL Server Native Client]
ms.assetid: 5e24b3a0-0658-44fc-b653-f4c52f9eb328
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f0059533e9f0fb5d0722f940c9687f9404b0ef80
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73789429"
---
# <a name="icommand-ole-db"></a>ICommand (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  В этом разделе обсуждаются особенности OLE DB, касающиеся собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="icommandexecute"></a>ICommand::Execute  
 Вставка данных, превышающих размер столбца, как правило, приводит к ошибке. Однако в некоторых ситуациях происходит возврат значения S_OK, хотя параметру *dwStatus* присваивается значение DBSTATUS_S_TRUNCATED. Обычно такая ситуация возникает при вставке данных с параметрами, когда размера столбца не хватает для размещения данных и не был вызван метод **ICommandWithParameters::SetParameterInfo** .  
  
## <a name="see-also"></a>См. также раздел  
 [Интерфейсы &#40;OLE DB&#41;](https://msdn.microsoft.com/library/34c33364-8538-45db-ae41-5654481cda93)  
  
  
