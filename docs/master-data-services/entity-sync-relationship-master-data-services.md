---
title: Отношение синхронизации сущностей (Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: bd627a2d-dc64-47e9-9a71-2d0ad04b4962
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 30864765a61bfc0175fba06d54eebaea43b6baaf
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65483946"
---
# <a name="entity-sync-relationship-master-data-services"></a>Отношение синхронизации сущностей (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Синхронизация сущностей — это односторонняя повторяемая синхронизация между версиями сущности. Она позволяет разным моделям совместно использовать данные сущностей. Можно поддерживать единый источник истины в одной модели и использовать эти основные данные в других моделях. Например, можно хранить данные о штатах США в сущности одной модели и использовать эти данные в других моделях.  
  
 Синхронизация сущностей также позволяет сделать однократную копию данных.  
  
 Все конечные элементы с атрибутами свободных форм и файлов в исходной сущности будут синхронизированы с целевой сущностью в ходе синхронизации. При этом создаются, удаляются и изменяются схема сущности и ее элементы.  
  
 После установления отношения синхронизации целевая сущность может быть изменена только в ходе синхронизации. Отношение синхронизации в любое время можно удалить, чтобы сделать целевую сущность доступной для редактирования.  
  
## <a name="see-also"></a>См. также  
 [Создание и выполнение отношений синхронизации сущностей (Master Data Services)](../master-data-services/create-and-execute-an-entity-sync-relationship-master-data-services.md)   
 [Создание и удаление отношения синхронизации сущностей (Master Data Services)](../master-data-services/edit-and-delete-an-entity-sync-relationship-master-data-services.md)  
  
  
