---
title: Power Pivot обновления данных | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ppvt-sharepoint
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 243c2649af82aad3488051da543628203699a27e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68208108"
---
# <a name="power-pivot-data-refresh"></a>Обновление данных Power Pivot
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  После создания книги, содержащей данные [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , их придется периодически обновлять путем повторного выполнения запроса или команды, чтобы получать новые данные из источников, которые использовались при создании книги. Этот процесс называется **обновлением данных**. Обновление данных может производиться по запросу [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)]или как запланированная операция путем запуска процесса служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] на сервере приложений фермы SharePoint. Дополнительные сведения см. в разделе:  
  
-   [Обновление данных Power Pivot в SharePoint 2010](http://msdn.microsoft.com/01b54e6f-66e5-485c-acaa-3f9aa53119c9)  
  
-   [Настройка учетной записи автоматического обновления данных Power Pivot (Power Pivot для SharePoint)](http://msdn.microsoft.com/81401eac-c619-4fad-ad3e-599e7a6f8493)  
  
-   [Настройка сохраненных учетных данных для обновления данных Power Pivot (Power Pivot для SharePoint)](http://msdn.microsoft.com/987eff0f-bcfe-4bbd-81e0-9aca993a2a75)  
  
-   [Планирование обновления данных (Power Pivot для SharePoint)](http://msdn.microsoft.com/8571208f-6aae-4058-83c6-9f916f5e2f9b)  
  
-   [Просмотр журнала обновления данных (Power Pivot для SharePoint)](../../analysis-services/power-pivot-sharepoint/view-data-refresh-history-power-pivot-for-sharepoint.md)  
  
> [!NOTE]
>  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и SharePoint Server 2013 Excel Services используется другая архитектура для обновления сведений в моделях данных [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Архитектура SharePoint 2013 в качестве основного компонента для загрузки моделей данных [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] использует службы Excel. В прежней архитектуре обновления данных для загрузки моделей данных использовался сервер с [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System Service и [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме SharePoint. Дополнительные сведения см. в следующих разделах:  
> 
>  -   [Обновление данных PowerPivot в SharePoint 2013](../../analysis-services/power-pivot-sharepoint/power-pivot-data-refresh-with-sharepoint-2013.md)  
> -   [Обновление книг и запланированное обновление данных (SharePoint 2013 )](../../analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md)  
  
  
