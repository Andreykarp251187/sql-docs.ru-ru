---
title: Свойства SQL Server (страница FILESTREAM) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql13.swb.serverproperties.filestream.f1
helpviewer_keywords:
- FILESTREAM [SQL Server], properties page
ms.assetid: 8a8d38d3-e97a-4b09-a40b-659b2e3a5c47
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d40d7111bf7beac4c8a34f91481368b94f62c519
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68025451"
---
# <a name="server-properties---filestream-page"></a>Свойства SQL Server (страница FILESTREAM)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Эта страница используется, чтобы включить FILESTREAM для этой установки [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## <a name="uielement-list"></a>Список элементов пользовательского интерфейса  
 **Разрешить FILESTREAM при доступе через Transact-SQL**  
 Выберите, чтобы включить FILESTREAM для доступа [!INCLUDE[tsql](../../includes/tsql-md.md)] . Необходимо выбрать этот элемент управления, прежде чем будут доступны другие параметры управления.  
  
 **Разрешить FILESTREAM при потоковом доступе файлового ввода-вывода**  
 Выберите, чтобы разрешить потоковый доступ Win32 для FILESTREAM.  
  
 **Имя общего ресурса Windows**  
 Этот элемент управления используется для ввода имени общего ресурса Windows, в котором будут храниться данные FILESTREAM.  
  
 **Разрешить удаленным клиентам потоковый доступ к данным FILESTREAM**  
 Выберите этот элемент управления, чтобы разрешить удаленным клиентам доступ к этим данным FILESTREAM на этом сервере.  
  
## <a name="see-also"></a>См. также:  
 [FILESTREAM (SQL Server)](../../relational-databases/blob/filestream-sql-server.md)   
 [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
