---
title: MSSQLSERVER_1401 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1401 (Database Engine error)
ms.assetid: 02928770-aa63-4509-8713-406c73e4cedc
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 821a0bdcef41ce6691497e691f5350c0357a6693
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62915928"
---
# <a name="mssqlserver_1401"></a>MSSQLSERVER_1401
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|1401|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBM_MASTERSTARTUP|  
|Текст сообщения|Запуск подпрограммы основного потока зеркального отображения базы данных завершился неудачей по следующей причине: %ls. Устраните причину данной ошибки и перезапустите службу SQL Server.|  
  
## <a name="explanation"></a>Объяснение  
 Запуск контрольного потока зеркального отображения завершился неудачно.  
  
## <a name="user-action"></a>Действие пользователя  
 В журнале событий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] найдите сведения об ошибке, предшествующей сообщению. Устраните причину этой ошибки и перезапустите службу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER).  
  
## <a name="see-also"></a>См. также:  
 [Запуск, остановка, приостановка, возобновление и перезапуск компонента Database Engine, агента SQL и службы браузера SQL Server](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)  
  
  
