---
title: Удаление пользователей или групп (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deleting groups [Master Data Services]
- groups [Master Data Services], deleting
- users [Master Data Services], deleting
- deleting users [Master Data Services]
ms.assetid: 0bbf9d2c-b826-48bb-8aa9-9905db6e717f
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 81b16bc5b2bc8f2158a82733fb96f5144b7d15f9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67906268"
---
# <a name="delete-users-or-groups-master-data-services"></a>Удаление пользователей или группы (службы Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Удалите пользователей и группы, если больше не нужно, чтобы они имели доступ к среде [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
 Помните о следующих правилах при удалении пользователей и групп.  
  
-   При удалении пользователя, который является членом группы с доступом к [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], у него останется доступ к [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , пока его не удалить из группы Active Directory или локальной группы.  
  
-   При удалении группы все пользователи из этой группы, которые ранее обращались к [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , будут отображаться в списке **Пользователи** , пока они не будут удалены.  
  
-   Изменения безопасности распространяются на MDS [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] спустя 20 минут.  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Разрешения пользователей и групп** ;  
  
### <a name="to-delete-users-or-groups"></a>Удаление пользователей или групп  
  
1.  В среде [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните **Разрешения пользователей и групп**.  
  
2.  Чтобы удалить пользователя, оставайтесь на странице **Пользователи** . Чтобы удалить группу, в строке меню щелкните **Управление группами**.  
  
3.  Выберите в сетке строку для пользователя или группы, которых необходимо удалить.  
  
4.  Нажмите **Удалить выбранного пользователя** или **Удалить выбранную группу**.  
  
5.  В диалоговом окне подтверждения нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [Безопасность (службы Master Data Services)](../master-data-services/security-master-data-services.md)  
  
  
