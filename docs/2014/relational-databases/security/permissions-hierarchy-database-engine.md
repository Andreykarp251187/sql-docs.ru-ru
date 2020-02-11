---
title: Иерархия разрешений (ядро СУБД) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.server.permissions.f1--May use common.permissions
helpviewer_keywords:
- security [SQL Server], denying access
- hierarchies [SQL Server], permissions
- securables [SQL Server]
- security [SQL Server], permissions
- permissions [SQL Server], hierarchy
- security [SQL Server], granting access
ms.assetid: f6d20a55-ef03-4e14-85f9-009902889866
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 05cc0d47053d8ddef0962c4aceee75e61b8b4b64
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68211953"
---
# <a name="permissions-hierarchy-database-engine"></a>Иерархия разрешений (компонент Database Engine)
  Компонент [!INCLUDE[ssDE](../../../includes/ssde-md.md)] управляет иерархической коллекцией сущностей, защита которых производится при помощи разрешений. Эти сущности называются *защищаемыми объектами*. Важнейшими защищаемыми компонентами являются серверы и базы данных, однако отдельные разрешения можно задавать на гораздо более глубоком уровне. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] регулирует действия участников на защищаемых объектах, проверяя, что им были предоставлены соответствующие разрешения.  
  
 На следующей иллюстрации показана связь между иерархиями разрешений компонента [!INCLUDE[ssDE](../../../includes/ssde-md.md)] .  
  
 ![Диаграмма иерархий разрешений компонента Database Engine](../../database-engine/media/wj-security-layers.gif "Диаграмма иерархий разрешений компонента Database Engine")  
  
## <a name="chart-of-sql-server-permissions"></a>Диаграмма разрешений SQL Server  
 Для получения диаграммы с размером афиши [!INCLUDE[ssDE](../../../includes/ssde-md.md)] всех разрешений в формате PDF см [https://go.microsoft.com/fwlink/?LinkId=229142](https://go.microsoft.com/fwlink/?LinkId=229142). раздел.  
  
## <a name="working-with-permissions"></a>Работа с разрешениями  
 Выполнение различных действий с разрешениями осуществляется при помощи обычных запросов [!INCLUDE[tsql](../../includes/tsql-md.md)] : GRANT, DENY и REVOKE. Сведения о разрешениях доступны через представления каталога [sys.server_permissions](/sql/relational-databases/system-catalog-views/sys-server-permissions-transact-sql) и [sys.database_permissions](/sql/relational-databases/system-catalog-views/sys-database-permissions-transact-sql) . Существует также поддержка запроса сведений о разрешениях при помощи встроенных функций.  
  
## <a name="see-also"></a>См. также:  
 [Защита SQL Server](securing-sql-server.md)   
 [Разрешения &#40;ядро СУБД&#41;](permissions-database-engine.md)   
 [Защищаемые объекты](securables.md)   
 [Участники &#40;ядро СУБД&#41;](authentication-access/principals-database-engine.md)   
 [ПРЕДОСТАВЛЕНИЕ &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql)   
 [ОТОЗВАТЬ &#40;Transact-SQL&#41;](/sql/t-sql/statements/revoke-transact-sql)   
 [DENY &#40;&#41;Transact-SQL](/sql/t-sql/statements/deny-transact-sql)   
 [HAS_PERMS_BY_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/has-perms-by-name-transact-sql)   
 [sys. fn_builtin_permissions &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql)   
 [sys. server_permissions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-permissions-transact-sql)   
 [sys. database_permissions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-permissions-transact-sql)  
  
  
