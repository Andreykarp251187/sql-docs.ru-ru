---
title: Свойства созданного оператора (страница "Общие")
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.operator.general.f1
ms.assetid: c036d1c9-83d1-4a95-b67e-29d283b1a046
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 7f59aa6f41d1de3dc8bf4fa2aa0451af7ab76f34
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85715689"
---
# <a name="operator-properties---new-operator-general-page"></a>Свойства оператора — создание оператора (страница "Общие")

[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Используйте эту страницу для просмотра и изменения общих свойств операторов агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="options"></a>Параметры  
**Название**  
Изменить имя оператора.  
  
**Enabled**  
Разрешить оператор. Если он не включен, то уведомления оператору не отправляются.  
  
**Имя для электронной почты**  
Определяет адрес электронной почты оператора.  
  
**Адрес для команды net send**  
Задает адрес, используемый для **net send**.  
  
**Имя для сообщения на пейджер**  
Определяет адрес электронной почты пейджера оператора.  
  
**Расписание работы для пейджера**  
Указывает время, когда пейджер активен.  
  
**Понедельник — воскресенье**  
Выберите дни, когда пейджер активен.  
  
**Начало рабочего дня**  
Выберите время суток, после которого агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отправляет сообщения на пейджер.  
  
**Конец рабочего дня**  
Выберите время суток, после которого агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] перестает отправлять сообщения на пейджер.  
  
## <a name="see-also"></a>См. также:  
[Операторы](../../ssms/agent/operators.md)  
  
