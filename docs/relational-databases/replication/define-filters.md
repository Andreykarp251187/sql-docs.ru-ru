---
description: Определение фильтров
title: Определение фильтров | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.replconflictviewer.definefilters.f1
helpviewer_keywords:
- Define Filters dialog box
ms.assetid: 1fa71d22-ce5a-4aae-ba05-4d755842aeac
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e4834e78ec82a681faba9f6c0fa780d78f890def
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88498792"
---
# <a name="define-filters"></a>Определение фильтров
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
   Диалоговое окно **Определение фильтров** позволяет определять фильтры, применяемые к конфликтам данных для просмотра подмножества этих конфликтов в данной сетке. Чтобы определить фильтр, выберите оператор из раскрывающегося списка **Оператор** , а затем введите значение. Например, чтобы просмотреть только те конфликты, в которых проигравшей стороной является сервер **ReplTest1**, выберите **Равно** из раскрывающегося списка **Оператор** и введите **ReplTest1** в первом столбце **Значение** .  
  
## <a name="options"></a>Параметры  
 **Оператор**  
 Выберите оператор для фильтра, например **Меньше**или Равно.
  
 **Значение**  
 Введите значение для фильтра. Для большинства операторов нужно только значение в первом столбце **Значение** , но для операторов **Между** и **Вне** необходимы значения в обоих столбцах **Значение** .  
  
 **Clear**  
 Нажмите эту кнопку для сброса всех ранее определенных фильтров.  
  
## <a name="see-also"></a>См. также:  
 [Средство просмотра конфликтов репликации (Майкрософт) (репликация слиянием)](../../relational-databases/replication/microsoft-replication-conflict-viewer-merge-replication.md)   
 [Средство просмотра конфликтов репликации (Майкрософт) (репликация транзакций)](../../relational-databases/replication/microsoft-replication-conflict-viewer-transactional-replication.md)  
  
  
