---
title: Свойства сервера (страница "Ведение журнала") | Документация Майкрософт
ms.date: 06/10/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: tools
ms.topic: conceptual
f1_keywords:
- sql13.swb.reportserver.serverproperties.logging.f1
ms.assetid: b338deab-4868-4951-9f22-0605add2fc95
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 9e9286363970b568e0690b622fac6d94c2b01f6b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65571390"
---
# <a name="server-properties-logging-page"></a>Свойства сервера (страница «Регистрация»)
  Эта страница [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] используется в [!INCLUDE[ssManStudioFull_md](../../includes/ssmanstudiofull-md.md)] для задания предельных значений данных, собираемых сервером отчетов при выполнении отчета. Данные выполнения сохраняются самим приложением в базе данных сервера отчетов. Предусмотрена возможность отслеживать действия с отчетами применительно к серверу отчетов, который работает в собственном режиме или в режиме интеграции с SharePoint. Если сервер отчетов представляет собой часть масштабного развертывания, то в журнале выполнения отчета ведется регистрация всех действий с отчетами для всего проекта развертывания в виде одного файла журнала.  
  
 Чтобы открыть эту страницу:
 1) Запуск [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]
 2) Подключитесь к серверу отчетов.
 3) Щелкните правой кнопкой мыши имя сервера отчетов и выберите пункт **Свойства**. 
 4) Нажмите кнопку **Ведение журнала** , чтобы открыть эту страницу.  
  
## <a name="options"></a>Параметры  
 **Включить ведение журнала выполнения отчета**  
 Щелкните, чтобы создать и сохранить данные о действиях с отчетами на сервере. Если этот параметр включен, то сервер отчетов отслеживает используемые отчеты, частоту выполнения отчетов, типы выполненных операций с отчетами, форматы вывода и тех, кто вызвал отчет на выполнение. Дополнительные сведения о других данных, регистрируемых в журнале, см. в разделе [Журнал выполнения сервера отчетов и представление ExecutionLog3](../../reporting-services/report-server/report-server-executionlog-and-the-executionlog3-view.md).  
  
 **Удалить записи журнала, произведенные более заданного количества дней тому назад**  
 Задается количество дней, после которого записи журнала будут удалены из журнала выполнения отчета. Значение по умолчанию — 60 суток.  
  
## <a name="see-also"></a>См. также:  
 [Установка свойств сервера отчетов (среда Management Studio)](../../reporting-services/tools/set-report-server-properties-management-studio.md)   
 [Подключение к серверу отчетов в среде Management Studio](../../reporting-services/tools/connect-to-a-report-server-in-management-studio.md)   
 [Файлы и источники журналов служб Reporting Services](../../reporting-services/report-server/reporting-services-log-files-and-sources.md)   
 [Справка F1 по использованию сервера отчетов среде Management Studio](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)   
 [Журнал выполнения сервера отчетов и представление ExecutionLog3](../../reporting-services/report-server/report-server-executionlog-and-the-executionlog3-view.md)  
  
  
