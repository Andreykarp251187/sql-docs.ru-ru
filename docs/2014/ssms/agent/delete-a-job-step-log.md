---
title: Удаление журнала шага задания | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- job steps [SQL Server Agent]
- deleting job step logs
- logs [SQL Server], jobs
- removing job step logs
ms.assetid: ee20c6cd-0258-4550-bdb0-71e86a0fb330
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 945c403a44f2b0c2cf2d691a1bcfda6cc96d422b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62523750"
---
# <a name="delete-a-job-step-log"></a>Удаление журнала шага задания
  В этом разделе описывается, как удалить журнал шага задания агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   **Перед началом:**  
  
     [Ограничения](#Restrictions)  
  
     [безопасность](#Security)  
  
-   **Для удаления журнала шага задания агента SQL Server используется:**  
  
     [Среда SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [Управляющие объекты SQL Server](#SMO)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
 При удалении шагов задания автоматически удаляются их выходные журналы.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Если пользователь не является членом предопределенной роли сервера **sysadmin** , он может изменять только свои собственные задания.  
  
##  <a name="SSMS"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-delete-a-sql-server-agent-job-step-log"></a>Удаление журнала шага задания агента SQL Server  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]и разверните его.  
  
2.  Разверните узел **Агент SQL Server**, выберите раздел **Задания**, щелкните правой кнопкой мыши задание, которое нужно изменить, и выберите пункт **Свойства**.  
  
3.  В диалоговом окне **Свойства задания** удалите выбранный шаг задания.  
  
##  <a name="TSQL"></a> Использование Transact-SQL  
  
#### <a name="to-delete-a-sql-server-agent-job-step-log"></a>Удаление журнала шага задания агента SQL Server  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- removes the job step log for step 2 in the job Weekly Sales Data Backup  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_delete_jobsteplog  
        @job_name = N'Weekly Sales Data Backup',  
        @step_id = 2;  
    GO  
    ```  
  
 Дополнительные сведения см. в разделе [sp_delete_jobsteplog &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-jobsteplog-transact-sql).  
  
##  <a name="SMO"></a> Использование управляющих объектов SQL Server  
 Вызовите методы `DeleteJobStepLogs` класса `Job`, используя выбранный язык программирования, например Visual Basic, Visual C# или PowerShell. Дополнительные сведения см. в разделе[Управляющие объекты SQL Server](https://msdn.microsoft.com/library/ms162169.aspx).  
  
```  
-- Uses PowerShell to delete all job step log files that have ID values larger than 5.  
$srv = new-object Microsoft.SqlServer.Management.Smo.Server("(local)")  
$jb = $srv.JobServer.Jobs["Test Job"]  
$jb.DeleteJobStepLogs(5)  
```  
  
  
