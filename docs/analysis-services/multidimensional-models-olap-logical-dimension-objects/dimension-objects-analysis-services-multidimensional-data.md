---
title: Измерение объектов (службы Analysis Services — многомерные данные) | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b296da3faed422aea0da42d01e0a6ece7333e39c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68209273"
---
# <a name="dimension-objects-analysis-services---multidimensional-data"></a>Объекты измерений (службы Analysis Services — многомерные данные)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Простой объект <xref:Microsoft.AnalysisServices.Dimension> состоит из основной информации, атрибутов и иерархий. Основная информация включает имя измерения, тип измерения, источник данных, режим хранения и др. Атрибуты определяют фактические данные в измерении. Атрибуты не обязательно принадлежат к иерархии, но иерархии формируются из атрибутов. В иерархии создаются упорядоченные списки уровней и определяются способы, с помощью которых пользователь может исследовать данное измерение.  
  
## <a name="in-this-section"></a>в этом разделе  
 В следующих разделах приведена дополнительная информация о проектировании и реализации объектов измерения.  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Измерения (службы Analysis Services — многомерные данные)](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)|В [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], измерения являются основными компонентами куба. В измерениях данные привязаны к некоторой предметной области, например заказчики, магазины или служащие.|  
|[Атрибуты и иерархии атрибутов](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)|Измерения — это коллекции атрибутов, которые в представлении источника данных привязаны к одному или нескольким столбцам таблицы или представления.|  
|[Связи атрибутов](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)|В [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], атрибуты измерения всегда связаны прямо или косвенно с ключевым атрибутом. Когда измерение определяется по схеме «звезда», где все атрибуты измерения наследуются из одной реляционной таблицы, то связи между ключевыми и не ключевыми атрибутами определяются автоматически. Когда измерение определяется по схеме «снежинка», где атрибуты измерения наследуются от разных реляционных таблиц, связи атрибутов автоматически определяются следующим образом:<br /><br /> Между ключевым атрибутом и каждым не ключевым атрибутом, привязанным к столбцу главной таблицы измерения.<br /><br /> Между ключевым атрибутом и атрибутами, привязанными к внешнему ключу вспомогательной таблицы, которая связывает таблицы базового измерения.<br /><br /> Между атрибутом, привязанным к внешнему ключу вспомогательной таблицы, и каждым не ключевым атрибутом, привязанным к столбцам вспомогательной таблицы.|  
  
  
