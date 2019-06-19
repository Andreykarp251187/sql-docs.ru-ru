---
title: Запуск системного монитора | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- System Monitor [SQL Server], running
- Windows System Monitor [SQL Server], running
- remote procedure calls [SQL Server]
- starting Windows NT System Monitor
- RPC
ms.assetid: 05297984-bc8d-43df-829c-032387f7ea61
author: julieMSFT
ms.author: jrasnick
manager: craigg
ms.openlocfilehash: 67652dd6931f1961bbfc9f19b19a5044816edcc3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62672068"
---
# <a name="run-system-monitor"></a>Запуск системного монитора
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Системный монитор использует удаленные вызовы процедур (RPC) для сбора данных о Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Любой пользователь, обладающий разрешениями Microsoft Windows для запуска системного монитора, может его для мониторинга [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  При использовании системного монитора нельзя подключиться к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , запущенному в системе Windows 98.  
  
 Как и в случаях со всеми средствами мониторинга производительности, следует ожидать некоторого снижения производительности при использовании системного монитора для мониторинга [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Реальное снижение производительности на каком-либо определенном экземпляре зависит от аппаратного обеспечения, числа счетчиков и выбранного интервала обновления. Однако системный монитор специально интегрирован в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для уменьшения снижения производительности.  
  
> [!NOTE]  
>  Если для мониторинга выбраны счетчики производительности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в системном мониторе, то счетчики будут видны, даже если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не работает.  
  
 Сведения о запуске системного монитора см. в разделе [Запуск системного монитора (Windows)](../../relational-databases/performance/start-system-monitor-windows.md).  
  
  
