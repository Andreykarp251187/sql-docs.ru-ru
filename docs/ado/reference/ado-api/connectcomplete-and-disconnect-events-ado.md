---
title: ConnectComplete и события (ADO) отключения | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Disconnect
- Connection::ConnectComplete
- ConnectComplete
- Connection::Disconnect
helpviewer_keywords:
- Disconnect event [ADO]
- ConnectComplete event [ADO]
ms.assetid: 568f5252-d069-4d99-a01b-2ada87ad1304
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 2f84f89b1ace38350261d461993bf6f89bc155c1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66698755"
---
# <a name="connectcomplete-and-disconnect-events-ado"></a>События ConnectComplete и Disconnect (ADO)
**ConnectComplete** событие вызывается после начала соединения. **Disconnect** событие вызывается после завершения соединения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ConnectComplete pError, adStatus, pConnection  
Disconnect adStatus, pConnection  
```  
  
#### <a name="parameters"></a>Параметры  
 *pError*  
 [Ошибка](../../../ado/reference/ado-api/error-object.md) объекта. Он описывает ошибки, возникшей при значение *adStatus* — **adStatusErrorsOccurred**; в противном случае оно не задано.  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) возвращает значение, всегда **adStatusOK**.  
  
 Когда **ConnectComplete** является именем, этот параметр имеет значение **adStatusCancel** Если **WillConnect** событий запросило отмену ожидающего подключения.  
  
 Перед возвратом любого события, присвойте этому параметру значение **adStatusUnwantedEvent** игнорировать последующие уведомления. Тем не менее, закрытие и повторное открытие [подключения](../../../ado/reference/ado-api/connection-object-ado.md) вызывает эти события к еще раз.  
  
 *pConnection*  
 **Подключения** объекта, для которого применяется это событие.  
  
## <a name="see-also"></a>См. также  
 [Пример модели событий ADO (Visual C++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Общие сведения об обработчике событий ADO](../../../ado/guide/data/ado-event-handler-summary.md)
