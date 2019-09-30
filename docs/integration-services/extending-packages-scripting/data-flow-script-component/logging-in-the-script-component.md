---
title: Ведение журнала в компоненте скрипта | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Script component [Integration Services], logging
ms.assetid: 17c19787-379e-43fe-9107-e36e17ecda53
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 52f4c841d2022216480051576bb0b6da7bdb5d34
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2019
ms.locfileid: "71286462"
---
# <a name="logging-in-the-script-component"></a>Ведение журнала в компоненте скрипта

[!INCLUDE[ssis-appliesto](../../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Ведение журнала в пакетах служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] позволяет сохранить подробные сведения о процессе выполнения, результатах и проблемах, записывая стандартные события или определенные пользователем сообщения с целью последующего анализа. Компонент скрипта может использовать метод <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> класса **ScriptMain** для записи определяемых пользователем данных. Если ведение журнала включено и событие **ScriptComponentLogEntry** выбрано для записи на вкладке **Подробности** диалогового окна **Настройка журналов служб SSIS**, единичный вызов метода <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> сохраняет сведения о событии во всех поставщиках журналов, настроенных для задачи потока данных.  
  
 Далее приведен простой пример ведения журнала.  
  
 `Dim bt(0) As Byte`  
  
 `Me.Log("Test Log Event", _`  
  
 `0, _`  
  
 `bt)`  
  
> [!NOTE]  
>  Хотя журнал можно вести непосредственно из компонента скрипта, может потребоваться реализовать события, а не журнал. При использовании событий кто угодно может включить запись сообщений о событиях в журнал, но можно использовать для отклика на события стандартные или определяемые пользователем обработчики событий.  
  
 Дополнительные сведения о ведении журналов см. в разделе [Ведение журналов в службах Integration Services (SSIS)](../../../integration-services/performance/integration-services-ssis-logging.md).  
  
## <a name="see-also"></a>См. также:  
 [Ведение журналов в службах Integration Services (SSIS)](../../../integration-services/performance/integration-services-ssis-logging.md)  
  
  
