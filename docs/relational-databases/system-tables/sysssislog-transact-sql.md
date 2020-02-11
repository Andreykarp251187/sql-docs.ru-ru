---
title: sysssislog (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdtslog90_TSQL
- sysdtslog90
dev_langs:
- TSQL
helpviewer_keywords:
- sysssislog system table
ms.assetid: 7fa288a1-81e3-42a0-82f6-8a59019693d0
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d837049f36e4f7925f8e62a18987f51235f19c14
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68029608"
---
# <a name="sysssislog-transact-sql"></a>sysssislog (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждой записи журнала, сформированной пакетами или их задачами и контейнерами во время выполнения. Эта таблица создается в базе данных msdb при установке [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Если ведение журнала настроено таким образом, что записи вносятся в журнал другой базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то в указанной базе данных создается таблица sysssislog следующего формата.  
  
> [!NOTE]  
>  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]записывает записи журнала в эту таблицу **только** в том случае [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , если пакеты используют регистратор.  
  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|id|**int**|Уникальный идентификатор для записи журнала.|  
|event|**имеет sysname**|Имя события, которое сформировало запись журнала.|  
|computer|**nvarchar**|Компьютер, на котором был запущен пакет, когда была сформирована запись журнала.|  
|оператор|**nvarchar**|Имя пользователя сотрудника, запустившего пакет, который сформировал запись журнала.|  
|источник|**nvarchar**|Имя исполняемого объекта в пакете, который сформировал запись журнала.|  
|sourceid|**UNIQUEIDENTIFIER**|Идентификатор GUID исполняемого объекта в пакете, который сформировал запись журнала.|  
|executionid|**UNIQUEIDENTIFIER**|Идентификатор GUID экземпляра выполнения исполняемого объекта, который сформировал запись журнала.|  
|время начала|**datetime**|Время начала выполнения пакета.|  
|endtime|**datetime**|Время завершения выполнения пакета.<br /><br /> Эта функция не реализована. Значение в столбце endtime всегда равно значению в столбце starttime.|  
|datacode|**int**|Необязательное целочисленное значение, которое обычно указывает на результат выполнения контейнера или задачи.|  
|databytes|**Эскиз**|Необязательный байтовый массив для хранения дополнительной информации.|  
|Message|**nvarchar**|Описание события и сведения, связанные с событием.|  
  
## <a name="see-also"></a>См. также:  
 [Ведение журнала&#41; Integration Services &#40;SSIS](../../integration-services/performance/integration-services-ssis-logging.md)   
  
  
