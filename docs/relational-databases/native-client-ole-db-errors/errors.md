---
title: Ошибки | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- OLE/COM errors
- errors [OLE DB]
- OLE DB error handling, about error handling
- OLE DB error handling
ms.assetid: bd0612f4-96ef-4919-b0f9-b5447210fe93
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 45dd62bfcf1006bd675259c279b1f85a64ea630a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "73769447"
---
# <a name="errors"></a>ошибки
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Объекты OLE/COM сообщают об ошибках с помощью кодов возврата HRESULT функций-членов объектов. Тип HRESULT в OLE/COM представляет собой структуру с битовой упаковкой. OLE предоставляет макросы для разыменования членов структуры.  
  
 OLE/COM задает интерфейс **IErrorInfo**. Интерфейс предоставляет доступ к методам (например, **GetDescription**). Это позволяет клиентам получать подробную информацию об ошибках у серверов OLE/COM. В OLE DB к интерфейсу **IErrorInfo** добавлена поддержка возврата сразу нескольких пакетов информации об ошибках на один вызов метода.  
  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может возвращать несколько ошибок. Приложение может получать ошибки сервера поочередно, вызывая метод [IMultipleResults::GetResult](https://go.microsoft.com/fwlink/?LinkId=129630) в сочетании с ISQLErrorInfo и IErrorRecords.  
  
 Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента предоставляет OLE DB расширенный интерфейс **IErrorInfo**с записью, Пользовательский **ISQLErrorInfo**и интерфейсы объекта [ISQLServerErrorInfo](https://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1) Error, относящиеся к конкретному поставщику.  
  
 Сведения об ошибках трассировки см. в статье [Отслеживание доступа к данным](https://go.microsoft.com/fwlink/?LinkId=125805). Дополнительные сведения об улучшениях трассировки ошибок, добавленных [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]в, см. в разделе [доступ к диагностическим сведениям в журнале расширенных событий](../../relational-databases/native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md).  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Коды возврата](../../relational-databases/native-client-ole-db-errors/return-codes.md)  
  
-   [Сведения в интерфейсах обработки ошибок](../../relational-databases/native-client-ole-db-errors/information-in-error-interfaces.md)  
  
-   [Подробные сведения об ошибках SQL Server](../../relational-databases/native-client-ole-db-errors/sql-server-error-detail.md)  
  
-   [Получение информации об ошибке](../../relational-databases/native-client-ole-db-errors/retrieving-error-information.md)  
  
-   [Результаты сообщения SQL Server](../../relational-databases/native-client-ole-db-errors/sql-server-message-results.md)  
  
## <a name="see-also"></a>См. также:  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
