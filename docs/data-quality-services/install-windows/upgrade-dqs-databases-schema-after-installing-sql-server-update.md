---
title: Обновление схемы баз данных DQS после установки SQL Server обновления
description: Узнайте, как обновить экземпляр служб Data Quality Services (DQS) с помощью DQSInstaller. exe после обновления SQL Server с помощью исправления, исправления или накопительного обновления.
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: c8f3fbae-02c4-464d-a35c-7108f48c58cb
author: swinarko
ms.author: sawinark
ms.openlocfilehash: db5009ef7f5c9ff2a57022d30b2eb9f009fb6ab8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "75558071"
---
# <a name="upgrade-dqs-databases-schema-after-installing-sql-server-update"></a>Обновление схемы баз данных DQS после установки SQL Server обновления

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  После установки обновления SQL Server (обновления, исправления или накопительного обновления) на ранее настроенном экземпляре DQS можно обновить схему баз данных DQS, запустив файл DQSInstaller.exe с параметром командной строки **upgrade** . В противном случае может появиться сообщение об ошибке при попытке соединения с сервером DQS через клиент Data Quality:  
  
```  
An error occurred in the Microsoft .NET Framework while trying to load assembly id 65581.  
```  
  
 Обновление схемы баз данных DQS не влияет на существующие данные в базах данных DQS (базах знаний, проектах качества данных и экспортированные результаты в базе данных DQS_STAGING_DATA). Однако необходимо создать резервную копию баз данных DQS, прежде чем обновлять схему баз данных DQS, чтобы предотвратить любую случайную потерю данных при обновлении схемы. Дополнительные сведения о создании резервной копии баз данных DQS см. в разделе [Backing Up and Restoring DQS Databases](../../data-quality-services/backing-up-and-restoring-dqs-databases.md).  
  
> [!NOTE]  
>  Большинство обновлений SQL Server требует обновления схемы баз данных DQS. Дополнительные сведения об обновлениях SQL Server, которые требуют обновления до схемы баз данных DQS, см. в диаграмме на шаге 1.А в статье [Upgrade DQS: Installing Cumulative Updates or Hotfix Patches on Data Quality Services](https://go.microsoft.com/fwlink/?LinkID=251565)(Обновления службы DQS: установка накопительных обновлений или исправлений для служб Data Quality Services).  
  
## <a name="prerequisites"></a>Предварительные требования  
  
-   Необходимо выполнить вход от имени члена группы администраторов на компьютере [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] .  
  
-   Учетная запись пользователя Windows должна входить в предопределенную роль сервера sysadmin на экземпляре SQL Server, где установлен сервер [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] .  
  
### <a name="to-upgrade-dqs-databases-schema"></a>Обновление схемы базы данных DQS  
  
1.  (Рекомендуется) Создать резервную копию баз данных DQS, прежде чем продолжить обновление схемы. Дополнительные сведения о создании резервной копии баз данных DQS см. в разделе [Backing Up and Restoring DQS Databases](../../data-quality-services/backing-up-and-restoring-dqs-databases.md).  
  
2.  Откройте командную строку.  
  
3.  В командной строке перейдите в папку, где находится файл DQSInstaller.exe. Если был установлен экземпляр SQL Server по умолчанию, файл DQSInstaller.exe будет помещен в папку C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn:  
  
    ```  
    cd C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn  
    ```  
  
4.  В командной строке введите следующую команду и нажмите клавишу ВВОД:  
  
    ```  
    dqsinstaller.exe -upgrade  
    ```  
  
5.  Установщик предложит создать резервную копию базы данных DQS, прежде чем продолжить. Если резервное копирование базы данных DQS уже выполнено, введите **Y** или **Yes** и нажмите клавишу ВВОД, чтобы продолжить обновление.  
  
6.  После успешного обновления схемы баз данных DQS отображается сообщение о завершении.  
  
## <a name="next-steps"></a>Дальнейшие действия  
 Войдите на обновленный сервер из клиентского приложения Data Quality.  
  
 Дополнительные сведения об обновлении схемы баз данных DQS после установки обновлений SQL Server и о шагах по устранению связанных с обновлением неполадок см. в статье [Upgrade DQS: Installing Cumulative Updates or Hotfix Patches on Data Quality Services](https://go.microsoft.com/fwlink/?LinkID=251565)(Обновления службы DQS: установка накопительных обновлений или исправлений для служб Data Quality Services).  
  
## <a name="see-also"></a>См. также:  
 [Установка служб Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md)   
 [Обновление сборок SQLCLR после загрузки обновлений .NET Framework](../../data-quality-services/install-windows/upgrade-sqlclr-assemblies-after-net-framework-update.md)  
  
  
