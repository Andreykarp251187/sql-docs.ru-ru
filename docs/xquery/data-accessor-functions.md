---
title: Функции метода доступа к данным | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- data-accessor functions [XQuery]
ms.assetid: 31bad04f-7c74-4773-9f83-612704fdd21c
author: rothja
ms.author: jroth
ms.openlocfilehash: b3726686a2c0e5229a0fccf4d9f51c0e1404f1a3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68038949"
---
# <a name="data-accessor-functions"></a>Функции метода доступа к данным
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  В темах этого раздела приводятся и обсуждаются образцы кода с использованием функций доступа к данным.  
  
## <a name="understanding-fndata-fnstring-and-text"></a>Основные сведения о функциях fn:data(), fn:string(), и text()  
 Язык XQuery включает функцию **fn: Data()** для извлечения скалярных типизированных значений из узлов, проверку узла **text()** для возврата текстовых узлов, а функция **fn: String()** , возвращающий Строковое значение узла. Их применение понятно далеко не всем. Ниже приведены рекомендации по правильному использованию этих функций в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Экземпляр XML \<age > 12 \< /age > используется в целях иллюстрации.  
  
-   Нетипизированный XML: Выражение пути /age/text() возвращает текстовый узел «12». Функции fn:data(/age) и fn:string(/age) возвращают строковое значение«12».  
  
-   Типизированный XML: Выражение /age/text() возвращает статическую ошибку для любого простого типизированного \<age > элемента. С другой стороны, функция fn:data(/age) возвращает целое число 12. Функция fn:string(/age) возвращает строку «12».  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Функция String &#40;XQuery&#41;](../xquery/data-accessor-functions-string-xquery.md)  
  
-   [данные функции &#40;XQuery&#41;](../xquery/data-accessor-functions-data-xquery.md)  
  
## <a name="see-also"></a>См. также  
 [Выражения пути &#40;XQuery&#41;](../xquery/path-expressions-xquery.md)  
  
  
