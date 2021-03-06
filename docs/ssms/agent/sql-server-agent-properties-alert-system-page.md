---
title: Свойства агента SQL Server (страница «Система предупреждений»)
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.agent.alert.f1
ms.assetid: 3e6d3bfd-20ee-4593-86cc-f65b1c08c69d
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 17ecd6435258e255538cfedc345a835610f55a97
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85755165"
---
# <a name="sql-server-agent-properties-alert-system-page"></a>Свойства агента SQL Server (страница «Система предупреждений»)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Эта страница используется для просмотра и изменения параметров сообщений, отправляемых предупреждениями агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="options"></a>Параметры  
**Почтовый сеанс**  
Параметры в данном разделе предназначены для настройки почты агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
**Включить почтовый профиль**  
Включает почту агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . По умолчанию почта агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не включена.  
  
**Почтовая система**  
Устанавливает почтовую систему для использования агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Database Mail  
  
> [!NOTE]  
> После изменений системы электронной почты необходимо перезапустить службу агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , чтобы эти изменения вступили в силу.  
  
**Профиль электронной почты**  
Устанавливает профиль для использования агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Можно также выбрать **\<new Database Mail profile...>** , чтобы создать новый профиль.  
  
**Электронные сообщения на пейджер**  
Параметры в этом разделе позволяют настроить электронные сообщения, отправляемые на адреса пейджеров для работы с вашей пейджинговой системой.  
  
**Форматирование адреса для электронных сообщений на пейджер**  
Данный раздел позволяет задать формат адресов и темы, включаемые в электронные сообщения на пейджер.  
  
**Поле «Кому»**  
Задает параметры для строки сообщения **Кому** .  
  
**Prefix**  
Введите любой фиксированный текст, требуемый системой в начале строки **Кому** сообщений, отправляемых на пейджер.  
  
**Пейджер**  
Содержит адрес электронной почты для сообщения между префиксом и суффиксом.  
  
**Суффикс**  
Введите любой фиксированный текст, требуемый пейджинговой системой в конце строки **Кому** сообщений, отправляемых на пейджер.  
  
**Поле «Копия»**  
Задает параметры для строки сообщения **Копия** .  
  
**Prefix**  
Введите любой фиксированный текст, требуемый системой в начале строки **Копия** сообщений, отправляемых на пейджер.  
  
**Пейджер**  
Содержит адрес электронной почты для сообщения между префиксом и суффиксом.  
  
**Суффикс**  
Введите любой фиксированный текст, требуемый пейджинговой системой в конце строки **Копия** сообщений, отправляемых на пейджер.  
  
**Тема**  
Задает параметры для строки темы сообщения.  
  
**Prefix**  
Введите любой фиксированный текст, требуемый системой в начале строки **Тема** сообщений, отправляемых на пейджер.  
  
**Суффикс**  
Введите любой фиксированный текст, требуемый системой в конце строки **Тема** сообщений, отправляемых на пейджер.  
  
**Включить тело электронного письма в сообщение уведомления**  
Включает тело электронного письма в сообщение, отправляемое на пейджер.  
  
**Резервный оператор**  
Данный раздел позволяет задать параметры для резервного оператора.  
  
**Включить резервный оператор**  
Задает резервный оператор.  
  
**Оператор**  
Устанавливает имя оператора для получения уведомлений об отказах.  
  
**Уведомлять с помощью**  
Устанавливает метод для использования при уведомлении резервного оператора.  
  
**Замена токенов**  
Данный раздел позволяет включить токены шагов заданий, которые могут использоваться в заданиях, выполняемых предупреждениями агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения о токенах шагов заданий см. в разделе [Использование токенов в шагах задания](../../ssms/agent/use-tokens-in-job-steps.md).  
  
> [!IMPORTANT]  
> Все пользователи Windows с разрешением на запись в журнал событий Windows могут получить доступ к шагам заданий, которые активированы предупреждениями агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Чтобы избежать этого нарушения безопасности, в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] токены агента, которые могут использоваться в заданиях, активированных предупреждениями, по умолчанию отключены. К этим токенам относятся: **$(A-DBN)** , **$(A-SVR)** , **$(A-ERR)** , **$(A-SEV)** и **$(A-MSG)** .  
>   
> При необходимости использовать эти токены перед их включением убедитесь, что только члены доверенных групп безопасности Windows, таких как группа «Администраторы», обладают разрешением на работу с журналом событий компьютера, на котором находится [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
**Заменить токенами всех ответов заданий на предупреждения**  
Установите этот флажок, чтобы включить замену токенов для заданий, активизированных предупреждениями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>См. также:  
[Операторы](../../ssms/agent/operators.md)  
[Настройка почты агента SQL Server на использование компонента Database Mail](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)  
[Database Mail](../../relational-databases/database-mail/database-mail.md)  
  
