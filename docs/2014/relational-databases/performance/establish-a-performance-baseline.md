---
title: Определение базовых показателей производительности | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- database performance [SQL Server], baselines
- monitoring performance [SQL Server], baselines
- tuning databases [SQL Server], baselines
- server performance [SQL Server], baselines
- performance [SQL Server], baselines
- baseline performance [SQL Server]
- measurements for baseline statistics [SQL Server]
- monitoring server performance [SQL Server], establishing baseline
- database monitoring [SQL Server], baselines
ms.assetid: dc5aa8d6-2507-448f-ad86-4196443915fc
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 4b382545e9f7e5af1607d67539f2ae9f29cfdce3
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63150894"
---
# <a name="establish-a-performance-baseline"></a>Формирование базовых показателей производительности
  Чтобы определить, оптимально ли функционирует система [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , необходимо измерять производительность через определенные промежутки времени, даже если не возникает никаких проблем, для установления базового уровня производительности. Сравните каждый новый набор измерений с полученными ранее.  
  
 Ниже представлены зоны, влияющие на производительность [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   ресурсы системы (оборудование);  
  
-   Сетевая архитектура  
  
-   операционная система;  
  
-   приложения базы данных;  
  
-   Клиентские приложения  
  
 Как минимум используйте измерения базового уровня для определения следующих значений:  
  
-   пиковые и непиковые часы операции;  
  
-   время ответа на подачу запроса или команды пакета;  
  
-   время завершения резервного копирования и восстановления базы данных.  
  
 После установления базового уровня производительности сервера сравните статистику базовых строк с текущей производительностью сервера. Числа намного выше и намного ниже базового уровня являются кандидатами для дальнейшего изучения. Они могут указывать зоны, которым необходимы настройка или повторная конфигурация. Например, если количество времени для выполнения набора запросов увеличивается, изучите запросы, чтобы определить, могут ли они быть переписаны и есть ли необходимость добавлять статистику столбца или новые индексы.  
  
## <a name="see-also"></a>См. также:  
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
