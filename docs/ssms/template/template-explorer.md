---
title: Обозреватель шаблонов | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.swb.templates.explorer.f1
- sql13.wb.templates.f1
helpviewer_keywords:
- templates [SQL Server]
- SQL Server Management Studio [SQL Server], Template Explorer
- Template Explorer
- templates [Transact-SQL]
- templates [SQL Server], Template Explorer
ms.assetid: b9ee55c5-bb44-4f76-90ac-792d8d83b4c8
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 7268e5c4b04688f055c0e9f7149446f836d17379
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65102661"
---
# <a name="template-explorer"></a>Template Explorer
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет целый ряд шаблонов. Шаблоны — это файлы со стандартным текстом, содержащие скрипты SQL, которые помогают создавать объекты в базе данных. После первого открытия обозревателя шаблонов копия шаблонов помещается в папку пользователя "AppData\Roaming\Microsoft\SQL Server Management Studio\130\Templates" в "C:\Users".  
  
Предусмотрена возможность просматривать доступные шаблоны в обозревателе шаблонов, затем открывать шаблон для включения его кода в окно редактора кода. Можно также создавать пользовательские шаблоны.  
  
## <a name="benefits-of-templates"></a>Преимущества шаблонов  
Шаблоны доступны для решений, проектов и различных типов редакторов кода. Имеются шаблоны создания таких объектов, как базы данных, таблицы, представления, индексы, хранимые процедуры, триггеры, статистические данные и функции. Кроме того, есть такие шаблоны, которые помогают управлять сервером путем создания расширенных свойств, связанных серверов, имен входа, ролей, пользователей и шаблонов для [!INCLUDE[ssASnoversion](../../includes/ssasnoversion_md.md)].  
  
Шаблоны, поставляемые со среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , содержат параметры для облегчения настройки кода. После открытия шаблона используйте диалоговое окно **Замена параметров шаблона** для вставки значений в скрипт.  
  
Для часто выполняемых задач можно создать пользовательские шаблоны. Организуйте свои скрипты в существующих папках или создайте новую структуру файлов.  
  
Кроме того, редактор запросов компонента [!INCLUDE[ssDE](../../includes/ssde_md.md)] позволяет вставить фрагменты кода в скрипт, для чего достаточно щелкнуть правой кнопкой мыши в нужном месте скрипта.  
  
## <a name="related-tasks"></a>Связанные задачи  
Используйте следующие разделы, чтобы приступить к работе с шаблонами  
  
|**Description**|**Раздел**|  
|-------------------|-------------|  
|Описано, как включить код из шаблона в окно редактора кода.|[Открытие шаблона](../../ssms/template/open-a-template.md)|  
|Описано, как заменить значения параметров шаблона после открытия шаблона в редакторе кода.|[Замена параметров шаблона](../../ssms/template/replace-template-parameters.md)|  
  
