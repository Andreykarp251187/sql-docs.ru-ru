---
title: LOCALDB_ERROR_TOO_MANY_SHARED_INSTANCES | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: c1595263-6264-4a43-9535-5eb76ece3a57
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9be09d2579e074c1dfc5d34d721f2918f2022112
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63044019"
---
# <a name="localdberrortoomanysharedinstances"></a>LOCALDB_ERROR_TOO_MANY_SHARED_INSTANCES
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|287|  
|Источник события|Среда выполнения локальной базы данных SQL Server 12.0|  
|Компонент|API среды выполнения локальной базы данных|  
|Текст сообщения|Общих экземпляров слишком много, и создать уникальное имя пользовательского экземпляра не удается. Отключите совместный доступ к некоторым из существующих общих экземпляров.|  
  
## <a name="explanation"></a>Объяснение  
 Общих экземпляров слишком много, и создать уникальное имя пользовательского экземпляра не удается.  
  
## <a name="user-action"></a>Действие пользователя  
 Отключите совместный доступ к одному или нескольким общим экземплярам среды выполнения локальной базы данных и повторите попытку.  
  
  
