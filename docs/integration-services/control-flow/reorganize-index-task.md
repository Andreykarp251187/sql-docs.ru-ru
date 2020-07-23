---
title: Задача "Реорганизация индекса" | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.reorganizeindextask.f1
helpviewer_keywords:
- reorganizing indexes
- Reorganize Index task [Integration Services]
- indexes [Integration Services]
ms.assetid: 9ed87861-e5c3-4fcd-8760-d112f4c0af0c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 74e3b6d54dfddc976080a5a530d89905524887bc
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86921170"
---
# <a name="reorganize-index-task"></a>Задача «Реорганизация индекса»

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Задача «Реорганизация индекса» перестраивает индексы в таблицах и представлениях базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения об управлении индексами см. в разделе [Реорганизация и перестроение индексов](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md).  
  
 Используя задачу «Реорганизация индекса», пакет может перестроить индексы в одной или нескольких базах данных. Если задача перестраивает индексы только одной базы данных, можно выбрать представления или таблицы, чьи индексы будут реорганизованы. Задача «Реорганизация индекса» также содержит параметр сжатия больших объектов данных. Большой объект данных — это данные, содержащие значение типа данных **image**, **text**, **ntext**, **varchar(max)** , **nvarchar(max)** , **varbinary(max)** или **xml** . Дополнительные сведения см. в разделе [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md).  
  
 Задача «Реорганизация индекса» содержит инструкцию Transact-SQL ALTER INDEX. Если необходимо сжать большой объект данных, инструкция использует предложение REORGANIZE WITH (LOB_COMPACTION = ON), иначе значение LOB_COMPACTION устанавливается в OFF. Дополнительные сведения см. в разделе [ALTER INDEX (Transact-SQL)](../../t-sql/statements/alter-index-transact-sql.md).  
  
> [!IMPORTANT]  
>  Время, необходимое на создание инструкции Transact-SQL, которая будет выполнена задачей, пропорционально количеству индексов, которые необходимо перестроить. Если задача настроена на перестроение всех таблиц и представлений базы данных, которая содержит большое количество индексов, или нужно перестроить индексы нескольких баз данных, то создание инструкции Transact-SQL может занять значительное время.  
  
## <a name="configuration-of-the-reorganize-index-task"></a>Настройка задачи «Реорганизация индекса»  
 Свойства задаются с помощью конструктора служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] . Эта задача находится в разделе **Задачи плана обслуживания** **области элементов** в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в следующих разделах:  
  
-   [Задача "Реорганизация индекса" (план обслуживания)](../../relational-databases/maintenance-plans/reorganize-index-task-maintenance-plan.md)  
  
## <a name="related-tasks"></a>Связанные задачи  
 Дополнительные сведения о настройке свойств этих свойств в конструкторе [!INCLUDE[ssIS](../../includes/ssis-md.md)] см. в разделе [Задание свойств задач или контейнеров](https://msdn.microsoft.com/library/52d47ca4-fb8c-493d-8b2b-48bb269f859b).  
  
## <a name="see-also"></a>См. также:  
 [Задачи служб Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Поток управления](../../integration-services/control-flow/control-flow.md)  
  
  
