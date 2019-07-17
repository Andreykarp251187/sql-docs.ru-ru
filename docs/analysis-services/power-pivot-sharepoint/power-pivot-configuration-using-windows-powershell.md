---
title: Power Pivot конфигурации, с помощью Windows PowerShell | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ppvt-sharepoint
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e290e0e15797a8b84a6d52c945a5fd78458515fc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68208202"
---
# <a name="power-pivot-configuration-using-windows-powershell"></a>Настройка PowerPivot с помощью Windows PowerShell
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] включает в себя командлеты Windows PowerShell, которые можно использовать для настройки установки [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]. Для полной настройки установки c PowerShell требуются как командлеты SharePoint, так и командлеты [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint. Большую часть настройки можно выполнить с помощью одного из средств [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Дополнительные сведения об этих средствах см. в разделе [Средства настройки PowerPivot](../../analysis-services/power-pivot-sharepoint/power-pivot-configuration-tools.md).  
  
> [!IMPORTANT]  
>  При работе с фермой SharePoint 2010 необходимо установить SharePoint 2010 с пакетом обновления 1 (SP1), чтобы иметь возможность настроить [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint или ферму SharePoint, в которой используется сервер базы данных [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] . Если пакет обновления еще не установлен, установите его, прежде чем начать настройку сервера.  
  
## <a name="benefits-of-configuring-power-pivot-for-sharepoint-using-powershell"></a>Преимущества настройки PowerPivot для SharePoint с помощью PowerShell  
 Для автоматизации задач настройки можно построить файлы скриптов Windows PowerShell (PS1). Этот подход рекомендуется, если необходимо обеспечить установку и настройку с помощью скриптов, которые можно выполнить на любом сервере. В случае отказа аппаратной части подобный скрипт может потребоваться как часть плана аварийного восстановления сервера.  
  
## <a name="view-a-list-of-the-power-pivot-cmdlets-on-a-server"></a>Просмотр списка командлетов PowerPivot на сервере  
 Содержимое и примеры командлетов [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] см. в разделе [Справочник по PowerShell для Power Pivot для SharePoint](../../analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint.md).  
  
 Для просмотра списка командлетов [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] с помощью PowerShell выполните следующие действия.  
  
1.  Откройте консоль управления SharePoint с параметром **Запуск от имени администратора** .  
  
2.  Введите следующую команду:  
  
    ```  
    Get-help *powerpivot*  
    ```  
  
     Появится список командлетов, содержащих в имени " [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ". Например, `Get-PowerPivotServiceApplication`. Число доступных командлетов зависит от используемой версии служб Analysis Services.  
  
    -   10 командлетов на сервере служб SQL Server 2012 Analysis Services с пакетом обновления 1 (SP1), работающим в режиме интеграции с SharePoint и SharePoint 2013. Версия 2012 с пакетом обновления 1 (SP1) использует новую архитектуру, которая позволяет серверу анализа данных работать за пределами фермы SharePoint и требует меньше командлетов управления Windows PowerShell.  
  
    -   17 командлетов на сервере служб Analysis Services SQL Server 2012, работающем в режиме интеграции с SharePoint и SharePoint 2010.  
  
     Если команды не возвращаются в списке или вы видите сообщение об ошибке, аналогичную "`get-help could not find *powerpivot* in a help file in this session.`«, см. ниже в этом разделе инструкции по включению [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] командлетов на сервере.  
  
     Для всех командлетов имеется справка в Интернете. В следующем примере показано, как посмотреть справку в Интернете для командлета **New-PowerPivotServiceApplication** .  
  
    ```  
    Get-help new-powerpivotserviceapplication -full  
    ```  
  
     Кроме того, чтобы просмотреть только примеры, используйте следующий синтаксис.  
  
    ```  
    Get-help new-powerpivotserviceapplication -example  
    ```  
  
## <a name="enable-power-pivot-cmdlets-on-a-server"></a>Включение командлетов PowerPivot на сервере  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Командлеты доступны после установки [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint и развертывания решения фермы. Решения развертываются при запуске средства настройки [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Выполните следующие действия, чтобы включить использование командлетов.  
  
1.  Откройте консоль управления SharePoint с параметром **Запуск от имени администратора** .  
  
2.  Запустите первый командлет.  
  
    ```  
    Add-SPSolution -LiteralPath "C:\Program Files\Microsoft SQL Server\110\Tools\PowerPivotTools\ConfigurationTool\Resources\PowerPivotFarm.wsp"  
    ```  
  
     Командлет возвратит имя решения, его идентификатор, а также атрибут Deployed=False. На следующем шаге будет выполнено развертывание решения.  
  
3.  Выполните второй командлет, чтобы развернуть решение.  
  
    ```  
    Install-SPSolution -Identity PowerPivotFarm.wsp -GACDeployment -Force  
    ```  
  
4.  Закройте окно. Откройте его снова с помощью варианта **Запуск от имени администратора** .  
  
## <a name="related-content"></a>См. также  
 [Настройка и администрирование сервера Power Pivot в центре администрирования](../../analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration.md)  
  
 [Средства настройки PowerPivot](../../analysis-services/power-pivot-sharepoint/power-pivot-configuration-tools.md)  
  
 [Справочник по PowerShell для Power Pivot для SharePoint](../../analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint.md)  
  
  
