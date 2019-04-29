---
title: С помощью диаграмм обновления для изменения данных в SQLXML 4.0 | Документация Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, updategrams
- data insertions [SQLXML]
- data deletions [SQLXML]
- updating data [SQLXML]
- modifying data [SQLXML]
- OPENXML function
- updategrams [SQLXML]
- database modifications [SQLXML]
- data updates [SQLXML]
- modifying databases
- data modifications [SQLXML]
- deleting data
- inserting data
ms.assetid: b8b3b892-cb73-41d0-b945-bce148d81d9b
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: df86cae9fe4fd132393b6c882977156bd5c0ff45
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63025331"
---
# <a name="using-updategrams-to-modify-data-in-sqlxml-40"></a>Использование диаграмм обновления для изменения данных в SQLXML 4.0
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Можно изменить (вставки, обновления или удаления) базы данных в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] из существующего XML-документа с помощью диаграммы обновления или OPENXML [!INCLUDE[tsql](../../../includes/tsql-md.md)] функции.  
  
 В этом разделе содержатся сведения о диаграммах обновления и примеры их использования.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Общие сведения о диаграммах обновления &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/introduction-to-updategrams-sqlxml-4-0.md)  
 Содержит основные сведения и примеры диаграмм обновления.  
  
 [Определение схемы с заметками сопоставления в диаграмме обновления &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)  
 Содержит объяснение и примеры аннотированных схем сопоставления в диаграммах обновления.  
  
 [Обработка NULL &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/null-handling-sqlxml-4-0.md)  
 Содержит описание задания значений NULL для значений элементов и атрибутов.  
  
 [Вставка данных с помощью диаграмм обновления XML &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md)  
 Содержит описание и примеры использования диаграмм обновления для добавления данных.  
  
 [Удаление данных с помощью диаграмм обновления XML &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/deleting-data-using-xml-updategrams-sqlxml-4-0.md)  
 Содержит описание и примеры использования диаграмм обновления для удаления данных.  
  
 [Обновление данных с помощью диаграмм обновления XML &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/updating-data-using-xml-updategrams-sqlxml-4-0.md)  
 Содержит описание и примеры использования диаграмм обновления для изменения существующих данных.  
  
 [Передача параметров в диаграммы обновления &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/passing-parameters-to-updategrams-sqlxml-4-0.md)  
 Содержит описание и примеры передачи параметров в диаграммы обновления.  
  
 [Обработка базы данных проблем параллелизма в диаграммах обновления &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/handling-database-concurrency-issues-in-updategrams-sqlxml-4-0.md)  
 Содержит описание и примеры возможных уровней защиты для решения проблем параллелизма в диаграммах обновления.  
  
 [Образцы приложений диаграмм обновления &#40;SQLXML 4.0&#41;](https://msdn.microsoft.com/library/d2287e10-4007-4ba4-ad84-4e2b6adfede5)  
 Содержит образцы приложений, использующих диаграммы обновления.  
  
 [Рекомендации и ограничения диаграмм обновления XML &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/guidelines-and-limitations-of-xml-updategrams-sqlxml-4-0.md)  
 Содержит перечень фактов, о которых необходимо помнить при работе с диаграммами обновления.  
  
  
