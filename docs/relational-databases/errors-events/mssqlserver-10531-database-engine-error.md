---
description: MSSQLSERVER_10531
title: MSSQLSERVER_10531 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10531 (Database Engine error)
ms.assetid: bb40e994-231c-44ce-933f-8d767fb2f450
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c8e91f999a9a7526e0419f49e06cdc4710d8db92
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88338588"
---
# <a name="mssqlserver_10531"></a>MSSQLSERVER_10531
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|10531|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|PG_NO_ELIGIBLE_STMT|  
|Текст сообщения|Не удалось создать структуру плана «%.*ls» из кэша, поскольку пользователь не имеет необходимых разрешений. Предоставьте разрешение VIEW SERVER STATE пользователю, создающему структуру плана.|  
  
## <a name="explanation"></a>Объяснение  
Пользователь не имеет разрешений, необходимых для создания указанной структуры плана из кэша планов.  
  
## <a name="user-action"></a>Действие пользователя  
Предоставьте разрешение VIEW SERVER STATE пользователю, создающему структуру плана.  
  
## <a name="see-also"></a>См. также:  
[Руководства планов](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide (Transact-SQL)](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[sp_create_plan_guide_from_handle (Transact-SQL)](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
