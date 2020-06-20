---
title: Назначение флага версии (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- version flags [Master Data Services], assigning flags
- versions [Master Data Services], assigning flags
ms.assetid: 6629ec7e-32e7-4a1e-8b31-eb43c5923766
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 94c387915d4962eba4d97aa758ca5d5a2aa74b13
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84972244"
---
# <a name="assign-a-flag-to-a-version-master-data-services"></a>Назначение флага версии (службы Master Data Services)
  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]назначается флаг версии, чтобы указать версию, которую следует использовать пользователям или системам-подписчикам.  
  
> [!NOTE]  
>  Флаг можно назначить только одной версии в каждый момент времени. Если назначить флаг, уже назначенный другой версии, то он переместится к выбранной версии.  
  
## <a name="prerequisites"></a>Предварительные условия  
 Для выполнения этой процедуры:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Управление версиями** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в разделе [administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
-   Нужно создать флаг версии для назначения. Дополнительные сведения см. в статье [Создание флага версии (службы Master Data Services)](../../2014/master-data-services/create-a-version-flag-master-data-services.md).  
  
### <a name="to-assign-a-flag-to-a-version"></a>Назначение флага версии  
  
1.  В среде [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Управление версиями**.  
  
2.  На странице **Управление версиями** в строке версии, которой необходимо назначить флаг, дважды щелкните ячейку в столбце **Флаг** .  
  
3.  Выберите из списка флаг, который нужно назначить.  
  
    > [!NOTE]  
    >  Если нужный флаг недоступен, то, возможно, он доступен только для **зафиксированных** версий. Чтобы удостовериться в этом, перейдите на страницу **Управление флагами версии** и просмотрите поле **Только зафиксированные версии** флага.  
  
4.  Нажмите клавишу ВВОД, чтобы сохранить изменение.  
  
## <a name="see-also"></a>См. также:  
 [Создание флага версии &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-version-flag-master-data-services.md)   
 [Версии (службы Master Data Services)](../../2014/master-data-services/versions-master-data-services.md)  
  
  
