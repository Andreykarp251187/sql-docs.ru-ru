---
title: Редактор задачи «очередь сообщений» (страница «Общие») | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.msgqueuetask.general.f1
helpviewer_keywords:
- Message Queue Task Editor
ms.assetid: 09368b18-37a5-4321-a173-7cfe5d42d2a2
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 25053ac966629c1265d735df8502eccad1d8a290
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84950934"
---
# <a name="message-queue-task-editor-general-page"></a>Редактор задачи «Очередь сообщений» (страница «Общие»)
  **Страница «Общие»** диалогового окна **Редактор задачи «Очередь сообщений»** позволяет задавать имя и описывать задачу «Очередь сообщений», определять формат сообщений, а также указывать, будет ли задача отправлять или получать сообщения.  
  
 Дополнительные сведения об этой задаче см. в разделе [Message Queue Task](control-flow/message-queue-task.md).  
  
## <a name="options"></a>Параметры  
 **имя**;  
 Задайте уникальное имя задаче «Очередь сообщений». Это имя используется в качестве метки для значка задачи.  
  
> [!NOTE]  
>  Имена задач в пределах пакета должны быть уникальными.  
  
 **Описание**  
 Введите описание задачи «Очередь сообщений».  
  
 **Use2000Format**  
 Укажите, нужно ли использовать формат 2000 службы очередей сообщений (MSMQ). Значение по умолчанию — `False`.  
  
 **MSMQConnection**  
 Выберите существующий диспетчер подключений MSMQ или щелкните \<**New connection...**> , чтобы создать новый диспетчер соединений.  
  
 **См. также**: [Диспетчер FTP-соединений](connection-manager/msmq-connection-manager.md), [Редактор диспетчера FTP-соединений](../../2014/integration-services/msmq-connection-manager-editor.md)  
  
 **Message**  
 Указывает, будет ли задача «Очередь сообщений» отправлять или получать сообщения. При выборе режима **Отправить сообщение**на левой панели диалогового окна появляется страница «Отправка», при выборе режима **Получить сообщение**появляется страница «Получение». По умолчанию, устанавливается режим **Отправить сообщение**.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по ошибкам и сообщениям Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор задачи "очередь сообщений" &#40;"получить страницу"&#41;](../../2014/integration-services/message-queue-task-editor-receive-page.md)   
 [Редактор задачи "очередь сообщений" &#40;"Отправить страницу"&#41;](../../2014/integration-services/message-queue-task-editor-send-page.md)   
 [Страница «Выражения»](expressions/expressions-page.md)  
  
  
