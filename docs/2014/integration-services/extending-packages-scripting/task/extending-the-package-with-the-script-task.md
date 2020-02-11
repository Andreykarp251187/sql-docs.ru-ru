---
title: Расширение пакета с помощью задачи "Скрипт" | Документы Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- scripts [Integration Services]
- SSIS Script task
- tasks [Integration Services], scripts
- Script task [Integration Services], about Script task
- scripts [Integration Services], about Script task with packages
- SSIS Script task, about Script task
ms.assetid: 911e6d26-a6fd-4fc3-a111-bf5f048e9bff
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 10cfa4d5d9deeeeb6bc664fc6480e31bc5dc483e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62894778"
---
# <a name="extending-the-package-with-the-script-task"></a>Расширение пакета с помощью задачи «Скрипт»
  Задача «Скрипт» расширяет возможности [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] времени выполнения пакетов с помощью пользовательского кода, написанного [!INCLUDE[msCoName](../../../includes/msconame-md.md)] на Visual Basic [!INCLUDE[msCoName](../../../includes/msconame-md.md)] или Visual C#, который компилируется и выполняется во время выполнения пакета. Задача «Скрипт» упрощает разработку пользовательской задачи времени выполнения, если задачи, включенные в службы [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], не полностью удовлетворяют требованиям разработчика. Задача «Скрипт» самостоятельно пишет весь инфраструктурный код, давая разработчику возможность сосредоточиться исключительно на коде, необходимом для пользовательской обработки.  
  
 Задача «Скрипт» взаимодействует с пакетом-контейнером через глобальный объект `Dts`, экземпляр класса <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel>, предоставляемого средой скриптов. В задаче «Скрипт» можно писать код, который изменяет значения, хранящиеся в переменных служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]. Позже пакет использует эти обновленные значения для определения рабочего процесса. Задача «Скрипт» может также использовать пространство имен [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)], библиотеку классов платформы [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] и пользовательские сборки для реализации собственной функциональности.  
  
 Задача «Скрипт» и инфраструктурный код, который она создает, значительно упрощают разработку пользовательской задачи. Однако, чтобы понять, как работает задача "Скрипт", будет полезно прочитать раздел [Разработка пользовательской задачи](../../extending-packages-custom-objects/task/developing-a-custom-task.md), чтобы ознакомиться с шагами разработки пользовательской задачи.  
  
 Если создается задача, которую планируется повторно использовать в нескольких пакетах, вместо использования задачи «Скрипт» следует разработать собственную задачу. Дополнительные сведения см. в разделе [Сравнение решений со сценариями и пользовательских объектов](../comparing-scripting-solutions-and-custom-objects.md).  
  
## <a name="in-this-section"></a>в этом разделе  
 В следующих разделах представлены дополнительные сведения о задаче «Скрипт».  
  
 [Настройка задачи «Скрипт» в редакторе задачи «Скрипт»](configuring-the-script-task-in-the-script-task-editor.md)  
 Объясняется, как настроенные в окне **Редактор задачи "скрипт"** свойства влияют на возможности и производительность кода в задаче "Скрипт".  
  
 [Написание кода и отладка задачи «Скрипт»](../../control-flow/script-task.md)  
 Объясняется, как [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] использовать средства для приложений (VSTA) для разработки скриптов, содержащихся в задаче «Скрипт».  
  
 [Использование переменных в задаче «Скрипт»](using-variables-in-the-script-task.md)  
 Объясняется использование переменных с помощью свойства <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A>.  
  
 [Соединение с источниками данных в задаче «Скрипт»](connecting-to-data-sources-in-the-script-task.md)  
 Объясняется использование соединений с помощью свойства <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A>.  
  
 [Вызов событий в задаче «Скрипт»](raising-events-in-the-script-task.md)  
 Объясняется инициирование событий с помощью свойства <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A>.  
  
 [Ведение журнала в задаче «Скрипт»](logging-in-the-script-task.md)  
 Объясняется регистрация сведений с помощью метода <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A>.  
  
 [Возврат результатов из задачи «Скрипт»](returning-results-from-the-script-task.md)  
 Объясняется возвращение результатов через свойства <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A> и <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A>.  
  
 [Примеры задачи «Скрипт»](../../extending-packages-scripting-task-examples/script-task-examples.md)  
 Содержит примеры, в которых показано несколько возможных использований задачи «Скрипт».  
  
![Значок Integration Services (маленький)](../../media/dts-16.gif "Значок служб Integration Services (маленький)")  **следит за обновлениями Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы [!INCLUDE[msCoName](../../../includes/msconame-md.md)], а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетить страницу «Службы Integration Services» на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
## <a name="see-also"></a>См. также:  
 [Задача "Скрипт"](../../control-flow/script-task.md)   
 [Сравнение задачи «Скрипт» и компонента скрипта](../../extending-packages-scripting/comparing-the-script-task-and-the-script-component.md)  
  
  
