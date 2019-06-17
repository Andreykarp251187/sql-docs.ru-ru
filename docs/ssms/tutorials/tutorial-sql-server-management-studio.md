---
title: Руководство. SQL Server Management Studio (SSMS) | Документация Майкрософт
ms.custom: sqlfreshmay19
ms.date: 05/14/2019
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: sstein
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.tutorialstart.ssms.f1
helpviewer_keywords:
- projects [SQL Server Management Studio], tutorials
- templates [SQL Server], SQL Server Management Studio
- source controls [SQL Server Management Studio], tutorials
- Help [SQL Server], SQL Server Management Studio
- tutorials [SQL Server Management Studio]
- Transact-SQL tutorials
- solutions [SQL Server Management Studio], tutorials
- SQL Server Management Studio [SQL Server], tutorials
- scripts [SQL Server], SQL Server Management Studio
ms.assetid: d2bade70-07cf-4d94-b5d2-88aecb538ed1
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: bf2776df77af8f4ba5fec9595d6ba9cddf927f7a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65620511"
---
# <a name="tutorials-for-sql-server-management-studio-ssms"></a>Учебники по SQL Server Management Studio (SSMS)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

В руководстве по SQL Server Management Studio (SSMS) описана интегрированная среда для управления инфраструктурой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] представляет собой графический интерфейс для настройки, отслеживания и администрирования Базы данных Azure SQL, Управляемого экземпляра Базы данных Azure SQL, Хранилища данных SQL Azure и экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Среда также позволяет развертывать, отслеживать и обновлять компоненты уровня данных, используемые приложениями, например базами данных. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] также предоставляет редакторы [!INCLUDE[tsql](../../includes/tsql-md.md)], языка многомерных выражений, расширений интеллектуального анализа данных и XML для изменения и отладки скриптов.  
  
## <a name="what-you-will-learn"></a>Обзор учебника  

Эти учебники помогут вам понять принципы представления информации в SSMS и расскажут, как эффективно использовать возможности этой среды.
  
Лучший способ познакомиться с SSMS — это поработать в среде самостоятельно. В этих учебниках вы ознакомитесь с различными функциями, доступными в среде SSMS.  С их помощью вы научитесь работать с компонентами SSMS и легко находить регулярно используемые функции.  

В учебниках рассматриваются следующие темы:


- [Учебник. Подключение и отправка запроса к SQL Server с помощью SQL Server Management Studio](connect-query-sql-server.md)

    Из этого учебника вы узнаете, как подключиться к экземпляру SQL Server. Вы также ознакомитесь с некоторыми основными командами Transact-SQL (T-SQL) для создания базы данных и выполнения запросов к ней. 

- [Учебник. Написание скриптов для объектов в SSMS](scripting-ssms.md)

    Из этого учебника вы узнаете, как создавать скрипты для различных объектов в среде SSMS, включая базы данных и запросы. 

- [Учебник. Использование шаблонов в SSMS](templates-ssms.md)
   
    Из этого учебника вы узнаете, как работать с готовыми шаблонами в среде SSMS. Шаблоны — это малоизвестный компонент, в котором хранится ряд фрагментов кода Transact-SQL для разных задач администрирования баз данных. 

- [Учебник. Конфигурация SSMS](ssms-configuration.md)

    Из этого учебника вы узнаете основы настройки среды SSMS, например изменение структуры среды. В нем также описываются разные компоненты SSMS. 
  

- [Учебник. Дополнительные советы и рекомендации по использованию SSMS](ssms-tricks.md)

    В этом руководстве представлены дополнительные советы и рекомендации по использованию среды SSMS. Учебник включает следующее:
    - закомментирование и раскомментирование текста;
    - добавление отступов в тексте;
    - фильтрация объектов в обозревателе объектов;
    - доступ к журналу ошибок SQL Server;
    - определение имени экземпляра. 
 
  
## <a name="requirements"></a>Требования  
Учебник предназначен для опытных администраторов и разработчиков баз данных, незнакомых с [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], но знакомых с основными понятиями баз данных и языком [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
Для работы с учебником в системе должны быть установлены следующие компоненты:  

  -   Последняя версия [SQL Server Management Studio (SSMS)](../download-sql-server-management-studio-ssms.md).  

В первом разделе приводятся пошаговые инструкции по созданию базы данных. Образцы баз данных можно также найти на странице [Образцы баз данных AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases). Инструкции по восстановлению баз данных в SSMS можно найти в статье [Восстановление базы данных](https://docs.microsoft.com/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms). 


  
## <a name="see-also"></a>См. также:  
[Учебники по компоненту ядра СУБД](../../relational-databases/database-engine-tutorials.md)          
  
  
  

