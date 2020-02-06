---
title: Свойство базы данных TRUSTWORTHY | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: security
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- TRUSTWORTHY database property
ms.assetid: 64b2a53d-4416-4a19-acc0-664a61b45348
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: ec745810697b325b8f1e1b2d5e67871136b9f089
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68126823"
---
# <a name="trustworthy-database-property"></a>Свойство базы данных TRUSTWORTHY
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Свойство TRUSTWORTHY используется для указания того, доверяет ли экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базе данных и ее содержимому. По умолчанию это свойство имеет значение OFF, но его можно установить в ON при помощи инструкции ALTER DATABASE. Например, `ALTER DATABASE AdventureWorks2012 SET TRUSTWORTHY ON;`.  
  
> [!NOTE]  
>  Изменять это свойство могут только члены предопределенной роли сервера **sysadmin** .  
  
 Это свойство позволяет уменьшить уязвимость системы перед рядом угроз, связанных с присоединением базы данных, содержащей один из следующих объектов:  
  
-   вредоносные сборки с параметром разрешения EXTERNAL_ACCESS или UNSAFE. Дополнительные сведения см. в статье [CLR Integration Security](../../relational-databases/clr-integration/security/clr-integration-security.md).  
  
-   вредоносные модули, выполняемые в контексте привилегированных пользователей. Дополнительные сведения см. в разделе [Предложение EXECUTE AS (Transact-SQL)](../../t-sql/statements/execute-as-clause-transact-sql.md).  
  
 В обеих ситуациях объектам нужны конкретные права доступа, что повышает уязвимость системы. Для защиты от атак при использовании таких объектов в контексте базы данных, уже присоединенной к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], применяют соответствующие механизмы. Однако, если база данных переведена в режим работы «вне сети», пользователь, имеющий доступ к файлу базы данных, теоретически может присоединить ее к любому экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и добавить в нее вредоносное содержимое. Когда в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]отсоединяются и присоединяются базы данных, для файлов данных и журналов задаются определенные разрешения, ограничивающие доступ к файлам базы данных.  
  
 Так как база данных, присоединенная к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , не может сразу стать доверенной, то ей не разрешается доступ к ресурсам вне ее области до тех пор, пока не будет явно отмечена как доверенная. Таким образом, если вы создаете резервную копию базы данных или отсоединяете базу данных, параметру TRUSTWORTHY которой задано значение ON, и затем присоединяете или восстанавливаете базу данных на том же или другом экземпляре SQL Server, после присоединения или восстановления параметр TRUSTWORTHY будет иметь значение OFF. Для успешного выполнения модулей, которые обращаются к ресурсам, внешним по отношению к базе данных, и сборок с параметром разрешения EXTERNAL_ACCESS или UNSAFE нужно, чтобы были удовлетворены кое-какие дополнительные требования.  
  
## <a name="related-content"></a>См. также  
 [Центр безопасности для ядра СУБД SQL Server и Базы данных Azure SQL](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)  
  
  
