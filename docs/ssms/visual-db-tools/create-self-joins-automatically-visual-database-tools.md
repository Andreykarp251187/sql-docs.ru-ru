---
title: Автоматическое соединение самосоединения (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- automatic joins
- self-joins
- joins [SQL Server], self
ms.assetid: f9ec90e8-3aad-415c-a5c4-8dfa9540e37f
author: markingmyname
ms.author: maghan
manager: jroth
ms.openlocfilehash: 7958ed99aa26de79893329d57471ead88ea4519b
ms.sourcegitcommit: 5d839dc63a5abb65508dc498d0a95027d530afb6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2019
ms.locfileid: "67680238"
---
# <a name="create-self-joins-automatically-visual-database-tools"></a>Автоматическое создание самосоединения (визуальные инструменты для баз данных)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Если таблица имеет рефлексивную связь в базе данных, можно автоматически создать самосоединение.  
  
### <a name="to-create-a-self-join-automatically"></a>Автоматическое создание самосоединения  
  
1.  Добавьте на [панель диаграмм](../../ssms/visual-db-tools/diagram-pane-visual-database-tools.md) нужную таблицу.  
  
2.  Еще раз добавьте эту таблицу, чтобы на панели диаграмм эта таблица была показана дважды.  
  
    [Конструктор запросов и представлений](../../ssms/visual-db-tools/query-and-view-designer-tools-visual-database-tools.md) присваивает второму экземпляру псевдоним, добавляя порядковый номер к имени таблицы. Кроме того, конструктор запросов и представлений создает линию соединения между двумя прямоугольниками, представляющими два разных способа, которыми таблица участвует в запросе.  
  
## <a name="see-also"></a>См. также:  
[Запросы с соединениями (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/query-with-joins-visual-database-tools.md)  
  
