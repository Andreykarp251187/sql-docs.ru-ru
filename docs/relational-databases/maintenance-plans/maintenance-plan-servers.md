---
title: План обслуживания (серверы) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql13.swb.maint.servers.f1
- sql13.swb.maint.maintplanproperties.server.f1
ms.assetid: ac24d1a8-dd2f-4162-b804-c0df1fc1e61d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: aaad5af180ff1275dc6e95bb1cc5687487a22fb4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68115670"
---
# <a name="maintenance-plan-servers"></a>План обслуживания (серверы)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Диалоговое окно **Серверы** используется для выбора серверов, для которых нужно запустить план обслуживания.  
  
 Многосерверную среду, содержащую один главный сервер и один или несколько целевых серверов, необходимо настроить для создания многосерверного плана обслуживания. В многосерверных планах обслуживания локальный сервер настраивается, как и главный сервер. В многосерверной среде это диалоговое окно отображает главный **(локальный)** сервер и все соответствующие целевые серверы. Для локального сервера создается одно задание агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Оно включается или отключается в зависимости от текущего выбора **(локального)** сервера. Если выбраны целевые серверы, то создается многосерверное задание, которое загружается на выделенные целевые серверы. Если не выбран ни один целевой сервер, многосерверное задание удаляется.  
  
## <a name="see-also"></a>См. также:  
 [Планы обслуживания](../../relational-databases/maintenance-plans/maintenance-plans.md)   
 [Создание многосерверной среды](../../ssms/agent/create-a-multiserver-environment.md)   
 [Создание главного сервера](../../ssms/agent/make-a-master-server.md)   
 [Создание целевого сервера](../../ssms/agent/make-a-target-server.md)  
  
  
