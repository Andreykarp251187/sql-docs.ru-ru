---
title: Включение регулятора ресурсов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, enabling
ms.assetid: 4d17af53-cf11-4ce4-aab4-deda94a49836
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 5ef8d77de1df31387d33e6577fe84bd5ef9fa680
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63216024"
---
# <a name="enable-resource-governor"></a>Активация регулятора ресурсов
  Регулятор ресурсов отключен по умолчанию. Регулятор ресурсов можно включить с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или Transact-SQL.  
  
-   **Перед началом:**  [ограничения](#LimitationsRestrictions), [разрешения](#Permissions)  
  
-   **Включение Resource Governor с использованием:**  [обозревателя объектов](#RGOnObjEx), [свойств Resource Governor](#RGOnProp), [Transact-SQL](#RGOnTSQL)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
 В результате включения регулятора ресурсов произойдет следующее.  
  
-   Будет выполнена функция-классификатор для новых соединений, что позволит связать их рабочую нагрузку с определенными группами рабочей нагрузки.  
  
-   Ограничения ресурсов, заданные в конфигурации регулятора ресурсов, будут соблюдены и применены.  
  
-   Запросы, которые существовали до включения регулятора ресурсов, будут испытывать воздействие всех изменений конфигурации, которые были внесены, пока регулятор ресурсов был отключен.  
  
###  <a name="LimitationsRestrictions"></a> Ограничения  
 В ходе пользовательской транзакции нельзя использовать инструкцию `ALTER RESOURCE GOVERNOR` для включения регулятора ресурсов.  
  
###  <a name="Permissions"></a> Permissions  
 Для включения регулятора ресурсов требуется разрешение CONTROL SERVER.  
  
##  <a name="RGOnObjEx"></a> Включение регулятора ресурсов с использованием обозревателя объектов  
 **Включение регулятора ресурсов с помощью обозревателя объектов**  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]откройте обозреватель объектов и рекурсивно разверните узел **Управление** вплоть до узла **Регулятор ресурсов**.  
  
2.  Щелкните элемент **Resource Governor**правой кнопкой мыши и выберите команду **Включить**.  
  
##  <a name="RGOnProp"></a> Включение регулятора ресурсов с применением свойств регулятора ресурсов  
 **Включение регулятора ресурсов с использованием страницы свойств регулятора ресурсов**  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]откройте обозреватель объектов и рекурсивно разверните узел **Управление** вплоть до узла **Регулятор ресурсов**.  
  
2.  Щелкните правой кнопкой мыши элемент **Resource Governor** и выберите пункт **Свойства**, после чего откроется страница **Свойства Resource Governor** .  
  
3.  Установите флажок **Включить регулятор ресурсов** и нажмите кнопку **ОК**.  
  
##  <a name="RGOnTSQL"></a> Включение регулятора ресурсов с применением Transact-SQL  
 **Включение регулятора ресурсов с применением Transact-SQL**  
  
1.  Выполните инструкцию **ALTER RESOURCE GOVERNOR RECONFIGURE** .  
  
### <a name="example-transact-sql"></a>Пример (Transact-SQL)  
 В следующем примере показано включение регулятора ресурсов.  
  
```  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [регулятор ресурсов](resource-governor.md)   
 [Отключение регулятора ресурсов](disable-resource-governor.md)   
 [Пул ресурсов регулятора ресурсов](resource-governor-resource-pool.md)   
 [Группа рабочей нагрузки регулятора ресурсов](resource-governor-workload-group.md)   
 [Функция-классификатор регулятора ресурсов](resource-governor-classifier-function.md)   
 [ALTER RESOURCE GOVERNOR (Transact-SQL)](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
