---
title: Наблюдение за трассировками (XMLA) | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 60c44d2771033c86814cb9dbc0a18aab7c79c483
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63261631"
---
# <a name="monitoring-traces-xmla"></a>Наблюдение за трассировками (XMLA)
  Можно использовать [Subscribe](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/subscribe-element-xmla) в XML для аналитики (XMLA) для наблюдения за существующей трассировкой, определенной в экземпляре команда [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. **Subscribe** команда возвращает результаты трассировки в виде набора строк.  
  
## <a name="specifying-a-trace"></a>Задание трассировки  
 [Объект](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) свойство **Subscribe** команды должен содержать ссылку объекта либо [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] экземпляра или трассировку на [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] экземпляра. Если **объект** свойство не указано или не указан идентификатор трассировки в **объект** свойство, **Subscribe** команда отслеживает трассировку сеанса по умолчанию для явного сеанса, указанного в заголовке SOAP для команды.  
  
## <a name="returning-results"></a>Возвращаемые результаты  
 **Subscribe** команда возвращает набор строк, содержащий события трассировки, охватываемым указанной трассировки. **Subscribe** команда возвращает результаты трассировки, пока не будет отменена командой [отменить](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla) команды.  
  
 Набор строк содержит столбцы, перечисленные в следующей таблице.  
  
|Столбец|Data type|Описание|  
|------------|---------------|-----------------|  
|EventClass|Целочисленный|Класс события, полученного трассировкой.|  
|EventSubclass|Long integer|Подкласс события, полученного трассировкой.|  
|CurrentTime|Datetime|Время начала события, если доступно. Ожидаемые форматы фильтрации: «ГГГГ-ММ-ДД» и «ГГГГ-ММ-ДД ЧЧ:ММ:СС».|  
|StartTime|Datetime|Время начала события, если доступно. Ожидаемые форматы фильтрации: «ГГГГ-ММ-ДД» и «ГГГГ-ММ-ДД ЧЧ:ММ:СС».|  
|EndTime|Datetime|Время окончания события, если оно известно. Ожидаемые форматы фильтрации: «ГГГГ-ММ-ДД» и «ГГГГ-ММ-ДД ЧЧ:ММ:СС».<br /><br /> Этот столбец не заполняется для классов событий, описывающих начало процесса или действия.|  
|Duration|Long integer|Общее время (в миллисекундах), прошедшее для события.|  
|CPUTime|Long integer|Общее время процессора (в миллисекундах), прошедшее для события.|  
|JobID|Long integer|Идентификатор задания для процесса.|  
|SessionID|String|Идентификатор сеанса, к которому относится происшедшее событие.|  
|SessionType|String|Тип сеанса, к которому относится происшедшее событие.|  
|ProgressTotal|Long integer|Общий ход выполнения, о котором сообщает событие, в числовом или количественном выражении.|  
|IntegerData|Long integer|Целочисленные данные, связанные с событием. Содержимое этого столбца зависит от класса событий и подкласса событий.|  
|ObjectID|String|Идентификатор объекта, к которому относится происшедшее событие.|  
|ObjectType|String|Тип объекта, указанного в ObjectName.|  
|ObjectName|String|Имя объекта, к которому относится происшедшее событие.|  
|ObjectPath|String|Иерархический путь объекта, к которому относится происшедшее событие. Путь представлен в виде строки идентификаторов объектов, разделенной запятыми, для родителей объекта, указанного в ObjectName.|  
|ObjectReference|String|XML-представление ссылки объекта для объекта, указанного в ObjectName.|  
|NestLevel|Целочисленный|Уровень транзакции, к которой относится происшедшее событие.|  
|NumSegments|Long integer|Количество сегментов данных, затронутых или открытых командой, к которой относится происшедшее событие.|  
|Severity|Целочисленный|Степень серьезности исключения для события. Столбец может содержать одно из следующих значений.<br /><br /> <br /><br /> 0: Success<br /><br /> <br /><br /> 1: Сведения<br /><br /> <br /><br /> 2: Предупреждение<br /><br /> <br /><br /> 3: Ошибка|  
|Success|Логическое значение|Указывает, выполнена ли команда успешно или окончилась неудачей.|  
|Ошибка|Long integer|Номер ошибки события, если это применимо.|  
|ConnectionID|String|Идентификатор соединения, к которому относится происшедшее событие.|  
|DatabaseName|String|Имя базы данных, к которой относится происшедшее событие.|  
|NTUserName|String|Имя пользователя Windows, связанного с событием.|  
|NTDomainName|String|Домен пользователя Windows, связанного с событием.|  
|ClientHostName|String|Имя компьютера, на котором выполняется клиентская программа. Данный столбец заполняется значениями, переданными клиентским приложением.|  
|ClientProcessID|Long integer|Идентификатор процесса клиентского приложения.|  
|ApplicationName|String|Имя клиентского приложения, установившего соединение с экземпляром служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Этот столбец заполняется значениями, передаваемыми клиентским приложением, а не отображаемым именем программы.|  
|NTCanonicalUserName|String|Каноническое имя пользователя Windows пользователя, связанного с событием.|  
|SPID|String|Идентификатор процесса сервера (SPID) сеанса, к которому относится происшедшее событие. Значение этого столбца непосредственно соответствует идентификатору сеанса, указанному в заголовке SOAP сообщения XMLA, к которому относится происшедшее событие.|  
|TextData|String|Текстовые данные, связанные с событием. Содержимое этого столбца зависит от класса событий и подкласса событий.|  
|ServerName|String|Имя экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], к которому относится происшедшее событие.|  
|RequestParameters|String|Параметры параметризированного запроса или команды XMLA, к которой относится происшедшее событие.|  
|RequestProperties|String|Свойства метода XMLA, к которому относится происшедшее событие.|  
  
## <a name="see-also"></a>См. также  
 [Разработка с использованием XMLA в службах Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
