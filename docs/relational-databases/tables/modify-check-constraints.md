---
title: Изменение проверочного ограничения | Документация Майкрософт
ms.custom: ''
ms.date: 06/28/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- CHECK constraints, modifying
- modifying constraints
- constraints [SQL Server], check
- constraints [SQL Server], modifying
ms.assetid: f22daef8-e350-40ef-8ff0-b5f87d1d9e56
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 35ab525e1420d5e8db2a63f4892d8e17a3673158
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68139619"
---
# <a name="modify-check-constraints"></a>Изменение проверочного ограничения
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Изменение проверочных ограничений в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] осуществляется в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] , если необходимо изменить выражение ограничения или параметры, включающие или отключающие ограничение для конкретных условий.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [безопасность](#Security)  
  
-   **Изменение проверочного ограничения с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Требуется разрешение ALTER на таблицу.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-modify-a-check-constraint"></a>Изменение проверочного ограничения  
  
1.  В **обозревателе объектов**щелкните правой кнопкой мыши таблицу, содержащую проверочное ограничение, и выберите пункт **Конструктор**.  
  
2.  В меню **Конструктор таблиц** выберите **Проверочные ограничения...** .  
  
3.  В диалоговом окне **Проверочные ограничения** выберите ограничение, которое нужно изменить, из списка **Выбранное проверочное ограничение**.  
  
4.  Выполните действие из следующей таблицы.  
  
    |Чтобы|Выполните следующее|  
    |--------|------------------------|  
    |Изменить выражение ограничения|Введите новое выражение в поле **Выражение** .|  
    |Переименуйте ограничение|Введите новое имя в поле **Имя** .|  
    |Применить ограничение к существующим данным|Установите флажок **Проверить существующие данные при создании или включении** .|  
    |Отключить ограничение при добавлении в таблицу новых данных или обновлении существующих данных таблицы.|Снимите флажок **Принудительное ограничение для инструкций INSERT и UPDATE** .|  
    |Отключить ограничение при вставке или обновлении данных в таблице агентом репликации.|Снимите флажок **Включить использование для репликации** .|  
  
    > [!NOTE]  
    >  В некоторых базах данных проверочные ограничения различаются по функциональности.  
  
5.  Щелкните **Закрыть**.  
  
6.  В меню **Файл** выберите пункт **Сохранить**_table name_.  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Изменение проверочного ограничения**  
  
 Чтобы изменить ограничение `CHECK` с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)], нужно удалить существующее ограничение `CHECK` и повторно создать его с новым определением. Дополнительные сведения см. в разделах [Удаление проверочного ограничения](../../relational-databases/tables/delete-check-constraints.md) и [Создание ограничений CHECK](../../relational-databases/tables/create-check-constraints.md).  
  
###  <a name="TsqlExample"></a>  
