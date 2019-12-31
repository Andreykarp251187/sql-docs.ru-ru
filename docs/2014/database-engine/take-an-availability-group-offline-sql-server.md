---
title: Изменение группы доступности в автономном режиме
description: Действия по настройке группы доступности Always On в автономном режиме
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], take offline
ms.assetid: 50f5aad8-0dff-45ef-8350-f9596d3db898
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 87dff347bd0aee1211093d9e3406a24670a80e7f
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/19/2019
ms.locfileid: "75228171"
---
# <a name="take-an-availability-group-offline-sql-server"></a>Перевод группы доступности в режим «вне сети» (SQL Server)
  В этом разделе описывается перевод группы доступности AlwaysOn из состояния ONLINE в состояние OFFLINE с помощью [!INCLUDE[tsql](../includes/tsql-md.md)] в [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] и более поздних версий. У баз данных с синхронной фиксацией потери данных не происходит, поскольку реплика с синхронной фиксацией не синхронизирована, режим OFFLINE вызывает ошибку, а группа доступности остается в режиме ONLINE. Продолжение работы группы доступности в режиме «в сети» защищает несинхронизированные базы данных с синхронной фиксацией от возможной потери данных. После перехода группы доступности в режим «вне сети» ее базы данных становятся недоступными для клиентов, при этом невозможно перевести группу доступности обратно в режим «в сети». Таким образом, переводить группу доступности в режим «вне сети» следует только в целях миграции ресурсов этой группы доступности с одного кластера WSFC на другой.  
  
 Если во время миграции [!INCLUDE[ssHADR](../includes/sshadr-md.md)]с одного кластера на другой какие-либо приложения подключаются напрямую к первичной реплике группы доступности, то эту группу доступности необходимо перевести в режим «вне сети». Миграция [!INCLUDE[ssHADR](../includes/sshadr-md.md)] поддерживает обновление операционной системы с минимальным временем простоя групп доступности. Типичный сценарий — использование миграции [!INCLUDE[ssHADR](../includes/sshadr-md.md)] с одного сервера на другой для обновления до [!INCLUDE[win8](../includes/win8-md.md)] или [!INCLUDE[win8srv](../includes/win8srv-md.md)]. Дополнительные сведения см. в документе [Миграция между кластерами групп доступности AlwaysOn для обновления ОС](https://msdn.microsoft.com/library/jj873730.aspx).  
  

  
##  <a name="BeforeYouBegin"></a>Перед началом  
  
> [!CAUTION]  
>  Используйте вариант OFFLINE только для миграции ресурсов группы доступности с одного кластера на другой.  
  
###  <a name="Prerequisites"></a>Требований  
  
-   На экземпляре сервера, где вводится команда OFFLINE, должны быть запущены службы [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] или более поздней версии (выпуск Enterprise Edition или более продвинутый выпуск).  
  
-   Группа доступности должна быть в данный момент в сети.  
  
###  <a name="Recommendations"></a>Проектирован  
 Прежде чем переводить группу доступности в режим «вне сети», удалите прослушиватели группы доступности. Дополнительные сведения см. в документе [Remove an Availability Group Listener &#40;SQL Server&#41;](availability-groups/windows/remove-an-availability-group-listener-sql-server.md).  
  
###  <a name="Security"></a>Бюллетеня  
  
####  <a name="Permissions"></a>Чтение  
 Необходимо разрешение ALTER AVAILABILITY GROUP для группы доступности, разрешение CONTROL AVAILABILITY GROUP, разрешение ALTER ANY AVAILABILITY GROUP или разрешение CONTROL SERVER.  
  
##  <a name="TsqlProcedure"></a>Использование Transact-SQL  
 **Перевод группы доступности в режим «вне сети»**  
  
1.  Подключитесь к экземпляру сервера, где размещается реплика доступности для группы доступности. Эта реплика может быть первичной или вторичной.  
  
2.  Инструкция [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) используется следующим образом:  
  
     ALTER AVAILABILITY GROUP *имя_группы* OFFLINE  
  
     где *имя_группы* — это имя группы доступности.  
  
### <a name="example"></a>Пример  
 В следующем примере выполняется перевод группы доступности `AccountsAG` в режим «вне сети».  
  
```sql
ALTER AVAILABILITY GROUP AccountsAG OFFLINE;  
```  
  
##  <a name="FollowUp"></a>Дальнейшие действия. после перехода группы доступности в режим «вне сети»  
  
-   **Ведение журнала автономной операции:**  Удостоверение узла WSFC, в котором была инициирована АВТОНОМная операция, хранится в журнале кластера WSFC и в журнале ошибок SQL.  
  
-   **Если прослушиватель группы доступности не был удален до перевода группы в режим «вне сети»:**  При переносе группы доступности в другой кластер WSFC удалите VNN и виртуальный IP-адрес прослушивателя. Их можно удалить с помощью консоли управления отказоустойчивым кластером либо с помощью командлета [Remove-ClusterResource](https://technet.microsoft.com/library/ee461015\(WS.10\).aspx) PowerShell или [cluster.exe](https://technet.microsoft.com/library/ee461015\(WS.10\).aspx). Обратите внимание, что программа cluster.exe в Windows 8 является устаревшей.  
  
##  <a name="RelatedTasks"></a>Связанные задачи  
  
-   [Удаление &#40;прослушивателя группы доступности SQL Server&#41;](availability-groups/windows/remove-an-availability-group-listener-sql-server.md)  
  
-   [Измените контекст кластера HADR &#40;экземпляра сервера SQL Server&#41;](availability-groups/windows/change-the-hadr-cluster-context-of-server-instance-sql-server.md)  
  
##  <a name="RelatedContent"></a>Связанное содержимое  
  
-   [Технические статьи по SQL Server 2012](https://msdn.microsoft.com/library/bb418445\(SQL.10\).aspx)  
  
-   [Блог группы разработчиков SQL Server AlwaysOn: официальный блог группы разработчиков SQL Server AlwaysOn](https://blogs.msdn.com/b/sqlalwayson/)  
  
## <a name="see-also"></a>См. также  
 [Группы доступности AlwaysOn &#40;SQL Server&#41;](availability-groups/windows/always-on-availability-groups-sql-server.md)  
