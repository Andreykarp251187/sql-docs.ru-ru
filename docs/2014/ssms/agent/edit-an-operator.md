---
title: Изменение оператора | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- modifying operators
- jobs [SQL Server Agent], operators
- operators (users) [Database Engine], modifying with Management Studio
ms.assetid: b2ba2168-ca0b-4b59-9007-4e1e4c30679e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9ee3228eea9970563540be9bc6a4c3b9a3677112
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68189327"
---
# <a name="edit-an-operator"></a>Изменение оператора
  В этом разделе описано, как изменить доступность операторов к получению уведомлений, а также для них адрес электронной почты, номер пейджера и адрес net send в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [безопасность](#Security)  
  
-   **Изменение данных оператора с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Режимы отправки уведомлений с помощью пейджера и команды **net send** будут удалены из агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в следующей версии [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Старайтесь не использовать эти функции в новых разработках и предусмотрите соответствующие изменения в приложениях, которые используют их в настоящее время.  
  
-   Обратите внимание, что для использования компонента Database Mail для отправки операторам уведомлений по электронной почте и на пейджер агент SQL Server необходимо настроить для использования компонента Database Mail. Дополнительные сведения см. в разделе [Назначить предупреждения для оператора](assign-alerts-to-an-operator.md).  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] обеспечивает доступный графический способ управления заданиями и рекомендуется для создания и управления инфраструктурой заданий.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Изменять данные операторов могут указывать только члены предопределенной роли сервера **sysadmin** .  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-edit-an-operator"></a>Редактирование данных оператора  
  
1.  В **обозревателе объектов**щелкните значок «плюс», чтобы развернуть сервер, содержащий оператора, данные которого нужно изменить.  
  
2.  Щелкните знак "плюс", чтобы развернуть **Агент SQL Server**.  
  
3.  Щелкните значок «плюс», чтобы развернуть папку **Операторы** .  
  
4.  Щелкните правой кнопкой оператора, данные которого нужно изменить, и выберите пункт **Свойства**.  
  
     Дополнительные сведения о доступных параметрах, содержащихся в диалоговом окне _Свойства_**имя_оператора** , см. в разделе:  
  
    -   [Свойства оператора и оператора New &#40;страница "Общие"&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)  
  
    -   [Свойства оператора: Оператор New &#40;страница "уведомления"&#41;](operator-properties-new-operator-notifications-page.md)  
  
    -   [Свойства оператора (страница "Журнал")](operator-properties-history-page.md)  
  
5.  После завершения нажмите кнопку **ОК**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-edit-an-operator"></a>Редактирование данных оператора  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- updates the operator status to enabled, and sets the days   
    -- (from Monday through Friday, from 8 A.M. through 5 P.M.) when the operator can be paged.   
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_operator   
        @name = N'Fran??ois Ajenstat',  
        @enabled = 1,  
        @email_address = N'fran??oisa',  
        @pager_address = N'5551290AW@pager.Adventure-Works.com',  
        @weekday_pager_start_time = 080000,  
        @weekday_pager_end_time = 170000,  
        @pager_days = 64 ;  
    GO  
    ```  
  
 Дополнительные сведения см. в разделе [sp_update_operator &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-operator-transact-sql).  
  
  
