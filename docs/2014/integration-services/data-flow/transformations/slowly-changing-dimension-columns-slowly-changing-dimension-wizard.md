---
title: Столбцы медленно изменяющихся измерений (мастер медленно изменяющихся измерений) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.loaddimwizard.scdsupport.f1
ms.assetid: 36de99d5-5368-48e0-b876-17e9c6862c6c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: c49f0ce7498215d5758557fba4c67740dca1239e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62770677"
---
# <a name="slowly-changing-dimension-columns-slowly-changing-dimension-wizard"></a>Столбцы медленно меняющихся измерений (мастер медленно изменяющихся измерений)
  Диалоговое окно **Столбцы медленно меняющихся измерений** используется для выбора типа изменения для каждого столбца медленно меняющихся измерений.  
  
 Дополнительные сведения о работе этого мастера см. в разделе [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md).  
  
## <a name="options"></a>Параметры  
 **Столбцы измерений**  
 Выберите столбец измерения из списка.  
  
 **Тип изменения**  
 Выберите пункт **Атрибут неизменности**или один из двух типов изменяющихся атрибутов. Используйте пункт **Атрибут неизменности** , когда значение в столбце не должно изменяться; службы [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] тогда будут воспринимать изменения как ошибки. Используйте **Изменяемый атрибут** для замены существующих значений измененными значениями. Используйте **Атрибут c предысторией** для сохранения измененных значений в новых записях с пометкой предыдущих записей как устаревших.  
  
 **Удалить**  
 Выберите столбец измерения и удалите его из списка сопоставленных столбцов, нажав кнопку **Удалить**.  
  
## <a name="see-also"></a>См. также:  
 [Настройка выходов с помощью мастера медленно изменяющихся измерений](configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
