---
title: MSSQLSERVER_ 10536 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10536 (Database Engine error)
ms.assetid: 9f97b41f-0ef8-4ad2-aec0-906a5d7522ba
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0ace2712cd53b1b0371bd9deeb4191308a1393de
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68060651"
---
# <a name="mssqlserver10536"></a>MSSQLSERVER_10536
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|10536|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|PG_TOO_MANY_STMTS|  
|Текст сообщения|Не удалось создать структуру плана "%.\*ls", поскольку пакет или модуль, соответствующий указанному параметру **@plan_handle** , содержит более 1000 подходящих инструкций. Создайте структуру плана для каждой инструкции в пакете или модуле, указав для каждой инструкции значение **statement_start_offset**.|  
  
## <a name="explanation"></a>Объяснение  
Пакет или модуль, соответствующий указанному дескриптору **@plan_handle** , содержит больше 1000 подходящих инструкций.  
  
## <a name="user-action"></a>Действие пользователя  
Создайте структуру плана для каждой инструкции в пакете или модуле, указав для каждой инструкции значение **statement_start_offset**.  
  
## <a name="see-also"></a>См. также:  
[sp_create_plan_guide (Transact-SQL)](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[Руководства планов](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide_from_handle (Transact-SQL)](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
