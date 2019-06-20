---
title: LOCALDB_ERROR_INSTANCE_ALREADY_SHARED | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: 35b4d6fa-ebb9-49d3-aaab-d4e37b6f3760
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5f562a0cbd489202d5dbab7de6ac0d19ebeef348
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62519371"
---
# <a name="localdberrorinstancealreadyshared"></a>LOCALDB_ERROR_INSTANCE_ALREADY_SHARED
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|284|  
|Источник события|Среда выполнения локальной базы данных SQL Server 12.0|  
|Компонент|API среды выполнения локальной базы данных|  
|Текст сообщения|Указанный экземпляр локальной базы данных уже используется совместно.|  
  
## <a name="explanation"></a>Объяснение  
 Указанный экземпляр локальной базы данных уже используется совместно под другим общим именем.  
  
## <a name="user-action"></a>Действие пользователя  
 Отключить включенный совместный доступ к экземпляру, прежде чем снова предоставлять его в совместный доступ под другим общим именем.  
  
  
