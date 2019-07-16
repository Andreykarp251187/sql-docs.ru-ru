---
title: Определение связей фактов и свойств связей фактов | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2341335d1d9c4904e1832e0a8087c0fa8198fd58
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68178837"
---
# <a name="define-a-fact-relationship-and-fact-relationship-properties"></a>Определение связей фактов и свойств связей фактов
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  При определении нового измерения куба или новой группы мер службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] попытаются определить, существует ли связь измерений фактов, и задать для параметра использования измерения значение **Fact**. Связь измерений фактов можно просмотреть или отредактировать на вкладке **Использование измерений** конструктора кубов. Связь фактов между измерением и группой мер имеет следующие ограничения.  
  
-   Измерение куба может иметь только одну связь фактов с конкретной группой мер.  
  
-   Измерение куба может иметь отдельные связи фактов с несколькими группами мер.  
  
-   Атрибут гранулярности для связи должен быть ключевым атрибутом (таким как номер транзакции) для измерения. Это создает связь «один к одному» между измерением и фактами в таблице фактов.  
  
  
