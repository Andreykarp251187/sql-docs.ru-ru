---
title: Настройка регулятора ресурсов с помощью шаблона | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, templates
ms.assetid: f342dec2-d1d6-483e-b44e-98eb7d168b5e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 3da27154a824433d214dc495bf7f236ff104274f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68198938"
---
# <a name="configure-resource-governor-using-a-template"></a>Настройка регулятора ресурсов с помощью шаблона
  Можно настроить регулятор ресурсов с помощью шаблона, имеющегося в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
-   **Перед началом:**  [Разрешения](#Permissions)  
  
-   **Создание группы рабочей нагрузки с использованием:**  [шаблон](#ConfRGTemplate)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
 С помощью дополнительных шагов можно открыть и изменить шаблон, который создает пул ресурсов и группу рабочей нагрузки для этого пула. Кроме того, данный шаблон позволяет создавать определяемую пользователем функцию-классификатор, направляющую новые соединения либо в группу по умолчанию, либо в пользовательскую группу рабочей нагрузки.  
  
###  <a name="Permissions"></a> Permissions  
 Для выполнения инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] регулятора ресурсов, содержащихся в шаблоне, требуется разрешение CONTROL SERVER.  
  
##  <a name="ConfRGTemplate"></a> Настройка регулятора ресурсов с помощью шаблона  
 **Настройка регулятора ресурсов с помощью шаблона в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]в меню **Вид** выберите пункт **Обозреватель шаблонов**.  
  
2.  В **Обозревателе шаблонов**разверните **Регулятор ресурсов**, затем дважды щелкните значок **Настройка регулятора ресурсов**.  
  
3.  В разделе **Подключение к компоненту Database Engine**введите необходимые сведения и нажмите кнопку **ОК**. В составе редактора запросов поставляется шаблон Configure Resource Governor.sql. С помощью этого шаблона можно создать и настроить пул ресурсов, группу рабочей нагрузки и функцию-классификатор.  
  
4.  Чтобы изменить значения в шаблоне, нажмите сочетание клавиш CTRL+SHIFT+M. В окне **Задание значений для параметров шаблона** введите необходимые значения.  
  
5.  Чтобы сохранить изменения, внесенные в шаблон, нажмите кнопку **ОК**.  
  
6.  Чтобы запустить запрос, нажмите кнопку **Выполнить**.  
  
## <a name="see-also"></a>См. также  
 [регулятор ресурсов](resource-governor.md)   
 [Активация регулятора ресурсов](enable-resource-governor.md)   
 [Пул ресурсов регулятора ресурсов](resource-governor-resource-pool.md)   
 [Группа рабочей нагрузки регулятора ресурсов](resource-governor-workload-group.md)   
 [Функция-классификатор регулятора ресурсов](resource-governor-classifier-function.md)   
 [Просмотр свойств регулятора ресурсов](view-resource-governor-properties.md)   
 [CREATE RESOURCE POOL (Transact-SQL)](/sql/t-sql/statements/create-resource-pool-transact-sql)   
 [CREATE WORKLOAD GROUP (Transact-SQL)](/sql/t-sql/statements/create-workload-group-transact-sql)   
 [CREATE FUNCTION (Transact-SQL)](/sql/t-sql/statements/create-function-transact-sql)   
 [ALTER RESOURCE GOVERNOR (Transact-SQL)](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
