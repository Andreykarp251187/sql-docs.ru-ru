---
title: Класс SqlServerAlias | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
apiname:
- SqlServerAlias Class
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SqlServerAlias class
ms.assetid: 475662b9-6985-45bf-b1e9-b0f26ef50443
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: cdcbd34978738d64d52b3c70a280507b6cb0c391
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68052375"
---
# <a name="sqlserveralias-class"></a>Класс SqlServerAlias
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Класс [SqlServerAlias](../../../relational-databases/wmi-provider-configuration-classes/sqlserveralias-class/sqlserveralias-class.md) представляет псевдоним соединения сервера.  
  
 Псевдоним соединения сервера требуется при возникновении обоих следующих событий:  
  
-   клиент соединяется с экземпляром [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] по сетевому средству передачи данных, не являющемуся сетевым транспортом по умолчанию;  
  
-   экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , с которым соединяется клиент, прослушивает альтернативный именованный канал.  
  
 **Примечание.** [Класс SqlServerAlias](../../../relational-databases/wmi-provider-configuration-classes/sqlserveralias-class/sqlserveralias-class.md) наследует **поместить** метод из класса Provider. Однако он не возвращает результаты, как указано методом **Provider::Put** . Дополнительные сведения см. в документации WMI.  
  
## <a name="see-also"></a>См. также  
 [Настройка клиентских протоколов](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
