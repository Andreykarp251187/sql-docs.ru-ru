---
title: Изменение стартовой учетной записи службы для SQL Server (диспетчер конфигурации SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 01/07/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server services, startup account changes
- startup accounts [SQL Server]
- changing startup accounts for services
ms.assetid: d721c796-0397-46a7-901b-1a9a3c3fb385
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a2a830ad4d6fa87cd754910baf8be53216086cab
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62810445"
---
# <a name="change-the-service-startup-account-for-sql-server-sql-server-configuration-manager"></a>изменить стартовую учетную запись службы для SQL Server (диспетчер конфигурации SQL Server)
  В этом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] разделе описывается использование Configuration Manager для изменения параметров запуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] служб и изменения учетных записей служб, которые используются службами [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агентом, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] браузером [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], и. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]или PowerShell. Дополнительные сведения о выборе учетной записи службы см. в разделе [Configure Windows Service Accounts and Permissions](configure-windows-service-accounts-and-permissions.md).  
  
> [!IMPORTANT]  
>  После изменения стартовой учетной записи службы для компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] необходимо перезапустить службу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)]), чтобы изменение вступило в силу. При перезапуске службы все базы данных, связанные с этим экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , станут недоступны до того момента, когда служба успешно перезапустится. Если нужно изменить стартовую учетную запись службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , это можно делать только в период планового обслуживания или в случае, если базы данных можно перевести в режим «вне сети», не создавая помех для повседневной работы.  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Кластеризованные серверы  
  
     Изменение учетной записи службы, которая используется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , должно выполняться из активного узла кластера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
     Во время работы на Windows Server 2008 (в нестандартной конфигурации, использующей группы домена) для изменения учетной записи службы, которая используется продуктом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , необходимо остановить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в диспетчере конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , отключив группы ресурсов.  
  
-   Обновление номера SKU (от[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] до другого номера SKU)  
  
     Во время установки [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] служба « [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , агент» настраивается для использование учетной записи Network Service, но отключается. В диспетчере конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно изменить учетную запись, назначенную для службы "Агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]", но нельзя включить или запустить эту службу. После обновления номера SKU с [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] до другого номера SKU служба агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не включается автоматически, но при необходимости ее можно включить с помощью диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и задать для нее тип запуска «Вручную» или «Авто».  
  
##  <a name="SSMSProcedure"></a>Использование диспетчер конфигурации SQL Server  
  
#### <a name="to-change-the-sql-server-service-startup-account"></a>Изменение стартовой учетной записи службы SQL Server  
  
1.  В меню **Пуск** последовательно укажите пункты **Все программы**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **Средства настройки**и выберите пункт **Диспетчер конфигурации SQL Server**.  
  
    > [!NOTE]  
    >  Поскольку диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] является оснасткой консоли управления ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] ), а не изолированной программой, при работе в более новых версиях Windows диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не отображается как приложение.  
    >   
    >  -   **Windows 10**:  
    >          Чтобы открыть [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, на **начальной странице**введите SQLServerManager12. msc (для [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]). Для предыдущих версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] замените 12 на меньшее число. Если щелкнуть SQLServerManager12.msc, откроется диспетчер конфигурации. Чтобы закрепить Configuration Manager на начальной странице или на панели задач, щелкните правой кнопкой мыши SQLServerManager12. msc и выберите **открыть расположение файла**. В проводнике Windows щелкните правой кнопкой мыши файл SQLServerManager12. msc и выберите пункт **закрепить на** **панели задач или закрепить на**ней.  
    > -   **Windows 8**:  
    >          Чтобы открыть [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, во вложенном поле **Поиск** в разделе **приложения**введите **SQLServerManager\<Version>. msc** `SQLServerManager12.msc`, например, и нажмите клавишу **Ввод**.  
  
2.  В диспетчере конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выберите пункт **Службы SQL Server**.  
  
3.  В области сведений щелкните правой кнопкой мыши имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , для которого нужно изменить стартовую учетную запись службы, и пункт **Свойства**.  
  
4.  В диалоговом окне **Свойства SQL Server \<***имя_экземпляра***>** перейдите на вкладку **Вход** и выберите один из типов учетных записей в поле **Использовать для входа**.  
  
5.  Выбрав новую стартовую учетную запись службы, нажмите кнопку **ОК**.  
  
     Появится окно сообщения с подтверждением перезапуска службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
6.  Нажмите **Да**и закройте диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>См. также:  
 [Запуск, остановка, приостановка, возобновление и перезапуск ядро СУБД, агент SQL Server или службы обозреватель SQL Server](start-stop-pause-resume-restart-sql-server-services.md)   
 [Настройка инструментария WMI для отображения состояния сервера в инструментальных средствах SQL Server](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md)  
  
  
