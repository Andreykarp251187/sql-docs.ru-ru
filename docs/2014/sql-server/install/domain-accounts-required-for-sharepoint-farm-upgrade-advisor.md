---
title: Учетные записи домена, необходимые для фермы SharePoint (Советник по переходу) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 90cd6d3e-a271-4cb8-81f2-fc555b2d3cab
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 983e01046fd90fbaf8d9ff680492f1b385435f61
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63253575"
---
# <a name="domain-accounts-required-for-sharepoint-farm-upgrade-advisor"></a>Для фермы SharePoint требуются учетные записи домена (советник по переходу)
  Продукты SharePoint, которые настроены для среды ферм, требуют использования учетных записей домена.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Режиме интеграции с SharePoint.|  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssRS](../../includes/ssrs.md)]  
  
### <a name="description"></a>Описание  
 Продукты SharePoint, настроенные для среды ферм, требуют использования учетных записей домена для служб и подключений к базе данных. Это касается учетной записи, заданной в качестве учетной записи службы Reporting Services.  
  
 Страницы центра администрирования SharePoint 2010 — единственное место, где можно увидеть ошибки, если для службы Reporting Services не используется учетная запись пользователя домена. При попытке настройки интеграции служб Reporting Services будет выдано сообщение об ошибке следующего содержания:  
  
 «Сервер отчетов запущен от имени встроенной учетной записи NT AUTHORITY\NETWORK SERVICE, которая не поддерживается установкой фермы SharePoint. Необходимо повторно настроить службу сервера отчетов для запуска от имени учетной записи пользователя домена».  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Для [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и предыдущих версий, используйте диспетчер конфигурации служб Reporting Services, чтобы изменить учетную запись, которой назначена как учетная запись службы сервера отчетов.  
  
#### <a name="to-change-the-service-account-from-configuration-manager"></a>Изменение учетной записи службы, используйте диспетчер конфигурации  
  
1.  Из **запустить** меню, выберите **все программы**, а затем нажмите кнопку **Microsoft SQL Server 2008 R2**.  
  
2.  Выберите **средства настройки**, а затем нажмите кнопку **диспетчер конфигурации служб Reporting Services**.  
  
3.  В Configuration Manager выберите **учетной записи службы** вкладки.  
  
4.  Выберите **использовать другую учетную запись** и введите учетные данные для учетной записи домена.  
  
5.  Нажмите кнопку **Применить**.  
  
## <a name="see-also"></a>См. также  
 [Настройка учетной записи службы сервера отчетов (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)  
  
  
