---
title: Реализация класса DataReader для модуля обработки данных | Документы Майкрософт
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], data readers
- data readers [Reporting Services]
- DataReader class
- read-only data
ms.assetid: 23e286e7-6074-4fbe-be29-203420d6c3d0
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 1367774e84dd10c2749f46a1ee6c38b8d5f6dd7b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63193917"
---
# <a name="implementing-a-datareader-class-for-a-data-processing-extension"></a>Реализация класса DataReader для модуля обработки данных
  Объект **DataReader** позволяет клиенту принимать доступный только для чтения однопроходный поток данных из источника данных. Результаты возвращаются после выполнения запроса и хранятся в сетевом буфере на клиенте до тех пор, пока не будут запрошены с помощью метода **Read** класса **DataReader**. Чтобы создать класс **DataReader**, следует реализовать <xref:Microsoft.ReportingServices.DataProcessing.IDataReader> и, возможно, реализовать <xref:Microsoft.ReportingServices.DataProcessing.IDataReaderExtension>. Объект **DataReader** позволяет увеличить производительность приложения двумя способами: путем получения данных, как только они становятся доступны, вместо ожидания возвращения всех результатов запроса, а также (по умолчанию) путем сохранения в памяти только одной строки за один раз, что снижает нагрузку на системные ресурсы.  
  
 После создания экземпляра класса **Command** создайте объект **DataReader**, вызвав **Command.ExecuteReader** для получения строк из источника данных. Реализация **DataReader** должна предоставлять две основные возможности: однопроходный доступ к результирующим наборам, полученным при выполнении команды, и доступ к типам столбцов, именам и значениям в каждой строке. Клиенты используют метод **Read** объекта **DataReader** для получения строки из результатов запроса.  
  
 В конструкторе отчетов объект **DataReader** используется для получения списка полей, а также сведений о схеме для результирующего набора. Это достигается путем реализации методов **GetName**, **GetValue**, **GetFieldType** и **GetOrdinal** экземпляра <xref:Microsoft.ReportingServices.DataProcessing.IDataReader>.  
  
 Экземпляр <xref:Microsoft.ReportingServices.DataProcessing.IDataReaderExtension> позволяет предоставлять конкретные сведения статистической обработки результирующего набора. Пример реализации класса **DataReader** см. в разделе [Образцы продуктов служб SQL Server Reporting Services](https://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>См. также:  
 [Модули служб Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Реализация модуля обработки данных](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Библиотека модулей Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
