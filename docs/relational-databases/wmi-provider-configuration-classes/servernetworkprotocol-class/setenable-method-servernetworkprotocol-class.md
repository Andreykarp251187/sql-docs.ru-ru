---
title: Метод SetEnable (класс ServerNetworkProtocol) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetEnable Method (ServerNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetEnable method
ms.assetid: a287950b-086f-4b6d-a2d8-4d3973bd1b21
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 3a55f6f75caafa300d9c605b7c94a9cc7fb99909
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62817066"
---
# <a name="setenable-method-servernetworkprotocol-class"></a>Метод SetEnable (класс ServerNetworkProtocol)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Задействует сетевой протокол сервера.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.SetEnable()  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 A [класса ServerNetworkProtocol](../../../relational-databases/wmi-provider-configuration-classes/servernetworkprotocol-class/servernetworkprotocol-class.md) , который представляет сетевой протокол, используемый экземпляром [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение **uint32** , равное 0, если служба изменена успешно, и 1, если запрос не поддерживается. Любое другое значение указывает на ошибку.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Настройка сетевых протоколов сервера и сетевых библиотек](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
