---
title: Просмотр XML-служб Analysis Services Project (SSDT) | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b1542c33d67c95c1c7154d08dbffd550b5f8cc72
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62743140"
---
# <a name="view-the-xml-for-an-analysis-services-project-ssdt"></a>Просмотр XML-кода проекта служб Analysis Services (среда SSDT)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  При работе с базой данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме проекта среда [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] создает определение XML для каждого объекта в папке проекта. В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]можно просмотреть содержимое файла XML для каждого объекта. XML-файл можно редактировать напрямую, однако в большинстве случаев это не рекомендуется, так как может привести к нечитабельности XML-файла в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
> [!NOTE]  
>  Код XML всего проекта посмотреть нельзя, но можно просмотреть код для каждого объекта, так как для каждого объекта существуют отдельные файлы. Единственный способ просмотреть код всего проекта — построить проект и посмотреть код ASSL код в \<имя проекта > файл с расширением asdatabase.  
  
### <a name="to-view-the-xml-code-for-an-object"></a>Просмотр XML-кода объекта  
  
1.  Откройте проект служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
2.  В обозревателе решений щелкните правой кнопкой мыши объект и выберите пункт **Просмотр кода**.  
  
     XML-код объекта появится в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Построение проектов служб Analysis Services (среда SSDT)](../../analysis-services/multidimensional-models/build-analysis-services-projects-ssdt.md)  
  
  
