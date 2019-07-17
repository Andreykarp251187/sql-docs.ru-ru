---
title: Импорт из Power Pivot в службах Analysis Services | Документация Майкрософт
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 21abcfbec94808df6560af887ff0598d97fcb068
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68207676"
---
# <a name="import-from-power-pivot"></a>Импорт из Power Pivot 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  В этой статье описывается создание нового проекта табличной модели путем импорта метаданных и данных из [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] книги с помощью импорта из [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] шаблона проекта в [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
## <a name="create-a-new-tabular-model-from-a-power-pivot-for-excel-file"></a>Создание новой табличной модели из файла Power Pivot для Excel  
 Метаданные, импортируемые из книги [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] при создании нового проекта табличной модели и определяющие структуру книги, используются для создания и определения структуры проекта табличной модели в [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]. Такие объекты, как таблицы, столбцы, меры и связи, сохраняются, а затем появляются в проекте табличной модели, как в книге [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Изменения в файл книги XLSX не вносятся.  
  
> [!NOTE]  
>  Связанные таблицы не поддерживаются в табличных моделях. При импорте связанных таблиц из книги [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] данные из них обрабатываются как вставленные с помощью операции копирования и вставки и сохраняются в файле Model.bim. При просмотре свойств таблицы, вставленной с помощью операции копирования и вставки, свойство **Исходные данные** и диалоговое меню **Свойства таблицы** в меню **Таблица** отключены.  
>   
>  Существует ограничение в 10 000 строк, которые можно добавить к данным, внедренным в модель. Если при импорте модели из [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] и отображается ошибка «данные были усечены. Вставленные таблицы не может содержать более 10000 строк», то необходимо исправить [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] моделирования, переместив внедренные данные в другой источник данных, например таблицу SQL Server и затем повторно импортировать.  
  
 В зависимости от того, находится база данных рабочей области в экземпляре служб Analysis Services, расположенном на одном компьютере (локальном) со средой [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] , или на удаленном экземпляре служб Analysis Services, нужно учитывать особые требования.  
  
 Если база данных рабочей области находится в локальном экземпляре служб Analysis Services, то из книги [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] можно импортировать и метаданные, и данные. Метаданные копируются из книги и используются для создания проекта табличной модели. Затем данные копируются из книги и хранятся в базе данных рабочей области проекта (за исключением данных копирования и вставки, который хранится в файле Model.bim).  
  
 Если база данных рабочей области находится на удаленном экземпляре служб Analysis Services, то импортировать данные из книги [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для Excel нельзя. Метаданные при этом импортировать можно, однако в этом случае скрипт будет выполняться на удаленном экземпляре служб Analysis Services. Метаданные следует импортировать только из доверенных книг [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Данные должны быть повторно импортированы из источников, определенных в подключениях к источнику данных. Скопированные и вставленные, а также связанные табличные данные из книги [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] необходимо скопировать и вставить в проект табличной модели.  
  
#### <a name="to-create-a-new-tabular-model-project-from-a-power-pivot-for-excel-file"></a>Создание нового проекта табличной модели из файла Power Pivot для Excel  
  
1.  В среде [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]в меню **Файл** выберите пункт **Создать**, а затем выберите пункт **Проект**.  
  
2.  В диалоговом окне **Создание проекта** выберите в разделе **Установленные шаблоны** пункт **Бизнес-аналитика**, затем нажмите кнопку **Импортировать из [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]** .  
  
3.  В поле  **Имя**введите имя проекта, укажите расположение и имя решения, а затем нажмите кнопку **ОК**.  
  
4.  В диалоговом окне **Открыть** выберите файл [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] , содержащий необходимые для импорта метаданные модели и данные, и нажмите кнопку **Открыть**.  
  
## <a name="see-also"></a>См. также  
 [База данных рабочей области](../../analysis-services/tabular-models/workspace-database-ssas-tabular.md)   
 [Копирование и вставка данных](../../analysis-services/tabular-models/ssas-import-data-copy-and-paste-data.md)  
  
  
