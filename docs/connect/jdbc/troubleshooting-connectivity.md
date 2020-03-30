---
title: Устранение неполадок с подключением | Документация Майкрософт
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: bfba0b49-2e1f-411d-a625-d25fad9ea12d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d6a64589b44de50328aa3384a51e29e0c2cc9a6e
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "69027617"
---
# <a name="troubleshooting-connectivity"></a>Устранение неполадок с подключением
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] для обмена данными с базой данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] необходим установленный протокол TCP/IP. Просмотреть установленные протоколы сетевой библиотеки можно с помощью диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Попытка подключить к базе данных может завершиться с ошибкой по многим причинам. Можно выполнить следующие действия.  
  
-   Протокол TCP/IP не включен для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], либо указан неправильный сервер или номер порта. Убедитесь, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с включенным протоколом TCP/IP прослушивает заданный порт на указанном сервере. При этом может быть вызвано исключение, схожее с «Не удалось войти в систему. Не удалось соединиться с узлом по протоколу TCP/IP". Это указывает на одну из следующих причин:  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] установлен, но сетевой протокол TCP/IP не установлен для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью программы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Network Utility для [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] или диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версий.  
  
    -   TCP/IP установлен в качестве протокола [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], но не прослушивается порт, указанный в URL-адресе для подключения к JDBC. Порт 1433 задан по умолчанию, но при установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно настроить прослушивание любого порта. Убедитесь, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] прослушивает порт 1433. Кроме того, если порт был изменен, убедитесь, что порт, указанный в URL-адресе для соединения с JDBC, совпадает с измененным портом. Дополнительные сведения о формировании URL-адресов для соединения с JDBC см. в [этой статье](../../connect/jdbc/building-the-connection-url.md).  
  
    -   Адрес компьютера, указанный в URL-адресе для подключения к JDBC, не содержит ссылки на сервер, где установлен и запущен [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    -   Нарушено взаимодействие по протоколу TCP/IP между клиентом и сервером, где запущен [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Проверьте подключение TCP/IP к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью программы telnet. Например, введите в командной строке `telnet 192.168.0.0 1433`, где 192.168.0.0 — это адрес компьютера, где запущен [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а 1433 — это прослушиваемый порт. Если появится сообщение "Подключение telnet невозможно", значит TCP/IP не прослушивает подключения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на этом порте. Используйте программу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Network Utility для [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] или диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версий, чтобы настроить в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использование TCP/IP по порту 1433.  
  
    -   Используемый сервером порт закрыт брандмауэром. Это может быть порт, используемый сервером, или (необязательно) порт, связанный с именованным экземпляром сервера.  
  
-   Указано неверное имя базы данных. Убедитесь, что такая база данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] действительно существует.  
  
-   Неправильное имя пользователя или пароль. Проверьте вводимые данные.  
  
-   При использовании проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] JDBC Driver требует, чтобы на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] была установлена проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], отличная от проверки по умолчанию. Убедитесь, что этот параметр включен при установке или настройке вашего экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также раздел  
 [Диагностика проблем с JDBC Driver](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)   
 [Подключение к SQL Server с помощью JDBC Driver](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
  
  
