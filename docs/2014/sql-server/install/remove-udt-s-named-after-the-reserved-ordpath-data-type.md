---
title: Удаление определяемых пользователем ТИПОВ&#39;s с именем, зарезервированным типом данных ORDPATH | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 474e910a-6abb-4e28-acc2-055338c011d4
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3ee155c70a8b10d4437d6b2f374c8b9497bf3faa
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66092920"
---
# <a name="remove-udt39s-named-after-the-reserved-ordpath-data-type"></a>Удаление определяемых пользователем ТИПОВ&#39;s с именем, зарезервированным типом данных ORDPATH
  Помощник по обновлению обнаружил определяемый пользователем тип, имя которого совпадает с именем, зарезервированным для типа данных `ORDPATH`.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Описание  
 Имена терминов, используемых во встроенных типах данных, не должны использоваться в качестве имен определяемых пользователем типов среды CLR или их псевдонимов.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Удалите определяемый пользователем тип и создайте его повторно с именем, отличным от зарезервированного.  
  
## <a name="external-resources"></a>Внешние ресурсы  
 [Создание определяемого пользователем типа](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)  
  
  
