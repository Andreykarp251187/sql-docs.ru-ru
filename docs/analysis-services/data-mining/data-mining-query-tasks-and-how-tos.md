---
title: Запросов интеллектуального анализа данных, задачи и инструкции по | Документация Майкрософт
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c3c06f78302aa46fdebe05b95d394905116b973f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68210096"
---
# <a name="data-mining-query-tasks-and-how-tos"></a>Задачи и инструкции по запросам интеллектуального анализа данных
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Чтобы воспользоваться моделями интеллектуального анализа данных, чрезвычайно важно грамотно составлять запросы. В этом разделе приведены ссылки на примеры создания запросов к модели интеллектуального анализа данных с помощью средств, предоставляемых в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Дополнительные сведения о том, что представляет собой запрос к модели интеллектуального анализа данных, а также о типах создаваемых запросов см. в разделе [Запрос интеллектуального анализа данных](../../analysis-services/data-mining/data-mining-queries.md).  
  
## <a name="creating-queries-with-prediction-query-builder"></a>Создание запросов с помощью построителя прогнозирующих запросов  
 Построитель прогнозирующих запросов имеется как в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] , так и в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] . Он служит для графического построения запросов к моделям интеллектуального анализа. В следующих разделах описано, как можно выбрать модель, указать источник данных, настроить прогнозы и сохранить полученные данные.  
  
-   [Создание прогнозирующего запроса с помощью построителя прогнозирующих запросов](../../analysis-services/data-mining/create-a-prediction-query-using-the-prediction-query-builder.md)  
  
-   [Создание одноэлементного запроса в конструкторе интеллектуального анализа данных](../../analysis-services/data-mining/create-a-singleton-query-in-the-data-mining-designer.md)  
  
-   [Создание прогнозирующего запроса с помощью построителя прогнозирующих запросов](../../analysis-services/data-mining/create-a-prediction-query-using-the-prediction-query-builder.md)  
  
-   [Просмотр и сохранение результатов прогнозирующего запроса](../../analysis-services/data-mining/view-and-save-the-results-of-a-prediction-query.md)  
  
-   [Изменение прогнозирующего запроса вручную](../../analysis-services/data-mining/manually-edit-a-prediction-query.md)  
  
-   [Применение функций прогнозирования к модели](../../analysis-services/data-mining/apply-prediction-functions-to-a-model.md)  
  
-   [Выбор и сопоставление входных данных для прогнозирующего запроса](../../analysis-services/data-mining/choose-and-map-input-data-for-a-prediction-query.md)  
  
## <a name="using-other-data-mining-query-tools"></a>Использование других средств построения запросов интеллектуального анализа данных  
 Кроме построителя прогнозирующих запросов, можно воспользоваться расширениями интеллектуального анализа данных или XMLA, введя запрос непосредственно в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] . Вы также можете программно создавать прогнозирующие запросы и направлять их на сервер [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . В следующих разделах приведены дополнительные сведения о создании и использовании прогнозирующих запросов вне построителя прогнозирующих запросов.  
  
 [Создание одноэлементного прогнозирующего запроса из шаблона](../../analysis-services/data-mining/create-a-singleton-prediction-query-from-a-template.md)  
 Описывает использование средств в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] для построения и выполнения прогнозирующего запроса.  
  
 [создать одноэлементный прогнозирующий запрос из шаблона](../../analysis-services/data-mining/create-a-singleton-prediction-query-from-a-template.md)  
 Описывает использование шаблонов, предоставляемых в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , для добавления параметров прогнозирующего запроса.  
  
 [изменить значение времени ожидания для запросов интеллектуального анализа данных](../../analysis-services/data-mining/change-the-time-out-value-for-data-mining-queries.md)  
 Описывает задание на сервере свойств, управляющих поведением запросов, связанных с интеллектуальным анализом данных.  
  
 [Создание запроса содержимого к модели интеллектуального анализа данных](../../analysis-services/data-mining/create-a-content-query-on-a-mining-model.md)  
 Описывает создание запросов, возвращающих детализированные данные, хранящиеся в модели интеллектуального анализа данных, на основе наборов рядов схемы интеллектуального анализа.  
  
 [Создание запроса интеллектуального анализа данных с помощью XMLA](../../analysis-services/data-mining/create-a-data-mining-query-by-using-xmla.md)  
 Описывает создание запросов содержимого модели интеллектуального анализа данных с помощью XMLA-шаблонов в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Справочник по языку запросов и выражений (службы Analysis Services)](http://msdn.microsoft.com/library/9597533d-35f4-4742-9d8c-7af392163527)   
 [Хранимые процедуры интеллектуального анализа данных (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/data-mining-stored-procedures-analysis-services-data-mining.md)  
  
  
