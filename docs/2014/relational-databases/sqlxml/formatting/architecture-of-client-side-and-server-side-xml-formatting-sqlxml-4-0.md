---
title: Архитектура клиентские и серверные форматирования XML (SQLXML 4.0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- providers [SQLXML], XML formatting architecture
- SQLOLEDB provider
- client-side XML formatting
- data providers [SQLXML], XML formatting architecture
- SQLNCLI, XML
- server-side XML formatting
- SQL Server Native Client, XML
- SQLXMLOLEDB Provider, XML formatting architecture
ms.assetid: 52440d9e-89fd-4c15-a008-a1ea99f41387
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 03601c4d36a3e11de4df35bc32237ac554ca93fd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66014443"
---
# <a name="architecture-of-client-side-and-server-side-xml-formatting-sqlxml-40"></a>Архитектура форматирования XML на стороне клиента и сервера (SQLXML 4.0)
  На следующей иллюстрации показана архитектура форматирования XML на стороне сервера.  
  
 ![Архитектура форматирования XML-кода на стороне сервера. ](../../../database-engine/dev-guide/media/serversidexml.gif "Архитектуры из XML-форматирование на стороне сервера.")  
  
 В этом примере команда, указанная на стороне клиента, передается на сервер. Сервер создает XML-документ и возвращает его клиенту. В этом случае сервер имеет экземпляр [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Чтобы форматировать XML-документ на стороне сервера, можно применять либо поставщик SQLXMLOLEDB, либо SQLOLEDB.  Поставщик SQLXMLOLEDB использует библиотеку Sqlxml4.dll, входящую в SQLXML 4.0. Если используется поставщик SQLOLEDB, по умолчанию получаем функциональность SQLXML, предоставляемую библиотекой Sqlxmlx.dll, входящей в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows, или компоненты доступа к данным MDAC 2.6 или более поздней версии. Чтобы использовать библиотеку Sqlxml4.dll с поставщиком SQLOLEDB, необходимо задать свойство версии SQLXML для «SQLXML.4.0» для объекта SQLOLEDB Connection. В любом случае сервер создает XML-документ и передает его клиенту.  
  
> [!NOTE]  
>  Запросы XPath и диаграммы обновления анализируются на клиенте. Чтобы вернуть шаблон XPath или диаграмму обновления в SQLXML 4.0, используйте библиотеку Sqlxml4.dll.  
  
 На следующей иллюстрации показана архитектура форматирования XML на стороне клиента.  
  
 ![Архитектура форматирования XML-кода на стороне клиента. ](../../../database-engine/dev-guide/media/clientsidexml.gif "Архитектуры из XML-форматирование на стороне клиента.")  
  
 В этом примере клиент использует поставщик SQLXMLOLEDB. В строке подключения свойство поставщика данных должно быть присвоено значение SQLOLEDB. (Это единственное допустимое значение в SQLXML 4.0). На сервер отправляется команда, выполняемая на стороне клиента. Созданный на сервере набор строк отправляется клиенту. Форматирование XML-документа на основе набора строк выполняется на стороне клиента.  
  
 В SQLXML 4.0 в качестве поставщика данных может использоваться собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (SQLNCLI11) или поставщик SQLOLEDB. Теоретически можно получить доступ к любому источнику данных. Если запрос возвращает единственный набор строк, преобразование XML может применяться на клиенте.  
  
  
