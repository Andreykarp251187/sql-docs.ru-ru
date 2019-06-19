---
title: Методы веб-службы сервера отчетов | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Report Server Web service, methods
- Web service [Reporting Services], methods
- XML Web service [Reporting Services], features
- Web service [Reporting Services], features
- Report Server Web service, features
- XML Web service [Reporting Services], methods
ms.assetid: ce5afa27-e90c-44a7-b204-098a065b3665
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 37d0031ebfb4ec6d31da6aad9a8842c0623cb75b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63283482"
---
# <a name="report-server-web-service-methods"></a>Методы веб-службы сервера отчетов
  Веб-службы сервера отчетов содержат различные категории методов, основанных на функциях компонентов. Эти методы доступны через несколько конечных точек веб-служб (три для управления отчетами и одна для их выполнения), которые в свою очередь доступны как члены классов <xref:ReportService2010.ReportingService2010> и <xref:ReportExecution2005.ReportExecutionService>. Эти классы можно создать автоматически с помощью средства создания класса-посредника, например средства wsdl.exe, включенного в пакет SDK [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Дополнительные сведения об использовании веб-служб сервера отчетов и [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] см. в разделе [Построение приложений с помощью веб-службы и платформы .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md).  
  
## <a name="endpoints-and-methods"></a>Конечные точки и методы  
 В следующей таблице указаны конечные точки веб-службы сервера отчетов и категории методов, предоставленные конечной точкой <xref:ReportService2010.ReportingService2010>. Дополнительные сведения о методах, доступных в других конечных точках, см. в разделе [Технический справочник (службы SSRS)](../../technical-reference-ssrs.md).  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Конечные точки веб-службы сервера отчетов](report-server-web-service-endpoints.md)|Содержит описание конечных точек для управления и выполнения, используемых веб-службой сервера отчетов.|  
|[Методы управления пространством имен сервера отчетов](report-server-namespace-management-methods.md)|Описывает методы управления базой данных сервера отчетов. В частности, эти методы позволяют управлять папками и ресурсами, а также настраивать свойства элемента.|  
|[Способы авторизации](authorization-methods.md)|Описывает методы управления задачами, ролями и политиками.|  
|[Источники данных и способы подключения](data-sources-and-connection-methods.md)|Описывает методы настройки и управления соединениями с источниками данных и учетными данными для отчетов.|  
|[Методы параметров отчета](report-parameters-methods.md)|Описывает методы задания и получения параметров отчетов.|  
|[Методы моделей](../report-server-web-service.md)|Описывает методы, которые можно использовать для управления моделями.|  
|[Визуализация и методы выполнения](rendering-and-execution-methods.md)|Описывает методы управления выполнением, подготовкой к просмотру и кэшированием отчетов.|  
|[Методы журнала отчета](report-history-methods.md)|Описывает методы создания моментальных снимков журнала отчета и управления ими.|  
|[Методы планирования](scheduling-methods.md)|Описывает методы создания общих расписаний и планов обновления кэша, используемых сервером отчетов, и управления ими.|  
|[Методы подписки и доставки](subscription-and-delivery-methods.md)|Описывает методы создания и управления подписками и доставки отчетов.|  
|[Методы связанных отчетов](linked-reports-methods.md)|Описывает методы создания связанных отчетов и управления ими.|  
  
## <a name="see-also"></a>См. также  
 [Доступ к API SOAP](../accessing-the-soap-api.md)   
 [Создание приложений с помощью веб-службы и .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Веб-служба сервера отчетов](../report-server-web-service.md)   
 [Технический справочник (службы SSRS)](../../technical-reference-ssrs.md)  
  
  
