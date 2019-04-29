---
title: Обновление отказоустойчивого кластера SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- upgrading failover clusters
- clusters [SQL Server], upgrading
- failover clustering [SQL Server], upgrading
ms.assetid: daac41fe-7d0b-4f14-84c2-62952ad8cbfa
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a7a8d5f04808582bd56c106adce0df2c1f66aa77
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62913730"
---
# <a name="upgrade-a-sql-server-failover-cluster"></a>Обновление отказоустойчивого кластера SQL Server
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает отдельное обновление компонента [!INCLUDE[ssDE](../../../includes/ssde-md.md)] и служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] с версий [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] и [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] отказоустойчивого кластера на всех узлах отказоустойчивого кластера.  
  
 Далее приведены сведения о поддержке:  
  
-   Обновление поддерживается как через пользовательский интерфейс, так и из командной строки. Дополнительные сведения см. в статьях [Обновление экземпляра отказоустойчивого кластера SQL Server (программа установки)](upgrade-a-sql-server-failover-cluster-instance-setup.md) и [Установка SQL Server 2014 из командной строки](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).  
  
-   Обновление с [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] -обновление можно запустить из командной строки, на каждом узле отказоустойчивого кластера, либо с помощью пользовательского интерфейса программы установки для обновления каждого узла кластера. Если компоненты Full-Text Search и репликации не существуют на обновляемом экземпляре, они будут установлены автоматически, при этом возможности отключить их установку нет.  
  
-   Установка пакета обновления — на отказоустойчивых кластерах [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] пакеты обновления и обновления [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] следует устанавливать для каждого узла отдельно.  
  
-   Следующие сценарии не поддерживаются.  
  
    -   Невозможно перенести изолированный экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] на кластер отработки отказа.  
  
    -   Добавление компонентов в кластер отработки отказа. Например, невозможно добавить компонент [!INCLUDE[ssDE](../../../includes/ssde-md.md)] в существующий отказоустойчивый кластер, имеющий только службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
    -   Невозможно понизить узел отказоустойчивого кластера до изолированного экземпляра.  
  
-   Дополнительные сведения см. в статье [Экземпляры отказоустойчивого кластера (режим AlwaysOn) (SQL Server)](always-on-failover-cluster-instances-sql-server.md).  
  
## <a name="upgrading-a-includessnoversionincludesssnoversion-mdmd-multi-subnet-failover-cluster"></a>Обновление отказоустойчивого кластера с несколькими подсетями [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]  
 Вы не можете напрямую обновить подсеть не с несколькими [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] отказоустойчивый кластер с несколькими подсетями. Дополнительные сведения см. на разделе [Обновление экземпляра отказоустойчивого кластера SQL Server (программа установки)](upgrade-a-sql-server-failover-cluster-instance-setup.md).  
  
## <a name="see-also"></a>См. также  
 [Поддерживаемые обновления версий и выпусков](../../../database-engine/install-windows/supported-version-and-edition-upgrades.md)   
 [Обновление экземпляра отказоустойчивого кластера SQL Server &#40;установки&#41;](upgrade-a-sql-server-failover-cluster-instance-setup.md)   
 [Установка SQL Server 2014 из командной строки](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)  
  
  
