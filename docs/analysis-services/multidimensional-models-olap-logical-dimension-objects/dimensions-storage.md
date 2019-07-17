---
title: Аналитика хранилища | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3d739bd19cd5be1f9b6167acbf104f569fc517ec
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68209254"
---
# <a name="dimensions---storage"></a>Измерения — хранение
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Измерения в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] поддерживают два режима хранения:  
  
-   Реляционный OLAP (ROLAP)  
  
-   Многомерный OLAP (MOLAP)  
  
 Режим хранения определяет место и форму данных измерения. MOLAP — режим хранения измерений по умолчанию. **См. также:** [режимы хранения и обработки](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md)  
  
## <a name="molap"></a>MOLAP  
 Данные для измерения в режиме MOLAP хранятся в многомерной структуре в экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Эта многомерная структура создается и заполняется при обработке измерения. Измерения MOLAP обеспечивают более высокую производительность, чем измерения ROLAP.  
  
## <a name="rolap"></a>ROLAP  
 Данные для измерения, использующего режим ROLAP, фактически хранятся в таблицах, используемых для определения измерения. Режим хранения ROLAP можно использовать для крупных измерений без дублирования больших объемов данных, однако, это приведет к потере производительности запроса. Измерения основаны непосредственно на таблицах в представлении источника данных, используемого для определения измерения, поэтому режим хранения ROLAP также может поддерживать OLAP реального времени.  
  
> [!IMPORTANT]  
>  Если измерение использует режим хранения ROLAP и при этом входит в состав куба, использующего режим хранения MOLAP, все изменения схемы в исходной таблице должны сопровождаться немедленной обработкой куба. В противном случае может возникнуть несогласованность результатов при запросах к кубу. **См. также:** [автоматизировать административные задачи служб Analysis Services с помощью служб SSIS](../../analysis-services/instances/automate-analysis-services-administrative-tasks-with-ssis.md).  
  
## <a name="see-also"></a>См. также  
 [Режимы хранения и обработка секции](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md)  
  
  
