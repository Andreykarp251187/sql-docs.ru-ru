---
description: Откат журнала изменений элемента (Master Data Services)
title: Откат журнала изменений элемента
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: d39d3474-20e7-429f-9c8d-fcc4eb0854fc
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: fe275fe7aef826b3eeaa6ef6e959f8c8bea33b4f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461726"
---
# <a name="rollback-member-revision-history-master-data-services"></a>Откат журнала изменений элемента (Master Data Services)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  Запись в журнал изменений элемента осуществляется каждый раз при изменении элемента. Существует возможность откатить журнал изменений элемента к предыдущей версии.  
  
## <a name="prerequisites"></a>Предварительные требования  
  
-   Необходимо иметь разрешение на обновление хотя бы одного из атрибутов выбранного элемента. При откате журнала изменений все значения атрибутов, которые могут быть обновлены, откатываются к значениям предыдущей версии.  
  
-   Журнал изменений доступен, только если типом журнала транзакций сущности является элемент.  
  
 **Откат журнала изменений элемента**  
  
1.  В диспетчере основных данных откройте обозреватель.  
  
2.  Выберите сущность и элемент для отката.  
  
3.  Щелкните **Просмотр журнала**.  
  
4.  Выберите версию для отката и нажмите **Откат**.  
  
## <a name="see-also"></a>См. также:  
 [Журнал изменений элемента &#40;Master Data Services&#41;](../master-data-services/member-revision-history-master-data-services.md)   
 [Изменение типа журнала транзакций сущности (службы Master Data Services)](../master-data-services/change-the-entity-transaction-log-type-master-data-services.md)  
  
  
