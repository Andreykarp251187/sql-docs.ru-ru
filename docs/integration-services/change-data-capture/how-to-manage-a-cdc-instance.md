---
title: Управление экземпляром CDC | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5d9e677f-b872-497d-9cde-472184a214ab
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 5fd3788cb31e7e3e6408cc7161f45ba008cf081c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65728780"
---
# <a name="how-to-manage-a-cdc-instance"></a>How to Manage a CDC Instance

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Эта процедура описывает управление операциями экземпляра CDC во время выполнения с помощью консоли конструктора CDC.  
  
### <a name="to-manage-cdc-instance-operations"></a>Управление операциями экземпляра CDC  
  
1.  В меню **Пуск** выберите **Консоль конструктора CDC**.  
  
2.  На панели слева разверните узел **Отслеживание измененных данных** , а затем разверните службу, содержащую экземпляр, данные которого необходимо просмотреть.  
  
3.  Выберите имя нужного экземпляра.  
  
4.  На панели **Действия** справа в консоли конструктора CDC щелкните операцию, которую нужно выполнить.  
  
     Можно также щелкнуть имя экземпляра на левой панели и выбрать операцию, которую необходимо выполнить.  
  
     Можно выполнить следующие задачи:  
  
    -   **Запуск**. Начать отслеживание изменений.  
  
    -   **Остановка**. Остановить отслеживание изменений.  
  
    -   **Сброс**. Нажмите кнопку **Сброс** , чтобы перевести экземпляр CDC в первоначальное (пустое) состояние. Этот параметр доступен только тогда, когда экземпляр CDC остановлен. Все изменения в таблицах изменений, а также внутреннее состояние экземпляра CDC будут удалены. При последующем запуске экземпляра CDC отслеживание изменений начнется с этого момента и будет содержать только те транзакции, выполнение которых началось после запуска экземпляра CDC.  
  
    -   **Удалить**. Удалить экземпляр CDC.  
  
    -   **Скрипт журналирования Oracle**. Щелкните **Oracle Logging Script** (Скрипт журналирования Oracle), чтобы открыть диалоговое окно со вспомогательным скриптом журналирования Oracle. Сведения о том, что можно сделать в этом диалоговом окне, см. в разделе [Oracle Supplemental Logging Script](../../integration-services/change-data-capture/oracle-supplemental-logging-script.md).  
  
         **Примечание.** При выполнении скриптов дополнительного журналирования открывается диалоговое окно «Учетные данные Oracle для выполнения скриптов», в которое необходимо ввести допустимые имя пользователя Oracle и пароль. Сведения об указании надлежащих учетных данных Oracle см. в разделе [Oracle Credentials for Running Script](../../integration-services/change-data-capture/oracle-credentials-for-running-script.md).  
  
    -   **Развертывание экземпляра CDC**. Создать скрипт развертывания для экземпляра CDC. Сведения об этом диалоговом окне см. в разделе [CDC Instance Deployment Script](../../integration-services/change-data-capture/cdc-instance-deployment-script.md).  
  
     Дополнительные сведения об этих задачах см. в разделе [Manage a CDC Instance](../../integration-services/change-data-capture/manage-a-cdc-instance.md).  
  
 Можно также выбрать **Свойства** , чтобы изменить свойства конфигурации экземпляра CDC. Дополнительные сведения об изменении свойств экземпляра CDC см. в разделе [Edit Instance Properties](../../integration-services/change-data-capture/edit-instance-properties.md).  
  
  
