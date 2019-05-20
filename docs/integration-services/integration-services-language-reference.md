---
title: Справочник по языку служб Integration Services | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: c67b72f1-0a1e-42f0-878a-84e85efc915b
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: ea7b40ca0a7a7bd0502feb6c8613141257d3ee20
ms.sourcegitcommit: 8d288ca178e30549d793c40510c4e1988130afb0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/16/2019
ms.locfileid: "65805381"
---
# <a name="integration-services-language-reference"></a>Справочник по языку служб Integration Services

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  В этом разделе описывается API-интерфейс [!INCLUDE[tsql](../includes/tsql-md.md)] для администрирования проектов служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], которые развернуты на экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 Службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] сохраняют объекты, настройки и рабочие данные в базе данных, которая называется каталогом [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Имя каталога [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] по умолчанию — SSISDB. Объекты, которые хранятся в каталоге, включают проекты, пакеты, параметры, среды и журнал операций.  
  
 В каталоге служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] данные хранятся во внутренних таблицах, невидимых для пользователей. Однако к требуемым сведениям можно получить доступ через ряд общедоступных представлений, выполнив к ним запросы. База данных также содержит ряд хранимых процедур, которые могут использоваться для выполнения типичных задач, связанных с каталогом.  
  
 Как правило, управление объектами служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] в каталоге осуществляется путем открытия среды [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Однако можно также непосредственно использовать представления базы данных и хранимые процедуры или написать пользовательский код, который вызывает управляемый API. Среда [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] и управляемый API запрашивают представления и вызывают хранимые процедуры, описанные в этом разделе, для выполнения многих своих задач.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Представления (каталог служб Integration Services)](../integration-services/system-views/views-integration-services-catalog.md)  
 Запросы к представлениям позволяют получить доступ к объектам, настройкам и рабочим данным служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
 [Хранимые процедуры (каталог служб Integration Services)](../integration-services/system-stored-procedures/stored-procedures-integration-services-catalog.md)  
 Вызовы хранимых процедур позволяют добавлять, удалять и изменять объекты и параметры служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
 [Функции (каталог служб Integration Services)](https://msdn.microsoft.com/library/9f2aec85-3d4c-415f-b1f8-8328a60b1c7f)  
 Вызывайте функции для администрирования проектов служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
  
