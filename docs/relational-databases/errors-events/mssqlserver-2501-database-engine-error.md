---
title: MSSQLSERVER_2501 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 2501 (Database Engine error)
ms.assetid: 895aafe3-a4e7-4ed8-acc5-93be76ef3664
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 37f19ae950906ed463ceb05e4f5194fb5e02386a
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68056573"
---
# <a name="mssqlserver_2501"></a>MSSQLSERVER_2501
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|2501|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC_NO_SUCH_TABLE_NAME|  
|Текст сообщения|Невозможно найти таблицу или объект с именем «NAME». Проверьте системный каталог.|  
  
## <a name="explanation"></a>Объяснение  
Не удается найти указанный объект.  
  
### <a name="possible-causes"></a>Возможные причины  
Возможны следующие причины возникновения этой ошибки.  
  
-   Объект указан неверно.  
  
-   Объект не существует или был удален до того, как инструкция к нему обратилась.  
  
-   Объект может существовать, но быть недоступным пользователю. Например, у пользователя могут отсутствовать необходимые разрешения для данного объекта, либо объект является внутренней таблицей, которую пользователь просматривать не может.  
  
## <a name="user-action"></a>Действие пользователя  
  
-   Проверьте правильность контекста текущей базы данных. Дополнительные сведения см. в статье [USE (Transact-SQL)](~/t-sql/language-elements/use-transact-sql.md).  
  
-   Проверьте правильность имени таблицы или объекта.  
  
-   Проверьте имя схемы, содержащей объект. Если объект принадлежит к схеме, отличной от схемы по умолчанию (**dbo**), имя таблицы или объекта необходимо указывать в двухкомпонентном формате *имя_схемы.имя_объекта*.  
  
-   Проверьте наличие объекта в системных таблицах. Чтобы проверить существование таблицы или другого объекта на уровне схемы, отправьте запрос к представлению каталога [sys.objects](~/relational-databases/system-catalog-views/sys-objects-transact-sql.md). Если объект отсутствует в системных таблицах, значит он был удален или у пользователя отсутствуют разрешения на просмотр метаданных объекта. Дополнительные сведения о просмотре метаданных объекта см. в статье [Настройка видимости метаданных](~/relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
[Представления каталога (Transact-SQL)](~/relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
