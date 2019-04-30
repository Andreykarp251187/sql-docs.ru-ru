---
title: rsAccessedDenied — ошибка служб Reporting Services | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- rsAccessDenied error
ms.assetid: 2f76b1bf-96a2-4755-b76b-84e933220efc
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3928d77d79a59dbda6b203c59e626f157d670803
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63229064"
---
# <a name="rsaccesseddenied---reporting-services-error"></a>rsAccessedDenied - Ошибка службы Reporting Services
  Ошибка службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] **rsAccessedDenied** происходит, когда у пользователя нет разрешения на выполнение действия. Например, у них нет назначения роли, которая позволяет им открывать отчет или они открыли свой браузер без необходимых разрешений.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Собственный режим | Режим интеграции с SharePoint|  
  
-   Если ошибка произошла во время доступа к серверу отчетов напрямую при помощи URL-адреса, то это исключение соответствует ошибке HTTP 401.  
  
-   Если ошибка произошла во время работы с диспетчером отчетов или другой программой, то ошибка появится на странице ошибок.  
  
-   Если ошибка произошла во время запланированной операции, подписки или доставки, то сведения о ней появятся только в файле журнала сервера отчетов.  
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|**Название продукта**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|**Идентификатор события**|rsAccessedDenied|  
|**Источник события**|Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings|  
|**Компонент**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|**Текст сообщения**|Предоставленные пользователю 'mydomain\myAccount' разрешения недостаточны для выполнения данной операции. (rsAccessDenied) (ReportingServicesLibrary)|  
  
## <a name="user-action"></a>Действие пользователя  
 Разрешения на доступ к содержимому и операциям сервера отчетов назначаются при помощи ролей. В новой установке только у локальных администраторов есть доступ к серверу отчетов. Чтобы предоставить доступ другим пользователям, локальному администратору необходимо создать назначение ролей, описывающее учетную запись пользователя или группы домена, одну или несколько ролей, определяющих, какие задачи пользователь сможет выполнять, и область видимости (обычно корневую папку или корневой узел в иерархии папок сервера отчетов). Назначения ролей можно создать при помощи диспетчера отчетов. Дополнительные сведения см. по ключевому слову «назначения ролей» в электронной документации по SQL Server.  
  
 Данная ошибка вызывается также локальным администрирование сервера отчетов. Дополнительные сведения см. в разделе [настроить сервер отчетов в собственном режиме для локального администрирования &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).  
  
## <a name="see-also"></a>См. также  
 [Назначения ролей](../security/role-assignments.md)   
 [Предоставление разрешений на сервер отчетов в собственном режиме](../security/granting-permissions-on-a-native-mode-report-server.md)   
 [Роли и разрешения (службы Reporting Services)](../security/roles-and-permissions-reporting-services.md)  
  
  
