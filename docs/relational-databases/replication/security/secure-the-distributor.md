---
description: Организация безопасности распространителя
title: Организация безопасности распространителя | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- security [SQL Server replication], Distributors
- Distributors [SQL Server replication], security
ms.assetid: 76d78229-0ff2-4aa4-9b4e-ad97534c5296
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 0e0a8a7e42259553e2748d2e323b0322a877f01c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88405030"
---
# <a name="secure-the-distributor"></a>Организация безопасности распространителя
[!INCLUDE[sql-asdbmi](../../../includes/applies-to-version/sql-asdbmi.md)]
  К распространителю подключаются следующие агенты репликации: агент чтения журнала, агент моментальных снимков, агент чтения очереди, агент распространителя и агент слияния. Важно обеспечить для каждого из этих агентов соответствующее имя входа, соблюдая при этом принцип предоставления минимальных необходимых прав, а также защищая хранилище всех паролей:  
  
-   Сведения об управлении именами для входа и паролями см. в статье [Управление именами для входа и паролями при репликации](../../../relational-databases/replication/security/identity-and-access-control-replication.md).  
  
-   Дополнительные сведения о разрешениях, необходимых каждому агенту, см. в разделе [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md).  
  
 В дополнение к надлежащему управлению именами входа и паролями важно понимать роль канала связи с удаленным сервером **repl_distributor** и учетной записи **distributor_admin** .  
  
## <a name="securing-the-connection-from-the-publisher-to-the-distributor"></a>Защита соединения издателя с распространителем  
 Система репликации автоматически настраивает удаленный сервер **repl_distributor**для поддержания связи, необходимой при выполнении административных хранимых процедур на издателе и при обновлении данных на распространителе. Запись удаленного сервера **repl_distributor** используется для связи с базой данных распространителя вне зависимости от того, содержится ли эта база данных на экземпляре издателя (локальный распространитель) или находится на удаленном экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (удаленный распространитель).  
  
 Когда база данных распространителя содержится на локальном экземпляре, формируется и автоматически настраивается случайный пароль. Когда база данных распространителя находится на удаленном экземпляре сервера, администратор настраивает общий пароль при настройке издателя и распространителя; в дальнейшем этот пароль используется для проверки подлинности трафика, проходящего через канал связи с сервером **repl_distributor** .  
  
 Распространитель использует запись удаленного сервера **repl_distributor** , чтобы удостовериться в том, что удаленный сервер настроен на распространителе как издатель, проверяет пароль, предъявляемый издателем, а во время выполнения хранимой процедуры проверяет, что это — хранимая процедура репликации.  
  
 Пароль, устанавливаемый для записи удаленного сервера **repl_distributor** при первоначальной настройке, связан с именем входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , **distributor_admin**, добавляемым к предопределенной роли сервера **sysadmin** на распространителе. Имя входа **distributor_admin** используется хранимыми процедурами репликации при подключении к распространителю.  
  
> [!NOTE]  
>  Не меняйте пароль для имени **distributor_admin** вручную. Всегда пользуйтесь хранимой процедурой **sp_changedistributor_password** или диалоговыми окнами **Свойства распространителя** и **Обновление паролей репликации** в среде [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], потому что в этом случае изменения паролей применяются к локальным публикациям автоматически.  
  
## <a name="snapshot-folder-security"></a>Безопасность папки моментальных снимков  
 Убедитесь в том, что учетной записи, под которой выполняется агент слияния (для репликации слиянием) или агент распространителя (для репликации моментальных снимков и репликации транзакций), предоставлен доступ к хранилищу моментальных снимков на чтение, а учетной записи, под которой выполняется агент моментальных снимков, предоставлен доступ к хранилищу моментальных снимков на запись. Дополнительные сведения о папке моментальных снимков см. в статье [Организация безопасности папки моментальных снимков](../../../relational-databases/replication/security/secure-the-snapshot-folder.md).  
  
## <a name="see-also"></a>См. также  
 [Просмотр и изменение параметров безопасности репликации](../../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)   
 [Включение шифрования соединений в ядре СУБД (диспетчер конфигурации SQL Server)](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)   
 [Replication Security Best Practices](../../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Просмотр и изменение параметров безопасности репликации](../../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)  
  
  
