---
title: Коннектионвалидшаредмемори dbmslpcn. dll
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 6ae35826-7d75-4542-b686-5f79316b6157
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1f3bb097965563afb458b4529676d1e9967e4899
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303898"
---
# <a name="connectionvalidsharedmemory-function-in-dbmslpcndll-shared-memory"></a>Функция ConnectionValidSharedMemory в общей памяти dbmslpcn.dll
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Функция определяет, установлена ли и активна SQL Server общая память.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
BOOL ConnectionValidSharedMemory(char * szServerName);  
```  
  
## <a name="parameters"></a>Параметры  
 *сзсервернаме*  
  
-   Тип: **char\* **  
  
-   Имя сервера SQL Server.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Тип: **bool** .  
  
 Возвращает значение 0, если недопустимо; Else возвращает ненулевое значение.  
  
  
