---
title: MSSQLSERVER_10060 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
f1_keywords:
- "10060"
helpviewer_keywords:
- 10060 (Database Engine error)
ms.assetid: 28c21277-cad8-406c-a955-07933a56982a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 05d10406c4eb3e0a854942084047c4c42b576062
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68095657"
---
# <a name="mssqlserver10060"></a>MSSQLSERVER_10060
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|10060|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя||  
|Текст сообщения|При соединении с сервером произошла ошибка.  Эта ошибка при соединении с SQL Server может быть вызвана тем, что в параметрах SQL Server по умолчанию запрещены удаленные соединения. (поставщик: поставщик TCP, ошибка: 0 — "Попытка установить соединение была безуспешной, т.к. от другого компьютера за требуемое время не получен нужный отклик, или было разорвано уже установленное соединение из-за неверного отклика уже подключенного компьютера".) (Microsoft SQL Server, ошибка: 10060)|  
  
## <a name="explanation"></a>Объяснение  
Клиенту [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не удается установить соединение с сервером. Эта ошибка может возникать, если брандмауэр сервера отказывает в соединении либо если на сервере не настроен прием удаленных соединений.  
  
## <a name="user-action"></a>Действие пользователя  
Чтобы устранить эту неполадку, выполните следующие действия.  
  
-   Убедитесь, что в брандмауэре на компьютере для этого экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] настроен прием соединений.  
  
-   С помощью диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] разрешите в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] прием удаленных соединений.  
  
## <a name="see-also"></a>См. также:  
[Настройка брандмауэра Windows для доступа к компоненту Database Engine](~/database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)  
[Настройка клиентских протоколов](~/database-engine/configure-windows/configure-client-protocols.md)  
[Сетевые протоколы и библиотеки](~/sql-server/install/network-protocols-and-network-libraries.md)  
[Конфигурация клиентской сети](~/database-engine/configure-windows/client-network-configuration.md)  
[Настройка клиентских протоколов](~/database-engine/configure-windows/configure-client-protocols.md)  
[Включение или отключение сетевого протокола сервера](~/database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
