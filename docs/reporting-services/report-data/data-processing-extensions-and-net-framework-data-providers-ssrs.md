---
title: Модули обработки данных и поставщики данных .NET Framework (службы SSRS) | Документы Майкрософт
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-data
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], data
- data processing extensions [Reporting Services]
- data providers [Reporting Services]
- data retrieval [Reporting Services]
- Reporting Services, data sources
- report data [Report Builder], accessing
ms.assetid: 42a5afb5-f4c8-4957-b1fd-77bf39afa5be
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 424dbb31ab96153dbf959c304456d8d1b2e4abd0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65573102"
---
# <a name="data-processing-extensions-and-net-framework-data-providers-ssrs"></a>Модули обработки данных и поставщики данных .NET Framework (службы SSRS)
  Модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] — это компонент, устанавливаемый вместе со службами [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]и предназначенный для получения данных из источников данных конкретного типа, а также предоставляющий дополнительную поддержку при проектировании и обработке отчетов. Модуль обработки данных служб [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] — это компонент, предоставляемый [!INCLUDE[msCoName](../../includes/msconame-md.md)] или сторонними поставщиками, который поддерживает интерфейсы <xref:System.Data> , позволяющие получать и изменять данные из источника данных определенного типа.  
  
## <a name="understanding-a-data-processing-extension"></a>Основные сведения о модуле обработки данных  
 Модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] поддерживает подмножество интерфейсов <xref:System.Data> . Для модулей обработки данных необходим лишь доступ только для чтения к источнику данных, поэтому интерфейсы для операций записи и обновления не реализованы. Каждый модуль обработки данных может предоставлять пользовательские функции обработки отчетов. Например, модуль обработки данных может поддерживать следующие типы функций.  
  
-   Управление учетными данными отдельно от строки соединения  
  
-   Поддержка многозначных параметров  
  
-   Получение серверных статистических значений, вычисленных в источнике данных  
  
-   Получение свойств данных, а также значений данных из источника данных  
  
## <a name="understanding-a-data-provider"></a>Основные сведения о поставщике данных  
 Модуль обработки данных служб [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] (иногда называемый драйвером) поддерживает стандартный набор интерфейсов <xref:System.Data> для операций чтения, записи и обновления данных в источнике данных. Поставщик данных может использоваться при отсутствии доступного модуля обработки данных для конкретного типа источника данных. Доступно много стандартных поставщиков данных [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] сторонних производителей.  
  
 Поскольку службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] имеют расширяемую архитектуру поставщиков данных, существует возможность создания специализированного модуля обработки данных, содержащего дополнительную функциональность, расширяющую возможности модулей обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Дополнительные сведения см. в разделе [Implementing a Data Processing Extension](../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md). Сведения о модулях обработки данных сторонних производителей см. в документации, поставляемой вместе с этими модулями.  
  
> [!NOTE]  
>  Поставщик данных [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] или специализированный модуль обработки данных необходимо установить и зарегистрировать, прежде чем его можно будет использовать для доступа к данным из источника данных. Чтобы можно было просматривать опубликованный отчет, модуль обработки данных должен быть установлен и зарегистрирован на компьютере клиента для разработки отчета, и на сервере отчетов для просмотра опубликованного отчета. Не все поставщики данных предназначены для работы в серверной среде. Дополнительные сведения см. в статьях [Регистрация стандартного поставщика данных .NET Framework (службы SSRS)](../../reporting-services/report-data/register-a-standard-net-framework-data-provider-ssrs.md).и [Развертывание модуля обработки данных](../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension.md).  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о модулях обработки данных](../../reporting-services/extensions/data-processing/data-processing-extensions-overview.md)   
 [Внедренные и общие наборы данных отчета (построитель отчетов и службы SSRS)](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
  
  
