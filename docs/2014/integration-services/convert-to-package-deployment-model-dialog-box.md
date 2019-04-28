---
title: Преобразовать в пакет развертывания модели диалоговое окно | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.bids.converttolegacydeployment.f1
ms.assetid: 9e60a34a-10f7-48d1-966f-b3ff236ab4b7
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 88a8d26716ed0945488fdd24ce1e19d3877e049f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62829330"
---
# <a name="convert-to-package-deployment-model-dialog-box"></a>Преобразовать в модель диалоговое окно "пакет развертывания"
  С помощью команды **Преобразовать в модель развертывания пакетов** можно выполнить преобразование пакета в модель развертывания пакетов после проверки проекта и каждого пакета в проекте на совместимость с данной моделью. Если пакет использует специальные функции в модели развертывания проекта, такие как параметры, то пакет невозможно преобразовать.  
  
## <a name="task-list"></a>Список задач  
 Преобразование пакета в модель развертывания пакетов выполняется в два этапа.  
  
1.  При выборе команды **Преобразовать в модель развертывания пакетов** из меню **Проект** выполняется проверка проекта и каждого пакета на совместимость с этой моделью. Результаты отображаются в таблице **Результаты** .  
  
     Если проект или пакеты не прошли проверку на совместимость, щелкните **Ошибка** в столбце **Результат** для получения дополнительных сведений. Нажмите кнопку **Сохранить отчет** для сохранения копии этих сведений в текстовый файл.  
  
2.  Если проект и все пакеты прошли испытание на совместимость, нажмите кнопку **ОК** для преобразования пакета.  
  
> [!NOTE]  
>  Для преобразования проекта в модель развертывания проектов воспользуйтесь **Мастером преобразования проекта служб Integration Services**. Дополнительные сведения см. в статье [Integration Services Project Conversion Wizard](../../2014/integration-services/integration-services-project-conversion-wizard.md).  
  
## <a name="see-also"></a>См. также  
 [Развертывание проектов и пакетов](packages/deploy-integration-services-ssis-projects-and-packages.md)   
 [Развертывания пакета &#40;служб SSIS&#41;](packages/legacy-package-deployment-ssis.md)   
 [Мастер преобразования проекта служб Integration Services](../../2014/integration-services/integration-services-project-conversion-wizard.md)  
  
  
