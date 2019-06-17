---
title: Передача другим пользователям права владения заданием | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], owners
- owners [SQL Server], jobs
- SQL Server Agent jobs, owners
ms.assetid: 2ded5e9c-4251-4fb1-a047-99f13d150b61
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f22d153d55674d5dd615ab50848e4a7fd85a6dcb
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63075265"
---
# <a name="give-others-ownership-of-a-job"></a>Give Others Ownership of a Job
  В этом разделе описано, как изменить владельца заданий агента [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   **Перед началом:**  [Ограничения](#Restrictions), [Безопасность](#Security)  
  
-   **Для передачи другим пользователям права владения заданием используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProc2)  
  
     [Transact-SQL](#TsqlProc2)  
  
     [Управляющие объекты SQL Server](#SMOProc2)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
 Чтобы создать задание, пользователь должен быть членом одной из предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или членом предопределенной роли сервера **sysadmin** . Задание может быть изменено его владельцем или членом роли **sysadmin** . Дополнительные сведения о предопределенных ролях базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе [Предопределенные роли базы данных агента SQL Server](sql-server-agent-fixed-database-roles.md).  
  
 Чтобы изменить владельца задания, необходимо быть системным администратором.  
  
 Назначение задания другому имени входа не гарантирует того, что новый владелец обладает достаточными разрешениями для успешного запуска задания.  
  
###  <a name="Security"></a> безопасность  
 Из соображений безопасности изменять определение задания может только его владелец или член роли **sysadmin** . Только члены предопределенной роли сервера **sysadmin** могут предоставлять права владения заданием другим пользователям, а также могут запускать любое задание, независимо от того, кто является его владельцем.  
  
> [!NOTE]  
>  Если задать в качестве нового владельца задания пользователя, не являющегося членом предопределенной роли сервера **sysadmin** , а задание выполняет шаги, которым требуются учетные записи-посредники (например, выполнение пакета служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] ), убедитесь в том, что пользователь имеет доступ к этой учетной записи-посреднику, в противном случае задание завершится ошибкой.  
  
####  <a name="Permissions"></a> Permissions  
 Дополнительные сведения см. в разделе [Обеспечение безопасности агента SQL Server](implement-sql-server-agent-security.md).  
  
##  <a name="SSMSProc2"></a> Использование среды SQL Server Management Studio  
 **Передача другим пользователям права владения заданием**  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]и разверните его.  
  
2.  Разверните **Агент SQL Server**, **Задания**, затем щелкните правой кнопкой мыши задание и выберите пункт **Свойства**.  
  
3.  В списке **Владелец** выберите имя входа. Чтобы изменить владельца задания, необходимо быть системным администратором.  
  
     Назначение задания другому имени входа не гарантирует того, что новый владелец обладает достаточными разрешениями для успешного запуска задания.  
  
##  <a name="TsqlProc2"></a> Использование Transact-SQL  
 **Передача другим пользователям права владения заданием**  
  
1.  В обозревателе объектов подключитесь к экземпляру компонента Database Engine и разверните его.  
  
2.  На панели инструментов нажмите кнопку **Создать запрос**.  
  
3.  В окне запроса введите следующие инструкции, использующие [sp_manage_jobs_by_login &#40;Transact-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-manage-jobs-by-login-transact-sql) системной хранимой процедуры. В следующем примере производится передача всех заданий от пользователя `danw` пользователю `fran??oisa`.  
  
    ```  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_manage_jobs_by_login  
        @action = N'REASSIGN',  
        @current_owner_login_name = N'danw',  
        @new_owner_login_name = N'fran??oisa' ;  
    GO  
    ```  
  
##  <a name="SMOProc2"></a> Использование управляющих объектов SQL Server  
 **Передача другим пользователям права владения заданием**  
  
1.  Вызовите класс `Job` с использованием выбранного языка программирования, например Visual Basic, Visual C# или PowerShell. Пример кода см. в разделе [Планирование автоматических административных задач в агенте SQL Server](sql-server-agent.md).  
  
## <a name="see-also"></a>См. также  
 [Реализация заданий](implement-jobs.md)   
 [Создание заданий](create-jobs.md)  
  
  
