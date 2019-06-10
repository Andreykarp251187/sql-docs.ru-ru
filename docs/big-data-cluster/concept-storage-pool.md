---
title: Что такое пул носителей?
titleSuffix: SQL Server big data clusters
description: В этой статье описывается пула носителей в кластер SQL Server 2019 больших данных.
author: rothja
ms.author: jroth
manager: jroth
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 7ff8b16ec5f1ea0d1df401cee9657eb8d564863a
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66782986"
---
# <a name="what-is-the-storage-pool-sql-server-big-data-clusters"></a>Что такое пул носителей (кластеры больших данных в SQL Server)

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье описывается роль *пул носителей для SQL Server* в кластере SQL Server 2019 больших данных (Предварительная версия). В следующих разделах об архитектуре и функциях SQL пула носителей.

## <a name="storage-pool-architecture"></a>Архитектура хранилища пула

Пул носителей состоит из хранилища, которые узлы состоит из SQL Server в Linux, Spark и HDFS. Все узлы хранилища в кластере SQL больших данных являются членами кластера HDFS.

![Архитектура хранилища пула](media/concept-storage-pool/scale-big-data-on-demand.png)

## <a name="responsibilities"></a>Обязанности

Узлы хранилища отвечают за:

- Прием данных через Spark.
- Хранилище данных в HDFS (формат Parquet). HDFS также представлена сохранение данных HDFS данные распределяются на всех узлах хранилища в кластере SQL больших данных.
- Доступ к данным через конечные точки HDFS и SQL Server.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах больших данных SQL Server, см. следующие ресурсы:

- [Что такое кластеры SQL Server 2019 больших данных?](big-data-cluster-overview.md)
- [Семинар: Кластерами больших данных Microsoft SQL Server архитектуры](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
