---
title: Диспетчер подключений MSMQ | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], message queues
- connection managers [Integration Services], MSMQ
- MSMQ connection manager
- message queue connections [Integration Services]
ms.assetid: a86900e2-450e-479f-b207-e1b02361d395
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 78377fe5eaf5b9f0639533f17fa7a45cca69a537
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62833663"
---
# <a name="msmq-connection-manager"></a>диспетчер соединений MSMQ
  Диспетчер соединений MSMQ позволяет пакетам соединяться с очередями сообщений, которые используют службу очередей сообщений (также называемую MSMQ). Задача «Очередь сообщений», содержащаяся в службах [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , использует диспетчер соединений MSMQ.  
  
 При добавлении к пакету диспетчера MSMQ-сеансов службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] создают диспетчер соединений, который будет решать задачи MSMQ-сеансов во время работы, устанавливает свойства диспетчера соединений и добавляет его к коллекции пакета `Connections`. Свойству `ConnectionManagerType` диспетчера соединений присваивается значение `MSMQ`.  
  
 Настроить диспетчер соединений MSMQ можно следующими способами.  
  
-   Указать строку соединения.  
  
-   Указать путь к очереди сообщений для подключения.  
  
 Формат пути зависит от типа очереди, как показано в следующей таблице.  
  
|Тип очереди|Образец пути|  
|----------------|-----------------|  
|Открытый|\<имя компьютера>\\<имя очереди\>|  
|Private|\<имя компьютера>\Private$\\<имя очереди\>|  
  
 Для представления локального компьютера можно использовать знак точки («.»).  
  
## <a name="configuration-of-the-msmq-connection-manager"></a>Настройка диспетчера соединений MSMQ  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно задавать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в статье [Редактор диспетчера MSMQ-сеансов](../msmq-connection-manager-editor.md).  
  
 Дополнительные сведения о программной настройке диспетчера подключений см. в разделах <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> и [Добавление соединений программным образом](../building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="see-also"></a>См. также  
 [Задача «Очередь сообщений»](../control-flow/message-queue-task.md)   
 [Соединения в службах Integration Services (SSIS)](integration-services-ssis-connections.md)  
  
  
