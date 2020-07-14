---
title: Запуск SQL Server при наличии и отсутствии сети | Документы Майкрософт
description: Узнайте, как запускать SQL Server при наличии и отсутствии сети. Сведения о локальном использовании см. в разделе об использовании локального канала. Сведения об использовании в сети см. в разделе о проверке наличия требуемых служб.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- verifying Server service has been started
- net start [SQL Server]
- command prompt [SQL Server], connections
- SQL Server services, networks
- status information [SQL Server], Server service
- running SQL Server
- networking [SQL Server], SQL Server with or without
- services [SQL Server], networks
- starting Server service
- SQL Server, running
ms.assetid: 54eac961-5c7a-4481-982d-f93a64b5c2f4
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 40da72c64afd53e01e7ce5060d18a273c5263796
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85651506"
---
# <a name="run-sql-server-with-or-without-a-network"></a>Запуск SQL Server при наличии и отсутствии сети
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может работать в сети или без подключения к ней.  
  
## <a name="running-sql-server-on-a-network"></a>Запуск SQL Server при подключении к сети  
 Чтобы сервер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] мог взаимодействовать с клиентами и другими серверами в сети, должна быть запущена служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . По умолчанию [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows автоматически запускает встроенную службу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Чтобы определить, была ли запущена служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , в командной строке введите следующее:  
  
 **net start**  
  
 Если службы, связанные с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , запущены, следующие службы отобразятся в выходных данных команды **net start** :  
  
-   Службы Analysis Services (MSSQLSERVER)  
  
-   SQL Server (MSSQLSERVER)  
  
-   SQL Server Agent (MSSQLSERVER)  
  
## <a name="running-sql-server-without-a-network"></a>Запуск SQL Server без подключения к сети  
 При запуске экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] без подключения к сети нет необходимости запускать встроенную службу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Поскольку [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], диспетчер конфигураций SQL Server и команды **net start** и **net stop** могут работать даже без подключения к сети, процедуры запуска и остановки экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] аналогичны при работе в сети и автономной работе.  
  
 При подключении к изолированному экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из локального клиента, например **sqlcmd**, осуществляется обход сети и подключение к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] напрямую через локальный канал. Разница между локальным и сетевым каналами заключается в использовании сети. И локальный, и сетевой каналы устанавливают соединение с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] через стандартный канал (\\\\.\pipe\sql\query), если не указано другое.  
  
 При подключении к локальному экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] без указания имени сервера используется локальный канал. При подключении к локальному экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с явным указанием имени сервера используется или сетевой канал, или другой механизм сетевого межпроцессного взаимодействия (IPC), например через протоколы межсетевого и последовательного обмена пакетами (IPX/SPX), если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] настроен для работы с несколькими сетями. Так как отдельный сервер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает сетевые каналы, при соединении с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из клиента ненужный аргумент **/** _<имя_сервера>_ необходимо опустить. Например, для подключения к отдельному экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из **osql**введите:  
  
 **osql /Usa /P** _\<saPassword>_  
  
  
