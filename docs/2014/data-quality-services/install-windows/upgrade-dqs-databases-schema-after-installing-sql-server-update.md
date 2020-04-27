---
title: Обновление схемы базы данных DQS после установки обновления SQL Server | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: c8f3fbae-02c4-464d-a35c-7108f48c58cb
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 5a2b13c80c9e6ee83d2713feab5d9839ded4a6d7
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "65481266"
---
# <a name="upgrade-dqs-databases-schema-after-installing-sql-server-update"></a>Обновление схемы базы данных DQS после установки обновления SQL Server
  После установки обновления SQL Server (обновления, исправления или накопительного обновления) на ранее настроенном экземпляре DQS можно обновить схему баз данных DQS, запустив файл DQSInstaller.exe с параметром командной строки **upgrade** . В противном случае может появиться сообщение об ошибке при попытке соединения с сервером DQS через клиент Data Quality:  
  
```  
An error occurred in the Microsoft .NET Framework while trying to load assembly id 65581.  
```  
  
 Обновление схемы баз данных DQS не влияет на существующие данные в базах данных DQS (базах знаний, проектах качества данных и экспортированные результаты в базе данных DQS_STAGING_DATA). Однако необходимо создать резервную копию баз данных DQS, прежде чем обновлять схему баз данных DQS, чтобы предотвратить любую случайную потерю данных при обновлении схемы. Дополнительные сведения о создании резервной копии баз данных DQS см. в разделе [Backing Up and Restoring DQS Databases](../backing-up-and-restoring-dqs-databases.md).  
  
> [!NOTE]  
>  Большинство обновлений SQL Server требует обновления схемы баз данных DQS. Дополнительные сведения об обновлениях SQL Server, которые требуют обновления до схемы баз данных DQS, см. в диаграмме на шаге 1.А в статье [Upgrade DQS: Installing Cumulative Updates or Hotfix Patches on Data Quality Services](https://go.microsoft.com/fwlink/?LinkID=251565)(Обновления службы DQS: установка накопительных обновлений или исправлений для служб Data Quality Services).  
  
## <a name="prerequisites"></a>Предварительные условия  
  
-   Необходимо выполнить вход от имени члена группы администраторов на компьютере [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] .  
  
-   Учетная запись пользователя Windows должна входить в предопределенную роль сервера sysadmin на экземпляре SQL Server, где установлен сервер [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] .  
  
### <a name="to-upgrade-dqs-databases-schema"></a>Обновление схемы базы данных DQS  
  
1.  (Рекомендуется) Создать резервную копию баз данных DQS, прежде чем продолжить обновление схемы. Дополнительные сведения о создании резервной копии баз данных DQS см. в разделе [Backing Up and Restoring DQS Databases](../backing-up-and-restoring-dqs-databases.md).  
  
2.  Откройте командную строку.  
  
3.  В командной строке перейдите в папку, где находится файл DQSInstaller.exe. Если был установлен экземпляр SQL Server по умолчанию, файл DQSInstaller.exe будет находиться в папке «C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn».  
  
    ```  
    cd C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn  
    ```  
  
4.  В командной строке введите следующую команду и нажмите клавишу ВВОД:  
  
    ```  
    dqsinstaller.exe -upgrade  
    ```  
  
5.  Установщик предложит создать резервную копию базы данных DQS, прежде чем продолжить. Если резервное копирование баз данных DQS уже выполнено, введите `Y` или `Yes` и нажмите клавишу ВВОД, чтобы продолжить обновление.  
  
6.  После успешного обновления схемы баз данных DQS отображается сообщение о завершении.  
  
## <a name="next-steps"></a>Дальнейшие действия  
 Войдите на обновленный сервер из клиентского приложения Data Quality.  
  
 Дополнительные сведения об обновлении схемы баз данных DQS после установки обновлений SQL Server и о шагах по устранению связанных с обновлением неполадок см. в статье [Upgrade DQS: Installing Cumulative Updates or Hotfix Patches on Data Quality Services](https://go.microsoft.com/fwlink/?LinkID=251565)(Обновления службы DQS: установка накопительных обновлений или исправлений для служб Data Quality Services).  
  
## <a name="see-also"></a>См. также  
 [Установка служб Data Quality Services](install-data-quality-services.md)   
 [Обновление сборок SQLCLR после загрузки обновлений .NET Framework](upgrade-sqlclr-assemblies-after-net-framework-update.md)  
  
  
