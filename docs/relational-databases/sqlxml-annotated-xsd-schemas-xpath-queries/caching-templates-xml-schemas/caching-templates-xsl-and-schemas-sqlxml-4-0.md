---
title: Кэширование шаблонов, XSL и схем (SQLXML 4.0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, caching
- cache [SQLXML]
- memory [SQLXML]
ms.assetid: 80b4fa79-243f-442c-9f22-74ad66186501
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ab740322ff0cf8847e12905cd0545667e7ae6f9b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68001347"
---
# <a name="caching-templates-xsl-and-schemas-sqlxml-40"></a>Кэширование шаблонов, XSL и схем (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Для повышения производительности [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 поддерживает кэширование шаблонов, XSL и схем.  
  
 Все схемы, шаблонов и XSL-файлы (Кроме файлов с https:// или ftp: / / расположение) кэшируются. Кэшированные файлы остаются в памяти, пока процесс выполняется. При завершении процесса содержимое кэша уничтожается. Поэтому, если в запросе выполняется один процесс, выигрыш от кэширования может быть незначителен.  
  
 Подразделы этого раздела содержат дополнительные сведения о кэшировании.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Кэширование шаблонов &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/template-caching-sqlxml-4-0.md)  
 Описывается кэширование шаблонов и приводится соответствующий раздел реестра.  
  
 [Кэширование XSL &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/xsl-caching-sqlxml-4-0.md)  
 Описывается кэширование XSL и приводится соответствующий раздел реестра.  
  
 [Кэширование схем &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/schema-caching-sqlxml-4-0.md)  
 Обсуждаются вопросы параллельной установки SQLXML, связанные с кэшированием схем, и приводятся соответствующие разделы реестра.  
  
  
