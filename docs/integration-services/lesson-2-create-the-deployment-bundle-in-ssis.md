---
title: Занятие 2. Создание пакета развертывания в службах SSIS | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: ab17289d-c3d4-4a5e-b7f5-4fea8ae21707
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 23d700f7886b046896397eb1cce4eb21f9c32850
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "71296003"
---
# <a name="lesson-2-create-the-deployment-bundle-in-ssis"></a>Занятие 2. Создание пакета развертывания в службах SSIS

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


На [занятии 1: подготовка к созданию пакета развертывания](../integration-services/lesson-1-preparing-to-create-the-deployment-bundle.md)был создан проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , названный "Учебник по развертыванию", к нему были добавлены пакеты и вспомогательные файлы, а также выполнена настройка пакетов.  
  
На этом занятии создается пакет развертывания, представляющий собой папку, в которой содержатся все элементы, необходимые для установки пакетов на другом компьютере. В пакет развертывания необходимо включить манифест развертывания, копии пакетов и копии файлов поддержки из проекта «Учебник по развертыванию». В манифесте развертывания перечисляются пакеты, различные файлы и настройки из пакета развертывания.  
  
Помимо этого будет проверен список файлов в пакете развертывания и содержимое манифеста.  
  
**Предполагаемое время выполнения данного занятия:** 30 минут  
  
## <a name="lesson-tasks"></a>Задачи занятия  
Это занятие содержит следующие задачи.  
  
-   [Шаг 1. Построение программы развертывания](../integration-services/lesson-2-1-building-the-deployment-utility.md)  
  
-   [Шаг 2. Проверка пакета развертывания](../integration-services/lesson-2-2-verifying-the-deployment-bundle.md)  
  
## <a name="start-the-lesson"></a>Начало занятия  
[Шаг 1. Построение программы развертывания](../integration-services/lesson-2-1-building-the-deployment-utility.md)  
  
  
  
