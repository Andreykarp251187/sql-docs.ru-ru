---
title: Типы подписчиков | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.subscribertypes.f1
ms.assetid: a70656cb-21c9-4489-be77-ccd396747e3b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ba8a2c83b852abc9d82a84b2d0b2e98f969d0a7b
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85047648"
---
# <a name="subscriber-types"></a>Типы подписчиков
  Репликация слиянием позволяет задавать типы подписчиков, которые должна поддерживать публикация. Выбор типов подписчиков устанавливает *уровень совместимости публикации*, который определяет, какие возможности будут использоваться публикацией.  
  
 После создания моментального снимка публикации можно повысить ее уровень совместимости (еще более ограничить ее совместимость) на странице **Общие** диалогового окна **Свойства публикации** . Понизить уровень совместимости нельзя.  
  
## <a name="options"></a>Параметры  
 Выберите тип подписчика, который должна поддерживать эта публикация.  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
 Публикация может использовать все возможности.  
  
 [!INCLUDE[ssEW](../../includes/ssew-md.md)]  
 Публикации требуется, чтобы файлы моментального снимка имели символьный формат (агент моментальных снимков выполняет это автоматически). [!INCLUDE[ssEW](../../includes/ssew-md.md)] также имеет ряд ограничений, не связанных с уровнем совместимости.  
  
 Если выбран этот параметр, то для публикации включается параметр веб-синхронизации. Дополнительные сведения о веб-синхронизации см. в разделе [Web Synchronization for Merge Replication](web-synchronization-for-merge-replication.md).  
  
## <a name="see-also"></a>См. также:  
 [Публикация данных и объектов базы данных](publish/publish-data-and-database-objects.md)   
 [Create a Publication](publish/create-a-publication.md)   
 [Просмотр и изменение свойств издателя и распространителя](view-and-modify-distributor-and-publisher-properties.md)   

  
