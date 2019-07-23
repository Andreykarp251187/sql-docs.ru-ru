---
title: Диалоговое окно "Параметры запроса" (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:69645
- vdt.dlgbox.definequeryparameters
ms.assetid: 31cdaee2-d7cd-4d64-a45f-924b27e8b1f0
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 8bea7f04d7a0275b035879dabcb1da8b3952c849
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68266303"
---
# <a name="query-parameters-dialog-box-visual-database-tools"></a>Диалоговое окно «Параметры запроса» (визуальные инструменты для баз данных)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Данное диалоговое окно позволяет вводить значения для параметров, определенных в запросе. Это диалоговое окно появляется при выполнении запроса, содержащего параметры, которые должны быть введены конечным пользователем во время запуска.  
  
## <a name="options"></a>Параметры  
**Название**  
Список параметров, определенных для выполняемого запроса. Если запрос содержит именованные параметры, то имена отобразятся в списке. Если запрос содержит неименованные параметры, то для каждого параметра запроса в списке будут приведены имена параметров, определенные системой.  
  
**Значение**  
Введите значение для каждого параметра, приведенного в списке **Имя**. Значение, использованное в последний раз, будет отображено в качестве значения параметра по умолчанию.  
  
## <a name="example"></a>Пример  
Следующий запрос на панели SQL открывает диалоговое окно «Параметры запроса» при выполнении в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
```  
SELECT   FirstName, LastName  
FROM    Person.Person AS Lastname  
WHERE   (LastName = @Param1);  
```  
  
## <a name="see-also"></a>См. также:  
[Запрос с параметрами (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/query-with-parameters-visual-database-tools.md)  
  
