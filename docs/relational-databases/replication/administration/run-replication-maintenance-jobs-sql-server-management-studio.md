---
title: Запуск заданий по обслуживанию репликации (SQL Server Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server replication]
ms.assetid: 0dc485a0-5a50-41eb-a29d-f2b2fb920174
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: e7d5764e3cfdaf88ebfa23cedd61884f3c4f347e
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2019
ms.locfileid: "68768772"
---
# <a name="run-replication-maintenance-jobs-sql-server-management-studio"></a>запустить задания по обслуживанию репликаций (среда SQL Server Management Studio)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Репликация использует следующие задания по обслуживанию:  
  
-   **Повторная инициализация подписок, имеющих сбои при выполнении проверки данных**  
  
-   **Очистка журнала агента: распределение**  
  
-   **Обновитель монитора репликацией для распространителя**  
  
-   **Контроль за агентами репликации**  
  
-   **Очистка распространения: распространение**  
  
-   **Очистка истекшей подписки**  
  
 Запустить и остановить эти задания можно из папки **Задания** в среде [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] и на вкладке **Агенты** монитора репликации. Сведения о запуске монитора репликации см. в [этой статье](../../../relational-databases/replication/monitor/start-the-replication-monitor.md). Просмотр и изменение свойств каждого задания осуществляется в диалоговом окне **Свойства задания — \<задание>** , доступном в той же папке и на той же вкладке.  
  
### <a name="to-start-or-stop-a-replication-maintenance-job-in-management-studio"></a>Запуск или остановка задания по обслуживанию репликации в среде Management Studio  
  
1.  Подключитесь к распространителю в [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]и разверните узел сервера.  
  
2.  Раскройте папку **Агент SQL Server** , а затем — папку **Задания** .  
  
3.  Щелкните правой кнопкой мыши задание, а затем щелкните **Запустить задание** или **Остановить задание**.  
  
### <a name="to-start-or-stop-a-replication-maintenance-job-in-replication-monitor"></a>Запуск или остановка задания по обслуживанию репликации в мониторе репликации  
  
1.  В мониторе репликации раскройте группу издателей и выберите в ней издателя.  
  
2.  Перейдите на вкладку **Агенты** .  
  
3.  Щелкните правой кнопкой мыши задание в сетке, а затем щелкните **Запустить задание** или **Остановить задание**.  
  
### <a name="to-view-and-modify-properties-for-a-replication-maintenance-job-in-management-studio"></a>Просмотр и изменение свойств задания по обслуживанию репликации в среде Management Studio  
  
1.  Подключитесь к распространителю в [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]и разверните узел сервера.  
  
2.  Раскройте папку **Агент SQL Server** , а затем — папку **Задания** .  
  
3.  Правой кнопкой мыши щелкните задание и выберите **Свойства**.  
  
4.  В диалоговом окне **Свойства задания — \<задание>** измените любые свойства по необходимости, а затем нажмите кнопку **ОК**.  
  
### <a name="to-view-and-modify-properties-for-a-replication-maintenance-job-in-replication-monitor"></a>Просмотр и изменение свойств задания по обслуживанию репликации в мониторе репликации  
  
1.  В мониторе репликации раскройте группу издателей и выберите в ней издателя.  
  
2.  Перейдите на вкладку **Агенты** .  
  
3.  Щелкните правой кнопкой мыши задание в сетке, а затем щелкните **Свойства**.  
  
4.  В диалоговом окне **Свойства задания — \<задание>** измените любые свойства по необходимости, а затем нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также:  
 [Запуск и остановка агента репликации (среда SQL Server Management Studio)](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)   
 [Просмотр сведений и выполнение задач для издателя (монитор репликации)](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-replication-monitor.md)   
 [Администрирование агента репликации](../../../relational-databases/replication/agents/replication-agent-administration.md)  
  
  
