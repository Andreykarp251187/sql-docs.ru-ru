---
title: MSSQLSERVER_17128 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17128 (Database Engine error)
ms.assetid: 7b15a5e6-fd41-47ce-ba87-54f72acea4bb
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7a73f2469c38d611b95e3446e80755687f40346e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62869712"
---
# <a name="mssqlserver_17128"></a>MSSQLSERVER_17128
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|17128|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|INIT_NOBUFSPACE|  
|Текст сообщения|initdata: недостаточно памяти для буферов ядра.|  
  
## <a name="explanation"></a>Объяснение  
 Не удается провести начальное выделение памяти из буферного пула или резервирование памяти. SQL Server завершает работу.  
  
## <a name="user-action"></a>Действие пользователя  
 Эта обычно случается при запуске SQL Server на очень маломощном компьютере, параметры которого не достигают минимальных требований к системе.  
  
  
