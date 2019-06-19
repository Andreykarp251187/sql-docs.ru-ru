---
title: Переключение сеанса зеркального отображения базы данных на другой ресурс вручную (среда SQL Server Management Studio) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- failover [SQL Server], database mirroring
- manual failover [SQL Server]
- database mirroring [SQL Server], failover
ms.assetid: 4ecf9c63-b3a4-4c54-b553-5bc37973232b
author: MikeRayMSFT
ms.author: mikeray
manager: jroth
ms.openlocfilehash: 48dbf8caf5a38e228d6c11e6b5917693adc24176
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66795410"
---
# <a name="manually-fail-over-a-database-mirroring-session-sql-server-management-studio"></a>Переключение сеанса зеркального отображения базы данных на другой ресурс вручную (среда SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Когда зеркальная база данных синхронизирована (то есть база данных находится в состоянии SYNCHRONIZED), владелец базы данных может инициировать отработку отказа на зеркальном сервере вручную.  
  
 При отработке отказа вручную основная и зеркальная роли сервера для базы данных, в которых произошла отработка отказа, меняются местами. Зеркальная база данных становится основной базой данных, а основная — зеркальной. Например в следующей таблице показано, как отработка отказа вручную меняет местами роли двух участников зеркального отображения: `SQLDBENGINE0_1` и `SQLDBENGINE0_2`.  
  
|Сервер|До отработки отказа|После отработки отказа|  
|------------|---------------------|--------------------|  
|`SQLDBENGINE0_1`|PRINCIPAL|MIRROR|  
|`SQLDBENGINE0_2`|MIRROR|PRINCIPAL|  
  
 Обратите внимание на то, что роли сервера для других сеансов зеркального отображения баз данных не подвергаются изменению. Дополнительные сведения см. в статье [Переключение ролей во время сеанса зеркального отображения базы данных (SQL Server)](../../database-engine/database-mirroring/role-switching-during-a-database-mirroring-session-sql-server.md).  
  
### <a name="to-manually-fail-over-database-mirroring"></a>Ручное переключение зеркального отображения базы данных  
  
1.  Установите соединение с экземпляром основного сервера и на панели **Обозреватель объектов** щелкните имя сервера, чтобы развернуть этот узел.  
  
2.  Раскройте узел **Базы данных**и выберите базу данных для перехода на другой ресурс.  
  
3.  Щелкните базу данных правой кнопкой мыши, выберите **Задачи**, а затем **Зеркальное отображение**. Откроется страница **Зеркальное отображение** диалогового окна **Свойства базы данных** .  
  
4.  Щелкните **Отработка отказа**.  
  
     Появится окно подтверждения.  Основной сервер начинает работу с подключения к зеркальному серверу, используя проверку подлинности Windows. Если проверка подлинности Windows не работает, основной сервер выводит диалоговое окно **Соединение с сервером** . Если зеркальный сервер использует проверку подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , выберите вариант **Проверка подлинности SQL Server** в поле **Проверка подлинности** . Укажите в текстовом поле **Имя входа** учетную запись входа, с которой устанавливается соединения на зеркальном сервере, а в текстовом поле **Пароль** — пароль для этой учетной записи.  
  
     Если отработка отказа выполняется успешно, диалоговое окно **Свойства базы данных** закрывается. Зеркальная база данных становится основной базой данных, а основная — зеркальной.  
  
     При ошибке отработки отказа отображается сообщение об ошибке и диалоговое окно останется открытым.  
  
    > [!IMPORTANT]  
    >  Если с момента открытия страницы **Зеркальное отображение** были изменены какие-либо свойства, эти изменения не будут сохранены.  
  
     Диалоговое окно закрывается автоматически.  
  
## <a name="see-also"></a>См. также:  
 [Свойства базы данных (страница "Зеркальное отображение")](../../relational-databases/databases/database-properties-mirroring-page.md)   
 [Зеркальное отображение базы данных (SQL Server)](../../database-engine/database-mirroring/database-mirroring-sql-server.md)   
 [Переключение сеанса зеркального отображения базы данных на другой ресурс вручную (язык Transact-SQL)](../../database-engine/database-mirroring/manually-fail-over-a-database-mirroring-session-transact-sql.md)   
 [Приостановка или возобновление сеанса зеркального отображения базы данных (SQL Server)](../../database-engine/database-mirroring/pause-or-resume-a-database-mirroring-session-sql-server.md)   
 [Удаление зеркального отображения базы данных (SQL Server)](../../database-engine/database-mirroring/remove-database-mirroring-sql-server.md)  
  
  
