---
title: Переводы куба | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 82ded06c9008e4a403e5707a4a0b2fafec261e58
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68180973"
---
# <a name="cube-translations"></a>Переводы куба
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Перевод — это простой механизм для отображения меток и заголовков на другом языке. Каждый перевод определяется как пара значений: строка с переведенным текстом и значение с идентификатором языка. Переводы доступны для всех объектов в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Значения атрибутов измерений также можно перевести. Клиентское приложение отвечает за поиск языка, заданного пользователем, и отображения на этом языке всех меток и заголовков. Объект может иметь неограниченное число переводов.  
  
 Простой объект <xref:Microsoft.AnalysisServices.Translation> содержит кода языка и переведенного заголовка. — Номер идентификатора языка **целое число** с идентификатором языка. Переведенное текстовое обозначение является заголовком.  
  
 В [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], Переводы куба представляют зависящие от языка представление имени объекта куба, например заголовка или папки отображения. Службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] также поддерживают переводы имен измерений и элементов.  
  
 Переводы обеспечивают серверную поддержку клиентских приложений, которые поддерживают несколько языков. Часто данные куба просматривают пользователи из разных стран. Полезно иметь возможность переводить различные элементы куба на другой язык, чтобы пользователи в разных странах могли просматривать и понимать метаданные куба. Например, если пользователь из Франции обращается к кубу с рабочей станции, имеющей французскую локаль, он видит значения свойств объекта на французском языке. Аналогично пользователь в Германии может обращаться к тому же кубу с рабочей станции с немецкой локалью и просматривать значения свойств объекта на немецком языке.  
  
 Сведения о параметрах сортировки и языке для компьютера клиента хранятся в виде кода локали. При соединении клиент передает идентификатор языка экземпляру служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Экземпляр использует этот код языка, чтобы определить, какой набор переводов необходимо использовать при предоставлении метаданных для объектов служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] для каждого пользователя. Если объект служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] не содержит заданного перевода, то для возвращения содержимого обратно клиенту используется язык по умолчанию.  
  
## <a name="see-also"></a>См. также  
 [Переводы измерений](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimension-translations.md)   
 [Поддержка параметров перевода в службах Analysis Services](../../analysis-services/translation-support-in-analysis-services.md)   
 [Советы и рекомендации по глобализации (службы Analysis Services)](../../analysis-services/globalization-tips-and-best-practices-analysis-services.md)  
  
  
