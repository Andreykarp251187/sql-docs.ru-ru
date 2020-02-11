---
title: Настройка сервера для прослушивания определенного TCP-порта (диспетчер конфигурации SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- fixed port
- static ports
- ports [SQL Server], assigning numbers
- assigning port numbers
- dynamic ports [SQL Server]
- TCP/IP [SQL Server], port numbers
ms.assetid: 2276a5ed-ae3f-4855-96d8-f5bf01890640
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e85b1a85ab9415c76fdaeee5453c992994a286ba
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62813590"
---
# <a name="configure-a-server-to-listen-on-a-specific-tcp-port-sql-server-configuration-manager"></a>Настройка сервера для прослушивания указанного TCP-порта (диспетчер конфигурации SQL Server)
  В этом разделе описано, как настроить экземпляр компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] для прослушивания определенного фиксированного порта с помощью диспетчера конфигурации SQL Server. Если прослушивание включено, то экземпляр компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] по умолчанию прослушивает TCP-порт 1433. Именованные экземпляры компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и [!INCLUDE[ssEW](../../includes/ssew-md.md)] настроены для использования динамических портов. Это означает, что при запуске службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для них выбирается свободный порт. При соединении с именованным экземпляром через брандмауэр необходимо настроить компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] на прослушивание определенного порта. Это позволит открыть в брандмауэре необходимый порт.  
  
 Дополнительные сведения о настройках брандмауэра Windows по умолчанию и описание портов TCP, влияющих на компонент Database Engine, службы Analysis Services, службы Reporting Services и службы Integration Services, см. в разделе [Настройка брандмауэра Windows для разрешения доступа к SQL Server](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).  
  
> [!TIP]  
>  При выборе номера порта ознакомьтесь [http://www.iana.org/assignments/port-numbers](http://www.iana.org/assignments/port-numbers) со списком номеров портов, назначенных конкретным приложениям. Выберите незанятый номер порта. Дополнительные сведения см. в разделе [Предусмотренный по умолчанию динамический диапазон портов для TCP/IP, который изменился в Windows Vista и Windows Server 2008](https://support.microsoft.com/kb/929851).  
  
> [!WARNING]  
>  Компонент Database Engine начнет прослушивание нового порта после перезапуска. Однако служба браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отслеживает реестр и возвращает новый номер порта, как только будет изменена конфигурация, даже если компонент Database Engine его не использует. Перезапустите компонент Database Engine, чтобы обеспечить согласованность и избежать ошибок соединения.  
  
 **В этом разделе**  
  
-   **Настройка сервера для прослушивания определенного TCP-порта с помощью:**  
  
     [Диспетчер конфигурации SQL Server](#SSMSProcedure)  
  
##  <a name="SSMSProcedure"></a>Использование диспетчер конфигурации SQL Server  
  
#### <a name="to-assign-a-tcpip-port-number-to-the-sql-server-database-engine"></a>Назначение ядру СУБД SQL Server порта TCP/IP  
  
1.  В диспетчер конфигурации SQL Server в области консоли разверните узел **SQL Server конфигурация сети**, разверните узел **протоколы для \<имени экземпляра>**, а затем дважды щелкните **TCP/IP**.  
  
2.  В диалоговом окне **Свойства TCP/IP** на вкладке **IP-адреса** появится несколько IP-адресов в формате **IP1**, **IP2**до **IPAll**. Одним из приведенных IP-адресов является адрес адаптера заглушки 127.0.0.1. Для каждого IP-адреса на компьютере появляются дополнительные IP-адреса. Чтобы определить настраиваемый IP-адрес, щелкните правой кнопкой мыши каждый адрес и выберите пункт **Свойства**.  
  
3.  Если в диалоговом окне **Динамические порты TCP** содержится значение **0**, означающее прослушивание компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)] динамических портов, удалите его.  
  
4.  В области **Свойства** **IP**_n_ в поле **TCP-порт** введите номер порта, который должен прослушивать этот IP-адрес, а затем нажмите кнопку **ОК**.  
  
5.  На панели консоли выберите **Службы SQL Server**.  
  
6.  В области сведений щелкните правой кнопкой мыши **SQL Server (**\<имя экземпляра>**)** и выберите команду **перезапустить**, чтобы прерывать и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]перезапускать.  
  
 После настройки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на прослушивание определенного порта установить соединение с ним с помощью клиентского приложения можно тремя способами:  
  
-   Запустите службу браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на сервере для подключения к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] по имени.  
  
-   Создайте псевдоним на клиенте, указав номер порта.  
  
-   Настройте клиент на использование пользовательской строки подключения.  
  
## <a name="see-also"></a>См. также:  
 [Создание или удаление псевдонима сервера, используемого &#40;ом клиента диспетчер конфигурации SQL Server&#41;](create-or-delete-a-server-alias-for-use-by-a-client.md)  
  
  
