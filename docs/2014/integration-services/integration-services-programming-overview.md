---
title: Общие сведения о программировании служб Integration Services | Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Integration Services, programming
- architecture [Integration Services]
- assemblies [Integration Services]
- SSIS, programming
- SQL Server Integration Services, programming
- run-time engine [Integration Services]
- packages [Integration Services], programming
- data flow engine [Integration Services]
- languages [Integration Services]
ms.assetid: 262babc6-eea5-4609-bc65-07d64cbcfee9
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: e9bb972afddfe5275f5995870b18038b683236ff
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62892721"
---
# <a name="integration-services-programming-overview"></a>Общие сведения о программировании служб Integration Services
  Архитектура служб [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] отделяет перемещение и преобразование данных от потока управления пакета. Существует два отдельных ядра, определяющих эту архитектуру. При создании программ для служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] их функции можно автоматизировать и расширить. Подсистема выполнения реализует поток управления и инфраструктуру управления пакетами, которые позволяют разработчикам контролировать поток выполнения и задавать параметры журналов, обработчиков событий и переменных. Подсистема обработки потока данных представляет собой специализированное высокопроизводительное ядро, предназначенное для извлечения, преобразования и загрузки данных. При создании программ для служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] необходимо использовать возможности этих двух подсистем.  
  
 На следующей иллюстрации изображена архитектура служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
 ![Архитектура служб Integration Services](media/mw-dts-01.gif "Архитектура служб Integration Services")  
  
## <a name="integration-services-run-time-engine"></a>Подсистема выполнения служб Integration Services  
 Подсистема выполнения служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] контролирует управление пакетами и их выполнение, реализуя инфраструктуру, которая позволяет определить порядок выполнения, журналы, переменные и обработчики событий. Программирование подсистемы выполнения служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] дает разработчикам возможность автоматизировать создание, настройку и выполнение пакетов, а также решение специальных задач и реализацию других расширений.  
  
 Дополнительные сведения см. в разделах [Расширение пакета с помощью задачи "Скрипт"](extending-packages-scripting/task/extending-the-package-with-the-script-task.md), [Разработка пользовательской задачи](extending-packages-custom-objects/task/developing-a-custom-task.md) и [Программная сборка пакетов](building-packages-programmatically/building-packages-programmatically.md).  
  
## <a name="integration-services-data-flow-engine"></a>Подсистема обработки потока данных служб Integration Services  
 Подсистема обработки потока данных управляет задачей потока данных, представляющей собой специализированную высокопроизводительную задачу, предназначенную для перемещения и преобразования данных из несовместимых источников. В отличие от других задач, задача потока данных содержит дополнительные объекты, которые называются компонентами потока данных. Это могут быть источники, преобразования и назначения. Такие компоненты составляют основную движущую силу задачи. Они определяют перемещение и преобразование данных. Программирование подсистемы обработки потока данных позволяет разработчикам автоматизировать создание и настройку компонентов задачи потока данных и создание пользовательских компонентов.  
  
 Дополнительные сведения см. в разделе [расширение потока данных с помощью компонента скрипта] (extending-packages-scripting/data-flow-скрипт-component/extending--данных-flow-with--скрипт-component.md, [Разработка пользовательского компонента потока данных ](extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md), и [программное построение пакетов](building-packages-programmatically/building-packages-programmatically.md).  
  
## <a name="supported-languages"></a>Поддерживаемые языки  
 Службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] полностью поддерживают платформу [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Это позволяет разработчикам программировать для служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] на том .NET-совместимом языке, который они предпочитают. Несмотря на то, что как подсистема выполнения, так и подсистема обработки потока данных написаны на машинном коде, они доступны через полностью управляемую модель объектов.  
  
 Пакеты [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], пользовательские задачи и компоненты можно программировать в [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] или другом текстовом редакторе или редакторе кода. Среда [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] предлагает разработчику множество средств и функций, упрощающих и ускоряющих итерационные циклы создания кода, отладки и тестирования. Среда [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] также упрощает процесс развертывания. Тем не менее наличие [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] не является обязательным условием для компиляции и сборки программных проектов для служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Пакет SDK для платформы [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] включает компиляторы [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] и [!INCLUDE[csprcs](../includes/csprcs-md.md)], а также связанные средства.  
  
> [!IMPORTANT]  
>  По умолчанию с [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] устанавливается платформа [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], но не устанавливается пакет SDK для платформы [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Если пакет SDK не установлен на компьютере, а в коллекцию электронной документации не входит документация по пакету SDK, ссылки на содержимое пакета SDK в этом разделе работать не будут. После установки пакета SDK для платформы [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] можно добавить документацию по пакету SDK в коллекцию электронной документации и в оглавление, выполнив инструкции из раздела [Добавление или удаление документации по продукту SQL Server](../2014-toc/books-online-for-sql-server-2014.md).  
  
 Задача "Скрипт" и компонент "Скрипт" служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] используют набор средств [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tools для работы с приложениями (VSTA) в качестве внедренной среды создания скриптов. Средства VSTA поддерживают работу с языками [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Basic и [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual C#.  
  
> [!NOTE]  
>  Прикладные программные интерфейсы служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] несовместимы с языками скриптов на основе COM, такими как VBScript.  
  
## <a name="locating-assemblies"></a>Поиск сборок  
 В [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]сборки служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] были обновлены до .NET 4.0. Существует отдельный глобальный кэш сборок для .NET 4, который находится в следующем расположении: *\<диск>* :\Windows\Microsoft.NET\assembly. Там вы можете найти все сборки [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , обычно в папке GAC_MSIL.  
  
 Как и в предыдущих версиях [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], путь к основным DLL-файлам расширения [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] имеет вид: *\<диск>* :\Program Files\Microsoft SQL Server\100\SDK\Assemblies.  
  
## <a name="commonly-used-assemblies"></a>Сборки общего назначения  
 В следующей таблице перечислены сборки, часто используемые при программировании для служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] с использованием [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
|Сборка|Описание|  
|--------------|-----------------|  
|Microsoft.SqlServer.ManagedDTS.dll|Содержит управляемую подсистему выполнения.|  
|Microsoft.SqlServer.RuntimeWrapper.dll|Содержит основную сборку (оболочку) взаимодействия (PIA) для собственной подсистемы выполнения.|  
|Microsoft.SqlServer.PipelineHost.dll|Содержит управляемую подсистему обработки потока данных.|  
|Microsoft.SqlServer.PipelineWrapper.dll|Содержит основную сборку (оболочку) взаимодействия (PIA) для собственной подсистемы обработки потока данных.|  

![Значок служб Integration Services (маленький)](media/dts-16.gif "значок служб Integration Services (маленький)")**оставаться до даты со службами Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетите страницу служб Integration Services на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
  
