---
title: Редактор источника XML (страница «Диспетчер соединений») | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.xmlsourceadapter.connectionmanager.f1
helpviewer_keywords:
- XML Source Editor
ms.assetid: e6507403-a3ce-4b6f-91fc-a7de9f7b6283
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 52933b6bc560ecf2e1d7efda8b54502bafe72a6b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62877420"
---
# <a name="xml-source-editor-connection-manager-page"></a>Редактор источника «XML» (страница «Диспетчер соединений»)
  Используйте страницу **Диспетчер соединений** компонента **Редактор источника «XML»** для указания XML-файла и XSD-схемы, выполняющей преобразование XML-данных.  
  
 Дополнительные сведения об источнике XML см. в разделе [XML Source](data-flow/xml-source.md).  
  
## <a name="static-options"></a>Статические параметры  
 **Режим доступа к данным**  
 Укажите метод выбора данных из источника.  
  
|Значение|Описание|  
|-----------|-----------------|  
|Расположение XML-файла|Извлечь данные из XML-файла.|  
|XML-файл из переменной|Указать имя XML-файла в переменной.<br /><br /> **Дополнительные сведения** [Использование переменных в пакетах](../../2014/integration-services/use-variables-in-packages.md)|  
|XML-данные из переменной|Извлечь XML-данные из значения переменной.|  
  
 **Использовать встроенную схему**  
 Устанавливает, содержит ли источник XML-данных в себе XSD-схему, определяющую и проверяющую его структуру и данные.  
  
 **Местоположение XSD**  
 Введите путь и имя файла XSD-схемы или найдите этот файл, нажав кнопку **Обзор**.  
  
 **Обзор**  
 Используйте диалоговое окно **Открыть** для выбора нужного файла XSD-схемы.  
  
 **Сформировать XSD**  
 Используйте диалоговое окно **Сохранение** для выбора местоположения автоматически сформированного файла XSD-схемы. Редактор формирует схему на основе структуры XML-данных.  
  
## <a name="data-access-mode-dynamic-options"></a>Динамические параметры режима доступа к данным  
  
### <a name="data-access-mode--xml-file-location"></a>Режим доступа к данным = местоположение XML  
 **Местоположение XML**  
 Введите путь и имя файла с XML-данными или определите расположение файла, нажав кнопку **Обзор**.  
  
 **Обзор**  
 Используйте диалоговое окно **Открыть** для нахождения нужного файла с XML-данными.  
  
### <a name="data-access-mode--xml-file-from-variable"></a>Режим доступа к данным = XML-файл из переменной  
 **Имя переменной**  
 Выберите переменную, содержащую путь и имя XML-файла.  
  
### <a name="data-access-mode--xml-data-from-variable"></a>Режим доступа к данным = XML-данные из переменной  
 **Имя переменной**  
 Выберите переменную, содержащую XML-данные.  
  
## <a name="see-also"></a>См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор источника "XML" (страница "Столбцы")](../../2014/integration-services/xml-source-editor-columns-page.md)   
 [Редактор источника "XML" (страница "Вывод ошибок")](../../2014/integration-services/xml-source-editor-error-output-page.md)   
 [Извлечение данных с помощью XML-источника](data-flow/extract-data-by-using-the-xml-source.md)  
  
  
