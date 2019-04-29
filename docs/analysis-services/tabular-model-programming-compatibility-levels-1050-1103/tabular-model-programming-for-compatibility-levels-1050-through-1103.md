---
title: Analysis Services табличной модели программирования для уровни совместимости 1050 – 1103 | Документация Майкрософт
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fe2ce43ffb5d2c5be0afb39931f231d2f0d24e14
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63025295"
---
# <a name="tabular-model-programming-for-compatibility-levels-1050-through-1103"></a>Программирование табличных моделей для уровней совместимости 1050–1103
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  В табличных моделях реляционные конструкции служат для моделирования данных служб Analysis Services, которые используются в аналитических приложениях и отчетах. Эти модели работают в экземпляре служб Analysis Services, настроенном для табличного режима, с использованием модуля аналитики в памяти для хранения и быстрого просмотра таблиц, при применении которого выполняется статистическая обработка и вычисление данных по запросу.  
  
 Если требованиям пользовательского решения для бизнес-аналитики лучше всего отвечает табличный шаблон базы данных, то для интеграции приложения с табличными моделями в экземпляре служб Analysis Services можно использовать любые клиентские библиотеки и интерфейсы программирования служб Analysis Services. Для запроса к данным табличной модели и вычисления таких данных можно использовать в коде внедренные многомерные выражения или DAX.  
  
 Для табличных моделей, созданных в более ранних версиях служб Analysis Services, в определенной модели на уровнях совместимости 1050 по 1103, являются объекты, работать с программными средствами в объектах AMO, ADOMD.NET, XMLA или OLE DB, принципиально одинаковы для табличных и многомерные решения. В частности метаданные объекта, определенные для многомерных моделей также используется для табличной модели уровней совместимости 1050 – 1103.  
  
 Начиная с SQL Server 2016, табличные модели может быть построен или обновлены до уровня совместимости 1200 или выше, который использует табличные метаданные для определения модели. Метаданные и программирование отличаются фундаментально на этом уровне. См. в разделе [программирование табличных моделей с уровнем совместимости 1200 и выше](../../analysis-services/tabular-model-programming-compatibility-level-1200/tabular-model-programming-for-compatibility-level-1200.md) и [обновление служб Analysis Services](../../database-engine/install-windows/upgrade-analysis-services.md) Дополнительные сведения.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Заметки языка CSDL для бизнес-аналитики (CSDLBI)](https://docs.microsoft.com/bi-reference/csdl/csdl-annotations-for-business-intelligence-csdlbi)  
  
 [Общие сведения о модели табличного объекта на совместимость уровни 1050 по 1103](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
 [Технический справочник по аннотациям бизнес-аналитики для языка CSDL](https://docs.microsoft.com/bi-reference/csdl/technical-reference-for-bi-annotations-to-csdl)  
  

[Интерфейс IMDEmbeddedData](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/imdembeddeddata-interface.md)


  
  
