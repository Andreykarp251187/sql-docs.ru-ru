---
title: Создание расписания | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- scheduling jobs [SQL Server]
- SQL Server Agent jobs, scheduling
- jobs [SQL Server Agent], scheduling
- schedules [SQL Server], jobs
ms.assetid: 8c7ef3b3-c06d-4a27-802d-ed329dc86ef3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a00b07bb54d30d4e1db49cf2db70dec8286b27e0
ms.sourcegitcommit: f912c101d2939084c4ea2e9881eb98e1afa29dad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2019
ms.locfileid: "72798294"
---
# <a name="create-a-schedule"></a>Создание расписания
  Расписание для заданий агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] вы можете создать с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]или управляющих объектов SQL Server.  
  
-   **Перед началом:**  
  
     [безопасность](#Security)  
  
-   **Для создания расписания используется:**  
  
     [Среда Среда SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [Управляющие объекты SQL Server](#SMO)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
 Дополнительные сведения см. в разделе [Обеспечение безопасности агента SQL Server](implement-sql-server-agent-security.md).  
  
##  <a name="SSMS"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-create-a-schedule"></a>Создание расписания  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]и разверните его.  
  
2.  Разверните узел **Агент SQL Server**, щелкните правой кнопкой мыши узел **Задания**и выберите **Управление расписаниями**.  
  
3.  В диалоговом окне **Управление расписаниями** щелкните **Создать**.  
  
4.  В поле **Имя** введите имя нового расписания.  
  
5.  Если не нужно, чтобы расписание вступило в силу немедленно после создания, снимите флажок **Включено** .  
  
6.  Выберите одно из следующих значений для параметра **Тип расписания**:  
  
    -   Чтобы запускать задание, когда процессоры переходят в состояние бездействия, щелкните **Запускать при бездействии процессоров**.  
  
    -   Если необходимо периодическое выполнение расписания, выберите пункт **Повторяющееся задание**. Затем в диалоговом окне заполните группы **Частота**, **Сколько раз в день**и **Продолжительность** .  
  
    -   Если планируется однократное выполнение, выберите **Один раз**. Для установки расписания **Один раз** заполните в диалоговом окне группу **Однократное выполнение** .  
  
##  <a name="TSQL"></a> Использование Transact-SQL  
  
#### <a name="to-create-a-schedule"></a>Создание расписания  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```sql
    -- creates a schedule named RunOnce.   
    -- The schedule runs one time, at 23:30 on the day that the schedule is created.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_schedule  
        @schedule_name = N'RunOnce',  
        @freq_type = 1,  
        @active_start_time = 233000 ;  
  
    GO  
    ```  
  
 Дополнительные сведения см. в [разделе &#40;SP_ADD_SCHEDULE Transact-&#41;SQL](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql).  
  
##  <a name="SMO"></a>Использование управляющие объекты SQL Server  
 **Создание расписания**  
  
 Воспользуйтесь классом `JobSchedule` в любом языке программирования (Visual Basic, Visual C# или PowerShell). Дополнительные сведения см. в статье [Управляющие объекты SQL Server (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).  
