---
title: Виртуальные каталоги не указаны (Советник по переходу) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- virtual directories [Reporting Services]
ms.assetid: 7d32b560-49d6-4558-b5d6-9127067f82d6
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: cbadcd0f42f8d5ae81ea2a97625be96214df4ce2
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63270269"
---
# <a name="virtual-directories-are-unspecified-upgrade-advisor"></a>Виртуальные каталоги не указаны (советник по переходу)
  Помощник по обновлению не обнаружил настроек виртуального каталога для веб-службы сервера отчетов или диспетчера отчетов. После завершения обновления необходимо настроить резервирования URL-адресов для сервера отчетов с помощью диспетчера конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в основном режиме.|  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Описание  
 При обновлении установки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] резервируются новые URL-адреса для веб-службы сервера отчетов и диспетчера отчетов. Помощник по обновлению не нашел в настройках обновляемого экземпляра виртуальные каталоги для веб-службы сервера отчетов или диспетчера отчетов. У помощника по обновлению недостаточно информации, чтобы зарезервировать URL-адреса для обновленного сервера отчетов. Процесс обновления может быть продолжен, но виртуальные каталоги для сервера отчетов и диспетчера отчетов после новой установки не будут определены.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 После окончания обновления задайте URL-адреса сервера отчетов и диспетчера отчетов при помощи диспетчера конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. В диспетчере служб IIS удалите все виртуальные каталоги, в которых больше нет необходимости.  
  
 Дополнительные сведения см. в разделе [задан URL-адрес &#40;диспетчер конфигурации служб SSRS&#41; ](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления служб Reporting Services &#40;помощник по обновлению&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
