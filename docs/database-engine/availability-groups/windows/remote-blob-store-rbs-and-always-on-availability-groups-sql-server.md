---
title: Удаленное хранилище больших двоичных объектов (RBS) с группами доступности
description: 'Описание использования хранилища удаленных больших двоичных объектов (RBS) с базами данных, которые являются частью группы доступности Always On. '
ms.custom: seodec18
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 01a70258-d4fd-40bc-bc44-c490b5d6c420
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 864ed8080c3978ec272f5212fa0a5e8dc40c2350
ms.sourcegitcommit: f8cf8cc6650a22e0b61779c20ca7428cdb23c850
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/04/2019
ms.locfileid: "74822482"
---
# <a name="use-remote-blob-store-rbs-with-always-on-availability-groups"></a>Использование удаленного хранилища больших двоичных объектов (RBS) и групп доступности Always On
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] может обеспечить решение высокой доступности и аварийного восстановления для BLOB-объектов [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][удаленного хранилища больших двоичных объектов (RBS)](../../../relational-databases/blob/remote-blob-store-rbs-sql-server.md) . [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] защищает все метаданные и схемы удаленного хранилища больших двоичных объектов, хранящиеся в базе данных доступности, копируя их на вторичные реплики. Эта база данных содержимого SharePoint. В целом [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] хранит метаданные этого удаленного хранилища больших двоичных объектов независимо от больших двоичных объектов.  
  
 Защита BLOB-данных в RBS зависит от расположения хранилища больших двоичных объектов следующим образом:  
  
|Место хранения большого двоичного объекта|Могут ли группы доступности защищать данные этого большого двоичного объекта?|  
|-------------------------|-----------------------------------------------------|  
|Та же база данных, содержащая метаданные удаленного хранилища больших двоичных объектов (хранимая с помощью удаленного поставщика FILESTREAM хранилища RBS)|Да|  
|Другая база данных в том же экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (хранимая с помощью удаленного поставщика FILESTREAM хранилища RBS)|Да<br /><br /> Рекомендуется поместить эту базу данных в ту же группу доступности, что и базу данных, содержащую метаданные удаленного хранилища больших двоичных объектов.|  
|Другая база данных находится на другом экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (хранимая с помощью удаленного поставщика FILESTREAM хранилища RBS)|Да<br /><br /> Эта база данных должна находиться в отдельной группе доступности.|  
|Стороннее хранилище больших двоичных объектов|нет<br /><br /> Чтобы защитить эти BLOB-данные, воспользуйтесь механизмами высокого уровня доступности поставщика хранилища больших двоичных объектов.|  
  
##  <a name="Limitations"></a> Ограничения  
  
-   Программы обслуживания хранилища RBS должны быть нацелены на первичную реплику.  
  
##  <a name="Recommendations"></a> Рекомендации  
  
-   Используйте прослушивателя группы доступности. Дополнительные сведения см. в разделе [Прослушиватели групп доступности, возможность подключения клиентов и отработка отказа приложений (SQL Server)](../../../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md).  
  
##  <a name="RelatedContent"></a> См. также  
  
-   [Обслуживание удаленного хранилища больших двоичных объектов](https://msdn.microsoft.com/library/gg316773\(SQL.105\).aspx) (в электронной документации [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] )  
  
-   [Запуск программы обслуживания удаленного хранилища больших двоичных объектов](https://blogs.msdn.com/b/sqlrbs/archive/2010/03/19/running-rbs-maintainer.aspx) (блог)  
  
-   [Настройка удаленного хранилища больших двоичных объектов (RBS) с поставщиком FILESTREAM (SharePoint 2010)](https://blogs.msdn.com/b/mvpawardprogram/archive/2012/04/02/configure-remote-blob-storage-rbs-with-the-filestream-provider-sharepoint-2010.aspx) (блог)  
  
## <a name="see-also"></a>См. также:  
 [Подключение клиента AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/always-on-client-connectivity-sql-server.md)   
 [Удаленное хранилище больших двоичных объектов (RBS) (SQL Server)](../../../relational-databases/blob/remote-blob-store-rbs-sql-server.md)  
  
  
