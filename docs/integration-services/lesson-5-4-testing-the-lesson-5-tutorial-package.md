---
title: Шаг 4. Тестирование пакета, созданного на занятии 5 | Документация Майкрософт
ms.custom: ''
ms.date: 01/08/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 5215b77d-c2ec-4b25-a3de-ca49ea197d74
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 660c2ee9f09bcd3e8a4c883247bdded124561509
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67911475"
---
# <a name="lesson-5-4-test-the-lesson-5-package"></a>Занятие 5-4. Тестирование пакета занятия 5

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



Во время выполнения пакету присваивается значение свойства **Каталог** из переменной конфигурации, а не имя каталога, которое было указано при создании пакета. Значение этой переменной берется из XML-файла **SSISTutorial.dtsConfig**.  
  
Чтобы убедиться в том, что пакет обновляет свойство **Каталог** новым значением во время выполнения, выполните пакет. Так как в новом каталоге имеются только три файла образцов данных, поток данных запускается только три раза.  
  
## <a name="checking-the-package-layout"></a>Проверка макета пакета  
Прежде чем проверить пакет, нужно убедиться в том, что потоки данных и управления в пакете занятия 5 аналогичны объектам, показанным на следующих схемах:  
  
**Поток управления**  
  
![Поток управления в пакете](../integration-services/media/task4lesson2control.gif "Поток управления в пакете")  
  
**Поток данных**  
  
![Поток данных в пакете](../integration-services/media/task9lesson1data.gif "Поток данных в пакете")  
  
## <a name="test-the-lesson-5-package"></a>Тестирование пакета занятия 5  
  
1.  В меню **Отладка** выберите команду **Начать отладку**.  
  
2.  После окончания работы пакета выберите в меню **Отладка** пункт **Остановить отладку**.  
  
## <a name="next-lesson"></a>Следующее занятие  
[Занятие 6. Использование параметров в модели развертывания проекта в службах SSIS](../integration-services/lesson-6-using-parameters-with-the-project-deployment-model-in-ssis.md)  
  
  
  
