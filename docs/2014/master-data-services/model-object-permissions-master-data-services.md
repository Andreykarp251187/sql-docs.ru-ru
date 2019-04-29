---
title: Разрешения объекта модели (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- permissions [Master Data Services], model objects
- models [Master Data Services], object permissions
ms.assetid: fab6335b-4cae-47de-ae7c-6c4743e0680f
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: d9e2838e2ba3cfcb713c0353b89054ca549e4e5c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62923573"
---
# <a name="model-object-permissions-master-data-services"></a>Разрешения объекта модели (службы Master Data Services)
  Разрешения объекта модели являются обязательными. Они определяют атрибуты, к которым пользователь может получить доступ в функциональной области **Обозреватель** пользовательского интерфейса.  
  
 Например, если пользователь имеет разрешение **Обновление** в сущности «Продукт», то пользователь может обновлять все атрибуты этой сущности. Если назначено разрешение **Обновление** для одного атрибута, то пользователь может обновлять только этот атрибут.  
  
 Для определения безопасности, назначенной каждому индивидуальному значению атрибута, разрешения объектов модели можно сочетать с разрешениями элементов иерархии, к которым пользователь может получить доступ.  
  
 Чтобы предоставить пользователю доступ к функциональной области, отличное от **Explorer**, пользователь должен быть администратором модели, что также требует назначения разрешений объекта модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](administrators-master-data-services.md).  
  
 Разрешения объекта модели назначаются в пользовательском интерфейсе [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] в функциональной области **Разрешения пользователей и групп** на вкладке **Модели**. На этой вкладке модель представлена в виде древовидной структуры. При назначении разрешения для объекта дерева это разрешение наследуют все объекты, находящиеся ниже данного узла. Чтобы переопределить наследование разрешений, нужно назначить разрешение отдельным объектам.  
  
 Вы можете назначить **только для чтения**, **обновление**, или **Deny** разрешения на объекты модели. Если на вкладке **Модели** не будут назначены никакие разрешения, то пользователь не сможет просматривать модели и данные в среде [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
## <a name="best-practice"></a>Рекомендации  
 Как правило, следует назначить **обновления** разрешение на объект модели, а затем явно назначить разрешение объектам на нижнем уровне. Если объектам на нижнем уровне не назначить разрешение, то разрешения будут унаследованы, а пользователь станет администратором.  
  
## <a name="see-also"></a>См. также  
 [Назначение разрешения для объекта модели (службы Master Data Services)](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Разрешения модели (службы Master Data Services)](../../2014/master-data-services/model-permissions-master-data-services.md)   
 [Разрешения функциональной области (службы Master Data Services)](../../2014/master-data-services/functional-area-permissions-master-data-services.md)   
 [Разрешения на элементы иерархии (службы Master Data Services)](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md)   
 [Способ определения разрешений (службы Master Data Services)](../../2014/master-data-services/how-permissions-are-determined-master-data-services.md)  
  
  
