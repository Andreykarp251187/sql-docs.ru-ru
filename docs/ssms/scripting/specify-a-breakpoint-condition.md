---
title: Указание условия в точке останова | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, breakpoint conditions
ms.assetid: b43d8a2b-99a3-4fb7-8848-99c042ea7ef7
author: markingmyname
ms.author: maghan
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 63043009d9c908ad5edc3771e5d353cf2f66b010
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65821928"
---
# <a name="specify-a-breakpoint-condition"></a>Задание условия точки останова
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Условием для точки останова служит выражение [!INCLUDE[tsql](../../includes/tsql-md.md)] , проверяемое отладчиком по достижению точки останова. Если достигнуто указанное число попаданий или удовлетворяется указанное условие, то отладчик останавливает выполнение или выполняет действие, заданное для точки останова.  
  
## <a name="specifying-conditions"></a>Задание условий  
 Необходимо задать допустимое выражение Transact-SQL, результатом вычисления которого является логическое значение. Дополнительные сведения см. в разделе [Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md).  
  
 Если задать условие точки останова с недопустимым синтаксисом, немедленно появится предупреждение. Если задать условие с допустимым синтаксисом, но недопустимой семантикой, предупреждение появится, когда точка останова будет достигнута в первый раз. В любом случае отладчик прервет выполнение, как только будет достигнута недопустимая точка останова.  
  
#### <a name="to-specify-a-condition"></a>Задание условия  
  
1.  В окне редактора щелкните глиф точки останова правой кнопкой мыши и выберите в контекстном меню пункт **Условие** .  
  
     -или-  
  
     В окне **Точки останова** щелкните глиф точки останова правой кнопкой мыши и выберите в контекстном меню пункт **Условие** .  
  
2.  Введите в поле **Условие** диалогового окна **Условие точки останова** допустимое логическое выражение.  
  
3.  Если выбрать **Истинно** , выполнение будет прерываться, когда выражение принимает значение **true**, а если **Изменилось** — когда значения выражения изменяется.  
  
    > [!NOTE]  
    >  Отладчик не проверяет это логическое выражение, пока не будет достигнута первая точка останова. Если выбрать **Изменилось**, отладчик не будет считать первую проверку изменением и, следовательно, не будет прерывать при ней исполнение.  
  
## <a name="see-also"></a>См. также:  
 [Настройка счетчика числа попаданий](../../relational-databases/scripting/specify-a-hit-count.md)   
 [Задание действия в точке останова](../../relational-databases/scripting/specify-a-breakpoint-action.md)  
