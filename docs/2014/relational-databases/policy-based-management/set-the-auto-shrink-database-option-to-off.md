---
title: Задание значения OFF для параметра базы данных AUTO_SHRINK | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 16403850-d745-4754-b84f-5f01aaecd24e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: c81885e5a3aaec197b8963c2e868b6f65a0b0544
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62691515"
---
# <a name="set-the-auto_shrink-database-option-to-off"></a>Задание значения параметра базы данных AUTO_SHRINK, равного OFF
  Это правило проверяет, имеет ли параметр базы данных AUTO_SHRINK значение OFF. Нередко сжатие и расширение базы данных ведет к физической фрагментации.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Присвойте параметру базы данных AUTO_SHRINK значение OFF. Если известно, что освобождаемое место не понадобится в будущем, можно освободить это место, выполнив сжатие базы данных вручную.  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 Статья [315512](https://go.microsoft.com/fwlink/?linkid=117750)базы знаний Майкрософт  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
