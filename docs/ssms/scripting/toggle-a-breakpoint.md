---
title: Переключение точки останова | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: c477ab89-a1cd-4f2c-aa7c-40525041100f
author: markingmyname
ms.author: maghan
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 20a7c05dff339e56be8faef3cdd9503d993fc590
ms.sourcegitcommit: c29150492383f48ef484fa02a483cde1cbc68aca
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2019
ms.locfileid: "65821844"
---
# <a name="toggle-a-breakpoint"></a>Переключение точки останова
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Установка точки останова для инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] называется переключением точки останова.  
  
## <a name="breakpoints"></a>Точки останова  
 Установленная точка останова отображается значком на серой полосе слева от инструкции. Этот значок называется глифом точки останова. [!INCLUDE[tsql](../../includes/tsql-md.md)] применяются к полной инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] . Когда точка останова включена, отладчик подсвечивает связанную инструкцию [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
 При наличии в строке нескольких инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] можно включить точку останова для каждой из них. При щелчке серой полосы в левой части окна переключается точка останова для первой инструкции в строке. Чтобы переключить точку останова следующей инструкции, выделите любую часть этой инструкции или переместите курсор в нее и нажмите клавишу F9 либо выберите команду **Переключить точку останова** в меню **Отладка** . Нескольким точкам останова в одной строке соответствует одна глифом точки останова.  
  
 После переключения точки останова можно выполнять различные действия с точкой останова, например изменить свойства или временно отключить. Дополнительные сведения см. в разделе [Точки останова Transact-SQL](../../relational-databases/scripting/transact-sql-breakpoints.md).  
  
## <a name="toggle-a-breakpoint"></a>Переключение точки останова  
 **Переключение точки останова на инструкции языка Transact-SQL**  
  
1.  Щелкните серую полосу слева от инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
2.  Выделите любую часть инструкции или переместите курсор в инструкцию и выполните любое из следующих действий.  
  
    -   Нажмите клавишу F9.  
  
    -   В меню **Отладка** выбрать пункт **Переключить точку останова**.  
  
  
