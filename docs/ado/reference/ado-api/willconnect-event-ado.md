---
description: Событие WillConnect (ADO)
title: Событие Виллконнект (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- WillConnect
- Connection::WillConnect
helpviewer_keywords:
- WillConnect event [ADO]
ms.assetid: da561d58-eb58-446c-a4fd-1838c76073c0
author: rothja
ms.author: jroth
ms.openlocfilehash: 259ef55060d7968d9ec557c831412ad58609a6df
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88987785"
---
# <a name="willconnect-event-ado"></a>Событие WillConnect (ADO)
Событие **виллконнект** вызывается до начала соединения.  
  
 Область **применения:** [объект соединения (ADO)](./connection-object-ado.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
WillConnect ConnectionString, UserID, Password, Options, adStatus, pConnection  
```  
  
#### <a name="parameters"></a>Параметры  
 *ConnectionString*  
 **Строка** , содержащая сведения о соединении для ожидающего подключения.  
  
 *UserID*  
 **Строка** , содержащая имя пользователя для ожидающего подключения.  
  
 *Пароль*  
 **Строка** , содержащая пароль для ожидающего подключения.  
  
 *Параметры*  
 Значение **типа Long** , указывающее, как поставщик должен оценивать *ConnectionString*. Единственный вариант — **адасинкопен**.  
  
 *адстатус*  
 Значение состояния [евентстатусенум](./eventstatusenum.md) .  
  
 При вызове этого события этот параметр по умолчанию имеет значение **адстатусок** . Он имеет значение **адстатускантдени** , если событие не может запрашивать отмену ожидающей операции.  
  
 Перед возвратом этого события задайте для этого параметра значение **адстатусунвантедевент** , чтобы предотвратить появление последующих уведомлений. Задайте для этого параметра значение **адстатусканцел** , чтобы запросить операцию подключения, которая привела к отмене этого уведомления.  
  
 *пконнектион*  
 Объект [соединения](./connection-object-ado.md) , к которому относится данное уведомление о событии. Изменения параметров **соединения** обработчиком событий **виллконнект** не будут влиять на **соединение**.  
  
## <a name="remarks"></a>Remarks  
 При вызове **виллконнект** параметры *ConnectionString*, *UserID*, *Password*и *Options* устанавливаются в значения, установленные операцией, вызвавшей это событие (ожидающее подключение), и могут быть изменены перед возвратом события. **Виллконнект** может возвращать запрос на отмену ожидающего подключения.  
  
 При отмене этого события будет вызван **коннекткомплете** с его параметром *адстатус* , установленным в **адстатусеррорсоккурред**.  
  
## <a name="see-also"></a>См. также  
 [Пример модели событий ADO (Visual c++)](./ado-events-model-example-vc.md)   
 [Общие сведения об обработчике событий ADO](../../guide/data/ado-event-handler-summary.md)