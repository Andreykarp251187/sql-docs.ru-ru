---
title: Управление табличными пространствами Oracle | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], managing tablespaces
- tablespaces [SQL Server replication]
ms.assetid: b8ea6c3b-01d6-4efc-bbfb-03b264530bbd
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9a6bf22c7649646506b65628f556b52fead23375
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63022295"
---
# <a name="manage-oracle-tablespaces"></a>Управление табличными пространствами Oracle
  Табличное пространство — это единица хранилища базы данных, приблизительно эквивалентная группе файлов в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Табличные пространства предоставляют возможности хранения и управления объектами баз данных в рамках индивидуальных групп. Дополнительные сведения см. в документации Oracle.  
  
 При настройке таблицы как части публикации Oracle можно при желании указать, что существующее табличное пространство Oracle будет использоваться для хранения информации о ходе репликации. В противном случае табличным пространством для объектов репликации будет табличное пространство по умолчанию, связанное с административной пользовательской схемой репликации, которая была настроена при настройке издателя.  
  
 **Указание табличного пространства для таблицы регистрации статей**:  
  
-   Задайте табличное пространство в диалоговом окне **Свойства статьи** . Дополнительные сведения о доступе к этому диалоговому окну см. в разделе [Просмотр и изменение свойств публикации](../publish/view-and-modify-publication-properties.md).  
  
-   Используйте [sp_changearticle (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql). Чтобы использовать **sp_changearticle**, укажите следующее:  
  
    -   имя издателя Oracle в качестве параметра **@publisher**.  
  
    -   имя публикации Oracle в качестве параметра **@publication**.  
  
    -   имя статьи в качестве параметра **@article**.  
  
    -   значение tablespace для параметра **@property**.  
  
    -   имя табличного пространства для параметра **@value**.  
  
## <a name="see-also"></a>См. также  
 [Настройка издателя Oracle](configure-an-oracle-publisher.md)   
 [Objects Created on the Oracle Publisher](objects-created-on-the-oracle-publisher.md)  
  
  
