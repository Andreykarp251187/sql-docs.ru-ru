---
title: Обработка нескольких результирующих наборов с помощью интерфейса IMultipleResults | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- multiple rowsets
- rowsets [OLE DB], multiple
- IMultipleResults interface
- multiple-rowset results
ms.assetid: 754d3f30-7d94-4b67-8dac-baf2699ce9c6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e160733e01c3df2063a57d61bb8178438d383e1a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63155024"
---
# <a name="using-imultipleresults-to-process-multiple-result-sets"></a>Обработка нескольких результирующих наборов при помощи интерфейса IMultipleResults
  Потребители используют **IMultipleResults** интерфейс для обработки результатов, возвращенных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполнение команды поставщика OLE DB для собственного клиента. Когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента отправляет команду для выполнения, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняет инструкции и возвращает результаты.  
  
 Клиент должен обработать все результаты выполнения команды. Так как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполнение команды поставщика OLE DB для собственного клиента могут создавать объекты с несколькими наборами строк как результат, используйте **IMultipleResults** интерфейса, чтобы убедиться, что выполняется получение данных приложения инициированные клиентом цикла приема-передачи.  
  
 Следующая инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)] формирует несколько наборов строк, при этом некоторые содержат данные строк из таблицы **OrderDetails**, а некоторые — результаты предложения COMPUTE BY:  
  
```  
SELECT OrderID, FullPrice = (UnitPrice * Quantity), Discount,  
    Discounted = UnitPrice * (1 - Discount) * Quantity  
FROM OrderDetails  
ORDER BY OrderID  
COMPUTE  
    SUM(UnitPrice * Quantity), SUM(UnitPrice * (1 - Discount) * Quantity)  
    BY OrderID  
```  
  
 Если потребитель выполняет команду, содержащую этот текст, и запрашивает набор строк в качестве интерфейса возвращаемых результатов, возвращается только первый набор строк. Потребитель может обработать все строки в возвращенном наборе строк. Но, если свойство источника данных DBPROP_MULTIPLECONNECTIONS имеет значение VARIANT_FALSE и режим MARS не включен для подключения, никакие другие команды могут выполняться в объекте сеанса ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента не будет создавать другой подключение) пока не будет отменена команда. Если режим MARS не включен в соединении, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента возвращает ошибку DB_E_OBJECTOPEN, если свойство DBPROP_MULTIPLECONNECTIONS имеет значение VARIANT_FALSE и возвращает E_FAIL, если активная транзакция.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента возвратит также DB_E_OBJECTOPEN при использовании потоковых выходных параметров и приложение не потребило все значения возвращенных параметров перед вызовом **IMultipleResults::GetResults**  для получения следующего набора результатов. Если режим MARS не включен и соединение занято выполнением команды, не производящей набор строк или производящей набор строк, который не является серверным курсором, и в том случае, если свойство источника данных DBPROP_MULTIPLECONNECTIONS имеет значение VARIANT_TRUE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client Поставщик OLE DB создает дополнительные соединения для поддержки параллельных объектов команды, если транзакция является активной, в противном случае возвращает ошибку. Управление транзакциями и блокировками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] производит отдельно для каждого соединения. Если создано второе соединение, команда в отдельном соединении не использует общие блокировки. Необходимо соблюдать осторожность и убедиться, что одна команда не блокирует другую, удерживая блокировки строк, запрошенных другой командой. Если включен режим MARS, в одном соединении могут быть активными несколько команд, а если выполняются явные транзакции, все команды совместно используют общую транзакцию.  
  
 Потребитель может отменить команду с помощью метода [ISSAbort::Abort](../native-client-ole-db-interfaces/issabort-abort-ole-db.md) или освободив все удерживаемые ссылки на объект команды и производный набор строк.  
  
 Использование интерфейса **IMultipleResults** во всех экземплярах позволяет потребителю получить все наборы строк, сформированные командой, и соответствующим образом определить, когда нужно отменить выполнение команды, чтобы освободить объект сеанса для других команд.  
  
> [!NOTE]  
>  При использовании курсоров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполнение команды создает курсор [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает успех или ошибку создания курсора, поэтому обмен данными с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] завершается по выполнении команды. Следовательно, каждый вызов **GetNextRows** становится обменом данными. Таким образом, могут существовать несколько активных объектов команд, каждая из которых обрабатывает набор строк, являющийся результатом выборки из серверного курсора. Дополнительные сведения см. в статье [Наборы строк и курсоры SQL Server](../native-client-ole-db-rowsets/rowsets-and-sql-server-cursors.md).  
  
## <a name="see-also"></a>См. также  
 [Команды](commands.md)  
  
  
