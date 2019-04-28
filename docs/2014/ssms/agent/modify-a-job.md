---
title: Изменение задания | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], modifying
- modifying jobs
- SQL Server Agent jobs, modifying
ms.assetid: dd5e5f20-20c4-4ab9-a19a-db87577dcd43
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 614c35992be2f85ef15afd0645140746041d083d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62656387"
---
# <a name="modify-a-job"></a>Изменение задания
  В этом разделе описано, как изменять свойства заданий агента [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью среды [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]или управляющих объектов SQL Server.  
  
 **В этом разделе**  
  
-   **Перед началом работы**   
  
     [Ограничения](#Restrictions)  
  
     [безопасность](#Security)  
  
-   **Для изменения задания используется:**  
  
     [Среда SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [Управляющие объекты SQL Server](#SMO)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
 Главное задание агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не может быть ориентировано как на локальный, так и на удаленный сервер.  
  
###  <a name="Security"></a> безопасность  
 Если пользователь не является членом предопределенной роли сервера **sysadmin** , он может изменять только свои собственные задания. Дополнительные сведения см. в разделе [Обеспечение безопасности агента SQL Server](implement-sql-server-agent-security.md).  
  
##  <a name="SSMS"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-modify-a-job"></a>Изменение задания  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]и разверните его.  
  
2.  Разверните узел **Агент SQL Server**, выберите раздел **Задания**, щелкните правой кнопкой мыши задание, которое нужно изменить, и выберите пункт **Свойства**.  
  
3.  В диалоговом окне **Свойства задания** обновите свойства, шаги, расписание, предупреждения и уведомления задания, воспользовавшись соответствующими страницами.  
  
##  <a name="TSQL"></a> Использование Transact-SQL  
  
#### <a name="to-modify-a-job"></a>Изменение задания  
  
1.  В обозревателе объектов подключитесь к экземпляру компонента Database Engine и разверните его.  
  
2.  На панели инструментов нажмите кнопку **Создать запрос**.  
  
3.  В окне запроса используйте следующие системные хранимые процедуры для изменения задания.  
  
    -   Выполнение [sp_update_job &#40;Transact-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql) Чтобы изменить атрибуты задания.  
  
    -   Выполнение [sp_update_schedule &#40;Transact-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-update-schedule-transact-sql) на изменение параметров расписания для определения задания.  
  
    -   Выполнение [sp_add_jobstep &#40;Transact-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql) Чтобы добавить новые шаги к заданию.  
  
    -   Выполнение [sp_update_jobstep &#40;Transact-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql) Чтобы изменить существующие шаги задания.  
  
    -   Выполнение [sp_delete_jobstep &#40;Transact-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql) удалить шаг задания из задания.  
  
    -   Дополнительные хранимые процедуры для изменения любого главного задания агента SQL Server.  
  
        -   Выполнение [sp_delete_jobserver &#40;Transact-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql) для удаления сервера, связанного с заданием.  
  
        -   Выполнение [sp_add_jobserver &#40;Transact-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql) связывание сервера с текущим заданием.  
  
##  <a name="SMO"></a> Использование управляющих объектов SQL Server  
 **Изменение задания**  
  
 Воспользуйтесь классом `Job` в любом языке программирования (Visual Basic, Visual C# или PowerShell). Дополнительные сведения см. в статье [Управляющие объекты SQL Server (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).  
  
  
