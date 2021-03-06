---
description: Параметры проекта (сопоставление типов) (Акцесстоскл)
title: Параметры проекта (сопоставление типов) (Акцесстоскл) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Access data types
- data types, default mappings
- default data type mappings
- Project Settings dialog box, Type Mapping
- SQL Server data types
- Type Mapping settings
ms.assetid: b87b9683-abed-4677-8c50-18bdba704655
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 48054f25a5c7156a6d9d25d4770d19437d9dbadf
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88454307"
---
# <a name="project-settings-type-mapping-accesstosql"></a>Параметры проекта (сопоставление типов) (Акцесстоскл)
Параметры проекта сопоставления типов позволяют задать сопоставления типов по умолчанию для проекта SSMA. Можно также указать сопоставления типов для отдельных объектов базы данных. Дополнительные сведения см. в разделе [Сопоставление исходных и целевых типов данных](mapping-source-and-target-data-types-accesstosql.md).  
  
Сопоставление типов доступно в диалоговых окнах **Параметры проекта** и **Параметры проекта по умолчанию** :  
  
-   Используйте диалоговое окно **Параметры проекта** , чтобы задать параметры конфигурации для текущего проекта. Чтобы получить доступ к параметрам сопоставления типов, в меню **Сервис** выберите пункт **Параметры проекта**, а затем на панели слева щелкните **Сопоставление типов** .  
  
-   Используйте диалоговое окно **Параметры проекта по умолчанию** , чтобы задать параметры конфигурации для всех проектов. Чтобы получить доступ к параметрам сопоставления типов, в меню **Сервис** выберите **Параметры проекта по умолчанию**, выберите тип проекта миграции, для которого необходимо просмотреть параметры,/чанжед из раскрывающегося списка **версия целевого объекта миграции** , а затем щелкните **Сопоставление типов** в левой области.  
  
## <a name="options"></a>Варианты  
**Тип источника**  
Тип данных Access для сопоставлений.  
  
**Тип целевого объекта**  
Целевой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure тип данных для указанного типа данных Access.  
  
В следующей таблице показано сопоставление по умолчанию между исходным и целевым типами данных.  
  
|Тип данных Access|Тип данных SQL Server|  
|--------------------|------------------------|  
|**Binary [ \* .. \* ]**|**varbinary [ \* ]**|  
|**boolean**|**bit**|  
|**byte**|**tinyint**|  
|**режиме**|**money**|  
|**date**|**datetime**|  
|**decimal**|**float**|  
|**double**|**float**|  
|**guid**|**uniqueidentifier**|  
|**integer**|**smallint**|  
|**long**|**int**|  
|**лонгбинари**|**varbinary(max)**|  
|**memo**|**nvarchar(max)**|  
|**МЕМО** — для Access 97|**varchar(max)**|  
|**single**|**real**|  
|**Text [ \* .. \* ]**|**nvarchar [ \* ]**|  
|**Text [ \* .. \* ]** — для Access 97|**varchar [ \* ]**|  
  
**Добавление**  
Нажмите, чтобы добавить тип данных в список сопоставления.  
  
**Edit** (Изменение)  
Нажмите, чтобы изменить тип данных в списке сопоставление.  
  
**Удалить**  
Нажмите, чтобы удалить выбранное сопоставление типа данных из списка сопоставления.  
  
**Сброс до значений по умолчанию**  
Нажмите, чтобы сбросить все сопоставления типов данных на значения SSMA по умолчанию.  
  
## <a name="see-also"></a>См. также  
[Сопоставление исходного и целевого типов данных](mapping-source-and-target-data-types-accesstosql.md)  
[Справочник по пользовательскому интерфейсу (доступ)](https://msdn.microsoft.com/af24c303-4a41-449b-9c86-d6558a97e839)  
  
