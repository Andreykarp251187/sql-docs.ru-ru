---
title: Метод SetProtocolsOrder (класс ClientNetworkProtocol) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetProtocolsOrder Method (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetProtocolsOrder method
ms.assetid: b86d98b9-aae4-4e74-b4da-1ec984d5c8b4
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 16a939835d5129a12d5c3b9fce9d6fa5e0c07f80
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62826612"
---
# <a name="setprotocolsorder-method-clientnetworkprotocol-class"></a>Метод SetProtocolsOrder (класс ClientNetworkProtocol)
  Меняет порядок протоколов в списке.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object  
.SetProtocolsOrder(  
ProtocolOrderList  
)  
  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 A [класса ClientNetworkProtocol](clientnetworkprotocol-class.md) , который представляет сетевой протокол, используемый клиентом [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
#### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|---------------|-----------------|  
|*ProtocolOrderList*|Массив значений string[], представляющий список сетевых протоколов клиента в новом порядке.|  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение `uint32`, равное 0, если служба изменена успешно, и 1, если запрос не поддерживается. Любое другое значение указывает на ошибку.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Настройка клиентских протоколов](https://technet.microsoft.com/library/ms181035.aspx)   
 [Настройка клиентских сетевых протоколов и сетевых библиотек](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
