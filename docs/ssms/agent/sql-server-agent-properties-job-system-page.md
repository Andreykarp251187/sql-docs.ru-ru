---
title: Свойства агента SQL Server (страница "Система заданий") | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.agent.job.f1
ms.assetid: e171d13e-1302-4f0e-88be-67d656aec8d3
author: markingmyname
ms.author: maghan
manager: jroth
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 2da80fa6ba2e8b28c91b8750e4515acaa6b1cddc
ms.sourcegitcommit: 5d839dc63a5abb65508dc498d0a95027d530afb6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2019
ms.locfileid: "67681788"
---
# <a name="sql-server-agent-properties-job-system-page"></a>Свойства агента SQL Server (страница «Система заданий»)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Эта страница предназначена для просмотра и изменения того, каким образом служба агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] управляет заданиями.  
  
## <a name="options"></a>Параметры  
**Время ожидания при завершении работы (в секундах)**  
Указывает число секунд, в течение которых агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ожидает завершения заданий при окончании работы. Если отведенное время истекло, а задание так и не завершилось, агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] принудительно его останавливает.  
  
**Использовать неадминистративную учетную запись-посредник**  
Задает неадминистративную учетную запись-посредник для агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)] и более поздние версии поддерживают несколько учетных записей-посредников, и поэтому этот параметр применим только в случае работы с версиями агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ранее [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)].  
  
**User name**  
Введите имя пользователя для неадминистративной учетной записи-посредника. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает несколько учетных записей-посредников, и поэтому этот параметр применим только в случае работы с версиями агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ранее [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)].  
  
**Пароль**  
Введите пароль пользователя для неадминистративной учетной записи-посредника. [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздние версии поддерживают несколько учетных записей-посредников, и поэтому этот параметр применим только в случае работы с версиями агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ранее [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
**Домен**  
Введите домен пользователя для неадминистративной учетной записи-посредника. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает несколько учетных записей-посредников, и поэтому этот параметр применим только в случае работы с версиями агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ранее [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)].  
  
## <a name="see-also"></a>См. также:  
[Реализация заданий](../../ssms/agent/implement-jobs.md)  
  
