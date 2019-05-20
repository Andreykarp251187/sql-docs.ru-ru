---
title: Переименование компьютера, на котором установлен сервер отчетов | Документы Майкрософт
ms.date: 03/20/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
helpviewer_keywords:
- renaming report servers
ms.assetid: 82fc4ba2-291a-4939-a025-271b8d687c54
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 15c69293cbe602cd69e4e0dfe0f0c29deb79347c
ms.sourcegitcommit: dda9a1a7682ade466b8d4f0ca56f3a9ecc1ef44e
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 05/14/2019
ms.locfileid: "65581430"
---
# <a name="rename-a-report-server-computer"></a>Переименование компьютера, на котором установлен сервер отчетов
  Переименование компьютера приведет к изменению соответствующих имен веб-сервера и экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (если они установлены на одном компьютере). В некоторых случаях службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] могут оказаться недоступным после изменения имени компьютера. Чтобы заново настроить сервер отчетов после изменения имени компьютера, выполните шаги, описанные в этом разделе.  
  
## <a name="renaming-a-sql-server-database-engine"></a>Переименование компонента SQL Server Database Engine  
 При переименовании экземпляра компонента  [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , на котором работает база данных сервера отчетов, выполните следующие действия.  
  
1.  Запустите программу настройки служб Reporting Services и подключитесь к серверу отчетов, который использует базу данных сервера отчетов на переименованном сервере.  
  
2.  Откройте страницу «Установка базы данных».  
  
3.  В окне **Имя сервера**введите или выберите имя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , затем нажмите кнопку **Подключиться**.  
  
4.  Нажмите кнопку **Применить**.  
  
 Если сервер отчетов применяет локальный экземпляр компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] , для указания сервера можно использовать имя *(local)* или *(local)\имя_экземпляра* . Если для ссылки на сервер используется имя *(local)* , переименование сервера не повлияет на работу соединений. Если используется удаленный сервер или службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] настроены с помощью имени сервера, при изменении имени сервера необходимо обновлять сведения о подключении к базе данных.  
  
## <a name="renaming-a-report-server-computer"></a>Переименование компьютера, на котором установлен сервер отчетов  
 Если был переименован компьютер, на котором выполняется сервер отчетов, выполните следующее:  
  
1.  Откройте файл RSReportServer.config в текстовом редакторе и измените настройку **UrlRoot** , чтобы она соответствовала новому имени сервера. Настройка **UrlRoot** используется модулями доставки при формировании URL-адреса, предназначенного для доступа к элементам, хранящимся на сервере отчетов. При изменении URL-адреса сервера отчетов необходимо обновить настройку **UrlRoot** , чтобы подписки продолжали выполнять доставку отчетов должным образом.  
  
2.  В том же файле, если он задан, измените значение параметра **ReportServerUrl** , чтобы оно отражало новое имя сервера. Имейте в виду, что эта настройка используется не во всех установках. Если она отсутствует, ничего не меняйте.  
  
    > [!NOTE]  
    >  Если в корпоративной сети используется служба WINS, сервер отчетов и диспетчер отчетов некоторое время могут быть доступны под предыдущим именем. Служба WINS сопоставляет IP-адрес с каждым из компьютеров, которые она обслуживает. После того как службой WINS будет обновлен IP-адрес переименованного компьютера, старое имя компьютера больше не сможет использоваться для доступа к серверу отчетов или диспетчеру отчетов.  
  
## <a name="see-also"></a>См. также:  
 [Файл конфигурации RsReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)   
 [Использование диспетчера конфигурации служб Reporting Services (собственный режим)](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md)   
 [Сервер отчетов служб Reporting Services (основной режим)](../../reporting-services/report-server/reporting-services-report-server-native-mode.md)   
 [Запуск и остановка службы сервера отчетов](../../reporting-services/report-server/start-and-stop-the-report-server-service.md)   
 [Программа rsconfig (SSRS)](../../reporting-services/tools/rsconfig-utility-ssrs.md)  
  
  
