---
title: Обратная совместимость служб IIS, компоненты не были обнаружены (Советник по переходу) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- IIS [Reporting Services]
ms.assetid: e794185a-0a77-480a-9aea-d09f8760a6b8
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 9cfae4d34ef825ac1781c90fda8d7e38c0299a1b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66094777"
---
# <a name="iis-backward-compatibility-components-were-not-detected-upgrade-advisor"></a>Не найдены компоненты обратной совместимости служб IIS (советник по переходу)
  Помощник по обновлению не обнаружил компонентов и настроек служб IIS, которые содержат информацию, используемую программой настройки для создания новых URL-адресов служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в основном режиме.|  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Описание  
 Службы IIS включают компоненты, которые предоставляют информацию о виртуальных каталогах сервера отчетов и диспетчера отчетов. Эти компоненты не установлены на компьютере, на котором размещен сервер отчетов. Обновление может быть продолжено, но URL-адреса сервера отчетов и диспетчера отчетов повторно созданы не будут.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 После окончания обновления задайте URL-адреса сервера отчетов и диспетчера отчетов при помощи программы настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. В диспетчере служб IIS удалите виртуальные каталоги, в которых больше нет необходимости.  
  
 Дополнительные сведения см. в разделе [задан URL-адрес &#40;диспетчер конфигурации служб SSRS&#41; ](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления служб Reporting Services &#40;помощник по обновлению&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
