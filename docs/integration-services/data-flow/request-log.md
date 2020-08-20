---
description: Журнал запросов
title: Журнал запросов | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 165d3833-0493-490c-9f63-8a134a7fafb8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fe85b46fcdcfdb398993dc073f69a8c31aa08742
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88484587"
---
# <a name="request-log"></a>Журнал запросов

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Используйте диалоговое окно **Журнал запросов** для просмотра событий, зарегистрированных в момент запроса, который выполняется в системе SAP Netweaver BW для образца данных. Эти сведения могут быть полезны, если необходимо устранить неисправности в конфигурации источника SAP BW.  
  
 Для получения дополнительных сведений о компоненте источника SAP BW для [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 для SAP BW см. раздел [Источник SAP BW](../../integration-services/data-flow/sap-bw-source.md).  
  
> [!IMPORTANT]  
>  Документация по Microsoft Connector 1.1 для SAP BW предполагает, что читатель знаком со средой SAP Netweaver BW. Дополнительные сведения о SAP Netweaver BW или сведения о настройке объектов и процессов SAP Netweaver BW см. в документации SAP.  
  
> [!IMPORTANT]  
>  Для извлечения данных из SAP Netweaver BW требуется дополнительная лицензия SAP. Обратитесь к SAP, чтобы уточнить требования.  
  
 **Открытие диалогового окна «Журнал запросов»**  
  
1.  В [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте пакет [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , содержащий источник SAP BW.  
  
2.  На вкладке **Поток данных** дважды щелкните источник SAP BW.  
  
3.  В **Редакторе источника SAP BW**щелкните **Диспетчер соединений** , чтобы открыть страницу редактора **Диспетчер соединений** .  
  
4.  После настройки источника SAP BW, нажмите кнопку **Предварительный просмотр** , чтобы просмотреть события в диалоговом окне **Журнал запросов** .  
  
    > [!NOTE]  
    >  Щелчок правой кнопкой мыши **Предварительный просмотр** также открывает диалоговое окно **Предварительный просмотр** . Дополнительные сведения об этом диалоговом окне см. в разделе [Preview](../../integration-services/data-flow/preview.md).  
  
## <a name="options"></a>Параметры  
 **Time**  
 Отображает время записи события в журнал.  
  
 **Тип**  
 Указывает тип события, которое было зарегистрировано в журнале. В следующей таблице перечислены возможные типы событий.  
  
|Значение|Описание|  
|-----------|-----------------|  
|S|Сообщение об успехе.|  
|E|Сообщение об ошибке|  
|W|Предупреждающее сообщение.|  
|I|Информационное сообщение.|  
|Объект|Операция была прервана.|  
  
 **Message**  
 Отображает текст сообщения, связанный с событием, записанным в журнал.  
  
## <a name="see-also"></a>См. также:  
 [Редактор источника SAP BW (страница "Диспетчер подключений")](../../integration-services/data-flow/sap-bw-source-editor-connection-manager-page.md)   
 [Справка F1 по Microsoft Connector для SAP BW](../../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
  
  
