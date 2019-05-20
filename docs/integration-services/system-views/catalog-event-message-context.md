---
title: catalog.event_message_context | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 273a54f8-b107-4f36-9461-2b475644760d
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: d230b60b204d775e4a5329392960917c28b7c32d
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/16/2019
ms.locfileid: "65715119"
---
# <a name="catalogeventmessagecontext"></a>catalog.event_message_context 

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Отображает сведения об условиях, которые связаны с сообщениями о событиях выполнения, для выполнений на сервере [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|Context_id|BIGINT|Уникальный идентификатор контекста ошибки.|  
|Event_message_id|BIGINT|Уникальный идентификатор сообщения, к которому относится контекст.|  
|Context_depth|ssNoversion|При увеличении глубины контекст оказывается дальше от ошибки. При возникновении ошибки глубина контекста начинается с 1. Значение 0 указывает состояние пакета да начала выполнения.|  
|Package_path|Nvarchar(max)|Путь к пакету для источника контекста.|  
|Context_type|smallint|Тип объекта, который является источником для контекста. Список типов контекста см. в разделе **Примечания**.|  
|Context_source_name|Nvarchar(4000)|Имя объекта, который является источником для контекста.|  
|Context_source_id|Nvarchar(38)|Уникальный идентификатор объекта, который является источником для контекста.|  
|Property_name|Nvarchar(4000)|Имя свойства, связанного с источником контекста.|  
|Property_value|Sql_variant|Значение свойства, связанного с источником контекста.|  
  
## <a name="remarks"></a>Remarks  
 В следующей таблице перечислены типы контекстов.  
  
||||  
|-|-|-|  
|Значение типа контекста|Имя типа|Описание|  
|10|Задача|Состояние задачи при возникновении ошибки.|  
|20|Pipeline|Ошибка компонента конвейера: компонент источника, назначения или преобразования.|  
|30|Последовательность|Состояние последовательности.|  
|40|Цикл For|Состояние цикла For.|  
|50|Цикл Foreach|Состояние цикла Foreach|  
|60|Пакет|Состояние пакета при возникновении ошибки.|  
|70|Переменная|Значение переменной|  
|80|Диспетчер соединений|Свойства диспетчера соединений.|  
  
## <a name="permissions"></a>Разрешения  
 Это представление требует применения одного из следующих разрешений:  
  
-   Разрешение READ по отношению к операции  
  
-   Членство в роли базы данных **ssis_admin**.  
  
-   Членство в роли сервера **sysadmin**.  
  
  
