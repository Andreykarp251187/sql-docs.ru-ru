---
title: Справочник по библиотеке поставщика WMI служб Reporting Services (SSRS) | Документы Майкрософт
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
apiname:
- Reporting Services WMI Provider Library
apilocation:
- reportingservices.mof
helpviewer_keywords:
- WMI provider [Reporting Services], library
ms.assetid: 17ba711d-7eff-4423-9168-63dc425a3428
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: af3b51f934b9b0221747116772af7a747813e70f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65571057"
---
# <a name="reporting-services-wmi-provider-library-reference-ssrs"></a>Справочник по библиотеке поставщика WMI служб Reporting Services (SSRS)
  Поставщик WMI служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] поддерживает операции WMI, позволяющие создавать скрипты и код для изменения параметров сервера и диспетчера отчетов.  
  
 Например, чтобы изменить режим использования встроенной безопасности при соединении сервера отчетов с его базой данных, создайте экземпляр класса MSReportServer_ConfigurationSetting и воспользуйтесь свойством DatabaseIntegratedSecurity экземпляра сервера отчетов. Классы, показанные в следующей таблице, представляют компоненты служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Классы определены в пространстве имен [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)] или [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)] . Все они поддерживают операции считывания и записи. Операции создания не поддерживаются.  
  
## <a name="classes"></a>Классы  
 [Класс MSReportServer_Instance](../../reporting-services/wmi-provider-library-reference/msreportserver-instance-class.md)  
 Основные сведения, необходимые клиенту для подключения к установленному серверу отчетов.  
  
 [Класс MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
 Представляет установочные параметры и параметры времени выполнения для экземпляра сервера отчетов. Эти параметры хранятся в файле конфигурации для сервера отчетов.  
  
 Дополнительные сведения об операциях WMI см. в документации по пакету SDK WMI, который поставляется вместе с пакетом SDK для [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] .  
  
## <a name="see-also"></a>См. также:  
 [Доступ к поставщику WMI для служб Reporting Services](../../reporting-services/tools/access-the-reporting-services-wmi-provider.md)   
 [Технический справочник (службы SSRS)](../../reporting-services/technical-reference-ssrs.md)  
  
  
