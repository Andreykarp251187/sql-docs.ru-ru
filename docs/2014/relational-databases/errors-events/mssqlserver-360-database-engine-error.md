---
title: MSSQLSERVER_360 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 360 (Database Engine error)
ms.assetid: e2b7c1b2-3679-4206-9b25-6bd55ef96a2c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: bc46a5cf1252df209243623a63ec9bdc68e71873
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62867959"
---
# <a name="mssqlserver360"></a>MSSQLSERVER_360
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|360|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DML_UPDATE_SPARSE_AND_COLSET|  
|Текст сообщения|Список целевых столбцов для инструкций INSERT, UPDATE или MERGE не может содержать одновременно разреженный столбец и набор столбцов, в состав которого входит разреженный столбец. Перепишите запрос таким образом, чтобы список целевых столбцов содержал либо разреженный столбец, либо набор столбцов, но не то и другое сразу.|  
  
## <a name="explanation"></a>Объяснение  
Набор столбцов представляет собой нетипизированное XML-представление, объединяющее несколько столбцов таблицы в виде структурированного вывода. Была предпринята попытка изменить набор столбцов и столбец, являющийся частью набора столбцов, в результате чего были созданы две ссылки на один и тот же столбец.  
  
## <a name="user-action"></a>Действие пользователя  
Перепишите инструкцию таким образом, чтобы в ней содержалась ссылка либо на столбец, либо на набор столбцов, но не на то и другое одновременно.  
  
