---
title: Изменение хранимых процедур, в которых используются неподдерживаемые свойства полнотекстового поиска | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- discontinued properties [Full-Text Search]
- stored procedures [Full-Text Search]
ms.assetid: 8d9392d9-a9ba-4378-84e4-59f516b67ddb
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f19fa2dc044d5975edfbc201c8fc3eb9e9244936
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85044608"
---
# <a name="modify-stored-procedures-that-use-discontinued-full-text-search-properties"></a>Измените хранимые процедуры, в которых используются неподдерживаемые свойства полнотекстового поиска
  Чтобы обеспечить правильную работу хранимых процедур, нужно изменить существующие процедуры, удалив свойства и настройки, связанные с полнотекстовым поиском, которые были удалены или устарели.  
  
## <a name="component"></a>Компонент  
 Полнотекстовый поиск  
  
## <a name="description"></a>Описание  
 Следующие свойства и настройки, связанные с полнотекстовым поиском, были удалены.  
  
-   **DataTimeout**  
  
-   **ConnectTimeout**  
  
-   **Clean_up**  
  
-   **LogSize**  
  
 Следующие свойства и настройки, связанные с полнотекстовым поиском, были удалены или устарели.  
  
-   Параметр Path полнотекстового каталога. Полнотекстовый каталог будет логическим объектом, не имеющим конкретного файлового пути.  
  
-   Включение или отключение полнотекстового поиска с помощью процедуры SP_FULLTEXT_DATABASE больше не работает, так как в [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] базы данных по умолчанию всегда доступны для полнотекстового поиска.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Измените хранимые процедуры, чтобы удалить эти свойства.  
  
## <a name="see-also"></a>См. также:  
 [Работа с помощником по обновлению](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
