---
title: Пространство (ADO — синтаксис WFC) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- DataSpace collection [ADO], ADO/WFC syntax
ms.assetid: 950d45d8-07de-467b-b255-f9a7b997204c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 569944991c029c091f0f17be4e5d943a893333a7
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "67919189"
---
# <a name="dataspace-ado---wfc-syntax"></a>DataSpace (ADO — синтаксис WFC)
Метод **CreateObject** класса **пространства** данных определяет как бизнес-объект для обработки запросов клиентских приложений (*ProgID*), так и протокол связи и сервер (*соединение*). Функция **CreateObject** возвращает объект [обжектпрокси](../../../ado/reference/ado-api/objectproxy-ado-wfc-syntax.md) , представляющий сервер.  
  
## <a name="package-commswfcdata"></a>упаковать com. MS. WFC. Data  
  
### <a name="constructor"></a>Конструктор  
  
```  
public DataSpace()  
```  
  
### <a name="methods"></a>Методы  
  
```  
public static ObjectProxy DataSpace.createObject(String  
    progid, String connection)  
```  
  
### <a name="properties"></a>Свойства  
  
```  
public static int getInternetTimeout()  
public static void setInternetTimeout(int plInetTimeout)  
```  
  
## <a name="see-also"></a>См. также  
 [Объект DataSpace (служба удаленных рабочих столов)](../../../ado/reference/rds-api/dataspace-object-rds.md)
