---
title: Параметр конфигурации сервера "SMO and DMO XPs" | Документы Майкрософт
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: bcd945ba-5d81-4124-9a2b-d87491c2a369
author: MikeRayMSFT
ms.author: mikeray
manager: jroth
ms.openlocfilehash: 7c0f82a57cdbc9117e28e03b65a070055831ef13
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66775581"
---
# <a name="smo-and-dmo-xps-server-configuration-option"></a>Параметр конфигурации сервера «SMO and DMO XPs»
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  С помощью параметра «SMO and DMO XPs» включите расширенные хранимые процедуры управляющих объектов (SMO) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на этом сервере.  
  
 Обратите внимание, что, начиная с версии [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], объекты DMO были удалены из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Возможные значения описаны в следующей таблице:  
  
|Значение|Значение|  
|-----------|-------------|  
|0|Расширенные хранимые процедуры объектов SMO недоступны.|  
|1|Расширенные хранимые процедуры объектов SMO доступны. Это значение по умолчанию.|  
  
 Изменение этой настройки вступает в силу немедленно.  
  
## <a name="examples"></a>Примеры  
 В следующем примере активируются расширенные хранимые процедуры объектов SMO.  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'SMO and DMO XPs', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Учебник по программированию управляющих объектов SQL Server (SMO)](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
  
