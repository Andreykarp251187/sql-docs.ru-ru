---
title: Общие сведения о скрипте развертывания Analysis Services | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services Deployment Wizard, scripts
- deploying [Analysis Services], scripts
- Analysis Services deployments, scripts
- scripts [Analysis Services], deployment
ms.assetid: a63ebee9-9848-48f1-82ad-64ecf2e47019
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a9436d33cdc99cf979509a40f06ceea15c0cd765
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66072658"
---
# <a name="understanding-the-analysis-services-deployment-script"></a>Основные сведения о скрипте развертывания служб Analysis Services
  Скрипт развертывания XML для аналитики, сформированный мастером развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , состоит из двух частей.  
  
-   Первая часть скрипта развертывания содержит команды, необходимые для создания, изменения или удаления соответствующих [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] объектов в целевой базе данных. По умолчанию входные файлы, сформированные проектом служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , основываются на добавочном развертывании. В результате скрипт развертывания XML для аналитики влияет только на те объекты, которые были изменены или удалены.  
  
-   Вторая часть скрипта развертывания содержит команды, необходимые для обработки только тех объектов, которые были созданы или изменены на целевом сервере (параметр «Обработка по умолчанию») или для полной обработки целевой базы данных. Кроме того, можно выбрать, чтобы скрипт развертывания не содержал команд обработки.  
  
 Весь скрипт развертывания может выполняться в одной транзакции или в нескольких транзакциях. Если скрипт выполняется в нескольких транзакциях, то первая часть скрипта выполняется в виде одной транзакции, а каждый объект обрабатывается в собственной транзакции.  
  
> [!IMPORTANT]  
>  Мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] развертывает объекты только в одну базу данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Он не осуществляет развертывание никаких объектов или данных уровня сервера.  
  
## <a name="see-also"></a>См. также  
 [Запуск мастера развертывания Analysis Services](running-the-analysis-services-deployment-wizard.md)   
 [Основные сведения о входных файлах, применяемых для создания скрипта развертывания](deployment-script-files-input-used-to-create-deployment-script.md)  
  
  
