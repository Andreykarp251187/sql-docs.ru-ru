---
title: Изменения в работе syslockinfo и процедуры sp_lock | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- syslockinfo
- sp_lock
ms.assetid: b9892ae3-ac15-48be-8b52-78dbed6467ed
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4e2fa557efb6f09eae78180390c733f35bdc4a17
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63214998"
---
# <a name="changes-to-behavior-in-syslockinfo-and-splock"></a>Изменение в работе представления syslockinfo и процедуры sp_lock
  Представление**syslockinfo** и хранимая процедура **sp_lock** могут возвратить непредвиденные значения. Кроме того, они могут вернуть дополнительные строки, в то время как предыдущие версии представления **syslockinfo** и хранимой процедуры **sp_lock** возвращали не более двух строк на каждый ресурс блокировки.  
  
 Для доступа к информации представления **syslockinfo** или запуска хранимой процедуры **sp_lock** необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Описание  
 В [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]столбцы **rsc_objid** и **rsc_indid** в таблице **syslockinfo** , а также столбцы **objid** и **indid** в хранимой процедуре **sp_lock** в обязательном порядке возвращают идентификатор объекта и идентификатор индекса. В [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]может быть возвращено нулевое значение.  
  
 В [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]представление **syslockinfo** и хранимая процедура **sp_lock** возвращают не более двух строк на каждый отдельный ресурс блокировки в отдельной транзакции. Начиная с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], если включено секционирование блокировок, может быть возвращено несколько строк для одного и того же ресурса, выполняющегося в рамках одной транзакции. Может быть до N + 1 строк возвращен, где N — число процессоров. Кроме того, теперь запросы GRANTED и WAITING могут отображаться для одного ресурса, что было невозможно в [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].  
  
## <a name="permissions"></a>Разрешения  
 необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
