---
title: Срочное применение разрешений для элемента (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- members [Master Data Services], applying permissions immediately
- permissions [Master Data Services], applying member permissions immediately
ms.assetid: 5b16de66-5c39-49f5-992f-402a9eb319aa
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: bd7fd390010096e943e397a95c018c967f09d21a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62696046"
---
# <a name="immediately-apply-member-permissions-master-data-services"></a>Срочное применение разрешения для элемента (службы Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]можно не ждать, пока безопасность элемента задействуется через обычные промежутки времени, а применить разрешения для элемента немедленно.  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   пользователь должен иметь разрешения на выполнение хранимой процедуры mdm.udpSecurityMemberProcessRebuildModel в базе данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. Дополнительные сведения см. в разделе [Защита объектов базы данных (службы Master Data Services)](../master-data-services/database-object-security-master-data-services.md).  
  
### <a name="to-immediately-apply-hierarchy-member-permissions"></a>Немедленное применение разрешений для элементов иерархии  
  
1.  Откройте среду [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] и установите соединение с экземпляром компонента [!INCLUDE[ssDE](../includes/ssde-md.md)] для базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
2.  Создайте новый запрос.  
  
3.  Введите следующий текст, заменив *database* именем своей базы данных, а *Model_Name* — именем модели.  
  
    ```  
    USE [database];  
    GO  
  
    DECLARE @Model_ID INT;  
    SELECT @Model_ID = ID FROM mdm.tblModel WHERE [Name] = N'Model_Name';  
    EXEC [mdm].[udpSecurityMemberProcessRebuildModel] @Model_ID=@Model_ID, @ProcessNow=1;  
    GO  
    ```  
  
4.  Выполните запрос.  
  
## <a name="see-also"></a>См. также  
 [Назначение разрешений для элемента иерархии (службы Master Data Services)](../master-data-services/assign-hierarchy-member-permissions-master-data-services.md)   
 [Разрешения на элементы иерархии (службы Master Data Services)](../master-data-services/hierarchy-member-permissions-master-data-services.md)  
  
  
