---
title: Реализация модуля доставки | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery [Reporting Services]
- custom delivery extensions [Reporting Services]
- extensions [Reporting Services], delivery
- delivery extensions [Reporting Services]
ms.assetid: 600cd229-efcd-480e-8c95-3c3c39ff4e7a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cae33496e4dddcaf2d14ba2d87f0d4013795e58f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63165132"
---
# <a name="implementing-a-delivery-extension"></a>Реализация модуля доставки
  Службы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] позволяют пользователям создавать и публиковать отчеты, которые затем могут доставляться в различные места. Кроме того, службы [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] содержат несколько модулей доставки и API-интерфейс доставки, который позволяет разработчикам создавать дополнительные модули доставки, расширяя возможности доставки в службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 Образец реализации модуля доставки см. в разделе [Образцы продуктов служб SQL Server Reporting Services](https://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="in-this-section"></a>в этом разделе  
 [Общие сведения о модулях доставки] доставки расширения overview.md)  
 Введение в процесс написания пользовательского модуля доставки для служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 [Подготовка к реализации модуля доставки](preparing-to-implement-a-delivery-extension.md)  
 Описывает интерфейсы и классы, доступные при реализации модуля доставки служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], а также вопросы, которые следует обдумать перед реализацией.  
  
 [Создание библиотеки модулей доставки](creating-a-delivery-extension-library.md)  
 Описывается процесс присвоения пространства имен модулю доставки служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] и процесс компиляции модуля доставки в DLL-библиотеку.  
  
 [Реализация интерфейса IDeliveryExtension для модуля доставки](implementing-the-ideliveryextension-interface-for-a-delivery-extension.md)  
 Описывает атрибуты модуля доставки и процесс реализации собственного класса модуля доставки.  
  
 [Использование класса Notification для модуля доставки](using-a-notification-class-for-a-delivery-extension.md)  
 Описывает атрибуты класса **Notification** и способ его использования в реализации модуля доставки.  
  
 [Использование класса Setting для модуля доставки](using-the-setting-class-for-a-delivery-extension.md)  
 Описывает атрибуты класса **Setting** и способ его использования в реализации модуля доставки.  
  
 [Использование интерфейса IDeliveryReportServerInformation для модуля доставки](using-the-ideliveryreportserverinformation-interface-for-a-delivery-extension.md)  
 Описывает атрибуты интерфейса **IDeliveryReportServerInformation** и способ его использования в реализации модуля доставки.  
  
 [Использование класса Report для модуля доставки](using-the-report-class-for-a-delivery-extension.md)  
 Описывает атрибуты класса **Report** и способ его использования в реализации модуля доставки.  
  
 [Использование класса RenderedOutputFile для модуля доставки](using-the-renderedoutputfile-class-for-a-delivery-extension.md)  
 Описывает атрибуты класса **RenderedOutputFile** и способ его использования в реализации модуля доставки.  
  
 [Реализация интерфейса ISubscriptionBaseUIUserControl для модуля доставки](implementing-the-isubscriptionbaseuiusercontrol-interface.md)  
 Описывает атрибуты управления пользователями модуля доставки и способ реализации собственного пользовательского интерфейса для подписки.  
  
 [Развертывание модуля доставки](deploying-a-delivery-extension.md)  
 Описывается процесс развертывания модуля доставки.  
  
 [Отладка кода модулей доставки](debugging-delivery-extension-code.md)  
 Описывается процесс отладки кода модулей доставки.  
  
 [Удаление модуля доставки](removing-a-delivery-extension.md)  
 Описывается процесс удаления модуля доставки с сервера отчетов.  
  
## <a name="see-also"></a>См. также  
 [Модули служб Reporting Services](../reporting-services-extensions.md)   
 [Библиотека модулей Reporting Services](../reporting-services-extension-library.md)  
  
  
