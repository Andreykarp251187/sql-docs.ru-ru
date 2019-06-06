---
title: Событие FetchComplete (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset::ExecuteComplete
- ExecuteComplete
helpviewer_keywords:
- FetchComplete event [ADO]
ms.assetid: a28d3858-566c-468d-b070-d1de4339fbea
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 7b5fb32f567dcfffb6112e843b53cb99a3b106bc
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66697897"
---
# <a name="fetchcomplete-event-ado"></a>Событие FetchComplete (ADO)
**FetchComplete** событие вызывается после получения всех записей в длительных асинхронных операций в [записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
FetchComplete pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Параметры  
 *pError*  
 [Ошибка](../../../ado/reference/ado-api/error-object.md) объекта. Он описывает ошибки, возникшей при значение **adStatus** — **adStatusErrorsOccurred**; в противном случае оно не задано.  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) значение состояния. Когда это событие вызывается, этот параметр имеет значение **adStatusOK** при успешной операции, которая вызвала событие, или чтобы **adStatusErrorsOccurred** Если произошел сбой операции.  
  
 Прежде чем это событие возвращает, присвойте этому параметру значение **adStatusUnwantedEvent** игнорировать последующие уведомления.  
  
 *pRecordset*  
 Объект **записей** объекта. Объект, для которого были получены записи.  
  
## <a name="remarks"></a>Примечания  
 Чтобы использовать **FetchComplete** с Microsoft Visual Basic, Visual Basic 6.0 или более поздней версии необходим.  
  
## <a name="see-also"></a>См. также  
 [Пример модели событий ADO (Visual C++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Общие сведения об обработчике событий ADO](../../../ado/guide/data/ado-event-handler-summary.md)
