---
description: Свойство IpAddresses (класс ServerNetworkProtocol)
title: Свойство IpAddresses (класс servernetworkprotocol)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- IpAddresses Property (ServerNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- IpAddresses property
ms.assetid: e5d66f7e-9719-436e-b723-12d56f914a05
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d499e84bef9a88ddb094586f6ff61904ef6f42ea
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88446226"
---
# <a name="ipaddresses-property-servernetworkprotocol-class"></a>Свойство IpAddresses (класс ServerNetworkProtocol)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Возвращает IP-адреса, связанные с сетевым протоколом сервера.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.IpAddresses [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект **класс servernetworkprotocol** , представляющий сетевой протокол, используемый экземпляром [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Массив объектов [класса объект servernetworkprotocolipadress](../../../relational-databases/wmi-provider-configuration-classes/servernetworkprotocolipaddress-class/servernetworkprotocolipaddress-class.md) , ПРЕДСТАВЛЯЮЩИХ IP-адреса, поддерживаемые сетевым протоколом сервера.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>См. также:  
 [Конфигурирование сетевых протоколов сервера и сетевых библиотек](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
