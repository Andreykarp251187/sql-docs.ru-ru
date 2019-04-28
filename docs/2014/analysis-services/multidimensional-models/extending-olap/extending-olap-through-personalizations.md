---
title: Расширение OLAP через личные настройки | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- Analysis Services, extensibility
ms.assetid: 348e49fc-4390-43c1-9b6c-61b386ff4373
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 74c5b777dda06cf70a6afa2e6384eb2a3587d431
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62725988"
---
# <a name="extending-olap-through-personalizations"></a>Расширение OLAP через личные настройки
  Службы Microsoft [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)] предоставляют множество встроенных функций для использования в языках многомерных выражений (MDX) и расширений интеллектуального анализа данных (DMX). Эти функции спроектированы, чтобы выполнять практически все, от стандартных статистических вычислений до прохода по элементам иерархии. Однако, как и в случае с любым другим сложным и надежным продуктом, возникает необходимость в дальнейшем расширении функциональности такого продукта.  
  
 Поэтому службы Analysis Services предоставляют возможность добавлять сборки и модули персонализации в экземпляр службы, чтобы удовлетворить потребности, не охватываемые стандартной функциональностью.  
  
## <a name="assemblies"></a>Сборки  
 Сборки позволяют расширять бизнес-функции многомерных выражений и расширений интеллектуального анализа данных. Требуемые функции формируются в виде библиотеки, например динамически подключаемой библиотеки (DLL), которая затем добавляется в качестве сборки к экземпляру служб Analysis Services или к базе данных служб Analysis Services. Общие методы в библиотеке затем открываются в виде пользовательских функций для многомерных выражений и выражений расширений интеллектуального анализа данных, их процедур, вычислений, действий и клиентских приложений.  
  
## <a name="personalized-extensions"></a>Модули персонализации  
 Модули персонализации служб SQL Server Analysis Services лежат в основе архитектуры подключаемых модулей. Модули персонализации служб Analysis Services — простое и элегантное изменение существующей архитектуры управляемых сборок. Модули доступны через объектную модель служб Analysis Services <xref:Microsoft.AnalysisServices.AdomdServer>, синтаксис многомерных выражений и наборы строк схемы.  
  
## <a name="see-also"></a>См. также  
 [Управление сборками многомерной модели](../multidimensional-model-assemblies-management.md)   
 [Расширения персонализации служб Analysis Services](analysis-services-personalization-extensions.md)  
  
  
