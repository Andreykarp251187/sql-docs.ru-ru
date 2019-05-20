---
title: Приостановка и возобновление общих расписаний | Документы Майкрософт
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: subscriptions
ms.topic: conceptual
helpviewer_keywords:
- pausing schedules
- report-specific schedules [Reporting Services]
- shared schedules [Reporting Services], resuming
- resuming schedules
- continuing schedules
- schedules [Reporting Services], resuming
- schedules [Reporting Services], pausing
ms.assetid: e416be75-5234-4aa6-a3de-77f60f25169a
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 7ec4c97ad3627ae91fd01cf0d8d73a2569a0c41a
ms.sourcegitcommit: dda9a1a7682ade466b8d4f0ca56f3a9ecc1ef44e
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 05/14/2019
ms.locfileid: "65578181"
---
# <a name="pause-and-resume-shared-schedules"></a>Приостановка и возобновление общих расписаний
  Можно приостановить и возобновить общее расписание, используемое в данное время. Приостановка выполнения общего расписания позволяет временно приостановить действие расписания, инициирующего обработку отчетов и подписок. Приостанавливать и возобновлять можно только общие расписания. Расписания конкретных отчетов приостанавливать нельзя.  
  
 Нельзя приостанавливать и возобновлять обработку отчетов, которая выполняется в данный момент. Приостанавливать и возобновлять можно лишь расписания, находящиеся в очереди расписаний службы агента SQL Server. Подсистема расписаний не может управлять выполняемыми заданиями. Дополнительные сведения см. в разделе [Управление запущенным процессом](../../reporting-services/subscriptions/manage-a-running-process.md).  
  
 Пока общее расписание приостановлено, все операции, которые должны были произойти, прекращаются. После возобновления общего расписания обработка отчетов и подписок начнется в следующее указанное в расписании время, при этом используется локальное время сервера отчетов. Сервер отчетов, работающий в собственном режиме, или приложения служб SharePoint не составляют запланированные операции, которые выполнялись бы, если бы расписание не было приостановлено.  
  
 В этом разделе.  
  
-   [Приостановка и возобновление общих расписаний (собственный режим)](#bkmk_native)  
  
-   [Приостановка и возобновление общих расписаний (режим интеграции с SharePoint)](#bkmk_sharepoint)  
  
##  <a name="bkmk_native"></a> Приостановка и возобновление общих расписаний (собственный режим)  
 Чтобы приостанавливать и возобновлять выполнение общих расписаний, используйте страницу «Общие расписания» диспетчера отчетов. В среде [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]это невозможно, она не предоставляет возможность приостанавливать и возобновлять выполнение расписаний. Дополнительные сведения см. в статье [Create, Modify, and Delete Schedules](../../reporting-services/subscriptions/create-modify-and-delete-schedules.md).  
  
#### <a name="to-pause-or-resume-a-shared-schedule"></a>Остановка и возобновление общего расписания  
  
1.  В диспетчере отчетов щелкните **Параметры сайта**.  
  
2.  Нажмите кнопку **Расписания**.  
  
3.  Выберите расписание и на ленте нажмите кнопку **Приостановить** или **Возобновить** . Если в настоящее время расписание приостановлено, то в столбце **Состояние** будет указано **Приостановлено**.  
  
##  <a name="bkmk_sharepoint"></a> Приостановка и возобновление общих расписаний (режим интеграции с SharePoint)  
 Для приостановки и возобновление общего расписания используется страница «Параметры сайта» или PowerShell. Управление расписаниями выполняется для каждого сайта SharePoint отдельно.  
  
#### <a name="to-pause-or-resume-a-shared-schedule"></a>Остановка и возобновление общего расписания  
  
1.  Щелкните **Действия сайта**.  
  
2.  Щелкните элемент **Настройки сайта**.  
  
3.  В разделе служб Reporting Services щелкните **Управление общими расписаниями**.  
  
4.  Выберите расписание, затем нажмите кнопку **Приостановить выбранные расписания** или **Запустить выбранные расписания**. Если в настоящее время расписание приостановлено, то в столбце **Состояние** будет указано **Приостановлено**.  
  
## <a name="see-also"></a>См. также:  
 [Расписания](../../reporting-services/subscriptions/schedules.md)   
 [Create, Modify, and Delete Schedules](../../reporting-services/subscriptions/create-modify-and-delete-schedules.md)   
 [Изменение часовых поясов и настроек часов на сервере отчетов](../../reporting-services/subscriptions/change-time-zones-and-clock-settings-on-a-report-server.md)   
 [Управление запущенным процессом](../../reporting-services/subscriptions/manage-a-running-process.md)  
  
  
