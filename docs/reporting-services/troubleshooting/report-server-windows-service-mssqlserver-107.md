---
title: Служба Windows сервера отчетов (MSSQLServer) 107 | Документы Майкрософт
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: troubleshooting
ms.topic: conceptual
helpviewer_keywords:
- MSSQLServer 107 error
ms.assetid: 52b5704b-27f9-400a-a821-d8fa0786afe4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 0133ef77db176910c33ae8e78174cb5c3e507c3c
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "65575548"
---
# <a name="report-server-windows-service-mssqlserver-107"></a>Служба Windows сервера отчетов (MSSQLServer) 107
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Идентификатор события|107|  
|Источник события|Служба Windows сервера отчетов|  
|Компонент|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|Текст сообщения|Служба Windows сервера отчетов (MSSQLSERVER) не может соединиться с базой данных сервера отчетов.|  
  
## <a name="explanation"></a>Объяснение  
 Службе сервера отчетов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не удается соединиться с базой данных сервера отчетов. Такая ошибка возникает при перезапуске службы, если не удается установить соединение с базой данных сервера отчетов. Эта ошибка возникает при следующих условиях.  
  
-   Компонент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] — служба не была запущена в момент запуска службы сервера отчетов.  
  
-   Не удалось установить соединение со службой компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] , так как не включено использование удаленных соединений или протокола TCP/IP.  
  
-   База данных сервера отчетов настроена неправильно.  
  
-   Учетная запись службы настроена неправильно или не имеет разрешений для доступа к базе данных сервера отчетов. Это может произойти в том случае, если настройка учетной записи или базы данных сервера отчетов производилась не через программу настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
## <a name="user-action"></a>Действие пользователя  
 Если служба компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] еще не запущена, то запустите ее и убедитесь, что включены удаленные соединения для протокола TCP/IP.  
  
 Производите настройку базы данных сервера отчетов и учетной записи службы при помощи программы настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
## <a name="internal-only"></a>Только для внутреннего использования  
  
## <a name="see-also"></a>См. также:  
 [Настройка учетной записи службы сервера отчетов (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Использование диспетчера конфигурации служб Reporting Services (собственный режим)](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md)   
 [Запуск и остановка службы сервера отчетов](../../reporting-services/report-server/start-and-stop-the-report-server-service.md)  
  
  
