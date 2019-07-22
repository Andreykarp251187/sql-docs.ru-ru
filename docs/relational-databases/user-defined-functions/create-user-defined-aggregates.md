---
title: Создание определяемых пользователем агрегатных функций | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- aggregate functions [SQL Server], user-defined
- user-defined functions [CLR integration]
ms.assetid: c278b746-6323-4b32-b460-239915acc067
author: rothja
ms.author: jroth
ms.openlocfilehash: 8e4291cbe79bf0eea51fdf10e2c13fea7f1e23a0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68138353"
---
# <a name="create-user-defined-aggregates"></a>Создание определяемых пользователем агрегатных функций
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]
  Можно создать объект базы данных внутри [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , который запрограммирован в сборке среды CLR. В число объектов базы данных, способных эффективно использовать предоставляемую средой CLR многофункциональную модель программирования, входят триггеры, хранимые процедуры, функции, агрегатные функции и типы.  
  
 Подобно встроенным агрегатным функциям, предоставленным в [!INCLUDE[tsql](../../includes/tsql-md.md)], пользовательские агрегатные функции производят вычисление в ряде значений и возвращают одиночное значение.  
  
 Создание пользовательской агрегатной функции в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] включает в себя следующие шаги.  
  
-   Определите пользовательскую агрегатную функцию как класс на языке, поддерживаемом платформой [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET. Дополнительные сведения о программировании определяемых пользователем статистических функций в среде CLR см. в статье [Пользовательские агрегатные функции среды CLR](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md). Скомпилируйте этот класс для построения сборки среды CLR, используя соответствующий языку компилятор.  
  
-   Зарегистрируйте сборку в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью инструкции CREATE ASSEMBLY. Дополнительные сведения о работе со сборками в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в статье [Сборки (компоненты Database Engine)](../../relational-databases/clr-integration/assemblies-database-engine.md).  
  
-   Создайте пользовательское статистическое выражение, которое ссылается на зарегистрированную сборку, используя инструкцию CREATE AGGREGATE.  
  
> [!NOTE]
>  Развертывание проекта SQL Server в [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] регистрирует сборку в базе данных, указанной для проекта. Развертывание проекта также создает пользовательские статистические функции в базе данных для всех классов, которые могут иметь атрибут **SqlUserDefinedAggregate** . Дополнительные сведения см. в статье [Deploying CLR Database Objects](../../relational-databases/clr-integration/deploying-clr-database-objects.md).  
> 
> [!NOTE]
>  Возможность [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполнять код CLR по умолчанию отключена. Можно создавать, изменять и удалять объекты базы данных, которые ссылаются на модули управляемого кода, но эти ссылки не будут выполнены в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , пока параметр [clr enabled](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) не получит значение True с помощью хранимой процедуры [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md).  
  
 **Создание, изменение или удаление сборки**  
  
-   [CREATE ASSEMBLY (Transact-SQL)](../../t-sql/statements/create-assembly-transact-sql.md)  
  
-   [ALTER ASSEMBLY (Transact-SQL)](../../t-sql/statements/alter-assembly-transact-sql.md)  
  
-   [DROP ASSEMBLY (Transact-SQL)](../../t-sql/statements/drop-assembly-transact-sql.md)  
  
 **Создание пользовательской статистической функции**  
  
-   [CREATE AGGREGATE (Transact-SQL)](../../t-sql/statements/create-aggregate-transact-sql.md)  
  
## <a name="see-also"></a>См. также:  
 [Основные понятия о программировании интеграции со средой (CLR)](../../relational-databases/clr-integration/common-language-runtime-clr-integration-programming-concepts.md)  
  
  
