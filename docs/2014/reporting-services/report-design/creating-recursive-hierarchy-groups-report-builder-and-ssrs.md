---
title: Создание групп рекурсивной иерархии (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 06eccab6-4089-46e8-a84f-5bf3bbe0c23b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 92412bbde8a1032b34264ca254560f31704281e8
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "59946660"
---
# <a name="creating-recursive-hierarchy-groups-report-builder-and-ssrs"></a>Создание групп рекурсивной иерархии (построитель отчетов и службы SSRS)
  Чтобы вывести рекурсивные данные, отражающие связь между родительским и дочерним, представленную полями набора данных, можно задать выражение группы области данных, на основании дочернего поля и установить свойство Parent на основании родительского поля.  
  
 Обычно группы рекурсивной иерархии используются для отображения иерархических данных, например, отношений подчиненных в структуре организации. Набор данных включает в себя список сотрудников и руководителей, причем имена руководителей также перечислены в списке сотрудников.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="creating-recursive-hierarchies"></a>Создание рекурсивных иерархий  
 Чтобы создать рекурсивную иерархию в области данных табликса, нужно задать для поля выражение группы, задающее дочерние данные, а свойству Parent группы присвоить поле, задающее родительские данные. Например, если набор данных содержит идентификатор сотрудника и идентификатор руководителя, нужно присвоить выражению группы идентификатор сотрудника, а свойству Parent — идентификатор руководителя.  
  
 Группа, которая определена как рекурсивная иерархия (то есть группа, которая использует свойство Parent), может иметь только одно выражение группы. Можно использовать функцию `Level` для дополнения текстового поля, чтобы выровнять имена служащих на основе их уровней в иерархии.  
  
 Дополнительные сведения см. в разделах [Добавление или удаление группы в области данных (построитель отчетов и службы SSRS)](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md) и [Создание группы рекурсивной иерархии (построитель отчетов и службы SSRS)](create-a-recursive-hierarchy-group-report-builder-and-ssrs.md).  
  
### <a name="aggregate-functions-that-support-recursion"></a>Агрегатные функции, поддерживающие рекурсию  
 Для вычисления сводных данных в рекурсивных иерархиях можно использовать агрегатные функции служб Reporting Services, принимающие параметр *Recursive* . Следующие функции допускают `Recursive` как параметр: ](report-builder-functions-sum-function.md)Sum[, ](report-builder-functions-avg-function.md)Avg[, ](report-builder-functions-count-function.md)Count[, ](report-builder-functions-countdistinct-function.md)CountDistinct[, ](report-builder-functions-countrows-function.md)CountRows[, ](report-builder-functions-max-function.md)Max[, ](report-builder-functions-min-function.md)Min[, ](report-builder-functions-stdev-function.md)StDev[, ](report-builder-functions-stdevp-function.md)StDevP[, ](report-builder-functions-sum-function.md)Sum[, ](report-builder-functions-var-function.md)Var[ и ](report-builder-functions-varp-function.md)VarP. Дополнительные сведения см. в разделах [Справочник по агрегатным функциям (построитель отчетов и службы SSRS)](report-builder-functions-aggregate-functions-reference.md).  
  
## <a name="see-also"></a>См. также  
 [Таблицы, матрицы и списки (построитель отчетов и службы SSRS)](tables-matrices-and-lists-report-builder-and-ssrs.md)   
 [Область данных табликса (построитель отчетов и службы SSRS)](../tablix-data-region-report-builder-and-ssrs.md)   
 [Справочник по агрегатным функциям (построитель отчетов и службы SSRS)](report-builder-functions-aggregate-functions-reference.md)   
 [Таблицы &#40;построитель отчетов и службы SSRS&#41;](tables-report-builder-and-ssrs.md)   
 [Матрицы &#40;построитель отчетов и службы SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md)   
 [Списки &#40;построитель отчетов и службы SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)   
 [Таблицы, матрицы и списки (построитель отчетов и службы SSRS)](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
