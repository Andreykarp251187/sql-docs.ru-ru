---
title: Не удалось загрузить «Microsoft.AnalysisServices.SharePoint.Integration» | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ppvt-sharepoint
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4da716ab3797f4f6ea54d94c53f753685972df25
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68208293"
---
# <a name="could-not-load-microsoftanalysisservicessharepointintegration"></a>Не удалось загрузить Microsoft.AnalysisServices.SharePoint.Integration
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  В среде SharePoint 2010, где установлен [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint, эта ошибка возникает, если решение на уровне приложений для [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] развернуто неправильно.  
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Область применения|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint|  
|Номер версии продукта|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Причина|Решение Powerpivotwebapp не развернуто или развернуто неправильно.|  
|Текст сообщения|Не удалось загрузить файл или сборку Microsoft.AnalysisServices.SharePoint.Integration|  
  
## <a name="explanation"></a>Объяснение  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint использует пакеты решений для развертывания своих компонентов на сервере SharePoint. Одно из решений развернуто неправильно. Поэтому при попытке открыть коллекцию [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] или другие страницы приложения [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] на сайте SharePoint возникает эта ошибка.  
  
## <a name="user-action"></a>Действие пользователя  
 Выполните развертывание пакета решения.  
  
1.  В разделе «Системные параметры» центра администрирования выберите **Управление решениями фермы**.  
  
2.  Щелкните **Powerpivotwebapp**.  
  
3.  Нажмите **Развернуть решение**.  
  
4.  Выберите веб-приложение, для которого возникает эта ошибка. Если имеются несколько веб-приложений, выполните повторное развертывание для них всех.  
  
5.  Нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [Развертывание решений PowerPivot в SharePoint](../../analysis-services/power-pivot-sharepoint/deploy-power-pivot-solutions-to-sharepoint.md)  
  
  
