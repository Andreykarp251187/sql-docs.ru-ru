---
title: Редактор назначения обработки измерений (страница «Диспетчер соединений») | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dimprocessingtransformation.connection.f1
helpviewer_keywords:
- Dimension Processing Destination Editor
ms.assetid: 44aab631-d62d-4895-8fc7-7f1f3b1b68ce
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 2259b19cec6674cdb1f5f4a0064334f78aa5300f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66059439"
---
# <a name="dimension-processing-destination-editor-connection-manager-page"></a>Редактор назначения обработки измерений (страница «Диспетчер соединений»)
  Страница **Диспетчер соединений** в диалоговом окне **Редактор назначения обработки измерений** позволяет указать соединение с проектом служб [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] или с экземпляром служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 Дополнительные сведения о назначении обработки измерений см. в разделе [Dimension Processing Destination](data-flow/dimension-processing-destination.md).  
  
## <a name="options"></a>Параметры  
 **Connection manager**  
 Выберите из списка существующий диспетчер соединений или нажмите кнопку **Создать** , чтобы создать диспетчер соединений.  
  
 **Создать**  
 Создайте новое соединение, воспользовавшись диалоговым окном **Добавление диспетчера соединений со службами Analysis Services** .  
  
 **Список доступных измерений**  
 Выберите измерение для обработки.  
  
 **Метод обработки**  
 Выберите метод обработки, применяемый к выбранному в списке измерению. Значение этого параметра по умолчанию — **Полная**.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**Добавление (дополнительное)**|Выполнить добавочную обработку измерения.|  
|**Полная**|Выполнить полную обработку измерения.|  
|**Update**|Выполнить обновление обработки измерения.|  
  
## <a name="see-also"></a>См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор назначения "Обработка измерения" (страница "Сопоставления")](../../2014/integration-services/dimension-processing-destination-editor-mappings-page.md)   
 [Редактор назначения "Обработка измерения" (страница "Дополнительно")](../../2014/integration-services/dimension-processing-destination-editor-advanced-page.md)  
  
  
