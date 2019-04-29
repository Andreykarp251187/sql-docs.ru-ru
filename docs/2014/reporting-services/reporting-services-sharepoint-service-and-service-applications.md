---
title: Службы SharePoint Services и приложения службы Reporting | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 501aa9ee-8c13-458c-bf6f-24e00c82681b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 40bfd5e68aa8c27ee0024147eeadc99f0da91ce2
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63182876"
---
# <a name="reporting-services-sharepoint-service-and-service-applications"></a>Служба SharePoint и Служебные приложения службы Reporting Services
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] спроектирован на основе архитектуры службы SharePoint и использует службу SharePoint, а также одно или несколько приложений службы. Создание приложения службы открывает доступ к службе и формирует базу данных приложения службы. Можно создать несколько приложений службы Reporting Services, однако для большинства сценариев развертывания достаточно одного приложения службы.  
  
 В этом разделе рассматриваются следующие сведения:  
  
-   [Создание приложения службы Reporting Services](#bkmk_createapp)  
  
-   [Изменение взаимосвязей приложения службы с использованием группы прокси-серверов](#bkmk_associations)  
  
-   [Изменение свойств приложения службы](#bkmk_editserviceapplication)  
  
-   [Создание приложения службы Reporting Services с помощью PowerShell](#bkmk_powershell_create_ssrs_serviceapp)  
  
-   [Связанные задачи](#bkmk_related)  
  
##  <a name="bkmk_createapp"></a> Создание приложения службы Reporting Services  
 Центр администрирования SharePoint или скрипты PowerShell можно использовать для создания приложений служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Дополнительные сведения об использовании центра администрирования SharePoint см. в разделе "Создание приложения службы Reporting Services" статьи [Установка служб Reporting Services в режиме интеграции с SharePoint для SharePoint 2010](../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md). В подразделе PowerShell этого раздела приведен пример скрипта PowerShell для создания приложений службы.  
  
##  <a name="bkmk_associations"></a> Изменение взаимосвязей приложения службы с использованием группы прокси-серверов  
 Новая страница для создания приложения служб содержит раздел **Связь с веб-приложением**. Данный раздел позволяет связать приложение службы во время его создания. Для изменения взаимосвязи и установки пользовательской конфигурации в приложении службы выполните следующие шаги. Можно использовать тот же общий процесс, но вместо изменения взаимосвязи приложения службы с пользовательской группой добавить учетную запись-посредник в группу по умолчанию.  
  
1.  В центре администрирования SharePoint в разделе «Управление приложениями» выберите пункт **Настройка связей приложения службы**.  
  
2.  На странице «Связи между приложениями служб» измените представление для **Приложения служб**.  
  
3.  Найдите и щелкните название нового приложения службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Можно щелкнуть группу прокси-серверов приложения **по умолчанию** для добавления прокси-сервера в группу по умолчанию.  
  
4.  В списке **Изменить следующую группу соединений** выберите **Пользовательская**.  
  
5.  Установите флажок для учетной записи-посредника и нажмите кнопку **ОК**.  
  
##  <a name="bkmk_editserviceapplication"></a> Изменение свойств приложения службы  
 Для изменения свойств можно повторно открыть страницу свойств приложения службы.  
  
1.  В центре администрирования SharePoint, в разделе «Управление приложениями», выберите **Управление приложениями служб**.  
  
2.  Выберите приложение службы, щелкнув столбец типа, чтобы выделить всю строку. Если щелкнуть имя приложения, откроется страница «Параметры управления» для службы, а не свойства приложения службы.  
  
3.  На ленте «Приложения службы» нажмите кнопку **Свойства**.  
  
##  <a name="bkmk_powershell_create_ssrs_serviceapp"></a> Создание приложения службы Reporting Services с помощью PowerShell  
 Создать приложение службы и прокси-сервер можно с помощью PowerShell. В следующем примере предполагается, что пул приложения, который необходимо настроить для использования приложения службы, известен вам.  
  
1.  Добавьте объект пула приложений, соответствующий имени пула приложений, в переменную, передаваемую в новое действие.  
  
    ```  
    $appPoolName = get-spserviceapplicationpool "<application pool name>"  
    ```  
  
2.  Создайте приложение службы с указанным именем и именем пула приложений.  
  
    ```  
    New-SPRSServiceApplication -Name 'MyServiceApplication' -ApplicationPool $appPoolName -DatabaseName 'MyServiceApplicationDatabase' -DatabaseServer '<Server Name>'  
    ```  
  
3.  Получите новый объект приложения службы и передайте объект в канал командлета создания новой учетной записи-посредника.  
  
    ```  
    Get-SPRSServiceApplication -name MyServiceApplication | New-SPRSServiceApplicationProxy "MyServiceApplicationProxy"  
    ```  
  
##  <a name="bkmk_related"></a> Связанные задачи  
  
|Задача|Ссылка|  
|----------|----------|  
|Управление параметрами приложения службы.|[Управление приложением службы SharePoint — Reporting Services](../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md)|  
|Резервное копирование и восстановление приложения службы и связанных компонентов, таких как ключи шифрования и прокси-серверы.|[Резервное копирование и восстановление Служебного приложения SharePoint службы Reporting Services](../../2014/reporting-services/backup-and-restore-reporting-services-sharepoint-service-applications.md)|  
  
  
