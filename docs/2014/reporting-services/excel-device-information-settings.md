---
title: Настройки сведений об устройстве Excel | Документы Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- device information settings [Reporting Services], Excel rendering
- Excel [Reporting Services], rendering
ms.assetid: bb5f3566-f033-4470-be87-1f52fb7a4ab6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5d1ec9b650592be41c8ae2f7043649c91ea78442
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63164575"
---
# <a name="excel-device-information-settings"></a>Настройки сведений об устройстве Excel
  В следующей таблице перечислены настройки сведений об устройстве для подготовки к просмотру в формате [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] .  
  
|Параметр|Значение|  
|-------------|-----------|  
|**OmitDocumentMap**|Показывает, нужно ли исключать схему документа из параметров отчетов, поддерживающих ее. Значение по умолчанию — `false`.|  
|**OmitFormulas**|Показывает, нужно ли исключать формулы из отчета, готового для просмотра. Значение по умолчанию — `false`.|  
|`SimplePageHeade`rs|Показывает, преобразуется ли верхний колонтитул страницы отчетов в верхний колонтитул Excel при подготовке к просмотру. Значение `false` показывает, что верхний колонтитул страницы при подготовке к просмотру преобразуется в первую строку листа. Значение по умолчанию — `false`.|  
  
## <a name="see-also"></a>См. также  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Передача настроек сведений об устройстве модулям подготовки отчетов к просмотру](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Настройка параметров модулей подготовки отчетов в RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Технический справочник (службы SSRS)](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
