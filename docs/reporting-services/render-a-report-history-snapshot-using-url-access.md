---
title: Обработка моментального снимка журнала отчета с использованием доступа по URL-адресу | Документы Майкрософт
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- URL access [Reporting Services], report history
- history snapshots [Reporting Services]
- historical data [Reporting Services]
- snapshots [Reporting Services], URL access
- snapshots [Reporting Services], rendering report history
ms.assetid: 3f87f82d-0e61-4492-9c4b-f5238c39e8cd
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 2caf9def46440aa87f8b4e143cc9e3163e408ba5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65580805"
---
# <a name="render-a-report-history-snapshot-using-url-access"></a>Обработка моментального снимка журнала отчета с использованием доступа по URL-адресу
  Подготовить отчет к просмотру можно с помощью моментального снимка журнала отчета. Для этого необходимо указать параметр *rs:Snapshot* и присвоить ему значение допустимого идентификатора моментального снимка. Значение параметра должно указываться в формате ГГГГ-ММ-ДДТЧЧ:ММ:СС согласно стандарту Международной организации по стандартизации (ISO) 8601.  
  
 Если этот параметр не указан, то отчет подготавливается к просмотру согласно параметрам его выполнения и параметрам управления кэшем на сервере отчетов. Дополнительные сведения о выполнении отчетов см. в разделе [Установка свойств обработки отчетов](../reporting-services/report-server/set-report-processing-properties.md).  
  
## <a name="example"></a>Пример  
 В приведенном ниже примере показан URL-адрес, по которому происходит получение моментального снимка журнала отчета.  
  
```  
https://myrshost/reportserver?/SampleReports/Company Sales&rs:Snapshot=2003-04-07T13:40:02  
```  
  
## <a name="see-also"></a>См. также:  
 [Доступ по URL-адресу (службы SSRS)](../reporting-services/url-access-ssrs.md)   
 [Ссылка на параметр доступа по URL-адресу](../reporting-services/url-access-parameter-reference.md)  
  
  
